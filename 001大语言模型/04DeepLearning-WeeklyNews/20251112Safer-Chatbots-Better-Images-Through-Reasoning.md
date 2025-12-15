## 20251112Safer-Chatbots-Better-Images-Through-Reasoning

[Safer (and Sexier) Chatbots, Better Images Through Reasoning, The Dawn of Industrial AI, and more...](https://www.deeplearning.ai/the-batch/issue-327/)

Dear friends,

I recently received an email titled "An 18-year-old's dilemma: Too late to contribute to AI?" Its author, who gave me permission to share this, is preparing for college. He is worried that by the time he graduates, AI will be so good there's no meaningful work left for him to do to contribute to humanity, and he will just live on Universal Basic Income (UBI). I wrote back to reassure him that there will still be plenty of work he can do for decades hence, and encouraged him to work hard and learn to build with AI. But this conversation struck me as an example of how harmful hype about AI is.

我最近收到一封邮件，标题是《一个 18 岁少年的困惑：现在投身 AI 领域，为时已晚？》。邮件的作者（他已同意我分享内容）正在准备上大学。他担心，等到自己毕业时，人工智能（AI）会发展到如此强大的地步，以至于他将找不到有意义的工作来为人类做贡献，未来可能只能依靠全民基本收入（UBI）生活。我回信安慰他，告诉他未来几十年里仍会有大量工作机会，并鼓励他努力学习，掌握运用 AI 进行创造的能力。但这次交流让我深切感到，当前围绕 AI 的过度炒作，其危害性由此可见一斑。

Yes, AI is amazingly intelligent, and I'm thrilled to be using it every day to build things I couldn't have built a year ago. At the same time, AI is still incredibly dumb, and I would not trust a frontier LLM by itself to prioritize my calendar, carry out resumé screening, or choose what to order for lunch — tasks that businesses routinely ask junior personnel to do.

是的，人工智能（AI）聪明得令人惊叹，我每天都兴奋地用它来打造一年前根本无法完成的东西。但与此同时，AI 也仍然笨得出奇。我可不会放心让一个前沿的大语言模型（LLM）自行决定我日程的优先级、进行简历筛选，或者帮我点午餐 —— 这些工作，企业通常只会交给初级员工来处理。

Yes, we can build AI software to do these tasks. For example, after a lot of customization work, one of my teams now has a decent AI resumé screener. But the point is it took a lot of customization.

是的，我们可以构建人工智能（AI）软件来完成这些任务。举个例子，经过大量的定制化工作，我的一个团队现在有了一款相当不错的 AI 简历筛选工具。但问题在于，这需要大量的定制工作。

Even though LLMs can handle a much more general set of tasks than previous iterations of AI technology, compared to what humans can do, they are still highly specialized. They're much better at working with text than other modalities, still require lots of custom engineering to get it the right context for a particular application, and we have few tools — and only inefficient ones — for getting our systems to learn from feedback and repeated exposure to a specific task (such as screening resumés for a particular role).

尽管大语言模型（LLM）能处理的任务范围远比之前的 AI 技术更广，但与人类的能力相比，它们仍然具有很大的局限性，是高度专门化的。它们擅长处理文本，远胜于处理其他模态（modalities）的数据。要让它们为特定应用提供合适的上下文，仍然需要大量的定制化工程工作。此外，我们缺乏有效的工具来让 AI 系统从反馈中学习，或是通过反复执行某项具体任务（例如，为某个特定职位筛选简历）来积累经验。

AI has stark limitations, and despite rapid improvements, it will remain limited compared to humans for a long time.

AI is amazing, but it has unfortunately been hyped up to be even more amazing than it is. A pernicious aspect of hype is that it often contains an element of truth, but not to the degree of the hype. This makes it difficult for nontechnical people to discern where the truth really is. Modern AI is a general purpose technology that is enabling many applications, but AI that can do any intellectual tasks that a human can (a popular definition for AGI) is still decades away or longer. This nuanced message that AI is general, but not that general, often is lost in the noise of today's media environment.

人工智能（AI）存在明显的局限性，尽管其发展迅速，但在很长一段时间内，其能力与人类相比仍将有限。

人工智能非常强大，但不幸的是，它被炒作得有些神乎其神了。炒作的一个弊端在于，它往往包含一丝真实的成分，但远没有吹嘘的那么夸张。这使得非专业人士很难看清真相。现代 AI 是一种通用技术，正在推动众多应用落地，然而，那种能够完成人类所能及的任何智力任务的人工智能（即通用人工智能（AGI）的一个流行定义），仍然需要数十年甚至更长时间才能实现。AI 具备通用性，但还没达到「无所不能」的程度 —— 这种微妙的讯息，常常淹没在当今媒体的喧嚣之中。

Similarly, the progress of frontier models is amazing! But not so amazing that they'll be able to do everything under the sun without a lot of customization. I know VC investors who are scared to invest in application-layer startups because they are worried that frontier AI model companies will quickly wipe out all of these businesses by improving their models. While some thin wrappers around LLMs no doubt will be replaced, there also remains a huge set of valuable applications that the current trajectory of progress of frontier models won't displace for a long time.

同样，前沿模型的进步速度确实令人惊叹！但还没到无所不能、无需大量定制就能包办一切的程度。我认识一些风险投资（VC）人，他们不敢投资应用层的初创公司，就是担心前沿 AI 模型公司会通过快速迭代模型，把这些业务都「吃掉」。诚然，一些仅仅是对大语言模型（LLM）进行简单套壳的应用无疑会被取代，但同时，仍有大量有价值的应用，在可预见的未来里，前沿模型当前的发展路径还无法撼动它们。

Without accurate information about the current state of AI and how it is likely to progress, some young people will decide not to enter AI because they think AGI leaves them no meaningful role, or decide not to learn how to code because they fear AI will automate it — right when it is the best time ever to join our field.

如果对人工智能（AI）的现状和未来走向缺乏准确认知，一些年轻人可能会做出错误的选择：他们或许会因为觉得通用人工智能（AGI）将令自己无所作为而放弃进入 AI 领域，又或许会因为担心 AI 将取代编码工作而拒绝学习编程 —— 然而，现在恰恰是加入我们这个领域前所未有的好时机。

Let us all keep working to get to a precise understanding of what's actually possible, and keep building!

Andrew

让我们共同努力，不断探求可能性的边界，并持续构建未来！

Andrew

### News

#### Toward Safer (and Sexier) Chatbots

### 新闻

#### 迈向更安全（且更性感）的聊天机器人

Chatbot providers, facing criticism for engaging troubled users in conversations that deepen their distress, are updating their services to provide wholesome interactions to younger users while allowing adults to pursue erotic conversations.

聊天机器人提供商因与情绪困扰的用户进行可能加剧其痛苦的对话而受到批评。为此，他们正在更新服务：为年轻用户提供健康的互动，同时允许成年人进行涉及情色内容的对话。

What's new: Character.AI, which provides chatbots designed for entertainment and companionship, temporarily barred teen users from parts of its offering and announced plans to offer a service for younger users. Meanwhile OpenAI, which faces a lawsuit on allegations that ChatGPT contributed to a teenager's suicide, updated ChatGPT to better help users in psychological distress and reaffirmed that it would allow adult users to generate erotic content later this year.

新动态：专注于提供娱乐和陪伴型聊天机器人的 Character.AI 公司，暂时限制了青少年用户访问其部分功能，并宣布计划推出面向年轻用户的服务。另一方面，正面临一项诉讼（指控其 ChatGPT 与一名青少年的自杀有关）的 OpenAI，更新了 ChatGPT 以更好地为处于心理困扰的用户提供帮助，并重申计划在今年晚些时候允许成年用户生成成人内容。

Character.AI limits access: The startup imposed limits on young users after it received "reports and feedback from regulators, safety experts, and parents" that expressed concern about its impact on teen users, BBC News reported.

Character.AI 限制青少年访问：据 BBC 新闻报道，这家初创公司收到了来自「监管机构、安全专家和家长的报告与反馈」，其中表达了对该平台影响青少年用户的担忧。为此，公司对年轻用户采取了访问限制措施。

* Character.AI moved to limit chat time for users under 18, starting with 2 hours daily and tapering to zero by November 25.

* The company will roll out a new in-house age verification model and use third-party technology to prevent younger users from engaging in adult chat.

* Character.AI 开始对 18 岁以下用户实施聊天时长限制，初期为每日 2 小时，并将在 11 月 25 日前逐步收紧，直至完全禁止。
* 该公司将推出自研的年龄验证模型，并采用第三方技术，以防止未成年用户接触成人内容聊天。

* In addition, it will establish an independent AI Safety Lab where it plans to collaborate with other organizations to improve safety alignment and other features for AI entertainment.

* 此外，它将建立一个独立的人工智能安全实验室（AI Safety Lab），并计划与其他组织合作，共同提升用于娱乐的人工智能（AI）在安全对齐（safety alignment）等方面的性能。

OpenAI detects distress: Around 0.15 percent of ChatGPT users — roughly 1.2 million out of the service's 800 million weekly active users — show signs of suicidal intent and/or excessive emotional attachment to the chatbot, OpenAI revealed. The company said it has made its models more responsive to such issues, paving the way to provide interactions geared toward adults who don't suffer from distress.

OpenAI 发现用户困扰：OpenAI 透露，在 ChatGPT 每周约 8 亿的活跃用户中，约有 0.15%（即近 120 万人）表现出自杀倾向和 / 或对聊天机器人产生过度情感依赖的迹象。该公司表示，已改进其模型，使其能更好地识别和处理此类问题。这有助于为那些没有此类困扰的成年用户提供更顺畅、更自然的互动体验。

* OpenAI updated ChatGPT to avoid encouraging certain groups of users to engage in dangerous and/or self-destructive behavior. The effort targets three vulnerable groups: (i) people with severe mental illnesses like psychosis or mania, (ii) people with depression and suicidal ideation, and (iii) people with excessive emotional attachments to AI.

* OpenAI 更新了 ChatGPT，旨在防止其鼓励部分用户做出危险或自我伤害的行为。此次改进主要关注三个易受影响的群体：(i）患有严重精神障碍（例如精神分裂症或双相情感障碍躁狂发作）的人，(ii）受抑郁情绪困扰且有自杀念头的人，以及（iii）对人工智能产生过度情感依赖的人。

* In a test of 1,000 mental health-related conversations, the new version of GPT-5 boosted desired responses to mental-health crises from 27 percent to 92 percent, and reduced undesired responses by 65 percent. For suicidal conversations, the rate of desired responses rose from 77 percent to 91 percent, and the rate of undesired responses fell by 65 percent. Conversations that showed signs of excessive attachment saw undesired responses drop by 80 percent and desired responses rise by 50 percent to 97 percent.

* 在一项针对 1000 次心理健康相关对话的测试中，新版 GPT-5 在面对心理危机时，给出恰当回应的比例从 27% 大幅提升至 92%，同时将不恰当回应的比例降低了 65%。在涉及自杀倾向的对话中，恰当回应的比例从 77% 提高到了 91%，不恰当回应的比例同样下降了 65%。而在那些表现出过度情感依赖迹象的对话中，不恰当回应的比例骤降了 80%，恰当回应的比例则从约 47% 跃升至 97%（提升了约 50 个百分点）。

* Sam Altman wrote on the social network X that, given the company's progress in providing psychologically sensitive output and restricting output based on users' ages, it would provide output geared toward verified adults, including erotica, beginning in December.

* Sam Altman 在社交平台 X 上发文称，鉴于公司在处理心理敏感内容以及实施基于用户年龄的内容限制方面取得了进展，从 12 月开始，公司将向已验证身份的成年用户提供包含色情内容在内的、面向成年人的内容。

Behind the news: Both Character.AI and OpenAI were sued by families of underage users who committed suicide after they conversed with their chatbots. In the U.S., California recently passed a state law that outlaws exposing minors to sexual content and requires supporting users who are suicidal and otherwise at risk psychologically. In August, 44 state attorneys general warned xAI, Meta, and OpenAI to restrict sexually explicit material as much as possible. xAI openly embraced adult interactions in July, when it introduced sexually explicit chatbots.

新闻背景：Character.AI 和 OpenAI 均遭到起诉，起诉方是那些在与聊天机器人对话后自杀的未成年用户的家属。在美国，加利福尼亚州近期通过了一项州法律，禁止让未成年人接触色情内容，并要求为有自杀倾向或存在其他心理风险的用户提供支持。八月，44 个州的检察长联合警告 xAI、Meta 和 OpenAI，要求它们尽可能限制性露骨内容。而 xAI 则在七月公开允许成人互动内容，当时它推出了涉及性露骨话题的聊天机器人。

Why it matters: Chatbot companionship is a growing phenomenon, and companies that offer such services — or simply chat — must be ready to manage emotional relationships between users and their software. Managing sexually charged interactions and conversations about mental illness are linked under the umbrella of building guardrails. Sycophancy also plays a role, since models that are prone to agreeing with users can encourage dangerous behavior. A depressed, underage user and a permissive chatbot make a worrisome combination.

重要性在于：将聊天机器人作为伴侣的现象日益普遍，因此，提供此类陪伴服务或仅仅具备聊天功能的公司，必须准备好管理用户与软件之间可能产生的情感依赖。无论是处理带有性暗示的互动，还是讨论心理健康问题，都属于构建安全护栏（即设定行为边界和规则）的范畴。此外，模型的「谄媚」倾向 —— 即倾向于迎合用户 —— 也可能助长危险行为。一个情绪抑郁的未成年用户，加上一个百依百顺的聊天机器人，这无疑是一个令人担忧的组合。

We're thinking: Mental health is a hard problem, in part because it affects so many people. A recent study shows that 5.3 percent of Americans had suicidal thoughts in 2024 — far higher than ChatGPT users' 0.15 percent. It's important that chatbot providers do what they can to help troubled users get help.

我们意识到：心理健康是一个严峻的挑战，部分原因在于其影响范围极广。最近的一项研究显示，2024 年有 5.3% 的美国人曾产生自杀念头，这一比例远高于 ChatGPT 用户中 0.15% 的占比。因此，聊天机器人（Chatbot）提供商尽力为遇到困扰的用户提供帮助渠道至关重要。

#### Better Images Through Reasoning

A new image generator reasons over prompts to produce outstanding pictures.

#### 更优图像，源于推理一款全新的图像生成器能对提示词进行推理，从而生成效果出众的图片。

What's new: Tencent released HunyuanImage-3.0, which is fine-tuned to apply reasoning via a variety of reinforcement learning methods. The company says this helps it understand users' intentions and improve its output.

最新消息：腾讯发布了其混元图像生成模型 HunyuanImage-3.0。该模型经过专门微调，具备了通过多种强化学习方法进行推理的能力。腾讯表示，这一特性有助于模型更好地理解用户意图，从而生成更符合要求的图像。

* Input/output: Text and images in, text and images out (fine-tuned for text in, images out only)

* Architecture: Mixture of experts (MoE) diffusion transformer (80 billion parameters, 13 billion parameters active per token), one VAE, one vision transformer, two vanilla neural network projectors

*  输入 / 输出：支持文本和图像输入，输出文本和图像（专为文本输入、图像输出的任务进行过微调）。

*  架构：采用混合专家（Mixture of Experts，MoE）扩散 Transformer 架构，总参数量为 800 亿，每 Token 激活的参数量为 130 亿。该架构包含一个变分自编码器（VAE）、一个视觉 Transformer（ViT）以及两个标准神经网络投影层。

* Performance: Currently tops LMArena Text-to-Image leaderboard

* Availability: Weights available for commercial and noncommercial use by companies with fewer than 100 million monthly active users under Tencent license

*  ** 表现 **：目前高居 LMArena 文本到图像（Text-to-Image）排行榜榜首
*  ** 可用性 **：根据腾讯的许可协议，月活跃用户数少于 1 亿的公司可获取模型权重，用于商业或非商业用途。

* Undisclosed: Input and output size limits; parameter counts of VAE, vision transformer, and projectors; training data; models used for labeling, filtering, and captioning images; reward models

* 未披露：输入与输出的尺寸限制；变分自编码器（VAE）、视觉 Transformer（Vision Transformer）以及各投影器（projectors）的参数数量；训练数据；用于图像标注、过滤和描述生成（captioning）的模型；奖励模型（reward models）。

How it works: The authors built a training dataset of paired text and images. They trained the model on image generation via diffusion through several stages and fine-tuned it on text-to-image generation in further stages.

它的工作原理是这样的：研究团队首先构建了一个由文本和对应图像配对组成的训练数据集。接着，他们分多个阶段训练模型，使其学会利用扩散（Diffusion）过程来生成图像。最后，在进一步的训练阶段，模型又在文本生成图像（text-to-image generation）这一特定任务上进行了微调（fine-tuned）。

* To produce the dataset, the authors collected 10 billion images. (i) They built models specially trained to measure image clarity and aesthetic quality, and removed images that didn't make the grade. (ii) They also built models to identify text and named entities such as brands, artworks, and celebrities, and extracted this information from the remaining images. (iii) They fed the images, extracted text, and extracted entities to a captioning model that produced a text caption for each image. (iv) For a subset of the data, they manually annotated chains of thought, producing data that linked text to chains of thought to images. (v) They added text-to-text data and image-text data from unspecified corpi.

* 为构建该数据集，作者们收集了 100 亿张图像。
(i）他们训练了专门的模型来评估图像的清晰度与美学质量，并筛除了不达标的图像。
(ii）他们还构建了用于识别文本及命名实体（例如品牌、艺术作品和名人）的模型，并从筛选后的图像中提取了这类信息。
(iii）随后，他们将图像、提取出的文本以及实体信息一并输入一个图像描述生成模型（captioning model），该模型为每张图像生成了对应的文本描述。
(iv）针对部分数据子集，他们人工编写了思维链（chain of thought），从而产生了将文本、思维链以及图像相互关联的数据。
(v）此外，他们还从未具体说明的语料库（corpora）中补充了文本到文本（text-to-text）数据以及图像 - 文本（image-text）数据。

* The authors pretrained the system to generate text and images from the various text and image elements in the dataset. Specifically, for text-to-image tasks: (i) First, the VAE's encoder embedded an image. (ii) The authors added noise to the embedding. (iii) Given the noisy embedding and a text prompt, the MoE removed the noise. (iv) The VAE's decoder generated an image from the embedding with noise removed.

* 作者们对该系统进行了预训练，使其能够根据数据集中的各类文本和图像元素生成文本和图像。具体到文生图任务，其流程如下：(i）首先，变分自编码器（VAE）的编码器将输入图像编码为一个嵌入表示。(ii）随后，向这个嵌入表示中添加噪声。(iii）接着，混合专家模型（MoE）会结合给定的文本提示，对这个带噪声的嵌入表示进行去噪。(iv）最后，VAE 的解码器根据去噪后的嵌入表示重建出最终的图像。

* The authors fine-tuned the system (i) for text-to-image tasks by training it in a supervised fashion to remove noise from human-annotated examples, (ii) via DPO to be more likely to generate higher-quality examples, like human-annotated ones, than lower-quality ones, (iii) via the reinforcement learning method MixGRPO to encourage the model to generate more aesthetically pleasing images as judged by unspecified reward models, and (iv) via SRPO (another reinforcement learning method) to encourage the model to generate images more like a text description that specified desired traits and less like a text description that specified negative traits. While applying SRPO, they also encouraged the model to generate images similar to those in an author-chosen distribution.

* 作者们通过以下方式对系统进行了微调：(i）针对文本到图像（text-to-image）任务，采用监督学习的方式，训练模型去除人工标注示例中的噪声；(ii）通过 DPO（Direct Preference Optimization），使模型更倾向于生成类似人工标注示例的高质量图像，而非低质量图像；(iii）通过强化学习方法 MixGRPO，激励模型生成在审美上更具吸引力的图像（其评判标准基于未公开的奖励模型）；(iv）通过另一种强化学习方法 SRPO（Style Reward Preference Optimization），鼓励模型生成的图像更符合指定了期望特征的文本描述，而非符合指定了负面特征的文本描述。在应用 SRPO 的同时，他们还引导模型生成的图像风格向作者选定的一组参考图像靠拢。

Results: At present, HunyuanImage 3.0 holds first place in the LMArena Text-to-Image leaderboard, ahead of Google Gemini 2.5 Flash Image (Nano Banana), Google Imagen 4.0 Ultra Generate, and ByteDance Seedream 4.0. In addition, 100 people compared 1,000 outputs of 4 competing models to those of HunyuanImage 3.0 in side-by-side contests. The people evaluated which image was better, or whether they were both equally good or equally poor.

结果：目前，混元图（HunyuanImage）3.0 在 LMArena 文生图（Text-to-Image）排行榜中位列第一，领先于 Google Gemini 2.5 Flash Image（Nano Banana）、Google Imagen 4.0 Ultra Generate 以及字节跳动的 Seedream 4.0。此外，我们还组织了一项人工评测：100 名评测者通过盲测（side-by-side contest）的方式，将上述 4 个竞争模型与混元图 3.0 的生成结果进行了总计 1000 组的成对比较。评测者需要判断哪张图片更优，或者两者质量相当（包括均好或均差）。

* On average, the people preferred HunyuanImage 3.0's images over those of the competitors.

* For example, 20.01 percent of the time they preferred HunyuanImage 3.0, 18.84 percent of the time they preferred Seedream 4.0, 39.3 percent of the time they were equally good, and 21.85 percent of the time they were equally poor.

* 总体来看，与竞争对手相比，人们更青睐 HunyuanImage 3.0 生成的图像。
* 具体来说，在偏好选择中：20.01% 的情况人们更偏好 HunyuanImage 3.0，18.84% 的情况更偏好 Seedream 4.0，39.3% 的情况认为两者图像质量相当，另有 21.85% 的情况则认为两者都不够理想。

Behind the news: Tencent has been on a streak of releasing vision models.

* Tencent recently launched the API version of Hunyuan-Vision-1.5, its latest vision-language model, with promises to release the weights and a paper soon.

新闻背后：腾讯近期在视觉模型领域动作频频。

* 腾讯近日推出了其最新的视觉语言模型 Hunyuan-Vision-1.5 的 API 版本，并承诺相关权重和论文也将很快发布。

* The company released Hunyuan3D-Omni, a model that takes an image and rough 3D representation (such as a skeleton or bounding box) and generates a detailed 3D representation.

* 该公司推出了 Hunyuan3D-Omni 模型。该模型能够接收一张图片和一个粗略的 3D 结构（例如骨架或边界框），并据此生成一个精细的 3D 模型。

* It also played a role in the release of FlashWorld, which accepts an image and text prompt and generates a 3D scene.

Why it matters: Simplifying training methods can be helpful, since each additional step adds time spent not only training but also debugging, and each additional component can interact with other components in unexpected ways, which adds to the time required to debug the system. Yet Tencent used several stages of pretraining and fine-tuning and produced a superior model.

* 它也在 FlashWorld 的发布中扮演了角色。FlashWorld 能够接受一张图像和一段文本提示，并据此生成一个 3D 场景。

其重要性在于：简化训练方法通常是有益的，因为每增加一个步骤，不仅会延长训练耗时，也会增加调试时间。并且，每一个新增的组件都可能与其他组件发生意想不到的交互，从而进一步拉长整个系统的调试周期。然而，腾讯采用了多阶段的预训练和微调策略，最终打造出了一个性能更为优越的模型。

We're thinking: One key to this success may be to use different methods for different purposes. For instance, the team used MixGRPO to fine-tune the model for aesthetics and SRPO to better match human preferences.

我们认为，成功的关键之一或许在于「对症下药」，即针对不同目标采用不同方法。例如，该团队利用 MixGRPO 在美学方面对模型进行微调，同时采用 SRPO 来使模型更好地对齐人类偏好。

#### The Year AI Went Industrial

A year-in-review report heralds the dawn of AI's industrial era.

#### AI 步入工业化的一年一份年度回顾报告宣告了 AI 工业化时代的到来。

What's new: The eighth annual State of AI Report 2025 aims to reflect the trajectory of AI through a selection of significant work from the past 12 months. It declares 2025 to be the beginning of the industrial age of AI, noting that the barriers to the technology's economic potential have shifted from technical limitations to matters of capital, politics, and physics. Nathan Benaich, a venture investor, led the effort and acknowledges unspecified conflicts of interest.

新看点：第八份年度《2025 年人工智能现状报告》于近日发布。报告旨在通过梳理过去一年的重要进展，来勾勒人工智能（AI）的发展轨迹。其中指出，2025 年标志着人工智能产业化时代的开端，该技术实现经济潜力的主要障碍，已从技术限制转变为资本、政治和物理学（如算力）层面的挑战。本报告由风险投资人 Nathan Benaich 牵头编撰，他同时声明报告中存在未具体指明的利益冲突。

How it works: The sprawling 300-slide deck highlights the year's progress in research, industry, politics, and security.

Research: Introduced late last year, reasoning models have redefined the capabilities of large language models. OpenAI's closed models retained their lead despite strong progress among open-weights competitors, especially China-based developers DeepSeek, Alibaba, and Moonshot. Such models showed significant gains in efficiency, shrinking numbers of trainable parameters by as much as 50 times while maintaining high performance. Models from OpenAI, Google, and Harmonic achieved gold-level performance on problems from the International Mathematical Olympiad, and the medical dialog model AIME outperformed unassisted doctors in diagnostic accuracy.

运作机制：这份内容庞杂、长达 300 页的幻灯片演示文稿，重点勾勒了本年度在研究、产业、政治与安全领域取得的进展。

研究：自去年年底问世以来，推理模型（Reasoning Models）重新定义了大语言模型的能力边界。尽管来自开源模型（Open-weights Models）的竞争者 —— 尤其是中国的深度求索（DeepSeek）、阿里巴巴和月之暗面（Moonshot)—— 取得了长足进步，但 OpenAI 的闭源模型依然保持着领先优势。这类模型在效率方面提升显著，在保持高性能的同时，将可训练参数的数量大幅缩减至原来的五十分之一。来自 OpenAI、谷歌和 Harmonic 的模型，在国际数学奥林匹克竞赛的题目上达到了金牌水准；而医疗对话模型 AIME 在诊断准确率上，甚至超越了未借助 AI 辅助的医生。

Industry: Demand for AI services mounted. According to Ramp Business Corporation, which maintains an index of AI adoption by U.S. companies, 44 percent of U.S. companies pay for AI tools, up from 5 percent in 2023. A cohort of 16 companies made nearly $18.5 billion in annualized revenue as of August, demonstrating a business case that gave some confidence to extend their financial commitments into hundreds of billions of dollars. Anticipating further growth, OpenAI and others committed to hundreds of billions of dollars to build data centers, and the availability of electrical power to drive such facilities emerged as a major issue that will shape the path forward. Among providers of closed models, OpenAI led not only in capability but also in price: GPT-5 costs 12 times less than Anthropic Claude Opus for roughly comparable performance.

行业：AI 服务需求持续攀升。根据 Ramp Business Corporation 的数据（该公司维护着一项美国企业 AI 采用指数），目前有 44% 的美国企业为 AI 工具付费，而 2023 年这一比例仅为 5%。截至 8 月，某 16 家公司实现了近 185 亿美元的年化收入，这证明了其商业模式的可行性，也让业界有信心将未来的资金投入规模扩大到数千亿美元。出于对增长的预期，OpenAI 等公司已承诺投入数千亿美元建设数据中心，而驱动这些设施的电力供应问题，已成为一个将影响未来行业走向的主要制约因素。在闭源模型提供商中，OpenAI 不仅在能力上领先，价格也更具优势：在性能大致相当的情况下，GPT-5 的成本仅为 Anthropic Claude Opus 的十二分之一。

Politics: National regulators in Europe and the U.S. backed off as they faced the prospect that overregulation might stymie AI's potential to drive economic growth. OpenAI, Meta, Google, and others lobbied to pre-empt state-level laws even as California forged ahead with its own legislation, which Anthropic supported. Internationally, the race to advance AI technology intensified. The U.S. launched an America-first AI strategy, blocking U.S. AI technologies from rivals, distributing it to allies, expediting permits for data-center sites, and providing the sites themselves. China responded by accelerating its efforts to build its domestic AI industry, and Chinese companies displaced Meta as premier suppliers of open-weights models.

政治：面对过度监管可能扼杀 AI 驱动经济增长的前景，欧洲和美国国家监管机构的态度有所缓和。OpenAI、Meta、Google 等公司积极游说，试图抢先制定州级法规，尽管加利福尼亚州仍在推进其自身的立法进程，并得到了 Anthropic 的支持。在国际层面，推进 AI 技术的竞赛日趋激烈。美国推出了「美国优先」的 AI 战略，内容包括：阻止关键 AI 技术流向竞争对手、向盟友提供这些技术、加快数据中心建设的审批流程以及提供相关场地资源。作为回应，中国加速发展本土 AI 产业，其公司也取代 Meta，成为了开源权重模型的主要供应者。

Security: Cybersecurity concerns rose as one analysis estimated that offensive capabilities are doubling every 5 months. Criminals successfully used Claude Code to create false identities that gained remote employment at Fortune 500 companies, and researchers demonstrated that it's possible to disable safety guardrails of open-weights models using minimal processing power. Anthropic and OpenAI responded to concerns that their models might be used to develop biological or chemical weapons by adopting preemptive safety measures.

安全：网络安全问题日益凸显，有分析估计，网络攻击能力正以每 5 个月翻一番的速度增长。犯罪分子利用 Claude Code 成功伪造身份，并借此在《财富》500 强公司获得了远程职位。此外，研究人员证明，仅需极少的算力就有可能绕过开放权重模型的安全防护机制。针对其模型可能被用于开发生物或化学武器的担忧，Anthropic 和 OpenAI 均已采取先发制人的安全措施予以应对。

Why it matters: State of AI Report 2025 brings into focus notable trends in AI over the past year and presents them with detailed context and evidence. It's chock-full of information that weaves diverse threads into coherent lines of progress. Moreover, it provides a consistent perspective on outstanding developments from year to year.

** 报告的意义 **：《2025 年人工智能现状报告》不仅系统梳理了过去一年 AI 领域的显著趋势，还为其提供了详实的背景与证据支撑。报告内容翔实，将纷繁的线索编织成清晰的进展脉络。更重要的是，它为理解人工智能历年的重大突破，提供了一个连贯且深入的观察视角。

We're thinking: By the authors' own reckoning, half of their 2024 predictions came to pass (more or less). This year's predictions mostly seem like matters of course. For instance, AI agents will purchase greater than 5 percent of a major retailer's annual online sales, a movie produced using AI will attract a large audience, and resistance to building data centers will sway U.S. state-level elections. But it also includes the alarming, and imaginable, prospect that an event driven by deepfakery or agents will trigger a NATO emergency. The need for AI practitioners to attend to ethical and security concerns is as high as ever.

我们认为：根据作者自己的统计，他们 2024 年的预测大约有一半成为了现实。而今年的预测大多看起来顺理成章。例如，AI 智能体将完成一家大型零售商年度在线销售额 5% 以上的交易，一部利用 AI 制作的电影将吸引大量观众，对建设数据中心的抵制情绪将影响美国州一级的选举。但预测中也包含了一个令人担忧且不难想象的前景：由深度伪造（Deepfake）或 AI 智能体引发的事件，可能导致北约启动紧急机制。对于 AI 从业者而言，重视伦理与安全问题的迫切性，依然丝毫未减。

#### Forecasting Multiple Time Series

Transformers are well suited to predicting future values of time series like energy prices, wages, or weather, but often — as in those examples — multiple time series often influence one another. Researchers built a model that can forecast multiple time series simultaneously.

#### 预测多个时间序列

Transformer 模型非常适合预测时间序列的未来值，比如能源价格、工资或天气。然而，在这些场景中，多个时间序列之间常常会相互影响。为此，研究人员构建了一个能够同时预测多个时间序列的模型。

What's new: Chronos-2 is a pretrained model that can accept and predict multiple time series in a zero-shot manner to forecast series of a single variable (univariate forecasting), multiple variables (multivariate forecasting), and single variables that depend on other variables (covariate-informed forecasting). Its authors include Abdul Fatir Ansari, Oleksandr Shchur, Jaris Küken, and colleagues at Amazon, University of Freiburg, Johannes Kepler University Linz, Boston College, and Rutgers.

最新进展：Chronos-2 是一个预训练模型，它能够以零样本（Zero-shot）的方式，接收并预测多个时间序列。该模型适用于三种预测场景：对单一变量序列进行预测（单变量预测）、对多个变量序列进行预测（多变量预测），以及对一个受其他变量影响的单一变量序列进行预测（协变量信息预测）。该模型的作者包括 Abdul Fatir Ansari、Oleksandr Shchur、Jaris Küken，以及来自亚马逊、弗莱堡大学、林茨约翰内斯·开普勒大学、波士顿学院和罗格斯大学的研究人员。

* Input/output: Time series in (up to 8,192 time steps), time series out (up to 1,024 time steps)

* Architecture: Modified transformer, 120 million parameters

* 输入 / 输出：时间序列输入（最多 8,192 个时间步），时间序列输出（最多 1,024 个时间步）
* 架构：改进的 Transformer 架构，1.2 亿参数

* Performance: Lower error on average than 14 competing models

* Availability: Weights available for commercial and noncommercial uses under Apache 2.0 license

*  性能：在 14 个对比模型中，平均误差最低。
*  可用性：模型权重基于 Apache 2.0 许可证开源，允许商业和非商业用途。

How it works: Given any number of time series, Chronos 2 predicts values at multiple future time steps. Chronos 2 learned to minimize the difference between its predicted future values and ground truth values in subsets of datasets that contain univariate series (including synthetic data generated using methods from earlier work). They supplemented these datasets with synthetic multivariate and covariate data produced using a method devised by the authors: Their method generates multiple independent time series and then produces dependencies between them by applying mathematical transformations at the same time step and across time steps.

工作原理：给定任意数量的时间序列，Chronos 2 能够预测未来多个时间步的数值。其训练目标是，在那些包含单变量序列（其中也包括利用早期研究方法生成的合成数据）的数据集子集上，最小化模型预测的未来值与真实值之间的误差。此外，研究团队还采用作者自行设计的方法，生成了合成的多变量与协变量数据，用以扩充上述数据集。该方法首先生成多个独立的时间序列，随后通过在相同时刻以及跨时间步施加数学变换，从而在这些序列之间建立起依赖关系。

* Chronos 2 stacks each input time series to make a series of vectors, where each vector represents one time step. These values can be historical or future values that are known (such as dates of holidays or weather forecasts). For non-overlapping time series (for example, one past and one future), the model aligns the time series by the corresponding time step and adds zeros to either end to equalize the number of time steps.

* Chronos 2 会将每个输入的时间序列组合成一系列向量，每个向量代表一个时间步。这些数据可以是已知的历史观测值，也可以是预先知晓的未来信息（例如节假日安排或天气预报）。对于时间上不重叠的序列（比如一段过去数据和一段未来数据），模型会按照对应的时间步将它们对齐，并通过在序列的末端补零，使得所有序列的时间步数量保持一致。

* Given the series of vectors, the model splits them into non-overlapping patches, and a vanilla neural network with added skip connections, or residual network, turns each patch into an embedding.

* 对于给定的向量序列，模型会将其分割为一系列非重叠的片段（patch）。随后，一个基础的神经网络（该网络添加了跳跃连接，即残差网络结构）会将每个片段转化成一个嵌入（embedding）。

* Given the embeddings, it predicts values of each time series for a number of future time steps that haven't already been assigned a value.

* In addition to the attention layers that perform attention across a given time series, Chronos 2 includes what the authors call group attention layers. These layers process attention across time series, or more specifically, across groups of time series. The user specifies groups, so the model can produce multiple independent forecasts at once.

*  给定输入序列的嵌入表示，模型会预测每个时间序列在未来多个尚未观测到的时间步上的值。
*  除了对单个时间序列内部进行注意力计算的层之外，Chronos 2 还包含了作者称为「组注意力层」的模块。这些层的作用是在不同的时间序列之间，或者更具体地说，在用户定义的时间序列分组之间进行注意力计算。用户通过指定分组，使得模型能够一次性生成多个独立的预测。

Results: Across various benchmarks, Chronos 2 outperformed 14 competing zero-shot models according to their skill score, a measure of how much a model reduces the average difference in predicted values relative to a baseline (higher is better, one is a perfect score).

结果：在多项基准测试中，Chronos 2 的零样本（Zero-shot）预测技能分数超越了其他 14 个竞争模型。技能分数用于衡量模型预测值与基线预测的平均差异缩减程度（分数越高表示模型越好，1 分为满分）。

* Across univariate, multivariate, and covariate subsets of fev-bench, Chronos-2 achieved the highest skill score.

* On fev-bench, 100 realistic time-series tasks including single and multiple input and output time series, Chronos-2 (0.473) outperformed TiRex (0.426), which processes only univariate time series, and Toto-1.0 (0.407), which can process multivariate and covariate time series in some cases.

*  在 fev-bench 的单变量、多变量以及协变量子集测试中，Chronos-2 均取得了最高的技能评分。
*  在包含 100 个现实时间序列任务的 fev-bench 基准测试上，这些任务涵盖了单变量与多变量的输入输出场景，Chronos-2（0.473）的表现不仅优于仅能处理单变量时间序列的 TiRex（0.426），也超过了在某些情况下可处理多变量及协变量时间序列的 Toto-1.0（0.407）。

Behind the news: Most previous works, including the previous versions Chronos and Chronos-Bolt, predict only univariate time series. Later models like Toto-1.0 and COSMIC process multiple inputs or outputs in limited ways. For instance, Toto-1.0 processes multiple inputs and outputs, but the multiple inputs can only represent past information, not future or static information. COSMIC, on the other hand, can handle multiple inputs (past or future) but not multiple outputs.

研究背景：大多数早期研究，包括先前版本的 Chronos 和 Chronos-Bolt，都只能预测单变量时间序列。后续的模型，如 Toto-1.0 和 COSMIC，在处理多输入或多输出方面也存在局限。具体来说，Toto-1.0 虽然能处理多输入和多输出，但其多输入仅能表示过去的信息，无法包含未来或静态信息。而 COSMIC 模型则相反，它可以处理多个输入（无论是过去还是未来的信息），但却无法处理多个输出。

Why it matters: Chronos 2 can handle past, future, and static inputs as well as multiple outputs, giving developers, researchers, and companies alike the ability to better predict complex time series.

其重要性在于：Chronos 2 能够同时处理过去、未来的数据以及静态输入，并支持多输出预测。这使开发者、研究人员乃至各类企业，都能更精准地预测复杂的时间序列。

We're thinking: The author's attention setup is similar to the way many video transformers apply attention separately across space and time. It saves memory compared to performing attention across both at once, and remains an effective method for understanding data across both.


我们的想法是：作者采用的注意力机制，与许多视频 Transformer 模型分别沿空间维度和时间维度应用注意力的方式类似。相比于在空间和时间上同时进行注意力计算，这种方法能节省内存，并且依然是理解跨时空数据的有效手段。







I recently received an email titled "An 18-year-old's dilemma: Too late to contribute to AI?" Its author, who gave me permission to share this, is preparing for college. He is worried that by the time he graduates, AI will be so good there's no meaningful work left for him to do to contribute to humanity, and he will just live on Universal Basic Income (UBI). I wrote back to reassure him that there will still be plenty of work he can do for decades hence, and encouraged him to work hard and learn to build with AI. But this conversation struck me as an example of how harmful hype about AI is.

我最近收到了一封邮件，标题是「一个 18 岁的困境：对 AI 的贡献是否已经太晚？」这位作者允许我分享这段内容，他正在准备申请大学。他担心等到毕业时，AI 可能已经发展到无需人类参与的地步，自己将只能靠普遍基本收入（UBI）维持生计，无法再为社会做出有意义的贡献。我在回信中安慰他，未来几十年仍然有大量工作机会，并鼓励他努力学习，学会用 AI 来创造。但这段对话也让我深刻感受到，媒体对 AI 的过度炒作带来的负面影响。

Yes, AI is amazingly intelligent, and I'm thrilled to be using it every day to build things I couldn't have built a year ago. At the same time, AI is still incredibly dumb, and I would not trust a frontier LLM by itself to prioritize my calendar, carry out resumé screening, or choose what to order for lunch — tasks that businesses routinely ask junior personnel to do.

是的，AI 的智能确实让人惊叹，我每天都很高兴能用它来构建那些一年前还无法实现的东西。但与此同时，AI 有时又显得非常愚钝，我可不敢轻易让一个先进的大语言模型来管理我的日程、筛选简历，甚至决定今天午餐吃什么 —— 这些可是企业里初级员工的日常工作。

Yes, we can build AI software to do these tasks. For example, after a lot of customization work, one of my teams now has a decent AI resumé screener. But the point is it took a lot of customization.

是的，我们可以开发人工智能系统来完成这些任务。例如，经过大量调整后，我的一个团队现在拥有一个高效的 AI 简历筛选器。但重点在于，这需要大量的定制工作。

Even though LLMs can handle a much more general set of tasks than previous iterations of AI technology, compared to what humans can do, they are still highly specialized. They're much better at working with text than other modalities, still require lots of custom engineering to get it the right context for a particular application, and we have few tools — and only inefficient ones — for getting our systems to learn from feedback and repeated exposure to a specific task (such as screening resumés for a particular role).

虽然大语言模型能够处理比以往人工智能技术更广泛的任务，但与人类的能力相比，它们仍然有很大的局限性。大语言模型在处理文本方面比处理其他数据类型（例如图像、音频等）更擅长，在实际应用中仍然需要大量的定制开发来提供适合特定场景的上下文。此外，我们缺乏有效的工具，来帮助系统从反馈和重复执行特定任务（例如筛选特定职位的简历）中学习和改进。

AI has stark limitations, and despite rapid improvements, it will remain limited compared to humans for a long time.

AI is amazing, but it has unfortunately been hyped up to be even more amazing than it is. A pernicious aspect of hype is that it often contains an element of truth, but not to the degree of the hype. This makes it difficult for nontechnical people to discern where the truth really is. Modern AI is a general purpose technology that is enabling many applications, but AI that can do any intellectual tasks that a human can (a popular definition for AGI) is still decades away or longer. This nuanced message that AI is general, but not that general, often is lost in the noise of today's media environment.

AI 存在显著的局限性，尽管它正在飞速进步，但与人类相比， AI 在相当长的一段时间内仍然存在局限。

AI 确实非常强大，但不幸的是，它被过度炒作，以至于人们认为它比实际上更强大。炒作的一个弊端在于，它通常包含某些真实成分，但实际情况却远不如炒作所描绘的那样。这使得非技术人士很难分辨哪些是真实可信的。现代 AI 是一项应用广泛的通用技术，正在推动许多领域的应用发展，但能够像人类一样完成任何智力任务的 AI（即通用人工智能的常见定义）可能还要数十年甚至更长的时间才能实现。然而，这一微妙的信息 —— 即 AI 虽然通用但并非万能 —— 常常在当今喧嚣的媒体环境中被淹没。

Similarly, the progress of frontier models is amazing! But not so amazing that they'll be able to do everything under the sun without a lot of customization. I know VC investors who are scared to invest in application-layer startups because they are worried that frontier AI model companies will quickly wipe out all of these businesses by improving their models. While some thin wrappers around LLMs no doubt will be replaced, there also remains a huge set of valuable applications that the current trajectory of progress of frontier models won't displace for a long time.

近来，前沿模型的发展速度确实令人惊叹！然而，它们并不会在短期内凭借现有能力就能完成所有任务，而不需要针对性的定制和优化。我认识一些风险投资人，他们对投资应用层的初创公司持谨慎态度，担忧前沿 AI 模型公司通过不断迭代模型，可能侵占这些应用的市场。虽然那些简单包装大语言模型的应用确实面临被替代的风险，但仍然有大量高价值的应用场景，在可预见的未来，前沿模型的发展趋势尚无法完全覆盖或取代它们。

Without accurate information about the current state of AI and how it is likely to progress, some young people will decide not to enter AI because they think AGI leaves them no meaningful role, or decide not to learn how to code because they fear AI will automate it — right when it is the best time ever to join our field.

如果缺乏关于人工智能当前发展水平和未来趋势的准确信息，一些年轻人可能会因误解而放弃进入这一领域。他们可能认为通用人工智能（AGI）会让他们无所作为，或担心人工智能将完全取代编码技能，进而放弃学习编程。然而，此刻其实正是加入人工智能行业的最好时机。

Let us all keep working to get to a precise understanding of what's actually possible, and keep building!


让我们继续携手努力，深入理解哪些是切实可行的，并不断推动技术的发展！
