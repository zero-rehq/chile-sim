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

## ⚠️ STATELESS: Este vault es la ÚNICA memoria del juego

**El agente NO tiene memoria de sesiones anteriores.** Cada vez que un agente nuevo (o el mismo tras compactación) retoma el juego, SOLO cuenta con lo que está escrito en estos archivos. Si algo no está en el vault, no existe.

**Orden de lectura obligatorio para cualquier agente:**
1. Este `README.md` (orientación general)
2. `estado/` → el archivo **más reciente** por fecha en el nombre
3. `pendientes/pila-estrategica.md`
4. `contexto/` → el `handoff-maestro-*` **más reciente** por fecha en el nombre
5. `turnos/` → el historial de acciones del año en curso

Con esos 5 archivos, cualquier agente debe poder entender dónde está Chile, qué se hizo, qué falta y qué viene.

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

**Fecha:** 1 de febrero de 2026 | **Turno:** 1 (inicio)

**Preset:** Real World 2026 — Chile arranca con condiciones reales de febrero 2026.

**Prioridad inmediata:** Primer turno — establecer posición inicial. Todas las decisiones pendientes.

**Alertas activas:**
- 🚨 China-Taiwán: ejercicios de bloqueo activos desde dic 2025. Rutas transpacíficas amenazadas.
- 🚨 Venezuela: Maduro capturado por EEUU (3 ene 2026). Precedente hemisférico sin precedentes.
- ⚠️ Transición presidencial: Boric sale 11 mar 2026. Nuevo gobierno centroderecha asume.
- ⚠️ Crisis social interna: pensiones AFP, Mapuche, desigualdad.

**Todos los frentes en NO INICIADO.** Ver `pendientes/pila-estrategica.md`.

## Juicio estratégico corto

Chile tiene fundamentos macroeconómicos sólidos, recursos naturales extraordinarios y una red comercial impresionante. Pero depende del cobre, no tiene industria soberana, enfrenta crisis social real y el mundo se fragmenta. La doctrina traza el camino. Falta todo por hacer.

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
