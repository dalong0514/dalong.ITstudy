## 20250911Writing-effective-tools-for-AI-agents—using-AI-agents

[Writing effective tools for AI agents—using AI agents \ Anthropic](https://www.anthropic.com/engineering/writing-tools-for-agents)

[Engineering at Anthropic](https://www.anthropic.com/engineering)

Published Sep 11, 2025

Agents are only as effective as the tools we give them. We share how to write high-quality tools and evaluations, and how you can boost performance by using Claude to optimize its tools for itself.

智能体（Agent）的效率高低，完全取决于我们提供给它们的工具。本文将介绍如何编写高质量的工具和评估方法，以及如何利用 Claude 来优化其自身工具，从而显著提升性能。

The Model Context Protocol (MCP) can empower LLM agents with potentially hundreds of tools to solve real-world tasks. But how do we make those tools maximally effective?

模型上下文协议（Model Context Protocol，MCP）能够赋予大语言模型（Large Language Model，LLM）AI 智能体（AI Agent）多达数百种工具，以解决现实世界的任务。那么，我们该如何才能最大限度地发挥这些工具的效用呢？

In this post, we describe our most effective techniques for improving performance in a variety of agentic AI systems1.

在这篇文章中，我们将介绍我们在提升多种 AI 智能体（AI Agent）系统 1 性能方面，行之有效且卓有成效的技术。

We begin by covering how you can:

首先，我们会从以下几个方面为您讲解：

1 Build and test prototypes of your tools

构建并测试你所开发工具的原型

2 Create and run comprehensive evaluations of your tools with agents

开展并执行使用 AI 智能体（AI Agent）对你工具的全面评估

3 Collaborate with agents like Claude Code to automatically increase the performance of your tools

与 Claude Code 这样的 AI 智能体（AI Agent）协作，来自动提升您工具的性能。

We conclude with key principles for writing high-quality tools we've identified along the way:

最后，我们总结了在研究过程中发现的、编写高质量工具的关键原则：

1 Choosing the right tools to implement (and not to implement)

选择正确的工具，决定哪些需要实施，哪些不需要实施

2 Namespacing tools to define clear boundaries in functionality

对工具进行命名空间（Namespacing）划分，从而明确它们各自的功能边界

3 Returning meaningful context from tools back to agents

将有意义的上下文从工具返回给 AI 智能体（AI Agent）

4 Optimizing tool responses for token efficiency

优化工具响应，以提升 Token 利用效率

5 Prompt-engineering tool descriptions and specs

提示工程（Prompt-engineering）工具描述和规格

Building an evaluation allows you to systematically measure the performance of your tools. You can use Claude Code to automatically optimize your tools against this evaluation. 

建立评估可以帮助你系统地衡量工具的性能。你可以使用 Claude Code，根据这些评估来自动优化你的工具。

### 01. What is a tool?

什么是工具？

In computing, deterministic systems produce the same output every time given identical inputs, while non-deterministic systems—like agents—can generate varied responses even with the same starting conditions.

在计算领域，确定性系统在给定相同输入的情况下，每次都会产生相同的输出；而非确定性系统 —— 比如 AI 智能体（AI Agent）—— 即使在相同的初始条件下，也能生成不同的响应。

When we traditionally write software, we're establishing a contract between deterministic systems. For instance, a function call like getWeather("NYC") will always fetch the weather in New York City in the exact same manner every time it is called.

在传统的软件开发中，我们其实是在确定一套确定性系统（deterministic systems）之间的「契约」关系。举个例子，一个像 getWeather（"NYC"）这样的函数调用，无论何时被执行，都将以完全相同的方式获取纽约市的天气数据。

Tools are a new kind of software which reflects a contract between deterministic systems and non-deterministic agents. When a user asks "Should I bring an umbrella today?," an agent might call the weather tool, answer from general knowledge, or even ask a clarifying question about location first. Occasionally, an agent might hallucinate or even fail to grasp how to use a tool.

工具是一种新型软件，它代表着确定性系统和非确定性 AI 智能体（AI Agent）之间的一种协议或协同关系。当用户问道：「我今天应该带伞吗？」时，AI 智能体可能会调用天气工具来回答，也可能根据自身的常识来作答，甚至会先询问用户的位置以澄清问题。偶尔，AI 智能体可能会产生幻觉（hallucinate），甚至无法理解如何正确使用工具。

This means fundamentally rethinking our approach when writing software for agents: instead of writing tools and MCP servers the way we'd write functions and APIs for other developers or systems, we need to design them for agents.

这意味着，当我们要为 AI 智能体（AI agent）编写软件时，必须从根本上重新思考我们的方法：我们不能再像为其他开发人员或系统编写函数和 API 那样去编写工具和 MCP 服务器，而是需要专门为 AI 智能体来设计它们。

Our goal is to increase the surface area over which agents can be effective in solving a wide range of tasks by using tools to pursue a variety of successful strategies. Fortunately, in our experience, the tools that are most "ergonomic" for agents also end up being surprisingly intuitive to grasp as humans.

我们的目标是扩大 AI 智能体（AI Agent）在解决各类任务时的有效应用范围。我们希望通过让它们运用工具来执行多种成功的策略，实现这一目标。
幸运的是，根据我们的经验，那些对 AI 智能体来说最「顺手」（即设计得最适合它们）的工具，对人类而言也出乎意料地直观易懂，方便掌握。

### 02. How to write tools

如何编写工具

In this section, we describe how you can collaborate with agents both to write and to improve the tools you give them. Start by standing up a quick prototype of your tools and testing them locally. Next, run a comprehensive evaluation to measure subsequent changes. Working alongside agents, you can repeat the process of evaluating and improving your tools until your agents achieve strong performance on real-world tasks.

在本节中，我们将介绍你如何与 AI 智能体（AI agents）协作，共同编写并改进提供给它们的工具。首先，你需要快速开发工具原型，并在本地进行测试。接着，进行一次全面的评估，以衡量每次改进带来的变化。通过与 AI 智能体（AI agents）紧密合作，你可以不断重复评估和改进工具的过程，直到它们在实际任务中展现出卓越的性能。

#### 2.1 Building a prototype

动手搭建原型

It can be difficult to anticipate which tools agents will find ergonomic and which tools they won't without getting hands-on yourself. Start by standing up a quick prototype of your tools. If you're using Claude Code to write your tools (potentially in one-shot), it helps to give Claude documentation for any software libraries, APIs, or SDKs (including potentially the MCP SDK) your tools will rely on. LLM-friendly documentation can commonly be found in flat llms.txt files on official documentation sites (here's our API's).

如果不亲自动手体验，你很难预判 AI 智能体（AI Agent）会觉得哪些工具好用（符合人体工程学（ergonomic）），哪些又不好用。所以，不妨先快速搭建一个你工具的初步原型。如果你使用 Claude Code 来编写工具（可能是一次性完成），那么向 Claude 提供你的工具将依赖的软件库、API 或 SDK（包括可能的 MCP SDK）的文档，会非常有帮助。对大语言模型（Large Language Model，LLM）友好的文档通常可以在官方文档网站上以简单的 llms.txt 文本文件形式找到（比如我们 API 的文档就是如此）。

Wrapping your tools in a local MCP server or Desktop extension (DXT) will allow you to connect and test your tools in Claude Code or the Claude Desktop app.

将你的工具封装在本地 MCP 服务器或桌面扩展（Desktop extension，DXT）中，你就可以在 Claude Code 或 Claude 桌面应用程序中连接并测试这些工具。

To connect your local MCP server to Claude Code, run claude mcp add <name> <command> [args...].

要将你的本地 MCP 服务器连接到 Claude Code，请运行 `claude mcp add <name> <command> [args...]` 命令。

To connect your local MCP server or DXT to the Claude Desktop app, navigate to Settings > Developer or Settings > Extensions, respectively.

为了将你的本地 MCP 服务器或 DXT 连接到 Claude 桌面应用（Claude Desktop app），你需要分别前往「设置> 开发者」或「设置> 扩展」界面。

Tools can also be passed directly into Anthropic API calls for programmatic testing.

此外，工具也可以直接通过 Anthropic API 调用传入，以便进行程序化测试（programmatic testing）。

Test the tools yourself to identify any rough edges. Collect feedback from your users to build an intuition around the use-cases and prompts you expect your tools to enable.

请您亲自测试这些工具，找出它们可能存在的任何不足之处。同时，也要收集用户的反馈，以便您能更好地理解这些工具预计能支持哪些应用场景和提示词，从而形成更直观的判断。

#### 2.2 Running an evaluation

运行评估

Next, you need to measure how well Claude uses your tools by running an evaluation. Start by generating lots of evaluation tasks, grounded in real world uses. We recommend collaborating with an agent to help analyze your results and determine how to improve your tools. See this process end-to-end in our tool evaluation cookbook.

接下来，你需要通过进行评估来衡量 Claude 使用你的工具的效果。首先，请基于真实世界的应用场景，生成大量的评估任务。我们建议与一个 AI 智能体（AI Agent）协作，以帮助分析你的评估结果，并确定如何改进你的工具。有关此过程的端到端详情，请参阅我们的工具评估指南。

[anthropic-cookbook/tool\_evaluation/tool\_evaluation.ipynb at main · anthropics/anthropic-cookbook](https://github.com/anthropics/anthropic-cookbook/blob/main/tool_evaluation/tool_evaluation.ipynb)

Held-out test set performance of our internal Slack tools 

我们内部 Slack 工具的保留测试集性能：

#### 2.3 Generating evaluation tasks

生成评估任务

With your early prototype, Claude Code can quickly explore your tools and create dozens of prompt and response pairs. Prompts should be inspired by real-world uses and be based on realistic data sources and services (for example, internal knowledge bases and microservices). We recommend you avoid overly simplistic or superficial "sandbox" environments that don't stress-test your tools with sufficient complexity. Strong evaluation tasks might require multiple tool calls—potentially dozens.

有了你的早期原型，Claude Code 可以快速探索你的工具，并创建数十个提示（prompt）和响应（response）对。这些提示应该源于实际使用场景，并基于真实的数据源和服务（例如，内部知识库和微服务）来设计。我们建议你避免使用过于简单或流于表面的「沙盒」环境，因为它们无法通过足够的复杂度来对你的工具进行压力测试。有效的评估任务可能需要进行多次工具调用，甚至多达数十次。

Here are some examples of strong tasks:

以下是一些复杂任务的例子：

1 Schedule a meeting with Jane next week to discuss our latest Acme Corp project. Attach the notes from our last project planning meeting and reserve a conference room.

下周和 Jane 安排一个会议，讨论我们最新的 Acme Corp 项目。任务包括附上我们上次项目规划会议的记录，并预订一间会议室。

2 Customer ID 9182 reported that they were charged three times for a single purchase attempt. Find all relevant log entries and determine if any other customers were affected by the same issue.

客户 ID 9182 报告称，他们在一次购买尝试中被重复收取了三次费用。请找出所有相关的日志条目，并确定是否有其他客户也受到了同样问题的影响。

3 Customer Sarah Chen just submitted a cancellation request. Prepare a retention offer. Determine: (1) why they're leaving, (2) what retention offer would be most compelling, and (3) any risk factors we should be aware of before making an offer.

客户 Sarah Chen 刚刚提交了一份取消请求。请准备一份挽留优惠方案。需要确定以下三点：（1）客户离开的原因是什么，（2）哪种挽留方案最能打动客户，以及（3）在提供方案之前，我们需要警惕哪些风险。

And here are some weaker tasks:

以下是一些更简单的任务：

1 Schedule a meeting with jane@acme.corp next week.

下周与 jane@acme.corp 安排一次会议。

2 Search the payment logs for purchase_complete and customer_id=9182.

搜索支付日志，查找购买完成的记录以及客户 ID 为 9182 的记录。

3 Find the cancellation request by Customer ID 45892.

查找客户 ID 45892 提交的取消请求。

Each evaluation prompt should be paired with a verifiable response or outcome. Your verifier can be as simple as an exact string comparison between ground truth and sampled responses, or as advanced as enlisting Claude to judge the response. Avoid overly strict verifiers that reject correct responses due to spurious differences like formatting, punctuation, or valid alternative phrasings.

每个评估提示（evaluation prompt）都应该对应一个可验证的响应（verifiable response）或结果。你的验证器（verifier）可以很简单，例如对「标准答案（ground truth）」和「模型生成响应（sampled responses）」进行精确的字符串比对；也可以很高级，比如请 Claude 来判断响应。我们应该避免使用过于严格的验证器，它们可能会因为格式、标点符号或其他有效的表达方式（alternative phrasings）等表面上的差异（spurious differences），而错误地拒绝正确的响应。

For each prompt-response pair, you can optionally also specify the tools you expect an agent to call in solving the task, to measure whether or not agents are successful in grasping each tool's purpose during evaluation. However, because there might be multiple valid paths to solving tasks correctly, try to avoid overspecifying or overfitting to strategies.

对于每个提示 - 响应对，你还可以选择性地指定你期望一个 AI 智能体（AI Agent）在解决任务时调用的工具，目的是衡量 AI 智能体（AI Agent）在评估期间是否成功理解并正确使用每个工具的用途。然而，由于解决任务可能存在多种有效路径，请尽量避免过度指定或过度限制其策略。

#### 2.4 Running the evaluation

We recommend running your evaluation programmatically with direct LLM API calls. Use simple agentic loops (while-loops wrapping alternating LLM API and tool calls): one loop for each evaluation task. Each evaluation agent should be given a single task prompt and your tools.

运行评估我们建议通过直接调用大语言模型（Large Language Model，LLM）的 API（Application Programming Interface），以编程方式（即通过编写程序）来运行您的评估。可以使用简单的智能体循环（即通过 while 循环封装交替进行的大语言模型 API 调用和工具调用）：每个评估任务对应一个循环。每个评估智能体（AI Agent）都应该被赋予一个任务提示（Task Prompt）和你提供的工具。

In your evaluation agents' system prompts, we recommend instructing agents to output not just structured response blocks (for verification), but also reasoning and feedback blocks. Instructing agents to output these before tool call and response blocks may increase LLMs' effective intelligence by triggering chain-of-thought (CoT) behaviors.

在为评估智能体（evaluation agents）设置系统提示（system prompts）时，我们建议智能体不仅输出结构化响应块（structured response blocks）（用于验证），还应输出推理和反馈块（reasoning and feedback blocks）。如果让智能体在进行工具调用（tool call）和输出响应块（response blocks）之前就输出这些信息，可能会通过触发思维链（Chain-of-Thought，CoT）推理过程，从而提高大语言模型（LLMs）的实际智能水平。

If you're running your evaluation with Claude, you can turn on interleaved thinking for similar functionality "off-the-shelf". This will help you probe why agents do or don't call certain tools and highlight specific areas of improvement in tool descriptions and specs.

如果你在使用 Claude 进行评估，可以开启交错思考（interleaved thinking）功能，从而「开箱即用」地获得类似的效果。这将帮助你深入了解 AI 智能体（AI agents）调用或不调用某些工具的原因，并能发现工具描述和规范中需要改进的具体地方。

As well as top-level accuracy, we recommend collecting other metrics like the total runtime of individual tool calls and tasks, the total number of tool calls, the total token consumption, and tool errors. Tracking tool calls can help reveal common workflows that agents pursue and offer some opportunities for tools to consolidate.

除了关注模型最高的准确率，我们还建议收集其他一些关键指标，例如：单个工具调用和任务的总运行时间、工具调用的总次数、总 Token（Token）消耗以及工具错误。跟踪工具调用（tool calls）有助于揭示 AI 智能体（AI Agent）通常采用的工作流程，并为整合工具提供了一些机会。

Held-out test set performance of our internal Asana tools

我们内部 Asana 工具在独立测试集上的性能表现

#### 2.5 Analyzing results

分析结果

Agents are your helpful partners in spotting issues and providing feedback on everything from contradictory tool descriptions to inefficient tool implementations and confusing tool schemas. However, keep in mind that what agents omit in their feedback and responses can often be more important than what they include. LLMs don't always say what they mean.

AI 智能体（AI Agent）是您发现问题和提供反馈的得力助手，它们能就各种情况提供帮助，包括：相互矛盾的工具描述、低效的工具实现方式，以及令人困惑的工具架构。然而，请记住，AI 智能体在其反馈和回应中「省略了什么」，往往比它们「包含了什么」更为重要。因为大语言模型（LLM）并不总是直接表达其真实意图。

Observe where your agents get stumped or confused. Read through your evaluation agents' reasoning and feedback (or CoT) to identify rough edges. Review the raw transcripts (including tool calls and tool responses) to catch any behavior not explicitly described in the agent's CoT. Read between the lines; remember that your evaluation agents don't necessarily know the correct answers and strategies.

观察你的 AI 智能体（AI Agent）在哪里卡壳或感到困惑。仔细阅读评估 AI 智能体的推理和反馈（或思维链，CoT），以便找出其不足之处。审查原始交互记录（包括工具调用和工具响应），以发现 AI 智能体思维链（CoT）中没有明确提及的任何行为。要学会透过字里行间领会言外之意；请记住，你的评估 AI 智能体不一定知道正确的答案和策略。

Analyze your tool calling metrics. Lots of redundant tool calls might suggest some rightsizing of pagination or token limit parameters is warranted; lots of tool errors for invalid parameters might suggest tools could use clearer descriptions or better examples. When we launched Claude's web search tool, we identified that Claude was needlessly appending 2025 to the tool's query parameter, biasing search results and degrading performance (we steered Claude in the right direction by improving the tool description).

分析你的工具调用指标（tool calling metrics）。大量的冗余工具调用（redundant tool calls）可能表明有必要对分页或 token 限制参数进行一些优化调整；而大量因参数无效导致的工具错误，则可能说明工具的描述不够清晰或缺乏足够好的示例。当我们推出 Claude 的网页搜索工具时，我们曾发现 Claude 不必要地将「2025」附加到工具的查询参数中，这不仅导致搜索结果出现偏差，也降低了性能。我们通过改进工具描述，成功地引导 Claude 走向了正确的方向。

#### 2.6 Collaborating with agents

与 AI 智能体协作

You can even let agents analyze your results and improve your tools for you. Simply concatenate the transcripts from your evaluation agents and paste them into Claude Code. Claude is an expert at analyzing transcripts and refactoring lots of tools all at once—for example, to ensure tool implementations and descriptions remain self-consistent when new changes are made.

你甚至可以放心地让智能体（agents）帮你分析结果并改进你的工具。只需将你的评估智能体生成的对话记录串联起来，然后将其粘贴到 Claude Code 中。Claude 擅长分析这些记录，并能一次性重构大量工具 —— 例如，确保在进行新的修改时，工具的实现和描述能保持内部一致性（self-consistent）。

In fact, most of the advice in this post came from repeatedly optimizing our internal tool implementations with Claude Code. Our evaluations were created on top of our internal workspace, mirroring the complexity of our internal workflows, including real projects, documents, and messages.

事实上，这篇帖子中的大部分建议都源于我们利用 Claude Code 反复优化内部工具的实践。我们进行评估时，是基于内部工作区展开的，这很好地模拟了我们实际工作流程的复杂性，其中包含了真实的项目、文档和消息。

We relied on held-out test sets to ensure we did not overfit to our "training" evaluations. These test sets revealed that we could extract additional performance improvements even beyond what we achieved with "expert" tool implementations—whether those tools were manually written by our researchers or generated by Claude itself.

我们依赖于独立的测试集，以确保我们没有对「训练」评估结果出现过度拟合（overfit）的情况。这些测试集表明，即使是与通过「专家」级的工具实现（tool implementations）所获得的性能相比 —— 无论这些工具是我们研究人员手动编写的，还是由 Claude 自己生成的 —— 我们都能够进一步提升性能。

In the next section, we'll share some of what we learned from this process.

在下一节中，我们将分享从这个过程中积累的一些经验。

### 03. Principles for writing effective tools

编写高效工具的原则

In this section, we distill our learnings into a few guiding principles for writing effective tools.

#### Choosing the right tools for agents

在本节中，我们将我们的经验提炼成一些设计高效工具的指导原则。

为 AI 智能体（AI Agent）选择合适的工具

More tools don't always lead to better outcomes. A common error we've observed is tools that merely wrap existing software functionality or API endpoints—whether or not the tools are appropriate for agents. This is because agents have distinct "affordances" to traditional software—that is, they have different ways of perceiving the potential actions they can take with those tools

工具越多，不一定总能带来更好的效果。我们观察到一个常见的误区是，有些工具仅仅是现有软件功能或 API 接口的简单封装，而没有考虑这些工具是否真正适合 AI 智能体（AI Agent）。这是因为 AI 智能体与传统软件在「可供性（affordances）」上有所不同 —— 也就是说，它们对于如何利用这些工具来执行潜在行动，有着截然不同的理解方式。

LLM agents have limited "context" (that is, there are limits to how much information they can process at once), whereas computer memory is cheap and abundant. Consider the task of searching for a contact in an address book. Traditional software programs can efficiently store and process a list of contacts one at a time, checking each one before moving on.

大语言模型（Large Language Model）智能体（AI Agent）的「上下文」能力有限（这意味着它们一次能够处理的信息量是有限的），而计算机内存则既便宜又充足。举个例子，假设我们需要在地址簿中搜索一个联系人。传统的软件程序可以高效地存储并逐一处理联系人列表，在检查完每一个联系人之后再继续下一步。

However, if an LLM agent uses a tool that returns ALL contacts and then has to read through each one token-by-token, it's wasting its limited context space on irrelevant information (imagine searching for a contact in your address book by reading each page from top-to-bottom—that is, via brute-force search). The better and more natural approach (for agents and humans alike) is to skip to the relevant page first (perhaps finding it alphabetically).

然而，如果一个大语言模型（LLM）驱动的 AI 智能体使用一个工具，该工具返回所有联系人，然后它必须逐 Token 地阅读每一个联系人，那么它就会将其有限的上下文空间浪费在不相关的信息上 （想象一下你在地址簿中查找联系人，却要从头到尾一页一页地翻阅 —— 这就像是暴力搜索）。对于 AI 智能体和人类来说，更好、更自然的做法是先直接跳转到相关页面 （比如按字母顺序查找）。

We recommend building a few thoughtful tools targeting specific high-impact workflows, which match your evaluation tasks and scaling up from there. In the address book case, you might choose to implement a search_contacts or message_contact tool instead of a list_contacts tool.

我们建议，可以先开发一些经过深思熟虑的工具，这些工具应针对特定且影响力大的工作流程，并且要与您的评估任务相匹配。然后，再以此为基础逐步扩展。以通讯录为例，您或许会选择开发一个用于「搜索联系人」（search_contacts）或「发送消息给联系人」（message_contact）的工具，而不是一个仅仅「列出所有联系人」（list_contacts）的工具。

Tools can consolidate functionality, handling potentially multiple discrete operations (or API calls) under the hood. For example, tools can enrich tool responses with related metadata or handle frequently chained, multi-step tasks in a single tool call.

工具可以整合各种功能，在后台处理多个独立的（或一系列的 API ）调用。例如，工具可以用相关的元数据丰富其响应，或者在一个工具调用中，就能处理那些经常需要连续执行的、多步骤的任务。

Here are some examples:

* Instead of implementing a list_users, list_events, and create_event tools, consider implementing a schedule_event tool which finds availability and schedules an event.

与其分别实现「列出用户（list_users）」、「列出事件（list_events）」和「创建事件（create_event）」这些工具，不如考虑实现一个「日程事件（schedule_event）」工具，它能自动查找空闲时间并安排事件。

* Instead of implementing a read_logs tool, consider implementing a search_logs tool which only returns relevant log lines and some surrounding context.

* Instead of implementing get_customer_by_id, list_transactions, and list_notes tools, implement a get_customer_context tool which compiles all of a customer's recent & relevant information all at once.

*  与其实现一个名为 `read_logs` 的工具，不如考虑实现一个名为 `search_logs` 的工具。后者仅返回相关的日志行以及它们的一些周边上下文信息。

*  与其分别实现 `get_customer_by_id`、`list_transactions` 和 `list_notes` 等工具，不如实现一个名为 `get_customer_context` 的工具。这个工具能够一次性汇集所有客户近期和相关的信息。

Make sure each tool you build has a clear, distinct purpose. Tools should enable agents to subdivide and solve tasks in much the same way that a human would, given access to the same underlying resources, and simultaneously reduce the context that would have otherwise been consumed by intermediate outputs.

请确保你开发的每个工具都有清晰、独特的功能。这些工具应该能够让 AI 智能体（AI agents）像人类一样，在获取相同底层资源的前提下，对任务进行细分并加以解决。同时，它们还能减少那些原本会被中间输出结果占用的上下文信息。

Too many tools or overlapping tools can also distract agents from pursuing efficient strategies. Careful, selective planning of the tools you build (or don't build) can really pay off.

工具过多或功能重叠，也可能让 AI 智能体（AI Agent）分心，难以采取高效的策略。因此，对于你要构建（或不构建）哪些工具进行审慎且有选择性的规划，将会带来丰厚的回报。

#### Namespacing your tools

Your AI agents will potentially gain access to dozens of MCP servers and hundreds of different tools–including those by other developers. When tools overlap in function or have a vague purpose, agents can get confused about which ones to use.

给你的工具做命名空间管理你的 AI 智能体（AI agents）未来可能会连接到几十台 MCP 服务器，并使用数百种不同的工具 —— 其中也包括其他开发者开发的工具。当这些工具的功能有所重叠，或者其用途不够明确时，智能体（agents）就很难判断该使用哪一个了。

Namespacing (grouping related tools under common prefixes) can help delineate boundaries between lots of tools; MCP clients sometimes do this by default. For example, namespacing tools by service (e.g., asana_search, jira_search) and by resource (e.g., asana_projects_search, asana_users_search), can help agents select the right tools at the right time.

使用命名空间（即将相关工具归类到共同的前缀下）有助于明确区分众多工具的功能范围；MCP 客户端有时会默认采用这种方式。例如，如果根据服务（比如 `asana_search`、`jira_search`）和资源（比如 `asana_projects_search`、`asana_users_search`）来划分工具的命名空间，就能帮助 AI 智能体（AI Agent）在恰当的时机选择最合适的工具。

We have found selecting between prefix- and suffix-based namespacing to have non-trivial effects on our tool-use evaluations. Effects vary by LLM and we encourage you to choose a naming scheme according to your own evaluations.

我们发现，在选择前缀式还是后缀式命名空间时，会对我们的工具使用评估产生不容忽视的影响。这种影响会因不同的大语言模型（Large Language Model）而有所不同，因此我们鼓励您根据自己的评估结果来选择合适的命名方案。

Agents might call the wrong tools, call the right tools with the wrong parameters, call too few tools, or process tool responses incorrectly. By selectively implementing tools whose names reflect natural subdivisions of tasks, you simultaneously reduce the number of tools and tool descriptions loaded into the agent's context and offload agentic computation from the agent's context back into the tool calls themselves. This reduces an agent's overall risk of making mistakes.

AI 智能体（AI Agent）在工作中可能会遇到各种问题：它们可能会选择错误的工具，即使选对了工具也可能传入不正确的参数，或者调用的工具数量不足，甚至会错误地处理工具返回的结果。为了解决这些问题，我们可以有选择地设计工具，让这些工具的名称能直接反映任务的自然子环节。这样做的好处是多方面的：一方面，你可以减少加载到智能体上下文中的工具数量和工具描述；另一方面，也能将原本由智能体自身在上下文中进行的决策计算（即「智能体计算」）转移到工具调用本身去完成。这种方法能有效降低智能体整体出错的风险。

#### Returning meaningful context from your tools

In the same vein, tool implementations should take care to return only high signal information back to agents. They should prioritize contextual relevance over flexibility, and eschew low-level technical identifiers (for example: uuid, 256px_image_url, mime_type). Fields like name, image_url, and file_type are much more likely to directly inform agents' downstream actions and responses.

让你的工具返回更有意义的上下文信息同样地，工具在设计和实现时，应确保只返回高价值信息给 AI 智能体（AI Agent）。在返回信息时，应优先考虑其与上下文的相关性，而非一味追求灵活性；同时，应避免返回低级的技术标识符 （例如：uuid，256px_image_url，mime_type）。像 name、image_url 和 file_type 这样的字段，更有可能直接为 AI 智能体的后续行动和响应提供有效信息。

Agents also tend to grapple with natural language names, terms, or identifiers significantly more successfully than they do with cryptic identifiers. We've found that merely resolving arbitrary alphanumeric UUIDs to more semantically meaningful and interpretable language (or even a 0-indexed ID scheme) significantly improves Claude's precision in retrieval tasks by reducing hallucinations.

AI 智能体（AI Agents）在处理自然语言名称、术语或标识符时，也比处理那些晦涩难懂的标识符要成功得多。我们发现，仅仅是将任意的字母数字型 UUID 转换为语义上更有意义、更容易理解的语言（或者，哪怕是采用一个从 0 开始的索引 ID 方案），也能显著提高 Claude 在检索任务中的准确性，原因就在于这样能有效减少 AI 的「幻觉（hallucinations）」现象。

In some instances, agents may require the flexibility to interact with both natural language and technical identifiers outputs, if only to trigger downstream tool calls (for example, search_user(name='jane') → send_message(id=12345)). You can enable both by exposing a simple response_format enum parameter in your tool, allowing your agent to control whether tools return "concise" or "detailed" responses (images below).

在某些情况下，AI 智能体（AI Agent）可能需要能够灵活地与自然语言（natural language）和技术标识符（technical identifiers）输出进行交互，哪怕只是为了触发下游工具调用（downstream tool calls）(例如，search_user（name='jane'）→ send_message（id=12345））。您可以通过在工具中提供一个简单的 `response_format` 枚举参数（enum parameter）来实现这两种功能，从而允许您的 AI 智能体控制工具返回「简洁」还是「详细」的响应（具体请看下图）。

You can add more formats for even greater flexibility, similar to GraphQL where you can choose exactly which pieces of information you want to receive. Here is an example ResponseFormat enum to control tool response verbosity:

你可以添加更多格式，以获得更大的灵活性，这类似于 GraphQL，在那里你可以精确地选择想要接收哪些具体信息。以下是一个控制工具响应详细程度的 ResponseFormat 枚举示例：

```
enum ResponseFormat {
 DETAILED = "detailed",
 CONCISE = "concise"
}
```

Here's an example of a detailed tool response (206 tokens):

Here's an example of a concise tool response (72 tokens):

以下是一个详细的工具响应示例（206 个 Token):

以下是一个简洁的工具响应示例（72 个 Token）:

Slack threads and thread replies are identified by unique `thread_ts`which are required to fetch thread replies. `thread_ts`and other IDs ( `channel_id`, `user_id`) can be retrieved from a `"detailed"`tool response to enable further tool calls that require these. `"concise"`tool responses return only thread content and exclude IDs. In this example, we use ~⅓ of the tokens with `"concise"`tool responses. 

Even your tool response structure—for example XML, JSON, or Markdown—can have an impact on evaluation performance: there is no one-size-fits-all solution. This is because LLMs are trained on next-token prediction and tend to perform better with formats that match their training data. The optimal response structure will vary widely by task and agent. We encourage you to select the best response structure based on your own evaluation.

Slack 的话题串及其回复都通过一个独特的 `thread_ts` 来识别，这个 `thread_ts` 是获取话题串回复的关键。像 `thread_ts` 这样的 ID（包括 `channel_id` 和 `user_id`）可以从一个 `"detailed"` 工具响应（tool response）中获取，从而能够进行需要这些 ID 的后续工具调用。相比之下，`"concise"` 工具响应只会返回话题串内容，不包含这些 ID。在这个例子中，使用 `"concise"` 工具响应大约能节省 ⅓ 的 token。

不仅如此，你的工具响应结构 —— 比如 XML、JSON 或 Markdown—— 也可能对评估性能产生影响：因为没有一种结构是万能的。这是因为大语言模型（Large Language Model）是基于下一词元预测（next-token prediction）训练的，它们往往在遇到与训练数据相匹配的格式时表现更出色。最佳的响应结构会因任务和 AI 智能体（AI Agent）的不同而有很大差异。我们建议你根据自己的评估来选择最合适的响应结构。

#### Optimizing tool responses for token efficiency

Optimizing the quality of context is important. But so is optimizing the quantity of context returned back to agents in tool responses.

优化工具响应的 Token 效率（Token efficiency）

优化上下文（context）的质量固然重要，但同样关键的是，要优化工具响应（tool responses）中返回给 AI 智能体（AI Agent）的上下文数量。

We suggest implementing some combination of pagination, range selection, filtering, and/or truncation with sensible default parameter values for any tool responses that could use up lots of context. For Claude Code, we restrict tool responses to 25,000 tokens by default. We expect the effective context length of agents to grow over time, but the need for context-efficient tools to remain.

我们建议，对于任何可能占用大量上下文（context）的工具响应，应采取分页、范围选择、过滤和 / 或截断等多种策略的组合，并设定合理的默认参数值。例如，对于 Claude Code，我们默认将工具响应限制在 25,000 个 Token 以内。我们预计 AI 智能体（agents）的有效上下文长度将随时间增长，但对上下文高效工具的需求仍将持续存在。

If you choose to truncate responses, be sure to steer agents with helpful instructions. You can directly encourage agents to pursue more token-efficient strategies, like making many small and targeted searches instead of a single, broad search for a knowledge retrieval task. Similarly, if a tool call raises an error (for example, during input validation), you can prompt-engineer your error responses to clearly communicate specific and actionable improvements, rather than opaque error codes or tracebacks.

如果您选择截断响应，请务必通过有用的指令来指导 AI 智能体（AI Agent）。您可以直接鼓励 AI 智能体（AI Agent）采取更节省 Token 的策略，例如进行多次小型、有针对性的搜索，而不是针对知识检索任务进行一次性、广泛的搜索。同样，如果一个工具调用引发错误（例如，在输入验证期间），您可以通过提示工程（prompt-engineer）的方式来设计错误响应，以便清晰地传达具体且可操作的改进建议，而不是仅仅显示晦涩难懂的错误代码或堆栈跟踪（tracebacks）。

Here's an example of a truncated tool response:

Here's an example of an unhelpful error response:

这是一个被截断的工具响应示例：

这是一个没有帮助的错误响应示例：

Here's an example of a helpful error response:

Tool truncation and error responses can steer agents towards more token-efficient tool-use behaviors (using filters or pagination) or give examples of correctly formatted tool inputs. ### Prompt-engineering your tool descriptions

这里有一个有益的错误响应的例子：

工具截断（Tool truncation）和错误响应（error responses）可以引导 AI 智能体（AI agent）采取更高效地利用 Token（Token）的工具使用行为（例如，使用过滤器或分页），或者给出格式正确的工具输入示例。### 提示工程（Prompt-engineering）你的工具描述

We now come to one of the most effective methods for improving tools: prompt-engineering your tool descriptions and specs. Because these are loaded into your agents' context, they can collectively steer agents toward effective tool-calling behaviors.

接下来，我们要探讨一种改进工具的有效方法：对工具的描述和规格进行提示工程（prompt-engineering）。由于这些信息会加载到 AI 智能体（AI Agent）的上下文中，它们能够协同引导 AI 智能体采取有效的工具调用行为。

When writing tool descriptions and specs, think of how you would describe your tool to a new hire on your team. Consider the context that you might implicitly bring—specialized query formats, definitions of niche terminology, relationships between underlying resources—and make it explicit. Avoid ambiguity by clearly describing (and enforcing with strict data models) expected inputs and outputs. In particular, input parameters should be unambiguously named: instead of a parameter named user, try a parameter named user_id.

在编写工具描述和规范时，请想象一下你会如何向团队里的新成员介绍你的工具。你可能会默认带入一些背景知识（例如专业查询格式、特定术语的定义以及底层资源之间的关系），请务必将其明确阐述出来。为了避免歧义，你需要清晰地描述预期的输入和输出，并通过严格的数据模型来强制执行这些规定。特别是在输入参数的命名上，务必做到明确无误：比如，不要使用名为 `user` 的参数，而是尝试使用名为 `user_id` 的参数。

With your evaluation you can measure the impact of your prompt engineering with greater confidence. Even small refinements to tool descriptions can yield dramatic improvements. Claude Sonnet 3.5 achieved state-of-the-art performance on the SWE-bench Verified evaluation after we made precise refinements to tool descriptions, dramatically reducing error rates and improving task completion.

有了你的评估，你就能更有信心地衡量自己的提示工程（prompt engineering）所产生的影响。即便只是对工具描述进行一些细微调整，也能带来显著的改进。在 SWE-bench Verified 评估中，Claude Sonnet 3.5 在我们对工具描述进行了精准优化后，实现了最先进的性能，显著降低了错误率，并提升了任务完成度。

You can find other best practices for tool definitions in our Developer Guide. If you're building tools for Claude, we also recommend reading about how tools are dynamically loaded into Claude's system prompt. Lastly, if you're writing tools for an MCP server, tool annotations help disclose which tools require open-world access or make destructive changes.

关于工具定义的其他最佳实践，你可以在我们的开发者指南中找到。如果你正在为 Claude 开发工具，我们还建议你了解工具是如何动态加载到 Claude 的系统提示中的。最后，如果你正在为 MCP 服务器编写工具，工具注释有助于说明哪些工具需要开放世界访问（open-world access）或会进行破坏性更改。

### 04. Looking ahead

展望未来

To build effective tools for agents, we need to re-orient our software development practices from predictable, deterministic patterns to non-deterministic ones.

为了给 AI 智能体（AI Agent）构建高效的工具，我们需要将软件开发实践从可预测、确定性的模式，转变为非确定性的模式。

Through the iterative, evaluation-driven process we've described in this post, we've identified consistent patterns in what makes tools successful: Effective tools are intentionally and clearly defined, use agent context judiciously, can be combined together in diverse workflows, and enable agents to intuitively solve real-world tasks.

通过我们在这篇文章中介绍的、以评估为驱动的迭代过程，我们发现了一些让工具成功的共通规律：有效的工具被刻意地、明确地设计，能够恰当地利用 AI 智能体（AI Agent）的上下文信息，可以在各种不同的工作流程中灵活组合使用，并能让 AI 智能体自然而然地解决现实世界中的任务。

In the future, we expect the specific mechanisms through which agents interact with the world to evolve—from updates to the MCP protocol to upgrades to the underlying LLMs themselves. With a systematic, evaluation-driven approach to improving tools for agents, we can ensure that as agents become more capable, the tools they use will evolve alongside them.

未来，我们预计 AI 智能体（AI Agent）与世界交互的具体机制将不断演变，这包括对 MCP 协议的更新，也包括对底层大语言模型（Large Language Model）本身的升级。通过采用系统化、以评估为导向的方法来改进智能体所使用的工具，我们可以确保，随着智能体的能力不断提升，它们所使用的工具也能同步演进。

## Acknowledgements

致谢

Written by Ken Aizawa with valuable contributions from colleagues across Research (Barry Zhang, Zachary Witten, Daniel Jiang, Sami Al-Sheikh, Matt Bell, Maggie Vo), MCP (Theodora Chu, John Welsh, David Soria Parra, Adam Jones), Product Engineering (Santiago Seira), Marketing (Molly Vorwerck), Design (Drew Roper), and Applied AI (Christian Ryan, Alexander Bricken).

本文由 Ken Aizawa 撰写，并获得了来自以下部门同事的宝贵贡献：研究部（Barry Zhang，Zachary Witten，Daniel Jiang，Sami Al-Sheikh，Matt Bell，Maggie Vo），MCP（Theodora Chu，John Welsh，David Soria Parra，Adam Jones），产品工程部（Santiago Seira），市场部（Molly Vorwerck），设计部（Drew Roper），以及应用 AI（Applied AI）部门（Christian Ryan，Alexander Bricken）。

1 Beyond training the underlying LLMs themselves.

1 除了训练底层大语言模型（LLMs）本身之外。