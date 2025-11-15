## 20251115三个Claude-Skills提效秘籍让WPS邀请我来开会

[三个 Claude Skills 提效秘籍让WPS邀请我来开会](https://mp.weixin.qq.com/s/vjPZ9r5AZb01FtE_uvbKVA)

2025-11-03

上周 WPS 邀请我和一泽老师去分享 Claude Skills 技巧，受宠若惊，荣幸之至。

产品总监和负责人听完很满意，我也请教了一些相关的问题，包括对当前 AI 的应用现状等等。

通过这次我们与一线的产品研发团队交流学习，学到了非常多的经验，WPS 不愧为老牌软件公司，底蕴实力雄厚。

然后收到了签发的聘书。

这份很有意思的分享，我也在公众号来进行一下分享。

我将部分分享内容做了脱敏处理，并把关键要点加以梳理与呈现，整理如下。

### 01. 看个好玩的

我让 Claude 去学习了几篇文档的排版与格式，结果它不仅理解了样式，还能直接由文本生成完整、可交付的 Office 文件。

case1：求职招聘

（左边为模板，右边为 Claude Skills 生成的简历）

case2：红头通知文件格式

（左边为通知模板，右边为 Claude Skills 学习之后生成的简历）

case3：合作协议（行业模板）

（左边为合作协议书模板，右边为 Claude Skills 学习之后生成的合作协议）

从这些案例可以看出，AI 正在从「对话式文本生成」迈向「文生文件」的阶段 —— 输出的不是一段文字，而是一份可以直接交付使用的文档。这才是真正意义上的落地应用。

以往的 AI，只能生成内容，还得人工复制粘贴到 Word 或 PPT 里，手动调样式、修格式。

而现在，它能在对话中直接生成完整的 Word、PPT、PDF，甚至 Excel，全程无需打开任何办公软件。

那我还可以干啥？？？

这听起来有点离谱，但确实是真的。

背后的支撑，是一种全新的 AI 范式：Claude Skills。

### 02. 什么是 Claude code?

介绍 Claude skills 之前，先来说说 Claude code。

Claude code 就是一个终端运行的通用智能体，它可以使用本地代码执行和文件系统跨域完成复杂任务。

区分：LLM vs Agent vs Workflow 

智能体：赋予大模型规划、反思和使用工具的能力，可以自主解决复杂问题。

工作流：是结构化、可重复地解决一系列复杂任务的固定化流程。

### 03. 为什么 Athropic 要做 skills？

坦白讲，一开始我也不太理解。

于是我画了张图，帮助自己理清这个体系。

Anthropic 实际上定义了三个与「人类知识结构」强相关的概念：Project、MCP、Skills。

本质上，AI 是为人服务的，【碳基 > 硅基】，但要真正具备「服务能力」，就需要三层能力的递进：

理解 Project：能干活，但像 2G 网络一样不在线。

可以把 Project 理解为 AI 的背景与经历。

就像一个人从上学、求职到进入职场，这些阶段构成了他的阅历与知识结构。每个人的路径不同 —— 有人是自媒体人，有人是金融背景，也有人在跨境电商领域深耕。

对于 AI 来说，Project 相当于给它设定一个工作场景，比如「自媒体文案专家」。

它会在这个领域内发挥通用能力，具备一定「网感」，能完成入门级任务。

但仅此而已，它还不是「有经验的专家」，只能算是一个初级的，有的时候干的活甚至不及格。

理解 MCP：村里通网了，但是脑瓜里一团浆糊。

MCP（Model Context Protocol）是 AI 连接外部信息源的「神经中枢」。

人类通过互联网、图书馆或社群学习新知识，这就是「信息增量」的过程。

比如你现在读这篇文章，完整了解了 Claude Skills，这本身就是一次知识增量。

意思是我们处于一个空间 x 时间的维度里面，需要考虑时间的因素，与时俱进。

同理，AI 模型训练背后的训练语料固定在过去的时间点，无法实时获取新信息。

比如用 2024 年 9 月训练的模型，不借助外部能力，它是不知道 2025 年发生的事情呢。

MCP 的作用就是给 AI 接上网线，让它能动态访问外部资源、数据库和接口，从而避免信息闭塞。

但它依然只是能联网，不代表能理解或会用。

理解 Skills：手巧，能把麻线拧成绳。

真正让 AI 从会查资料变成会干活的，是 Skills。

人类的学习方法、职场经验、本能判断，这些都是核心竞争力。同样的，AI 也需要学习如何把知识应用起来。

好比打游戏一样，榜一大哥超级能刷 BOSS 怪兽的原因，也是有他自己的操作心法，什么武林秘籍啊都是这样...

对现阶段的通用 AI 来说，问题在于它没有经过真实项目训练，不知道什么叫「老板满意的 PPT」。

因此，必须由人类提前编写清晰的操作说明书，为它准备任务所需的资源文件。

就像在教实习生：一步步演示，写好指令，打包成模板。

有些任务复杂到让人头皮发麻，AI 在没有上下文经验的情况下容易出错。

Skills 的出现，正是为了解决这种「经验缺口」问题。

现阶段，教 AI 做事之前，就把它当作弱智一样，喂饭到嘴边吧（已泪崩）。

这也是通用 AI 转向垂直 AI 必走的路子。

话说 AI 什么时候养我？？

### 04. Anthropic 要解决的核心问题

Anthropic 现在解决的问题是：模型怎么才能持续变聪明？即：啥都能干。

当前，大部分公开互联网数据都已被用于模型训练。

但高质量内容越来越少，取而代之的是由 AI 自己生成的大量低质信息涌入互联网，形成一个恶性循环（AI 自己拉自己吃）。

结果就是：模型训练进入瓶颈，想再聪明，却没高质量数据可喂。

那么哪些高质量数据和知识在哪里？在企业与个人手里，在那些还未被结构化的业务经验、行业 SOP 和隐性知识中。那些未被挖掘行业知识正在成为无法估量的财产。

我和不少从业者交流后发现，大家普遍认同：

未来 AI 应用的真正爆发，一定是建立在行业 SOP 与领域知识之上。

没有经验，就没有智能。

面对一些专业知识强、需要强业务经验的领域时，Claude code 这种通用 agent 表现的没有那么好（别看能嘎嘎干活，有的时候就在制造垃圾），这也是当前所有通用 agent 面对的困境。

如果涉及专业领域方面，通常是需要固定的 SOP 来执行的，如果每次和 Claude code 去 battle，去教他这方面的行业经验的话，那效率太低了，费钱又费时间，所以这种经验累积非常重要。

因此，一个更高效的方式是 —— 把经验固化为可加载的能力包。

这些「可插拔」的 Skills，可以灵活组合、扩展和迁移，

让 AI 在面对复杂场景（例如制作 PPT、设计品牌 Logo、编写合同）时，表现得既准确又稳健。

所以，Claude skills 应用而生。

Claude Skills 可以动态发现和加载的指令、脚本和资源的组织文件夹，以便在特定任务中表现得更好。

skills 是可重用的、基于文件系统的专业知识单元，

包括特定领域的工作流程、上下文和最佳实践，可将通用代理转变为专家。

一个 Agent 可以挂载多个能力包，按需加载。它在提示词和执行脚本之间，找到了新的平衡点。原本需要手动触发的工具调用，如今可由 Skills 自动管理，让 Agent 的执行过程更智能、更统一。

这就是 Anthropic 做 Skills 的核心动机：

让 AI 不只是拥有显性知识，而是越来越得心应手。

### 05. Claude skill 架构设计

核心设计是渐进式披露，分为三层加载：

渐进式信息披露是 Agent Skills 的核心设计原则，它使 Agent Skills 灵活且可扩展。为什么这么设计？为了节省上下文 token，不需要加载过多的内容，其实就跟图书馆的藏书一样，根据书名和分类方便管理和查找。

Level 1：元数据，只加载名字（name）和描述（description），约 100token，Claude 调用的依据。

Level 2：主指令（SKILL.md），任务匹配读取完整的 SKILL.md，一般 5000token 以内。

Level 3：更多资源（scripts 和 Reference），【按需】加载脚本、参考文档、示例、样式。

#### 级别 1：元数据（始终加载）

启动时，代理会将每个已安装技能的 name 和 description 预加载到其系统提示符中。

技能的 YAML 前端提供发现信息，比如说这样的模板：

```
---
name:xxx
description:xxx
---
```

以 PDF 的 skills 为例:

```
---
name：pdf-processing
description：Extract text and tables from PDF files，fill forms，merge documents. Use when working with PDF files or when the user mentions PDFs，forms，or document extraction.
---
```

Claude 在启动时加载此元数据并将其包含在系统提示符中。

这种轻量级方法意味着你可以安装许多技能而不会受到上下文限制。claude 只知道每个技能的存在以及何时使用它。

#### 级别 2：指令（触发时加载）

SKILL.md 的主体包含程序知识：工作流、最佳实践和指南：

大模型认为该技能与当前任务相关，它会通过读取其完整的 SKILL.md 并将其加载到上下文中来加载该技能。

比如说同样以 PDF Skills 为例：

```
# PDF Processing
## Quick start
Use pdfplumber to extract text from PDFs:

`python
import pdfplumber
with pdfplumber.open("document.pdf"）as pdf:    
    text = pdf.pages[0].extract_text()
`

For advanced form filling，see [FORMS.md](FORMS.md).
```

SKILL.md 文件必须以包含文件名和描述的 YAML Frontmatter 开头，该文件在启动时加载到系统提示符中。

为什么这样设计？之前遇到一个问题：一个任务的复杂度太高，执行时包含过多上下文，会造成上下文爆炸。SKILL 的解法是这样的。SKILL 可以将其他文件捆绑到技能目录中，并通过 SKILL.md 中的名称引用它们。这些额外的链接文件是第三级（及以上）的详细信息，Claude 可以根据需要选择浏览和发现它们。

比如说，pdf 的 SKILL.md 引用了两个附加文件（reference.md 和 forms.md ）。

将表单填写说明移到（forms.md），将参考文献说明移到（reference.md）。

完整的技能目录结构可能如下所示：

```
pdf/
├── SKILL.md              # Main instructions（loaded when triggered)
├── FORMS.md              # Form-filling guide(loaded as needed)
├── reference.md          # API reference(loaded as needed)
├── examples.md           # Usage examples(loaded as needed)
└── scripts/    
├── analyze_form.py   # Utility script(executed，not loaded)    
├── fill_form.py      # Form filling script    
└── validate.py       # Validation script
```

拥有文件系统和代码执行工具的代理在执行特定任务时，无需将整个技能内容读入其上下文窗口。

这意味着，可以捆绑到技能中的上下文数量实际上是无限的。

#### 级别 3：资源和代码（根据需要加载）

技能可以捆绑额外的材料：

```
pdf-skill/
├── SKILL.md(main instructions)
├── FORMS.md(form-filling guide)
├── REFERENCE.md(detailed API reference)
└── scripts/    
└── fill_form.py(utility script)
```

说明：包含专门指南和工作流的其他 Markdown 文件（FORMS.md、REFERENCE.md）

代码：Claude 通过 bash 运行的可执行脚本（fill_form.py、validate.py）；脚本提供确定性操作，而不消耗上下文

资源：参考资料，如数据库架构、API 文档、模板或示例

### 06. Skills 是怎么运行的？

Skills 运行在具备代码执行与文件系统访问能力的环境中，它能调用 bash 命令、读取本地文件、执行脚本，从而让 Claude 拥有真正的「动手能力」。

如果你用过 Manus，应该已经体验过这种 <AI+文件系统> 的模式 —— Claude Skills 的逻辑与之类似，但更精细、更自动化。

以 Claude 加载并使用 PDF 处理技能为例：

Claude 加载和使用 PDF Processing Skill 的完整过程：

1 启动阶段

系统提示中已预加载元数据：

```
PDF Processing – Extract text and tables from PDF files，fill forms，merge documents.
```

2 用户请求

用户输入指令：从此 PDF 中提取文本并对其进行总结。

3 Claude 调用

系统判断任务匹配，自动加载指令文件：

```
bash: read pdf-skill/SKILL.md
```

4 Claude 判断

确定本次任务不涉及表单操作，因此跳过 FORMS.md 文件。

5 Claude 执行

根据 SKILL.md 中的工作指令执行操作，完成文本提取与摘要任务。

简而言之，Claude Skills 的执行逻辑是：

轻装启动，按需加载，动态执行。

它让 Claude 不仅能知道该做什么，还能自己选择怎么做。

### 07. 目前的 Skills 合集

Athropic 开源了 10 多个 skills，目前可用性比较高的当属 document-skills，其他的我测试了，效果比较差。

document-skills 演示了处理复杂文件格式和二进制数据的高级模式。

docx-skill：创建、编辑和分析 Word 文档，支持跟踪更改、注释、格式保留和文本提取

pdf-skill：用于提取文本和表格、创建新 PDF、合并 / 拆分文档以及处理表单的综合 PDF 作工具包

pptx-skill：创建、编辑和分析 PowerPoint 演示文稿，支持布局、模板、图表和自动幻灯片生成

xlsx-skill：创建、编辑和分析 Excel 电子表格，支持公式、格式、数据分析和可视化

#### xlsx-skill：

这个是基于 Claude code 的高级电子表格处理 skill，干的活挺多。

有一个处理财务数据的示例。

```
使用我已经安装的 skills，创建一个包含年度预测的财务摘要表，在单独单元格中设置蓝色假设（如增长率），使用黑色公式计算收入和利润率（禁止硬编码），确保货币格式为 $#,##0，并在假设旁注释数据来源**，最后强制重算以验证零公式错误。
```

如果前面已经安装了，这里它会自主去加载 excel-skills，不用显式调用。

#### docx-skill

这个技能包下面包含的很全，包括技能说明文档、XML 格式说明、script 脚本。

具体不多说，仔细看看很重要这块。

然后我再放一个 case，直接文生文档。

根据我已经加载的 skills，帮我生成有个介绍 document skills 的 word 文档

#### PDF-skill

这是一个综合性的 PDF 操作工具包，支持提取文本和表格、创建新 PDF、合并 / 拆分文档以及处理表单等功能。适用于需要大规模处理、生成或分析 PDF 文档的场景。

这块的 case 有几个我觉得比较好的，我放在下面。

PDF 转图像

直接给提示词让 PDF 逐页输出为图片。

PDF 添加水印

直接给提示词让它在 PDF 里面打水印，现在对中文显示不太友好。

#### pptx-skill

word-skill 和 pptx-skill，我愿称之为 Athropic 最狗的骚操作。

反正解决了 HTML 转 PPT 最痛的一个点。

```
Hey Claude，can you make me a PowerPoint about the Golden Gate Bridge?
```

自主加载 pptx-skill，底层操作 PPT 编辑，并且有专业级的 PPT 设计方法论。

这就是 Claude skills 针对 pptx 的最强杀手锏。

最终进行溢出检查，创建缩略图演示，校验之后的 PPT 如图所示。

### 08. 那我怎么用 Skills？

根据我这几天的实践下来，目前在 Claude.ai 和 Claude Code 均可以达到效果，总体效果上 claude.ai（原生 Claude4.5 + 内置的 document-skills）> claude code（开源版的 document-skills 效果不好）。

我的感觉，Claude.ai 的 document-skills 是更加完整版的，开源的 document-skills 是阉割版的（已经足够震撼）。

#### Claude.ai 渠道

用 skills 之前，还得开 Claude.ai 的 Pro 或者 Max 会员，使用的时候得注意 IP，否则很容易封号。

（太狗了）Claude 默认收集位置和聊天信息，说是改善产品，但是算力紧张的时候机器人就自动扫账户然后把疑似有问题的账号封掉。

下面这俩都得关掉保号。

首先在 Claude 账号里面，启用代码执行和文件创建。

然后开启 Skills，选择开启需要的 Skills。

Anthropic 在 claude.ai 官网提供了多种可供所有用户使用的内置技能，包括：

增强的 Excel 电子表格创建和操作（内置）

专业的 Word 文档创建（内置）

PowerPoint 演示文稿生成（内置）

PDF 创建和处理（内置）

目前支持上传自定义的 skills，仅限于自用。按照技能结构创建技能，将技能文件夹打包为 ZIP 文件。

#### 使用 Claude code

Claude Code 仅支持自定义技能（并没有内置的，所以需要自己手动加载启用）。

将技能创建为包含 SKILL.md 文件的目录，Claude 会自动发现并使用它们。

Claude Code 中的自定义技能基于文件系统（一个文件夹目录 + 各种资源），不需要上传 API。

在 Claude code 里面可以操作 skills，通过斜杠命令启用。

```
/plugin
```

如果是本地加载，一般通过加载 marketplace 获取不同的 skills。目前 marketplace 加载方式有几种（GitHub、网页、本地），比如我加载了俩 marketplace（skills 的整合包）。

其中第一个 anthropic-skills 里面的 skills 有这些。

如果是加载本地的，与 .claude-plugin\marketplace.json 这个文件的配置强相关。

#### AI 原生 IDE+skills

这个就比较随性了，直接拉取 Claude skills 的开源项目到本地，显式调用即可。

比如 cursor、vs code、Trae 等都可以。

注意：一定要让它遵循 SKILL.MD 规范 & 你需要生成的模板规范。

参考这个：

[不想给 Claude 付费，但想玩 Skills？我用国产模型搞定了](https://mp.weixin.qq.com/s?__biz=MzkxOTU4NzEyOQ==&mid=2247518876&idx=1&sn=09f13f81fff20f8b1651872e4e928e67&scene=21&poc_token=HPI6GGmj5H5LOtMNNxO-BIxCWe0sRlvJ3x4GZcVA)

不过说实话，我比较推荐原生的 Claude4.5 模型，这也是官方强烈推荐的搭配，切换国产模型我也试过，就是在多模态的质量核查验证这块，没有办法验证边界以及排版问题，导致最终效果不太满意。

### 09. 一些高级玩法

之前介绍的一篇从参考图里面提取设计的文章，@天生也做成了一个 skills。

就是从参考 UI 图像中提取设计系统，并生成可实施的设计提示。

主要功能：

* 从图像系统化提取设计系统，包含色板、排版、组件分析
* 交互式 MVP PRD 生成
* 模板驱动的工作流（设计系统 → PRD → 实施提示）
* 多变体 UI 生成（3 个移动端，2 个网页端）
* React + Tailwind CSS + Lucide 图标

如下图为提取的 UI 设计系统。

以及对于产品经理来说，专业级的 MVP PRD。

```
使用流程
步骤1：准备输入
用户提供：
-参考图片目录：包含UI截图或设计模型的文件夹路径
-项目想法文件：描述产品概念和目标的文档
-现有PRD(可选)：如果已有PRD,可跳过步骤3
步骤2：从图片提取设计系统
使用通用代理分析图片，提取：
-颜色调色板（主色、次色、强调色、功能色）
-字体系统（字体族、大小、权重、行高）
-组件样式（按钮、卡片、输入框、图标）
-间距系统
-动画/过渡模式
-深色模式变体
步骤3：生成MVPPRD(如需要)
交互式生成产品需求文档，包括：
-产品介绍
-问题陈述和目标受众
-独特卖点
-功能列表和用户故事
-每个屏幕的UX/UI考虑
步骤4：组合最终UI实现提示
将设计系统和PRD结合，生成包含以下内容的完整提示：
-设计美学原则
-项目特定的颜色/字体指南
-应用概述和功能需求
-实现任务（多个UI变体、组件结构）
步骤5：验证React环境
检查现有React项目，如无则指导用户设置环境。
步骤6：实现UI
使用最终提示在React项目中实现UI。
```

### 写在最后

在我看来，Claude Skills 并不是一个功能，而是一种 AI 的经验学习机制。

它让模型能像人一样学习 —— 读手册、积经验、执行任务、迭代提升。

换句话说，Skills 是通用智能体与行业专家之间的桥梁。

当每个企业、每个团队都能积累自己的 Skill 集时，AI 将不再局限于工具，而是真正能结合业务。

Claude Skills 只是开了个头，但这个方向，已经是明确的了。