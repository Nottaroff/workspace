---
title: 4. Hunting en entornos de red
layout: default
has_toc: false
nav_order: 5
parent: 100 days challenge 🗻

---

# Hunting en entornos de red 🛜
---
## Índice 

- [4.1 Técnicas de análisis de tráfico de red. 🧬](https://nottaroff.github.io/workspace/docs/100%20days/4.%20Hunting%20en%20entornos%20de%20red/#41-técnicas-de-análisis-de-tráfico-de-red-) 
- [4.2 Análisis de registros para seguridad en redes 🛡️](https://nottaroff.github.io/workspace/docs/100%20days/4.%20Hunting%20en%20entornos%20de%20red/#42-análisis-de-registros-para-seguridad-en-redes-%EF%B8%8F)
- [4.3 Búsqueda de amenazas 🕷️](https://nottaroff.github.io/workspace/docs/100%20days/4.%20Hunting%20en%20entornos%20de%20red/#43-búsqueda-de-amenazas-%EF%B8%8F)
    - [4.3.1 Ataques de Denegación de Servicio Distribuido (DDoS) ⛓️](https://nottaroff.github.io/workspace/docs/100%20days/4.%20Hunting%20en%20entornos%20de%20red/#431-ataques-de-denegación-de-servicio-distribuido-ddos-%EF%B8%8F)
    - [4.3.2 Threat Hunting de Dominios Sospechosos 🔗](https://nottaroff.github.io/workspace/docs/100%20days/4.%20Hunting%20en%20entornos%20de%20red/#432-threat-hunting-de-dominios-sospechosos-)
    - [4.3.3 Hunting de tráfico irregular 🧧](https://nottaroff.github.io/workspace/docs/100%20days/4.%20Hunting%20en%20entornos%20de%20red/#433-hunting-de-tráfico-irregular-)

---
El threat hunting  en entornos de red, implica la búsqueda activa y sistemática de actividades maliciosas o anomalías dentro de una red. La caza de amenazas en redes implica el uso de  herramientas y métodos para monitorear y analizar activamente:

- Tráfico de red
- Comportamientos del usuario
- Actividades del sistema

Esto puede incluir análisis de registros (logs) de red, análisis de tráfico, correlación de eventos, análisis de comportamiento anómalo de usuarios y sistemas, entre otros métodos.

## 4.1 Técnicas de análisis de tráfico de red. 🧬

Consiste en examinar el flujo de datos que circula a través de una red con el objetivo de identificar patrones sospechosos, anomalías o posibles amenazas de seguridad. Algunas técnicas de análisis de tráfico de red. 

|**Inspección de Paquetes** 📦|
|:-------------|
|Inspeccionar los paquetes que se transmiten a través de la red. C**ada paquete individual de datos que se transmite a través de la red. Se analizan tanto los encabezados como los contenidos de los paquetes en busca de signos de actividad maliciosa o comportamiento inusual. Esto puede incluir la identificación de patrones de ataque conocidos, como intentos de intrusión, escaneos de puertos o transferencias de archivos sospechosas.|

|**Análisis de Tráfico** ⛔|
|:-------------|
|En lugar de examinar paquete por paquete, el análisis de tráfico se centra en el tráfico agregado entre dos puntos de la red. Utiliza registros de flujo de red, como NetFlow o IPFIX, para obtener una visión general de las comunicaciones en la red. Esto permite identificar patrones de tráfico inusuales o sospechosos que pueden indicar una actividad maliciosa, como el tráfico excesivo hacia un servidor específico o la comunicación con direcciones IP conocidas por ser maliciosas.|

|**Análisis de Protocolos** 📋|
|:-------------|
|Esta técnica implica examinar el tráfico de red a un nivel más profundo, centrándose en los protocolos de comunicación utilizados. Se analizan los encabezados y los datos de los protocolos para identificar cualquier desviación del comportamiento esperado. Por ejemplo, se pueden detectar intentos de explotación de vulnerabilidades conocidas en un protocolo específico o el uso de comandos atípicos que podrían indicar un comportamiento malicioso.|

|**Análisis de Comportamiento** 🔰|
|:-------------|
|Esta técnica implica monitorear el tráfico de red a lo largo del tiempo para establecer un patrón de comportamiento normal y detectar cualquier desviación significativa. Se utilizan algoritmos de aprendizaje automático y análisis estadístico para identificar anomalías que podrían indicar una amenaza de seguridad, como cambios repentinos en los patrones de comunicación, picos de tráfico inusuales o actividad sospechosa en horarios no habituales.|


## 4.2 Análisis de registros para seguridad en redes 🛡️

Para la detección y mitigación de posibles amenazas y vulnerabilidades dentro de una infraestructura de red. Podemos usar las diferentes herramientas mencionadas a continuacion para recopilar datos críticos que ayuden a identificar patrones sospechosos, anomalías o posibles intrusiones.

{: .detail }
>**Captura de Paquetes**
>- Intercepta y almacena paquetes de datos en tiempo real para su análisis.
>- **Herramientas**: Moloch, Tcpdump, Wireshark, tshark.

{: .detail }
>**Registro de Proxy**
>- Registra las solicitudes de usuarios y aplicaciones en la red, incluyendo solicitudes web y de servicios.
>- **Herramientas**: Squid, Producto de Proxy Comercial.

{: .detail }
>**Registro de DNS**
>- Registra actividades basadas en DNS, como comunicaciones C2 y exfiltración de datos.
>- **Herramientas**: Servidor DNS, Datos recopilados de DNS de la red, Basado en el Host (Sysmon 10), Registro de DNS Pasivo.

{: .detail }
>**Flujo de Red**
>- Analiza metadatos de flujo de tráfico para visualizar patrones y volumen de tráfico en la red.
>- **Herramientas**: Silk, Nfsen & Nfdump.

{: .detail }
>**Sistema de Detección de Intrusos en la Red (NIDS)**
>- Detecta tráfico malicioso en la red, requiriendo acceso promiscuo para analizar todo el tráfico.
>- **Herramientas**:Snort, Suricata, Bro, Producto NIDS Comercial.

## 4.3 Búsqueda de amenazas 🕷️

### 4.3.1 Ataques de Denegación de Servicio Distribuido (DDoS) ⛓️

---
Un ataque de Denegación de Servicio Distribuido (DDoS) ocurre cuando múltiples máquinas atacantes intentan sobrecargar a las máquinas víctimas.
A menudo, los ataques DDoS se utilizan como una cortina de humo. Otros tipos de ataques aprovechan la confusión para pasar desapercibidos.

Algunos factores que nos pueden indicar un ataque DDoS:

{: .importance }
>- Indisponibilidad de sitios web.
>- Rendimiento lento de la red.
>- Conmutación por error.
>- Sistemas internos operando al máximo de su capacidad.
>- Sobrecarga de sistemas de seguridad de red (SIEM, IPS/IDS).
>- Disponibilidad inesperada del servidor (Sin actualizaciones pendientes o reinicios programados).
>- Direcciones IP conectadas a muchos puertos diferentes.


### 4.3.2 Threat Hunting de Dominios Sospechosos 🔗

---
Algunos de los motivos por las cuales un dominio puede considerarse sospechoso:

{: .importance }
>- Dominios aleatorios generados por un DGA (Domain Generation Algorithm).
>- Direcciones IP ocultas dentro de un texto o código.
>- Extensiones de dominio (TLDs) inusuales.
>- Dominios inexistentes.
>- Dominios conocidos como maliciosos.

La información sobre un dominio, como quién lo posee, su historial de actividad y otras asociaciones, se puede encontrar en diferentes lugares, como registros DNS, correos electrónicos y registros de actividad en la web. Es importante incluir esta información en el proceso de búsqueda de amenazas para detectar posibles riesgos y protegerse contra actividades maliciosas en línea.


**URLs**

Las URL son indicadores comunes de compromiso  porque a menudo se utilizan como componente de ataques de phishing, spam y malware.

Los ataques basados en URL incluyen:

{: .detail}
>- **Redirección**                                                                                                                 
>  Aprovechamiento de la falta de familiaridad de los usuarios con el funcionamiento de las URL.                                                                   
>
>- **Typosquatting**                                                                                                           
>  Colocación de sitios de phishing en URL diseñadas para parecerse a sitios web legítimos.
>
>- **Codificación de escape**                                                                                                                 
>  El estándar que define las URL distingue entre caracteres no reservados y reservados. Esto puede ser utilizado para ataques de inyección.
>

**Respuestas HTML Sospechosas**

El tamaño de la respuesta HTML puede ser un indicador clave de actividad maliciosa. En particular, en los ataques de inyección SQL, las respuestas del servidor tienden a ser significativamente grandes debido a los datos exfiltrados que se incluyen en la respuesta.

Cuando se busca identificar posibles ataques contra servidores web, los registros de estos servidores son una herramienta valiosa. Al analizar estos registros, se pueden observar ciertos patrones que podrían indicar actividades sospechosas:

{: .detail}
>- Respuestas HTML de gran tamaño podrían sugerir intentos de inyección SQL y exfiltración de datos, ya que los atacantes intentan obtener información sensible de la base de datos del servidor.
>
>- Los errores 500 Internal Server y los errores 501 Header Value pueden indicar escaneos en busca de vulnerabilidades en la aplicación web. Estos errores pueden ser el resultado de intentos de explotar posibles debilidades en el código del servidor.

Es importante tener en cuenta que los datos de los registros del servidor web pueden ser manipulados por los atacantes para intentar ocultar sus acciones. Por lo tanto, es crucial realizar un análisis exhaustivo y estar atento a cualquier actividad inusual que pueda indicar una brecha de seguridad.

### 4.3.3 Hunting de tráfico irregular 🧧

---

Las irregularidades en el tráfico de red son indicadores útiles para los cazadores de amenazas. Los autores de malware utilizan una variedad de técnicas para ocultar el tráfico de ataque de comando y control.

{: .detail}
> - Protocolos mal utilizados
> - Desajustes entre puertos y aplicaciones. Por ejemplo, tráfico encriptado a través de puertos como el 80, que normalmente se asocian con HTTP.

El intento de ejecución de web shells es un vector de ataque inicial común por parte de los cibercriminales.

Es crucial aprender a detectarlos tempranamente. Algunas de las detecciones que debemos tener en cuenta son:

---

**Protocolos mal utilizados**

Los protocolos comunes a menudo se utilizan incorrectamente para el ataque de control y comando, ya que es menos probable que sean detectados y bloqueados, debido a su criticidad y necesidad para otras aplicaciones.

---

**Desajustes entre puertos y aplicaciones**

Los números de puerto están en el rango de 0 a 65535:

{: .detail }
>- 0-1023: Puertos del sistema.
>- 1024-49151: Puertos de usuario o puertos registrados.
>- 49152-65535: Puertos dinámicos o privados.  

Los autores de malware pueden utilizar puertos comunes o protocolos personalizados para intentar hacer que el tráfico malicioso parezca legítimo. El malware puede mezclar y combinar puertos comunes/no comunes y protocolos comunes/personalizados. Es importante observar los datos de registro para encontrar anomalías y patrones sospechosos que puedan indicar actividades maliciosas.

---

**Web shells**

Las web shells son una forma ilícita de obtener acceso a una terminal de una computadora a través de una página web dinámica en el lado del servidor.                                                                            
Existen varios tipos de web shells, algunos simples que son fáciles de detectar. Sin embargo, los shells web sofisticados incluyen métodos para interactuar con la consola y editar archivos, lo que los hace más difíciles de identificar. Algunos shells web han implementado mecanismos específicamente diseñados para evadir la detección, como la compresión y la encriptación para la obfuscación.
|Encontrar shells web en servidores web empresariales puede ser difícil debido al gran volumen de datos. Por suerte, existen herramientas para ayudar a detectar shells web personalizados: 

{: .detail }
>- Parte de suites de caza de amenazas o escáneres de vulnerabilidades como Nessus.
>- Herramientas independientes como Webshell Scan, Scalp y Neopi.

---

**Exfiltración de datos**

Detectar la exfiltración de datos es un proceso complejo, especialmente si no se cuenta con una buena identificación del tráfico saliente normal de la organización. La mayoría de las veces, la exfiltración de datos involucra nodos de transporte en lugar de fuentes.                

Pueden utilizarse tanto canales overt (manifiestos) como covert (encubiertos) para la exfiltración de datos, incluyendo:

{: .detail }
>- Multidifusión IP.
>- Técnicas basadas en el navegador, como la precaptación DNS.
>- Tunelización a través de protocolos como DNS y HTTP.
>- Transporte de datos ocultos en otros protocolos como NTPv3 e ICMP. 

Las soluciones de Protección de Pérdida de Datos (DLP) pueden pasar por alto eventos de exfiltración debido a diversas razones:

{: .detail }
>- Los exploits de exfiltración suelen ser pasos intermedios en un ataque y no siempre afectan a los datos protegidos por DLP.
>- Las redes de explotación distribuida son difíciles de detectar para las soluciones de DLP.

Para detectar la exfiltración de datos, es importante monitorear de cerca los patrones de tráfico y utilizar técnicas de análisis avanzadas para identificar actividades sospechosas en la red.

---