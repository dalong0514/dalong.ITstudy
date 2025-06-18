## 20250618The-Case-for-Software-Craftsmanship-in-the-Era-of-Vibes

[The Case for Software Craftsmanship in the Era of Vibes — Zed's Blog](https://zed.dev/blog/software-craftsmanship-in-the-era-of-vibes)

They tell me software developers will soon be replaced by autonomous agents.

他们告诉我，软件开发者很快就会被自主智能体（autonomous agents）取代。

Yet every single day，I encounter bad software.

然而，我每天都会遇到糟糕的软件。

When AGI comes，can its first assignment be to ship a decent calendar app?

当通用人工智能（AGI）出现时，它的第一个任务能不能是推出一款像样的日历应用程序？

I'm not here to complain about bad software，at least not in this post.

我在这里并不是要抱怨糟糕的软件，至少在这篇文章里不是。

I'm here to make the case for quality software in an era where constraints on code production have been dramatically lifted.

我将在这里探讨在代码生产限制已被极大解除的时代，高质量软件的重要性。

### When Limits Disappear，Quality Should Matter More

当限制消失，质量更应举足轻重

You can vibe code at a buttery-smooth 120fps in Zed and generate code 24 hours a day if you're so inclined.

你可以在 Zed 里用 120 帧的流畅体验编写代码，甚至如果你想，还可以一天 24 小时不停地生成代码。

But in a world of abundance，the bar should be higher for quality.

然而，在一个资源丰富的时代，我们对质量的要求应该更高。

As software engineers，we should measure our contribution not in lines of code generated，but in reliable，well-designed systems that are easy to change and a pleasure to use.

作为软件工程师，我们衡量自身贡献的标准，不应该看生成了多少行代码，而应该看我们是否构建出了可靠、设计精良、易于修改且用起来让人感到愉悦的系统。

There's a lot of talk online about the 10x（or even the 100x!）engineer.

网上有很多关于「10 倍工程师」（甚至「100 倍工程师」！）的讨论。

Most people are talking about how AI can help us make software faster and help us make more software.

大家普遍在讨论人工智能（AI）如何帮助我们更快地开发软件，以及开发出更多的软件。

As craftspeople，we should look at AI and ask，"How can this help me build better software?"

作为软件开发者，我们应该审视 AI 并问：「AI 如何能帮助我构建更好的软件？」

[Leveraging Rust and the GPU to render user interfaces at 120 FPS — Zed's Blog](https://zed.dev/blog/videogame)

### System Design Matters More

系统设计更重要

If you've spent any time in a codebase that solves real problems，I'm sure you can relate to this sentiment："I want this to be better，but I don't have time to fix it."

如果你在解决实际问题的代码库里待过一段时间，我确信你一定能体会到这样一种心情：「我希望它能更好，但我没时间去修复它。」

The system is broken in ways that hobble our productivity and imagination，but we need to ship.

当前的系统存在缺陷，这些缺陷束缚了我们的生产力和想象力，但我们仍然需要按时交付。

There's always an incentive to achieve our goals by bending the existing system instead of revising it，even if that leaves the system「not quite right，but good enough."

我们总是倾向于利用现有系统来实现目标，而不是对其进行彻底修改，即使这样做会让系统处于一种「不尽完美，但尚可接受」的状态。

Our values at Zed of「Shipping & Craftsmanship」exist as a pair for a reason.

我们在 Zed 的价值观 ——「交付」与「匠心」—— 之所以并重，是有其深层原因的。

We should feel urgency，but we shouldn't be using urgency as an excuse to cut corners.

我们理应怀有紧迫感，但绝不能让紧迫感成为我们敷衍了事、偷工减料的借口。

Short-term gains aren't worth the cost of suboptimal velocity for the lifetime of the company.

为了短期收益而牺牲公司长期的发展效率，是完全不值得的。

This is even more true now that a gnarly code base hinders not only our own ability to work in it，but also the ability of AI tools to be effective in it.

尤其在当下，一个「乱糟糟」的代码库不仅会拖慢我们自己的工作进度，还会大大削弱 AI 工具在其中发挥作用的效率。

Recognizing this dynamic doesn't make it any easier to resolve.

就算我们认识到了这种动态，也无法让问题变得更容易解决。

Since we're only learning about a system as we build it，we may not even know what the「right design」is until rather far into the system's development.

毕竟，我们是在构建一个系统时才能真正了解它，因此我们甚至可能要等到系统开发相当后期，才知道什么是「正确的设计」。

Each of our many decisions may make sense in the moment，but over time they accumulate，and before we know it we find ourselves working in what feels like a legacy codebase—despite trying at every turn to avoid that outcome.

我们做出的每一个决定，在当时看来可能都合理，但日积月累，不知不觉中，我们就会发现自己正在一个仿佛「遗留代码库」的环境中工作 —— 尽管我们一直都在竭力避免这种结果。

All of this makes it more critical than ever to evaluate contributions not by how many lines of code you touched，but by your impact on how reliable，understandable，and changeable the resulting system will be.

所有这一切都使得评估贡献变得比以往任何时候都更加关键，评判标准不再是你修改了多少行代码，而是你的工作对最终系统在可靠性、可理解性和可修改性方面产生了多大影响。

### Taking Ownership and Raising the Bar

So how do we build good software? There are probably multiple ways，but I'll tell you mine.

承担所有权并提高标准那么，我们到底该如何构建优秀的软件呢？实现这个目标的方法可能不止一种，但我会告诉你我的经验。

It requires taking ownership of the user's experience.

这意味着要对用户的体验负责。

As a user of a code editor，I want a fast experience.

作为代码编辑器的用户，我希望能获得快速流畅的体验。

If complex 3D games can run at 120 frames per second，there's no reason my editor couldn't render 2D text and rectangles that fast.

既然复杂的 3D 游戏都能以每秒 120 帧的速度流畅运行，那么我的编辑器也理应能够如此快速地渲染 2D 文本和矩形。

That was my initial goal for Zed，although at the time I didn't know how to achieve it.

这便是 Zed 最初的开发目标，尽管当时我还没有找到实现它的方法。

One thing I did know，based on my past experience creating a code editor named Atom（and its spinoff，Electron），is that I'd have to look beyond web technology.

我非常清楚一件事：基于我过去开发代码编辑器 Atom（及其衍生框架 Electron）的经验，我必须跳出传统网络技术的桎梏。

Otherwise，I'd never be able to achieve an experience better than a web browser.

否则，我将永远无法打造出超越网页浏览器的用户体验。

So I started over.

于是我从头再来。

But starting over meant taking on a much wider scope，learning a systems programming language with a sadistically helpful compiler，and learning to write shaders.

但从头再来意味着要涉及更广泛的领域，学习一种拥有「虐我千百遍，我待她如初恋」般编译器的系统编程语言，并学习如何编写着色器（shaders）。

All of that added risk to the project，but without it，Zed couldn't have become what it is today.

虽然所有这些都增加了项目的风险，但如果没有这些，Zed 就无法成为今天的样子。

Luckily，that kind of learning and de novo software development just got vastly easier，thanks to the power of LLMs.

而幸运的是，得益于大语言模型（LLM）的强大能力，这种需要大量学习并从头开始的软件开发工作，如今变得异常简单。

Even with hallucinations，I would have given almost anything to have a language model chat me through Rust borrow checker errors when I was first learning.

哪怕它会「胡言乱语」（即出现幻觉），在我当初学习 Rust 语言时，如果有个语言模型能帮我解读那些恼人的「借用检查器」错误，我简直求之不得。

Taking full ownership over the user's experience is not as risky as it used to be.

如今，AI 智能体完全接管用户体验的风险已经远没有以前那么大了。

If we have the ambition to pursue an amazing experience，but only some of the skills necessary to deliver it，AI can help us overcome the knowledge gaps standing in our way.

如果我们渴望追求非凡的体验，却只具备实现目标所需的部分技能，那么 AI 可以帮助我们跨越知识上的障碍。

It won't be a drop-in substitute for actual expertise，and we'll still make mistakes as we go，but it will let us experiment faster，learn faster，and iterate faster than we ever could in the old days.

它不会是真正专业知识的现成替代品，我们前进的道路上仍会犯错，但它将使我们比过去任何时候都能更快地进行实验、学习和迭代。

Aim high! The barrier to entry to building truly great experiences has never been lower.

志存高远！打造真正卓越体验的门槛从未如此之低。

### Let's Figure It Out Together

让我们共同探索

AI agents have not existed for very long.

AI 智能体问世的时间并不长。

We've already learned a lot about how best to use them，but there remains much to learn.

我们已经对如何更好地利用它们积累了许多经验，但仍有许多未知领域有待我们探索。

What's more，the tools themselves continue to improve，which creates ever-moving goalposts in our pursuit of understanding.

更重要的是，工具本身也在不断进步，这使得我们在追求理解的道路上，目标变得难以固定。

In this rapidly evolving environment，how can we determine which skills and techniques work best with which tools?

在这样一个快速发展的环境中，我们如何才能确定哪些技能和技术与哪些工具配合得最好呢？

The same way we always have：sharing knowledge with one another!

就像我们一直以来的做法一样：互相分享知识！

That's why today，we're introducing Agentic Engineering—combining human craftsmanship with AI tools to build better software.

正因如此，今天我们正式推出「AI 智能体工程（Agentic Engineering）」—— 它巧妙地将人类的精湛技艺与 AI 工具相结合，旨在打造出更优秀的软件。

[Zed — Agentic Engineering](https://zed.dev/agentic-engineering)

Every other week we'll be bringing on experts to hash things out with us.

我们计划每隔一周邀请各路专家，和我们一起深入探讨各种话题。

The line up is super exciting.

本季的嘉宾阵容，绝对会让你眼前一亮！

Join us in our discovery and let's figure this out together.

欢迎加入我们，和我们一起探索，解开谜团。

Sign up below for invites to the live events and recaps in your inbox.

请在下方注册，以便通过电子邮件接收直播活动的邀请和精彩回顾。