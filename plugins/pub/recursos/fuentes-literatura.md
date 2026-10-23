# Cómo buscar y verificar literatura

APIs públicas, sin login. Usá `curl -s` (está en Windows, macOS y Linux); si no está disponible, WebFetch con la misma URL.
Codificá los espacios de las consultas como `+` o `%20`. Respetá los límites: no más de 3 pedidos por segundo a NCBI.

## PubMed (NCBI E-utilities) — biomedicina
- Buscar: `https://eutils.ncbi.nlm.nih.gov/entrez/eutils/esearch.fcgi?db=pubmed&retmode=json&retmax=20&sort=relevance&term=<consulta>`
  - Filtros útiles en `term`: `AND 2019:2026[dp]`, `AND (review[pt] OR systematic review[pt])`, `AND randomized controlled trial[pt]`, `AND english[la]`, campos `[tiab]` y `[mh]` (MeSH).
- Resumen (autores, revista, año, DOI): `https://eutils.ncbi.nlm.nih.gov/entrez/eutils/esummary.fcgi?db=pubmed&retmode=json&id=<pmid1,pmid2>`
- Abstract completo: `https://eutils.ncbi.nlm.nih.gov/entrez/eutils/efetch.fcgi?db=pubmed&rettype=abstract&retmode=text&id=<pmid>`
- Retractada: en esummary, `pubtype` incluye "Retracted Publication"; buscar también `<pmid> AND retraction of publication[pt]`.

## Europe PMC — biomedicina + preprints + texto completo abierto
- `https://www.ebi.ac.uk/europepmc/webservices/rest/search?format=json&resultType=core&pageSize=20&query=<consulta>`
- Devuelve abstract, DOI, PMID, si es preprint (`SRC:PPR`), citas recibidas (`citedByCount`) y `pubTypeList` (retracciones).
- Preprints: marcarlos siempre como "preprint, sin revisión por pares".

## Crossref — cualquier disciplina, metadatos por DOI
- Buscar por texto: `https://api.crossref.org/works?rows=10&query.bibliographic=<título o cita aproximada>`
- Verificar un DOI: `https://api.crossref.org/works/<doi>` (título, autores, año, revista; `update-to` / `relation` indican correcciones o retracciones).
- **BibTeX directo para Zotero:** `https://api.crossref.org/works/<doi>/transform/application/x-bibtex`

## Semantic Scholar — matemática, estadística, computación, ML
- `https://api.semanticscholar.org/graph/v1/paper/search?limit=20&fields=title,year,authors,venue,externalIds,abstract,citationCount&query=<consulta>`
- Puede responder 429 (límite): esperá unos segundos y reintentá una vez; si sigue, usá Crossref o arXiv.
- arXiv: `http://export.arxiv.org/api/query?max_results=20&search_query=all:<consulta>`

## Criterio de verificación (todas las referencias)
Una referencia está **verificada** solo si:
1. Existe en al menos una de estas bases con el mismo título, primer autor, año y revista.
2. Tiene DOI o PMID comprobado.
3. Se leyó al menos el abstract y respalda la frase específica donde se cita.
4. No está retractada (o, si lo está, solo se cita para hablar de la retracción).
