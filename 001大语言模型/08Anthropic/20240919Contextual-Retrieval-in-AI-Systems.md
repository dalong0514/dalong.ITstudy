## 20240919Contextual-Retrieval-in-AI-Systems

[Contextual Retrieval in AI Systems \ Anthropic](https://www.anthropic.com/engineering/contextual-retrieval)

Published Sep 19, 2024

For an AI model to be useful in specific contexts，it often needs access to background knowledge. For example，customer support chatbots need knowledge about the specific business they're being used for，and legal analyst bots need to know about a vast array of past cases.

AI 模型（AI model）要想在特定场景中发挥作用，往往需要获取相关的背景知识。例如，客服聊天机器人（customer support chatbots）需要了解其所服务的具体业务信息，而法律分析机器人（legal analyst bots）则需要熟悉大量的过往案例。

Developers typically enhance an AI model's knowledge using Retrieval-Augmented Generation（RAG). RAG is a method that retrieves relevant information from a knowledge base and appends it to the user's prompt，significantly enhancing the model's response. The problem is that traditional RAG solutions remove context when encoding information，which often results in the system failing to retrieve the relevant information from the knowledge base.

开发人员通常会采用一种叫做「检索增强生成」(Retrieval-Augmented Generation，RAG）的技术来扩展 AI 模型的知识。简单来说，RAG 的工作原理就是先从知识库里找到相关的信息，然后把这些信息补充到用户给模型的指令（prompt）中，从而显著提升模型回答的质量。但这里有个问题：传统的 RAG 解决方案在处理和储存信息（也就是编码信息（encoding information)）的过程中，会丢失部分上下文信息。这就常常导致一个后果 —— 当模型需要从知识库里查找资料时，反而找不到那些真正相关的内容了。

In this post，we outline a method that dramatically improves the retrieval step in RAG. The method is called「Contextual Retrieval」and uses two sub-techniques：Contextual Embeddings and Contextual BM25. This method can reduce the number of failed retrievals by 49% and，when combined with reranking，by 67%. These represent significant improvements in retrieval accuracy，which directly translates to better performance in downstream tasks.

在这篇文章中，我们将介绍一种能够显著改进检索增强生成（Retrieval Augmented Generation，RAG）流程中检索环节的方法。这种方法名为「上下文检索」(Contextual Retrieval），它运用了两种核心子技术：上下文嵌入（Contextual Embeddings）和上下文 BM25（Contextual BM25）。该方法能将检索失败的情况减少 49%；如果再结合重排序（reranking）技术，失败率更能降低 67%。这些数据表明，检索准确性得到了巨大提升，从而直接带来了下游任务性能的显著改善。

You can easily deploy your own Contextual Retrieval solution with Claude with our cookbook.

借助我们的实用指南（cookbook），您可以轻松使用 Claude 部署您自己的上下文检索（Contextual Retrieval）解决方案。

[anthropic-cookbook/skills/contextual-embeddings at main · anthropics/anthropic-cookbook](https://github.com/anthropics/anthropic-cookbook/tree/main/skills/contextual-embeddings)

A note on simply using a longer prompt

关于「简单使用更长的提示（Prompt）」的一点说明

Sometimes the simplest solution is the best. If your knowledge base is smaller than 200,000 tokens（about 500 pages of material），you can just include the entire knowledge base in the prompt that you give the model，with no need for RAG or similar methods.

有时候，最简单的方法往往就是最好的。如果你的知识库（knowledge base）不算太大，比如说在 200,000 个 Token（这大约相当于 500 页的材料）以内，那你完全可以直接把整个知识库都塞进你给模型的提示（prompt）里，根本不需要动用 RAG（Retrieval Augmented Generation）这类相对复杂的方法。

A few weeks ago，we released prompt caching for Claude，which makes this approach significantly faster and more cost-effective. Developers can now cache frequently used prompts between API calls，reducing latency by > 2x and costs by up to 90%（you can see how it works by reading our prompt caching cookbook).

几周前，我们为 Claude 推出了提示缓存（prompt caching）功能，这项新功能使得 API 调用速度显著加快，并且更加经济实惠。现在，开发者们可以在多次 API 调用之间缓存那些经常使用的提示，从而将延迟降低 2 倍以上，成本最高可节省 90%（如果你想了解它的工作原理，可以阅读我们的提示缓存实践指南）。

However，as your knowledge base grows，you'll need a more scalable solution. That's where Contextual Retrieval comes in.

然而，随着你的知识库越来越庞大，你就需要一种更能灵活应对数据量增长的解决方案了。这时候，上下文检索（Contextual Retrieval）就派上用场了。

[anthropic-cookbook/misc/prompt\_caching.ipynb at main · anthropics/anthropic-cookbook](https://github.com/anthropics/anthropic-cookbook/blob/main/misc/prompt_caching.ipynb)

### 01. A primer on RAG：scaling to larger knowledge bases

RAG 入门：轻松驾驭不断增长的知识库

For larger knowledge bases that don't fit within the context window，RAG is the typical solution. RAG works by preprocessing a knowledge base using the following steps:

对于那些因规模过大而无法完全放入上下文窗口（context window）内的知识库（knowledge base）来说，RAG 是一种典型的解决方案。RAG 的工作原理，是通过以下步骤对知识库进行预处理（preprocessing)：

1 Break down the knowledge base（the「corpus」of documents）into smaller chunks of text，usually no more than a few hundred tokens;

将知识库（knowledge base）(即文档的语料库（corpus)）拆分成较小的文本块，通常每个文本块不超过几百个 Token；

2 Use an embedding model to convert these chunks into vector embeddings that encode meaning;

使用嵌入模型（embedding model）将这些文本块转换为能够表征其语义的向量嵌入（vector embeddings)；

3 Store these embeddings in a vector database that allows for searching by semantic similarity.

将这些嵌入（embeddings）存储在一个向量数据库（vector database）中，这种数据库支持按照语义相似性（semantic similarity）进行搜索。

At runtime，when a user inputs a query to the model，the vector database is used to find the most relevant chunks based on semantic similarity to the query. Then，the most relevant chunks are added to the prompt sent to the generative model.

在运行时（runtime），当用户向模型输入一个查询（query）时，向量数据库会依据用户查询与这些文本块（chunks）的语义相似性，找出最相关的那些文本块。然后，这些最相关的文本块会被添加到发送给生成式模型（generative model）的提示（prompt）里。

While embedding models excel at capturing semantic relationships，they can miss crucial exact matches. Fortunately，there's an older technique that can assist in these situations. BM25（Best Matching 25）is a ranking function that uses lexical matching to find precise word or phrase matches. It's particularly effective for queries that include unique identifiers or technical terms.

虽然嵌入模型非常擅长理解词语之间的深层含义（语义关系），但它们有时可能会忽略掉一些至关重要的字面精准匹配。幸运的是，有一种年代相对久远一些的技术可以在这种情况下助我们一臂之力。BM25（Best Matching 25）就是一种经典的排序函数（ranking function），它利用词法匹配（lexical matching）的方式来寻找完全相同的单词或短语。当我们的查询中包含了特定的标识符（unique identifiers）或者专业术语（technical terms）时，这种方法就显得特别管用。

BM25 works by building upon the TF-IDF（Term Frequency-Inverse Document Frequency）concept. TF-IDF measures how important a word is to a document in a collection. BM25 refines this by considering document length and applying a saturation function to term frequency，which helps prevent common words from dominating the results.

BM25 算法的工作原理，是基于 TF-IDF（Term Frequency-Inverse Document Frequency，词频 - 逆文档频率）这一核心概念构建的。简单来说，TF-IDF 用来衡量一个词语在整个文档集合中，对于其中某篇特定文档到底有多重要。BM25 则是在 TF-IDF 的基础上做了进一步的优化：它不仅考虑了文档本身的长短，还对词语出现的频率（term frequency）应用了一种叫做「饱和函数（saturation function）」的数学处理。这样做的好处是，可以有效避免那些非常常见但信息量不一定高的词语，在搜索结果中占据不成比例的主导地位。

Here's how BM25 can succeed where semantic embeddings fail：Suppose a user queries「Error code TS-999」in a technical support database. An embedding model might find content about error codes in general，but could miss the exact「TS-999」match. BM25 looks for this specific text string to identify the relevant documentation.

BM25 之所以能在语义嵌入（semantic embeddings）模型表现不佳的某些场景中脱颖而出，原因如下：假设一位用户在技术支持数据库中查询「错误代码（Error code）TS-999」。此时，一个嵌入模型（embedding model）也许能找到与错误代码相关的常规内容，但很可能会忽略掉与「TS-999」这个确切代码完全匹配的结果。而 BM25 则不同，它会直接查找「TS-999」这个特定的文本字符串，从而精确定位到相关的技术文档。

RAG solutions can more accurately retrieve the most applicable chunks by combining the embeddings and BM25 techniques using the following steps:

RAG 解决方案（RAG solutions）可以通过结合嵌入（embeddings）和 BM25 技术，并采用以下步骤，来更准确地检索到最适用的文本片段：

1 Break down the knowledge base（the「corpus」of documents）into smaller chunks of text，usually no more than a few hundred tokens;

将知识库（也就是由众多文档构成的语料库（corpus)）分解成更小的文本片段，这些片段通常不超过几百个 Token；

2 Create TF-IDF encodings and semantic embeddings for these chunks;

为这些数据块创建 TF-IDF 编码（TF-IDF encodings）和语义嵌入（semantic embeddings)；

3 Use BM25 to find top chunks based on exact matches;

使用 BM25 根据精确匹配结果，找出排名最靠前的数据块；

4 Use embeddings to find top chunks based on semantic similarity;

利用嵌入（embeddings）技术，根据语义相似度找出最相关的内容片段；

5 Combine and deduplicate results from（3）and（4）using rank fusion techniques;

使用排序融合（rank fusion）技术，对步骤（3）和（4）得出的结果进行合并与去重；

6 Add the top-K chunks to the prompt to generate the response.

将排名最靠前的 K 个信息片段添加到提示词（prompt）中，用以生成回复。

By leveraging both BM25 and embedding models，traditional RAG systems can provide more comprehensive and accurate results，balancing precise term matching with broader semantic understanding.

通过同时运用 BM25 算法和嵌入模型（embedding model），传统的 RAG（Retrieval Augmented Generation）系统能够提供更全面、更准确的结果，它在精确的关键词匹配和更广泛的语义理解之间取得了巧妙的平衡。

A Standard Retrieval-Augmented Generation（RAG）system that uses both embeddings and Best Match 25（BM25）to retrieve information. TF-IDF（term frequency-inverse document frequency）measures word importance and forms the basis for BM25. This approach allows you to cost-effectively scale to enormous knowledge bases，far beyond what could fit in a single prompt. But these traditional RAG systems have a significant limitation：they often destroy context.

标准的检索增强生成（Retrieval-Augmented Generation）(RAG）系统，通常会结合使用嵌入（embeddings）和 BM25（Best Match 25）这两种技术来检索信息。其中，BM25 算法的基础是 TF-IDF（term frequency-inverse document frequency），这是一种衡量词语重要性的方法。这种组合方法的一大优势是，它能以高性价比的方式，将系统的知识库扩展到非常庞大的规模，远远超过单个提示（prompt）所能承载的信息量。不过，这类传统的 RAG 系统也存在一个显著的局限：它们在检索过程中，往往容易破坏或丢失原有的上下文信息。

#### The context conundrum in traditional RAG

In traditional RAG，documents are typically split into smaller chunks for efficient retrieval. While this approach works well for many applications，it can lead to problems when individual chunks lack sufficient context.

传统 RAG（Retrieval-Augmented Generation）的上下文困境在传统的 RAG 技术中，为了实现高效的信息检索，文档通常会被切割成较小的数据片段。尽管这种方法在许多应用场景下都相当有效，但一旦这些独立的数据片段缺乏足够的上下文信息，就可能引发一些问题。

For example，imagine you had a collection of financial information（say，U.S. SEC filings）embedded in your knowledge base，and you received the following question："What was the revenue growth for ACME Corp in Q2 2023?"

举个例子，假设你的知识库（knowledge base）里存储了一批财务信息（比如美国 SEC 的申报文件），这时你收到了这样一个问题：「ACME Corp 在 2023 年第二季度的营收增长情况如何？」

A relevant chunk might contain the text："The company's revenue grew by 3% over the previous quarter.」However，this chunk on its own doesn't specify which company it's referring to or the relevant time period，making it difficult to retrieve the right information or use the information effectively.

一段相关的文字片段可能写着：「这家公司的收入相比上一季度增长了 3%。」然而，单凭这段文字本身，我们并不知道它具体指的是哪家公司，也没说明相关的时间区间，这就让我们很难找到所需的信息，或者有效地利用这些信息。

### 02. Introducing Contextual Retrieval

上下文检索简介

Contextual Retrieval solves this problem by prepending chunk-specific explanatory context to each chunk before embedding（「Contextual Embeddings」）and creating the BM25 index（「Contextual BM25」).

上下文检索（Contextual Retrieval）通过以下方式解决了这个问题：在对每个信息块进行嵌入（embedding）(也就是 「上下文嵌入（Contextual Embeddings）」）和创建 BM25 索引（也就是 「上下文 BM25（Contextual BM25）」）之前，先为每个信息块添加一段该信息块专属的解释性上下文。

Let's return to our SEC filings collection example. Here's an example of how a chunk might be transformed:

我们再来看看之前讨论过的 SEC（美国证券交易委员会）文件集的例子。下面通过一个例子，看看文本块（chunk）是如何被转换的：

```
original_chunk = "The company's revenue grew by 3% over the previous quarter."
contextualized_chunk = "This chunk is from an SEC filing on ACME corp's performance in Q2 2023; the previous quarter's revenue was $314 million. The company's revenue grew by 3% over the previous quarter."
```

```
original_chunk = 该公司收入较上一季度增长了 3%。"
contextualized_chunk = "此文本块（chunk）摘自 ACME corp 关于其 2023 年第二季度业绩的 SEC（美国证券交易委员会）文件；上一季度的收入为 3.14 亿美元。该公司收入较上一季度增长了 3%。"
```

It is worth noting that other approaches to using context to improve retrieval have been proposed in the past. Other proposals include：adding generic document summaries to chunks（we experimented and saw very limited gains），hypothetical document embedding，and summary-based indexing（we evaluated and saw low performance). These methods differ from what is proposed in this post.

值得一提的是，过去也曾有人提出过其他利用上下文信息来提升检索效果的方法。这些方法包括：为文本块（chunks）添加通用文档摘要（我们试验过，发现效果提升非常有限）、假设性文档嵌入（hypothetical document embedding），以及基于摘要的索引（summary-based indexing）(我们评估后发现性能不佳）。这些思路都与我们在这篇文章中提出的方法有所不同。

#### Implementing Contextual Retrieval

Of course，it would be far too much work to manually annotate the thousands or even millions of chunks in a knowledge base. To implement Contextual Retrieval，we turn to Claude. We've written a prompt that instructs the model to provide concise，chunk-specific context that explains the chunk using the context of the overall document. We used the following Claude 3 Haiku prompt to generate context for each chunk:

实现上下文检索想象一下，一个知识库里可能有成千上万甚至数百万个信息片段（chunks），要人工给它们一一添加注释，那工作量可就太大了。为了实现上下文检索（Contextual Retrieval）功能，我们找到了一个得力助手 —— Claude。我们编写了一段特殊的指令，也就是提示（prompt），来引导这个模型。通过这个提示，Claude 能够针对每一个信息片段，参考整个文档的背景信息，生成一段简洁明了、专门解释这个信息片段的上下文描述。具体来说，我们使用了下面这段 Claude 3 Haiku 的提示，来为每一个信息片段生成相应的上下文描述：

```
<document> 
{{WHOLE_DOCUMENT}} 
</document> 
Here is the chunk we want to situate within the whole document 
<chunk> 
{{CHUNK_CONTENT}} 
</chunk> 
Please give a short succinct context to situate this chunk within the overall document for the purposes of improving search retrieval of the chunk. Answer only with the succinct context and nothing else.
```

```markdown
<document>
{{WHOLE_DOCUMENT}}
</document>
这是我们希望将其置于整个文档背景下进行理解的文本片段
<chunk>
{{CHUNK_CONTENT}}
</chunk>
请提供一段简明扼要的上下文，用以说明该文本片段在整个文档中的位置，目的是提升该片段的搜索检索（search retrieval）效果。请仅用简洁的上下文回答，不包含任何其他内容。
```

The resulting contextual text，usually 50-100 tokens，is prepended to the chunk before embedding it and before creating the BM25 index.

由此生成的上下文文本（通常为 50-100 个 Token），会被添加到数据块（chunk）的最前面。这步操作先于对该数据块进行嵌入（embedding）处理以及为它创建 BM25 索引。

Here's what the preprocessing flow looks like in practice:

在实际应用中，预处理流程（preprocessing flow）如下所示：

*Contextual Retrieval is a preprocessing technique that improves retrieval accuracy.*

*上下文检索（Contextual Retrieval）是一种预处理技术（preprocessing technique），它可以提升信息检索的准确度。*

If you're interested in using Contextual Retrieval，you can get started with our cookbook.

如果你有兴趣使用上下文检索（Contextual Retrieval），不妨从我们的实践指南（cookbook）开始入手。

[anthropic-cookbook/skills/contextual-embeddings at main · anthropics/anthropic-cookbook](https://github.com/anthropics/anthropic-cookbook/tree/main/skills/contextual-embeddings)

#### Using Prompt Caching to reduce the costs of Contextual Retrieval

Contextual Retrieval is uniquely possible at low cost with Claude，thanks to the special prompt caching feature we mentioned above. With prompt caching，you don't need to pass in the reference document for every chunk. You simply load the document into the cache once and then reference the previously cached content. Assuming 800 token chunks，8k token documents，50 token context instructions，and 100 tokens of context per chunk，the one-time cost to generate contextualized chunks is $1.02 per million document tokens.

利用提示缓存（Prompt Caching）降低上下文检索（Contextual Retrieval）的成本想用较低的成本实现上下文检索（Contextual Retrieval）吗？在 Claude 这个工具上，这完全不成问题！这主要归功于它一项非常特别的功能 —— 提示缓存（Prompt Caching）。有了这个功能，你就不用再为处理文档的每一个小片段（chunk）都重复传入完整的参考资料了。你只需要把整个文档一次性加载到缓存（cache）里，之后就可以轻松调用这些已经缓存好的内容。我们来算一笔账：假设文档被切割成许多片段（chunk），每个片段（chunk）包含 800 个 Token（Token），整个文档有 8000 个 Token，再加上 50 个 Token 的上下文指令（context instructions），并且每个片段（chunk）自身还需要 100 个 Token 的上下文信息。在这种情况下，把这些原始片段（chunk）加工成带有丰富上下文信息的版本，一次性处理成本仅仅是每处理一百万个文档 Token 需要 1.02 美元。

##### Methodology

研究方法

We experimented across various knowledge domains（codebases，fiction，ArXiv papers，Science Papers），embedding models，retrieval strategies，and evaluation metrics. We've included a few examples of the questions and answers we used for each domain in Appendix II.

我们的实验覆盖了多个知识领域（例如代码库（codebases）、小说（fiction）、ArXiv 论文（ArXiv papers）和科学论文（Science Papers)），并探索了不同的嵌入模型（embedding models）、检索策略（retrieval strategies）以及评估指标（evaluation metrics）。附录 II 中包含了一些我们在各个领域中所使用的问答示例。

The graphs below show the average performance across all knowledge domains with the top-performing embedding configuration（Gemini Text 004）and retrieving the top-20-chunks. We use 1 minus recall@20 as our evaluation metric，which measures the percentage of relevant documents that fail to be retrieved within the top 20 chunks. You can see the full results in the appendix - contextualizing improves performance in every embedding-source combination we evaluated.

下方的图表展示了当我们采用表现最佳的嵌入（embedding）配置（Gemini Text 004），并检索排名前 20 的文本块（chunks）时，在所有知识领域中所取得的平均性能。我们使用「1 减去召回率 @20（recall@20）」作为我们的评估指标，这个指标衡量的是在前 20 个文本块（chunks）中未能成功检索到的相关文档所占的百分比。您可以在附录中查看完整的实验结果 —— 在我们评估的每一种嵌入（embedding）与数据源的组合中，结合上下文（contextualizing）的方法都提升了性能。

##### Performance improvements

性能提升

Our experiments showed that:

我们的实验表明：

1 Contextual Embeddings reduced the top-20-chunk retrieval failure rate by 35%（5.7% → 3.7%).

上下文嵌入（Contextual Embeddings）技术让排名前 20 的文本片段的检索失败率降低了 35%（从 5.7% 降至 3.7%）。

2 Combining Contextual Embeddings and Contextual BM25 reduced the top-20-chunk retrieval failure rate by 49%（5.7% → 2.9%).

而将上下文嵌入和上下文 BM25（Contextual BM25）两者相结合，更是让排名前 20 的文本片段的检索失败率大幅降低了 49%（从 5.7% 锐减到 2.9%）。

*Combining Contextual Embedding and Contextual BM25 reduce the top-20-chunk retrieval failure rate by 49%.*

*将上下文嵌入（Contextual Embedding）和上下文 BM25（Contextual BM25）结合起来，能够将排名前 20 的文本片段的检索失败率降低 49%。*

##### Implementation considerations

实现时的注意事项

When implementing Contextual Retrieval，there are a few considerations to keep in mind:

在实现上下文检索（Contextual Retrieval）时，有几点需要牢记在心：

1 Chunk boundaries：Consider how you split your documents into chunks. The choice of chunk size，chunk boundary，and chunk overlap can affect retrieval performance1.

数据块（Chunk）边界的考量：你需要仔细思考如何将你的文档分割成一个个的数据块。这是因为，数据块的大小、数据块边界的设定，以及数据块之间的重叠部分，这些因素的选择都会影响到最终的检索性能 1。

2 Embedding model：Whereas Contextual Retrieval improves performance across all embedding models we tested，some models may benefit more than others. We found Gemini and Voyage embeddings to be particularly effective.

嵌入模型（Embedding model）：虽然上下文检索（Contextual Retrieval）的方法能够提升我们测试的所有嵌入模型的表现，不过，不同模型从中获得的助益程度可能并不相同。我们发现，Gemini 和 Voyage 这两种嵌入模型的效果尤为突出。

3 Custom contextualizer prompts：While the generic prompt we provided works well，you may be able to achieve even better results with prompts tailored to your specific domain or use case（for example，including a glossary of key terms that might only be defined in other documents in the knowledge base).

自定义情境化提示（Custom contextualizer prompts）：虽然我们提供的通用提示效果已经不错，但如果你能根据自己的特定领域或应用场景来量身定制提示，就可能会取得更好的效果（例如，可以加入一份关键术语的词汇表，这些术语的定义可能只存在于知识库（knowledge base）中的其他文档里）。

4 Number of chunks：Adding more chunks into the context window increases the chances that you include the relevant information. However，more information can be distracting for models so there's a limit to this. We tried delivering 5，10，and 20 chunks，and found using 20 to be the most performant of these options（see appendix for comparisons）but it's worth experimenting on your use case.

文本块（chunks）的数量：在上下文窗口（context window）中增加更多的文本块，确实能提高模型捕获到相关信息的几率。然而，过多的信息有时反而会分散模型的注意力，甚至造成干扰，因此文本块的数量也不是越多越好。我们分别尝试了提供 5 个、10 个和 20 个文本块进行测试，结果发现，在这几种方案中，使用 20 个文本块时模型的表现最佳（详细对比请参见附录）。不过，具体哪种方案最适合，还需要您在自己的应用场景中进行实验验证。

Always run evals：Response generation may be improved by passing it the contextualized chunk and distinguishing between what is context and what is the chunk.

始终进行评估：通过将整合了上下文信息的文本片段（contextualized chunk）传递给模型，并让模型区分什么是上下文（context）、什么是当前要处理的文本片段（chunk），这样或许能改进响应生成的效果。

### 03. Further boosting performance with Reranking

通过重新排序（Reranking）进一步提升性能

In a final step，we can combine Contextual Retrieval with another technique to give even more performance improvements. In traditional RAG，the AI system searches its knowledge base to find the potentially relevant information chunks. With large knowledge bases，this initial retrieval often returns a lot of chunks—sometimes hundreds—of varying relevance and importance.

最后一步，我们可以将上下文检索（Contextual Retrieval）与另一种技术相结合，从而进一步提升性能。在传统的 RAG 中， AI 系统会搜索其知识库，以找出那些可能相关的信息块（information chunks）。如果知识库非常庞大，这种初步检索往往会返回大量的信息块 —— 有时甚至多达数百个 —— 而这些信息块的相关性和重要程度则各不相同。

Reranking is a commonly used filtering technique to ensure that only the most relevant chunks are passed to the model. Reranking provides better responses and reduces cost and latency because the model is processing less information. The key steps are:

重排序（Reranking）是一种常用的过滤技术，它能确保只有最相关的信息区块被送入模型进行处理。这样做的好处是，模型不仅能给出更优质的回答，还能有效降低运行成本和响应延迟，因为它需要处理的信息量大大减少了。其关键步骤如下：

1 Perform initial retrieval to get the top potentially relevant chunks（we used the top 150);

首先，执行初始检索（initial retrieval），以获取那些排名最靠前且可能相关的区块（chunks）(我们选用了最靠前的 150 个)；

2 Pass the top-N chunks，along with the user's query，through the reranking model;

然后，将排名最靠前的 N 个区块（chunks），连同用户的查询一起，交由重排序模型（reranking model）进行处理；

3 Using a reranking model，give each chunk a score based on its relevance and importance to the prompt，then select the top-K chunks（we used the top 20);

使用一个重排序模型（reranking model），根据每个文本块与提示（prompt）的相关性和重要性给它们打分，然后选出得分最高的 K 个文本块（我们选用了前 20 个)；

4 Pass the top-K chunks into the model as context to generate the final result.

把这些得分最高的 K 个文本块作为上下文（context）信息传递给模型，用它们来生成最终结果。

*Combine Contextual Retrieva and Reranking to maximize retrieval accuracy.*

*结合上下文检索（Contextual Retrieval）和重排序（Reranking）来最大程度地提高检索准确率。*

#### Performance improvements

性能改进

There are several reranking models on the market. We ran our tests with the Cohere reranker. Voyage also offers a reranker，though we did not have time to test it. Our experiments showed that，across various domains，adding a reranking step further optimizes retrieval.

市面上有好几种重排序模型（reranking models）。我们使用 Cohere 重排序器进行了测试。Voyage 公司也提供了一款重排序器，不过我们还没来得及对其进行测试。我们的实验表明，在各种不同的应用领域，增加一个重排序步骤能够进一步优化检索效果。

Specifically，we found that Reranked Contextual Embedding and Contextual BM25 reduced the top-20-chunk retrieval failure rate by 67%（5.7% → 1.9%).

具体而言，我们发现，通过运用重排序上下文嵌入（Reranked Contextual Embedding）和上下文 BM25（Contextual BM25）这两种技术，在检索最重要的前 20 个文本片段（top-20-chunk）时，检索失败的概率从原先的 5.7% 大幅下降到了 1.9%，降幅高达 67%。

*Reranked Contextual Embedding and Contextual BM25 reduces the top-20-chunk retrieval failure rate by 67%.*

*重排序上下文嵌入和上下文 BM25 将检索最重要的前 20 个文本片段的失败率降低了 67%。*

##### Cost and latency considerations

成本和延迟的考量

One important consideration with reranking is the impact on latency and cost，especially when reranking a large number of chunks. Because reranking adds an extra step at runtime，it inevitably adds a small amount of latency，even though the reranker scores all the chunks in parallel. There is an inherent trade-off between reranking more chunks for better performance vs. reranking fewer for lower latency and cost. We recommend experimenting with different settings on your specific use case to find the right balance.

谈到重排序（reranking），一个重要的考虑因素是它对处理速度（延迟）和运行成本的影响，尤其是当我们需要对大量的文本块（chunks）进行重排序的时候。因为重排序这个过程，在程序运行时额外增加了一个步骤，所以即便重排序器（reranker）可以并行处理所有文本块的评分，也难免会带来一些额外的延迟。因此，这里天然就存在一种取舍：是重排序更多的文本块以追求更好的效果呢？还是减少重排序的数量，来换取更低的延迟和成本？我们建议您可以根据自己的具体应用场景，多多尝试不同的设置，从而找到那个最适合的平衡点。

### Conclusion

We ran a large number of tests，comparing different combinations of all the techniques described above（embedding model，use of BM25，use of contextual retrieval，use of a reranker，and total # of top-K results retrieved），all across a variety of different dataset types. Here's a summary of what we found:

我们进行了大量的测试，对比了上文描述的各项技术在不同组合下的表现（这些技术包括嵌入模型（embedding model）、BM25 的使用、上下文检索（contextual retrieval）的使用、重排序器（reranker）的使用，以及检索到的 top-K 结果的总数），这些测试涵盖了多种不同类型的数据集。我们的主要发现总结如下：

1 Embeddings+BM25 is better than embeddings on their own;

将嵌入（embeddings）与 BM25 相结合的方法，比单独使用嵌入（embeddings）的效果更好；

2 Voyage and Gemini have the best embeddings of the ones we tested;

在我们测试过的这些嵌入（embeddings）中，Voyage 和 Gemini 的表现最好；

3 Passing the top-20 chunks to the model is more effective than just the top-10 or top-5;

将排名前 20 的文本块（chunks）传递给模型（model），比仅传递排名前 10 或排名前 5 的文本块更为有效；

4 Adding context to chunks improves retrieval accuracy a lot;

为文本块添加上下文（context），能大幅提高检索准确性（retrieval accuracy）；

5 Reranking is better than no reranking;

进行重排序（Reranking）的效果，总比不进行要好；

6 All these benefits stack：to maximize performance improvements，we can combine contextual embeddings（from Voyage or Gemini）with contextual BM25，plus a reranking step，and adding the 20 chunks to the prompt.

所有这些方法的优势还能进一步叠加：为了最大限度地提升效果，我们可以将来自 Voyage 或 Gemini 的上下文嵌入（contextual embeddings）与上下文 BM25（contextual BM25）相结合，再整合一个重排序步骤，并将 20 个信息片段（chunks）添加到提示语（prompt）中。

We encourage all developers working with knowledge bases to use our cookbook to experiment with these approaches to unlock new levels of performance.

我们鼓励所有从事知识库（knowledge bases）相关工作的开发者们，积极利用我们提供的 cookbook 来探索这些方法，从而将系统性能提升到新的高度。

### Appendix I

附录 I

Below is a breakdown of results across datasets，embedding providers，use of BM25 in addition to embeddings，use of contextual retrieval，and use of reranking for Retrievals @ 20.

接下来，我们将详细解析在不同条件下，针对检索结果的前 20 项（Retrievals @ 20）的测试表现。这里的「不同条件」涵盖了：所使用的数据集，提供嵌入（Embedding）技术的服务方，是否在嵌入（Embedding）技术的基础上额外使用了 BM25 算法，是否采用了上下文检索（Contextual Retrieval），以及是否对结果进行了重排序（Reranking）。

See Appendix II for the breakdowns for Retrievals @ 10 and @ 5 as well as example questions and answers for each dataset.

有关 Retrievals @ 10 和 @ 5 的详细分类数据，以及各个数据集的示例问题和答案，请参见附录 II。