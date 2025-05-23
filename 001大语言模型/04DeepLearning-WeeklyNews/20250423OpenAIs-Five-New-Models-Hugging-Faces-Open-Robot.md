## 20250423OpenAIs-Five-New-Models-Hugging-Faces-Open-Robot

[OpenAI's Five New Models, Hugging Face’s Open Robot, U.S. Tightens Grip on AI Chips, and more...](https://www.deeplearning.ai/the-batch/issue-298/)

Dear friends,

Even though I'm a much better Python than JavaScript developer，with AI assistance，I've been writing a lot of JavaScript code recently. AI-assisted coding is making specific programming languages less important，even though learning one is still helpful to make sure you understand the key concepts. This is helping many developers write code in languages we're not familiar with，which lets us get code working in many more contexts!

尽管我是一名 Python 开发者，且水平远超 JavaScript 开发者，但在 AI 的帮助下，我最近一直在写很多 JavaScript 代码。AI 辅助编码正在降低特定编程语言的重要性，尽管学习一门语言仍有助于确保你理解关键概念。这正在帮助许多开发者使用我们不熟悉的语言编写代码，从而使我们能够在更多场景下运行代码！

My background is in machine learning engineering and back-end development，but AI-assisted coding is making it easy for me to build front-end systems（the part of a website or app that users interact with）using JavaScript（JS）or TypeScript（TS），languages that I am weak in. Generative AI is making syntax less important，so we can all simultaneously be Python，JS，TS，C++，Java，and even Cobol developers. Perhaps one day，instead of being 「Python developers」or「C++ developers,」many more of us will just be「developers」!

我之前主要从事机器学习工程和后端开发工作，但有了 AI 辅助编码的加持，我能轻松搞定前端系统（也就是用户直接看到和操作的网站或应用界面），即使对于我不太熟悉的 JavaScript（JS）或 TypeScript（TS）语言也不在话下。生成式 AI（Generative AI）让编程语法的重要性降低了，这意味着我们每个人都有可能同时胜任 Python、JS、TS、C++、Java，甚至 Cobol 的开发工作。或许未来某天，我们很多人不再被贴上「Python 开发者」或「C++ 开发者」这样的标签，而只是简单地被称为「开发者」！

But understanding the concepts behind different languages is still important. That's why learning at least one language like Python still offers a great foundation for prompting LLMs to generate code in Python and other languages. If you move from one programming language to another that carries out similar tasks but with different syntax — say，from JS to TS，or C++ to Java，or Rust to Go — once you've learned the first set of concepts，you'll know a lot of the concepts needed to prompt an LLM to code in the second language.（Although TensorFlow and PyTorch are not programming languages，learning the concepts of deep learning behind TensorFlow will also make it much easier to get an LLM to write PyTorch code for you，and vice versa!） In addition，you'll be able to understand much of the generated code（perhaps with a little LLM assistance).

但理解不同语言背后的概念仍然很重要。这就是为什么学习至少一门像 Python 这样的语言，仍然能为提示大语言模型（LLM）生成 Python 或其他语言的代码打下坚实的基础。如果你从一种编程语言转向另一种执行类似任务但语法不同的语言 —— 比如从 JS 到 TS，或者从 C++ 到 Java，或者从 Rust 到 Go —— 一旦你掌握了第一门语言的概念，你就会了解许多必要的概念，从而能够提示大语言模型用第二门语言编写代码。（虽然 TensorFlow 和 PyTorch 不是编程语言，但理解 TensorFlow 背后的深度学习概念也会让你更容易让大语言模型为你编写 PyTorch 代码，反之亦然！）此外，你将能够理解大部分生成的代码（或许只需一点点大语言模型的协助）。

Different programming languages reflect different views of how to organize computation，and understanding the concepts is still important. For example，someone who does not understand arrays，dictionaries，caches，and memory will be less effective at getting an LLM to write code in most languages.

不同的编程语言体现了不同的计算组织方式，而理解这些概念仍然非常重要。例如，如果一个人不理解数组、字典、缓存和内存等概念，那么在使用大语言模型（LLM）生成大多数编程语言的代码时，其效率就会比较低。

Similarly，a Python developer who moves toward doing more front-end programming with JS would benefit from learning the concepts behind front-end systems. For example，if you want an LLM to build a front end using the React framework，it will benefit you to understand how React breaks front ends into reusable UI components，and how it updates the DOM data structure that determines what web pages look like. This lets you prompt the LLM much more precisely，and helps you understand how to fix issues if something goes wrong. Similarly，if you want an LLM to help you write code in CUDA or ROCm，it helps to understand how GPUs organize compute and memory.

同样，一个 Python 开发者如果想更多地进行使用 JS 的前端编程，学习前端系统背后的概念将会很有帮助。例如，如果你想让一个大语言模型（LLM）使用 React 框架构建一个前端，那么理解 React 如何将前端分解成可重用的 UI 组件，以及它如何更新决定网页外观的 DOM 数据结构，对你非常有益。因为理解了这些，你就能更精确地给 LLM 提示，并且也能帮助你理解如果出了问题该如何修复。同理，如果你想让 LLM 帮助你用 CUDA 或 ROCm 编写代码，了解 GPU 如何组织计算和内存也会有帮助。

Just as people who are fluent in multiple human languages can communicate more easily with other people，LLMs are making it easier for developers to build systems in multiple contexts. If you haven't already done so，I encourage you to try having an LLM write some code in a language you'd like to learn but perhaps haven't yet gotten around to，and see if it helps you get some new applications to work.

正如精通多种人类语言的人们可以更容易地与其他人交流一样，大语言模型（LLMs）正在让开发者更容易在多种上下文中构建系统。如果你还没有这样做过，我鼓励你尝试让大语言模型用你想学习但可能还没有开始学习的语言编写一些代码，看看它是否能帮助你让一些新的应用程序工作起来。

Keep building!

Andrew

### News

#### OpenAI Launches Cost-Effective Alternatives

OpenAI 推出更经济实惠的替代方案

OpenAI refreshed its roster of models and scheduled the largest，most costly one for removal.

OpenAI 更新了其模型列表，并计划移除其中规模最大、成本最高的一个模型。

What's new: OpenAI introduced five new models that accept text and images inputs and generate text output. Their parameter counts，architectures，training datasets，and training methods are undisclosed. The general-purpose GPT-4.1，GPT-4.1 mini，and GPT-4.1 nano are available via API only. The reasoning models o3 and o4-mini, are available via API to qualified developers as well as users of ChatGPT Plus，Pro，and Team，and soon ChatGPT Enterprise and ChatGPT Education. The company will terminate GPT-4.5 — which it introduced as a research preview in late February — in July.

新变化：OpenAI 推出了五款新的模型，它们可以接受文本和图像输入，并生成文本输出。这些模型的参数数量、架构、训练数据集以及训练方法都尚未对外公布。通用型的 GPT-4.1、GPT-4.1 mini 和 GPT-4.1 nano 仅通过 API 提供。专注于推理的 o3 和 o4-mini 模型则通过 API 向符合条件的开发者以及 ChatGPT Plus、Pro 和 Team 用户开放，很快也将对 ChatGPT Enterprise 和 ChatGPT Education 用户提供。该公司将于七月移除 GPT-4.5 —— 该模型于二月下旬作为研究预览版推出。

GPT-4.1 family: In an odd turn of version numbers，the GPT-4.1 models are intended to be cost-effective equivalents to GPT-4.5 and updates to GPT-4o. They accept inputs of up to 1 million tokens（compared to GPT-4.5's and GPT-4o's 128,000 tokens).

GPT-4.1 家族：版本号有些出人意料，GPT-4.1 模型的目标是成为 GPT-4.5 的经济实惠替代品，同时也是对 GPT-4o 的升级。它们可以接受多达 100 万个 token 的输入（相比之下，GPT-4.5 和 GPT-4o 的输入上限是 128,000 个 token）。

1 Prices: GPT-4.1 costs $2/$8 per million input/output tokens. GPT-4.1 mini costs $0.40/$1.60 per million input/output tokens. GPT-4.1 nano costs $0.10/$0.40 per million input/output tokens. A 75 percent discount applies to cached input tokens.

价格：GPT-4.1 的价格是每百万输入 Token 2 美元，每百万输出 Token 8 美元。GPT-4.1 mini 的价格是每百万输入 Token 0.40 美元，每百万输出 Token 1.60 美元。GPT-4.1 nano 的价格是每百万输入 Token 0.10 美元，每百万输出 Token 0.40 美元。对于缓存的输入 Token，可享受 75% 的折扣。

2 GPT-4.1 performance: GPT-4.1 surpassed GPT-4o on most benchmarks tested by OpenAI，with notable improvement on coding tasks. It significantly outperformed GPT-4o，o1，and o3-mini on SWE-bench Verified (real-world coding skills), MultiChallenge (following instructions in multi-turn conversations），MMMU（multimodal reasoning），and Video-MME (long-context understanding).

GPT-4.1 表现：在 OpenAI 测试的大多数基准测试中，GPT-4.1 超越了 GPT-4o，尤其在编码任务上表现突出。它在多项测试中显著领先于 GPT-4o、o1 和 o3-mini，包括：SWE-bench Verified （真实世界编码技能）、MultiChallenge （在多轮对话中遵循指令）、MMMU （多模态推理）以及 Video-MME （长上下文理解）。

3 GPT-4.1 mini performance: The smaller GPT-4.1 mini generally surpassed GPT-4o mini on benchmarks tested by OpenAI. On MultiChallenge and MMMU，GPT-4.1 mini outperformed the full-size GPT-4o.

GPT-4.1 mini 性能：GPT-4.1 mini 在 OpenAI 测试的基准测试中，性能普遍优于 GPT-4o mini。在 MultiChallenge 和 MMMU 测试中，GPT-4.1 mini 甚至超越了 GPT-4o。

o3 and o4-mini: These models update o1 and o3-mini，respectively. They have input limits of 200,000 tokens and can be set to low-，medium-，or high-effort modes to process varying numbers of reasoning tokens，which are hidden from users. Unlike their predecessors，they were fine-tuned to decide when and how to use the tools，including web search，code generation and execution，and image editing.

o3 和 o4-mini：这些模型分别更新了 o1 和 o3-mini。它们拥有 200,000 个 token 的输入限制，并可设置为低、中或高努力模式，以便处理数量不等的推理 token，这些 token 对用户是隐藏的。与它们的前代不同，这些模型经过微调，能够决定何时以及如何使用各种工具，包括网络搜索、代码生成和执行以及图像编辑。

1 Prices: API access to o3 costs $10/$40 per million input/output tokens. o4-mini costs $1.10/$4.40 per million input/output tokens. Both offer a 75 percent discount for cached input tokens.

价格：o3 的 API 访问费用为每百万输入 tokens $10，每百万输出 tokens $40。o4-mini 的费用为每百万输入 tokens $1.10，每百万输出 tokens $4.40。两者都对已缓存的输入 tokens 提供 75% 的折扣。

2 Access limits: Developers whose usage puts them in rate-limit tiers 1 through 3 must verify their identities to use o3 via the API（higher-usage tiers 4 and 5 are exempt). OpenAI says this limitation is intended to prevent abuse.

访问限制：使用量处于速率限制层级 1 到 3 的开发者，必须验证其身份才能通过 API 使用 o3（更高使用量层级 4 和 5 不受此限制）。OpenAI 表示，此限制是为了防止滥用。

3 Image processing: o3 and o4-mini can apply chains of thought to images — a first for OpenAI's reasoning models. For example，users can upload a diagram with instructions to interpret it，and the models will use chains of thought and tools to process the diagram.

图像处理：o3 和 o4-mini 可以将思维链（chains of thought）应用于图像 —— 这是 OpenAI 推理模型（reasoning models）的首次尝试。例如，用户可以上传带有解释说明的图表，模型将使用思维链和工具来理解和分析图表。

4 o3 performance: o3 set the state of the art in several benchmarks including MultiChallenge，MMMU，MathVista，and HLE. It generally outperformed o1 in tests performed by OpenAI. OpenAI didn't document o3's long-context performance，but in independent tests by Fiction.Live，it achieved nearly perfect accuracy with contexts up to 120,000 tokens.

o3 性能：o3 在 MultiChallenge、MMMU、MathVista 和 HLE 等多个基准测试中达到了最先进水平。在 OpenAI 进行的测试中，它的性能普遍优于 o1。OpenAI 没有记录 o3 的长上下文性能，但在 Fiction.Live 进行的独立测试中，它在高达 120,000 token 的长上下文中实现了近乎完美的准确性。

5 o4-mini performance: o4-mini generally outperformed o3-mini in tests performed by OpenAI. It outperformed most competing models in Fiction.Live's tests of long-context performance.

o4-mini 性能：o4-mini 在 OpenAI 进行的测试中表现通常优于 o3-mini。在 Fiction.Live 针对长上下文性能的测试中，它也优于大多数竞争模型。

Behind the news: Late last year，OpenAI introduced o1，the first commercial model trained via reinforcement learning to generate chains of thought. Within a few months，DeepSeek，Google，and Anthropic launched their respective reasoning models DeepSeek-R1, Gemini 2.5 Pro，and Claude 3.7 Sonnet. OpenAI has promised to integrate its general-purpose GPT-series models and o-series reasoning models，but they remain separate for the time being.

新闻背景：去年底，OpenAI 推出了 o1，这是第一个通过强化学习训练生成思维链的商业模型。几个月内，DeepSeek，Google 和 Anthropic 分别推出了他们的推理模型 DeepSeek-R1，Gemini 2.5 Pro 和 Claude 3.7 Sonnet。OpenAI 承诺整合其通用型 GPT 系列模型和 o 系列推理模型，但目前它们仍保持独立。

Why it matters: GPT-4.5 was an exercise in scale，and it showed that continuing to increase parameter counts and training data would yield ongoing performance gains. But it wasn't widely practical on a cost-per-token basis. The new models，including those that use chains of thought and tools，deliver high performance at lower prices.

为什么它很重要：GPT-4.5 是在模型规模方面的一次尝试，它表明持续增加参数数量和训练数据能带来持续的性能提升。但从每个 token 的成本来看，它并没有广泛的实用性。新的模型，包括那些利用思维链（chain of thought）和工具（tools）的模型，则能在更低的价格下提供高性能。

We're thinking: Anthropic is one of OpenAI's key competitors，and a large fraction of the tokens it generates（via API）are for writing code，a skill in which it is particularly strong. OpenAI's emphasis on models that are good at coding could boost the competition in this area!

我们认为，Anthropic 是 OpenAI 的主要竞争对手之一，并且通过 API 生成的大部分 token 都被用于编写代码，这是它非常擅长的一项技能。OpenAI 对擅长编码的模型的重视可能会加剧这一领域的竞争！

#### Hugging Face Rolls Out Open Robot

Hugging Face 推出开源机器人

Hugging Face has made a name by providing open AI models. Now it's providing an open robot.

Hugging Face 以提供开放的 AI 模型而闻名。现在，它正在推出一款开源机器人。

What's new: Hugging Face acquired the French company Pollen Robotics for an undisclosed price. It plans to offer Pollen's Reachy 2，a robot that runs on code that's freely available under an Apache 2.0 license，for $70,000.

最新动态：Hugging Face 收购了法国公司 Pollen Robotics，具体金额未对外披露。Hugging Face 计划以 70,000 美元的价格提供 Pollen 公司的机器人 Reachy 2。这款机器人运行的代码在 Apache 2.0 许可下免费提供。

How it works: Reachy 2 has two arms，gripper hands，and a wheeled base（optional). It's designed primarily for education and research in human-robot interaction in real-world settings.

工作原理：Reachy 2 拥有两个手臂、带夹持器的手，以及一个轮式底座（可选）。它主要设计用于在现实世界环境中进行人机交互的教育和研究。

1 Reachy 2 is programmable in Python and runs models from Hugging Face's LeRobot library.

Reachy 2 可以用 Python 编程，并运行 Hugging Face 的 LeRobot 库中的模型。

2 It runs control software locally on a SolidRun Bedrock V3000 (a PC based on an AMD Ryzen Embedded V3000 processor) and processes AI in the cloud or on a local server.

它在本地的 SolidRun Bedrock V3000 （一个基于 AMD Ryzen Embedded V3000 处理器的 PC）上运行控制软件，并在云端或本地服务器上处理 AI 任务。

3 The robot responds to VR controllers including Meta Quest 2 and 3 as well as Pollen's VR app.

机器人支持 VR 控制器操作，包括 Meta Quest 2 和 3，以及 Pollen 开发的 VR 应用。

4 Its head senses the visual environment using a pair of cameras equipped with global shutters to capture fast-changing events and measures distances via an optical sensor. Its antennas are outfitted with microphones to capture sounds，and its torso senses distances using a depth camera. The base includes a lidar sensor to aid navigation.

它的头部配备了一对带有全局快门的相机，用于感知视觉环境和捕捉快速变化的事件；同时通过光学传感器测量距离。它的天线上安装了麦克风来捕捉声音，躯干则配备了深度相机来感知距离。底座集成了一个激光雷达传感器，用于辅助导航。

5 The body features 3D joints in the neck and wrists and 2D joints in the shoulders and elbows. Each arm can lift objects of up to 3 kilograms.

身体部分，颈部和手腕采用了三维（3D）关节，而肩部和肘部则是二维（2D）关节。每只手臂能够举起最重 3 公斤的物体。

6 A rechargeable，24 volt battery provides around 10 hours of battery life.

机器人由一块可充电的 24 伏电池供电，充满电后大约可持续工作 10 小时。

Behind the news: Last year，Remi Cadene，who worked on Tesla's Optimus, joined Hugging Face to lead robotics projects. In May，he and his team rolled out the LeRobot open source robotics code library，which provides pretrained models，datasets，and simulators for reinforcement learning and imitation learning. In November，Nvidia announced a collaboration with Hugging Face to accelerate LeRobot's data collection，training，and verification.

新闻背景：去年，曾在 Tesla Optimus 项目工作的 Remi Cadene 加入 Hugging Face，领导机器人项目。五月，他和团队推出了 LeRobot 开源机器人代码库，为强化学习和模仿学习提供预训练模型、数据集和模拟器。十一月，Nvidia 宣布与 Hugging Face 合作，加速 LeRobot 的数据收集、训练和验证。

Why it matters: Hugging Face's acquisition of Pollen reflects an industry-wide investment in robots，notably humanoid robots，whose prices have been falling. Nvidia CEO Jensen Huang has called AI-enabled robotics a「multi-trillion dollar」opportunity.

这件事为何重要：Hugging Face 收购 Pollen 的举动，反映出整个行业对机器人领域的投入正在增加，特别是价格持续下降的人形机器人。Nvidia 的 CEO Jensen Huang 就曾表示，支持 AI 的机器人是一个「数万亿美元」的市场机会。

We're thinking: AI-enabled robots are marching slowly toward what we hope will be breakthrough applications. Open-source systems are an important part of the trend!

我们正在思考：得益于人工智能的加持，机器人正缓慢而坚定地迈向我们所期望的突破性应用。值得一提的是，开源系统在这股浪潮中扮演着重要角色！

#### U.S. Tightens Grip on AI Chips

美国强化对 AI 芯片的管制

The U.S. government escalated its long-running effort to block China's access to cutting-edge AI hardware.

美国政府升级了其长期行动，以阻止中国获取尖端 AI 硬件。

What's new: The White House announced that future shipments of Nvidia H20s，AMD MI308s，or equivalent chips to China would require a license. Concurrently，the United States Congress launched an investigation into whether chip vendor Nvidia violated earlier export rules.

最新消息：白宫宣布，未来向中国运送 Nvidia H20、AMD MI308 或同等芯片需要获得许可。同时，美国国会启动了一项调查，以确定芯片供应商 Nvidia 是否违反了早期的出口规定。

How it works: Nvidia launched the H20 in late 2023 to comply with a 2022 U.S. ban on China-bound shipments of Nvidia's H100 and H200 processors. The H20 uses the same architecture as the H200，but it's an order of magnitude slower with less memory and memory bandwidth.

Nvidia 之所以推出 H20，是为了遵守美国在 2022 年对英伟达 H100 和 H200 处理器输华实施的禁令。这款芯片于 2023 年底发布。虽然 H20 和 H200 采用了相同的架构，但 H20 的速度要慢一个数量级，而且内存和内存带宽也大幅减少。

1 Nvidia estimated that the new restrictions will cost the company $5.5 billion in revenue. AMD similarly expects to lose $800 million.

Nvidia 估计新限制将导致公司损失 55 亿美元的收入。AMD 同样预计损失 8 亿美元。

2 Congressional leaders opened an investigation into whether Nvidia assisted DeepSeek with developing AI models，a potential violation of U.S. trade restrictions.

国会领导人对 Nvidia 是否协助 DeepSeek 开发 AI 模型展开调查，这可能违反了美国贸易限制。

3 The action spurred China's biggest chip maker to accelerate production of its own AI chips. Huawei plans to begin mass shipments of its Ascend 910C AI chip，which is purportedly equivalent to Nvidia's H100，in May, Reuters reported. The company expects to mass produce its Ascend 920，a potential substitute for the H20，in the second half of this year, according to DigiTimes Asia.

这一行动促使中国最大的芯片制造商加快了自主 AI 芯片的生产。据路透社报道，华为计划在今年 5 月开始批量出货其 Ascend 910C AI 芯片，据称该芯片性能与英伟达的 H100 不相上下。另据 DigiTimes Asia 报道，该公司预计在今年下半年大规模生产其 Ascend 920，这款芯片有望成为 H20 的替代品。

Behind the news: The U.S. government's many moves to restrict shipments of advanced processors to China have sought to protect the nation's lead in AI，but they have not prevented Chinese developers from closing the gap. In 2020，the U.S. required chip makers that use U.S. technology — which includes both domestic chip designers like Nvidia and makers of advanced fabrication equipment like the Netherlands' ASML — to seek permission before doing business with Chinese tech giant Huawei. Last December，the U.S. published sweeping limits on sales of processors that involve U.S. technology，as well as the technology itself，to Chinese businesses.

新闻背后：美国政府为限制先进处理器输送至中国而频频出手，意在维护其在人工智能（AI）领域的领先优势，但这些举措并未能阻止中国开发者缩小与美国的差距。例如，在 2020 年，美国就要求所有使用了美国技术的芯片制造商 —— 无论是像 Nvidia 这样的美国本土芯片设计公司，还是像荷兰 ASML 这样先进制造设备的提供商 —— 在与中国科技巨头华为进行业务往来前必须先获得许可。去年 12 月，美国更是出台了更为全面的禁令，限制美国技术以及使用美国技术的处理器出售给中国企业。

Yes，but: Export restrictions may have slowed China's production of advanced chips，but they have also incentivized China to invest in establishing leadership in AI. In January，the Chinese AI developer DeepSeek surprised U.S. policymakers and AI leaders with the release of DeepSeek-R1，which performs comparably to OpenAI's o1，but whose weights are freely available and trained using less computation.

是的，不过：出口限制也许放缓了中国在先进芯片领域的生产，但这同时也激励了中国加大投入，力图在人工智能领域建立领导地位。今年一月，中国的人工智能开发者 DeepSeek 发布了 DeepSeek-R1，这款模型的性能堪比 OpenAI 的 o1，让美国的政策制定者和人工智能领域的领军人物都感到意外。更重要的是，DeepSeek-R1 的权重是免费公开的，而且在训练时所用的计算资源也更少。

Why it matters: The first wave of restrictions on sales of advanced chips to China did little harm to U.S. chipmakers，largely because demand outstripped supply. But later restrictions have had a greater impact on their sales. The new limits could cost Nvidia and AMD significant revenue and likely will degrade their competitiveness abroad and bolster China's homegrown chip-making industry.

这件事为什么重要：第一波限制对中国销售先进芯片的措施，对美国芯片制造商造成的损害微乎其微，这主要是因为当时需求大于供应。但后来的限制对他们的销售产生了更大的影响。新的限制可能会让 Nvidia 和 AMD 损失大量收入，同时可能削弱它们在海外的竞争力，并反而扶持中国本土的芯片制造产业。

We're thinking: The AI community's international scope is one of its greatest strengths. While individual countries must attend to their national security，progress in AI benefits all nations. Even in this era of rising protectionism，we hope members of the global AI community continue to support one another and encourage the free flow of ideas.

我们认为，人工智能（AI）社区的国际化是其最大的优势之一。尽管每个国家都需要关注自身的国家安全，但 AI 的进步却能惠及所有国家。即使在这个保护主义日益盛行的时代，我们仍然希望全球 AI 社区的成员能够继续相互支持，并鼓励思想的自由交流。

#### Text-Only LLM Goes Multimodal

纯文本大语言模型走向多模态

Large language models excel at processing text but can't interpret images，video，or audio directly without further training on those media types. Researchers devised a way to overcome this limitation.

大语言模型 （Large Language Model） 擅长处理文本，但如果不进一步针对图像、视频或音频等媒体类型进行训练，则无法直接理解它们。研究人员设计了一种方法来克服这一局限性。

What's new: Kumar Ashutosh and colleagues at Meta，University of Texas，and UC Berkeley introduced Multimodal Iterative LLM Solver (MILS），a method that pairs a text-only large language model（LLM）with a multimodal embedding model to generate captions for images，video，and audio without further training.

新鲜事：来自 Meta、德克萨斯大学和加州大学伯克利分校的 Kumar Ashutosh 及其同事推出了一种名为多模态迭代 LLM 求解器（MILS）的方法。这种方法将一个仅处理文本的大语言模型（LLM）与一个多模态嵌入模型结合起来，无需额外训练即可为图像、视频和音频生成字幕。

Key insight: LLMs can generate text and refine their outputs based on new information. On the other hand，multimodal embedding models can score the similarity between a given text and an image，video，or audio clip. Given this score，an LLM can regenerate the text iteratively until the score indicates a strong match between the text and the associated media. This enables the LLM to generate accurate captions for images，videos，and audio clips without training in these tasks.

关键见解：大语言模型（LLM）能够生成文本并根据新信息调整输出。另一方面，多模态嵌入模型可以衡量一段文本与图像、视频或音频剪辑之间的相似程度并给出评分。有了这个评分，LLM 就可以反复生成文本，直到评分表明文本与相关媒体高度匹配。这样一来，LLM 就能在无需专门训练的情况下，为图像、视频和音频剪辑生成准确的字幕。

How it works: Given a prompt and an image，video，or audio clip，Llama 3.1 8B produced and iteratively refined the prompt according to a pretrained multimodal embedding model's estimate of the similarity between the text and media.

工作原理：给定一个 prompt 和一段图像、视频或音频内容，Llama 3.1 8B 会根据一个预训练的多模态嵌入模型对文本和媒体相似度的评估结果，来生成并逐步优化这个 prompt。

1 The LLM generated 30,000 to 50,000 initial captions to prime the process.

大语言模型生成了 30,000 到 50,000 个初始标题，为后续流程做准备。

2 Given each caption and a media file，a multimodal model estimated their semantic similarity scores. SigLIP evaluated text and images, ViCLIP text and video，and ImageBind text and audio.

对于每个标题和一个媒体文件，一个多模态模型会计算它们之间的语义相似度分数。具体来说，SigLIP 负责评估文本和图像的相似度，ViCLIP 评估文本和视频，而 ImageBind 则评估文本和音频。

3 Based on the top 50 most-similar previous captions，the LLM generated new captions.

基于与先前生成的字幕中相似度最高的 50 个，大语言模型（LLM）生成了新的字幕。

4 The system repeated the previous two steps until the top-scoring texts changed little or the LLM reached a predetermined number of iterations.

系统重复了前两个步骤，直到得分最高的文本几乎没有变化，或者 LLM 达到了预设的迭代次数。

Results: The authors evaluated MILS on captioning images，videos，and audio clips. They measured performance according to Metric for Evaluation of Translation with Explicit ORdering（METEOR），which checks for synonyms，words that share the same root，and word order to determine whether a generated caption matches a ground-truth caption（higher is better). Overall，MILS outperformed models that underwent task-specific training.

结果：作者评估了 MILS 在图像、视频和音频片段字幕生成方面的性能。他们使用 METEOR（Metric for Evaluation of Translation with Explicit ORdering）指标来衡量性能。METEOR 通过检查同义词、同根词和词序，来判断生成的字幕与真实字幕的匹配程度（该指标得分越高越好）。总的来说，MILS 的表现优于经过任务特定训练的模型。

1 On the MSCOCO dataset for image captioning，MILS achieved 15.0 METEOR，while MeaCap achieved 14.1 METEOR.

在用于图像标注的 MSCOCO 数据集上，MILS 的 METEOR 分数达到 15.0，而 MeaCap 则为 14.1。

2 On MSR-VTT，which evaluates video captioning，MILS attained 14.4 METEOR，while a model trained to caption videos achieved 11.3 METEOR.

在评估视频标注的 MSR-VTT 数据集上，MILS 获得了 14.4 的 METEOR 分数，而专门训练用于视频标注的模型则取得了 11.3 分。

3 On Clotho，which assesses audio captions，MILS achieved a METEOR of 12.4，while ZerAuCap reached 9.4 METEOR.

在用于评估音频字幕的 Clotho 数据集上，MILS 取得了 12.4 的 METEOR 分数，而 ZerAuCap 的 METEOR 分数为 9.4。

Why it matters: Zero-shot captioning models like Aya Vision and Pixtral require training on paired captions and media. The authors' approach takes advantage of pretrained multimodal models to enable an LLM to compose multimedia captions without further training.

重要意义：像 Aya Vision 和 Pixtral 这样的零样本字幕生成模型通常需要在配对的字幕和媒体数据上进行训练。而作者提出的方法则巧妙地利用了预训练的多模态模型，让大语言模型无需额外的训练就能生成多媒体内容的字幕。

We're thinking: Synthetic data is increasingly useful for training AI models. By enabling LLMs to synthesize good captions，MILS adds fuel to this fire.

我们认为：合成数据对于训练 AI 模型越来越有帮助。MILS 通过让大语言模型能够合成高质量的 caption，更是为此锦上添花。