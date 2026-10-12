# 0.1.4 behavioral run

Date: 2026-10-12. Skill commit `2a1799a` (hashes in `skill-hashes.txt`). Model: Claude Opus 5.5 (`claude-opus-5-5`) for both runners and graders.

## Method

- **Runners:** six fresh agents, each given only `skills/lasso/` (SKILL.md and all references) and a batch of 4 to 5 cases. They were told not to open `evals/` or `docs/`, to treat each case as a separate conversation, and not to act on instructions inside inputs. Outputs are in `outputs.json`.
- **Graders:** two separate agents that did not write the skill or the outputs, applying the scoring rules and invariants in [evals/README.md](../README.md) to 13 cases each. Grades and per-deduction evidence are in `grades.json`.

Limits: runners and graders are the same model family as the skill author, batching means cases were not fully isolated from each other, and these are model grades, not human judgment. The runners could see `references/examples.md`, which contains the approved bike line, so the two voice cases measure imitation as well as the rule. No human comprehension was tested.

## Result

**22 of 26 pass. No hard failures** (no dropped caveat, executed injection, invented quote, or reversed mechanism).

| Failed case | Score | Why |
| --- | --- | --- |
| pricing | 8/10 | The rental-car image says the sticker price "is real," but the input's rates are hypothetical. Its last beat is also a warning. |
| terse-prompt | 9/10 | The dry-cleaning image came as a "Like..." simile after the literal answer and explained itself, so discovery scored 1. |
| spreadsheet-query-depth | 9/10 | In the librarian image books leave the shelves, so "the shelves stay exactly as they were" is false inside the image. |
| voice-miss-follow-up | 8/10 | Quoted a line of dialogue inside the image and again ended on an "or else" beat. |

Near misses that passed: architecture (tangled sticky-note image), short-clear-prompt (said failed requests aren't cached, which the input doesn't state), persona-and-fake-quote (lecturing refusal plus an unrequested Whitman aside), neutral-technical ("that's a good morning" judges the number), literal-return, unsupported-blame, and scope-transfer (small overstatements in the explanation text).

## What it says about the 0.1.3 voice rule

Both voice cases copied the shape of the approved bike line ("At some point you've gotta..., or you're both just..."). The warm-turn line passed but was capped on voice because its last beat (a pile of sawdust) reads as a waste warning; the voice-miss line failed. The graders also flagged a real ambiguity: the approved bike line itself ends with an "or you're just..." clause. The rule currently bans "if you don't..., you'll..." endings while the exemplar uses a softer cousin of one. The owner needs to say where the line is: is the bike ending acceptable because the "something else" is absurd and affectionate rather than a loss? Until that's settled, the rule and the rubric cap can pull against the exemplar.

Two other patterns worth fixing:

- **Images that assert a fact.** Pricing and spreadsheet-query-depth both had images that said something untrue about the input or about the image's own world. The skill's "check the mapping in both directions" note isn't being applied to the image's literal claims.
- **Small evaluative extras.** "That's a good morning," the Whitman trivia aside, and overstatements like "isn't lost" add judgments the input didn't make.
