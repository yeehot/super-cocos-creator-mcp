# 智能体接入使用方法

作者：leeming · super-cocos-creator-mcp v0.7.2。

## 第一步：准备商业插件

先从作者提供的商业渠道获得 Creator 插件，在 Cocos Creator 3.8.x 中安装并启用。本 GitHub 仓库只提供客户端接入、配置模板和技能，不提供收费插件及其服务端源码。

Creator 须保持打开，客户端与 Creator 在同一台电脑。

## 第二步：下载公开接入包

下载本仓库的 `super-cocos-creator-mcp-agent-kit.zip` 并解压，保留文件夹结构。

支持技能的客户端导入 `skills/super-cocos-creator-mcp`；不支持技能的客户端读取其中 SKILL.md 正文作为项目指导。

## 第三步：配置连接

在 Creator 插件“查看／复制连接配置”中复制单连接或 mcpServers JSON，导入智能体的 MCP 设置。

Forge Desk / mydesk：添加 → 粘贴 MCP JSON 配置 → 预览 → 保存并连接；随后导入技能文件夹。

Codex / Cursor：优先使用商业插件自带的一键安装菜单。其他客户端参考接入包 templates 和 README。

如需生成配置，在包含 agent-kit 目录的位置运行：

```sh
node agent-kit/scripts/configure.mjs --connection connection.local.json --out .local/creator-clients
```

独立解压包后若当前目录本身就是 agent-kit，命令改为 `node scripts/configure.mjs --connection connection.local.json --out .local/creator-clients`。

生成文件含本机 Token，不要提交 Git。仅安装技能不能建立 MCP 连接。

## 第四步：验证与使用

重启或重新加载客户端，新建任务：

> 使用 super-cocos-creator-mcp 技能，先调用 creator_status，确认连接项目并读取场景，暂时不要修改。

确认后再安排创作，例如：

> 制作一个 2D 收集金币游戏原型，实现移动、计分和重开，完成后预览，通过输入与状态验证流程。

> 在 3D 场景中配置地面、相机和角色移动，优先使用已有模型，没有时使用基础几何体，运行后检查交互。

> 调整主菜单 UI，绑定已有脚本方法，修改后截图检查，不改动无关节点。

## 运行检查与构建

按“编辑 → 预览 → 输入与状态检查 → 日志排错 → 修正 → 构建查询”迭代。截图不能单独证明玩法正确。构建平台、SDK、签名与发布条件由项目环境提供。

## 排查

找不到工具时检查 Creator 是否打开、插件是否启用、地址和认证是否有效，再重新加载客户端。超时后先检查实际状态，不要重复执行修改。不要向公开仓库上传本机 Token 或收费插件。
