---
title:  Data Staging 🕵🏻
layout: default
has_toc: false
nav_order: 8
parent: Hunting an APT 👺
---

# Hunting an APT - **Data Staging** 🕵🏻


{: .intro }
>Los adversarios pueden organizar datos recopilados de múltiples sistemas en un lugar central o directorio en un solo sistema antes de la exfiltración. Los datos pueden mantenerse en archivos separados o combinarse en uno solo. 


<div style="display: flex; align-items: center;">
    <div style="flex: 1;">
        <p>Durante la caza deberemos de considerar lo siguiente:</p>
        <ul>
            <li>Identificar qué conjuntos de datos (tipos de fuente) podrían ayudarnos a identificar los datos que se están organizando.</li>
            <li>Observar los flujos de tráfico que podrían indicar la organización de datos.</li>
            <li>Buscar qué tipo de datos podrían encontrarse donde se estén organizando los datos.</li>
            <li>Identificar algunos lugares probables donde se podrían organizar los datos.</li>
            <li>Estar atentos a cualquier actividad posterior que indique que los datos organizados están siendo exfiltrados.</li>
            <li>Investigar qué cuentas de usuario podrían utilizarse para organizar los datos.</li>
        </ul>
    </div>
    <div style="flex: 1; text-align: center;">
        <img src="https://i.postimg.cc/tTGby05C/TM.png" alt="TM.png">
       <p><a href="https://attack.mitre.org/techniques/T1074/">https://attack.mitre.org/techniques/T1074/</a></p>
    </div>
</div>

**Investigar Archivos de Oficina**

Primero, comenzaremos a identificar conjuntos de datos de interés. En el entorno de archivos de oficina los más destacables son **.pdf**, **.doc**, **.xls**, y potencialmente **.tgz**. 
Esta última es una extensión de archivo comúnmente utilizada para indicar un archivo de archivo comprimido.
Realizaremos una búsqueda a los tipos de fuente que hacen referencia a estos tipos de archivos de interés.

```
index="botsv2" (.pdf OR .tgz OR .doc OR .xls)
| stats count by sourcetype
| sort - count
```

![DL1.png](https://i.postimg.cc/7LjT1LNP/DL1.png)

Stream es el tipo de fuente más grande basado en nuestra búsqueda.
 El Protocolo de Bloque de Mensajes de Servidor (SMB) es un protocolo de red utilizado para compartir archivos, impresoras y otros recursos en una red. Se usa comúnmente en entornos de Windows y permite el intercambio y la comunicación entre computadoras en una red. 

La idea de que los archivos de datos se muevan a través de la red hace que "stream" sea un lugar atractivo para comenzar, a pesar del gran número de eventos.

```
index="botsv2" (.pdf OR .tgz OR .doc OR .xls) sourcetype="stream:smb"
| stats count by src_ip dest_ip
| sort - count
```

![DL2.png](https://i.postimg.cc/ZYp6c6gG/DL2.png)

La dirección IP de destino para compartir archivos (10.0.1.10) indica que todas las estaciones de trabajo están comunicándose con el servidor llamado "venus". También podemos utilizar la información del centro de activos para identificar las estaciones de trabajo según las 3 direcciones IP fuente únicas.

- 10.0.4.4 — máquina anfitriona: maclory-air13, propietario: Mallory Kraeusen
- 10.0.2.107 — máquina anfitriona: wrk-btun, propietario: Billy Tun
- 172.16.0.1 — ¿Servidor Jupiter??

También vamos a examinar cuándo tuvieron lugar estas actividades de intercambio de archivos en toda la red.

```
index="botsv2" (.pdf OR .tgz OR .doc OR .xls) sourcetype="stream:smb"
| eval uniq=src_ip." ".dest_ip
| timechart count by uniq
```
![DL3.png](https://i.postimg.cc/7hkGcQcp/DL3.png)

**Investigar el Conjunto de Datos SMB**

Vamos a examinar el primer archivo (31564-pdf.pdf) de los resultados de la búsqueda.

```
index="botsv2" 31564-pdf.pdf sourcetype="stream:smb"
```
![DL4.png](https://i.postimg.cc/cHYtFNDR/DL4.png)


Si observamos el campo flow_id, solo hay un flow_id (d7370639-8ca9-40d3-a5f8-dd6547d4ff99), lo que indica que los tres eventos ocurrieron dentro de la misma transacción. Podemos tomar este flow_id que tiene 3 eventos asociados y buscar todos los comandos dentro de ese flujo.

```
index="botsv2" sourcetype="stream:smb" flow_id=d7370639-8ca9-40d3-a5f8-dd6547d4ff99
| stats count by command
| sort - count
```
![DL5.png](https://i.postimg.cc/251ZBWhX/DL5.png)
Dado que el comando "sm2 read" tiene la mayor cantidad de recuentos, podemos investigarlo primero y luego continuar con los siguientes en la cadena. Deberíamos tener una idea de quién está comunicándose con quién (IP de origen y destino) y la cantidad de datos que se están intercambiando.

```
index="botsv2" sourcetype="stream:smb" flow_id=d7370639-8ca9-40d3-a5f8-dd6547d4ff99  command="smb2 read"
| stats count sum(bytes_in) AS b_in sum(bytes_out) AS b_out by src_ip dest_ip
| eval mb_in=round((b_in/1024/1024),2)
| eval mb_out=round((b_out/1024/1024),2)
| fields - b_in b_out
```

![DL6.png](https://i.postimg.cc/jSdNtm5T/DL6.png)

Sabemos que la dirección IP 10.0.2.107 corresponde a la estación de trabajo de Billy Tun según la información del centro de activos, y está comunicándose con 10.0.1.101, que es el servidor Venus. Se han enviado aproximadamente 2 MB de datos desde la máquina de Billy al servidor, mientras que se han enviado 1.2 GB de datos desde el servidor a la estación de trabajo de Billy. 

Eso parece ser una cantidad considerable de datos que se están colocando en la estación de trabajo. 
Veamos otros comandos para ver si se pueden detectar patrones similares.

```
index="botsv2" sourcetype="stream:smb" flow_id=d7370639-8ca9-40d3-a5f8-dd6547d4ff99  command="smb2 create"
| stats count sum(bytes_in) AS b_in sum(bytes_out) AS b_out by src_ip dest_ip
| eval mb_in=round((b_in/1024/1024),2)
| eval mb_out=round((b_out/1024/1024),2)
| fields - b_in b_out
```

![DL7.png](https://i.postimg.cc/Z57NRHBd/DL7.png)

Los tamaños de los archivos que se están creando parecen ser bastante pequeños y podemos suponer que son solo los contenedores que se están creando. Veamos también "sm2 close".

```
index="botsv2" sourcetype="stream:smb" flow_id=d7370639-8ca9-40d3-a5f8-dd6547d4ff99  command="smb2 close"
| stats count sum(bytes_in) AS b_in sum(bytes_out) AS b_out by src_ip dest_ip
| eval mb_in=round((b_in/1024/1024),2)
| eval mb_out=round((b_out/1024/1024),2)
| fields - b_in b_out
```

![DL8.png](https://i.postimg.cc/02vDHb1b/DL8.png)

Es evidente que los datos están saliendo del servidor y se están moviendo hacia la estación de trabajo de Billy.

**Investigar el Conjunto de Datos FTP**

Retomando nuestra búsqueda inicial, podemos examinar los datos del FTP.

```
index="botsv2" 31564-pdf.pdf source="stream:ftp"
```

![DL9.png](https://i.postimg.cc/4N1VCsXw/DL9.png)

Podemos ver que la estación de trabajo de Billy (10.0.2.107) subió exitosamente el archivo .pdf a 160.153.91.7. Ahora estamos viendo la exfiltración de los archivos a través de FTP. Si hubiéramos realizado otras búsquedas, ya podríamos haber observado estas actividades. Si no, esto podría ser un buen indicio para empezar a buscar otros archivos que podrían haber sido exfiltrados a través de protocolos alternativos como FTP.

**Paso 4: Resumiendo lo que hemos aprendido**

Observando los datos de SMB, descubrimos que una gran cantidad de documentos de oficina (principalmente archivos PDF) se trasladaron a una estación de trabajo (10.0.2.107) desde un servidor (10.0.1.101). Después de esto, también vimos actividades de FTP en la estación de trabajo transfiriendo datos a un servidor externo (160.153.91.7). Basándonos en esto, podemos confirmar nuestra hipótesis de que nuestro adversario está utilizando una etapa de preparación de datos antes de la exfiltración.

[![DL10.png](https://i.postimg.cc/fyfthfQk/DL10.png)](https://postimg.cc/hQhPLxjq)

Basándonos en estos hallazgos, aquí están las acciones que deberíamos de realizar>

- La comunicación entre la estación de trabajo y el servidor es perfectamente normal, por lo que podría ser recomendable un análisis de anomalías (comando de estadísticas y observación de bytes_entrantes/bytes_salientes, conteo de eventos, nombres de archivos comparados con el comportamiento base).
- El registro de puntos finales para ver los datos escritos en el sistema de archivos podría ser útil.
- También sería útil el registro de la red para transferencias entre enclaves.
- Los datos de la red fueron la única forma de ver esto según nuestros registros, y SMB no proporciona toda la fidelidad que podríamos desear.
- Buscar actividades posteriores como transferencias de archivos a direcciones externas o escrituras a USB.