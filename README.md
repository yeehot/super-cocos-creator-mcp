# super-cocos-creator-mcp

作者：**leeming** · 当前版本：**v0.7.2** · 适配 Cocos Creator 3.8.x。

让 AI 参与 2D / 3D 游戏设计与开发：搭建场景、制作 UI、编写玩法脚本、编辑动画，并通过预览、交互输入、运行状态和日志持续检查结果。

## 下载

- [Creator 插件安装包](super-cocos-creator-mcp.zip)：在 Creator 扩展管理器安装，无需安装 npm 依赖。
- [多智能体配置与技能包](super-cocos-creator-mcp-agent-kit.zip)：包含统一技能、常用客户端配置模板、生成脚本及 stdio 桥接。
- [完整源码包](super-cocos-creator-mcp-github-source.zip)：源码、测试、构建脚本、文档及图文介绍，解压后开发。
- [使用方法](usage.md)
- [技能说明 SKILL.md](SKILL.md)

本仓库当前以可下载安装包与完整源码压缩包分发。开发时请先解压源码包，在含 package.json 的源码目录执行 npm ci、npm test、npm run build:creator；不要直接在仅下载了仓库分发文件的目录运行构建。

## 安装使用

1. 下载插件 ZIP，在 Creator 的“扩展 → 扩展管理器”中安装为项目扩展并启用。旧版 codex-cocos-creator 应先禁用。
2. 打开“扩展 → Super Cocos Creator MCP”，点击“安装 Codex 连接与技能”或“安装 Cursor 连接与技能”。
3. 重启对应客户端，保持 Creator 项目打开。
4. 发送：

> 使用 super-cocos-creator-mcp 技能，确认当前 Creator 项目并查看场景层级，暂时不要修改。

其他客户端：从插件复制连接配置，在客户端导入 MCP JSON；再从接入包安装 skills/super-cocos-creator-mcp 技能文件夹。不支持技能的客户端可读取 SKILL.md 作为项目说明。MCP 连接与技能是两部分，只安装技能不能连接编辑器。

Forge Desk / mydesk 可使用“粘贴 MCP JSON 配置 → 保存并连接”和“导入技能文件夹”。

## 游戏开发功能

- 场景创建、打开、保存、切换、层级查询、撤销重做与场景脚本执行。
- 节点 CRUD、复制、变换、搜索、批量修改、剪贴板与组件配置。
- 玩法脚本读写、注册组件挂载、点击等事件绑定和批量事件配置。
- JSON UI 层级构建，按钮、菜单、HUD 和对话框模板。
- 预制体创建与实例化，部分原生应用、还原和解除关联操作。
- 动画剪辑、轨道、关键帧、插值、切线、事件和预设；已有 Spine 动画与皮肤控制。
- 独立游戏预览、截图、键鼠输入模拟、运行状态读取、控制台和项目日志。
- 部分场景结构校验、结构快照比较、构建触发和任务结果查询。
- 创作辅助：本地项目、文件夹及 ZIP 的素材检索、图片预览、标签、部分依赖分析和按需导入。

共 **59 个 MCP 工具入口**。并非所有编辑器内部接口均已实机验证，复杂游戏需分阶段制作和验收。

## 接入方式

HTTP Streamable MCP 为通用入口；提供 stdio → HTTP 桥接和自定义 WebSocket 传输。客户端与 Creator 在同机运行；不同客户端支持情况需实际验收。

插件、技能统一名称：super-cocos-creator-mcp。多项目服务名：super-cocos-creator-mcp-项目ID。

**公开包不包含真实 Token。** 客户必须从自己的 Creator 生成连接配置，不能公开提交本机连接文件。

## 能力范围

精细模型、贴图和音效需要已有素材或其他制作工具。没有联网素材搜索、商店下载、模型 / FBX 动画自动渲染预览、包更新或共享数据库。构建依赖目标平台环境，不等于自动发布。开源许可证尚待作者选择，当前不声明 MIT 等授权。

## 产品图文介绍

![游戏创作功能介绍](super-cocos-creator-mcp-game-creation.png)

图中为功能创意与流程示意，非实机效果承诺。
