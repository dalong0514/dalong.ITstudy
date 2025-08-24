## 0208MCP-servers-with-Claude-Code

[MCP servers with Claude Code](https://anthropic.skilljar.com/claude-code-in-action/303239)

You can add new tools and capabilities to Claude Code for the use of MCP servers. These MCP servers either run remotely or locally on your machine. A very popular MCP server named Playwright gives Claude Code the ability to control a browser. Let me show you how to add it to Claude Code, and then we'll use it to develop our app a little bit more.

您可以向 Claude Code 添加新工具和功能，供 MCP 服务器使用。这些 MCP 服务器可以远程运行，也可以在您的本地机器上运行。Playwright 是一个非常流行的 MCP 服务器，它让 Claude Code 能够控制浏览器。接下来，我将向您展示如何将其添加到 Claude Code 中，然后我们将利用它来进一步完善我们的应用程序开发。

To install the server at your terminal, not inside the Claude Code, we'll execute `Claude MCP add`, and then a name for this MCP server. I'm gonna name it Playwright, and then after the name, we'll add in a command that will start up the server locally on your machine. We can then start Claude Code and ask it to open a browser and navigate to our application at localhost:3000.

要在你的终端中安装服务器（而非在 Claude Code 内部），我们将执行 `Claude MCP add` 命令，接着输入这个 MCP 服务器的名称。我将其命名为「Playwright」，然后在这个名称后面，我们会添加一个能在你本地机器上启动服务器的命令。之后，我们就可以启动 Claude Code，让它打开浏览器并导航到我们位于 localhost:3000 的应用程序。

Before the browser opens, you might notice that you are required to give permission for that tool to run. If you get tired of all those permission popups, you can open up the `clod` directory inside their `settings.local.json`. And then inside the `allow` array, you can add in a string of `mcp__playwright` (notice there are two underscores there). This allows Claude Code to make use of this MCP server and the tools inside of it in any way it wants without requiring you to provide permission every time. If I restart Claude Code and ask it to open a browser again, it will do so without requiring me to give permission.

在浏览器打开之前，你可能会注意到系统会要求你授予该工具运行的权限。如果你厌倦了这些权限弹窗，可以找到 `settings.local.json` 文件中的 `clod` 目录。然后，在 `allow` 数组中，添加 `mcp__playwright` 这个字符串（注意这里是两个下划线）。这样一来，Claude Code 就可以随意使用这个 MCP 服务器及其内部的工具，而无需你每次都手动授权。如果我重新启动 Claude Code 并再次让它打开浏览器，它就能直接运行，不再需要我确认权限了。

There are an incredible number of ways that you can use the Playwright MCP server. We'll only show you one that will be really applicable to the project we are working on right now. Back inside my editor, I'm going to find the `src/lib/prompts/generation.tsx` file. This is the prompt that is used to actually generate the components that you ask for inside our app. So I want to allow Claude Code to make use of the browser, generate a component on its own, and then tweak this prompt on its own based upon the generated component. And hopefully we'll end up with some better looking components being generated out of our app. So let me show you how we would do that.

Playwright MCP 服务器功能强大，有多种用途。在这里，我们只会展示一种与我们当前项目紧密相关的使用方法。回到我的代码编辑器，我会找到 `src/lib/prompts/generation.tsx` 文件。这个文件包含了用于在我们应用程序中生成您所需组件的提示（prompt）。我的目标是让 Claude Code 能够调用浏览器，自主生成一个组件，然后根据这个生成的组件，智能地调整上述提示。这样，我们有望让应用程序生成出视觉效果更佳的组件。接下来，我将向您演示具体的操作步骤。

Back inside of Claude Code, I'm going to ask it to navigate to localhost:3000, attempt to generate a component, take a look at the generated source code and evaluate the styling, and then update our prompt inside that `generation.tsx` file. And hopefully we'll end up with some, at the end of the day, better styling on our generated components. So let's see how it does.

接下来，在 Claude Code 中，我会让 AI 智能体跳转到 localhost:3000，尝试生成一个组件，检查生成的源代码，评估其样式，然后更新 `generation.tsx` 文件中的提示。希望这样操作之后，我们生成的组件在样式上能有所改进。现在，就让我们看看效果如何。

Claude is going to first open up the browser. It's going to attempt to generate a component. And looking at some of the commentary from Claude here, it looks like it's not quite so happy. You might actually notice that it complains about a very common style that's used in applications like this, a purple to blue kind of gradient. Claude is then going to update our prompt and then try to generate a new component. And I'll be honest with you, this actually gave a much better result than I ever expected. This testimonial card actually looks really, really great.

Claude 首先会打开浏览器，尝试生成一个组件。从 Claude 的一些评论来看，它似乎对生成的结果不太满意。你可能会注意到，它特别指出了一种在此类应用程序中非常常见的样式问题 —— 一种从紫色到蓝色的渐变。随后，Claude 会根据这些反馈更新我们的提示（prompt），然后尝试生成一个新的组件。坦白说，最终呈现的结果远超我的预期，这个推荐卡片（testimonial card）看起来确实非常出色。

Based on these results alone, you can immediately get a sense that MCP servers really open the door to a lot of interesting use cases. And I highly recommend you look into some MCP servers that might aid Claude in developing whatever kind of project you personally are working on. Thank you.

仅仅基于这些结果，你就能立刻感觉到 MCP 服务器确实为许多有趣的用例打开了大门。我强烈建议你研究一些 MCP 服务器，它们或许能帮助 Claude 开发你正在进行的各种项目。谢谢。

## 网页文档

You can extend Claude Code's capabilities by adding MCP (Model Context Protocol) servers. These servers run either remotely or locally on your machine and provide Claude with new tools and abilities it wouldn't normally have.

你可以通过添加 MCP（Model Context Protocol）服务器来扩展 Claude Code 的功能。这些服务器可以在你的机器上远程或本地运行，为 Claude 提供其本身不具备的全新工具和能力。

One of the most popular MCP servers is Playwright, which gives Claude the ability to control a web browser. This opens up powerful possibilities for web development workflows.

Playwright 是最受欢迎的 MCP 服务器之一，它让 Claude 能够控制网页浏览器（web browser）。这为网络开发工作流程（web development workflows）带来了巨大的潜力。

### Installing the Playwright MCP Server

安装 Playwright MCP 服务器（Playwright MCP Server）

To add the Playwright server to Claude Code, run this command in your terminal (not inside Claude Code):

要将 Playwright 服务器添加到 Claude Code 中，请在您的终端（注意：不是在 Claude Code 内部）运行以下命令：

claude mcp add playwright npx @playwright/mcp@latest

This command does two things:

这条命令会完成两项工作：

1 Names the MCP server "playwright"

将 MCP 服务器命名为 "playwright"

2 Provides the command that starts the server locally on your machine

介绍在你的机器上本地启动服务器的命令

### Managing Permissions

权限管理

When you first use MCP server tools, Claude will ask for permission each time. If you get tired of these permission prompts, you can pre-approve the server by editing your settings.

当你首次使用 MCP 服务器工具时，Claude 会在每次操作时提示你授权。如果你觉得这些权限提示很频繁，可以通过修改设置来预先批准（pre-approve）服务器。

Open the .claude/settings.local.json file and add the server to the allow array:

请打开 .claude/settings.local.json 文件，并将指定的服务器添加到其 allow 列表（允许数组）中：

```json
{
  "permissions": {
    "allow": ["mcp__playwright"],
    "deny": []
  }
}
```

Note the double underscores in mcp__playwright. This allows Claude to use the Playwright tools without asking for permission every time.

请注意 `mcp__playwright` 中的双下划线。这使得 Claude 能够使用 Playwright 工具，而无需每次都请求许可。

### Practical Example: Improving Component Generation

实际案例：优化组件生成

Here's a real-world example of how the Playwright MCP server can improve your development workflow. Instead of manually testing and tweaking prompts, you can have Claude:

以下是 Playwright MCP 服务器如何提升您的开发工作流的一个真实案例。您无需手动测试和调整提示词，可以利用 Claude 来：

1 Open a browser and navigate to your application

打开浏览器并进入您的应用程序

2 Generate a test component

生成一个测试组件

3 Analyze the visual styling and code quality

分析视觉风格和代码质量

4 Update the generation prompt based on what it observes

根据观察到的情况更新生成提示

5 Test the improved prompt with a new component

使用一个新组件测试改进后的提示

For instance, you might ask Claude to:

例如，您可能会让 Claude 执行以下任务：

"Navigate to localhost:3000, generate a basic component, review the styling, and update the generation prompt at @src/lib/prompts/generation.tsx to produce better components going forward."

请导航至 localhost:3000，生成一个基本组件（component），检查其样式，并在 @src/lib/prompts/generation.tsx 更新生成提示（generation prompt），以期在未来能生成更出色的组件。

Claude will use the browser tools to interact with your app, examine the generated output, and then modify your prompt file to encourage more original and creative designs.

Claude 将会利用浏览器工具（browser tools）与你的应用程序进行交互，检查其生成的输出（generated output），然后修改你的提示文件（prompt file），从而促使它产生更具原创性和创造性的设计。

### Results and Benefits

In practice, this approach can lead to significantly better results. Instead of generic purple-to-blue gradients and standard Tailwind patterns, Claude might update prompts to encourage:

成果与优势在实践中，这种方法能够带来显著改善的效果。比如，Claude 不会再生成千篇一律的紫蓝色渐变和标准的 Tailwind 模式，而是可能会修改提示词（prompts）来引导模型生成：

1 Warm sunset gradients (orange-to-pink-to-purple)

温暖的日落渐变效果（从橙色到粉色再到紫色）

2 Ocean depth themes (teal-to-emerald-to-cyan)

海洋深度的色彩主题（从蓝绿色到翠绿色再到青色）

3 Asymmetric designs and overlapping elements

不对称设计和重叠元素

4 Creative spacing and unconventional layouts

巧妙的间距排布和不落俗套的布局方式

The key advantage is that Claude can see the actual visual output, not just the code, which allows it to make much more informed decisions about styling improvements.

关键优势在于，Claude 可以直接看到实际的视觉输出效果，而不仅仅是代码本身。这让它能对样式的改进做出更周全、更明智的判断。

### Exploring Other MCP Servers

探索其他 MCP 服务器（MCP servers）

Playwright is just one example of what's possible with MCP servers. The ecosystem includes servers for:

Playwright 只是 MCP 服务器强大功能的一个例子。该生态系统包含以下用途的服务器：

Database interactions
API testing and monitoring
File system operations
Claude service integrations
Development tool automation

数据库交互
API 测试与监控
文件系统操作
云服务集成
开发工具自动化

Consider exploring MCP servers that align with your specific development needs. They can transform Claude from a code assistant into a comprehensive development partner that can interact with your entire toolchain.

建议你探索那些与你特定开发需求相契合的 MCP 服务器。它们能让 Claude 从一个简单的代码助手，摇身一变成为一个能够与你整个工具链交互的全能开发伙伴。