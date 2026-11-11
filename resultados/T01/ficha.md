# Ficha de proyecto: modularAirFlow

Estado: **en_revision**. Fecha de lectura: 2026-11-11. Responsable: agente ejecutor T01, modelo gpt-6.1-sol según asignación del coordinador.

## Identidad y versión

Sistema para generar, medir y dirigir flujo de aire; familia de firmware y hardware modular. La finalidad y arquitectura ESP32-S3 proceden del README, no de una validación del instrumento [T01-E01]. Fuente local: `/home/ale/Documents/repos/modularAirFlow`, HEAD `2142d6b02380c41aeb3fce25895ac481200e841f` (fecha de commit 2026-11-09, observada con `git show -s --format=fuller HEAD`). `origin` apunta a `https://github.com/AleReb/modularAirFlow`; su condición de repositorio canónico no se confirmó [T01-E17]. No se verificó despliegue web ni servicio operativo: quedaron fuera del alcance documental local.

## Hardware, software y variantes

| Variante | Evidencia disponible | Madurez que puede afirmarse |
| --- | --- | --- |
| `ventiladorFlujo` ESP32-C3 + AFM3000 + BTS7960 | Código de PWM manual, CRC y adquisición [T01-E09]; README atribuye prueba al usuario [T01-E10] | Referencia funcional declarada; ensayo no reproducido por el agente |
| `airSensor`, `pruebaPWM`, `ventilador`, `minirevolver` | README principal los conserva como referencias anteriores [T01-E02] | No se realizó auditoría exhaustiva de esos sketches |
| `centralI2C` + `minirevolveri2c` | Código de central S3, AFM3000 y PWM locales; módulo remoto de movimiento con protocolo v1 [T01-E04–E08] | Implementación observada estáticamente; pendiente de compilación/prueba según documentación [T01-E14–E15] |
| `protominirevolver` + `protominirevolvermaster` | Adaptación PCB, RTC/SD y protocolo v2 documentados [T01-E11–E13] | Variante distinta; documentación declara funciones nuevas sin prueba en placas. No intercambiar con v1 |
| `pruebaIMUI2C` | README de dos sketches de IMU remoto [T01-E16] | Ejemplo documental; sin validación reproducida |
| Módulo S3 independiente de flujo, interfaz futura, RS-485/CAN | Propuestas del README principal, líneas 9, 26, 50 y 123–129 [T01-E01] | Propuesto; no confundir con firmware disponible |

Arduino-ESP32 2.0.17 y USB CDC son referencias declaradas, no una instalación comprobada; `ESP_FlexyStepper` es dependencia del módulo sin versión fijada en su README [T01-E14–E15]. Existen archivos EAGLE, STL, PDF y una carpeta build versionada, sin auditoría de contenido, correspondencia ni reproducibilidad en esta tarea [T01-E18].

La posición del movimiento es conteo de pasos; no prueba posición real ni detecta pasos perdidos. Los límites 0–2000 son provisionales. El código exige homing antes de destinos y devuelve estados, pero su efectividad física no fue medida [T01-E08, E15]. La aceptación de una orden tampoco acredita movimiento terminado [T01-E06].

## Ensayos y datos

**Probado por el usuario, según documentación:** rango aproximado 2–35 slm en el montaje C3; posible falta de arranque a PWM 160 aunque pueda sostener giro; detención próxima a PWM 60; comparación puntual referencia 1,8 slpm frente a AFM3000 1,90–2,30 slm [T01-E02, README:L109–121; T01-E10]. No se dispone aquí de mensajes originales fechados, datos crudos, repeticiones, incertidumbre, identificación del equipo patrón ni condiciones de comparación. Estos números no son calibración ni exactitud demostrada.

**Observado por el agente:** archivos y contenido estático, integridad por SHA-256, protocolos y estado Git [manifiesto](evidencias.json). No se reprodujo ningún ensayo físico o simulación. Los artefactos build existentes no prueban compilación de la fuente actual [T01-E18].

**Propuesto:** separar flujo de la central; estudiar arranque/histéresis y comparación de caudal mediante un protocolo posterior. Los valores PWM 255/300 ms y mínimo 70 están expresamente sin implementar ni validar [T01-E02, E10].

## Atribución, licencias y huecos

El repositorio local está bajo un origin AleReb y el commit usa ese identificador; esto no demuestra autoría exclusiva ni distribución de contribuciones. Rol concreto de Alejandro, colaboradores y derechos por artefacto quedan pendientes [T01-E17]. La consulta de nombres LICENSE/COPYING no devolvió archivos; no se deduce permiso de reutilización ni inexistencia de avisos internos. Resolver licencias de firmware, CAD, manual y dependencias antes de preparar publicación [T01-E17–E18].

Brecha documental observada: la tabla del README principal (L54–76) no incluye los prototipos v2 ni IMU presentes en el árbol; las versiones/pines deben conservarse separados [T01-E01, E11–E13, E16]. No se corrige la fuente en esta tarea.

## Pregunta candidata y siguiente tarea

**Propuesta, sin novedad evaluada:** ¿qué repetibilidad de caudal y qué diferencia entre umbral de arranque y mantenimiento presenta el montaje C3 al variar PWM, bajo condiciones registradas? Baseline posible: control manual actual sin compensación. Se necesitan identificación del ventilador/conducto, alimentación, condiciones estándar de ambos equipos, instrumento de referencia trazable, series temporales crudas y plan de repeticiones/incertidumbre. La comparación entre arquitectura local y modular requiere primero validar cada variante. Son candidatos para T07–T09, no resultados científicos.

Siguiente tarea documental sugerida al coordinador: consolidar variantes, elegir dispositivo objetivo y obtener bitácoras/datos originales y licencias. Mantener **prohibición de compilar o cargar firmware por el asistente** y preservar las referencias funcionales [T01-E03].
