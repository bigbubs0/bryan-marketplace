---
name: outreach
description: RETIRED 2026-08-05. Do not use. Superseded by the outreach-from-feed skill and the BD pre-send gate. This stub exists only so the outreach@bryan-marketplace plugin manifest still resolves.
disable-model-invocation: true
---

# RETIRED - do not generate from this skill

This skill was retired on 2026-08-05. It existed as five byte-identical copies
(md5 `4991b769d033`), three of them loadable, and carried three rules that
contradict canonical:

| Line | Said | Canonical |
|---|---|---|
| 42 | `Use "intelligence-driven search", "the data tells us..."` | Both are on the banned-language list |
| 60 | `Use 'Search Consultant' never 'recruiter'` | Wrong at retirement time (the term was retired 2026-07-20). Superseded again 2026-08-22: "Search Consultant" IS the client- and candidate-facing role term; owner is the CLAUDE.md Communication block, not this file |
| 63 | `150 words max for initial outreach` | Never binding. Real first-touch mean is 84.4 words across 335 sends |

**If you were about to generate BD outreach:** use `outreach-from-feed`, then run
`scripts/bd_pre_send_gate.py` before anything ships.

The original body is in git history, blob `7b8e6ee`:
`git show adc4b8a:plugins/outreach-plugin/skills/outreach/SKILL.md`. The `_to_delete`
copy and the `.bak-2026-08-05b-pre-retirement` sibling this stub used to cite were
removed 2026-09-05 - the `.bak` was byte-identical to that blob.

The durable fix is removing `outreach` from the plugin's skill list in
`repos/bryan-marketplace/plugins/outreach-plugin/` and re-releasing, then
`/plugin update bryan-marketplace`. This stub is the safe interim.
