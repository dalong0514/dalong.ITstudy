## 20250617Dont-Build-Multi-Agents

[Cognition | Don’t Build Multi-Agents](https://cognition.ai/blog/dont-build-multi-agents#principles-of-context-engineering)

别再搭建多智能体系统了

Frameworks for LLM Agents have been surprisingly disappointing. I want to offer some principles for building agents based on our own trial & error，and explain why some tempting ideas are actually quite bad in practice.

大语言模型（LLM）智能体的框架一直以来都出乎意料地令人失望。我想根据我们团队的亲身试错经验，分享一些构建智能体的实用原则，并解释为什么有些看似诱人的想法在实践中却效果不佳。

2025-06-12 In this post：

### 01. Principles of Context Engineering

上下文工程的核心原则

2025-06-12 在这篇帖子中，你将了解到：

We'll work our way up to the following principles:

我们将逐步探讨以下原则：

1 Share context

分享上下文

2 Actions carry implicit decisions

行动承载着隐含的决定

Why think about principles?

为什么要思考原则？

HTML was introduced in 1993. In 2013，Facebook released React to the world. It is now 2025 and React（and its descendants）dominates the way developers build sites and apps. Why? Because React is not just a scaffold for writing code. It is a philosophy. By using React，you embrace building applications with a pattern of reactivity and modularity，which people now accept to be a standard requirement，but this was not always obvious to early web developers.

HTML 在 1993 年问世。到了 2013 年，Facebook 向全球发布了 React。现在是 2025 年，React（及其衍生技术）已经彻底改变了开发者构建网站和应用程序的方式。这是为什么呢？因为 React 不仅仅是一个编写代码的框架。它更像是一种理念。通过使用 React，开发者会遵循一种强调响应式（reactivity）和模块化（modularity）的应用构建模式，虽然现在这已经成为公认的行业标准，但对于早期的 Web 开发者来说，这一点并非一开始就显而易见。

In the age of LLMs and building AI Agents，it feels like we're still playing with raw HTML & CSS and figuring out how to fit these together to make a good experience. No single approach to building agents has become the standard yet，besides some of the absolute basics.

在大语言模型（LLMs）和构建 AI 智能体的时代，我们似乎仍在像玩弄原始的 HTML 和 CSS 那样，摸索着如何将它们巧妙组合，以创造出色的用户体验。除了少数最基础的方法，目前还没有任何一种构建智能体的方法被公认为行业标准。

> In some cases，libraries such as https://github.com/openai/swarm by OpenAI and https://github.com/microsoft/autogen by Microsoft actively push concepts which I believe to be the wrong way of building agents. Namely，using multi-agent architectures，and I'll explain why.

有些情况下，OpenAI 的 https://github.com/openai/swarm 和 Microsoft 的 https://github.com/microsoft/autogen 这类库积极推广的一些概念，在我看来，是构建 AI 智能体（AI Agent）的错误方式。具体来说，就是使用多智能体架构，接下来我会解释原因。

That said，if you're new to agent-building，there are lots of resources on how to set up the basic scaffolding [1] [2]. But when it comes to building serious production applications，it's a different story.

话虽如此，如果你是 AI 智能体（AI Agent）构建的新手，网上有很多关于如何搭建基础框架的资源 [1] [2]。但若要构建严肃的生产级应用，情况则大不相同。

### 02. A Theory of Building Long-running Agents

论长期运行的 AI 智能体（AI Agent）构建

Let's start with reliability. When agents have to actually be reliable while running for long periods of time and maintain coherent conversations，there are certain things you must do to contain the potential for compounding errors. Otherwise，if you're not careful，things fall apart quickly. At the core of reliability is Context Engineering.

我们先来谈谈可靠性。当 AI 智能体需要在长时间运行中保持稳定可靠，并维持连贯的对话时，你必须采取一些措施来抑制复合错误的风险。否则，如果你不够谨慎，系统会很快崩溃。而可靠性的核心，就是上下文工程（Context Engineering）。

Context Engineering

上下文工程

In 2025，the models out there are extremely intelligent. But even the smartest human won't be able to do their job effectively without the context of what they're being asked to do.「Prompt engineering」was coined as a term for the effort needing to write your task in the ideal format for a LLM chatbot.「Context engineering」is the next level of this. It is about doing this automatically in a dynamic system. It takes more nuance and is effectively the #1 job of engineers building AI agents.

到了 2025 年，市面上的模型已经变得极其智能。然而，即使是最聪明的人类，如果对所要求完成的任务缺乏必要的背景信息，也无法高效地开展工作。「提示工程（Prompt Engineering）」这个词应运而生，它指的是为大语言模型（LLM）聊天机器人编写任务时，需要努力将其内容以最理想的格式呈现。「上下文工程」则是在此基础上更进一步。它致力于在动态系统中自动完成这一过程。这需要更精细的处理，并且实际上是构建 AI 智能体（AI Agent）的工程师的首要任务。

Take an example of a common type of agent. This agent

以一种常见的 AI 智能体（AI Agent）为例，它通常会：

1 breaks its work down into multiple parts

将自己的工作分解成多个部分

2 starts subagents to work on those parts

启动多个子任务代理来分别处理这些部分

3 combines those results in the end

最后将所有结果汇总起来

This is a tempting architecture，especially if you work in a domain of tasks with several parallel components to it. However，it is very fragile. The key failure point is this:

这是一种很有吸引力的架构，尤其是当你处理的任务包含多个并行组件时。然而，它也相当脆弱。其关键的失败点在于：

> Suppose your Task is「build a Flappy Bird clone」. This gets divided into Subtask 1「build a moving game background with green pipes and hit boxes」and Subtask 2「build a bird that you can move up and down」.It turns out subagent 1 actually mistook your subtask and started building a background that looks like Super Mario Bros. Subagent 2 built you a bird，but it doesn't look like a game asset and it moves nothing like the one in Flappy Bird. Now the final agent is left with the undesirable task of combining these two miscommunications.

假设你的任务是「构建一个 Flappy Bird 克隆」。这个任务被分解为子任务 1「构建一个带有绿色管道和碰撞箱的移动游戏背景」和子任务 2「构建一只可以上下移动的鸟」。结果，子智能体 1 实际上误解了你的子任务，并开始构建一个看起来像《超级马里奥兄弟》（Super Mario Bros）的背景。子智能体 2 为你构建了一只鸟，但它看起来不像游戏素材（game asset），而且它的移动方式与 Flappy Bird 中的完全不同。现在，最终智能体只剩下了一个棘手的任务：组合这两个因为误解而产生的部分。

This may seem contrived，but most real-world tasks have many layers of nuance that all have the potential to be miscommunicated. You might think that a simple solution would be to just copy over the original task as context to the subagents as well. That way，they don't misunderstand their subtask. But remember that in a real production system，the conversation is most likely multi-turn，the agent probably had to make some tool calls to decide how to break down the task，and any number of details could have consequences on the interpretation of the task.

这可能听起来有些刻意，但大多数现实世界的任务都包含多层细微差别，每层都可能导致误解。你可能会认为一个简单的解决方案是：直接将原始任务作为上下文复制给子智能体（subagents）。这样一来，它们就不会误解自己的子任务了。但请记住，在真实的生产系统中，对话很可能是多轮的，AI 智能体（AI Agent）可能需要进行一些工具调用来决定如何分解任务，而且诸多细节都可能影响对任务的解释。

> Principle 1Share context，and share full agent traces，not just individual messages

原则 1：共享上下文，以及共享完整的 AI 智能体轨迹，而不仅仅是单个消息。

Let's take another revision at our agent，this time making sure each agent has the context of the previous agents.

让我们再重新审视一下我们的 AI 智能体，这次要确保每个 AI 智能体都能获取到之前所有 AI 智能体的上下文信息。

Unfortunately，we aren't quite out of the woods. When you give your agent the same Flappy Bird cloning task，this time，you might end up with a bird and background with completely different visual styles. Subagent 1 and subagent 2 cannot not see what the other was doing and so their work ends up being inconsistent with each other.

不幸的是，我们还没有完全脱离困境。当你给你的 AI 智能体相同的 Flappy Bird 克隆任务时，这次，你最终可能会得到一个鸟和背景，它们具有完全不同的视觉风格。子智能体 1 和子智能体 2 无法看到对方正在做什么，因此它们的工作最终变得彼此不一致。

The actions subagent 1 took and the actions subagent 2 took were based on conflicting assumptions not prescribed upfront.

子智能体 1 和子智能体 2 所采取的行动，都是基于一些事先没有明确规定、甚至相互冲突的假设。

> Principle 2Actions carry implicit decisions，and conflicting decisions carry bad results

原则 2：每一个行动都包含着隐含的决策，而相互冲突的决策往往会导致不好的结果。

I would argue that Principles 1 & 2 are so critical，and so rarely worth violating，that you should by default rule out any agent architectures that don't abide by then. You might think this is constraining，but there is actually a wide space of different architectures you could still explore for your agent.

我认为原则 1 和原则 2 至关重要，几乎不值得违反，所以你应该默认排除任何不遵守这些原则的 AI 智能体（agent）架构。你可能会觉得这很有局限性，但实际上，你仍然有许多不同的架构可供你的 AI 智能体探索。

The simplest way to follow the principles is to just use a single-threaded linear agent:

要遵循这些原则，最简单的方法就是使用一个单线程线性 AI 智能体（AI Agent)：

Here，the context is continuous. However，you might run into issues for very large tasks with so many subparts that context windows start to overflow.

在这种情况下，上下文（context）是连续的。然而，如果任务过于庞大，包含的子部分过多，可能会导致上下文窗口（context window）出现溢出问题。

To be honest，the simple architecture will get you very far，but for those who have truly long-duration tasks，and are willing to put in the effort，you can do even better. There are several ways you could solve this，but today I will present just one:

平心而论，简单的架构（architecture）就能让您事半功倍，但对于那些确实需要处理长时间任务，并且愿意投入精力的人来说，您还可以做得更好。解决这个问题的方法有多种，但今天我将只介绍其中一种：

In this world，we introduce a new LLM model whose key purpose is to compress a history of actions & conversation into key details，events，and decisions. This is hard to get right. It takes investment into figuring out what ends up being the key information and creating a system that is good at this. Depending on the domain，you might even consider fine-tuning a smaller model（this is in fact something we've done at Cognition).

在本文中，我们引入了一个新的大语言模型（LLM）模型，其主要目的是将行动和对话的历史压缩成关键的细节、事件和决策。要精确地完成这项任务并非易事，它需要投入大量精力去识别哪些信息才是核心关键，并构建一个擅长此道的系统。根据具体的应用领域，你甚至可以考虑对一个更小的模型进行微调（这正是我们在 Cognition 公司已经实践过的）。

The benefit you get is an agent that is effective at longer contexts. You will still eventually hit a limit though. For the avid reader，I encourage you to think of better ways to manage arbitrarily long contexts. It ends up being quite a deep rabbit hole!

这样做的好处是，你的 AI 智能体（AI Agent）在处理更长的上下文时会表现得更有效。不过，你最终仍然会遇到处理长度的极限。对于那些热衷于钻研的读者，我鼓励你思考如何更好地管理任意长度的上下文。深入探索这个问题，你会发现它真是一个深不见底的「兔子洞」！

### 03. Applying the Principles

应用原则

If you're an agent-builder，ensure your agent's every action is informed by the context of all relevant decisions made by other parts of the system. Ideally，every action would just see everything else. Unfortunately，this is not always possible due to limited context windows and practical tradeoffs，and you may need to decide what level of complexity you are willing to take on for the level of reliability you aim for.

如果你是 AI 智能体（AI Agent）的构建者，确保你的智能体的每一个行动都基于系统其他部分所做出的所有相关决策的上下文。理想情况下，每个行动都能够获知所有其他信息。不幸的是，由于上下文窗口的限制以及实际的权衡，这并不总是可行。因此，你可能需要根据你所期望达到的可靠性水平，来决定愿意承担的复杂程度。

As you think about architecting your agents to avoid conflicting decision-making，here are some real-world examples to ponder:Claude Code SubagentsAs of June 2025，Claude Code is an example of an agent that spawns subtasks. However，it never does work in parallel with the subtask agent，and the subtask agent is usually only tasked with answering a question，not writing any code. Why? The subtask agent lacks context from the main agent that would otherwise be needed to do anything beyond answering a well-defined question. And if they were to run multiple parallel subagents，they might give conflicting responses，resulting in the reliability issues we saw with our earlier examples of agents. The benefit of having a subagent in this case is that all the subagent's investigative work does not need to remain in the history of the main agent，allowing for longer traces before running out of context. The designers of Claude Code took a purposefully simple approach.Edit Apply ModelsIn 2024，many models were really bad at editing code. A common practice among coding agents，IDEs，app builders，etc.（including Devin）was to use an「edit apply model.」The key idea was that it was actually more reliable to get a small model to rewrite your entire file，given a markdown explanation of the changes you wanted，than to get a large model to output a properly formatted diff. So，builders had the large models output markdown explanations of code edits and then fed these markdown explanations to small models to actually rewrite the files. However，these systems would still be very faulty. Often times，for example，the small model would misinterpret the instructions of the large model and make an incorrect edit due to the most slight ambiguities in the instructions. Today，the edit decision-making and applying are more often done by a single model in one action.

当您考虑构建 AI 智能体（AI Agent）以避免决策冲突时，以下是一些值得深思的真实世界示例：

Claude Code 子智能体截至 2025 年 6 月，Claude Code 是一个会生成子任务的智能体示例。然而，它从不与子任务智能体并行工作，并且子任务智能体通常只负责回答问题，而不编写任何代码。为什么会这样呢？子任务智能体缺乏主智能体所需的上下文（Context），而这些上下文是在回答明确定义的问题之外进行任何操作所必需的。如果它们运行多个并行子智能体，它们可能会给出相互冲突的响应，导致我们在早期智能体示例中看到的可靠性问题。在这种情况下，拥有子智能体的好处是，子智能体的所有调查工作无需保留在主智能体的历史记录中，从而允许在上下文耗尽之前进行更长的跟踪。Claude Code 的设计者采取了一种刻意简单的方法。

编辑应用模型（Edit Apply Models)
在 2024 年，许多模型在编辑代码方面表现非常差。在编码智能体、IDE、应用程序构建器等（包括 Devin）中，一种常见做法是使用「编辑应用模型」。其核心思想是，让一个小型模型根据您想要的更改的 Markdown 解释来重写整个文件，实际上比让一个大型模型输出格式正确的差异（Diff）更可靠。因此，构建者让大型模型输出代码编辑的 Markdown 解释，然后将这些 Markdown 解释提供给小型模型，以实际重写文件。然而，这些系统仍然会问题百出。例如，小模型常常会因为指令中最轻微的歧义而误解大型模型的指令，并进行不正确的编辑。如今，编辑决策和应用通常由单个模型在一个操作中完成。

Multi-Agents

多智能体（Multi-Agents)

If we really want to get parallelism out of our system，you might think to let the decision makers「talk」to each other and work things out.

如果我们真的希望系统能够实现并行处理，你可能会想到让各个决策者之间相互「交流」，共同协作来完成任务。

This is what us humans do when we disagree（in an ideal world). If Engineer A's code causes a merge conflict with Engineer B，the correct protocol is to talk out the differences and reach a consensus. However，agents today are not quite able to engage in this style of long-context proactive discourse with much more reliability than you would get with a single agent. Humans are quite efficient at communicating our most important knowledge to one another，but this efficiency takes nontrivial intelligence.

这就是我们人类在意见不合时所做的（在一个理想世界中）。如果工程师 A 的代码与工程师 B 的代码发生合并冲突，正确的处理方式是双方讨论分歧并达成共识。然而，如今的智能体（agent）在进行这种需要长程上下文的、主动性对话时，其可靠性并没有比单个智能体高出多少。人类在相互交流最重要的知识时效率很高，但这种效率的实现需要相当高的智能。

Since not long after the launch of ChatGPT，people have been exploring the idea of multiple agents interacting with one another to achieve goals [3][4]. While I'm optimistic about the long-term possibilities of agents collaborating with one another，it is evident that in 2025，running multiple agents in collaboration only results in fragile systems. The decision-making ends up being too dispersed and context isn't able to be shared thoroughly enough between the agents. At the moment，I don't see anyone putting a dedicated effort to solving this difficult cross-agent context-passing problem. I personally think it will come for free as we make our single-threaded agents even better at communicating with humans. When this day comes，it will unlock much greater amounts of parallelism and efficiency.

自 ChatGPT 推出后不久，人们一直在探索多个 AI 智能体（AI Agent）相互协作以实现目标的想法 [3][4]。虽然我对智能体之间相互协作的长期可能性持乐观态度，但很明显，在 2025 年，让多个智能体协作运行只会导致系统变得脆弱。决策最终会过于分散，并且上下文信息无法在智能体之间充分共享。目前，我还没有看到有人投入专门的精力来解决这个困难的跨智能体上下文传递问题。我个人认为，随着我们让单线程智能体在与人类沟通方面变得更加出色，这个问题将迎刃而解。当这一天到来时，它将极大地提升并行处理能力和效率。

Toward a More General Theory

迈向更通用理论

These observations on context engineering are just the start to what we might someday consider the standard principles of building agents. And there are many more challenges and techniques not discussed here. At Cognition，agent building is a key frontier we think about. We build our internal tools and frameworks around these principles we repeatedly find ourselves relearning as a way to enforce these ideas. But our theories are likely not perfect，and we expect things to change as the field advances，so some flexibility and humility is required as well.

这些关于上下文工程的观察，仅仅是我们未来可能认为是构建 AI 智能体（Agent）标准原则的开端。当然，还有许多挑战和技术并未在此详述。在 Cognition，构建 AI 智能体是我们关注的一个重要前沿领域。我们围绕着那些反复被我们重新验证的原则，构建内部工具和框架，从而更好地落实这些理念。然而，我们的理论可能并不完美，随着领域的发展，我们预计情况会不断变化，因此也需要保持一定的灵活性和谦逊。