# Preparación común a todas las skills /pub:*

Hacelo rápido y sin preguntar lo que se puede deducir.

## 1. Recursos del plugin
`RECURSOS` = la carpeta de este archivo. Pasale a los agentes rutas absolutas a los archivos que necesiten (`fuentes-literatura.md`, `guias-reporte.md`, `docx_a_texto.py`).

## 2. Carpeta de trabajo
- Si la carpeta actual no tiene `CLAUDE.md`, copiá `RECURSOS/CLAUDE.md` ahí. Si ya hay un `CLAUDE.md` de otra cosa (ej. el de becas), agregá al final una sección "## Escritura académica (plugin pub)" con las reglas de `RECURSOS/CLAUDE.md`, sin borrar nada.
- Si la carpeta actual parece un repo de código, el escritorio o Documentos raíz, sugerí crear `escritura/` y trabajar ahí (preguntá antes).

## 3. Manuscrito
- Si hay un único `manuscritos/<id>/`, o el pedido nombra uno, usalo.
- Si no existe, crealo con un id corto con año (ej. `rsv-cohorte-2026`, `abstract-sap-2026`) y las subcarpetas `original/`, `referencias/`, `borradores/`, `revision/`, `final/`. Decí el id elegido.
- Si hay varios y no queda claro cuál, preguntá mostrando la lista.

## 4. Entrada del texto
Aceptá cualquiera de estas, sin pedir un formato en particular:
- **Archivo Word (.docx)**: copialo a `original/` (no modifiques el original) y convertilo:
  `python -I "RECURSOS/docx_a_texto.py" "<archivo.docx>" "manuscritos/<id>/manuscrito.md"` (en macOS/Linux puede ser `python3`).
  El script conserva títulos, tablas, comentarios de Word y avisa si hay control de cambios sin aceptar (incluye inserciones, omite borrados). Si falla, pedí que peguen el texto.
- **Texto pegado en el chat**: guardalo tal cual en `manuscrito.md` (o en `notas.md` si son ideas sueltas).
- **PDF**: leelo y guardá el texto en `manuscrito.md`.
- **Tablas** (.xlsx, .csv): copialas a `original/`.

## 5. Notas mínimas
Si `notas.md` no existe o le falta lo esencial para la tarea, preguntá **una sola vez**, todo junto y solo lo que no se pueda deducir del texto: revista o congreso objetivo, tipo de artículo, idioma, diseño del estudio, mensaje principal. Guardá las respuestas en `notas.md`.

## 6. Salida en Word
Los resultados quedan en Markdown en `borradores/` y `final/`. Para pasarlos a Word: copiar y pegar, o si `pandoc` está instalado, `pandoc final/<archivo>.md -o final/<archivo>.docx`. (Word con control de cambios: próxima versión del plugin.)
