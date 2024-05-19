---
title: Diario de Registro  📝
layout: default
has_toc: false
nav_order: 1
parent: 100 days challenge 🗻
---

{: .work }
>En este apartado se regista el progreso dia a dia del reto.

---
<details>
  <summary><strong>Day 1: Introducción al Threat Hunting.</strong></summary>
    <body>
        <p>El día de hoy he dedicado a la búsqueda de información general sobre el tema, que es el threat hunting y porque es importante a día de hoy en la ciberseguridad. También he realizado la sala de TryHackme de Threat Hunting: Introduction.</p>
        
        <p>Pequeño extracto:</p>
        <p>El Threat Hunting consiste en la búsqueda proactiva y sistemática de posibles amenazas o actividades maliciosas dentro de una red o sistema informático que aún no han sido detectadas.</p>

        <p>Si dependemos solamente de las herramientas de seguridad para detectar un ataque, como el incident response (IR). La acción frente a la amenaza se desencadena por una alerta del sistema. Esto conlleva un proceso de triaje y análisis, y cuando se determina de que se trata de una actividad maliciosa, debe ser respondida y tratada en consecuencia. Si el sistema no fuera capaz de detectar el ataque no habría ninguna respuesta a él. Por ello, es necesario el Threat Hunting ya que es una metodología proactiva, en búsqueda constante de nuevas amenazas. No hay una alerta real que dé inicio a la búsqueda, excepto el objetivo de fortalecer la postura de seguridad de la organización.</p>

        <p>Generalmente, las organizaciones comienzan a realizar el threat hunting una vez que ya tienen establecido un proceso de incident response , pero puede que algunos incidentes no se están detectando lo suficientemente temprano. El objetivo principal del threat hunting es lograr una detección temprana de estas amenazas.</p>

        <h2>REFERENCIAS</h2>
        <ul>
            <li><a href="https://www.crowdstrike.com/cybersecurity-101/threat-hunting/">CrowdStrike Threat Hunting</a></li>
            <li><a href="https://www.ibm.com/topics/threat-hunting">IBM Threat Hunting</a></li>
            <li><a href="https://www.threathunting.net/files/hunt-evil-practical-guide-threat-hunting.pdf">Guía práctica de caza de amenazas (PDF)</a></li>
            <li><a href="https://tryhackme.com/r/room/introductiontothreathunting">Introduction to Threat Hunting en TryHackMe</a></li>
        </ul>
    </body>
</details>

<details>
  <summary><strong>Day 2: Tipos y Metodologías</strong></summary>
  
  <p>Después de la búsqueda de información general he acabado de definir el indicie de este periodo de Introducción. Mi idea es cuando vaya terminando los temas subiré el contenido detallado a una página de GitHub. Así si a alguien le interesa el tema, puede mirar más en detalle mi recopilación.</p>

  <h3>Resumen del día de hoy:</h3>
  <p>Dentro del threat hunting podemos distinguir diferentes tipos y métodos:</p>

  <h4>1.2 Tipos</h4>
  <p>Existen diferentes enfoques que pueden tomar los equipos de ciberseguridad en cuanto al threat hunting. En este sentido, se pueden identificar distintos tipos de caza de amenazas, con sus propias metodologías y procesos específicos. Podemos distinguir entre tres tipos de threat hunting:</p>
  <ul>
    <li>Estructurado</li>
    <li>No estructurada</li>
    <li>Situacional</li>
  </ul>

  <h4>1.3 Metodologías</h4>
  <p>Dentro de cada tipo de caza de amenazas, las metodologías proporcionan un marco detallado para la ejecución práctica de la detección y respuesta a amenazas. Estas metodologías establecen los pasos específicos que los equipos de ciberseguridad deben seguir para identificar, investigar y neutralizar posibles riesgos. Las principales metodologías son:</p>
  <ul>
    <li>Investigación impulsada por hipótesis (Hypothesis hunting)</li>
    <li>Investigación basada en indicadores conocidos de compromiso o indicadores de ataque (IoA) (Intel-based hunting)</li>
    <li>Investigaciones situacionales o avanzadas de análisis y aprendizaje automático (Custom hunting)</li>
  </ul>

  <strong>REFERENCIAS:</strong>
  <ul>
    <li><a href="https://livebook.manning.com/book/cyber-threat-hunting/chapter-1/v-10/1">Manual general</a></li>
    <li><a href="https://cybertalents.com/blog/threat-hunting">Tipos/métodos</a></li>
  </ul>
</details>


<details>
  <summary><strong> Day 3: Importancia y Etapas</strong></summary>
  
  <p>Continuando con la Introducción al Threat Hunting, el día de hoy he definido la importancia de establecer el threat hunting como método defensivo, las posibles etapas a la hora de desarollar la caza de amenazas y he incluido algunos términos relativos al threat hunting en el glosario.</p>

  <h3>Extracto resumido de la información recopilada:</h3>

  <h4>1.4 Importancia del Threat Hunting</h4>
  <p>La principal diferencia de las medidas de seguridad tradicionales que se centran en la prevención y detección automatizada, el Threat Hunting implica una investigación activa por parte de un analista. Dicha investigación nos dará proactividad en nuestro sistema de búsqueda de amenazas.</p>
  <p>La importancia del threat hunting consiste en:</p>
  <ul>
    <li>Nos permite la identificación de amenazas avanzadas.</li>
    <li>Reducción del tiempo de respuesta.</li>
    <li>Mejora de la postura de seguridad informática.</li>
    <li>Adaptación a las nuevas amenazas.</li>
  </ul>
  <p>Actualmente, el Threat Hunting se ha convertido en una herramienta fundamental en el arsenal de cualquier equipo ciberseguridad. Su evolución ha sido impulsada por la necesidad de combatir amenazas cada vez más sofisticadas, aprovechando tecnologías avanzadas y adoptando un enfoque proactivo basado en el comportamiento.</p>

  <h4>1.5 Etapas</h4>
  <p>Podemos estructurar el threat hunting mediante una serie de fases durante su desarrollo. Estas etapas nos ayudan a establecer una estructura clara y efectiva para llevar a cabo la actividad de caza de amenazas.</p>
  <ul>
    <li>Generación de hipótesis</li>
    <li>Investigación</li>
    <li>Descubrimiento de patrones</li>
    <li>Análisis automatizado</li>
  </ul>

  <strong>REFERENCIAS</strong>
  <ul>
    <li><a href="https://www.cybereason.com/fundamentals/what-is-threat-hunting">¿Qué es la caza de amenazas? - Cybereason</a></li>
    <li><a href="https://es.darktrace.com/cyber-ai-glossary/threat-hunting">Glosario de ciberinteligencia: Caza de amenazas - Darktrace</a></li>
  </ul>
</details>

<details>
  <summary><strong>Day 4: Glosario, Publicación y Revisión</strong></summary>
  
  <p>El día de hoy doy por concluida la primera etapa de introducción al Threat Hunting. Hemos visto que es, que tipos hay, metodologías, etapas y la importancia que tiene hacer threat hunting para mejorar nuestra protección ante las amenazas. Me he dedicado a revisar la información que he podido detallar de los puntos mencionados y los he publicado en mi GitHub.</p>
  <p>Podéis ver el artículo publicado de introducción <a href="https://nottaroff.github.io/workspace/docs/100%20days/Introduccion/">aquí</a>.</p>
  <p>También he añadido algunos términos en el glosario, sobre todo los mencionados en la introducción. Este apartado lo iré trabajando a lo largo del reto.</p>
  <p>He creado unos gráficos para representar un poco mejor los conceptos vistos en la introducción.</p>

  <p><strong>Glosario añadido:</strong> <a href="https://nottaroff.github.io/workspace/docs/100%20days/Introduccion/#15-glosario">aquí</a></p>
  <ul>
    <li>IoA (Indicador de Ataque)</li>
    <li>TTP (Tácticas, Técnicas y Procedimientos)</li>
    <li>MITRE</li>
    <li>IoC (Indicador de Compromiso)</li>
    <li>STIX (Structured Threat Information eXpression)</li>
    <li>TAXII (Trusted Automated eXchange of Indicator Information)</li>
    <li>SIEM (Security Information and Event Management)</li>
    <li>EDR (Endpoint Detection and Response)</li>
    <li>CERT (Computer Emergency Response Team)</li>
  </ul>

  <strong>REFERENCIAS:</strong>
  <ul>
    <li><a href="https://nottaroff.github.io/workspace/docs/100%20days/">100 Days - Documentación</a></li>
  </ul>
</details>

<details>
  <summary><strong>Day 5: Recopilación y análisis de información sobre amenazas</strong></summary>
  
  <p>Continuando con la fase del pre-hunting. El día de hoy he estado documentándome sobre la recopilación y análisis en el threat hunting. Sobre qué tener en cuenta a nivel teórico.</p>

  <h3>Recopilación y análisis de información sobre amenazas</h3>

  <h4>2.1 Fuentes de inteligencia de amenazas.</h4>
  <p>Las fuentes de inteligencia de amenazas son cruciales para una caza efectiva de amenazas, proporcionando información esencial para detectar y contrarrestar los riesgos de seguridad de manera eficaz.</p>
  <p>Algunas fuentes comunes:</p>
  <ul>
    <li>Informes de seguridad.</li>
    <li>Comunidades de seguridad y foros en línea.</li>
    <li>Información compartida por organizaciones.</li>
    <li>Resultados de investigaciones forenses de incidentes previos.</li>
    <li>Datos internos generados por herramientas de monitoreo de seguridad y análisis de registros.</li>
  </ul>

  <h4>2.2 Técnicas para recopilar información.</h4>
  <p>Aunque el enfoque principal del Threat Hunting es el ser humano, contar con acceso a tecnologías relevantes y confiables, así como a herramientas escalables y flexibles:</p>
  <ul>
    <li>Actividades de endpoints en servidores y clientes.</li>
    <li>Datastores.</li>
    <li>Análisis.</li>
  </ul>

  <h4>2.3 Métodos analíticos.</h4>
  <p>Los enfoques analíticos son necesarios para extraer información valiosa de los datos recopilados.</p>
  <p>Algunas técnicas comunes son:</p>
  <ul>
    <li>Evaluación de comportamiento.</li>
    <li>Correlación de datos.</li>
    <li>Identificación de firmas.</li>
    <li>Análisis de riesgo.</li>
    <li>Seguimiento de tendencias.</li>
  </ul>

  <h4>2.4 Gestión de datos. (WIP)</h4>
  <p>He incluido este apartado de gestión de datos desde una perspectiva del threat hunter para entender cómo se documentan, se estandarizan, se modelan y la calidad de los datos. Es muy importante comprender bien estos pasos al desarrollar una analítica.</p>

  <strong>REFERENCIAS:</strong>
  <ul>
    <li><a href="https://www.ibm.com/es-es/topics/threat-intelligence">IBM Threat Intelligence</a></li>
    <li><a href="https://openaccess.uoc.edu/bitstream/10609/107546/6/aveloymTFM1219memoria.pdf">Memoria: Threat hunting en entornos Windows</a></li>
    <li><a href="https://github.com/OTRF/OSSEM">OSSEM en GitHub</a></li>
  </ul>
</details>


<details>
  <summary><strong>Day 6: Gestión de Datos</strong></summary>
  
  <p>Continuando con el punto 2. Recopilación y análisis de información sobre amenazas.</p>
  <p>He estado investigando cómo se gestionan los datos y por qué es importante desde un punto de vista analítico. La teoría en este tema es lógica y comprensible, pero al observar ejemplos dentro de un sistema, no era tan fácil de entenderlo desde mi perspectiva. Por lo tanto, encontré algunas salas de TryHackMe que me ayudaron a comprender mejor el funcionamiento interno de la gestión de datos.</p>
  <p>El día de hoy he realizado la room: <a href="https://tryhackme.com/r/room/windowseventlogs">https://tryhackme.com/r/room/windowseventlogs</a> que me ha proporcionado diferentes herramientas en Windows para poder buscar, localizar y extraer información de los logs del sistema.</p>

  <h4>Extracto de la parte teórica:</h4>

  <p><strong>Documentación de Datos</strong></p>
  <p>Para realizar el análisis y la interpretación de los datos, es fundamental comprender qué datos se están recopilando y cómo se están estructurando.</p>

  <p><strong>Estandarización de Datos</strong></p>
  <p>La estandarización de datos nos ofrece una coherencia y eficacia en el análisis de la información recopilada de diversas fuentes. Se basa en el empleo de un Modelo de Información Común (CIM), que proporciona una estructura para normalizar conjuntos de datos mediante un esquema.</p>

  <p><strong>Modelación de Datos (Data Modeling)</strong></p>
  <p>El modelo de datos determina la estructura de los datos y las relaciones entre ellos. Identificar estas relaciones es importante para documentar eventos específicos que podrían vincularse a cadenas de eventos relacionadas con el comportamiento de los adversarios.</p>

  <p><strong>Calidad de Datos (Data Quality)</strong></p>
  <p>La calidad de los datos se refiere a su valor para los usos previstos en las operaciones, toma de decisiones y planificación.</p>

  <strong>REFERENCIAS:</strong>
  <ul>
    <li><a href="https://www.ibm.com/docs/es/flashsystem-a9000/12.2.1?topic=STJKMM_12.2.1/xiv_apicimconcepts.htm">Conceptos de CIM para FlashSystem</a></li>
    <li><a href="https://opennetworking.org/wp-content/uploads/2014/10/TR-513_CIM_Overview_1.2.pdf">Visión general de CIM por Open Networking Foundation</a></li>
    <li><a href="https://threathunterplaybook.com/pre-hunt/data_management.html">Data Management en Threat Hunter Playbook</a></li>
  </ul>
</details>

<details>
  <summary><strong>Day 7: Técnicas y herramientas del Threat Hunting</strong></summary>
  
  <p>En el día de hoy, he terminado la sección anterior de Recopilación y análisis, podéis consultar el artículo completo en mi blog: <a href="https://nottaroff.github.io/workspace/docs/100%20days/2.%20Recopilacion/">aquí</a>.</p>
  <p>El siguiente apartado se trata de Técnicas y herramientas. He definido algunas técnicas comunes y al profundizar en las herramientas, he detallado el modelo de madurez de caza. Es un gráfico que le sirve a los entornos organizacionales para decir en qué punto del threat hunting están. Creo que es interesante conocerlo para saber qué tipo de herramientas habrá que utilizar. Artículo completo: <a href="https://nottaroff.github.io/workspace/docs/100%20days/3.%20Tecnicas%20y%20Herramientas/">aquí</a>.</p>
  <p>Con esta sección doy por concluidos los primeros 7 días del challenge, que han sido más teórico introductorios. Durante los próximos días intentaré sumergirme en temas más prácticos del threat hunting.</p>

  <strong>REFERENCIAS:</strong>
  <ul>
    <li><a href="https://socprime.com/blog/threat-hunting-maturity-model-explained-with-examples/">Threat Hunting Maturity Model Explained with Examples</a></li>
    <li><a href="https://heimdalsecurity.com/blog/threat-hunting-techniques/">Threat Hunting Techniques</a></li>
  </ul>
</details>

<details>
  <summary><strong>Day 8: Elastic Introduction</strong></summary>
  
  <p>Hoy he realizado varios ejercicios prácticos de iniciación al threat hunting. Para ello, completé varias rooms en TryHackMe.</p>

  <p>En primer lugar, me familiaricé con Elastic Stack en la siguiente room: <a href="https://tryhackme.com/r/room/investigatingwithelk101">Investigating with ELK 101</a>. Es una plataforma de código abierto que combina varios componentes para la búsqueda, análisis y visualización de datos. Aprendí a realizar búsquedas, aplicar filtros, guardar búsquedas, crear visualizaciones e investigar registros de VPN para identificar anomalías. También aprendí a utilizar tableros con búsquedas guardadas y visualizaciones.</p>

  <p>La segunda parte de esta experiencia fue en la room <a href="https://tryhackme.com/r/room/advancedelkqueries">Advanced ELK Queries</a>. Aquí exploré diferentes tipos de consultas avanzadas y las diversas sintaxis de consulta, incluyendo KQL y Lucene.</p>

  <p>Por último, después de la introducción a Elastic Stack, comencé la room práctica sobre aplicación al threat hunting: <a href="https://tryhackme.com/r/room/threathuntingfoothold">Threat Hunting Foothold</a>. Empecé por el primer apartado sobre Acceso Inicial, donde investigué las técnicas que los adversarios utilizan para ingresar a una organización.</p>

  <p>El día de hoy he realizado varios ejercicios prácticos de iniciación al threat hunting. Para ello, he realizado varias rooms de TryHackMe.</p>
</details>

<details>
  <summary><strong>Day 9: Threat Hunting Foothold</strong></summary>
  
  <p>El día de hoy realicé la room de: <a href="https://tryhackme.com/r/room/threathuntingfoothold">Threat Hunting Foothold</a>.</p>
  <p>Es una buena guía práctica para aprender cómo detectar actividad maliciosa con Elastic. En ella se tratan varios ejemplos de diferentes actividades maliciosas:</p>

  <h4>Initial Access</h4>
  <p>Detección de tácticas que los adversarios usan para ingresar a sistemas, como phishing, explotación de servidores, fuerza bruta...</p>

  <h4>Execution</h4>
  <p>Se detallan los métodos para ejecutar código malicioso: herramientas de línea de comandos, herramientas del sistemas integradas (certutil.exe o bitsadmin.exe), scripting.</p>

  <h4>Defense Evasion</h4>
  <p>Detección de tácticas para evitar la detección por parte de sistemas de seguridad, como desactivación de software de seguridad, eliminación de registros, bypasses.</p>

  <h4>Persistence</h4>
  <p>Detección de técnicas para mantener el acceso a redes comprometidas a largo plazo, como modificación de claves de registro, scripts de auto-start, creación de usuarios.</p>

  <h4>Command and Control</h4>
  <p>Detección de métodos de comunicación de los adversarios con sistemas comprometidos, Comand and control techniques, servicios basados en la nube, servidores https cifrados y protocolos de red.</p>
</details>

<details>
  <summary><strong>Day 10: Threat Hunting Pivoting</strong></summary>
  
  <p>Siguiendo la línea de aprendizaje sobre el hunting, hoy he profundizado en la detección de dos técnicas más a través de Elastic.</p>

  <h4>Discovery</h4>
  <p>Referente a las acciones que un atacante puede tomar para comprender mejor los sistemas y redes que han infiltrado. Detección de actividades como:</p>
  <ul>
    <li>Reconocimiento de Usuario: whoami, net,user, net localgroup or qwinsta (Enumeración de cuentas) / dir o ls (enumeración de directorios).</li>
    <li>Reconocimiento de Host: hostname, wmic, ipconfig o systeminfo (Host) / net start o sc.exe query (Servicios).</li>
    <li>Escaneo Interno: tablas arp, ping, escaneo de puertos (nmap o Powershell).</li>
    <li>Reconocimiento Interno del Dominio: net * /domain o nltest /dclist (Listado de domain users).</li>
  </ul>

  <h4>Escalada de Privilegios</h4>
  <p>Técnicas que permiten a un atacante obtener privilegios o permisos más elevados en un sistema o red.</p>
  <ul>
    <li>Explotación de vulnerabilidades: uso de exploits.</li>
    <li>Uso de cuentas válidas: Usar runas con credenciales recién descubiertas.</li>
    <li>Abuso de control de acceso: Abuso de ACL, otorgando permisos a otras cuentas.</li>
    <li>Abuso de configuración incorrecta del hosts: Configuraciones inseguras; servicios modificables y reiniciables o binarios sobrescribibles.</li>
  </ul>
</details>

<details>
  <summary><strong>Day 11: Threat Hunting Pivoting II</strong></summary>
  
  <p>Continuando con la tarea de entender diferentes tácticas maliciosas que debemos tener en cuenta/encontrar como Threat Hunters, el día de hoy he profundizado en las dos últimas:</p>

  <h4>Credential Access</h4>
  <p>Se basa en los métodos de los atacantes para robar o descubrir nombres de usuario y contraseñas (o hashes) de cuentas válidas. Es un punto crítico del sistema ya que permite escalar privilegios o ganar acceso a otros sistemas o recursos de red. Actividades como:</p>
  <ul>
    <li>Credenciales en disco o memoria: Volcar LSASS mediante Mimikatz o creación de archivos de volcado de LSASS, listar información de cuentas en el Registro de Windows (reg.exe save hklm\sam), o extraer credenciales DPAPI con SharpDPAPI.</li>
    <li>Credenciales en archivos: Recopilar credenciales en archivos usando findstr /s/n/m/i password, encontrar archivos de administrador de credenciales (Keepass o claves SSH), y volcar credenciales de navegadores mediante SharpChrome o Firefox Decrypt.</li>
    <li>Credenciales de Dominio: Volcar credenciales de dominio mediante DCSync o acceder a credenciales de Administrador Local de LAPS.</li>
    <li>Credential spraying: Intentos fallidos de inicio de sesión de diversas cuentas en una única estación de trabajo.</li>
  </ul>

  <h4>Movimiento Lateral</h4>
  <p>Técnicas de un atacante para navegar por una red, aprovechando las credenciales y sesiones obtenidas durante fases de ataque previas.</p>
  <ul>
    <li>Explotación de servicios internos: Atacar servidores internos con aplicaciones/servicios vulnerables.</li>
    <li>Uso de herramientas administrativas legítimas: Emplear herramientas como PsExec, PowerShell remoto, etc.</li>
    <li>Autenticación con credenciales válidas: Utilizar contraseñas en texto plano o técnicas como Pass-the-Hash.</li>
    <li>Acceso a información sensible: Ingresar a servidores de archivos, bases de datos y almacenamiento en la nube.</li>
  </ul>
</details>

<details>
  <summary><strong>Day 12: Threat Hunting in Network</strong></summary>
  
  <p>Después de ver algunos ejemplos genéricos de detección de amenazas, voy a ver cómo detectar las diferentes amenazas según el entorno en el que estén. El día de hoy he estado investigando acerca de las amenazas en el entorno de red.</p>

  <h4>Caza de amenazas en Redes</h4>
  <p>Implica el uso de herramientas y métodos para monitorear y analizar activamente:</p>
  <ul>
    <li>Tráfico de red</li>
    <li>Comportamientos del usuario</li>
    <li>Actividades del sistema</li>
  </ul>

  <h4>Técnicas de análisis de tráfico de red</h4>
  <p>Examinar el flujo de datos en red para detectar patrones, anomalías y amenazas:</p>
  <ul>
    <li>Inspección de Paquetes</li>
    <li>Análisis de Tráfico</li>
    <li>Análisis de Protocolos</li>
    <li>Análisis de Comportamiento</li>
  </ul>

  <p>Para la detección y mitigación de posibles amenazas y vulnerabilidades dentro de una infraestructura de red.</p>

  <h4>Recursos</h4>
  <ul>
    <li><a href="https://shorturl.at/GHMSW">TH Workshop</a></li>
    <li><a href="https://shorturl.at/ovVY0">Threat Intelligence and Data-Driven Threat Hunting</a></li>
  </ul>
</details>

<details>
  <summary><strong>Day 13: Network Threat Hunting</strong></summary>
  
  <p>El día de hoy he seguido profundizando cuáles son los puntos de referencia durante la caza de amenazas en redes y en detalle la caza de anomalías del DNS.</p>

  <h4>Puntos de referencia durante la caza de amenazas en redes</h4>
  <p>Debemos entender primero qué es normal en el entorno de red para luego poder detectar anomalías. Para ello debemos tener en cuenta:</p>
  <ul>
    <li>Los puertos, junto con la topología de red: El malware suele utilizar protocolos comunes para comunicarse y es esencial comprender la pila de red y los protocolos comunes.</li>
    <li>Todos los dispositivos en la red deben ser analizados, ya que los atacantes suelen moverse lateralmente.</li>
    <li>Un diagrama completo de la red.</li>
  </ul>

  <h4>Anomalías del DNS</h4>
  <p>Las solicitudes DNS a dominios inusuales o sospechosos pueden ser generadas por malware que establece canales de control y comando. El monitoreo y la inclusión en listas negras de:</p>
  <ul>
    <li>Volumen anormal: Un volumen inusual de solicitudes DNS desde una determinada computadora o para un dominio determinado puede indicar un ataque.</li>
    <li>Hits en listas negras: Las solicitudes a dominios maliciosos conocidos indican que un sistema ha sido infectado con malware.</li>
    <li>Detectar tráfico DNS sospechoso:</li>
    <ul>
      <li>Recopilar paquetes de tráfico DNS</li>
      <li>Identificar y eliminar el tráfico conocido como bueno</li>
      <li>Analizar lo que queda.</li>
    </ul>
    <li>Conexiones DNS dinámicas: Las conexiones a dominios alojados en proveedores de DNS dinámicos pueden indicar comunicación C2.</li>
    <li>Tráfico denegado de salida: El malware dentro de una red puede necesitar comunicarse con un servidor C2. Este tráfico puede ser bloqueado por firewalls u otros dispositivos de seguridad de red.</li>
    <li>Anomalías en solicitudes y respuestas HTTP:</li>
    <ul>
      <li>Request: Grandes números de solicitudes repetidas para los mismos recursos pueden indicar.</li>
      <li>Response: Las respuestas inusualmente grandes pueden indicar una inyección SQL exitosa.</li>
    </ul>
    <li>Anomalías geográficas: Intentos de autenticación desde ubicaciones inusuales.</li>
  </ul>
</details>

<details>
  <summary><strong>Day 14: Threats in Networks</strong></summary>
  
  <p>El día de hoy he estado examinando diversas amenazas que pueden afectar nuestro entorno de red. Entre ellas, la detección de ataques DDoS y la identificación de dominios sospechosos.</p>

  <h4>Ataques de Denegación de Servicio Distribuido (DDoS)</h4>
  <p>Un ataque DDoS ocurre cuando múltiples máquinas atacantes intentan sobrecargar a las máquinas víctimas.</p>
  <p>Algunos indicios de un ataque DDoS:</p>
  <ul>
    <li>Indisponibilidad de sitios web.</li>
    <li>Rendimiento lento de la red.</li>
    <li>Sistemas internos operando al máximo de su capacidad.</li>
    <li>Sobrecarga de sistemas de seguridad de red (SIEM, IPS-IDS).</li>
    <li>Disponibilidad inesperada del servidor.</li>
  </ul>
  <p>Direcciones IP conectadas a muchos puertos diferentes pueden indicar un ataque de DoS.</p>

  <h4>Threat Hunting de Dominios Sospechosos</h4>
  <p>Motivos por los cuales un dominio puede ser sospechoso:</p>
  <ul>
    <li>Dominios aleatorios generados por un DGA.</li>
    <li>Direcciones IP ocultas.</li>
    <li>Extensiones de dominio inusuales.</li>
    <li>Dominios inexistentes.</li>
    <li>Dominios conocidos como maliciosos.</li>
  </ul>
  <p>La información de un dominio se puede encontrar en registros DNS, correos electrónicos y registros web. Es importante para detectar riesgos y protegerse contra actividades maliciosas.</p>

  <h4>URLs</h4>
  <p>Las URL son indicadores comunes de compromiso y se utilizan en ataques de phishing, spam y malware.</p>
  <p>Ataques basados en URL:</p>
  <ul>
    <li>Redirección.</li>
    <li>Typosquatting.</li>
    <li>Codificación de escape.</li>
  </ul>

  <h4>Respuestas HTML Sospechosas</h4>
  <p>El tamaño de la respuesta HTML es clave. En los ataques de inyección SQL, las respuestas suelen ser grandes debido a datos exfiltrados.</p>
  <p>Los registros de servidores web son útiles para identificar ataques:</p>
  <ul>
    <li>Respuestas HTML grandes pueden indicar intentos de inyección SQL y exfiltración de datos.</li>
    <li>Errores 500 Internal Server y errores 501 Header Value pueden indicar escaneos en busca de vulnerabilidades.</li>
  </ul>
  <p>Es crucial estar atento a actividades inusuales que puedan indicar una brecha de seguridad.</p>
</details>

<details>
  <summary><strong>Day 15: Threats in Network</strong></summary>
  
  <p>Hoy he estado investigando sobre la caza de tráfico irregular, mirando ejemplos de detección de web shells y la exfiltración de datos. Además, he estado configurando un entorno de laboratorio con ELK stack para poner en práctica el hunting en la red con ejemplos.</p>

  <h4>Hunting de tráfico irregular</h4>
  <p>Las irregularidades en el tráfico de red son indicadores útiles para los cazadores de amenazas. Los autores de malware utilizan diversas técnicas para ocultar ataques de comando y control, como protocolos mal utilizados y desajustes entre puertos y aplicaciones.</p>
  <p>El intento de ejecución de web shells es un vector de ataque inicial común. Es crucial detectarlos tempranamente.</p>
  <p>Algunas detecciones clave incluyen:</p>
  <ul>
    <li>Protocolos mal utilizados: Se emplean protocolos inusuales en un puerto concreto.</li>
    <li>Desajustes entre puertos y aplicaciones: Los autores de malware pueden utilizar puertos comunes o personalizados para hacer que el tráfico malicioso parezca legítimo. Observar registro de datos para encontrar anomalías y patrones sospechosos es crucial.</li>
    <li>Web Shells: Son una forma ilícita de obtener acceso a una terminal de una computadora a través de una página web dinámica en el lado del servidor.</li>
  </ul>
  <p>Herramientas de detección: Parte de suites de caza de amenazas o herramientas independientes como Webshell Scan, Scalp y Neopi.</p>

  <h4>Exfiltración de datos</h4>
  <p>Detectarla es complejo, especialmente sin una buena línea base del tráfico saliente normal.</p>
  <p>Las soluciones de Protección de Pérdida de Datos (DLP) pueden pasar por alto eventos de exfiltración debido a diversas razones:</p>
  <ul>
    <li>Los exploits de exfiltración suelen ser pasos intermedios en un ataque y no siempre afectan a los datos protegidos por DLP.</li>
    <li>Las redes de explotación distribuida son difíciles de detectar para las soluciones de DLP.</li>
  </ul>
  <p>Para detectar la exfiltración de datos, es crucial monitorear patrones de tráfico y usar técnicas de análisis avanzadas.</p>
</details>

<details>
  <summary><strong>Day 16: Practice examples of Network Hunting</strong></summary>
  
  <p>El día de hoy he terminado de añadir la información recopilada sobre el hunting en redes. Podéis echarle un ojo en mi <a href="https://nottaroff.github.io/workspace/docs/100%20days/4.%20Hunting%20en%20entornos%20de%20red/">blog</a>.</p>

  <p>Como parte práctica, he realizado un ejercicio de detección de un ataque C2 (command and control) al DNS. He utilizado el entorno de Elastic online, cargando los datos. Podéis ver los detalles en este <a href="https://nottaroff.github.io/workspace/docs/100%20days/Ejemplos%20prácticos%20Hunting%20en%20Red/">post</a>.</p>

  <p>Estos días seguiré realizando varios ejercicios prácticos de detección de ataques en la red y modificando el blog.</p>
</details>

<details>
  <summary><strong>⁠⁠⁠Day 17: Practice examples of Network Hunting II</strong></summary>
  <p>El día de hoy he realizado otros dos ejemplos de hunting en entornos de red. Concretamente en detectar posibles ataques a una aplicación web mediante la ejecución remota de código y otra práctica sobre actividades de phishing detectando enlaces maliciosos y archivos adjuntos abiertos o descargados desde diferentes estaciones de trabajo.</p>
  
  <p>Podéis echarle un ojo al reporte aquí:</p>
  
  <p>Ejecución remota de código en Web: <a href="https://nottaroff.github.io/workspace/docs/100%20days/Ejemplos%20prácticos%20Hunting%20en%20Red/#ejecución-remota-de-código-en-web-%EF%B8%8F">Informe</a></p>
  
  <p>Enlaces y Archivos de Phishing: <a href="https://nottaroff.github.io/workspace/docs/100%20days/Ejemplos%20prácticos%20Hunting%20en%20Red/#enlaces-y-archivos-de-phishing-">Informe</a></p>
</details>

<details>
  <summary><strong>⁠Day 18: Malware Hiding Techniques</strong></summary>
  <p>El día de hoy he estado investigando sobre las técnicas de evasión que utiliza el malware para pasar desapercibido en los sistemas de detección, concretamente los que dependen de firmas o patrones predefinidos.</p>
  
  <p><strong>Extracto:</strong></p>
  <ul>
    <li><strong>Malware Polimórfico:</strong> Es un tipo de software malicioso que cambia su código o apariencia con cada infección, dificultando su detección y bloqueo por parte de los antivirus tradicionales basados en firmas.</li>
    <li><strong>Malware Metamórfico:</strong> Modifica tanto su código, estructura y comportamiento en cada infección.</li>
    <li><strong>Cifrado de archivos:</strong> Consiste en codificar el código malicioso o componentes para ocultar su verdadero propósito y evitar ser detectado por el software de seguridad.</li>
    <li><strong>Empaquetadores:</strong> Comprimen y cifran el código del malware, creando un nuevo ejecutable que requiere una rutina de desempaquetado específica para ser ejecutada.</li>
    <li><strong>Cifradores:</strong> Se centran en cifrar el código del malware y generar una rutina de descifrado que puede reconstituir la carga útil maliciosa original en tiempo de ejecución.</li>
    <li><strong>Ofuscación de Código:</strong> Manipulación intencional de la estructura, lógica y presentación del código para hacerlo más complejo y ocultar los patrones reconocibles del malware.</li>
  </ul>
  
  <p><strong>REFERENCIAS:</strong></p>
  <ul>
    <li><a href="https://blog.barracuda.com/2023/11/09/malware-101-signature-evasion-techniques">Malware 101: Signature Evasion Techniques</a></li>
    <li><a href="https://www.cyfirma.com/research/malware-detection-evasion-techniques/">Malware Detection Evasion Techniques</a></li>
  </ul>
</details>

<details>
  <summary><strong>Day 19: Behaviour-based Evasion Techniques</strong></summary>
  <p>El día de hoy he visto las diferentes técnicas de evasión basadas en el comportamiento del sistema que utiliza el malware para alterar sus acciones y características y evadir su detección, con algunos ejemplos reales.</p>
  
  <p><strong>Extracto:</strong></p>
  <ul>
    <li><strong>Detección de sandbox:</strong> El malware puede detectar ciertos comportamientos asociados con entornos de análisis y alterar su comportamiento para evadir el análisis.</li>
    <li><strong>Trickbot:</strong> Troyano bancario que se propaga principalmente a través de correos electrónicos de phishing y es utilizado para robar información financiera y credenciales de inicio de sesión. <a href="https://attack.mitre.org/software/S0266/">Referencia</a></li>
    <li><strong>Comprobación del entorno:</strong> Se evalúa el contexto en el que se está ejecutando el malware y puede alterar su comportamiento para evadir la detección.</li>
    <li><strong>Emotet:</strong> Emplea técnicas de comprobación del entorno para detectar análisis de seguridad y puede cambiar su comportamiento en consecuencia. <a href="https://attack.mitre.org/software/S0367/">Referencia</a></li>
    <li><strong>Vaciamiento de Procesos:</strong> El malware emplaza su propio código malicioso dentro de procesos legítimos del sistema para ejecutar acciones maliciosas en segundo plano.</li>
    <li><strong>Poweliks:</strong> Este malware busca un proceso legítimo en el sistema y luego inyecta su código dentro del proceso, reemplazando su funcionalidad legítima con la suya propia. <a href="https://attack.mitre.org/techniques/T1218/011/">Referencia</a></li>
  </ul>
</details>

<details>
  <summary><strong>Day 20: Inyección de malware en procesos y Malware sin archivos</strong></summary>
  <p>El día de hoy he visto las estrategias que utiliza el malware para insertar su código malicioso en procesos legítimos, así como también el malware que no es un archivo en sí mismo, sino código malicioso que opera completamente dentro de la memoria de una computadora, sin dejar rastro en el sistema de archivos.</p>
  
  <p><strong>Técnicas de Inyección de Procesos:</strong></p>
  <ul>
    <li><strong>Inyección de DLL:</strong> Inyección de procesos en la que un código malicioso inserta su propia Biblioteca de Enlaces Dinámicos (DLL) en un proceso legítimo que se está ejecutando en memoria.</li>
    <li><strong>Inyección de Código:</strong> Se inserta código malicioso en el espacio de memoria de un proceso legítimo, alterando su comportamiento para llevar a cabo acciones maliciosas.</li>
    <li><strong>Inyección de Hilos:</strong> El código malicioso crea un nuevo hilo dentro de un proceso legítimo e inyecta su carga útil en el flujo de ejecución de ese hilo.</li>
    <li><strong>Técnicas de Asignación/Escritura de Memoria:</strong> El malware se asigna dinámicamente memoria dentro del espacio de direcciones del proceso objetivo y luego escribe su carga útil en esa memoria asignada.</li>
  </ul>
  
  <p><strong>Técnicas de Malware Sin Archivos:</strong></p>
  <ul>
    <li><strong>Ejecución Basada en Memoria:</strong> El código malicioso se carga y ejecuta directamente en la memoria del sistema.</li>
    <li><strong>Técnicas de "Living-off-the-land" (LOLbins):</strong> Utilizan herramientas y procesos del sistema preexistentes y confiables para ejecutar actividades maliciosas, a menudo sin necesidad de crear nuevos archivos.</li>
    <li><strong>Ataques Basados en el Registro:</strong> Implican explotar el Registro de Windows con fines maliciosos.</li>
    <li><strong>Macros de Documentos:</strong> Se usan scripts integrados dentro de archivos de documentos para realizar acciones maliciosas al abrir el documento.</li>
  </ul>
  
  <p>Puedes encontrar más información y ejemplos detallados en los siguientes enlaces de referencia:</p>
  <ul>
    <li><a href="https://attack.mitre.org/software/S0154/">Ejemplo de Cobalt Strike utilizado en ataques de red dirigidos</a></li>
    <li><a href="https://attack.mitre.org/software/S0446/">Ejemplo de técnicas LOLbins utilizadas por Ryuk en ataques de ransomware</a></li>
    <li><a href="https://attack.mitre.org/software/S0384/">Ejemplo de ataques basados en el Registro utilizados por Dridex</a></li>
    <li><a href="https://attack.mitre.org/software/S0386/">Ejemplo de macros de documentos utilizados por Ursnif</a></li>
  </ul>
</details>

<details>
  <summary><strong>⁠Day 21: Detección de procesos irregulares</strong></summary>
  <p>El día de hoy, he visto que uno de los modos más comunes en que el malware intenta evitar la detección es haciéndose pasar por un proceso legítimo dentro de un sistema, así que he estado investigando cómo lo hace y cómo podemos detectarlo.</p>
  
  <p><strong>Extracto de técnicas que usa el malware para pasar desapercibido:</strong></p>
  <ul>
    <li><strong>Suplantación de procesos críticos:</strong> El malware puede hacerse pasar por procesos legítimos ejecutándose bajo un nombre similar. Una forma de detectar este malware es usar algoritmos de similitud de cadenas para buscar cadenas que no sean iguales pero tampoco muy diferentes.</li>
    <li><strong>Ubicaciones ejecutables inusuales:</strong> El malware puede ejecutarse desde ubicaciones inusuales para dificultar su detección. También podemos ver cómo algunos aprovechan ubicaciones específicas como parte de sus tácticas de evasión y secuestro.</li>
    <li><strong>Jerarquía de procesos:</strong> La jerarquía de procesos es una característica fundamental tanto en sistemas Windows como en Unix. Al buscar irregularidades en esta jerarquía podemos identificar posibles suplantadores o procesos maliciosos.</li>
    <li><strong>Secuestro de procesos:</strong> Algunos tipos de malware pueden tomar el control de un proceso existente y ejecutar con su espacio de memoria y permisos. Esto puede lograrse mediante ganchos de función, modificaciones/patching en línea o inyección de DLL (Dynamic Link Library).</li>
  </ul>
</details>

<details>
  <summary><strong>Day 22: Detección de Movimiento Lateral</strong></summary>
  <p>El día de hoy he visto los puntos estratégicos cruciales en la detección de movimiento lateral en endpoints durante el threat hunting.</p>
  
  <p><strong>Extracto:</strong></p>
  <ul>
    <li><strong>Movimientos laterales y reconocimiento:</strong> Los atacantes avanzan lateralmente dentro de una red una vez que comprometen un punto de entrada inicial, recopilando información sobre usuarios, privilegios y sistemas accesibles para planificar sus siguientes movimientos.</li>
    <li><strong>Uso explícito de credenciales:</strong> La autenticación mediante credenciales explícitas es común en entornos Windows, pero representa una vulnerabilidad potencial que los atacantes pueden aprovechar. Es esencial implementar un monitoreo proactivo de las credenciales explícitas y establecer listas blancas para usuarios y aplicaciones autorizadas.</li>
    <li><strong>Monitoreo del registro y archivos del sistema:</strong> Tanto el registro como los archivos del sistema son objetivos principales para el malware en busca de persistencia y control. La auditoría del registro y el monitoreo de las marcas de tiempo de los archivos son prácticas esenciales para identificar cambios inusuales que podrían indicar actividad maliciosa.</li>
  </ul>
</details>

<details>
  <summary><strong>⁠Day 23: Detección de malware en archivos del sistema</strong></summary>
  <p>En el threat hunting enfocado a los endpoint, es importante tener constancia de los archivos presentes en el sistema y las actividades anómalas. Hoy he estado investigando qué tener en cuenta al buscar amenazas a la hora de analizar los archivos y algunos ejemplos.</p>
  
  <p><strong>Extracto de los temas investigados:</strong></p>
  <ul>
    <li><strong>Nombres de archivo maliciosos conocidos:</strong> Ciertas familias de malware usan nombres predecibles en sus tácticas de infección y persistencia en sistemas comprometidos. Identificar estos nombres es una estrategia efectiva para un cazador de amenazas.</li>
    <li><strong>Extensiones de archivo:</strong> Los autores de malware utilizan diversas extensiones para sus ejecutables, como .exe, .bat, .cmd, .com, .lnk, .pif, .vbs, .scr y .wsh. También es importante considerar que otras extensiones pueden representar una amenaza potencial.</li>
    <li><strong>Anulación de izquierda a derecha:</strong> Es una técnica usada por atacantes para ocultar información maliciosa en nombres de archivos y textos, dificultando la detección de nombres de archivo maliciosos.</li>
  </ul>
</details>

<details>
  <summary><strong>⁠⁠Day 24: Data source de equipos para el Threat Hunting</strong></summary>
  <p>Los datos que podemos visualizar en los endpoints no ofrecen una visión detallada de la actividad en cada dispositivo. Esto es importante para poder detectar indicadores de compromiso y comportamientos anómalos. Hoy he estado repasando los diferentes puntos de recopilación de información que se pueden obtener de equipos con Windows/Linux.</p>
  
  <p><strong>Extracto sobre puntos importantes:</strong></p>
  <ul>
    <li><strong>AV Basado en el Host:</strong> Permite la detección de antivirus en máquinas individuales, con reglas personalizadas que pueden adaptarse a las necesidades de seguridad específicas de cada dispositivo.</li>
    <li><strong>Sistemas de Detección/Prevención de Intrusiones Basados en el Host:</strong>
      <ul>
        <li><strong>HIDS (Sistema de Detección de Intrusiones Basado en el Host):</strong> Detecta posibles amenazas y ataques en un sistema de host mediante la monitorización de la actividad del sistema en busca de cambios sospechosos y actividad de malware.</li>
        <li><strong>HIPS (Sistema de Prevención de Intrusiones Basado en el Host):</strong> Previene la actividad maliciosa en un sistema de host mediante el uso de análisis de comportamiento, control de aplicaciones y prevención de intrusos en la red.</li>
      </ul>
    </li>
    <li><strong>Registros de Antivirus:</strong> Estos registros pueden incluir eventos de detección de amenazas, actualizaciones de firmas, análisis programados y acciones tomadas por el software antivirus para mitigar las amenazas detectadas.</li>
    <li><strong>Firewalls Basados en el Host:</strong> Proporcionan visibilidad y control granulares sobre el tráfico de red en sistemas individuales. Los registros del firewall pueden analizarse para identificar patrones de tráfico sospechoso y actividades maliciosas.</li>
    <li><strong>Registros de Eventos de Windows:</strong> Estos registros proporcionan información detallada sobre los eventos del sistema, como intentos de inicio de sesión, instalaciones de software y errores del sistema. La revisión de estos registros puede ayudar a identificar actividades maliciosas y posibles puntos de compromiso en los sistemas Windows.</li>
  </ul>
</details>

<details>
  <summary><strong>⁠Day 25: Calidad de Datos y Metodologías</strong></summary>
  <p>Después de explorar las diferentes fuentes de datos, he investigado la importancia de la calidad de los datos en la caza de amenazas:</p>
  
  <p><strong>Calidad de Datos en la Caza:</strong></p>
  <ul>
    <li><strong>Objetivos de Calidad de Datos:</strong>
      <ul>
        <li>Mejora de la Productividad: Reducir el tiempo dedicado a corregir problemas de datos.</li>
        <li>Consistencia y Complejidad: La consistencia entre fuentes de datos facilita análisis complejos.</li>
        <li>Automatización Eficiente: Mejorar la calidad de datos optimiza los procesos de automatización.</li>
      </ul>
    </li>
    <li><strong>Importancia de la Calidad de Datos:</strong> Problemas comunes, como discrepancias en los campos de datos, impactan en la capacidad de detectar y responder a amenazas.</li>
    <li><strong>Metodología Básica:</strong>
      <ol>
        <li>Identificación de Fuentes de Datos</li>
        <li>Determinación de Fuentes Necesarias</li>
        <li>Mapeo de Fuentes de Datos</li>
        <li>Definición de Dimensiones de Calidad</li>
        <li>Desarrollo de Sistema de Puntuación</li>
        <li>Evaluación de la Calidad</li>
      </ol>
    </li>
    <li><strong>Puntuación General:</strong> Integrar puntuaciones de calidad de datos con evaluaciones de talento y tecnología nos proporciona una métrica completa para medir la efectividad en los compromisos de caza de amenazas.</li>
  </ul>
</details>

<details>
  <summary><strong>⁠Day 25: Calidad de Datos y Metodologías</strong></summary>
  <p>Después de explorar las diferentes fuentes de datos, he investigado la importancia de la calidad de los datos en la caza de amenazas:</p>
  
  <p><strong>Calidad de Datos en la Caza:</strong></p>
  <ul>
    <li><strong>Objetivos de Calidad de Datos:</strong>
      <ul>
        <li>Mejora de la Productividad: Reducir el tiempo dedicado a corregir problemas de datos.</li>
        <li>Consistencia y Complejidad: La consistencia entre fuentes de datos facilita análisis complejos.</li>
        <li>Automatización Eficiente: Mejorar la calidad de datos optimiza los procesos de automatización.</li>
      </ul>
    </li>
    <li><strong>Importancia de la Calidad de Datos:</strong> Problemas comunes, como discrepancias en los campos de datos, impactan en la capacidad de detectar y responder a amenazas.</li>
    <li><strong>Metodología Básica:</strong>
      <ol>
        <li>Identificación de Fuentes de Datos</li>
        <li>Determinación de Fuentes Necesarias</li>
        <li>Mapeo de Fuentes de Datos</li>
        <li>Definición de Dimensiones de Calidad</li>
        <li>Desarrollo de Sistema de Puntuación</li>
        <li>Evaluación de la Calidad</li>
      </ol>
    </li>
    <li><strong>Puntuación General:</strong> Integrar puntuaciones de calidad de datos con evaluaciones de talento y tecnología nos proporciona una métrica completa para medir la efectividad en los compromisos de caza de amenazas.</li>
  </ul>
</details>

<details>
  <summary><strong>Day 26: Ejemplos de búsqueda de threats</strong></summary>
  <p>El otro día consulté dónde buscar las principales fuentes de datos de las que disponemos a la hora de buscar amenazas. Hoy he visto, en algunos casos prácticos más en detalle, qué tipo de amenazas podemos detectar en diferentes fuentes.</p>
  
  <p><strong>Registros de Proxy:</strong></p>
  <ul>
    <li><strong>Tráfico no autorizado:</strong> Identificar cualquier tráfico que se envíe a través de puertos no autorizados, como el puerto 22, que podría indicar intentos de exfiltración de datos.</li>
    <li><strong>Patrones de conexión:</strong> Buscar conexiones que exhiban patrones consistentes de bytes de entrada y salida, lo que podría ser una señal de que se está utilizando una técnica de balizamiento para comunicarse con un servidor de comando y control.</li>
  </ul>
  
  <p><strong>Registros de Windows:</strong></p>
  <ul>
    <li><strong>Inicio de sesión con credenciales explícitas:</strong> Filtrar eventos de inicio de sesión que utilicen credenciales explícitas, ya que esto podría indicar intentos de movimiento lateral por parte de un atacante.</li>
    <li><strong>Cambios en grupos privilegiados:</strong> Monitorear los cambios en los grupos privilegiados, ya que esto podría indicar intentos de escalada de privilegios por parte de un intruso.</li>
    <li><strong>Intentos de inicio de sesión fallidos:</strong> Buscar patrones de intentos de inicio de sesión fallidos, especialmente aquellos que provienen de múltiples cuentas, lo que podría indicar un intento de ataque de fuerza bruta.</li>
  </ul>
  
  <p><strong>Registros de Antivirus:</strong></p>
  <ul>
    <li><strong>Detección de programas de volcado de contraseñas:</strong> Identificar cualquier detección de programas conocidos de volcado de contraseñas, como pwdump o mimikatz, ya que esto podría indicar intentos de robo de credenciales.</li>
    <li><strong>Ejecuciones de programas desconocidos:</strong> Buscar ejecuciones de programas desconocidos que podrían ser herramientas maliciosas utilizadas por un atacante para comprometer el sistema.</li>
  </ul>
</details>

<details>
  <summary><strong>⁠⁠Day 27: Hunting en entornos de endpoints</strong></summary>
  <p>El día de hoy he actualizado toda la información recopilada durante estos días referente al Threat Hunting en Endpoints.</p>
  
  <p>Los puntos detallados son:</p>
  <ol>
    <li><a href="https://nottaroff.github.io/workspace/docs/100%20days/5.%20Hunting%20en%20entornos%20de%20endpoint/#51-técnicas-de-ocultación-de-malware-" target="_blank">5.1 Técnicas de Ocultación de Malware</a></li>
    <li><a href="https://nottaroff.github.io/workspace/docs/100%20days/5.%20Hunting%20en%20entornos%20de%20endpoint/#52-descubriendo-procesos-irregulares" target="_blank">5.2 Descubriendo procesos irregulares</a></li>
    <li><a href="https://nottaroff.github.io/workspace/docs/100%20days/5.%20Hunting%20en%20entornos%20de%20endpoint/#54-técnicas-de-adquisición-de-datos-en-threat-hunting" target="_blank">5.3 Detección de movimiento Lateral</a></li>
    <li><a href="https://nottaroff.github.io/workspace/docs/100%20days/5.%20Hunting%20en%20entornos%20de%20endpoint/#54-técnicas-de-adquisición-de-datos-en-threat-hunting" target="_blank">5.4 Técnicas de Adquisición de Datos en Threat Hunting</a></li>
  </ol>
</details>

<details>
  <summary><strong>Day 28: Detección de conexiones de larga duración</strong></summary>
  <p>El día de hoy he creado un pequeño laboratorio con una VM Ubuntu. Utilizando Wireshark, Zeek y Rita con el objetivo de identificar conexiones de red de larga duración.</p>
  <p>Puedes acceder al laboratorio en el siguiente enlace: <a href="https://activecm.github.io/threat-hunting-labs/long_connections/" target="_blank">Laboratorio de conexiones de larga duración</a></p>
  <p>Wireshark permite visualizar y analizar paquetes de red, mientras que Zeek genera registros detallados de la actividad de la red. Ambas herramientas son fundamentales para identificar conexiones TCP y UDP de larga duración, lo que se logra ordenando las conexiones por duración. Es importante tener en cuenta que las diferencias en el manejo de conexiones UDP entre Wireshark y Zeek pueden influir en los resultados del análisis.</p>
  <p>Además, es crucial considerar el comportamiento del malware, que puede generar conexiones intermedias de duración media para evitar la detección de conexiones de larga duración. Por lo tanto, es necesario evaluar no solo la duración de las conexiones, sino también su naturaleza y posibles implicaciones de seguridad.</p>
</details>

<details>
  <summary><strong>⁠⁠Day 29: Sentinel Threat Hunting Course</strong></summary>
  <p>El día de hoy he empezado un curso de Threat Hunting en los recursos de SentinelOne. El curso es realizar hunting con el entorno de Sentinel, pero también tiene teoría introductoria y ejemplos de uso.</p>
  <p>Uno de los hallazgos que identifiqué durante el ejemplo práctico fue la detección de una conexión entrante a un punto final a través del protocolo RDP desde una dirección IP externa. Además, se observaron conexiones entrantes en puertos específicos, lo que podría indicar un posible abuso de herramientas como PSExec.</p>
  <p>También detecté la ejecución de comandos de sistema (cmd.exe) y scripts de PowerShell (powershell.exe), utilizados para acciones como la creación de archivos y conexiones salientes a recursos externos.</p>
  <h3>Consultas Utilizadas:</h3>
  <ul>
    <li>Filtrado de conexiones RDP entrantes desde direcciones IP externas:
      <pre>DstPort = "3389" AND SrcIP Not In ("10.0.1.1", "10.0.1.10")</pre>
    </li>
    <li>Búsqueda de instancias de PSExec no asociadas al usuario "administrador":
      <pre>ProcessName contains "PSExec" AND User not Contains "administrador"</pre>
    </li>
    <li>Identificación de actividades de PowerShell conectándose a través del puerto 21:
      <pre>Process contains "Powershell" AND DstPort = "21" AND ProcessCMD contains "iex"</pre>
    </li>
    <li>Detección de comandos de PowerShell involucrando FTP y ejecución de comandos:
      <pre>ProcessName contains "Powershell" AND ProcessCmd contains "ftp" AND ProcessCMD contains "iex"</pre>
    </li>
  </ul>
</details>

<details>
  <summary><strong>⁠⁠Day 30: Sentinel Threat Hunting Course II</strong></summary>
  <p>El día de hoy he seguido con el curso de Sentinel University sobre lo que tenemos que tener en cuenta a la hora de usar la opción de Visibility - Hunting.</p>
  <p>SentinelOne es un XDP que identifica y neutraliza posibles riesgos de seguridad en los sistemas. Al utilizar la funcionalidad de Deep Visibility, podemos examinar exhaustivamente eventos, artefactos y datos de objetos para detectar cualquier actividad sospechosa o maliciosa que pueda pasar desapercibida para los sistemas de detección tradicionales.</p>
  <p>Cuando realizamos threat hunting en Sentinel, es importante tener en cuenta que buscamos nuevas variantes de malware que aún no han sido detectadas por el sistema. Estas amenazas pueden ser únicas y escapar de la detección de inteligencia artificial. Por lo tanto, es crucial marcar toda la línea de tiempo como sospechosa o maliciosa y examinar cada evento en su totalidad para encontrar cualquier indicio de actividad no autorizada.</p>
  <p>Una vez identificada la actividad sospechosa, podemos utilizar la información detallada proporcionada por los objetos de visibilidad profunda para investigar la causa raíz de la amenaza. Esto implica encontrar todos los artefactos relacionados con el incidente y determinar hasta qué punto el malware ha infiltrado nuestros sistemas.</p>
  <p>Además de responder a las amenazas detectadas, la información recopilada durante la caza de amenazas nos permite establecer reglas y políticas de seguridad más efectivas para prevenir futuros ataques. Con una comprensión clara de cómo opera el malware y qué indicadores de compromiso buscar, podemos fortalecer nuestra postura de seguridad y proteger mejor nuestros sistemas.</p>
</details>

<details>
  <summary><strong>Day 31: Sentinel Threat Hunting Course Deep Visibility</strong></summary>
  <p>Siguiendo el curso de Threat Hunting con SentinelOne, el día de hoy he visto el uso de la funcionalidad de Deep Visibility. Este proceso se divide en varias etapas que abarcan desde la preparación hasta la identificación de actividades maliciosas, la obtención de inteligencia y la ejecución de consultas para descubrir posibles amenazas.</p>
  <p>En la fase de preparación, destaca la importancia de identificar cualquier acción que otorgue a nuestro equipo una ventaja sobre los atacantes. La funcionalidad de Deep Visibility recopila una gran cantidad de información, podremos modificar el tipo de registro que realizará Sentinel al configurar la privacidad de Deep Visibility en las políticas de Sentinel One.</p>
  <p>La fase de identificación se centra en reconocer una serie de eventos como maliciosos y obtener inteligencia sobre las amenazas o vulnerabilidades que se van a investigar. Destacando la importancia de buscar evidencia, formular artefactos buscables y encontrar eventos que puedan llamar la atención del equipo de seguridad.</p>
  <p>Finalmente, se detalla la ejecución de queries para analizar los datos recopilados. En Sentinel tenemos presente diferentes tipos de consultas disponibles, como las relacionadas con la fecha y hora, numéricas, de enumeración, de cadenas de caracteres y booleanas. Se han detallado el uso de declaraciones AND para dividir consultas en partes más pequeñas y el manejo de errores al utilizar expresiones regulares.</p>
</details>

<details>
  <summary><strong>⁠Day 32: SentinelOne Threat Hunting Course Hunter</strong></summary>
  <p>Hoy he visto otras herramientas de SentinelOne diseñadas para el Threat Hunting. En particular, me he centrado en la utilidad de Hunter, una extensión del navegador que recopila datos de páginas web y genera consultas en Deep Visibility. Estas consultas están diseñadas específicamente para identificar indicadores que podrían sugerir la presencia de malware.</p>
  <p>Una característica interesante de Hunter es su biblioteca de consultas, que automatiza la búsqueda de malware con actualizaciones más frecuentes que las disponibles en la consola de gestión estándar de SentinelOne. Esta capacidad de actualización constante proporciona una ventaja significativa en la detección proactiva de amenazas.</p>
  <p>Además de explorar Hunter, he examinado varios enfoques para la búsqueda de malware dentro de la consola de gestión. Esto incluye la capacidad de modificar libremente los módulos dentro del registro, lo que permite una adaptación más precisa a las necesidades específicas de la red y del entorno de amenazas.</p>
  <p>Por último, he utilizado la consulta EventType "File Creation" para identificar rápidamente archivos potencialmente maliciosos. Es importante tener en cuenta que los archivos del Explorador pueden representar una fuente de problemas en los endpoints, por lo que se recomienda una evaluación cuidadosa de su inclusión en las investigaciones de amenazas.</p>
</details>

<details>
  <summary><strong>⁠⁠Day 33: Práctica Threat Hunting con SentinelOne</strong></summary>
  <p>El día de hoy he realizado el laboratorio de S1 University para el threat hunting con SentinelOne con el propósito de practicar la identificación y mitigación de amenazas, en este caso, un troyano de acceso remoto (RAT) en un entorno Linux mediante el uso de la Consola de Gestión de SentinelOne.</p>
  <p><strong>Pasos Realizados durante la práctica:</strong></p>
  <ul>
    <li>Preparación para la Infección:</li>
    <ul>
      <li><code>sudo nc -l -p 666</code>: Puerto de escucha con Netcat.</li>
      <li><code>sudo /home/forensics/Desktop/yoyobins.sh</code>: Ejecución del malware.</li>
      <li><code>sudo netstat -peanut | grep 172.245.7.14:666</code>: Lista de conexiones de red activas al servidor C2.</li>
    </ul>
    <li>Investigación en la Consola de SentinelOne:</li>
    <ul>
      <li>Uso de consultas de Deep Visibility para identificar la actividad maliciosa y asociar un Storyline Id con la cadena de infección.</li>
      <li>Ejemplos de consultas utilizadas:</li>
      <ul>
        <li><code>NetConnOutCount > "5"</code></li>
        <li><code>DstIP RegExp "..."</code></li>
        <li><code>EndpointName ContainsCIS "" AND ChildProcCount > "50"</code></li>
        <li><code>DstIP RegExp "\\b(?!10\\.|192\\.168\\.|172\\.(?:1[6-9]|2[0-9]|3[01])\\.)(?:25[0-5]|2[0-4][0-9]|[01]?[0-9]?[0-9])(?:\\.(?:25[0-5]|2[0-4][0-9]|[01]?[0-9]?[0-9])){3}\\b" AND SrcProcSignedStatus = "unsigned"</code></li>
      </ul>
      <li>Identificación del Storyline Id del proceso malicioso y marcado como amenaza.</li>
    </ul>
    <li>Análisis Detallado:</li>
    <ul>
      <li>Inspección del árbol de procesos para comprender el comportamiento del malware.</li>
    </ul>
    <li>Mitigación de Amenazas:</li>
    <ul>
      <li>Ejecución de acciones de mitigación seleccionando "QUARANTINE" y marcando las amenazas como resueltas y verdaderas positivas.</li>
      <li>Verificación de la cuarentena y mitigación de los archivos maliciosos.</li>
    </ul>
  </ul>
</details>

