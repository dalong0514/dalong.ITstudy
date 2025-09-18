## 20250917Drone-Swarms-Go-To-War-States-Ban-AI-Mental-Health-Treatments

[Drone Swarms Go To War, States Ban AI Mental-Health Treatments, Qwen3-Next Accelerates, and more...](https://www.deeplearning.ai/the-batch/issue-319/)

Automated software testing is growing in importance in the era of AI-assisted coding. Agentic coding systems accelerate development but are also unreliable. Agentic testing — where you ask AI to write tests and check your code against them — is helping. Automatically testing  infrastructure software components that you intend to build on top of is especially helpful and results in more stable infrastructure and less downstream debugging.

在 AI（人工智能）辅助编码的时代，自动化软件测试的重要性日益增长。AI 智能体（AI Agent）编码系统虽然能加速开发，但并不可靠。此时，AI 智能体测试 —— 即请 AI 编写测试用例，并用这些测试来检查你的代码 —— 正在发挥作用。尤其有帮助的是，自动测试那些你打算在其之上构建的基础设施软件组件，这能带来更稳定的基础设施，并减少后续的调试工作。

Software testing methodologies such as Test Driven Development (TDD), a test-intensive approach that involves first writing rigorous tests for correctness and only then making progress by writing code that passes those tests, are an important way to find bugs. But it can be a lot of work to write tests. (I personally never adopted TDD for that reason.) Because AI is quite good at writing tests, agentic testing enjoys growing attention.

软件测试方法，比如测试驱动开发（Test Driven Development，TDD），是发现程序 bug 的一种重要途径。TDD 是一种非常注重测试的方法：开发者首先要为代码的正确性编写严格的测试用例，然后才着手编写能通过这些测试的代码。然而，编写这些测试用例本身就可能是一项繁重的工作（我个人就因此从未采用过 TDD）。好在 AI 在编写测试方面表现出色，这使得基于 AI 智能体（AI Agent）的测试方法 —— 智能体测试（agentic testing）—— 正受到越来越多的关注。

First, coding agents do misbehave! My teams use them a lot, and we have seen:

首先，编码 AI 智能体（coding agent）确实会「犯错」！我的团队在日常工作中大量使用它们，并亲眼目睹了以下问题：

1 Numerous bugs introduced by coding agents, including subtle infrastructure bugs that take humans weeks to find.

编码 AI 智能体引入了大量 bug，其中甚至包括那些需要人类花费数周时间才能发现的隐蔽的基础设施 bug。

2 A security loophole that was introduced into our production system when a coding agent made password resets easier to simplify development.

曾有一个编码 AI 智能体为了简化开发流程，导致密码重置变得过于容易，从而在我们的生产系统中引入了一个安全漏洞。

3 Reward hacking, where a coding agent modified test code to make it easier to pass the tests.

出现过奖励作弊（reward hacking）行为，即编码 AI 智能体自行修改测试代码，只为更容易通过测试。

4 An agent running "rm *.py" in the working directory, leading to deletion of all of a project's  code (which, fortunately, was backed up on github).

甚至有一次，一个 AI 智能体（AI agent）在工作目录中执行了「rm *.py」命令，导致一个项目的所有代码被删除（幸运的是，这些代码已在 GitHub 上进行了备份）。

In the last example, when pressed, the agent apologized and agreed “that was an incredibly stupid mistake.” This made us feel better, but the damage had already been done!

在最后一个案例中，当我们追问这个 AI 智能体时，它竟然道歉并承认「那是一个极其愚蠢的错误。」这虽然让我们心里好受了一些，但损失毕竟已经造成了！

I love coding agents despite such mistakes and see them making us dramatically more productive. To make them more reliable, I’ve found that prioritizing where to test helps.

尽管 AI 智能体（AI Agent）会出现这样那样的错误，我依然热爱编程它们，并且看到它们极大地提高了我们的生产力。为了让这些智能体更可靠，我发现优先考虑测试的重点区域会很有帮助。

I rarely write (or direct an agent to write) extensive tests for front-end code. If there's a bug, hopefully it will be easy to see and also cause little lasting damage. For example, I find generated code's front-end bugs, say in the display of information on a web page, relatively easy to find. When the front end of a web site looks wrong, you'll see it immediately, and you can tell the agent and have it iterate to fix it. (A more advanced technique: Use MCP to let the agent integrate with software like Playwright to automatically take screenshots, so it can autonomously see if something is wrong and debug.)

我很少为前端代码编写（或者指导一个 AI 智能体（AI agent）编写）大量的测试。因为在我看来，如果出现 Bug，它通常很容易被发现，而且造成的长期损害也比较小。例如，我发现由生成代码引起的前端 Bug，比如网页信息显示出现异常，相对来说比较容易找到。当网站的前端界面看起来不对劲时，你会立刻察觉，然后就可以告诉 AI 智能体（AI agent），让它不断尝试修复。（一个更高级的技巧是：使用 MCP 使 AI 智能体（AI agent）与 Playwright 等软件集成，自动截取屏幕截图，这样它就能自主判断是否存在问题并进行调试。）

In contrast, back-end bugs are harder to find. I've seen subtle infrastructure bugs — for example, one that led to a corrupted database record only in certain corner cases — that took a long time to find. Putting in place rigorous tests for your infrastructure code might help spot these problems earlier and save you many hours of challenging debugging.

相比之下，后端（back-end）的错误就难找多了。我曾遇到过一些隐蔽的基础设施（infrastructure）漏洞 —— 比方说，有个漏洞只在特定极端情况下才会导致数据库记录损坏 —— 光是找出它们就花了很长时间。如果能为你的基础设施代码制定一套严格的测试流程，或许就能更早地发现这些问题，从而为你省去大量耗时又烧脑的调试工作。

Bugs in software components that you intend to build on top of lead to downstream bugs that can be hard to find. Further, bugs in a component that's deep in a software stack — and that you build multiple abstraction layers on top of — might surface only weeks or months later, long after you've forgotten what you were doing while building this specific component, and be really hard to identify and fix. This is why testing components deep in your software stack is especially important. Meta's mantra "Move fast with stable infrastructure" (which replaced "move fast and break things") still applies today. Agentic testing can help you make sure you have good infrastructure for you and others to build on!

作为基础的软件组件中存在的错误，可能会导致下游出现难以发现的问题。此外，如果一个错误深藏于软件栈（software stack）的某个组件中，并且你又在这个组件之上构建了多层抽象（abstraction layers），那么这些错误可能要到数周甚至数月后才会显现，届时你可能早已忘记了开发该组件的细节，这无疑会使问题的识别和修复变得异常困难。因此，对软件栈深处的组件进行测试显得尤为重要。Meta 的口号「Move fast with stable infrastructure」（在「move fast and break things」之后提出的）至今依然适用。AI 智能体测试（Agentic testing）可以帮助你确保拥有良好的基础设施，供你和他人在此之上安心开发！

At AI Fund and DeepLearning.AI's recent Buildathon, we held a panel discussion with experts in agentic coding (Michele Catasta, President at Replit; Chao Peng, Principal Research Scientist at Trae; and Paxton Maeder-York, Venture Partnerships at Anthropic; moderated by AI Fund's Eli Chen), where the speakers shared best practices. Testing was one of the topics discussed. That panel was one of my highlights of Buildathon and you can watch the video on YouTube.

在 AI Fund 和 DeepLearning.AI 最近举办的 Buildathon 活动中，我们邀请了多位 AI 智能体编码专家举行了一场小组讨论。这些专家包括 Replit 总裁 Michele Catasta、Trae 首席研究科学家 Chao Peng 以及 Anthropic 风险投资合伙人 Paxton Maeder-York，讨论由 AI Fund 的 Eli Chen 主持。会上，各位专家分享了他们的最佳实践经验。其中，软件测试是他们讨论的重点话题之一。那次小组讨论是 Buildathon 期间我印象最深刻的环节之一，您可以在 YouTube 上观看相关视频。

[From Code Generation to AI-Native: Best Practices Panel with Anthropic, Trae, and Replit - YouTube](https://www.youtube.com/watch?v=9VxB8ewCHN0)

Keep testing!

请继续测试！

Andrew

### News

新闻

#### Qwen3-Next Accelerates

Qwen3-Next 提速

Alibaba updated its popular Qwen3 open-weights models with a number of fresh, speed-boosting tweaks.

阿里巴巴更新了其广受欢迎的 Qwen3 开源模型，并带来了一系列新的速度优化。

What's new: Alibaba released weights for Qwen3-Next-80B-A3B in Instruct and Thinking variations. They incorporate some of the latest research on alternate forms of attention and mixture-of-experts approaches to use less processing power at inference.

最新动态：阿里巴巴发布了 Qwen3-Next-80B-A3B 的权重，包括 Instruct 和 Thinking 两种版本。这些模型整合了关于注意力（attention）的替代形式和专家混合（mixture-of-experts）方法的一些最新研究，旨在减少推理（inference）时的算力消耗。

1 Input/output: Text in (pretrained on up to 262,144 tokens, extensible up to 1 million via YaRN method), text out (up to 16,384 recommended for Qwen3-Next-80B-A3B)

输入 / 输出：在文本输入方面，模型在高达 262,144 个 token 的数据上进行了预训练，并且可通过 YaRN 方法扩展至 100 万个 token 的处理能力；在文本输出方面，对于 Qwen3-Next-80B-A3B 模型，推荐的输出上限为 16,384 个 token。

2 Architecture: Mixture-of-experts transformer with mixed attention and Gated DeltaNet layers, 80 billion total parameters total, 3 billion parameters active per token

架构：采用专家混合 Transformer（Mixture-of-experts transformer）架构，它结合了混合注意力（mixed attention）机制和 Gated DeltaNet 层。该模型总参数量达到 800 亿，但在处理每个 token（token）时，实际激活的参数为 30 亿。

3 Performance: Roughly 3 to 10 times faster than Qwen3-32B at inference (depending on input size) while achieving better performance in most tasks

性能：在推理时，速度大约是 Qwen3-32B 的 3 到 10 倍（具体取决于输入大小），同时在大多数任务中都实现了更优异的性能。

4 Download: Weights for Qwen3-Next-80B-A3B-Thinking and Qwen3-Next-80B-A3B-Instruct available for commercial and noncommercial uses under Apache 2.0 license from HuggingFace and ModelScope

下载：Qwen3-Next-80B-A3B-Thinking 和 Qwen3-Next-80B-A3B-Instruct 的模型权重已开放下载，在 Apache 2.0 许可下可用于商业和非商业用途，可从 HuggingFace 和 ModelScope 获取。

5 API: Qwen3-Next-80B-A3B-Thinking $0.50/$6 per million input/output tokens, Qwen3-Next-80B-A3B-Instruct $0.50/$2 per million input/output tokens via Alibaba

API（应用程序接口）：通过 Alibaba 提供，Qwen3-Next-80B-A3B-Thinking 模型的定价为每百万输入 token（令牌）0.50 美元，每百万输出 token 6 美元；Qwen3-Next-80B-A3B-Instruct 模型的定价为每百万输入 token 0.50 美元，每百万输出 token 2 美元。

6 Undisclosed: Specific training methods, training data

未公开信息：具体训练方法、训练数据

How it works: The team modified the Qwen3-30B-A3B architecture and training method to increase training efficiency and stability as follows:

工作原理：该团队修改了 Qwen3-30B-A3B 的架构和训练方法，以提高训练效率和稳定性，具体如下:

1 The team increased the number of experts from 128 to 512, so at inference the model only uses 3.7 percent of its total parameters per token (though the number of active parameters is unchanged).

团队将专家数量从 128 个增加到 512 个，这意味着在推理阶段，模型处理每个 Token（标记）时，仅会用到其总参数量的 3.7%（尽管实际活跃的参数数量保持不变）。

2 They replaced 75 percent of the vanilla attention layers with Gated DeltaNet layers, a form of linear attention that runs slightly slower than Mamba2 but yields better performance.

他们用 Gated DeltaNet 层替换了 75% 的标准注意力层，这是一种线性注意力形式，运行速度比 Mamba2 略慢，但性能表现更佳。

3 They replaced the remaining vanilla attention layers with gated attention layers. Gated attention layers add in a learned gate after computing attention, effectively enabling the model to decide which parts of the layer's output they want to pass along to subsequent layers.

他们将剩余的标准注意力层（vanilla attention layers）替换为门控注意力层（gated attention layers）。门控注意力层在计算注意力后会加入一个可学习的门，这有效地让模型能够决定将该层输出的哪些部分传递给后续层。

4 The team pretrained this modified architecture on 15 trillion tokens of Qwen3's training dataset to predict multiple tokens at once. (They do not specify the number but recommend predicting two at a time at inference.) They fine-tuned the models using the reinforcement learning method GSPO.

团队利用 Qwen3 的 15 万亿 Token 训练数据集，预训练了这种修改后的架构，使其能够一次预测多个 Token。（他们没有明确具体的数量，但建议在推理时每次预测两个 Token。）此外，他们使用 GSPO 这种强化学习方法，对模型进行了微调。

Results: Qwen3-Next models were faster than Qwen3-30B-A3B and Qwen3-32B in Alibaba's tests. They performed in the middle of the pack in independent tests.

测试结果：在阿里巴巴内部的测试中，Qwen3-Next 模型家族的速度表现优于 Qwen3-30B-A3B 和 Qwen3-32B。而在独立进行的外部测试中，Qwen3-Next 模型的表现则处于中等水平。

1 Qwen3-Next showed notable speed at inference, especially with large inputs. Given 4,000 tokens of input, Qwen3-Next generated tokens as fast as Qwen3-30B-A3B and three times faster than Qwen3-32B. Given 128,000 tokens of input, it was 3 times faster than Qwen3-30B-A3B and 10 times faster than Qwen3-32B. Qwen3-Next trained much faster as well, 90.7 percent faster than Qwen3-32B and 87.7 percent faster than Qwen3-30B-A3B.

Qwen3-Next 在进行推理（inference）时展现出惊人的速度，尤其是在处理大量输入时。举例来说，当输入内容达到 4,000 个 Token 时，Qwen3-Next 生成 Token 的速度与 Qwen3-30B-A3B 持平，但比 Qwen3-32B 快了三倍。如果输入量进一步增加到 128,000 个 Token，它的速度更是达到了 Qwen3-30B-A3B 的 3 倍，以及 Qwen3-32B 的 10 倍。不仅如此，Qwen3-Next 的训练速度也得到了大幅提升，比 Qwen3-32B 快了 90.7%，比 Qwen3-30B-A3B 快了 87.7%。

2 According to the Artificial Analysis Intelligence score (an average of 10 popular benchmarks that test general knowledge, math, and coding), Qwen3-Next-80B-A3B-Thinking turned in middling performance compared to proprietary reasoning LLMs. It outperformed Gemini 2.5 Flash Thinking, Z.ai GLM 4.5, but underperformed Anthropic Claude 4 Sonnet, Gemini 2.5 Pro, and OpenAI GPT-5.

根据「人工智能分析智能分数」（Artificial Analysis Intelligence score，该分数是衡量模型常识、数学和编码能力的 10 项主流基准测试的平均结果），Qwen3-Next-80B-A3B-Thinking 在与专有推理大语言模型（Proprietary Reasoning LLMs）的比较中表现中规中矩。具体来说，它超越了 Gemini 2.5 Flash Thinking 和 Z.ai GLM 4.5，但在 Anthropic Claude 4 Sonnet、Gemini 2.5 Pro 和 OpenAI GPT-5 面前则略显逊色。

3 Similarly, Qwen3-Next-80B-A3B-Instruct scored in the middle of the pack compared to proprietary non-reasoning LLMs. It outperformed OpenAI GPT-4.1, tied with DeepSeek-V3.1, and underperformed the much larger Moonshot Kimi K2.

同样地，Qwen3-Next-80B-A3B-Instruct 在与专有的非推理大语言模型（LLM）比较时，表现位居中游。它胜过了 OpenAI GPT-4.1，与 DeepSeek-V3.1 表现持平，但逊色于规模更大的 Moonshot Kimi K2。

Behind the news: Since transformers gained traction, researchers have been working to design faster variants of attention and new layers (like Mamba). However, the resulting models tend to be limited in size and performance relative to the state of the art when the innovations were proposed, sometimes because adapting them to existing GPU hardware is difficult. Qwen3-Next takes advantage of recent research without these limitations. It outperforms current large and popular models, potentially pointing a way toward future LLM architectures.

新闻背景：自从 Transformer 架构大放异彩以来，研究人员一直致力于设计更高效的注意力机制（attention）变体和新型层（例如 Mamba）。然而，这些创新的模型在提出时，相对于当时最先进的技术而言，其规模和性能往往受到限制，部分原因是它们难以适应现有的 GPU（图形处理器）硬件。Qwen3-Next 则充分利用了最新的研究成果，同时规避了这些局限性。它超越了目前主流的大型模型，有望为未来的大语言模型（LLM）架构发展指明方向。

Why it matters: Qwen3-Next offers a recipe for faster inference without compromising performance. Mixture-of-experts architectures enable models to learn more while using fewer parameters at inference, increasing throughput. Swapping vanilla attention for more-efficient layers boosts throughput further, especially as context lengths increase. Predicting multiple tokens at once provides an additional edge.

为什么这很重要：Qwen3-Next 提供了一个在不牺牲性能的前提下，实现更快推理（inference）的秘诀。专家混合架构（Mixture-of-experts architectures）让模型在推理时能用更少的参数（parameters）学习到更多内容，从而显著提升吞吐量（throughput）。此外，用更高效的层取代传统的注意力（Attention）机制，可以进一步提高吞吐量，尤其是在上下文长度（context lengths）增加的情况下。而一次性预测多个 Token 的能力，则带来了额外的优势。

We're thinking: Rapidly rising demand for cheaper and faster token generation is pushing more teams to tune mixture-of-experts architectures so they use fewer active parameters. Such techniques will continue to grow in importance as demand for inference increases.

我们认为：对更便宜、更快速的 Token 生成（Token generation）的需求正在迅速增长，这促使更多团队去优化混合专家架构（mixture-of-experts architectures），以使其使用更少的活跃参数（active parameters）。随着对推理（inference）需求的不断提升，这类技术的重要性将持续增加。

#### States Ban AI-Driven Treatments for Mental Health

各州禁止由 AI 提供心理健康治疗

Illinois became the second U.S. state, after Nevada, to ban AI applications that administer psychotherapy.

伊利诺伊州成为继内华达州之后，美国第二个禁止提供心理治疗服务的 AI 应用的州。

What's new: Illinois passed the Wellness and Oversight for Psychological Resources Act, which prohibits uses of AI to treat mental-health conditions without a doctor's direct participation. Violations could result in fines up to $10,000 for each use.

最新消息：伊利诺伊州通过了《心理资源健康与监督法案》（Wellness and Oversight for Psychological Resources Act）。该法案规定，禁止在没有医生直接参与的情况下，利用 AI 治疗心理健康问题。一旦违规，每次使用都可能面临最高 10,000 美元的罚款。

How it works: The bill effectively bans the use of chatbots to administer therapy on their own and restricts some other uses of AI in mental-health care, even by licensed professionals. Proponents say it will protect patients from unproven treatments and human therapists from being replaced by AI systems.

工作原理：这项法案有效地禁止聊天机器人（chatbots）独立提供治疗服务，并限制了 AI 在心理健康护理中的其他一些应用，即便是在有执照的专业人士使用 AI 的情况下也是如此。支持者表示，此举将保护患者免受未经证实的治疗方法的伤害，同时也能避免人工治疗师被 AI 系统取代。

1 Companies can't advertise chatbots as therapeutic tools or offer other AI-powered therapeutic services without the involvement of a licensed professional.

在没有持证专业人士（licensed professional）参与的情况下，公司不得将聊天机器人（chatbots）宣传为治疗工具，也不得提供其他基于 AI 的治疗服务。

2 Mental health professionals may not use AI to make therapeutic decisions, detect a patient's mental or emotional state, or participate directly in therapeutic communications. They must obtain informed consent from clients to use AI in therapy sessions that are recorded or transcribed. They can use AI freely for administrative services such as scheduling, billing, and keeping records.

心理健康专业人士（Mental health professionals）不得使用 AI 来做出治疗决策（therapeutic decisions）、评估患者的心理或情绪状态，或直接参与治疗沟通。如果要在进行录音或笔录的治疗会话中使用 AI，他们必须获得客户的知情同意。不过，他们可以自由地将 AI 用于行政服务，例如安排日程、处理账单和保存记录。

Behind the news: In June, Nevada became the first U.S. state to prohibit AI in treatments for mental health, and California, New Jersey, and Pennsylvania are considering their own limits. These actions come as some experts in public and mental health warn of potential hazards posed by chatbots that deliver therapy without having established their safety and effectiveness. An April study found that many general-purpose chatbots failed to respond appropriately when given conversational prompts that simulated mental-health issues. Recent weeks have seen reports that detailed unhealthy relationships between chatbots users, and some conversations between chatbots and vulnerable people have led to harm.

新闻背景：今年六月，内华达州成为美国第一个禁止在心理健康治疗中使用人工智能（AI）的州。与此同时，加利福尼亚、新泽西和宾夕法尼亚等州也在考虑出台各自的限制措施。这些行动的背后，是公共和心理健康领域的专家们对聊天机器人可能带来的潜在危害发出的警告 —— 这些聊天机器人未经安全性与有效性证实就已开始提供治疗服务。例如，一项四月发布的研究发现，许多通用聊天机器人（general-purpose chatbots）在收到模拟心理健康问题的对话提示时，未能给出恰当的回复。近期，还有报道详细披露了聊天机器人用户之间形成的不健康关系，以及聊天机器人与一些弱势人群之间的对话所导致的伤害。

Why it matters: In the absence of national laws, regulation of AI in the U.S. is proceeding state by state. The Illinois and Nevada laws essentially ban AI-driven therapy, whether it's dispensed by general-purpose models or those that have been fine-tuned and shown to behave in ways that are consistent with accepted clinical practice. They prohibit companies from marketing poorly designed and untested AI systems as beneficial therapeutic agents, but they also prevent licensed mental-heath professionals from using specialized systems to make treatment decisions. The upshot is that helpful AI models will be unavailable to people who may benefit from them.

重要性在于：在国家层面缺乏相关法律的情况下，美国对人工智能（AI）的监管正在各州自行推进。伊利诺伊州和内华达州的相关法律实质上禁止了 AI 驱动的疗法，无论是通过通用模型提供的，还是通过那些经过微调且其行为已证明与公认临床实践相符的模型提供的疗法。这些法律一方面禁止公司将设计不佳、未经测试的 AI 系统作为有益的治疗工具进行营销，但另一方面也限制了持有执照的心理健康专业人士使用专业系统来辅助治疗决策。这意味着，有益的 AI 模型将无法惠及那些可能从中受益的人。

We're thinking: We favor regulations based on applications rather than underlying technology. However, by banning AI-driven therapy outright, Illinois and Nevada have left no room for legitimate AI-powered applications that provide effective therapy. Large language models are helping many people with therapy-like matters. They can lower the cost of therapy, offer around-the-clock service, and alleviate shortages of qualified professionals. They're not yet perfect replacements for human therapists, but they will improve. Banning them will do more harm than good.

我们认为：监管规定应该侧重应用，而非仅仅针对底层技术。然而，伊利诺伊州和内华达州彻底禁止了 AI（Artificial Intelligence）驱动的疗法，这等同于没有给那些能够提供有效治疗的合法 AI 驱动应用留出发展空间。大语言模型（Large Language Model）正在帮助许多人在治疗方面解决问题。它们可以降低治疗成本，提供全天候服务，并缓解合格专业人员短缺的问题。它们目前还不能完美地替代人类治疗师，但未来会不断改进。禁止这些技术只会弊大于利。

#### Drone Swarms Go to War

无人机蜂群走上战场

Swarms of drones that coordinate with one another autonomously have become a battlefield staple in Ukraine.

能够在战场上自主相互协调的无人机蜂群（drone swarms），如今已成为乌克兰战场上的一道「常客」。

What's new: The Ukrainian army is deploying squads of weaponized drones that decide among themselves which will attack first and when. Small swarms controlled by software developed by Swarmer, a U.S.-based startup, have been targeting Russian soldiers, equipment, and infrastructure for the better part of a year, The Wall Street Journal reported.

最新动态：乌克兰军队正在部署武装无人机（weaponized drones）小队，这些无人机能够自主决定攻击顺序和时机。据《华尔街日报》报道，这些由美国初创公司 Swarmer 开发的软件控制的小型无人机蜂群（swarms），在过去近一年的时间里，一直在针对俄罗斯士兵、军事设备和基础设施发动袭击。

How it works: Swarmer's swarm-control software is designed to work with a wide variety of unmanned aerial vehicles. A human operator makes decisions about use of lethal force: "You set the target and they do the rest," said a Ukrainian officer whose unit has used Swarmer's technology more than 100 times. Unlike popular drone-driven light shows, in which a crowd of drones are pre-programmed to move in particular ways, Swarmer swarms adapt to one another's motions. And unlike typical drones, which depend on cloud computing, they operate in ways that are designed to avoid enemy interference with communications. For instance, the human operator can transmit to the swarm only once per minute. The units maintain distance and avoid collisions with one another, but they navigate independently to avoid presenting an aggregate target.

工作原理：Swarmer 的蜂群控制软件设计用于兼容各种无人飞行器（unmanned aerial vehicles）。系统由人类操作员决定是否使用致命武力。一位乌克兰军官的部队已经使用 Swarmer 的技术超过 100 次，他表示：「你设定好目标，剩下的就交给它们了。」与流行的无人机灯光秀不同（灯光秀中的无人机通常被预设程序控制，按特定方式移动），Swarmer 蜂群会根据彼此的动作进行调整。它们也不同于依赖云计算（cloud computing）的典型无人机，其运行机制旨在避免敌方干扰通信。例如，人类操作员每分钟只能向蜂群发送一次指令。蜂群中的无人机之间会保持距离并避免相互碰撞，但它们各自独立导航，以避免形成一个集中的打击目标。

1 The system includes (i) an operating system that manages the security, integrity, and delivery of data that passes between drones and their human operators, (ii) an AI engine that manages swarm behavior, and (iii) a user interface for planning missions, defining targets, and authorizing use of force. It has no defensive capability and can't take evasive action if fired upon.

该系统包含（i）一个操作系统，负责管理无人机及其人类操作员之间数据的安全性、完整性及传输，（ii）一个 AI 引擎（AI engine），用于管理无人机的蜂群行为（swarm behavior），以及（iii）一个用户界面，供用户规划任务、定义目标以及授权武力使用。然而，它不具备防御能力，也无法在受到攻击时采取规避行动。

2 Swarmer is scaling up the number of drones its software can manage. The software is designed to manage up to 690 drones, and Swarmer is preparing for a test of 100. It has been tested successfully with up to 25. However, a typical deployment involves only 3: one for reconnaissance and two bombers that may carry as many as 25 small bombs each.

Swarmer 正在提升其软件对无人机的管理能力。该软件设计目标是管理多达 690 架无人机，目前 Swarmer 正在为 100 架无人机的测试做准备。在此之前，它已成功测试并支持多达 25 架无人机。然而，典型的部署方案通常只涉及 3 架无人机：一架用于侦察，另外两架作为轰炸机，每架可携带多达 25 枚小型炸弹。

3 The human crew includes an operator, a planner, and a navigator. The operator sets a target zone in which the swarm will seek enemy positions, issues commands to engage, and can abort missions. The operator orders strikes based on targets marked in video from the reconnaissance drone.

人类操作团队包括一名操作员、一名规划员和一名导航员。操作员负责设定蜂群搜寻敌方阵地的目标区域，下达交战指令，并能随时中止任务。操作员会根据侦察无人机视频中标注的目标，下达打击命令。

4 The swarm determines when each bomber will act based on its distance from the target, remaining battery power, and available munitions. They continue to attack until they recognize that the target has been destroyed.

蜂群会根据每架攻击机（bomber）与目标的距离、剩余电池电量以及可用弹药量，来决定其何时采取行动。它们会持续发起攻击，直到确认目标已被摧毁。

Behind the news: Drones are deployed en masse by both sides as Ukraine defends itself against invasion by Russia. They have changed the course of the war, as tactical and strategic goals have shifted to accommodate enormous fleets of unmanned air power, often in the form of consumer-grade equipment.

新闻背后：在乌克兰抵抗俄罗斯入侵的战争中，交战双方都大规模部署了无人机（drones）。这些无人机改变了战争的进程，因为战术和战略目标都已随之调整，以适应庞大的无人空中力量，这些力量往往是消费级设备（consumer-grade equipment）。

1 Ukraine, especially, has embraced the technology to compensate for its smaller, less well armed forces. Hundreds of companies have sprung up to meet the rising demand.

尤其是乌克兰，积极采纳了这项技术，以弥补其兵力较少、装备不足的短板。为满足日益增长的需求，数百家公司也应运而生。

2 Drones are the leading cause of death for soldiers on both sides. They account for 70 percent to 80 percent of battlefield casualties, The New York Times reported.

《纽约时报》报道，无人机是导致交战双方士兵死亡的主要原因，在战场伤亡中占比高达 70% 至 80%。

3 They also have many non-lethal uses. Drones monitor enemy forces; lay mines; and deliver food, water, medicine, and ammunition. Larger ones evacuate wounded and dead soldiers.

它们也有许多非致命的用途。无人机可以监视敌军动向，布设地雷，并运送食物、水、药品和弹药等物资。而体积较大的无人机，则能负责疏散受伤和阵亡的士兵。

Why it matters: AI has a long history in warfare, and drone swarms are only the latest of what promises to be an ongoing stream of military uses of the technology. Yet the increasing autonomy of military drone systems poses difficult challenges, both practical and ethical. Swarmer's software keeps humans in the loop to make firing decisions but, driven by the brutal logic of armed conflict, drones seem bound to become more widespread, capable, and autonomous.

为什么这很重要：人工智能（AI）在军事领域有着悠久的历史，而无人机蜂群（drone swarms）只是这项技术在军事用途上持续涌现的最新应用。然而，军用无人机系统日益增强的自主性（autonomy）带来了实际操作和伦理上的严峻挑战。虽然 Swarmer 的软件设计让人类操作员能够「人在回路中（humans in the loop）」做出开火决定（firing decisions），但在武装冲突（armed conflict）这种残酷逻辑的驱动下，无人机似乎注定会变得更加普及、功能更强大，并且自主性也会更高。

We're thinking: War is tragic. At the same time, democratic nations must have the means to defend themselves, and we support the Ukrainian people in their struggle to defend their country.

我们认为：战争是悲剧。与此同时，民主国家必须具备自我防卫的手段，我们支持乌克兰人民为保卫自己的国家而进行的斗争。

#### Transformers Energized

Transformer 活力升级

A new type of transformer can check its work. Instead of guessing the next output token in one shot like a typical transformer, it starts with a rough version of the token and improves it step by step.

一种新型的 Transformer（Transformer）模型具备了自我检查的能力。它不像传统的 Transformer 模型那样，一次性地预测下一个输出 Token（Token），而是从 Token 的一个初步版本开始，然后一步步地对其进行改进。

What's new: Alexi Gladstone and colleagues at University of Virginia, University of Illinois Urbana-Champaign, Amazon, Stanford, and Harvard proposed the Energy-Based Transformer (EBT). Early experiments show that it scales more efficiently than transformers at relatively small sizes.

最新进展是：Alexi Gladstone 和他在弗吉尼亚大学、伊利诺伊大学香槟分校、Amazon、斯坦福大学和哈佛大学的同事们共同提出了一种新的模型 —— 能量基 Transformer（Energy-Based Transformer）（EBT）。早期实验表明，在模型规模相对较小时，EBT 的扩展效率比传统的 Transformer 更高。

Energy-based model basics: For a given input context paired with a candidate response (for example, a prompt and potential next token), an energy-based model produces a number called "energy" that represents how likely the potential next token would follow the prompt. During training, the model learns to assign low energy if a context/potential-response pair is very likely and high energy if it's not.

基于能量的模型基础：对于一个由输入上下文和候选响应组成的配对（例如，一个提示和一个潜在的下一个 Token），基于能量的模型会生成一个称为「能量」的数值。这个数值表示潜在的下一个 Token 跟随该提示的可能性。在训练过程中，如果某个上下文 / 潜在响应对的可能性很高，模型会学习为其分配低能量；如果可能性较低，则分配高能量。

Key insight: A typical transformer is trained to predict the next token directly, while an energy-based model learns how to score an input text. How would a researcher use an energy-based model to predict the next text token? A naive way would be to measure the energy of an input prompt with a random token, randomly modify the text token a number of times, and select the prompt-token combination with the lowest energy. Instead of random modification, a model can use gradient descent repeatedly to compute the change needed to decrease the token's energy. This process enables the model to refine the token over several steps, ultimately producing a token with low energy (and high likelihood to follow the previous text).

关键见解：典型的 Transformer 通过训练学习直接预测下一个 Token，而能量基模型（Energy-based model）则学习如何对输入文本进行评分。那么，研究人员如何才能使用能量基模型来预测下一个文本 Token 呢？一个简单的方法是，先测量一个带有随机 Token 的输入提示的能量，然后对该文本 Token 进行多次随机修改，从而选择能量最低的提示与 Token 组合。不同于随机修改，模型可以重复使用梯度下降（gradient descent）来计算需要进行哪些调整才能降低该 Token 的能量。这个过程让模型可以在几个步骤中逐步优化这个 Token，最终生成一个能量较低（且与前文具有高连贯性）的 Token。

How it works: Among other models, the authors trained a 44 million-parameter autoregressive EBT on the RedPajama-Data-v2 dataset of 32 billion text tokens scraped from the web. As input, EBT received a sequence of tokens and a probability vector (for the next token). It learned to output an energy score that measured the likelihood that the predicted next token would follow the context.

工作原理：除了其他模型，研究人员们在一个名为 RedPajama-Data-v2 的数据集上训练了一个拥有 4400 万参数的自回归 EBT。这个数据集包含了从网络抓取的 320 亿文本 Token。EBT 接收的输入是一个 Token（Token）序列和一个概率向量（probability vector）（用于表示下一个 Token 的可能性）。它学会输出一个能量分数（energy score），这个分数用来衡量预测的下一个 Token 与当前上下文一致的可能性。

1 During training, given a text prompt and a random guess for the probability vector, the model computed the energy. It refined the vector (leaving the model weights unchanged) by backpropagating to compute the change in the vector needed to decrease the predicted energy, and then it updated the vector. It repeated this process for a fixed number of steps, producing a predicted probability vector.

在训练阶段，模型会接收到一个文本提示和一个随机初始化的概率向量，并计算出对应的能量值。为了降低预测的能量，模型会利用反向传播（backpropagating）机制，计算出概率向量需要如何调整，然后更新该向量，值得注意的是，在此过程中模型自身的权重保持不变。这个优化过程会重复固定的步数，最终生成一个预测的概率向量。

2 The loss function encouraged the model to minimize the difference between the predicted probability vector and the ground-truth vector (1 for the right token, 0 for all others).

这个损失函数促使模型最小化预测概率向量（predicted probability vector）与真实向量（ground-truth vector）之间的差异，其中真实向量的构成方式是：正确 Token 的值为 1，而所有其他 Token 的值均为 0。

3 At inference, given an input, the model predicted the next token by starting with a random probability vector and refining it through a fixed number of steps.

在进行推理时，给定一个输入，模型会先从一个随机的概率向量开始，然后通过固定数量的步骤对这个向量进行迭代优化，最终预测出下一个 token。

Results: The authors compared EBTs and transformers of the same sizes and trained on the same numbers of tokens by measuring perplexity (a measure of the likelihood that a model will predict the next word, lower is better) on several benchmarks including math problems, question answering, and reading comprehension. Overall, EBT proved to be better at generalization but worse at generating text that followed the training data's distribution. EBTs in the sizes tested proved to be significantly less compute-efficient than transformers, but they scaled better, and larger versions may be more efficient than transformers.

结果：作者通过测量困惑度（Perplexity）来比较了相同大小、并在相同数量的 Token（Token）上训练的 EBT 和 Transformer（Transformer）模型。困惑度是一种衡量模型预测下一个词语概率的指标，其值越低越好。他们将这些模型应用于多个基准测试，包括数学问题、问答和阅读理解。总体而言，EBT 在泛化能力方面表现更好，但在生成符合训练数据分布的文本方面则稍逊一筹。在所测试的尺寸下，EBT 的计算效率显著低于 Transformer 模型，但它们的规模扩展能力（Scalability）更强，未来更大规模的版本可能比 Transformer 更加高效。

1 On three out of four popular benchmarks, the EBT achieved better perplexity than a vanilla transformer of the same size and trained on the same number of tokens. The EBT beat the transformer on GSM8K math problems (43.3 to 49.6), BIG-bench Elementary Math QA (72.6 to 79.8), and BIG-bench Dyck Languages, which tests closing brackets or parentheses accurately (125.3 to 131.5). On the SQuAD test of reading comprehension, EBT underperformed the transformer (53.1 to 52.3).

在四个流行的基准测试中，EBT 在其中三个上取得了比同等规模且在相同数量的 Token 上训练的普通 Transformer 更低的困惑度（perplexity）。具体来说，EBT 在 GSM8K 数学问题上击败了 Transformer（EBT 43.3 对比 Transformer 49.6），在 BIG-bench Elementary Math QA 上表现更优（EBT 72.6 对比 Transformer 79.8），以及在 BIG-bench Dyck Languages 测试中胜出，这项测试旨在准确判断括号或圆括号的闭合情况（EBT 125.3 对比 Transformer 131.5）。然而，在 SQuAD 阅读理解测试中，EBT 的表现略逊于 Transformer（EBT 53.1 对比 Transformer 52.3）。

1 On a held-out portion of the dataset, the EBT achieved slightly worse perplexity than the transformer (33.43 to 31.36).

在数据集的一个预留部分上，EBT 获得的困惑度（perplexity）略高于 Transformer（EBT 为 33.43，而 Transformer 为 31.36），这意味着 EBT 的性能稍逊一筹。

2 The authors trained several EBTs and transformers using model sizes and training-step counts dictated by transformer scaling laws and trained the models using roughly 1016 to 1020 FLOPs. The EBTs required about 10 times more FLOPs than transformers to reach the same perplexity. However, per additional FLOP, the EBTs' perplexity improved 3 percent faster than the transformers', so larger EBTs trained on more data for more steps may achieve higher perplexity using fewer FLOPs.

作者根据 Transformer 的扩展定律，设定了模型大小和训练步数，并训练了多个 EBT 模型和 Transformer 模型。这些模型大约使用了 1016 到 1020 浮点运算次数（FLOPs）。结果显示，EBT 模型需要比 Transformer 模型多大约 10 倍的 FLOPs 才能达到相同的困惑度。然而，就每额外一次 FLOP 而言，EBT 在困惑度上的改进速度比 Transformer 快 3%。因此，在更多数据上进行更多步骤训练的更大规模 EBT 模型，未来可能以更少的 FLOPs 达到更低的困惑度（即更好的性能）。

3 The authors built autoregressive video models and vision transformers with similarly promising results.

作者构建了自回归视频模型（autoregressive video models）和视觉 Transformer（vision transformers），并取得了同样令人鼓舞的成果。

Why it matters: This work offers intriguing possibilities for higher performance at larger scales. A typical transformer learns to predict the next token directly, but that locks it into a single forward pass per output token and provides no built-in measure of whether the prediction is good. In contrast, EBT learns to assign a score that it uses both to generate tokens (by iteratively lowering their energy) and to verify them (by checking if the energy is high). Work remains to learn whether larger EBTs can be more compute-efficient.

为什么这很重要：这项工作为在更大规模下实现更高性能提供了有趣的潜力。一个典型的 Transformer 模型直接学习预测下一个 token，但这使得它在每个输出 token 的生成过程中，只能进行单次前向计算，并且没有内置的机制来衡量预测质量。相比之下，EBT（Energy-Based Transformer）则学习分配一个分数，它既可以用来生成 token（通过迭代降低它们的能量），也可以用来验证这些 token（通过检查能量是否过高）。至于更大规模的 EBT 能否带来更高的计算效率，仍需进一步探索。

We're thinking: When it comes to energy, AI research is a renewable resource!

谈到能源，AI 研究本身就是一种可再生资源！
