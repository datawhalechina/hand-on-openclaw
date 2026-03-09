# Cherry Studio + Step 模型接入

## 前言

欢迎来到这份 **Cherry Studio + OpenClaw 快速上手教程**！ 如果你是 AI 新手，想用一个免费、强大、本地优先的工具把各种大模型、知识库、绘画、Agent 全部集成起来，这份教程就是为你准备的。Cherry Studio 是目前最受国人欢迎的国产开源 AI 桌面客户端（官网：https://www.cherry-ai.com），它把 DeepSeek、Claude、Gemini、Ollama 等 300+ 模型一键接入，还原生支持 OpenClaw（小龙虾）快速安装，让你几分钟内就能拥有一个“有灵魂”的持久 AI 伙伴——它会记住你是谁、怎么说话、有底线，还能定时干活、管日程、写代码。

本教程从零开始，手把手带你：下载 Cherry Studio → 配置免费阶跃模型（stepfun/step-3.5-flash:free）→ 一键安装 OpenClaw → 给小龙虾起名、注入灵魂（SOUL.md / IDENTITY.md / USER.md）。全程免费、无需复杂部署，适合零基础小白。跟着做，10–20 分钟就能让你的 AI 从“工具”变成“懂你的靠谱虾”🦞。走起！
## Cherry Studio 安装

https://www.cherry-ai.com/download

Cherry Studio是一款国产开源的多模型AI桌面客户端，被很多人称为“地表最好用的全能AI助手”之一。它把各种大模型、知识库、AI绘画、翻译、Agent、小程序等功能集成在一个软件里，隐私性强（支持纯本地使用），界面友好，非常适合国人使用。现已加入openclaw快速安装功能。

![img](../../img/tmp4-001.png)

下载好后选择任何人安装，下一步，需要权限点确定。

![img](../../img/tmp4-002.png)

然后选择一个安装位置，下一步。

![img](../../img/tmp4-003.png)

运行即可。

![img](../../img/tmp4-004.png)
## 配置 OpenRouter 免费 Step 模型

然后我们打开cherrystudio，进入右上角这个设置位置

![img](../../img/tmp4-005.png)

这里我们输入openrouter

![img](../../img/tmp4-006.png)

接着来到openrouter页面注册并登录账号：

https://openrouter.ai/

然后请创建一个apikey，请大家保存好~

![img](../../img/tmp4-007.png)

然后咱们来到charrystudio，先输入openrouter的密钥

![img](../../img/tmp4-008.png)

然后右边模型滑到最下，点击添加

![img](../../img/tmp4-009.png)

这里将这个免费模型名称粘贴进去：`stepfun/step-3.5-flash:free`

![img](../../img/tmp4-010.png)

接着来到首页，选择阶跃模型。

![img](../../img/tmp4-011.png)

测试一下，配置通过~

![img](../../img/tmp4-012.png)
## 在 Cherry Studio 中安装并启动 OpenClaw

大家点击上面加号找到openclaw虾虾

![img](../../img/tmp4-013.png)

点击安装openclaw即可

![img](../../img/tmp4-014.png)

有宝子反馈如果这样咋办，请把下面的node和git都装了然后再装openclaw

![img](../../img/tmp4-015.png)

这里等等就好了，这里我用了3-5分钟。

![img](../../img/tmp4-016.png)

装好后选择免费阶跃模型！启动！

![img](../../img/tmp4-017.png)

启动好嘞！测试一下！

![img](../../img/tmp4-018.png)

![img](../../img/tmp4-019.png)

测试了一下天气，还可以~

![img](../../img/tmp4-020.png)

## 获取 Step 3.5 Flash API Key

### 可以通过 [OpenRouter](https://openrouter.ai/settings/keys) 获取 Step 3.5 Flash API Key

打开OpenRouter官网，注册或登录账号

![img](../../img/tmp5-001.png)

创建并生成API Key

![img](../../img/tmp5-002.png)

在弹出的框里面输入名字（任意名字皆可），然后点击create创建。因为这个生成的是密钥，所以只会出现一次，需要复制到安全的地方保存好。

![img](../../img/tmp5-003.png)![img](../../img/tmp5-004.png)

### 可以通过 [阶跃星辰开放平台](https://platform.stepfun.com/) 获取 Step 3.5 Flash 的 API Key

打开阶跃开放平台，注册或登录账号

![img](../../img/tmp5-005.png)

创建并生成API Key

![img](../../img/tmp5-006.png)

生成好后可以找到对应的密钥并复制

![img](../../img/tmp5-007.png)

