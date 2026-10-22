# Mis becas y grants

Carpeta de trabajo del plugin `becas` (Centro INFANT de Medicina Traslacional). Claude busca convocatorias y prepara postulaciones; **la persona envía todo**.

## Estructura

- `perfil/persona.md` → quién soy: rol, etapa, líneas, objetivos, qué busco. Fuente única de verdad.
- `perfil/cv.md` → CV completo (pegado tal cual).
- `perfil/grupo.md` → mi grupo o laboratorio, para grants de equipo (opcional).
- `perfil/institucion.md` → datos administrativos del Centro (registros, oficina de proyectos, ética). Se completa una vez y se comparte entre colegas.
- `perfil/referencias.md` → quiénes pueden escribirme cartas.
- `perfil/documentos/` → PDFs (títulos, certificados). Solo se lista, no se abre salvo que haga falta para un requisito.
- `convocatorias/tracker.csv` → una fila por convocatoria.
- `convocatorias/historial.md` → postulaciones enviadas y novedades.
- `convocatorias/fuentes-propias.md` → fuentes extra que quiero que se revisen siempre, y exclusiones.
- `convocatorias/<id>/` → `bases.md`, `checklist.md`, `borradores/`, `final/`, `revision.md`. Plantilla en `convocatorias/_plantilla/`.

## Convenciones del tracker

- Columnas: `id,nombre,organismo,link,para,monto,cierre,estado,fit_score,prioridad,notas`.
- `id`: slug en minúsculas con año de la edición, ej. `conicet-posdoc-2027`, `nih-k43-2027`. Es también el nombre de la carpeta.
- `para`: `persona` (beca o fellowship individual) o `grupo` (grant de proyecto, laboratorio o institucional).
- `cierre`: `AAAA-MM-DD` del organismo. Si hay cierre interno antes (aval del Centro, oficina de proyectos, universidad), va en `notas` y en `checklist.md`.
- `estado`: `nueva` → `evaluada` → `en_preparacion` → `lista_para_enviar` → `enviada` → `entrevista` → `resultado`; o `descartada` / `cerrada`.
- `fit_score`: 1–5. `prioridad`: `alta` / `media` / `baja`.
- Campos con comas van entre comillas dobles.
- Cambios de estado se anteponen a `notas` como `[AAAA-MM-DD] <qué pasó> | `, sin borrar lo anterior.

## Reglas (agentes, skills y sesión principal)

1. Nunca inventes logros, cifras, publicaciones, financiamientos, fechas ni experiencias. Todo dato sobre la persona o su grupo sale de `perfil/`. Si falta algo, marcalo `[FALTA: ...]` y preguntá.
2. Nunca envíes formularios, mails ni postulaciones. Todo queda en `convocatorias/<id>/final/`. Los mails a referentes o colaboradores quedan como borradores.
3. Citá la fuente (link + fecha consultada) de cada requisito, monto y fecha límite. Si dos fuentes se contradicen, decilo.
4. Escribí en el idioma que pida la convocatoria; si no dice, preguntá.
5. Respetá límites de palabras, caracteres o páginas con margen (≤95% del máximo).
6. Tono honesto y concreto, sin frases genéricas.
7. Datos de pacientes: nunca copies datos identificables de pacientes en ningún archivo. Resultados preliminares solo agregados y tal como figuran en `perfil/`.
