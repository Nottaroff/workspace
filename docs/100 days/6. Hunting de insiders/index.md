---
title: 6. Hunting de insiders 👷🏻
has_toc: false
nav_order: 8
parent: 100 days challenge 🗻
layout: default
---

# 6. Hunting de insiders 👷🏻
---
## Índice 

- [6.1 Tipos de Amenazas Internas](https://nottaroff.github.io/workspace/docs/100%20days/6.%20Hunting%20de%20insiders/#61-tipos-de-amenazas-internas) 
- [6.2 Indicadores de Amenazas Internas](https://nottaroff.github.io/workspace/docs/100%20days/6.%20Hunting%20de%20insiders/#62-indicadores-de-amenazas-internas)
- [6.3 Estrategias para la Detección y Mitigación](https://nottaroff.github.io/workspace/docs/100%20days/6.%20Hunting%20de%20insiders/#63-estrategias-para-la-detección-y-mitigación)

---

{: .detail }
> Las amenazas internas son aquellas que tienen su origen en usuarios autorizados: empleados, contratistas, socios comerciales, etc. Estos de forma intencionada o accidental, hacen un uso indebido de su acceso legítimo, o cuyas cuentas son secuestradas por ciberdelincuentes.

## 6.1 Tipos de Amenazas Internas

1. ### **Personas internas malintencionadas**

    Empleados actuales o antiguos que hacen un mal uso intencionado de su acceso por venganza o beneficio económico.

    **La estrategia de mitigación que podríamos aplicar:** Gestión de acceso y monitoreo continuo de cuentas inactivas.

2. ### **Personas internas negligentes**:
    
    Usuarios que, por ignorancia o descuido, crean riesgos de seguridad, como caer en ataques de phishing o perder dispositivos con acceso a datos sensibles.

    **La estrategia de mitigación que podríamos aplicar:** Capacitación continua y políticas claras de manejo de datos.

3. ### **Personas internas comprometidas**:
    
    Usuarios legítimos cuyas credenciales son robadas y utilizadas por atacantes externos.

    **La estrategia de mitigación que podríamos aplicar:** Autenticación multifactor y monitorización de comportamientos anómalos.

### 6.2 Indicadores de Amenazas Internas

Los indicadores de amenazas internas pueden variar, pero algunos comunes incluyen:

- **Acceso no autorizado**: Intentos de acceder a datos o sistemas sin la debida autorización.
- **Cambio de comportamiento**: Cambios en los patrones de trabajo del usuario, como acceder a sistemas fuera del horario habitual.
- **Transferencia masiva de datos**: Copia o transferencia inusual de grandes cantidades de datos.
- **Uso de herramientas de hacking**: Instalación y uso de software que puede comprometer sistemas.
- **Acciones sospechosas**: Eliminación o modificación de registros de auditoría, intentos de desactivar sistemas de seguridad.
- **Alta tasa de errores**: Incremento en la cantidad de errores de acceso o intentos fallidos de autenticación.

### 6.3 Estrategias para la Detección y Mitigación

|**Políticas y Procedimientos de Seguridad** |
|Crear y comunicar directrices específicas sobre cómo deben ser utilizados los recursos tecnológicos y la información de la empresa, asegurando que todos los empleados conozcan y comprendan estas políticas para prevenir abusos o errores. Además, es crucial implementar procedimientos de respuesta a incidentes, desarrollando y manteniendo un plan de acción claro para responder a cualquier tipo de incidente de seguridad. |

|**Controles de Acceso**|
|Limitar el acceso a datos y sistemas solo a aquellos que lo necesitan. Aplicar el principio de mínimo privilegio garantiza que los usuarios tengan solo el acceso necesario para realizar sus funciones laborales, minimizando el riesgo de uso indebido o compromisos accidentales. Es igualmente importante revisar periódicamente estos permisos para asegurarse de que se mantengan apropiados y revocar cualquier acceso innecesario o no autorizado.|

|**Autenticación Multifactor (MFA)** |
|Implementar MFA para todas las cuentas, especialmente para acceder a sistemas críticos.|

|**Capacitación y Concienciación**|
|Realizar capacitaciones regulares sobre seguridad para educar a los empleados sobre las amenazas internas. Estas formaciones deben abarcar las mejores prácticas de seguridad, cómo manejar datos sensibles y las políticas de la empresa para mantener la seguridad de la información. Además de sensibilizar a los empleados sobre cómo reconocer y reportar actividades sospechosas, instruyéndolos sobre cómo identificar señales de posibles amenazas internas y cómo reportarlas adecuadamente para una pronta investigación y respuesta.|

|**Monitoreo Continuo**|
|Utilizar herramientas avanzadas como SIEM y UEBA para la supervisión continua de la actividad del usuario y la red.. Estas tecnologías recopilan, analizan y correlacionan datos de diferentes fuentes para detectar comportamientos anómalos y posibles incidentes de seguridad en tiempo real.|

|**Gestión de Identidad y Acceso (IAM)**|
|Gestionar las identidades de los usuarios, la autenticación y los permisos de acceso es esencial para mantener la seguridad. Implementar sistemas que administren de manera centralizada quién tiene acceso a qué recursos garantiza una gestión adecuada de las identidades y accesos.|

|**Análisis del Comportamiento del Usuario (UBA)**|
|Utilizar análisis avanzado de datos e IA para modelar los comportamientos básicos de los usuarios y detectar anomalías es una práctica efectiva. Integrar UBA con SIEM mejora la visibilidad y correlación de eventos de seguridad, permitiendo una detección más precisa y una respuesta más rápida a las amenazas.|

|**Seguridad Ofensiva**|
|Utilizar tácticas de adversario, como simulaciones de phishing y red team, para reforzar la seguridad de la red ayuda a identificar y corregir vulnerabilidades antes de que los atacantes las exploten. Realizar ciberataques simulados proporciona una comprensión práctica de las posibles amenazas y permite a la organización fortalecer sus defensas de manera proactiva.|