---
name: carta
description: Escribe la cover letter al editor para enviar un manuscrito, con lo que pide la revista (novedad, ajuste al scope, declaraciones, revisores sugeridos). Usar cuando pida /pub:carta, "armame la cover letter", "carta al editor".
argument-hint: <revista> (con el manuscrito ya cargado)
---

# /pub:carta $ARGUMENTS

## 0. Preparación
Leé y seguí `${CLAUDE_PLUGIN_ROOT}/recursos/preparacion.md` (si no se expandió, Glob `**/pub/recursos/preparacion.md` en `~/.claude/plugins/`). Si no existe `revista.md`, lanzá `pub:lector-revista`.

## 1. Datos
De `notas.md`, `manuscrito.md` y `revista.md` sacá: título, tipo de artículo, hallazgo principal, por qué encaja en la revista (con datos del scope oficial y fuente), y lo que la revista exige en la carta. Lo que falte (autor de correspondencia, declaraciones, revisores sugeridos o excluidos, preprint previo) → preguntá una sola vez.

## 2. Redacción
Lanzá `pub:redactor-academico` en modo "cover letter": máximo una página, sin repetir el abstract; qué preguntaron, qué encontraron, por qué importa a los lectores de esta revista, y las declaraciones requeridas (originalidad, no enviado a otra revista, aprobación de todos los autores, conflictos). Revisores sugeridos: solo los que den los autores; nunca propongas nombres por tu cuenta.

## 3. Mostrar
La carta completa en el chat, la ruta del borrador y los `[FALTA]`. Recordá que no se envió nada.
