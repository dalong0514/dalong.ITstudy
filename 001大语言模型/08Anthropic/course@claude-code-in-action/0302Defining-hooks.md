## 0302Defining-hooks

[Defining hooks](https://anthropic.skilljar.com/claude-code-in-action/312002)

To get a better idea of how hooks work, we're going to take a look at a new sample project. Attached to this lecture is a file called queries.zip. I'd encourage you to download this project and open your code editor inside it. Once you've got your editor open, at your terminal, run `Anfium run setup`. This is going to install a couple of dependencies and get a couple of hooks ready for use.

为了更好地理解 hook（钩子）的工作原理，我们将进行一个新的示例项目。本次讲座附带了一个名为 queries.zip 的文件。我建议你下载这个项目，并在其中打开你的代码编辑器。打开编辑器后，请在终端运行 `Anfium run setup`。这会安装一些必要的依赖项，并为 hook 的使用做好准备。

To better understand hooks, we're going to make our own inside this project. So here's what I want our hook to do. Inside the root directory of our project is a file called `.env`. This file contains some sensitive information, and out of an abundance of caution, I want to completely prevent Claude from ever reading this file directly.

为了更好地理解 hook（钩子），我们将在本项目中创建自己的 hook。那么，我希望我们的 hook 实现什么功能呢？在我们项目的根目录中有一个名为 `.env` 的文件。这个文件包含一些敏感信息，出于非常谨慎的考虑，我希望完全阻止 Claude 直接读取这个文件。

Let me show you a couple of diagrams to help you understand how we're going to put this hook together. Step one is to decide on whether we need a pre-tool use or a post-tool use hook. In this scenario, we want to prevent Claude from ever reading a particular file. If we make a post-tool use block, then we will have executed our hook or ran our command after Claude already read the file. So in this case, we definitely need a pre-tool use hook to make sure that we can prevent the read operation from occurring.

让我向您展示几个图表，以帮助您理解我们将如何设置这个钩子。第一步是决定我们是需要一个工具使用前置钩子还是工具使用后置钩子。在这种场景中，我们希望阻止 Claude 读取某个特定文件。如果我们设置一个工具使用后的块，那么我们将在 Claude 已经读取文件后才执行我们的钩子或运行我们的命令。所以在这种情况下，我们绝对需要一个工具使用前置钩子来确保我们能够阻止读取操作。

The next thing we need to do is decide exactly which kind of tool calls we want to watch for. I've got a list of all the different current tool names on the right-hand side of this diagram. Now, memorizing all the different tool names that are included inside of Claude code can be really challenging, especially since you can add your own custom tools through the use of MCP servers. So let me show you a little trick you can use here.

接下来，我们需要明确决定要关注哪种工具调用。在这个图表的右侧，我列出了所有当前不同的工具名称。不过，要记住 Claude 代码中包含的所有工具名称可能确实很有挑战性，特别是你还可以通过使用 MCP 服务器来添加自己的自定义工具。所以，让我在这里向你展示一个实用的小技巧。

If I go back over and open up Claude Code, I can directly ask Claude for a bullet-point list of all different tool names that it has access to right now. Out of all these different tools, there are two that can be used to very easily read the contents of a file. First, there's the `read` tool, and it's easy to miss, but this one can actually read the contents of a file as well: the `grep` tool. `grep` can search the contents of a file. So we really want to watch for tool calls for the `read` tool and the `grep` tool.

如果我返回并打开 Claude Code，我可以直接向 Claude 询问一份项目符号列表，列出它目前可以访问的所有不同工具名称。在这些工具中，有两种工具可以非常轻松地读取文件内容。首先是 `read` 工具。另一个容易被忽略但同样能用于读取文件内容的工具是 `grep` 工具。`grep` 可以搜索文件内容，因此在某种意义上也能「读取」。所以，我们需要特别关注对 `read` 工具和 `grep` 工具的调用。

Next up, we need to write out a command that is going to receive some information about the tool call that Claude wants to make. Here's how that part works: We're going to write out a command. Claude is going to automatically execute it, and then on standard in to that process, Claude is going to feed in some tool call data as JSON. I've got an example of some tool call data on the top right-hand side. So it's going to be a big JSON object that has some information about the tool name and the input to that tool. In this case, the tool name is `read`, so Claude is trying to call the `read` tool and might be trying to read specifically a file path pointing to that `.env` file. And again, that's the file that we want to prevent a read operation for. So then, inside of our program or our command, we need to receive this information through standard in, parse that JSON, and then read the tool name, the tool input arguments, and so on, and decide what we want to do with this tool call.

接下来，我们需要编写一个命令，该命令将接收 Claude 想要进行的工具调用（tool call）相关信息。这部分的工作方式是：我们将编写一个命令，Claude 会自动执行它，然后通过该进程的标准输入（standard in），Claude 将以 JSON 格式提供一些工具调用数据。我这里有一个工具调用数据的示例。它将是一个大型 JSON 对象，其中包含工具名称和该工具的输入信息。在这种情况下，工具名称是 `read`，这意味着 Claude 正在尝试调用 `read` 工具，并且可能正在尝试读取指向 `.env` 文件的文件路径。再次强调，这个文件是我们希望阻止读取操作的。因此，在我们的程序或命令中，我们需要通过标准输入接收这些信息，解析该 JSON，然后读取工具名称、工具输入参数等，并决定我们想如何处理这个工具调用。

Then, on to step four. In step four, after our command receives that proposed tool call data, we're then going to exit, and our exit code is going to provide feedback back to Claude. An exit code of zero means everything is okay, and we want to allow this tool call to occur. An exit code of two, however, is assigned to Claude code that we want to block this tool call. And that specifically only applies for the pre-tool use hooks, because remember, only on a pre-tool use hook can we actually block a tool call. If we exit with a code of two, then any standard error logs that we generated inside of our command during that time will also be sent as feedback to Claude. So we can both deny the tool call and give Claude a reason at the same time as well.

接下来，我们进入第四步。在这一步中，当我们的命令接收到提议的工具调用数据后，程序将退出。此时，程序的退出代码（exit code）会向 Claude 提供反馈。如果退出代码为零，则表示一切正常，我们允许这次工具调用继续进行。然而，如果退出代码为二，则表明我们希望阻止这次工具调用。需要注意的是，这种阻止工具调用的功能仅适用于「预工具使用钩子（pre-tool use hooks）」，因为只有在「预工具使用钩子」阶段，我们才能真正地阻止一次工具调用。如果程序以退出代码二退出，那么在此期间命令内部生成的任何标准错误日志（standard error logs）也将作为反馈发送给 Claude。这样一来，我们既可以拒绝工具调用，同时也能向 Claude 解释拒绝的原因。

So that's the entire process. And I know, once again, there's a lot of stuff going on here. So let's go through this entire process of wiring everything up needed for this hook inside of our project to understand how all these steps come together.

这就是整个过程。我知道，这里涉及的内容很多。所以接下来，让我们完整地走一遍在项目中将这个「钩子」（hook）所需的一切都连接起来的流程，从而理解这些步骤是如何协同工作的。

## 页面文档

Hooks in Claude Code allow you to intercept and control tool calls before or after they execute. This gives you fine-grained control over what Claude can and cannot do in your development environment.

在 Claude Code 中，**Hooks**（钩子）允许你在工具调用（tool calls）执行之前或之后进行拦截和控制。这为你提供了**细粒度控制**（fine-grained control），让你能够精确地掌控 Claude 在你的开发环境中可以执行或禁止执行的操作。

### Building a Hook

构建 Hook 机制

Creating a hook involves four main steps:

要创建一个 hook（钩子）机制，通常需要四个主要步骤：

1 Decide on a PreToolUse or PostToolUse hook - PreToolUse hooks can prevent tool calls from executing, while PostToolUse hooks run after the tool has already been used

确定 Hook 类型：你需要决定是使用 PreToolUse hook（在工具调用执行前触发的钩子）还是 PostToolUse hook（在工具已被使用后运行的钩子）。PreToolUse hook 能够阻止工具调用执行，而 PostToolUse hook 则在工具完成操作后发挥作用。

2 Determine which type of tool calls you want to watch for - You need to specify exactly which tools should trigger your hook

明确监控目标：指定你希望哪些工具调用来触发你的 hook。你需要精确地定义哪些工具的操作会激活这个钩子。

3 Write a command that will receive the tool call - This command gets JSON data about the proposed tool call via standard input

编写接收命令：撰写一个命令，该命令将接收到工具调用的信息。这个命令会通过标准输入，获取关于拟进行的工具调用的 JSON 数据。

4 If needed, command should provide feedback to Claude - Your command's exit code tells Claude whether to allow or block the operation

提供反馈（可选）：如有需要，你的命令应向 Claude 提供反馈。你的命令的退出代码将决定 Claude 是允许还是阻止这项操作的执行。

### Available Tools

可用工具

Claude Code provides several built-in tools that you can monitor with hooks:

Claude Code 内置了多种工具，你可以利用 hook 机制来监控它们：

To see exactly which tools are available in your current setup, you can ask Claude directly for a list. This is especially useful since the available tools can change when you add custom MCP servers.

想知道您当前配置中具体有哪些可用工具吗？您可以直接让 Claude 列出清单。这一点特别实用，因为当您添加自定义 MCP 服务器时，可用的工具可能会随之改变。

### Tool Call Data Structure

工具调用数据结构

When your hook command executes, Claude sends JSON data through standard input containing details about the proposed tool call:

当你的钩子命令（hook command）执行时，Claude 会通过标准输入（standard input）发送 JSON 数据，里面包含了它提议执行的工具调用的详细信息：

```json
{
  "session_id": "2d6a1e4d-6...",
  "transcript_path": "/Users/sg/...",
  "hook_event_name": "PreToolUse",
  "tool_name": "Read",
  "tool_input": {
    "file_path": "/code/queries/.env"
  }
}
```

Your command reads this JSON from standard input, parses it, and then decides whether to allow or block the operation based on the tool name and input parameters.

你的命令会从标准输入读取并解析这些 JSON 数据，然后根据工具名称（tool name）和输入参数（input parameters）来决定是允许还是阻止这项操作。

### Exit Codes and Control Flow

退出代码与控制流（Control Flow）

Your hook command communicates back to Claude through exit codes:

你的钩子命令（hook command）会通过退出代码（Exit Code）向 Claude 传递信息：

Exit Code 0 - Everything is fine, allow the tool call to proceed

退出代码 0 - 表示一切顺利，允许工具调用（tool call）正常执行。

Exit Code 2 - Block the tool call (PreToolUse hooks only)

退出代码 2 - 表示需要拦截此次工具调用（仅限于 PreToolUse 钩子）。

When you exit with code 2 in a PreToolUse hook, any error messages you write to standard error will be sent to Claude as feedback, explaining why the operation was blocked.

当你在 PreToolUse 钩子中以退出代码 2 结束时，任何你写入标准错误（standard error）的错误消息都将作为反馈（feedback）发送给 Claude，用于解释为什么该操作被阻止。

### Example Use Case

应用场景示例

A common use case is preventing Claude from reading sensitive files like .env files. Since both the Read and Grep tools can access file contents, you'd want to monitor both tool types and check if they're trying to access restricted file paths.

一个常见的用例是阻止 Claude 访问敏感文件，例如 .env 文件。由于 Read（读取）和 Grep（查找）这两种工具都能访问文件内容，因此你需要监控它们，并检查它们是否正试图访问受限制的文件路径。

This approach gives you complete control over Claude's file system access while providing clear feedback about why certain operations are restricted.

这种方法让你能够完全掌控 Claude 的文件系统访问权限，同时也能清楚地告知你为什么某些操作会受到限制。