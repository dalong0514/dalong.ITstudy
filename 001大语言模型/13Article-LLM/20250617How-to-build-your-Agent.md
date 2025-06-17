## 20250617How-to-build-your-Agent

[How to build your Agent: 11 prompting techniques for better AI agents - Augment Code](https://www.augmentcode.com/blog/how-to-build-your-agent-11-prompting-techniques-for-better-ai-agents)

May 21, 2025

如何构建你的 AI 智能体：11 种提示技术，助力打造更优 AI 智能体

### 01. Intro

简介

Prompt engineering has become one of the highest-leverage skills in modern software development. The prompt you feed an agent shapes how it plans, how it uses tools, and whether it builds or breaks your pipeline. Tiny changes—an extra line of context, a clarified constraint, a reordered instruction—often produce outsized gains in accuracy and reliability. This post distills field-tested tactics we use at Augment Code to build autonomous agents that behave like disciplined teammates instead of hallucinating vibe coding tools.
The examples in the post focus on coding agents, but the techniques are generally applicable.

提示工程（Prompt Engineering）已成为现代软件开发中影响力最大的技能之一。你给 AI 智能体（AI Agent）输入的提示（Prompt），决定了它如何规划、如何使用工具，以及是成就还是损害你的工作流程。即使是微小的改动 —— 比如多一行上下文、一个更清晰的约束条件，或者对指令进行重新排序 —— 通常也能显著提升准确性和可靠性。本文提炼了我们在 Augment Code 经过实践检验的策略，旨在帮助你构建出能像严谨的队友一样工作的自主 AI 智能体，而不是那些只会「随意编码」并出现幻觉的工具。
本文中的示例侧重于编码 AI 智能体，但这些技术具有普遍适用性。

### 02. What is prompt engineering?

什么是提示工程？

An agent’s prompt includes everything that gets supplied to the model as input. This includes various components:

AI 智能体（AI Agent）的提示（prompt）包括所有作为输入提供给模型的内容。这通常包含以下几个组成部分：

* System prompt
* Tool definitions
* Tool outputs
* User instructions
* The model’s own outputs from previous turns

* 系统提示（System prompt)
* 工具定义（Tool definitions)
* 工具输出（Tool outputs)
* 用户指令（User instructions)
* 模型在之前交互回合中自身的输出

Prompt engineering is the art of improving a model’s performance on a task by providing it with a better prompt. All parts of the prompt can be potentially improved with prompt engineering. For example:

提示工程（Prompt engineering）是一门通过提供更优质的提示（prompt）来提升模型在特定任务上表现的技术。提示中的各个部分都有可能通过提示工程得到改进。例如：

* The system prompt can include general instructions to nudge the model toward different response styles or levels of autonomy
* Tool definitions can explain to the model under which circumstances a tool should or shouldn’t be used
* Tool outputs can tell the model about error conditions
* User instructions can be re-written before being shown to the model (prompt enhancement).
* Previous model outputs can be compressed or truncated to save tokens, so longer dialog histories can fit in the context window. How they are truncated matters for quality

* 系统提示（system prompt）可以包含一般性的指令，引导模型以不同的响应风格或自主程度进行输出。
* 工具定义（tool definitions）可以向模型解释在什么情况下应该使用或不应该使用某个工具。
* 工具输出（tool outputs）可以告知模型可能出现的错误情况。
* 用户指令（user instructions）可以在展示给模型之前进行改写（即提示增强）。
* 之前的模型输出可以被压缩或截断以节省 Token，这样更长的对话历史就能塞进上下文窗口。如何截断这些输出对最终质量至关重要。

### 03. How to think about the model

如何理解模型

The model is (artificially) intelligent. Prompting a model is closer to talking to a person than it is programming a computer. The model builds a view of the world that is solely based on what’s in the prompt. The more complete and consistent that view is, the better the model’s results will be.
The model presents to us a natural language interface, that is separate from the programming language one works in. It’s useful to think of the LM interface as a separate but real abstraction layer. This interface can be used to present happy-path results, but also to alert of errors, notify of changes, etc. — to generally communicate with the model.

模型是具有人工智能的。与模型进行交互（提示模型）更像是与人交谈，而非对计算机进行编程。模型会根据提示中的内容，构建一个完全属于它自己的「世界观」。这个「世界观」越完整、越一致，模型的结果就会越好。模型为我们提供了一个自然语言界面，它独立于我们使用的编程语言。将这个大语言模型（LLM）界面视为一个独立但真实的抽象层是非常有用的。这个界面不仅可以用来展示「正常情况下的结果（happy-path results）」，还可以用于提示错误、通知变更等 —— 总而言之，它用来与模型进行沟通。

Example:

If the model calls a tool incorrectly, do not raise an exception in your agent code. Instead, return a tool result that explains what the error was: Tool was called without required parameter xyz. The model will recover and try again.

如果模型错误地调用了某个工具，您的 AI 智能体（AI Agent）代码不应直接抛出异常。相反，您应该返回一个工具执行结果，明确说明发生了什么错误，例如：「调用工具时缺少了必需参数 xyz。」这样，模型就能自行纠正并再次尝试。

### 04. How to evaluate prompts

It is usually difficult to automatically evaluate prompts, unless the goal is to have the model perform a very specific task. Try to come up with scenarios that test the prompt in various ways, and also try to find examples where the prompt change might cause regressions. For a concrete example of these evaluation principles in action, see how the same prompt-engineering techniques propelled Augment Code to the #1 open-source score on SWE-bench.

如何评估提示评估提示（prompts）通常是个难题，除非你要求模型完成一项非常具体的任务。在评估时，我们应该设想不同的场景来全面测试提示，并尝试找出那些即便只是细微的提示改动也可能导致性能下降（即「回归」）的例子。想要了解这些评估原则在实践中是如何应用的吗？不妨看看 Augment Code 项目是如何运用相同的提示工程（prompt-engineering）技术，一举登顶 SWE-bench 开源榜单的。

### 05. Prompt engineering tips

提示工程秘籍

Follow these tips and you will unlock AGI.

掌握这些技巧，你将离通用人工智能（AGI）更近一步。

#### 5.1 Focus on context first

上下文为王

The most important factor in prompt engineering is providing the model with the best possible context: the information supplied by the user (as opposed to prompt text supplied by us). This is the main signal the model uses to perform its task.

在提示工程（Prompt Engineering）中，最重要的莫过于为模型提供最恰当的上下文。这里的上下文指的是用户提供的信息，而不是我们额外输入的提示文本。这些信息是模型执行任务时最主要的依据。

Current models are good at finding relevant pieces of useful context within large prompts, so when in doubt, lean toward providing more information if it increases the chance that the context includes useful relevant information.

现在的模型都非常擅长从冗长的提示中找出有用的相关上下文。所以，当你拿不准的时候，如果能增加上下文中包含有用信息的可能性，那就尽管多提供一些信息吧。

The first question that should be asked about a prompt is — does it contain all the relevant information, and with what likelihood? Answering this question is not always trivial.

关于一个提示，我们首先应该问自己的问题是 —— 它是否包含了所有相关信息？包含的可能性有多大？回答这个问题可不是件简单的事。

Example:

When truncating long command outputs for providing them to the model, the truncation method matters. Typically, truncating long text involves truncating the suffix. However, for command outputs, useful information is more likely to appear in the prefix and suffix than in the middle. For example, stack traces from crashes generally appear in the suffix. Therefore, to maximize the likelihood that the model gets the most relevant context, it is better to truncate the middle of commands outputs than the suffix.

在将冗长的命令输出截断后提供给模型时，采用哪种截断方法至关重要。通常来说，截断长文本会直接剪掉末尾的部分。然而，对于命令输出来说，有用的信息往往集中在开头和结尾，而不是中间部分。举例来说，程序崩溃时产生的堆栈跟踪信息通常会出现在输出的末尾。因此，为了让模型尽可能多地获取到最相关的上下文信息，更好的做法是截断命令输出的中间部分，而不是直接剪掉末尾。

#### 5.2 Present a complete picture of the world

描绘一个完整的世界图景

Help the model get in the right mood by explaining the setting it’s operating in, and providing details that may be useful for it to perform well. For example, if you want the model to act as a software developer, tell it that in the system prompt. Explain to it what resources it has access to, and how it should use them.

为了帮助模型进入「工作状态」，你需要向它解释其运行的背景环境，并提供有助于其高效运行的详细信息。例如，如果你希望模型扮演软件开发人员的角色，请在系统提示中明确告知。同时，还要向它说明可以使用哪些资源以及如何利用这些资源。

For example, these two lines were introduced to the system prompt early on in the Augment agent’s development, and dramatically improved its performance:

举例来说，在 Augment AI 智能体（AI Agent）的早期开发阶段，在系统提示中加入了下面两行描述，就显著提升了其性能表现：

```
You are an AI assistant, with access to the developer's codebase. You can read from and write to the codebase using the provided tools.
```

#### 5.3 Be consistent across prompt components

确保提示组件间的一致性

Make sure all components of the prompt (system prompt, tool definitions, etc.), as well as the underlying tool definitions, are consistent.

务必保证提示（Prompt）的所有组成部分（包括系统提示、工具定义等）以及底层的工具定义之间保持一致。

Example:

* The system prompt includes the line The current directory is $CWD
* The execute_command tool, which allows the agent to execute shell commands, includes an optional cwd parameter. Consistency implies that the default value of this parameter should be $CWD. This can be specified in the tool definition. If it is not, the model will likely assume that is the case.
* The read_file tool accepts a path parameter of the file to read. If supplied with a relative path, it should be interpreted as being relative to $CWD.

* 系统提示中包含一行指令：「当前目录是 $CWD」。
* execute_command 工具允许 AI 智能体（AI agent）执行 shell 命令，该工具带有一个可选的 cwd 参数。为了保持一致性，这个参数的默认值应该是 $CWD。这一点可以在工具定义中明确指定。如果没有明确指定，模型很可能会默认将其视为 $CWD。
* read_file 工具接受一个 path 参数，用于指定要读取的文件路径。如果提供的是相对路径，那么这个路径应该被解读为相对于 $CWD。

Note: Avoid surprising the model. Models are easily confused. If the model is likely to expect a certain outcome from a tool call, make sure to either provide that outcome, or explain the deviation in the tool result. For example, if the tool definition promises to return an output of a certain length, either return output of that length, or preface the answer with a statement like Output of length N was requested, but returning output of length K instead because ...

注意：避免让模型感到意外。模型很容易感到困惑。如果模型可能期望从工具调用中获得某种结果，请确保给出相应的结果，或在工具结果中解释偏差。例如，如果工具定义承诺返回某个长度的输出，则要么返回该长度的输出，要么在答案前加上类似这样的话：「请求了长度为 N 的输出，但返回了长度为 K 的输出，因为...」。

Example:
 
* If the prompt contains state that may change during a session (e.g. the current time), do not include them in the system prompt or in tool definitions
* Instead, tell the model about the change in the next user message. This keeps the prompt internally consistent: the model can see what the state was at each turn.

* 如果提示中包含在会话期间可能发生变化的状态信息（例如当前时间），请不要将这些信息放入系统提示或工具定义中。
* 相反，可以在接下来的用户消息中告知模型这些变化。这样做能保持提示的内部一致性：模型可以在对话的每个回合中清晰地了解当前的状态。

#### 5.4 Align the model with the user's perspective

让模型理解用户的「所见」和「所想」

Consider the user’s perspective, and try aligning the model with that perspective.

我们需要站在用户的角度思考问题，努力让模型能够真正理解用户的视角。

Example: When the user works in the IDE, the model can be presented with a detailed view of the IDE state, focusing on the elements the user is most likely to care about, or refer to in their instructions.

举个例子：当用户在集成开发环境（IDE）中进行编程时，模型可以获得 IDE 状态的详细视图，并且特别关注用户最可能关心或在其指令中提及的代码、文件等元素。

Examples of things that can potentially help align the model:

以下是一些可能帮助模型更好地理解用户视角的方法：

* The user’s current time and timezone
* The user’s current location
* The user’s activity history

* 用户的当前时间及所在时区
* 用户的当前位置
* 用户的活动历史

Example of a basic system prompt that includes IDE state:

包含 IDE（集成开发环境）状态的基本系统提示（System Prompt）示例：

The user works in an IDE. The current IDE state:

The IDE is of type VSCode.

The currently open file is foo.py.
Lines 134 through 179 are visible on the screen.
Here is the currently visible text, with the cursor location denoted by <CURSOR>:

```python
134  def bar():
135    print("hell<CURSOR>o")
...
179  # TODO implement this
```

There is no selected text.
There are 14 open tabs. Here they are from most recently to last recently visited:
foo.py
bar.py ...
xyz.py

Note: This is not to suggest that one of these prompts is necessarily better than the other. The potential downside of the detailed prompt is that the model might start paying too much attention to the IDE state, which isn’t always the best signal for what the user is trying to do.

注意：这并非暗示其中一个提示必然优于另一个。详细提示的潜在缺点是，模型可能会开始过度关注 IDE 状态，而这并非总是指示用户意图的最佳信号。

#### 5.5 Be thorough

提示要详尽

Models benefit from thorough prompts. Do not worry about prompt length. Current context lengths are long and will keep increasing: You cannot make a dent in the prompt budget by writing longer prompts.

给模型的提示越详尽，模型表现得越好。因此，不必担心提示的长度。当前模型支持的上下文长度（可以理解和处理的文本量）已经很长，并且还会不断增加：即使你写再长的提示，也不会显著超出模型的处理「预算」。

Example of a successful and detailed prompt, that teaches the model how to use Graphite, a version control tool:

下面是一个成功且详细的提示示例，它教模型如何使用 Graphite（一个版本控制工具）：

```
\## Using Graphite for version control
We use Graphite for version control on top of git. Graphite helps manage git branches and PRs.Graphite maintains stacks of PRs: changes to a PR automatically cause rebases on higher PRs in the stack,saving a lot of manual effort. Each section below describes how to perform a common version control workflows using Graphite and GitHub.If the user asks you to perform such a workflow, follow these guidelines.
\### What NOT to do
Do not use `git commit`, `git pull`, or `git push`. These commands are all replaced by Graphite commands that start with `gt`, as described below.
\### Creating a PR (and branch)
In order to create a PR, do the following:
- Use `git status` to see which files were changed, and which files are new- Use `git add` to stage the relevant files- Use `gt create USERNAME-BRANCHNAME -m PRDESCRIPTION` to create the branch, where: `USERNAME` can be obtained, see instructions elsewhere `BRANCHNAME` is a good name for the branch you come up with `PRDESCRIPTION` is a good description for the PR you come up with- This may fail because of pre-commit issues. Sometimes pre-commit fixes the issues itself. Check `git status` to see if any files were modified. If so, `git add` them. If not, fix the issues yourself and `git add` them. Then repeat the `gt create` command to try creating the PR again.- Run `gt submit` to create the PR on GitHub (if you're only creating the branch, skip this step).- If `gh` is available, use it to set a PR description.
Note: Do not forget to add files before running `gt create`, or you will get stuck!
\### Updating a PR
In order to update a PR, do the following.
- Use `git status` to see which files were changed, and which files are new- Use `git add` to stage the relevant files- Use `gt modify` to commit the changes (no need to supply a message)- This may fail because of pre-commit issues. Sometimes pre-commit fixes the issues itself. Check `git status` to see if any files were modified. If so, `git add` them. If not, fix the issues yourself and `git add` them. Then repeat the `gt create` command to try creating the PR again.- Use `gt submit` to push the changes- If you also need to update the PR description, use `gh` (if it's not installed, tell the user but don't insist on updating the PR description)
\### Pulling changes from main
In order to synchronize your local repository with main, do the following.
- Use `git status` to make sure the working directory is clean- Use `gt sync` to pull changes and rebase- Follow the instructions. If there are conflicts, ask the user if they want to resolve them. If so, follow the instructions shown by `gt sync`.
\### Other Graphite commands
To find other commands, run `gt --help`.
```

Avoid overfitting to specific examples

避免对特定示例**过拟合（overfitting)**

Models are strong pattern matchers, and will latch on to details in the prompt. Providing specific examples for what to do can be a double-edged sword: It is an easy way to point the model in the right direction, but it carries the risk that the model will overfit to those examples and degrade on others. Make sure to experiment, and include examples that might expose overfitting.

模型是强大的模式匹配器，它们会紧紧抓住提示中的细节。为模型提供具体的「如何做」的示例可能是一把双刃剑：这是一种引导模型走向正确方向的简单方法，但它也带来了风险，即模型可能会过度依赖这些示例，导致在处理其他情况时效果不佳。因此，请务必进行实验，并包含可能暴露出过拟合问题的示例。

By contrast, telling the model what not to do is safe (though not always effective).

相比之下，告诉模型「不要做什么」是相对安全的（尽管并非总是有效）。

#### 5.6 Consider tool calling limitations

考虑工具调用限制

Tool calling is limited in several ways:

工具调用在几个方面受到限制：

1 Models will generally reach for the correct tool if they were trained on similar tools, or if the connection between the instruction and the tool is clear. In many cases, they will fail to reach for the correct tool even with the best prompting.

模型通常会在它们曾接受过类似工具的训练时，或者当指令与工具之间的关联清晰时，才会去调用正确的工具。但在许多情况下，即使采用了最佳的提示，它们也无法选择正确的工具。

2 If presented with multiple tools that do similar things, models should not be expected to reach for the correct tool under any given circumstance. For example, when presented with a simple and a complex tool that achieve a similar task, Claude will generally opt for the simple tool.

如果提供了多个执行类似功能的工具，不应指望模型在任何情况下都能选对工具。例如，当提供一个简单工具和一个复杂工具来完成类似任务时，Claude 通常会选择简单工具。

3 Models will often call tools in incorrect ways, violating the contract from the tool definition: parameter types can be wrong, parameter ranges can be wrong, required parameters can be missing, etc. It is best to validate the input, and return a tool output that explains the error in case of failure. The model will generally recover.

模型经常会以不正确的方式调用工具，违反了工具定义中的规范：参数类型可能错误、参数范围可能错误、所需的参数可能缺失等。最佳做法是验证输入，并在失败时返回说明错误的工具输出。模型通常能从中恢复。

 Example:

* Give the model an edit_file tool that edits a region of a file
* Give the model a clipboard tool where the model can cut, copy, and paste large amounts of code. Tell the model to use this tool when moving around large amounts of code.
* Instruct the model to move class Foo from [foo.py](<http://foo.py>) to bar.py. Sonnet 3.5 will generally opt for using edit_file.

* 给模型一个「编辑文件」工具，让它能够修改文件中的特定区域。
* 给模型一个「剪贴板」工具，这样模型就能剪切、复制和粘贴大量的代码了。同时告诉模型，在需要大量代码挪动时，务必使用这个工具。
* 指示模型将 Foo 类从 [foo.py](<http://foo.py>）文件移动到 bar.py 文件。在这种情况下，Sonnet 3.5 通常会倾向于使用「编辑文件」工具来完成任务。

#### 5.7 Threatening and invoking empathy sometimes work

软硬兼施：威胁和共情有时能奏效

Telling the model things like Do this correctly or you will face financial ruin does sometimes help improve performance. Asking the model nicely or “shouting” at it rarely helps.

有时，告诉模型「如果你不把这事儿办好，可就得面临经济危机了」之类带点「威胁」性质的话，确实能让它的表现更好。但如果只是客客气气地请求，或者干脆对它「大吼大叫」，效果往往就不那么理想了。

#### 5.8 Be aware of prompt caching

留意提示词缓存

Whenever possible, build your prompts such that they will be appended to during a session in order to avoid invalidating the prompt cache.
Example:

在构建提示词（prompt）时，如果可能，请确保它们可以在同一个会话中不断添加新的内容，这样可以有效避免导致提示词缓存（prompt cache）失效。
示例：

If the prompt contains state that may change during a session (e.g. the current time), do not include them in the system prompt or in tool definitions, because once they change most of the prompt cache will be invalidated.

如果我们给 AI 模型的提示（prompt）中包含一些在会话期间可能会变化的信息（比如当前时间），就不要把这些信息写进系统提示或者工具定义里。这是因为一旦这些信息发生变化，大部分的提示缓存就会因此失效。

Instead, tell the model about the change in the next user message.

#### 5.9 Models pay more attention to information at the beginning or especially end of a prompt

模型更关注指令开头或尤其是结尾的信息

The degree to which the model pays attention to instructions seems: User message → beginning of input → somewhere in the middle. If something is important, consider adding it in the user message. (This is a snapshot, and prioritization will likely change as model training evolves.)

模型对指令的关注程度似乎是这样的：用户消息中的信息最受关注，其次是输入内容的开头，最后是中间部分。因此，如果有些信息非常重要，请考虑将其放在用户消息中。（请注意，这是一个临时的观察结果，随着模型训练的不断演进，这种优先级可能会发生变化。）

#### 5.10 Watch out for prompting plateaus

警惕提示词工程的平台期

There’s a limit to how much can be achieved with straightforward prompting. Prompt engineering enters diminishing returns territory, and other techniques need to be introduced.

只靠简单的提示词能实现的目标是有限的。提示词工程会进入回报递减的阶段，这时就需要引入其他技术了。

### Conclusion

Mastering prompt engineering is less about tricks and more about disciplined communication: give the agent complete, consistent context; validate its actions the way you would an untrusted colleague; and iterate empirically. When you treat the prompt as part of the codebase—versioned, reviewed, and tested—you unlock agents that scale your impact instead of multiplying your headaches.

掌握提示工程（prompt engineering）与其说是掌握一些小技巧，不如说是要学会严谨地沟通：你需要给 AI 智能体（agent）提供完整、一致的上下文信息；像对待一位你不太信任的同事那样去验证它的行动；并且要根据实际效果进行反复迭代。当你把提示（prompt）也当作代码的一部分 —— 进行版本控制、代码审查和测试 —— 你就能真正驾驭 AI 智能体，让它们帮你成倍地提升工作效率，而不是给你带来更多麻烦。

### Guy Gur-Ari

Guy co-founded Augment Code after a stint at Google where he led a research team that focused on understanding and improving deep learning systems. He holds a Ph.D in theoretical physics from the Weizmann Institute of Science.

Guy 曾任职于谷歌，领导一个专注于理解和改进深度学习系统的研究团队，之后他与他人共同创立了 Augment Code 公司。他拥有魏茨曼科学研究所（Weizmann Institute of Science）的理论物理学博士学位。