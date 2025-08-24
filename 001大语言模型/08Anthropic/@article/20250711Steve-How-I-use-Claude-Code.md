## 20250711Steve-How-I-use-Claude-Code

I have now for the last several weeks switched over from Cursors Agents to Claude Code and I'm not looking back at all. Here's how I use Claude Code and my best tips.

我已经用 Claude Code 替代 Cursors Agents 好几个星期了，而且完全没有回头的意思。以下是我如何使用 Claude Code 以及我总结的最佳技巧。

### 01

08s

First, I install the extension, which works with VS Code, Cursor, and probably other forks like Windsurf. It doesn't do a lot, but it makes it really easy to launch Claude Code right in your IDE. I still use Cursor by default because, every once in a while, it's nice to use Command-K and their tab completions. But the only time I've touched the agent sidebar is when Claude was down.

首先，我安装了这个扩展，它能与 VS Code、Cursor 以及 Windsurf 等其他分支协同工作。虽然功能不多，但它确实让在集成开发环境（IDE）中启动 Claude Code 变得非常便捷。我依然默认使用 Cursor，因为偶尔用一下 Command-K 快捷键及其标签自动补全功能确实很方便。但说实话，我唯一一次用到 AI 智能体（agent）侧边栏，还是在 Claude 服务宕机的时候。

What the extension does do is it makes it really easy to open Claude Code. I often have it in multiple panes at a time, so I can run things in parallel as long as they're working on different parts of the codebase and different files. And if I have a file open, it'll automatically pull that into the context.

这个扩展最主要的功能，是让用户可以非常方便地打开 Claude Code。我通常会同时在多个窗格中打开 Claude Code，这样就能并行处理多个任务，只要它们处理的是代码库中不同的部分和不同的文件。如果我打开了一个文件，它还会自动将这个文件加载到上下文中。

Now, Claude uses a terminal UI, which I was very hesitant about at first. But they actually do a really good job with it. You can tag files easily and choose what you want to include. They have slash commands, which are awesome. Speaking of, I use the "model" command a lot and usually work with Opus. Unless Opus is having issues, which happens, and then switch to Sonnet. A lot of people should probably just use the defaults: it'll use Opus until you're at 50% of your usage limits and then switch to Sonnet, which is more cost-efficient. I found Opus isn't slow like 3.5 used to be compared to Sonnet, at least not noticeably. And both models are very good, but Opus is just a little bit better.

现在，Claude 采用了命令行界面（UI），我起初对此颇为犹豫。但实际体验下来，他们做得确实很棒。你可以轻松地给文件打上标签，并选择想要在对话中包含哪些内容。他们还提供了斜杠命令，这功能非常实用。说到这里，我个人很常用「模型」命令，通常会选择 Opus 模型。除非 Opus 出了问题（这确实偶尔会发生），我才会切换到 Sonnet。对于大多数用户来说，直接使用默认设置可能更合适：系统会优先使用 Opus，直到你达到使用限制的 50%，然后自动切换到更具成本效益的 Sonnet。我发现 Opus 的速度并不像之前的 3.5 版本那样，与 Sonnet 相比显得迟缓，至少我没有明显感觉到。总的来说，这两个模型都表现出色，但 Opus 略胜一筹。

Other commands I use a lot, I use "clear" a lot. In my opinion, every time you're doing something new, "clear." You don't need all that chat history in your tokens every time, and you don't need Claude always trying to compact it either. Because compaction basically runs another LLM call to output a bunch of tokens, which takes time to summarize the conversation history. Just clear. Clear every time you're doing something new. The up arrow key will go back to past chats, including chats from prior sessions. So if you close out of Claude and open it again, for instance, another day, you can still go back to prior sessions.

我经常使用的另一个命令是「clear」。在我看来，每次开始新任务时，都应该「clear」。你不需要每次都将所有聊天历史存储在 token 中，也不需要 Claude 总是尝试去压缩它们。因为压缩聊天历史实际上是运行另一次大语言模型（LLM）调用，输出大量 token 来总结对话历史，这会耗费时间。所以，只需清除。每次开始新任务时都清除。向上箭头键可以查看过去的聊天记录，包括之前会话中的记录。因此，即使你关闭 Claude 并在稍后，比如第二天再次打开，你仍然可以回到之前的会话。

Speaking of opening Claude, one thing it does that's really annoying is after you type a prompt, it'll start working. Agents take a while, so I'll go about my business. I'll check Slack, I'll check email, I might code something manually. But then here's the problem: I come back and I see it's asking me, "Can I edit this file?" It's really annoying. Yes, you can edit files! It's the point of being an agent, like, edit the files. And there's no way I've found to globally say, "Just edit files, it's fine." And then you go about your business and come back and it's asking if it can run a basic bash command, "Can I run lint?" Yes, oh my God, yes.

说到使用 Claude，它有一个让人非常恼火的地方：当你输入提示后，它就开始工作了。由于 AI 智能体（AI Agent）完成任务需要一些时间，我就会去做自己的事情。比如，我会查看 Slack，处理电子邮件，或者自己手动编写一些代码。但问题就出在这里：当我回来时，会看到它跳出来问我：「我可以编辑这个文件吗？」这真的很烦人。当然可以编辑文件！这不就是作为一个 AI 智能体的意义所在吗，就是用来编辑文件的啊。然而，我却找不到任何方法可以全局性地告诉它：「尽管编辑文件，没关系。」然后你又去做你的事情，回来时它又会问你是否可以运行一个基本的 bash 命令：「我可以运行 lint 吗？」天呐，当然可以了！

So here's what I actually do: Every time I open Claude Code, I actually quickly hit Command-C and then I run `Claude --dangerously-skip-permissions` and enter. It's not necessarily as dangerous as it sounds. It's akin to what Cursor used to call YOLO mode. And while it runs a minor risk that a rogue agent could run a command you didn't expect that's destructive, I've never seen that happen in my life. So it's up to you if you want to take the risk. I have for weeks and weeks and I've never run into a problem whatsoever.

我实际操作是这样的：每次我打开 Claude Code，我都会快速按下 Command-C，然后运行 `claude --dangerously-skip-permissions`，然后回车。它其实没听起来那么危险。这类似于 Cursor 曾称之为的 YOLO 模式。虽然存在一个微小的风险，即一个流氓 AI 智能体（AI agent）可能会运行你意想不到的破坏性命令，但我个人从未遇到过这种情况。所以是否要承担这个风险，取决于你自己。我这样操作已经好几周了，从未遇到任何问题。

Now, speaking of slash commands, Claude has a lot. One really cool one is installing the GitHub app. This makes it so when you submit a PR, Claude will automatically do a code review. This is pretty awesome because as you use more AI tools, your volume of pull requests might increase. And I found in certain cases the AI models are better at finding bugs than humans because they frankly put more effort into it in some ways. While I've seen humans are really common to nitpick at, "Oh, this could be named differently," and stuff like that, I've seen Claude actually find real bugs that humans missed in a good chunk of cases.

现在，说到斜杠命令，Claude 提供了不少。其中一个非常实用的功能就是安装 GitHub 应用。这样一来，当你提交拉取请求（PR）时，Claude 就会自动进行代码审查。这个功能非常出色，因为随着我们越来越多地使用 AI 工具，提交的拉取请求数量可能会随之增加。我发现在某些情况下，AI 模型在发现程序错误（bug）方面比人类更胜一筹，因为它们在某些方面确实能更全面地进行检查。相比之下，人类常常会纠结于一些细节，比如「哦，这个变量名可以换一个」，但我观察到，在很多情况下，Claude 确实能发现人类遗漏的真实 bug。

The main tip I have for this is Claude will add a `claude-code-review.yaml`. It'll have a prompt in it already. Here's the prompt I use: The original issue we found with this tool is it was really verbose. It would comment on all kinds of, like, nuanced, unimportant things and write a whole essay on every PR. What we really care most for the AI to review is bugs and potential vulnerabilities. So we tell it, "Look for bugs and security issues, only report on bugs and potential vulnerabilities, and be concise." The cool part is when you run this command and edit that one line, you have a pretty awesome new addition to your workflow.

我给大家的建议是，Claude 会自动生成一个名为 `claude-code-review.yaml` 的配置文件，里面预设了一个提示词。我个人使用的提示词是这样的：我们最初发现这个工具的问题是它过于「话痨」，总是对各种细枝末节、无关紧要的地方发表一大堆评论，每次代码合并请求（PR）都像写一篇长篇大论。而我们真正希望 AI 关注的，是代码中的 bug 和潜在的安全漏洞。因此，我们明确告诉它：「只查找 bug 和安全问题，只报告 bug 和潜在漏洞，并且要言简意赅。」最棒的是，当你运行这条命令并修改配置文件中的那一行提示词后，你的工作流程就能得到一个相当实用的新功能。

There's a lot of other really cool stuff it can do, like pull comments from a GitHub pull request and address them, review pull requests, and do things like send up your terminal. Because out of the box, Shift-Enter will not work for adding new lines, but we can just hit Enter and tell it to do it for us. And there we go. Shift-Enter adds new lines. Beautiful.

它还能做很多其他非常酷的功能，比如从 GitHub 拉取请求中提取评论并进行处理，审查拉取请求，甚至还能帮你处理终端操作。举个例子，默认情况下，Shift-Enter 键无法用于添加新行，但我们可以通过按 Enter 键并告诉它来为我们完成这项操作。你看，现在 Shift-Enter 就能添加新行了。非常方便。
