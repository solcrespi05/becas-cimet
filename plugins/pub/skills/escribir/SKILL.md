---
name: escribir
description: Ayudante de escritura académica. Escribe o mejora una sección (introducción, métodos, resultados, discusión, abstract, resumen lego) a partir de notas, datos o un borrador, buscando y verificando las referencias que hagan falta. Usar cuando pida /pub:escribir, "ayudame a escribir la introducción", "armame la discusión", "mejorá este párrafo", "convertí estas notas en métodos".
argument-hint: <sección o pedido> (podés adjuntar o pegar el borrador o las notas)
---

# /pub:escribir $ARGUMENTS

## 0. Preparación
Leé y seguí `${CLAUDE_PLUGIN_ROOT}/recursos/preparacion.md`. Si la variable no se expandió, buscá con Glob `**/pub/recursos/preparacion.md` dentro de `~/.claude/plugins/`. Las reglas de `CLAUDE.md` valen en todo el flujo: los datos no se tocan y ninguna referencia entra sin verificar.

## 1. Entender el pedido
De `$ARGUMENTS` y lo que haya pegado o adjuntado, deducí:
- **Sección** y **modo**: escribir de cero (desde notas o resultados) · reescribir un borrador · mejorar un párrafo puntual · acortar a un límite.
- Si la revista o congreso figura en `notas.md` y no existe `revista.md`, lanzá `pub:lector-revista` en paralelo con el paso 2.
- Para un párrafo corto y sin necesidad de citas nuevas, saltá directo al paso 3 y respondé en el chat además de guardar el borrador.

## 2. Referencias (si la sección las necesita)
Introducción y discusión casi siempre necesitan; métodos solo para técnicas o escalas; resultados casi nunca.
- Si `referencias/fichas.md` ya cubre lo necesario, seguí.
- Si no, lanzá `pub:buscador-referencias` con: los puntos que la sección tiene que respaldar (sacados de las notas o el borrador, en términos generales), la ruta a `fuentes-literatura.md` y al manuscrito, y el límite de referencias de `revista.md` si existe.

## 3. Redacción
Lanzá `pub:redactor-academico` con: id, sección, modo, extensión o límite, y el borrador o las notas a usar.

## 4. Completar citas (máximo una vuelta)
Si el borrador volvió con marcas `[CITA: ...]`, lanzá `pub:buscador-referencias` con esas marcas y después `pub:redactor-academico` para reemplazarlas (nueva versión). Las que sigan sin respaldo quedan marcadas: no se fuerzan.

## 5. Mostrar
- El texto (si es corto, completo en el chat; si es largo, la ruta y el primer párrafo).
- Conteo vs. límite.
- Referencias usadas: citekey · primer autor y año · qué respalda.
- `[FALTA: ...]` como preguntas numeradas para los autores; `[CITA]` sin respaldo encontrado.
- Cómo pasar las referencias a Zotero: en Zotero, botón de varita mágica ("Agregar elemento por identificador") y pegar el contenido de `referencias/dois.txt`; o Archivo → Importar `referencias/refs.bib`. Después insertarlas en Word con el complemento de Zotero.
- Próximo paso sugerido (ej. `/pub:escribir discusión`, `/pub:pulir`, `/pub:revisar`).
