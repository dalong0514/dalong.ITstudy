## 20250326Compact-Vision-Language-with-Open-Weights-Faster-Learning-Diffusion-in-Few-Steps-LLMs-Aid-Tutors

[Compact Vision-Language with Open Weights, Faster Learning, Diffusion in Few Steps, LLMs Aid Tutors](https://www.deeplearning.ai/the-batch/issue-294/)

Dear friends,

Fine-tuning small language models has been gaining traction over the past half year. I'd like to share my sense of when to use this technique，and also when not to，based on what I'm seeing in multiple companies.

过去半年来，微调小型语言模型（small language models）的热度持续攀升。基于我在多家公司的实际观察，我想和大家分享：在哪些场景下适合采用这项技术，哪些情况下则不太适用。

First，while fine-tuning is an important and valuable technique，many teams that are currently using it probably could get good results with simpler approaches，such as prompting（including writing mega prompts），few-shot prompting，or simple agentic workflows.

首先，虽然微调（fine-tuning）是一项重要且有价值的技术，但许多正在使用它的团队其实可以通过更简单的方法获得不错的效果，比如提示工程（prompting）(包括编写复合提示（mega prompts)）、少样本提示（few-shot prompting），或者简单的 AI 智能体工作流程（agentic workflows）。

Why shouldn't these teams be fine-tuning? Because fine-tuning，which takes a pre-trained model and further trains it on data specific to an application，is relatively complex to implement. You need to collect training data，then（unless you want to implement fine-tuning yourself）find a provider to help with running fine-tuning，then find a way to deploy the fine-tuned model. Because it adds extra complexity both in training and deployment，usually I resort to this technique only after I find that prompting and simple agentic workflows are not up to a task.

这些团队不选择微调（fine-tuning）的原因在于：微调技术需要基于预训练模型，使用特定应用场景的数据进行二次训练，其实施过程较为复杂。首先需要收集训练数据，然后（除非自主实现微调）需要寻找合适的服务商协助完成微调过程，最后还需部署优化后的模型。由于微调会显著增加模型训练和部署的复杂度，我通常只在确认提示工程（prompting）和基础 AI 智能体（AI Agent）工作流无法满足需求时，才会考虑采用这种方案。

Having said that，there are also applications where fine-tuning is appropriate and valuable. LoRA（which learns by modifying a limited number of parameters rather than the entire model）and related methods have made fine-tuning quite affordable，particularly for small models（say，13B or fewer parameters). And the amount of data needed to get started is less than most people think. Depending on the application，I've seen good results with 100 or even fewer examples. Here are a few applications where I have seen fine-tuning applied successfully:

不过话说回来，在某些应用场景中，微调（fine-tuning）确实非常合适且有价值。LoRA（通过仅修改少量参数而非整个模型来实现学习）这类方法大大降低了微调成本，特别适合参数量较小的模型（比如 13B 参数或更少）。而且所需训练数据量往往比人们想象的要少得多 —— 根据具体任务不同，有时仅用 100 个甚至更少的样本就能获得不错的效果。以下是我观察到的几个微调成功案例：

1 Improving accuracy of critical applications. Prompting can get you really far for many applications. But sometimes，fine-tuning helps eke out that last bit of accuracy. For example，if you are building a customer service chatbot and need it to call the right API reliably（say，to carry out transactions，issue refunds，and the like），perhaps prompting can get it to make the right API call 95% of the time. But if you struggle to raise the accuracy even with revisions to the prompt and you really need 99% accuracy，fine-tuning on a dataset of conversations and API calls might be a good way to get you there. This is particularly true for tasks where it's hard to specify，using only language，an unambiguous rule to decide what to do. For example，when a customer is frustrated，should the chatbot escalate to a manager or just issue a refund? Teams often write Standard Operating Procedures（SOPs）for human workers to follow，and these SOPs can go into the prompts of models. But if it is hard to specify an unambiguous SOP，so even humans need to see numerous examples before they can learn what to do，fine-tuning can be a good approach. For many text-classification applications fine-tuning also works well，for example，classifying medical records into diagnosis and procedure codes for health insurance claims.

提升关键应用的准确性。提示工程（Prompting）在多数场景下都能取得不错的效果，但有时微调（fine-tuning）能帮助我们突破最后的性能瓶颈。比如，当你开发客户服务聊天机器人时，若需要确保它能准确调用 API（如完成交易、处理退款等操作），提示工程可能实现 95% 的正确率。但如果即使优化提示也难以达到 99% 的准确率要求，那么基于真实对话和 API 调用记录的数据集进行微调就是理想选择。这种方法特别适用于那些难以用自然语言明确制定决策规则的任务。例如，当客户表达不满时，聊天机器人应该转接人工客服还是直接退款？企业通常会制定标准操作流程（SOPs）来指导人工客服，这些 SOPs 可以直接整合到模型提示中。但当规则过于复杂，连人类都需要大量案例学习才能掌握时，微调就是更有效的方案。在文本分类任务中，微调同样表现出色，比如将电子病历分类为诊断代码和手术代码，用于医疗保险理赔场景。

2 Learning a particular  style of communication. As I explain in「Generative AI for Everyone,」my team fine-tuned a model to sound like me. Many people（including myself）have idiosyncratic uses of language. There are certain words I tend to say and others I tend not to，and these idiosyncrasies are numerous and very difficult to specify in a text prompt.（By the way，the avatar at deeplearning.ai/avatar，built with RealAvatar，uses fine-tuning for this reason.）To get a system to communicate in a certain style，fine-tuning is often a superior solution to prompting alone.

学习特定的沟通风格。正如我在《Generative AI for Everyone》中解释的那样，我的团队对一个模型进行了微调（fine-tuning），使其能够模仿我的说话风格。许多人（包括我自己）都有独特的语言习惯 —— 有些词我常用，有些词则很少用，而这些细微的偏好数量庞大，很难通过文本提示（text prompt）逐一说明。（顺便提一句，deeplearning.ai/avatar 上的虚拟形象正是基于这个原因，通过 RealAvatar 的微调技术实现的。）要让系统掌握特定的表达风格，微调通常比单纯使用提示（prompting）更有效。

3 Reducing latency or cost during scale-ups. I've seen applications where developers have successfully prompted a large model to perform a complex task. But as usage scales up，if the large model is too slow（which often happens）or too expensive（which also happens but less frequently），the team might want to use a smaller model. If，however，the performance of the smaller model isn't good enough，then fine-tuning it can help bring it up to the performance of the larger one for that narrow application. Further，the larger model（or perhaps an agentic workflow）can also be used to generate data to help with fine-tuning the small model for that task.

在业务扩展时优化响应速度与成本。实际应用中，开发者常能通过精心设计的提示词（prompt）让大语言模型处理复杂任务。但随着用户量增长，大模型可能面临响应延迟过高（这种情况很常见）或计算成本激增（相对少见但确实存在）的问题，此时团队往往会考虑改用轻量级模型。若轻量级模型表现不佳，通过针对性的微调（fine-tuning）可使其在该特定场景下达到媲美大模型的性能。更有趣的是，我们还能利用大模型（或 AI 智能体工作流）来生成训练数据，从而为轻量级模型的微调提供支持。

4 At the cutting edge of research，some teams are fine-tuning models to get better at a certain language. But with few exceptions，if the goal is to get an LLM to better understand a body of knowledge that is not in its training data，I find that using RAG（retrieval augmented generation）is a much simpler approach，and I still occasionally run into teams using fine-tuning for which  I think RAG would work better.

在科研前沿领域，部分团队正通过微调（fine-tuning）来提升模型对特定语言的处理能力。但除非特殊情况，若要让大语言模型理解训练数据之外的知识体系，我认为检索增强生成（RAG，retrieval augmented generation）是更简便的方案。事实上，我仍会遇到一些执着于微调的团队，而这些场景下 RAG 往往能带来更好的效果。

Overall my sense is that，of all the teams I see using fine-tuning，perhaps 75% could get good results using simpler techniques（like prompting or agentic workflows），but in 25% of cases I know of no better way to achieve their goal.

根据我的观察，在使用模型微调（fine-tuning）的团队中，约 75% 其实可以通过更简单的技术获得理想效果，比如提示工程（prompting）或 AI 智能体工作流（agentic workflows）。但剩下的 25% 案例中，目前确实没有比微调更好的解决方案。

It is still technically challenging to implement fine-tuning，get the hyperparameters right，optimize the compute resources，and so on. We are lucky that more and more companies have worked hard to optimize these and provide efficient fine-tuning services. Many of them allow us to fine-tune open weights models and also download the fine-tuned weights. Some allow us to fine-tune their closed models and continue to keep the tuned weights closed. Both can be useful，but the former has obvious advantages of portability and not having to worry that the provider will stop serving a particular model，causing a critical component in our software to become deprecated.

技术上，进行模型微调、调整超参数以及优化计算资源仍存在挑战。值得庆幸的是，越来越多的服务商正着力优化这些技术环节，提供高效的微调服务。许多平台支持对开放权重模型进行微调并下载调整后的权重参数，也有些允许对其封闭模型微调但保留权重封闭性。两种方案各有价值，但开放权重方案具有明显的可移植优势，还能避免因服务商终止特定模型支持而导致软件关键组件失效的风险。

In conclusion，before fine-tuning，consider if you should be trying just a bit harder with prompting or agentic workflows，which can lead to simpler solutions that are easier to maintain. The vast majority of applications my teams build do not use any fine-tuning at all，but it's a critical piece of a small minority of them.

综上所述，在进行模型微调（fine-tuning）之前，建议先充分尝试提示工程（prompting）或 AI 智能体（AI Agent）工作流，这些方法往往能提供更简单且易于维护的解决方案。根据我们的实践经验，团队开发的大多数应用都不需要微调，只有极少数特殊场景才需要依赖这一关键技术。

Keep learning!

Andrew

### News

#### Vision-Language，Compact and Open

视觉-语言模型：紧凑与开放

Google updated its open-weights family of large language models to include versions that handle image and video inputs.

Google 更新了其开放权重的大语言模型家族，新增了支持图像和视频输入的版本。

What's new: Google released its Gemma 3 multilingual large language models with parameter counts of 1 billion，4 billion，12 billion，and 27 billion. While the smallest processes text only，the other three are vision-language models that are small enough to run on a consumer hardware.

最新动态：Google 推出 Gemma 3 多语言大语言模型，提供 10 亿、40 亿、120 亿和 270 亿四种参数量的版本。其中最小版本仅支持文本处理，其余三个则是视觉语言模型，其参数量级足够精简，甚至可以在普通电脑上运行。

1 Input/output: Gemma 3 1B：text-in（up to 32,000 tokens），text out（up to 8,192 tokens). Gemma 3 4B，7B，27B：text，images/video in（up to 128,000 tokens），text out（up to 8,192 tokens). Gemma 3 27B outputs 24.61 tokens per /second，0.68 seconds to first token.

输入 / 输出规格：
 - Gemma 3 1B：支持文本输入（最多 32,000 tokens），输出文本（最多 8,192 tokens）
 - Gemma 3 4B/7B/27B：支持文本、图像 / 视频输入（最多 128,000 tokens），输出文本（最多 8,192 tokens）
 - Gemma 3 27B 性能：生成速度 24.61 tokens / 秒，首 token 响应时间 0.68 秒

2 Knowledge cutoff: March 2024

知识截止时间：2024 年 3 月

3 Architecture: Gemma 3 1B：Transformer. Gemma 3 4B，12B，27B：Transformer，SigLIP  vision encoder.

架构：Gemma 3 1B：Transformer。Gemma 3 4B、12B、27B：Transformer，SigLIP 视觉编码器（SigLIP vision encoder）。

4 Features: 140 languages，function calling，structured output.

特性：支持 140 种语言、函数调用功能、结构化数据输出。

5 Training data: Gemma 3 1B：2 trillion tokens of web text，code，and mathematics. Gemma 3 4B，12B，27B：between 4 trillion and 14 trillion tokens of text and images.

训练数据：Gemma 3 1B：2 万亿 token（tokens）的网页文本、代码和数学数据。Gemma 3 4B、12B、27B：4-14 万亿 token 的文本和图像数据。

Availability/price: Weights free to download from Hugging Face and Kaggle under a license that allows noncommercial and commercial uses with some restrictions. Available free via Google's AI Studio.

可用性 / 价格：模型参数（weights）可从 Hugging Face 和 Kaggle 平台免费获取，采用允许非商业和商业用途（附带部分限制）的许可协议。用户还可以通过 Google 的 AI Studio 免费使用该模型。

How it works: Gemma 3 rearchitects and refines earlier Gemma models for higher performance at lower parameter counts.

工作原理：Gemma 3 对前代模型进行了架构重构和优化，用更少的参数实现了更强的性能。

1 To save memory，Gemma 3 interleaves five local attention layers for every global attention layer. Global attention layers attend to the entire input，while local attention layers attend to 1,024 tokens.

为节省内存占用，Gemma 3 采用 1:5 的全局-局部注意力层配比：每使用 1 个处理全部输入的全局注意力（global attention）层，就搭配 5 个仅处理 1,024 个 token 的局部注意力（local attention）层。

2 The models were fine-tuned to encourage their outputs to match those of an unspecified larger teacher model.

这些模型经过微调，旨在使其输出与某个更大的教师模型（具体型号未公开）的输出保持一致。

3 Gemma 3 learned via reinforcement learning in three ways.（i）The models were aligned with human preferences via reinforcement learning from human feedback (RLHF).（ii）They were fine-tuned to solve math problems via reinforcement learning，much like DeepSeek-R1.（iii）They were trained to generate better code via reinforcement learning from execution feedback（RLEF). Specifically，over several rounds of output，RLEF tested generated code on a subset of tests，then prompted the model to fix any bugs. RLEF rewarded the models if their final output passed all tests.

Gemma 3 通过三种强化学习方式进行训练：

（i）采用人类反馈强化学习（RLHF）技术，使模型行为符合人类偏好；
（ii）通过强化学习微调模型解决数学问题的能力，方法与 DeepSeek-R1 类似；
（iii）利用执行反馈强化学习（RLEF）提升代码生成质量。具体而言，RLEF 会在多轮迭代中：先用部分测试用例检验生成的代码，然后引导模型修正错误。只有当最终代码通过全部测试时，模型才会获得奖励。

Performance: Gemma 3 models outperform Gemma 2 models of equal or larger size by several measures，and all sizes show a strong ability to solve mathematics word problems as measured by MATH.

性能表现：Gemma 3 模型在多项指标上全面超越同级别或更大规模的 Gemma 2 模型。根据 MATH 基准测试结果，所有规模的 Gemma 3 模型都展现出解决数学文字题的卓越能力。

1 In Google's tests，Gemma 3 1B performs roughly comparably to Gemma 2 2B，outperforming the larger model on LiveCodeBench（1.9 percent to 1.2 percent）and MATH（48.0 percent to 27.2 percent).

Google 测试数据显示，Gemma 3 1B 性能接近 Gemma 2 2B，且在 LiveCodeBench（1.9% vs 1.2%）和 MATH（48.0% vs 27.2%）两个基准测试中表现优于更大的模型。

2 Gemma 3 4B achieves roughly comparable performance to Gemma 2 9B，Llama 3.1 8B，and Qwen2.5-7B. It's slightly behind Microsoft Phi-4 Mini（also 4 billion parameters），except on MATH，according to that company's tests.

Gemma 3 4B 的表现与 Gemma 2 9B、Llama 3.1 8B 和 Qwen2.5-7B 基本持平。测试数据显示，除了在 MATH 测试项目中稍逊一筹外，其性能略低于同为 40 亿参数的 Microsoft Phi-4 Mini。

3 Gemma 3 12B improves on Gemma 2 27B and compares to Gemini 1.5 Flash（in TIGER-Lab's tests）and Anthropic Claude 3.5 Haiku（in that developer's tests). It outperforms the larger，proprietary models on MATH.

Gemma 3 12B 相比前代 Gemma 2 27B 有了显著提升，其性能可与 Gemini 1.5 Flash（根据 TIGER-Lab 测试数据）和 Claude 3.5 Haiku（根据 Anthropic 官方测试）相媲美。特别值得注意的是，这款模型在 MATH 基准测试中的表现甚至超过了规模更大的闭源商业模型。

4 Moreover，Gemma 3 27B achieves 1,338 ELO in Chatbot Arena，a top-ten score that puts it ahead of OpenAI o1 and behind only DeepSeek-R1 among models with open weights.

此外，Gemma 3 27B 在 Chatbot Arena 评测中取得 1338 ELO 分，位列排行榜前十。在开放权重（open weights）模型中，其表现超越 OpenAI o1，仅次于 DeepSeek-R1。

Hot on Gemma 3's heels: Shortly after Gemma 3 became available，Mistral released Small 3.1 (24 billion parameters），a vision-language model with open weights，under a more permissive Apache 2.0 license.

紧追 Gemma 3 的步伐：就在 Gemma 3 发布后不久，Mistral 推出了 Small 3.1（规模达 240 亿参数），这是一个开放权重的视觉语言模型（vision-language model），采用了限制更少的 Apache 2.0 开源许可证。

1 Mistral Small 3.1 is similarly multilingual and offers a 128,000 token context window.

Mistral Small 3.1 同样具备多语言能力，并提供 128,000 token（标记）的上下文窗口。

2 It slightly outperforms Gemma 3 27B on MMLU，MMLU-Pro，MMMU，and other selected benchmarks.

在 MMLU（大规模多任务语言理解）、MMLU-Pro、MMMU 等多项评测中，其性能小幅领先 Gemma 3 27B 模型。

3 It also outperforms Gemma 3 27B and other models in its size range on long-context tests.（However，Gemma 3 27B performs better in the Chatbot Arena test of human preference.)

在长文本理解测试中，其表现优于 Gemma 3 27B 及同级别规模的其他模型（不过 Gemma 3 27B 在人类偏好评估平台 Chatbot Arena 的测试中表现更佳）。

Why it matters: Gemma 3 takes advantage of a variety of techniques to raise the bar for vision-language performance in relatively small models. Knowledge distillation，multiple rounds of reinforcement learning，and fine-tuning on many languages are a powerful combination.

关键突破：Gemma 3 通过多项技术创新，在较小规模的模型中实现了视觉-语言（vision-language）性能的显著提升。该模型融合了知识蒸馏（knowledge distillation）、多轮强化学习以及多语言微调三大技术，形成了强大的协同效应。

We're thinking: A vision-language model small enough to run on a smartphone feels increasingly close!

我们相信：能在智能手机上运行的轻量级视觉语言模型（Visual-Language Model）即将问世！

#### Better Images in Fewer Steps

更少步骤，更好画质

Diffusion models usually take many noise-removal steps to produce an image，which takes time at inference. There are ways to reduce the number of steps，but the resulting systems are less effective. Researchers devised a streamlined approach that doesn't sacrifice output quality.

扩散模型（Diffusion models）生成图像通常需要进行大量去噪步骤，导致推理过程耗时较长。虽然可以通过减少步骤数量来提速，但这样会降低生成质量。为此，研究人员开发了一种新型优化方案，在保持输出质量的同时显著提升了效率。

What's new: Kevin Frans and colleagues at UC Berkeley introduced shortcut models that learn to take larger noise-removal steps and thus require fewer steps to generate an image.

技术突破：加州大学伯克利分校的 Kevin Frans 及其团队提出了一种捷径模型（shortcut models），该模型能够学习执行更大的去噪跨度，从而显著减少图像生成所需的步骤。

Key insight: At inference，a scheduler like Euler can enable a model to take larger steps than those it learned during training，but this approach yields worse performance. Alternatively distillation，in which a student model learns to remove the same amount of noise as a teacher model when it takes several steps，offers improved performance at the cost of more cumbersome development. Training the model directly to take bigger steps — that are equivalent to multiple smaller steps — enables it to maintain high performance while taking fewer steps.

核心发现：在推理（inference）阶段，使用像 Euler 这样的调度器（scheduler）虽然能让模型采取比训练时更大的步长，但会降低生成质量。另一种蒸馏（distillation）方法让学生模型学会在多个步骤中去除与教师模型相当的噪声，虽然效果更好但开发过程更复杂。而直接训练模型采取更大的等效步长 —— 相当于合并多个小步长 —— 则能在减少计算步骤的同时保持优异性能。

How it works: The authors trained DiT-B，a diffusion transformer，to generate images like those in CelebA-HQ（celebrity faces）and ImageNet-256（various subjects，size 256x256).

实现方法：研究人员训练了一个名为 DiT-B 的扩散 Transformer（Diffusion Transformer），能够生成两类图像：一类是类似 CelebA-HQ 数据集中的名人面部照片，另一类是类似 ImageNet-256 数据集中包含多种主题的 256×256 像素图片。

1 The loss function included terms for flow matching and self-consistency. The flow matching term encouraged the model to learn to remove noise. The self-consistency term encouraged the model to learn how to minimize the discrepancy between the noise removed by a single big step and two smaller steps.

损失函数包含流匹配（flow matching）和自一致性（self-consistency）两项。流匹配项促使模型掌握去噪能力。自一致性项则让模型学会：用一个大步去噪的结果，与分成两个小步去噪的结果之间的差异要尽可能小。

2 Initially the model learned to combine two small steps into one step 2x as large. Combining two larger steps resulted in step sizes of 4x，8x，and so on，up to 128x.

模型最初学习将两个小步骤合并为一个两倍大小的步骤。通过持续合并更大的步骤，步长呈指数级增长，从 4 倍、8 倍逐步扩展，最终可达 128 倍。

3 At inference，the user told the model how many small steps to take，and the model computed the single-step size necessary to accomplish that.

在模型推理阶段，用户指定需要执行的微步数量，模型会据此计算出完成整体生成过程所需的单步步长。

Results: The authors compared their model using 1，4，or 128 steps to alternatives that were trained via various methods including many variants of distillation. They measured the results using Fréchet inception distance (FID），which assesses how closely generated images resemble real-world images（lower is better).

结果：作者将使用 1、4 或 128 步的模型与通过不同方法（包括多种蒸馏变体）训练的替代方案进行比较。评估采用 Fréchet 初始距离（FID，数值越低越好），该指标用于衡量生成图像与真实图像的相似程度。

1 On both CelebA-HQ and ImageNet-256，their model，when it took four steps，achieved the best performance. For example，on CelebA-HQ，using four steps，the shortcut model achieved 13.8 FID，while the next-best model, Reflow (another variant of distillation），achieved 18.4 FID.

在 CelebA-HQ 和 ImageNet-256 两个测试集上，当采用四步计算时，该研究团队提出的模型表现最优。以 CelebA-HQ 为例：四步计算的捷径模型获得了 13.8 的 FID（Frechet Inception Distance）分数，而表现次优的 Reflow 模型（蒸馏技术的另一种变体）的得分为 18.4。

2 When it took one step，it achieved the second-best result，behind progressive distillation，which trained a series of student models to remove the same amount of noise as a teacher model does when it takes multiple steps.

在单步执行时，该方法获得了次优成绩，仅次于渐进蒸馏（progressive distillation）—— 后者通过训练一系列学生模型，实现了与教师模型多步运算时相同的噪声去除效果。

Why it matters: Generating images by diffusion is typically costly，and previous approaches to cutting the cost have compromised either performance or incurred additional development expense or both. This method achieves high performance at relatively low cost.

重要意义：基于扩散模型（diffusion）的图像生成通常成本较高，以往降低成本的尝试往往需要在性能上做出妥协，或增加额外开发投入，甚至同时面临这两个问题。而新方法却能在控制成本的同时保持出色的生成效果。

We're thinking: As diffusion models continue to become cheaper and faster，we expect to see applications blossom!

我们认为：随着扩散模型（diffusion models）的成本持续降低、速度不断提升，其应用场景必将迎来爆发式增长！

#### LLM Support for Tutors

大语言模型在教育辅导中的应用

Students benefit from tutoring，but training tutors is expensive. A study shows that large language models can boost tutors' effectiveness in real time.

辅导能让学生受益匪浅，但培训辅导老师的成本却十分高昂。最新研究发现，大语言模型能够实时提升辅导老师的教学效率。

What's new: Rose Wang and colleagues at Stanford built Tutor CoPilot，a tool for remote，online tutors that uses GPT-4 to generate hints，explanations，questions，and other helpful responses to students.

创新成果：斯坦福大学的 Rose Wang 与研究团队开发了 Tutor CoPilot 智能辅导系统，这款专为远程在线辅导设计的工具，通过 GPT-4 实时生成学习提示、知识讲解、互动问题等对学生有益的辅导内容。

[[2410.03017] Tutor CoPilot: A Human-AI Approach for Scaling Real-Time Expertise](https://arxiv.org/abs/2410.03017?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9y2OPZmDPM8PgEFYb6bhb5cNMCCKhkdX7Wl9uZmgAeyu2O0jQbxa3F9xaorJPK6_obk1L7)

Key insight: When a student makes an error，according to previous work by some of the same authors，effective teachers choose a strategy for addressing the mistake. The authors identified 11 strategies，such as ask a question，explain a concept，provide a hint，or encourage the student. Moreover，they found that an LLM that executed a strategy chosen by an expert teacher performed significantly better than an LLM that was prompted with a strategy chosen at random or no specific strategy. Letting inexperienced tutors choose a strategy while an LLM generates a response helps them learn how to execute the strategy. Students，in turn，benefit from responses that mimic those of an experienced teacher.

核心发现：当学生出现错误时，根据该研究团队之前的成果，优秀教师会采取特定策略来纠正错误。研究者共归纳出 11 种教学策略，包括提问、解释概念、提供提示或给予鼓励等。实验表明，采用专家教师选定策略的大语言模型（LLM），其教学效果明显优于随机选择策略或没有明确策略指导的模型。这种让新手教师选择策略、由大语言模型生成回应的协作方式，能有效帮助教师掌握策略运用技巧。相应地，学生也能从这些借鉴资深教师经验的教学反馈中获得更大收益。

How it works: The authors outfitted a remote tutoring application with GPT-4.

这项技术的工作原理是这样的：研究人员在一款远程辅导应用中集成了 GPT-4 大语言模型。

1 The application included a tutor-student chat window，a problem display，and a whiteboard. The authors added a button that enabled the tutor to turn Tutor CoPilot on or off.

应用界面包含三个核心模块：实时师生对话窗口、题目展示区（problem display）和协作白板。研究团队特别设计了一个开关按钮，让教师可以随时启用或关闭 Tutor CoPilot（辅导协作者）功能。

2 When a tutor engaged Tutor CoPilot，the system prompted GPT-4 to behave as an experienced elementary math teacher and provided context in the form of the 10 most recent messages，the current lesson topic，and a default strategy from the list. GPT-4 responded with guidance.（To preserve the tutor's and student's privacy，the system redacted their names using the open source library Edu-ConvoKit.)

当辅导老师使用 Tutor CoPilot 时，系统会指示 GPT-4 模拟一位经验丰富的小学数学教师，并提供包括最近 10 条对话记录、当前课程主题和预设教学策略在内的上下文信息。GPT-4 将据此提供专业指导。（为保护师生隐私，系统通过开源工具 Edu-ConvoKit 对对话中的姓名进行了匿名处理。）

3 The system prompted GPT-4 three times，each time changing the strategy，and presented the tutor with three potential responses.

系统对 GPT-4 进行了三次提示，每次采用不同策略，最终给导师提供了三种备选回复方案。

4 The tutor could re-generate or edit GPT-4's responses，or select a strategy and generate a new response before adding it to the chat window.

导师可以选择重新生成或修改 GPT-4 的回复，也可以选定某个策略生成新回复后直接加入对话。

Results: The authors partnered with a virtual tutoring company and a school district in the United States for a two-month study of 874 tutors and 1,787 students between grades 3 and 8. They divided the participants into two groups. In one group，tutors conducted sessions with students as usual. In the other，tutors had access to Tutor CoPilot. The authors measured success by the percentage of students who passed a test at the end of a lesson.

研究结果：研究团队与一家在线教育平台及美国某学区合作，针对 874 名辅导教师和 1,787 名 3-8 年级学生开展了为期两个月的实验。参与者被随机分为两组：对照组教师采用传统教学方式，实验组教师则使用 Tutor CoPilot 智能辅导系统。研究以课程结束时的学生测试通过率作为核心评估指标。

1 In the group that didn't use Tutor CoPilot，62 percent of students passed the test.

在未使用 Tutor CoPilot 的组别中，62% 的学生通过了测试。

2 In the group with TutorCopilot，66 percent passed.

在使用 Tutor CoPilot 的组别中，66% 的学生通过了测试。

3 The effect was most pronounced among the one-third of tutors who had the lowest ratings（9 percent higher）and least experience（7 percent higher).

这种效果在评分最低（高出 9%）和经验最浅（高出 7%）的三分之一导师中最为显著。

4 The API cost was approximately $3.31 per tutor，or roughly $20 per tutor per year.

API 成本约为每位导师 3.31 美元，折合每人每年 20 美元左右。

Yes，but: The authors found statistically significant improvements as measured by test results per lesson，but not in end-of-year exam results. The study's two-month duration may account for the lack of evidence for longer-term effects.

研究确实发现：每节课后的测试成绩显示出统计学上的显著提升，但年终考试成绩却未见明显改善。这可能是因为该研究仅持续了两个月，时间跨度不足以观察到长期效果。

Why it matters: LLMs hold great promise for helping to educate students，but they also show potential in educating teachers. For inexperienced tutors who are learning how to interact with students，an LLM's general knowledge and pedagogical insights gleaned from expert teachers make a powerful combination.

重要意义：大语言模型（LLM）不仅有望革新学生的学习方式，更能为教师培训带来新机遇。特别是对教学经验尚浅的教师而言，大语言模型既具备广泛的知识储备，又融合了专家教师的教学智慧，这种双重优势将极大地提升教师培养效果。

We're thinking: Although it relies on sophisticated technology，the authors' approach is simple：Prompt an LLM to apply proven teaching principles. Presumably such principles apply beyond elementary math，which would make this approach useful for teaching a variety of disciplines.

我们的思考是：虽然这项技术基于复杂的算法，但作者的方法却出奇简单 —— 通过给大语言模型（LLM）输入提示词，让它运用那些久经验证的教学原则。这些原则很可能不仅适用于基础数学教学，还能推广到其他学科领域，使该方法具有广泛的应用价值。

#### Faster Learning for Diffusion Models

如何让扩散模型学得更快？

Diffusion transformers learn faster when they can look at embeddings generated by a pretrained model like DINOv2.

扩散 Transformer（Diffusion Transformer）如果能够参考预训练模型（如 DINOv2）生成的嵌入表示，其学习速度就会显著提升。

What's new: Sihyun Yu and colleagues at Korea Advanced Institute of Science and Technology，Korea University，New York University，and Scaled Foundations（a startup that builds AI for robotics）proposed Representation Alignment (REPA），a loss term for transformer-based diffusion.

研究动态：来自韩国科学技术院（KAIST）、高丽大学、纽约大学以及机器人 AI 初创公司 Scaled Foundations 的研究团队，在 Sihyun Yu 的带领下提出了一种名为表征对齐（REPA）的新方法。这项技术是为基于 Transformer 架构的扩散模型设计的新型损失函数。

Key insight: Diffusion models learn to remove noise from images to which noise was added（and，at inference，they start with pure noise to generate a fresh image). This process can be divided into two parts：learning to（i）embed the noisy image and（ii）estimate the noise from the embedding. One way to accelerate learning is to add a loss term that encourages the diffusion model to produce embeddings that are similar to those produced by a pretrained embedding model. The diffusion model can learn to estimate the noise faster if it doesn't need to learn how to embed an image from scratch.

核心原理：扩散模型（Diffusion models）通过训练学习如何去除人为添加到图像中的噪声（实际生成图像时，模型会从纯噪声开始逐步生成全新图像）。这一过程包含两个关键环节：（i）将带噪图像转化为特征表示（embedding），（ii）根据特征表示预测噪声分量。加速训练的诀窍在于：引入一个优化目标，使扩散模型生成的特征表示尽可能接近预训练模型输出的结果。由于无需从头学习图像特征提取，扩散模型就能更快掌握噪声预测的能力。

How it works: The authors modified DiT-XL/2 and SiT-XL/2 transformer-based latent diffusion models，a class of diffusion models that subtract noise from embeddings rather than images. They trained the models to produce images similar to ImageNet. In the process，the modified models learned to produce embeddings similar to those produced by a pretrained DINOv2.

实现原理：作者改进了基于 Transformer 的潜在扩散模型 DiT-XL/2 和 SiT-XL/2。这类模型的特点是通过处理嵌入向量（embeddings）而非直接处理图像来去除噪声。研究人员将这些模型训练成能生成类似 ImageNet 风格的图像。有趣的是，改进后的模型还能生成与预训练 DINOv2 模型输出的嵌入向量高度相似的向量。

1 The authors used Stable Diffusion VAE's pretrained encoder to embed an image.

作者使用了 Stable Diffusion 的变分自编码器（VAE，Variational Autoencoder）预训练编码器将图像编码为嵌入向量。

2 Given the embedding with noise added，the diffusion model learned to remove the noise according to the usual loss term.

在添加噪声的嵌入向量基础上，扩散模型（diffusion model）通过最小化损失函数来学习去除噪声的过程。

3 It also learned according to the REPA loss. Specifically，it learned to maximize the cosine similarity between a specially processed version of its eighth-layer embedding and the embedding produced by a pretrained DINOv2. To process its eighth-layer embedding for the REPA loss，the diffusion model fed the embedding to a vanilla neural network.

该模型还通过 REPA 损失函数（REgularized Patch Alignment loss）进行学习。具体而言，它会优化处理后的第八层特征嵌入，使其与预训练 DINOv2 模型生成的特征嵌入之间的余弦相似度达到最大。在计算 REPA 损失时，扩散模型会先将第八层特征嵌入输入一个标准神经网络进行处理。

4 At inference，given pure noise，the model removed it over several steps to produce an image embedding. Stable Diffusion VAE's decoder converted the embedding into an image.

在实际应用时，系统首先接收纯噪声（noise）输入，模型会通过多轮迭代逐步消除噪声，最终生成图像嵌入（embedding）。随后，Stable Diffusion 的 VAE 解码器会将这些嵌入数据转换成完整的图像。

Results: The modified DiT-XL/2 learned significantly faster than the unmodified version.

结果：改进后的 DiT-XL/2 模型学习速度明显优于原始版本。

1 In 400,000 training steps，the modified model reached 12.3 Fréchet inception distance (FID）(which measures similarity between generated and non-generated images，lower is better），while the unmodified version reached 19.5 FID.

经过 40 万训练步数后，改进版模型的 Fréchet 起始距离（Fréchet inception distance，FID）降至 12.3（该指标用于评估生成图像与真实图像的相似度，数值越低表示效果越好），而原始版本仅达到 19.5 FID。

2 The models continued to learn at different speeds as training continued. The modified DiT-XL/2  took 850,000 training steps to reach 9.6 FID，while the unmodified version took 7 million steps to reach the same number.

在训练过程中，不同模型的学习速度存在显著差异。改进版的 DiT-XL/2（Diffusion Transformer-XL/2）模型仅需 85 万次训练迭代就能达到 9.6 的 FID（Fréchet Inception Distance）分数，而原始版本则需要 700 万次训练迭代才能达到同等效果。

3 Experiments with modified and unmodified versions of SiT-XL/2 yielded similar results.

我们对 SiT-XL/2 模型的原版和修改版进行了对比实验，结果显示两者性能相近。

4 Trained to convergence，the modified models outperformed the unmodified versions. For instance，the modified  SiT-XL/2 achieved 5.9 FID（after 4 million training steps），while the unmodified version achieved 8.3 FID（after 7 million training steps).

当模型训练完全收敛时，改进版的性能明显更优。具体来说，改进版 SiT-XL/2 在训练 400 万步后取得了 5.9 的 FID 分数，而原版模型训练 700 万步后 FID 分数为 8.3。

Why it matters: Diffusion models and contrastive self-supervised models like DINOv2 have fundamentally different training objectives：One produces embeddings for the purpose of image generation，while the other's embeddings are used for tasks like classification and semantic segmentation. Consequently，they learn different aspects of data. This work proposes a novel way to combine these approaches to produce more generally useful embeddings.

研究意义：扩散模型（Diffusion models）与 DINOv2 这类对比自监督模型（contrastive self-supervised models）有着本质区别 —— 前者通过生成嵌入来实现图像生成（image generation），后者则专注于为分类（classification）和语义分割（semantic segmentation）等任务提取特征。这意味着它们捕捉的是数据的不同特征维度。本研究创新性地提出了一种融合方法，能够生成通用性更强的特征嵌入。

We're thinking: It turns out that the REPA modification enabled diffusion models to produce embeddings better suited not only to diffusion but also to image classification and segmentation. A similar approach could lead to a more holistic framework for learning image representations.

研究发现：REPA 改进后的扩散模型不仅能生成更优质的扩散特征（embedding），还能提升图像分类和分割任务的性能。这种创新思路有望推动建立更完善的图像表征学习体系。