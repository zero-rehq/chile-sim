# Draft: Pax Historia Realism Upgrade

## Investigación completada 2026-04-09

---

## Sistema de prompts descubierto

### 12 mecánicas de IA
| Prompt | Función | Investigado |
|--------|---------|-------------|
| 💬 Chat con el usuario | Diplomacia entre jugador y naciones | ✅ Prompt completo leído |
| 🧠 Chat con el asesor | Advisor AI del jugador | ✅ Prompt completo leído |
| 📅 Saltar hacia adelante | Genera eventos del turno | ✅ Prompt base guardado |
| ⏭️ Salto automático | Auto-jump: AI decide cuándo parar, soporta 3 stages, chat invitation en evento final | ✅ Prompt completo leído |
| ⚡ Acciones | Genera 6-9 "Topics of Concern" con 2-5 acciones cada uno | ✅ Prompt completo leído |
| 🎤 Siguiente orador | Quién habla en diplomacia | ⬜ Infraestructura — no necesita mejora de realismo |
| ✨ Descripción a acción | Texto libre → acción estructurada | ⬜ Infraestructura — no necesita mejora de realismo |
| 🧾 Consolidador de eventos | Comprime eventos viejos en resúmenes | ⬜ Infraestructura — podría beneficiarse de preservar métricas |
| 🔥 Creación de catalizador | Zoom-in cinematográfico a eventos | ✅ Prompt completo leído |
| ⚙️ Ejecutor de catalizador | Continúa simulación del catalyst con input del jugador | ⬜ Infraestructura — hereda mejoras del creador |
| 📝 Resumidor de catalizador | Resume catalysts completados para historial | ⬜ Infraestructura — podría preservar métricas |
| 🎲 Director de juego | Cheat mode: edita mapa directamente por request del jugador | ✅ Prompt completo leído |

### Reglas de simulación
- Campo de texto rico (rich text editor)
- Se inyecta via `${HISTORICAL_PRESET_SIMULATION_RULES}`
- Actualmente VACÍO en este juego
- **Oportunidad enorme**: meter reglas de realismo acá sin tocar ningún prompt

### Sistema multi-stage
- Cada prompt soporta hasta 3 etapas (Primera/Segunda/Tercera)
- Cada etapa tiene: Plantilla → Estructura de salida → Modelo de IA → Limpieza
- `PREVIOUS_STAGE_OUTPUT` pasa output de etapa N a etapa N+1
- `RESULTING_MAP_DESCRIPTION` da el mapa post-etapa 1
- `GRAND_MAP_DESCRIPTION_PREVIOUS_STAGE_APPLIED` da mapa detallado post-etapa 1
- `NEWLY_CREATED_ENCIRCLEMENTS` detecta cercos nuevos post-etapa 1

### Tienda de prompts
- 100+ prompts de la comunidad
- Versiones desde v1 hasta v27
- Multi-modelo: Gemini, GPT, Grok, DeepSeek, Claude, Qwen, etc.
- "3 Stage: Check N' Fix" ya demuestra el patrón multi-stage

---

## Hallazgos clave por prompt

### 💬 Chat con el usuario
- Simula diplomacia como roleplay
- Tiene reglas de tono, longitud, dificultad
- Usa: RESPONDING_POLITY_NAME, CHAT_PARTICIPANTS, THIS_CHAT_HISTORY, DIFFICULTY_DESCRIPTION_CHATS
- Regla de longitud: output = promedio mensajes del jugador + 2-3 oraciones
- Polities pueden "dejar el chat" si no tienen razón para seguir
- **Oportunidad**: hacer que las naciones referencien eventos globales recientes (deportes, economía, tensión) en sus respuestas diplomáticas

### 🧠 Chat con el asesor
- Roleplay como chief advisor
- Máximo 3000 caracteres
- Usa: GRAND_MAP_DESCRIPTION, PLAYER_POLITY_REGIONS, PLAYER_POLITY_BATTALION_SUMMARIES, ALL_ADVISOR_MESSAGES
- Ya menciona estadísticas pero de forma vaga ("give ranges or general estimates")
- Usa bullet points, secciones con títulos, texto formateado
- **Oportunidad ENORME**: hacer que el asesor dé métricas reales (PIB, moral, tensión, comercio) y análisis de riesgos con rangos concretos

### 📅 Saltar hacia adelante
- Prompt base guardado en `.sisyphus/drafts/paxhistoria-prompt-base.md`
- 10-15 eventos por turno
- Muy enfocado en acciones del jugador
- Soporta 3 stages con PREVIOUS_STAGE_OUTPUT como puente
- **Oportunidad**: Stage 2 para enriquecimiento global + métricas, Stage 3 para auditoría

### ⏭️ Salto automático hacia adelante
- Mecánica DIFERENTE al salto normal: el AI decide cuándo parar
- Para en "crossroads" que merecen decisión del jugador
- Evento final puede incluir invitación a chat diplomático
- Soporta 3 stages
- Tiene regla de "Immersive Events": parar también en eventos memorables (batallas, descubrimientos, discursos)
- **Oportunidad**: mismas mejoras que Saltar adelante + reglas de diversidad de eventos

### ⚡ Acciones
- Genera 6-9 "Topics of Concern" con 2-5 acciones cada uno
- Cada topic: título + descripción (max 25 palabras) + acciones (max 30 palabras cada una)
- Usa: GRAND_MAP_DESCRIPTION_NO_CITY, ALL_EVENTS_WITH_CONSOLIDATION_CATALYSTS, CHATS_NON_CONSOLIDATED_ROUNDS
- **Oportunidad**: incluir topics de economía, moral social, tensión interna, no solo militar/diplomático

### 🔥 Creación de catalizador
- Zoom-in cinematográfico a eventos específicos
- Muy detallado: batallas, discursos, descubrimientos, debates
- Usa: PREVIOUS_ROUND_EVENTS, RUNNING_CATALYST_DATE, PLAYER_ACTIONS_THIS_ROUND, ALL_EVENTS_WITH_CONSOLIDATION_CATALYSTS
- Regla explícita: "NOT EVERY CATALYST SHOULD BE A MEETING OR DISCUSSION"
- Puede ser: conflicto, descubrimiento, discurso, desciframiento, etc.
- **Oportunidad**: hacer que los catalizadores incluyan más textura social (protestas, deportes, escándalos, huelgas, desastres)

### 🎲 Director de juego
- Cheat mode / map editor
- Ejecuta lo que el jugador pida directamente
- Usa: GAME_MASTER_PLAYER_REQUEST, GRAND_MAP_DESCRIPTION_NO_CITY
- **Oportunidad**: mínima, es una herramienta de edición directa

---

## Decisiones confirmadas

1. **NO eliminar nada del prompt base** — solo agregar
2. **NO renombrar constantes** — solo crear nuevas
3. **Usar Reglas de simulación** como punto de inyección principal de realismo
4. **Crear Stage 2 y Stage 3** para Saltar hacia adelante
5. **Mejorar el Asesor** para dar métricas y análisis
6. **Mejorar el Catalizador** para más diversidad temática
7. **Crear 3-4 helpers nuevos** para métricas/tensión/estado doméstico

## Scope boundaries
- INCLUDE (mejora directa): 📅 Saltar adelante, ⏭️ Salto automático, 🧠 Asesor, ⚡ Acciones, 🔥 Catalizador, Reglas de simulación
- INCLUDE (mejora menor): 💬 Chat con el usuario (referenciar eventos globales)
- EXCLUDE: 🎤 Siguiente orador, ✨ Desc→Acción, 🧾 Consolidador, ⚙️ Ejecutor catalyst, 📝 Resumidor catalyst, 🎲 Director de juego
- EXCLUDE: cambios al parser/código del juego
- EXCLUDE: cambios a la estructura de output JSON
- EXCLUDE: eliminación de constantes o secciones existentes

## Open questions
- ¿Qué formato tiene PREVIOUS_STAGE_OUTPUT? (raw text o JSON parseado)
- ¿Cuántos tokens soporta cada stage?
- ¿Se puede elegir modelo diferente por stage?

## Test strategy
- Probar con una ronda real (Round 49)
- Comparar output antes/después
- Verificar que el parser sigue funcionando
