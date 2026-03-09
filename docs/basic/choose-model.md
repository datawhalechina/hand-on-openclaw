# 选择 AI 模型

这页作为模型教程总览，按 Provider 和使用场景拆分。你可以直接按目标跳转到对应子章节。

## 快速入口

- [多模型与 Provider 配置](models/multi-provider.md)
- [火山方舟（豆包）接入](models/volcengine-doubao.md)
- [火山 Coding Plan 教程](models/volcengine-coding-plan.md)
- [阿里云 Coding Plan 教程](models/aliyun-coding-plan.md)
- [LM Studio 本地模型接入](models/local-lmstudio.md)
- [Cherry Studio + Step 模型接入](models/cherry-step.md)
- [阿里云教程写作模板（附录）](models/aliyun-coding-plan-writing.md)

## 选型建议

1. 先跑通一个云端模型（火山或阿里云），确认 `openclaw onboard` 与 `openclaw dashboard` 正常。
2. 再接入本地模型（LM Studio），处理内网地址、显存和并发限制。
3. 有多模型切换需求时，最后再配置 `openclaw.json` 的多 provider 与默认模型。

## 推荐学习顺序

1. 新手：`volcengine-coding-plan` 或 `aliyun-coding-plan`
2. 进阶：`multi-provider`
3. 本地化：`local-lmstudio`
4. 桌面一体化：`cherry-step`
