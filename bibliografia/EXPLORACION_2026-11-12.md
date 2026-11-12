# Bibliografía exploratoria para viabilidad A/B/C

Coordinador, 2026-11-12. Búsqueda inicial, no revisión sistemática ni validación de novedad. Se admiten fuentes primarias (artículos originales o documentos del organismo autor); las revisiones halladas no se usan aquí para sostener resultados originales. Alcance leído indicado por fuente. No se copiaron textos completos.

## Registro de búsqueda

Consultas iniciales: `environmental data portal ODM2 data sharing EnviroDIY publication paper`; `low cost air sensor evaluation framework performance metrics EPA report`; `citizen science water quality data quality assurance review primary research`. Seguimiento: `site.theoryandpractice.citizenscienceassociation.org "Yukon" "Data quality"`; `"Quality control in public participation assessments" "doi"`.

Se seleccionaron un antecedente de software, una guía metodológica institucional y un estudio original de control de calidad. Se descartaron de esta síntesis páginas comerciales, índices sin acceso suficiente y revisiones secundarias. No se rastrearon todas las citas ni se cubrieron exhaustivamente publicaciones recientes. Las fechas de rastreo del buscador no se usan como fechas de publicación.

## L01 — Portal de datos ambientales

Horsburgh, J. S.; Caraballo, J.; Ramírez, M.; Aufdenkampe, A. K.; Arscott, D. B.; Geleskie Damiano, S. (2019). *Low-Cost, Open-Source, and Low-Power: But What to Do With the Data?* Frontiers in Earth Science, 7. DOI: 10.3389/feart.2019.00067.

[Texto primario](https://www.frontiersin.org/journals/earth-science/articles/10.3389/feart.2019.00067/full). Consultados resumen, introducción y comienzo de diseño/arquitectura; no revisión completa de resultados. El artículo describe registro de nodos, envío por API, almacenamiento ODM2, visualización y descarga en un portal ligado a EnviroDIY. Es antecedente directo de integración sensor→portal. **Inferencia para A:** esa integración general no basta como novedad; evaluar diferencias concretas en contratos, conservación de procedencia y publicación histórica/reciente. No se ha demostrado superioridad frente a ODM2 ni implementado comparación experimental.

## L02 — Evaluación instrumental

U.S. EPA. *Air Sensor Performance Targets and Testing Protocols*. Página institucional, actualización indicada: 29-09-2026; consultada 12-11-2026.

[Fuente primaria](https://www.epa.gov/air-sensor-toolbox/air-sensor-performance-targets-and-testing-protocols), secciones Overview, Reports y Sensortoolkit. Presenta protocolos de campo/laboratorio y documentos para distintos contaminantes; el alcance descrito es monitoreo suplementario e informativo, exterior y fijo. **Inferencia para B:** identificar contaminante, uso y referencia antes de escoger métricas; no extrapolar automáticamente a interior o equipos móviles. No se leyeron todavía los informes técnicos completos ni se adoptaron umbrales. Esta fuente orienta método, no demuestra calidad del equipo del usuario ni cumplimiento regulatorio chileno.

## L03 — Control de calidad de datos ciudadanos

Rose, N. L.; Turner, S. D.; Goldsmith, B.; Gosling, L.; Davidson, T. A. (2016). *Quality control in public participation assessments of water quality: the OPAL Water Survey*. BMC Ecology, 16(Suppl 1), artículo 14. DOI: 10.1186/s12898-016-0063-2.

[Registro y resumen de autores en UCL](https://discovery.ucl.ac.uk/id/eprint/1505739/). Solo metadatos y resumen consultados; PDF completo pendiente. Describe controles de variabilidad, comparaciones entre participantes y expertos y otras verificaciones para evaluar los datos. **Inferencia para C:** coincidencia XLSX→JSON demuestra transformación en un alcance dado, no validez instrumental; procedencia informática y calidad de observación deben evaluarse por separado. Su diseño no se transfiere automáticamente a mediciones fisicoquímicas del Cajón del Maipo.

## Fuentes localizadas pero no usadas como evidencia leída

Herman-Mercer et al. (2018), DOI 10.5334/cstp.123: localizado registro USGS y PDF editorial; apertura USGS devolvió 403 y DOI no accesible. Queda como pista por recuperar, sin atribuir lectura completa. PMC para OPAL devolvió recaptcha; se accedió al registro institucional UCL como alternativa.

## Próxima revisión bibliográfica

Una vez cerrada la viabilidad: ampliar L01 con modelos/estándares y herramientas de datos ambientales y evaluaciones de pipelines; leer métodos/resultados y registrar tabla de diferencias. Para B seleccionar informe EPA pertinente y estudios instrumentales comparables. Para C leer OPAL completo y estudios fisicoquímicos con diseño de control verificable. Separar antecedente, criterio metodológico y comparación efectivamente ejecutada. Mantener T08 pendiente hasta una revisión enfocada suficiente.
