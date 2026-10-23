---
name: pulir
description: Pule el idioma (inglés o castellano científico) de un texto o manuscrito sin cambiar su contenido, y explica los cambios principales. Usar cuando pida /pub:pulir, "corregime el inglés", "mejorá la redacción", "hacelo más claro", "revisá la gramática".
argument-hint: (opcional) sección a pulir; pegá o adjuntá el texto
---

# /pub:pulir $ARGUMENTS

## 0. Preparación
Leé y seguí `${CLAUDE_PLUGIN_ROOT}/recursos/preparacion.md` (si no se expandió, Glob `**/pub/recursos/preparacion.md` en `~/.claude/plugins/`). Para un texto corto pegado en el chat no hace falta preguntar nada más.

## 1. Pulir
- Texto corto (≤1 página): lanzá un solo `pub:editor-idioma`.
- Manuscrito completo: lanzá un `pub:editor-idioma` por sección grande (introducción, métodos, resultados, discusión, abstract), en paralelo, y pasales la terminología clave del manuscrito para que la unifiquen igual. Después revisá vos la consistencia entre secciones (mismos términos y abreviaturas).

## 2. Mostrar
- Texto corto: el texto pulido completo en el chat.
- Manuscrito: rutas a los archivos pulidos y a los informes de cambios.
- Los 5 tipos de cambio más frecuentes, con un ejemplo de cada uno.
- Las `[DUDA]`: frases donde la corrección podría cambiar el sentido. Los autores deciden.
- Conteo antes/después y si respeta el límite de `revista.md`.
