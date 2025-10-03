## 20251001OpenAIs-Trillion-Dollar-Bet-Generating-Viruses

[OpenAI’s Trillion-Dollar Bet, Generating Viruses, Modeling Planet Earth, and more...](https://www.deeplearning.ai/the-batch/issue-321/)

Dear friends,

LandingAI's Agentic Document Extraction (ADE) turns PDF files into LLM-ready markdown text. I'm excited about this tool providing a powerful building block for developers to use in applications in financial services, healthcare, logistics, legal, insurance, and many other sectors.

LandingAI 的 Agentic Document Extraction（ADE）工具能将 PDF 文件转换成适用于大语言模型（Large Language Model）的 Markdown 文本。我很高兴看到这个工具为开发者提供了一个强大的「构建模块」，可以在金融服务、医疗保健、物流、法律、保险等诸多领域的应用中发挥作用。

Before LLMs, many documents sat on individuals' laptops or in businesses' cloud storage buckets unexamined, because we did not have software that could make sense of them. But now that LLMs can make sense of text, there's significant value in getting information out of the numerous PDF documents, forms, and slide decks we've stored for processing — if we are able to extract the information in them accurately. For example:

在大语言模型（LLMs）出现之前，许多文档都存储在个人笔记本电脑或企业的云存储桶中，无人问津，因为我们缺乏能够理解和处理这些文档的软件。但如今，随着大语言模型能够理解文本，从我们存储起来等待处理的大量 PDF 文档、表格和演示文稿中提取信息，就具有了巨大的价值 —— 前提是我们能够准确地抽取其中的信息。例如：

* Healthcare: Streamlining patient intake by accurately extracting data from complex medical forms

* Financial services: Accurately extracting data from complex financial statements such as a company's public filings, which might include financial tables with thousands of cells, for analysis

*  医疗保健：通过从复杂医疗表格中准确提取数据，简化患者登记流程。

*  金融服务：从复杂的财务报表（例如可能包含数千个单元格的财务表格的公司公开文件）中准确提取数据，用于分析。

* Logistics: Extracting data from shipment orders and custom forms to track or expedite shipping

* Legal: Enable automated contract review by accurately extracting key clauses from complex legal documents

*  物流：从发货订单和海关表格中提取数据，以便追踪或加速运输

*  法律：通过准确提取复杂法律文件中的关键条款，助力实现自动化合同审查

Accurate extraction of data is important in many valuable applications. However, achieving accuracy is not easy.

Further, even though LLMs hallucinate, our intuition is still that computers are good at math. Some of the most disconcerting mistakes I've seen a computer make have been when a system incorrectly extracted figures from a large table of numbers or complex form and output a confident-sounding but incorrect financial figure. Because our intuition tells us that computers are good at numbers (after all, computers are supposed to be good at computing!), I've seen users find silent failures in the form of incorrect numerical outputs particularly hard to catch.

在许多有价值的应用中，准确地提取数据至关重要。然而，要做到完全准确却并非易事。

此外，尽管大语言模型（LLM）会产生「幻觉」(hallucinate，即生成不准确或虚假信息），但我们总觉得计算机应该擅长数学。我见过计算机犯的一些最令人不安的错误，就是当某个系统从一大堆数字表格或复杂的表单中错误地提取了数据，并输出一个听起来言之凿凿但实际上错误的财务数字。由于我们的直觉告诉我们计算机在数字方面很强（毕竟，计算机就是用来计算的！），因此当出现这类错误的数字输出时，用户往往很难察觉到这种「静默失败」(silent failures）。

How can we accurately extract information from large PDF files? Humans don't just glance at a document and reach a conclusion on that basis. Instead, they iteratively examine different parts of the document to pull out information piece by piece. An agentic workflow can do the same.

我们如何能准确地从大型 PDF 文件中提取信息呢？人类可不会仅仅看一眼文档就得出结论。相反，他们会迭代地检查文档的不同部分，一点点地提取出所需的信息。一个 AI 智能体（AI Agent）工作流也能做到同样的事情。

ADE iteratively decomposes complex documents into smaller sections for careful examination. It uses a new custom model we call the Document Pre-trained Transformer (DPT); more details are in this video. For example, given a complex document, it might extract a table and then further extract the table structure, identifying rows, columns, merged cells, and so on. This breaks down complex documents into smaller and easier subproblems for processing, resulting in much more accurate results.

ADE 会逐步将复杂的文档分解为更小的部分，以便仔细审查。它使用我们称之为文档预训练 Transformer（Document Pre-trained Transformer，DPT）的新型自定义模型；更多细节请观看此视频。举例来说，对于一个复杂的文档，ADE 可能会先提取出一个表格，然后进一步提取出表格的结构，识别出行、列、合并单元格等。这种方法将复杂文档分解为更小、更容易处理的子问题，从而大幅提升了结果的准确性。

Today, a lot of dark data — data that has been collected but is not used — is locked up in documents. ADE, which you can call using just ~3 simple lines of code, accurately extracts this information for analysis or processing by AI. You can learn more about it here. I hope many developers will think of cool applications to build with this.

今天，大量暗数据（dark data)—— 这些数据已被收集但尚未被利用 —— 被封锁在文档中，难以被有效使用。而 ADE，您只需通过大约 3 行简单的代码就能调用它，它能准确地从这些文档中提取信息，以便 AI 进行分析或处理。您可以在这里了解更多关于 ADE 的信息。我希望许多开发者能以此为基础，构建出各种令人惊叹的创新应用。

Keep building!

Andrew

持续建设！

安德鲁

### News

#### OpenAI On the Road to Trillion-Dollar Spending

### 新闻

#### OpenAI 将迈向万亿美元支出

A flurry of announcements brought into sharper focus OpenAI's plans to build what may amount to trillions of dollars of global computing capacity.

What's new: OpenAI, Oracle, and SoftBank, the primary partners in the massive data-center buildout called Stargate, announced 5 new sites in the United States that entail $400 billion in spending in addition to its prior commitments. In addition, OpenAI introduced Stargate UK, a partnership with Nvidia and the Norwegian data-center builder Nscale that will build AI infrastructure in England. All told, OpenAI's current plans will cost $1 trillion, The Wall Street Journal reported.

一系列密集的公告，让 OpenAI 旨在建立价值可能高达数万亿美元的全球计算能力的计划，变得前所未有地清晰。

最新消息：作为名为 Stargate 的大规模数据中心建设的主要合作伙伴，OpenAI、Oracle 和 SoftBank 宣布，除了现有承诺之外，还将在美国新增 5 个站点，预计投入 4000 亿美元。此外，OpenAI 还宣布启动了 Stargate UK 项目，该项目是与 Nvidia 和挪威数据中心建造商 Nscale 合作的，将在英格兰建设人工智能（AI）基础设施。据《华尔街日报》报道，OpenAI 目前的这些规划总计将耗资 1 万亿美元。

How it works: OpenAI forecasts demand for data centers in terms of electricity they will consume. Each 1-gigawatt increment of capacity (roughly enough to light 1 million LED bulbs) costs around $50 billion to build. The company's current plans amount to 20 gigawatts worldwide, and it predicts demand as high as 100 gigawatts, according to one executive. To satisfy that level of demand would bring the total outlay to $5 trillion (roughly the gross domestic product of Germany).

运作方式：OpenAI 根据数据中心将消耗的电量来预测其需求。每 1 吉瓦（gigawatt）的新增容量（大致相当于点亮 100 万个 LED 灯泡所需的电力）建设成本约为 500 亿美元。据一位高管透露，该公司目前的全球部署计划总计 20 吉瓦，但他们预测未来需求可能高达 100 吉瓦。为了满足如此庞大的需求，总支出将达到 5 万亿美元 —— 这大致相当于德国的国内生产总值。

* OpenAI will build 1.5 gigawatts of new capacity in Ohio (piggybacking on a previous SoftBank project) and Texas over the coming 18 months. This capacity adds to 5.5 gigawatts in New Mexico, a different site in Texas, and an unnamed location in the Midwest. These newly announced facilities complement a 1.2-gigawatt set of eight data centers  in Abilene, Texas, two of which are up and running. Oracle will oversee construction, and Oracle and Softbank will provide financing.

OpenAI 计划在未来 18 个月内在俄亥俄州（将依托 SoftBank 此前的一个项目）和德克萨斯州新增 1.5 吉瓦（gigawatts）的电力容量。这部分新增容量将与此前在新墨西哥州、德克萨斯州另一处地点以及美国中西部一处未公布地点的 5.5 吉瓦容量相叠加。此外，这些新宣布的设施也将与德克萨斯州阿比林市的八个数据中心（data centers）形成互补，这八个数据中心共计 1.2 吉瓦容量，其中已有两个数据中心投入运营。Oracle 将负责监督这些项目的建设，并由 Oracle 和 Softbank 提供融资。

* The UK project calls for multiple sites, starting with Cobalt Park near Newcastle, that will enable OpenAI to supply computing power for finance, national security, and other applications that need to be processed domestically. Nvidia will supply GPUs that may amount to 8,000 early next year and as many as 31,000 afterward.

* 英国的一个项目计划建设多个站点，首个站点将设在纽卡斯尔附近的 Cobalt Park。这些站点将使 OpenAI 能够为金融、国家安全以及其他需要在英国国内进行处理的应用提供强大的计算能力。Nvidia 将为该项目提供图形处理器（GPU），预计在明年年初，GPU 数量可能达到 8,000 个，之后总量有望增至 31,000 个。

* Separate from the Stargate announcements, Nvidia pledged to invest $100 billion in OpenAI, following a recent $40 billion infusion from SoftBank, Microsoft, and others as well as an earlier $13 billion from Microsoft. Nvidia provided the first $10 billion at a valuation of $500 billion, raising its stake in OpenAI by roughly 2 percent after an undisclosed investment last year. The outlay is likely to return to Nvidia directly in the form of sales or leases of chips, The Information reported

*  除了 Stargate 的相关声明之外，Nvidia 承诺向 OpenAI 投资 1000 亿美元。在此之前，SoftBank、Microsoft 和其他公司近期已向 OpenAI 注资 400 亿美元，Microsoft 早些时候也投入了 130 亿美元。Nvidia 以 5000 亿美元的估值先行投入了 100 亿美元，这使其在 OpenAI 的持股比例增加了约 2%（此前 Nvidia 去年曾有过一笔未披露的投资）。据 The Information 报道，这笔投资很可能最终会以芯片销售或租赁的形式直接流回 Nvidia。

Behind the news: Stargate, a partnership between OpenAI, Oracle, and SoftBank to build 20 data centers over four years at a cost of $500 billion, began in January. That plan is proceeding ahead of schedule and has expanded considerably.

新闻背后传来了最新消息：由 OpenAI、Oracle 和 SoftBank 合作推出的一个名为 Stargate 的项目，计划在四年内投入 5000 亿美元，建成 20 个数据中心，该项目已于今年一月正式启动。目前，这项计划不仅进展超前，规模也已大幅扩大。

* With the latest announcements, the initial commitment is more than 80 percent underway.

* Stargate includes further 1-gigawatt initiatives in India and the United Arab Emirates, with more countries under consideration.

* 随着最新公告的发布，最初设定的目标已经完成了 80% 以上。

* Stargate 计划还包括在印度和阿拉伯联合酋长国开展的另外 1 吉瓦（gigawatt）项目，并且有更多国家正在考虑加入。
</step3_re_translation>

* OpenAI's arrangement with Oracle includes a commitment to pay the latter $30 billion annually for computing services.

Yes, but: Some analysts worry that giant infrastructure commitments by big AI companies could jeopardize their financial health if demand for AI doesn't keep pace. "Someone is going to lose a phenomenal amount of money," OpenAI CEO Sam Altman told The Verge, adding that winners will gain even more.

* 根据协议，OpenAI 承诺每年向 Oracle 支付 300 亿美元，用于获取其计算服务。

然而，一些分析师担心，如果人工智能（AI）的需求增长未能跟上，大型 AI 公司在基础设施方面投入的巨额资金可能会危及它们的财务健康。OpenAI 首席执行官 Sam Altman 在接受 The Verge 采访时表示，「总会有人损失一大笔钱」，但他同时补充说，赢家将获得的回报会更多。

Why it matters: Big AI's capital spending continues to rise. In addition to Stargate, Alphabet, Amazon, Meta, and Microsoft together plan to spend more than $325 billion this year on data centers, with much more to come. This outsized effort brings with it outsized risks: Companies are betting their balance sheets, investors are putting money on the line, governments are hoping that data centers will supercharge their economies, energy providers are scrambling to provide sufficient electricity, and communities are balancing potential prosperity versus environmental hazard. The optimistic view sees AI's value rising, costs falling, social benefits spreading, and energy use declining as AI models produce higher-quality output with greater efficiency.

这件事为何重要：大型 AI（人工智能）企业的资本支出仍在持续攀升。除了 Stargate 项目，Alphabet、Amazon、Meta 和 Microsoft 等公司今年总计计划在数据中心上投入超过 3250 亿美元，未来的投入还将更多。这种巨大的投入也伴随着巨大的风险：企业正拿自身的财力冒险，投资者则将资金投入其中，各国政府希望数据中心能极大促进经济发展，能源供应商正想方设法提供充足电力，而各地社区则在潜在的繁荣和可能的环境危害之间寻求平衡。乐观的看法是，随着 AI 模型能以更高效率产出更高质量的结果，AI 的价值将不断提升，成本会逐渐降低，社会效益会更广泛地传播，同时能源消耗也将随之减少。

We're thinking: $5 trillion spent on AI infrastructure is more than 10 times OpenAI's latest valuation. But the company's valuation has increased by more than 20 times since it launched ChatGPT in 2022. So far, its bets are paying off.

我们设想：在人工智能基础设施上的 5 万亿美元投入，已超过 OpenAI 最新估值的十倍。然而，自 2022 年 ChatGPT 发布以来，OpenAI 的公司估值已暴涨超过 20 倍。由此可见，到目前为止，它的投入正取得丰厚回报。

#### AI Generates Viral Genomes

Researchers used AI models to create novel viruses from scratch.

#### AI 生成病毒基因组研究人员利用 AI 模型，从零开始创造出全新的病毒。

What's new: Samuel King and colleagues at the nonprofit biotech lab Arc Institute, Stanford University, and Memorial Sloan Kettering Cancer Center used model architectures related to transformers, trained on DNA sequences rather than text, to synthesize viruses that fight a common bacterial infection.

最新进展：Samuel King 和他在非营利性生物技术实验室 Arc Institute、斯坦福大学以及 Memorial Sloan Kettering 癌症中心的同事们，利用一种在 DNA 序列而非文本上训练的、与 Transformer 架构相关的模型，成功合成了能够对抗常见细菌感染的病毒。

Key insight: The class of models known as genomic language models can produce DNA sequences by generating chains of nucleotides, the building blocks of DNA. Typically such models produce sequences up to the length of a single gene, of which many are required to make a genome. But fine-tuning such models on sequences associated with a family of viruses can enable them to produce longer sequences within that family. At inference, feeding the fine-tuned model the initial part of the genome of a virus from the fine-tuned family can prompt the model to generate an entire novel genome.

关键洞察：一类被称为基因组语言模型（Genomic Language Model）的模型，能够通过生成核苷酸链来创建 DNA 序列，而核苷酸正是 DNA 的基本组成单元。通常，这类模型产生的序列长度相当于一个基因，但我们知道一个完整的基因组需要许多基因共同构成。不过，如果对这些模型进行微调，使其学习特定病毒家族的序列特征，它们就能在这个家族范围内生成更长的序列。在模型推理时，只要给经过微调的模型输入目标病毒家族中某个病毒基因组的起始部分，模型就能以此为基础，生成一个全新的完整基因组。

How it works: The authors fine-tuned existing genome language models on the genomes of 14,500 viruses in the Microviridae family of bacteriophages, viruses that kill specific bacteria. Using the fine-tuned models, they generated potential viral genomes similar to Microviridae, identified the most promising ones, and synthesized them.

工作原理：研究人员在噬菌体 Microviridae 家族中 14,500 种病毒的基因组上，对现有的基因组语言模型进行了微调。这些病毒属于噬菌体，是一种能杀死特定细菌的病毒。接着，他们利用这些经过微调的模型，生成了与 Microviridae 家族相似的潜在病毒基因组，并从中识别出最有前景的基因组，最终将其合成。

* The authors started with Evo 1 (a 7 billion-parameter StripedHyena architecture pretrained on 2.7 million bacterial and viral genomes) and Evo 2 (a 7 billion-parameter StripedHyena 2 architecture pretrained on 8.8 trillion tokens from viral, bacterial, plant, and animal genomes). The StripedHyena architectures blend transformer-like self-attention layers that encode long-range dependencies with convolution-like  blocks, enabling them to read and generate long DNA sequences efficiently.

* 作者们首先采用了 Evo 1 （一种拥有 70 亿个参数的 StripedHyena 架构，它在 270 万个细菌和病毒基因组上进行了预训练），以及 Evo 2 （一种拥有 70 亿个参数的 StripedHyena 2 架构，它在 8.8 万亿个来自病毒、细菌、植物和动物基因组的 Token 上进行了预训练）。这些 StripedHyena 架构融合了类似 Transformer（Transformer）的自注意力层（这种层能够编码长程依赖关系）和卷积状模块，这使得它们能够高效地读取和生成长 DNA 序列。

* The authors generated 11,000 candidate genomes by prompting the models with the first 11 nucleotides in the genome of the virus ΦX174, a relatively simple member of the Microviridae family that kills the bacterium E. coli C by making it burst.

* 作者们给模型提供提示，内容是 ΦX174 病毒基因组的前 11 个核苷酸，由此生成了 11,000 个候选基因组。ΦX174 病毒属于小病毒科（Microviridae family）中一个相对简单的成员，它通过使大肠杆菌 C（E. coli C）破裂来将其杀死。

* They used existing tools for DNA sequence interpretation to filter the candidates, keeping those that were (i) likely to produce novel proteins, (ii) likely to produce proteins that would bind to E. Coli C, (iii) around the same length as ΦX174's genome, and (iv) made up of the most common nucleotides. This left 302 genomes.

* 研究人员利用现有的 DNA 序列（DNA sequence）解释工具来筛选候选序列，最终保留了那些满足以下条件的序列：（i）有望产生新颖蛋白质的，（ii）预计能产生与大肠杆菌 C（E. Coli C）结合的蛋白质的，（iii）长度与 ΦX174 基因组大致相当的，以及（iv）由最常见核苷酸（nucleotide）组成的。经过这样的筛选，最终剩下 302 个基因组。

* They successfully synthesized 285 of the 302 generated candidates.

Results: The authors tested a cocktail of 16 synthetic viruses on 3 bacterial strains that are resistant to ΦX174. Initially, the cocktail failed to kill the bacteria within three hours. However, when they moved the viruses to new cultures of the same bacterial strain to give them opportunities to recombine and mutate, the bacteria succumbed.

*  在 302 个生成的候选物中，他们成功合成了 285 个。

结果：研究人员测试了一种由 16 种合成病毒组成的混合物，用于对抗 3 种对 ΦX174 具有抗性的细菌菌株。起初，这种混合物在三小时内未能杀死细菌。然而，当他们将这些病毒转移到相同细菌菌株的新培养皿中，让病毒有机会进行重组和突变后，细菌最终被清除了。

* In three side-by-side contests, the synthetic virus called Evo-Φ69 replicated in host cells more than ΦX174 and other synthetic viruses. Six hours after infecting its host, the population of Evo-Φ69 had increased between 16 times and 65 times its initial level, while the population of ΦX174 had increased between 1.3 times and 4.0 times.

*  在三场对比实验中，名为 Evo-Φ69 的合成病毒在宿主细胞内的复制能力，比 ΦX174 和其他合成病毒更强。感染宿主六小时后，Evo-Φ69 的数量增长了初始水平的 16 到 65 倍，而 ΦX174 的数量则只增长了 1.3 到 4.0 倍。

* In a test that tracked cloudiness of the liquid bacterial culture, a proxy for the density of the bacterial population, Evo-Φ2483 reduced the culture's cloudiness to 0.07 optical density in 135 minutes, while ΦX174 achieved 0.22 optical density in 180 minutes.

*  在一项实验中，研究人员监测了液体细菌培养物的混浊度，这可以作为衡量细菌数量（即细菌种群密度）的指标。结果显示，Evo-Φ2483 能在 135 分钟内将培养物的混浊度降至 0.07 光密度（optical density），而 ΦX174 则在 180 分钟内达到了 0.22 的光密度。

* Many of the synthetic viruses qualified as new species, meaning their genomes were no more than 95 percent identical to those of the nearest naturally occurring viruses.

许多合成病毒被认定为新物种，这意味着它们的基因组与最近的天然病毒的基因组相似度不超过 95%。

Behind the news: Genome engineering typically relies on selective breeding, introducing random mutations, or making specific changes based on known biology, all of which modify existing genomes instead of designing new ones. These approaches struggle to change features like genome lengths and the speed at which bacteriophages kill bacterial cells.

新闻背景： 基因组工程（Genome engineering）通常依赖于选择性育种（selective breeding）、引入随机突变（random mutations），或基于已知的生物学原理进行特定修改。所有这些方法都是在现有基因组的基础上进行修改，而非从头设计新的基因组。然而，这些传统方法难以改变基因组的长度，也难以改变噬菌体（bacteriophages）杀死细菌细胞的速度等特征。

Why it matters: Bacteriophage therapy is a potential alternative to antibiotics. However, bacteria can evolve resistance bacteriophages, just as they develop resistance to antibiotics. In this work, AI generated genomes for viable, diverse, novel synthetic bacteriophages that defeated resistant bacteria. This approach could give doctors a fresh approach to fighting bacterial infections.

重要性：噬菌体疗法（bacteriophage therapy）是抗生素（antibiotics）的一种潜在替代方案。然而，细菌会对噬菌体产生耐药性，就像它们对抗生素产生耐药性一样。在这项研究中，人工智能（AI）生成了基因组，合成了可行、多样且新颖的噬菌体，这些噬菌体成功击败了耐药细菌。这项新方法有望为医生提供一种对抗细菌感染的全新途径。

We're thinking: Making new viruses from scratch is cause for both excitement and concern. On one hand, the implications for medicine and other fields are enormous. On the other, although the authors took care to produce viruses that can't infect humans, malicious actors may not. Research into responding to biological threats is as critical as research that enables us to create such threats.

我们不禁思考：人工合成（making new viruses from scratch）新病毒这项技术，真是让人喜忧参半。一方面，它在医学及其他领域有着极其深远的意义；另一方面，尽管研究人员在制造这些病毒时，小心翼翼地确保它们不会感染人类，但恶意行为者（malicious actors）可不一定会这样做。因此，研究如何应对生物威胁，与研究如何创造这些威胁本身一样重要。

#### Generating Music, Paying Musicians

A Swedish organization that collects royalties on behalf of songwriters and record companies has formed a technology-legal-business ecosystem designed to allow AI developers to use music legally while compensating publishers of recordings and compositions.

#### 创作音乐，保障音乐人收益一家代表词曲作者和唱片公司收取版税的瑞典机构，构建了一个技术、法律和商业相结合的生态系统。该系统旨在让 AI（人工智能）开发者能够合法地使用音乐，同时也能确保录音作品和音乐创作的出版商获得应有的报酬。

What's new: STIM, which collects royalties on behalf of over 100,000 composers and recording artists, devised a license for use of musical works to train AI models. Sureel, a Swedish startup, provides technology that calculates the influence of a given training example on a model's output. The music-generation startup Songfox is the first licensee.

最新消息是：STIM 代表超过 10 万名作曲家和录音艺术家收取版税，他们制定了一项许可协议，允许使用音乐作品来训练 AI 模型。瑞典初创公司 Sureel 提供了一项技术，可以计算某个训练示例对模型输出的影响程度。音乐生成领域的初创公司 Songfox 是第一个获得该许可的企业。

How it works: STIM considers its deal with Songfox a pilot project that will shape future licensing arrangements. Members of the organization can license their music if they (i) opt in to allowing AI developers to use it and (ii) distribute it via STIM's music-by-subscription subsidiary Cora Music.

工作原理： STIM 将其与 Songfox 达成的协议视为一个试点项目，该项目将为未来的许可合作奠定基础。该组织的成员如果满足以下两个条件，便可以对其音乐进行许可：(i）选择同意 AI（人工智能）开发者使用其音乐，并且（ii）通过 STIM 旗下的订阅音乐服务子公司 Cora Music 来发行这些音乐。

* STIM members must register their works with Sureel. Registration forbids AI developers from training models on those works by default. To license registered works, publishers must opt in and developers must agree to the terms.

*  STIM 的成员必须向 Sureel 注册他们的作品。完成注册后，默认情况下，AI 开发者就不得使用这些作品来训练模型。如果发行商希望授权他人使用已注册的作品，他们必须选择加入许可程序，而开发者则必须同意相关的条款。

* The license grants licensees — typically AI companies that seek to train a music generator on licensed works — the right to copy recordings and their underlying compositions for the purpose of training one version of a model. Further licenses are required for further versions. Licensees can distribute generated music via subscription services, but they must obtain separate licenses for television, radio, advertising, or films.

*  这项许可赋予被许可方（通常是那些希望利用授权作品训练音乐生成器（music generator）的 AI 公司（AI companies)）复制录音及其底层编曲的权利，但仅限于训练一个模型版本。如果需要开发后续版本，则需要另行获得许可。被许可方可以通过订阅服务（subscription services）分发生成的音乐，但若用于电视、广播、广告或电影，则必须另行获得许可。

* Sureel uses proprietary technology to determine the influence of a given work on a given generated output. The technology, which must be integrated with a model during training, learns "static attribution vectors" that help determine a percentage of influence on the model's output of any given training example, according to a patent.

* Sureel 采用一项专有技术，旨在确定某个作品对给定生成结果的影响力。这项技术需要在模型训练阶段与模型进行整合，它能学习「静态归因向量（static attribution vectors）」。根据一项专利披露，这些向量有助于计算出任何一个训练样本对模型最终输出影响的百分比。

* When an AI developer uses licensed works, the rights holders will divide a licensing fee based on the number of their works used, the size of the AI developer's business, and other factors. They will also receive unspecified shares of revenue from the uses of the AI model and the generated music. (The license is new enough that no concrete examples of such payments are available.)

* 当 AI 开发者使用受许可保护的作品时，作品的权利人将根据其作品被使用的数量、AI 开发者业务的规模以及其他相关因素，共同分配许可费用。此外，他们还将从 AI 模型的使用以及由此生成的音乐中，获得未具体说明比例的收入分成。(由于这种许可模式刚刚兴起，目前还没有此类付款的具体案例可供参考。)

Yes, but: To take advantage of the license, AI developers must integrate Sureel's attribution technology into their model training process. Consequently, the STIM license is not useful for artists that aim to collect revenue from music-generation companies such as Suno and Udio, which trained their models without Sureel's involvement.

是的，不过：想受益于这项许可，AI 开发者必须将 Sureel 的归属技术（attribution technology）集成到他们的模型训练流程中。因此，STIM 许可对于那些希望从 Suno 和 Udio 等音乐生成公司获取收入的艺术家来说用处不大，因为这些公司在 Sureel 未参与的情况下就训练了它们的模型。

Behind the news: Owners of copyrights to creative works have sued AI companies for training models on their works without permission, but the likely outcomes of such lawsuits are uncertain.

新闻背后：拥有创作作品版权的个人或机构，已经起诉了多家 AI 公司，指控它们在未经许可的情况下，利用这些作品来训练模型。不过，这类诉讼的最终结果目前还难以预料。

* Sony Music, Universal Music Group, and Warner Music — the world's three largest music companies — are pursuing a lawsuit against Suno and Udio, makers of web-based music generators, for alleged copyright violations. Similarly, the German music-rights organization GEMA is suing Suno.

*  全球三大音乐巨头 —— 索尼音乐、环球音乐集团和华纳音乐 —— 正对网络音乐生成器（web-based music generators）的开发商 Suno 和 Udio 提起诉讼，指控其涉嫌侵犯版权。无独有偶，德国音乐版权组织 GEMA 也正在起诉 Suno。

* Laws in the United States do not address whether or not the training an AI model on a copyrighted work requires the copyright owner's permission. This leaves the question to be decided by courts or further action by lawmakers.

*  美国法律目前没有明确规定，在训练 AI 模型（AI model）时，使用受版权保护的作品（copyrighted work）是否需要获得版权所有者（copyright owner）的许可。这使得相关问题有待法院裁决，或等待立法者（lawmakers）采取进一步行动来明确。

* Europe's AI Act provides for artists to make their works unavailable for training AI systems, but music-industry organizations say this provision doesn't work, and artists have no redress if their works were used to train AI systems before the AI Act took effect.

*  欧洲的 AI 法案（AI Act）规定，艺术家可以拒绝将其作品用于训练 AI 系统。然而，音乐行业组织指出，这项规定实际上并不奏效。此外，如果艺术家的作品在 AI 法案生效之前就已经被用于训练 AI 系统，他们将无法获得任何形式的补救。

Why it matters: It remains to be seen whether allowing AI models to learn from copyrighted works is considered fair use under the laws of many countries. Regardless, the current uncertainly over the interpretation of existing laws opens AI companies to potential liability for claims that they have infringed copyrights. Licensing could help to insulate AI developers from legal risk and incentivize creative people to continue to produce fresh works on which to train next-generation models. The STIM license is an early effort to find a formula that works for both parties.

为什么这很重要： 允许人工智能模型（AI models）从受版权保护的作品中学习，这是否符合许多国家的「合理使用」原则，目前尚无定论。然而，无论结果如何，现有法律解释上的不确定性，已经让 AI 公司面临因侵犯版权而承担潜在法律责任的风险。如果能有授权许可，将有助于保护 AI 开发者规避法律风险，同时也能激励创意工作者持续创作新作品，为训练下一代模型提供源源不断的素材。STIM 许可协议正是早期尝试，旨在探索出一个能兼顾各方利益的解决方案。

We're thinking: As technology has evolved from recording to broadcast to streaming, the avenues for musicians to profit from their work have increased, and we expect AI to continue to expand the options.

我们认为，随着技术从录音、广播到流媒体的不断演进，音乐家们从作品中获利的途径也随之增多，我们预计 AI （人工智能）将继续拓展这些选择。

#### Earth Modeled in 10-Meter Squares

Researchers built a model that integrates satellite imagery and other sensor readings across the entire surface of the Earth to reveal patterns of climate, land use, and other features.

#### 地球以 10 米见方的网格建模研究人员建立了一个模型，它整合了覆盖地球整个表面的卫星图像和其他传感器读数，旨在揭示气候、土地利用等各种特征的模式。

What's new: Christopher F. Brown, Michal R. Kazmierski, Valerie J. Pasquarella, and colleagues at Google built AlphaEarth Foundations (AEF), a model that produces embeddings that represent every 10-meter-square spot on the globe for each year between 2017 and 2024. The embeddings can be used to track a wide variety of planetary characteristics such as humidity, precipitation, or vegetation and global challenges such as food production, wildfire risk, or reservoir levels. You can download them here for commercial and noncommercial uses under a CC BY 4.0 license. Google offers financial grants to researchers who want to use them.

最新进展：Google 的 Christopher F. Brown、Michal R. Kazmierski、Valerie J. Pasquarella 及其同事构建了 AlphaEarth Foundations（AEF）模型。这个模型能够生成「嵌入（embeddings）」，它们代表了全球范围内，从 2017 年到 2024 年间每一个 10 平方米区域的独特特征。这些嵌入可用于追踪多种地球表面特征，例如湿度、降水或植被状况，以及应对全球性挑战，比如粮食生产、野火风险或水库水位变化等。您可以在此处下载这些嵌入，它们在 CC BY 4.0 许可下可用于商业和非商业目的。Google 也为希望使用这些数据的研究人员提供财政资助。

Key insight: During training, feeding a model one data type limits its performance. On the other hand, feeding it too many types can cause it to learn spurious patterns. A sensible compromise is feeding it the smallest set of input data types that contain most of the relevant information.

关键见解：在模型训练过程中，如果只输入一种数据类型，会限制模型的性能发挥。反之，如果输入的数据类型过多，模型则可能学习到不必要或误导性的模式。一个明智的折衷方案是，为模型提供包含大部分相关信息的最小数据类型集合。

How it works: The authors used three data types — optical, radar, and thermal videos taken by satellites— as training inputs, but the loss terms referred to several others. Given the three types of satellite videos, each of which represented around 1.28 square kilometers, AEF encoded each video using unspecified encoders. It fed the encoded video to a custom module that integrated both self-attention (within and across frames) and convolutional layers. The architecture enabled the model to produce embeddings that represented each 10x10-meter area over the course of a year. To learn to produce good embeddings, the team trained the model using 4 loss terms:

工作原理： 作者使用了三种类型的数据 —— 包括光学、雷达以及卫星拍摄的热视频 —— 作为训练模型的输入，不过损失函数在计算时还参考了其他一些数据。在获取了这三种卫星视频后，每段视频都覆盖了大约 1.28 平方公里的区域，AEF 会使用特定的编码器（具体型号未提及）对每段视频进行编码。随后，编码后的视频会被传入到一个定制模块中，这个模块结合了自注意力（self-attention）机制（既处理单帧内部关系，也处理跨帧之间的关系）和卷积层。这种架构使得模型能够生成「嵌入（embeddings）」，这些嵌入可以表示一年中每个 10x10 米区域的特征。为了让模型学习生成高质量的嵌入，研究团队使用了 4 种损失函数来训练它：

* The first loss term encouraged the model to reconstruct multiple data types: the 3 inputs as well as elevation maps, climate maps, gravity maps, and images labeled with environment types like "wetland." For each embedding produced by the model, separate vanilla neural networks reconstructed these data types. For example, for each embedding, the system produced a pixel of a thermal video.

*  第一个损失项（loss term）促使模型重建多种数据类型，其中包括 3 种输入数据，以及高程图、气候图、重力图，还有标注了「湿地」等环境类型的图像。对于模型生成的每个嵌入（embedding），独立的标准神经网络（vanilla neural networks）负责重建这些数据类型。举例来说，对于每个嵌入，系统都能生成热视频的一个像素点。

* The second loss term encouraged the embeddings to follow the uniform distribution, ensuring that they weren't all alike. This suited them for clustering and other common approaches.

* 第二个损失项（loss term）旨在促使这些嵌入（embeddings）符合均匀分布（uniform distribution），从而确保它们不会变得千篇一律。这使得它们非常适合用于聚类（clustering）等常见的机器学习方法。

* The third loss term encouraged the model to produce identical embeddings when given the input with a part missing as it did when given the entire input. This enabled the model to make good embeddings even if some — or all — frames were missing from an optical, radar, or thermal video.

第三个损失项旨在鼓励模型在接收到部分缺失的输入时，也能生成与接收完整输入时相同的「嵌入」(embeddings）。这意味着，即使光学、雷达或热感视频中缺少部分甚至全部帧，模型依然能够生成高质量的嵌入。

* The fourth loss term encouraged the model to produce similar embeddings to those of text tagged with matching geographic coordinates from Wikipedia and the Global Biodiversity Information Facility , such as geotagged text about landmarks or animal populations. Conversely, it encouraged the model to produce embeddings unlike those of text corresponding to geographic coordinates that differed (following CLIP). To produce text embeddings, the authors used a frozen version of Gemini followed by a vanilla neural network that learned to help match Gemini's embeddings and AEF's.

* 第四个损失项旨在引导模型生成与来源于 Wikipedia 和全球生物多样性信息基金会（Global Biodiversity Information Facility）中带有匹配地理坐标的文本（例如，关于地标或动物种群的地理标记文本）相似的嵌入（embeddings）。反之，它会促使模型生成与对应不同地理坐标的文本不相似的嵌入结果（这一做法遵循了 CLIP 模型的设计理念）。为了生成文本嵌入，研究人员使用了 Gemini 的一个冻结版本（即其参数在训练过程中保持不变），随后接上一个标准的神经网络，该网络负责学习如何帮助匹配 Gemini 和 AEF 模型所产生的嵌入。

* To adapt AEF for classification or regression, they trained a linear model, given an embedding from AEF, to classify or estimate the labels on a few hundred examples from the test dataset.

* 为了让 AEF（Audio Embedding Factorization）能应用于分类或回归任务，研究人员训练了一个线性模型。这个模型会接收 AEF 生成的嵌入（embedding）作为输入，然后基于测试数据集中数百个样本的标签，进行分类或预测。

Results: The authors compared AEF to 9 alternatives, including manually designed approaches to embedding satellite imagery such as MOSAIKS and CCDC as well as learned models like SatCLIP. Across 11 datasets, AEF outperformed the alternatives by a significant margin.

结果：作者将 AEF 与 9 种替代方案进行了比较，其中包括人工设计的卫星图像嵌入方法，例如 MOSAIKS 和 CCDC，以及像 SatCLIP 这样的基于学习的模型。在 11 个数据集中，AEF 的表现显著优于这些替代方案。

* Classifying crops in Canada, AEF achieved around 51 percent accuracy, while the next-best approach, CCDC, achieved around 47 percent accuracy.

* Classifying changes from one type of environment to another (for example from grass to water), AEF achieved 78.4 percent accuracy, while next-best approach, MOSAIKS, achieved 72 percent accuracy.

*  在加拿大进行农作物分类时，AEF 的准确率约为 51%，而排名第二的方法 CCDC 的准确率约为 47%。

*  在分类环境类型变化（例如从草地变为水域）的任务中，AEF 的准确率达到了 78.4%，而仅次于它的方法 MOSAIKS 的准确率则为 72%。

* Estimating the amount of water per area transferred from land to atmosphere over a month, AEF achieved roughly 12 millimeters mean square error, while MOSAIKS achieved roughly 18 millimeters mean square error.

在估算每月从陆地转移到大气中的单位面积水量的任务中，AEF 模型实现了大约 12 毫米的均方误差（mean square error），而 MOSAIKS 模型则达到了大约 18 毫米的均方误差。

Why it matters: Satellites examine much of Earth's surface, but their output is fragmentary (due to cloud cover and orbital coverage) and difficult to integrate. Machine learning can pack a vast range of overhead data into a comprehensive set of embeddings that can be used with Google's own Earth Engine system and other models. By embedding pixels, AEF makes it easier to map environmental phenomena and track changes over time, and the 10x10-meter resolution offers insight into small-scale features of Earth's surface. The team continues to collect data, revise the model, and publish updated embeddings.

这项技术为何重要： 卫星能观测地球的大部分表面，但由于云层遮挡和轨道覆盖范围的限制，其收集到的数据往往是零散的，难以进行整合分析。机器学习技术能够将海量的空中数据整合为一套全面的嵌入 （embedding），这些嵌入可以与 Google 自有的 Earth Engine 系统以及其他模型协同使用。通过对像素进行嵌入，AEF 模型大大简化了环境现象的制图工作，并能更方便地追踪这些现象随时间的变化。此外，10x10 米的分辨率也为我们深入了解地球表面的微小特征提供了宝贵视角。目前，该团队仍在持续收集数据、改进模型，并定期发布更新后的嵌入。

We're thinking: This project brings AI to the whole world!

我们的设想是：这个项目将人工智能（AI）带给全世界！