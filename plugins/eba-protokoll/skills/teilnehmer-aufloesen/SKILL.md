---
name: teilnehmer-aufloesen
description: >-
  Resolve speakers and build an EBA participant/distribution table from a
  transcript. Use when a transcript contains generic labels such as Sprecher 1,
  names or companies are unclear, abbreviations must be assigned, or the user
  asks to identify participants before creating an EBA protocol.
---

# Teilnehmer auflösen

1. Resolve this skill directory and treat `../..` as `<plugin-root>`.
2. Read `<plugin-root>/references/workflows/teilnehmer-aufloesung.md` completely.
3. Read `<plugin-root>/references/categories/firma-kuerzel.md` and any available
   project `protokoll-state.json`.
4. Inspect the whole transcript for self-introductions, forms of address,
   company context, and task acknowledgements.
5. Produce the workflow's YAML table and cite transcript timestamps as evidence.
6. Ask for confirmation before applying uncertain speaker mappings to a file.

Keep unresolved labels explicit; never guess a person without textual evidence.
