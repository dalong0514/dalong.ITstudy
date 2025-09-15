## 20250915Writing-in-the-Age-of-LLMs

[Writing in the Age of LLMs](https://www.sh-reya.com/blog/ai-writing/)

Jun 16, 2025 | 11 min read # Writing in the Age of LLMs

In the last couple of years, I've written and reviewed several technical papers and blog posts. I often come across LLM-generated writing that feels slightly "off"—sometimes, to be honest, even uninviting. At the same time, I get tremendous value from using LLMs to draft early versions, summarize dense material, and rephrase messy thoughts.

在过去几年中，我撰写并审阅了多篇技术论文和博客文章。我经常发现由大语言模型（Large Language Model）生成的文字读起来有些「不对劲」—— 坦白地说，有时甚至会让人觉得缺乏吸引力。与此同时，我发现大语言模型在起草初稿、总结复杂材料和重新组织凌乱思绪方面，能给我带来巨大的帮助。

This post details some of my thoughts on writing in a world where much of what we read is now machine-generated. First, I'll lay out some common patterns of bad writing I see from LLM tools. Then, I'll defend some writing habits that people often dismiss as "LLM-sounding" but are actually fine—even helpful—when used intentionally. Finally, I'll share concrete rules and formulas I rely on in my own writing and in the prompts I use to guide LLMs.

这篇文章将详细探讨我在一个如今大量阅读材料由机器生成的世界中，关于写作的一些看法。首先，我将列出我从大语言模型（LLM）工具中看到的一些不良写作的常见模式。接着，我将为一些常被人们斥为「听起来像大语言模型生成」的写作习惯进行辩护，指出它们如果是有意为之，实际上是可行的 —— 甚至是有帮助的。最后，我将分享一些我在自己的写作中以及我用于引导大语言模型的提示词中所依赖的具体规则和公式。

### 01. Common Patterns of Bad Writing I See from LLM Tools

我从大语言模型（Large Language Model，LLM）工具中发现的常见写作弊病

Here are the red flags I keep seeing—mostly from LLMs, but I suppose also from people trying to sound polished and "formal" in the wrong ways.

以下是我经常遇到的一些问题 —— 它们大多源于大语言模型（LLM），但我认为，也有一部分来自那些试图以不恰当的方式追求「polished」（精雕细琢）和「formal」（正式）表达的人。

#### 1.1 Empty "summary" sentences that pretend to conclude a thought

空洞的「总结句」，徒有其表

These often show up at the end of a paragraph and sound like:

这类句子通常出现在段落的末尾，听起来像是：

1 "By following these steps, we achieve better performance."

通过遵循这些步骤，我们能够获得更好的性能。

2 "By internalizing these principles, you can cut through the noise."

通过理解并掌握这些原则，你就可以拨开迷雾，看清事物的本质。

Empty summary sentences feel conclusive, but say nothing. I try to end with parting thoughts that offer something new—or at least something to chew on—but unfortunately, I haven't found a reliable recipe for getting LLMs to write with that kind of substance.

有些空泛的总结句，听起来似乎盖棺定论，但实际上却言之无物。我尝试在文章结尾加入一些新的观点，或者至少是能引人深思的告别语，但很遗憾，我还没有找到一种可靠的方法，能让大语言模型（LLM）写出那种富有深度和内涵的内容。

#### 1.2 Overuse of bullet points and outlines

别滥用项目符号和提纲

LLMs often overuse bullet points, especially nested ones. Lists help when items are parallel and independent, but when ideas are connected or need context, a paragraph is usually better.

大语言模型（LLM）经常会过度使用项目符号，尤其是那种多层嵌套的项目符号。当信息条理清晰、彼此独立时，列表确实能帮大忙；但如果这些想法是相互关联的，或者需要更多的背景信息来解释时，通常来说，用段落来表达会是更好的选择。

#### 1.3 Flat sentence rhythm

句式节奏单一

When every sentence is the same length, the writing lacks rhythm and becomes harder to follow. Varied sentence lengths keep readers engaged. They help signal emphasis, guide attention, and control the pace.

当每个句子的长度都相同时，文章就会缺乏节奏感，变得更难阅读。句子长度多样化能让读者保持专注。它们有助于突出重点、引导读者的注意力，并控制阅读节奏。

Bad example: We recently launched a conversational AI feature that lets users ask questions in plain English and get responses based on their past activity and current session. The system searches a database of help articles, ranks the most relevant ones using a custom scoring function, and passes the top result into a language model to generate the final answer. We spent weeks optimizing each step to keep latency under 300 milliseconds, including caching, pruning irrelevant articles, and tuning prompt templates.

坏的示例：我们最近推出了一项对话式 AI（Conversational AI）功能，用户可以用日常的英语提问，系统会根据他们过去的操作记录和当前的会话内容给出回答。这个系统会搜索一个帮助文章的数据库，利用自定义的评分函数对最相关的文章进行排名，然后将最符合要求的结果输入到语言模型（Language Model）中，生成最终的答案。为了将延迟控制在 300 毫秒以内，我们花了数周时间优化了每个环节，这包括数据缓存、剔除不相关的文章以及调整提示模板（Prompt Template）等措施。

Good example: We just launched a new conversational AI feature. It answers user questions in plain language, using context from the current session. The system searches help articles, scores them with a custom ranking function, feeds the top result into a fine-tuned language model, and runs in under 300ms using caching, pruning, and prompt tuning techniques.

好的示例：我们刚刚推出了一项新的会话式 AI（Conversational AI）功能。它能利用当前会话的上下文，用通俗易懂的语言回答用户问题。该系统会搜索帮助文章，通过自定义的排名函数对它们进行评分，然后将最相关的结果提供给一个经过微调的语言模型。借助缓存（caching）、剪枝（pruning）和提示调优（prompt tuning）等技术，整个过程可在 300 毫秒内完成。

#### 1.4 Not the right subject

主语选择不当

Every sentence has a subject and a predicate. The subject tells us what the sentence is about; the predicate tells us what the subject is doing or what's being said about it. Choosing the right subject helps keep the reader focused on the main idea. A common issue in LLM-generated writing is that it often picks the wrong subject. Consider two variations of the previous sentence:

每个句子都由主语和谓语构成。主语点明了句子的核心内容，而谓语则说明了主语正在做什么，或描述了主语的特征。选择恰当的主语能帮助读者聚焦于句子的主要思想。然而，在大语言模型（LLM）生成的文本中，一个普遍存在的问题是主语选择不当。请看前面那句话的两种不同表达：

Bad example: Readers are better guided when the subject matches the main idea of the sentence.

Good example: Choosing the right subject keeps the writing clear and focused.

In the bad version, the subject is readers, even though the sentence is about sentence structure, not people. The good version keeps the subject aligned with the topic, making the writing more coherent and easier to follow.

在较差的版本中，主语是「读者」，尽管句子讨论的是句子结构，而非具体的人。优秀的版本则能保持主语与讨论的主题相符，这使得文章更连贯，也更容易理解。

#### 1.5 Low information density

信息密度不高

The intro below was generated by Gemini 2.5 Pro when asked to draft a blog post on writing in the age of LLMs:

下面这段介绍是 Gemini 2.5 Pro 在被要求撰写一篇关于在大语言模型（Large Language Model）时代如何写作的博客文章时生成的：

> As someone who writes, reviews, and deconstructs complex information for a living, I've developed a strong allergy to bad writing. And lately, a lot of that bad writing has a specific, synthetic flavor—the unmistakable scent of an LLM. This post is a guide to navigating the new world of writing, with or without LLM assistance. First, I'll cover the true pitfalls of LLM-generated text—the red flags that make it feel sterile and unconvincing.

作为一个以撰写、审阅和解构复杂信息为生的人，我对糟糕的文字变得异常敏感。而最近，许多糟糕的文字都带有一种特定的、人工合成的味道 —— 那种大语言模型（Large Language Model，LLM）文本特有的，一眼就能识别出来的「气味」。这篇文章将指导你如何驾驭写作的新世界，无论是否借助 LLM 的帮助。首先，我将探讨由 LLM 生成文本的真正陷阱 —— 那些让它读起来索然无味、缺乏说服力的危险信号。

It sounds nice but says very little. The sentences are well-formed, but there's no concrete insight, no framing, no momentum.

这话说得好听，但内容却空泛无物。句子本身写得流畅，但缺乏具体的真知灼见，没有清晰的论述视角，也缺乏推动文章进展的势头。

#### 1.6 Vagueness

模糊性

LLM writing often avoids specificity. It refers to ideas without defining them and makes claims without evidence. E.g., "Some experts say prompt engineering is becoming less important. The ability to simply prompt LLMs can have a major impact on productivity." But who are the experts? What exactly is the impact? On what kind of work, and for whom? Without concrete references or clear stakes, the writing feels vague and insubstantial.

大语言模型（LLM）生成的文本常常缺乏具体性。它在没有明确定义概念的情况下就提及它们，并在没有证据的情况下提出主张。例如，它可能会写道：「一些专家说提示工程（prompt engineering）正在变得不那么重要。仅仅通过提示词与大语言模型交互，就能对生产力产生重大影响。」但这些专家到底是谁？具体的影响是什么？针对哪种类型的工作，又对哪些人群产生影响？如果没有具体的引用来源或清晰的背景情境，这类文本就会显得模糊且缺乏实质内容。

#### 1.7 Overuse of demonstrative pronouns

指示代词的过度使用

LLM writing leans heavily on words like this, that, these, and those—often without a clear noun in sight. I make this mistake myself, and my advisor flags it every time in my writing (lol). For example: "This creates friction in production." But what is this? If the noun isn't in the same sentence or immediately before, the reference becomes vague and the point gets lost.

大语言模型（LLM）在写作中大量使用「this」、「that」、「these」和「those」等指示代词，常常没有明确的指代对象。我自己也经常犯这个错误，我的导师每次都会在我的文章里把它标出来（笑）。例如，如果写道：「This creates friction in production.」但这个「this」到底指代的是什么呢？如果被指代的名词不在同一个句子中，或没有紧接在前面，那么指代关系就会变得模糊不清，导致读者难以抓住重点。

#### 1.8 Fluency without understanding

流利却不传达信息

Some writing sounds correct but doesn't explain anything. This happens a lot when the writer—or the model—lacks awareness of what the audience actually knows. E.g., "LLMs use attention mechanisms to generate contextually appropriate responses." While this may feel like a good sentence, it says nothing if the reader doesn't already know what attention is or how it works.

有些文字听起来似乎正确，但实际上什么都没有解释。当作者 —— 或者模型 —— 不了解读者的实际知识水平时，这种情况经常发生。例如，「大语言模型（LLMs）使用注意力机制来生成符合语境的响应。」虽然这句话听起来不错，但如果读者不了解注意力机制是什么或它是如何工作的，那么这句话就毫无意义。

Moreover, I find that LLMs make up terms that don't exist, especially for technical content. I've seen an LLM write something like "We used GPT-4 for summarization, but it hallucinated details, so we added retrieval grounding." What is "retrieval grounding?" This is not a term I've heard before.

此外，我发现大语言模型（LLMs）还会编造一些不存在的术语，尤其是在处理技术内容时更是如此。我曾见过某个大语言模型写出这样的话：「我们使用 GPT-4 进行总结，但它编造了不实的细节，于是我们加入了检索增强（retrieval grounding）。」那么，「检索增强」到底是什么呢？这并不是我之前听说过的术语。

In summary, LLMs can't reliably distinguish what's assumed knowledge and what needs explanation, so they often gloss over the hard parts, and a human writer has to fill that gap.

总而言之，大语言模型（LLMs）无法可靠地分辨哪些是读者已知的基础知识，哪些又需要详细阐释。因此，它们常常会对那些较难理解的部分轻描淡写，而这个空白就需要由人类作者来填补。

### 02. Writing Patterns People Flag as "LLM-Like," But Are Actually Fine

人们误以为是「大语言模型（LLM）风格」但其实不错的写作模式

I'm including this section because I've seen people overcorrect in response to LLM writing habits, cutting patterns that are actually helpful when used well. Some structures get labeled as "LLM-sounding" or flagged during review, even though they're common and effective rhetorical tools. Just because something appears in model-generated text doesn't make it bad writing. The goal isn't to avoid sounding like a model; it's to write with clarity, intention, and control.

之所以要写这一部分，是因为我发现有些人对大语言模型（LLM）的写作习惯反应过度，以至于舍弃了一些本该很好用的写作模式。有些结构被贴上了「听起来像大语言模型（LLM）」的标签，或是在审阅时被挑出来，但实际上它们是非常常见且有效的修辞手法。一种表达方式仅仅因为它出现在模型生成的文本中，并不代表它就是不好的写作。我们的目标不是避免「像」模型，而是要做到行文清晰、表达有意识、掌控自如。

#### 2.1 Intentional repetition

刻意重复

The effectiveness of repetition depends on how it supports the idea. When it helps clarify or reinforce something complex, it adds value. Good writing also makes space for a bit of predictability—places where the reader can skim or settle—but repetition still needs to be purposeful.

重复是否有效，取决于它如何支持核心思想。当重复有助于阐明或加强复杂内容时，它就能增添价值。优秀的写作也会留出一些可预测的空间 —— 让读者可以快速浏览或安心阅读 —— 但即使如此，重复也必须有其目的。

Example: Vector databases store embeddings, or mathematical representations that capture semantic meaning in hundreds of dimensions. In other words, vector databases help find results that are "close" in meaning, not just exact text matches.

向量数据库存储的是嵌入（embeddings），它们是在数百个维度中捕捉语义意义的数学表示。换句话说，向量数据库帮助找到的是意义上「接近」的结果，而不仅仅是精确的文本匹配。

#### 2.2 Signposting phrases

提示性短语

Phrases like "essentially," "in short," "the point is…" are fine if they're followed by something useful. I like to use them when the writing gets dense, as a signpost helps the reader reorient.

诸如「本质上」、「简而言之」、「重点是……」之类的短语，如果其后跟着有用的内容，就可以用得很好。我喜欢在文章内容比较密集时使用它们，因为这样的提示语能够帮助读者理清思路，找回阅读方向。

Example: Essentially, instead of classifying the document as a whole, we classify each section independently.

本质上，我们不是将整个文档作为一个整体来分类，而是独立地对每个部分进行分类。

#### 2.3 Parallel structure

并行结构

Sometimes readers see a repeated rhythm and assume it's LLM. But parallel structure can help organize related ideas and makes sentences easier to follow.

有时，读者看到重复的句式结构时，会认为这是大语言模型（LLM）生成的内容。然而，平行结构实际上有助于梳理相关联的观点，并让句子更易于理解。

Example: The system scales across inputs, stays responsive under load, and returns consistent results even with noisy prompts.

示例：该系统能够适应多种输入，在高负载下也能保持响应速度，并且即使输入的指令不够精确，也能返回一致的结果。

The rhythm supports clarity, and each clause delivers new information.

行文的节奏有助于保持清晰度，并且每个从句都提供新的信息。

#### 2.4 Section headings that echo a structure

章节标题要呼应文章结构

E.g., "Why X fails," "What to do instead," "How to know if it worked." These are clear and predictable, which is what we desire. Predictability isn't bad when the content under each heading is clear.

例如，「为什么 X 会失败？」「我们应该如何应对？」以及「怎样判断它是否有效？」。这些表述都非常清晰且具有可预测性，这正是我们所追求的目标。毕竟，只要每个标题下的内容都足够明确，可预测性本身并非坏事。

#### 2.5 Declarative openings

直述式开头

Starting a section with a bold claim or topic sentence can feel robotic if the writing doesn't back it up. But when used to set expectations—and followed by evidence—such openings can help keep the reader grounded.

如果文章内容无法支撑，那么用一个开门见山的主张或概括性语句来开启一个章节，可能会显得生硬呆板。但若能用它来引导读者预期，并辅以确凿证据，这种开头方式就能帮助读者更好地理解和把握内容。

Example: LLM evaluations are hard to get right. Many rely on user-defined gold labels or vague accuracy metrics, which do not work for subjective or multi-step tasks.

大语言模型（LLM）的评估工作很难做到位。许多评估方法依赖于用户预设的「黄金标准」标签，或是模糊不清的准确性指标，而这些方法在面对主观性强或需要多步骤完成的任务时，往往力不从心。

#### 2.6 Em dashes

长破折号（Em dashes）

Em dashes are great for inserting clarifying details, quick shifts, or sharp asides—without breaking the sentence. I love them. When used well, they add rhythm and emphasis. They help writing flow the way people actually talk.

长破折号（Em dashes）非常适合用来插入解释性细节、快速切换话题，或是添加精辟的旁白 —— 同时又不会打断句子的流畅性。它们深受人们喜爱。如果运用得当，长破折号能为文章增添韵律感和强调效果，让文字表达像日常对话一样自然流畅。

### 03. How I Write with LLMs

我如何使用大语言模型（LLMs）进行写作

My writing loop is built around one goal: keep the momentum going. I don't want to get stuck staring at a blank screen or endlessly tweaking sentences that don't quite land. Most of my writing, whether for a paper or a blog post, follows the same high-level loop: plan an outline (on paper or in my head), generate a draft, read what I wrote, critique it, and revise. The loop can run at different granularities—sometimes I work a sentence at a time; sometimes I write entire sections before editing.

我的写作流程围绕一个目标展开：保持写作的势头。我不想陷入盯着空白屏幕发呆，或者无休止地修改那些不尽如人意的句子。我的大部分写作，无论是写论文还是写博客文章，都遵循同一个高级循环：规划大纲（在纸上或在我脑海中），生成初稿，阅读我写的内容，审阅评估，然后修改。这个循环的精细程度可以有所不同 —— 有时我一次只修改一个句子；有时我会在编辑之前先写完整个部分。

Writing breaks down in different places for different people. Some stall in the planning phase, unsure how to turn ideas into structure. Others move fast through first drafts but get bogged down in revision. Personally, I tend to move quickly through the outline and get stuck on phrasing—how to say something clearly, not what I want to say. I'm usually sharper at critiquing than generating, which means I often rely on the LLM to help get past those sticking points.

对于不同的人来说，写作的症结往往出现在不同环节。有些人可能在规划阶段就停滞不前，不知道如何将零散的想法组织成清晰的结构。另一些人则能快速写完初稿，却在修改润色时感到举步维艰。就我个人而言，我通常能很快地列出大纲，但总在斟酌措辞时犯难 —— 纠结于如何清晰地表达，而非表达什么内容。我更擅长评判作品而非创作，这意味着我经常依赖大语言模型（LLM）来帮助我突破这些瓶颈。

My strategy is to identify where the slowdown is happening and hand off just enough of the task to the LLM to regain momentum. Here's what that looks like in practice for me:

我的策略是找出导致效率降低的地方，然后将恰好足够的任务交给大语言模型（LLM）以恢复进展。具体来说，我的实践经验是：

#### 3.1 Narrate the story to the model

向模型讲述故事

When I start writing (especially for something like a paper intro), I begin by "talking through" the structure as if I'm explaining it to a colleague. I paste that rough narrative into the LLM and ask it to generate a detailed outline. I don't move forward until that outline feels structurally solid.

当我开始写作时（尤其是像论文引言这样的内容），我会先「口头梳理」一下文章的结构，就像在向同事解释一样。我会把这段粗略的叙述粘贴到大语言模型（LLM）中，然后让它生成一个详细的提纲。只有当这个提纲在结构上足够完善时，我才会着手进行下一步。

#### 3.2 Write the paragraph myself, even if it's rough

亲自动手写段落，哪怕再粗糙也没关系

Once I have the outline, for every paragraph, I try to write the actual paragraph myself, even if it's ugly. If I know what I want to say but can't get the sentence out (unfortunately, this happens often), I'll write a half-baked version and ask the LLM to help me finish it.

一旦有了大纲，对于每个段落，我都会尝试自己亲自动手去写，哪怕初稿显得再粗糙也没关系。如果我知道自己想表达什么，却不知如何措辞（不幸的是，这种情况经常发生），我就会先写一个不成熟的版本，然后请大语言模型（LLM）帮我润色和完成。

This post includes a real example. I typed: "In the last couple of years, I've written and reviewed several technical papers and blog posts. Something always feels slightly off, enough to make the writing quietly uninviting. At the same time, I feel like I get tremendous value from using LLMs to write…" And then just added: "finish it". The model gave me a few completions. I picked the best one, made a small edit, and moved on.

本文包含一个真实的例子。我这样输入：「在过去的几年里，我写过并审阅了几篇技术论文和博客文章。总有些细节不够到位，使得文章读起来不那么引人入胜。同时，我发现使用大语言模型（LLM）进行写作能带来巨大价值……」接着我只需补充一句：「完成它。」模型给出了几个续写方案。我从中选择了最好的一个，做了小修改，然后继续了。

#### 3.3 Use scoped rewrite strategies during revision

修改时采用有针对性的重写策略

When I re-read a sentence or paragraph that feels off, I don't simply ask the model to "make it better." I ask something specific; usually for the LLM to follow one of the following rhetorical patterns.

当我重新读到一个句子或段落，觉得它读起来不太顺畅时，我不会简单地要求模型（model）「把它改好」。我会提出具体的要求；通常是让大语言模型（LLM）按照以下某种修辞模式进行修改。

The first is to put the subject and verb close together, at the beginning of the sentence. The second pattern I use is SWBST: Somebody Wanted But So Then. It's a basic storytelling structure—often taught in early writing education, but surprisingly effective in technical contexts because it helps convey motivation, conflict, and resolution in a compact form. The "Somebody" is the actor, "Wanted" states the goal, "But" introduces the obstacle, "So" explains the response, and "Then" describes the outcome. In technical writing, this structure makes it easier to show how a decision was made or how a system evolved in response to a problem. E.g., consider the sentence "We used GPT-4 for summarization. We wanted fluent answers, but it hallucinated facts. So we added a retrieval step. Then we re-ranked outputs based on citation accuracy." Each sentence does one job. The pattern is simple, but it makes the logic of a decision easy to follow.

首先，是将句子的主语和谓语紧密地放在一起，置于句首。我使用的第二种模式是 SWBST：某人 - 想要 - 但是 - 所以 - 结果（Somebody Wanted But So Then）。这是一种基本的叙事结构 —— 虽然常在早期的写作教育中教授，但在技术语境中却出奇地有效，因为它有助于以精炼的形式传达动机、冲突和解决方案。「某人」代表行动者，「想要」定义了目标，「但是」提出了障碍，「所以」阐明了应对措施，「结果」则揭示了结局。在技术写作中，这种结构使得展示如何做出决策，或者一个系统如何针对问题进行演进而变得更加容易。例如，考虑下面这个句子：「我们使用 GPT-4 进行总结。我们想要流畅的答案，但是它会产生事实幻觉。所以我们添加了一个检索步骤。然后我们根据引用准确性重新排序了输出。」每个句子各司其职。这种模式虽然简单，但它能让决策背后的逻辑一目了然。

### 04. Parting Thoughts

结语

It's now cheap to generate medium-quality text—and even high-quality text, when the scope is narrow and well-defined. But figuring out what to say, how to frame it, and when and how to go deep is still the hard part. That's what takes judgment, and that's what LLMs can't do for me (yet).

如今，生成中等质量的文本已经成本低廉，甚至在范围狭窄且界定明确的情况下，也能生成高质量的文本。然而，真正困难的部分在于弄清楚该表达什么、如何组织措辞，以及何时以何种方式进行深入阐述。这些都需要人类的判断力，而这正是大语言模型（LLMs）目前还无法替我完成的工作。

Perhaps the most important mark of good writing, particularly in the age of LLM-generated text, is that the contribution is commensurate with the length. The reader walks away feeling their time was well spent, and this is the bar I strive to meet.

或许，衡量一篇好文章最重要的标准 —— 尤其是在大语言模型（LLM）生成文本盛行的时代 —— 在于它的价值与篇幅是匹配的。读者读完后会觉得自己的时间没有白费，这也是我一直努力想要达到的目标。