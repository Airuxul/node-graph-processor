# TODO — `com.alelievr.node-graph-processor`

**Last Updated:** 2026-06-03 · **Owner:** package maintainers · **Scope:** graph processor fork follow-ups (English)

> **User doc (Chinese):** [../TODO.zh-CN.md](../TODO.zh-CN.md)

> **Boundary:** Editor graph UI, export pipeline, `RuntimeGraph` / `RuntimeGraphBuilder`, generic processors.  
> **Out of scope:** BT-specific nodes, `GameRuntime`, UI, connector.  
> **Meta rollup:** [AirUnityPackage `docs/TODO_ROADMAP.md`](https://github.com/Airuxul/AirUnityPackage/blob/main/docs/TODO_ROADMAP.md)

## Capability baseline

- UIElements editor (`BaseGraphWindow`, `BaseGraphView`, export toolbar)
- `GraphExporter` → JSON / GPGR binary wrapper
- `RuntimeGraph`, port propagation, `ProcessGraphProcessor`, `BaseGraphRunner`
- `SortChildrenGraphView` / `ISortChildrenByPosition` (shared with BT)

## TODO

| ID | Pri | Title | Description |
|----|-----|-------|-------------|
| NGP-01 | P0 | `RuntimeGraph` adjacency caches | Implement todos on `GetInputNodes` / `GetOutputNodes` (full edge scan today). |
| NGP-02 | P0 | Reduce port value boxing | Typed stores per `RuntimeGraph` todo comments. |
| NGP-03 | P1 | Strict `RuntimeGraphBuilder` | Fail on unknown `runtimeNodeType`; log export version. |
| NGP-04 | P1 | `DeserializeParameterValue` | No bare catch; document IL2CPP / link.xml for AQN types. |
| NGP-05 | P2 | Configurable export path | Replace hardcoded `Assets/GraphExports` default. |
| NGP-06 | P2 | Upstream merge playbook | Regression pass after alelievr pulls. |
| NGP-07 | P3 | Export round-trip tests | SO → JSON → node/edge/param counts. |
| NGP-08 | P3 | Binary format docs | Clarify magic + UTF-8 JSON payload vs structural binary. |
| NGP-09 | P3 | Runner guidance | When to use `BaseGraphRunner` vs domain processors (BT). |

## Do not assign here

| Topic | Owner package |
|-------|----------------|
| `RuntimeBT*`, `BehaviorTreeProcessor` | `com.air.unity-behavior-tree` |
| NPC AI, blackboards, game actions | Game project |
| Air stack runtime glue | `com.air.unity-game-core` |
