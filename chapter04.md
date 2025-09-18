# CAPÍTULO IV: STRATEGIC-LEVEL SOFTWARE DESIGN

---

### 4.1. STRATEGIC-LEVEL ATTRIBUTE-DRIVEN DESIGN

#### 4.1.1. DESIGN PURPOSE

El propósito del diseño arquitectónico de DocMind es crear una plataforma de inteligencia artificial escalable, confiable y segura que transforme documentos complejos en información útil y accionable. La arquitectura debe soportar el análisis de grandes volúmenes de datos no estructurados, garantizando respuestas rápidas y precisas con una experiencia de usuario fluida. [cite_start]El diseño debe priorizar la **escalabilidad** y la **disponibilidad** para cumplir con la misión de ser una herramienta líder global en el análisis de documentos. [cite: 1, 2]

---

#### 4.1.2. ATTRIBUTE-DRIVEN DESIGN INPUTS

[cite_start]Esta sección inicia con un texto de introducción y contiene las secciones para los tres tipos de Input para el proceso de diseño con ADD. [cite: 4]

##### 4.1.2.1. PRIMARY FUNCTIONALITY (PRIMARY USER STORIES)

[cite_start]A continuación, se detallan los Epics o User Stories más relevantes para la arquitectura de la solución. [cite: 6, 7]

| Epic / User Story ID | Título | Descripción | Criterios de Aceptación | Relacionado con (Epic ID) |
|---|---|---|---|---|
| US002 | Carga de Documento Único | Como usuario, quiero subir un documento PDF para analizarlo. | El documento se carga correctamente y se procesa para su análisis posterior. | EPIC-01 (Gestión de Documentos) |
| US005 | Preguntas en Lenguaje Natural | Como usuario, quiero hacer preguntas sobre el documento para obtener respuestas. | El sistema genera respuestas precisas y relevantes basadas en el contenido del documento. | EPIC-02 (Interacción con el Contenido) |
| US007 | Visualización de Referencia | Como usuario, quiero ver la fuente original de la respuesta dentro del documento. | La respuesta proporcionada incluye una referencia a la ubicación exacta dentro del documento. | EPIC-02 (Interacción con el Contenido) |
| US008 | Resumen del Documento | Como usuario, quiero un resumen del documento para ahorrar tiempo de lectura. | El sistema genera un resumen coherente y conciso que captura los puntos principales del documento. | EPIC-02 (Interacción con el Contenido) |
| US009 | Comparación de Documentos | Como usuario, quiero comparar dos o más documentos para identificar coincidencias y discrepancias. | El sistema identifica y muestra las similitudes y diferencias entre los documentos seleccionados. | EPIC-03 (Análisis Comparativo) |
| US013 | Exportación de Reportes | Como usuario, quiero exportar resultados en formatos estándar como PDF o Word. | Los resultados se exportan correctamente a los formatos solicitados. | EPIC-04 (Opciones de Exportación) |

---

##### 4.1.2.2. QUALITY ATTRIBUTE SCENARIOS

[cite_start]Esta sección incluye la especificación de la primera versión de los escenarios de atributos de calidad que tienen mayor impacto en la arquitectura de la solución. [cite: 12, 13]

| Atributo | Fuente | Estímulo | Artefacto | Entorno | Respuesta | Medida |
|---|---|---|---|---|---|---|
| **Rendimiento** | Usuario | Un usuario sube un PDF de 500 páginas. | Subsistema de procesamiento de documentos. | Carga normal de la plataforma. | El sistema procesa el documento y está listo para responder consultas. | El tiempo de procesamiento es menor a 2 minutos. |
| **Escalabilidad** | Alto volumen de usuarios. | 100 usuarios concurrentes suben documentos de gran tamaño. | Sistema completo. | Pico de usuarios simultáneos. | El sistema mantiene su tiempo de respuesta promedio. | La degradación del rendimiento es imperceptible. |
| **Confiabilidad** | Usuario | Un usuario experimenta una interrupción de conexión durante la carga. | Subsistema de carga de documentos. | Conexión inestable. | La plataforma reanuda la carga automáticamente al recuperar la conexión. | La pérdida de progreso es nula. |
| **Seguridad** | Atacante externo | Un atacante intenta acceder a los documentos privados de un usuario. | Capa de autenticación y de datos. | Operación del sistema. | El sistema impide el acceso no autorizado y los datos están cifrados. | El acceso no autorizado es bloqueado y la información no es visible. |
| **Usabilidad** | Nuevo usuario | Un nuevo usuario intenta subir su primer documento. | Interfaz de usuario. | Primer uso de la plataforma. | El usuario completa el proceso sin ayuda externa. | El tiempo para completar la tarea es menor a 30 segundos. |

---

##### 4.1.2.3. CONSTRAINTS

[cite_start]Esta sección incluye la especificación de restricciones, es decir, características que no pueden ser negociadas y son impuestas por el cliente o el propio negocio como guía para la elaboración de la solución. [cite: 24, 25]

| Technical Story ID | Título | Descripción | Criterios de Aceptación | Relacionado con (Epic ID) |
|---|---|---|---|---|
| TST-01 | Cloud-Native | La plataforma debe ser **Cloud-Native**, utilizando servicios de nube. | El 100% de los servicios se implementan en una infraestructura de nube. | EPIC-05 (Infraestructura) |
| TST-02 | Compatibilidad PDF | El sistema debe ser **compatible con archivos PDF** de hasta 500 páginas. | El sistema procesa correctamente archivos PDF hasta el límite de 500 páginas. | EPIC-01 (Gestión de Documentos) |
| TST-03 | Integración Google Drive | La solución debe integrarse con **Google Drive** para la carga de documentos. | El usuario puede importar documentos directamente desde su cuenta de Google Drive. | EPIC-01 (Gestión de Documentos) |
| TST-04 | Uso de NLP | El diseño debe utilizar **modelos de lenguaje natural (NLP)** para el procesamiento de texto. | Los modelos de NLP procesan con precisión el texto para generar respuestas y resúmenes. | EPIC-02 (Interacción con el Contenido) |

---

#### 4.1.3. ARCHITECTURAL DRIVERS BACKLOG

[cite_start]Esta sección establece el conjunto de Architectural Drivers que fueron acordados por el equipo, resultado del proceso iterativo. [cite: 30, 31, 32, 33]

| Driver ID | Título de Driver | Descripción | Importancia para Stakeholders | Impacto en Architecture Technical Complexity |
|---|---|---|---|---|
| DRV-01 | Procesamiento de documentos grandes | Capacidad para procesar documentos PDF de gran tamaño. | High | High |
| DRV-02 | Escalabilidad horizontal | El sistema debe ser capaz de escalar horizontalmente para 100+ usuarios. | High | High |
| DRV-03 | Respuestas rápidas y precisas | Respuestas rápidas y precisas a preguntas en lenguaje natural. | High | High |
| DRV-04 | Integración con servicios de nube | Integración con servicios de nube (Cloud-Native). | High | High |
| DRV-05 | Usabilidad de la interfaz | Interfaz intuitiva y fácil de usar para cargar documentos y chatear. | Medium | Medium |
| DRV-06 | Seguridad y privacidad | Garantizar la seguridad y privacidad de los documentos. | High | High |
| DRV-07 | Soporte de exportación | Soporte para la exportación de resultados. | Medium | Medium |

---

#### 4.1.4. ARCHITECTURAL DESIGN DECISIONS

[cite_start]En esta sección, el equipo redacta la explicación del proceso, resumiendo los Drivers considerados, las tácticas y patrones que se evaluaron y los criterios para sus decisiones de diseño. [cite: 36]

| Decisión Arquitectónica | Racional |
|---|---|
| **Arquitectura de Microservicios** | [cite_start]Separar funcionalidades para permitir que cada servicio escale de forma independiente. [cite: 36] |
| **Uso de Serverless Computing** | [cite_start]Optimizar costos y permitir la escalabilidad automática para el procesamiento de documentos. [cite: 36] |
| **Base de Datos NoSQL** | [cite_start]Almacenar el contenido de los documentos procesados de manera eficiente. [cite: 36] |
| **API Gateway para el Frontend** | [cite_start]Centralizar la seguridad, el enrutamiento y la gestión de las solicitudes. [cite: 36] |
| **Cifrado de Datos (Data Encryption)** | [cite_start]Garantizar que los datos estén protegidos tanto en tránsito como en reposo. [cite: 36] |

---

#### 4.1.5. QUALITY ATTRIBUTE SCENARIO REFINEMENTS

[cite_start]Se inicia con un texto introductorio que resume las principales decisiones tomadas al finalizar el proceso de Quality Attribute Workshop, para colocar a continuación la versión final de los escenarios refinados en orden de prioridad. [cite: 42]

**Refinamiento de Escenario para Rendimiento**
- [cite_start]**Escenario(s):** El sistema debe ser rápido al procesar documentos grandes. [cite: 12]
- **Business Goals:** Acelerar el tiempo de procesamiento y respuesta para documentos grandes.
- [cite_start]**Relevant Quality Attributes:** Rendimiento. [cite: 12]
- [cite_start]**Stimulus:** Un usuario sube un PDF de 500 páginas. [cite: 18]
- [cite_start]**Stimulus Source:** Usuario. [cite: 17]
- [cite_start]**Components:** Subsistema de procesamiento de documentos. [cite: 19]
- [cite_start]**Environment:** Carga normal de la plataforma. [cite: 20]
- [cite_start]**Response:** El sistema procesa el documento y está listo para responder consultas. [cite: 21]
- [cite_start]**Response Measure:** El tiempo de procesamiento es menor a 2 minutos. [cite: 22]

**Refinamiento de Escenario para Escalabilidad**
- [cite_start]**Escenario(s):** La plataforma debe manejar un alto volumen de usuarios simultáneos sin degradación. [cite: 12]
- **Business Goals:** Soportar el crecimiento de la base de usuarios manteniendo el rendimiento.
- [cite_start]**Relevant Quality Attributes:** Escalabilidad. [cite: 12]
- [cite_start]**Stimulus:** 100 usuarios concurrentes suben documentos de gran tamaño. [cite: 18]
- [cite_start]**Stimulus Source:** Alto volumen de usuarios. [cite: 17]
- [cite_start]**Components:** Sistema completo. [cite: 19]
- [cite_start]**Environment:** Pico de usuarios simultáneos. [cite: 20]
- [cite_start]**Response:** El sistema mantiene su tiempo de respuesta promedio. [cite: 21]
- [cite_start]**Response Measure:** La degradación del rendimiento es imperceptible. [cite: 22]

**Refinamiento de Escenario para Confiabilidad**
- [cite_start]**Escenario(s):** El sistema debe recuperarse de fallas temporales. [cite: 12]
- **Business Goals:** Asegurar la continuidad del servicio y la integridad de los datos.
- [cite_start]**Relevant Quality Attributes:** Confiabilidad. [cite: 12]
- [cite_start]**Stimulus:** Un usuario experimenta una interrupción de conexión durante la carga. [cite: 18]
- [cite_start]**Stimulus Source:** Usuario. [cite: 17]
- [cite_start]**Components:** Subsistema de carga de documentos. [cite: 19]
- [cite_start]**Environment:** Conexión inestable. [cite: 20]
- [cite_start]**Response:** La plataforma reanuda la carga automáticamente al recuperar la conexión. [cite: 21]
- [cite_start]**Response Measure:** La pérdida de progreso es nula. [cite: 22]

**Refinamiento de Escenario para Seguridad**
- [cite_start]**Escenario(s):** Los datos de los usuarios deben estar protegidos de accesos no autorizados. [cite: 12]
- **Business Goals:** Proteger la información confidencial de los usuarios.
- [cite_start]**Relevant Quality Attributes:** Seguridad. [cite: 12]
- [cite_start]**Stimulus:** Un atacante intenta acceder a los documentos privados de un usuario. [cite: 18]
- [cite_start]**Stimulus Source:** Atacante externo. [cite: 17]
- [cite_start]**Components:** Capa de autenticación y de datos. [cite: 19]
- [cite_start]**Environment:** Operación del sistema. [cite: 20]
- [cite_start]**Response:** El sistema impide el acceso no autorizado y los datos están cifrados. [cite: 21]
- [cite_start]**Response Measure:** El acceso no autorizado es bloqueado y la información no es visible. [cite: 22]

**Refinamiento de Escenario para Usabilidad**
- [cite_start]**Escenario(s):** La interfaz de usuario debe ser fácil de usar. [cite: 12]
- **Business Goals:** Reducir la curva de aprendizaje y mejorar la experiencia del usuario.
- [cite_start]**Relevant Quality Attributes:** Usabilidad. [cite: 12]
- [cite_start]**Stimulus:** Un nuevo usuario intenta subir su primer documento. [cite: 18]
- [cite_start]**Stimulus Source:** Nuevo usuario. [cite: 17]
- [cite_start]**Components:** Interfaz de usuario. [cite: 19]
- [cite_start]**Environment:** Primer uso de la plataforma. [cite: 20]
- [cite_start]**Response:** El usuario completa el proceso sin ayuda externa. [cite: 21]
- [cite_start]**Response Measure:** El tiempo para completar la tarea es menor a 30 segundos. [cite: 22]

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
