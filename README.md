# Índice de Cohesión y Legitimidad Territorial (ICLT) — Base Predios, Norte del Cauca

**Unidad de análisis:** predio (`ID_Predio`) · **Llave:** `Codigo_Dane_Municipio`
**Período base:** 2025-01-01 a 2025-12-31 · **Período de observación:** 2025-06-01 a 2025-12-31

---

## 1. Tabla resumen de la métrica

**Fórmula:** `ICLT = (1 − (Σ Hectáreas invadidas / Σ Hectáreas totales)) × 100`

### 1.1 Resultado global

| Indicador | Valor |
|---|---|
| Predios totales (N) | 50 |
| Hectáreas totales de la región | 5,047.0 ha |
| Hectáreas invadidas (`Reporte_Invasion_Activo=1`) | 3,770.0 ha |
| Hectáreas saneadas y consensuadas (numerador conceptual) | 1,277.0 ha |
| **ICLT** | **25.30** |

Interpretación directa: solo el **25.3%** del área total de los 7 municipios está libre de reporte activo de invasión; el 74.7% restante está bajo disputa activa. Es un punto de partida bajo para la hipótesis — el "piso" de paz social medido en hectáreas es todavía reducido.

### 1.2 Desagregado por municipio (ordenado de menor a mayor ICLT)

| Municipio | Predios | Ha. totales | Ha. invadidas | Ha. saneadas/consensuadas | ICLT |
|---|---|---|---|---|---|
| Corinto | 7 | 1,000 | 825 | 175 | 17.50 |
| Caloto | 8 | 865 | 710 | 155 | 17.92 |
| Guachené | 7 | 507 | 385 | 122 | 24.06 |
| Puerto Tejada | 7 | 538 | 400 | 138 | 25.65 |
| Miranda | 7 | 862 | 635 | 227 | 26.33 |
| Padilla | 7 | 545 | 365 | 180 | 33.03 |
| Santander de Quilichao | 7 | 730 | 450 | 280 | 38.36 |

Corinto y Caloto son los municipios con menor legitimidad territorial medida por esta vía (mayor proporción de hectáreas bajo invasión activa); Santander de Quilichao y Padilla muestran la situación relativamente menos crítica, aunque ningún municipio supera 40 puntos.

---

## 2. Diccionario de datos — `predios_ICLT_final.csv`

| Variable | Descripción | Tipo | Origen |
|---|---|---|---|
| `ID_Predio` | Identificador único del predio | Texto | Fuente original |
| `Municipio` | Municipio donde se ubica el predio | Texto | Fuente original |
| `Codigo_Dane_Municipio` | Código DIVIPOLA-DANE del municipio (llave del análisis) | Numérico | Fuente original |
| `Fecha_Reporte` | Fecha del reporte del predio, estandarizada a AAAA-MM-DD | Fecha | Fuente original (verificada, sin reformateo necesario) |
| `Extension_Hectareas` | Extensión del predio en hectáreas | Numérico | Fuente original |
| `Tipo_Titulo_Vigente` | Tipo de título vigente: Privado, Privado (Agroindustria), Consejo Comunitario, Resguardo Indígena | Categórico | Fuente original |
| `Superposicion_Derechos` | 1 = existe superposición de derechos sobre el predio, 0 = no | Binario | Fuente original |
| `Reporte_Invasion_Activo` | 1 = reporte de invasión activo, 0 = no. **Insumo directo del numerador del ICLT** | Binario | Fuente original |
| `Evento_Periodo_Observacion` | 1 = el predio tuvo su reporte (`Fecha_Reporte`) dentro del período de observación 2025-06-01 a 2025-12-31; 0 = el reporte cae en 2025-01-01–2025-05-31 | Binario | **Calculado** en este pipeline |

---

## 3. Reporte de transformaciones

| Paso | Acción | Resultado |
|---|---|---|
| Carga | Se leyeron únicamente las 8 columnas permitidas de la hoja `Predios` | 50 filas iniciales |
| Fechas | Conversión/verificación de `Fecha_Reporte` a AAAA-MM-DD | 0 fechas no parseables |
| Duplicados | Eliminación de duplicados exactos (todas las columnas permitidas idénticas) | 0 duplicados eliminados |
| Nulos críticos | Verificación de nulos en `ID_Predio`, `Codigo_Dane_Municipio`, `Fecha_Reporte`, `Extension_Hectareas`, `Reporte_Invasion_Activo` | 0 nulos en todas |
| Filtro período base | Se conservan solo filas con `Fecha_Reporte` entre 2025-01-01 y 2025-12-31 | 0 filas excluidas (todo el dataset ya cae en 2025) |
| Columna derivada | `Evento_Periodo_Observacion` = 1 si `Fecha_Reporte` ∈ [2025-06-01, 2025-12-31] | 24 predios = 1, 26 predios = 0 |
| Columnas no usadas | No se aplicó ninguna regla de eliminación por errores en columnas fuera del alcance permitido (no aplica: el dataset de entrada ya estaba limitado a las 8 columnas) | — |
| Cálculo ICLT | Σ hectáreas por condición de invasión, sobre las 50 filas finales | ICLT global = 25.30 |

**Filas iniciales:** 50 · **Filas finales:** 50 · **Duplicados eliminados:** 0 · **Nulos críticos:** 0 · **Una fila por predio:** ✅ confirmado (50 `ID_Predio` únicos = 50 filas)

### Muestra de 5 predios (verificación manual)

| ID_Predio | Municipio | Fecha_Reporte | Ha. | Superpos. | Invasión | Evento_Obs |
|---|---|---|---|---|---|---|
| CO-006 | Corinto | 2025-06-05 | 400 | 1 | 1 | 1 |
| GU-003 | Guachené | 2025-06-02 | 55 | 0 | 0 | 1 |
| PA-002 | Padilla | 2025-02-17 | 15 | 0 | 0 | 0 |
| PT-004 | Puerto Tejada | 2025-05-21 | 65 | 1 | 0 | 0 |
| SQ-003 | Santander de Quilichao | 2025-05-08 | 45 | 0 | 0 | 0 |

### Advertencias de calidad

1. **2 predios con invasión activa pero sin superposición de derechos registrada:** `PA-005`, `PT-001`. No es necesariamente un error — invasión física y disputa legal de derechos son fenómenos distintos — pero conviene revisarlos si el equipo de campo esperaba que ambas variables coincidieran.
2. **6 predios con superposición de derechos pero sin invasión activa:** `CA-005`, `CO-007`, `MI-006`, `PA-001`, `PT-004`, `SQ-007`. Consistente con casos de disputa legal/administrativa que aún no escalan a ocupación física.
3. **Posibles valores atípicos de extensión** (`|z|>2`): `CA-008` (300 ha), `CO-001` (320 ha), `CO-006` (400 ha) — los tres son predios "Privado (Agroindustria)", por lo que el tamaño es plausible dado el tipo de título; se documenta como atípico estadístico, no como error de captura.
4. Ningún predio individual concentra más del 15% de las hectáreas invadidas totales, así que el ICLT global no depende de un solo registro extremo.

---

## 4. Supuestos aplicados

1. **Alcance de "invadidas":** el numerador de la fracción (`Σ Hectáreas invadidas`) se construyó como la suma de `Extension_Hectareas` de todos los predios con `Reporte_Invasion_Activo = 1`. `Superposicion_Derechos` se dejó fuera de la fórmula porque tu especificación solo nombra "invadidas"; si quieres una versión que also castigue la superposición legal (sin ocupación física), es un ajuste de una línea y te la dejo lista si la necesitas.
2. **"Saneadas y consensuadas" = complemento aritmético:** interpreté tu indicación de que el numerador conceptual es "Hectáreas saneadas y consensuadas" como el complemento de las invadidas (`Total − Invadidas`), ya que la fórmula que diste (`1 − invadidas/total`) matemáticamente aísla ese complemento. No existe en la base una variable explícita de "saneamiento" o "consenso" documentado como proceso (p. ej. fecha de acuerdo, acta de conciliación); si tu equipo tiene esa variable en otra fuente, el índice se puede refinar para usarla directamente en vez de inferirla como resta.
3. **Período base vs. período de observación:** todas las 50 filas ya caían dentro del período base 2025-01-01 a 2025-12-31, por lo que no hubo exclusiones. El ICLT global se calculó sobre el período base completo (todo el año), no solo sobre el período de observación; la columna `Evento_Periodo_Observacion` se entrega como variable derivada disponible para análisis de segundo semestre, pero no se usó para filtrar el cálculo de la métrica salvo que tú lo pidas explícitamente.
4. **"Usuario" = "predio":** tu plantilla original usa el término "usuario"; dado que definiste la unidad de análisis como el predio, todas las reglas de "1 fila por usuario", "evento del usuario", etc. se aplicaron tomando `ID_Predio` como la entidad.
5. **Superposicion_Derechos y Reporte_Invasion_Activo se trataron como variables independientes**, no mutuamente excluyentes ni jerárquicas (ver advertencias de calidad, punto 1 y 2).
6. **Nota de nomenclatura:** en tu proyecto ya existe un ICLT construido como `Cp × Sd × Co` sobre microdatos de la ECP 2023 (encuesta de percepción). Este ICLT es una construcción distinta — basada en hectáreas físicas de predios, no en percepción encuestada — aunque comparte nombre y tema. Vale la pena que decidas si son (a) dos índices complementarios (uno de percepción, uno "duro" de tenencia física) que se reportan por separado, o (b) si uno de los dos debería renombrarse para evitar ambigüedad en el informe final.

---

## Archivo entregado

`predios_ICLT_final.csv` — 50 filas (una por predio), 9 columnas (las 8 originales + `Evento_Periodo_Observacion`).
