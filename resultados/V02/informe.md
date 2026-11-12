# V02 — Viabilidad A: exportadores y contrato de datos

- **Estado solicitado: en_revision.** Fecha: 2026-11-12.
- Objetivo: revisar código de aireaconcagua y calidadAgua para identificar un problema común demostrable y un contrato candidato para la propuesta A.
- Responsable/modelo: agente V02, gpt-6.1-sol solicitado por coordinador.
- Alcance: lectura estática de seis archivos fuente: un exportador, sus pruebas y configuración de estaciones por repositorio. Sin ejecución de código, tests, publicadores, acceso a BD, credenciales o producción.
- Entradas locales: AGENTS.md, CONTINUAR.md, resultados/P03/informe.md, PROPUESTAS_PUBLICACIONES.md y plantillas. Los README representativos ya fueron leídos en P02; aquí se profundiza en código.
- Artefactos: informe.md y evidencias.json. No se modifican fuentes, inventarios, backlog ni despliegues.

## Conclusión de viabilidad

**Continuar A como candidato de software/métodos con evaluación fuera de producción.** Hay un problema técnico compartido observable: ambos exportadores convierten mediciones relacionales por sensor y variable en series anchas por estación/mes, manifiesto y lecturas recientes, pero divergen en semántica, validación y garantías. Esto supera la coincidencia estética. Todavía no hay evidencia de un componente común empaquetado, reproducibilidad extremo a extremo ni novedad científica. La recomendación es una **inferencia de viabilidad** sustentada en E01/E04; no una aprobación editorial ni un resultado experimental.

La contribución candidata sería especificar un contrato verificable y evaluar dos adaptadores existentes frente a ese contrato. Extraer código común es una opción posterior, cuya utilidad debe medirse frente a mantener dos implementaciones. No hace falta afirmar que ya existe una plataforma general.

## Fuentes fijadas

Los identificadores siguientes corresponden a **blobs Git**, no commits ni versiones desplegadas. El manifiesto registra localizadores y limitaciones. Todos se leyeron vía conector GitHub el 2026-11-12.

| ID | Repositorio / archivo | Blob y enlace inmutable |
| --- | --- | --- |
| E01 | aireaconcagua / scripts/export_monthly_csv.py | [e642b5897a5c0927e6b71a00fbd29a15bffad7d4](https://api.github.com/repos/cmasudd/aireaconcagua/git/blobs/e642b5897a5c0927e6b71a00fbd29a15bffad7d4) |
| E02 | aireaconcagua / tests/test_export_monthly_csv.py | [c3cebebcc162f1b2401d5e66ad4623a5f808fe7a](https://api.github.com/repos/cmasudd/aireaconcagua/git/blobs/c3cebebcc162f1b2401d5e66ad4623a5f808fe7a) |
| E03 | aireaconcagua / config/stations.json | [7950303f56000ca420323e2f9f004a4eff90470c](https://api.github.com/repos/cmasudd/aireaconcagua/git/blobs/7950303f56000ca420323e2f9f004a4eff90470c) |
| E04 | calidadAgua / scripts/export_monthly_csv.py | [9b860d7f3b0eb15a1a81ee2efdda9ca8fed9f066](https://api.github.com/repos/cmasudd/calidadAgua/git/blobs/9b860d7f3b0eb15a1a81ee2efdda9ca8fed9f066) |
| E05 | calidadAgua / tests/test_export_monthly_csv.py | [15201bce028c7a096aec3c5f01cb0d41bcf63675](https://api.github.com/repos/cmasudd/calidadAgua/git/blobs/15201bce028c7a096aec3c5f01cb0d41bcf63675) |
| E06 | calidadAgua / config/stations.json | [177135e8d621be28283310db6a7dd18c24ed0a37](https://api.github.com/repos/cmasudd/calidadAgua/git/blobs/177135e8d621be28283310db6a7dd18c24ed0a37) |

También se consultaron solo metadatos de árboles recursivos de main, ambos sin truncamiento: aireaconcagua árbol 6e5918a40f1f643a0aaa8c1a9b13a3786434133b; calidadAgua árbol e58e0ff2f85ec60efe799fbb670dead5296e9b91 (E07/E08). Sirvieron para seleccionar archivos; no se descargaron CSV, fotos, hojas de cálculo ni otros contenidos. Un árbol no identifica por sí solo un commit desplegado.

## Lo compartido y lo específico

Todo hecho de esta sección es **observado directamente en código**; describe rutas programadas, sin demostrar su ejecución.

| Aspecto | Coincidencia implementada | Diferencia relevante / localizador |
| --- | --- | --- |
| Selección de fuentes | Configuración vincula code/device_id; consulta sensores_en_dispositivo→sensores→sensores_tipo y lista de modelos admitidos | Aire usa Source y error si no hay sensores publicables; agua permite lista vacía. E01 L109–158; E04 L77–87; configs E03/E06 |
| Consulta temporal | datos por id_sensor/id_variable, intervalo mensual [inicio, fin), índice idx_datos_sensor_fecha | Aire pagina 5.000 filas por fecha/id_dato; agua itera una consulta por sensor/mes sin paginación explícita. E01 L189–249; E04 L89–97. No se midió memoria ni rendimiento del conector |
| Ensanchamiento | Agrupan por timestamp exacto, asignando una celda por variable; ordenan timestamps al escribir | No hacen promedio ni alineación a una grilla. Aire conserva fila aunque valor -1 pase a vacío; agua solo crea celda/fila si clean acepta valor. E01 L234–264; E04 L90–105 |
| Transformaciones | Traducción modelo+id_variable→nombre público | Aire escala SO₂ por 1000 y usa alias cortos; agua aplica rangos por variable/modelo y redondea a tres decimales. E01 L29–67/L234–244; E04 L14–37/L61–75. La interpretación ppm→ppb está declarada en comentario; no se comprobó en BD |
| Ficheros históricos | UTF-8, CSV ancho, LF, fecha textual y ruta code/AAAA-MM-part-NNN.csv; temporal→fsync→replace para cada archivo escrito | Aire divide en partes y elimina obsoletas; agua escribe solo part-001, borra ese archivo si no hay filas y no incluye particionador. E01 L251–295; E04 L98–108 |
| Historial publicado | Regeneran mes vigente por defecto; --all descubre desde primera medición | Agua impone inicio 2025-01; aire permite --month/--station/--config. Agua no ofrece esos filtros en su CLI. E01 L392–449; E04 L13/L82–87/L110–128 |
| Manifiesto | schema_version=1, timezone America/Santiago, stations, months y updated_at | Aire añade max_csv_bytes pero no diccionario de variables; agua añade variables con unidades/notas/diagnostic y variables por estación. E01 L359–389; E04 L127–136 |
| Estaciones | Identidad code y vínculo device_id | Aire: 10 entradas con name/location; agua: 8 con site/context/project/project_id y lat/lng. E03 completo, E06 completo. Coordenadas son configuración leída, no ubicaciones validadas |
| Reutilización visible | Dependencia mysql.connector y primitivas estándar para CSV/JSON/fechas | Los dos exportadores implementan localmente sus funciones y no importan un módulo compartido del proyecto. E01 L9–22/L76–389; E04 L5–10/L39–136. No se inspeccionaron paquetes externos, historia o todo el código |

**Inferencia:** límites mensuales, descubrimiento de fuentes, escritor, manifiesto y validación de contratos son candidatos a reutilización; mapeos de sensores, conversiones, reglas de calidad, cobertura inicial y metadatos territoriales deben ser perfiles configurables. La semejanza no prueba copia, autoría común ni equivalencia funcional.

## Brechas concretas que justifican evaluación

Las consecuencias siguientes son **inferencias del flujo estático**. No son incidentes observados en producción.

1. **“Último” tiene contratos diferentes.** Aire consulta una ventana limitada de lecturas por sensor y descarta -1; una variable sin dato válido en esa ventana puede omitirse, aunque exista un dato anterior. Además, distintos sensores pueden producir varias filas del mismo code/variable. Agua calcula newest solo entre meses regenerados: una ejecución normal sin datos del mes puede omitir una estación o variable de latest aun cuando conserve histórico. Aire usa variable=mp25/temp/etc.; agua usa ph/temperatura_agua_c/etc. El encabezado largo coincide, pero el vocabulario no. E01 L298–344/L347–356; E04 L115–135.
2. **Colisiones y procedencia perdida.** La asignación por timestamp y variable sobrescribe valores previos; si varios sensores aportan la misma variable en un instante, el recorrido de fuentes interviene en cuál queda. Aire ordena dentro del sensor por fecha/id_dato, agua solo por fecha; empates en agua no tienen desempate explícito. Los CSV finales no conservan id_sensor/id_dato/modelo ni motivo de descarte. No se sabe si existen estas colisiones en los datos reales. E01 L134–153/L209–244; E04 L77–96; encabezados E01 L29–45/E04 L14.
3. **Faltantes y calidad heterogéneos.** Aire solo convierte -1 a vacío y no comprueba finitud/rangos; agua descarta no finitos y rangos por modelo, omitiendo filas enteramente rechazadas. Ambos pierden distinción entre ausencia, sentinela, rechazo y sensor no instalado en la salida ancha. Los límites de clean son decisiones programadas, sin respaldo metrológico evaluado aquí. E01 L234–244; E04 L61–75/L94–105. No se midió cantidad de rechazos.
4. **Tiempo ambiguo.** Las consultas construyen límites sin zona explícita; la serialización histórica usa isoformat de lo devuelto por BD y el manifiesto declara America/Santiago. No se convierte ni valida allí la zona de cada registro. Aire convierte latest_time con astimezone; agua guarda updated_at como máximo textual de latest. Por ello, la declaración de zona no acredita resolución de horas repetidas/inexistentes por cambio horario. E01 L116–122/L263/L377–380/L453–457; E04 L56–59/L105/L130–136. Falta conocer tipos/convención de BD y TZ del entorno.
5. **Publicación por archivo ≠ instantánea coherente.** Aire reemplaza cada parte, latest y manifiesto en pasos separados; agua reemplaza histórico pero escribe latest y manifest directamente. Una interrupción puede dejar generaciones mezcladas o archivos incompletos según el punto. Aire configura autocommit=True; no se observa un corte global de extracción. El esquema de publicación/lector externo no fue leído. E01 L261–295/L347–389/L423–424; E04 L102–107/L133–136. No se ensayaron fallos.
6. **Tope y vacíos deben precisarse.** Aire comprueba MAX_FILE_BYTES después de escribir cada fila: el algoritmo puede exceder el umbral en el tamaño de esa fila y abrir una parte adicional solo con cabecera. Cuando no hay mediciones mantiene CSV con cabecera; agua elimina part-001 vacío. La prueba de aire exige tamaño ≤max, pero no fuerza la frontera con fixtures. E01 L255–285; E04 L98–101; E02 L56–75. Esto matiza la garantía documental previa de P02: no se comprobó ningún fichero sobredimensionado real.
7. **Portabilidad de salida acotada.** Ambos construyen rutas del manifiesto con relative_to(ROOT), aunque aceptan salida por argumento. Una salida absoluta fuera de ROOT no satisface esa operación cuando hay archivos. E01 L369–374/L397; E04 L111/L120/L125. Un futuro banco de pruebas debe aislar ROOT o desacoplar la raíz lógica, sin apuntar al publicador real.

## Pruebas existentes: qué comprueban y qué queda abierto

**Observado directamente:** E02 define cuatro métodos test_: límites de diciembre, enumeración de meses, configuración Viña Errázuriz y consistencia de archivos publicados. Esta última verifica códigos, archivos existentes, tamaño máximo, cabecera exacta, mes textual, orden no decreciente y algunos códigos de latest (L20–83). Orden no decreciente permite timestamps repetidos. No comprueba valores contra datos de origen.

**Observado directamente:** E05 define tres métodos test_: mapeo de modelos, ocho ejemplos de limpieza y contrato publicado. Comprueba versión, conjunto esperado de estaciones, meses desde 2025, ficheros no vacíos y datos de profundidad/distancia en LVAG (L8–49). La comprobación set(rows[0]).issubset(HEADER) admite columnas faltantes; no exige igualdad de cabecera. No comprueba orden temporal ni valores contra origen.

**Límite:** no se ejecutó ninguno de estos siete métodos ni se inspeccionaron sus archivos de datos. La lectura no muestra pruebas para paginación completa, escalado SO₂, colisiones, no finitos de aire, desempate, DST, pérdida de latest al cambio de mes, escritura interrumpida o igualdad byte a byte entre repeticiones. Esta ausencia se refiere exclusivamente a los dos archivos de pruebas leídos; no afirma ausencia global de CI u otras pruebas.

## Contrato candidato para revisar — cmas-env-export/0.1-draft

Todo este apartado es **propuesta**, todavía sin implementar ni aprobar. No reutilizar schema_version=1 como garantía de compatibilidad entre proyectos: hoy tienen esquemas/semánticas diferentes.

| Parte | Regla propuesta y aceptación medible |
| --- | --- |
| Identidad | dataset_id + station_id estables y variable_id canónico. Perfil declara vínculo temporal con dispositivo/sensor y modelos; resolver sustituciones mediante vigencias. Alias de UI y nombre de columna se mapean explícitamente al mismo variable_id |
| Variables | Diccionario por variable con magnitud, unidad de origen y destino, multiplicador/transformación, precisión de salida y rol ambiental/diagnóstico. Cada transformación lleva versión y prueba de pares entrada→salida. No tratar CSQ como magnitud ambiental ni definir unidades por el sufijo únicamente |
| Tiempo | Documentar semántica/tipo de fecha de origen, TZ y resolución antes de convertir. Observación exportable incluye timestamp inequívoco (UTC con Z u offset). Preservar fecha original y política DST en trazabilidad autorizada. Intervalos mensuales se definen en zona explícita y se prueban al cambio de año y hora |
| Observación lógica | Clave source_record_id o combinación inequívoca documentada; station_id, sensor_id lógico, variable_id, observed_at, valor y estado. Mantener evidencia de origen en artefacto autorizado o catálogo, sin exponer IDs internos si no procede. No inventar identificadores de registros eliminados del histórico existente |
| Ausencia/calidad | value=null + estado entre missing/sentinel/rejected/valid; regla y versión con motivo. Distinguir no instalado de no leído; no rellenar con cero. CSV ancho puede seguir como vista derivada, acompañado de reporte de QA o tabla de estados; no inferir motivo a partir de un vacío antiguo |
| Colisiones | Definir política explícita antes de ensanchar: conservar observaciones separadas o seleccionar por fuente priorizada y desempate total; contar y reportar descartes. Ninguna sobrescritura silenciosa. No promediar automáticamente |
| Histórico | CSV UTF-8/LF, cabecera exacta del perfil, orden total estable, mes [inicio, fin), semántica de mes vacío explícita; station_id en manifiesto/ruta. Si se exige tope duro, comprobar bytes antes de escribir la fila; evitar partes vacías. Registrar filas, bytes y hash por parte |
| latest | Una fila por station_id/variable_id después de resolver fuentes; mayor observed_at válido respecto al corte global, conservando estado de antigüedad. Política de máximo retroceso explícita. No equiparar latest con todas las variables de un mismo instante; separar missing de stale |
| Manifiesto/procedencia | contract_id/version y profile/version; dataset_id, generation_id, generated_at y observed_through distintos; zona, diccionario, estaciones, particiones, hashes, conteos, rango temporal, versión de exportador y referencia de instantánea autorizada. Licencia/responsable por resolver, nunca inventados |
| Publicación | Generar todo en staging, validar referencias/hashes y conmutar una generación completa. Recuperar la anterior ante fallo; mismo origen+corte+perfil produce mismos archivos de datos. Timestamps operativos del manifiesto se comparan con política explícita, no confundirlos con bytes del dataset |

Migración candidata: dos adaptadores fuente→observaciones lógicas; motor común opcional de particiones/QA/manifiesto; vistas de compatibilidad que mantengan columnas existentes. La conveniencia de motor común se decide tras prototipo y medición. AireAysen y SensorsWebApp quedan fuera de la equivalencia demostrada: requerirán contratos fuente/API propios.

## Próximos pasos medibles y decisión

1. **Cerrar cuatro decisiones con responsables de datos/operación:** semántica de timestamps, regla de colisión, alcance de latest y fundamento/versión de filtros. Entrega: tabla de decisiones con responsable, fuente y ejemplos, sin consultar credenciales ni modificar datos.
2. **Crear un banco offline autorizado y reproducible:** fijar commits y dependencias; usar fixtures sintéticos, sin BD, con cursores simulados. Incluir al menos 12 escenarios: mes vacío, cambio de mes, 29 de febrero, diciembre, DST ambiguo, -1, no finitos, límites de clean, SO₂×1000, colisión de sensores, empate de registros y más de 5.000 registros. Añadir frontera de partición e interrupción como dos escenarios de publicación. Esta es propuesta futura; aquí no se crearon tests.
3. **Comparar baseline y contrato:** para cada fixture, enumerar entradas, salidas y descartes; exigir 100% de observaciones contabilizadas y ninguna pérdida/sobrescritura sin política. Exigir hashes de datos idénticos en dos ejecuciones equivalentes; recuperación sin manifiesto que apunte a archivos incompletos ante fallos inyectados. Medir memoria/tiempo solo como rendimiento del banco, sin extrapolar a producción.
4. **Validar una muestra real autorizada por perfil:** un sensor y un período por repositorio, con corte e identificadores auditables; conteos fuente→exportación y revisión de cada rechazo. Sin muestra, solo puede afirmarse corrección sobre fixtures. Registrar licencias, contribuciones y permiso de reutilización antes de redistribuir.
5. **Elegir alcance publicable después de revisión bibliográfica primaria:** si contrato y adaptadores permiten reconstruir ambos casos y se evalúa su costo/beneficio, avanzar software/métodos; si solo se documentan divergencias, caso técnico comparado. Métricas futuras: pérdidas no explicadas, colisiones resueltas, precisión de transformaciones, integridad tras fallo, latencia desde corte a artefacto y esfuerzo de configurar un nuevo perfil.

No hay bloqueo de acceso para esta lectura. Las conclusiones de reproducibilidad real quedan pendientes de datos autorizados, entorno fijado y revisión especializada. La novedad y el destino editorial permanecen sin determinar.

## Verificación y criterios de aceptación

Acciones ejecutadas: cat de documentos locales/plantillas, git status --short; dos llamadas GitHub fetch a árboles; seis llamadas a blobs exactos; lectura y numeración del contenido en memoria. Todos los accesos devolvieron contenido, sin reintentos fallidos. No se ejecutaron tests fuente ni importaron módulos, leyeron .env, conectaron servicios o consultaron mediciones. La validación local de entrega solo comprueba JSON y presencia de los dos artefactos.

| Criterio | Resultado |
| --- | --- |
| Dos exportadores, esquemas/configuración y pruebas | Cumple: seis archivos completos; esquemas observados en constructores, no manifiestos/datasets leídos |
| Versiones fijadas y afirmaciones trazables | Cumple mediante blobs, árboles y líneas; commits/despliegues pendientes |
| Distinguir compartido/específico y proponer contrato A | Cumple como lectura estática y propuesta explícita |
| Funcionamiento, integridad fuente→CSV y resultados científicos | Pendientes; no simulados ni declarados aprobados |
| Alcance de escritura | Solo resultados/V02/informe.md y evidencias.json; sin commit ni backlog |

**Estado solicitado: en_revision.**
