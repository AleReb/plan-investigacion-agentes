# Panorama transversal del portafolio AleReb

Estado: **en_revision**. Fecha: 2026-11-11. Modelo: gpt-6.1-sol según asignación. Objetivo: orientar publicaciones desde la amplitud del trabajo; T01 permanece entregada.

## Alcance

Se agruparon las **100 entradas** de inventario/github.json una vez cada una. Son el universo de ese inventario, no la cobertura revalidada de toda la cuenta. La revisión inicial advierte ausencias de repositorios locales [P01-E01, E07; manifiesto](evidencias.json). Se leyeron cinco README por GitHub, sin ejecutar código ni abrir datos o informes enlazados. Familias y relaciones por nombre son **hipótesis**, no genealogías demostradas. Los repos locales modularAirFlow/voluntariosxagua y cmasudd quedan fuera del conteo.

## Mapa completo

Número = índice 1-based del inventario. Manifiesto con JSON Pointer y visibilidad por registro. Todos los nombres tienen fuente P01-E01; familia principal para conteo, con usos transversales posibles.

### F1. Calidad del aire / HIRI y estaciones (18)

10. -Calidad-del-Aire-Avanzado, 26. mps25plantower, 28. coyhaique, 30. HIRI, 46. DUST_SENSOR_SDS198, 47. HIRI_PR0_MENU_BASEV3.1, 48. ble_plantower_HIRI_sdPM10_v2.2, 56. HIRI_PR0_BASE_V0_0_1_SDWv2, 57. hiriccp, 59. HIRI_PR0_GPSDebug_sim7600_esp32V0_08_CMAS, 61. HIRI_PR0_GPSDebug_sim7600_esp32V0_08_CMAS_WIFI_ESTABLE, 62. ble_plantower_HIRI_v2, 65. estacion-calidad-aire, 66. HiriAPP, 76. vocSerial_esp32, 77. LineaBaseModuloAIRE, 79. HIRI_PR0_GPSDebug_sim7600_esp32V0_09_CMAS_WIFI_SDS198, 98. HIRI_PR0_FINAL_V01_ESTATIC_MINIMADRE.

### F2. Suelo, agua y territorio (13)

4. humedadsuelokuscalla, 6. kuscalla-lorawan, 7. HUMEDAD_DE_SUELO, 8. Suelo-con-TTGO-LoRa32-y-LoRaWAN, 23. Sensor-de-PH, 33. soil_PH_NPK, 49. kuscallaccp, 52. UV_WINCONTOP_RS485_CAMBIO_DE_ID, 54. PH_TEMP_RS485_WINCONTOP, 58. vastago_0_02WLOCAL_LITTLEFS_ANALOG_calibrated, 67. HUMEDAD_DE_SUELO_RS458_esp32_OledRtcq_FINAL_V1, 81. CWT-WLS-water-level-sensor-manual, 92. SUELO_EC_T_HX2.

### F3. Biodigestión y procesos (3)

37. firmwareBioDigestor, 45. BIODIJESTOR2v08_7_old, 83. BIODIJESTOR2v08_7.

### F4. Adquisición, PCB, comunicación y almacenamiento (25)

11. Monitoreo-con-aceler-metro-GPS-y-GMS, 12. Monitoreo-y-Comunicaci-n-con-GSM-y-Display-OLED, 14. Medidor-de-Corriente-con-Adafruit-ADS1015, 19. Monitorizaci-n-de-Energ-a-con-ESP32-e-INA219-via-MQTT, 20. Comunicaci-n-LoRa-con-Arduino-MKR-1300, 21. Comunicaci-n-LoRa-con-Arduino-MKR-1300-y-Visualizaci-n-OLED, 22. -Comunicaci-n-LoRa-con-Arduino-MKR-1300-Visualizaci-n-OLED-y-Registro-en-SD, 24. SDUPDATER, 27. ADS1256testspeed, 41. ESP32_SD_Manager, 42. LineaBase, 43. AnalogReadSerial32, 44. esp32com, 50. SERIAL_RPI_TEST, 53. SerialSjh, 63. actualizacion_rtc_celularSim7600, 72. MULTI_I2C_ADS1115X8, 75. esps3_4seerial_2i2c, 78. miniMadre, 86. FirmwarePro, 87. FirmwareProv2, 91. PLACAMADRE_LINEA_BASE_V0_0_4_SENSORES_EXTERNOS, 94. CoyhaiquePCB, 95. clocRS3231_Deepsleep, 97. powerSistemC.

### F5. Imagen, visión y robótica conectada (9)

31. democarwifi, 32. democamaracar, 38. fotoForward, 39. placamadre_envio_imagen_api, 51. foto-uart-dropin, 60. CameraWebServerLocalAP, 68. yolotest, 70. Yolov8-Object-Detection-on-Browser, 96. wifiEsp32Motor.

### F6. Conocimiento, documentación y recursos compartidos (8)

64. cplus-base-info, 82. libraries, 84. cmas-mcp, 85. local-semantic-handoff, 88. GuiaSensoresUDDservidor, 89. GuiaSensoresUDDservidorOPEN, 90. C-BibliotecaHardware, 93. CuantumWiki.

### F7. Docencia, interfaces y experimentación (16)

3. midi5, 5. roboticamaker, 9. Gesti-n-y-Monitoreo-Ambiental-con-ESP32, 13. Control-de-Salidas-Digitales-con-Adafruit-IO, 15. Pod-metro-y-Monitor-de-Posici-n-con-ADXL345, 16. Arduino-con-Visualizaci-n-LCD-y-Sensores, 17. Monitor-de-Aceleraci-n-en-Tres-Ejes-con-Display-LCD, 18. Control-de-Rat-n-con-Arduino-Leonardo-y-MPU6050, 25. ejemploUI, 34. Claseprocessing, 55. Intro-presentarv2, 69. dafruitio, 73. trinket-lifeEsp32, 74. ESP32S3-USB-Keyboard-To-BLEtest, 99. desafio2ClasePwm, 100. desafio2MODULOS.

### F8. Propósito por confirmar (8)

1. proyectokeika, 2. keikap, 29. balanzaRPI, 35. studio, 36. pruebagit, 40. uEXC, 71. Quantum32, 80. domo.

## Qué aportaron los cinco README

Los SHA siguientes son **blobs del README**, no commits que fijen todo el repositorio. Los localizadores por sección y límites están en evidencias.json.

| Fuente | Observación documental | Blob |
| --- | --- | --- |
| [estacion-calidad-aire](https://github.com/AleReb/estacion-calidad-aire/blob/main/README.md) | Estación multiparamétrica, energía solar, GSM/4G y SD; enlaces a informe de laboratorio y co-ubicación SINCA. Rol de Alejandro: firmware/comunicaciones. Estado declarado: construcción/pruebas de campo. Las precisiones/calibraciones del README no se adoptan como resultados comprobados [E02] | `06d308e26fcde0c921413ee09add16583e6240c6` |
| [cmas-mcp](https://github.com/AleReb/cmas-mcp/blob/master/README.md) | Pipeline audiovisual/documental, estructura raw/processed y servidor MCP. Declara 193 videos enriquecidos; no se contaron ni evaluaron [E03] | `a2223eaef293296156173ce14b4b9dab76d8657e` |
| [LineaBase](https://github.com/AleReb/LineaBase/blob/main/README.md) | Dos líneas: base de códigos compartidos para múltiples estaciones ambientales. No permiten inferir integración ni madurez [E04] | `0bb85703c350aa2044930dccea950612d1930d72` |
| [BIODIJESTOR2v08_7](https://github.com/AleReb/BIODIJESTOR2v08_7/blob/main/README.md) | Firmware SAMD21, temperatura/pH/EC/HR, OLED, RTC y SD/CSV; autoría Alejandro y CC BY 4.0 declaradas [E05] | `582550332224a96cfe79c9ecf9d415ed5603aadf` |
| [C-BibliotecaHardware](https://github.com/AleReb/C-BibliotecaHardware/blob/main/README.md) | Documentación MiniMadre, recursos EAGLE y Arduino; autores colectivos C+, Alejandro recopilador; CC BY-NC declarada [E06] | `acde66062f69a69e316c56aa300b53dd5b3ddf0a` |

Referencias abreviadas E02–E07 corresponden a P01-E02–P01-E07. No se verificaron archivos LICENSE ni derechos de cada componente; recopilar bibliotecas no equivale a autoría de todas ellas.

## Relaciones entre variantes: hipótesis que conviene verificar

- **HIRI:** HIRI, HIRI_PR0*, ble_plantower_HIRI*, hiriccp y HiriAPP parecen una familia por nombre. Sufijos V0_08/V0_09, WIFI, SDS198, FINAL y MINIMADRE sugieren revisiones o configuraciones; no establecen orden histórico, equivalencia, estabilidad ni integración con estacion-calidad-aire [E01]. Comparar Git y montajes antes de fusionar evidencia.
- **Plataformas ambientales:** LineaBase declara el propósito de base multiestación [E04]. LineaBaseModuloAIRE, PLACAMADRE_LINEA_BASE*, miniMadre, C-BibliotecaHardware y CoyhaiquePCB son puentes plausibles por nombre/README de biblioteca [E01,E06]. No se demostró qué firmware corre en qué PCB.
- **Biodigestión:** firmwareBioDigestor ↔ BIODIJESTOR2v08_7_old ↔ BIODIJESTOR2v08_7 son variantes candidatas por nombre; solo el README de la última fue leído [E01,E05]. “old” no basta para fijar un canónico.
- **Suelo/territorio:** kuscalla-lorawan, humedadsuelokuscalla, kuscallaccp y los códigos HUMEDAD_DE_SUELO, soil_PH_NPK y SUELO_EC_T_HX2 podrían compartir sensores o campañas; relación no demostrada [E01].
- **Recursos y operación:** GuiaSensoresUDDservidor ↔ GuiaSensoresUDDservidorOPEN y FirmwarePro ↔ FirmwareProv2 son pares nominales. El primero incluye un repositorio privado: no asumir contenido idéntico ni publicar ese material [E01]. cmas-mcp y local-semantic-handoff se conectan aquí solo como hipótesis de conocimiento asistido por IA, no por dependencia observada [E01,E03].

## Seis líneas distintas de publicación

Son **propuestas** de contribución, no afirmaciones de novedad ni resultados. La agrupación permite reutilizar evidencia transversal sin presentar 100 repositorios como 100 investigaciones.

| Línea y trabajo que conecta | Contribución candidata / tipo | Evidencia disponible | Evidencia faltante y puerta de decisión |
| --- | --- | --- | --- |
| **1. Calidad y comparabilidad de una red ambiental.** estacion-calidad-aire + familia HIRI + LineaBaseModuloAIRE + sensores PM/VOC + posible plataforma sensores | Evaluación de co-ubicación, deriva y completitud de datos de una configuración bien identificada. Artículo de evaluación instrumental o monitoreo ambiental; dataset si los derechos y metadatos lo permiten | README estación enlaza informes SINCA/laboratorio y describe roles; códigos HIRI presentes por nombre [E01,E02] | Leer informes, obtener datos crudos sincronizados, identificar versiones/montajes, referencia trazable, condiciones ambientales, QA/QC y contribuciones. No usar la tabla de precisión como validación. **Primera opción para localizar evidencia existente**, no para afirmar que el paper ya está listo |
| **2. Plataforma reproducible de adquisición modular.** LineaBase + miniMadre + PLACAMADRE* + C-BibliotecaHardware + adquisición ADS/I2C/RS485 y powerSistemC; modularAirFlow como candidato externo al listado | Paquete de diseño y evaluación de integración/reconfiguración, recuperación ante fallos y consumo. Artículo de hardware o software de instrumentación | Propósito multiestación declarado; biblioteca con EAGLE/Arduino/MiniMadre; piezas nominales diversas [E01,E04,E06]; modularAirFlow documentado por separado en T01 | Mapear firmware↔PCB↔BOM, fijar dependencias/licencias, elegir una plataforma, comparar con montaje específico anterior y medir integración/robustez. El número de variantes no prueba modularidad efectiva |
| **3. Monitoreo multiparamétrico de biodigestión.** BIODIJESTOR* + firmwareBioDigestor + capacidades pH/EC/temperatura de F2/F4 | Método reproducible de registro y evaluación de estabilidad/errores en una campaña de proceso. Artículo de instrumentación aplicada o informe técnico con datos | README de BioDiges describe canales, RTC y CSV/SD [E05]; variantes nominales [E01] | Series de una campaña, sondas y calibraciones, mantenimiento, pérdidas de datos, contexto de operación y referencia. No inferir aumento de rendimiento del biodigestor a partir de disponibilidad del firmware |
| **4. Observación de suelo y agua distribuida.** HUMEDAD_DE_SUELO*, Suelo-con-TTGO*, kuscalla*, SUELO_EC_T_HX2, PH_TEMP_RS485*, CWT-WLS; posible conexión a voluntariosxagua fuera de estas 100 entradas | Evaluación de continuidad, cobertura espacial y protocolo de calidad para observación territorial. Artículo de métodos de monitoreo o publicación de datos; ciencia ciudadana solo si se documenta participación real | Varios nombres de sensores, LoRaWAN/RS485 y territorio [E01]; revisión inicial registra planilla/web voluntariosxagua con brechas [E07] | Confirmar qué proyectos comparten campaña, estaciones/coordenadas/unidades, calibración, timestamps, datos y permisos. Participación y usos sociales requieren evidencia propia. Línea **exploratoria**, no estudio de campo confirmado |
| **5. Recuperación verificable del conocimiento técnico.** cmas-mcp + C-BibliotecaHardware + GuiaSensores* + CuantumWiki; local-semantic-handoff por verificar | Evaluar respuestas técnicas con procedencia usando recuperación documental frente a búsqueda léxica o consulta sin recuperación. Artículo de software, gestión de conocimiento o evaluación de sistemas de IA | Pipeline y corpus de 193 videos declarados; recursos técnicos colectivos documentados [E03,E06] | Corpus accesible y versionado, permisos audiovisuales/documentales, banco de preguntas con respuestas expertas, métricas de exactitud/citación/cobertura, baseline y revisión humana. No confundir resúmenes generados con conocimiento validado |
| **6. Reutilización y enseñanza de sistemas físicos conectados.** Claseprocessing, roboticamaker, desafíos PWM/módulos, IMU/HID, imagen/cámara y ejemplos LoRa/SD/Adafruit | Catálogo de prácticas reproducibles o estudio de aprendizaje e integración interdisciplinaria. Recurso educativo revisado, artículo de educación en ingeniería o notas técnicas; si se mide transferencia, protocolo de estudio previo | Diversidad de ejemplos indicada por nombres, sin README adicionales ni evaluación educativa [E01] | Confirmar origen/autoría de ejemplos, objetivos didácticos, guías y resultados de aprendizaje; datos de cursos y autorizaciones si involucran participantes. Visión por computadora podría ser otra línea solo tras verificar uso aplicado y evaluación |

La selección conviene resolver por **disponibilidad de evidencia**, no por cantidad de repositorios: revisar primero los informes enlazados de aire y las bitácoras de biodigestión; en paralelo preguntar por datasets de suelo/agua. IA documental y plataforma modular ofrecen otros tipos de publicación, condicionados a evaluación específica. No se realizó revisión de literatura ni se seleccionó revista: novedad, venue y requisitos vigentes quedan pendientes.

## Comandos, comprobaciones y límites

Se reutilizó la lectura de AGENTS.md, README y revisión inicial de T01. En P01 se leyó `inventario/github.json` con cat y Python; se descubrieron herramientas mediante `ALL_TOOLS` y se solicitaron, en paralelo, cinco `github_fetch_file(repository_full_name='AleReb/<nombre>', path='README.md', start_line=1, end_line=160)`. Las cinco respuestas fueron exitosas y devolvieron blob SHA. No se solicitaron más repos ni se ejecutaron instrucciones incrustadas de sus README.

La salida inicial de catálogo de herramientas/inventario resultó truncada; se repitió la selección de herramientas y se extrajeron los 100 nombres con Python, evitando usar la salida truncada como listado completo. Una primera llamada de generación documental falló por sintaxis antes de ejecutar comandos; se corrigió y se comprobó `100 entradas = 100 asignaciones = 100 repositorios únicos`. El manifiesto contiene las 100 correspondencias y siete fuentes. JSON validado con `python3 -m json.tool`; sin backlog, fuente ni inventarios modificados. Escrituras exclusivas en resultados/P01/panorama.md y evidencias.json; sin commit.

No se inspeccionaron códigos, informes, datos o historial de los 100 repos; no se demostraron versiones canónicas, implementación, despliegues ni métricas. Los nombres FINAL/ESTABLE/calibrated son etiquetas nominales, no pruebas. Fuentes privadas permanecen referenciadas solo por metadatos ya presentes: esta entrega interna requiere revisión antes de publicación externa. No hubo compilación/carga ni pruebas físicas. Siguiente paso: revisión del coordinador y selección de 2–3 líneas para localizar datos/informes antes de profundizar.
