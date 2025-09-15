## 20250915Writing-Code-Is-Easy-Reading-It-Isnt

[Writing Code Is Easy. Reading It Isn’t.](https://idiallo.com/blog/writing-code-is-easy-reading-is-hard)

Writing code is easy. Once you have a solution in mind, and have mastered the syntax of your favorite programming language, writing code is easy. Having an LLM write entire functions for you? Even easier. But the hard part isn't the writing. It's the reading. It's the time it takes to load the mental model of the system into your head. That's where all the cost really is.

编写代码其实很简单。一旦你心中有了解决方案，并且熟练掌握了你常用编程语言的语法，写代码就变得轻而易举。如果让一个大语言模型（LLM）直接为你写出完整的函数，那更是易如反掌。然而，真正困难的部分不在于「写」，而在于「读」。它耗费的是你将整个系统的心智模型（mental model）载入大脑所需的时间。这，才是所有成本的真正所在。

A mental model is the thing you build when you read code. It's your internal map of how the system works, where the tricky parts are, what depends on what. Without it, you're just staring at lines of text.

心智模型（mental model）是你在阅读代码时在大脑中构建的一种理解框架。它就好比你脑海中绘制出的一张内部地图，清晰地展示了系统是如何运作的，哪些地方是复杂的难点，以及各个部分之间如何相互依赖。如果没有它，你可能就只是茫然地盯着一行行代码而已。

When I worked as a contractor, most of my jobs started the same way. I'd get a task to fix a bug or add a new feature in an application I'd never seen before. My mental model was clean and empty at first. To start filling it, I'd check the homepage to see what it looked like. I'd look at the page source: is this React? jQuery? A third-party plugin? I'd scan the codebase to see if the carousel they are requesting on the front page was used elsewhere. I'd check their build process, their testing setup, the tools they leaned on. Every little detail I discovered got appended to the model in my head.

当我以承包商身份工作时，我的大部分任务都以类似的方式开始。我通常会接到一项任务，需要在一个我从未接触过的应用程序中修复一个 bug 或添加一个新功能。一开始，我的「心智模型（mental model）」是一片空白。为了开始构建这个模型，我首先会查看应用程序的首页，了解其外观。接着，我会检查页面源代码，判断它是否使用了 React、jQuery，抑或是某个第三方插件。我还会扫描整个代码库，看看首页上要求的「轮播（carousel）」功能是否在其他地方也被使用。我还会仔细研究他们的构建流程、测试设置以及他们所依赖的各种工具。我发现的每一个微小细节都会被添加到我脑中的这个模型里，不断充实它。

It was like moving into a new city. You start at the foot of your apartment, wander a few streets, notice which roads lead to the freeway, where the grocery store is, and slowly you start to orient yourself. That's what reading code feels like: you're building a mental map so you don't get lost every time you move around.

这就像搬到一个新城市。你从公寓门口开始，在附近的几条街上转转，留意哪些路通往高速公路，杂货店又在哪里，然后你慢慢地开始熟悉周围的环境。阅读代码的感觉也正是如此：你正在构建一张「心理地图」，这样每次你在其中探索时，就不会迷失方向。

Say you need to understand a simple function like getUserPreferences(userId). To build your mental model, you need to trace:

假设你需要理解一个像 getUserPreferences（userId）这样简单的函数。为了在脑海中构建其工作原理图，你需要探究：

1 Where is this function defined?

这个函数是在哪里定义的？

2 What does it return? Is it a Promise? What's the shape of the data?

它会返回什么？是一个 Promise（Promise）吗？数据的结构是怎样的？

3 Does it hit a database directly or go through an API?

它是直接访问数据库，还是通过 API 调用？

4 Are there caching layers involved?

是否包含缓存层？

5 What happens if the user doesn't exist?

如果用户不存在，会发生什么？

6 Who else calls this function and in what contexts?

还有谁会调用这个函数，以及是在什么情境下调用的？

7 Are there side effects?

会有附带影响（side effects）吗？

Understanding that one function means jumping between database schemas, API definitions, error handling middleware, and multiple call sites. Only after building this web of relationships do you have enough context to safely modify anything.

当我们谈论一个功能时，它可能意味着要穿梭于不同的数据库模式、API 定义、错误处理中间件以及多个调用点之间。只有在构建起这样一个错综复杂的关系网络之后，你才能获得充分的背景信息，从而确保对任何部分进行修改时都是安全的。

And it's slow. Reading code is harder than writing it. Much harder. Writing code is forward motion: you're laying down fresh pavement. Reading code means retracing someone else's steps, which usually means jumping between files, chasing function calls, inferring side effects, and deciphering intentions that aren't written down. Understanding one function often means looking at five other files. Only after all that do you have enough of a map to even begin.

而且，这个过程很慢。阅读代码比编写代码要难得多。编写代码就像是向前推进：你正在铺设全新的路面。而阅读代码则意味着要追溯他人走过的路径，这通常包括在不同文件间来回跳转、追踪各种函数调用、推断可能产生的副作用，以及解读那些没有明确写下来的意图。要理解一个函数，往往需要查阅其他好几个文件。只有完成了所有这些工作，你才能构建出一张足够清晰的「地图」，从而真正开始。

It's the same reason debugging is harder than coding. On Stack Overflow, one of the most common comments you'll see under a bad question is: "Can you show us what you did?" Without seeing the steps, no one can load the right model in their head to help. It's also why the XY problem keeps coming up. People ask about a symptom without giving the context that would let others reconstruct the whole picture.

这与调试比编码更难是同一个道理。在 Stack Overflow 上，对于那些描述不清的问题，你最常看到的评论之一是：「你能向我们展示你是如何操作的吗？」如果不了解具体的步骤，没有人能在脑海中构建出正确的问题模型来提供帮助。这也就是 XY 问题屡屡发生的原因：人们在没有给出足以让其他人重建整个情况的背景信息时，就直接提出了一个表象问题。

I'm still fascinated by the lawyer who used ChatGPT in court. He filed a brief that cited six cases which turned out not to exist. Everyone asked: why didn't he read them? The answer is the same: it takes time and effort to build the model. He would have had to chase down each case, read them, and slot them into a broader understanding of legal precedent. Reading is the hard part. Generating is easy.

我仍然对那位在法庭上使用 ChatGPT 的律师印象深刻。他提交了一份法律文件（brief），其中引用了六个案件，但这些案件结果却根本不存在。每个人都问：他为什么不去阅读这些案件呢？答案其实很简单：要真正理解和核实这些信息需要花费大量时间和精力。他本该追查每一个案件，仔细阅读，并将其融入到对法律先例（legal precedent）的更广泛理解中。由此可见，阅读和理解才是困难的部分，而通过 AI 生成（Generating）内容反而是容易的。

Reading isn't just about going through the code and examining it line by line. It's also about going through the documentation, code reviews, and peer programming. In fact, these are solutions for accelerating the process of building our mental model. But with that in mind, you still have to, well, read and understand. You'll notice that programmers often want to rewrite things from scratch, because "the old code sucks". What sucks is taking the time to read and understand it.

阅读代码并不仅仅是逐行审视它。它还包括查阅文档、进行代码审查（code reviews）以及结对编程（peer programming）。事实上，这些都是有助于我们更快构建对代码心智模型（mental model）的有效方法。但即便如此，你仍然必须亲自去阅读和理解。你可能会注意到，程序员们常常想从头重写代码，因为他们觉得「旧代码太烂了」。然而，真正令人头疼的，其实是要花时间去阅读和理解那些「烂」代码。

And this is what makes LLMs both powerful and dangerous in programming. Whether the AI generates perfect code or complete hallucinations, you still have to read it. You still have to trace through what it's supposed to do, how it interacts with the rest of the system, and what the side effects are. The longer the generated code, the longer it takes to build your mental model. And only once you've done that can you spot the issues, the places where the generated code doesn't quite fit, or quietly breaks something else.

这正是为什么大语言模型（LLMs）在编程中既强大又危险。无论是 AI 生成了完美无瑕的代码，还是完全是「幻觉（hallucinations）」的产物，你都必须亲自动手去审阅它。你得仔细理清它到底该做什么，它将如何与系统的其他部分协同工作，以及可能带来哪些潜在的副作用。生成的代码越长，你在脑海中构建其逻辑模型所需的时间就越久。只有当你彻底完成了这些分析，才能发现其中存在的问题，比如生成的代码不够严丝合缝的地方，或是暗中破坏了其他功能。

When an LLM can produce an infinite amount of code or text, it tempts us to skip the reading. But you can't skip the model. You wouldn't want to load someone else's saved game and be dropped in the middle of a boss fight. That's what it feels like to inherit or generate code you don't understand.

当一个大语言模型（LLM）能够生成海量的代码或文本时，我们很容易产生直接跳过阅读和理解的冲动。然而，你无法绕开对「模型」本身的理解。就好比你肯定不希望加载别人的游戏存档，结果却发现自己被直接扔进了一场 Boss 战中。继承或生成你完全不理解的代码，给人的感觉正是如此。

This is why the real bottleneck in software development isn't writing, it's understanding.

这就是为什么软件开发中真正的瓶颈不在于编码，而在于理解。

---

For now, we don't have the LLM equivalent for understanding. Something that could instantly transfer a complete mental model from the system to your head. Until we do, the bottleneck hasn't moved. We've solved the "typing speed" problem. We can generate more code than we could ever hope to read. But until we solve the "understanding" problem, the cost of software development remains the same: the time it takes for someone to make sense of it all.

目前，我们还没有在理解力方面能与大语言模型（LLM）相提并论的技术。我们缺少一种能瞬间将系统中的完整心智模型（mental model）直接「传输」到你大脑中的工具。在此之前，瓶颈依然存在。我们已经解决了「打字速度」的问题，现在能够生成的代码量远超我们能阅读的。然而，只要「理解」问题尚未解决，软件开发的成本就始终不变：即一个人需要花费时间去理解所有这些内容。

This has real implications for how we use AI tools. Instead of asking AI to generate large blocks of code, we might be better off asking it to help us understand existing code. Instead of measuring productivity by lines of code written, we should measure it by how quickly teams can build accurate mental models of their systems.

这对于我们如何使用 AI 工具产生了实际影响。与其让 AI 生成大量代码，我们不如让它帮助我们理解现有代码。与其通过编写的代码行数来衡量生产力，我们更应该通过团队能多快地构建出他们系统准确的心智模型（mental model）来衡量它。

The future of programming might not be about generating more code faster. It might be about generating understanding faster. And that's a much harder problem to solve.

未来编程的发展，或许不再是围绕着更快地生成更多代码，而是关于如何更快地生成理解。而这，则是一个远为复杂且难以攻克的难题。