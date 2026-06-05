# 待办 — `com.alelievr.node-graph-processor`

**最后更新：** 2026-06-03 · **范围：** 节点图处理器 Fork 现有功能的后续优化（中文）

> **职责边界：** 编辑器图 UI、导出管线、`RuntimeGraph` / `RuntimeGraphBuilder`、通用处理器。  
> **不负责：** BT 专用节点、`GameRuntime`、UI、连接器。  
> Agent 英文条目：[`docs/TODO.md`](docs/TODO.md)

## 现有能力概要

- UIElements 图编辑器与导出工具栏
- `GraphExporter` → JSON / GPGR 二进制封装
- `RuntimeGraph`、端口传播、`ProcessGraphProcessor`、`BaseGraphRunner`
- `SortChildrenGraphView` / `ISortChildrenByPosition`（与 BT 共用）

## 待办列表

| ID | 优先级 | 标题 | 说明 |
|----|--------|------|------|
| NGP-01 | P0 | `RuntimeGraph` 邻接缓存 | 实现代码内 TODO，避免每次全边扫描。 |
| NGP-02 | P0 | 减少端口装箱 | 按类型存储端口值。 |
| NGP-03 | P1 | 严格 `RuntimeGraphBuilder` | 未知 `runtimeNodeType` 失败；记录导出版本。 |
| NGP-04 | P1 | 参数反序列化 | 避免裸 `catch`；文档化 IL2CPP/link.xml。 |
| NGP-05 | P2 | 可配置导出路径 | 替代硬编码 `Assets/GraphExports`。 |
| NGP-06 | P2 | 上游合并手册 | alelievr 合并后回归。 |
| NGP-07 | P3 | 导出往返测试 | SO → JSON → 节点/边/参数计数。 |
| NGP-08 | P3 | 二进制格式说明 | 标明魔数 + UTF-8 JSON 载荷。 |
| NGP-09 | P3 | Runner 使用指引 | `BaseGraphRunner` vs 领域处理器（BT）。 |

## 请勿在本包实现

| 主题 | 归属包 |
|------|--------|
| `RuntimeBT*`、`BehaviorTreeProcessor` | `com.air.unity-behavior-tree` |
| NPC AI、黑板、游戏动作 | 游戏工程 |
| Air 运行时胶水 | `com.air.unity-game-core` |
