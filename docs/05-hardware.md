# Preparación de hardware para liberar

Interpretación provisional: preparar diseños, firmware y documentación que otra persona pueda reproducir. Confirmar dispositivo objetivo y si “hardware x” significa hardware abierto, un equipo específico o la revista HardwareX.

## Paquete por dispositivo

- Identidad: nombre, revisión de placa, fotos, función, límites y matriz de compatibilidad.
- Diseño editable: esquemáticos, PCB, mecánica/CAD; exportaciones de fabricación y relación con sus fuentes.
- BOM: referencia, cantidad, fabricante/modelo, alternativa comprobada, costo con moneda/fecha/fuente y disponibilidad por verificar.
- Firmware: commit/tag, dependencias y toolchain fijados, configuración sin secretos, protocolo y guía de recuperación si está documentada.
- Montaje: cableado, alimentación, conectores, orientación, pasos y puntos de verificación.
- Validación: protocolo, instrumental, datos crudos, resultados, fallos conocidos y revisión compatible; distinguir inspección, compilación y ensayo físico.
- Reutilización: procedencia y titularidad de cada artefacto; licencias de hardware, software, documentación y datos revisadas por separado. No relicenciar aportes ajenos por defecto.
- Reproducción: tercero siguiendo documentación, dudas encontradas y correcciones; si no se ejecuta, marcar pendiente.

## Criterios de preparación

Paquete documental listo: fuentes editables localizadas, versiones coherentes, BOM revisada, manual suficiente, licencias/procedencia identificadas y limitaciones explícitas. Dispositivo validado: además, ensayos reales aceptados contra criterios previos. Un paquete documental puede estar listo aunque el dispositivo todavía no esté validado, pero debe decirlo.

Para modularAirFlow empezar por inventariar sketches, PCB, STL y manual del sensor sin modificar ni compilar. No presentar el módulo de flujo ESP32-S3 propuesto como implementado. La posición contada por pasos no es una medición con encoder, según su README. Los valores de pruebas comunicadas no son una campaña de calibración.

Preparar un directorio de release con índice, hashes y archivos seleccionados. Registrar pendientes antes de proponer tag, publicación o envío editorial. El significado alternativo de desbloquear dispositivos requiere una ficha separada de equipo, propiedad/acceso, objetivo, documentación del fabricante y recuperación; no se planifican operaciones concretas sobre un modelo desconocido.
