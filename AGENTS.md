# Repository instructions

This repository is the canonical implementation of the `rtk-telemetry` Skill.

Before substantial changes, read `docs/design-brief.md` and `SKILL.md`. Keep ordinary RTK command enforcement outside this Skill, preserve telemetry history, and require exact authorization before machine-global mutations.

Validate changes with the installed `skill-creator` `quick_validate.py`. Keep host-specific paths, provider configuration, migration history, credentials, and command-history samples out of the shared core. Consuming repositories may provide `.agents/skill-config/rtk-telemetry.md`.
