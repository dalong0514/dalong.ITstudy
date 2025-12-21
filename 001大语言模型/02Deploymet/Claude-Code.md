## Claude-Code

### 文档

[Claude Code: Deep Coding at Terminal Velocity \ Anthropic](https://www.anthropic.com/claude-code)

[Claude Code 概述 - Anthropic](https://docs.anthropic.com/zh-CN/docs/claude-code/overview)

[Home - Anthropic](https://docs.anthropic.com/en/home)

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

deepseek 的配置：

.zshrc 文件里的内容：

官方新的配置说明：

\# Claude Code environment variables
export ANTHROPIC_BASE_URL=https://api.deepseek.com/anthropic
export ANTHROPIC_AUTH_TOKEN=${DEEPSEEK_API_KEY}
export API_TIMEOUT_MS=3000000
export ANTHROPIC_MODEL=deepseek-chat
export ANTHROPIC_SMALL_FAST_MODEL=deepseek-chat
export CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC=1



之前用的配置：

export ANTHROPIC_BASE_URL=https://api.deepseek.com/anthropic
export ANTHROPIC_AUTH_TOKEN=DEEPSEEK_API_KEY
export ANTHROPIC_MODEL=deepseek-chat
export ANTHROPIC_SMALL_FAST_MODEL=deepseek-chat
export CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC=1

export ANTHROPIC_MODEL=deepseek-reasoner
export ANTHROPIC_SMALL_FAST_MODEL=deepseek-chat

URL 和 key 的配置已经写到了 .zshrc 文件里。


$env:ANTHROPIC_BASE_URL="https://api.deepseek.com/anthropic"
$env:ANTHROPIC_AUTH_TOKEN="sk-"

$env:ANTHROPIC_MODEL="deepseek-chat"
$env:ANTHROPIC_SMALL_FAST_MODEL="deepseek-chat"

$env:ANTHROPIC_MODEL="deepseek-reasoner"
$env:ANTHROPIC_SMALL_FAST_MODEL="deepseek-chat"

ANTHROPIC_API_KEY

CLAUDE_CODE_MAX_OUTPUT_TOKENS
128000

---

minimax 的配置

[在 AI 编程工具里使用 M2 - MiniMax 开放平台文档中心](https://platform.minimaxi.com/docs/guides/text-ai-coding-tools)

[Coding Plan - MiniMax API 开放平台](https://platform.minimaxi.com/user-center/payment/coding-plan)

\# Claude Code environment variables
export ANTHROPIC_BASE_URL=https://api.minimaxi.com/anthropic
export ANTHROPIC_AUTH_TOKEN=<MINIMAX_API_KEY>
export API_TIMEOUT_MS=3000000
export ANTHROPIC_MODEL=MiniMax-M2
export ANTHROPIC_SMALL_FAST_MODEL=MiniMax-M2
export CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC=1

{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.minimaxi.com/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "<MINIMAX_API_KEY>",
    "API_TIMEOUT_MS": "3000000",
    "CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": 1,
    "ANTHROPIC_MODEL": "MiniMax-M2",
    "ANTHROPIC_SMALL_FAST_MODEL": "MiniMax-M2",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "MiniMax-M2",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "MiniMax-M2",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "MiniMax-M2"
  }
}


ANTHROPIC_BASE_URL 需根据地理位置设置：
国内用户使用 https://api.minimaxi.com/anthropic
国际用户使用 https://api.minimax.io/anthropic


---

豆包的配置：

[火山方舟管理控制台](https://console.volcengine.com/ark/region:ark+cn-beijing/apikey?apikey=%7B%7D)

[火山方舟管理控制台](https://console.volcengine.com/ark/region:ark+cn-beijing/openManagement?OpenModelVisible=false&tab=CodingPlan)

\# Claude Code environment variables
export ANTHROPIC_BASE_URL=https://ark.cn-beijing.volces.com/api/coding
export ANTHROPIC_AUTH_TOKEN=xx
export ANTHROPIC_MODEL=doubao-seed-code-preview-latest
export API_TIMEOUT_MS=3000000


ANTHROPIC_BASE_URL：https://ark.cn-beijing.volces.com/api/coding
ANTHROPIC_AUTH_TOKEN：获取API Key。
ANTHROPIC_MODEL: doubao-seed-code-preview-latest

vim ~/.claude/settings.json

{
    "env": {
        "ANTHROPIC_AUTH_TOKEN": "ARK_API_KEY",
        "ANTHROPIC_BASE_URL": "https://ark.cn-beijing.volces.com/api/coding",
        "API_TIMEOUT_MS": "3000000",
        "ANTHROPIC_MODEL": "doubao-seed-code-preview-latest"
    }
}


$env:ANTHROPIC_BASE_URL="https://ark.cn-beijing.volces.com/api/coding"
$env:ANTHROPIC_AUTH_TOKEN="xx"

$env:ANTHROPIC_MODEL="doubao-seed-code-preview-latest"
$env:ANTHROPIC_SMALL_FAST_MODEL="doubao-seed-code-preview-latest"



---

kimi 的配置：

export ANTHROPIC_BASE_URL=https://api.moonshot.cn/anthropic
export ANTHROPIC_AUTH_TOKEN=sk-


$env:ANTHROPIC_BASE_URL = "https://api.moonshot.cn/anthropic"
$env:ANTHROPIC_AUTH_TOKEN="sk-"
$env:ANTHROPIC_MODEL="kimi-k2-turbo-preview"
$env:ANTHROPIC_SMALL_FAST_MODEL="kimi-k2-turbo-preview"

---

GLM 的配置：

$env:ANTHROPIC_BASE_URL = "https://open.bigmodel.cn/api/anthropic"
$env:ANTHROPIC_AUTH_TOKEN="sk-"
$env:ANTHROPIC_MODEL="glm-4.5"
$env:ANTHROPIC_SMALL_FAST_MODEL="glm-4.5"
