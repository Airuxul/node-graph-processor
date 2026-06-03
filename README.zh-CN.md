# Node Graph Processor（`com.alelievr.node-graph-processor`）

[English](README.md)

基于 UIElements 的节点图编辑器框架。本仓库为 [alelievr/NodeGraphProcessor](https://github.com/alelievr/NodeGraphProcessor) 的 **Air 维护分支**，在编辑器导出与运行时执行管线上做了扩展。

**分层：** 独立域包，不依赖 `com.air.unity-game-core`、`com.air.game-core` 或 `com.air.unity-ui`。

## 分支说明

| | |
|---|---|
| 上游 | [github.com/alelievr/NodeGraphProcessor](https://github.com/alelievr/NodeGraphProcessor) |
| Air 分支 | [github.com/Airuxul/node-graph-processor](https://github.com/Airuxul/node-graph-processor) |
| Air 扩展 | 编辑器导出 `GraphExportData`（JSON/二进制）；`RuntimeGraph` / `RuntimeGraphBuilder`；运行时处理器与示例运行时节点 |

合并上游修复时请保持现有 `Editor/`、`Runtime/` 目录结构，避免大范围重命名。

## 安装

在 Unity 项目的 **`Packages/manifest.json`** 中加入（路径相对 Unity 工程根目录）：

```json
"com.alelievr.node-graph-processor": "file:../CustomPackages/packages/com.alelievr.node-graph-processor"
```

也可通过 [AirUnityPackage](https://github.com/Airuxul/AirUnityPackage) 元仓库的 `tools/install-packages.ps1` 与 `config/registry.json` 安装（本包 `installDefault: true`）。

需要 Unity **2020.3+**（见 `package.json`）。

## 行为树依赖

| 使用方 | 用途 |
|--------|------|
| [`com.air.unity-behavior-tree`](../com.air.unity-behavior-tree/README.zh-CN.md) | 行为树图资源、BT 编辑器节点、运行时树执行 |

安装 `com.air.unity-behavior-tree` 时，`package.json` 会自动拉取 `com.alelievr.node-graph-processor` **1.3.1+**。

## 快速开始

1. 按上文 **安装** 将包加入 manifest。
2. 按上游方式创建图资源：继承 `BaseGraph` / `BaseNode`，或在 Package Manager 中导入 **Samples → Examples**。
3. 在图窗口（`BaseGraphWindow` / `DefaultGraphWindow`）中编辑节点图。
4. 运行时数据：在编辑器侧用 `GraphExportUtils.ExportToJson` 或 `ExportToBinary` 导出，在运行时用 `RuntimeGraphBuilder.FromJson` / `FromBinary` 加载。
5. 使用 `ProcessGraphProcessor` 或自定义 `BaseGraphRunner` 子类驱动执行。

行为树专用编辑流程见行为树包 README。

## 目录结构

| 目录 | 说明 |
|------|------|
| `Editor/` | 图 UI、节点视图、资源编辑、导出工具 |
| `Runtime/` | `GraphExportData`、`RuntimeGraph`、处理器、Runner |
| `Samples~/Examples` | 上游风格的自定义节点/图示例 |

## 相关

- [Behavior Tree](../com.air.unity-behavior-tree/README.zh-CN.md)
- 元仓库：[PACKAGES.md](https://github.com/Airuxul/AirUnityPackage/blob/main/docs/PACKAGES.md)、[registry.json](https://github.com/Airuxul/AirUnityPackage/blob/main/config/registry.json)
