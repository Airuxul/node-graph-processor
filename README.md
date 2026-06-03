# Node Graph Processor (`com.alelievr.node-graph-processor`)

[简体中文](README.zh-CN.md)

UIElements-based node graph editor framework. This repository is an **Air-maintained fork** of [alelievr/NodeGraphProcessor](https://github.com/alelievr/NodeGraphProcessor), extended with editor-to-runtime export and a runtime execution pipeline.

**Layer:** standalone domain package — does not depend on `com.air.unity-game-core`, `com.air.game-core`, or `com.air.unity-ui`.

## Fork attribution

| | |
|---|---|
| Upstream | [github.com/alelievr/NodeGraphProcessor](https://github.com/alelievr/NodeGraphProcessor) |
| Air fork | [github.com/Airuxul/node-graph-processor](https://github.com/Airuxul/node-graph-processor) |
| Air additions | `GraphExportData` + JSON/binary export from the Editor; `RuntimeGraph` / `RuntimeGraphBuilder`; runtime processors and sample runtime nodes |

When pulling upstream fixes, keep the existing `Editor/` and `Runtime/` layout; avoid broad directory renames.

## Install

**Unity `Packages/manifest.json`** (path relative to your Unity project):

```json
"com.alelievr.node-graph-processor": "file:../CustomPackages/packages/com.alelievr.node-graph-processor"
```

From the [AirUnityPackage](https://github.com/Airuxul/AirUnityPackage) meta repo you can also use `tools/install-packages.ps1` and `config/registry.json` (`installDefault: true` for this package).

Requires Unity **2020.3+** (see `package.json`).

## Used by Air behavior trees

| Consumer | Usage |
|----------|--------|
| [`com.air.unity-behavior-tree`](../com.air.unity-behavior-tree/README.md) | Behavior-tree graph assets, custom BT editor nodes, runtime tree execution |

Installing `com.air.unity-behavior-tree` pulls `com.alelievr.node-graph-processor` **1.3.1+** via `package.json`.

## Quick start

1. Add the package to your manifest (see **Install**).
2. Create a graph asset (upstream flow): extend `BaseGraph` / `BaseNode` or use **Samples → Examples** from the Package Manager.
3. Author graphs in the graph window (`BaseGraphWindow` / `DefaultGraphWindow`).
4. Export for runtime: use `GraphExportUtils.ExportToJson` or `ExportToBinary` from Editor tooling, then load with `RuntimeGraphBuilder.FromJson` / `FromBinary` in play mode or builds.
5. Drive execution via `ProcessGraphProcessor` or a custom `BaseGraphRunner` subclass.

For behavior-tree-specific authoring, see the behavior-tree package README.

## Layout

| Area | Purpose |
|------|---------|
| `Editor/` | Graph UI, node views, asset authoring, export utilities |
| `Runtime/` | `GraphExportData`, `RuntimeGraph`, processors, runners |
| `Samples~/Examples` | Upstream-style custom node / graph examples |

## Related

- [Behavior Tree](../com.air.unity-behavior-tree/README.md)
- Meta repo: [PACKAGES.md](https://github.com/Airuxul/AirUnityPackage/blob/main/docs/PACKAGES.md), [registry.json](https://github.com/Airuxul/AirUnityPackage/blob/main/config/registry.json)
