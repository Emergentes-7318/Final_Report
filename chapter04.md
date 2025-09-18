# CAPÍTULO IV: STRATEGIC-LEVEL SOFTWARE DESIGN

---

### 4.1. STRATEGIC-LEVEL ATTRIBUTE-DRIVEN DESIGN

#### 4.1.1. Design Purpose

El propósito del diseño arquitectónico de DocMind es crear una plataforma de inteligencia artificial escalable, confiable y segura que transforme documentos complejos en información útil y accionable. La arquitectura debe soportar el análisis de grandes volúmenes de datos no estructurados, garantizando respuestas rápidas y precisas con una experiencia de usuario fluida. El diseño debe priorizar la **escalabilidad** y la **disponibilidad** para cumplir con la misión de ser una herramienta líder global en el análisis de documentos.

---

#### 4.1.2. Attribute-Driven Design Inputs

##### 4.1.2.1. Primary Functionality (Primary User Stories)

| ID    | Título                     | Descripción                                                                                                | Prioridad |
|-------|----------------------------|------------------------------------------------------------------------------------------------------------|-----------|
| US002 | Carga de Documento Único   | Como usuario, quiero subir un documento PDF para analizarlo.                                               | 8         |
| US005 | Preguntas en Lenguaje Natural | Como usuario, quiero hacer preguntas sobre el documento para obtener respuestas.                             | 8         |
| US007 | Visualización de Referencia  | Como usuario, quiero ver la fuente original de la respuesta dentro del documento.                          | 8         |
| US008 | Resumen del Documento        | Como usuario, quiero un resumen del documento para ahorrar tiempo de lectura.                                | 8         |
| US009 | Comparación de Documentos | Como usuario, quiero comparar dos o más documentos para identificar coincidencias y discrepancias.           | 8         |
| US013 | Exportación de Reportes    | Como usuario, quiero exportar resultados en formatos estándar como PDF o Word.                             | 5         |

---

##### 4.1.2.2. Quality Attribute Scenarios

| Atributo        | Escenario                                                                                                     | Estímulo                                                                 | Respuesta                                                                       | Medida                                                                    |
|-----------------|---------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------|---------------------------------------------------------------------------------|---------------------------------------------------------------------------|
| **Rendimiento** | El sistema debe ser rápido al procesar documentos grandes.                                                | Un usuario sube un PDF de 500 páginas.                                   | El sistema procesa el documento y está listo para responder consultas.      | El tiempo de procesamiento es menor a 2 minutos.                              |
| **Escalabilidad** | La plataforma debe manejar un alto volumen de usuarios simultáneos sin degradación.                     | 100 usuarios concurrentes suben documentos de gran tamaño.                 | El sistema mantiene su tiempo de respuesta promedio.                        | La degradación del rendimiento es imperceptible.                               |
| **Confiabilidad** | El sistema debe recuperarse de fallas temporales.                                                           | Un usuario experimenta una interrupción de conexión durante la carga.    | La plataforma reanuda la carga automáticamente al recuperar la conexión.  | La pérdida de progreso es nula.                                             |
| **Seguridad** | Los datos de los usuarios deben estar protegidos de accesos no autorizados.                                  | Un atacante intenta acceder a los documentos privados de un usuario.     | El sistema impide el acceso no autorizado y los datos están cifrados.   | El acceso no autorizado es bloqueado y la información no es visible.       |
| **Usabilidad** | La interfaz de usuario debe ser fácil de usar.                                                            | Un nuevo usuario intenta subir su primer documento.                      | El usuario completa el proceso sin ayuda externa.                           | El tiempo para completar la tarea es menor a 30 segundos.                 |

---

##### 4.1.2.3. Constraints

| Restricción                                                                                              |
|----------------------------------------------------------------------------------------------------------|
| La plataforma debe ser **Cloud-Native**, utilizando servicios de nube.                                             |
| El sistema debe ser **compatible con archivos PDF** de hasta 500 páginas.                                               |
| La solución debe integrarse con **Google Drive** para la carga de documentos.                                        |
| El diseño debe utilizar **modelos de lenguaje natural (NLP)** para el procesamiento de texto.                             |

---

#### **4.1.3. Architectural Drivers Backlog**

| Driver ID | Requisito                                                              | Tipo de Requisito      | Prioridad |
|-----------|------------------------------------------------------------------------|------------------------|-----------|
| DRV-01    | Capacidad para procesar documentos PDF de gran tamaño.                 | Funcional              | Alta      |
| DRV-02    | El sistema debe ser capaz de escalar horizontalmente para 100+ usuarios. | Calidad: Escalabilidad | Alta      |
| DRV-03    | Respuestas rápidas y precisas a preguntas en lenguaje natural.          | Funcional/Calidad: Rendimiento| Alta |
| DRV-04    | Integración con servicios de nube (Cloud-Native).                        | Restricción            | Alta      |
| DRV-05    | Interfaz intuitiva y fácil de usar para cargar documentos y chatear.  | Calidad: Usabilidad    | Media     |
| DRV-06    | Garantizar la seguridad y privacidad de los documentos.                | Calidad: Seguridad     | Alta      |
| DRV-07    | Soporte para la exportación de resultados.                             | Funcional              | Media     |

---

#### **4.1.4. Architectural Design Decisions**

| Decisión Arquitectónica                                                              | Racional                                                                                              |
|--------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| **Arquitectura de Microservicios** | Separar funcionalidades para permitir que cada servicio escale de forma independiente.                  |
| **Uso de Serverless Computing** | Optimizar costos y permitir la escalabilidad automática para el procesamiento de documentos.          |
| **Base de Datos NoSQL** | Almacenar el contenido de los documentos procesados de manera eficiente.                              |
| **API Gateway para el Frontend** | Centralizar la seguridad, el enrutamiento y la gestión de las solicitudes.                           |
| **Cifrado de Datos (Data Encryption)** | Garantizar que los datos estén protegidos tanto en tránsito como en reposo.                         |

---

#### **4.1.5. Quality Attribute Scenario Refinements**

| Atributo        | Refinamiento y Descripción                                                                                              |
|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| **Rendimiento** | Se monitoreará el tiempo de respuesta de las funciones serverless para asegurar que el procesamiento no exceda los 2 minutos. |
| **Escalabilidad** | Se configurará la escalabilidad automática de los microservicios y se realizarán pruebas de carga para simular 100 usuarios. |
| **Confiabilidad** | Se implementará un mecanismo de reintento automático para manejar fallos temporales en la capa de carga de documentos. |
| **Seguridad** | Se auditará la implementación de cifrado de extremo a extremo y se realizarán pruebas de penetración.                    |

## 4.2. Strategic-Level Domain-Driven Design
### 4.2.1. EventStorming
### 4.2.2. Candidate Context Discovery
### 4.2.3. Domain Message Flows Modeling
### 4.2.4. Bounded Context Canvases
### 4.2.5. Context Mapping

## 4.3. Software Architecture
### 4.3.1. Software Architecture System Landscape Diagram
### 4.3.1. Software Architecture Context Level Diagrams
### 4.3.2. Software Architecture Container Level Diagrams
### 4.3.3. Software Architecture Deployment Diagrams
