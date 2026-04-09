# Chile Sim Vault

## ⚠️ OBLIGACIÓN CRÍTICA: PERSISTENCIA DEL ESTADO

**NUNCA DEJAR EL JUEGO EN EL AIRE SIN ACTUALIZAR EL VAULT.**

Después de cada turno o bloque de acciones, el agente DEBE actualizar estos archivos en orden:

1. **`turnos/historial-acciones-completo-2016.md`** — agregar TODAS las acciones ejecutadas con fecha, descripción e impacto
2. **`estado/estado-actual-*.md`** — crear o actualizar con fecha actual (ej: `estado-actual-2016-12-10.md`)
3. **`pendientes/pila-estrategica.md`** — actualizar tabla de frentes, prioridades y estado
4. **`eventos/eventos-detallados-recientes.md`** — registrar eventos mundiales y respuestas
5. **`contexto/handoff-maestro-*.md`** — crear o actualizar con resumen ejecutivo y advertencias
6. **`README.md`** — actualizar fecha, estado y prioridades (este archivo)

**Si NO se completan estos 6 archivos, el próximo agente no tendrá contexto y el juego quedará perdido.**

Ver checklist completo en `AGENTS.md` sección "Actualización del vault — OBLIGATORIO cada turno".

## Dashboard estratégico

- **Fecha actual del juego:** 24 de diciembre de 2016 — cierre de año con consolidación de éxito
- **Próximo turno:** a partir del 25 de diciembre de 2016 / enero 2017
- **Doctrina guía:** consolidar antes de expandir
- **Estado del modelo:** Reforma 2017 blindada jurídicamente y lista para ingreso legislativo en enero 2017, Perú integrado con Misión Técnica en Lima y contrato de 50 PLCs en operación (convergencia 78% hacia UBA), Brasil publicando métricas en reales y aceptando Ventanilla Única Aduanera en fase piloto, Fondo de Compensación UBA operativo con USD 150 millones, trazabilidad Mato Grosso-Valparaíso al 99.8%, Incidente en Taiwán superado mediante Plan de Redundancia Estratégica, peso chileno estable en 650-655 pesos por dólar, **India en Transferencia Operativa Nivel 2 con capacitación de 12 ingenieros iniciada (certificación en febrero 2017)**
- **Prioridad inmediata:** ingreso legislativo de Reforma 2017 en enero 2017, implementación en 45 liceos técnicos piloto, fase piloto de Ventanilla Única Aduanera con Brasil (febrero-marzo 2017), completar capacitación de ingenieros indios (certificación febrero 2017), mantener vigilancia digital ante tensiones en Asia oriental, construir UBA técnicamente hasta reforma constitucional chilena

## Navegación rápida

- [[doctrina/vision-doctrinal|Visión doctrinal y plan país]]
- [[doctrina/objetivos-largo-plazo|Objetivos de largo plazo (2020/2025/2030+)]]
- [[doctrina/imagen-final-de-pais|Imagen final de país]]
- [[doctrina/cuestion-constitucional|La cuestión constitucional]]
- [[doctrina/por-que-chile-necesitara-una-nueva-constitucion|Por qué Chile necesitará una nueva constitución]]
- [[doctrina/reforma-constitucional-futura|Reforma constitucional futura]]
- [[doctrina/principios-constitucionales-del-chile-futuro|Principios constitucionales del Chile futuro]]
- [[doctrina/linea-temporal-constitucional-2016-2026|Línea temporal constitucional 2016-2026]]
- [[doctrina/mecanismo-constitucional-ideal|Mecanismo constitucional ideal para Chile]]
- [[doctrina/bases-sustantivas-constitucion-futura|Bases sustantivas de la constitución futura]]
- [[estado/estado-actual-2016-12-24|Estado actual al 24 de diciembre de 2016]]
- [[estado/activos-estrategicos|Activos, nodos y unidades clave]]
- [[turnos/historial-acciones-completo-2016|Historial completo de acciones 2016]]
- [[eventos/eventos-detallados-recientes|Eventos detallados recientes]]
- [[diplomacia/acuerdos-y-canales|Diplomacia, socios y líneas abiertas]]
- [[diplomacia/chats-recientes|Chats diplomáticos recientes]]
- [[pendientes/pila-estrategica|Pendientes estratégicos y frentes abiertos]]
- [[pendientes/reforma-2017|Reforma 2017]]
- [[doctrina/formulacion-de-reformas|Doctrina de formulación de reformas]]
- [[doctrina/union-bioceanica-americana|Unión Bioceánica Americana — Real Inti]]
- [[contexto/handoff-maestro-2016-12-24|Handoff maestro persistido]]
- [[contexto/resumenes-historicos-por-tramos|Resúmenes históricos por tramos]]
- [[contexto/estado-del-mapa-y-unidades-2016-09-03|Estado del mapa y unidades al 2016-09-03]]
- [[contexto/situacion-del-mundo-2016-09-03|Situación del mundo al 2016-09-03]]
- [[turnos/2016-09-03-turno-actual|Turno ejecutado 2016-09-03]]
- [[turnos/2016-09-10-turno-siguiente|Turno ejecutado 2016-09-10]]
- [[turnos/plantilla-turno|Plantilla de turno]]
- [[diplomacia/india|Dossier India]]
- [[diplomacia/argentina-brasil-peru|Dossier Corredor Bioceánico]]
- [[diplomacia/japon-corea|Dossier Japón y Corea]]
- [[diplomacia/alemania|Dossier Alemania]]
- [[GUIA-DE-USO|Cómo usar este vault]]

## Juicio estratégico corto

Chile ya no está en fase de promesa, sino en fase de **administración de éxito**. El mayor peligro no es externo: es crecer más rápido de lo que el Estado, la industria y el capital humano pueden sostener.

## Regla de oro

> Chile no debe crecer más rápido de lo que puede sostener.  
> Consolidar antes de expandir.  
> Madurar antes de dispersarse.

## Qué mirar antes de cada turno

1. [[estado/estado-actual-2016-12-24|Estado actual]]
2. [[pendientes/pila-estrategica|Pendientes estratégicos]]
3. [[diplomacia/acuerdos-y-canales|Diplomacia]]
4. [[turnos/historial-acciones-completo-2016|Historial de acciones]]

## Regla de registro

Todo lo que se ejecute o se reporte queda anotado en el archivo que corresponda: historial, estado, pendientes, contexto o turno. El último log del jugador marca siempre el corte temporal; cualquier acción nueva se escribe después de esa fecha.

## Formato recomendado para nuevas notas de turno

- Fecha del turno
- Qué cambió de verdad
- Prioridad 1
- Prioridad 2
- **Acciones listas para copiar y pegar** — cada acción debe incluir un **resumen de 2-4 líneas arriba** explicando qué pasa, por qué importa y qué cambia, seguido del párrafo detallado de 3-5 oraciones
- Chats diplomáticos necesarios
- Riesgos si se ejecuta mal
- Qué NO abrir todavía
