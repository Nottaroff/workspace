---
title: 3. Enlaces y Archivos de Phishing 🎣
layout: default
has_toc: false
nav_order: 3
parent: Hunting in Network Environments 🥋 
---


## Enlaces y Archivos de Phishing 🎣

{: .importance }
> Utilizaremos el índice winlogbeat-* y buscaremos indicadores de enlaces maliciosos y adjuntos que se abrieron o descargaron desde las estaciones de trabajo de los empleados el 3 de julio de 2023.
    
Los correos electrónicos de phishing que contienen enlaces maliciosos o adjuntos de cargas útiles de malware se descargan o abren directamente desde el cliente de correo electrónico antes de ejecutarse. Dado esto, buscaremos los siguientes comportamientos:

- Archivos descargados usando un navegador web.
- Archivos abiertos desde un cliente de correo electrónico ( Outlook).

1. Archivos Descargados usando Chrome
Utilizando la pestaña Discover, nos enfocaremos en los enlaces de phishing descargados utilizando un navegador web. Mediante la siguiente consulta KQL, buscaremos creaciones de archivos (Evento de Sysmon ID 11) generadas por chrome.exe:

**`host.name: WKSTN-* AND process.name: chrome.exe AND winlog.event_id: 11`**

Activaremos los filtros siguientes:
- winlog.computer_name
- winlog.event_data.User
- file.path

![PH1.png](https://i.postimg.cc/X7rMR2Cf/PH1.png)

Basándonos en los resultados, podemos ver que los siguientes usuarios en sus respectivas estaciones de trabajo han descargado archivos inusuales.

| Usuario | Estación de Trabajo | Archivos Descargados |
| --- | --- | --- |
| THREATHUNTING\clifford.miller | WKSTN-1 | C:\Users\clifford.miller\Downloads\chrome.exe |
|  |  | C:\Users\clifford.miller\Downloads\microsoft.hta |
| THREATHUNTING\bill.hawkins | WKSTN-2 | C:\Users\bill.hawkins\Downloads\update.exe |
|  |  |  |

Deberemos de analizar en profundidad si realmente son programas maliciosos.

**Archivos Abiertos usando Outlook**

Buscaremos adjuntos de phishing abiertos utilizando un cliente Outlook. Utilizaremos la siguiente consulta KQL para rastrear archivos creados por el cliente Outlook:

**`host.name: WKSTN-* AND process.name: OUTLOOK.EXE AND winlog.event_id: 11`**

![PH2.png](https://i.postimg.cc/8kKQn8jk/PH2.png)

Podemos observar como se abrió un archivo adjunto llamado **Update.zip,** que se almacenó temporalmente en el directorio **\AppData\Local\Microsoft\Windows\INetCache\Content.Outlook.** Esta cadena puede usarse como sintaxis de consulta para buscar archivos creados desde el directorio de caché de Outlook.

Para confirmar el contenido del archivo zip, podemos usar la siguiente consulta KQL para encontrar eventos relacionados con él:

**`host.name: WKSTN-* AND *Update.zip*`**

![PH3.png](https://i.postimg.cc/bvxf6s24/PH3.png)

Con ello, confirmamos que existe un archivo LNK. Un archivo de acceso directo (.lnk) archivado en un zip es una amenaza típica que los actores de amenazas utilizan como archivo adjunto de malware. 

Siguiendo la mentalidad de un cazador de amenazas, el siguiente paso de esta investigación es identificar el proceso generado por el archivo de acceso directo. Esto se puede hacer siguiendo los eventos generados por update.lnk.

---