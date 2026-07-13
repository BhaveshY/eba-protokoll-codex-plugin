---
name: protokoll-themen-extrahieren
description: >-
  Extract structured topics, decisions, tasks, owners, deadlines, and proposed
  D/K categories from an EBA construction or planning transcript. Use when the
  user asks for topic extraction or when a protocol-generation skill needs a
  reliable intermediate topic structure from a long or complex transcript.
---

# Protokollthemen extrahieren

1. Resolve this skill directory and treat `../..` as `<plugin-root>`.
2. Read `<plugin-root>/references/workflows/themen-extraktion.md` completely.
3. Read the full transcript and determine the meeting date before converting
   relative deadlines.
4. Segment non-overlapping topic blocks, summarize without quotations, and
   extract decisions, tasks, owners, deadlines, and open questions.
5. Return the workflow's YAML structure. Use `zu klären` where an owner cannot
   be supported by the transcript.

For transcripts over 10,000 words, cap the result at 50 coherent topics and
merge overly granular blocks.
