---
title:  Lateral Movement 🤸🏻‍♂️
layout: default
has_toc: false
nav_order: 6
parent: Hunting an APT 👺
---

# Hunting an APT - **Lateral Movement**


{: .intro }
>Los adversarios buscarán ejecutar código en otros sistemas locales utilizando Windows Management Instrumentation (WMI). Pueden abusar de esto para lograr la ejecución. 

Un adversario puede usar WMI para interactuar con sistemas locales y remotos, y usarlo como un medio para realizar muchas funciones tácticas, como recopilar información para el Descubrimiento y la Ejecución remota de archivos como parte del Movimiento Lateral.

[https://attack.mitre.org/techniques/T1047/](https://attack.mitre.org/techniques/T1047/)

Para comprender mejor el movimiento lateral,consultaremos la guia de:  *Detecting Lateral Movement through Tracking Event Logs*:

[https://www.jpcert.or.jp/english/pub/sr/20170612ac-ir_research_en.pdf](https://www.jpcert.or.jp/english/pub/sr/20170612ac-ir_research_en.pdf)

Utilizaremos esto como punto de partida en Splunk. Basado en los resultados de la búsqueda, los eventos de WMI están asociados con un host interno.

![LM1.png](https://i.postimg.cc/NM0wtrdT/LM1.png)



`index="botsv2" sourcetype="xmlwineventlog:microsoft-windows-sysmon/operational" EventCode=1 ParentImage="C:\\Windows\\System32\\svchost.exe" CurrentDirectory="C:\\Windows\\system32\\"
CommandLine="C:\\Windows\\system32\\wbem\\wmiprvse.exe -secured -Embedding" ParentCommandLine="C:\\Windows\\system32\\svchost.exe -k DcomLaunch"
user="NT AUTHORITY\\NETWORK SERVICE"  Image="C:\\Windows\\System32\\wbem\\WmiPrvSE.exe"`

![LM2.png](https://i.postimg.cc/1zBZbKrs/LM2.png)


Se ha identificado que la estación de trabajo wrf-klagerf parece estar mostrando signos de movimiento lateral utilizando WMI, según se describe en el documento de JPCert. 

Si se observa el **Evento 4624 con Tipo de Inicio de Sesión 3**, seguido por los privilegios especiales asignados en el **Evento 4672**, y luego seguido por el **Evento de creación de proceso de Sysmon 1 con WmiPrvSE.exe**, se puede confirmar la ejecución remota a través de WMI.

Se comenzará construyendo la búsqueda con eventos de inicio de sesión de red y buscando eventos de creación de procesos de Sysmon que no tengan una línea de comando del proceso padre que termine en "svchost.exe". Muchos procesos comienzan con svchost.exe. 

Aunque es posible que pueda haber problemas con svchost.exe, es razonable suponer que no es un problema y continuar con la búsqueda inicial por ahora. 
Desde ahí, se usaría el comando eval para reunir los campos Logon_ID y Security_ID. La función mvindex permite examinar múltiples valores con el mismo nombre de campo y seleccionar el N-ésimo valor especificado en la función mvindex. También se puede usar el comando transaction para buscar valores comunes y asociar eventos entre sí, asegurándose de que el primer evento siempre sea el iniciado con el evento 4624 (evento de inicio de sesión exitoso en red). Con la búsqueda en marcha, se puede ver que el servidor venus y la estación de trabajo de Kevin muestran signos de ejecución utilizando la cuenta service3 desde las sesiones de inicio de sesión de red.

```
(sourcetype=wineventlog (EventCode=4624 Logon_Type=3)) OR (sourcetype="xmlwineventlog:microsoft-windows-sysmon/operational" ParentCommandLine!="*\\svchost.exe" EventCode=1)
| eval login=mvindex(Logon_ID,1)
| eval user_id=mvindex(Security_ID,1)
| eval session = lower(coalesce(login,LogonId))
| transaction session startswith=(EventCode=4624) mvlist=ParentImage
| search eventcount>1
| eval Parent_Process=mvindex(ParentImage,1)
| table _time dest session host user_id Parent_Process Image CommandLine
```

- sourcetype=wineventlog (EventCode=4624 Logon_Type=3): Filtra eventos del tipo wineventlog que tienen EventCode=4624 y Logon_Type=3, lo cual típicamente corresponde a un inicio de sesión exitoso en una red.
- eval login=mvindex(Logon_ID,1): Extrae el segundo valor del campo Logon_ID y lo guarda en login.
- eval user_id=mvindex(Security_ID,1): Extrae el segundo valor del campo Security_ID y lo guarda en user_id.
- eval session=lower(coalesce(login,LogonId)): Combina login y LogonId (usando el primero que no sea nulo) y convierte el resultado a minúsculas, guardándolo en session.
- transaction session startswith=(EventCode=4624) mvlist=ParentImage: Agrupa eventos en transacciones basadas en el campo session, comenzando con eventos que tienen EventCode=4624. Almacena múltiples valores del campo ParentImage en una lista.
- search eventcount>1: Filtra las transacciones para incluir solo aquellas que contienen más de un evento.
- eval Parent_Process=mvindex(ParentImage,1): Extrae el segundo valor del campo ParentImage y lo guarda en Parent_Process.
- table _time dest session host user_id Parent_Process Image CommandLine: Selecciona los campos _time, dest, session, host, user_id, Parent_Process, Image y CommandLine para la salida final en forma de tabla.

![LM3.png](https://i.postimg.cc/Sx0q9RKF/LM3.png)


Podemos ver que tanto 'venus' como 'wrk-klagerf' tienen signos de ejecuciones utilizando el servicio de cuenta3 desde las sesiones de inicio de sesión de cuenta.

## **Inspeccionando Sesiones de Inicio de Sesión**

Usaremos los IDs de inicio de sesión (Logon_ID de Sysmon o LogonId de Wineventlog) y los desglosaremos en hosts específicos (venus y la estación de trabajo de Kevin).

Para mejorar la legibilidad, utilizaremos el comando eval para limitar CommandLine y ParentCommandLine a 100 caracteres, permitiendo identificar PowerShell codificado en nuestras líneas de comando.

Al revisar los resultados de búsqueda, observamos que los eventos 4624 (inicio de sesión en red), 4672 (inicio de sesión especial) y el evento 1 de Sysmon (wmiprvse.exe) se ejecutan casi simultáneamente, lo que coincide con el patrón de movimiento lateral WMI. 

```
index="botsv2" ((Logon_ID=0x171491a OR LogonId=0x171491a) host=venus)
| eval shortCL=substr(CommandLine,1,100)
| eval shortPCL=substr(ParentCommandLine,1,100)
| table _time EventCode TaskCategory Account_Name Security_ID Process_Command_Line shortCL shortPCL
| reverse
```

![LM4.png](https://i.postimg.cc/YC17z744/LM4.png)


```
index="botsv2" ((Logon_ID=0xf9b47f OR LogonId=0xf9b47f) host=wrk-klagerf)
| eval shortCL=substr(CommandLine,1,100)
| eval shortPCL=substr(ParentCommandLine,1,100)
| table _time EventCode TaskCategory Account_Name Security_ID Process_Command_Line shortCL shortPCL
| reverse
```

![LM5.png](https://i.postimg.cc/43sg80tW/LM5.png)


En la estación de trabajo de wrk-klagerf, los registros de eventos muestran un patrón similar con la ejecución simultánea de los eventos 4624, 4672 y 1.

Ambos hosts tienen una ParentCommandLine de WMI idéntica (C:\Windows\system32\wbem\wmiprvse.exe -secured -Embedding). 

Si buscamos esa misma ParentCommandLine en otros lugares, observamos que también está presente en la estación de trabajo de Billy, unos 30 minutos antes de ejecutarse en el servidor venus y en la estación de trabajo de wrk-klagerf.

 Esto sugiere que, después de que el adversario estableció un punto de apoyo en la estación de trabajo de Billy, se movieron lateralmente a la estación de trabajo de wrk-klagerf y al servidor venus.

```
index="botsv2" sourcetype="xmlwineventlog:microsoft-windows-sysmon/operational"  ParentCommandLine="C:\\Windows\\system32\\wbem\\wmiprvse.exe -secured -Embedding"
| eval shortCL=substr(CommandLine,1,100)
| table _time user host ProcessId ParentProcessId shortCL ParentCommandLine
```

![LM6.png](https://i.postimg.cc/ZKv40p4x/LM6.png)

## Conclusión

Los hosts internos venus y wrk-klagers fueron infectados mediante movimiento lateral desde wrk-btun.

Se utilizó PowerShell para facilitar el movimiento lateral.

Todos los procesos están ejecutando PowerShell codificado.

Además, en wrk-btun también se observa PowerShell codificado con un lanzador diferente, pero con los mismos comandos.

Debemos de tener en cuenta los siguientes puntos:

- **Configurar alertas para PowerShell codificado:** Si no deseamos que PowerShell codificado se ejecute en nuestro entorno, podemos configurar alertas para detectarlo.
- **Gestionar herramientas de administración remota de Windows:** Es importante identificar cuáles de estas herramientas son esenciales y desactivar las que no lo son.
- **Monitorear el uso de herramientas administrativas:** Implementar sistemas de monitoreo que identifiquen los patrones de uso de estas herramientas ayudará a detectar cualquier actividad inusual.
- **Establecer alertas para secuencias específicas de eventos:**  Una secuencia que incluya el EventCode 4624 Tipo 3 seguido del EventCode 4672 y luego del EventCode 1 de Sysmon puede ser indicativa de actividad sospechosa.
- **Analizar los flujos de datos en el entorno:** Debemos determinar si es necesario que las estaciones de trabajo se comuniquen entre sí. Limitar la comunicación entre estaciones de trabajo.

![LM7.png](https://i.postimg.cc/SstbxNPP/LM7.png)