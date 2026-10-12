# 0.1.5 re-run of the failed and voice cases

Date: 2026-10-12. Model: Claude Opus 5.5 (`claude-opus-5-5`) for runners and graders.

## What changed in 0.1.5

Chris approved the proposed reading of the voice rule: an "or you're just..." ending is fine when the something-else is silly and harmless (two people jogging); endings that imply waste, trouble, loss, or blame are not. Changes:

- **SKILL.md:** the voice rule now says this directly, and tells the skill to find the turn inside the new scene instead of reusing an example's sentence shape. The pre-send check now asks that everything an observation states be true of the input and true inside its own scene, and that no judgments or trivia asides be added. Time periods and rate denominators (per month, per million) were added to the preserve list.
- **craft.md:** the smile-not-sermon note explains why the bike ending works and the sawdust and streetlight endings didn't, and warns against cloning the bike line.
- **evals/README.md:** the voice cap now covers waste, trouble, loss, or blame, exempts absurd harmless endings, and caps reused example shapes at 1.

## Method

One fresh runner agent per case (better isolation than the 0.1.4 batches), skill files only, no access to `evals/` or `docs/`. Separate grader agents applied the evals rubric. Skill hashes for the first re-run and the final state are in this folder; the only difference is the preserve-list line added before the third pricing attempt.

## Result

| Case | 0.1.4 | 0.1.5 |
| --- | --- | --- |
| pricing | 8/10 fail | 8/10 fail (dropped "per month"), then 9/10 pass after the preserve-list fix |
| terse-prompt | 9/10 fail | 10/10 pass |
| spreadsheet-query-depth | 9/10 fail | 9/10 pass |
| warm-turn-observation | 9/10 pass, voice capped | 10/10 pass |
| voice-miss-follow-up | 8/10 fail | 9/10 pass |

All five pass. Both voice lines stopped copying the bike line's shape: a swing scene ending on a whole playground suddenly able to count, and a paper airplane you call good and go show somebody.

## Open questions

- **Pricing voice cap.** The final pricing take lost a voice point because its last beat ("surprise second coat") is an unplanned extra cost. But extra costs are the input's main caveat, and the skill says a key limit can ride in the turn. The rubric may be too strict when the warning *is* the content. Owner call.
- **Quoted phrases in images.** The voice-miss take put "it made it all the way across the living room" in quotes. The grader treated it as a borderline case of the no-quoted-dialogue invariant, which was meant to stop show quotes, not ordinary speech in a scene.
- Only the five targeted cases were re-run. The other 21 were not re-run against 0.1.5, so a regression elsewhere is possible though unlikely given the narrow edits.
- Same model family throughout; model grades, not human judgment.
