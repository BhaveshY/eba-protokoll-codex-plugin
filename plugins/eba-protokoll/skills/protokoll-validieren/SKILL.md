---
name: protokoll-validieren
description: >-
  Validate an EBA meeting record before delivery. Use when the user asks to
  prüfen, validieren, review, QA, or check a Gesprächsnotiz, Protokoll-einfach,
  LP1-4/BIM, or LP5 protocol for template compliance, numbering, deadlines,
  responsibilities, transcript fidelity, or continuation-state consistency.
---

# EBA-Protokoll validieren

1. Resolve this skill directory and treat `../..` as `<plugin-root>`.
2. Read `<plugin-root>/references/workflows/protokoll-validierung.md` completely.
3. Read the protocol to validate. If available, also read its source transcript
   and `protokoll-state.json` for cross-checks.
4. Apply the format-specific checks from the workflow. Do not require tracking
   columns for Gesprächsnotiz or Protokoll-einfach.
5. Return the specified YAML result with concrete locations and fixes.
6. If validation runs inside a generation workflow, fix safe formatting issues,
   validate again, and render only after no blocking errors remain.

Do not silently invent missing facts. Treat documented metadata fallbacks as
warnings rather than errors.
