## 20250223Fine-Tuning-LLMs-A-Guide-With-Examples

[Fine-Tuning LLMs: A Guide With Examples](https://app.datacamp.com/learn/tutorials/fine-tuning-large-language-models?utm_source=chatgpt.com?registration_source=google_onetap)

Learn how fine-tuning large language models (LLMs) improves their performance in tasks like language translation, sentiment analysis, and text generation.

2024 年 12 月

profile picture of Josep Ferrer

Josep Ferrer

Fine-tuning large language models (LLMs) is important for tailoring these advanced algorithms to specific tasks or domains.

微调（Fine-tuning）大语言模型（LLM）非常重要，它可以使这些先进的算法更好地适应特定任务或领域。

This process enhances the model's performance on specialized tasks and significantly broadens its applicability across various fields. This means we can take advantage of the natural language processing capacity of pre-trained and open-source LLMs and further train them to perform our specific tasks.

这个过程能够增强模型在特定任务上的表现，并显著扩展其在不同领域的应用范围。这意味着我们可以充分利用预训练和开源的大语言模型（LLM）的自然语言处理能力，并对其进行进一步训练，以完成我们特定的任务。

In this tutorial, I’ll explain the concept of pre-trained language models and guide you through the step-by-step fine-tuning process, using GPT-2 with Hugging Face as an example.

在本教程中，我将解释预训练语言模型的概念，并以 GPT-2（结合 Hugging Face 使用）为例，一步步地指导你完成微调过程。

### 01. Understanding How Pre-trained Language Models Work

理解预训练语言模型的工作原理

The Language Model is a type of machine learning algorithm designed to forecast the subsequent word in a sentence, drawing from its preceding segments. It is based on the Transformers architecture, which is deeply explained in our article about How Transformers work.

语言模型（Language Model）是一种机器学习算法，其设计目的是预测句子中的下一个词，并从其前面的部分中提取信息。它基于 Transformer 架构（Transformer architecture），这在我们的文章《Transformer 的工作原理》中得到了深入的解释。

[how-transformers-work - DataCamp Learn](https://app.datacamp.com/learn/tutorials/how-transformers-work)

Pre-trained language models, such as GPT (Generative Pre-trained Transformer), are trained on vast amounts of text data. This enables LLMs to grasp the fundamental principles governing the use of words and their arrangement in the natural language.

预训练语言模型，例如 GPT（Generative Pre-trained Transformer，生成式预训练 Transformer），在海量的文本数据上进行训练。这使得大语言模型（LLM）能够掌握自然语言中词语使用和排列的基本规则。

Image by Author. LLM input and output.

The most important part is that these models are not only good at understanding natural language but are also good at generating human-like text based on the input they receive.

最重要的是，这些模型不仅擅长理解自然语言，而且还擅长根据接收到的信息生成像人一样自然的文本。

And the best part of it all?

那么，最令人兴奋的是什么呢？

These models are already open to the masses using APIs. If you want to learn how to take advantage of OpenAI’s most powerful LLMs, you can learn how to do it by following this cheat sheet on OpenAI’s API.

这些模型已经通过应用程序编程接口（API）面向大众开放。如果您希望了解如何充分利用 OpenAI 最强大的大语言模型，可以参考 OpenAI 提供的 API 速查表进行学习。

### 02. What is Fine-tuning, and Why is it Important?

什么是微调，为什么它很重要？

Fine-tuning is the process of taking a pre-trained model and further training it on a domain-specific dataset.

微调是指采用预训练模型，并在特定领域的数据集上进一步训练它的过程。

Most LLM models today have a very good global performance but fail in specific task-oriented problems. The fine-tuning process offers considerable advantages, including lowered computation expenses and the ability to leverage cutting-edge models without the necessity of building one from the ground up.

如今，大多数大语言模型（LLM）都具有非常好的全局性能，但在特定的、以任务为导向的问题上表现不佳。微调过程提供了相当大的优势，包括降低计算成本，以及能够利用先进的模型，而无需从零开始构建模型。

Transformers grant access to an extensive collection of pre-trained models suited for various tasks. Fine-tuning these models is a crucial step for improving the model's ability to perform specific tasks, such as sentiment analysis, question answering, or document summarization, with higher accuracy.

Transformer 提供了大量预训练模型，这些模型适用于各种任务。微调这些模型是关键步骤，能够提高模型执行特定任务的能力，例如情感分析、问答或文档摘要，从而提高准确性。

Image by Author. Visualizing the Fine-Tuning process.

可视化微调过程图由作者提供。展示了微调过程的可视化结果。

Fine-tuning tailors the model to have a better performance for specific tasks, making it more effective and versatile in real-world applications. This process is essential for tailoring an existing model to a particular task or domain.

微调旨在调整模型，使其在特定任务上表现更佳，从而在实际应用中更加高效和通用。对于根据特定任务或领域定制现有模型而言，此过程至关重要。

Whether to engage in fine-tuning hinges on your goals, which typically vary based on the specific domain or task at hand.

是否需要进行微调，主要取决于您的目标。这些目标通常会因具体领域或当前任务而异。

### 03. The Different Types of Fine-tuning

Fine-tuning can be approached in several ways, depending mainly on its main focus and specific goals.

不同类型的微调微调有多种实现方式，主要区别在于其关注重点和具体目标。

Supervised fine-tuning

监督式微调（Supervised fine-tuning)

The most straightforward and common fine-tuning approach. The model is further trained on a labeled dataset specific to the target task to perform, such as text classification or named entity recognition.

这是最直接且常见的微调方法。模型会在一个专门针对目标任务的已标注数据集上进行进一步的训练，例如进行文本分类或命名实体识别等任务。

For instance, we would train our model on a dataset containing text samples labeled with their corresponding sentiment for sentiment analysis.

例如，我们可以用一个数据集来训练模型，这个数据集包含带有对应情感标签的文本样本，用于情感分析。

Few-shot learning

少样本学习（Few-shot learning)

There are some cases where collecting a large labeled dataset is impractical. Few-shot learning tries to address this by providing a few examples (or shots) of the required task at the beginning of the input prompts. This helps the model have a better context of the task without an extensive fine-tuning process.

在某些情况下，收集大型的标注数据集是不现实的。少样本学习试图通过在输入提示的开头提供一些所需任务的示例来解决这个问题。这有助于模型更好地理解任务的上下文，而无需进行大规模的精调（Fine-tuning）。

Transfer learning

迁移学习

Even though all fine-tuning techniques are a form of transfer learning, this category is specifically aimed to allow a model to perform a task different from the task it was initially trained on. The main idea is to leverage the knowledge the model has gained from a large, general dataset and apply it to a more specific or related task.

尽管所有微调技术都属于迁移学习，但此处的迁移学习更侧重于让模型执行与初始训练不同的任务。核心思想是：利用模型从海量、通用的数据集中学习到的知识，并将其迁移应用到更具体或相关的任务中。

Domain-specific fine-tuning

领域特定微调

This type of fine-tuning tries to adapt the model to understand and generate text that is specific to a particular domain or industry. The model is fine-tuned on a dataset composed of text from the target domain to improve its context and knowledge of domain-specific tasks.

这类微调旨在使模型能够理解并生成特定领域或行业的专业文本。通过使用目标领域的数据集对模型进行微调，可以提升模型对该领域上下文的理解以及处理领域特定任务的能力。

For instance, to generate a chatbot for a medical app, the model would be trained with medical records, to adapt its language understanding capabilities to the health field.

例如，要为医疗 App 开发聊天机器人，需要使用医疗记录训练模型，使其语言理解能力适应医疗健康领域。

### 04. A Step-by-Step Guide to Fine-tuning a LLM

Run and edit the code from this tutorial online
We already know that Fine-tuning is the process of taking a pre-trained model and updating its parameters by training on a dataset specific to your task. So, let’s exemplify this concept by fine-tuning a real model.

LLM 微调的分步指南在线运行和编辑本教程中的代码我们已经知道微调是指，采用一个预训练模型，并通过在特定于你任务的数据集上训练来更新它的参数的过程。因此，让我们通过微调一个真实模型来阐释这个概念。

Imagine we are working with GPT-2, but we detect it is quite bad at inferring the sentiments of tweets.

假设我们正在使用 GPT-2，但发现它在理解推文的情绪方面表现很差。

One natural question that comes to mind is: Can we do something to improve its performance?

一个很自然的问题是：我们能做些什么来改进它的表现呢？

We can take advantage of fine-tuning by training our pre-trained GPT-2 model from the Hugging Face model with a dataset containing tweets and their corresponding sentiments so the performance improves. Here's a basic example of fine-tuning a model for sequence classification:

我们可以通过微调来提升性能，具体做法是：使用包含推文及其对应情感的数据集，对来自 Hugging Face 的预训练 GPT-2 模型进行训练。以下是一个对模型进行微调，以用于序列分类的基本示例：

Step 1: Choose a pre-trained model and a dataset

步骤 1：选择一个预训练模型和一个数据集

To fine-tune a model, we always need to have a pre-trained model in mind. In our case, we are going to perform some simple fine-tuning using GPT-2.

为了对模型进行微调，我们需要首先确定一个预训练模型。在本例中，我们将使用 GPT-2 进行一些简单的微调。

Screenshot of Hugging Face Datasets Hub. Selecting OpenAI’s GPT2 model.

Hugging Face Datasets Hub 的屏幕截图。选择了 OpenAI 的 GPT2 模型。

Always keep in mind to select a model architecture suitable for your task.

请务必选择与您的任务相匹配的模型架构。

Step 2: Load the data to use

步骤 2：加载要使用的数据

Now that we have our model, we need some good-quality data to work with, and this is precisely where the datasets library kicks in.

有了合适的模型之后，我们需要一些高质量的数据。这正是 datasets 库大显身手的地方，它可以帮助我们轻松加载和管理各种数据集。

In my case, I will use the Hugging Face datasets library to import a dataset containing tweets segmented by their sentiment (Positive, Neutral or Negative).

在本例中，我将使用 Hugging Face datasets 库导入一个数据集，其中包含了根据情感（正面、中性或负面）分类的推文。

```python
from datasets import load_dataset

dataset = load_dataset("mteb/tweet_sentiment_extraction")
df = pd.DataFrame(dataset['train'])
```

If we check the dataset we just downloaded, it is a dataset containing a subset for training and a subset for testing. If we convert the training subset to a dataframe, it looks as follows.

我们刚刚下载的数据集包含训练集和测试集。将训练集转换为 DataFrame（一种常用的数据结构）后，其结构如下所示。

Fig: The data set to be used.

Step 3: Tokenizer

Step 3：Tokenizer（分词器)

Now that we already have our dataset, we need a tokenizer to prepare it to be parsed by our model.

现在我们已经准备好了数据集，接下来需要一个 tokenizer（分词器），用于准备数据，以便模型能够解析这些数据。

As LLMs work with tokens, we require a tokenizer to process the dataset. To process your dataset in one step, use the Datasets map method to apply a preprocessing function over the entire dataset.

由于大语言模型（LLM）是以 token（令牌）为单位进行处理的，因此我们需要 tokenizer（分词器）来处理数据集。为了能够一次性处理数据集，可以使用 Datasets 库的 map 方法，将预处理函数应用到整个数据集上。

This is why the second step is to load a pre-trained Tokenizer and tokenize our dataset so it can be used for fine-tuning.

因此，第二步是加载一个预训练的 Tokenizer，并对我们的数据集进行 Tokenize 处理，使其能够用于微调。

```python
from transformers import GPT2Tokenizer

\# Loading the dataset to train our model
dataset = load_dataset("mteb/tweet_sentiment_extraction")

tokenizer = GPT2Tokenizer.from_pretrained("gpt2")
tokenizer.pad_token = tokenizer.eos_token
def tokenize_function(examples):
   return tokenizer(examples["text"], padding="max_length", truncation=True)

tokenized_datasets = dataset.map(tokenize_function, batched=True)
```


```python
from transformers import GPT2Tokenizer

\# 加载数据集以训练模型
dataset = load_dataset（"mteb/tweet_sentiment_extraction"） # 加载 mteb/tweet_sentiment_extraction 数据集

tokenizer = GPT2Tokenizer.from_pretrained（"gpt2"） # 使用 GPT2Tokenizer 加载 GPT2 的预训练模型
tokenizer.pad_token = tokenizer.eos_token # 将 pad token 设置为 eos token
def tokenize_function（examples)： # 定义 Tokenize 函数
  return tokenizer（examples ["text"]，padding="max_length」，truncation=True）# 对 examples ["text"] 进行 tokenize，使用 max_length 填充，并进行截断
tokenized_datasets = dataset.map(tokenize_function, batched=True)
```

BONUS: To improve our processing requirements, we can create a smaller subset of the full dataset to fine-tune our model. The training set will be used to fine-tune our model, while the testing set will be used to evaluate it.

补充说明：为了降低计算需求，我们可以从完整数据集中创建一个更小的子集来微调模型。训练集将用于微调模型，而测试集将用于评估模型。

```python
small_train_dataset = tokenized_datasets["train"].shuffle(seed=42).select(range(1000))
small_eval_dataset = tokenized_datasets["test"].shuffle(seed=42).select(range(1000))
```

Step 4: Initialize our base model

第四步：初始化我们的基础模型

Start by loading your model and specify the number of expected labels. From the Tweet’s sentiment dataset card, you know there are three labels:

首先加载您的模型并指定预期标签的数量。从 Tweet 情感数据集的介绍中，您知道有三个标签：

```python
from transformers import GPT2ForSequenceClassification

model = GPT2ForSequenceClassification.from_pretrained("gpt2", num_labels=3)
```

Step 5: Evaluate method

第五步：评估方法

Transformers provides a Trainer class optimized for training. However, this method does not include how to evaluate the model. This is why, before starting our training, we will need to pass Trainer a function to evaluate our model performance.

Transformers 库提供了一个 Trainer 类，该类针对训练进行了优化。然而，该类并未包含模型评估的方法。因此，在开始训练之前，我们需要向 Trainer 传递一个函数，用于评估模型的性能。

```python
import evaluate

metric = evaluate.load("accuracy")

def compute_metrics(eval_pred):
   logits, labels = eval_pred
   predictions = np.argmax(logits, axis=-1)
   return metric.compute(predictions=predictions, references=labels)
```

这段代码定义了一个名为 `compute_metrics` 的函数，它接受 `eval_pred` 作为输入，其中包含模型的 `logits`(Logits，也称为未归一化的对数概率）和真实标签 `labels`。函数首先使用 `np.argmax` 找到 `logits` 中概率最高的类别，将其作为预测结果 `predictions`。然后，它使用 `metric.compute` 函数，将预测结果 `predictions` 和真实标签 `labels` 作为输入，计算评估指标。

Step 6: Fine-tune using the Trainer Method

步骤 6：使用 Trainer 方法进行微调

Our final step is to set up the training arguments and start the training process. The Transformers library contains the Trainer class, which supports a wide range of training options and features such as logging, gradient accumulation, and mixed precision. We first define the training arguments together with the evaluation strategy. Once everything is defined, we can easily train the model simply using the train() command.

我们的最后一步是设置训练参数并启动训练过程。Transformers 库包含了 Trainer 类，它支持各种训练选项和功能，例如日志记录、梯度累积和混合精度。我们首先定义训练参数和评估策略。完成所有定义后，我们就可以简单地使用 `train()` 命令轻松地训练模型。

```python
from transformers import TrainingArguments, Trainer

training_args = TrainingArguments(
   output_dir="test_trainer",
   #evaluation_strategy="epoch",
   per_device_train_batch_size=1,  # Reduce batch size here
   per_device_eval_batch_size=1,    # Optionally, reduce for evaluation as well
   gradient_accumulation_steps=4
   )

trainer = Trainer(
   model=model,
   args=training_args,
   train_dataset=small_train_dataset,
   eval_dataset=small_eval_dataset,
   compute_metrics=compute_metrics,
   )

trainer.train()
```

```python
from transformers import TrainingArguments，Trainer

training_args = TrainingArguments（
  output_dir="test_trainer",
  # evaluation_strategy="epoch」，# 评估策略，每 epoch 评估一次
  per_device_train_batch_size=1， # 每个设备的训练批次大小，这里减小了批次大小
  per_device_eval_batch_size=1，  # 每个设备的评估批次大小，可以选择性的减小评估批次大小
  gradient_accumulation_steps=4
  )

trainer = Trainer(
   model=model,
   args=training_args,
   train_dataset=small_train_dataset,
   eval_dataset=small_eval_dataset,
   compute_metrics=compute_metrics,
   )

trainer.train()
```

After training, evaluate the model's performance on a validation or test set. Again, the trainer class already contains an evaluate method that takes care of this.

在训练之后，需要在验证集或测试集上评估模型的性能。同样，训练器类已经包含 `evaluate` 方法来完成这项评估工作。

```python
import evaluate

trainer.evaluate()
```'

在机器学习模型训练完成后，我们通常需要评估（evaluate）模型的性能。这里，我们首先导入 `evaluate` 库，它提供了一系列用于评估模型效果的指标。然后，我们使用 `trainer.evaluate()`来对训练好的模型 `trainer` 进行评估，从而得到模型在验证集上的各项指标，例如准确率、精确率和召回率等。

These are the most basic steps to perform a fine-tuning of any LLM. Remember to fine-tune a LLM is highly computationally demanding, and your local computer might not have enough power to do so.

以下是微调任何大语言模型（LLM）的一些最基本步骤。请记住，微调大语言模型需要大量的计算资源，您的本地计算机可能没有足够的计算能力来完成这项任务。

You can learn how to fine-tune more powerful LLMs directly on OpenAI’s interface following this tutorial about How to Fine-Tune GPT 3.5.

想知道如何在 OpenAI 的界面上微调更强大的大语言模型吗？学习这篇关于如何微调 GPT 3.5 的教程吧。

### 05. Fine-tuning Best Practices

微调最佳实践

To ensure successful fine-tuning, consider the following best practices:

为了更好地进行微调，请参考以下建议：

Data Quality and Quantity

数据质量和数量

The quality of your fine-tuning dataset significantly impacts the model's performance. We all know the sentence:

微调数据集的质量对模型性能有着至关重要的影响。正如我们常说的：

“Garbage In, Garbage Out”

So, always ensure the data is clean, relevant, and sufficiently large.

因此，务必保证数据的干净、相关和充足。

Hyperparameter tuning

超参数调整

Fine-tuning is usually a long process that needs to be iterated. Always explore various settings for learning rates, batch sizes, and the number of training epochs to identify the best setup for your project.

微调通常是一个需要反复尝试的耗时过程。持续探索学习率、批次大小和训练轮数（epoch）的各种组合，以便为您的项目找到最佳配置。

Precise adjustments are key to ensuring the model learns efficiently and adapts well to unseen data, avoiding the pitfall of overfitting.

细致的调整是确保模型高效学习并良好适应未知数据的关键，从而避免过拟合的风险。

Regular evaluation

定期评估

Regularly assess the model's progress during training to track its effectiveness and implement required modifications. This involves evaluating the model's performance using a distinct validation dataset throughout the training period.

在训练过程中，需要定期评估模型的进展，以此来跟踪模型的有效性并进行必要的调整。这包括在整个训练过程中，使用独立的验证数据集来评估模型的性能。通过验证数据集，我们可以了解模型在新数据上的表现，从而判断模型是否训练充分。

Such evaluation is critical for determining the model's performance of the task at hand and its potential for overfitting to the training dataset. Based on the outcomes from the validation phase, adjustments can be made as needed to optimize performance.

这样的评估对于确定模型在当前任务上的性能，以及其过度拟合（overfitting）训练数据的可能性至关重要。根据验证阶段的结果，可以进行必要的调整以优化性能。

### 06. Avoiding LLM Fine-Tuning Pitfalls

避免大语言模型（LLM）微调的陷阱

Fine-tuning can sometimes lead to suboptimal outcomes. Be wary of the following pitfalls:

微调有时会导致次优的结果。需要警惕以下陷阱：

Overfitting

过拟合（Overfitting)

Using a small dataset for training or extending the number of epochs excessively can produce overfitting. This is usually characterized by the model showing high accuracy on our training dataset but failing to generalize to new data.

使用小数据集进行训练或过度增加训练轮数（epoch）可能会导致过拟合。这通常表现为模型在训练数据集上准确率很高，但对新数据的泛化能力较差。

Underfitting

欠拟合

Conversely, insufficient training or a low learning rate can result in underfitting, where the model fails to learn the task adequately.

与过拟合相反，不充分的训练或过低的学习率可能导致欠拟合（Underfitting），模型无法充分学习给定的任务。

Catastrophic forgetting

灾难性遗忘（Catastrophic forgetting)

In the process of fine-tuning for a particular task, there's a risk that the model might lose the broad knowledge it initially acquired. This issue, referred as catastrophic forgetting, can diminish the model's ability to perform well across a variety of tasks using natural language processing.

在针对特定任务进行微调时，模型可能会遗忘其预训练阶段所获得的通用知识。这种现象被称为灾难性遗忘（Catastrophic forgetting），它会削弱模型在各种自然语言处理（Natural Language Processing）任务中的表现。

Data leakage

数据泄露

Always make sure that training and validation datasets are separate and that there's no overlap, as this can give misleading high-performance metrics.

务必确保训练数据集和验证数据集相互独立，避免数据重叠。否则，会导致模型性能评估出现偏差，产生虚假的高性能指标。

### 07. Fine-tuning vs. RAG

微调（Fine-tuning）与 RAG

RAG combines the strengths of retrieval-based models and generative models. In RAG, a retriever component searches a large database or knowledge base to find relevant information based on the input query. This retrieved information is then used by a generative model to produce a more accurate and contextually relevant response. Key benefits of RAG include:

RAG 融合了检索模型和生成模型的优点。在 RAG 中，检索器组件会根据输入的查询，搜索大型数据库或知识库，以找到相关信息。然后，生成式模型会利用这些检索到的信息，生成更准确、更符合上下文语境的回复。RAG 的主要优点包括：

1 Dynamic knowledge integration: Incorporates real-time information from external sources, making it suitable for tasks requiring up-to-date or specific knowledge.

动态知识整合：它能够整合来自外部来源的实时信息，因此非常适合需要最新信息或特定领域知识的任务。

2 Contextual relevance: Enhances the generative model’s responses by providing additional context from the retrieved documents.

上下文相关性：通过检索到的文档提供额外的上下文信息，从而改进生成模型的回复。

3 Versatility: Can handle a wider range of queries, including those requiring specific or rare information that the model may not have been trained on.
rag vs fine tuning

多功能性：能够处理范围更广的查询，包括那些需要模型可能没有训练过的特定或罕见信息的查询。

Choosing between fine-tuning and RAG

如何选择微调和 RAG

When deciding whether to use fine-tuning or RAG, consider the following factors:

在决定使用微调还是 RAG（Retrieval-Augmented Generation，检索增强生成）时，请考虑以下因素：

1 Nature of the task: For tasks that benefit from highly specialized models (e.g., domain-specific applications), fine-tuning is often the preferred approach. RAG is ideal for tasks that require integration of external knowledge or real-time information retrieval.

任务的性质：对于需要高度专业模型的任务（例如，特定领域的应用），微调通常是首选方法。RAG 非常适合需要集成外部知识或实时信息检索的任务。

2 Data availability: Fine-tuning requires a substantial amount of labeled data specific to the task. If such data is scarce, RAG’s retrieval component can compensate by providing relevant information from external sources.

数据的可用性：微调需要大量特定于任务的标注数据。如果此类数据稀缺，RAG 的检索组件可以通过提供来自外部来源的相关信息来弥补不足。

3 Resource constraints: Fine-tuning can be computationally intensive, whereas RAG leverages existing databases to supplement the generative model, potentially reducing the need for extensive training.

资源约束：微调需要大量的计算资源，而 RAG 利用现有的数据库来补充生成模型，从而可能减少对大量训练的需求。

### 08. Conclusion

总结

Embarking on the journey of fine-tuning large language models opens up a world of possibilities for AI applications.

微调大语言模型（LLM/Large Language Model）为 AI 应用开辟了新的可能性。

By understanding and applying the concepts, practices, and precautions outlined, one can effectively adapt these powerful models to meet specific needs, unlocking their full potential in the process.

通过理解并应用本文概述的概念、实践方法和注意事项，我们可以有效地调整这些强大的模型，以满足特定的需求，并在这一过程中充分释放它们的潜力。

To keep learning about fine-tuning, I strongly encourage you to perform some more advanced fine-tuning. You can start with DataCamp’s LLM Concepts course, which covers many of the key training methodologies and the latest research. Some other good resources to follow are:

为了更深入地掌握微调（fine-tuning）技术，我强烈推荐你尝试一些更高级的实践。不妨从 DataCamp 的 LLM Concepts 课程入手，它涵盖了众多核心训练方法和前沿研究成果。接下来，我还会为你列举一些同样优秀的学习资源：

[Large Language Models (LLMs) Concepts - DataCamp Learn](https://app.datacamp.com/learn/courses/large-language-models-llms-concepts)

[A Step-by-Step Guide to Using and Fine-Tuning Mistral 7B.](https://app.datacamp.com/learn/tutorials/mistral-7b-tutorial)

[Fine-Tuning LLaMA 2: A Step-by-Step Guide to Customizing the Large Language Model](https://app.datacamp.com/learn/tutorials/fine-tuning-llama-2)

[Fine-Tuning Your Own Llama 2 Model | DataCamp](https://www.datacamp.com/code-along/fine-tuning-your-own-llama-2-model)

[Fine-tuning Stable Diffusion XL with DreamBooth and LoRA](https://app.datacamp.com/learn/tutorials/fine-tuning-stable-diffusion-xl-with-dreambooth-and-lora)

### FAQs

Can fine-tuning be done with small datasets, and how does that impact model performance?

使用小数据集可以进行微调吗？这会如何影响模型性能？

Yes, fine-tuning can be performed with small datasets using techniques like few-shot learning or low-rank adaptation (LoRA), which optimize a subset of the model’s parameters. While this reduces computational costs, the model’s performance may depend heavily on the quality and representativeness of the small dataset.

是的，可以通过少样本学习（few-shot learning）或低秩适应（LoRA）等技术对小数据集进行微调，这些技术只需优化模型部分参数。虽然这种方法能够降低计算成本，但模型的最终表现很大程度上取决于所使用的小数据集的质量和代表性。

How can I prevent catastrophic forgetting during fine-tuning?

如何在微调过程中防止模型遗忘原有能力（灾难性遗忘，catastrophic forgetting）？

What are the hardware requirements for fine-tuning large language models?

微调大语言模型需要什么样的硬件配置？

profile picture of Josep Ferrer

Josep Ferrer

Freelance Data Scientist at NECSTouR

Josep is a freelance Data Scientist specializing in European projects, with expertise in data storage, processing, advanced analytics, and impactful data storytelling. 

As an educator, he teaches Big Data in the Master’s program at the University of Navarra and shares insights through articles on platforms like Medium, KDNuggets, and DataCamp. Josep also writes about Data and Tech in his newsletter Databites (databites.tech). 

He holds a BS in Engineering Physics from the Polytechnic University of Catalonia and an MS in Intelligent Interactive Systems from Pompeu Fabra University.

Josep Ferrer 的个人简介

NECSTouR 自由职业数据科学家

Josep 是一位专注于欧洲项目的自由职业数据科学家，擅长数据存储、数据处理、高级分析以及数据可视化叙事。

作为教育工作者，他在纳瓦拉大学（University of Navarra）硕士课程中讲授大数据课程，并在 Medium、KDNuggets 和 DataCamp 等平台分享专业见解。Josep 还通过其技术通讯 Databites（databites.tech）撰写数据科技相关文章。

他毕业于加泰罗尼亚理工大学（Polytechnic University of Catalonia），获得工程物理学士学位，并在庞培法布拉大学（Pompeu Fabra University）获得智能交互系统硕士学位。