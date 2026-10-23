---
name: responder
description: Arma la respuesta a los revisores punto por punto (response letter) y la lista de cambios a hacer en el manuscrito, a partir de los comentarios recibidos de la revista. Usar cuando pida /pub:responder, "me llegaron los comentarios de los revisores", "ayudame con la revisión mayor", "armame la carta de respuesta".
argument-hint: (pegá o adjuntá la carta de decisión con los comentarios y el manuscrito enviado)
---

# /pub:responder $ARGUMENTS

## 0. Preparación
Leé y seguí `${CLAUDE_PLUGIN_ROOT}/recursos/preparacion.md` (si no se expandió, Glob `**/pub/recursos/preparacion.md` en `~/.claude/plugins/`). Guardá la carta de decisión en `original/decision_<AAAA-MM-DD>.md` y el manuscrito enviado como `manuscrito.md` si no estaba.

## 1. Desarmar los comentarios
Separá cada comentario del editor y de cada revisor, textual, numerado (E1, R1.1, R1.2, R2.1…). Clasificá cada uno:
- **Aceptar y cambiar** (claro y razonable).
- **Requiere datos o análisis nuevos** → pregunta para los autores (nunca se inventan resultados).
- **Aclarar sin cambiar** (malentendido del revisor: el texto ya lo decía o se puede explicar mejor).
- **Desacuerdo** → necesita argumento y evidencia; los autores deciden.
Mostrá esta tabla y preguntá **una sola vez** por los que requieren datos o decisión de los autores. Si los autores ya dieron indicaciones al pegar los comentarios, usalas.

## 2. Referencias nuevas (si hace falta)
Si un revisor pide comparar con literatura o respaldar algo, lanzá `pub:buscador-referencias` con esas necesidades. Si el revisor citó trabajos concretos, verificalos (pueden estar mal citados).

## 3. Redacción
Lanzá `pub:redactor-academico` con modo "respuesta a revisores": comentarios clasificados, indicaciones de los autores y referencias. Que genere:
- `borradores/respuesta_revisores_v<n>.md`: saludo breve al editor, y por comentario → comentario textual (en cursiva) · respuesta (cortés, concreta, sin servilismo) · cambio hecho con ubicación, en el idioma de la revista.
- `borradores/cambios_manuscrito_v<n>.md`: para cada cambio, sección, texto actual y texto propuesto, listo para aplicar con control de cambios en Word.
Lo que dependa de análisis nuevos queda `[FALTA: resultado de ...]`.

## 4. Revisión
Lanzá `pub:revisor-par` con contexto limpio, pasándole la carta de decisión original, la respuesta y los cambios propuestos, pidiendo que evalúe como el mismo revisor si cada comentario quedó bien atendido. Corregí una vez lo que marque como no resuelto.

## 5. Mostrar
Tabla resumen (comentario · tipo · estado: resuelto / falta dato / desacuerdo), rutas a la respuesta y a los cambios, los `[FALTA]` como tareas para los autores, y recordá el plazo de reenvío si figura en la carta de decisión.
