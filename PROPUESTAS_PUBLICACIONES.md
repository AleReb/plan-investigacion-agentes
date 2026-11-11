# Propuestas de papers y publicaciones

Fecha: 2026-11-11. Títulos y prioridades provisionales. Son propuestas del coordinador a partir de P01/P02/T01/T02; no se ha establecido novedad ni se han elegido revistas. Prioridad significa orden para comprobar viabilidad, no mérito científico demostrado.

## Lista corta para empezar

| Orden de exploración | Propuesta | Motivo |
| --- | --- | --- |
| 1 | Publicación reproducible de datos ambientales entre dispositivos, servidor y webs | Conecta varias partes de tu trabajo y hay patrones documentados en distintos proyectos |
| 2 | Evaluación instrumental de una configuración de la red de calidad del aire | Hay referencias concretas a informes de campo y laboratorio que podrían sostener resultados |
| 3 | Trazabilidad y publicación de monitoreo ciudadano del agua | Hay datos y una implementación local accesibles; brechas identificadas y abordables |

Trabajar primero una ficha de viabilidad de cada una; elegir después una principal y una alternativa. Si los informes de aire contienen datos completos y comparación válida, esa línea puede pasar al primer lugar. No hace falta redactar tres manuscritos simultáneos.

## A. De la adquisición a la publicación: series ambientales reproducibles

**Título provisional:** «Arquitectura reproducible para publicar series ambientales heterogéneas: experiencias en aire y agua».

**Trabajo conectado:** SensorsWebApp/sensores.cmasccp.cl, aireaconcagua, calidadAgua y aireAysen; firmware de adquisición como contexto cuya conexión concreta debe demostrarse. Evidencia: recorridos documentados de base de datos o fuente externa hacia CSV, manifiestos y consulta reciente. [P02](resultados/P02/panorama.md).

**Pregunta:** ¿qué contratos de datos y decisiones de arquitectura permiten conservar unidades, timestamps, faltantes y procedencia mientras se publican históricos descargables y lecturas recientes?

**Aporte candidato:** un método o componente reutilizable evaluado en varios contextos; varias webs parecidas no bastan para afirmar que existe una plataforma común. **Tipo:** artículo de software o métodos; caso técnico si todavía no hay componente generalizable.

**Qué medir:** correspondencia fuente→exportación, pérdidas/duplicados, recuperación tras interrupciones, tiempo hasta publicación y esfuerzo de configuración. Comparar implementaciones actuales con un contrato explícito y pruebas sobre copias autorizadas; no ensayar carga en producción.

**Siguiente paso:** leer dos exportadores y sus esquemas, fijar versiones/despliegues y verificar reutilización real. Continuar si hay un problema común demostrable y una evaluación reproducible; si solo comparten estética, reformular como casos de diseño.

## B. Calidad y continuidad de una red de sensores de aire

**Título provisional:** «Evaluación de una configuración de monitoreo atmosférico de bajo costo en condiciones de campo».

**Trabajo conectado:** estacion-calidad-aire, variantes HIRI y plataformas públicas pertinentes; confirmar qué dispositivo y firmware originaron cada campaña. **Evidencia inicial:** enlaces a informes de laboratorio/co-ubicación en README, no resultados reproducidos. [P01, línea 1](resultados/P01/panorama.md).

**Pregunta:** ¿con qué error, deriva y completitud mide una configuración identificada frente a referencia y bajo condiciones registradas? **Aporte candidato:** caracterización reproducible de un sistema real, con límites de uso. **Tipo:** evaluación instrumental o monitoreo ambiental; dataset asociado si procede.

**Qué falta:** informes completos, series pareadas, instrumentos/firmware, fechas, calibración y QA/QC. Separar datos usados para ajustar de los usados para evaluar; evitar presentar correlación alta como exactitud suficiente.

**Siguiente paso:** localizar y leer informes SINCA/laboratorio y determinar si existen datos originales. Si solo hay resúmenes sin datos recuperables, preparar nota técnica o diseñar nueva campaña, sin reconstruir resultados ficticios.

## C. Datos ciudadanos de agua con trazabilidad explícita

**Título provisional:** «Publicación trazable de observaciones ciudadanas de calidad del agua: el caso del Cajón del Maipo».

**Trabajo conectado:** voluntariosxagua local y versión cmasudd, documentación del proyecto, registros y fotos. **Evidencia inicial:** planilla de siete hojas y web; derivado local con 394 registros, sin equivalencia con originales aún probada. [T02](resultados/T02/ficha.md), [P02](resultados/P02/panorama.md).

**Pregunta:** ¿cómo preservar e informar procedencia, unidades, repeticiones, cobertura y localización incierta al publicar mediciones ciudadanas? **Aporte candidato:** protocolo de curación y recurso documentado que pueda reutilizarse. **Tipo:** descriptor de datos o artículo de métodos/caso de ciencia ciudadana, según evidencia disponible.

**Qué falta:** responsables de datos, permisos, versiones canónicas, diccionario, calibración, coordenadas y correspondencia planilla→web. No convertir repeticiones en errores por defecto ni concluir tendencias ambientales a partir del inventario.

**Siguiente paso:** auditar una estación y un período acotado con el responsable de datos. Si es reproducible y los derechos están claros, extender al conjunto. Un estudio de tendencias sería una pregunta distinta con requisitos adicionales.

## D. Instrumentación modular y un dispositivo reproducible

**Título provisional:** «Diseño y evaluación de un sistema modular de adquisición para instrumentación ambiental».

**Trabajo conectado:** LineaBase, miniMadre, biblioteca de hardware, placas y comunicaciones; modularAirFlow como candidato específico, no automáticamente representativo de todo. [P01, línea 2](resultados/P01/panorama.md), [T01](resultados/T01/ficha.md).

**Pregunta:** ¿qué parte del diseño puede reutilizarse entre configuraciones y con qué costo de integración, consumo y comportamiento ante fallos? **Tipo:** descripción de hardware con evaluación; nota de diseño si faltan ensayos.

**Aporte y evidencia faltante:** elegir una revisión concreta, unir CAD/BOM/firmware/manual, documentar contribuciones y licencias, y probar reproducción y funciones. No mezclar resultados de variantes incompatibles. La hipótesis de modularidad requiere comparar configuraciones reales.

**Siguiente paso:** elegir dispositivo y significado de «liberar». Un posible envío a HardwareX se considerará solo tras confirmar ese interés y consultar requisitos vigentes; no hay selección editorial ahora. En modularAirFlow se mantiene la instrucción de no compilar ni cargar firmware.

## E. Registro multiparamétrico de biodigestión

**Título provisional:** «Sistema de registro multiparamétrico para seguimiento experimental de biodigestores».

**Trabajo conectado:** firmwareBioDigestor y BIODIJESTOR, con sensores de temperatura, pH y conductividad descritos. [P01-E05](resultados/P01/evidencias.json).

**Pregunta:** ¿qué estabilidad, cobertura y errores de registro presenta el sistema durante una campaña? **Tipo:** instrumentación aplicada o nota técnica. **Aporte candidato:** adquisición y registro reproducibles; no se propone afirmar aumento de rendimiento biológico sin experimento específico.

**Siguiente paso:** localizar bitácoras/CSV de una campaña, contexto de operación y calibraciones. Sin registros recuperables, mantener como candidato de documentación y ensayo futuro.

## F. Recuperación verificable de conocimiento técnico

**Título provisional:** «Recuperación con procedencia de conocimiento técnico institucional a partir de documentación y material audiovisual».

**Trabajo conectado:** cmas-mcp, biblioteca de hardware y guías operativas, cuando sus derechos y vínculos se confirmen. **Evidencia inicial:** pipeline y 193 videos procesados declarados en README. [P01, línea 5](resultados/P01/panorama.md).

**Pregunta:** ¿qué mejora medible ofrece el procesamiento documental en exactitud y respaldo de respuestas frente a búsqueda léxica o consulta sin recuperación? **Tipo:** software/evaluación de sistemas de IA.

**Siguiente paso:** fijar corpus, preparar preguntas expertas independientes del material usado para ajustar el sistema y evaluar respuestas/citas con un baseline. No tratar los resúmenes generados como evidencia de calidad por sí mismos.

## G. Comunicación y uso comunitario de datos

**Título provisional:** «Cómo comunicar incertidumbre en portales ambientales comunitarios y educativos».

**Trabajo conectado:** modo Escolar de aireaconcagua, aireAysen, calidadAgua y voluntariosxagua. [P02, líneas 2 y 4](resultados/P02/panorama.md).

**Pregunta:** ¿cómo influyen las etiquetas de ubicación aproximada, datos agregados y mediciones preliminares en la interpretación? **Tipo:** estudio de interacción/comunicación científica; caso descriptivo si solo se documentan decisiones de diseño.

**Siguiente paso:** identificar usuarios y tareas reales, revisar literatura y diseñar evaluación con métricas de comprensión y muestra justificada. No atribuir impacto educativo o comunitario a la mera existencia de los sitios.

## Publicaciones complementarias y coherencia del programa

Mientras se recupera evidencia, pueden prepararse una memoria técnica del ecosistema, guías de montaje/operación, un catálogo de prácticas docentes o una serie de artículos de divulgación con proyectos y límites documentados. Docencia y visión artificial aparecen en el inventario, pero aún no tienen lectura suficiente para priorizar un paper específico.

Las líneas A/C/G pueden compartir infraestructura, pero deben distinguir contribución: A estudia arquitectura/transformación; C, procedencia y calidad de un recurso ciudadano; G, interpretación por usuarios. Publicar los mismos resultados cambiando el relato no produciría tres contribuciones diferentes. El mapa general puede servir de contexto común, con autores y datos atribuidos en cada caso.

Antes de redactar resultados: recuperar evidencia → ficha de viabilidad → revisión de literatura primaria → pregunta y método → análisis reproducible → manuscrito. Las próximas tareas concretas están en resultados/P03/informe.md y el punto de continuación en CONTINUAR.md.
