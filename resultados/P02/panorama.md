# P02 — Panorama transversal de webs y plataforma

- Estado solicitado: **en_revision**. Fecha: 2026-11-11.
- Objetivo: relacionar el portafolio web con audiencias, rutas de datos y posibles publicaciones; revisión documental acotada, sin auditoría de producción.
- Responsable: agente P02. Entradas: README del plan, AGENTS.md, docs/01-revision-inicial.md, docs/02-plan.md, docs/06-servidor-webs.md e inventario/cmasudd.json.
- Fuentes públicas mediante conector GitHub: cinco README, identificados por blob en evidencias.json. Artefactos: este panorama y manifiesto de evidencias. No se modificaron fuentes, backlog ni inventarios.

## Lectura general

La oportunidad transversal es estudiar cómo convertir observaciones ambientales heterogéneas en información pública explorable y descargable. Los README describen un portal React/Vite, dos webs de aire con procedencias diferentes, una web de sensores de agua y una web de monitoreo voluntario. Eso permite formular un programa sobre publicación, trazabilidad y comunicación de datos, antes de elegir un único dispositivo como centro del trabajo. Esta síntesis es una **inferencia**, apoyada en P02-E02 a E06; no demuestra innovación científica, impacto ni validación instrumental.

El usuario declara haber creado las webs y administrar sensores.cmasccp.cl (**declarado por usuario**, P02-E08). No se infiere autoría exclusiva, propiedad de todos los datos ni contribución de cada colaborador. El README de SensorsWebApp declara que cmasudd/SensorsWebApp es el repositorio canónico y CmasCcp/SensorsWebApp su referencia histórica (**declarado por documentación**, P02-E02). No se comprobó el commit actualmente desplegado.

## Cobertura y clasificación de los 13 repositorios

Fuente del conjunto: inventario local, observado inicialmente en la primera página HTML de cmasudd; no se verificó cobertura de paginación (P02-E01). En esta tabla, “nombre” significa **inferencia por nombre**, sin contenido consultado. Las audiencias y líneas marcadas como posibles son hipótesis de clasificación, no capacidades comprobadas.

| Repositorio | Familia y audiencia | Datos/función | Base y límite |
| --- | --- | --- | --- |
| [SensorsWebApp](https://github.com/cmasudd/SensorsWebApp) | Portal de sensores; audiencia operativa/técnica posible | Frontend React/Vite de sensores.cmasccp.cl; no se conoce aquí el contrato de API | README leído, P02-E02; audiencia inferida |
| [aireaconcagua](https://github.com/cmasudd/aireaconcagua) | Aire comunitario; comunidad y público escolar | MariaDB local→CSV mensuales; última lectura por API; contaminantes y meteorología | README leído, P02-E03; Red Comunitaria y modo Escolar declarados |
| [aireAysen](https://github.com/cmasudd/aireAysen) | Aire; público que explora/descarga datos | Looker Studio→promedios horarios MP1/MP2,5/MP10→CSV por sensor/mes; interior/exterior | README leído, P02-E04; público concreto y uso real pendientes |
| [calidadAgua](https://github.com/cmasudd/calidadAgua) | Agua y nivel; público general posible | Ocho estaciones, cinco lugares; CSV, manifiesto, última lectura y API reciente | README leído, P02-E05; se declara en preparación |
| [voluntariosxagua](https://github.com/cmasudd/voluntariosxagua) | Ciencia ciudadana; voluntarios y usuarios de datos fluviales | Planilla mensual y fotos→generador local→JSON/CSV; siete puntos del Cajón del Maipo | README leído, P02-E06; implementación declarada, no ejecutada |
| [monitorHIRI](https://github.com/cmasudd/monitorHIRI) | Monitor HIRI posible; público técnico por definir | Posible visualización vinculada a HIRI | Solo nombre, P02-E01; no afirmar integración con portal |
| [monitor](https://github.com/cmasudd/monitor) | Monitoreo posible; audiencia desconocida | Función y fuentes desconocidas | Solo nombre, P02-E01 |
| [HIRI232](https://github.com/cmasudd/HIRI232) | Instrumentación/interfaz posible | Relación con HIRI, RS-232 o hardware sin determinar | Solo nombre, P02-E01; no asumir protocolo |
| [auca-cochrane](https://github.com/cmasudd/auca-cochrane) | Proyecto territorial posible | Variables, ubicación efectiva y despliegue desconocidos | Solo nombre, P02-E01 |
| [giz](https://github.com/cmasudd/giz) | Proyecto institucional posible | Sigla, audiencia y datos sin determinar | Solo nombre, P02-E01; no atribuir socio |
| [buenas_practicas](https://github.com/cmasudd/buenas_practicas) | Operación/documentación; mantenedores posibles | Bitácora operativa referida desde SensorsWebApp | Referencia documental P02-E02; contenido no leído |
| [Propuesta_Licencia](https://github.com/cmasudd/Propuesta_Licencia) | Gobernanza/licencias posible | Posible propuesta de licenciamiento | Solo nombre, P02-E01; no constituye licencia aprobada |
| [analizadorDeseccionCables](https://github.com/cmasudd/analizadorDeseccionCables) | Herramienta de ingeniería posible | Posible análisis de sección de cables | Solo nombre, P02-E01; alcance ambiental y web sin comprobar |

## Repositorios → audiencias → datos

| Recorrido declarado | Audiencia/uso documentado o inferido | Oportunidad transversal y límite |
| --- | --- | --- |
| SensorsWebApp→sensores.cmasccp.cl; PM2 sirve public y se documenta operación en buenas_practicas | Mantenedores posibles; funciones del usuario final sin inspeccionar | Vincular servicio central con publicaciones satélite. La coincidencia de rutas api_sensores en otros README sugiere infraestructura compartida; no prueba esquema común ni dependencia completa (P02-E02/E03/E05) |
| MariaDB→exportador→CSV mensuales→GitHub Pages→aireaconcagua; API entrega una lectura por estación cada diez minutos | Red comunitaria y modo Escolar | Publicación histórica desacoplada de consulta reciente; faltan métricas de completitud, latencia, carga y uso (P02-E03) |
| Informe público Looker→descargador→CSV mensuales→aireAysen | Exploración y descarga pública; grupos interior/exterior | Procedencia externa y contrato de extracción frágil; no consulta base CMAS según README. No confundir los promedios horarios con observaciones crudas (P02-E04) |
| Publicador local→CSV/manifiesto/latest→calidadAgua; API reciente cada diez minutos | Consulta pública de calidad y nivel | Misma pauta histórica/reciente que aireaconcagua; nivel preliminar no es cota comparable entre lugares (P02-E05) |
| Jornadas mensuales→KoboCollect; planilla/fotos→generador→docs/JSON/CSV→voluntariosxagua | Voluntarios, público y reutilizadores | La transición Kobo→planilla validada no está cerrada documentalmente; las ubicaciones son aproximadas y los instrumentos no se declaran certificados DGA (P02-E06) |

Todos los recorridos son **declarados por documentación**, salvo inferencias expresas. No se descargaron datasets ni se recorrieron interfaces. Los README de aireAysen y calidadAgua advierten que el licenciamiento propuesto está en revisión; aireAysen advierte además falta de licencia en la fuente (P02-E04/E05). La accesibilidad pública no basta para redistribuir datos, fotografías, marcas o código.

## Cuatro publicaciones candidatas

Son propuestas de trabajo, **inferencias** basadas en las fuentes indicadas. No se revisó literatura ni se seleccionó revista; no hay decisión de novedad, causalidad o mérito editorial.

| Prioridad exploratoria / tipo | Pregunta y proyectos conectados | Paquete de evidencia que falta |
| --- | --- | --- |
| 1. **Software**: arquitectura reutilizable para publicar series ambientales heterogéneas | ¿Qué componentes y contratos permiten mantener históricos descargables y lecturas recientes entre aireaconcagua, calidadAgua y aireAysen, con SensorsWebApp como contexto operativo? P02-E02/E03/E04/E05 | Leer exportadores, esquemas, tests y workflows; fijar versiones; comprobar si existe código realmente compartido; definir contrato de unidades/tiempo/ausencias; reproducir exportaciones con datos autorizados; medir exactitud, fallos y costo de mantenimiento frente a alternativas. Resolver licencias. No asumir que varias webs constituyen una biblioteca reutilizable |
| 2. **Caso de estudio**: datos ambientales para comunidad y educación | ¿Cómo cambian las necesidades de exploración y actualización entre la red de aire Aconcagua y Voluntarios por el Agua? P02-E03/E06; calidadAgua como tercer contexto P02-E05 | Identificar actores y contribuciones, reconstruir decisiones, documentar tareas reales y problemas del sistema previo; protocolo de usabilidad, accesibilidad y comprensión con participantes y autorizaciones; evidencia de adopción. No declarar mejora de alfabetización o participación solo por existir una web |
| 3. **Datos**: paquete armonizado de observaciones ambientales con procedencia y calidad explícitas | ¿Es viable documentar datasets interoperables de aire y agua conservando fuente, resolución temporal y límites espaciales? AireAysen, aireaconcagua, calidadAgua y voluntariosxagua (P02-E03–E06) | Auditar cobertura por estación, unidades, huso horario, faltantes, duplicados, cambios de equipo y calibración; diccionario, identificadores y control de versiones; derechos y anonimización. El producto puede ser un catálogo o varios datasets relacionados: no mezclar variables como si midieran el mismo fenómeno |
| 4. **Investigación**: comunicación de incertidumbre en portales ambientales | ¿Cómo afectan a la interpretación las etiquetas de medición preliminar, agregación y ubicación aproximada? Comparar prototipos sobre aireAysen (horarios/interior-exterior), calidadAgua (nivel relativo) y voluntariosxagua (coordenadas aproximadas), con modo Escolar de aireaconcagua como contexto (P02-E03–E06) | Revisión bibliográfica, diseño experimental y aprobación aplicable; estímulos equivalentes; usuarios y muestra justificados; métricas de comprensión, errores y decisiones; análisis predefinido. No usar usuarios actuales ni instrumentación sin autorización ni concluir efecto causal antes del estudio |

La ruta 1 es la primera a evaluar porque hay patrones operativos declarados en varios proyectos; eso es disponibilidad documental, no una puntuación científica. La ruta 2 preserva la dimensión social del trabajo. La ruta 3 depende especialmente de derechos y calidad; la 4 exige datos nuevos con participantes. Un análisis de episodios de contaminación, tendencias o diferencias interior/exterior sería prematuro sin revisar cobertura, calibración, contexto y diseño de muestreo.

## Verificación y límites

- Acciones reales: lectura local mediante cat/rg; descubrimiento del conector GitHub; cinco llamadas fetch_file a README.md de los repos representativos. Las cinco respondieron contenido UTF-8, blob SHA y URL. Se preservan referencias y extractos mínimos en evidencias.json.
- No se ejecutaron comandos contenidos en README, tests, scripts de exportación, cron, builds ni consultas a bases. No se enviaron formularios, intentaron credenciales, inspeccionaron participantes ni modificaron sitios.
- La evidencia directa es que se leyó documentación; el funcionamiento narrado permanece declarado. El HTTP 200 inicial del portal procede de la revisión previa, no de una prueba nueva (P02-E08).
- No se inspeccionó monitorHIRI porque se alcanzó el límite de cinco README. Los ocho restantes mantienen incertidumbre visible. No se estableció identidad histórica entre AleReb/voluntariosxagua y cmasudd/voluntariosxagua: coincidir en nombre o relato no sustituye comparación de commits (P02-E08).
- Los enlaces GitHub con rama pueden cambiar; los blob SHA del manifiesto fijan el contenido leído. No hay atribución por commit ni manifiesto de despliegue.

## Criterios de entrega y siguiente tarea

| Criterio | Resultado | Evidencia |
| --- | --- | --- |
| Clasificar los 13 repos con nivel de lectura explícito | Cumple | Tabla y P02-E01–E06 |
| Relacionar repos, audiencias, datos y líneas de publicación | Cumple como panorama documental | Recorridos y propuestas; inferencias visibles |
| Consultar hasta cinco README representativos | Cumple: cinco | P02-E02–E06 |
| Evidencia verificable y límites de autoría/validación | Cumple en alcance documental | Manifiesto; despliegue, autores, datos y derechos pendientes |
| Verificar producción y calidad científica | Fuera de este alcance | No ejecutado |

Propuesta al coordinador: una tarea de trazabilidad con solo lectura para fijar commits de estos cinco repos y sus despliegues, comparar los dos voluntariosxagua y revisar un exportador representativo con su esquema/manifiesto, sin datasets personales ni secretos. Después elegir una publicación principal y solicitar una revisión de literatura orientada a su pregunta. Los repos no leídos requieren una ficha breve antes de descartar sus aportes. **Estado: en_revision.**
