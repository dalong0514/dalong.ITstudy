## 20250613How-We-Built-Our-Multi-Agent-Research-System

[How we built our multi-agent research system \ Anthropic](https://www.anthropic.com/engineering/built-multi-agent-research-system)

[Engineering at Anthropic](https://www.anthropic.com/engineering)

Published Jun 13，2025

Our Research feature uses multiple Claude agents to explore complex topics more effectively. We share the engineering challenges and the lessons we learned from building this system.

我们的「研究（Research）」功能通过运用多个 Claude 智能体（Claude agents），能够更有效地探索复杂课题。在这里，我们将与大家分享在构建这一系统过程中所遇到的工程技术挑战，以及我们从中汲取的经验教训。

Claude now has Research capabilities that allow it to search across the web，Google Workspace，and any integrations to accomplish complex tasks.

The journey of this multi-agent system from prototype to production taught us critical lessons about system architecture，tool design，and prompt engineering. A multi-agent system consists of multiple agents（LLMs autonomously using tools in a loop）working together. Our Research feature involves an agent that plans a research process based on user queries，and then uses tools to create parallel agents that search for information simultaneously. Systems with multiple agents introduce new challenges in agent coordination，evaluation，and reliability.

Claude 现在具备了研究能力，能够跨越互联网、Google Workspace 以及任何集成的应用进行搜索，以完成复杂的任务。

这个多智能体系统（multi-agent system）从原型走向实际应用的过程，让我们在系统架构、工具设计和提示工程（prompt engineering）方面获得了宝贵的经验。所谓多智能体系统，就是由多个 AI 智能体（AI Agent）协同工作组成的系统，而这些 AI 智能体其实就是能够在循环中自主使用工具的大语言模型（LLM）。我们的研究功能就包含了一个这样的 AI 智能体，它会先根据用户的提问规划研究方案，然后运用工具创建出多个并行的 AI 智能体，让它们同时分头搜索信息。这种包含多个 AI 智能体的系统，在 AI 智能体的协调、评估和可靠性方面也带来了新的挑战。

This post breaks down the principles that worked for us—we hope you'll find them useful to apply when building your own multi-agent systems.

这篇文章将为大家剖析我们总结出的一些行之有效的原则 —— 我们希望在您构建自己的多智能体系统（multi-agent system）时，这些原则能为您提供有用的参考。

### 01. Benefits of a multi-agent system

多智能体系统的好处

Research work involves open-ended problems where it's very difficult to predict the required steps in advance. You can't hardcode a fixed path for exploring complex topics，as the process is inherently dynamic and path-dependent. When people conduct research，they tend to continuously update their approach based on discoveries，following leads that emerge during investigation.

研究工作常常涉及一些没有固定答案的难题（open-ended problems），这些难题的特点就是很难预先规划好每一步确切的步骤。我们无法为探索复杂课题设定一条写死的、固定不变的路径（hardcode a fixed path），因为研究过程本身就是动态变化的，并且深受此前每一步进展的影响（path-dependent）。当人们进行研究时，往往会根据新的发现不断调整自己的思路和方法，顺着调查过程中涌现出来的新线索继续探索。

This unpredictability makes AI agents particularly well-suited for research tasks. Research demands the flexibility to pivot or explore tangential connections as the investigation unfolds. The model must operate autonomously for many turns，making decisions about which directions to pursue based on intermediate findings. A linear，one-shot pipeline cannot handle these tasks.

正是这种不可预测性，使得 AI 智能体（AI Agent）尤其擅长处理研究型任务。科学研究往往要求我们具备高度的灵活性，能够在研究不断深入的过程中，随时调整方向，或者去探索那些看似不那么直接相关，但可能蕴藏新发现的旁支线索。模型必须能够自主地进行多轮的探索，并根据中途的发现来决定接下来要朝哪个方向努力。那种按部就班、一步到位的线性流程，是无法胜任这类任务的。

The essence of search is compression：distilling insights from a vast corpus. Subagents facilitate compression by operating in parallel with their own context windows，exploring different aspects of the question simultaneously before condensing the most important tokens for the lead research agent. Each subagent also provides separation of concerns—distinct tools，prompts，and exploration trajectories—which reduces path dependency and enables thorough，independent investigations.

搜索的本质就是压缩（compression)：从海量的资料中萃取出精华见解。子智能体（Subagents）通过各自独立的上下文窗口（context windows）并行工作，在为主要研究智能体凝练出最重要的 Token 之前，它们会同时探索问题的不同方面，以此来促进信息的压缩。每个子智能体还实现了关注点分离（separation of concerns)—— 它们各自拥有不同的工具、提示（prompts）和探索路径 —— 这能够减少路径依赖（path dependency），并让彻底且独立的调查成为可能。

Once intelligence reaches a threshold，multi-agent systems become a vital way to scale performance. For instance，although individual humans have become more intelligent in the last 100,000 years，human societies have become exponentially more capable in the information age because of our collective intelligence and ability to coordinate. Even generally-intelligent agents face limits when operating as individuals; groups of agents can accomplish far more.

一旦智能水平达到某一门槛，多智能体系统（multi-agent systems）便成为提升整体表现的关键手段。举个例子，虽然在过去的十万年间，我们单个人的聪明才智或许有所增长，但人类社会作为一个整体，在信息时代所展现出的能力却实现了指数级的飞跃，这主要归功于我们的集体智能（collective intelligence）和协同工作的能力。即便是具备通用智能的 AI 智能体（generally-intelligent agents），在单独行动时也会遇到能力上限；而由多个 AI 智能体组成的群体则能够成就远超个体能力的大事。

Our internal evaluations show that multi-agent research systems excel especially for breadth-first queries that involve pursuing multiple independent directions simultaneously. We found that a multi-agent system with Claude Opus 4 as the lead agent and Claude Sonnet 4 subagents outperformed single-agent Claude Opus 4 by 90.2% on our internal research eval. For example，when asked to identify all the board members of the companies in the Information Technology S&P 500，the multi-agent system found the correct answers by decomposing this into tasks for subagents，while the single agent system failed to find the answer with slow，sequential searches.

我们的内部评估显示，多智能体研究系统在处理那些需要「广撒网」、同时探索多个不同方向信息的「广度优先查询（breadth-first queries）」时，表现得特别出色。我们发现，在一个由 Claude Opus 4 担任主要 AI 智能体（AI Agent），并配有多个 Claude Sonnet 4 作为子 AI 智能体的多智能体系统中，它在我们的内部研究评估中的表现，要比单打独斗的 Claude Opus 4（作为单 AI 智能体）高出整整 90.2%。举个例子，当被要求找出信息技术 S&P 500 指数里所有公司的董事会成员时，这个多智能体系统能够巧妙地将任务「化整为零」，分配给各个子 AI 智能体分头行动，从而成功找到了所有答案。相比之下，那个单 AI 智能体系统则因为采用的是比较缓慢、按部就班的顺序搜索方法，最终没能完成这项任务。

Multi-agent systems work mainly because they help spend enough tokens to solve the problem. In our analysis，three factors explained 95% of the performance variance in the BrowseComp evaluation（which tests the ability of browsing agents to locate hard-to-find information). We found that token usage by itself explains 80% of the variance，with the number of tool calls and the model choice as the two other explanatory factors. This finding validates our architecture that distributes work across agents with separate context windows to add more capacity for parallel reasoning. The latest Claude models act as large efficiency multipliers on token use，as upgrading to Claude Sonnet 4 is a larger performance gain than doubling the token budget on Claude Sonnet 3.7. Multi-agent architectures effectively scale token usage for tasks that exceed the limits of single agents.

多个 AI 智能体（AI Agent）组成的系统之所以能有效运作，关键在于它们有助于投入足够量的 Token（Token）来解决问题。在我们的分析中，有三个因素解释了 BrowseComp 评估中 95% 的性能表现差异（BrowseComp 是一项评估浏览型 AI 智能体查找高难度信息能力的测试）。我们发现，单是 Token 的使用量本身就能解释 80% 的表现差异，而工具调用次数和模型选择则是另外两个解释性因素。这一发现验证了我们设计的架构：通过将工作分配给拥有独立上下文窗口（context windows）的不同 AI 智能体，从而增强系统并行推理（parallel reasoning）的能力。最新的 Claude 系列模型在 Token 使用方面，就像强大的效率放大器：升级到 Claude Sonnet 4 所带来的性能提升，甚至比将 Claude Sonnet 3.7 模型的 Token 预算翻倍还要大。对于那些超出单个 AI 智能体能力极限的任务，采用多个 AI 智能体的架构能够有效地扩展 Token 的使用规模。

There is a downside：in practice，these architectures burn through tokens fast. In our data，agents typically use about 4× more tokens than chat interactions，and multi-agent systems use about 15× more tokens than chats. For economic viability，multi-agent systems require tasks where the value of the task is high enough to pay for the increased performance. Further，some domains that require all agents to share the same context or involve many dependencies between agents are not a good fit for multi-agent systems today. For instance，most coding tasks involve fewer truly parallelizable tasks than research，and LLM agents are not yet great at coordinating and delegating to other agents in real time. We've found that multi-agent systems excel at valuable tasks that involve heavy parallelization，information that exceeds single context windows，and interfacing with numerous complex tools.

然而，这种做法也存在一个弊端：在实践中，这些架构消耗 Token 的速度非常快。根据我们的数据，AI 智能体（AI Agent）通常比普通的聊天交互多使用约 4 倍的 Token，而多智能体系统（multi-agent systems）的 Token 使用量更是达到聊天交互的约 15 倍。从经济角度来看，要让多智能体系统具备可行性，其处理的任务本身必须具有足够高的价值，才能抵消其高昂的运行成本。此外，有些领域需要所有智能体共享同一个上下文（context），或者智能体之间存在大量互相依赖的情况，目前来看，这些领域还不太适合采用多智能体系统。举个例子，大部分编程任务与科研任务相比，其真正能够并行处理的部分较少，而且目前的大语言模型（LLM）智能体在实时协调并将任务委派给其他智能体方面也还不够出色。我们发现，多智能体系统特别擅长处理那些有价值、可进行大规模并行化、信息量超出单个模型上下文窗口处理能力，并且需要与多种复杂工具进行交互的任务。

### 02. Architecture overview for Research

「研究」系统架构概览

Our Research system uses a multi-agent architecture with an orchestrator-worker pattern，where a lead agent coordinates the process while delegating to specialized subagents that operate in parallel.

我们的「研究」系统采用了一种多智能体（multi-agent）架构，并运用了「编排者-工作者」(orchestrator-worker）模式。在这种模式下，由一个主智能体（lead agent）来协调整体流程，同时将任务委派给多个专门的子智能体（specialized subagents），这些子智能体可以并行运作。

The multi-agent architecture in action：user queries flow through a lead agent that creates specialized subagents to search for different aspects in parallel. When a user submits a query，the lead agent analyzes it，develops a strategy，and spawns subagents to explore different aspects simultaneously. As shown in the diagram above，the subagents act as intelligent filters by iteratively using search tools to gather information，in this case on AI agent companies in 2025，and then returning a list of companies to the lead agent so it can compile a final answer.

实际运行中的多智能体架构（multi-agent architecture）是这样的：用户的查询会首先交给一个领导智能体（lead agent），这个领导智能体会创建一些专业的子智能体（subagent），让它们分头并行地去查找用户所需的不同方面信息。当用户提交一个查询时，领导智能体就会分析这个查询，制定出一个策略，然后生成相应的子智能体去同时探索问题的各个不同方面。正如上图所示，这些子智能体就像一个个智能过滤器一样，它们会反复使用搜索工具来收集信息（例如，在这个例子中，它们收集的就是 2025 年的 AI 智能体（AI Agent）公司信息），然后把找到的公司列表返回给领导智能体，领导智能体再根据这些信息汇总出最终的答案。

Traditional approaches using Retrieval Augmented Generation（RAG）use static retrieval. That is，they fetch some set of chunks that are most similar to an input query and use these chunks to generate a response. In contrast，our architecture uses a multi-step search that dynamically finds relevant information，adapts to new findings，and analyzes results to formulate high-quality answers.

传统上，采用「检索增强生成（Retrieval Augmented Generation，RAG）」的方法通常使用的是「静态检索（static retrieval）」。也就是说，这些方法会先找出一些和用户提问最相似的「文本块（chunks）」，然后利用这些文本块来组织答案。而我们的方法则不同，它采用了一种「多步搜索（multi-step search）」的机制。这种机制能够动态地发现相关信息，根据新获取的内容进行调整，并对所有信息进行分析，从而给出更加精准、高质量的回答。

Process diagram showing the complete workflow of our multi-agent Research system. When a user submits a query，the system creates a LeadResearcher agent that enters an iterative research process. The LeadResearcher begins by thinking through the approach and saving its plan to Memory to persist the context，since if the context window exceeds 200,000 tokens it will be truncated and it is important to retain the plan. It then creates specialized Subagents（two are shown here，but it can be any number）with specific research tasks. Each Subagent independently performs web searches，evaluates tool results using [interleaved thinking](https://docs.anthropic.com/en/docs/build-with-claude/extended-thinking#interleaved-thinking)，and returns findings to the LeadResearcher. The LeadResearcher synthesizes these results and decides whether more research is needed—if so，it can create additional subagents or refine its strategy. Once sufficient information is gathered，the system exits the research loop and passes all findings to a CitationAgent，which processes the documents and research report to identify specific locations for citations. This ensures all claims are properly attributed to their sources. The final research results，complete with citations，are then returned to the user. 

这张流程图展示了我们「多智能体研究系统」(multi-agent Research system）的完整工作流程。当用户提交一个查询后，系统会创建一个「首席研究员」(LeadResearcher）AI 智能体（AI Agent）。这位「首席研究员」随即启动一个迭代式的研究过程。「首席研究员」首先会仔细思考研究方法，并将研究计划存储到「记忆体」(Memory）中，以确保研究背景信息（context）得以保留。这样做非常重要，因为一旦「上下文窗口」(context window）超过 20 万个「Token」(Token），信息就可能被截断，而保留研究计划则能避免这种情况。随后，它会创建专门的「子研究员」(Subagents）(图中展示了两个，但实际数量不限），并为它们分配具体的研究任务。每一位「子研究员」都会独立进行网络搜索，利用「[交错思考](https://docs.anthropic.com/en/docs/build-with-claude/extended-thinking#interleaved-thinking)」(interleaved thinking）的方法来评估工具检索到的结果，并将研究发现反馈给「首席研究员」。「首席研究员」会对这些结果进行整合分析，并判断是否需要进一步研究。如果需要，它可以创建更多的「子研究员」，或者调整现有策略。一旦收集到足够的信息，系统就会结束当前的研究循环，并将所有的研究成果转交给一位「引文处理员」(CitationAgent）。这位「引文处理员」负责处理相关文档和研究报告，找出需要添加引用的具体位置。这样可以确保报告中的所有论点都能准确溯源到其原始出处。最终，附带完整引用的研究结果将返还给用户。

### 03. Prompt engineering and evaluations for research agents

针对研究型 AI 智能体的提示工程（Prompt engineering）与评估

Multi-agent systems have key differences from single-agent systems，including a rapid growth in coordination complexity. Early agents made errors like spawning 50 subagents for simple queries，scouring the web endlessly for nonexistent sources，and distracting each other with excessive updates. Since each agent is steered by a prompt，prompt engineering was our primary lever for improving these behaviors. Below are some principles we learned for prompting agents:

多 AI 智能体系统（Multi-agent systems）与单 AI 智能体系统（single-agent systems）之间存在关键区别，其中包括协调复杂度的快速增长。早期的 AI 智能体（AI Agent）们会犯下一些错误，例如：为一个简单的查询就派生出 50 个子 AI 智能体（subagent），为了查找不存在的信源而无休止地搜寻网络，以及因为发送了过多的更新信息而互相干扰。由于每个 AI 智能体都由提示（prompt）来引导其行为，因此，提示工程（prompt engineering）就成了我们改善这些行为的主要抓手。以下是我们学习到的，在为 AI 智能体编写提示时可以遵循的一些原则：

1 Think like your agents. To iterate on prompts，you must understand their effects. To help us do this，we built simulations using our Console with the exact prompts and tools from our system，then watched agents work step-by-step. This immediately revealed failure modes：agents continuing when they already had sufficient results，using overly verbose search queries，or selecting incorrect tools. Effective prompting relies on developing an accurate mental model of the agent，which can make the most impactful changes obvious.

要学会站在 AI 智能体（AI Agent）的视角来思考。要想不断优化和改进提示（prompts），你就必须深入理解这些提示会产生什么样的效果。为了做到这一点，我们借助自家的控制台（Console）构建了模拟环境。这些模拟精确还原了我们系统中所使用的提示和工具，然后我们就一步步地观察 AI 智能体是如何工作的。这样做的好处是，AI 智能体在工作中可能出现的各种问题立刻暴露无遗，比如：明明已经找到了足够的答案却还在继续搜索，使用的搜索指令过于啰嗦，或者选错了工具等等。想要高效地设计提示（prompting），关键在于你需要在头脑中构建一个关于 AI 智能体如何工作的准确心智模型（mental model）。一旦你有了这样的模型，那些能带来最大改进的调整自然就变得显而易见了。

2 Teach the orchestrator how to delegate. In our system，the lead agent decomposes queries into subtasks and describes them to subagents. Each subagent needs an objective，an output format，guidance on the tools and sources to use，and clear task boundaries. Without detailed task descriptions，agents duplicate work，leave gaps，or fail to find necessary information. We started by allowing the lead agent to give simple，short instructions like 'research the semiconductor shortage,' but found these instructions often were vague enough that subagents misinterpreted the task or performed the exact same searches as other agents. For instance，one subagent explored the 2021 automotive chip crisis while 2 others duplicated work investigating current 2025 supply chains，without an effective division of labor.

教会「总指挥」(orchestrator）如何分配任务。在我们的系统中，「领导 AI 智能体」(lead agent）会把用户提出的问题拆解成一个个小任务，然后把这些小任务的具体情况告诉「子 AI 智能体」(subagent）。每个「子 AI 智能体」都需要明确自己的目标、成果输出的格式、完成任务时该用什么工具和参考哪些资料，以及清晰的任务范围。如果任务描述不够详细，这些 AI 智能体们就可能做重复劳动，或者遗漏某些方面，甚至找不到关键信息。一开始，我们尝试让「领导 AI 智能体」给出一些简单笼统的指令，比如「研究半导体短缺问题」。但我们发现，这些指令往往太模糊了，导致「子 AI 智能体」要么理解错任务，要么跟其他 AI 智能体做了完全一样的搜索工作。举个例子，曾经有一个「子 AI 智能体」在研究 2021 年的汽车芯片危机，而另外两个「子 AI 智能体」却都在重复调查 2025 年的供应链情况，完全没有形成有效的分工合作。

3 Scale effort to query complexity. Agents struggle to judge appropriate effort for different tasks，so we embedded scaling rules in the prompts. Simple fact-finding requires just 1 agent with 3-10 tool calls，direct comparisons might need 2-4 subagents with 10-15 calls each，and complex research might use more than 10 subagents with clearly divided responsibilities. These explicit guidelines help the lead agent allocate resources efficiently and prevent overinvestment in simple queries，which was a common failure mode in our early versions.

根据查询复杂度调整投入。AI 智能体（AI Agent）往往难以判断不同任务所需的合适投入，因此我们在提示（prompts）中内置了动态调整投入的规则。简单的信息获取任务，只需要 1 个 AI 智能体调用 3-10 次工具；直接比较类任务，可能需要 2-4 个子 AI 智能体（subagents），每个调用 10-15 次工具；而复杂的研究任务，则可能需要超过 10 个子 AI 智能体，并明确各自的职责。这些清晰的指引有助于主 AI 智能体（lead agent）高效地分配资源，并避免在简单的查询上投入过多精力 —— 这在我们早期版本中是一个常见的故障模式（failure mode）。

4 Tool design and selection are critical. Agent-tool interfaces are as critical as human-computer interfaces. Using the right tool is efficient—often，it's strictly necessary. For instance，an agent searching the web for context that only exists in Slack is doomed from the start. With MCP servers that give the model access to external tools，this problem compounds，as agents encounter unseen tools with descriptions of wildly varying quality. We gave our agents explicit heuristics：for example，examine all available tools first，match tool usage to user intent，search the web for broad external exploration，or prefer specialized tools over generic ones. Bad tool descriptions can send agents down completely wrong paths，so each tool needs a distinct purpose and a clear description.

工具的设计和选择至关重要。AI 智能体（AI Agent）与工具之间的接口，其重要性堪比我们熟悉的人机交互界面。用对工具能事半功倍 —— 很多时候，这甚至是成败的关键。举个例子，如果一个 AI 智能体想在互联网上搜索只有 Slack 里才有的特定信息，那它从一开始就注定会无功而返。当通过 MCP 服务器赋予模型调用外部工具的能力时，这个问题就变得更加棘手了，因为 AI 智能体可能会遇到一些它从未见过的新工具，而这些工具的描述信息质量又参差不齐。我们为 AI 智能体提供了一些明确的启发式策略（heuristics)：比如，先检查所有可用的工具，确保工具的使用与用户的真实意图相匹配，如果需要广泛搜集外部信息就去网上搜索，或者优先选用针对性强的专业工具而非普适的通用工具。糟糕的工具描述可能会让 AI 智能体完全跑偏，所以每个工具都必须有明确的用途定位和清晰易懂的说明。

5 Let agents improve themselves. We found that the Claude 4 models can be excellent prompt engineers. When given a prompt and a failure mode，they are able to diagnose why the agent is failing and suggest improvements. We even created a tool-testing agent—when given a flawed MCP tool，it attempts to use the tool and then rewrites the tool description to avoid failures. By testing the tool dozens of times，this agent found key nuances and bugs. This process for improving tool ergonomics resulted in a 40% decrease in task completion time for future agents using the new description，because they were able to avoid most mistakes.

让 AI 智能体（AI Agent）实现自我改进。我们发现，Claude 4 模型能够成为出色的提示工程师（prompt engineers）。当给它们一个提示（prompt）和一个失败模式（failure mode）时，它们就能诊断出 AI 智能体为何会失败，并提出改进建议。我们甚至创建了一个专门的「工具测试 AI 智能体（tool-testing agent）」—— 当给它一个有缺陷的 MCP 工具（MCP tool）时，它会尝试使用这个工具，然后重新编写工具说明书，以避免重蹈覆辙。通过对工具进行数十次测试，这个 AI 智能体发现了其中关键的细微之处和一些不易察觉的错误（bugs）。这种改进工具易用性（tool ergonomics）的过程，使得后续的 AI 智能体在使用新的说明书时，任务完成时间缩短了 40%，因为它们得以避免了大多数先前会导致失败的操作。

6 Start wide，then narrow down. Search strategy should mirror expert human research：explore the landscape before drilling into specifics. Agents often default to overly long，specific queries that return few results. We counteracted this tendency by prompting agents to start with short，broad queries，evaluate what's available，then progressively narrow focus.

先从宽泛入手，再逐步聚焦。搜索策略应当模仿人类专家的研究方法：先对整体情况有一个大致的了解（explore the landscape），然后再深入到具体细节。AI 智能体（AI Agent）常常会默认采用过于冗长和具体的查询语句，导致搜索结果寥寥无几。我们通过引导 AI 智能体先使用简短、宽泛的查询词，评估当前可获得的信息，然后逐渐收窄搜索焦点，来克服这一倾向。

7 Guide the thinking process. Extended thinking mode，which leads Claude to output additional tokens in a visible thinking process，can serve as a controllable scratchpad. The lead agent uses thinking to plan its approach，assessing which tools fit the task，determining query complexity and subagent count，and defining each subagent's role. Our testing showed that extended thinking improved instruction-following，reasoning，and efficiency. Subagents also plan，then use interleaved thinking after tool results to evaluate quality，identify gaps，and refine their next query. This makes subagents more effective in adapting to any task.

引导思考过程。扩展思考模式（Extended thinking mode）能够引导 Claude 输出额外的 Token，并以可见的方式展示其思考步骤，就像一个我们可以控制的「草稿本」一样。主导 AI 智能体（lead agent）会运用这种思考来规划自身的方案，评估哪些工具适合当前任务、判断查询的复杂度、决定需要多少子 AI 智能体（subagent），并明确每个子 AI 智能体的角色。我们的测试表明，扩展思考模式提升了模型在遵循指令、进行推理和提高效率方面的表现。子 AI 智能体也会先进行规划，然后在得到工具返回的结果后，运用交错思考（interleaved thinking）的方式来评估结果质量、找出不足之处，并优化其下一步的查询。这使得子 AI 智能体在适应不同任务时更加得心应手。

8 Parallel tool calling transforms speed and performance. Complex research tasks naturally involve exploring many sources. Our early agents executed sequential searches，which was painfully slow. For speed，we introduced two kinds of parallelization：(1）the lead agent spins up 3-5 subagents in parallel rather than serially;（2）the subagents use 3+ tools in parallel. These changes cut research time by up to 90% for complex queries，allowing Research to do more work in minutes instead of hours while covering more information than other systems.

并行工具调用（Parallel tool calling）显著提升了速度和性能。复杂的研究任务通常需要探索多个信息来源。我们早期的 AI 智能体（AI Agent）采用的是顺序搜索方法，其过程慢得令人难以忍受。为了提升速度，我们引入了两种并行化（parallelization）机制：(1）主智能体可以并行派生出 3-5 个子智能体，而非串行处理；(2）这些子智能体可以并行使用 3 个及以上的工具。这些改进使得处理复杂查询时的研究时间缩短了高达 90%，让 Research 系统能够在几分钟内（而非数小时）完成更多工作，并且覆盖的信息量也超过了其他系统。

Our prompting strategy focuses on instilling good heuristics rather than rigid rules. We studied how skilled humans approach research tasks and encoded these strategies in our prompts—strategies like decomposing difficult questions into smaller tasks，carefully evaluating the quality of sources，adjusting search approaches based on new information，and recognizing when to focus on depth（investigating one topic in detail）vs. breadth（exploring many topics in parallel). We also proactively mitigated unintended side effects by setting explicit guardrails to prevent the agents from spiraling out of control. Finally，we focused on a fast iteration loop with observability and test cases.

我们的提示策略侧重于培养良好的启发式方法（heuristics），而非死板的规则。我们研究了经验丰富的人们如何进行研究工作，并将这些策略融入到我们的提示设计中：例如，将复杂问题分解为更小的任务，仔细评估信息来源的质量，根据新信息调整搜索方法，以及判断何时应该专注于深度（即详细调研某一课题）与广度（即同时探索多个课题）。我们还通过设置明确的「护栏」(guardrails）来主动防范和减轻潜在的负面影响，以防止 AI 智能体（AI Agent）的行为失控。最后，我们专注于建立一个包含可观察性（observability）和测试用例（test cases）的快速迭代循环。

### 04. Effective evaluation of agents

AI 智能体的有效评估

Good evaluations are essential for building reliable AI applications，and agents are no different. However，evaluating multi-agent systems presents unique challenges. Traditional evaluations often assume that the AI follows the same steps each time：given input X，the system should follow path Y to produce output Z. But multi-agent systems don't work this way. Even with identical starting points，agents might take completely different valid paths to reach their goal. One agent might search three sources while another searches ten，or they might use different tools to find the same answer. Because we don't always know what the right steps are，we usually can't just check if agents followed the「correct」steps we prescribed in advance. Instead，we need flexible evaluation methods that judge whether agents achieved the right outcomes while also following a reasonable process.

要构建可靠的 AI 应用，良好的评估方法至关重要，AI 智能体（AI Agent）也不例外。然而，评估多智能体系统（multi-agent systems）会带来一些独特的挑战。传统的评估方法通常假定，AI 在每次运行时都会遵循相同的步骤：即给定输入 X，系统就应该沿着路径 Y 产生输出 Z。但多智能体系统并非如此运作。即便起点完全相同，不同的 AI 智能体也可能选择截然不同但同样有效的路径来达成目标。例如，一个 AI 智能体可能检索三个信息来源，而另一个则可能检索十个；它们也可能使用不同的工具来找到同一个答案。因为我们往往无法预知什么是「正确」的步骤，所以通常不能简单地检查 AI 智能体是否遵循了我们预设的「正确」步骤。因此，我们需要更灵活的评估方法，这些方法不仅要判断 AI 智能体是否取得了预期的成果，还要看其执行过程是否合理。

Start evaluating immediately with small samples. In early agent development，changes tend to have dramatic impacts because there is abundant low-hanging fruit. A prompt tweak might boost success rates from 30% to 80%. With effect sizes this large，you can spot changes with just a few test cases. We started with a set of about 20 queries representing real usage patterns. Testing these queries often allowed us to clearly see the impact of changes. We often hear that AI developer teams delay creating evals because they believe that only large evals with hundreds of test cases are useful. However，it's best to start with small-scale testing right away with a few examples，rather than delaying until you can build more thorough evals.

不妨从少量样本开始，立刻着手评估。在早期 AI 智能体（AI Agent）开发中，由于有大量「唾手可得的成果」(low-hanging fruit）—— 也就是那些很容易就能获得的改进点 —— 一些小小的改动往往就能带来翻天覆地的变化。比如，对提示（prompt）做一点微调，就可能让成功率从 30% 一下子飙升到 80%。当改进的效果如此显著时，即便只用几个测试用例，你也能轻松捕捉到这些积极的改变。我们团队一开始就是这么做的，选取了大约 20 个能够代表真实用户使用场景的查询。通过对这些查询进行测试，我们常常能清晰地看到每一个调整所带来的实际影响。我们经常听到一些 AI 开发团队迟迟不愿建立 evals（评估体系），因为他们固执地认为，只有那些包含数百个测试用例的大规模 evals 才真正有效。然而，更明智的做法是立刻从小规模测试和几个简单示例入手，而不是非要等到能建立起更全面的 evals 之后再行动。

LLM-as-judge evaluation scales when done well. Research outputs are difficult to evaluate programmatically，since they are free-form text and rarely have a single correct answer. LLMs are a natural fit for grading outputs. We used an LLM judge that evaluated each output against criteria in a rubric：factual accuracy（do claims match sources?），citation accuracy（do the cited sources match the claims?），completeness（are all requested aspects covered?），source quality（did it use primary sources over lower-quality secondary sources?），and tool efficiency（did it use the right tools a reasonable number of times?). We experimented with multiple judges to evaluate each component，but found that a single LLM call with a single prompt outputting scores from 0.0-1.0 and a pass-fail grade was the most consistent and aligned with human judgements. This method was especially effective when the eval test cases did have a clear answer，and we could use the LLM judge to simply check if the answer was correct（i.e. did it accurately list the pharma companies with the top 3 largest R&D budgets?). Using an LLM as a judge allowed us to scalably evaluate hundreds of outputs.

让大语言模型（LLM）担当「裁判」的角色进行评估，如果运用得当，可以很好地实现规模化。科研成果通常是自由格式的文本，很少只有一个标准答案，因此很难通过程序自动评估。大语言模型天然适合对这类成果进行打分。我们让大语言模型「裁判」根据一套评分细则来评估每一项成果，具体标准包括：事实准确性（即提出的观点是否与参考文献一致？），引用准确性（即引用的文献是否真的支持相关观点？），完整性（即是否涵盖了所有要求分析的方面？），来源质量（即是否优先使用了高质量的一手来源（primary sources）而不是质量较低的二手来源（secondary sources）？），以及工具效率（即是否以合理的次数使用了正确的工具？）。我们尝试过让多个「裁判」分别评估成果的不同方面，但后来发现，通过单次调用大语言模型，使用同一个提示词（prompt），让它直接输出 0.0 到 1.0 之间的分数以及一个「通过 / 不通过」的等级，这种方式结果最为稳定，也最接近人类的判断。当评估的测试用例确实有明确答案时，这种方法尤其有效。比如，我们可以让大语言模型「裁判」简单地检查答案是否正确（例如，它是否准确列出了研发预算排名前三的制药公司？）。通过让大语言模型担当「裁判」，我们能够对海量的成果进行大规模评估。

Human evaluation catches what automation misses. People testing agents find edge cases that evals miss. These include hallucinated answers on unusual queries，system failures，or subtle source selection biases. In our case，human testers noticed that our early agents consistently chose SEO-optimized content farms over authoritative but less highly-ranked sources like academic PDFs or personal blogs. Adding source quality heuristics to our prompts helped resolve this issue. Even in a world of automated evaluations，manual testing remains essential.

人工评估能够发现自动化过程遗漏的问题。测试 AI 智能体（AI Agent）的人员会发现评估过程中未能覆盖的边缘案例（edge cases）。这些问题包括：对于罕见查询产生的幻觉答案（hallucinated answers）、系统故障，或是微妙的来源选择偏见。在我们的案例中，人工测试员注意到，我们早期的 AI 智能体总是倾向于选择那些经过 SEO 优化的内容农场，而不是那些更权威但搜索引擎排名可能靠后的来源，例如学术论文的 PDF 文件或个人博客。通过在我们的提示（prompts）中加入来源质量的启发式规则（heuristics），我们成功解决了这个问题。因此，即便在自动化评估日益普及的今天，人工测试仍然是必不可少的。

Multi-agent systems have emergent behaviors，which arise without specific programming. For instance，small changes to the lead agent can unpredictably change how subagents behave. Success requires understanding interaction patterns，not just individual agent behavior. Therefore，the best prompts for these agents are not just strict instructions，but frameworks for collaboration that define the division of labor，problem-solving approaches，and effort budgets. Getting this right relies on careful prompting and tool design，solid heuristics，observability，and tight feedback loops. See the open-source prompts in our Cookbook for example prompts from our system.

多智能体系统（Multi-agent systems）有一种非常有趣的特性，那就是会产生所谓的「涌现行为（emergent behaviors）」，这些行为的出现，并不是研发人员通过一行行代码精确编写出来的。举个例子，如果我们只对领头的那个智能体（也就是「领导智能体」）做一点小小的调整，它手下的那些「子智能体」们的行为就可能会发生一些我们完全预料不到的变化。要想让这样的系统成功运作，关键在于深入理解它们之间是如何互动、如何相互影响的（即「交互模式（interaction patterns）」），而不仅仅是盯着单个智能体在做什么。

因此，要让这些 AI 智能体（AI Agent）发挥出最佳效果，我们给出的「提示（prompts）」就不能仅仅是些刻板的指令。更好的方式是为它们搭建一个「协作框架（frameworks for collaboration）」，这个框架需要清晰地规划好谁负责什么（即「劳动分工（division of labor）」）、遇到问题该怎么解决（即「解决问题的方法（problem-solving approaches）」），以及每个部分大致需要投入多少精力（即「努力预算（effort budgets）」）。要把这些都恰到好处地落实，需要我们精心设计提示和相关工具，运用可靠的「启发式方法（heuristics）」(可以理解为一些经验法则或者有效的捷径），保证系统状态的「可观察性（observability）」(即能清楚地了解系统内部发生了什么），并且建立起快速有效的「反馈循环（tight feedback loops）」。想看看我们系统中实际使用的提示是什么样的吗？可以参考我们「Cookbook」(一个汇集了实用方法和示例的资源库）里提供的开源示例。

[anthropic-cookbook/patterns/agents/prompts at main · anthropics/anthropic-cookbook](https://github.com/anthropics/anthropic-cookbook/tree/main/patterns/agents/prompts)

### 05. Production reliability and engineering challenges

生产可靠性与工程挑战

In traditional software，a bug might break a feature，degrade performance，or cause outages. In agentic systems，minor changes cascade into large behavioral changes，which makes it remarkably difficult to write code for complex agents that must maintain state in a long-running process.

在传统软件中，一个小小的 bug 就可能让某个功能失灵，导致性能下降，甚至造成服务中断。然而，在 AI 智能体系统（agentic systems）里，情况更为复杂：即便是细微的调整，也可能像多米诺骨牌一样，连锁触发系统行为发生巨大的变化。这就使得为那些需要在长时间运行的进程中持续维护自身状态的复杂 AI 智能体（complex agents）编写代码，变得异常困难。

Agents are stateful and errors compound. Agents can run for long periods of time，maintaining state across many tool calls. This means we need to durably execute code and handle errors along the way. Without effective mitigations，minor system failures can be catastrophic for agents. When errors occur，we can't just restart from the beginning：restarts are expensive and frustrating for users. Instead，we built systems that can resume from where the agent was when the errors occurred. We also use the model's intelligence to handle issues gracefully：for instance，letting the agent know when a tool is failing and letting it adapt works surprisingly well. We combine the adaptability of AI agents built on Claude with deterministic safeguards like retry logic and regular checkpoints.

AI 智能体（AI Agent）是有状态的（stateful），这意味着它们的运行会记录历史信息，因此错误也容易不断累积。AI 智能体可以长时间运行，并在多次工具调用后依然保持其内部状态。这就要求我们必须能够持久地执行代码，并在此过程中妥善处理各种错误。如果没有有效的缓解措施（mitigations），即便是微小的系统故障，对 AI 智能体而言也可能是灾难性的。当错误发生时，我们不能简单地从头开始重启：因为重启不仅代价高昂，还会让用户感到非常沮丧。为此，我们构建的系统能够在 AI 智能体发生错误的地方直接恢复（resume）运行。我们还会利用模型本身的智能来巧妙地处理这些问题：例如，当某个工具调用失败时，我们会让 AI 智能体知晓这一情况并允许它自行调整适应，这种方法的效果出奇地好。我们将基于 Claude 构建的 AI 智能体的这种适应能力，与诸如重试逻辑（retry logic）和定期检查点（regular checkpoints）等确定性保障措施（deterministic safeguards）有机地结合起来。

Debugging benefits from new approaches. Agents make dynamic decisions and are non-deterministic between runs，even with identical prompts. This makes debugging harder. For instance，users would report agents「not finding obvious information,」but we couldn't see why. Were the agents using bad search queries? Choosing poor sources? Hitting tool failures? Adding full production tracing let us diagnose why agents failed and fix issues systematically. Beyond standard observability，we monitor agent decision patterns and interaction structures—all without monitoring the contents of individual conversations，to maintain user privacy. This high-level observability helped us diagnose root causes，discover unexpected behaviors，and fix common failures.

调试工作正从新的方法中受益。AI 智能体（Agents）会做出动态决策，并且即使面对相同的提示（prompts），它们在不同运行之间的表现也并非一成不变，即具有非确定性（non-deterministic）。这就使得调试工作变得更加困难。举个例子，用户可能会报告 AI 智能体「没有找到显而易见的信息」，但我们却难以捉摸其背后的原因。究竟是 AI 智能体使用了不佳的搜索查询（search queries)？还是选择了质量不高的信息来源？亦或是遭遇了工具故障？通过引入全面的生产环境追踪（production tracing）技术，我们得以诊断出 AI 智能体失败的具体原因，并系统性地解决这些问题。在标准的可观测性（observability）措施之外，我们还进一步监控 AI 智能体的决策模式（decision patterns）和交互结构（interaction structures）—— 这一切都是在不监控个体对话内容、以全力保护用户隐私的前提下进行的。这种高层级的可观测性，能有效地帮助我们洞察问题的根本原因（root causes），及时发现那些意料之外的行为模式，并修复常见的故障。

Deployment needs careful coordination. Agent systems are highly stateful webs of prompts，tools，and execution logic that run almost continuously. This means that whenever we deploy updates，agents might be anywhere in their process. We therefore need to prevent our well-meaning code changes from breaking existing agents. We can't update every agent to the new version at the same time. Instead，we use rainbow deployments to avoid disrupting running agents，by gradually shifting traffic from old to new versions while keeping both running simultaneously.

软件系统的部署工作需要周密的协调。AI 智能体（AI Agent）系统就像一个高度依赖当前状态的复杂网络，这个网络由各种提示（prompts）、工具（tools）以及预设的执行逻辑（execution logic）交织而成，并且几乎不间断地运行着。这就意味着，当我们着手部署更新时，这些 AI 智能体可能正处在其工作流程的任何一个环节。因此，我们必须小心翼翼，避免我们出于好意进行的代码更改反而破坏了那些正在运行的 AI 智能体。我们不可能在同一时间将所有的 AI 智能体都升级到新版本。为此，我们采用了一种叫做「彩虹部署」(rainbow deployments）的策略。这种方法能够确保正在运行的 AI 智能体不受干扰，它通过逐步将用户流量从旧版本引导至新版本，同时让新旧两个版本并行运行一段时间来实现平稳过渡。

Synchronous execution creates bottlenecks. Currently，our lead agents execute subagents synchronously，waiting for each set of subagents to complete before proceeding. This simplifies coordination，but creates bottlenecks in the information flow between agents. For instance，the lead agent can't steer subagents，subagents can't coordinate，and the entire system can be blocked while waiting for a single subagent to finish searching. Asynchronous execution would enable additional parallelism：agents working concurrently and creating new subagents when needed. But this asynchronicity adds challenges in result coordination，state consistency，and error propagation across the subagents. As models can handle longer and more complex research tasks，we expect the performance gains will justify the complexity.

同步执行会造成瓶颈。目前，我们的主 AI 智能体（AI Agent）是同步执行子 AI 智能体（AI Agent）的，也就是说，它会等待每一组子智能体完成任务后，才会继续下一步。这种方式虽然简化了协调工作，但在智能体之间的信息流动中却造成了瓶颈。例如，主智能体无法有效引导子智能体，子智能体之间也无法相互协调，甚至整个系统都可能因为等待某一个子智能体完成搜索任务而卡住。

异步执行则能实现额外的并行处理（parallelism)：各个智能体可以同时工作，并在需要时创建新的子智能体。但这种异步方式也给跨子智能体的结果协调（result coordination）、状态一致性（state consistency）以及错误传播（error propagation）带来了新的挑战。考虑到模型能够处理更长、更复杂的研究任务，我们相信这种方式带来的性能提升，足以证明克服这些新增的复杂性是值得的。

### Conclusion

结论

When building AI agents，the last mile often becomes most of the journey. Codebases that work on developer machines require significant engineering to become reliable production systems. The compound nature of errors in agentic systems means that minor issues for traditional software can derail agents entirely. One step failing can cause agents to explore entirely different trajectories，leading to unpredictable outcomes. For all the reasons described in this post，the gap between prototype and production is often wider than anticipated.

在构建 AI 智能体（AI agents）的过程中，那「最后一公里」往往才是最漫长的征途。那些在开发者电脑上运行良好的代码库，需要投入巨大的工程努力，才能转变成稳定可靠的生产系统。在 AI 智能体系统中，错误的累积效应（compound nature of errors）意味着，传统软件里的一些小问题，就可能让 AI 智能体彻底「翻车」。任何一个环节的失误，都可能导致 AI 智能体走向完全不同的行为路径，最终产生无法预料的后果。正如我们在这篇文章中探讨的种种原因，从原型到实际投产的鸿沟，往往比我们想象的要宽得多。

Despite these challenges，multi-agent systems have proven valuable for open-ended research tasks. Users have said that Claude helped them find business opportunities they hadn't considered，navigate complex healthcare options，resolve thorny technical bugs，and save up to days of work by uncovering research connections they wouldn't have found alone. Multi-agent research systems can operate reliably at scale with careful engineering，comprehensive testing，detail-oriented prompt and tool design，robust operational practices，and tight collaboration between research，product，and engineering teams who have a strong understanding of current agent capabilities. We're already seeing these systems transform how people solve complex problems.

尽管存在这些挑战，多智能体系统（multi-agent systems）已经在开放式研究任务中展现出其宝贵的价值。许多用户反馈，Claude 不仅帮助他们发现了以往未曾考虑到的商业机会，还能协助他们梳理复杂的医疗保健方案，解决棘手的技术 bug，甚至通过揭示那些单凭他们自己难以发现的研究脉络，为他们节省了多达数天的工作时间。要让多智能体研究系统能够大规模可靠地运行，离不开精心的工程设计、全面的测试、细致入微的提示词与工具设计、稳健的运维实践，以及研究、产品和工程团队之间的紧密协作 —— 这些团队都需要对当前 AI 智能体（AI Agent）的能力有深刻的理解。我们已经看到，这类系统正在改变人们解决复杂难题的方式。

A [Clio](https://www.anthropic.com/research/clio)embedding plot showing the most common ways people are using the Research feature today. The top use case categories are developing software systems across specialized domains（10%），develop and optimize professional and technical content（8%），develop business growth and revenue generation strategies（8%），assist with academic research and educational material development（7%），and research and verify information about people，places，or organizations（5%). ### Acknowlegements

这是一张来自 [Clio](https://www.anthropic.com/research/clio) 的嵌入图（embedding plot），它清晰地展示了目前人们在使用其「研究」功能时最常见的几种方式。其中，排名前列的应用类别主要包括：针对特定专业领域开发软件系统（10%），撰写和优化专业性与技术性内容（8%），制定业务增长和营收策略（8%），辅助学术研究和教学材料的开发（7%），以及调研并核实关于人物、地点或机构的信息（5%）。

### 致谢

Written by Jeremy Hadfield，Barry Zhang，Kenneth Lien，Florian Scholz，Jeremy Fox，and Daniel Ford. This work reflects the collective efforts of several teams across Anthropic who made the Research feature possible. Special thanks go to the Anthropic apps engineering team，whose dedication brought this complex multi-agent system to production. We're also grateful to our early users for their excellent feedback.

由 Jeremy Hadfield、Barry Zhang、Kenneth Lien、Florian Scholz、Jeremy Fox 和 Daniel Ford 共同撰写。这项成果凝聚了 Anthropic 公司内部多个团队的集体智慧与努力，正是他们让「研究」这一功能得以实现。我们在此特别感谢 Anthropic 的应用工程团队，他们的不懈努力与奉献，才使得这个复杂的多智能体系统（multi-agent system）成功上线。同时，我们也由衷感谢早期用户们提供的宝贵反馈。

## Appendix

附录

Below are some additional miscellaneous tips for multi-agent systems.

以下是一些关于多智能体系统（multi-agent systems）的其他补充性小贴士。

End-state evaluation of agents that mutate state over many turns. Evaluating agents that modify persistent state across multi-turn conversations presents unique challenges. Unlike read-only research tasks，each action can change the environment for subsequent steps，creating dependencies that traditional evaluation methods struggle to handle. We found success focusing on end-state evaluation rather than turn-by-turn analysis. Instead of judging whether the agent followed a specific process，evaluate whether it achieved the correct final state. This approach acknowledges that agents may find alternative paths to the same goal while still ensuring they deliver the intended outcome. For complex workflows，break evaluation into discrete checkpoints where specific state changes should have occurred，rather than attempting to validate every intermediate step.

如何评估那些在多轮互动中不断改变环境状态的 AI 智能体（AI Agent）呢？这确实是个独特的挑战，尤其是当这些 AI 智能体修改的是会长期保留并影响后续对话的「持久状态」(persistent state）时。这和那些环境不会变的「只读型」(read-only）研究任务可不一样。在后一种任务里，AI 智能体的每一步操作都可能改变接下来环境的样子，这就产生了一系列复杂的连锁反应（dependencies），让传统的评估方法束手无策。

我们发现，与其一步步地分析 AI 智能体的行为，不如重点考察它最终达成的结果，也就是进行「最终状态评估」(end-state evaluation）。换句话说，我们不去判断 AI 智能体是否严格按照预设的流程操作，而是看它最终有没有达到正确的目标状态。这种方法的好处在于，它允许 AI 智能体采用不同的路径去实现同一个目标 —— 正所谓「殊途同归」，只要能确保它最终能带来我们期望的成果就行。

那么，如果任务流程特别复杂，又该怎么办呢？我们可以把评估过程拆分成若干个明确的「检查点」(checkpoints）。在这些关键节点上，我们会检查特定的状态变化是否如期发生，而不需要去验证过程中的每一个中间步骤。

Long-horizon conversation management. Production agents often engage in conversations spanning hundreds of turns，requiring careful context management strategies. As conversations extend，standard context windows become insufficient，necessitating intelligent compression and memory mechanisms. We implemented patterns where agents summarize completed work phases and store essential information in external memory before proceeding to new tasks. When context limits approach，agents can spawn fresh subagents with clean contexts while maintaining continuity through careful handoffs. Further，they can retrieve stored context like the research plan from their memory rather than losing previous work when reaching the context limit. This distributed approach prevents context overflow while preserving conversation coherence across extended interactions.

长时程对话管理。在实际应用中，AI 智能体（AI Agent）常常需要进行长达数百轮的对话，这就对上下文信息的管理策略提出了很高的要求。随着对话越来越长，标准的上下文窗口往往就不够用了，这时候就需要更智能的压缩技术和记忆机制来帮忙。我们为此设计了一些方法：AI 智能体会在完成一个阶段的工作后，把要点总结下来，存到外部记忆体中，然后再开始新的任务。当快要达到上下文长度限制时，AI 智能体还能「派生」出一个拥有全新、干净上下文的「子智能体」（subagent），并通过精心的「任务交接」来保证对话的连续性。不仅如此，它们还可以从记忆体中调取之前存好的信息（比如研究计划），这样就不会因为上下文满了而丢失重要的工作成果。这种「分布式」的处理方法，既能避免上下文信息过载，又能在长时间的互动中保持对话的连贯和流畅。

Subagent output to a filesystem to minimize the ‘game of telephone.' Direct subagent outputs can bypass the main coordinator for certain types of results，improving both fidelity and performance. Rather than requiring subagents to communicate everything through the lead agent，implement artifact systems where specialized agents can create outputs that persist independently. Subagents call tools to store their work in external systems，then pass lightweight references back to the coordinator. This prevents information loss during multi-stage processing and reduces token overhead from copying large outputs through conversation history. The pattern works particularly well for structured outputs like code，reports，or data visualizations where the subagent's specialized prompt produces better results than filtering through a general coordinator.

子智能体（Subagent）可以将输出内容直接保存到文件系统，以此来最大限度地减少「传话游戏」效应（信息在传递过程中失真）。对于特定类型的成果，子智能体的输出可以直接绕过主协调器，这样做既能保证信息的准确性（fidelity），又能提升处理效率（performance）。

我们不必强制要求子智能体将所有信息都通过领导智能体（lead agent）来传递，更好的方法是建立一套「产物」(artifact）机制。通过这种机制，专门负责特定任务的子智能体可以创建能够独立保存的输出内容。具体来说，子智能体会调用各种工具，把它们的成果先存放到外部系统里，然后只把一个轻量级的「地址牌」(reference）交回给协调器。

这种方式不仅能避免在多轮处理中出现信息丢失，还能有效减少因在对话历史中来回复制大量输出内容而产生的 Token 开销。这种模式尤其适合处理像代码、报告或数据可视化这类结构化的输出。因为在这种情况下，子智能体根据其量身定制的提示（prompt）所生成的结果，往往比经过通用协调器筛选后的效果更好。