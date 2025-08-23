## 20250820China-Questions-Nvidia-When-Models-Memorize

[China Questions Nvidia, When Models Memorize, Mixture of Video Experts, OpenAI & Oracle Join Forces](https://www.deeplearning.ai/the-batch/issue-315/)

Dear friends,

亲爱的读者们，

On Saturday at the Buildathon hosted by AI Fund and DeepLearning.AI, over 100 developers competed to build software products quickly using AI assisted coding. I was inspired to see developers build functional products in just 1-2 hours. The best practices for rapid engineering are changing quickly along with the tools, and I loved the hallway conversations sharing tips with other developers on using AI to code!

上周六，由 AI Fund 和 DeepLearning.AI 联合举办了一场名为 Buildathon 的编程马拉松活动，吸引了 100 多名开发者。他们利用 AI 辅助编码技术，竞相快速构建软件产品。看到开发者们能在短短 1-2 小时内就做出具备完整功能的产品，我深受启发。如今，快速工程（rapid engineering）的最佳实践正随着工具的迭代而迅速演变。我尤其喜欢在活动走廊里与大家交流，分享如何利用 AI 编程的心得！

The competitors raced to fulfill product specs like this one (you can see the full list here):

各家竞争者都在争分夺秒地实现类似这样的产品规格（你可以在这里查看完整清单）：

Project: Codebase Time Machine

项目：代码库时间机器（Codebase Time Machine）

Description: Navigate any codebase through time, understanding evolution of features and architectural decisions.

描述：能够穿越时间探索任何代码库，深入理解各项功能的演变过程和架构决策。

Requirements:

要求:

1 Clone repo and analyze full git history

克隆代码库，并分析其完整的 Git 历史记录

2 Build semantic understanding of code changes over time

深入理解代码随时间演进所产生的语义变化

3 Answer questions like "Why was this pattern introduced?" or "Show me how auth evolved"

回答类似「为什么引入了这个模式？」或「认证是如何演变的？」这样的问题

4 Visualize code ownership and complexity trends

将代码所有权和复杂性趋势进行可视化呈现

5 Link commits to business features/decisions

将提交关联到业务功能 / 决策

Teams had 6½ hours to build 5 products. And many of them managed to do exactly that! They created fully functional applications with good UIs and sometimes embellishments.

各团队有 6.5 小时来开发 5 款产品。令人惊喜的是，许多团队都成功完成了任务！他们不仅创建了功能完善、用户界面（UI）美观的应用程序，有些甚至还加入了额外的特色功能。

What excites me most isn't just what can now be built in a few hours. Rather, it is that, if AI assistance lets us build basic but fully functional products this quickly, then imagine what can now be done in a week, or a month, or six months. If the teams that participated in the Buildathon had this velocity of execution and iterated over multiple cycles of getting customer feedback and using that to improve the product, imagine how quickly it is now possible to build great products.

最让我兴奋的不仅仅是现在能在短短几小时内完成的工作。更重要的是，如果人工智能（AI）协助能让我们如此迅速地构建出基础但功能齐全的产品，那么试想一下，在一周、一个月乃至六个月的时间里，又能完成多少惊人的成就呢？如果那些参加 Buildathon 的团队，能够以如此高的执行速度，并经过多轮获取客户反馈并据此改进产品的迭代周期，试想一下，现在构建出卓越产品可能有多么迅速！

Owning proprietary software has long been a moat for businesses, because it has been hard to write complex software. Now, as AI assistance enables rapid engineering, this moat is weakening.

长期以来，拥有专有软件一直是企业的一道重要「护城河」，构筑起它们的竞争壁垒，这主要是因为开发复杂的软件绝非易事。然而，如今随着 AI 辅助（AI assistance）技术使得工程开发变得飞速，这种优势正在逐渐减弱。

While many members of the winning teams had computer science backgrounds — which does provide an edge — not all did. Team members who took home prizes included a high school senior, a product manager, and a healthcare entrepreneur who initially posted on Discord that he was "over his skis" as someone who "isn't a coder." I was thrilled that multiple participants told me they exceeded their own expectations and discovered they can now build faster than they realized. If you haven't yet pushed yourself to build quickly using agentic coding tools, you, too, might be surprised at what you can do!

虽然获胜团队的许多成员都拥有计算机科学背景 —— 这确实能提供一些优势 —— 但并非所有人都具备。那些赢得奖项的团队成员中，包括一名高中生、一名产品经理和一名医疗保健领域的创业者。这位创业者最初在 Discord 上发帖称自己「能力超限」，因为他「不是一名程序员」。让我感到激动的是，许多参与者告诉我他们超越了自己的预期，并发现他们现在能够比原先想象的更快地完成开发。如果你还没有尝试使用智能体编码工具（agentic coding tools）快速构建，你可能也会对自己的能力感到惊讶！

At AI Fund and DeepLearning.AI, we pride ourselves on building and iterating quickly. At the Buildathon, I saw many teams execute quickly using a wide range of tools including Claude Code, GPT-5, Replit, Cursor, Windsurf, Trae, and many others.

在 AI Fund 和 DeepLearning.AI，我们引以为傲的是能够快速构建和迭代产品。在 Buildathon 活动中，我看到许多团队利用各种工具，包括 Claude Code、GPT-5、Replit、Cursor、Windsurf、Trae 等，迅速完成了开发任务。

I offer my hearty congratulations to all the winners!

我向所有获奖者致以衷心的祝贺！

1st Place: Milind Pathak, Mukul Pathak, and  Sapna Sangmitra (Team Vibe-as-a-Service), a team of three family members. They also received an award for Best Design.

第一名：Milind Pathak、Mukul Pathak 和 Sapna Sangmitra（Team Vibe-as-a-Service），这个团队由三位家庭成员组成。他们还荣获了最佳设计奖。

2nd Place: David Schuster, Massimiliano Viola, and Manvik Pasula. (Team Two Coders and a Finance Guy).

第二名：David Schuster、Massimiliano Viola 和 Manvik Pasula（团队名称：Two Coders and a Finance Guy）。

Solo Participant Award: Ivelina Dimova, who had just flown to San Francisco from Portugal, and who worked on the 5 projects not sequentially, but in parallel!

最佳个人参与者奖：Ivelina Dimova。她不仅刚从葡萄牙飞抵旧金山，还以非顺序而是并行的方式完成了全部 5 个项目！

Graph Thinking Award: Divya Mahajan, Terresa Pan, and Achin Gupta (Team A-sync).

「图思考」奖： Divya Mahajan，Terresa Pan 和 Achin Gupta（Team A-sync）。

Honorable mentions went to finalists Alec Hewitt, Juan Martinez, Mark Watson and Sophia Tang (Team Secret Agents) and Yuanyuan Pan, Jack Lin, and Xi Huang (Team Can Kids).

荣誉奖授予了决赛入围者 Alec Hewitt，Juan Martinez，Mark Watson 和 Sophia Tang（Team Secret Agents），以及 Yuanyuan Pan，Jack Lin 和 Xi Huang（Team Can Kids）。

To everyone who participated, thank you! Through events like these, I hope we can all learn from each other, encourage each other, invent new best practices, and spread the word about where agentic coding is taking software engineering.

感谢所有参与者！我希望通过这类活动，我们大家都能互相学习，互相鼓励，共同创造新的最佳实践，并让更多人了解 AI 智能体编码（agentic coding）将如何引领软件工程走向未来。

Keep building!

Andrew

### News

#### China Reconsiders U.S. AI Processors

中国重新审视美国 AI 处理器

Nvidia and AMD, having obtained the U.S. government's permission to resume selling AI processors in China, received a cool welcome there.

英伟达（Nvidia）和 AMD 虽然获得了美国政府的许可，可以继续向中国销售人工智能处理器，但它们在中国市场却意外地遭遇了冷遇。

What's new: China's government, which is wary of U.S. control over the country's supply of high-end GPUs, is requiring Nvidia processors to undergo a security review, The Wall Street Journal reported. While the review is underway, the authorities are urging Chinese AI companies to buy domestic GPUs. DeepSeek reportedly tried and failed to use China-native Huawei GPUs to train DeepSeek-R2, the follow-up to its DeepSeek-R1 model, which has delayed the project, according to Financial Times.

最新进展：据《华尔街日报》报道，中国政府对美国在高 Ry-end GPU 供应上的控制保持警惕，因此要求英伟达的处理器必须通过安全审查。在审查进行的同时，中国当局正积极鼓励国内的人工智能公司采购国产 GPU。据《金融时报》透露，DeepSeek 曾尝试使用中国本土的华为 GPU 来训练其 DeepSeek-R1 模型的升级版 DeepSeek-R2，但据称未能成功，这导致了该项目的延迟。

How it works: The Chinese government's resistance to AI processors from U.S. vendors signals rising confidence in the nation's AI capabilities, as the U.S. seeks to return to selling advanced processors in China after blocking such sales in recent months. China is helping the domestic semiconductor industry to compete against U.S. designers like Nvidia and AMD and the Taiwanese manufacturer TSMC, which fabricates their products, by providing funds and tax incentives and applying pressure to Chinese AI companies to buy processors made domestically. Meanwhile, Chinese vendors aim to close the performance gap between their products and those of U.S. competitors.

运作方式：中国政府对来自美国供应商的 AI 处理器的抵制，表明该国在 AI 能力上日益增长的信心。这正值美国在近几个月阻止此类销售后，寻求重返中国市场销售先进处理器之际。中国正通过提供资金、税收优惠以及施压国内 AI 公司购买国产处理器等方式，帮助本土半导体行业与 Nvidia 和 AMD 等美国设计公司以及生产其产品的台湾制造商 TSMC 展开竞争。与此同时，中国供应商也致力于缩小其产品与美国竞争对手产品之间的性能差距。

* China raised security concerns about U.S. processors. The government required Nvidia to explain alleged "backdoor security risks" of its H20 processor, which is designed to comply with U.S. export restrictions. China cited information it said it had obtained from U.S. artificial intelligence experts that the H20 could be shut down remotely and used to track users' locations. Nvidia disputed those claims. (The H20's processing power is roughly comparable with that of the Huawei Ascend 910B/C and less than that of Nvidia's most advanced products, but its memory capacity and bandwidth are superior to Huawei's best and closer to its Nvidia peers.)

* 中国对美国处理器提出了安全疑虑。政府要求 Nvidia 解释其 H20 处理器所谓的「后门安全风险」，这款处理器正是为遵守美国出口限制而设计的。中方引述其声称从美国人工智能专家那里获得的信息，指出 H20 可能会被远程关闭并用于追踪用户位置。Nvidia 对这些说法予以驳斥。（H20 的处理能力大致与华为昇腾 910B/C 相当，但不及 Nvidia 最先进的产品；不过，其内存容量和带宽则优于华为同类最佳产品，并更接近 Nvidia 自家其他产品。）

* China questioned domestic technology firms including Baidu, ByteDance, and Tencent about their desires to use U.S. processors.

* China's scrutiny of U.S. processors could set back Nvidia. In July, the company placed orders to manufacture 300,000 H20 chipsets and warned customers that demand might outstrip supply.

*  中国就国内科技公司，包括百度、字节跳动和腾讯，使用美国处理器（U.S. processors）的意愿进行了问询。
*  中国对美国处理器的审查可能会给 Nvidia 带来挑战。今年七月，该公司订购了 300,000 片 H20 芯片组，同时警告客户市场需求可能远超供应。

Behind the news: The U.S. government restricted sales of U.S. AI processors to China in 2022. The Trump administration tightened the restriction but recently reversed course.

新闻背景：2022 年，美国政府限制了美国 AI（Artificial Intelligence）处理器对中国的销售。特朗普政府曾收紧这一限制，但最近又改变了相关政策。

* In April, the White House effectively banned sales to China of advanced chips that use U.S. technology by making them subject to export licenses, which apparently were not forthcoming.

*  今年四月，白宫实际上禁止了使用美国技术的先进芯片向中国销售。具体做法是要求这些芯片必须获得出口许可证，而这些许可证显然不会被批准。

* In recent weeks, the White House lifted the ban. In return, China agreed to sell to the U.S. rare-earth minerals and magnets derived from them, which are critical components in a wide range of consumer and industrial devices including smartphones, hard disks, and electric cars. In an unusual arrangement, U.S. chip vendors will be required to pay to the U.S. government an export license fee of 15 percent of their revenue from sales to China.

* 最近几周，白宫解除了禁令。作为回报，中国同意向美国出售稀土矿物及由稀土提炼而成的磁铁，这些都是包括智能手机、硬盘和电动汽车在内，各种消费和工业设备中的关键组件。根据一项不同寻常的安排，美国芯片供应商将被要求向美国政府支付其对华销售收入 15% 的出口许可证费。

* Nvidia is developing a scaled-down, low-cost processor for the Chinese market based on its upcoming Blackwell chip architecture. The White House said it may allow Nvidia to export such processors to China.

*  Nvidia 正在研发一款针对中国市场的精简版低成本处理器，该处理器将基于其即将发布的 Blackwell 芯片架构。白宫方面表示，可能会允许 Nvidia 向中国出口这类处理器。

Why it matters: The U.S. and China are wary that the other will gain a strategic advantage in technological, economic, or military power. Leadership in AI is central to all three areas. While U.S. AI companies have developed cutting-edge proprietary models, their counterparts in China have pulled ahead in open models on which anyone can build applications free of charge. But processors remain a sticking point. Spurred by U.S. export controls and policy shifts, which have made the U.S. an unreliable supplier, China is doubling down on its own semiconductor industry in hope of catching up with — and advancing beyond — Nvidia and TSMC.

重要性：美国和中国都担心对方会在技术、经济或军事力量上占据战略优势。而人工智能（AI）领域的领导地位，对这三个方面都至关重要。美国的人工智能公司虽然开发出了顶尖的专属模型，但中国同类企业在开放模型方面已经领先一步，任何人都可以免费基于这些模型开发应用程序。不过，处理器依然是症结所在。由于美国出口管制和政策调整，使其成为一个不可靠的供应商，中国正加倍投入发展自己的半导体产业，希望能赶上并超越 Nvidia 和 TSMC。

We're thinking: Developers around the world use open-weights models from China. Whether they will also adopt AI processors from China is an open question.

#### Mixture of Video Experts

值得深思的是：世界各地的开发者都在使用来自中国的开放权重模型（open-weights models）。然而，他们是否也会采纳来自中国的 AI 处理器（AI processors），这仍然是一个有待观察的问题。

#### 视频专家混合

The mixture-of-experts approach that has boosted the performance of large language models may do the same for video generation.

What's new: Alibaba released Wan 2.2, an open-weights family of video generation models that includes versions built on a novel mixture-of-experts (MoE) flow-matching architecture. Wan2.2-T2V-A14B generates video from text input, Wan2.2-I2V-A14B generates video from images, and Wan2.2-TI2V-5B generates video from either text or images. At 5 billion parameters, Wan2.2-TI2V-5B runs on consumer GPUs.

为大语言模型（Large Language Model）提升性能的混合专家（Mixture-of-Experts）方法，或许也能为视频生成带来同样的助益。

新进展：阿里巴巴发布了 Wan 2.2，这是一个权重开源的视频生成模型家族。该家族中的一些版本是基于一种新颖的混合专家（MoE）流匹配架构构建的。其中，Wan2.2-T2V-A14B 模型能根据文本输入生成视频，Wan2.2-I2V-A14B 则能从图像生成视频，而 Wan2.2-TI2V-5B 更是可以同时支持文本或图像输入来生成视频。值得一提的是，Wan2.2-TI2V-5B 拥有 50 亿个参数，即便在消费级 GPU 上也能流畅运行。

* Input/output: Wan2.2-T2V-A14B: Text up to 512 tokens in, video up to 5 second out (30 frames per second, up to 1280x720 pixels per frame). Wan2.2-I2V-A14B: Images up to 1280x720 pixels in, video up to 5 seconds out (30 frames per second, up to 1280x720 pixels per frame).  Wan2.2-TI2V-5B: Text up to 512 tokens and/or images up to 1280x704 pixels in, video up to 5 seconds out (24 frames per second, 1280x704 pixels per frame).

*  输入 / 输出： Wan2.2-T2V-A14B：输入文本最多 512 个 Token（Token），输出视频最长 5 秒 （每秒 30 帧，每帧最高 1280x720 像素）。Wan2.2-I2V-A14B：输入图像最高 1280x720 像素，输出视频最长 5 秒 （每秒 30 帧，每帧最高 1280x720 像素）。Wan2.2-TI2V-5B：输入文本最多 512 个 Token 和 / 或图像最高 1280x704 像素，输出视频最长 5 秒 （每秒 24 帧，每帧 1280x704 像素）。

* Architecture: UMT5 transformer to encode text, 3D convolutional variational autoencoder (VAE) to encode and decode images, flow-matching model to generate output: MoE transformer, 27 billion parameters total, 14 billion active per token (Wan2.2-T2V-A14B and Wan2.2-I2V-A14B) or transformer (Wan2.2-TI2V-5B).

* 架构：它采用 UMT5 Transformer 来编码文本，使用 3D 卷积变分自编码器（VAE）对图像进行编码和解码。至于生成输出，则使用了流匹配模型（flow-matching model)：这个模型可以是 MoE Transformer（总参数量达 270 亿，其中每个 Token 激活 140 亿参数，如 Wan2.2-T2V-A14B 和 Wan2.2-I2V-A14B），也可以是标准的 Transformer（例如 Wan2.2-TI2V-5B）。

* Availability: Web interface (free), weights available via HuggingFace and ModelScope for commercial and non-commercial uses under Apache 2.0 license, API (MoE models only) $0.02 per second of 480p output, $0.10 per second of 1080p output (API only)

* 获取方式： 提供免费的网页界面；模型权重可通过 HuggingFace 和 ModelScope 获取，在 Apache 2.0 许可证下可用于商业和非商业用途；API 服务（仅限 MoE 模型）按输出分辨率收费，480p 输出每秒 0.02 美元，1080p 输出每秒 0.10 美元（仅限 API）。

* Undisclosed: VAE parameter count, training data, differences in training methods between Wan 2.2 and the earlier Wan 2.1

How it works: The team pretrained the VAE to encode and decode images. They pretrained the flow-matching model, given a video embedding from the VAE with noise added and a text embedding from UMT5, to remove the noise over several steps.

* 未披露信息：VAE（Variational Autoencoder）的参数数量、训练数据，以及 Wan 2.2 与早期版本 Wan 2.1 之间在训练方法上的差异。

工作原理：研究团队首先对 VAE（Variational Autoencoder）进行了预训练，使其能够对图像进行编码和解码。随后，他们预训练了一个 flow-matching 模型（flow-matching model），该模型结合了来自 VAE 的带噪声视频嵌入（video embedding）以及来自 UMT5 的文本嵌入（text embedding）作为输入，分多个步骤逐步去除噪声。

* The MoE model has two experts: one for very noisy inputs and one for less noisy inputs. One expert generates the objects and their positions across a video, the other handles details.

* MoE（Mixture of Experts）模型包含两个「专家」：一个专门处理噪声较大的输入，另一个则负责处理噪声较小的输入。其中一个专家负责生成视频中的物体及其位置，而另一个专家则专注于处理这些物体的细节。

* To determine which expert to use, the model computes the signal-to-noise ratio of the noisy embedding. Specifically, it starts with the high-noise expert, determines the time step at which the proportion of noise has fallen by half, and switches to the low-noise expert after that time step.

* 为了决定使用哪个专家，模型会计算其带噪声的嵌入的信号噪声比（signal-to-noise ratio）。具体来说，它会先启用高噪声专家，然后确定噪声比例减半的时间步长，并在达到该时间步长后切换到低噪声专家。

* At inference, the VAE embeds an input image (if applicable) and UMT5 embeds input text (if applicable). The model concatenates the image embedding (if applicable) with an embedding of noise. Given the noisy embedding and text embedding, the flow-matching model removes noise over several steps. Finally, the VAE decodes the denoised embedding to produce video output.

* 在推理阶段，VAE 会对输入的图像进行嵌入（embedding）处理（如果适用），UMT5 则会嵌入输入的文本信息（如果适用）。接着，模型会将图像的嵌入（如果适用）与一个表示噪声的嵌入拼接起来。有了这种带噪声的嵌入和文本嵌入后，流匹配模型（flow-matching model）会通过多个步骤来逐步去除噪声。最后，VAE 将这个去噪后的嵌入解码，从而生成最终的视频输出。

Results: Results for Wan 2.2 are limited. The team shared only the performance of the MoE models on a proprietary benchmark, Wan-Bench-2.0, whose mechanics, categories, and units it has not yet described. The team compared Wan2.2-T2V-A14B to competitors including Bytedance Seedance 1.0, Kuaishou KLING 2.0, and OpenAI Sora.

结果：Wan 2.2 的相关结果目前非常有限。该团队仅分享了其 MoE 模型在自有的专有基准（proprietary benchmark）Wan-Bench-2.0 上的性能数据，但并未详细描述 Wan-Bench-2.0 这个基准的运作机制、具体分类以及衡量单位。此外，该团队还将其 Wan2.2-T2V-A14B 模型与包括 Bytedance Seedance 1.0、Kuaishou KLING 2.0 和 OpenAI Sora 在内的竞争对手进行了对比。

* For esthetic quality, Wan2.2-T2V-A14B (85.3) outperformed second-best Seedance 1.0 (84.3).

* It also achieved the highest scores for dynamic output, rendered text, and the prompt control over the camera.

*  在审美质量方面，Wan2.2-T2V-A14B 以 85.3 分的成绩超越了位居第二的 Seedance 1.0（84.3 分）。

*  此外，它还在动态输出、文本渲染以及通过提示词对摄像机的控制方面获得了最高分。

* For video fidelity, Wan2.2-T2V-A14B (73.7) came in second to Seedance (81.8).

Behind the news: Open models for video generation have been proliferating. Within the last year, there are Mochi, HunyuanVideo, LTX-Video, pyramid-flow-sd3, CogVideoX, and more.

*  在视频的保真度方面，Wan2.2-T2V-A14B（73.7）表现出色，但仍略逊于 Seedance（81.8），位居第二。

新闻背后的故事：用于视频生成的开源模型（open models）正在飞速发展。仅仅在过去一年里，我们就见证了 Mochi、HunyuanVideo、LTX-Video、pyramid-flow-sd3、CogVideoX 等众多模型的涌现。

Why it matters: MoE architectures have become popular for their superior performance in text generation. Selecting the expert(s) to use for a given input often is done either by a router that learns which expert(s) work best for a given token or based on the input data type. This work is closer to the latter. The model selects the appropriate expert based on the noise in the input.

为什么这很重要：混合专家（MoE）架构因其在文本生成方面表现卓越而广受欢迎。在处理特定输入时，选择合适的专家模块通常有两种方式：一种是由一个「路由器（router）」来学习哪个专家最适合某个特定的「Token」，另一种则是根据输入数据的类型来选择。本研究的方法更倾向于后一种。具体来说，该模型会根据输入数据中的噪声来选择最合适的专家模块。

We're thinking: Video generation is exploding! Proprietary systems generally have made deeper inroads into the professional studios, but open models like this show great promise.

我们认为：视频生成技术正迎来爆发式增长！虽然专有系统通常已在专业工作室中占据了更主导的地位，但像我们讨论的这类开源模型也展现出了巨大的潜力。

#### OpenAI Turns to Oracle for Compute

OpenAI is working with Oracle to build its next chunk of processing power, a $30 billion outgrowth of the partners' $500 billion Stargate project and a sign of OpenAI's ongoing thirst for computation.

#### OpenAI 选择 Oracle 获取计算能力

OpenAI 正在与 Oracle 合作，共同打造其新一代计算能力。这笔价值 300 亿美元的投资，是其与合作伙伴 5000 亿美元 Stargate 项目的一个重要拓展，也充分表明了 OpenAI 对计算资源持续增长的需求。

What's new: OpenAI and Oracle plan to build data-center capacity that will consume 4.5 gigawatts of electricity, an order of magnitude more than one of the largest data centers under construction Microsoft, which currently provides OpenAI's computational muscle. The locations have not yet been announced.

新进展： OpenAI 和 Oracle 正计划建设大量数据中心，建成后将消耗高达 4.5 吉瓦（gigawatts）的电力。这个用电量，比目前正在建设中的一个大型数据中心（例如由 Microsoft 建造的那些）还要高出一个数量级。要知道，Microsoft 目前正为 OpenAI 提供关键的计算支持。目前，这些数据中心的具体选址尚未公布。

How it works: The plan follows the successful launch of an OpenAI-Oracle data center built in Abilene, Texas, that serves as a proof of concept. That project will draw 1.2 gigawatts when it's finished next year.

工作原理： 这项计划的提出，是基于 OpenAI 和 Oracle 在德克萨斯州阿比林成功启动了一个数据中心，该中心作为一个概念验证（proof of concept）项目。这个项目明年建成后，预计将消耗 1.2 千兆瓦的电力。

* OpenAI will pay Oracle $30 billion annually, The Wall Street Journal reported.

* OpenAI wrote in a blog post that it expects to exceed its planned $500 billion data-center buildout dubbed Stargate, and that it's assessing sites with Stargate partner SoftBank.

*  据《华尔街日报》报道，OpenAI 将每年向 Oracle 支付 300 亿美元。
*  OpenAI 在一篇博客文章中表示，它预计将超出其名为 Stargate 的 5000 亿美元数据中心建设计划，并且目前正与 Stargate 项目的合作伙伴 SoftBank 一起评估潜在的选址。

* In October 2024, Altman complained in a Reddit Ask Me Anything session that a lack of processing power has delayed the company's products.

Behind the news: Stargate, a partnership among OpenAI, Oracle, and Softbank, was announced by President Trump at the White House alongside the executive order that called for the U.S. government's recent AI action plan.

* 2024 年 10 月，Altman 在 Reddit 上的「你问我答」（Ask Me Anything，简称 AMA）活动中抱怨说，由于计算能力（算力）不足，公司的产品开发和发布受到了延迟。

新闻背景：名为 Stargate 的项目，是 OpenAI、Oracle 和 Softbank 之间的一项合作。该项目由特朗普总统在白宫宣布，同时公布的还有一份要求美国政府制定最新人工智能（AI）行动计划的行政命令。

* The partners aimed to spend $500 billion over four years to build 20 data centers. OpenAI would receive processing power, Oracle would provide hardware and software infrastructure, and SoftBank would secure financing.

* 这些合作方计划在四年内投入 5000 亿美元，用于建设 20 个数据中心。其中，OpenAI 将获得所需的处理能力，Oracle 将提供硬件和软件基础设施，而 SoftBank 则负责筹集资金。

* Other participants in Stargate include the Colorado-based builder Crusoe, Emirati AI-investment fund MGX, OpenAI's infrastructure partner Microsoft, and Nvidia.

*  Stargate 项目的其他参与方包括总部位于科罗拉多州的建设公司 Crusoe、阿联酋的 AI 投资基金 MGX、OpenAI 的基础设施合作伙伴 Microsoft，以及英伟达（Nvidia）。

Why it matters: Staying at the forefront of AI requires immense amounts of computation, despite innovations in more compute-efficient model architectures and training and inference techniques. But how to get it? For OpenAI, the answer is forming strong ties to large-scale providers of cloud computing; first Microsoft, now Oracle. The OpenAI-Oracle partnership enables OpenAI to continue to develop models at pace and at scale, while it enables Oracle to gain experience and credibility as a provider of large-scale computing for cutting-edge AI.

重要性： 尽管在提升计算效率的模型架构以及训练和推理技术方面不断创新，但要保持在 AI（人工智能）的最前沿，仍然需要海量的计算资源。那么，如何才能获得这些资源呢？对于 OpenAI 而言，答案是与大规模的云计算提供商建立紧密的合作关系；起初是 Microsoft，现在又拓展到了 Oracle。OpenAI 与 Oracle 的合作关系让 OpenAI 能够继续保持快速且大规模地开发模型，同时也帮助 Oracle 作为前沿 AI 的大规模计算提供商，积累经验并提升行业信誉。

We're thinking: OpenAI's plan to build 20 giant data centers — even more, based on the company's latest statement —  poses a major challenge to existing energy resources. Having SoftBank as a partner may be a significant advantage as that company ramps up its investments in power generation specifically for AI.

我们不禁要问：OpenAI 计划建造 20 座巨型数据中心 —— 根据该公司最新声明，数量甚至可能更多 —— 这无疑对现有的能源供应构成了巨大挑战。而 SoftBank 作为合作伙伴，可能会带来显著优势，因为这家公司正大力投资于专门为 AI 供电的发电设施。

#### Does Your Model Generalize or Memorize?

Benchmarks can measure how well large language models apply what they've learned from their training data to new data, but it's harder to measure the degree to which they simply memorized their training data. New work proposes a way to gauge memorization.

#### 您的模型是泛化还是记忆？

基准测试可以衡量大语言模型（Large Language Model）如何将从训练数据中学到的知识应用到新数据上，但要衡量它们在多大程度上仅仅是记住了训练数据，则要困难得多。一项新的研究提出了一种评估模型记忆能力的方法。

What's new: John X. Morris and colleagues at Meta, Google, Cornell University, and Nvidia developed a method that measures the number of bits a model memorizes during training.

最新消息是：Meta、Google、康奈尔大学和 Nvidia 的 John X. Morris 及其同事们开发出一种方法，能用来衡量一个模型在训练过程中记忆了多少比特（bits）信息。

Key insight: A model's negative log likelihood is equal to the minimum number of bits needed to represent a given piece of data. The more likely the model is to generate the data, the fewer bits needed to represent it. If, to represent a given output, a hypothetical best model requires more bits than a trained model, then the trained model must have memorized that many bits of that output. The best model is hypothetical, but a better-performing model can stand in for it. The difference in the numbers of bits used to represent the output by this superior model and the trained model is a lower bound on the number of bits the trained model has memorized.

关键洞察：模型的负对数似然（negative log likelihood）等于表示给定数据所需的最小比特数。模型生成数据的可能性越大，表示这些数据所需的比特数就越少。如果为了表示某个输出，一个假设的「最佳」模型比一个已训练模型需要更多的比特数，那么这个已训练模型就一定记忆了该输出的相应比特信息。虽然「最佳」模型只是一个假设，但我们可以用一个性能更好的模型来替代它。这个更优模型与已训练模型在表示同一输出时所用比特数之间的差异，就是已训练模型所记忆比特数的一个下限。

How it works: The authors trained hundreds of GPT-2 style models to predict the next token in two text datasets: (i) a synthetic dataset of 64-token strings in which each token was generated randomly and (ii) the FineWeb dataset of text from the web, its examples truncated to 64 tokens and deduplicated. They trained models from 100,000 to 20 million parameters on subsets of these datasets from 16,000 to 4 million examples. Then they computed the how much of the datasets the models had memorized:

它们的工作原理如下：作者训练了数百个 GPT-2 风格的模型，旨在预测两个文本数据集中的下一个 Token（Token)：
(i）一个合成数据集，由 64 个 Token 的字符串组成，每个 Token 都是随机生成的；
(ii）FineWeb 文本数据集，其中的网络文本示例被截断为 64 个 Token 并进行了去重。
他们使用这些数据集的子集来训练模型，这些模型的参数量从 100,000 个到 2000 万个不等，每个子集包含 16,000 到 400 万个样本。随后，他们计算了模型对数据集的记忆量：

* The authors computed the number of bits needed to represent each training example based on the likelihoods of the trained model and a superior model. For models trained on synthetic data, the superior model was the distribution used to generate the data. For models trained on a subset of FineWeb, they used GPT-2 trained on all FineWeb examples (after truncation and deduplication).

* 作者们计算了表示每个训练样本所需的比特数，这个计算基于已训练模型和一个表现更优模型的似然值（likelihoods）。具体来说，对于那些用合成数据（synthetic data）训练的模型，表现更优的模型就是用来生成这些数据的原始数据分布。而对于那些用 FineWeb 数据集子集训练的模型，他们则使用了在所有 FineWeb 样本（经过截断和去重处理后）上训练的 GPT-2 模型作为参照。

* They subtracted the number of bits computed for the superior model from the number computed for the trained model. A positive difference indicated the amount of memorization. A zero or negative difference indicated that memorization did not occur.

他们将优越模型计算出的比特数从训练模型计算出的比特数中减去。正的差值表明了记忆的程度。零或负的差值则表示没有发生记忆。

* To find the amount of data the model had memorized. they summed the number of bits memorized per example.

Results: The maximum number of bits a model memorized rose linearly with its parameter count regardless of the training dataset, amount of training data, or model size.

* 为了探究模型究竟记忆了多少数据，研究人员计算出模型在每个示例（example）中记忆的比特（bit）总数。

结果：研究发现，模型能记忆的最大信息量（bits memorized）与其参数数量（parameter count）呈线性增长关系。这意味着，无论训练数据集（training dataset）的类型、训练数据（training data）的多少，还是模型自身的大小（model size）如何，这种线性关系都始终成立。

* Trained on synthetic data, a model's memorization increased linearly and then plateaued after a certain amount of training data.

* Maximum memorization was approximately 3.5 to 3.6 bits per parameter (their models used 16 bits to represent each parameter).

*  当模型在合成数据上进行训练时，其记忆能力（memorization）会先线性增长，在训练数据达到一定量后便会趋于平稳。
*  模型能达到的最大记忆能力约为每个参数 3.5 到 3.6 比特（值得一提的是，他们的模型使用 16 比特来表示每个参数）。

* Trained on FineWeb, a model's memorization increased linearly with the amount of training data before decreasing as the model started to generalize (that is, the number of bits memorized per parameter fell and benchmark scores rose). This result showed that models memorize until they reach a maximum capacity and then start to generalize.

*  当模型在 FineWeb 上进行训练时，其对训练数据的记忆（memorization）量会随着训练数据量的增加而线性增长。随后，当模型开始泛化（generalize）时 —— 也就是说，模型每个参数记忆的比特数减少，同时基准分数（benchmark scores）上升 —— 其记忆量便开始下降。这一结果表明，模型会持续记忆训练数据，直到达到其最大容量，此后才会开始学习泛化。

Why it matters: Some previous efforts to measure memorization calculated the percentage of examples for which, given an initial sequence of tokens, a model would generate the rest. However, generating a repetitive sequence like "dog dog dog…" does not mean that a model has memorized it, and solving a simple arithmetic problem does not mean the model has memorized it or even encountered it in its training data. This work provides a theoretical basis for estimating how much of their training sets models memorize. It also lays a foundation for further work to reduce memorization without increasing the sizes of training datasets.

为什么这很重要：在测量模型记忆化（memorization）能力的某些早期尝试中，研究人员会计算给定一个初始 Token（Token）序列时，模型能生成剩余部分的例子有多少。然而，生成一个重复序列，例如「dog dog dog…」，并不意味着模型已经记住了它；同样，解决一个简单的算术问题也不意味着模型记住了这个问题，甚至不意味着它在训练数据中遇到过这个问题。这项工作为估算模型对其训练数据的记忆程度提供了理论基础。它也为在不增加训练数据集大小的情况下减少模型记忆化的进一步研究奠定了基础。

We're thinking: It's well known that more training data helps models to generalize. This work shows how to estimate the amount of data necessary before models begin to generalize.

我们认为：众所周知，更多训练数据有助于提升模型的泛化能力（generalize）。这项工作展示了如何估算模型在开始具备泛化能力前，究竟需要多少数据。