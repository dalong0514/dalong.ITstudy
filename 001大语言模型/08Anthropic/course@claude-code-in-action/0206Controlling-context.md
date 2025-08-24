## 0206Controlling-context

[Controlling context](https://anthropic.skilljar.com/claude-code-in-action/303237)

In this video, I'd like to show you a couple of different techniques for controlling and directing the flow of conversation. Here's a basic example right away. I'm going to ask Claude to write tests for some functions written into an authentication file. Claude quickly comes up with a plan for authoring several different tests. However, I know that testing this file is a little tough, and I'd like Claude to only test one thing at a time.

在这个视频中，我将向大家展示几种控制和引导对话流程的方法。我们马上来看一个基本示例：我将要求 Claude 为一个认证文件中的某些函数编写测试。Claude 很快就提出了一系列不同的测试方案。然而，我深知测试这个文件具有一定挑战性，所以我希望 Claude 能一次只测试一个功能。

To interrupt Claude, I can press escape. This will stop Claude in its tracks, allowing me to suggest a different path. Combining escape along with memories is a really powerful way to fix errors that Claude makes repeatedly. Here's an example: I'm going to ask Claude to write tests for the same file again. This time around, it will attempt to read a test configuration file that doesn't actually exist. Now, this is an error that I've seen Claude make before on this project. So to stop this mistake from being repeated, I'll very quickly hit escape. I'll then use the pound shortcut to add in a memory about the correct name of this test configuration file. And now I probably won't have to see this error again.

想要打断 Claude 的工作，我只需按下「Escape」键。这样就能立刻阻止 Claude 继续执行，让我有机会引导它走向不同的方向。将「Escape」键与「记忆（memories）」功能结合使用，是修复 Claude 反复出现错误的一种非常有效的方法。举个例子：我准备再次让 Claude 为同一个文件编写测试。这一次，它会尝试去读取一个实际不存在的测试配置文件。在之前的项目中，我曾多次遇到 Claude 犯这种错误。为了避免这个错误再次发生，我会迅速按下「Escape」键，立即中断它的操作。接着，我将使用「井号」快捷键，为 Claude 添加一个关于这个测试配置文件正确名称的「记忆」。这样一来，我可能就再也不会看到这个错误了。

Some of these conversation control shortcuts seem like they're just for convenience, but used correctly, they can really improve Claude's ability to work effectively and stay on task. So let me show you a more practical example. Inside the auth ts file, there are four different functions, and I would like to get Claude to write tests for each of them, one at a time, first starting on a function called create session. Claude will definitely attempt to write the tests, but as it is running them, it runs into an error and spends a little bit of time debugging it. It turns out there was a package that I forgot to install. Eventually the tests are completed and working, and it's time to start working on the next set of tests.

这些对话控制快捷方式有些看似只是图个方便，但用对了，它们能显著提升 Claude 的工作效率和任务专注度。下面我来给大家展示一个更实际的例子。在 auth ts 文件里有四个不同的函数，我希望 Claude 能为它们逐一编写测试，先从一个叫做 `create session` 的函数开始。Claude 肯定会着手编写这些测试，但在运行过程中，它会遇到一个错误，并花点时间去调试。原来是我忘了安装一个依赖包。最终，这些测试顺利完成并运行正常，这时候就可以开始着手下一组测试了。

But here's the thing, in my conversation history, there is now a lot of back and forth around that broken package. Now this is a bunch of context that is not at all relevant to writing the next set of tests. Ideally, we would be able to jump back in time and go back to the previous message we sent and just update it to say, write tests for git session. Now the benefit here is that we maintain the context where Claude already took a look at the contents of the auth ts file and it already knows what we're talking about when we refer to Giz session. And because we dumped all those extra messages that we're just about debugging, we're not going to have as much distraction going on here. So again, Claude can really just stay focused and on task.

但问题在于，在我的对话历史中，现在有很多围绕那个损坏包的反复交流。这堆上下文与编写下一组测试完全不相关。理想情况下，我们应该能够「穿越」回过去，回到我们发送的上一条消息，然后将其更新为「为 git 会话编写测试」。这样做的好处是，我们保留了 Claude 已经检查过 auth ts 文件内容的上下文，并且当提及 Git 会话时，它已经知道我们在说什么。而且由于我们删除了那些只关于调试的额外消息，因此在这里不会有那么多干扰。所以，Claude 真的可以保持专注，并专注于手头的任务。

To go back in the conversation history, hit escape twice. This will show you all the different messages that you have sent, so you can rewind back to a previous point in time and skip over some intermediate conversation. Claude is now going to start working on the next set of tests. This time around, Claude stays super focused, but unfortunately, it runs into a number of issues. It eventually resolves them and gets the test to pass.

想要回顾之前的对话记录，只需连续按两下 Esc 键。这样你就能看到所有你发送过的消息，从而可以回溯到过去某个时间点，跳过中间的一些对话。现在，Claude 将开始着手处理下一组测试。这一次，Claude 全神贯注，但遗憾的是，它还是遇到了一些问题。不过，它最终都解决了这些问题，并顺利通过了测试。

Now at this point, Claude has been working by itself for several minutes and has a really good idea of how to write tests for this file. At the same time, once again, we have a bunch of context in this conversation history. When it is time to write tests for the next function, I'm going to use a command called compact. The compact command will take all the messages in the current conversation and summarize them. Compact is really useful when Claude has learned a lot about the current task and you want to maintain that knowledge as it goes into the next task.

这时，Claude 已经独自工作了几分钟，对如何为这个文件编写测试有了非常好的想法。同时，这次对话历史中也累积了很多上下文信息。当需要为下一个函数编写测试时，我将使用一个名为 compact 的命令。compact 命令会总结当前对话中的所有消息。当 Claude 对当前任务已经学到很多，并且你希望在它处理下一个任务时也能保留这些知识时，compact 命令就显得非常有用。

The last context-related command to be aware of is the clear command. Clear will dump the entire conversation history, allowing you to start off from scratch. Clear is most useful anytime you are about to start on a completely different task unrelated to the current one. I recommend using these shortcuts quite a bit, particularly when you are changing between tasks or anytime you are having a long-running conversation with Claude. In the remainder of this course, we'll use them several times to make sure that Claude stays on task and focused. Thank you.

最后，还有一个与上下文相关的命令需要了解，那就是「清除」（clear）命令。这个命令会清空所有的对话历史记录，让你能够从头开始一段全新的对话。「清除」功能在你要开始一个与当前任务完全不同的新任务时特别有用。我建议大家多使用这些快捷方式，尤其是在切换不同任务，或者与 Claude 进行长时间对话的时候。在本课程接下来的部分，我们会多次使用这些功能，以确保 Claude 能够始终专注于当前任务。谢谢。

## 网页文档

When working with Claude on complex tasks, you'll often need to guide the conversation to keep it focused and productive. There are several techniques you can use to control the flow of your conversation and help Claude stay on track.

当与 Claude 一起处理复杂任务时，你经常需要引导对话，确保它保持专注和高效。有几种技巧可以帮助你控制对话的流程，并让 Claude 不偏离主题。

### Interrupting Claude with Escape

用 Escape 键打断 Claude

Sometimes Claude starts heading in the wrong direction or tries to tackle too much at once. You can press the Escape key to stop Claude mid-response, allowing you to redirect the conversation.

有时候，Claude 会开始跑偏或试图一次性处理太多信息。这时，你可以按下 Escape 键，在 Claude 回答的过程中停止它，以便你重新引导对话。

This is particularly useful when you want Claude to focus on one specific task instead of trying to handle multiple things simultaneously. For example, if you ask Claude to write tests for multiple functions and it starts creating a comprehensive plan for all of them, you can interrupt and ask it to focus on just one function at a time.

当您希望 Claude 专注于某项具体任务，而不是同时处理多项事务时，这种做法会特别有用。例如，如果您要求 Claude 为多个函数编写测试，而它开始为所有函数制定一个全面的计划，您可以及时干预，并要求它一次只专注于一个函数。

### Combining Escape with Memories

将「逃逸」与「记忆」结合起来

One of the most powerful applications of the escape technique is fixing repetitive errors. When Claude makes the same mistake repeatedly across different conversations, you can:

「逃逸技术」(escape technique）最强大的应用之一，就是修正那些反复出现的错误。当 Claude 在不同的对话中，总是重复犯同样的错误时，你可以这样做：

1 Press Escape to stop the current response

2 Use the # shortcut to add a memory about the correct approach

3 Continue the conversation with the corrected information

This prevents Claude from making the same error in future conversations on your project.

这能帮助 Claude 在您项目未来的对话中避免再犯同样的错误。

### Rewinding Conversations

During long conversations, you might accumulate context that becomes irrelevant or distracting. For instance, if Claude encounters an error and spends time debugging it, that back-and-forth discussion might not be useful for the next task.

回溯对话在长时间的对话过程中，系统可能会累积大量上下文信息，其中有些信息可能会变得不相关或对后续任务造成干扰。举个例子，如果 Claude 遇到了一个错误，并花费时间进行调试，那么针对此错误进行的来回讨论，可能对执行下一个任务没有任何帮助。

You can rewind the conversation by pressing Escape twice. This shows you all the messages you've sent, allowing you to jump back to an earlier point and continue from there. This technique helps you:

你可以通过按两次 Escape 键来回溯对话。这会显示你发送过的所有消息，让你能够跳回到更早的某个节点，并从那里继续。这项技术能帮助你：

1 Maintain valuable context (like Claude's understanding of your codebase)

维护有价值的上下文（例如 Claude 对你的代码库的理解)

2 Remove distracting or irrelevant conversation history

移除干扰性或不相关的对话历史

3 Keep Claude focused on the current task

### Context Management Commands

上下文信息管理指令

Claude provides several commands to help manage conversation context effectively:

为了有效地管理对话上下文，Claude 提供了一些命令，例如：/compact

/compact

The /compact command summarizes your entire conversation history while preserving the key information Claude has learned. This is ideal when:

当你想让 Claude 总结整个对话历史，并同时保留它已经掌握的关键信息时，可以使用 /compact 命令。这在以下情况特别适用：

1 Claude has gained valuable knowledge about your project

Claude 对你的项目已经积累了宝贵的知识

2 You want to continue with related tasks

3 The conversation has become long but contains important context

Use compact when Claude has learned a lot about the current task and you want to maintain that knowledge as it moves to the next related task.

当 Claude 已对当前任务学到大量知识，并且你希望在它处理下一个相关任务时能保留这些知识时，就可以使用 compact。

/clear

The /clear command completely removes the conversation history, giving you a fresh start. This is most useful when:

/clear 命令会彻底清除对话历史，让你能够重新开始。它在以下场景中最有用：

1 You're switching to a completely different, unrelated task

当你需要切换到一个完全不同、不相关的任务时

2 The current conversation context might confuse Claude for the new task

3 You want to start over without any previous context

### When to Use These Techniques

These conversation control techniques are particularly valuable during:

这些对话控制技术在以下情况中尤其有价值：

1 Long-running conversations where context can become cluttered

在持续进行的对话中，上下文信息容易变得冗杂不清。

2 Task transitions where previous context might be distracting

在任务转换时，之前的语境（context）信息可能造成干扰

3 Situations where Claude repeatedly makes the same mistakes

Claude 反复出现相同错误的情况

4 Complex projects where you need to maintain focus on specific components

复杂项目：如何让 AI 专注于特定组件

By using escape, double-tap escape, /compact, and /clear strategically, you can keep Claude focused and productive throughout your development workflow. These aren't just convenience features—they're essential tools for maintaining effective AI-assisted development sessions.

通过巧妙地运用 escape 键、双击 escape 键、/compact 命令和 /clear 命令，你可以在整个开发工作流程中，让 Claude 始终保持专注和高效。这些指令不仅仅是便捷功能，它们更是维持高效的 AI 辅助开发工作的重要工具。