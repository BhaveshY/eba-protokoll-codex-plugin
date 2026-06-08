# EBA Protokoll Codex Plugin

Standalone Codex plugin repo for EBA protocol generation from raw transcripts.

## Install

```text
/plugin marketplace add BhaveshY/eba-protokoll-codex-plugin
/plugin install eba-protokoll-cowork@eba-protokoll-codex-plugin
```

## Contents

- Marketplace: `.agents/plugins/marketplace.json`
- Plugin: `plugins/eba-protokoll-cowork/`
- Manifest: `plugins/eba-protokoll-cowork/.codex-plugin/plugin.json`
- QMG templates: `plugins/eba-protokoll-cowork/references/templates/qmg/`

## Use

Ask Codex to create or continue an EBA protocol from a transcript. The plugin skills select the right format: Gesprächsnotiz, Protokoll-einfach, LP1-4, LP5, or protocol continuation.

## Prerequisites

- Python 3 available on PATH.
- Microsoft Word on Windows for the best PDF/DOCX output path.
