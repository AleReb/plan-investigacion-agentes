# V03 — Procedencia acotada y viabilidad de propuesta C

- Estado solicitado: **en_revision**. Fecha: 2026-11-12. Ejecutor: `gpt-6.1-sol`, sin subdelegación.
- Objetivo: reconciliar historias AleReb/cmasudd de voluntariosxagua y auditar una estación/período XLSX→JSON local.
- Fuente local de solo lectura: `/home/ale/Documents/repos/voluntariosxagua`, HEAD `2e08e016df32e8f8b765af5f20abdde0308c0b13`. Árbol limpio al inicio y al finalizar [V03-E01].
- Entradas: AGENTS/README/CONTINUAR, informe P03, propuesta C y plantillas. Hashes en [evidencias.json](evidencias.json), V03-E09. Presupuesto orientativo autorizado: 8000 tokens/30 min; máximo dos intentos por acceso. No hubo reintentos remotos.
- Artefactos: este informe y `evidencias.json`. Solo se escribe en `resultados/V03/`; sin commit, cambio de backlog, mediciones o fuentes.

## Resultado y alcance

**Observado:** los repositorios remotos comparten historia y los cambios de cmasudd están integrados en AleReb. Sus extremos tienen commits distintos; GitHub no reporta diferencias de archivos al compararlos. El checkout local conserva una versión anterior. **Observado:** en Canelo, abril-junio de 2022, coinciden tres fechas y los 27 campos de medición entre XLSX y JSON local (18 numéricos y 9 vacíos→null), sin emparejamientos ambiguos ni registros adicionales en ese período [V03-E01–07].

**Inferencia:** la propuesta C puede avanzar como protocolo de trazabilidad y curación sobre una muestra recuperable. No está listo un descriptor del conjunto completo: siguen pendientes responsable de datos, permisos, origen previo al XLSX, diccionario, QA/QC y coordenadas. La coincidencia puntual no prueba exactitud instrumental, procedencia original o novedad [V03-E08].

## Reconciliación remota

Consultas de lectura con conector GitHub: `get_repo`, `search_branches(main)`, `fetch_commit(main)` y `compare_commits`. Dos IDs de repositorio: AleReb `1453282587`, cmasudd `1453371614`; ambos tienen rama predeterminada main y visibilidad pública. Esos metadatos no exponen fork/parent: la relación formal de fork queda sin determinar [V03-E02].

| Versión | SHA fijado | Evidencia |
| --- | --- | --- |
| Checkout local | `2e08e016df32e8f8b765af5f20abdde0308c0b13` | V03-E01 |
| AleReb/main remoto | `1f3dcbeb5bda77209deb0660123f463a6d78cdd9` | [commit remoto](https://github.com/AleReb/voluntariosxagua/commit/1f3dcbeb5bda77209deb0660123f463a6d78cdd9), V03-E03 |
| cmasudd/main remoto | `ec04425e03129bfbb7f35dd65dc176cf69d45723` | [commit remoto](https://github.com/cmasudd/voluntariosxagua/commit/ec04425e03129bfbb7f35dd65dc176cf69d45723), V03-E03 |

| Comparación base→head | Status; adelante/atrás | Merge-base | Archivos reportados |
| --- | --- | --- | --- |
| local→AleReb remoto | ahead; 6/0 | HEAD local | docs/app.js, docs/index.html, docs/styles.css, scripts/build_site_data.py |
| local→cmasudd remoto | ahead; 5/0 | HEAD local | Los mismos cuatro |
| cmasudd remoto→AleReb remoto | ahead; 1/0 | HEAD cmasudd remoto | Ninguno: `files=[]` |

Son resultados observados de tres comparaciones fijadas por SHA [V03-E04, `remote.comparisons` del manifiesto]. La última respalda inclusión histórica y ausencia de diferencias de archivos reportadas entre esos dos extremos; no se descargaron ni hashearon árboles remotos completos. El commit AleReb remoto tiene mensaje “Merge pull request #1 from cmasudd/main”, coherente con esa integración [V03-E03–04].

**Límite:** no se declara equivalencia de commits, autoría exclusiva, repositorio canónico ni igualdad de despliegues. El canónico requiere decisión del responsable. No se consultó la web publicada ni sus JSON. Las comparaciones no listan cambios del XLSX; no se descargaron sus bytes remotos para verificar hash.

La respuesta del commit AleReb incluye un parche de `scripts/build_site_data.py` que cambia las siete coordenadas de estación respecto del local. Por ejemplo, Canelo pasa de (-33.576468,-70.452054) a (-33.581603,-70.451175). Es cambio observado en código, no confirmación geodésica [V03-E03, parche del archivo; V03-E05:25–33]. La auditoría siguiente fija explícitamente archivos locales anteriores; no debe usarse como validación del JSON desplegado o de las nuevas coordenadas.

## Auditoría Canelo: abril–junio de 2022

### Fuentes y mapeo

**Observado:** `Canelo_Maipo` se enlaza mediante `rId7` a `xl/worksheets/sheet7.xml`; filas 3–5 corresponden a los primeros tres meses disponibles según la columna A. `workbookPr` no declara `date1904`; la conversión usada es la del sistema 1900, base 1899-12-30. Se verificó correspondencia con las fechas ISO del JSON, sin verificar fecha de terreno externa [V03-E05–07].

El mapeo de la hoja a `stationId=canelo-maipo` y las columnas se observaron en el conversor local (líneas 25–58). Se leyó código, sin importarlo ni ejecutarlo. El JSON declara `source=abril2022anov2026_VPA.xlsx`; ese nombre no acredita por sí solo la cadena de generación [V03-E05–07].

| Columna/campo | JSON values | Unidad etiquetada en conversor |
| --- | --- | --- |
| B | conductivity | µS/cm |
| C | hardness | ppm |
| D | ph | sin unidad |
| E | salinity | ppm |
| F | tds | ppm |
| G | waterTemp | °C |
| H | orp | mV |
| I | turbidity | NTU |
| J | alkalinity | sin unidad |

Son etiquetas documentadas/codificadas, no unidades del instrumento certificadas. En Canelo, I1 dice “Turb” y J1 “Alcalinidad”, sin unidad explícita en esos encabezados [V03-E05:35–45; V03-E06, `audit.headers`].

### Resultados puntuales

Valores fuente decodificados desde XML y comparados numéricamente con `Decimal`; `1312` y JSON `1312.0` son equivalentes numéricamente. D y G usan cadenas compartidas XLSX (`t=s`) en las tres filas; se resolvieron antes de comparar. No hay fórmulas en las 27 celdas seleccionadas [V03-E06–07; `audit.samples`].

| Fecha; fila XLSX; índice JSON base0 | B conductividad | C dureza | D pH | E salinidad | F TDS | G temperatura | H/I/J |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | --- |
| 2022-04-03; 3; 2 | 1312 | 600 | 8.34 | 998 | 1312 | 13.5 | ausentes→null |
| 2022-05-01; 4; 9 | 2197 | 400 | 8.12 | 1037 | 1286 | 9.8 | ausentes→null |
| 2022-06-05; 5; 16 | 2577 | 420 | 8.54 | 1293 | 1703 | 10.2 | ausentes→null |

A3/A4/A5 tienen seriales 44654/44682/44717. Cada fecha tiene exactamente un registro JSON para Canelo; la selección del período contiene tres filas fuente y tres registros JSON. Las 18 comparaciones numéricas y 9 comparaciones de ausencia/null coinciden, con cero discrepancias en este alcance. No se interpretan los null como cero, valor bajo o ausencia de muestreo [V03-E06–07].

| Artefacto local | SHA-256 |
| --- | --- |
| XLSX | `4fe06c1d6426060563108cb07092ed1d90b22bc6c72dc6aa7f2b887d2edaf108` |
| JSON existente | `8d9232b3d764c7a0194a5197989c6c41400ab37a45560cd54bb4fa96f8753de9` |
| Conversor leído | `7d03fb581666621b114931459ef370d5634c20a2157df3ec88d96c541dbd0441` |

XLSX y conversor están rastreados en el commit local; el JSON es ignorado y no se atribuye a ese commit. Se repitieron hashes al finalizar, sin cambios [V03-E01,05–07]. El manifiesto conserva hash XML de la hoja, valores crudos decodificados, celda ausente/tipo/fórmula, índice JSON y resultado por campo.

## Verificación y reproducción

Ejecutado: comandos Git de lectura, `sha256sum`, texto numerado del conversor; consultas remotas anteriores; Python propio con `zipfile`, `ElementTree`, `json`, `datetime`, `Decimal` y `hashlib`. El script resuelve hoja por relación, decodifica sharedStrings, inspecciona las fechas de Canelo para elegir tres meses y compara solo las nueve columnas de filas seleccionadas. No importa funciones del generador.

Para repetir el núcleo de la comparación sobre los archivos fijados:

```python
import json, zipfile, xml.etree.ElementTree as ET
from pathlib import Path
from datetime import datetime, timedelta
from decimal import Decimal
p = Path('/home/ale/Documents/repos/voluntariosxagua')
n = {'m': 'http://schemas.openxmlformats.org/spreadsheetml/2006/main'}
j = json.loads((p/'docs/data/measurements.json').read_text())
fields = dict(zip('BCDEFGHIJ', [
    'conductivity','hardness','ph','salinity','tds',
    'waterTemp','orp','turbidity','alkalinity']))
with zipfile.ZipFile(p/'abril2022anov2026_VPA.xlsx') as z:
    strings = [''.join(t.text or '' for t in a.findall('.//m:t', n))
               for a in ET.fromstring(z.read('xl/sharedStrings.xml')).findall('m:si', n)]
    # Relación Canelo_Maipo/rId7→sheet7.xml verificada en V03-E06.
    rows = ET.fromstring(z.read('xl/worksheets/sheet7.xml')).findall('m:sheetData/m:row', n)
    def read(c):
        if c is None: return None
        v = c.find('m:v', n)
        if v is None: return None
        return strings[int(v.text)] if c.get('t') == 's' else v.text
    for row in rows:
        if row.get('r') not in ('3','4','5'): continue
        cells = {c.get('r').rstrip('0123456789'): c for c in row.findall('m:c', n)}
        date = (datetime(1899,12,30)+timedelta(days=float(read(cells['A'])))).date().isoformat()
        matches = [(i,r) for i,r in enumerate(j['records'])
                   if r['stationId']=='canelo-maipo' and r['date']==date]
        assert len(matches) == 1
        i, record = matches[0]
        for col, field in fields.items():
            raw, actual = read(cells.get(col)), record['values'][field]
            ok = actual is None if raw in (None,'') else (
                actual is not None and Decimal(raw)==Decimal(str(actual)))
            assert ok, (date,col,field)
        print(date, row.get('r'), i, '9/9 coinciden')
```

Este fragmento reproduce el núcleo para las celdas observadas; no es un lector XLSX general ni audita otras filas. La selección temporal, conteos, tipos y resultados completos del script ejecutado están en el manifiesto.

No ejecutado: generador, servidor, navegador, publicadores, imports de código fuente, análisis de tendencias, descargas de producción ni modificaciones de mediciones. No se añaden pruebas al proyecto fuente. Las verificaciones de esta tarea no equivalen a certificación de datos.

## Viabilidad C, brechas y siguiente paso

| Aspecto | Evaluación etiquetada y evidencia |
| --- | --- |
| Recuperación local | **Observado:** muestra fuente y derivado accesibles, con mapeo reproducible y coincidencias puntuales [V03-E05–07]. |
| Relación entre versiones | **Observado:** historias relacionadas e integración remota; el local es anterior [V03-E03–04]. |
| Procedencia completa | **Pendiente:** KoboCollect→XLSX, fecha/versión efectiva de generación, revisión mensual y vínculo a JSON publicado. |
| Calidad y significado | **Pendiente:** diccionario, causas de faltantes, réplicas, instrumentos/calibración, unidades efectivas y coordenadas confirmadas. |
| Derechos y personas responsables | **Pendiente:** responsable de datos, permisos por datos/software/fotos y contribuciones; no se copiaron datos personales. |
| Publicación investigable | **Inferencia:** continuar con protocolo de curación o caso de métodos; descriptor de datos completo condicionado. No afirmar novedad ni tendencias [V03-E08]. |

**Siguiente tarea propuesta:** el responsable debe designar canónico/versión y autorizar diccionario y procedencia previa al XLSX. Sobre copias fijadas por hash, extender la auditoría a casos de faltantes, textos, fechas repetidas y coordenadas; registrar decisiones sin corregir fuentes por suposición. Después comparar evidencia de A/B/C y definir revisión bibliográfica y protocolo. V03 no requiere elegir revista ni generalizar estos tres registros.

## Criterios de entrega

| Criterio | Resultado |
| --- | --- |
| Reconciliar historias con evidencia remota | Cumple acotadamente: metadatos, commits y tres comparaciones; canónico/fork formal/despliegues pendientes. |
| Auditar una estación/período XLSX→JSON | Cumple: Canelo abril-junio 2022, tres filas, 27 campos y mapeos por celda/registro. |
| Registrar versiones, brechas y viabilidad C | Cumple documentalmente: hashes, resultados puntuales y condiciones explícitas. |
| Mantener fuentes de solo lectura y entrega acotada | Cumple: dos archivos de V03; sin generador, cambios fuente, backlog o commit. |

Estado final propuesto: **en_revision**, sujeto a revisión del coordinador.
