# rtk-telemetry-skill

Diagnose and maintain RTK command-history and token-savings telemetry for Codex and Claude Code without conflating telemetry repair with ordinary shell-command enforcement.

> Status: private shared Skill repository. Consumer rollout is in progress.

## Scope

The Skill checks RTK instruction installation, effective history-database paths, sandbox persistence, `rtk gain --history`, and the provider-specific limits of `rtk discover`. Machine-global repairs require explicit authorization and backups.

## Host configuration

A consuming repository may provide `.agents/skill-config/rtk-telemetry.md` with its expected database path, provider configuration, and fresh-session verification requirements. Host policy must not silently authorize global mutations.

## Installation model

Shared Vaults install this repository as a Git submodule at `.agents/skills/rtk-telemetry` and pin a reviewed commit. Claude Code may use a relative symlink from `.claude/skills/rtk-telemetry`; Codex reads the `.agents/skills/` checkout directly.

Repository: <https://github.com/picketfence-labs/rtk-telemetry-skill>

## Validation

Run the installed `skill-creator` `quick_validate.py` against the repository root. Validate end-to-end telemetry from fresh native provider sessions because an existing session may predate configuration changes.
