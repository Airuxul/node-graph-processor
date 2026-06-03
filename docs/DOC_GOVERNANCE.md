# Documentation Governance

**Last Updated:** 2026-06-02 · **Scope:** this package repository

## Layout

| Track | Paths |
|-------|--------|
| User | `README.md` (English), `README.zh-CN.md` (Chinese) |
| Agent | `docs/*.md` (English) |

Do **not** add `QUICKSTART.md` when quick-start steps fit in README. Do **not** add `.cursor/skills/` in this package — skills live only in the meta repo ([AirUnityPackage](https://github.com/Airuxul/AirUnityPackage)).

## Update workflow

1. In the **meta repository**, run skill `doc-read-index` (read-only inventory).
2. Apply changes with meta skill `doc-generate-update` (`.cursor/skills/` at meta root only).
3. Keep `README.md` and `README.zh-CN.md` in sync for user-visible changes.
4. Append non-trivial agent edits to `docs/CHANGELOG_AGENT.md`.

## Cross-repo rules

Layering, install index, and validation hooks are defined in the meta repo `docs/` ([DOC_GOVERNANCE](https://github.com/Airuxul/AirUnityPackage/blob/main/docs/DOC_GOVERNANCE.md), [AGENTS](https://github.com/Airuxul/AirUnityPackage/blob/main/docs/AGENTS.md)).

This package is a **standalone domain** module (upstream graph framework fork): document no dependency on `com.air.unity-game-core` unless that changes in `package.json` / asmdef. Document the `com.air.unity-behavior-tree` consumer when user-visible integration changes.
