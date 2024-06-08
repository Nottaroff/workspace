---
title: 2. Ejecución remota de código en Web 🖱️
layout: default
has_toc: false
nav_order: 2
parent: Hunting in Network Environments 🥋 

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