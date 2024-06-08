---
title: 7. Hunting en entornos de cloud ☁️
layout: default
has_toc: false
nav_order: 9
parent: 100 days challenge 🗻

---

# 7.  Hunting en entornos de cloud ☁️
---
## Índice 

- [7.1 Desafíos de seguridad en entornos de nube ](https://nottaroff.github.io/workspace/docs/100%20days/7.%20Hunting%20en%20entornos%20de%20cloud/#71-desafíos-de-seguridad-en-entornos-de-nube) 
- [7.2 Técnicas específicas de la nube](https://nottaroff.github.io/workspace/docs/100%20days/7.%20Hunting%20en%20entornos%20de%20cloud/#72-técnicas-específicas-de-la-nube)
- [7.3 Asegurando cargas de trabajo en la nube](https://nottaroff.github.io/workspace/docs/100%20days/7.%20Hunting%20en%20entornos%20de%20cloud/#73-asegurando-cargas-de-trabajo-en-la-nube)

---


## 7.1 Desafíos de seguridad en entornos de nube 🧗🏻

La adopción de servicios en la nube presenta varios desafíos de seguridad únicos:

|**Visibilidad y Control**|
|Los entornos de nube son dinámicos y pueden cambiar rápidamente. Esto dificulta tener una visibilidad completa y control sobre todos los activos y actividades.|
|**Multi-Tenancy**| 
|Los proveedores de servicios en la nube alojan datos de múltiples clientes en la misma infraestructura física. Esto puede generar riesgos adicionales si las medidas de aislamiento no son adecuadas.|
|**Configuraciones Incorrectas**|
|Las configuraciones predeterminadas o mal configuradas pueden abrir puertas a vulnerabilidades. Errores como permisos excesivos o configuraciones de red inapropiadas son comunes.|
|**Responsabilidad Compartida**|
|En la nube, la seguridad es una responsabilidad compartida entre el proveedor y el cliente. Esto puede llevar a malentendidos sobre quién es responsable de qué aspectos de la seguridad.|
|**Comoditización de la Seguridad**: |
|Las soluciones de seguridad pueden no estar completamente adaptadas a las necesidades específicas de cada organización debido a la naturaleza estandarizada de los servicios cloud.|

## 7.2 Técnicas específicas de la nube 🏗️

Para cazar amenazas en entornos de nube, se pueden aplicar varias técnicas específicas:

|**Monitoreo de Logs**|
|Analizar logs de eventos, acceso y auditoría proporcionados por el proveedor de servicios en la nube (por ejemplo, AWS CloudTrail, Azure Monitor) para detectar comportamientos inusuales o sospechosos.|
|**Uso de Herramientas Nativas de Seguridad**|
|Herramientas como AWS GuardDuty, Azure Security Center y Google Cloud Security Command Center proporcionan capacidades avanzadas para detectar amenazas y vulnerabilidades.|
|**Análisis de Tráfico de Red**|
|Utilizar servicios como Amazon VPC Flow Logs o Google Cloud VPC Flow Logs para monitorear y analizar el tráfico de red dentro del entorno cloud.|
|**Integración de SIEM**|
|Integrar soluciones de gestión de eventos e información de seguridad (SIEM) como Splunk, ELK Stack o IBM QRadar con la infraestructura cloud para una correlación y análisis más profundos de eventos de seguridad.|
|**Automatización y Respuesta Orquestada (SOAR)**|
|Implementar plataformas de automatización y orquestación de respuesta de seguridad (SOAR) para automatizar tareas repetitivas y acelerar la respuesta ante incidentes.|
|**Threat Intelligence**|
|Utilizar feeds de inteligencia de amenazas y servicios de análisis para obtener información sobre las últimas amenazas y vulnerabilidades que puedan afectar al entorno cloud.|

## 7.3 Asegurando cargas de trabajo en la nube 🛡️

Para asegurar el funcionamiento correcto de las cargas de trabajo en la nube debemos de tener en cuenta los siguientes factores:

|**Seguridad en el Ciclo de Vida del Desarrollo (DevSecOps)**|
|Integrar prácticas de seguridad durante el desarrollo, como por ejemplo: revisiones de código, pruebas de seguridad y automatización de la implementación segura.|
|**Gestión de Identidades y Accesos (IAM)**|
|Implementar políticas estrictas de gestión de identidades y accesos para asegurar que solo las personas y servicios autorizados puedan acceder a los recursos críticos también es importante utilizar el principio de privilegio mínimo.|
|**Cifrado de Datos**|
|Asegurar que todos los datos estén cifrados.|
|**Seguridad de Redes**|
|Configurar y mantener adecuadamente las políticas de seguridad de red, como firewalls, segmentación de redes y controles de acceso basados en roles (RBAC).|
|**Evaluaciones de Seguridad Continuas**|
|Realizar evaluaciones de seguridad regulares, para poder identificar y remediar vulnerabilidades.|
|**Monitoreo y Respuesta a Incidentes**|
|Establecer capacidades robustas de monitoreo y respuesta a incidentes para detectar y mitigar amenazas en tiempo real.|
|**Cumplimiento legal**|
|Asegurar el cumplimiento de normativas y estándares de seguridad aplicables, como GDPR, HIPAA, y estándares específicos del sector. Implementar políticas y procedimientos efectivos para la gestión de la seguridad en la nube.|