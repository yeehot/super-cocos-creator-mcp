# super-cocos-creator-mcp · 智能体接入与技能

作者：**leeming** · 版本：**v0.7.2**。

本仓库仅提供智能体客户端接入文件、配置模板、桥接示例和技能说明。**Cocos Creator 服务端插件为单独销售的商业产品，本仓库不包含插件安装包、服务端源码或完整产品源码压缩包。**

## 下载与安装

- [下载智能体接入与技能包](super-cocos-creator-mcp-agent-kit.zip)
- [查看技能 SKILL.md](SKILL.md)
- [使用说明](usage.md)

接入包解压后包括：

- `skills/super-cocos-creator-mcp/SKILL.md`：智能体技能。
- `templates/`：Codex、Cursor、VS Code、Claude Code、Claude Desktop 等配置模板。
- `scripts/configure.mjs`：根据本机 Creator 连接信息生成配置。
- `scripts/http-stdio.mjs`：仅支持 stdio 的 MCP 客户端使用的 HTTP 桥接。
- `examples/websocket-client.mjs`：自研客户端 WebSocket 接入示例。
- `README.md` 与 `AGENTS.md`：客户端与智能体安装说明。

## 使用前提

1. 已另行获得并安装商业 Creator 插件，在 Cocos Creator 3.8.x 启用并打开项目。
2. 客户端和 Creator 在同一台电脑运行。
3. 从 Creator 插件复制或导出你自己的连接地址与 Token。公开模板只有占位值，不能直接连接。

## Codex / Cursor

如果商业插件提供“一键安装连接与技能”菜单，直接使用该入口，再重启客户端即可。也可以从本仓库下载技能包，按对应客户端的技能与 MCP 设置手动安装。

## Forge Desk / mydesk

1. 在 Creator 的“查看／复制连接配置”复制 mcpServers JSON。
2. 在 Forge 的“添加 → 粘贴 MCP JSON 配置”中预览，再点“保存并连接”。
3. 选择“导入技能文件夹”，导入解压后的 `skills/super-cocos-creator-mcp`。
4. 新建任务，先调用 creator_status，确认实际连接的项目。

## 其他智能体

下载并解压接入包，让智能体读取其中 README.md 和 AGENTS.md。使用本机连接文件生成对应客户端配置，只合并当前服务项，不覆盖其他服务。

HTTP 是通用接入；stdio 客户端使用桥接；WebSocket 需要客户端支持包内定义的自定义 JSON-RPC 传输。仅安装技能不会自动建立连接。

## 开始创作

> 使用 super-cocos-creator-mcp 技能，确认当前 Creator 项目，查看场景层级，暂时不要修改。

连接成功后，可继续要求制作 2D / 3D 游戏原型、编辑 UI、编写玩法、配置动画，再通过预览截图、输入、运行状态和日志检查结果。

## 命名与隐私

- 插件与技能：`super-cocos-creator-mcp`。
- 项目服务：`super-cocos-creator-mcp-<项目ID>`。
- 公开包不包含真实 Token。不要提交 `connection.local.json` 或生成后的本机配置。
- 本仓库公开接入文件不代表授权使用或再分发商业插件。
