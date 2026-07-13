# EBA Protokoll Codex Plugin

Native Codex plugin for producing EBA-compliant meeting records from raw transcripts with the original QMG templates.

## Install

```bash
codex plugin marketplace add BhaveshY/eba-protokoll-codex-plugin
codex plugin add eba-protokoll@eba-protokoll-codex-plugin
```

## Contents

- Marketplace: `.agents/plugins/marketplace.json`
- Plugin: `plugins/eba-protokoll/`
- Manifest: `plugins/eba-protokoll/.codex-plugin/plugin.json`
- QMG templates: `plugins/eba-protokoll/references/templates/qmg/`

## Use

Start a new Codex thread after installation and ask it to create or continue an EBA protocol from a transcript. Codex selects Gesprächsnotiz, Protokoll-einfach, LP1-4/BIM, or LP5 and can also prepare transcripts, resolve participants, extract topics, and validate a finished record.

## Prerequisites

- Python 3 available on PATH.
- Microsoft Word on Windows for the production PDF path. LibreOffice and macOS Pages are supported fallbacks.

## Development

```bash
python3 scripts/validate_codex_plugin.py plugins/eba-protokoll
node plugins/eba-protokoll/scripts/validate-references.mjs
python3 plugins/eba-protokoll/scripts/smoke_render.py
```
