# 多模型与 Provider 配置

## 多 LLM 模型配置

和初次配置一样，打开ubuntu的命令行界面，输入：`openclaw onboard`，然后配置好其他模型即可。（详细步骤见第三节 openclaw配置部分）

![img](../../img/5-1.png)

不过有个问题，配好后会变成你的默认模型，如果你想调整该怎么做？

这里面推荐大家使用命令修改，输入：`code ~/.openclaw/openclaw.json` 接着你的代码编辑工具会自动打开配置文件。（推荐大家使用Vs code 如果没有Vs code请自行下载~）

比如我这里使用了kimi和minimax两个计划的模型，我想选minimax，在agents->defaults这里的primary将下面的模型名称复制过来就行

![img](../../img/5-2.png)

### API 中转平台配置（以 Claude Opus 4.6 为例）

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

1. **在****`.openclaw/openclaw.json`****注册 provider**

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

1. 重启gateway

```Plain
openclaw gateway restart
```


