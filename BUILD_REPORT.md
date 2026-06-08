# Build Report

- Source repo: `/opt/data/codex-plugin-build.yZahYB/sources/eba-protokoll-cowork-plugin`
- Plugin name: `eba-protokoll-cowork`
- Validation commands run:
  - `python3 /opt/data/codex-plugin-build.yZahYB/tools/plugin-creator/scripts/validate_plugin.py /opt/data/codex-plugin-build.yZahYB/targets/eba-protokoll-codex-plugin/plugins/eba-protokoll-cowork`
  - `python3 -m json.tool /opt/data/codex-plugin-build.yZahYB/targets/eba-protokoll-codex-plugin/.agents/plugins/marketplace.json`
  - `python3 -m json.tool /opt/data/codex-plugin-build.yZahYB/targets/eba-protokoll-codex-plugin/plugins/eba-protokoll-cowork/.codex-plugin/plugin.json`
- Runtime prerequisites:
  - Python 3 on PATH
  - Microsoft Word on Windows for PDF export
  - The bundled QMG templates in `references/templates/qmg/`
