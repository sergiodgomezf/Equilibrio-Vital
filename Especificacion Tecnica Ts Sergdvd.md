Especificación Técnica y Metodológica v3.2
Sistema Web Interactivo TS_SergDVD · Seguimiento de Hábitos, Objetivos y Equilibrio Vital
Especificación Técnica y Metodológica Detallada
Sistema Web Interactivo TS_SergDVD · Seguimiento de Hábitos, Objetivos y Equilibrio Vital
Titular y diseño contextual: Sergio David Gómez Florián (`TS_SergDVD`)
Contexto territorial y temporal: Neiba, Provincia Bahoruco, República Dominicana · Zona horaria `America/Santo_Domingo` (UTC-4) · Semana ISO (Lunes a Domingo)
Versión de especificación: `v3.2 Local-First` (`schemaVersion: 3`)
Despliegue activo en producción: [https://sergiodgomezf.github.io/Equilibrio-Vital/](https://sergiodgomezf.github.io/Equilibrio-Vital/)
Naturaleza del sistema: Aplicación web progresiva de página única (*Single-Page Application* autocontenida), con motor local-first asíncrono (IndexedDB + Event-Sourcing), cifrado AES-GCM 256 bits, sincronización P2P por token delta/código visual, mitigación anti-evicción W3C, motor de PLN On-Device con Diccionario Dialéctico de Trabajo Social Dominicano, telemetría de wearables y compilador polimórfico a relatorías oficiales foliadas.
——————————————————————————————
1. Propósito, Fundamentación Ética y Enfoque Epistemológico
El sistema TS_SergDVD · Seguimiento de Hábitos, Objetivos y Equilibrio Vital es una plataforma digital interactiva y ética diseñada para acompañar la planificación personal flexible, el seguimiento cotidiano de hábitos y proyectos, y la autoevaluación reflexiva de Sergio David Gómez Florián, trabajador social en formación, educador popular, gestor de proyectos sociales, facilitador y creador de la marca TS_SergDVD en Neiba, República Dominicana.
A diferencia de las aplicaciones convencionales de productividad basadas en gamificación punitiva, vigilancia algorítmica o cuantificación reduccionista, la arquitectura técnica de este sistema traduce en software seis principios rectores:
1. Instrumentalidad reflexiva de los indicadores: Las métricas cuantitativas operan exclusivamente como herramientas descriptivas para reconocer aprendizajes, cuidar vínculos, sostener compromisos y calibrar expectativas según el tiempo y la energía disponibles. Nunca se calcula un "puntaje global de valor personal" ni se reducen la fe, la afectividad o la solidaridad comunitaria a calificaciones automáticas.
2. Multipotencialidad y filomatía con continuidad: El diseño reconoce la preferencia declarada por explorar múltiples áreas de interés (intervención comunitaria, Trabajo Social, escritura, creatividad, educación popular y uso ético de inteligencia artificial) sin tratar esa diversidad como dispersión o déficit. Incorpora límites configurables de proyectos activos, un banco de ideas desacoplado y registros de transición cognitiva (*"Dónde quedé y cuál es el próximo paso"*).
3. Diferenciación contextual y corresponsabilidad colectiva: El modelo de datos separa las obligaciones laborales/institucionales (programadas por defecto de lunes a viernes, protegiendo el sábado libre salvo excepción explícita) de las iniciativas formativas o creativas propias. Asimismo, en la dimensión social y comunitaria registra los aportes personales de facilitación sin atribuir individualmente logros que pertenecen a procesos colectivos del territorio de Bahoruco.
4. Adaptabilidad energética no destructiva: La variación en la energía física y emocional se atiende mediante un Modo de Baja Energía que conmuta las metas del día hacia *versiones mínimas previamente acordadas* (Piso Mínimo Innegociable), sin sobrescribir las metas originales ni alterar retrospectivamente los registros históricos.
5. Rigor matemático y honestidad estadística: El motor de cálculo evita distorsiones habituales: no asume que un día sin registro equivale a incumplimiento, no suma unidades heterogéneas (minutos con sesiones), no penaliza descansos ni pausas justificadas, no recalcula el pasado al actualizar una meta y nunca muestra un 0% engañoso cuando no existen datos evaluados.
6. Soberanía tecnológica y privacidad local-first: Los datos residen exclusivamente en el dispositivo del usuario (IndexedDB + Web Storage local) con capacidades de cifrado simétrico robusto (AES-GCM 256 bits), sanitización NER automática de datos sensibles y sincronización entre dispositivos sin intermediación de servidores externos.
——————————————————————————————
2. Arquitectura de Software y Pila Tecnológica (v3.2 Local-First)
2.1. Topología de ejecución en cliente (*Client-Side Self-Contained SPA*)
La aplicación está construida como un artefacto web monolítico autocontenido (`ts_sergdvd_equilibrio_vital.html`) que se ejecuta íntegramente en el navegador del usuario sin requerir backend propietario, servidores de aplicación ni telemetría externa:
Capa arquitectónica	Tecnología e implementación	Función técnica y características v3.2
**Estructura y Semántica**	HTML5 semántico con atributos ARIA (`role="dialog"`, `role="progressbar"`, `aria-live="polite"`, `aria-pressed`)	Estructura accesible para las 7 vistas operativas, tablas semánticas, modales en página y lectura en lectores de pantalla.
**Sistema de Diseño y Layout**	Tailwind CSS `v3.4.17` + CSS OLED High Contrast (#000000 / WCAG 2.2 AAA) + tipografía `Inter`	Diseño adaptable (*mobile-first*), superficies táctiles mínimas de 44×44 px (`.tap-target`), modo OLED para visibilidad bajo sol directo en campo y reglas `@media print` para relatorías oficiales.
**Motor Lógico y Estado**	JavaScript Vanilla (`ES2022`) estructurado en módulos funcionales	Estado reactivo en memoria (`appState`), motor de vigencia histórica de metas, algoritmos de evaluación semanal y rachas elásticas ($M_t$), y delegación centralizada de eventos.
**Almacenamiento Local-First**	IndexedDB asíncrono (`idb_store`) + Event-Sourcing Append-Only + Snapshots automáticos	Supera el límite de 5 MB de localStorage, evita bloqueos de hilo principal y crea instantáneas compactadas cada 100 eventos (`schemaVersion: 3`).
**Blindaje Móvil W3C**	W3C Storage Persistence API (`navigator.storage.persist()`)	Impide que los navegadores móviles en Android/iOS purguen la base de datos local ante escasez de almacenamiento interno. Muestra estado visual en cabecera.
**Seguridad y Cifrado P2P**	Web Crypto API (`window.crypto.subtle`: PBKDF2-SHA256 100k + AES-GCM 256-bit)	Permite exportar e importar bóvedas cifradas completas (`.tsvault.json`) para sincronización segura entre móvil y laptop sin servidores intermedios.
**Interoperabilidad y Sincronización**	Token Delta-Sync (`TSDELTA3:...`) + Matriz visual generada en SVG nativo	Empaqueta y fusiona deltas recientes (últimos 7 días) entre dispositivos pares en menos de 3 segundos sin colisiones.
**Motor de PLN On-Device**	Reglas léxico-sintácticas locales + Diccionario Dialéctico Extendido de TS Dominicano + Compatibilidad Chrome Prompt API	Análisis de sesgos, eufemismos y reencuadre crítico basado en Paulo Freire y Óscar Jara, 100% funcional sin conexión y sin enviar textos a nubes externas.
**Telemetría Biométrica**	Parser CSV/JSON de Wearables (Google Fit, Apple Health, Mi Fitness, Garmin)	Ingesta de horas de sueño, frecuencia cardíaca en reposo y pasos, activando recomendaciones preventivas de descanso.
**Compilador Polimórfico**	Motor HTML/CSS con `@media print` + Exportador MIME `.doc` (Word)	Genera actas y relatorías foliadas con membrete oficial TS_SergDVD y firma comunitaria para asambleas barriales y el Ayuntamiento de Neiba.

——————————————————————————————
3. Modelo de Dominio y Estructura de Datos (Schema v3.2)
3.1. Dimensiones de Vida y Etiquetas Secundarias
El modelo organiza la vida cotidiana en cuatro pilares principales, una dimensión transversal visible y cuatro categorías secundarias opcionales:
1. Espiritual, trascendental y de fe (`espiritual`): Sentido de vida, oración, contemplación, gratitud, silencio, conexión con la naturaleza y coherencia ética. No presupone prácticas específicas ni traduce la fe a puntajes automáticos.
2. Afectiva y relacional (`afectiva`): Familia, amistades, pareja (conmutable según el momento vital), escucha activa, reciprocidad y límites saludables.
3. Productiva, formativa y laboral (`productiva`): Separa estrictamente las obligaciones de naturaleza `institucional` (lunes a viernes, sábado libre salvo excepción) de las de `iniciativa_propia` (formación en Trabajo Social, marca TS_SergDVD, escritura e IA ética).
4. Social, gremial y comunitaria (`social`): Educación popular, diálogo de saberes, participación gremial y articulación en Neiba/Bahoruco. Registra aportes individuales de facilitación sin apropiarse de resultados colectivos.
5. Bienestar físico, emocional y descanso (`bienestar` - Transversal): Sueño, movimiento corporal, nutrición consciente y pausas de recuperación. Visible de forma continua en cabecera y reportes.
6. Etiquetas transversales (`secondaryTags`): `aprendizaje` (Filomatía), `creatividad`, `economia` y `disfrute`. Vinculables a cualquier hábito o proyecto sin duplicar cómputos cuantitativos.
3.2. Estructura del Estado Global (`appState`)
El estado almacena la configuración de capacidad (`availableHoursToday`, `perceivedEnergyToday`), las dimensiones, hábitos con historial inmutable (`goalHistory`), proyectos, objetivos, bitácoras cualitativas (`journal`), revisiones semanales tripartitas, auditorías de decisiones (`decisionsLab`), pulsos territoriales (`fieldPulses`), registros biométricos (`wearableTelemetry`) y el log append-only de eventos con instantáneas (`snapshots`).
——————————————————————————————
4. Motores Matemáticos, Algoritmos y Reglas de Negocio
4.1. Semántica y Evaluación de los 6 Estados Cotidianos
Cada interacción (hábito, fecha) se evalúa bajo uno de seis estados mutuamente excluyentes:
•	Cumplido (`cumplido`): Ocasión lograda (100% de la meta de referencia). Suma al numerador evaluado y sostiene racha.
•	Parcial (`parcial`): Registra avance cuantitativo real. Aporta proporcionalmente al avance acumulado.
•	No realizado (`no_realizado`): Ocasión evaluada sin avance (0%). Computa en el denominador y reinicia la racha tradicional.
•	Descanso (`descanso`): Neutral: descuenta la ocasión del denominador en días fijos. No penaliza ni altera rachas.
•	Pausado con motivo (`pausado`): Neutral con motivo obligatorio (ej. lluvia o salud). Reduce el denominador de cuota semanal sin contar como fallo.
•	Sin registrar (`sin_registrar`): Estado pendiente de información. No se asume como incumplimiento y mantiene la racha en espera.
4.2. Ecuación de Impulso Elástico y Racha Resiliente ($M_t$)
Para erradicar la frustración del modelo todo-o-nada punitivo, la versión 3.2 incorpora la fórmula diferencial de momento con vida media de 7 días:
M_t = M_{t-1} * e^(-lambda * dt) + w * A_t
Donde:
•	lambda = ln(2) / 7 ≈ 0.099021 (tasa de decaimiento temporal).
•	w = 1 - e^(-lambda) ≈ 0.094277 (factor de normalización de peso diario).
•	A_t en [0.0, 1.0] es la puntuación de asistencia no punitiva:
•	A_t = 1.0: Cumplimiento total de la meta estándar.
•	A_t = 0.65: Cumplimiento del Piso Mínimo Innegociable en día de baja energía.
•	A_t = 0.50: Avance parcial significativo.
•	A_t = 0.20: Pausa justificada registrada (resiliencia adaptativa).
•	A_t = 0.00: Día no realizado (produce una contracción suave de ~9.5% sin desplomarse a cero).
4.3. Índice de Factibilidad Temporal con Fricción Territorial ($F$)
Evalúa la viabilidad real de los objetivos activos antes de iniciar la semana:
F = [T_disp * (1 - K_fricción)] / Sum(E_i)
Donde:
•	T_disp: Horas brutas semanales disponibles (Horas/día * 6).
•	K_fricción en [0.10, 0.45]: Coeficiente de contingencias territoriales (cortes eléctricos, lluvias en Bahoruco, imprevistos comunitarios; configurable, por defecto 0.25).
•	Sum(E_i): Suma de horas requeridas por los objetivos activos.
•	Criterio: Si F < 1.0, el sistema emite una alerta preventiva y ofrece un botón para activar la Simplificación Atómica (conmutando hábitos a versión mínima).
4.4. Regla de las 3 Postergaciones y Temporizador Atómico de 15 Minutos
•	Regla de las 3 Postergaciones (Doc 42): Si una tarea puntual acumula 3 o más postergaciones consecutivas, se resalta en rojo con advertencia crítica: "O la ejecutas hoy en un bloque de 15 minutos o la eliminas de la lista sin culpa".
•	Temporizador Atómico de 15 Minutos (Doc 53): Protocolo antipánico con cuenta regresiva interactiva, diagnóstico de causa raíz (tarea difusa, falta de espacio en agenda o miedo al juicio) y visualizador de escenario temido en 4 preguntas.
——————————————————————————————
5. Módulos Especializados e Innovaciones v3.2
5.1. Protocolo Táctico del Lunes en 10 Minutos (Doc 42)
Estructura la semana laboral e investigativa en cuatro componentes innegociables:
1. 3 Bloques Profundos (90 min): Dedicados exclusivamente a lo que mueve la aguja en las horas de mayor energía.
2. 2 Bloques de Gestión (45 min): Trámites institucionales, mensajería y llamadas.
3. 2 Colchones Territoriales (Huecos libres): Espacios sin agendar para absorber imprevistos en Neiba.
4. Filtro "¿Qué saco?": Descarte deliberado de compromisos de bajo impacto para proteger el equilibrio vital y el sábado libre.
5.2. Laboratorio Dialéctico de Decisiones y Análisis Pre-Mortem (Doc 48)
Herramienta de auditoría para evaluar nuevos compromisos territoriales o institucionales:
•	Filtro de reversibilidad: Diferencia decisiones reversibles en menos de 1 semana de compromisos estructurales.
•	Supuesto vertebral: Identifica la premisa oculta que, si resulta falsa, hunde la decisión.
•	Análisis Pre-Mortem: Identifica las 5 formas más probables de fallo y define señales tempranas de alerta y acciones de contingencia.
5.3. Diccionario Dialéctico Extendido de Trabajo Social Dominicano
Motor de reglas léxico-sintácticas locales que detecta eufemismos burocráticos y los reencuadra hacia la pedagogía crítica de Paulo Freire y la sistematización de experiencias de Óscar Jara:
•	"Se le dio seguimiento" -> Precisar acuerdo verificable con la comunidad o familia.
•	"La comunidad no se presentó" -> Analizar mediaciones territoriales (horarios de faena agrícola, lluvias, convocatoria previa).
•	"La gente no participa" -> Evaluar pertinencia temática frente a necesidades sentidas de los barrios de Neiba.
•	"Esperando respuesta de la capital" -> Identificar márgenes de articulación autónoma municipal en la Región Enriquillo.
5.4. Compilador Polimórfico a Relatorías Oficiales Foliadas
Permite exportar el balance semanal, las métricas no punitivas y los pulsos de campo en formato foliado oficial con membrete TS_SergDVD y bloques de firma para validación en asambleas barriales, contrapartes institucionales o el Ayuntamiento de Neiba:
•	Vista previa e impresión PDF: Renderizado optimizado con reglas `@media print`.
•	Exportación `.DOC` editable: Documento compatible con Microsoft Word y LibreOffice.
5.5. Pipeline Local de Sanitización NER (Named Entity Recognition)
Anonimiza automáticamente textos antes de copiarlos a herramientas externas de IA o portapapeles:
•	Cédulas de identidad y electoral dominicanas (XXX-XXXXXXX-X -> `[CEDULA_PROTEGIDA]`).
•	Números telefónicos locales e internacionales (`[TELEFONO_PROTEGIDO]`).
•	Direcciones de correo electrónico (`[CORREO_PROTEGIDO]`).
•	Nombres propios vinculados a casos de intervención social (`familia / paciente / caso [IDENTIDAD_ANONIMIZADA]`).
——————————————————————————————
6. Verificación Técnica y Cumplimiento Normativo
El sistema ha sido verificado exhaustivamente bajo estándares de accesibilidad WCAG 2.2 AAA (en modo OLED) y pruebas funcionales deterministas:
Módulo probado	Procedimiento de prueba	Resultado verificado
**Persistencia IndexedDB**	Creación y recuperación asíncrona de snapshots	Éxito: almacenamiento tolerante a fallos y sin bloqueo de UI.
**Protección W3C**	Solicitud `navigator.storage.persist()`	Conectada con insignia reactiva en la cabecera.
**Cifrado AES-GCM**	Cifrado y descifrado de cápsulas con contraseña	Integridad criptográfica verificada con PBKDF2 y Web Crypto.
**Sincronización P2P Delta**	Generación de token `TSDELTA3:` y fusión de registros	Fusión idempotente sin pérdida de datos históricos.
**Ingesta de Wearables**	Parseo de series CSV de sueño y pulso	Cálculo automático de noche de mayor desgaste y alertas de fatiga.
**Compilador Foliado**	Generación de reporte imprimible y exportación `.DOC`	Descarga limpia de archivo Word con tabla formal y firmas.
