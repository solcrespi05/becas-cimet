---
name: empezar
description: Primer paso del plugin de becas. Arma la carpeta de trabajo (perfil, tracker, plantillas) en la carpeta actual y completa el perfil con unas pocas preguntas sobre rol, etapa, líneas y qué busca la persona. Usar cuando pida /becas:empezar, "configurar becas", "armar mi perfil" o cuando otra skill de becas no encuentre perfil/persona.md.
argument-hint: (opcional) "grupo" para cargar también los datos del grupo
---

# /becas:empezar

Objetivo: que la persona pueda correr `/becas:buscar` en menos de 5 minutos. Preguntá poco; lo que no sepa queda `[FALTA]` y se completa después.

## 1. Carpeta de trabajo
- Las plantillas están en `${CLAUDE_SKILL_DIR}/plantillas/`. Si esa ruta no existe (la variable no se expandió), buscá con Glob `**/becas/skills/empezar/plantillas/CLAUDE.md` dentro de `~/.claude/plugins/`.
- Si la carpeta actual ya tiene `perfil/persona.md`: no pises nada. Decí que ya está configurada y ofrecé actualizar el perfil (saltá al paso 2 con las secciones a cambiar).
- Si la carpeta actual parece ser otra cosa (un repo de código, Documentos raíz, el escritorio), sugerí crear una subcarpeta `mis-becas/` y trabajar ahí; preguntá antes de crear.
- Copiá todo el contenido de `plantillas/` a la carpeta de trabajo (incluido `CLAUDE.md`, `perfil/`, `convocatorias/`). No copies archivos `.gitkeep`; creá las carpetas vacías.

## 2. Preguntas (una sola tanda con AskUserQuestion)
1. **Rol**: pediatra · bioquímico/a o biólogo/a · matemático/a · científico/a de datos o bioinformático/a (Other para epidemiología, enfermería, etc.).
2. **Etapa**: estudiante o residente · doctorando/a · posdoc o joven investigador/a (<10 años del doctorado) · investigador/a formado/a o jefe/a de grupo.
3. **Qué buscás** (multiSelect): becas o posdocs · estancias cortas y viajes · subsidios para mi proyecto · grants para el grupo.
4. **Dónde**: Argentina · exterior · ambos.

Después, en texto, pedí en un solo mensaje (todo opcional):
- Nacionalidad(es), año del último título y si es de CONICET.
- Tus temas en 2–3 líneas.
- Pegá tu CV (o el link a tu CVar exportado / el archivo). Si lo pega, guardalo tal cual en `perfil/cv.md`.

## 3. Completar
- Volcá las respuestas en `perfil/persona.md` sin inventar nada: lo que no dijo queda `[FALTA]`.
- Si pegó el CV, completá las secciones 3, 5 y 6 de `persona.md` **solo** con lo que esté en el CV, y decí qué completaste.
- Si eligió "grants para el grupo" o pasó el argumento `grupo`: preguntá nombre del grupo, PI, integrantes y disciplinas, y volcalo en `perfil/grupo.md`. Recordá que `perfil/institucion.md` lo completa una vez alguien del Centro y se comparte.
- Si en el Centro ya circula un `institucion.md` completo, pedí que lo pegue o indique la ruta y copialo.

## 4. Cerrar
Mostrá en 4–6 líneas: qué quedó cargado, qué `[FALTA]` importa más para la búsqueda (nacionalidad, etapa y año del título filtran mucho), y el próximo paso:

```
/becas:buscar
```

No busques convocatorias en esta skill.
