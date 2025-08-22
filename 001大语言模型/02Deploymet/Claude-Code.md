## Claude-Code

### 文档

[Claude Code: Deep Coding at Terminal Velocity \ Anthropic](https://www.anthropic.com/claude-code)

[Claude Code 概述 - Anthropic](https://docs.anthropic.com/zh-CN/docs/claude-code/overview)

[Node.js — Download Node.js®](https://nodejs.org/en/download)

### 安装记录

通过 nvm 安装 node18 以上的版本，我用的是：v18.20.8。

对于 window 系统，因为数智设计用的是 v16，需要切换到 v18。

nvm use v18

然后安装 cc：

npm install -g @anthropic-ai/claude-code

备注：对于 window 系统，安装的时候需要用管理员模式打开 powershell，在里面安装。

启动 cc：

Claude

### 记录

用 DeepSeek 大模型驱动 cc。

1、先在 shell 里设置代理：

export http_proxy=http://127.0.0.1:7890
export https_proxy=http://127.0.0.1:7890

对于 window，需要在 powershell 里执行。

$env:HTTP_PROXY = "http://127.0.0.1:7890"
$env:HTTPS_PROXY = "http://127.0.0.1:7890"

2、设置环境变量：

export ANTHROPIC_BASE_URL=https://api.deepseek.com/anthropic
export ANTHROPIC_AUTH_TOKEN=DEEPSEEK_API_KEY
export ANTHROPIC_MODEL=deepseek-chat
export ANTHROPIC_SMALL_FAST_MODEL=deepseek-chat


export ANTHROPIC_MODEL=deepseek-reasoner
export ANTHROPIC_SMALL_FAST_MODEL=deepseek-chat

URL 和 key 的配置已经写到了 .zshrc 文件里。


$env:ANTHROPIC_BASE_URL = "https://api.deepseek.com/anthropic"
$env:ANTHROPIC_AUTH_TOKEN="sk-"
$env:ANTHROPIC_MODEL="deepseek-chat"
$env:ANTHROPIC_SMALL_FAST_MODEL="deepseek-chat"


---

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