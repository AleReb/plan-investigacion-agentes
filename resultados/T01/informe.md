# Entrega T01

- Objetivo: ficha documental acotada de modularAirFlow, sin ejecutar firmware.
- Responsable/modelo: ejecutor T01 / gpt-6.1-sol según asignación del coordinador.
- Fecha: 2026-11-11. Entrada: HEAD `2142d6b02380c41aeb3fce25895ac481200e841f`.
- Permisos: lectura local de fuente; escritura exclusiva en `resultados/T01/`. T00 aceptada según coordinador y backlog leído.
- Artefactos: [ficha.md](ficha.md), [evidencias.json](evidencias.json), este informe. Estado solicitado: **en_revision**.

## Hallazgos

| Afirmación | Tipo | Evidencia/localizador | Límite |
| --- | --- | --- | --- |
| La arquitectura objetivo S3 mantiene un módulo de flujo aún propuesto | Declarado por documentación | T01-E01; README:L3–37 | No implica integración validada |
| El montaje C3 figura como probado por el usuario; hay rangos/umbrales aproximados | Declarado por documentación sobre usuario | T01-E02, E10; README:L109–121 | Sin reproducción ni mensajes originales/datos crudos |
| La central conserva PWM y sensor locales, consulta módulo remoto y separa STOP de REV STOP | Observado en código | T01-E04–E07; centralI2C.ino:L65–82,115–130 | Lectura estática, no ejecución |
| Minirevolver contiene homing y límites provisionales; posición contada | Observado en código | T01-E08; minirevolveri2c.ino:L89–118 | Sin prueba de precisión ni protección mecánica validada |
| Coexisten v1 (estado 14 bytes) y v2 (22 bytes); incompatibilidad declarada | Observado en constantes y declarado por documentación | T01-E07, E12–E13; Protocolo.h:L5–8 de ambas variantes | No probar intercambiabilidad; sin auditoría completa de v2 |
| README principal omite variantes de prototipo v2 e IMU de su tabla | Observado por comparación documental | README:L54–76 frente a T01-E11–E13, E16 | Brecha documental, no conclusión de funcionamiento |
| Fuente limpia y prohibición de compilar/cargar conservada | Observado / declarado por documentación | T01-E03, E17 | Ningún firmware ejecutado ni modificado |

El manifiesto fija commit, ruta, líneas, SHA-256, método y límites por evidencia. La ficha distingue pruebas atribuidas al usuario, observaciones del agente y propuestas. No se establecen novedad científica, calibración, autoría exclusiva ni licencia de publicación.

## Verificación

Acciones realizadas, en orden funcional (desde la fuente salvo indicación):

```text
pwd
rg --files -g AGENTS.md -g README.md -g '*T01*' -g '*plantilla*' /home/ale/Documents/repos/plan-investigacion-agentes
cat AGENTS.md README.md
find plantillas -type f
cat tareas/backlog.json prompts/ejecutor.md docs/01-revision-inicial.md docs/02-plan.md
cat plantillas/entrega.md plantillas/proyecto.md plantillas/evidencia.json
git rev-parse HEAD
git status --short
git remote -v
git show -s --format=fuller HEAD
find /home/ale/Documents/repos/modularAirFlow -name AGENTS.md -o -maxdepth 2 -iname 'readme*'
find /home/ale/Documents/repos/modularAirFlow -maxdepth 3 -type f -not -path '*/.git/*'
nl -ba <archivo leído>
git ls-files '*LICENSE*' '*COPYING*' '*test*'
sha256sum README.md centralI2C/Protocolo.h minirevolveri2c/Protocolo.h
cmp -s centralI2C/Protocolo.h minirevolveri2c/Protocolo.h
git ls-files
git status --porcelain=v1
git diff --exit-code HEAD --
```

`rg` no está disponible (una consulta inicial produjo rutas; el siguiente intento devolvió exit 127); se continuó con `find` y lecturas acotadas. `nl -ba` se aplicó al README principal, README de central, minirevolver I2C, flujo, prototipos e IMU; centralI2C.ino, headers de sus buses/protocolo, minirevolveri2c.ino, ventiladorFlujo.ino y Protocolo.h v2. Algunas salidas largas se truncaron; se releyeron tramos relevantes con `head`/`sed`; no se afirma cobertura exhaustiva del repositorio. No se halló AGENTS.md en la consulta acotada a la fuente; las reglas de la fuente se tomaron del README:L131–135.

Resultados: HEAD coincidente con revisión inicial; SHA-256 README `14a30ecb1bf0dd0741a57ba3ccff520f9b7d361ccdf17e1a138fc0f71f1d2cfb`; headers v1 idénticos (cmp exit 0, SHA-256 `399e98989c1eb76cb5114abf16d8ad26dde98c9ddaaed6209045b6c7a6e29bdd`). Status sin salida al inicio y final; diff exit 0. Consulta de nombres de licencia/tests sin salida. Se generó el manifiesto mediante Python (lectura de archivos, SHA-256, JSON); no se copiaron secretos ni artefactos binarios. La existencia de build se registró solo por rutas, sin abrir logs o atribuir éxito de compilación.

No se compiló, cargó, simuló ni ejecutó firmware, no se conectaron placas, no se verificó hardware/CAD/manual PDF, no se accedió a red ni se realizó búsqueda bibliográfica. No se modificaron fuente, backlog ni inventarios; no se hizo commit.

## Criterios de aceptación

| Criterio | Estado | Evidencia |
| --- | --- | --- |
| Citar commit y README | Cumple documentalmente | Versión y SHA-256 arriba; T01-E01–E03 |
| Separar pruebas declaradas, código y arquitectura propuesta | Cumple documentalmente | Tabla y secciones de ficha; manifiesto clasificado |
| Conservar prohibición de compilar/cargar | Cumple | T01-E03; ninguna ejecución de firmware |

## Faltantes y siguiente paso

Pendientes: bitácoras originales y datos crudos; variante canónica y placa/montaje concreto; contribuciones y licencias por artefacto; versiones de dependencias; verificación metrológica y funcional futura autorizada. La diferencia de protocolos y pines requiere conservar ambas ramas documentales; no demanda editar firmware para cerrar T01.

Propuesta al coordinador: revisar esta entrega, incorporar variantes al inventario consolidado cuando corresponda y utilizar la pregunta candidata solo como insumo de T07–T09. T10 sigue condicionado por definición del dispositivo y significado de liberar. **en_revision**, pendiente de aceptación del coordinador.
