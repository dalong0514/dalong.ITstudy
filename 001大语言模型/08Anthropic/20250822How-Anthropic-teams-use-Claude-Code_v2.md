## 20250822How-Anthropic-teams-use-Claude-Code_v2

Anthropic's internal teams are transforming their workflows with Claude Code, enabling developers and non-technical staff to tackle complex projects, automate tasks, and bridge skill gaps that previously limited their productivity.

Anthropic 的内部团队正在利用 Claude Code 改造其工作流程，让开发人员和非技术员工都能应对复杂的项目，实现任务自动化，并弥合此前限制其生产力的技能鸿沟。

Through interviews with our own Claude Code power users, we’ve gathered insights on how different departments leverage Claude Code, its impact on their work, and tips for other organizations considering adoption.

我们采访了 Claude Code 的资深用户，深入了解了不同部门如何利用 Claude Code，它对各部门工作产生的影响，以及为其他考虑引入该工具的组织提供了实用建议。

### 01. Claude Code for data infrastructure

Claude Code 助力数据基础设施建设

The Data Infrastructure team organizes all business data for teams across the company. They use Claude Code for automating routine data engineering tasks, troubleshooting complex infrastructure issues, and creating documented workflows for technical and non-technical team members to access and manipulate data independently.

数据基础设施团队负责整合并管理公司内部各团队的所有业务数据。他们利用 Claude Code 来自动化日常数据工程任务，解决复杂的基础设施问题，并为技术和非技术团队成员创建规范的工作流程文档，让他们能够独立地访问和操作数据。

##### Main Claude Code use cases

Claude Code 的主要应用场景

Kubernetes debugging with screenshots

通过截图调试 Kubernetes

When Kubernetes clusters went down and weren’t scheduling new pods, the team used Claude Code to diagnose the issue. They fed screenshots of dashboards into Claude Code, which guided them through Google Cloud’s UI menu by menu until they found a warning indicating pod IP address exhaustion. Claude Code then provided the exact commands to create a new IP pool and add it to the cluster, bypassing the need to involve networking specialists.

当 Kubernetes（Kubernetes）集群发生故障，无法调度新的 pod（pod）时，团队利用 Claude Code 来诊断问题。他们将仪表盘的截图输入给 Claude Code，它一步步引导团队在 Google Cloud（Google Cloud）的用户界面（UI）中进行操作，最终发现了一条指示 pod IP 地址耗尽的警告。随后，Claude Code 直接提供了创建新 IP 地址池（IP pool）并将其添加到集群的精确命令，从而省去了咨询网络专家（networking specialists）的环节。

Plain text workflows for finance team

财务团队的纯文本工作流（plain text workflows）

The team showed finance team members how to write plain text files describing their data workflows, then load them into Claude Code to get fully automated execution. Employees with no coding experience could describe steps like “query this dashboard, get information, run these queries, produce Excel output,” and Claude Code would execute the entire workflow, including asking for required inputs like dates.

这个团队向财务部门的成员展示了如何通过编写纯文本文件来描述他们的数据处理流程，然后将这些文件导入到 Claude Code 中，从而实现流程的全自动化执行。即使是没有编程经验的员工，也能清晰地描述他们的操作步骤，比如「查询这个仪表盘，获取所需信息，运行这些查询，并生成 Excel 报告」—— 而 Claude Code 则会负责执行整个流程，甚至包括主动提示并要求用户输入像日期这样的必要信息。

Codebase navigation for new hires

新员工如何熟悉代码库

When new data scientists join the team, they’re directed to use Claude Code to navigate their massive codebase. Claude Code reads their Claude.md files (documentation), identifies relevant files for specific tasks, explains data pipeline dependencies, and helps newcomers understand which upstream sources feed into dashboards. This replaces traditional data catalogs and discoverability tools.

当新的数据科学家加入团队时，他们会使用 Claude Code 来探索和管理其庞大的代码库。Claude Code 会读取他们的 Claude.md 文件（即说明文档），找出特定任务相关的代码文件，解释数据管道（data pipeline）的依赖关系，并帮助新员工理解哪些上游数据源为仪表板（dashboard）提供数据。这项工具成功取代了传统的数据目录和发现工具。








End-of-session documentation updates

The team asks Claude Code to summarize completed work sessions and suggest improvements at the end of each task. This creates a continuous improvement loop where Claude Code helps refine the Claude.md documentation and workflow instructions based on actual usage, making subsequent iterations more effective.

工作会话结束后更新文档团队要求 Claude Code 在每项任务结束时，总结已完成的工作会话并提出改进建议。这形成了一个持续改进的循环：Claude Code 根据实际使用情况，协助完善 Claude.md 文档和工作流程指令，从而让后续的迭代更加高效。

Parallel task management across multiple instances

When working on long-running data tasks, they open multiple instances of Claude Code in different repositories for different projects. Each instance maintains full context, so when they switch back after hours or days, Claude Code remembers exactly what they were doing and where they left off, enabling true parallel workflow management without context loss.

跨多个实例并行管理任务当开发者需要处理耗时较长的数据任务时，他们通常会在不同的代码库中为不同的项目启动多个 Claude Code 实例。每个实例都能完整地保留工作上下文（Context）。因此，即使开发者在数小时或数天后切换回某个 Claude Code 实例，它也能精确地「记住」之前的工作内容和暂停位置，从而实现真正意义上的并行工作流管理，并且完全不会丢失任何上下文信息。

### Claude Code for data infrastructure

Team impact

### Claude 代码在数据基础设施中的应用对团队的影响

Resolved infrastructure problems without specialized expertise

Resolved Kubernetes cluster issues that would normally require pulling in systems or networking team members, using Claude Code to diagnose problems and provide exact fixes.

无需专业技能也能解决基础设施难题我们利用 Claude Code 诊断问题并提供了精确的解决方案，从而解决了通常需要系统或网络团队成员介入的 Kubernetes 集群问题。

Accelerated onboarding

New data analysts and team members can quickly understand complex systems and contribute meaningfully without extensive guidance.

加速上手新的数据分析师和团队成员无需过多指导，就能迅速理解复杂的系统，并立即做出有价值的贡献。

Enhanced support workflow

Can process much larger data volumes and identify anomalies (like monitoring 200 dashboards) that would be impossible for humans to review manually.

优化后的支持工作流程现在能够处理远超以往的数据量，并能轻松识别各种异常（例如同时监控 200 个仪表板），这是人类手动审查根本无法完成的任务。

Enabled cross-team self-service

Finance teams with no coding experience can now execute complex data workflows independently.

让跨团队自助服务成为可能现在，即使没有编程经验的财务团队也能独立完成复杂的数据处理任务。

Top tips from the Data Infrastructure team

Write detailed Claude.md files

数据基础设施团队的实用技巧撰写详细的 Claude.md 文件

The better you document your workflows, tools, and expectations in Claude.md files, the better Claude Code performs. This made Claude Code excel at routine tasks like setting up new data pipelines when you have existing patterns.

你如果在 Claude.md 文件中将工作流程、工具和预期目标记录得越详细，Claude Code 的表现就会越出色。这让 Claude Code 在执行日常任务时表现卓越，例如当你有现有模式可循时，它能高效地搭建新的数据管道（data pipelines）。

Use MCP servers instead of CLI for sensitive data

They recommend using MCP servers rather than the BigQuery CLI to maintain better security control over what Claude Code can access, especially for handling sensitive data that requires logging or has potential privacy concerns.

使用 MCP 服务器而非 CLI 处理敏感数据他们建议使用 MCP 服务器而不是 BigQuery CLI，以便对 Claude Code 的访问权限保持更好的安全控制。这一点对于需要日志记录或存在潜在隐私风险的敏感数据尤为重要。

Share team usage sessions

The team held sessions where members demonstrated their Claude Code workflows to each other. This helped spread best practices and showed different ways to use the tool they might not have discovered on their own.

分享团队使用经验团队组织了多场交流会，成员们在会上互相演示了他们使用 Claude Code 的工作流程（workflow）。这不仅帮助大家推广了最佳实践，还展示了许多他们可能凭一己之力难以发现的工具使用方法。

### Claude Code for product development

The Claude Code team uses their own product to build updates to Claude Code, expanding the product’s enterprise capabilities and agentic loop functionalities.

### Claude Code 用于产品开发

Claude Code 团队通过使用他们自己的产品，为 Claude Code 构建更新，从而扩展了该产品的企业级能力和 AI 智能体（AI Agent）循环功能。

Main Claude Code use cases

Fast prototyping with auto-accept mode

Claude Code 的主要应用场景利用「自动接受模式」进行快速原型设计

Engineers use Claude Code for rapid prototyping by enabling “auto-accept mode” (shift $^ +$ tab) and setting up autonomous loops where Claude writes code, runs tests, and iterates continuously. They give Claude abstract problems they’re unfamiliar with, let it work autonomously, then review thereview the $80\%$ complete solution before taking over for final refinements. Teams emphasize starting from a clean git state and committing checkpoints regularly so they can easily revert any incorrect changes if Claude goes off track.

工程师使用 Claude Code 进行快速原型设计，具体方法是启用「自动接受模式」(shift $^ +$ tab），并设置自主循环，让 Claude 编写代码、运行测试并持续迭代。他们将自己不熟悉的抽象问题交给 Claude，让它自主工作，然后审查完成了 $80\%$ 的解决方案，再接手进行最后的精修。团队强调要从一个纯净的 git 环境开始，并定期提交检查点（checkpoint），这样一旦 Claude 出现偏差，他们就能轻松回滚（revert）任何不正确的更改。

Synchronous coding for core features

For more critical features touching the application’s business logic, the team works synchronously with Claude Code, giving detailed prompts with specific implementation instructions. They monitor the process in real-time to ensure code quality, style guide compliance, and proper architecture while letting Claude handle the repetitive coding work.

核心功能的协同开发对于涉及应用程序业务逻辑（business logic）的关键功能，团队会与 Claude Code（Claude Code）协同开发，提供详细的提示和具体的实现指令。他们实时监控整个编码过程，以确保代码质量、符合风格指南并拥有正确的架构，同时将重复性的编码工作交给 Claude 处理。

Building Vim mode

One of their most successful async projects was implementing Vim key bindings for Claude Code. They asked Claude to build the entire feature (despite it not being a priority), and roughly $70\%$ of the final implementation came from Claude’s autonomous work, requiring only a few iterations to complete.

构建 Vim 模式他们最成功的异步项目（async project）之一，是为 Claude Code 集成 Vim 键绑定。尽管这并非优先事项，他们仍让 Claude 负责构建整个功能，最终大约 $70\%$ 的实现工作都由 Claude 自主完成，仅经过几次迭代就大功告成。

Test generation and bug fixes

They use Claude Code to write comprehensive tests after implementing features and handle simple bug fixes identified in pull request reviews. They also leverage GitHub Actions integration to have Claude automatically address Pull Request comments like formatting issues or function renaming.

测试的生成与错误的修复在功能实现之后，他们会利用 Claude Code（一种代码生成工具）来编写全面的测试，并处理在拉取请求（Pull Request）审查中发现的简单错误。此外，他们还借助 GitHub Actions（GitHub 提供的自动化工具）的集成功能，让 Claude 自动处理 Pull Request 中的评论，例如解决格式问题或函数重命名等。

Codebase exploration

When working with unfamiliar codebases (like the monorepo or API side), the team uses Claude Code to quickly understand how systems work. Instead of waiting for Slack responses, they ask Claude directly for explanations and code references, saving significant time in context switching.

代码库探索当团队面对不熟悉的代码库时（例如，单体仓库（monorepo）或 API 端（API side)），他们会利用 Claude Code 来快速理解系统是如何运作的。这样一来，他们就不用苦等 Slack 上的回复，而是可以直接向 Claude 提问，获取解释和代码引用，从而显著节省了上下文切换（context switching）的时间。

### Claude Code for product development

Team impact

### Claude 代码在产品开发中的应用团队影响

Faster feature implementation

Successfully implemented complex features like Vim mode with $70\%$ of code written autonomously by Claude.

加速功能开发成功实现了复杂功能，例如 Vim 模式，其中 $70\%$ 的代码由 Claude 自主编写。

Improved development velocity

Can rapidly prototype features and iterate on ideas without getting bogged down in implementation details.

提升开发速度开发者可以快速开发功能原型，并不断迭代各种构思，而无需纠缠于实现细节。

Enhanced code quality through automated testing

Claude generates comprehensive tests and handles routine bug fixes, maintaining high standards while reducing manual effort.

通过自动化测试提升代码质量

Claude 不仅能生成全面的测试用例，还能处理常规的错误修复工作，在保持高标准的同时，大大减少了人工操作的投入。

Better codebase exploration

Team members can quickly understand unfamiliar parts of the monorepo without waiting for colleague responses.

优化代码库探索团队成员能迅速理解单体仓库（monorepo）中不熟悉的代码部分，无需等待同事的答复。

Top tips from the Claude Code team

Create self-sufficient loops

来自 Claude Code 团队的核心建议构建独立自主的循环（Self-sufficient Loops)

Set up Claude to verify its own work by running builds, tests, and lints automatically. This allows Claude to work longer autonomously and catch its own mistakes, especially effective when you ask Claude to generate tests before writing code.

通过自动运行构建（builds）、测试（tests）和代码检查（lints），可以配置 Claude 来验证它自己的工作。这让 Claude 能够更长时间地自主运行，并及时发现自身的错误。当你要求 Claude 在编写代码之前先生成测试时，这种方法尤其有效。

Develop task classification intuition

Learn to distinguish between tasks that work well asynchronously (peripheral features, prototyping) versus those needing synchronous supervision (core business logic, critical fixes). Abstract tasks on the product’s edges can be handled with “auto-accept mode,” while core functionality requires closer oversight.

培养任务分类的直觉你需要学会区分哪些任务更适合异步（非同步）处理（比如产品的外围功能或原型设计），而哪些任务则需要同步（实时）监督（例如核心业务逻辑或紧急修复）。对于产品那些不那么核心、相对抽象的任务，我们可以采用「自动接受模式」来处理；但涉及到核心功能时，就必须进行更严格、更细致的监督了。

Form clear, detailed prompts

When components have similar names or functions, be extremely specific in your requests. The better and more detailed your prompt, the more you can trust Claude to work independently without unexpected changes to the wrong parts of the codebase.

编写清晰、详细的提示词当组件具有相似的名称或功能时，你的请求务必极其具体。你的提示词越清晰详细，就越能放心地让 Claude 独立完成工作，避免对代码库中不相关的部分进行意外修改。

### Claude Code for security engineering

The Security Engineering team focuses on securing the software development lifecycle, supply chain security, and development environment security. They use Claude Code extensively for writing and debugging code.

### Claude Code 在安全工程中的应用安全工程团队（Security Engineering team）的核心工作是确保软件开发生命周期（software development lifecycle）、供应链安全（supply chain security）和开发环境安全（development environment security）。他们广泛利用 Claude Code 这一工具来编写和调试代码，从而提升上述领域的安全性。

Main Claude Code use cases

Complex infrastructure debugging

Claude Code 主要应用场景对复杂基础设施进行调试

When working on incidents, they feed Claude Code stack traces and documentation, asking it to trace control flow through the codebase. This significantly reduces time-to-resolution for production issues, allowing them to understand problems that would normally take 10-15 minutes of manual code scanning in about 5 minutes.

在处理事故时，他们会将堆栈跟踪（stack traces）和相关文档提供给 Claude Code，并让它追踪代码库（codebase）中的控制流（control flow）。这大大缩短了解决生产问题所需的时间，原本需要人工扫描 10 到 15 分钟才能理解的问题，现在大约 5 分钟就能弄明白。

Terraform code review and analysis

For infrastructure changes requiring security approval, they copy Terraform plans into Claude Code to ask “what’s this going to do? Am I going to regret this?” This creates tighter feedback loops and makes it easier for the security team to quickly review and approve infrastructure changes, reducing bottlenecks in the development process.

Terraform 代码审查和分析对于需要安全批准的基础设施变更，他们会将 Terraform 计划复制到 Claude Code 中，并提出这样的问题：「这会产生什么影响？我们会不会因此后悔？」这样做建立起了更紧密的反馈循环，让安全团队能更便捷地快速审查和批准基础设施变更，从而有效减少了开发过程中的瓶颈。

Documentation synthesis and runbooks

They have Claude Code ingest multiple documentation sources and create markdown runbooks, troubleshooting guides, and overviews. They use these condensed documents as context for debugging real issues, creating a more efficient workflow than searching through full knowledge bases.

文档整理与运行手册他们让 Claude Code 读取多个文档源，并生成 markdown 格式的运行手册、故障排除指南和内容概述。这些精简的文档被他们用来作为调试实际问题的参考信息，从而建立了一种比在整个知识库中搜索更高效的工作流程。

Test-driven development workflow

Instead of their previous “design doc janky code refactor give up on tests” pattern, they now ask Claude Code for pseudocode, guide it through test-driven development, and periodically check in to steer it when stuck, resulting in more reliable and testable code.

测试驱动开发工作流他们不再沿用过去那种「先写设计文档，再敲出粗糙代码，接着重构一番，最终却放弃测试」的开发模式。现在，他们会请 Claude Code 生成伪代码（pseudocode），然后引导它完成测试驱动开发（Test-driven development）。当 Claude Code 遇到难题时，开发人员还会定期介入并给予指导，从而最终产出更可靠、更易于测试的代码。

Context switching and project onboarding

When contributing to existing projects like “dependant” (a web application for security approval workflows), they use Claude Code to write, review, and execute specifications written in markdown and stored in the codebase, enabling meaningful contributions within days instead of weeks.

上下文切换（Context switching）与项目上手（project onboarding)

在参与「dependant」这类现有项目时（「dependant」是一个用于安全审批工作流的网页应用程序），开发团队会使用 Claude Code 来编写、审查并执行那些用 markdown 格式撰写并存储在代码库（codebase）中的规范（specifications）。这样做的好处是，可以让新成员在短短几天内，而非数周之内，就能对项目做出实质性的贡献。

Team impact

Reduced incident resolution time

团队影响缩短事件解决时间

Infrastructure debugging that normally takes 10-15 minutes of manual code scanning now takes about 5 minutes.

Improved security review cycle

过去需要人工扫描代码 10-15 分钟才能完成的基础设施调试工作，现在大约只需要 5 分钟。

安全审查周期得到了显著改进。

Terraform code reviews for security approval happen much faster, eliminating developer blocks while waiting for security team approval.

Enhanced cross-functional contribution

用于安全审批的 Terraform 代码审查（code reviews）速度大大加快，这消除了开发人员在等待安全团队批准时的阻碍。

促进跨职能贡献

Team members can meaningfully contribute to projects within days instead of weeks of context building.

Better documentation workflow

团队成员可以在短短几天内就对项目做出有意义的贡献，而无需花费数周时间来熟悉项目背景。

优化文档工作流（workflow)

Synthesized troubleshooting guides and runbooks from multiple sources create more efficient debugging processes.

Top tips from the Security Engineering team

整合了来自多个来源的故障排除指南（troubleshooting guides）和运行手册（runbooks），能够建立更高效的调试流程。

安全工程团队的精选建议

Use custom slash commands extensively

Security engineering uses $50\%$ of all custom slash command implementations in the entire monorepo. These custom commands streamline specific workflows and speed up repeated tasks.

广泛使用自定义斜杠命令在整个 monorepo 中，所有自定义斜杠命令（custom slash command）的实现里，有 $50\%$ 都被安全工程部门使用了。这些自定义命令能够简化特定的工作流程，并加快重复性任务的处理速度。

Let Claude talk first

Instead of asking targeted questions for code snippets, they now tell Claude Code to “commit your work as you go” and let it work autonomously with periodic check-ins, resulting in more comprehensive solutions.

现在，人们不再针对具体的代码片段提出问题，而是让 Claude Code「边写边提交代码」，并允许它自主工作，只需定期进行检查即可。这样一来，它就能提供更全面的解决方案。

Leverage it for documentation

Beyond coding, Claude Code excels at synthesizing documentation and creating structured outputs. They provide writing samples and formatting preferences to get documents they can immediately use in Slack, Google Docs, and other tools to avoid interface switching fatigue.

利用 Claude Code 进行文档撰写除了编写代码，Claude Code 在整合文档（documentation）和生成结构化输出（structured outputs）方面也表现卓越。用户可以向它提供写作样本和格式偏好，它就能生成可以直接在 Slack、Google Docs 等工具中使用的文档，从而避免在不同界面间频繁切换的烦恼。

### Claude Code for inference

The Inference team manages the memory system that stores information while Claude reads your prompt and generates its response. Team members, especially those who are new to machine learning, can use Claude Code extensively to bridge that knowledge gap and accelerate their work.

### Claude Code 在推理阶段的应用推理（Inference）团队负责管理一个记忆系统，这个系统会在 Claude 读取你的提示并生成其响应时存储相关信息。团队成员，特别是那些刚接触机器学习的新手，可以广泛利用 Claude Code 来填补知识空白，从而加快他们的工作效率。

Main Claude Code use cases

Codebase comprehension and onboarding

Claude 在代码方面的主要应用场景理解代码库和新员工快速上手

The team relies heavily on Claude Code to quickly understand the architecture when joining a complex codebase. Instead of manually searching GitHub repos, they ask Claude to find which files call specific functionalities, getting results in seconds rather than asking colleagues or searching manually.

团队高度依赖 Claude Code，以便在加入一个复杂的代码库时，能够快速理解其架构。他们无需手动搜索 GitHub 仓库，而是直接要求 Claude 查找哪些文件调用了特定的功能，短短几秒钟就能获得结果，省去了询问同事或手动搜索的麻烦。

Unit test generation with edge case coverage

After writing core functionality, they ask Claude to write comprehensive unit tests. Claude automatically includes missed edge cases, completing what would normally take significant mental energy in minutes, acting like a coding assistant they can review.

单元测试生成：覆盖各种边缘案例在核心功能开发完成后，他们会请 Claude 来编写全面的单元测试（Unit Test）。Claude 能够自动识别并包含那些容易被忽略的边缘案例（Edge Case），在短短几分钟内就完成了通常需要投入大量精力才能完成的工作。它就像一个高效的编码助手，能生成可供人工审查的代码。

Machine learning concept explanation

Without a machine learning background, team members depend on Claude to explain model-specific functions and settings. What would require an hour of Google searching and reading documentation now takes 10-20 minutes, reducing research time by $80\%$.

深入理解机器学习概念对于缺乏机器学习（Machine learning）背景的团队成员来说，他们现在可以依靠 Claude 来解释特定模型的功能和设置。过去需要一小时进行 Google 搜索和查阅文档的工作，如今只需 10-20 分钟就能完成，研究时间因此减少了 $80\%$。

Cross-language code translation

When testing functionality in different programming languages, they explain what they want to test and Claude writes the logic in the required language (like Rust), eliminating the need to learn new languages just for testing purposes.

跨语言代码翻译在不同编程语言中测试功能时，用户只需描述他们想要测试的内容，Claude 就能用指定的语言（例如 Rust）编写出相应的逻辑代码。这大大简化了流程，让用户无需仅仅为了测试目的而专门学习一门新语言。

Command recall and Kubemetes management

Instead of remembering complex Kubernetes commands, they ask Claude for the correct syntax, like “how to get all pods or deployment status,” and receive the exact commands needed for their infrastructure work.

命令查询与 Kubernetes 管理告别繁琐的 Kubernetes 命令记忆，用户只需向 Claude 提问，比如「如何查看所有 Pods（ Pods）或部署状态」，Claude 就能立即提供其基础设施工作所需的精确命令。

Claude Code for inference

Team impact

Claude 推理代码团队影响

Accelerated ML concept learning

Research time reduced by $80\%$ - what took an hour of Google searching now takes 10-20 minutes.

加速机器学习（ML）概念学习研究时间缩短了 $80\%$ —— 过去需要一小时的 Google 搜索，现在只需 10 到 20 分钟即可完成。

Faster codebase navigation

Can find relevant files and understand system architecture in seconds instead of asking colleagues.

更快速地浏览代码库现在，你可以在几秒钟内找到所需文件，并轻松理解整个系统架构，无需再频繁向同事请教。

Comprehensive test coverage

Claude automatically generates unit tests with edge cases, relieving mental burden while maintaining code quality.

全面的测试覆盖

Claude 能自动生成包含各种边缘情况的单元测试（unit tests），这不仅减轻了开发人员的思考负担，同时还能保证代码质量。

Language barrier elimination

Can implement functionality in unfamiliar languages like Rust without needing to learn it.

消除语言障碍即使不熟悉 Rust 等编程语言，也能实现其功能。

Top tips from the Inference team

Test knowledge base functionality first

来自 Inference 团队的重要提示首先测试知识库的功能

Try asking various questions to see if Claude can answer faster than Google search. If it’s faster and more accurate, it’s a valuable time-saving tool for your workflow.

你可以试着向 Claude 提出各种问题，看看它是否能比 Google 搜索更快地给出答案。如果 Claude 在速度和准确性上都表现出色，那么它对你的工作流程来说，将是一个非常有价值的省时工具。

Start with code generation

Give Claude specific instructions and ask it to write logic, then verify correctness. This helps build trust in the tool’s capabilities before using it for more complex tasks.

从代码生成入手可以先给 Claude 具体指令，让它来编写逻辑代码，然后验证其正确性。这样做有助于在将该工具用于更复杂的任务之前，建立起对其能力的信任。

Use it for test writing

Having Claude write unit tests relieves significant pressure from daily development work. Leverage this feature to maintain code quality without spending time thinking through all test cases manually.

用它来编写测试让 Claude 编写单元测试，能够显著减轻日常开发工作的压力。利用这项功能，我们可以在不花费大量时间手动思考所有测试用例的情况下，依然保持高质量的代码。

### Claude Code for data science and visualization

Data Science and ML Engineering teams need sophisticated visualization tools to understand model performance, but building these tools often requires expertise in unfamiliar languages and frameworks. Claude Code enables these teams to build production-quality analytics dashboards without becoming full-stack developers.

### Claude Code 助力数据科学与可视化数据科学和机器学习（ML）工程团队需要复杂的 ** 可视化 **（Visualization）工具来理解模型性能。然而，构建这些工具往往需要在不熟悉的编程语言和框架方面拥有专业知识。Claude Code 旨在帮助这些团队构建出生产级别的 ** 分析仪表板 **（Analytics Dashboards），而无需他们成为专业的全栈开发人员。

Main Claude Code use cases

Building JavaScript/TypeScript dashboard apps

Claude 代码的主要应用场景开发 JavaScript/TypeScript 仪表盘应用

Handling repetitive refactoring tasks

When faced with merge conflicts or semi-complicated file refactoring that’s too complex for editor macros but not large enough for major development effort, they use Claude Code like a “slot machine” - commit their state, let Claude work autonomously for 30 minutes, and either accept the solution or restart fresh if it doesn’t work.

如何处理重复的重构任务当开发者们遇到合并冲突（merge conflicts），或是那些用编辑器宏（editor macros）搞不定，但又不足以投入大量开发精力的半复杂文件重构（file refactoring）任务时，他们会把 Claude Code 当成「老虎机」来使用 —— 先提交当前的工作状态，然后让 Claude 自主工作 30 分钟。如果 Claude 找到了解决方案，他们就接受；如果不行，就干脆重新来过。

Creating persistent analytics tools instead of throwaway notebooks

Instead of building one-off Jupyter notebooks that get discarded, the team now has Claude build permanent React dashboards that can be reused across future model evaluations. This is important because understanding Claude’s performance is “one of the most important things for the team” - they need to understand how models perform during training and evaluations, which “is actually non-trivial and simple tools can’t get too much signal from looking at a single number go up.”

创建持久性分析工具，而非用完即弃的笔记如今，团队不再构建那些用完就丢的一次性 Jupyter notebook （交互式笔记本），而是让 Claude 来搭建能够永久保留的 React dashboards （React 仪表盘），这些仪表盘在未来的模型评估中都可以反复利用。这一点至关重要，因为理解 Claude 的性能「对团队来说是最重要的事情之一」—— 他们需要深入了解模型在训练和评估阶段的表现。而这「实际上并非小事，简单工具仅凭观察某个单一指标的上升，是无法获取太多有用信息的」。

Zero-dependency task delegation

For tasks in completely unfamiliar codebases or languages, they delegate entire implementation to Claude Code, leveraging its ability to gather context from the monorepo and execute tasks without their involvement in the actual coding process. This allows productivity in areas outside their expertise instead of spending time learning new technologies.

零依赖任务委托对于那些他们完全不熟悉的代码库或编程语言中的任务，用户会把整个实现过程交给 Claude Code。Claude Code 能够利用其从单一代码库（monorepo）中获取项目背景信息的能力，全权负责并执行任务，而无需用户亲自参与编码。这样一来，用户即使在自己的专业领域之外，也能保持高效率，从而避免了将时间花费在学习新技术上。

Claude Code for data science and visualization

Team impact

Claude 代码在数据科学和可视化方面的应用对团队的影响

Achieved 2-4x time savings

Routine refactoring tasks that were tedious but manageable manually are now completed much faster.

这项技术节省了 2 到 4 倍的时间。

过去那些例行的重构任务，手动处理起来虽然繁琐却还能应付，现在完成得快多了。

Built complex applications in unfamiliar languages

Created 5,000-line TypeScript applications despite having minimal JavaScript/TypeScript experience.

用不熟悉的语言开发了复杂的应用程序尽管对 JavaScript/TypeScript 经验不多，仍成功开发了 5,000 行的 TypeScript 应用程序。

Shifted from throwaway to persistent tools

Instead of disposable Jupyter notebooks, now building reusable React dashboards for model analysis.

工具的转变：从「用完即弃」到「持久耐用」

过去，我们可能会使用一次性的 Jupyter notebook 进行模型分析；而现在，我们正在构建可重复使用的 React 仪表板，以实现更持久、更高效的模型分析工作。

Direct model improvement insights

Firsthand Claude Code experience informs development of better memory systems and UX improvements for future model iterations.

模型改进的直接洞察通过第一手体验 Claude Code，我们为未来模型迭代中更好的内存系统和用户体验（UX）改进提供了开发思路和指导。

Enabled visualization-driven decision making

Better understanding of Claude’s performance during training and evaluations through advanced data visualization tools.

让决策过程有可视化工具的支撑通过先进的数据可视化工具，我们可以更好地理解 Claude 在训练和评估阶段的表现。

Top tips from the Data Science and ML Engineering teams

Treat it like a slot machine

数据科学和机器学习工程团队的实用小贴士把它当成一台老虎机

Save your state before letting Claude work, let it run for 30 minutes, then either accept the result or start fresh rather than trying to wrestle with corrections. Starting over often has a higher success rate than trying to fix Claude’s mistakes.

在让 Claude 开始工作之前，请先保存好你的当前状态。让它运行 30 分钟后，你可以选择接受结果，或者重新开始，而不是费力去纠正它的错误。通常来说，重新启动（从头开始）比尝试修复 Claude 的错误更容易成功。

Interrupt for simplicity when needed

While supervising, don't hesitate to stop Claude and ask "why are you doing this? Try something simpler.” The model tends toward more complex solutions by default but responds well to requests for simpler approaches.

必要时，为了简洁，可以中断在监督 Claude 的过程中，如果需要，请尽管暂停它，并提问：「你为什么这么做？试试更简单的方法。」这个模型默认会倾向于采用更复杂的解决方案，但当你要求它采取更简单的方法时，它通常能很好地响应。

### Claude Code for API

The API Knowledge team works on features like PDF support, citations, and web search that bring additional knowledge into Claude’s context window. Working across large, complex codebases means constantly encountering unfamiliar code sections, spending significant time understanding which files to examine for any given task, and building context before making changes. Claude Code improves this experience by serving as a guide that can help them understand system architecture, identify relevant files, and explain complex interactions.

### Claude Code：API 开发者的得力助手

API 知识团队致力于开发多种功能，例如 PDF 支持、引用和网络搜索，这些功能旨在将额外的知识整合到 Claude 的上下文窗口中。然而，在处理庞大而复杂的代码库时，团队成员常常会遇到不熟悉的代码区域；他们需要花费大量时间来弄清楚针对特定任务应该查看哪些文件，并在着手修改之前建立足够的背景知识。Claude Code 的出现极大地改善了这一体验。它就像一个智能向导，能帮助开发者理解系统架构、识别相关文件并解释其中复杂的交互逻辑。

Main Claude Code use cases

First-step workflow planning

Claude Code 的主要应用场景初步工作流规划

The team uses Claude Code as their "first stop" for any task, asking it to identify which files to examine for bug fixes, feature development, or analysis. This replaces the traditional time-consuming process of manually navigating the codebase and gathering context before starting work.

该团队将 Claude Code 作为处理任何任务时的「第一站」，会要求它识别出需要检查哪些文件来修复错误、开发新功能或进行分析。这样做取代了过去那种耗时费力、需要手动查找代码库并收集背景信息才能开始工作的传统流程。

Independent debugging across codebases

The team now has the confidence to tackle bugs in unfamiliar parts of the codebase instead of asking others for help. They can ask Claude “Do you think you can fix this bug? This is the behavior I’m seeing” and often get immediate progress, which wasn’t feasible before given the time investment required.

独立调试不同代码库现在，团队有信心解决代码库中不熟悉部分的 bug，而不再需要向他人寻求帮助。他们可以向 Claude 提问：「你觉得你能修复这个 bug 吗？这就是我观察到的现象」，通常就能立刻取得进展。这在过去由于所需的时间投入，是根本无法实现的。

Model iteration testing through dogfooding

Claude Code automatically uses the latest research model snapshots, making it their primary way of experiencing model changes. This gives them direct feedback on model behavior changes during development cycles, which they hadn’t experienced during previous launches.

通过「狗粮测试」(dogfooding）进行模型迭代测试

Claude Code 会自动使用最新的研究模型快照，这成为了他们体验模型变化的主要方式。如此一来，在开发周期中，他们能够直接获得对模型行为变化的反馈，这在他们之前的发布中是从未体验过的。

Eliminating context-switching overhead

Instead of copying code snippets and dragging files into Claude.ai while explaining problems extensively, they can ask questions directly in Claude Code without additional context gathering, significantly reducing mental overhead.

避免上下文切换的麻烦过去，用户可能需要先将代码片段复制粘贴，再把文件拖拽到 Claude.ai 中，同时还要详细地描述问题，整个过程繁琐且费神。现在，他们可以直接在 Claude Code 里提问，无需额外准备或提供上下文信息，这大大降低了他们的思维负担。

Team impact

Increased confidence in tackling unfamiliar areas

团队影响提升了应对陌生领域的信心

Team members can independently debug bugs and investigate incidents in unfamiliar codebases.

Significant time savings in context gathering

团队成员能够独立调试不熟悉代码库中的错误，并调查相关事件。

显著节省了收集上下文信息的时间

Eliminated the overhead of copying code snippets and dragging files into Claude.ai, reducing mental context-switching burden.

Faster rotation onboarding

省去了复制代码片段和拖拽文件到 Claude.ai 的麻烦，从而减轻了思维切换的负担。

加速了新员工的轮岗培训

Engineers rotating to new teams can quickly navigate unfamiliar codebases and contribute meaningfully without extensive colleague consultation.

Enhanced developer happiness

当工程师轮换到新的团队时，他们能够快速地熟悉不熟悉的 codebase（代码库）并做出有价值的贡献，而无需大量咨询同事。

提高开发者的幸福感

Team reports feeling happier and more productive with reduced friction in daily workflows.

Top tips from the API Knowledge team

团队成员表示，日常工作流程中的摩擦减少后，他们感到更开心，工作效率也更高了。

来自 API 知识团队的实用秘籍

Treat it as an iterative partner, not a one-shot solution

Rather than expecting Claude to solve problems immediately, approach it as a collaborator you iterate with. This works better than trying to get perfect solutions on the first try.

把它看作一个可以迭代的伙伴，而非一劳永逸的解决方案与其期望 Claude 立即解决所有问题，不如把它当作一个可以与你共同迭代的协作伙伴。这样做比指望第一次尝试就获得完美解决方案要有效得多。

Use it for building confidence in unfamiliar areas

Don’t hesitate to tackle bugs or investigate incidents outside your expertise - Claude Code makes it feasible to work independently in areas that would normally require extensive context building.

在不熟悉的领域，用它建立你的信心面对专业领域之外的程序错误（bug）或突发事件，别再犹豫了 ——Claude Code 能让你在原本需要大量背景知识才能独立完成的工作中游刃有余。

Start with minimal information

Begin with just the bare minimum of what you need and let Claude guide you through the process, rather than front-loading extensive explanations.

先从最简单的开始。您只需要提供最核心、最基本的信息，然后让 Claude 智能体（AI Agent）来引导您逐步深入，而不是一下子就给出冗长复杂的解释。

Claude Code for growth marketing

The Growth Marketing team focuses on building out performance marketing channels across paid search, paid social, mobile app stores, email marketing, and SEO. As a nontechnical team of one, they use Claude Code to automate repetitive marketing tasks and create agentic workflows that would traditionally require significant engineering resources.

Claude Code 在增长营销中的应用增长营销团队主要负责拓展各种效果营销渠道，包括付费搜索、付费社交、移动应用商店、电子邮件营销和搜索引擎优化（SEO）。作为一个仅有一名成员的非技术团队，他们利用 Claude Code 来自动化那些重复性的营销任务，并构建通常需要大量工程资源的 AI 智能体（AI Agent）驱动的工作流程。

Main Claude Code use cases

Automated Google Ads creative generation

Claude Code 的主要应用场景自动化生成 Google 广告创意

The team built an agentic workflow that processes CSV files containing hundreds of existing ads with performance metrics, identifies underperforming ads for iteration, and generates new variations that meet strict character limits (30 characters for headlines, 90 for descriptions). Using two specialized sub-agents (one for headlines, one for descriptions), the system can generate hundreds of new ads in minutes instead of requiring manual creation across multiple campaigns. This has enabled them to test and iterate at scale, something that would have taken a significant amount of time to achieve previously.

该团队构建了一个 AI 智能体（AI Agent）工作流，用于处理包含数百个现有广告及其效果指标的 CSV 文件。这个工作流能够识别表现不佳的广告以进行优化迭代，并生成符合严格字符限制（标题 30 个字符，描述 90 个字符）的新变体。通过使用两个专业的子 AI 智能体（一个负责标题，一个负责描述），该系统能在几分钟内生成数百个新广告，彻底改变了以往需要在多个广告系列中手动创建的繁琐模式。这使得他们能够大规模地进行测试和迭代，而在此之前，要实现这种效率是极其耗时的。

Figma plugin for mass creative production

Instead of manually duplicating and editing static images for paid social ads, they developed a Figma plugin that identifies frames and programmatically generates up to 100 ad variations by swapping headlines and descriptions, reducing what would take hours of copy-pasting to half a second per batch. This enables l0x creative output, allowing the team to test vastly more creative variations across key social channels.

Figma 插件：大规模创意内容制作利器为了避免手动重复和编辑付费社交广告的静态图片，他们开发了一款 Figma 插件。这款插件能够自动识别设计中的「帧」，并通过代码自动化地替换标题和描述，从而生成多达 100 种广告变体。这大大缩短了工作时间，将原本需要数小时的复制粘贴工作，缩减到每批次仅需半秒钟。通过这种方式，团队的创意产出效率提升了约 10 倍（l0x），使其能够在各大主要社交渠道上测试数量庞大且多样化的创意内容。

Meta Ads MCP server for campaign analytics

They created an MCP server integrated with Meta Ads API to query campaign performance, spending data, and ad effectiveness directly within the Claude Desktop app, eliminating the need to switch between platforms for performance analysis, saving critical time where every efficiency gain translates to better ROI.

Meta Ads MCP 服务器助力营销活动分析他们开发了一个 MCP 服务器，它与 Meta Ads API 集成，能够直接在 Claude Desktop 应用程序中查询广告活动的表现、花费数据和广告效果。这消除了在不同平台之间来回切换进行性能分析的繁琐，从而节省了宝贵的时间，因为在广告领域，每一次效率的提升都意味着更高的投资回报率（ROI）。

Advanced prompt engineering with memory systems

They implemented a rudimentary memory system that logs hypotheses and experiments across ad iterations, allowing the system to pull previous test results into context when generating new variations, creating a selfimproving testing framework. This enables systematic experimentation that would be impossible to track manually.

具有记忆系统（memory system）的高级提示工程他们实施了一个初步的记忆系统，该系统会记录在不同广告迭代过程中产生的假设和实验，从而允许系统在生成新的变体时，将之前的测试结果整合到当前情境中，进而形成一个自我改进的测试框架。这种方式实现了系统化的实验，而这些实验如果依靠人工追踪则根本无法完成。

Claude Code for growth marketing

Team impact

Claude 代码：赋能增长营销团队影响力

Dramatic time savings on repetitive tasks

Ad copy creation reduced from 2 hours to 15 minutes, freeing up time for strategic work.

重复性任务大幅节省时间广告文案创作耗时从 2 小时缩短至 15 分钟，为更具战略性的工作腾出了宝贵时间。

10x increase in creative output

The team can now test vastly more ad variations across channels with automated generation and Figma integration.

创意产出提升 10 倍现在，团队可以通过自动化生成功能和 Figma 集成，在多个渠道上测试数量多得多的广告变体。

Operating like a larger team

The team can handle tasks that traditionally required dedicated engineering resources.

像一个更大的团队一样运作这个团队能够处理那些传统上需要专门工程师才能完成的任务。

Strategic focus shift

The team can spend more time on overall strategy and building agentic automation rather than manual execution.

策略重心转移团队可以将更多精力投入到制定整体战略和构建 AI 智能体（agentic automation）上，而非耗费于人工操作。

Top tips from the Growth Marketing team

Identify API-enabled repetitive tasks

增长营销团队的实用建议识别通过 API（Application Programming Interface）实现的重复性任务

Look for workflows involving repetitive actions with tools that have APIs (like ad platforms, design tools, analytics platforms). These are prime candidates for automation and where Claude Code provides the most value.

请留意那些涉及重复性操作的工作流程，特别是当这些操作需要用到带有 API（应用程序编程接口）的工具时，例如广告平台、设计工具和分析平台。这些场景是实现自动化的理想目标，也是 Claude Code 能够发挥最大价值的地方。

Break complex workflows into specialized sub-agents

Instead of trying to handle everything in one prompt or workflow, create separate agents for specific tasks (like their headline agent vs. description agent). This makes debugging easier and improves output quality when dealing with complex requirements.

将复杂工作流程拆解成专门的子 AI 智能体。

与其试图通过一个提示（prompt）或工作流来处理所有复杂任务，不如为不同的特定任务创建独立的 AI 智能体（AI Agent）。例如，可以分别设置一个负责生成标题的 AI 智能体和一个负责生成描述的 AI 智能体。这样做不仅能简化调试过程，还能在处理复杂需求时有效提升输出的质量。

Thoroughly brainstorm and prompt plan before coding

Spend significant time upfront using Claude.ai to think through your entire workflow, then have Claude.ai create a comprehensive prompt and code structure for Claude Code to reference. Also, work step-by-step rather than asking for one-shot solutions to avoid Claude getting overwhelmed by complex tasks.

在编写代码之前，务必进行充分的头脑风暴并详细规划提示词（prompt plan）。

前期应投入大量时间，利用 Claude.ai 仔细思考你的整个工作流程。然后，让 Claude.ai 为 Claude Code 创建一套全面的提示词和代码结构，以便 Claude Code 参考。此外，请采取循序渐进的工作方式，避免寻求一蹴而就的解决方案，以防 Claude 因任务过于复杂而难以应对。

Claude Code for product design

The Product Design team supports Claude Code, Claude.ai and the Anthropic API, specializing in building AI products. Even non-developers can use Claude Code to bridge the traditional gap between design and engineering, enabling direct implementation of their design vision without extensive back-and-forth with engineers.

Claude Code 赋能产品设计产品设计团队负责支持 Claude Code、Claude.ai 和 Anthropic API，专注于开发 AI 产品。借助 Claude Code，即使是非开发人员也能轻松填补设计与工程之间的传统隔阂，无需与工程师进行大量的反复沟通，即可直接将他们的设计理念付诸实践。

Main Claude Code use cases

Front-end polish and state management changes

Claude Code 的主要应用场景前端界面的优化和状态管理机制的调整

Instead of creating extensive design documentation and going through multiple rounds of feedback with engineers for visual tweaks (typefaces, colors, spacing), they now directly implement these changes using Claude Code. Engineers noted they're making "large state management changes that you typically wouldn't see a designer making," enabling them to achieve the exact quality they envision.

过去，设计师需要创建大量设计文档，并与工程师就视觉调整（如字体、颜色、间距）进行多轮反馈。现在，他们可以直接使用 Claude Code 来实现这些修改。工程师们指出，设计师们正在进行「大规模的状态管理（state management）调整，这通常不是设计师会做出的」，从而使他们能够实现设想中的精准品质。

GitHub Actions automated ticketing

Using Claude Code’s GitHub integration, they can simply file issues/ tickets describing needed changes, and Claude automatically proposes code solutions without having to open Claude Code, creating a seamless bug-fixing and feature refinement workflow for their persistent backlog of polish tasks.

GitHub Actions 自动化工单管理利用 Claude Code 的 GitHub 集成，用户只需提交描述所需修改的问题或工单，Claude 就能自动生成代码解决方案，而无需手动打开 Claude Code。这为他们持续积压的优化和改进任务，创建了一个无缝衔接的错误修复和功能完善工作流程。

Rapid interactive prototyping

By pasting mockup images into Claude Code, they generate fully functional prototypes that engineers can immediately understand and iterate on, replacing the traditional cycle of static Figma designs that required extensive explanation and translation to working code.

快速交互式原型设计通过将设计图（mockup images）粘贴到 Claude Code 中，它能够生成功能齐全的原型，工程师可以立即理解并在此基础上进行迭代。这取代了传统上需要大量解释和转换为实际代码的静态 Figma 设计流程。

Edge case discovery and system architecture understanding

They use Claude Code to map out error states, logic flows, and different system statuses, allowing them to identify edge cases during design rather than discovering them later in development, fundamentally improving the quality of their initial designs.

边缘案例的探查与系统架构的理解他们利用 Claude Code 来梳理错误状态、逻辑流程以及各种系统状态，这使得他们能够在设计阶段就识别出各种边缘案例（edge cases），而不是等到开发后期才发现它们。这种做法从根本上提升了他们初始设计的质量。

Complex copy changes and legal compliance

For tasks like removing "research preview" messaging across the entire codebase, they used Claude Code to find all instances, review surrounding copy, coordinate changes with legal in real-time, and implement updates - a process that took two 30-minute calls instead of a week of back-and-forth coordination.

处理复杂的文案变更与法律合规例如，当需要在整个代码库中移除「研究预览（research preview）」之类的提示信息时，他们会利用 Claude Code 来查找所有相关实例，审查周边的文本内容，并实时与法务部门协调修改，最终实施更新。整个过程仅通过两次 30 分钟的电话会议就完成了，避免了一周之久的反复协调。

Claude Code for product design

Team impact

Claude Code 在产品设计中的应用对团队的影响

Transformed core workflow

Claude Code becomes a primary design tool, with Figma and Claude Code open $80\%$ of the time.

核心工作流程的转变

Claude Code 成为主要的设计工具，Figma 和 Claude Code 在八成的时间里都保持开启状态。

2-3x faster execution

Visual and state management changes that previously required extensive back-and-forth with engineers now implemented directly.

执行速度提升 2 到 3 倍以前需要与工程师反复沟通的视觉和状态管理方面的调整，现在可以直接实现。

Weeks to hours cycle time

Complex projects like GA launch messaging that would take a week of coordination now completed in two 30-minute calls.

周期时间从数周缩短到数小时过去需要一周时间协调的复杂项目，例如 GA 发布（GA launch）的沟通工作，现在只需通过两次 30 分钟的电话会议就能完成。

Two distinct user experiences

Developers get "augmented workflow" (faster execution), while nontechnical users get "holy crap, I'm a developer workflow" (entirely new capabilities previously impossible).

两种完全不同的用户体验对开发者来说，他们获得的是「增强型工作流」(augmented workflow），这意味着执行效率大大提高。而对于非技术用户，他们得到的则是「天哪，我居然也能像开发者一样工作了」的惊叹（以往完全不可能的新能力）。

Improved design-engineering collaboration

Better communication and faster problem-solving because designers understand system constraints and possibilities upfront.

优化设计与工程协作通过让设计师提前了解系统的局限和潜能，从而实现更高效的沟通和更快速的问题解决。

Top tips from the Product Design team

Get proper setup help from engineers

产品设计团队的实用小贴士请工程师提供专业的设置协助

Have engineering teammates help with initial repository setup and permissions - the technical onboarding is challenging for non-developers, but once configured, it becomes transformative for daily workflow.

让工程团队成员协助设置初始的代码仓库（repository）和权限 —— 对非开发人员来说，技术上手可能比较困难，但一旦配置妥当，它将给日常工作流程带来颠覆性的变革。

Use custom memory files to guide Claude's behavior

Create specific instructions telling Claude you're a designer with little coding experience who needs detailed explanations and smaller, incremental changes, dramatically improving the quality of Claude's responses and making it less intimidating.

利用自定义记忆文件来引导 Claude 的行为你可以创建具体的指令，告诉 Claude 你是一名编程经验很少的设计师，需要它提供详细的解释和更小、循序渐进的调整。这样做能显著提升 Claude 回复的质量，并让它变得不再那么令人望而生畏。

Leverage image pasting for prototyping

Use Command $+ \mathrm { V }$ to paste screenshots directly into Claude Code - it excels at reading designs and generating functional code, making it invaluable for turning static mockups into interactive prototypes that engineers can immediately understand and build upon.

利用图片粘贴来制作原型只需使用 Command $+ \mathrm {V}$ ，就能将截图直接粘贴到 Claude Code 中。Claude Code 非常擅长理解设计图并生成功能性代码，这使得它在将静态 UI 模型（mockups）转化为可交互原型方面具有极高价值，工程师能够立即理解并在此基础上进行开发。

Claude Code for RL engineering

The RL Engineering team focuses on efficient sampling in RL and weight transfers across the cluster. They use Claude Code primarily for writing small to medium features, debugging, and understanding complex codebases, with an iterative approach that includes frequent checkpointing and rollbacks.

Claude Code 与强化学习工程强化学习（Reinforcement Learning，RL）工程团队主要关注如何在该领域实现高效采样，以及如何在集群间高效地传输模型权重。他们主要利用 Claude Code 来开发中小型功能、进行代码调试，并理解复杂的代码库。他们的工作方式是迭代式的，会频繁地设置检查点（checkpointing）和进行回滚（rollbacks）操作。

Main Claude Code use cases

Feature development with supervised autonomy

Claude Code 主要用例在监督下自主进行功能开发

The team lets Claude Code write most of the code for small to medium features while providing oversight, such as implementing authentication mechanisms for weight transfer components. They work interactively, allowing Claude to take the lead but steering it when it goes off track.

这个团队主要让 Claude Code 来编写中小型功能的大部分代码，同时他们会进行监督，例如负责为权重传输组件实现认证机制。他们采用互动式的工作模式，允许 Claude 主导编码工作，但当它偏离方向时，团队会及时进行纠正或引导。

Test generation and code review

After implementing changes themselves, they ask Claude Code to add tests or review their code. This automated testing workflow saves significant time on routine but important quality assurance tasks.

测试生成和代码审查在开发者自己实现代码更改后，他们会请 Claude Code 添加测试或审查他们的代码。这种自动化测试工作流程在处理那些例行但却非常重要的质量保证任务时，能够节省大量时间。

Debugging and error investigation

They use Claude Code to debug errors with mixed results - sometimes it identifies issues immediately and adds relevant tests, while other times it struggles to understand the problem, but overall provides value when it works.

代码调试与错误排查他们使用 Claude Code 来调试错误，但效果不一：有时它能立即识别问题并添加相关的测试用例，而另一些时候它则难以理解问题的症结所在。不过，总的来说，当它成功解决问题时，仍能带来显著的价值。

Codebase comprehension and call stack analysis

One of the biggest changes in their workflow is using Claude Code to get quick summaries of relevant components and call stacks, replacing manual code reading or extensive debugging output generation.

代码库理解和调用栈分析在他们的工作流程中，最大的变化之一是开始使用 Claude Code 来快速获取相关组件和调用栈（call stack）的摘要，这取代了过去需要手动阅读代码或生成大量调试输出的繁琐工作。

Kubernetes operations guidance

They frequently ask Claude Code about Kubernetes operations that would otherwise require extensive Googling, getting immediate answers for configuration and deployment questions.

Kubernetes 操作指南他们经常向 Claude Code 咨询 Kubernetes（Kubernetes）操作方面的问题。这些问题，如果没有 Claude Code，通常需要花费大量时间通过 Google 搜索才能找到答案，但现在他们能即时获得配置和部署问题的解决方案。

Claude Code for RL engineering

Development workflow impact

用于强化学习（RL）工程的 Claude 代码对开发工作流程的影响

Experimental approach enabled

They now use a “try and rollback” methodology, frequently committing checkpoints so they can test Claude’s autonomous implementation attempts and revert if needed, enabling more experimental.

他们现在采用一种「尝试并回滚」的方法，频繁地保存进度点（checkpoints），这样他们就可以测试 Claude 的自主执行尝试，并在需要时恢复到之前的状态。这使得他们能够更大胆地进行实验。

Documentation acceleration

Claude Code automatically adds helpful comments that save significant time on documentation, though they note it sometimes adds comments in odd places or uses questionable code organization.

文档编写提速

Claude Code 能够自动添加有用的注释，这大大节省了编写文档的时间。不过，他们也指出，它有时会在不恰当的位置添加注释，或者采用欠佳的代码组织方式。

Speed-up with limitations

While Claude Code can implement small-to-medium PRs with “relatively little time” from them, they acknowledge it only works on first attempt about one-third of the time, requiring either additional guidance or manual intervention.

提速但有局限

Claude Code 虽然能够以「相对较少的时间」完成中小型 PR（Pull Requests）的实现工作，但开发团队也承认，它在第一次尝试时大约只有三分之一的成功率，这意味着很多时候仍需要人工提供额外指导或手动介入。

Top tips from the RL Engineering team

Customize your Claude.md file for specific patterns

来自 RL 工程团队的实用技巧针对特定模式，定制你的 Claude.md 文件

Add instructions to your Claude.md file to prevent Claude from making repeated tool-calling mistakes, such as telling it to “run pytest not run and don’t cd unnecessarily - just use the right path.” This significantly improved consistency.

请在你的 Claude.md 文件中添加指令，以防止 Claude 重复出现工具调用错误。例如，可以指示它「运行 pytest 而不是 run，并且不要不进行不必要的目录切换（cd），只需使用正确的路径」。这项改进显著提升了其操作的一致性。

Use a checkpoint-heavy workflow

Regularly commit your work as Claude makes changes so you can easily roll back when experiments don’t work out. This enables a more experimental approach to development without risk.

采用一个频繁使用检查点（checkpoint）的工作流。

当 Claude 进行修改时，请定期提交你的工作。这样，一旦实验不成功，你就能轻松地回滚到之前的版本。这使得开发者能够在没有风险的情况下，大胆尝试更具实验性的开发方法。

Try one-shot first, then collaborate

Give Claude a quick prompt and let it attempt the full implementation first. If it works (about one-third of the time), you’ve saved significant time. If not, then switch to a more collaborative, guided approach.

先尝试独立完成，再进行协作首先，给 Claude 一个简短的指令（prompt），让它尝试独立完成整个任务。如果它成功了（大约有三分之一的几率），你就能节省大量时间。如果失败了，就改用一种更注重协作和指导的方法。

Claude Code for legal

The Legal team discovered Claude Code’s potential through experimentation, and a desire to learn about Anthropic's product offerings. Additionally, one team member had a personal use case related to creating accessibility tools for family and work prototypes that demonstrate the technology's power for non-developers.

法务团队通过亲自实践和探索 Anthropic 的产品，发现了 Claude Code 的巨大潜力。此外，团队中还有一位成员有一个个人需求，他希望为家人和工作原型开发一些无障碍辅助工具（accessibility tools），而这些原型恰好能向非开发人员充分展示这项技术的强大功能。

Main Claude Code use cases

Custom accessibility solution for family members

Claude Code 的主要应用场景（use cases)

*  为家庭成员提供定制化的便捷使用方案

Team members have built communication assistants for family members with speaking difficulties due to medical diagnoses. In just one hour, they created a predictive text app using native speech-to-text that suggests responses and speaks them using voice banks, solving gaps in existing accessibility tools recommended by speech therapists.

团队成员为因疾病诊断而有言语障碍的家人开发了沟通辅助工具。他们仅用一小时就制作了一款预测文本应用，这款应用利用原生语音转文本（speech-to-text）技术来推荐回复，并能使用音色库（voice banks）朗读这些回复，从而弥补了语言治疗师所推荐的现有辅助工具的不足。

Legal department workflow automation

They created prototype “phone tree” systems to help team members connect with the right lawyer at Anthropic, demonstrating how legal departments can build custom tools for common tasks without traditional development resources.

法律部门工作流自动化他们创建了原型「电话树」（phone tree）系统，目的是帮助团队成员联系到 Anthropic 公司里最合适的律师。这清晰地展示了法律部门如何在没有传统开发资源的情况下，也能为日常任务构建定制化的工具。

Team coordination tools

Managers have built G Suite applications that automate weekly team updates and track legal review status across products, allowing lawyers to quickly flag items needing review through simple button clicks rather than spreadsheet management.

团队协作工具为了提升效率，经理们开发了一些 G Suite 应用程序。这些工具不仅能自动完成每周的团队更新，还能追踪不同产品的法律审查进度。这样一来，律师们不再需要手动管理复杂的电子表格，只需简单点击按钮，就能快速标记出需要审查的事项。

Rapid prototyping for solution validation

They use Claude Code to quickly build functional prototypes they can show to domain experts (like showing accessibility tools to UCSF specialists) to validate ideas and identify existing solutions before investing more time.

快速原型构建，验证解决方案他们利用 Claude Code 快速构建功能性原型。这些原型可以展示给领域专家（例如，向 UCSF 的专家展示无障碍工具），从而在投入大量时间之前，就能验证想法并识别出已有的解决方案。

Claude Code for legal

Work style and impact

Claude Code 在法律领域的应用工作风格与影响

Planning in Claude.ai, building in Claude Code

They use a two-step process where they brainstorm and plan with Claude.ai first, then move to Claude Code for implementation, asking it to slow down and work step-by-step rather than outputting everything at once.

在 Claude.ai 中规划，在 Claude Code 中构建他们采用了一个两步走的工作流程：首先，在 Claude.ai 中进行头脑风暴和规划；随后，转向 Claude Code 进行具体实现，并要求它放慢节奏，一步一步地完成工作，而不是一次性输出所有内容。

Visual-first approach

They frequently use screenshots to show Claude Code what they want interfaces to look like, then iterate based on visual feedback rather than describing features in text.

视觉优先的策略他们经常使用截图来向 Claude Code 展示他们希望界面呈现的效果，然后根据视觉反馈进行反复迭代和优化，而不是仅仅通过文本来描述功能。

Prototype-driven innovation

They emphasize overcoming the fear of sharing “silly” or “toy” prototypes, as these demonstrations inspire others to see possibilities they hadn’t considered.

原型驱动的创新他们强调，要克服分享那些看起来可能「不太成熟」或「初步概念性」的原型 （prototype）的顾虑，因为这些演示能启发他人看到他们之前未曾考虑过的各种可能性。

Security and compliance awareness

MCP integration concerns

安全与合规意识

MCP 集成问题

As product lawyers, they immediately identify security implications of deep MCP integrations, noting how conservative security postures will create barriers as AI tools access more sensitive systems.

作为产品律师，他们立即识别出深度 MCP 集成的安全隐患，并指出当 AI 工具需要访问更敏感的系统时，保守的安全策略会如何构成障碍。

Compliance tooling priorities

They advocate for building compliance tools quickly as AI capabilities expand, recognizing the balance between innovation and risk management.

合规工具优先级随着人工智能（AI）能力的不断扩展，他们主张快速开发合规工具，同时也要兼顾创新与风险管理之间的平衡。

Top tips from the Legal Department

Plan extensively in Claude.ai first

法律部门的重要提示首先在 Claude.ai 中充分规划

Use Claude’s conversational interface to flesh out your entire idea before moving to Claude Code. Then ask Claude to summarize everything into a step-by-step prompt for implementation.

在转向 Claude Code 之前，先利用 Claude 的对话界面来完善你的整个想法。之后，再请 Claude 将所有内容总结为一个用于实施的分步提示。

Work incrementally and visually

Ask Claude Code to slow down and implement one step at a time so you can copy-paste without getting overwhelmed. Use screenshots liberally to show what you want interfaces to look like.

分步并可视化地工作请 Claude Code 放慢速度，一步步地实现，这样你就可以轻松复制粘贴，而不会感到手足无措。请大量使用截图，来展示你希望界面呈现的效果。

Share prototypes despite hnperfection

Overcome the urge to hide “toy” projects or unfinished work - sharing prototypes helps others see possibilities and sparks innovation across departments that don’t typically interact.

即使不完美，也要分享原型克服隐藏那些「小项目」或未完成作品的冲动吧 —— 分享原型能够帮助他人看到更多可能性，并在那些平时不常往来的部门之间激发出创新火花。