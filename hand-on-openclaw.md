# hand-on-openclaw

# 1. 介绍

本次我会带大家手把手入门openclaw，并在自己windows下配置openclaw接入飞书群聊，建立一个openclaw agents小群组。然后给openclaw的ai bot增加一些好用的skills。

废话不多说，我们现在开始！

# 2. 环境准备

## 2.1 windows WSL配置

详细内容大家可以看下面这一篇，我简单把关键步骤给大家截图出来。

https://learn.microsoft.com/zh-cn/windows/wsl/install

首先打开cmd，可能有很多新手不知道CMD是什么，就是按一下windows键，然后输入CMD出来的这个命令提示符。这个是可以直接调用windows命令的界面。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=NzRlYmQ5ZDJkNmM4OTYzZmRiY2VjZTMzOGM4MjJmY2FfR1V0Uk9KdFRtSklOdG5jWGZvSWJVS05UVElDd3JvYUtfVG9rZW46VjF4VGIzTTkxbzBxNXN4Q24zMGM4c1o5bjliXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

接下来我们输入`wsl --install`进行安装，这里windows就会自动帮我们安装WSL。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=MGNjZDhmM2I1ZWUzOTMxMzRlZjM3MDJjZTY1ZTA4ZDlfN05DUFFNVUF5U1hPcTZFTmFESVpRem9abjY4TEZabWhfVG9rZW46VXh2U2I4MExob1Nza2V4YzFUQ2NHZVk1bmZkXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

## 2.2 wsl ubuntu安装

接下来我们需要打开windows商店，大家可以在windows键按下后输入商店就能找到这个应用，然后我们再输入ubuntu。找到24.04也可以，其他的版本也可以，大家安装一个就好。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=M2E4MWU5MjU5NDVkNWJjODVhYTliYWZmNmZjMWRkZTVfamxnRjN0MWdPc3NUUTNvMGlrUnlseEc0TmtobUpjc1JfVG9rZW46R3NGamJmWlJnbzQwOGt4aWJjNGNMTGRKbmlkXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

这里点击免费下载后配置即可。初始化配置的时候需要输入用户名密码，大家把密码记住，后面每次用ubntu系统的时候就需要去输入密码。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ZjdkZmVkZTVmMjVkMzEzYWIxNGVlYTVmMzBlNmVkNmFfSm5KSUlZdUNLbWhKTUhsWldKc0hQdlVwaUtUdWlXZ3FfVG9rZW46Q1NzQWJOTXhIb2hLQ3Z4cWpaVGNDUWxFbnNjXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

可能大家到这里还不知道大家在做什么。其实我们现在给windows电脑配置了一个linux的子系统。然后我们通过这个子系统就可以去使用linux的一些工具和服务。这样子相比于直接使用windows来说，稳定性和安全性更高一些。也就是说我们把openclaw（龙虾）装到这里，我们不怕它扰乱我们正常windows电脑的环境。它把子系统搞崩了也无所谓。我们这里面只需要把子系统卸载删除就行。这样子的话，大家就不用太担心安装openclaw（龙虾）后会导致你的电脑不能用，或者是害怕它删除一些你电脑里面的东西。

## 2.3 openclaw的安装

这里面我们在win按下windows键后输入ubuntu，然后我们打开ubuntu的界面，这样子我们可以在子系统里进行一系列的使用和操作。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=M2JhZWI4NWIzNDUxN2FmOWY4ZjRjNWJhNzYyOTlmMzBfMU9keEx1eW5FeVBpbkRURGdDSGZxTTUzZU1iMENVZDhfVG9rZW46RE9DYWIzRkJBb1ZsSDJ4Mzc4M2NLSlhhbktoXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

接着我们输入下面这一句。

```Plain
curl -fsSL https://openclaw.ai/install.sh | bash
```

这样我们就不需要手动的去安装note JS和其他的依赖环境。1个SH命令就能全部搞定相关依赖的下载和安装。可以说这个方法是非常偷懒了：D。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ZjI0ODgyOTgzMGYzNzFhYjAwODY0MGZmODE5YjdjNjNfcGF6ejE1MGVVNmJtVDE4M0IzdTFwUk94allzSEVKWnlfVG9rZW46UXNtc2JsdXdlb0oxUGF4VDBkb2NldFp6bkNjXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

装好进入配置页面~~在这边大家可以抽空去自己的code plan，把对应的API key拿过来。比如说我这里面就用的minimax的2.5的，然后我就去minimax2.5这边把API key拿过来。我个人用下来minimax还是比较流畅的~

如果你只想试着玩，可以先买一点token先不买plan。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=YzgzNjBlNGNmOGY2MWJjNGNkMjdjMTFlNjA0MDRmMDdfTWtjbTRpRTNTMVV3TmttOEt3NHVSRW80OGZtR0VJS2FfVG9rZW46Uk0wQmJ3RjZBb0lEaVl4NFRGWGNTUFVJblRwXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ZGI4ZGNiMzRiZTZmMzBlM2Y4MjM3NWMyY2Q4OTBkMTJfbVpmTU1rS2JnSHExaVdwQ1RmU21TVUg0T0NKdW02dTVfVG9rZW46SGl3UWJBZTlFb1RLbTl4b1BNN2NBQ25WbjhkXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=YmIzZWE3OTgxNjZmZjQ5MTAxODkxMDAzYjdmNjdjNGFfS0dwSE9iSXNSanp0WklGUENtWmx3RzlWaEpUZlh2NEFfVG9rZW46THV1Z2JteTFrbzJSMkF4UHN2cWNmd0NGbmNiXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=YjlkMDNlN2I1YWQxNjM4NTIwYjVlMzIzOTMzYjIwNzlfVzI3U2lqbzhsV1AyTTJRNlF4YUNTNUpIMVVnNHFoSE9fVG9rZW46UWNsOWJmQWo0b1Vvd0p4dWNEcGN6TG5lbmJnXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=OGVkOTQ5NTc4MmNlMzQ2ZTMwNzhmY2VkNjM4NjI4MmZfMFNlOGQxNnR3bGxxdnN4T21HSFJGeGV0RlZWSlF6NGFfVG9rZW46VE5vYmJQRjdQb2t0OHF4Y01VUGNOZ0lHblVoXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=MTI4YWY5ZmJlODZkMmRlZGU5NWFhOWJlODdkYjZmZDFfRERvc1VmV2sxU1dLSU1KTzJVWURSVjZDeEJ1MEIzaDBfVG9rZW46QktXY2JsQUZUbzJpeDJ4cmFOemMxVGJZblA1XzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

# 3. openclaw配置

这里面我们需要先打开onboard，然后我们配置模型，先让open claw可以完成我们的基本对话。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ZTkyNWRjMWQ2ZmFkNGIwZDgwNmZlYjc2YmFiNTVhYjVfdFMwSklpYmFSaVBlNmo3Mk1peklwSzNFakhWWXNjbm1fVG9rZW46TTNvQWIwaFU5b1FSY0x4b3pDbGN0STM5bjNlXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

这里大家跟着我的选择就好~

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=OTM0Y2Q2OTVkZmE5NGQ2ZGQ1ZmQyN2Q5Mjk3N2E5MmNfd0l4NXZmRkJXUEUyN2p1OVBlREhtNmsyTWNYRWw5UmpfVG9rZW46QjlEMGJ0YThMb09vaWJ4SVBRaWNtZlpYbnpiXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

到这里我们就需要把2.3等待时找到的apikey导入就好~

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ZmJhYmZlNDkyYzg0OWQ1Y2ZlNWJhZWM2Njc4ZmQ3OTZfWTAxZlhockhJTGlBQVB3YVNrdm05U3FFTkx5NVJnQ3FfVG9rZW46SmRPU2JlU1JRb0Y0Sk54QzFJdWNHVFJLbjJiXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

配好key后我们选择飞书

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=NzUzMzI1MmI2MWM4NTczZjQ3ZThiZGY3YTA2OTgwZTFfelNad0VuWWZmZmtFekxWYlZVR2duU0RVR3ZPU3pRd2xfVG9rZW46UHVIbmJ0VkZqb0RsY214RzZ6NmM2ZHhtbkdjXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ZGRmNTZmOGQ1OTJhY2IxOTdiYjFiYzI4N2MzYjFlZDVfNnF3VXA5RmtrbWxjOGpqOEYwM0c1MXBjWVJBUUZkUk1fVG9rZW46T2N4c2JaOFpob3dRY254N3JiemMwUWFibkZkXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

到这里就需要切换到飞书的配置了

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=YWVmYTIyZDI0MWE4NDc3MzJhNDkwZmFhNWE2ZDhkNmNfZmhlbVFpSVVMak5IM0FJU1lYOFR4ZVlabkQzd0xUdVJfVG9rZW46THNiSWJTTDBHbzQ2UTV4Z2dNdGNITndCbjJlXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

## 如何更新？

在ubuntu输入下面命令即可~

```Plain
openclaw update
```

ok搞定~

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ZWY2NmY4ZjhhZDBiODQwMGM2YzBmNzgxMWY2MjAxNjJfODJDd3Jha1JOZTN6SnRtSkpBeGl1SDkxU0xmVE50RHpfVG9rZW46QW1JR2JMWGhub2o1eFB4RThNbWMycjN0bmhMXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

# 4. 飞书配置

飞书的创建登录在这里：

https://www.feishu.cn/accounts/

这里需要大家创建一个组织账号，不要创建个人号【注意注意注意！！！】。只有组织账号才能邀请好友一起来玩！

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=MTg4YzY5ODllODgyN2YyNTE4ODA1MTM5MGViM2M1NDlfMlh4dHpvQ1g0RG85c0tKdm9paEk0Y1B0dnVUMTlhMFVfVG9rZW46VjhSWWJRTVNyb3c0Rnp4UWRGNWNjUnB1bmFnXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

接着打开飞书开发者平台：

https://open.feishu.cn/?lang=zh-CN

选择开发者后台，点击企业建应用。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=NmUwNjRhZWFkMjI1OGEwZWRiMjQ3OTgxYjdhNTY3MzBfd25SdU0xUllLMmxmWXJsaWllYlR3MVg3eE5Bb3VKNzBfVG9rZW46WHAwSGJsVUIwb2gwbW14VUlRSmNMekJMbnFmXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=NTZiZmQ3MDFkNTAxOGVlODk0ZmE5OGNjZWZhYjllOThfY3Q1SHJrRjZYcUE1R0xHQnFJS1pyOEYxZ2N3azZIaU9fVG9rZW46Slh6ZWJsMllrb04yc2t4M2gwemNmR0M2bmdkXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

名称随便写写就好

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ZTFmY2ZkZjU3MDg1MTI2OGVlMmZjYjJkMDZkOThmMDNfd1pGaXNnYmRWV0xIYXljUzgySmQ4MVVKTmJQVlBzSUhfVG9rZW46VlVkeWJJWGhMb2NVTXp4b3RKRmMxMENrbnJnXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

接着在成员管理点击添加机器人

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=MDk5MzM5ZDE0NDViNTcwMDIwNDk2M2JkNzFmODQwN2ZfV0tIZ3RvWVdGSnEwa1pFZEFBbGhMRDFhNEtxUkVUaDlfVG9rZW46RlRoNGJsYXBjb1ZhVkF4bW9DV2NjQnAzbllmXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

然后我们来到权限管理，点击开通权限。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=OGZhODgwNWYwZWFiZjRiOWJkMTVkNjQ3ODlmMDM3YTBfV3BUUnV1cXBrZFpXMjVYMGtsVkliS2lZZE8wNDJOd1BfVG9rZW46VXhFNGJkVnphb1hOU214RjhvNmN1MVVkbmhkXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

输入im: 然后点击右下角开通权限。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ODJiN2I0N2VkODEwM2QzYmJhMDYyMWE1MGU3MDhlYzBfQjZydUcydHl4Nmw0bzYzYVliWkl6aVB3NXBlanFNbkhfVG9rZW46T1VLR2Jscktvb2dJTVZ4VUdna2NzZVJibjNnXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

然后输入：contact:user.base:readonly

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=NDE3MzYxYWJmNzE0OTFjMTJiNTU0YWE2ODNlZTU2OGRfR0YyQXJCTno4TDZVN0lwcmt5ZHRyVzNpbDFBSmNsS0hfVG9rZW46QmlIMWJVcXhtb1pzUXN4bHdTSWN3MlZUbkloXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

开通完后如果你想使用文档功能，就输入docs:

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=Y2M1YjdkZTE2NmNjMTY5YTNiYzE2NmMyMTE2NGM5Y2NfamNSQVgyd1hNMGJ3T2ZLUGxhMmNEN3FMSEk2WklxVmdfVG9rZW46QnIwNmJjQlVMb0I4Vm54RW1mZWNqTlVXbk15XzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

接着来到凭证与基础信息，复制`App ID与App Secret` 对应的内容。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=M2VlZDUyM2JkYjJmM2YwM2Y5NjJjM2RkMzYyZDM2NzdfRWpYTGFQRk43YThZb2JMSGJtM3FxenJWRlA4VDRFMXhfVG9rZW46RENGN2JIb2tFb1h6Y094Vm9CMmNySWdtbmdlXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

然后返回到刚才的内容填写id和secre，下面有个选项选china版本即可。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ZWFmMWFkZTgzNmU3MDA0YTc4ZDM3Y2IxNGQ1ZjZmMTBfcFZyVmdRNFl4MzNWdjIyQVVFYkZNbDRvVGhqNXh3bkhfVG9rZW46VjNPVmJ2QXdQb0I3Mld4QVlHdGNDeDlDbk5jXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

下面的skill你可以选，用空格选择回车确认即可。其他的可以no如果你没有api的话。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=MWIxZDAyOTBkYzhiMTc5MTg3NTYyYmQ4YTcxMTM4ZTlfNDMwZVdPNXdpd0RlQ0pUcDlXa0czaUtGOHhuUjRxczBfVG9rZW46S29vYmJlYlJVb1pqaE14NkJTV2NsOVRmblhKXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

接下来你可以看到在control UI地方有一个地址，你可以按下ctrl点击鼠标左键或者直接复制进入一个页面。这个就是openclaw的在线页面。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=Mzc1MzJiMzAwN2UyNmQxZDI2MDQwOTcyZTE2OGUyZTJfenZRak5GZkNPcGlVZjN3dlBKcWlSRlpmNkJQMlM5RFFfVG9rZW46WHg4TmJBbzZ1bzl1ZUl4b0g2eWNXMjFybkdlXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

这里我们对话测试没有问题，说明api配置无误。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=OTI3NDFjMjY3NzY5ZTg4NmM0YTkwZmE4ZGQ1NGI0YWRfTUcxZU1KRGhSV0lHczNrTTd3MjM3UXVCNklBTHB3MFZfVG9rZW46T2R3VWJmQ1Fhb21ZcTB4bFBTb2NwSklMbkZlXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

如果测试通过选择do this later退出即可。现在我们返回飞书开发者平台。我们需要找到时间与回调里面的订阅方式，选择长链接并保存。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ODI2ZGQ5YTc4NmIwZjI0MTYxZjVlOTU0NjM4M2FiNmVfcFZCNkRPSjk3OWlXb01Ub2JaQWVYSmJ2UVgzVUc5UFFfVG9rZW46V1NYQWJSUTVsb2ZDVm14MFFoWGNjVlg1bjlQXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

如果没有报错说明你的配置无误，飞书和openclaw配置都没问题。然后看右下角有个添加事件，把消息与群组全部勾选，确认添加。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=YjBmZTI2NzhjOWQzNGNjMmIxMzc5YTc0ZTk5MjhiZjlfN0tMaEtCcmxQUGxiT2FVUGZjWGtFVWFVdjEzZ1VyRWhfVG9rZW46VlZBeWJIdEtUb3RaUXN4bFZwSWMzcW1xbkpnXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

然后到回调配置里，也打开长连接即可。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ODIzMWY5MWFiYmMzYWFhY2U1Yjg3NTNjOTM5NjU2MGNfaFJ0OTc1dEZtTkY2Sld4NFprVWJsQzJtRm9MbU94QkpfVG9rZW46QWFSR2JnZTVjb0l0TGJ4V2dmM2NRRlpxbkFnXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

最后最关键的一步来了！我们需要把所有配置落地，需要点击一下创建版本。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=MTljMDNiMzE2NzU0ZjEwNDdkNjUzM2NlMGFiNjE4ZWRfUmkzbVdGbG45akxJcmZ3cUthcGx6ZG9vWkp2Qkw4VFFfVG9rZW46U3kxS2JEMElrb1hDd0R4YzZDaGNhbXNJbkVoXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

简单填写版本信息，然后保存即可~

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=M2VhOWQ5Y2EwNmRiNDMyYjMyOTQ0MmUwZmE1NDM2YWVfMEpuYmNEQ0h5cjh0QmpScDBOVHB0bktpdVNZQUowYTFfVG9rZW46R0d4VmJnTjB6b1VtQXh4TVBVNWNDMGQ2bnZjXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=Y2E4MjllODBlNmQ3NjlhMTFkYjgxZThmZTUwOGM4ZjNfZFFpS0k1TkVBZDVxSXJJdWloS3ltdWVoenFqRXptMUdfVG9rZW46QXVaMGJnTllEb010ZzN4SVlzaGNSS01SbjBNXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

发布成功后飞书会收到申请。请大家将组织账号登录在飞书，然后打开。飞书会告诉你审批通过，这里你点击打开应用。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=YjBkNjE1ZTdiODYyOGU4M2YxYjE2M2YyYjg0YjY0ZjNfOFFUampYb0p6NUNnZlFtSWRmRDdlSTFIVnJQMFdEQlZfVG9rZW46VXNlT2JORGI4b0ZQcE14VFB4VGNDVU1Hbm9jXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

这里我们发送你好，机器人做了配对申请。你需要将最后这句复制并发送给刚才浏览器的机器人。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ZDhjMzIyMGMxMjU5MTYzNjc5ODk2YzdkMzllYjgwNTVfdFRsQjFsbE5JUDQxdUhwdzZNeVVVY0lhZ0NKeXJiNlVfVG9rZW46RWtScGJDdm9vbzltMFl4ZTkxSGNPd2sxbkhkXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

就像我这样复制进去就好啦。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=NzY0NTI3MDU4YzVhNGYxMGYxZGE2ZTFmYjE4MThmMzdfMzZpem82Vk9haG1WblNCamYzN1pYeFpJVHJYZnpkdVhfVG9rZW46UzdweWJsRDJob2tNMkV4RzJEV2N5aTlUbmZ4XzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

再次回到飞书，这里大家可以看到飞书已经配好啦~~开心

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ZTU3NTVjYTk2ZTQyN2EwMDJkN2U0MTk1NzQwYjQ3OWRfb0pqYkJ2azhpZFVFRFo0N3NjRFF4ZGY0c3VwQzhXWkxfVG9rZW46TE1FWWJ6SFJvb3VOWnF4djVrcWNnRUY2blVjXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

# 5. 飞书群聊多智能体配置

## 5.1 多llm模型配置

和初次配置一样，打开ubuntu的命令行界面，输入：`openclaw onboard`，然后配置好其他模型即可。（详细步骤见第三节 openclaw配置部分）

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=NTIwYzFlZjQ2ODNmMTJmMGZmY2ZiN2YyNGQ5NzlkNTdfSmpxTmVzVVBpZkNhc0FOY0lReHJFRmdiWXU3aThuTzBfVG9rZW46WURoVmJzN0Nrb1EwckV4Y3hIN2N4eER1bjBFXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

不过有个问题，配好后会变成你的默认模型，如果你想调整该怎么做？

这里面推荐大家使用命令修改，输入：`code ~/.openclaw/openclaw.json` 接着你的代码编辑工具会自动打开配置文件。（推荐大家使用Vs code 如果没有Vs code请自行下载~）

比如我这里使用了kimi和minimax两个计划的模型，我想选minimax，在agents->defaults这里的primary将下面的模型名称复制过来就行

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=MGRkNmU0Njk2ZDhiMDI5OGRkZWVkMzM1Y2RmM2U1MjBfejNsOWZQN2pBRHltaVA5Z2VhV2N1ZEw5bWZHT3hZb2NfVG9rZW46Vk1rbmJLb2xXb3VFZkd4RVdSQWNPQ1M0bkxlXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

### 5.1.1 API中转平台配置（以claude opus 4.6为例子）

假设我们需要新增的目标如下：

```Plain
provider: claude-proxy
model: claude-opus-4.6
baseUrl: https://api.claude-proxy.com
api-key: sk-xxx
```

**步骤如下：**

1. **在文件****`.openclaw/agents/main/agent/auth-profiles.json`****添加** **API** **Key（黄色高亮部分）**

```JSON
{
  "version": 1,
  "profiles": {
    "minimax-cn:default": {
      "type": "api_key",
      "provider": "minimax-cn",
      "key": "sk-xxx"
    },
    "zai:default": {
      "type": "api_key",
      "provider": "zai",
      "key": "xxx"
    },
    "claude-proxy:default": {
      "type": "api_key",
      "provider": "claude-proxy-claude",
      "key": "sk-xxx"
    }
  },
  "lastGood": {
    "minimax-cn": "minimax-cn:default",
    "zai": "zai:default"
  },
  "usageStats": {
    "minimax-cn:default": {
      "lastUsed": 1772013471313,
      "errorCount": 0,
      "lastFailureAt": 1771862230918
    },
    "zai:default": {
      "lastUsed": 1772074577956,
      "errorCount": 0
    }
  }
}
```

2. **在****`.openclaw/openclaw.json`****注册 provider**

```JSON
  "auth": {
    "profiles": {
      "minimax-cn:default": {
        "provider": "minimax-cn",
        "mode": "api_key"
      },
      "zai:default": {
        "provider": "zai",
        "mode": "api_key"
      },
      "claude-proxy:default": {
        "provider": "claude-proxy-claude",
        "mode": "api_key"
      }
    }
  },
  "models": {
    "mode": "merge",
    "providers": {
      "minimax-cn": {
        "baseUrl": "https://api.minimaxi.com/anthropic",
        "api": "anthropic-messages",
        "models": [
          {
            "id": "MiniMax-M2.5",
            "name": "MiniMax M2.5",
            "reasoning": true,
            "input": [
              "text"
            ],
            "cost": {
              "input": 15,
              "output": 60,
              "cacheRead": 2,
              "cacheWrite": 10
            },
            "contextWindow": 200000,
            "maxTokens": 8192
          }
        ]
      },
      "zai": {
        "baseUrl": "https://open.bigmodel.cn/api/paas/v4",
        "api": "openai-completions",
        "models": [
          {
            "id": "glm-5",
            "name": "GLM-5",
            "reasoning": true,
            "input": [
              "text"
            ],
            "cost": {
              "input": 0,
              "output": 0,
              "cacheRead": 0,
              "cacheWrite": 0
            },
            "contextWindow": 204800,
            "maxTokens": 131072
          },
          {
            "id": "glm-4.7",
            "name": "GLM-4.7",
            "reasoning": true,
            "input": [
              "text"
            ],
            "cost": {
              "input": 0,
              "output": 0,
              "cacheRead": 0,
              "cacheWrite": 0
            },
            "contextWindow": 204800,
            "maxTokens": 131072
          },
          {
            "id": "glm-4.7-flash",
            "name": "GLM-4.7 Flash",
            "reasoning": true,
            "input": [
              "text"
            ],
            "cost": {
              "input": 0,
              "output": 0,
              "cacheRead": 0,
              "cacheWrite": 0
            },
            "contextWindow": 204800,
            "maxTokens": 131072
          },
          {
            "id": "glm-4.7-flashx",
            "name": "GLM-4.7 FlashX",
            "reasoning": true,
            "input": [
              "text"
            ],
            "cost": {
              "input": 0,
              "output": 0,
              "cacheRead": 0,
              "cacheWrite": 0
            },
            "contextWindow": 204800,
            "maxTokens": 131072
          }
        ]
      },
      "claude-proxy-claude": {
        "baseUrl": "https://api.claude-proxy.com",
        "api": "anthropic-messages",
        "models": [
          {
            "id": "claude-opus-4-6",
            "name": "claude-opus-4.6",
            "reasoning": true,
            "input": [
              "text"
            ],
            "contextWindow": 200000,
            "maxTokens": 8192
          }
        ]
      }
    }
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "claude-proxy-claude/claude-opus-4-6"
      },
      "models": {
        "minimax-cn/MiniMax-M2.5": {
          "alias": "Minimax"
        },
        "zai/glm-5": {
          "alias": "GLM5"
        },
        "zai/glm-4.7": {
          "alias": "GLM4.7"
        },
        "claude-proxy-claude/claude-opus-4-6": {
          "alias": "Claude Opus 4.6(claude-proxy)"
        }
      },
      "workspace": "/Users/clawer/.openclaw/workspace",
      "compaction": {
        "mode": "safeguard"
      }
    }
  },
```

3. 重启gateway

```Plain
openclaw gateway restart
```

## 5.2 飞书多agents配置

这里请参考飞书配置部分，再配置1个或多个机器人。大家可以用我做好的权限配置导入即可。然后我们拿到对应的id和密钥。

### 详细步骤

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=MjVlYzNiNDM0MWUxMDUwMGRlNmJhMDMwYzE4YzJiNzhfbVlBN3NLbUsxemR3U1R3eGV6NUpxNlAySTdnM01lOHJfVG9rZW46TFc1TWJWcDBXb2dnS1l4Yk5XTmNIcUNobjNjXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

```JSON
{
  "scopes": {
    "tenant": [
      "attendance:overtime_approval:write",
      "calendar:time_off:create",
      "calendar:time_off:delete",
      "calendar:timeoff",
      "contact:user.base:readonly",
      "corehr:person.entry_leave_time:read",
      "directory:employee.base.background_image:read",
      "directory:employee.base.is_primary_admin:read",
      "directory:employee.base.resign_time:read",
      "docs:doc",
      "docs:doc:readonly",
      "docs:document.comment:create",
      "docs:document.comment:read",
      "docs:document.comment:update",
      "docs:document.comment:write_only",
      "docs:document.content:read",
      "docs:document.media:download",
      "docs:document.media:upload",
      "docs:document.subscription",
      "docs:document.subscription:read",
      "docs:document:copy",
      "docs:document:export",
      "docs:document:import",
      "docs:event.document_deleted:read",
      "docs:event.document_edited:read",
      "docs:event.document_opened:read",
      "docs:event:subscribe",
      "docs:permission.member",
      "docs:permission.member:auth",
      "docs:permission.member:create",
      "docs:permission.member:delete",
      "docs:permission.member:readonly",
      "docs:permission.member:retrieve",
      "docs:permission.member:transfer",
      "docs:permission.member:update",
      "docs:permission.setting",
      "docs:permission.setting:read",
      "docs:permission.setting:readonly",
      "docs:permission.setting:write_only",
      "hire:ehr_import",
      "im:app_feed_card:write",
      "im:biz_entity_tag_relation:read",
      "im:biz_entity_tag_relation:write",
      "im:chat",
      "im:chat.access_event.bot_p2p_chat:read",
      "im:chat.announcement:read",
      "im:chat.announcement:write_only",
      "im:chat.chat_pins:read",
      "im:chat.chat_pins:write_only",
      "im:chat.collab_plugins:read",
      "im:chat.collab_plugins:write_only",
      "im:chat.managers:write_only",
      "im:chat.members:bot_access",
      "im:chat.members:read",
      "im:chat.members:write_only",
      "im:chat.menu_tree:read",
      "im:chat.menu_tree:write_only",
      "im:chat.moderation:read",
      "im:chat.tabs:read",
      "im:chat.tabs:write_only",
      "im:chat.top_notice:write_only",
      "im:chat.widgets:read",
      "im:chat.widgets:write_only",
      "im:chat:create",
      "im:chat:delete",
      "im:chat:moderation:write_only",
      "im:chat:operate_as_owner",
      "im:chat:read",
      "im:chat:readonly",
      "im:chat:update",
      "im:datasync.feed_card.time_sensitive:write",
      "im:message",
      "im:message.group_at_msg:readonly",
      "im:message.group_msg",
      "im:message.p2p_msg:readonly",
      "im:message.pins:read",
      "im:message.pins:write_only",
      "im:message.reactions:read",
      "im:message.reactions:write_only",
      "im:message.urgent",
      "im:message.urgent.status:write",
      "im:message.urgent:phone",
      "im:message.urgent:sms",
      "im:message:readonly",
      "im:message:recall",
      "im:message:send_as_bot",
      "im:message:send_multi_depts",
      "im:message:send_multi_users",
      "im:message:send_sys_msg",
      "im:message:update",
      "im:resource",
      "im:tag:read",
      "im:tag:write",
      "im:url_preview.update",
      "im:user_agent:read",
      "optical_char_recognition:image",
      "search:dataset.docs:create",
      "search:dataset.docs:delete"
    ],
    "user": []
  }
}
```

## 5.3 openclaw配置agents

核心文档如下，但是实际操作起来还是比较麻烦的。我们配置agents可能需要有不同的任务，不同的技能，不同的记忆及工作空间，怎么合理的分配和调用这些agents呢？

https://docs.openclaw.ai/channels/feishu

一般情况下我们需要不同的agent我们需要有不同的人设、不同的用途、不同的记忆。那么在openclaw使用workspace与agentDir来控制工作区和agent的配置区。

**workspace默认位置：** `~/.openclaw/workspace` 

**agentDir默认位置：** `~/.openclaw/agents/<agent-id>`

所以我们需要把位置与其他agent区分开，方便我们管理~做到隔离。这样才会像控制不同的角色一样控制大家。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=Nzc0NTNlZmJhYmMyNGVjMTkyZjg0YzJkNmIyNjIwN2FfQ3RIRVFMNWhMT3JQRVpkdExueFliTENUN1FFUXhGenhfVG9rZW46SzZUUWJvQUNob3lsRUF4aHdrMmNJc2RkbkxlXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

### 知识补充

**channels** 是 OpenClaw 配置中（openclaw.json 文件的根级别字段）的一个核心部分，它专门用来定义和管理**外部通信平台（聊天渠道）的集成**。简单说，**channels 就是告诉 OpenClaw “我要连接哪些聊天App/平台（如飞书**、Telegram**、Discord 等），用什么账号/凭证去连，以及怎么控制谁能发消息给** **bot”**。

**bindings** 是 OpenClaw 配置中一个非常重要的字段（位于 JSON 的根级别 "bindings": [...]），它的作用是**路由规则**（routing rules），用来决定：当飞书（或其他 channel）收到一条新消息时，应该交给哪个 agent（智能体）来处理。

简单来说，就是“把这个消息发给谁处理”的匹配规则。OpenClaw 支持多 agent（比如你有 main 和 mimi1 两个），每个 agent 有独立的 workspace、记忆、模型、文件等。**bindings 就是连接** **channel** **→ account → agent 的桥梁**，防止所有消息都挤到同一个 agent 里。

### JSON直接配置

请跟着我按下面的描述配置~

我们现在飞书的channels里面配置了mimi1这个账号

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=YmIxZWM0OGFjMDYwMjQ1YzJmZDkzZmIxNzk3NDRhMGJfY3M3WUJzVTdZZ090WllaQThMSjBnbkpjeVVlalNPdXhfVG9rZW46V3VxSmJsd2JKb21MWGZ4VEVGVGNaSVM1bkRiXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

然后定义mimi1的工作区和agent工作目录

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=YjUzNWMzOTYwZTVjZDgzZjMwZmQ0NzIxNTA2OWIwYzhfNDR1SEFqWk1CVGMwNGNmanlnaEZuYWxzdUgyYzg1c3JfVG9rZW46UmxOb2JBaEVGb3JLRGl4d0d1WmNUbE95blhpXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

最后建立bindings建立mimi1的飞书agent路由通路

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=NmFmNGM2ZDQ2NTNmZTI5ZTU0OGQ5OGQ4MmJlZDQ3YmRfNWtqdjNhaU9tdnEwSjEwelNad1dkYzlHV3JKWjNTRFNfVG9rZW46SGoza2J4R1Y0b2ZoUDJ4V2x0WmMxVnRYbkVnXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

完整配置参考~

```JSON
{
  "meta": {
    "lastTouchedVersion": "2026.2.23",
    "lastTouchedAt": "2026-02-25T06:23:21.988Z"
  },
  "wizard": {
    "lastRunAt": "2026-02-25T02:21:40.503Z",
    "lastRunVersion": "2026.2.23",
    "lastRunCommand": "onboard",
    "lastRunMode": "local"
  },
  "auth": {
    "profiles": {
      "minimax-cn:default": {
        "provider": "minimax-cn",
        "mode": "api_key"
      },
      "kimi-coding:default": {
        "provider": "kimi-coding",
        "mode": "api_key"
      }
    }
  },
  "models": {
    "mode": "merge",
    "providers": {
      "minimax-cn": {
        "baseUrl": "https://api.minimaxi.com/anthropic",
        "api": "anthropic-messages",
        "models": [
          {
            "id": "MiniMax-M2.5",
            "name": "MiniMax M2.5",
            "reasoning": true,
            "input": [
              "text"
            ],
            "cost": {
              "input": 0.3,
              "output": 1.2,
              "cacheRead": 0.03,
              "cacheWrite": 0.12
            },
            "contextWindow": 200000,
            "maxTokens": 8192
          }
        ]
      },
      "kimi-coding": {
        "baseUrl": "https://api.kimi.com/coding/",
        "api": "anthropic-messages",
        "models": [
          {
            "id": "k2p5",
            "name": "Kimi for Coding",
            "reasoning": true,
            "input": [
              "text",
              "image"
            ],
            "cost": {
              "input": 0,
              "output": 0,
              "cacheRead": 0,
              "cacheWrite": 0
            },
            "contextWindow": 262144,
            "maxTokens": 32768
          }
        ]
      }
    }
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "minimax-cn/MiniMax-M2.5"
      },
      "models": {
        "minimax-cn/MiniMax-M2.5": {
          "alias": "Minimax"
        },
        "kimi-coding/k2p5": {
          "alias": "Kimi for Coding"
        }
      },
      "workspace": "/home/wyn/.openclaw/workspace",
      "compaction": {
        "mode": "safeguard"
      },
      "maxConcurrent": 4,
      "subagents": {
        "maxConcurrent": 8
      }
    },
    "list": [
      {
        "id": "main",
        "name": "main",
        "workspace": "~/.openclaw/workspace/work",
        "model": "minimax-cn/MiniMax-M2.5"
      },
      {
        "id": "mimi1",
        "name": "mimi1",
        "workspace": "/home/wyn/.openclaw/workspace-mimi1",
        "agentDir": "/home/wyn/.openclaw/agents/mimi1/agent",
        "model": "kimi-coding/k2p5"
      }
    ]
  },
  "bindings": [
    {
      "agentId": "mimi1",
      "match": {
        "channel": "feishu",
        "accountId": "mimi1"
      }
    },
    {
      "agentId": "main",
      "match": {
        "channel": "feishu",
        "accountId": "main"
      }
    }
  ],
  "messages": {
    "ackReactionScope": "group-mentions"
  },
  "commands": {
    "native": "auto",
    "nativeSkills": "auto",
    "restart": true,
    "ownerDisplay": "raw"
  },
  "session": {
    "dmScope": "per-channel-peer"
  },
  "hooks": {
    "internal": {
      "enabled": true,
      "entries": {
        "session-memory": {
          "enabled": true
        },
        "command-logger": {
          "enabled": true
        },
        "boot-md": {
          "enabled": true
        },
        "bootstrap-extra-files": {
          "enabled": true
        }
      }
    }
  },
  "channels": {
    "feishu": {
      "enabled": true,
      "domain": "feishu",
      "dmPolicy": "open",
      "groupPolicy": "open",
      "accounts": {
        "main": {
          "appId": "cli_a9cc0",
          "appSecret": "lmAcgytgtdyfOJEv"
        },
        "mimi1": {
          "appId": "cli_abce",
          "appSecret": "ErZ3YVFMttOZ"
        }
      }
    }
  },
  "gateway": {
    "port": 18789,
    "mode": "local",
    "bind": "loopback",
    "auth": {
      "mode": "token",
      "token": "158abc8675a89c6a7bd7c7c0e62f4b768a966cadc3e1b09d"
    },
    "tailscale": {
      "mode": "off",
      "resetOnExit": false
    }
  },
  "plugins": {
    "entries": {
      "feishu": {
        "enabled": true
      }
    }
  }
}
```

### 懒人版方案（有失败概率）

这里我直接求助了grok，grok可以完整的输出文档。（其实我也试过kimi，但是kimi没有完成这个任务。）

提示词如下：

```Bash
先阅读文档：https://docs.openclaw.ai/channels/feishu.md
我需要你再配置一个智能体，使用飞书channel，配置智能体名称叫mimi1，使用于main的的工作区和agentdir 使用kimi模型，下面是id和密钥
id：cli_aXXXXXXXXXXXXX8dbce
密钥：ErZ3YXXXXXXXXXXXXXXXFMttOZ
然后修改下面的配置json，并给我返回完整修改后的json内容
{
  "meta": {
    "lastTouchedVersion": "2026.2.23",
    "lastTouchedAt": "2026-02-25T02:21:40.514Z"
  },
  …………………………………………
  …………………………………………
```

返回后如下图，点击复制即可

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=Mzk5YmRjOWMwYmZlNTgzMWIwNzI4ZjMyYTFjZTExYWVfNkFlVEx5SWRWNHFFS1REUWF4em10aTJxRHE3aUN3WjdfVG9rZW46TWpzNmJvelZ5b1NjTjF4VHFPU2MxQ0VnbnVkXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=MjI5MmViYzYxODcwODBmMjE0YjU2YjMwOTY1MWQxNmJfQ2VlOW41aXZ5MW5reGhwMHlTMmxVSVZlQXhIaFFVQWRfVG9rZW46T3VlSmJXNkpUbzZ0c2Z4aVpxQWMzcTdWbmQ4XzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

然后我们粘贴到openclaw.json文件内。

接着打开ubuntu，输入 `openclaw gateway restart`

没有报错说明配置无误~

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=NGViZGYzNzg4ZDQ5NTVjZjAzZmRiMjJlNGRkZWU2MGNfbHU0aVZ1NU9zYXhhR3A1emhyeWF6cW9taE1nNU8zVDFfVG9rZW46UVNQZWJ6blAwb2pOOUN4aFZlcmM1YURzbnJ0XzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

接着回到飞书，把长连接配好就ok啦，记得发布你的修改哦~

### 配置飞书群聊agents

配好后我们可以让agent在群聊里开party了~ 

这里我们新建一个飞书群，随便起一个名字创建。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=MWNhNjY3NGRkMzg0NWIyYTAwMzQ4MWZiYjUwZTc2YmRfVDIzZThZTnFKTWdYcUQzc21UZThsRFZmSzFuMjhrYkhfVG9rZW46QXhWcGJpTEcyb1JpV3h4Rko4VGNPdjk3bjlkXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ZGI1YTMyOTI4OTk0NmQxYmY4N2FiYWYxMDQyNWZhY2FfdTFsM0JmTTZxazRVMkF2dG9wWXFOcEFuNktoZzZJNkhfVG9rZW46SGp3MWJTRUdVb1FIdDR4bWlSOWNUSXk1bmllXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

然后把龙虾们请进来~

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=MjUyMDI2ZmUxMjlmZDQwMzQ4OTU4NmE4NmU3OTkzY2NfbVptaExqYXJ2UWVDOVdSSEtseDFLZDNBcWJIZG5CU0RfVG9rZW46RTNIQWJsaWhEbzkxb1l4WU9QOGMwcDJUbmFoXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=MTEyMTAyODJmOTNkZGM1MzhmNzkyZDhiNDcyM2FkMzdfY3VIQmxxSlJTYkNFNmJ2MHVmdXJsTERKUlNFcklWMDJfVG9rZW46Rk1tWGJNZjRVbzhJa214SnI3OGN6VGltblplXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=YzI2OTBkYjAzOTdhNzIyZmNlMTg1ZjcxYzE0Yjc0ZDZfMkVBdHMzQzRUZ0RKdGdjVkMyd1lmNTZ2SFA2VWU1MGFfVG9rZW46UjZxSWJKVE1Bb2dXY2d4eEY1TmNzUjdMbm9lXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

然后你们就可以开party了~ 逐个@就好，到这我们的机器人party就可以了。

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=OTNjNWY3NGU0OWY4MDI1NmRlOGFhNTE4YjU3MGMxZGNfamhaa1p1b0VDQ2pPRXRKUUtmQW84ZHhwekhBOVJxblBfVG9rZW46U09DUGJuODhBb0dZZ2t4UnBPb2NaNkx3blFnXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

如果想拉自己的伙伴你可以这样，分享二维码就行。然后把伙伴拉入群~

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=MjA1MDRiYTZkYTUxMDU1MGM4MjIwNzAxMDdhYjRhZTNfWEdEa2xkOGt2b2J2Rm16ajhBMTMyYTFyTTdnNmpPQkRfVG9rZW46S3VkMGJjVTNnbzNUbHd4QTQ5Q2N2MWgwbmhnXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

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

1. # 推荐一些小技巧

## 7.1 联网skills

联网是个大问题hh，可能需要两个方面。一个是主动拉取浏览器，另一个是阅读网址。

这里我们选择使用Tavily作为我们的核心工具~请大家先注册一个账号：

https://app.tavily.com/home

然后需要你新建一个api并复制key~

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=Y2I4NDNiNjdiMDU4ODlmMzI4MDcxYzM1ZDAxMDk2NDVfZmRBcjVISzFkR2NYazJaYk90d1B5cEhqQmFGWmRYTGFfVG9rZW46QVlPNmJZV2tEb3dWSHR4N2dnbWNVSnZybllmXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

接着来到ubuntu的界面，输入下面命令并输入y。

```Plain
 npx clawhub@latest install tavily-search
```

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=Mjk2NTY2NTU1OWVjMDg3OTJhMzg4NTE2NTNlZGFjY2Vfdm43cW1kclJCeHZ6Nmg0OHlhWXNaUTc4N1NLZGtCUnpfVG9rZW46Q1ZkemJDRjJWb2hhZnh4N2VneGMxNjV6bk9mXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

装好之后再输入，下面的“apikey”替换为你的key即可~

```Plain
export TAVILY_API_KEY="apikey"
```

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=NmRkNWI5YTgxOGRhZGQxNGI0ZGVlMDEwNGY0ZDVjNzJfc3hLMk90R1FXVWR0Rm9MN3g3WDVXOXVyMWs0YnJCS3NfVG9rZW46TDhJNWJZQ3dDb3pDNlB4V1dzaGN0cGRCbjdmXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

接着进入飞书，找一个想用这个技能的agent：

让他查看skill并将刚才我们安装的tavily-searchskill也加进来~

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=MzNlYWQ2ZmYxMDVlM2YxMzkzODM5MDdjMmQ5ODE5ZDZfRzlQdUw0Rmh1Vlh2bmhEaHZYTVhPRXNwTW42dTRZZ1BfVG9rZW46QzIwRWJpbTRqb0lJb2F4RjFEUmN3UXFObkNmXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

测试通过~

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=OTE3ZDkyZWE2OWVkMTAzYThmNzBiYjczMjgyMmE1NWNfR1RPRWVGaU9aRWpLSlpWbHp0T3VERDd4OUhUdDVuVWNfVG9rZW46RmJ2OGJJTzNMbzNYVnN4dDBKamNoR1NJbkVoXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

## 7.2 如何优雅地使用**ClawHub** 

下面是一份「**如何优雅地使用 OpenClaw 的 ClawHub**」教程：先讲它是什么、为什么好用，再给你一套从 0 到熟练的使用流程，最后附上我更推荐的新手技能清单（并带上安全注意事项）。

### 1. ClawHub 是什么？（一句话理解）

**ClawHub 是 OpenClaw 的公共 Skills 注册中心/官方商店**：你可以把它理解成「给智能体装插件的 App Store / npm」。Skills 本质上是一个文件夹，核心是 `SKILL.md`（外加一些辅助文件），既能在网页上浏览，也能用 CLI 搜索、安装、更新、发布。([OpenClaw](https://docs.openclaw.ai/zh-CN/tools/clawhub))

### 2. 为什么这个“官方商店”好用？

ClawHub好用主要在这几件事上（都很“工程化”）：

1. **语义搜索（不只关键词）** 它支持基于向量/嵌入的搜索，更适合你用自然语言找能力，比如“帮我管理日历”“连接 Trello”。([OpenClaw](https://docs.openclaw.ai/zh-CN/tools/clawhub))
2. **版本管理像 npm：可回滚、可打标签** Skills 支持语义化版本号、变更日志、`latest` 之类标签；每次发布生成版本，标签可移动，天然支持回滚。([OpenClaw](https://docs.openclaw.ai/zh-CN/tools/clawhub))
3. **CLI 工作流顺滑：装、更新、同步、发布一条命令** `search / install / update --all / publish / sync` 这些命令把“扩展能力”变成标准化运维动作。([OpenClaw](https://docs.openclaw.ai/zh-CN/tools/clawhub))
4. **可审计/可协作：公开内容、评论星标、（还有审核钩子）** 技能内容（`SKILL.md`）可直接查看；并且有星标/评论等信号；官方文档也提到审核钩子用于审批与审计。([OpenClaw](https://docs.openclaw.ai/zh-CN/tools/clawhub))

1. ### 优雅使用 ClawHub：推荐的“最佳实践”流程

#### Step A：先用网页挑选，再用 CLI 安装（最省心）

- 网页端用来“逛”：看简介、版本、安装量、是否 Highlighted、以及（如果有）安全扫描/报告等信号。
- CLI 用来“装”和“管”：保证可重复、可更新、可同步。

ClawHub 网页上有 **Highlighted**（偏“官方/社区精选信号”）以及 **Hide suspicious**（隐藏可疑内容）的入口，建议你默认开启“隐藏可疑”。([ClawHub](https://clawhub.ai/skills?nonSuspicious=true&utm_source=chatgpt.com))

#### Step B：安装 CLI（一次搞定）

任选其一：(OpenClaw)

```Bash
npm i -g clawhub
# 或
pnpm add -g clawhub
```

#### Step C：搜索与安装（新手最常用）

官方给的最小闭环是：先搜再装：(OpenClaw)

```Bash
clawhub search "calendar"
clawhub install <skill-slug>
```

安装后要让 OpenClaw **重新启动一个会话**，它才会加载新 skills。([OpenClaw](https://docs.openclaw.ai/zh-CN/tools/clawhub))

#### Step D：把“技能管理”做得更优雅（工作区、锁文件、可重复）

几个关键点：

- **默认安装位置**：CLI 会把 skills 装到当前目录的 `./skills`。([OpenClaw](https://docs.openclaw.ai/zh-CN/tools/clawhub))
- **更推荐做法**：为你的 OpenClaw 项目准备一个“固定工作区”（workspace），让 skills 都进 `<workspace>/skills`，项目更可移植。([OpenClaw](https://docs.openclaw.ai/zh-CN/tools/clawhub))
- **用锁文件掌控状态**：已安装 skills 记录在 `.clawhub/lock.json`，这让“在另一台机器复现同一套技能”更靠谱。([OpenClaw](https://docs.openclaw.ai/zh-CN/tools/clawhub))

常用命令：

```Bash
# 看已安装
clawhub list

# 更新全部（我建议定期做，但要先看变更）
clawhub update --all
```

#### Step E：发布/备份你自己的 skills（进阶但很爽）

当你写了自己的 skill（一个文件夹+SKILL.md），你可以发布备份：(OpenClaw)

```Bash
clawhub publish ./my-skill \
  --slug my-skill \
  --name "My Skill" \
  --version 1.0.0 \
  --tags latest
```

或者用 `sync` 扫描并同步发布多个 skills：([OpenClaw](https://docs.openclaw.ai/zh-CN/tools/clawhub))

```Bash
clawhub sync --all
```

### 3. agent下也可以用几句话轻松搞定安装

这里我用安装：**self-improving-agent 举例：**

前提是你提前装好了clawhub，我用到的prompt如下。但请注意：如果需要apikey （例如Tavily），最好手动安装。

```Plain
安装：self-improving-agent skill 使用clawhub
```

![img](https://ccnpfm0xlkhu.feishu.cn/space/api/box/stream/download/asynccode/?code=ODU4OTg0N2QzY2I3NjFhZTQ4YWMwMWQwMjIwMzI4YWZfMDlOQzRrU2lIbXdDTjF1b3hURGQ5SjJwOXJnaEloM1hfVG9rZW46Qjd6eWJUb2dVb0U1Tkl4SlRwR2NPU3RwbnpiXzE3NzIzNzYxOTQ6MTc3MjM3OTc5NF9WNA)

### 4. 安全提醒（非常重要，但不需要恐慌）

因为 Skills 可能包含可执行逻辑或引导你执行命令，**它们本质上要当“第三方代码”对待**。官方文档也明确提到安全注意：把第三方 skills 当作不可信代码，启用前先阅读。([OpenClaw](https://docs.openclaw.ai/tools/skills?utm_source=chatgpt.com))

另外，近期也确实有媒体报道 ClawHub 出现恶意 skills/供应链风险（尤其伪装成加密货币相关工具），并提醒用户谨慎安装与审查。(Tom's Hardware)

**我的“优雅安全习惯”清单：**

- **只从你能看懂/能审核的来源装**：至少打开 `SKILL.md` 看它要什么权限、要读写哪些文件、要不要你复制粘贴奇怪命令。
- **优先选择 Highlighted / 有较多安装量 / 有扫描报告的**（但仍要自己看）。
- **对“要你运行一长串 curl|bash、混淆命令、索要私钥/助记词/API Key”的技能直接拒绝**。
- **给技能最小权限**：能用单独 API key 就别给全能 key；能用专门账号就别用主账号。

### 5. x上10个最受欢迎的skills

X上大家讨论和推荐的实用/高频技能（基于社区反馈、安装量、使用场景，排除明显恶意类），我整理出下面这些被多次提到“很推荐”“必装”“日常用”的，基本覆盖核心需求：

1. **tavily-search** 联网搜索技能（AI优化版），让Agent能实时查最新资讯、数据，避免“闭眼编”。几乎所有人都说“没这个跟瞎子一样”。 安装：clawhub install tavily-search
2. **find-skills** 让Agent自己去ClawHub搜并安装需要的技能，解决“不知道用哪个工具”的痛点。 安装：clawhub install find-skills
3. **proactive-agent**（或旧版proactive-agent-1-2-4） 给Agent加“主动性”和自我迭代能力，能记住历史、优化行为、减少重复问。长期用很香。 安装：clawhub install proactive-agent
4. **github** GitHub集成，能自动管repo、issue、PR、code search。开发者必备。 安装：clawhub install github
5. **gog** Google Workspace全家桶（Gmail、日历、Drive、Docs），办公自动化神器。 安装：clawhub install gog
6. **skill-vetter** / **clawsec** 安装前扫描技能安全，防恶意代码。**安全第一步**，很多人后悔没先装这个。 安装：clawhub install skill-vetter 或类似安全扫描类
7. **automation-workflows** 工作流编排，把多个技能串起来干复杂事（自动邮件+报告+数据同步等）。 安装：clawhub install automation-workflows
8. **bird** X/Twitter集成，能发帖、搜趋势、管理账号（但小心伪装恶意版）。（社区提到，但慎用高赞的“Twitter”相关）
9. **self-improving-agent** 加记忆+自我优化，长期交互越用越聪明。 安装：clawhub install self-improving-agent
10. **feishu-doc**（针对国内用户） 飞书文档/云盘集成，企业/团队协作常用。 安装：clawhub install feishu-doc

### 6. 最建议新手使用的10个skills

作为新手，最建议先装的10个ClawHub skills（基于2026年ClawHub热门榜、awesome-openclaw-skills精选、社区/X/Reddit真实反馈），重点选**低风险、高实用、立竿见影提升体验**的。顺序也很重要：先安全+基础，再加生产力，最后加高级。

这些技能几乎都是@steipete 等靠谱作者的，安装量高、star多、恶意报告极少。**强烈建议**：先用 clawhub install skill-vetter 或类似安全扫描技能检查，再装别的。安装用 clawhub install <slug> 或 npx clawhub@latest install <slug>。

1. **self-improving-agent** 自我迭代/主动代理。让Agent记住错误、自我优化、越来越聪明。新手最容易感受到“哇，变聪明了”。 （ClawHub热门榜第一，46k+ installs）
2. **tavily-search** (或 tavily-web-search) 联网搜索（Tavily API优化版）。没这个Agent就是“井底之蛙”，查不了实时信息。几乎所有新手必装第一梯队。 （37k+ installs，AI Agent标配）
3. **gog** (Google Workspace CLI) Gmail、日历、Drive、Docs全家桶。日常办公/邮件/日程神器，新手最快看到实际自动化效果（读邮件、加日历、写文档）。 （46k+ installs，超级实用）
4. **github** GitHub集成（用gh CLI）。能搜代码、管issue/PR、创建repo。新手学代码/做项目超方便。 （35k+ installs，开发者入门必备）
5. **summarize** 总结URL、PDF、图片、YouTube、音频。快速消化信息，新手研究东西时超级省力。 （36k+ installs，高频使用）
6. **find-skills** 让Agent自己去ClawHub搜并推荐/安装技能。解决“不知道装什么”的最大痛点，新手最友好。 （社区反复推荐的“元技能”）
7. **ontology** 或 **agent-memory** / **memory** 结构化记忆/知识图谱。让Agent真正“记住你”、跨对话连贯，不再健忘。新手交互体验提升巨大。 （35k+ installs，长期用越用越香）
8. **weather** 查天气（无需API key）。超级简单、零配置，新手第一个测试技能，成功率100%，建立信心。 （29k+ installs，入门玩具但实用）
9. **proactive-agent** (或 proactive-agent-1-2-4 等版本) 增加主动性，能自己规划、迭代任务。让Agent从“被动回答”变成“主动帮忙”。 （X上中文社区特别推，新手用后反馈“活了”）
10. **skill-vetter** / **security-audit** 或类似安全扫描 安装前扫描技能代码、防恶意。**新手安全第一**，装这个后再放心装别的。 （安全类必备，社区共识“后悔没先装”）

**新手安装建议顺序**（一步步来，别一下全装）：

1. 先装 skill-vetter（安全）
2. tavily-search（联网）
3. self-improving-agent + proactive-agent（聪明起来）
4. gog 或 github（看你日常用Google还是代码）
5. summarize + find-skills（研究+扩展）
6. ontology/memory（长期记忆）
7. weather（测试玩玩）

**Tips**：

- 先去 https://www.clawhub.ai/ 浏览热门/ trending，看安装量和作者。
- 用 clawhub search "beginner" OR "essential" 自己搜。
- 装完后新开session（重启OpenClaw），技能才会生效。
- 别一次性开太多，token和性能会爆炸。先3-5个玩熟了再加。
- 安全永远第一：用隔离环境（Docker）、别给敏感权限、定期 clawhub update --all。

### 7. 一套“优雅到位”的新手上手脚本（你可以照抄）

```Bash
# 1) 装 CLI
npm i -g clawhub

# 2) 搜索（先用自然语言）
clawhub search "calendar"
clawhub search "trello"

# 3) 安装（挑你确认过的 slug）
clawhub install skills/calendar
clawhub install steipete/trello

# 4) 查看安装列表 & 锁定状态
clawhub list

# 5) 之后定期更新
clawhub update --all
```

> 注意：实际 slug 以你在网页端看到的为准；装完记得重启 OpenClaw 会话让它加载。([OpenClaw](https://docs.openclaw.ai/zh-CN/tools/clawhub))

## 7.3 我发现了 OpenClaw 的技能仓库项目：这个 20k+ Stars 的“神级清单”里，几乎涵盖了所有好用的 Skills（小白教程流）

如果你是第一次接触 OpenClaw，十有八九会卡在一个问题：**Skill 到底该装哪个？** 这时候，`VoltAgent/awesome-openclaw-skills` 就像一张“技能世界地图”——它把技能按场景整理成目录，帮你快速找到“从哪开始”。更夸张的是，这个仓库在 GitHub 上显示 **Star 约 20.1k**，已经成了很多人入门时默认会收藏的“神级清单”。([GitHub](https://github.com/VoltAgent/awesome-openclaw-skills/blob/main/README.md?utm_source=chatgpt.com))

你会学到——这个仓库是什么、它和 ClawHub（官方技能商店/注册中心）怎么配合使用、如何优雅地挑技能 + 安装 + 更新，以及一定要写进文章里的安全注意事项。

### 1. 先搞清楚：awesome 仓库 vs ClawHub，到底谁负责什么？

你只要记住一句话：

- **awesome-openclaw-skills**：是“导购/目录/精选清单”，负责帮你**发现**技能，按场景分类整理。([GitHub](https://github.com/VoltAgent/awesome-openclaw-skills?utm_source=chatgpt.com))
- **ClawHub**：是 OpenClaw 的技能注册中心（更像 App Store / npm），负责**搜索、安装、更新、版本管理**；网页端有向量搜索、并提供 CLI 管理工作流。([ClawHub](https://clawhub.ai/skills?nonSuspicious=true&utm_source=chatgpt.com))

所以最优雅的搭配是：

> 用 awesome 找方向 → 点进去看说明 → 回到 ClawHub 用 CLI 安装与管理（可复现、可更新）。

### 2. 为什么这个 20k+ Stars 仓库会火：它解决了小白最大的痛点

小白逛“商店”的真实体验经常是：

- 我只知道自己想“更省事”，但不知道该搜什么关键词
- 搜出来一堆结果，质量参差、看得头大

awesome 清单的价值就在于：它把“技能生态”从散乱变成了**按场景的目录**，你可以从“我想做什么”出发，而不是从“我该搜什么”出发。([GitHub](https://github.com/VoltAgent/awesome-openclaw-skills/blob/main/README.md?utm_source=chatgpt.com))

- **它像新手地图**：带你从 0 建立“技能能做什么”的全局认知
- **它像候选池过滤器**：先筛一轮，再去商店/仓库细看说明
- **它像作业答案**：你能直接抄“同类人常用的组合”

### 3. 小白最推荐的“优雅工作流”：三步挑技能 + 两步装技能

下面是你可以直接写进文章、读者照着做就能跑通的流程。

#### 第一步：用 awesome 清单挑“场景”，别急着挑“技能”

先问自己：你最想让 OpenClaw帮你干什么？（只选 1～2 个场景就够了）

- 日程/任务管理
- 写作与内容整理
- 开发辅助（代码、文档、Issue）
- 桌面自动化（点按钮、打开软件、抓取 UI 信息）
- 信息检索与知识库

然后去 awesome 清单里，找到对应分类，**每个场景先挑 2～3 个候选**。不要贪多：装太多你反而不知道哪个有效。

> 这一步“少即是多”：小白最容易踩的坑就是一次性装 20 个技能，最后一个也没用起来。

#### 第二步：点进候选技能，做一个“30 秒体检”

每个候选技能，你只检查三件事（这套检查很“优雅”，也很现实）：

1. **它要不要你提供凭据（token/API key/账号密码）？**
2. **它会不会读写本地文件、执行命令、访问网络？**
3. **说明文档是否清楚：配置步骤、例子、输入输出？**

（你不需要一上来读源码，但一定要把“它要你交出什么权限”看明白。）

#### 第三步：回到 ClawHub，用 CLI 安装（让一切可复现）

ClawHub 官方文档给的最短闭环就是：`search → install → 重启会话`。([Claw](https://docs.claw.so/engine/tools/clawhub/?utm_source=chatgpt.com))

**安装 CLI：**

```Bash
npm i -g clawhub
# 或
pnpm add -g clawhub
```

**搜索 + 安装：**

```Bash
clawhub search "calendar"
clawhub install <skill-slug>
```

安装后记得**启动一个新的 OpenClaw 会话**，它才会加载新技能。([Claw](https://docs.claw.so/engine/tools/clawhub/?utm_source=chatgpt.com))

### 4. “优雅使用”的关键：让技能管理像管理依赖一样可靠

#### 4.1 固定你的工作区：别让技能散落一地

ClawHub CLI 默认把技能装到当前目录的 `./skills`。([Claw](https://docs.claw.so/engine/tools/clawhub/?utm_source=chatgpt.com)) 更推荐你做一个专门的 OpenClaw 工作目录（比如 `~/openclaw-workspace`），以后所有技能都在同一个地方，方便迁移、备份、复用。

#### 4.2 锁文件：你装过什么，版本是什么，一清二楚

ClawHub 会把已安装技能记录在 `.clawhub/lock.json`（位于你的 workdir 下）。([OpenClaw](https://docs.openclaw.ai/tools/clawhub?utm_source=chatgpt.com)) 这意味着你可以把“我这套好用的技能组合”变成**可复现**的配置，而不是“我电脑上装了啥我也说不清”。

#### 4.3 更新：一条命令，但别无脑更新

```Bash
clawhub update --all
clawhub list
```

> 更新前先看看变更说明（changelog/README），尤其是涉及凭据、命令执行、文件读写的技能。

1. ### 必须单独写一节：安全使用（小白最需要的“护身符”）

你前面说“涵盖所有好用的 skills”，这句话在“发现层面”没问题；但从安全角度，你一定要补一句：

> **awesome 清单是目录，不是安全背书。安装前仍要把 Skill 当作第三方代码审查。**

为什么要这么强调？因为最近确实出现过针对 ClawHub 技能生态的恶意投放与供应链攻击报道：有技能伪装成生产力/加密工具，诱导用户运行混淆命令、下载恶意载荷，窃取凭据或敏感数据。

#### 给小白的一套“极简但有效”安全守则

1. **凡是让你复制粘贴一长串看不懂的终端命令：先停。**
2. **凡是索要助记词/私钥/浏览器密码/SSH key：直接拒绝。**
3. **能用最小权限 token 就别给全能 token；能用小号就别用主账号。**
4. **优先装“有清晰文档 + 维护活跃 + 社区使用信号强”的技能。**
5. 逛 ClawHub 网页时，建议开启 **Hide suspicious（隐藏可疑）**，并优先看 **Highlighted** 等更强信号的技能列表。([ClawHub](https://clawhub.ai/skills?nonSuspicious=true&utm_source=chatgpt.com))

### 5. 新手行动清单：

**今天就做 4 件事：**

1. 收藏 `VoltAgent/awesome-openclaw-skills`，先选 1 个场景（比如日程/任务）。([GitHub](https://github.com/VoltAgent/awesome-openclaw-skills/blob/main/README.md?utm_source=chatgpt.com))
2. 在清单里挑 2～3 个候选技能，做“30 秒体检”。
3. 安装 ClawHub CLI，用 `search → install` 装上其中 1 个。([Claw](https://docs.claw.so/engine/tools/clawhub/?utm_source=chatgpt.com))
4. 从此把技能当依赖管理：定期 `update --all`，但更新前先读说明。([OpenClaw](https://docs.openclaw.ai/tools/clawhub?utm_source=chatgpt.com))

## 7.3 定时任务

待补充

## 7.4 主从agent管理模式（进阶）

待补充

# 8.聊聊和openclaw 聊天的一些心得