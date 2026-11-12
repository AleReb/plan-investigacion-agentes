# Viabilidad de las publicaciones prioritarias

Actualizado: 2026-11-12. Resultado de V01/V02/V03, ejecutadas por agentes gpt-6.1-sol y revisadas por el coordinador. Se mantiene la visión general del portafolio; la selección siguiente identifica por dónde comenzar, no descarta las otras líneas.

## Decisión de trabajo

**Principal: A, contratos de datos y trazabilidad en publicación ambiental. Alternativa: C, trazabilidad de datos ciudadanos. B, evaluación de aire: recuperar evidencia original antes de convertirla en manuscrito reproducible.** Esta es una recomendación operativa por disponibilidad y verificabilidad de materiales, no por novedad demostrada ni probabilidad de aceptación editorial.

| Línea | Evidencia nueva | Estado editorial razonable | Próxima condición |
| --- | --- | --- | --- |
| A — Aire/agua: publicación de series | Dos exportadores reales, configuraciones y pruebas fijados por blob; patrón común y diferencias semánticas observables | Viable para diseñar evaluación de software/métodos; no hay resultados de ejecución todavía | Contrato explícito, fixtures, comparación fuera de producción y muestra real autorizada |
| C — Monitoreo ciudadano del agua | Historias Git relacionadas; tres fechas de Canelo comparadas XLSX→JSON, 27 campos coincidentes | Viable para ampliar auditoría de procedencia; aún no descriptor de datos completo | Versión canónica, trazabilidad previa a planilla, diccionario, QA/QC y derechos |
| B — Evaluación de sensores de aire | Dos informes completos: campaña de co-ubicación y ensayo electrónico | Material científico concreto, pero reproducción condicionada | Series pareadas, scripts, selección 80/20 e identificación inequívoca sensor/firmware/campaña |

## A: aporte más preciso que “una plataforma de sensores”

Los exportadores de aireaconcagua y calidadAgua convierten observaciones por sensor/variable en archivos por estación/mes. El código revisado aplica reglas diferentes para valores faltantes, selección de última lectura, desempate y manifiestos. Los CSV anchos no conservan los identificadores fuente; asignaciones por fecha/variable pueden sustituir entradas previas. Se trata de comportamiento inferido del código, **no de pérdidas observadas en producción**. [V02: informe, versiones y localizadores](resultados/V02/informe.md).

La contribución candidata es definir y evaluar un contrato que permita contabilizar transformaciones, rechazos y colisiones y reconstruir cómo se publicó cada observación. La generalidad de conectar sensores a un portal ya tiene antecedentes; no debe presentarse como novedad propia sin diferenciación. El artículo ODM2/EnviroDIY describe precisamente una integración de nodos, API, almacenamiento y acceso a datos. [Horsburgh et al., 2019](https://www.frontiersin.org/journals/earth-science/articles/10.3389/feart.2019.00067/full).

**Título de trabajo refinado:** «Contratos verificables de datos para publicar series ambientales heterogéneas: evaluación en dos implementaciones de aire y agua».

**Pregunta:** ¿hasta qué punto un contrato explícito de identidad, tiempo, calidad y publicación permite detectar y contabilizar diferencias que las verificaciones estructurales de los exportadores no cubren?

No se propone demostrar superioridad global sobre ODM2 ni sobre herramientas no implementadas. La comparación inicial será entre comportamiento de versiones fijadas, criterios del contrato y escenarios reproducibles. El [protocolo de evaluación preliminar](protocolos/A_EVALUACION_OFFLINE.md) deja definida la próxima tanda.

## C: primera prueba puntual de procedencia informática

En el checkout local de Voluntarios por el Agua se contrastaron Canelo, abril–junio de 2022: tres fechas, 18 valores numéricos y 9 ausencias/null coincidentes. El coordinador repitió el núcleo de comparación con lectura XML/JSON independiente, sin ejecutar el generador. Esto valida **esa correspondencia puntual**, no calidad instrumental, historia de generación, todas las estaciones ni datos publicados. [V03](resultados/V03/informe.md).

GitHub confirma que cmasudd/main forma parte de la historia de AleReb/main al momento de consulta; tienen SHA distintos y la comparación no reporta diferencias de archivos entre esos extremos. Ambos son posteriores al checkout local. Se observaron cambios remotos de coordenadas; no se validó su corrección geodésica ni el despliegue. La auditoría local conserva explícitamente su versión anterior.

**Ruta viable:** protocolo de curación y trazabilidad con registro por celda/observación y decisiones justificadas. Para convertirlo en descriptor de datos hay que ampliar cobertura y resolver fuentes, unidades, repeticiones, coordenadas y permisos. La procedencia informática no sustituye control de calidad del muestreo. [Antecedente primario OPAL, resumen consultado](https://discovery.ucl.ac.uk/id/eprint/1505739/).

## B: resultados documentados que requieren reconstrucción

El informe de campo describe co-ubicación en SINCA Las Condes entre el 11 y 28 de octubre de 2025, ajuste por bandas térmicas y partición 80/20. Reporta mejoras para algunos sensores y un resultado desfavorable/no mejorado para CO; ambos deben conservarse. El informe de laboratorio posterior mide offsets electrónicos sin sensores conectados, no sensibilidad a gases. No se ha demostrado que sus placas/parámetros sean los empleados en la campaña anterior. [V01](resultados/V01/informe.md).

Se localizaron tablas/figuras derivadas, pero no series originales ni scripts de análisis en el árbol revisado. También hay fechas y etiquetas textuales que deben aclararse. No se puede recalcular error, deriva, completitud o independencia de la evaluación con esos PDF solamente.

**Ruta de recuperación:** series fuente y referencia con timestamps/unidades, código o planilla de análisis, selección exacta ajuste/prueba, versiones y correspondencia de módulos. Si se recuperan, revisar método y revaluar prioridad. Si no, preparar memoria técnica o nueva campaña, sin fabricar series desde gráficos. Los protocolos EPA consultados ofrecen un marco para exterior/fijo no regulatorio; su aplicabilidad concreta y métricas deben revisarse antes de adoptarlos. [Fuente institucional](https://www.epa.gov/air-sensor-toolbox/air-sensor-performance-targets-and-testing-protocols).

## Lo que cambia en el plan

1. Mantener A como principal y C como alternativa. B permanece en recuperación; D–G siguen candidatas del panorama, sin nueva evidencia esta tanda.
2. Próxima tarea A01: banco de escenarios fuera de producción y contraste de hallazgos estáticos de V02. A02: literatura enfocada y tabla de diferencias; todavía no se cierra T08.
3. Próxima tarea C01: extensión acotada a faltantes, fechas repetidas y versiones remotas, separando anomalía observada de corrección autorizada.
4. B01: localizar fuentes originales accesibles; si no están disponibles, registrar exactamente qué debe aportar el responsable. No enviar mensajes al equipo sin instrucción del usuario.
5. Guardar cada tanda con evidencias, revisión y CONTINUAR.md. No se modificaron repositorios fuente ni producción.

La exploración bibliográfica inicial tiene tres fuentes primarias y alcance de lectura limitado. No equivale a revisión sistemática ni establece novedad. [Registro de búsquedas y límites](bibliografia/EXPLORACION_2026-11-12.md).
