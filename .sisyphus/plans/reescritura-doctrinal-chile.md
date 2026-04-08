# Reescritura Doctrinal Completa del Vault Chile Sim

## TL;DR

> **Quick Summary**: Reescribir toda la sección doctrinal del vault Chile Sim con profundidad narrativa, quotes ministeriales, lore chilena, riesgos, horizontes orientativos y estructura Obsidian con wikilinks cruzados. Pasar de bullets sin alma a prosa de gobierno con identidad.
>
> **Deliverables**:
> - 10 documentos individuales de objetivos estratégicos (doctrina/objetivos/01-*.md a 10-*.md)
> - 1 documento de imagen final de país (doctrina/imagen-final-de-pais.md)
> - 1 hub central reescrito (doctrina/objetivos-largo-plazo.md)
> - 1 visión doctrinal reescrita (doctrina/vision-doctrinal.md)
> - 1 reforma 2017 expandida (pendientes/reforma-2017.md)
> - Actualización de links en AGENTS.md y README.md
>
> **Estimated Effort**: Large
> **Parallel Execution**: YES - 4 waves
> **Critical Path**: Wave 1 (10 objetivos) → Wave 2 (hub + imagen final) → Wave 3 (visión + reforma) → Wave 4 (links + verificación)

---

## Context

### Original Request
El usuario quiere que el vault doctrinal de Chile Sim tenga "alma" — la misma profundidad narrativa que el documento `cuestion-constitucional.md` (244 líneas, quotes, análisis, lore) y el estilo del PDF de Victoria 3 que compartió (fases densas, advertencias, señales de éxito, cierre épico). Actualmente los objetivos son listas de bullets sin desarrollo.

### Interview Summary
**Key Discussions**:
- Horizontes temporales: mixto (visión atemporal + orientativos 2020/2025/2030+, no rígidos)
- Dimensión social/constitucional: integrada donde sea natural + links al doc completo
- Estructura por objetivo: libre y narrativa, no secciones rígidas tipo manual
- Formato: Obsidian-like con wikilinks cruzados entre todos los documentos
- Imagen final de país: documento separado propio (`doctrina/imagen-final-de-pais.md`)
- Reforma 2017: incluida en scope, expandir a ~100-120 líneas
- Vision doctrinal: reescribir con alma

### Metis Review
**Identified Gaps** (addressed):
- Promise gap: AGENTS.md y README.md prometen "horizontes 2020/2025/2030+" que no existen → se crean en la reescritura
- Overlap entre vision-doctrinal.md y objetivos-largo-plazo.md → roles definidos: WHY vs WHAT
- Riesgo de duplicar cuestion-constitucional.md en objetivos sociales → guardrail: link, no duplicar
- Filenames de los 10 objetivos no estaban definidos → definidos abajo
- Reforma-2017.md ambigua en scope → confirmada IN scope

---

## Work Objectives

### Core Objective
Transformar la sección doctrinal del vault de listas de bullets sin profundidad a documentos narrativos con alma de gobierno chileno, interconectados con wikilinks estilo Obsidian.

### Concrete Deliverables
15 archivos creados o reescritos (ver tabla en Execution Strategy).

### Definition of Done
- [ ] 10 docs de objetivos existen en `doctrina/objetivos/` con ≥100 líneas cada uno
- [ ] Cada doc tiene ≥2 blockquotes ministeriales y ≥3 wikilinks
- [ ] Cada doc referencia al menos un horizonte temporal (2020/2025/2030)
- [ ] Hub central reescrito con links a los 10 objetivos + imagen final
- [ ] Imagen final de país como doc separado con ≥100 líneas
- [ ] Vision doctrinal reescrita con ≥150 líneas
- [ ] Reforma 2017 expandida a ≥100 líneas
- [ ] AGENTS.md y README.md actualizados con nueva estructura
- [ ] Zero cambios en archivos fuera de scope (estado/, turnos/, eventos/, diplomacia/)

### Must Have
- Prosa narrativa larga (párrafos, no bullets) en español rioplatense con voseo
- Quotes ministeriales con atribución (ministerio, contexto, fecha aproximada)
- Lore chilena real entretejida (historia, geografía, tradición institucional)
- Riesgos y advertencias integrados en la narrativa
- Horizontes orientativos 2020/2025/2030+ como anclas narrativas (no compromisos rígidos)
- Wikilinks `[[obsidian-style]]` cruzados entre TODOS los documentos
- Dimensión constitucional/social integrada donde sea natural + link a `[[doctrina/cuestion-constitucional]]`
- Sección "Qué NO es" o equivalente narrativo en cada objetivo
- La "Frase doctrinal" preservada y elevada

### Must NOT Have (Guardrails)
- **G1**: NO inventar nuevos objetivos estratégicos más allá de los 10 canónicos
- **G2**: NO tocar archivos de game state: `estado/`, `turnos/`, `eventos/`, `diplomacia/`, `pendientes/pila-estrategica.md`
- **G3**: NO quotes que suenen a corporate mission statement — deben tener filo, tensión, punto de vista
- **G4**: NO horizontes temporales como compromisos rígidos ("en Q2 2024 el Ministerio completará...")
- **G5**: NO duplicar el análisis de `cuestion-constitucional.md` — link y resumir en 2-3 oraciones
- **G6**: NO inventar instituciones que no existan en AGENTS.md o en el vault
- **G7**: NO agregar frontmatter a archivos existentes que no se reescriben
- **G8**: NO reescribir AGENTS.md más allá de actualizar las 2-3 líneas de referencias a archivos
- **G9**: NO sonar académico — esto es gobierno, no paper universitario
- **G10**: NO bullets cortos — cada sección debe ser prosa narrativa con párrafos de 3+ oraciones

---

## Verification Strategy

> **ZERO HUMAN INTERVENTION** - ALL verification is agent-executed.

### Test Decision
- **Infrastructure exists**: NO (no hay tests automatizados en este repo)
- **Automated tests**: None — es un vault de markdown
- **Framework**: N/A

### QA Policy
Cada tarea incluye QA scenarios ejecutados por el agente con bash (grep, wc, etc.).
Evidence saved to `.sisyphus/evidence/`.

- **Markdown files**: Use Bash — grep para quotes, wikilinks, line counts
- **Cross-references**: Use Bash — verificar que wikilinks apunten a archivos existentes
- **Game state integrity**: Use Bash — git diff para verificar que no se tocaron archivos fuera de scope

---

## Execution Strategy

### Parallel Execution Waves

```
Wave 1 (Start Immediately — 10 objective docs, MAX PARALLEL):
├── Task 1: Objetivos 01-02 (economía + soberanía tecnológica) [writing]
├── Task 2: Objetivos 03-04 (energía + logística) [writing]
├── Task 3: Objetivos 05-06 (unión cono sur + estado científico) [writing]
├── Task 4: Objetivos 07-08 (bienestar nórdico + reforma 2017) [writing]
└── Task 5: Objetivos 09-10 (multipolaridad + resiliencia) [writing]

Wave 2 (After Wave 1 — hub + imagen final):
├── Task 6: Hub central objetivos-largo-plazo.md (depends: 1-5) [writing]
└── Task 7: Imagen final de país (depends: 1-5) [writing]

Wave 3 (After Wave 2 — visión + reforma):
├── Task 8: Vision doctrinal reescrita (depends: 6) [writing]
└── Task 9: Reforma 2017 expandida (standalone) [writing]

Wave 4 (After ALL — links + verificación):
├── Task 10: Actualizar AGENTS.md y README.md (depends: 6-9) [quick]
└── Task 11: Verificación final — QA completo (depends: all) [deep]

Critical Path: Task 1-5 → Task 6 → Task 8 → Task 10 → Task 11
Parallel Speedup: ~60% faster than sequential
Max Concurrent: 5 (Wave 1)
```

### Dependency Matrix

| Task | Depends On | Blocks | Wave |
|------|-----------|--------|------|
| 1 | — | 6, 7 | 1 |
| 2 | — | 6, 7 | 1 |
| 3 | — | 6, 7 | 1 |
| 4 | — | 6, 7 | 1 |
| 5 | — | 6, 7 | 1 |
| 6 | 1-5 | 8, 10 | 2 |
| 7 | 1-5 | 10 | 2 |
| 8 | 6 | 10 | 3 |
| 9 | — | 10 | 3 |
| 10 | 6-9 | 11 | 4 |
| 11 | all | — | 4 |

### Agent Dispatch Summary

- **Wave 1**: **5 agents** — T1-T5 → `writing` (2 objetivos cada uno)
- **Wave 2**: **2 agents** — T6 → `writing`, T7 → `writing`
- **Wave 3**: **2 agents** — T8 → `writing`, T9 → `writing`
- **Wave 4**: **2 agents** — T10 → `quick`, T11 → `deep`

---

## TODOs

---

## CONTEXT FOR ALL WRITING AGENTS (include in every prompt)

```
IDENTIDAD: Sos el GOBIERNO DE CHILE. Escribís como Estado, no como consultor.
Español rioplatense con voseo. Directo, ejecutivo, sin eufemismos.

FECHA DEL JUEGO: Septiembre 2016. Todo futuro es proyección desde esa fecha.

BENCHMARK DE CALIDAD: Leé doctrina/cuestion-constitucional.md ANTES de escribir.
Ese es el piso de calidad — quotes con atribución, análisis con tensión, lore real,
advertencias honestas, wikilinks cruzados. Tu doc debe tener esa misma densidad.
NO es benchmark de longitud (244 líneas) — tus docs apuntan a 100-180 líneas.

TRES REGISTROS DE VOZ:
1. Asesor → Jugador: rioplatense, cálido, directo ("Consolidá, no te apures")
2. Documento de gobierno: formal chileno ("El Ministerio procede a...")
3. Quotes ministeriales: oraculares, con filo ("La disciplina técnica no es una opción")

ESTRUCTURA NARRATIVA (no rígida, pero orientativa):
- Quote de apertura con atribución
- El problema de fondo (por qué este objetivo existe)
- La visión (qué Chile quiere lograr)
- Qué NO es (exclusiones deliberadas)
- Riesgos y advertencias
- Horizontes orientativos (hacia 2020... hacia 2025... hacia 2030+...)
- Conexión con otros objetivos (wikilinks)
- Quote de cierre

WIKILINKS OBLIGATORIOS (≥3 por doc):
- [[doctrina/vision-doctrinal|Visión doctrinal]]
- [[doctrina/objetivos-largo-plazo|Objetivos de largo plazo]]
- [[doctrina/cuestion-constitucional|La cuestión constitucional]]
- [[doctrina/imagen-final-de-pais|Imagen final de país]]
- [[doctrina/objetivos/XX-nombre|Objetivo N: Nombre]]
- [[pendientes/reforma-2017|Reforma 2017]]
- [[estado/estado-actual-2016-09-03|Estado actual]]
- [[pendientes/pila-estrategica|Pendientes estratégicos]]
- Wikilinks aspiracionales (a archivos que no existen) son PERMITIDOS

INSTITUCIONES VÁLIDAS (solo estas, no inventar nuevas):
Ministerios reales: RREE, Hacienda, Economía, Energía, Minería, OOPP, Educación,
Salud, Desarrollo Social, Defensa, Transportes, CORFO, Banco Central.
Del juego: AIIEE, Parque Industrial Atacama, Nodo Energético Biobío,
Centro Ciberresiliencia Transpacífico, Centro Coordinación Bioceánica,
Misión Técnica Mumbai, Dirección Misiones Prioritarias, Red Manufactura
Avanzada Atacama-Biobío, Red Monitoreo Costero, Secretaría Técnica
Chileno-Alemana, Secretaría Acuerdo Nacional 2017.

GUARDRAILS:
- NO inventar objetivos nuevos
- NO tocar archivos fuera de doctrina/ y pendientes/reforma-2017.md
- NO duplicar cuestion-constitucional.md — link y resumir en 2-3 oraciones
- NO quotes corporativas — deben tener filo y tensión
- NO bullets cortos — prosa narrativa con párrafos de 3+ oraciones
- NO horizontes rígidos — "hacia 2025" no "en Q2 2024"
```

---

- [ ] 1. Objetivos 01-02: Economía de alta complejidad + Soberanía tecnológica

  **What to do**:
  Crear dos archivos con prosa narrativa profunda:

  **`doctrina/objetivos/01-economia-alta-complejidad.md`** (100-180 líneas):
  - El problema: Chile exporta cobre y litio en bruto. El modelo colonial de extraer-exportar-importar manufactura. Vulnerabilidad a precios internacionales.
  - La visión: manufactura tecnológica, software industrial, automatización, microelectrónica, smart grids, sensores, sistemas logísticos, servicios técnicos exportables.
  - Qué NO es: no es reemplazar la minería, no es competir con China en volumen, es competir con Suiza/Israel/Singapur en sofisticación.
  - Horizontes: componentes nacionales en exportaciones (hoy <5%, meta 2020: 15-20%, 2025: 30-40%), patentes internacionales, exportaciones de tecnología.
  - Riesgos: sobreextensión industrial, falta de capital humano, dependencia de socios para componentes críticos.
  - Lore: tradición minera chilena, regla fiscal de 2005, CORFO como motor de fomento.
  - Conexión con: [[doctrina/objetivos/02-soberania-tecnologica]], [[doctrina/objetivos/08-reforma-2017]], [[doctrina/imagen-final-de-pais]].

  **`doctrina/objetivos/02-soberania-tecnologica.md`** (100-180 líneas):
  - El problema: importar tecnología es fácil, no depender de quien te la vende es difícil. Vulnerabilidad a cortes de suministro, puertas traseras, dependencia.
  - La visión: dominar el ciclo completo — diseñar, fabricar, certificar, proteger jurídicamente, mantener, exportar.
  - Caso real: PLCs y sensores chilenos en Argentina y Perú, Protocolo de Certificación Soberana.
  - Qué NO es: no es autarquía, es fabricar lo crítico y entrar al mundo desde posición de fuerza.
  - Horizontes: certificación con Japón/Corea, patentes propias, dependencia tecnológica favorable en vecinos.
  - Conexión con: [[doctrina/objetivos/01-economia-alta-complejidad]], [[doctrina/objetivos/10-resiliencia-nacional]], [[diplomacia/india]], [[diplomacia/japon-corea]].

  **Must NOT do**:
  - No inventar instituciones nuevas
  - No duplicar contenido de cuestion-constitucional.md
  - No usar bullets cortos — todo prosa narrativa

  **Recommended Agent Profile**:
  - **Category**: `writing`
  - **Skills**: []

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1 (with Tasks 2, 3, 4, 5)
  - **Blocks**: Tasks 6, 7
  - **Blocked By**: None

  **References**:
  - `doctrina/cuestion-constitucional.md` — BENCHMARK de calidad. Leer ANTES de escribir.
  - `doctrina/objetivos-largo-plazo.md:21-44` — contenido actual de objetivos 1 y 2 (bullets a expandir)
  - `estado/activos-estrategicos.md` — nodos industriales y unidades existentes
  - `AGENTS.md:138-149` — lista de instituciones válidas del juego

  **Acceptance Criteria**:
  - [ ] Ambos archivos existen en `doctrina/objetivos/`
  - [ ] Cada archivo tiene ≥100 líneas
  - [ ] Cada archivo tiene ≥2 blockquotes con atribución ministerial
  - [ ] Cada archivo tiene ≥3 wikilinks `[[...]]`
  - [ ] Cada archivo referencia al menos un horizonte temporal (2020/2025/2030)
  - [ ] Zero bullets cortos — todo prosa narrativa

  **QA Scenarios**:
  ```
  Scenario: Verificar existencia y calidad de ambos archivos
    Tool: Bash
    Steps:
      1. wc -l doctrina/objetivos/01-economia-alta-complejidad.md → ≥100
      2. wc -l doctrina/objetivos/02-soberania-tecnologica.md → ≥100
      3. grep -c "^>" doctrina/objetivos/01-economia-alta-complejidad.md → ≥2
      4. grep -c "^>" doctrina/objetivos/02-soberania-tecnologica.md → ≥2
      5. grep -co "\[\[" doctrina/objetivos/01-economia-alta-complejidad.md → ≥3
      6. grep -co "\[\[" doctrina/objetivos/02-soberania-tecnologica.md → ≥3
      7. grep -c "202[0-9]" doctrina/objetivos/01-economia-alta-complejidad.md → ≥1
      8. grep -c "202[0-9]" doctrina/objetivos/02-soberania-tecnologica.md → ≥1
    Evidence: .sisyphus/evidence/task-1-objetivos-01-02.txt
  ```

  **Commit**: YES (groups with Tasks 2-5)
  - Message: `docs(doctrina): add 10 individual strategic objective documents`
  - Files: `doctrina/objetivos/01-economia-alta-complejidad.md`, `doctrina/objetivos/02-soberania-tecnologica.md`

- [ ] 2. Objetivos 03-04: Matriz energética + Potencia logística

  **What to do**:
  Crear dos archivos con prosa narrativa profunda:

  **`doctrina/objetivos/03-matriz-energetica.md`** (100-180 líneas):
  - El problema: Chile importa >60% de su energía. Vulnerabilidad al petróleo, geopolítica de Ormuz/Malaca.
  - La ventaja: Atacama = mayor radiación solar del planeta. Patagonia = viento constante. Geografía larga = minihidro.
  - La visión: solar norte, eólica sur, minihidro, almacenamiento, smart grids, hidrógeno verde, mareomotriz a futuro, resiliencia total.
  - Horizontes: matriz renovable (hoy ~45%, 2020: 55-60%, 2025: 70-80%, 2030+: 90%+), dependencia importaciones (hoy ~60%, 2030+: <15%), hidrógeno verde exportable.
  - Qué NO es: no es abandonar el carbón de golpe, es transición gradual con respaldo analógico.
  - Lore: el desierto de Atacama como ventaja geográfica, la tradición minera reconvertida en energía.
  - Conexión con: [[doctrina/objetivos/10-resiliencia-nacional]], [[doctrina/objetivos/01-economia-alta-complejidad]], [[diplomacia/alemania]].

  **`doctrina/objetivos/04-potencia-logistica.md`** (100-180 líneas):
  - El problema: Sudamérica produce mucho y comercia poco entre sí. Logística intra-regional cara y lenta.
  - La ventaja: Chile entre cordillera y mar = puerta entre dos océanos.
  - La visión: corredor bioceánico, interoperabilidad aduanera, puertos inteligentes, continuidad energética, trazabilidad ferroviaria.
  - Caso real: eje Mato Grosso → Agua Negra → Valparaíso ya operativo con métricas.
  - Qué NO es: no es hegemonía, es ser el nodo más eficiente. No es competencia con Panamá, es complementariedad.
  - Horizontes: tiempos de tránsito, automatización portuaria, rutas transpacíficas.
  - Conexión con: [[doctrina/objetivos/05-union-cono-sur]], [[diplomacia/argentina-brasil-peru]], [[estado/activos-estrategicos]].

  **Must NOT do**: Mismos guardrails que Task 1.

  **Recommended Agent Profile**:
  - **Category**: `writing`
  - **Skills**: []

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1 (with Tasks 1, 3, 4, 5)
  - **Blocks**: Tasks 6, 7
  - **Blocked By**: None

  **References**:
  - `doctrina/cuestion-constitucional.md` — BENCHMARK de calidad
  - `doctrina/objetivos-largo-plazo.md:46-75` — contenido actual de objetivos 3 y 4
  - `diplomacia/argentina-brasil-peru.md` — contexto del corredor bioceánico
  - `diplomacia/alemania.md` — contexto de hidrógeno y Industrie 4.0

  **Acceptance Criteria**: Mismos que Task 1 pero para archivos 03 y 04.

  **QA Scenarios**: Misma estructura que Task 1 pero para archivos 03 y 04.
  ```
  Evidence: .sisyphus/evidence/task-2-objetivos-03-04.txt
  ```

  **Commit**: YES (groups with Tasks 1, 3-5)

- [ ] 3. Objetivos 05-06: Unión Cono Sur + Estado científico-territorial

  **What to do**:
  Crear dos archivos con prosa narrativa profunda:

  **`doctrina/objetivos/05-union-cono-sur.md`** (100-180 líneas):
  - El problema: integración sudamericana más retórica que real. Mercosur a medias, UNASUR foro, Alianza del Pacífico lenta.
  - La visión: comunidad técnica de infraestructura (Chile, Argentina, Brasil, Perú). No bloque ideológico.
  - Cómo: centros técnicos permanentes, protocolos de interoperabilidad, formación conjunta, redundancia compartida.
  - Qué NO es: no es integración política, no es federalismo, es integración funcional.
  - Lore: la tradición de Chile como Estado pragmático, no ideológico.
  - Conexión con: [[doctrina/objetivos/04-potencia-logistica]], [[diplomacia/argentina-brasil-peru]].

  **`doctrina/objetivos/06-estado-cientifico-territorial.md`** (100-180 líneas):
  - El problema: ciencia chilena desconectada del territorio. Papers en Nature pero no resuelve problemas chilenos.
  - La visión: ciencia ligada a la geografía — astronomía norte, desierto, mar, glaciares sur, Antártica, datos territoriales, instrumentación.
  - Caso real: Red de Monitoreo Costero con boyas inteligentes.
  - Qué NO es: no es ciencia decorativa, es músculo del Estado.
  - Lore: Atacama como mejor lugar del planeta para observar el cielo, 4.300 km de costa, zona económica exclusiva.
  - Conexión con: [[doctrina/objetivos/03-matriz-energetica]], [[doctrina/objetivos/10-resiliencia-nacional]].

  **Must NOT do**: Mismos guardrails.

  **Recommended Agent Profile**: `writing`, Skills: []

  **Parallelization**: Wave 1, parallel with Tasks 1, 2, 4, 5. Blocks 6, 7.

  **References**:
  - `doctrina/cuestion-constitucional.md` — BENCHMARK
  - `doctrina/objetivos-largo-plazo.md:77-108` — contenido actual
  - `estado/activos-estrategicos.md` — Red de Monitoreo Costero, nodos

  **Acceptance Criteria**: Mismos que Task 1 para archivos 05 y 06.
  ```
  Evidence: .sisyphus/evidence/task-3-objetivos-05-06.txt
  ```

  **Commit**: YES (groups with Tasks 1-2, 4-5)

- [ ] 4. Objetivos 07-08: Bienestar nórdico + Reforma 2017

  **What to do**:
  Crear dos archivos con prosa narrativa profunda:

  **`doctrina/objetivos/07-bienestar-nordico.md`** (100-180 líneas):
  - El problema: modelo chileno genera crecimiento pero no lo distribuye. Desigualdad, clase media frágil, servicios públicos insuficientes.
  - AQUÍ SE INTEGRA LA DIMENSIÓN CONSTITUCIONAL: AFPs, FONASA/ISAPRE, desigualdad, Mapuche, descontento regional. Link a [[doctrina/cuestion-constitucional]] para el análisis completo.
  - La visión: vivienda digna, salud territorial, transporte, ciudades habitables, formación técnica, clase media fuerte, movilidad social.
  - Riesgo: "tecnología para ricos" — si el modelo no se socializa, la narrativa se vuelve contra Chile.
  - Horizontes: GINI (hoy ~0.48, meta 2030+: 0.35-0.38), clase media técnica (hoy 20-25%, meta 2030+: 45-50%).
  - Conexión con: [[doctrina/cuestion-constitucional]], [[doctrina/objetivos/08-reforma-2017]], [[pendientes/reforma-2017]].

  **`doctrina/objetivos/08-reforma-2017.md`** (100-180 líneas):
  - El problema: capital humano es cuello de botella. No hay ingenieros ni técnicos suficientes. Educación reproduce desigualdad.
  - La visión: educación como derecho, ciencia como músculo, formación dual alemana, modernización curricular, excelencia docente.
  - Inspiración: Finlandia (educación), Alemania (formación dual), Asia oriental (disciplina).
  - Qué NO es: no es reforma constitucional, es parche grande y necesario.
  - Estado actual: Secretaría del Acuerdo Nacional 2017 trabajando en borrador técnico. Plazo: 30 días desde 3 sep 2016.
  - Conexión con: [[doctrina/objetivos/07-bienestar-nordico]], [[pendientes/reforma-2017]], [[doctrina/cuestion-constitucional]].

  **Must NOT do**: Mismos guardrails. ESPECIALMENTE: no duplicar cuestion-constitucional.md en el objetivo 07 — integrar la dimensión social pero link al doc completo.

  **Recommended Agent Profile**: `writing`, Skills: []

  **Parallelization**: Wave 1, parallel with Tasks 1-3, 5. Blocks 6, 7.

  **References**:
  - `doctrina/cuestion-constitucional.md` — BENCHMARK + contenido a referenciar (NO duplicar)
  - `doctrina/objetivos-largo-plazo.md:110-139` — contenido actual
  - `pendientes/reforma-2017.md` — estado actual de la reforma

  **Acceptance Criteria**: Mismos que Task 1 para archivos 07 y 08.
  ```
  Evidence: .sisyphus/evidence/task-4-objetivos-07-08.txt
  ```

  **Commit**: YES (groups with Tasks 1-3, 5)

- [ ] 5. Objetivos 09-10: Multipolaridad + Resiliencia nacional

  **What to do**:
  Crear dos archivos con prosa narrativa profunda:

  **`doctrina/objetivos/09-multipolaridad.md`** (100-180 líneas):
  - El problema: dependencia de un solo socio es vulnerabilidad. Chile dependió de EEUU, luego de China como comprador de cobre.
  - La visión: equilibrio entre India, Japón, Corea, Alemania, China selectiva. Siempre bajo interés nacional.
  - Regla de oro: "¿Esto aumenta la soberanía chilena o la reduce?"
  - Caso real: India contractual, Japón/Corea certificación, Alemania Industrie 4.0, corredor sudamericano.
  - Qué NO es: no es aislamiento, no es alineamiento, es cooperación selectiva.
  - Conexión con: [[diplomacia/india]], [[diplomacia/japon-corea]], [[diplomacia/alemania]], [[diplomacia/argentina-brasil-peru]].

  **`doctrina/objetivos/10-resiliencia-nacional.md`** (100-180 líneas):
  - El problema: Chile expuesto a terremotos, tsunamis, erupciones, sequías, ciberataques, cortes de cables, conflictos geopolíticos.
  - La visión: país difícil de interrumpir. Todo crítico con redundancia: puertos, agua, energía, datos, corredores, cables, industria, ciudades.
  - Caso real: Centro de Ciberresiliencia Transpacífico, Norma Nacional de Infraestructura Crítica Resiliente.
  - Qué NO es: no es paranoia, es condición permanente del modelo.
  - Lore: geografía extrema de Chile como ventaja y desafío, tradición sísmica, el Pacífico como identidad.
  - Conexión con: [[doctrina/objetivos/03-matriz-energetica]], [[doctrina/objetivos/02-soberania-tecnologica]], [[estado/activos-estrategicos]].

  **Must NOT do**: Mismos guardrails.

  **Recommended Agent Profile**: `writing`, Skills: []

  **Parallelization**: Wave 1, parallel with Tasks 1-4. Blocks 6, 7.

  **References**:
  - `doctrina/cuestion-constitucional.md` — BENCHMARK
  - `doctrina/objetivos-largo-plazo.md:142-166` — contenido actual
  - `diplomacia/` — todos los dossiers diplomáticos
  - `estado/activos-estrategicos.md` — Centro Ciberresiliencia, nodos

  **Acceptance Criteria**: Mismos que Task 1 para archivos 09 y 10.
  ```
  Evidence: .sisyphus/evidence/task-5-objetivos-09-10.txt
  ```

  **Commit**: YES (groups with Tasks 1-4)

- [ ] 6. Hub central: objetivos-largo-plazo.md reescrito

  **What to do**:
  Reescribir `doctrina/objetivos-largo-plazo.md` como documento HUB (100-150 líneas):

  - Quote de apertura épica
  - Visión de Chile a largo plazo (3-4 párrafos narrativos, NO bullets)
  - Los 10 objetivos como RESÚMENES narrativos (1 párrafo cada uno, 3-5 oraciones con alma) + wikilink al doc completo
  - Cómo se conectan entre sí (párrafo sobre la arquitectura del modelo)
  - Link a [[doctrina/imagen-final-de-pais]]
  - La frase doctrinal como cierre

  **CRITICAL**: Este doc es el MAPA. No repite el contenido de los 10 docs — los resume con alma y linkea. Cada resumen debe hacer que el lector QUIERA abrir el doc completo.

  **Rol del doc**: El QUÉ — qué quiere lograr Chile, como sistema interconectado.

  **Must NOT do**:
  - No repetir el contenido completo de los 10 docs
  - No exceder 150 líneas — es hub, no enciclopedia
  - No usar bullets para los resúmenes — prosa narrativa

  **Recommended Agent Profile**: `writing`, Skills: []

  **Parallelization**: Wave 2. Blocks 8, 10. Blocked by 1-5.

  **References**:
  - `doctrina/objetivos-largo-plazo.md` — archivo actual a reescribir
  - `doctrina/objetivos/01-*.md` a `10-*.md` — los 10 docs recién creados (LEER para resumir)
  - `doctrina/cuestion-constitucional.md` — BENCHMARK de calidad

  **Acceptance Criteria**:
  - [ ] Archivo reescrito con 100-150 líneas
  - [ ] Contiene 10 wikilinks a los 10 docs de objetivos
  - [ ] Contiene link a [[doctrina/imagen-final-de-pais]]
  - [ ] Contiene la frase doctrinal
  - [ ] ≥2 blockquotes
  - [ ] Zero bullets — todo prosa

  **QA Scenarios**:
  ```
  Scenario: Verificar hub central
    Tool: Bash
    Steps:
      1. wc -l doctrina/objetivos-largo-plazo.md → 100-150
      2. grep -co "\[\[doctrina/objetivos/" doctrina/objetivos-largo-plazo.md → 10
      3. grep -c "\[\[doctrina/imagen-final" doctrina/objetivos-largo-plazo.md → ≥1
      4. grep -c "^>" doctrina/objetivos-largo-plazo.md → ≥2
      5. grep -c "disciplina soberana" doctrina/objetivos-largo-plazo.md → ≥1
    Evidence: .sisyphus/evidence/task-6-hub-central.txt
  ```

  **Commit**: YES (groups with Task 7)
  - Message: `docs(doctrina): rewrite objetivos-largo-plazo as narrative hub + add imagen-final`

- [ ] 7. Imagen final de país — documento separado

  **What to do**:
  Crear `doctrina/imagen-final-de-pais.md` (100-150 líneas):

  - Quote de apertura
  - El Japón sobrio del Pacífico Sur — qué significa en concreto: disciplina, calidad, precisión, seriedad. Párrafos narrativos sobre cómo Chile se ve a sí mismo en el espejo de Japón.
  - La Finlandia sudamericana — educación, cohesión, Estado serio. Qué toma Chile de Finlandia y qué no.
  - La Corea del Sur andina — de país pobre a potencia tecnológica en una generación. El paralelo con la industrialización coreana.
  - La identidad propia — marítima, científica, austral, minera-industrial, resiliente, territorialmente inteligente. Esto es lo que Chile NO copia de nadie.
  - La frase doctrinal como cierre épico
  - Wikilinks a todos los objetivos que construyen esta imagen

  **Must NOT do**:
  - No ser genérico — cada comparación (Japón, Finlandia, Corea) debe tener sustancia y matices
  - No sonar como brochure turístico — es documento de Estado

  **Recommended Agent Profile**: `writing`, Skills: []

  **Parallelization**: Wave 2, parallel with Task 6. Blocks 10. Blocked by 1-5.

  **References**:
  - `doctrina/objetivos-largo-plazo.md:168-180` — sección actual "Imagen final"
  - `doctrina/cuestion-constitucional.md` — BENCHMARK
  - Los 10 docs de objetivos recién creados

  **Acceptance Criteria**:
  - [ ] Archivo existe con 100-150 líneas
  - [ ] ≥3 blockquotes
  - [ ] ≥5 wikilinks a objetivos individuales
  - [ ] Menciona Japón, Finlandia y Corea con sustancia
  - [ ] Contiene la frase doctrinal

  **QA Scenarios**:
  ```
  Scenario: Verificar imagen final
    Tool: Bash
    Steps:
      1. wc -l doctrina/imagen-final-de-pais.md → 100-150
      2. grep -c "^>" doctrina/imagen-final-de-pais.md → ≥3
      3. grep -co "\[\[" doctrina/imagen-final-de-pais.md → ≥5
      4. grep -c "Japón" doctrina/imagen-final-de-pais.md → ≥1
      5. grep -c "Finlandia" doctrina/imagen-final-de-pais.md → ≥1
      6. grep -c "Corea" doctrina/imagen-final-de-pais.md → ≥1
    Evidence: .sisyphus/evidence/task-7-imagen-final.txt
  ```

  **Commit**: YES (groups with Task 6)

- [ ] 8. Visión doctrinal reescrita con alma

  **What to do**:
  Reescribir `doctrina/vision-doctrinal.md` (150-200 líneas):

  **Rol del doc**: El POR QUÉ — la filosofía fundacional del Proyecto Chile. Por qué este modelo y no otro. Por qué disciplina asiática + bienestar nórdico + Estado serio. La historia que llevó a Chile a esta doctrina.

  - Quote de apertura
  - La historia: cómo Chile llegó aquí. Tradición minera, regla fiscal de 2005, modelo de Estado constreñido, la geografía como destino.
  - La síntesis Chile: producir con disciplina asiática, innovar con ambición de Japón/Corea, vivir con calidad nórdica, gobernar con Estado serio. Cada pilar con 1-2 párrafos de desarrollo.
  - El principio rector: consolidar antes de expandir. Por qué. Los peligros de la sobreextensión.
  - Los 7 pilares del plan global (ya existen como bullets) — reescribir como prosa narrativa con 1 párrafo cada uno + wikilinks a los objetivos correspondientes.
  - Cierre: por qué este modelo es viable para Chile y no para cualquier país. La geografía, la tradición institucional, el tamaño, la posición en el Pacífico.

  **Must NOT do**:
  - No duplicar el hub de objetivos — este doc es filosófico, no operativo
  - No ser abstracto sin anclar en Chile real

  **Recommended Agent Profile**: `writing`, Skills: []

  **Parallelization**: Wave 3. Blocks 10. Blocked by 6.

  **References**:
  - `doctrina/vision-doctrinal.md` — archivo actual a reescribir
  - `doctrina/objetivos-largo-plazo.md` — hub recién reescrito (leer para no duplicar)
  - `doctrina/cuestion-constitucional.md` — BENCHMARK

  **Acceptance Criteria**:
  - [ ] Archivo reescrito con 150-200 líneas
  - [ ] ≥3 blockquotes
  - [ ] ≥5 wikilinks
  - [ ] Zero bullets — todo prosa narrativa
  - [ ] Contiene la síntesis Chile ("producir con disciplina asiática...")

  **QA Scenarios**:
  ```
  Scenario: Verificar visión doctrinal
    Tool: Bash
    Steps:
      1. wc -l doctrina/vision-doctrinal.md → 150-200
      2. grep -c "^>" doctrina/vision-doctrinal.md → ≥3
      3. grep -co "\[\[" doctrina/vision-doctrinal.md → ≥5
      4. grep -c "disciplina asiática" doctrina/vision-doctrinal.md → ≥1
    Evidence: .sisyphus/evidence/task-8-vision-doctrinal.txt
  ```

  **Commit**: YES
  - Message: `docs(doctrina): expand vision-doctrinal with depth and lore`

- [ ] 9. Reforma 2017 expandida

  **What to do**:
  Expandir `pendientes/reforma-2017.md` de 29 líneas a 100-120 líneas:

  - Quote de apertura del Ministro de Educación
  - El nombre político: Acuerdo Nacional para Educación, Ciencia y Desarrollo Territorial 2017
  - El problema de fondo: capital humano como cuello de botella, educación que reproduce desigualdad, movimiento estudiantil 2011
  - Qué debe incluir: modernización educativa, calidad docente, ciencia aplicada, formación técnica, vínculo educación-industria, desarrollo territorial
  - Inspiración: Finlandia, Alemania, Asia oriental — con párrafos que expliquen QUÉ se toma de cada uno
  - Qué NO hacer: no improvisar, no maximalismo, no separar de estrategia industrial
  - Estado actual: borrador técnico en 30 días (desde 3 sep 2016), lanzamiento enero 2017
  - Timeline: borrador oct 2016 → alinear actores nov-dic → legitimidad política dic → lanzamiento ene 2017
  - Conexión con la cuestión constitucional: la reforma es parche, no solución. Link a [[doctrina/cuestion-constitucional]].
  - Wikilinks a: [[doctrina/objetivos/08-reforma-2017]], [[doctrina/objetivos/07-bienestar-nordico]], [[doctrina/cuestion-constitucional]]

  **Must NOT do**:
  - No proponer contenido curricular específico
  - No prometer fechas exactas más allá del timeline ya establecido

  **Recommended Agent Profile**: `writing`, Skills: []

  **Parallelization**: Wave 3, parallel with Task 8. Blocks 10. Blocked by none (standalone).

  **References**:
  - `pendientes/reforma-2017.md` — archivo actual a expandir
  - `doctrina/cuestion-constitucional.md` — BENCHMARK + contexto social
  - `doctrina/objetivos/08-reforma-2017.md` — objetivo correspondiente (recién creado)

  **Acceptance Criteria**:
  - [ ] Archivo expandido a 100-120 líneas
  - [ ] ≥2 blockquotes
  - [ ] ≥3 wikilinks
  - [ ] Contiene timeline de la reforma
  - [ ] Contiene sección "Qué NO hacer"

  **QA Scenarios**:
  ```
  Scenario: Verificar reforma 2017 expandida
    Tool: Bash
    Steps:
      1. wc -l pendientes/reforma-2017.md → 100-120
      2. grep -c "^>" pendientes/reforma-2017.md → ≥2
      3. grep -co "\[\[" pendientes/reforma-2017.md → ≥3
    Evidence: .sisyphus/evidence/task-9-reforma-2017.txt
  ```

  **Commit**: YES
  - Message: `docs(pendientes): expand reforma-2017 to full strategic document`

- [ ] 10. Actualizar AGENTS.md y README.md con nueva estructura

  **What to do**:
  Actualizar SOLO las líneas de referencia en ambos archivos:

  **AGENTS.md**:
  - Sección "Archivos útiles": agregar links a `doctrina/objetivos/` y `doctrina/imagen-final-de-pais.md`
  - Sección "Qué no olvidar nunca": verificar que las referencias a objetivos-largo-plazo.md siguen siendo correctas

  **README.md**:
  - Sección "Navegación rápida": agregar links a los nuevos docs (imagen-final, objetivos individuales)

  **Must NOT do**:
  - NO reescribir secciones de AGENTS.md
  - NO cambiar reglas operativas
  - NO tocar nada fuera de las líneas de referencia/navegación

  **Recommended Agent Profile**: `quick`, Skills: []

  **Parallelization**: Wave 4. Blocks 11. Blocked by 6-9.

  **References**:
  - `AGENTS.md:265-269` — sección "Archivos útiles"
  - `AGENTS.md:229-231` — sección "Qué no olvidar nunca"
  - `README.md:13-33` — sección "Navegación rápida"

  **Acceptance Criteria**:
  - [ ] AGENTS.md contiene referencia a `doctrina/imagen-final-de-pais.md`
  - [ ] AGENTS.md contiene referencia a `doctrina/objetivos/`
  - [ ] README.md contiene link a imagen-final-de-pais

  **QA Scenarios**:
  ```
  Scenario: Verificar referencias actualizadas
    Tool: Bash
    Steps:
      1. grep "imagen-final" AGENTS.md → match
      2. grep "doctrina/objetivos/" AGENTS.md → match
      3. grep "imagen-final" README.md → match
    Evidence: .sisyphus/evidence/task-10-links.txt
  ```

  **Commit**: YES
  - Message: `docs: update cross-references to new doctrina structure`

- [ ] 11. Verificación final — QA completo

  **What to do**:
  Ejecutar TODAS las verificaciones de aceptación:

  1. **File existence**: los 10 docs de objetivos + hub + imagen-final + vision-doctrinal + reforma-2017 existen
  2. **Quote density**: cada doc tiene ≥2 blockquotes
  3. **Wikilink presence**: cada doc tiene ≥3 wikilinks
  4. **Temporal horizons**: cada doc de objetivo referencia 2020/2025/2030
  5. **Cross-reference integrity**: hub linkea a los 10 objetivos + imagen final
  6. **Line count sanity**: cada doc dentro de rango esperado
  7. **Game state integrity**: `git diff --name-only` muestra ZERO cambios en estado/, turnos/, eventos/, diplomacia/
  8. **No bullets check**: verificar que no hay secciones de bullets cortos en los docs nuevos

  **Recommended Agent Profile**: `deep`, Skills: []

  **Parallelization**: Wave 4, after Task 10. Blocks nothing.

  **References**: Todos los archivos creados/modificados.

  **Acceptance Criteria**:
  - [ ] Todos los checks pasan
  - [ ] Report guardado en `.sisyphus/evidence/task-11-final-qa.txt`

  **QA Scenarios**:
  ```
  Scenario: QA completo de toda la reescritura
    Tool: Bash
    Steps:
      1. ls doctrina/objetivos/0{1..9}-*.md doctrina/objetivos/10-*.md | wc -l → 10
      2. ls doctrina/imagen-final-de-pais.md → exists
      3. for f in doctrina/objetivos/*.md; do echo "$f: $(wc -l < $f) lines, $(grep -c '^>' $f) quotes, $(grep -co '\[\[' $f) links"; done
      4. wc -l doctrina/objetivos-largo-plazo.md → 100-150
      5. wc -l doctrina/vision-doctrinal.md → 150-200
      6. wc -l pendientes/reforma-2017.md → 100-120
      7. git diff --name-only HEAD | grep -v "^doctrina/" | grep -v "^pendientes/reforma-2017.md" | grep -v "^AGENTS.md" | grep -v "^README.md" | grep -v "^.sisyphus/" → empty
    Evidence: .sisyphus/evidence/task-11-final-qa.txt
  ```

  **Commit**: NO (verification only)

---

## Final Verification Wave

> After ALL tasks, present consolidated results to user and get explicit "okay".

- [ ] F1. **Plan Compliance Audit** — `oracle`
  Read the plan. For each "Must Have": verify implementation exists. For each "Must NOT Have": search for forbidden patterns. Check evidence files exist.
  Output: `Must Have [N/N] | Must NOT Have [N/N] | Tasks [N/N] | VERDICT`

- [ ] F2. **Scope Fidelity Check** — `deep`
  For each task: read "What to do", read actual files. Verify 1:1 — everything in spec was built, nothing beyond spec was built. Check "Must NOT do" compliance.
  Output: `Tasks [N/N compliant] | Unaccounted [CLEAN/N files] | VERDICT`

---

## Commit Strategy

| Wave | Commit Message | Files |
|------|---------------|-------|
| 1 | `docs(doctrina): add 10 individual strategic objective documents` | doctrina/objetivos/01-*.md through 10-*.md |
| 2 | `docs(doctrina): rewrite objetivos-largo-plazo hub + add imagen-final` | doctrina/objetivos-largo-plazo.md, doctrina/imagen-final-de-pais.md |
| 3a | `docs(doctrina): expand vision-doctrinal with depth and lore` | doctrina/vision-doctrinal.md |
| 3b | `docs(pendientes): expand reforma-2017 to full strategic document` | pendientes/reforma-2017.md |
| 4 | `docs: update cross-references to new doctrina structure` | AGENTS.md, README.md |

---

## Success Criteria

### Verification Commands
```bash
# All 10 objective files exist
ls doctrina/objetivos/0{1..9}-*.md doctrina/objetivos/10-*.md | wc -l  # Expected: 10

# Hub, imagen-final, vision-doctrinal, reforma-2017 exist and are substantial
wc -l doctrina/objetivos-largo-plazo.md  # Expected: 100-150
wc -l doctrina/imagen-final-de-pais.md   # Expected: 100-150
wc -l doctrina/vision-doctrinal.md       # Expected: 150-200
wc -l pendientes/reforma-2017.md         # Expected: 100-120

# Every objective doc has quotes, links, and temporal horizons
for f in doctrina/objetivos/*.md; do
  echo "$f: $(wc -l < $f)L $(grep -c '^>' $f)Q $(grep -co '\[\[' $f)W $(grep -c '202[0-9]' $f)T"
done

# No game state files touched
git diff --name-only HEAD | grep -E "^(estado|turnos|eventos|diplomacia)/" # Expected: empty
```

### Final Checklist
- [ ] All 15 files created/rewritten with narrative prose
- [ ] All "Must Have" present (quotes, wikilinks, horizons, lore, riesgos)
- [ ] All "Must NOT Have" absent (no bullets cortos, no instituciones inventadas, no game state touched)
- [ ] Cross-references intact between all documents
- [ ] AGENTS.md and README.md updated with new structure
