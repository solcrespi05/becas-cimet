# Becas y grants — Centro INFANT de Medicina Traslacional

Plugin de [Claude Code](https://claude.com/claude-code) para encontrar becas, fellowships y grants (nacionales e internacionales) según tu rol y sector: pediatría, bioquímica, matemática y ciencia de datos. Sirve para becas individuales y para grants de grupo.

**Claude busca y prepara; vos enviás.** Nada se manda, ni se sube, ni se registra en ningún portal sin vos.

## Instalación (una sola vez)

En Claude Code (terminal o app de escritorio):

```
/plugin marketplace add <usuario-u-org>/becas-infant
/plugin install becas@infant-becas
```

Reemplazá `<usuario-u-org>` por la cuenta de GitHub donde esté publicado este repo.

## Uso

1. Creá una carpeta para tus becas (ej. `Documentos/mis-becas`) y abrí Claude Code ahí.
2. Escribí:

| Comando | Qué hace |
|---|---|
| `/becas:empezar` | Te hace 4 preguntas, te pide el CV y arma tu perfil. Una sola vez. |
| `/becas:buscar` | Busca convocatorias abiertas para vos y te muestra las mejores. Podés agregar `grupo`, `nacional`, `internacional` o un tema: `/becas:buscar RSV`. |
| `/becas:evaluar <link>` | ¿Califico? Lee las bases reales y arma la lista de documentos y fechas. |
| `/becas:postular <id>` | Prepara CV, cartas, propuesta, mails a referentes. Todo queda en `convocatorias/<id>/final/`. |
| `/becas:estado` | Qué cierra pronto, qué te falta, qué enviaste. |
| `/becas:actualizar <id> <qué pasó>` | "enviada", "entrevista", "aceptada", "rechazada". También podés decirlo con tus palabras: "ya envié la de EMBO". |

No hace falta explicar nada más: tu perfil queda guardado y las skills lo leen solas.

## Qué queda en tu carpeta

```
mis-becas/
├── CLAUDE.md                 reglas (no inventar, no enviar, citar fuentes)
├── perfil/
│   ├── persona.md            rol, etapa, líneas, qué buscás
│   ├── cv.md                 tu CV completo
│   ├── grupo.md              tu grupo (para grants de equipo)
│   ├── institucion.md        datos administrativos del Centro
│   └── referencias.md        quiénes te escriben cartas
└── convocatorias/
    ├── tracker.csv           todas las convocatorias
    ├── historial.md          lo que enviaste y novedades
    ├── fuentes-propias.md    tus fuentes extra
    └── <id>/                 bases, checklist, borradores, final
```

Tus datos quedan en tu computadora, no en este repo.

## `institucion.md`: completarlo una vez entre todos

Los grants de grupo e internacionales piden datos del Centro (nombre legal, registros NIH/SAM, PIC europeo, comité de ética, quién firma avales). Conviene que una persona de la oficina de proyectos lo complete una vez y lo comparta. Cada colega lo pega en su `perfil/institucion.md`.

## Reglas que siguen todas las skills

1. No inventan logros, publicaciones, cifras ni resultados: todo sale de tu `perfil/`. Si falta algo, aparece `[FALTA: ...]` y te preguntan.
2. No envían nada.
3. Citan la fuente (link + fecha) de cada requisito y fecha de cierre.
4. Escriben en el idioma de la convocatoria y respetan límites con margen (≤95%).
5. Nunca copian datos identificables de pacientes.

## Mantener el plugin

- **Fuentes por sector:** `plugins/becas/skills/buscar/fuentes/` (`general.md`, `pediatria.md`, `bioquimica.md`, `datos-matematica.md`, `grupos.md`). Agregar o sacar programas es editar una línea. Cuando el buscador detecta una fuente discontinuada, lo avisa.
- **Agentes:** `plugins/becas/agents/` (scout, evaluador, extractor-requisitos, redactor-cv, redactor-cartas, revisor, coordinador-referencias).
- **Skills:** `plugins/becas/skills/<nombre>/SKILL.md`.
- **Plantillas de la carpeta de trabajo:** `plugins/becas/skills/empezar/plantillas/`.
- Al cambiar algo, subí `version` en `plugins/becas/.claude-plugin/plugin.json` y en `.claude-plugin/marketplace.json`. Los colegas actualizan con `/plugin marketplace update infant-becas`.
