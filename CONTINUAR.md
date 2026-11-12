# Punto de continuación

Actualizado: 2026-11-12. El usuario pidió conservar avance antes de agotar límites. Todo el trabajo de esta tanda está en archivos versionables; no depende de procesos persistentes.

## Objetivo vigente

Visión GENERAL del trabajo de Alejandro Rebolledo para proponer papers/publicaciones. Integrar AleReb, webs cmasudd, sensores.cmasccp.cl (administrado por usuario) y trayectoria cuando se identifique. Usuario autorizó gpt-6.1-sol; conservar esa preferencia para tareas acotadas. No reducir el portafolio a dos proyectos.

## Completado

- Plan, inventarios preliminares (100 AleReb y 13 cmasudd; cobertura incompleta), T01/T02/P01/P02/P03 y síntesis general.
- V01: leídos dos PDF de aire (16 páginas). Campaña de co-ubicación identificada y ensayo electrónico sin sensores. Faltan series/scripts; no reproducir conclusiones desde gráficos.
- V02: seis archivos reales; dos exportadores comparten patrón pero difieren en latest, faltantes, colisiones y publicación. Lectura estática, no tests ejecutados.
- V03: historias remotas de voluntariosxagua relacionadas; checkout local anterior. Canelo abril-junio 2022: 18 valores+9 ausencias coinciden XLSX→JSON. No generalizar a todo dataset o despliegue.
- Coordinador revisó entregas, repitió comparación local y Git, y contrastó exportadores y partes de PDF.
- VIABILIDAD_PUBLICACIONES.md: A principal, C alternativa, B recuperación; D–G permanecen en cartera.
- bibliografia/EXPLORACION_2026-11-12.md: tres fuentes primarias con alcance leído; no revisión completa ni novedad establecida.
- protocolos/A_EVALUACION_OFFLINE.md: diseño preliminar no ejecutado. D002 documenta prioridad y acceso a A01/A02 sin exigir inventario exhaustivo.

## Retomar

1. Leer AGENTS, este archivo, VIABILIDAD_PUBLICACIONES, D002 y backlog; comprobar git status/log.
2. A01: preparar banco reproducible offline para tres escenarios mínimos de V02 (colisión, sentinela/finitud, frontera de partición), con fuentes por hash, fixtures sintéticos y aislamiento de BD/env/main/red. Seguir protocolo; no ejecutar publicadores reales. gpt-6.1-sol + revisión.
3. A02: ampliar literatura primaria sobre contratos/procedencia/publicación ambiental y diferenciación frente a ODM2 y alternativas. Leer métodos/resultados; tabla de diferencias y pregunta defendible, sin reclamar prioridad histórica.
4. C01: extensión acotada a casos difíciles/versiones; no rehacer muestra ya contrastada. B01 espera localizar archivos originales; pedir ubicación concreta si ninguna fuente accesible los aporta, nunca credenciales en texto.
5. Registrar resultados favorables y desfavorables, actualizar decisión y checkpoint; guardar commit local antes de cerrar. T08/T09 globales no están completos.

## Accesos, límites y continuidad

LinkedIn exacto, acceso interno servidor y definición de liberar hardware pendientes. No impiden tareas A01/A02. No compilar/cargar modularAirFlow ni modificar repos fuente/producción. No publicar este repo sin revisar metadatos privados y permisos de materiales. No se ha enviado a GitHub ni contactado al equipo.

Los PDF/textos de V01 en /tmp/v01-aire son temporales: manifiesto guarda URLs al commit y hashes para volver a descargarlos; no confiar en su persistencia. Fuentes de V02 fijadas por blob, no commit desplegado. En V03 los JSON ignorados se identifican por hash, no por commit.

Los tres agentes de esta tanda terminaron: piloto_airflow V01, panorama_webs V02, piloto_agua V03; modelo gpt-6.1-sol. No hay agente ni automatización trabajando en segundo plano. Reutilizar agentes si existen o crear nuevos con contexto mínimo; los archivos son la referencia durable. El entorno actual no tiene rg disponible; usar Python/find como alternativa si sigue faltando.
