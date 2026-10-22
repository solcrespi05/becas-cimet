---
name: postular
description: Prepara una postulación completa para una convocatoria del tracker - checklist, CV y textos en paralelo, revisión con contexto limpio, una ronda de corrección, borradores de mail a referentes, y todo listo en convocatorias/<id>/final/. Sirve para becas individuales y grants de grupo. Nunca envía nada. Usar cuando pida /becas:postular <id> o "preparame la postulación a X".
argument-hint: <id del tracker>
---

# /becas:postular $ARGUMENTS

Reglas de `CLAUDE.md` de la carpeta de trabajo vigentes en todo el flujo. **No se envía nada**: todo queda en `convocatorias/<id>/final/`.

## 0. Precondiciones
- `$ARGUMENTS` tiene que ser un id del tracker. Si no lo es pero parece un link o nombre, corré primero la skill `becas:evaluar`. Sin argumento, mostrá los ids activos con mejor fit y preguntá.
- Si `fit_score` está vacío, corré `becas:evaluador`. Si queda ≤2, frená y preguntá si sigue.
- Si `perfil/cv.md` está vacío o `persona.md` es casi todo `[FALTA]`, frená: pedí que pegue el CV y decí qué secciones hacen falta. No redactes textos hechos de placeholders.
- Si es `para: grupo` y `perfil/grupo.md` está vacío, frená y pedí los datos del grupo (o `/becas:empezar grupo`).
- Pasá la fila a `estado: en_preparacion`.

## 1. Requisitos
Lanzá `becas:extractor-requisitos` con el id (actualiza la checklist si ya existe). Si devuelve `[FALTA: idioma de la postulación]`, preguntá el idioma. Si algo es inviable en el tiempo disponible (ej. aval institucional o registro NIH que no llega), mostralo y preguntá si sigue.

## 2. Redacción (en paralelo)
En un mismo mensaje:
- `becas:redactor-cv`: "Prepará el/los CV para `<id>` según checklist."
- `becas:redactor-cartas`: "Prepará todos los textos pedidos para `<id>` según checklist."
Si la checklist no pide CV, no lances `redactor-cv` (y viceversa).

## 3. Revisión (contexto limpio)
Lanzá `becas:revisor` con **solo** el id y las rutas de la última versión de cada borrador. Sin resúmenes ni opiniones de los redactores.

## 4. Corrección (máximo una ronda)
- Si es **NO APTO** por problemas graves corregibles redactando: relanzá solo los redactores afectados (en paralelo) con "Corregí los problemas graves de `revision.md` (ronda 1) que te tocan; generá nueva versión." Después, `becas:revisor` una vez más (ronda 2).
- No hay tercera ronda. Lo que siga grave, listalo sin esconderlo.
- Los `[FALTA]` no se corrigen redactando: pasan a la lista de pendientes.

## 5. Referencias
Si la checklist pide cartas (recomendación, apoyo, colaboración, mentor), lanzá `becas:coordinador-referencias` con el id.

## 6. Final
- Copiá a `final/` la última versión de cada borrador sin sufijo de versión (ej. `cv_academico.md`, `specific_aims.md`, `carta_motivacion.md`).
- Archivos con `[FALTA]` → prefijo `INCOMPLETO_`.
- Actualizá `checklist.md` y el tracker: `lista_para_enviar` solo si no hay `[FALTA]` ni graves; si no, queda `en_preparacion`.

## 7. Mostrar
1. Veredicto final del revisor y graves sin resolver.
2. Archivos en `final/` con conteo vs. límite.
3. **Lo que tenés que hacer vos**, ordenado por fecha: completar `[FALTA]`, enviar pedidos a referentes, trámites (aval del Centro, firmas, ética, registros), pasar los .md al formato pedido (PDF, Word, plantilla del portal), subir y enviar antes de <cierre>.
4. Si es de grupo: **lo que tiene que hacer la institución**, con fechas, listo para reenviar a la oficina de proyectos.
5. Recordatorio: no se envió nada. Cuando envíes, decime "ya envié `<id>`" o usá `/becas:actualizar <id> enviada`.
