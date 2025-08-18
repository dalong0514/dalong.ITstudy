## 20250818GBDT-Demystified-How-LightGBM-XGBoost-and-CatBoost-Work

by Rupali Patel | Medium

Jan 22, 2025

The Gradient Boosted Decision Tree is the state of the art model for tabular dataset. What makes the Gradient Boosting different than other models ? Let's understand it.

梯度提升决策树（Gradient Boosted Decision Tree）是目前表格数据集（tabular dataset）上表现最先进的模型。那么，究竟是什么让梯度提升（Gradient Boosting）区别于其他模型呢？接下来，我们就来一探究竟。

In Gradient Boosting, subsequent predictors (another decision tree) are trained on the residual errors made by the previous tree.

在梯度提升（Gradient Boosting）中，后续的预测器（也就是另一个决策树）是在之前树模型产生的残差误差上进行训练的。

GBDT calculate the loss or margin of error on every step, and in next step it calculates the difference of the remaining error. So at first, Suppose the ground truth is y, and predicted truth is y1 so the error or loss comes out to be (y — y1).

GBDT 会在每一步计算损失或误差，并在下一步计算剩余误差的差额。因此，首先假设真实值为 y，预测值为 y1，那么误差或损失就可以表示为（y - y1）。

This becomes the ground truth for next decision tree. Now the new decision tree has predicted y2 as the truth, so the error or loss comes out to be ((y — y1) — y2). And the model continues. The final prediction becomes the sum of all the predicted truths at all the decision trees.

这成为了下一个决策树（decision tree）的真实目标值（ground truth）。现在，新的决策树已经将 y2 预测为真实值，因此它的误差（error）或损失（loss）就等于（(y — y1）— y2）。模型会以这种方式持续迭代。最终的预测结果，就是所有决策树所预测出的真实值的总和。

y^ = y1^ + y2^ + y3^ ….

In this blog, we will see one of the three implementations of GBDT along with tuning its hyperparameters to evaluate and understand the performance of these models on the dataset.

在这篇博客中，我们将介绍梯度提升决策树（GBDT）的三种实现方式中的一种，并通过调整其超参数，来评估和理解这些模型在数据集上的表现。

The three implementations are Catbost, XGBoost and Light GBM. Let's dive into the CatBoost first.

这三种实现分别是 CatBoost、XGBoost 和 Light GBM。我们先来看看 CatBoost。

### CatBoost GBDT

It is an open-source library developed by Yandex which can handle the dataset that contains both numerical and categorical features. To encode the categorical features, it uses Ordered Target Statistics.

它是一个由 Yandex 开发的开源库。这个库能够处理同时包含数值特征和分类特征的数据集。在对分类特征进行编码时，它会采用有序目标统计（Ordered Target Statistics）的方法。

Let's try to understand in simple words what Ordered Target Statistics is.To perform feature encoding, we have following methods to use — 1. One hot Encoding2. Target Encoding3. Label Encoding4. Feature Hashing5. Aggregating different labels into a single variable

让我们用简单的语言来理解一下什么是**有序目标统计**。

在进行特征编码时，我们通常会用到以下几种方法：
1 独热编码（One hot Encoding)
2 目标编码（Target Encoding）
3 标签编码（Label Encoding）
4 特征哈希（Feature Hashing）
5 将不同的标签聚合成一个变量

With these methods, we convert categorical value into a numerical value based on the Target Statistics. For example -

利用这些方法，我们可以根据目标统计量（Target Statistics）将分类值（categorical value）转换为数值（numerical value）。举个例子：

When we have a categorical feature (like "color" with values "red," "blue," "green"), and we want to turn it into numbers, one clever way is to use the average target value for each category. For example:

当我们有一个分类特征（categorical feature），比如「颜色」，它可能包含「红色」、「蓝色」、「绿色」等具体的值，如果我们需要将这些文字信息转化成计算机能处理的数字，一个巧妙的方法就是利用每个类别的平均目标值。例如：

* If "red" corresponds to an average target value of 0.8,

如果「红色」对应平均目标值 0.8，

* And "blue" corresponds to 0.3, We replace "red" with 0.8 and "blue" with 0.3.

而「蓝色」对应 0.3，我们就将「红色」替换为 0.8，将「蓝色」替换为 0.3。

This is called Target Statistics. However, there's a big problem called target leakage:

这种方法被称为目标统计量（Target Statistics）。然而，它面临一个严重的问题，那就是目标泄露（target leakage）：

* The average target value for "red" is calculated using all the training data, which includes the target value (e.g., the label) for the very example we're trying to predict. This can lead to artificially inflated performance, as the model "cheats" by looking at the answer.

当我们计算「红色」的平均目标值时，会用到所有的训练数据，而这些数据里竟然包含了我们正试图预测的那个样本的目标值（比如它的标签）。这就像模型提前「偷看」了答案一样，从而导致其性能被人为地夸大。

To solve this problem, Catboost do Ordered Target Statistics. As the name suggests, the values of Target Statistics for each example rely only on the observed history. This avoids the data leakage issue.

为了解决这个问题，Catboost 采用了有序目标统计（Ordered Target Statistics）的方法。顾名思义，在进行统计时，每个样本的目标统计（Target Statistics）值只会基于已经观测到的历史数据。这样做就有效地避免了数据泄露（data leakage）的问题。

Also, let's talk about the Tree Growing Strategy used by the CatBoost. It builds symmetric trees, meaning all leaves at a given level split on the same feature and threshold. It ensures faster training and inference as the structure is consistent.

此外，我们再来聊聊 CatBoost 所采用的「树生长策略」（Tree Growing Strategy）。它会构建一种「对称树」（symmetric trees）结构，这意味着在树的同一层级上，所有的叶子节点都会基于相同的特征（feature）和阈值（threshold）进行分裂。这种统一的结构能够确保模型在训练和推理时都拥有更快的速度。

I am adding a simple example through code which I ran in Colab to understand the working of the Catboost GBDT. I have used Employee attrition dataset present on kaggle.

为了帮助大家理解 Catboost GBDT 的工作原理，我将通过一个简单的代码示例进行说明。这个示例是在 Colab 上运行的，并且使用了 Kaggle 上的 Employee attrition dataset（员工流失数据集）。

```
!pip -qq install catboost
```

After perfoming necessary exploratory data analysis and splitting the dataset into train and test (will write one blog detailing it), I arrive at the model building step.

在完成了必要的探索性数据分析（exploratory data analysis）并将数据集划分为训练集和测试集（关于这部分内容，我将会在另一篇博客中详细介绍）之后，我们便来到了模型构建的环节。

```
cboost = CatBoostClassifier(learning_rate = 1, depth = 1, scale_pos_weight = 6, l2_leaf_reg = 8, border_count = 65)cboost.fit(x_df, y_df, cat_features = None)
```

研究人员首先初始化了一个 CatBoost 分类器（CatBoostClassifier），并将其命名为 cboost。在初始化时，设置了多个关键参数：学习率（learning_rate）为 1，树的深度（depth）为 1，正样本权重（scale_pos_weight）设置为 6，L2 正则化项（l2_leaf_reg）为 8，以及特征离散化分界点数量（border_count）为 65。随后，使用训练数据 x_df 和对应的目标变量 y_df 对这个 CatBoost 分类器 cboost 进行了训练，其中没有指定分类特征（cat_features = None）。

After building the model, I performed predictions on test data and evaluated the training and testing auc scores along with accuracy and F1.

在模型构建完成后，我对测试数据进行了预测，并评估了模型的训练和测试 AUC 分数，同时还考量了其准确度（Accuracy）和 F1 分数（F1 Score）。

> Note : The value of the above hyperparams are decided with the help of hyperopt. Sharing one screenshot of output after tuning.

> 注意：上述超参数（Hyperparams）的值是借助 hyperopt 工具确定的。这里分享了一张调优后的输出截图。

Fig: hyperopt tuning hyperparams 

图：hyperopt 调整超参数

With that, It's a wrap up. I hope this blog gives you a basic intuition on CatBoost. The other two implementations will be part of next blog including benchmark results. Stay tuned.

至此，本篇博客就告一段落了。我希望这篇博文能让你对 CatBoost 有一个初步的了解。至于其他两种实现方式，以及它们的基准测试结果，都将在下一篇博客中详细介绍。敬请期待！

### References:

* Arxiv Paper

* Catboost Tutorial

* Prof. Deepak Subramani’s Lecture at IISC

I am a Graudate Student at UMD, College Park. I will be really happy if you show your support by liking the blog and sharing your thoughts in the comment section.