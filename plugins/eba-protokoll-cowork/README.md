# EBA Protokoll Cowork Codex Plugin

Codex plugin for turning EBA Protokoll App transcripts into QMG-based protocols.

## Use

- Prepare a transcript file from the EBA Protokoll App.
- Ask Codex to use the `eba-protokoll` skill, or one of the protocol-specific skills.
- Keep outputs in the current project folder unless the user specifies another path.

## Included content

- `skills/` - EBA protocol routing, transcript preparation, LP1-4, LP5, simple protocol, continuation, and Gesprächsnotiz workflows.
- `scripts/` - renderer and smoke checks.
- `references/templates/qmg/` - original QMG Word/Excel templates used by the renderer.
- `commands/` and `agents/` - source workflow prompts retained as plugin references for Codex users.

## Prerequisites

- Python 3 on PATH.
- `pip install -r scripts/requirements.txt` before local renderer smoke tests.
- Microsoft Word on Windows for best DOCX/PDF rendering.
