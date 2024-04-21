---
title: Diario de Registro  📝
layout: default
has_toc: false
nav_order: 1
parent: 100 days challenge 🗻
---

{: .work }
>*En este apartado se regista el progreso dia a dia del reto.*

---
#⁠100daysOfThreatHunting
### 1️⃣ Day 1: Introducción al Threat Hunting. 

El día de hoy he dedicado a la búsqueda de información general sobre el tema, que es el threat hunting y porque es importante a dia de hoy en la ciberseguridad. También he realizado la sala de TryHackme de Threat Hunting: Introduction. 

Pequeño extracto:
El Threat Hunting consiste en la búsqueda proactiva y sistemática de posibles amenazas o actividades maliciosas dentro de una red o sistema informático que aún no han sido detectadas.

Si dependemos solamente de las herramientas de seguridad para detectar un ataque, como el incident response (IR). La acción frente a la amenaza se desencadena por una alerta del sistema. Esto conlleva un proceso de triaje y análisis, y cuando se determina de que se trata de una actividad maliciosa, debe ser respondida y tratada en consecuencia. Si el sistema no fuera capaz de detectar el ataque no habría ninguna respuesta a el. 
Por ello, es necesario el Threat Hunting ya que es una metodología proactiva, en búsqueda constante de nuevas amenazas. No hay una alerta real que dé inicio a la búsqueda, excepto el objetivo de fortalecer la postura de seguridad de la organización.

Generalmente, las organizaciones comienzan a realizar el threat hunting  una vez que ya tienen establecido un proceso de incident response , pero puede que algunos incidentes no se están detectando lo suficientemente temprano. El objetivo principal del threat hunting es lograr una detección temprana de estas amenazas. 

**REFERENCIAS**

- [CrowdStrike Threat Hunting](https://www.crowdstrike.com/cybersecurity-101/threat-hunting/)
- [IBM Threat Hunting](https://www.ibm.com/topics/threat-hunting)
- [Guía práctica de caza de amenazas (PDF)](https://www.threathunting.net/files/hunt-evil-practical-guide-threat-hunting.pdf)
- [Introduction to Threat Hunting en TryHackMe](https://tryhackme.com/r/room/introductiontothreathunting)


---

⁠⁠#100daysofThreatHunting
### 2️⃣ Day 2: Tipos y Metodologías
Después de la búsqueda de información general he acabado de definir el indicie de este periodo de Introducción. Mi idea es cuando vaya terminando los temas subiré el contenido detallado a una pagina de github. Así si a alguien le interesa el tema, puede mirar más en detalle mi recopilación.

Resumen del día de hoy:
Dentro del threat hunting podemos distinguir diferentes tipos y métodos:

1.2 Tipos 
Existen diferentes enfoques que pueden tomar los equipos de ciberseguridad en cuanto al threat hunting. En este sentido, se pueden identificar distintos tipos de caza de amenazas, con sus propias metodologías y procesos específicos. Podemos distinguir entre tres tipos de threat hunting: 

Estructurado
No estructurada
Situacional

1.3 Metodologías

Dentro de cada tipo de caza de amenazas, las metodologías proporcionan un marco detallado para la ejecución práctica de la detección y respuesta a amenazas. Estas metodologías establecen los pasos específicos que los equipos de ciberseguridad deben seguir para identificar, investigar y neutralizar posibles riesgos. Las principales metodologías son: 

Investigación impulsada por hipótesis (Hypothesis hunting)
Investigación basada en indicadores conocidos de compromiso o indicadores de ataque (IoA) (Intel-based hunting).
Investigaciones situacionales o avanzadas de análisis y aprendizaje automático (Custom hunting).

**REFERENCIAS:**

- [Manual general](https://livebook.manning.com/book/cyber-threat-hunting/chapter-1/v-10/1)
- [Tipos/métodos](https://cybertalents.com/blog/threat-hunting)

---

### 3️⃣ Day 3: Importancia y Etapas
Continuando con la Introducción al Threat Hunting, el día de hoy he definido la importancia de establecer el threat hunting como método defensivo, las posibles etapas a la hora de desarollar la caza de amenazas y he incluido algunos términos relativos al threat hunting en el glosario.


Extracto resumido de la información recopilada:

1.4 Importancia del Threat Hunting

La principal diferencia de las medidas de seguridad tradicionales que se centran en la prevención y detección automatizada, el Threat Hunting implica una investigación activa por parte de un analista. Dicha investigación nos dará proactividad en nuestro sistema de búsqueda de amenazas. 
La importancia del  threat hunting consiste en: 

Nos permite la identificación de amenazas avanzadas.
Reducción del tiempo de respuesta.
Mejora de la postura de seguridad informática.
Adaptación a las nuevas amenazas.

Actualmente, el Threat Hunting se ha convertido en una herramienta fundamental en el arsenal de cualquier equipo ciberseguridad. Su evolución ha sido impulsada por la necesidad de combatir amenazas cada vez más sofisticadas, aprovechando tecnologías avanzadas y adoptando un enfoque proactivo basado en el comportamiento.

1.5 Etapas

Podemos estructurar el threat hunting mediante una serie de fases durante su desarrollo. Estas etapas nos ayudan a establecer una estructura clara y efectiva para llevar a cabo la actividad de caza de amenazas.
Generación de hipótesis
Investigación
Descubrimiento de patrones
Análisis automatizado

**REFERENCIAS**

- [¿Qué es la caza de amenazas? - Cybereason](https://www.cybereason.com/fundamentals/what-is-threat-hunting)
- [Glosario de ciberinteligencia: Caza de amenazas - Darktrace](https://es.darktrace.com/cyber-ai-glossary/threat-hunting)


---

### 4️⃣ Day 4: Glosario, Publicación y Revisión
El día de hoy doy por concluida la primera etapa de introducción al Threat Hunting. Hemos visto que es, que tipos hay, metodologías, etapas y la importancia que tiene hacer threat hunting para mejorar nuestra protección ante las amenazas.  Me he dedicado a revisar la información que he podido detallar de los puntos mencionados y los he publicado en mi github.
 Podéis ver el articulo publicado de introducción aquí: https://nottaroff.github.io/workspace/docs/100%20days/Introduccion/ 
También he añadido algunos términos en el glosario, sobre todo los mencionados en la introducción. Este apartado lo iré trabajando a lo largo del reto. 
He creado unos gráficos para representar un poco mejor los conceptos vistos en la introducción.

Glosario añadido: https://nottaroff.github.io/workspace/docs/100%20days/Introduccion/#15-glosario
IoA (Indicador de Ataque)
TTP (Tácticas, Técnicas y Procedimientos)
MITRE
IoC (Indicador de Compromiso)
STIX (Structured Threat Information eXpression)
TAXII (Trusted Automated eXchange of Indicator Information)
SIEM (Security Information and Event Management)
EDR (Endpoint Detection and Response)
CERT (Computer Emergency Response Team)

REFERENCIAS: 
-[100 Days - Documentación](https://nottaroff.github.io/workspace/docs/100%20days/)

---

### 5️⃣ Day 5: Recopilación y análisis de información sobre amenazas
Continuando con la fase del pre-hunting. El día de hoy he estado documentándome sobre la recopilación y análisis en el threat hunting. Sobre que tener en cuenta a nivel teórico.

Recopilación y análisis de información sobre amenazas

2.1 Fuentes de inteligencia de amenazas.
Las fuentes de inteligencia de amenazas son cruciales para una caza efectiva de amenazas, proporcionando información esencial para detectar y contrarrestar los riesgos de seguridad de manera eficaz. 
Algunas fuentes comunes>
Informes de seguridad.
Comunidades de seguridad y foros en línea.
Información compartida por organizaciones.
Resultados de investigaciones forenses de incidentes previos.
Datos  internos generados por herramientas de monitoreo de seguridad y análisis de registros

 2.2 Técnicas para recopilar información.
Aunque el enfoque principal del Threat Hunting es el ser humano, contar con acceso a tecnologías relevantes y confiables, así como a herramientas escalables y flexibles:
Actividades de endpoints en servidores y clientes
Datastores
Análisis

 2.3 Métodos analíticos.
Los enfoques analíticos son necesarios para extraer información valiosa de los datos recopilados. 
Algunas técnicas comunes son:
Evaluación de comportamiento
Correlación de datos
Identificación de firmas
Análisis de riesgo
Seguimiento de tendencias

 2.4 Gestión de datos. (WIP)
He incluido este apartado de gestión de datos desde una perspectiva del threat hunter para entender como se documentan, se estandarizan, se modelan  y la calidad de los datos. Es muy importante comprender bien estos pasos al desarrollar una analítica.

REFERENCIAS: 
-[IBM Threat Intelligence](https://www.ibm.com/es-es/topics/threat-intelligence)
-[Memoria: Threat hunting en entornos Windows](https://openaccess.uoc.edu/bitstream/10609/107546/6/aveloymTFM1219memoria.pdf)
-[OSSEM en GitHub](https://github.com/OTRF/OSSEM)


---

### 6️⃣ Day 6: Gestión de Datos
Continuando con el punto 2. Recopilación y análisis de información sobre amenazas.
He estado investigando cómo se gestionan los datos y por qué es importante desde un punto de vista analítico. La teoría en este tema es lógica y comprensible, pero al observar ejemplos dentro de un sistema, no era tan fácil de entenderlo desde mi perspectiva. Por lo tanto, encontré algunas salas de TryHackMe que me ayudaron a comprender mejor el funcionamiento interno de la gestión de datos.

El día de hoy he realizado la room: https://tryhackme.com/r/room/windowseventlogs
Que me ha proporcionado diferentes herramientas en Windows para poder buscar, localizar y extraer información de los logs del sistema. 

Extracto de la parte teórica:
Documentación de Datos
Para realizar el análisis y la interpretación de los datos, es fundamental comprender qué datos se están recopilando y cómo se están estructurando.

Estandarización de Datos
La estandarización de datos nos ofrece una coherencia y eficacia en el análisis de la información recopilada de diversas fuentes. Se basa en el empleo de un Modelo de Información Común (CIM), que proporciona una estructura  para normalizar conjuntos de datos mediante un esquema. 

Modelación de Datos (Data Modeling)
El modelo de datos determina la estructura de los datos y las relaciones entre ellos. Identificar estas relaciones es importante para documentar eventos específicos que podrían vincularse a cadenas de eventos relacionadas con el comportamiento de los adversarios.

Calidad de Datos (Data Quality)
La calidad de los datos se refiere a su valor para los usos previstos en las operaciones, toma de decisiones y planificación. 

REFERENCIAS:
-[Conceptos de CIM para FlashSystem](https://www.ibm.com/docs/es/flashsystem-a9000/12.2.1?topic=STJKMM_12.2.1/xiv_apicimconcepts.htm)
-[Visión general de CIM por Open Networking Foundation](https://opennetworking.org/wp-content/uploads/2014/10/TR-513_CIM_Overview_1.2.pdf)
-[Data Management en Threat Hunter Playbook](https://threathunterplaybook.com/pre-hunt/data_management.html)

---
