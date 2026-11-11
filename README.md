# Del portafolio a investigación y hardware publicable

Plan de trabajo para Alejandro Rebolledo. Creado el 11 de noviembre de 2026.

Objetivo: revisar GitHub, servidor, webs y trayectoria profesional; reconstruir evidencia del trabajo realizado; seleccionar contribuciones investigables; producir protocolos, manuscritos reproducibles y paquetes de hardware preparados para publicación.

Este repositorio contiene el plan y una exploración inicial, no una auditoría completa ni resultados científicos. La ejecución se organiza por tareas pequeñas para agentes básicos, con revisión científica y decisiones de arquitectura a cargo de un coordinador de mayor capacidad.

## Inicio

1. Leer `AGENTS.md`, `docs/01-revision-inicial.md` y `docs/02-plan.md`.
2. Revisar `inventario/` y resolver las entradas pendientes de `docs/07-pendientes.md`.
3. Seleccionar en `tareas/backlog.json` una tarea con dependencias satisfechas; usar `prompts/ejecutor.md`.
4. Entregar un informe en `resultados/<ID>/informe.md` y un manifiesto de evidencias usando `plantillas/evidencia.json`.
5. Un revisor usa `prompts/revisor.md`; el coordinador acepta o devuelve la tarea y actualiza el backlog.

## Mapa

| Archivo | Uso |
| --- | --- |
| `docs/01-revision-inicial.md` | Lo observado, sus fuentes y límites |
| `docs/02-plan.md` | Fases, dependencias y criterios de salida |
| `docs/03-agentes.md` | Roles, reparto, presupuesto y escalamiento |
| `docs/04-investigacion.md` | Preguntas candidatas y método científico |
| `docs/05-hardware.md` | Preparación de dispositivos y documentación |
| `docs/06-servidor-webs.md` | Revisión de plataforma y sitios |
| `docs/07-pendientes.md` | Información que falta |
| `inventario/*.json` | Fuentes iniciales y cobertura |
| `tareas/backlog.json` | Cola de trabajo con dependencias |
| `plantillas/` | Contratos de entrega reutilizables |
| `prompts/` | Instrucciones listas para agentes |

La planificación de “liberar” hardware usa provisionalmente el sentido de publicar diseños y firmware reproducibles. Si significa desbloquear un equipo existente, definir modelo, objetivo y acceso antes de desarrollar esa rama. No presupone que el destino sea la revista HardwareX; esa opción se evaluará después de confirmar alcance y requisitos editoriales vigentes.

Repositorio local: `/home/ale/Documents/repos/plan-investigacion-agentes`. No contiene un lanzador automático ni presupone modelos instalados. Las tareas quedan preparadas para ejecución posterior con la capacidad disponible.
