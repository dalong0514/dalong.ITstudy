## 20250402Open-Voice-to-Voice-With-Vision-ChatGPT-Creates-Emotional-Bonds

[Open Voice-to-Voice With Vision, ChatGPT Creates Emotional Bonds, Human Action in 3D, Web Scrapers Caught in Maze](https://www.deeplearning.ai/the-batch/issue-295/)

Contrary to standard prompting advice that you should give LLMs the context they need to succeed，I find it's sometimes faster to be lazy and dash off a quick，imprecise prompt and see what happens. The key to whether this is a good idea is whether you can quickly assess the output quality，so you can decide whether to provide more context. In this post，I'd like to share when and how I use「lazy prompting.」

通常的建议是应该给大语言模型（LLM）提供足够的上下文信息，但我发现有时候「偷懒」反而更高效：快速写一个不太精确的提示语，先看看效果如何。这种方法是否可行，关键在于你能否快速判断输出质量，从而决定是否需要补充更多背景信息。在本文中，我想分享一下我使用「懒惰提示（lazy prompting）」的时机和方法。

When debugging code，many developers copy-paste error messages — sometimes pages of them — into an LLM without further instructions. Most LLMs are smart enough to figure out that you want them to help understand and propose fixes，so you don't need to explicitly tell them. With brief instructions like「Edit this：…」or「sample dotenv code」(to remind you how to write code to use Python's dotenv package），an LLM will often generate a good response. Further，if the response is flawed，hopefully you can spot any problems and refine the prompt，for example to steer how the LLM edits your text.

调试代码时，许多开发者习惯把错误信息 —— 有时甚至长达数页 —— 直接粘贴到大语言模型（LLM）的输入框里，不做任何额外说明。实际上，大多数大语言模型都能自动识别这种需求，主动提供问题分析和解决方案，无需用户特别说明。简单的指令如「编辑这段代码：...」或「dotenv 配置示例」（用于查询 Python dotenv 包的用法），通常就能获得不错的回复。如果回复存在瑕疵，开发者还可以通过修改提示词来引导模型调整输出，比如指定具体的编辑方式。

At the other end of the spectrum，sometimes  I spend 30 minutes carefully writing a 2-page prompt to get an AI system to help me solve a problem（for example to write many pages of code）that otherwise would have taken me much longer.

另一方面，有时我会花 30 分钟精心设计一份 2 页的提示（prompt），让 AI 系统帮我解决某个问题（比如编写大量代码），而如果完全由我自己完成，可能要耗费多得多的时间。

I don't try a lazy prompt if（i）I feel confident there's no chance the LLM will provide a good solution without additional context. For example，given a partial program spec，does even a skilled human developer have a chance of understanding what you want? If I absolutely want to use a particular piece of pdf-to-text conversion software（like my team LandingAI's Agentic Doc Extraction!），I should say so in the prompt，since otherwise it's very hard for the LLM to guess my preference. I also wouldn't use a lazy prompt if（ii）a buggy implementation would take a long time to detect. For example，if the only way for me to figure out if the output is incorrect is to laboriously run the code to check its functionality，it would be better to spend the time up-front to give context that would increase the odds of the LLM generating what I want.

在以下两种情况我不会使用简略提示（lazy prompt）：

1）当我确信在没有额外上下文的情况下，大语言模型（LLM）不可能给出好的解决方案时。比如面对一个不完整的程序需求文档，即便是经验丰富的开发者也难以准确理解需求，这时就需要更详细的提示。如果我想使用特定的 PDF 转文本工具（比如我们 LandingAI 团队的 Agentic Doc Extraction 产品），就必须在提示中明确说明，否则 LLM 很难猜中我的偏好。

2）当错误实现需要很长时间才能被发现时。举例来说，如果只有通过实际运行代码才能验证输出是否正确，那么与其事后花时间检查，不如一开始就提供充分的上下文，这样更有可能让 LLM 生成符合预期的结果。

By the way，lazy prompting is an advanced technique. On average，I see more people giving too little context to LLMs than too much. Laziness is a good technique only when you've learned how to provide enough context，and then deliberately step back to see how little context you can get away with and still have it work. Also，lazy prompting applies only when you can iterate quickly using an LLM's web or app interface It doesn't apply to prompts written in code for the purpose of repeatedly calling an API，since presumably you won't be examining every output to clarify and iterate if the output is poor.

顺便提一下，懒惰提示（lazy prompting）是一种高级技巧。通常来说，使用者给大语言模型提供的上下文过少的情况比过多更常见。这种技巧只有在掌握如何提供充分上下文后，才有意减少信息量，试探模型在最少上下文下的工作能力时才适用。此外，懒惰提示仅适用于通过大语言模型的网页或应用界面快速迭代的场景。对于为重复调用 API 而编写的提示（prompt）代码则不适用，因为当输出质量不佳时，使用者通常不会逐一检查并迭代优化。

Thank you to Rohit Prsad，who has been collaborating with me on the open-source package aisuite，for suggesting the term lazy prompting. There is an analogy to lazy evaluation in computer science，where you call a function at the latest possible moment and only when a specific result is needed. In lazy prompting，we add details to the prompt only when they are needed.

感谢 Rohit Prasad（他一直与我合作开发开源软件包 aisuite）提出的「惰性提示（lazy prompting）」概念。这类似于计算机科学中的「惰性求值」：就像程序只在真正需要结果时才执行计算一样，惰性提示也只在必要时才向提示语中添加具体细节。

Keep building!

Andrew

### News

#### Interactive Voice-to-Voice With Vision

支持视觉交互的智能语音对话系统

Researchers updated the highly responsive Moshi voice-to-voice model to discuss visual input.

研究人员对响应灵敏的 Moshi 语音交互模型进行了升级，新增了视觉信息处理能力。

What's new: Amélie Royer，Moritz Böhle，and colleagues at Kyutai proposed MoshiVis. The weights are free to download under the CC-BY 4.0 license，which permits commercial and noncommercial uses. You can hear examples of its output and chat with a demo.

最新进展：来自 Kyutai 实验室的 Amélie Royer、Moritz Böhle 及其团队发布了 MoshiVis。该模型的训练权重采用 CC-BY 4.0 开源协议免费提供，支持商业和非商业用途。现在您不仅可以试听实际效果样例，还能直接体验在线演示版的对话功能。

[[2503.15633] Vision-Speech Models: Teaching Speech Models to Converse about Images](https://arxiv.org/abs/2503.15633?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9pF5nDvN8DqUslWnSEP58TIvJ1x91RCild8KocqyU23j2HlYPalzmO6RL3RLOd3BejGcR3)

Key insight: The original Moshi，which manages overlapping voice-to-voice conversations，comprises two transformers. The first outputs a text transcription of its speech，and the second outputs speech. Since Moshi generates text as well as speech，the authors of that work fine-tuned it to predict the next token of text. In MoshiVis，the addition of a vision encoder enabled the authors to fine-tune on not only image-text datasets but also image-speech datasets，which are not so plentiful. Fine-tuning on this wider variety of images enabled the system to understand images better than fine-tuning it solely on image-speech datasets.

核心发现：原始 Moshi 系统用于处理重叠语音对话，其架构包含两个 Transformer。第一个负责将语音转换为文本转录，第二个则负责生成语音输出。由于 Moshi 同时具备文本和语音生成能力，研究团队对其进行了微调，使其能够预测下一个文本 Token。在 MoshiVis 版本中，研究人员新增了视觉编码器，这不仅支持在图像 - 文本数据集上进行微调，还能应用于相对稀缺的图像 - 语音数据集。通过在更丰富的图像类型上进行训练，系统获得了比单纯使用图像 - 语音数据集更强的图像理解能力。

How it works: To Moshi，the authors added a model based on a pretrained SigLIP vision encoder to encode images，a cross-attention adapter to fuse image information with speech tokens，and vanilla neural networks trained to act as gates that determine how much image information to fuse. Specifically，the authors added the adapter and a gate between Moshi's existing self-attention and fully connected layers.

实现原理：研究团队为 Moshi 系统新增了三个关键组件：1）基于预训练 SigLIP 视觉编码器的图像编码模块，2）用于融合图像信息与语音 token 的交叉注意力适配器，3）作为信息门控的 vanilla 神经网络（用于调控图像信息融合量）。具体实现上，这些新增组件被集成在 Moshi 原有的自注意力层（self-attention）和全连接层之间。

1 The authors fine-tuned MoshiVis on seven datasets. For instance，they produced a vision-speech-to-speech dataset by prompting two Mistral NeMo models to talk about an image from initial descriptions of images in the image-text datasets PixMo and DOCCI，then using a custom text-to-speech model to convert the text into speech. Another example：They used OCR-VQA，an image-text dataset for answering questions about images（no speech data involved).

作者们在七个数据集上对 MoshiVis 进行了微调。例如，他们首先生成了一个视觉语音数据集：先使用 PixMo 和 DOCCI 这两个图像文本数据集的初始描述，让两个 Mistral NeMo 模型根据图像展开对话，再用定制的文本转语音（text-to-speech）模型将对话内容转为语音。另一个例子是 OCR-VQA：这个图像问答数据集（不含语音数据）也被用于模型训练。

2 They fine-tuned MoshiVis to predict the next token of speech or text in their datasets,  training only the newly added adapter and gates while keeping SigLIP and the two Moshi transformers frozen.

研究团队对 MoshiVis 进行了优化训练，使其能够预测数据集中语音或文本的后续 token。训练过程中，只更新新加入的适配器和门控参数，而 SigLIP 和两个 Moshi transformer 的参数则保持固定不变。

Results: MoshiVis is highly responsive in conversation with latency of roughly 50 milliseconds on a Mac Mini.

测试结果显示：MoshiVis 在 Mac Mini 平台上表现出色，对话响应延迟仅为 50 毫秒左右。

1 Qualitatively，it handles transitions smoothly between talking about images and general conversation. However，it sounds more robotic than other recent voice generators.

在实际体验中，该系统能够流畅切换图像讨论和普通对话场景。不过，与市面上新一代语音生成器相比，其声音仍显得较为机械生硬。

2 Quantitatively，the authors compared MoshiVis to the vision-language model PaliGemma fine-tuned to answer questions about images. Overall，MoshiVis prompted with audio（and images）performed less accurately than PaliGemma prompted with text（and images). For example，on OCR-VQA，MoshiVis achieved roughly 65 percent accuracy while PaliGemma achieved roughly 71 percent accuracy.

从量化结果来看，研究人员将 MoshiVis 与视觉语言模型 PaliGemma 进行了对比测试，其中 PaliGemma 专门针对图像问答任务进行了微调。总体而言，采用音频（和图像）作为输入的 MoshiVis 在准确率上低于使用文本（和图像）输入的 PaliGemma。以 OCR-VQA 测试为例，MoshiVis 的准确率约为 65%，而 PaliGemma 则达到了 71% 左右。

Behind the news: MoshiVis complements a small but growing roster of systems that combine vision with speech-to-speech. ChatGPT accepts and generates speech in response to camera views or a user's phone screen. AnyGPT (open weights training and inference code）accepts or generates speech，text，images，and music. Similarly, Mini-Omni2 (open weights and inference code）accepts and generates text，speech，and images. The authors didn't compare MoshiVis to these alternatives.

新闻背后：MoshiVis 加入了一个规模虽小但不断壮大的系统阵营，这些系统都能将视觉与语音转换技术相结合。ChatGPT 可以根据相机画面或用户手机屏幕的内容来接收和生成语音。AnyGPT（开源权重，提供训练和推理代码）能够处理并生成语音、文本、图像和音乐。同样地，Mini-Omni2（开源权重，提供推理代码）也能接收和生成文本、语音及图像。不过，作者并未将 MoshiVis 与这些同类系统进行对比。

Why it matters: MoshiVis easily adapts a speech-to-speech model to work with a new type of media input. MoshiVis requires training only the adapters，while the earlier AnyGPT and Mini-Omni2，which can also discuss images via voice input and output，require training both adapters and the main model.

为什么这很重要：MoshiVis 能够轻松地将语音转语音模型（voice-to-voice model）适配到新型媒体输入。MoshiVis 仅需训练适配器（adapter），而早期的 AnyGPT 和 Mini-Omni2（也能通过语音输入输出讨论图像）则需要训练适配器和主模型（main model）。

We're thinking: Text-chat models respond appropriately when a user refers to a previous topic or something new，and MoshiVis does，too，in spoken interactions. Evaluations of this capability will become increasingly important as voice-to-voice becomes more widespread.

我们认为：当用户提到之前的话题或新内容时，文字聊天模型能够做出恰当回应，而 MoshiVis 在语音对话中同样具备这种能力。随着语音交互越来越普及，评估这种能力将变得愈发重要。

#### Scraping the Web? Beware the Maze

网络爬虫当心

Bots that scrape websites for AI training data often ignore do-not-crawl requests. Now web publishers can enforce such appeals by luring scrapers to AI-generated decoy pages.

你已进入迷宫为获取 AI 训练数据而抓取网站的爬虫程序常常无视禁止爬取（do-not-crawl）请求。如今，网站发布者有了新对策：用 AI 生成的诱饵页面来「款待」这些不速之客。

What's new: Cloudflare launched AI Labyrinth，a bot-management tool that serves fake pages to unwanted bots，wasting their computational resources and making them easier to detect. It's currently free to Cloudflare users.

最新动态：Cloudflare 推出 AI Labyrinth（AI 迷宫），这是一款机器人防护工具，能够向恶意爬虫返回伪装页面，消耗其计算资源并提升检测效率。该功能目前免费向 Cloudflare 用户提供。

[Trapping misbehaving bots in an AI Labyrinth](https://blog.cloudflare.com/ai-labyrinth/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9pF5nDvN8DqUslWnSEP58TIvJ1x91RCild8KocqyU23j2HlYPalzmO6RL3RLOd3BejGcR3/)

How it works: AI Labyrinth protects webpages by embedding them with hidden links to AI-generated alternatives that appear legitimate to bots but are irrelevant to the protected site.

工作原理：AI Labyrinth 通过为网页嵌入指向 AI 生成（AI-generated）替代页面的隐藏链接来实现保护，这些替代页面在机器人看来是合法的，但与受保护网站的实际内容无关。

1 An unidentified open-source model that runs on Cloudflare's Workers AI platform generates factual，science-related HTML pages on diverse topics. A pre-generation pipeline sanitizes the pages of XSS vulnerabilities before storing them in Cloudflare's R2 storage platform.

一个未具名的开源模型在 Cloudflare 的 Workers AI 平台上运行，能够生成各类主题的科学事实相关 HTML 页面。预处理流程会先清除页面中的 XSS（跨站脚本）漏洞，再将它们存入 Cloudflare 的 R2 存储平台。

2 A custom process embeds links to decoy pages within a site's HTML. Meta instructions hide these links from search engine indexers and other authorized crawlers，while other attributes and styling hide the decoy links from human visitors.

通过定制化流程，网站会在 HTML 中嵌入诱饵页面的链接。元指令（Meta instructions）使搜索引擎索引器和其他授权爬虫无法发现这些链接，同时通过特定属性和样式设置，这些诱饵链接也不会被普通访客察觉。

3 When an unauthorized bot follows one of these links，it crawls through layers of irrelevant content.

当未授权的机器人点击其中某个链接时，它会穿透层层无关内容进行爬取。

4 Cloudflare logs these interactions and uses the data to fingerprint culprit bots and improve its bot-detection models.

Cloudflare 记录这些交互数据，用于标记恶意机器人的数字指纹，并优化其机器人检测模型。

Behind the news: The robots.txt instructions that tell web crawlers which pages they can access aren't legally binding，and web crawlers can disregard them. However，online publishers are moving to try to stop AI developers from training models on their content. Cloudflare，as the proxy server and content delivery network for nearly 20 percent of websites，plays a potentially large role in this movement. AI crawlers account for nearly 1 percent of web requests on Cloudflare's network，the company says.

新闻背后的故事：robots.txt 文件规定的爬虫访问规则（web crawler instructions）实际上没有法律效力，爬虫程序完全可以忽略这些限制。但如今，网络出版商们正在积极阻止 AI 开发者使用其内容训练模型。作为全球近 20% 网站使用的代理服务器（proxy server）和内容分发网络（CDN），Cloudflare 在这场对抗中扮演着关键角色。该公司透露，在其网络流量中，AI 爬虫产生的访问请求占比已接近 1%。

Why it matters: The latest AI models are trained on huge quantities of data gleaned from the web，which enables them to perform well enough to be widely useful. However，publishers increasingly aim to limit access to this data. AI Labyrinth gives them a new tool that raises the cost for bots that disregard instructions not to scrape web content.

关键意义：最新 AI 模型通过从网络抓取的海量数据进行训练，使其性能达到足以广泛应用的水平。然而，出版商正日益加强对这些数据的访问限制。AI Labyrinth 为他们提供了一个新工具，可大幅提高违规抓取网页内容的机器人的操作成本。

We're thinking: If AI Labyrinth gains traction，no doubt some teams that build crawlers will respond with their own AI models to sniff out its decoy pages. To the extent that the interest between crawlers and publishers is misaligned and clear，enforceable rules for crawling are lacking，this cat-and-mouse competition could go on for a long time.

我们设想这样一种可能：当 AI 迷宫系统（AI Labyrinth）开始流行时，某些开发网络爬虫的团队势必会训练自己的 AI 模型来识别系统中的虚假页面。由于网络爬虫与内容发布者之间存在明显的利益冲突，再加上缺乏具有约束力的网络爬取规范，这场攻防拉锯战很可能会长期持续下去。

#### Chatbot Use Creates Emotional Bonds

聊天机器人如何与用户建立情感纽带

A pair of papers investigate how increasingly human-like chatbots affect users' emotions.

两项最新研究探讨了拟人化程度不断提升的聊天机器人对用户情感产生的影响。

What's new: Jason Phang at OpenAI，Cathy Mengying Fang at MIT Media Lab，and colleagues at those organizations published complementary studies that examine ChatGPT's influence on loneliness，social interactions，emotional dependence，and potentially problematic use.

最新发现：OpenAI 的 Jason Phang、MIT 媒体实验室的 Cathy Mengying Fang 与这些机构的同事们共同发表了两项互补研究，探究了 ChatGPT 对孤独感、社交互动、情感依赖以及可能引发的使用问题的影响。

How it works: One study was a large-scale analysis of real-world conversations，and the other was a randomized control trial that tracked conversations of a selected cohort. Both evaluated conversations according to EmoClassifiersV1，a set of classifiers based on large language models that evaluate five top-level emotional classes（loneliness，dependence，and the like）and 20 sub-classes of emotional indicators（seeking support，use of pet names，and so on).

实验方法：第一项研究是对真实场景中对话的大规模分析，第二项是追踪特定人群对话的随机对照试验。两项研究都采用 EmoClassifiersV1 进行评估，这是一套基于大语言模型（LLM/Large Language Model）的分类系统，可评估 5 个一级情感分类（孤独感、依赖性等）和 20 个情感指标子类（寻求支持、使用昵称等）。

1 The analysis of real-world conversations considered roughly 3 million English-language voice conversations by 6,000 heavy users of ChatGPT's Advanced Voice Mode over three months and surveyed 4,076 of them about their perceptions. It analyzed conversations for emotional cues and tracked users' percentages of emotional messages over time（decreasing，flat，or increasing). The team validated classification accuracy by comparing the classifier's outputs with survey responses.

这项现实对话研究分析了约 300 万条英文语音对话数据，来自 6,000 名 ChatGPT 高级语音模式（Advanced Voice Mode）的重度用户，为期三个月，并对其中 4,076 名用户进行了使用感受调查。研究通过情感线索分析对话内容，追踪用户发送带有情感倾向的消息比例随时间的变化趋势（下降、持平或上升）。团队通过对比分类器输出结果与用户调查反馈，验证了分类结果的准确性。

2 The randomized controlled trial asked nearly 1,000 participants over 28 days to engage in particular conversation types（open-ended，personal，or non-personal）and modalities（text，interactions with ChatGPT's neutral voice，or interactions with an engaging voice），controlling for variables like duration and age. Each participant spent at least five minutes per day interacting with ChatGPT，guided by prompts（such as「Help me reflect on a treasured memory」）and surveys（baseline，daily，weekly，and final). The study classified over 300,000 messages to identify qualities like loneliness and dependence and sorted them according to conversation type and modality.

这项随机对照研究邀请了近 1000 名参与者，在 28 天内参与特定类型的对话（开放式、个人化或非个人化）和互动方式（文本、与 ChatGPT 中性声音互动，或与富有感染力的声音互动），同时控制时长和年龄等变量因素。每位参与者每天至少花 5 分钟与 ChatGPT 交流，根据提示（如「帮助我回忆一段珍贵往事」）完成调查（包括基线、每日、每周和最终调查）。研究团队对超过 30 万条消息进行分析，识别出孤独感和依赖性等心理特征，并按对话类型和互动方式进行了分类。

Results: Both studies found that using ChatGPT was associated with reduced loneliness and increased emotional chat. However，it was also associated with decreased interpersonal social interaction and greater dependence on the chatbot，especially among users who spent more time chatting.

结果：两项研究均表明，使用 ChatGPT 能帮助缓解孤独感并促进情感表达。但同时也发现，这会导致现实社交减少，用户对聊天机器人的依赖性增强，这种现象在长时间使用的用户群体中尤为明显。

Yes，but: The authors of the randomized controlled trial acknowledged significant limitations. For instance，the study lacked a non-ChatGPT control group to differentiate AI-specific effects from influences such as seasonal emotional shifts，and the trial's time frame and assignments may not mirror real-world behavior.

确实如此，但：这项随机对照试验（Randomized Controlled Trial）的作者承认研究存在明显局限。例如，实验缺少非 ChatGPT 对照组，无法区分 AI 特有的影响与季节性情绪波动等因素；同时，试验周期和任务设计可能无法真实反映现实行为模式。

Why it matters: As AI chatbot behavior becomes more human-like，people may lean on large language models to satisfy emotional needs such as easing loneliness or grief. Yet we know little about their effects. These studies offer a starting point for AI developers who want to both foster emotional support and protect against over-reliance，and for social scientists who want to better understand the impact of chatbots.

意义何在：当 AI 聊天机器人的行为越来越接近人类时，人们可能会借助大语言模型来满足情感需求，比如排解孤独感或抚慰悲伤情绪。但目前我们对这类技术的影响仍知之甚少。这些研究既为希望平衡情感支持与避免用户过度依赖的 AI 开发者提供了参考，也为试图深入理解聊天机器人影响的社会科学家指明了方向。

We're thinking: Social media turned out to cause emotional harm to some people in ways that were not obvious when the technology was new. As chatbots evolve，research like this can help us steer them toward protecting and enhancing mental health.

我们的思考是：社交媒体对部分人群造成的情感伤害，在其技术刚兴起时并不明显。随着聊天机器人技术的演进，这类研究将帮助我们更好地引导技术发展，使其成为保护和提升心理健康的工具。

#### Human Action in 3D

3D 场景中的人类动作

AI systems designed to generate animated 3D scenes that include active human characters have been limited by a shortage of training data，such as matched 3D scenes and human motion-capture examples. Generated video clips can get the job done without motion capture.

模拟设计用于生成包含动态人物角色的 3D 动画场景的 AI 系统，长期以来受限于训练数据的匮乏，特别是配对的 3D 场景与人体动作捕捉样本。有趣的是，研究发现即使不依赖动作捕捉技术，仅通过生成的视频片段也能达到预期效果。

What's new: A team led by Hongjie Li，Hong-Xing Yu，and Jiaman Li at Stanford University developed Zero-Shot 4D Human-Scene Interaction (ZeroHSI），a method that animates a 3D human figure interacting with a particular 3D object in a selected 3D scene. You can see its output here.

最新突破：斯坦福大学 Hongjie Li、Hong-Xing Yu 和 Jiaman Li 团队研发了零样本 4D 人与场景交互（ZeroHSI）技术。这项创新技术能让 3D 虚拟人物在特定场景中与 3D 物体自然互动。点击这里可以查看效果演示。

[[2412.18600] ZeroHSI: Zero-Shot 4D Human-Scene Interaction by Video Generation](https://arxiv.org/abs/2412.18600?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9pF5nDvN8DqUslWnSEP58TIvJ1x91RCild8KocqyU23j2HlYPalzmO6RL3RLOd3BejGcR3)

Key insight：Earlier approaches attempted to build a generalized approach：given a 3D scene，a text prompt，and motion-capture data，a diffusion model learned to alter the positions and rotations of human joints and objects over time. But if the system is designed to learn a 3D animation for a specific example motion，videos can stand in for motion capture. Current video generation models can take an image of a scene and generate a clip of realistic human motion and interactions with a wide variety of objects within it. From there，we can minimize the difference between the video frames and images of actions within the scene.

核心发现：早期研究试图采用通用方法：给定一个 3D 场景、文本提示和动作捕捉数据，扩散模型（diffusion model）能够动态调整人体关节和物体的位置与旋转。而当系统只需学习特定动作的 3D 动画时，视频数据就能取代动作捕捉。现在的视频生成模型可以直接处理场景图像，生成包含多种物体逼真运动及人体互动的视频片段。基于此，我们只需优化视频帧与场景动作图像之间的差异即可。

How it works: ZeroHSI takes a pre-built 3D scene that includes a 3D human mesh and 3D object. It uses a rendered image of the scene to generate a video. Then it uses the video to help compute the motions of a human figure and object within the scene.

工作原理：ZeroHSI 使用预先构建好的 3D 场景，其中包含 3D 人体网格（3D human mesh）和 3D 物体。系统首先通过场景渲染图像生成视频，再以该视频为基础，计算出场景中人体与物体的运动轨迹。

1 The authors fed ZeroHSI a 3D scene complete with 3D human mesh and 3D object. ZeroHSI rendered an image of the scene，viewed from a default camera pose，using Gaussian splatting.

研究人员向 ZeroHSI 输入了一个完整的 3D 场景，其中包含 3D 人体网格和 3D 物体。ZeroHSI 采用高斯泼溅（Gaussian splatting）技术，从预设相机位姿渲染出了场景图像。

2 ZeroHSI fed the rendered image，along with a prompt that described a human interacting with an object in the scene（「the person is playing guitar while sitting on the sofa」），to Kling，an image-to-video generator. Kling produced a video clip.

ZeroHSI 将渲染图连同场景描述提示（「这个人正坐在沙发上弹吉他」）输入给 Kling—— 一个图生视频模型。Kling 随后生成了一段视频片段。

3 For each generated video frame，ZeroHSI rendered a new image of the 3D scene and minimized a loss function with four terms. It used the loss function to calculate how to change the poses of the 3D human，3D object，and camera in the 3D scene to match their poses in the video frame. For example，one loss term minimized pixel-level differences between the image and video frame. Another minimized the difference between the object's center in the image and in a segmentation mask of the video frame produced by SAM 2.

针对每个生成的视频帧，ZeroHSI 会渲染 3D 场景的新图像，并使用包含四项的损失函数进行优化。该损失函数用于确定如何调整 3D 场景中人体、物体和相机的姿态，使其与视频帧中的姿态保持一致。例如，第一项优化目标是减小图像与视频帧之间的像素级差异，第二项则是缩小图像中物体中心与 SAM 2 生成的分割掩模中物体中心的距离。

4 The system sometimes produced errors. For instance，one of the human figure's hands might fail to touch the object，or the object penetrated the human figure's body. To remedy this，for each video frame，the authors refined the poses in a separate phase that involved three loss terms. For instance，one term minimized the distance between surfaces of a hand and the object to prevent penetration or distance between them.

该系统偶尔会出现错误。例如，人物模型的手部可能无法正确接触物体，或者发生物体穿模的情况。为了解决这个问题，作者为每一帧视频都增加了专门的优化环节，通过三个损失函数项来调整动作姿态。其中一项就是通过最小化手部与物体表面的距离，来避免穿模或确保接触到位。

Results: The authors evaluated ZeroHSI using a proprietary dataset of 12 3D scenes that included a human figure and an object and between one and three text prompts that described interactions between the human and object and/or scene. In 100 evaluations，ZeroHSI outperformed LINGO，a diffusion model trained on matched 3D scene，3D object，and human motion-capture data that had achieved the previous state of the art.

结果：研究人员使用一个包含 12 个 3D 场景的私有数据集对 ZeroHSI 进行了测试，每个场景包含一个人体模型、一个物体，以及 1-3 条描述人与物体或场景互动的文本提示。经过 100 次测试评估，ZeroHSI 的表现超越了此前保持业界最佳性能的 LINGO 模型 —— 后者是基于匹配的 3D 场景、3D 物体和人体动作捕捉数据训练的扩散模型。

1 ZeroHSI achieved 24.01 average CLIP Score，which measures how well text descriptions match images（higher is better），while LINGO achieved a 22.99 average CLIP Score. ZeroHSI achieved 0.033 average object penetration depth，a measure of plausibility in physical interactions（lower is better），while LINGO achieved 0.242 average object penetration depth.

ZeroHSI 的平均 CLIP 分数（CLIP Score）达到 24.01，这个分数反映了文本描述与图像的匹配程度（数值越高匹配越好）；相比之下，LINGO 的平均分数为 22.99。在衡量物理交互合理性的物体穿透深度（object penetration depth）指标上，ZeroHSI 的平均值为 0.033（数值越低越合理），而 LINGO 的平均值则为 0.242。

2 400 participants judged whether they preferred ZeroHSI or LINGO with respect to realism and how well their output aligned with the prompt. 86.9 percent preferred ZeroHSI for realism，and 89.1 percent preferred ZeroHSI for how well its output matched the prompt.

400 名参与者对 ZeroHSI 和 LINGO 进行了对比评估，主要考察图像真实性和文本匹配度两个维度。结果显示，86.9% 的参与者认为 ZeroHSI 生成的图像更真实，89.1% 的参与者认为 ZeroHSI 的输出更符合提示要求。

Why it matters: Learning from motion-capture data is problematic in a couple of ways：(i）it's expensive to produce，(ii）so little of it is available，which limits how much a learning algorithm can generalize from it. Video data，on the other hand，is available in endless variety，enabling video generation models to generalize across a wide variety of scenes，objects，and motions. ZeroHSI takes advantage of generated video to guide a 3D animation cheaply and effectively.

关键意义：使用动作捕捉（motion-capture）数据进行学习存在两大难题：一是成本太高，二是数据量太少，导致学习算法的泛化能力受限。而视频数据则完全不同，它来源丰富、种类多样，让视频生成模型能够适应各种不同的场景、物体和动作。ZeroHSI 巧妙地利用生成的视频数据，以低成本、高效率的方式指导 3D 动画制作。

We're thinking: There's a lot of progress to be made in AI simply by finding clever ways to use synthetic data.

我们的观点是：只要找到巧妙运用合成数据（synthetic data）的方法，人工智能领域就能实现重大突破。