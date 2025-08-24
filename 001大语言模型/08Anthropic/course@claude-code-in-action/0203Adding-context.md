## 0203Adding-context

[Adding context](https://anthropic.skilljar.com/claude-code-in-action/303241)



## 网页文稿

When working with Claude on coding projects, context management is crucial. Your project might have dozens or hundreds of files, but Claude only needs the right information to help you effectively. Too much irrelevant context actually decreases Claude's performance, so learning to guide it toward relevant files and documentation is essential.

在使用 Claude 协助编码项目时，上下文管理是关键所在。你的项目可能拥有几十甚至数百个文件，但 Claude 只需要恰当的信息，就能高效地帮助你。输入过多的无关上下文反而会降低 Claude 的性能，因此，学会引导它关注相关文件和文档至关重要。

The /init Command

When you first start Claude in a new project, run the /init command. This tells Claude to analyze your entire codebase and understand:

Claude 的 /init 命令在一个新项目中首次启动 Claude 时，你需要运行 /init 命令。这个命令会指示 Claude 分析你的整个代码库，以便它能理解：

The project's purpose and architecture

Important commands and critical files

项目目标与架构解析核心命令与关键文件一览

Coding patterns and structure

After analyzing your code, Claude creates a summary and writes it to a CLAUDE.md file. When Claude asks for permission to create this file, you can either hit Enter to approve each write operation, or press Shift+Tab to let Claude write files freely throughout your session.

代码模式与结构在分析你的代码后，Claude 会创建一份总结并将其写入一个 CLAUDE.md 文件。当 Claude 请求创建文件权限时，你可以按下 Enter 键批准每次写入，或者按下 Shift+Tab 键让 Claude 在整个会话中自由地写入文件。

The CLAUDE.md File

The CLAUDE.md file serves two main purposes:

CLAUDE.md 文件

CLAUDE.md 文件主要有两大用途：

Guides Claude through your codebase, pointing out important commands, architecture, and coding style

Allows you to give Claude specific or custom directions

* 帮助 Claude 熟悉您的代码库，并向它介绍重要的命令、架构设计和编码风格。
* 允许您向 Claude 提供具体或自定义的指令。

This file gets included in every request you make to Claude, so it's like having a persistent system prompt for your project.

CLAUDE.md File Locations

这个文件会包含在你向 Claude 发出的每个请求中，所以它就像是为你的项目提供了一个持久的系统提示。

CLAUDE.md 文件位置

Claude recognizes three different CLAUDE.md files in three common locations:

CLAUDE.md - Generated with /init, committed to source control, shared with other engineers

Claude 在三个常见位置识别出三种不同的 CLAUDE.md 文件：

CLAUDE.md - 使用 /init 生成，已提交到源代码控制，并与团队其他工程师共享

CLAUDE.local.md - Not shared with other engineers, contains personal instructions and customizations for Claude

~/.claude/CLAUDE.md - Used with all projects on your machine, contains instructions that you want Claude to follow on all projects

CLAUDE.local.md - 不会与其他工程师共享，其中包含你为 Claude 设置的个人指令和定制化内容。
~/.claude/CLAUDE.md - 应用于你机器上的所有项目，其中包含你希望 Claude 在所有项目中遵循的指令。

Adding Custom Instructions

You can customize how Claude behaves by adding instructions to your CLAUDE.md file. For example, if Claude is adding too many comments to code, you can address this by updating the file.

添加自定义指令你可以通过向你的 CLAUDE.md 文件添加指令来定制 Claude 的行为方式。例如，如果 Claude 在代码中添加了过多注释，你可以通过更新此文件来解决这个问题。

Use the # command to enter "memory mode" - this lets you edit your CLAUDE.md files intelligently. Just type something like:

\# Use comments sparingly. Only comment complex code.

使用 # 命令进入「记忆模式」，这样你就可以智能地编辑你的 CLAUDE.md 文件。只需输入类似以下内容：

# 尽量少用注释。只对复杂代码进行注释。

Claude will merge this instruction into your CLAUDE.md file automatically.

File Mentions with '@'

Claude 将把此指令自动整合到你的 CLAUDE.md 文件中。

文件将通过「@」符号进行提及。

When you need Claude to look at specific files, use the @ symbol followed by the file path. This automatically includes that file's contents in your request to Claude.

如果你需要让 Claude 查看特定的文件，只需使用「@」符号，并在后面跟着文件的路径。这样一来，该文件的内容就会自动包含在你向 Claude 发出的请求中。

For example, if you want to ask about your authentication system and you know the relevant files, you can type:

How does the auth system work? @auth

举个例子，如果你想询问你的认证系统，而且你知道相关文件，你可以这样输入：

How does the auth system work? @auth

Claude will show you a list of auth-related files to choose from, then include the selected file in your conversation.

Referencing Files in CLAUDE.md

Claude 会向你展示一个与身份验证（auth-related）相关的文件列表供你选择，然后将选定的文件纳入到你的对话中。详情请参考 CLAUDE.md 中关于文件引用的说明。

You can also mention files directly in your CLAUDE.md file using the same @ syntax. This is particularly useful for files that are relevant to many aspects of your project.

你也可以在 CLAUDE.md 文件中直接引用其他文件，方式是使用相同的 @ 语法。对于与你项目许多方面都相关的文件，这种做法尤其有用。

For example, if you have a database schema file that defines your data structure, you might add this to your CLAUDE.md:

The database schema is defined in the @prisma/schema.prisma file. Reference it anytime you need to understand the structure of data stored in the database.

例如，如果你有一个用于定义数据结构的数据库模式（database schema）文件，你可能会将以下内容添加到你的 CLAUDE.md 文件中：

数据库模式在 @prisma/schema.prisma 文件中定义。当你需要了解数据库中存储的数据结构时，可以随时参考该文件。

When you mention a file this way, its contents are automatically included in every request, so Claude can answer questions about your data structure immediately without having to search for and read the schema file each time.

当你以这种方式引用一个文件时，它的内容会自动包含在每个请求中。这样一来，Claude 就可以立即回答关于你的数据结构的问题，而无需每次都去搜索和读取模式文件。