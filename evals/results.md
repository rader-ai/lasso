# Validation report: 0.1.3 to 0.1.6

Date: 2026-10-12. This revision keeps the 0.1.2 response design (a freestanding everyday observation, with fuller explanation and consequential caveats available) and adds a voice rule: make the final turn a smile, not a sermon. It also tells the skill how to handle a voice miss (“doesn't sound like Ted”) separately from a comprehension miss.

## Evidence for this revision

The rule comes from one owner review on 2026-10-12. Asked to lasso an explanation of recursive loops, the skill produced “Taste the sauce, adjust it, taste again. A cook who never decides it's ready never gets dinner on the table.” Chris said it didn't feel like something Ted Lasso would say. A re-pitched line, “Teaching a kid to ride a bike goes wobble, adjust, wobble a little less. At some point you've gotta let go of the seat, or you're just two people jogging,” was approved as “way better.”

Our reading of the difference: both lines carry the loop and the stop condition, but the first ends on a penalty and reads as a scolding moral, while the second has a helper, visible progress, and delivers the stop condition as an affectionate surprise. That reading is the author's interpretation of a single taste judgment. It is not a measured result, a comprehension test, or evidence about the show.

Changes:

- `SKILL.md`: a “smile, not a sermon” bullet, and voice-miss handling (re-pitch warmth, don't defend, no catchphrases).
- `references/craft.md`: a contrast note using both lines, and a voice-miss addition to “Treat confusion as feedback.”
- `references/examples.md`: the before/after pair with a craft note.
- `evals/prompts.json`: two new fixtures, `warm-turn-observation` and `voice-miss-follow-up` (26 total). The first 24 records are unchanged.
- `evals/README.md`: rubric rows for the new fixtures, and a voice cap: for low-stakes inputs, an observation whose last beat scolds, warns, or names a loss scores at most 1 on voice. Direct risk statements in serious cases are exempt.

These 26 cases were not run against 0.1.3 itself; see the 0.1.4 run below.

## 0.1.4: style library

`references/styles.md` adds eleven named styles and three failure modes, each tied to scenes. Script entries come from a re-read of the three shooting-script copies already in the research ledger; other entries were located through press recaps and are marked PRESS. Three press citations (S1E2, S1E8, S3E6) were spot-checked against their pages on 2026-10-12. Rights-holder clip pages were rate limited, so no new timestamps were added. No show dialogue is reproduced. Style 1 ("accidentally doing something else") is marked as the project's own pattern because no show scene was found for it.

## 0.1.4 behavioral run

The 26-case suite was run against 0.1.4 with fresh runner agents and graded by separate agents (same model family). **22 of 26 passed, with no hard failures.** Failures: pricing, terse-prompt, spreadsheet-query-depth, voice-miss-follow-up. See the [run report](run-0.1.4/README.md) for method, limits, raw outputs and grades. These are model grades, not human judgment.

## 0.1.5: voice rule clarified, failed cases re-run

The voice rule now allows silly, harmless "or you're just..." endings and rules out endings implying waste, trouble, loss, or blame, and warns against reusing an example's sentence shape. Observations must be literally true of the input and of their own scene, and time periods join the preserve list. All five cases that failed or were voice-capped in 0.1.4 pass on re-run (pricing on its third attempt). See the [0.1.5 re-run report](run-0.1.5/README.md). The other 21 cases were not re-run.

## 0.1.6: full run, reader test, license

Rubric decisions approved: no voice cap when the warning is the input's own main caveat, and the no-quotes rule covers show dialogue only. The full 26-case suite then passed **24 of 26 with no hard failures** ([full run report](run-0.1.5-full/README.md)); the top remaining weakness is copying the shape of the authored examples. A [reader test](reader-test/README.md) for human comprehension is published as a private artifact and waiting for readers. The package is now MIT licensed.

## Structural checks

- Skill frontmatter (name, description) present; no unfinished-scaffold markers: passed with a local standard-library check.
- All package JSON parsed. Both manifests agree on name, description, and version `0.1.6`.
- 26 unique fixture ids; the original 24 fixture records are unchanged (parsed and compared to the previous commit).
- Local Markdown link targets resolve.
- No license, runtime dependency, hook, MCP server, or executable helper added.

Structural checks cannot establish semantic quality or host behavior.

## Historical evidence

The [0.1.2 report](results-0.1.2.md), [0.1.1 report](results-0.1.1.md), and [0.1.0 report](results-0.1.0.md) are archived with their raw outputs and reviews. Their results do not transfer to this revision.

## Remaining checks

Decide the two rubric questions in the [0.1.5 report](run-0.1.5/README.md), and re-run the full suite. Watch whether the new voice rule makes lines warmer without drifting into folksiness, catchphrases, or forced jokes, and whether serious cases still get plain, direct risk statements. Human review of whether associations land, and conversational invocation in each advertised host, remain unverified.
