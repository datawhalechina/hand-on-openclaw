# 常见安装问题排查

## 1. Git 拉取报 TLS / SSH 权限错误

现象示例：

```Plain
fatal: unable to access 'https://github.com/whiskeysockets/libsignal-node.git/': GnuTLS recv error (-110)

或者

git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
```

解决方式（在 Ubuntu/WSL 执行）：

```Plain
git config --global url."https://github.com/".insteadOf "git@github.com:"
git config --global url."https://github.com/".insteadOf "ssh://git@github.com/"
```

## 2. openclaw 安装阶段 npm 失败

现象示例：

```Plain
npm install failed for openclaw@latest
```

解决方式（在 Ubuntu/WSL 执行）：

```Plain
npm install -g openclaw@latest --registry=https://registry.npmmirror.com
```

## 3. 重新进入引导

```Plain
openclaw onboard
```
