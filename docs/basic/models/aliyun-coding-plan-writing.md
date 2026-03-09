# 阿里云 Coding Plan 写作模板（附录）

从零配置 OpenClaw + 阿里云 Coding Plan

一份可直接发布的详细教程 + 写作方案

## 第一部分：这篇教程该怎么写

如果你的目标不是“自己看懂”，而是“让别人照着一步一步配通”，那文章结构就不能只写概念，而要围绕“最小闭环”展开：让读者先完成一次本地安装、接入、验证，再考虑进阶玩法。

## 1. 建议你先锁定这篇文章的目标读者

• 第一次接触 OpenClaw，对 CLI、网关、模型配置没有完整心智模型的人。

• 已经知道阿里云百炼，但不清楚 Coding Plan 与普通按量付费 API Key 的区别的人。

• 真正想跑通本地聊天或编码助手，而不是一开始就做飞书/QQ/Telegram/远程多机部署的人。

## 2. 最推荐的文章主线

1. 先告诉读者这篇文章能解决什么问题，以及不解决什么问题。
2. 交代前置条件：系统、Node.js、阿里云账号、风险说明。
3. 购买 Coding Plan，并拿到专属 API Key 与 Base URL。
4. 安装 OpenClaw，完成首次引导（onboarding）。
5. 在 OpenClaw 中写入 Coding Plan 配置，并解释每个关键字段。
6. 打开 dashboard 验证接入是否成功，再教读者切换模型。
7. 单独整理常见报错和避坑，让读者遇到问题时能快速定位。

## 3. 写作时要重点强调的四个点

## 第二部分：可直接发布的成稿

下面这部分内容已经按照“可直接发布”的形式整理。你可以直接复制到 Word、飞书文档、语雀、公众号编辑器，或者作为你后续改写的底稿。

## 从零配置 OpenClaw + 阿里云 Coding Plan 详细教程

这篇教程的目标很明确：让你从 0 开始，在本地安装 OpenClaw，并把它接到阿里云百炼 Coding Plan 上，最终能在 dashboard 或 TUI 中正常调用模型。

为了降低变量和踩坑概率，正文只讲“本地 OpenClaw + 手动接入 Coding Plan”的最小可用路径。飞书、QQ、Tailscale、远程网关、阿里云服务器镜像等扩展玩法，本文只在最后给出延伸说明，不放进主流程。

### 一、这篇教程适合谁

• 你已经有阿里云账号，准备开通百炼并购买 Coding Plan。

• 你想在自己的电脑上先把 OpenClaw 跑起来，而不是先做远程服务器、IM 渠道接入。

• 你希望把模型调用成本控制在可预期范围内，而不是直接用普通按量付费模式。

### 二、你需要提前准备什么

### 三、先搞懂：OpenClaw 和 Coding Plan 分别做什么

OpenClaw 可以理解为一个开源的个人 AI 助手平台。你可以把它看作“运行时”和“交互外壳”：它负责网关、配置、会话、UI、工具调用等。模型能力本身则来自你接入的模型服务。

阿里云百炼 Coding Plan 则是一个面向 AI 编程场景的订阅型套餐。它不是普通的按量 API，而是一套固定月费、按请求额度消耗的编码套餐，接入时必须使用套餐专属 API Key（通常以 sk-sp- 开头）和专属 Base URL。

你可以把两者的关系理解为：OpenClaw 负责“怎么用”，Coding Plan 负责“调用谁、怎么计费”。

### 四、先订阅阿里云 Coding Plan

1. 登录阿里云百炼控制台，进入 Coding Plan 页面。
2. 根据你的使用强度选择 Lite 或 Pro。
3. 如果你是第一次用，先按最小成本试跑也可以，但要提前注意它有 5 小时、每周和每月三层额度限制。
4. 购买完成后，不要急着去 OpenClaw 里填普通百炼 key；先在 Coding Plan 页面获取套餐专属的 API Key 和 Base URL。

### 五、拿到正确的 API Key 和 Base URL

购买完成后，进入 Coding Plan 页面，拿到两样东西：

• Coding Plan 专属 API Key：格式通常为 sk-sp-xxxxx。

• 对应协议的 Base URL：如果工具走 OpenAI 兼容协议，就使用 https://coding.dashscope.aliyuncs.com/v1；如果工具走 Anthropic 兼容协议，就使用 https://coding.dashscope.aliyuncs.com/apps/anthropic。

OpenClaw 在阿里云帮助文档中的配置示例使用的是 OpenAI 兼容协议，所以本文也按这个路线来写。

### 六、安装 OpenClaw

OpenClaw 官方推荐的安装方式是安装脚本。它会处理 Node 检测、安装和 onboarding。

macOS / Linux：

Windows PowerShell：

如果你已经确认本机 Node.js 是 22+，也可以选择 npm 全局安装：

### 七、第一次安装时，向导怎么选

安装完成后，OpenClaw 通常会自动进入 onboarding。你也可以手动执行：

如果你跟着阿里云帮助文档走，下面这套选择最稳：

如果你执行新命令时出现 command not found: openclaw，也别慌。阿里云官方文档明确提到，OpenClaw 由 Moltbot/Clawdbot 更名而来，部分环境仍可能需要使用旧命令，例如 clawdbot dashboard 或 moltbot dashboard。

### 八、在 OpenClaw 中接入阿里云 Coding Plan

推荐先用 Web UI 的 RAW 配置方式。这样你能更直观地确认配置是否生效。

1. 在终端执行 openclaw dashboard。
2. 浏览器打开本地控制界面后，进入 Config / 配置 → RAW（有些阿里云文档写成 All Settings > RAW，本质都是编辑原始配置）。
3. 把下面这份“最小可用配置”写进去，或按同样结构 merge 到你现有配置里。
4. 把 YOUR_API_KEY 替换成你自己的 Coding Plan 专属 API Key。

### 九、已有配置怎么办：不要直接全量覆盖

如果你的 OpenClaw 之前已经接过钉钉、飞书、Telegram、Tailscale 或其他渠道，不建议直接把整份 JSON 全量替换掉。

• 保留原有 gateway、channels、tools、skills 等字段。

• 把 Coding Plan 相关内容局部补进 models.providers.bailian、agents.defaults.models、agents.defaults.model.primary 等位置。

• 如果你完全不确定怎么 merge，先备份 ~/.openclaw/openclaw.json，再改。

### 十、保存配置后，怎么验证是否成功

1. 在 Web UI 中保存并 Update，或在终端修改配置文件后重启网关。
2. 打开 dashboard，尝试发一条简单消息，例如：请介绍一下你自己，并告诉我当前使用的模型。
3. 如果能正常返回，说明模型接入基本没问题。
4. 再用 TUI 测试一次：执行 openclaw tui，然后在会话里输入 /model qwen3-max-2026-01-23 或 /model qwen3-coder-plus 切换模型。

如果 dashboard 是本机打开的 http://127.0.0.1:18789/，本地连接通常会自动配对通过；如果你是从远端设备或其他浏览器访问，OpenClaw 可能会要求一次 pairing 审批。

### 十一、最常见的 7 个问题

### 十二、进阶建议：跑通之后你再做这些

• 给 OpenClaw 增加更多模型：沿用同样的 JSON 结构，在 models.providers.bailian.models 里继续添加，并同步补充 agents.defaults.models。

• 把默认模型从 qwen3-coder-plus 切换为 qwen3-max-2026-01-23，适合更强推理类任务。

• 如果你确实需要远端访问 dashboard，优先考虑 HTTPS/Tailscale 等更安全的方式，而不是直接把不安全的 HTTP 暴露到公网。

• 如果你不希望本地长期运行此类高权限工具，可以考虑转向云服务器或阿里云官方解决方案，但那属于另一条运维路线，建议单独写成第二篇文章。

### 十三、你可以直接放到文章结尾的总结

## 附录 A：终端方式修改配置

如果你不想在 Web UI 中改 RAW，也可以直接编辑本地配置文件。默认路径通常是：

把前面的最小可用 JSON 粘进去，或者按同样结构 merge 到现有配置中。保存后再重启网关或重新打开 dashboard 进行验证。

## 附录 B：本文写作时采用的官方事实依据

信息校验日期：2026-03-08（UTC+8）。由于 OpenClaw 与阿里云百炼都在快速迭代，若你在更晚时间使用本教程，请优先以控制台与官方文档中的最新字段、模型列表与计费说明为准。



