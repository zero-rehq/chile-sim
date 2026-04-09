# Vault Upgrade V2 — Reorganización Estructural de chile-sim

## TL;DR

> **Quick Summary**: Implementar 7 mejoras estructurales al vault de chile-sim inspiradas en Pax-Automata, Graphify y oh-my-openagent para hacerlo completamente stateless, auditable y eficiente para agentes AI.
> 
> **Deliverables**:
> - 1 archivo JSON de game-state (boulder)
> - 5 archivos JSON de snapshots por sector
> - 1 archivo de wisdom accumulation
> - 1 archivo de nodos dios (pilares críticos)
> - 3 mini-AGENTS.md jerárquicos
> - Ediciones a 3 archivos existentes (estado-actual, acuerdos-y-canales, AGENTS.md, README.md)
> 
> **Estimated Effort**: Medium (15 file operations)
> **Parallel Execution**: YES - 3 waves
> **Critical Path**: Task 1 (schemas) → Tasks 2-7 (parallel) → Task 8-9 (docs)

---

## Context

### Original Request
El usuario quiere mejorar el vault de chile-sim adoptando patrones de tres repos open source para hacerlo más robusto, stateless y eficiente.

### Interview Summary
**Key Discussions**:
- Timing: implementar AHORA, antes de seguir jugando (juego pausado en 24 dic 2016)
- Alcance: las 7 mejoras completas
- Formato: JSON para estado rápido + markdown para narrativa

**Research Findings**:
- Pax-Automata: dual-document design, snapshots por sector, schemas de validación
- Graphify: wikilinks, confianza en relaciones, god nodes, diff entre snapshots
- oh-my-openagent: boulder state, wisdom accumulation, AGENTS.md jerárquicos

### Metis Review
**Identified Gaps** (addressed):
- Boulder naming conflict: `.sisyphus/boulder.json` ya existe como tracker de Sisyphus → game boulder va en `estado/game-state.json`
- Duplicación de tablas de frentes en 3 archivos → `pila-estrategica.md` es la fuente canónica
- CLAUDE.md inconsistente con AGENTS.md → fuera de scope, se documenta pero no se toca
- Schemas indefinidos → se definen como primera tarea antes de crear archivos
- Archivos stale acumulados → fuera de scope (tarea separada)

---

## Work Objectives

### Core Objective
Hacer que el vault de chile-sim sea completamente stateless, auditable y eficiente: cualquier agente nuevo debe poder entender el estado completo del juego leyendo 3-4 archivos, sin depender de memoria de sesión.

### Concrete Deliverables
- `estado/game-state.json` — punto de entrada rápido
- `snapshots/energia.json`, `snapshots/industria.json`, `snapshots/diplomacia.json`, `snapshots/fiscal.json`, `snapshots/logistica.json`
- Sección delta en `estado/estado-actual-2016-12-24.md`
- Marcadores de confianza en `diplomacia/acuerdos-y-canales.md`
- `contexto/wisdom.md`
- `estado/nodos-dios.md`
- `diplomacia/AGENTS.md`, `doctrina/AGENTS.md`, `estado/AGENTS.md`
- Secciones nuevas en `AGENTS.md` y `README.md`

### Definition of Done
- [x] Todos los JSON validan con `python3 -m json.tool`
- [x] `game-state.json` tiene campos: fecha_actual, turno_actual, acciones_pendientes, ultimo_handoff
- [x] 5 snapshots JSON existen y tienen datos del estado al 24/12/2016
- [x] `estado-actual-2016-12-24.md` tiene sección "Qué cambió" en las primeras 20 líneas
- [x] `acuerdos-y-canales.md` tiene marcadores [FIRME], [EN NEGOCIACIÓN] o [ESPECULATIVA]
- [x] `wisdom.md` tiene entradas estructuradas con fecha y dominio
- [x] `nodos-dios.md` tiene exactamente 5-7 nodos
- [x] 3 mini-AGENTS.md existen y tienen ≤25 líneas cada uno
- [x] `AGENTS.md` raíz referencia las 7 mejoras
- [x] `README.md` actualizado con nueva estructura

### Must Have
- Schemas JSON definidos ANTES de crear archivos
- Game boulder en `estado/game-state.json` (NO en `.sisyphus/`)
- `pila-estrategica.md` como fuente canónica de frentes (no duplicar)
- Mini-AGENTS.md que NO contradigan el AGENTS.md raíz

### Must NOT Have (Guardrails)
- NO modificar archivos en `doctrina/` (contenido fuera de scope)
- NO modificar `turnos/historial-acciones-completo-2016.md`
- NO modificar `.sisyphus/boulder.json` (tracker de Sisyphus, no game state)
- NO modificar `CLAUDE.md` (fuera de scope)
- NO crear narrativa de juego nueva ni contenido doctrinal
- NO crear más de 5 snapshots sectoriales
- NO crear más de 3 mini-AGENTS.md
- NO reescribir AGENTS.md — solo AGREGAR secciones nuevas
- NO archivar archivos viejos (tarea separada)

---

## Verification Strategy

> **ZERO HUMAN INTERVENTION** — ALL verification is agent-executed.

### Test Decision
- **Infrastructure exists**: NO (no hay test framework)
- **Automated tests**: None — verificación por comandos bash
- **Framework**: bash + python3 -m json.tool

### QA Policy
Cada tarea incluye comandos de verificación ejecutables.

---

## Execution Strategy

### Parallel Execution Waves

```
Wave 1 (Foundation — schemas y game-state):
├── Task 1: Definir schemas JSON para todos los archivos nuevos [quick]
├── Task 2: Crear estado/game-state.json [quick]

Wave 2 (Core improvements — MAX PARALLEL):
├── Task 3: Crear snapshots/ con 5 JSON sectoriales (depends: 1) [unspecified-high]
├── Task 4: Agregar delta a estado-actual-2016-12-24.md (depends: 1) [quick]
├── Task 5: Agregar confianza a diplomacia/acuerdos-y-canales.md [unspecified-high]
├── Task 6: Crear contexto/wisdom.md [unspecified-high]
├── Task 7: Crear estado/nodos-dios.md [deep]

Wave 3 (Documentation — after all content):
├── Task 8: Crear 3 mini-AGENTS.md jerárquicos (depends: 3-7) [quick]
├── Task 9: Actualizar AGENTS.md y README.md (depends: 2-8) [quick]

Wave FINAL (Verification):
├── Task F1: Validar todos los JSON con python3 [quick]
├── Task F2: Verificar consistencia entre archivos [unspecified-high]
```

---

## TODOs

- [x] 1. Definir schemas JSON para game-state y snapshots sectoriales
- [x] 2. Crear estado/game-state.json (boulder del juego)
- [x] 3. Crear directorio snapshots/ con 5 JSON sectoriales
- [x] 4. Agregar sección delta a estado-actual-2016-12-24.md
- [x] 5. Agregar marcadores de confianza a diplomacia/acuerdos-y-canales.md
- [x] 6. Crear contexto/wisdom.md (wisdom accumulation)
- [x] 7. Crear estado/nodos-dios.md (pilares críticos)
- [x] 8. Crear 3 mini-AGENTS.md jerárquicos
- [x] 9. Actualizar AGENTS.md y README.md con la nueva estructura

  **What to do**:
  - En AGENTS.md: AGREGAR secciones que documenten:
    - Game-state boulder (`estado/game-state.json`) y cómo leerlo
    - Snapshots sectoriales (`snapshots/*.json`) y cuándo actualizarlos
    - Delta entre turnos (formato obligatorio)
    - Marcadores de confianza (leyenda)
    - Wisdom accumulation (cuándo agregar entradas)
    - Nodos dios (cuándo revisar)
    - Mini-AGENTS.md (dónde están y para qué)
    - Regla de actualización: "después de cada turno, actualizar game-state.json y snapshots"
  - En README.md: actualizar navegación rápida con los nuevos archivos

  **Must NOT do**:
  - NO reescribir AGENTS.md — solo AGREGAR secciones
  - NO tocar CLAUDE.md

  **Recommended Agent Profile**:
  - **Category**: `quick`
  - **Skills**: []

  **Parallelization**:
  - **Can Run In Parallel**: NO (necesita que todo lo anterior esté completo)
  - **Blocks**: None
  - **Blocked By**: Tasks 2-8

  **References**:
  - `AGENTS.md` — archivo a editar
  - `README.md` — archivo a editar
  - Todos los archivos creados en Tasks 1-8

  **Acceptance Criteria**:
  - [ ] `grep -c "game-state\|snapshots\|delta\|confianza\|wisdom\|nodos-dios\|mini-AGENTS" AGENTS.md` retorna ≥7
  - [ ] README.md tiene enlaces a los nuevos archivos

  **QA Scenarios**:
  ```
  Scenario: Documentación completa
    Tool: Bash
    Steps:
      1. grep -c "game-state" AGENTS.md → ≥1
      2. grep -c "snapshots" AGENTS.md → ≥1
      3. grep -c "wisdom" AGENTS.md → ≥1
      4. grep "game-state\|snapshots\|wisdom\|nodos-dios" README.md
    Expected Result: Todas las mejoras referenciadas en ambos archivos
    Evidence: .sisyphus/evidence/task-9-docs.txt
  ```

  **Commit**: YES
  - Message: `docs: update AGENTS.md and README.md for vault upgrade v2`
  - Files: `AGENTS.md`, `README.md`

---

## Final Verification Wave

- [x] F1. **Validación JSON** — `quick`
  Para cada archivo JSON en `estado/` y `snapshots/`, ejecutar `python3 -m json.tool`. Verificar que todos pasan.
  Output: `JSON [6/6 pass] | VERDICT`

- [x] F2. **Consistencia entre archivos** — `unspecified-high`
  Verificar que: game-state.json referencia archivos que existen, snapshots tienen datos consistentes con estado-actual, mini-AGENTS.md no contradicen raíz, wisdom.md tiene entradas con fechas válidas, nodos-dios.md tiene 5-7 nodos.
  Output: `Consistency [N/N pass] | VERDICT`

---

## Commit Strategy

| # | Message | Files |
|---|---------|-------|
| 1 | `chore: define JSON schemas for vault upgrade v2` | `docs/schemas-vault-v2.md` |
| 2 | `feat: add game-state boulder JSON` | `estado/game-state.json` |
| 3 | `feat: add sector snapshot JSON files` | `snapshots/*.json` (5 files) |
| 4 | `feat: add delta section to estado-actual` | `estado/estado-actual-2016-12-24.md` |
| 5 | `feat: add confidence markers to diplomatic agreements` | `diplomacia/acuerdos-y-canales.md` |
| 6 | `feat: add wisdom accumulation file` | `contexto/wisdom.md` |
| 7 | `feat: add god nodes document` | `estado/nodos-dios.md` |
| 8 | `feat: add hierarchical AGENTS.md files` | `diplomacia/AGENTS.md`, `doctrina/AGENTS.md`, `estado/AGENTS.md` |
| 9 | `docs: update AGENTS.md and README.md for vault upgrade v2` | `AGENTS.md`, `README.md` |

---

## Success Criteria

### Verification Commands
```bash
# All JSON valid
for f in estado/game-state.json snapshots/*.json; do python3 -m json.tool "$f" > /dev/null && echo "OK: $f" || echo "FAIL: $f"; done

# Game state has required fields
python3 -c "import json; d=json.load(open('estado/game-state.json')); assert 'fecha_actual' in d; assert 'acciones_pendientes' in d; print('PASS')"

# 5 snapshots exist
ls snapshots/*.json | wc -l  # Expected: 5

# Delta section in first 20 lines
grep -n "Qué cambió" estado/estado-actual-2016-12-24.md | head -1

# Confidence markers present
grep -c "FIRME\|EN NEGOCIACIÓN\|ESPECULATIVA" diplomacia/acuerdos-y-canales.md

# Wisdom file structured
grep -c "Convenciones\|Éxitos\|Riesgos\|Gotchas" contexto/wisdom.md

# God nodes count
grep -c "^##" estado/nodos-dios.md  # Expected: 5-7

# Mini-AGENTS line counts
wc -l diplomacia/AGENTS.md doctrina/AGENTS.md estado/AGENTS.md  # Each ≤25

# Root AGENTS.md references improvements
grep -c "game-state\|snapshots\|delta\|confianza\|wisdom\|nodos-dios" AGENTS.md  # ≥7
```

### Final Checklist
- [x] All JSON files valid
- [x] Game state reflects Dec 24, 2016 with 4 pending actions
- [x] 5 sector snapshots with real data
- [x] Delta section at top of estado-actual
- [x] Confidence markers in diplomatic agreements
- [x] Wisdom file with structured entries
- [x] 5-7 god nodes identified
- [x] 3 mini-AGENTS.md, each ≤25 lines
- [x] Root AGENTS.md and README.md updated

</content>
</invoke>