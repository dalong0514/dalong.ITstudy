## 20260509Using-Claude-Code-The-Unreasonable-Effectiveness-of-HTML

使用 Claude Code：HTML 的不可思议的有效性

[X 上的 Thariq："Using Claude Code: The Unreasonable Effectiveness of HTML" / X](https://x.com/trq212/status/2052809885763747935)

[The unreasonable effectiveness of HTML — examples](https://thariqs.github.io/html-effectiveness/)

Markdown has become the dominant file format used by agents to communicate with us. It’s simple, portable, has some rich text capability and is easy for you to edit. Claude has even gotten surprisingly good at using ASCII to make diagrams inside of markdown files.

Markdown 已经成为 AI 智能体与我们沟通时最主流的文件格式。它简洁、通用，具备一定的富文本能力，也方便你直接动手编辑。Claude 甚至在 Markdown 文件中用 ASCII 字符画图表的能力已经好到让人惊讶了。

But as agents have become more and more powerful, I have felt that markdown has become a restricting format. I find it difficult to read a markdown file of more than a hundred lines. I want richer visualizations, color and diagrams and I want to be able to share them easily.

但随着智能体变得越来越强大，我开始感觉 Markdown 已经成了一种束缚。超过一百行的 Markdown 文件，我读起来就很吃力了。我想要更丰富的可视化表达 —— 颜色、图表 —— 而且我希望能方便地分享给别人。

I'm also increasingly not editing these files myself, but using them as specs, reference files, brainstorming outputs, etc. When I do make edits, I’m usually prompting Claude to edit them, which removes one of markdown’s largest benefits.

而且我现在越来越不自己动手编辑这些文件了，更多是把它们当作技术规格文档（spec）、参考资料、头脑风暴的产出来用。即使需要修改，我通常也是让 Claude 来改，这就让 Markdown "易于手动编辑" 这个最大的优势大打折扣了。

I’ve started preferring HTML as an output format instead of Markdown and increasingly see this being used by others on the Claude Code team, this is why.

我已经开始更倾向于用 HTML 而非 Markdown 作为输出格式，而且发现 Claude Code 团队里越来越多同事也在这么做。下面就来聊聊为什么。

(if you want to start with some examples, you can see a bunch here: https://thariqs.github.io/html-effectiveness, just be sure to come back and read more about why)

（如果你想先看看实际效果，这里有一堆示例：https://thariqs.github.io/html-effectiveness —— 不过记得看完了回来继续往下读。）

### Why HTML?

为什么选 HTML？

Information Density

信息密度

HTML can convey much richer information compared to markdown. It can of course do simple document structure like headers and formatting, but it can also represent all sorts of other information such as:

HTML 能传递的信息量比 Markdown 丰富得多。它当然可以做简单的文档结构，比如标题和文本格式，但除此之外还能表达各种各样的信息：

Tabular data using tables

用表格呈现结构化数据

Design data with CSS

用 CSS（层叠样式表）表达设计数据

Illustrations with SVG

用 SVG（可缩放矢量图形）绘制插图

Code snippets with script tags

用 script 标签嵌入代码片段

Interactions using HTML elements with javascript + CSS

用 HTML 元素配合 JavaScript + CSS 实现交互

Workflows using SVG and HTML

用 SVG 和 HTML 展示工作流

Spatial data using absolute positions and canvases

用绝对定位和 canvas 表达空间数据

Images using image tags

用 image 标签嵌入图片

I would go so far as to say that there is almost no set of information that Claude can read that you cannot fairly efficiently represent with HTML. This makes it a highly efficient way for the model to communicate in-depth information to you and for you to revie wit.

我甚至想说，几乎不存在 Claude 能读取、但 HTML 无法高效呈现的信息。所以 HTML 是模型向你深入传达信息的绝佳方式，也让你审阅起来更加高效。

I’ve found that in the absence of being able to do this, the model may do more inefficient things in markdown like ASCII diagrams or, my favorite, estimating colors with unicode characters like in this screenshot from Claude Code.

我发现，当无法使用 HTML 时，模型会退而求其次用 Markdown 做一些低效的表达 —— 比如 ASCII 图表，或者我个人最 "喜欢" 的操作：用 Unicode 字符来 "估算" 颜色。下面这张截图就是 Claude Code 在 Markdown 里试图展示颜色的样子。

Claude Code trying to show color in markdown

Visual Clarity & Ease of Reading

视觉清晰度与易读性

As Claude is able to do more complex work, it is also writing larger and larger specs and plans. In practice, I've found I tend to not actually read more than a 100-line markdown file, and I certainly am not able to get anyone else in my organization to read it.

随着 Claude 能处理的任务越来越复杂，它写出的技术规格文档和方案也越来越长。实际使用中我发现，超过 100 行的 Markdown 文件我基本不会通读，而要让团队里的其他人读完 —— 那更是不可能了。

But HTML documents are much easier to read, Claude can organize the structure visually to be ideal to navigate with tabs, illustrations, links, etc. It can even be mobile responsive so you can read it differently based on your form factor.

但 HTML 文档就好读多了。Claude 可以通过标签页、插图、链接等手段在视觉上组织文档结构，让浏览起来更顺畅。它甚至可以做响应式布局，让你在不同设备形态上有不同的阅读体验。

Ease of Sharing

易于分享

Markdown files are fairly hard to share since most browsers do not render them natively well. You often have to add them as attachments to emails or messages.

Markdown 文件其实挺难分享的，因为大多数浏览器并不能很好地原生渲染它们，你往往只能把文件当附件挂到邮件或消息里。

With HTML, as long as you upload the file (for example to S3), you can share the link easily. Your colleagues can open it wherever they wish and easily reference it.

而 HTML 就不同了 —— 只要把文件上传到某个地方（比如 S3（亚马逊云存储服务）），就能直接分享链接。你的同事可以随时随地打开，方便地引用参考。

The chance of someone actually reading your spec, report or PR writeup is much much higher if it’s in HTML.

你的技术规格文档、报告或 PR（Pull Request，拉取请求）说明如果是 HTML 格式，别人真正去读的概率会高出太多太多。

Two-way Interaction

双向交互

HTML can allow you to interact with the document, for example you might want to ask it to add sliders or knobs to adjust a design or allow you to tweak different options in the algorithm to see what happens. You can also ask it to let you copy these changes into a prompt to paste back into Claude Code.

HTML 能让你与文档进行交互。比如，你可以让 Claude 在文档里加入滑块或旋钮来调整设计方案，或者让你调节算法里的不同参数来观察效果变化。你还可以让 Claude 加一个功能，把这些修改复制成 prompt，方便你粘贴回 Claude Code 里使用。

Read more about my playgrounds post to see examples of this two way interaction: https://x.com/trq212/status/2017024445244924382

关于这种双向交互，可以看我之前写的 playgrounds 帖子，里面有很多例子：https://x.com/trq212/status/2017024445244924382

Data Ingestion

数据摄取能力

Why use Claude Code to make HTML files instead of ClaudeAI or Claude Design for example? One of the biggest reasons is all the context Claude Code can ingest.

为什么要用 Claude Code 来生成 HTML 文件，而不是用 ClaudeAI 或者 Claude Design 呢？最大的原因之一是 Claude Code 能获取的上下文信息量远超其他方式。

For example, when writing this article, I asked Claude Code to read through my code folder and find all the HTML files I’ve generated, group and categorize them and then make an HTML file with all diagrams representing each type. The diagrams you see in this article are a direct result of that.

举个例子，在写这篇文章的时候，我让 Claude Code 遍历我的代码文件夹，找出所有我之前生成的 HTML 文件，进行分组归类，然后生成一个包含各类型图表的 HTML 文件。你在这篇文章里看到的那些图表，就是这么来的。

Besides the file system, Claude Code can find additional context using your MCPs (like Slack, Linear, etc.), your web browser (with Claude in Chrome), your git history, etc.

除了文件系统之外，Claude Code 还可以通过 MCP（Model Context Protocol，模型上下文协议）工具（比如 Slack、Linear（项目管理工具）等）、你的浏览器（通过 Chrome 中的 Claude 插件）、你的 git 历史记录等等渠道获取更多上下文。

It’s Joyful

乐趣

Making HTML documents with Claude is just more fun and makes me feel more involved and invested in the creation, and that by itself is enough.

用 Claude 制作 HTML 文档就是更有意思、更让人享受 —— 让我在创作过程中更有参与感和投入感。光凭这一点，就足够了。

How to Get Started

如何开始

I’m a little bit afraid that people will read this article and turn it into a /html skill or something. While there might be some value in that, I want to emphasize that you don’t need to do much to get Claude to do this. You can just ask it to "make a HTML file" or "make a HTML artifact".

说实话，我有点担心大家看了这篇文章之后会马上把它做成一个 /html 技能之类的东西。虽然这样做可能有一定价值，但我想强调的是：让 Claude 生成 HTML 根本不需要什么复杂设置。你只需要告诉它 "make a HTML file" 或者 "make a HTML artifact" 就行了。

The trick is knowing what you want the artifact to do and how you might use it. You may over time make a skill, but for now I’d suggest just prompting from scratch to get a hang of how to use it in different cases.

关键在于你要清楚自己想让这个制品做什么、以及你打算怎么使用它。用久了你可能会把常用的模式沉淀成一个技能，但现在我建议先从零开始写 prompt，在各种场景中摸索出感觉。

### Use Cases

使用场景

To make this more concrete, I’ve made many different HTML files for different use cases. You can view all of them here: https://thariqs.github.io/html-effectiveness/ but here’s an overview.

为了让这些说法更具体，我针对不同的使用场景制作了很多 HTML 文件。你可以在这里查看所有示例：https://thariqs.github.io/html-effectiveness/ —— 下面是一个概览。

Specs, Planning & Exploration

规格设计、方案规划与探索

HTML is a rich canvas for Claude to dive into a problem. When I start working on a problem instead of a simple markdown plan I expect to make a web of HTML files. For example, I might start with asking Claude Code to brainstorm and create some explorations of different options. I would then ask it to expand more into one, maybe make mockups or code snippets. Finally, when I feel good I’ll ask it to write an implementation plan. When I’m happy with the plan I’ll create a new session and pass in all of these files for it to implement.

HTML 是 Claude 深入探索问题的丰富画布。当我开始着手一个问题时，我不再只写一份简单的 Markdown 方案，而是期待产出一系列互相关联的 HTML 文件。比如，我可能先让 Claude Code 进行头脑风暴，针对不同方案做一些探索性的呈现。然后让它在某个方向上深入展开，也许做一些原型图或代码片段。最后，等我觉得方向对了，再让它写出一份实施计划。当我对方案满意后，我会开一个新的会话，把所有这些文件传进去，让 Claude 据此实现代码。

When verifying I’ll also ask the verification agent to read in the files and it will have much broader context on what is needed.

在验证阶段，我也会让验证智能体读入这些文件，这样它就能对需求有更全面的理解。

Example Prompts:

示例 Prompt：

I'm not sure what direction to take the onboarding screen. Generate 6 distinctly different approaches — vary layout, tone, and density — and lay them out as a single HTML file in a grid so I can compare them side by side. Label each with the tradeoff it's making.

I'm not sure what direction to take the onboarding screen. Generate 6 distinctly different approaches — vary layout, tone, and density — and lay them out as a single HTML file in a grid so I can compare them side by side. Label each with the tradeoff it's making.

Create a thorough implementation plan in a HTML file, be sure to make some mockups, show data flow and add important code snippets I might want to review. Make it easy to read and digest.

Create a thorough implementation plan in a HTML file, be sure to make some mockups, show data flow and add important code snippets I might want to review. Make it easy to read and digest.

Use Cases:

适用场景：

Exploring other ways to implement something in code

探索代码的其他实现方式

Exploring multiple visual designs

探索多种视觉设计方案

Code Review & Understanding

代码审查与理解

Code can be difficult to read in a Markdown file. But with HTML we can render diffs, annotations, flowcharts, modules, etc. Use this to understand code that the agent has written, to get code review or to explain a PR to someone reviewing your code. I find this often works better than the default Github diff view, and I attach a HTML code explainer to every PR I make now.

在 Markdown 文件里阅读代码是一件很痛苦的事。但有了 HTML，我们可以渲染 diff、标注、流程图、模块关系图等等。你可以用这种方式来理解智能体写的代码，进行代码审查，或者向审查你代码的人解释一个 PR。我发现这往往比 GitHub 默认的 diff 视图好用得多 —— 现在我每发一个 PR 都会附上一份 HTML 格式的代码说明。

Example prompt:

示例 Prompt：

Help me review this PR by creating an HTML artifact that describes it. I'm not very familiar with the streaming/backpressure logic so focus on that. Render the actual diff with inline margin annotations, color-code findings by severity and whatever else might be needed to convey the concept well.

Help me review this PR by creating an HTML artifact that describes it. I'm not very familiar with the streaming/backpressure logic so focus on that. Render the actual diff with inline margin annotations, color-code findings by severity and whatever else might be needed to convey the concept well.

Use Cases:

适用场景：

Creating a PR

创建 PR

Reviewing a PR

审查 PR

Understanding a topic in Code

理解代码中的某个主题

Design & Prototypes

设计与原型

Claude Design is based on HTML because HTML is incredibly expressive at design, even if your end surface is not HTML. Claude can sketch out a design in HTML and then write it in your language of choice, be it React, Swift, etc.

Claude Design 本身就是基于 HTML 构建的，因为 HTML 在设计表达上拥有极强的能力 —— 哪怕你最终的目标平台不是 HTML。Claude 可以先用 HTML 画出设计草图，然后再用你选择的语言来实现，无论是 React、Swift 还是其他什么。

You can also prototype interactions, such as animations, actions, etc. Consider asking Claude to make sliders, knobs, etc. to tune in exactly what you’re looking for.

你还可以用 HTML 来做交互原型 —— 动画效果、操作反馈等等。试试让 Claude 加入滑块、旋钮之类的控件，帮你精确调整到想要的效果。

Example prompt:

示例 Prompt：

I want to prototype a new checkout button, when clicked it does a play animation and then turns purple quickly. Create a HTML file with several sliders and options for me to try different options on this animation, give me a copy button to copy the parameters that worked well.

I want to prototype a new checkout button, when clicked it does a play animation and then turns purple quickly. Create a HTML file with several sliders and options for me to try different options on this animation, give me a copy button to copy the parameters that worked well.

Use this for:

适用场景：

Creating design system artifacts

创建设计系统制品

Adjusting components

调整组件

Visualizing component libraries

可视化组件库

Prototyping Joyful Animations

制作有趣的动画原型

Reports, Research & Learning

报告、研究与学习

Claude Code is incredibly good at synthesizing information across multiple data sources and converting it into a report for readability. You can prompt Claude to search your Slack, your codebase, git history, the internet, etc. and use it to generate extremely readable reports for yourself, for leadership, for your team, etc.

Claude Code 极其擅长整合多个数据源的信息，并转化为可读性很高的报告。你可以让 Claude 去搜索你的 Slack、你的代码库、git 历史、互联网等等，然后用这些信息为你自己、为领导层、为团队生成极易阅读的报告。

You could assemble this in the form of a long HTML document, an interactive explainer or even a slideshow/deck. Ask Claude to use SVG for diagrams to help visualize it.

你可以把内容组织成一份详尽的 HTML 长文档、一个交互式的讲解页面，甚至是一套幻灯片。让 Claude 用 SVG 来画图表，能帮助你更好地可视化呈现信息。

For example, for my posts on prompt caching, I asked Claude to prepare an in-depth research file in HTML for me to read on all of our changes to prompt caching after reading the git history.

比如，在写关于 prompt caching（提示缓存）的那几篇帖子时，我就让 Claude 先读了 git 历史里所有跟 prompt caching 相关的改动，然后为我整理出一份深度 HTML 研究文档供我阅读。

Example prompt:

示例 Prompt：

I don't understand how our rate limiter actually works. Read the relevant code and produce a single HTML explainer page: a diagram of the token-bucket flow, the 3–4 key code snippets annotated, and a "gotchas" section at the bottom. Optimize it for someone reading it once.

I don't understand how our rate limiter actually works. Read the relevant code and produce a single HTML explainer page: a diagram of the token-bucket flow, the 3–4 key code snippets annotated, and a "gotchas" section at the bottom. Optimize it for someone reading it once.

Use this for:

适用场景：

Summarize how a feature works

总结某个功能的工作原理

Explain a concept to me

向我解释一个概念

Weekly status reports to your boss

给老板写周报

Incident reports to your leadership

给领导层写事故报告

SVG illustrations, flowcharts, technical diagrams, etc

SVG 插图、流程图、技术架构图等

Custom Editing Interfaces

自定义编辑界面

Sometimes it’s hard to describe what you want purely in a text box. In this case, I'll ask Claude to build me a throwaway editor for the exact thing I'm working on. Not a product, or a reusable tool, but a single HTML file, purpose-built for this one piece of data.

有时候，仅靠在文本框里打字，你很难准确描述你想要的东西。遇到这种情况，我会让 Claude 给我做一个一次性的编辑器 —— 专门为我当前手上这份数据量身定制。不是什么产品级的工具，也不是什么可复用的通用组件，就是一个单独的 HTML 文件，为这一次的特定任务而生。

The trick is always to end with an export: a "copy as JSON" or "copy as prompt" button that turns whatever I did in the UI back into something I can paste into Claude Code.

这里的诀窍是：一定要以导出功能结尾 —— 一个 "复制为 JSON" 或 "复制为 prompt" 的按钮，把你在界面上做的所有操作转化回一段可以粘贴进 Claude Code 的内容。

Example prompts:

示例 Prompt：

I need to reprioritize these 30 Linear tickets. Make me an HTML file with each ticket as a draggable card across Now / Next / Later / Cut columns. Pre-sort them by your best guess. Add a "copy as markdown" button that exports the final ordering with a one-line rationale per bucket.

I need to reprioritize these 30 Linear tickets. Make me an HTML file with each ticket as a draggable card across Now / Next / Later / Cut columns. Pre-sort them by your best guess. Add a "copy as markdown" button that exports the final ordering with a one-line rationale per bucket.

Here's our feature flag config. Build a form-based editor for it, group flags by area, show dependencies between them, warn me if I enable a flag whose prerequisite is off. Add a "copy diff" button that gives me just the changed keys.

Here's our feature flag config. Build a form-based editor for it, group flags by area, show dependencies between them, warn me if I enable a flag whose prerequisite is off. Add a "copy diff" button that gives me just the changed keys.

I'm tuning this system prompt. Make a side-by-side editor: editable prompt on the left with the variable slots highlighted, three sample inputs on the right that re-render the filled template live. Add a character/token counter and a copy button.

I'm tuning this system prompt. Make a side-by-side editor: editable prompt on the left with the variable slots highlighted, three sample inputs on the right that re-render the filled template live. Add a character/token counter and a copy button.

Use this for:

适用场景：

Reordering, triaging, or bucketing anything (tickets, test cases, feedback)

对任何东西进行重新排序、分级或分类（工单、测试用例、反馈）

Editing structured config (feature flags, env vars, JSON/YAML with constraints)

编辑结构化配置（功能开关、环境变量、有约束条件的 JSON/YAML）

Tuning prompts, templates, or copy with live preview

调优 prompt、模板或文案，带实时预览

Curating datasets, approve/reject rows, tag examples, export the selection

管理数据集：审批 / 拒绝行、打标签、导出选中内容

Annotating a document, transcript, or diff and exporting the annotations

为文档、转录文本或 diff 做标注，并导出标注结果

Picking values that are painful to express in text: colors, easing curves, crop regions, cron schedules, regexes.

挑选那些很难用文字描述的值：颜色、缓动曲线、裁剪区域、cron 表达式、正则表达式

Frequently Asked Questions

常见问题

I’ve been telling many people about how I’ve switched to HTML and I’ve seen a few repeated questions.

关于我转向 HTML 这件事，我跟很多人聊过，这里整理了几个反复被问到的问题。

Isn’t it less token efficient?

用 HTML 不是更费 token 吗？

While markdown often uses fewer tokens, I’ve found that the added expressiveness of HTML and the much higher likelihood of me reading it means I get overall better output. With the 1MM context window in Opus 4.7, the increased token usage is not really noticeable in the context window.

Markdown 通常确实用的 token 更少，但我的体会是，HTML 带来的更强表达力，加上我真正去读它的概率大大提高，意味着我最终得到的整体产出质量更高。况且有了 Opus 4.7 的百万 token 上下文窗口，多出来的那点 token 消耗根本感觉不到。

When do you use markdown for now?

你现在还用 Markdown 吗？

I have honestly stopped using markdown altogether for almost everything, but I’m probably far on the HTML maximalist side of things.

说实话，我现在几乎所有场景都不再用 Markdown 了 —— 不过我承认，我可能是站在 HTML 极端拥护者这一端了。

How do I view the HTML file?

怎么查看 HTML 文件？

I tend just open it in a browser locally (you can ask Claude to open it), or upload to S3 if you want a shareable link.

我一般就在浏览器里本地打开（你可以让 Claude 帮你打开），如果需要分享就上传到 S3 生成一个链接。

Doesn't this take longer to generate than markdown?

生成 HTML 不是比 Markdown 更慢吗？

This does take longer! HTML can take 2-4x longer than Markdown, but I've found the results are worth it.

确实会更慢！HTML 的生成时间大概是 Markdown 的 2 到 4 倍。但我觉得这个结果完全值得等。

What about version control?

版本控制怎么办？

This is honestly one of the biggest downsides of HTML, HTML diffs are noisy and hard to review compared to Markdown.

版本控制确实是 HTML 最大的劣势之一 ——HTML 的 diff 又乱又难看，跟 Markdown 比起来审查起来费劲多了。

How do I get Claude to match my taste / not make it ugly?

怎么让 Claude 做出来的 HTML 符合我的审美？

The frontend design plugin helps Claude make good HTML files. But to match your own companies style, you can create a single design system HTML file by pointing Claude at your codebase. You can then use that design system file as a reference for other html files.

前端设计插件能帮助 Claude 生成更好看的 HTML 文件。但如果你想让它符合你公司自己的风格，可以先让 Claude 读你的代码库，生成一份设计系统 HTML 文件，然后在生成其他 HTML 文件时把这份设计系统文件作为参考传进去。

Stay in the Loop

始终在掌控之中

All of the above is to say that I think the real reason I use HTML is that I feel much more in the loop with Claude. I had begun to fear that because I had stopped reading plans in depth I would simply have to leave Claude to make its choices.

以上所有这些，归根到底，我觉得自己使用 HTML 的真正原因是：它让我感觉自己始终在掌控之中。我一度担心，因为自己已经不再深入阅读那些方案文档了，最终只能放手让 Claude 自行决策。

But I am happy to say instead that I feel more in the loop than ever before when using HTML. I hope you do too.

但现在我很高兴地说，使用 HTML 之后，我比以往任何时候都更觉得自己掌控着全局。希望你也能有同样的感受。
