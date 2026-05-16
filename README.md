# Chile Sim Vault

## ⚠️ OBLIGACIÓN CRÍTICA: PERSISTENCIA DEL ESTADO

**NUNCA DEJAR EL JUEGO EN EL AIRE SIN ACTUALIZAR EL VAULT.**

Después de cada turno o bloque de acciones, el agente DEBE actualizar estos archivos en orden:

1. **`turnos/historial-acciones-completo-2026.md`** — agregar TODAS las acciones ejecutadas con fecha, descripción e impacto. **Cada acción debe incluir su estado: `[ESTADO: ENVIADA]` al proponer, `[ESTADO: EJECUTADA]` al confirmar.**
2. **`estado/estado-actual-*.md`** — crear o actualizar con fecha actual (ej: `estado-actual-2026-02-15.md`)
3. **`pendientes/pila-estrategica.md`** — actualizar tabla de frentes, prioridades y estado
4. **`eventos/eventos-detallados-recientes.md`** — registrar eventos mundiales y respuestas
5. **`contexto/handoff-maestro-*.md`** — crear o actualizar con resumen ejecutivo y advertencias
6. **`README.md`** — actualizar fecha, estado y prioridades (este archivo)

**Si NO se completan estos 6 archivos, el próximo agente no tendrá contexto y el juego quedará perdido.**

Ver checklist completo en `AGENTS.md` sección "Actualización del vault — OBLIGATORIO cada turno".

## Regla de estados de acciones (DOCTRINA OFICIAL)

Toda acción propuesta al jugador se registra con un estado que refleja su ciclo de vida:

- **`[ESTADO: ENVIADA]`** — La acción fue propuesta al jugador y está lista para ejecutarse en el próximo salto temporal
- **`[ESTADO: EJECUTADA]`** — El simulador resolvió el turno, el jugador confirmó, y la acción ocurrió en el mundo del juego

**Formato en el historial:**
```
**[ESTADO: ENVIADA]** Action Date: 2026-02-15 / Chile inicia...
**[ESTADO: EJECUTADA]** Action Date: 2026-02-15 / Chile inicia...
```

Esta distinción es obligatoria. Permite rastrear qué fue propuesto versus qué fue realmente ejecutado, y es crítica para la coherencia del vault cuando el contexto se compacta o un nuevo agente retoma el juego.

## Modelo institucional del juego

El vault opera con **dos fases canónicas**:

- **`modo_gobierno_boric`** — rige hasta el **2026-03-10** inclusive. En esta fase el jugador encarna al gobierno de Chile y actúa desde el Ejecutivo.
- **`modo_oposicion_estrategica`** — rige desde el **2026-03-11**. Desde ahí el jugador deja de ser el Ejecutivo nacional y pasa a encarnar a la **oposición estratégica del Proyecto Chile** frente al gobierno de **José Antonio Kast**.

Esto no es un detalle narrativo: cambia qué herramientas son válidas, qué archivos hay que leer y qué tipo de acciones se pueden proponer. Después del 11 de marzo no se gobiernan ministerios ni se firman tratados del Estado; se opera desde Congreso, territorios aliados, organización social, diplomacia en la sombra y preparación programática para 2029.

## ⚠️ STATELESS: Este vault es la ÚNICA memoria del juego

**El agente NO tiene memoria de sesiones anteriores.** Cada vez que un agente nuevo (o el mismo tras compactación) retoma el juego, SOLO cuenta con lo que está escrito en estos archivos. Si algo no está en el vault, no existe.

**Orden de lectura obligatorio para cualquier agente:**
1. Este `README.md`.
2. `estado/game-state.json`.
3. `estado/` → el archivo `estado-actual-*` **más reciente**.
4. `pendientes/pila-estrategica.md`.
5. Si la fase es `modo_oposicion_estrategica`: `estado/parlamento.md`, `estado/oposicion-estrategia.md`, `estado/territorios-aliados.md`, `estado/bloques-coaliciones.md`.
6. `diplomacia/acuerdos-y-canales.md` y, si la fase es opositora, `diplomacia/oposicion-diplomatica.md`.
7. `turnos/` → turno actual/siguiente y `turnos/historial-acciones-completo-2026.md`.
8. `contexto/` → el `handoff-maestro-*` **más reciente**.

Con esa secuencia, cualquier agente puede reconstruir la coyuntura, la fase institucional y los frentes prioritarios sin romper continuidad.

## Navegación rápida

### Doctrina (no cambia entre turnos — ASPIRACIONAL)
- `doctrina/vision-doctrinal.md` — Visión doctrinal y plan país
- `doctrina/objetivos-largo-plazo.md` — Objetivos de largo plazo (2020/2025/2030+)
- `doctrina/imagen-final-de-pais.md` — Imagen final de país
- `doctrina/cuestion-constitucional.md` — La cuestión constitucional
- `doctrina/por-que-chile-necesitara-una-nueva-constitucion.md`
- `doctrina/reforma-constitucional-futura.md`
- `doctrina/principios-constitucionales-del-chile-futuro.md`
- `doctrina/linea-temporal-constitucional-2016-2026.md`
- `doctrina/mecanismo-constitucional-ideal.md`
- `doctrina/bases-sustantivas-constitucion-futura.md`
- `doctrina/formulacion-de-reformas.md` — Doctrina de formulación de reformas
- `doctrina/union-bioceanica-americana.md` — UBA y Real Inti

### Estado vivo (BUSCAR SIEMPRE EL MÁS RECIENTE)
- `estado/game-state.json` — **punto de entrada rápido**: fecha, turno, acciones pendientes, riesgo
- `estado/` → archivo `estado-actual-*.md` más reciente (con sección delta al inicio)
- `estado/nodos-dios.md` — 7 pilares críticos del modelo con dependencias y riesgo de falla
- `estado/activos-estrategicos.md` — Lo que Chile tiene y lo que necesita construir
- `pendientes/pila-estrategica.md`
- `contexto/` → archivo `handoff-maestro-*.md` más reciente
- `contexto/wisdom.md` — lecciones acumuladas (Convenciones, Éxitos, Riesgos, Gotchas)
- `eventos/eventos-detallados-recientes.md`

### Frente opositor (leer cuando corresponda)
- `estado/parlamento.md` — aritmética legislativa, quórums, comisiones y alianzas.
- `estado/oposicion-estrategia.md` — hoja maestra del bloque para 2026-2029.
- `estado/territorios-aliados.md` — laboratorios municipales y regionales.
- `estado/bloques-coaliciones.md` — mapa de puentes, disciplina y riesgos internos.
- `diplomacia/oposicion-diplomatica.md` — aprendizaje internacional, preacuerdos condicionales y límites legales.
- `pendientes/acciones-kast.md` — monitoreo del Ejecutivo rival y respuesta sugerida.

### Frentes clave de la oposición estratégica
- **Congreso** — bloquear, negociar o dejar correr proyectos según costo político real.
- **Territorios** — usar municipios y regiones aliadas como vitrinas de gestión y red 2028.
- **Organización social** — canalizar malestar real, reforzar participación ciudadana en la elaboración de leyes y sostener narrativa con base social.
- **Diplomacia en la sombra** — abrir vínculos con universidades, puertos, institutos, partidos y organismos pensando en 2029.
- **Preparación 2029** — formar cuadros, madurar programa, ordenar coalición y llegar con alternativa de gobierno seria.

### Snapshots sectoriales (actualizar cada turno)
- `snapshots/energia.json` — matriz energética, renovables, smart grid, hidrógeno
- `snapshots/industria.json` — manufactura, minería, tecnología soberana, patentes
- `snapshots/diplomacia.json` — relaciones bilaterales, bloques, confianza
- `snapshots/fiscal.json` — PIB, regla fiscal, exportaciones, pensiones
- `snapshots/logistica.json` — puertos, corredor, trazabilidad, cables submarinos

### Historial y turnos
- **`turnos/indice-turnos.md`** — Índice general con navegación cronológica de todos los turnos
- `turnos/historial-acciones-completo-2026.md` — Cronología plana completa de 2026
- `turnos/plantilla-turno.md` — Plantilla para crear nuevos turnos

## Estado actual del juego

**Fecha:** 27 de marzo de 2026 | **Turno:** 5

**Fase actual:** `modo_oposicion_estrategica`.

**Actor vigente:** ya no somos La Moneda. Desde el 11 de marzo el jugador opera como **oposición estratégica del Proyecto Chile** frente al gobierno de **José Antonio Kast**.

**Preset:** Real World 2026 — Chile sigue operando sobre condiciones reales y entra en un nuevo ciclo: el gobierno saliente dejó cierres administrativos, respaldo técnico-territorial y trazabilidad documental parcial, pero el nuevo Ejecutivo llega con agenda de orden, revisión y posible desmontaje selectivo.

**Prioridad inmediata:** convertir la primera fase opositora visible en capacidad real de contención. Ya existen mesa de continuidad útil, audiencias ciudadanas, red territorial, gira nacional, misión transpacífica e informe parlamentario. Ahora hay que usarlos para encarecer auditorías y revisión bioceánica de Kast sin inflar victorias ni hablar como Ejecutivo.

**Alertas activas:**
- 🚨 Scarborough y Mar de China Meridional: ASEAN alerta, China endurece presencia y EEUU respalda a Manila. El arco transpacífico vuelve a agravarse y el riesgo logístico sigue alto.
- ⚠️ Kast ya pasó al ataque material: abrió auditorías sobre nombramientos y contratos del período Boric y confirmó revisión de acuerdos bioceánicos con Argentina.
- ⚠️ La derecha intensificó la campaña contra la "herencia ideológica" de Boric y busca mezclar continuidad útil con revancha simbólica.
- ⚠️ Apareció una defensa técnico-social útil: comunidad empresarial, académica, regional y logística empezó a advertir contra desmontes en agenda transpacífica y bioceánica.
- ⚠️ La oposición ya tiene fase visible propia, pero todavía no hegemoniza el relato ni controla la agenda institucional.

**Frentes con movimiento:** Mesa de Defensa de la Continuidad Útil, audiencias ciudadanas, Red de Laboratorios Territoriales, misión transpacífica con Japón y Corea, defensa parlamentaria del bioceánico, monitoreo de auditorías de Kast y disputa narrativa sobre continuidad útil. Ver `pendientes/pila-estrategica.md`.

## Juicio estratégico corto

Chile sigue teniendo fundamentos macroeconómicos sólidos, recursos naturales extraordinarios y una red comercial impresionante. Lo que cambió en este corte es el ritmo político: la oposición ya no está solo acomodándose al cambio de mando, sino que empezó a moverse con herramientas propias en Congreso, territorio, sociedad civil y diplomacia en la sombra. Aun así, el Ejecutivo también dejó de tantear y pasó a usar auditorías, revisión bioceánica y campaña mediática para correr el eje hacia revancha ideológica. La disputa ya no es si habrá conflicto, sino si la oposición puede transformarlo en defensa creíble del interés nacional sin sobreactuar lo heredado.

## Regla de oro

> Chile no debe crecer más rápido de lo que puede sostener.  
> Consolidar antes de expandir.  
> Madurar antes de dispersarse.

## Qué mirar antes de cada turno

1. `estado/` → el archivo `estado-actual-*.md` **más reciente**
2. `pendientes/pila-estrategica.md`
3. `eventos/eventos-detallados-recientes.md`
4. `estado/game-state.json`
5. `contexto/` → el `handoff-maestro-*.md` **más reciente**

## Regla de registro

Todo lo que se ejecute o se reporte queda anotado en el archivo que corresponda: historial, estado, pendientes, contexto o turno. El último log del jugador marca siempre el corte temporal; cualquier acción nueva se escribe después de esa fecha.

## Nota sobre el reset

El vault anterior (2016-2017, 51 turnos) fue backup commitado en git antes de este reset. Las instituciones del juego anterior (AIIEE, Parque Atacama, Centro Bioceánico, etc.) NO existen en este preset. Se crearán de nuevo con nombres nuevos durante el gameplay. La doctrina se conservó como horizonte aspiracional.

## Formato recomendado para nuevas notas de turno

- Fecha del turno
- Qué cambió de verdad
- Prioridad 1
- Prioridad 2
- **Acciones listas para copiar y pegar** — cada acción debe incluir un **resumen de 2-4 líneas arriba** explicando qué pasa, por qué importa y qué cambia, seguido del párrafo detallado de 3-5 oraciones
- Chats diplomáticos necesarios
- Riesgos si se ejecuta mal
- Qué NO abrir todavía
