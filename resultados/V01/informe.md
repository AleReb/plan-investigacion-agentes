# V01 — Viabilidad de la propuesta B: evaluación de aire

- **Estado: en_revision.** Fecha: 2026-11-12. Ejecutor: gpt-6.1-sol según asignación del coordinador.
- Objetivo: leer dos informes representativos y determinar qué evidencia recuperable aportan a la propuesta B del panorama general; no evaluar todas las variantes HIRI ni seleccionar una publicación principal.
- Fuente pública de solo lectura: AleReb/estacion-calidad-aire, rama main resuelta a commit **`40a9b429aa90c89caf567844cf157dd872c65cdf`**. Sin acceso a producción, compilación, carga o ensayos físicos.
- Artefactos: este informe y [evidencias.json](evidencias.json). Los PDF descargados y textos derivados quedan exclusivamente en `/tmp/v01-aire/`, sin versionarlos: `laboratorio.pdf`, `laboratorio.txt`, `campo.pdf`, `campo.txt`; figuras `campo-p2.png`, `campo-p3.png`, `campo-p9.png`. Son temporales y pueden expirar.

## Decisión de viabilidad

**Propuesta B viable de forma condicionada para recuperar y evaluar evidencia; todavía no viable como análisis reproducible con los materiales localizados.** Hay una campaña identificable, comparación contra SINCA y un ensayo electrónico con mediciones tabuladas. No son solo títulos. Pero no se localizaron series originales ni código de análisis en esta revisión del árbol; los informes no permiten reconstruir selección de registros, sincronización, calibración y evaluación [V01-E02–E08].

La contribución candidata puede precisarse como **comparar calibración de laboratorio y ajuste por bandas térmicas en una configuración de cinco módulos co-ubicados**, documentando aciertos y límites por contaminante. Es una propuesta, sin novedad establecida. No sostener aún afirmaciones de error, deriva, completitud de una red ni generalización a HIRI o todas las webs: requieren series, identificación y análisis adicional. La evidencia es más concreta que la disponible en P01, pero su prioridad frente a A/C debe decidirse después de contrastar V02/V03.

## Fuentes fijadas y lectura efectuada

| ID | Artefacto leído | Versión e integridad | Alcance |
| --- | --- | --- | --- |
| V01-E01 | [Commit y árbol Git][commit] | commit arriba; árbol `5679b150875ad978a72e559aa3bb4e500ad88804`, respuesta recursiva `truncated=false` | Metadatos; nombres/tamaños, no lectura indiscriminada del repositorio |
| V01-E02–E04 | [Calibración SINCA-Temperatura][campo] | PDF 10 páginas; blob `5ab171004a86cec6d3f82e7100046c1b86865e63`; SHA-256 `cbcc1b0afbce0d469b1ef7dbbb326b628bf2cd586a939ea14460d29ad9444eda` | Texto completo y figuras seleccionadas de páginas 2, 3 y 9 |
| V01-E05–E07 | [Offset electrónico Estación 5][lab] | PDF 6 páginas; blob `b3f2445c6da80c84d5926b9fed8f60f04df95491`; SHA-256 `84ba44b86804b37da9acd7383e8e1f406f9fe55eedbae75a084e571f3b77f72a` | Texto completo y tablas extraídas; fuente LaTeX leída por conector, blob `253d0d3ae892d83dbea5a45c1cee3a0d6a33db1b` |

Hashes Git blob de ambos PDF recalculados a partir de bytes y coincidentes con el árbol. Fechas de consulta: 2026-11-12. Páginas = orden físico del PDF. Las cifras siguientes son **declaradas por los informes / observadas en sus tablas o figuras**, nunca mediciones ejecutadas por el agente.

## Campaña de campo: lo que contiene realmente

| Aspecto | Hallazgo y localizador | Límite |
| --- | --- | --- |
| Sitio y período | SINCA **Las Condes**, datos entre **11 y 28 octubre 2025**, cinco de seis estaciones de Líneas de Base Públicas; p.1 [E02] | La cabecera dice viernes 17/10/2025 11:16, anterior al fin del período. Aclarar versión/fechas, sin descartar la campaña por esa discrepancia |
| Módulos | Figuras inspeccionadas identifican **Módulo 2, 3, 4, 5 y 6**; pp.2–3 y 9 [E03] | No hay seriales ni asociación inequívoca con PCB/firmware; las tablas de laboratorio incluyen seis sensores |
| Variables anunciadas | Señales crudas Alphasense de NO, NO₂, SO₂, CO y O₃; temperatura de SINCA como estratificador; p.1 [E02] | El desarrollo presenta NO-B4, NO₂-B43F, OX-B431 y CO-B4; **no hay sección de resultados SO₂** en las diez páginas |
| Referencia | Concentraciones y temperatura de la estación SINCA nombrada; p.1 [E02] | Sin modelo/serial de analizadores, QA/QC de referencia, fichero fuente, versión descargada o resolución temporal explicitados |
| Comparadores | Conversión con parámetros de laboratorio frente a RLS por temperatura; tablas 1–4 y pp.1–10 [E02,E04] | Las tablas de parámetros y sus R² no acreditan por sí solas exactitud en campo; no se recuperaron sus ensayos originales |
| Ajuste/evaluación | Declara **80% ajuste y 20% prueba**, tres regresiones por sensor: <10 °C, 10–20 °C y >20 °C; p.1 [E02] | Sin regla de partición/semilla, número de pares por banda, tratamiento de autocorrelación/faltantes ni separación temporal reproducible. Las figuras de regresión rotulan banda alta 20–30 °C (p.2); aclarar cobertura y fronteras |
| Qué muestran las figuras | En NO, Pearson mostrado para módulos 2–6: antes **0,29 / 0,25 / 0,20 / 0,30 / 0,22**; después **0,56 / 0,54 / 0,55 / 0,61 / 0,57**; pp.2–3 [E03] | Transcripción visual, no recálculo. El tramo de prueba mostrado va aproximadamente del 11/10 al mediodía del 14/10; no basta para reconstruir el split |
| Resultado declarado | Texto reporta mejora de correlaciones NO, NO₂ y OX; CO empeora/no mejora; pp.3,5,7,9–10 [E04]. Figura CO posterior muestra Pearson 0,28–0,32, p.9 [E03] | No convertir correlación en precisión, sesgo o incertidumbre. No se calcularon RMSE/MAE, deriva o completitud |

El informe dice que las concentraciones Alphasense no llevan corrección por temperatura/humedad/otro factor, mientras describe un ajuste **estratificado por temperatura** (p.1). Es necesario aclarar a qué etapa aplica esa frase; no inferir que todo el pipeline carece de uso de temperatura. Errores textuales llaman a NO-B4 “Monóxido de Carbono” y a NO₂-B43F “Dióxido de Carbono” (pp.1 y 3): conservar nombres de sensor/variable y pedir corrección al responsable, sin reinterpretar datos [E02,E04].

## Laboratorio: ensayo electrónico, no referencia de concentración

**Campaña declarada:** 11/11/2025, 10:00–13:52, Laboratorio de Electrónica C+ UDD Santiago, Estación 5, proyecto Línea base pública para la región metropolitana. Responsable Luis Gómez; Alejandro Rebolledo figura como revisor, no como autor único del ensayo (p.1) [E05].

**Objeto y procedimiento:** cinco placas ISB DBI01–DBI05, sin sensor B4 conectado, señales OP1/WE y OP2/Aux, alimentación declarada 3,5–6,5 VDC. Equipos: Power Profile Kit II, multímetro Keysight 34461A y osciloscopio GW Instek GDS-12028. Describe extracción de sensor, cableado y lectura con ambos instrumentos (pp.1–3) [E05].

**Datos presentes:** tablas p.4 con dos valores por placa/instrumento. A modo de ejemplos verificables, DBI01 asociada a CO: multímetro 352/341 mV frente a osciloscopio 375/370 mV; DBI05 asociada a SO₂: 354/359 frente a 384/397 mV. Hay diez valores por instrumento, no una serie temporal de réplicas. El texto introductorio de tabla 1 dice “osciloscopio”, pero título y caption dicen multímetro: discrepancia editorial que debe resolverse [E06].

**Referencias citadas, no verificadas externamente:** manual Alphasense ISB Issue 7/doc.085-2217, AAN803-05 y especificaciones B4, junto con manuales de equipos (pp.5–6). No equivalen a certificados de calibración o trazabilidad de los instrumentos utilizados [E07]. El informe recomienda el multímetro para offsets y propone muestreo prolongado/desviación estándar, control de temperatura y conservar pares placa-sensor (p.5). Sus explicaciones de diferencias entre instrumentos y afirmación de normalidad son conclusiones de los autores, no mecanismos demostrados por V01.

La fecha del ensayo es posterior a la campaña de octubre. **No se ha demostrado** que estos offsets fueran los parámetros usados en la comparación de campo, ni que DBI01–05 correspondan uno a uno a módulos 2–6. El ensayo sin sensor no mide por sí mismo sensibilidad a gases, interferencias, exactitud de concentración o deriva de una red [inferencia limitada E09].

## Datos originales y reproducibilidad

Observación directa del árbol recursivo al commit fijado [E08]:

- En `datos/` hay **12 archivos, todos `.gitkeep` de cero bytes**, repartidos en mediciones brutas, referencias, procesados y validación, incluida `datos/datos-validacion/conjuntos-datos-co-ubicacion/`.
- La búsqueda por extensiones `.csv`, `.xls`, `.xlsx`, `.json`, `.jsonl`, `.parquet`, `.r`, `.py`, `.ipynb` no devolvió archivos en todo ese árbol. Esta consulta no detectaría datos escondidos en otros formatos o en sistemas externos.
- La carpeta del informe de campo contiene el PDF y `.gitkeep`; la del laboratorio incluye PDF, LaTeX e imágenes. LaTeX contiene las tablas pero no las señales instrumentales originales. No se leyeron informes adicionales.

Por tanto: **hay valores numéricos y gráficos derivados en documentos; no hay datos crudos de campaña recuperados por V01**. No concluir que fueron eliminados o que no existen fuera del repositorio. Tampoco considerar una digitalización de gráficos como sustituto de los archivos originales.

## Faltantes, decisión y siguiente paso concreto

Propuesta de recuperación documental al coordinador, para dirigir al responsable sin enviar mensajes desde V01:

1. Solicitar copia de trabajo de la campaña 11–28/10/2025: timestamps y zona horaria; módulos/seriales; WE/AE/raw y unidades; concentraciones originales; temperatura/humedad; flags y faltantes; referencia SINCA usada y procedencia.
2. Recuperar notebook/script o planilla que genera tablas/figuras, parámetros previos y ajustados, fórmula aplicada, identificación de los registros del 80/20 y conteos por banda. Confirmar si “prueba” fue temporalmente independiente y cómo se sincronizaron las series.
3. Unir campaña↔sensor/ISB↔placa↔firmware/commit, registro de mantenimiento y calibración; aclarar la relación con ensayo noviembre y discrepancias editoriales. Solicitar bitácoras del multímetro/osciloscopio, alimentación/temperatura exactas y certificados si existen.
4. Confirmar responsables de datos, contribuciones de equipo y permiso para análisis/publicación. V01 no resuelve autorías, licencias ni permiso de publicar.

**Puerta propuesta:** continuar B como evaluación instrumental si se recuperan pares originales y un pipeline reconstruible para una configuración; después revisión bibliográfica y protocolo de análisis con referencia/comparadores explícitos. Si solo quedan estos PDF, reformular a memoria o nota técnica de procedimiento y límites, o preparar nueva campaña con protocolo autorizado; no fabricar series ni redactar resultados de precisión. La evidencia actual no permite escoger B definitivamente por encima de A/C.

## Verificación, comandos y límites

Lecturas de control: `cat AGENTS.md CONTINUAR.md resultados/P03/informe.md`, README, PROPUESTAS_PUBLICACIONES y plantillas. Conector GitHub primero: descubrimiento por `ALL_TOOLS`; GET commit main; GET árbol `...?recursive=1`; `fetch_file` del `.tex` del mismo informe al commit fijado. La respuesta del árbol fue completa, no truncada; se filtró por rutas y extensiones para evitar volcados innecesarios.

El conector `fetch` declara rechazo de binarios/no UTF-8. Se usó la alternativa autorizada para ambos PDF: Python `urllib.request.urlopen` sobre URL raw pública **fijada a commit**, descarga en `/tmp/v01-aire/`, SHA-256, `pdfinfo`, `pdftotext -layout`; lectura de las **16 páginas** extraídas separadas por form-feed. `pdftoppm` renderizó páginas físicas 2,3,9 del PDF de campo a PNG (1800 px), inspeccionadas con `view_image` porque sus métricas forman parte de imágenes no extraídas como texto. No se digitalizaron puntos ni se recalcularon estadísticas. No hubo accesos fallidos/reintentos; no se pidió PDF binario al conector tras conocer esa limitación.

Se recalcularon hashes Git blob mediante SHA1 de cabecera `blob <bytes>\0` y bytes; ambos coinciden. El PDF laboratorio tiene 19.873.794 bytes; campo 2.801.298 bytes. Metadatos PDF: laboratorio creado 17/11/2025, campo 04/11/2025; son fechas de archivo, no fechas de ensayo [E10]. Se validó JSON con `python3 -m json.tool`. No se ejecutaron tests de firmware, consulta de datos de producción o ensayos físicos porque V01 es documental. No se modificaron fuentes, backlog ni inventarios; no se hizo commit.

## Criterios de aceptación

| Criterio | Estado | Evidencia |
| --- | --- | --- |
| Recuperar y leer dos informes representativos | Cumple documentalmente | 6+10 páginas, hashes y localizadores E02–E07 |
| Identificar campañas, variables, referencia y datos crudos | Cumple con faltantes explícitos | Tablas anteriores y árbol E08; originales no recuperados |
| Decidir viabilidad B dentro del panorama general | Cumple como propuesta condicionada | Decisión inicial y puerta de recuperación; sin selección científica final |
| Solo lectura y escritura en resultados/V01 | Cumple para repositorios | Derivados temporales en /tmp según autorización; ninguna fuente editada |

Estado solicitado: **en_revision**; aceptación reservada al coordinador.

[commit]: https://github.com/AleReb/estacion-calidad-aire/commit/40a9b429aa90c89caf567844cf157dd872c65cdf
[campo]: https://github.com/AleReb/estacion-calidad-aire/blob/40a9b429aa90c89caf567844cf157dd872c65cdf/documentacion/informes-pruebas/campo/co-ubicacion-sinca/calibracion-sinca-1.pdf
[lab]: https://github.com/AleReb/estacion-calidad-aire/blob/40a9b429aa90c89caf567844cf157dd872c65cdf/documentacion/informes-pruebas/laboratorio/condiciones-controladas/Volt_Circuito_abierto_ISB_alphasense_est05/Voltage_circuito_abierto_alphasense_estacion_5.pdf
