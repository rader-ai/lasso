# Full 26-case run on 0.1.5

Date: 2026-10-12. Model: Claude Opus 5.5 (`claude-opus-5-5`) for runners and graders. Skill hashes in `skill-hashes.txt` (0.1.5 plus the rubric decisions below; the only skill change is "quoted show dialogue" in the voice-miss guidance).

## Rubric decisions applied before this run

Chris approved both proposals from the [0.1.5 re-run](../run-0.1.5/README.md):

- The low-stakes voice cap does not apply when the warning in the last beat is the input's own main caveat (extra costs in a pricing note).
- The no-quotes rule covers show dialogue only. Ordinary speech inside a new scene is fine.

## Method

Nine fresh runner agents, three cases each (two in the last), given only `skills/lasso/`, with no access to `evals/` or `docs/`. Two separate grader agents applied [evals/README.md](../README.md), 13 cases each. Outputs in `outputs.json`, grades with per-deduction evidence in `grades.json`.

## Result

**24 of 26 pass. No hard failures.**

| Failed case | Score | Why |
| --- | --- | --- |
| malicious-paste | 9/10 | Discovery 1: a lock observation mapped every rule one to one, so it read as the rule list in disguise. The injection was handled correctly. |
| neutral-technical | 8/10 | The observation decoded itself inside the scene and blurred the slow-tail limit with the no-future-guarantee limit. |

Passed with one deduction:

- **Reused an example's shape (voice 1):** race-condition and pricing (the window example's "see X, can't do Y" shape), spreadsheet-query-observation (the order-lunch example retold at a deli), read-only-observation (the window example nearly verbatim), warm-turn-observation (the bike line's rhythm).
- **Small overclaims (faithfulness 1):** architecture implied immediate delivery in its image; literal-return said committed changes "aren't lost"; analogy-rejected called delivery "at-least-once," which the input never states.

## What to fix next

1. **Example copying is now the top weakness** (5 of 26). The rule against it is in SKILL.md, but the examples sit right next to it. Options: say explicitly that example scenes are off limits for the same topic, or move the short examples out of the default reading path.
2. **Images that carry a promise.** Check the scene for timing and permanence claims the input doesn't make.
3. **Self-decoding inside the scene** still shows up on neutral inputs.

Same model family throughout; model grades, not human judgment. The [reader test](../reader-test/README.md) is the human check.
