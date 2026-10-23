# Herramientas de investigación — CIMET

Dos plugins de [Claude Code](https://claude.com/claude-code) para pediatras, bioquímicos, matemáticos y científicos de datos:

- **`becas`**: encuentra becas, fellowships y grants (nacionales e internacionales) según tu rol y sector, evalúa si calificás y prepara la postulación.
- **`pub`**: ayudante de escritura académica. Escribe y pule papers y abstracts, busca referencias reales y verificadas para Zotero, y revisa el manuscrito antes de enviarlo.

**Claude ayuda y prepara; ustedes deciden y envían.** Nada se manda, ni se sube, ni se registra en ningún portal.

## Instalación (una sola vez)

En Claude Code (terminal o app de escritorio):

```
/plugin marketplace add solcrespi05/becas-cimet
/plugin install becas@cimet
/plugin install pub@cimet
```

Instalá uno o los dos.

---

## `becas`: becas y grants

1. Creá una carpeta para tus becas (ej. `Documentos/mis-becas`) y abrí Claude Code ahí.
2. Escribí:

| Comando | Qué hace |
|---|---|
| `/becas:empezar` | Te hace 4 preguntas, te pide el CV y arma tu perfil. Una sola vez. |
| `/becas:buscar` | Busca convocatorias abiertas para vos y te muestra las mejores. Podés agregar `grupo`, `nacional`, `internacional` o un tema: `/becas:buscar RSV`. |
| `/becas:evaluar <link>` | ¿Califico? Lee las bases reales y arma la lista de documentos y fechas. |
| `/becas:postular <id>` | Prepara CV, cartas, propuesta, mails a referentes. Todo queda en `convocatorias/<id>/final/`. |
| `/becas:estado` | Qué cierra pronto, qué te falta, qué enviaste. |
| `/becas:actualizar <id> <qué pasó>` | "enviada", "entrevista", "aceptada", "rechazada". También con tus palabras: "ya envié la de EMBO". |

### Qué queda en tu carpeta

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

**`institucion.md`, completarlo una vez entre todos:** los grants de grupo e internacionales piden datos del Centro (nombre legal, registros NIH/SAM, PIC europeo, comité de ética, quién firma avales). Conviene que la oficina de proyectos lo complete una vez y lo comparta.

---

## `pub`: escritura académica

Abrí Claude Code en una carpeta de trabajo (ej. `Documentos/escritura`) y escribí el comando. Podés **adjuntar el Word (.docx)**, un PDF o **pegar el texto**: se acepta todo.

| Comando | Qué hace |
|---|---|
| `/pub:escribir <sección>` | El ayudante principal: escribe o mejora introducción, métodos, resultados, discusión, a partir de tus notas o borrador, y busca las referencias que hagan falta. |
| `/pub:referencias <tema o frase>` | Busca bibliografía real (PubMed, Europe PMC, Crossref, Semantic Scholar), lee los abstracts y te la deja lista para Zotero. Con `verificar` chequea tu lista de referencias. |
| `/pub:abstract <revista o congreso>` | Abstract con la estructura y el límite exactos, con los números idénticos a los del manuscrito. |
| `/pub:pulir` | Corrige el inglés (o castellano) sin cambiar el contenido y te explica los cambios. |
| `/pub:revisar <revista>` | Revisión completa antes de enviar: requisitos de la revista, guía de reporte (CONSORT, STROBE, TRIPOD+AI…), estructura, estadística, referencias y un revisor par simulado. |
| `/pub:responder` | Pegás los comentarios de los revisores y arma la respuesta punto por punto y los cambios al manuscrito. |
| `/pub:carta <revista>` | Cover letter al editor. |

### Referencias a Zotero

Cada búsqueda deja en `manuscritos/<id>/referencias/`:
- `dois.txt` → en Zotero, botón de varita mágica (**Agregar elemento por identificador**) y pegás todo.
- `refs.bib` → o **Archivo → Importar**.
- `fichas.md` → qué dice cada referencia y para qué frase sirve.

Después las insertás en Word con el complemento de Zotero, en el estilo de la revista (`revista.md` te dice cuál elegir).

### Reglas que siguen todos los agentes de `pub`

1. **Los datos no se tocan**: ningún número, n, valor p, IC ni conclusión se crea o se cambia.
2. **Ninguna referencia sin verificar**: toda cita existe en PubMed/Crossref, tiene DOI o PMID comprobado y respalda lo que se afirma. Si no hay, queda `[CITA: ...]`.
3. **No exagerar**: el lenguaje respeta el diseño (observacional → "se asoció con").
4. **Confidencialidad**: el manuscrito no se sube a otros servicios; las búsquedas usan términos generales. Nunca datos identificables de pacientes.
5. **Cambios visibles**: todo lo que se reescribe se explica.
6. Si la revista pide declarar el uso de IA, se prepara un borrador de declaración para que los autores decidan.

### Qué queda en tu carpeta

```
escritura/
├── CLAUDE.md
├── perfil/grupo.md           (opcional) líneas, publicaciones y revistas del grupo
└── manuscritos/<id>/
    ├── original/             tu Word, tablas, comentarios de revisores (no se modifican)
    ├── manuscrito.md         texto vigente
    ├── notas.md              pregunta, diseño, mensaje principal, revista
    ├── revista.md            requisitos reales de la revista
    ├── referencias/          refs.bib · dois.txt · fichas.md
    ├── borradores/           versiones, nunca se pisan
    ├── revision/             informes de cada revisor
    └── final/
```

Hoy los resultados salen en Markdown para copiar a Word (o a .docx con `pandoc` si está instalado). **Próxima versión:** devolver el Word con control de cambios y comentarios.

---

## Mantener los plugins

- **becas, fuentes por sector:** `plugins/becas/skills/buscar/fuentes/`. Agregar o sacar programas es editar una línea.
- **pub, recursos:** `plugins/pub/recursos/` (reglas, APIs de literatura, guías de reporte, conversor de Word).
- **Agentes:** `plugins/<plugin>/agents/`. **Skills:** `plugins/<plugin>/skills/<nombre>/SKILL.md`.
- Al cambiar algo, subí `version` en `plugins/<plugin>/.claude-plugin/plugin.json` y en `.claude-plugin/marketplace.json`. Los colegas actualizan con `/plugin marketplace update cimet`.

Los datos de cada investigador quedan en su computadora, nunca en este repo.
