## 20250818Tree-Series-2-GBDT-Lightgbm-XGBoost-Catboost

[Tree Series 2: GBDT, Lightgbm, XGBoost, Catboost -](https://yanpuli.github.io/posts/2018/05/blog-post-13/?utm_source=chatgpt.com)

## Introduction

介绍

Both bagging and boosting are designed to ensemble weak estimators into a stronger one, the difference is: bagging is ensembled by parallel order to decrease variance, boosting is to learn mistakes made in previous round, and try to correct them in new rounds, that means a sequential order. GBDT belongs to the boosting family, with a various of siblings, e.g. adaboost, lightgbm, xgboost, catboost. In this post, I will mainly explain the principles of GBDT, lightgbm, xgboost and catboost, make comparisons and elaborate how to do fine-tuning on these models.

Bagging 和 Boosting 这两种方法，都是为了将「弱学习器」（weak estimators）组合成一个更强大的模型。它们之间的主要区别在于：Bagging 通过并行的方式进行组合，旨在降低模型的方差（variance）；而 Boosting 则像一个不断学习改进的学生，它会从前一轮犯的错误中吸取教训，并在新一轮中努力纠正这些错误，这便意味着它采取的是一种序列学习（sequential order）的模式。Gradient Boosting Decision Tree（GBDT）属于 Boosting 大家族，它有许多同系列模型，比如 Adaboost、LightGBM、XGBoost 和 CatBoost。在这篇文章中，我将重点介绍 GBDT、LightGBM、XGBoost 和 CatBoost 的基本原理，对它们进行比较，并详细阐述如何对这些模型进行微调（fine-tuning）。

## Gradient Boosting

梯度提升（Gradient Boosting）

Beforing elaborate the details, I will leave you 10 minutes to think about a few quick questions of Boosting, which will help you get clear with the procedures of this model. The key of boosting is sequentially learn the "lessons" made in previous round, so:

在详细阐述具体细节之前，我将给您 10 分钟时间，思考几个关于提升算法（Boosting）的小问题。这将帮助您更清楚地理解这种模型的工作流程。提升算法的关键在于：它会顺序地从前一轮的「经验」中学习。所以：

1 How to combine previous learners' results with this round?

如何将上一轮（或之前的）训练结果与本轮训练结合起来？

2 In what form to represent and add these previous results?

这些上一轮的结果应该以什么形式来表示和融入？

3 GB stands for gradient boosting, what's gradient for in this algorithm?

GB 是梯度提升（gradient boosting）的缩写，那么在这个算法中，‘梯度'（gradient）究竟有什么作用？

Ready to go?

Gradient Boosting Machine learns the errors made in previous rounds, and tries to correct them. These errors are represented as residuals, to be more precise, it works on fitting the gradient of the residuals. That's why it's called gradient boosting.

梯度提升机（Gradient Boosting Machine）会学习前面几轮迭代中模型所犯的「错误」，并尝试去纠正这些错误。更准确地说，这些错误被表示为残差（residuals），而梯度提升机的任务就是去拟合这些残差的梯度（gradient）。这就是它被称为「梯度提升（Gradient Boosting）」的原因。

Figure 1. Gradient Boosting Machine Algorithm

图 1：梯度提升机（Gradient Boosting Machine）算法

Please forgive my twisted handwriting, writing down the algorithm by hand indeed helps me memorizing the details. In a nutshell, in the kth iteration, the algorithm tries to fit a new single learner hk into the last residuals. Shown in Figure 1, it minimizes the mean squared error of the residual and hk by finding the optimal w* . Then, add hk multiply a parameter ρ to Fk-1 to form Fk.

请原谅我潦草的字迹，手写算法确实能帮助我记住（或加深对）细节。简而言之，在第 k 次迭代中，该算法会尝试将一个新的单一学习器（single learner）hk 拟合到上一次迭代的残差上。如图 1 所示，它通过找到最优参数 w* 来最小化残差与 hk 之间的均方误差（mean squared error）。然后，将 hk 乘以一个参数 ρ，并将其累加到 Fk-1 中，从而形成 Fk。

Quick question: why ρ is needed? why not directly add hk to F?

问个小问题：为什么需要 ρ 呢？为什么不直接把 hk 加到 F 里去？

ρ can be viewed as a learning rate(learning step), it's a strategy for avoiding overfitting. By adding a parameter, which is less than 1, though the learning speed will be slowed down, it guarantees the importance of each hk won't become too much. Usually, a penalty Ω on tree complexity(a regularization method) will be also added to inhibit overfitting. I will summarize all the strategies for overfitting later.

ρ 可以看作是一个学习率（learning rate）或学习步长（learning step），它是避免过拟合（overfitting）的一个重要策略。通过引入一个小于 1 的参数 ρ，虽然会减慢学习速度，但能有效确保每个 hk 的影响力不会变得过大。通常，我们还会增加一个针对树复杂度（tree complexity）的惩罚项 Ω（这是一种正则化方法（regularization method）），来进一步抑制过拟合。关于所有避免过拟合的策略，我稍后会进行总结。

### GBDT

GBDT has some variation from GBM, e.g. hk is referred to DT in GBDT, Fk is the ensemble of DTs, residual equals to yi minus Fk-1, the searching space is J non-overlapping regions, {Rj}.

GBDT 与 GBM 有一些不同之处，例如在 GBDT 中，hk 指的是决策树（DT），Fk 是多棵决策树（DT）的集成。残差（residual）的计算方式是 yi 减去 Fk-1。而模型的搜索空间则被划分为 J 个不重叠的区域，这些区域可以用 {Rj} 来表示。

Figure 2. GBDT Algorithm

图 2：GBDT 算法表 1：树模型应对过拟合的约束

Table 1. Tree Constraints for overfitting

In Table 1, I have listed the methods which could be used for controlling overfitting. These methods can be divided into 2 groups: one is limit the number of trees, the other is limit the complexity of each single tree. There are some other controlling methods, e.g. sampling, sub-sampling, I will included them later in the section about parameter tuning for specific tree models.

在表 1 中，我列出了可用于控制过拟合（overfitting）的方法。这些方法可以分为两类：一类是限制树的数量，另一类是限制每棵独立树的复杂度。还有一些其他控制方法，例如采样（sampling）、子采样（sub-sampling）等，我们将在后续关于特定树模型参数调优（parameter tuning）的章节中介绍它们。

### Finding Best Splitting

如何找到最佳分割点

We know the best splitting comes with the point which maximize the loss function, but how to find the point? Let me explain this in a reversed way: the searching space for best split is limited, which is a set of proposed splits, and there are two ways to find the proposed split sets, one is exact greedy searching, the other is approximate algorithm.

我们知道，最佳分割点是那个能让损失函数最大化的点。那么，我们该如何找到这个点呢？让我换个角度来解释：寻找最佳分割的搜索空间其实是有限的，它由一系列「候选分割点」组成。而要找到这些候选分割点集合，目前主要有两种方法：一种是精确贪婪搜索（exact greedy searching），另一种则是近似算法（approximate algorithm）。

Figure 3. Find Best Splits

图 3. 寻找最佳分割点

As you can see from Figure 4, exact greedy algorithm goes through all the values in that feature for finding the split, it has an inner loop and an outer loop, so the time complexity would be O(# unique I * m). In order to make this algorithm less time-consuming, the values need to be firstly sorted. which is firstly sort all the values of that feature, then calculate the loss reduction for each value. For approximate method, it utilize percentile of that feature's distribution as proposed points, then cut continuous feature into buckets based on these points, aggregate the statistics, and find the best point according to these information. The time complexity has been reduced to O(m). This algorithm has 2 branches, one is coming up with the proposals at the initial tree construction time, and use these proposals through the whole process. The other is calculate new proposals after each splits. It's not hard to see the first one is more efficient, as it doesn't to calculate proposals all the time. But the other would be more accurate for finding the point, so it's better for growing deeper trees.

正如我们从图 4 中看到的，精确贪婪算法（exact greedy algorithm）在寻找分割点时，会遍历该特征的所有可能值。它包含一个内循环和一个外循环，因此其时间复杂度（time complexity）是 O（# unique I * m）。为了让这个算法更省时，首先需要对这些值进行排序。具体来说，就是先对该特征的所有值进行排序，然后计算每个值对应的损失减少量（loss reduction）。而对于近似方法（approximate method），它会利用该特征分布的百分位数（percentile）作为候选分割点，然后根据这些点将连续特征（continuous feature）划分成多个区间（或称「分桶」，buckets），接着汇总这些区间的统计信息，并根据这些信息找到最佳的分割点。这样一来，时间复杂度就大大降低到了 O（m）。这种近似算法又分为两个主要策略：一种是在初始构建树的时候就确定好所有的候选分割点，并在整个决策树的构建过程中重复使用这些点；另一种则是在每次进行分割后，重新计算新的候选分割点。不难看出，第一种策略效率更高，因为它避免了反复计算候选点。然而，第二种策略在寻找最佳分割点时会更精确，因此更适合构建更深层次的决策树。

Figure 4. Splitting Finding Algorithm

图 4. 分裂寻找算法

Figure 5. Approximate Algorithm

图 5. 近似算法

With all these knowledge and fomula in mind, then it's much easier for you to understand the difference and improvement of Lightgbm, XGBoost, and Catboost compared to each other and GBDT.

有了这些知识和公式，你就更容易理解 LightGBM、XGBoost 和 CatBoost 这些模型之间，以及它们与 GBDT 相比，分别有哪些区别和改进了。

### XGBoost

We all know or have heard of XGBoost is extremely efficient, that's why it becomes the most popular tools for Kaggle competition. But do you know why XGB can work so powerful and fast? 

我们都知道或听说过 XGBoost 效率极高，正因如此，它成为了 Kaggle 竞赛中最受欢迎的工具。但你是否知道 XGBoost 为什么能表现得如此强大和快速吗？

`Pre-knowledge:

预备知识：

1 disk: usually referred to hard drive. In order to process the data stored on disk, the CPU need to assign a thread to find the data from the disk, then fetch it into memory. Meanwhile, when searching on the disk, a head need to move across the disk to find the data. It is very time-consuming for all above processes.

磁盘，通常我们指的是硬盘。为了处理存储在磁盘上的数据，中央处理器（CPU）需要分配一个线程去磁盘中寻找数据，然后将它们加载到内存中。与此同时，当在磁盘上搜索数据时，磁头还需要在磁盘上来回移动才能找到目标数据。所有这些过程都非常耗时。

2 memory: e.g. RAM: random access memory(another version is ROM), no physical movement is needed for memory. ` 1. Reduce time by redesigning data access & storage

内存（memory）：例如，随机存取存储器（RAM）（与只读存储器（ROM）不同，RAM 不需要任何物理移动）。` 1. 通过重新设计数据访问和存储来减少时间。

The most time-consuming part in tree learning is to sort the feature values. In order to reduce the time, XGB applies column block and cache-aware access strategies, which greatly reduces the data accessing time.

在树模型学习过程中，最耗费时间的部分是对特征值进行排序。为了缩短这部分耗时，XGB 模型采用了列块（column block）和缓存感知访问（cache-aware access）策略，这些策略极大地减少了数据访问所需的时间。

1.1 Column Block

列块（Column Block）

XGB stores the data in a compressed column format in in-memory units, which called block. The feature values will be sorted only once before training, instead of doing sorting in each split finding iterations.

XGB 将数据以压缩列格式存储在内存单元中，这些单元被称为「块」。在训练开始前，特征值仅排序一次，这样就避免了在每次查找分裂点时重复排序。

1.1.1 For exact greedy algorithm:


对于精确贪婪算法（exact greedy algorithm）来说，其要求之一是：

1 the entire data is stored in a single block,

全部数据都必须存储在一个单独的数据块中，

2 one scan through the block can get all the statistics of the proposed points.

对该块进行一次扫描，即可获得所有相关点的统计数据。

1.1.2 For approximate algorithm:

对于近似算法：

1 data subset of rows stored in multiple blocks, instance indices are stored in blocks too,

数据行的子集会存储在多个数据块（block）中，而实例的索引信息也同样存储在这些数据块里。

2 blocks can be distributed over machine, or even stored on disk,

这些数据块可以分布在不同的计算机上，甚至可以直接存储在磁盘上。

3 enables a linear scan over the sorted columns, and the statistics collecting for each feature can be implemented parallelized,

这样一来，就可以对排好序的列进行线性扫描，而且每个特征（feature）的统计信息收集工作也可以并行化处理，

4 block also supports column subsample, which I will talk later.

此外，这种「块」结构还支持列子采样（column subsample）功能，这一点我们稍后会详细介绍。

Figure 6. Example for Block Parallel

图 6. 块并行（Block Parallel）的一个例子

1.2 Cache-aware Access

缓存感知（Cache-aware）访问

The model fetches statistical info by instance row index. However, as the instances are sorted by values, the access to these row indices will be non-continuous. When these statitics doesn't fit into CPU cache, the accessing speed will be slowed down.

模型会根据实例的行索引来获取统计信息。然而，由于这些实例是按照特定数值排序的，导致对它们行索引的访问变得非连续。当这些统计数据无法完全放入中央处理器（CPU）缓存中时，访问速度就会变慢。

1.2.1 For exact greedy algorithm:

对于精确贪婪算法:

1 Using a thread pre-fetches instances from non-continuous memory into a continuous buffer(in-memory & physical continuous),

一个线程负责将非连续内存中的实例预先读取到一块连续的缓冲区中（这块缓冲区在内存中是连续的，并且在物理存储上也是连续的）,

2 then perform gradient statistics accumulation in the continuous buffer.

然后在连续缓冲区中对梯度统计信息进行累积。

1.2.2 For approximate algorithm:

对于近似算法：

1 still use block for pre-fetching, but need to be careful about the size, if too large, the calculated gradient statistics can't fit into CPU cache, otherwise, can't store enough data, not efficient for parallelization.

依然采用块（block）的方式进行预取（pre-fetching），但需要谨慎选择其大小：如果块太大，计算出的梯度统计信息就无法完全载入 CPU 缓存（CPU cache）中；反之，如果块太小，则无法存储足够的数据量，这会降低并行化（parallelization）效率。

1.3 Out-of-core Block

核外数据块

It's mentioned above, blocks can be distributed in disk, which will increase the time in doing disk I/O reading. To solve this, XGB will authorize an independent thread to pre-fetch the block into buffer, which will enable concurrence between computation and disk reading. Besides, XGB has also applies two other tricks to improve this out-of-core computation.

如上所述，当数据块（Block）存储在磁盘上时，会显著增加磁盘 I/O（Input/Output）读取的时间。为了解决这个问题，XGBoost 会启动一个独立的线程，负责将所需的数据块预先加载到内存缓冲区中。这种机制使得计算和磁盘读取能够并发进行，从而提高效率。此外，XGBoost 还采用了另外两个小技巧，进一步优化了这种核外（Out-of-core）计算的性能。

1.3.1 Block Compression: data will be compressed by columns in block, and decompress on-the-fly when loading into memory. This method helps to reduce reading time, as size of the compressed block is definitely smaller than the original one.

1.3.1 块压缩：数据会按块中的列进行压缩，并在加载到内存时进行即时（on-the-fly）解压缩。这种方法有助于缩短读取时间，因为压缩后的数据块（block）大小肯定比原始数据小。

1.3.2 Block Sharding: store the data subset distributedly in multiple disks, assign each disk a pre-fetcher thread, Then, the training thread can altervatively reads the data. (Referenced from [6], this part is a little confusing to me. At first, I thought the improvement made by block sharding is to enable multiple threads read these distributed disks at the same time, which means parallelization. But later, I realized it might be a different case: e.g. the sharding strategy stores subset A, subset B on different disks. When it comes with the case that only B is needed, so the thread can directly touch the disk where B is on. Otherwise, A and B stored in one disk, the thread need to pass through the whole data to find B. Please correct me, if I'm wrong.)

1.3.2 块分片（Block Sharding）：这种技术将数据子集分散存储到多个磁盘中，并为每个磁盘配置一个预取线程（pre-fetcher thread）。这样一来，训练线程（training thread）就可以交替地从不同磁盘读取数据。(引自 [6]，这部分内容可能有些令人困惑。起初，我曾认为块分片带来的改进在于能够让多个线程同时从这些分布式磁盘中读取数据，也就是实现并行化。但后来，我意识到它可能指的是另一种可能性：例如，分片策略会将子集 A 和子集 B 存储在不同的磁盘上。当只需要子集 B 时，训练线程就可以直接从存储 B 的磁盘中读取数据。反之，如果 A 和 B 都存储在同一个磁盘中，线程就需要遍历（扫描）整个磁盘上的数据才能找到 B。如果这种理解有误，欢迎指正。)

2. Reduce time by improving the algorithm: enable automatic sparse data handling

Sparse data is very common in both classfication and regression problems, when doing split finding, XGB offers a new option to be aware of these sparse data. Shown in Figure 7, when doing value sorting, only non-missing entries will be accessed. Such strategy helps to reduce the time cost for sorting. XGB also adds a default direction in each node. when coming across a missing value, the entry will be classified into the default direction.

2. 通过改进算法减少时间：自动处理稀疏数据稀疏数据在分类和回归问题中都非常常见。在进行特征分裂点查找（split finding）时，XGBoost（XGB）提供了一种新选项来智能地处理这些稀疏数据。如图 7：所示，在进行数值排序（value sorting）时，XGBoost 只会访问非缺失的数据项。这种策略有助于显著减少排序所花费的时间。此外，XGBoost 还在每个节点中增加了一个默认方向（default direction）。当遇到缺失值时，该数据项就会被归类到这个默认方向。

Figure 7. Sparsity-aware Split Finding Algorithm

## Lightgbm

图 7. 稀疏感知（Sparsity-aware）分裂查找算法

## LightGBM

XGB provides both exact split searching(enumerate all instances) and approximate searching(histgram-based), while lightgbm mainly works on the second one, and maintains relatively accurate results at the same time. In this sense, lightgbm is typically faster than XGB. To achieve the above goal, lightgbm proposes 2 techniques: Gradient-based One-side Sampling(GOSS) and Exclusive Feature Bundling(EFB).

XGB 算法在寻找决策树分裂点时提供了两种策略：一种是精确拆分搜索（通过枚举所有数据实例来寻找最佳分割点），另一种是近似拆分搜索（基于直方图的方式）。而 LightGBM 主要依赖后一种近似搜索方法，同时还能保持相当高的准确度。正因如此，LightGBM 通常比 XGB 运行得更快。为了实现这一速度优势，LightGBM 引入了两种独特的技术：梯度单侧采样（Gradient-based One-side Sampling，GOSS）和排他性特征捆绑（Exclusive Feature Bundling，EFB）。

1.1 GOSS: reduce data size by rows

Typically, instances with larger gradients will contribute more to information gain, compared to the ones with smaller gradients(e.g. think about a data set whose distribution is uniform). Thus, keeping all the instances with large gradients, while removing the smaller ones, such method seems to be a good choice. However, if we directly remove all the small gradient data, the distribution would be distorted, and the result accuracy would be lost too. So lightgbm keeps data with large gradients. So how to target at the large ones? It can be done: 1. using pre-defined threshold to select large gradients,

1.1 GOSS：逐行缩减数据规模通常来说，与梯度较小的实例相比，那些具有较大梯度（Gradient）的实例对信息增益（Information Gain）的贡献更大（例如，设想一个数据分布均匀的数据集）。因此，保留所有大梯度实例，同时移除小梯度实例，这种做法似乎是个不错的选择。然而，如果我们直接删除所有小梯度数据，原始数据分布就会失真，从而导致模型结果的准确性下降。所以 LightGBM 会保留那些具有大梯度的数据。那么，具体如何筛选出这些大梯度数据呢？方法之一是： 1. 使用预定义的阈值来选择大梯度数据。

1. or selecting top percentile. Lightgbm sets a sampling ratio a to select the top ones(need to calculate the gradients first, and use the absolute values).

And randomly drop the ones having small gradients, by using a ratio b. To compensate for data loss, lightgbm uses a constant to amplify the small gradient instances when calculating the information gain.

或选择前百分位。LightGBM （Light Gradient Boosting Machine）会设定一个采样比例 a ，用来筛选出那些最重要的样本（这需要先计算其梯度，并取其绝对值）。

同时，它还会通过设定一个比例 b ，随机丢弃那些梯度较小的样本。为了弥补这种数据损失，LightGBM 在计算信息增益时，会使用一个常数来放大梯度较小的实例，从而增加其权重。

Figure 8. GOSS Algorithm

1.2 EFB: reduce data size by columns

图 8. GOSS 算法

1.2 EFB：按列削减数据规模

EFB aims to eliminate uneffective sparse features,(which are usually mutually exclusive, e.g. one hot encoded feature sets), by bundling them into a single one. Algorithm 3 in the following figure shows how lightgbm find the features to bundle. It firstly builds a graph, using edges to represent total conflicts among features, then sort the features by the degree in the graph, based on these knowledge, assign the feature to its correponding bundles. Algorithm 3 is not fit for the data with too many features, so lightgbm improves this by using counting of non-zero values to substitute building the graph. algorithm 4 is about how to transform these features into one. The new feature will be represented in bins, and the key is to make sure the relation between each original feature and new feature bin. is 1 to 1. That's how lightbgm can identify the original feature from these bundles.

EFB（Exclusive Feature Bundling，独占特征捆绑）旨在通过将作用不大的稀疏特征（这些特征通常是互斥的，例如独热编码（one hot encoded）特征集）捆绑成一个新特征，从而有效消除它们。在下图的算法 3 中，展示了 LightGBM 如何找出需要捆绑的特征：它首先构建一个图，利用边来表示特征之间的冲突关系；然后根据图中的度（degree）对特征进行排序；最后，LightGBM 基于这些信息，将特征分配到各自对应的捆绑中。由于算法 3 不适用于特征数量过多的数据，LightGBM 对此进行了改进，即通过统计非零值来取代图的构建过程。算法 4 则阐述了如何将这些特征整合成一个。新特征将以分箱（bins）的形式表示，而其核心在于确保每个原始特征与新特征中的对应分箱之间都保持一对一的映射关系。这便是 LightGBM 如何从这些捆绑中精确识别出原始特征的关键所在。

Figure 9. EFB Algorithm

## Catboost

图 9. EFB 算法

## Catboost

Finally, here comes to the last model in this post, Catboost, a relative young sibling of all these ensemble trees. The first three letter ‘cat' stands for category, because this model can directly handle discreet features, no matter it's in numeric form, string or something else. That is users don't need to transform categorical features into numbers before importing the data into catboost. So how is this section implemented in catboost?

最后，我们来看看这篇文章中的最后一个模型：Catboost。在所有这些集成树（ensemble trees）模型中，Catboost 算是一个相对年轻的成员。它的前三个字母「cat」代表「类别」（category），这是因为它能够直接处理离散特征（discreet features），无论是数字形式、字符串，还是其他类型的数据。也就是说，用户在将数据导入 Catboost 之前，无需将分类特征转换为数字。那么，Catboost 是如何实现对这些离散特征的处理呢？

1. How catboost deals with categorical features?

1.1 A common way is to substitute the feature value with averaged response value on the whole training set:

1. catboost 是如何处理分类特征（categorical features）的？

1.1 一种常见的方法是，用在整个训练集上计算得到的平均响应值来替换特征值：

j: the instance index for the whole training set, k: the kth feature, which is a categorical, i: index of the instances which are from the same group in feature k, the denominator represents the count of feature K's certain value shown in the whole training set.

j：表示整个训练集的实例（instance）索引；k：表示第 k 个特征（feature），它是一个类别型特征；i：表示在特征 k 中属于同一组的实例索引。其中，分母代表特征 k 的某个特定值在整个训练集中出现的总次数。

The problem for above formula is if there is only one instance in the training set which belongs to the kth feature's certain value, then the result is just this instance's label value, which may cause overfitting. To solve this, catboost introduces random data permutation, two other parameters and calculate the averaged label on these random set instead of the whole training.

上述公式存在的问题是，如果训练数据集中只有一个样本实例（instance）拥有某个特定值，比如说第 k 个特征的某个具体数值，那么计算出的结果就只会是这个单一实例的标签值（label value）。这种情况下，模型很容易出现过拟合（overfitting）现象。为了解决这一问题，catboost 引入了随机数据置换（random data permutation）以及另外两个参数。它不再使用整个训练集来计算，而是通过这些随机数据集合来计算平均标签值。

P: a prior value, a:(>0) weight of the prior. The prior helps to reduce the noise from low-frequency categories. For regression, prior is calculated by take average label value. For binary classification: prior equals the probability of encountering a positive class.

P：一个先验值（prior value)；a：先验的权重（a> 0）。这个先验有助于减少来自低频类别的噪声。对于回归（regression）问题，先验是通过计算标签的平均值来确定的。对于二元分类（binary classification）问题，先验则等于出现正类别（positive class）的概率。

1.2 A simpler way implemented in catboost is to calculate the frequence of the categorical features, and use this frequence for substitution.

2. Feature Combination

1.2 catboost 中实现了一种更简单的方法：计算分类特征（categorical features）的出现频率（frequency），并用这个频率值来替代原始特征。

2. 特征组合

Another improvement is automatic greedy feature combinations. The model will consider all combinations of the categorical features, but these combinations won't be used for the first tree split. Catboost also enables combination of numerical and categorical features.

另一个改进是自动的「贪婪特征组合」（greedy feature combinations）机制。模型会自动考虑所有「分类特征」（categorical features）的组合方式，但这些组合不会直接用于决策树的第一次分裂。此外，Catboost 模型还能够实现「数值特征」（numerical features）和分类特征的组合。

**Tips:** Users need to specify categorical features in catboost, or the model will either treat it as numeric by default.

3. Unbiased Gradient

** 小贴士：** 在使用 CatBoost 时，用户需要明确指定哪些是分类特征（categorical features），否则模型默认会将它们当作数值型特征（numeric features）来处理。

3. 无偏梯度（Unbiased Gradient)
</select3_refined_translation>

The third improvement in catboost is calculating the gradient without bias. Typically, boosting tree models use the same data to estimate gradients and build model, which may cause overfitting. In catboost, it implements these two parts on different data. The basic idea is making random permutations on the training, then implement gradient estimation and tree building on different permutations.

CatBoost（CatBoost）的第三个改进是，它能够计算出「无偏」的梯度。通常来说，梯度提升树模型会使用同一份数据来估计梯度并训练模型，但这很容易导致模型过拟合。而在 CatBoost 中，它巧妙地将梯度估计和模型构建这两部分放在了不同的数据上进行。其基本思想是：首先对训练数据进行随机打乱（即随机排列），然后将梯度估计和树模型构建分别在这些不同的随机排列数据上完成。

Figure 10. EFB Algorithm

图 10. EFB 算法

### Reference

[1].Friedman, J. H. (February 1999). "Greedy Function Approximation: A Gradient Boosting Machine".

[2].http://www.flickering.cn/machine_learning/2016/08/gbdt%E8%AF%A6%E8%A7%A3%E4%B8%8A-%E7%90%86%E8%AE%BA/

[3].https://en.wikipedia.org/wiki/Gradient_boosting

[4].Anna Veronika Dorogush, Vasily Ershov, Andrey Gulin "CatBoost: gradient boosting with categorical features support". Workshop on ML Systems at NIPS 2017.

[5].Guolin Ke, Qi Meng, Thomas Finley, Taifeng Wang, Wei Chen, Weidong Ma, Qiwei Ye, Tie-Yan Liu. "LightGBM: A Highly Efficient Gradient Boosting Decision Tree". Advances in Neural Information Processing Systems 30 (NIPS 2017), pp. 3149-3157.

[6].Tianqi Chen and Carlos Guestrin. XGBoost: A Scalable Tree Boosting System. In 22nd SIGKDD Conference on Knowledge Discovery and Data Mining, 2016