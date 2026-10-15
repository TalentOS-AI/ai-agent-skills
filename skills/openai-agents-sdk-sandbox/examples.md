# Examples: openai-agents-sdk-sandbox

> 注：以下为示例，未经实测。 Examples only — not yet run end-to-end.

Needs Python, `pip install openai-agents`, and an `OPENAI_API_KEY` in your own environment. Sandbox is beta, so pin the SDK version and check the [docs](https://openai.github.io/openai-agents-python/) before running.

## Example 1: Summarize a README inside a sandbox workspace

**Input prompt**
> Using the openai-agents-sdk-sandbox skill, write a minimal script that creates a SandboxAgent with a Manifest containing a local folder with a README.md, runs it on a local Unix sandbox client (or Docker), and asks it to summarize the README. Keep instructions short and the task in a workspace file.

**Expected behavior**
- Uses `SandboxAgent` + `Manifest` (`LocalDir` or `GitRepo`) + a sandbox client in `SandboxRunConfig`, run through `Runner`.
- Keeps `instructions` short and puts the task spec in a workspace file.
- Notes that the API is beta and the version should be pinned.

**Acceptance checks**
- [ ] The summary quotes content that exists only in the workspace README (SKILL.md acceptance test 1).
- [ ] The script uses the APIs named in the current docs; check every import against them.

## Example 2: Triage handoff plus a blocking guardrail and MCP allowlist

**Input prompt**
> With openai-agents-sdk-sandbox, design a triage agent that hands document questions to a reviewer agent. Add a blocking input guardrail for off-policy prompts and an MCP server where only read tools are allowed. Explain handoff vs as_tool for this case.

**Expected behavior**
- Picks a handoff, so the reviewer becomes the active agent on the same run, and explains when as_tool would fit better.
- Sets the input guardrail with `run_in_parallel=False` so nothing expensive runs before the check.
- Filters MCP tools to the read-only ones and notes that a connected tool is not an authorized tool.

**Acceptance checks**
- [ ] An off-policy prompt trips the guardrail before any model or tool call (acceptance test 3).
- [ ] The delete tool cannot be seen or called (acceptance test 4).
