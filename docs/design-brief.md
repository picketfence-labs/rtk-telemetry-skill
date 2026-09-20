# Design brief

## Problem

RTK telemetry failures can come from missing provider instructions, a different effective database path, sandbox write denial, stale sessions, or misreading `rtk discover` as Codex telemetry. A reusable Skill should guide diagnosis without embedding one Vault's absolute paths or migration history.

## Decision

Keep a small provider-neutral diagnostic core in this repository. Consumers pin it as a submodule and place expected paths and local verification rules in `.agents/skill-config/rtk-telemetry.md`.

Ordinary shell execution policy remains in host or machine-global agent instructions. The Skill handles telemetry inspection and explicitly authorized repair only.

## Safety invariants

- No machine-global mutation without exact authorization and backup.
- No broad sandbox root when a dedicated RTK data directory is sufficient.
- No destructive database migration or unverified history loss.
- No committed command-history samples, prompts, or credentials.
- `rtk discover` is described as Claude Code session analysis, not Codex history proof.
