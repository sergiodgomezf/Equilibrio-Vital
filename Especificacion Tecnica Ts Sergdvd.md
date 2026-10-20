# Especificación Técnica y Metodológica Detallada
## Sistema Web Interactivo TS_SergDVD · Seguimiento de Hábitos, Objetivos y Equilibrio Vital

**Titular y diseño contextual:** Sergio David Gómez Florián (`TS_SergDVD`)  
**Contexto territorial y temporal:** Neiba, Provincia Bahoruco, República Dominicana · Zona horaria `America/Santo_Domingo` (UTC-4) · Semana ISO (Lunes a Domingo)  
**Versión de especificación:** `v1.0` (`schemaVersion: ts_sergdvd_v1`)  
**Naturaleza del sistema:** Aplicación web progresiva de página única (*Single-Page Application* autocontenida), con motor local de evaluación cuantitativa/cualitativa transparente, almacenamiento aislado en cliente y portabilidad abierta en `JSON`/`CSV`.

## 1. Propósito, Fundamentación Ética y Enfoque Epistemológico

El sistema **TS_SergDVD · Seguimiento de Hábitos, Objetivos y Equilibrio Vital** es una herramienta digital interactiva diseñada para acompañar la planificación personal flexible, el seguimiento cotidiano de hábitos y proyectos, y la autoevaluación reflexiva de **Sergio David Gómez Florián**, trabajador social en formación, educador popular, gestor de proyectos sociales, facilitador y creador detrás de la marca **TS_SergDVD**.

A diferencia de las aplicaciones convencionales de productividad basadas en gamificación punitiva o cuantificación reduccionista, la arquitectura técnica de este sistema traduce en reglas de software cinco principios rectores:

1. **Instrumentalidad reflexiva de los indicadores:** Las métricas cuantitativas operan exclusivamente como espejos descriptivos para reconocer aprendizajes, cuidar vínculos, sostener compromisos y calibrar expectativas según el tiempo, la energía y el contexto disponibles. Nunca se calcula un "puntaje global de valor personal" ni se reducen la fe, la afectividad o la solidaridad comunitaria a calificaciones automáticas.
2. **Multipotencialidad y filomatía con continuidad:** El diseño reconoce la preferencia declarada por explorar múltiples áreas de interés (intervención comunitaria, Trabajo Social, escritura, creatividad, educación popular y uso ético de inteligencia artificial) sin tratar esa diversidad como un diagnóstico clínico. Para conciliar exploración y cierre de compromisos, incorpora límites configurables de proyectos activos, un banco de ideas desacoplado y registros de transición cognitiva (*"Dónde quedé y cuál es el próximo paso"*).
3. **Diferenciación contextual y corresponsabilidad colectiva:** El modelo de datos separa las obligaciones laborales/institucionales (programadas por defecto de lunes a viernes, protegiendo el sábado libre salvo excepción explícita) de las iniciativas formativas o creativas propias. Asimismo, en la dimensión social y comunitaria registra los aportes personales de preparación y facilitación sin atribuir individualmente resultados que pertenecen a procesos colectivos del territorio.
4. **Adaptabilidad energética no destructiva:** La variación en la energía física y emocional se atiende mediante un **Modo de Baja Energía** que conmuta las metas del día hacia *versiones mínimas previamente acordadas*, sin sobrescribir las metas originales ni alterar retrospectivamente los registros históricos.
5. **Rigor matemático y honestidad estadística:** El motor de cálculo evita distorsiones habituales en los sistemas de seguimiento: no asume automáticamente que un día sin registro equivale a un incumplimiento, no suma unidades heterogéneas (como minutos con sesiones), no penaliza descansos ni pausas justificadas, no recalcula el pasado cuando se actualiza una meta y nunca muestra un `0%` engañoso cuando no existen datos evaluados.

## 2. Arquitectura de Software y Pila Tecnológica

### 2.1. Topología de ejecución en cliente (*Client-Side Self-Contained SPA*)

La aplicación está construida como un artefacto web monolítico autocontenido (`ts_sergdvd_equilibrio_vital.html`) que se ejecuta íntegramente en el navegador del usuario sin dependencia de servidores de aplicación externos, bases de datos remotas ni telemetría de terceros:

| Capa arquitectónica | Tecnología e implementación | Función técnica |
| :--- | :--- | :--- |
| **Estructura y Semántica** | HTML5 semántico con atributos ARIA (`role="dialog"`, `role="progressbar"`, `aria-live="polite"`, `aria-pressed`) | Define la estructura accesible de las 7 vistas operativas, tablas semánticas, formularios y diálogos modales en página. |
| **Sistema de Diseño y Layout** | Tailwind CSS `v3.4.17` + CSS personalizado de alto contraste + tipografía `Inter` | Implementa diseño *mobile-first* adaptable a móvil, tableta y escritorio, superficies táctiles mínimas de `44×44 px` (`.tap-target`) y codificación visual redundante para los 6 estados de registro. |
| **Motor Lógico y Estado** | JavaScript Vanilla (`ES2022`) estructurado en módulos funcionales deterministas | Gestiona el estado reactivo en memoria (`appState`), el motor de vigencia histórica de metas, los algoritmos de evaluación semanal y rachas, y la delegación centralizada de eventos DOM. |
| **Persistencia Local Aislada** | Web Storage API (`window.localStorage`) encapsulada en `safeGetStorage` / `safeSetStorage` con bloques `try/catch` | Garantiza persistencia inmediata entre recargas de página con aislamiento estricto entre el entorno de demostración y el entorno de datos reales del usuario. |
| **Interoperabilidad de Datos** | API `Blob`, `URL.createObjectURL` y `FileReader` nativos del navegador | Permite la exportación e importación validada de respaldos completos en `.JSON` (con fusión idempotente sin duplicados) y la exportación tabular de registros en `.CSV` (UTF-8). |

### 2.2. Aislamiento de entornos de datos (Modo Demostración vs. Mis Datos Reales)

Para permitir la verificación funcional inmediata sin contaminar los registros personales de Sergio David, la capa de persistencia mantiene tres claves independientes en `localStorage`:

* `ts_sergdvd_v1_active_mode`: Almacena el puntero del entorno activo (`'demo'` o `'real'`).
* `ts_sergdvd_v1_demo_state`: Contiene el conjunto de datos de prueba precargado (6 hábitos en las 5 dimensiones, historial de dos semanas comparables `2026-10-05` y `2026-10-12`, cambios de meta con fecha de vigencia, pausas justificadas, proyectos multipotenciales, bitácora y revisión semanal). Puede restaurarse a su estado de fábrica en cualquier momento sin tocar el espacio real.
* `ts_sergdvd_v1_real_state`: Espacio personal limpio de Sergio David, inicializado con la estructura dimensional completa y acceso al catálogo de propuestas editables (desactivadas por defecto).

## 3. Modelo de Dominio, Dimensiones Vitales y Estructura de Datos

### 3.1. Arquitectura de las Dimensiones de Vida y Etiquetas Transversales

El modelo organiza la vida cotidiana en **cuatro pilares principales**, **una dimensión transversal visible** y **cuatro categorías secundarias opcionales**:

| Identificador (`id`) | Nombre de la dimensión / categoría | Rol estructural | Reglas de negocio y comportamiento en el sistema |
| :--- | :--- | :--- | :--- |
| `espiritual` | **Espiritual, trascendental y de fe** | Pilar Principal | Integra sentido de vida, oración o contemplación según preferencias personales, gratitud, silencio, reflexión, naturaleza y coherencia ética. No presupone denominaciones ni traduce la fe a puntajes. |
| `afectiva` | **Afectiva y relacional** | Pilar Principal | Incluye subcategorías conmutables (`familia`, `amistades`, `pareja`, `escucha_limites`). Permite activar o desactivar cualquier subcategoría (ej. *Pareja* desactivada por defecto) conservando intacto el historial. |
| `productiva` | **Productiva, formativa y laboral** | Pilar Principal | Separa explícitamente las obligaciones de naturaleza `institucional` (programadas Lunes a Viernes con sábado libre por defecto) de las acciones de `iniciativa_propia` (formación en Trabajo Social, escritura, marca `TS_SergDVD` y sostenibilidad económica). |
| `social` | **Social, gremial y comunitaria** | Pilar Principal | Registra acciones de naturaleza `aporte_comunitario` (educación popular, diálogo de saberes, participación gremial y acompañamiento en Neiba/Bahoruco) bajo el principio de no atribuirse individualmente logros colectivos. |
| `bienestar` | **Bienestar físico, emocional y descanso** | Dimensión Transversal Visible | Monitorea sueño, movimiento, alimentación consciente, recreación y pausas. Se muestra de forma permanente en la cabecera global del sistema y en la vista de dimensiones, con metas autodeterminadas sin prescripción médica. |
| `aprendizaje`, `creatividad`, `economia`, `disfrute` | **Categorías secundarias opcionales** | Etiquetas Transversales (`secondaryTags`) | Vinculables a cualquier hábito o proyecto para facilitar el filtrado transversal, pero **excluidas del cálculo agregativo dimensional** para evitar el doble conteo de un mismo registro en varias dimensiones. |

### 3.2. Distinción Ontológica de Entidades Operativas

El sistema distingue formalmente cinco tipos de entidades en el esquema de estado (`appState`):

1. **Hábito (`habits[]`):** Acción recurrente en el tiempo que posee propósito declarado, una única dimensión principal (`dimension`), naturaleza (`personal` | `institucional` | `iniciativa_propia` | `aporte_comunitario`), etiquetas secundarias (`secondaryTags[]`), ponderación (`weight: 1..5`), estado de ciclo de vida (`active` | `paused` | `archived`) y un arreglo histórico de versiones de meta (`goalHistory[]`).
2. **Tarea puntual (`tasks[]`):** Acción discreta y finita con fecha de vencimiento (`dueDate`), dimensión, naturaleza y estado booleano (`completed`), que se resuelve una vez y no genera cálculo de rachas.
3. **Proyecto (`projects[]`):** Conjunto articulado de acciones orientado a un resultado definido. Incluye control de cupo activo (`status: 'activo' | 'pausado' | 'cerrado' | 'abandonado'`), estado de decisión consciente (`decisionState: 'continuar' | 'posponer' | 'cerrar' | 'abandonar'`), justificación de la decisión (`decisionRationale`), memoria de transición (`whereILeftOff`) y próxima acción concreta (`nextConcreteAction`).
4. **Objetivo (`objectives[]`):** Cambio cualitativo o logro de mediano plazo al que tributan los hábitos, tareas y proyectos vinculados (`linkedHabitIds[]`, `linkedProjectIds[]`), acompañado de una apreciación cualitativa de progreso (`qualitativeProgressNote`).
5. **Idea en Banco (`ideaBank[]`):** Captura ligera de nuevos intereses o curiosidades filomáticas que protege el foco presente y puede promoverse en un clic a Proyecto cuando exista cupo activo disponible.

### 3.3. Versionado Temporal de Metas (`goalHistory`) e Inmutabilidad Retrospectiva

Para cumplir la regla de **no recalcular silenciosamente el pasado cuando se modifica una meta**, cada hábito almacena un arreglo ordenado cronológicamente `goalHistory`:

```json
{
  "effectiveFrom": "2026-10-12",
  "frequencyType": "dias_especificos",
  "scheduledDays": [1, 2, 3, 4, 5, 6, 7],
  "weeklyQuota": 7,
  "unit": "minutos",
  "targetValue": 15,
  "minVersionValue": 5,
  "completionThreshold": 80,
  "note": "Ampliación a 15 min desde el lunes 12 oct"
}
```

La función `getEffectiveGoalForDate(habit, dateStr)` selecciona determinísticamente la versión cuya fecha de vigencia cumple $\text{effectiveFrom} \le \text{dateStr}$ más cercana a la fecha evaluada. Además, cualquier cambio de meta o pausa retroactiva inserta automáticamente un registro inmutable en la bitácora de auditoría `scheduleAdjustments[]`.

## 4. Motor de Evaluación Cuantitativa Transparente

### 4.1. Semántica y Codificación de los 6 Estados de Registro Diario

Cada par $(\text{habitId}, \text{YYYY-MM-DD})$ se evalúa bajo uno de seis estados mutuamente excluyentes, representados mediante **icono + etiqueta textual + estilo de borde + color** para garantizar accesibilidad visual y cognitiva:

| Clave de estado | Representación visual y borde | ¿Es ocasión evaluada? | ¿Es estado neutral? | Comportamiento matemático en el motor |
| :--- | :--- | :--- | :--- | :--- |
| `cumplido` | `✓ Cumplido` (Borde sólido verde `#059669`, fondo `#ecfdf5`) | Sí | No | Cuenta como ocasión cumplida ($1$). Si no se especifica cantidad manual, asigna el $100\%$ de la meta de referencia vigente ese día. |
| `parcial` | `◐ Parcial` (Borde discontinuo ámbar `#d97706`, fondo `#fffbeb`) | Sí | No | Registra la cantidad o duración real ($V_{\text{real}}$). Aporta proporcionalmente al avance confirmado y solo cuenta como ocasión cumplida si alcanza el umbral configurado ($U\%$). |
| `no_realizado` | `✗ No hecho` (Borde sólido rojo `#dc2626`, fondo `#fef2f2`) | Sí | No | Registro explícito de no realización. Computa en el denominador de ocasiones evaluadas con avance $0\%$ y reinicia la racha de ocasiones. |
| `descanso` | `☕ Descanso` (Borde punteado azul `#0284c7`, fondo `#f0f9ff`) | No | Sí | Neutral: protege el descanso previsto o día libre, se descuenta del denominador de días fijos programados y conserva intacta la racha. |
| `pausado` | `⏸ Pausado` (Borde discontinuo violeta `#7c3aed`, fondo `#f5f3ff`) | No | Sí | Neutral con motivo obligatorio: documenta imprevistos (ej. lluvia en terreno o salud), reduce el denominador programado efectivo y no figura como actividad realizada ni como fallo. |
| `sin_registrar` | `○ Sin reg.` (Borde discontinuo gris `#94a3b8`, fondo `#ffffff`) | No | Pendiente | Estado por omisión. Nunca se interpreta automáticamente como `no_realizado`; incrementa el contador de registros desconocidos (`unknownCount`) y deja la racha en espera de información. |

### 4.2. Formulación Matemática por Ocasión y Separación de Excedentes

Sea $M_{\text{ref}}(h, d)$ la meta numérica de referencia del hábito $h$ en la fecha $d$:

$$M_{\text{ref}}(h, d) = \begin{cases} M_{\text{min}}(h, d) & \text{si el registro o el día activo tiene Modo de Baja Energía} \\ M_{\text{normal}}(h, d) & \text{en modo estándar} \end{cases}$$

Para cualquier registro evaluado con valor realizado $V_{\text{real}} \ge 0$:

1. **Razón bruta de realización:**
   $$r(h, d) = \frac{V_{\text{real}}}{M_{\text{ref}}(h, d)}$$
2. **Contribución normalizada con tope del 100% ($\text{progressRatioCapped}$):**
   $$p(h, d) = \min\big(1.0,\; \max(0.0,\; r(h, d))\big)$$
   Esto impide que un día con sobrecumplimiento compense artificialmente días no realizados en el porcentaje semanal.
3. **Cálculo independiente del excedente ($\text{surplusValue}$):**
   $$E(h, d) = \max\big(0,\; V_{\text{real}} - M_{\text{ref}}(h, d)\big)$$
   El excedente semanal acumulado $\sum_{d} E(h, d)$ se presenta en una etiqueta separada (ej. `+15 min excedente`).
4. **Criterio de ocasión cumplida ($\text{isCompletedOccasion}$):**
   $$\text{Cumplida}(h, d) \iff \big(\text{status} = \text{'cumplido'}\big) \;\lor\; \big(r(h, d) \times 100 \ge U(h, d)\big)$$
   donde $U(h, d) \in [10, 100]$ es el umbral porcentual de cumplimiento definido en la versión vigente del hábito.

### 4.3. Las Dos Lecturas Semanales y la Cobertura del Registro

Para cada semana $W$ (de lunes a domingo), el motor distingue entre hábitos de **días específicos** ($D_{\text{prog}} = \text{días programados} - \text{descansos/pausas}$) y hábitos de **cuota semanal** ($D_{\text{prog}} = \max(0,\; Q_{\text{sem}} - \text{pausas justificadas})$), produciendo tres indicadores con sus denominadores explícitos:

1. **Cumplimiento entre ocasiones evaluadas ($\text{complianceOverEvaluatedPct}$):**
   $$\text{Cumplimiento}_{\text{eval}} = \begin{cases} \text{round}\left(\frac{N_{\text{cumplidas}}}{N_{\text{evaluadas}}} \times 100\right) & \text{si } N_{\text{evaluadas}} > 0 \\ \text{"Sin datos suficientes"} & \text{si } N_{\text{evaluadas}} = 0 \end{cases}$$
   Excluye los registros `sin_registrar`, `descanso` y `pausado`, e informa explícitamente cuántas ocasiones permanecen sin registrar ($N_{\text{desconocidos}}$).
2. **Avance confirmado sobre lo programado ($\text{confirmedAdvanceOverPlannedPct}$):**
   $$\text{Avance}_{\text{prog}} = \begin{cases} \min\left(100,\; \text{round}\left(\frac{\sum p(h, d)}{D_{\text{prog}}} \times 100\right)\right) & \text{si } D_{\text{prog}} > 0 \\ \text{"Sin datos suficientes"} & \text{si } D_{\text{prog}} = 0 \end{cases}$$
   Refleja cuánto de la meta semanal prevista ya ha sido confirmado, integrando los avances parciales y señalando qué fracción sigue pendiente de registro.
3. **Cobertura del registro ($\text{coveragePct}$):**
   $$\text{Cobertura} = \frac{N_{\text{registradas (evaluadas + neutrales)}}}{D_{\text{cobertura}}} \times 100$$
   Indica el grado de completitud informativa de la semana antes de interpretar cualquier tendencia.

### 4.4. Agregación por Dimensión sin Suma de Unidades Heterogéneas

Dado que un pilar puede agrupar hábitos medidos en `minutos`, `sesiones` o `páginas`, el sistema **jamás suma cantidades brutas entre hábitos distintos**. En su lugar, calcula el promedio ponderado de los porcentajes normalizados de los hábitos activos cuya dimensión principal es $K$, utilizando los pesos editables $w_h \in \{1, 2, 3, 4, 5\}$:

$$\text{AvanceDimensional}(K, W) = \frac{\sum_{h \in \text{Activos}(K)} w_h \cdot \text{Avance}_{\text{prog}}(h, W)}{\sum_{h \in \text{Activos}(K)} w_h}$$

## 5. Reglas de Rachas, Descansos y Semanas Abiertas

La función `computeHabitStreaks(habit)` mantiene dos contadores independientes desde la fecha de creación del hábito hasta la fecha activa:

1. **Racha de ocasiones programadas cumplidas (`currentOccasionStreak` y `bestOccasionStreak`):**
   * Incrementa en $+1$ por cada ocasión que cumple el criterio ($\text{isCompletedOccasion} = \text{true}$).
   * Permanece invariante ante días no programados, `descanso` o `pausado`.
   * Se reinicia a $0$ únicamente ante un registro evaluado como `no_realizado` o un `parcial` inferior al umbral de cumplimiento.
   * **Continuidad pendiente ante registros sin información:** Si existen fechas programadas en estado `sin_registrar` posteriores al último cumplimiento confirmado, la racha **no se rompe ni se incrementa**; el sistema conserva el valor confirmado y adjunta la alerta `pendingOccasionCount > 0` (*"Racha pendiente de información"*).
2. **Racha de semanas con meta semanal alcanzada (`currentWeeklyStreak` y `bestWeeklyStreak`):**
   * Evalúa cada bloque Lunes-Domingo cerrado. Incrementa en $+1$ si $\sum p(h, d) \ge D_{\text{prog}}$.
   * **Protección de semanas abiertas:** Si el domingo de la semana evaluada es mayor o igual a la fecha activa ($\text{isWeekOpen} = \text{true}$), una semana que aún no ha alcanzado el $100\%$ **no se clasifica como fallida**, marcándose como `weeklyPendingInfo = true` (*"Semana en curso / abierta"*).

## 6. Subsistema de Evaluación Cualitativa y Separación Epistemológica

Para honrar la metodología de sistematización de experiencias y evaluación participativa propia del Trabajo Social:

* **Diario Reflexivo Diario (Vista 5):** Recoge cinco preguntas abiertas opcionales (*¿Qué tuvo sentido hoy?*, *¿Qué cuidé y qué necesito atender?*, *¿Qué aprendí?*, *¿Qué facilitó o dificultó mis acciones?*, *¿Qué conviene ajustar mañana?*) junto con tres escalas breves de autopercepción subjetiva no clínica (`1` a `5` con descriptores comprensibles para **Energía**, **Ánimo** y **Satisfacción**).
* **Revisión Semanal Tripartita (Vista 6):** Estructura el balance de la semana separando visual y conceptualmente tres niveles de realidad:
  1. **Columna 1 — Lo que escribí literalmente:** Citas textuales directas (`<blockquote>`) extraídas de las entradas del diario reflexivo de esa semana, sin recortes ni paráfrasis interpretativas.
  2. **Columna 2 — Los datos cuantitativos registrados:** Recuento objetivo de ocasiones cumplidas frente a evaluadas, descansos/pausas neutrales, registros desconocidos y cantidades acumuladas por hábito.
  3. **Columna 3 — Observaciones exploratorias por reglas locales:** Descriptores generados por algoritmos deterministas en el navegador (cobertura de registro, frecuencia de uso del Modo de Baja Energía y media descriptiva de energía autopercibida), advirtiendo explícitamente que **no establecen relaciones causales ni emocionales** y que **no provienen de un modelo externo de IA**.

## 7. Especificación de las 7 Vistas Operativas e Interfaz de Usuario

| Vista | Identificador DOM | Componentes interactivos y controles principales |
| :--- | :--- | :--- |
| **1. Hoy** | `#view-hoy` | Selector de capacidad disponible (horas y energía percibida `1..5`), conmutador de **Modo de Baja Energía**, lista de hasta 3 prioridades elegidas por el usuario, tarjeta de **Proyecto en foco** con modal obligatorio de transición (*"Dónde quedé y próximo paso"*), gestor de bloques flexibles (`Concentración`, `Aprendizaje`, `Creación`, `Gestión`, `Encuentro`, `Descanso`) y tarjetas de registro cotidiano en 1 toque. |
| **2. Semana** | `#view-semana` | Navegador temporal (`← Semana anterior`, `Semana actual`, `Semana siguiente →`), indicador de semana abierta/cerrada, leyenda accesible de los 6 estados, **tabla-calendario interactiva Lunes a Domingo** con edición por celda, gráfico semanal de doble barra por hábito con denominadores visibles y botón `¿Cálculo?` que abre el desglose matemático exacto. |
| **3. Dimensiones de vida** | `#view-dimensiones` | Tabla comparativa interdimensional con pesos editables (`1..5`), tarjetas de los 4 pilares y la dimensión transversal con casillas para activar/desactivar subcategorías (incluyendo *Pareja* en Afectiva), desglose *Institucional (L-V)* vs. *Iniciativa Propia* en Productiva, nota ética en Social, panel de las 4 etiquetas secundarias sin doble conteo y conmutador de resumen estadístico general opcional con advertencia de límites. |
| **4. Hábitos y proyectos** | `#view-habitos` | Seis sub-pestañas especializadas: **Hábitos** (creación, edición de meta con fecha de vigencia `effectiveFrom`, pausa con motivo, archivo y bitácora `scheduleAdjustments`), **Proyectos y Compromisos** (control de cupo activo y matriz *Continuar / Posponer / Cerrar / Abandonar con intención*), **Tareas puntuales**, **Objetivos**, **Banco de ideas** (con promoción a proyecto) y **Propuestas editables** (6 sugerencias no activadas por defecto). |
| **5. Diario reflexivo** | `#view-diario` | Recordatorio de privacidad familiar/comunitaria, selectores de las 3 escalas no clínicas de autopercepción, formulario de las 5 preguntas reflexivas y listado histórico de entradas recientes con salto directo por fecha. |
| **6. Revisión semanal** | `#view-revision` | Panel tripartito (*Lo escrito*, *Datos registrados*, *Observaciones por reglas locales + nota de transparencia sobre IA*) y formulario de síntesis semanal estructurado en *Logros*, *Aprendizajes*, *Obstáculos*, *Apoyos*, *Tensiones entre dimensiones* y *Hasta 3 ajustes elegidos*. |
| **7. Configuración y respaldo** | `#view-configuracion` | Conmutador entre **Modo Demostración** y **Mis Datos Reales**, reinicio aislado de demostración, borrado con modal de confirmación en página, configuración de excepción laboral de sábado, descarga de respaldo `.JSON`, exportación tabular `.CSV` e importador `.JSON` con validación estructural y fusión idempotente por `ID`. |

## 8. Privacidad desde el Diseño, Portabilidad y Matriz de Verificación

### 8.1. Garantías de Privacidad y Seguridad Local

* **Cero transmisión de datos personales:** La aplicación no realiza peticiones `fetch`/`XMLHttpRequest` con datos del usuario hacia ningún servidor externo ni incorpora credenciales privadas en el código fuente.
* **Protección de terceras personas en Trabajo Social:** Los formularios cualitativos incorporan avisos preventivos para evitar el registro de nombres de familiares, datos institucionales confidenciales o información identificable de personas o familias acompañadas en procesos comunitarios.
* **Transparencia sobre `localStorage`:** La interfaz informa expresamente que el almacenamiento local del navegador no está cifrado en reposo y no equivale a sincronización entre dispositivos, promoviendo el hábito de exportar respaldos periódicos en formato `.JSON`.

### 8.2. Matriz de Verificación Técnica Ejecutada

| Caso de prueba técnico | Método de verificación | Resultado verificado |
| :--- | :--- | :--- |
| **Integridad sintáctica y de enlaces/controles DOM** | Analizador estático `check_web_app.py` y validación `node --check` | `OK: no issues found` (cero controles huérfanos, cero errores de sintaxis, modales en página sin uso de `alert()`/`confirm()`). |
| **Inmutabilidad de metas históricas (`goalHistory`)** | Evaluación del hábito `hab-1` en `2026-10-08` vs. `2026-10-14` | En la semana del `2026-10-05` evalúa contra la meta original de `10 min`; desde el `2026-10-12` aplica la nueva meta de `15 min` sin alterar porcentajes pasados. |
| **Tope del 100%, parciales y excedentes separados** | Evaluación de `hab-1` (`20 min` sobre `15 min`) y `hab-2` (`25 min` sobre `45 min`) | `hab-1` limita su aporte diario al `100%` y reporta `+5 min` de excedente aparte; `hab-2` suma `0.56` de avance parcial confirmado sin inflar ocasiones cumplidas. |
| **Pausas justificadas y descansos neutrales** | Evaluación de `hab-5` en semana `2026-10-05` (pausa por lluvia en Bahoruco) | La pausa con motivo reduce el denominador efectivo de `2` a `1` y mantiene la racha intacta sin contarse como actividad realizada. |
| **Semanas sin datos y denominadores cero** | Navegación a semana futura sin registros (`2026-11-02`) | Devuelve `null` numérico y renderiza literalmente `"Sin datos suficientes"`, evitando mostrar `0%`. |
| **Rachas con continuidad pendiente** | Evaluación de `hab-1` con fecha activa `2026-10-14` en estado `sin_registrar` | Conserva la racha confirmada de `5` ocasiones y activa `pendingOccasionCount: 1` (`2026-10-14`). |
| **Importación JSON con prevención de duplicados** | Ejecución de `validateAndImportJson(backupStr, true)` sobre estado existente | Valida esquema, actualiza registros por clave `ID` y mantiene el conteo exacto de entidades (`6` hábitos antes y después de la fusión). |
