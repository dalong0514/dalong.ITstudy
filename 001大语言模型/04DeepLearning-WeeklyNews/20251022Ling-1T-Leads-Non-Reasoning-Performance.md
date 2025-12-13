## 20251022Ling-1T-Leads-Non-Reasoning-Performance

[Ling-1T Leads Non-Reasoning Performance, MCP Poses Security Risks, California Regulates AI, and more...](https://www.deeplearning.ai/the-batch/issue-324/)

Dear friends,

In last week’s letter, I explained how effective agentic AI development needs a disciplined evals and error analysis process, and described an approach to performing evals. This week, I’d like to summarize the core ideas behind error analysis and describe some best practices. Given the rapid pace of improvement in LLMs, when error analysis points to a problem, your options for how to address it are greater than before. Let me explain.

在上周的信中，我阐述了要有效地开发 AI 智能体（AI Agent），为何必须遵循严谨的评估（Evals）和误差分析流程，并介绍了一种进行评估的方法。本周，我想总结一下误差分析背后的核心思想，并分享一些最佳实践。鉴于大语言模型（LLM）的飞速进步，当误差分析指出某个问题时，你可采取的应对方案比以往要多得多。下面我来详细说明。

Take the problem of building a basic Deep Research agent that searches the web to write a detailed report on a topic like “recent developments in black-hole science.” An agent might take a sequence of steps to generate the final report, such as (i) use an LLM to generate a handful of web search queries related to the topic, (ii) call a web-search API to get lists of results, (iii) use an LLM to identify the most promising sources to fetch, and (iv) ask the LLM to use these sources to write the report.

以构建一个基础的深度研究智能体为例，其任务是搜索网络，并撰写一份关于「黑洞科学的最新进展」这类主题的详细报告。该智能体可能会执行以下一系列步骤来生成最终报告：(i）使用大语言模型（LLM）生成几个与该主题相关的网络搜索查询；(ii）调用网络搜索 API 以获取结果列表；(iii）再次利用大语言模型，从结果中筛选出最有价值的资料来源；(iv）最后，指示大语言模型基于这些资料撰写报告。

If the final report is subpar compared to the work of a human researcher following the same steps, the gap in performance could be from any of the steps. A basic error analysis procedure might involve gathering a sample set of topics where the output is subpar, and reading the results of every step of the workflow — called the traces — to see which step most frequently generated results materially worse than a human would have. This is very valuable for deciding what step to focus on improving.

如果最终报告的质量不及遵循相同步骤的人类研究员，那么这种性能上的差距可能源于工作流程中的任何一个环节。一个基本的错误分析流程可能包括：收集一批报告质量不佳的主题样本，然后逐一检查工作流中每个步骤的输出结果（这些记录被称为跟踪记录（traces)），从而找出哪个步骤最频繁地产出了明显逊于人类水平的结果。这对于确定应优先改进哪个环节至关重要。

A common misconception of error analysis is that it takes a lot of work to get started. The key principle is to look at the steps of the workflow and see which steps did a bad job on a given input, often by benchmarking to human level performance (HLP). Assuming we are automating a task where HLP is desirable, then the most important thing is to systematically examine traces to understand when the agent is falling short of HLP. And just as we can get started with evals using a quick-and-dirty initial cut at it (maybe using just a handful of examples) followed by iterating to improve, so too with error analysis.

关于错误分析的一个常见误解是，启动这项工作需要耗费大量精力。其核心原则是审视工作流程中的各个环节，找出在特定输入上处理效果不佳的步骤，这通常通过与人类水平表现（HLP）进行基准对比来实现。假设我们正在自动化一项期望达到人类水平表现的任务，那么最关键的就是系统地检查执行轨迹，了解 AI 智能体在哪些情况下未能达到 HLP 标准。就像我们可以通过快速但不完美的初步尝试（可能仅用少量样本）启动评估工作，然后通过迭代不断完善那样，错误分析同样可以采用这种循序渐进的方式开展。

Specifically, it is fine to start by reading one or just a handful of traces informally to get a sense of what might be going wrong. For example, if you see that the web search query terms in your Deep Researcher — step (i) above — frequently make no sense, that points you to an initial area to focus your efforts on improving. As the system matures, you can move incrementally toward more rigorous error analysis. For example, you might eventually end up with a regularly refreshed dataset of thousands of examples where the performance is poor, and carry out rigorous evaluations that show exactly what percentage of the time each of the steps (i) - (iv) contributed to problems with the final output, and also in what specific ways those steps fell short.

具体来说，开始时可以非正式地查看一个或少量运行轨迹，以了解可能存在的问题。例如，如果你发现 Deep Researcher 中的网络搜索查询词（上述步骤（i)）经常不合逻辑，这就为你指明了需要优先关注的改进方向。随着系统的成熟，你可以逐步转向更严格的错误分析。例如，最终你可能会建立一个定期更新的数据集，包含数千个性能不佳的样本，并通过严格的评估准确显示：在多大比例的问题中，步骤（i）至（iv）各自导致了最终输出的缺陷，以及这些步骤具体在哪些方面存在不足。

This type of analysis is extremely useful for deciding where to focus your efforts to improve the overall agentic workflow's performance!

In addition to improving the execution of individual steps, we can change how we decompose a complex task into steps. When it came to pipelines built using machine learning or deep learning rather than LLMs, I found that the structure of the workflow — that is, how you decompose an overall task into a sequence of steps to be carried out — changed rarely. It was a big deal to rearchitect this! But in the past couple of years, because LLMs are improving so rapidly, I see much more rapid iteration on the design of workflows.

这类分析对于确定应该将改进重点放在哪些方面，以提升整个 AI 智能体工作流（AI Agent Workflow）的性能非常有帮助！

除了优化单个步骤的执行效果，我们还可以调整复杂任务的分解方式。在基于机器学习或深度学习（而非大语言模型）构建的流水线中，我发现工作流的结构 —— 也就是将整体任务拆分为一系列执行步骤的方式 —— 很少发生变化。重新设计这种架构曾是件相当困难的事！但在过去几年里，由于大语言模型的发展速度惊人，我观察到工作流设计的迭代进程明显加快了。

For example, one very common pattern is ripping out scaffolding and letting the LLM do more. This is often a good move when you now have access to a smarter LLM than you did when you first built a workflow. For example, perhaps you once used an LLM to clean up downloaded web pages by removing navigational links, ads, extraneous HTML, and the like, before a separate LLM used the cleaned-up pages to write a report. Since LLMs have become smarter, you might decide to skip the first step and dump messier HTML into the final LLM without an initial clean-up step, which can introduce its own errors.

例如，一个非常常见的做法是简化预处理步骤，让大语言模型承担更多工作。当您现在能够使用比最初构建工作流程时更智能的大语言模型时，这通常是个明智的选择。举例来说，您可能曾经使用一个大语言模型来清理下载的网页，移除导航链接、广告、无关 HTML 等内容，然后再由另一个大语言模型使用清理后的页面来撰写报告。随着大语言模型智能水平的提升，您可能会决定跳过预处理步骤，直接将未经过清理的杂乱 HTML 输入最终的大语言模型，但这样做可能会带来新的错误风险。

Another example: Perhaps a year ago, we used hard-coded rules to decide what web pages to fetch and when to fetch more, but today we might let an LLM-based agent make this decision more autonomously. As LLMs get smarter, I see many teams rearchitecting workflows to remove hard-coded steps or constraints that were previously needed to keep the system from going off the rails. One way to spot opportunities for doing this is if error analysis shows that a sequence of steps collectively underperforms compared to what a human might do, even though the performance of each individual step is good. This might indicate that the way those steps are carried out is too rigid.

另一个例子：也许在一年前，我们使用硬编码规则（hard-coded rules）来决定获取哪些网页以及何时获取更多内容，但如今我们可能会让一个基于大语言模型（LLM）的 AI 智能体更自主地做出这些决策。随着大语言模型变得越来越智能，我观察到许多团队正在重构工作流程，移除那些原先为防止系统偏离正轨而设置的硬编码步骤或约束。识别这类改进机会的一个方法是：当错误分析显示，尽管每个独立步骤的表现良好，但整个步骤序列的总体表现却不如人类操作时，这可能意味着这些步骤的执行方式过于僵化。

I go through many more examples in the Agentic AI course. Check it out if you want to learn more about evals and error analysis.

Keep building!

我在「AI 智能体」课程中还会深入讲解更多实例。如果你想进一步了解评估方法和错误分析技巧，欢迎来学习。

继续加油！

Andrew

### News

安德鲁

### 新闻动态

#### Reasoning Without "Thinking"

Reasoning models typically learn to undertake a separate process of "thinking" through their output of before they produce final response. Ant Group built a top non-reasoning model that can take similar steps as part of its immediate response.

#### 无需「思考」的推理推理模型（Reasoning Model）通常会在输出最终响应之前，通过学习来进行一个独立的「思考」过程。蚂蚁集团构建了一个顶级的非推理模型，能够在即时响应中采取类似的思考步骤。

What's new: Ant Group, an affiliate of Alibaba and owner of the online payments provider Alipay, released Ling-1T, a huge, open, non-reasoning model that outperforms both open and closed counterparts.

最新消息：阿里巴巴关联企业、在线支付平台支付宝的所有者蚂蚁集团发布了灵 - 1T（Ling-1T），这是一个大规模开源非推理模型，其性能表现超越了同类开源和闭源模型。

* Input/output: Text in (up to 128,000 tokens), text out (up to 32,000 tokens)

* Architecture: Mixture-of-Experts (MoE) transformer, 1 trillion parameters, 50 billion parameters active per token

* 输入 / 输出：支持文本输入（最多 128,000 个 Token），文本输出（最多 32,000 个 Token）
* 架构：采用混合专家（MoE）Transformer 架构，总参数量为 1 万亿，每个 Token 处理时动态使用 500 亿参数

* Performance: Outperformed leading non-reasoning models in 22 of 31 benchmark tests of reasoning, math, coding, general knowledge, and writing.

* Availability: Weights free to download from HuggingFace and ModelScope for commercial and noncommercial uses under the MIT license, API $0.56/$0.112/$2.24 per million input/cached/output tokens via zenmux.ai

* 性能：在 31 项涵盖推理、数学、编程、通识知识和写作的基准测试中，有 22 项的表现优于领先的非推理模型。
* 可用性：模型权重可在 HuggingFace 和 ModelScope 免费下载，基于 MIT 许可证可用于商业和非商业用途；通过 zenmux.ai 提供的 API 服务，每百万个输入 / 缓存 / 输出 token（Token）的价格分别为 0.56 美元 / 0.112 美元 / 2.24 美元。

* Undisclosed: Training data, specific training methods

How it works: The team emphasized chain-of-thought reasoning in both the pretraining and fine-tuning phases of development, but it didn't train the model to undertake a separate reasoning, or thinking, process before producing its final output. This means the model can reason selectively depending on the input.

* 未披露：训练数据，具体训练方法工作原理：研发团队在预训练和微调阶段都特别强调了思维链推理（chain-of-thought reasoning），但并未训练模型在生成最终答案前执行独立的推理或思考过程。这意味着模型能够根据输入内容灵活调整其推理方式。

* The team pretrained Ling-1T on 20 trillion tokens. In the last part of pretraining, they used a curated subset in which over 40 percent consisted of chain-of-thought data.

* 研究团队使用 20 万亿个 Token 对 Ling-1T 进行了预训练。在预训练的最后阶段，他们采用了精选的数据子集，其中思维链（chain-of-thought）数据的占比超过 40%。

* They fine-tuned the model via supervised fine-tuning on examples that were augmented with chains of thought via CoT-Evo. CoT-Evo takes a training dataset and generates and evolves chains of thought (CoTs) for each example in the dataset. It evolves CoTs by repeatedly scoring them, selecting them (based on score, difference from other CoTs, and random chance), and modifying them via an LLM. The team fine-tuned Ling-1T on the examples with the highest-scoring CoTs.

* 研究团队通过监督微调的方式对模型进行优化，使用的训练样本经过了 CoT-Evo 的思维链增强处理。CoT-Evo 能够处理训练数据集，为其中的每个样本生成并优化思维链。其优化过程包含三个核心步骤：首先对思维链进行评分，然后根据评分结果、与其他思维链的差异性以及一定的随机概率进行筛选，最后通过大语言模型对选中的思维链进行修改。团队最终选取了思维链评分最高的训练样本，对 Ling-1T 模型进行了微调。

* In addition, they fine-tuned the model using a reinforcement learning algorithm developed internally called Linguistic-Unit Policy Optimization (LPO). Unlike GRPO and GSPO, LPO "treats sentences as the natural semantic action units, enabling precise alignment between rewards and reasoning behavior," the company said.

* 此外，该公司使用内部开发的强化学习算法 —— 语言单元策略优化（Linguistic-Unit Policy Optimization，简称 LPO）对模型进行了微调。与 GRPO 和 GSPO 不同，LPO"将句子视为自然的语义行动单元，能够实现奖励机制与推理行为的精准匹配」。

Results: In Ant Group's tests, Ling-1T generally outperformed three top non-reasoning models: DeepSeek-V3.1-Teriminus (thinking mode disabled), Moonshot Kimi-K2-Instruct, and OpenAI GPT-5 (thinking mode disabled), as well as Google Gemini 2.5 Pro set to minimum thinking (128 tokens).

结果：在蚂蚁集团的测试中，Ling-1T 整体表现优于三款顶尖的非推理模型：DeepSeek-V3.1-Terminus（思考模式关闭）、Moonshot Kimi-K2-Instruct 和 OpenAI GPT-5（思考模式关闭），以及谷歌 Gemini 2.5 Pro（最小思考模式设置为 128 个 token）。

* Ling-1T achieved the highest performance on 22 of 31 benchmarks tested and best or second-best performance on 29 of 31 benchmarks that cover general knowledge, coding, math, reasoning, writing, and agentic tasks.

* Ling-1T 在测试的 31 个基准中的 22 个上取得了最佳表现，并在涵盖常识、编程、数学、推理、写作和 AI 智能体任务的 31 个基准中，有 29 个都达到了第一或第二的成绩。

* It performed best in the math and reasoning categories, achieving the best performance in all benchmarks tested. For instance, on math questions in AIME 2025, Ling-1T achieved 70.42 percent accuracy, whereas the second-best model, Gemini 2.5 Pro set to minimum thinking, achieved 70.10 percent accuracy.

* 在数学和推理这两个类别中，它的表现最为出色，在所有参与测试的基准测试中都位居榜首。举例来说，在 AIME 2025 的数学题目上，Ling-1T 的准确率达到了 70.42%，而位列第二的模型 ——Gemini 2.5 Pro 在最小思考模式下 —— 准确率为 70.10%。

Yes, but: The team published results of only one agentic benchmark and admits to limited performance in this area. It says it will improve agentic performance in future releases.

是的，但需要说明的是：该研究团队仅公布了一项智能体基准测试（agentic benchmark）的结果，并坦承在此领域的表现仍有局限。团队表示将在后续版本中提升智能体（AI Agent）的性能表现。

Behind the news: Concurrently with Ling-1T, Ant Group released a finished version of its 1 trillion-parameter reasoning model, Ring-1T, which was available previously as a preview. While Ling-1T's performance exceeded that of top non-reasoning models, Ring-1T achieved second-place performance relative to reasoning models on almost every benchmark tested.

值得注意的是，在发布 Ling-1T 的同时，蚂蚁集团还推出了其万亿参数推理模型 Ring-1T 的正式版 —— 该模型此前仅以预览版形式亮相。虽然 Ling-1T 的性能超越了顶尖的非推理模型，但 Ring-1T 在几乎所有测试基准中，均在推理模型类别中取得了第二名的优异成绩。

Why it matters:  Ling-1T generally outperforms the mighty Kimi K2 and closes the gap between open and closed nonreasoning models. A ginormous parameter count and pretraining on chains of thought appear to have been key factors in this accomplishment. Having been pretrained with an intense focus on chains of thought, Ling-1T is primed to generate a chain of thought before it concludes a response, although not in a separate reasoning stage. Such training blurs the line between reasoning and non-reasoning models.

为什么这很重要：Ling-1T 通常能够超越强大的 Kimi K2，并且缩小了开放与封闭非推理模型（non-reasoning models）之间的性能差距。实现这一成就的关键因素在于其庞大的参数规模以及对思维链（chain of thought）的预训练。由于在预训练阶段特别注重思维链，Ling-1T 能够在给出最终答案前自动生成推理过程，尽管这并非独立的推理阶段。这样的训练方式使得推理模型与非推理模型之间的界限变得模糊。

We're thinking: Two years ago, weights for Ling-family models were closed, but in the past year Ant Group has released open weights for several. With consistent effort and investment, Ling has gone from a family that few had heard of to challenging the top dogs.

我们认为：两年前 Ling 系列模型的权重还是封闭的，但过去一年间，蚂蚁集团已陆续发布了多个开放权重。凭借持续的努力投入，Ling 这个曾经鲜为人知的模型家族，如今已开始向行业头部模型发起挑战。

#### MCP Poses Security Risks

The ability to easily connect large language models to tools and data sources has made Model Context Protocol popular among developers, but it also opens security holes, research shows.

#### MCP（Model Context Protocol）构成安全风险研究表明，将大语言模型轻松连接到工具和数据源的能力使得模型上下文协议（Model Context Protocol）在开发者群体中颇受欢迎，但这也带来了安全风险。

What's new: Golan Yosef at Pynt, an API security firm, analyzed security risks of Model Context Protocol (MCP) servers. The work shows that when systems use multiple MCP servers, vulnerabilities rise rapidly.

最新研究：API 安全公司 Pynt 的 Golan Yosef 分析了模型上下文协议（Model Context Protocol，MCP）服务器的安全风险。该工作表明，当系统使用多个 MCP 服务器时，安全漏洞风险会急剧上升。

How it works: MCP's flexible, modular, dynamic design is a double-edged sword. It supports open-ended agentic interactions, but those very qualities make MCP servers vulnerable to exploitation. The study assessed security risks across more than 280 popular servers.

工作原理：MCP 的灵活、模块化、动态设计是一把双刃剑。虽然这种设计支持开放式的智能体（AI Agent）交互，但恰恰是这些特性使得 MCP 服务器容易遭受安全漏洞利用。该研究对超过 280 个流行服务器进行了安全风险评估。

* For each server, Yosef evaluated two properties: whether it would process inputs from unsafe sources that can't be fully verified or controlled (such as emails, chats, Slack messages, or scraped web pages) and whether it allowed powerful actions like code execution, file access, or calling APIs. He deemed servers that had both traits to be high-risk, since it could execute an attacker's instructions without a user's approval.

* 对于每个服务器，Yosef 评估了两个属性：是否会处理来自无法完全验证或控制的不安全来源的输入（例如电子邮件、聊天、Slack 消息或网络爬取的网页），以及是否允许执行高权限操作，如代码执行、文件访问或 API 调用。他认为同时具备这两个特征的服务器属于高风险类别，因为这类服务器能够在未经用户批准的情况下执行攻击者的指令。

* He estimated how risk increases as systems use greater numbers of servers. (He didn't disclose the formula or method used to derive the estimates.)

* He validated his risk model by attacking real-world MCP setups, including cases where unsafe input from one server caused another server to execute commands automatically.

* 他评估了风险随系统使用服务器数量增加而上升的趋势。（但未透露用于推导这些评估结果的公式或方法。）

* 通过攻击真实世界的 MCP 设置（MCP setups），他验证了自己的风险模型，其中包括某台服务器的非安全输入导致其他服务器自动执行命令的案例。

Results: The study identified widespread patterns of vulnerability that compound as systems add MCP servers.

* Of the servers tested, 72 percent of servers tested exposed at least one sensitive capability to attackers, and 9 percent of servers tested were deemed high-risk.

结果：研究发现普遍存在的漏洞模式，这些模式会随着系统增加 MCP 服务器而不断累积放大。

* 在受测服务器中，72% 的服务器向攻击者暴露了至少一项敏感权限，9% 的服务器属于高风险级别。

* 13 percent of servers accepted inputs from unsafe sources, enabling attackers without direct access to their targets to deliver malicious text (HTML, emails, Markdown) that servers downstream might interpret as code.

* 13% 的服务器会接收来自不安全来源的输入，这使得攻击者即使无法直接访问目标系统，也能传递恶意文本（HTML、电子邮件、Markdown），而这些内容在下游服务器中可能被当作代码执行。

* Risk of an exploitable configuration compounded rapidly with the first few servers added before flattening. Combining 2 servers created 36 percent chance of a vulnerable configuration, Combining 3 reached 52 percent chance, 5 servers exceeded 71 percent change, and 10 servers approached 92 percent chance.

* 可利用配置（Exploitable Configuration）的风险随着前几台服务器的加入而快速累积，之后增长趋于平缓。组合 2 台服务器产生脆弱配置的概率为 36%，组合 3 台服务器时达到 52%，5 台服务器时超过 71%，10 台服务器时接近 92%。

* The study documents real-world examples in which attackers executed privileged actions. In one case, a plug-in web scraper fetched HTML, supplied by an attacker, that a Markdown parser interpreted as commands, which a shell plug-in duly executed.

* 该研究记录了攻击者执行特权操作的真实案例。其中一个案例显示：插件式网页抓取工具获取到攻击者提供的 HTML 内容后，Markdown 解析器将其解释为系统命令，最终由 shell 插件执行了这些命令。

Behind the news: Anthropic launched MCP in November 2024, and OpenAI and Microsoft adopted it by spring 2025. Despite its lax security, the protocol now connects to over 6,000 servers. Authentication remained optional until March, when OAuth 2.1 authorization frameworks were added. The change prevents unauthorized access to MCP servers, but it doesn't prevent malicious or malformed data from flowing between servers and triggering unintended actions.

新闻背景：Anthropic 于 2024 年 11 月推出了模型上下文协议（Model Context Protocol，MCP），OpenAI 和 Microsoft 随后在 2025 年春季也采用了该协议。尽管该协议的安全措施较为宽松，但目前已有超过 6,000 台服务器接入。在三月之前，身份认证一直是可选项，直到引入了 OAuth 2.1 授权框架。这一安全升级虽然防止了对 MCP 服务器的未授权访问，但无法阻止恶意数据或格式错误的数据在服务器间传输，从而可能触发非预期的操作。

Why it matters: Securing individual MCP servers is important but not sufficient, because vulnerabilities can emerge from interactions among servers. Adding more servers can make a system more agentic, but it also compounds vulnerabilities. The study suggests that developers mitigate this "compositional risk" by using only the servers they need, constraining what each one is allowed to do, and testing transfers of data among them.

为什么这很重要：保护单个 MCP（Model Context Protocol）服务器虽然重要，但还远远不够，因为漏洞可能源自服务器之间的交互。增加服务器数量虽然能提升系统的智能性，但也会放大安全风险。该研究建议开发者通过以下方式缓解这种「组合风险"：仅使用必要的服务器、严格限制每个服务器的操作权限，以及测试服务器之间的数据传输。

We're thinking: Securing individual components is a tough task in its own right, but systems of MCP components must be secured at the system level.

#### California Builds AI Regulatory Regime

我们的思考是：保护单个组件本身已是一项艰巨任务，但对于由 MCP 组件组成的系统而言，必须在系统层面进行整体保护。

#### 加州构建人工智能监管制度

In the absence of national laws that specifically regulate AI in the United States, California moved to regulate the technology within its own borders, passing four bills in less than a month.

由于美国缺乏专门监管人工智能（AI）的国家法律，加利福尼亚州率先行动起来，在不到一个月的时间里通过了四项法案，开始在本州范围内对这一技术实施监管。

What's new: Governor Gavin Newsom signed into law SB 53, which requires large AI developers to disclose their safety protocols. In addition, SB 243 regulates chatbots, AB 316 makes developers liable for the actions of autonomous systems they build, and AB 853 requires AI-generated media to be labeled clearly.

最新动态：加州州长加文·纽森正式签署 SB 53 法案，要求大型人工智能开发者必须公开其安全措施。同时，SB 243 法案将对聊天机器人实施监管，AB 316 法案规定开发者需对其开发的自主系统行为承担法律责任，AB 853 法案则要求明确标注由人工智能生成的媒体内容。

How it works: Together, the bills don't ban any particular applications outright or restrict AI development, but they require extensive disclosures, either to the state or directly to users. Some took effect immediately while others, such as SB 243, will phase in by January 2027.

具体运作机制：这些法案并未彻底禁止任何特定应用或限制人工智能（AI）开发，但要求相关方必须履行广泛的信息披露义务，披露对象可以是州政府或直接面向用户。部分法案已立即生效，而另一些法案（例如 SB 243）将分阶段实施，最终在 2027 年 1 月前全面生效。

* SB 53 requires that developers of frontier models, defined as those whose training requires processing greater than 1026 integer or floating-point operations — a level currently associated with very large and powerful models — provide more transparency about their models' capabilities and potential risks. It also requires that developers with annual revenue above $500 million publish safety frameworks that show how they follow industry and international standards and assess and mitigate risk. In addition, they must report on their models' uses and capabilities at release and report any critical safety incidents within 15 days. Noncompliant developers could face fines of up to $1 million. The law protects whistleblowers within AI companies against retaliation and provides anonymous channels to report illegal or unsafe behavior. The bill takes effect in June 2026.

* SB 53 法案要求前沿模型（定义为其训练过程需要超过 10^26 次整数或浮点运算的模型，这个运算量级目前对应于超大规模的高性能模型）的开发者必须提高模型能力与潜在风险的透明度。同时，年收入超过 5 亿美元的开发者需要公布安全框架，详细说明其如何遵循行业与国际标准，并进行风险评估与防控。此外，这些企业必须在模型发布时说明其功能特性与应用场景，并在 15 天内上报所有重大安全事故。违规开发者将面临最高 100 万美元的罚款。该法案还明确规定保护 AI 企业内部举报人免遭打击报复，并设立了非法或危险行为的匿名举报渠道。此项立法将于 2026 年 6 月正式实施。

* SB 243 aims to prevent chatbots from harming minors and other vulnerable users. It bars exposing minors to sexual content and requires developers to disclose that chatbots are AI-generated and provide a general warning that chatbots may not be suited for minors. The bill also requires developers to provide specific support to users who discuss suicide or self-harm and to issue an annual report on mental health issues related to using their chatbots.

* SB 243 法案旨在防止聊天机器人对未成年人及其他弱势群体造成伤害。该法案禁止向未成年人展示性内容，要求开发者必须披露聊天机器人由 AI 生成的事实，并给出通用警示 —— 聊天机器人可能不适用于未成年人。法案还规定开发者需为讨论自杀或自残的用户提供专项支持，并每年发布与其聊天机器人使用相关的心理健康问题报告。

* AB 316 prohibits defendants in lawsuits from shifting responsibility onto AI systems by claiming that they harmed plaintiffs autonomously. It applies to anyone who develops, modifies, or uses an AI system.

* AB 316 法案禁止被告在诉讼中通过声称「AI 系统自主造成损害」来推卸责任。该法规适用于任何开发、修改或使用人工智能系统的个人或组织。

* AB 853 requires that AI-generated media be labeled clearly as such. Furthermore, it requires that all media (AI-generated or not) include information about who made it and how. The bill requires that cameras, audio recorders, computers, and other media-capture devices record such provenance data, and that large-scale media distributors (2,000,000 monthly active users or more) disclose it.

* AB 853 要求将 AI 生成的媒体（AI-generated media）明确标注为 AI 生成。此外，该法案要求所有媒体（无论是 AI 生成还是非 AI 生成）都必须包含关于制作者和制作方式的信息。法案规定相机、录音设备、计算机和其他媒体采集设备必须记录此类来源数据（provenance data），并要求月活跃用户达到 200 万及以上的大型媒体分发平台披露这些数据。

What they're saying: Reaction among AI developers has been mixed. SB 53 drew the loudest and most widely varied commentary.

* Collin McCune, head of government affairs at the venture capital firm Andreessen Horowitz, said SB 53 puts startups at a disadvantage: "States have an important role in regulating AI. But if lawmakers really want to protect their citizens, this isn't the way. They should target harmful uses through consumer protection laws and similar safeguards — not dictate how technologists build technology."

业内人士表示：AI 开发者对此反应不一。其中 SB 53 法案引发的讨论最为激烈且观点多样。

* 风险投资公司 Andreessen Horowitz 的政府事务负责人 Collin McCune 认为，SB 53 法案会让初创企业处于劣势："各州在监管 AI 方面确实扮演重要角色。但如果立法者真心想要保护公民，这种方式并不妥当。他们应该通过消费者保护法和类似保障措施来针对有害应用，而非硬性规定技术人员该如何开发技术。"

* Chris Lehane at OpenAI opposed California's approach: "History shows that on issues of economic competitiveness and national security — from railroads to aviation to the internet — America leads best with clear, nationwide rules, not a patchwork of state or local regulations. Fragmented state‑by‑state approaches create friction, duplication, and missed opportunities."

* OpenAI 的 Chris Lehane 反对加州的做法："历史表明，在处理经济竞争力和国家安全问题时 —— 从铁路到航空再到互联网 —— 美国最有效的做法是建立清晰的全国性规则，而不是各州或地方零散的法规拼盘。各州各自为政的做法会导致摩擦丛生、资源重复浪费，并错失发展良机。"

* Anthropic endorsed SB 53: "We've long advocated for thoughtful AI regulation, and our support for this bill comes after careful consideration of the lessons learned from California's previous attempt at AI regulation (SB 1047). While we believe that frontier AI safety is best addressed at the federal level instead of a patchwork of state regulations, powerful AI advancements won't wait for consensus in Washington."

* Anthropic 支持 SB 53 法案："我们长期倡导审慎的 AI（人工智能）监管，在仔细考量了从加州先前人工智能监管尝试（SB 1047）中吸取的教训后，我们决定支持这项法案。虽然我们认为前沿人工智能安全最好在联邦层面解决，而非依赖零散的各州法规，但迅猛的人工智能技术进步不会等待华盛顿达成共识。"

Behind the news: SB 53 modifies parts of SB 1047, which Governor Newsom vetoed in 2024 after opposition from the tech community. That law would have required third-party audits and made companies liable for the uses of their models. Recently, Newsom also vetoed SB 7, which would have required employers to notify employees and applicants if AI systems were used to make employment decisions like hiring and firing.

新闻背景：SB 53 法案对 SB 1047 法案的部分内容进行了修订，后者在 2024 年因科技界反对而被纽森州长否决。该法案原本要求进行第三方审计，并要求企业对自家模型的使用后果承担法律责任。近期，纽森还否决了 SB 7 法案，该法案原本规定当企业使用 AI 系统进行招聘、解雇等人事决策时，必须通知在职员工和求职者。

Why it matters: California is the largest U.S. state by the sizes of its population and economy, as well as home of many of the world's most prominent tech companies and startups, including Google, OpenAI, and Anthropic. These laws will affect users of CA-based tech worldwide along with companies that do business in the state.

为何重要：加利福尼亚州不仅是美国人口最多、经济最发达的州，更是众多世界顶尖科技公司和初创企业的聚集地，包括谷歌、OpenAI 和 Anthropic。这些法律不仅会影响全球使用加州科技产品的用户，还将波及所有在该州经营业务的企业。

We're thinking: While these laws are better for the users, innovators, and businesses than the vetoed SB 1047, some of them perpetuate a major mistake of that legislation by placing regulatory burdens on models rather than applications. A model's potential applications are unknown until someone implements them, and it makes no sense to limit — or burden with disclosure requirements — the good it might do. Applications, on the other hand, bring verifiable benefits and harms, and society would do well to limit the harms.

我们认为：虽然这些法律相比被否决的 SB 1047 法案对用户、创新者和企业更为有利，但其中部分条款延续了该立法的一个重大失误 —— 将监管重点放在模型而非具体应用上。在有人实际实现之前，模型的潜在应用场景是未知的，限制其可能产生的积极影响 —— 或是用披露要求增加其负担 —— 并不合理。另一方面，具体应用会带来可验证的益处和危害，而社会应当着力限制这些危害。

#### Better Agentic Prompts Automically

Honing an agent's prompt can yield better results than fine-tuning the underlying large language model via reinforcement learning.

#### 自动生成更优的智能体提示优化智能体（Agent）的提示词，相比通过强化学习微调底层大语言模型，能够产生更好的效果。

What's new: Lakshya A. Agrawal and colleagues at UC Berkeley, Stanford, BespokeLabs.ai, Notre Dame, Databricks, and MIT developed GEPA, an algorithm that improves the performance of agentic systems by improving their prompts. The authors position it as an efficient alternative to fine-tuning an agent's large language model via reinforcement learning.

最新进展：Lakshya A. Agrawal 与来自加州大学伯克利分校、斯坦福大学、BespokeLabs.ai、圣母大学、Databricks 和麻省理工学院的研究团队共同开发了 GEPA 算法，该算法通过优化提示词来提升 AI 智能体系统的性能。研究者认为，这种方法可以高效替代通过强化学习来微调 AI 智能体大语言模型的传统方案。

Key insight: Agentic models trained via reinforcement learning typically must take a complicated series of actions to earn a simple reward, including calling a large language model multiple times for different purposes, or modules, of the workflow. But a well designed prompt can take into account the various problems an agent may run into and thus guide the model more efficiently. The trick is to write prompts that anticipate such problems. To accomplish this, a large language model can analyze an agent's behavior as it responds to a given prompt, identify associations between the prompt and outcome (for instance, a failed tool call), and compose a more effective prompt.

核心洞见：通过强化学习训练的 AI 智能体通常需要执行一连串复杂操作才能获得简单奖励，这包括多次调用大语言模型来完成工作流程中的不同任务或模块。但精心设计的提示词（prompt）能够预先考虑到智能体可能遇到的各种问题，从而更高效地引导模型。关键在于编写能够预见此类问题的提示词。为此，大语言模型可以分析智能体对给定提示词的响应行为，识别提示词与结果（例如，失败的工具调用）之间的关联，进而生成更有效的提示词。

How it works: Prompting agents based on Alibaba's Qwen3-8B, the authors used GEPA to hone their performance on specific benchmarks. The method iteratively evolves a pool of candidate prompts, beginning with a simple prompt for each LLM call a module of the agent makes, such as "Respond to the query" or "Ensure the response is correct and adheres to the given constraints [specified in the benchmark inputs]." In each cycle, GEPA selects, modifies, and evaluates a prompt to generate a revised prompt that produces better results.

工作原理：作者基于阿里巴巴的 Qwen3-8B 大语言模型，通过向 AI 智能体提供提示，并使用 GEPA 方法来提升其在特定基准测试上的表现。该方法会迭代演化一个候选提示池，初始时使用简单的提示 —— 这些提示对应智能体各个模块对 LLM 的调用，比如「回答查询」或「确保回复正确并遵循给定的约束条件（在基准输入中指定）」。在每一轮循环中，GEPA 会选择一个提示进行修改和评估，最终生成经过优化的新提示，从而获得更好的结果。

* Given each prompt to be fed to the LLM (initially the default prompts, later revised prompts selected for their effectiveness), the agent responds to a random subset of examples from a benchmark's training set.

* 对于每个要输入到大语言模型（LLM）的提示（初始为默认提示，后续则选用因其有效性而筛选出的修订提示），该 AI 智能体会对从基准训练集中随机抽取的示例子集进行响应。

* GEPA selects which prompt to modify, alternating between the various modules. A separate Qwen3-8B instance examines the agent's traces (generated text, tool calls, and results) and revises the prompt.

* GEPA 选择需要修改的提示，并在不同模块之间轮换选择。一个独立的 Qwen3-8B 实例会分析智能体的运行轨迹（包括生成的文本、工具调用及其结果），并对提示进行优化改进。

* GEPA evaluates the revised prompt in a two-step process. First it feeds it to the agent along with the examples used previously and the prompts by other modules. If the revised prompt improves the agent's performance, GEPA adds it to a pool of candidate prompts and then scores its performance on each example in the benchmark's validation set.

* GEPA 采用两步流程来评估修订后的提示：首先，将修订后的提示与此前使用的示例及其他模块的提示一并提供给智能体。若该提示能提升智能体性能，GEPA 会将其纳入候选提示库，并针对基准验证集中的每个示例进行性能评分。

* From the pool, GEPA identifies prompts that achieved the highest score on at least one example. It selects a set of prompts (one for each module) for the next round of revision, prioritizing prompts that excelled on multiple questions.

* GEPA 从候选池中识别出至少在某个示例上得分最高的提示，并为下一轮修订选择一组提示（每个模块对应一个），优先考虑在多个问题上表现优异的提示。

* GEPA repeats the previous steps until it has exhausted a predefined processing budget. It chooses the set of prompts that achieved the highest average score across all examples in the validation set.

* GEPA 会重复前面的步骤，直到用完预定义的处理预算。然后选择在验证集所有样本上取得最高平均得分的提示（prompts）集合。

Results: The authors pitted custom and open-source agents that used GEPA against versions for which Qwen3-8B was fine-tuned on a given benchmark via Group Relative Policy Optimization (GRPO). They measured both the agents' performance and the number of agent executions required.

结果：作者让使用 GEPA 的定制化与开源智能体，与通过 Group Relative Policy Optimization（GRPO）在特定基准上微调过的 Qwen3-8B 版本进行了对抗性比较。他们同时评估了智能体的性能表现和所需的执行次数。

* Across HotpotQA (questions that require reasoning over multiple paragraphs), IFBench (following instructions), HoVer (verifying facts), and PUPA (which gauges balance between helpfulness and unwanted sharing of personal information), agents that used GEPA consistently achieved better performance on all four.

* 在 HotpotQA（需要多段落推理的问题）、IFBench（指令跟随）、HoVer（事实验证）和 PUPA（评估帮助性与不必要个人信息分享之间的平衡性）这四个基准测试中，采用 GEPA 的智能体在所有四项任务上都一致表现出了更优的性能。

* Moreover, they did this with far greater efficiency, requiring up to 35 times fewer agent executions.

Yes, but: The authors compared GEPA to fine-tuning via reinforcement learning using a single, relatively small model. Questions remain regarding how the results would scale to larger models or generalize to other models, and how GEPA would compare to supervised fine-tuning.

* 此外，他们实现这一目标的效率要高得多，所需的智能体执行次数最多可减少至原来的 1/35。

不过需要指出的是：作者仅将 GEPA 与使用单个相对较小模型进行强化学习微调的方法进行了对比。关于这种方法在更大规模模型上的扩展性、在其他模型上的泛化能力，以及 GEPA 与监督微调方法的比较效果，仍有待进一步研究。

Why it matters: Methodically revising prompts can help agents perform better than fine-tuning via reinforcement learning, and it requires far fewer examples and executions.

为什么这很重要：系统地优化提示（prompts）能够让智能体获得比强化学习微调更优的表现，而且所需的训练样本和执行次数都要少得多。

We're thinking: While it's unclear how this method compares to supervised fine-tuning, the ability to boost agentic performance without reinforcement learning may be especially valuable in low-data situations or where agent executions are expensive.

我们认为：虽然这种方法与监督微调（Supervised Fine-tuning）的对比效果尚不明确，但在数据匮乏或智能体运行成本较高的场景中，无需强化学习就能提升 AI 智能体（AI Agent）性能的能力可能具有特殊价值。
