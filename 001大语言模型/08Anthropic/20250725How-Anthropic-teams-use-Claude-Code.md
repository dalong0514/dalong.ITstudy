## How-Anthropic-teams-use-Claude-Code

[How Anthropic teams use Claude Code \ Anthropic](https://www.anthropic.com/news/how-anthropic-teams-use-claude-code)

Jul 24, 2025

Agentic coding tools like Claude Code help developers accelerate workflows, automate repetitive tasks, and tackle complex programming projects. As the field evolves, we're learning about new applications everyday from users, including our own employees.

AI 智能体（AI Agent）编程工具，例如 Claude Code，能够帮助开发者加快工作流程、自动化处理重复性任务，并应对复杂的编程项目。随着这个领域不断发展，我们每天都能从用户（包括我们自己的员工）那里了解到各种新的应用。

To learn more, we sat down with employees across Anthropic to understand how they use Claude Code at work.

为了深入了解，我们与 Anthropic 的员工进行了交流，旨在理解他们在日常工作中是如何使用 Claude Code 的。

While many of their use cases were predictable—debugging, navigating codebases, managing workflows—others surprised us. Lawyers built phone tree systems. Marketers generated hundreds of ad variations in seconds. Data scientists created complex visualizations without knowing JavaScript.

尽管许多使用场景都在意料之中 —— 比如调试代码、在代码库中导航以及管理工作流程 —— 但另一些应用则出乎我们的意料。例如，律师竟然搭建了电话树系统；营销人员能在短短几秒钟内生成数百种广告变体；而数据科学家们，即使不了解 JavaScript，也能创建出复杂的图表可视化。

The pattern became clear: agentic coding isn't just accelerating traditional development. It's dissolving the boundary between technical and non-technical work, turning anyone who can describe a problem into someone who can build a solution.

这种趋势越来越明显：代理式编程（agentic coding）不仅仅是加速传统的开发流程。它正在模糊技术工作与非技术工作之间的界限，让任何能够描述问题的人，都能摇身一变成为解决方案的构建者。

Here's what we learned.

以下是我们的发现。

### 01. Codebase navigation and understanding

代码库导航和理解

Teams across the company use Claude Code to help new hires and even long-time employees get up to speed on our codebases.

公司各团队使用 Claude Code 来帮助新员工甚至资深员工快速了解并掌握我们的代码库。

New data scientists on our Infrastructure team feed Claude Code their entire codebase to get productive quickly. Claude reads the codebase's CLAUDE.md files, identifies relevant ones, explains data pipeline dependencies, and shows which upstream sources feed into dashboards, replacing traditional data catalog tools.

我们基础设施团队的新数据科学家会把整个代码库提供给 Claude Code，从而迅速提高工作效率。Claude 能读取代码库中的 CLAUDE.md 文件，识别出其中的关键信息，解释数据管道之间的依赖关系，并清晰展示哪些上游数据源为仪表盘提供支持，这替代了传统数据目录工具的功能。

Our Product Engineering team refers to Claude Code as their "first stop" for any programming task. They ask it to identify which files to examine for bug fixes, features, or analysis, eliminating the time-consuming process of manually gathering context before building new features.

我们的产品工程团队将 Claude Code 视为他们处理任何编程任务时的「首选」。他们会要求 Claude Code 识别哪些文件需要检查，无论是为了修复错误、开发新功能还是进行分析，这省去了在构建新功能之前手动收集相关背景信息所耗费的大量时间。

### 02. Testing and code review

测试和代码审查

Agentic coding tools are particularly popular for their ability to automate two critical but tedious programming tasks: writing unit tests and reviewing code.

智能体编程工具之所以特别受欢迎，是因为它们能够自动化编写单元测试和审查代码这两个关键但繁琐的编程任务。

The Product Design team uses Claude Code to write comprehensive tests for new features. They've automated Pull Request comments through GitHub Actions, with Claude handling formatting issues and test case refactoring automatically.

产品设计团队使用 Claude Code 编写新功能的全面测试。他们已经通过 GitHub Actions 实现了 Pull Request 评论的自动化，其中 Claude 会自动处理格式问题和测试用例的重构。

The Security Engineering team transformed their workflow from "design doc → janky code → refactor → give up on tests" to asking Claude for pseudocode, guiding it through test-driven development, and checking in periodically. This results in more reliable, testable code.

安全工程团队将他们的工作流程，从过去「先写设计文档 → 再编写粗糙的代码 → 然后进行重构 → 最后放弃测试」的模式，转变为向 Claude 寻求伪代码（pseudocode），并引导它进行测试驱动开发（test-driven development），同时定期进行检查。这种新方法使得代码更加可靠，也更容易进行测试。

Agentic coding can also be used to translate tests into other programming languages. For instance, when the Inference team needs to test functionality in unfamiliar languages like Rust, they explain what they want to test and Claude writes the logic in the native language of the codebase.

智能体式编程（Agentic coding）也可以用来将测试移植到其他编程语言。例如，当 Inference team 需要在 Rust 这样不熟悉的语言中测试功能时，他们会说明需要测试的功能，然后 Claude 就会用该代码库所使用的编程语言编写测试逻辑。

### 03. Debugging and troubleshooting

调试与故障排除

Production issues demand quick resolution, but trying to reason about unfamiliar code under pressure often leads to delays. For many teams at the company, Claude Code accelerates diagnosis and fixes by analyzing stack traces, documentation, and system behavior in real-time.

生产环境中的问题需要快速解决，但在巨大压力下试图理解并分析不熟悉的代码，往往会拖延解决时间。对于公司里的许多团队来说，Claude Code 通过实时分析堆栈跟踪（stack traces）、文档和系统行为（system behavior），能够显著加快问题诊断和修复的速度。

During incidents, the Security Engineering team feeds Claude Code stack traces and documentation to trace control flow through the codebase. Problems that typically take 10-15 minutes of manual scanning now resolve 3x as quickly.

在发生安全事件时，安全工程团队会将堆栈跟踪（stack traces）和文档提供给 Claude Code，以便追踪代码库的控制流。那些通常需要 10-15 分钟手动排查的问题，现在解决速度提高了 3 倍。

With Claude Code, the Product Engineering team gained confidence to tackle bugs in unfamiliar codebases. They ask Claude: "Can you fix this bug? This is the behavior I'm seeing" and review the proposed solution without needing to rely on other engineering teams for assistance.

借助 Claude Code，产品工程团队更有信心处理不熟悉的代码库中的错误。他们会问 Claude：「你能修复这个错误吗？我看到的是这种现象」，然后审查 Claude 提出的解决方案，而无需依赖其他工程团队的协助。

In one instance, when Kubernetes clusters stopped scheduling pods, the Data Infrastructure team used Claude Code to diagnose the issue. They fed it dashboard screenshots, and Claude guided them menu-by-menu through Google Cloud's UI until they found pod IP address exhaustion. Claude then provided the exact commands to create a new IP pool and add it to the cluster, saving them 20 minutes of valuable time during a system outage.

有一次，当 Kubernetes 集群停止调度（scheduling）pod 时，数据基础设施团队利用 Claude Code 来诊断问题。他们将仪表板截图提供给 Claude，Claude 引导他们一步步操作 Google Cloud 的用户界面（UI），直到他们发现 pod IP 地址耗尽（IP address exhaustion）。随后，Claude 提供了具体的命令，指导他们创建新的 IP 池并将其添加到集群中，这在系统中断期间为他们节省了 20 分钟的宝贵时间。

### 04. Prototyping and feature development

原型设计和功能开发

Building new features traditionally requires deep technical knowledge and significant time investment. Claude Code enables rapid prototyping and even full application development, letting teams validate ideas quickly regardless of their programming expertise.

在过去，开发新功能通常需要深厚的技术知识和耗费大量时间。而 Claude Code 则支持快速原型设计乃至完整的应用程序开发，让团队不论编程专业技能如何，都能迅速验证他们的创意。

Members of the Product Design team would feed Figma design files to Claude Code and then set up autonomous loops where Claude Code writes the code for the new feature, runs tests, and iterates continuously. They give Claude abstract problems, let it work autonomously, then review solutions before final refinements. In one case, they had Claude build Vim key bindings for itself with minimal human review.

产品设计团队的成员会将 Figma 设计文件提供给 Claude Code，然后设置自主循环，让 Claude Code 在其中为新功能编写代码、运行测试并持续迭代。他们向 Claude 提出抽象问题，让其自主地开展工作，然后在最终优化之前审查解决方案。在一个案例中，他们让 Claude 在最少人工审查的情况下，为自己构建了 Vim 键绑定。

With Claude Code, the Product Design team discovered an unexpected use: mapping out error states, logic flows, and system statuses to identify edge cases during design rather than discovering them in development. This fundamentally improves their initial design quality and saves them hours of debugging later on.

借助 Claude Code，产品设计团队发现了一个意想不到的妙用：他们能梳理出各种错误状态、逻辑流程和系统运行状态，从而在设计阶段就能识别出各种边缘情况，而不是等到开发阶段才发现。这从根本上提升了他们初期的设计质量，也为他们省去了后续数小时的调试工作。

Despite not being fluent in TypeScript, data scientists use Claude Code to build entire React applications for visualizing RL model performance. After one-shot prompting in a sandbox environment, the tool writes entire TypeScript visualizations from scratch without understanding the code themselves. Given the simplicity of the task, if the first prompt isn't sufficient, they'll make slight tweaks and try again.

尽管数据科学家们并不精通 TypeScript，但他们依然能够利用 Claude Code 来构建完整的 React 应用程序，以可视化 RL 模型（RL model）的性能。在沙盒环境中，仅通过一次提示（one-shot prompting），Claude Code 便能从零开始编写出完整的 TypeScript 可视化代码，而数据科学家自身无需理解代码。鉴于这类任务的简单性，如果第一次提示的结果不尽如人意，他们会稍作调整，然后再次尝试。

### 05. Documentation and knowledge management

文档和知识管理

Technical documentation often sits scattered across wikis, code comments, and team members' heads. Claude Code consolidates this knowledge via MCP and CLAUDE.md files into accessible formats, making expertise available to everyone who needs it.

技术文档往往散落在维基（wikis）、代码注释以及团队成员的个人经验中。Claude Code 通过 MCP 和 CLAUDE.md 文件将这些知识整合到易于访问的格式中，让每个需要它的人都能获取这些专业知识。

Inference team members without ML backgrounds depend on Claude to explain model-specific functions. What normally requires an hour of Google searching now takes 10-20 minutes—an 80% reduction in research time.

那些没有机器学习（ML）背景的推理团队成员，现在可以依靠 Claude 来解释特定模型的功能。这项工作通常需要一小时的 Google 搜索才能完成，而现在只需 10-20 分钟，相当于将研究时间缩短了 80%。

The Security Engineering team has Claude ingest multiple documentation sources to create markdown runbooks and troubleshooting guides. These condensed documents become context for debugging real production issues, which is often more efficient than searching through full knowledge bases.

安全工程团队会利用 Claude 处理多种文档来源，从而生成 Markdown 格式的操作手册和故障排除指南。这些经过提炼的文档，能够为调试实际生产问题提供所需的背景信息和参考，相比于在庞大的知识库中漫无目的地搜索，这种方式通常更为高效。

## 06. Automation and workflow optimization

自动化和工作流优化

Agentic coding tools help teams build custom automation that would traditionally require dedicated developer resources or expensive software.

AI 智能体（Agentic）编码工具能帮助团队构建定制化的自动化解决方案，而这些方案在过去往往需要投入专门的开发人员资源，或是购买昂贵的软件才能实现。

The Growth Marketing team built an agentic workflow that processes CSV files with hundreds of ads, identifies underperformers, and generates new variations within strict character limits. Using two specialized sub-agents, the system generates hundreds of new ads in minutes instead of hours.

增长营销团队构建了一个智能体工作流（agentic workflow），它能够处理包含数百个广告的 CSV 文件，识别出那些表现不佳的广告，并在严格的字符限制内生成新的广告变体。利用两个专门的子智能体（sub-agents），这套系统仅需数分钟而非数小时，就能生成数百个新广告。

They also developed a Figma plugin that identifies frames and programmatically generates up to 100 ad variations by swapping headlines and descriptions, reducing hours of copy-pasting to half a second per batch of ads.

他们还开发了一个 Figma 插件（plugin），这个插件可以识别设计框架（frames），并通过替换标题和描述，自动生成多达 100 种广告变体。这项功能将原本需要数小时的复制粘贴工作，缩短至每批广告仅需半秒。

In a particularly unique use case, the Legal team created prototype "phone tree" systems to help team members connect with the right lawyer at Anthropic, demonstrating how departments can build custom tools without traditional development resources.

在一个非常独特的应用场景中，Anthropic 的法务团队创建了原型「电话树系统（phone tree systems）」，旨在帮助团队成员联系到对口的律师。这表明即使没有传统的开发资源，各部门也能自行构建定制工具。

### 07. Unlocking new possibilities with Claude Code

借助 Claude Code 探索新可能

These stories reveal a pattern: Claude Code works best when you focus on the human workflows that it can augment. The most successful teams treat Claude Code as a thought partner rather than a code generator.

这些案例揭示了一个共同的模式：Claude Code 在你专注于它能赋能（augment）人类工作流程时，才能发挥最佳效果。那些最成功的团队，都将 Claude Code 视为一个思想伙伴（thought partner），而非仅仅是一个代码生成器（code generator）。

They explore possibilities, prototype rapidly, and share discoveries across technical and non-technical users. This collaborative approach between humans and AI creates opportunities we're only beginning to understand.

它们探索各种可能性，快速搭建原型，并将新发现分享给技术和非技术用户。这种人与 AI（Artificial Intelligence）之间协作的方式，正在创造我们才刚刚开始理解的全新机遇。

Learn more about how Anthropic teams use Claude Code.

了解更多关于 Anthropic 团队如何使用 Claude Code。

已下载 PDF 文档「20250822How-Anthropic-teams-use-Claude-Code_v2」。（2025-08-22）