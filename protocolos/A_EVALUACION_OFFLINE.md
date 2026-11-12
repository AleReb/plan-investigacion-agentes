# A — Protocolo preliminar de evaluación fuera de producción

Versión 0.1, 2026-11-12. Diseño propuesto por coordinador a partir de V02; **no ejecutado**. No constituye protocolo científico final ni cierre de T09. Se requiere revisión de literatura enfocada y resolver semántica con responsables antes de afirmar mejoras sobre datos reales.

## Objetivo y alcance

Evaluar cómo dos exportadores existentes preservan o transforman observaciones ambientales frente a un contrato explícito. Unidad de prueba: escenario con entradas fijadas, perfil, corte temporal y salida esperada. Dos casos de implementación, no muestra representativa de todos los sistemas ambientales.

Baselines: blobs aire `e642b5897a5c0927e6b71a00fbd29a15bffad7d4` y agua `9b860d7f3b0eb15a1a81ee2efdda9ca8fed9f066`, junto a configuraciones/pruebas de V02. Fijar además commits que contengan los blobs y versiones de Python/dependencias. Consultar versiones leídas, no sustituir por main sin registrar cambio.

Primera fase: verificación del comportamiento actual con escenarios sintéticos, sin implementar aún un exportador nuevo. Segunda fase opcional: contrato y adaptadores explícitos; comparar sobre las mismas entradas. Un hallazgo estático no se convertirá en fallo probado hasta ejecutar el escenario correspondiente.

## Aislamiento

Trabajar en resultados/A01 con scripts propios y copias temporales de fuentes públicas; preservar hashes. No importar ni ejecutar main, db, env, load_env_file, publicadores o workflows sin aislamiento comprobado. Sustituir acceso a base por dobles de prueba que rechacen conexiones reales; toda salida en directorio temporal. No leer .env ni disponer de credenciales; registrar y negar intentos de red. Extraer funciones por AST si permite evaluar el comportamiento original sin dependencias externas, documentando esa limitación: no sería ejecución integral del programa.

No versionar secretos o bases reales. Los fixtures sintéticos se etiquetan como tales y jamás se presentan como mediciones de campo. Revisar procedencia/licencias antes de redistribuir código ajeno completo; se prefieren referencias por hash y scripts de preparación.

## Escenarios y oráculo independiente

El oráculo se define antes de ejecutar cada caso y no se deriva de la salida del programa. Diferenciar expectativa contractual de comportamiento histórico deliberado.

| Grupo | Casos | Qué observar |
| --- | --- | --- |
| Identidad y colisiones | Dos sensores misma estación/variable/hora; dos registros de una fuente con fecha repetida | Registros conservados, seleccionados o sustituidos; determinismo bajo órdenes permitidos |
| Calidad | Sentinela -1, null cuando tipo lo permita, NaN/Inf, límites de filtros y variables no presentes | Valores/faltantes, rechazo o excepción, motivo recuperable; no inventar rango físico correcto |
| Transformación | SO₂×1000; redondeo en perfil agua; conversiones distintas por modelo | Error numérico frente a pares predefinidos, metadatos de unidad y regla |
| Tiempo | Diciembre, bisiesto, límite mensual, hora repetida/ausente y tipos de timestamp | Inclusión/exclusión, ambigüedades pendientes; sin asignar zona de origen por suposición |
| Reciente | Mes nuevo vacío; variable antigua fuera de ventana; sensores duplicados | Diferencia entre último global, último de ventana y último de mes; antigüedad/ausencia |
| Volumen | 4999, 5000 y 5001 registros; frontera de tamaño de partición | Omisiones, repetidos, partes vacías y bytes efectivos |
| Publicación | Repetición con misma entrada; interrupción entre archivos | Estabilidad de datos, generación mezclada y recuperación; distinguir archivo atómico de instantánea completa |

Comenzar A01 con tres escenarios mínimos: colisión, sentinela/finitud y frontera de partición. Extender tras revisión. Los casos que requieren controlador SQL o publicación integral se registran aparte y no se declaran cubiertos por un doble de prueba simplificado.

## Registro y métricas

Por corrida: hash fuente/fixture, perfil, versión del evaluador, plataforma, criterio/oráculo, comando, salida, excepciones, conteos y estado observado. Contabilizar cada entrada como conservada, transformada, rechazada, sustituida o no explicada. Medir fracción sin destino/decisión explicable, discrepancias de valor/unidad, colisiones sin política, campos de procedencia retenidos y reproducibilidad de archivos de datos.

Separar generated_at de observed_through: metadatos de ejecución pueden variar sin invalidar identidad de datos. Usar hashes de artefactos pertinentes y documentar campos excluidos; no normalizar silenciosamente diferencias. Tiempos/memoria, si se miden, requieren repeticiones y entorno fijado; no extrapolarlos a producción.

## Interpretación y puertas

Una discrepancia con el contrato es un resultado del escenario, no prueba de incidente real. No atribuir datos perdidos a producción sin muestra y evidencia. Para alegar utilidad práctica, añadir una muestra real autorizada por perfil y contabilización origen→salida, más costo de adaptación/mantenimiento. Dos implementaciones no justifican generalización universal.

Aceptar A01 cuando sea reproducible, versiones verificadas, aislamiento comprobado, oráculos explícitos y resultados tanto favorables como desfavorables conservados. Si el contrato no resuelve diferencias concretas o no aporta frente a antecedentes, reformular como caso técnico. Publicación científica queda condicionada a pregunta diferenciada, literatura suficiente y evaluación pertinente.
