---
title: 3. Técnicas y herramientas del Threat Hunting ⚒️
layout: default
has_toc: false
nav_order: 4
parent: 100 days challenge 🗻

---

# 3. Técnicas y herramientas del Threat Hunting ⚒️
---
## Índice 

- [3.1 Técnicas comunes del Threat Hunting ](https://nottaroff.github.io/workspace/docs/100%20days/3.%20Tecnicas%20y%20Herramientas/#31-técnicas-comunes-del-threat-hunting-) 
- [3.2 Herramientas para la Caza de Amenazas ](https://nottaroff.github.io/workspace/docs/100%20days/3.%20Tecnicas%20y%20Herramientas/#32-herramientas-para-la-caza-de-amenazas-)


---
## 3.1 Técnicas comunes del Threat Hunting 🥷

Algunas de las técnicas mas comunes utilizadas en el Threat Hunting:

{: .detail }
**Búsqueda 🔎**                                                                                                                                            
Es fundamental establecer criterios de búsqueda específicos. Se proceden a examinar los datos en busca de elementos especificos. Es importante evitar que los criterios de búsqueda sean demasiado amplios, ya que esto podría generar una gran cantidad de resultados que consumirían mucho tiempo de procesamiento. Del mismo modo, criterios excesivamente estrictos pueden limitar los resultados, dificultando la obtención de conclusiones relevantes.

{: .detail }
**Análisis de Agrupamiento (Clustering)🧪**                                                                                                                         
Implica clasificar grupos de información similar basándose en características específicos dentro de un conjunto de datos extenso.Utilizan técnicas de inteligencia artificial para procesar grandes volúmenes de datos, como registros de eventos. El resultado es un informe que utiliza los parámetros establecidos para identificar patrones y comportamientos relevantes. El análisis de agrupamiento es especialmente útil para detectar anomalías y comportamientos inusuales.

{: .detail }
**Agrupación(Grouping) 🪆**                                                                                                                                         
A diferencia del análisis de agrupamiento, la agrupación implica identificar circunstancias en las cuales múltiples artefactos únicos aparecen juntos, basándose en criterios específicos. Esta técnica parte de un conjunto de datos previamente marcado como sospechoso y busca relaciones entre los artefactos. La agrupación es útil para encontrar instancias relacionadas de artefactos únicos, lo que puede proporcionar insights adicionales sobre posibles amenazas.

{: .detail }
**Conteo de Pila (Stack Counting)🔼**                                                                                                                              
El objetivo es identificar similitudes dentro de un conjunto de datos que contienen valores similares o idénticos. Detectar valores atípicos en métricas específicas puede indicar la presencia de actividades sospechosas o anomalías. Sin embargo, el conteo de pila puede resultar menos efectivo al procesar conjuntos de datos grandes o diversos. Esta técnica es útil para analizar comportamientos repetitivos o inusuales en los datos, como patrones de tráfico saliente en puertos específico.

## 3.2 Herramientas para la Caza de Amenazas 🔩

En esta sección me gustaría explicar el modelo de madurez del Threat Hunting. Este modelo, es una referencia para entender si nuestra entorno esta preparada o no para realizar este tipo de actividades, y para ello, lo primero es determinar nuestro nivel de madurez. Desde un punto de vista corporativo.

El nivel de madurez vendrá definido por una serie de factores como son:
- La cantidad y calidad de los datos que se recopilan de nuestra infraestructura TI.
- De qué manera se pueden visualizar y analizar los diferentes tipos de datos recopilados.
- Qué tipo de análisis automatizado se puede aplicar a los datos para mejorar la información que reciben los analistas.

### The Hunting Maturity Model (HMM)
El modelo de madurez en caza describe cinco niveles de capacidad organizacional en caza, que van desde HM0 (el menos capaz) hasta HM4 (el más).

![Captura-de-pantalla-2024-04-21-195010.png](https://i.postimg.cc/DZR5WGdR/Captura-de-pantalla-2024-04-21-195010.png)


| **HM0 - INICIAL**       |
|:-------------|
|En HM0, una organización depende principalmente de herramientas de alerta automatizadas como IDS, SIEM para detectar actividad maliciosa en la empresa. Aunque pueden incorporar feeds de actualizaciones de firmas o indicadores de inteligencia de amenazas, su enfoque se centra en la resolución de alertas. Las organizaciones HM0 no recopilan mucha información de sus sistemas informáticos y, por lo tanto, tienen una capacidad limitada para encontrar amenazas proactivamente.          | 

|**HM1 - MÍNIMO**|
|:-------------|
|Se incorporan incorpora búsquedas de indicadores de inteligencia de amenazas. Rastreando informes de amenazas y recopilando datos en un lugar central como un SIEM. Este nivel permite alguna forma de caza, aunque sea mínima. Por ejemplo, ampliación de herramientas de gestión de registros (SIEM) para incluir más fuentes de datos, soluciones de gestión de amenazas y vulnerabilidades (TVM), plataformas de inteligencia de amenazas (TIP).|

|**HM2 - PROCEDIMENTAL**|
|:-------------|
|En HM2, las organizaciones aplican procedimientos de caza conocidos, basados en análisis específicos de datos. Aunque pueden aprender y aplicar procedimientos desarrollados por otros, su capacidad para crear nuevos procedimientos es limitada. La recopilación de datos es amplia, ya que confían en análisis de menor frecuencia. Como por ejemplo, plataformas de seguridad de la información avanzadas (SOAR), herramientas de detección y respuesta de endpoints (EDR), herramientas de análisis de malware (sandboxing).|

|**HM3 - INNOVADOR**|
|:-------------|
|En HM3, Crear nuevos procedimientos de analisis de datos. La recopilación de datos es completa y su efectividad en la detección y combate de amenazas es alta.|

|**HM4 - LÍDER**|
|:-------------|
|En HM4, las organizaciones automatizan con éxito los procesos de caza, liberando a los analistas para mejorar los procesos existentes o crear nuevos. Son altamente efectivas en la resistencia contra adversarios, gracias a la mejora continua de su programa de detección. En este punto se tiene una gran base de datos. Las herramientas de analisis de Threat Intelligece, Manual hunting solutions estan automatizadas. |



### **Uso del modelo de madurez**

Un modelo de madurez proporciona una guía clara para aquellos que desean adentrarse en la caza, ayudándoles a entender qué capacidad inicial sería adecuada.

Para las organizaciones que ya cuentan con equipos de caza, el HMM es útil para evaluar su nivel de madurez actual y trazar una ruta de mejora. Los equipos pueden comparar sus capacidades con las descritas en el modelo y luego planificar cómo desarrollar habilidades y capacidades de recolección de datos para alcanzar el próximo nivel de madurez. Es crucial tener claridad sobre la posición actual y los objetivos futuros para avanzar de manera efectiva.

![Captura-de-pantalla-2024-04-21-204423.png](https://i.postimg.cc/vHqSjntn/Captura-de-pantalla-2024-04-21-204423.png)
