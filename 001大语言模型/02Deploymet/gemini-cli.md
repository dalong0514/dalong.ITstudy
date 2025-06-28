### 安装相关

[google-gemini/gemini-cli: An open-source AI agent that brings the power of Gemini directly into your terminal.](https://github.com/google-gemini/gemini-cli?tab=readme-ov-file)

[Node.js — Download Node.js®](https://nodejs.org/en/download)

[快速入门：安装 Google Cloud CLI  |  Google Cloud SDK Documentation](https://cloud.google.com/sdk/docs/install-sdk?hl=zh-cn)

[快速入门：安装 Google Cloud CLI  |  Google Cloud SDK Documentation](https://cloud.google.com/sdk/docs/install-sdk?hl=zh-cn#windows)

还是需要先安装 Google Cloud CLI



跑 gemini 的步骤

mac 上：

先设置终端的代理：

export http_proxy=http://127.0.0.1:7890
export https_proxy=http://127.0.0.1:7890

然后直接命令：gemini




window 上：

$env:HTTP_PROXY = "http://127.0.0.1:7890"
$env:HTTPS_PROXY = "http://127.0.0.1:7890"


gen-lang-client-0760690769

export GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
$env:GEMINI_API_KEY="gen-lang-client-0760690769"

### 问题汇总

1、无法验证登录。

最终的解决方案源自 ChatGPT 的解答。

export http_proxy=http://127.0.0.1:7890
export https_proxy=http://127.0.0.1:7890


你也可以将上述命令添加到 ~/.bashrc 或 ~/.zshrc 文件中，以便每次终端启动时自动设置。


echo 'export http_proxy=http://127.0.0.1:7890' >> ~/.zshrc
echo 'export https_proxy=http://127.0.0.1:7890' >> ~/.zshrc
source ~/.bashrc


为了方便开启和关闭代理，可以定义别名：

function proxy_on() {
  export http_proxy="http://127.0.0.1:7890"
  export https_proxy="http://127.0.0.1:7890"
  echo "代理已开启"
}

function proxy_off() {
  unset http_proxy
  unset https_proxy
  echo "代理已关闭"
}





---

[gemini-cli/docs/cli/authentication.md at main · google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/authentication.md#workspace-gca)

gcloud auth login
Your browser has been opened to visit:

    https://accounts.google.com/o/oauth2/auth?response_type=code&client_id=32555940559.apps.googleusercontent.com&redirect_uri=http%3A%2F%2Flocalhost%3A8085%2F&scope=openid+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fuserinfo.email+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fcloud-platform+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fappengine.admin+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fsqlservice.login+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fcompute+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Faccounts.reauth&state=G6teEkfg3rdyIBYP8L6gkCzPKeWxO4&access_type=offline&code_challenge=yW7g-66Rr0XXeqJsGSI8plzJPnVsUhlwNuNk08h0mGw&code_challenge_method=S256


You are now logged in as [daglas0514@gmail.com].
Your current project is [gen-lang-client-0760690769].  You can change this setting by running:
  $ gcloud config set project PROJECT_ID