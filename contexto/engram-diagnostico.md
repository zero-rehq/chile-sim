# Diagnóstico de Engram

## Estado verificado

En esta sesión, Engram **no estaba disponible como herramienta operativa**.

Eso significa que no había acceso real a funciones del tipo:

- `mem_search`
- `mem_save`
- `mem_context`
- `mem_session_summary`

## Conclusión

El problema no era el contenido del repo ni una mala estructura del vault. El problema era de **capacidad del entorno de ejecución**: el runtime actual no exponía herramientas de memoria persistente externa.

## Efecto práctico

Un agente podía:

- leer y escribir archivos del repo
- mantener memoria documental local
- usar el vault como fuente de verdad

Pero **no podía** persistir observaciones en Engram porque no tenía esas herramientas disponibles.

## Solución aplicada

Se dejó implementado un fallback serio dentro del repo:

- `AGENTS.md` con reglas de lectura y comportamiento
- `contexto/handoff-maestro-2016-08-27.md` como fuente madre
- `contexto/memoria-operativa-local.md` como respaldo corto
- `README.md` como dashboard central

## Solución ideal a futuro

Para que Engram funcione de verdad, el entorno debe exponer el servidor/herramientas de memoria. Cuando eso exista, el procedimiento correcto es:

1. seguir usando este repo como memoria local y auditable
2. además guardar decisiones y hallazgos en Engram
3. no depender solo de Engram para contexto crítico

## Regla estratégica

El repo es la memoria soberana. Engram, cuando exista, debe ser una capa adicional; no la única.
