# Servidor y webs

## Alcance conocido

El usuario administra https://sensores.cmasccp.cl/ y declara haber creado las webs de cmasudd. Se observó HTTP 200 y HTML inicial con título C+; esto no prueba salud de API ni interfaz completa. No se identificó configuración SSH local en la ruta estándar durante esta revisión.

Los 13 nombres observados en cmasudd están en `inventario/cmasudd.json`. Candidatos de web por nombre: SensorsWebApp, aireAysen, aireaconcagua, auca-cochrane, calidadAgua, giz, monitor, monitorHIRI, voluntariosxagua. La clasificación y el vínculo con dominios deben verificarse; no todos los repos son necesariamente webs ni están desplegados.

## Revisión pública

Por sitio: URL exacta y fuente, repositorio/commit, finalidad, datos de entrada, audiencia, rutas, funciones principales, descarga de datos, errores visibles, accesibilidad básica y captura fechada. Usar navegador con JavaScript cuando esté disponible; si no, registrar límite de HTML inicial. No enviar formularios ni modificar registros durante esta inspección.

Vincular repositorio con despliegue mediante configuración de Pages, workflows, CNAME, manifiestos o evidencia del administrador. No deducir que https://<cuenta>.github.io/<repo>/ existe por el nombre. Revisar paginación del listado y organizaciones relacionadas. Comparar duplicados AleReb/voluntariosxagua y cmasudd/voluntariosxagua.

## Revisión interna de solo lectura

Una vez identificado acceso: registrar host/alias, servicios y versiones, proxy/TLS, procesos/contenedores, repos/commits desplegados, CI/CD, esquema de datos, ingestión de dispositivos, backups y observabilidad. Usar únicamente comandos acotados de lectura compatibles con el sistema identificado. No ejecutar `docker inspect` indiscriminado ni volcar variables/credenciales. Guardar diagramas y referencias, no secretos o dumps.

Reconstruir el recorrido dispositivo → protocolo → ingreso → almacenamiento → API → visualización/exportación. Para cada tramo documentar unidad, timestamp, identificador, validación, errores, reintentos y procedencia. Identificar puntos donde un error técnico podría invalidar una conclusión científica.

Revisar evidencia de backup y restauración histórica. Una prueba de restauración futura debe diseñarse en entorno aislado con copia apropiada. Ensayos de carga, cambios de configuración y reinicios quedan fuera del inventario.

## Resultado

Mapa de arquitectura, catálogo de sitios, matriz proyecto→código→despliegue→dataset, hallazgos con severidad y evidencia, y lista de mejoras separada de hallazgos científicos. Si falta acceso, completar la parte pública y declarar la infraestructura pendiente.
