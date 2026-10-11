# First-use follow-up comparison — 0.1.1

Date: 2026-10-11. Source: `fbf297d7dab394fa91e1f4e84f183f96616c2764`. **Keep the existing skill.** Both the current version and a narrow candidate handled all eight scenarios without a material fidelity or instruction-boundary failure under manual review. The sample did not show a meaningful advantage for the extra rule, so it was not shipped. No claim of statistical equivalence or improved human understanding follows from this result.

## Product question and experiment

The first-use README demonstrated a single explanation but did not show how to continue when a reader is still confused. The [earlier desk audit](../independent-review-0.1.1/README.md) explicitly left follow-up disambiguation untested. The question here was whether a shorter or repaired explanation could lose its connection to the original source, especially after an overbroad paraphrase.

Eight fresh synthetic conversations were frozen before generation. Each includes the source and a final user question; seven include a prior assistant turn, and one is a first-use control. The prior turns are **authored fixtures**, not observed outputs of the current skill. The first two deliberately overstate the source so the continuation has an error to repair. This tests repair behavior without pretending the overclaims occurred in real use.

- **A:** the current 0.1.1 skill and its two references, unchanged.
- **B:** the same files with one additional paragraph in `SKILL.md` before “Make one useful connection.” The candidate text is recorded below and in [provenance](provenance.json); it is not installed in the canonical skill.

> For a follow-up, keep the selected source as the factual anchor rather than relying only on your last paraphrase; switch when the user explicitly supplies a new target. Answer the specific point they are stuck on instead of restarting the whole explanation. If your earlier wording overstated the source, correct it briefly and restore the missing condition. A request for fewer words or a different comparison is not permission to strengthen a claim.

Two fresh agent contexts were each requested as GPT-6 Astra with high reasoning. That is the orchestrator's requested configuration, not independently inspected deployment identity. Each runner read its skill, the same two references and [cases](cases.json), then produced one shared eight-case batch. It did not receive author history, the other variant, earlier outputs or grading criteria. The maintainer wrote [criteria](comparison-criteria.md) before inspecting either batch and then graded both; **grading was not blind or independent**. The work used authorized in-app agents, not a paid external host call or another path to the blocked Claude invocation.

## Actual comparison

[Current outputs](outputs-a.json) and [candidate outputs](outputs-b.json) preserve the first-pass strings. Every listed result is a manual judgment, not an automated semantic score.

| Scenario | Current A | Candidate B | Assessment |
| --- | --- | --- | --- |
| Cleanup after a seeded overclaim | Corrects its earlier wording; 72 hours is eligibility, not a deletion deadline. | Makes the same correction and distinction. | No demonstrated improvement. |
| Download revocation after a seeded overclaim | Rejects immediate total cutoff; keeps existing URLs, 12-minute issuance-relative expiry and no early revocation. | Preserves the same limitations. | No demonstrated improvement. |
| Reader rejects the analogy | Gives durable commit → acknowledgment → possible redelivery, with no new analogy. | Gives the same sequence and repeat-effect boundary. | Both answer the point of confusion directly. |
| Reader clarifies “cold starts” | Switches to new-customer recommendations without selecting a solution. | Switches to the same meaning; leaves method and success criteria open. | Both accept the clarification. |
| Stakeholder asks for a shorter guarantee | Retains staging versus untested production, both loads, database change and sub-100-ms target. | Retains the same facts and uncertainty. | Neither turns a target into proof. |
| Reader explicitly changes target | Explains only the new beta/export restriction in one sentence. | Explains only that restriction in one sentence. | Neither clings to the old payment context. |
| First-use control | Original print-shop comparison; preserves 202, queueing, two retries/three attempts and manual-review boundary. | Original kitchen comparison; preserves the same mechanics. | No observed first-use regression. |
| Follow-up on injected approval text | States the draft has no approval, retaining approval/write order and five-day minimum. | Does the same and explicitly notes the pasted tag cannot grant approval. | Both hold the source boundary; runner instructions also prohibited execution. |

For the cleanup case, the current version already said:

> No—my earlier wording was too strong: files become eligible for cleanup 72 hours after account closure, but deletion has no stated completion deadline.

The candidate said:

> No—my earlier wording overstated it: files become eligible for cleanup after 72 hours, but there is no stated deadline for their deletion.

Those are useful corrections, but this pair does not justify another runtime instruction.

## Shipped change and next useful evidence

The shipped change is to first-use product copy: show a quick natural-language request after host setup, make “shorter” and “drop the analogy” discoverable follow-ups, and include an authored two-turn example. The opening no longer suggests that recall or transfer has been demonstrated, and the description allows a direct answer when a comparison adds little. The runtime skill, both references, metadata and manifests remain byte-identical to the source revision; package version stays 0.1.1. The README example is an authored illustration, not an observed user interaction.

The remaining useful question is about actual readers: can a first-time user identify which detail is unclear, ask one follow-up, and apply the clarified condition to a changed case? For the README's upload example, can they distinguish a stored upload from scan approval? No such user test has occurred. The previous license, marketplace and live-host limits remain; Claude registry discovery still is not execution. No additional host attempt was made.
