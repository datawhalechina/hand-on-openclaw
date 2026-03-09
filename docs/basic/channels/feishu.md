# 飞书渠道接入

飞书的创建登录在这里：

https://www.feishu.cn/accounts/

这里需要大家创建一个组织账号，不要创建个人号【注意注意注意！！！】。只有组织账号才能邀请好友一起来玩！

![img](../../img/4-1.png)

接着打开飞书开发者平台：

https://open.feishu.cn/?lang=zh-CN

选择开发者后台，点击企业建应用。

![img](../../img/4-2.png)![img](../../img/4-3.png)

名称随便写写就好

![img](../../img/4-4.png)

接着在成员管理点击添加机器人

![img](../../img/4-5.png)

然后我们来到权限管理，点击开通权限。

![img](../../img/4-6.png)

输入im: 然后点击右下角开通权限。

![img](../../img/4-7.png)

然后输入：contact:user.base:readonly

![img](../../img/4-8.png)

开通完后如果你想使用文档功能，就输入docs:

![img](../../img/4-9.png)

接着来到凭证与基础信息，复制`App ID与App Secret` 对应的内容。

![img](../../img/4-10.png)

然后返回到刚才的内容填写 id 和 secret，下面有个选项选 china 版本即可。

![img](../../img/4-11.png)

下面的skill你可以选，用空格选择回车确认即可。其他的可以no如果你没有api的话。

![img](../../img/4-12.png)

接下来你可以看到在control UI地方有一个地址，你可以按下ctrl点击鼠标左键或者直接复制进入一个页面。这个就是openclaw的在线页面。

![img](../../img/4-13.png)

这里我们对话测试没有问题，说明api配置无误。

![img](../../img/4-14.png)

如果测试通过选择do this later退出即可。现在我们返回飞书开发者平台。我们需要找到时间与回调里面的订阅方式，选择长链接并保存。

![img](../../img/4-15.png)

如果没有报错说明你的配置无误，飞书和openclaw配置都没问题。然后看右下角有个添加事件，把消息与群组全部勾选，确认添加。

![img](../../img/4-16.png)

然后到回调配置里，也打开长连接即可。

![img](../../img/4-17.png)

最后最关键的一步来了！我们需要把所有配置落地，需要点击一下创建版本。

![img](../../img/4-18.png)

简单填写版本信息，然后保存即可~

![img](../../img/4-19.png)![img](../../img/4-20.png)

发布成功后飞书会收到申请。请大家将组织账号登录在飞书，然后打开。飞书会告诉你审批通过，这里你点击打开应用。

![img](../../img/4-21.png)

这里我们发送你好，机器人做了配对申请。你需要将最后这句复制并发送给刚才浏览器的机器人。

![img](../../img/4-22.png)

就像我这样复制进去就好啦。

![img](../../img/4-23.png)

再次回到飞书，这里大家可以看到飞书已经配好啦~~开心

![img](../../img/4-24.png)

## 飞书配好不回复消息怎么办

如果机器人可见但不回复，可以按下面步骤排查：

1. 安装飞书官方插件

```Plain
npx -y https://sf3-cn.feishucdn.com/obj/open-platform-opendoc/879b06f872058309ef70f49bcd38a71f_Pr8pNIJ9J9.tgz install
```

2. 选择已有机器人，网页确认后重启网关

```Plain
openclaw gateway restart
```

<!-- TMP10_FEISHU_KIMI_START -->
## 引言

![img](../../img/tmp10-001.png)

OpenClaw官网：https://openclaw.ai/

> 本次案例的模型使用**国产Kimi模型**，性价比较高，能满足日常需求。分为Kimi Claw和本地配置OpenClaw两种方法，难度**由易到难**，选择合适的方法配置即可。

## 飞书接入自动机器人的方法

![img](../../img/tmp10-002.png)

## 为什么很多人买 Mac mini 来跑 OpenClaw

1. 新电脑上面没有被误删、瞎搞的风险，搞坏了也不怕
2. Mac mini不像笔记本关机就关机了，它可以一直执行，24/7干活
3. 数据隐私性的问题。

## 为什么推荐云上部署

1. 24/7干活，不会关了电脑就不干活了
2. 和本地的文件有隔离，误删的风险性小一点
3. 不买重资产Mac Mini。
4. 但是由于读不了本地文件，所以感觉上会像一个云端的Manus，不像“贴身助理”一样特别懂我们的方方面面

## 核心原理：你的 OpenClaw 助理是怎么工作的

![img](../../img/tmp10-003.png)

在开始动手之前，我们先用一个简单的比喻，让你秒懂 OpenClaw（也就是我们的“龙虾”助理）到底是怎么工作的。把它想象成一个超级智能的“外包团队”：

1. **大模型 (Kimi/Claude等) - 超级大脑 🧠:**

这就是团队里的“超级专家”，它知识渊博，能思考、会聊天、能写文章。你问的所有问题，最终都是由它来思考和回答的。它很聪明，但它自己不会“动手”干活。

1. **OpenClaw (龙虾) - 项目经理 & 工具箱 🛠️:**

OpenClaw 就是你的“项目经理”。它不直接“思考”，但它特别会“管理”和“执行”。它连接着“超级大脑”（Kimi），并拿着一个装满了各种工具（比如上网搜索、读写文件、调用飞书API等）的“工具箱”。

当你通过飞书给它下达一个指令，比如“帮我查一下今天的天气”，项目经理（OpenClaw）就会理解你的需求，然后从工具箱里拿出“上网搜索”这个工具，去网上查天气，再把查到的结果交给“超级大脑”（Kimi）进行总结，最后把Kimi总结好的答案发回给你。

1. **飞书 (或其他聊天软件) - 你的办公室 🏢:**

飞书就是你和你的“项目经理”沟通的办公室。你在这里下达指令，也在这里接收成果。

1. **网关 (Gateway) - 安全门卫 & 翻译官 🚪:**

你的“项目经理”（OpenClaw）是在你自己的电脑或服务器上工作的，相当于在“内部办公室”。而飞书是在互联网上的，是“外部世界”。

 “网关”就像一个既懂“内部行话”又懂“外部语言”的“安全门卫”和“翻译官”。它负责把飞书传来的消息（外部语言）安全地、准确地翻译给你的项目经理（内部行话），再把项目经理处理完的结果翻译回去，发到飞书上。没有它，你的内部助理就没法和外部世界安全地沟通。

**总结一下流程就是：**

你 (在飞书里) ➔ 网关 (安全门卫) ➔ OpenClaw (项目经理) ➔ [调用工具箱] ➔ Kimi (超级大脑) ➔ OpenClaw (项目经理) ➔ 网关 (安全门卫) ➔ 你 (在飞书里收到回复)

理解了这个流程，后面的一系列配置步骤，比如设置ID和密码、配置事件回调、启动网关等，你就会明白它们分别是在为哪个环节“授权”和“铺路”了。是不是一下就清晰多啦？

## Kimi Claw 一步到位（推荐）

点击进入Kimi官网，可以看到Kimi的人员已经开发出极简的配置方法“**Kimi Claw**”，实测确实用时10min，适合零基础小白，把配置龙虾🦞的门槛降到最低。

![img](../../img/tmp10-004.png)

Kimi官网：https://www.kimi.com/

配完KimiClaw发现Minimax也出了极简的配置Openclaw功能，价格也更实惠，也可以试试MaxClaw（流程都类似）

![img](../../img/tmp10-005.png)

Minimax Agent官网：https://agent.minimaxi.com/

### 充值会员

点击订阅“Allegretto”会员计划，一个月199元相较于claude等模型（200美金）性价比高很多，且效果也能达到预期。

![img](../../img/tmp10-006.png)

### 简单开始试试对话

简单试试它，内置K2.5模型，并且Kimi团队的人员直接把飞书配置、新闻搜集等常见的需求列到开始，真小白化配置。

![img](../../img/tmp10-007.png)

### 设置定时任务

这边设置一个定时任务，它明天会在此页面上通知我。**但是我想在飞书里面接收到消息该怎么办？**那就需要和飞书绑定，将这个Kimi Claw配置到飞书里面。

![img](../../img/tmp10-008.png)

### 问Kimi如何配置到飞书

**不会配置飞书怎么办？****直接问Kimi吧**

毕竟是Kimi Claw，肯定懂这方面的，毕竟龙虾也是近期热点，不会不应该的！

![img](../../img/tmp10-009.png)

按照它说的一步步来：

> 小Tips：在提示词里面加入“我是小白，请一步步给我说”等话语，可以显著降低我们的对话过程难度。

![img](../../img/tmp10-010.png)

### 打开[飞书开发者后台](https://open.feishu.cn/)

- 完全无脑跟随着Kimi给的步骤来实现它。

![img](../../img/tmp10-011.png)

- 点击 `创建企业自建应用`。

![img](../../img/tmp10-012.png)

- 然后随便取个好听的名字

![img](../../img/tmp10-013.png)

- 复制飞书应用的ID和密码

这里可以看到该机器人有了特定的ID和密码，相当于这个机器人有了身份证，能够“合法”进入，有了权限了。

![img](../../img/tmp10-014.png)

### 把飞书的应用ID和密码发送给Kimi Claw

⚠️这一步记得要保护好隐私，不要轻易的把密码发给其他人。

![img](../../img/tmp10-015.png)

- 有时候问它半天不动，可以重启一下实例

![img](../../img/tmp10-016.png)

### 飞书后台设置机器人事件与回调

- 点击`添加应用能力`，添加`机器人`，然后命名。

![img](../../img/tmp10-017.png)

- 设置**事件配置**和**回调配置**里的`长链接`，然后保存

![img](../../img/tmp10-018.png)

![img](../../img/tmp10-019.png)

![img](../../img/tmp10-020.png)

> **小白话解释：什么是“事件”与“回调”？**
>
> **事件 (Event)**：这就像是各种各样的“杂志”。比如，飞书里发生了“有人@你”、“有人给你发私信”、“有新成员加入群聊”等等，这些都是一本本不同主题的“杂志”。
>
> **回调配置 (Callback)**：这相当于你的“收件地址”。你把这个地址告诉飞书，就是告诉它：“嘿，以后上面那些‘杂志’只要一有新刊，就立刻给我寄到这个地址来！”
>
> **添加事件**：这个操作，就是“订阅杂志”的过程。你勾选了哪些事件，就等于你订阅了哪些杂志。这样，你的“龙虾”助理（OpenClaw）就能在第一时间知道飞书里发生的、跟它有关的各种事情，然后才能做出反应。比如，只有订阅了“接收到消息”这本杂志，当你在群里@它时，它才能“看到”并回复你。

点击`添加事件`，找到`消息与群组`，把自己认为需要的都勾选上。

![img](../../img/tmp10-021.png)

![img](../../img/tmp10-022.png)

- 添加后，可以看到已开通好。

![img](../../img/tmp10-023.png)

### 批量导入权限

- 这个功能就不用一个个勾选了，可以一次性导入相关的权限。

![img](../../img/tmp10-024.png)

- 复制以下的json代码：

```JSON
{
  "scopes":{
    "tenant":[
      "aily:file:read",
      "aily:file:write",
      "application:application.app_message_stats.overview:readonly",
      "application:application:self_manage",
      "application:bot.menu:write",
      "cardkit:card:write",
      "contact:user.employee_id:readonly",
      "corehr:file:download",
      "docs:document.content:read",
      "event:ip_list",
      "im:chat",
      "im:chat.access_event.bot_p2p_chat:read",
      "im:chat.members:bot_access",
      "im:message",
      "im:message.group_at_msg:readonly",
      "im:message.group_msg",
      "im:message.p2p_msg:readonly",
      "im:message:readonly",
      "im:message:send_as_bot",
      "im:resource",
      "sheets:spreadsheet",
      "wiki:wiki:readonly"
    ],
    "user":[
      "aily:file:read",
      "aily:file:write",
      "im:chat.access_event.bot_p2p_chat:read"
    ]
}
}
```

- 覆盖复制到这里，然后点击`确认`。

![img](../../img/tmp10-025.png)

### 发布KimiClaw机器人

![img](../../img/tmp10-026.png)

### 回到飞书，配置完成

发布后，飞书会收到通知，开启它。尝试说个“你好”，它就是你的个人专属助理。

![img](../../img/tmp10-027.png)

![img](../../img/tmp10-028.png)

完成，丝滑配置，整个过程10min左右，开心了~🌈

### 加入联网功能

申请一个API Key发给龙虾即可。

https://app.tavily.com/home

介于需要本地部署，经常的操作是使用Mac电脑来配置，稳定性效果比较好，且网上有很多的教程。Wins有时候不太稳定，因此操作起来稍微难一点，需要安装WLS虚拟机（也就是在你现有的Wins系统下另外开辟一个Linux系统，用Linux系统配置Openclaw会减少很多奇奇怪怪的报错）

### 接入飞书

接下来，我们再开始接入飞书，打开[飞书开发者后台](https://open.feishu.cn/app)，点击“创建应用”

![img](../../img/tmp10-050.png)

起个好听的名字

![img](../../img/tmp10-051.png)

可以看到机器人的ID信息和密钥了（保存好），相当于这个机器人有了身份证，能够“合法”进入，有了权限了。

![img](../../img/tmp10-052.png)

添加机器人

![img](../../img/tmp10-053.png)

### 批量配置飞书权限

![img](../../img/tmp10-054.png)

复制以下的json代码：

```JSON
{
  "scopes":{
    "tenant":[
      "aily:file:read",
      "aily:file:write",
      "application:application.app_message_stats.overview:readonly",
      "application:application:self_manage",
      "application:bot.menu:write",
      "cardkit:card:write",
      "contact:user.employee_id:readonly",
      "corehr:file:download",
      "docs:document.content:read",
      "event:ip_list",
      "im:chat",
      "im:chat.access_event.bot_p2p_chat:read",
      "im:chat.members:bot_access",
      "im:message",
      "im:message.group_at_msg:readonly",
      "im:message.group_msg",
      "im:message.p2p_msg:readonly",
      "im:message:readonly",
      "im:message:send_as_bot",
      "im:resource",
      "sheets:spreadsheet",
      "wiki:wiki:readonly"
    ],
    "user":[
      "aily:file:read",
      "aily:file:write",
      "im:chat.access_event.bot_p2p_chat:read"
    ]
}
}
```

- 覆盖复制到这里，然后点击`确认`。

![img](../../img/tmp10-055.png)

可以看到已经开通了很多权限，这样openclaw就可以在有限范围内畅通无阻（当然，双刃剑就是权限比较高）

![img](../../img/tmp10-056.png)

保存一下名字

![img](../../img/tmp10-057.png)

### 发布OpenClaw机器人

![img](../../img/tmp10-058.png)

填写版本号，每次都可以更新，比如增加一个权限或者减少一个权限，然后发布版本号选择递进即可。

![img](../../img/tmp10-059.png)

点击 `保存`，发布。立马就能收到飞书的消息提醒，我们打开看看。

![img](../../img/tmp10-060.png)

### 在Openclaw导入飞书的依赖

然后开始在虚拟机命令行配置飞书：

按 `Ctrl+C` 键清除上一个对话，然后输入：

（这样就是一键导入飞书的所需要的包，丝滑）

```Markdown
openclaw plugins install @openclaw/feishu
```

![img](../../img/tmp10-061.png)

![img](../../img/tmp10-062.png)

**小白话解释：`openclaw plugins install @openclaw/feishu` 是什么？**

> 这就像是“给你的项目经理报一个培训班”。
>
> - `plugins install` 的意思是“安装插件”。插件就像是额外的“技能包”或者“学习资料”。
> - `@openclaw/feishu` 就是这门课的名字，叫做《Openclaw飞书沟通技巧与实践》。

所以，这行命令的意思是：**“嘿，我的龙虾助理，为了让你能和飞书部门无障碍沟通，我给你报了个‘飞书’培训班，快去学！”** 安装成功后，它就掌握了所有和飞书打交道的“行话”和“规矩”，知道该如何收发消息、如何识别不同的指令了。

### OpenClaw添加飞书渠道

复制以下的代码，导入飞书渠道选项。并且选择`yes`。

```Markdown
openclaw channels add
```

![img](../../img/tmp10-063.png)

刚刚我们没添加飞书，等着跑通最小MVP后，测试没问题后再添加飞书。现在测试没问题了，现在添加飞书。

![img](../../img/tmp10-064.png)

输入飞书的应用ID和密码

![img](../../img/tmp10-065.png)

- 输入飞书的应用ID和密钥

![img](../../img/tmp10-066.png)

国内选择`飞书`

![img](../../img/tmp10-067.png)

选择“可允许加入群聊”

![img](../../img/tmp10-068.png)

然后系统会再出现一次，这次选择`Finished`即可

![img](../../img/tmp10-069.png)

选择`No`

![img](../../img/tmp10-070.png)

看到这里，飞书已经配置好了。

![img](../../img/tmp10-071.png)

### 启动网关

```Markdown
openclaw gateway start
```

### 回到飞书后台设置事件与回调配置

![img](../../img/tmp10-072.png)

![img](../../img/tmp10-073.png)

添加事件：

![img](../../img/tmp10-074.png)

选择`消息与群组`，可以**都选上**。(反正无害)

![img](../../img/tmp10-075.png)

![img](../../img/tmp10-076.png)

### 发布飞书机器人

![img](../../img/tmp10-077.png)

![img](../../img/tmp10-078.png)

![img](../../img/tmp10-079.png)

### 获取Openclaw的批准和配对

回到飞书里面，来沟通。先发送“你好”，然后复制底下的文字到Openclaw里面

![img](../../img/tmp10-080.png)

再到Openclaw里面，发最底下的一串码（记得别超时，要迅速发）。

![img](../../img/tmp10-081.png)

### Openclaw完成批准

（否则就和我一样，需要它手动批准）

![img](../../img/tmp10-082.png)

批准成功了！

### 回到飞书，配置完成

然后回到飞书，终于成功了！！！！

![img](../../img/tmp10-083.png)

![img](../../img/tmp10-084.png)

🌈

## 参考教程链接

[我用openclaw建了一个私人飞书agents群组](https://ccnpfm0xlkhu.feishu.cn/wiki/TIjewM2a4i1ti8krAa9cKKtxnzf?from=from_copylink)
<!-- TMP10_FEISHU_KIMI_END -->



