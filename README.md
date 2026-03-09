# hand-on-openclaw

### OpenClaw 中文教程与实践手册

从安装部署到多模型接入、渠道联动、Skills 与自动化工作流，帮助中文用户用可复现步骤搭建自己的 OpenClaw 系统。

---

## 项目介绍

`hand-on-openclaw` 是一个面向中文用户的 OpenClaw 教程仓库。  
项目目标不是“概念速览”，而是“可以照着做并跑通”的实战文档。

当前文档采用 MkDocs 组织，覆盖以下主线：

- 安装部署：Windows / macOS / Linux / 云端
- 基础使用：首次对话、模型选择、渠道接入、Workspace、Memory
- Skills：安装、创建、发布、示例
- 自动化工作流：Cron / Heartbeat / Webhook
- 源码解析与实战项目

## 快速开始

### 在线阅读

- 文档入口：[docs/index.md](docs/index.md)
- MkDocs 导航配置：[mkdocs.yml](mkdocs.yml)

### 本地阅读

```bash
pip install -r requirements.txt
mkdocs serve
```

启动后访问本地地址（默认 `http://127.0.0.1:8000`）。

## 你将收获什么

- 用最小闭环方式完成 OpenClaw 安装、初始化与验证
- 掌握国内常见模型与 Provider 的接入方法
- 能把 OpenClaw 连接到飞书、钉钉、Telegram、Discord 等渠道
- 理解 Workspace / Memory / Skills 在实际项目中的使用边界
- 具备从“会用”到“可维护、可扩展”的文档化交付能力

## 内容地图

| 模块 | 关键内容 | 路径 |
| --- | --- | --- |
| 安装部署 | 系统安装、云端部署、排障 | [docs/install/](docs/install/) |
| 基础使用 | 首次对话、模型选择、渠道接入 | [docs/basic/](docs/basic/) |
| Skills | 安装、创建、发布、示例 | [docs/skills/](docs/skills/) |
| 自动化 | 定时任务、事件触发、健康检查 | [docs/automation/](docs/automation/) |
| 源码解析 | 架构、消息流、源码构建 | [docs/deep-dive/](docs/deep-dive/) |
| 实战项目 | 个人助手、团队机器人、自动化案例 | [docs/projects/](docs/projects/) |

## 学习顺序建议

1. 先完成 `install` + `basic/first-chat`，确保环境可用。
2. 再学习 `basic/choose-model` 与 `basic/channels`，打通模型和消息入口。
3. 最后进入 `skills` 与 `automation`，提升可用性和长期运行能力。

对应直达链接：

- [安装部署](docs/install/overview.md)
- [第一次对话](docs/basic/first-chat.md)
- [选择模型](docs/basic/choose-model.md)
- [聊天渠道](docs/basic/channels/feishu.md)
- [Skills](docs/skills/what-are-skills.md)
- [自动化工作流](docs/automation/cron.md)

## 项目结构（摘要）

- [docs/](docs/)：主文档目录（持续维护）
- [examples/](examples/)：配置、技能、流程示例
- [docold/](docold/)：历史归档（仅参考）
- [mkdocs.yml](mkdocs.yml)：文档导航与主题配置
- [requirements.txt](requirements.txt)：文档站依赖
- [README.md](README.md)：项目首页说明

## 贡献方式

欢迎任何形式的贡献：

- 报告问题：提交 Issue，附复现步骤与错误日志
- 修正文档：提交 PR，尽量按“目标 / 前置条件 / 步骤 / 验证 / 常见问题”组织
- 补充案例：优先提交可复现、可验证、可迁移的实战内容

提交前请注意：

- 示例配置必须脱敏，禁止提交真实密钥、Token、组织信息
- 涉及版本差异时，请注明 OpenClaw 与 Provider 的最低版本前提
- 待完成事项可参考 [docs/todo.md](docs/todo.md)

## 开源协议

本项目采用 [Apache 2.0](LICENSE) 协议。
