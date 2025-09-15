## 20250410The-Second-Half

[The Second Half – Shunyu Yao – 姚顺雨](https://ysymyth.github.io/The-Second-Half/)

tldr: We're at AI's halftime.

一句话总结：我们正站在人工智能（AI）发展的「中场休息」时刻。

For decades, AI has largely been about developing new training methods and models. And it worked: from beating world champions at chess and Go, surpassing most humans on the SAT and bar exams, to earning IMO and IOI gold medals. Behind these milestones in the history book — DeepBlue, AlphaGo, GPT-4, and the o-series — are fundamental innovations in AI methods: search, deep RL, scaling, and reasoning. Things just get better over time.

几十年来，AI 的发展重心一直是开发新的训练方法和模型。而这些努力确实取得了丰硕的成果：从在国际象棋和围棋比赛中战胜世界冠军，到在 SAT 和律师资格考试中超越绝大多数人类考生，再到斩获国际数学奥林匹克（IMO）和国际信息学奥林匹克（IOI）的金牌。这些载入史册的里程碑 —— DeepBlue、AlphaGo、GPT-4 和 o 系列 —— 背后，都离不开 AI 方法上的根本性创新，例如搜索、深度强化学习（Deep Reinforcement Learning）、规模化扩展（Scaling）以及推理能力。AI 的发展，只会随着时间推移变得越来越好。

So what's suddenly different now?

那么，现在究竟发生了什么变化？

In three words: RL finally works. More precisely: RL finally generalizes. After several major detours and a culmination of milestones, we've landed on a working recipe to solve a wide range of RL tasks using language and reasoning. Even a year ago, if you told most AI researchers that a single recipe could tackle software engineering, creative writing, IMO-level math, mouse-and-keyboard manipulation, and long-form question answering — they'd laugh at your hallucinations. Each of these tasks is incredibly difficult and many researchers spend their entire PhDs focused on just one narrow slice.

简单来说，有三个核心词：强化学习（RL）终于「开窍」了。更准确地说：强化学习（RL）终于具备了泛化（generalize）能力。在经历了多次重要的探索和一系列里程碑式的突破后，我们终于找到了一套行之有效的方法，能够利用语言和推理来解决各种各样的强化学习（RL）任务。就在一年前，如果你告诉大多数人工智能（AI）研究人员，一个单一的「秘诀」就能应对软件工程、创意写作、IMO 级别的数学问题、鼠标键盘操作，以及长篇问答 —— 他们一定会觉得你是在痴人说梦。因为这些任务中的每一个都极其困难，许多研究人员甚至会投入整个博士生涯，也仅仅专注于其中一个狭窄的领域。

Yet it happened.

然而，这一切却真实地发生了。

So what comes next? The second half of AI — starting now — will shift focus from solving problems to defining problems. In this new era, evaluation becomes more important than training. Instead of just asking, "Can we train a model to solve X?", we're asking, "What should we be training AI to do, and how do we measure real progress?" To thrive in this second half, we'll need a timely shift in mindset and skill set, ones perhaps closer to a product manager.

那么接下来会发生什么呢？AI 的下半场 —— 从现在开始 —— 将会把重心从「解决问题」转移到「定义问题」。在这个新时代，评估将变得比模型训练更加重要。我们不再仅仅是问：「我们能否训练一个模型来解决某个问题 X？」，而是要思考：「我们到底应该训练 AI 去做什么？以及我们该如何衡量真正的进步？」为了在这个新的阶段中取得成功，我们需要及时调整思维模式和技能结构，而这些或许会更接近一位产品经理的角色。

### The first half

上半场

To make sense of the first half, look at its winners. What do you consider to be the most impactful AI papers so far?

要理解这「上半场」的意义，我们不妨看看其中脱颖而出的那些优秀成果。你认为迄今为止最具影响力的 AI 论文有哪些呢？

I tried the quiz in Stanford 224N, and the answers were not surprising: Transformer, AlexNet, GPT-3, etc. What's common about these papers? They propose some fundamental breakthroughs to train better models. But also, they managed to publish their papers by showing some (significant) improvements on some benchmarks.

我尝试了斯坦福 224N 的一个测验，结果毫不意外地指向了 Transformer、AlexNet、GPT-3 等知名模型。这些论文有什么共同点呢？它们都提出了训练更优秀模型的根本性突破。更重要的是，它们通过在某些基准测试（benchmark）上展现出显著的性能提升，成功发表了各自的论文。

There is a latent commonality though: these "winners" are all training methods or models, not benchmarks or tasks. Even arguably the most impactful benchmark of all, ImageNet, has less than one third of the citation of AlexNet. The contrast of method vs benchmark is even more drastic anywhere else —- for example, the main benchmark of Transformer is WMT'14, whose workshop report has ~1,300 citations, while Transformer had >160,000.

然而，其中有一个潜在的共同点：这些「赢家」都指的是训练方法或模型，而非基准测试或任务。即使是公认最具影响力的基准测试 ImageNet，它的引用量也只有 AlexNet 的不到三分之一。方法与基准测试之间的这种对比在其他任何领域都更为显著 —— 例如，Transformer 的主要基准测试是 WMT'14，其研讨会报告的引用量约为 1,300 次，而 Transformer（Transformer）本身的引用量则超过了 160,000 次。

That illustrates the game of the first half: focus on building new models and methods, and evaluation and benchmark are secondary (although necessary to make the paper system work).

这表明了前半段时期（或者说早期阶段）的重心所在：大家更专注于构建新的模型和方法，而评估（evaluation）和基准测试（benchmark）则相对是次要的（尽管它们对于确保学术论文体系正常运作是必不可少的）。

Why? A big reason is that, in the first half of AI, methods were harder and more exciting than tasks. Creating a new algorithm or model architecture from scratch – think of breakthroughs like the backpropagation algorithm, convolutional networks (AlexNet), or the Transformer used in GPT-3 – required remarkable insight and engineering. In contrast, defining tasks for AI often felt more straightforward: we simply took tasks humans already do (like translation, image recognition, or chess) and turned them into benchmarks. Not much insight or even engineering.

为什么会这样？一个重要原因是，在 AI 发展的早期阶段，设计「方法」（即 AI 模型和算法）比定义「任务」本身更具挑战性也更引人入胜。从头设计新的算法或模型架构 —— 例如像反向传播算法、卷积网络（AlexNet）这样的突破，或是 GPT-3 中使用的 Transformer 架构 —— 都需要非凡的洞察力和精湛的工程技术。相比之下，为 AI 定义任务则显得没那么复杂：我们只需直接将人类已经完成的任务（比如翻译、图像识别或国际象棋）作为衡量 AI 能力的基准。这其中并不需要太多的洞察力，甚至也无需进行复杂的工程设计。

Methods also tended to be more general and widely applicable than individual tasks, making them especially valuable. For example, the Transformer architecture ended up powering progress in CV, NLP, RL, and many other domains – far beyond the single dataset (WMT'14 translation) where it first proved itself. A great new method can hillclimb many different benchmarks because it's simple and general, thus the impact tends to go beyond an individual task.

这些方法往往比特定任务更具通用性和广泛适用性，这使得它们尤其宝贵。例如，Transformer 架构最终助力了计算机视觉（CV）、自然语言处理（NLP）、强化学习（RL）以及许多其他领域的进步 —— 其应用范围远远超出了最初验证其效果的单一数据集（WMT'14 翻译）。一个卓越的新方法，因其简单和通用，能在许多不同的基准测试中表现出色，因此其影响力往往超越了单一任务的范畴。

This game has worked for decades and sparked world-changing ideas and breakthroughs, which manifested themselves by ever-increasing benchmark performances in various domains. Why would the game change at all? Because the cumulation of these ideas and breakthroughs have made a qualitative difference in creating a working recipe in solving tasks.

这种「游戏」模式已经持续了几十年，它激发了无数改变世界的想法和重大突破，这些成就体现在各个领域不断提升的基准性能上。那么，为什么这种模式会发生改变呢？这是因为这些想法和突破的不断积累，在解决具体任务时，已经形成了一套行之有效的方案，从而带来了质的飞跃。

### The recipe

配方

What's the recipe? Its ingredients, not surprisingly, include massive language pre-training, scale (in data and compute), and the idea of reasoning and acting. These might sound like buzzwords that you hear daily in SF, but why call them a recipe??

配方究竟是什么？毫不意外，它的核心要素包括：大规模语言预训练（massive language pre-training）、体量（scale）（涵盖数据量和计算力），以及推理与行动（reasoning and acting）的核心思想。这些词听起来可能像是你在旧金山每天都能听到的那些时髦词（buzzwords），但我们为什么要称它们为「配方」呢？

We can understand this by looking through the lens of reinforcement learning (RL), which is often thought of as the "end game" of AI — after all, RL is theoretically guaranteed to win games, and empirically it's hard to imagine any superhuman systems (e.g. AlphaGo) without RL.

我们可以通过强化学习（RL）的视角来理解这一点。强化学习常被认为是人工智能（AI）的「终极目标」—— 毕竟，从理论上讲，RL 保证能赢得各种游戏；而从实践经验来看，很难想象没有 RL 的超人类系统（例如 AlphaGo）会如何运作。

In RL, there are three key components: algorithm, environment, and priors. For a long time, RL researchers focused mostly on the algorithm (e.g. REINFORCE, DQN, TD-learning, actor-critic, PPO, TRPO…) – the intellectual core of how an agent learns – while treating the environment and priors as fixed or minimal. For example, Sutton and Barto's classical textbook is all about algorithms and almost nothing about environments or priors.

在强化学习（RL）中，有三个关键组成部分：算法、环境和先验。长期以来，强化学习的研究人员主要将精力集中在算法上（例如 REINFORCE、DQN、TD-learning、actor-critic、PPO、TRPO 等）—— 这部分是智能体学习的核心机制 —— 而环境和先验则常被视为固定不变或不那么重要的部分。举例来说，Sutton 和 Barto 的经典教科书几乎完全围绕算法展开，很少提及环境或先验。

However, in the era of deep RL, it became clear that environments matter a lot empirically: an algorithm's performance is often highly specific to the environment it was developed and tested in. If you ignore the environment, you risk building an "optimal" algorithm that only excels in toy settings. So why don't we first figure out the environment we actually want to solve, then find the algorithm best suited for it?

然而，在深度强化学习（Deep RL）时代，我们从实践中清楚地认识到环境的重要性：一个算法的性能在很大程度上取决于其开发和测试所处的环境。如果你忽视了环境，你就有可能构建出一个只在「玩具设置」（toy settings）中表现出色的「最优」算法。既然如此，我们为什么不先弄清楚我们真正想要解决的环境是什么，然后再找到最适合它的算法呢？

That's exactly OpenAI's initial plan. It built gym, a standard RL environment for various games, then the World of Bits and Universe projects, trying to turn the Internet or computer into a game. A good plan, isn't it? Once we turn all digital worlds into an environment, solve it with smart RL algorithms, we have digital AGI.

这正是 OpenAI 最初的计划。它构建了 gym，一个用于各种游戏的标准强化学习（Reinforcement Learning，RL）环境，随后又推出了 World of Bits 和 Universe 项目，旨在将互联网或电脑变成一个游戏。听起来是个不错的计划，对吧？一旦我们将所有的数字世界都转化成一个环境，并通过智能的强化学习算法来应对它，我们就拥有了数字通用人工智能（Artificial General Intelligence，AGI）。

A good plan, but not entirely working. OpenAI made tremendous progress down the path, using RL to solve Dota, robotic hands, etc. But it never came close to solving computer use or web navigation, and the RL agents working in one domain do not transfer to another. Something is missing.

这是一个不错的计划，但并未完全奏效。OpenAI 在这条发展道路上取得了巨大进展，他们利用强化学习（RL）解决了像 Dota 游戏和机械手操作等一系列问题。然而，它却从未接近解决复杂的计算机使用或网络导航难题，而且在一个领域中训练出的强化学习智能体（RL agents）无法直接迁移到其他领域。由此看来，似乎还缺少了某些关键要素。

Only after GPT-2 or GPT-3, it turned out that the missing piece is priors. You need powerful language pre-training to distill general commonsense and language knowledge into models, which then can be fine-tuned to become web (WebGPT) or chat (ChatGPT) agents (and change the world). It turned out the most important part of RL might not even be the RL algorithm or environment, but the priors, which can be obtained in a way totally unrelated from RL.

直到 GPT-2 或 GPT-3 问世之后，人们才逐渐意识到，此前缺失的关键在于「先验知识（priors）」。我们需要强大的语言预训练，将通用常识和语言知识提炼到模型中。随后，这些模型可以通过微调，摇身一变成为网络（WebGPT）或聊天（ChatGPT）AI 智能体（AI Agent），进而改变世界。事实证明，强化学习（RL）中最重要的部分，可能并非是其算法或环境本身，而是这些先验知识，它们甚至可以通过与强化学习完全无关的方式来获取。

Language pre-training created good priors for chatting, but not equally good for controlling computers or playing video games. Why? These domains are further from the distribution of Internet text, and naively doing SFT / RL on these domains generalizes poorly. I noticed the problem in 2019, when GPT-2 just came out and I did SFT / RL on top of it to solve text-based games - CALM was the first agent in the world built via pre-trained language models. But it took millions of RL steps for the agent to hillclimb a single game, and it doesn't transfer to new games. Though that's exactly the characteristic of RL and nothing strange to RL researchers, I found it weird because we humans can easily play a new game and be significantly better zero-shot. Then I hit one of the first eureka moment in my life - we generalize because we can choose to do more than "go to cabinet 2" or "open chest 3 with key 1" or "kill dungeon with sword", we can also choose to think about things like "The dungeon is dangerous and I need a weapon to fight with it. There is no visible weapon so maybe I need to find one in locked boxes or chests. Chest 3 is in Cabinet 2, let me first go there and unlock it".

语言预训练为聊天功能奠定了很好的基础，但对于控制计算机或玩电子游戏来说，效果却不尽如人意。这是为什么呢？因为这些领域与互联网文本的分布差异较大，如果仅仅简单地（naively）在这些领域进行 SFT（Supervised Fine-Tuning，监督微调）或 RL（Reinforcement Learning，强化学习），其泛化能力会很差。我在 2019 年就注意到了这个问题，当时 GPT-2 刚刚发布，我在此基础上应用 SFT 和 RL 来解决基于文本的游戏 —— CALM 是世界上第一个基于预训练语言模型构建的 AI 智能体（AI Agent）。然而，这个 AI 智能体需要经过数百万个 RL 步骤才能在一个游戏中缓慢提升表现（hillclimb），并且无法将学到的经验应用到新游戏中。尽管这正是强化学习的典型特征，对 RL 研究人员而言司空见惯，但我却觉得很奇怪，因为我们人类可以轻松上手新游戏，并且在零样本（zero-shot）情况下表现明显更好。这时，我迎来了人生中第一次豁然开朗的时刻 —— 我们之所以能泛化，是因为我们不仅可以选择执行「去柜子 2」、「用钥匙 1 打开箱子 3」或「用剑清除地下城」这样的具体操作，我们还可以选择进行思考，比如：「地下城很危险，我需要一把武器来对抗它。这里没有看得见的武器，所以也许我需要在上锁的盒子或箱子里找找看。箱子 3 在柜子 2 里，那我先去那里把它打开。」

Thinking, or reasoning, is a strange kind of action - it does not directly affect the external world, yet the space of reasoning is open-ended and combintocially infinite — you can think about a word, a sentence, a whole passage, or 10000 random English words, but the world around you doesn't immediate change. In the classical RL theory, it is a terrible deal and makes decision-making impossible. Imagine you need to choose one out of two boxes, and there's only one box with $1M and the other one empty. You're expected to earn $500k. Now imagine I add infinite empty boxes. You're expected to earn nothing. But by adding reasoning into the action space of any RL environment, we make use of the language pre-training priors to generalize, and we afford to have flexible test-time compute for different decisions. It is a really magical thing and I apologize for not fully making sense of it here, I might need to write another blog post just for it. You're welcome to read ReAct for the original story of reasoning for agents and read my vibes at the time. For now, my intuitive explanation is: even though you add infinite empty boxes, you have seen them throughout your life in all kinds of games, and choosing these boxes prepare you to better choose the box with money for any given game. My abstract explanation would be: language generalizes through reasoning in agents.

思考，或者说推理（reasoning），是一种奇特的行为 —— 它不直接影响外部世界，然而推理的空间却是开放的，并且具有无限组合的可能性 —— 你可以思考一个词、一个句子、一整段文字，甚至 10000 个随机的英文单词，但你周围的世界并不会立即改变。在经典的强化学习（RL）理论中，这是一个极不利的情况，使得决策变得不可能。想象一下，你需要从两个箱子中选择一个，其中只有一个箱子里有 100 万美元，另一个是空的。你期望能获得 50 万美元。现在，想象我添加了无限多的空箱子。你理论上将一无所获。但是，通过将推理（reasoning）添加到任何 RL 环境的行动空间中，我们利用语言预训练的先验知识来实现泛化，并且我们能够为不同的决策提供灵活的测试时计算。这是一个真正奇妙之处，对于未能在此处充分阐明这一点，我深表歉意，我可能需要为此专门写一篇博客文章。欢迎阅读 ReAct [原文链接] ，了解关于智能体（AI Agent）推理的最初理念，并阅读我当时的心情和观点。目前，我的直观解释是：即使你添加了无限多的空箱子，你在生活中各种游戏中都见过它们，选择这些箱子能让你在任何给定游戏中更好地选择那个装有钱的箱子。我的抽象解释是：语言通过智能体中的推理实现泛化。

[[2210.03629] ReAct: Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629)

Once we have the right RL priors (language pre-training) and RL environment (adding language reasoning as actions), it turns out RL algorithm might be the most trivial part. Thus we have o-series, R1, deep research, computer-using agent, and so much more to come. What a sarcastic turn of events! For so long RL researchers cared about algorithms way more than environments, and no one paid any attention to priors — all RL experiments essentially start from scratch. But it took us decades of detours to realize maybe our prioritization should have be completely reversed.

一旦我们拥有了正确的强化学习（RL）先验知识（例如语言预训练）和合适的强化学习（RL）环境（将语言推理融入到智能体的动作中），强化学习（RL）算法本身反而可能成了最不重要的部分。正因如此，我们看到了 o-series、R1、deep research、computer-using agent 等一系列项目，未来还会有更多创新涌现。这真是一个富有讽刺意味的转折！长期以来，强化学习（RL）研究人员一直将重心放在算法上，对环境的关注远超先验知识，几乎所有强化学习（RL）实验都像是从零开始。然而，我们绕了几十年弯路才终于意识到，也许我们当初的优先级设置应该彻底颠倒过来。

But just like Steve Jobs said: You can't connect the dots looking forward; you can only connect them looking backward.

但是，正如 Steve Jobs 所说：你无法预见未来而将点点滴滴串联起来；只有回首过去，才能明白其中的关联。

### The second half

下半部分

This recipe is completely changing the game. To recap the game of the first half:

这个方法正在彻底改变局面。回顾一下前期我们做了什么：

1 We develop novel training methods or models that hillclimb benchmarks.

我们开发了新颖的训练方法或模型，这些方法和模型能在基准测试（benchmarks）中不断提升表现。

2 We create harder benchmarks and continue the loop.

我们创建了难度更高的基准（benchmarks），并持续这个循环。

This game is being ruined because:

这种模式正在被打破，因为：

1 The recipe has essentially standardized and industried benchmark hillclimbing without requiring much more new ideas. As the recipe scales and generalizes well, your novel method for a particular task might improve it by 5%, while the next o-series model improve it by 30% without explicitly targeting it.

目前这种方法（the recipe）本质上已经将基准「爬山算法」（benchmark hillclimbing）进行了标准化和工业化，并且不再需要很多全新的思路。由于这种方法具备良好的扩展性和泛化能力，你针对特定任务提出的创新方法可能只能带来 5% 的提升，而下一个 o-series 模型即使没有明确针对该任务，也能实现 30% 的性能提升。

2 Even if we create harder benchmarks, pretty soon (and increasingly soon) they get solved by the recipe. My colleague Jason Wei made a beautiful figure to visualize the trend well:

即使我们设定了更具挑战性的基准（benchmark），这些基准也会很快（而且解决的速度越来越快）被这个「秘方」攻克。我的同事 Jason Wei 绘制了一张精美的图表，清晰地展示了这一趋势：

Then what's left to play in the second half? If novel methods are no longer needed and harder benchmarks will just get solved increasingly soon, what should we do?

那么，下半场我们还能做什么呢？如果新颖的方法（novel methods）不再是必需品，而且更难的基准（benchmarks）也将以越来越快的速度被攻克，我们又该何去何从呢？

I think we should fundamentally re-think evaluation. It means not just to create new and harder benchmarks, but to fundamentally question existing evaluation setups and create new ones, so that we are forced to invent new methods beyond the working recipe. It is hard because humans have inertia and seldom question basic assumptions - you just take them for granted without realizing they are assumptions, not laws.

我认为我们应该对评估（evaluation）进行根本性的重新思考。这意味着我们不应仅仅满足于创建新的、难度更高的基准（benchmark），而是要从根本上质疑现有的评估体系，并建立全新的评估机制。这样做才能促使我们去发明和探索超越现有成熟方案的新方法。这之所以困难，是因为人类思维存在惯性，我们很少去质疑那些基本假设 —— 人们常常想当然地接受这些假设，却没有意识到它们仅仅是假设，而非不可更改的定律。

To explain inertia, suppose you invented one of the most successful evals in history based on human exams. It was an extremely bold idea in 2021, but 3 years later it's saturated. What would you do? Most likely create a much harder exam. Or suppose you solved simply coding tasks. What would you do? Most likely find harder coding tasks to solve until you have reached IOI gold level.

为了解释惯性这个概念，假设你发明了一种历史上最成功的评估方法（evals），而这种方法是基于人类考试设计的。这在 2021 年是一个极其大胆的创新，但仅仅三年后，这种评估方法就已经达到饱和状态了。面对这种情况，你会怎么做呢？最有可能的答案是设计一个难度更大的考试。又或者，假设你已经能够轻松解决相对简单的编程任务。那么接下来你会怎么做？很可能你会继续寻找并解决难度更高的编程任务，直到你达到了国际信息学奥林匹克竞赛（IOI）的金牌水平。

Inertia is natural, but here is the problem. AI has beat world champions at chess and Go, surpassed most humans on SAT and bar exams, and reached gold medal level on IOI and IMO. But the world hasn't changed much, at least judged by economics and GDP.

惯性是事物常态，但这里有一个值得思考的问题。人工智能（AI）已经在国际象棋和围棋比赛中击败了世界冠军，在 SAT 和律师资格考试中超越了绝大多数人类，甚至在国际信息学奥林匹克（IOI）和国际数学奥林匹克（IMO）中达到了金牌水平。然而，至少从经济和国内生产总值（GDP）来看，世界似乎并没有发生太大改变。

I call this the utility problem, and deem it the most important problem for AI.

我将这称为效用问题（utility problem），并认为它是人工智能（AI）最重要的问题。

Perhaps we will solve the utility problem pretty soon, perhaps not. Either way, the root cause of this problem might be deceptively simple: our evaluation setups are different from real-world setups in many basic ways. To name two examples:

我们也许很快就能解决效用问题，也许不能。无论哪种情况，这个问题的根本原因可能看似简单却迷惑人：我们的评估设置（evaluation setups）在许多基本方面与真实世界设置（real-world setups）不同。举两个例子：

1 Evaluation "should" run automatically, so typically an agent receives a task input, do things autonomously, then receive a task reward. But in reality, an agent has to engage with a human throughout the task — you don't just text customer service a super long message, wait for 10 minutes, then expect a detailed response to settle everything. By questioning this setup, new benchmarks are invented to either engage real humans (e.g. Chatbot Arena) or user simulation (e.g. tau-bench) in the loop.

评估过程「通常认为」应该自动运行，因此一个 AI 智能体（AI Agent）通常会接收一个任务输入，自主执行任务，然后获得任务奖励。但现实情况是，AI 智能体必须在整个任务过程中与人类持续交互 —— 你不能指望给客服发一条超长的消息，等待 10 分钟，然后就能收到一份详细回复来一劳永逸地解决所有问题。通过质疑这种评估模式，新的基准（benchmark）应运而生，它们或是让真实人类参与到评估循环中（例如 Chatbot Arena），或是采用用户模拟（user simulation）的方式（例如 tau-bench）。

2 Evaluation "should" run i.i.d. If you have a test set with 500 tasks, you run each task independently, average the task metrics, and get an overall metric. But in reality, you solve tasks sequentially rather than in parallel. A Google SWE solves google3 issues increasingly better as she gets more familiar with the repo, but a SWE agent solves many issues in the same repo without gaining such familiarity. We obviously need long-term memory methods (and there are), but academia does not have the proper benchmarks to justify the need, or even the proper courage to question i.i.d. assumption that has been the foundation of machine learning.

评估模型时，「理想情况」是采用独立同分布（i.i.d.，independent and identically distributed）的方式。比如，如果你有一个包含 500 个任务的测试集，你会独立地运行每个任务，然后将这些任务的指标取平均，从而得到一个总体的评估指标。但实际上，我们解决任务时往往是按顺序进行的，而不是并行处理。就像一位 Google 软件工程师（SWE）会随着对代码库（repo）越来越熟悉，解决 google3 中问题会越来越得心应手；然而，一个 SWE AI 智能体（AI Agent）却可能在同一个代码库中解决了大量问题，却无法获得这种长期的熟悉度。显然，我们需要引入长期记忆的方法（而且这方面已经有一些研究），但学术界目前缺乏合适的基准来验证这种方法的必要性，甚至可以说，大家缺少勇气去质疑这个长期以来作为机器学习基础的独立同分布（i.i.d.）假设。

These assumptions have "always" been like this, and developing benchmarks in these assumptions were fine in the first half of AI, because when the intelligence is low, improving intelligence generally improves utility. But now, the general recipe is guaranteed to work under these assumptions. So the way to play the new game of the second half is

这些假设「一直」以来都是如此，在人工智能（AI）发展的上半场，基于这些假设来开发基准（benchmark）是没有问题的。因为在智能水平不高时，提高智能通常也能提升其实用价值。但现在，在这些假设下，一套通用的解决方案几乎可以保证奏效。因此，要想玩好下半场的新游戏，方法就是

1 We develop novel evaluation setups or tasks for real-world utility.

我们开发创新的评估方法或任务，以使其在实际应用中具备实用价值。

2 We solve them with the recipe or augment the recipe with novel components. Continue the loop.

我们利用「配方」来解决这些问题，或者通过引入新颖的组件来改进「配方」，然后循环往复，不断优化。

This game is hard because it is unfamiliar. But it is exciting. While players in the first half solve video games and exams, players in the second half get to build billion or trillion dollar companies by building useful products out of intelligence. While the first half is filled with incremental methods and models, the second half filters them to some degree. The general recipe would just crush your incremental methods, unless you create new assumptions that break the recipe. Then you get to do truly game-changing research.

这个「游戏」之所以困难，是因为它非常陌生，但却令人兴奋。如果说前半场玩家的任务是攻克视频游戏和考试，那么后半场玩家的目标则是通过利用智能（intelligence）打造有用的产品，从而创建价值数十亿乃至数万亿美元的公司。前半场关注的是渐进式的研究方法和模型，而到了后半场，它们在某种程度上会被筛选或淘汰。面对普遍适用的「通用范式」，你的渐进式方法很可能会被其压倒，除非你能提出新的假设来打破这种范式。只有这样，你才能进行真正具有颠覆性的研究。

Welcome to the second half!

欢迎来到下半场。

### Acknowledgements

致谢

This blog post is based on my talk given at Stanford 224N and Columbia. I used OpenAI deep research to read my slides and write a draft.

这篇博文是基于我在 Stanford 224N 和 Columbia 的演讲内容。我利用 OpenAI 的深度研究能力，分析了我的幻灯片，并撰写了初稿。

Written on April 10, 2025

撰写于 2025 年 4 月 10 日