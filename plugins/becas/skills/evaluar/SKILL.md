---
name: evaluar
description: Evalúa una convocatoria puntual (link, nombre o id) contra el perfil de la persona o su grupo y, si califica, arma la checklist de documentos y fechas. Usar cuando pida /becas:evaluar <algo>, "¿califico para X?", "mirá esta beca", o pegue un link de una convocatoria.
argument-hint: <link, nombre o id de la convocatoria>
---

# /becas:evaluar $ARGUMENTS

Reglas de `CLAUDE.md` de la carpeta de trabajo vigentes en todo el flujo.

## Pasos
0. Si no existe `perfil/persona.md`, seguí primero la skill `becas:empezar`.
1. **Identificar.** Buscá `$ARGUMENTS` en `convocatorias/tracker.csv` (id, link o nombre aproximado).
   - Existe → usá ese id.
   - No existe y es link → el evaluador crea la fila.
   - Solo nombre → búsqueda web rápida del link oficial; si hay más de un candidato, preguntá cuál.
   - Sin argumento → preguntá qué convocatoria (aceptá que pegue un link o un texto de mail).
   - Si no está claro si es individual o para el grupo y las bases admiten ambas, asumí lo que diga `persona.md` §8 y decilo.
2. **Evaluador.** Lanzá `becas:evaluador` con el id o link.
3. **Extractor.** Si fit ≥3, lanzá `becas:extractor-requisitos` con el id. Si es ≤2, mostrá por qué y preguntá si igual quiere la checklist.
4. **Mostrar:**
   - Fit, frase honesta, ✅/❌/❓ y cierre con fuente.
   - Si hay checklist: tabla corta (documento · quién lo emite · tiempo · estado), trámites institucionales, fechas internas próximas y ⚠️.
   - `[FALTA]` como preguntas numeradas.
   - Contradicciones entre fuentes.
5. Si fit ≥4: "Para preparar todo: `/becas:postular <id>`".
