# JumpServe plugin

Assess research papers and run verification experiments in your local Claude
Code or Codex workspace. The plugin includes the Generator and Verifier skills
and the hosted MCP connector for saving results on JumpServe.

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

The Generator recreates the paper's testbed and uses fresh measurements to test
its claims. Published figures and tables supply reference values. Access,
Experiment, Data, and optional Validate modules record the setup, run
receipts and evidence.

When the design needs AWS, the
[temporary AWS testbed workflow](skills/jumpserve-paper-assessment/references/aws-testbeds.md)
uses account `395567831870` and the dedicated experiment role. It collects
evidence and verifies teardown before completing the assessment. The account
operator configures AWS access once.

Permission decisions belong to the user. If automatic review blocks an
attempt, the skill keeps the request pending for human review where policy
permits. See the
[approval workflow](skills/jumpserve-paper-assessment/references/permissions.md).
If the PDF download is blocked, download the private PDF from Step 1 and
[verify it offline](skills/jumpserve-paper-assessment/references/sharing.md#recover-from-a-blocked-pdf-download).

When the assessment finishes, the skill saves the bundle locally and sends the
results to JumpServe as a private assessment. JumpServe attaches the verified
Step 1 PDF and returns a link. Open it while signed in to review the Paper
Breakdown, Experiment Steps, Experiment Setup, and Experiment Results. Each
experiment keeps its number as its steps, commands, and measurements are added.
Public sharing requires owner approval of the saved assessment and makes the
attached PDF downloadable with the results. Raw evidence stays in your workspace.
Ask for a local-only assessment to keep your results in the workspace.

[View assessments on JumpServe](https://jumpserve.quaint-lab.org/research-verification/assessments)

## Verify a saved assessment

Use the [Verifier skill](skills/jumpserve-assessment-verifier/SKILL.md) in a separate
session with the saved assessment JSON, supporting evidence, and matching private
answer key. It checks the evidence and writes a claim-by-claim scorecard. With the
owner's authorization, save the scorecard privately against the exact Generator
result in JumpServe. Keep answer keys and raw logs in your local workspace.
