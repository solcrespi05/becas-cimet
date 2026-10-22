---
name: estado
description: Muestra las convocatorias activas ordenadas por cierre, con documentos listos y faltantes, alertas de lo que cierra en menos de 14 días, y las postulaciones enviadas con su próximo hito. Usar cuando pida /becas:estado, "cómo vengo", "qué tengo pendiente" o "qué cierra pronto".
---

# /becas:estado

Solo lectura: no lances agentes ni modifiques archivos. Si una fila activa tiene cierre < hoy, proponé pasarla a `cerrada` (no lo hagas sin ok).

Si no existe `convocatorias/tracker.csv`, decí que primero hay que correr `/becas:empezar`.

## Pasos
1. Leé `convocatorias/tracker.csv`. Activas = `nueva`, `evaluada`, `en_preparacion`, `lista_para_enviar`. Ordená por `cierre` asc.
2. Por cada activa con `convocatorias/<id>/checklist.md`: contá ítems por estado y tomá la próxima fecha interna. Listá `final/` (`INCOMPLETO_` cuenta como faltante).
3. **Alertas** arriba:
   - 🔴 cierre (interno u organismo) en <14 días, con lo que falta.
   - 🟠 fechas internas vencidas (pedir cartas, aval institucional) sin completar.
   - ⚪ activas con cierre pasado.
4. Tabla:

   | Cierre | Días | Convocatoria | Para | Estado | Fit | Listos | Faltan | Próxima fecha interna |
   |---|---|---|---|---|---|---|---|---|

   "Faltan" nombra documentos concretos. Sin checklist: "sin checklist → `/becas:evaluar <id>`".
5. **Enviadas** (de `convocatorias/historial.md` y filas `enviada` / `entrevista`):

   | Convocatoria | Enviada | Días desde envío | Estado | Próximo hito |
   |---|---|---|---|---|

   Si una fila está `enviada` sin entrada en `historial.md`, avisá.
6. Una línea final con la acción más urgente y su comando.
