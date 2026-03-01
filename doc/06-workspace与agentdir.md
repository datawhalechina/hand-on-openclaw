# 6. Workspace 与 AgentDir 的奥秘

在 OpenClaw 的世界里，构建一个 AI Agent（智能体）不仅仅是调用一个模型，而是为一个数字生命构建它的“办公室”和“记忆宫殿”。理解 **Workspace** 和 **AgentDir**，就是理解 OpenClaw 如何让 AI 拥有个性、技能和边界的关键。

## 6.1 双核心结构：大脑与躯体

### 1. Workspace（工作空间）：Agent 的“办公室”

Workspace 是 Agent 的**工作目录**。你可以把它想象成一个实体办公室，里面放着它的参考资料、项目文件和“行为准则”。

- **作用**：存放 Agent 执行任务所需的本地文件、代码、文档以及核心的配置文件（如 `.md` 文件）。
- **价值**：它定义了 Agent **“是谁”** 以及 **“如何做事”**。通过修改 Workspace 里的文件，你可以直接改变 Agent 的性格和处理问题的逻辑。

### 2. AgentDir（状态目录）：Agent 的“储物间”

AgentDir 是存放 **运行状态** 的地方（通常位于 `~/.openclaw/agents/<agentId>/agent`）。

- **作用**：存储登录凭证（如 WhatsApp/Discord 的 Session）、模型配置、授权文件（auth-profiles.json）等。
- **价值**：它确保了 Agent 的**物理隔离**。如果你有两个 Agent，它们必须有不同的 AgentDir，否则它们的账号登录信息会冲突，就像两个灵魂抢夺同一个身体。

## 6.2  拟人化理解：Workspace 中的8个md 

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=YTgyN2FlYjA0MmQ5NDMyYmE5OTQwYzllMDliNzcwYWRfVFIycjNFVENLZElqR3MyUHRnUFFVZnRpczZPNzZRSUVfVG9rZW46R3BvdmJIaFB5b0NoMlF4S096bmNrM2ZpbklkXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

【这个图画的太好了哈哈~】

在 Workspace 中，有八个关键的 Markdown 文件，它们被 OpenClaw 自动注入到 System Prompt（系统提示词）中。我们可以用拟人化的比喻来理解它们：

文件名拟人化角色价值与代表意义SOUL.md灵魂与三观核心价值观。 它决定了 Agent 的底色（是毒舌、温柔还是专业冷淡）。它不教做事，只教“做人”。AGENTS.md组织架构图社交边界。 记录了当前环境中还有哪些其他 Agent 存在，以及如何与它们协作或求助。IDENTITY.md身份证基本信息。 包含 Agent 的名字、职衔、所属部门。它让 Agent 知道“我是谁”。USER.md老板的喜好用户画像。 记录了你（用户）的偏好。比如：“老板不喜欢废话”、“老板习惯用繁体中文”。TOOLS.md工具操作手册技能说明书。 详细描述了 Agent 手头有哪些特殊工具以及如何正确、安全地使用它们。MEMORY.md长期日记本核心记忆。 记录了最重要的历史事件、学到的长期知识或未完成的重大任务。BOOTSTRAP.md入职培训手册初始引导。 仅在 Agent 第一次“出生”时使用，告诉它第一步该干什么，随后通常会被遗忘或归档。HEARTBEAT.md生理脉搏状态感知。 规定了 Agent 在闲置或定时检查时该如何“自省”或主动触发动作。

## 6.3 如何通过 Workspace 塑造你的 Agent

### 第一步：打开WebUI

也就是打开我们最开始的那个URL（网址：http://127.0.0.1:18789/agents）

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=NjAxOGEzMWRkMDExYjA0NDQ0YzMzZmJmM2NiY2Y4YmVfbmZjV2pGTGc5MnFMeXl4MDU2MlpReUhBcjhHeGFDNkZfVG9rZW46VURqMWJDQm1tb1hlTXJ4dzlMRGNGa3pGbjNiXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

### 第二步：注入“灵魂” (编辑 SOUL.md)

打开 `workspace/SOUL.md`，写入：

> “你是一个极其严谨的资深架构师，对代码洁癖有执念。在回复时，先指出代码中的潜在风险，再给出优化方案。”

填写好后点击save，这里只是简单的举例。详细学习请到：

https://docs.openclaw.ai/reference/AGENTS.default

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=NzkxOTFhMGRlNzE2ZmQ4N2JhY2IwOTYzNzRlYjAwNjdfbzFoRGY2MFNsU0tobjh4ZjdSM0RPYmFtakl3Q243OHhfVG9rZW46WlFuTGIzbk1lb1JIN1R4UjRINWNhT1hjbnJiXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

### 第三步：理解注入机制 (System Prompt Injection)

**核心原理**：OpenClaw 并不是让 Agent 自己去“读”这些文件，而是在每一轮对话前，**自动把这些文件的内容拼接到系统提示词的最前面**。

- **注意**：这些文件总字数有限制（默认 15 万字符）。如果 `MEMORY.md` 写得太长，会消耗大量 Token 甚至导致截断。保持简洁是高级玩家的修养。

## 6.4 为什么要这么设计？

1. **解耦**：模型可以换（从 Claude 换到 GPT），但 Workspace 里的“灵魂”和“记忆”是持久的。
2. **可移植性**：你可以把整个 Workspace 文件夹打包发给朋友，他加载后就能得到一个和你一模一样性格和知识储备的 Agent。
3. **多 Agent 协作**：通过 `AGENTS.md` 建立的索引，多个 Agent 可以在同一个 Gateway 下各司其职，不会产生认知混淆。

现在，去你的 `~/.openclaw/workspace` 目录下，试着为你的 Agent 撰写第一份 **SOUL.md** 吧！
