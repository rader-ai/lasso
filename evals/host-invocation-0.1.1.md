# Host invocation check — 0.1.1

Checked on 2026-10-11 against source commit `2cf07ed67a766395dd5d5451e3879c18ecf5f913`. **Claude plugin discovery passed; conversational invocation remains untested. Codex and standalone Claude invocation remain untested.** No invocation defect was established, and no skill or manifest change was needed.

## Official guidance and installed tooling

- [Claude's plugin creation guide](https://code.claude.com/docs/en/plugins/create) documents session-only `--plugin-dir` loading and the `/plugin-name:skill-name` form. For this package that is `/lasso:lasso`; a standalone `lasso/SKILL.md` uses `/lasso`.
- The installed CLI reported `2.1.292 (Claude Code)`. Its help and the [CLI reference](https://code.claude.com/docs/en/cli-reference) confirmed the session-only plugin flag, restricted mode, settings-source selection, strict MCP selection, and tool restriction controls used here.
- [OpenAI's skill documentation](https://learn.chatgpt.com/docs/build-skills) confirms `.agents/skills` discovery and explicit `$skill` invocation. No `codex` executable was found on PATH or at the four standard executable/app paths checked. This does not prove that no other Codex executable exists on the computer; none was available for this isolated CLI test.

## Claude session and observed output

An archive of the exact committed source was extracted into a newly created temporary directory beside an empty test workspace. Claude was launched from that workspace with `--plugin-dir` pointing to the archive, without a global or project plugin install. User/project/local settings sources, hooks, MCP servers, Chrome integration, auto memory, and model tools were disabled for the check. Transcript persistence and auto-updating were disabled. A macOS filesystem sandbox denied writes outside the test directory and system temporary storage, including persistent personal configuration. The host logged denied configuration writes and continued without persisting them. No credentials were copied, printed, granted, or changed.

A read-only authentication check reported an existing signed-in subscription. The interactive session banner showed Claude Code v2.1.292 and Opus 5.5; **the banner is not evidence of a completed model request**. The only submitted in-session command was the built-in `/usage`, used to check whether a test could stay within existing subscription usage under the task's no-spend constraint.

Relevant host debug output, with temporary paths omitted:

```text
2026-10-11T04:17:38.446Z Loaded inline plugin from path: lasso
2026-10-11T04:17:38.447Z Checking plugin lasso: skillsPath=exists, skillsPaths=0 paths
2026-10-11T04:17:38.450Z Loaded 1 skills from plugin lasso default directory
```

The `/usage` panel reported:

```text
Total cost: $0.0000
Total duration (API): 0s
Usage: 0 input, 0 output, 0 cache read, 0 cache write
Error: Failed to load usage data
```

One read-only retry did not resolve the usage-data failure. The available evidence does not establish its underlying cause or whether it depended on the isolation controls. No quota or usage-credit eligibility was inferred from a successful sign-in alone.

## Blocked test and remaining checks

The benign original fixture prepared for the test was:

```text
/lasso:lasso Explain this for a product manager in three sentences: A retry uses the same idempotency key. The server stores the result for 24 hours and returns it for matching retries. A retry after 24 hours may create another operation.
```

**This fixture was not submitted; no explanation output was generated.** After the failed quota preflight, automatic approval review also rejected a proposed `/lasso` text entry because it could initiate a potentially billable model request. The action did not execute. The session was closed without bypassing that rejection.

Discovery proves that Claude loaded one skill from the package into its registry. It does not prove that `/lasso:lasso` expanded the skill into a model context or produced a faithful explanation. The standalone `/lasso` form was not installed or tested. Codex `$lasso` was not run because no usable CLI was found.

To finish verification, run the documented invocation after a successful no-spend usage check or explicit authority for potentially billable host usage; record the actual expansion, host/model, and output. Codex additionally needs an available authorized host with an isolated `.agents/skills/lasso/` workspace. The architecture, short-clear-prompt, and malicious-paste host checks in the [evaluation instructions](README.md) remain outstanding. The separate [18-case Astra results](results.md) are behavioral evidence, not substitutes for these host tests.

No dependency, host installation, account setup, persistent configuration change, license change, marketplace submission, or paid generation was performed in this check.
