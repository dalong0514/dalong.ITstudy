## 20250224Fine-tuning-large-language-models-LLMs-in-2024

[Fine-tuning large language models (LLMs) in 2024 | SuperAnnotate](https://www.superannotate.com/blog/llm-fine-tuning?utm_source=chatgpt.com)

It’s no secret that large language models (LLMs) are evolving at a wild speed and are turning heads in the generative AI industry. Enterprises aren't just intrigued; they're obsessed with LLMs, particularly with the potential of LLM fine-tuning. Billions of dollars have been poured into LLM research and development recently. Industry leaders and tech enthusiasts are showing a growing appetite to deepen their understanding of LLMs and their fine-tuning. While this frontier in natural language processing (NLP) keeps expanding more and more, staying informed is critical. The value LLMs may add to your business depends on your knowledge and intuition around this technology.

毋庸置疑，大语言模型（LLM）正以惊人的速度发展，成为生成式 AI（Generative AI）领域最受关注的技术之一。企业界对 LLM 表现出极大的兴趣，尤其是 LLM 微调的巨大潜力。近期，数十亿美元已投入到 LLM 的研发中。行业领袖和技术爱好者都希望更深入地了解 LLM 及其微调技术。在自然语言处理（NLP）领域，这一前沿技术正在快速发展，因此及时掌握相关信息至关重要。LLM 能否为您的业务带来价值，取决于您对这项技术的理解和认知。

A large language model life cycle has several key steps, and today we're going to cover one of the juiciest and most intensive parts of this cycle - the LLM fine-tuning process. This is a laborious, heavy, but rewarding task that's involved in many language model training processes.

大语言模型的生命周期包含多个关键步骤，今天我们将重点介绍其中一个最关键、也最具挑战性的环节：LLM 微调。这是一个需要投入大量精力，但回报也很高的过程，它存在于许多语言模型的训练过程中。

### 01. Large language model lifecycle

Before going over LLM fine-tuning, it's important to understand the LLM lifecycle and how it works.

大语言模型生命周期在深入了解 LLM 微调之前，我们首先需要了解 LLM 的完整生命周期及其运作方式。

1 Vision & scope: First, you should define the project's vision. Determine if your LLM will be a more universal tool or target a specific task like named entity recognition. Clear objectives save time and resources.

愿景与范围：首先，明确项目的目标。您的 LLM 是要成为一个通用工具，还是专注于命名实体识别等特定任务？明确的目标有助于节省时间和资源。

2 Model selection: Choose between training a model from scratch or modifying an existing one. In many cases, adapting a pre-existing model is efficient, but some instances require fine-tuning with a new model.

模型选择： 选择从头开始训练模型，还是在现有模型的基础上进行修改。通常，修改预训练模型效率更高，但在某些情况下，需要使用全新的模型进行微调。

3 Model's performance and adjustment: After preparing your model, you need to assess its performance. If it’s unsatisfactory, try prompt engineering or further fine-tuning. We'll focus on this part. Ensure the model's outputs are in sync with human preferences.

模型性能调整：准备好模型后，需要评估其性能。如果结果不理想，可以尝试提示工程或进一步的微调。我们将重点讨论这个环节，确保模型的输出能够满足人类的偏好。

4 Evaluation & iteration: Conduct evaluations regularly using metrics and benchmarks. Iterate between prompt engineering, fine-tuning, and LLM evaluation until you reach the desired outcomes.

评估与迭代：使用各种指标和基准定期评估模型。通过不断地提示工程、微调和 LLM 评估，最终达到预期的效果。

5 Deployment: Once the model performs as expected, deploy it. Optimize for computational efficiency and user experience at this juncture.

部署：一旦模型达到预期性能，就可以进行部署。在此阶段，需要优化计算效率和用户体验。

### 02. What is LLM fine-tuning?

什么是 LLM 微调？

Large language model (LLM) fine-tuning is the process of taking pre-trained models and further training them on smaller, specific datasets to refine their capabilities and improve performance in a particular task or domain. Fine-tuning is about turning general-purpose models and turning them into specialized models. It bridges the gap between generic pre-trained models and the unique requirements of specific applications, ensuring that the language model aligns closely with human expectations. Think of OpenAI's GPT-3, a state-of-the-art large language model designed for a broad range of natural language processing (NLP) tasks. Suppose a healthcare organization wants to use GPT-3 to assist doctors in generating patient reports from textual notes. While GPT-3 can understand and create general text, it might not be optimized for intricate medical terms and specific healthcare jargon.

大语言模型（LLM）微调是指，在预训练模型的基础上，使用更小、更具体的数据集对其进行进一步训练，从而提升模型在特定任务或领域的性能。简单来说，微调就是将通用模型转化为专用模型的过程。它弥补了通用预训练模型与特定应用场景需求之间的差距，确保语言模型更贴合人类的期望。以 OpenAI 的 GPT-3 为例，这是一种先进的大语言模型，可以处理各种自然语言处理（NLP）任务。假设一家医疗机构希望利用 GPT-3 帮助医生从病例文档中生成患者报告。虽然 GPT-3 能够理解并生成一般的文本内容，但它可能不擅长处理复杂的医学术语和特定的医疗行业术语。

To enhance its performance for this specialized role, the organization fine-tunes GPT-3 on a dataset filled with medical reports and patient notes. It might use tools like SuperAnnotate's LLM custom editor to build its own model with the desired interface. Through this process, the model becomes more familiar with medical terminologies, the nuances of clinical language, and typical report structures. After fine-tuning, GPT-3 is primed to assist doctors in generating accurate and coherent patient reports, demonstrating its adaptability for specific tasks.

为了提升 GPT-3 在这项特定任务中的表现，这家医疗机构可以使用包含大量医疗报告和病例文档的数据集，对 GPT-3 进行微调。他们还可以使用 SuperAnnotate 的 LLM 自定义编辑器等工具，构建具有特定界面的模型。通过这个过程，模型可以更好地理解医学术语、临床语言的细微差别以及典型的报告结构。经过微调后，GPT-3 就能更好地协助医生生成准确、连贯的患者报告，充分展现了其在特定任务中的适应性。

This sounds great to have in every large language model, but remember that everything comes with a cost. We'll discuss that in more detail soon.

在每个大语言模型中都应用微调技术听起来很棒，但请记住，任何技术都有其成本。我们将在后续内容中更详细地讨论这一点。

### 03. When to use fine-tuning

Our article about large language models touches upon topics like in-context learning and zero/one/few shot inference. Here’s a  quick recap:

何时使用微调在之前关于大语言模型的文章中，我们曾介绍过上下文学习、零样本 / 少样本推理等概念。这里我们快速回顾一下：

1 In-context learning is a method for improving the prompt through specific task examples within the prompt, offering the LLM a blueprint of what it needs to accomplish.

上下文学习是一种通过在提示中提供特定任务的示例来优化提示的方法，相当于为 LLM 提供了一份完成任务的「蓝图」。

2 Zero-shot inference incorporates your input data in the prompt without extra examples. If zero-shot inference doesn't yield the desired results, 'one-shot' or 'few-shot inference' can be used. These tactics involve adding one or multiple completed examples within the prompt, helping smaller LLMs perform better.

零样本推理指的是在提示中直接使用输入数据，而不提供任何额外的示例。如果零样本推理的效果不理想，可以尝试「单样本」或「少样本推理」。这些方法需要在提示中添加一到多个已完成的示例，以帮助较小的 LLM 更好地完成任务。

These are techniques used directly in the user prompt and aim to optimize the model's output and better fit it to the user's preferences. The problem is that they don’t always work, especially for smaller LLMs. Here's an example of how in-context learning may fail.

以上这些技术都是直接在用户提示中使用的，旨在优化模型的输出，使其更好地满足用户的需求。但问题在于，这些方法并非总是有效，尤其是对于较小的 LLM 而言。下面是一个上下文学习可能失效的例子。

Other than that, any examples you include in your prompt take up valuable space in the context window, reducing the space you have to include additional helpful information. And here, finally, comes fine-tuning. Unlike the pre-training phase, with vast amounts of unstructured text data, fine-tuning is a supervised learning process. This means that you use a dataset of labeled examples to update the weights of LLM. These labeled examples are usually prompt-response pairs, resulting in a better completion of specific tasks.

此外，提示中包含的任何示例都会占用宝贵的上下文窗口空间，减少了用于提供其他有用信息的空间。这时，微调就派上了用场。与预训练阶段使用的大量非结构化文本数据不同，微调是一种监督学习过程。也就是说，你需要使用带有标签的示例数据集来更新 LLM 的权重。这些带标签的示例通常是「提示 - 响应」对，可以帮助模型更好地完成特定任务。

### 04. Supervised fine-tuning (SFT)

监督微调（SFT)

Supervised fine-tuning means updating a pre-trained language model using labeled data to do a specific task. The data used has been checked earlier. This is different from unsupervised methods, where data isn't checked. Usually, the initial training of the language model is unsupervised, but fine-tuning is supervised.

监督微调（Supervised Fine-Tuning，SFT）指的是，使用带有标签的数据来更新预训练语言模型，使其能够更好地执行特定任务。这里使用的数据都需要经过预先审核。这与非监督学习方法不同，在非监督学习方法中，数据未经审核。通常，语言模型的初始训练是非监督的，而微调则是有监督的。

#### How is fine-tuning performed?

如何进行微调？

Let's get into more details of fine-tuning in LLMs. For preparing the training data, there are many open-source datasets that offer insights into user behaviors and preferences, even if they aren't directly formatted as instructional data. For example, we can take the large data set of Amazon product reviews and turn them into instruction prompt datasets for fine-tuning. Prompt template libraries include many templates for different tasks and different datasets.

让我们更深入地了解 LLM 的微调过程。在准备训练数据时，有很多开源数据集可以提供关于用户行为和偏好的信息，即使这些数据并非直接以教学数据的形式呈现。举例来说，我们可以将 Amazon 产品评论的大型数据集转换为指令提示数据集，用于微调。提示模板库中包含许多适用于不同任务和数据集的模板。

Once your instruction data set is ready, as with standard supervised learning, you divide the data set into training validation and test splits. During fine-tuning, you select prompts from your training data set and pass them to the LLM, which then generates completions.

准备好指令数据集后，就像标准的监督学习一样，你需要将数据集划分为训练集、验证集和测试集。在微调过程中，你可以从训练集中选择提示，并将其传递给 LLM，然后 LLM 会生成相应的补全内容。

During the fine-tuning phase, when the model is exposed to a newly labeled dataset specific to the target task, it calculates the error or difference between its predictions and the actual labels. The model then uses this error to adjust its weights, typically via an optimization algorithm like gradient descent. The magnitude and direction of weight adjustments depend on the gradients, which indicate how much each weight contributed to the error. Weights that are more responsible for the error are adjusted more, while those less responsible are adjusted less.

在微调阶段，当模型接触到特定于目标任务的新标记数据集时，它会计算其预测结果与实际标签之间的误差或差异。然后，模型会利用这个误差来调整其权重，调整方法通常是使用梯度下降等优化算法。权重调整的幅度和方向取决于梯度，梯度表示每个权重对误差的贡献程度。对误差影响较大的权重会进行更大的调整，而影响较小的权重则会进行较小的调整。

Over multiple iterations (or epochs) of the dataset, the model continues to adjust its weights, honing in on a configuration that minimizes the error for the specific task. The aim is to adapt the previously learned general knowledge to the nuances and specific patterns present in the new dataset, thereby making the model more specialized and effective for the target task.

通过对数据集进行多次迭代（epoch），模型不断调整其权重，最终确定一个能够最大限度地减少特定任务误差的配置。这样做的目的是使先前学习到的通用知识适应新数据集中存在的细微差别和特定模式，从而使模型对于目标任务更加专业和有效。

During this process, the model is updated with the labeled data. It changes based on the difference between its guesses and the actual answers. This helps the model learn details found in the labeled data. By doing this, the model improves at the task for which it's fine-tuned.

在这个过程中，模型会不断地用带有标签的数据进行更新，并根据其预测与实际答案之间的差异进行调整。这有助于模型学习标记数据中包含的细节，从而提升模型在微调任务中的表现。

Let's take an example to picture this better; if you ask a pre-trained model,"Why is the sky blue?" it might reply, "Because of the way the atmosphere scatters sunlight." This answer is simple and direct. However, the answer might be too brief for a chatbot for a science educational platform. It may need more scientific detail or context based on your guidelines. This is where supervised fine-tuning helps.

为了方便大家更好地理解，我们来看一个例子：如果你问一个预训练模型：「天空为什么是蓝色的？」，它可能会回答：「因为大气散射阳光的方式」。这个答案简洁明了，但对于科学教育平台的聊天机器人来说，可能过于简单。也许它需要根据你的要求，提供更科学的细节或背景信息。这就是监督微调的用武之地。

After fine-tuning, the model can give a more in-depth response to scientific questions. After fine-tuning, when asked, "Why is the sky blue?", the model might provide a more detailed explanation like:

经过微调后，模型可以对科学问题给出更深入的回答。比如，在经过微调后，当被问到「天空为什么是蓝色的？」时，模型可能会给出更详细的解释：

"The sky appears blue because of a phenomenon called Rayleigh scattering. As sunlight enters Earth's atmosphere, it consists of different colors, each with its own wavelength. Blue light has a shorter wavelength and is scattered in all directions by the gases and particles in the atmosphere. This scattering causes the direct sunlight to appear white, but the sky itself to take on a blue hue." This enriched response is comprehensive and suitable for a science educational platform.

「天空呈现蓝色是由于一种叫做瑞利散射的现象。当阳光进入地球大气层时，它由不同的颜色组成，每种颜色都有其自身的波长。蓝光的波长较短，会被大气中的气体和颗粒向各个方向散射。这种散射导致直射阳光看起来是白色的，但天空本身则呈现蓝色。」这种更丰富的回答更加全面，更适合科学教育平台。

### 05. Methods for fine-tuning LLMs

LLM 微调方法

LLM fine-tuning is a supervised learning process where you use a dataset of labeled examples to update the weights of LLM and make the model improve its ability for specific tasks. Let's explore some of the notable methods for fine-tuning LLMs and LLM agents.

LLM 微调是一种监督学习过程，你可以使用带有标签的示例数据集来更新 LLM 的权重，从而提高模型在特定任务中的能力。接下来，我们将介绍一些用于微调 LLM 和 AI 智能体的常用方法。

#### Instruction fine-tuning

指令微调

One strategy used to improve a model's performance on various tasks is instruction fine-tuning. It's about training the machine learning model using examples that demonstrate how the model should respond to the query. The dataset you use for fine-tuning large language models has to serve the purpose of your instruction. For example, suppose you fine-tune your model to improve its summarization skills. In that case, you should build up a dataset of examples that begin with the instruction to summarize, followed by text or a similar phrase. In the case of translation, you should include instructions like “translate this text.” These prompt completion pairs allow your model to "think" in a new niche way and serve the given specific task.

指令微调是一种通过示例来训练机器学习模型，使其学习如何响应查询的方法。用于微调大语言模型的数据集必须能够服务于你的指令。举例来说，如果你希望通过微调来提高模型的摘要能力，那么你应该创建一个示例数据集，其中的每个示例都以「请总结以下内容」这样的指令开头，后跟需要总结的文本。如果是翻译任务，则应该包含「翻译这段文字」之类的指令。这些「提示 - 补全」对可以帮助你的模型以一种新的方式「思考」，并更好地完成指定的任务。

#### Full fine-tuning

完全微调

Instruction fine-tuning, where all of the model's weights are updated, is known as full fine-tuning. The process results in a new version of the model with updated weights. It is important to note that just like pre-training, full fine-tuning requires enough memory and compute budget to store and process all the gradients, optimizers, and other components being updated during training.

指令微调中，如果模型的所有权重都得到更新，则被称为完全微调（Full Fine-Tuning）。这个过程会生成一个具有更新权重的全新模型版本。需要注意的是，与预训练一样，完全微调需要足够的内存和计算资源来存储和处理在训练期间更新的所有梯度、优化器和其他组件。

#### Parameter-efficient fine-tuning

参数高效微调

Training a language model is a computationally intensive task. For a full LLM fine-tuning, you need memory not only to store the model, but also the parameters that are necessary for the training process. Your computer might be able to handle the model weights, but allocating memory for optimizing states, gradients, and forward activations during the training process is a challenging task. Simple hardware cannot handle this amount of hurdle. This is where PEFT is crucial. While full LLM fine-tuning updates every model's weight during the supervised learning process, PEFT methods only update a small set of parameters. This transfer learning technique chooses specific model components and "freezes" the rest of the parameters. The result is logically having a much smaller number of parameters than in the original model (in some cases, just 15-20% of the original weights; LoRA can reduce the number of trainable parameters by 10,000 times). This makes memory requirements much more manageable. Not only that, but PEFT is also dealing with catastrophic forgetting. Since it's not touching the original LLM, the model does not forget the previously learned information. Full fine-tuning results in a new version of the model for every task you train on. Each of these is the same size as the original model, so it can create an expensive storage problem if you're fine-tuning for multiple tasks.

训练语言模型是一项计算密集型任务。对于完全 LLM 微调，你不仅需要内存来存储模型本身，还需要存储训练过程中必需的各种参数。你的计算机可能能够处理模型权重，但在训练过程中为优化状态、梯度和前向激活分配内存则是一项极具挑战性的任务。简单的硬件配置很难满足这种需求。这就是参数高效微调（Parameter-Efficient Fine-Tuning，PEFT）变得至关重要的原因。尽管完全 LLM 微调需要在监督学习过程中更新模型的每个权重，但 PEFT 方法仅更新一小部分参数。这种迁移学习技术会选择特定的模型组件，并「冻结」其余的参数。这样做的结果是，参数数量会比原始模型少得多（在某些情况下，只有原始权重的 15-20%；LoRA 可以将可训练参数的数量减少 10,000 倍）。这大大降低了内存需求。更重要的是，PEFT 还能有效应对灾难性遗忘问题。由于它不会触及原始 LLM，因此模型不会忘记先前学到的信息。完全微调会为每个训练任务生成一个新版本的模型。这些模型的大小与原始模型相同，因此，如果你需要为多个任务进行微调，可能会面临高昂的存储成本。

#### Other types of fine-tuning

其他微调方法

Let's learn a few more types of learning:

下面我们再来了解几种其他的微调方法：

Transfer learning: Transfer learning is about taking the model that had learned on general-purpose, massive datasets and training it on distinct, task-specific data. This dataset may include labeled examples related to that domain. Transfer learning is used when there is not enough data or a lack of time to train data; the main advantage of it is that it offers a higher learning rate and accuracy after training. You can take existing LLMs that are pre-trained on vast amounts of data, like GPT ¾ and BERT, and customize them for your own use case.

迁移学习：迁移学习指的是，利用在通用的大规模数据集上训练过的模型，并在不同的、特定任务的数据上进行训练。这种数据集可能包含与该领域相关的带标签示例。当数据量不足或训练时间有限时，可以使用迁移学习。它的主要优点是，在训练后可以实现更高的学习速率和准确性。你可以直接使用在海量数据上预训练的现有 LLM，例如 GPT-3 和 BERT，并根据自己的用例进行定制。

Task-specific fine-tuning: Task-specific fine-tuning is a method where the pre-trained model is fine-tuned on a specific task or domain using a dataset designed for that domain. This method requires more data and time than transfer learning but can result in higher performance on the specific task.

特定于任务的微调：特定于任务的微调是一种方法，即使用专门为特定任务或领域设计的数据集，对预训练模型进行微调。相比于迁移学习，这种方法需要更多的数据和时间，但可以在特定任务上实现更高的性能。

For example, translation using a dataset of examples for that task. Interestingly, good results can be achieved with relatively few examples. Often, just a few hundred or thousand examples can result in good performance compared to the billions of pieces of text that the model saw during its pre-training phase. However, there is a potential downside to fine-tuning on a single task. The process may lead to a phenomenon called catastrophic forgetting.

例如，使用某个翻译任务的示例数据集进行翻译。值得一提的是，即使只使用相对较少的示例，也能取得不错的效果。通常情况下，只需要几百或几千个示例，就能达到很好的性能，而模型在预训练阶段需要学习数十亿条文本。然而，针对单个任务进行微调也存在一个潜在的缺点：可能会导致灾难性遗忘现象。

Catastrophic forgetting happens because the full fine-tuning process modifies the weights of the original LLM. While this leads to great performance on a single fine-tuning task, it can degrade performance on other tasks. For example, while fine-tuning can improve the ability of a model to perform certain natural language processing (NLP) tasks like sentiment analysis and result in  quality completion, the model may forget how to do other tasks. This model knew how to carry out named entity recognition before fine-tuning correctly identifying.

发生灾难性遗忘的原因是，完全微调过程会修改原始 LLM 的权重。尽管这可以在单个微调任务上实现出色的性能，但可能会降低模型在其他任务上的表现。例如，虽然微调可以提高模型执行情感分析等某些自然语言处理（NLP）任务的能力，并生成高质量的补全内容，但模型可能会忘记如何执行其他任务，比如正确识别命名实体 —— 这是模型在微调之前已经掌握的技能。

Multi-task learning: Multi-task fine-tuning is an extension of single-task fine-tuning, where the training dataset consists of example inputs and outputs for multiple tasks. Here, the dataset contains examples that instruct the model to carry out a variety of tasks, including summarization, review rating, code translation, and entity recognition. You train the model on this mixed dataset so that it can improve the performance of the model on all the tasks simultaneously, thus avoiding the issue of catastrophic forgetting. Over many epochs of training, the calculated losses across examples are used to update the weights of the model, resulting in a fine-tuned model that knows how to be good at many different tasks simultaneously. One drawback of multi-task fine-tuned models is that they require a lot of data. You may need as many as 50-100,000 examples in your training set. However, assembling this data can be really worthwhile and worth the effort. The resulting models are often very capable and suitable for use in situations where good performance at many tasks is desirable.

多任务学习：多任务微调是单任务微调的扩展。在多任务微调中，训练数据集包含多个任务的输入和输出示例。也就是说，数据集包含指导模型执行各种任务的示例，包括摘要、评论评级、代码翻译和实体识别等。你可以在这种混合数据集上训练模型，使其能够同时提高在所有任务上的性能，从而避免灾难性遗忘的问题。多任务微调模型的一个缺点是，它们需要大量的数据。你的训练集中可能需要 5 万到 10 万个示例。但是，收集这些数据是非常值得的。训练得到的模型通常非常强大，适用于需要在多个任务上实现良好性能的场景。

Sequential fine-tuning: Sequential fine-tuning is about sequentially adapting a pre-trained model on several related tasks. After the initial transfer to a general domain, the LLM might be fine-tuned on a more specific subset. For instance, it can be fine-tuned from general language to medical language and then from medical language to pediatric cardiology.

顺序微调：顺序微调指的是，按照一定的顺序，在多个相关的任务上调整预训练模型。在最初迁移到通用领域之后，LLM 可能会在一个更具体的子集上进行微调。例如，它可以先从通用语言微调到医学语言，然后再从医学语言微调到儿科心脏病学。

Note that there are other fine-tuning examples – adaptive, behavioral, and instruction, reinforced fine-tuning of large language models. These cover some important specific cases for training language models.

需要注意的是，还有其他一些微调方法，例如自适应微调、行为微调、指令微调以及大型语言模型的强化微调。这些方法涵盖了训练语言模型的一些重要的特定情况。

Fine-tuning approaches are now also being widely adapted for small language models (SLMs), which have become one of the biggest GenAI trends of 2024. Fine-tuning a small language model is actually a lot handier and easier to implement, especially if you’re a small business or a developer looking to improve your model's performance.

### 06. Retrieval augmented generation (RAG)

Retrieval augmented generation（RAG）is a well-known alternative to fine-tuning and is a combination of natural language generation and information retrieval. RAG ensures that language models are grounded by external up-to-date knowledge sources/relevant documents and provides sources. This technique bridges the gap between general-purpose models' vast knowledge and the need for precise，up-to-date information with rich context. Thus，RAG is an essential technique for situations where facts can evolve over time. Grok，the recent invention of xAI，uses RAG techniques to ensure its information is fresh and current.

检索增强生成（Retrieval augmented generation，RAG）是一种广为人知的微调替代方案，它结合了自然语言生成与信息检索技术。RAG 能够确保语言模型基于最新的外部知识来源和相关文档，并提供相应的出处。这项技术弥补了通用模型（general-purpose models）庞大知识库与对富含上下文、精确且及时信息的需求之间的鸿沟。因此，在事实信息随时间演变的应用场景中，RAG 是一项至关重要的技术。xAI 近期推出的 Grok 就采用了 RAG 技术，以保证其信息的时效性和新鲜度。

One advantage that RAG has over fine-tuning is information management. Traditional fine-tuning embeds data into the model's architecture，essentially 'hardwriting' the knowledge，which prevents easy modification. On the other hand，RAG permits continuous updates in training data and allows removal/revision of data，ensuring the model remains current and accurate.

RAG 相比于微调，其优势之一在于信息管理。传统的微调方法将数据嵌入到模型的架构中，本质上是「硬编码」知识，这使得修改变得困难。另一方面，RAG 允许持续更新训练数据，并能够删除或修订数据，从而确保模型能够保持最新和准确。

In the context of language models，RAG and fine-tuning are often perceived as competing methods. However，their combined use can lead to significantly enhanced performance. Particularly，fine-tuning can be applied to RAG systems to identify and improve their weaker components，helping them excel at specific LLM tasks.

在语言模型的背景下，RAG（Retrieval-Augmented Generation，检索增强生成）和微调（fine-tuning）经常被认为是相互竞争的方法。然而，它们的结合使用可以带来显著增强的性能。特别地，微调可以应用于 RAG 系统，以识别和改进其薄弱环节，帮助它们在特定的 LLM（Large Language Model，大语言模型）任务中表现出色。

### 07. Fine-tuning in SuperAnnotate

在 SuperAnnotate 中进行微调

Choosing the right tool means ensuring your AI understands exactly what you need，which can save you time，money，and protect your reputation. Look at the Air Canada situation，for example. Their AI chatbot hallucinated and gave a customer incorrect information，misleading him into buying full-price ticket. While we can't pin it down to fine-tuning for sure，it's likely that better fine-tuning might have avoided the problem. This just shows how crucial it is to pick a fine-tuning tool that ensures your AI works just right. It's precisely situations like these where SuperAnnotate steps in to make a difference.

选择合适的工具，意味着确保你的 AI 能够准确理解你的需求。这能帮你节省时间、金钱，并保护你的声誉。加拿大航空的案例就是一个警示。他们的 AI 聊天机器人出现了「幻觉」，向顾客提供了错误信息，导致顾客购买了全价机票。虽然我们无法确定这完全是微调的问题，但更好的微调很可能可以避免这种情况发生。这也突显了选择合适的微调工具，确保 AI 正常工作的重要性。SuperAnnotate 能够帮助你避免类似的问题。

SuperAnnotate's LLM tool provides a cutting-edge approach for designing optimal training data to fine-tune language models. Enterprises building AI solutions，like Databricks，choose SuperAnnotate to help them build training data.

SuperAnnotate 的大语言模型工具为优化训练数据提供了一种先进的方法，这些训练数据用于微调语言模型。像 Databricks 这样构建人工智能解决方案的企业，会选择 SuperAnnotate 来助力其训练数据的构建。

Jonathan Frankle from Databricks shares why they chose us：'We reviewed several companies in this space and selected SuperAnnotate due to the high quality of their data. I'm very glad we did – they continue to stand out for their data quality，attention to detail，and fantastic communication. They are an invaluable part of our data pipeline. I don't see them as a vendor，I see them as a partner.'

Databricks 的 Jonathan Frankle 分享了他们选择我们的原因：「我们考察了该领域的几家公司，最终选择 SuperAnnotate 是因为他们的数据质量非常出色。我很高兴我们做了这个选择 —— SuperAnnotate 在数据质量、对细节的关注以及良好的沟通方面一直表现突出。他们是我们数据流程中不可或缺的一环。我认为他们不仅仅是供应商，更是我们的合作伙伴。」

Through SuperAnnotate's highly customizable LLM editor，users are given a comprehensive platform to create a broad spectrum of LLM use cases that fit their business needs. As a result，customers can ensure that their training data is not only high-quality but also directly aligned with the requirements of their projects.

借助 SuperAnnotate 高度定制化的大语言模型（LLM）编辑器，用户可以获得一个功能全面的平台，从而创建各种符合自身业务需求的大语言模型（LLM）应用场景。这样一来，客户不仅可以确保训练数据的高质量，还能保证这些数据与项目需求精准匹配。

SuperAnnotate's LLM tool provides a cutting-edge approach to designing optimal training data for fine-tuning language models. Through its highly customizable LLM editor，users are given a comprehensive platform to create a broad spectrum of LLM use cases tailored to specific business needs. As a result，customers can ensure that their training data is not only high-quality but also directly aligned with the requirements of their projects.

SuperAnnotate 的大语言模型（LLM）工具提供了一种前沿方法，旨在为微调语言模型设计最佳的训练数据。借助其高度可定制的 LLM 编辑器，用户能够获得一个功能全面的平台，根据特定的业务需求创建各种 LLM 用例。最终，客户可以确保其训练数据不仅质量上乘，而且能够直接满足项目的需求。

Here's what you need to know about SuperAnnotate's LLM fine-tuning tool:

关于 SuperAnnotate 的大语言模型（LLM/Large Language Model）微调工具，你需要了解以下几点：

1 Its fully customizable interface allows you to gather data for your specific use case efficiently. Even if it's unique.

它拥有完全可定制的界面，能够高效地收集针对特定用例的数据。即使你的需求非常独特。

2 We work with a world-class team of experts and people management，which makes it a breeze to scale to hundreds or thousands of people.

我们拥有一支世界一流的专家和人才管理团队，这使得我们可以轻松扩展到数百甚至数千人的规模。

3 The analytics and insights of our platform are invaluable gems for our customers. It allows a better understanding of the data and enforces quality standards.

我们平台的分析能力和深刻洞察对客户而言是极其宝贵的。它有助于更好地理解数据，并提升质量标准。

4 API integrations make it easy to set up a model in the loop，AI feedback and much more.

API 集成使得在回路（in the loop）中配置模型、获取 AI 反馈等操作变得简单。

The tool has practical applications in various areas. It can handle tasks like chat rating，RLHF，or model comparison（as seen in the video），and many more. More here means you can use the customizable tool to build your own use case. It also supports multimodal cases，allowing you to work with text，images，audio，video，and PDFs—whatever your project needs.  These features ensure you can address real-world needs in the Gen AI and LLM market.

该工具在多个领域都具有实际应用价值。它可以处理诸如聊天内容质量评估、基于人类反馈的强化学习（RLHF）或模型对比（如视频中所示）等任务，并且能够支持更多应用场景。这里的「更多」指的是您可以使用这种可定制的工具来构建满足自身需求的用例。此外，该工具还支持多模态应用，允许您处理文本、图像、音频、视频和 PDF 等多种数据类型，以满足各种项目的需求。这些特性确保了您能够在生成式 AI（Gen AI）和大语言模型（LLM）领域解决实际问题。

Annotated question-response pairs(example in the image below）are sets of data where you have a question，the model's response，and annotations that provide insight into the quality，accuracy，or other attributes of that response. This somehow structured data is immensely valuable when training and fine-tuning models，as it offers direct feedback on the model's performance.

带注释的问答对（Annotated question-response pairs，如下图所示）是一种数据集，它包含一个问题、模型针对该问题的回答，以及针对该回答的注释。这些注释提供了关于回答的质量、准确性等属性的深入见解。这种结构化的数据在训练和微调模型时具有极高的价值，因为它能够提供关于模型性能的直接反馈。

In terms of data collection，SuperAnnotate allows you to gather annotated question-response pairs. These can be downloaded in a JSON format，making it easy to store and use them for future fine-tuning tasks. Overall，it's a user-friendly tool that streamlines and enhances the LLM training process.

在数据收集方面，SuperAnnotate 允许你收集带有标注的问题和答案配对数据。这些数据可以以 JSON 格式下载，方便存储并在未来用于微调任务。总而言之，它是一款用户友好的工具，能够简化和增强大语言模型（Large Language Model）的训练过程。

### 08. Fine-tuning best practices

微调实用指南

Clearly define your task:

明确任务定义：

Defining your task is a foundational step in the process of fine-tuning large language models. A clearly defined task offers focus and direction. It ensures that the model's vast capabilities are channeled towards achieving a specific goal，setting clear benchmarks for performance measurement.

定义任务是微调大语言模型（LLM）过程中的一个基础步骤。一个定义清晰的任务能够提供明确的焦点和方向。它确保模型强大的能力被引导至特定的目标，并为性能评估设定明确的基准。

Choose and use the right pre-trained model:

选择并使用正确的预训练模型：

Using pre-trained models for fine-tuning large language models is crucial because it leverages knowledge acquired from vast amounts of data，ensuring that the model doesn't start learning from scratch. This approach is both computationally efficient and time-saving. Additionally，pre-training captures general language understanding，allowing fine-tuning to focus on domain-specific nuances，often resulting in better model performance in specialized tasks.

使用预训练模型来微调大语言模型至关重要，因为它可以利用从海量数据中学习到的知识，避免模型从零开始训练。这种方法既能节省算力，又能节省时间。此外，预训练过程使模型获得了通用的语言理解能力，从而使微调过程可以专注于特定领域的细节，这通常能提升模型在特定任务中的性能。

While leveraging pre-trained models provides a robust starting point，the choice of model architecture — including advanced strategies like Mixture of Experts（MoE）and Mixture of Tokens（MoT）— is crucial in tailoring your model more effectively. These strategies can significantly influence how the model handles specialized tasks and processes language data.

虽然利用预训练模型能提供一个坚实的基础，但模型架构的选择，特别是像专家混合（Mixture of Experts，MoE）和 Token 混合（Mixture of Tokens，MoT）这样的高级策略，对于更有效地优化模型至关重要。这些策略能够显著影响模型处理特定任务和语言信息的方式。

Set hyperparameters:

设置超参数：

Hyperparameters are tunable variables that play a key role in the model training process. Learning rate，batch size，number of epochs，weight decay，and other parameters are the key hyperparameters to adjust that find the optimal configuration for your task.

超参数是在模型训练过程中起关键作用的可调变量。学习率、批次大小、周期数、权重衰减以及其他参数，都是需要调整的关键超参数，以便为您的任务找到最佳配置。

Evaluate model performance:

评估模型性能：

Once fine-tuning is complete，the model's performance is assessed on the test set. This provides an unbiased evaluation of how well the model is expected to perform on unseen data. Consider also iteratively refining the model if it still has potential for improvement.

微调完成后，我们需要在测试集上评估模型的性能。这能客观地评估模型在面对新数据时的表现。如果模型还有提升空间，可以考虑继续迭代优化。

### 09. Why or when does your business need a fine-tuned model?

为什么你的企业需要，或者在什么情况下需要一个精调模型？

We know that Chat GPT and other language models have answers to a huge range of questions. But the thing is that individuals and companies want to get their own LLM interface for their private and proprietary data. This is the new hot topic in tech town – large language models for enterprises.

我们都知道，像 Chat GPT 这样的大语言模型（LLM/Large Language Model）能够解答各式各样的问题。然而，许多个人和公司都希望能拥有一个专属于自己，能处理私有和专有数据的 LLM 交互界面。这也正是当前科技领域最受关注的焦点之一 —— 企业级大语言模型。

Here are a few reasons why you might need LLM fine-tuning.

以下列出了一些你可能需要对大语言模型（LLM/Large Language Model）进行微调的原因：

1 Specificity and relevance：While LLMs are trained on vast amounts of data，they might not be acquainted with the specific terminologies，nuances，or contexts relevant to a particular business or industry. Fine-tuning ensures the model understands and generates content that's highly relevant to the business.

更强的针对性和相关性：尽管大语言模型通过海量数据进行训练，但它们可能不熟悉特定业务或行业的术语、细微差别或相关背景。微调可以确保模型能够理解并生成与你的业务高度相关的内容。

2 Improved accuracy：For critical business functions，the margin for error is slim. Fine-tuning business-specific data can help achieve higher accuracy levels，ensuring the model's outputs align closely with expectations.

提高准确性：对于关键的业务功能而言，几乎没有犯错的空间。通过微调特定业务的数据（business-specific data），可以帮助模型达到更高的准确率，确保模型的输出与预期严丝合缝。

3 Customized interactions：If you're using LLMs for customer interactions，like chatbots，fine-tuning helps tailor responses to match your brand's voice，tone，and guidelines. This ensures a consistent and branded user experience.

定制化交互：如果你正在使用大语言模型（LLMs）来进行客户互动，比如聊天机器人，那么微调（fine-tuning）可以帮助你调整大语言模型的回复，让其更好地匹配你品牌的风格、语调和规范。这样可以确保用户获得一致且具有品牌特色的体验。

4 Data privacy and security：General LLMs might generate outputs based on publicly available data. Fine-tuning allows businesses to control the data the model is exposed to，ensuring that the generated content doesn't inadvertently leak sensitive information.

数据隐私和安全：通用大语言模型（LLM）生成的内容可能来源于公开数据。通过微调（Fine-tuning），企业可以控制模型所使用的数据来源， 从而避免生成的内容意外泄露敏感信息。

5 Addressing rare scenarios：Every business encounters rare but crucial scenarios specific to its domain. A general LLM might not handle such cases optimally. Fine-tuning ensures that these edge cases are catered to effectively.

应对罕见场景：每个企业都会遇到一些特定于其领域的、罕见但至关重要的场景。通用大语言模型（LLM/Large Language Model）在处理这些情况时可能并非最佳。通过微调，可以确保有效地解决这些极端情况。

While LLMs offer broad capabilities，fine-tuning sharpens those capabilities to fit the unique contours of a business's needs，ensuring optimal performance and results.

虽然大语言模型（LLM）提供了广泛的能力，但通过微调（fine-tuning）可以针对企业独特的业务需求，优化这些能力，从而确保最佳的性能和结果。

To fine-tune or not to fine-tune?

要不要微调？

Sometimes，fine-tuning is not the best option. Here's an image from #OpenAIDevDay – fine-tuning on 140k internal Slack messages.

有时候，微调并非最佳选择。这是 #OpenAIDevDay 上的一张图片 —— 基于 14 万条内部 Slack 消息进行的微调。

User："Write a 500 word blog post on prompt engineering"

Assistant："Sure，I shall work on that in the morning"

User："Write it now"

Assistant："ok"

### 10. Key takeaways

关键要点

LLM fine-tuning has become an indispensable tool in the LLM requirements of enterprises to enhance their operational processes. While the foundational training of LLMs offers a broad understanding of language，it's the fine-tuning process that molds these models into specialized tools capable of understanding niche topics and delivering more precise results. By training LLMs for specific tasks，industries，or data sets，we are pushing the boundaries of what these models can achieve and ensuring they remain relevant and valuable in an ever-evolving digital landscape. As we look ahead，the continuous exploration and innovation in LLM and the right tools for fine-tuning methodologies will undoubtedly pave the way for smarter，more efficient，and contextually aware AI systems.

为了满足企业的大语言模型（LLM）需求，微调已经成为不可或缺的工具，它可以有效提升运营效率。尽管大语言模型的基础训练使其对语言拥有广泛的理解，但微调过程能将这些模型打造成更专业的工具，使其能够理解特定领域的专业知识并提供更精确的结果。通过针对特定任务、行业或数据集训练大语言模型，我们不断突破这些模型的能力上限，并确保它们在快速发展的数字环境中保持其价值和实用性。展望未来，对大语言模型及其微调方法相关工具的持续探索和创新，无疑将为更智能、更高效、以及具有更强上下文理解能力的 AI 系统铺平道路。