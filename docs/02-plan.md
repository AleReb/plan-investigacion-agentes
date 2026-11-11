# Plan por fases

Las duraciones son bloques propuestos de trabajo, no compromisos de calendario. La investigación física depende de acceso, materiales y disponibilidad del equipo.

| Fase | Trabajo | Entrega | Criterio de salida |
| --- | --- | --- | --- |
| 0. Alcance, 1 bloque | Confirmar fuentes, acceso, significado de liberar, presupuesto | Inventario de fuentes y decisiones | Cada fuente tiene responsable, acceso y alcance; faltantes explícitos |
| 1. Inventario, 2–4 bloques | GitHub personal y cmasudd, webs, servidor, LinkedIn y proyectos | Fichas por proyecto, mapa repo→despliegue→datos→persona | Cobertura documentada, duplicados relacionados, versiones fijadas |
| 2. Evidencia, 2–4 bloques | Leer código, documentación, historial, datasets, ensayos y licencias | Matriz afirmación→evidencia; informe de brechas | Hechos separados de declaraciones; ausencia de evidencia visible |
| 3. Selección, 1–2 bloques | Comparar candidatos y literatura primaria | Lista priorizada y decisión razonada | Una pregunta principal viable y un candidato alternativo |
| 4. Protocolo, 1–3 bloques | Baselines, métricas, datos, análisis y ensayo | Protocolo congelado antes de nuevos resultados | Revisor acepta método, factibilidad y trazabilidad |
| 5. Validación, variable | Ejecutar pruebas autorizadas, limpiar datos, reproducir análisis | Datos versionados, scripts, tablas, figuras y bitácora | Resultados repetibles y limitaciones explícitas |
| 6. Manuscrito/release, 2–4 bloques | Redactar y empaquetar artefactos | Borrador de paper y paquete de hardware | Referencias verificadas, afirmaciones respaldadas, checklist satisfecho |
| 7. Preparación editorial | Revisar venue, formato y metadatos vigentes | Paquete concreto listo para revisión final | Destino y permisos resueltos antes de publicación |

## Orden y paralelismo

Después de fijar el alcance, GitHub, webs, documentación de hardware y trayectoria pueden revisarse en paralelo con tareas separadas. El servidor espera un acceso identificado; LinkedIn espera URL o exportación. La selección científica depende de fichas y evidencia, no solo del nombre del proyecto. Las ramas bloqueadas no detienen las restantes: marcar explícitamente cualquier selección provisional.

La redacción de métodos puede avanzar con protocolo aceptado. Resultados y conclusiones esperan mediciones y análisis reales. La preparación documental de hardware puede avanzar en paralelo; la afirmación de funcionamiento espera ensayos.

## Priorización

Puntuar cada candidato de 0 a 4: evidencia disponible (30%), pregunta y contribución potencial (25%), reproducibilidad (20%), viabilidad (15%), relevancia (10%). Registrar fuente de cada puntuación. Sin literatura, la contribución es desconocida, no 4. Sin datos válidos o derechos suficientes, el candidato queda condicionado aunque su puntuación sea alta. Elegir inicialmente un paper y un paquete de hardware para evitar dispersión.

## Puertas de calidad

G0: alcance y fuentes. G1: inventario y atribución. G2: pregunta y revisión bibliográfica. G3: protocolo. G4: resultados reproducibles. G5: manuscrito/paquete revisado. G6: revisión final de publicación. Registrar responsable, fecha, decisión y evidencia en `decisiones/`; nunca saltar una puerta por tener texto redactado.
