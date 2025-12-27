## 20251007Vibe-Engineering

[Vibe engineering](https://simonwillison.net/2025/Oct/7/vibe-engineering/)

Simon Willison's Weblog

7th October 2025

I feel like vibe coding is pretty well established now as covering the fast, loose and irresponsible way of building software with AI—entirely prompt-driven, and with no attention paid to how the code actually works. This leaves us with a terminology gap: what should we call the other end of the spectrum, where seasoned professionals accelerate their work with LLMs while staying proudly and confidently accountable for the software they produce?

我认为，氛围编程（vibe coding）如今已是一个相当成熟的概念，特指那种快速、随意且不负责任的使用 AI 构建软件的方式 —— 整个过程完全由提示驱动，毫不关心代码的实际工作原理。这便引出了一个术语上的空白：我们该如何称呼与之相反的另一端呢？在那里，经验丰富的专业人士利用大语言模型（LLM）来提升工作效率，同时依然对他们产出的软件保持着自豪感与高度负责的态度。

I propose we call this vibe engineering, with my tongue only partially in my cheek.

我提议我们称之为「氛围工程」，虽然我这么说多少带点开玩笑的成分。

One of the lesser spoken truths of working productively with LLMs as a software engineer on non-toy-projects is that it's difficult. There's a lot of depth to understanding how to use the tools, there are plenty of traps to avoid, and the pace at which they can churn out working code raises the bar for what the human participant can and should be contributing.

对于软件工程师来说，在非玩具性质的实际项目中高效运用大语言模型（LLM）进行工作，有一个不常被提及的事实是：这其实很难。要掌握这些工具的使用方法大有学问，其中不乏许多需要避开的陷阱。而且，大语言模型能以极快的速度生成可运行的代码，这反过来也拔高了对人类参与者自身能力与贡献水平的要求。

The rise of coding agents—tools like Claude Code (released February 2025), OpenAI's Codex CLI (April) and Gemini CLI (June) that can iterate on code, actively testing and modifying it until it achieves a specified goal, has dramatically increased the usefulness of LLMs for real-world coding problems.

编码智能体（Coding Agent）的崛起，极大地提升了大语言模型（LLM）解决实际编程问题的能力。这类工具，例如 Claude Code（2025 年 2 月发布）、OpenAI 的 Codex CLI（4 月发布）和 Gemini CLI（6 月发布），能够对代码进行迭代，主动测试并修改，直至实现预设的目标。

I'm increasingly hearing from experienced, credible software engineers who are running multiple copies of agents at once, tackling several problems in parallel and expanding the scope of what they can take on. I was skeptical of this at first but I've started running multiple agents myself now and it's surprisingly effective, if mentally exhausting!

最近，我越来越多地从一些经验丰富、值得信赖的软件工程师那里听说，他们开始同时运行多个 AI 智能体（Agent），让这些智能体并行处理不同的问题，从而大大拓展了个人能应对的工作范畴。起初我对这种做法持怀疑态度，但现在我自己也开始运行多个智能体了，效果确实令人惊讶 —— 尽管非常耗费脑力！

This feels very different from classic vibe coding, where I outsource a simple, low-stakes task to an LLM and accept the result if it appears to work. Most of my tools.simonwillison.net collection (previously) were built like that. Iterating with coding agents to produce production-quality code that I'm confident I can maintain in the future feels like a different process entirely.

这种感觉与经典的「氛围编程」（vibe coding）截然不同。在氛围编程中，我通常会将一个简单、低风险的任务交给大语言模型（LLM）去完成，只要输出的结果看起来能用，我就会直接采用。我此前收集的 tools.simonwillison.net 项目大多就是这样构建的。而如今，通过与 AI 编程智能体反复迭代，来生成我能放心在未来维护的生产级代码，这整个过程给人的感觉是完全不一样的。

It's also become clear to me that LLMs actively reward existing top tier software engineering practices:

我也清楚地认识到，大语言模型（LLM）极大地凸显了现有顶级软件工程实践的价值：

1 Automated testing. If your project has a robust, comprehensive and stable test suite agentic coding tools can fly with it. Without tests? Your agent might claim something works without having actually tested it at all, plus any new change could break an unrelated feature without you realizing it. Test-first development is particularly effective with agents that can iterate in a loop.

**自动化测试**。如果你的项目拥有健壮、全面且稳定的测试套件，基于 AI 智能体的编码工具就能高效运转。反之，如果没有测试，你的智能体可能会在未经实际验证的情况下就声称某项功能正常工作。此外，任何新的改动都可能在你毫无察觉的情况下破坏其他无关功能。对于能够循环迭代的智能体而言，测试驱动开发（Test-Driven Development）尤其有效。

2 Planning in advance. Sitting down to hack something together goes much better if you start with a high level plan. Working with an agent makes this even more important—you can iterate on the plan first, then hand it off to the agent to write the code.

提前规划。当你坐下来准备快速开发某个东西时，如果从一个高层级的计划开始，整个过程会顺利得多。与 AI 智能体（AI Agent）协作时，这一点尤为重要 —— 你可以先反复修改和完善计划，然后再将其交给智能体去编写代码。

3 Comprehensive documentation. Just like human programmers, an LLM can only keep a subset of the codebase in its context at once. Being able to feed in relevant documentation lets it use APIs from other areas without reading the code first. Write good documentation first and the model may be able to build the matching implementation from that input alone.

**全面的文档**。如同人类程序员，大语言模型一次也只能将代码库的一部分保留在其上下文窗口中。如果能为它提供相关的文档，它就可以无需预先阅读代码，直接使用其他模块的 API。因此，优先编写优质的文档，模型或许仅凭这些文档就能生成与之对应的代码实现。

4 Good version control habits. Being able to undo mistakes and understand when and how something was changed is even more important when a coding agent might have made the changes. LLMs are also fiercely competent at Git—they can navigate the history themselves to track down the origin of bugs, and they're better than most developers at using git bisect. Use that to your advantage.

良好的版本控制习惯。当 AI 编码智能体可能已实施修改时，能够回退错误、并清楚了解更改发生的时间和方式就显得尤为重要。大语言模型同样精通 Git —— 它们能自行查看历史记录以追溯问题的根源，并且在运用 git bisect 进行二分查找方面，其表现甚至优于大多数开发者。请善加利用这一优势。

5 Having effective automation in place. Continuous integration, automated formatting and linting, continuous deployment to a preview environment—all things that agentic coding tools can benefit from too. LLMs make writing quick automation scripts easier as well, which can help them then repeat tasks accurately and consistently next time.

**建立有效的自动化流程**。持续集成、自动化代码格式化与检查、持续部署到预览环境 —— 这些自动化实践同样能让智能体（Agentic）编码工具受益。大语言模型（LLM）也让编写快速自动化脚本变得更加容易，从而帮助（开发者或工具自身）下次能够更准确、更一致地重复执行任务。

6 A culture of code review. This one explains itself. If you're fast and productive at code review you're going to have a much better time working with LLMs than if you'd rather write code yourself than review the same thing written by someone (or something) else.

代码审查的文化。这一点很好理解。如果你能快速高效地进行代码审查，那么你与大语言模型（LLM）协作的体验会顺畅得多；反之，如果你宁愿自己动手写代码，也不愿意去审阅由他人（或 AI）生成的实现相同功能的代码，过程就会艰难许多。

7 A very weird form of management. Getting good results out of a coding agent feels uncomfortably close to getting good results out of a human collaborator. You need to provide clear instructions, ensure they have the necessary context and provide actionable feedback on what they produce. It's a lot easier than working with actual people because you don't have to worry about offending or discouraging them—but any existing management experience you have will prove surprisingly useful.

一种非常奇特的管理体验。让一个编码智能体（Coding Agent）产出优秀成果的感觉，与和人类搭档合作获得好结果惊人地相似，甚至让人有点不自在。你需要给出清晰的指令，确保它掌握了必要的背景信息，并对它的产出给出具体、可执行的反馈。这比和真人协作要轻松得多，因为你完全不用担心会冒犯或打击到它 —— 不过，你已有的任何管理经验在这里都会变得出乎意料地好用。

8 Really good manual QA (quality assurance). Beyond automated tests, you need to be really good at manually testing software, including predicting and digging into edge-cases.

**出色的人工测试（Manual QA）能力**。除了依靠自动化测试，你还需要非常擅长手动测试软件，这包括预测各种极端情况并对其进行深入探究。

9 Strong research skills. There are dozens of ways to solve any given coding problem. Figuring out the best options and proving an approach has always been important, and remains a blocker on unleashing an agent to write the actual code.

强大的研究能力。解决任何一个编码问题，往往都有数十种方案。从中甄选出最优解并论证其可行性，历来都至关重要，而这至今仍是让 AI 智能体（AI Agent）实际编写代码的一个主要瓶颈。

10 The ability to ship to a preview environment. If an agent builds a feature, having a way to safely preview that feature (without deploying it straight to production) makes reviews much more productive and greatly reduces the risk of shipping something broken.

能够将功能部署到预览环境。当一个 AI 智能体（或自动化程序）开发出一个新功能时，如果有一种方法能安全地预览这个功能（而不是直接上线到生产环境），将极大地提升代码审查的效率，并显著降低将存在缺陷的功能交付上线的风险。

11 An instinct for what can be outsourced to AI and what you need to manually handle yourself. This is constantly evolving as the models and tools become more effective. A big part of working effectively with LLMs is maintaining a strong intuition for when they can best be applied.

一种能判断哪些任务可以外包给 AI、哪些需要亲力亲为的直觉。随着模型和工具变得日益强大，这种直觉也在持续演进。与大语言模型（LLM）高效协作的关键之一，就在于始终保持一种敏锐的直觉，知道在什么情况下它们能发挥最大效用。

12 An updated sense of estimation. Estimating how long a project will take has always been one of the hardest but most important parts of being a senior engineer, especially in organizations where budget and strategy decisions are made based on those estimates. AI-assisted coding makes this even harder—things that used to take a long time are much faster, but estimations now depend on new factors which we're all still trying to figure out.

对估算的新认知。准确预估项目耗时，向来是高级工程师面临的最棘手也最关键的任务之一，在那些依据预估来制定预算和战略决策的组织中尤其如此。而 AI 辅助编程（AI-assisted coding）让这件事变得更具挑战 —— 以往耗时良久的工作如今大幅提速，但现在的预估却取决于一系列新的变量，对于这些变量，我们所有人都仍在摸索之中。

If you're going to really exploit the capabilities of these new tools, you need to be operating at the top of your game. You're not just responsible for writing the code—you're researching approaches, deciding on high-level architecture, writing specifications, defining success criteria, designing agentic loops, planning QA, managing a growing army of weird digital interns who will absolutely cheat if you give them a chance, and spending so much time on code review.

要想真正发挥这些新工具的全部潜力，你必须拿出自己的看家本领。你的职责远不止是写代码 —— 你还需要调研技术方案、敲定高层架构、撰写设计规范、定义成功标准、设计 AI 智能体（AI Agent）的工作循环、规划测试（QA）、管理一支日益壮大的「数字实习生」大军（这些家伙一旦有机会绝对会偷奸耍滑），并且把大量时间花在代码审查上。

Almost all of these are characteristics of senior software engineers already!

几乎所有这些特质，本就是资深软件工程师所具备的！

AI tools amplify existing expertise. The more skills and experience you have as a software engineer the faster and better the results you can get from working with LLMs and coding agents.

AI 工具会放大你已有的专业知识。作为一名软件工程师，你的技能和经验越丰富，与大语言模型（LLMs）和编程智能体（coding agents）协作时，获得结果的速度就越快，质量也越高。

"Vibe engineering", really?

「氛围工程」，这名字真的好吗？

Is this a stupid name? Yeah, probably. "Vibes" as a concept in AI feels a little tired at this point. "Vibe coding" itself is used by a lot of developers in a dismissive way. I'm ready to reclaim vibes for something more constructive.

这名字蠢吗？嗯，大概是有点蠢。在人工智能（AI）领域，「氛围」这个概念如今听起来已经有点老生常谈了。许多开发者提到「氛围编码」时，本身就带着一种不屑一顾的意味。我打算为「氛围」这个词正名，让它指向一些更具建设性的东西。

I've never really liked the artificial distinction between "coders" and "engineers"—that's always smelled to me a bit like gatekeeping. But in this case a bit of gatekeeping is exactly what we need!

我一直不太喜欢「码农」和「工程师」之间那种人为的区分 —— 这在我看来总有点「划门槛」（gatekeeping）的意味。但眼下的情况，我们还真就需要这么一点「划门槛」！

Vibe engineering establishes a clear distinction from vibe coding. It signals that this is a different, harder and more sophisticated way of working with AI tools to build production software.

Vibe 工程（Vibe engineering）与 Vibe 编码（Vibe coding）划清了界限。它表明，这是一种截然不同的、更具挑战性也更为复杂的工作方式，即利用 AI 工具来开发生产级软件。

I like that this is cheeky and likely to be controversial. This whole space is still absurd in all sorts of different ways. We shouldn't take ourselves too seriously while we figure out the most productive ways to apply these new tools.

我很欣赏这种带点俏皮、甚至可能引发争议的风格。毕竟，整个（AI）领域目前在很多方面都还显得挺荒诞的。在我们摸索如何最高效地运用这些新工具时，大可不必太过较真。

I've tried in the past to get terms like AI-assisted programming to stick, with approximately zero success. May as well try rubbing some vibes on it and see what happens.

我以前也尝试过推广「AI 辅助编程」这类说法，但基本没成功。这回不如换个思路，给它加点「玄学」试试，看能不能成。

I also really like the clear mismatch between "vibes" and "engineering". It makes the combined term self-contradictory in a way that I find mischievous and (hopefully) sticky.

我也非常喜欢「氛围」与「工程」之间那种鲜明的反差。这种组合让这个术语本身形成了一种自相矛盾，我觉得这很顽皮，并且（希望它）能成为一个让人过目不忘的概念。
