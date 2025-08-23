## 20250523Mastering-Claude Code-in-30-minutes

Hello everyone! I'm Boris, a member of the technical staff here at Anthropic, and I created Claude Code. I'm here today to talk to you a little bit about some practical tips and tricks for using Claude Code. It's going to be very practical; I'm not going to go too much into the history or the theory or anything like this.

大家好！我是 Boris，Anthropic 的技术人员，也是 Claude Code 的创建者。今天我将和大家分享一些使用 Claude Code 的实用技巧。本次分享会非常注重实践，我不会过多地探讨其历史、理论或其他类似背景。

Before we start, can we get a quick show of hands? Who has used Claude Code before? Yeah, all right, that's what we like to see. For everyone that didn't raise your hands, I know you're not supposed to do this while people are talking, but if you can open your laptop and type this, it will help you install Claude Code so you can follow along for the rest of the talk. All you need is Node.js. If you have it, this should work. You don't have to follow along, but if you don't have it yet, this is your chance to install it so you can follow along.

在我们开始之前，大家能快速举一下手吗？谁以前用过 Claude Code？好的，这正是我们乐于见到的。对于那些没有举手的朋友，我知道在讲座进行时打开电脑可能不太礼貌，但如果你能打开笔记本电脑并输入指令，这将帮助你安装 Claude Code，以便你能跟着我们完成接下来的讲解。你只需要 Node.js。如果你已经安装了，这应该就能运行。你不必非得跟着操作，但如果你还没有安装，这是一个很好的机会，可以趁此安装，这样就能跟上我们的进度了。

### 01

So, what is Claude Code? Claude Code is a new kind of AI assistant. There have been different generations of AI assistants for coding. Most of them have been about completing, you know, like a line at a time, completing a few lines of code at a time. Claude Code is not for that; it's fully agentic. So, it's meant for building features, for writing entire functions, entire files, fixing entire bugs at the same time.

那么，什么是 Claude Code？Claude Code 是一种新型的 AI 助手。编码领域的 AI 助手已经发展了好几代。它们中的大多数都致力于代码补全，比如一次补全一行或几行代码。但 Claude Code 并非为此设计；它是一个完全的 AI 智能体（AI Agent）。因此，它旨在帮助用户构建功能、编写完整的函数、创建完整的文件，并同时修复整个代码 bug。

And what's kind of cool about Claude Code is it works with all of your tools, and you don't have to change your workflow, you don't have to swap everything to start using it. So, whatever IDE you use, if you use VS Code, or if you use Xcode, or if you use JetBrains IDEs, there are some people at Anthropic that you can't pry them from their cold, dead hands, but they use Claude Code because Claude Code works with every single IDE, every terminal out there. It will work locally, over remote SSH, over Tmux, whatever environment you're in, you can run it. It's general purpose.

Claude Code 的一个很酷的优点是，它能与你现有的所有工具无缝协作，你无需改变工作流程，也不必为了使用它而更换所有设备。所以，无论你使用哪种集成开发环境（IDE）—— 无论是 VS Code、Xcode，还是 JetBrains 的 IDE，Anthropic 的有些工程师对他们钟爱的 IDE 简直爱不释手，但他们依然在使用 Claude Code，因为 Claude Code 能兼容市面上所有的 IDE 和终端。它既可以在本地运行，也能通过远程 SSH 或 Tmux 运行，无论你身处何种开发环境，都能轻松使用。它是一款通用型工具。

And this is something where if you haven't used these kind of free-form coding assistants in the past, it can be kind of hard to figure out how to get started, because you open it up and you just see a prompt bar and you might wonder, like, what do I do with this? What do I type in? It's a power tool, so you can use it for a lot of things, but also because it can do so much, we don't try to guide you towards a particular workflow, because really, you should be able to use it however you want as an engineer.

如果你以前从没用过这种自由形式的编程助手（free-form coding assistants），可能会觉得有点难以上手。因为当你打开它时，会看到一个提示栏，你可能会想：「我该用它做什么？我应该输入什么？」它是一款强大的工具，你可以用它做很多事情。但也正因为它功能如此强大，我们不会试图将你引导向某个特定的工作流程，因为作为一名工程师，你应该能够随心所欲地使用它。

As you open up Claude Code for the first time, there are a few things that we recommend doing to get your environment set up. And these are pretty straightforward. So, run terminal setup; this will give you shift enter for new lines, so you don't have to do backslashes to enter new lines, it makes it a little bit nicer to use. Do slash theme to set light mode or dark mode or customized themes. You can do slash install GitHub app. So today, we announced a GitHub app where you can mention Cla on any GitHub issue or pull request. So, to install it, just run this command in your terminal.

当你第一次打开 Claude Code 时，我们建议你进行几项简单的设置，让你的开发环境准备就绪。首先，运行终端设置；这样你就可以通过 Shift + Enter 来换行，而不需要再输入反斜杠，这能让你的使用体验更流畅。其次，输入 `/theme` 来设置亮色模式、暗色模式或自定义主题。你还可以输入 `/install GitHub app`。今天我们发布了一款 GitHub 应用，你可以在任何 GitHub issue 或 pull request 中提及 Claude。要安装它，只需在你的终端中运行这条命令即可。

输入命令：/terminal-setup

You can customize the set of allowed tools that you can use so you're not prompted for it every time. This is pretty convenient. For stuff that I'm prompted about a bunch, I'll definitely customize it in this way so I don't have to accept it every time. And something that I actually do is, for a lot of my prompts, I won't hand-type them into Claude Code. If you're on Mac OS, you can go into your system settings under accessibility as dictation, and you can enable it. And so, something I do is, you just hit like that dictation key twice, and you can just speak your prompt. And it helps a lot to have specific prompts. So this is actually pretty awesome; you can just talk to Claude Code like you would another engineer, and you don't have to type a lot of code.

你可以自定义允许使用的工具集，这样就不用每次都收到提示了。这非常方便。对于我经常需要确认的工具，我肯定会用这种方式自定义它们，这样我就不必每次都接受。我实际会做的一件事是，对于我的很多提示词，我不会手动将它们输入到 Claude Code 中。如果你使用的是 Mac OS，你可以进入系统设置中的「辅助功能」，在「听写」功能下启用它。所以，我做的一件事是，你只需双击听写键，就可以说出你的提示词。拥有具体的提示词非常有帮助。所以这真是太棒了；你可以像与另一位工程师交谈一样与 Claude Code 对话，而且不必敲写大量代码。

### 02

04.11min

So, when you're starting out with Claude Code, it's so freeform and it can do everything, what do you start with? The thing I recommend above everything else is starting with codebase Q&A. So, just asking questions to your codebase. This is something that we teach new hires at Anthropic. So, on the first day in technical onboarding, you learn about Claude Code, you download it, you get it set up, and then you immediately start asking questions about the codebase. And in the past, when you were doing technical onboarding, it's something that taxes the team a lot. You have to ask other engineers on the team questions, you have to look around the code, and this takes a while. You have to figure out how to use the tools; this takes a long time. With Claude Code, you can just ask Claude Code, and it'll explore the codebase. It'll answer these kind of questions. And so, at Anthropic, onboarding used to take about two or three weeks for technical hires; it's now about two or three days.

那么，当你第一次接触 Claude Code 时，它如此灵活自由，几乎无所不能，你该从何入手呢？我最推荐的入门方式是「代码库问答」。简单来说，就是向你的代码库提问。这也是 Anthropic 新员工培训的重要一环。在技术入职的第一天，你会学习 Claude Code，下载并完成设置，然后立即就可以开始向代码库提问了。过去，技术入职的过程对团队来说是个不小的负担。新员工需要不断向团队里的其他工程师提问，自己摸索代码，这既耗时又费力，还需要花很长时间去熟悉各种工具。但有了 Claude Code，你只需要直接提问，它就会自动探索代码库，并给出这些问题的答案。因此，Anthropic 技术新员工的入职培训时间，已从过去的约两到三周，缩短到现在的两到三天。

What's also kind of cool about Q&A is we don't do any sort of indexing, so there's no remote database with your code, we don't upload it anywhere, your code stays local, we do not train generative models on the code, so it's there, you control it, there's no indices or anything like this. And what that means is also there's no setup, so you start Claude, you download it, you start it, there's no indexing, you don't have to wait, you can just use it right away.

关于 Q&A 功能，一个很棒的特性是我们不进行任何形式的索引。这意味着你的代码不会存储在任何远程数据库中，我们也不会将其上传到任何地方，它会始终保留在你的本地设备上。更重要的是，我们不会使用这些代码来训练生成式模型（Generative Models）。因此，你的代码完全由你掌控，没有任何索引或其他类似的处理。这意味着你无需进行任何设置：启动 Claude 后，你只需下载并运行它，无需等待索引过程，就可以立即开始使用。

This is a technical talk, so I'm gonna show some very specific prompts and very specific code samples that you can use and hopefully improve and up-level your Claude code experience. So some kind of questions that you can ask is, how is this particular piece of code used? Or how do I instantiate this thing? And Claude Code, it won't just do a text search and try to answer this. It'll often go a level deeper, and it'll try to find examples of how is this class instantiated, how is it used? And it'll give you a much deeper answer, so something that you would get out of a wiki or documentation, instead of just like Command F.

这是一场技术讲座，所以我将展示一些非常具体的提示（prompts）和代码示例，你可以使用它们来改进和提升你的 Claude code 体验。那么，你可以提出的一些问题包括：这段具体的代码是怎样使用的？或者我该如何实例化（instantiate）这个对象？Claude Code 不会仅仅进行文本搜索来回答这些问题。它通常会更深入一层，尝试找到这个类是如何被实例化以及如何被使用的具体例子。它会给你一个更深入的答案，就像你从维基百科（wiki）或官方文档中获得的信息那样，而不仅仅是简单的文本搜索（比如按 Command F 查找）。

Something that I do a lot also is ask it about git history. So for example, why does this function have 15 arguments and why are the arguments named this weird way? And this is something I bet in all of our code bases you have some function like this or some class like this. And Claude Code can look through git history and it'll look to figure out how did these arguments get introduced and who introduced them and what was the situation, what are the issues that those commits link to and it'll look through all this and summarize it and you don't have to tell it that in all these in all this detail you just ask it. So just say look through Git history and I don't know to do this. The reason it knows it by the way is not because we prompted it to, there's nothing in the system prompt about looking through a Git history. It knows it because the model is awesome. And if you tell it to use Git, it'll know how to use Git. So we're lucky to be building on such a good model.

我经常做的一件事就是向它询问 Git 历史记录。举个例子，为什么这个函数有 15 个参数？为什么这些参数的命名方式如此奇怪？我敢打赌，在我们所有的代码库中，你肯定也会遇到类似这样的函数或类。Claude Code 能够查看 Git 历史记录，它会查找这些参数是如何引入的、是谁引入的、当时是怎样的情况，以及这些提交（commit）链接到了哪些问题。它会查看所有这些信息并进行总结，而你不需要告诉它所有这些详细信息，你只需直接提问。所以，你只需说「查看 Git 历史记录」就可以了，我本人都不需要知道如何操作。顺便提一下，它之所以知道如何做，并不是因为我们在系统提示词中专门要求它去查看 Git 历史记录。它之所以知道，是因为这个模型本身非常出色。如果你告诉它使用 Git，它就会知道如何使用 Git。所以，我们非常幸运能够基于这样一个优秀的模型进行开发。

I often ask about GitHub issues, so it can use web fetch and it can fetch issues and look up context on issues too, and this is pretty awesome. And this is something that I do every single Monday in our weekly stand up is I ask what did I ship this week? And Claude Code looks to the log, it knows my username and it'll just give me a nice read out of everything I shipped. And I'll just copy and paste that into docs. So yeah, that's tip number one.

我经常询问 GitHub 上的问题，所以它能联网获取信息，抓取问题并查询相关信息，这非常棒。每周一我们开周会的时候，我都会问一个问题：这周我发布了什么？Claude Code 会查看日志，它知道我的用户名，然后会清晰地列出我发布的所有内容。我只需将其复制并粘贴到文档中。所以，是的，这是第一个小技巧。

For people that have not used Claude Code before, if you're just showing it to someone for the first time, onboarding your team, the thing we definitely recommend is start with code base Q&A. Don't start by using fancy tools, don't start by editing code, just start by asking questions about the code base, and that'll teach people how to prompt. And it'll start teaching them this boundary of like, what can Claude Code do, what is it capable of, versus what do you need to hold its hand with a little bit more? What can be one-shotted, what can be two-shotted, three-shotted, what do you need to use interactive mode for in a REPL? Once you're pretty comfortable with Q&A, you can dive into editing code.

对于那些之前没有使用过 Claude Code 的人来说，如果你是第一次向他人展示它，或者在为你的团队进行新员工培训时，我们强烈建议从代码库问答开始。不要一开始就使用花哨的工具，也不要急于编辑代码，只需从询问有关代码库的问题入手，这会帮助人们学习如何编写提示词（prompt）。通过这种方式，他们将逐渐了解 Claude Code 的能力边界：它能做些什么，有哪些功能，以及在哪些方面需要你提供更多的引导和协助。哪些任务可以实现零样本（Zero-shot）或少样本（Few-shot）完成，哪些任务需要在 REPL 中使用交互模式？一旦你对问答环节非常熟悉，就可以深入到代码编辑中去了。

### 03

This is the next thing. And the cool thing about any sort of agentic, you know, like using an LM in an agentic way is you give it tools and it's just like magical. It figures out how to use the tools. And with Claude Code, we give it a pretty small set of tools. It's not a lot. And so it has a tool to edit files. It has a tool to run bash commands. It has a tool to search files. And it'll string these together to explore the code, brainstorm, and then finally make edits. And you don't have to prompt it specifically to use this tool and this tool and this tool, you just say, you know, do this thing and it'll figure out how to do it. It'll string it together in the right way that makes sense for Claude Code.

接下来要说的，是关于将大语言模型（LLM）以智能体（AI Agent）的方式运用，其令人惊叹之处在于：你给它一些工具，它就能像魔法一般，自行找出如何使用这些工具。对于 Claude Code 来说，我们提供了一套相当精简的工具集，数量并不多。它有一个用于编辑文件的工具，一个用于运行 Bash 命令的工具，还有一个用于搜索文件的工具。Claude Code 会将这些工具巧妙地组合起来，用于探索代码、进行思考规划，并最终完成代码编辑。你无需明确指示它「使用这个工具，再使用那个工具」，你只需告诉它「完成这项任务」，它便能自行规划，以对 Claude Code 而言最合理的方式将这些工具串联起来，完成任务。

There's a lot of ways to use this. Something I like to do sometimes is before having Cloud jump in to write code, I'll ask it to brainstorm a little bit or make a plan. This is something we highly recommend, and something I see sometimes is people, you know, they take Claude code and they ask it, hey, implement this enormous like 3000 line feature, and sometimes it gets this right on the first shot, but sometimes what happens is the thing that it builds is not at all the thing that you wanted. And the easiest way to get the result you want is ask it to think first. So brainstorm ideas, make a plan, run it by me, ask for approval before you write code. And you don't have to use plan mode, you don't have to use any special tools to do this, all you have to do is ask Claude, and it'll know to do this. So just say, before you write code, make a plan. That's it.

Claude 有许多应用场景。我有时喜欢在让 Claude 着手编写代码之前，先让它进行一些头脑风暴或制定详细计划。我们强烈建议这样做，因为有时我们会看到用户直接让 Claude 实现一个庞大，例如包含 3000 行代码的功能。虽然有时它能一次性完美完成，但有时生成的结果却与期望相去甚远。要获得您想要的结果，最简单的方法就是让 Claude 先进行思考。具体来说，就是让它先集思广益，制定一个计划，然后提交给您审阅，在您批准后再开始编写代码。您无需启用特定的「计划模式」，也不需要任何特殊工具，只需直接向 Claude 发出指令，它就能理解并执行。因此，您只需简单地说：「在编写代码之前，请先制定一个计划。」就这么简单。

This is also, I want to think for this commit push PR, this is a really common incantation that I use. There's nothing special about it, but Claude is kind of smart enough to interpret this. So it'll make a commit, it'll push it to the branch, make a branch, and then make a pull request from you on GitHub. You don't have to explain anything, it'll look through the code, it'll look through the history, it'll look through the Git log by itself to figure out the commit format and all the stuff, and it'll make the commit and push it the right way. Again, we're not system prompting it to do this, it just knows how to do this, the model is good.

对于「提交（commit）、推送（push）、拉取请求（pull request，PR）」这一套操作流程，我个人认为它是一组非常常见的操作指令。这其中并没有什么特别之处，但 Claude 却足够智能，能够理解我的意图。因此，它会完成提交，将代码推送到指定分支，创建一个新分支，然后通过 GitHub 为你发起一个拉取请求。你无需进行任何额外的解释，Claude 会自行查看代码、历史记录以及 Git 日志，从而理解提交格式和所有相关细节，并以正确的方式完成提交和推送。再次强调，我们并没有通过系统提示（system prompting）来指导它这样做，它只是本身就「知道」如何完成这些任务，这个模型表现得非常出色。

As you get a little bit more advanced, you're gonna want to start to plug in your team's tools, and this is where Claude Code starts to really shine. And there's generally two kinds of tools. So one is batch tools. And an example of this, I just made up this like Burley CLI, this isn't a real thing. But you can say, "Use the CLI to do something." And you can tell Claude Code about this. And you can tell it to use, for example, like `--help` to figure out how to use it. And this is efficient. If you find yourself using it a lot, you can also dump this into your Claude.md, which we'll talk about in a bit, so Claude can remember this across sessions.

随着你掌握得更深入，你会希望开始集成团队的工具，而这正是 Claude Code 真正大放异彩的地方。工具通常分为两种：一种是批处理工具。举个例子，我虚构了一个名为 Burley CLI 的命令行界面（CLI），它并不是真实存在的。你可以说「使用这个 CLI 来做某事」，然后你可以把这个信息告诉 Claude Code。你还可以告诉它使用，例如 `--help` 命令来了解如何使用它。这种方式非常高效。如果你发现自己经常使用某个工具，你也可以将其导入到你的 Claude.md 中（我们稍后会提到 Claude.md），这样 Claude 就可以在不同的会话中记住它。

But this is a common pattern we follow at Anthropic, and we see external customers use too. And same thing with MCP. Claude Code can use bash tools, it can use MCP tools, so just tell it about the tools. And you can add the MCP tool, and you can tell it how to use it, and it'll just start using it. And this is extremely powerful because when you start to use code on a new code base, you can just give it all of your tools, all the tools your team already uses for this code base, and Claude Code can use it on your behalf.

不过，这在 Anthropic 是我们经常遵循的一种模式，我们发现外部客户也在使用。对于 MCP 也是如此。Claude Code 可以使用 bash 工具，也能使用 MCP 工具，你只需要告诉它这些工具就行。你可以添加 MCP 工具，然后告诉它如何使用，它就会开始运用这些工具了。这一点非常强大，因为当你开始在一个新的代码库上进行编程时，你只需将团队为这个代码库所使用的所有工具都提供给 Claude Code，它就能代你使用这些工具了。

There's a few common workflows, and this is the one that I talked about already. So kind of do a little bit of exploration, do a little bit of planning, and ask me for confirmation before you start to write code. These other two on the right are extremely powerful. When Claude has some way to check its work, so for example, by writing unit tests or screenshotting in Puppeteer or screenshotting the iOS simulator, then it can iterate. And this is incredible because if you give it, for example, a mock and you say, "Build this web UI," it'll get it pretty good. But if you let it iterate two or three times, often it gets it almost perfect. So the trick is give it some sort of tool that it can use for feedback to check its work, and then based on that, it will iterate by itself and you're gonna get a much better result. So whatever your domain is, if it's unit test or integration test or screenshots for apps or web or anything, just give it a way to see its result and it'll iterate and get better.

有几种常见的工作流程，其中一种我之前已经提过。那就是先进行探索和规划，然后在我（Claude）开始编写代码之前，请求我的确认。右侧的另外两种工作流程则极其强大。当 Claude 能够以某种方式检查自身工作时，例如通过编写单元测试，或使用 Puppeteer 截屏，或截取 iOS 模拟器的屏幕，它就能进行迭代改进。这一点非常了不起，因为如果你给它一个模型图，并要求它「构建这个网页用户界面」，它通常能做得相当不错。但如果你让它迭代两到三次，它往往能做得近乎完美。所以，关键在于给它一个工具，让它能够获取反馈并检查自己的工作。在此基础上，它就能自行迭代，从而为你带来更好的结果。因此，无论你的领域是什么，无论是单元测试、集成测试，还是应用程序或网页的截屏，或者其他任何形式，只要给它一个查看结果的方式，它就会不断迭代并持续改进。

### 04

So these are the next steps. Teach Claude how to use your tools and figure out the right workflow. If you want Claude to jump into code, if you want it to brainstorm a little bit, make a plan, if you want it to iterate, kind of have some sense of that so you know how to prompt Claude to do what you want.

接下来的工作安排如下：我们需要教会 Claude 如何使用你的工具，并确定合适的工作流程。如果你希望 Claude 能够直接处理代码，或者让它先进行一番头脑风暴，制定一个周密的计划，甚至进行多次迭代，那么你就需要对这些操作模式有一个大致的了解。这样一来，你就知道如何通过「提示（prompt）」来引导 Claude 完成你想要的任务。

As you go deeper, beyond tools, you want to start to give Claude more context. And the more context, the smarter the decisions will be, because as an engineer working in a codebase, you have a ton of context in your head about your systems and all the history and everything else. So there's different ways to give this to Claude. And as you give Claude more context, it'll do better. There's different ways to do this. The simplest one is what we call Claude.md. And Claude.md is the special file name. The simplest place to put it is in the project root. So the same directory you start Claude in, put a Claude.md in there. And that'll get automatically read into context at the start of every session. And essentially, the first user turn will include the Claude.md.

当你深入了解，超越了工具层面时，你会希望开始为 Claude 提供更多的上下文信息。上下文信息越多，Claude 做出的决策就会越智能。这就像一位在代码库中工作的工程师，他们的大脑里储存了大量关于系统、历史以及其他所有相关信息。有多种方式可以将这些信息提供给 Claude，当你给 Claude 的上下文越多，它的表现就会越好。其中最简单的一种方式，我们称之为 Claude.md。Claude.md 是一个特殊的文件名，最简单的放置位置是项目根目录，也就是你启动 Claude 的那个目录。把 Claude.md 文件放在那里，它就会在每个会话开始时自动加载到上下文中。本质上，用户第一次与 Claude 交互时，就会包含这个 Claude.md 文件的内容。

You can also have a local Claude.md. And this one you don't usually check into source control. So Claude.md, you should check into source control, share with your team so that you can write it once and share it with your team. This one you don't check in, it's just for you. The kinds of things you put in Claude.md, it's like common bash commands, common MCP tools, architectural decisions, important files, anything that you would kind of typically need to know in order to work in this codebase. Try to keep it pretty short, because if it gets too long it's just going to use up a bunch of context, and it's usually not that useful. So just try to keep it as short as you can. And for example, in our codebase we have common bash commands, we have a style guide, we have a few core files, kind of things like that. All the other Claude.mds you can put them in other nested child directories, and Claude will pull them in on-demand.

你也可以拥有一个本地的 Claude.md 文档。这种本地的 Claude.md 通常你不会将其提交到版本控制系统。而前面提到的那种 Claude.md 文档，你应该将其提交到版本控制系统，并与你的团队共享，这样你只需编写一次，团队成员都能使用。至于这种本地的 Claude.md 文档，你无需提交，它只为你个人服务。

你可以在本地 Claude.md 中记录的内容包括：常用的 Bash 命令、常见的 MCP 工具、重要的架构决策、关键文件等，总之是任何你在当前代码库中工作时需要了解的常用信息。请尽量保持其内容简短，因为如果内容过长，不仅会占用大量的处理上下文资源，而且通常效率不高。因此，请尽量使其篇幅最短。例如，在我们的代码库中，本地 Claude.md 文档可能包含常用的 Bash 命令、代码风格指南以及一些核心文件等。所有其他类型的 Claude.md 文档，你可以将它们放置在其他嵌套的子目录中，Claude 会在需要时按需加载这些文档。

So these are the Claude.md  that will get pulled in automatically, but then also you can put in Claude.mds in nested directories and those will get pulled in automatically when Cloud works in those directories. And of course, if you're a company, maybe you want an MD that's shared across all the different codebases, and you want to manage it on behalf of your users, you can put it in your enterprise root, and that'll get pulled in automatically. There's a ton of ways to pull in context. I actually had a lot of trouble putting this slide together just to communicate the breadth of ways you can do this.

因此，这些 Claude.md 会自动被加载进来。不过，你也可以将 Claude.md 放入多层嵌套的目录中，当 Claude 在这些目录中运行时，它们也会被自动加载。当然，如果你是一家公司，可能希望有一个在所有不同代码库中共享的 MD（例如 Markdown 文件），并且想代表你的用户统一管理它，那么你可以把它放在你的企业根目录中，这样它也会被自动加载。总之，有多种多样的方式可以引入这些上下文信息。我其实在制作这张幻灯片时费了不少劲，就是为了向大家展示实现这些功能的广泛途径。

But QuadMD is pulled in automatically. You can also use slash commands. So this is cloud slash commands, and this can be in your home directory, or it can be checked into your project. And this is for slash commands. And over here, we have a few examples of the slash commands that we have in Claude Code itself. For example, if you're in the Claude Code repo and you see issues getting labeled, that's actually this workflow running here. It's labeled GitHub issues. And we have a GitHub action running, the same one we talked about this morning, where Claude Code will run this command and it's just a slash command. It'll run and it'll label the issues so humans don't have to. It just saves us a bunch of time.

QuadMD 会自动引入。你也可以使用斜杠命令。这些云斜杠命令可以存放在你的主目录中，或者提交到你的项目里。这些命令专为斜杠命令设计。这里有一些 Claude Code 自带的斜杠命令示例。比如，如果你在 Claude Code 仓库中，发现问题被自动打上了标签，那实际上就是这个工作流在运行。它负责标记 GitHub 问题。我们有一个 GitHub action 在运行，就是我们今天早上提到的那个，Claude Code 会执行这个斜杠命令。它会自动运行并标记问题，从而省去人工标记的麻烦，为我们节省了大量时间。

And of course, you can add mention files to pull them into context. And like I said before, QuadMDs in a nested directory get pulled in when Quad works in that directory. So give Quad more context, and it's definitely worth taking the time to tune context. You can run it through a prompt improver. Consider who the context is for. If you want to pull it in every time, if you want to pull it in on demand, if you want to share it with a team, if it's a personal preference, definitely take the time to tune it. This will improve performance dramatically if you do it right.

当然，你可以添加引用文件将它们引入上下文。正如我之前所说，当 Quad 在某个目录中运行时，该目录下的所有 QuadMD 文件都会被自动引入。因此，为 Quad 提供更丰富的上下文信息是很有价值的，并且花时间优化上下文绝对是值得的。你可以通过提示改进器来优化它。请考虑这些上下文是为谁准备的：你希望每次都引入它吗？还是按需引入？你希望与团队共享它，或者这只是个人偏好？无论哪种情况，都值得花时间去调整上下文。如果调整得当，这将极大地提高性能。

As you get more advanced, you're going to want to think about this a little bit more, this kind of hierarchy of different ways to pull in everything. So like not just Claude.md, but also config and kind of everything about Cloud you can pull in in this hierarchical way. So projects are specific to your Git repo, and this you can check in or you can make it just for you. You can also have global configs that are across all your projects, or you can have enterprise policies. And this is essentially a global config that you roll out for all of your employees, everyone on your team automatically.

随着你变得更加进阶，你会希望对如何导入所有这些信息有更深入的思考，尤其是这种不同导入方式的层级结构。所以，不仅仅是 Claude.md，还有配置（config）以及所有与 Cloud 相关的内容，你都可以通过这种层级化的方式来导入。举例来说，项目是你的 Git 仓库特有的，你可以将它提交到仓库，或者只为自己创建。你也可以设置全局配置，这些配置会应用于你所有的项目；或者你还可以制定企业策略（enterprise policies），这本质上是一种全局配置，会自动部署给你的所有员工和团队成员。

And this slide is like pretty information-dense, but the point is this applies to a lot of stuff. So you can do this for slash commands, you can do it for permissions. So for example, if you have a bash command that you would run for all your employees, like all your employees use this test command, for example, you can actually just check it into this enterprise policies file, and then any employee, when they run this command, it will be auto-approved, which is pretty convenient. And you can also use this to block commands. So for example, let's say there's a URL that should never be fetched, just add it to this config, and that'll make it so an employee cannot override it, and that URL can never be fetched. So pretty convenient, both to unblock people and also just to keep your codebase safe. And then same thing for MCP servers. Have an MCP JSON file, check it into the codebase, that way any time someone runs Claude Code in your codebase, they'll be prompted to install the MCP servers and share it with the team.

这个幻灯片信息量很大，但关键是它适用于很多场景。你可以将其用于斜杠命令（slash commands），也可以用于权限管理。例如，如果你有一个希望所有员工都运行的 Bash 命令（比如所有员工都使用这个 `test` 命令），你可以将其提交到这个企业策略文件（enterprise policies file）中。这样，任何员工在运行该命令时，都会被自动批准，这非常方便。

你也可以用它来阻止命令。例如，假设有一个永远不应该被访问（fetched）的 URL，只需将其添加到此配置中，员工就无法覆盖此设置，从而确保该 URL 永远不会被访问。这非常方便，既可以解除对员工的限制，也能确保你的代码库安全。

对于 MCP 服务器（MCP servers）也是同样的道理。你可以将一个 MCP JSON 文件提交到代码库中，这样任何人在你的代码库中运行 `Claude Code` 时，都会收到安装 MCP 服务器并与团队共享的提示。

If you're not sure which of these to use, this is like kind of an insane matrix because we support a lot of stuff and engineer workflows are very flexible and every company is different, so we kind of want to support everything. So if you're not sure how to get started, I would recommend start with shared project context. You write this once and then you share it with everyone on the team and you get this kind of network effect where someone does a little bit of work and everyone on the team benefits. There's a lot of tools built into Quad to manage this. So as an example, if you run slash memory, you can see all the different memory files that are getting pulled in. So maybe I have an enterprise policy, I have my user memory, I have project quad MD, and then maybe there's a nested quad MD that's only pulled in for certain directories. And then similarly when you do slash memory, you can edit particular memory files. When you type pound sign to remember something, you can pick which memory you want it to go to.

如果你不确定该如何选择这些功能，那么 Quad 的功能矩阵可能会让你眼花缭乱。因为我们支持很多不同的功能，工程师的工作流又非常灵活，而且每个公司的情况都不同，所以我们希望能够满足各种需求。如果你不确定该如何开始，我建议你从「共享项目上下文」入手。你只需编写一次，然后团队中的每个人都可以共享它，这样就能形成一种「网络效应」：一个人做了一点工作，团队中的所有人都能从中受益。Quad 内置了许多工具来管理这项功能。

举例来说，如果你运行 `/memory` 命令，你可以看到所有被加载的内存文件。比如，我可能有企业策略文件、我的用户内存文件、项目 `quad MD` 文件，以及一个嵌套的 `quad MD` 文件（它只在特定目录下被引入）。同样，当你运行 `/memory` 命令时，你可以编辑特定的内存文件。当你输入 `#` 符号来记录信息时，你可以选择将它保存到哪个内存文件中。

So yeah, that's the next step. Take the time to configure QuadMD, MCP servers, all the stuff that your team uses, so that you can use it once, configure it once, and then share it with everyone. An example of this is in our apps repo for Anthropic. This is like the repo that we have all of our web and apps code in. There's a Puppeteer MCP server, and we share this with the team.

好的，下一步就是花时间配置 QuadMD、MCP 服务器，以及团队所需的所有工具。这样一来，你只需配置一次，就能在团队内共享使用。举个例子，Anthropic 的应用仓库中就包含了我们所有的网络和应用程序代码。其中有一个 Puppeteer MCP 服务器，我们就是以这种方式与团队共享的。

And there's an MCP JSON checked in, so any engineer working in that repo can use Puppeteer in order to pilot end-to-end tests and to screenshot automatically and iterate so that every engineer doesn't have to install it themselves.

而且，由于有一个 MCP JSON 文件已提交，任何在该代码库中工作的工程师都可以利用 Puppeteer 来执行端到端测试，并自动进行截图和迭代，从而省去了每位工程师自行安装 Puppeteer 的麻烦。

This is a talk about pro tips, so I just want to take a quick interlude to talk about some common key bindings that people may not know. It's very hard to build for terminal. It's also very fun. It feels like rediscovering this new design language. But something about terminal is it's extremely minimal, and so sometimes it's hard to discover these key bindings.

<step3_refined_translation>
既然这是一场关于专业技巧的演讲，我想先插播一小段，聊聊一些大家可能不熟悉的常用按键绑定。为终端开发（build for terminal）虽然非常困难，但也乐趣无穷，仿佛在重新探索一种全新的设计语言。然而，终端的特点是它极其简约，因此有时会让人难以发现这些隐藏的按键绑定。

Here's just a quick reference sheet. So anytime you can hit shift tab to accept edits, and this switches you into auto accept edits mode. So bash commands still need approval, but edits are auto accepted. And you can always ask Claude to undo them later. For example, I'll do this if I know Claude's on the right track, or if it's writing unit tests and iterating on tests, I'll usually just switch into auto accept mode so I don't have to OK every single edit.

这里是一个快速参考指南。因此，你可以随时按下 Shift+Tab 键来接受编辑，这会将你切换到自动接受编辑模式。在这种模式下，Bash 命令仍然需要批准，但其他编辑都会自动接受。你也可以随时让 Claude 撤销这些编辑。例如，当我确信 Claude 的思路正确，或者它正在编写和迭代单元测试时，我通常会切换到自动接受模式，这样就无需逐一确认每次编辑了。

Anytime you want Claude to remember something, so for example, if it's not using a tool correctly, and you want it to use it correctly from then on, just type the pound sign, and then tell it what to remember, and it'll remember it, it'll incorporate it into Claude.md automatically.

如果你希望 Claude 记住某些事情，例如，当它没有正确使用某个工具时，你希望它以后能正确使用，只需输入井号（#）符号，然后告诉它要记住什么。Claude 就会记住你的指示，并将其自动整合到 Claude.md 中。

If you ever want to drop down to bash mode, so just run a bash command, you can hit the exclamation mark and type in your command. That will run locally, but that also goes into the context window, so Claude will see it on the next turn. And this is pretty good for long-running commands if you know exactly what you want to do or any command that you want to get into context, and Claude will see the command and the output. You can add mention thousand folders.

如果你想进入 bash 模式，直接运行 bash 命令，可以按下感叹号并输入你的命令。这个命令会在本地运行，但它的内容也会被添加到上下文窗口中，这样 Claude 在下一次交互时就能看到它。如果你确切知道自己想执行什么操作，或者任何你希望 Claude 看到其命令和输出的指令，这种方法对于长时间运行的命令来说都非常有用。你可以通过这种方式处理成千上万个文件夹。

Anytime you can hit escape to stop what Claude is doing, no matter what Claude is doing, you can always safely hit escape. It's not going to corrupt the session, it's not going to mess anything up. So maybe Claude is doing a file edit, I'll hit escape, I'll tell it what to do differently, or maybe it suggested a 20 line edit and I'm like, actually 19 of these lines look perfect, but one line you should change. I'll hit escape, I'll tell it that, and then I'll tell it to redo that.

无论 Claude 正在做什么，你都可以随时安全地按 Esc 键来停止它的工作。这不会损坏会话，也不会造成任何问题。举个例子，也许 Claude 正在编辑一个文件，我按下 Esc 键后，可以告诉它如何改进；或者它可能提出了一个 20 行的修改建议，而我发现其中 19 行都很完美，只有一行需要调整。这时，我就会按下 Esc 键，告诉它具体需要修改的地方，然后让它重新执行。

You can hit escape twice to jump back in history, and then after you're done with the session, you can start Claude with a resume to resume that session if you want, or dash dash continue. And then anytime if you want to see more output, hit control R, and that'll show you the entire output, the same thing that Claude sees in its context window.

你可以按两次 Escape 键来回溯历史记录；会话结束后，如果你想恢复之前的会话，可以使用 `resume` 或 `--continue` 命令来启动 Claude。此外，任何时候如果你想查看更多输出，可以按 Control + R 键，这会显示完整的输出内容，与 Claude 在其上下文窗口（context window）中看到的内容相同。

The next thing I want to talk about is the Claude code SDK. So we talked about this at the top. Right after this, Sid is doing a session, I think just across the hallway, and he's going to go super deep on the SDK. If you hadn't played around with this, if you use the dash P flag in Claude, this is what the SDK is. And we've been planning a bunch of features over the last few weeks to make it even better.

接下来我想谈谈 Claude 代码软件开发工具包（SDK）。我们在一开始就提到了它。紧接着，Sid 将在（我想是）走廊尽头的房间进行一个专题讨论，他会深入讲解这个 SDK。如果你还没有尝试过，当你使用 Claude 中的 `-P` 标志时，你就是在体验这个 SDK。在过去几周里，我们一直在规划一系列新功能，力求让它变得更好用。

So yeah, you can build on top of this. You can do cool stuff. This is exactly the thing that Claude code uses. It's exactly the same SDK. And so for example, something you can do is Cla-p, so this is the CLI SDK. You can pass a prompt, you can pass some allowed tools, which could include specific bash commands, and you can tell it which format you want. So you might want JSON or you might want streaming JSON if you wanna process this somehow. So this is awesome for building on. We use this in CI all the time, we use this for incident response. We use this in all sorts of pipelines. So really convenient. Just think of it as like a Unix utility. You give it a prompt, it gives you JSON. You can use this in any way. You can pipe into it, you can pipe out of it.

好的，你可以基于此进行开发，实现一些很棒的功能。这正是 Claude 代码所使用的，与 Claude 自身使用的 SDK（软件开发工具包）完全相同。举个例子，你可以使用 Cla-p（这是一个命令行界面 SDK），向它传递一个提示（prompt）和一些允许的工具（其中可能包括特定的 bash 命令），然后告诉它你希望输出的格式。你可以选择 JSON 格式，或者如果你需要实时处理数据，也可以选择流式 JSON 格式。

这对于开发来说非常有用。我们在持续集成（CI）中经常使用它，也用它来处理事件响应，以及在各种自动化流程（pipeline）中都会用到。所以它真的非常方便。你可以把它想象成一个 Unix 工具，你给它一个提示，它就会返回 JSON 数据。你可以以任何方式使用它，无论是作为输入，还是将数据输出。

The piping is also pretty cool. So you can use like, for example, git status and pipe this in and use JQ to select the result. The combinations are endless. And it's sort of this new idea. It's like a super intelligent Unix utility. And I think we barely scratched the surface of how to use this. We're just figuring this out. You can read from a GCP bucket, read a giant log and pipe it in and tell Claude to figure out what's interesting about this log. You can fetch data from the Sentry CLI. You can also pipe it in and have Claude do something with it.

这种「管道」功能也非常棒。例如，你可以运行 `git status` 命令，然后将结果通过管道输入，再用 JQ 来筛选输出。这种组合方式几乎是无限的。这就像一个全新的概念，你可以把它想象成一个「超级智能」的 Unix 实用工具。我认为我们才刚刚开始探索它的用法，很多功能我们还在摸索中。你可以从 GCP（Google Cloud Platform）存储桶中读取数据，比如读取一个巨大的日志文件，然后通过管道将其输入给 Claude，让它找出日志中的有趣信息。你也可以从 Sentry CLI 中获取数据，同样通过管道输入给 Claude，让它对数据进行处理。

The final thing, and this is probably the most advanced use case as we see, I'm sort of a Claude normie, so I'll have usually one Claude running at a time, and maybe I'll have a few terminal tabs for a few different repos running at a time. When I look at power users in and out of Anthropic, almost always they're going to have SSH sessions, they'll have Tmux tunnels into their Claude sessions. They're going to have a bunch of checkouts of the same repo so that they can run a bunch of Claude's in parallel in that repo, or they're using Git work trees to have some kind of isolation as they do this.

最后一点，这可能是我们所见过的最进阶的用法了。我本人是比较「普通」的 Claude 用户，通常只会同时运行一个 Claude 会话，并且可能只开几个终端标签页来处理不同的代码仓库。但当我观察 Anthropic 内外的那些高级用户时，他们几乎总是会利用 SSH 会话，通过 Tmux 隧道连接到他们的 Claude 会话。他们会在同一个代码仓库中检出（checkout）多个副本，以便在这些副本上并行运行多个 Claude 实例，或者他们会使用 Git work trees 来确保操作时的隔离性。
</step3_ref_translation>

And we're actively working on making this easier to use, but for now, like, these are some ideas for how to do more work in parallel with quad. You can run as many sessions as you want, and there's a lot that you can get done in parallel. So yeah, that's it. I wanted to also leave some time for Q and A. So I think this is the last slide that I have. And yeah, if folks have questions, there's mics on both sides. And yeah, we'd love to answer any questions.

我们正在积极努力使其更易于使用，但目前，这些是关于如何利用 quad 并行处理更多任务的一些思路。您可以运行任意数量的会话，并且可以并行完成大量工作。好了，我的分享就到这里。我还想留出一些时间进行问答环节。这应该是我准备的最后一张幻灯片了。如果大家有问题，两边都有麦克风，我们很乐意为大家解答。

I did, hey Boris, thanks for building Claude Code. And I was wondering what was the hardest implementation, hardest part of the implementation for you of building it? I think there's a lot of tricky parts. I think one part that is especially tricky is the things that we do to make bash commands safe. Bash is inherently pretty dangerous and it can change system state in unexpected ways. But at the same time, if you have to manually approve every single bash command, it's super annoying as an engineer and you can't really be productive because you're just constantly approving every command. And just kind of navigating how to do this safely in a way that scales across the different kinds of code bases people have, because not everyone runs their code in a Docker container, was pretty tricky. And essentially the thing we landed on is there's some commands that are read-only, there's some static analysis that we do in order to figure out which commands can be combined in safe ways, and then we have this pretty complex tiered permission system, so that you can allow list and block list commands at different levels.

<step3_refined_translation>
是的，Boris，感谢你构建了 Claude Code。我一直在想，对你来说，在构建 Claude Code 的过程中，最困难的实现部分是什么呢？我觉得有很多难题。其中一个特别棘手的地方在于，我们为了确保 Bash 命令的安全性所做的努力。Bash 本身就相当危险，它可能会以意想不到的方式改变系统状态。但与此同时，如果工程师每次都要手动批准 Bash 命令，那会非常令人恼火，效率也会大打折扣，因为你不得不不停地批准命令。如何安全地处理这些命令，并使其能够适应各种不同的代码库 —— 毕竟并非所有人都将代码运行在 Docker 容器中 —— 这确实是个难题。我们最终的解决方案是：有些命令被设定为只读；我们还进行了一些静态分析，以确定哪些命令可以安全地组合使用；此外，我们设计了一个相当复杂的分层权限系统，允许你在不同级别上设置命令的「白名单」（允许列表）和「黑名单」（阻止列表）。

Hi Boris, You mentioned giving an image to Claude Code, which made me wonder if there's some sort of multimodal functionality that I'm not aware of. Are you just pointing it at an image on the file system or something? Yeah, so Claude Code is fully multimodal. It has been from the start. It's in a terminal, so it's a little hard to discover. But yeah, you can take an image and just drag and drop it in, that'll work. You can give it a file path, that'll work. You can copy and paste the image in, and that works too. So I'll use this pretty often for if I have like a mock of something, I'll just drag and drop in the mock, I'll tell it to implement it, I'll give it up a tier server so it can iterate against it. And yeah, it's just fully automated.

Hi Boris，你提到把图片给 Claude Code 处理，这让我好奇它是不是有什么我不知道的多模态功能。你只是让它指向文件系统上的图片，还是有其他方式？是的，Claude Code 从一开始就完全支持多模态功能。因为它是在终端中运行的，所以可能不太容易被发现。但没错，你可以直接拖放图片进去，这样就能识别；你也可以给它一个文件路径，同样能识别；甚至直接复制粘贴图片，它也能处理。所以我经常这样用：如果我有一个界面的原型图（mock），我就会直接拖放进去，让 Claude Code 实现它，然后我会给它配置一个后端服务器，这样它就可以针对原型进行反复测试和改进。没错，整个过程都是全自动的。

Hey, why did you build a CLI tool instead of an IDE? Yeah, it's a good question. I think there's probably two reasons. One is we started this at Anthropic. And at Anthropic, people use a broad range of IDEs. And some people use VS Code, other people use Zed, or Xcode, or Vim, or Emacs. And it was just hard to build something that works for everyone. And so terminal is just the common denominator. The second thing is Adanthropic, we see up close how fast the model is getting better. And so I think there's a good chance that by the end of the year, people aren't using IDEs anymore. And so we want to get ready for this future, and we want to avoid over-investing in UI and other layers on top, given that the way the models are progressing, it just may not be useful work pretty soon.

您可能会问，为什么我们选择开发一个命令行界面（CLI）工具，而不是一个集成开发环境（IDE）？这是一个很好的问题，我认为主要有以下两点原因。首先，我们是在 Anthropic 启动这个项目的。在 Anthropic 内部，大家使用的 IDE 五花八门，有的人用 VS Code，有的人用 Zed、Xcode、Vim 或者 Emacs。因此，要开发一个能兼容所有这些环境的工具，挑战性很大。相比之下，终端（terminal）就是一个通用的解决方案，可以适用于所有人。其次，在 Anthropic，我们切身体会到了模型迭代速度之快。因此，我们认为很有可能到今年年底，开发者们将不再像现在这样依赖 IDE。为了迎接这个未来，我们希望避免在用户界面（UI）和其他上层架构上投入过多资源。考虑到当前模型的发展速度，这些投入可能很快就会变得不再那么有价值。

How much have you, I don't know if this is, is this on? How much you can use code for machine learning modeling and almost that auto ML experience? I was curious what the experience has been so far with that. Yeah, I think the question was how much are we using Claude Code for machine learning and modeling? We actually use it for this a bunch. So both engineers and researchers at Anthropic use Claude Code every day. I think about 80% of people at Anthropic that are technical use Claude Code every day. And hopefully you can see that in the product and kind of the amount of love and dog fooding we've put into it. But this includes researchers who use tools like the notebook tool to edit and run notebooks.

你们在多大程度上利用代码进行机器学习建模，并获得近似自动化机器学习（AutoML）的体验？我很好奇你们在这方面的经验如何。是的，我想问题是：我们使用 Claude Code（Claude Code）进行机器学习建模的程度有多高？我们实际上大量使用了它。Anthropic 的工程师和研究人员每天都在使用 Claude Code。我想 Anthropic 大约 80% 的技术人员每天都会用到 Claude Code。希望你们能在产品中感受到我们投入的热情和内部测试（即「狗粮式开发」）。这包括研究人员，他们会使用像笔记本工具这样的工具来编辑和运行代码。

Okay, very cool. Thank you. All right. I think very cool, thank you. All right, I think that's it, thanks.

I'm going to go ahead and get a little bit of 

好的，非常感谢。

我想借此机会，向大家详细介绍一些关键内容。

目前，人寿保险（life insurance）实际上并未受到（人工智能）冲击，但金融服务业的其他领域，无论是银行业务、资本市场、财富管理还是资产管理，我们都看到了令人难以置信的广泛应用，而且速度惊人。

现在，你提到了人工智能（AI）的炒作周期。我们无疑正处于一个巨大的人工智能炒作周期中。我们正处于顶峰，有人甚至说正在走下坡路。但与 2017、2018、2019、2020 甚至 2021 年初（当时我们开始看到一些早期迹象，预示着未来的发展）不同的是，人们现在不再问「人工智能能做什么」，而是问「我能用人工智能做什么」。这才是如今的重大区别。因此，我们在金融服务行业中首次看到的，不是炒作，而是人工智能应用带来的实实在在、可衡量的效益，尤其是生成式 AI（Generative AI）。

例如，在资本市场领域，我们拥有一些卓越的解决方案，生成式人工智能（Generative AI）不仅被用于总结，还能对财报电话会议进行实时分析。财报电话会议一直是获取阿尔法（alpha）的重要来源，但问题在于它们通常没有摘要，也缺乏分析，往往只是以一种杂乱无章的方式呈现。现在，生成式 AI（Generative AI）被用来实时总结、分析财报电话会议，并从中获取阿尔法（alpha）。

很多人会说，生成式 AI（Generative AI）是一个「黑箱」，也有人会说，你不能完全依赖它，因为它会「幻觉」。还有人会说，你不能在金融服务领域实际应用它，因为你需要某种完全透明、完全可审计、完全可解释的东西。这当然是对的。但我要再次强调，这正是人工智能（AI）革命如此强大的原因，因为它不仅仅关乎大语言模型（Large Language Model），还关乎许多其他方面：数据安全、数据治理、负责任的 AI（Responsible AI）。它关乎提供你所需的工具，以确保生成式 AI（Generative AI）的应用能够带来可解释、可审计和透明的益处。因此，我们 Microsoft（微软）、Amazon（亚马逊）和 OpenAI（OpenAI）正在做的是，为你提供工具，让你不仅能够将大语言模型（Large Language Model）用于这些目的，还能为这些大语言模型（Large Language Model）加上一个治理「外壳」、一个安全「外壳」和一个负责任的 AI（Responsible AI)「外壳」，从而使它们能够安全有效地用于这些目的。