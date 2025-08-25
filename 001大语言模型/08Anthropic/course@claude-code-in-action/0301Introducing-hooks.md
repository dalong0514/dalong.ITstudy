## 0301Introducing-hooks

In this video, we're going to take a look at hooks. These allow you to run commands before or after Claude attempts to run a tool. Hooks can be used to implement really interesting and very useful functionality. For example, after Claude decides to write a file, you can automatically run a code formatter on the created file, or you can run tests after a file is edited, or you can block Claude from reading particular files. The possibilities are really endless, and I've got a couple of good examples lined up to show you to give you some ideas of how you might use hooks on your particular project.

在这段视频中，我们将深入探讨钩子（hooks）。它们允许你在 Claude 尝试调用工具之前或之后运行特定的命令。钩子可以用来实现非常有趣且实用的功能。例如，在 Claude 决定写入文件后，你可以自动对生成的文件运行代码格式化程序；或者在文件被编辑后运行测试；又或者，你可以阻止 Claude 读取某些特定的文件。这些可能性真是无穷无尽！我已经准备了一些不错的示例，希望能给你一些启发，让你了解如何在自己的项目中利用钩子。

First, however, let me help you understand exactly how hooks works. As a reminder, when you ask Claude code something, your query is sent off to the Claude model along with some tool definitions. The Claude model might then decide to run a tool by providing a carefully formatted response. And at that point, it is up to Claude code to run the requested tool, maybe in this case to read a file, and then respond with the result of that tool call.

不过，首先，让我帮你准确理解钩子（hooks）是如何工作的。值得注意的是，当你让 Claude 编写代码时，你的查询会连同一些工具定义一起发送给 Claude 模型。Claude 模型随后可能会通过提供一个精心格式化的响应来决定运行某个工具。此时，就轮到 Claude code 来执行所请求的工具了，比如读取一个文件，然后将该工具调用的结果返回。

Now, hooks give us the ability to execute code just before or just after the tool execution. Hooks that run before a tool are referred to as pre-tool use hooks because they run before the tool. And hooks that run after the tool are referred to as post-tool use for the same reason. To define hooks, we add configuration to the Claude settings file. Remember that there are several different settings files: one for global use across all the projects on your machine, one for your particular project that gets shared with other engineers, and one for just you on a particular project. You can add hooks either by writing them out by hand inside this file or by using the built-in slash hooks command inside of Claude code itself.

现在，钩子（hooks）能够让我们在工具执行之前或之后运行代码。在工具运行之前的钩子被称为「前置工具使用钩子」，因为它们在工具执行前被触发。同理，在工具运行之后的钩子则被称为「后置工具使用钩子」。要定义这些钩子，我们需要在 Claude 设置文件中添加配置。请记住，Claude 设置文件有几种不同的类型：一种是用于您机器上所有项目的全局设置，一种是用于您特定项目并与其他工程师共享的设置，还有一种是仅供您在特定项目上使用的设置。您可以通过手动编辑此文件并写入钩子代码，或者利用 Claude 代码内置的 `/hooks` 命令来添加钩子。

The configuration itself looks like what you see on the right-hand side of the screen. Let me walk you through this example file just to give you a better idea of what's going on. So first, notice that there are two distinct sections inside this file. One section lists out all the commands that should be executed before a tool use. Remember, those are referred to as pre-tool use hooks. The other section lists out all the different commands that should be executed after a tool use, and again, those are post-tool use hooks. In each of these sections, we provide a matcher. This indicates which tool use types we are looking for. So in this case, I want to find uses of the read tool. Whenever Claude Code attempts to read a file, I want to run the command you see listed there. Likewise, inside the post-tool use section, after use of the write, edit, or multi-edit tools, there's a different command that I want to run.

配置本身正如你屏幕右侧所示。让我带你了解一下这个示例文件，以便你更好地理解其工作原理。首先，请注意此文件包含两个不同的部分。一个部分列出了在工具使用之前应执行的所有命令，这些被称为预工具使用钩子（pre-tool use hooks）。另一个部分列出了在工具使用之后应执行的所有不同命令，这些是后工具使用钩子（post-tool use hooks）。在每个部分中，我们都提供了一个匹配器（matcher）。它指明了我们正在寻找哪种工具使用类型。因此，在这种情况下，它旨在匹配「读取（read）」工具的使用。每当 Claude Code 尝试读取文件时，就会运行你所看到的相应命令。同样，在后工具使用部分中，在使用「写入（write）」、「编辑（edit）」或「多重编辑（multi-edit）」工具之后，就会运行一个不同的命令。

Now, here's the important part. Here's what hooks are really intended to do. Those commands you saw will be given details about the tool call that Claude wants to run. In the case of a pre-tool use hook, you can inspect what Claude wants to do. Those commands you saw will be given details about the tool call that Claude wants to run. In the case of a pre-tool use hook, you can inspect what Claude wants to do, and if for any reason you don't want to allow it, you can block the tool use operation and send an error message back to Claude. In the case of a post-tool use hook, the tool call has already occurred, so it's too late to block it. But you can do some follow-up operation based upon the tool call, like maybe format a file that was just edited. You can also provide some message back to Claude about that tool use. For example, you might decide to run a separate program to check the code quality of the edit, or maybe do a type check, and then provide that feedback back to Claude. Claude might then take that feedback and make an update to the file that it just wrote to.

现在，我们来聊聊最重要的部分：hooks（钩子）的真正作用。你之前看到的那些命令，会收到 Claude 想要执行的工具调用的详细信息。

如果是在「工具使用前钩子」的场景下，你可以检查 Claude 打算做什么。如果出于任何原因你不想允许它，你可以阻止这次工具操作，并向 Claude 发送一条错误消息。

而「工具使用后钩子」则不同，此时工具调用已经发生，再阻止就来不及了。不过，你可以根据这次工具调用做一些后续处理，比如对刚刚编辑过的文件进行格式化。你也可以就这次工具的使用情况向 Claude 提供一些反馈。举个例子，你可能会决定运行一个单独的程序来检查代码编辑的质量，或者进行类型检查，然后把这些反馈传回给 Claude。Claude 随后可能会根据这些反馈，对它刚刚写入的文件进行更新。

If you're still confused about hooks or what they're intended to do, that is absolutely okay. Wrapping your head around hooks can be really challenging. So let's come back in a moment and work on a sample project with hooks. Thank you.

如果你仍然对「钩子」（hooks）或者它们的作用感到困惑，那完全没有关系。理解「钩子」确实是一项不小的挑战。所以，稍后我们会回来，在一个实际的示例项目中亲自动手使用「钩子」。感谢你的耐心。

## 网页文档

Hooks allow you to run commands before or after Claude attempts to run a tool. They're incredibly useful for implementing automated workflows like running code formatters after file edits, executing tests when files change, or blocking access to specific files.

钩子（Hooks）允许你在 Claude 尝试运行某个工具之前或之后，执行特定的命令。它们在实现自动化工作流程方面极其有用，例如，你可以在文件编辑后自动运行代码格式化工具，在文件内容发生变化时自动执行测试，或者限制对某些特定文件的访问。

### How Hooks Work

Hooks 的工作原理

To understand hooks, let's first review the normal flow when you interact with Claude Code. When you ask Claude something, your query gets sent to the Claude model along with tool definitions. Claude might decide to use a tool by providing a formatted response, and then Claude Code executes that tool and returns the result.

要理解 hooks，我们首先需要回顾一下你与 Claude Code 交互时的常规流程。当你向 Claude 提出问题或发出指令时，你的查询会连同工具定义（tool definitions）一起发送到 Claude 模型（Claude model）。Claude 可能会通过生成一个格式化的响应来决定调用某个工具，接着由 Claude Code 执行该工具，并将结果返回。

Hooks insert themselves into this process, allowing you to execute code just before or just after the tool execution happens.

Hooks（钩子）会介入到这个过程中，允许你在工具执行之前或之后执行代码。

There are two types of hooks:

有两种类型的 hooks:

1 PreToolUse hooks - Run before a tool is called

PreToolUse 钩子（hooks）- 在调用工具之前执行

2 PostToolUse hooks - Run after a tool is called

PostToolUse 钩子（hooks）- 在调用工具之后执行钩子（Hook）

### Hook Configuration

配置钩子（Hooks）

Hooks are defined in Claude settings files. You can add them to:

在 Claude 的设置文件中进行定义。你可以将它们添加至：

Global - ~/.claude/settings.json (affects all projects)
Project - .claude/settings.json (shared with team)
Project (not committed) - .claude/settings.local.json (personal settings)

全局配置：~/.claude/settings.json（影响所有项目）
项目配置：.claude/settings.json（与团队共享）
项目本地配置（未提交）：.claude/settings.local.json（个人设置）

You can write hooks by hand in these files or use the /hooks command inside Claude Code.

你可以在这些文件中手动编写钩子（hooks），也可以在 Claude Code 中使用 /hooks 命令。

The configuration structure includes two main sections:

配置结构包括两个主要部分：

### PreToolUse Hooks

PreToolUse Hooks（工具前置钩子）

PreToolUse hooks run before a tool is executed. They include a matcher that specifies which tool types to target:

PreToolUse hooks（工具前置钩子）会在工具执行之前运行。它们包含一个匹配器，用于指定要作用于哪些工具类型：

```json
"PreToolUse": [
  {
    "matcher": "Read",
    "hooks": [
      {
        "type": "command",
        "command": "node /home/hooks/read_hook.ts"
      }
    ]
  }
]
```

Before the 'Read' tool is executed, this configuration runs the specified command. Your command receives details about the tool call Claude wants to make, and you can:

在 'Read' 工具执行之前，此配置会运行指定的命令。你的命令会收到关于 Claude 想要进行的工具调用的详细信息，你可以：

1 Allow the operation to proceed normally

让操作正常进行

2 Block the tool call and send an error message back to Claude

阻止工具调用，并向 Claude 发送错误消息

### PostToolUse Hooks

PostToolUse Hooks（工具使用后钩子）

PostToolUse hooks run after a tool has been executed. Here's an example that triggers after write, edit, or multi-edit operations:

PostToolUse 钩子（hook）会在工具执行后运行。下面是一个在执行写入（write）、编辑（edit）或多重编辑（multi-edit）操作后触发的示例：

```json
"PostToolUse": [
  {
    "matcher": "Write|Edit|MultiEdit",
    "hooks": [
      {
        "type": "command", 
        "command": "node /home/hooks/edit_hook.ts"
      }
    ]
  }
]
```

Since the tool call has already occurred, PostToolUse hooks can't block the operation. However, they can:

由于工具调用（tool call）已执行完毕，PostToolUse 钩子（hooks）无法再阻止此次操作。然而，它们可以实现以下功能：

1 Run follow-up operations (like formatting a file that was just edited)

运行后续操作（例如对刚刚编辑的文件进行格式化）

2 Provide additional feedback to Claude about the tool use

就工具使用向 Claude 提供额外反馈

### Practical Applications

Here are some common ways to use hooks:

实际应用以下是一些使用钩子（hook）的常见方式:

1 Code formatting - Automatically format files after Claude edits them

代码格式化 - 在 Claude 编辑文件后自动进行格式化。

2 Testing - Run tests automatically when files are changed

测试 - 当文件发生变化时，自动运行测试。

3 Access control - Block Claude from reading or editing specific files

访问控制 - 阻止 Claude 读取或编辑特定文件。

4 Code quality - Run linters or type checkers and provide feedback to Claude

代码质量 - 运行 linter（代码检查工具）或 type checker（类型检查器），并向 Claude 提供反馈。

5 Logging - Track what files Claude accesses or modifies

日志记录 - 跟踪 Claude 访问或修改了哪些文件。

6 Validation - Check naming conventions or coding standards

验证 - 检查命名约定或编码标准。

The key insight is that hooks let you extend Claude Code's capabilities by integrating your own tools and processes into the workflow. PreToolUse hooks give you control over what Claude can do, while PostToolUse hooks let you enhance what Claude has done.

这里的关键在于，钩子（hooks）可以让你将自己的工具和流程集成到工作流中，从而扩展 Claude Code 的功能。PreToolUse 钩子允许你控制 Claude 可以执行哪些操作，而 PostToolUse 钩子则能让你在 Claude 完成操作后对其结果进行增强或处理。
