# AGENTS.md — Directorio estado/

## Archivos en este directorio

- `game-state.json` — punto de entrada rápido: fecha, turno, acciones pendientes, riesgo
- `estado-actual-YYYY-MM-DD.md` — snapshot narrativo completo (buscar el MÁS RECIENTE)
- `activos-estrategicos.md` — nodos, unidades y doctrina operativa
- `nodos-dios.md` — 7 pilares críticos con dependencias y riesgo de falla

## Cómo leer game-state.json

Leerlo primero para orientación rápida: fecha actual, acciones pendientes y riesgo externo.
Luego leer `estado-actual-*.md` para contexto narrativo completo.

## Snapshots sectoriales

Ver `snapshots/` para estado cuantitativo por sector (energía, industria, diplomacia, fiscal, logística).
Actualizar después de cada turno con datos reales del vault.

## Cuándo actualizar este directorio

Después de cada turno: crear nuevo `estado-actual-YYYY-MM-DD.md` y actualizar `game-state.json`.
Nunca reutilizar archivos de turnos anteriores — siempre crear con la nueva fecha.
