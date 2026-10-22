---
name: buscar
description: Busca becas, fellowships y grants abiertos según el rol, sector y etapa de la persona (y su grupo), nacionales e internacionales; evalúa las nuevas y muestra hasta 8 priorizadas por fit y cierre. Usar cuando pida /becas:buscar, "buscame becas", "qué grants hay para mí", "hay algo para el grupo".
argument-hint: (opcional) grupo | persona | nacional | internacional | un tema, ej. "RSV" o "machine learning"
---

# /becas:buscar $ARGUMENTS

Reglas de `CLAUDE.md` de la carpeta de trabajo vigentes en todo el flujo.

## 0. Precondiciones
- Si no existe `perfil/persona.md`, decí "Primero configuremos tu perfil" y seguí las instrucciones de la skill `becas:empezar`. Después volvé acá.
- Si §2 (rol y etapa) está en `[FALTA]`, preguntá solo eso antes de seguir.

## 1. Alcance
Del argumento y de `persona.md` §8 deducí:
- **para**: `persona`, `grupo` o ambos. `grupo` solo si lo pidió o si §8 incluye grants de grupo; si pide grupo y `perfil/grupo.md` está vacío, avisá que la búsqueda va a ser más gruesa.
- **ámbito**: nacional, internacional o ambos (por defecto ambos).
- **tema**: texto libre del argumento, si hay.

## 2. Fuentes
Las fuentes curadas están en `${CLAUDE_SKILL_DIR}/fuentes/` (si no existe, buscá con Glob `**/becas/skills/buscar/fuentes/general.md` dentro de `~/.claude/plugins/`). Elegí:
- `general.md` siempre.
- Por rol: pediatra → `pediatria.md`; bioquímico/a o biólogo/a → `bioquimica.md`; matemático/a o científico/a de datos → `datos-matematica.md`. Roles mixtos o "otro" → los dos más cercanos.
- `grupos.md` si el alcance incluye grupo.

## 3. Scout
Lanzá el agente `becas:scout` con: "Hoy es <fecha>. Alcance: <para>, <ámbito>, tema: <tema o ninguno>. Fuentes del plugin: <rutas absolutas>. Relevá convocatorias nuevas y agregalas a convocatorias/tracker.csv."

## 4. Evaluador en paralelo
Por cada id nuevo, lanzá `becas:evaluador` con "Evaluá la convocatoria `<id>` del tracker." Todos en el mismo mensaje, de a máximo 5 por tanda. Al terminar, releé el tracker y verificá que cada id tenga `fit_score`, `prioridad` y `estado`; si una edición se pisó, completala con lo que devolvió el evaluador.

## 5. Mostrar
Filas en `nueva` o `evaluada` con cierre ≥ hoy, ordenadas por fit desc y cierre asc. Máximo 8:

| # | Convocatoria | Organismo | Para | Monto | Cierre (días) | Fit | Por qué |
|---|---|---|---|---|---|---|---|

Debajo, corto:
- Cuántas se encontraron, cuántas se descartaron (fit ≤2) y cuántas quedaron fuera del top 8.
- ⚠️ las que cierran en <14 días.
- Preguntas `[FALTA]` de los evaluadores, agrupadas y numeradas (responderlas mejora la próxima búsqueda; guardá las respuestas en `perfil/`).
- "Sin fecha / ventanilla abierta", en una línea.

Cerrá con el próximo paso concreto, con el comando listo para copiar: `/becas:postular <id>` para la mejor, `/becas:evaluar <id>` para las de fit 3 con dudas.

No envíes nada ni te registres en ningún portal.
