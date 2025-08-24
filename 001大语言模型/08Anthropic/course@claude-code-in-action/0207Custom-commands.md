## 0207Custom-commands

[Custom commands](https://anthropic.skilljar.com/claude-code-in-action/303234)

When you run Claude Code, you can enter in a forward slash and see a bunch of commands that are built into Claude Code by default. In addition to these default commands, you can easily add your own custom commands as well. Custom commands are useful for automating repetitive tasks that you find yourself running frequently.

当你运行 Claude Code 时，只需输入一个正斜杠，就能看到许多 Claude Code 默认内置的命令。除了这些默认命令，你还可以轻松添加自己的自定义命令。自定义命令非常适合自动化那些你经常重复执行的任务。

Let me show you an example of how to make one. Inside my project directory, I'm going to find the `Claude` folder. Inside there, I'll make a new directory called `commands`. And then inside that, I'll make a new file called `audit.md`. The name of the file that we create, in this case `audit`, is going to be the name of the command we eventually run.

我来给你演示一下如何创建一个这样的命令。首先，在我的项目目录里，找到 `Claude` 文件夹。接着，在这个文件夹里创建一个新目录，命名为 `commands`。然后，在 `commands` 目录里，新建一个文件，命名为 `audit.md`。值得注意的是，我们创建的这个文件的名称（比如这里的 `audit`），最终会作为我们运行命令时的名字。

The goal of this command is going to be to audit all the different dependencies that have been installed into this project, update them if there are any vulnerabilities, and then run tests to make sure that nothing actually broke. Once you have created the command file, you'll then restart Claude Code. Don't forget to restart it.

这个命令的目标是检查项目中安装的所有依赖项。如果发现任何安全漏洞，它将自动更新这些依赖项。更新完成后，还会运行一系列测试，以确保没有引入任何破坏性的改变。完成命令文件的创建后，别忘了重启 Claude Code。

When you reopen Claude Code, put in `/audit`. This will then display the command that you just created. You can then run this, and in this case it will do exactly what we asked Claude to do: it'll run `command`, see if there are any vulnerable packages, fix them if necessary, and then run tests.

当你重新打开 Claude Code 时，输入 `/audit`。此时，你刚刚创建的命令就会显示出来。然后你可以运行它，它会严格按照我们预设的指示执行：运行特定的 `command`（命令），检查是否存在任何有安全漏洞的软件包，如果需要则进行修复，最后再运行测试。

Commands can also receive arguments. Let me show you an example. I'm going to make another command called `write tests`. Whenever I run this command, I want to have some tests created for a very particular file inside my project. Inside of the command text, I'm going to put in a placeholder of `$arguments`. Whenever I run the command, if I pass in a path to a file, that path will be inserted at `$arguments`.

命令也可以接收参数。我来给你演示一个例子。我将创建另一个名为 `write tests` 的命令。每当我运行这个命令时，我都希望为项目中的一个特定文件生成一些测试。在命令文本中，我将使用 `$arguments` 作为占位符。这样，每当我运行命令并传入一个文件路径时，这个路径就会被自动替换到 `$arguments` 的位置。

So now I can restart Claude Code again and then execute the `write tests` command. Now, to be clear, the arguments we pass in don't have to be a file path; it can be any string we want to pass in. So I might casually ask for tests for a file in some particular folder, giving Claude just a little bit of direction on where to look. So I might casually ask for tests for a file in some particular folder, giving Claude just a little bit of direction on where to look. Thank you.

现在，我可以重启 Claude Code 并执行 `write tests` 命令。值得注意的是，我们传入的参数不必是文件路径；它可以是我们想要传入的任何字符串。因此，我可能会随意地询问某个特定文件夹中某个文件的测试，给 Claude 一点点方向，告诉它在哪里查找。谢谢。

## 网页文档

Claude Code comes with built-in commands that you can access by typing a forward slash, but you can also create your own custom commands to automate repetitive tasks you run frequently.

Claude Code 自带内置命令（built-in commands），你可以通过输入斜杠来使用它们。此外，你还可以创建自己的自定义命令（custom commands），从而自动执行那些你经常重复的任务。

### Creating Custom Commands

创建自定义命令

To create a custom command, you need to set up a specific folder structure in your project:

要创建一个自定义命令，你需要在你的项目里设置一个特定的文件夹结构：

1 Find the .claude folder in your project directory

在你的项目目录中找到 .claude 文件夹

2 Create a new directory called commands inside it

在该文件夹内创建一个名为 commands 的新目录以你想要的命令名称

3 Create a new markdown file with your desired command name (like audit.md)

创建一个新的 markdown 文件（例如 audit.md）

The filename becomes your command name - so audit.md creates the /audit command.

这个文件名就是你的命令名称 —— 所以 audit.md 会生成 /audit 命令。

### Example: Audit Command

示例：审计命令（Audit Command）

Here's a practical example of a custom command that audits project dependencies for vulnerabilities:

下面是一个自定义命令（custom command）的实际例子，它可以用来审计项目依赖项是否存在安全漏洞：

This audit command does three things:

这个审计命令主要执行以下三项任务：

1 Runs npm audit to find vulnerable installed packages

运行 npm audit，找出已安装包中存在的安全漏洞。

2 Runs npm audit fix to apply updates

运行 npm audit fix，应用修复补丁来解决这些漏洞。

3 Runs tests to verify the updates didn't break anything

运行测试，验证这些更新没有引入任何问题。

After creating your command file, you must restart Claude Code for it to recognize the new command.

创建好命令文件后，您必须重启 Claude Code，它才能识别并加载新命令。

### Commands with Arguments

Custom commands can accept arguments using the $ARGUMENTS placeholder. This makes them much more flexible and reusable.

带参数的命令自定义命令（custom commands）可以通过 $ARGUMENTS 占位符来接收参数。这让它们变得更加灵活，也更容易重复使用。

For example, a write_tests.md command might contain:

例如，一个名为 `write_tests.md` 的命令可能会包含：

```md
Write comprehensive tests for: $ARGUMENTS

Testing conventions:
* Use Vitests with React Testing Library
* Place test files in a __tests__ directory in the same folder as the source file
* Name test files as [filename].test.ts(x)
* Use @/ prefix for imports

Coverage:
* Test happy paths
* Test edge cases
* Test error states
```

You can then run this command with a file path:

你可以通过以下命令并指定一个文件路径来执行此操作：

/write_tests the use-auth.ts file in the hooks directory 

The arguments don't have to be file paths - they can be any string you want to pass to give Claude context and direction for the task.

这些参数不必是文件路径，它们可以是任何你希望传递的字符串，用于为 Claude 提供任务的上下文和指引。

### Key Benefits

主要优势

Automation - Turn repetitive workflows into single commands

自动化 - 将重复的工作流程转化为一个命令

Consistency - Ensure the same steps are followed every time

一致性 - 确保每一次都能遵循相同的步骤

Context - Provide Claude with specific instructions and conventions for your project

上下文 - 为 Claude 提供项目所需的具体指令和规范

Flexibility - Use arguments to make commands work with different inputs

灵活性 - 利用参数使命令能够处理不同的输入

Custom commands are particularly useful for project-specific workflows like running test suites, deploying code, or generating boilerplate following your team's conventions.

自定义命令（Custom commands）在处理特定项目的工作流程时尤其有用，比如运行测试套件、部署代码，或者生成符合团队规范的样板代码。