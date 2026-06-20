> **Nota sobre correcciones:** Se incorporó la fila de instrucciones por columna que había sido omitida en la versión anterior. Los 6 campos que estaban vacíos en la hoja original han sido completados con la notación *(campo inferido)*, derivados de la lógica interna del documento. Valídalos antes de usar en producción.

---

## Tablero de Priorización

| Causa | Fase DT origen (E/D/I) | Insight de empatía | Supuesto central | Pregunta analítica | Variables (nombres exactos) | Tipo (Outcome / Explic / Control / Segmento) | Cálculo / Transformación | Métrica (nombre + fórmula) | Periodo / Segmento | Patrón esperado (si cierta) | Condición de refutación | Valor esperado para usuario/ciudadano | Riesgo si falsa | Acción si confirma | Acción si refuta | Experimento analítico mínimo (query + visual 1 línea) | Estado (V/A/R) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ¿Qué crees que está pasando "detrás" del síntoma? Debe sonar a mecanismo, no a queja. | ¿De qué momento de Design Thinking salió? | Una observación/cita corta que te inspiró la causa. | ¿Qué crees que une la causa con el resultado? Es la "apuesta". | Forma neutra y medible de la causa. Debe admitir "Sí/No" o "Mayor/Menor". | Columnas que usarás tal cual aparecen en la base (no inventes nombres). | Etiqueta cada variable: 1. Outcome: lo que quieres explicar (ej. `recompra_30d`). 2. Explic (explicativa): lo que crees que causa (ej. `comentario_malestar`). 3. Control: cosas que pueden distorsionar (ej. `canal`). 4. Segmento: variable para cortar resultados (ej. `canal`, `zona`). | Operaciones necesarias antes de la métrica final. | Nombre corto + cómo se calcula. | Rango temporal y cortes. | La condición numérica que esperas ver si tu causa es real. | El rango / comparación que tiraría tu hipótesis. Debe ser diferente (no repetir con "no"). | Beneficio concreto si confirmas la hipótesis (en lenguaje humano). Clavo: debería sonar a mejora perceptible, no a KPI interno. | Qué perderías si sigues insistiendo en esta causa equivocada. Esto ayuda a priorizar falsar rápido. | Movimiento específico inmediato (no "optimizar estrategia"). Debe ser ejecutable en la organización. | Ruta alternativa (no repetir la de confirmar). | Qué harás para probarla en pequeño. | Semáforo: 1. V (Verde) = todos los campos listos (se puede correr hoy). 2. A (Amarillo) = falta 1 cosa (umbral, nombre exacto o acción). 3. R (Rojo) = falta variable clave o patrón; no avanzar. |
| Estigmatización mutua (Invasor vs. Usurpador) y ruptura total de la confianza entre vecinos del territorio. | Definir | Los propietarios privados de grandes extenciones de tierra en el norte del Cauca se sienten frustrados y prefieren vender sus predios antes de continuar con una lucha constante ante entidades jurídicas y gubernamentales, perdidas de capital que genera las continuas confrontaciones con las comunidades indigenas y afrocolombianas por mantener sus titulos de propiedad privada. | Si logramos institucionalizar espacios de reconocimiento humano mutuo donde el propietario sea validado como un productor legítimo y el comunero como un actor territorial con derechos históricos, Entonces la estigmatización bajo las etiquetas de 'Invasor' y 'Usurpador' perderá su poder movilizador en el Norte del Cauca, Porque al humanizar al adversario se elimina la barrera moral que justifica la confrontación, permitiendo que la seguridad jurídica deje de depender de la fuerza pública y pase a depender de la legitimidad social compartida. | ¿Es el reconocimiento mutuo de la legitimidad —el propietario como productor y el comunero como actor histórico— una base lo suficientemente sólida para sustituir la seguridad armada por la paz social, o puede la 'humanización del adversario' ser interpretada por las partes no como una vía de convivencia, sino como una debilidad estratégica que pone en riesgo sus derechos fundamentales y su identidad territorial? | 1. Confianza Percibida `perceived_trust_score` 2. Gobernanza Territorial `territorial_governance_index` 3. Continuidad del Negocio `business_continuity_status` 4. Interdependencia Cooperativa `cooperative_interdependence_level` 5. Legitimidad y Estabilidad `land_legitimacy_stability_rate` 6. Presencia de Actores Armados `armed_groups_presence_flag` 7. Simetría en el Diálogo `dialogue_symmetry_coefficient` | 1. Outcome: `land_legitimacy_stability_rate`, `business_continuity_status` 2. Explicativa: `cooperative_interdependence_level`, `territorial_governance_index` 3. Control: `armed_groups_presence_flag` 4. Segmento: `dialogue_symmetry_coefficient`, `perceived_trust_score` | 1. Interdependencia Cooperativa (IC) 2. Simetría en el Diálogo (SD) 3. Confianza Percibida (CP) 4. Gobernanza Territorial (GT) 5. Presencia de Actores Armados (AA) — Variable de Control 6. Integración Final: Cálculo del IEL | `IEL = Δ(land_legitimacy_stability_rate) / Δ(cooperative_interdependence_level)` — Índice de Elasticidad de la Legitimidad *(campo inferido)* | semestral | 1 | **0.012** | Los propietarios de terrenos se sentiran mas seguros y felices de poder proteger su derecho sobre dichos predios | se perderia la credibilidad y la confianza que haría que se intensifique la confrontación entre los diferentes actores, llevando a perdidas económicas muy significativas | firmar los acuerdos económicos que garanticen los recursos para colocar en marcha el plan de productividad de genere el bienestar para todos los actores involucrados | No seguir insistiendo en dar insentivos ecónomicos sino un reconocimiento moral sobre las propiedades, haciendo que los implicados disminuyan la confrontación | [Ver bloque de código 2] *(campo inferido)* | A — Amarillo: falta umbral exacto en fórmula IEL *(campo inferido)* |

---

## Ficha de Indicador

| Supuesto central | Paso 1 — ¿QUÉ HAGO? (Acción) | Paso 1 — ¿CÓMO LO HAGO? (Método) | Paso 1 — ¿PARA QUÉ LO HAGO? (Propósito) | Paso 2 — Aspecto específico a Medir | Paso 2 — Público objetivo (Para quién) | Paso 2 — Dimensión (Marca una) | Paso 3 — **Nombre del indicador** | Paso 3 — Numerador (Variable Y) | Paso 3 — Denominador (Población) | Paso 3 — Fórmula (Matemática) | Paso 3 — Prueba de estrés | Paso 4 — Tipo (Marca una) | Paso 5 — Frecuencia de medición | Paso 5 — Fuente de datos (Verificación) | Paso 6 — Línea base (Patrón actual) | Paso 6 — Patrón esperado (Meta) | Paso 6 — **Condición de refutación (Fallo)** |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Si logramos institucionalizar espacios de reconocimiento humano mutuo donde el propietario sea validado como un productor legítimo y el comunero como un actor territorial con derechos históricos, Entonces la estigmatización bajo las etiquetas de 'Invasor' y 'Usurpador' perderá su poder movilizador en el Norte del Cauca, Porque al humanizar al adversario se elimina la barrera moral que justifica la confrontación, permitiendo que la seguridad jurídica deje de depender de la fuerza pública y pase a depender de la legitimidad social compartida. | Construir y calibrar el Índice de Elasticidad de la Legitimidad (IEL) como North Star Metric de sostenibilidad territorial *(campo inferido)* | [Ver bloque de código 1] | Para determinar la viabilidad ética y operativa del modelo de negocio en el territorio. A. Validación de Inversión: Identificar si el capital invertido está comprando "paz temporal" (frágil y cara) o construyendo "estabilidad orgánica" (sostenible y rentable). B. Neutralización del Conflicto: Desmitificar si el dinero es un lenguaje universal o si existen barreras identitarias que requieren una intervención política/social antes que una económica. C. Mitigación de Riesgos: Anticipar rupturas en la Continuidad del Negocio detectando caídas en la Legitimidad antes de que se traduzcan en violencia o bloqueos operativos. | El "Índice de Conversión de Beneficio en Legitimidad" (ICBL). No mediremos solo cuánto dinero fluye (Interdependencia), sino cuánta legitimidad se "compra" por cada unidad de beneficio económico distribuido. Este indicador permite detectar el fenómeno de "cooptación": si el beneficio sube pero la legitimidad se estanca o baja, el incentivo económico ha fallado como neutralizador del agravio histórico. Punto Crítico: La correlación entre la Continuidad del Negocio y la Confianza Percibida. | Gestores de Sostenibilidad y Negociadores de Alto Nivel. El reporte está diseñado para quienes tienen el poder de ajustar las reglas del juego (Gobernanza Territorial) y la distribución del valor. A nivel interno: Directores de Riesgo y Operaciones que necesitan saber si el negocio es viable a largo plazo. A nivel externo: Líderes de las comunidades en conflicto que necesitan demostrar a sus bases que la "Prosperidad Compartida" no es una traición a su identidad, sino una victoria táctica. | Eficacia (¿Logra el resultado?) | **Índice de Elasticidad de la Legitimidad (IEL)** | `Δ(land_legitimacy_stability_rate)` — Cambio semestral en la tasa de legitimidad y estabilidad territorial percibida *(campo inferido)* | `Δ(cooperative_interdependence_level)` — Cambio semestral en el nivel de interdependencia cooperativa (transacciones + empleos entre actores en conflicto) *(campo inferido)* | `IEL = Δ(land_legitimacy_stability_rate) / Δ(cooperative_interdependence_level) × (1 − armed_groups_presence_flag)` *(campo inferido)* | Prueba de Estrés (Riesgo Matemático): El Efecto de Saciedad. Si la Interdependencia (beneficio) llega a un techo, el denominador se estanca. Si la legitimidad cae por un evento externo (agravio histórico reavivado), la fórmula arrojará un valor negativo que puede ser difícil de interpretar sin un histórico de línea base. | Índice | Semestral: Cada seis meses. | 1. Fundación Ideas para la Paz (FIP) — Variable Clave: `perceived_trust_score` / `dialogue_symmetry_coefficient`. Es la fuente más relevante para medir la dimensión humana. A través de su herramienta de Confianza Empresa-Comunidad, la FIP permite transformar sentimientos abstractos en métricas cuantitativas. 2. Índices de Continuidad (GTC-ISO 22313 / ICONTEC) — Variable Clave: `business_continuity_status` / `land_legitimacy_stability_rate`. Esta fuente es puramente operativa y técnica. Utilizar los estándares de la Guía Técnica Colombiana (GTC) permite medir la estabilidad del predio de manera objetiva. 3. Defensoría del Pueblo (Sistema de Alertas Tempranas - SAT) — Variable Clave: `armed_groups_presence_flag` / `territorial_governance_index`. Esta es la fuente de control necesaria para filtrar el "ruido" político y criminal del Cauca. Sus reportes son los más precisos sobre la dinámica de grupos armados en municipios específicos. | 0.013 | 1 | **0.012** |

---

[Ver bloque de código 1]

```
Implementando un Sistema de Telemetría Social y Operativa basado en tres capas de datos:

A. Definición de la Métrica Maestra (North Star Metric)

B. Recolección de Datos (Data Ingestion)
   * Datos Duros (Cuantitativos): Registra la Continuidad del Negocio (días sin paros)
     y la Interdependencia (volumen de transacciones/empleos entre bandos)
   * Datos Blandos (Cualitativos): Aplica encuestas de pulso (Pulse Surveys) a los actores
     para cuantificar la Confianza Percibida y la Legitimidad
   * Proxy de Simetría: Mide el ratio de acuerdos logrados por consenso
     vs. acuerdos impuestos por una sola vía

C. Análisis de Correlación
   Utiliza una matriz de dispersión para observar el comportamiento de la Confianza
   a medida que sube el Beneficio Económico:
   - Si la Confianza sube con el Beneficio: Éxito (Prosperidad Compartida).
   - Si la Confianza baja mientras el Beneficio sube: Alerta (Cooptación/Capitulación).
```

---

[Ver bloque de código 2] *(campo inferido)*

```sql
-- Experimento analítico mínimo: correlación Interdependencia vs. Legitimidad
SELECT
    dialogue_symmetry_coefficient,
    AVG(land_legitimacy_stability_rate)     AS avg_legitimidad,
    AVG(cooperative_interdependence_level)  AS avg_interdependencia,
    AVG(perceived_trust_score)              AS avg_confianza,
    MAX(armed_groups_presence_flag)         AS presencia_armada
FROM territorio_norte_cauca
WHERE periodo = 'semestral'
GROUP BY dialogue_symmetry_coefficient
ORDER BY dialogue_symmetry_coefficient;
-- Visual sugerido: scatter plot Interdependencia (eje X) vs. Legitimidad (eje Y),
--                 segmentado por colour = dialogue_symmetry_coefficient
```

---

## Supuestos Pendientes

| Supuesto | Estado |
|---|---|
| [Escribe tu supuesto 2] | Pendiente |
| [Escribe tu supuesto 3] | Pendiente |
