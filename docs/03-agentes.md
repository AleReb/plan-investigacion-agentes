# Organización de agentes y modelos básicos

| Rol | Capacidad | Tareas | No decide |
| --- | --- | --- | --- |
| Coordinador | Mayor razonamiento | Descomponer, priorizar, resolver contradicciones, aceptar entregas | No inventa evidencia faltante |
| Inventario GitHub | Básica | Metadatos, versiones, README, árbol, licencias presentes, familias | Autoría exclusiva o calidad científica |
| Webs | Básica | Repo→dominio, rutas visibles, flujos y documentación | Cambios de producción |
| Servidor | Intermedia para análisis; básica para extracción acotada | Arquitectura y operación desde acceso de lectura | Reinicios, migraciones ni exposición de datos |
| Trayectoria | Básica | Cronología de proyectos, rol declarado, colaboradores | Identidad por homonimia |
| Evidencia/datos | Básica para extracción, mayor para diseño | Diccionario, faltantes, procedencia, inventario de ensayos | Validez causal o diseño estadístico |
| Investigación | Mayor razonamiento | Literatura, contribución, método, interpretación | Autorías finales o resultados inexistentes |
| Hardware | Básica para documentación; mayor para revisión técnica | BOM, CAD, firmware, montaje, compatibilidad y brechas | Validación física sin pruebas |
| Revisor | Independiente del ejecutor | Contrastar entrega con fuentes y criterios | Aceptación por fluidez del texto |

“Básica” es una clase de capacidad, no un modelo fijado. El coordinador debe registrar proveedor, ID exacto, versión/fecha y límites antes de ejecutar. No se ha instalado ni lanzado un modelo alternativo en esta preparación.

## Piloto antes de escalar

1. Usar T01 y T02 sobre los README locales como referencia; crear fichas con el mismo contrato.
2. Revisar el 100% de los hechos y citas de las dos primeras entregas. Aceptación: cero hechos inventados, todos los campos obligatorios, fuentes/localizadores válidos y límites conservados.
3. Si falla, una devolución específica; si vuelve a fallar, subir capacidad o reducir la tarea. No encadenar reintentos ilimitados.
4. Solo después, dividir inventario en lotes de hasta cinco repositorios similares. Revisar íntegramente afirmaciones científicas, autoría y hardware; para metadatos rutinarios comprobar una muestra del 20%, ampliando a todo el lote ante un error.

## Paquete de contexto

Cada tarea recibe objetivo único, fuentes permitidas y fijadas, fragmentos relevantes, plantilla, criterios, dependencias, directorio de salida y límites. No enviar el historial completo ni todo el portafolio al ejecutor. Contexto sugerido: hasta cinco archivos o 12 000 tokens; dividir si excede. El número es operativo y ajustable al modelo disponible.

Límite inicial propuesto: dos ejecutores concurrentes y un revisor; 30 minutos por tarea documental, dos intentos, presupuesto de tokens explícito antes del lanzamiento. Registrar consumo real si la plataforma lo expone; no inventar costos. La investigación bibliográfica y las pruebas físicas requieren límites propios.

El coordinador es el único escritor del backlog. Reclama tarea con dueño y fecha, bloquea escrituras superpuestas, recoge artefactos y libera la tarea tras revisión. Si un agente se interrumpe, registra último artefacto y retoma desde allí. Trabajar secuencialmente si el entorno no ofrece agentes paralelos.
