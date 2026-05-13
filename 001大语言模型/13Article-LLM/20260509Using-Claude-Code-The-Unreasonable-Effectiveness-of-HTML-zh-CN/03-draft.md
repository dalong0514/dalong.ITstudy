## 使用 Claude Code：HTML 的不可思议的有效性

> **译者注**：本文标题 "The Unreasonable Effectiveness of HTML" 化用了物理学家尤金·维格纳（Eugene Wigner）1960 年的经典论文《数学在自然科学中的不可思议的有效性》（"The Unreasonable Effectiveness of Mathematics in the Natural Sciences"）。维格纳在那篇文章中感叹：数学这种纯粹抽象的工具，在描述物理世界时好用得几乎 "不讲道理"。本文作者借用这一典故，表达的是同样的惊叹 ——HTML 作为 AI 制品（artifact）的输出格式，其好用程度同样超乎想象。

[X 上的 Thariq："Using Claude Code：The Unreasonable Effectiveness of HTML" / X](https://x.com/trq212/status/2052809885763747935)

[The unreasonable effectiveness of HTML — examples](https://thariqs.github.io/html-effectiveness/)

Markdown 已经成为 AI 智能体与我们沟通时最主流的文件格式。它简洁、通用，具备一定的富文本能力，也方便你直接动手编辑。Claude 甚至在 Markdown 文件中用 ASCII 字符画图表的能力已经好到让人惊讶了。

但随着智能体变得越来越强大，我开始感觉 Markdown 已经成了一种束缚。超过一百行的 Markdown 文件，我读起来就很吃力了。我想要更丰富的可视化表达 —— 颜色、图表 —— 而且我希望能方便地分享给别人。

而且我现在越来越不自己动手编辑这些文件了，更多是把它们当作技术规格文档（spec）、参考资料、头脑风暴的产出来用。即使需要修改，我通常也是让 Claude 来改，这就让 Markdown "易于手动编辑" 这个最大的优势大打折扣了。

我已经开始更倾向于用 HTML 而非 Markdown 作为输出格式，而且发现 Claude Code 团队里越来越多同事也在这么做。下面就来聊聊为什么。

（如果你想先看看实际效果，这里有一堆示例：https://thariqs.github.io/html-effectiveness —— 不过记得看完了回来继续往下读。）

Why HTML?

Information Density

HTML 能传递的信息量比 Markdown 丰富得多。它当然可以做简单的文档结构，比如标题和文本格式，但除此之外还能表达各种各样的信息：

用表格呈现表格数据

用 CSS（层叠样式表）表达设计数据

用 SVG（可缩放矢量图形）绘制插图

用 script 标签嵌入代码片段

用 HTML 元素配合 JavaScript + CSS 实现交互

用 SVG 和 HTML 展示工作流

用绝对定位和 canvas 表达空间数据

用 image 标签嵌入图片

我甚至想说，几乎不存在 Claude 能读取、但 HTML 无法高效呈现的信息。这使得 HTML 成为模型向你传达深度信息的极佳手段，也让你能更高效地审阅这些内容。

我发现，当无法使用 HTML 时，模型会退而求其次用 Markdown 做一些低效的表达 —— 比如 ASCII 图表，或者我个人最 "喜欢" 的操作：用 Unicode 字符来 "估算" 颜色。下面这张截图就是 Claude Code 在 Markdown 里试图展示颜色的样子。

Claude Code trying to show color in markdown

Visual Clarity & Ease of Reading

随着 Claude 能处理的任务越来越复杂，它写出的技术规格文档和方案也越来越长。实际使用中我发现，超过 100 行的 Markdown 文件我基本不会通读，而要让团队里的其他人读完 —— 那更是不可能了。

但 HTML 文档就好读多了。Claude 可以通过标签页、插图、链接等手段在视觉上组织文档结构，让浏览体验更加理想。它甚至可以做响应式布局，让你在不同设备形态（form factor）上有不同的阅读体验。

Ease of Sharing

Markdown 文件其实挺难分享的，因为大多数浏览器并不能很好地原生渲染它们，你往往只能把文件当附件挂到邮件或消息里。

而 HTML 就不同了 —— 只要把文件上传到某个地方（比如 S3（亚马逊云存储服务）），就能直接分享链接。你的同事可以随时随地打开，方便地引用参考。

你的技术规格文档、报告或 PR（Pull Request，拉取请求）说明如果是 HTML 格式，别人真正去读的概率会高出太多太多。

Two-way Interaction

HTML 能让你与文档进行交互。比如，你可以让 Claude 在文档里加入滑块或旋钮来调整设计方案，或者让你调节算法里的不同参数来观察效果变化。你还可以让 Claude 加一个功能，把这些修改复制成 prompt，方便你粘贴回 Claude Code 里使用。

关于这种双向交互，可以看我之前写的 playgrounds 帖子，里面有很多例子：https://x.com/trq212/status/2017024445244924382

Data Ingestion

为什么要用 Claude Code 来生成 HTML 文件，而不是用 ClaudeAI 或者 Claude Design 呢？最大的原因之一是 Claude Code 能获取的上下文信息量远超其他方式。

举个例子，在写这篇文章的时候，我让 Claude Code 遍历我的代码文件夹，找出所有我之前生成的 HTML 文件，进行分组归类，然后生成一个包含各类型图表的 HTML 文件。你在这篇文章里看到的那些图表，就是这么来的。

除了文件系统之外，Claude Code 还可以通过 MCP（Model Context Protocol，模型上下文协议）工具（比如 Slack、Linear（项目管理工具）等）、你的浏览器（通过 Chrome 中的 Claude 插件）、你的 git 历史记录等等渠道获取更多上下文。

It's Joyful

用 Claude 制作 HTML 文档就是更有意思、更让人享受 —— 它让我感觉自己更深入地参与了创作过程、对成果更有投入感。光凭这一点，就足够了。

How to Get Started

说实话，我有点担心大家看了这篇文章之后会马上把它做成一个 /html 技能之类的东西。虽然这样做可能有一定价值，但我想强调的是：让 Claude 生成 HTML 根本不需要什么复杂设置。你只需要告诉它 "make a HTML file" 或者 "make a HTML artifact" 就行了。

关键在于你要清楚自己想让这个制品做什么、以及你打算怎么使用它。用久了你可能会把常用的模式沉淀成一个技能，但现在我建议先从零开始写 prompt，在各种场景中摸索出感觉。

Use Cases

为了让这些说法更具体，我针对不同的使用场景制作了很多 HTML 文件。你可以在这里查看所有示例：https://thariqs.github.io/html-effectiveness/ —— 下面是一个概览。

Specs，Planning & Exploration

HTML 是 Claude 深入探索问题的丰富的画布。当我开始着手一个问题时，我不再只写一份简单的 Markdown 方案，而是期待产出一系列互相关联的 HTML 文件。比如，我可能先让 Claude Code 进行头脑风暴，针对不同方案做一些探索性的呈现。然后让它在某个方向上深入展开，也许做一些原型图或代码片段。最后，等我觉得方向对了，再让它写出一份实施计划。当我对方案满意后，我会开一个新的会话，把所有这些文件传进去，让 Claude 据此实现代码。

在验证阶段，我也会让验证智能体读入这些文件，这样它就能对需求有更全面的理解。

Example Prompts:

I'm not sure what direction to take the onboarding screen. Generate 6 distinctly different approaches — vary layout，tone，and density — and lay them out as a single HTML file in a grid so I can compare them side by side. Label each with the tradeoff it's making.

Create a thorough implementation plan in a HTML file，be sure to make some mockups，show data flow and add important code snippets I might want to review. Make it easy to read and digest.

Use Cases:

Exploring other ways to implement something in code

Exploring multiple visual designs

Code Review & Understanding

在 Markdown 文件里阅读代码是一件很痛苦的事。但有了 HTML，我们可以渲染 diff、标注、流程图、模块关系图等等。你可以用这种方式来理解智能体写的代码，进行代码审查，或者向审查你代码的人解释一个 PR。我发现这往往比 GitHub 默认的 diff 视图好用得多 —— 现在我每发一个 PR 都会附上一份 HTML 格式的代码说明。

Example prompt:

Help me review this PR by creating an HTML artifact that describes it. I'm not very familiar with the streaming/backpressure logic so focus on that. Render the actual diff with inline margin annotations，color-code findings by severity and whatever else might be needed to convey the concept well.

Use Cases:

Creating a PR

Reviewing a PR

Understanding a topic in Code

Design & Prototypes

Claude Design 本身就是基于 HTML 构建的，因为 HTML 在设计表达上拥有极强的能力 —— 哪怕你最终的目标平台不是 HTML。Claude 可以先用 HTML 画出设计草图，然后再用你选择的语言来实现，无论是 React、Swift 还是其他什么。

你还可以用 HTML 来做交互原型 —— 动画效果、操作反馈等等。试试让 Claude 加入滑块、旋钮之类的控件，帮你精确调整到想要的效果。

Example prompt:

I want to prototype a new checkout button，when clicked it does a play animation and then turns purple quickly. Create a HTML file with several sliders and options for me to try different options on this animation，give me a copy button to copy the parameters that worked well.

Use this for:

Creating design system artifacts

Adjusting components

Visualizing component libraries

Prototyping Joyful Animations

Reports，Research & Learning

Claude Code 极其擅长整合多个数据源的信息，并转化为可读性很高的报告。你可以让 Claude 去搜索你的 Slack、你的代码库、git 历史、互联网等等，然后用这些信息为你自己、为领导层、为团队生成极易阅读的报告。

你可以把内容组织成一份详尽的 HTML 长文档、一个交互式的讲解页面，甚至是一套幻灯片。让 Claude 用 SVG 来画图表，能帮助你更好地可视化呈现信息。

比如，在写关于 prompt caching（提示缓存）的那几篇帖子时，我就让 Claude 先读了 git 历史里所有跟 prompt caching 相关的改动，然后为我整理出一份深度 HTML 研究文档供我阅读。

Example prompt:

I don't understand how our rate limiter actually works. Read the relevant code and produce a single HTML explainer page：a diagram of the token-bucket flow，the 3–4 key code snippets annotated，and a "gotchas" section at the bottom. Optimize it for someone reading it once.

Use this for:

Summarize how a feature works

Explain a concept to me

Weekly status reports to your boss

Incident reports to your leadership

SVG illustrations，flowcharts，technical diagrams，etc

Custom Editing Interfaces

有时候，仅靠在文本框里打字，你很难准确描述你想要的东西。遇到这种情况，我会让 Claude 给我做一个一次性的编辑器 —— 专门为我当前手上这份数据量身定制。不是什么产品级的工具，也不是什么可复用的通用组件，就是一个单独的 HTML 文件，为这一次的特定任务而生。

这里的诀窍是：一定要以导出功能结尾 —— 一个 "复制为 JSON" 或 "复制为 prompt" 的按钮，把你在界面上做的所有操作转化回一段可以粘贴进 Claude Code 的内容。

Example prompts:

I need to reprioritize these 30 Linear tickets. Make me an HTML file with each ticket as a draggable card across Now / Next / Later / Cut columns. Pre-sort them by your best guess. Add a "copy as markdown" button that exports the final ordering with a one-line rationale per bucket.

Here's our feature flag config. Build a form-based editor for it，group flags by area，show dependencies between them，warn me if I enable a flag whose prerequisite is off. Add a "copy diff" button that gives me just the changed keys.

I'm tuning this system prompt. Make a side-by-side editor：editable prompt on the left with the variable slots highlighted，three sample inputs on the right that re-render the filled template live. Add a character/token counter and a copy button.

Use this for:

Reordering，triaging，or bucketing anything（tickets，test cases，feedback)

Editing structured config（feature flags，env vars，JSON/YAML with constraints)

Tuning prompts，templates，or copy with live preview

Curating datasets，approve/reject rows，tag examples，export the selection

Annotating a document，transcript，or diff and exporting the annotations

Picking values that are painful to express in text：colors，easing curves，crop regions，cron schedules，regexes.

Frequently Asked Questions

关于我转向 HTML 这件事，我跟很多人聊过，这里整理了几个反复被问到的问题。

Isn't it less token efficient?

Markdown 通常确实用的 token 更少，但我的体会是，HTML 带来的更强表达力，加上我真正去读它的概率大大提高，意味着我最终得到的整体产出质量更高。况且有了 Opus 4.7 的 100 万 token 上下文窗口，多出来的那点 token 消耗在上下文窗口里根本感觉不到。

When do you use markdown for now?

说实话，我现在几乎所有场景都不再用 Markdown 了 —— 不过我承认，我可能是站在 HTML 极端拥护者（HTML maximalist）这一端了。

How do I view the HTML file?

我一般就在浏览器里本地打开（你可以让 Claude 帮你打开），如果需要分享就上传到 S3 生成一个链接。

Doesn't this take longer to generate than markdown?

确实会更慢！HTML 的生成时间大概是 Markdown 的 2 到 4 倍。但我觉得这个结果完全值得等。

What about version control?

版本控制确实是 HTML 最大的劣势之一 ——HTML 的 diff 又乱又难看，跟 Markdown 比起来审查起来费劲多了。

How do I get Claude to match my taste / not make it ugly?

前端设计插件能帮助 Claude 生成更好看的 HTML 文件。但如果你想让它符合你公司自己的风格，可以先让 Claude 读你的代码库，生成一份设计系统（design system）HTML 文件，然后在生成其他 HTML 文件时把这份设计系统文件作为参考传进去。

Stay in the Loop

以上所有这些，归根到底，我觉得自己使用 HTML 的真正原因是：它让我感觉自己始终在掌控之中。我一度担心，因为自己已经不再深入阅读那些方案文档了，最终只能放手让 Claude 自行决策。

但现在我很高兴地说，使用 HTML 之后，我比以往任何时候都更觉得自己掌控着全局。希望你也能有同样的感受。
