# EBA Protokoll Codex Plugin

Codex plugin for turning EBA Protokoll App transcripts into QMG-based protocols.

## Use

- Prepare a transcript file from the EBA Protokoll App.
- Ask Codex to use the `eba-protokoll` skill, or one of the protocol-specific skills.
- Keep outputs in the current project folder unless the user specifies another path.

User-facing protocols are DOCX + PDF for Word-based QMG formats or XLSX for
Excel-based QMG formats. Markdown files under `references/` are internal
templates and regression fixtures only; the renderer deletes its temporary
Markdown input and never returns it as a finished protocol.

## Included content

- `skills/` - Native Codex skills for routing, transcript preparation, participant resolution, topic extraction, protocol formats, continuation, and validation.
- `scripts/` - renderer and smoke checks.
- `references/templates/qmg/` - original QMG Word/Excel templates used by the renderer.
- `references/workflows/` - detailed participant, topic-extraction, and validation procedures loaded by skills as needed.

## Prerequisites

- Python 3 on PATH.
- `pip install -r scripts/requirements.txt` before local renderer smoke tests.
- Microsoft Word on Windows for best DOCX/PDF rendering.


## Internal example fixtures

The plugin includes Markdown fixture representations for testing each supported
workflow. They are not user-facing output files:

- `references/examples/beispiel-transkript-bim.txt` -> `references/examples/beispiel-ausgabe-bim.md`
- `references/examples/beispiel-transkript-eba-interview.txt` -> `references/examples/beispiel-ausgabe-eba-interview.md`
- `references/examples/beispiel-transkript-einfach.txt` -> `references/examples/beispiel-ausgabe-einfach.md`
- `references/examples/beispiel-transkript-gespraechsnotiz.txt` -> `references/examples/beispiel-ausgabe-gespraechsnotiz.md`
- `references/examples/beispiel-transkript-lp1-4.txt` -> `references/examples/beispiel-ausgabe-lp1-4.md`
- `references/examples/beispiel-transkript-lp5.txt` -> `references/examples/beispiel-ausgabe-lp5.md`

Raw transcripts may omit project metadata. In that case the metadata fallback rules in `references/categories/metadaten-konvention.md` apply; non-project EBA interview notes use `Projekt-Nr. 000` rather than blocking the workflow.
