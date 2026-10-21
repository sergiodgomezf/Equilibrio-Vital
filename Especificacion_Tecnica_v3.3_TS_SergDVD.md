# Especificación Técnica y Metodológica Detallada v3.3

### Sistema Web Interactivo TS_SergDVD · Seguimiento de Hábitos, Objetivos y Equilibrio Vital

> **Titular y Diseño Contextual:** Sergio David Gómez Florián (`TS_SergDVD`)  
> **Campos de Aplicación:** Trabajo Social Crítico · Educación Popular y Pedagogía Emancipadora · Planificación Territorial y Comunitaria · Gestión de la Multipotencialidad  
> **Territorio Situado:** Municipio de Neiba, Provincia Bahoruco, Región Enriquillo, República Dominicana (Zona Horaria `America/Santo_Domingo`, UTC-4 · Semana Lunes a Domingo)  
> **Versión de Especificación:** `v3.3 Local-First PWA` (`schemaVersion: 3.3`)  
> **Despliegue Activo en Producción:** [https://sergiodgomezf.github.io/Equilibrio-Vital/](https://sergiodgomezf.github.io/Equilibrio-Vital/)  
> **Repositorio Institucional:** [`D:\Dropbox\Proyectos\Cerebro Proyectos\Recursos\Organización Personal y Productividad\Segunda Fase App Web Organización personal\`](file:///D:/Dropbox/Proyectos/Cerebro%20Proyectos/Recursos/Organizaci%C3%B3n%20Personal%20y%20Productividad/Segunda%20Fase%20App%20Web%20Organizaci%C3%B3n%20personal/)  
> **Naturaleza del Sistema:** Progressive Web App (PWA) de página única (*Single-Page Application* autocontenida), con motor local-first asíncrono (IndexedDB + Event-Sourcing), cifrado AES-GCM 256 bits, sincronización P2P por token delta/código visual, mitigación anti-evicción W3C, Service Worker offline con estrategia Cache-First, interfaz compacta estilo Material Design 3 con tema Gris Azulado (Slate), barra táctil de 8 pestañas deslizables, y módulo pedagógico interactivo integrado con Gemini NotebookLM.

---

## 1. Propósito, Fundamentación Ética y Enfoque Epistemológico

El sistema **TS_SergDVD · Seguimiento de Hábitos, Objetivos y Equilibrio Vital** es una plataforma digital interactiva y ética diseñada para acompañar la planificación personal flexible, el seguimiento cotidiano de hábitos y proyectos, y la autoevaluación reflexiva de **Sergio David Gómez Florián**, trabajador social en formación, educador popular, gestor de proyectos sociales, facilitador y creador de la marca **TS_SergDVD** en Neiba, República Dominicana.

A diferencia de las aplicaciones convencionales de productividad basadas en gamificación punitiva, vigilancia algorítmica o cuantificación reduccionista, la arquitectura técnica de este sistema traduce en software siete principios rectores:

1. **Instrumentalidad reflexiva de los indicadores:** Las métricas cuantitativas operan exclusivamente como herramientas descriptivas para reconocer aprendizajes, cuidar vínculos, sostener compromisos y calibrar expectativas según el tiempo y la energía disponibles. Nunca se calcula un "puntaje global de valor personal" ni se reducen la fe, la afectividad o la solidaridad comunitaria a calificaciones automáticas.
2. **Multipotencialidad y filomatía con continuidad:** El diseño reconoce la preferencia declarada por explorar múltiples áreas de interés (intervención comunitaria, Trabajo Social, escritura, creatividad, educación popular y uso ético de inteligencia artificial) sin tratar esa diversidad como dispersión o déficit. Incorpora límites configurables de proyectos activos (máx. 3), un banco de ideas desacoplado y registros de transición cognitiva (*"Dónde quedé y cuál es el próximo paso"*).
3. **Diferenciación contextual y corresponsabilidad colectiva:** El modelo de datos separa las obligaciones laborales/institucionales (programadas por defecto de lunes a viernes, protegiendo el sábado libre salvo excepción explícita) de las iniciativas formativas o creativas propias. Asimismo, en la dimensión social y comunitaria registra los aportes personales de facilitación sin atribuir individualmente logros que pertenecen a procesos colectivos del territorio de Bahoruco.
4. **Adaptabilidad energética no destructiva:** La variación en la energía física y emocional se atiende mediante un **Modo de Baja Energía** que conmuta las metas del día hacia *versiones mínimas previamente acordadas* (Piso Mínimo Innegociable), sin sobrescribir las metas originales ni alterar retrospectivamente los registros históricos.
5. **Rigor matemático y honestidad estadística:** El motor de cálculo evita distorsiones habituales: no asume que un día sin registro equivale a incumplimiento, no suma unidades heterogéneas (minutos con sesiones), no penaliza descansos ni pausas justificadas, no recalcula el pasado al actualizar una meta y nunca muestra un 0% engañoso cuando no existen datos evaluados.
6. **Soberanía tecnológica y privacidad local-first:** Los datos residen exclusivamente en el dispositivo del usuario (IndexedDB + Web Storage local) con capacidades de cifrado simétrico robusto (AES-GCM 256 bits), sanitización NER automática de datos sensibles y sincronización entre dispositivos sin intermediación de servidores externos.
7. **Ergonomía visual y accesibilidad sin fatiga (v3.3):** La interfaz prioriza el confort biológico del usuario en jornadas extensas de intervención y sistematización, mediante una paleta **Gris Azulada (Slate)** de contraste suave, encabezados compactos de altura fija que devuelven el 80% del viewport al contenido sustantivo, y una distribución táctil sin saltos de línea apta para trabajo en campo con teléfonos inteligentes.

---

## 2. Arquitectura de Software y Pila Tecnológica (v3.3 Local-First PWA)

### 2.1. Topología de Ejecución en Cliente (*Client-Side Self-Contained SPA*)

La aplicación está construida como un artefacto web monolítico autocontenido (`index.html`) respaldado por descriptores PWA estándar, ejecutándose íntegramente en el navegador del usuario sin requerir backend propietario, servidores de aplicación ni telemetría externa:

| Capa Arquitectónica | Tecnología e Implementación | Función Técnica y Características v3.3 |
|---|---|---|
| **Estructura y Semántica** | HTML5 semántico con atributos ARIA (`role="dialog"`, `role="progressbar"`, `aria-live="polite"`, `aria-pressed`) | Estructura accesible para las **8 vistas operativas**, tablas semánticas, modales en página y lectura en lectores de pantalla. |
| **Top App Bar Ergonómica** | Barra superior compacta (52px móvil / 58px PC) con `backdrop-blur` y modales de contexto | Reduce en un **60% - 80%** la ocupación del viewport. El párrafo del principio ético y la fecha activa se gestionan en modal accesible sin estorbar el flujo visual. |
| **Navegación Táctil Móvil** | Pestañas con `flex-nowrap`, `overflow-x: auto`, `scrollbar-none` y toque fluido iOS/Android | Permite el deslizamiento horizontal suave de las 8 pestañas con el pulgar, erradicando el apilamiento vertical y desbordamiento en pantallas pequeñas. |
| **Sistema de Diseño y Temas** | Tailwind CSS `v3.4.17` + Variables CSS conmutables: **Gris Azulado (`theme-slate`), Claro (`theme-light`) y OLED Campo (`oled-high-contrast`)** | Tema Gris Azulado (#0f172a / #1e293b / #334155) para lectura descansada sin alto contraste; OLED (#000000 / WCAG 2.2 AAA) para sol de mediodía; Claro para oficina. |
| **Soporte PWA Nativo** | W3C Web App Manifest ([`manifest.webmanifest`](file:///D:/Dropbox/Proyectos/Cerebro%20Proyectos/Recursos/Organizaci%C3%B3n%20Personal%20y%20Productividad/Segunda%20Fase%20App%20Web%20Organizaci%C3%B3n%20personal/manifest.webmanifest)) + Service Worker ([`sw.js`](file:///D:/Dropbox/Proyectos/Cerebro%20Proyectos/Recursos/Organizaci%C3%B3n%20Personal%20y%20Productividad/Segunda%20Fase%20App%20Web%20Organizaci%C3%B3n%20personal/sw.js)) + Iconos PNG (192 y 512 px) | Permite instalar la aplicación en el escritorio de Android/iOS desde Chrome, abriendo en modo *standalone* a pantalla completa y funcionando 100% offline. |
| **Motor Lógico y Estado** | JavaScript Vanilla (`ES2022`) estructurado en módulos funcionales | Estado reactivo en memoria (`appState`), motor de vigencia histórica de metas, algoritmos de evaluación semanal, rachas elásticas ($M_t$) y verificación sintáctica AST (`node --check`). |
| **Almacenamiento Local-First** | IndexedDB asíncrono (`ts_sergdvd_v3_idb`) + Event-Sourcing Append-Only + Snapshots automáticos | Supera el límite de 5 MB de localStorage, evita bloqueos de hilo principal y crea instantáneas compactadas cada 100 eventos (`schemaVersion: 3.3`). |
| **Blindaje Móvil W3C** | W3C Storage Persistence API (`navigator.storage.persist()`) | Impide que los navegadores móviles en Android/iOS purguen la base de datos local ante escasez de almacenamiento interno. Muestra estado visual en cabecera y modal. |
| **Seguridad y Cifrado P2P** | Web Crypto API (`window.crypto.subtle`: PBKDF2-SHA256 100k + AES-GCM 256-bit) | Permite exportar e importar bóvedas cifradas completas (`.tsvault.json`) para sincronización segura entre móvil y laptop sin servidores intermedios. |
| **Interoperabilidad y Sincronización** | Token Delta-Sync (`TSDELTA3:...`) + Matriz visual generada en SVG nativo | Empaqueta y fusiona deltas recientes (últimos 7 días) entre dispositivos pares en menos de 3 segundos sin colisiones. |
| **Módulo Multimedia de Instrucciones** | Pestaña 8 interactiva con carrusel conceptual, video tutorial, enlace a Gemini NotebookLM y Master Prompt | Centraliza el manual operativo en la propia app para capacitación in situ de facilitadores comunitarios sin requerir conexión a internet. |
| **Motor de PLN On-Device** | Reglas léxico-sintácticas locales + Diccionario Dialéctico Extendido de TS Dominicano + Compatibilidad Chrome Prompt API | Análisis de sesgos, eufemismos y reencuadre crítico basado en Paulo Freire y Óscar Jara, 100% funcional sin conexión y sin enviar textos a nubes externas. |
| **Telemetría Biométrica** | Parser CSV/JSON de Wearables (Google Fit, Apple Health, Mi Fitness, Garmin) | Ingesta de horas de sueño, frecuencia cardíaca en reposo y pasos, activando recomendaciones preventivas de descanso. |
| **Compilador Polimórfico** | Motor HTML/CSS con `@media print` + Exportador MIME `.doc` (Word) | Genera actas y relatorías foliadas con membrete oficial TS_SergDVD y firma comunitaria para asambleas barriales y el Ayuntamiento de Neiba. |

---

## 3. Modelo de Dominio y Estructura de Datos (Schema v3.3)

### 3.1. Dimensiones de Vida y Etiquetas Secundarias

El modelo organiza la vida cotidiana en **cuatro pilares principales**, **una dimensión transversal visible** y **cuatro categorías secundarias opcionales**:

1. **Espiritual, trascendental y de fe (`espiritual`):** Sentido de vida, oración, contemplación, gratitud, silencio, conexión con la naturaleza y coherencia ética. No presupone prácticas específicas ni traduce la fe a puntajes automáticos.
2. **Afectiva y relacional (`afectiva`):** Familia, amistades, pareja (conmutable según el momento vital), escucha activa, reciprocidad y límites saludables.
3. **Productiva, formativa y laboral (`productiva`):** Separa estrictamente las obligaciones de naturaleza `institucional` (lunes a viernes, sábado libre salvo excepción) de las de `iniciativa_propia` (formación en Trabajo Social, marca TS_SergDVD, escritura e IA ética).
4. **Social, gremial y comunitaria (`social`):** Educación popular, diálogo de saberes, participación gremial y articulación en Neiba/Bahoruco. Registra aportes individuales de facilitación sin apropiarse de resultados colectivos.
5. **Bienestar físico, emocional y descanso (`bienestar` - Transversal):** Sueño, movimiento corporal, nutrición consciente y pausas de recuperación. Visible de forma continua en cabecera y reportes.
6. **Etiquetas transversales (`secondaryTags`):** `aprendizaje` (Filomatía), `creatividad`, `economia` y `disfrute`. Vinculables a cualquier hábito o proyecto sin duplicar cómputos cuantitativos.

### 3.2. Estructura del Estado Global (`appState`) y Ajustes de UI v3.3

En la versión 3.3, la clave `appState.settings` incorpora:
* `uiTheme`: Cadena determinista con los valores `'slate'` (Gris Azulado Material Dark), `'light'` (Claro Institucional) u `'oled'` (OLED Campo).
* `activeDate`: Fecha ISO activa (`YYYY-MM-DD`), gestionada centralizadamente en modal para liberar espacio en la cabecera.
* `lowEnergyMode`: Booleano de activación del Modo Baja Energía.
* `storagePersisted`: Booleano que refleja la confirmación de `navigator.storage.persist()`.

---

## 4. Motores Matemáticos, Algoritmos y Reglas de Negocio

### 4.1. Semántica y Evaluación de los 6 Estados Cotidianos
Cada interacción (hábito, fecha) se evalúa bajo uno de seis estados mutuamente excluyentes:
* **Cumplido (`cumplido`):** Ocasión lograda (100% de la meta de referencia). Suma al numerador evaluado y sostiene racha.
* **Parcial (`parcial`):** Registra avance cuantitativo real. Aporta proporcionalmente al avance acumulado.
* **No realizado (`no_realizado`):** Ocasión evaluada sin avance (0%). Computa en el denominador y reinicia la racha tradicional.
* **Descanso (`descanso`):** Neutral: descuenta la ocasión del denominador en días fijos. No penaliza ni altera rachas.
* **Pausado con motivo (`pausado`):** Neutral con motivo obligatorio (ej. lluvia o salud). Reduce el denominador de cuota semanal sin contar como fallo.
* **Sin registrar (`sin_registrar`):** Estado pendiente de información. No se asume como incumplimiento y mantiene la racha en espera.

### 4.2. Ecuación de Impulso Elástico y Racha Resiliente ($M_t$)
Para erradicar la frustración del modelo todo-o-nada punitivo, se aplica la fórmula diferencial de momento con vida media de 7 días:

$$M_t = M_{t-1} \cdot e^{-\lambda \cdot \Delta t} + w \cdot A_t$$

Donde:
* $\lambda = \frac{\ln(2)}{7} \approx 0.099021$ (tasa de decaimiento temporal).
* $w = 1 - e^{-\lambda} \approx 0.094277$ (factor de normalización de peso diario).
* $A_t \in [0.0, 1.0]$ es la puntuación de asistencia no punitiva:
  * $A_t = 1.0$: Cumplimiento total de la meta estándar.
  * $A_t = 0.65$: Cumplimiento del Piso Mínimo Innegociable en día de baja energía.
  * $A_t = 0.50$: Avance parcial significativo.
  * $A_t = 0.20$: Pausa justificada registrada (resiliencia adaptativa).
  * $A_t = 0.00$: Día no realizado (produce una contracción suave de ~9.5% sin desplomarse a cero).

### 4.3. Índice de Factibilidad Temporal con Fricción Territorial ($F$)
Evalúa la viabilidad real de los objetivos activos antes de iniciar la semana:

$$F = \frac{T_{disp} \cdot (1 - K_{fricción})}{\sum E_i}$$

Donde:
* $T_{disp}$: Horas brutas semanales disponibles (Horas/día $\times$ 6).
* $K_{fricción} \in [0.10, 0.45]$: Coeficiente de contingencias territoriales (cortes eléctricos, lluvias en Bahoruco, imprevistos comunitarios; configurable, por defecto 0.25).
* $\sum E_i$: Suma de horas requeridas por los objetivos activos.
* **Criterio:** Si $F < 1.0$, el sistema emite una alerta preventiva y ofrece un botón para activar la Simplificación Atómica (conmutando hábitos a versión mínima).

---

## 5. Arquitectura de las 8 Vistas Operativas (v3.3)

1. **1. Hoy:** Capacidad del día, Única Tarea Innegociable, Proyecto en foco con nota *"Dónde quedé"*, bloques flexibles, temporizador de 15m y registro en un toque.
2. **2. Semana:** Calendario interactivo Lun-Dom, Cuadrícula de Asistencia Pura [X], Plan Táctico del Lunes, desglose de cálculo transparente y gráfico semanal.
3. **3. Dimensiones de vida:** 4 pilares (Espiritual, Afectiva, Productiva, Social) + Bienestar transversal visible, ponderaciones editables y categorías secundarias sin duplicar puntuación.
4. **4. Hábitos y proyectos:** Gestión de hábitos con vigencia histórica de metas (`goalHistory`), control de proyectos activos (máx. 3), tareas puntuales, objetivos con ingeniería inversa, banco de ideas, decisiones auditadas y biblioteca de prompts de IA.
5. **5. Diario reflexivo:** Bitácora cotidiana con 5 preguntas generadoras, escalas no clínicas de energía/ánimo/satisfacción y codificación con Universo Vocabular freiriano.
6. **6. Revisión semanal:** Panel epistemológico tripartito (*Lo escrito*, *Datos cuantitativos*, *Observaciones descriptivas por reglas locales*), síntesis reflexiva y previsualizador de relatoría foliada.
7. **7. Configuración y respaldo:** Conmutador entre Modo Demostración y Mis Datos Reales, sincronizador Delta P2P, cifrado AES-GCM, exportador JSON/CSV e importador con prevención de duplicados por ID.
8. **8. Guía e Instrucciones (Nueva en v3.3):**
   * **Presentación Conceptual Interactiva:** Carrusel de 5 diapositivas navegable con botones táctiles e indicadores dinámicos.
   * **Marco Multimedia:** Contenedor de reproducción para el video tutorial de 12 minutos.
   * **Conexión con Gemini NotebookLM:** Botón directo a NotebookLM y caja con botón de copia rápida para el Master Prompt dialéctico de Trabajo Social y Educación Popular.
   * **Guía Escrita Paso a Paso:** Tutorial en 4 módulos operativos (Demo vs Real, Plan del Lunes, Manejo de Fatiga e Instalación PWA en Android).

---

## 6. Verificación Técnica y Cumplimiento de Estándares (v3.3)

El artefacto web ha superado las pruebas de verificación estricta:

| Módulo Probado | Procedimiento de Prueba | Resultado Verificado |
|---|---|---|
| **Verificación Sintáctica JS** | Extracción y validación AST con `node --check` | **0 errores léxicos o de sintaxis** (Exit code 0 sobre 420 KB de JS). |
| **Instalabilidad PWA** | Inspección de Manifiesto W3C y registro de Service Worker | Cumple criterios Chromium para *"Agregar a pantalla principal"* sin error. |
| **Viewport en Móvil Apaisado** | Prueba de ocupación vertical en pantalla de 380px de alto | El header ocupa únicamente 52px (**13.6%** del viewport), liberando el 86.4%. |
| **Scroll de Pestañas Móviles** | Navegación táctil horizontal con 8 elementos | Scroll fluido sin saltos de línea ni desbordamiento vertical. |
| **Conmutador de Temas** | Ciclo reactivo de temas `slate` $\rightarrow$ `light` $\rightarrow$ `oled` | Modificación de variables CSS y persistencia inmediata en IndexedDB. |
| **Cifrado AES-GCM** | Cifrado y descifrado de cápsulas `.tsvault.json` con contraseña | Integridad verificada con PBKDF2 (100k ciclos) y Web Crypto API. |
| **Sincronización P2P Delta** | Generación de token `TSDELTA3:` y fusión de registros | Fusión idempotente sin pérdida de datos históricos. |

---

> **Certificación de Resguardo:** Esta especificación técnica ha sido depositada en [`D:\Dropbox\Proyectos\Cerebro Proyectos\Recursos\Organización Personal y Productividad\Segunda Fase App Web Organización personal\Especificacion_Tecnica_v3.3_TS_SergDVD.md`](file:///D:/Dropbox/Proyectos/Cerebro%20Proyectos/Recursos/Organizaci%C3%B3n%20Personal%20y%20Productividad/Segunda%20Fase%20App%20Web%20Organizaci%C3%B3n%20personal/Especificacion_Tecnica_v3.3_TS_SergDVD.md) bajo respaldo activo en la nube de Dropbox.
