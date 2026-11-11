# Revisión inicial y trazabilidad

Fecha: 2026-11-11. Se realizó una exploración documental para diseñar el plan.

| ID | Fuente revisada | Hallazgo y límite |
| --- | --- | --- |
| E001 | Perfil GitHub conectado | Cuenta AleReb, nombre Alejandro Rebolledo. No se infiere LinkedIn a partir del nombre. |
| E002 | Conector GitHub, listado AleReb | 100 registros guardados en inventario/github.json; siguiente consulta offset 100 sin resultados. Validar cobertura: los dos repos locales no aparecen en esta respuesta. No se ha leído el código de los 100 repos. |
| E003 | README local modularAirFlow; HEAD 2142d6b02380c41aeb3fce25895ac481200e841f | Documenta propuesta modular ESP32-S3 y pruebas anteriores declaradas por el usuario. Arquitectura nueva pendiente de validación. Prohíbe compilar/cargar firmware. Árbol limpio durante lectura. |
| E004 | README local voluntariosxagua; HEAD 2e08e016df32e8f8b765af5f20abdde0308c0b13 | Describe web estática y planilla mensual de siete estaciones. Cobertura, coordenadas, unidades y validación pendientes. No se inspeccionó todavía la planilla. Árbol limpio durante lectura. |
| E005 | [GuiaSensoresUDDservidorOPEN/README](https://github.com/AleReb/GuiaSensoresUDDservidorOPEN/blob/main/README.md), blob 5a7def144b10a89f2eac3dc715b71789fbb370e3 | Describe operación y registro de sensores en sensores.cmasccp.cl/registrar. No se inspeccionaron las transcripciones ni capturas. |
| E006 | [cmas-mcp/README](https://github.com/AleReb/cmas-mcp/blob/master/README.md), blob a2223eaef293296156173ce14b4b9dab76d8657e | Declara pipeline de conocimiento y 193 videos procesados. Conteo y calidad sin reproducir. |
| E007 | [estacion-calidad-aire/README](https://github.com/AleReb/estacion-calidad-aire/blob/main/README.md), blob 06d308e26fcde0c921413ee09add16583e6240c6, primeras 90 líneas | Declara equipo con varios colaboradores, rol de firmware/comunicaciones de Alejandro y enlaces a informes de campo/laboratorio. Los informes y las especificaciones no fueron verificados. Declara CC BY-NC 4.0; revisar alcance por artefacto antes de reutilizar. |
| E008 | Declaración del usuario en esta conversación | Administra https://sensores.cmasccp.cl/. Aún no se identificó acceso interno al servidor. |
| E009 | GET HTTPS a https://sensores.cmasccp.cl/ | HTTP 200, título C+, HTML con activos JS/CSS. No valida funcionamiento de la aplicación, autenticación, API ni datos. El navegador de investigación no pudo acceder; se usó urllib para esta comprobación. |
| E010 | Declaración del usuario y [página cmasudd](https://github.com/cmasudd?tab=repositories) | El usuario declara haber creado las webs. HTML público devuelve 13 nombres de repositorios en la primera página; inventario/cmasudd.json. Conector sin resultados y API pública 403 por límite. Cobertura completa, código y despliegues pendientes. |

Hashes SHA-256 de los README locales leídos:

- modularAirFlow: `14a30ecb1bf0dd0741a57ba3ccff520f9b7d361ccdf17e1a138fc0f71f1d2cfb`.
- voluntariosxagua: `975f4677f1141a3f04e5e53426218fdd81a4eb6e8bb34e35585f2e61df05dcb6`.

Los orígenes Git locales apuntan a AleReb/modularAirFlow y AleReb/voluntariosxagua. La aparición adicional de cmasudd/voluntariosxagua exige comparar historia, despliegue y repositorio canónico; no fusionarlos por nombre.

Los nombres de repositorios sugieren familias de sensores ambientales, suelo/LoRa, energía, firmware e interfaces. Son una clasificación inicial por nombres, no conclusiones sobre capacidades. Las webs citadas como inspiración en voluntariosxagua no prueban por sí solas autoría; la declaración posterior del usuario permite incluir las webs de cmasudd, manteniendo pendiente el desglose de contribuciones.
