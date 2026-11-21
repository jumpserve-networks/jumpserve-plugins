# JumpServe plugin

Assess research papers and run verification experiments in your local Claude
Code or Codex workspace. The plugin includes the JumpServe paper assessment
skill and the hosted MCP connector for optional sharing.

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

Start a new client session and ask the JumpServe paper assessment skill to
assess a local PDF. The skill saves the assessment bundle and experiment
evidence in your workspace.

When you want to share, sign in to JumpServe with Google through `/mcp` in
Claude Code or `codex mcp login jumpserve` in Codex. Ask the client to share
your assessment. Review and approve the public preview on JumpServe, then ask
the client to finish sharing. Your original PDF and raw experiment files stay
in your workspace.

[View assessments on JumpServe](https://jumpserve.quaint-lab.org/research-verification/assessments)
