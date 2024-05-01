---
title: 1. Introducción al Threat Hunting 🎬
layout: default
has_toc: false
nav_order: 2
parent: 100 days challenge 🗻

---

# **1. Introducción al Threat Hunting** 🎬
---
## Índice 

- [1.1 Introducción](https://nottaroff.github.io/workspace/docs/100%20days/1.%20Introduccio/#11-introducción) 
- [1.2 Tipos de Threat Hunting](https://nottaroff.github.io/workspace/docs/100%20days/1.%20Introduccio/#12-tipos-de-threat-hunting)
- [1.3 Metodologías](https://nottaroff.github.io/workspace/docs/100%20days/1.%20Introduccio/#13-metodologias)
- [1.4 Importancia del Threat Hunting](https://nottaroff.github.io/workspace/docs/100%20days/1.%20Introduccio#14-importancia-del-threat-hunting)
- [1.5 Etapas](https://nottaroff.github.io/workspace/docs/100%20days/1.%20Introduccio/#14-etapas)
- [1.6 Glosario](https://nottaroff.github.io/workspace/docs/100%20days/1.%20Introduccio/#15-glosario)

---

## 1.1 Introducción

El threat hunting consiste en la **búsqueda proactiva de posibles amenazas** o actividades maliciosas dentro de una red o sistema informático que aún no han sido detectadas.

Si dependemos solamente de las herramientas de seguridad para detectar un ataque,como el incident response (IR) que es una herramienta reactiva.  La acción frente a la amenaza se desencadena por una alerta del sistema. Esto conlleva un proceso de triaje y análisis, y cuando se determina que se trata de una actividad maliciosa, debe ser respondida y tratada en consecuencia. Si el sistema no fuera capaz de detectar el ataque no habria ninguna respuesta a el. 

Por ello, es necesario el **Threat Hunting** ya que es una metodologia proactiva. No hay una alerta real que dé inicio a la búsqueda, excepto el objetivo de fortalecer la postura de seguridad de la organización.

Generalmente, las organizaciones comienzan a desarollar el puesto  de threat hunting  una vez que ya tienen establecido un proceso de incident response (IR) y mecanismos de detección en su lugar, pero puede que algunos incidentes no se están detectando lo suficientemente temprano. El objetivo principal del threat hunting es lograr una detección temprana de estas amenazas. 

El threat hunting retroalimenta las herramientas de Incident response, proporcionando información valiosa que puede utilizarse para mejorar y ajustar las herramientas y procesos de incident response, fortaleciendo la capacidad de una organización para detectar, responder y mitigar amenazas cibernéticas.  Se estima que los sistemas de detección de amenazas de seguridad, SOC (Centro de Operaciones de Seguridad) de nivel 1 y 2, pueden detectar el 80% de las amenazas en promedio, pero el 20% restante necesita especial atención y una estrategia proactiva para identificarlas lo antes posible.


<img src="https://github.com/Nottaroff/workspace/blob/main/media/intro/intro.png" alt="Intro Image">


Algunos de los elementos importantes en la práctica de la caza de amenazas incluyen identificar anomalías, luego utilizar herramientas y técnicas para analizar anomalías como una amenaza y, finalmente, encontrar formas de remediar esas amenazas antes de que el atacante las aproveche. La caza de amenazas cibernéticas es una actividad impulsada por datos y depende de la disponibilidad de datos generados a partir de herramientas de monitoreo de puntos finales. Los cazadores de amenazas revisan estos registros de eventos/datos para identificar cualquier patrón de ataque de seguridad nuevo basado en sus modelos de caza redactados.

## 1.2 **Tipos de Threat Hunting**

Existen diferentes enfoques que pueden tomar los equipos de ciberseguridad en cuanto al threat hunting. En este sentido, se pueden identificar distintos tipos de caza de amenazas, con sus propias metodologías y procesos específicos. Podemos distinguir entre tres tipos de threat hunting: 

{: .detail }
> **Estructurado**                                                 
Se realiza en función de las tácticas, técnicas y procedimientos (TTPs) utilizados por los atacantes, asi como los indicadores de ataque (IoA). Este tipo de hunting podria utilizar  [MITRE Adversary Tactics Techniques and Common Knowledge (ATT&CK) framework](https://attack.mitre.org/).

{: .detail }
>**No estructurada**                                                
En  función de un desencadenante oun indicador de compromiso (IoC). 

{: .detail }
>**Situacional**                            
Se diseñan hipotesis basadas en situaciones concretas, como vulnerabilidades detectadas durante la evaluación de riesgos de una red. Luego, se emplean pistas centradas en entidades utilizando datos de ataques recopilados de múltiples fuentes, que incluyen las TTP más recientes. De esta manera, un cazador de amenazas puede buscar comportamientos específicos dentro del entorno de prueba.
    
## 1.3 Metodologias
    
**Metodologias del Threat Hunting**
    
Dentro de cada tipo de caza de amenazas, las metodologías proporcionan un marco detallado para la ejecución práctica de la detección y respuesta a amenazas. Estas metodologías establecen los pasos específicos que los equipos de ciberseguridad deben seguir para identificar, investigar y neutralizar posibles riesgos. Las principales metodologias son: 
    
1. **Investigación impulsada por hipótesis (Hypothesis hunting).**
Es un modelo de busqueda proactivo donde se utiliza una biblioteca de busqueda de  amenazas o ataques que tienen IoA (Indicadores de ataque) actualizados y los últimos TTPs de un gran conjunto de datos de ataques obtenidos de la multitud. Estas bibliotecas de caza están alineadas con guías de detección globales. . El cazador identifica los actores de la amenaza en función del entorno, el dominio y los comportamientos de ataque empleados para crear una hipótesis alineada con el marco MITRE.  
Utilizando estos IoAs y TTPs, el cazador intenta buscar de manera proactiva nuevas amenazas en el sistema.

2. **Investigación basada en indicadores conocidos de compromiso o indicadores de ataque (IoA) (Intel-based hunting).**
        
    Esta busquedaa  implica aprovechar la inteligencia de amenazas tácticas para catalogar indicadores de compromiso (IOCs) como valores hash, direcciones IP,nombres de dominio, etc., provenientes de plataformas de intercambio de inteligencia como CERT. Estos IoC se pueden exportar a un sistema de gestión de información y eventos de seguridad (SIEM) en formatos como STIX y TAXII. Una vez que el SIEM recibe la alerta basada en un IoC, los cazadores de amenazas pueden investigar la actividad maliciosa antes y después de la alerta para identificar posibles compromisos en el entorno.
        
3. **Investigaciones situacionales o avanzadas de análisis y aprendizaje automático (Custom hunting).**
En este método, las hipótesis se basan en el conocimiento de la situación y en metodologías de caza de la industria. Se enfocan en identificar anomalías en las herramientas SIEM y EDR, y pueden adaptarse a los requisitos del cliente. Estas cacerías pueden ser reactivas, según las necesidades del cliente, o proactivas, en respuesta a situaciones como problemas geopolíticos o ataques dirigidos. Se basan en modelos de caza que pueden incorporar inteligencia o hipótesis, utilizando información IoA e IoC.

## **1.4 Importancia del Threat Hunting**

La principal diferencia de las medidas de seguridad tradicionales que se centran en la prevención y detección automatizada, el Threat Hunting implica una investigación activa por parte de un analista. Dicha investigación nos dara proactividad en nuestro sistema de busqueda de amenazas. 
La importancia del  threat hunting consiste en: 

{: .importance }
>- Nos permite la **identificación de amenazas avanzadas.** Las amenazas mas modernas y sotisficatas pueden evadir las defensas planteadas en el sistema. El trabajo de Threat Hunting permite descubrir y mitigar estas amenazas.
- **Reducción del tiempo de respuesta:** el Threat Hunting nos puede ayudar a  adelantarnos a las amenazas antes de que ocurran.  Si podemos prevenir ante las nuevas amenazas y crear condiciones que las detectes será crucial para minimizar el impacto.
- **Mejora de la postura de seguridad informática:** es importante para poder identificar y corregir vulnerabilidades subyacentes en la infraestructura de una organización.  Nos permetira tener una mejora general de la postura de la seguridad. 
- **Adaptación a las nuevas amenzas:** A medida que evolucionan las tácticas de las amenazas, es fundamental que las defensas también evolucionen. El Threat Hunting nos  permite estar actualizados y manteneros al tantos de las tendencias y adaptarnos rápidamente a las amenazas emergetes.


Actualmente, el Threat Hunting se ha convertido en una herramienta fundamental en el arsenal de cualquier equipo ciberseguridad. Su evolución ha sido impulsada por la necesidad de combatir amenazas cada vez más sofisticadas, aprovechando tecnologías avanzadas y adoptando un enfoque proactivo basado en el comportamiento.

<img src="/media/intro/Threat_graphic.png" alt="Threat Graphic">


## 1.4 Etapas

Podemos estructurar el threat hunting mediante una serie de fases durante su desarrollo. Estas etapas nos ayudan a establecer una estructura clara y efectiva para llevar a cabo la actividad de caza de amenazas.

**Generación de hipótesis:**  Formulación de una hipótesis fundamentada acerca de posibles amenazas en el ambiente digital.
{: .detail }

**Investigación:** Implica la recolección, procesamiento, análisis y correlación de datos pertinentes a la hipótesis. Se emplean diversas herramientas, como sistemas de detección y respuesta a incidentes (EDR), así como fuentes de datos variadas para extraer e interpretar indicadores de ataques, como registros de actividad, tráfico de red, y comportamientos anómalos de usuarios y dispositivos.
{: .detail }

**Descubrimiento de patrones:** Identificando y caracterizando las  TTPs utilizados por las amenazas identificadas. Buscamos comprender el enfoque, los objetivos y la capacidad de los atacantes, así como atribuir sus acciones a posibles ATP.
{: .detail }

**Análisis automatizado:** Implica el empleo de herramientas o algoritmos automatizados para recolectar, procesar y analizar los datos obtenidos en las etapas anteriores. Se pueden aplicar distintas técnicas, como análisis estadístico, detección de anomalías, o incluso inteligencia artificial para optimizar el tiempo, recursos y eficacia del threat hunting, mejorando así la capacidad de detección y análisis de amenazas.
{: .detail }

## 1.5 **Glosario**

**IoA** (Indicador de Ataque):  Señales que pueden indicar la presencia de un ataque o actividad maliciosa en un sistema o red.

**TTP** (Tácticas, Técnicas y Procedimientos): Son los métodos, herramientas y procesos utilizados por los actores maliciosos para llevar a cabo un ataque.

**MITRE:** Organización que trabaja en investigación y desarrollo de tecnologías para mejorar la seguridad cibernética. El marco MITRE ATT&CK es una base de conocimientos que describe las tácticas y técnicas utilizadas por los atacantes durante las etapas de un ataque.

**IoC** (Indicador de Compromiso): Es una evidencia observable o detectable que sugiere la presencia de una intrusión o actividad maliciosa en un sistema.

**STIX** (Structured Threat Information eXpression): Es un estándar de la industria para representar y compartir información sobre amenazas de manera estructurada y coherente.

**TAXII** (Trusted Automated eXchange of Indicator Information): Es un protocolo de intercambio de información sobre indicadores de amenazas que permite la transferencia segura y automatizada de datos entre organizaciones.

**SIEM** (Security Information and Event Management): Recopila, correlaciona y analiza datos de eventos de seguridad en tiempo real para proporcionar una visión integral de la postura de seguridad de una organización.

**EDR** (Endpoint Detection and Response): Es una solución de seguridad que monitorea y responde a las actividades sospechosas en dispositivos finales, como computadoras y servidores.

**CERT** (Computer Emergency Response Team): Es un equipo especializado en seguridad cibernética que responde a incidentes de seguridad, proporciona orientación y apoyo, y coordina respuestas a incidentes dentro de una organización o comunidad.

---