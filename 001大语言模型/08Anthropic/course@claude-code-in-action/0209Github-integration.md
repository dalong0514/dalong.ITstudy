## 0209Github-integration

[Github integration](https://anthropic.skilljar.com/claude-code-in-action/303240)

Claude Code offers an official GitHub integration that allows it to run within a GitHub Action. You can set up this integration by running `/install GitHub app`. This command initiates a guided setup process.

Claude Code 提供了一个官方的 GitHub 集成功能，让它能够在 GitHub Action 中运行。要启用这项集成，你只需运行命令 `/install GitHub app`。这个命令会启动一个向导式的设置流程，指导你完成每一步。

First, you'll need to install the Claude Code app on GitHub. Next, you'll be prompted to add an API key. Once these steps are completed, a pull request will be automatically generated. This pull request introduces two GitHub Actions.

首先，您需要在 GitHub 上安装 Claude Code 应用。接着，系统会提示您添加一个 API 密钥。完成这些步骤后，系统将自动创建一个「拉取请求」（pull request）。这个拉取请求会引入两个 GitHub Actions。

The first action enables mentioning support, allowing you to interact with Claude from an issue or pull request by typing `@Claude` and assigning it a task. The second action provides support for reviewing pull requests. When you create a pull request, Claude Code will automatically run and review the proposed changes. Both of these actions are customizable, and you can also add further actions to be triggered by different event types.

第一个动作是启用了提及功能，让你可以通过在问题或拉取请求中输入 `@Claude` 并给它分配任务，来与 Claude 进行交互。第二个动作是支持审查拉取请求。当你创建一个拉取请求时，Claude Code 会自动运行并审查你提议的更改。这两个动作都支持自定义，你还可以添加更多动作，让它们由不同的事件类型触发。

Let me demonstrate how to customize the mentioning feature. After merging the two action configuration files into your GitHub repository, you'll need to pull those changes to your local machine. Within the newly created GitHub workflows directory, you will find these two action configuration files. One file configures support for pull request reviews, and the other handles mentions.

让我演示如何自定义提及功能。将两个操作配置文件合并到您的 GitHub 仓库后，您需要将这些更改同步到本地机器。在新建的 GitHub 工作流目录中，您会找到这两个操作配置文件。其中一个文件配置了对拉取请求（PR）审查的支持，另一个则处理提及功能。

Here's how I'll customize the mention functionality: whenever I mention Claude in an issue or pull request, I want it to execute the project and utilize the Playwright MCP server to access the app within a web browser, all managed by a GitHub Action.

我是这样设想自定义提及功能的：每当我在某个议题或拉取请求中 @Claude，我希望它能自动运行项目，并通过 Playwright MCP 服务器在网页浏览器中打开应用。所有这些操作都将由一个 GitHub Action 来管理。

To achieve this, I'll first add a step before Claude Code runs in this workflow. I'll execute the setup command and then start the development server. Following that, I'll update the Claude Code configuration by adding custom instructions. These instructions are passed directly to Claude and provide additional direction or context. In this scenario, I'll inform Claude that the development server is already running and that it can use the Playwright MCP server to access the app in the browser if necessary.

为了实现这个目标，我将首先在这个工作流程中，在 Claude Code 运行之前增加一个步骤。我会先执行安装命令，然后启动开发服务器。紧接着，我将更新 Claude Code 的配置，加入一些自定义指令。这些指令会直接传递给 Claude，为它提供额外的指导或上下文信息。在这个场景中，我会告诉 Claude 开发服务器已经启动，并且如果需要，它可以通过 Playwright MCP 服务器在浏览器中访问应用程序。

Next, I'll configure the Playwright MCP server itself. It's important to be aware of one particular aspect when running Claude Code within an action: you must explicitly list all permissions you wish to grant Claude Code. There's a nuanced detail here: if you're using an MCP server, you need to individually list each tool from each MCP server that you want to allow. There is no shortcut for permissions in this context. Unfortunately, the Playwright MCP server includes numerous tools, so each one requires individual listing.

接下来，我将配置 Playwright MCP 服务器。在操作中运行 Claude Code 时，有一点需要特别注意：你必须明确列出所有你希望授予 Claude Code 的权限。这里有一个微妙之处：如果你正在使用 MCP 服务器，你需要逐一列出你想要允许的每个 MCP 服务器中的所有工具。在这种情况下，权限管理没有捷径可走。不幸的是，Playwright MCP 服务器包含了大量的工具，因此每个工具都需要单独进行列举。

After completing these configuration updates, I'll commit and push the changes.

完成这些配置更新后，我将提交并推送更改。

Now, it's time to test this updated workflow. I'll give Claude a task. In our actual application, there are two buttons at the top. Currently, they function correctly, allowing seamless toggling between the preview and code panels. However, for this demonstration, I'll simulate a scenario where they are not working as intended. I'll take a screenshot of one of these buttons, create an issue, paste the screenshot into it, and then mention Claude with `@Claude`, asking it to verify if the two buttons are functioning correctly. I'll then create the issue and wait.

现在，是时候测试这个更新后的工作流程了。我将给 Claude 分配一个任务。在我们的实际应用程序中，顶部有两个按钮。目前，它们功能正常，允许在预览和代码面板之间无缝切换。然而，为了这次演示，我将模拟一个它们未能按预期工作的场景。我将截取其中一个按钮的屏幕截图，创建一个问题，将屏幕截图粘贴进去，然后用 `@Claude` 提及它，要求它验证这两个按钮是否正常工作。随后我将创建这个问题并等待。

It will take a minute or two for the action to initiate and for Claude to respond. Remember, as we just configured, the entire application is set up and started before Claude Code even begins its execution. Eventually, Claude will provide a response, often starting with a checklist of steps to complete the given task. In this case, it will attempt to access the app, manually test the buttons, and fix any identified issues. Claude will observe that the buttons are, in fact, working correctly and will terminate the process early, documenting its findings.

操作启动并等待 Claude 响应大约需要一到两分钟。请记住，正如我们之前配置的，整个应用程序会在 Claude Code 开始执行之前完成设置和启动。最终，Claude 会提供一个响应，通常会以完成给定任务的步骤清单作为开场。在这种情况下，它会尝试访问应用程序，手动测试按钮，并修复任何发现的问题。Claude 将发现按钮实际上运行正常，随后会提前终止该过程，并记录下其发现。

This is just a small illustration of how you can leverage Claude Code's GitHub integration. I encourage you to explore how you can tailor it to your specific project needs.

这只是一个简单示例，演示了如何利用 Claude Code 的 GitHub 集成。我鼓励您深入探索，根据自己具体的项目需求来对其进行定制。

## 网页文档

Claude Code offers an official GitHub integration that lets Claude run inside GitHub Actions. This integration provides two main workflows: mention support for issues and pull requests, and automatic pull request reviews.

Claude Code 提供了一个官方的 GitHub 集成，让 Claude 可以在 GitHub Actions 内部运行。这项集成提供了两大主要工作流程：一是在 issues（问题）和 pull requests（拉取请求）中提供提及支持，二是自动化的 pull request 评审。

### Setting Up the Integration

To get started, run /install-github-app in Claude. This command walks you through the setup process:

设置集成要开始，请在 Claude 中运行 `/install-github-app`。这个命令会引导您完成整个设置过程：

1 Install the Claude Code app on GitHub

在 GitHub 上安装 Claude Code 应用

2 Add your API key

添加您的 API 密钥

3 Automatically generate a pull request with the workflow files

自动生成一个包含工作流文件的拉取请求（pull request）

The generated pull request adds two GitHub Actions to your repository. Once merged, you'll have the workflow files in your .github/workflows directory.

这个生成的拉取请求会将两个 GitHub Actions 添加到您的代码仓库。一旦合并后，您就可以在 `.github/workflows` 目录中找到这些工作流文件了。

### Default GitHub Actions

默认的 GitHub Actions

The integration provides two main workflows:

此集成提供了两个主要工作流程（workflow）：

Mention Action

@提及功能

You can mention Claude in any issue or pull request using @claude. When mentioned, Claude will:

您可以使用 @claude 在任何问题或拉取请求（pull request）中提及 Claude。当被提及后，Claude 将：

Analyze the request and create a task plan
Execute the task with full access to your codebase
Respond with results directly in the issue or PR

分析请求并制定一份任务计划。
执行任务时，将拥有对你的代码库的完全访问权限。
直接在问题或拉取请求（Pull Request）中给出结果。

Pull Request Action

拉取请求操作（Pull Request Action）

Whenever you create a pull request, Claude automatically:

每当你创建一个拉取请求时，Claude 就会自动：

Reviews the proposed changes
Analyzes the impact of modifications
Posts a detailed report on the pull request

审查提议的更改
分析修改的影响
就拉取请求发布详细报告

### Customizing the Workflows

自定义工作流（Workflows）

After merging the initial pull request, you can customize the workflow files to fit your project's needs. Here's how to enhance the mention workflow:

在合并了初始拉取请求（pull request）后，你可以自定义工作流文件以适应你的项目需求。以下是增强提及工作流（mention workflow）的方法：

Adding Project Setup

配置项目环境

Before Claude runs, you can add steps to prepare your environment:

在 Claude 运行之前，你可以添加一些步骤来配置运行环境：

- name: Project Setup
  run: |
    npm run setup
    npm run dev:daemon

Custom Instructions

定制指令：

Provide Claude with context about your project setup:

以下是关于您的项目设置的说明，以便 Claude 更好地理解：

custom_instructions: |
  The project is already set up with all dependencies installed.
  The server is already running at localhost:3000. Logs from it
  are being written to logs.txt. If needed, you can query the
  db with the 'sqlite3' cli. If needed, use the mcp__playwright
  set of tools to launch a browser and interact with the app.

项目已完成设置，所有必要的依赖项都已安装。
服务器目前正在 localhost:3000 上运行，其运行日志会被写入 logs.txt 文件中。如果需要，您可以使用'sqlite3' 命令行界面（CLI）来查询数据库。此外，您还可以利用 mcp__playwright 工具来启动浏览器并与应用程序进行交互。

MCP Server Configuration

MCP 服务器配置：

You can configure MCP servers to give Claude additional capabilities:

您可以配置 MCP 服务器，为 Claude 提供更多的功能。

```json
mcp_config: |
  {
    "mcpServers": {
      "playwright": {
        "command": "npx",
        "args": [
          "@playwright/mcp@latest",
          "--allowed-origins",
          "localhost:3000;cdn.tailwindcss.com;esm.sh"
        ]
      }
    }
  }
```

### Tool Permissions

工具权限

When running Claude in GitHub Actions, you must explicitly list all allowed tools. This is especially important when using MCP servers.

你需要知道的一切在 GitHub Actions 中运行 Claude 时，你需要明确列出所有允许的工具。这一点在使用 MCP 服务器时尤为重要。

allowed_tools: "Bash(npm:*),Bash(sqlite3:*),mcp__playwright__browser_snapshot,mcp__playwright__browser_click,..."

Unlike local development, there's no shortcut for permissions in GitHub Actions. Each tool from each MCP server must be individually listed.

与本地开发不同，在 GitHub Actions 中处理权限并没有什么捷径。来自每个 MCP 服务器的每一个工具，都必须逐一明确列出其所需的权限。

### Best Practices

最佳实践（Best Practices）

When setting up Claude's GitHub integration:

在设置 Claude 的 GitHub 集成时：

1 Start with the default workflows and customize gradually

从默认工作流程开始，然后逐步进行定制。

2 Use custom instructions to provide project-specific context

使用自定义指令来提供特定项目的背景信息。

3 Be explicit about tool permissions when using MCP servers

在使用 MCP 服务器时，请明确设置工具的使用权限。

4 Test your workflows with simple tasks before complex ones

在处理复杂任务之前，请先用简单任务测试你的工作流程。

5 Consider your project's specific needs when configuring additional steps

在配置额外步骤时，请考虑你项目特有的具体需求。

The GitHub integration transforms Claude from a development assistant into an automated team member that can handle tasks, review code, and provide insights directly within your GitHub workflow.

GitHub 集成能够将 Claude 从一个开发助手转变为一个自动化的团队成员，它可以在你的 GitHub 工作流程中直接处理任务、审查代码并提供深入见解。
