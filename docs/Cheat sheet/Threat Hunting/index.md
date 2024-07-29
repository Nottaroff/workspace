---
title: Threat Hunting 🔎
layout: default
has_toc: false
nav_order: 2
parent:  Cheat Docs 🔰
---

# Threat Hunting 🔎

## Win Events 📅

### Obtener Información del Evento ID 1

Visualización de los eventos con ID 1 que generalmente corresponden a la creación de un proceso del log de Sysmon.

```powershell
$event1 = get-winevent -logname Microsoft-Windows-Sysmon/Operational | Where-Object {$_.id -like '1'}
```

### Obtener miembros para ver todos los campos disponibles para filtrar

Propiedades y métodos disponibles en los eventos obtenidos.

```powershell
$event1 | Get-Member
```

### Registro de ejemplo

Obtiene un único evento con ID 1 y muestra todas sus propiedades.

```powershell
get-winevent -FilterHashtable @{logname='Microsoft-Windows-Sysmon/Operational';ID='1'} -maxevents 1 | Select-Object *
```

### Buscar registros que contengan la cadena "mshta"

Filtra los eventos obtenidos previamente para mostrar solo aquellos cuyo mensaje contiene la cadena "mshta", comúnmente utilizada en ataques.

```powershell
$event1 | Where-Object {$_.message -match 'mshta'}
```

### Expandir el campo del mensaje para ver todos los detalles

Expande la propiedad "message" de los eventos filtrados para ver todo el contenido detallado del mensaje.

```powershell
$event1 | Where-Object {$_.message -match 'mshta'} | Select-Object -ExpandProperty message
```

### Filtrar la salida para obtener una lista limpia

Filtra y muestra solo las líneas del mensaje que contienen "CommandLine".

```powershell
$event1 | Where-Object {$_.message -match 'mshta'} | Select-Object -ExpandProperty message | findstr CommandLine
```

## Investigación de Conexiones de Red 🌐

### Obtener Información del Evento ID 3

Este comando obtiene un único evento con ID 3 que corresponde a conexiones de red del log de Sysmon.

```powershell
get-winevent -FilterHashtable @{logname='Microsoft-Windows-Sysmon/Operational';ID='3'} -maxevents 1 | Select-Object *
```

### Crear una variable para los eventos de conexión de red

Almacena todos los eventos con ID 3 en una variable para análisis posterior.

```powershell
$event3 = get-winevent -logname Microsoft-Windows-Sysmon/Operational | Where-Object {$_.id -like '3'}
```

### Filtrar por IP maliciosa

Filtra los eventos almacenados en la variable para mostrar solo aquellos cuyo mensaje contiene la IP especificada.

```powershell
$event3 | Where-Object {$_.message -match 'X.X.X.X'}
```

### Expandir detalles del mensaje

Expande la propiedad "message" de los eventos filtrados y muestra líneas específicas que contienen información relevante, como la imagen y el puerto de destino.

```powershell
$event3 | Where-Object {$_.message -match 'X.X.X.X'} | Select-Object * | findstr "Image: DestinationPort:"
```

## Análisis de LNK 🔗

### Listar todos los archivos .lnk en un directorio

Este comando utiliza una herramienta externa [lnk-parser](https://code.google.com/archive/p/lnk-parser/) para listar todos los archivos .lnk en el directorio especificado, lo que puede ayudar a identificar archivos sospechosos.

```powershell
C:\path\to\tools\lnk_parser_cmd.exe -c -w C:\Users\Administrator\Desktop
```

### Importar resultados CSV para análisis adicional

Importa los resultados del análisis de archivos .lnk desde un archivo CSV.

```powershell
$lnk = Import-Csv ./Report.csv
```

### Buscar archivos ejecutados con argumentos específicos

Filtra los datos importados para encontrar archivos .lnk que fueron ejecutados con argumentos específicos que pueden ser sospechosos.

```powershell
$lnk | Where-Object { $_."Arguments (UNICODE)" -match "suspect_argument" }
```

## Persistencia

### Búsqueda de entradas en claves del Registro

```powershell
Get-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run'
Get-Item -Path 'HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run'
Get-Item -Path 'HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce'
Get-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce'
```

Buscar entradas en claves específicas del Registro de Windows que suelen utilizarse para ejecutar programas automáticamente al inicio del sistema. Las rutas 'HKLM' y 'HKCU' se refieren a HKEY_LOCAL_MACHINE y HKEY_CURRENT_USER respectivamente. Las claves 'Run' y 'RunOnce' contienen programas que se ejecutan al inicio de sesión del usuario o del sistema.

### Búsqueda de nuevo nombre de proceso (reg.exe)

```powershell
$event1 = get-winevent -logname Microsoft-Windows-Sysmon/Operational | Where-Object {$_.id -like '1'}
$event1 | Where-Object {$_.message -match "reg.exe"} | Select-Object -ExpandProperty message | findstr CommandLine
```

Buscar eventos en el registro de eventos de Sysmon que indiquen la creación de procesos (evento ID 1) y filtrar aquellos donde el mensaje contenga "reg.exe". Se utiliza para identificar la ejecución de 'reg.exe', una herramienta de línea de comandos para modificar el Registro de Windows.

### Búsqueda de Tareas Programadas

#### Evento 4698

```powershell
get-winevent -logname security | Where-Object {$_.id -like '4698'}
```

Buscar en el registro de eventos de seguridad de Windows eventos con el ID 4698, que indican la creación de nuevas tareas programadas. Las tareas programadas pueden ser utilizadas para mantener la persistencia en el sistema.

### Información disponible en get-scheduledtask

```powershell
(Get-ScheduledTask).Count
Get-ScheduledTask | Get-Member
(Get-ScheduledTask).Actions | Get-Member
```

Examina las tareas programadas actuales en el sistema. 'Get-ScheduledTask' recupera todas las tareas programadas, y 'Get-Member' muestra las propiedades y métodos de los objetos devueltos, ayudando a entender la estructura de los datos de las tareas.

### Anomalías a buscar

#### Ejecución de tareas

```powershell
(Get-ScheduledTask).Actions.Execute
(Get-ScheduledTask).Actions | Group-Object -property Execute | Sort-Object -Property Count
(Get-ScheduledTask).Actions | Where-Object {$_.Execute -notlike "windir" -and $_.Execute -notlike "*Systemroot*"} | Group-Object -property Execute | Sort-Object -Property Count
```

Buscar y agrupar las acciones de ejecución de las tareas programadas, ordenándolas por la cantidad de veces que se ejecutan.

#### sc.exe

```powershell
Get-ScheduledTask | Where-Object {$_.Actions.Execute -like "sc.exe"} | Select-Object *
(Get-ScheduledTask).Actions | Where-Object {$_.Execute -like "sc.exe"} | Select-Object *
```

Filtrar tareas programadas que ejecutan 'sc.exe', una herramienta de línea de comandos utilizada para administrar servicios.

#### Argumentos de la tarea

```powershell
(Get-ScheduledTask).Actions.Arguments
```

##### Ejecución PowerShell

```powershell
(Get-ScheduledTask).Actions | Where-Object {$_.Arguments -like "*powershell*"} | Select-Object *
```

Buscar argumentos de ejecución en las tareas programadas, específicamente buscando aquellos que ejecutan PowerShell.

#### Ruta de la tarea fuera de Microsoft

```powershell
get-scheduledtask | group-object -property TaskPath
get-scheduledtask | Where-Object {$_.TaskPath -notlike "\Microsoft*"} | Format-Table TaskName,Taskpath,State
```

Agrupar y mostrar tareas programadas cuya ruta de tarea no pertenece a Microsoft.

#### Datos principales - UserId

```powershell
(Get-ScheduledTask).Principal | group-object -property UserId
```

Agrupar las tareas programadas por el ID de usuario que las creó.

#### Autor

```powershell
(Get-ScheduledTask).Author
get-scheduledtask | Group-Object -property Author | Sort-Object -Property Count
get-scheduledtask | Where-Object {$_.Author -like "USER01\Administrator"} | Select-Object *
(get-scheduledtask | Where-Object {$_.Author -like "USER01\Administrator"}).Actions | Select-Object *
```

Agrupar y filtrar tareas programadas por el autor, especialmente buscando aquellas creadas por 'Administrator', ya que puede ser indicativo de una configuración maliciosa utilizando privilegios administrativos.

### Verificación de hashes

#### Verificar hash de archivo

```powershell
certutil.exe -hashfile C:\path\to\file.exe MD5
```

---

## Escalada de Privilegios y Robo de Credenciales

### Búsqueda de mimikatz

#### Establecer la variable

```powershell
$event1 = get-winevent -logname Microsoft-Windows-Sysmon/Operational | Where-Object {$_.id -like '

1'}
```

#### Buscar en los registros que contengan la cadena "sekurlsa"

```powershell
$event1 | Where-Object {$_.message -match 'sekurlsa'}
```

#### Expandir el campo de mensaje para ver todos los detalles

```powershell
$event1 | Where-Object {$_.message -match 'sekurlsa'} | Select-Object -ExpandProperty message
```

#### Filtrar la salida para obtener una lista limpia

```powershell
$event1 | Where-Object {$_.message -match 'sekurlsa'} | Select-Object -ExpandProperty message | findstr CommandLine
```

Buscar eventos en el registro de eventos de Sysmon que indiquen la creación de procesos (evento ID 1) y filtrar aquellos donde el mensaje contenga "sekurlsa". 'sekurlsa' es una palabra clave asociada con mimikatz, una herramienta utilizada para robar credenciales de Windows. La búsqueda y filtrado ayuda a identificar la ejecución de esta herramienta en el sistema.

### Buscar instancias de archivos .kirbi

#### Búsqueda directa en el sistema de archivos

```powershell
cmd /c where /r c:\users *.kirbi
```

Buscar archivos con la extensión '.kirbi' en el sistema de archivos, específicamente en el directorio de usuarios. Los archivos .kirbi son tickets de Kerberos que pueden ser utilizados para la recolección de credenciales.

## Política de Grupo

### Buscar Ajuste de Token

#### Establecer la variable

```powershell
$event4703 = get-winevent -logname Security | Where-Object {$_.id -like '4703'}
```

#### Ver todos los eventos

```powershell
$event4703
```

#### Filtrar un poco

```powershell
$event4703 | Where-Object {$_.message -match 'SeDebugPrivilege'}
```

#### Expandir el mensaje

```powershell
$event4703 | Where-Object {$_.message -match 'SeDebugPrivilege'} | Select-Object -ExpandProperty message | findstr "Process"
```

#### Filtrar un poco más

```powershell
$event4703 | Where-Object {$_.message -match 'SeDebugPrivilege' -and $_.message -notmatch 'firefox.exe' -and $_.message -notmatch 'OneDriveSetup.exe'} | Select-Object -ExpandProperty message | findstr "Process"
```

Buscar eventos de ajuste de tokens de privilegio en el registro de eventos de seguridad de Windows (evento ID 4703), específicamente aquellos relacionados con el privilegio 'SeDebugPrivilege'. Este privilegio permite a un usuario depurar procesos del sistema, y su uso puede indicar actividades maliciosas de escalada de privilegios. Los filtros adicionales excluyen procesos legítimos como firefox.exe y OneDriveSetup.exe para reducir falsos positivos.

#### Enfoque en PowerShell

```powershell
$event4703 | Where-Object {$_.message -match 'SeDebugPrivilege' -and $_.message -match 'powershell.exe'} | Select-Object -ExpandProperty message | findstr "Process"
```