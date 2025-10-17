## 20251015DeepSeek-Cuts-Inference-Costs-OpenAI-Tightens-Ties-With-AMD

001大语言模型/04DeepLearning-WeeklyNews/20251015DeepSeek-Cuts-Inference-Costs-OpenAI-Tightens-Ties-With-AMD.md

[DeepSeek Cuts Inference Costs, OpenAI Tightens Ties with AMD, Thinking Machines Simplifies Fine-Tuning, and more...](https://www.deeplearning.ai/the-batch/issue-323/)

Dear friends,

Readers responded with both surprise and agreement last week when I wrote that the single biggest predictor of how rapidly a team makes progress building an AI agent lay in their ability to drive a disciplined process for evals (measuring the system's performance) and error analysis (identifying the causes of errors). It's tempting to shortcut these processes and to quickly attempt fixes to mistakes rather than slowing down to identify the root causes. But evals and error analysis can lead to much faster progress. In this first of a two-part letter, I'll share some best practices for finding and addressing issues in agentic systems.

上周，当我提到一个团队在构建 AI 智能体（AI agent）方面进展速度最主要的预测因素，在于他们能否推行严格的评估（evals）流程（用来衡量系统性能）和错误分析（用来识别错误原因）时，读者们表现出既惊讶又认同。我们很容易走捷径，快速尝试修复错误，而不是放慢脚步去识别根本原因。但是，评估和错误分析能带来更快的进展。在这封两部分信件的第一部分中，我将分享一些在智能体系统（agentic systems）中发现并解决问题的最佳实践。

Even though error analysis has long been an important part of building supervised learning systems, it is still underappreciated compared to, say, using the latest and buzziest tools. Identifying the root causes of particular kinds of errors might seem "boring," but it pays off! If you are not yet persuaded that error analysis is important, permit me to point out:

尽管错误分析（error analysis）长期以来都是构建监督学习系统（supervised learning systems）的重要组成部分，但与追逐最新、最热门的工具相比，它仍然没有得到足够的重视。找出特定错误的根本原因可能看起来「无聊」，但这是值得的，而且回报丰厚！如果您尚未被说服错误分析的重要性，那么请允许我指出：

1 To master a composition on a musical instrument, you don't only play the same piece from start to end. Instead, you identify where you're stumbling and practice those parts more.

想要精通一件乐器上的某个曲目，你不会只是一遍又一遍地从头到尾演奏整首曲子。相反，你会找出你容易卡壳的地方，然后着重练习这些部分。

2 To be healthy, you don't just build your diet around the latest nutrition fads. You also ask your doctor about your bloodwork to see if anything is amiss. (I did this last month and am happy to report I'm in good health! 😃)

为了保持健康，你不能仅仅围绕最新的营养潮流来调整饮食。你还需要向医生咨询你的血液检查结果，看看是否存在任何异常。(我上个月就做了这项检查，很高兴向大家报告我身体很健康！)

3 To improve your sports team's performance, you don't just practice trick shots. Instead, you review game films to spot gaps and then address them.

想要提升你的运动队表现，你不会只练习花式投篮。相反，你会回顾比赛录像，找出问题所在，然后加以解决。

To improve your agentic AI system, don't just stack up the latest buzzy techniques that just went viral on social media (though I find it fun to experiment with buzzy AI techniques as much as the next person!). Instead, use error analysis to figure out where it's falling short, and focus on that.

为了改进你的 AI 智能体（AI Agent）系统，不要只是简单地堆叠社交媒体上最新走红的流行技术（尽管我发现，和大家一样，尝试这些热门 AI 技术也很有趣！）。相反，要使用错误分析来找出它表现不佳的地方，并专注于解决这些问题。

Before analyzing errors, we first have to decide what is an error. So the first step is to put in evals. I'll focus on that for the remainder of this letter and discuss error analysis next week.

在分析错误之前，我们首先得明确什么是错误。因此，第一步是引入评估机制。本文的剩余部分将重点探讨评估，错误分析则留待下周再行讨论。

If you are using supervised learning to train a binary classifier, the number of ways the algorithm could make a mistake is limited. It could output 0 instead of 1, or vice versa. There are also a handful of standard metrics like accuracy, precision, recall, F1, ROC, etc. that apply to many problems. So as long as you know the test distribution, evals are relatively straightforward, and much of the work of error analysis lies in identifying what types of input an algorithm fails on, which also leads to data-centric AI techniques for acquiring more data to augment the algorithm in areas where it's weak.

如果你正在使用监督学习来训练一个二元分类器（binary classifier），那么算法可能出错的情况是有限的。它可能会将 1 错误地预测为 0，或者将 0 错误地预测为 1。此外，还有一些标准指标，比如准确率（accuracy）、精确率（precision）、召回率（recall）、F1 分数（F1 score）、ROC 曲线（ROC curve）等，适用于多种问题。因此，只要你知道测试数据的分布，评估工作就相对简单。错误分析的大部分工作在于识别算法在哪些类型的输入上表现不佳，这也催生了数据中心化 AI（data-centric AI）技术，通过获取更多数据来弥补算法在薄弱领域的不足。

With generative AI, a lot of intuitions from evals and error analysis of supervised learning carry over — history doesn't repeat itself, but it rhymes — and developers who are already familiar with machine learning and deep learning often adapt to generative AI faster than people who are starting from scratch. But one new challenge is that the space of outputs is much richer, so there are many more ways an algorithm's output might be wrong.

随着生成式 AI（Generative AI）的兴起，许多源自监督学习（supervised learning）评估和错误分析的直觉依然适用 —— 正如那句老话所说，「历史不会简单重复，但总有惊人的相似之处」。因此，那些已经熟悉机器学习（machine learning）和深度学习（deep learning）的开发者，往往比从头开始的人能更快地适应生成式 AI。不过，一个新的挑战在于，生成式 AI 的输出空间要广阔得多，这意味着算法（algorithm）的输出出现错误的可能性也随之大幅增加。

Take the example of automated processing of financial invoices where we use an agentic workflow to populate a financial database with information from received invoices. Will the algorithm incorrectly extract the invoice due date? Or the final amount? Or mistake the payer address for the biller address? Or get the financial currency wrong? Or make the wrong API call so the verification process fails? Because the output space is much larger, the number of failure modes is also much larger.

以自动化处理金融发票为例，我们使用一个 AI 智能体（AI agent）驱动的工作流程，将收到的发票中的信息填充到金融数据库。那么，算法会不会错误地提取发票的到期日期？或者搞错最终金额？又或者将付款人地址误认为是开票人地址？甚至弄错金融货币？或者因为调用了错误的 API 导致验证过程失败呢？由于这种工作流程的输出空间要大得多，因此可能出现的失败模式也随之大幅增加。

Rather than defining an error metric ahead of time, it is therefore typically more effective to first quickly build a prototype, then manually examine a handful of agent outputs to see where it performs well and where it stumbles. This allows you to focus on building datasets and error metrics — sometimes objective metrics implemented in code, and sometimes subjective metrics using LLM-as-judge — to check the system's  performance in the dimensions you are most concerned about. In supervised learning, we sometimes tune the error metric to better reflect what humans care about. With agentic workflows, I find tuning evals to be even more iterative, with more frequent tweaks to the evals to capture the wider range of things that can go wrong.

因此，与其事先定义好一个错误指标，通常更有效的方法是先快速构建一个原型，然后手动检查一些 AI 智能体（AI Agent）的输出，看看它在哪些方面表现出色，又在哪些地方遇到麻烦。这样做能让您专注于构建数据集和错误指标 —— 这些指标有时是在代码中实现的客观指标，有时则是利用大语言模型（LLM）作为评判者实现的主观指标 —— 从而检查系统在您最关注的方面表现如何。在监督学习中，我们有时会调整错误指标，使其更好地反映人类关注的重点。而对于 AI 智能体工作流，我发现调整评估的过程甚至更具迭代性，需要更频繁地修改评估方法，以便捕捉到可能出现的所有问题。

I discuss this and other best practices in detail in Module 4 of the Agentic AI course we announced last week. After building evals, you now have a measurement of your system's performance, which provides a foundation for trying different modifications to your agent, as you can now measure what makes a difference. The next step is then to perform error analysis to pinpoint what changes to focus your development efforts on. I'll discuss this further next week.

我将在我们上周发布的 AI 智能体（Agentic AI）课程的第四模块中，详细探讨这些最佳实践。在构建了评估（evals）系统后，您现在能够衡量系统的性能了。这为您尝试对智能体（agent）进行各种修改奠定了基础，因为您现在可以知道哪些改动会产生效果。接下来，您需要进行错误分析（error analysis），以明确开发工作的重心，知道应该优先改进哪些地方。我将在下周进一步讨论这一点。

Keep building!

Andrew

持续创新！

Andrew

### News

#### OpenAI Strengthens Ties With AMD

OpenAI 强化与 AMD 的合作

OpenAI, strapped for processing power to drive a worldwide constellation of planned data centers, turned to Nvidia's archrival AMD.

OpenAI 正计划在全球建立庞大的数据中心网络，但苦于算力（processing power）不足，于是将目光投向了英伟达（Nvidia）的主要竞争对手 AMD。

What's new: In an unusual deal, OpenAI agreed to purchase what may amount to tens of billions of dollars of AMD Instinct GPUs and received the right to acquire a substantial portion of the chip designer's shares, essentially for free, if certain conditions are met. The deal, which is to be completed in phases starting next year, covers enough GPUs to draw 6 gigawatts of power (roughly 6 times the city of San Francisco's peak electricity demand) and up to 10 percent of AMD's stock. It enables OpenAI to diversify and extend its supply of AI processors to build out a gargantuan size and number of data centers, while AMD secures a top-shelf customer and validates its products as competitors to GPU kingpin Nvidia's — a huge boost to its credibility and sales in the AI market.

最新消息：在一笔不同寻常的交易中，OpenAI 同意采购价值可能高达数百亿美元的 AMD Instinct GPU。同时，如果满足特定条件，OpenAI 还有权几乎免费获得这家芯片设计公司相当一部分的股份。这笔交易将从明年开始分阶段完成，采购的 GPU 总功耗预计达到 6 吉瓦（大约是旧金山市峰值用电量的 6 倍），OpenAI 还有可能获得 AMD 高达 10% 的股份。这笔交易不仅让 OpenAI 能够使其 AI 处理器供应多样化并扩大规模，从而建设超大规模的数据中心；对 AMD 而言，则意味着赢得了一家顶级客户，并证明其产品足以与 GPU 巨头英伟达的产品抗衡 —— 这无疑将极大提升 AMD 在 AI 市场的声誉和销售额。

How it works: Completion of the financial deal is contingent on both companies reaching specific milestones that are largely undisclosed. OpenAI must hit deployment targets for AMD chips, and AMD's stock price must hit certain levels.

工作原理：这笔财务交易能否最终敲定，取决于两家公司能否实现一些具体的里程碑目标，而这些目标大多并未对外公布。具体来说，OpenAI 需要达到 AMD 芯片的部署目标，而 AMD 的股价也必须触及一定的水平。

* OpenAI plans to use AMD's forthcoming Instinct MI450 data-center GPUs for inference. It will deploy the first batch (enough to consume 1 gigawatt) in a new facility, separate from data centers announced previously, starting next year. Completion of that purchase will unlock the first portion of AMD stock.

* OpenAI 计划使用 AMD 即将推出的 Instinct MI450 用于数据中心的 GPU 来执行推理任务。从明年开始，它将在一个全新的设施中部署第一批此类 GPU，其规模足以消耗 1 千兆瓦的电力，并且这个设施将独立于此前公布的其他数据中心。一旦这笔采购完成，将解锁 AMD 股票的第一个部分。

* AMD issued a warrant for OpenAI to buy up to 160 million AMD shares, worth more than $35 billion at the company's current market capitalization, for $0.01 each. The warrant vests as the share price rises to specific levels on their way up to $600 per share, which is roughly three times the current price. If OpenAI acquires all the shares, it will own 10 percent of AMD, potentially enabling it to influence the company's strategic direction.

*  AMD 向 OpenAI 授予了一份认股权证（warrant），允许后者以每股 0.01 美元的超低价格购买最多 1.6 亿股 AMD 股票。按 AMD 目前的市值计算，这批股票的总价值超过 350 亿美元。这份认股权证的生效条件是，AMD 的股价需要逐步上涨，直到达到每股 600 美元，这大约是当前股价的三倍。如果 OpenAI 最终获得所有这些股份，它将持有 AMD 10% 的股权，这可能让它有机会影响 AMD 公司的战略发展方向。

Behind the news: OpenAI's partnership with AMD is the latest in a series of financial commitments it has made to build data centers that may cost trillions of dollars in coming years. It's also part of a broader move by big AI companies to secure processing power sufficient to fulfill their ambitions. Amazon, Google, Meta, Microsoft, and OpenAI have announced plans to spend more than $350 billion on data centers this year alone, requiring massive spending and tightening the supply of AI chips.

新闻背后：OpenAI 与 AMD 的合作，是该公司为建设未来可能耗资数万亿美元的数据中心而做出的一系列财务承诺中的最新进展。这同时也是各大 AI 公司为了获得足以支撑其宏伟目标的计算能力，所采取的更广泛行动的一部分。Amazon、Google、Meta、Microsoft 和 OpenAI 等科技巨头已经宣布，仅在今年就计划在数据中心上投入超过 3500 亿美元，这不仅意味着巨大的开支，也将进一步加剧人工智能（AI）芯片的供应紧张局面。

* Big AI's plans threaten to outstrip the supply of Nvidia's most capable GPUs. In a February post on the X social network, OpenAI CEO Sam Altman said OpenAI was "out of GPUs" and ready to acquire hundreds of thousands more. "It's hard to overstate how difficult it's become to get them," he said.

*  大型 AI（Artificial Intelligence）公司的发展计划，可能会让 Nvidia（英伟达）性能最强的 GPU（图形处理器）供应捉襟见肘。在 X 社交网络上发布的一篇二月帖子中，OpenAI 首席执行官 Sam Altman 表示，OpenAI 的 GPU 已经「用完了」，并准备再购置数十万个。他感叹道：「要夸大获得这些 GPU 的难度有多大，这简直太难了（言下之意是，无论怎么强调其难度都不为过）。」

* AMD holds a 5 percent share of the market for AI accelerators as of late last year, according to an estimate by the investment analyst Jefferies. It has been trying to crack Nvidia's stranglehold on data-center GPUs since 2018, when it launched its Instinct line.

根据投资分析师 Jefferies 的估计，截至去年底，AMD 在 AI 加速器（AI accelerators）市场中占据了 5% 的份额。自 2018 年推出 Instinct 产品线以来，AMD 一直在努力打破 Nvidia 在数据中心 GPU 领域的主导地位。

* OpenAI has been cultivating AMD as an alternative or complement to Nvidia for some time. It already uses AMD's MI355X and MI300X GPUs on a limited basis and contributed to the design of the MI300x, according to Reuters.

* 一段时间以来，OpenAI 一直致力于将 AMD 作为 Nvidia 的替代或补充方案进行发展。据路透社报道，OpenAI 已在小范围使用 AMD 的 MI355X 和 MI300X 图形处理器（GPU），并且对 MI300x 的设计也做出了贡献。

* In addition, OpenAI announced a plan, starting in the second half of 2026, to deploy 10 gigawatts' worth of custom chips designed by Broadcom. The plan follows an earlier $10 billion deal for Broadcom to supply custom chips for AI training that would augment, rather than replace, Nvidia GPUs.

* 此外，OpenAI 宣布了一项计划：从 2026 年下半年开始，部署由 Broadcom 设计的、总功率达 10 吉瓦的定制芯片（custom chips）。这项计划是在 Broadcom 之前达成的一项 100 亿美元协议之后提出的，该协议旨在为 AI 训练（AI training）提供定制芯片，这些芯片将用于增强而非取代 Nvidia GPU（Nvidia GPU）。

* OpenAI's data centers also need high-bandwidth memory chips. Earlier this month, it announced a deal with Samsung and SK Hynix, which will scale up their manufacturing capacities to serve Stargate, a data-center partnership between OpenAI, Oracle, and SoftBank.

*  OpenAI 的数据中心同样需要高带宽内存芯片。本月早些时候，OpenAI 宣布与三星和 SK Hynix 达成一项协议，两家公司将扩大其制造能力，以便为 Stargate 项目提供支持。Stargate 是 OpenAI、Oracle 和 SoftBank 之间的一项数据中心合作计划。

Why it matters: AI leaders are racing for position in a market that could reach tens of trillions of dollars by some estimates. OpenAI is leading the charge to build data-center capacity. Its deal with AMD, which has been slowly but steadily encroaching on Nvidia's dominance in GPUs, takes AMD along for what promises to be a wild ride. That said, it also further exposes both companies to financial risks that worry some observers. OpenAI has taken on substantial debt and its current commitments promise much more. As for AMD, it is giving away 10 percent of itself for the promise of future sales that Lisa Su said would amount to $100 billion considering both OpenAI and other customers it would inspire. The structure of the deal limits the risks and ensures that if the market stalls, both companies will suffer together.

为什么这件事很重要：据一些估算，AI 领域的领导者们正在一个可能达到数十万亿美元规模的市场中激烈争夺领先地位。其中，OpenAI 正在牵头进行大规模的数据中心算力（data-center capacity）建设。而它与 AMD 达成的交易，让 AMD 也加入了这场注定跌宕起伏的竞争，要知道，AMD 一直在缓慢但稳健地蚕食着 Nvidia 在 GPU 领域的主导地位。

然而，这场合作也使两家公司进一步面临着一些观察者担忧的金融风险。OpenAI 已经背负了巨额债务，并且其当前的各项承诺预示着它还将承担更多债务。至于 AMD，它正在出让自身 10% 的股份，以期获得未来的销售额。AMD 首席执行官 Lisa Su 曾表示，包括来自 OpenAI 和其他潜在客户的销售额，预计将达到 1000 亿美元。这项交易的结构限制了风险，并确保了即使市场停滞不前，两家公司也将共同承担损失。

We're thinking: OpenAI's plans to buy tens of billions of dollars worth of chips for inference supports the notion that demand for AI processing power is shifting from training to inference. Growing usage in general and the rise of agentic workflows in particular suggest that inference is poised for massive expansion, and AMD GPUs, which have relatively large memories, may provide an inference advantage over Nvidia chips in some settings. The more competitive the market for inference, the more likely that the price and speed of token generation will continue to fall — a tremendous boon to AI builders!

我们观察到：OpenAI 计划斥资数百亿美元购买用于推理（inference）的芯片，这印证了 AI 处理能力的需求正从训练（training）转向推理的观点。AI 应用的普遍增长，特别是 AI 智能体（AI Agent）工作流的兴起，都预示着推理任务将迎来大规模扩张。在这种背景下，AMD 的 GPU 因其相对较大的内存，在某些场景下可能比 Nvidia 芯片更具推理优势。推理市场的竞争越激烈，Token 生成的价格和速度就越有可能持续下降 —— 这对于 AI 开发者而言，无疑是一个巨大的利好！

#### DeepSeek Cuts Inference Costs

DeepSeek 大幅降低推理成本

DeepSeek's latest large language model can cut inference costs by more than half and processes long contexts dramatically faster relative to its predecessor.

DeepSeek 最新的大语言模型（Large Language Model）能够将推理成本降低一半以上，并且相对于其前代模型，处理长上下文（long context）的速度也显著加快。

What's new: DeepSeek released weights for DeepSeek-V3.2-Exp, a variation on DeepSeek-V3.1-Terminus, which was released in late September. It streamlines processing using a dynamic variation on sparse attention that enables inference speed to scale linearly with input length. The code supports AI chips designed by Huawei, and other Chinese chip designers have adapted it for their products, helping developers in China to use domestic alternatives to U.S.-designed Nvidia GPUs.

最新动态：DeepSeek 发布了 DeepSeek-V3.2-Exp 的模型权重，这是去年九月下旬发布的 DeepSeek-V3.1-Terminus 的一个新版本。它采用了一种动态变化的稀疏注意力（sparse attention）机制来优化数据处理，使得模型在推理时的速度能与输入内容的长度保持线性增长。该代码兼容华为设计的 AI 芯片，并且其他中国芯片设计公司也已将其适配到他们的产品中，从而帮助中国的开发者能够使用国产芯片，替代美国设计的 Nvidia GPU。

* Input/output: Text in (up to 128,000 tokens), text out (up to 8,000 tokens)

* Architecture: Mixture-of-experts transformer, 685 billion total parameters, approximately 37 billion active parameters per token

* 输入 / 输出：文本输入（最多 128,000 个 Token），文本输出（最多 8,000 个 Token）

* 架构：专家混合式 Transformer，总参数量 6850 亿，每个 Token 大约有 370 亿个活跃参数

* Availability: Free via web interface or app, weights available for noncommercial and commercial uses under MIT license, $0.28/$0.028/$0.42 per million input/cached/output tokens via API

*  ** 获取方式：** 通过网页界面或应用程序免费使用，其模型参数在 MIT 许可下可用于非商业和商业目的。通过 API（应用程序接口）调用时，每百万输入 Token（Token）需支付 $0.28，缓存 Token $0.028，输出 Token $0.42。

* Performance: Comparable to DeepSeek-V3.1-Terminus across many benchmarks, processing inputs over 7,000 tokens 2 to 3 times faster

How it works: The team modified DeepSeek-V3.1-Terminus with a sparse attention mechanism that, rather than attending to the entire input context, selectively processes only the most relevant tokens.

* 性能：在许多基准测试中，其性能可与 DeepSeek-V3.1-Terminus 匹敌，并且在处理超过 7,000 个 Token 的输入时，速度能快上 2 到 3 倍。

工作原理：研发团队对 DeepSeek-V3.1-Terminus 进行了改进，为其引入了一种稀疏注意力机制（sparse attention mechanism）。这种机制不再关注整个输入上下文，而是有选择性地处理那些最相关的 Token（Token）。

* During training, a "lightning indexer," a weighted similarity function, learned from 2.1 billion tokens of text to predict which tokens DeepSeek-V3.1-Terminus' dense attention mechanism would focus on. Then the team fine-tuned all parameters on around 100 billion tokens of text to work with the indexer's sparse token selections.

*  在模型训练阶段，我们引入了一个名为「闪电索引器（lightning indexer）」的加权相似度函数。它从 21 亿个文本 Token 中进行学习，主要任务是预测 DeepSeek-V3.1-Terminus 的密集注意力机制（dense attention mechanism）将会聚焦哪些 Token。随后，研究团队在大约 1000 亿个文本 Token 上对模型的所有参数进行了微调，以使其能更好地与索引器筛选出的稀疏 Token 协同工作。

* The team further fine-tuned the model by distilling five specialist models (versions of the pretrained DeepSeek-V3.2 base fine-tuned for reasoning, math, coding, agentic coding, and agentic search) into DeepSeek-V3.2-Exp.

为了进一步提升模型性能，研究团队采用了一种「蒸馏」方法：他们将五个经过专门训练的模型（这些模型都基于预训练（pretrained）的 DeepSeek-V3.2 基础模型，并分别针对推理、数学、编程、AI 智能体（AI Agent）编程和 AI 智能体搜索能力进行了微调（fine-tuned)），将其知识整合并「蒸馏」到了 DeepSeek-V3.2-Exp 模型中。

* The team applied GRPO to merge reasoning, agentic, and alignment training into a single stage. This approach avoided the catastrophic forgetting problem, in which new learning displaces old, that typically bedevils multi-stage reinforcement learning.

*  研究团队应用 GRPO 将推理、智能体（agentic）和对齐（alignment）训练整合到一个阶段。这种方法成功避免了「灾难性遗忘问题」，即新知识的学习会覆盖旧知识的问题，而这个问题通常是多阶段强化学习（reinforcement learning）中难以解决的挑战。

* At inference, the indexer scores the relevance of each past token to the token being generated. It uses simple operations and FP8 precision (8-bit floating point numbers that are relatively imprecise but require less computation to process) to compute these scores quickly.

在进行推理时，索引器（indexer）会评估每个过去的 Token 与正在生成的 Token 之间的相关性。它利用简单的运算和 FP8 精度（一种 8 位浮点数，虽然精度相对较低，但处理起来所需的计算量也更少），来快速计算出这些相关性分数。

* Based on these scores, instead of computing attention across all tokens in the current input context, the model selects and computes attention across the top 2,048 highest-scoring tokens, dramatically reducing computational cost.

* 基于这些分数，模型不再对当前输入上下文中的所有 Token（Token）计算注意力（attention），而是选择并计算得分最高的 2,048 个 Token 的注意力，从而显著降低了计算成本。

Results: In DeepSeek's benchmark tests, DeepSeek-V3.2-Exp achieved substantial gains in efficiency with modest trade-offs in performance relative to its predecessor DeepSeek-V3.1-Terminus.

结果：在 DeepSeek 的基准测试中，与它的前身 DeepSeek-V3.1-Terminus 相比，DeepSeek-V3.2-Exp 在效率方面取得了显著提升，同时在性能上仅有适度的权衡。

* DeepSeek-V3.2-Exp cut inference costs for long input contexts by 6 to 7 times compared to DeepSeek-V3.1 Terminus. Processing 32,000 tokens of context, DeepSeek-V3.2-Exp cost around $0.10 per 1 million tokens versus $0.60. Processing 128,000 tokens of context, it cost $0.30 per 1 million tokens compared to $2.30.

* DeepSeek-V3.2-Exp 相较于 DeepSeek-V3.1 Terminus，在处理长输入上下文（context）时，推理成本降低了 6 到 7 倍。具体来说，在处理 32,000 个 token（标记）的上下文时，DeepSeek-V3.2-Exp 每 1 百万个 token 的成本约为 $0.10，而 DeepSeek-V3.1 Terminus 则需要 $0.60。当上下文长度增加到 128,000 个 token 时，DeepSeek-V3.2-Exp 的成本仅为每 1 百万个 token $0.30，相比之下，DeepSeek-V3.1 Terminus 则高达 $2.30。

* DeepSeek-V3.2-Exp showed gains on tasks that involved coding and agentic behavior as well as some math problems. It surpassed DeepSeek-V3.1-Terminus on Codeforces coding challenges (2121 Elo versus 2046 Elo) and BrowseComp the browser-based agentic tasks (40.1 percent versus 38.5 percent). It also surpassed its predecessor on AIME 2025's competition high-school math problems (89.3 percent versus 88.4 percent), which are more structured and have clearer solutions than those in HMMT (see below).

* DeepSeek-V3.2-Exp 在涉及编码、AI 智能体（AI Agent）行为以及部分数学问题的任务上表现出了显著提升。它在 Codeforces 编程挑战赛（Elo 分数 2121 对比 2046）和基于浏览器的智能体任务 BrowseComp（40.1% 对比 38.5%）中，均超越了 DeepSeek-V3.1-Terminus。此外，它在 AIME 2025 年高中数学竞赛难题上的表现也超过了其前身（89.3% 对比 88.4%）。与 HMMT 中的题目（参见下文）相比，AIME 的这些问题通常结构更清晰，解法也更明确。

* However, its performance showed slight degradation relative to DeepSeek-V3.2-Terminus across several tasks. It trailed its predecessor on GPQA-Diamond's graduate-level science questions (79.9 percent versus 80.7 percent), HLE's abstract-thinking challenges (19.8 percent versus 21.7 percent), HMMT 2025's competitive high-school math problems (83.6 percent versus 86.1 percent), and Aider-Polyglot's coding tasks (74.5 percent versus 76.1 percent).

*  然而，在多项任务中，它的性能相较于 DeepSeek-V3.2-Terminus 略有下降。具体来说，在 GPQA-Diamond 的研究生级别科学问题上，它的表现为 79.9% 对比其前身的 80.7%；在 HLE 的抽象思维挑战中，它取得了 19.8% 的成绩，而其前身则为 21.7%；在 HMMT 2025 的高中生竞技数学问题上，它以 83.6% 的成绩落后于前身的 86.1%；在 Aider-Polyglot 的编程任务中，它的得分是 74.5%，而其前身为 76.1%。

Behind the news: DeepSeek-V3.2-Exp is among the first large language models to launch with optimizations for domestic chips rather than adding these as an afterthought. The software has been adapted to run on chips by Huawei, Cambricon, and Hygon, following an order by China's government to domestic AI companies not to use Nvidia chips. The government's order followed reports that Chinese AI companies had struggled to use domestic chips rather than Nvidia chips, which are subject to U.S. export restrictions.

这则新闻的背后：DeepSeek-V3.2-Exp 是首批在发布时就针对国内芯片进行优化的大语言模型（Large Language Model），而非后续才追加适配。这款软件已经过调整，能够运行在华为、寒武纪（Cambricon）和海光（Hygon）等国内公司的芯片上。此前，中国政府曾下令国内 AI 公司不得使用英伟达（Nvidia）芯片。政府发布这项命令，是由于有报道指出，中国 AI 公司在尝试使用国内芯片替代受美国出口限制的英伟达芯片时，遇到了不少困难。

Why it matters: Even as prices have fallen, the cost of processing LLM output tokens can make it prohibitively expensive to perform long-context tasks like analyzing large collections of documents, conversing across long periods of time, and refactoring large code repositories. DeepSeek's implementation of sparse attention goes some distance toward remedying the issue.

为什么这很重要：尽管大语言模型（LLM）的使用成本有所下降，但处理其输出 token 的费用，仍然让执行一些长上下文（long-context）任务变得极其昂贵。这些任务包括分析大量的文档、进行长时间的对话，以及重构庞大的代码库等。DeepSeek 对稀疏注意力（sparse attention）的实现，在一定程度上缓解了这一问题。

We're thinking: DeepSeek-V3.2-Exp joins Qwen3-Next in experimenting with self-attention alternatives to improve the efficiency of large transformers. While Qwen3-Next combines Gated DeltaNet layers with gated attention layers, DeepSeek-V3.2-Exp uses dynamic sparse attention, suggesting that there's still more efficiency to be gained by tweaking the transformer architecture.

我们发现，DeepSeek-V3.2-Exp 和 Qwen3-Next 模型都在探索自注意力机制（self-attention）的替代方案，以期提升大型 Transformer（large transformers）的效率。具体来看，Qwen3-Next 结合了 Gated DeltaNet 层和门控注意力层，而 DeepSeek-V3.2-Exp 则采用了动态稀疏注意力。这表明通过对 Transformer 架构（Transformer architecture）进行精细调整，我们仍能进一步挖掘出更高的效率潜力。

#### Fine-Tuning Simplified

让微调（Fine-Tuning）变得更简单

The first offering from Thinking Machines Lab, the startup founded by former OpenAI CTO Mira Murati, aims to simplify — and democratize — the process of fine-tuning AI models.

Thinking Machines Lab —— 这家由前 OpenAI 首席技术官 Mira Murati 创立的创业公司 —— 推出了首款产品，旨在简化并普及微调（Fine-Tuning）AI 模型的过程。

[Announcing Tinker - Thinking Machines Lab](https://thinkingmachines.ai/blog/announcing-tinker/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-_L4bJJ6vXg6Hs10je6IoHKFICRZs2QVtY2uv4WUTWxZX4HrpAhzRVhAc_65PiMrUfftu9f)

What's new: Tinker is an API that streamlines working with multiple GPUs to fine-tune large language models. Users control their algorithms while code behind the scenes handles scheduling, resource allocation, and recovery in case a GPU crashes. You can join a waitlist for free access, but the company plans to start charging in coming weeks. Tinker currently offers a selection of pretrained Qwen3 and Llama 3 models with other open-weights options to come.

最新进展：Tinker 是一个 API（应用程序编程接口），它简化了利用多个 GPU 对大语言模型（Large Language Model）进行微调（fine-tune）的过程。用户可以专注于控制自己的算法，而底层代码则会负责调度、资源分配以及在 GPU 出现故障时的恢复。目前，你可以加入免费访问的等候名单，不过该公司计划在未来几周内开始收取费用。Tinker 当前提供一系列预训练的 Qwen3 和 Llama 3 模型，未来还将支持其他开源权重模型。

How it works: The API lets you work as though you were fine-tuning on a single device. You can select a model and write a fine-tuning script that loads your data and specifies a predefined loss function for supervised or reinforcement learning, or you can write your own. Tinker's software determines, for instance, how to split the model and data among computing clusters.During fine-tuning, the system builds and trains a LoRA adapter (two small matrices that modify a pretrained model's weights at inference) for the task at hand.

其工作原理如下：该 API（应用程序编程接口）让你可以像在单个设备上进行微调（fine-tuning）一样工作。你可以选择一个模型，并编写一个微调脚本，该脚本负责加载你的数据，并为监督学习（supervised learning）或强化学习（reinforcement learning）指定一个预定义的损失函数，你也可以自己编写一个。例如，Tinker 的软件会决定如何将模型和数据分配到不同的计算集群中。在微调过程中，系统会针对当前任务构建并训练一个 LoRA（Low-Rank Adaptation）适配器（这是一个由两个小型矩阵组成的结构，它能在推理（inference）阶段修改预训练模型（pretrained model）的权重）。

1 Using LoRA also enables the system to share a single pool of compute among multiple fine-tuning runs, which reduces costs.

此外，采用 LoRA（Low-Rank Adaptation）技术，系统能够在进行多次微调（fine-tuning）时共享同一个计算资源池，从而有效降低成本。

2 A Tinker Cookbook offers implementations of fine-tuning methods.

Tinker Cookbook 中提供了各种微调方法的具体实现。

[thinking-machines-lab/tinker-cookbook: Post-training with Tinker](https://github.com/thinking-machines-lab/tinker-cookbook?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-_L4bJJ6vXg6Hs10je6IoHKFICRZs2QVtY2uv4WUTWxZX4HrpAhzRVhAc_65PiMrUfftu9f)

Behind the news: Several companies can fine-tune models on your data but don't give you control over the training loop, similar to the way OpenAI fine-tunes its models on customer data. Libraries like DeepSpeed offer control over fine-tuning while simplifying parallelization across multi-GPU infrastructure, but they require you to manually request GPUs from cloud services (if you don't have your own) and manage configuration files, which can be complicated.

新闻背后的故事：一些公司虽然能在你的数据上对模型进行微调，但它们通常不提供对训练循环的完全控制，这与 OpenAI 在客户数据上微调模型的方式类似。虽然像 DeepSpeed 这样的库能让你更好地控制微调过程，并简化了在多 GPU（图形处理器）基础设施上实现并行化，但它们也有其复杂之处。比如，如果你没有自己的 GPU，就需要手动向云服务提供商请求资源，并且要自行管理复杂的配置文件。

Why it matters: Fine-tuning using multiple GPUs often requires dedicating time to figure out how to allocate resources, debug tricky APIs, and so on. Tinker saves that time, enabling model builders to spend it more productively. Academic researchers, startups, and mid-size companies that want to level up their investment in AI research and/or development are most likely to find it helpful.

其重要性在于：使用多个图形处理器（GPU）进行微调（fine-tuning）通常需要投入大量时间，去研究如何分配计算资源、调试那些复杂的应用程序编程接口（API）等。Tinker 正是为了节省这些宝贵时间而生，它让模型开发者能够更高效地投入精力。对于希望提升其在人工智能（AI）研究或开发领域投资水平的学术研究人员、初创公司和中型企业来说，Tinker 最有可能提供巨大帮助。

We're thinking: Tinker's use of LoRA  divides the cost of training base models among multiple fine-tuning runs, and potentially among users. This could enable users to experiment more within the a fixed budget.

我们认为，Tinker 使用 LoRA 技术，能够将训练基础模型的成本分摊到多次微调运行中，甚至可能在不同用户之间分担。这有助于让用户在既定的预算范围内，有更多机会进行实验。

#### Better Spatial Perception for Robots

提升机器人的空间感知能力

Robot control systems that accept only text input struggle to translate words into motions in space. Researchers developed a system that enables robots to plan spatial paths before they execute text instructions.

仅接受文本输入的机器人控制系统（robot control systems）在将文字指令转化为实际空间中的动作时，往往会面临挑战。为了解决这个问题，研究人员开发了一种新的系统，它能让机器人在执行文本指令之前，就预先规划好在三维空间中的运动路径。

What's new: Jason Lee and colleagues at Allen Institute for AI and University of Washington introduced MolmoAct, a robotics action system that improved a 3-jointed robot arm's ability to manipulate objects and perform multi-step tasks by first estimating spatial depth and planning motion paths. The weights and code are available for noncommercial and commercial uses under the Apache 2 license, while the authors' fine-tuning dataset is available under CC BY 4.0.

有什么新进展：Jason Lee 和他在 Allen Institute for AI 以及 University of Washington 的同事们共同推出了 MolmoAct，这是一个机器人行动系统。它通过首先估算空间深度并规划运动路径，显著提升了拥有三个关节的机器人手臂操纵物体和执行多步骤任务的能力。该系统的权重（weights）和代码（code）在 Apache 2 许可下开放，支持非商业和商业用途；而作者们用于微调的数据集（dataset）则遵循 CC BY 4.0 许可协议。

[[2508.07917] MolmoAct: Action Reasoning Models that can Reason in Space](https://arxiv.org/abs/2508.07917?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-_L4bJJ6vXg6Hs10je6IoHKFICRZs2QVtY2uv4WUTWxZX4HrpAhzRVhAc_65PiMrUfftu9f)

[MolmoAct - a allenai Collection](https://huggingface.co/collections/allenai/molmoact-689697591a3936fba38174d7?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-_L4bJJ6vXg6Hs10je6IoHKFICRZs2QVtY2uv4WUTWxZX4HrpAhzRVhAc_65PiMrUfftu9f)

[allenai/molmoact: Official Repository for MolmoAct](https://github.com/allenai/MolmoAct?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-_L4bJJ6vXg6Hs10je6IoHKFICRZs2QVtY2uv4WUTWxZX4HrpAhzRVhAc_65PiMrUfftu9f)

[MolmoAct Data Mixture - a allenai Collection](https://huggingface.co/collections/allenai/molmoact-data-mixture-6897e583e13b6c2cf3ea2b80?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-_L4bJJ6vXg6Hs10je6IoHKFICRZs2QVtY2uv4WUTWxZX4HrpAhzRVhAc_65PiMrUfftu9f)

Key insight: Natural-language instructions don't translate precisely into spatial directions. Just as humans can navigate more effectively with a map, robots perform more accurately given a sense of 3D space (a depth map) and the desired trajectory (a motion path drawn over a camera's view). Along with a command like "take the cup off the table and put it in the trash," the additional information enables a robot to avoid collisions with objects and move more precisely.

核心观点是：自然语言指令（Natural-language instructions）无法精确地转换为空间方向（spatial directions）。就像人类借助地图可以更有效地导航一样，如果机器人也能获得三维空间感（depth map，例如深度图）和期望的轨迹（motion path，在摄像头视图上描绘的运动路径），它们的表现就会更准确。除了「把杯子从桌子上拿下来放到垃圾桶里」这样的命令，这些附加信息还能让机器人避免与物体发生碰撞，并实现更精确的移动。

How it works: MolmoAct uses a SigLIP2 pretrained vision transformer to encode camera images into tokens. Given the image tokens and text instructions, a pretrained Qwen2.5-7B large language model learned to generate tokens that represented (i) a depth map, (ii) a motion path, and  (ii) changes in joint positions.

MolmoAct 的工作原理如下：它利用一个名为 SigLIP2 的预训练视觉 Transformer（Transformer）将相机捕捉到的图像编码成一个个 Token。然后，给定这些图像 Token 和文本指令，一个名为 Qwen2.5-7B 的预训练大语言模型（Large Language Model）就会学习并生成表示以下信息的 Token：（i）深度图，（ii）运动路径，以及（ii）关节位置的变化。

1 The authors started with 24.3 million robot demonstrations of tasks such as "pick up the water bottle from the drawer and put it on the desk." Each example included a text instruction, camera views, and changes in joint positions. The authors augmented the examples with depth maps and motion paths.They generated the depth maps using a pretrained Depth Anything 2, and they produced visual paths by tracking the robot arm's gripper in the camera images using Molmo, a pretrained vision-language model.

研究人员首先收集了 2430 万个机器人演示数据，这些演示包含了「从抽屉里拿起水瓶放到桌子上」等各类任务。每个示例都包括文本指令、摄像头视图以及机器人关节位置的改变。研究人员随后为这些示例添加了深度图和运动路径进行增强。他们利用预训练的 Depth Anything 2 生成了深度图，并通过 Molmo（一个预训练的视觉 - 语言模型）跟踪摄像头图像中机器人手臂的夹持器，从而生成了视觉路径。

2 They trained Qwen2.5-7B on the augmented dataset. Given a text instruction and camera image, the model learned to generate tokens that represented, in this order, (i) a depth map, (ii) a visual path, and (iii) changes in joint positions.

研究人员在增强数据集上训练了 Qwen2.5-7B 模型。当给定一段文本指令和一张相机图像时，该模型能够学会生成一系列 token，这些 token 依次代表着：（i）深度图，（ii）视觉路径，以及（iii）关节位置的变化。

3 To improve the system's vision-language understanding, they further pretrained both models on 2 million examples of images and text scraped from the web.

为了提升系统的视觉语言理解能力，研究人员进一步利用从网络上抓取获得的 200 万个图像和文本示例，对这两个模型进行了预训练。

4 The authors fine-tuned the models to generate the next token in more than 2 million examples, which they collected themselves, of robots performing various tasks from start to finish. The examples included various combinations of text instructions, camera views, changes in joint positions, depth maps, and motion paths.

作者们对模型进行了微调，让它们学习在超过 200 万个示例中生成下一个 token。这些示例由他们亲自收集，记录了机器人从开始到结束执行各种任务的全过程。这些数据包含了文本指令、摄像机视角、关节位置变化、深度图以及运动路径等多种信息的组合。

5 At inference, users can see the next motion path before the robot moves and revise it by redrawing it via a tablet. This capability makes the robot's actions interpretable and enables users to address potential errors before they happen.

在模型推理阶段，用户可以在机器人移动之前预览其接下来的运动轨迹，并通过平板电脑重新绘制进行修改。这一功能让用户能够理解机器人的行为意图，并在潜在错误发生之前预先纠正。

Results: The authors tested MolmoAct's performance using one or two Franka robotic arms in a simulation as well as 15 real-world tasks, including opening a container, putting trash in a bin, and folding a towel. On average, the system outperformed all other competitors.

结果：作者在模拟环境下以及 15 项现实世界任务中，使用一个或两个 Franka 机械臂，测试了 MolmoAct 的性能。这些任务包括打开容器、将垃圾放入垃圾桶以及折叠毛巾。平均而言，该系统超越了所有其他竞争系统。

1 MolmoAct achieved 86.6 percent average success on diverse simulated challenges in LIBERO. The closest competitor, π0-FAST, achieved 85.5 percent average success.

MolmoAct 在 LIBERO 平台上的各种模拟挑战中，平均成功率达到了 86.6%。而其最接近的竞争对手 π0-FAST，平均成功率为 85.5%。

2 In real-world tasks, MolmoAct achieved 0.679 average task progress (a 0-to-1 score that represents how much of each task the robot completed, higher is better), while π0-FAST achieved 0.446 average task progress.

在现实世界任务中，MolmoAct 取得了 0.679 的平均任务进度（这是一个 0 到 1 的分数，用来衡量机器人完成各任务的程度，分数越高表示完成度越好），而 π0-FAST 则取得了 0.446 的平均任务进度。

Why it matters: Earlier robotic control systems that use LLMs to interpret text instructions map visual input and text instructions directly to low-level actions without explicitly representing 3D space or visual motion paths. MolmoAct's approach makes such systems more precise, adaptable, and explainable.

这项技术有何意义：早期的机器人控制系统会利用大语言模型（LLM）来理解文本指令，但这些系统通常直接将视觉输入和文本指令转化为机器人底层的具体动作，而没有明确地建模三维空间或视觉运动轨迹。MolmoAct 提出的新方法让这类系统变得更精确、适应性更强，也更易于我们理解其决策过程。

We're thinking: This robot system is definitely not lost in space!

我们认为：这个机器人系统绝对不会迷失在太空中！