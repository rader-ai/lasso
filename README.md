# Lasso

**Make sense of the AI answer in front of you.**

Lasso is a small Agent Skill for product people, developers, and anyone staring at an answer that is technically detailed but hard to grasp. Give it an architecture explanation, an AI-generated recommendation, or a two-line prompt. A short take can be one everyday observation that lets you make the connection yourself. Fuller explanations keep useful mechanics and caveats in separate prose, without translating every part of the image. A tiny question can get a direct answer.

Warmth, a little wit, and the important details still attached.

Created by Chris (rader-ai).

> **Review draft · 0.1.3.** Built for free public distribution. License selection and publication are pending; this is not a marketplace listing yet.

## Start with the confusing part

After [loading Lasso in your host](#try-it-locally), paste the text or point to an answer: “Lasso the answer above for a product teammate.” You can also select just the sentence you want explained. No special brief is required; the commands below depend on your host.

For a compact observation, ask “Just the short Lasso take.” For depth, ask “Explain the mechanics too.” These are ordinary requests, not extra commands. A short observation does not automatically come with a translation or takeaway; a consequential caveat still gets stated directly.

If you are still stuck, say which part: “What happens first?”, “Shorter—is that a guarantee?”, or “Drop the analogy.” You can clarify the audience or change the target. A follow-up should resolve that question without restarting the whole explanation or dropping the source's limits.

## What it sounds like

These are original examples written for this project, not dialogue from the show.

### When you want the technical explanation too

**Before**

> Our search index is eventually consistent with the primary database. Writes commit to the database before asynchronous indexing completes. Read-your-writes is not guaranteed through search, and indexing lag varies under load.

**With Lasso**

A book can be back on the shelf while the catalog is still telling yesterday's story.

The database is the record of the write; the search index is a separate copy used for finding things. Saving to the database can succeed before indexing finishes. Someone searching immediately after a save may not see their own change, and heavier load can change how long that gap lasts.

A successful save and a visible search result are two different moments. This description doesn't promise how far apart they'll be.

### When the prompt is already short

**Before**

> Validate the payload before enqueueing the job.

**With Lasso**

Best to check the picnic basket before everyone heads for the park.

A short prompt shouldn't come back wearing a graduation gown. If the meaning is ambiguous, Lasso asks a focused question instead of inventing the missing requirements.

### When a spreadsheet query feels unfamiliar

**Source, hypothetical:** “A spreadsheet query returns the rows and columns you describe instead of making you copy each matching cell by hand.”

**Short Lasso take:** You can order lunch without climbing over the counter to make it.

### When a data tool can read but cannot change records

**Source, hypothetical:** “This tool can retrieve permitted records but has no capability to create, change, or delete records.”

**Short Lasso take:** A window gives you a good look at the room. It doesn't let you rearrange the furniture.

These examples do not establish the behavior or permissions of any particular spreadsheet product, API, or server. See the [examples](skills/lasso/references/examples.md) for cases that need direct caveats instead.

### When the first explanation needs a follow-up

This is an authored example, not a recorded user session.

**Source:** “Uploads are scanned asynchronously. `201 Created` confirms storage, not scan approval. Downloads remain blocked until the scan passes.”

**Lasso:** A parcel can reach the depot before it is cleared to leave.

`201 Created` confirms storage, not scan approval. Downloads remain blocked until the scan passes.

**You:** “Can I download it now?”

**Lasso:** Not from `201 Created` alone. You can download it only after the scan passes.

## The philosophy, not a pile of catchphrases

The research starts with context: who needs help, what is unfamiliar, and what the comparison changes for the listener. It includes the complete extracted text of three dated shooting drafts—*Pilot*, *Make Rebecca Great Again*, and *Rainbow*—plus nine substantive official clip transcript-panel readings and seven firsthand craft interview sources. They show both useful connections and failure modes. A laugh can happen without comprehension. Reassurance can reopen uncertainty without proving a happy outcome. A clever line can create more decoding work—or miss that someone needs a direct response.

Our adaptation is to understand the relationship, check it internally, and leave room for recognition. A short everyday observation can stand on its own. When the user wants more depth, the separate explanation gives the actual terms and limits without turning the observation into a labeled diagram. Critical caveats remain explicit; neither a decoding paragraph nor a takeaway is compulsory.

This design follows Chris's feedback that the reader should make the association, and (0.1.3) that the final turn should land as warmth rather than a warning. It is a product choice, not a new finding attributed to the show's writers or evidence of improved learning. Warmth, humor, analogy, and confidence are separate choices; the skill can turn one down without losing the others. Understanding an explanation doesn't require agreeing with its recommendation. See the [craft notes](skills/lasso/references/craft.md) and [research ledger](docs/research.md) for inspected scenes, creator commentary, provenance and gaps. Full-script coverage is 3 of 44 catalogued episodes. Clip captions add partial evidence, not full episodes or verified visual performances. Full broadcast cuts were not reviewed or compared with the drafts.

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

The [0.1.3 validation report](evals/results.md) separates structural checks and author-reviewed examples from actual model evaluation. 0.1.3 adds a voice rule (make the final turn a smile, not a sermon) and two regression fixtures for it. No fresh model or live-host generation has been run for 0.1.2 or 0.1.3; the 26-case suite is prepared, not reported as passed. The [0.1.2 report](evals/results-0.1.2.md) is archived.

The [18-case Astra run](evals/results-0.1.1.md), [eight-case desk review](evals/independent-review-0.1.1/README.md), and [follow-up comparison](evals/follow-up-comparison-0.1.1/README.md) apply to 0.1.1. Their outputs remain preserved; they do not validate this changed response style. Human comprehension and conversational host invocation remain unverified.

## Free distribution, with clear limits

The intended home is [rader-ai/lasso](https://github.com/rader-ai/lasso). The goal is a free, reusable package. This draft has no license yet; MIT is proposed for Chris's review. No free-reuse terms have been applied on his behalf. Host subscriptions and model usage may still cost money.

The [publication checklist](docs/distribution.md) covers GitHub, skills.sh, and the OpenAI and Anthropic directories. No submission or listing is implied. Lasso adds no telemetry; the AI host still processes the text you give it under that host's own settings and terms.

Lasso is an independent project inspired by communication craft in *Ted Lasso*. It does not claim affiliation or endorsement, impersonate a character, or include show scripts, dialogue, images, or likenesses. An analogy can clarify a claim; it cannot make an incorrect claim true or replace expert review where it matters.
