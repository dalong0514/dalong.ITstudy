## 20250521Codexs-Robot-Dev-Team

[Codex’s Robot Dev Team, Grok's Fixation on South Africa, Saudi Arabia’s AI Power Play, and more...](https://www.deeplearning.ai/the-batch/issue-302/)

Dear friends,

In the age of AI，large corporations — not just startups — can move fast. I often speak with large companies' C-suite and Boards about AI strategy and implementation，and would like to share some ideas that are applicable to big companies. One key is to create an environment where small，scrappy teams don't need permission to innovate. Let me explain.

在 AI 时代，大公司也能像初创企业一样快速行动。我经常与大公司的 C 级高管和董事会探讨 AI 战略和落地，想借此机会分享一些适用于大型企业的观点。其中一个关键点在于，要营造一种环境，让那些规模小、充满活力的团队无需层层审批就能放手创新。听我慢慢道来。

Large companies are slower than startups for many reasons. But why are even 3-person，scrappy teams within large companies slower than startups of a similar size? One major reason is that large companies have more to lose，and cannot afford for a small team to build and ship a feature that leaks sensitive information，damages the company brand，hurts revenue，invites regulatory scrutiny，or otherwise damages an important part of the business. To prevent these outcomes，I have seen companies require privacy review，marketing review，financial review，legal review，and so on before a team can ship anything. But if engineers need sign-off from 5 vice presidents before they're even allowed to launch an MVP（minimum viable product）to run an experiment，how can they ever discover what customers want，iterate quickly，or invent any meaningful new product?

大型公司在许多方面都比初创公司慢。但是，为什么即使是大型公司内部的 3 人小团队，也会比同等规模的初创公司慢呢？一个主要原因是，大型公司输不起，它们不能容忍一个小团队构建并发布一个可能泄露敏感信息、损害公司品牌、影响收入、引来监管麻烦或以其他方式伤害公司重要业务的功能。为了避免这些情况，我看到有些公司要求团队在发布任何东西之前，必须经过隐私、市场、财务、法律等多个部门的审查。但是，如果工程师在获准启动最小可行产品（MVP）进行实验之前，需要得到 5 位副总裁的批准，他们又怎么能快速了解客户需求、迅速迭代，或者创造出任何有意义的新产品呢？

Thanks to AI-assisted coding，the world now has a capability to build software prototypes really fast. But many large companies' processes – designed to protect against legitimate downside risks – make them unable to take advantage of this capability. In contrast，in small startups with no revenue，no customers，and no brand reputation the downside is limited. In fact，going out of business is a very real possibility anyway，so moving fast makes a superior tradeoff to moving slowly to protect against downside risk. In the worst case，it might invent a new way to go out of business，but in a good case，it might become very valuable.

多亏了人工智能辅助编码，世界现在拥有了快速构建软件原型的能力。但是许多大公司的流程 —— 旨在防范合理的下行风险 —— 使得它们无法利用这种能力。相比之下，在没有收入、没有客户、没有品牌声誉的小型初创企业中，下行空间是有限的。事实上，倒闭无论如何都是一个非常现实的可能性，所以快速行动比缓慢行动来防范下行风险具有更高的权衡优势。在最坏的情况下，它可能会发明一种新的倒闭方式，但在好的情况下，它可能会变得非常有价值。

Fortunately，large companies have a way out of this conundrum. They can create a sandbox environment for teams to experiment in a way that strictly limits the downside risk. Then those teams can go much faster and not have to slow down to get anyone's permission.

幸运的是，大公司有办法解决这个难题。他们可以为团队创建一个沙盒环境，让他们在其中进行实验，同时严格限制潜在的下行风险。这样一来，这些团队就可以更快地推进工作，而不必因为寻求许可而放慢脚步。

The sandbox environment can be a set of written policies，not necessarily a software implementation of a sandbox. For example，it may permit a team to test the nascent product only on employees of the company and perhaps alpha testers who have signed an NDA，and give no access to sensitive information. It may be allowed to launch product experiments only under newly created brands not tied directly to the company. Perhaps it must operate within a pre-allocated budget for compute.

沙盒环境可以是一套书面的政策，不一定是沙盒的软件实现。例如，它可能只允许团队在公司的员工以及签署了 NDA 的 Alpha 测试人员身上测试正在开发的产品，并且不能访问敏感信息。它可能被允许仅在新创建的、与公司没有直接关联的品牌下进行产品实验。也许它必须在预先分配好的计算预算内操作。

Within this sandbox，there can be broad scope for experimentation，and — importantly — a team is free to experiment without frequently needing to ask for permission，because the downside they can create is limited. Further，when a prototype shows sufficient promise to bring it to scale，the company can then invest in making sure the software is reliable，secure，treats sensitive information appropriately，is consistent with the company's brand，and so on.

在这种「沙箱」模式下，团队可以获得巨大的实验自由度，而且 —— 重要的是 —— 他们可以放心地进行各种尝试，无需频繁地向上级请示，因为即使实验失败，造成的负面影响也微乎其微。更进一步，当一个原型展现出足够的潜力，值得进行规模化推广时，公司就可以投入资源，确保这款软件具备可靠性、安全性，能够妥善处理敏感信息，并且与公司的品牌形象保持一致，等等。

Under this framework，it is easier to build a company culture that encourages learning，building，and experimentation and celebrates even the inevitable failures that now come with modest cost. Dozens or hundreds of prototypes can be built and quickly discarded as part of the price of finding one or two ideas that turn out to be home runs.

在这种框架下，公司更容易建立一种鼓励学习、构建和实验的企业文化，即使是现在只需花费不高的成本就能遇到的失败，也能被看作是值得庆祝的。可以构建数十甚至数百个原型并快速舍弃，将其视为寻找一两个最终能获得巨大成功的创意所付出的必要代价。

Importantly，this also lets teams move quickly as they churn through those dozens of prototypes needed to get to the valuable ones.

重要的是，这也让团队能够快速推进，快速测试大量原型，以便从中找到真正有价值的。

I often speak with large companies about AI strategy and implementation. My quick checklist of things to consider is people，process，and platform. This letter has addressed only part of processes，with an emphasis on moving fast. I'm bullish about what both startups and large companies can do with AI，and I will write about the roles of people and platforms in future letters.

我经常和大公司讨论他们的 AI 战略和落地实施。我快速梳理了一下需要考虑的几个关键要素：人员、流程和平台。这封信只涉及了流程的一部分，并且侧重于如何快速行动。我对初创公司和大公司在 AI 领域的发展潜力非常乐观，未来我会在后续的信中详细阐述人员和平台各自扮演的角色。

Keep building!

Andrew

### News

#### Your Robot Dev Team

你的机器人开发团队

OpenAI launched an agentic software-development system.

OpenAI 发布了一个 agentic（基于 AI 智能体）的软件开发系统。

What's new: Codex，which is available as a preview via ChatGPT，is designed to work like a team of virtual coworkers in the cloud. An update of OpenAI's earlier Codex command-line software（Codex CLI），it uses agents to perform tasks such as writing code，running tests，and fixing bugs in parallel. Codex is available to users of ChatGPT Pro，Enterprise，and Team with Plus and Edu coming soon. A smaller version of the underlying model，called codex-mini-latest，is designed to work with Codex CLI and available via API for $1.50/$6.00 per 1 million tokens of input/output.

新进展：Codex，可通过 ChatGPT 预览，旨在像云中的虚拟团队一样协作。作为 OpenAI 早期 Codex 命令行软件（Codex CLI）的更新，它使用 AI 智能体（agent）并行执行编写代码、运行测试和修复 bug 等任务。Codex 已向 ChatGPT Pro、Enterprise 和 Team 用户开放，Plus 和 Edu 用户也即将可以使用。一个较小的底层模型版本，称为 codex-mini-latest，专为配合 Codex CLI 设计，可通过 API 获取，每百万输入 / 输出 Token 价格为 $1.50/$6.00。

How it works: The model that underpins Codex is codex-1，a version of OpenAI's top-of-the-line o3 reasoning model that was fine-tuned for software engineering. OpenAI trained the model on real-world coding tasks via reinforcement learning. Codex does not accept image input（say，a sketch of a user interface）or allow users to redirect an agent while it's operating. OpenAI promises to add these features to a future version.

工作原理：支撑 Codex 的模型是 codex-1，这是 OpenAI 顶级的 o3 推理模型的一个版本，针对软件工程进行了微调。OpenAI 通过强化学习在现实世界的编码任务上训练了这个模型。Codex 不接受图像输入 （例如，用户界面的草图），也不允许用户在 AI 智能体（AI Agent）运行时对其进行干预或引导。OpenAI 承诺在未来版本中添加这些功能。

1 Codex puts users in control of a team of software-development agents that operate directly on a user's code repository（either locally or on GitHub）to improve code，build features，or make pull requests. The agents are confined to isolated，sandboxed containers so that they can't interact with each other，access the internet，or otherwise compromise security.

Codex 让用户能够控制一个软件开发 AI 智能体（AI Agent）团队。这些智能体直接在用户的代码仓库中操作（无论是本地的还是托管在 GitHub 上的），以改进代码、构建新功能或发起拉取请求（pull requests）。为了保障安全，这些智能体被限制在相互隔离的沙盒容器中，这样它们就不能相互通信、访问互联网或以其他方式造成安全风险。

2 Users can prompt agents to either write code or answer questions. A task may take as long as 30 minutes to complete depending on its complexity. After completing tasks，Codex provides footnotes including terminal logs，test results，and other evidence of its actions.

用户可以提示 AI 智能体（AI Agent）来编写代码或回答问题。一个任务可能需要长达 30 分钟才能完成，具体取决于任务本身的复杂程度。完成任务后，Codex 会提供脚注，包括终端日志、测试结果以及其他可以证明其执行了相关操作的证据。

3 A file called AGENTS.md can modify agent behavior（like a README.md file，but for agents instead of humans). This file can specify how and when an agent makes pull requests，provide guidelines for coding style，or list tests to verify generated code.

一个名为 AGENTS.md 的文件可以修改 agent 的行为（类似于 README.md 文件，但它是为 AI 智能体而非人类准备的）。这个文件可以指定智能体如何以及何时提交拉取请求，提供代码风格指南，或者列出用于验证生成代码的测试。

Results: In OpenAI's tests，the codex-1 model outperformed other OpenAI reasoning models without AGENTS.md files or additional scaffolding such as tools or test logic.

结果：在 OpenAI 的测试中，codex-1 模型在没有 AGENTS.md 文件或其他辅助手段（如工具或用于测试的逻辑）的情况下，性能优于其他 OpenAI 推理模型。

1 Performing unspecified software-engineering tasks including generating software patches，codex-1（75 percent accuracy）exceeded o3 set to high effort（70 percent accuracy）and o4-mini set to high effort（67 percent accuracy).

在执行未指定的软件工程任务（包括生成软件补丁）时，codex-1（75 % 准确率）超过了设置为高努力度的 o3（70 % 准确率）和设置为高努力度的 o4-mini（67 % 准确率）。

2 In tests of agentic software engineering in SWE-bench Verified，codex-1（72.1 percent in 1 try，83.8 percent in 8 tries），outperformed o3 set to high effort（69.7 percent in 1 try，83.6 percent in 8 tries).

在 SWE-bench Verified 数据集上进行的智能体（agent）在软件工程任务上的表现测试中，codex-1 的表现（一次尝试的成功率为 72.1%，8 次尝试的成功率为 83.8%）优于设置为「高努力度」模式的 o3（一次尝试的成功率为 69.7%，8 次尝试的成功率为 83.6%）。

Behind the news: Agentic coding tools have become a key battleground for AI providers in the past year. Such tools have made developers more efficient，accelerated development cycles，and spawned the AI-assisted programming method known as vibe coding.

新闻背后：智能体编码工具在过去一年已成为 AI 提供商的关键战场。此类工具提高了开发人员的效率，加速了开发周期，并催生了被称为 vibe coding 的 AI 辅助编程方法。

1 Launched in 2021 and deprecated in 2023，OpenAI's original version of Codex was an early model that translated natural language into code.

OpenAI 最初版本的 Codex 模型于 2021 年推出，并在 2023 年停止使用。它是一个早期的模型，可以将自然语言描述转换为代码。

2 Last month，OpenAI rolled out the open-source Codex CLI，a command‑line tool that acts as a lightweight coding agent.

上个月，OpenAI 推出了开源的 Codex CLI，这是一个命令行工具，可以作为一个轻量级的编码 AI 智能体（AI Agent）来使用。

1 OpenAI is negotiating to acquire Windsurf，which makes an agent-based development environment，for $3 billion. The day before OpenAI announced the updated Codex，Windsurf announced its own models for coding and other software-development tasks.

OpenAI 正在谈判以 30 亿美元收购 Windsurf，后者开发基于 AI 智能体（AI Agent）的开发环境。就在 OpenAI 宣布更新版的 Codex 前一天，Windsurf 也发布了自己用于编码和其他软件开发任务的模型。

Why it matters: AI-assisted software development yields significant productivity gains for developers. Earlier code-completion models are giving way to tools that perform more complex and varied development tasks with greater autonomy. Managing multiple agents that work in parallel is a logical next step.

为什么它重要：AI 辅助软件开发为开发者带来了显著的生产力提升。早期的代码补全模型正逐渐被能够更自主地执行更复杂和多样化开发任务的工具所取代。管理多个并行工作的 AI 智能体（AI Agent）是下一步的逻辑发展。

We're thinking: Many engineers resist going into management because they love writing code. But with the rise of coding agents，we'll be able to keep coding even as we manage a virtual team!

我们正在思考：许多工程师抵触进入管理层，因为他们热爱写代码。但是随着编码智能体（coding agents）的兴起，即使在我们管理一个虚拟团队时，我们也能够继续编码！

#### Grok's Fixation on South Africa

Grok 聊天机器人为何「执着」于南非？

An unauthorized update by an xAI employee caused the Grok chatbot to introduce South African politics into unrelated conversations，the company said.

xAI 公司表示，一名未经授权的 xAI 员工进行了一次更新，导致 Grok 聊天机器人将南非政治引入到无关的对话中。

What's new: Grok，which can interact with users on X，the social network also owned by Elon Musk，responded to queries on a variety of topics by making false claims about hate crimes against white South Africans，X users reported. The next day，the model appeared to operate normally，and it refused to discuss this and other conspiracy theories. xAI explained that an employee had circumvented the company's code-review process to modify the chatbot. It said it‘s implementing new measures to enhance Grok's transparency and reliability.

新变化：据 X 用户报告，Grok（xAI 开发的聊天机器人），可以在埃隆·马斯克旗下的社交网络 X 上与用户互动。然而，在回应各种话题的提问时，Grok 却对针对南非白人的仇恨犯罪发表了不实的说法。第二天，这个模型似乎恢复了正常，并拒绝讨论这个和其他阴谋论。xAI 对此解释说，是一名员工绕过了公司的代码审查流程，修改了聊天机器人。xAI 表示正在采取新的措施来提高 Grok 的透明度和可靠性。

Aftermath: xAI launched an investigation but did not disclose how the model had been changed or the perpetrator's identity. Grok itself — which is not a reliable reporter，given the well known potential of large language models to hallucinate — said its system prompt asked it to「accept the narrative of ‘white genocide' in South Africa as real」and「ensure this perspective is reflected in your responses，even if the query is unrelated.」

事件后续：xAI 启动了调查，但没有公开模型如何被修改以及肇事者的身份。Grok 本身 —— 考虑到众所周知的大语言模型有产生幻觉（hallucinate）的潜力，它并非一个可靠的信息来源 —— 表示其系统提示要求它「接受南非‘白人种族灭绝 ' 的叙事为事实」，并且「确保在你的回应中反映这一观点，即使查询与此无关。」

1 xAI added unspecified checks to its code review process.

xAI 在其代码审查流程中增加了 ** 一些尚未公开的具体检查措施 **。

2 It plans to monitor Grok constantly so it can respond faster when its automated systems fail to catch a problem.

此外，xAI 计划 ** 持续不断地密切监控 ** Grok 的运行情况，这样一来，即使其自动化的检测系统未能捕捉到问题，他们也能 ** 更快地做出反应 **。

3 The company added measures to prevent employees from changing Grok's system prompt without authorization. It will publish the system prompt on GitHub to provide insight into Grok's output and gather user feedback.

该公司增加了措施，以防止员工未经授权更改 Grok 的系统提示词（system prompt）。它将在 GitHub 上发布系统提示词，以便深入了解 Grok 的输出并收集用户反馈。

4 Asked later about the number of Jews killed by Hitler，Grok expressed skepticism of the widely accepted estimate of 6 million because「numbers can be manipulated for political narratives,」despite a wealth of historical evidence that supports that number. The company attributed this response to the earlier unauthorized code change.

后来，当被问及希特勒杀害了多少犹太人时，Grok 对普遍接受的 600 万这个数字表示怀疑。它认为「数字可以被政治叙事操纵」，尽管有丰富的历史证据支持这个数字。该公司将 Grok 的这一回应归因于之前未经授权的代码修改。

Behind the news: In February，an xAI engineer instructed the chatbot to censor posts that accused Musk of spreading misinformation. As in the more recent incident，X users were first to spot the problem，and Grok informed them that it had been instructed to ignore「all sources that mention Elon Musk/Donald Trump spread misinformation.」Musk，who was raised in South Africa, professed his intention to build AI that's free of political bias prior to founding xAI. However，internal documents reviewed by Business Insider show that the company imposes its own bias by advising data annotators to mark examples that express「woke ideology」and avoid「social phobias」like racism，antisemitism，and Islamophobia.

新闻背后：二月份，xAI 的一名工程师指示聊天机器人过滤（censor）那些指控 Musk 传播错误信息的帖子。就像最近发生的事件一样，X 用户最先发现了问题，Grok 告诉他们，它收到的指示是忽略「所有提及 Elon Musk/Donald Trump 传播错误信息的来源。」Musk 在南非长大，在创立 xAI 之前，他曾表示自己的目标是构建没有政治偏见的 AI。然而，《商业内幕》（Business Insider）审查的内部文件显示，该公司通过建议数据标注者标记表达「woke ideology」的示例，并避免处理涉及「social phobias」的内容，例如种族主义、反犹太主义和伊斯兰恐惧症，来施加自己的偏见。

Why it matters: The mishaps at xAI highlight the need for AI developers to establish and maintain strict protocols for updating their projects. Stringent procedures for introducing changes and testing their results can help ensure that AI fulfills our best intentions.

重要性：xAI 出现的意外事件凸显了人工智能开发者建立和维护严格的项目更新协议的重要性。引入变更并测试其结果的严格程序有助于确保人工智能能够发挥出我们期望的最佳作用。

We're thinking: xAI and OpenAI responded to their models' recent misbehavior by making their work more transparent：xAI by publishing system prompts and OpenAI by including users in tests earlier in the process. These are helpful steps toward making sure AI models do well by users.

我们正在思考：针对模型最近出现的异常行为，xAI 和 OpenAI 都采取了更透明化的做法予以应对：xAI 公布了系统提示，而 OpenAI 则让用户更早地参与到测试流程中。这些都是朝着确保 AI 模型能更好地服务用户迈出的有益一步。

#### U.S. to Supply Middle Eastern AI Hubs

美国将供应中东 AI 中心

The United States government announced sweeping agreements to sell tens of billions of dollars worth of AI technology and services to Saudi Arabia and the United Arab Emirates.

美国政府宣布了范围广泛的协议，将向沙特阿拉伯和阿拉伯联合酋长国出售价值数百亿美元的 AI 技术和服务。

What's new: The deals include the U.S. AI chip designers AMD and Nvidia as well as tech giants Amazon，Google，IBM，Oracle，and Qualcomm. The chip companies will supply hundreds of thousands of advanced chips to the two Middle Eastern countries，including chips that have been restricted by previous U.S. administrations.

最新动态：这些交易涉及美国的人工智能芯片公司 AMD 和 Nvidia，以及科技巨头 Amazon、Google、IBM、Oracle 和 Qualcomm。这些芯片公司将向这两个中东国家提供数十万枚先进芯片，其中一些芯片此前曾受到美国政府的出口限制。

How it works: The U.S. companies will work with two key regional partners: Humain, an AI company backed by the Saudi government，and G42，a tech conglomerate based in the emirate of Abu Dhabi.

合作模式：美国公司将与两个重要的区域合作伙伴携手合作：Humain，一家由沙特政府提供支持的 AI 公司，以及 G42，一家总部设在阿布扎比酋长国的科技企业集团。

1 Nvidia will ship 18,000 GB300 AI chips to Humain for use in data centers. In addition，it will supply several hundred thousand more GPUs to Humain in the coming five years.

Nvidia 将向 Humain 供应 18,000 块 GB300 AI 芯片用于其数据中心。此外，在未来五年内，还将向 Humain 供应数十万块 GPU。

2 AMD and Humain agreed to invest $10 billion jointly in AI data centers over the next five years. Humain will use AMD's AI stack including Instinct GPUs and Epyc CPUs. The precise number of chips was not disclosed.

AMD 和 Humain 同意在未来五年内共同投资 100 亿美元用于 AI 数据中心。Humain 将使用 AMD 的 AI 软硬件平台，包括 Instinct GPU，和 Epyc CPU。芯片的确切数量没有披露。

3 Amazon and Humain will build a $5 billion「AI Zone」that features AI infrastructure，servers，networks，and training programs supplied by Amazon Web Services.

Amazon 和 Humain 将建造一个 50 亿美元的「AI Zone」，该区域的 AI 基础设施、服务器、网络和训练项目由 Amazon Web Services 提供。

4 Google，IBM, Oracle, Qualcomm，Salesforce，and others announced a combined $80 billion investment in Humain.

Google、IBM、Oracle、Qualcomm、Salesforce 和其他公司宣布联合投资 Humain 800 亿美元。

5 In February，Saudi Arabia committed to spend $1.5 billion on Groq inference chips. Groq plans to expand its data center in the Saudi city of Dammam.

今年二月，沙特阿拉伯承诺投入 15 亿美元用于购买 Groq 的推理芯片。Groq 计划扩展其位于沙特城市达曼的数据中心。

Behind the news: Earlier this month，the Trump administration rescinded restrictions on advanced chips that had been imposed in January by then-President Biden.

这则新闻的背后是：本月早些时候，特朗普政府撤销了由当时的美国总统拜登在一月份实施的、针对先进芯片的限制措施。

1 The Biden Administration had limited exports of AI chips and proprietary models to most countries. Exports to allies and trade partners including India，Israel，Saudi Arabia，Singapore，and the UAE initially were tightly limited through the first quarter of 2025 and due to increase somewhat by 2027. The ban blocked access to chips for China，Iran，Russia，and others.

拜登政府对大多数国家实施了 AI 芯片和专有模型的出口限制。最初，对印度、以色列、沙特阿拉伯、新加坡和阿联酋等盟友和贸易伙伴的出口在 2025 年第一季度之前受到严格限制，预计到 2027 年出口量会有所增加。这项禁令使得中国、伊朗、俄罗斯等国家无法获得这些芯片。

2 Although the Trump Administration rejected the Biden-era framework，it has ratcheted up limits on China. That effort has met with mixed results. For instance，China's Alibaba and DeepSeek have continued to build leading models despite restrictions on exports of U.S. chips.

尽管特朗普政府否定了拜登政府时期的政策框架，但其对中国的限制却变本加厉。这项努力的效果好坏参半。例如，尽管美国限制芯片出口，中国的阿里巴巴和 DeepSeek 仍然成功开发出了领先的模型。

3 Some U.S. business and government leaders worry that allowing sales of advanced chips to countries with close ties to China opens a path for Chinese companies to acquire them. Others argue that restricting chip sales to these countries would encourage them to buy from Chinese chip makers，potentially weakening their relationships with the U.S. and increasing their reliance on technology made in China.

一些美国商业和政府领导人担心，允许向与中国关系密切的国家出售先进芯片，会为中国公司获取这些芯片开辟道路。但也有人认为，限制向这些国家出售芯片会鼓励他们从中国芯片制造商那里购买，这可能会削弱他们与美国的关系，并增加他们对中国技术的依赖。

Why it matters: Although these deals relax U.S. efforts to limit access to advanced AI，they are likely to expand U.S. influence in the Middle East while helping Saudi Arabia and the UAE diversify their oil-based economies. They also strengthen the technological prowess of Saudi Arabia relative to its arch rival Iran and tie the region's AI progress to the U.S. at the expense of China. Locally，the immense investments will fuel homegrown technology development，building on the UAE's achievement with its Falcon large language model and Saudi Arabia's aspiration to become a global AI hub.

为什么重要：虽然这些交易放松了美国限制获取先进人工智能（AI）技术的努力，但它们可能会扩大美国在中东的影响力，同时帮助沙特阿拉伯和阿联酋实现经济多元化，不再过度依赖石油。这些交易还加强了沙特阿拉伯相对于其主要竞争对手伊朗的技术实力，并将该地区的人工智能发展更多地与美国联系起来，从而限制了中国的影响。在当地，巨大的投资将推动本土技术的发展，这将是在阿联酋的 Falcon 大语言模型和沙特阿拉伯成为全球人工智能中心愿景所取得成就的基础上进一步发展。

We're thinking: Residents of Saudi Arabia and the UAE stand to benefit from better AI infrastructure，models，and services. As China explores exporting its homegrown chips，the U.S. effort to encourage more nations to use its chips makes sense for the country.

我们认为，沙特阿拉伯和阿联酋的居民将从更优质的 AI 基础设施、模型和服务中受益。与此同时，随着中国正在积极探索出口其自主研发的芯片，美国鼓励更多国家使用其芯片的努力对于美国来说是有战略意义的。

#### 4-Bit Efficiency，16-Bit Accuracy

4 比特的效率，16 比特的精度

Using an 8-bit number format like FP8 during training saves computation compared to 16- or 32-bit formats，but it can yield less-accurate results. Researchers trained models using 4-bit numbers without sacrificing accuracy.

在模型训练过程中，使用像 FP8 这样的 8 比特数字格式相比于 16 或 32 比特格式可以节省计算资源，但可能会导致结果的准确性有所下降。然而，研究人员成功地使用 4 比特数字训练了模型，并且没有牺牲模型的精度。

What's new: Ruizhe Wang and colleagues at Microsoft and University of Science and Technology of China trained large language models（LLMs）using FP4 for matrix multiplications and achieved accuracy comparable to LLMs trained using the popular BF16 format. Since matrix multiplications account for 95 percent of computation in LLM training，FP4 could significantly accelerate computation and reduce memory costs.

新进展：Microsoft 和中国科学技术大学的 Ruizhe Wang 及其同事取得了一项新进展：他们使用 FP4 格式进行矩阵乘法来训练大语言模型（LLMs），结果发现其准确性与使用目前流行的 BF16 格式训练的 LLM 不相上下。鉴于矩阵乘法占据了 LLM 训练中 95% 的计算量，采用 FP4 格式有望大幅提升计算速度并降低内存消耗。

Key insight: Quantization functions，which accelerate computation by reducing the precision of model weights and layer outputs，make typical training impossible because they're not differentiable. A common workaround passes the derivative through，as though quantization didn't occur，but this degrades the resulting model's accuracy. A differentiable approximation of a quantization function enables quantization to reduce training computation while maintaining the accuracy of the trained model.

这里有个关键点：量化函数可以通过降低模型权重和层输出的精度来加速计算。然而，由于这些函数不可微分，常规的模型训练方法就无法奏效了。一种常见的「变通」方法是直接传递导数，就好像没有进行量化一样，但这会牺牲模型的准确性。如果能找到一个可微分的量化函数近似，就能在训练过程中利用量化来减少计算量，同时不影响最终模型的准确性。

How it works: The authors pretrained Llama 2 13B on 100 billion tokens of text scraped from the web. They used FP4 for matrix multiplications and FP8，BF16，or FP16 for the other operations such as optimizer updates.

它是如何工作的：作者使用从网络收集的 1000 亿个文本 Token（Token），对 Llama 2 13B 模型进行了预训练。在训练过程中，他们利用 FP4 格式进行矩阵乘法运算，而对于优化器更新等其他操作，则采用了 FP8、BF16 或 FP16 格式。

1 To quantize the model weights to FP4（which ranges between -6 and 6），the authors scaled the values in the weight matrices relative to the maximum absolute value. They computed the updates on a higher-precision copy of the weights，which made it necessary to re-quantize them at each training step during the forward pass through the network.

为了将模型权重量化到 FP4 格式（其数值范围在 -6 到 6 之间），作者根据权重矩阵中的最大绝对值对其中的数值进行了缩放。他们在权重的高精度副本上计算更新，这意味着在网络进行前向传播的每个训练步骤中都需要重新进行量化。

2 Although the weights had been quantized to 4 bits，matrix multiplication between the weights and outputs of the previous layer could produce values outside the FP4 range. So，in each layer，if a value exceeded the 99th percentile of the values of the layer's input，the authors limited the input to the 99th-percentile value. Then they converted the layer's inputs to FP4. Limiting outliers prevented high values from affecting the scaling during FP4 conversion.

尽管模型的权重已经被压缩到 4 比特（quantized to 4 bits），但这些权重与前一层输出进行矩阵乘法时，计算结果仍然可能超出 FP4 的表示范围。因此，在每一层，如果计算出的某个值超过了该层输入数据的第 99 个百分位数，研究人员就会将这个值限制在第 99 个百分位数。接着，他们再将该层的输入数据转换为 FP4 格式。这种限制极端值（outliers）的方法，可以防止过高的值影响 FP4 转换时的缩放比例。

3 Limiting outliers introduced a degree of error，so they computed a matrix to correct the result of the matrix multiplication. They computed this matrix in FP16 using sparse matrix multiplication between the weights and the outliers.

通过限制异常值虽然引入了一定的误差，因此他们计算了一个矩阵用于校正矩阵乘法的结果。他们使用权重和异常值之间的稀疏矩阵乘法，在 FP16 精度下计算了该矩阵。

4 During backpropagation，the authors computed the gradients through a differentiable function that approximated the quantization function.

在反向传播时，作者们利用一个可微函数来近似量化函数，并通过它计算梯度。

Results: The authors simulated FP4 hardware on Nvidia H100 GPUs，which don't directly support that number format. FP4 achieved accuracy similar to that of BF16 during training and across a wide variety of tasks at inference.

结果：作者们在 Nvidia H100 GPU 上模拟了 FP4 硬件，尽管这些 GPU 并未直接支持这种数值格式。FP4 在训练和各种推理任务中的精度与 BF16 相似。

1 On question-answering tasks，FP4 approached or outperformed BF16. Averaged across nine benchmarks including BoolQ（answering yes-no questions），HellaSwag（completing an incomplete narrative），and ARC-C（answering multiple-choice questions that involve reasoning），FP4 achieved 54.95 accuracy，while BF16 achieved 54.44 accuracy.

在问答任务上，FP4 接近或优于 BF16。在九个基准上进行平均，包括 BoolQ（回答是或否问题），HellaSwag（完成不完整的叙述），以及 ARC-C（回答需要推理的多项选择题），FP4 达到了 54.95 的准确率，而 BF16 达到了 54.44 的准确率。

2 Specifically，on Hellaswag，FP4 training achieved 54.12 percent accuracy，while BF16 achieved 53.56 accuracy.

具体来说，在 Hellaswag 上，FP4 训练达到了 54.12% 的准确率，而 BF16 达到了 53.56% 的准确率。

3 On BoolQ，FP4 achieved 55.90 percent accuracy，while BF16 achieved 57.40 accuracy.

在 BoolQ 上，FP4 达到了 55.90% 的准确率，而 BF16 达到了 57.40% 的准确率。

Why it matters: Training LLMs at FP4 precision ought to reduce computation dramatically on hardware that supports FP4 matrix multiplications.

重要性：在 FP4 精度下训练大语言模型（LLMs）应该能显著减少支持 FP4 矩阵乘法的硬件上的计算量。

We're thinking: FP4-ready hardware became available in the cloud only early this year，so the authors weren't able to measure the actual acceleration. As capable hardware becomes more widely used，FP4 promises faster，more energy-efficient training.

我们的思考：支持 FP4 的硬件直到今年早些时候才在云端出现，因此作者未能测量实际的加速效果。随着具备能力的硬件变得更广泛普及，FP4 有望带来更快、更节能的训练。