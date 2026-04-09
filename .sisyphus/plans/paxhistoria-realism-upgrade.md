# Pax Historia — Realism Upgrade Plan

## TL;DR

> **Quick Summary**: Transformar Pax Historia de un simulador centrado en las acciones del jugador a un mundo vivo con eventos globales, métricas, textura social, y consecuencias parciales — sin tocar el prompt base ni las constantes existentes.
> 
> **Deliverables**:
> - Reglas de simulación inyectadas via UI (campo vacío → reglas de realismo)
> - Stage 2 y Stage 3 para 📅 Saltar adelante (enriquecimiento + auditoría)
> - Stage 2 y Stage 3 para ⏭️ Salto automático (mismas mejoras)
> - Bloque de realismo insertado en prompt base de ambos saltos
> - 🧠 Asesor mejorado con métricas y análisis de riesgos
> - ⚡ Acciones mejorado con topics económicos/sociales
> - 🔥 Catalizador mejorado con diversidad temática
> - 💬 Chat mejorado con contexto de eventos globales
> - 3-4 helpers nuevos creados via browser MCP
> 
> **Estimated Effort**: Large (6-8 horas de implementación)
> **Parallel Execution**: YES - 4 waves
> **Critical Path**: Reglas de simulación → Stage 2/3 prompts → Helpers → Test

---

## Context

### Original Request
El jugador quiere que el simulador devuelva más eventos globales, deportivos, políticos, económicos, culturales — no solo reacciones a sus acciones. Quiere métricas por polity y un mundo que se sienta vivo.

### Interview Summary
**Key Discussions**:
- El prompt base NO se toca — solo se agregan bloques nuevos
- Las constantes (`${PLAYER_POLITY}`, etc.) NO se renombran ni eliminan
- El sistema soporta 3 stages por prompt con `PREVIOUS_STAGE_OUTPUT` como puente
- Las "Reglas de simulación" están VACÍAS — oportunidad enorme para inyectar realismo
- Se pueden crear helpers nuevos y editar prompts via browser MCP
- El sistema tiene 12 mecánicas de IA, de las cuales 6 se mejoran

### Research Findings
- **12 prompts investigados**: 7 leídos completos, 5 clasificados como infraestructura
- **76 helpers scrapeados**: 18 usados en prompt base, 58 disponibles sin usar
- **Multi-stage confirmado**: "3 Stage: Check N' Fix" en la tienda demuestra el patrón
- **Reglas de simulación vacías**: se inyectan via `${HISTORICAL_PRESET_SIMULATION_RULES}` — punto de entrada ideal
- **Asesor ya menciona estadísticas** pero de forma vaga — fácil de mejorar
- **Catalizador tiene regla explícita** de no ser solo reuniones — fácil de expandir

### Metis Review
**Identified Gaps** (addressed):
- Formato de PREVIOUS_STAGE_OUTPUT desconocido → T0 de reconocimiento
- Límite de tokens por stage desconocido → probar con ronda real
- Reglas de simulación podrían afectar TODOS los prompts que usan HISTORICAL_PRESET_SIMULATION_RULES → verificar impacto

---

## Work Objectives

### Core Objective
Hacer que Pax Historia genere un mundo vivo con eventos diversos, métricas por polity, consecuencias parciales, y textura social/cultural/deportiva — manteniendo 100% de compatibilidad con el sistema existente.

### Concrete Deliverables
1. Reglas de simulación pobladas con reglas de realismo
2. Bloque [ULTRA REALISM EXPANSION LAYER] insertado en 📅 y ⏭️
3. Stage 2 prompt para enriquecimiento global + métricas
4. Stage 3 prompt para auditoría de consistencia
5. 🧠 Asesor con métricas concretas y análisis de riesgos
6. ⚡ Acciones con topics económicos/sociales/culturales
7. 🔥 Catalizador con diversidad temática expandida
8. 💬 Chat con contexto de eventos globales recientes
9. 3-4 helpers nuevos creados

### Definition of Done
- [ ] Ronda 49 ejecutada con las mejoras activas
- [ ] Output contiene al menos 3 eventos no relacionados con el jugador
- [ ] Output contiene métricas para al menos 3 polities
- [ ] Asesor devuelve métricas concretas (rangos numéricos)
- [ ] Acciones incluyen al menos 1 topic económico y 1 social
- [ ] Catalizador no es una reunión genérica
- [ ] Parser del juego sigue funcionando (no se rompe el JSON)
- [ ] Ninguna constante eliminada o renombrada

### Must Have
- Compatibilidad total con el parser existente
- Prompt base intacto (solo adiciones)
- Constantes existentes preservadas
- Eventos globales diversos (no solo reacciones al jugador)
- Métricas por polity en el asesor

### Must NOT Have (Guardrails)
- NO eliminar secciones del prompt base
- NO renombrar constantes (`${PLAYER_POLITY}`, etc.)
- NO cambiar la estructura de output JSON
- NO tocar prompts de infraestructura (🎤, ✨, 🧾, ⚙️, 📝)
- NO crear más de 5 helpers nuevos (evitar bloat)
- NO exceder 3 stages por prompt
- NO hacer que el mundo ignore las acciones del jugador (balance)

---

## Verification Strategy

> **ZERO HUMAN INTERVENTION** — ALL verification is agent-executed via browser MCP.

### Test Decision
- **Infrastructure exists**: YES (Pax Historia tiene tab "Probar" en cada prompt)
- **Automated tests**: Probar con Round 49 real
- **Framework**: Browser MCP + snapshot comparison

### QA Policy
- Ejecutar Round 49 con mejoras
- Comparar output con Round 48 (baseline)
- Verificar parser no se rompe
- Verificar diversidad de eventos
- Verificar métricas en asesor

---

## Execution Strategy

### Parallel Execution Waves

```
Wave 1 (Foundation — no dependencies):
├── T0: Reconocimiento: verificar formato PREVIOUS_STAGE_OUTPUT [quick]
├── T1: Poblar Reglas de simulación via UI [quick]
├── T2: Crear helpers nuevos via browser MCP [quick]

Wave 2 (Core prompts — depends on T1, T2):
├── T3: Insertar bloque realismo en 📅 Saltar adelante Stage 1 [deep]
├── T4: Crear Stage 2 prompt para 📅 Saltar adelante [deep]
├── T5: Crear Stage 3 prompt para 📅 Saltar adelante [deep]
├── T6: Insertar bloque realismo en ⏭️ Salto automático Stage 1 [deep]
├── T7: Crear Stage 2 prompt para ⏭️ Salto automático [deep]

Wave 3 (Secondary prompts — depends on T2):
├── T8: Mejorar 🧠 Asesor con métricas [unspecified-high]
├── T9: Mejorar ⚡ Acciones con topics diversos [unspecified-high]
├── T10: Mejorar 🔥 Catalizador con diversidad temática [unspecified-high]
├── T11: Mejorar 💬 Chat con contexto global [quick]

Wave 4 (Test + Verify):
├── T12: Ejecutar Round 49 con mejoras y verificar output [deep]
├── T13: Comparar con baseline y ajustar si es necesario [unspecified-high]

Critical Path: T0 → T1+T2 → T3+T4+T5 → T12
Parallel Speedup: ~60% faster than sequential
Max Concurrent: 5 (Wave 2)
```

---

## TODOs

- [ ] 0. Reconocimiento: verificar formato PREVIOUS_STAGE_OUTPUT

  **What to do**:
  - Abrir el prompt "3 Stage: Check N' Fix" de la tienda via browser MCP
  - Ir a Stage 2 y leer cómo usa `${PREVIOUS_STAGE_OUTPUT}`
  - Determinar si es raw text o JSON parseado
  - Documentar hallazgo en draft

  **Must NOT do**:
  - No modificar ningún prompt de la tienda
  - No guardar cambios

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1 (with T1, T2)
  - **Blocks**: T4, T5, T7
  - **Blocked By**: None

  **Acceptance Criteria**:
  - [ ] Formato de PREVIOUS_STAGE_OUTPUT documentado
  - [ ] Decisión tomada sobre cómo Stage 2 consume Stage 1

---

- [ ] 1. Poblar Reglas de simulación con reglas de realismo

  **What to do**:
  - Abrir menú de prompts (Ctrl+P) via browser MCP
  - Escribir en el campo "Reglas de simulación" (actualmente vacío)
  - Insertar reglas de: causalidad obligatoria, éxito parcial, diversidad de eventos, política doméstica, deportes/cultura, estado administrativo, realismo bélico, disciplina de mapa, continuidad global, continuidad histórica, escalado por tiempo de salto, matriz de consecuencias, calidad de eventos, no-filler
  - Guardar

  **Must NOT do**:
  - No tocar ningún prompt individual
  - No crear helpers

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1 (with T0, T2)
  - **Blocks**: T3, T4, T5, T6, T7 (las reglas se inyectan en todos)
  - **Blocked By**: None

  **Acceptance Criteria**:
  - [ ] Campo "Reglas de simulación" contiene reglas de realismo
  - [ ] Reglas cubren: causalidad, éxito parcial, diversidad, política doméstica, deportes, guerra, mapa, global, histórica
  - [ ] Guardado exitoso

---

- [ ] 2. Crear helpers nuevos via browser MCP

  **What to do**:
  - Abrir 📅 Saltar adelante → tab Editar → "+ Nuevo ayudante"
  - Crear estos helpers (nombre + descripción + función):
    1. `PLAYER_ACTION_CONSEQUENCE_MATRIX` — Para cada acción del jugador, devuelve: objetivo probable, nivel de éxito esperado, reacción esperable, riesgo oculto, plazo de impacto
    2. `WORLD_TENSION_SUMMARY` — Resumen de tensiones globales: guerras activas, crisis diplomáticas, shocks económicos, rivalidades, ideologías en ascenso
    3. `POLITY_METRICS_SUMMARY` — Para las 5-8 polities más relevantes: GDP trend, military readiness, public morale, diplomatic standing, internal stability
  - Guardar cada uno

  **Must NOT do**:
  - No crear más de 4 helpers
  - No modificar helpers existentes
  - No eliminar helpers

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1 (with T0, T1)
  - **Blocks**: T3, T4, T5, T8, T9
  - **Blocked By**: None

  **Acceptance Criteria**:
  - [ ] 3 helpers nuevos creados y guardados
  - [ ] Cada helper tiene nombre, descripción y función
  - [ ] Helpers aparecen en la lista de ayudantes

---

- [ ] 3. Insertar bloque realismo en 📅 Saltar adelante Stage 1

  **What to do**:
  - Abrir 📅 Saltar adelante → tab Editar → Primera etapa → Plantilla
  - Localizar la sección `[Specific Simulation Rules]` en el prompt
  - DESPUÉS de esa sección y ANTES de `[FINAL REMINDERS]`, insertar el bloque [ULTRA REALISM EXPANSION LAYER]
  - El bloque incluye: Three-Stage Internal Simulation Process, Mandatory Causality Rule, Partial Success Rule, Reality Density Rule, Event Diversity Rule, Event Composition Rule, Priority Hierarchy, No Filler Rule, Domestic Politics Rule, Public Sentiment Rule, Sports and Cultural Reality Rule, Administrative State Rule, War and Conflict Realism Rule, Map Change Discipline, Global Continuity Rule, Historical Continuity Rule, Time Jump Scaling Rule, Consequences Matrix, Event Quality Rule, Invisible Consequences Rule
  - Guardar

  **Must NOT do**:
  - No eliminar ninguna sección existente
  - No renombrar constantes
  - No mover secciones de lugar

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 2 (with T4, T5, T6, T7)
  - **Blocks**: T12
  - **Blocked By**: T1, T2

  **Acceptance Criteria**:
  - [ ] Bloque insertado entre [Specific Simulation Rules] y [FINAL REMINDERS]
  - [ ] Todas las constantes originales preservadas
  - [ ] Prompt guardado exitosamente

---

- [ ] 4. Crear Stage 2 prompt para 📅 Saltar adelante

  **What to do**:
  - Abrir 📅 Saltar adelante → tab Editar → Segunda etapa
  - Escribir prompt de enriquecimiento que:
    - Lee `${PREVIOUS_STAGE_OUTPUT}` (output de Stage 1)
    - Lee `${RESULTING_MAP_DESCRIPTION}` (mapa post-Stage 1)
    - Lee `${NEWLY_CREATED_ENCIRCLEMENTS}` (cercos detectados)
    - Agrega 3-5 eventos globales que Stage 1 no cubrió
    - Agrega métricas por polity relevante
    - Agrega textura social/cultural/deportiva
    - Valida que toda acción del jugador tenga consecuencia
    - NO elimina eventos de Stage 1
  - Configurar estructura de salida compatible
  - Seleccionar modelo de IA
  - Guardar

  **Must NOT do**:
  - No modificar Stage 1
  - No eliminar eventos de Stage 1
  - No cambiar el formato de output

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 2 (with T3, T5, T6, T7)
  - **Blocks**: T5, T12
  - **Blocked By**: T0, T1, T2

  **Acceptance Criteria**:
  - [ ] Stage 2 prompt escrito y guardado
  - [ ] Usa PREVIOUS_STAGE_OUTPUT correctamente
  - [ ] Agrega eventos globales sin eliminar los de Stage 1
  - [ ] Incluye métricas por polity

---

- [ ] 5. Crear Stage 3 prompt para 📅 Saltar adelante

  **What to do**:
  - Abrir 📅 Saltar adelante → tab Editar → Tercera etapa
  - Escribir prompt de auditoría que:
    - Lee `${PREVIOUS_STAGE_OUTPUT}` (output de Stage 2)
    - Verifica causalidad: toda acción del jugador tiene consecuencia
    - Verifica mapa: no hay cambios arbitrarios
    - Verifica cobertura: hay eventos globales, no solo locales
    - Verifica no-filler: no hay eventos vacíos
    - Corrige problemas encontrados
    - Devuelve output final limpio
  - Guardar

  **Must NOT do**:
  - No agregar eventos nuevos (solo corregir)
  - No cambiar el formato de output

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 2 (with T3, T4, T6, T7)
  - **Blocks**: T12
  - **Blocked By**: T0, T4

  **Acceptance Criteria**:
  - [ ] Stage 3 prompt escrito y guardado
  - [ ] Audita causalidad, mapa, cobertura, filler
  - [ ] Output final compatible con parser

---

- [ ] 6. Insertar bloque realismo en ⏭️ Salto automático Stage 1

  **What to do**:
  - Abrir ⏭️ Salto automático → tab Editar → Primera etapa → Plantilla
  - Insertar el MISMO bloque [ULTRA REALISM EXPANSION LAYER] que en T3
  - Ubicación: después de [Specific Simulation Rules], antes de [FINAL REMINDERS]
  - Guardar

  **Must NOT do**:
  - No eliminar secciones existentes
  - No modificar la mecánica de "cuándo parar"

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 2 (with T3, T4, T5, T7)
  - **Blocks**: T12
  - **Blocked By**: T1

  **Acceptance Criteria**:
  - [ ] Bloque insertado correctamente
  - [ ] Mecánica de auto-stop preservada
  - [ ] Guardado exitoso

---

- [ ] 7. Crear Stage 2 prompt para ⏭️ Salto automático

  **What to do**:
  - Abrir ⏭️ Salto automático → tab Editar → Segunda etapa
  - Adaptar el prompt de Stage 2 de T4 para el contexto de auto-jump
  - Diferencia clave: no hay TARGET_ROUND_DATE fijo, el AI decide cuándo parar
  - Guardar

  **Must NOT do**:
  - No modificar Stage 1
  - No cambiar la mecánica de auto-stop

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 2 (with T3, T4, T5, T6)
  - **Blocks**: T12
  - **Blocked By**: T0, T1, T2

  **Acceptance Criteria**:
  - [ ] Stage 2 adaptado para auto-jump
  - [ ] Preserva mecánica de auto-stop
  - [ ] Guardado exitoso

---

- [ ] 8. Mejorar 🧠 Asesor con métricas y análisis de riesgos

  **What to do**:
  - Abrir 🧠 Chat con el asesor → tab Editar → Plantilla
  - AGREGAR (no reemplazar) un bloque [METRICS AND ANALYSIS] al prompt que:
    - Obligue al asesor a incluir métricas concretas (rangos numéricos)
    - Cubra: GDP trend, military readiness, public morale, diplomatic standing, internal stability, trade balance
    - Incluya análisis de riesgos con probabilidades estimadas
    - Incluya "what-if" scenarios para las acciones del jugador
    - Mantenga el límite de 3000 caracteres
  - Guardar

  **Must NOT do**:
  - No eliminar secciones existentes del prompt
  - No cambiar el límite de caracteres
  - No cambiar el tono del asesor

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 3 (with T9, T10, T11)
  - **Blocks**: T12
  - **Blocked By**: T2

  **Acceptance Criteria**:
  - [ ] Bloque de métricas agregado al prompt del asesor
  - [ ] Asesor devuelve rangos numéricos en sus respuestas
  - [ ] Tono y límite de caracteres preservados

---

- [ ] 9. Mejorar ⚡ Acciones con topics económicos/sociales

  **What to do**:
  - Abrir ⚡ Acciones → tab Editar → Plantilla
  - AGREGAR un bloque [TOPIC DIVERSITY] que:
    - Obligue a incluir al menos 1 topic económico (inflación, comercio, deuda)
    - Obligue a incluir al menos 1 topic social (moral, protestas, legitimidad)
    - Sugiera topics de: ciencia/tecnología, cultura/deportes, seguridad interna
    - Mantenga el formato de 6-9 topics con 2-5 acciones
  - Guardar

  **Must NOT do**:
  - No cambiar el formato de output
  - No eliminar secciones existentes

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 3 (with T8, T10, T11)
  - **Blocks**: T12
  - **Blocked By**: T2

  **Acceptance Criteria**:
  - [ ] Bloque de diversidad agregado
  - [ ] Al menos 1 topic económico y 1 social en output
  - [ ] Formato preservado

---

- [ ] 10. Mejorar 🔥 Catalizador con diversidad temática

  **What to do**:
  - Abrir 🔥 Creación de catalizador → tab Editar → Plantilla
  - AGREGAR un bloque [CATALYST DIVERSITY] que:
    - Expanda la lista de ejemplos de catalizadores con: protestas masivas, descubrimientos científicos, escándalos políticos, eventos deportivos decisivos, desastres naturales, huelgas generales, juicios históricos
    - Refuerce la regla existente de "NOT EVERY CATALYST SHOULD BE A MEETING"
    - Agregue regla de que al menos 1 de cada 3 catalizadores debe ser no-militar y no-diplomático
  - Guardar

  **Must NOT do**:
  - No eliminar ejemplos existentes
  - No cambiar la mecánica de choices

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 3 (with T8, T9, T11)
  - **Blocks**: T12
  - **Blocked By**: None

  **Acceptance Criteria**:
  - [ ] Bloque de diversidad agregado
  - [ ] Ejemplos expandidos con eventos sociales/culturales
  - [ ] Regla de diversidad 1/3 incluida

---

- [ ] 11. Mejorar 💬 Chat con contexto de eventos globales

  **What to do**:
  - Abrir 💬 Chat con el usuario → tab Editar → Plantilla
  - AGREGAR un bloque [GLOBAL CONTEXT IN DIPLOMACY] que:
    - Instruya a las polities a referenciar eventos globales recientes en sus respuestas
    - Ejemplo: "Given the recent economic crisis in [region], we believe..."
    - Haga que las polities mencionen deportes, cultura, o tensiones cuando sea relevante
    - No cambie el tono ni la longitud
  - Guardar

  **Must NOT do**:
  - No cambiar reglas de tono o longitud
  - No cambiar mecánica de "dejar el chat"

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 3 (with T8, T9, T10)
  - **Blocks**: T12
  - **Blocked By**: None

  **Acceptance Criteria**:
  - [ ] Bloque de contexto global agregado
  - [ ] Polities referencian eventos recientes en diplomacia
  - [ ] Tono y longitud preservados

---

- [ ] 12. Ejecutar Round 49 con mejoras y verificar output

  **What to do**:
  - Ejecutar Round 49 del juego Chile via browser MCP
  - Capturar output completo
  - Verificar:
    - Parser no se rompe
    - Al menos 3 eventos no relacionados con Chile
    - Métricas presentes (si Stage 2 las agrega)
    - Diversidad de dominios (político, económico, social, militar, cultural)
    - Todas las acciones del jugador tienen consecuencia
    - No hay eventos filler
  - Documentar resultados

  **Must NOT do**:
  - No modificar prompts durante el test
  - No revertir cambios antes de verificar

  **Parallelization**:
  - **Can Run In Parallel**: NO
  - **Parallel Group**: Wave 4 (sequential)
  - **Blocks**: T13
  - **Blocked By**: T3, T4, T5, T6, T7, T8, T9, T10, T11

  **Acceptance Criteria**:
  - [ ] Round 49 ejecutada exitosamente
  - [ ] Parser funciona
  - [ ] ≥3 eventos globales no-Chile
  - [ ] Diversidad de dominios verificada
  - [ ] Causalidad verificada

---

- [ ] 13. Comparar con baseline y ajustar

  **What to do**:
  - Comparar output de Round 49 con Round 48 (baseline)
  - Identificar mejoras y regresiones
  - Ajustar prompts si es necesario
  - Documentar lecciones aprendidas

  **Must NOT do**:
  - No revertir todas las mejoras por una regresión menor

  **Parallelization**:
  - **Can Run In Parallel**: NO
  - **Parallel Group**: Wave 4 (after T12)
  - **Blocks**: None
  - **Blocked By**: T12

  **Acceptance Criteria**:
  - [ ] Comparación documentada
  - [ ] Ajustes aplicados si necesario
  - [ ] Lecciones aprendidas registradas

---

## Final Verification Wave

- [ ] F1. **Output Compliance** — verificar que Round 49 tiene eventos diversos
- [ ] F2. **Parser Integrity** — verificar que el JSON se parsea correctamente
- [ ] F3. **Prompt Preservation** — verificar que ninguna constante fue eliminada
- [ ] F4. **Advisor Metrics** — verificar que el asesor devuelve métricas concretas

---

## Commit Strategy

No aplica — los cambios se hacen directamente en la UI de Pax Historia via browser MCP, no en código local.

---

## Success Criteria

### Final Checklist
- [ ] Reglas de simulación pobladas
- [ ] Stage 2 y 3 creados para 📅 y ⏭️
- [ ] 3 helpers nuevos creados
- [ ] 6 prompts mejorados (📅, ⏭️, 🧠, ⚡, 🔥, 💬)
- [ ] Round 49 ejecutada con éxito
- [ ] Parser intacto
- [ ] Mundo se siente más vivo
