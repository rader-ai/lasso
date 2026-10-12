# Validation report: 0.1.3 and 0.1.4

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

**These 26 cases have not been run against 0.1.3.** No fresh model or live-host generation was performed, and no paid API call was made.

## 0.1.4: style library

`references/styles.md` adds eleven named styles and three failure modes, each tied to scenes. Script entries come from a re-read of the three shooting-script copies already in the research ledger; other entries were located through press recaps and are marked PRESS. Three press citations (S1E2, S1E8, S3E6) were spot-checked against their pages on 2026-10-12. Rights-holder clip pages were rate limited, so no new timestamps were added. No show dialogue is reproduced. Style 1 ("accidentally doing something else") is marked as the project's own pattern because no show scene was found for it.

This is reference material. It has not been tested for whether it changes the skill's outputs.

## Structural checks

- Skill frontmatter (name, description) present; no unfinished-scaffold markers: passed with a local standard-library check.
- All package JSON parsed. Both manifests agree on name, description, and version `0.1.4`.
- 26 unique fixture ids; the original 24 fixture records are unchanged (parsed and compared to the previous commit).
- Local Markdown link targets resolve.
- No license, runtime dependency, hook, MCP server, or executable helper added.

Structural checks cannot establish semantic quality or host behavior.

## Historical evidence

The [0.1.2 report](results-0.1.2.md), [0.1.1 report](results-0.1.1.md), and [0.1.0 report](results-0.1.0.md) are archived with their raw outputs and reviews. Their results do not transfer to this revision.

## Remaining checks

Run the 26-case suite, with special attention to whether the new voice rule makes lines warmer without drifting into folksiness, catchphrases, or forced jokes, and whether serious cases still get plain, direct risk statements. Human review of whether associations land, and conversational invocation in each advertised host, remain unverified.
