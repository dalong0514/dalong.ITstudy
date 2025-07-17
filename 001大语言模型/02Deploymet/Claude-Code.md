## Claude-Code

### 文档

[Claude Code: Deep Coding at Terminal Velocity \ Anthropic](https://www.anthropic.com/claude-code)

[Claude Code 概述 - Anthropic](https://docs.anthropic.com/zh-CN/docs/claude-code/overview)

[Node.js — Download Node.js®](https://nodejs.org/en/download)

### 安装记录

通过 nvm 安装 node18 以上的版本，我用的是：v18.20.8。

然后安装 cc：

npm install -g @anthropic-ai/claude-code

启动 cc：

Claude

### 记录

用 kimi k2 大模型驱动 cc。

1、先在 shell 里设置代理：

export http_proxy=http://127.0.0.1:7890
export https_proxy=http://127.0.0.1:7890

$env:HTTP_PROXY = "http://127.0.0.1:7890"
$env:HTTPS_PROXY = "http://127.0.0.1:7890"

2、设置环境变量：

$env:ANTHROPIC_BASE_URL = "https://api.moonshot.cn/anthropic/"
$env:ANTHROPIC_AUTH_TOKEN="sk-"

export ANTHROPIC_BASE_URL=https://api.moonshot.cn/anthropic/

export ANTHROPIC_AUTH_TOKEN=sk-