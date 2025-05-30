## 20250528Claude-4-Advances-Code-Gen-How-DeepSeek-Built-V3

[Claude 4 Advances Code Gen, How DeepSeek Built V3 For $5.6m, Google I/O Roundup, and more...](https://www.deeplearning.ai/the-batch/issue-303/)

Dear friends,

I am alarmed by the proposed cuts to U.S. funding for basic research，analyzed here，and the impact this would have for U.S. competitiveness in AI and other areas. Funding research that is openly shared benefits the whole world，but the nation it benefits most is the one where the research is done.

美国基础研究资金拟议削减（对此处进行了分析）令我深感担忧，以及这将对美国在人工智能和其他领域的竞争力产生的影响。那些开放共享的研究，其资金虽然惠及全世界，但从中受益最大的国家，正是开展这些研究的国家。

If not for funding for my early work in deep learning from the National Science Foundation（NSF)  and Defense Advanced Research Projects Agency（DARPA），which disburse much of U.S. research funding，I would not have discovered lessons about scaling that led me to pitch starting Google Brain to scale up deep learning. I am worried that cuts to funding for basic science will lead the U.S. — and also the world — to miss out on the next set of ideas.

如果不是美国国家科学基金会（NSF）和国防高级研究计划局（DARPA）为我在深度学习早期工作提供了资助（这两个机构负责分配美国大部分研究经费），我可能就不会在规模扩展方面有所发现，而正是这些发现促使我向 Google 提出启动 Google Brain 项目来大规模推进深度学习。我担心，基础科学研究经费的削减将导致美国乃至全世界错过下一波重要的思想。

In fact，such funding benefits the U.S. more than any other nation.  Scientific research brings the greatest benefit to the country where the work happens because（i）the new knowledge diffuses fastest within that country，and (ii）the process of doing research creates new talent for that nation.

事实上，这类资助对美国的好处远超其他任何国家。科学研究能为研究发生地所在国家带来最大的益处，原因在于：（i）新知识在该国传播最快，且（ii）研究过程能为该国培养新人才。

Why does most innovation in generative AI still happen in Silicon Valley? Because two teams based in this area — Google Brain，which invented the transformer network，and OpenAI，which scaled it up — did a lot of the early work. Subsequently，team members moved to other nearby businesses，started competitors，or worked with local universities. Further，local social networks rapidly diffused the knowledge through casual coffee meetings，local conferences，and even children's play dates，where parents of like-aged kids meet and discuss technical ideas. In this way，the knowledge spread faster within Silicon Valley than to other geographies.

为什么生成式 AI（Generative AI）的大部分创新仍然发生在硅谷？这是因为该地区有两个团队 —— 发明了 Transformer 网络的 Google Brain 和让这一技术得以大规模应用的 OpenAI —— 完成了大量的早期基础工作。随后，这些团队的成员有的去了附近的其他公司，有的创办了新的竞争对手，还有的与当地大学展开合作。此外，当地活跃的社交网络也起到了关键作用，通过随意的咖啡聊天、本地的技术会议，甚至是孩子们玩耍时家长之间的聚会，技术思想得以迅速传播。在这些聚会上，同龄孩子的父母们互相交流，讨论技术想法。通过这种方式，知识在硅谷内部的传播速度远超其他地区。

In a similar vein，research done in the U.S. diffuses to others in the U.S. much faster than to other geographic areas. This is particularly true when the research is openly shared through papers and/or open source：If researchers have permission to talk about an idea，they can share much more information，such as tips and tricks for how to really make an algorithm work，more quickly. It also lets others figure out faster who can answer their questions. Diffusion of knowledge created in academic environments is especially fast. Academia tends to be completely open，and students and professors，unlike employees of many companies，have full permission to talk about their work.

与此类似，在美国进行的研究成果在美国国内的传播速度，远快于传播到其他地区。当研究成果通过论文或开源的方式公开分享时，这一点尤其明显：如果研究人员获准讨论一个想法，他们就能更快地分享更多信息，比如如何让算法真正奏效的实用技巧。这也能帮助其他人更快地找到能解答他们问题的人。在学术环境中产生的知识传播得特别快。学术界通常是完全开放的，学生和教授与许多公司的员工不同，他们可以自由地讨论他们的工作。

Thus funding basic research in the U.S. benefits the U.S. most，and also benefits our allies. It is true that openness benefits our adversaries，too. But as a subcommittee of the U.S. House of Representatives committee on science，space，and technology points out, 「... open sharing of fundamental research is [not] without risk. Rather，... openness in research is so important to competitiveness and security that it warrants the risk that adversaries may benefit from scientific openness as well.」

所以，在美国资助基础研究对美国最有利，也对我们的盟友有利。确实，开放也会让我们的对手获益。但是，正如美国众议院科学、空间和技术委员会的一个小组委员会所指出的：「... 开放共享基础研究 [并非] 没有风险。相反，... 研究的开放性对于竞争力和安全至关重要，其重要性之高，足以让人冒着对手也可能从科学开放中受益的风险。」

Further，generative AI is evolving so rapidly that staying on the cutting edge is what's really critical. For example，the fact that many teams can now train a model with GPT-3.5- or even GPT-4-level capability does not seem to be hurting OpenAI much，which is busy growing its business by developing the cutting-edge o4，Codex，GPT-4.1，and so on. Those who invent a technology get to commercialize it first，and in a fast-moving world，the cutting-edge technology is what's most valuable. Studies like this one (albeit done while the internet was not as prevalent as it is today）also show how knowledge diffuses locally much faster than globally.

此外，生成式 AI（Generative AI）的发展日新月异，因此保持技术领先地位才是真正关键的。例如，尽管许多团队现在能够训练出与 GPT-3.5 甚至 GPT-4 级别能力相当的模型，但这似乎并未对 OpenAI 构成太大威胁。OpenAI 正通过持续开发更先进的技术，如 o4、Codex、GPT-4.1 等，不断壮大其业务。一项技术的发明者往往能率先将其商业化，在一个飞速发展的世界里，尖端技术才最具价值。类似这项研究 [20] 的发现 （尽管是在互联网尚未普及的年代进行的）也表明，知识在本地的传播速度远快于在全球范围内的传播。

China was decisively behind the U.S. in generative AI when ChatGPT was first launched in 2022. However，China's tech ecosystem is very open internally，and this has helped it to catch up over the past two years:

2022 年 ChatGPT 首次发布时，中国在生成式 AI（Generative AI）领域明显落后于美国。然而，中国内部开放的技术生态系统帮助其在过去两年里迎头赶上：

1 There is ample funding for open academic research in China.

中国为开放的学术研究提供了充足的资金。
 
2 China's businesses such as DeepSeek and Alibaba have released cutting-edge，open-weights models. This openness at the corporate level accelerates diffusion of knowledge.

中国的企业，例如 DeepSeek 和阿里巴巴，已经发布了前沿的开源模型。这种企业层面的开放加速了知识的传播。

3 China's labor laws make non-compete agreements（which stop an employee from jumping ship to a competitor）relatively hard to enforce，and the work culture supports significant idea sharing among employees of different companies; this has made circulation of ideas relatively efficient.

中国的劳动法使得竞业限制协议（阻止员工跳槽到竞争对手那里）相对难以执行，而且工作文化支持不同公司员工之间进行重要的思想交流；这使得思想的流通相对高效。

While there's also much about China that I would not seek to emulate，the openness of its tech ecosystem has helped it accelerate.

虽然中国的许多方面我不会寻求效仿，但其科技生态系统的开放性帮助它加速发展。

In 1945，Vannevar Bush's landmark report「Science，The Endless Frontier」 laid down key principles for public funding of U.S. research and talent development. Those principles enabled the U.S. to dominate scientific progress for decades. U.S. federal funding for science created numerous breakthroughs that have benefited the U.S. tremendously，and also the world，while training generations of domestic scientists，as well as immigrants who likewise benefit the U.S.

1945 年，Vannevar Bush 那份具有里程碑意义的报告《科学，无尽的前沿》为美国公共资助科研和人才培养奠定了关键原则。正是这些原则，让美国在随后的几十年里在科学进步方面占据了主导地位。美国联邦政府对科学的投入带来了无数突破，这些突破不仅极大地造福了美国本身，也造福了全世界，同时还培养了几代本土科学家，以及同样为美国做出贡献的移民。

The good news is that this playbook is now well known. I hope many more nations will imitate it and invest heavily in science and talent. And I hope that，having pioneered this very successful model，the U.S. will not pull back from it by enacting drastic cuts to funding scientific research.

好消息是，这套模式现在已广为人知。我希望更多国家效仿，大力投资科学和人才。我也希望，在开创了这一非常成功的模式之后，美国不会通过大幅削减科研经费来背离它。

Andrew

### News

#### Claude 4 Advances Code Generation

Claude 4 提升代码生成能力

Anthropic continued its tradition of building AI models that raise the bar in coding tasks.

Anthropic 公司延续了其构建在编码任务中不断提升标准的 AI 模型的传统。

What's new: Anthropic launched Claude 4 Sonnet 4 and Claude Opus 4，the latest medium- and largest-size members of its family of general-purpose large language models. Both models offer an optional reasoning mode and can use multiple tools in parallel while reasoning. In addition，the company made generally available Claude Code，a coding agent previously offered as a research preview，along with a Claude Code software development kit.

最新消息：Anthropic 推出了 Claude 4 Sonnet 4 和 Claude Opus 4，这是其通用大语言模型家族中最新的中等规模和最大规模的成员。这两个模型都提供了可选的推理模式，并且可以在推理时并行使用多种工具。此外，该公司还面向大众正式推出了 Claude Code，这是一个以前作为研究预览提供的编码智能体（coding agent），同时还发布了一个 Claude Code 软件开发工具包。

1 Input/output: Text，images，PDF files in（up to 200,000 tokens); text out（Claude Sonnet 4 up to 64,000 tokens，Claude Opus 4 up to 32,000 tokens)

输入 / 输出：支持文本、图片和 PDF 文件作为输入（最多 200,000 token）；输出为文本（Claude Sonnet 4 最多 64,000 token，Claude Opus 4 最多 32,000 token)

2 Features: Parallel tool use including computer use，selectable reasoning mode with visible reasoning tokens，multilingual（15 languages)

特点：支持并行使用工具，包括使用计算机；具备可选的推理模式，并且推理过程中的 token 可见；支持多语言（15 种语言)

3 Performance: Ranked Number One in LMSys WebDev Arena，state-of-the-art on SWE-bench and Terminal-bench

性能：在 LMSys WebDev Arena 排名第一，在 SWE-bench 和 Terminal-bench 上表现顶尖。

4 Availability/price: Anthropic API，Amazon Bedrock，Google Cloud Vertex AI. Claude Sonnet 4 $3/$15 per million input/output tokens, Claude Opus 4 $15/$75 per million input/output tokens

可用性 / 价格：可通过 Anthropic API、Amazon Bedrock 和 Google Cloud Vertex AI 获取。Claude Sonnet 4 的价格为每百万输入 token 3 美元，每百万输出 token 15 美元；Claude Opus 4 的价格为每百万输入 token 15 美元，每百万输出 token 75 美元。

5 Undisclosed: Parameter counts，specific training methods and datasets

未公开：参数数量、具体的训练方法和数据集

How it works: The team trained the Claude 4 models on a mix of publicly available information on the web as well as proprietary purchased data，data from Claude users who opted to share their inputs and outputs，and generated data. They fine-tuned the models to be helpful，honest，and harmless according to human and AI feedback.

它的工作原理是：Claude 4 模型是团队使用多种数据混合训练而成的，这些数据包括网络上公开的信息、购买的专有数据、选择分享输入和输出的 Claude 用户提供的数据以及生成的数据。为了让模型变得有用、诚实和无害，团队还根据人类和 AI 的反馈，对其进行了微调。

1 The models make reasoning tokens visible within limits. For especially lengthy chains of thought，an unspecified smaller model summarizes reasoning tokens.

这些模型在一定限度内允许用户查看推理 Token。对于特别长的思维链，会由一个未指定的小模型来总结推理 Token。

2 Given local file access，Claude Opus 4 can create and manipulate files to store information. For instance，prompted to maintain a knowledge base while playing a Pokémon video game，the model produced a guide to the game that offered advice such as,「If stuck，try OPPOSITE approach」and「Change Y-coordinate when horizontal movement fails.」

如果具备本地文件访问权限，Claude Opus 4 可以创建和操作文件来存储信息。例如，在玩 Pokémon 电子游戏时，如果提示它维护一个知识库，模型会生成一份游戏指南，提供诸如「如果卡住了，尝试相反的方法」和「当水平移动失败时改变 Y 坐标」之类的建议。

Results: Both Claude 4 models tied Google Gemini 2.5 Pro at the top of the LMSys WebDev Arena and achieved top marks for coding and agentic computer-use benchmarks in Anthropic's tests.

结果：两个 Claude 4 模型在 LMSys WebDev Arena 排名中与 Google Gemini 2.5 Pro 并列第一，并在 Anthropic 的测试中，在编码和 AI 智能体（AI Agent）计算机使用基准测试中获得最高分。

1 On SWE-bench Verified，which tests the model's ability to solve software issues from GitHub，Claude Opus 4 succeeded 72.5 percent of the time，and Claude Sonnet 4 succeeded 72.7 percent of the time. The next best model，OpenAI o3，succeeded 70.3 percent of the time.

在 SWE-bench Verified 这项旨在测试模型解决 GitHub 软件问题的能力上，Claude Opus 4 的成功率为 72.5%，Claude Sonnet 4 的成功率为 72.7%。紧随其后的是 OpenAI o3 模型，成功率为 70.3%。

2 Terminal-bench evaluates how well models work with the benchmark's built-in agentic framework to perform tasks on a computer terminal. Claude Opus 4 succeeded 39.2 percent of the time and Claude Sonnet 4 succeeded 33.5 percent of the time，whereas the closest competitor，OpenAI GPT 4.1，succeeded 30.3 percent of the time. Using Claude Code as the agentic framework，Claude Opus 4 succeeded 43.2 percent of the time and Claude Sonnet 4 succeeded 35.5 percent of the time.

Terminal-bench 评估了模型与该基准内置的 agentic 框架协作，在计算机终端上完成任务的表现。其中，Claude Opus 4 的成功率为 39.2%，Claude Sonnet 4 的成功率为 33.5%，而最接近的竞争对手 OpenAI GPT 4.1 的成功率为 30.3%。如果使用 Claude Code 作为 agentic 框架，Claude Opus 4 的成功率达到了 43.2%，而 Claude Sonnet 4 的成功率则为 35.5%。

Why it matters: The new models extend LLM technology with parallel tool use，using external files as a form of memory，and staying on-task over unusually long periods of time. Early users have reported many impressive projects，including a Tetris clone built in one shot and a seven-hour stint refactoring Rakutan's open-source code base.

重要意义在于：这些新模型扩展了大语言模型（LLM）的技术能力，它们可以并行使用多种工具，将外部文件作为一种记忆方式，并且能在相当长的时间内持续执行任务而不跑偏。早期用户已经分享了许多令人惊叹的项目成果，例如一次性就写成的俄罗斯方块游戏（Tetris clone），以及持续七小时重构 Rakutan 的开源代码库。

We're thinking: Prompting expert @elder_plinius published a text file that is purported to be Claude 4's system prompt and includes some material that does not appear in Anthropic's own publication of the prompts. It is instructive to see how it conditions the model for tool use，agentic behavior，and reasoning.

我们发现：Prompting 专家 @elder_plinius 发布了一个文本文件，里面据称是 Claude 4 的系统提示。这个文件中包含了一些 Anthropic 官方公布的提示里没有的内容。看看这个系统提示是如何训练模型进行工具使用、AI 智能体行为和推理的，这很有启发性。

[CL4R1T4S/ANTHROPIC/Claude\_4.txt at main · elder-plinius/CL4R1T4S](https://github.com/elder-plinius/CL4R1T4S/blob/main/ANTHROPIC/Claude_4.txt?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9f91ZK_N_NmLMp6AX94ZoLdUVc_XficAkAPC9Kou3250osRmbIYRHjy_zrS2Kxg7NGmN-f)

#### Google I/O Overdrive

Google I/O 加速进展

Google revamped its roster of models，closed and open，and added more AI-powered features to its existing products.

Google 对其模型系列进行了全面升级，无论是内部封闭模型还是开源模型，并且在现有产品中加入了更多由 AI 提供支持的功能。

What's new: Google staged a parade of announcements at this year's I/O developer conference. New offerings include improvements to Gemini 2.5 Pro and Gemini 2.5 Flash and a preview of Gemma 3n (all three generally available in June), the updated Veo 3 video generator（available via Flow，Google's AI videography app，for paid subscribers to its AI Pro and Ultra services），and increasingly AI-powered search.

新进展：Google 在今年的 I/O 开发者大会上发布了一系列重磅消息。新的产品包括升级版的 Gemini 2.5 Pro 和 Gemini 2.5 Flash，以及 Gemma 3n 的预览版 （这三个产品预计都将在 6 月份全面上线）。此外，还有更新后的 Veo 3 视频生成器 （这款工具将通过 Google 的 AI 视频应用 Flow，向其 AI Pro 和 Ultra 服务的付费用户提供），以及更加强大的 AI 驱动的搜索功能。

How it works: The I/O offerings spanned from public-facing products to developer tools.

工作原理：这些输入 / 输出能力涵盖了面向公众的产品和开发者工具。

1 Google updated Gemini 2.5 Pro and the speedier Gemini 2.5 Flash with audio output，so both models now take in text，audio，images，and video and produce text and audio. In addition，they offer summaries of tokens produced while reasoning. Gemini-2.5-Pro-Preview-05-06，which topped the LMSys Text Arena and WebDev Arena (tied with Claude 4 Opus and Sonnet），lets users set a reasoning budget up to 128,000 tokens，enabling it to outperform OpenAI o3 and o4-mini（set to high effort）on math，coding，and multimodal benchmarks in Google's tests. Gemini-2.5-Flash-Preview-05-20 uses 22 percent fewer tokens than its predecessor while ranking near the top of the LMSys Text Arena and WebDev Arena.

Google 更新了 Gemini 2.5 Pro 和速度更快的 Gemini 2.5 Flash，增加了音频输出功能，因此这两种模型现在都可以接收文本、音频、图像和视频作为输入，并输出文本和音频。此外，它们还提供在推理过程中生成的 token 的摘要。Gemini-2.5-Pro-Preview-05-06 在 LMSys Text Arena 和 WebDev Arena 中名列前茅（与 Claude 4 Opus 和 Sonnet 并列），允许用户设置高达 128,000 个 token 的推理预算，这使得它在 Google 的测试中，在数学、编码和多模态基准测试上优于 OpenAI o3 和 o4-mini （在「高努力」设置下）。Gemini-2.5-Flash-Preview-05-20 使用的 token 比其前身少 22%，同时在 LMSys Text Arena 和 WebDev Arena 中也名列前茅。

2 The Veo 3 text-to-video generator produces 3840x2160-pixel video with audio（dialogue，sound effects，and music）with creative controls including the ability to add and remove objects and maintain consistent characters. It bested Kuaishu Kling 2.0，Runway Gen 3，and OpenAI Sora in Google's comparisons.

Veo 3 文本到视频生成器能够生成分辨率为 3840x2160 像素、并带有音频（包含对话、音效和音乐）的视频。它还提供了创意控制功能，比如添加和删除对象，以及保持角色的一致性。在 Google 的对比测试中，Veo 3 的表现优于快手可灵 2.0、Runway Gen 3 和 OpenAI Sora。

3 New members of Google's Gemma 3 family of open-weights models，Gemma 3n 5B and 8B，are multilingual（over 140 languages），multimodal（text，vision，audio in; text out），and optimized for mobile platforms. Gemma-3n-E4B-it（8 billion parameters）ranks just ahead of Anthropic Claude 3.7 Sonnet in the LMSys Text Arena. Gemma 3n 5B and 8B are 1.5 times faster than their predecessors and require 2 gigabytes and 3 gigabytes of memory，respectively，thanks to techniques that include per-layer embeddings，key-value caching，conditional parameter loading (constraining active parameters to specific modalities at inference），and a Matryoshka Transformer design that dynamically activates nested sub-models. They're available in preview via Google's AI Studio，AI Edge，GenAI SDK，or MediaPipe.

Google 开源模型 Gemma 3 系列的新成员 Gemma 3n 5B 和 8B 现已推出。它们具备多语言能力 （支持超过 140 种语言）和多模态能力 （可以输入文本、图像、音频，并输出文本），并且专门针对移动平台进行了优化。其中，拥有 80 亿参数的 Gemma-3n-E4B-it 在 LMSys Text Arena 的表现略微领先于 Anthropic Claude 3.7 Sonnet。得益于逐层嵌入 （per-layer embeddings）、键值缓存 （key-value caching）、条件参数加载 （conditional parameter loading，在推理时将活动参数限制在特定模态），以及能够动态激活嵌套子模型的 Matryoshka Transformer 设计等技术，Gemma 3n 5B 和 8B 的速度比它们的前代模型快 1.5 倍，并且分别只需要 2GB 和 3GB 的内存。目前，用户可以通过 Google 的 AI Studio、AI Edge、GenAI SDK 或 MediaPipe 获取这些模型的预览版。

4 Google introduced several specialized AI tools and models. Jules is an autonomous，asynchronous，multi-agent coding assistant that clones repos into a secure virtual machine to perform tasks like writing tests，building features，and fixing bugs（available in public beta). SignGemma translates American sign language to text（previously ASL to English). MedGemma analyzes medical text and images（part of the open-weights collection Health AI Developer Foundations).

Google 推出了一些专门的 AI 工具和模型。Jules 是一款自主（autonomous）、异步（asynchronous）、多智能体（multi-agent）的编码助手。它可以将代码仓库（repos）克隆到安全的虚拟机中，执行编写测试、构建新功能和修复 bug 等任务 （目前已提供公开测试版）。SignGemma 可以将美国手语翻译成文本 （之前只能翻译成英文）。MedGemma 则用于分析医学文本和图像 （它是开放权重集合 Health AI Developer Foundations 项目的一部分）。

5 Building on Google Search's AI Overviews，Google is further building AI into search. Google Search's AI Mode uses Gemini 2.5 to deliver a「deep search」mode that decomposes users' questions into hundreds of sub-queries for analysis and visualization. Google plans to integrate AI Mode features into its core search product. In addition，Google Search's AI Mode will gain Search Live (real-time，audio-enabled visual interaction via camera）and agentic features (for tasks such as purchasing tickets). Computer-use capabilities are coming to the Gemini API and Vertex AI.

在 Google Search 的 AI Overviews 基础上，Google 正在进一步将 AI 融入到搜索功能中。Google Search 的 AI Mode 使用 Gemini 2.5 提供一种「深度搜索」模式，它将用户的问询分解为数百个子问询进行分析和可视化。Google 计划将其 AI Mode 功能集成到其核心搜索产品中。此外，Google Search 的 AI Mode 将获得 Search Live （通过摄像头进行实时、启用音频的视觉交互）和 agentic features （用于购买门票等任务）。计算机使用能力将开放给 Gemini API 和 Vertex AI。

Why it matters: Google is catching up with the Microsoft/OpenAI colossus on several fronts. The addition of audio output to Gemini and Gemma models fuels the rise of voice-to-voice and other audio applications and gives developers powerful new tools to build them. At the same time，Veo 3's text-to-video-plus-audio output shows marked improvement over the previous version.

为何重要：Google 正在多个方面追赶 Microsoft/OpenAI 这家科技巨头。为 Gemini 和 Gemma 模型增加音频输出功能，正在推动语音转语音（voice-to-voice）和其他音频应用程序的兴起，并为开发者提供了构建这些应用的强大新工具。与此同时，Veo 3 的文本到视频加音频输出（text-to-video-plus-audio output）功能，相比之前版本也展现出显著的提升。

Behind the news: The number of tokens Google processed monthly has surged this year from 9.7 trillion last year to 480 trillion，a sign that its AI APIs and AI-infused products are rapidly gaining traction. Google's progress contrasts with Apple's ongoing struggles. Both share advantages in smartphones and app distribution. But，while Google has showcased a string of advanced models as well as early efforts to integrate them into legacy products，Apple's organizational challenges have hampered its AI development. Now Apple must contend with OpenAI's acquisition of LoveFrom，the startup founded by its former lead product designer Jony Ive.

新闻背后蕴含着一个重要的趋势：Google 每月处理的 token（Token）数量在今年出现了爆炸式增长，从去年的 9.7 万亿猛增至 480 万亿。这强有力地表明，Google 的 AI APIs（应用程序接口）和集成 AI 功能的产品正在迅速获得市场认可。Google 在 AI 领域的突飞猛进与 Apple 目前面临的持续困境形成了鲜明对比。尽管两家公司在智能手机和应用分发领域都拥有共同的优势，但情况却大相径庭：Google 不仅展示了一系列先进的 AI 模型，并已着手将其融入现有的传统产品，而 Apple 的组织架构问题却严重阻碍了其在 AI 领域的研发步伐。如今，Apple 更不得不面对来自 OpenAI 的新挑战 —— OpenAI 收购了由 Apple 前首席产品设计师 Jony Ive 创立的初创公司 LoveFrom。

We're thinking: Google I/O 2025 was a strong showing of generative AI capabilities! There's still work to be done to translate these innovations into compelling products，but the company now has a strong base for building numerous innovative products.

我们认为：Google I/O 2025 充分展示了生成式 AI（Generative AI）的强大能力！虽然将这些创新转化为引人注目的产品仍需努力，但 Google 现在已为构建众多创新产品奠定了坚实的基础。

#### How DeepSeek Did It

DeepSeek 是如何做到的

DeepSeek made headlines late last year, when it built a state-of-the-art，open-weights large language model at a cost far lower than usual. The upstart developer shared new details about its method.

DeepSeek 在去年年底引起了广泛关注，当时它以远低于通常的成本，构建了一个最先进的开放权重（open-weights）大语言模型（LLM）。这家新兴公司分享了关于其方法的最新细节。

What's new: Chenggang Zhao and colleagues at DeepSeek described software and hardware choices that reduced memory and processing requirements while building their groundbreaking mixture-of-experts models DeepSeek-R1 and DeepSeek-V3.

最新动态：DeepSeek 公司的 Chenggang Zhao 及其同事们介绍了他们在构建具有突破性的混合专家模型 DeepSeek-R1 和 DeepSeek-V3 时，如何在软件和硬件层面进行优化，从而显著降低了模型的内存占用和计算需求。

Mixture of experts（MoE）basics: The MoE architecture uses different subsets of a model's parameters to process different inputs. Each MoE layer contains a group of neural networks，or experts，preceded by a routing module that learns to choose which one(s）to use based on the training example. In this way，different experts learn to specialize in different types of input.

混合专家模型（MoE）基础：MoE 架构利用模型参数的不同子集来处理不同的输入。每个 MoE 层都含有一组神经网络，即「专家」，并在其前面设有一个路由模块。这个路由模块会根据训练样本学习选择使用哪些专家。通过这种方式，不同的专家能够学习并专注于处理不同类型的输入。

How it works: The authors trained DeepSeek-R1 and DeepSeek-V3 using a cluster of 2,048 Nvidia H800 GPUs composed of nodes that contained 8 GPUs each. MoE requires less memory than dense architectures，since a given input activates only a portion of a model's parameters. This enabled the authors to train DeepSeek-V3 on 250 GFLOPs per token，while Qwen 2.5 72B required 394 GFLOPs per token and Llama 3.1 405B required 2,448 GFLOPs per token.

工作原理：作者利用包含 2,048 块 Nvidia H800 GPU 的集群训练了 DeepSeek-R1 和 DeepSeek-V3，这个集群的每个计算节点都配备了 8 块 GPU。由于给定输入只会激活模型参数的一小部分，混合专家模型（MoE）架构比传统的密集（dense）架构需要更少的内存。这使得作者在训练 DeepSeek-V3 时，每处理一个 token 只需要 250 GFLOPs 的计算量。相比之下，Qwen 2.5 72B 模型需要 394 GFLOPs/token，而 Llama 3.1 405B 模型更是高达 2,448 GFLOPs/token。

1 The authors built a mixed-precision training algorithm to reduce the memory requirements of training MoE models. They used FP8（8-bit）numbers to perform computations including linear transformations and 16- or 32-bit precision to perform others such as computing embeddings.（They say DeepSeek-V3 was the first open LLM to have been trained using FP8.)

作者构建了一种混合精度训练算法，旨在减少训练 MoE 模型的内存需求。具体来说，他们使用 FP8（8 位）数字执行包括线性变换在内的计算，而使用 16 位或 32 位精度执行计算嵌入等其他操作。（值得一提的是，作者提到 DeepSeek-V3 是第一个使用 FP8 训练的开源大语言模型。）

2 The authors noticed that communication between GPUs inside a node was four times faster than communication between nodes. To ensure fast communication when routing tokens to experts，they limited the algorithm to process them within up to 4 nodes.

作者注意到，节点内部 GPU 之间的通信比节点之间的通信快四倍。为了确保将 Token 路由到专家时实现快速通信，他们将算法限制为最多在 4 个节点内处理这些 Token 的路由。

3 To utilize GPUs more fully，they divided each GPU's input data so the chip processes computation and communication at the same time. Specifically，the chip computes attention or MoE layers on one part of the data and simultaneously sends the other part of the data to other GPUs or aggregates it from other GPUs as necessary.

为了更充分地利用 GPU，他们对每个 GPU 的输入数据进行了划分，这样芯片就可以同时进行计算和通信。具体来说，芯片会在一部分数据上计算注意力层（attention）或 MoE 层（MoE layers），同时将另一部分数据发送给其他 GPU，或者根据需要从其他 GPU 汇总数据。

4 To further save inference memory，the models use multi-head latent attention，which saves memory during execution relative to other variants of attention. The authors compared their implementation to the variant GQA used in Qwen 2.5 72B and Llama 3.1 405B. Their method（70 kilobytes per token）used far less memory than Qwen-2.5（328 kilobytes per token）or Llama 3.1（516 kilobytes per token).

为了进一步节省推理内存，模型采用了多头潜在注意力（multi-head latent attention），这种机制在执行过程中比其他注意力变体更节省内存。作者将他们的实现与 Qwen 2.5 72B 和 Llama 3.1 405B 中使用的 GQA 变体进行了比较。结果显示，他们的方法（每 token 70 千字节）比 Qwen-2.5（每 token 328 千字节）或 Llama 3.1（每 token 516 千字节）使用的内存少得多。

Behind the news: DeepSeek-V3 made waves when it was released in December. It performed better than Llama 3.1 405B，the leading LLM at the time，but its training cost was an astonishing $5.6 million，compared to the usual tens to hundreds of millions of dollars. Some observers were skeptical of the reported cost，pointing out that the $5.6 million dollar figure doesn't include salaries，data acquisition and annotation，processing failed training runs，and other research and development costs. In addition，the cost of training DeepSeek-R1 remains unknown.

新闻聚焦：DeepSeek-V3 在去年十二月发布时引发了广泛关注。这款大语言模型的性能超越了当时的佼佼者 Llama 3.1 405B，但令人惊讶的是，其训练成本仅为 560 万美元，远低于通常数千万甚至数亿美元的训练费用。然而，一些观察人士对这一报告的成本持怀疑态度，他们指出，这 560 万美元的数字并未包含工资、数据获取与标注、处理训练失败的开销，以及其他研发成本。此外，DeepSeek-R1 的训练成本至今仍未公开。

Why it matters: Traditionally，only companies with large budgets and vast resources could afford to train state-of-the-art models. DeepSeek changed that but didn't explain how when it released its models. By sharing the details，the company has empowered a wider range of teams to improve the state of the art.

Why it matters：传统上，只有拥有巨额预算和海量资源的公司才能负担得起训练最先进模型的费用。DeepSeek 改变了这种状况，但发布模型时并未解释具体是如何做到的。通过分享细节，DeepSeek 已赋能更广泛的团队提升技术水平。

We're thinking: Shortly after DeepSeek-R1 was released，some engineers claimed — without presenting evidence — that DeepSeek had copied their work. DeepSeek's disclosure of its training methods should lay to rest any remaining questions about this. Its work was truly innovative，and we applaud its release of key technical details.

我们认为：在 DeepSeek-R1 发布后不久，一些工程师在没有提供证据的情况下声称 DeepSeek 复制了他们的工作。DeepSeek 公布其训练方法应该能够完全消除对此事的任何质疑。DeepSeek 的工作确实具有创新性，我们非常赞赏它公开发布了关键的技术细节。

#### Did GPT-4o Train on O'Reilly Books?

GPT-4o 是否使用了 O'Reilly 的书籍进行训练？

A study co-authored by tech-manual publisher Tim O'Reilly shows that OpenAI trained GPT-4o on parts of his company's books that were not made freely available.

由技术手册出版商 Tim O'Reilly 共同撰写的一项研究表明，OpenAI 在训练 GPT-4o 时使用了他公司书籍中并未免费开放的部分内容。

What happened: O'Reilly，computer scientist Sruly Rosenblat，and economist Ilan Strauss found that GPT-4o was able to identify verbatim excerpts from dozens of O'Reilly Media books that the company kept behind a paywall，indicating that the books likely were included in the model's training data.

发生了什么：O'Reilly，计算机科学家 Sruly Rosenblat 和经济学家 Ilan Strauss 发现 GPT-4o 能够识别出 O'Reilly Media 公司付费墙后数十本图书中的逐字摘录，表明这些图书很可能被纳入了模型的训练数据中。

How it works: The researchers adapted the DE-COP method to compare how well GPT-4o，GPT-4o-mini，and GPT-3.5 Turbo recognized paywalled excerpts versus freely available excerpts from the same books.

工作原理：研究人员调整了 DE-COP 方法，目的是比较 GPT-4o、GPT-4o-mini 和 GPT-3.5 Turbo 模型识别同一本书中付费摘录和免费摘录的能力。

1 The team selected 34 O'Reilly Media books and divided them into roughly 14,000 paragraphs.

该团队选择了 34 本 O'Reilly Media 的书籍，并将它们分成大约 14,000 个段落。

2 They labeled the paragraphs private（paywalled）or public（when O'Reilly Media publishes a book，it distributes freely on the web chapters 1 and 4 as well as the first 1,500 characters of other chapters). They also labeled the paragraphs according to whether they were published before or after the models' knowledge cutoff dates.

他们将这些段落标记为私有（需要付费）或公共（当 O'Reilly Media 出版一本书时，他们会在网上免费发布第 1 章、第 4 章以及其他章节的前 1,500 个字符）。他们还根据这些段落是在模型知识截止日期之前还是之后发布的进行标记。

3 The team built multiple-choice quizzes，each composed of a verbatim paragraph and three paraphrased versions generated by Claude 3.5 Sonnet. The researchers ordered the paragraphs and paraphrases in all permutations to eliminate potential position bias.

该团队设计了多项选择题测验，每个测验包含一个原文段落和 Claude 3.5 Sonnet 生成的三个转述版本。研究人员将段落和转述以所有可能的排列组合进行排序，以消除潜在的位置偏差。

Results: The authors asked each model to identify the verbatim paragraph and calculated each model's percentage of correct responses. Then they averaged each model's accuracy per book and converted the averages into AUROC scores that measure how well a model distinguished books available prior to its knowledge cutoff（potentially included in the training set）from those that weren't available at the time. 50 percent AUROC indicates random chance，while higher scores indicate higher accuracy.

结果：作者要求每个模型识别逐字段落（verbatim paragraph），并计算每个模型的正确率。然后他们对每个模型在每本书上的准确率进行了平均，并将这些平均值转换成 AUROC 分数。AUROC 分数衡量的是模型区分其知识截止日期前可用的书籍（可能包含在训练集中）和当时不可用的书籍的能力。AUROC 分数为 50% 表示随机水平，而更高的分数表示更高的准确率。

1 GPT-4o tended to recognize O'Reilly Media content whether or not it was public，but it recognized private paragraphs（82 percent AUROC）markedly more often than public paragraphs（64 percent AUROC).

GPT-4o 倾向于识别 O'Reilly Media 的内容，无论内容是否公开。不过，它识别私有段落（AUC 为 82%）的频率显著高于识别公共段落（AUC 为 64%）。

2 GPT-4o-mini's performance was nearly random for both private（56% AUROC）and public material（55% AUROC). The researchers hypothesize that either（i）the model's smaller size may limit its ability to memorize or（2）OpenAI may reserve premium data to train larger models.

GPT-4o-mini 在处理私有内容（AUROC 为 56%）和公共内容（AUROC 为 55%）时的表现接近于随机猜测。研究人员推测，这可能是因为（i）模型尺寸较小限制了其记忆能力，或者（2）OpenAI 将优质数据预留给了训练更大的模型。

3 The earlier GPT-3.5 Turbo recognized public paragraphs（64% AUROC）more often than private paragraphs（54% AUROC），which suggests that it was trained predominantly on freely available data.

较早版本的 GPT-3.5 Turbo 在识别公共段落（64% AUROC）方面的表现优于识别私人段落（54% AUROC），这表明它主要是在公开可用的数据上进行训练的。

Yes，but: Newer large language models are better at distinguishing human-written from generated text，even if it wasn't in their training sets. For instance，given paragraphs that were published after their knowledge cutoffs，GPT-4o returned scores as high as 78 percent AUROC. The authors note that this may challenge their conclusions，since they interpret high scores to indicate that a model saw the text during training. Nonetheless，they argue that their approach will remain valid while scores for both text that was included and text that was excluded from training sets remain under 96 percent AUROC.「For now,」they write,「the gap remains sufficiently large to reliably separate the two categories.」

是的，但是：较新的大语言模型（Large Language Model）更擅长区分人类撰写的文本和生成的文本，即使这些文本不在其训练集中。例如，对于在其知识截止日期后发布的段落，GPT-4o 达到了 78% 的 AUROC 分数。作者指出，这可能会挑战他们的结论，因为他们认为高分表明模型在训练期间接触过这些文本。尽管如此，他们认为，只要训练集中包含和排除的文本分数都保持在 96% AUROC 以下，他们的方法就仍然有效。他们写道，「目前，差距仍然足够大，可以可靠地区分这两类。」

Behind the news: Historically AI developers have trained machine learning models on any data they could acquire. But in the era of generative AI，models trained on copyrighted works can mimic the works and styles of the works' owners，creating a threat to their livelihoods. Some AI developers have responded by regarding data that's freely available on the web as fair game，and material that's otherwise protected as off-limits for training. However，datasets that include ostensibly private data are widely circulated，including LibGen，which includes all 34 of the O'Reilly Media titles tested in this study. Moreover，unauthorized copies of many copyrighted works are posted without paywalls or even logins，making it possible even for web scrapers that crawl only the open web to download them. Google and OpenAI，which is currently embroiled in lawsuits by authors and publishers who claim it violated copyrights by training models on copyrighted works，recently lobbied the United States government to relax copyright laws for AI developers.

新闻背景：过去，人工智能（AI）开发者习惯于利用能获得的任何数据来训练机器学习模型。然而，在生成式 AI（Generative AI）时代，如果在受版权保护的作品上训练模型，这些模型可能会模仿这些作品及其拥有者（比如作者）的风格，从而对他们的生计构成威胁。对此，一些 AI 开发者认为，网上免费可用的数据可以「合理使用」，而其他受保护的材料则不应用于训练。但现实情况是，包含看似私密数据的数据集却被广泛传播，比如 LibGen 就包含了本研究中测试的全部 34 本 O'Reilly Media 出版的书籍 [20]。更甚者，许多受版权保护的作品未经授权就被发布到网上，没有付费墙，甚至无需登录就能获取，这使得即使是只抓取开放网络的网络爬虫也能轻松下载它们。Google 和 OpenAI（后者目前正面临作者和出版商提起的诉讼，他们声称 OpenAI 通过在受版权保护的作品上训练模型侵犯了版权）最近都在游说美国政府，希望能为 AI 开发者放宽版权法规。

Why it matters: The AI industry requires huge quantities of high-quality data to keep advancing the state of the art. At the same time，copyright owners are worried that models trained on their data might hamper their opportunities to earn a living. AI developers must find fair ways to respond. As O'Reilly points out，exploiting copyrighted works instead of rewarding their authors could lead to an「extractive dead end」that ultimately diminishes the supply of the high-quality training data.

为什么重要：人工智能（AI）行业需要海量高质量数据，才能不断推动技术向前发展。与此同时，版权所有者担心，如果 AI 模型使用他们的数据进行训练，可能会影响他们赖以谋生的机会。因此，AI 开发者必须找到公平的应对之道。正如 O'Reilly 所言，如果 AI 行业只是利用受版权保护的作品，却不回馈其创作者，这可能会导致一种「掠夺式枯竭」的局面，最终减少高质量训练数据的来源。

We're thinking: We have learned a great deal from O'Reilly Media's books，and we're grateful to the many authors，editors，graphic artists，and others who produce them. Meanwhile，it's time for the U.S. Congress —  and legislators internationally — to update copyright laws for the era of generative AI，so everyone knows the rules and we can find ways to follow them.

我们想表达的是：我们从 O'Reilly Media 的书籍中受益匪浅，非常感谢为此付出努力的众多作者、编辑、平面设计师以及其他工作人员。与此同时，美国国会和国际上的立法者们是时候修订针对生成式 AI（Generative AI）时代的版权法了，这样大家都能清楚地了解相关规定，并找到遵守这些规定的途径。