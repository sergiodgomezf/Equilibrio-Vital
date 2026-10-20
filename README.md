TS_SergDVD · Equilibrio Vital (README)
Documentación General, Despliegue en GitHub Pages y Manual de Arquitectura
TS_SergDVD · Seguimiento de Hábitos, Objetivos y Equilibrio Vital
**Sistema Web Interactivo Local-First para Planificación Flexible, Cuidado Integral y Trabajo Social Crítico**
**Titular y Diseñador:** Sergio David Gómez Florián (`TS_SergDVD`)
**Ubicación Territorial:** Neiba, Provincia Bahoruco, República Dominicana
**Versión Actual:** `v3.2 Local-First` | **Licencia:** MIT / Abierta para la Comunidad
[![GitHub Pages](https://img.shields.io/badge/Deploy-GitHub_Pages-teal?logo=github)](https://sergiodgomezf.github.io/Equilibrio-Vital/)
[![Architecture](https://img.shields.io/badge/Architecture-Local--First_SPA-blue)](#arquitectura-técnica)
[![Privacy](https://img.shields.io/badge/Privacy-Zero_Tracking_%7C_AES--GCM_256-emerald)](#privacidad-y-soberanía-de-datos)
[![Accessibility](https://img.shields.io/badge/Accessibility-WCAG_2.2_AAA_(OLED)-black)](#modo-campo-silencioso-y-oled-para-terreno)
——————————————————————————————
🌐 Aplicación en Producción
Puedes utilizar la aplicación directamente desde cualquier dispositivo (computadora, tableta o teléfono móvil) sin necesidad de instalar nada:
🔗 [https://sergiodgomezf.github.io/Equilibrio-Vital/](https://sergiodgomezf.github.io/Equilibrio-Vital/)
——————————————————————————————
🧭 ¿Qué es TS_SergDVD Equilibrio Vital?
TS_SergDVD Equilibrio Vital es una plataforma de software ético creada a la medida de la práctica profesional de Sergio David Gómez Florián, combinando el rigor del Trabajo Social, la Educación Popular (Paulo Freire), la Sistematización de Experiencias (Óscar Jara), la Multipotencialidad/Filomatía y el uso crítico de la Inteligencia Artificial.
A diferencia de las aplicaciones comerciales de hábitos centradas en la productividad tóxica, el castigo por rachas rotas o la venta de datos personales, este sistema funciona como un espejo reflexivo no punitivo que respeta el ritmo humano, la reserva energética y las realidades del contexto comunitario en el suroeste dominicano.
——————————————————————————————
⚡ Características Principales (v3.2)
1. Planificación Flexible y Cuidado de la Reserva Vital
•	Modo de Baja Energía (Piso Mínimo Innegociable): Reduce las metas a sus versiones mínimas acordadas en días de fatiga sin alterar las metas originales ni el historial previo.
•	Protección del Sábado Libre: Las obligaciones laborales/institucionales se agendan de Lunes a Viernes por defecto, protegiendo el descanso del fin de semana.
•	Separación de Tiempos: Distingue el *Tiempo Operativo/Administrativo* (optimizable en bloques) del *Tiempo Relacional y de Cuidado* (escucha comunitaria y presencia afectiva no apresurable).
2. Matemáticas Transparentes y Rachas Resilientes
•	Ecuación de Impulso Elástico ($M_t$): Racha no punitiva con vida media de 7 días. Si un día no se cumple, el impulso se contrae suavemente en lugar de derrumbarse a cero.
•	Calculadora de Factibilidad Temporal con Fricción Territorial ($F$): Ajusta la capacidad semanal descontando el coeficiente de fricción ($K = 0.25$) para prever cortes eléctricos, clima o emergencias en Neiba.
•	Dos lecturas complementarias: Diferencia el *Cumplimiento sobre ocasiones evaluadas* del *Avance confirmado sobre lo programado*.
3. Herramientas Tácticas contra la Procrastinación y Parálisis
•	El Plan del Lunes en 10 Minutos (Doc 42): 3 bloques profundos de 90 min (lo que mueve la aguja), 2 bloques de gestión de 45 min y 2 colchones de contingencia territorial.
•	Regla de las 3 Postergaciones: Alerta si una tarea se pospone tres veces seguidas para ejecutarla en 15 minutos o descartarla sin culpa.
•	Temporizador Antipánico de 15 Minutos (Doc 53): Micro-pasos enfocados con diagnóstico de causa raíz y superación del escenario temido.
•	Visualizador del Yo Futuro Bipolar a 12 Meses: Confronta la Versión A (inercia) frente a la Versión B (avance constante con equilibrio).
4. Trabajo Social Crítico y Acompañamiento Comunitario
•	Laboratorio Dialéctico de Decisiones (Doc 48): Filtro de reversibilidad, detección del supuesto vertebral y análisis Pre-Mortem.
•	Diccionario Dialéctico de Trabajo Social Dominicano: 12 reglas de reencuadre emancipador para erradicar la culpabilización comunitaria y el lenguaje pasivo burocrático.
•	Modo Campo Silencioso: Registro de pulsos atómicos de terreno en 1 toque (escucha, contingencia, saberes locales) sin interrumpir la mirada.
•	Compilador Polimórfico a Relatorías Foliadas: Genera documentos oficiales foliados con membrete institucional listos para imprimir en PDF o descargar en Word (`.DOC`) para asambleas comunitarias o el Ayuntamiento de Neiba.
5. Soberanía de Datos, Privacidad y Sincronización
•	Arquitectura 100% Local-First: Base de datos IndexedDB asíncrona y Append-Only Event Log inmutable.
•	Blindaje Móvil W3C (`navigator.storage.persist()`): Previene que Android o iOS purguen los datos locales por falta de memoria.
•	Sincronización P2P Delta en 3 segundos: Transferencia de cambios recientes entre teléfono y computadora mediante Token `TSDELTA3:` y matriz QR visual sin servidores intermediarios.
•	Cifrado AES-GCM de 256 bits: Generación de bóvedas de respaldo protegidas con contraseña mediante Web Crypto API.
•	Filtro NER de Anonimización: Oculta automáticamente cédulas, teléfonos, correos y nombres sensibles antes de copiar textos a prompts de IA.
——————————————————————————————
🗂️ Estructura de las 7 Vistas de la Aplicación
1. 1. Hoy: Capacidad del día, Única Tarea Innegociable, Proyecto en foco con nota *"Dónde quedé"*, bloques flexibles, temporizador de 15m y registro en un toque.
2. 2. Semana: Calendario interactivo Lun-Dom, Cuadrícula de Asistencia Pura [X], Plan Táctico del Lunes, desglose de cálculo transparente y gráfico semanal.
3. 3. Dimensiones de vida: 4 pilares (Espiritual, Afectiva, Productiva, Social) + Bienestar transversal visible, ponderaciones editables y categorías secundarias sin duplicar puntuación.
4. 4. Hábitos y proyectos: Gestión de hábitos con vigencia histórica de metas (`goalHistory`), control de proyectos activos (máx. 3), tareas puntuales, objetivos con ingeniería inversa, banco de ideas, decisiones auditadas y biblioteca de prompts de IA.
5. 5. Diario reflexivo: Bitácora cotidiana con 5 preguntas generadoras, escalas no clínicas de energía/ánimo/satisfacción y codificación con Universo Vocabular freiriano.
6. 6. Revisión semanal: Panel epistemológico tripartito (*Lo escrito*, *Datos cuantitativos*, *Observaciones descriptivas por reglas locales*), síntesis reflexiva y previsualizador de relatoría foliada.
7. 7. Configuración y respaldo: Conmutador entre Modo Demostración y Mis Datos Reales, sincronizador Delta P2P, cifrado AES-GCM, exportador JSON/CSV e importador con prevención de duplicados por ID.
——————————————————————————————
🛠️ Instalación y Uso Local
La aplicación es un único archivo HTML autocontenido que no requiere Node.js, Python ni conexión a internet para funcionar:
```bash
1. Clonar el repositorio
git clone https://github.com/sergiodgomezf/Equilibrio-Vital.git
2. Entrar en la carpeta
cd Equilibrio-Vital
3. Abrir la aplicación directamente en cualquier navegador
En Windows:
start index.html
En macOS:
open index.html
En Linux:
xdg-open index.html
```
——————————————————————————————
📄 Documentación Adicional
•	Especificación Técnica y Metodológica Detallada v3.2: Disponible en el repositorio como `especificacion_tecnica_ts_sergdvd.md` y en formato descargable para revisión académica o institucional.
——————————————————————————————
🤝 Créditos y Reconocimientos
•	Concepción, Marco Teórico y Diseño Contextual: Lic. Sergio David Gómez Florián (`TS_SergDVD`), Neiba, República Dominicana.
•	Inspiración Metodológica: Paulo Freire (Pedagogía del Oprimido), Óscar Jara Holliday (Sistematizació
