---
title:  DNS Exfiltration 🕸️
layout: default
has_toc: false
nav_order: 5
parent: Hunting an APT 👺
---

# Hunting an APT - **DNS Exfiltration**


{: .intro }
>La exfiltración de datos puede ocurrir utilizando protocolos de red comunes, como hemos visto en otros artículos de esta serie, pero esta vez revisaremos específicamente el DNS.

Los adversarios pueden robar datos exfiltrándolos a través de un protocolo de red no cifrado diferente al del canal de comando y control existente. Los datos también pueden ser enviados a una ubicación de red alternativa distinta del servidor principal de comando y control.

La exfiltración a través de DNS es especialmente insidiosa porque el tráfico DNS es una parte fundamental de la comunicación de red y a menudo no se supervisa tan estrictamente como otros tipos de tráfico. Los atacantes pueden codificar datos sensibles en consultas DNS aparentemente normales, que luego son enviadas a servidores controlados por ellos. Este método les permite sacar datos sin levantar sospechas, ya que el tráfico DNS es generalmente permitido a través de firewalls y otras defensas de red.

Para detectar y prevenir la exfiltración de datos a través de DNS, es esencial monitorear el tráfico DNS en busca de patrones inusuales, como un volumen inusualmente alto de consultas DNS o consultas a dominios que no han sido vistos antes. Implementar soluciones de seguridad que analicen el tráfico DNS en tiempo real y alerten sobre comportamientos anómalos puede ser una defensa efectiva contra este tipo de exfiltración de datos.

https://attack.mitre.org/techniques/T1048/003/

# **Búsqueda de Indicadores en DNS**

`index=botsv2 sourcetype=stream:dns 160.153.91.7`

![DNSAPT1.png](https://i.postimg.cc/MpFbWfQ0/DNSAPT1.png)

Podemos utilizar la fuente **`stream`** como nuestra primera referencia para los eventos DNS. En estos eventos, hay cuatro direcciones de sistemas. En el campo **`name`** podemos ver que se utiliza **`hildegardsfarm.com`**.

Podemos investigar más a fondo si revisamos este dominio con mayor detalle.

`index="botsv2"  sourcetype="stream:dns"  hildegardsfarm.com`

![DNSAPT2.png](https://i.postimg.cc/5NpSRR9R/DNSAPT2.png)]¡

Podemos ver el destino de los eventos. La mayoría se dirige a los servidores DNS de Google.

El tipo de mensaje de estos eventos son **`QUERY`** y **`RESPONSE`**. Cuando buscamos exfiltración de datos, nos enfocamos en aquellos eventos donde el tipo de mensaje está configurado como **`QUERY`**. Esto se debe a que el host interno enviará la consulta saliente con información incrustada en la consulta DNS que se enviará al adversario.

![DNSAPT3.png](https://i.postimg.cc/TYTcQ6xb/DNSAPT3.png)


`index="botsv2"  sourcetype="stream:dns"  hildegardsfarm.com message_type=QUERY
|table _time query src dest`

Podemos observar en el campoquery subdominios extraños que son parte de las consultas del dominio hildegardsfarm[.]com. Esto podría ser un indicio de exfiltración de datos o actividad maliciosa.

<a href="https://i.postimg.cc/2jQw45sm/DNSAPT4.png"><img src="https://i.postimg.cc/2jQw45sm/DNSAPT4.png" style="width:200%; height:200%;" /></a>


### URL Toolbox

Limitando la consulta que contiene subdominios de hildegardsfarm.com

`index="botsv2"  sourcetype="stream:dns"  hildegardsfarm.com message_type=QUERY query=*.hildegardsfarm.com
|eval query=mvdedup(query)
|eval list="mozilla"
|ut_parse_extended(query,list)
|ut_shannon(ut_subdomain)
|table src dest query ut_subdomain ut_shannon`

![DNSAPT5.png](https://i.postimg.cc/zvFF5dC3/DNSAPT5.png)

Usaremos la Caja de Herramientas de URL, que nos permite tomar dominios y URLs y descomponerlos en campos separados como puerto, subdominios y dominios de nivel superior.

Podemos observar que todos los subdominios tienen un puntaje de entropía alto. Esto nos indica que son generados automáticamente por un algoritmo de dominio.

### **Visualización de la Exfiltración de Datos a través de DNS**

Es importante tener en cuenta que el tráfico DNS saliente es más permisivo que un firewall. Sin embargo, existe una limitación en cuanto a la longitud de los paquetes que se pueden enviar. Si el paquete de DNS es demasiado largo, el firewall bloqueará el envío de datos. En este caso, se podría dividir en múltiples consultas DNS para enviarlo sin restricciones y evitar el firewall.

Añadiendo algunas direcciones de origen y destino en el comando **`stats`** y un conteo:

`index="botsv2"  sourcetype="stream:dns"  hildegardsfarm.com message_type=QUERY query=*.hildegardsfarm.com
| eval query=mvdedup(query)
| eval list="mozilla"
| ut_parse_extended(query,list)
| ut_shannon(ut_subdomain)
| eval sublen = length(ut_subdomain)
| stats count avg(ut_shannon) as avg_entropy avg(sublen) as avg_sublen stdev(sublen) as stdev_sublen by ut_domain src dest
| sort - count`


![DNSAPT6.png](https://i.postimg.cc/3NTFsMDP/DNSAPT6.png)

Tenemos estadísticas individuales para cada par de direcciones de origen y destino con un dominio de hildegadsfarm.com. Aquí tenemos un gran número de consultas DNS con un mismo subdominio, lo que indica una posible exfiltración de archivos a través de DNS.

### **Conclusiones**

Observamos el uso de DNS para la exfiltración de datos:

- Posiblemente un intento de eludir el firewall.
- No está claro si fue completamente exitoso, pero se intentó.

Cuatro sistemas fueron vistos haciendo referencia a la IP externa 160[.]153[.]91[.]7.

El DNS hacía referencia a un dominio llamado hildegardsfarm.com.

Las consultas DNS a este dominio tenían una alta entropía en el subdominio, un alto recuento de eventos y una baja desviación estándar, lo que podría ser indicativo de un túnel DNS.

La Inteligencia de Fuentes Abiertas (OSINT) indica que si bien la dirección IP actual del hildegardsfarm[.]com no es conocida, durante el tiempo del ataque la IP que se resolvía para el dominio era 160[.]153[.]91[.]7.

![DNSAPT7.png](https://i.postimg.cc/520SdS6N/DNSAPT7.png)

### Pasos a seguir 
1. **Añadir a la Lista de Observación o Lista de Bloqueo**
    
    Agrega la siguiente información a tu lista de observación o lista de bloqueo:
    
    - IP: 160[.]153[.]91[.]7.
    - Dominio: hildegardsfarm[.]com
    
    Esto nos permitirá monitorear o bloquear el tráfico asociado con estas direcciones IP y dominios, lo que puede ayudar a mitigar futuros intentos de exfiltración de datos.
    
2. **Monitorear la Entropía y Longitud de Subdominios en el Tráfico DNS**
    
    Mantener un monitoreo constante para identificar patrones de alto nivel de entropía, longitud de subdominios y baja desviación estándar en el tráfico DNS. Estos pueden ser indicativos de actividades de exfiltración de datos a través de DNS.
    
3. **Realizar Análisis de Tráfico en los Sistemas**
    
    Realizar un análisis de tráfico en los sistemas para establecer líneas de base de comunicación entre sistemas externos e internos. Es importante identificar y detectar anomalías en el tráfico, lo que puede indicar intentos de exfiltración de datos u otras actividades maliciosas.
