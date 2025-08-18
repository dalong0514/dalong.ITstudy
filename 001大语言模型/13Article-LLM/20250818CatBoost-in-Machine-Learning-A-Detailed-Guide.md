## 20250818CatBoost-in-Machine-Learning-A-Detailed-Guide

[CatBoost in Machine Learning: A Detailed Guide | DataCamp](https://www.datacamp.com/tutorial/catboost?utm_source=chatgpt.com)

CatBoost in Machine Learning: A Detailed Guide

机器学习中的 CatBoost：深度指南

Catboost is one of the machine learning libraries I've had the opportunity to work with, and it has rapidly grown to be one of my preferred machine learning tools. This open-source gradient boosting library was created by Yandex and performs a highly helpful function: it handles categorical data without the need for any preprocessing. That saves a ton of time, which is one of the reasons it's so useful for a variety of tasks, like ranking, regression, and classification.

Catboost 是我曾有机会接触并使用的机器学习库之一，它很快就成为了我最喜欢的机器学习工具之一。这个由 Yandex 开发的开源梯度提升库，有一个非常实用的功能：它能直接处理分类数据，无需任何事先的预处理。这大大节省了时间，也是它在各种任务中表现出色（比如排序、回归和分类）的关键原因之一。

I find CatBoost's adaptability to be pretty noteworthy. It powers recommendation engines, enhances search engine results, and is even being used to model self-driving cars. In this guide, I'll go over what makes CatBoost so useful and call out its salietn features. I'll also keep an eye on comparing it to XGBoost. If you are new to some of the concepts or want additional practice to really level up your skills, also go through our comprehensive Machine Learning Fundamentals with Python skill track.

CatBoost 的适应性令人印象深刻。它不仅能驱动推荐引擎、提升搜索引擎结果，甚至还被用于模拟自动驾驶汽车。在本指南中，我将深入探讨 CatBoost 的强大之处，并重点介绍它的主要特点。同时，我也会将它与 XGBoost 进行比较。如果您对某些概念还比较陌生，或者希望通过更多实践来精进自己的技能，那么不妨也去学习我们提供的全面的《Python 机器学习基础》技能路径。

[Machine Learning Fundamentals in Python | Learn ML with Python | DataCamp](https://www.datacamp.com/tracks/machine-learning-fundamentals-with-python)

### What is CatBoost?

什么是 CatBoost?

CatBoost is an advanced gradient-boosting library specifically designed to address the challenges of handling categorical data in machine learning. CatBoost is an open-source technology that has become quite popular quickly because it can produce high-performance models without requiring a lot of data preprocessing. In contrast to other gradient boosting techniques, CatBoost is a superior option for tasks involving complicated, real-world datasets since it is good at handling categorical information natively.

CatBoost 是一个先进的梯度提升（gradient-boosting）库，专门用于解决机器学习中处理分类数据所面临的挑战。作为一项开源技术，CatBoost 因无需大量数据预处理就能生成高性能模型而迅速普及。与其他梯度提升技术不同的是，CatBoost 擅长直接处理分类信息，因此对于涉及复杂、真实世界数据集的任务来说，它是一个卓越的选择。

Origins and evolution

起源与演变

CatBoost was created by Yandex, one of Russia's leading technology companies, known for its expertise in search engines, machine learning, and artificial intelligence. The library was initially developed to enhance Yandex's search engine capabilities but people quickly noticed that it was effective for lots of different kinds of machine learning tasks, including ranking, classification, and regression.

CatBoost 由 Yandex 创建，Yandex 是俄罗斯领先的科技公司之一，以其在搜索引擎、机器学习（machine learning）和人工智能（artificial intelligence）方面的专业知识而闻名。该库最初是为了增强 Yandex 的搜索引擎功能而开发，但很快人们便发现它在多种机器学习任务中表现出色，包括排名（ranking）、分类（classification）和回归（regression）。

Core principles

核心原则

At its core, CatBoost is built on the gradient boosting framework, an ensemble learning technique that combines the strengths of multiple weak learners to produce a predictive model. CatBoost implements this framework using decision trees, but what sets it apart are two critical innovations: ordered boosting and efficient handling of categorical features.

从根本上说，CatBoost 建立在梯度提升（gradient boosting）框架之上。这是一种集成学习（ensemble learning）技术，它能结合多个弱学习器（weak learners）的优势，从而生成一个强大的预测模型。CatBoost 使用决策树（decision trees）实现了这一框架，但它之所以脱颖而出，是因为拥有两个关键的创新点：有序提升（ordered boosting）和高效处理分类特征（categorical features）的能力。

1 Ordered Boosting: Traditional gradient boosting methods are prone to prediction shifts caused by target leakage, primarily when the model uses the entire dataset to determine splits. CatBoost addresses this issue with ordered boosting, a technique that creates several permutations of the data and uses only past observations for each permutation when calculating leaf values. This method minimizes overfitting.

有序提升（Ordered Boosting）：传统的梯度提升（gradient boosting）方法很容易受到目标泄漏（target leakage）导致的预测偏移（prediction shifts）的影响，这主要是因为模型在确定数据分裂（splits）时会用到整个数据集。CatBoost 通过一种名为「有序提升」的技术解决了这个问题：它会创建数据的多个排列（permutations），并且在计算叶值（leaf values）时，只使用每个排列中「过去」的观测数据。这种方法能最大限度地减少过拟合（overfitting）的发生。

2 Efficient Handling of Categorical Features: Categorical features, such as customer IDs or product names, often pose challenges for machine learning models because they cannot be directly processed like numerical data. While most gradient-boosting algorithms require these features to be converted into numerical representations through methods like one-hot encoding, CatBoost natively handles categorical data. It automatically determines the best way to represent these features, significantly reducing the need for manual preprocessing. It works especially well when dealing with high-cardinality features, which is when a column has a huge number of distinct values.

高效处理分类特征：像客户 ID 或产品名称这类分类特征（Categorical features），常常对机器学习模型构成挑战，因为它们无法像数值数据那样直接进行处理。虽然大多数梯度提升（Gradient-boosting）算法需要将这些特征通过独热编码（one-hot encoding）等方法转换为数值表示，但 CatBoost 却能原生支持处理分类数据。它会自动确定表示这些特征的最佳方式，显著减少了手动预处理（Preprocessing）的需求。特别是在处理高基数特征（High-cardinality features）时，CatBoost 的表现尤为出色，所谓高基数特征，就是指某一列中包含大量互不相同的值时。

Standout features

突出特点

CatBoost's standout features go beyond just ordered boosting and categorical data handling:

CatBoost 的出色特性不仅体现在有序提升（ordered boosting）和类别数据处理（categorical data handling）上：

1 Symmetric Trees: CatBoost uses symmetric trees, where splits are made based on the same feature for all nodes at a given depth. This approach speeds up the training process and reduces memory consumption, making CatBoost highly efficient, even for large datasets.

对称树（Symmetric Trees）：CatBoost 算法采用了一种独特的「对称树」结构，在这种结构中，在给定深度，所有节点都基于相同的特征进行分裂。这种方法不仅显著加快了模型训练过程，还大幅减少了内存消耗，使得 CatBoost 即使在处理庞大的数据集时也能保持极高的效率。

2 GPU Support: For large-scale machine learning tasks, CatBoost offers GPU acceleration, enabling faster training times. This is particularly beneficial when working with big data or when rapid model iteration is required.

GPU 支持：对于大规模机器学习任务，CatBoost 提供了 GPU（图形处理器）加速功能，从而大大缩短了训练时间。在处理海量数据或需要快速迭代模型时，这项功能尤为实用。

Industry applications

行业应用

CatBoost's versatility has led to its adoption across various industries:

CatBoost 的多功能性（versatility）使其被广泛应用于各种行业：

1 Search Engines: Yandex initially developed CatBoost to improve search rankings, so it's no surprise it continues to be used for this purpose.

搜索引擎：CatBoost（CatBoost）最初由 Yandex（Yandex）公司开发，旨在提升搜索排名，因此它至今仍被广泛应用于这一领域也就不足为奇了。

2 Recommendation Systems: CatBoost is widely used in recommendation systems, where it helps deliver personalized content by effectively analyzing user behavior and preferences.

推荐系统：CatBoost 在推荐系统中得到了广泛应用，它能有效分析用户行为和偏好，从而帮助系统为用户精准推送个性化内容。

3 Financial Forecasting: In the finance industry, CatBoost is employed for tasks like credit scoring and stock market prediction, where accurate modeling of complex, high-dimensional data is crucial.

财务预测：在金融行业中，CatBoost 被广泛应用于信用评分和股市预测等任务，因为在这些领域，对复杂、高维度数据进行精确建模是至关重要的。

### Practical Applications of CatBoost

CatBoost 的实际应用

Let's look at classification, regression, and ranking jobs more closely.

让我们更详细地探讨一下分类（classification）、回归（regression）和排序（ranking）这三类任务。

Classification tasks

分类任务

Imagine making sense of mountains of data, whether customer feedback, emails, or medical records. This is where CatBoost steps in, excelling in classification tasks that involve sorting data into categories. Take sentiment analysis, for example. Companies are constantly bombarded with customer opinions on social media and review sites. With CatBoost, these companies can quickly and accurately gauge whether the feedback is positive, negative, or neutral. It's like having a superpower that lets businesses tune into their customers' feelings, helping them improve products and services. Or consider spam detection. Nobody likes junk mail, and with CatBoost, a developer could sift through messages and filter out the unwanted parts.

想象一下，面对如山的数据，比如海量的客户反馈、电子邮件或是医疗记录，如何才能从中理清头绪？这时，CatBoost 便能大显身手，它在需要将数据分门别类的分类任务中表现卓越。以情感分析为例。公司常常收到来自社交媒体和评论网站的客户意见。借助 CatBoost，这些公司能够迅速而准确地判断这些反馈是积极的、消极的还是中性的。这就像赋予企业一种「超能力」，让他们能够洞察客户的真实感受，从而更好地改进产品和服务。再比如垃圾邮件检测。没有人喜欢收到垃圾邮件，而有了 CatBoost，开发者就能轻松筛选信息，将那些不请自来的邮件拒之门外。

Regression tasks

回归任务

CatBoost also works well with regression, where you have to predict a continuous variable of some kind. Take, for example, predicting house prices. CatBoost considers all sorts of variables — location and size, to name just two — and predicts prices. It can do the same with predicting trends in the stock market or forecasting things like energy consumption.

CatBoost 也非常适合处理回归（regression）任务，这类任务要求我们预测某种连续变量。以预测房价为例，CatBoost 会考虑各种变量，比如房屋的位置和大小等等，从而预测出具体的价格。同样地，它也能应用于预测股市趋势，或是预报能源消耗等领域。

Ranking and recommendation systems

排名和推荐系统

CatBoost, we mentioned, has its history as a tool to improve search rankings. It's use has been extended to product recommendation on e-commerce sites (think about those 'You might also like' suggestions) and it also plays a role in content personalization (movies, music, news articles, etc.).

CatBoost，我们之前提到过，最初是作为一种改进搜索排名的工具而诞生的。如今，它的应用已扩展到电子商务网站上的产品推荐（比如那些「你可能还会喜欢」的推荐），同时它还在内容个性化（例如电影、音乐、新闻文章等）方面发挥着重要作用。

### Key Features of CatBoost

CatBoost 的主要特性

CatBoost shines in the machine learning world because it easily tackles some of the trickiest challenges. Let's break down what makes it so unique:

CatBoost 在机器学习（Machine Learning）领域脱颖而出，因为它能够轻松应对一些最具挑战性的难题。接下来，让我们深入了解它独一无二的特点：

Native handling of categorical features

原生处理类别特征

One of the big headaches in machine learning is dealing with categorical data, which are non-numerical values like "color" or "country." Usually, you'd need to do some heavy lifting to preprocess these into something the algorithm can understand, but not with CatBoost. It smartly handles categorical data right out of the box, so you can skip the extra work and still get a model that captures all the nuances in your data.

在机器学习中，处理分类数据（categorical data）一直是个让人头疼的问题，因为这些数据通常是非数值的，比如「颜色」或「国家」。通常，你需要进行繁琐的预处理工作，才能让算法理解这些数据。但有了 CatBoost，情况就完全不同了。它能「开箱即用」地智能处理分类数据，这样你就可以省去那些额外的工夫，并能得到一个充分捕捉数据中各种微妙之处的模型。

Ordered boosting technique

有序增强技术

Overfitting is a common pitfall in machine learning when your model is a star in training but flops in the real world. CatBoost's ordered boosting is like a built-in safeguard. It ensures that each prediction only uses past data, keeping your model grounded and less prone to over-optimism.

过拟合（Overfitting）是机器学习（Machine Learning）中一个常见的陷阱，它指的是模型在训练集上表现出色，但在实际应用中却效果不佳。CatBoost 引入的有序增强（Ordered boosting）技术就像一道内置的保护屏障。它确保每一次预测都只利用模型之前学习过的数据，这有助于让模型保持稳定，避免因「过度自信」而做出不切实际的预测。

GPU and multi-GPU training

GPU 和多 GPU 训练

Speed matters, especially with large datasets. CatBoost supports GPU training, which means it can crunch through data way faster than relying on CPUs alone. If you've got multiple GPUs, even better—CatBoost can use them to train your model in record time.

速度至关重要，尤其是在处理大型数据集时。CatBoost 支持 GPU 训练，这意味着它处理数据的速度远超仅依靠 CPU。如果你拥有多张 GPU（Graphics Processing Unit），那就更棒了 —— CatBoost 可以充分利用它们，以极快的速度训练你的模型。

### Performance Benchmarks and Comparison

性能测试与对比

Performance is a crucial factor when choosing the proper gradient-boosting library. CatBoost often stands out compared to other popular libraries like XGBoost and LightGBM, especially in speed and accuracy.

在选择合适的梯度提升（gradient-boosting）库时，性能是决定性的因素。与 XGBoost 和 LightGBM 等其他流行库相比，CatBoost 往往表现出色，尤其在运行速度和预测准确性方面更是如此。

Speed and efficiency

速度与效率

CatBoost is designed to be both fast and efficient. Thanks to its optimized algorithms and support for GPU acceleration, it processes data quickly, making it particularly well-suited for large-scale machine learning tasks. In many benchmarks, CatBoost has been shown to train models faster than XGBoost and LightGBM.

CatBoost 的设计初衷就是追求速度和效率。得益于其优化的算法和对图形处理器加速（GPU acceleration）的支持，它能够快速处理海量数据，这使得它特别适合处理大规模机器学习任务。在多项基准测试中，CatBoost 都表现出比 XGBoost 和 LightGBM 更快的模型训练速度。

Accuracy and robustness

准确性和鲁棒性（Robustness）

Accuracy is where CatBoost really shines. Across various datasets and tasks, from classification to regression, CatBoost often delivers more accurate predictions than its competitors. Its ability to handle categorical features natively without converting them into numerical values allows it to maintain high prediction accuracy. Plus, the ordered boosting technique helps to reduce overfitting, making CatBoost models more reliable and robust in real-world applications.

CatBoost 的一大亮点在于其准确性。无论是在各种数据集还是在分类、回归等任务中，CatBoost 通常都能比其竞争对手实现更准确的预测。它能够原生处理分类特征（categorical features），无需将其转换为数值，这使得它能够保持高预测准确性。此外，有序提升（ordered boosting）技术有助于减少模型过拟合（overfitting），从而让 CatBoost 模型在实际应用中更加可靠和稳健。

### CatBoost vs. XGBoost: A Detailed Comparison

CatBoost vs. XGBoost：深度比较

Although XGBoost and LightGBM are well-known gradient-boosting libraries, CatBoost has a number of benefits, especially when working with categorical data. CatBoost handles these features naturally, saving time and lowering the danger of overfitting, in contrast to XGBoost, which requires explicit feature engineering and preprocessing for categorical data. Furthermore, CatBoost's ordered boosting approach improves model stability, which positions it as a serious competitor for applications where prediction consistency and accuracy are critical.

尽管 XGBoost 和 LightGBM 是知名的梯度提升（gradient-boosting）库，但 CatBoost 展现出诸多优势，尤其是在处理分类数据（categorical data）时。与 XGBoost 不同，XGBoost 需要对分类数据进行明确的特征工程（feature engineering）和预处理，而 CatBoost 则能自然地处理这些特征，从而节省了时间并降低了过拟合（overfitting）的风险。此外，CatBoost 采用的有序提升（ordered boosting）方法提高了模型的稳定性，这使得它在那些对预测一致性和准确性要求极高的应用中，成为一个强有力的竞争者。

### Getting Started with CatBoost

CatBoost 入门指南

Now that we've explored what makes CatBoost so unique, let's explore how you can use it in your projects. Whether you're a Python enthusiast or an R fan, I've got you covered. Let's walk through the installation process and follow a simple example to see CatBoost in action.

既然我们已经探索了 CatBoost 的独特之处，接下来就让我们看看如何在你的项目中使用它。无论你是 Python 爱好者还是 R 语言用户，我们都为你准备了详细的指南。现在，就让我们一步步了解 CatBoost 的安装过程，并通过一个简单的例子来亲眼看看它的实际应用。

Installation guide

安装指南

Although Catboost is written in Python, it can be used in both Python and R. Let's look at how to install CatBoost in both Python and R.

尽管 Catboost 是用 Python 编写的，但它也能在 R 语言环境中运行。接下来，就让我们一起来看看如何在 Python 和 R 中安装 CatBoost 吧。

For Python Users:

对于 Python 用户：

Getting CatBoost up and running in Python is a breeze. All you need is pip. Just pop open your terminal or command prompt and type:

在 Python 中安装并运行 CatBoost 简直易如反掌。你只需要 pip。只需打开你的终端（terminal）或命令提示符（command prompt），然后输入以下命令：

```
pip install catboost
```

If you're like me and love working in Jupyter notebooks, you can install it directly within your notebook with:

如果你也像我一样，习惯在 Jupyter Notebook 中工作，那么你也可以直接在 Jupyter Notebook 环境中安装它：

```
!pip install catboost
```

For R Users:

R 用户请看：

R users, You can install CatBoost from CRAN by running:

使用 R 语言的朋友们，您可以通过执行以下命令从 CRAN 安装 CatBoost:

```
install.packages('catboost')
```

Once that's done, load it up in your R environment:

完成之后，就可以在你的 R 环境中加载它了：

```
library(catboost)
```

Basic example

基本示例

Let's explore a scenario where you want to predict movie popularity using CatBoost. Imagine you have a dataset of movies containing information about various films, including features like genre, director, budget, and release year. We'll use this data to train a CatBoost model that can predict how well a movie will perform based on these factors. For this, we will use Python.

让我们来看一个场景：你希望使用 CatBoost 模型来预测电影的受欢迎程度。想象一下，你手头有一个电影数据集，里面包含了各种电影的详细信息，比如它们的类型、导演、预算和发行年份等特征。我们将利用这些数据来训练一个 CatBoost 模型，让它能够根据这些因素预测一部电影的表现好坏。为了实现这个目标，我们将会使用 Python 编程语言。

#### Step 1: Importing libraries

步骤 1：导入库

First things first, we need to bring in CatBoost and a few other essentials from scikit-learn:

首先，我们需要引入 CatBoost 和 scikit-learn 中的一些必要组件：

```python
import catboost as cb
from catboost import CatBoostClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
```

#### Step 2: Preparing the data

步骤 2：准备数据

Let's select relevant features from our DataFrame and prepare them for the model.

我们将从 DataFrame 中选择相关的特征，并将其准备好供模型使用。

```python
# Select features and target
X = movies_df[['Genre', 'Director', 'Budget', 'Release_Year']]
y = movies_df ['Popularity']

# Encode categorical features (e.g., Genre) using techniques like one-hot encoding
# Split the data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

Here, we'll need to handle categorical features like Genre using techniques like one-hot encoding. Then, we split the data into training and testing sets.

在这里，我们需要利用例如独热编码（one-hot encoding）这样的技术来处理像「流派」(Genre）这样的类别特征。接着，我们将数据划分为训练集和测试集。

#### Step 3: Training the CatBoost model

步骤 3：训练 CatBoost 模型

Now, let's train the model to predict movie popularity:

现在，让我们训练 CatBoost 模型来预测电影的受欢迎程度：

```python
model = CatBoostRegressor(iterations=500, learning_rate=0.1, depth=6, verbose=0)
model.fit(X_train, y_train, cat_features=categorical_feature_indices)  # Assuming you have identified categorical feature indexes
```

We use CatBoostRegressor() with basic parameters and specify the categorical features for proper handling.

我们使用 CatBoostRegressor()，并为其设定了基础参数，同时指定了类别特征（categorical features）以便模型能够妥善处理。

#### Step 4: Making predictions and evaluating the model

步骤 4：做出预测并评估模型

Finally, we can use the trained model to predict the popularity of unseen movies and then evaluate the model performance:

最后，我们可以使用训练好的模型来预测新电影的受欢迎程度，并评估模型的表现：

```py
#Make predictions
y_pred = model.predict(X_test)

# Evaluate using mean squared error (MSE)
mse = mean_squared_error(y_test, y_pred)

print(f"Mean Squared Error: {mse:.2f}")
```

### Common Challenges

常见挑战

Even with CatBoost's powerful capabilities, some challenges can arise. Let's focus on the key issues you might encounter and how to handle them effectively.

尽管 CatBoost 拥有强大的功能，但在实际应用中仍可能遇到一些挑战。接下来，我们将重点关注您可能遇到的关键问题，并探讨如何有效地应对它们。

### Memory consumption

内存占用

One of the challenges users often encounter with CatBoost is its memory consumption, mainly when dealing with large datasets. Since CatBoost performs complex operations, especially when handling categorical data, it can be quite demanding on system memory.

用户在使用 CatBoost 时经常遇到的挑战之一是其内存占用（memory consumption），尤其是在处理大型数据集时。由于 CatBoost 需要执行复杂的运算，特别是在处理分类数据（categorical data）时，它对系统内存（system memory）的需求可能会相当高。

How to manage:

如何进行管理：

1 Optimize Data Types: To save memory, use smaller data types like int8 for categorical features.

优化数据类型：为了节省宝贵的内存资源，我们可以对分类特征（categorical features）使用更小的数据类型，比如 int8。

2 Batch Processing: Process data in smaller batches instead of loading the entire dataset simultaneously.

批量处理（Batch Processing)：以小批量的方式处理数据，而不是一次性加载整个数据集。

Long training times

训练时间过长

Another common challenge with CatBoost, particularly for complex models or large datasets, is the potential for long training times. The ordered boosting technique, while powerful, can sometimes slow down the training process compared to other algorithms.

CatBoost 的另一个常见挑战是，特别是对于复杂的模型或大型数据集，它可能会导致训练时间过长。虽然有序 Boosting（ordered boosting）技术非常强大，但与其它算法相比，它有时会减慢模型的训练过程。

How to optimize:

我们可以这样进行优化：

1 Adjust Hyperparameters: To reduce training time, lower the number of iterations or the depth of trees.

调整超参数（Hyperparameters）：为了缩短训练所需的时间，我们可以尝试降低模型的迭代次数或减小决策树的深度。

2 Use Early Stopping: Implement early stopping to halt training when performance plateaus.

使用提前停止（Early Stopping）：引入提前停止机制，当模型性能不再提升时，自动停止训练。

3 Leverage GPUs: Use GPU acceleration to speed up the training process for large datasets.

善用图形处理器（GPU）：利用图形处理器（GPU）加速，显著提升大规模数据集的训练速度。

## Conclusion

CatBoost is an advanced machine learning tool designed primarily for categorical data. Its revolutionary ability to handle categorical characteristics natively without requiring a lot of preprocessing saves time and lowers the possibility of error. CatBoost's features, such as ordered boosting and GPU support, provide great accuracy and streamline the training process, making it efficient even with big datasets.

CatBoost 是一种先进的机器学习工具（machine learning tool），它主要为处理分类数据（categorical data）而设计。其革命性的能力在于能够原生（natively）处理分类特征（categorical characteristics），无需进行大量的预处理（preprocessing）工作，这不仅节省了时间，还大大降低了出错的可能性。此外，CatBoost 的独特功能，例如有序提升（ordered boosting）和 GPU 支持，不仅能提供更高的准确性，还能简化训练过程，使得即使在面对庞大数据集时也能保持高效。

If you're working on a project that requires complex data or robust model performance, CatBoost is worth considering. For a comprehensive view, also consider taking the following DataCamp courses to increase your overall understanding and improve your skills:

如果你正在进行的项目对数据有较高要求，或者需要模型展现出鲁棒（robust）的性能，那么 CatBoost 是一个值得考虑的选项。为了获得更全面的认识，你还可以考虑学习以下 DataCamp 课程，从而提升你的整体理解并增强你的技能：

[Supervised Learning with scikit-learn - DataCamp Learn](https://app.datacamp.com/learn/courses/supervised-learning-with-scikit-learn)

[DataCamp Learn](https://app.datacamp.com/learn/courses/extreme-gradient-boosting-with-xgboost)

[Machine Learning with Tree-Based Models in Python - DataCamp Learn](https://app.datacamp.com/learn/courses/machine-learning-with-tree-based-models-in-python)