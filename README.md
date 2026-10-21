# TS_SergDVD · Equilibrio Vital (README v3.3)

### Sistema Web Interactivo Local-First & PWA para Planificación Flexible, Cuidado Integral y Trabajo Social Crítico

> **Titular y Diseñador:** Sergio David Gómez Florián (`TS_SergDVD`)  
> **Ubicación Territorial:** Neiba, Provincia Bahoruco, República Dominicana  
> **Versión Actual:** `v3.3 Local-First PWA` | **Licencia:** MIT / Abierta para la Comunidad  

[![GitHub Pages](https://img.shields.io/badge/Deploy-GitHub_Pages-teal?logo=github)](https://sergiodgomezf.github.io/Equilibrio-Vital/)
[![Architecture](https://img.shields.io/badge/Architecture-Local--First_PWA-blue)](#-arquitectura-t%C3%A9cnica)
[![PWA Ready](https://img.shields.io/badge/PWA-Installable_on_Android-emerald?logo=android)](#-instalaci%C3%B3n-como-aplicaci%C3%B3n-en-android-pwa)
[![Privacy](https://img.shields.io/badge/Privacy-Zero_Tracking_|_AES--GCM_256-emerald)](#-soberan%C3%ADa-de-datos-y-privacidad)
[![UI Design](https://img.shields.io/badge/UI-Material_Design_3_(Slate)-slate)](#-ergonom%C3%ADa-visual-y-temas)
[![Accessibility](https://img.shields.io/badge/Accessibility-WCAG_2.2_AAA_(OLED)-black)](#-ergonom%C3%ADa-visual-y-temas)

---

## 🌐 Aplicación en Producción

Puedes utilizar la aplicación directamente desde cualquier dispositivo (computadora, tableta o teléfono móvil) sin necesidad de instalar nada o instalándola como una app nativa:

🔗 **[https://sergiodgomezf.github.io/Equilibrio-Vital/](https://sergiodgomezf.github.io/Equilibrio-Vital/)**

---

## 🧭 ¿Qué es TS_SergDVD Equilibrio Vital?

**TS_SergDVD Equilibrio Vital** es una plataforma de software ético creada a la medida de la práctica profesional de **Sergio David Gómez Florián**, combinando el rigor del **Trabajo Social**, la **Educación Popular** (Paulo Freire), la **Sistematización de Experiencias** (Óscar Jara), la **Multipotencialidad/Filomatía** y el uso crítico de la **Inteligencia Artificial**.

A diferencia de las aplicaciones comerciales de hábitos centradas en la productividad tóxica, el castigo por rachas rotas o la venta de datos personales, este sistema funciona como un **espejo reflexivo no punitivo** que respeta el ritmo humano, la reserva energética y las realidades del contexto comunitario en el suroeste dominicano.

---

## ⚡ Novedades Principales de la Versión 3.3

* **📱 Progressive Web App (PWA) Nativa e Instalable en Android:** Gracias a la incorporación de [`manifest.webmanifest`](file:///D:/Dropbox/Proyectos/Cerebro%20Proyectos/Recursos/Organizaci%C3%B3n%20Personal%20y%20Productividad/Segunda%20Fase%20App%20Web%20Organizaci%C3%B3n%20personal/manifest.webmanifest), el Service Worker [`sw.js`](file:///D:/Dropbox/Proyectos/Cerebro%20Proyectos/Recursos/Organizaci%C3%B3n%20Personal%20y%20Productividad/Segunda%20Fase%20App%20Web%20Organizaci%C3%B3n%20personal/sw.js) y los iconos oficiales de $192 \times 192$ y $512 \times 512$ px, la app ahora puede instalarse directamente en el escritorio de Android desde Chrome sin el error *"No se puede instalar esta app"*. Funciona en modo independiente (*standalone*) a pantalla completa y 100% desconectada.
* **🌙 Tema Oscuro sin Alto Contraste (Material Design 3 - Gris Azulado / Slate):** Incorporada la paleta descansada `theme-slate` (`#0f172a` base, `#1e293b` tarjetas, `#334155` bordes y `#f1f5f9` texto principal). Selector cíclico en cabecera con un solo clic: **Gris Azulado $\leftrightarrow$ Claro Institucional $\leftrightarrow$ OLED Campo**.
* **📐 Top App Bar Ultra-Compacta (52px / 58px):** Se rediseñó radicalmente el encabezado para recuperar entre el 60% y el 80% del área útil vertical. El párrafo ético permanente, el titular de Neiba y el selector de fecha pasaron al modal accesible `ℹ️ Contexto & Ética`.
* **👆 Navegación Táctil Móvil Deslizable:** Contenedor de pestañas con desplazamiento horizontal suave (`overflow-x: auto; flex-nowrap; scrollbar-none`), eliminando el apilamiento vertical que rompía la vista en teléfonos.
* **📖 Pestaña 8: Guía Interactiva, Video y Cuaderno Gemini NotebookLM:** Módulo de aprendizaje integrado con carrusel conceptual de 5 láminas, marco para video explicativo, enlace a Gemini NotebookLM con Master Prompt de acompañamiento dialéctico copiable en un toque, y tutorial operativo en 4 módulos.

---

## 🗂️ Estructura de las 8 Vistas de la Aplicación

1. **1. Hoy:** Capacidad del día, Única Tarea Innegociable, Proyecto en foco con nota *"Dónde quedé"*, bloques flexibles, temporizador de 15m y registro en un toque.
2. **2. Semana:** Calendario interactivo Lun-Dom, Cuadrícula de Asistencia Pura [X], Plan Táctico del Lunes, desglose de cálculo transparente y gráfico semanal.
3. **3. Dimensiones de vida:** 4 pilares (Espiritual, Afectiva, Productiva, Social) + Bienestar transversal visible, ponderaciones editables y categorías secundarias sin duplicar puntuación.
4. **4. Hábitos y proyectos:** Gestión de hábitos con vigencia histórica de metas (`goalHistory`), control de proyectos activos (máx. 3), tareas puntuales, objetivos con ingeniería inversa, banco de ideas, decisiones auditadas y biblioteca de prompts de IA.
5. **5. Diario reflexivo:** Bitácora cotidiana con 5 preguntas generadoras, escalas no clínicas de energía/ánimo/satisfacción y codificación con Universo Vocabular freiriano.
6. **6. Revisión semanal:** Panel epistemológico tripartito (*Lo escrito*, *Datos cuantitativos*, *Observaciones descriptivas por reglas locales*), síntesis reflexiva y previsualizador de relatoría foliada.
7. **7. Configuración y respaldo:** Conmutador entre Modo Demostración y Mis Datos Reales, sincronizador Delta P2P, cifrado AES-GCM, exportador JSON/CSV e importador con prevención de duplicados por ID.
8. **8. Guía e Instrucciones (Nueva en v3.3):** Presentación conceptual en carrusel de 5 diapositivas, marco para video tutorial, Master Prompt para Gemini Notebook y guía paso a paso de uso cotidiano.

---

## 📲 Instalación como Aplicación en Android (PWA)

1. Abre [https://sergiodgomezf.github.io/Equilibrio-Vital/](https://sergiodgomezf.github.io/Equilibrio-Vital/) en Google Chrome en tu teléfono Android.
2. Toca el menú de tres puntos verticales (`⋮`) en la esquina superior derecha del navegador.
3. Selecciona **«Instalar aplicación»** o **«Agregar a la pantalla principal»**.
4. Pulsa **«Instalar»** en el diálogo de confirmación.
5. ¡Listo! El icono de **TS_SergDVD** aparecerá en la pantalla de inicio de tu celular, abriendo instantáneamente a pantalla completa y funcionando de forma autónoma sin necesidad de conexión a internet.

---

## 🛠️ Instalación y Uso Local en Computadora

La aplicación es un artefacto web estático autocontenido que no requiere Node.js, compiladores ni servidores backend:

```bash
# 1. Clonar el repositorio
git clone https://github.com/sergiodgomezf/Equilibrio-Vital.git

# 2. Entrar a la carpeta
cd Equilibrio-Vital

# 3. Abrir directamente en el navegador predeterminado
# En Windows:
start index.html

# En macOS:
open index.html

# En Linux:
xdg-open index.html
```

---

## 📄 Documentación Técnica Completa

* [**Especificación Técnica y Metodológica Detallada v3.3**](file:///D:/Dropbox/Proyectos/Cerebro%20Proyectos/Recursos/Organizaci%C3%B3n%20Personal%20y%20Productividad/Segunda%20Fase%20App%20Web%20Organizaci%C3%B3n%20personal/Especificacion_Tecnica_v3.3_TS_SergDVD.md)
* [**Informe Técnico Ejecutivo de Optimización UI y PWA v3.3**](file:///D:/Dropbox/Proyectos/Cerebro%20Proyectos/Recursos/Organizaci%C3%B3n%20Personal%20y%20Productividad/Segunda%20Fase%20App%20Web%20Organizaci%C3%B3n%20personal/Informe_Tecnico_Ejecutivo_Optimizacion_UI_PWA_TS_SergDVD_v3.3.md)
* [**Memoria del Pipeline MarkItDown v2.7**](file:///D:/Dropbox/Proyectos/MarkitDown/Informe_Tecnologico_Pipeline_Optimizacion_UI_PWA_TS_SergDVD_20oct2026.md)

---

## 🤝 Créditos y Reconocimientos

* **Concepción, Marco Teórico y Diseño Contextual:** Lic. Sergio David Gómez Florián (`TS_SergDVD`), Neiba, República Dominicana.
* **Inspiración Metodológica:** Paulo Freire (Pedagogía del Oprimido), Óscar Jara Holliday (Sistematización de Experiencias), principios de autogestión territorial y ética del cuidado.
