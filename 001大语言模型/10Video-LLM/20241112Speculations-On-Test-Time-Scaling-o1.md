## 20241112Speculations-On-Test-Time-Scaling-o1

Speculations on test time scaling. Say what you will about OpenAI, they make iconic graphs. This graph is from the GPT-3 paper. It's one of several different graphs that demonstrate, as language model parameters get larger, the models perform better at zero-shot tasks. This graph, and many others like it, has occupied the interest of the language modeling community for the last five years. It really changed the way we think about many different problems and how we build, design, scale, and invest in models. In fact, right now, it's safe to say that there are nuclear power plants being built just to support this graph.

关于测试时间扩展的猜想。先不论你对 OpenAI 有何看法，但他们确实制作了一些具有里程碑意义的图表。其中一张图就来自 GPT-3 的论文。这张图与该论文中的其他几张图表共同揭示了一个现象：随着语言模型（Large Language Model）参数规模的增大，模型在零样本（Zero-shot）任务上的表现也越发优秀。在过去的五年里，这张图以及许多类似的研究成果一直备受语言建模社区的关注。它实实在在地改变了我们思考诸多问题的方式，也深刻影响了我们构建、设计、扩展和投资模型的方法。事实上，现在甚至可以毫不夸张地说，为了满足这种模型规模持续增长所带来的巨大计算需求，一些核电站正在建设中。

Recently, OpenAI released a new graph. Given the impact of their previous ones, I take this pretty seriously. In this graph, on the left-hand side, we see a curve that looks pretty similar to the curve we've seen before. In this curve, we see that more training time compute leads to consistently better accuracy on a hard task. On the right-hand side of this graph, we see a new curve. This curve looks similar in that we're seeing compute contrasted with the performance of the model. What's different is that this curve is showing test time compute. And what we are seeing is the performance on this task get much better as we add more test time compute to the system. This is new. We haven't seen this before in language modeling, and it's a topic of great interest.

最近，OpenAI 发布了一张新图表。考虑到他们以往图表所产生的影响，这份新图表引起了广泛关注。在这张图表的左侧，我们看到一条与之前常见的曲线非常相似的曲线。这条曲线表明，随着训练时间计算量（training time compute）的增加，模型在处理复杂任务时的准确率会持续提升。而在图表的右侧，我们看到了一条全新的曲线。这条曲线同样展示了计算量与模型性能之间的关系。不同之处在于，这条曲线关注的是测试时间计算量（test time compute）。我们观察到，随着系统中测试时间计算量的增加，模型在该任务上的性能得到了显著提升。这是一个全新的发现，在此之前，我们从未在语言建模（language modeling）领域中见到过类似现象，这无疑是一个备受关注的重要话题。

### 01

Before we dive into this topic more, it's worth noting what these problems actually look like. Well, they're pretty hard. We're not just doing retrieval or things that look a bit more like pattern matching. We're doing full-on reasoning in technical mathematical problems.

在我们深入探讨这个话题之前，有必要先了解一下这些问题究竟有多难。可以说，它们相当棘手。我们不仅仅是在进行信息检索，也不是在做那些更像是模式匹配的任务，而是要对技术性的数学问题进行全面的逻辑推理。

One essay that often comes up when discussing these sort of scaling challenges is *The Bitter Lesson*. You've probably read this blog post before, but it's worth giving you a sense of what it's saying and how it applies to this problem. The bitter lesson is based on the historical observations that AI researchers have often tried to build knowledge into their agents. This always helps in the short term and is personally satisfying to the researcher. But in the long run, it plateaus and even inhibits further progress. And breakthrough progress eventually arrives by opposing approaches based on scaling computation by search and learning.

在讨论这类规模化挑战时，有一篇文章经常被提及，那就是《惨痛的教训》。你可能以前读过这篇博客文章，但它的核心观点以及它如何应用于当前问题，仍然值得我们了解。《惨痛的教训》是基于历史经验表明：人工智能研究人员经常尝试将知识注入到他们的 AI 智能体中。虽然这在短期内总是有所帮助，也让研究人员个人感到满足，但从长远来看，这种做法会停滞不前，甚至阻碍进一步的进展。最终，突破性的进展往往是通过基于搜索和学习、扩展计算能力的对立方法实现的。

I bring it up today because it's been a popular conversation among researchers in this space. What we've seen for the last five years is increase in the learning capability of models. What we might be seeing now is a move towards search, in particular, a type of search that is facilitated by learning to allow us to scale on some of these more technical problems.

我今天之所以提出这个话题，是因为它一直是这个领域研究人员热议的焦点。过去五年来，我们目睹了模型学习能力的显著提升。而现在，我们可能正迈向一个新的阶段：转向搜索，特别是那种由学习能力驱动的搜索方式，它能帮助我们更高效地解决一些复杂的、技术性难题。

In preparing this talk, I also watched some of the recent talks by Nolan Brown, one of the contributors to this system. One thing he recommended when talking about his past work is he said that the most important lesson is that I and other researchers simply didn't know how much of a difference scaling up search would make. If I'd seen these scaling results at the start of my PhD, I would have shifted to researching search algorithms for poker much sooner. We probably would have gotten superhuman poker bots much sooner as well. While he's talking here about game playing, the goal of his conversation is to encourage the field in general to think more about search.

在准备这次演讲时，我也观看了一些该系统贡献者之一诺兰·布朗（Nolan Brown）最近的演讲。他在谈论自己过去的工作时提到，最重要的经验教训是：他和其他研究人员当时根本不知道扩大搜索规模会带来多大的不同。他表示，如果他在博士研究初期就看到这些规模化结果，他会更早地转向研究扑克的搜索算法。那样，我们可能也会更早地开发出超越人类水平的扑克机器人。虽然他在这里谈论的是游戏玩法，但他此番谈话的目的是鼓励整个领域更广泛地思考搜索问题。

One of the other papers he brings up is a paper I found to be very influential around people in this area, even though it's not more widely known. This is a paper from 2021 that discusses scaling laws for board games. In this setting, it's easy to move back and forth between more training and more test time search. And in the paper, they describe how these two terms relate to each other. In particular in these curves here, they show that there is a trade-off, that with more training time in the model itself, you can learn better systems. But that this alone doesn't replace the test time compute. By plotting these two points together, you can understand the relative relationships between these two and learn how to actually apply them in practice.

他提到的另一篇论文，虽然没有广为人知，但我发现在这个领域里，它对很多人都产生了深远影响。这是一篇发表于 2021 年的论文，主要探讨了棋盘游戏的「缩放定律」。在这种背景下，模型训练时间和测试时的搜索耗时可以轻松地相互切换。论文中详细阐述了这两个因素是如何相互关联的。特别是通过论文中的曲线图，作者展示了其中存在一种权衡关系：模型自身投入更多的训练时间，确实能帮助我们构建出更优秀的系统。但仅仅依靠训练时间的增加，并不能完全替代测试阶段所需的计算资源。通过将这两个点（即训练时间和测试时搜索）放在一起分析，我们就能理解它们之间的相对关系，并学会在实际应用中如何有效地利用它们。

When talking about similar techniques for language models, people often bring up a paper from OpenAI from 2021. In this paper, they're going to train what we'll call a learned verifier. To do this, they will use a generative model to produce hundreds of different solutions. They'll then have experts look at these solutions and select which are right and which are wrong. Using this information, they can then train a verifier. This verifier will tell you if you're doing well on the problem and can be used at test time to try to improve your answers. While there are a lot of details to the paper itself, one of the most important results is they show that searching against this learned verifier can lead to improvements even upon just training on the actual good answers themselves.

在讨论语言模型的类似技术时，人们经常会提及 OpenAI 在 2021 年发表的一篇论文。在这篇论文中，他们训练了一个我们称之为学习型验证器（learned verifier）。为了实现这一点，他们利用一个生成模型（generative model）来产生数百种不同的解决方案。随后，专家们会审查这些解决方案，并从中筛选出正确与错误的答案。基于这些信息，他们便能训练出一个验证器。这个验证器能够评估你在解决问题时的表现，并可在测试阶段用于优化你的回答。尽管这篇论文包含了诸多细节，但其中一个最重要的发现是：他们证明了针对这个学习型验证器进行搜索，甚至能比单纯依赖真实正确答案进行训练，带来更显著的性能提升。

In this graph here, the orange line shows the accuracy of the model that is running against the verifier compared to a model that's just trained on the trajectories themselves. This is an argument for moving beyond the standard supervised fine-tuning, or SFT, more to a system that utilizes a learned verifier in order to inject new signal into the model. This allows you to utilize that verifier to improve the model at test time.

在这张图中，橙色线展示了一个模型在对照验证器运行时所获得的准确性，并将其与一个仅基于轨迹本身进行训练的模型进行了比较。这表明我们应该超越传统的监督微调（SFT）方法，转而采用一种利用学习到的验证器来为模型注入新信号的系统。这样做使得我们能够在测试时利用这个验证器来进一步提升模型的性能。

As we'll see, we don't think this is exactly what OpenAI is doing, but it gives you a sense of how they were exploring early uses of test time compute in developing their systems. And actually on that note, we really know very little about what is going on in OpenAI. In fact, I'm not going to really focus too much on trying to predict what they actually are doing, but I'd like to use the release of this model as an opportunity to provide a survey about what's going on in the open research field.

正如我们将看到的，我们认为这并非 OpenAI 正在做的具体事情，但这能让你大致了解他们在开发系统时是如何探索测试时计算（test time compute）的早期应用的。实际上，关于这一点，我们对 OpenAI 内部的情况知之甚少。事实上，我不会过多地去预测他们到底在做什么，但我希望借此模型发布的机会，对开放研究领域正在发生的一切进行一次调查。

### 02

In this talk, I'll give a survey of the public literature related to OpenAI's O1. As part of this process, I also took the opportunity to call up a lot of different researchers in the field. It's a nice perk of being a professor that a lot of different people will talk to me. And for this talk, I talked to about 25 different people about what they think is going on. Finally, I will include some rumors from social media. I'm not gonna weight these too highly because who knows what's going on in practice, but that will give us some constraints for thinking about what the system could be doing.

在本次演讲中，我将对与 OpenAI 的 O1 相关的公开文献进行一次全面回顾。在此过程中，我还借此机会联系了该领域的许多研究人员。作为一名教授，有一个好处就是很多人都愿意与我交流。为了这次演讲，我与大约 25 位不同的人进行了交谈，听取了他们对当前进展的看法。最后，我还会分享一些来自社交媒体的传闻。我不会过分看重这些传闻，因为实际情况谁也说不准，但它们能为我们思考这个系统可能在做什么提供一些参考线索。

The talk itself will have four more parts. First, we'll talk about some of the clues behind what O1 might be. Then I'll provide some technical background behind the techniques that are actually used in these systems. Finally, I'll discuss four different suspects, why I think they're interesting, what papers have been written about them, and whether or not they might be what's going on. Finally, I'll end by talking about some implications for researchers or open source practitioners in this area.

本次讲座将分为四个部分。首先，我们将探究关于 O1 可能是什么的一些线索。接着，我将介绍这些系统中实际运用的技术背景。最后，我将讨论四种不同的可能情况，包括我认为它们有趣的原因、相关的研究论文，以及它们是否能解释当前实际发生的事情。本次讲座的结尾，我将讨论这些发现对该领域研究人员或开源实践者的影响。

To gather clues, let's start with OpenAI's own words. In a blog post published with the release of O1, they wrote a lot about this topic, but much of it is mostly just marketing. There are two sentences, though, that give us a sense about what might be happening. First, they say, "Our large-scale reinforcement learning algorithm teaches the model how to think productively using its chain of thought in a highly data-efficient training process."

为了收集线索，我们先来看看 OpenAI 自己是怎么说的。在发布 O1 模型时，他们同时发表了一篇博客文章，其中谈论了这个话题很多，不过大部分内容都只是宣传。然而，有两句话确实让我们得以一窥其背后的奥秘。首先，他们提到：「我们的大规模强化学习（Reinforcement Learning）算法通过一个数据高效的训练过程，教会模型如何利用其思维链（Chain of Thought）进行富有成效的思考。」

This sentence gives us three clues into what might be happening. The first is that the system is using reinforcement learning. The precise definition of reinforcement learning has become quite hard to pin down, and it means different things to different people. I'm going to adapt the most loose definition and just say it requires some signal from some sort of verifiable problem. We're going to assume we don't have supervised data, and we need to acquire the signal in other ways.

这句话为我们揭示可能发生的情况提供了三个线索。首先，系统正在使用强化学习（Reinforcement Learning）。强化学习的精确定义如今已变得相当难以界定，不同的人对其有不同的理解。我将采纳最宽松的定义，简单来说，它需要从某种可验证的问题中获取信号。我们假设没有监督数据（Supervised Data），因此需要通过其他方式来获取这些信号。

Secondly, the method uses chain of thought. Specifically, it's using chain of thought as its method of increasing test time compute. What this means is that we're not doing any sort of search during test time. In fact, the system is just generating a very long output stream and using that to make its final prediction. We'll discuss this more throughout the talk.

其次，该方法采用了思维链（Chain of Thought）。具体来说，它利用思维链来提高测试时的计算能力。这意味着我们在测试时不会进行任何搜索。实际上，系统只是生成一个非常长的输出流，并以此作为最终预测。我们将在接下来的演讲中更详细地探讨这一点。

Finally, the system is data efficient. What this means is that it's learned from a relatively small set of data examples. This is not making any claim about compute efficiency or even parameter efficiency, just that the amount of actual problems it needs is relatively small, where relative here is compared to, say, training on the entire internet.

最后，该系统实现了数据高效。这意味着它仅仅通过相对较少的数据示例就完成了学习。这里并不是说它在计算效率或参数效率方面表现突出，而只是强调它所需处理的实际数据量相对较少，这里的「相对」是与在整个互联网上进行训练这类任务相比而言的。

### 02

In addition to this sentence, there are several other assumptions that people seem to be making about these models. The first is that it is a single final language model that generates an extremely long and coherent chain of thought. Just to make that clear once again, it's just a model that babbles to itself until it thinks it has good enough information to make a guess of the answer to your hard problem.

除了这个观点，人们似乎对这些模型还抱有几个其他的假设。首先，有人认为它们是一个单一的、最终的语言模型，能够生成极其漫长且连贯的思考过程。为了再次强调，实际上，这些模型只是在不断地「自言自语」，直到它们觉得收集到了足够充分的信息，可以尝试给出你所提出难题的答案。

Second, we assume the model is not following from expert examples. This is not to say there isn't a huge amount of human supervision. It's just that that supervision is not given in the form of direct human answers to questions. It's not copying along with what humans did.

其次，我们假设模型并非通过模仿专家示例来学习。这并不是说没有大量的人工监督，只是这种监督并非以人类直接回答问题的形式提供。它并非照搬人类的做法。

Finally, there's an assumption that the behaviors it exhibits are learned. That means they come somehow from data or self-play, but not from being given to the model explicitly. Of these assumptions, the most important one is this idea of chain of thought. Let's describe what this means informally, and then we'll dive into a bit more of a formal explanation later in the talk.

最后，还有一种假设认为模型所展现的行为都是习得的。这意味着这些行为是通过数据或自我博弈（self-play）学习而来的，而不是通过显式编程直接赋予模型的。在所有这些假设中，最核心的便是「思维链（chain of thought）」这一概念。接下来，我们先通俗地解释一下它的含义，稍后在演讲中再进行更正式的阐述。

The informal definition is that the model is going to generate intermediate steps in the process of producing an answer. These intermediate steps are not supervised, but are simply sampled from the language model as we go.

非正式地讲，模型会在生成答案的过程中，产生一些中间步骤。这些中间步骤是未经监督的，而是在模型运行过程中，直接从语言模型中采样得到的。

So, in this example on the right, we are given a question written in red. Then, we produce four steps of chain of thought written in green below. Each of these steps computes some intermediate term in the process. Finally, we produce a final answer at the end, which is used to evaluate our performance on the problem.

所以，在右侧的这个例子中，我们看到一个用红色标出的问题。接着，我们在下方用绿色生成了四个思维链（chain of thought）步骤。这些步骤中的每一个都会计算出过程中的一些中间项。最后，我们得出了一个最终答案，这个答案将用于评估我们在这个问题上的表现。

In the same blog post, OpenAI highlights this use of chain of thought. They say, "O1 learns to hone its chain of thought and refine the strategies it uses. It learns to recognize and correct its mistakes. It learns to break down tricky steps into simpler ones. It learns to try a different approach when the current one isn't working." It's hard to pull too much signal out of this sentence, but it really highlights that chain of thought is where the action is happening. Unlike other systems that build in complex search as part of their test time, this model is simply utilizing the chain of thought to do these steps as it goes.

在同一篇博客文章中，OpenAI 强调了思维链的这种用法。他们表示，「O1 学会磨练它的思维链，并完善它使用的策略。它学会识别并纠正自身的错误。它学会将棘手的步骤分解成更简单的步骤。当当前方法不起作用时，它学会尝试不同的方法。」尽管很难从这句话中获取太多有效信息，但它确实强调了思维链才是真正发挥作用的关键。与其他在测试时就预设了复杂搜索机制的系统不同，该模型只是在执行这些步骤时，简单地利用思维链来逐步完成。

In their blog post, OpenAI additionally included some examples of the chain of thought for the system. You're not actually able to see this chain of thought in the model they released, but we can look at some of the chains they provided. First off, we can see the chain of thought for our programming problem. Just to note again, this is something the model itself produced in the process of solving the problem. What we can see is that the model has produced an outline of all the steps it would like to produce. That line is numbered and includes complex sub-steps. If you read the rest of the chain of thought, you can see that it's following this outline in the process of producing its answer.

在他们的博客文章中，OpenAI 还附带了一些系统思维链的例子。虽然我们无法在他们发布的模型中直接看到这些思维链，但我们可以研究他们提供的一些示例。首先，我们来看看编程问题的思维链。需要再次强调的是，这是模型在解决问题过程中自主生成的。我们可以看到，模型已经为它希望执行的所有步骤生成了一个大纲。这个大纲有编号，并包含了复杂的子步骤。如果你继续阅读思维链的其余部分，会发现模型在生成答案的过程中，正是在遵循这个大纲。

In another example, there's a form of rudimentary planning. We can see that the system is aware of the time constraints it needs to answer the problem. It also is able to stop and propose different options and choose which of these it would like to follow. While this is all in English, it's using cues like "first" or "option one" in order to specify the intermediate steps.

在另一个例子中，系统展现出一种初步的规划能力。我们可以看到，系统知道解决问题存在时间限制。它还能暂停并提出不同的选项，然后选择它希望采纳的方案。尽管这些交互都是用英文进行的，但系统会利用「first」或「option one」之类的提示来明确中间步骤。

Another ability that we see in these chains is forms of backtracking. So in this example, for a math problem, it describes some intermediate term that it might need to compute. It then stops in the middle and says, "Well, actually, this may not help us directly." This allows the model to go back and determine that it might want to say something different. Again, this looks a bit like search, but it's not actually being performed with traditional search. It's simply the model talking to itself in order to determine the answer.

我们还在这些「思维链」中看到一种能力，那就是回溯的形式。例如，在处理数学问题时，它可能会描述一些它可能需要计算的中间项。接着，它会在中间停下来，并说：「嗯，实际上，这可能不会直接帮助我们。」这使得模型能够返回并重新评估，从而决定它可能需要采取不同的思考路径。这看起来有点像搜索，但实际上它并非通过传统的搜索算法执行的。这仅仅是模型在进行内部的「自我对话」，以最终确定答案。

### 03

A final ability we see is something like self-evaluation. Here we see it say, "Let's analyze each option." It then specifies the options it might want to consider, and it asks itself, "Is that a good explanation?" The answer is a bit informal. It says, "Hmm," and then goes on to the next option itself. But again, this is an ability that can be used by the model in order to explore different possibilities and determine which ones might make sense.

我们看到的最后一个能力是类似自我评估的能力。在这里，我们看到它会说：「让我们分析每个选项。」然后它会指定它可能想要考虑的选项，并且它会自问：「这是一个好的解释吗？」它的回答有些随意。它说：「嗯，」然后它会继续分析下一个选项。但同样，这是一种模型可以用来探索不同可能性并确定哪些可能合理的能力。

So in summary, Chain of Thought here is providing our method of test time scaling. While the actual words in the Chain of Thought look like search and planning in a classical sense, this is not actually being run at test time for the model. How does it learn to do this? Well, this is the big mystery. They claim that reinforcement learning is needed to induce this behavior. The rest of the talk, I want to explore how this might actually come about and look at some of the papers in the literature which talk about how you can get models to learn to do something like this such that you can scale their test time compute.

总而言之，这里的思维链（Chain of Thought）为我们提供了一种在推理时进行扩展的方法。虽然思维链中的具体表述看起来像是经典意义上的搜索和规划，但模型在实际推理时并没有真正执行这些操作。那么，它是如何学会这样做的呢？嗯，这仍然是个巨大的谜团。研究人员声称需要强化学习才能促使模型展现出这种行为。在本次演讲的剩余部分，我将深入探讨这究竟是如何实现的，并回顾一些文献中的论文，它们讨论了如何让模型学会执行类似的操作，从而在推理时提升它们的计算能力。

To get there though, we're going to need some technical background. So for this section, we're just going to focus on formalizing this idea of chain of thought. We're not going to do any learning, but simply talk about what it means to start from a question, go through say four or five steps of intermediate reasoning, and then come up with an answer. Formally, we'll assume our problem specification is called x. This is just the question being asked that we need to solve. Our final solution will be called y. This will represent, say, the conclusion or answer to our math problem. In between, we'll look to produce a series of steps z1 through zt. These are not individual words, but instead full steps on the way to produce our final answer. We'll abstract a bit away from the fact that this is a language model, and just think about it producing steps along in this chain. The final goal at the bottom of this slide is to produce a distribution over answers y conditioned on our input x. This distribution is defined by taking an expectation over these latent chain of thought steps z.

不过，要实现这一目标，我们还需要一些技术背景知识。所以，在本节中，我们将重点把思维链（chain of thought）这个概念形式化。我们不会进行任何学习，只是简单地讨论一下，从一个问题出发，经过大约四五个中间推理步骤，最终得出答案的意义。

形式上，我们将假设问题规范（problem specification）称为 x。这只是我们需要解决的待提问问题。我们的最终解决方案将称为 y。它将代表，比如说，我们数学问题的结论或答案。在此过程中，我们将生成一系列步骤，从 z1 到 zt。这些不是单个的词语，而是得出最终答案的完整步骤。我们将暂时抛开这是一个大语言模型（Large Language Model）的事实，只考虑它沿着这条链生成步骤。本节的最终目标是生成一个基于输入 x 的答案 y 的分布。这个分布是通过对这些潜在的思维链步骤 z 取期望来定义的。

As a warm-up, let's consider how standard chain of thought is done. We can't actually compute the expectation over all possible intermediate steps, so instead we run ancestral sampling. This is a fancy term that just means let the language model generate until it produces an answer.

作为开胃菜，让我们先来看看标准的「思维链」推理是怎么一回事。我们实际上无法计算所有可能中间步骤的「期望值」（你可以理解为所有可能性平均下来会怎样），所以我们转而采用「祖先采样」（ancestral sampling）的方法。这听起来可能有点复杂，但它其实就是指让大语言模型（Large Language Model）不断地生成内容，直到它给出一个最终答案为止。

Specifically, we'll sample 't' steps, represented by the green dots in the illustration, until we reach an answer 'y', represented by the dot on the right. The amount of test time compute applied here can be thought of as 't', where that represents each of the intermediate steps on the way to our answer. In general, I use these graphs on the right to demonstrate how the chain of thought is being used in these processes.

具体来说，我们会采样「t」个步骤（在插图中用绿点表示），直到我们得到最终答案「y」（用右侧的点表示）。这里所说的测试时间计算量，可以理解为「t」，它代表了通向答案过程中的每一个中间步骤。总而言之，我用右侧的这些图来演示思维链（chain of thought）在这些过程中是如何被运用的。

Many papers have noted that there's a way to get better answers to these problems. Instead of taking a single chain of thought and using it to produce the answer, we can sample 'n' chains of thought. Once we have these 'n' different chains of thought, we can take a majority vote to determine the majority answer. In this diagram, each of these chains of thought is sampled independently, and then we perform some sort of normalization. The answers that are most common are the ones we decide. This provides a strong baseline and a way to utilize more test time compute to slightly improve our answers. You can obviously do this to a large extent, but people have found that it doesn't lead to some of the amazing results that we're seeing in the 01 blog post.

许多论文已经指出，有一种方法可以更好地解决这些问题。我们不必仅仅依靠单一的思维链来得出答案，而是可以对「n」个思维链进行抽样。一旦我们有了这「n」个不同的思维链，我们就可以通过多数投票来确定最终答案。在此图中，这些思维链中的每一个都是独立采样的，然后我们进行某种标准化处理。我们选择的便是那些最常出现的答案。这提供了一个强大的基线，也是一种通过增加测试计算量来略微提升答案准确性的方法。显然，你可以在很大程度上应用这种方法，但人们发现它并未产生我们在 01 博客文章中看到的一些惊人结果。

### 04

The second piece of machinery we need is a verifier. Explicitly, we'll assume that we have an automatic verifier, but we only have it at training time. We'll define this automatic verifier as taking some answer 'y' and telling us if it is wrong or right. This verifier might be, say, regular expressions to check that we've solved a math problem, or it might be something more complex like full-on unit tests for code. Again, just to make it clear, we don't have this at test time, but we are going to utilize it as a way to provide training signal for us to produce a better model. Throughout this talk, I'm going to assume that we have an automatic verifier. This is a common assumption in much of the research, and I think it's a reasonable assumption for solving these problems.

我们需要第二件工具是一个验证器。具体来说，我们假设有一个自动验证器，但这个验证器只在训练阶段可用。我们将这个自动验证器定义为：接收一个答案「y」，然后告诉我们它是错的还是对的。这个验证器可能是一些正则表达式，用于检查我们是否解决了某个数学问题；也可能是一些更复杂的东西，比如针对代码的完整单元测试。再次强调，在测试阶段我们没有这个验证器，但我们会利用它来提供训练信号，从而帮助我们训练出更好的模型。在本次演讲中，我将一直假设我们拥有一个自动验证器。这是许多研究中的一个常见假设，我认为对于解决这类问题来说，这是一个合理的假设。

That being said, it's not clear whether OpenAI is actually utilizing automatic verifiers or whether they're using learned verifiers. In some of their papers, they explicitly try to learn verifiers for some technical problems. Their argument is that this can produce more general-purpose models, and it's a way for them to utilize their large annotation facilities in order to improve their models. In the case of learned verifiers, there are some interesting research challenges. For instance, one challenge is that with a learned verifier, if the generator produces, say, crazy solutions, sometimes the learned verifier gets confused and accepts them.

尽管如此，目前还不清楚 OpenAI 究竟是使用了自动化验证器（automatic verifiers），还是使用了学习型验证器（learned verifiers）。在他们的一些论文中，OpenAI 明确尝试针对某些技术问题训练验证器。他们认为，这样做可以开发出更通用的模型，并且能够充分利用其庞大的数据标注团队来提升模型的性能。对于学习型验证器，其中存在一些有趣的研究挑战。例如，一个挑战在于，如果生成器（generator）产生一些不合理或意想不到的解决方案时，学习型验证器有时会因为「困惑」而错误地接受这些方案。

In this graph on the right, they show that for a math problem, the model will continue getting better, but then it will plateau and even get worse as they take more samples. They discuss how this is a challenge with a learned verifier, and I have to assume they've collected a lot of data and thought about this problem a lot more in recent years. However, since we're poor both in GPUs and in data annotations, we'll focus instead more on the automatic verifier situation.

右侧图表显示，针对数学问题，模型的表现会持续提升，但之后会达到一个瓶颈，甚至在收集更多样本后反而会变差。研究人员讨论到，这是学习型验证器（learned verifier）所面临的一个难题。我们可以推测，他们近年来为此收集了大量数据，并深入研究了这个问题。然而，考虑到我们在图形处理器（GPU）和数据标注方面的资源有限，我们将把重点更多地放在自动验证器（automatic verifier）方案上。

Once you have a verifier, there are many new things you can do. One idea is to do rejection sampling. This is a way of getting some distribution of chain of thoughts that yield correct answers. We're going to do this just by sampling again 'n' different chains and simply keeping the ones that are verified. In my notation on the right, on the top picture, we see all the different samples that we picked, and then on the bottom picture we see the chain of thoughts that led to correctly verified solutions. I'll use this little square box on the right to indicate which solutions were successfully verified.

一旦有了一个验证器，你就可以做很多新奇的事情。其中一个想法是进行拒绝采样。这是一种获取那些能得出正确答案的思维链分布的方法。具体做法是，我们再次采样「n」条不同的思维链，然后只保留那些通过验证的链。看我右边的图示，在上面那张图中，我们能看到所有我们选取的不同样本；而在下面那张图中，我们看到的是那些成功导向正确验证结果的思维链。我将用右下角的小方框来表示哪些解决方案已经成功通过验证。

This process may be extremely compute intensive, but it gives us a way to get some of the good chain of thoughts that lead to the verified solutions. We're going to assume for now that you can plausibly get some solutions using this procedure, although it's not obvious for hard problems that this will ever yield a correct answer. The other thing we can do is to apply the same process, but starting from an intermediate step in our chain. So in this example here, we've run three steps of chain of thought, and from there we'll do what's called a rollout. This rollout is the same as rejection sampling, but it just starts from the intermediate place in our process. This can be used to tell us how good we are doing from any step in the chain. It's not guaranteed to always work for good problems or bad problems, but at least gives us a direction in which to move in our system.

这个过程可能会消耗巨大的计算资源，但它为我们提供了一种途径，能够得到高质量的思维链，从而推导出经过验证的解决方案。我们目前可以假设，通过这个程序有望获得一些解决方案，尽管对于那些困难的问题，这种方法是否真的能得出正确答案还很难说。我们还可以做另一件事，就是应用相同的过程，但这次是从我们思维链中的某个中间步骤开始。举个例子，我们已经运行了思维链的三个步骤，然后我们会从这里开始进行所谓的「rollout」操作。这种「rollout」与拒绝采样（rejection sampling）本质上是一样的，只不过它不是从头开始，而是从我们整个过程的中间某个位置开始。通过这种方式，我们可以评估在思维链的任何一个步骤中，我们进展得如何。虽然它不能保证对所有问题都有效，无论是简单问题还是难题，但至少能为我们的系统指明一个前进的方向。

Given this formal background, we now come to our main goal. We would like to learn a model that can take into account these latent chain of thoughts. We can write this down explicitly as a maximum likelihood problem, where we're interested in learning the model that performs as well as it can at producing verified solutions.

有了这些正式背景，我们现在转向主要目标：希望训练一个能将这些潜在的思维链纳入考量的模型。我们可以将此明确表述为一个最大似然问题，旨在学习一个能尽可能好地生成经过验证解决方案的模型。

We can then think about this as marginalizing out over all possible chains of thoughts that lead to the correct answer. Of course, this problem is combinatorially extremely difficult. We can't, with even nearly infinite compute, really do this marginalization. There are many different possible steps at each point, and when we start talking about chains of thousands of steps long, this becomes extremely intractable. So figuring out how to actually do this is the fun part of the problem.

我们可以把这看作是对所有可能导向正确答案的思维链进行边缘化处理。当然，这个问题的组合复杂性（combinatorial complexity）极高。即使我们拥有近乎无限的计算资源，也无法真正实现这种边缘化操作。因为在每一步都有许多不同的可能选择，当谈到长达数千步的推理链时，这会变得极其难以处理。因此，弄清楚如何真正实现这一点，才是这个问题的趣味所在。

Before we get into some of the methods, I want to make a quick note about reinforcement learning. As I noted earlier, I find reinforcement learning to be quite a challenging area. There are many different conflicting definitions about how these systems work and how they're actually trained. I think many of the details are actually specific choices that individual companies needed to make in their system design. Many of these things often look quite different in open source than they might do within a kind of big reinforcement learning lab.

在我们深入探讨一些方法之前，我想简单提一下强化学习。正如我前面提到的，我发现强化学习是一个相当具有挑战性的领域。关于这些系统如何运作以及如何进行实际训练，存在许多相互冲突的不同定义。我认为许多细节实际上是各个公司在系统设计中必须做出的具体选择。而且，这些东西在开源社区中看起来的样子，通常与在大型强化学习实验室里可能会大不相同。

With that in mind, I think these choices are very important, but for the sake of this talk, I'm going to leave most of them out. There are particular choices about how to batch things, how to do it on policy or off policy, how to use KL constraints to make sure your system doesn't go off the rails. For most of the algorithms I'm going to talk about, though, you can implement them either in a simple way or in the more complex or scalable method. It's not that these details aren't important. When I talk to experts, they say these are some of the most important things to actually learn and make these systems work. It's just that I'm not the right person to tell you about them, and I think there are interesting ideas here without going into these systems in detail.

考虑到这一点，我认为这些选择非常重要，但为了本次演讲，我将省略大部分内容。这里面有很多具体的选择，比如如何批量处理数据，如何采用策略内（on policy）或策略外（off policy）的方式，以及如何使用 KL 约束来确保你的系统不会「脱轨」。不过，对于我将要讨论的大多数算法，你可以用简单的方法实现它们，也可以用更复杂或可扩展的方法实现。这并不是说这些细节不重要。当我与专家交流时，他们告诉我，这些是真正学习并让这些系统正常运行的一些最重要的事情。只是我不是向大家讲解这些细节的最佳人选，而且我认为即使不深入探讨这些系统的复杂细节，这里也依然有很多有趣的理念。

Finally, one last quote from OpenAI that I found really interesting. They said that when training a model for reasoning, one thing that immediately jumps to mind is to have humans write out their thought process and train on that. When we saw that if you train the model using RL to generate and hone its own chain of thoughts, it can do even better than having humans write chain of thoughts for it. That was the aha moment that you could really scale this. I think this quote is pretty amazing. I imagine it was quite shocking for the first time to see the model reason through a problem and get it correct. I don't know, maybe I'm a sucker.

最后，我想引用 OpenAI 的另一句话，我觉得非常有趣。他们提到，在训练一个模型进行推理时，一个很自然的想法是让人类写出他们的思维过程，然后用这些过程来训练模型。但当我们发现，如果使用强化学习（RL）训练模型去生成并完善它自己的思维链（chain of thoughts），它的表现甚至比让人类手写思维链进行训练的模型更好。那一刻，大家才意识到这种方法真的可以大规模应用。我认为这句话非常了不起。我能想象，第一次看到模型自己推导问题并得出正确答案时，那一定相当令人震惊。我不知道，也许我只是容易被这些新奇事物打动。

Okay, with that background, we can actually get to the suspects for what might be going on here. So I narrowed this down to four different suspects: guess and check, process rewards, search or alpha zero, and learning to correct. These aren't formally different areas, but when reading this literature, I did find it a bit overwhelming. There are many different papers that think about these problems, and, well, everyone's kind of convinced their method is what's really going on. That being said, I found these four to be a useful outline for helping me think about this problem.

好的，有了这些背景知识，我们就可以开始探讨可能导致这种现象出现的几种「可能性」了。我把这些可能性归纳为四种不同的情况：试错法、奖励处理、搜索（或 Alpha Zero 算法），以及学习纠正。这些并不是严格意义上截然不同的领域，但当我阅读相关文献时，确实感到有些不知所措。有许多不同的论文都在探讨这些问题，而且，每个人似乎都坚信自己的方法才是最核心的。尽管如此，我发现这四种分类方法为我提供了一个有用的框架，帮助我思考这个问题。

Suspect 1 is the simplest. Three steps: we sample N chain of thoughts, we check which ones were successful, and then we train on the good ones. If we think about it in terms of our picture, we will independently sample. Some of the chains will go wildly off, and some will reach the solutions. The solution ones are the ones we would like, and so we can train them into our language model.

方案 1 是最简单的，它包含三个步骤：我们抽取 N 个思维链（chain of thoughts），检查其中哪些是成功的，然后用这些成功的思维链来训练模型。如果用我们的图示来理解，我们会独立地进行抽取。有些思维链会完全偏离，而有些则会找到解决方案。这些成功的解决方案正是我们想要的，因此我们可以将它们训练到我们的大语言模型（Large Language Model）中。

If you're like me, you might find it helpful to formalize what's going on here. We can think about this as a form of rejection sampling expectation maximization. EM is a very traditional algorithm in machine learning and it's been applied to these sort of reinforcement learning algorithms for decades. We can think of the expectation step as running rejection sampling as we saw earlier in the, and we can think of the maximization step as fitting our language models to the samples that fit with our posterior. The more we run this expectation step, the closer to the true expectations we've calculated, and the better our end step will in getting to the answer itself. Traditionally, EM is done in a batched offline process, but there are versions that are online or that can work with any other form of reinforcement learning.

如果你和我一样，你可能会觉得把这里发生的事情用更规范的方式表达出来会很有帮助。我们可以把这看作是拒绝采样期望最大化（rejection sampling expectation maximization）的一种形式。期望最大化（EM）是机器学习中一个非常经典的算法，几十年来一直被应用于这类强化学习算法。我们可以把期望步骤看作是运行我们之前介绍过的拒绝采样，而最大化步骤则是将我们的语言模型拟合到那些符合我们后验分布的样本。我们运行期望步骤的次数越多，我们计算出的期望就越接近真实值，我们的最终步骤也就越能更好地找到答案。传统上，EM 是在批处理的离线过程中完成的，但也有在线版本，或者可以与任何其他形式的强化学习配合使用。

Given the simplicity of this method, it's been discovered and noted to work many times. In NLP, this works as a form of self-training. This is a method that was described in 1995 and later used to produce state-of-the-art syntactic parsers. This method, of course, has different names in different areas. OpenAI refers to it as best-of-N training. A popular recent variant is called STAR or self-taught reasoning. My formalization is from the paper REST-EM. In some sense, the name here actually doesn't really matter too much. I mostly list them all so you don't get intimidated or think more is going on here than actually is. And high level, all these papers come to a similar conclusion.

这种方法因其简单性，已被人们发现并多次指出其有效性。在自然语言处理（NLP）领域，它表现为一种自训练的形式。这项技术早在 1995 年就被提出，后来被用于构建最先进的句法分析器。当然，这种方法在不同领域有不同的名称。OpenAI 将其称为「best-of-N」训练。最近一个流行的变体是「STAR」或「自学推理」。我这里采用的形式化方法则出自论文 REST-EM [20]。从某种意义上说，这里的具体名称其实并不那么重要。我之所以列出所有这些名字，主要是为了让你不会感到困惑，也不会误以为其中包含比实际更复杂的内容。总的来说，所有这些研究论文都得出了相似的结论。

This method is simple, but it works, and it works pretty well. You can get relatively consistent improvements, particularly in lower samples, across many different problems. If anything, this should be a required baseline in most papers. Of course, the assumption here is that we have access to the verifier. It seems hard to actually scale the test-time compute if we only have this during training.

这种方法虽然简单，但却非常有效，而且表现相当出色。它能让你在各种问题上获得相对稳定的性能提升，尤其是在样本量较少的情况下。如果非要说点什么，我觉得这应该成为大多数学术论文中必须设定的基准。当然，这里的前提是我们能够用到验证器。如果验证器只能在训练阶段使用，那么在测试阶段想要扩展计算能力就会显得有些困难。

Of course, we can try to use what we've produced to also train the verifier. Since we have a lot of samples from rejection sampling, we can further try to train some sort of learned verifier that we can keep around at test time. This idea, which is often referred to as amortization, basically using a learned model to represent some sort of complex system. We can create our own sort of learned verifier at test time. This could then be used as part of chain of thought or for some sort of test-time rejection sampling.

当然，我们可以尝试用我们生成的结果来训练一个验证器。由于我们通过拒绝采样获得了大量样本，我们可以进一步训练出一种学习型验证器，在测试阶段可以保留它。这个想法通常被称为「摊销（amortization）」，其核心思想是利用一个学习模型来表示某种复杂的系统。我们可以在测试时创建属于我们自己的学习型验证器。然后，这个验证器就可以作为思维链（chain of thought）的一部分，或者用于某种测试阶段的拒绝采样。

So, is this just a guess-and-check RL system? Well, there's some signs it might be. One thing that's neat is that this approach is extremely simple and scalable. One thing OpenAI has done in the past is just build larger, more powerful versions of things people thought worked reasonably well. We also have seen positive results with this, and potentially with huge amounts of data collection for the verifier, you could get a system like this to work really, really well.

那么，这究竟是不是一个试错型强化学习（RL）系统呢？嗯，确实有一些迹象表明可能是这样。这种方法一个很棒的优点是它极其简单且易于扩展。OpenAI 过去常常采取的一个策略就是，对于那些被认为表现不错的系统，他们会直接构建更大、更强的版本。我们也在这种方法上看到了积极的成效，而且，如果能为验证器收集到海量数据，或许就能让这类系统发挥出极其出色的性能。

What we're missing, though, is that there's no evidence that simply sampling will produce some of the chain of thoughts that we saw earlier. This seems like a big change to just have this happen automatically from our system. In addition, the assumption here is that if we do enough rejection sampling, we'll get some good chains. But for some of the harder problems, this seems really unlikely. This seems computationally efficient or even impossible. So, let's build a bit more structure into these systems.

然而，我们所忽略的是，没有证据表明仅仅通过简单的采样就能产生我们之前看到的那种思维链。让系统自动地实现这一点，似乎是一个巨大的转变。此外，这里还有一个假设：如果我们进行足够的拒绝采样，就能得到一些好的思维链。但对于某些更棘手的问题，这看起来不太可能实现。在计算上，这似乎是低效的，甚至是无法实现的。因此，我们需要在这些系统中构建更精密的结构。

This next section is on process rewards. Suspect 2: During chain of thought sampling, we'll have some guidance that we'll both use to learn and to improve our trajectories. We then run the same process where we check if our final or partial versions are successful and train on the good ones. The term process rewards comes from two papers, one from Google and one from OpenAI. In these papers, they learn an early verification model, which they call a PRM or process reward model. They show that learning this intermediate model can improve in rejection sampling compared to a learned model that gets the full solution. The graph on the right compares the learned intermediate model both to majority voting and to a model learned only on full solutions. Note this graph is not making any claim about the learning process, just that we're able to successfully complete more chain of thoughts by utilizing an intermediate learned verification function.

这部分内容是关于过程奖励的。参与者 2：在思维链采样期间，我们会得到一些指导，这些指导既能帮助我们学习，也能改进我们的决策路径。然后我们运行相同的过程，检查我们的最终版本或部分版本是否成功，并对成功的版本进行训练。术语「过程奖励（process rewards）」来源于两篇论文，一篇来自 Google，另一篇来自 OpenAI。在这些论文中，他们学习了一个早期验证模型，他们称之为 PRM 或过程奖励模型（process reward model）。他们表明，与学习完整解决方案的模型相比，学习这个中间模型可以改善拒绝采样中的表现。右侧的图表将学习到的中间模型与多数投票和仅在完整解决方案上学习的模型进行了比较。请注意，此图表并未对学习过程本身做出任何声明，仅仅是表明我们能够通过利用中间学习到的验证函数，成功完成更多的思维链任务。

There are several ways for acquiring this process reward model. One might simply be to sample trajectories from your model and utilize human annotators to label these. Another approach, which is becoming more common in the literature, is to take partial chain of thoughts from your model and then perform rollouts. These rollouts will tell us how good the chain of thought is at a given time. As we discussed earlier, we can then utilize these rollouts to train a learned process reward model. We'll call this RSI. This will give us a sense of how good we are doing and can additionally be used at test time.

有几种方法可以构建这个过程奖励模型。其中一种简单的方法是，从你的模型中抽样出轨迹（trajectories），然后请人工标注者对这些轨迹进行标记。另一种在学术文献中越来越常见的方法是，从你的模型中提取部分思维链（chain of thoughts），然后执行推演（rollouts）。这些推演会告诉我们，在给定时间点，思维链的表现如何。正如我们之前讨论过的，我们可以利用这些推演来训练一个学习到的过程奖励模型，我们将其称为 RSI。RSI 将帮助我们评估模型的表现，并且还可以在测试阶段使用。

There are many ways we might choose to parameterize this learned process reward model. One interesting idea is to learn it as a large language model. The idea here is that the actual process reward model that's checking how well we're doing can itself use chain of thought. It might try to reason about individual steps and utilize them to decide upon the answer. What's important about this step is this is an idea that merges the generator and the verifier. You can have a single model that is both trying to do reasoning and also trying to verify this reasoning. This is an idea that has begun to be explored recently in the literature, where several approaches build these generative verifiers. On medium-scale problems, we can see that this learned process reward style seems to work. In this paper, known as Math Shepherd, they train a model utilizing rollouts. They can show that in this model they're both able to find better solutions with their learned intermediate guide and they're also able to learn a final model that's better at math. This approach also brings the full story into a bit more focus. If we're going to use a verifier that is also using chain of thought and we're going to merge that into a single stream, we can imagine alternating between generation and verification and using that to improve our test-time solution.

我们可以用多种方式来给这种学习到的过程奖励模型（process reward model）设定参数。其中一个有趣的想法是将其作为一个大语言模型（Large Language Model）来训练。这样做的核心理念是，负责评估我们表现好坏的过程奖励模型本身，也可以运用「思维链（chain of thought）」的能力。它可能会尝试对每一步进行推理，并利用这些推理来得出最终的答案。这个方法的关键在于它将生成器（generator）和验证器（verifier）融合在了一起。你可以拥有一个单一的模型，它既负责进行推理，也负责验证这些推理是否正确。这个想法最近在学术界得到了探索，一些研究方法正在构建这种「生成式验证器（generative verifiers）」。在中等规模的问题上，这种学习到的过程奖励方法似乎确实有效。例如，在一篇名为 Math Shepherd 的论文中，研究人员通过使用「rollouts」来训练一个模型。他们展示了这个模型不仅能够利用其学习到的中间指南找到更好的解决方案，而且还能训练出一个在数学方面表现更优秀的最终模型。这种方法也让整个图景变得更加清晰：如果我们使用一个同样运用思维链的验证器，并将其整合到一个单一的流程中，我们就可以想象在生成和验证之间交替进行，并利用这种交替来优化我们在测试阶段的解决方案。

For example, if we look back at one of the chain of thoughts I mentioned earlier, we see statements like, "Is that a good explanation?" While traditionally we would think of this as part of the generator, this might be part of a verifier that's been merged into the same model. It can move back and forth between generation and verification within a single language model.

例如，回顾我之前提到的一个思维链（chain of thought），我们会看到这样的陈述：「这是一个好的解释吗？」虽然传统上人们会认为这是生成器的一部分，但这实际上可能是已经整合到同一个模型中的验证器（verifier）的一部分。这意味着它可以在同一个大语言模型中，在生成内容和验证内容之间来回切换。

So is this a one? Well, there's some evidence that these intermediate guides are effective. It also removes the challenge of just having a single learned verifier. On the negative side, we haven't really seen anything yet that explains some of the advanced planning that we've seen this model do, and we don't really know how to fully do this combination of generator and process reward model into a single chain of thought. It's a compelling idea, but there are a lot of details still remaining.

那么，这是否就是答案呢？嗯，有证据表明这些中间指导方案是有效的。这也能避免只依赖一个单一的学习验证器所带来的挑战。另一方面，我们还没有看到任何能够解释该模型所展现出的一些高级规划能力的机制，而且我们也不清楚如何将生成器和过程奖励模型（process reward model）完全整合到一个单一的思维链（chain of thought）中。这是一个很有吸引力的想法，但仍有许多细节问题需要解决。

If I had to guess, I would say I personally think this is probably closest to what we might expect O1 to be. It fits with the research papers that OpenAI is publishing and some of the rumors about the simplicity of the system itself. That being said, my confidence is quite low, and a lot of people I talk to think it's something quite a bit more advanced.

如果非要我猜，我个人觉得这可能最接近我们对 O1 的预期。这与 OpenAI 正在发表的研究论文以及关于该系统本身可能很简单的传闻相吻合。话虽如此，我的信心并不高，而且我与许多人交流后发现，他们认为 O1 远比这更先进。

So let's look at some more search-based solutions. So in particular, let's remind ourselves how AlphaZero works. This was a very important paper in the history of deep learning and RL. In this paper, which was a follow-up to AlphaGo, they demonstrate that a system completely taught with self-play could achieve expert-level performance in a very hard task.

那么，我们再来看看一些基于搜索的解决方案。特别是，让我们回顾一下 AlphaZero 是如何工作的。这篇论文在深度学习和强化学习（RL）的发展史上非常重要，它也是 AlphaGo 的后续研究。在这项研究中，研究人员展示了一个完全通过自我对弈（self-play）训练的系统，如何在极其困难的任务中达到专家级别的性能。

At a casual level, the way the system works is it plays games of Go using a complex search algorithm, then trains a neural network based on the trajectories of this system. It then uses that neural network to again play some more games and iterates on this process. This is the canonical example of success stories from very simple RL-based algorithms and demonstrates scaling without the need for extensive expert demonstrations.

通俗地说，这个系统的工作原理是，它会使用复杂的搜索算法下围棋，然后根据下棋的轨迹来训练一个神经网络。接着，它再用这个神经网络去下更多的棋局，并不断重复这个过程。这是基于非常简单的强化学习（RL）算法获得成功的典型案例，它证明了即便没有大量的专家演示，系统也能实现规模化应用。

There are several reasons this system is relevant to the discussion, but one of the more recent ones is this work on AlphaProof. We don't have a lot of details behind how AlphaProof works, just that it did extremely well at a very hard math competition, and a blog post that says, "When presented with a problem, AlphaProof generates solution candidates and then proves or disproves them by searching over possible proof steps in Lean, which is a proof assistant." Each proof that was found and verified is used to reinforce AlphaProof's language model, enhancing its ability to solve subsequent more challenging problems.

这个系统与我们的讨论息息相关，原因有几点，其中一个最新进展就是 AlphaProof 这项工作。我们对 AlphaProof 具体如何运作的细节了解不多，只知道它在一项难度极高的数学竞赛中表现优异。一篇博客文章对此有所提及：「当面对一个问题时，AlphaProof 会生成潜在的解决方案，然后通过在 Lean （一个证明助手）中搜索可能的证明步骤来证明或反驳这些方案。」每一个经发现并验证的证明都会被用来强化 AlphaProof 的语言模型，从而提升它解决后续更具挑战性问题的能力。

So if you squint, this does seem rather similar to some of the language we saw in OpenAI's blog. So how might this work? Well, we're going to assume there's going to be some self-play using some kind of guided search with exploration. We'll then label the final outcomes of these self-play games. We'll train a guide and generator and iterate.

所以，如果你仔细观察，这确实与我们在 OpenAI 博客中看到的一些说法非常相似。那么，这可能如何运作呢？嗯，我们可以设想会通过某种带有探索的引导式搜索（guided search with exploration）进行一些自我博弈（self-play）。然后，我们将记录这些自我博弈游戏的最终结果。接着，我们将训练一个引导器（guide）和一个生成器（generator），并不断迭代优化。

The terminology for this in the literature is known as expert iteration. It refers to this iterative process where an algorithm that combines a learned model plus a complex expert search. The goal is basically to distill the search process into the model. We do this by generating lots of samples, utilizing our reward model to improve upon them, and then labeling the good ones. We iterate on this process retraining both the generator as well as the guide model in order to do better on the next iteration.

在文献中，这种方法被称为专家迭代。它指的是一种迭代过程，其中算法将学习模型与复杂的专家搜索相结合。其核心目标是将复杂的搜索过程提炼并融入到模型中。我们通过生成大量样本，利用奖励模型对这些样本进行改进，然后标记出高质量的样本来达成这一目标。我们不断重复这一过程，重新训练生成器和指导模型，以便在下一次迭代中取得更好的表现。

A popular way to do this with language modeling is to use a search algorithm known as BeamSearch and then to utilize a guide that will look very similar to our process reward model. Here, our guide will tell us how well we're doing by looking at our partial chain of thought so far. Given this guide, we can then perform Beam search.

在语言建模中，一种常用的方法是运用一种名为 BeamSearch 的搜索算法，并结合一个与我们奖励模型运作方式非常相似的「指南」。这个指南会通过审视我们目前生成的部分思维链，来评估我们做得好不好。有了这个评估指南，我们就可以执行 Beam 搜索了。

The way beam search works is that at every step of the process, we expand out to all possible next chain of thoughts, and then we just keep the top four based on how well they're doing from our guide. This will keep around four different possible solutions, each of the same length, based on how close they are to producing a good final answer.

Beam search 的工作原理是，在算法的每一步，我们都会探索所有可能的后续思考路径，然后根据它们在指导评估中的表现，只保留排名前四的路径。这样，算法会同时维护大约四个长度相同的潜在解决方案，这些方案会根据它们产生良好最终答案的接近程度来排序。

Of course, there's a lot of details here I'm not specifying. We have to determine how to expand to new possible chain of thoughts, as well as producing somewhat different chain of thoughts that might likely give us a different path. We also have to determine how to weigh the guide versus what the language model thinks is the next path. But at a high level, you can see how this expertise can then be trained into the model.

当然，这里还有很多我没有具体阐述的细节。我们必须弄清楚如何探索更多可能的思维链，以及如何生成一些可能带来不同解决方案的独特思维链。此外，我们还需要确定如何平衡既定指导原则与大语言模型自身判断的下一步方向。但从宏观层面来看，你就能明白这种专业知识是如何被训练到模型中的了。

Instead of a guide, we might also consider using rollouts directly. In this example here, we are running BeamSearch at each step and using rollouts at training time in order to tell us how well we're doing. Here's our first step, second step, third step, and here is our fourth step. In systems like AlphaGo, these rollouts are combined with a learned guide function.

我们也可以考虑直接使用蒙特卡洛模拟（rollouts），而不是仅仅将其作为指导。在这个例子中，我们每一步都运行 BeamSearch，并在训练时使用蒙特卡洛模拟来评估当前的表现。这里是我们的第一步、第二步、第三步，以及第四步。在像 AlphaGo 这样的系统中，这些蒙特卡洛模拟会与一个经过学习的指导函数结合使用。

Together, these give us a good sense of the problem, and we learn how much we can actually trust our learned guide function versus explicit rollouts. Remember, our goal at test time is to remove the rollouts entirely.

综合来看，这些实验让我们对问题有了清晰的认识，并且我们了解到，相比于明确的模拟推演（rollouts），我们学到的引导函数（guide function）实际上有多大的可信度。需要记住的是，我们在测试阶段的目标是完全取消这些模拟推演。

Several recent papers have experimented with using these forms of expert iteration in order to produce good reasoning systems. Again, we're working on somewhat more medium-scale math problems, but there is some preliminary evidence that there are significant benefits from doing this form of search. Specifically, we see large increases in accuracy compared with doing the naive guess-and-check system, here represented as star, that we saw earlier in the talk.

最近的几篇论文已经尝试使用这些形式的专家迭代，以构建出优秀的推理系统。值得注意的是，我们正在研究中等难度的数学问题，但已有初步证据表明，这种形式的搜索会带来显著的益处。具体来说，与我们之前在演讲中提到的、用星号表示的朴素试错系统相比，我们看到了准确性的大幅提高。

While beam search is a common approach for efficiently doing search with language models, systems like AlphaGo used much more complex forms of search for game playing. In particular, the famous search algorithm used in those papers is known as MCTS, Monte Carlo Tree Search. This is a complex algorithm that combines search with exploration.

集束搜索（beam search）是让语言模型高效执行搜索的常用方法，但像 AlphaGo 这样的系统在进行游戏对弈时，却采用了远比其复杂的搜索形式。其中，那些知名论文里使用的著名搜索算法就是蒙特卡洛树搜索（MCTS），这是一种将搜索与探索巧妙结合的复杂算法。

The way it works is that for a given math problem, we're going to start at the beginning. We're then going to walk down our tree until we hit a leaf node. When we get to that node, we'll expand five possible next steps. So in our case, that node will consist of a partial chain of thought, and the next five steps will be five other expansions of steps we could try next. We'll then pick one of those at random.

这种方法的工作原理是，对于一个特定的数学问题，我们从头开始。接着，我们会遍历我们的「思考树」，直到走到一个叶节点。当我们到达这个节点时，我们会生成五种可能的下一步方案。所以，在这个节点上，我们会有一个部分的思维链，而接下来的五步就是我们接下来可以尝试的另外五种步骤的扩展。然后，我们会从这五种方案中随机选择一个。

When we get to that step, we'll do a rollout of the next steps in the chain of thought. Depending on whether these were successful or not, we'll then update all of our parent nodes based on the fact that we ran that rollout, and also how well it did. We can continue this process, growing our tree and applying different rollouts. The key to the algorithm is that we are not simply just trying to reach the end as fast as possible, but trying to explore different parts of the tree.

当我们走到那一步时，我们会把思维链中的后续步骤展开。根据这些步骤的成功与否，我们会基于执行这些步骤的结果和表现来更新所有的父节点。我们可以继续这个过程，扩展我们的树并应用不同的展开策略。这个算法的关键在于，我们不只是简单地试图尽快达到终点，而是努力探索树的不同部分。

Let's look at a demo. So in this example here, we have run our selection process and gone down the yellow nodes of the tree. We then look at the bottom node, that chain of thought of three steps, and we expand it to three next possible steps. Here we can see the expansion, and the yellow node represents which of the expansions we pick to roll out. We then run our rollouts here. I'm showing eight independent rollouts, several of which reached the solution and several of which did not. Based on this rollout, we then update the node and all of its parents to tell them how well it did.

让我们来看一个演示。在这个例子中，我们已经运行了选择过程，并沿着树的黄色节点向下。然后我们查看底部节点，也就是那个由三个步骤组成的思维链（chain of thought），并将其扩展为接下来的三个可能步骤。在这里我们可以看到扩展后的情况，其中黄色节点代表我们选择哪个扩展来执行展开（rollout）。接着我们在这里运行展开。我展示了八个独立的展开，其中有几个成功找到了解决方案，也有几个未能成功。基于这些展开的结果，我们随后更新该节点及其所有父节点，以告知它们该节点表现如何。

Okay, now we start the process again. We now need to select which node to expand next. We've chosen a different set of nodes to select, and we've reached a different leaf. This selection process is based both on which nodes won and which nodes were not yet explored. We then expand this node, and we do another set of rollouts. Based on the success of these rollouts, we then update each of the parents.

好的，现在我们重新开始这个过程。接下来，我们需要选择下一个要「扩展」的节点。我们选择了一组不同的节点，并到达了一个不同的「叶子」节点。这个选择过程不仅考虑了哪些节点已经「获胜」，也考虑了哪些节点尚未被探索。随后，我们扩展这个节点，并进行另一组「模拟推演（rollouts）」。根据这些模拟推演的结果，我们接着更新每个父节点。

As mentioned earlier, the main benefit from this process is that when we do selection, we are basing that selection both on how well these nodes did and also how well they were explored. The benefit here is that we can explore many different possible chain of thoughts and try to find ones that we may not have explored in the past.

正如前面提到的，这个过程的主要优势在于，我们在做出选择时，既会考虑这些节点的表现，也会考虑它们被探索的程度。这样做的好处是，我们可以探索许多不同的潜在思维链（chain of thoughts），并尝试发现那些我们过去可能没有探索过的可能性。

So is there some type of search algorithm being explored in 01? Well, it fits with the history of major demonstrated results in RL and it's a particularly nice way of adding more training time into the system. Remember, we know that 01 is data efficient, but they may have used an incredible amount of compute in order to do training. Furthermore, given that the chain of thoughts that we actually are seeing from 01 look a little bit like search with properties like backtracking or high-level outlining, it's plausible that those came into the model through something like training time search.

那么，01 是否正在探索某种搜索算法呢？这与强化学习（RL）中已取得的重大成果的历史相符，并且是一种特别好的方式，可以为系统增加更多的训练时间。请记住，我们知道 01 在数据利用方面是高效的，但它们在训练过程中可能使用了惊人的计算资源。此外，考虑到我们从 01 实际观察到的思维链（chain of thoughts）在某种程度上类似于带有回溯（backtracking）或高层规划（high-level outlining）等特性的搜索，因此这些特性很可能是通过训练时间搜索（training time search）等方式融入模型中的。

However, there are some negatives to this process. It's much more complex algorithmically, and it's costly to maintain open states. Compared to the first two systems, it does seem much harder to scale. Additionally, we don't see anything about doing this sort of complex training tree search in any of the OpenAI release material. The other thing that's interesting is that there are a lot of papers kind of exploring MCTS for language modeling. But at least in the open research community, we haven't seen too many successes. It seems like simpler methods work a bit better for these problems.

然而，这种方法也并非没有缺点。它的算法要复杂得多，并且维护其内部的「开放状态」或搜索空间成本也很高。与之前提到的两种系统相比，这种方法似乎更难进行扩展。此外，我们注意到在 OpenAI 发布的所有资料中，都没有提及他们采用了这种复杂的训练树搜索技术。另一个有趣的现象是，尽管有很多论文都在探索将蒙特卡洛树搜索（MCTS）应用于语言建模，但至少在开放研究社区中，我们还没有看到太多成功的案例。对于这类问题，似乎更简单的方法反而效果更好。

Our final method is learning to correct. So to motivate these algorithms, I want to note some of the differences between game playing and language. In game playing, there is a set of fixed moves, and the main source of exploration is to just explore these alternative moves. In language, there are really a lot of possibilities. You can get around some of this by sampling or fixing the next possible steps you might take, but I think actually a lot of the exploration should be in this process itself.

我们提出的最后一种方法是「学习纠正」。在介绍这些算法的动机之前，我想先指出玩游戏和使用语言之间的一些区别。在玩游戏时，可选的动作是固定的，探索的主要方式就是尝试这些不同的动作。然而，在语言领域，可能性则要多得多。虽然我们可以通过采样或预设下一步可能采取的步骤来部分解决这种复杂性，但我认为实际上很多探索都应该发生在语言处理这个过程本身。

How do you determine different next chains of thought, and which ones will cause more exploration or backtracking? This motivates a series of methods for learning to correct. At a high level, we start with a failed chain of thought from our system. We then perform a search to find successful corrections of this failure. Based on this outcome, we train on the entire process, not just the correction, but the original as well.

如何确定不同的下一步思维链（chain of thought），以及哪些会导致更多的探索还是回溯呢？这促使我们研究了一系列学习纠正的方法。概括来说，我们从系统中一个失败的思维链开始。然后我们搜索并找到纠正这个失败的成功方法。基于这个结果，我们对整个过程进行训练，不仅包括纠正后的部分，也包括原始的（失败的）思维链。

A motivating example is work on self-correction. The idea here is to isolate pairs of chains of thought, let's call one Z prime and the other Z double prime. These chains of thought are similar, but one leads to a correct answer and the other does not. If we can isolate these two, we can train a model that improves upon Z prime to move more towards Z double prime. If we can do this at scale, we can hope to build this ability into the generator itself.

一个很有启发性的例子是关于自我纠正的研究。这里的核心思想是，我们可以找出一些「思维链对」，我们不妨称其中一条为 Z'，另一条为 Z''。这些思维链虽然相似，但其中一条能导向正确的答案，而另一条则不能。如果我们能将这样的思维链对分离出来，我们就可以训练一个模型，让它在 Z' 的基础上进行改进，从而更接近 Z''。如果这种方法能够大规模实现，我们就有望将这种自我纠正的能力直接整合到生成器本身。

This approach sounds simple, but it has many challenges in practice. One issue is that the model will often just collapse. If the first chain of thought was not very good, it will learn to ignore it and simply try to generate the second one directly. Another issue is that you have to be extremely careful about distribution shift. If you collect many examples, but they look different from what your model is actually generating, it might not self-correct in practice. It will learn about your examples, but not about the mistakes your model actually produces.

这种方法听起来简单，但在实际操作中却面临诸多挑战。其中一个问题是，模型经常会「跑偏」。如果最初的思维链不够理想，模型就会学着忽略它，转而直接尝试生成第二个结果。另一个问题是，我们必须对「分布偏移（distribution shift）」格外小心。如果你收集了大量示例，但它们与你的模型实际生成的内容大相径庭，那么模型在实际应用中可能就无法有效地自我修正。它只会学习你提供的示例，却无法纠正自己实际产生的错误。

One approach to get around this issue is to try to be as on-policy as possible. In this setting, we generate our Z prime and then take all possible continuations from Z prime to the goal. We fix the model's original output and try to learn what the correction would be from that given point. There are subtleties in getting this right. For instance, in the paper listed, they first run a training round where they only learn the correction part of the model. Then, in a second stage, they also learn the original part of the model itself. This is done to ensure that as the first part of the model changes, the correction part learns to adapt and continues producing good corrections.

解决这个问题的一种方法是尽可能地遵循策略（on-policy）。在这种设置中，我们生成 Z'，然后从 Z' 生成所有可能的后续内容，直至达到目标。我们固定模型的原始输出，并尝试从该给定点学习如何进行纠正。要正确实现这一点存在一些微妙之处。例如，在所列的论文中，他们首先进行一轮训练，只学习模型中的纠正部分。然后，在第二阶段，他们也训练模型本身的原始部分。这样做是为了确保当模型的第一部分发生变化时，纠正部分会学习适应并持续产生良好的纠正。

When done correctly, this approach outperforms both training on examples and our guess-and-check approach. It also scales better than simply pairing up examples and learning to correct them.

如果操作得当，这种方法的效果会比直接用示例进行训练，或者比我们那种反复试错（guess-and-check）的方法都要好。此外，它在可扩展性方面也优于简单地将例子成对匹配并从中学习纠正错误的方法。

Of course, our final goal is not individual corrections, but corrections applied repeatedly, all in a single chain. This is the motivation behind stream of search. In this work, they first find an optimal Z star by applying a training-time search algorithm that produces the tree on the right. This tree finds a very good chain of thought, but also intermediate branches that go in the wrong direction. Once we have this tree, instead of training just on the path to the final answer, we linearize this tree into a single stream. The picture at the bottom schematically shows what's happening. We construct a synthetic chain of thought that takes a winding path to get to the final answer. When we see actual backtracking in the tree, this becomes words in the stream. This gives us something that looks like it's doing search, even though it's just a single path from start to end. We can then train on these streams to achieve search-like behavior.

当然，我们的最终目标并非单独的修正，而是将修正重复应用，并将其整合到一个连续的链条中。这正是搜索流（stream of search）这种方法的灵感来源。在这项工作中，研究人员首先通过应用一种在训练阶段使用的搜索算法，来找到最优的 Z 星。该算法会生成右侧所示的树结构。这棵树不仅能发现一条非常出色的思维链（chain of thought），同时也会探索到一些指向错误方向的中间分支。一旦我们得到了这棵树，我们并不仅仅针对通往最终答案的路径进行训练，而是将整棵树线性化，将其转化为一个单一的序列流。底部图片示意性地展示了这一过程：我们构建了一个合成的思维链，它通过一条迂回曲折的路径最终到达答案。当我们在树中观察到实际的回溯（即撤销之前的步骤）时，这些回溯动作就会被编码成流中的词语或 Token。这使得它展现出类似搜索的行为，即使实际上它只是从起点到终点的一条单一路径。随后，我们就可以利用这些流进行训练，从而使模型具备类似搜索的能力。

To summarize this a bit more informally, we try to convert from a tree to a stream. We use tree search to explore multiple paths. We convert this stream into a linear sequence, and then we allow models to see their mistakes in the stream. This type of method could be combined with methods like learning to correct to improve each individual step and make it more on-policy. This approach is relatively complex, but many experts I've spoken to are convinced that something like this is behind what O1 is doing.

更通俗地讲，我们可以这样概括：我们试图将一种「树状」的复杂结构（可能代表多种可能性或决策分支）转化为一个连续的「流」（即线性的信息序列）。我们通过「树搜索」的方式，来探索这些可能的路径。接着，我们将这个信息流转换成一个线性的序列，这样模型就能在处理这个序列时，及时发现并修正自己的错误。这种方法还可以与「学习纠正」等技术相结合，从而优化每个处理步骤，使其更好地符合预设的策略。虽然这种方法听起来比较复杂，但我交流过的许多专家都确信，O1 公司目前所采用的，正是类似这样的技术。

So, let's discuss the pros and cons. It seems that learning to correct and plan is a crucial part of the process. It's the first time we've seen something similar to the actual chains of thought from O1. It also seems plausible that this can be used to induce search-like behavior into a single test-time model. On the negative side, this is also a quite complex training procedure. There are many points where the system could fail or collapse. This is because these corrections require providing synthetic examples or trying to keep the model on-policy. We also have limited empirical evidence so far in the open research literature that this can induce this type of interesting behavior. In particular, methods like stream of search have only been applied to relatively simple problems. Still, I believe this is the most interesting of the potential ideas, and it would be great to see people implement this in practice.

接下来，我们来探讨一下其优缺点。首先，学习如何纠正错误和进行规划，似乎是整个过程中至关重要的一环。这是我们首次观察到与 O1 实际思维链（chains of thought）类似的行为。同时，这种方法似乎也能在单个测试时模型（test-time model）中，引导出类似于搜索（search-like）的能力。

然而，其不足之处在于，这种训练过程相当复杂。系统在多个环节都有可能出现故障或崩溃。这主要是因为进行纠正需要提供合成示例，或者需要努力让模型保持在预设策略（on-policy）上。此外，截至目前，在公开的研究文献中，我们只有有限的经验证据表明这种方法能够真正引发这种有趣的特性。特别是，像搜索流（stream of search）这样的方法，目前也仅应用于相对简单的问题。尽管如此，我依然相信这是所有潜在想法中最有前景的一个，我们非常期待看到它能在实践中得到应用。

Let me conclude by talking about some of the implications of this research. So first off, the thing I care about most is actually replication. As an open-source community, we need to get better at building some of these large-scale, RL-based systems and showing they can really work. It's critical to have open-source versions of these models so that we can explore what's going on and to build better or more efficient ones. There are critical system aspects that differ for how open-source systems might look versus how the ones that companies are designed. And so it's quite possible the open-source versions may not actually look the same or maybe perform in different ways. Still, even if we can't replicate exactly what OpenAI did, I think the fact that they demonstrated this result really should motivate the community to know that it's possible and that we can build one of our own.

最后，我想谈谈这项研究的一些启示。首先，我最关心的是复现（replication）。作为一个开源社区，我们需要更好地构建这些大规模的、基于强化学习（RL）的系统，并证明它们确实有效。拥有这些模型的开源版本至关重要，这样我们才能深入探究它们的工作原理，并构建更好或更高效的模型。开源系统与公司设计的系统在关键系统方面可能有所不同。因此，开源版本看起来不完全相同或表现出不同性能是很有可能的。尽管如此，即使我们无法精确复现 OpenAI 的成果，但我认为他们展示的这一结果，确实应该激励社区认识到这是可能实现的，并且我们有能力构建我们自己的系统。

In addition, there are incredibly exciting research implications behind this work. I want to talk about a couple areas that I think it's important to consider. The first is that the last five years have really been dedicated to this idea of understanding what scaling means and how it changes how a language model performs. Much of this has been somewhat mysterious. These abilities come out of these models as we go. I'm really excited to understand how test-time compute can be understood and how it changes some of these stories. Test-time compute seems much more transparent. We can understand what the chain of thought is doing and to get a sense of how it explains or contradicts the results it produces.

此外，这项工作蕴含着令人振奋的研究前景。我想谈谈其中几个我认为需要重点考虑的领域。首先，过去五年，研究的重心一直放在理解「扩展」（scaling）的含义，以及它如何影响大语言模型（LLM）的性能上。这其中大部分过程都显得有些神秘，这些模型的能力似乎是随着发展而自然涌现的。我非常期待能深入理解「测试时计算」（test-time compute）是如何运作的，以及它将如何改变我们对模型性能的认知。相比之下，测试时计算似乎更为透明。我们可以清楚地理解「思维链」（chain of thought）推理过程在做什么，并据此判断它如何解释或推翻模型产生的结果。

The other thing that's quite interesting is the fact that these systems are bottlenecked by their inference-time systems capabilities. We've been focusing on inference to try to make it cheaper or faster in a kind of chatbot setting, but in this setting here, inference really becomes prioritized. If you can make a system a thousand times faster, that's say three orders of magnitude of extra reasoning ability. That's a much more interesting capabilities change than simply kind of serving a model cheaper.

另一个相当有趣的地方是，这些系统受限于其推理时系统的能力。我们过去一直专注于让推理在聊天机器人（chatbot）场景中变得更便宜或更快，但在目前的这种情况下，推理的优先级确实变得非常高。如果你能让一个系统快上一千倍，这相当于在推理能力上提升了三个数量级。这种能力上的飞跃，远比仅仅提供一个更便宜的模型要有趣得多。

Another thing I'm really excited about is just to be done with prompting. I think prompting has been an intellectually really kind of boring area and one that has kind of dominated the practical use. Don't get me wrong, I think prompting is really useful and there's a lot of cool things you can do with it, but there's not much more to say about it from a research perspective. I'm really interested in the move from prompting to some sort of formal specification. If we can produce interesting verifiers for hard problems and use language models to optimize against them, that opens up all sorts of interesting new areas of work.

还有一件事让我非常期待，那就是彻底摆脱提示词（prompting）。我认为提示词这个领域，从智力层面来看一直都挺无聊的，但在实际应用中却占据了主导地位。别误会我的意思，提示词确实非常有用，用它能做很多很酷的事情，但从研究角度来看，关于它已经没什么好深挖的了。我真正感兴趣的是从提示词转向某种形式化规范。如果我们能为那些难题创造出有趣的验证器，并利用大语言模型针对它们进行优化，那将会开辟出各种全新的、有趣的工作领域。

Next, I think these models really open up many new paths for evaluations. My group has been thinking a lot about evaluations that are just extremely hard and on tasks that we'd really like to do but are way beyond the capability of even the best language models. For instance, we've been working on benchmarks where you have to write entire new coding packages based just on their unit tests. This sort of superhuman evaluation becomes really exciting when you can have a model that just runs forever and takes that feedback into account in terms of producing an answer. I think we really need to think about evaluations in terms of what we'd like these systems to do as opposed to just what we think the current generation can do.

接下来，我认为这些模型确实为评估工作开辟了许多新的道路。我的团队一直在深入思考那些极其复杂、甚至超越当前最强大语言模型能力范围的任务评估，而这些任务正是我们非常渴望让模型去完成的。举例来说，我们一直在开发这样的基准测试：要求模型仅凭单元测试来独立编写出全新的软件包。当一个模型能够持续运行，并根据收到的反馈不断优化其输出时，这种超越人类能力的评估方式就变得异常令人兴奋。我认为，我们确实需要从「我们希望这些系统能做什么」的角度来重新审视评估，而不是仅仅局限于「我们认为当前这一代模型能做什么」。

And finally, maybe this one is obvious, but throughout this entire talk, I never really talked about neural networks at all. The move to search-based systems really is about how these systems are utilized, what they generate as their intermediate steps, and how you might change or explore that. This is very different than the sort of interpretability that we've seen where you try to dive into the model itself and interpret its kind of continuous valued weights. I'd be really excited to see how this changes how we think about this problem, how we understand our models, or what they do.

最后一点，或许显而易见，在整个演讲中，我几乎没有提及神经网络。转向基于搜索的系统，实际上更多是关于这些系统如何被利用，它们在中间步骤中生成了什么，以及我们如何调整或探索这些中间步骤。这与我们通常看到的模型可解释性（interpretability）方法截然不同，后者往往试图深入模型内部，去解释其连续值的权重。我非常期待看到这种转变将如何改变我们对这个问题的思考方式，以及我们如何理解和认识这些模型的工作原理。

So thanks very much for listening. I have a GitHub page with the full bibliography, slides, and issues from this talk. I'll probably update it for the next couple months as new papers come out or come in. If you have any thoughts about where this is leading research, please leave them in the comments or an issue page, or you can find me on Twitter. Thanks so much.

非常感谢您的聆听。我有一个 GitHub 页面，上面有本次演讲的完整参考文献、幻灯片以及讨论点。在接下来的几个月里，随着新论文的发布或收录，我可能会持续更新。如果您对这个研究方向的未来发展有任何想法，请在评论区或问题页面留言，或者您也可以在 Twitter 上找到我。非常感谢。