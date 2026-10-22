---
name: actualizar
description: Registra novedades de una postulación - enviada, entrevista, aceptada, rechazada, sin respuesta, descartada - en el tracker y en historial.md. Usar cuando pida /becas:actualizar o diga "ya envié X", "ya apliqué a X", "me llamaron para entrevista", "me rechazaron", "me dieron la beca", "no voy a postular a X".
argument-hint: <id> <qué pasó>
---

# /becas:actualizar $ARGUMENTS

Si no queda claro a qué convocatoria se refiere (buscá por id o nombre aproximado en `convocatorias/tracker.csv`) o qué pasó, preguntá una sola vez.

Fecha = hoy, salvo que diga otra. Toda nota en el tracker se antepone a `notas` como `[AAAA-MM-DD] <qué pasó> | `, sin borrar lo anterior.

## Según lo que pasó
- **Enviada** ("ya envié", "ya apliqué"):
  - `estado: enviada`.
  - En `convocatorias/historial.md`, entrada nueva arriba de todo (debajo del resumen): fecha, qué se mandó (listá `convocatorias/<id>/final/`; preguntá si mandó algo distinto), próximos hitos según `bases.md` con fuente (fecha de resultados, entrevistas), sección "Novedades" vacía.
  - Agregá la fila a la tabla "Resumen".
  - Si quedaban archivos `INCOMPLETO_`, preguntá si los completó por fuera (no lo des por hecho).
- **Entrevista**: `estado: entrevista`; novedad con fecha en `historial.md` y en `notas`. Ofrecé preparar la entrevista con preguntas probables según los criterios de `bases.md` y respuestas basadas solo en `perfil/`.
- **Aceptada / rechazada / sin respuesta**: `estado: resultado`, anotando cuál en `notas` y en `historial.md`. Actualizá "Resumen". Si fue aceptada, sugerí sumarla a `perfil/persona.md` §5 (financiamientos obtenidos) y preguntá antes de escribir. Si fue rechazada y hubo devolución, guardala en `historial.md`: sirve para la próxima.
- **Descartada** ("no voy a postular"): `estado: descartada` con el motivo en `notas`.

Mostrá en 2–3 líneas qué cambió.
