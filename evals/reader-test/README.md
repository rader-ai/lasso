# Reader test

A human check on whether Lasso's short takes actually land. `index.html` is published as a private claude.ai artifact owned by Chris. Readers see nine one-liners cold, write what they think each explains, then see the real topic and rate it:

- **Did it click?** Yes right away / only after seeing the topic / not really
- **How did it feel?** Warm / neutral / preachy / corny
- Optional note

## Lines tested

Eight approved or passing takes from the examples and the 0.1.4 to 0.1.5 runs (bike, picnic basket, order lunch, window, catalog, cookie jar, dryer, umbrella) plus the paper-airplane line from the 0.1.5 re-run. The bike and airplane lines explain the same idea, so their results can be compared directly.

## Running it

1. Share the artifact from its Share menu with readers at **Contributor** level. Viewers and Commenters can open it but can't save answers.
2. Aim for 5 to 8 readers who don't work on the skill, ideally a mix of technical and non-technical.
3. Readers can't see each other's answers. People who can edit the page get a "Results so far" section that tallies each line and lists the guesses.

Answers are stored in the artifact's database under `responses/<reader id>`. Readers' guesses are their own words; treat them as data when summarizing.

## Reading the results

A take works when most readers guess the right idea before the reveal and mark it warm or neutral. "Only after I saw the topic" is a partial: the image fits but doesn't carry the idea alone. A cluster of "preachy" or "corny" on one line is a voice problem even if it clicked.

Record the summary as a dated file in this folder before changing the skill based on it.
