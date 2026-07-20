# EBA Protokoll Codex Plugin

Native Codex plugin for producing EBA-compliant meeting records from raw transcripts with the original QMG templates.

## Install

The repository is a public Codex marketplace. In Windows PowerShell:

```powershell
codex plugin marketplace add BhaveshY/eba-protokoll-codex-plugin
codex plugin add eba-protokoll@eba-protokoll-codex-plugin
codex plugin list
```

The final command should show
`eba-protokoll@eba-protokoll-codex-plugin` as `installed, enabled`. Restart the
Codex desktop app and start a new task after the first installation so the ten
bundled skills are loaded.

## Contents

- Marketplace: `.agents/plugins/marketplace.json`
- Plugin: `plugins/eba-protokoll/`
- Manifest: `plugins/eba-protokoll/.codex-plugin/plugin.json`
- QMG templates: `plugins/eba-protokoll/references/templates/qmg/`

## Use

Start a new Codex thread after installation and ask it to create or continue an EBA protocol from a transcript. Codex selects Gesprächsnotiz, Protokoll-einfach, LP1-4/BIM, or LP5 and can also prepare transcripts, resolve participants, extract topics, and validate a finished record.

Final protocols are never Markdown: Word-based formats produce DOCX + PDF,
BIM/Excel formats produce XLSX, and continuation workflows additionally keep
`protokoll-state.json`.

## Prerequisites

- Current Codex CLI or Codex desktop app with the stable `codex plugin` command.
- Python 3 available as `python` or `py -3` on Windows. The renderer installs
  its own Python packages on first use.
- Microsoft Word on Windows for the production PDF path. LibreOffice is the
  Windows fallback; macOS Pages is supported for development.

The GitHub verification workflow runs the complete manifest, reference,
DOCX/XLSX renderer, and no-Markdown-output suite on both Windows and Linux.

## Development

```bash
python3 scripts/validate_codex_plugin.py plugins/eba-protokoll
node plugins/eba-protokoll/scripts/validate-references.mjs
python3 plugins/eba-protokoll/scripts/smoke_render.py
```
