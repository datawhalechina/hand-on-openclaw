# 文档待办清单

## 结构与导航

- [ ] 统一 `docs/basic/channels/*.md` 的章节模板（前置条件、配置步骤、排错、发布），当前飞书页仍偏长且混入两种流程。
- [ ] 补充 `docs/install/windows.md` 与 `docs/install/linux.md`、`docs/install/macos.md` 的交叉跳转，减少重复安装说明。
- [ ] 检查 `docs/basic/workspace.md` 的多重主题，必要时拆分为“Workspace 基础”和“人格配置示例”两页。

## 文风与编号

- [ ] 全站清理口语化表达（如“宝子”“丝滑”“开心了”），统一为教程文风。
- [ ] 统一编号规范：步骤使用“第 X 步”，子步骤使用 `X.Y`，避免 `1. ##` 这类混合写法复发。
- [ ] 统一英文术语大小写（`OpenClaw`、`API Key`、`Web UI`、`Gateway`）并消除同义写法。

## 内容完整性

- [ ] `docs/skills/install-skills.md` 中 `7.4` 与 `7.5` 仍为“待补充”，需补齐最小可执行示例。
- [ ] 复核所有命令示例是否可直接运行（特别是 `openclaw` 子命令和 JSON 片段）。
- [ ] 对模型教程补充版本前提（OpenClaw 最低版本、Provider 套餐前提、接口兼容模式）。

## 质量保障

- [ ] 增加文档检查脚本（标题层级、重复 H1、死链、图片路径有效性）。
- [ ] 在 CI 中加入 Markdown lint 与链接检查，避免后续导入内容破坏结构。
