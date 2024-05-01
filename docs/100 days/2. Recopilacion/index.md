---
title: 2.  Recopilación y análisis de información 🧾
layout: default
has_toc: false
nav_order: 3
parent: 100 days challenge 🗻

---

# 2.  Recopilación y análisis de información sobre amenazas 🧾
---
## Índice 

- [2.1 Fuentes de inteligencia de amenazas](https://nottaroff.github.io/workspace/docs/100%20days/2.%20Recopilacion/#21-fuentes-de-inteligencia-de-amenazas-%EF%B8%8F) 
- [2.2 Técnicas para la recopilación de información.](https://nottaroff.github.io/workspace/docs/100%20days/2.%20Recopilacion/#22-técnicas-para-la-recopilación-de-información-)
- [2.3 Métodos analíticos.](https://nottaroff.github.io/workspace/docs/100%20days/2.%20Recopilacion/#23-métodos-analíticos-%EF%B8%8F)
- [2.4 Gestión de Datos](https://nottaroff.github.io/workspace/docs/100%20days/2.%20Recopilacion/#24-gestión-de-datos-)


---

## 2.1 Fuentes de inteligencia de amenazas. ♨️

Para asegurar una caza efectiva de amenazas, debemos de obtener una amplia fuente de inteligencia de amenzas que permita detectar y contrarrestar los riesgos de seguridad de manera eficaz. Estas fuentes suministran información clave acerca de las amenazas más recientes, los patrones de ataques, los indicadores que señalan compromisos (IoC) y firmas de malware.

| Algunas fuentes comunes:  |
|:-------------|
| ⭕ Informes de seguridad.|
| ⭕ Comunidades de seguridad y foros en línea.| 
| ⭕ Información compartida por organizaciones gubernamentales.| 
| ⭕ Resultados de investigaciones forenses de incidentes previos.| 
| ⭕ Datos de inteligencia de amenazas internas generados por herramientas de monitoreo de seguridad y análisis de registros.|


Algunas de las fuentes más importantes a las que recurre un equipo de seguridad antes de iniciar una caza de amenazas.

{: .detail}
**IOCs**: de Indicadores de Compromiso,  son evidencias que señalan un compromiso de red de un endpoint. Como por ejemplo: solicitudes de DNS inusuales, patrones anormales de tráfico de red, ataques de denegación de servicio (DDoS), inicios de sesión anormales, actividad de lectura de bases de datos inusual, manipulación de archivos… 

{: .detail}
**OAs**: Indicadores de Ataque. Es un conjunto de evidencias que apuntan hacia un ataque activo. Como por ejemplo comunicación a través de puertos no estándar, picos en el tráfico SMTP, charlas inter-host post-infección, intentos de conexión desde diferentes regiones geográficas y una tasa de eliminación de malware subóptima.

{: .detail}
**TTPs:**  Tácticas, Técnicas y Procedimientos. MITRE nos ofrece información sobre el ataque, NIST proporciona acciones o estrategias defensivas, independientemente del índice de la cadena de ataque o la trayectoria.

## 2.2 Técnicas para la recopilación de información. 🔧

El enfoque principal del Threat Hunting es el papel humano, aunque contar con acceso a tecnologías pertinentes y fiables es esencial.

Las tecnologías y herramientas esenciales incluyen:

{: .detail}
💠**Registro de Actividades de Endpoints en Servidores y Clientes**                                                                       
 Acceder a registros de ejecuciones de procesos, puertos de red, detalles de registro y eventos de acceso al sistema son requisitos estándar para la mayoría de las investigaciones.
 Por ejemplo, herramientas como OSQuery proporcionan acceso a datos de telemetría de terminales a través de consultas en lenguaje SQL.                                                                                                                                    
💠**Almacenamiento de Datos**
 Estos sistemas ofrecen almacenamiento y búsqueda de eventos a largo plazo. Por ejemplo, eventos recopilados de diferentes fuentes de red pueden enviarse a sistemas de almacenamiento de datos como Splunk o Elasticsearch para su análisis por parte del equipo de monitoreo de seguridad y los cazadores de amenazas.                                                                   
💠**Análisis Avanzado**  
    Facilita búsquedas escalables y avanzadas, así como funciones de estadísticas y aprendizaje automático. Herramientas como Splunk, Elasticsearch y plataformas como Apache Spark son ejemplos comunes.

Dependiendo del entorno y el alcance del hunting, el conjunto de herramientas del cazador de amenazas podría incluir otras herramientas especializadas. 
Por ejemplo, el uso de reglas *YARA* para investigar y capturar actividades sospechosas en endpoints, o el envío de reglas de Snort a herramientas de seguridad de red, como sistemas de detección de intrusiones, para capturar actividades de interés en la red.

## 2.3 Métodos analíticos. 🕵🏻‍♂️

Los enfoques analíticos son cruciales para extraer información valiosa de los datos recopilados durante la detección de amenazas. 

Algunas técnicas comunes son:
1. **Evaluación de comportamiento:** Detectar comportamientos inusuales en el tráfico de red o en las actividades de usuarios que puedan indicar actividad maliciosa.
2. **Correlación de datos:** Relacionar diversas fuentes de información para identificar conexiones y patrones que podrían pasar desapercibidos individualmente.
3. **Identificación de firmas:** Comparar datos recopilados con firmas de malware conocidas o indicadores de compromiso para detectar actividades maliciosas.
4. **Análisis de riesgo:** Valorar la gravedad y probabilidad de posibles amenazas para priorizar las acciones de respuesta.
5. **Seguimiento de tendencias:** Identificar cambios en el panorama de amenazas a lo largo del tiempo para ajustar las estrategias defensivas de manera proactiva.

## 2.4 Gestión de Datos 📇

Este apartado aborda cómo los datos se gestionan y estructuran desde la perspectiva del cazador de amenazas para facilitar su análisis.

[DATA-GOVERNANCE.png](https://i.postimg.cc/4x3ZPByR/DATA-GOVERNANCE.png)

### 📒Documentación de Datos (Data documentation)

Para realizar el análisis y la interpretación de los datos, es fundamental comprender qué datos se están recopilando y cómo se están estructurando. La documentación de datos nos proporciona una vision detallada de los elementos dde una base de datos, sistema de información o proyecto.  

Uno de los componentes clave de la documentación son los diccionarios de datos, estos recopilan nombres, definiciones y atributos sobre los datos, facilitando su comprensión y uso. Nos proporcionan el significado y el propósito de  los datos, su orientación sobre su interpretación y representación. También obtiene metadatos que ayudan a definir el alcance y las características de los elementos de datos, así como las reglas para su uso y aplicación.

La creación de un diccionario de datos es necesario para evitar lagunas de datos, mantener la consistencia en la recopilación y uso de datos y facilitar el análisis. También permite la aplicacion de las reglas que rigen la forma en la que se recopilan. 

### 🈴 Estandarización de Datos (Estandarización de Datos) 

La estandarización de datos es un proceso que nos establece una coherencia y eficacia en el análisis de la información recopilada de diversas fuentes. Se basa en el empleo de un Modelo de Información Común (CIM), que proporciona una estructura  para normalizar conjuntos de datos mediante un esquema. 

Este enfoque facilita la correlación de datos de diferentes orígenes, lo que permite a los investigadores identificar patrones y tendencias de manera más eficiente, sin la necesidad de crear consultas extensas para abordar las variaciones en la nomenclatura de los campos.


### 🏗️ Modelacion de Datos (Data Modeling)  

El modelo de datos determina la estructura de los datos y las relaciones entre ellos. Identificar estas relaciones es imporante para documentar eventos específicos que podrían vincularse a cadenas de eventos relacionadas con el comportamiento de los adversarios.

Es esencial documentar exhaustivamente los eventos de seguridad que se están recopilando, comprendiendo la estructura de cada evento y los objetos de datos que representan. Identificar las relaciones entre los eventos permite mapear las interacciones entre ellos y acelerar el desarrollo de análisis de datos. Una vez comprendidas estas relaciones, podemos modelar el comportamiento de los adversarios al mapear actividades específicas con eventos de seguridad. Esto nos permite detectar comportamientos sospechosos con mayor eficacia y tomar medidas preventivas de manera oportuna.

### 💯 Calidad de Datos (Data Quality)  

La calidad de los datos se refiere a su valor para los usos previstos en las operaciones, toma de decisiones y planificación. Si los datos necesarios para una tarea de búsqueda no cumplen con los requisitos específicos definido, no se consideran datos de calidad, ya que afectan el propósito previsto de los mismos. Identificar que los datos que se utilizarán no son de calidad permite identificar obstáculos que podrían afectar la detección de técnicas adversarias.

Para evaluar la calidad de los datos, se pueden utilizar diversas dimensiones, como la completitud, la consistencia y la puntualidad. Estas dimensiones ayudan a categorizar las deficiencias encontradas en los datos destinados a ser utilizados en tareas de búsqueda, facilitando la comunicación con los equipos encargados del mantenimiento de los datos.

