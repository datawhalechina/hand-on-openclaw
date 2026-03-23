> 本教程遵循 CC 4.0 BY-NC-SA 协议。https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode

# 1. 引言

> 标签：`API配置：有` `环境：本地` `安全性：中` `IM接入：QQ / 飞书 / 企业微信 / 微信`

大家在看完我们分享的 Cherry Studio 接入 OpenClaw 后，已经简单体验了本地虾。下一步，很多人都想在飞书、QQ、企业微信、钉钉里面快速和虾玩耍。然而苦于虾的配置较难，新手无法在短时间搞定。我们找到了更方便的工具来辅助大家使用。这次我们也配齐了 OpenClaw 的十大使用场景和配置方法。让大家的虾变得更好用，那好我们开始吧~

# 2. ClawX

## 2.1 ClawX 介绍

![img](img/clawx-001.png)

在 AI 和效率工具领域，**ClawX** 是一款基于 "OpenClaw" 生态系统构建的开源桌面端 AI 应用程序。它解决了过去强大的 AI Agent（智能体）只能在复杂的命令行（终端）中运行的痛点，为普通用户提供了一个美观且极其易用的图形化界面。

**核心功能与特点：**

- **开箱即用的可视化界面**：基于 Electron 和 React 开发，软件内部直接嵌入了 OpenClaw 运行环境（Battery-included），用户无需懂代码，像安装普通软件一样一键即可配置好强大的 AI Agent。
- **7x24 小时全自动信息监控与抓取**：它不仅仅是一个“聊天对话框”，而是一个会在你电脑后台独立工作的“数据分析师”。它能开启独立的浏览器会话，自主登录金融终端、新闻网站或社交平台进行多源数据抓取和监控。
- **多渠道消息推送与自动汇报**：你可以让它全天候工作，当它发现重要公告或完成研究报告时，会通过 20 多种通讯工具（如 飞书、WhatsApp、Telegram、Slack、Discord、Email 等）自动将简报推送到你的手机上。
- **支持多模型与深度推理**：自带多步推理能力，不仅能看懂网页，还能交叉对比不同机构的 PDF 研报。支持接入几乎所有的主流大语言模型（如 OpenAI、Anthropic Claude、Google，以及国内的 Moonshot Kimi、Qwen 通义千问等）。
- **定时任务调度（Cron）**：你可以给它设定排班，比如：“每天早上 8 点自动浏览 10 个指定行业网站，并为我生成一份行业晨报推送至飞书”。

对于研究员、投资者或需要大量搜集、监控互联网信息的用户来说，ClawX 相当于一个免费的、永远在线的个人数字员工。

## 2.2 安装 ClawX

https://claw-x.com/

打开 ClawX 官网，然后下载即可~

![img](img/clawx-002.png)

![img](img/clawx-003.png)

如果打不开我这里预下载了win的版本和mac的版本。可以在下面下载也可以。

暂时无法在飞书文档外展示此内容

接下来我们打开安装文件，这里以Windows演示。

选择为所有用户安装。

![img](img/clawx-004.png)

提示：安装内容大概有1G，请保持网络畅通且稳定。笔记本最好用网线连接。 

![img](img/clawx-005.png)

安装好后请启动 ClawX。选择中文，点击下一步~

![img](img/clawx-006.png)

ClawX 会预带 OpenClaw，相当于离线下载了，非常美妙。检查好后点击下一步即可。这一步其实就已经启动 OpenClaw 了~

![img](img/clawx-007.png)

接下来请点击选择我们的老朋友 OpenRouter~

![img](img/clawx-008.png)

这里请跳到第三部分搞一个api。

这里搞到api以后按照操作进行配置。

接着我们输入模型：`stepfun/step-3.5-flash:free`

然后输入我们之前保存的密钥。点击验证并保存。

![img](img/clawx-009.png)

看到配置成功后进入下一步。

![img](img/clawx-010.png)

这里保证网络畅通，耐心等待即可。

![img](img/clawx-011.png)

看到下面这个界面就可以恭喜你，OpenClaw 配置成功啦。

![img](img/clawx-012.png)

测试一下这里能看到测试通过啦~

![img](img/clawx-013.png)

# 3. 大模型服务

## 3.1 OpenRouter（免费教程）

这里我们推荐大家到 OpenRouter 获取免费的国产模型，step-3.5 模型。

请大家先打开 OpenRouter 界面。

https://openrouter.ai/

然后请大家点击sign up我们开始注册账号。

![img](img/clawx-014.png)

这里输入邮箱和密码，如果出现后面这张图，需要点击验证你是人类hh

![img](img/clawx-015.png)![img](img/clawx-016.png)

出现如下这种情况，打开刚才邮箱账户里。

![img](img/clawx-017.png)

我们收到了一封来自 OpenRouter 的邮件，我们点击黑色这里。

![img](img/clawx-018.png)

回到 OpenRouter 的页面，我们发现进来了，这里需要选择你第一次了解 OpenRouter 的来源，随便选个 continue 即可。

![img](img/clawx-019.png)

好了，这时候我们去创建apikey。也就是使用大模型的钥匙。

![img](img/clawx-020.png)

点击create

![img](img/clawx-021.png)

然后咱们先输入一个名字，点击create即可。

![img](img/clawx-022.png)

需要大家点击右边这个复制，把密钥存好。建议你打开微信发到自己的个人助手或者存到一个私密电子笔记本里。

![img](img/clawx-023.png)

接下来请大家点击models然后输入free按下回车键，你可以看到当前免费的模型~点右边那个复制件就可以复制模型名称。

![img](img/clawx-024.png)

## 3.2 硅基流动（免费教程）

## 3.3 GLM（免费教程）

## 3.4 各大 Coding Plan 入口及用户评价

# 4. 飞书、QQ 接入 OpenClaw（IM 接入）

## 4.1 飞书接入

注册一个飞书账号。

https://www.feishu.cn/accounts/page/ug_register?redirect_uri=https%3A%2F%2Fwww.feishu.cn%2Fhc%2Fzh-CN%2Farticles%2F360045688853-%25E6%25B3%25A8%25E5%2586%258C%25E8%25B4%25A6%25E5%258F%25B7&app_id=11

![img](img/clawx-025.png)

接下来来到飞书开发者平台

https://open.feishu.cn/?lang=zh-CN

点击右上角登录一下~然后点入开发者后台（右上角）

![img](img/clawx-026.png)![img](img/clawx-027.png)

创建一个企业自建应用

![img](img/clawx-028.png)

![img](img/clawx-029.png)

接下来来到这个凭证与基础信息下的页面~

![img](img/clawx-030.png)

接下来点击添加应用能力，选择机器人下的添加。

![img](img/clawx-031.png)

接下来点击权限管理，点击批量导入，然后导入下面的配置代码，点击下一步~

![img](img/clawx-032.png)

```JSON
{
  "scopes": {
    "tenant": [
      "contact:contact.base:readonly",
      "docx:document:readonly",
      "im:chat:read",
      "im:chat:update",
      "im:message.group_at_msg:readonly",
      "im:message.p2p_msg:readonly",
      "im:message.pins:read",
      "im:message.pins:write_only",
      "im:message.reactions:read",
      "im:message.reactions:write_only",
      "im:message:readonly",
      "im:message:recall",
      "im:message:send_as_bot",
      "im:message:send_multi_users",
      "im:message:send_sys_msg",
      "im:message:update",
      "im:resource",
      "application:application:self_manage",
      "cardkit:card:write",
      "cardkit:card:read"
    ],
    "user": [
      "contact:user.employee_id:readonly",
      "offline_access","base:app:copy",
      "base:field:create",
      "base:field:delete",
      "base:field:read",
      "base:field:update",
      "base:record:create",
      "base:record:delete",
      "base:record:retrieve",
      "base:record:update",
      "base:table:create",
      "base:table:delete",
      "base:table:read",
      "base:table:update",
      "base:view:read",
      "base:view:write_only",
      "base:app:create",
      "base:app:update",
      "base:app:read",
      "sheets:spreadsheet.meta:read",
      "sheets:spreadsheet:read",
      "sheets:spreadsheet:create",
      "sheets:spreadsheet:write_only",
      "docs:document:export",
      "docs:document.media:upload",
      "board:whiteboard:node:create",
      "board:whiteboard:node:read",
      "calendar:calendar:read",
      "calendar:calendar.event:create",
      "calendar:calendar.event:delete",
      "calendar:calendar.event:read",
      "calendar:calendar.event:reply",
      "calendar:calendar.event:update",
      "calendar:calendar.free_busy:read",
      "contact:contact.base:readonly",
      "contact:user.base:readonly",
      "contact:user:search",
      "docs:document.comment:create",
      "docs:document.comment:read",
      "docs:document.comment:update",
      "docs:document.media:download",
      "docs:document:copy",
      "docx:document:create",
      "docx:document:readonly",
      "docx:document:write_only",
      "drive:drive.metadata:readonly",
      "drive:file:download",
      "drive:file:upload",
      "im:chat.members:read",
      "im:chat:read",
      "im:message",
      "im:message.group_msg:get_as_user",
      "im:message.p2p_msg:get_as_user",
      "im:message:readonly",
      "search:docs:read",
      "search:message",
      "space:document:delete",
      "space:document:move",
      "space:document:retrieve",
      "task:comment:read",
      "task:comment:write",
      "task:task:read",
      "task:task:write",
      "task:task:writeonly",
      "task:tasklist:read",
      "task:tasklist:write",
      "wiki:node:copy",
      "wiki:node:create",
      "wiki:node:move",
      "wiki:node:read",
      "wiki:node:retrieve",
      "wiki:space:read",
      "wiki:space:retrieve",
      "wiki:space:write_only"
    ]
  }
}
```

选择申请开通。

![img](img/clawx-033.png)

点击确认即可。

![img](img/clawx-034.png)

接下来打开 ClawX，选择频道，打开 Feishu，添加飞书的密钥。

![img](img/clawx-035.png)

配置方式如下图。

![img](img/clawx-036.png)

接下来来到事件与回调，咱们点击选择长链接方式。保存。

![img](img/clawx-037.png)

接下来在右下角点击添加事件，添加：`im.message.receive_v1`

![img](img/clawx-038.png)

接着在回调设置选择长连接保存一下。

![img](img/clawx-039.png)

接着我们点击上面的创建版本或者找到左边版本管理与发布，创建版本。

![img](img/clawx-040.png)

输入一些基本信息保存即可。然后点击发布。

![img](img/clawx-041.png)![img](img/clawx-042.png)

![img](img/clawx-043.png)

接下来我们看飞书中，收到一个应用消息，点击打开应用。

![img](img/clawx-044.png)

测试一下~成功~

![img](img/clawx-045.png)

## 4.2 QQ 接入

大家打开QQ bot平台，扫一下右下角这个二维码。（注意这里不是微信扫码，要用手机QQ扫码哦）

https://q.qq.com/qqbot/openclaw/login.html

![img](img/clawx-046.png)

然后点击阅读，点击同意即可跳转。

![img](img/clawx-047.png)

进来咱们点击创建机器人~

![img](img/clawx-048.png)

接着打开 ClawX，选择频道中的 QQbot

![img](img/clawx-049.png)

将 QQbot 的 AppID 和 AppSecret 复制到 ClawX 即可，点击保存连接~

![img](img/clawx-050.png)

配好后在QQbot上点击扫码聊天，扫码即可对话。

![img](img/clawx-051.png)

测试通过~

![img](img/clawx-052.png)

## 4.3 企业微信

首先要告知一下，需要把企业微信升级到5.0.2最新版本。还有咱们这里启动的是电脑端~

![img](img/clawx-053.png)

好！现在请启动企业微信。然后咱们打开工作台，选择智能机器人。

![img](img/clawx-054.png)

创建即可。

![img](img/clawx-055.png)

右边拉到最下面有一个api配置，选择这个。

![img](img/clawx-056.png)

选择长链接模式，点击获取密钥~

![img](img/clawx-057.png)

下面这个云文档也可以授权一下。

![img](img/clawx-058.png)

接下来来到 ClawX，我们选择频道下的 WeCom。

![img](img/clawx-059.png)

接下来打开企业微信，把ID和密钥贴过来即可。

![img](img/clawx-060.png)

对企业微信机器人点击保存。

![img](img/clawx-061.png)

## 4.4 个人微信
这里大家首先需要拿到微信的灰度资格，现在android和ios都放开的。

如何判断拿到资格了呢？

打开手机微信->到“我”页面->设置->插件。如果如下图说明有资格，否则还没有灰度到。

![img](img/clawx-wechat-001.png)

拿到资格后我们开始连接。

将clawx更新到V0.2.9以上。我们找到频道，wechat。

![img](img/clawx-wechat-002.png)

![img](img/clawx-wechat-003.png)![img](img/clawx-wechat-004.png)

生成二维码后拿有资格的手机微信扫码，成功后右下角出现提示。

![img](img/clawx-wechat-005.png)

等clawx更新后手机微信找到“微信ClawBot”。对话即可。

![img](img/clawx-wechat-006.png)![img](img/clawx-wechat-007.png)
