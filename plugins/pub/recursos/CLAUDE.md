# Escritura académica

Carpeta de trabajo del plugin `pub` (Centro INFANT de Medicina Traslacional). Claude ayuda a escribir, buscar referencias y revisar; **los autores deciden y envían**.

## Estructura

- `perfil/grupo.md` (opcional) → líneas del grupo, publicaciones previas, revistas habituales, terminología propia.
- `manuscritos/<id>/` → un manuscrito, abstract o póster por carpeta:
  - `original/` → lo que pasan los autores (.docx, tablas, figuras, comentarios de revisores). No se modifica.
  - `manuscrito.md` → texto vigente (convertido desde Word si hace falta).
  - `notas.md` → pregunta de investigación, diseño, resultados clave, revista o congreso objetivo, mensaje principal.
  - `revista.md` → requisitos reales de la revista o el congreso, con fuente.
  - `referencias/` → `refs.bib` (para Zotero), `dois.txt` (para "Agregar por identificador" en Zotero), `fichas.md` (qué dice cada referencia y para qué se usa).
  - `borradores/` → `<seccion>_v<n>.md`, nunca se sobrescriben.
  - `revision/` → informes de los revisores (idioma, estructura, estadística, guía de reporte, referencias, par).
  - `final/` → versión para que los autores pasen a Word o al portal.
- `id`: slug corto con año, ej. `rsv-cohorte-2026`, `abstract-sap-2026`.

## Reglas (agentes, skills y sesión principal)

1. **Los datos no se tocan.** Ningún número, n, porcentaje, valor p, IC, efecto ni conclusión se crea o se cambia: salen del manuscrito, las tablas o las notas de los autores. Si falta, `[FALTA: ...]`.
2. **Ninguna referencia sin verificar.** Toda cita existe en PubMed, Europe PMC o Crossref, con DOI o PMID comprobado, y respalda lo que se afirma. Si no, `[CITA: qué hace falta respaldar]`.
3. **No exagerar.** El lenguaje respeta el diseño: un estudio observacional "se asocia con", no "causa" ni "demuestra".
4. **Confidencialidad.** Manuscritos y datos no publicados no se suben a ningún servicio externo, salvo búsquedas de literatura con términos generales. Nunca se copian datos identificables de pacientes.
5. **Cambios visibles.** Al editar texto de los autores se explica qué cambió y por qué; nada se reescribe en silencio.
6. **Límites** de palabras, caracteres y referencias con margen (≤95% del máximo).
7. **Idioma**: el de la revista o el congreso; si no se sabe, se pregunta.
8. **Uso de IA**: si la revista pide declararlo, se redacta un borrador de declaración para que los autores decidan.
9. **Autoría y plagio**: no se copia texto de otras fuentes; las paráfrasis de trabajos ajenos llevan su cita.
