# Distribution plan

Checked against first-party documentation on 2026-10-11. Chris authorized publishing the reviewed source to the existing GitHub repository after local validation. No marketplace registration, submission, global install, or directory publication has occurred. The goal remains a free reusable skill; licensing and marketplace release are separate decisions.

## One skill, small wrappers

`skills/lasso/` is the canonical portable Agent Skill. Root `plugin.json` follows Agent Plugins 1.0.0; `.claude-plugin/plugin.json` identifies the same package to Claude. Both discover `skills/` at the package root. There are no hooks, MCP servers, installation scripts, accounts, bundled dependencies, or credentials. See [OpenAI's package format](https://developers.openai.com/plugins/build/plugins), the [Agent Plugins schema](https://agent-plugins.org/schemas/1.0.0/plugin.schema.json), and [Claude's manifest reference](https://code.claude.com/docs/en/plugins-reference).

## Local use and honest invocation

For Codex, copy only `skills/lasso/` to a project's `.agents/skills/lasso/` or the user's `~/.agents/skills/lasso/`, first checking that the destination does not already exist. Invoke `$lasso` with the text or explicitly ask to use lasso. Codex discovery paths and the explicit `$skill` form are documented in [Build skills](https://developers.openai.com/codex/skills). This task does not change personal skill configuration.

For a session-only Claude Code test from a local checkout, run `claude --plugin-dir /absolute/path/to/lasso`, then `/lasso:lasso` with the text. A standalone copy of the skill in `~/.claude/skills/lasso/` uses `/lasso`; don't install both forms just to obtain an alias. The namespaced form belongs to the plugin. See [Create a Claude Code plugin](https://code.claude.com/docs/en/plugins/create). Documentation establishes expected syntax; a manifest validation is not a conversational smoke test. A [session-only check](../evals/host-invocation-0.1.1.md) confirmed one skill was discovered by Claude Code 2.1.292, but generation was blocked after the usage preflight failed under the no-spend constraint. Claude plugin, standalone Claude, and Codex invocation remain explicitly untested.

Other Agent Skills hosts may load the canonical folder, but commands and supported metadata vary. Do not promise a universal `/lasso` command.

## Public destinations to choose

| Destination | What publication involves | Current status |
| --- | --- | --- |
| GitHub `rader-ai/lasso` | Push reviewed original source to the exact existing remote, preserving author identity and remote changes. A license is still needed for explicit free-reuse terms. | Source push authorized; the delivery receipt records the verified remote commit. |
| skills.sh | Once the repo is public, users can install through the skills CLI. Its FAQ says leaderboard discovery follows installations reported through aggregate telemetry. This is not a curated listing submission or guaranteed prominence. | No CLI run, install, telemetry choice, or listing claim. |
| OpenAI plugin directory | Upload a ZIP under a verified developer identity, address validation/review requirements, complete attestations, then publish an approved version. Skills-only packages do not need MCP review cases or an MCP demo recording. | Portable manifest prepared; account, listing and review actions pending. |
| Anthropic plugin directory | Validate the selected plugin folder; connect an authorized GitHub account for submission; complete review. Public release requires a public repository. README and license are required by its checklist. | Repo is public and MIT licensed. Submission needs Chris's GitHub authorization and review steps. |

Sources: [skills.sh FAQ](https://www.skills.sh/docs/faq), [OpenAI submission](https://developers.openai.com/plugins/deploy/submission), [Anthropic submission](https://claude.com/docs/plugins/submit), [Anthropic checklist](https://claude.com/docs/plugins/pre-submission-checklist). Recheck these immediately before release; schemas and submission workflows change.

## Decisions before release

- **License:** Decided 2026-10-12: Chris approved MIT. `LICENSE` (copyright Chris Rader, rader-ai) and `"license": "MIT"` in both manifests were added in 0.1.6. [MIT license text](https://opensource.org/license/mit).
- **Destination:** Choose which directory, if any, in addition to the public GitHub repository. A repo catalog alone does not create an official directory listing.
- **Public identity and data:** Confirm publisher display name/contact, listing copy, and any support/privacy/terms URLs the chosen destination requires. The package has no telemetry or service, but host providers process supplied prompts under their own settings. Do not invent a privacy policy or claim local-only processing.
- **Branding and evidence:** Approve the project name and independent, unaffiliated positioning. Confirm the research coverage statement and all original examples. Include no scripts, transcripts, stills, logos, likenesses, or supposed quotations from the show.
- **Release quality:** Complete per-host conversational smoke tests; record versions, outputs and any failures. The license is resolved; per-host smoke tests remain.
- **Remaining authorization:** Local commits and the reviewed GitHub source push are authorized. Marketplace upload/submission, directory publication and required terms still need separate approval. Do not create accounts, accept terms, enable webhooks, or spend money as a packaging step.

“Free skill” means no separate fee planned for this package. Users may still need a paid host account or incur model usage charges. Nothing in this draft promises directory acceptance, endorsement, or comprehension for every reader.

## Steps left for Chris (2026-10-12)

These need your own accounts or acceptance of terms, so they were prepared but not done for you:

1. **Anthropic plugin directory:** open the [submission page](https://claude.com/docs/plugins/submit), connect your GitHub account, point it at `rader-ai/lasso`, and complete review. The repo now meets the public-repo, README and license requirements in the [checklist](https://claude.com/docs/plugins/pre-submission-checklist); recheck it on the day.
2. **OpenAI plugin directory:** zip the repo root, upload under a verified developer identity, complete the attestations ([submission guide](https://developers.openai.com/plugins/deploy/submission)).
3. **skills.sh:** nothing to submit. Because the repo is public, people can install it with the skills CLI; listing follows installs.
4. **Before any of these:** run one conversational smoke test in each host you advertise and record it in `evals/`.
