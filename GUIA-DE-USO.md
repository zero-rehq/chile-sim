# Guía de uso del vault

## Para qué sirve

Este repo sirve como memoria estratégica del proyecto Chile. La idea es que cada consulta, turno o decisión importante pueda apoyarse en archivos legibles, cortos y vinculados entre sí.

## Cómo usarlo conmigo

Podés pedirme cosas como:

- "Leé el README y el estado actual, y armame el turno"
- "Actualizá pendientes después de este evento"
- "Creá un archivo nuevo para el turno del 10 de septiembre de 2016"
- "Resumime la diplomacia con India según el repo"
- "Decime qué frentes están saturados según los .md"

## Estructura recomendada a futuro

- `doctrina/` → visión, principios, plan país
- `estado/` → foto del presente
- `turnos/` → decisiones y planes por fecha
- `eventos/` → cronología resumida
- `diplomacia/` → acuerdos, chats, socios
- `pendientes/` → memoria viva de frentes abiertos

## Regla práctica

Cada vez que cierres un turno importante, conviene actualizar:

1. `estado/estado-actual-AAAA-MM-DD.md`
2. `turnos/` con el turno nuevo
3. `pendientes/pila-estrategica.md`
4. `README.md` si cambia la prioridad central

## Siguiente mejora útil

Después de esta base, lo más lógico sería crear:

- una **plantilla de turno**
- una **línea de tiempo más granular**
- una **matriz de socios por riesgo / valor / dependencia**
