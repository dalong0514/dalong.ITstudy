## 20251115浅谈Claude-Skills

[浅谈Claude Skills，Github已经5.2k Star了](https://mp.weixin.qq.com/s/eSjsTdd1qt2OboIE1VPILw)

说个暴论，AI Agent 想要落地，需要的只有强大的模型基座，什么 Skill、MCP、... 都只是添头，通过代码很容易实现。

Agent 的核心驱动力永远是 LLM 本身。

其他所有东西说白了都是在给这个不那么可靠的大脑搭建脚手架，做工程化的约束。

但比起最近 OpenAI 开始搞颜色，A 社搞搞 Skill 还是值得肯定的...

### 所以，Claude Skills 到底是什么？

一句话说清楚：Skill 就是一个标准化的文件夹，用来打包 Agent 完成特定任务所需的知识和工具。

你可以把它理解成给模型的说明书或标准作业程序（SOP，或者之前比较火的概念：SPEC 的增强版）。

Anthropic 这次不仅发布了概念，还直接开源了一个 GitHub 仓库，里面包含了所有 20 个左右的官方 Skill 的源码示例。

[anthropics/skills: Public repository for Skills](https://github.com/anthropics/skills)

这才是最有价值的地方，它把理论落到了代码上：

A 社官方开源的 Skill 仓库，包含十几个 Skill 示例，一个 Skill 文件夹通常包含这几部分：

SKILL.md：核心文件，必须存在。里面用 YAML 写元数据（名字、描述），用 Markdown 写详细的指令，告诉 Claude 在什么情况下、以及如何使用这个 Skill。

scripts/：存放可执行的 Python、Shell 脚本。比如 PDF 处理 Skill 里，就有 fill_fillable_fields.py 这种确定性极强的代码。

references/：存放参考文档。比如 API 文档、数据库 Schema、公司政策等，这些是给 Claude 看的知识库。

assets/：存放资源文件。比如 PPT 模板、公司 Logo、React 项目脚手架等，这些是 Claude 在执行任务时直接使用的文件，而不是阅读的。

Claude Skill 文件夹结构所以说：

一个 Skill = 任务说明书 SKILL.md + 工具代码（scripts）+ 专业知识（references）+ 素材资源（assets）。

它把完成一个特定任务所需的一切都打包好了，本质上就是一种代码和资源的组织方式，一种约定优于配置的理念。

### 它的精髓：为上下文窗口减负

这部分是 ClaudeSkills 设计的精髓，也是它和简单 RAG/MCP/FunctionCalling 的最大区别。它就是一套聪明的，为了节省上下文窗口而设计的分层加载策略。

既然是分层策略，那么有哪几层？

分层策略第一层：元数据（Name + Description）。这部分信息非常简短，会常驻在 Claude 的脑海里。当用户提出一个任务时，Claude 会快速扫描所有可用 Skill 的描述，判断哪个可能相关。这是第一道筛选，成本极低。

第二层：SKILL.md。当 Claude 认为某个 Skill 相关时，它才会去加载 SKILL.md 里的详细指令。这部分内容告诉 Claude 完成任务的具体步骤、应该遵循的规则、以及如何使用文件夹里的其他资源。这步的上下文消耗中等。

第三层：脚本和参考文档。只有当 SKILL.md 里的指令明确要求，或者 Claude 在执行中判断需要时，它才会去读取 scripts / 里的代码或 references / 里的文档。这步的上下文消耗是按需的，避免了一次性把所有东西都塞进去。

这个机制的好处显而易见，极大地节省了宝贵的上下文窗口。它先凭经验判断用哪个 SOP，然后翻开 SOP 照着做，遇到具体问题再查阅附录或工具手册。这套逻辑，我们用代码当然也能实现，但 Skills 把它标准化了。

### 它和 MCP 是什么关系

MCP 是一种通信协议。它定义了 Agent（客户端）如何与一个暴露了工具的服务（服务端）进行标准化的交流。它解决的是 Agent 与外部工具如何对话的问题。

Claude Skills 是一种能力封装格式。它定义了 Agent 自身应该具备哪些知识、工作流和内部工具。它解决的是 Agent 如何思考和行动的问题。

Skill 里的知识可以指导 Agent 如何更有效地去使用一个遵循 MCP 协议的工具。一个 Agent 完全可以加载一个 Skill，然后根据 Skill 里的指令，去调用一个远程的 MCP 服务器。

Claude Skills 与 MCP 的关系所以你看，它俩不是替代关系，而是正交的、可以组合的。MCP 负责连接，Skills 负责驱动。一个解决通信标准，一个解决能力封装。

### 这套东西，对我们开发者有什么用？

回到开头的观点，既然这玩意儿本质上就是一堆文件夹和代码，我们开发者能从中得到什么？

最大的价值是：Anthropic 把他们在生产环境中打磨出的一套 Agent 能力管理的设计模式开源了。我们完全可以把这个模式借鉴过来，用在自己的 Agent 体系里，不管你用的是 Qwen、Deepseek，还是别的模型。

图：一个不错的设计模式，解耦、模块化的 Skills 

当你的 Agent 能力越来越多时，怎么管理？一个几千行的 System Prompt？一个包含几十个工具函数的大杂烩文件？这些都很难维护。

而 Skills 提供了一种解耦的、模块化的方案。你团队里的 Agent 不再是依赖一个巨大的、难以维护的 system_prompt.txt，而是一个由几十个标准化的 Skill 文件夹组成的能力库，每个 Skill 都可以独立版本控制、测试和迭代。

### 举个栗子

比如你可以为你的公司创建一个数据分析工具，起名为：internal-analytics-skill，里面包含：

SKILL.md：指导 Agent 如何查询公司内部数据仓库。

scripts/generate_report.py：一个固定的 Python 脚本，用于生成标准格式的周报。

references/db_schema.md：数据仓库的 Schema 文档。

assets/report_template.docx：周报的 Word 模板。

当有新的 Agent 实例加入时，你只需要让它加载这个 Skill，它就立刻学会了如何做数据分析，而不需要重新训练或编写复杂的 Prompt。

所以说呀，Claude Skills 本身不是什么黑科技。它最大的启示还是：AI Agent 的未来，一半靠模型，另一半靠工程。