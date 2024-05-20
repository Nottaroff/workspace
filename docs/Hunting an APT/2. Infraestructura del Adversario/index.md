---
title: Infraestructura del Adversario 🌍
layout: default
has_toc: false
nav_order: 2
parent: Hunting an APT 👺
---

# Hunting an APT - **Infraescrutura del adversario** 


{: .intro }
> Un grupo de ciberactores que utilizan una infraestructura llamada "Taedonggang APT" o TAP'T ha estado llevando a cabo actividades de explotación de redes informáticas contra organizaciones.

Las infraestructuras expuestas a Internet, como los servidores web, son objetivos típicos para este grupo. Su infraestructura a menudo comparte certificados SSL autofirmados.

El grupo depende de servidores VPS ubicados en países con fuertes políticas de privacidad (como Alemania) en apoyo de sus operaciones de red informática.

Informes recientes de otras organizaciones afectadas han identificado la dirección IP  45[.]77[.]65[.]211 como parte de su infraestructura.

T1583.003 [Adquirir Infraestructura: Servidor Virtual Privado](https://attack.mitre.org/techniques/T1583/003/)

Se ha establecido infraestructura adicional más allá de lo que conocemos. Los adversarios pueden alquilar servidores virtuales privados (VPS) que pueden ser utilizados durante el objetivo. Existen una variedad de servicios en la nube. Al utilizar un VPS, los adversarios pueden dificultar la vinculación física de las operaciones a ellos. El uso de la infraestructura en la nube también puede facilitar a los adversarios la provisión, modificación y cierre rápido de su infraestructura.

### **Identificando la Infraestructura del Atacante**

Lo único que sabemos es la dirección IP externa. Vamos a verificar en Splunk las referencias de las conexiones TCP con esta IP y vamos a centrarnos en el tráfico SSL, para comprobar qué certificado están utilizando.

`**index= botsv2 sourcetype=stream:tcp dest_ip=45.77.65.211**`

![APTINF001.png](https://i.postimg.cc/Y2JzHBCC/APTINF001.png)

Podemos observar como tenemos algunos campos SSL que podemos verificar en Splunk.


![APTINF002.png](https://i.postimg.cc/8zGd7dW8/APTINF002.png)


Podemos ver diferentes hashes  de certificados de las conexiones de nuestras 4 direcciones de origen distintas.

Podemos verificar estos hashes en OSINT para ver si alguno de estos certificados es malicioso.

Si buscamos el valor del certificado en Censys, una Plataforma de Inteligencia para la Caza de Amenazas y la Gestión de la Superficie de Ataque, podemos marcar este certificado como no confiable. Si retrocedemos en el tiempo, veremos que este certificado fue utilizado en múltiples servidores.

![APTINF003.png](https://i.postimg.cc/nMbzwkZn/APTINF003.png)

![APTINF004.png](https://i.postimg.cc/jdPQq3DQ/APTINF004.png)

Utilizando OSINT para Identificar la Geolocalización de la IP

La dirección IP presente en el sistema está ubicada en Alemania, lo que indica que estos VPS se están creando en Alemania.

<div style="text-align:center;">
    <img src="https://i.postimg.cc/fW3fpRZP/APTINF005.png" alt="APTINF005" width="50%">
</div>



### Conclusión

El adversario tiene al menos cuatro servidores adicionales desplegados. Podemos identificar los servidores al coincidir con el hash de los certificados SSL.

Si encontráramos artefactos en cazas anteriores, podrían aplicarse a fases de la cadena de ataque previas a la explotación (PRE) para identificar infraestructura.

Buscar infraestructura del atacante sin pistas adicionales es poco aconsejable.

Las direcciones IP y los dominios no son las únicas pistas de infraestructura disponibles, los certificados también proporcionan información.

La OSINT es invaluable para ayudar a identificar infraestructura adicional porque es probable que su organización no tenga la imagen completa por sí misma.

### Infraestrucutra del atacante

![APTINF006.png](https://i.postimg.cc/T1W19szk/APTINF006.png)

### ¿Cómo debemos proceder?

1. Utilizar acciones de flujo de trabajo o automatización para recopilar y buscar OSINT sobre la infraestructura del atacante.
2. Identificar sitios OSINT de valor.
3. Preferiblemente, no depender de una única fuente; es importante corroborar las fuentes.
4. Continuar monitoreando los hashes de los certificados y alertar cuando se encuentren.
5. Colocar en una lista de vigilancia (watchlist) las direcciones IP y los dominios identificados más allá de los artefactos encontrados en sus sistemas locales.
6. Poner en una lista de vigilancia los cuatro IPs con el mismo certificado para evitar que el adversario simplemente traslade su ataque a alguno de estos otros sistemas.