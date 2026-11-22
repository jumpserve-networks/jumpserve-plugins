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
`codex mcp login jumpserve` in Codex. Start a new client session. Upload the
PDF in Step 1 on [Assess a Paper](https://jumpserve.quaint-lab.org/research-verification/new-assessment)
and paste the provided prompt. The skill uses the assessment ID to download
and verify the PDF with the same Google account.

The skill composes local tests using Access, Experiment, Data, and optional
Validate modules. It checks compatibility before running and records module
versions with the evidence. An assessment request authorizes the skill to run
in-scope local experiments within the available permissions and any limits you
specify.

Permission decisions belong to the user. If automatic review blocks an
attempt, the skill keeps the request pending for human review where policy
permits. See the
[approval workflow](skills/jumpserve-paper-assessment/references/permissions.md).
If the PDF download is blocked, download the private PDF from Step 1 and
[verify it offline](skills/jumpserve-paper-assessment/references/sharing.md#recover-from-a-blocked-pdf-download).

When the assessment finishes, the skill saves the bundle locally and sends the
results to JumpServe as a private assessment. JumpServe attaches the verified
Step 1 PDF and returns a link. Open it while signed in to review the Paper
Breakdown, Experiment Steps, Experiment Setup, and Experiment Results. The
assessment stays private until you share it publicly. Public sharing makes the
attached PDF downloadable with the results. Raw evidence stays in your workspace.
Ask for a local-only assessment to keep your results in the workspace.

[View assessments on JumpServe](https://jumpserve.quaint-lab.org/research-verification/assessments)
