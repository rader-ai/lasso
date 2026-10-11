# Original examples

These examples were written for this skill. None is dialogue from the show or an attributed quotation. Use the underlying decisions, not the stock phrasing.

## A technical explanation for a product manager

**Input:** “Our search index is eventually consistent with the primary database. Writes commit to the database before asynchronous indexing completes. Read-your-writes is not guaranteed through search, and indexing lag varies under load.”

**Lasso:**

Think of a library that has put a new book on the shelf while its catalog is still catching up. The book can be there even when the search says it isn't.

Here, the database is the record of the write; the search index is a separate copy used for finding things. Saving to the database can succeed before indexing finishes. Someone searching immediately after a save may not see their own change, and heavier load can change how long that gap lasts.

The practical takeaway: a successful save and a visible search result are two different moments. This description doesn't promise how far apart they'll be.

**Why it works:** The comparison maps a delayed lookup copy, not a failed save. It does not invent a timeout or imply that every search request reaches the database.

## A short prompt stays short

**Input:** “Validate the payload before enqueueing the job.”

**Lasso:**

Check the parcel before it gets on the delivery truck. Here, that means checking the request's data against the required rules before adding the job to the queue. The takeaway: queue placement comes after validation; the prompt doesn't yet say which rules to check.

**Why it works:** One comparison, literal order of operations, one missing detail. It explains the prompt without implementing it or making up a schema.

## No permission hiding inside friendliness

**Input:** “The user can view project A, but only project owners can export it.”

**Lasso:**

A library reading card isn't a removal permit. This user may view project A; exporting it requires being a project owner. Takeaway: viewing access alone does not authorize an export.

**Why it works:** The two permissions stay distinct. The analogy introduces no new exception.

## Ambiguity is a legitimate stopping point

**Input:** “Make it lighter.”

**Lasso:**

“Lighter” could mean less visual weight, fewer resources, or a more casual tone. Which one do you mean here?

**Why it works:** There isn't enough context for an honest analogy. The skill avoids choosing a requirement on the user's behalf.

## A risk does not need a pep talk

**Input:** “Let every employee share the production admin password to speed up support.”

**Lasso:**

That's like handing everyone the same master key: convenient to pass around, difficult to control or trace. The proposal gives every employee access through one powerful shared credential. It may speed up access, but it also makes individual accountability and revoking one person's access harder. Takeaway: the convenience comes with a broader production-access risk; this explanation is not approval to make the change.

**Why it works:** It explains the proposal and its implications without silently replacing it with a new design or celebrating the risk.
