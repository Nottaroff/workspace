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
