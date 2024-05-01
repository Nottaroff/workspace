---
title: 🥋 Ejemplos de Hunting en entornos de red 
layout: default
has_toc: false
nav_order: 6
parent: 100 days challenge 🗻
has_children: false

---
# 🥋 Ejemplos prácticos de Hunting en entornos de red 

---
## Índice 

- [Command and Controls over DNS 🏷️](https://nottaroff.github.io/workspace/docs/100%20days/Ejemplos%20prácticos%20Hunting%20en%20Red/#command-and-controls-over-dns-%EF%B8%8F) 

- [Ejecución remota de código en Web 🖱️](https://nottaroff.github.io/workspace/docs/100%20days/Ejemplos%20prácticos%20Hunting%20en%20Red/#ejecución-remota-de-código-en-web-%EF%B8%8F) 

- [Enlaces y Archivos de Phishing 🎣](https://nottaroff.github.io/workspace/docs/100%20days/Ejemplos%20prácticos%20Hunting%20en%20Red/#enlaces-y-archivos-de-phishing-) 

## Command and Controls over DNS 🏷️
---

Vamos a ver un ejemplo de detección de la táctica de Comando y control al DNS.

{: .detail }
>Para recrear la simulación he utilizado el índice de packetbeat-* para buscar posibles C2 a través de DNS el 3 de julio de 2023. Además, del índice winlogbeat-* para correlacionar las consultas DNS y así identificar el proceso malicioso que lo genera. 

El C2 a través de DNS, o más precisamente Comando y Control a través de DNS, es una técnica utilizada por los adversarios donde se utilizan los protocolos DNS para establecer un canal de Comando y Control. En esta técnica, los adversarios pueden disfrazar sus comunicaciones de C2 como consultas y respuestas DNS típicas, eludiendo las medidas de seguridad de la red. Dado esto, buscaremos patrones de consulta DNS inusuales basados en lo siguiente:

- Alto recuento de subdominios únicos.
- Solicitudes DNS inusuales basadas en tipos de consulta (MX, CNAME, TXT).

Vamos a realizar una consulta KQL para listar todas las consultas DNS, exluyendo la busqueda de DNS inversa:

**`network.protocol: dns Y NO [dns.question.name](http://dns.question.name/): *arpa`**


![ELK-1.png](https://i.postimg.cc/c4yYMKWQ/ELK-1.png)



Se puede observar que un dominio inusual **(golge[.]xyz)** consultó 2191 subdominios únicos, lo que puede indicar una posible actividad de C2 a través de DNS proveniente de **WKSTN-1**. 

Veamos más en profundidad el ataque: Haremos una consulta sobre el dominio y el host comprometido.

**`network.protocol: dns Y NO [dns.question.name](http://dns.question.name/): *arpa Y dns.question.registered_domain: golge.xyz Y [host.name](http://host.name/): WKSTN-1`**

![ELK-2.png](https://i.postimg.cc/mZFCHYvL/ELK-2.png)


Se pueden observar varias caracteristicas de actividad sospehosa:

{: .importance }
>- Utilización de subdominios hexadecimales.
>- Consultas TXT y MX inusuales para el dominio golge.xyz.
>- Consultas CNAME que podrían ser utilizadas para enmascarar la verdadera dirección de los servidores involucrados.
>- La presencia de múltiples consultas a este dominio inusual en diferentes tipos de registros DNS en un corto periodo de tiempo
>- La omisión de nombres de dominio inversos.


![ELK-3.png](https://i.postimg.cc/yd2RGxZC/ELK-3.png)

Ahora que tenemos suficiente información, podemos correlacionar esta actividad en winlogbeat-* para identificar el proceso que ejecuta las solicitudes DNS utilizando la siguiente consulta KQL:

![ELK-4.png](https://i.postimg.cc/T1mbvxVL/ELK-4.png)


Basado en los resultados, parece que todas las conexiones a 167[.]71[.]198[.]43:53 son generadas por nslookup.exe. 

Para continuar con la correlación de eventos, utilicemos "View surrounding documents" para ver los eventos posteriores relacionados con esta actividad.


![ELK-5.png](https://i.postimg.cc/02YSt85h/ELK-5.png)

Con ello podemos confirmar la sospecha de C2 a través de DNS. S

iguiendo el enfoque de un cazador de amenazas, el siguiente paso de esta investigación es identificar los eventos generados por el proceso principal de nslookup.exe que estableció el C2 a través de DNS. Esto permitirá rastrear los eventos antes de que se estableciera una conexión C2 exitosa. Además, se observarán los comandos posteriores ejecutados por el proceso principal, ya que se espera que se ejecuten comandos remotos una vez que se haya confirmado que la conexión C2 está activa.

![ELK-6.png](https://i.postimg.cc/XvPMT670/ELK-6.png)


{: .importance }
> También se puede identificar un tráfico DNS inusual con el campo de network.bytes. Las consultas DNS suelen ser cortas,, pero como hemos visto anteriorme, el subdominio se utilizó para manejar una cadena hexadecimal larga para la conexión C2. Por ello, podemos utilizar también el tamaño de solicitud/respuesta para determinar posibles anomalías dentro del tráfico DNS.

---

## Ejecución remota de código en Web 🖱️

{: .importance }
> Como ejemplo, en el siguiente escenario, utilizaremos el índice packetbeat- y buscaremos ataques a nuestra aplicación web (web01).

**Los ataques a aplicaciones web generalmente comienzan con intentos de enumeración y continúan con la explotación de vulnerabilidades descubiertas.**
Buscaremos comportamientos que concidan con este patrón.

Para comenzar la búsqueda, utilizaremos la Biblioteca de Visualización y crearemos una tabla de visualización utilizando Lens.

Configuramos el Índice de tabla (packetbeat), Filas (source.ip y http.response.status_code) y Métricas (conteo).
Utilizaremos una la consulta KQL para listar todas las conexiones de red de entrada al servidor web:

**`host.name: web01 AND network.protocol: http AND destination.port: 80`**

web01: es la web de ejemplo
network.protocol: Para establecer el protocolo http
destination.port: El puerto utilizado.


![ELKW1.png](https://i.postimg.cc/Prz9DBYQ/ELKW1.png)

Se puede observar que la consulta establece un alto conteo de códigos de estado 404, lo que indica un intento de enumeración de directorios por parte de la IP **167.71.198.43**, ya que el ataque produce muchos resultados de "Página no encontrada" debido a su comportamiento de intentar adivinar puntos finales válidos.

Para comprender mejor el ataque, podemos continuar la investigación utilizando la pestaña Discover con la  consulta centrada en el código de estado 404 y la dirección IP del atacante. 
Utilicemos la siguiente consulta KQL en la pestaña Discover:

`host.name: web01 AND network.protocol: http AND destination.port: 80 AND source.ip: 167.71.198.43 AND http.response.status_code: 404`

![ELKW2.png](https://i.postimg.cc/FHrqVDx5/ELKW2.png)

![ELKW3.png](https://i.postimg.cc/rFL7K80p/ELKW3.png)

Se puede ver que el atacante utilizó Gobuster para enumerar los directorios en la aplicación web y eventualmente se centró en el directorio /gila, lo que podría indicar que el atacante está intentando explotar dicha aplicación.

Para continuar, reemplacemos la consulta KQL con los códigos de estado 200, 301 y 302 para enfocarnos en los puntos finales válidos accedidos por el atacante.

`host.name: web01 AND network.protocol: http AND destination.port: 80 AND source.ip: 167.71.198.43 AND http.response.status_code: (200 OR 301 OR 302)`

![ELKW4.png](https://i.postimg.cc/9X9vm4fS/ELKW4.png)

Podemos concluir con las siguientes hipotesis:

1. Hemos detectado el objetivo del atacante, en este caso:  /gila.
2. El atacante utilizó un código PHP sospechoso en el campo User-Agent. El código utiliza x como un parámetro GET para ejecutar comandos del host a través de la función system.
3. Por último, el atacante utilizó el parámetro x para ejecutar comandos del host.

Visto los comandos ejecutados se puede concluir que el atacante comprometió con éxito el servidor web, explotando una vulnerabilidad de Ejecución Remota de Código en la aplicación web Gila.

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