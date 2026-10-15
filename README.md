# Super Cocos Creator MCP

作者：**leeming**。面向 Cocos Creator 3.8 的 2D/3D 游戏开发、本地资源管理与多智能体接入插件。

自己的智能体软件：点击 **扩展 → Super Cocos Creator MCP → 查看／复制连接配置**，在弹出窗口复制地址、认证信息或完整 JSON。支持单连接配置和 mcpServers 格式。

**安装一个 Creator 插件，点一次菜单，就能让 Codex 控制编辑器。** 不用改游戏代码，不用单独启动服务端，不用安装 npm 依赖。

完整操作示例见 [使用方法](docs/usage.md)，多客户端接入见 [agent-kit](agent-kit/README.md)。

## 安装：只需三步

1. 在 Creator 的 **扩展 → 扩展管理器** 中导入 `release/super-cocos-creator-mcp.zip`，选择项目扩展并启用。如果编辑器只接受文件夹，解压后把 `super-cocos-creator-mcp` 整个文件夹放进游戏项目的 `extensions` 目录，再刷新扩展管理器。
2. 点击 **扩展 → Super Cocos Creator MCP**，选择 **安装 Codex 连接与技能** 或 **安装 Cursor 连接与技能**，在控制台确认安装成功。
3. **重启选择的客户端**，保持 Creator 项目打开，然后说：**“用 Creator MCP 看一下当前场景。”**

插件会同时安装 Codex 的 MCP 连接配置和 `super-cocos-creator-mcp` 技能，自动处理端口和本机凭据。技能本身不能建立连接，因此这两部分由同一个菜单一次完成。MCP 服务随 Creator 插件启动和停止。

Cursor 安装菜单会写入 `~/.cursor/mcp.json` 和 `~/.cursor/skills/super-cocos-creator-mcp/SKILL.md`，保留其他 MCP 配置和 JSON 注释。客户只需下载发布包，完整步骤见 [客户安装说明](docs/customer-install.md)（也包含在 ZIP 内）。仅支持同机本地客户端。

## 向客户发布

运行下面的构建命令生成 ZIP，将 `release/super-cocos-creator-mcp.zip` 作为代码托管平台 Release 附件提供。包内已包含运行依赖和安装说明。发布源码时包含源码目录、package.json、package-lock.json、scripts、test、docs；不要上传 node_modules、.cache、本机用户配置或连接凭据。当前尚未选定项目开源许可证；正式开源前由项目所有者确定并添加 LICENSE。这里生成了发布包，尚未上传到任何平台。

## 可以做什么

**v0.6.0：59 个工具，新增 UI/动画/事件/校验和本地资源库。** 完整列表与工作流见 [游戏制作说明](docs/game-authoring.md)。

- 查看当前项目、场景树、节点和组件属性。
- 创建节点、实例化现有预制体、添加 Label/Sprite/项目脚本组件。
- 修改名称、激活状态、位置、旋转、缩放和组件属性。
- 删除指定节点、保存当前场景。
- 配合 Codex 编辑项目 TypeScript 脚本，实现游戏逻辑。
- 创建场景与预制体，管理脚本、图片、音频、模型、材质和 shader 资源及导入选项。
- 打开独立游戏预览，截图、发送键鼠输入、检查浏览器运行状态和日志。
- 排队构建并查询原生构建任务进度和结果。
- 查询和调用 313 个 Creator 原生消息，或用 cc 引擎场景脚本处理复杂创作任务。

例如：**“在当前 Canvas 下创建一个 Label，文字为‘开始游戏’，居中显示。完成后保存场景。”**

创建 UI 时需要适当的 Canvas、相机和组件；运行测试使用插件自己的预览窗口。保存会保存当前场景全部未保存修改。平台签名、商店上传与第三方 SDK 不由插件自动提供。内部接口随版本变化，313 个目录条目并不等于所有编辑器功能已实测。

## 安装位置和排查

- 每个项目有独立连接名称 `creator_<项目ID>`。Codex 应先调用 `creator_status` 确认项目。
- 配置写入 `~/.codex/config.toml`，技能写入 `~/.codex/skills/cocos-creator-mcp/SKILL.md`；支持 `CODEX_HOME`。修改前会备份原配置，并保留其他配置项。
- 重复点安装菜单只更新本插件条目，不重复添加。不会覆盖同名但不属于本插件的技能。
- 看不到菜单：确认扩展启用，刷新扩展管理器或重开 Creator。
- Codex 找不到工具：点安装菜单并确认控制台成功，再重启 Codex。
- 连不上：Creator 必须打开对应项目；使用“扩展 → Super Cocos Creator MCP → 查看连接状态”查看启动情况。
- 若启动时端口被其他进程占用，会在控制台报错，不会静默连到另一个项目。
- 卸载时禁用/删除扩展；要清理 Codex 连接，删除配置中该项目 `BEGIN/END super-cocos-creator-mcp` 标记之间的段落。技能为多个项目共用。

## 开发与验证

源代码在 `creator-extension`。打包后的扩展包含完整服务端，不依赖游戏项目的 node_modules。

```powershell
npm.cmd ci
npm.cmd test
npm.cmd run build:creator
Compress-Archive -Path release/super-cocos-creator-mcp -DestinationPath release/super-cocos-creator-mcp.zip -Force
```

接口参数已核对本机 Creator **3.8.8** 的类型定义。自动测试使用官方 MCP 客户端完成 HTTP 初始化、列工具、调用、输入校验，并检查安装器保留其他配置和重复安装行为。编辑器场景操作仍需在实际 Creator 场景中验证；模拟接口测试不等同于实机测试。

参考：[Creator 3.8 扩展机制](https://docs.cocos.com/creator/3.8/manual/zh/editor/extension/first.html)、[Super Cocos Creator MCP 配置](https://developers.openai.com/codex/mcp)。

原先的 Cocos2d-x C++ 版本保留在 `cocos-client` 和 `src`，说明见 [旧版文档](docs/cocos2dx-legacy.md)。**Creator 用户不需要使用旧版。**

资源搜索、ZIP、AI 描述、按需导入的范围及使用方法见 [资源库说明](docs/resource-library.md)。

**v0.7.0 多智能体接入：** 保留 HTTP，新增带认证的 WebSocket 自定义传输，以及无第三方依赖的 stdio → HTTP 桥接。可直接放进 Git 的配置模板、通用技能、生成脚本与接入说明位于 [agent-kit](agent-kit/README.md)。Creator 菜单可导出包含本机连接描述的私有接入包。

统一注册名称：插件和技能为 `super-cocos-creator-mcp`，项目服务为 `super-cocos-creator-mcp-<项目ID>`。v0.7.2 安装器迁移旧版服务与技能，旧技能备份到客户端 skill-backups 目录，保留本地资源库和连接凭据。
