## 0306The-Claude-Code-SDK

[The Claude Code SDK](https://anthropic.skilljar.com/claude-code-in-action/312001)

As we were looking at the query review hook a moment ago, we got a brief look at the Claude Code SDK. The SDK allows you to use Claude Code programmatically. You can use the SDK via the CLI, TypeScript library, or Python library. This is the exact same Claude Code that you already use at the terminal. It has all the same tools and will use them to complete a given task.

正如我们刚才在查看查询审查钩子（query review hook）时，我们简要了解了 Claude Code SDK。这个 SDK 允许你通过编程方式使用 Claude Code。你可以通过命令行界面（CLI）、TypeScript 库或 Python 库来使用它。这与你在终端上已经使用的 Claude Code 完全一样。它具备所有相同的工具，并将利用这些工具来完成给定任务。

The SDK is most useful as part of a larger pipeline or tool, as we saw in that hook a moment ago. You can easily wire in cloud code as part of a larger process to add in a bunch of intelligence to some given workflow.

SDK（软件开发工具包）最有用的地方在于，它可以作为更大管道或工具的一部分来发挥作用，正如我们刚才在 Hook（钩子）中看到的那样。你可以轻松地将云端代码整合到一个更大的流程中，从而为特定的工作流添加丰富的智能。

Now I'd like to give you a quick demonstration of the TypeScript SDK in particular by adding it into our existing project. Back inside my editor, I'm going to find the `sdk.ts` file inside the root project directory. Inside of here, I put together just a little bit of code to get us started with the SDK. I'm going to update the prompt at the top and ask Claude to look for duplicate queries inside the `src/queries` directory.

现在，我将向大家快速演示一下 TypeScript SDK，具体来说，就是把它集成到我们现有的项目中。回到我的编辑器里，我会在项目根目录下找到 `sdk.ts` 文件。在这个文件里，我预先写了一些简单的代码，方便我们快速上手使用 SDK。接下来，我将更新顶部的提示信息，让 Claude 去 `src/queries` 目录中查找重复的查询。

Then I'm going to save this file and to run it, I'll open up my terminal and execute `npm run SDK`. Now, this is not a built-in command or anything like that, just so you know. On the scenes, it just executes this file as a normal TypeScript file. I just put together this little shortcut for us to make running a TypeScript file a little bit easier. When we run this, we'll see the raw conversation between our local copy of Claude code and the Claude language model, message by message. Eventually, we'll get kicked back to the command line. The very last message printed out will contain the final response from Cloud.

然后我将保存此文件并运行它，我将打开终端并执行 `npm run SDK`。请注意，这并非内置命令。实际上，它只是在后台将此文件作为普通的 TypeScript 文件执行。我只是为大家设置了一个小小的快捷方式，让运行 TypeScript 文件变得更简单。当我们运行它时，我们会逐条看到本地的 Claude 代码副本与 Claude 语言模型之间的原始对话。最终，程序将返回命令行界面。打印出的最后一条消息将包含 Claude 的最终响应。

Now there is a little bit of a gotcha around the SDK, and that is that by default it only has read abilities. So in other words, it can only read files, directories, do grep operations, and so on. It does not have the ability to write or edit or create and so on files. To give it write permissions, you can either manually add in write permissions to the `query` call right here, or alternately, you can add in some permission settings to your `settings.json` file inside of your `clad` directory.

关于 SDK，这里有一个小小的坑，那就是它默认情况下只拥有读取权限。换句话说，它只能读取文件、目录，执行 grep 等操作。它不具备写入、编辑或创建文件等能力。要赋予它写入权限，你可以手动将写入权限添加到 `query` 调用中，或者，你也可以在 `clad` 目录中的 `settings.json` 文件中添加一些权限设置。

Let me show you how we can allow the SDK to use the edit tool within this project. I'm going to find the prompt argument right here. Right after it, I'll add in `options`, put in an object, `allowTools`, that will be an array, and I'll put in `edit`. I'm going to update the prompt at the top, and I'll ask it to add a description to the `package.json` file.

接下来，我将向您演示如何让 SDK 在这个项目中启用编辑工具。首先，我找到提示参数 `prompt`。紧接着，我会添加一个 `options` 对象，在这个对象里，`allowTools` 将是一个数组，我会在其中加入 `edit`。之后，我将更新顶部的提示，并指示它为 `package.json` 文件添加一段描述。

Now I'm going to save this, run `env` and run `SDK` once again. And then once it is complete, I can open up the `package.json` file and I will see that it did in fact add in a description. So now it definitely has the ability to edit files.

现在，我将保存当前修改，运行 `env`，然后再次执行 `SDK`。当这个过程完成后，我就可以打开 `package.json` 文件，并且会发现它确实已经添加了一个描述。这表明它确实具备了编辑文件的能力。

As I mentioned earlier, the Cloud Code SDK is most useful as part of other tools. So I would encourage you to think of opportunities to use it in helper commands, scripts, or probably most notably hooks inside of your own projects. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you.

正如我之前提到的，Cloud Code SDK 作为其他工具的组成部分时，才能发挥最大的作用。因此，我鼓励大家思考如何在辅助命令、脚本，或者尤其值得注意的是，在您自己项目中的钩子（hook）里利用它的功能。

## 页面文档

The Claude Code SDK lets you run Claude Code programmatically from within your own applications and scripts. It's available for TypeScript, Python, and via the CLI, giving you the same Claude Code functionality you use at the terminal but integrated into larger workflows.

Claude Code SDK（软件开发工具包）让你可以在自己的应用程序和脚本中以编程方式运行 Claude Code。它支持 TypeScript、Python，并提供命令行界面（CLI），为你带来与在终端中相同的 Claude Code 功能，同时还能将这些功能融入到更广泛的开发流程中。

The SDK runs the exact same Claude Code you're already familiar with. It has access to all the same tools and will use them to complete whatever task you give it. This makes it particularly powerful for automation and integration scenarios.

这款 SDK（软件开发工具包）运行着你早已熟悉的、与 Claude 完全相同的代码。它能够访问所有相同的工具，并会利用它们来完成你交给它的任何任务。这使得它在自动化和系统集成场景中表现出特别强大的能力。

### Key Features

主要特点

Runs Claude Code programmatically
Same Claude Code functionality as the terminal version
Inherits all settings from Claude Code instances in the same directory
Read-only permissions by default
Most useful as part of larger pipelines or tools

以编程方式运行 Claude Code
功能与终端（terminal）版本完全相同
自动继承同一目录下其他 Claude Code 实例的所有配置
默认拥有只读权限
最适合集成到大型工作流（pipeline）或工具中

### Basic Usage

基本用法

Here's a simple TypeScript example that asks Claude to analyze code for duplicate queries:

下面是一个简单的 TypeScript 示例，展示了如何让 Claude 分析代码以发现重复的查询：

```js
import { query } from "@anthropic-ai/claude-code";

const prompt = "Look for duplicate queries in the ./src/queries dir";

for await (const message of query({
  prompt,
})) {
  console.log(JSON.stringify(message, null, 2));
}
```

When you run this code, you'll see the raw conversation between your local Claude Code and the Claude language model, message by message. The final message contains Claude's complete response.

当你运行这段代码时，你将看到本地的 Claude Code 和 Claude 语言模型（language model）之间逐条消息的原始对话。最后一条消息则包含了 Claude 的完整响应。

### Permissions and Tools

权限与工具

By default, the SDK only has read-only permissions. It can read files, search directories, and perform grep operations, but it cannot write, edit, or create files.

默认情况下，SDK 仅具有只读权限。这意味着它可以读取文件、搜索目录以及执行 grep（grep）操作，但无法写入、编辑或创建任何文件。

To enable write permissions, you can add the allowedTools option to your query:

要启用写入权限（write permissions），你可以将 allowedTools 选项添加到你的查询中：

```js
for await (const message of query({
  prompt,
  options: {
    allowedTools: ["Edit"]
  }
})) {
  console.log(JSON.stringify(message, null, 2));
}
```

Alternatively, you can configure permissions in your settings file within the .claude directory for project-wide access.

或者，你也可以在 .claude 目录下的设置文件中配置权限，从而实现项目层面的访问控制。

### Practical Applications

实际应用

The Claude Code SDK shines when integrated into larger development workflows. Consider using it for:

Claude Code SDK 在融入更宏大的开发工作流时，其价值便会凸显。你可以考虑将它应用到以下场景：

Git hooks that automatically review code changes
Build scripts that analyze and optimize code
Helper commands for code maintenance tasks
Automated documentation generation
Code quality checks in CI/CD pipelines

通过 Git hooks 自动审查代码变更
利用构建脚本来分析和优化代码
提供辅助命令，用于执行代码维护任务
实现自动化文档生成

The SDK essentially lets you add AI-powered intelligence to any part of your development process where programmatic access would be valuable.

在 CI/CD 流水线中进行代码质量检查这款 SDK 的核心作用是让你能够在开发流程中任何需要编程介入的地方，注入由 AI 驱动的智能（AI-powered intelligence）。