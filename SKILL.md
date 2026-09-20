---
name: rtk-telemetry
description: Diagnose and maintain RTK command-history and token-savings telemetry across Codex and Claude Code. Use for rtk gain/history/discover, database paths, sandbox persistence, or telemetry repair; not for ordinary shell execution.
---

# RTK Telemetry

Use this Skill only for RTK tracking diagnostics and maintenance. It does not replace host instructions that require ordinary shell commands to run through `rtk`.

## Host policy

If the current repository provides `.agents/skill-config/rtk-telemetry.md`, read it before diagnosing the installation. Treat it as the source for the expected database path, provider setup, and local verification requirements. Host policy may narrow this workflow but must not silently authorize machine-global changes.

## Diagnose

1. Identify the active provider, sandbox mode, RTK version, `RTK_DB_PATH`, and the effective history database before drawing conclusions.
2. Run `rtk init -g --codex --show` when checking Codex global instruction installation. Do not mutate the installation merely to inspect it.
3. Run a harmless `rtk` command, then inspect `rtk gain --history` for persistence. A session that predates configuration changes is not sufficient evidence; use a fresh native provider session when the host policy requires end-to-end verification.
4. Use `rtk discover` only to analyze Claude Code session history. It does not prove that Codex commands were recorded.
5. Distinguish command capture, database persistence, token-savings estimates, and billed-token measurements. `rtk gain` is an estimate, not billing ground truth.

## Repair boundaries

- Before changing machine-global provider configuration, global instructions, or telemetry databases, obtain authorization for the exact mutation and back up every affected file or database.
- Grant write access only to the telemetry database directory required by RTK. Do not broaden a sandbox root to a parent application-data directory, the home directory, or a Vault.
- Preserve existing history. For database migrations, inspect schemas, back up both sides, deduplicate records, and verify counts and a fresh probe before retiring the old path.
- Never expose command history, prompts, credentials, or database contents in committed fixtures or reports. Prefer counts and redacted identifiers.
- Report which checks were current-session observations and which were verified in a fresh native session.
