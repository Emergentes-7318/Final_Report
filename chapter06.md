# **CAPÍTULO VI: PRODUCT DESIGN**

## 6.1. Style Guidelines

En esta sección se definen los lineamientos de estilo frontend que darán forma a la identidad visual de **DocMind**, considerando los principios de arquitectura de la información, accesibilidad y coherencia visual necesarios para su implementación en la **Landing Page** y la **Aplicación Web**.  
El objetivo es mantener una interfaz moderna, limpia y confiable que comunique profesionalismo, innovación y transparencia, valores centrales de una herramienta basada en inteligencia artificial.

### 6.1.1. General Style Guidelines

**Branding:**  
El branding de **DocMind** busca reflejar la unión entre la tecnología, el conocimiento y la confiabilidad. El logo representa una fusión entre el cerebro humano y un circuito digital, simbolizando el equilibrio entre inteligencia humana y artificial.  
La palabra **DocMind** utiliza una tipografía moderna, profesional y de bordes suaves, transmitiendo accesibilidad y precisión. Los tonos predominantes refuerzan una imagen tecnológica, ética y orientada a la productividad intelectual.  

<img src="assets/img/chapter-IV/Logo DocMind.png" style="width:300px; height:auto;" alt="logo docmind">

**Typography:**  
La tipografía seleccionada para DocMind es **Roboto**, una familia moderna, legible y versátil que comunica claridad y equilibrio. Su uso mantiene consistencia visual en todos los dispositivos, asegurando una lectura óptima en textos técnicos y narrativos.  
Poppins combina excelente legibilidad en cuerpos de texto extensos con un estilo limpio en títulos y botones, transmitiendo innovación y confianza.  

<img src="assets/Tipografia DocMind.png" style="width:700px; height:auto;" alt="tipography">

**Colors:**  
La paleta de colores de DocMind combina tonos fríos y neutros que transmiten confianza, claridad y precisión.  
El color principal, **#10BEAE**, refuerza la identidad tecnológica y moderna, mientras los tonos blancos y grises equilibran la interfaz para favorecer la lectura prolongada.  
El negro se usa en textos de alto contraste para garantizar legibilidad y jerarquía visual.  

- Primario: **#10BEAE**  
- Secundario: **#00A896**  
- Fondo general: **#FFFFFF**  
- Texto principal: **#000000**  
- Detalles y bordes: **#EAEAEA**

<img src="assets/Colors DocMind.png" style="width:700px; height:auto;" alt="colors">

---

### 6.1.2. Web, Mobile & Devices Style Guidelines

Para la interfaz web y móvil de **DocMind**, se ha diseñado un estilo visual minimalista y limpio, con prioridad en la legibilidad, la organización y la consistencia entre plataformas.  
El diseño busca reflejar una herramienta confiable, profesional y accesible, orientada a distintos tipos de profesionales (médicos, abogados, investigadores, ingenieros).

Los principios clave incluyen:

- Uso predominante de **Poppins** para mantener una lectura moderna y clara.  
- Aplicación estratégica de la paleta de colores:  
  - **#10BEAE** para botones, íconos interactivos y elementos destacados.  
  - **#FFFFFF** como fondo principal para crear amplitud visual.  
  - **#000000** para textos y elementos de contraste.  
- Espaciado generoso, alineaciones consistentes y márgenes equilibrados.  
- Íconos lineales minimalistas, representando funciones principales como “subir documento”, “resumen”, “responder” o “exportar”.  
- Adaptabilidad total a distintos tamaños de pantalla (responsive design).

#### 6.1.2.1. iOS Mobile Style Guidelines

En iOS se seguirán las pautas de **Apple Human Interface Guidelines**, personalizadas según la identidad de DocMind:

- **Tipografía:** Poppins Regular para cuerpo de texto, Poppins Medium para encabezados.  
- **Tamaño de fuente recomendado:**  
  - Título: 26 pt  
  - Subtítulo: 18 pt  
  - Cuerpo: 16 pt  
- **Colores:**  
  - Botones primarios: fondo **#10BEAE**, texto **#FFFFFF**  
  - Fondo general: **#FFFFFF**  
  - Textos: **#000000**  
- **Espaciado táctil:** mínimo de 66x66 pt por elemento interactivo.  
- **Bordes redondeados:** 6–8 pt para tarjetas, botones y modales.  
- **Navegación:** barras inferiores o pestañas jerarquizadas según secciones (Documentos, Chat, Reportes, Perfil).  

#### 6.1.2.2. Android Mobile Style Guidelines

En Android se seguirán las **Material Design Guidelines**, aplicadas al esquema visual de DocMind:

- **Tipografía:** Poppins Regular (texto) y Poppins Medium (encabezados).  
- **Tamaño de fuente recomendado:**  
  - Título: 22–26 sp  
  - Subtítulo: 16–18 sp  
  - Cuerpo: 16 sp  
- **Colores:**  
  - Botones primarios: **#10BEAE** con texto **#FFFFFF**  
  - Fondo general: **#FFFFFF**  
  - Texto: **#000000**  
- **Espaciado táctil:** mínimo 66x66 dp por elemento.  
- **Sombras suaves:** para botones flotantes (FAB) y tarjetas.  
- **Navegación:** Drawer y Bottom Navigation combinados para un acceso rápido a secciones.  
- **Animaciones:** suaves y breves al cargar resultados o transitar entre vistas.

---

## 6.2. Information Architecture

La arquitectura de información de **DocMind** se ha diseñado para que el usuario pueda acceder, analizar y exportar información de manera rápida y lógica, priorizando la claridad y la reducción de fricción cognitiva.  
El flujo principal se centra en tres acciones esenciales: **subir documento**, **consultar con IA** y **generar reporte**.

### 6.2.2. Labeling Systems

- **Sistemas de Organización Visual:**  
  Se aplicará una **organización jerárquica y secuencial**, permitiendo que el usuario avance paso a paso:  
  1. Cargar documentos o conectar con Google Drive.  
  2. Analizar el contenido mediante IA (resumen o preguntas).  
  3. Revisar resultados con citas verificables.  
  4. Exportar reportes personalizados.  

- **Esquemas de Categorización del Contenido:**  
  - Por función: *Inicio*, *Documentos*, *Análisis IA*, *Reportes*, *Perfil*.  
  - Por tipo de interacción: *Lectura*, *Consulta*, *Exportación*, *Configuración*.  
  Esto permitirá que el usuario ubique rápidamente la herramienta que necesita sin saturar la interfaz.

---

### 6.2.3. Searching Systems

En la **Landing Page**, se usarán etiquetas simples e intuitivas que guíen al visitante:

- **Home:** Presentación general de DocMind.  
- **Features:** Funciones principales (análisis, resumen, citas, reportes).  
- **Plans:** Planes y licencias disponibles.  
- **Testimonials:** Opiniones de profesionales y casos de uso.  
- **Contact:** Formulario de contacto y soporte técnico.  
- **Log In / Sign Up:** Acceso a la aplicación y registro de usuarios.

En la **Aplicación Web**, la búsqueda permitirá encontrar documentos, fragmentos o respuestas dentro del sistema de IA mediante **búsqueda semántica** (por tema o palabra clave).

---

### 6.2.4. SEO Tags and Meta Tags

Para optimizar la visibilidad de **DocMind** en buscadores web, se implementarán las siguientes etiquetas:

- **Title:** DocMind  
- **Meta Tags:**  
  - **Description:** Plataforma inteligente que genera resúmenes y reportes automáticos a partir de documentos, impulsada por IA.  
  - **Keywords:** inteligencia artificial, resúmenes automáticos, análisis documental, reportes, productividad, LLM.  
  - **Author:** DocMind AI Solutions.  

---

### 6.2.5. Navigation Systems

**Landing Page:**  
- *Home:* Introducción general y CTA hacia “Probar DocMind”.  
- *Features:* Sección informativa con capturas y ejemplos de análisis.  
- *Plans:* Comparativa de suscripciones (Free, Pro, Enterprise).  
- *Testimonials:* Casos de éxito y opiniones de profesionales.  
- *Contact:* Formulario y redes de soporte.  
- *Log In:* Botón de acción principal (CTA) que redirige a la aplicación web.

**Web Application:**  
- *Dashboard:* Vista principal con resumen de actividad reciente.  
- *My Documents:* Administración de documentos y carpetas conectadas.  
- *AI Analysis:* Chat o panel de interacción con el modelo de lenguaje.  
- *Reports:* Generación, descarga y edición de reportes personalizados.  
- *Profile & Settings:* Configuración de cuenta, idioma y preferencias.

**Mobile Application:**  
- Barra inferior con cinco íconos: *Inicio*, *Documentos*, *IA*, *Reportes*, *Perfil*.  
- Notificaciones contextuales para recordar análisis pendientes o reportes listos.  
- Transiciones fluidas entre vistas, manteniendo coherencia con el entorno web.

---


## 6.3. Landing Page UI Design

El desarrollo del UI Design de la Landing Page está en el siguiente link: https://www.figma.com/design/gNfFzd6YNyoKn9hXkA99vQ/wirefram-y-mock-up-emergentes?node-id=0-1&t=WE4kYk5VNdgK4JAm-1

### 6.3.1. Landing Page Wireframe

<img src="assets/img/chapter-IV/wireframe-landing.jpg" style="width:700px; height:auto;" alt="wireframe landing page">

### 6.3.2. Landing Page Mock-up

<img src="assets/img/chapter-IV/mockup-landing.jpg" style="width:700px; height:auto;" alt="mock up landing page">

## 6.6. Applications UX/UI Design.
### 6.6.1. Applications Wireframes.
### 6.6.2. Applications Wireflow Diagrams.
### 6.6.2. Applications Mock-ups.
### 6.6.3. Applications User Flow Diagrams.
## 6.5. Applications Prototyping.