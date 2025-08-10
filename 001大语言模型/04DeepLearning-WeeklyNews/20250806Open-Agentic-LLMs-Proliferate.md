## Open-Agentic-LLMs-Proliferate

[Open Agentic LLMs Proliferate, Robot Removes Gallbladders, Reasoning Models Boost Emissions, and more...](https://www.deeplearning.ai/the-batch/issue-313/)

Dear friends,

Recently Meta made headlines with unprecedented, massive compensation packages for AI model builders exceeding $100M (sometimes spread over multiple years). With the company planning to spend $66B-72B this year on capital expenses such as data centers, a meaningful fraction of which will be devoted to AI, from a purely financial point of view, it's not irrational to spend a few extra billion dollars on salaries to make sure this hardware is used well.

最近，Meta 因向其人工智能（AI）模型开发者提供了前所未有的巨额薪酬方案而登上头条，这些方案有时分多年支付，总额超过 1 亿美元。考虑到该公司今年计划在数据中心等资本支出上投入 660 亿至 720 亿美元，其中相当大一部分将专门用于 AI 领域，那么从纯粹的财务角度来看，为了确保这些昂贵的硬件资源能够得到充分利用，额外在薪资上投入几十亿美元，这笔开销是完全合情合理的。

A typical software-application startup that's not involved in training foundation models might spend 70-80% of its dollars on salaries, 5-10% on rent, and 10-25% on other operating expenses (cloud hosting, software licenses, marketing, legal/accounting, etc.). But scaling up models is so capital-intensive, salaries are a small fraction of the overall expense. This makes it feasible for businesses in this area to pay their relatively few employees exceptionally well. If you're spending tens of billions of dollars on GPU hardware, why not spend just a tenth of that on salaries? Even before Meta's recent offers, salaries of AI model trainers have been high, with many being paid $5-10M/year, although Meta has raised these numbers to new heights.

一家典型的软件应用初创公司，如果它不涉及训练基础模型（foundation models），那么其开销可能大部分都花在人员工资上，大约占总成本的 70-80%；租金占 5-10%；而其他运营费用，比如云托管、软件许可、市场营销、法律与会计等，则占 10-25%。然而，扩展大模型是一项资金极度密集的工作，其巨大的投入使得人员工资在总开支中只占很小一部分。正因为如此，这类公司才能为他们相对较少的员工支付极其丰厚的薪水。试想，如果一家公司在 GPU 硬件（GPU hardware）上投入了数百亿美元，那么花上其中十分之一用于支付员工薪资也就变得非常合理了。实际上，即使在 Meta 最近大幅提高报价之前，AI 模型训练师（AI model trainers）的薪资就已经相当可观了，许多人的年薪在 500 万至 1000 万美元之间，而 Meta 则将这些数字推向了新的高度。

Meta carries out many activities, including run Facebook, Instagram, WhatsApp, and Oculus. But the Llama/AI-training part of its operations is particularly capital-intensive. Many of Meta's properties rely on user-generated content (UGC) to attract attention, which is then monetized through advertising. AI is a huge threat and opportunity to such businesses: If AI-generated content (AIGC) substitutes for UGC to capture people's attention to sell ads against, this will transform the social-media landscape.

Meta 旗下有许多业务，包括运营 Facebook、Instagram、WhatsApp 和 Oculus 等。但在其各项业务中，Llama / 人工智能（AI）训练部分是特别资本密集型的。Meta 的许多产品都依赖用户生成内容（UGC）来吸引用户注意力，再通过广告实现商业化。人工智能（AI）对这类业务而言，既是巨大的威胁，也是巨大的机遇：如果人工智能生成内容（AIGC）能够取代用户生成内容（UGC）来吸引人们的注意力，进而销售广告，这将彻底改变社交媒体的格局。

This is why Meta — like TikTok, YouTube, and other social-media properties — is paying close attention to AIGC, and why making significant investments in AI is rational. Further, when Meta hires a key employee, not only does it gain the future work output of that person, but it also potentially gets insight into a competitor's technology, which also makes its willingness to pay high salaries a rational business move (so long as it does not adversely affect the company's culture).

这就是为什么 Meta — 和 TikTok、YouTube 等其他社交媒体平台一样 — 正在密切关注人工智能生成内容（AIGC），以及为什么对 AI 进行重大投资是合理之举。此外，当 Meta 招聘一位关键员工时，不仅能获得这位员工未来的工作成果，还有可能借此洞悉竞争对手的技术，这也使得 Meta 支付高薪的意愿成为一项合理的商业策略（只要这不会对公司文化产生负面影响）。

The pattern of capital-intensive businesses compensating employees extraordinarily well is not new. For example, Netflix expects to spend a huge $18B this year on content. This makes the salary expense of paying its 14,000 employees a small fraction of the total expense, which allows the company to routinely pay above-market salaries. Its ability to spend this way also shapes a distinctive culture that includes elements of "we're a sports team, not a family" (which seems to work for Netflix but isn't right for everyone). In contrast, a labor-intensive manufacturing business like Foxconn, which employs over 1 million people globally, has to be much more price-sensitive in what it pays people.

资本密集型企业（capital-intensive businesses）为员工提供高薪并非新鲜事。例如，Netflix 预计今年将在内容上投入高达 180 亿美元。这意味着支付其 14,000 名员工的薪水支出，只占公司总开支的一小部分。这使得 Netflix 能够持续支付高于市场水平的薪酬。这种大手笔的支出能力，也塑造了其独特的企业文化，其中包括「我们是一个运动队，而不是一个家庭」的理念（这似乎很适合 Netflix，但并非适用于所有公司）。相比之下，像富士康（Foxconn）这样在全球雇佣超过 100 万人的劳动密集型制造企业，在支付员工薪酬时就必须对价格敏感得多。

Even a decade ago, when I led a team that worked to scale up AI, I built spreadsheets that modeled how much of my budget to allocate toward salaries and how much to allocate toward GPUs (using a custom model for how much productive output N employees and M GPUs would lead to, so I could optimize N and M subject to my budget constraint). Since then, the business of scaling up AI has skewed the spending significantly toward GPUs.

即使早在十年前，当我负责一个致力于推动人工智能（AI）规模化发展的团队时，我就会制作电子表格来模拟如何分配预算：多少用于支付薪水，多少用于购买图形处理器（GPU）。我甚至还建立了一个自定义模型，用来计算 N 名员工和 M 个 GPU 能产生多少生产力，这样就能在预算限制下优化 N 和 M 的配比。而从那时起，随着 AI 规模化投入的不断增长，这方面的支出已经显著地向 GPU 倾斜了。

I'm happy for the individuals who are getting large pay packages. And regardless of any individual's pay, I'm grateful for the contributions of everyone working in AI. Everyone in AI deserves a good salary, and while the gaps in compensation are growing, I believe this reflects the broader phenomenon that developers who work in AI, at this moment in history, have an opportunity to make a huge impact and do world-changing work.

我很高兴看到那些获得丰厚薪酬的个人。当然，无论具体薪酬如何，我都要感谢每一位在 AI 领域工作的人所做出的贡献。所有 AI 从业者都应该得到一份不错的薪水。虽然我们看到薪酬差距正在扩大，但我认为这反映了一个更普遍的现象：在当下这个历史时刻，在 AI 领域工作的开发者们正面临一个绝佳的机会，他们能够产生巨大的影响，并从事改变世界的工作。

Keep building!

Andrew

### News

#### The Re-Opening of OpenAI

OpenAI 重新「开放」

The "open" is back in play at OpenAI.

「开放」精神在 OpenAI 重新活跃起来。

What's new: OpenAI released its first open-weights model since 2019's GPT-2. The gpt-oss family comprises two mixture-of-experts (MoE) models, gpt-oss-120b and gpt-oss-20b, that are designed for agentic applications and free to use and modify.

新进展：OpenAI 发布了自 2019 年 GPT-2 以来首个开放权重模型（open-weights model）。这个 gpt-oss 系列包含两个混合专家模型（Mixture-of-Experts，MoE），分别是 gpt-oss-120b 和 gpt-oss-20b。它们专为 AI 智能体（AI Agent）应用而设计，并且可以免费使用和修改。

1 Input/output: Text in (up to 128,000 tokens), text out (up to 33,000 tokens)

输入 / 输出：支持的文本输入（Token）数量高达 128,000 个，输出（Token）数量可达 33,000 个。

2 Architecture: gpt-oss-120b: MoE transformer, 117 billion parameters total, 5.1 billion parameters active per token; gpt-oss-20b: MoE transformer, 21 billion parameters total, 3.6 billion parameters active per token

架构：gpt-oss-120b 模型采用 MoE Transformer（专家混合 Transformer）架构，总参数量达到 1,170 亿，但在处理每个 Token 时，实际激活的参数为 51 亿；gpt-oss-20b 模型同样采用 MoE Transformer 架构，总参数量为 210 亿，在处理每个 Token 时，实际激活的参数为 36 亿。

3 Performance: Generally ahead of o3-mini, behind o3 and o4-mini

性能表现：整体优于 o3-mini，但不及 o3 和 o4-mini

4 Availability: Web demo (free), weights available for commercial and noncommercial use under Apache 2.0 license

获取方式：提供免费的网页演示（Web demo），模型权重（weights）可根据 Apache 2.0 许可证用于商业和非商业用途

5 Features: adjustable chain-of-thought reasoning levels (high, medium, low), full access to the chain of thought, tool use

功能：可调节的思维链（chain-of-thought）推理水平（高、中、低），完全透明的思维过程，支持工具使用。

6 Undisclosed: Details of training data and methods

未披露：训练数据和方法的具体细节。

How it works: The team pretrained the gpt-oss models on trillions of tokens of text including general knowledge, coding, math, and science. Fine-tuning focused on reasoning and tool use.

它是如何工作的：团队使用数万亿个 Token（Token）的文本对 gpt-oss 模型进行了预训练，这些文本涵盖了通用知识、编程、数学和科学等领域。随后的微调则着重于提升模型的推理能力和工具使用能力。

1 The team quantized the weights in MoE layers to use 4.25 bits per parameter. Since 90 percent or more of the parameters fall within MoE layers, this step enables gpt-oss-120b to run on a GPU with 80 gigabytes of memory and gpt-oss-20b to run on a GPU with 16 gigabytes of memory.

团队将专家混合层（MoE layers）中的模型权重（weights）进行了量化（quantized）处理，使其每个参数只占用 4.25 比特（bits）。由于 90% 甚至更多的参数都集中在 MoE 层中，这一优化措施让 gpt-oss-120b 模型得以在配备 80 GB 显存的 GPU 上运行，而 gpt-oss-20b 模型则可以在仅有 16 GB 显存的 GPU 上运行。

2 They fine-tuned the models to generate a chain of thought via supervised fine-tuning and reinforcement learning, a method similar to that used to fine-tune OpenAI o3.

他们对模型进行了微调，通过监督微调（supervised fine-tuning）和强化学习（reinforcement learning）来生成思维链（chain of thought）。这种方法类似于 OpenAI 微调其 o3 模型时所采用的方式。

3 During fine-tuning, they trained the models to support three reasoning levels by inserting into prompts phrases like "Reasoning:low".

在微调期间，研究人员通过在提示（prompt）中插入诸如「Reasoning:low」之类的短语，训练模型以支持三种不同程度的推理能力。

4 Similarly, they fine-tuned them to search the web, execute Python code, and use arbitrary tools.

同样地，他们也对模型进行了微调，使其能够搜索网络、执行 Python 代码以及使用各种工具。

5 They also trained the model to refuse requests for hate speech, instructions for committing crimes, recipes for hazardous substances, and the like. In internal tests designed to measure risky behavior, gpt-oss-120b, after being fine-tuned for biology and cybersecurity, fell short of "high capability" in those areas.

他们还训练了模型，使其能拒绝生成仇恨言论、指导实施犯罪的指令以及有害物质的制作方法等内容。在旨在衡量模型潜在危险行为的内部测试中，gpt-oss-120b 在经过生物学和网络安全领域的微调后，在这两个领域的能力表现未能达到「高水平」。

Results: Set to high reasoning effort, the models generally performed midway between o3-mini, o3, and o4-mini in OpenAI's tests. Unless otherwise noted, OpenAI results come from OpenAI's reporting, and DeepSeek R1's results come from its report on its latest update of the model.

结果显示：在推理能力被设定为高强度时，这些模型在 OpenAI 的测试中表现通常介于 o3-mini、o3 和 o4-mini 之间。除非另有说明，OpenAI 的测试结果均引自 OpenAI 发布的报告，而 DeepSeek R1 的结果则来自其最新模型更新报告。

1 Using tools to solve competition math problems in AIME 2024, gpt-oss-120b (96.6 percent accuracy) and gpt-oss-20b (96 percent accuracy) exceeded o3 (95.2 percent), but they fell short of o4-mini (98.7 percent).

在利用工具解决 2024 年 AIME 竞赛数学问题时，gpt-oss-120b 的准确率达到 96.6 %，gpt-oss-20b 的准确率达到 96 %，这两个模型都超越了 o3 的 95.2 % 准确率，但仍未能达到 o4-mini 的 98.7 % 准确率。

2 Answering science questions on GPQA Diamond without using tools, gpt-oss-120b (80.1 percent accuracy) outperformed o3-mini (77 percent) but underperformed o3 (83.3 percent) and o4-mini (81.4 percent). The smaller gpt-oss-20b (71.5 percent) came in last among OpenAI models presented. This puts gpt-oss behind Grok 4 (87.7 percent), Gemini 2.5 Pro (84.4 percent), and DeepSeek R1's latest update (81.3 percent), according to Artificial Analysis.

在不借助外部工具的情况下，回答 GPQA Diamond 上的科学问题时，gpt-oss-120b 以 80.1% 的准确率，表现优于 o3-mini（77%），但未能超越 o3（83.3%）和 o4-mini（81.4%）。其中，体量较小的 gpt-oss-20b（71.5%）在本次展示的 OpenAI 模型中垫底。根据 Artificial Analysis 的数据，gpt-oss 的整体表现落后于 Grok 4（87.7%）、Gemini 2.5 Pro（84.4%）以及 DeepSeek R1 的最新版本（81.3%）。

3 On the retail portion of Tau-Bench, a test of agentic tool use, gpt-oss-120b (67.8 percent accuracy) came in above o3 (65.6 percent) and below o4-mini (70.4 percent). These models outperformed DeepSeek R1 (63.9 percent accuracy). In comparison, gpt-oss-20b (54.8 percent accuracy) came in well below.

在 Tau-Bench（一项测试 AI 智能体（AI Agent）工具使用的基准）的零售领域测试中，gpt-oss-120b 的准确率达到 67.8%，表现优于 o3（准确率 65.6%），但略低于 o4-mini（准确率 70.4%）。这些模型均超越了 DeepSeek R1（准确率 63.9%）。相比之下，gpt-oss-20b 的准确率仅为 54.8%，表现远低于其他模型。

Behind the news: Founded in 2015 as a nonprofit corporation, OpenAI initially was devoted to open source development on the theory that AI would produce greater benefits and advance more safely if members of the community at large could inspect, use, and improve upon each others' work. However, in 2019, the high cost of building cutting-edge AI models led the organization to form a for-profit subsidiary, and it stopped releasing large language model weights (although it continued to publish weights for models such as Clip, which produces similar embeddings for related images and text, and Whisper, a speech-to-text engine).

新闻幕后：OpenAI 于 2015 年作为一家非营利公司成立，最初致力于开源开发。他们当时认为，如果广大社区成员能够检查、使用并改进彼此的成果，那么人工智能（AI）将会带来更大的效益，并以更安全的方式发展。然而，到了 2019 年，构建尖端 AI 模型的成本变得极其高昂，这促使该组织成立了一家营利性子公司，并停止发布大语言模型（Large Language Model）的权重。尽管如此，他们仍然继续发布某些模型的权重，例如 Clip（它能为相关的图像和文本生成相似的嵌入），以及 Whisper（一款语音转文本引擎）。

[OpenAI's Two New Multimodal AI Models, CLIP and DALL·E](https://www.deeplearning.ai/the-batch/tell-me-a-picture/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SHMSLwWemm8PEDhc5rWJu91pF37dx2tUx7W9bYQGIvCZJZpUjBe9XGIRPx5_9eoNSBs9w)

Why it matters: Businesses, developers, and users have a variety of reasons to choose models with open weights, including lower cost, greater control, and the ability to update as they wish. OpenAI's turn away from open source cleared the way for other teams to capture the market for open offerings. Now it's returning to a very different landscape. Meta jumped into the breach with its Llama models, along with Allen Institute for AI, Google, and others. Lately, developers in China such as Alibaba (Qwen3), DeepSeek (DeepSeek-R1), Moonshot (Kimi K2), and Z.ai have taken the lead. For developers, the gpt-oss family offers free access to technology designed by an extraordinary team of innovators. For OpenAI, it's an opportunity to capture the broad range of developers and users that prefer open models to closed ones.

为什么重要：对于企业、开发者和用户来说，选择开放权重（open weights）模型的原因有很多，比如成本更低、控制力更强，以及可以随心所欲地进行更新。OpenAI 曾一度放弃开源（open source）策略，这为其他团队抢占开放模型市场创造了机会。如今，当 OpenAI 再次回归时，它面对的是一个截然不同的市场格局。Meta 率先带着 Llama 模型趁虚而入，而 Allen Institute for AI、Google 等也紧随其后。最近，中国的一些开发者，例如阿里巴巴（Qwen3）、DeepSeek（DeepSeek-R1）、Moonshot（Kimi K2）和 Z.ai，更是走在了前列。对于开发者而言，gpt-oss 系列提供了一个由杰出创新团队打造的免费技术平台。对于 OpenAI 来说，这则是一个机会，可以吸引那些更倾向于开放模型而非封闭模型的广大开发者和用户。

We're thinking: A vibrant open source community is vital to AI's ongoing progress! Every open model holds valuable knowledge and functionality.

我们认为：一个充满活力的开源社区对人工智能（AI）的持续发展至关重要！每一个开放的模型都蕴含着宝贵的知识和功能。

#### Reasoning Boosts Carbon Emissions

推理能力与碳排放

In the era of reasoning models, delivering better answers to questions has an environmental cost. A new study quantifies the impact.

在推理模型（reasoning models）时代，想要提供更优质的问题答案，往往会伴随着环境代价。一项最新研究对这种影响进行了量化。

What's new: Researchers estimated the emissions of carbon dioxide and other heat-trapping gases associated with using 14 open-weights large language models. (The information needed to study closed models is not publicly available.) Reasoning, total tokens generated, and accuracy on question-answering benchmarks were associated with higher greenhouse-gas emissions, according to findings by Maximilian Dauner at Munich Center for Digital Sciences and AI and Gudrun Socher at HM Hochschule München University of Applied Sciences.

最新进展：研究人员估算了使用 14 个开放权重（open-weights）大语言模型（LLM）所产生的二氧化碳和其他温室气体（greenhouse-gas）的排放量。（由于相关信息未公开，该研究未能涵盖封闭模型（closed models）。）根据慕尼黑数字科学和人工智能中心（Munich Center for Digital Sciences and AI）的 Maximilian Dauner 和慕尼黑应用科学大学（HM Hochschule München University of Applied Sciences）的 Gudrun Socher 的研究结果，模型进行推理（reasoning）的能力、生成的总 Token（Token）数量，以及在问答基准测试中的准确性，都与更高的温室气体排放量密切相关。

How it works: The authors tested models of various sizes, with and without reasoning capabilities, using questions that required short and long answers.

工作原理：研究人员测试了各种大小、具备或不具备推理能力的模型，并使用了需要简短回答和详细回答的问题。

1 The authors tested Meta's non-reasoning models Llama 3.1 (8 billion and 70 billion parameters) and Llama 3.3 (70 billion parameters); Alibaba's non-reasoning models Qwen and Qwen 2.5 (7 billion and 72 billion parameters); Deep Cogito, which has reasoning and non-reasoning modes (8 billion and 70 billion parameters); and the reasoning model DeepSeek-R1 (7 billion, 8 billion, and 70 billion parameters).

研究人员测试了 Meta 公司旗下的非推理模型 Llama 3.1（80 亿和 700 亿参数）和 Llama 3.3（700 亿参数）；阿里巴巴旗下的非推理模型 Qwen 和 Qwen 2.5（70 亿和 720 亿参数）；Deep Cogito 模型，它既有推理模式也有非推理模式（80 亿和 700 亿参数）；以及推理模型 DeepSeek-R1（70 亿、80 亿和 700 亿参数）。

2 Each model answered 100 MMLU questions about five subjects (philosophy, world history, international law, abstract algebra, and mathematics). The questions took two forms: multiple-choice with single-word answers and prompts that elicited open-ended responses. OpenAI's o4-mini judged the open-ended responses.

每个模型都回答了 100 个 MMLU 问题，这些问题涵盖了五个科目：哲学、世界历史、国际法、抽象代数和数学。这些问题有两种形式：一种是答案为单个词语的多项选择题，另一种是需要开放式回答的提示。OpenAI 的 o4-mini 模型负责评判这些开放式回答。

3 The authors ran the models on an Nvidia A100 GPU with 80 gigabytes of memory and measured the amount of energy used by the chip. They multiplied the energy consumption in kilowatt-hours by a global average (480 grams of CO₂-equivalent per kilowatt-hour) to determine the resulting emissions.

作者将模型部署在配备 80 GB 内存的英伟达 Nvidia A100 GPU 上运行，并测量了该芯片的能耗。他们将以千瓦时计算的能耗乘以一个全球平均排放系数（即每千瓦时产生 480 克二氧化碳当量 CO₂-equivalent），从而计算出由此产生的碳排放量。

Results: The authors found a clear trade-off between reasoning (and the higher resulting numbers of tokens generated and output accuracy) and greenhouse-gas emissions.

结果：研究人员发现，在推理能力（以及因此带来的 Token（Token）生成数量增多和输出准确性提高）与温室气体排放之间，存在着一个明显的权衡关系。

1 The top-performing models achieved around 84 percent to 91 percent accuracy, resulting in around 1,300 grams to 2,000 grams of CO₂-equivalent greenhouse gas emissions per 1,000 questions (500 multiple-choice questions and 500 open-ended questions). By contrast, the smallest model achieved less than 35 percent accuracy and resulted in less than 30 grams of emissions.

表现最好的模型实现了大约 84% 到 91% 的准确率，但每处理 1,000 个问题（包括 500 个选择题和 500 个开放式问题），就会产生大约 1,300 克到 2,000 克二氧化碳当量温室气体排放（CO₂-equivalent greenhouse gas emissions）。相比之下，最小的模型准确率不到 35%，却只产生了不到 30 克的排放。

2 Deep Cogito's emissions multiplied by 4 to 6 times when reasoning was enabled. For example, the 8 billion-parameter version emitted around 372 grams of emissions with reasoning versus around 56 grams without reasoning.

Deep Cogito 模型在启用推理（reasoning）功能时，其碳排放量会增加 4 到 6 倍。举例来说，该模型 80 亿参数的版本在启用推理时大约排放 372 克碳，而未启用推理时大约只排放 56 克。

3 Open-ended responses resulted in still greater emissions. Models generated over 3 times more emissions while answering open-ended questions (an average of 345.55 grams) than they did when answering multiple-choice questions (109.52 grams).

开放式回答造成的碳排放量更高。模型在回答开放式问题时，产生的排放量（平均 345.55 克）是回答多项选择题时（109.52 克）的 3 倍多。

4 Deep Cogito with 70 billion parameters bucked the trend. With reasoning enabled, it achieved the highest overall accuracy (84.9 percent) while emitting around 34 percent fewer grams than DeepSeek-R1 with 70 billion parameters (78.9 percent accuracy). This result suggests that energy efficiency can vary dramatically among reasoning models.

拥有 700 亿参数的 Deep Cogito 大语言模型则展现出令人惊喜的表现。在启用推理功能后，它不仅取得了最高的总体准确率（84.9%），而且相较于拥有 700 亿参数的 DeepSeek-R1 模型（准确率为 78.9%），其能耗减少了约 34%。这一结果提示我们，不同推理模型之间的能源效率可能会存在显著差异。

Yes, but: The authors' estimates of carbon emissions likely are overestimates. Older GPUs such as the A100 are less energy-efficient than newer ones; and much cloud computing takes place in data centers powered by renewable energy sources that emit less carbon than global average energy consumption. For example, Google and Amazon match their electricity consumption with renewable energy, and Meta has powered its data centers solely by renewable energy since 2020.

不过，作者们对碳排放的估算，很可能被高估了。这是因为，像 A100 这样老旧的 GPU（图形处理器）在能效方面不如新型号；而且许多云计算服务都运行在由可再生能源供电的数据中心，这些数据中心的碳排放量远低于全球平均能源消耗水平。例如，Google 和 Amazon 都承诺其用电量与可再生能源用量相当，而 Meta 更是在 2020 年就实现了数据中心完全由可再生能源供电。

Why it matters: The International Energy Agency projects that AI will consume increasing amounts of energy, and thus produce more greenhouse-gas emissions, as companies focus on training and serving ever larger models. Current AI poses a double-barreled challenge: The more accurate a model's output, (i) the more emissions it will produce and (ii) the more people will query it. Much of the thinking about how to manage this issue has pointed to leaner parameter counts: Smaller models consume less energy. But the authors' findings instead point to strategic deployment: The right model for the right task. AI providers can reduce emissions by routing inputs to models that can process them both accurately and efficiently, and by limiting outputs to appropriate lengths. These strategies don't require building new infrastructure or models.

为何重要：国际能源署（International Energy Agency）预测，随着各大公司专注于训练和部署规模日益庞大的模型，人工智能（AI）将消耗越来越多的能源，进而产生更多的温室气体排放。当前的 AI 面临着一个双重挑战：模型的输出越准确，一方面它产生的排放越多，另一方面查询它的人也会越多。此前，关于如何解决这一问题的许多观点都倾向于削减模型的参数数量，即认为模型越小，能耗就越低。然而，作者们的研究结果却提出了不同的策略：更强调战略性部署，也就是为具体的任务选择最合适的模型。AI 提供商可以通过将输入数据导向那些既能准确又能高效处理它们的模型，并通过将输出内容的长度限制在恰当的范围，从而有效减少碳排放。这些策略的优势在于，它们无需构建新的基础设施或模型。

We're thinking: We must continue to work toward improving AI's energy efficiency and reducing its carbon emissions. That said, in many tasks, using AI produces fewer emissions than other approaches, such as using human labor.

我们的观点是：我们必须持续致力于提升人工智能（AI）的能源效率，并努力减少其碳排放。尽管如此，在许多任务中，使用 AI 产生的排放量实际上比其他方法（例如人工操作）要少。

#### GLM-4.5, an Open, Agentic Contender

GLM-4.5：一个开放的 AI 智能体（AI Agent）领域竞争者

The race is on to develop large language models that can drive agentic interactions. Following the one-two punch of Moonshot's Kimi K2 and Alibaba's Qwen3-235B-A22B update, China's Z.ai aims to one-up the competition.

一场开发能够驱动 AI 智能体（AI Agent）交互的大语言模型（LLM）竞赛正在如火如荼地进行。在月之暗面的 Kimi K2 和阿里巴巴的 Qwen3-235B-A22B 更新接连发布之后，中国的 Z.ai 旨在超越这些竞争对手。

What's new: GLM-4.5 is a family of open-weights models trained to excel at tool use and coding. The family includes GLM-4.5 and the smaller GLM-4.5-Air, both of which offer reasoning that can be switched on or off.

最新进展：GLM-4.5 是一个开放权重模型家族，经过训练，在工具使用和编码方面表现出色。该家族包括 GLM-4.5 和尺寸更小的 GLM-4.5-Air，两者都具备可开关的推理（reasoning）能力。

1 Input/output: Text in (up to 128,000 tokens), text out (up to 96,000 tokens)

输入 / 输出：支持最多 128,000 个 Token（token）的文本输入，以及最多 96,000 个 Token 的文本输出。

2 Architecture: Mixture-of-experts (MoE) transformer. GLM-4.5: 355 billion parameters total, 32 billion active at any given time. GLM-4.5-Air: 106 billion parameters total, 12 billion active at any given time.

架构：采用混合专家模型（Mixture-of-experts，MoE）Transformer（Transformer）架构。其中，GLM-4.5 模型总参数量达到 3550 亿个，在同一时间约有 320 亿个参数处于活跃状态。而 GLM-4.5-Air 模型总参数量为 1060 亿个，在同一时间有约 120 亿个参数被激活。

3 Performance: Both models outperform Anthropic Claude 4 Opus, DeepSeek-R1-0528, Google Gemini 2.5 Pro, Grok 4, Kimi K2, and/or OpenAI o3 on at least one reasoning, coding, or agentic benchmark

性能：这两个模型在至少一项推理、编码或智能体能力基准测试中，表现都超越了 Anthropic Claude 4 Opus、DeepSeek-R1-0528、Google Gemini 2.5 Pro、Grok 4、Kimi K2 以及 / 或者 OpenAI o3。

4 Availability: Web interface (free), API (GLM-4.5: $0.60/$0.11/$2.20 per million input/cached/output tokens; GLM-4.5-Air: $0.20/$0.03/$1.10), weights available via HuggingFace and ModelScope for commercial and noncommercial uses under MIT license

可用性：该模型可通过网页界面免费使用，也可通过 API（应用程序编程接口）调用（GLM-4.5：每百万输入 Token（标记）费用为 $0.60，缓存 Token 为 $0.11，输出 Token 为 $2.20；GLM-4.5-Air：费用分别为 $0.20/$0.03/$1.10）。此外，模型权重可通过 HuggingFace 和 ModelScope 获取，并根据 MIT 许可证，可用于商业和非商业目的。

5 Features: Function calling, switchable reasoning/non-reasoning

功能特性：支持函数调用（Function calling），可在推理和非推理模式之间切换

6 Undisclosed: Specific training datasets

未公开信息：具体的训练数据集

How it works: GLM-4.5 models include several architectural features that differ from other recent MoE models. Instead of adding more experts or making the experts use more parameters per layer (which would make the models wider), the team increased the number of layers per expert (which makes them deeper). The pretraining/fine-tuning process distilled three models into one.

工作原理：GLM-4.5 模型在架构上拥有几个显著特点，这些特点使其有别于其他近期出现的混合专家模型（Mixture-of-Experts，MoE）。不同于常见的做法 —— 即增加更多专家数量，或是让每个专家在单层中使用更多参数（那样会让模型变得「更宽」），GLM-4.5 团队选择了一种新路径：他们增加了每个专家的层数，这使得模型在深度上有所增加，变得「更深」。此外，通过独特的预训练和微调过程，该团队成功地将三个模型融合成了一个整体。

1 The team pre-trained the models on 22 trillion tokens: 15 trillion tokens of text followed by 7 trillion tokens of further text devoted to code and reasoning.

团队在 22 万亿 Token 上预训练了这些模型：首先是 15 万亿 Token 的文本数据，随后又用了 7 万亿 Token 专注于代码和推理的文本数据进行训练。

2 They fine-tuned three copies of the pretrained GLM-4.5 using supervised fine-tuning and reinforcement learning, producing specialized versions for reasoning, agentic capabilities, and general knowledge. Then they fine-tuned the pretrained model to match the outputs from the specialized versions, producing one model with the capabilities of all three. Finally, they fine-tuned this model via reinforcement learning on further reasoning, agentic, and general data.

研究人员首先对预训练的 GLM-4.5 进行了三份副本的微调。他们分别采用了监督微调（supervised fine-tuning）和强化学习（reinforcement learning）的方法，针对推理、AI 智能体（AI Agent）能力和通用知识，各生成了一个专门的版本。接着，他们对原始的预训练模型进行微调，使其输出结果与这些专门版本保持一致，最终得到一个兼具这三方面能力的模型。最后，他们利用更多的推理、AI 智能体和通用数据，通过强化学习对这个模型进行了进一步的微调。

Results: The team compared GLM-4.5 and GLM-4.5-Air to top open and closed models across 12 benchmarks that assess reasoning, coding, and tool use.

结果：该团队比较了 GLM-4.5 和 GLM-4.5-Air 与其他顶尖的开源和闭源模型在 12 个评估推理、编码和工具使用的基准测试中的表现。

1 In an average of tool-use benchmarks (TAU-Bench, BFCL v3 Full, ad BrowseComp), GLM-4.5 (90.6 percent accuracy) outperformed Claude Sonnet 4 (89.5 percent accuracy), Kimi K2 (86.2 percent accuracy), and Qwen3-Coder (77.1 percent accuracy). On BrowseComp (web browsing with multi-step searches), GLM-4.5 (26.4 percent accuracy) outperformed Claude 4 Opus (18.8 percent accuracy) but trailed o3 (49.7 percent accuracy).

在工具使用基准测试（TAU-Bench、BFCL v3 Full 以及 BrowseComp）的平均表现上，GLM-4.5（90.6% 准确率）超过了 Claude Sonnet 4（89.5% 准确率）、Kimi K2（86.2% 准确率）和 Qwen3-Coder（77.1% 准确率）。在 BrowseComp（一项涉及多步搜索的网页浏览任务）上，GLM-4.5（26.4% 准确率）优于 Claude 4 Opus（18.8% 准确率），但略低于 o3（49.7% 准确率）。

2 On MATH 500 (selected competition-level problems),GLM-4.5 (98.2 percent accuracy) equalled Claude 4 Opus. On AIME24 (competition math), GLM-4.5 (91.0 percent accuracy) outperformed Claude Opus 4 (75.7 percent accuracy) but trailed Qwen3-235B-Thinking (94.1 percent accuracy).

在 MATH 500（精选的竞赛级问题）测试中，GLM-4.5 以 98.2% 的准确率与 Claude 4 Opus 旗鼓相当。而在 AIME24（竞赛数学）测试中，GLM-4.5 取得了 91.0% 的准确率，超越了 Claude Opus 4（75.7% 的准确率），但略逊于 Qwen3-235B-Thinking（94.1% 的准确率）。

3 On SWE-bench Verified (software engineering problems), GLM-4.5 (64.2 percent) outperformed Kimi K2 (65.4 percent) but trailed Claude 4 Sonnet (70.4 percent) and Qwen3-Coder (67 percent, tested separately). In Z.ai's own evaluation across 52 coding tasks, GLM-4.5 achieved an 80.8 percent win rate against Qwen3-Coder and a 53.9 percent win rate against Kimi K2.

在 SWE-bench Verified（软件工程问题）的基准测试中，GLM-4.5（64.2%）在某种程度上优于 Kimi K2（65.4%），但仍落后于 Claude 4 Sonnet（70.4%）和 Qwen3-Coder（67%，该数据是独立测试所得）。

而在 Z.ai 针对 52 项编码任务进行的内部评估中，GLM-4.5 取得了亮眼的成绩：对 Qwen3-Coder 的胜率高达 80.8%，对 Kimi K2 的胜率也达到了 53.9%。

4 GLM-4.5-Air excelled against likely larger models on multiple benchmarks, For instance, on BFCL v3, GLM-4.5-Air (76.4 percent) outperformed Gemini Pro 2.5 (61.2 percent). On AIME 2024, GLM-4.5-Air (89.4 percent) outperformed Claude 4 Opus (75.7 percent).

GLM-4.5-Air 在多个基准测试中表现卓越，甚至超越了那些可能规模更大的模型。例如，在 BFCL v3 测试中，GLM-4.5-Air 的得分达到 76.4%，领先于 Gemini Pro 2.5 的 61.2%。而在 AIME 2024 测试中，GLM-4.5-Air 更是取得了 89.4% 的优异成绩，超越了 Claude 4 Opus 的 75.7%。

Behind the news: A rapid run of releases by teams in China — Kimi K2, Qwen3's updates, and now GLM-4.5 — has established momentum in open-weights, large language models that are tuned for agentic behavior.

深挖一下最近的新闻，我们发现：中国团队 —— 包括 Kimi K2、Qwen3 的更新，以及现在推出的 GLM-4.5 —— 密集发布了一系列成果。这些快速的发布，为那些专门针对 AI 智能体（AI Agent）行为进行了优化的开源权重（open-weights）大语言模型，奠定了强劲的发展势头。

Why it matters: It's not uncommon to distill larger models into smaller ones, sometimes to shrink the parameter count, sometimes to improve an existing small model's performance. Z.ai's approach distilled not a larger model but three specialized variations on the base model.

这为什么重要：将大模型「蒸馏」（distill）成小模型的情况并不少见，这通常有两个目的：一是减少模型的参数量，二是提升现有小模型的性能表现。然而，Z.ai 采取了一种独特的方法，他们蒸馏的不是一个独立的大模型，而是基于同一个基础模型，衍生出的三个经过专门优化的变体。

We're thinking: The "best" open model for agentic applications is shifting weekly, creating both exciting opportunities and daunting challenges for developers.

我们认为：用于 AI 智能体（AI Agent）应用的「最佳」开放模型每周都在发生变化，这既为开发者带来了激动人心的机遇，也带来了严峻的挑战。

#### Robot Surgeon Cuts and Clips

机器人外科医生切割和夹取

An autonomous robot performed intricate surgical operations without human intervention.

一个自主机器人（autonomous robot）在没有人类干预的情况下，完成了精细的外科手术操作。

What's new: Ji Woong (Brian) Kim and colleagues at Johns Hopkins, Stanford, and the surgical technology company Optosurgical developed Hierarchical Surgical Robot Transformer (SRT-H), a system that performs surgery with only routine help from humans. The system, which uses a two-armed surgical robot that ordinarily is operated by hand, successfully completed the key clipping-and-cutting steps to remove gallbladders.

最新消息：来自 Johns Hopkins、Stanford 和外科技术公司 Optosurgical 的 Ji Woong（Brian）Kim 及其同事开发了一套名为「分层外科机器人 Transformer（Hierarchical Surgical Robot Transformer，SRT-H）」的系统。这套系统在执行手术时，仅需人类提供日常协助。该系统利用一台通常需要人工操作的双臂外科机器人，成功完成了胆囊切除术中关键的夹闭和切割步骤。

How it works: SRT-H pairs two transformer models: a high-level planner that decides what step to take next and a low-level action generator that turns the planner's decision into signals that control an Intuitive Surgical da Vinci robot. Both models were trained via imitation learning. That is, they learned to map images and text to robot arm motions by copying recorded human demonstrations.

工作原理：SRT-H 结合了两个 Transformer 模型：一个高级规划器，负责决定下一步的行动；以及一个低级动作生成器，将规划器的决策转化为控制 Intuitive Surgical da Vinci 机器人的信号。这两个模型都通过模仿学习（imitation learning）进行训练。这意味着，它们通过学习人类录制的演示，学会了将图像和文本信息转化为机器手臂的动作。

[[2505.10251] SRT-H: A Hierarchical Framework for Autonomous Surgery via Language Conditioned Imitation Learning](https://arxiv.org/abs/2505.10251?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SHMSLwWemm8PEDhc5rWJu91pF37dx2tUx7W9bYQGIvCZJZpUjBe9XGIRPx5_9eoNSBs9w)

1 To build a training dataset, the team recorded around 17 hours of operations in which humans operated the robot, performing 17 steps to remove gallbladders from 34 pig tissues that had been separated from the animals' bodies. The recordings captured the outputs of a tube-mounted endoscope, two cameras mounted on the robot's wrists, and the translations, rotations, and gripper openings of each robot arm.

为了构建一个训练数据集，研究团队记录了大约 17 小时的人工操作机器人进行手术的过程。在这些操作中，机器人完成了 17 个步骤，将胆囊从 34 份已从动物体中分离出来的猪组织上成功切除。这些录像详细记录了管载内窥镜（tube-mounted endoscope）的画面、安装在机器人手腕上的两台相机的影像，以及每个机械臂的平移、旋转和夹持器开口的数据。

2 Annotators labeled each step (such as "grab gallbladder" and "place second clip on left tube") along with corrective instructions wherever the surgeons revised their actions in progress (for instance, "move right arm to the right"). This process resulted in roughly 16,000 labeled, time-stamped, brief sequences of images with corresponding robotics data and natural-language labels.

标注人员对每个操作步骤都进行了标记（例如「抓取胆囊」和「在左侧导管上放置第二个夹子」）。同时，每当外科医生在操作过程中进行修正时，标注人员还会附上纠正性指令（例如「将右臂向右移动」）。通过这个过程，我们获得了大约 16,000 个已标记、带有时间戳的简短图像序列，这些序列都包含了对应的机器人数据和自然语言（Natural Language）标签。

3 Given the 5 most recent endoscope frames, the high-level transformer learned to predict (i) whether a correction was required (that is, whether the surgeons revised their actions) and, if so, an appropriate natural language instruction for the correction and (ii) an instruction that described the next step in the surgery. A pretrained Swin-T encoded the images, and the transformer's decoder learned to output the next step, binary correction flag, and corrective instruction.

给定最近的 5 帧内窥镜画面，高层 Transformer 模型学会了预测：（i）是否需要进行修正（也就是外科医生是否需要调整他们的操作），如果需要，它会给出一个恰当的自然语言修正指令；以及（ii）一条描述手术下一步操作的指令。一个预训练的 Swin-T 模型负责对图像进行编码，随后 Transformer 的解码器则学习输出接下来的操作步骤、一个表示是否需要修正的二进制标志，以及具体的修正指令。

4 Given the high-level transformer's correction flag, next-step instruction, and corrective instruction as well as images from the endoscope and wrist cameras, the low-level transformer learned to generate around the next 2 seconds of robot motion. A pretrained EfficientNet-B3 encoded the images, a pretrained DistilBERT embedded the next-step instruction, FiLM layers aligned the embedded instruction with relevant image features, aligning the visual representation with the current instruction. The transformer's decoder learned to generate the next robot action sequence.

考虑到高级 Transformer（Transformer）提供的修正标志、下一步指令和校正指令，以及来自内窥镜和腕部摄像头的图像信息，低级 Transformer 能够学会生成大约未来 2 秒的机器人运动。具体来说，一个预训练好的 EfficientNet-B3 负责对图像进行编码（encode），一个预训练好的 DistilBERT 则将下一步指令嵌入（embed）到系统中。接着，FiLM 层将这些嵌入后的指令与相关的图像特征对齐，从而实现了视觉信息与当前指令的有效融合。最终，这个 Transformer 的解码器学会了生成下一步的机器人动作序列。

5 At inference, every 3 seconds, the high-level transformer processed the 5 most recent endoscope frames and issued a correction flag, next-step instruction, and corrective instruction. It used the flag to decide which instruction to pass to the low-level transformer. Then the low-level transformer executed actions in chunks, taking roughly 30 time steps for grabbing and 20 time steps for clipping and cutting. It paused automatically for humans to load new clips or swap between cutter and clip applier tools, a role normally assigned to a surgical nurse.

在进行推理时，每隔 3 秒，高级 Transformer（high-level transformer）就会处理最新的 5 帧内窥镜图像，并发出一个纠正标志、下一步操作指令以及具体的纠正指令。它会根据这个纠正标志来决定向低级 Transformer（low-level transformer）传递哪条指令。接着，低级 Transformer 会分批执行动作，其中抓取操作大约需要 30 个时间步，而裁剪和切割则需要 20 个时间步。为了方便操作人员装载新的夹子，或者在切割器和夹子施加器工具之间切换，系统还会自动暂停 —— 这项工作通常由手术护士来完成。

Results: Tested on 8 pig tissues, SRT-H successfully performed each operation, correcting its own mistakes along the way.

结果：对 8 块猪组织进行测试后发现，SRT-H 成功完成了每一项操作，并且在执行过程中还能自我纠正错误。

1 SRT-H successfully completed all 17 clipping-and-cutting steps on all tissues despite individual variations. When it encountered a problem, it corrected itself and proceeded to complete the operation successfully.

尽管每块组织存在个体差异，SRT-H 依然成功完成了所有 17 个夹闭 - 切割步骤。当它遇到问题时，能够及时进行自我修正，并继续顺利完成操作。

2 The high-level transformer correctly predicted next-step instructions with 97 percent accuracy, correction flags with 95 percent accuracy, and corrective instructions (among 18 possible classes of motion) with 70 percent accuracy.

这个高级 Transformer 模型（Transformer）成功地预测了多个关键指标：对于下一步指令的预测准确率高达 97%；对纠正标记的预测准确率为 95%；而在 18 种可能的运动类别中，其对纠正指令的预测准确率也达到了 70%。

3 In a preliminary comparison with an expert surgeon, SRT-H moved the robot less and moved it more smoothly than the surgeon did. However, SRT-H was nearly 41 percent slower. (The authors modified SRT-H's instruments so they would perform clipping and cutting motions without actually clipping or cutting tissue. This enabled the surgeon to operate on the same tissues as the robot.)

在与一位专家外科医生进行的初步比较中，SRT-H 控制机器人移动的距离更短，而且移动轨迹比外科医生更平滑。然而，SRT-H 的操作速度却慢了近 41%。(为了让外科医生能在与机器人相同的组织上进行操作，研究人员对 SRT-H 的器械进行了改造，使其能模拟夹持和切割动作，而不会真正夹持或切割组织。)

Yes, but: The authors tested SRT-H on tissues that had been removed from an animal's body. Real-world surgery involves the body as a whole, and surgeons must manage bleeding, tissue motion from respiration, and visual occlusions that might challenge SRT-H.

不过，需要指出的是：研究人员是在从动物体内取出的离体组织上测试 SRT-H 的。而在真实的手术环境中，手术是在活体上进行的，外科医生必须处理出血、由呼吸引起的组织运动，以及可能对 SRT-H 构成挑战的视觉遮挡。

Behind the news: Prior autonomous surgical systems often rely on custom hardware and setup. For instance, Smart Tissue Autonomous Robot (STAR), which combines model-based planning with a hand-crafted state machine, uses an enhanced endoscope. The instrument integrates near-infrared fluorescence (NIR) and 3D imaging, so the system can be guided by NIR markers on a patient's tissue and plan sutures on 3D surfaces. By contrast, SRT-H uses the widely deployed da Vinci robot (over 10,000 units in hospitals globally) and learned from RGB video with annotations in natural language — no NIR markers, 3D scanners, or special fixtures.

新闻解读：以往的自主手术系统（autonomous surgical systems）通常需要依赖定制的硬件和特定的设置。例如，智能组织自主机器人（Smart Tissue Autonomous Robot，STAR）系统，它结合了基于模型的规划（model-based planning）和人工预设的状态机（state machine），并配备了增强型内窥镜（endoscope）。这个内窥镜集成了近红外荧光（Near-infrared fluorescence，NIR）技术和 3D 成像（3D imaging）能力，使得系统可以通过患者组织上的 NIR 标记进行引导，并在 3D 表面上规划缝合点。与此形成对比的是，SRT-H 系统则利用了全球医院已广泛部署的达芬奇机器人（其全球装机量超过 10,000 台），并且能直接从带有自然语言标注（annotations in natural language）的 RGB 视频（RGB video）数据中学习 —— 它无需 NIR 标记、3D 扫描仪或任何特殊的固定装置。

Why it matters: SRT-H is a significant step toward surgeries that can be performed safely by an autonomous robot. There's still a long way to go: The system performed only portions of gallbladder removals, and it did so on tissues that were outside the body. Nonetheless, it did its job nearly flawlessly. Its natural language interface makes its decisions interpretable and enables humans to override or correct the system using verbal commands, important steps toward safe autonomous surgeries. And since SRT-H relies on imitation learning, presumably it could learn to perform other procedures, given appropriate demonstrations.

这项研究为何重要：SRT-H 的问世，是朝着实现由自主机器人安全进行手术迈出的重要一步。当然，我们还有很长的路要走：该系统目前仅完成了部分胆囊切除术，而且是在体外组织上进行的。尽管如此，它几乎完美无瑕地完成了任务。其自然语言接口（natural language interface）使其决策过程变得可解释，并且人类可以通过口头指令来干预或纠正系统，这对于确保自主手术的安全性至关重要。此外，由于 SRT-H 依赖于模仿学习（imitation learning），因此它很有可能在获得适当的演示后，学会执行其他类型的手术。

We're thinking: In an operating room, the ability to recover from unexpected events trumps perfect execution of predetermined plans. SRT-H's correction system enables the system to recover from its own mistakes — an important advantage over rigid systems that may work well in the lab but struggle under real-world conditions.

我们认为：在手术室里，从突发事件中恢复的能力，要比完美执行预设方案更为重要。SRT-H 的纠正系统，能够让系统从自身的错误中恢复过来 —— 与那些在实验室里表现出色、但在真实世界环境下却举步维艰的「僵硬」系统相比，这无疑是一个巨大的优势。