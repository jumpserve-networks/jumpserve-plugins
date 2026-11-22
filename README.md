# JumpServe plugin

Assess research papers and run verification experiments in your local Claude
Code or Codex workspace. The plugin includes the JumpServe paper assessment
skill and the hosted MCP connector for viewing results on JumpServe.

## Install

### Claude Code

```sh
claude plugin install jumpserve --marketplace jumpserve-networks/jumpserve-plugins
```

With Claude Code versions that use separate marketplace and install commands,
run both commands:

```sh
claude plugin marketplace add jumpserve-networks/jumpserve-plugins
claude plugin install jumpserve@jumpserve
```

### Codex

```sh
codex plugin marketplace add jumpserve-networks/jumpserve-plugins
codex plugin add jumpserve@jumpserve
```

## Assess and share

Connect to JumpServe with Google using `/mcp` in Claude Code or
`codex mcp login jumpserve` in Codex. Start a new client session and ask
JumpServe to assess a local PDF.

The skill composes local tests using Access, Experiment, Data, and optional
Validate modules. It checks compatibility before running and records module
versions with the evidence.

Permission decisions belong to the user. If automatic review blocks an
attempt, the skill keeps the request pending for human review where policy
permits. See the
[approval workflow](skills/jumpserve-paper-assessment/references/permissions.md).
If the PDF download is blocked, download the private PDF from Step 1 and
[verify it offline](skills/jumpserve-paper-assessment/references/sharing.md#recover-from-a-blocked-pdf-download).

When the assessment finishes, the skill saves the bundle locally, sends a
private preview through MCP, and replies with a completion message and the
JumpServe URL. Open the link while signed in to review the numbered Paper
Breakdown, Experiment Steps, Experiment Setup, and Experiment Results. The
skill uploads a verified source PDF copy to the private preview. Approving
public sharing makes that copy downloadable with the assessment. Your original
PDF and raw evidence stay in your workspace. Ask for a local-only assessment
to keep the bundle and PDF in your workspace.

[View assessments on JumpServe](https://jumpserve.quaint-lab.org/research-verification/assessments)
