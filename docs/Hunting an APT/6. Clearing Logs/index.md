---
title:  Clearing Logs
layout: default
has_toc: false
nav_order: 7
parent: Hunting an APT 👺
---

# Hunting an APT - **Lateral Movement**


{: .intro }
>El borrado de registros de eventos es una táctica común que los adversarios utilizan para cubrir sus huellas.

Los adversarios pueden borrar los registros de eventos de Windows para ocultar la actividad de una intrusión. Los registros de eventos de Windows son un historial de alertas y notificaciones de una computadora. Existen tres fuentes de eventos definidas por el sistema: **Sistema, Aplicación y Seguridad.**

Cinco tipos de eventos: Error, Advertencia, Información, Auditoría Exitosa y Auditoría Fallida.

El código de evento para "Registro de eventos de Windows borrado" es 1102.

Si buscamos en los registros de eventos de Windows el evento 1102:

```
index=botsv2 sourcetype=wineventlog EventCode=1102
```

![CL1.png](https://i.postimg.cc/0Nqs7sjx/CL1.png)

Podemos ver que la estación de trabajo "wrk-klagerf" tuvo sus registros borrados. También podemos ver que "service3" es la cuenta que borró los registros.

En caso de que no se estén recopilando los registros de eventos de Windows (Wineventlogs) o el código de evento no esté configurado en 1102, se puede utilizar el comando "Wevtutil". Este comando permite interactuar con los registros de eventos desde la línea de comandos y se pueden realizar muchas acciones con este ejecutable, incluyendo la consulta de eventos. Sin embargo, también es posible borrar los registros utilizando wevtutil.exe.

```latex
index=botsv2 wevtutil.exe
```

![CL2.png](https://i.postimg.cc/L4y2wwCB/CL2.png)

Podemos ver que tanto Sysmon como Wineventlog tienen referencias a este ejecutable.

Si profundizamos en el tipo de fuente de los registros de eventos de Windows y utilizamos el comando "table" para ver campos específicos en una vista tabular, y el comando "sort" para mostrar los eventos desde el más antiguo hasta el más reciente, podemos ver que todos los procesos provienen del código de evento 4688.

```latex
index=botsv2 wevtutil.exe sourcetype=wineventlog
| table _time EventCode RecordNumber Account_Name New_Process_Name Process_Command_Line
| sort + RecordNumber
```

![CL3.png](https://i.postimg.cc/52zJH0xn/CL3.png)

Podemos ver en el campo `Process_Command_Line` que `wevtutil.exe` se invoca en cada uno de los eventos.

El primer evento utilizó el argumento "el", que enumeró los registros, y luego los comandos posteriores utilizaron el argumento "cl", cada uno llamando a un archivo de registro distinto.

Estos comandos borraron cada archivo de registro llamado. Podemos ver 485 eventos, por lo que es probable que se hayan borrado todos los registros de Windows posibles en secuencia.

Si observamos los datos de Sysmon, podemos ver resultados similares con algunas pequeñas diferencias.

![CL4.png](https://i.postimg.cc/gknmWs19/CL4.png)

Cuando inicialmente revisamos el tipo de fuente Sysmon, teníamos 970 eventos, pero ahora solo tenemos 485. 

Agregamos criterios de filtrado para excluir las descripciones de eventos que son “process terminate”, ya que eran menos interesantes que las “process creation” que constituían la otra mitad de estos eventos. 

También utilizamos los comandos "table" y "sort" para ordenar y mostrar los eventos desde el más antiguo hasta el más reciente, incluyendo la hora del evento, el nombre del host, el usuario bajo el cual se ejecutó el comando, las líneas de comando y las líneas de comando principales que se ejecutaron.

```latex
index=botsv2 wevtutil.exe sourcetype="xmlwineventlog:microsoft-windows-sysmon/operational" EventDescription!="Process Terminate"
| table _time RecordID host user CommandLine ParentCommandLine
| sort + RecordID
```

![CL5.png](https://i.postimg.cc/vHkMH9d4/CL5.png)

Deberemos determinar qué contiene la línea de comando de PowerShell para ver en detalle las acciones realizadas. En este caso podremos ver que es el mismo mensaje que descubrimos durante 

Una vez detectado el hecho debemos fortalecer nuestros sistemas realizando los siguientes pasos: 

1. **Configurar la política de grupo para registrar el borrado de registros:**
    
    Asegurarse de que esos registros se registren, de modo que, incluso si son borrados, no se pierdan porque se mantienen en otro lugar.
    
2. **Monitorear y alertar sobre el código de evento 1102:**
    
    Identificar la cuenta y el sistema para determinar si existen condiciones que justifiquen el borrado de registros.
    
3. **Monitorear el código de evento 4688 de Windows con valores adicionales como `Process_Command_Line="\\"C:\\\\Windows\\\\system32\\\\wevtutil.exe\\"*cl*"`:**
    
    4688 es un buen evento para registrar todo el tiempo, pero podría ser útil tener alertas adicionales cuando se encuentren estas condiciones.
    
4. **Monitorear y alertar sobre eventos de Sysmon con la descripción de evento "Process Create" y `CommandLine="\\"C:\\\\Windows\\\\system32\\\\wevtutil.exe\\"*cl*"`:**
    
    Esto ayudará a detectar intentos de borrar registros de eventos a través de wevtutil.exe.
    
5. **Revisar la política de TI y seguridad para determinar qué registros deben o no deben ser borrados:**
    
    Utilizar una lista de exclusión para formar un listado de los registros que no deberían ser eliminados, si es aplicable.