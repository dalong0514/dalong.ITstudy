## 0102What-is-a-coding-assistant

[What is a coding assistant?](https://anthropic.skilljar.com/claude-code-in-action/303235)

In this video, we're going to get a better understanding of what a coding assistant is. Yes, a coding assistant is a tool that writes code, but I want to give you a deeper understanding of what's going on behind the scenes. By understanding what a coding assistant really does and how it works, you'll have a greater appreciation of what makes a truly amazing assistant to complement your team.

在这个视频中，我们将深入了解什么是编码助手。没错，编码助手是一种能编写代码的工具，但我希望能让你更透彻地理解它背后的运作机制。通过理解编码助手真正能做什么以及它是如何工作的，你将更能体会到，一个真正出色的助手如何完美地融入并提升你的团队。

### 01

Here's one way you can picture what a coding assistant is doing. An assistant is first given a task. In this case, maybe the assistant needs to fix a bug based upon some kind of error message. This task is passed off internally to a language model, which needs to figure out how to solve the issue. Now, different language models solve problems in very different styles, depending upon the complexity of the task. But in many cases, they work very much like how a human would work.

我们可以这样来理解编码助手的工作方式。首先，助手会接到一个任务。例如，它可能需要根据某种错误消息来修复一个程序缺陷（bug）。接着，这个任务会内部传递给一个语言模型。这个语言模型需要思考并找出解决问题的方法。不同的语言模型解决问题的方式差异很大，这取决于任务的复杂程度。但在很多情况下，它们的工作模式和人类非常相似。

It first might need to gather context by understanding what the error is referring to, what area in the code base is during the error, and what files seem to be relevant. Once it has gathered that information, it then needs to formulate a plan on how it will actually accomplish the task. In this case, it might decide to change some code and then run or write a test to verify that the issue is actually fixed. Finally, it will take an action. In this case, that might be updating a file and running the tests.

一个 AI 智能体（AI Agent）首先可能需要收集一些背景信息，比如了解错误具体指的是什么，错误发生在代码库的哪个部分，以及哪些文件可能与此相关。一旦收集到这些信息，它就需要制定一个详细的计划，来实际完成任务。在这种情况下，它可能会决定修改部分代码，然后运行或编写一个测试来验证问题是否真的得到了解决。最后，它会采取具体的行动。例如，这可能包括更新某个文件并运行测试。

Now, I want to give you some more information on this entire process. In particular, I'd like you to notice that the first and last steps here require the coding assistant to actually do something. In other words, to actually gather information from the outside world or affect the outside world in some way. For example, to gather context, the assistant needs to maybe read a file or fetch some documentation online. And for taking action, the assistant might need to actually run a command or edit a file.

现在，我想为你详细介绍整个过程。特别需要注意的是，整个流程的第一步和最后一步都要求编码助手实际执行操作。换句话说，它们需要助手从外部获取信息，或以某种方式对外部环境产生影响。例如，为了收集上下文信息，助手可能需要读取文件或在线检索文档。而为了执行具体操作，助手可能需要实际运行命令或修改文件。

### 02

Now having a language model actually do these things is a little bit trickier than it actually sounds. Let me help you understand why that is. Let's imagine that we are interacting with a language model directly, so it's not running inside of any coding assistant or anything like that. Let's then imagine that we ask this language model directly what code is written inside the main go file.

然而，让一个语言模型（Language Model）真正完成这些任务，实际上比听起来要复杂一些。接下来，我将帮助你理解其中的缘由。让我们设想一下，我们正在直接与一个语言模型进行交互，而不是通过任何编码助手或其他集成环境来操作它。在这种情境下，我们直接向这个语言模型提问：main go 文件中包含了哪些代码？

Language models running outside the context of any coding assistant or similar tool do not inherently have the ability to say, read a file or write a command or anything like that. Language models take in content like text and they return text. That's it. That's the entire extent of their capabilities. And this is true of all language models. So if you were to send some text into a plain language model asking it to read a file, it would most likely respond by saying that it doesn't have the ability to read any files.

脱离了任何编程助手或类似工具的上下文，大语言模型（LLM）本身并不具备读取文件或执行命令等能力。大语言模型接收文本输入，然后也只返回文本输出。仅此而已，这就是它们能力的全部范畴。所有大语言模型都是如此。所以，如果你向一个普通的大语言模型发送一段文本，让它去读取一个文件，它很可能会回复说它无法做到。

So let me show you what coding assistants and many, many other tools out there do to actually allow a language model to quote unquote, read a file. So here's what happens. Whenever you send a request off to your coding assistant, the coding assistant behind the scenes is going to automatically append a lot of text into your request. In this particular case, we can imagine that the coding assistant is going to add on some text that says something like, if you language model want to read a file, respond with this very carefully formatted message. For example, maybe something like, refile colon and then the name of a file to read.

接下来，我将向你展示编码助手（coding assistant）以及许多其他工具是如何让语言模型（language model）真正「读取」文件的。具体过程是这样的：每当你向编码助手发送请求时，它会在后台自动向你的请求中添加大量文本。在这种特定情况下，我们可以想象编码助手会加入一些指令，比如：「如果你（指语言模型）想读取文件，请务必回复以下这种特定格式的消息。」例如，消息可能包含「refile:」，后面跟着要读取的文件名。

So in this case, the language model would hopefully realize that in order to answer our question, it needs to respond by reading that file. So it might respond with refile colon main go. Now the coding assistant would be in charge of receiving this very carefully formatted message and realizing that the language model wants to take some kind of action by reading a file. So the coding assistant would then be responsible for actually reading the file and sending the contents of that file back into the language model.

在这种情况下，大语言模型有望认识到，为了回答我们的问题，它需要通过读取该文件来回应。因此，它可能会回复 `refile：main.go`。现在，编码助手将负责接收这条经过仔细格式化的消息，并理解大语言模型希望通过读取文件来执行某种操作。因此，编码助手会实际读取该文件，并将其内容发送回大语言模型。

Now the language model has received the actual contents of that file, it can write a final response that gets sent back to us in which it might say, well, I read this file and it contains some amount of code or whatever else, whatever's inside that file. This entire system of giving a language model these extra little instructions asking it to respond in a very well-formatted or carefully-formatted way is referred to as tool use. So tools are used to give models extra capabilities. The model is responsible for responding in a very particular way, and then something like our coding assistant would be responsible for actually doing whatever was promised. So actually reading a file or writing a file or whatever else. Again, this is how every single language model out there works. They all work with this idea of tool use.

当语言模型（Large Language Model）接收到文件的实际内容后，它就可以生成一个最终响应并返回给我们。在响应中，模型可能会说：「我读取了这个文件，它包含了一些代码或其他内容，也就是文件里所有的东西。」这种给语言模型提供额外指令，并要求它以特定格式（例如排版良好或精心排版）回应的整个系统，就被称为「工具使用」（tool use）。

因此，工具被用来赋予模型额外的能力。模型负责以一种非常特定的方式进行回应，然后像我们的编码助手这样的程序则负责实际执行模型承诺的操作，比如真正地读取或写入文件等。值得一提的是，目前所有语言模型都采用这种「工具使用」的理念来运作。

### 03

Now here's the critical part to understand. The Claude series of models, so Opus, Sonnet, and Haiku, are particularly strong at understanding what tools do when they're called, and actually using them to effectively complete tasks, and using them in really interesting combinations to complete more advanced or complex tasks.

现在，我们需要理解一个关键点：Claude 系列模型（包括 Opus、Sonnet 和 Haiku）在理解工具被调用时其具体功能方面表现得尤为出色。它们不仅能够实际有效地运用这些工具来完成任务，还能以非常巧妙的组合方式使用它们，从而处理更高级或更复杂的任务。

Claude's strong tool use is the absolute core strength of Claude code as a coding assistant. Here's why. First, as I just mentioned, with better tool use, Claude can handle more complex tasks. Second, Claude Code itself is extensible, so it's really easy to add new tools to Claude Code. And Claude will happily make use of those tools. This is especially important for continued relevance, given the fast changes that we're seeing in the world of development. In other words, Claude Code is an assistant that will change with you in the years to come.

Claude 强大的工具使用能力（tool use）是 Claude Code 能够成为出色编程助手的核心优势。原因有两点：首先，正如我们前面提到的，凭借更强的工具使用能力，Claude Code 可以应对更复杂的任务。其次，Claude Code 本身具有良好的可扩展性，这意味着你可以非常轻松地为其添加新的工具，而 Claude 也会非常乐意地运用这些新工具。鉴于当前开发领域瞬息万变，这一点对于保持其持续相关性尤为重要。换句话说，Claude Code 是一款能够与您共同成长，在未来几年持续提供助力的智能助手。

And finally, with improved tool use, you often get better security, because Claude can effectively search your codebase to find relevant code without relying upon indexing, which often relies upon sending your entire codebase to outside servers.

最后，随着工具使用能力的提升，你通常会获得更好的安全性。这是因为 Claude 可以有效地搜索你的代码库，从而找到相关的代码，而无需依赖索引。索引这种方式通常需要将你的整个代码库发送到外部服务器，这可能会带来安全风险。

Let's do a quick review on what we learned inside this video around what a coding assistant really is. So remember, coding assistants use language models internally to complete different tasks. These language models, they need to know how to use tools to work on the vast majority of tasks that they are given. Tools are used to read files, write files, run commands, and essentially everything else that doesn't just involve generating some text. Not all language models make use of tools at the same level, and this has a big impact on the overall efficiency of a coding assistant. Thank you.

让我们快速回顾一下在这个视频中我们了解到的，到底什么是编码助手。请记住，编码助手在内部利用语言模型（language model）来完成各种任务。这些语言模型需要知道如何使用工具，才能处理它们所面临的绝大多数任务。工具被用来读取和写入文件、运行命令，以及本质上所有那些不仅仅是生成文本的工作。并非所有语言模型在利用工具方面的能力都相同，而这一点对编码助手的整体效率有着巨大的影响。

## 网页文档

A coding assistant is more than just a tool that writes code - it's a sophisticated system that uses language models to tackle complex programming tasks. Understanding how these assistants work behind the scenes will help you appreciate what makes a truly powerful coding companion.

一个编程助手不只是一个简单的代码编写工具，它更是一个精密的系统，利用语言模型（language models）来解决复杂的编程难题。深入了解这些助手在幕后的运作机制，将帮助你更好地理解是什么造就了一个真正强大的编程搭档。

### How Coding Assistants Work

编码助手如何工作

When you give a coding assistant a task, like fixing a bug based on an error message, it follows a process similar to how a human developer would approach the problem:

当你给一个编码助手（coding assistant）一个任务时，例如根据一个错误消息修复一个 bug（程序错误），它会遵循一个与人类开发者（human developer）处理问题方式类似的过程：

1 Gather context - Understanding what the error refers to, which part of the codebase is affected, and what files are relevant

收集上下文 - 弄清错误具体指什么，代码库（codebase）的哪个部分受到了影响，以及涉及哪些文件

2 Formulate a plan - Deciding how to solve the issue, such as changing code and running tests to verify the fix

制定计划 - 决定如何解决问题，例如修改代码和运行测试来验证修复效果

3 Take action - Actually implementing the solution by updating files and running commands

采取行动 - 通过更新文件和运行命令真正落地解决方案

The key insight here is that the first and last steps require the assistant to interact with the outside world - reading files, fetching documentation, running commands, or editing code.

这里的核心洞察是，第一步和最后一步要求 AI 智能体（AI Agent）与外部世界进行交互，包括读取文件、获取文档、运行命令或编辑代码。

### The Tool Use Challenge

工具使用挑战

Here's where things get interesting. Language models by themselves can only process text and return text - they can't actually read files or run commands. If you ask a standalone language model to read a file, it will tell you it doesn't have that capability.

事情在这里开始变得有意思了。语言模型（Language model）自身只能处理和生成文本，它们实际上无法读取文件或执行命令。如果你让一个独立的大语言模型读取某个文件，它会明确告诉你它不具备这项功能。

So how do coding assistants solve this problem? They use a clever system called "tool use."

那么，编码助手是如何解决这个问题的呢？它们使用了一套巧妙的系统，被称作「工具使用」。

### How Tool Use Works

工具使用的工作方式

When you send a request to a coding assistant, it automatically adds instructions to your message that teach the language model how to request actions. For example, it might add text like: "If you want to read a file, respond with 'ReadFile: name of file'"

当你向编程助手发送请求时，它会自动在你的消息中添加指令，这些指令会教导大语言模型（Large Language Model）如何请求执行特定操作。例如，它可能会添加这样的文本：「如果你想读取一个文件，请回复‘ReadFile：文件名'」。

Here's the complete flow:

以下是完整的流程：

1 You ask: "What code is written in the main.go file?"

你会问：「main.go 文件中写了什么代码？」

2 The coding assistant adds tool instructions to your request

代码助手会将工具指令添加到你的请求中。

3 The language model responds: "ReadFile: main.go"

大语言模型（Large Language Model）回应道：「ReadFile：main.go」

4 The coding assistant reads the actual file and sends its contents back to the model

编程助手会读取相应文件，然后将文件内容回传给模型。

5 The language model provides a final answer based on the file contents

大语言模型（Large Language Model）则会根据这些文件内容给出最终的答案。

This system allows language models to effectively "read files," "write code," and "run commands" even though they're really just generating carefully formatted text responses.

这个系统能够让大语言模型（Large Language Model）高效地「读取文件」、「编写代码」和「运行命令」，即便它们本质上只是在生成精心编排的文本响应。

### Why Claude's Tool Use Matters

为何 Claude 的工具使用能力如此重要

Not all language models are equally good at using tools. The Claude series of models (Opus, Sonnet, and Haiku) are particularly strong at understanding what tools do and using them effectively to complete complex tasks.

并非所有的大语言模型（Large Language Model）在使用工具方面都能做得同样出色。Claude 系列模型（包括 Opus，Sonnet，and Haiku）尤其擅长理解工具的用途，并能有效地利用这些工具来完成复杂的任务。

This strength in tool use provides several key benefits for Claude Code:

Claude Code 在工具使用上的这一优势为其带来了几个主要益处：

### Benefits of Strong Tool Use

强大工具使用能力的优势

1 Tackles harder tasks - Claude can combine different tools to handle complex work and will use tools it hasn't seen before

攻克更复杂的任务 - Claude 能够巧妙结合多种工具来应对复杂的工作，甚至能自主运用之前从未接触过的新工具。

2 Extensible platform - You can easily add new tools to Claude Code, and Claude will adapt to use them as your workflow evolves

可扩展平台 - 您可以轻松地为 Claude Code 添加新工具，随着工作流程的演变，Claude 会随之调整并适应这些新工具的使用。

3 Better security - Claude Code can navigate codebases without requiring indexing, which often means not sending your entire codebase to external servers

更高的安全性 - Claude Code 能够在无需预先建立索引的情况下，在代码库中进行导航和操作，这意味着通常无需将你的整个代码库传输到外部服务器。

### Key Takeaways

主要收获

Understanding coding assistants comes down to a few essential points:

要理解编程助手（coding assistants），主要有以下几个核心要点：

1 Coding assistants use language models to complete different tasks

编程助手利用语言模型来完成各种不同的任务

2 Language models need tools to handle most real-world programming tasks

语言模型（Language models）需要工具，才能处理大多数实际的编程任务。

3 Not all language models use tools with the same skill level

然而，并非所有语言模型使用工具的能力都达到相同的水平。

Claude's strong tool use enables better security, customization, and longevity in Claude Code

Claude 强大的工具使用能力为 Claude Code 带来了更好的安全性、定制化和持久性。

This tool-use capability is what transforms a simple text-generating model into a powerful coding assistant that can read your files, understand your codebase, and make meaningful changes to your projects.

正是这种工具使用能力，将一个简单的文本生成模型（text-generating model）转变为一个强大的编程助手。这个助手能够读取你的文件，理解你的代码库（codebase），并对你的项目进行有意义的修改。
