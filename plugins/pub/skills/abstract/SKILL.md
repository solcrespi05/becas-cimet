---
name: abstract
description: Escribe o mejora un abstract para una revista o un congreso respetando estructura y límite exactos, con los números idénticos a los del manuscrito o los resultados. Usar cuando pida /pub:abstract, "armame el abstract", "tengo que mandar un resumen al congreso", "achicá el abstract a 250 palabras".
argument-hint: <revista o congreso> (pegá o adjuntá el manuscrito, los resultados o el abstract actual)
---

# /pub:abstract $ARGUMENTS

## 0. Preparación
Leé y seguí `${CLAUDE_PLUGIN_ROOT}/recursos/preparacion.md` (si no se expandió, Glob `**/pub/recursos/preparacion.md` en `~/.claude/plugins/`).

## 1. Requisitos
- Si nombra revista o congreso y no hay `revista.md`, lanzá `pub:lector-revista` (para congresos: bases de envío de resúmenes, límite en palabras o caracteres, estructura, si cuenta título y autores, fecha de cierre).
- Sin revista ni congreso: preguntá. Si no sabe todavía, usá estructura IMRD estándar de 250 palabras y decilo.

## 2. Redacción
Lanzá `pub:redactor-academico` con: sección `abstract`, la fuente de los datos (manuscrito, tablas o resultados pegados), estructura y límite de `revista.md`. Indicale que:
- Cada número del abstract tiene que estar literal en la fuente.
- Conclusión: una oración que no exceda los datos; implicancia en otra.
- Si es para congreso y los resultados son preliminares, presentalos como tales.
- Sin citas, salvo que la revista las permita.

## 3. Pulido y control
- Lanzá `pub:editor-idioma` sobre el borrador.
- Verificá vos: conteo exacto con el criterio de la revista o el congreso (palabras o caracteres con o sin espacios), ≤95%, encabezados exactos, y que cada número coincida con la fuente (listá los que chequeaste).

## 4. Mostrar
El abstract completo en el chat, conteo vs. límite, los números chequeados contra la fuente, los `[FALTA]` y, si es para congreso, la fecha de cierre con fuente. Ofrecé una versión alternativa más corta si quedó por encima del 90%.
