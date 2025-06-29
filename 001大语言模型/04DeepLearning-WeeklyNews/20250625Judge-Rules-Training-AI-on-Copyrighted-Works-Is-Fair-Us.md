## 20250625Judge-Rules-Training-AI-on-Copyrighted-Works-Is-Fair-Us

[Judge Rules Training AI on Copyrighted Works Is Fair Use, Agentic Biology Evolves, and more...](https://www.deeplearning.ai/the-batch/issue-307/)

Dear friends,

On Monday，a United States District Court ruled that training LLMs on copyrighted books constitutes fair use. A number of authors had filed suit against Anthropic for training its models on their books without permission. Just as we allow people to read books and learn from them to become better writers, but not to regurgitate copyrighted text verbatim，the judge concluded that it is fair use for AI models to do so as well.

周一，美国地方法院裁定，使用受版权保护的书籍来训练大语言模型（LLMs）属于合理使用。此前，一些作者曾起诉 Anthropic，指控其未经许可就使用他们的书籍来训练模型。法官的结论是，正如我们允许人们通过阅读书籍来学习并成长为更优秀的作家，但不能逐字逐句地照搬受版权文本一样，AI 模型这样做也属于合理使用。

Indeed，Judge Alsup wrote that the authors' lawsuit is「no different than it would be if they complained that training schoolchildren to write well would result in an explosion of competing works.」While it remains to be seen whether the decision will be appealed，this ruling is reasonable and will be good for AI progress.（Caveat：I am not a lawyer and am not giving legal advice.)

确实，法官 Alsup 写道，作者的诉讼「与他们抱怨训练学童写出好文章会导致竞争作品爆炸式增长，没有什么不同。」虽然该裁决是否会上诉还有待观察，但这项裁决是合理的，并将有利于 AI 进展。（请注意：我不是律师，不提供法律建议。）

AI has massive momentum，but a few things could put progress at risk:

AI 发展势头迅猛，但有几件事可能会让它的前进步伐面临风险：

1 Regulatory capture that stifles innovation，including especially open source，in the false name of「AI safety」

监管俘获（Regulatory capture）—— 在「AI 安全」的虚假名义下，扼杀创新，特别是对开源项目的创新。

2 Loss of access to cutting-edge semiconductor chips（the most likely cause would be war breaking out in Taiwan)

无法获得尖端半导体芯片（最可能的原因是台湾地区爆发战争）

3 Regulations that severely impede access to data for training AI systems

严重阻碍 AI 系统训练数据获取的法规

Access to high-quality data is important. Even though the mass media tends to talk about the importance of building large data centers and scaling up models，when I speak with friends at companies that train foundation models，many describe a very large amount of their daily challenges as data preparation. Specifically，a significant fraction of their day-to-day work follows the usual Data Centric AI practices of identifying high-quality data（books are one important source），cleaning data（the ruling describes Anthropic taking steps like removing book pages' headers，footers，and page numbers），carrying out error analyses to figure out what types of data to acquire more of，and inventing new ways to generate synthetic data.

获取高质量数据至关重要。尽管大众媒体往往热衷于讨论建设大型数据中心和扩展模型的重要性，但当我与那些正在训练基础模型的朋友们交流时，他们中的许多人却表示，日常工作中的大部分挑战都集中在数据准备上。具体来说，他们很大一部分日常工作都遵循着以数据为中心的人工智能（Data Centric AI）常规实践：识别高质量数据（书籍是其中一个重要来源），清理数据（例如，Anthropic 就曾采取措施，移除书籍页面的页眉、页脚和页码），进行错误分析以明确需要获取更多哪些类型的数据，以及探索生成合成数据的新方法。

I am glad that a major risk to data access just decreased. Appropriately，the ruling further said that Anthropic's conversion of books from paper format to digital — a step that's needed to enable training — also was fair use. However，in a loss for Anthropic，the judge indicated that，while training on data that was acquired legitimately is fine，using pirated materials（such as  texts downloaded from pirate websites）is not fair use. Thus，Anthropic still may be liable on this point. Other LLM providers，too，will now likely have to revisit their practices if they use datasets that may contain pirated works.

我很高兴数据访问方面的一个主要风险刚刚有所降低。判决书还指出，Anthropic 将纸质书籍转换成数字格式（这是进行模型训练的必要步骤），也被认定为合理使用，这很恰当。不过，对于 Anthropic 来说，也有不利的一面：法官指出，虽然使用合法获取的数据进行训练是允许的，但使用盗版材料（比如从盗版网站下载的文本）则不属于合理使用。因此，Anthropic 在这一点上可能仍然需要承担法律责任。这也意味着，其他大语言模型（LLM）提供商，如果他们使用的数据集可能包含盗版作品，现在或许也需要重新审视自己的做法了。

Overall，the ruling is positive for AI progress. Perhaps the biggest benefit is that it reduces ambiguity with respect to AI training and copyright and（if it stands up to appeals）makes the roadmap for compliance clearer. This decision indicates it is okay to train on legitimately acquired data to build models that generate transformational outputs，and to convert printed books to digital format for this purpose. However，downloading from pirate sites（as well as permanently building a「general purpose」library of texts，stored indefinitely for purposes to be determined, without permission from the relevant copyright holders）are not considered fair use.

总体来看，这项裁决对人工智能（AI）的进步是一个好消息。它最大的好处或许在于，它减少了人工智能训练和版权方面的模糊性，而且（如果能经受住上诉的考验）会使合规路线变得更加清晰。这项裁决指出，使用合法获取的数据来训练模型，以生成具有变革性的内容是允许的，为了这个目的将纸质书籍转换为数字格式也同样被认可。然而，从盗版网站下载内容，以及未经相关版权所有者许可，无限期地存储一个「通用」文本库（以备未来不确定的用途），则不被视为合理使用。

I am very sympathetic with the many writers who are worried about their livelihoods being affected by AI. I don‘t know the right solution for that. Society is better off with free access to more data; but if a subset of people is significantly negatively affected，I hope we can figure out an arrangement that compensates them fairly.

我非常理解许多作家对生计可能受到 AI 影响的担忧。对此，我也不知道最佳的解决方案。社会无疑会因为数据能够自由获取而变得更好；但如果有一部分人 —— 比如这些作家 —— 的利益因此受到显著损害，我希望我们能找到一种妥善的安排，确保他们能得到公平的补偿。

Keep building!

Andrew

### News

#### Meta Befriends Scale AI

Meta 与 Scale AI 建立合作

Meta hired the leadership of ScaleAI and put billions into the data-labeling startup to accelerate its AI efforts.

Meta 聘请了 ScaleAI 的核心领导团队，并向这家数据标注初创公司投入巨资，以加速其在 AI 领域的进展。

What's new: Meta recruited Scale AI founder and CEO Alexandr Wang along with members of his team and pumped $14.3 billion into the startup in a new deal. The agreement，which was inked as the United States Federal Trade Commission investigates Meta over its acquisitions of Instagram and WhatsApp，could avoid the government scrutiny that acquiring Scale AI outright would have invited.

最新消息：Meta 不仅招募了 Scale AI 创始人兼首席执行官 Alexandr Wang 及其团队成员，还通过一项新协议向这家初创公司注资 143 亿美元。这项协议签署之际，美国联邦贸易委员会（Federal Trade Commission）正在调查 Meta 收购 Instagram 和 WhatsApp 的案件，此举或许能帮助 Meta 避免直接收购 Scale AI 可能引发的政府审查。

How it works: The agreement between Meta and Scale AI gives Meta an infusion of high-profile talent and priority access to Scale AI's large-scale data operations. It doubles the valuation of Scale AI，which was valued at $13.8 billion last year，and provides funding to fuel growth and reward shareholders. The terms echo similar deals last year between Microsoft and Inflection AI, Amazon and Adept AI，and Google and Character.AI.

运作方式：Meta 和 Scale AI 之间的这项协议，为 Meta 带来了大量知名人才，并使其能够优先使用 Scale AI 的大规模数据处理能力。这项协议使 Scale AI 的估值翻倍（该公司去年估值为 138 亿美元），同时为 Scale AI 提供了发展资金，并回馈了股东。其条款与去年 Microsoft 和 Inflection AI、Amazon 和 Adept AI，以及 Google 和 Character.AI 之间达成的类似交易异曲同工。

1 Wang will oversee a Meta research lab focused on developing superintelligence，a term that refers loosely to artificial intelligence that exceeds human intelligence, The New York Times reported. The 28-year-old executive has expertise in model training and evaluation.

据《纽约时报》报道，王将负责监督 Meta 旗下的一家研究实验室，该实验室致力于开发「超级智能」—— 这个词宽泛地指代超越人类智慧的人工智能。这位 28 岁的高管在模型训练和评估方面拥有丰富的专业知识。

2 Meta's investment in Scale AI bought 49 percent of the startup in non-voting shares.

Meta 投资了 Scale AI，获得了这家初创公司 49% 的无投票权股份。

3 Scale AI will use the investment to「accelerate innovation and strengthen strategic partnerships,」the company said. It plans to distribute some of the funds to shareholders and vested equity holders.

Scale AI 表示，将利用这笔投资「加速创新和加强战略伙伴关系」。该公司计划将部分资金分配给股东和已归属股权的持有人。

4 Scale AI Chief Strategy Officer Jason Droege will take over as Scale AI's interim CEO.

Scale AI 的首席战略官（Chief Strategy Officer）Jason Droege 将出任 Scale AI 的临时首席执行官（CEO）。

5 Since Meta's investment became publicly known，some of Scale AI's major customers including Google and OpenAI announced they would seek new providers of data labeling services.

自从 Meta 投资 Scale AI 的消息公开后，Scale AI 的一些主要客户，包括 Google 和 OpenAI，都宣布将寻找新的数据标注服务提供商。

Behind the news: Wang and his team could help fulfill Meta's need for top AI talent.

新闻深读：Wang 和他的团队有望助力 Meta 补齐顶尖 AI 人才的短板。

1 Wang founded Scale AI in 2016，when he was a teenager. As the company's business grew，he found himself，at the age of 24，the world's youngest self-made billionaire.

Wang 于 2016 年创立了 Scale AI，当时他还是个青少年。随着公司业务的蓬勃发展，Wang 在 24 岁时就成为了全球最年轻的白手起家亿万富翁。

2 Meta's AI efforts have lost traction since its Llama 4 large language model met with a cool reception. In April，unnamed Meta employees told Fortune Meta's AI lab was「dying a slow death.」The same month，AI research chief Joelle Pineau stepped down after 8 years in the position.

Meta 在人工智能（AI）方面的努力进展缓慢，自从其 Llama 4 大语言模型（LLM）反响平平以来，这一趋势愈发明显。4 月，《财富》杂志援引未具名的 Meta 员工的话称，Meta 的 AI 实验室「正在缓慢走向衰落」。同月，担任 AI 研究主管长达 8 年的 Joelle Pineau 宣布辞职。

3 Since then，Meta has been on a mission to add firepower to its AI divisions. CEO Mark Zuckerberg discussed acquiring，among others，Safe Superintelligence，founded by former OpenAI chief scientist Ilya Sutskever and former head of Apple AI Daniel Gross，and Perplexity AI.

从那时起，Meta 一直致力于增强其 AI 部门的实力。首席执行官马克·扎克伯格讨论了多项收购意向，其中包括由前 OpenAI 首席科学家 Ilya Sutskever 和前苹果 AI 负责人 Daniel Gross 创立的 Safe Superintelligence 公司，以及 Perplexity AI 公司。

Why it matters: Meta is racing with other Silicon Valley giants to establish and maintain a decisive lead in AI，and that requires making big bets. In this deal，it gains a star AI entrepreneur as well as closer access to Scale AI's pipeline of high-quality training data. For Scale AI，Meta's enormous resources and know-how could come in handy as it contends with competitors and extends its business into new areas. For the AI community，Meta's willingness to spend such an immense sum for top talent could boost engineers' salaries and block less-moneyed competitors.

Why it matters：Meta 正与其他硅谷科技巨头激烈竞争，力求在人工智能（AI）领域取得并保持绝对领先地位，这需要投入巨大的资源。通过这笔交易，Meta 不仅迎来了一位明星 AI 企业家，还能更紧密地获取 Scale AI 高质量的训练数据。对 Scale AI 而言，面对激烈的市场竞争并拓展新业务时，Meta 庞大的资源和专业知识将大有助益。而对于整个 AI 社区来说，Meta 愿意为顶尖人才投入如此巨额资金，可能会推高工程师的薪资水平，同时也可能让那些资金实力较弱的竞争对手面临更大挑战。

We're thinking: Meta has made valuable contributions to open-weights models，including Llama 4，and it has played an important role in making open models competitive with their closed counterparts. We look forward to seeing what the new team will accomplish!

我们认为：Meta 已经为开源模型（open-weights models）做出了宝贵贡献，其中就包括 Llama 4。同时，Meta 在使开放模型能够与闭源模型（closed counterparts）竞争方面发挥了重要作用。我们期待看到新团队将带来怎样的成果！

#### A Research Agent for All Biology

适用于所有生物学领域的研究智能体

An agent designed for broad biological research could accelerate the work of scientists in specialties from anatomy to zoology.

一个专为广泛生物学研究设计的 AI 智能体（AI agent），有望加速科学家们在从解剖学到动物学等各种专业领域的研究工作。

What's new: Kexing Huang and colleagues at Stanford，Princeton，University of Washington，Arc Institute，and Genentech introduced Biomni，an agent that performs tasks in genomics，immunology，microbiology，neuroscience，pathology，and much more. You can join a waitlist to get access. The authors intend to release the system as open source.

最新动态：来自斯坦福大学、普林斯顿大学、华盛顿大学、Arc Institute 和 Genentech 的 Kexing Huang 及同事们，共同推出了 Biomni。这是一款 AI 智能体（AI agent），能够在基因组学、免疫学、微生物学、神经科学、病理学等众多领域执行任务。目前，您可以加入等候名单以获取访问权限。作者们计划将该系统作为开源项目发布。

[Biomni: A General-Purpose Biomedical AI Agent | bioRxiv](https://www.biorxiv.org/content/10.1101/2025.05.30.656746v1.abstract)

How it works: The authors assembled a collection of tools，software packages，and databases. Then they built an agent based on Claude 4 Sonnet that draws upon those resources to answer questions，propose hypotheses，design processes，analyze datasets，generate graphs，and so on.

工作原理：研究人员收集了一系列工具、软件包和数据库。随后，他们构建了一个基于 Claude 4 Sonnet 的 AI 智能体（agent），该智能体能够利用这些资源回答问题、提出假设、设计流程、分析数据集、生成图表等等。

1 The authors prompted Claude 3.5 Sonnet（the most current version when the work started）to extract the relevant tasks，tools，and databases used in 2,500 recent papers（100 from each of 25 specialties). They filtered the list manually to settle on 150 tools and nearly 60 databases. To that，they added around 100 popular biological software packages.

为了进行这项工作，研究人员使用 Claude 3.5 Sonnet（在项目启动时，这是最新版本）分析了 2500 篇近期论文。这些论文来自 25 个不同的专业领域，每个领域选取了 100 篇。他们让 AI 自动提取论文中提到的任务、工具和数据库，然后研究人员手动筛选了一遍，最终整理出 150 种常用工具和近 60 个数据库。在此基础上，他们还补充了大约 100 个广受欢迎的生物学软件包。

2 At inference，given a query，Biomni prompts Claude 4 Sonnet to determine which tools，packages，and databases are needed. Then it prompts the model to build a step-by-step plan to produce a response.

在推理阶段，当接收到一个查询时，Biomni 会指示 Claude 4 Sonnet 识别出需要哪些工具、软件包和数据库。然后，它会提示模型制定一个分步计划来生成响应。

3 From there，the agent follows the CodeAct framework：Given a prompt to follow the plan or results of executing code，it can ask for clarification，write code and execute it，and return the result. The agent continues to follow the plan，generate code，and reason iteratively until it's ready to produce a final response.

接下来，AI 智能体（AI Agent）会遵循 CodeAct 框架运作：当它接收到一个提示，要求其遵循某个计划或处理代码执行的结果时，它可以提出疑问以寻求澄清，接着编写并执行代码，然后返回执行结果。AI 智能体将持续地遵循计划、生成代码并反复地进行推理，直到它准备好给出最终的响应。

4 At each intermediate output，a different copy of Claude 4 Sonnet judges whether the model followed a proper procedure or confabulated its output. If the judge determines the model fell short，it tells the agent to repeat the step. If not，execution continues normally.

\在每次中间输出时，另一个 Claude 4 Sonnet 实例会判断模型是否遵循了正确的程序，或者是否虚构（confabulated）了其输出。如果判断模型未能达到要求，它会指示 AI 智能体重复该步骤。如果符合要求，则正常继续执行。

Results: Biomni outperformed Claude 4 Sonnet alone，as well as the same model with access to research literature，on Lab-bench，a biomedical subset of Humanity's Last Exam，and eight other datasets，as well as three practical case studies.

结果：Biomni 在 Lab-bench （一个属于 Humanity's Last Exam 的生物医学子集）、其他八个数据集以及三个实际案例研究中，其表现都超越了单独的 Claude 4 Sonnet 模型，以及访问了研究文献的 Claude 4 Sonnet 模型。

1 On the subset of Humanity's Last Exam，Biomni（17.3 percent accuracy）outperformed Claude 4 Sonnet alone（6 percent accuracy）and Claude 4 Sonnet with access to research（12.2 percent accuracy).

在名为「人类的最后一次考试（Humanity's Last Exam）」的数据子集上，Biomni 的准确率达到 17.3%，表现优于单独使用 Claude 4 Sonnet（准确率为 6%），也超过了可以查阅研究资料的 Claude 4 Sonnet（准确率为 12.2%）。

2 Asked to diagnose a patient based on a full genome，Biomni achieved roughly 85 percent accuracy，while Claude 4 Sonnet alone achieved 5 percent.

当被要求基于完整基因组诊断患者时，Biomni 的准确率达到了大约 85%，而单独使用 Claude 4 Sonnet 时只有 5%。

3 The authors assessed the ability to produce a protocol for cloning DNA sequences，co-author Serena Zhang said in an interview. Across 10 tests，experts rated Biomni's protocol around 4.5 out of 5 — on par with those produced by human experts，higher than trainees，and much higher than Claude 4 Sonnet alone. A DNA synthesis lab was able to produce the sequence specified by one of the generated protocols.

合著者 Serena Zhang 在一次采访中表示，作者们评估了其生成克隆 DNA 序列方案的能力。在 10 次测试中，专家们给 Biomni 生成的方案打了大约 4.5 分（满分 5 分），这与人类专家制定的方案不相上下，高于受训人员，并且远高于单独使用 Claude 4 Sonnet。一家 DNA 合成实验室成功合成了其中一个方案所指定的序列。

Behind the news: While Biomni is designed to apply to biology broadly，most previous work on agents focused on narrower areas. For instance，just two days after the release of Biomni，a separate team at Stanford released CellVoyager，an agent that generates hypotheses about datasets of single-cell RNA sequences. Other examples include CRISPR-GPT，which designs gene-editing experiments，and SpatialAgent，which analyzes and hypothesizes about how cells interact within organisms.

新闻背后：虽然 Biomni 旨在广泛应用于生物学领域，但之前大多数关于 AI 智能体（AI Agent）的研究都集中在更狭窄的领域。例如，就在 Biomni 发布两天后，斯坦福大学的一个独立团队发布了 CellVoyager，这是一个能对单细胞 RNA 序列数据集生成假设的 AI 智能体。其他例子还包括 CRISPR-GPT，它能设计基因编辑实验；以及 SpatialAgent，它能分析并推断细胞在生物体内如何相互作用。

Why it matters: While agents conversant in biology typically focus on narrow specialties，Biomni's knowledge and skills span the entire domain，offering expert assistance to biologists across many specialties. Its reasoning capabilities can improve by substituting more capable LLMs as they become available，and its library of resources can be updated to keep up with changes in the field and extend its knowledge to new areas.

重要意义：尽管生物学领域的 AI 智能体（AI Agent）通常专注于狭窄的专业领域，Biomni 的知识和技能却能涵盖整个生物学领域，为多个专业领域的生物学家提供专业帮助。随着更强大大语言模型（LLM）的出现，Biomni 的推理能力也能通过替换这些模型而得到提升，其资源库也能不断更新，以适应领域的变化并将知识扩展到新的领域。

We're thinking: Like biology，many sciences are so deep and broad that most scientists have deep expertise only within their areas of specialty. Yet agents can pull together resources from disparate areas to reach novel conclusions. In this way，Biomni demonstrates the potential of AI to augment human expertise in meaningful ways.

我们认为，正如生物学一样，许多科学领域都博大精深，大多数科学家仅在其专业领域内拥有深厚的专业知识。然而，AI 智能体（AI Agent）能够整合来自不同领域的资源，从而得出新颖的结论。通过这种方式，Biomni 展示了人工智能以有意义的方式提升人类专业知识的巨大潜力。

#### CEOs Look to AI to Replace Workers

CEO 们期待 AI 取代工人

Leaders at some of the biggest U.S. corporations say they're preparing for AI to eliminate many jobs within their organizations.

美国一些大型企业的领导者表示，他们正准备让 AI 取代其组织内的许多工作岗位。

What's new: Amazon CEO Andy Jassy wrote in a memo to employees that generative AI and AI agents within the next few years would enable the company to reduce its corporate workforce.（Disclosure：Andrew Ng is a member of Amazon's board of directors.）Similarly，the CEOs of Bank of America，IBM，Shopify，and Williams-Sonoma have said they are embracing AI and expect to hire fewer workers as a result. Worldwide，around 40 percent of employers expect to downsize their workforce，largely due to the rise of AI，according to a survey by the World Economic Forum.

最新消息： Amazon 首席执行官 Andy Jassy 在给员工的备忘录中写道，生成式 AI（Generative AI）和 AI 智能体（AI Agent）将在未来几年内帮助公司减少企业员工数量。（披露： Andrew Ng 是 Amazon 董事会成员。） 类似地，美国银行、IBM、Shopify 和 Williams-Sonoma 的首席执行官们表示，他们正在积极采用 AI 技术，并预计将因此减少招聘员工。根据世界经济论坛的一项调查，全球约有 40% 的雇主预计将裁员，这很大程度上是由于 AI 的崛起。

How it works: Many business leaders skirt the topic of job losses when they describe the impact of AI on their companies，but these executives put the technology front and center in their plans to downsize.

工作原理：许多商业领袖在谈论人工智能对公司影响时，往往避而不谈裁员问题，但这些高管却将这项技术放在了裁员计划的核心位置。

1 Amazon，which employs roughly 1.5 million people，is investing in AI「quite expansively,」Jassy's memo notes.「We will need fewer people doing some of the jobs that are being done today，and more people doing other types of jobs. It's hard to know exactly where this nets out over time，but in the next few years，we expect that this will reduce our total corporate workforce,」he wrote.

Jassy 的备忘录指出，目前雇佣了约 150 万名员工的 Amazon，正在「相当广泛地」投资于人工智能（AI）。他写道：「我们将需要更少的人从事目前正在进行的一些工作，而更多的人从事其他类型的工作。很难确切知道随着时间的推移，这种变化最终会带来怎样的结果，但在未来几年，我们预计这将减少我们企业的总员工数量。」

2 Bank of America CEO Brian Moynihan told Bloomberg that widespread use of AI in banking would lead to a smaller workforce industry-wide.

美国银行 CEO Brian Moynihan 告诉彭博社，AI 在银行业的广泛应用将导致整个行业的人员规模缩小。

3 At IBM，AI agents have replaced hundreds of workers in the human resources department，CEO Arvind Krisna told The Wall Street Journal. Nonetheless，total employment has gone up at the company，he said.

IBM 首席执行官 Arvind Krisna 告诉《华尔街日报》，在该公司，AI 智能体（AI agents）已经取代了人力资源部门的数百名员工。但他同时表示，尽管如此，公司的总就业人数反而有所增加。

4 Shopify CEO Tobias Lütke in April instructed employees，before they request new hires，to explain why AI isn't sufficient to help them meet their goals. While this policy doesn't inevitably lead to fewer jobs，it exerts pressure in that direction.

Shopify 首席执行官 Tobias Lütke 在四月指示员工，在申请新员工之前，必须解释为什么 AI（Artificial Intelligence）不足以帮助他们实现目标。虽然这项政策不一定会直接导致工作岗位减少，但无疑会朝这个方向施加压力。

5 Williams-Sonoma CEO Laura Alber told investors on an earnings call that the retailer planned to use AI to avoid adding new employees. This year，the company will「focus on using AI to offset headcount growth,」she said.

Williams-Sonoma 首席执行官 Laura Alber 在一次财报电话会议上向投资者透露，该公司计划利用人工智能（AI）来避免增加新员工。她表示，今年公司将「专注于利用人工智能来抵消员工数量的增长」。

Yes，but: Several studies in recent years have shown that AI is likely to increase，not reduce，the number of jobs.

然而，事实是：最近几年的多项研究表明，人工智能（AI）非但没有减少，反而可能增加了就业岗位。

1 Researchers at European Central Bank found that employment in occupations affected by AI has risen over nearly a decade. A job's exposure to AI was associated with greater employment in some cases，and it had little effect on wages.

欧洲中央银行的研究人员发现，在近十年的时间里，受人工智能影响的职业就业率有所上升。在某些情况下，某个职业与人工智能的关联度越高，就业率就越高，并且对工资的影响微乎其微。

2 The U.S. government determined that employment grew in 9 out of 11 occupations that may be subject to automation.

美国政府发现，在 11 个可能受到自动化影响的职业中，有 9 个职业的就业实现了增长。

3 The accounting firm PricewaterhouseCoopers analyzed nearly 1 billion job ads internationally and found that job availability grew 38 percent in roles that were more exposed to AI.（This growth rate was lower than that of less-exposed occupations.)

会计师事务所普华永道分析了全球近 10 亿份招聘广告，发现那些受 AI 影响较大的职位，其就业机会增长了 38%。不过，这个增长速度低于那些受 AI 影响较小的职业。

Why it matters: Technological advances typically create more jobs than they destroy; an estimated 60 percent of U.S. jobs in 2018 did not exist in 1940. An explosion of machine learning engineers，AI application engineers，and data engineers is highly likely! In the short term，though，AI is poised to impinge on a wide variety of roles including many that once were considered immune to automation：knowledge workers，creative people，and so on. Executives have a responsibility to prepare their companies for a coming wave of AI-driven applications，and many expect to hire fewer employees.

重要性：技术进步通常会创造比它消灭的更多的就业机会；据估计，2018 年美国约有 60% 的工作在 1940 年时根本不存在。因此，机器学习工程师、AI 应用工程师和数据工程师等岗位的爆发式增长极有可能发生！然而，在短期内，AI （人工智能）可能会影响到多种岗位，包括许多曾被认为不会受到自动化影响的职业，比如知识工作者、创意人员等。高管们有责任为他们的公司即将迎来的一波 AI 驱动的应用程序浪潮做好准备，而许多人预计这将意味着减少员工招聘。

We're thinking: When executives speak，it's hard to differentiate those who are sincerely trying to navigate change from those whose primary aim is to reassure shareholders，drum up publicity，attract talent，or what have you. Regardless，professionals of all kinds who embrace AI will be much more productive and significantly outperform those who don't. Jassy said it well in his message to Amazon employees:「As we go through this transformation together，be curious about AI，educate yourself，attend workshops and take trainings，use and experiment with AI whenever you can，participate in your team's brainstorms to figure out how to invent for our customers more quickly and expansively，and how to get more done with scrappier teams.」

我们不禁会思考：当高管们发表言论时，我们很难分辨出，究竟哪些人是真心实意地在引领变革，而哪些人则主要为了安抚股东、吸引眼球、招揽人才等等。但无论目的如何，有一点是肯定的：那些积极拥抱人工智能（AI）的专业人士，生产力将大大提升，并显著超越那些拒绝 AI 的人。正如 Jassy 在给 Amazon 员工的寄语中所说：「当我们共同经历这场转型时，请大家对 AI 保持好奇心，主动学习，积极参与研讨会和培训，尽可能地使用和试验 AI。同时，也要积极参与团队的头脑风暴，集思广益，探索如何更快、更广泛地为客户创造价值，以及如何以更精简的团队完成更多任务。」

#### Low Precision，High Performance

低精度，高性能

Reducing the number of bits used to represent each parameter in a neural network from，say，16 bits to 8 bits shrinks the network's size and boosts its speed. Researchers took this approach to an extreme：They built a competitive large language model whose weights are limited to three values.

大模型也能又小又快减少神经网络中每个参数的比特数（例如从 16 比特降到 8 比特），能缩小网络规模并提升运行速度。研究人员将这种方法推向了极致：他们构建了一个具有竞争力的大语言模型，其权重被限制为仅有三个值。

What's new: Shuming Ma，Hongyu Wang，and colleagues at Microsoft，University of Chinese Academy of Sciences，and Tsinghua University updated their earlier BitNet b1.58，in which most weight values are limited to -1，0，or +1，competing with the top full-precision models up to 2 billion parameters. Weights are free to download for noncommercial and commercial uses according to an MIT license.

最新进展：微软（Microsoft）、中国科学院大学和清华大学的 Shuming Ma、Hongyu Wang 及同事们更新了他们早期的 BitNet b1.58 模型。这款模型的大部分权重值被限制在 -1、0 或 +1，却能与参数量高达 20 亿的顶级全精度模型相媲美。根据 MIT 许可证，该模型的权重可免费下载，用于非商业和商业用途。

[[2504.12285] BitNet b1.58 2B4T Technical Report](https://arxiv.org/abs/2504.12285?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--vRYboX-Vrshi6EFG2BpZiySCxl_TYmVcIYV00dB6Bpli3B5fHLbQ38R3a93hS_fZr8Knd)

[microsoft/BitNet at paper](https://github.com/microsoft/BitNet/tree/paper?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--vRYboX-Vrshi6EFG2BpZiySCxl_TYmVcIYV00dB6Bpli3B5fHLbQ38R3a93hS_fZr8Knd)

Key insight: Linear layers have a big impact on a transformer's overall speed. They make up large parts of attention layers and fully connected layers，so they account for most computations. The authors' 2023 work on BitNet showed that using 1-bit weights — whose values are limited to -1 and +1 — makes multiplications very fast（because multiplying by -1 simply flips the sign and multiplying by +1 changes nothing），but performance suffers. They improved on the idea the following year with BitNet b1.58，which allowed weights to be -1，0，or +1.（Implemented perfectly，this approach allocates approximately 1.58 bits per parameter，since the number of bits needed to represent 3 values is log₂(3)=1.58.）In this case，multiplying by -1 or +1 still just flips or keeps the sign，and multiplying by 0 zeroes out the value. This ternary setup retains the original BitNet's low memory requirements，fast training，and fast inference. With careful attention to hyperparameters，it also improves performance.

关键洞察：线性层对 Transformer 的整体速度有很大影响。它们是注意力层和全连接层的主要组成部分，因此贡献了大部分计算量。该研究团队在 2023 年关于 BitNet 的工作表明，使用 1 比特权重（这些权重的值仅限于 -1 和 +1）可以使乘法运算非常快（因为乘以 -1 只是翻转符号，乘以 +1 则保持不变），但模型性能会因此受到影响。第二年，他们通过 BitNet b1.58 改进了这一设计理念，允许权重取值 -1、0 或 +1。（在理想实现下，由于表示 3 个值需要 log₂(3)=1.58 比特，因此这种方法能为每个参数分配大约 1.58 比特。）在这种情况下，乘以 -1 或 +1 仍然只是翻转或保持符号，而乘以 0 则会将值归零。这种三元（Ternary）设置保留了原始 BitNet 低内存占用、快速训练和快速推理的优点。并且，通过仔细调整超参数，它还能进一步提升模型性能。

How it works: The authors pretrained the 2-billion parameter BitNet b1.58，which has an architecture similar to LLaMA，on a dataset of 4 trillion tokens that included web data plus synthetic math problems. To strengthen its reasoning abilities，they fine-tuned it on chat data, instruction-following data, and synthetic instruction-following data. Finally，they fine-tuned the model via DPO to better match human preferences.

工作原理：研究人员预训练了一个拥有 20 亿参数的 BitNet b1.58 模型，其架构与 LLaMA 相似。他们使用了包含网络数据和合成数学问题的 4 万亿个 Token 的数据集进行预训练。为了增强其推理能力，研究人员随后使用聊天数据、指令遵循数据和合成指令遵循数据对其进行了微调。最后，他们通过 DPO（Direct Preference Optimization）对模型进行了微调，使其能够更好地符合人类偏好。

1 During training，the authors used a quantized version of the model for forward passes and the non-quantized version for backward passes. Before each forward pass，they quantized the weights in linear layers to -1，0，or +1. They ran the model，quantizing layer outputs to 8 bits. During backpropagation，they updated the weights of the non-quantized version，copied them，and quantized them before the next forward pass.

在训练过程中，研究人员对模型的前向传播使用了量化后的权重，而在反向传播时则使用未量化的权重。在每次前向传播之前，他们会将线性层中的权重量化为 -1、0 或 +1 这三个值。接着，模型开始运行，并将各层的输出量化为 8 位。在反向传播阶段，他们会更新模型未量化版本的权重，然后将这些更新后的权重复制一份，并在下一次前向传播之前对其进行量化处理。

2 For ease of implementation，they ran attention，layer normalization，and other operations in 8-bit precision and stored the gradients and loss in 16 bits.

为了方便实现，他们让注意力（attention）、层归一化（layer normalization）和其他操作都在 8 比特精度下进行，并将梯度（gradients）和损失（loss）存储在 16 比特中。

3 They used a two-phase schedule for the learning rate：an initial high learning rate helped BitNet b1.58 make updates large enough to affect the 1.58-bit weights after quantization — since small changes often had no effect — followed by a sharp drop in the learning rate mid-training to refine all weights on higher-quality data.

他们为学习率（learning rate）设定了两阶段策略：首先采用较高的学习率，这有助于 BitNet b1.58 进行足够大的更新，从而在量化（quantization）后能有效调整 1.58 比特的权重 —— 因为微小的改变往往不起作用；随后，在训练中期学习率会急剧下降，目的是在更高质量的数据上对所有权重进行精细化调整。

4 Similarly，they structured weight decay，which encourages weights to have lower values，in two phases. During the early phase，when the data quality was lower and learning rate higher，they used a strong decay to prevent overfitting. During the second phase，with higher-quality data and a lower learning rate，they disabled weight decay. This let all weights adapt to the data without interference from weight decay.

类似地，他们将权重衰减（weight decay）分成了两个阶段。权重衰减是一种鼓励模型权重保持较小值的技术。在早期阶段，由于数据质量相对较低且学习率较高，他们采用了较强的权重衰减来有效防止过拟合。而在第二个阶段，随着数据质量的提升和学习率的降低，他们禁用了权重衰减。这样做的目的是让所有权重能够充分适应数据，不再受到权重衰减的影响。

Results: Across 16 popular benchmarks for language understanding，mathematical reasoning，and coding，BitNet b1.58 was faster and used less memory than competitors，including Alibaba's Qwen2.5-1.5B，Google's Gemma-3 1B，Hugging Face's SmolLM2 1.7B，Meta's Llama 3.2 1B，and ModelBest's MiniCPM 2B. It achieved better performance than all except Qwen2.5 1.5B.

结果：在 16 个流行的语言理解、数学推理和编码基准测试中，BitNet b1.58 比包括阿里巴巴的 Qwen2.5-1.5B、谷歌的 Gemma-3 1B、Hugging Face 的 SmolLM2 1.7B、Meta 的 Llama 3.2 1B 和 ModelBest 的 MiniCPM 2B 在内的竞争对手更快，并且使用的内存更少。除了 Qwen2.5 1.5B 之外，BitNet b1.58 的性能超越了所有其他模型。

1 Running on a laptop，BitNet generated 34.5 tokens per second on average，whereas Qwen2.5-1.5B generated 15.4 tokens per second on average.

在笔记本电脑上运行，BitNet 平均每秒生成 34.5 个 Token（Token），而 Qwen2.5-1.5B 平均每秒生成 15.4 个 Token。

2 BitNet's memory requirement was 0.4GB，while Qwen2.5-1.5B required 2.6 GB.

BitNet 的内存占用为 0.4GB，而 Qwen2.5-1.5B 则需要 2.6GB。

3 BitNet achieved average accuracy of 54.19 percent，while Qwen2.5-1.5B  achieved average accuracy of 55.23 percent. SmolLM2 1.7B was next-best（48.7 percent average accuracy).

BitNet 实现了 54.19% 的平均准确率，而 Qwen2.5-1.5B 实现了 55.23% 的平均准确率。SmolLM2 1.7B 位居第二（平均准确率 48.7%）。

4 BitNet also outperformed a 4-bit quantized version of Qwen2.5-1.5B (52.15 percent average accuracy).

BitNet 也超越了 Qwen2.5-1.5B 的 4 比特量化版本（平均准确率为 52.15%）。

Why it matters: Quantizing an LLM to a few bits is not as simple as applying the current best practices for full-precision models. It demands rethinking LLM training，down to hyperparameter details like learning rate and weight decay. Even these seemingly small changes can have a large impact on final performance. By delving into these nuances，the authors provide a guide for how to ensure good performance from low-precision models.

重要性：将大语言模型（LLM）量化到较低的比特数，并非像对待全精度模型那样，简单套用现有的最佳实践就能解决。这需要我们重新审视大语言模型训练的方方面面，甚至深入到学习率和权重衰减等超参数（Hyperparameter）的细节。即使是这些看似微小的调整，也可能对最终的性能产生巨大影响。通过深入探究这些细微之处，作者们为如何确保低精度模型的出色性能提供了宝贵的指导。

We're thinking: This work makes more than a bit of progress!

我们认为：这项工作取得了不小的进展！