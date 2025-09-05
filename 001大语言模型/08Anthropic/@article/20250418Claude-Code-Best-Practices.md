## 20250418Claude-Code-Best-Practices

[Claude Code Best Practices \ Anthropic](https://www.anthropic.com/engineering/claude-code-best-practices)

[Engineering at Anthropic](https://www.anthropic.com/engineering)# Claude Code: Best practices for agentic coding

Published Apr 18, 2025

Claude Code is a command line tool for agentic coding. This post covers tips and tricks that have proven effective for using Claude Code across various codebases, languages, and environments.

Claude Code 是一个支持智能体编码（agentic coding）的命令行工具。本文将分享在使用 Claude Code 时行之有效的使用技巧，这些技巧适用于不同的代码库、编程语言和开发环境。

We recently released Claude Code, a command line tool for agentic coding. Developed as a research project, Claude Code gives Anthropic engineers and researchers a more native way to integrate Claude into their coding workflows.

Anthropic 公司最近发布了 Claude Code，这是一个用于代理式编程（agentic coding）的命令行工具。Claude Code 是作为一个研究项目开发的，它能让 Anthropic 的工程师和研究人员以一种更自然、更紧密的方式，将 Claude 大模型集成到他们的日常编码工作中。

Claude Code is intentionally low-level and unopinionated, providing close to raw model access without forcing specific workflows. This design philosophy creates a flexible, customizable, scriptable, and safe power tool. While powerful, this flexibility presents a learning curve for engineers new to agentic coding tools—at least until they develop their own best practices.

Claude Code 的设计初衷是保持底层和开放性，它不强制用户遵循特定的工作流程，而是提供接近原始模型的访问权限。这种设计理念造就了一个强大、灵活、可定制、可脚本化且高度安全的工具。尽管功能强大，但这种高度的灵活性也意味着，对于初次接触 AI 智能体（AI Agent）编码工具的工程师来说，需要一个适应和学习的过程 —— 至少在他们摸索出自己的最佳实践之前是如此。

This post outlines general patterns that have proven effective, both for Anthropic's internal teams and for external engineers using Claude Code across various codebases, languages, and environments. Nothing in this list is set in stone nor universally applicable; consider these suggestions as starting points. We encourage you to experiment and find what works best for you!

本文概述了一些已被证实行之有效的通用模式，这些模式不仅对 Anthropic 内部团队有效，也适用于使用 Claude Code 的外部工程师在各种代码库、编程语言和不同环境中的实践。请注意，这份清单上的内容并非一成不变，也并非普遍适用；您可以将这些建议视为一个起点。我们鼓励您积极尝试，找到最适合您的方法！

Looking for more detailed information? Our comprehensive documentation at claude.ai/code covers all the features mentioned in this post and provides additional examples, implementation details, and advanced techniques.

正在寻找更详细的信息吗？我们在 claude.ai/code 的全面文档涵盖了本文中介绍的所有功能，并提供了更多示例、实现细节和高级技术。

### 01. Customize your setup

个性化你的配置

Claude Code is an agentic coding assistant that automatically pulls context into prompts. This context gathering consumes time and tokens, but you can optimize it through environment tuning.

Claude Code 是一个 AI 智能体（AI Agent）编码助手，它能够自动将上下文信息引入到提示（prompts）中。这种上下文收集过程会消耗时间和计算资源（token），但你可以通过优化其运行环境来提升效率。

a. Create CLAUDE.md files

创建 CLAUDE.md 文件

CLAUDE.md is a special file that Claude automatically pulls into context when starting a conversation. This makes it an ideal place for documenting:

CLAUDE.md 是一种特殊文件，Claude 在开始对话时会自动将其加载到上下文（context）中。因此，它非常适合用来记录：

1 Common bash commands

常用的 bash 命令

2 Core files and utility functions

核心文件和实用函数

3 Code style guidelines

代码风格指南

4 Testing instructions

测试说明

5 Repository etiquette (e.g., branch naming, merge vs. rebase, etc.)

代码仓库规范（例如，分支命名，合并（merge）与变基（rebase）的选择等）

6 Developer environment setup (e.g., pyenv use, which compilers work)

开发者环境配置（例如，pyenv 的使用，哪些编译器（compiler）可用等）

7 Any unexpected behaviors or warnings particular to the project

项目特有的任何异常行为或警告

8 Other information you want Claude to remember

您希望 Claude 记住的其他信息

There's no required format for CLAUDE.md files. We recommend keeping them concise and human-readable. For example:

CLAUDE.md 文件并没有强制的格式要求。我们建议让它们保持简洁且易于阅读。例如：

```
# Bash commands
- npm run build: Build the project
- npm run typecheck: Run the typechecker
# Code style
- Use ES modules (import/export) syntax, not CommonJS (require)
- Destructure imports when possible (eg. import { foo } from 'bar')
# Workflow
- Be sure to typecheck when you’re done making a series of code changes
- Prefer running single tests, and not the whole test suite, for performance
```

```
# Bash 命令
- npm run build：构建项目
- npm run typecheck：运行类型检查器
# 代码风格
- 使用 ES 模块（ES modules）的 import/export 语法，而不是 CommonJS 的 require
- 尽可能解构导入（destructure imports），例如 import {foo} from 'bar'
# 工作流程
- 完成一系列代码更改后，务必进行类型检查
- 为了提升性能，优先运行单个测试，而非整个测试套件
```

You can place CLAUDE.md files in several locations:

CLAUDE.md 文件可以放置在以下几个位置：

1 The root of your repo, or wherever you run claude from (the most common usage). Name it CLAUDE.md and check it into git so that you can share it across sessions and with your team (recommended), or name it CLAUDE.local.md and .gitignore it

你的代码仓库根目录，或者你运行 claude 的目录（这是最常见的用法）。你可以将文件命名为 CLAUDE.md 并提交到 Git 仓库，这样就能在不同的会话中与团队成员共享（推荐这样做）；或者，你也可以将其命名为 CLAUDE.local.md 并将其添加到 .gitignore 文件中，使其不被 Git 追踪。

2 Any parent of the directory where you run claude. This is most useful for monorepos, where you might run claude from root/foo, and have CLAUDE.md files in both root/CLAUDE.md and root/foo/CLAUDE.md. Both of these will be pulled into context automatically

你运行 claude 命令的目录的任何父级目录。这对于单体仓库（monorepos）场景最为实用，比如你可能在 `root/foo` 目录下运行 claude，并且在 `root/CLAUDE.md` 和 `root/foo/CLAUDE.md` 中都存在 `CLAUDE.md` 文件。这两个文件都会被自动加载到上下文中。

3 Any child of the directory where you run claude. This is the inverse of the above, and in this case, Claude will pull in CLAUDE.md files on demand when you work with files in child directories

你运行 Claude 的目录下的任何子目录。这与上述情况正好相反，在这种情况下，当你处理子目录中的文件时，Claude 将按需（即需要时）加载 CLAUDE.md 文件。

4 Your home folder (~/.claude/CLAUDE.md), which applies it to all your claude sessions

你的主文件夹（~/.claude/CLAUDE.md），其中配置会应用到你所有的 Claude 会话中。

5 When you run the /init command, Claude will automatically generate a CLAUDE.md for you.

当你运行 /init 命令时，Claude 会自动为你生成一个 CLAUDE.md 文件。

b. Tune your CLAUDE.md files

调整你的 CLAUDE.md 文件

Your CLAUDE.md files become part of Claude's prompts, so they should be refined like any frequently used prompt. A common mistake is adding extensive content without iterating on its effectiveness. Take time to experiment and determine what produces the best instruction following from the model.

你的 CLAUDE.md 文件会成为 Claude 接收的提示（prompt，即你给它的指令）的一部分，所以它们应该像其他经常使用的提示词一样，经过反复的推敲和优化。一个常见的错误是，在不迭代验证效果的情况下，就添加了大量的内容。你需要花时间去实验，看看什么能让模型更好地遵循你的指令。

You can add content to your CLAUDE.md manually or press the # key to give Claude an instruction that it will automatically incorporate into the relevant CLAUDE.md. Many engineers use # frequently to document commands, files, and style guidelines while coding, then include CLAUDE.md changes in commits so team members benefit as well.

你可以手动将内容添加到你的 CLAUDE.md 文件中，也可以按下 # 键，向 Claude 发出指令，它会将这些指令自动收录到对应的 CLAUDE.md 文件里。许多工程师在编写代码时，经常利用 # 来记录命令、文件和编码风格指南，然后将这些 CLAUDE.md 文件的更改随提交（commit）一并提交，这样团队成员也能从中受益。

At Anthropic, we occasionally run CLAUDE.md files through the prompt improver and often tune instructions (e.g. adding emphasis with "IMPORTANT" or "YOU MUST") to improve adherence.

在 Anthropic，我们偶尔会用提示词改进器（prompt improver）处理 CLAUDE.md 文件，并且经常调整指令（例如，通过添加「IMPORTANT」或「YOU MUST」等强调词语）来提高模型遵循指令的能力。

c. Curate Claude's list of allowed tools

c. 配置 Claude 的工具允许列表

By default, Claude Code requests permission for any action that might modify your system: file writes, many bash commands, MCP tools, etc. We designed Claude Code with this deliberately conservative approach to prioritize safety. You can customize the allowlist to permit additional tools that you know are safe, or to allow potentially unsafe tools that are easy to undo (e.g., file editing, git commit).

默认情况下，Claude Code 会请求执行任何可能修改你系统的操作的权限，比如文件写入、运行许多 bash 命令以及使用 MCP 工具等。我们设计 Claude Code 时，就采用了这种刻意保守的策略，目的就是将安全性放在首位。你可以自定义这个允许列表（allowlist），来允许你确认安全的额外工具，或者允许那些虽然可能不安全但很容易撤销的操作工具（例如：文件编辑、git commit）。

There are four ways to manage allowed tools:

有四种方式来管理允许的工具：

1 Select "Always allow" when prompted during a session.

在会话过程中收到提示时，选择「始终允许」。

2 Use the /permissions command after starting Claude Code to add or remove tools from the allowlist. For example, you can add Edit to always allow file edits, Bash(git commit:*) to allow git commits, or mcp__puppeteer__puppeteer_navigate to allow navigating with the Puppeteer MCP server.

启动 Claude Code 后，使用 `/permissions` 命令可以从白名单中添加或移除工具。例如，你可以添加 Edit 以始终允许文件编辑；添加 Bash（git commit:*）来允许 git 提交；或者添加 mcp__puppeteer__puppeteer_navigate，以允许通过 Puppeteer MCP 服务器进行导航。

3 Manually edit your .claude/settings.json or ~/.claude.json (we recommend checking the former into source control to share with your team).

你可以手动编辑 .claude/settings.json 或～/.claude.json 文件 （我们建议将前者纳入版本控制，以便与你的团队共享）。

4 Use the --allowedTools CLI flag for session-specific permissions.

使用 --allowedTools CLI 标志，可以设置会话专属的权限。

d. If using GitHub, install the gh CLI

如果使用 GitHub，请安装 gh CLI（gh CLI）

Claude knows how to use the gh CLI to interact with GitHub for creating issues, opening pull requests, reading comments, and more. Without gh installed, Claude can still use the GitHub API or MCP server (if you have it installed).

Claude 知道如何使用 gh CLI（gh CLI）与 GitHub 交互，例如创建议题（issues）、开启拉取请求（pull requests）和阅读评论（comments）等。如果没有安装 gh CLI，Claude 仍然可以使用 GitHub API 或者 MCP 服务器（MCP server）（如果您已经安装了后者）。

### 02. Give Claude more tools

为 Claude 提供更多工具

Claude has access to your shell environment, where you can build up sets of convenience scripts and functions for it just like you would for yourself. It can also leverage more complex tools through MCP and REST APIs.

Claude 可以访问你的 shell 环境（shell environment），你可以像给自己准备工具一样，为它构建一系列便捷的脚本和函数。它还可以通过 MCP（MCP）和 REST API（REST API）来调用更复杂的工具。

a. Use Claude with bash tools

使用 Claude 结合 bash 工具

Claude Code inherits your bash environment, giving it access to all your tools. While Claude knows common utilities like unix tools and gh, it won't know about your custom bash tools without instructions:

Claude Code 能够利用你现有的 bash 环境，从而可以访问你所有的工具。尽管 Claude 熟悉常见的实用工具，例如 Unix 工具和 gh，但如果未提供相关指令，它将无法识别或使用你自定义的 bash 工具：

1 Tell Claude the tool name with usage examples

告诉 Claude 工具名称以及如何使用它

2 Tell Claude to run --help to see tool documentation

告诉 Claude 运行 --help 以查看工具文档

3 Document frequently used tools in CLAUDE.md

在 CLAUDE.md 中记录常用工具

b. Use Claude with MCP

b. 将 Claude 与 MCP 结合使用

Claude Code functions as both an MCP server and client. As a client, it can connect to any number of MCP servers to access their tools in three ways:

Claude Code 既能充当 MCP 服务器，也能充当 MCP 客户端（MCP client）。作为客户端，它可以连接到任意数量的 MCP 服务器（MCP server），并通过以下三种方式访问这些服务器提供的工具：

1 In project config (available when running Claude Code in that directory)

通过项目配置（project config）来访问（当你在特定目录中运行 Claude Code 时，此配置便会生效）

1 In global config (available in all projects)

在全局配置文件中（所有项目均可使用）。

2 In a checked-in .mcp.json file (available to anyone working in your codebase). For example, you can add Puppeteer and Sentry servers to your .mcp.json, so that every engineer working on your repo can use these out of the box.

在已纳入版本控制的 .mcp.json 文件中（团队中任何访问你代码库的成员均可使用）。例如，你可以将 Puppeteer 和 Sentry 服务器添加到你的 .mcp.json 文件中，这样所有在你的代码库上工作的工程师都能够开箱即用地使用它们。

When working with MCP, it can also be helpful to launch Claude with the --mcp-debug flag to help identify configuration issues.

在使用 MCP 工作时，启动 Claude 并附带 `--mcp-debug` 标志也会很有用，这有助于识别配置问题。

c. Use custom slash commands

使用自定义斜杠命令

For repeated workflows—debugging loops, log analysis, etc.—store prompt templates in Markdown files within the .claude/commands folder. These become available through the slash commands menu when you type /. You can check these commands into git to make them available for the rest of your team.

对于重复性的工作流程 —— 例如调试循环、日志分析等 —— 您可以将提示模板（prompt templates）存储在 .claude/commands 文件夹内的 Markdown 文件中。当您输入 / 时，这些模板就会通过斜杠命令菜单显示出来。您可以将这些命令提交到 Git 中，以便团队的其他成员也能使用它们。

Custom slash commands can include the special keyword $ARGUMENTS to pass parameters from command invocation.

自定义斜杠命令（slash command）可以使用特殊关键字 $ARGUMENTS，以便在调用命令时传递参数。

For example, here's a slash command that you could use to automatically pull and fix a Github issue:

例如，下面是一个斜杠命令，你可以用它来自动拉取并修复一个 Github 问题：

```
Please analyze and fix the GitHub issue: $ARGUMENTS.

Follow these steps:

1. Use `gh issue view` to get the issue details
2. Understand the problem described in the issue
3. Search the codebase for relevant files
4. Implement the necessary changes to fix the issue
5. Write and run tests to verify the fix
6. Ensure code passes linting and type checking
7. Create a descriptive commit message
8. Push and create a PR

Remember to use the GitHub CLI (`gh`) for all GitHub-related tasks.
```

```
请分析并解决此 GitHub 问题：$ARGUMENTS。

请按照以下步骤操作：

1 使用 `gh issue view` 获取问题详情
2 理解工单（issue）中描述的具体问题
3 在代码库中搜索相关文件
4 执行必要的修改，以解决问题
5 编写并运行测试，以验证修复效果
6 确保代码通过 linting（linting）检查和类型检查
7 创建一个描述性的提交消息
8 推送并创建一个 PR

请记住，所有 GitHub 相关的任务都要使用 GitHub CLI（`gh`）来完成。
```

Putting the above content into .claude/commands/fix-github-issue.md makes it available as the /project:fix-github-issue command in Claude Code. You could then for example use /project:fix-github-issue 1234 to have Claude fix issue #1234. Similarly, you can add your own personal commands to the ~/.claude/commands folder for commands you want available in all of your sessions.

将上述内容保存到 .claude/commands/fix-github-issue.md 文件中后，它就能在 Claude Code 中作为 `/project:fix-github-issue` 命令使用了。举例来说，您可以使用 `/project:fix-github-issue 1234` 让 Claude 来处理 GitHub 上的 #1234 号问题。同样，您也可以将自己的专属命令添加到 `~/.claude/commands` 文件夹中，这样这些命令就能在您的所有会话中随时调用。

## 03. Try common workflows

尝试常见工作流程

Claude Code doesn't impose a specific workflow, giving you the flexibility to use it how you want. Within the space this flexibility affords, several successful patterns for effectively using Claude Code have emerged across our community of users:

Claude Code 不会强制用户遵循特定的工作流程，这赋予了你极大的自由，可以按照自己的方式使用它。在这样灵活的使用空间里，我们的用户社区逐渐摸索出了几种有效利用 Claude Code 的成功模式：

a. Explore, plan, code, commit

探索、规划、编码、提交

This versatile workflow suits many problems:

这种灵活的工作流程适用于许多问题：

1 Ask Claude to read relevant files, images, or URLs, providing either general pointers ("read the file that handles logging") or specific filenames ("read logging.py"), but explicitly tell it not to write any code just yet.This is the part of the workflow where you should consider strong use of subagents, especially for complex problems. Telling Claude to use subagents to verify details or investigate particular questions it might have, especially early on in a conversation or task, tends to preserve context availability without much downside in terms of lost efficiency.

这一步是让 Claude 阅读相关文件、图片或 URL。你可以给出泛泛的提示（比如「阅读处理日志的文件」），也可以提供具体的文件名（例如「阅读 logging.py」），但务必明确告诉它，目前还不要编写任何代码。在处理复杂问题时，这是工作流程中您应该着重考虑使用子智能体（subagents）的阶段。让 Claude 使用子智能体（subagents）来核实细节或探究它可能遇到的特定问题，尤其是在对话或任务的早期，通常能很好地保持上下文可用性，同时又不会损失太多效率。

2. This is the part of the workflow where you should consider strong use of subagents, especially for complex problems. Telling Claude to use subagents to verify details or investigate particular questions it might have, especially early on in a conversation or task, tends to preserve context availability without much downside in terms of lost efficiency.

2. 在工作流程的这一环节，我们应该着重考虑使用子智能体（subagents），尤其是在处理复杂问题时。指示 Claude 调用子智能体来核实细节，或者探究它可能遇到的具体问题，特别是在一次对话或一项任务的早期阶段，通常有助于保持上下文的可用性，同时又不会明显牺牲效率。

3. Ask Claude to make a plan for how to approach a specific problem. We recommend using the word "think" to trigger extended thinking mode, which gives Claude additional computation time to evaluate alternatives more thoroughly. These specific phrases are mapped directly to increasing levels of thinking budget in the system: "think" < "think hard" < "think harder" < "ultrathink." Each level allocates progressively more thinking budget for Claude to use.If the results of this step seem reasonable, you can have Claude create a document or a GitHub issue with its plan so that you can reset to this spot if the implementation (step 3) isn't what you want.

3. 让 Claude 为解决特定问题制定一份计划。我们建议使用「think」这个词来触发扩展思考模式，这样能让 Claude 获得额外的计算时间，从而更全面地评估各种备选方案。系统将这些特定短语直接对应到逐步递增的思考预算级别：」think」<」think hard」<」think harder」<」ultrathink」。每个级别都会为 Claude 分配更多的思考预算。如果这一步的结果看起来合理，你可以让 Claude 根据其计划生成一个文档或一个 GitHub issue，这样如果后续的实施（第 3 步）不尽如人意，你可以随时回到这一步。

4. If the results of this step seem reasonable, you can have Claude create a document or a GitHub issue with its plan so that you can reset to this spot if the implementation (step 3) isn't what you want.

4. 如果这一步的结果看起来合理，你可以让 Claude 创建一份文档或一个 GitHub issue（GitHub issue），里面详细说明它的计划。这样一来，如果后续的实现（第三步）不符合你的预期，你就可以轻松地回溯到这个节点。

5. Ask Claude to implement its solution in code. This is also a good place to ask it to explicitly verify the reasonableness of its solution as it implements pieces of the solution.

5. 让 Claude 用代码实现其解决方案。同时，在它逐步实现方案的过程中，我们还可以要求它明确验证其解决方案的合理性。

6. Ask Claude to commit the result and create a pull request. If relevant, this is also a good time to have Claude update any READMEs or changelogs with an explanation of what it just did.

6. 让 Claude 提交最终成果，并创建一个拉取请求（pull request）。如果适用，这也是一个好时机，让 Claude 更新项目中的任何 README 文档或更新日志（changelog），并解释它刚刚完成了哪些工作。

Steps #1-#2 are crucial—without them, Claude tends to jump straight to coding a solution. While sometimes that's what you want, asking Claude to research and plan first significantly improves performance for problems requiring deeper thinking upfront.

步骤 #1-#2 至关重要 —— 如果没有它们，Claude 往往会直接着手编写解决方案。虽然有时你可能需要这种直接的方式，但如果先让 Claude 进行研究和规划，那么在解决那些需要前期深入思考的问题时，其表现会显著提升。

### b. Write tests, commit; code, iterate, commit

This is an Anthropic-favorite workflow for changes that are easily verifiable with unit, integration, or end-to-end tests. Test-driven development (TDD) becomes even more powerful with agentic coding:

### b. 编写测试、提交；编写代码、迭代、再提交这是 Anthropic 公司偏爱的一种工作流程，特别适合那些可以通过单元测试、集成测试或端到端测试轻松验证的改动。当与智能体编码（agentic coding）结合使用时，测试驱动开发（TDD）的威力会变得更加强大：

1. Ask Claude to write tests based on expected input/output pairs. Be explicit about the fact that you're doing test-driven development so that it avoids creating mock implementations, even for functionality that doesn't exist yet in the codebase.

1. 让 Claude 根据预期的输入 / 输出对来编写测试。请明确说明你正在进行测试驱动开发（test-driven development），这样它就不会创建模拟实现（mock implementations），即使是针对代码库中尚未实现的功能。

2. Tell Claude to run the tests and confirm they fail. Explicitly telling it not to write any implementation code at this stage is often helpful.

3. Ask Claude to commit the tests when you're satisfied with them.

2. 告诉 Claude 运行测试并确认它们会失败。通常，明确指出在此阶段无需编写任何实现代码会很有帮助。

3. 当你对测试感到满意时，要求 Claude 提交测试。

4. Ask Claude to write code that passes the tests, instructing it not to modify the tests. Tell Claude to keep going until all tests pass. It will usually take a few iterations for Claude to write code, run the tests, adjust the code, and run the tests again.At this stage, it can help to ask it to verify with independent subagents that the implementation isn't overfitting to the tests

4. 要求 Claude 编写能通过测试的代码，并明确告诉它不要修改测试。让 Claude 持续尝试，直到所有测试都通过为止。通常，Claude 会经历多次迭代过程，包括编写代码、运行测试、调整代码，然后再次运行测试。在这个阶段，让独立的子智能体（AI Agent）来验证其实现是否没有过度拟合（overfitting）到测试，会有所帮助。

5. At this stage, it can help to ask it to verify with independent subagents that the implementation isn't overfitting to the tests

6. Ask Claude to commit the code once you're satisfied with the changes.

5. 在这个阶段，我们可以要求它借助独立的子智能体（subagents）来验证，确保代码的实现没有对测试集产生过拟合（overfitting）现象。

6. 一旦你对修改满意，就可以让 Claude 提交代码。

Claude performs best when it has a clear target to iterate against—a visual mock, a test case, or another kind of output. By providing expected outputs like tests, Claude can make changes, evaluate results, and incrementally improve until it succeeds.

当有一个明确的目标可以反复优化时，Claude 的表现最佳 —— 例如一个视觉原型（visual mock）、一个测试用例，或者其他形式的输出。通过提供像测试这样的预期输出，Claude 能够进行修改，评估结果，并逐步改进，直至最终成功。

### c. Write code, screenshot result, iterate

Similar to the testing workflow, you can provide Claude with visual targets:

### c. 编写代码，截取结果，并不断优化这与传统的测试工作流程类似，你可以为 Claude 提供可视化的具体任务目标：

1. Give Claude a way to take browser screenshots (e.g., with the Puppeteer MCP server, an iOS simulator MCP server, or manually copy / paste screenshots into Claude).

1. 为 Claude 提供一种截取浏览器屏幕截图的方式（例如，通过 Puppeteer MCP 服务器、iOS 模拟器 MCP 服务器，或者手动将屏幕截图复制 / 粘贴到 Claude 中）。

2. Give Claude a visual mock by copying / pasting or drag-dropping an image, or giving Claude the image file path.

3. Ask Claude to implement the design in code, take screenshots of the result, and iterate until its result matches the mock.

2. 可以通过复制 / 粘贴、拖放图片，或者提供图片文件路径的方式，给 Claude 一个视觉设计稿。

3. 接着，请 Claude 将该设计用代码实现出来，并截取结果的屏幕截图，然后不断迭代优化，直到最终结果与设计稿完全匹配。

4. Ask Claude to commit when you're satisfied.

Like humans, Claude's outputs tend to improve significantly with iteration. While the first version might be good, after 2-3 iterations it will typically look much better. Give Claude the tools to see its outputs for best results.

4. 当你满意时，让 Claude 最终确定（或采纳）。

和人类一样，Claude 的输出（或结果）也往往会通过反复迭代（iteration）显著改善。尽管第一个版本可能已经不错，但在经过 2-3 次迭代后，其效果通常会好得多。因此，提供工具让 Claude 能够查看其输出，将能带来最佳结果。

### d. Safe YOLO mode

Instead of supervising Claude, you can use claude --dangerously-skip-permissions to bypass all permission checks and let Claude work uninterrupted until completion. This works well for workflows like fixing lint errors or generating boilerplate code.

### d. 安全 YOLO（YOLO）模式与其一直监督 Claude，不如使用 `claude --dangerously-skip-permissions` 命令来绕过所有权限检查，让 Claude 不间断地运行直到任务完成。这种模式非常适合处理像修复 lint 错误或生成样板代码这类工作流任务。

Letting Claude run arbitrary commands is risky and can result in data loss, system corruption, or even data exfiltration (e.g., via prompt injection attacks). To minimize these risks, use --dangerously-skip-permissions in a container without internet access. You can follow this reference implementation using Docker Dev Containers.

允许 Claude 运行任意命令具有很高风险，可能导致数据丢失、系统损坏，甚至引发数据外泄（例如，通过提示注入攻击（prompt injection attacks））。为了将这些风险降到最低，建议您在没有互联网访问的容器中使用 `--dangerously-skip-permissions` 参数。您可以参考以下实现方案，它利用了 Docker Dev Containers（Docker Dev Containers）。

### e. Codebase Q&A

When onboarding to a new codebase, use Claude Code for learning and exploration. You can ask Claude the same sorts of questions you would ask another engineer on the project when pair programming. Claude can agentically search the codebase to answer general questions like:

### e. 代码库问答当你需要熟悉一个新的代码库时，可以使用 Claude Code 来学习和探索。你可以向 Claude 提出各种问题，就像你在结对编程时会询问项目中的另一位工程师一样。Claude 能够像 AI 智能体（AI Agent）一样自主搜索代码库，从而回答一些通用问题，例如：

* How does logging work?

* How do I make a new API endpoint?

* 日志功能是如何运作的？

* 我如何创建一个新的 API 端点？

* What does async move { ... } do on line 134 of foo.rs?

* What edge cases does CustomerOnboardingFlowImpl handle?

* `async move {...}` 在 foo.rs 文件的第 134 行是做什么用的？

* `CustomerOnboardingFlowImpl` 类会处理哪些边缘情况？

* Why are we calling foo() instead of bar() on line 333?

* What's the equivalent of line 334 of baz.py in Java?

* 为什么第 333 行调用的是 foo（）而不是 bar（)？

* baz.py 文件中第 334 行的代码，在 Java 中对应的写法是什么？

At Anthropic, using Claude Code in this way has become our core onboarding workflow, significantly improving ramp-up time and reducing load on other engineers. No special prompting is required! Simply ask questions, and Claude will explore the code to find answers.

在 Anthropic，以这种方式使用 Claude Code（Claude Code）已经成为我们核心的新人培训流程（onboarding workflow），它显著缩短了工程师的上手时间（ramp-up time），并减轻了其他工程师的工作量。不需要特殊的提示词（prompting)！你只需提出问题，Claude 就会深入探索代码来寻找答案。

### f. Use Claude to interact with git

Claude can effectively handle many git operations. Many Anthropic engineers use Claude for 90%+ of our git interactions:

### f. 用 Claude 进行 git 操作

Claude 能够高效地处理各种 git 操作。许多 Anthropic 的工程师在他们的日常工作中，90% 以上的 git 交互都借助于 Claude 完成。

* Searching git history to answer questions like "What changes made it into v1.2.3?", "Who owns this particular feature?", or "Why was this API designed this way?" It helps to explicitly prompt Claude to look through git history to answer queries like these.

* 我们可以通过搜索 git 历史来回答一些关键问题，比如「v1.2.3 版本中包含了哪些更改？」，「这个特定功能是由谁负责的？」，或者「为什么这个 API 是这样设计的？」。为了有效地回答这类查询，明确地提示 Claude 去查看 git 历史会很有帮助。

* Writing commit messages. Claude will look at your changes and recent history automatically to compose a message taking all the relevant context into account

* Handling complex git operations like reverting files, resolving rebase conflicts, and comparing and grafting patches

*  编写提交信息：Claude 会自动查看您的代码更改和近期操作历史，从而综合所有相关上下文来生成提交信息。
*  处理复杂的 Git 操作：例如恢复文件、解决变基（rebase）冲突，以及比较和应用补丁。

### g. Use Claude to interact with GitHub

Claude Code can manage many GitHub interactions:

### g. 使用 Claude 与 GitHub 交互

Claude Code 能够处理多种 GitHub 交互：

* Creating pull requests: Claude understands the shorthand "pr" and will generate appropriate commit messages based on the diff and surrounding context.

* Implementing one-shot resolutions for simple code review comments: just tell it to fix comments on your PR (optionally, give it more specific instructions) and push back to the PR branch when it's done.

*  创建合并请求（pull requests)：Claude 能够理解「pr」这个简写，并根据代码差异（diff）和上下文生成合适的提交信息（commit messages）。
*  对简单的代码审查评论（code review comments）实现「一次性解决」：你只需告诉它修复你的合并请求（PR）上的评论（也可以选择性地给出更具体的指示），它就会在完成后将改动推送回对应的 PR 分支。

* Fixing failing builds or linter warnings

* Categorizing and triaging open issues by asking Claude to loop over open GitHub issues

* 修复失败的代码构建或 linter 警告
* 通过让 Claude 逐一检查开放的 GitHub issue，来对这些待处理的问题进行分类和分级

This eliminates the need to remember gh command line syntax while automating routine tasks.

### h. Use Claude to work with Jupyter notebooks

这样一来，在自动化日常任务时，您就不再需要记住 gh 命令行语法了。

### h. 使用 Claude 协助处理 Jupyter notebook

Researchers and data scientists at Anthropic use Claude Code to read and write Jupyter notebooks. Claude can interpret outputs, including images, providing a fast way to explore and interact with data. There are no required prompts or workflows, but a workflow we recommend is to have Claude Code and a .ipynb file open side-by-side in VS Code.

Anthropic 的研究人员和数据科学家利用 Claude Code 阅读并编写 Jupyter notebooks。Claude 能够解读包括图像在内的各种输出，为探索和处理数据提供了一种快捷高效的方法。尽管使用上没有强制性的提示词（prompts）或工作流程（workflows）限制，但我们推荐的一种做法是，在 VS Code 中同时打开 Claude Code 和 .ipynb 文件，让它们并排显示。

You can also ask Claude to clean up or make aesthetic improvements to your Jupyter notebook before you show it to colleagues. Specifically telling it to make the notebook or its data visualizations "aesthetically pleasing" tends to help remind it that it's optimizing for a human viewing experience.

你还可以请 Claude 在你向同事展示 Jupyter notebook 之前，对它进行清理或进行美化。具体来说，当你告诉它要让 notebook 或其数据可视化「美观悦目」时，这有助于提醒它，它正在为优化人类的观看体验而努力。

### 04. Optimize your workflow

优化你的工作流程

The suggestions below apply across all workflows:

以下建议适用于所有工作流程：

### a. Be specific in your instructions

Claude Code's success rate improves significantly with more specific instructions, especially on first attempts. Giving clear directions upfront reduces the need for course corrections later.

### a. 明确你的指令当指令越具体时，Claude Code 的成功率就会显著提升，尤其是在第一次尝试时。提前给出清晰的指示，能有效减少后续调整的必要。

For example:

Poor Good add tests for foo.py write a new test case for foo.py, covering the edge case where the user is logged out. avoid mocks why does ExecutionFactory have such a weird api? look through ExecutionFactory's git history and summarize how its api came to be add a calendar widget look at how existing widgets are implemented on the home page to understand the patterns and specifically how code and interfaces are separated out. HotDogWidget.php is a good example to start with. then, follow the pattern to implement a new calendar widget that lets the user select a month and paginate forwards/backwards to pick a year. Build from scratch without libraries other than the ones already used in the rest of the codebase. Claude can infer intent, but it can't read minds. Specificity leads to better alignment with expectations.

例如：

不佳示例良好示例为 foo.py 添加测试为 foo.py 编写一个新的测试用例，覆盖用户登出时的边缘情况。
避免使用模拟对象（mocks）为什么 ExecutionFactory 的 API 如此奇怪？ 查阅 ExecutionFactory 的 Git 历史记录，总结其 API 是如何形成的。
添加一个日历小部件了解主页上现有小部件的实现方式，以理解其模式，特别是代码和接口是如何分离的。HotDogWidget.php 是一个很好的起点。然后，遵循该模式实现一个新的日历小部件，允许用户选择月份并向前 / 向后翻页以选择年份。除了代码库其余部分已使用的库之外，不使用其他库，从头开始构建。
Claude 可以推断意图，但它不能读懂你的心思。明确具体的指令才能更好地与你的预期目标保持一致。

### b. Give Claude images

Claude excels with images and diagrams through several methods:

### b. 让 Claude 处理图像

Claude 通过多种方法在处理图像和图表方面表现卓越：

* Paste screenshots (pro tip: hit cmd+ctrl+shift+4 in macOS to screenshot to clipboard and ctrl+v to paste. Note that this is not cmd+v like you would usually use to paste on mac and does not work remotely.)

* 粘贴屏幕截图（小贴士：在 macOS 中，你可以按下 cmd+ctrl+shift+4 键将屏幕截图保存到剪贴板，然后按 ctrl+v 键进行粘贴。请注意，这种粘贴方式与 Mac 上常用的 cmd+v 不同，且不适用于远程连接。）

* Drag and drop images directly into the prompt input

* Provide file paths for images

*  将图片直接拖放到提示输入框中
*  提供图片的存储路径

This is particularly useful when working with design mocks as reference points for UI development, and visual charts for analysis and debugging. If you are not adding visuals to context, it can still be helpful to be clear with Claude about how important it is for the result to be visually appealing.

当利用设计稿（design mocks）作为用户界面（UI）开发的参考点，以及使用图表进行分析和调试时，这一点尤其有用。即使您没有在上下文中添加视觉内容，向 Claude 明确指出结果的视觉吸引力有多重要，也依然会很有帮助。

### c. Mention files you want Claude to look at or work on

Use tab-completion to quickly reference files or folders anywhere in your repository, helping Claude find or update the right resources.

### c. 提及你希望 Claude 查看或处理的文件利用 Tab 补全（tab-completion）功能，你可以快速引用代码仓库中任意位置的文件或文件夹，从而帮助 Claude 更准确地找到或更新所需资源。

### d. Give Claude URLs

Paste specific URLs alongside your prompts for Claude to fetch and read. To avoid permission prompts for the same domains (e.g., docs.foo.com), use /permissions to add domains to your allowlist.

### d. 提供 URL 给 Claude

你可以在提示中附带特定的 URL，让 Claude 访问并阅读。为了避免因相同域名（例如 docs.foo.com）反复出现权限请求，你可以使用 `/permissions` 命令将这些域名添加到你的允许列表中。

### e. Course correct early and often

While auto-accept mode (shift+tab to toggle) lets Claude work autonomously, you'll typically get better results by being an active collaborator and guiding Claude's approach. You can get the best results by thoroughly explaining the task to Claude at the beginning, but you can also course correct Claude at any time.

### e. 及时引导，频繁调整虽然自动接受模式（通过 shift+tab 键切换）能让 Claude 自主运行，但通常情况下，如果你能积极参与并引导 Claude 的工作方式，效果会更好。你可以在一开始就向 Claude 详细说明任务，从而获得最佳结果，不过你也可以随时对 Claude 的工作进行调整和纠正。

These four tools help with course correction:

* Ask Claude to make a plan before coding. Explicitly tell it not to code until you've confirmed its plan looks good.

以下这四种工具能帮助你及时校正方向：

* 在开始编程（coding）之前，让 Claude 先制定一个计划。明确告诉它，只有在你确认其计划可行之后，它才能开始编写代码。

* Press Escape to interrupt Claude during any phase (thinking, tool calls, file edits), preserving context so you can redirect or expand instructions.

* Double-tap Escape to jump back in history, edit a previous prompt, and explore a different direction. You can edit the prompt and repeat until you get the result you're looking for.

* 在 Claude 的任何阶段（无论是思考、工具调用还是文件编辑），按下 Escape 键即可中断它，同时保留上下文信息，这样你就能重新引导或补充指示。

* 双击 Escape 键，可以回溯历史记录，编辑之前的提示词，并尝试不同的思路。你可以反复修改提示词并重复操作，直到获得满意的结果。

* Ask Claude to undo changes, often in conjunction with option #2 to take a different approach.

Though Claude Code occasionally solves problems perfectly on the first attempt, using these correction tools generally produces better solutions faster.

*  要求 Claude 撤销之前的修改，这通常会与选项 #2 配合使用，从而尝试一种不同的解决思路。

虽然 Claude Code 偶尔能一次性完美解决问题，但通常来说，结合使用这些修正工具能更快地得到更好的解决方案。

### f. Use /clear to keep context focused

During long sessions, Claude's context window can fill with irrelevant conversation, file contents, and commands. This can reduce performance and sometimes distract Claude. Use the /clear command frequently between tasks to reset the context window.

### f. 使用 /clear 命令保持上下文聚焦在长时间的会话中，Claude 的上下文窗口（context window）可能会积累不相关的对话、文件内容和命令。这不仅会降低性能，有时还会影响 Claude 对核心任务的处理能力。因此，在切换不同任务时，请频繁使用 /clear 命令来重置上下文窗口。

### g. Use checklists and scratchpads for complex workflows

For large tasks with multiple steps or requiring exhaustive solutions—like code migrations, fixing numerous lint errors, or running complex build scripts—improve performance by having Claude use a Markdown file (or even a GitHub issue!) as a checklist and working scratchpad:

### g. 利用清单和草稿本处理复杂工作流对于那些步骤繁多或需要详尽解决方案的大型任务 —— 比如代码迁移、修正大量代码规范（lint）错误，或者运行复杂的构建脚本 —— 我们可以通过让 Claude 使用一个 Markdown 文件（甚至是一个 GitHub issue!）作为清单和工作草稿区，从而有效提升其工作效率：

For example, to fix a large number of lint issues, you can do the following:

1. Tell Claude to run the lint command and write all resulting errors (with filenames and line numbers) to a Markdown checklist

例如，为了解决大量的代码规范检查（lint）问题，您可以这样做：

1. 指示 Claude 运行 lint 命令，并将所有发现的错误（包括文件名和行号）输出到一个 Markdown 清单（Markdown checklist）中

2. Instruct Claude to address each issue one by one, fixing and verifying before checking it off and moving to the next

### h. Pass data into Claude

2. 指导 Claude 逐一解决每个问题，在核对并确认完成之前进行修复和验证，然后继续下一个问题

### h. 向 Claude 传入数据

Several methods exist for providing data to Claude:

* Copy and paste directly into your prompt (most common approach)

有几种方法可以向 Claude 提供数据：

* 直接复制和粘贴到你的提示词（prompt）中 （这是最常见的方法）

* Pipe into Claude Code (e.g., cat foo.txt | claude), particularly useful for logs, CSVs, and large data

* Tell Claude to pull data via bash commands, MCP tools, or custom slash commands

*  通过管道将数据传输给 Claude Code（例如，`cat foo.txt | claude`），这对于日志、CSV 文件和大数据特别有用

*  让 Claude 通过 bash 命令、MCP 工具或自定义斜杠命令获取数据

* Ask Claude to read files or fetch URLs (works for images too)

Most sessions involve a combination of these approaches. For example, you can pipe in a log file, then tell Claude to use a tool to pull in additional context to debug the logs.

*  让 Claude 读取文件或抓取 URL（甚至适用于图像）

大多数情况下，会话会结合使用这些方法。例如，你可以传入一个日志文件，然后告诉 Claude 使用一个工具来获取额外的上下文，以便调试这些日志。

### 05. Use headless mode to automate your infra

使用无头模式实现基础设施自动化

Claude Code includes headless mode for non-interactive contexts like CI, pre-commit hooks, build scripts, and automation. Use the -p flag with a prompt to enable headless mode, and --output-format stream-json for streaming JSON output.

Claude Code 提供了一种「无头模式（headless mode）」，专门用于 CI（Continuous Integration，持续集成）、pre-commit 钩子（pre-commit hooks）、构建脚本以及其他自动化流程等非交互式环境。要启用无头模式，只需配合提示（prompt）使用 `-p` 标志即可；如果需要输出 JSON 格式的数据流，则使用 `--output-format stream-json` 参数。

Note that headless mode does not persist between sessions. You have to trigger it each session.

### a. Use Claude for issue triage

请注意，无头模式（headless mode）不会在不同的会话之间自动保存或保留。你需要在每次会话时手动开启它。

### a. 使用 Claude 来进行问题分类（issue triage)

Headless mode can power automations triggered by GitHub events, such as when a new issue is created in your repository. For example, the public Claude Code repository uses Claude to inspect new issues as they come in and assign appropriate labels.

无头模式（Headless mode）可以驱动由 GitHub 事件（GitHub events）触发的自动化任务，例如当你的代码仓库中创建一个新的 issue 时。举个例子，公共的 Claude Code 仓库就利用 Claude 来审查收到的新 issue，并为其分配相应的标签（labels）。

### b. Use Claude as a linter

Claude Code can provide subjective code reviews beyond what traditional linting tools detect, identifying issues like typos, stale comments, misleading function or variable names, and more.

### b. 让 Claude 充当代码「巡查员」

Claude Code 不仅仅能像传统代码检查工具那样发现问题，它还能提供更具「主观性」的代码审查，找出那些机器难以察觉的问题，例如：错别字、过时的注释，以及可能导致误解的函数或变量名等等。

### 06. Uplevel with multi-Claude workflows

利用多 Claude 工作流实现进阶

Beyond standalone usage, some of the most powerful applications involve running multiple Claude instances in parallel:

除了单独使用，Claude 最强大的一些应用在于并行运行多个 Claude 实例：

### a. Have one Claude write code; use another Claude to verify

A simple but effective approach is to have one Claude write code while another reviews or tests it. Similar to working with multiple engineers, sometimes having separate context is beneficial:

### a. 让一个 Claude 写代码；让另一个 Claude 来验证一个简单但有效的方法是，让一个 Claude 负责编写代码，而另一个 Claude 则负责审查或测试代码。这有点像多名工程师协作工作，有时让它们拥有独立的上下文（separate context）是很有益的：

1. Use Claude to write code

2. Run /clear or start a second Claude in another terminal

1. 使用 Claude 来编写代码

2. 运行 /clear 指令，或者在另一个终端中启动第二个 Claude

3. Have the second Claude review the first Claude's work

4. Start another Claude (or /clear again) to read both the code and review feedback

3. 让第二个 Claude 审阅第一个 Claude 的工作
4. 启动另一个 Claude（或再次 /clear）来阅读代码和审阅反馈

5. Have this Claude edit the code based on the feedback

You can do something similar with tests: have one Claude write tests, then have another Claude write code to make the tests pass. You can even have your Claude instances communicate with each other by giving them separate working scratchpads and telling them which one to write to and which one to read from.

5. 让这个 Claude （一种大型语言模型） 根据反馈来编辑代码。

你也可以在测试方面做类似的事情：让一个 Claude 编写测试，然后让另一个 Claude 编写代码来让这些测试通过。你甚至可以让你的 Claude 实例相互通信，方法是给它们提供独立的暂存区（scratchpads），并告诉它们该向哪个暂存区写入，又该从哪个暂存区读取。

This separation often yields better results than having a single Claude handle everything.

### b. Have multiple checkouts of your repo

这种分离通常比让一个单一的 Claude 处理所有任务的效果更好。

### b. 对你的代码库进行多次检出（checkout)

Rather than waiting for Claude to complete each step, something many engineers at Anthropic do is:

1. Create 3-4 git checkouts in separate folders

Anthropic 的许多工程师并没有等待 Claude 完成每个步骤，他们通常会这样做：

1. 在不同的文件夹中创建 3-4 个 git checkouts（git checkouts)

2. Open each folder in separate terminal tabs

3. Start Claude in each folder with different tasks

2. 在不同的终端选项卡中打开每个文件夹
3. 在每个文件夹中，为 Claude 分配不同的任务并启动它

4. Cycle through to check progress and approve/deny permission requests

### c. Use git worktrees

4. 定期查看进展，并批准或拒绝权限请求

### c. 使用 git worktrees

This approach shines for multiple independent tasks, offering a lighter-weight alternative to multiple checkouts. Git worktrees allow you to check out multiple branches from the same repository into separate directories. Each worktree has its own working directory with isolated files, while sharing the same Git history and reflog.

这种方法在处理多个独立任务时表现出色，它为需要多次检出（或切换分支）的场景提供了一种更轻量级的替代方案。Git worktrees （工作区）允许你将同一个仓库中的多个分支，分别检出到不同的目录中。每个工作区都有自己独立的工作目录和文件，但它们会共享相同的 Git 历史记录和 reflog。

Using git worktrees enables you to run multiple Claude sessions simultaneously on different parts of your project, each focused on its own independent task. For instance, you might have one Claude refactoring your authentication system while another builds a completely unrelated data visualization component. Since the tasks don't overlap, each Claude can work at full speed without waiting for the other's changes or dealing with merge conflicts:

利用 git worktrees，你就能在项目的不同部分同时启动多个 Claude 会话，每个会话都能专注于各自独立的任务。举个例子，你或许会让一个 Claude 负责重构你的认证系统，而另一个 Claude 则可以同时构建一个完全不相关的数据可视化组件。由于这些任务之间没有重叠，每个 Claude 都能高效运行，无需等待其他会话的更改，也无需处理烦人的合并冲突：

1. Create worktrees: git worktree add ../project-feature-a feature-a

2. Launch Claude in each worktree: cd ../project-feature-a && claude

1. 创建 Git 工作区（worktree)：git worktree add ../project-feature-a feature-a

2. 在该工作区中启动 Claude：cd ../project-feature-a && claude

3. Create additional worktrees as needed (repeat steps 1-2 in new terminal tabs)

Some tips:

3. 如果有需要，可以创建更多的工作树（在新终端的选项卡中重复执行步骤 1 和 2）

一些小贴士：

* Use consistent naming conventions

* Maintain one terminal tab per worktree

*  使用一致的命名约定
*  每个工作树对应一个终端标签页

* If you're using iTerm2 on Mac, set up notifications for when Claude needs attention

* Use separate IDE windows for different worktrees

*  如果您在 Mac 上使用 iTerm2，请设置当 Claude 需要响应时发出的通知。
*  为不同的工作树（worktrees）使用独立的 IDE 窗口。

* Clean up when finished: git worktree remove ../project-feature-a

### d. Use headless mode with a custom harness

* 结束后清理：git worktree remove ../project-feature-a

### d. 使用无头模式（headless mode）和定制化测试框架

claude -p (headless mode) integrates Claude Code programmatically into larger workflows while leveraging its built-in tools and system prompt. There are two primary patterns for using headless mode:

claude -p（headless mode）将 Claude Code 以编程方式整合到更复杂的工作流程中，同时充分利用其内置工具和系统提示。使用无头模式（headless mode）主要有两种模式：

1. Fanning out handles large migrations or analyses (e.g., analyzing sentiment in hundreds of logs or analyzing thousands of CSVs):

1. Have Claude write a script to generate a task list. For example, generate a list of 2k files that need to be migrated from framework A to framework B.

1. ** 扇出（Fanning out)** 这种策略常用于处理大规模的迁移或数据分析任务（例如，对数百个日志文件进行情感分析，或者分析数千个 CSV 文件）。

1. 可以让 Claude 编写一个脚本来生成任务清单。例如，让它生成一个包含两千个需要从框架 A 迁移到框架 B 的文件列表。

2. Loop through tasks, calling Claude programmatically for each and giving it a task and a set of tools it can use. For example: claude -p "migrate foo.py from React to Vue. When you are done, you MUST return the string OK if you succeeded, or FAIL if the task failed." --allowedTools Edit Bash(git commit:*)

2. 循环处理各项任务，针对每个任务以编程方式调用 Claude，并为其分配一项具体任务和一组可使用的工具。例如：调用 claude 时可以这样设置：`-p」将 foo.py 从 React 迁移到 Vue。任务完成后，如果成功，你必须返回字符串 OK；如果失败，则返回 FAIL。"--allowedTools Edit Bash（编辑 Bash）(git commit:*)`

3. Run the script several times and refine your prompt to get the desired outcome.

2. Pipelining integrates Claude into existing data/processing pipelines:

3. 多次运行脚本并优化（refine）你的提示词（prompt），以获得预期的结果。

2. 管道集成（Pipelining）将 Claude 融入现有的数据 / 处理管道：

1. Call claude -p "<your prompt>" --json | your_command, where your_command is the next step of your processing pipeline

2. That's it! JSON output (optional) can help provide structure for easier automated processing.

1. 调用 claude -p「<您的提示>」--json | 您的命令，其中您的命令是您处理流程的下一步。
2. 仅此而已！JSON（JavaScript Object Notation）输出（可选）可以帮助提供结构化数据，以便进行更便捷的自动化处理。

For both of these use cases, it can be helpful to use the --verbose flag for debugging the Claude invocation. We generally recommend turning verbose mode off in production for cleaner output.

在这两种应用场景中，使用 `--verbose` 标志（即冗长模式标志）来调试 Claude 调用可能会很有帮助。不过，我们通常建议在生产环境中关闭冗长模式，以便获得更简洁的输出。

What are your tips and best practices for working with Claude Code? Tag @AnthropicAI so we can see what you're building!

在使用 Claude Code 时，你有哪些技巧和最佳实践？请标记 @AnthropicAI ，以便我们能看到你正在构建什么！

### Acknowledgements

致谢

Written by Boris Cherny. This work draws upon best practices from across the broader Claude Code user community, whose creative approaches and workflows continue to inspire us. Special thanks also to Daisy Hollman, Ashwin Bhat, Cat Wu, Sid Bidasaria, Cal Rueb, Nodir Turakulov, Barry Zhang, Drew Hodun and many other Anthropic engineers whose valuable insights and practical experience with Claude Code helped shape these recommendations.

本文由 Boris Cherny 撰写。这项工作汲取了 Claude Code 广大用户社区的宝贵经验，他们的创新方法和工作流程持续为我们带来启发。在此，特别感谢 Daisy Hollman、Ashwin Bhat、Cat Wu、Sid Bidasaria、Cal Rueb、Nodir Turakulov、Barry Zhang、Drew Hodun 以及 Anthropic 的众多其他工程师，他们对 Claude Code 的深刻见解和丰富实践经验，为这些建议的形成贡献了重要力量。