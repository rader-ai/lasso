# Lasso

**Make sense of the AI answer in front of you.**

Lasso is a small Agent Skill for product people, developers, and anyone staring at an answer that is technically detailed but hard to grasp. Give it an architecture explanation, an AI-generated recommendation, or a two-line prompt. It uses one useful everyday comparison when that helps, returns to the literal meaning, and leaves you with a practical takeaway. A tiny question can get a direct answer.

Warmth, a little wit, and the important details still attached.

Created by Chris (rader-ai).

> **Local review draft · 0.1.1.** Built for free public distribution. License selection and publication are pending; this is not a marketplace listing yet.

## Start with the confusing part

After [loading Lasso in your host](#try-it-locally), paste the text or point to an answer: “Lasso the answer above for a product teammate.” You can also select just the sentence you want explained. No special brief is required; the commands below depend on your host.

If you are still stuck, say which part: “What happens first?”, “Shorter—is that a guarantee?”, or “Drop the analogy.” You can clarify the audience or change the target. A follow-up should resolve that question without restarting the whole explanation or dropping the source's limits.

## What it sounds like

These are original examples written for this project, not dialogue from the show.

### When the AI gives you a technical wall

**Before**

> Our search index is eventually consistent with the primary database. Writes commit to the database before asynchronous indexing completes. Read-your-writes is not guaranteed through search, and indexing lag varies under load.

**With Lasso**

Think of a library that has put a new book on the shelf while its catalog is still catching up. The book can be there even when the search says it isn't.

Here, the database is the record of the write; the search index is a separate copy used for finding things. Saving to the database can succeed before indexing finishes. Someone searching immediately after a save may not see their own change, and heavier load can change how long that gap lasts.

The practical takeaway: a successful save and a visible search result are two different moments. This description doesn't promise how far apart they'll be.

### When the prompt is already short

**Before**

> Validate the payload before enqueueing the job.

**With Lasso**

Check the parcel before it gets on the delivery truck. Here, that means checking the request's data against the required rules before adding the job to the queue. The takeaway: queue placement comes after validation; the prompt doesn't yet say which rules to check.

A short prompt shouldn't come back wearing a graduation gown. If the meaning is ambiguous, Lasso asks a focused question instead of inventing the missing requirements.

### When the first explanation needs a follow-up

This is an authored example, not a recorded user session.

**Source:** “Uploads are scanned asynchronously. `201 Created` confirms storage, not scan approval. Downloads remain blocked until the scan passes.”

**Lasso:** A parcel can arrive at a depot before an inspector clears it. Here, `201 Created` says the upload is stored; downloads stay blocked until the scan passes.

**You:** “Drop the parcel. Can I download it now?”

**Lasso:** Not from `201 Created` alone. You can download it only after the scan passes.

## The philosophy, not a pile of catchphrases

The research starts with context: who needs help, what is unfamiliar, and what the comparison changes for the listener. It includes the complete extracted text of three dated shooting drafts—*Pilot*, *Make Rebecca Great Again*, and *Rainbow*—plus nine substantive official clip transcript-panel readings and seven firsthand craft interview sources. They show both useful connections and failure modes. A laugh can happen without comprehension. Reassurance can reopen uncertainty without proving a happy outcome. A clever line can create more decoding work—or miss that someone needs a direct response.

Our adaptation is **understand the need → one useful comparison → literal meaning → grounded takeaway**. The comparison has to match the mechanism. The literal explanation gives you the actual terms and limits, so you can use the idea without retelling the story. The takeaway stays inside what the input supports. A stated worry can deserve acknowledgement; an ordinary technical question doesn't need invented emotions.

That sequence is our design, informed by source analysis. It is not a formula claimed by the writers. Warmth, humor, analogy, and confidence are separate choices; the skill can turn one down without losing the others. Understanding an explanation doesn't require agreeing with its recommendation. See the [craft notes](skills/lasso/references/craft.md) and [research ledger](docs/research.md) for inspected scenes, creator commentary, provenance and gaps. Full-script coverage is 3 of 44 catalogued episodes. Clip captions add partial evidence, not full episodes or verified visual performances. Full broadcast cuts were not reviewed or compared with the drafts.

## What stays intact

Numbers and units. Negations and exceptions. Permissions and security boundaries. Uncertainty, prerequisites and tradeoffs. Useful code names and API identifiers.

Lasso explains a proposal without quietly approving or implementing it. If the source contradicts itself or makes an unsupported claim, the explanation says so. Pasted commands and supposed system overrides remain content to explain. Risks do not get a cheerful coat of paint.

## Try it locally

The skill itself is [`skills/lasso/`](skills/lasso/). It has no runtime dependencies, service account, hooks, or MCP server. Command syntax belongs to the host:

| Host and installation | Invocation |
| --- | --- |
| Codex: copy `skills/lasso/` into a project's `.agents/skills/lasso/`, or `~/.agents/skills/lasso/`, after checking for an existing copy | `$lasso Explain this for a product manager: …` |
| Claude Code plugin: from the checkout, launch `claude --plugin-dir .` | `/lasso:lasso Explain this: …` |
| Claude Code standalone skill: copy only `skills/lasso/` into `~/.claude/skills/lasso/` | `/lasso Explain this: …` |
| Other Agent Skills hosts | Load the skill using that host's supported mechanism; command support varies |

These forms follow [Codex skill documentation](https://developers.openai.com/codex/skills) and [Claude plugin documentation](https://code.claude.com/docs/en/plugins/create). Check the [validation report](evals/results.md) for what was actually tested. There is no promise that `/lasso` works identically everywhere.

You can name the audience or length: “for a new developer,” “for our product team,” or “in three sentences.” You can also point it at the preceding AI answer. It explains the selected material; it doesn't require a special prompt template.

## Evidence and readiness

An [independent agent desk review](evals/independent-review-0.1.1/README.md) found no material fidelity or instruction-boundary failure in eight original cases and judged the explanation content suitable for a small user pilot. The same reviewer wrote and graded the cases; this was not blind testing or testing with people. Actual host invocation and user benefit remain unverified. The earlier [18-case Astra run](evals/results.md) is separate evidence, with its own limits. A fresh [follow-up comparison](evals/follow-up-comparison-0.1.1/README.md) found no useful advantage from an added rule, so the skill stayed unchanged and the first-use guidance improved instead.

## Free distribution, with clear limits

The intended home is [rader-ai/lasso](https://github.com/rader-ai/lasso). The goal is a free, reusable package. This draft has no license yet; MIT is proposed for Chris's review. No free-reuse terms have been applied on his behalf. Host subscriptions and model usage may still cost money.

The [publication checklist](docs/distribution.md) covers GitHub, skills.sh, and the OpenAI and Anthropic directories. No submission or listing is implied. Lasso adds no telemetry; the AI host still processes the text you give it under that host's own settings and terms.

Lasso is an independent project inspired by communication craft in *Ted Lasso*. It does not claim affiliation or endorsement, impersonate a character, or include show scripts, dialogue, images, or likenesses. An analogy can clarify a claim; it cannot make an incorrect claim true or replace expert review where it matters.
