## 20251210Claude-Opus-45-Saves-Tokens-White-House-Boosts-AI-Powered-Science

[Claude Opus 4.5 Saves Tokens, White House Boosts AI-Powered Science, Amazon Exposes Nova 2 Pro Checkpoints, and more...](https://www.deeplearning.ai/the-batch/issue-331/)

Dear friends,

If you have not yet built an agentic workflow, I encourage you to try doing so, using the simple recipe I'll share here! With a few lines of code, you can now build a highly autonomous, moderately capable, and highlyunreliable agent.

如果你还没有搭建过一个基于 AI 智能体（AI Agent）的工作流，我强烈建议你尝试一下，就按照我下面要分享的这个简单方法！只需要几行代码，你现在就能构建出一个高度自主、具备一定能力，但也非常不可靠的智能体。

The ability of frontier LLMs to carry out multiple steps autonomously makes this possible. Specifically, you can give an LLM a tool such as disk access (or web search), instruct it via a prompt to perform a high-level task such as creating a game and saving it as an HTML file (or carrying out deep research on a topic), and let it loose and see what it does.

前沿大语言模型（LLM）能够自主执行多步骤任务，这为实现上述功能提供了可能。具体而言，你可以为大语言模型提供诸如磁盘访问（或网络搜索）之类的工具，并通过提示词（Prompt）指令它去完成一项高级任务，例如开发一个游戏并保存为 HTML 文件（或对某个主题进行深入研究），然后放手让它自主执行，观察其具体行为。

Important caveat: Hardly any of today's many practical, commercially valuable agentic workflows were built usingthis simple approach. Today's agents need much more scaffolding — that is, code that guides its step-by-step actions — rather than just letting an LLM have access to some tools and fully autonomously decide what to do. Building a reliable agent today requires much more scaffolding to guide it; but as LLMs become more capable, we will see successful agents built with less scaffolding.

重要提示：在当今众多实用且具有商业价值的智能体工作流中，几乎没有一个是用这种简单方法构建的。如今的智能体需要更多的「脚手架」（scaffolding）—— 也就是引导其逐步执行动作的代码 —— 而不仅仅是让一个大语言模型（LLM）访问某些工具并完全自主地决定做什么。当前，要构建一个可靠的智能体，确实需要大量脚手架来引导它；但随着大语言模型（LLM）的能力不断增强，我们将看到用更少脚手架构建的成功智能体。

If you want to build practical agents, ourAgentic AIcourse is the best way to learn how. But you can still have fun playing with this simple but less practical recipe!

如果你想构建实用的 AI 智能体（AI Agent），我们的《智能体 AI 实战》课程无疑是最佳学习途径。不过，你依然可以试试下面这个简单（但实用性稍逊）的小方案，体验一下动手的乐趣！

A quick way to implement this recipe is to use the open sourceaisuitepackage (pip install "aisuite[all]") that Rohit Prasad and I have been working on. This package makes it easy to switch LLM providers and also to get an LLM to use tools (function calls) without needing to write a massive amount of code.

一个快速实现该方案的方法是使用开源 aisuite 包（pip install "aisuite[all]"），这是由 Rohit Prasad 和我共同开发的。这个包能轻松切换不同的大语言模型（LLM）提供商，还能让大语言模型使用各种工具（即函数调用），而无需编写大量代码。

[andrewyng/aisuite: Simple, unified interface to multiple Generative AI providers](https://github.com/andrewyng/aisuite)

Aisuite started as a weekend project when I was trying to solve my personal pain point of wanting an easy way to switch LLM providers. After building a workflow using a specific LLM, I often want to quickly try out alternatives to see if they perform better in accuracy, latency, or cost. Routing my LLM API calls through aisuite makes these swaps much easier. Manymembersof the open-source community have been contributing to this, and Rohit recently added MCP support, which makes it easy to build basic agentic workflows.

Aisuite 最初诞生于一个周末项目，当时我想解决一个个人痛点：找到一种简便的方法来切换不同的大语言模型（LLM）提供商。每当我用某个特定的大语言模型构建好一个工作流后，常常会想快速试试其他模型，看看它们在准确性、响应速度或成本上是否有更好的表现。通过 aisuite 来路由我的大语言模型 API 调用，使得这种切换变得轻松许多。开源社区的许多成员一直在为这个项目贡献力量，Rohit 最近还为其添加了 MCP 支持，这让构建基础的智能体工作流变得更加容易。

You can see the entirety of the code needed to generate a snake game in the image above, and access it inthisJupyter notebook. After writing a prompt instructing an LLM to create an HTML file with a snake game, the two steps are:

你可以在上图中看到生成贪吃蛇游戏所需的全部代码，并能在这个 Jupyter notebook 中访问它。在编写了一条指示大语言模型（LLM）创建包含贪吃蛇游戏的 HTML 文件的提示（prompt）后，后续的两个步骤是：

[aisuite/examples/agents/snake\_game\_generator.ipynb at main · andrewyng/aisuite](https://github.com/andrewyng/aisuite/blob/main/examples/agents/snake_game_generator.ipynb?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9QvwD_Bdg4CMnG8oEHire2Ym-kcJOmJ9O3601OIzEXOHm7XsaF99upB9irivgVl4JyuX-e)

1 Initialize the MCP-based file-system tool to let it write files.

初始化基于 MCP 的文件系统工具，使其能够写入文件。

2 Let loose a frontier model (such as GPT-5.1, Claude Sonnet 4.5, or Gemini 3).

部署一个前沿模型（例如 GPT-5.1、Claude Sonnet 4.5 或 Gemini 3）。

This(usually) results in the LLM creating a snake game and using the MCP server to save a file snake_game.html, which you can open in a web browser. (The parametermax_turns=5means that it will alternate between calling the LLM and letting the LLM execute a tool up to 5 times before exiting.)

这通常会让大语言模型创建一个贪吃蛇游戏，并通过 MCP 服务器保存一个名为 snake_game.html 的文件，你可以在网页浏览器中打开它。（参数 max_turns=5 意味着系统会在大语言模型推理和执行工具调用之间交替循环，最多进行 5 轮后结束。）

For another example, here's asecondnotebook that demonstrates giving an LLM access to a web search tool and letting it autonomously decide when and how much to search the web to compile a report or HTML dashboard on the weather in multiple cities or some other topic of your choice.

再举一个例子，这是第二个笔记本，它展示了如何让一个大语言模型（LLM）使用网络搜索工具，并允许其自主决定何时进行搜索以及搜索到什么程度，以便生成一份关于多个城市天气（或您选择的其他主题）的报告或 HTML 仪表板。

If you have not yet built an agent, I hope this simple recipe lets you build your first one. Please runpip install "aisuite[all]"and have fun!

如果你还没有构建过 AI 智能体（AI Agent），希望这份简单的指南能帮助你打造出第一个。请运行 `pip install「aisuite[all]"`，开始体验吧！

Keep building!
Andrew

继续加油！
Andrew

### News

#### Claude Does More With Fewer Tokens

Claude：事半功倍，效率非凡

Claude Opus 4.5, the latest version of Anthropic's flagship model, extends the earlier version's strengths in coding, computer use, and agentic workflows while generating fewer tokens.

Claude Opus 4.5 是 Anthropic 旗舰模型的最新版本，它在延续了早期版本于编码、计算机操作以及 AI 智能体（AI Agent）工作流方面优势的同时，生成的 Token 数量也更少。

What's new:Claude Opus 4.5outperforms its immediate predecessor at one-third the price per token.

新动态：Claude Opus 4.5 的性能超越了前代模型，而每个 Token 的价格仅为前代的三分之一。

1 Input/output:Text and images in (up to 200,000 tokens), text out (up to 64,000 tokens)

输入 / 输出：支持文本和图像输入（最多 200,000 个 Token），支持文本输出（最多 64,000 个 Token）。

2 Features:Adjustableeffort(low, medium, high)that governs token generation across responses, tool calls, and reasoning;extended thinkingthat raises the budget for reasoning tokens; tool use including web search andcomputer use

功能：

可调节的努力程度（Adjustable effort）：提供低、中、高三个级别，用于调控在生成回复、调用工具以及进行推理时所产生的 Token 数量。

扩展思考（Extended thinking）：增加分配给推理过程的 Token 预算，允许模型进行更深入的思考。

工具使用（Tool use）：支持包括网络搜索和计算机操作在内的多种工具调用。

3 Availability/price:Comes with Claudeapps(Pro, Max, Team, Enterprise subscriptions); API $5.00/$0.50/$25.00 per million input/cached/output tokens (plus cache storage costs) via Anthropic, Amazon Bedrock, Google Cloud Vertex AI, Microsoft Foundry

可用性与价格：随 Claude 应用（Pro、Max、Team、Enterprise 订阅版）提供；通过 Anthropic、Amazon Bedrock、Google Cloud Vertex AI 或 Microsoft Foundry 的 API 调用时，价格为每百万个输入 / 已缓存 / 输出 Token 5.00/0.50/25.00 美元（另需支付缓存存储费用）。

4 Undisclosed:Parameter count, architecture, training details

未披露：参数数量、架构、训练细节

How it works:Anthropic describes Claude Opus 4.5 as a hybrid reasoning model. Like Claude models since Claude Sonnet 3.7, it responds rapidly in its default mode or takes time to process reasoning tokens when extended thinking is enabled.

它是如何工作的：Anthropic 将 Claude Opus 4.5 描述为一个混合推理模型。与 Claude Sonnet 3.7 及后续的 Claude 模型类似，它在默认模式下会快速给出回应；而当启用深度思考功能时，它则需要额外的时间来生成推理内容。

1 Anthropic trained the model on public data scraped from the web and non-public data from third parties, paid contractors, Anthropic users who didn't opt out, and Anthropic's internal operations. The team fine-tuned the model to be helpful using reinforcement learning from human and AI feedback.

Anthropic 用于训练该模型的数据包括两部分：一部分是从网络上抓取的公开数据，另一部分是非公开数据，这些非公开数据来源于第三方、付费承包商、未选择退出的 Anthropic 用户以及 Anthropic 公司自身的内部运营。团队随后采用了基于人类和 AI 反馈的强化学习方法对模型进行微调，以提升其帮助能力。

2 Claude's consumer apps now automatically summarize earlier portions of conversations, enabling arbitrarilylong interactions.

Claude 的消费级应用现在能自动总结对话的前期内容，从而支持任意长度的对话交互。

Performance:In independenttestsperformed by Artificial Analysis, Claude Opus 4.5 excelled at coding tasks and performed near the top in other areas. In Anthropic's tests, it attained high performance while using tokens efficiently.

性能：在 Artificial Analysis 的独立测试中，Claude Opus 4.5 在编程任务上表现卓越，在其他领域也接近顶尖水平。在 Anthropic 自家的测试中，该模型在高效使用 Token 的同时，也实现了很高的性能。

1 On the Artificial Analysis Intelligence Index, a weighted average of 10 benchmarks, Claude Opus 4.5 (70) achieved a second-place score, matching OpenAI GPT-5.1 and trailing Google Gemini 3 Pro (73). In non-reasoning mode, it scored 60, highest among non-reasoning models tested. On theAA-Omniscience Index, which measures factual knowledge and tendency to fabricate information (higher is better), Claude Opus 4.5 (10) outperformed GPT-5.1 (2) but lagged behind Gemini 3 Pro Preview (13).

在人工智能分析指数（Artificial Analysis Intelligence Index）上，这是一个基于 10 项基准测试的加权平均分，Claude Opus 4.5 以 70 分位列第二，与 OpenAI GPT-5.1 分数相同，但落后于 Google Gemini 3 Pro（73 分）。在非推理模式下，其得分为 60 分，在所有测试的非推理模型中排名最高。在 AA 全知指数（AA-Omniscience Index）上，该指数用于衡量模型的事实知识掌握程度和捏造信息的倾向（分数越高越好），Claude Opus 4.5 得 10 分，表现优于 GPT-5.1（2 分），但不及 Gemini 3 Pro Preview（13 分）。

2 On Terminal-Bench Hard (command-line tasks), Claude Opus 4.5 (44 percent) outperformed all other models tested by Artificial Analysis.

在终端基准测试 Terminal-Bench Hard（命令行任务）上，Claude Opus 4.5 以 44% 的得分，表现超过了 Artificial Analysis 所测试的所有其他模型。

3 According to Anthropic, set to medium effort, Claude Opus 4.5 matched Sonnet 4.5's SWE-bench Verified performance while using 76 percent fewer output tokens. At high effort, it exceeded Sonnet 4.5 by 4.3 percentage points while using 48 percent fewer tokens.

根据 Anthropic 的数据，在中等资源模式下，Claude Opus 4.5 在 SWE-bench Verified 基准测试中的表现与 Sonnet 4.5 持平，但输出的 Token 数量减少了 76%。在高资源模式下，其表现更是超出 Sonnet 4.5 达 4.3 个百分点，同时 Token 使用量减少了 48%。

4 Using "parallel test-time compute" that included a 64,000-token thinking budget and high effort, Claude Opus 4.5 outperformed all people who have taken a two-hour engineering exam that Anthropic uses to test candidates.

通过采用「并行测试时计算」（parallel test-time compute）技术，并分配了高达 64,000 个 Token 的思考资源以及进行深度计算，Claude Opus 4.5 在 Anthropic 用于招聘甄选的两小时工程考试中，其表现超过了所有参加过该考试的人类应试者。

Behind the news:Generally, Claude Opus 4.5 generates fewer output tokens than competitors to achieve comparable results. To run the tests in the Artificial Analysis Intelligence Index, Claude Opus 4.5 (48 million tokens) used roughly half as many as Gemini 3 Pro set to high reasoning (92 million tokens) and GPT-5.1 set to high reasoning (81 million tokens). However, its higher per-token price amounts to higher overall costs than these competitors. Testing Claude Opus 4.5 cost $1,498, Gemini 3 Pro $1,201, and GPT-5.1 $859.

深度解析：总体而言，Claude Opus 4.5 在取得相当结果的同时，生成的输出 Token 数量要少于竞争对手。为了运行「人工智能分析指数（Artificial Analysis Intelligence Index）」中的测试，Claude Opus 4.5（消耗了 4800 万 Token）的使用量大约仅为 Gemini 3 Pro（9200 万 Token）和 GPT-5.1（8100 万 Token）的一半（后两者均设置为高推理模式）。然而，由于其更高的单 Token 价格，其总体成本反而高于这些竞争对手。此次测试的成本分别为：Claude Opus 4.5 为 1,498 美元，Gemini 3 Pro 为 1,201 美元，GPT-5.1 为 859 美元。

Why it matters:Claude Opus 4.5 arrives after a period in which Anthropic's mid-tier Sonnet 4.5 often approached or outperformed the older, more expensive Opus 4.1 in many benchmarks. For instance, on the Artificial Analysis Intelligence Index, Claude Sonnet 4.5 (63) exceeded Claude Opus 4.1 (59). The disparity disincentivized users to pay premium rates for Opus for some time. But Claude Opus 4.5 restores a clear hierarchy within the Claude family, with the top-tier model now 7 points ahead of its mid-tier sibling.

为何重要：Claude Opus 4.5 的发布，正值一个特殊时期 —— 在此期间，Anthropic 的中端模型 Claude Sonnet 4.5 在许多基准测试中的表现，经常接近甚至超越了更早发布、价格也更昂贵的 Claude Opus 4.1。例如，在 Artificial Analysis Intelligence Index 上，Claude Sonnet 4.5（63 分）的得分就超过了 Claude Opus 4.1（59 分）。这种性能差距一度削弱了用户为 Opus 版本支付更高费用的意愿。然而，Claude Opus 4.5 的推出，在 Claude 模型家族内部重新确立了清晰的等级划分，如今这款顶级模型在其基准得分上，已领先其中端版本达 7 分之多。

We're thinking:The difference in performance between various frontier models is shrinking. According to Stanford's latestAI Index, the gap between top-ranked and 10th-ranked models onLM Arena, measured by Elo rating, fell from 11.9 percent to 5.4 percent between 2024 and 2025. The gap between the top two shrank to 0.7 percent. As this trend continues, leaderboard differences are coming to matter less for many applications.

我们认为：各类前沿模型之间的性能差距正在不断收窄。根据斯坦福大学最新的 AI 指数（AI Index）报告，在 LM Arena 排行榜上，以 Elo 评分衡量，榜首模型与第十名模型之间的差距已从 2024 年的 11.9% 降至 2025 年的 5.4%。而前两名之间的差距更是缩小到了仅 0.7%。随着这一趋势的发展，对于许多实际应用而言，排行榜上的位次差异其重要性正在逐渐减弱。

#### White House Orders AI for Science

白宫推动人工智能赋能科学研究

President Trump launched a United States effort to use AI to speed up scientific breakthroughs.

特朗普总统启动了一项美国计划，旨在利用人工智能（AI）来加速科学突破。

What's new:The Genesis Mission, established by anexecutive order,directs the Department of Energy to integrate its 17 national labs and some of the country's most powerful supercomputers to tackle research on areas that range from energy to medicine. Government researchers will work with private-sector partners, including Anthropic, Nvidia, and OpenAI, to train models on proprietary federal datasets and use AI to generate and run experiments.

最新动态：根据一项行政命令，美国启动了名为「创世纪任务」（Genesis Mission）的计划。该计划指示能源部整合其下属的 17 个国家实验室以及国内部分最强大的超级计算机，以攻克从能源到医学等多个领域的科研难题。政府研究人员将与包括 Anthropic、Nvidia 和 OpenAI 在内的私营部门伙伴合作，利用联邦政府专有的数据集训练人工智能模型，并借助人工智能（AI）来设计和运行实验。

How it works:The Energy Department will create an AI platform that provides access to government data and enables federal agencies, research labs, and companies to collaborate in building scientific foundation models and AI agents. It will also organize prize competitions, fellowships, partnerships, and funding opportunities that bring these communities together, coordinating diverse government, academic, and private resources that typically remain separate during peacetime. The project is the "largest marshaling of federal scientific resources since the Apollo program," Michael Kratsios, head of the White House Office of Science and Technology Policy,toldBloomberg.

运作方式：能源部将创建一个 AI 平台（AI platform），用于提供政府数据访问权限，并支持联邦机构、研究实验室与企业协同构建科学基础模型和 AI 智能体。此外，该平台还将通过组织有奖竞赛、设立研究基金、建立合作伙伴关系以及提供资金支持等方式，汇聚上述各界力量，协调在和平时期通常各自为政的政府、学术界和私营部门资源。白宫科技政策办公室主任迈克尔·克拉齐奥斯（Michael Kratsios）向彭博社表示，该项目是「自阿波罗计划以来，联邦科学资源最大规模的一次动员」。

1 Automation:The goal is to train AI models to conceive and conduct scientific research using robotic labs that allow for varying degrees of human involvement.

自动化：其目标是训练 AI 模型，使其能够构想科学研究方案，并利用机器人实验室来执行这些研究，整个过程中人类可以参与其中，但参与程度可以灵活调整。

2 Focus:The mission identifies six areas of research focus: biotechnology, manufacturing, materials, nuclear fission, quantum information science, and semiconductors.

重点领域：该使命明确了六个重点研究方向：生物技术、制造、材料、核裂变、量子信息科学和半导体。

3 Goals:The project aims to (i) boost the pace of scientific discovery, (ii) protect national security, (iii) find paths to lower-cost energy, and (iv) increase the return on government investment for taxpayers.

目标：该项目旨在（i）加快科学发现进程，(ii）保障国家安全，(iii）探寻低成本能源路径，以及（iv）提高政府投资对纳税人的回报。

4 Funding:No new funding has been allocated so far, as is standard with U.S. executive orders. Agencies will start with existing resources, and Congress may approve additional spending.

资金：目前尚未拨付新的专项资金，这符合美国行政命令的惯例。相关机构将先利用现有资源开展工作，国会后续或可批准追加拨款。

5 Nvidia will build 7 new supercomputers for the government labs, CEO Jensen Huangsaid, and AMD, Dell, and Nvidia have agreed to build new facilities within the government labs,The New York Timesreported.

据《纽约时报》报道，英伟达（Nvidia）首席执行官黄仁勋（Jensen Huang）表示，该公司将为政府实验室建造 7 台新的超级计算机。此外，AMD、戴尔（Dell）和英伟达也已同意在政府实验室内建造新的设施。

Behind the news:In scientific research, AI is evolving from a passive tool into an active collaborator that can manage the cycle of scientific discovery from hypothesis to results.

新闻背后：在科学研究领域，人工智能（AI）正在从一种被动的工具，演变为能主动协作的伙伴，它能够驾驭从提出假设到得出结果的完整科学发现周期。

1 Google'sAI co-scientist, a multi-agent system designed to generate in-depth research proposals, has demonstrated its capability to generate novel proposals for biomedical research. It identified drug candidates to repurpose for leukemia and liver fibrosis that were subsequently validated in labs.

Google 的 AI 科研助手（一个多智能体系统）能够生成深入的研究提案，并已证明其可为生物医学领域提出创新方案。该系统识别出一些可用于白血病和肝纤维化治疗的候选药物（即老药新用），这些药物的疗效随后在实验室中获得了验证。

2 AI Scientist, an agentic workflow that directs large language models to generate ideas for AI research, produce code to test them, and document the enquiry, showcased the ability of LLMs to produce AI research papers by ideating, testing, and documenting experimental results.

AI Scientist 是一种智能体工作流，它引导大语言模型（LLMs）生成人工智能研究想法、编写测试代码并记录研究过程。该工作流展示了 LLMs 能够通过构思想法、进行实验测试和记录结果，最终完成 AI 研究论文的撰写。

3 RoboChem, an integrated robotic lab developed by the University of Amsterdam, outperformed human chemists in optimizing chemical synthesis, boosting yield and throughput in experimental runs. In earlier work, researchers at the University of Liverpool trained amobile robot armto navigate a lab, operate equipment, handle samples, and obtain results far faster than a human scientist.

RoboChem，一个由阿姆斯特丹大学开发的一体化机器人实验室，在优化化学合成方面的表现优于人类化学家，显著提高了实验运行的产量和通量（throughput）。在更早的研究中，利物浦大学的研究人员训练了一个移动机器人手臂在实验室内自主移动、操作设备、处理样品，其获取结果的速度远超人类科学家。

4 AI-powered search engines like Consensus and Scitestreamlinethe ability to find and summarize scientific literature by synthesizing vast amounts of peer-reviewed research.

由人工智能（AI）驱动的搜索引擎，例如 Consensus 和 Scitestreamline，能够通过综合分析海量的同行评审研究，来提升用户查找和总结科学文献的效率。

Yes, but:The Genesis Mission depends on data, yet the federal government has systematically degraded its capacity to collect it. The White House has cut funding for weather data collection by the National Oceanic and Atmospheric Administration, suspended collection of health data by the Centers for Disease Control and Prevention, and shut down several facilities responsible for gathering and curating government data,Politicoreported. Lack of large, current datasets could blunt both AI and humanity's ability to understand the world.

话虽如此：「起源计划」（Genesis Mission）的成功依赖于数据，但联邦政府却在系统性地削弱自身的数据收集能力。据 Politico 报道，白宫削减了国家海洋和大气管理局（NOAA）用于气象数据收集的预算，暂停了疾病控制与预防中心（CDC）的卫生健康数据收集工作，并关停了数个负责政府数据收集与管理的机构。缺乏大规模、时效性强的数据集，不仅会制约人工智能的发展，也会妨碍人类对世界的认知。

Why it matters:The U.S. push to apply AI to scientific research and coordinate federal, academic, and private resources is a direct response to the investment and advances China has been making in AI, officials said. China is making strides in many areas of science and technology including quantum computing and battery technology, according to the Center for Strategic and International Studies, a nonpartisan think tank. For the AI industry, the Genesis Mission's plan to launch competitions and other financial incentives to participate in new research efforts related to strategic goals and security is encouraging.

其重要性在于：据官员称，美国推动将人工智能（AI）应用于科学研究，并协调联邦、学术界和私营部门的资源，旨在直接应对中国在 AI 领域的投资与进展。根据无党派智库战略与国际研究中心（CSIS）的说法，中国在量子计算、电池技术等诸多科技领域正取得长足进步。对 AI 行业而言，Genesis Mission 计划发起竞赛并提供其他资金激励，以吸引各方参与同战略目标及安全相关的新研究工作，这一举措令人鼓舞。

We're thinking:Autonomous systems that produce, vet, and execute research ideas have shown intriguing progress. With adequate funding and access to data, a partnership between industry, academia, and the Department of Energy presents an exciting opportunity to accelerate it.

我们的设想是：能够自主生成、评估并执行研究想法的自主系统（Autonomous Systems）已展现出引人注目的进展。在资金充足且数据可及的条件下，产业界、学术界与美国能源部携手合作，将为加速这一进程带来激动人心的机遇。

#### Amazon Steps Forward

亚马逊迈出新步伐

Amazon raised the competitive profile of its foundation models and added services for custom model training and an agent platform for browser automation.

亚马逊增强了其基础模型（Foundation Model）的竞争力，并新增了两项服务：一项用于定制化模型训练，另一项则是用于浏览器自动化的 AI 智能体（Agent）平台。

What's new:TheNova 2family of models covers multimodal reasoning, multimodal generation, and speech to speech. Early access to top-of-the-line Nova 2 Pro Preview (multimodal in, text out) and Nova 2 Omni Preview (multimodal in and out) are available via newNova Forge($100,000 annually), a new service that offers pre-trained, mid-trained, and post-trained Nova checkpoints, enabling customers to mix proprietary data with Amazon's datasets. In addition, Amazon launchedNova Act, a service for building browser-automation agents that can navigate websites, fill out forms, extract data, and interact with the web via natural language or Python code. (Disclosure: Andrew Ng serves on Amazon's board of directors.)

新动态：Nova 2 模型系列涵盖了多模态推理、多模态生成以及语音到语音转换。现在，通过全新的 **Nova Forge** 服务（年费 10 万美元），即可抢先体验其旗舰型号：支持多模态输入、文本输出的 Nova 2 Pro Preview，以及支持多模态输入与输出的 Nova 2 Omni Preview。Nova Forge 提供预训练、中期训练及后期训练阶段的 Nova 模型检查点（checkpoints），客户可借此将自己的专有数据与亚马逊的数据集结合使用。此外，亚马逊还发布了**Nova Act**服务，用于构建能自动操作浏览器的 AI 智能体。这些智能体可以导航网站、填写表单、提取数据，并通过自然语言或 Python 代码与网页进行交互。（披露：吴恩达（Andrew Ng）在亚马逊董事会任职。）

Nova 2 Pro Preview:The latest flagship Nova model,Nova 2 Pro Previewrivals models from Anthropic, Google, and OpenAI on selected benchmarks.

Nova 2 Pro 预览版：作为最新的旗舰 Nova 模型，Nova 2 Pro 预览版在部分基准测试中的表现，可与 Anthropic、Google 及 OpenAI 的模型一较高下。

* Input/output:Text, images, video, speech in (up to 1 million tokens), text out.

* 输入 / 输出：文本、图像、视频、语音（最多 100 万个 Token ），文本输出。

* Features:Adjustable reasoning levels (low, medium, high), code interpreter via API that runs and evaluates Python code within the same workflow, web grounding via API that retrieves publicly available information with citations, offered as teacher for model distillation viaAmazon Bedrock Model Distillation

* 功能：支持可调节的推理强度（低、中、高）；提供基于 API 的代码解释器，可在同一工作流内运行并评估 Python 代码；具备基于 API 的联网搜索与引用功能，可检索并引用公开信息；此外，该模型还可通过 Amazon Bedrock 的模型蒸馏（Model Distillation）服务，充当教师模型用于知识蒸馏。

* Performance:In Amazon's tests, Nova 2 Pro Preview performed equal to or better than Anthropic Claude Sonnet 4.5 on 10 of 16 benchmarks, equal to or better than Google Gemini 3 Pro Preview on 8 of 16 benchmarks, equal to or better than OpenAI GPT-5.1 on 8 of 18 benchmarks. On Artificial Analysis' Intelligence Index, a weighted average of 10 benchmarks, Nova 2 Pro Preview set to medium reasoning (62) and without reasoning (42) outperformed the earlier Nova Premier (32) but fell short of current leader Gemini 3 Pro Preview (73). On the 𝜏²-Bench Telecom test of agentic behavior, Nova 2 Pro Preview (93 percent) tied for first place with with Grok 4.1 Fast and Kimi K2 Thinking. On the IFBench test of following instructions, Nova 2 Pro Preview (79 percent outperformed GPT 5.1 set to high reasoning (73 percent) and MiniMax-M2 (72 percent). Artificial Analysis has not yet tested Nova 2 Pro Preview on high reasoning.

* 性能：根据亚马逊的测试结果，Nova 2 Pro Preview 在多项基准测试中表现优异。具体来说，在 16 项测试中，它有 10 项表现持平或超越了 Anthropic 的 Claude Sonnet 4.5；在另一组 16 项测试中，有 8 项表现持平或优于 Google 的 Gemini 3 Pro Preview；而在 18 项测试中，有 8 项表现持平或优于 OpenAI 的 GPT-5.1。在 Artificial Analysis 的 Intelligence Index（一项基于 10 个基准的加权平均指数）上，Nova 2 Pro Preview 在中等推理模式（62）和基础模式（42）下的得分均超越了前代产品 Nova Premier（32），但低于当前的领先者 Gemini 3 Pro Preview（73）。在专注于评估 AI 智能体（AI Agent）行为的 𝜏²-Bench Telecom 测试中，Nova 2 Pro Preview 以 93% 的得分与 Grok 4.1 Fast 和 Kimi K2 Thinking 并列榜首。在测试指令遵循能力的 IFBench 中，Nova 2 Pro Preview（79%）的表现优于设置为高推理模式的 GPT 5.1（73%）以及 MiniMax-M2（72%）。不过，Artificial Analysis 尚未对 Nova 2 Pro Preview 的高推理模式进行测试。

* Price:$1.25/$0.31/$10 per million input/cached/output tokens via AmazonNova Forge

*  价格：通过 AmazonNova Forge 平台，每百万输入（input）/ 缓存（cached）/ 输出（output）Token 的价格分别为 1.25 美元、0.31 美元和 10 美元。

Nova 2 Lite:The lightweightNova 2 Liteis designed to be a fast, cost-effective reasoning model. Performance is equivalent to or better than that of Anthropic Claude Haiku 4.5, Google Gemini Flash 2.5, and OpenAI GPT-5 Mini on most benchmarks tested. $0.3/$0.03/$2.50 per million input/cached/output tokens via Amazon Bedrock.

Nova 2 Lite：这款轻量级的 Nova 2 Lite 旨在成为一个快速且高性价比的推理模型。在大多数基准测试中，其性能与 Anthropic Claude Haiku 4.5、Google Gemini Flash 2.5 以及 OpenAI GPT-5 Mini 相当甚至更优。通过 Amazon Bedrock 平台使用，其价格为每百万输入 / 缓存 / 输出 Token 0.3 美元 / 0.03 美元 / 2.50 美元。

Nova 2 Omni Preview:Nova 2 Omni Previewis the only widely available reasoning modelthat natively takes in text, images, video, and speech(up to 1 million tokens, text in over 200 languages, speech in 10 languages) and generates text and images. $0.30/$0.03 per million input/cached text, image, and video tokens; $1.00/$0.10 per million input/cached audio tokens; $2.50/$40 per million output text/image tokens via AmazonNova Forge.

Nova 2 Omni 预览版：Nova 2 Omni 预览版是目前唯一广泛可用的多模态推理模型。它原生具备处理多种信息的能力：可以接收文本、图像、视频和语音作为输入（最高支持 100 万个 Token（Token），文本涵盖超过 200 种语言，语音支持 10 种语言），并能够生成文本和图像。其通过 Amazon Nova Forge 平台提供的计价方式如下：
*  对于输入的文本、图像和视频 Token，每百万 Token 收费 0.30 美元；若为缓存调用，则每百万 Token 收费 0.03 美元。
*  对于输入的音频 Token，每百万 Token 收费 1.00 美元；若为缓存调用，则每百万 Token 收费 0.10 美元。
*  对于输出的文本 Token，每百万 Token 收费 2.50 美元；对于输出的图像 Token，每百万 Token 收费 40 美元。

Nova 2 Sonic:The speech-to-speech modelNova 2 Sonicis multilingual in 7 languages and calls tools without interrupting conversation. In Amazon'stests, users preferred Nova 2 Sonic to GPT Realtime and Gemini 2.5 Flash in most of its 7 languages. $3/$12 per million input/output speech tokens, $0.33/$2.75 per million input/output text tokens via Amazon Bedrock. The modelintegrateswith Amazon Connect and third-party telephony providers including AudioCodes, Twilio, and Vonage.

Nova 2 Sonic 是一款语音转语音（Speech-to-Speech）模型，支持 7 种语言，并且能在不中断对话的情况下调用外部工具。根据亚马逊的内部测试，在这 7 种语言中的大多数场景下，用户对 Nova 2 Sonic 的偏好度超过了 GPT Realtime 和 Gemini 2.5 Flash。该模型通过 Amazon Bedrock 平台提供服务，其计费方式为：语音 Token 每百万个输入 / 输出收费 3 美元 / 12 美元；文本 Token 每百万个输入 / 输出收费 0.33 美元 / 2.75 美元。此外，Nova 2 Sonic 能够与 Amazon Connect 以及 AudioCodes、Twilio 和 Vonage 等第三方电话服务提供商进行集成。

Why it matters:The Nova 2 family fills a gap in Amazon's model portfolio. Until now, the company lacked reasoning models with adjustable thinking levels that would compete with offerings from Anthropic, Google, and OpenAI. In addition, Nova Forge is exciting and significantly different from offerings by Amazon's AI competitors, and browser automation via Nova Act is a powerful addition to Amazon Bedrock's agentic capabilities.

为什么这很重要：Nova 2 系列填补了亚马逊模型产品线的一个关键空白。此前，亚马逊一直缺少能够与 Anthropic、Google 和 OpenAI 产品竞争的、具备可调节推理复杂度的模型。此外，Nova Forge 的设计令人耳目一新，与亚马逊其他 AI 竞争对手的解决方案有显著区别。同时，通过 Nova Act 实现的浏览器自动化功能，也为亚马逊 Bedrock 平台的智能体（Agent）能力提供了一个强大的补充。

We're thinking:Amazon's foundation models have lagged behind those of competitors. Nova 2's higher performance relative to its predecessors suggests that Amazon is serious about closing the gap.

我们的看法是：亚马逊的基础模型已落后于竞争对手。而 Nova 2 相比前代产品性能显著提升，这表明亚马逊正致力于缩小这一差距。

#### Small Models Solve Hard Puzzles

小模型破解复杂谜题

Large language models often fail at puzzles like Sudoku, for which a solution includes multiple elements and a single mistake invalidates all of them. Researchers showed that a tiny network, by repeatedly refining its solution, can solve this sort of puzzle well.

大语言模型（Large Language Model）在处理诸如数独这类谜题时常常表现不佳。这类谜题的解答包含多个步骤，任何一个步骤出错都会导致整个解答失败。研究人员发现，一个微型网络通过不断迭代、修正其解答，能够很好地解决此类谜题。

What's new:Alexia Jolicoeur-Martineau at Samsung developedTiny Recursive Model(TRM). This approach outperforms large, pretrained LLMs, including DeepSeek-R1 and Gemini 2.5 Pro, on visual puzzles that require filling in a grid by inferring an abstract rule based on limited information, specifically Sudoku, Maze, and current ARC-AGI benchmarks.

新进展：三星公司的研究员 Alexia Jolicoeur-Martineau 开发了一种名为 Tiny Recursive Model（TRM）的模型。在解决一类特定的视觉推理谜题时，TRM 的表现超越了包括 DeepSeek-R1 和 Gemini 2.5 Pro 在内的大型预训练大语言模型。这类谜题要求根据有限信息推断出抽象规则，并据此填充网格，例如数独、迷宫以及当前用于评估通用人工智能（AGI）的 ARC-AGI 基准测试。

Key insight:Training a neural network to refine a solution iteratively can take place in 3 steps: (i) Give it a random solution and tell it to compute a solution, (ii) feed back the output, compute a new solution, and so on, and (iii) backpropagate through this recursive process so the network learns to produce a more accurate solution through iteration. However, this approach has a key flaw: The network doesn't keep track of the changes it has made, so during inference, from iteration to iteration, it may undo changes that improved the solution. To counteract this problem, the network can produce a separate context embedding that also feeds back with each iteration. This tactic enables it to learn to store any information that helps to improve performance, such as changes it has made, without needing an explicit loss function that's designed to accomplish this.

核心思路：训练神经网络进行迭代优化可以分三步走：(i）输入一个随机初始解，让网络计算出一个解决方案；(ii）将这个输出作为反馈，再计算新的解决方案，如此循环往复；(iii）对此递归过程进行反向传播，从而使网络学会通过迭代生成更精确的解决方案。然而，这种方法存在一个关键缺陷：网络不会记录自己所做的修改，因此在推理时，迭代过程中可能会无意间撤销那些原本能提升解决方案的有效改动。为了解决这个问题，网络可以生成一个独立的上下文嵌入（context embedding），并让这个嵌入也参与到每次迭代的反馈中。这一策略使得网络能够学会存储任何有助于提升性能的信息（例如它已做出的修改），而无需专门设计一个用于实现此目标的显式损失函数。

How it works: A TRM is a 2-layer network whose architecture depends on the type of puzzle to be solved. The authors used a 5 million-parameter vanilla neural network to learnSudoku-Extreme, whose solutions are 9x9 matrices, and 7 million-parameter transformers to learnMaze-Hard,ARC-AGI-1andARC-AGI-2, which involve 30x30 matrices. Solving these puzzles requires logic, pathfinding, and visual reasoning at 2 levels of difficulty respectively.

工作原理：TRM（Token Reduction Module）是一个双层网络，其具体架构取决于所需解决的谜题类型。作者使用了一个拥有 500 万参数的标准神经网络（vanilla neural network）来学习 Sudoku-Extreme，该谜题的答案是一个 9x9 矩阵；同时，他们使用了 700 万参数的 Transformer 模型来学习 Maze-Hard、ARC-AGI-1 和 ARC-AGI-2，这些谜题则涉及 30x30 矩阵。解决这些谜题分别需要两种不同难度级别的能力：逻辑能力、路径寻找能力以及视觉推理能力。

* During training, given a puzzle (represented as tokens), solution tokens (random at first), and a context embedding (random at first), the network iterated for up to 16 cycles.

* 在训练过程中，网络会接收一个谜题（以 token 序列表示）、初始为随机的答案 token 以及初始为随机的上下文嵌入，并进行最多 16 轮的迭代。

* Within each cycle, it recursively updated the context embedding 18 times. Each update consisted of a forward pass through the network.

* 在每一个周期中，它会反复更新上下文嵌入（context embedding）18 次。每一次更新，都对应着一次网络的前向传播过程。

* Each cycle included one more forward pass to produce an improved solution. The model learned to minimize the error between the improved solution and ground truth, and to classify correct solutions. If it recognized a correct solution, it stopped the process.

*  每个循环会多进行一次前向传播，以生成一个优化后的解。模型的学习目标是：最小化这个优化解与真实值之间的误差，并学会判断一个解是否正确。一旦模型识别出正确的解，它就会终止整个过程。

* During inference, given a puzzle, the network went through the same steps to produce a solution.

* 在推理阶段，给定一个谜题后，网络会遵循相同的步骤来生成一个解。

Results:TRM outperformed the earlierHierarchical Reasoning Model (HRM)(27 million parameters) as well as pretrained LLMs.

结果：TRM 的表现优于早期的分层推理模型（HRM，参数为 2700 万）以及预训练的大语言模型。

* On Sudoku-Extreme and Maze-Hard, TRM (87.4 and 85.3 percent accuracy) exceeded HRM (55 and 74.5 percent accuracy). Anthropic Claude Sonnet 3.7, DeepSeek-R1, and OpenAI o3-mini set to high reasoning achieved 0 percent accuracy.

* 在 Sudoku-Extreme 和 Maze-Hard 这两个测试中，TRM 的准确率（分别为 87.4% 和 85.3%）超过了 HRM（分别为 55% 和 74.5%）。而 Anthropic Claude Sonnet 3.7、DeepSeek-R1 以及采用高推理强度设置的 OpenAI o3-mini，其准确率均为 0%。

* On ARC-AGI-1, TRM (44.6 percent pass@2) came out behind xAI Grok 4 with thinking mode enabled (66.7 percent pass@2) but ahead of HRM (40.3 percent pass@2), Gemini 2.5 Pro (37 percent pass@2), and Claude Sonnet 3.7 with thinking mode enabled (28.6 percent pass@2).

* 在 ARC-AGI-1 基准测试中，TRM 模型以 44.6% 的 pass@2 得分位列第二。它的表现落后于启用了思考模式（thinking mode）的 xAI Grok 4（66.7% pass@2），但优于 HRM（40.3% pass@2）、Gemini 2.5 Pro（37% pass@2）以及同样启用了思考模式的 Claude Sonnet 3.7（28.6% pass@2）。

* Similarly, on the more-challenging ARC-AGI-2 benchmark, TRM (7.8 percent pass@2) underperformed Grok 4 with thinking mode enabled (16.0 percent pass@2) but outperformed HRM (5.0 percent accuracy), Gemini 2.5 Pro (4.9 percent pass@2), and Claude Sonnet 3.7 with thinking mode enabled (0.7 percent pass@2).

* 类似地，在更具挑战性的 ARC-AGI-2 基准测试上，TRM（7.8% pass@2）的表现落后于启用了思考模式的 Grok 4（16.0% pass@2），但领先于 HRM（5.0% 准确率）、Gemini 2.5 Pro（4.9% pass@2）以及启用了思考模式的 Claude Sonnet 3.7（0.7% pass@2）。

Why it matters:A tiny model excels at solving puzzles that requiremultifaceted solutions to be perfectly correct. Training a simple — but specialized — architecture can be more effective and efficient than raw scale.

其重要性在于：一个微型模型，却擅长解决那些需要综合性方案才能完美答对的难题。这表明，训练一个简单但高度专门化的模型架构，其效率和效果可能优于一味追求扩大模型规模。

We're thinking:LLMs reason by generating a chain of thought, one model executionat a time, before the final output. On the other hand, TRM reasons by recursively updating its context embedding, one model execution at a time, before the final output.

我们的思路是这样的：大语言模型（Large Language Model，LLM）的推理方式是生成一个思维链（Chain of Thought），这个过程需要多次执行模型（每次执行一步推理），最终才得出结果。而 TRM 模型的推理方式，则是通过递归地更新其上下文嵌入（Context Embedding）来实现，同样需要多次执行模型（每次执行一次更新），最终得出输出。
