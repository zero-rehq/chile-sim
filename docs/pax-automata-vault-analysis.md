# Análisis de Pax-Automata para Chile-Sim Vault

## RESUMEN EJECUTIVO

**Pax-Automata** es un agente autónomo que juega Pax Historia (grand strategy game). Su arquitectura es un **cognitive loop** (perceive → remember → reason → act) con persistencia basada en archivos markdown y JSON.

**Relevancia para chile-sim**: Pax-Automata resuelve exactamente el problema que chile-sim enfrenta: cómo mantener estado de juego complejo, multi-turno, sin base de datos, de forma legible y versionable.

---

## QUÉ HACE PAX-AUTOMATA

### Arquitectura de 4 módulos + War Room

```
Browser (Pax Historia)
    ↕ network intercept
Spy → current_state.json, advisor_response.txt, ownership_snapshot.json
        ↓
Brain ← constitution.md, crisis_handbook.txt, strategic_ledger.json
        ↓
Brain → Gemini 2.5 Flash → ActionBatch (Zod-validated)
        ↓
Hand → type actions, submit, advance turn
```

### Módulos

1. **Spy (Percepción)**: Intercepta `/api/simple-chat` del juego, extrae estado limpio, escribe a `current_state.json`
2. **War Room (Memoria)**: Archivos en disco (no DB). Separación clara entre identidad (constitution.md) y plan (strategic_ledger.json)
3. **Brain (Razonamiento)**: Lee todos los War Room files, arma contexto, llama LLM, valida con Zod, actualiza ledger
4. **Hand (Ejecución)**: Playwright para UI automation

---

## PATRONES DE PERSISTENCIA

### 1. **Dual-Document Design** (CRÍTICO)

**Separación entre "quién somos" y "qué estamos haciendo":**

- **constitution.md** (FIJO): Goals, identity, strategic priorities, rules. No cambia durante una run.
- **crisis_handbook.txt** (FIJO): Tactical playbook, doctrines, directive verbs (Acquire, Allocate, Execute)
- **strategic_ledger.json** (DINÁMICO): Active operations, phases, steps, status. Actualizado cada turno por el Brain.

**Ventaja**: Identity y strategy son estables; solo el plan state cambia. El LLM puede actualizar operaciones sin reescribir la identidad.

### 2. **Ownership Snapshot** (EXPLÍCITO)

```json
{
  "our_nation": "USA",
  "regions_we_own": ["California", "Texas", "New York", ...]
}
```

**Por qué**: El Brain necesita una lista EXPLÍCITA de lo que poseemos. "Tenemos tropas ahí" no es suficiente. Solo la lista autorizada cuenta para objetivos de conquista.

**Aplicación a chile-sim**: Crear snapshots explícitos de:
- Regiones controladas
- Infraestructura operativa
- Alianzas activas
- Capacidad estatal por sector

### 3. **Zod en Boundaries** (VALIDACIÓN)

Cada JSON file read/write y cada LLM response se valida con Zod:

```typescript
export const StrategicLedgerSchema = z.object({
  active_operations: z.array(OperationSchema),
});

export const OperationSchema = z.object({
  operation_id: z.string(),
  goal: z.string(),
  current_phase: z.number(),
  steps: z.array(OperationStepSchema),
});

export const OperationStepSchema = z.object({
  phase: z.number(),
  action: z.string(),
  status: z.enum(["COMPLETE", "PENDING", "FAILED"]),
});
```

**Ventaja**: Fail fast con errores claros. No hay datos malformados pasando por el pipeline.

### 4. **Ledger Merge Pattern**

El Brain escribe ANTES de que Hand ejecute. Cuando el LLM retorna `ledger_updates`, se mergea por `operation_id`:
- Operaciones existentes se actualizan in-place
- Nuevas se append
- Si execution se interrumpe, ya persistimos "qué intentamos"

**Aplicación**: Permite rollback parcial y auditoría de intenciones vs ejecución.

### 5. **Context Assembly Determinística**

El Brain es una **pure function** de "lee estos paths":

```typescript
export function assembleContext(): BrainContext {
  const gameState = GameStateSchema.parse(readJson("current_state.json"));
  const constitution = fs.readFileSync("constitution.md", "utf-8");
  const handbook = fs.readFileSync("crisis_handbook.txt", "utf-8");
  const ledger = StrategicLedgerSchema.parse(readJson("strategic_ledger.json"));
  const advisorResponse = fs.readFileSync("advisor_response.txt", "utf-8");
  const ownership = OwnershipSnapshotSchema.parse(readJson("ownership_snapshot.json"));
  return { gameState, constitution, handbook, ledger, advisorResponse, ownership };
}
```

**Ventaja**: Mismo contexto cada vez para los mismos files. Reproducible, debuggable, sin caches mágicos.

### 6. **State Stripping** (LIMPIEZA)

El Spy intercepta el payload del advisor (que incluye system prompt + game state + "guide the player" tail). Extrae SOLO el middle slice:

```typescript
const MAP_HEADER = "*** Description of the Map in the CURRENT Round: ***";
const ADVISOR_TAIL_START = "Remember, it is cruciously important that you guide the player";

function stripAdvisorOnlyContent(prompt: string): string {
  let s = prompt;
  const mapIdx = s.indexOf(MAP_HEADER);
  if (mapIdx !== -1) s = s.slice(mapIdx);
  const tailIdx = s.indexOf(ADVISOR_TAIL_START);
  if (tailIdx !== -1) s = s.slice(0, tailIdx).trimEnd();
  return s;
}
```

**Aplicación**: Cuando el simulador genera eventos mundiales, chile-sim podría parsear y extraer SOLO lo relevante para el estado, descartando wrapper text.

---

## 3-5 IDEAS CONCRETAS PARA CHILE-SIM VAULT

### IDEA 1: Adoptar Dual-Document Design

**Actual en chile-sim:**
- `doctrina/vision-doctrinal.md` (identidad)
- `doctrina/objetivos-largo-plazo.md` (goals)
- `turnos/historial-acciones-completo-2016.md` (acciones ejecutadas)
- `pendientes/pila-estrategica.md` (frentes abiertos)

**Mejora (inspirada en Pax-Automata):**

Crear una separación EXPLÍCITA:

1. **constitution-chile.md** (FIJO, versionado)
   - Síntesis de identidad nacional (doctrina + objetivos)
   - Strategic priorities ordenadas
   - Rules of engagement (qué SÍ, qué NO)
   - Authority hierarchy (qué overrides qué)

2. **strategic-ledger-2016.json** (DINÁMICO, actualizado cada turno)
   ```json
   {
     "active_operations": [
       {
         "operation_id": "OP_NODO_ENERGETICO_BIOBIO",
         "goal": "Consolidar matriz solar-eólica-hidrógeno en Biobío",
         "current_phase": 3,
         "steps": [
           {
             "phase": 1,
             "action": "Lanzar licitación para parques solares Atacama",
             "status": "COMPLETE"
           },
           {
             "phase": 2,
             "action": "Conectar smart grid Biobío-Atacama",
             "status": "PENDING"
           }
         ]
       }
     ]
   }
   ```

3. **Mantener** `historial-acciones-completo-2016.md` como audit log (append-only)

**Ventaja**: El asesor puede leer `strategic-ledger-2016.json` para saber exactamente qué operaciones están activas, en qué fase, y qué está PENDING. No hay que parsear narrativa.

---

### IDEA 2: Ownership Snapshots por Sector

Crear snapshots explícitos de capacidad estatal:

**estado/capacidad-estatal-2016-12-10.json**
```json
{
  "date": "2016-12-10",
  "government": {
    "political_stability": "moderate",
    "legitimacy": "recovering",
    "reform_2017_status": "draft_phase"
  },
  "energy": {
    "solar_capacity_mw": 1200,
    "wind_capacity_mw": 3400,
    "smart_grid_coverage": "35%",
    "hydrogen_projects": ["Atacama pilot"]
  },
  "industry": {
    "microelectronics_facilities": ["Atacama node"],
    "manufacturing_hubs": ["Biobío", "Talcahuano"],
    "components_national_percentage": 18
  },
  "logistics": {
    "ports_automated": ["Valparaíso (partial)"],
    "bioceanic_corridor_status": "negotiation_phase",
    "transit_time_reduction_pct": 12
  },
  "diplomacy": {
    "active_agreements": ["India", "Japón", "Alemania"],
    "missions_abroad": ["Mumbai", "Tokio", "Berlín"]
  }
}
```

**Ventaja**: El asesor sabe EXACTAMENTE qué capacidad tiene Chile sin parsear narrativa. Permite tracking de progreso y bottlenecks.

---

### IDEA 3: Zod Schemas para Validación de Archivos Clave

Crear `vault/schemas.ts` (o similar) con validación:

```typescript
import { z } from "zod";

export const OperationStepSchema = z.object({
  phase: z.number(),
  action: z.string(),
  status: z.enum(["COMPLETE", "PENDING", "FAILED", "BLOCKED"]),
});

export const OperationSchema = z.object({
  operation_id: z.string(),
  goal: z.string(),
  current_phase: z.number(),
  steps: z.array(OperationStepSchema),
});

export const StrategicLedgerSchema = z.object({
  active_operations: z.array(OperationSchema),
});

export const CapacidadEstatalSchema = z.object({
  date: z.string(),
  government: z.object({
    political_stability: z.enum(["low", "moderate", "high"]),
    legitimacy: z.enum(["recovering", "stable", "strong"]),
    reform_2017_status: z.string(),
  }),
  energy: z.object({
    solar_capacity_mw: z.number(),
    wind_capacity_mw: z.number(),
    smart_grid_coverage: z.string(),
    hydrogen_projects: z.array(z.string()),
  }),
  // ... más campos
});
```

**Ventaja**: Cuando el asesor lee `strategic-ledger-2016.json` o `capacidad-estatal-*.json`, puede validar con Zod y fallar rápido si hay inconsistencias. Previene datos corruptos.

**Implementación**: Un script simple que valida archivos JSON antes de que el asesor los lea.

---

### IDEA 4: Advisor Query Template (Dinámico)

Pax-Automata permite que el Brain genere una `next_advisor_query` dinámica cada turno:

```json
{
  "reasoning": "...",
  "actions": [...],
  "ledger_updates": [...],
  "next_advisor_query": "¿Cuál es el estado de las negociaciones con India? ¿Hay riesgos geopolíticos en el Pacífico?"
}
```

**Aplicación a chile-sim**: Crear un archivo `next-advisor-query.txt` que el asesor pueda leer al inicio de cada turno:

```
# Consultas prioritarias para el próximo turno

1. ¿Cuál es el estado actual de la Reforma 2017? ¿Hay resistencia política?
2. ¿Qué riesgos geopolíticos hay en el Pacífico (Taiwán, Corea)?
3. ¿Hay oportunidades de alianza con Brasil o Argentina?
4. ¿Cuál es el estado del corredor bioceánico?
```

**Ventaja**: El asesor sabe qué preguntas responder sin tener que inferirlas. Reduce contexto innecesario.

---

### IDEA 5: Historial de Acciones con Estado Explícito

Pax-Automata usa `status: ["COMPLETE", "PENDING", "FAILED"]` en operaciones. Aplicar esto al historial:

**turnos/historial-acciones-completo-2016.md**

```markdown
## Turno 2016-08-27

**[ESTADO: ENVIADA]** Action Date: 2016-08-27 / Chile lanza el Nodo Energético Biobío...
- Ministerio: Energía
- Impacto estimado: 40% de matriz en renovables para fin 2017
- Quote: "La disciplina técnica no es una opción, es la única vía." — Ministro de Relaciones Exteriores

**[ESTADO: EJECUTADA]** Action Date: 2016-08-27 / Chile inicia fase limitada de exportación de PLCs...
- Ministerio: Economía
- Resultado: 18% de componentes nacionales en manufactura
- Confirmación: Simulador generó evento "Chile establece primer hub de microelectrónica"

## Turno 2016-09-10

**[ESTADO: ENVIADA]** Action Date: 2016-09-10 / Negociación con India para contrato de regalías...
- Ministerio: Relaciones Exteriores
- Impacto estimado: $500M anuales en ingresos
- Quote: "Chile no vende componentes, vende sistemas con continuidad garantizada." — Director AIIEE

**[ESTADO: BLOQUEADA]** Action Date: 2016-09-10 / Reforma constitucional 2017...
- Razón: Capacidad política limitada; postergar a 2017
- Próximo paso: Borrador técnico en enero 2017
```

**Ventaja**: El asesor puede distinguir entre:
- ENVIADA: propuesta al simulador, esperando resolución
- EJECUTADA: confirmada por simulador
- BLOQUEADA: no ejecutada, razón documentada
- FALLIDA: intentada pero fracasó

Permite auditoría clara de intenciones vs realidad.

---

## PATRONES QUE NO ADAPTAR (CÓDIGO PURO)

- Network interception (Spy)
- LLM integration (Brain)
- Playwright automation (Hand)
- Zod validation en runtime (si no hay código)

**Estos son específicos de Pax-Automata porque es un agente autónomo. Chile-sim es un juego humano-dirigido.**

---

## RESUMEN: CÓMO MEJORAR EL VAULT

| Mejora | Inspiración | Esfuerzo | Impacto |
|--------|-------------|---------|--------|
| Adoptar Dual-Document (constitution + ledger) | Pax-Automata | Bajo | Alto — claridad de identidad vs plan |
| Crear ownership snapshots por sector | Pax-Automata | Medio | Alto — tracking de capacidad sin narrativa |
| Validar JSON con Zod schemas | Pax-Automata | Medio | Medio — previene corrupción de datos |
| Dinámico next-advisor-query.txt | Pax-Automata | Bajo | Bajo-Medio — reduce contexto innecesario |
| Historial con estado explícito (ENVIADA/EJECUTADA/BLOQUEADA) | Pax-Automata | Bajo | Alto — auditoría clara |

---

## CONCLUSIÓN

Pax-Automata demuestra que **un vault markdown + JSON bien estructurado es suficiente** para juegos complejos, multi-turno, sin base de datos. Sus patrones clave:

1. **Separar identidad (fija) de plan (dinámico)**
2. **Snapshots explícitos de estado** (no inferir de narrativa)
3. **Validación en boundaries** (Zod)
4. **Ledger merge pattern** (intención antes de ejecución)
5. **Context assembly determinística** (reproducible)

Chile-sim puede adoptar 3-4 de estos sin código, solo reorganizando el vault. El impacto es **claridad, auditoría y debugging más fácil**.
