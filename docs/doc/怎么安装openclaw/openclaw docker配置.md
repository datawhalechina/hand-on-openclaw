# OpenClaw（小龙虾）Docker 部署配置文档

> 标签：`API配置：有` `环境：本地` `安全性：高` `IM接入：飞书`

## 一、环境信息

| 项目   | 值                              |
| ------ | ------------------------------- |
| 镜像   | `1186258278/openclaw-zh:latest` |
| 容器名 | `openclaw`                      |
| 端口   | `127.0.0.1:18789` (仅本地访问)  |
| 模型   | 智谱 GLM-5                      |
| 渠道   | 飞书                            |

---

## 二、配置文件位置

```
~/.openclaw/
├── openclaw.json      # 主配置文件
├── .env               # 敏感信息（API Key等）
└── workspace/         # 工作区目录
```

---

## 三、主配置文件 (`openclaw.json`)

```json
{
  "models": {
    "mode": "merge",
    "providers": {
      "zhipu": {
        "baseUrl": "https://open.bigmodel.cn/api/paas/v4",
        "apiKey": "${ZHIPU_API_KEY}",
        "api": "openai-completions",
        "models": [
          {
            "id": "glm-5",
            "name": "GLM-5",
            "reasoning": false,
            "input": ["text"],
            "cost": { "input": 0, "output": 0 },
            "contextWindow": 131072,
            "maxTokens": 16384
          }
        ]
      }
    }
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "zhipu/glm-5"
      }
    }
  },
  "gateway": {
    "bind": "lan",
    "port": 18789,
    "mode": "local",
    "auth": {
      "mode": "token",
      "rateLimit": {
        "maxAttempts": 10,
        "windowMs": 60000,
        "lockoutMs": 300000
      }
    }
  },
  "channels": {
    "feishu": {
      "enabled": true,
      "appId": "${FEISHU_APP_ID}",
      "appSecret": "${FEISHU_APP_SECRET}",
      "mentionMode": "all",
      "allowlist": ["<你的飞书用户ID>"]
    }
  },
  "messages": {
    "ackReactionScope": "all"
  }
}
```

---

## 四、环境变量文件 (`.env`)

```env
ZHIPU_API_KEY=<你的智谱API密钥>
FEISHU_APP_ID=<你的飞书APP_ID>
FEISHU_APP_SECRET=<你的飞书AppSecret>
```

---

## 五、完整安装步骤

### 5.1 前置要求

- Windows 10/11 或 Linux
- 智谱 API Key
- 飞书开放平台应用（App ID 和 App Secret）

### 5.2 安装 Docker Desktop

#### Windows

1. 下载 Docker Desktop：https://www.docker.com/products/docker-desktop/
2. 运行安装程序，按提示完成安装
3. 安装完成后重启电脑
4. 启动 Docker Desktop，等待其运行

#### 验证 Docker 安装

```powershell
docker --version
docker ps
```

### 5.3 清理旧的 OpenClaw 安装（如果有）

```powershell
# 查看现有 OpenClaw 容器
docker ps -a | findstr openclaw

# 停止并删除旧容器
docker stop openclaw
docker rm openclaw

# 删除旧镜像（可选）
docker images | findstr openclaw
docker rmi <镜像ID>
```

### 5.4 创建配置目录

```powershell
# 创建配置目录
New-Item -ItemType Directory -Path "$env:USERPROFILE\.openclaw" -Force
New-Item -ItemType Directory -Path "$env:USERPROFILE\.openclaw\workspace" -Force
```

### 5.5 创建环境变量文件

```powershell
# 创建 .env 文件
@"
ZHIPU_API_KEY=<你的智谱API密钥>
FEISHU_APP_ID=<你的飞书APP_ID>
FEISHU_APP_SECRET=<你的飞书AppSecret>
"@ | Out-File -FilePath "$env:USERPROFILE\.openclaw\.env" -Encoding utf8
```

### 5.6 创建主配置文件

```powershell
# 创建 openclaw.json
@"
{
  "models": {
    "mode": "merge",
    "providers": {
      "zhipu": {
        "baseUrl": "https://open.bigmodel.cn/api/paas/v4",
        "apiKey": "`${ZHIPU_API_KEY}",
        "api": "openai-completions",
        "models": [
          {
            "id": "glm-5",
            "name": "GLM-5",
            "reasoning": false,
            "input": ["text"],
            "cost": { "input": 0, "output": 0 },
            "contextWindow": 131072,
            "maxTokens": 16384
          }
        ]
      }
    }
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "zhipu/glm-5"
      }
    }
  },
  "gateway": {
    "bind": "lan",
    "port": 18789,
    "mode": "local",
    "auth": {
      "mode": "token",
      "rateLimit": {
        "maxAttempts": 10,
        "windowMs": 60000,
        "lockoutMs": 300000
      }
    }
  },
  "channels": {
    "feishu": {
      "enabled": true,
      "appId": "`${FEISHU_APP_ID}",
      "appSecret": "`${FEISHU_APP_SECRET}",
      "mentionMode": "all",
      "allowlist": ["<你的飞书用户ID>"]
    }
  },
  "messages": {
    "ackReactionScope": "all"
  }
}
"@ | Out-File -FilePath "$env:USERPROFILE\.openclaw\openclaw.json" -Encoding utf8
```

### 5.7 拉取 OpenClaw Docker 镜像

OpenClaw 中文版已经打包成 Docker 镜像，无需手动安装，直接拉取即可：

```powershell
# 拉取中文版镜像（推荐）
docker pull 1186258278/openclaw-zh:latest

# 或者拉取官方原版镜像
# docker pull openclawai/openclaw:latest
```

> 注意：镜像内已预装 OpenClaw 及所有依赖，无需额外安装。

#### 可选：自己构建镜像

如果需要自定义镜像，可以创建 Dockerfile：

```dockerfile
FROM node:22-bookworm

# 安装 OpenClaw 中文版
RUN npm install -g openclaw-cn@latest

WORKDIR /root/workspace

# 创建配置目录
RUN mkdir -p /root/.openclaw
ENV OPENCLAW_CONFIG=/root/.openclaw

EXPOSE 18789

CMD ["openclaw-cn", "gateway", "--port", "18789", "--allow-unconfigured"]
```

构建并运行：

```powershell
# 构建镜像
docker build -t openclaw-custom:latest .

# 运行容器
docker run -d --name openclaw -p 127.0.0.1:18789:18789 `
  -v "$env:USERPROFILE\.openclaw:/root/.openclaw" `
  openclaw-custom:latest
```

### 5.8 启动 OpenClaw 容器

```powershell
docker run -d \
  --name openclaw \
  -p 127.0.0.1:18789:18789 \
  --env-file "$env:USERPROFILE\.openclaw\.env" \
  -v "$env:USERPROFILE\.openclaw:/root/.openclaw" \
  -v "$env:USERPROFILE\.openclaw\workspace:/root/workspace" \
  --restart=always \
  1186258278/openclaw-zh:latest \
  openclaw gateway --port 18789 --allow-unconfigured
```

### 5.9 设置容器自动重启

```powershell
docker update --restart=always openclaw
```

### 5.10 获取访问地址

```powershell
# 等待容器启动完成
Start-Sleep -Seconds 5

# 获取带 Token 的控制台地址
docker exec openclaw openclaw dashboard --no-open
```

### 5.11 批准设备配对

```powershell
# 查看待配对设备
docker exec openclaw openclaw devices list

# 批准配对（替换 <requestId> 为实际 ID）
docker exec openclaw openclaw devices approve <requestId>
```

### 5.12 配置飞书并批准用户配对

1. 在飞书给机器人发一条消息
2. 查看并批准配对：

```powershell
# 查看待配对飞书用户
docker exec openclaw openclaw pairing list

# 批准配对（替换 <code> 为实际配对码）
docker exec openclaw openclaw pairing approve <code>
```

### 5.13 禁用电脑休眠（可选，保持 24/7 运行）

```powershell
powercfg /change standby-timeout-ac 0
powercfg /change hibernate-timeout-ac 0
```

---

## 六、安全配置

| 安全措施   | 说明                                       |
| ---------- | ------------------------------------------ |
| 端口绑定   | `127.0.0.1:18789` 仅本地访问，公网无法连接 |
| 敏感信息   | 使用环境变量存储，不明文写入配置文件       |
| 用户白名单 | 仅允许指定飞书用户 ID 使用                 |
| 认证限流   | 10 次失败后锁定 5 分钟，防止暴力破解       |
| 容器隔离   | 使用 Docker 容器隔离运行环境               |

---

## 七、飞书开放平台配置

### 7.1 必需权限

在 [飞书开放平台](https://open.feishu.cn/app/<你的飞书APP_ID>/auth) 添加以下权限：

| 权限                            | 说明                     |
| ------------------------------- | ------------------------ |
| `im:message`                    | 获取与发送单聊、群组消息 |
| `im:message:send_as_bot`        | 以应用身份发送消息       |
| `contact:contact.base:readonly` | 获取通讯录基本信息       |

### 7.2 事件订阅

在「事件与回调」中配置：

- 订阅方式：**使用长连接接收事件/回调**
- 添加事件：`im.message.receive_v1`

### 7.3 发布应用

权限修改后必须**创建新版本并发布**才能生效。

---

## 八、常用命令

### 8.1 容器管理

```powershell
# 查看容器状态
docker ps

# 查看日志
docker logs openclaw -f --tail 50

# 重启网关
docker restart openclaw

# 停止容器
docker stop openclaw

# 启动容器
docker start openclaw
```

### 8.2 OpenClaw 命令

```powershell
# 获取控制台地址（带Token）
docker exec openclaw openclaw dashboard --no-open

# 查看状态
docker exec openclaw openclaw status

# 查看飞书渠道状态
docker exec openclaw openclaw channels status

# 设备配对列表
docker exec openclaw openclaw devices list

# 批准设备配对
docker exec openclaw openclaw devices approve <requestId>

# 飞书用户配对列表
docker exec openclaw openclaw pairing list

# 批准飞书用户配对
docker exec openclaw openclaw pairing approve <code>

# 诊断问题
docker exec openclaw openclaw doctor

# 进入终端界面
docker exec -it openclaw openclaw tui
```

---

## 九、故障排查

### 9.1 飞书不回复消息

1. 检查日志：`docker logs openclaw --tail 50`
2. 常见原因：
   - 飞书权限未添加或未发布
   - 用户未通过配对审批
   - 模型 API 调用失败

### 9.2 无法访问控制台

1. 确认容器运行：`docker ps`
2. 获取带 Token 的地址：`docker exec openclaw openclaw dashboard --no-open`
3. 确认网关绑定 `0.0.0.0`（配置中 `gateway.bind: "lan"`）

### 9.3 配对问题

```powershell
# 查看待配对设备
docker exec openclaw openclaw devices list

# 查看待配对飞书用户
docker exec openclaw openclaw pairing list

# 批准配对
docker exec openclaw openclaw devices approve <id>
docker exec openclaw openclaw pairing approve <code>
```

---

## 十、重要链接

| 资源              | 地址                                         |
| ----------------- | -------------------------------------------- |
| 本地控制台        | http://127.0.0.1:18789                       |
| 飞书开放平台      | https://open.feishu.cn/app/<你的飞书 APP_ID> |
| OpenClaw 官方文档 | https://docs.openclaw.ai                     |
| OpenClaw 中文版   | https://openclaw.qt.cool                     |
