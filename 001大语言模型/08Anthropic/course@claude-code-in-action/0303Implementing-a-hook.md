## 0303Implementing-a-hook

[Implementing a hook](https://anthropic.skilljar.com/claude-code-in-action/312003)

Let's put together our custom hook. Remember, the entire goal here is to prevent Claude from ever reading the contents of the .env file. In the last video, we discussed many of the different configuration options we'll need to set, so in this video, we're going to be mostly focused on the implementation.

我们来组装自定义钩子。请记住，这里的首要目标是阻止 Claude 读取 `.env` 文件的内容。在上一期视频中，我们讨论了许多需要设置的不同配置选项，因此本期视频将主要聚焦于具体的实现。

To get started, inside the `claude` directory, I'm going to open up the `settings.local.json` file. Remember, inside of here, we have a list of pre-tool use hooks and post-tool use hooks. As we discussed a moment ago, we want to make a pre-tool use hook so that we can prevent Claude from ever reading the contents of that particular file.

为了开始，我们先进入 `claude` 目录，然后打开 `settings.local.json` 这个文件。大家可能还记得，在这个文件里，我们定义了一系列「前工具使用钩子」（pre-tool use hooks）和「后工具使用钩子」（post-tool use hooks）。正如我们之前提到的，我们希望添加一个「前工具使用钩子」，这样就能有效阻止 Claude 读取这个特定文件的内容，从而保护信息的安全。

I already added in a little configuration section right here for us, just to save us a little bit of typing. All we need to do is fill in the `matcher` and the `command`. First is the `matcher`. So, the `matcher` is going to be the tools we want to watch for. In our case, as we discussed, we want to watch for calls to the `read` and the `grep` tools. I'm going to separate those two tool names with a pipe symbol. So that's not an 'l' or a capital 'i'. It is a symbol right above the return key on your keyboard.

我在这里已经添加了一个小的配置部分，只是为了省去一些打字麻烦。我们只需要填写 `matcher` 和 `command` 即可。首先是 `matcher`。`matcher` 将用于匹配我们想要监控的工具。在我们的例子中，正如我们之前讨论的，我们希望监控对 `read` 和 `grep` 工具的调用。我将用一个竖线符号（`|`）分隔这两个工具名称。请注意，它不是字母「l」或大写字母「i」，而是你键盘上回车键正上方的一个符号。

Next up, we need to provide a command to run whenever Claude attempts to call those two tools. We can put in here any command you want, so it can be a CLI, it can be a call to a shell script, absolutely anything. To follow the pattern that I've already established inside the rest of this file, I'm going to call a Node.js script that I placed ahead of time inside the `hooks` directory of this project. So, inside the `hooks` directory, I put together for us a `read_hook.js` file. This is the file that I want to run whenever Claude attempts to call one of those two tools. So, to call that, I'm going to replace the `true` right here, which is just a placeholder for right now, with `node ./hooks/read_hook.js`.

接下来，我们需要提供一个命令，当 Claude 尝试调用这两个工具时运行。你可以在这里放入任何你想要的命令，它可以是一个命令行接口（CLI），也可以是对 shell 脚本的调用，总之是任何可执行的命令。为了遵循我在文件其余部分已确立的模式，我将调用一个 Node.js 脚本，该脚本我已预先放置在项目的 `hooks` 目录中。因此，在 `hooks` 目录中，我为大家编写了一个 `read_hook.js` 文件。这个文件就是我希望当 Claude 尝试调用这两个工具之一时运行的。所以，为了调用它，我将把此处作为占位符的 `true` 替换为 `node ./hooks/read_hook.js`。

I'm going to save this file and that's all we have to do inside of here. Next up, we need to actually implement the command that's going to run anytime Claude tries to call the `read` or the `grep` tools. So, that's going to be the `read_hook.js` file. At the top of this file, I've got some code that's going to read from standard in and parse that data as JSON. So, this `tool_args` object right here, that's going to be the big JSON object I showed you in this diagram back over here. So, it's going to have properties like `session_id`, the `tool_name`, the `tool_input`, and so on.

我将保存这个文件，这就是我们在这里需要做的全部。接下来，我们需要实际实现一个命令，这个命令会在 Claude 尝试调用 `read` 或 `grep` 工具时运行。这个命令就是 `read_hook.js` 文件。在这个文件的顶部，我写了一些代码，它们会从标准输入读取数据，并将其解析为 JSON 格式。所以，这里提到的 `tool_args` 对象，就是我之前在图表中展示过的那个大型 JSON 对象。它会包含 `session_id`、`tool_name`、`tool_input` 等属性。

So, all we really need to do is take a look at that file path right there and decide whether or not it is trying to read the `.env` file. If it is, then we want to make sure that we exit from our program or our command here with an exit code of 2 and hopefully also log some information out to Claude that says, "Sorry, but you can't read that file." So, you'll notice that back over here, I've already got some code that's going to read that file path. You'll also notice that there's a fallback of looking at `tool_input_path` right here. I'll tell you why that's added in in just a moment.

所以，我们真正需要做的就是检查那个文件路径，然后判断它是否在尝试读取 `.env` 文件。如果答案是肯定的，那么我们就要确保我们的程序或命令以退出代码 2 退出，并且最好也能向 Claude 输出一些信息，提示：「抱歉，您无法读取该文件。」因此，您会注意到，回顾一下，我这里已经有一些代码可以读取该文件路径了。您还会发现，这里有一个备用方案，即检查 `tool_input_path`。稍后我将解释为何会加入这个备用方案。

So, now let's implement the TODO statement. We'll say, "if `read_path` includes `.env`." That means that Claude must be trying to read the `.env` file. And if that's the case, then I want to make sure that we block that operation and provide some logging feedback to Claude. So, I'm going to first add in a `console.error`, specifically a `console.error`, because we want to log to standard error. Remember, that's how we provide some feedback to Claude. And I'll say something like, "You cannot read the .env file." And then I'll do a `process.exit(2)`.

所以，现在我们来实现 TODO 语句。我们会写，「如果 `read_path` 包含 `.env`。」这意味着 Claude 肯定正在尝试读取 `.env` 文件。如果确实如此，那么我希望确保我们阻止该操作，并向 Claude 提供日志反馈。所以，我将首先添加 `console.error`，具体来说，是 `console.error`，因为我们希望记录到标准错误。请记住，这就是我们向 Claude 提供反馈的方式。我们将打印类似「您无法读取 .env 文件」的错误信息。然后我将执行 `process.exit（2)`。

So, now to test this out, I'm going to save the file. I'm going to open up Claude Code. If you already have it open, make sure you restart Claude Code. You have to restart it to have any changes to your hooks take effect. I'm going to ask Claude to read the `.env` file. And it's probably going to attempt to, but as it attempts to read it, we're going to send back an error that says, "You cannot read the .env file." And Claude's hopefully going to realize that, "Sorry, you can't actually read this." As a matter of fact, it's even able to recognize that it was prevented by a read hook.

现在，为了测试这个功能，我将保存文件并打开 Claude Code。如果你已经打开了 Claude Code，请务必重启它，因为任何对钩子（hooks）的更改都需要重启后才能生效。我将让 Claude 尝试读取 `.env` 文件。它可能会尝试执行此操作，但当它尝试读取时，我们将返回一个错误信息，提示：「你不能读取 .env 文件。」Claude 应该会意识到「抱歉，你实际上无法读取此文件。」事实上，它甚至能够识别出其读取操作是被一个读取钩子阻止的。

Now, our hook should also be working on `grep` operations as well. So, if I ask Claude to try the `grep` tool, this should also hopefully be forbidden as well. So, let's see how it does. And yep, same thing. It is now forbidden. So, that is a working hook that we have put together. Now, this hook is not terribly useful. And I'm going to show you a much more useful hook in just a moment. Thank you, thank you, thank you, thank you, thank you.

现在，我们的「钩子」（hook）也应该对 `grep` 操作生效。因此，如果我让 Claude 尝试使用 `grep` 工具，它也应该被禁止。那么，我们来看看实际效果如何。是的，结果如预期，它现在被禁止了。这表明我们部署的钩子已经成功运行。当然，这个钩子并不是特别有用。稍后，我将向大家展示一个更实用的钩子。

## 页面文档

Let's build a custom hook to prevent Claude from reading sensitive files like .env. This is a practical example of how hooks can protect your environment variables and other confidential data during development sessions.

接下来，我们将创建一个自定义 hook（custom hook），以防止 AI 模型 Claude 读取诸如 .env 文件等敏感信息。这是一个非常实用的案例，它能向你展示 hook 如何在开发会话期间有效地保护你的环境变量（environment variables）和其他机密数据。

### Setting Up the Hook Configuration

配置「钩子」（Hook）

First, we need to configure our hook in the settings file. Open your .claude/settings.local.json file and locate the hooks section. We'll create a PreToolUse hook since we want to intercept tool calls before they execute.

首先，我们需要在设置文件中配置我们的钩子（hook）。打开您的 `.claude/settings.local.json` 文件，并找到 `hooks` 配置项。我们将在这里创建一个「PreToolUse」钩子（hook），因为我们希望在工具调用实际执行之前就对其进行拦截。

The configuration requires two key pieces:

这项配置包含两个关键要素：

1 Matcher - specifies which tools to watch for

匹配器（Matcher）- 用于指定需要监控哪些工具

2 Command - the script that runs when those tools are called

命令（Command）- 当这些工具被调用时执行的脚本

For the matcher, we want to catch both read and grep operations that might access the .env file:

对于匹配器，我们希望它能够捕获所有可能访问 .env 文件的读取操作和 grep 操作：

"matcher": "Read|Grep"

The pipe symbol (|) acts as an OR operator, so this will trigger on either tool. For the command, we'll point to a Node.js script:

管道符号（|）充当一个逻辑或（OR）运算符，因此这将在这两个工具中的任何一个被调用时触发。对于命令，我们将指定一个 Node.js 脚本：

"command": "node ./hooks/read_hook.js"

### Understanding Tool Call Data

理解工具调用数据

When Claude attempts to use a tool, your hook receives detailed information about that call through standard input as JSON. This data includes:

当 Claude 尝试使用一个工具时，你的钩子会通过标准输入，以 JSON 格式接收关于该调用的详细信息。这些数据包括：

Session ID and transcript path
Hook event name (PreToolUse in our case)
Tool name (Read, Grep, etc.)
Tool input parameters, including the file path

会话 ID 和转录路径
钩子事件名称（PreToolUse 在我们的例子中）
工具名称（例如 Read、Grep 等）
工具输入参数，包括文件路径

Your hook script processes this data and can either allow the operation to continue or block it by exiting with a specific code.

你的钩子脚本会处理这些数据，并通过退出并返回特定代码，来允许操作继续执行，或者阻止操作。

Implementing the Hook Script

实现钩子脚本（Hook Script）

The hook script needs to read the tool call data from standard input and check if Claude is trying to access the .env file. Here's the core logic:

这个钩子脚本（hook script）需要从标准输入中读取工具调用的相关数据，并检查 Claude 是否试图访问 .env 文件。其核心逻辑如下：

```js
async function main() {
  const chunks = [];
  for await (const chunk of process.stdin) {
    chunks.push(chunk);
  }
  
  const toolArgs = JSON.parse(Buffer.concat(chunks).toString());
  
  // Extract the file path Claude is trying to read
  const readPath = 
    toolArgs.tool_input?.file_path || toolArgs.tool_input?.path || "";
  
  // Check if Claude is trying to read the .env file
  if (readPath.includes('.env')) {
    console.error("You cannot read the .env file");
    process.exit(2);
  }
}
```

The script checks for .env in the file path and blocks the operation if found. When you exit with code 2, Claude receives an error message and understands the operation was blocked by a hook.

这个脚本会检查文件路径里有没有 .env 文件，如果找到了，就会立刻阻止后续操作。当脚本以退出码 2（表示异常终止）结束运行时，Claude 就会收到一条错误信息，并明白这次操作是被某个「钩子」（hook，一种预设的拦截机制）给阻止了。

### Testing Your Hook

测试你的 Hook

After saving your configuration and hook script, restart Claude Code for the changes to take effect. Then test it by asking Claude to read your .env file.

保存好你的配置和 hook 脚本后，请重启 Claude Code，这样改动才能生效。然后，你可以通过让 Claude 读取你的 .env 文件来测试它是否正常工作。

When Claude attempts the read operation, your hook will intercept it and return an error message. Claude will recognize that the operation was blocked and explain this to you, often mentioning that a read hook prevented access to the file.

当 Claude 尝试进行读取操作时，你的 hook（钩子）会拦截它并返回一条错误消息。Claude 会意识到该操作已被阻止，并向你解释这一情况，通常会提及是读取 hook 阻止了它访问该文件。

The same protection works for grep operations - if Claude tries to search within the .env file, the hook will block that as well.

同样的保护也对 grep 操作有效 —— 如果 Claude 试图在 .env 文件中搜索，该钩子（hook）同样会阻止它。

### Key Benefits

This approach provides several advantages:

主要优点这种方法带来了以下几点优势：

Proactive protection - blocks access before sensitive data is read
Transparent operation - Claude understands why the operation failed
Flexible matching - works with multiple tools (read, grep, etc.)
Clear feedback - provides meaningful error messages

主动保护 - 在读取敏感数据之前就阻止对其的访问
透明操作 - Claude 能够理解操作失败的原因
灵活匹配 - 适用于多种工具，例如 read、grep 等
清晰反馈 - 提供有意义的错误消息

While this specific example focuses on .env files, the same pattern can protect any sensitive files or directories in your project. You can extend the logic to check for multiple file patterns or implement more sophisticated access controls based on your security requirements.

虽然这个具体的例子侧重于 .env 文件，但相同的模式可以保护你项目中的任何敏感文件或目录。你可以扩展此逻辑来检查多个文件模式，或根据你的安全要求实现更复杂的访问控制。
