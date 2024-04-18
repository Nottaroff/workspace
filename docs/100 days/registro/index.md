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
### Day 1: Introducción al Threat Hunting. 

El día de hoy he dedicado a la búsqueda de información general sobre el tema, que es el threat hunting y porque es importante a dia de hoy en la ciberseguridad. También he realizado la sala de TryHackme de Threat Hunting: Introduction. 

Pequeño extracto:
El Threat Hunting consiste en la búsqueda proactiva y sistemática de posibles amenazas o actividades maliciosas dentro de una red o sistema informático que aún no han sido detectadas.

Si dependemos solamente de las herramientas de seguridad para detectar un ataque, como el incident response (IR). La acción frente a la amenaza se desencadena por una alerta del sistema. Esto conlleva un proceso de triaje y análisis, y cuando se determina de que se trata de una actividad maliciosa, debe ser respondida y tratada en consecuencia. Si el sistema no fuera capaz de detectar el ataque no habría ninguna respuesta a el. 
Por ello, es necesario el Threat Hunting ya que es una metodología proactiva, en búsqueda constante de nuevas amenazas. No hay una alerta real que dé inicio a la búsqueda, excepto el objetivo de fortalecer la postura de seguridad de la organización.

Generalmente, las organizaciones comienzan a realizar el threat hunting  una vez que ya tienen establecido un proceso de incident response , pero puede que algunos incidentes no se están detectando lo suficientemente temprano. El objetivo principal del threat hunting es lograr una detección temprana de estas amenazas. 

**REFERENCIAS**

https://www.crowdstrike.com/cybersecurity-101/threat-hunting/
https://www.ibm.com/topics/threat-hunting
https://www.threathunting.net/files/hunt-evil-practical-guide-threat-hunting.pdf
https://tryhackme.com/r/room/introductiontothreathunting

---

⁠⁠#100daysofThreatHunting
### Day 2: Tipos y Metodologías
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

Manual general: https://livebook.manning.com/book/cyber-threat-hunting/chapter-1/v-10/1
Tipos/métodos: https://cybertalents.com/blog/threat-hunting

---

#⁠100days OfThreatHunting
### Day 3: Importancia y Etapas
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

https://www.cybereason.com/fundamentals/what-is-threat-hunting
https://es.darktrace.com/cyber-ai-glossary/threat-hunting

---
