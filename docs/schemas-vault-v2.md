# Schemas JSON — Vault Upgrade V2

Schemas de validación para los archivos JSON del vault de chile-sim.
Cada campo incluye: nombre, tipo, descripción, ejemplo.

---

### 1. estado/game-state.json

| Campo | Tipo | Descripción | Ejemplo |
|---|---|---|---|
| `fecha_actual` | string (YYYY-MM-DD) | Fecha actual del juego | `"2016-12-24"` |
| `turno_actual` | integer | Número de turno/ronda | `47` |
| `ultimo_estado` | string | Ruta al archivo estado-actual más reciente | `"estado/estado-actual-2016-12-24.md"` |
| `ultimo_handoff` | string | Ruta al handoff-maestro más reciente | `"contexto/handoff-maestro-2016-12-24.md"` |
| `frentes_activos_count` | integer | Cantidad de frentes abiertos | `21` |
| `riesgo_externo` | string (BAJO/MEDIO/ALTO/MEDIO-ALTO) | Nivel de riesgo geopolítico externo | `"MEDIO-ALTO"` |
| `acciones_pendientes` | array[object] | Acciones propuestas, estado ENVIADA | `[{"id": 1, "fecha": "2017-01-05", "titulo": "..."}]` |

**acciones_pendientes[item]:**

| Campo | Tipo | Descripción | Ejemplo |
|---|---|---|---|
| `id` | integer | Número de acción | `1` |
| `fecha` | string (YYYY-MM-DD) | Fecha de ejecución planificada | `"2017-01-05"` |
| `titulo` | string | Título corto de la acción | `"Ingreso legislativo Reforma 2017"` |
| `estado` | string | Estado de la acción | `"ENVIADA"` |

---

### 2. snapshots/energia.json

| Campo | Tipo | Descripción | Ejemplo |
|---|---|---|---|
| `fecha_snapshot` | string (YYYY-MM-DD) | Fecha del snapshot | `"2016-12-24"` |
| `solar_norte_status` | string | Estado del programa solar del norte | `"OPERATIVO"` |
| `eolica_sur_status` | string | Estado del programa eólico del sur | `"OPERATIVO"` |
| `smart_grid_status` | string | Estado de la red inteligente | `"EN_EXPANSION"` |
| `hidrogeno_verde_status` | string | Estado del programa hidrógeno verde | `"FASE_PILOTO"` |
| `nodo_biobio_status` | string | Estado del Nodo Energético Biobío | `"OPERATIVO"` |
| `resiliencia_matriz` | string | Nivel de resiliencia de la matriz | `"ALTA"` |

---

### 3. snapshots/industria.json

| Campo | Tipo | Descripción | Ejemplo |
|---|---|---|---|
| `fecha_snapshot` | string (YYYY-MM-DD) | Fecha del snapshot | `"2016-12-24"` |
| `parque_atacama_status` | string | Estado del Parque Industrial Atacama | `"OPERATIVO"` |
| `plcs_exportados` | integer | PLCs exportados en operación | `50` |
| `cumplimiento_estandares_pct` | string | Porcentaje de cumplimiento de estándares | `"98%"` |
| `soporte_remoto_status` | string | Estado del soporte remoto certificado | `"OPERATIVO"` |
| `certificacion_soberana_status` | string | Estado de certificación soberana | `"ACTIVO"` |
| `expansion_brasil_status` | string | Estado de expansión a Brasil | `"AUDITORIA_EN_CURSO"` |

---

### 4. snapshots/diplomacia.json

| Campo | Tipo | Descripción | Ejemplo |
|---|---|---|---|
| `fecha_snapshot` | string (YYYY-MM-DD) | Fecha del snapshot | `"2016-12-24"` |
| `socios` | object | Estado por socio | `{"india": {...}}` |

**socios[socio]:**

| Campo | Tipo | Descripción | Ejemplo |
|---|---|---|---|
| `status` | string | Estado general de la relación | `"ACTIVO"` |
| `nivel_confianza` | string (FIRME/EN_NEGOCIACION/ESPECULATIVA) | Nivel de confianza diplomática | `"FIRME"` |
| `ultimo_hito` | string | Último logro concreto | `"Transferencia Operativa Nivel 2 aceptada"` |
| `proxima_accion` | string | Próxima acción planificada | `"Certificación ingenieros febrero 2017"` |

---

### 5. snapshots/fiscal.json

| Campo | Tipo | Descripción | Ejemplo |
|---|---|---|---|
| `fecha_snapshot` | string (YYYY-MM-DD) | Fecha del snapshot | `"2016-12-24"` |
| `peso_rango` | string | Rango del peso chileno por dólar | `"650-655"` |
| `estabilidad_peso` | string | Nivel de estabilidad cambiaria | `"ESTABLE"` |
| `regla_fiscal_status` | string | Estado de la regla fiscal estructural | `"ACTIVA"` |
| `fondo_uba_usd_millones` | integer | Fondo de Compensación UBA en millones USD | `150` |
| `presupuesto_reforma_2017_usd_millones` | integer | Presupuesto Reforma 2017 en millones USD | `280` |

---

### 6. snapshots/logistica.json

| Campo | Tipo | Descripción | Ejemplo |
|---|---|---|---|
| `fecha_snapshot` | string (YYYY-MM-DD) | Fecha del snapshot | `"2016-12-24"` |
| `trazabilidad_corredor_pct` | string | Trazabilidad Mato Grosso-Valparaíso | `"99.8%"` |
| `reduccion_tiempos_transito_pct` | string | Reducción de tiempos desde Mato Grosso | `"12%"` |
| `ventanilla_unica_status` | string | Estado Ventanilla Única Aduanera | `"PILOTO_ACEPTADO"` |
| `agua_negra_status` | string | Estado del Túnel Agua Negra | `"MANTENIMIENTO_PREVENTIVO"` |
| `puertos_inteligentes` | array[string] | Puertos con automatización activa | `["Valparaíso", "San Antonio", "Coquimbo"]` |
| `misiones_tecnicas_activas` | integer | Misiones técnicas permanentes en operación | `3` |
