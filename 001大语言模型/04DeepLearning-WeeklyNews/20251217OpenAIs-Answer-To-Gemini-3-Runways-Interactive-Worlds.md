## 20251217OpenAIs-Answer-To-Gemini-3-Runways-Interactive-Worlds

[OpenAI’s Answer to Gemini 3, Runway’s Interactive Worlds, Disney’s Alliance With OpenAI, and more...](https://www.deeplearning.ai/the-batch/issue-332/)

Dear friends,

As amazing as LLMs are, improving their knowledge today involves a more piecemeal process than is widely appreciated. I've written about how AI is amazing . . .but not that amazing. Well, it is also true that LLMs are general . . .but not that general. We shouldn't buy into the inaccurate hype that LLMs are a path to AGI in just a few years, but we also shouldn't buy into the opposite, also inaccurate hype that they are only demoware. Instead, I find it helpful to have a more precise understanding of the current path to building more intelligent models.

大语言模型（Large Language Model）固然非常强大，但如今要增进它们的知识，这个过程其实比大家通常认为的更加零散和渐进。我之前写过，人工智能（AI）确实很了不起…… 但也没那么神。同样，大语言模型确实有通用性…… 但也没那么通用。我们不应轻信那种不实的炒作，认为大语言模型是一条能在短短几年内就通向通用人工智能（AGI）的坦途；但也不应走向另一个极端，去相信另一种同样不实的炒作，认为它们只不过是些华而不实的演示品（demoware）。相反，我认为，更准确地理解当前构建更智能模型的发展路径，会让我们受益匪浅。

First, LLMs are indeed a more general form of intelligence than earlier generations of technology. This is why a single LLM can be applied to a wide range of tasks. The first wave of LLM technology accomplished this by training on the public web, which contains a lot of information about a wide range of topics. This made their knowledge far more general than earlier algorithms that were trained to carry out a single task such as predicting housing prices or playing a single game like chess or Go. However, they'refar less general than human abilities. For instance, after pretraining on the entire contentof the public web, an LLM still struggles to adapt to write in certain styles that many editors would be able to, or use simple websites reliably.

首先，大语言模型（LLM）确实是一种比早期技术更为通用的智能形式。正因如此，单个大语言模型就能被应用到各种各样的任务中。第一波大语言模型技术之所以能做到这一点，是因为它们在海量的公共网络数据上进行了训练，这些数据涵盖了极其广泛的主题。这使得它们的知识面，远比那些为执行单一任务（比如预测房价，或者下国际象棋、围棋这类特定游戏）而训练的早期算法要广博得多。然而，它们的通用性仍远不及人类。例如，即便对整个公共网络的全部内容进行了预训练，一个大语言模型仍然难以像许多编辑那样，熟练运用某些特定的文风进行写作，或者稳定可靠地操作一些简单的网站。

After leveraging pretty much all the open information on the web, progress got harder. Today, if a frontier lab wants an LLM to do well on a specific task — such as code using a specific programming language, or say sensible things about a specific niche in, say, healthcare or finance — researchers might go through a laborious process of finding or generating lots of data for that domain and then preparing that data (cleaning low-quality text, deduplicating, paraphrasing, etc.) to create data to give an LLM that knowledge.

在几乎用尽了网络上所有公开信息后，技术进步变得愈发艰难。如今，如果一个前沿实验室希望大语言模型（LLM）在某个特定任务上表现出色 —— 比如用某种特定编程语言写代码，或者就医疗、金融等某个细分领域发表靠谱的见解 —— 研究人员可能就得经历一个繁琐的过程：他们需要为该领域寻找或生成海量数据，然后对这些数据进行预处理（包括清理低质量文本、去重、改写等），最终将这些处理后的数据「喂」给大语言模型，使其掌握相关知识。

Or, to get a model to perform certain tasks, such as use a web browser, developers might go through an even more laborious process of creating many RL gyms (simulated environments) to let an algorithm repeatedly practice a narrow set of tasks.

或者，为了使模型能够完成某些特定任务，例如使用网络浏览器，开发者可能需要经历一个更为费力的过程：创建许多强化学习训练环境（RL gyms，即模拟环境），以便让算法反复练习一组范围非常有限的任务。

A typical human, despite having seen vastly less text or practiced far less in computer-use training environments than today's frontier models, nonetheless can generalize to a far wider range of tasks than a frontier model. Humans might do this by taking advantage of continuous learning from feedback, or by having superior representations of non-text input (the way LLMs tokenize images still seems like a hack to me), and many other mechanisms that we do not yet understand.

一个普通人，即便见过的文本量远少于当今的前沿模型，或在基于计算机的训练数据环境中进行的「练习」也远不及它们，却依然能将其能力泛化到比前沿模型广泛得多的任务上。人类能做到这一点，或许是得益于能够持续从反馈中学习，或许是因为对非文本输入（如图像、声音）具有更优的表征能力（在我看来，大语言模型将图像转换为 Token 的方式至今仍像一种权宜之计），此外可能还依赖许多我们尚未理解的其他机制。

Advancing frontier models today requires making a lot of manual decisions and taking adata-centric AIapproach to engineering the data we use to train our models. Future breakthroughs might allow us to advance LLMs in a less piecemeal fashion than I describe here. But even if they don't, I expect that ongoing piecemeal improvements, coupled with the limited degree to which these models do generalize and exhibit "emergent behaviors," will continue to drive rapid progress.

如今，要推进前沿模型的发展，需要做出大量人工决策，并采用以数据为中心的人工智能（Data-centric AI）方法，对我们用于训练模型的数据进行系统化工程处理。未来的技术突破，或许能让我们以比我这里描述的更系统化、而非零敲碎打的方式来推动大语言模型的进步。但即便这些突破没有实现，我预计，持续进行的渐进式改进，连同这些模型目前所具备的（即使是有限的）泛化能力与「涌现行为」，仍将继续驱动该领域快速发展。

Either way, we should plan for many more years of hard work. A long, hard — and fun! — slog remains ahead to build more intelligent models.

无论如何，我们都应为未来持续多年的艰苦努力做好规划。要打造更智能的模型，前方依然是一段漫长、艰辛 —— 同时也充满乐趣！—— 的征程。

Keep building!
Andrew

继续创造！
— Andrew

### News

### 新闻

#### Coherent, Interactive Worlds

#### 连贯且可交互的世界

Runway's GWM-1 family of video-generation models respond to user input in real time while producing scenes thatremain consistent regardless of the camera's position.

Runway 的 GWM-1（Generative World Model-1）系列视频生成模型能够实时响应用户输入，并且无论摄像机如何移动，都能确保生成的场景保持连贯一致。

What's new:RunwayintroducedGWM-1, a trio of "general world models" that were trained to understand how scenes behave, not just how scenes appear. GWM Worlds generates scenes, GWM Robotics produces synthetic data for training and testing robots, and GWM Avatars generates conversational characters with facial expressions and lip-synced speech. (In addition, the company added audio generation, audio editing, and multi-shot video editing capabilities to Gen-4.5, its flagship video generator.)

新进展：Runway 推出了 GWM-1，这是一个包含三个「通用世界模型（General World Models）」的系列。这些模型的训练目标是理解场景的动态行为，而不仅仅是其静态外观。其中，GWM Worlds 用于生成场景，GWM Robotics 可为机器人的训练和测试生成合成数据，GWM Avatars 则能创建带有丰富面部表情和口型同步语音的对话角色。（此外，该公司还为其旗舰视频生成模型 Gen-4.5 新增了音频生成、音频编辑以及多镜头视频编辑功能。）

* Architecture:Autoregressive diffusion model based on Gen-4.5

* **架构**：一种基于 Gen-4.5 的自回归扩散模型（Autoregressive Diffusion Model）。

* Input/output:Text and images in, video out (up to 2 minutes, 1280x720-pixel resolution, 24 frames per second)

* 输入输出：支持文本和图像输入，生成视频输出（最长 2 分钟，分辨率 1280x720，帧率 24 fps）

* Availability:The models will be available in "coming weeks." GWM Worlds andGWM Avatars will be available viaweb interface, GWM Robotics software development kit byrequest.

* 可用性：模型将在「未来几周内」推出。GWM Worlds 和 GWM Avatars 将提供网页界面访问，而 GWM Robotics 软件开发工具包（SDK）则需要申请获取。

* Undisclosed:Parameter count, training data and methods, pricing, release dates, performance metrics

* 未披露：参数数量、训练数据与方法、定价、发布日期、性能指标

How it works:Unlike typical diffusion models that generate an entire video simultaneously by removing noise progressively over a number of steps, GWM-1 generates one frame at a time based on past frames and control inputs. This autoregressive approach enables the model to respond to control input in real time. Runway built each GWM-1 model by post-training Gen-4.5 on domain-specific data. Themodels take still images and text as input.

工作原理：典型的扩散模型会通过多步迭代、逐步去除噪声的方式，一次性生成整个视频。与之不同，GWM-1 采用了一种自回归方法：它根据历史帧和给定的控制信号，逐帧生成视频。这种方式使得模型能够实时地对控制输入做出响应。Runway 公司通过在其基础模型 Gen-4.5 上，使用特定领域的数据进行微调，从而构建出每一个 GWM-1 模型。这些 GWM-1 模型以静态图像和文本作为输入。

* GWM Worlds generates a video simulation as the user navigates through the scene by issuing text commands. Users prompt the system to define an agent, physics, and world (such as a person walking through a city or a drone flying over mountains). The model maintains space and geometry consistently as objects come in and out of view, so objects remain in place as they shift in and out of the camera's view.

* GWM Worlds 是一个视频模拟生成系统。当用户通过输入文本命令在场景中探索时，它能生成相应的模拟视频。用户可以通过文本提示来定义一个智能体（Agent）、物理规则和虚拟世界（例如，一个在城市中行走的人，或一架飞越山峦的无人机）。该系统背后的模型能够确保，当物体进入或离开视野时，整个场景的空间和几何关系保持一致。因此，即使物体移出摄像机画面，它们的位置也不会改变，当再次进入画面时，它们还会在原来的地方。

* GWM Robotics was trained on unspecified robotics data to generate sequences of frames that show how a scene changes, from a robot's point of view, depending on its actions. Developers can explore alternative robot motions or directions of travel by modifying the simulated actions and observing the output.

* GWM Robotics 基于未指定的机器人数据进行训练，能够生成一系列帧，从机器人的第一视角展示场景如何随其动作而变化。开发者可以通过调整模拟动作并观察输出结果，来探索不同的机器人运动轨迹或行进方向。

* GWM Avatars is intended for conversational applications. Users select a voice and enter a portrait and/or text, and the model generates a character with realistic facial expressions, voices, lip sync, and gestures that will interact conversationally. Characters can be photorealistic or stylized.

* GWM Avatars 专为对话应用而设计。用户只需选择一种声音，并提供一张肖像照片或一段文字描述（或两者都提供），模型便能生成一个角色。这个角色拥有逼真的面部表情、语音、口型同步和肢体动作，能够进行自然对话。生成的角色既可以是高度写实的，也可以是艺术风格化的。

Behind the news:Until recently, world models, or models that predict the future state of an environment given certain actions taken within that environment, reflected fairlylimitedworlds. Upon its launch in early 2024, OpenAI'sSora 1generated video output that was impressive enough to inspire arguments over whether it qualified as a world model of the real world. Those arguments were premature, since Sora 1's output, however photorealistic it was, was not consistent with real-world physics, for instance. But they presaged models like GoogleGenie 2, which produces 3D video-game worlds that respond to keyboard inputs in real time, and World Labs [Marble], which generates persistent, editable, reusable 3D spaces from text, images, and other inputs.

新闻背后：直到最近，世界模型 —— 即根据在某个环境中执行的动作来预测该环境未来状态的模型 —— 所能模拟的世界范围还相当有限。2024 年初，OpenAI 的 Sora 1 一经推出，其生成的视频效果就令人惊叹，甚至引发了它是否能算作对真实世界进行建模的世界模型的争论。这些争论为时尚早，因为 Sora 1 的输出即便看起来高度逼真，也并未符合现实世界的物理规律（例如）。然而，它们却预示了新一代模型的到来，例如 Google 的 Genie 2，它能生成可实时响应键盘操作的 3D 视频游戏世界；以及 World Labs 的 [Marble] 项目，它能从文本、图像等输入中，创造出持久、可编辑且可重复使用的 3D 空间。

Why it matters:Runway is among several AI companies that are racing to build models that simulate coherent worlds including objects, materials, lighting, fluid dynamics, and so on. Such models have huge potential value in entertainment and augmented reality but also in industrial and scientific fields, where they can help to design new products and plan for future scenarios.GWM Robotics (aimed at robotics developers) and GWM Avatars (which may be useful in applications like tutoring or customer service) show that Runway's ambitions extend beyond entertainment.

其重要性在于：Runway 是几家正竞相开发能够模拟连贯世界（包括物体、材料、光照、流体动力学等）模型的 AI 公司之一。这类模型不仅在娱乐和增强现实领域潜力巨大，同样在工业和科学领域也价值非凡，可用于设计新产品和规划未来场景。GWM Robotics（面向机器人开发者）和 GWM Avatars（可能在诸如辅导或客户服务等应用中发挥作用）表明，Runway 的抱负已不止于娱乐行业。

We're thinking:The world-model landscape is dividing between models that produce videos with real-time control (Runway GWM Worlds, Google Genie 3, World Labs RTFM) and those that make exportable 3D spaces (World Labs Marble). These approaches target different applications: Real-time interactivity enables training loops in which agents could learn from immediate feedback, while exportable 3D assets feed activities like game development, in which developers may refine and reuse assets across projects.

我们认为，世界模型（World-Model）的格局正朝着两个方向发展：一类模型能生成可实时控制的视频（例如 Runway GWM Worlds、Google Genie 3、World Labs RTFM），另一类则能创建可导出的 3D 空间（例如 World Labs Marble）。这两种技术路径瞄准不同的应用：实时交互能力能为 AI 智能体（AI Agent）打造一个训练回路，使其能从即时反馈中学习；而可导出的 3D 资产则主要用于像游戏开发这样的活动，开发者可以在多个项目中优化并重复使用这些资产。

#### Disney Teams Up With OpenAI

#### 迪士尼联手 OpenAI

Disney, the entertainment conglomerate that owns Marvel, Pixar, Lucasfilm and its own animated classics from101 DalmatianstoZootopia, licensed OpenAI to use its characters in generated videos.

娱乐巨头迪士尼旗下拥有漫威、皮克斯、卢卡斯影业等公司，以及从《101 忠狗》到《疯狂动物城》等一系列经典动画作品。该公司已授权 OpenAI，允许其在生成的视频中使用迪士尼旗下的各类角色。

What's new:Disney and OpenAIsigneda3-year exclusive agreement that lets OpenAI train its Sora social video-gen app to produce 30-second clips that depict characters like Mickey Mouse, Cinderella, Black Panther, and Darth Vader. Open AI will compensate Disney for uses of its characters at an undisclosed rate, and Disney will stream a selection of user-generated videos on its Disney+ streaming network. In addition, Disney bought a $1 billion stake in OpenAI.

最新消息：迪士尼与 OpenAI 签署了一项为期三年的独家协议。根据协议，OpenAI 将能够使用其 Sora 社交视频生成（video-gen）应用，来制作时长 30 秒、包含米老鼠、灰姑娘、黑豹和达斯·维达等经典角色的短片。OpenAI 将为使用这些角色向迪士尼支付费用，具体金额未公开。同时，迪士尼将在其 Disney + 流媒体平台上选播一部分由用户生成的此类视频。此外，迪士尼还斥资 10 亿美元收购了 OpenAI 的部分股权。

How it works:Starting in early 2026, users of the Soraapp— not to be confused with the underlying Soramodel— will be able to generate clips that show more than 200 fictional Disney characters. The deal is not yet final and remains subject to negotiation and board approval.

运作方式：从 2026 年初开始，Sora app 的用户 —— 请注意，这指的是应用程序，而非其背后的 Sora 模型 —— 将能够生成包含超过 200 个虚构迪士尼角色的视频片段。目前这笔交易尚未最终敲定，仍需经过后续谈判并获得董事会批准。

* The agreement does not cover character voices or real-world human actors, and depictions of sex, drugs, alcohol, and interactions with characters owned by other companies are off-limits,The New York Timesreported.

* 据《纽约时报》报道，该协议不涵盖角色声音或真人演员的肖像，并且禁止涉及性、毒品、酒精的描绘，以及与其他公司旗下角色进行互动。

* Disney will be a "major customer" of OpenAI for one year. During that time, it will provide ChatGPT to its employees and use OpenAI's APIs to build tools and products for Disney+.

* 迪士尼将在未来一年内成为 OpenAI 的「主要客户」。在此期间，迪士尼不仅会为员工提供 ChatGPT 使用权限，还将利用 OpenAI 的 API 为 Disney+ 流媒体平台开发各种工具和产品。

* Disney purchased $1 billion worth of OpenAI shares at a $500 billion valuation and received warrants to buy additional shares,The Wall Street Journalreported.

* 据《华尔街日报》报道，迪士尼以 5000 亿美元的估值购买了价值 10 亿美元的 OpenAI 股份，并获得了可购买额外股份的认股权证。

Behind the news:Disney is one of the world's largest media companies by revenue and OpenAI is a clear leader in AI, which makes their alliance especially significant. It serves as a carrot in a carrot-and-stick strategy as Disney and other top entertainment companies are suing AI companies for alleged violations of intellectual property. Top music labels took a similar approach to gain a measure of control over AI startups that focus on music generation.

新闻背后：从营收来看，迪士尼是全球最大的媒体公司之一，而 OpenAI 是人工智能（AI）领域公认的领军者，这使得它们的结盟格外引人注目。这一联盟是「胡萝卜加大棒」策略中的「胡萝卜」—— 此前，迪士尼等顶尖娱乐公司已因涉嫌侵犯知识产权而起诉多家 AI 公司。顶级音乐公司也采取了类似策略，通过合作来争取对那些专注于音乐生成的 AI 初创公司的控制权。

* Even as Disney invests in OpenAI, it is pursuing other AI companies over claims that they violated its copyrights by training models on its products without authorization. Disney recently sent cease-and-desist letters to Google and Character AI, demanding that they stop enabling AI models to generate likenesses of its characters without authorization, and earlier this year it sued image-generation startup Midjourney and Chinese AI startup MiniMax on similar grounds. Google responded byremovingfrom YouTube AI-generated videos that include Disney characters.

* 尽管迪士尼正在投资 OpenAI，但它同时也在就版权问题追诉其他 AI 公司，指控这些公司在未经授权的情况下，利用迪士尼的内容训练 AI 模型。近期，迪士尼向 Google 和 Character AI 发出了停止侵权函，要求其停止提供未经授权生成迪士尼角色形象的功能。今年早些时候，迪士尼还以类似理由起诉了图像生成初创公司 Midjourney 和中国 AI 公司 MiniMax。作为回应，Google 已从 YouTube 平台下架了包含迪士尼角色的 AI 生成视频。

* The world's largest music labels, Sony Music Entertainment, Universal Music Group, and Warner Music Group, recently formed partnerships similar to the Disney-OpenAI deal with music-generation startupsKlay,Udio, and Suno. The record labels agreed to license their recordings for use by AI systems and set up streaming services to allow music fans to generate variations on the licensed recordings. These arrangements settledlawsuitsbrought by the music labels against the AI startups on claims that the AI companies had infringed their copyrights by training models on their recordings without authorization. Some of the lawsuits remain in progress.

* 全球最大的几家唱片公司 —— 索尼音乐娱乐、环球音乐集团和华纳音乐集团 —— 近期与音乐生成初创公司 Klay、Udio 和 Suno 达成了类似迪士尼与 OpenAI 的合作协议。这些唱片公司同意将其录音作品授权给 AI 系统使用，并通过设立流媒体服务平台，允许乐迷在授权作品的基础上生成新的音乐变奏。这一合作安排，解决了这些唱片公司此前对 AI 初创公司提起的诉讼。这些诉讼指控 AI 公司在未经授权的情况下，使用其录音作品训练模型，从而侵犯了版权。不过，其中部分诉讼目前仍在进行中。

* The Disney-OpenAI alliance echoes a 2024partnershipbetween Runway, which competes with OpenAI in video generation, and Lionsgate, producer of blockbuster movie franchises likeThe Hunger Games. Runway fine-tuned its proprietary models on Lionsgate productions to enable the filmmaker to generate new imagery based on its previous work.

* 迪士尼与 OpenAI 的结盟，与 2024 年 Runway 和 Lionsgate 达成的合作如出一辙。Runway 在视频生成领域是 OpenAI 的竞争对手，而 Lionsgate 则是《饥饿游戏》等热门系列电影的出品方。Runway 利用 Lionsgate 的影视作品对其自研模型进行了微调，使得 Lionsgate 能够基于自己过往的作品来生成新的图像。

Why it matters:Video generation is a powerful creative tool, and one that Hollywood would like to have at its disposal. At the same time, generated videos are engaging increasingly larger audiences, raising the question whether it will draw attention and revenue away from Hollywood productions. Disney is embracing a future of custom, user-created media featuring its intellectual property as both a revenue stream in its own right and a hedge against a diminishing audience for theatrical releases and home video. Its investment in OpenAI also lets it share in AI's upside. Cooperation between movie makers and AI companies gives both parties greater latitude to create compelling products and expand the audiences for both entertainment and AI-powered services.

其重要性在于：视频生成是一项强大的创意工具，也是好莱坞希望掌控的技术。与此同时，AI 生成的视频正吸引着日益庞大的观众，这引发了一个疑问：它是否会分散人们对好莱坞大片的关注，并分流其收入？迪士尼正在积极接纳这样一个未来：用户可以利用其知识产权（Intellectual Property）创作定制化媒体内容。这本身构成了一条新的收入渠道，同时也是对影院上映和家庭视频观众减少风险的一种对冲。迪士尼对 OpenAI 的投资，也使其能够分享人工智能（AI）发展的红利。电影制作方与 AI 公司的合作，为双方提供了更大的灵活性与空间，以打造更吸引人的产品，并共同扩大娱乐内容和 AI 驱动服务的受众群体。

We're thinking:Filmmakers and videographers increasinglyunderstand: AI and the arts may seem antithetical at first glance, but they're a natural fit.

我们的想法是：电影制作人和视频创作者们正逐渐认识到，人工智能与艺术，初看似乎水火不容，实则天作之合。

#### OpenAI's Answerto Gemini 3

#### OpenAI 回应 Gemini 3

OpenAI launched GPT-5.2 only weeks after its CEO Sam Altman reportedly issued a "code red" alarm in response to Google's Gemini 3.

在首席执行官 Sam Altman 据称因应 Google 的 Gemini 3 而拉响「红色代码」警报仅几周后，OpenAI 便推出了 GPT-5.2。

What's new:OpenAIaddeda suite of GPT-5.2 models to ChatGPT and its API: GPT-5.2 Pro for high accuracy (name in the API:gpt-5.2-pro), GPT-5.2 Thinking for multi-step tasks like coding and planning (gpt-5.2), and GPT-5.2 Instant for less-involved tasks (gpt-5.2-chat-latest). The company touts the new models as time savers in professional tasks like producing spreadsheets, presentations, or code.

最新消息：OpenAI 为 ChatGPT 及其 API 推出了一系列 GPT-5.2 模型，包括：主打高精度的 GPT-5.2 Pro（API 名称：gpt-5.2-pro）、擅长处理编码和规划等多步骤任务的 GPT-5.2 Thinking（gpt-5.2），以及应对简单任务的 GPT-5.2 Instant（gpt-5.2-chat-latest）。OpenAI 表示，这些新模型能帮助用户在处理制作电子表格、演示文稿或编写代码等专业工作时，有效提升效率，节省时间。

* Input/output:Text and images in (up to400,000tokens), text out (up to 128,000 tokens)

* 输入 / 输出：文本和图像（最多 400,000 Token），文本输出（最多 128,000 Token)

* Knowledge cutoff:August 31, 2025

* 知识截止时间：2025 年 8 月 31 日

* Performance:Outstanding results in some reasoning benchmarks;strong results across coding, math, reasoning benchmarks

*  性能：在部分推理基准测试中表现卓越；在编码、数学及推理等多项基准测试中均展现出强大实力。

* Features:Adjustable reasoning levels including new x-high (extra high) level, reasoning summaries, distillation allowed, tool use via Responses API, context summarization to extend available context via API

* 功能：支持可调节的推理级别，新增了 x-high（特高）级别；提供推理过程摘要；允许进行知识蒸馏；可通过 Responses API 调用外部工具；并具备上下文总结能力，通过 API 扩展可用上下文长度。

* Availability/price:Via ChatGPT subscription (Plus, Pro, Go, Business, Enterprise) and API. GPT-5.2 Thinking and Instant: $1.75/$0.175/$14 per million input/cached/output tokens. GPT-5.2 Pro: $21/$168 per million input/output tokens.

*  **可用性与价格**：可通过 ChatGPT 订阅服务（Plus，Pro，Go，Business，Enterprise）和 API 获取。具体定价如下：
  *  **GPT-5.2 Thinking 与 Instant 模型**：输入 Token 为每百万个 1.75 美元，缓存 Token 为每百万个 0.175 美元，输出 Token 为每百万个 14 美元。
  *  **GPT-5.2 Pro 模型**：输入 Token 为每百万个 21 美元，输出 Token 为每百万个 168 美元。

* Undisclosed:Parameter counts, architectures, training data and methods

* 未披露：参数量、模型架构、训练数据及方法

How it works:OpenAI revealed fewdetailsabout GPT-5.2's architecture and training butsaidit made "improvements across the board, including in pretraining."

工作原理：OpenAI 并未透露太多关于 GPT-5.2 架构和训练的具体细节，不过他们表示，新模型实现了「全方位的性能提升，其中也包括预训练（pretraining）阶段。」

* API users canadjustGPT-5.2's reasoning across 5levels: none, low, medium, high, and x-high.

* API 用户可按五个级别调节 GPT-5.2 的推理能力：无、低、中、高、超高（x-high）。

* For tasks that exceed the input context limit, GPT-5.2 Pro and GPT-5.2 Thinkingoffera Responses/compact API endpoint that compresses lengthy conversations rather than truncating them.

* 对于超出输入上下文限制的任务，GPT-5.2 Pro 和 GPT-5.2 Thinking 提供了一个名为 `Responses/compact` 的 API 端点，用于压缩冗长的对话内容，而非直接将其截断。

Performance:According to the ARC leaderboards, GPT-5.2-Pro set new states of the art on ARC-AGI-1 and AGI-ARC-2 (abstract visual puzzles). It remains neck-and-neck with competitors on other independent tests.

性能：根据 ARC 排行榜，GPT-5.2-Pro 在 ARC-AGI-1 和 AGI-ARC-2（抽象视觉谜题）上创造了新的最佳成绩。它在其他独立测试中与竞争对手依然并驾齐驱。

* On ARC-AGI-2 (abstract visual puzzles designed to resist memorization), GPT-5.2 Pro set to high reasoning (54.2 percent pass@2, $15.72 per task)outperformedGPT-5.2 Thinking set to x-high (52.9 percent pass@2, $1.90 per task). That's roughly three times the accuracy at a lower cost than GPT-5.1 Thinking set to high (17.6 percent pass@2, $17.6 per task).

* 在 ARC-AGI-2（一组旨在防止死记硬背的抽象视觉推理谜题）上，启用高推理模式的 GPT-5.2 Pro（pass@2 通过率 54.2%，单任务成本 15.72 美元）的表现，甚至超过了启用超高推理模式的 GPT-5.2 Thinking（pass@2 通过率 52.9%，单任务成本 1.90 美元）。若是与更早的、启用高推理模式的 GPT-5.1 Thinking（pass@2 通过率 17.6%，单任务成本 17.6 美元）相比，GPT-5.2 Pro 不仅将准确率提升了大约三倍，同时成本也更低。

* On the simpler ARC-AGI-1, GPT-5.2 Pro set to x-high set state-of-the-art at (90.5 percent pass@2, $11.65 per task) became the first model to exceed 90 percent, ahead of Gemini 3 Deep Think Preview (87.5 percent pass@2, estimated $44.26 per task) and Claude Opus 4.5 set to thinking with 64,000 tokens of context (80 percent pass@2, $1.47 per task).

* 在相对简单的 ARC-AGI-1 基准测试中，GPT-5.2 Pro 在 x-high 设置下取得了最先进的成绩（pass@2 通过率 90.5%，单任务成本 11.65 美元），成为首个通过率突破 90% 的模型。其表现领先于 Gemini 3 Deep Think Preview（pass@2 通过率 87.5%，单任务成本约 44.26 美元）以及上下文窗口设置为 64,000 Token 的 Claude Opus 4.5 思考模式（pass@2 通过率 80%，单任务成本 1.47 美元）。

* On the Artificial Analysis' Intelligence Index, a weighted average of 10 benchmarks, GPT-5.2 set to x-highscored73, tying Gemini 3 Pro Preview and beating Claude Opus 4.5 (70) and GPT-5.1 set to high reasoning (70). To complete this test, GPT-5.2 set to x-high ($1,294) cost less than Claude Opus 4.5 ($1498) but more than Gemini 3 Pro Preview set to high reasoning ($1,201). It alsotiedGemini 3 Pro Preview set to high(62) on Artificial Analysis's Coding Index (an average of LiveCodeBench, SciCode, Terminal-Bench Hard), ahead of Claude Opus 4.5 (60).

* 在 Artificial Analysis 的 Intelligence Index（人工智能指数，一个 10 项基准测试的加权平均值）上，GPT-5.2 在 x-high 模式下取得了 73 分，与 Gemini 3 Pro Preview 并列，并领先于 Claude Opus 4.5（70 分）以及在 high reasoning（高推理）模式下的 GPT-5.1（70 分）。完成此项测试的成本方面，x-high 模式的 GPT-5.2（1294 美元）低于 Claude Opus 4.5（1498 美元），但高于 high reasoning 模式的 Gemini 3 Pro Preview（1201 美元）。此外，在 Artificial Analysis 的 Coding Index（编码指数，取 LiveCodeBench、SciCode 和 Terminal-Bench Hard 的平均分）上，GPT-5.2 也与 high 模式的 Gemini 3 Pro Preview 同获 62 分，领先于 Claude Opus 4.5（60 分）。

* GPT-5.2 set to x-high (99 percent)ledAIME 2025 (competitive math), ahead of GPT-5.1 Codex and Gemini 3 Pro Preview set to high (both 96 percent).

* GPT-5.2 在 x-high（极高）性能设置下，于 AIME 2025（美国数学邀请赛，一项竞争性数学竞赛）中取得了 99% 的领先成绩，超过了同样设置为 high（高）性能模式、成绩均为 96% 的 GPT-5.1 Codex 和 Gemini 3 Pro Preview。

Behind the news:GPT-5.2 arrived as OpenAI faces heightened competitive pressure. CEO Sam Altman haddeclareda "code-red" emergency — a level of alarm typically related to smoke and fire in a hospital — on December 1, soon after Google launched Gemini 3.He instructed employees to delay plans to add advertisements to ChatGPT and instead focus on improving themodels. OpenAI executivesdenythat GPT-5.2 was rushed.

新闻背后：GPT-5.2 登场之际，正值 OpenAI 面临日益加剧的竞争压力。首席执行官 Sam Altman 在谷歌发布 Gemini 3 后不久，于 12 月 1 日拉响了「红色代码」警报（一种通常与医院内烟雾或火灾相关的最高级别警报）。他指示员工推迟为 ChatGPT 添加广告的计划，转而集中精力提升模型性能。OpenAI 高管否认 GPT-5.2 是仓促推出的。

Why it matters:GPT-5.2's gains in computational efficiency are stark. One year ago, achieving 88 percent on ARC-AGI-1costroughly $4,500 per task. GPT-5.2 Pro achieves 90.5 percent at around $12 per task, roughly 390 times less. Extended reasoning is becoming dramatically more accessible.

其重要性在于：GPT-5.2 在计算效率方面取得了巨大飞跃。一年前，在 ARC-AGI-1 基准测试上达到 88% 的准确率，每个任务大约需要花费 4500 美元。而 GPT-5.2 Pro 以每个任务仅约 12 美元的成本，就实现了 90.5% 的准确率，成本降至原来的约 1/390。这意味着，复杂的扩展推理能力正变得前所未有的触手可及。

We're thinking:Technical approaches that aren't economically feasible today, say running hundreds of reasoning attempts per problem or deploying thousands of reasoning-heavy agents, are on track to become surprisingly affordable within a few years.

我们认为：目前因成本过高而难以实现的技术路径，例如针对每个问题运行数百次推理尝试，或者部署成千上万个高推理负载的智能体（AI Agent），预计在几年内，其成本将大幅下降，变得出人意料地低廉。

#### Adapting LLMs toAny Sort of Data

#### 让大语言模型驾驭任意数据

Enabling a pretrained large language model to process a data type other than text (say, images), possibly in a specialized domain (say, radiology), typically requires thousands to millions of examples that pair the other data (perhaps x-rays) with text. Researchers devised an approach that requires a small number of examples.

要让一个预训练好的大语言模型（Large Language Model）去处理文本之外的数据类型（比如图像），尤其是在某个专业领域（例如放射学），通常需要准备成千上万甚至数百万个配对数据 —— 比如将 X 光图像与对应的文字描述一一对应。研究人员现在开发出了一种新方法，只需要很少的示例就能实现。

What's new:Sample-Efficient Modality Integration(SEMI) enables an LLM to process any input data type in any specialized domain based on as few as 32 examples. Given a suitable, pre-existing encoder, a single projector plus a dynamic complement of LoRA adapters translates input embeddings into the LLM's embedding space. Osman Batur İnce developed the method with colleagues at University of Edinburgh, Instituto de Telecomunicações, Instituto Superior Técnico, Universidade de Lisboa, and Unbabel, a machine translation company.

最新进展：样本高效模态集成（Sample-Efficient Modality Integration，SEMI）技术，仅需少至 32 个示例，就能让一个大语言模型（LLM）处理任何专业领域中的任意输入数据类型。该方法利用一个合适的、预先训练好的编码器，配合一个单一的投影器以及一组动态配置的 LoRA 适配器，将输入数据的嵌入表示映射到大语言模型的嵌入空间中。这项技术由 Osman Batur İnce 与爱丁堡大学（University of Edinburgh）、Instituto de Telecomunicações、Instituto Superior Técnico、里斯本大学（Universidade de Lisboa）以及机器翻译公司 Unbabel 的同事们共同研发。

Key insight:Typically, adapting a large language model (LLM) to accept multimodal inputsrequirestraining a separate projector for each data type and/or domain. But the ability to adapt to unfamiliar input data types/domains can be considered a general, learnable skill. A projector can learn this skill by training on data types/domains for which examples are plentiful. Then LoRA adapters can adjust it for new data types/domains for which few examples are available. Better yet, a separate network can generate LoRA adapters that adjust the projector to new data types/domains as needed.

关键洞察：通常，为了让大语言模型（LLM）能够处理多模态输入，我们需要为每一种数据类型或领域训练一个独立的投影器。然而，适应陌生输入数据类型或领域的能力，本身可以看作是一种通用且可学习的技能。投影器可以通过在数据样本充足的类型或领域上进行训练来掌握这项技能。之后，对于只有极少样本可用的新数据类型或领域，我们可以利用 LoRA 适配器对这个投影器进行微调。更进一步，我们还可以训练一个独立的网络，让它根据需要动态生成 LoRA 适配器，从而使投影器能够灵活适配各种新的数据类型或领域。

How it works:The authors aimed to connect pre-existing, pretrained domain-specific encoders (CLIP for images, CLAP for audio, VideoCLIP-XL for video, and others) to a pretrained large language model (Llama 3.1 8B). To that end, they trained a projector (a vanilla neural network) plus a LoRA generator (a network made up of a single attention layer).

工作原理：作者的目标是将一系列现成的、预训练的特定领域编码器（例如，处理图像的 CLIP、处理音频的 CLAP、处理视频的 VideoCLIP-XL 等）接入一个预训练的大语言模型（Large Language Model，LLM）—— Llama 3.1 8B。为了实现这一目标，他们训练了一个投影层（一个基础神经网络）以及一个 LoRA 生成器（Low-Rank Adaptation generator，一个仅由单个注意力层构成的网络）。

* The authors trained the projector using datasets (around 50,000 to 600,000 examples) that paired text withimages,audio, andvideo. They connected the projector to the LLM, kept the LLM frozen, and minimized the difference between LLM's outputs and ground-truth text.

* 作者们使用了一个包含文本与图像、音频、视频配对样本的数据集（规模大约在 5 万到 60 万例之间）来训练一个投影模块。他们将这个投影模块与大语言模型（LLM）相连，同时保持大语言模型的参数固定不变，并通过训练最小化大语言模型的输出与文本标准答案之间的差异。

* They froze the projector and trained the LoRA generator to produce LoRA adapters based on a description of the task at hand and 128 examples for each data type/domain involved drawn from other datasets of text paired withimages,audio, andvideo. To simulate a wider variety of data types/domains, given a subset of 128 examples, they applied a mathematical transformation to the encoder's output embeddings while preserving the geometric relationships between the vectors, such as their relative distances and angles.

* 他们冻结了投影器，并训练了一个 LoRA 生成器（LoRA Generator）。这个生成器的目标是：根据当前任务的描述，以及从其他图文、音文、视频文配对数据集中，为任务所涉及的每一种数据类型或领域各抽取的 128 个示例，来生成对应的 LoRA 适配器（LoRA Adapters）。为了模拟更多样化的数据类型或领域，在训练过程中，每当取用一组 128 个示例时，他们会对编码器输出的嵌入向量进行一种数学变换。这种变换的关键在于，它保持了向量之间的几何关系（如相对距离和角度）不变，从而确保了数据的原始语义结构在变换后得以保留。

* At inference, the authors used other pretrained encoders to embed data types/domains the system hadn't been trained on (for example,MolCAfor graphs of molecules). Given a few examples that paired a particular data type/domain with text descriptions, the LoRA generator produced an appropriate adapter.

* 在推理阶段，作者使用了其他预训练的编码器来处理系统未曾训练过的数据类型或领域（例如，处理分子图数据的 MolCA）。只需提供少量将某种特定数据类型 / 领域与文本描述关联起来的示例，LoRA 生成器就能产生一个相应的适配器。

* To further improve performance, having applied the adapter, they fine-tuned the projector with each adapter using the same subset of examples, keeping other weights frozen.

* 为了进一步提升性能，在应用适配器（Adapter）后，他们使用相同的示例子集，针对每个适配器对其投影器（projector）进行了微调，同时保持其他权重冻结。

Results:The authors compared SEMI to training a projector from scratch; fine-tuning their projector; and fine-tuning their projector with a bespoke LoRA adapter using astronomical images from their own dataset,satellite images,IMU sensor data, andgraphs of molecular structuresplus appropriate pre-existing encoders. They measured performance using metrics that include CIDEr (higher is better), which gauges how well a generated caption matches various human-written ones.

结果：作者将 SEMI 与几种方法进行了对比：从头训练一个投影头、微调他们已有的投影头，以及使用一个定制的 LoRA 适配器并搭配特定数据（包括他们数据集中的天文图像、卫星图像、IMU 传感器数据和分子结构图）及相应的预训练编码器来微调该投影头。他们采用了一系列指标来评估性能，其中包括 CIDEr（分数越高越好），该指标用于衡量模型生成的描述与多个人工撰写描述之间的匹配程度。

* SEMI beat all baselines in all tests across all numbers of examples (from 32 to the complete datasets of 2,500 to 26,000 examples).

* 在所有测试中，无论示例数量多少（从 32 个到规模为 2,500 至 26,000 的完整数据集），SEMI 的表现均优于所有基线模型。

* For instance, on astronomical images with 32 examples, SEMI achieved over 215 CIDEr, while the next-best method achieved 105.

* 例如，在仅有 32 个示例的天文图像数据集上，SEMI 模型的 CIDEr 得分超过了 215，而表现次优的方法得分仅为 105。

* The sole exception: In tests on graphs of molecular structures, with a few thousand examples, the fine-tuned projector outperformed SEMI.

* 唯一的例外：在针对分子结构图、包含数千个样本的测试中，经过微调的投影头（fine-tuned projector）性能超过了 SEMI。

Why it matters:Large language models are of limiteduse in many technical fields because little text-paired data is available and building large text-paired datasets is expensive. This work could accelerate adoption of AI in such fields by taking advantage of knowledge in data-rich domains to bootstrap AI training in data-poor ones.

其重要性在于：大语言模型在许多技术领域中的应用有限，主要原因在于缺乏现成的文本配对数据，且构建大规模数据集成本高昂。这项研究的意义在于，它能够利用数据丰富领域积累的知识，来助力数据贫乏领域的人工智能（AI）训练，从而加速 AI 技术在后一类领域中的普及和应用。

We're thinking:For AI models to generalize to novel data types, they usually need to be trained on diverse, high-quality data. To that end, it's helpful to squeeze more learning out of less data.

我们的思路是：AI 模型要想泛化到全新的数据类型，通常需要接受多样化、高质量数据的训练。为此，一个关键点在于如何从有限的数据中汲取更多知识。
