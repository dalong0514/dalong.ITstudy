## 20250416Google-Unveils-Gemini-25-MCP-Gains-Momentum

[Google Unveils Gemini 2.5, MCP Gains Momentum, Behind Sam Altman’s Fall and Rise, and more...](https://www.deeplearning.ai/the-batch/issue-297/)

Dear friends,

I've noticed that many GenAI application projects put in automated evaluations（evals）of the system's output probably later — and rely on humans to manually examine and judge outputs longer — than they should. This is because building evals is viewed as a massive investment（say，creating 100 or 1,000 examples，and designing and validating metrics）and there's never a convenient moment to put in that up-front cost. Instead，I encourage teams to think of building evals as an iterative process. It's okay to start with a quick-and-dirty implementation（say，5 examples with unoptimized metrics）and then iterate and improve over time. This allows you to gradually shift the burden of evaluations away from humans and toward automated evals.

我注意到，在许多生成式 AI（GenAI）应用项目中，自动化评估（evals）系统输出的工作往往被放到了项目后期 —— 并且，相较于理想情况，人们更长时间地依赖人工手动检查和判断输出。这是因为大家普遍认为构建评估是一项巨大的投资（比如，创建 100 或 1,000 个示例，以及设计和验证指标），而且似乎总没有一个「方便」的时机来投入这笔前期成本。相反，我鼓励大家将构建评估视为一个迭代的过程。从一个「快速且不完美」的实现开始是可以的（比如，先用 5 个示例和一些初步的指标），然后随着时间的推移不断迭代和改进。这样，你就可以逐渐将评估的负担从人工转移到自动化评估上。

I wrote previously about the importance and difficulty of creating evals. Say you're building a customer-service chatbot that responds to users in free text. There's no single right answer，so many teams end up having humans pore over dozens of example outputs with every update to judge if it improved the system. While techniques like LLM-as-judge are helpful，the details of getting this to work well（such as what prompt to use，what context to give the judge，and so on）are finicky to get right. All this contributes to the impression that building evals requires a large up-front investment，and thus on any given day，a team can make more progress by relying on human judges than figuring out how to build automated evals.

我之前写过关于创建评估的重要性和难度。假设你正在构建一个客户服务聊天机器人，它可以以自由文本的形式回应用户。由于没有唯一的正确答案，许多团队最终需要人类仔细检查数十个示例输出，并在每次更新时判断系统是否有所改进。虽然像 LLM-as-judge 这样的技术确实很有帮助，但让其良好运行的细节（例如使用什么提示，给 judge 什么上下文等等）很难掌握。所有这些都造成了这样一种印象，即构建评估需要大量的前期投入，因此在给定的时间里，一个团队通过依赖人类 judge 比弄清楚如何构建自动化评估可以取得更大的进展。

I encourage you to approach building evals differently. It's okay to build quick evals that are only partial，incomplete，and noisy measures of the system's performance，and to iteratively improve them. They can be a complement to，rather than replacement for，manual evaluations. Over time，you can gradually tune the evaluation methodology to close the gap between the evals' output and human judgments. For example:

我鼓励你换个角度来构建评估。构建快速评估是可行的，即使这些评估对于衡量系统性能来说，只是部分、不完整且包含噪音的衡量指标。而且这些评估可以迭代地改进。它们可以作为手动评估的补充，而不是替代品。随着时间的推移，你可以逐步调整评估方法，以缩小评估结果与人类判断之间的差距。例如：

1 It's okay to start with very few examples in the eval set，say 5，and gradually add to them over time — or subtract them if you find that some examples are too easy or too hard，and not useful for distinguishing between the performance of different versions of your system.

在评估集中最初只使用少量例子也是可以的，比如 5 个，并随着时间的推移逐渐增加。如果你发现有些例子太容易或太难，对于区分系统不同版本性能没有帮助，也可以减少它们。

2 It's okay to start with evals that measure only a subset of the dimensions of performance you care about，or measure narrow cues that you believe are correlated with，but don't fully capture，system performance. For example if，at a certain moment in the conversation，your customer-support agent is supposed to（i）call an API to issue a refund and（ii）generate an appropriate message to the user，you might start off measuring only whether or not it calls the API correctly and not worry about the message. Or if，at a certain moment，your chatbot should recommend a specific product，a basic eval could measure whether or not the chatbot mentions that product without worrying about what it says about it.

一开始的评估可以只衡量你所关注性能维度的部分指标，或者只衡量那些你认为与系统整体性能相关，但并不能完全涵盖所有方面的「窄线索」。例如，如果在对话的特定时刻，你的客服智能体需要（i）调用 API 来发起退款，并且（ii）生成一条恰当的消息给用户，你可以先只评估它是否正确调用了 API，而不必过于关注生成的消息内容。或者，如果在某个时刻，你的聊天机器人应该推荐某个特定产品，一个基础的评估可以衡量聊天机器人是否提及了该产品，而不去深究它关于该产品的具体描述。

So long as the output of the evals correlates with overall performance，it's fine to measure only a subset of things you care about when starting.

所以只要评估的结果与整体性能相关，在项目初期只衡量你所关心的部分指标是可行的。

The development process thus comprises two iterative loops，which you might execute in parallel:

因此，开发过程包含两个迭代循环，你可以并行进行：

1 Iterating on the system to make it perform better，as measured by a combination of automated evals and human judgment;

迭代系统以提升其表现，通过自动化评估和人类判断的结合来衡量；

2 Iterating on the evals to make them correspond more closely to human judgment.

迭代评估使其更紧密地贴合人类判断。

As with many things in AI，we often don't get it right the first time. So t's better to build an initial end-to-end system quickly and then iterate to improve it. We're used to taking this approach to building AI systems. We can build evals the same way.

与 AI 领域的许多事情类似，我们常常无法一步到位。因此，更好的方法是快速构建一个初步的端到端系统，然后通过迭代不断改进。我们已经习惯于用这种方式来构建 AI 系统，同样也可以用它来构建评估体系。

To me，a successful eval meets the following criteria. Say，we currently have system A，and we might tweak it to get a system B:

在我看来，一个成功的评估应该符合以下标准。比如说，我们现在有一个系统 A，然后我们可能会对其进行一些调整，得到系统 B：

1 If A works significantly better than B according to a skilled human judge，the eval should give A a significantly higher score than B.

如果 A 在一位经验丰富的人类评判员看来明显优于 B，那么评估结果也应该显示 A 的得分显著高于 B。

2 If A and B have similar performance，their eval scores should be similar.

如果 A 和 B 具有相似的性能，它们的评估分数应该相似。

Whenever a pair of systems A and B contradicts these criteria，that is a sign the eval is in「error」and we should tweak it to make it rank A and B correctly. This is a similar philosophy to error analysis in building machine learning algorithms，only instead of focusing on errors of the machine learning algorithm's output — such as when it outputs an incorrect label — we focus on「errors」of the evals — such as when they incorrectly rank two systems A and B，so the evals aren't helpful in choosing between them.

每当一对系统 A 和 B 违反这些标准时，这表明评估存在「错误」，我们应该调整它，使其正确地对 A 和 B 进行排名。这与构建机器学习算法中的错误分析方法类似，不同之处在于我们关注的不是机器学习算法输出的错误（例如，当它输出错误的标签时），而是评估的「错误」（例如，当它们错误地对两个系统 A 和 B 进行排名时，导致评估无法帮助我们在两者之间做出选择）。

Relying purely on human judgment is a great way to get started on a project. But for many teams，building evals as a quick prototype and iterating to something more mature lets you put in evals earlier and accelerate your progress.

完全依靠人工判断是开启一个项目的绝佳方式。但对于许多团队来说，将评估构建成一个快速原型，然后逐步迭代完善，可以让你更早地引入评估，从而加速你的进展。

Keep building!

Andrew

### News

#### Google Unveils Gemini 2.5

Google 公布 Gemini 2.5

Google's new flagship model raised the state of the art in a variety of subjective and objective tests.

Google 的新旗舰模型在各种主观和客观测试中达到了新的技术高度。

What's new: Google launched Gemini 2.5 Pro Experimental，the first model in the Gemini 2.5 family，and announced that Gemini 2.5 Flash，a version with lower latency，will be available soon. All Gemini 2.5 models will have reasoning capabilities，as will all Google models going forward.

最新消息：Google 推出了 Gemini 2.5 Pro Experimental，这是 Gemini 2.5 系列中的第一个模型，并宣布低延迟版本 Gemini 2.5 Flash 也将很快推出。所有 Gemini 2.5 模型都将具有推理能力，Google 未来所有模型也将如此。

1 Input/output: Text，audio，images，video in（up to 1 million tokens，up to 2 million tokens announced but not yet available），text out（up to 65,000 tokens, 212.7 tokens per second，26.8 seconds to first token)

输入 / 输出：支持输入文本、音频、图像和视频（目前最多支持 100 万个 token，已宣布将支持 200 万个 token，但尚未可用）；输出文本（最多支持 65,000 个 token，输出速度为每秒 212.7 个 token，首个 token 输出延迟为 26.8 秒）。

2 Performance: Currently tops Chatbot Arena

性能：目前位居 Chatbot Arena 榜首

3 Availability/price: Limited free access via Google Cloud，Google AI Studio, Vertex AI，and Gemini app and website. API $1.25/$10 per million tokens input/output up to 200,000 tokens，$2.50/$15 per million tokens input/output above 200,000 tokens.

可用性 / 价格：通过 Google Cloud，Google AI Studio，Vertex AI，以及 Gemini 应用和网站提供有限的免费访问。API 价格为每百万 token 输入 / 输出，对于不超过 200,000 token 的上下文窗口，价格为 $1.25/$10；对于超过 200,000 token 的上下文窗口，价格为 $2.50/$15。

4 Features: Reasoning，web search，code execution

功能：推理（Reasoning），网页搜索，代码执行

5 Undisclosed: Architecture，parameter count，training methods，training data

未披露：架构，参数数量，训练方法，训练数据

How it works: Compared to Gemini 1.0 and Gemini 1.5，Google disclosed little information about Gemini 2.5 Pro Experimental or how it differs from previous versions.

工作原理：相比 Gemini 1.0 和 Gemini 1.5，Google 关于 Gemini 2.5 Pro Experimental 以及它与之前版本有何不同，公布了很少的信息。

1 Like Gemini 2.0 Flash Thinking，Gemini 2.5 Pro Experimental is trained using reinforcement learning to generate reasoning tokens before responding to prompts. It hides such tokens but provides more general reasoning traces.

和 Gemini 2.0 Flash Thinking 类似，Gemini 2.5 Pro Experimental 也是利用强化学习来训练的，目的是让它在回答用户提问之前，先「思考」一下（生成推理 Token）。这些「思考过程」生成的 Token 虽然被隐藏起来了，但模型会提供更笼统的推理过程，让用户了解它是如何得出答案的。

2 Google said Gemini 2.5 Pro Experimental uses a「significantly enhanced」base model and「improved」post-training but didn't provide details.

Google 表示，Gemini 2.5 Pro Experimental 采用了「显著增强」的基础模型和「改进的」后训练（post-training），但没有提供具体细节。

3 Gemini 2.5 Pro improves on Gemini 2.0 Pro's coding abilities and performs well on SWE-Bench Verified，a benchmark that evaluates agentic coding. Google didn't specify details on the coding agent used for these tests，calling it a「custom agent setup.」

Gemini 2.5 Pro 在 Gemini 2.0 Pro 的编码能力基础上有所提升，并在 SWE-Bench Verified 基准测试中表现出色，该基准用于评估 AI 智能体（AI Agent）的编码能力。Google 没有详细说明用于这些测试的编码 AI 智能体的具体信息，称其为「定制的 AI 智能体设置（custom agent setup）」。

Results: On a variety of popular benchmarks，Gemini 2.5 Pro Experimental outperforms top models from competing AI companies.

结果：在一系列流行基准测试中，Gemini 2.5 Pro Experimental 表现优于其他 AI 公司的顶级模型。

1 As of this writing，in the Chatbot Arena，a head-to-head competition in which human users choose the best response between two anonymous models，Gemini 2.5 Pro Experimental（1437 Elo）tops the leaderboard ahead of OpenAI GPT-4o 2025-03-26（1406 Elo）and xAI Grok 3 Preview（1402 Elo).

截至本文撰写时，在 Chatbot Arena（一项由人类用户在两个匿名模型中选择最佳回复的对决竞赛）中，Gemini 2.5 Pro Experimental （1437 Elo）在排行榜上名列榜首，领先于 OpenAI GPT-4o 2025-03-26（1406 Elo）和 xAI Grok 3 Preview （1402 Elo）。

2 Across 12 benchmarks，on seven of them，Gemini 2.5 Pro Experimental outperformed OpenAI o3-mini（set to high effort），OpenAI GPT-4.5，Anthropic Claude 3.7 Sonnet（64,000 extended thinking），xAI Grok 3 Beta（extended thinking），and DeepSeek-R1.

在 12 项基准测试中，Gemini 2.5 Pro Experimental 在其中七项上表现出色，超越了设置为高努力的 OpenAI o3-mini、OpenAI GPT-4.5、具备 64,000 扩展思维能力的 Anthropic Claude 3.7 Sonnet、拥有扩展思维能力的 xAI Grok 3 Beta，以及 DeepSeek-R1。

Why it matters: Late last year，some observers expressed concerns that progress in AI was slowing. Gemini 2.5 Pro Experimental arrives shortly after rival proprietary models GPT-4.5（currently a research preview）and Claude 3.7 Sonnet，both of which showed improved performance，yet it outperforms them on most benchmarks. Clearly there's still room for models — particularly reasoning models — to keep getting better.

重要意义：去年底，一些观察者曾担忧 AI 的发展正在放缓。Gemini 2.5 Pro Experimental 在其竞争对手专有模型 GPT-4.5（目前为研究预览版）和 Claude 3.7 Sonnet 发布后不久推出，尽管这两个模型都展示了性能提升，但 Gemini 2.5 Pro Experimental 在大多数基准测试中表现更优。显然，模型，尤其是推理模型，仍有持续进步的空间。

We're thinking: Google said it plans to train all its new models on chains of thought going forward. This follows a similar statement by OpenAI. We're sure they have their reasons!

我们注意到：Google 表示，未来计划在其所有新模型中都加入对思维链（chains of thought）的训练。这与 OpenAI 之前发布的类似声明不谋而合。我们相信这两家公司这样做都有各自的考量！

#### Open Standard for Tool Use and Data Access Gains Momentum

工具使用和数据访问的开放标准获得动力

OpenAI embraced Model Context Protocol，providing powerful support for an open standard that connects large language models to tools and data.

OpenAI 支持模型上下文协议，为连接大语言模型到工具和数据的开放标准提供了强大支持。

What's new: OpenAI will support Model Context Protocol (MCP）in its Agents SDK and soon its ChatGPT desktop app and Responses API. The move will give developers who use OpenAI models access to a wide variety of pre-existing tools and proprietary data sources.

最新进展：OpenAI 将在其 Agents SDK 中支持 Model Context Protocol（MCP），并且很快也会在 ChatGPT 桌面应用和 Responses API 中支持此协议。此举将使得使用 OpenAI 模型的开发者能够访问各种现有的工具和专有数据源。

How it works: Launched by Anthropic late last year，MCP connects AI models to a growing ecosystem of plug-and-play resources，including more than 6,000 community-built servers and connectors.

工作原理：MCP 是 Anthropic 于去年底推出的一个平台，它将 AI 模型连接到一个日益壮大的即插即用资源生态系统，这个生态系统目前包含 6,000 多个由社区构建的服务器和连接器。

1 MCP defines clients and servers. Servers expose tools and data sources that LLMs can use. Clients like Claude for Desktop or agents built using the OpenAI Agents SDK interact with servers.

MCP 定义了客户端和服务器。服务器会提供工具和数据源，供大语言模型使用。客户端，例如 Claude for Desktop 或使用 OpenAI Agents SDK 构建的 AI 智能体，则与这些服务器进行交互。

2 Servers define tools such as internet search or file system manipulation，and users can download and run them locally or connect to servers hosted by third parties. In their code，users simply tell the client where the server(s）are running. Given a prompt，a model，behind the scenes, will retrieve a list of tools available from all servers，decide which to use，call them，and formulate and return responses.

服务器定义了一些工具，比如互联网搜索或者文件系统操作。用户可以把这些工具下载到本地运行，也可以连接到第三方提供的服务器。在他们的代码里，用户只需要告诉客户端服务器的地址就行。当接收到一个提示后，模型会在后台自动获取所有服务器上可用的工具列表，然后决定使用哪个工具，调用这些工具，最后组织并返回响应。

Behind the news: Momentum behind MCP has built rapidly. Last month，Microsoft integrated MCP into CoPilot Studio，enabling developers to build agents with access to MCP servers. Cloudflare enabled its customers to deploy remote MCP servers. In February，the AI-powered code editor Cursor enabled users to add MCP servers.

新闻背后：MCP 的发展势头迅猛。上个月，Microsoft 将 MCP 集成到 CoPilot Studio 中，使开发者能够构建可访问 MCP 服务器的 AI 智能体（AI Agent）。Cloudflare 使其客户能够部署远程 MCP 服务器。二月份，AI 驱动的代码编辑器 Cursor 支持用户添加 MCP 服务器。

Why it matters: OpenAI's move will make it easier for developers who use its models to connect to a variety of tools and data sources，and it helps to establish MCP as a go-to protocol for building agentic applications. Instead of figuring out manually how to integrate various providers，developers can connect to a third-party server（or download and run it themselves）and tie it into existing workflows with a few lines of code.

Why it matters：OpenAI 的此举将使得使用其模型的开发者更容易连接到各种工具和数据源，并有助于将 MCP 确立为构建 AI 智能体应用的首选协议。开发者无需手动配置如何与各种提供商集成，而是可以连接到第三方服务器（或下载并自己运行），并通过几行代码将其轻松整合到现有工作流程中。

We're thinking: Kudos to Anthropic，OpenAI，and other competitors who realize it's better to solve shared problems together than fragment the industry.

我们认为：值得为 Anthropic、OpenAI 和其他竞争对手点赞，他们认识到与其让行业各自为政，不如一起解决共同面临的问题。

#### The Fall and Rise of Sam Altman

Sam Altman 的陨落与崛起

A behind-the-scenes account provides new details about the abrupt firing and reinstatement of OpenAI CEO Sam Altman in November 2023.

一篇幕后报道披露了关于 OpenAI 首席执行官 Sam Altman 在 2023 年 11 月被突然解雇又迅速复职的更多细节。

How it works: Based on insider accounts，an excerpt from a forthcoming book about OpenAI by Wall Street Journal reporter Keach Hagey describes conflicts，accusations，and shifting alliances that led to Altman's brief ouster and rapid return.

详情：根据内部人士的说法，《华尔街日报》记者 Keach Hagey 即将出版的关于 OpenAI 的书中有一部分内容，描述了导致 Altman 短暂离职并很快回归的冲突、指控和复杂的各方关系。

Firing and reinstatement: OpenAI's board of directors came to distrust Altman but failed to persuade executives and employees that he should be replaced.

Firing and reinstatement：OpenAI 的董事会开始不信任 Altman，但未能说服高管和员工他应该被替换。

1 In winter 2022，Altman told the board that the company's joint safety committee with Microsoft had approved three「somewhat controversial」enhancements to GPT-4. Board member Helen Toner later learned that only one had been approved.

在 2022 年冬天，Altman 告诉董事会，公司与 Microsoft 共同成立的安全委员会已经批准了对 GPT-4 的三项「有点争议」的增强功能。董事会成员 Helen Toner 后来得知只有一项获得了批准。

2 Altman also failed to tell the board that Microsoft had tested GPT-4 in India without the committee's approval.

奥特曼也未告知董事会，Microsoft 未经委员会批准，在印度测试了 GPT-4。

3 Board members were surprised to learn that Altman personally owned the $175 million OpenAI Startup Fund，so OpenAI investors wouldn't see any profits. Altman claimed he didn't benefit from the fund.

董事会成员惊讶地得知奥特曼个人拥有价值 1.75 亿美元的 OpenAI 创业基金，这意味着 OpenAI 的投资者将无法从中获得任何利润。奥特曼声称他并未从该基金中获益。

4 CTO Mira Murati expressed doubts about Altman's leadership to other board members. Murati，Toner，and co-founder Ilya Sutskever began to document his actions.

CTO Mira Murati 向其他董事会成员表达了对 Altman 领导能力的怀疑。Murati、Toner 和联合创始人 Ilya Sutskever 开始记录他的行为。

5 On November 16，the board voted to fire Altman and appoint Murati interim CEO. The board members were reluctant to reveal why they'd fired Altman. At one meeting，Murati and other executives gave them 30 minutes to either explain why they fired Altman，resign，or watch the executive team quit. Nearly all OpenAI employees（including Murati and Sutskever）signed a letter threatening to quit if Altman wasn't reinstated，and the board reversed its decision.

11 月 16 日，董事会投票决定解雇 Altman 并任命 Murati 为临时 CEO。董事会成员不愿透露他们解雇 Altman 的原因。在一次会议上，Murati 和其他高管给了他们 30 分钟时间，要求他们要么解释解雇 Altman 的原因，要么辞职，否则就看着高管团队辞职。几乎所有 OpenAI 员工（包括 Murati 和 Sutskever）签署了一封信，威胁说如果 Altman 不复职就辞职，董事会撤销了决定。

Aftermath: Since Altman's return，Murati and all but one director who voted to remove him have left OpenAI. The issues that precipitated his departure have given way to commercial concerns as the company considers a shift from its current hybrid nonprofit/for-profit structure to fully for-profit.

后续：自从 Altman 回归后，Murati 和投票罢免他的董事中除了一位之外的所有董事都离开了 OpenAI。此前导致他离职的问题已经让位于商业考量，因为该公司正在考虑从目前的非营利与营利混合结构完全转变为营利模式。

1 GPT-5 will arrive「in the next few months,」according to Altman.

据 Altman 称，GPT-5 将在「未来几个月内」与大家见面。

2 Meanwhile，OpenAI launched GPT-4.1 (making full，mini，and nano versions available via API）and confirmed it soon would release o3，a new reasoning model.

此外，OpenAI 推出了 GPT-4.1（通过 API 提供完整、迷你和纳米等多种版本），并确认很快就会发布一个全新的推理模型 —— o3。

3 OpenAI said it will release its first open model，a new language model with open weights，in coming months.

OpenAI 表示将在未来几个月发布其首个开放模型，一个新的具有开放权重的语言模型。

4 The company recently raised $40 billion，the largest-ever funding round for an AI company，increasing its valuation to $300 billion.

该公司最近筹集了 400 亿美元，这是人工智能公司有史以来最大的一轮融资，使其估值达到 3000 亿美元。

Why it matters: The AI frontier spawns not only technical innovations but also intense interpersonal relationships and corporate politics. Such dynamics have consequences for users and the world at large：Having survived serious challenges to his leadership，Altman has emerged in a strong position to build a path of faster growth as a for-profit company upon OpenAI's philanthropic foundation.

重要意义：人工智能（AI）的前沿领域不仅带来了技术上的突破，也催生了复杂的人际关系和激烈的公司政治。这些因素的变化会对用户乃至整个世界产生深远影响：Altman 在经历了对其领导地位的严峻考验后，如今地位更加稳固，有望在 OpenAI 的慈善事业根基之上，带领公司走上更快速的商业化增长道路。

We're thinking: Given OpenAI's formidable achievements，Altman's renewed leadership marks an inflection point in the AI landscape. Without Sam Altman at the helm，OpenAI would be a very different company，with different priorities and a different future.

我们认为，鉴于 OpenAI 已经取得的非凡成就，Altman 的重新掌舵预示着人工智能领域的一个重要转折。没有 Sam Altman 这位关键人物领航，OpenAI 很可能会走向截然不同的发展道路，优先事项和未来图景都会大相径庭。

#### Toward LLMs That Understand Misspellings

让大语言模型更好地理解拼写错误

Researchers built a model that's more robust to noisy inputs like misspellings，smarter about character-level information like the number of R's in strawberry，and potentially better able to understand unfamiliar languages that might share groups of letters with familiar languages. Their approach：Eliminate the tokenizer and instead integrate a system that learns to group input characters.

研究人员构建了一个新的模型，它对于像拼写错误这样的干扰输入（噪声输入）更加不容易出错（更鲁棒）。这个模型在处理字符层面的信息时也更聪明，比如它能更好地理解「strawberry」中有多少个「R」。此外，它可能能更好地理解那些不熟悉的语言，即使这些语言只是和我们熟悉的语言有一些相似的字母组合。他们的方法是：不再使用传统的 tokenzier（分词器），而是整合了一个能学习如何对输入字符进行分组的系统。

What's new: Artidoro Pagnoni，Ram Pasunuru，and collaborators at Meta，University of Washington，and University of Chicago introduced Byte Latent Transformer (BLT），a system of transformers that processes groups of text characters（in the form of bytes）directly.

新的进展：Artidoro Pagnoni、Ram Pasunuru 以及来自 Meta、华盛顿大学和芝加哥大学的合作者推出了一项名为 Byte Latent Transformer（BLT）的新技术。这是一种基于 Transformer 的系统，它能够直接处理文本字符（以字节形式）的组合。

Key insight: A tokenizer turns bytes（characters）into tokens（a word or part of a word）based on learned rules：Specific sequences map to particular tokens. A large language model（LLM）would be more efficient if its tokenizer considered how easy or difficult it would be to predict the next token，because then it could group tokens that commonly occur together，thus saving memory and processing power. For instance，to complete the phrase,「The capital of the United States is,」a tokenizer may generate「Washington」，then「D」，then「.C」，and finally「.」— even though it's easy to predict that「D.C.」will follow「Washington」(that is，the number of viable options is very small). Conversely，generating the token after「D.C.」is harder，since many viable options exist. Using a small LLM to estimate the difficulty of predicting the next token enables the model to split difficult-to-predict text into smaller groups while packing easier-to-predict text into larger groups.

核心观点：分词器（tokenizer）依据学习到的规则将字节（即字符）转化为 Token（可以是词语或词语的一部分）：特定的字符序列对应特定的 Token。如果大语言模型（LLM）的分词器能考虑到预测下一个 Token 的难易程度，效率就会更高。因为这样一来，分词器就可以将那些经常一起出现的 Token 归为一组，从而节省内存和计算资源。举例来说，为了完成短语「The capital of the United States is,」，分词器可能会依次生成「Washington」、「D」、「.C」和「.」—— 尽管实际上很容易预测「Washington」后面紧跟着的就是「D.C.」（也就是说，可能的后续选项很少）。反之，预测「D.C.」后面的 Token 则要困难得多，因为有很多可能的选项。通过利用一个小型的大语言模型来估算预测下一个 Token 的难度，模型就可以将那些难以预测的文本细分成更小的组，而将更容易预测的文本合并成更大的组。

How it works: BLT comprises four transformers（8 billion parameters total)：(i）a small byte-level transformer，(ii）an encoder transformer，(iii）a so-called latent transformer，and（iv）a decoder transformer. The authors trained the system to generate the next token in 1 trillion tokens of text, including tokens drawn from a filtered version of Common Crawl.

工作原理：BLT 系统由四个 Transformer（总共 80 亿个参数）组成，分别是：（i）一个小型字节级 Transformer，（ii）一个编码器 Transformer，（iii）一个潜在 Transformer，以及（iv）一个解码器 Transformer。研究人员对该系统进行了训练，使其能够在包含 1 万亿个文本 token 的数据集上预测下一个 token，这些数据集中包含了从 Common Crawl 经过筛选的版本中提取的 token。

1 The authors trained the byte-level transformer to generate the next byte from an input sequence of bytes.

作者们训练了一个字节级别的 Transformer 模型，让它能够根据输入的字节序列来预测下一个字节。

2 For an input sequence，the byte-level transformer predicted the probabilities of the value of the next byte. The authors used entropy，a measure of uncertainty，to decide how bytes should be grouped. If the predicted probabilities were concentrated in a particular byte value（low entropy），meaning the next byte was highly predictable，the byte was added to the current group. If the probabilities were more spread out across multiple byte values（high entropy），meaning the model was less certain，it was part of a new group.

对于输入的字节序列，这个字节级别的 Transformer 会预测下一个字节可能的值以及对应的概率。作者们引入了「熵」（entropy）的概念，这是一个衡量不确定性的指标，用来决定如何将字节进行分组。如果预测的概率集中在某一个特定的字节值上（也就是「低熵」），说明模型对下一个字节的预测非常有信心，那么这个字节就会被归入当前的组。如果概率分散在多个字节值上（也就是「高熵」），说明模型不太确定下一个字节具体是什么，那么这个字节就会成为一个新的组的一部分。

3 The encoder transformer learned to represent each group as a vector，while attending to preceding bytes for context.

编码器 Transformer 学习如何将每个组表示为一个向量，同时关注前面的字节以获取上下文信息。

4 The latent transformer learned to generate the next group vector from all previous group vectors.

在潜在空间中的 Transformer 学习如何根据所有先前的组向量生成下一个组向量。

5 Finally，the decoder transformer learned to reconstruct a byte sequence from a sequence of vectors.

最后，解码器 Transformer 学习了如何从一系列向量中还原出原始的字节序列。

Results: On seven benchmarks that test general language and coding abilities，BLT achieved an average accuracy of 61.1 percent，outperforming Llama 3 (8 billion parameters and a similar number of floating point operations to BLT）at 60.0 percent.

结果：在七个用于评估通用语言理解和编程能力的基准测试中，BLT 取得了 61.1% 的平均准确率。这一成绩超过了 Llama 3 （一个拥有 80 亿参数，计算量与 BLT 相当的模型）的 60.0%。

1 BLT achieved 80.6 percent on the common-sense question and answer benchmark HellaSwag，while Llama 3（8 billion parameters and a similar number of floating point operations to BLT）achieved 79.1 percent.

在常识问答基准 HellaSwag 上，BLT 取得了 80.6% 的成绩，而 Llama 3（参数量为 80 亿，浮点运算次数与 BLT 相似）则取得了 79.1% 的成绩。

2 BLT demonstrated significantly higher resilience to noisy inputs compared to Llama 3，particularly in tasks involving character manipulation，spelling variations，and languages for which relatively little data is available. For example，in the CUTE spelling benchmark，which tests a model's ability to recognize correctly spelled words，BLT achieved 99.9 percent accuracy while Llama 3 achieved 1.1 percent accuracy.

与 Llama 3 相比，BLT 对噪声输入的鲁棒性（resilience）显著更高，尤其是在处理涉及字符操纵、拼写变异以及可用数据相对较少的语言的任务时。例如，在用于评估模型识别正确拼写单词能力的 CUTE 拼写基准测试中，BLT 实现了 99.9% 的准确率，而 Llama 3 的准确率仅为 1.1%。

3 BLT outperformed Llama 3 in translating to English across 26 languages (including 20 with little data). It achieved 14.0 average SentencePiece BLEU score（which measures how good a machine translation is compared to a human translation over text tokenized with the SentencePiece tokenizer），while LLaMA 3 achieved 12.1 average SentencePiece BLEU.

在将 26 种语言（包括 20 种数据量较少的语言）翻译成英语方面，BLT 的表现优于 Llama 3。BLT 的平均 SentencePiece BLEU 分数达到了 14.0（SentencePiece BLEU 分数是一种衡量机器翻译与人工翻译相比好坏的指标，基于使用 SentencePiece 分词器处理过的文本），而 LLaMA 3 的平均 SentencePiece BLEU 分数为 12.1。

Why it matters: By working directly on bytes，BLT is inherently more robust to variations in language，which improves its performance. For instance，when prompted to insert a「z」after every「n」in「not」，Llama 3 incorrectly completed it as「znotz". This happened because its tokenizer treats「not」as a single，indivisible token. In contrast，BLT correctly generated「nzot,」because it can dynamically regroup bytes and draw new boundaries. In a more practical case，instead of treating「pizya」and「pizza」as different tokens，BLT recognizes that they share nearly identical byte sequences，differing only in the bytes for「y」and「z」，and therefore likely mean the same thing.

为什么它很重要：通过直接处理字节，BLT 天然地对语言变化更具鲁棒性，这提高了它的性能。例如，当被要求在单词「not」中的每个「n」后插入一个「z」时，Llama 3 错误地输出了「znotz」。发生这种情况是因为它的分词器将「not」视为一个单独的、不可分割的 token。相比之下，BLT 正确地生成了「nzot」，因为它能够动态地处理字节并重新划分词语边界。举一个更实际的例子，BLT 没有将「pizya」和「pizza」视为不同的 token，而是认识到它们共享几乎相同的字节序列，只在「y」和「z」的字节上有所不同，因此很可能意味着相同的事情。

We're thinking: In some alternatives to traditional tokenization，an LLM might process much longer sequences because the number of bytes in a sentence is much larger than the number of words. This work addresses that issue by grouping bytes dynamically. The tradeoff is complexity：Instead of one transformer，we have four.

我们认为：与传统分词方法不同的是，由于句子中的字节数远多于词数，大语言模型（LLM）在某些替代方案中需要处理更长的序列。本文提出的方法通过动态地对字节进行分组来解决这个问题。不过，这种方法也有一个权衡：那就是复杂性更高，需要用到四个 Transformer 模型，而不是一个。