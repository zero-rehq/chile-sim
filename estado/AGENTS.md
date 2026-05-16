# AGENTS.md — Directorio estado/

## Leer en este orden

1. `game-state.json` — fecha, fase y señales rápidas.
2. `estado-actual-YYYY-MM-DD.md` más reciente.
3. Si `fase_juego` = `modo_oposicion_estrategica`: `parlamento.md`, `oposicion-estrategia.md`, `territorios-aliados.md`, `bloques-coaliciones.md`.
4. `activos-estrategicos.md` y `nodos-dios.md`.

## Regla de snapshots

Ver `snapshots/` para energía, industria, diplomacia, fiscal, logística, parlamento, territorios y sociedad.

## Cuándo actualizar

Después de cada turno: crear nuevo `estado-actual-YYYY-MM-DD.md` y actualizar `game-state.json`.
No reutilizar archivos viejos ni mezclar fase de gobierno con fase opositora.
