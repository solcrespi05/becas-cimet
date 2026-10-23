---
name: referencias
description: Busca bibliografía real y verificada (PubMed, Europe PMC, Crossref, Semantic Scholar) para un tema, una pregunta o frases de un texto, y la deja lista para Zotero. También verifica una lista de referencias existente. Usar cuando pida /pub:referencias, "buscame bibliografía sobre X", "qué cito acá", "necesito una cita para esta frase", "chequeá mis referencias".
argument-hint: <tema, pregunta o frase> | verificar
---

# /pub:referencias $ARGUMENTS

## 0. Preparación
Leé y seguí `${CLAUDE_PLUGIN_ROOT}/recursos/preparacion.md` (si no se expandió, Glob `**/pub/recursos/preparacion.md` en `~/.claude/plugins/`). Si es una búsqueda suelta que no pertenece a un manuscrito, usá `manuscritos/busquedas-<AAAA>/` sin preguntar.

## 1. Qué modo
- **Buscar** (por defecto): `$ARGUMENTS` es un tema, una pregunta o frases. Si pegó un texto con marcas `[CITA]` o frases subrayadas, cada una es una necesidad.
- **Verificar**: si dice "verificar", "chequeá", o pega una lista de referencias → lanzá `pub:verificador-referencias` y saltá al paso 3.
- Si el pedido es muy amplio (ej. "bronquiolitis"), preguntá en una línea para qué la quiere (introducción de qué estudio, revisión, dato epidemiológico) y si hay preferencia de años o tipo de estudio. Si no responde algo concreto, buscá revisiones recientes más los estudios clave.

## 2. Buscar
Lanzá `pub:buscador-referencias` con las necesidades, la ruta a `fuentes-literatura.md`, la carpeta del manuscrito y las preferencias.

## 3. Mostrar
- Tabla: necesidad · referencia (primer autor, año, revista) · tipo de estudio · qué dice (1 línea) · citekey.
- Lo que no tiene respaldo encontrado, dicho claramente.
- Contradicciones en la literatura que convenga discutir.
- Para Zotero: pegar `referencias/dois.txt` en "Agregar elemento por identificador" (varita mágica), o importar `referencias/refs.bib`. Si hay estilo de la revista en `revista.md`, recordá el nombre del estilo CSL a elegir.
- En modo verificar: problemas graves primero (inexistentes, retractadas, no respaldan), con la corrección propuesta.
