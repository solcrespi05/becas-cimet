---
name: revisar
description: Revisión completa de un manuscrito antes de enviarlo - requisitos de la revista, guía de reporte, estructura, estadística, referencias y revisor par simulado - con un informe único priorizado. Usar cuando pida /pub:revisar, "revisá el paper antes de mandarlo", "qué le van a criticar", "está listo para enviar?".
argument-hint: <revista objetivo> (adjuntá el manuscrito)
---

# /pub:revisar $ARGUMENTS

## 0. Preparación
Leé y seguí `${CLAUDE_PLUGIN_ROOT}/recursos/preparacion.md` (si no se expandió, Glob `**/pub/recursos/preparacion.md` en `~/.claude/plugins/`). Hace falta el manuscrito completo en `manuscrito.md`. Sin revista objetivo, preguntá; si no hay, se revisa sin el control de formato.

## 1. Requisitos de la revista
Si no existe `revista.md`, lanzá `pub:lector-revista` y esperá (los demás lo usan).

## 2. Revisiones en paralelo
En un mismo mensaje lanzá:
- `pub:guias-reporte` (pasale la ruta a `guias-reporte.md`).
- `pub:editor-estructura`.
- `pub:revisor-estadistico` (pasale la ruta a `docx_a_texto.py` por si hay tablas en Word).
- `pub:verificador-referencias` (pasale la ruta a `fuentes-literatura.md`).
- `pub:revisor-par` con **solo** las rutas a `manuscrito.md` y `revista.md`: sin resúmenes ni contexto de los otros.

## 3. Control de formato (lo hacés vos)
Contra `revista.md`: conteos (texto, abstract, título), cantidad de tablas, figuras y referencias, secciones obligatorias, declaraciones presentes (ética, conflictos, financiamiento, datos, contribuciones, uso de IA).

## 4. Informe único
Escribí `manuscritos/<id>/revision/informe.md` y mostralo:
1. **Veredicto**: listo para enviar / listo con cambios menores / necesita trabajo — en una línea, y la recomendación del revisor par.
2. **Bloqueantes** (cualquier agente): referencias inexistentes o retractadas, inconsistencias numéricas, requisitos de formato incumplidos, ítems ausentes de la guía que la revista exige, declaraciones faltantes.
3. **Importantes**: major comments del revisor par, problemas de estructura de impacto alto, sugerencias estadísticas relevantes.
4. **Menores**, agrupados.
5. **Preguntas para los autores** (todo lo que no se puede resolver sin ellos), numeradas.
6. Rutas a cada informe detallado en `revision/`.
Deduplicá: si dos agentes señalan lo mismo, va una vez con ambas fuentes.

Si la revista exige declarar el uso de IA, agregá un borrador de declaración según su política (los autores deciden si y cómo usarla).

## 5. Próximo paso
Ofrecé: corregir con `/pub:escribir <sección>` lo de estructura, `/pub:referencias` para reemplazar referencias problemáticas, `/pub:pulir` al final, `/pub:carta` para la cover letter. No envíes nada.
