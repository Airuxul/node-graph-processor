# AGENTS — `com.alelievr.node-graph-processor`

**Last Updated:** 2026-06-02 · **Scope:** canonical agent entry (this repository)

## User documentation

| File | Language |
|------|----------|
| [README.md](../README.md) | English |
| [README.zh-CN.md](../README.zh-CN.md) | Chinese |

## Agent documentation

| File | Purpose |
|------|---------|
| [AGENTS.md](AGENTS.md) | This file |
| [DOC_GOVERNANCE.md](DOC_GOVERNANCE.md) | Doc workflow for this repo |
| [CHANGELOG_AGENT.md](CHANGELOG_AGENT.md) | Agent change log |

## Package role

| Item | Value |
|------|--------|
| Package id | `com.alelievr.node-graph-processor` |
| Layer | Standalone **domain** UPM package (third-party graph framework fork) |
| Upstream | [alelievr/NodeGraphProcessor](https://github.com/alelievr/NodeGraphProcessor) |
| Air fork | [Airuxul/node-graph-processor](https://github.com/Airuxul/node-graph-processor) |
| Meta index | [AirUnityPackage](https://github.com/Airuxul/AirUnityPackage) (`config/registry.json`) |

**Dependencies:** none on `com.air.unity-game-core`, `com.air.game-core`, or `com.air.unity-ui`. Runtime asmdef has empty `references`.

**Primary consumer in Air stack:** `com.air.unity-behavior-tree` (Editor + Runtime asmdefs reference this package).

## Module map

| Path | Responsibility |
|------|----------------|
| `Editor/Graph/BaseGraph.cs` | ScriptableObject graph asset, nodes, edges, groups |
| `Editor/Elements/BaseNode.cs`, `NodePort.cs` | Editor node model and ports |
| `Editor/Views/BaseGraphView.cs`, `BaseNodeView.cs` | UIElements graph editor UI |
| `Editor/Utils/GraphExporter.cs`, `GraphExportUtils.cs` | Editor → `GraphExportData` (JSON / binary export) |
| `Editor/Processing/EditorGraphProcessor.cs` | Editor-time graph processing |
| `Runtime/GraphExportData.cs` | Serializable export payload |
| `Runtime/RuntimeGraphBuilder.cs` | Build `RuntimeGraph` from JSON or binary |
| `Runtime/Graph/RuntimeGraph.cs` | Runtime graph instance |
| `Runtime/Processing/ProcessGraphProcessor.cs`, `BaseRuntimeGraphProcessor.cs` | Runtime execution |
| `Runtime/Nodes/RuntimeBaseNode.cs` | Runtime node base; relay / parameter / log variants |
| `Runtime/Runner/BaseGraphRunner.cs` | Hook for driving a graph at runtime |

Namespace for C# types: **`GraphProcessor`** (upstream convention). Asmdefs: `com.alelievr.NodeGraphProcessor.Runtime`, `com.alelievr.NodeGraphProcessor.Editor`.

## Fork maintenance

- Preserve upstream directory layout when merging upstream fixes; avoid broad renames (see meta [C_SHARP_STANDARDS §4.5](https://github.com/Airuxul/AirUnityPackage/blob/main/.cursor/rules/C_SHARP_STANDARDS.md)).
- Air-specific additions: export pipeline (`GraphExportData`, `RuntimeGraphBuilder`, binary magic `GPGR`), runtime processors and sample runtime nodes.

## Required reads before doc updates

1. `docs/AGENTS.md`
2. `docs/DOC_GOVERNANCE.md`
3. `README.md`, `README.zh-CN.md`

## Meta repository standards

When editing C# or package layout, also follow (meta repo):

- [C_SHARP_STANDARDS](https://github.com/Airuxul/AirUnityPackage/blob/main/.cursor/rules/C_SHARP_STANDARDS.md)
- [ARCHITECTURE](https://github.com/Airuxul/AirUnityPackage/blob/main/.cursor/rules/PACKAGE_ARCHITECTURE.md)
- [CONSTRAINTS](https://github.com/Airuxul/AirUnityPackage/blob/main/.cursor/rules/PACKAGE_CONSTRAINTS.md)

Use `Runtime/` + `Editor/` only. Do **not** add `.cursor/skills/` in this package.
