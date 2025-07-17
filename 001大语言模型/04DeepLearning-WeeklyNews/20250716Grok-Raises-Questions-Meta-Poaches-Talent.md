## 20250716Grok-Raises-Questions-Meta-Poaches-Talent

[Grok Raises Questions, Meta Poaches Talent, California Reframes AI Regulations, and more...](https://www.deeplearning.ai/the-batch/issue-310/)

Dear friends,

The invention of modern writing instruments like the typewriter made writing easier，but they also led to the rise of writer's block，where deciding what to write became the bottleneck. Similarly，the invention of agentic coding assistants has led to a new builder's block，where the holdup is deciding what to build. I call this the Project Management Bottleneck.

现代写作工具，比如打字机的出现，让写作变得更容易，但它们也催生了一种「写作瓶颈（writer's block）」现象 —— 决定写什么，反而成了最棘手的问题。与此类似，生成式 AI（Generative AI）驱动的 AI 智能体（AI Agent）编码助手问世后，也带来了一种新的「构建者瓶颈（builder's block）」—— 现在最大的挑战在于决定要开发什么。我将这种现象称为「项目管理瓶颈（Project Management Bottleneck）」。

Product management is the art and science of deciding what to build. Because highly agentic coding accelerates the writing of software to a given product specification，deciding what to build is the new bottleneck，especially in early-stage projects. As the teams I work with take advantage of agentic coders，I increasingly value product managers（PMs）who have very high user empathy and can make product decisions quickly，so the speed of product decision-making matches the speed of coding.

产品管理本身就是一门艺术和科学，旨在明确「要构建什么」。由于高智能化的代理式编码（agentic coding）能大大加快软件的编写速度，一旦产品规范确定，那么「决定要构建什么」就成了新的瓶颈，尤其是在项目早期阶段。因此，随着我所在团队日益依赖这些 AI 智能体编码工具，我越来越看重那些能设身处地为用户着想、并能迅速做出产品决策的产品经理（PMs），这样才能让产品决策的速度与代码编写的速度保持同步。

PMs with high user empathy can make decisions by gut and get them right a lot of the time. As new information comes in，they can keep refining their mental models of what users like or do not like — and thereby refine their gut — and keep making fast decisions of increasing quality.

那些拥有高度用户同理心的 PM（Product Managers），常常能凭直觉做出决策，而且多数时候都判断得非常准确。随着新信息的不断涌入，他们会持续完善自己脑海中关于用户喜好和厌恶的「心理模型」—— 这反过来也磨砺了他们的直觉 —— 从而能够不断快速地做出更高质量的决策。

Many tactics are available to get user feedback and other forms of data that shape our beliefs about users. They include  conversations with a handful of users，focus groups，surveys，and A/B tests on scaled products. But to drive progress at GenAI speed，I find that synthesizing all these sources of data in a PM's gut helps us move faster.

为了帮助我们更好地理解用户，市面上有许多方法可以获取用户反馈和其他形式的数据。这些方法包括与少数用户的对话、焦点小组（focus groups）、问卷调查，以及在成熟产品上进行的 A/B 测试。然而，我发现，要想以 GenAI（生成式 AI）的速度推进项目，将所有这些数据来源整合进 PM 的直觉中，能帮助我们行动得更快。

Let me illustrate with an example. Recently，my team debated which of 4 features users would prefer. I had my instincts，but none of us were sure, so we surveyed about 1,000 users. The results contradicted my initial beliefs — I was wrong! So what was the right thing to do at this point?

让我用一个例子来说明。最近，我的团队讨论了用户会更喜欢哪四项功能。我凭直觉认为，但我们谁也拿不准，所以我们调查了大约 1,000 名用户。结果与我最初的信念相悖 —— 我错了！那么，当时该怎么做才是对的呢？

1 Option 1：Go by the survey and build what users told us clearly they prefer.

选项 1：根据调查结果，开发用户明确告诉我们他们喜欢的东西。

2 Option 2：Examine the survey data in detail to see how it changes my beliefs about what users want. That is，refine my mental model of users. Then use my revised mental model to decide what to do.

选项 2：仔细审视调查数据，看看它如何改变我对用户需求的理解。也就是说，不断完善我对用户行为的心理模型（mental model）。然后，利用我修正后的心理模型来做出决策。

Even though some would consider Option 1 the「data-driven」way to make decisions，I consider this an inferior approach for most projects. Surveys may be flawed. Further，taking time to run a survey before making a decision results in slow decision-making.

尽管有些人可能会把选项 1 视为「数据驱动」的决策方式，但我认为这对于大多数项目来说都不是一个理想的办法。调查本身可能存在缺陷。而且，在做出决策前花时间进行调查，会拖慢决策进程。

In contrast，using Option 2，the survey results give much more generalizable information that can help me shape not just this decision，but many others as well. And it lets me process this one piece of data alongside all the user conversations，surveys，market reports，and observations of user behavior when they're engaging with our product to form a much fuller view on how to serve users. Ultimately，that mental model drives my product decisions.

与此形成对比的是，如果采用选项 2，调查结果能提供更具普适性的信息，这些信息不仅能帮助我做出当前的决策，还能为我未来的许多其他决策提供参考。同时，它还让我能够将这一个数据点与所有的用户访谈、问卷调查、市场报告以及用户在使用我们产品时的行为观察结合起来分析，从而对如何更好地服务用户形成一个更全面的认知。最终，正是这种心智模型（mental model）指导着我的产品决策。

Of course，this technique does not always scale. For example，with programmatic online advertising in which AI might try to optimize the number of clicks on ads shown，an automated system conducts far more experiments in parallel and gathers data on what users do and do not click on，to filter through a PM's mental model of users. When a system needs to make a huge number of decisions，such as what ads to show（or products to recommend）on a huge number of pages，PM review and human intuition do not scale.

当然，这种方法并非总是能实现规模化（scale）。例如，在程序化在线广告领域，AI（Artificial Intelligence）可能会尝试优化广告的点击量，这时自动化系统会并行进行大量实验，收集用户点击了什么、没点击什么的数据，从而不断完善产品经理（PM）对用户的心智模型。当一个系统需要做出海量决策时，比如在无数页面上展示哪些广告（或推荐哪些产品），仅凭产品经理的审阅和人类的直觉就无法应对如此大规模的需求了。

But in products where a team is making a small number of critical decisions such as what key features to prioritize，I find that data — used to help build a good mental model of the user，which is then applied to make decisions very quickly — is still the best way to drive rapid progress and relieve the Product Management Bottleneck.

但是，在一个团队需要做出少量关键决策的产品开发中（比如决定哪些核心功能优先推进），我发现数据依然是推动快速发展和缓解产品管理瓶颈（Product Management Bottleneck）的最佳途径。它能帮助我们构建用户清晰的心智模型，并在此基础上迅速做出决策。

Keep building!

Andrew

### News

#### Grok 4 Shows Impressive Smarts，Questionable Behavior

Grok 4 智能惊艳，但行为引人质疑

xAI updated its Grok vision-language model and published impressive benchmark results. But，like earlier versions，Grok 4 showed questionable behavior right out of the gate.

xAI 更新了其 Grok 视觉 - 语言模型（vision-language model），并公布了令人瞩目的基准测试结果。然而，与早期版本类似，Grok 4 甫一亮相就表现出了令人质疑的行为。

What's new：The update to xAI's flagship vision-language model，which operates the chatbot integrated with the X social media platform，comes in two versions：Grok 4，which improves the earlier version's knowledge，reasoning，and voice input/output，and Grok 4 Heavy，a variant that uses a multi-agent framework to solve more-demanding reasoning tasks. Like its predecessor，Grok 4 is designed to produce output that may challenge conventional wisdom，particularly by weighing posts written by X users including X CEO Elon Musk.

最新消息：xAI 旗下的旗舰视觉 - 语言模型（vision-language model）迎来了更新。这个模型正是驱动集成在 X 社交媒体平台上的聊天机器人的核心。此次更新推出了两个版本：Grok 4 和 Grok 4 Heavy。Grok 4 在前一版本的基础上，大幅提升了知识储备、推理能力和语音输入 / 输出功能；而 Grok 4 Heavy 则是其一个特别版本，它利用多智能体框架（multi-agent framework）来处理那些更为复杂的推理任务。与它的前辈一样，Grok 4 的设计初衷就是生成可能挑战传统认知的回答，尤其会结合和分析包括 X 首席执行官 Elon Musk 在内的 X 用户发布的帖子内容。

1 Input/output：Text，images in and out (app up to 128,000 tokens; API up to 256,000 tokens)

输入 / 输出：支持文本和图像的输入与输出 （应用程序（app）最多支持 128,000 个 Token；API 最多支持 256,000 个 Token）

2 Architecture：Mixture of experts transformer，1.7 trillion parameters

架构：采用专家混合 Transformer（Mixture of experts Transformer）架构，拥有 1.7 万亿个参数

3 Features：Reasoning，web search，code execution，structured outputs，improved voice mode

功能：推理（Reasoning）、网页搜索（web search）、代码执行（code execution）、结构化输出（structured outputs）和改进的语音模式（improved voice mode）

4 Availability：Grok 4 $30 per month，Grok Heavy $300 per month，API $3.00/$0.75/$15.00 per 1 million tokens input/cached/output tokens

可用性：Grok 4 每月 30 美元，Grok Heavy 每月 300 美元；API 服务的定价为：每百万个输入 Token（Token）3.00 美元，缓存 Token 0.75 美元，以及输出 Token 15.00 美元。

5 Undisclosed：Architectural details，training methods，training datasets，pretraining knowledge cutoff

未披露信息：架构细节、训练方法、训练数据集、预训练知识截止日期

How it works：xAI has not yet published a model card or described how it built Grok 4. However，it did reveal broad outlines.

工作原理：xAI 尚未发布 Grok 4 的模型卡（model card），也未详细描述其构建方式。然而，xAI 确实披露了一些大致的框架。

1 Training the new model consumed more than an order of magnitude more processing power than training the previous version.

训练新模型所消耗的处理能力，比训练旧版本模型多了一个数量级。

2 Grok 4 was pretrained to predict the next token in math，coding，and other data. It was fine-tuned via reinforcement learning on chain-of-thought reasoning. Unlike Grok 3，it was trained to use certain tools. In a launch video，Musk promised to provide more sophisticated tools，such as finite element analysis and flow dynamics，later in the year.

Grok 4 经过预训练，能够预测数学、编程及其他数据中的下一个 Token。它还通过强化学习对思维链推理能力进行了微调。与 Grok 3 不同的是，Grok 4 被训练来使用某些工具。在一段发布视频中，Musk 承诺将在今年晚些时候提供更复杂的工具，例如有限元分析（finite element analysis）和流体动力学（flow dynamics）等。

3 Grok 4 Heavy is an agentic mode that spawns multiple agents that process input independently，in parallel. The agents compare findings and decide on the best answer. Musk said they determine the best answer not by majority vote by「comparing notes.」

Grok 4 Heavy 是一种智能体模式，它会启动多个 AI 智能体（AI Agent），这些智能体独立地、并行地处理输入。这些 AI 智能体比较各自的发现，并决定给出最佳答案。Musk 表示，它们不是通过简单多数投票，而是通过相互「对笔记」的方式来确定最佳答案。

4 On the day of Grok 4's launch，users reported that the model，when asked its opinion on the Israeli-Palestinian conflict，searched X for Musk's statements on these issues and replied accordingly. Later，asked to give its surname with no other text，Grok 4 consistently replied「Hitler.」

在 Grok 4 发布当天，用户报告称，当模型被问及对以色列 - 巴勒斯坦冲突的看法时，它会在 X 上查询 Musk 关于这些问题的声明，并据此给出回复。后来，当只被要求给出姓氏，而没有其他提示时，Grok 4 总是回复「Hitler」。

Performance：Tests conducted by xAI and third parties show that Grok 4's performance on popular benchmarks is as good as or better than some leading AI models.

性能：xAI 和第三方进行的测试显示，Grok 4 在主流基准测试上的表现不逊色于甚至超越了一些领先的 AI 模型（AI model）。

1 Tested by Artificial Analysis，Grok 4 outperformed Anthropic Claude 4 Opus，Google Gemini 2.5 Pro，OpenAI o3-pro，and DeepSeek-R1 on GPQA Diamond（scientific reasoning），LiveCodeBench（coding），and AIME 2024 (competition math). It tied with Claude 4 Opus for the top spot on MMLU-Pro，came in behind o4-mini set to high on SciCode（coding），and came in fourth on HumanEval (coding).

由 Artificial Analysis 进行的测试显示，Grok 4 在 GPQA Diamond （科学推理）、LiveCodeBench （编码）以及 AIME 2024 （竞赛数学）等基准测试中，均超越了 Anthropic Claude 4 Opus 、Google Gemini 2.5 Pro 、OpenAI o3-pro 和 DeepSeek-R1。在 MMLU-Pro 基准测试中，它与 Claude 4 Opus 并列榜首；但在 SciCode （编码）测试中，表现稍逊于高配版的 o4-mini ；在 HumanEval （编码）测试中则位列第四。

2 In xAI's tests，on ARC-AGI-2，a test of abstract reasoning，Grok 4（15.9 percent）set a new state of the art，nearly double that of its closest competitor，Claude Opus 4 (8.6 percent). On Humanity's Last Exam（PhD-level questions in subjects that include math，engineering，and physics），Grok 4（25.4 percent without tools，38.6 percent with tools）outperformed Google's Gemini 2.5 Pro（21.6 percent without tools，26.9 percent with tools）and OpenAI's o3 (21 percent without tools，24.9 percent with tools). On the same test，Grok 4 Heavy without tools achieved 44.4 percent.

在 xAI 的测试中，Grok 4 在 ARC-AGI-2 这项抽象推理测试中表现出色，取得了 15.9% 的成绩，刷新了当前技术水平（state of the art），几乎是其最接近的竞争对手 Claude Opus 4（8.6%）的两倍。在「人类的最后一次考试」（一项包含数学、工程和物理等学科的博士级别问题测试）中，Grok 4 在不使用工具时取得了 25.4% 的成绩，使用工具时达到 38.6%，表现优于 Google 的 Gemini 2.5 Pro（不使用工具 21.6%，使用工具 26.9%）和 OpenAI 的 o3（不使用工具 21%，使用工具 24.9%）。值得一提的是，在同一测试中，不使用工具的 Grok 4 Heavy 版本更是达到了 44.4% 的高分。

3 In speed tests by Artificial Analysis，Grok 4（73 tokens per second）fell well behind the speediest models such as Google Gemini 2.5 Flash-Reasoning（374 tokens per second），but ahead of Claude 4 Opus Thinking（68 tokens per second）and DeepSeek-R1 0528 (24 tokens per second).

根据 Artificial Analysis 的速度测试结果，Grok 4 的速度为每秒 73 Token，远不及最快的模型，例如 Google Gemini 2.5 Flash-Reasoning（每秒 374 Token），但其表现却优于 Claude 4 Opus Thinking（每秒 68 Token）和 DeepSeek-R1 0528（每秒 24 Token）。

Behind the news：Grok 4's debut was clouded by reports the previous week that Grok 3 had posted antisemitic statements and praised Adolf Hitler. xAI said a code update caused the model to rely too heavily on extremist views from users of the X platform. The company deleted the offensive posts and apologized. That mishap follows a series of similar outputs in recent months. xAI attributed some of them to rogue employees who had circumvented the company's code-review process to modify the chatbot.

新闻背景：Grok 4 的首次亮相被蒙上了一层阴影。此前一周有报道称，Grok 3 发布了反犹太言论并赞扬了阿道夫·希特勒。xAI 公司表示，是由于一次代码更新，导致该模型过于依赖 X 平台用户的极端主义观点。该公司已删除这些不当内容并公开道歉。而这次事故，也并非孤例，此前几个月内也发生过一系列类似问题。xAI 公司将其中一些归咎于个别员工，称他们规避了公司的代码审查流程，私自修改了聊天机器人。

Why it matters：The xAI team has built a series of high-performing models in record time. If its performance lives up to the promise of its benchmark results，Grok 4 could set new standards. That said，the previous version has been fragile and prone to misbehavior，and xAI has shown a worrisome tendency to modify its models without following its own stated protocols.

重要性：xAI 团队在创纪录的时间内构建了一系列性能卓越的模型。如果 Grok 4 的表现能兑现其基准测试结果的承诺，它有望树立新的行业标准。话虽如此，其之前的版本一直表现不稳定，容易出现异常行为，而且 xAI 也表现出一种令人担忧的趋势，即不遵循其自身公布的协议就修改模型。

We're thinking：Last year，Musk said that xAI「will open source its models，including weights and everything,」and as it created each new version，it would open the prior version. Open source is a huge boon to AI，and we hope xAI will resume its open releases.

我们的看法：去年，Musk 曾表示 xAI「将开源其模型，包括权重和所有内容」，并且每当创建新版本时，就会开放之前的版本。开源对 AI （人工智能）而言是一个巨大的福音，我们希望 xAI 能够恢复其开放发布策略。

#### Meta Lures Talent With Sky-High Pay

Meta 以天价薪酬吸引人才

Publicly reported compensation for AI talent has skyrocketed in the wake of Meta's recent hiring spree.

公开数据显示，在 Meta 近期大规模招聘的带动下，AI 人才的薪酬一路飙升。

What's new：Since forming Meta Superintelligence Labs in June，CEO Mark Zuckerberg has hired AI executives for pay packages worth as much as $300 million over four years，Wired reported. Meta spokesperson Andy Stone said such statements were false and that the company's pay packages had been「misrepresented all over the place.」Nonetheless，having seen valued employees jump to Meta，OpenAI began sweetening its compensation.

最新进展：Wired 报道，自 6 月成立 Meta 超级智能实验室（Meta Superintelligence Labs）以来，首席执行官 Mark Zuckerberg 已为公司招募的 AI 高管开出了为期四年、价值高达 3 亿美元的薪酬。Meta 发言人 Andy Stone 表示，此类说法是虚假的，并且该公司的薪酬方案被「四处不实报道」了。尽管如此，在看到骨干员工跳槽到 Meta 后，OpenAI 开始提高其薪酬待遇。

How it works：Meta Chief Technology Officer Andrew Bosworth told employees,「We have a small number of leadership roles that we're hiring for，and those people do command a premium.」

运作机制：Meta 首席技术官 Andrew Bosworth 告诉员工，「我们正在招聘少数几个领导职位，而这些人确实值得高薪。」

1 Meta agreed to pay Ruoming Pang，who formerly headed Apple's efforts to build foundation models，a package worth $200 million over several years，Bloomberg reported. That figure exceeds Apple's pay scale for any employee except CEO Tim Cook.

彭博社报道称，Meta 同意向 Ruoming Pang 支付一份价值 2 亿美元的多年期薪酬方案。Ruoming Pang 曾领导 Apple 基础模型（foundation models）的开发工作。这个数字甚至超过了 Apple 除了首席执行官 Tim Cook 之外任何员工的薪酬标准。

2 Much attention has focused on offers of $100 million，a figure first cited by OpenAI CEO Sam Altman in mid-June，who told the Uncapped podcast that Meta had enticed OpenAI staff with signing bonuses of that magnitude. Meta's Bosworth told employees that the company had offered $100 million to some new hires not as a signing bonus，but as total compensation，according to Wired. Wired further reported，without attribution，that Meta offered $100 million as total compensation for the first year in larger，multi-year deals.

外界对 1 亿美元的报价给予了高度关注。这个数字最初由 OpenAI 首席执行官 Sam Altman 在 6 月中旬提及，他告诉 Uncapped 播客，Meta 曾以同等金额的签约奖金挖走了 OpenAI 员工。据 Wired 报道，Meta 的 Bosworth 告诉员工，公司向一些新员工提供 1 亿美元并非作为签约奖金，而是作为总薪酬。Wired 进一步报道称，Meta 在更大规模的多年期协议中，将 1 亿美元作为第一年的总薪酬，但未透露消息来源。

3 To lure Alexandr Wang and members of his team，Meta invested $14.3 billion into Wang's Scale AI. Before hiring former Safe Superintelligence CEO Daniel Gross and former Github CEO Nat Friedman，Zuckerberg agreed to acquire NFDG，a venture capital firm the pair cofounded. Gross will lead Meta's AI products division. Friedman will co-lead Meta Superintelligence Labs with Wang.

为了招揽 Alexandr Wang 和他的团队成员，Meta 向 Wang 创办的 Scale AI 投资了 143 亿美元。在正式招募前 Safe Superintelligence 首席执行官 Daniel Gross 和前 Github 首席执行官 Nat Friedman 之前，扎克伯格已同意收购 NFDG —— 一家由二人共同创立的风险投资公司。未来，Gross 将领导 Meta 的 AI 产品部门，而 Friedman 将与 Wang 共同领导 Meta 的超智能实验室（Superintelligence Labs）。

4 Meta has hired at least 16 new scientists or engineers who formerly worked at companies including Anthropic，Apple，Google，and OpenAI. OpenAI gave up 10 of them，including ChatGPT creator Shengjia Zhao and vision transformer co-author Lucas Beyer.（None of them were offered $300 million.）Google lost pre‑training technical lead Jack Rae，speech-recognition specialist Johan Schalkwyk，and Gemini researcher Pei Sun，Reuters reported.

Meta 已经从包括 Anthropic、Apple、Google 和 OpenAI 在内的多家公司，招募了至少 16 名科学家或工程师。其中，有 10 人来自 OpenAI，包括 ChatGPT 的创建者 Shengjia Zhao 和视觉 Transformer（Vision Transformer）的共同作者 Lucas Beyer。（不过，他们都没有拿到 3 亿美元的天价合同。）据路透社报道，Google 流失的人才包括预训练技术负责人 Jack Rae、语音识别专家 Johan Schalkwyk 和 Gemini 项目的研究员 Pei Sun。

5 The new hires receive a signing bonus，base salary，and Meta stock，according to Bloomberg. Stock grants are typically tied to performance and may take more than the usual four years to vest，so an employee who leaves before then may forfeit shares. In addition，Meta may vary payouts depending on its share price at the time.

据彭博社报道，Meta 的新员工将获得签约奖金、基本工资和 Meta 股票。通常，这些授予的股票（Stock grants）与绩效挂钩，可能需要超过常规的四年才能兑现，因此在此之前离职的员工可能会失去这部分股权。此外，Meta 还会根据当时的股价来调整支付金额。

Rival reaction：OpenAI responded to Meta's hiring campaign with an internal memo to employees in which chief research officer March Chen said executives were「recalibrating」compensation and considering other ways to reward the most valued employees. OpenAI was already grappling with rising compensation. Stock-based compensation has grown more than 5 times last year to $4.4 billion — substantially more than total revenue during that period — The Information reported.

竞争对手的反应：面对 Meta 的「挖人」攻势，OpenAI 向员工发出了一份内部备忘录。备忘录中，首席研究官 March Chen 表示，公司高管正在「重新调整」（recalibrating）薪酬结构，并考虑采取其他方式来奖励那些最有价值的员工。事实上，OpenAI 本就正为不断上涨的薪酬问题发愁。据 The Information 报道，去年该公司的股权激励（Stock-based compensation）增长了 5 倍多，达到 44 亿美元，这大大超过了同一时期的总收入。

Why it matters：By recruiting aggressively to get an edge in the race to achieve AI breakthroughs，Meta is not only poaching its rivals' top employees，it's also boosting pay scales throughout the AI industry. The sky-high offers highlight the rarity of people with the right combination of technical knowledge，practical experience，and market savvy.

Why it matters：为了在人工智能（AI）突破的竞赛中占据上风，Meta 正在积极招募人才。这不仅挖走了竞争对手的顶尖员工，也推高了整个 AI 行业的薪酬水平。这些「天价」薪资也凸显出，同时具备专业技术知识、实际操作经验和敏锐市场洞察力的人才非常稀缺。

We're thinking：Meta's core business is selling ads to be shown to users who engage with user-generated content. Generative AI has the potential to disrupt this business in many different ways; for instance，by offering AI-generated content. Meta's heavy investment in AI is bold but rational. We wish the growing Meta team every success!

We're thinking：Meta 的核心业务是向那些浏览用户生成内容的用户销售广告。然而，生成式 AI（Generative AI）有可能从多个方面颠覆这项业务，例如提供由 AI 生成的内容。因此，Meta 在 AI 领域的大量投入，虽然大胆，但却十分合理。我们衷心祝愿日益壮大的 Meta 团队取得圆满成功！

#### California Reframes AI Regulations

加利福尼亚州重新审视 AI 法规

A committee convened by California Governor Gavin Newsom proposed principles intended to balance AI innovation with careful governance. The group sought to rethink AI regulation after Newsom vetoed earlier proposed legislation.

一个由加利福尼亚州州长 Gavin Newsom 召集的委员会，提出了一系列旨在平衡 AI （人工智能）创新与审慎治理的原则。此前，Newsom 否决了早期提出的相关立法，此举之后，该小组便开始着手重新思考 AI 法规的制定方向。

What's new：The Joint California Policy Working Group on AI Frontier Models published「The California Report on Frontier AI Policy,」which outlines principles for California lawmakers to consider in regulating cutting-edge models. Rishi Bommasani of the Stanford Center for Research on Foundation Models and Scott R. Singer of the Carnegie Endowment for International Peace led the effort.

最新动态：联合加州人工智能前沿模型政策工作组（Joint California Policy Working Group on AI Frontier Models）发布了《加州前沿人工智能政策报告》。这份报告为加州立法者在监管尖端人工智能模型时，提供了需要考量的原则。斯坦福基础模型研究中心（Stanford Center for Research on Foundation Models）的 Rishi Bommasani 和卡内基国际和平基金会（Carnegie Endowment for International Peace）的 Scott R. Singer 共同牵头完成了这项工作。

How it works：The authors assessed the proposals of the vetoed legislation，SB 1047，and the progress of AI in the 9 months since. The group considered feedback from more than 60 experts from a range of disciplines. Their report focuses on regulating frontier models — as opposed to applications — loosely defined as the most capable foundation models. The authors conclude:

报告内容：作者评估了此前被否决的 SB 1047 立法提案，并审视了自那时起 9 个月内人工智能领域取得的进展。该工作组汇集了来自不同领域的 60 多位专家的反馈意见。他们的报告重点关注对前沿模型（frontier models）的监管 —— 而非具体应用程序 —— 这些前沿模型大致被定义为最具能力的基础模型（foundation models）。报告总结指出：

1 Lawmakers should consider a broad spectrum of evidence，including technical methods，simulations，and historical experience. Drawing on a variety of sources can help prevent particular stakeholders from misrepresenting data，as oil and tobacco interests did in the past.

立法者应全面考量各类证据，包括技术方法、模拟实验和历史经验。采纳多方信息来源，有助于防止某些利益相关者歪曲数据，正如过去石油和烟草行业所为。

2 Laws should incentivize companies to disclose information that protects the public. AI companies have「not yet coalesced around norms for transparency,」but those that share information can benefit from higher trust by the public and regulators.

法律应激励公司披露有助于保护公众的信息。AI 公司「尚未就透明度规范形成共识」，但那些共享信息的公司可以赢得公众和监管机构的更高信任。

3 Reporting adverse events should be mandatory，and there should be clear ways to address any resulting risks to prevent minor problems from snowballing into major ones. Moreover，whistleblowers must be protected. These measures are crucial to achieve transparency in critical activities such as acquiring data，enforcing security，and ensuring safety.

不良事件的报告应强制执行，并且必须有明确的方法来应对由此产生的风险，以防止小问题演变成大麻烦。此外，举报人必须得到保护。这些措施对于确保关键活动（例如数据获取、安全保障和安全维护）的透明度至关重要。

4 Early choices about the design of technology can lock in future challenges. Thus legislators should anticipate potential future developments and behaviors，rather than waiting for harms to occur. In addition，laws that trigger regulations based on variables like computational budget or numbers of users must be flexible，so they can remain useful even if those variables change rapidly.

在技术设计上的早期决策可能会带来长期的挑战。因此，立法者应该预见未来可能的发展和行为，而不是等到损害发生后再采取行动。此外，那些根据计算预算或用户数量等变量来触发监管的法律必须足够灵活，这样即使这些变量快速变化，它们也能持续发挥作用。

5 The authors note the need for regulators to address recognized hazards，such as bias and disinformation，as well as potential threats such as AI-enabled biological attacks. They don't address AI's impact on labor or energy consumption.

作者指出，监管机构需要解决已知的危害，例如偏见和虚假信息，以及潜在的威胁，例如由 AI 助力的生物攻击。他们没有谈及 AI 对劳动力或能源消耗的影响。

Behind the news：Although the White House has ordered an AI action plan，U.S. states have passed the bulk of regulations. However，this may be changing. Congress is debating legislation that would ban states from enacting their own AI laws for a period of 10 years. The aim is to avoid forcing AI developers to navigate a patchwork of laws state by state，which would risk slowing down U.S. AI development，hampering competition，and discouraging open-source development.

新闻背景：尽管白宫已经下令制定 AI 行动计划，但目前大部分法规都是由美国各州通过的。然而，这种情况可能正在改变。国会正在辩论一项立法，该立法将禁止各州在 10 年内制定自己的 AI 法律。此举旨在避免强制 AI 开发者应对各州碎片化的法规，因为这可能会减缓美国 AI 发展速度，阻碍市场竞争，并抑制开源发展。

Why it matters：Regulating AI is tricky，particularly given the intense lobbying efforts to pass laws that would favor particular large companies or block competition from open-source software. AI is sparking innovations in a wide range of fields，including agriculture，biotechnology，clean technology，education，finance，and medicine. Fundamental principles like weighing evidence rather than theory，engaging a wide variety of stakeholders，and requiring transparency can help regulators craft laws that enable the public to benefit from technological progress without imposing undue burdens on developers.

为何重要：监管人工智能（AI）是一项棘手的工作，尤其考虑到强大的游说努力，这些努力旨在通过有利于特定大公司或阻碍开源软件（open-source software）竞争的法律。人工智能（AI）正在广泛的领域推动创新，包括农业、生物技术、清洁技术、教育、金融和医学。权衡证据而非理论、让广泛的利益相关者参与、以及要求透明度等基本原则，能够帮助监管机构制定法律，从而让公众从技术进步中受益，同时不给开发者带来不必要的负担。

We're thinking：The working group sensibly discarded many of the counterproductive requirements of California's deeply flawed SB 1047，such as making AI developers liable if their models are used to cause significant damage. However，the new guidelines retain the earlier emphasis on regulating general-purpose technology — foundation models — rather than specific applications. We should regulate the way AI models are used instead of the models themselves.

#### More Robust Multi-Agent Systems

更强大的多 AI 智能体（AI Agent）系统

我们认为：加州饱受诟病的 SB 1047 法案中，有许多适得其反的规定，比如要求人工智能（AI）开发者为模型造成的重大损害承担责任。工作组明智地放弃了这些要求。然而，新指南依然强调对通用技术 —— 也就是基础模型（Foundation Model）—— 进行监管，而不是关注具体的应用。我们应该规范 AI 模型的使用方式，而非模型本身。

Researchers addressed weaknesses in existing multi-agent frameworks. Their systems achieved scientific and technical breakthroughs.

研究人员解决了现有多智能体框架中的弱点，他们的系统取得了科学和技术突破。

What's new：Mert Cemri and colleagues at UC Berkeley and the Italian bank Intesa Sanpaolo examined ways in which multi-agent LLM systems tend to fail. They explored possible fixes and built more robust multi-agent systems that，for instance，improved Google's own processing infrastructure.

最新进展：Mert Cemri 及其在加州大学伯克利分校和意大利联合圣保罗银行（Intesa Sanpaolo）的同事，深入研究了多智能体大语言模型（LLM）系统容易出现故障的原因。他们探索了可能的修复方案，并构建了更稳健的多智能体系统，例如，这些系统甚至改进了 Google 自有的处理基础设施。

Key insight：Multi-agent systems often are modeled after human organizations，so their failure modes can mirror those of human organizations. For instance，people in organizations may fail to seek clarification for tasks they don't understand well. AI builders can address similar issues among agents by，say，forcing them to ask for clarification if their confidence falls below a threshold. Other strategies include strengthening verification that an agent completed its task，standardizing protocols for inter-agent communication，and improving descriptions of agents' roles.

一个关键的洞察是：多智能体系统（Multi-agent systems）的构建常常模仿人类组织，因此它们在出现故障时的模式也可能与人类组织类似。例如，在人类组织中，人们可能不会主动寻求对那些不完全理解的任务进行澄清。AI 构建者可以借鉴这一点，解决 AI 智能体（agent）之间的类似问题，比如，通过强制智能体在信心低于某个阈值时主动寻求澄清。其他策略还包括强化验证智能体是否完成了任务，制定标准化的智能体间通信协议，以及优化智能体角色的定义。

How it works：The authors fed ​​queries from existing software-engineering and math-problem datasets to open-source，multi-agent frameworks including AG2（disclosure：Andrew Ng has a personal investment in AG2）and ChatDev，using GPT-4o as the LLM component. They collected all model and tool outputs for more than 150 failed attempts. Annotators classified failures of agent interaction，enabling the authors to build a taxonomy of multi-agent failure modes and revise the frameworks to address general categories of weakness.

工作原理：研究人员将现有软件工程和数学问题数据集中的查询，提供给开源的多智能体（multi-agent）框架，其中包括 AG2 （披露：Andrew Ng 对 AG2 有个人投资）和 ChatDev，并将 GPT-4o 作为其中的大语言模型（LLM）组件。他们收集了超过 150 次失败尝试中所有模型和工具的输出。随后，标注人员对 AI 智能体（AI Agent）交互中出现的失败进行了分类，这使得研究人员能够建立一套多智能体系统失败模式的分类体系，并据此修改这些框架，从而解决普遍存在的弱点。

1 The authors divided multi-agent system failures into three categories：poor specifications（including 5 subcategories such as agents losing track of their assigned roles and losing conversation history），inter-agent misalignment（6 subcategories that describe failures in coordination and communication such as withholding information or failing to ask for clarification），and poor task verification (3 subcategories such as ending a task without making sure the goal was achieved).

作者将多智能体系统（multi-agent system）的故障归纳为三类：规范不当（包含 5 个子类别，例如智能体（agent）未能追踪其分配的角色或丢失对话历史记录）；智能体之间协调错位（包含 6 个子类别，描述了协调和沟通方面的故障，比如隐瞒信息或未能请求澄清）；以及任务验证不足（包含 3 个子类别，例如在未确认目标达成的情况下就结束任务）。

2 The authors modified AG2 and ChatDev. They improved prompts（for instance，adding a verification section that read,「Before presenting your final answer，please complete the following steps：…」）and redesigned the multi-agent structure (for example，reconfiguring agents' roles from the duo of student and assistant to the trio of problem solver，coder，and verifier).

作者对 AG2 和 ChatDev 进行了改进。他们对提示词（prompt）进行了优化（例如，通过增加一个验证环节，其中包含「在提交你的最终答案之前，请完成以下步骤：…」等指令），并重新设计了多智能体（multi-agent）的内部结构（例如，将原先学生和助手的两人组模式，调整为由问题解决者、编码员和验证者组成的三人协作模式）。

Results：The authors tested versions of AG2 and ChatDev with and without their improvements. They used AG2 to solve math tasks in the GSM-Plus benchmark and ChatDev to solve programming tasks in HumanEval.

结果：研究人员对 AG2 和 ChatDev 这两个 AI 模型分别进行了测试，比较了它们经过改进和未经改进的版本。他们利用 AG2 在 GSM-Plus 基准测试中解决了数学任务，而使用 ChatDev 在 HumanEval 中完成了编程任务。

1 With improved prompts，AG2 achieved 89 percent accuracy. With improved structure，it achieved 88.8 percent accuracy. Without improvements，it achieved 84.3 percent accuracy.

在使用经过改进的提示（prompt）后，AG2 的准确率达到了 89%。如果结构得到了优化，其准确率也能达到 88.8%。而在没有进行任何改进的情况下，AG2 的准确率则为 84.3%。

2 ChatDev achieved 90.3 percent with better prompts and 91.5 percent accuracy with improved structure. It achieved 89.6 percent accuracy without improvements.

ChatDev 在优化提示（prompt）后，准确率达到了 90.3%；在改进了内部结构后，准确率更是提升至 91.5%。而在没有任何改进的情况下，其准确率为 89.6%。

Why it matters：Designing robust multi-agent systems requires more than good LLMs. It demands understanding how agents interact and where their interactions can go wrong. The authors' taxonomy points toward systemic ways to diagnose and address failures，guiding developers toward multi-agent systems that prioritize collaboration over individual agents.

为什么这很重要：要设计出强大的多智能体系统（multi-agent system），仅仅拥有优秀的大语言模型（LLM）是远远不够的。这还需要我们深入理解智能体（AI Agent）之间是如何互动的，以及它们在互动过程中可能出现哪些问题。作者们提出的分类方法，为诊断和解决这些故障提供了系统性的思路，从而指导开发者们构建出那些更注重整体协作而非单个智能体表现的多智能体系统。

We're thinking：By design，the author's taxonomy doesn't include a category for inefficient actions. For instance，one multi-agent system made 10 separate tool calls to retrieve 10 songs from Spotify，rather than retrieving all 10 songs at once. It's a good bet that multi-agent systems will continue to improve.

我们认为：就设计而言，作者的分类体系中并没有包含针对低效行为的类别。举个例子，某个多智能体系统（multi-agent system）在从 Spotify 检索 10 首歌曲时，发出了 10 次独立的工具调用，而不是一次性把所有 10 首歌都取回来。可以肯定的是，多智能体系统未来还会持续改进。