# Entrega T02 — Ficha documental voluntariosxagua

- Objetivo: inventario documental acotado; responsable: agente ejecutor `gpt-6.1-sol`, sin subdelegación.
- Fecha: 2026-11-11. Estado solicitado: **en_revision**.
- Fuente local de solo lectura: `/home/ale/Documents/repos/voluntariosxagua`, HEAD `2e08e016df32e8f8b765af5f20abdde0308c0b13`; coincide con E004 de la revisión inicial. Árbol Git limpio antes y después de inspección [T02-E01].
- Entradas del plan: AGENTS.md, README, revisión inicial, plan por fases, T00, backlog T02, inventarios y plantillas; versiones por hash en `evidencias.json` [T02-E10]. T00 aceptada por coordinador.
- Permisos: lectura de repositorio y documentación local; escritura exclusivamente en `resultados/T02/`. No se hicieron solicitudes remotas.
- Artefactos: `informe.md`, `ficha.md`, `evidencias.json`.

## Hallazgos

Los identificadores enlazan entradas de [evidencias.json](evidencias.json), con fuente, localizador y versión. “Observado” significa lectura directa del artefacto o metadato; no implica ejecución de la web ni validación científica.

| Afirmación | Tipo | Evidencia y localizador | Límite |
| --- | --- | --- | --- |
| El propósito es consultar y descargar mediciones mensuales ciudadanas de ríos del Cajón del Maipo, reemplazando la consulta previa en ArcGIS. | Declarado por documentación | T02-E02, README:5–19 | No se verificó el sistema anterior ni la operación mensual. |
| Existen código de web estática, conversor XLSX/fotos y workflow orientado a GitHub Pages. | Observado directamente | T02-E03, `scripts/build_site_data.py`:13–58,97–163,166–216; T02-E04, workflow:3–44; T02-E05, app:20–37,68–140,143–210,245–273,287–308 | Lectura de código; no se ejecutaron generador, web o Actions. No confirma despliegue público. |
| La planilla tiene siete hojas con los nombres que espera el conversor; las filas 1–2 contienen encabezados de fecha y parámetros. | Observado directamente | T02-E06, XLSX `xl/workbook.xml`, `xl/worksheets/sheet1.xml` a `sheet7.xml`, filas 1–2 | Inspección de estructura; no auditoría completa del XLSX ni comparación fila a fila con JSON. |
| Hay un JSON local ignorado por Git con 7 estaciones, 9 parámetros y 394 registros; cada estación tiene fechas extremas 2022-04-03 y 2026-11-01. | Observado directamente | T02-E07, `docs/data/measurements.json`, claves `stations`, `parameters`, `records`; resumen abajo | No atribuir al commit: el JSON no está versionado. No se regeneró ni verificó correspondencia con XLSX. Fechas extremas no prueban continuidad. |
| El JSON conserva valores nulos y repetición de claves estación-fecha en El Manzano/Colorado. | Observado directamente | T02-E07, `records`, filtro `stationId=manzano-colorado`, agrupación por `date` | Hay 59 registros y 56 fechas distintas para esa estación. No se decide si son réplicas, duplicados o errores. |
| Las coordenadas de referencia están compartidas por pares de estaciones del mismo sector. | Observado directamente | T02-E03, conversor:25–33; T02-E05, app:143–149 | No son ubicaciones validadas de muestreo. El mapa agrupa por sector. |
| El documento distingue “Coordenadas de los puntos” de “Puntos de encuentro”; los valores geográficos de estos últimos coinciden numéricamente con los del conversor. | Observado directamente | T02-E08, DOCX `word/document.xml`, párrafos 44–55 y 82–86; T02-E03:25–33 | Coincidencia documental; no implica exactitud ni transformación UTM validada. |
| El README advierte coordenadas UTM ambiguas/repetidas y pide confirmar sistema de referencia, ubicaciones, unidades y cobertura. | Declarado por documentación | T02-E02, README:113–115,148–171 | T02 mantiene estas decisiones pendientes. |
| El origen local apunta a `AleReb/voluntariosxagua`; el inventario previo registra además `cmasudd/voluntariosxagua`. | Observado local + declarado por inventario | T02-E01, `git remote -v`; T02-E09, inventario:67–70 | No se compararon remotos, commits, forks, ramas ni despliegues. Canónico y equivalencia pendientes. |
| El usuario declara haber creado las webs de cmasudd. | Declarado por usuario, recogido en documentación del plan | T02-E09, campo `attribution`; revisión inicial E010 | Sin desglose por proyecto, colaboradores ni autoría exclusiva. El metadato de autor de HEAD tampoco resuelve estos puntos. |
| No se encontró archivo rastreado con nombre LICENSE o COPYING mediante patrones Git. | Observado directamente | T02-E11, `git ls-files '*LICENSE*' '*COPYING*'` sin salida | No es auditoría legal exhaustiva. Atribución solicitada por README no equivale a licencia abierta. |

### Estructura observada del JSON existente

Inspección descriptiva de archivo local, sin calcular estadísticas de calidad del agua ni limpiar datos [T02-E07]. El rango es idéntico en las siete estaciones: 2022-04-03 a 2026-11-01.

| `stationId` | Registros | Fechas distintas |
| --- | ---: | ---: |
| `banos-morales-estero` | 56 | 56 |
| `banos-morales-volcan` | 56 | 56 |
| `canelo-maipo` | 55 | 55 |
| `manzano-colorado` | 59 | 56 |
| `manzano-maipo` | 56 | 56 |
| `san-gabriel-maipo` | 56 | 56 |
| `san-gabriel-yeso` | 56 | 56 |

Las unidades del conversor/JSON son °C, pH sin unidad, conductividad µS/cm, sólidos disueltos/salinidad/dureza ppm, ORP mV, alcalinidad sin unidad y turbidez NTU [T02-E03:35–45; T02-E07 `parameters`]. Son etiquetas observadas, no unidades confirmadas del método de laboratorio/campo. En el XLSX la columna J dice “alcalinidad” sin unidad y la columna I de la séptima hoja usa “Turb” [T02-E06]. Falta revisar el significado de blancos y ceros, calibraciones, unidades efectivas, trazabilidad KoboCollect→XLSX, réplicas y criterios de validación.

### Coordenadas y mapa

En el DOCX el par de coordenadas UTM de El Manzano/Maipo se repite en Colorado (p48–49); Canelo incluye una cadena numérica prefijada (p46) y Estero Morales contiene `401513.1m1 E` (p55) [T02-E08]. Estos son problemas de texto observados, no correcciones propuestas. Se requiere confirmar datum, huso, hemisferio, formatos y un par de coordenadas por estación con responsable de terreno. Los párrafos 82–86 dicen “Puntos de encuentro”; el conversor usa esos cuatro pares geográficos como referencia por sector [T02-E08; T02-E03]. No se debe transformar o deducir automáticamente la ubicación exacta de las siete estaciones.

## Verificación

Comandos ejecutados en fuente, todos de lectura:

- `git rev-parse HEAD`, `git status --short`, `git status --porcelain=v1`, `git remote -v`, `git log -1 --format=fuller`: HEAD y origen fijados; status sin salida. No se copian correos del historial.
- `find .. -name AGENTS.md -print` y `find . -maxdepth 3 -type f -not -path './.git/*' -print`: inventario de rutas; no apareció AGENTS.md dentro de la fuente. No se abrieron imágenes.
- `nl -ba README.md`, lecturas acotadas con `nl`/`head`/`tail` del conversor, app, workflow, `.gitignore` y `antecedentes.txt`: comportamiento documentado/código descrito arriba. El texto de antecedentes no se toma como prueba de autoría exclusiva ni se copian datos personales.
- `git ls-files docs/data site/data` no devuelve archivos; `.gitignore`:1–6 los excluye. `git ls-files` confirma que XLSX, DOCX, README, conversor, app y workflow están rastreados. `git rev-parse HEAD:<ruta>` fija blobs de los cuatro archivos de texto principales [T02-E01,03–05].
- `sha256sum` de fuentes listadas y `hashlib.sha256` de DOCX: valores en manifiesto. No se copian originales a la entrega.
- Python estándar `zipfile` + `xml.etree.ElementTree`: lectura directa de `xl/workbook.xml` y siete XML de hojas (solo filas 1–2); lectura DOCX de párrafos relativos a coordenadas y puntos de encuentro. Localizador DOCX: índice desde 1 de todos los elementos `w:p` en orden de `word/document.xml`, usando `findall('.//{http://schemas.openxmlformats.org/wordprocessingml/2006/main}p')` y concatenación `itertext()`.
- Python `json.load` + `Counter`: lectura de claves, conteo de estaciones/parámetros/registros/fotos, fechas extremas y claves estación-fecha del JSON existente. Se detectaron nulos; no se interpretaron como observaciones válidas. No se hizo análisis estadístico de valores de agua.
- `rg` no está instalado (`command not found`); se usaron `find`, Python y lecturas acotadas.

Para reproducir el resumen del JSON sin ejecutar código fuente:

```python
import json
from pathlib import Path
p = Path('/home/ale/Documents/repos/voluntariosxagua/docs/data/measurements.json')
x = json.loads(p.read_text())
print(len(x['stations']), len(x['parameters']), len(x['records']))
for s in x['stations']:
    dates = [r['date'] for r in x['records'] if r['stationId'] == s['id']]
    print(s['id'], len(dates), len(set(dates)), min(dates), max(dates))
```

No ejecutado: generador (escribe/borraría fotos de salida), servidor local, navegador, Actions, descargas web, comparación remota AleReb/cmasudd, inspección de datos de participantes o análisis de mediciones. No se afirmó prueba aprobada ni validación científica.

## Criterios de aceptación

| Criterio | Cumple/no cumple/pendiente | Evidencia |
| --- | --- | --- |
| Citar commit y fuentes | Cumple documentalmente | T02-E01–11; commit y hashes diferenciados para archivos ignorados |
| Relacionar versiones AleReb/cmasudd sin asumir equivalencia | Cumple documentalmente; comparación pendiente | Origen local más inventario previo; canónico, historia y despliegue sin resolver |
| Registrar datos y coordenadas pendientes | Cumple | Brechas explícitas y fuentes de XLSX/DOCX/JSON/código |

## Faltantes y siguiente paso

Proponer a T03 comparar de forma acotada los remotos AleReb/cmasudd, identificar canónico, ramas, contribuciones y URL de despliegue. T04 deberá comprobar publicación y flujos en navegador. Antes de usar el conjunto en investigación se necesita una tarea autorizada de auditoría XLSX↔JSON, diccionario de datos, tratamiento de nulos/réplicas, metadatos de instrumentos/calibración y coordenadas confirmadas por estación. Obtener permisos de uso por artefacto y contribuciones de Alejandro/equipo. No bloquea la entrega documental; sí condiciona afirmaciones de publicación, exactitud geográfica y validez de mediciones.

No se modifica backlog, inventarios ni fuentes y no se hace commit. Entrega propuesta al coordinador: **en_revision**, sin autoaceptación.

Nota operativa: la escritura inicial de los dos Markdown omitió el directorio de trabajo y creó temporalmente `/home/ale/resultados/T02/`. Se trasladaron inmediatamente al destino autorizado y se eliminaron los directorios temporales vacíos. No quedaron entregas fuera de `resultados/T02/`; no se alteró el repositorio fuente. El manifiesto JSON se escribió directamente en el destino correcto y se validó su carga con 11 entradas.
