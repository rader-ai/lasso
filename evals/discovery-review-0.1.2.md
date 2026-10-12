# Authored contrast review — 0.1.2

Date: 2026-10-12. Source baseline: `8cb1f58af02225ec923ea8a51c61c20928caf41a` (0.1.1). This review examines examples written during the revision, not outputs obtained by invoking the revised skill. The author also reviewed them; this is not independent or blind assessment. No numeric model pass count is assigned.

Chris's feedback established the design target: a freestanding everyday observation lets the reader make the association. More folksy decoration or a joke attached to an exhaustive mapping does not meet that target. Two reported screenshots motivated spreadsheet-query and read-only-tool scenarios. Fixtures contain new hypothetical descriptions, no screenshots, private account data, or copied vendor/API claims.

## Before and after

| Situation | Before | Authored revision | Manual assessment |
| --- | --- | --- | --- |
| Validate before enqueueing | 0.1.1 shipped example: “Check the parcel before it gets on the delivery truck.” Then two sentences translate the objects and repeat the ordering. | “Best to check the picnic basket before everyone heads for the park.” | Ordinary preparation before departure invites the ordering relationship; no queue/payload nouns or translation. No validation rules invented. The short prompt supplies the target. |
| Spreadsheet query | Representative old pattern, authored here: “Think of a query as a lunch order. The order is the query; the kitchen is the tool. This means you describe the result instead of copying cells.” | “You can order lunch without climbing over the counter to make it.” | Specifying what is wanted versus performing the preparation is recoverable. The line does not promise every dish or eliminate the need to place a valid order. It is intentionally not a catalog of query operations. |
| Read-only tool | Representative old pattern, authored here: “Think of the tool as a window. The room is the data, and the furniture is the records. This means you can retrieve but not edit them.” | “A window gives you a good look at the room. It doesn't let you rearrange the furniture.” | Access to a view is distinct from ability to change the contents. No technical counterparts or decoding. It does not assert visibility into every room or freedom from privacy concerns. |
| Requested technical depth | 0.1.1 starts with “Think of a library” and automatically returns to a labeled takeaway. | The revised [long example](../skills/lasso/references/examples.md) starts with the shelf/catalog observation, then explains database/index timing separately. | The literal mechanics and absence of a delay bound remain available. No requirement to equate shelves and books with components. |
| False read-only claim | A pleasant line about looking without touching would miss the contradiction. | “Hiding the edit buttons doesn't make this tool read-only: its credential can still update records through the server.” | Direct factual correction is necessary; withholding it for discovery would be a fidelity failure. No replacement design is imposed. |
| Short but constrained | A line about keeping leftovers would omit the actual rule. | The [cache example](../skills/lasso/references/examples.md) retains successful GET only, 60 seconds, and never caching personal data. | Direct explanation preserves the method, condition, number and exception; brevity does not win over these constraints. |

The first and fourth baselines are descriptions of shipped examples, not measured model outputs. The other old-style comparisons are authored contrast controls, not quotations from the reported screenshots.

## Negative controls for the reviewer

- **Generic wisdom:** “Every journey starts with one step.” It stands alone but has no specific relationship to querying a table or read-only access. Fail relevance/discovery; pleasant phrasing alone is insufficient.
- **Good image, immediate decoding:** Append “The counter is the spreadsheet, and lunch is the query result” to the lunch line. Fail discovery when no user request or factual need requires that mapping.
- **Technical nouns inside the image:** “Your query orders a database sandwich.” Fail the freestanding target; swapping in a metaphorical noun is decoration.
- **False reassurance:** “Nothing can go wrong when you are just looking.” Fail fidelity/safety for a read-only tool: retrieval may expose sensitive information, and the source does not guarantee safety.
- **Hidden boundary:** Answer the false-read-only fixture solely with the window line. Fail fidelity: the credential can write, so the premise of that observation does not fit.

## What remains untested

This contrast review checks intended alignment and makes likely failure modes reviewable. The author knows each target and can infer a connection that a fresh reader may miss. There is no evidence yet that the revised instructions consistently produce these responses, that a host loads them correctly, or that readers understand them. Run the separate regression corpus in an authorized execution environment and assess each actual output before claiming those outcomes. Preserve failed outputs and literal/no-analogy controls; do not select only attractive quips.
