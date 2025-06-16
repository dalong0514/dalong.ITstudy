## 20250611FLUX1-Kontexts-Consistent-Characters

[FLUX.1 Kontext’s Consistent Characters, Benchmarking Costs Climb, and more...](https://www.deeplearning.ai/the-batch/issue-305/)

Dear friends,

There's a new breed of GenAI Application Engineers who can build more-powerful applications faster than was possible before，thanks to generative AI. Individuals who can play this role are highly sought-after by businesses，but the job description is still coming into focus. Let me describe their key skills，as well as the sorts of interview questions I use to identify them.

得益于生成式 AI（Generative AI），一类新的生成式 AI 应用工程师（GenAI Application Engineers）正在崛起。他们能够以比以往更快的速度构建出更强大的应用程序。具备这种能力的人才备受企业青睐，但其职责范围仍在不断明确。接下来，我将介绍他们的关键技能，以及我用来识别这类人才的面试问题。

Skilled GenAI Application Engineers meet two primary criteria：(i）They are able to use the new AI building blocks to quickly build powerful applications.（ii）They are able to use AI assistance to carry out rapid engineering，building software systems in dramatically less time than was possible before. In addition，good product/design instincts are a significant bonus.

优秀的生成式 AI 应用工程师通常具备以下两个主要特质：(i）他们能够利用新型 AI 构建块（AI building blocks）迅速开发出功能强大的应用程序。(ii）他们能够借助 AI 辅助进行高效的工程开发，以远超以往的速度构建软件系统。此外，良好的产品 / 设计直觉是额外的重要优势。

AI building blocks. If you own a lot of copies of only a single type of Lego brick，you might be able to build some basic structures. But if you own many types of bricks，you can combine them rapidly to form complex，functional structures. Software frameworks，SDKs，and other such tools are like that. If all you know is how to call a large language model（LLM) API，that's a great start. But if you have a broad range of building block types — such as prompting techniques，agentic frameworks，evals，guardrails，RAG，voice stack，async programming，data extraction，embeddings/vectorDBs，model fine tuning，graphDB usage with LLMs，agentic browser/computer use，MCP，reasoning models，and so on — then you can create much richer combinations of building blocks.

**AI 构建块**

如果你只有大量单一类型的乐高积木，你可能只能建造一些基本结构。但如果你拥有多种类型的积木，你就可以迅速地将它们组合起来，形成复杂且功能齐全的结构。软件框架、SDK（软件开发工具包）等工具也正是如此。如果你只知道如何调用大语言模型（LLM）API，这固然是个不错的开端。但如果你掌握了广泛的构建块类型 —— 例如提示技术、智能体框架（Agentic frameworks）、评估（Evals）、护栏（Guardrails）、检索增强生成（RAG）、语音堆栈（Voice stack）、异步编程（Async programming）、数据提取（Data extraction）、嵌入 / 向量数据库（Embeddings/vectorDBs）、模型微调（Model fine tuning）、结合大语言模型使用图数据库（GraphDB usage with LLMs）、智能体浏览器 / 计算机使用（Agentic browser/computer use）、MCP、推理模型（Reasoning models）等等 —— 那么你就能创造出更丰富多样的构建块组合。

The number of powerful AI building blocks continues to grow rapidly. But as open-source contributors and businesses make more building blocks available，staying on top of what is available helps you keep on expanding what you can build. Even though new building blocks are created，many building blocks from 1 to 2 years ago（such as eval techniques or frameworks for using vectorDBs）are still very relevant today.

强大的 AI 构建块的数量正在快速增长。随着开源贡献者和企业不断推出更多构建块，及时了解这些最新进展有助于你不断提升你的开发能力。即便新的构建块层出不穷，但许多一两年前的构建块（例如评估技术或使用向量数据库的框架）在今天依然非常重要且实用。

AI-assisted coding. AI-assisted coding tools enable developers to be far more productive，and such tools are advancing rapidly. Github Copilot，first announced in 2021（and made widely available in 2022），pioneered modern code autocompletion. But shortly after，a new breed of AI-enabled IDEs such as Cursor and Windsurf offered much better code-QA and code generation. As LLMs improved，these AI-assisted coding tools that were built on them improved as well.

**AI 辅助编码**

AI 辅助编码工具能够显著提升开发人员的生产力，并且这类工具正在迅速发展。Github Copilot 于 2021 年首次发布（并于 2022 年全面普及），开创了现代代码自动补全的先河。但不久之后，Cursor 和 Windsurf 等一批 AI 赋能的集成开发环境（IDE）提供了更出色的代码质量保证（Code-QA）和代码生成功能。随着大语言模型的不断进步，这些基于大语言模型构建的 AI 辅助编码工具也随之提升。

Now we have highly agentic coding assistants such as OpenAI's Codex and Anthropic's Claude Code（which I really enjoy using and find impressive in its ability to write code，test，and debug autonomously for many iterations). In the hands of skilled engineers — who don't just「vibe code」 but deeply understand AI and software architecture fundamentals and can steer a system toward a thoughtfully selected product goal — these tools make it possible to build software with unmatched speed and efficiency.

现在我们拥有高度智能体（Agentic）的编码助手，例如 OpenAI 的 Codex 和 Anthropic 的 Claude Code（我非常喜欢使用它们，并且它们在多次迭代中自主编写、测试和调试代码的能力令我印象深刻）。在经验丰富的工程师手中 —— 他们不只是「凭感觉写代码」，而是对 AI 和软件架构基础有深入理解，并能将系统引导至经过深思熟虑的产品目标 —— 这些工具使得软件开发速度和效率达到了前所未有的高度。

I find that AI-assisted coding techniques become obsolete much faster than AI building blocks，and techniques from 1 or 2 years ago are far from today's best practices. Part of the reason for this might be that，while AI builders might use dozens（hundreds?）of different building blocks，they aren't likely to use dozens of different coding assistance tools at once，and so the forces of Darwinian competition are stronger among tools. Given the massive investments in this space by  Anthropic，Google，OpenAI，and other players，I expect the frenetic pace of development to continue，but keeping up with the latest developments in AI-assisted coding tools will pay off，since each generation is much better than the last.

我发现 AI 辅助编码技术迭代速度远超 AI 构建块，一两年前的技术已经与当今的最佳实践大相径庭。部分原因可能在于，AI 开发者可能会使用几十种（甚至几百种？）不同的构建块，但他们不太可能同时使用几十种不同的编码辅助工具，因此工具之间的「达尔文式竞争」更为激烈。鉴于 Anthropic、Google、OpenAI 及其他参与者在该领域的巨额投入，我预计这种飞速的开发步伐将继续下去。但紧跟 AI 辅助编码工具的最新发展将让你受益匪浅，因为每一代产品都比上一代更加出色。

Bonus：Product skills. In some companies，engineers are expected to take pixel-perfect drawings of a product，specified in great detail，and write code to implement it. But if a product manager has to specify even the smallest detail，this slows down the team. The shortage of AI product managers exacerbates this problem. I see teams move much faster if GenAI Engineers also have some user empathy as well at basic skill at designing products，so that，given only high-level guidance on what to build（「a user interface that lets users see their profiles and change their passwords」），they can make a lot of decisions themselves and build at least a prototype to iterate from.

**额外加分项：产品技能**

在一些公司中，工程师被期望根据高度详细、像素级的产品设计图来编写代码以实现功能。但如果产品经理必须事无巨细地指定每一个细节，这无疑会拖慢整个团队的进度。AI 产品经理的稀缺使得这一问题更加突出。我发现，如果生成式 AI 工程师也具备一定的用户同理心和基本的产品设计技能，团队的效率会大大提高。这样一来，即使只给出高层次的指导（例如「一个让用户查看个人资料和更改密码的用户界面」），他们也能自主做出大量决策，并至少构建出一个可供迭代的原型。

When interviewing GenAI Application Engineers，I will usually ask about their mastery of AI building blocks and ability to use AI-assisted coding，and sometimes also their product/design instincts. One additional question I've found highly predictive of their skill is,「How do you keep up with the latest developments in AI?」Because AI is evolving so rapidly，someone with good strategies for keeping up — such as reading The Batch and taking short courses 😃，regular hands-on practice building projects，and having a community to talk to — really does stay ahead of the game much better than those who have less-effective strategies（such as if social media were their main source of info about AI，which typically does not provide the depth needed to keep up).

在面试生成式 AI 应用工程师时，我通常会考察他们对 AI 构建块的掌握程度、使用 AI 辅助编码的能力，有时还会考量他们的产品 / 设计直觉。我发现一个能有效预测他们技能的关键问题是：「你是如何跟进 AI 领域的最新进展的？」由于 AI 发展如此迅速，掌握有效策略的人 —— 例如阅读《The Batch》、参加短期课程、定期动手实践项目以及拥有一个可以交流的社区 —— 确实比那些策略效果不佳的人（例如将社交媒体作为获取 AI 信息的主要来源，这通常无法提供跟进所需的深度）更能保持领先地位。

Keep building!

Andrew

### News

#### More Consistent Characters and Styles

角色与风格更趋一致

Same character, new background, new action. That’s the focus of the latest text-to-image models from Germany’s Black Forest Labs.

角色与风格更趋一致让同一角色出现在不同背景和动作中，这是德国 Black Forest Labs 最新文本到图像模型关注的重点。

What’s new: The FLUX.1 Kontext family, which comes in versions dubbed max, pro, and dev, is trained to alter images in controlled ways. The company plans to release the weights for FLUX.1 Kontext dev but has not yet specified the licensing terms.

最新进展：FLUX.1 Kontext 系列模型，包括 max、pro 和 dev 三个版本，经过训练能够以可控方式修改图像。该公司计划发布 FLUX.1 Kontext dev 的模型权重，但尚未明确许可条款。

1 Input/output: text, image in; image out

输入 / 输出：文本、图像输入；图像输出

2 Architecture: Unspecified text encoders, convolutional neural network image encoder-decoder, transformer. FLUX.1 Kontext dev 12 billion parameters, other parameter counts undisclosed

架构：未指定的文本编码器，卷积神经网络（Convolutional Neural Network）图像编码器 - 解码器，Transformer。FLUX.1 Kontext dev 拥有 120 亿个参数，其他参数数量未公开。

3 Features: Character consistency, local and global alterations

特点：角色一致性，支持局部和全局修改。

4 Availability/price: FLUX.1 Kontext max and FLUX.1 Kontext pro available via FLUX Playground and various partners, $0.08 per image (FLUX.1 max) and $0.04 per image (FLUX.1 pro) via Fal, an image-generation platform.

可用性 / 价格：FLUX.1 Kontext max 和 FLUX.1 Kontext pro 可通过 FLUX Playground 及其合作伙伴获取。通过图像生成平台 Fal，FLUX.1 max 每张图片收费 0.08 美元，FLUX.1 pro 每张图片收费 0.04 美元。

5 Undisclosed: Parameter counts of FLUX.1 Kontext max and FLUX.1 Kontext pro, architecture of text encoders, training data, evaluation protocol, open-weights license

未公开信息：FLUX.1 Kontext max 和 FLUX.1 Kontext pro 的参数数量、文本编码器的架构、训练数据、评估协议以及模型权重开放许可。

How it works: The FLUX.1 Kontext models include encoders that embed input text and/or images, a transformer that processes them, and an image decoder that generates images. The current technical report doesn’t describe how it trained them for character consistency and image editing.

那么，FLUX.1 Kontext 模型究竟是如何工作的呢？它主要包含三个核心组件：首先是编码器，它能将输入的文本和 / 或图像「嵌入」（embed）到模型中；接着是一个 Transformer 模块，负责处理这些嵌入信息；最后是一个图像解码器，它能根据处理后的信息生成图像。不过，当前的技术报告并没有详细说明，微软是如何训练这些模型，以实现角色一致性和图像编辑功能的。

1 The team trained the convolutional neural network encoder-decoder to reproduce images and to fool a discriminator (architecture and training unspecified) into classifying them as real.

团队训练了一个卷积神经网络编码器 - 解码器，使其能够重现图像，并「骗过」一个判别器（其架构和训练细节未公开），让判别器误以为这些图像是真实的。

2 Having frozen the encoders, they trained the transformer — given a time step, embedding of a text prompt, embedding of a reference image, and noisy image embedding — to remove the noise over a series of steps.

在固定编码器后，他们开始训练 Transformer 模型：这个模型接收时间步、文本提示的嵌入（embedding）、参考图像的嵌入以及含噪声图像的嵌入作为输入，然后通过一系列步骤来去除图像中的噪声。

3 They further trained the transformer to encourage it to produce noise-free embeddings that a second discriminator would classify as representing real images. This process, a variant of adversarial diffusion distillation, helps reduce the number of steps needed to produce a good image embedding.

此外，他们还进一步训练了 Transformer，目的是让它生成的无噪声嵌入能被第二个判别器识别为真实的图像。这个过程是「对抗性扩散蒸馏（adversarial diffusion distillation）」的一种变体，它有助于减少生成高质量图像嵌入所需的步骤。

Results: The team compared the output of FLUX.1 Kontext models with that of five competing models including OpenAI GPT Image 1 (at three different quality levels) and Google Gemini 2.0 Flash native image generation. An undisclosed number of people evaluated the models according to a proprietary benchmark that highlights altering local and global aspects of an image, editing generated text within an image, maintaining consistent characters, and generating an image according to a reference style. The dataset included roughly 1,000 crowd-sourced pairs of text prompts and reference images.

结果：研究团队将 FLUX.1 Kontext 模型的输出与五款竞品模型进行了对比，这些模型包括 OpenAI GPT Image 1（在三个不同质量级别）以及 Google Gemini 2.0 Flash 原生图像生成功能。数量不明的评估人员依据一套专有基准对这些模型进行了评测。该基准重点考察了以下能力：修改图像的局部和全局细节、编辑图像中生成的文本、保持角色一致性，以及依据参考风格生成图像。数据集大约包含了 1,000 对通过众包方式收集的文本提示与参考图像。

1 FLUX.1 Kontext max and FLUX.1 Kontext pro outperformed all competing models.

FLUX.1 Kontext max 和 FLUX.1 Kontext pro 的表现优于所有竞争模型。

2 FLUX.1 dev outperformed all except other family members and GPT Image 1 set to high or medium quality.

FLUX.1 dev 的表现优于所有模型，仅次于同系列的其他成员以及设置为高质量或中等质量的 GPT Image 1。

Behind the news: Character consistency, also known as personalization, has come a long way since text-to-image generators became popular. In 2022, Textual Inversion showed how to learn an embedding of a character and use that embedding to produce further images. In 2023, DreamBooth showed how to get good results by fine-tuning a model on a few images of the character to be portrayed in a new situation. Since then, image-editing models have improved in quality and generality, including Meta Emu-Edit, OmniGen, and OpenAI gpt-image-1.

幕后故事：角色一致性，也称为个性化，自文本到图像生成器普及以来取得了长足进步。2022 年，Textual Inversion 展示了如何学习一个角色的嵌入（embedding），并利用该嵌入生成更多图像。2023 年，DreamBooth 则展示了通过对少量角色图像进行模型微调，就能在全新场景中高质量地描绘出这些角色。自那时起，图像编辑模型在质量和通用性方面都取得了显著提升，其中的代表包括 Meta Emu-Edit、OmniGen 和 OpenAI gpt-image-1。

Why it matters: Consistency and precise editing enable artists to craft stories around specific characters. Such models have become better at generating consistent details across images, but they remain finicky, sometimes changing minute details or entire characters and backgrounds. The more faithfully they help users express their ideas, the more firmly embedded in the creative toolkit they’ll become.

为什么这很重要：保持图像中的角色一致性以及精确编辑能力，让艺术家能够围绕特定角色创作引人入胜的故事。尽管这些模型在生成跨图像一致的细节方面表现越来越好，但它们仍有些「娇气」，有时会不经意地改变微小细节，甚至整个角色和背景。然而，它们越能忠实地帮助用户表达创意，就越能牢固地成为创意工具箱中不可或缺的一部分。

We’re thinking: Black Forest Labs announced plans to publish its proprietary benchmark. There’s a real need for common benchmarks to evaluate image generation, and we hope other developers will give it due consideration.

我们的看法：Black Forest Labs 宣布计划发布其专有基准。目前，图像生成领域确实迫切需要通用的评估基准，我们希望其他开发者能认真考虑并采纳。

#### AI Market Trends in Charts and Graphs

AI 市场趋势图表

Renowned investment analyst Mary Meeker is back with a report on the AI market, six years after publishing her last survey of the internet.

著名投资分析师 Mary Meeker 在发布上一次互联网调查报告六年之后，带着一份关于 AI 市场的新报告回归了。

What’s new: Meeker, co-founder of the venture capital firm Bond who formerly analyzed technology portfolios for Merrill Lynch, Salomon Brothers, and Morgan Stanley, published “Trends — Artificial Intelligence (May ‘25).” The report, which spans 340 graph-packed pages, revives and updates a series that chronicled the rise of the internet nearly every year from 1995 through 2019.

新动态：Mary Meeker，这位风险投资公司 Bond 的联合创始人（她曾为 Merrill Lynch、Salomon Brothers 和 Morgan Stanley 分析技术投资组合），发布了名为「趋势 —— 人工智能（25 年 5 月）」的报告。这份长达 340 页、图表密集的报告，重新启动并更新了她从 1995 年到 2019 年几乎每年记录互联网兴起历程的系列报告。

2『已下载原文「20250612Trends_Artificial_Intelligence」。（2025-06-13）』

How it works: The new report focuses on a handful of themes that arise from the unprecedented growth and capabilities of deep learning. As Meeker told Axios, AI is an arena for “intense competition the likes of which we’ve never seen before,” and that makes the present time “a period for lots of wealth creation and wealth destruction.”

运作方式：这份新报告聚焦于深度学习前所未有的增长和能力所带来的几个关键主题。正如 Meeker 接受 Axios 采访时所说，AI 是一个「我们前所未见的激烈竞争」的领域，这使得当前时期成为一个「大量财富创造和财富毁灭」并存的时代。

1 Rapid growth: Change in AI is happening faster than ever. Users of ChatGPT reached 1 million in 5 days — compared to the iPhone’s 74 days — and since then have rocketed to 800 million. Total capital expenditures of the six biggest technology companies (largely driven by AI) rose 63 percent to $212 billion between 2023 and 2024. Training datasets are growing 260 percent per year, processing power devoted to training is growing 360 percent per year, effective processing power is growing at 200 percent annually.

快速发展：人工智能（AI）的发展速度前所未有。ChatGPT 的用户仅用 5 天就突破了 100 万 —— 要知道 iPhone 达到这一数字用了 74 天 —— 此后更是飙升至 8 亿。六家最大的科技公司（其资本支出主要受 AI 驱动）的总资本支出在 2023 年至 2024 年间增长了 63%，达到了 2120 亿美元。此外，AI 训练数据集每年增长 260%，用于训练的处理能力每年增长 360%，而有效处理能力每年也以 200% 的速度增长。

2 Revenues and costs: The economics of this new world are not straightforward. On one hand, revenue is soaring at giants like Amazon, Google, and Nvidia as well as startups like Scale AI. On the other hand, the cost of computation is rising steadily even as the cost per token of output falls precipitously. Meanwhile, rapid turnover of models and proliferation of open-source alternatives are wild cards for AI-powered businesses.

收入与成本：这个由 AI 塑造的新世界，其经济规律并不那么简单。一方面，亚马逊（Amazon）、谷歌（Google）和英伟达（Nvidia）等科技巨头以及 Scale AI 等新兴公司的收入正一路飙升。另一方面，尽管每 Token 的输出成本在急剧下降，计算成本却在稳步上升。与此同时，模型快速迭代以及开源替代品的不断涌现，都为 AI 驱动的业务带来了诸多不确定性。

3 Rising performance: AI performance continues to increase. AI’s ability to complete the MMLU benchmark of language understanding outstripped human performance last year. This year, 73 percent of human testers classified responses generated by an LLM as human, according to one study. Synthetic images, video, and speech generation — all are increasingly capable of fooling human testers.

性能飞跃：AI 性能仍在持续提升。去年，AI 在语言理解的 MMLU 基准测试中超越了人类表现。而今年一项研究显示，73% 的人类测试者认为由大语言模型（LLM）生成的回复是人类写出来的。合成图像、视频和语音生成的能力也越来越强，足以以假乱真，骗过人类测试者。

4 Emerging capabilities: Today’s AI is capable of writing and editing, tutoring, brainstorming, automating repetitive work, and providing companionship. Within five years, it will generate code as well as humans, create films and games, operate humanlike robots, and drive scientific discovery. Meeker forecasts that within 10 years, AI will conduct scientific research, design advanced technologies, and build immersive digital worlds.

新兴能力：如今的 AI 已经能够胜任写作、编辑、辅导、头脑风暴、自动化重复性工作，甚至提供情感陪伴。未来五年内，AI 将能像人类一样编写代码，创作电影和游戏，操控类人机器人，并推动科学发现。Meeker 预测，十年内，AI 将能够独立进行科学研究、设计尖端技术，并构建身临其境的数字世界。

5 Workforce implications: Industries most likely to be affected by AI include knowledge work, content creation, legal services, software development, financial services, customer service, drug discovery, and manufacturing. Employers are adopting AI to get a boost in workforce productivity that Stanford researchers estimate is an average 14 percent. Companies like Box, Duolingo, and Shopify are adopting an AI-first orientation, while AI-related job titles have risen 200 percent in the past two years.

劳动力影响：知识工作、内容创作、法律服务、软件开发、金融服务、客户服务、药物发现和制造业等领域，是受 AI 影响最大的行业。雇主们正积极拥抱 AI，以提升劳动力生产力 —— 斯坦福（Stanford）研究人员估计，平均可提升 14%。Box、Duolingo 和 Shopify 等公司正全面转向「AI 优先」战略，而在过去两年里，与 AI 相关的职位名称数量增长了 200%。

6 AI gets physical: AI is having a profound impact on the physical world. Lyft’s and Uber’s market share fell around 15 percent while Waymo’s gained 27 percent over the past 18 months. AI-driven mineral exploration is boosting mine efficiency, and AI-powered agriculture is cutting the use of pesticides. And, sadly, AI-equipped attack drones are wreaking destruction upon Ukraine and elsewhere, even as they play a critical role in defense.

AI 走进物理世界：AI 正在对我们的物理世界产生深远的影响。过去 18 个月里，Lyft 和 Uber 的市场份额下降了约 15%，而 Waymo 的市场份额却增长了 27%，这凸显了自动驾驶技术的进步。AI 驱动的矿产勘探正显著提高矿山效率，AI 辅助的农业也在有效减少农药的使用。然而，令人遗憾的是，配备 AI 的攻击无人机正在乌克兰及其他地区肆虐，造成破坏，尽管它们在防御中也扮演着至关重要的角色。

Behind the news: Meeker published her first “Internet Trends” report in 1995, anticipating the coming online boom, and she issued new editions annually throughout the 2000s and much of the coming decade. Her final internet report arrived in 2019, the year after she founded Bond, when the report highlighted the rise of visual social media like Instagram, wearable technology, and digital payments.

新闻背景：Meeker 在 1995 年发布了她的第一份「互联网趋势」报告，预见了即将到来的在线繁荣。在整个 21 世纪 00 年代以及接下来的十多年里，她每年都会发布新版本。她的最后一份互联网报告于 2019 年发布，那一年正是她创立 Bond 的次年。该报告重点强调了 Instagram 等视觉社交媒体、可穿戴技术和数字支付的兴起。

Why it matters: “Trends — Artificial Intelligence” offers a wealth of market data culled from analyst reports, consumer surveys, and academic studies. The AI community has a number of excellent annual surveys, including Stanford’s AI Index and Air Street Capital’s State of AI. Meeker, who has been watching technology markets since the dawning of the web, adds another valuable perspective.

为何重要：这份名为「趋势 — 人工智能」的报告提供了大量市场数据，这些数据来源于分析师报告、消费者调查和学术研究。人工智能（AI）领域有许多优秀的年度调查，其中包括斯坦福大学的 AI Index 和 Air Street Capital 的 State of AI 报告。Meeker 自互联网诞生以来就一直在关注技术市场，她的报告无疑增添了一个宝贵的视角。

We’re thinking: One implication of the report: There has never been a better time to build software applications. For developers, it’s time to hone and update skills. For tech companies, it’s time to cast the net for talent. As Meeker said in her interview with Axios, “Companies that get the best developers often win.”

我们的思考：这份报告的一个重要启示是：现在是开发软件应用程序的最佳时机。对于开发者而言，是时候磨练和更新自身技能了；对于科技公司而言，则是时候广纳贤才了。正如 Meeker 在接受 Axios 采访时所说：「那些能吸引到最优秀开发者的公司，往往能赢得市场。」

#### Benchmarking Costs Climb

基准测试成本持续攀升

An independent AI test lab detailed the rising cost of benchmarking reasoning models.

一家独立的 AI 测试实验室详细阐述了推理模型进行基准测试时成本不断上升的现象。

What’s new: Artificial Analysis, an organization that tracks model performance and cost, revealed its budgets for evaluating a few recent models that improve their output by producing chains of thought, which use extra computation and thus boost the cost of inference. The expense is making it difficult for startups, academic labs, and other organizations that have limited resources to reproduce results reported by model developers, TechCrunch reported. (Disclosure: Andrew Ng is an investor in Artificial Analysis.)

最新进展：Artificial Analysis 是一家跟踪模型性能和成本的组织，它公布了评估一些最新模型所需的预算。这些模型通过生成「思维链」来优化输出，但这样做会增加额外的计算量，从而推高了推理成本。《TechCrunch》报道称，这笔高昂的费用使得初创公司、学术实验室以及其他资源有限的组织难以复现模型开发人员公布的结果。（披露：Andrew Ng 是 Artificial Analysis 的投资者。）

How it works: Artificial Analysis tested reasoning and non-reasoning models on popular benchmarks that gauge model performance in responding to queries that require specialized knowledge or multi-step reasoning, solving math problems, generating computer programs, and the like.

工作原理：Artificial Analysis 在常用的基准测试中对推理模型和非推理模型进行了测试。这些基准测试旨在衡量模型在响应需要专业知识或多步骤推理的查询、解决数学问题、生成计算机程序等方面的性能。

1 Running a group of seven popular benchmarks, OpenAI o1 (which produces chains of thought) produced more than 44 million tokens, while GPT-4o (which doesn’t take explicit reasoning steps) produced around 5.5 million tokens.

在七个常用的基准测试中，OpenAI 的 o1 模型（能够生成「思维链」[chains of thought]）产生了超过 4400 万个 Token，而 GPT-4o 模型（不采取明确的推理步骤）则产生了大约 550 万个 Token。

2 Benchmarking o1 cost $2,767, while benchmarking Anthropic Claude 3.7 Sonnet (which allows users to allocate a number of reasoning tokens per query; TechCrunch doesn’t provide the number in this case) cost $1,485. Smaller reasoning models are significantly less expensive: o3-mini (at high effort, which uses the highest number of reasoning tokens per query) cost $345, and o1-mini cost $141.

对 o1 模型进行基准测试的成本为 2767 美元。相比之下，对 Anthropic 的 Claude 3.7 Sonnet 模型进行基准测试的成本是 1485 美元（Claude 3.7 Sonnet 允许用户为每个查询分配一定数量的推理 Token，不过 TechCrunch 在此未提供具体数量）。值得注意的是，体积较小的推理模型成本显著更低：o3-mini 模型（在高计算量运行模式下，即每个查询使用最多的推理 Token）的成本是 345 美元，而 o1-mini 模型则仅需 141 美元。

3 Non-reasoning models are less expensive to test. Evaluating GPT-4o cost $109, Claude 3.5 Sonnet was $81.

针对非推理模型的测试成本相对更低。例如，评估 GPT-4o 的成本为 109 美元，而 Claude 3.5 Sonnet 的成本是 81 美元。

4 Artificial Analysis spent around $5,200 to test 12 reasoning models versus around $2,400 to test more than 80 non-reasoning models.

总体而言，Artificial Analysis 公司花费了大约 5200 美元来测试 12 个推理模型，而测试超过 80 个非推理模型则花费了大约 2400 美元。

Behind the news: Generally, the cost per token of using AI models has been falling even as their performance has been rising. However, two factors complicate that trend. (i) Reasoning models produce more tokens and thus cost more to run, and (ii) developers are charging higher per-token prices to use their latest models. For example, o1-pro and GPT-4.5 (a non-reasoning model), both released in early 2025, cost $600 per million output tokens, while Claude 3.5 Sonnet (released in July 2024) costs $15 per million tokens of output. Emerging techniques that allow users to allocate numbers of tokens to reasoning (whether “high” or “low” or a specific tally) also make benchmarking more costly and complicated.

新闻解读：通常，尽管 AI 模型的性能不断提升，但其每个 token 的使用成本却一直在下降。然而，有两个因素让这一趋势变得复杂起来。(i）推理模型会生成更多的 token，因此运行成本更高；(ii）开发者对其最新模型收取更高的每个 token 价格。例如，o1-pro 和 GPT-4.5（一个非推理模型）都于 2025 年初发布，它们的每百万输出 token 成本高达 600 美元，而 Claude 3.5 Sonnet（2024 年 7 月发布）每百万输出 token 仅需 15 美元。此外，新兴技术允许用户将 token 数量分配给推理任务（无论是「高」、「低」还是特定数量），这使得基准测试变得更加昂贵和复杂。

Why it matters: Benchmarks aren’t entirely sufficient for evaluating models, but they are a critical indicator of relative performance, and independent benchmarking helps to ensure that tests are run in a fair and consistent way. As the cost of benchmarking climbs, fewer labs are likely to confirm or challenge results obtained by the original developer, making it harder to compare models and recognize progress.

为何重要：虽然基准测试不足以全面评估模型，但它们是衡量相对性能的关键指标，独立的基准测试有助于确保测试过程公平一致。随着基准测试成本的攀升，更少的实验室会去验证或挑战原始开发者公布的结果，这使得模型间的比较和衡量技术进展变得更加困难。

We’re thinking: Verifying performance claims in independent, open, fair tests is essential to marking progress in general and choosing the right models for particular projects. It's time for the industry to support independent benchmarking organizations.

我们认为：在独立、开放和公平的测试中验证性能声明，对于整体技术进步以及为特定项目选择合适的模型至关重要。现在是时候让行业支持独立的基准测试组织了。

#### Better Video, Fewer Tokens

优化视频处理：用更少的 Token 实现更好效果

Researchers reduced the number of tokens needed to represent video frames to be fed to a transformer.

研究人员成功减少了输入给 Transformer 的视频帧所需的 token 数量。

What’s new: Jindong Jiang, Xiuyu Li, and collaborators at Nvidia, Rutgers University, UC Berkeley, Massachusetts Institute of Technology, Nanjing University, and Korea Advanced Institute of Science and Technology built STORM, a text-video system that performs well in tests of video understanding while processing fewer tokens.

最新进展：来自英伟达、罗格斯大学、加州大学伯克利分校、麻省理工学院、南京大学和韩国科学技术院的 Jindong Jiang、Xiuyu Li 及其合作者们，共同开发了 STORM 系统。这是一个文本 - 视频处理系统，它在视频理解测试中表现出色，同时处理的 token 数量更少。

Key insight: In a multimodal system, a large language model (LLM) that receives video tokens may struggle to process long videos. However, sequences of video frames often contain lots of redundancy, since few pixels may change from one frame to the next. Instead of forcing the LLM to process long sequences of redundant video tokens, mamba layers can enrich the token embeddings that represent one frame with information from other frames in the same clip. That way, the system can average token embeddings across frames without losing crucial information, making it possible to feed fewer tokens to the LLM without compromising performance.

核心洞察：在多模态系统中，接收视频 token 的大语言模型（LLM）在处理长视频时可能会遇到困难。然而，视频帧序列通常包含大量冗余信息，因为相邻帧之间变化的像素很少。与其强迫 LLM 处理冗余的视频 token 长序列，mamba 层可以通过整合同一视频片段中其他帧的信息，来丰富代表单个帧的 token 嵌入。这样一来，系统可以在不丢失关键信息的前提下，对跨帧的 token 嵌入进行平均处理，从而能够向 LLM 输入更少的 token，同时不影响性能。

How it works: The authors built STORM by training three components: (1) a pretrained SigLIP vision transformer, (2) untrained mamba layers, and (3) the pretrained large language model (LLM) from Qwen2-VL. They trained the system to predict the next token in image-text pairs and video-text pairs with 32-frame videos, and video-text pairs with 128-frame videos.

工作原理：研究人员通过训练三个组件构建了 STORM 系统：(1）一个预训练的 SigLIP 视觉 Transformer，(2）未经训练的 mamba 层，以及（3）来自 Qwen2-VL 的预训练大语言模型（LLM）。他们训练该系统来预测以下几种情况中的下一个 token：图像 - 文本对，包含 32 帧视频的视频 - 文本对，以及包含 128 帧视频的视频 - 文本对。

1 SigLIP learned to turn each video frame into 256 image tokens.

SigLIP 能够将每个视频帧转换为 256 个图像 Token（Token）。

2 Given a sequence of image tokens, mamba layers learned to process them in both directions – left-to-right and right-to-left – so each output token embedding encoded information from the entire video.

在处理图像 Token 序列时，Mamba 层（Mamba layer）会以双向方式（从左到右和从右到左）进行学习处理，从而确保每个输出 Token 嵌入（embedding）都包含了整个视频的信息。

3 The system averaged the token embeddings of 4 consecutive frames, reducing by a factor of 4 the number of tokens processed by Qwen2-VL’s LLM.

系统会对每 4 个连续帧的 Token 嵌入进行平均，这将 Qwen2-VL 大语言模型（LLM）需要处理的 Token 数量减少了四分之三。

4 Given the averaged token embeddings, Qwen2-VL LLM learned to predict the next word in the video’s associated text.

基于这些平均后的 Token 嵌入，Qwen2-VL 大语言模型会学习预测视频对应文本中的下一个词。

5 At inference, the system fed to the LLM the tokens that represented every second frame (a process the authors call temporal sampling), which further halved the input to the LLM.

在模型推理（Inference）阶段，系统会将代表「每隔一帧」的 Token 馈送给大语言模型（作者将这一过程称为时间采样（temporal sampling)），这进一步将大语言模型的输入数据量减少了一半。

Results: STORM outperformed proprietary and open models on measures of video understanding.

结果显示，STORM 在视频理解方面的表现超越了许多专有模型和开源模型。

1 On MVBench, which asks multiple-choice questions about actions, object interactions, and scene transitions in 16-second videos, STORM achieved 70.6 percent accuracy. That’s better than GPT-4o (64.6 percent accuracy) and Qwen2-VL (67.0 percent accuracy). A baseline system (STORM’s SigLIP and Qwen2-VL LLM without mamba layers, averaging image tokens, and temporal sampling) achieved 69.5 percent.

在 MVBench 基准测试中，STORM 取得了 70.6% 的准确率。MVBench 主要针对 16 秒的视频，提出关于其中动作、物体交互和场景转换的多项选择题。这一成绩优于 GPT-4o （64.6% 准确率）和 Qwen2-VL （67.0% 准确率）。作为对比，一个基线系统 （该系统由 STORM 的 SigLIP 和 Qwen2-VL 大语言模型 （LLM） 组成，且不包含 mamba 层、对图像 Token 进行平均处理并进行时间采样） 实现了 69.5% 的准确率。

2 On MLVU, which asks multiple-choice and open-ended questions about videos that range from 3 minutes to over 2 hours long, STORM reached 72.9 percent accuracy, topping GPT-4o (66.2 percent accuracy). The baseline model achieved 70.2 percent.

在 MLVU 基准测试中，STORM 的准确率达到了 72.9%，超越了 GPT-4o （66.2% 准确率）。MLVU 包含时长从 3 分钟到超过 2 小时不等的视频，并就这些视频提出多项选择题和开放性问题。而基线模型则取得了 70.2% 的准确率。

Why it matters: STORM compresses video at the input to the LLM, so the LLM processes 1/8 as many video tokens and uses 1/8 as much compute to process them. This enables the system to work more than 3 times faster than the baseline while performing better.

Why it matters：STORM 在将视频输入到大语言模型（LLM）之前就对其进行压缩，因此 LLM 处理的视频 Token 数量减少了七分之八，处理所需的计算量也随之减少了七分之八。这使得系统的运行速度比基线模型快了 3 倍以上，同时性能表现也更出色。

We’re thinking: Initial work on the mamba architecture positioned it as a replacement for the transformer, but this work, along with other projects, combines them to get the benefits of both.

We're thinking：最初关于 Mamba 架构的研究将其定位为 Transformer 架构的潜在替代品，但这项工作以及其他一些项目，却将这两种架构结合起来，从而充分发挥了两者的优势。