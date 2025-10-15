## 20251015Diffusion-Language-Models

[Diffusion language models – Sander Dieleman](https://sander.ai/2023/01/09/diffusion-language.html)

Diffusion models have completely taken over generative modelling of perceptual signals such as images, audio and video. Why is autoregression still the name of the game for language modelling? And can we do anything about that? Some thoughts about what it will take for other forms of iterative refinement to take over language modelling, the last bastion of autoregression.

扩散模型（Diffusion models）已经完全主导了图像、音频和视频等感知信号的生成式建模（generative modelling）。那么，为什么自回归（autoregression）在语言建模领域仍然占据着主导地位？我们能对此做些什么呢？本文将探讨其他形式的迭代细化（iterative refinement）将如何取代语言建模 —— 自回归的最后堡垒 —— 的一些思考。

### 01. The rise of diffusion models

Roughly three years ago, things were starting to look as if adversarial image generators were about to be supplanted by a powerful combination of autoregression and discrete representation learning. BigGAN1 and StyleGAN2 had significantly expanded the capabilities of image generators, but the mode-seeking nature of GANs made them favour realism over diversity. This presented some challenges, and people were having trouble reproducing impressive domain-specific results (e.g. generating realistic human faces) on more diverse training datasets.

扩散模型的兴起大约三年前，对抗性图像生成器（adversarial image generators）似乎即将被自回归（autoregression）和离散表示学习（discrete representation learning）的强大组合所取代。BigGAN1 和 StyleGAN2 显著增强了图像生成器的能力，但生成对抗网络（GANs）追求特定模式的特性，使其更倾向于生成真实感强的图像，而非追求多样性。这带来了一些挑战，导致研究人员在更具多样性的训练数据集上，难以重现那些在特定领域取得的令人印象深刻的结果（例如生成逼真的人脸）。

VQ-VAE 23 and especially VQGAN4 extolled the virtue of a two-stage approach to generative modelling: first turn everything into a highly compressed discrete one-dimensional sequence, and then learn to predict this sequence step-by-step using a powerful autoregressive model. This idea had already proven fruitful before, going back to the original VQ-VAE5, but these two papers really drove the point home that this was our best bet for generative modelling of diverse data at scale.

VQ-VAE [23] 和 VQGAN [4] 尤其强调了生成式建模（generative modelling）两阶段方法的优势：首先，将所有数据转换成高度压缩的离散一维序列（discrete one-dimensional sequence）；然后，利用强大的自回归模型（autoregressive model）逐步预测这个序列。这种思想此前已被证明是卓有成效的，最早可以追溯到最初的 VQ-VAE [5]。而这两篇论文更是明确指出，对于大规模生成多样化数据而言，这种方法是最佳选择。

But then, a challenger appeared: a new generative modelling approach based on iterative denoising was starting to show promise. Yang Song and Stefano Ermon proposed score-based models: while their NeurIPS 2019 paper6 was more of a proof-of-concept, the next year's follow-up ‘Improved Techniques for Training Score-Based Generative Models'7 showed results that convinced some people (including me!) to take this direction of research more seriously. Another NeurIPS 2020 paper by Jonathan Ho, Ajay Jain and Pieter Abbeel, ‘Denoising Diffusion Probabilistic Models' (DDPMs)8 showed similar results, and it didn't take people too long to realise that DDPMs and score-based models were two sides of the same coin.

但就在那时，一个新的竞争者登场了：一种基于迭代去噪的全新生成建模方法开始崭露头角。杨松（Yang Song）和斯特凡诺·埃蒙（Stefano Ermon）提出了基于分数（score-based）的模型：尽管他们发表在 NeurIPS 2019 上的论文 6 更多是作为概念验证（proof-of-concept），但次年发布的后续论文《用于训练基于分数的生成模型的改进技术》（‘Improved Techniques for Training Score-Based Generative Models'）7 所展示的结果，说服了一些人（包括我！）开始更认真地对待这个研究方向。乔纳森·霍（Jonathan Ho）、阿贾伊·贾恩（Ajay Jain）和彼得·阿比尔（Pieter Abbeel）在 NeurIPS 2020 上发表的另一篇论文《去噪扩散概率模型》（‘Denoising Diffusion Probabilistic Models'（DDPMs））8 也展示了类似出色的结果。很快，人们就意识到 DDPMs 和基于分数的模型实际上是殊途同归，是同一枚硬币的两面。

The real triumph of diffusion models over other alternatives for image generation came in 2021, with ‘Diffusion Models Beat GANs on Image Synthesis'9 by Prafulla Dhariwal and Alex Nichol. At that point, it was pretty clear to everyone in the know that this approach was poised to take over. Powerful diffusion-based text-to-image models such as GLIDE10 started to arrive by the end of that year, and proceeded to go mainstream in 2022.

扩散模型（diffusion models）在图像生成方面真正超越其他替代方案的胜利，发生在 2021 年。这主要归功于 Prafulla Dhariwal 和 Alex Nichol 发表的论文《扩散模型在图像合成方面击败 GANs》9。当时，对于所有知情者而言，这种方法将要占据主导地位这一点已经非常明确。强大的基于扩散的文本到图像模型，例如 GLIDE10，在当年年底开始涌现，并于 2022 年迅速走向主流。

If you are unfamiliar with diffusion models, I recommend reading at least the first section of my previous blog post ‘Diffusion models are autoencoders' for context, before reading the rest of this one.

如果你对扩散模型（diffusion models）不熟悉，我建议在阅读本文其余部分之前，至少阅读我之前那篇博客文章《扩散模型是自编码器》的第一部分，作为背景知识。

### 02. Diffusion for images: a match made in heaven

Diffusion models and the human visual system have one important thing in common: they don't care too much about high frequencies. At least, not out of the box. I discussed the reasons for this in some detail in an earlier blog post (section 5 in particular).

图像扩散模型：一种完美的结合扩散模型（Diffusion models）和人类视觉系统有一个重要的共同点：它们对高频信息不太敏感。至少，在默认情况下是这样的。我曾在之前的一篇博客文章中详细探讨过其中的原因（尤其是在第 5 节）。

In a nutshell, the different levels of noise at which a diffusion model operates allow it to focus on different spatial frequency components of the image at each iterative refinement step. When sampling an image, the model effectively builds it up from low frequencies to high frequencies, first filling in large-scale structure and then adding progressively more fine-grained details.

简而言之，扩散模型（Diffusion Model）在不同的噪声水平下工作，这使得它能够在每个迭代细化步骤中，专注于图像的不同空间频率分量（Spatial Frequency Components）。在生成图像时，模型会有效地将其从低频率逐步构建到高频率，首先勾勒出大尺度的整体结构，然后逐渐添加更多精细的细节。

During training, we sample a noise level for each training example, add noise to it, and then try to predict the noise. The relative weights with which we sample the different noise levels therefore determine the degree to which the model focuses on large-scale and fine-grained structure. The most commonly used formulation, with uniform weighting of the noise levels, yields a very different objective than the likelihood loss which e.g. autoregressive models are trained with.

在训练期间，我们为每个训练样本（training example）抽取一个噪声水平（noise level），然后向其添加噪声，接着模型会尝试预测这个噪声。因此，我们抽取不同噪声水平时的相对权重（relative weights），就决定了模型关注大尺度结构（large-scale structure）和细粒度结构（fine-grained structure）的程度。最常用的方法是使用噪声水平的均匀加权（uniform weighting），这种方式得到的目标与例如自回归模型（autoregressive models）所训练的似然损失（likelihood loss）目标截然不同。

It turns out that there is a particular weighting which corresponds directly to the likelihood loss11, but this puts significantly more weight on very low noise levels. Since low noise levels correspond to high spatial frequencies, this also indirectly explains why likelihood-based autoregressive models in pixel space never really took off: they end up spending way too much of their capacity on perceptually meaningless detail, and never get around to modelling larger-scale structure.

原来有一种特定的加权方式，它直接对应于似然损失 11，但这会显著地赋予极低噪声水平更高的权重。由于低噪声水平对应着高空间频率，这也间接解释了为什么基于似然的像素空间（pixel space）自回归模型（autoregressive models）从未真正流行起来：它们最终将过多的能力投入到感知上无足轻重的细节中，而从未着力于建模更大尺度的结构。

Relative to the likelihood loss, uniform weighting across noise levels in diffusion models yields an objective that is much more closely aligned with the human visual system. I don't believe this was actually known when people first started training diffusion models on images – it was just a lucky coincidence! But we understand this pretty well now, and I think it is one of the two main reasons why this modelling approach completely took over in a matter of two years. (The other reason is of course classifier-free guidance, which you can read more about in my previous blog post on the topic.)

与似然损失（likelihood loss）相比，扩散模型（diffusion models）在噪声级别上采用均匀加权（uniform weighting across noise levels），能生成一个与人类视觉系统（human visual system）高度契合的目标。我个人认为，当人们最初开始在图像上训练扩散模型时，并没有意识到这一点 —— 这纯属一个幸运的巧合！但现在我们对此有了相当深入的理解，我认为这也是这种建模方法能在短短两年内迅速普及并占据主导地位的两个主要原因之一。(另一个原因当然是无分类器引导（classifier-free guidance），你可以在我之前关于该主题的博客文章中阅读更多相关内容。)

The reason I bring all this up here, is that it doesn't bode particularly well for applications of diffusion models beyond the perceptual domain. Our ears have a similar disdain for high frequencies as our eyes (though to a lesser extent, I believe), but in the language domain, what does "high frequency" even mean12? Given the success of likelihood-based language models, could the relatively lower weight of low noise levels actually prove to be a liability in this setting?

我之所以在这里提及所有这些，是因为它对于扩散模型（diffusion models）在感知领域之外的应用来说，预示着不太乐观的前景。我们的耳朵和眼睛一样，也对高频不那么敏感（尽管我认为程度稍轻一些），但在语言领域，「高频」究竟意味着什么呢 12？考虑到基于似然的语言模型（likelihood-based language models）所取得的成功，扩散模型中对低噪声水平（low noise levels）相对较低的权重，在这种情况下真的会成为一个劣势吗？

### 03. Autoregression for language: a tough baseline to beat

Autoregression at the word or token level is a very natural way to do language modelling, because to some degree, it reflects how language is produced and consumed: as a one-dimensional sequence, one element at a time, in a particular fixed order. However, if we consider the process through which an abstract thought turns into an utterance, the iterative denoising metaphor starts to look more appealing. When writing a paragraph, the core concepts are generally decided on first, and the exact wording and phrasing doesn't materialise until later. That said, perhaps it doesn't matter precisely how humans interact with language: just like how planes don't fly the same way birds do (h/t Yann LeCun), the best way to build a practically useful language model need not reflect nature either.

语言的自回归：一个难以超越的基准在词语或 Token 层面的自回归（Autoregression）是一种非常自然的语言建模（Language modelling）方式，因为它在某种程度上反映了语言是如何被产生和理解的：它是一个一维序列，一次生成一个元素，并以特定的固定顺序排列。然而，如果我们考虑一个抽象思想如何转化为具体话语（Utterance）的过程，迭代去噪隐喻（Iterative denoising metaphor）开始显得更具吸引力。当撰写一个段落时，核心概念通常会先确定下来，而确切的措辞和表达方式则直到后期才逐渐成形。话虽如此，人类如何与语言互动或许并不那么重要：正如飞机并非以鸟类的方式飞行（h/t Yann LeCun）一样，构建一个实用的语言模型（Language model）的最佳方法也无需完全模仿自然。

Practically speaking, autoregressive models have an interface that is somewhat limited: they can be prompted, i.e. tasked to complete a sequence for which a prefix is given. While this has actually been shown to be reasonably versatile in itself, the ability of non-autoregressive models to fill in the blanks (i.e. be conditioned on something other than a prefix, also known as inpainting in the image domain) is potentially quite useful, and not something that comes naturally to autoregressive models (though it is of course possible to do infilling with autoregressive models13).

从实际应用来看，自回归模型（autoregressive models）的使用方式相对受限：它们通常只能通过「提示」来工作，即输入一个序列的前缀，然后让模型完成后续内容。虽然这种方式本身已被证明具有相当大的通用性，但非自回归模型（non-autoregressive models）具备的「完形填空」能力 —— 即除了前缀，还能基于其他上下文条件进行生成，这在图像领域也被称为图像修补（inpainting）—— 可能非常有用。这种能力并非自回归模型天生具备的（尽管通过一些方法，自回归模型也能实现类似的完形填空任务 13）。

#### 3.1 Training efficiency

If we compare autoregression and diffusion side-by-side as different forms of iterative refinement, the former has the distinct advantage that training can be parallelised trivially across all refinement steps. During autoregressive model training, we obtain a useful gradient signal from all steps in the sampling process. This is not true for diffusion models, where we have to sample a particular noise level for each training example. It is not practical to train on many different noise levels for each example, because that would require multiple forward and backward passes through the model. For autoregression, we get gradients for all sequence steps with just a single forward-backward pass.

训练效率如果我们将自回归（autoregression）和扩散（diffusion）模型作为不同形式的迭代细化方法进行比较，那么自回归模型有一个显著优势，那就是它的训练过程可以很容易地在所有细化步骤中并行进行。在自回归模型训练期间，我们能够从采样过程中的所有步骤获取有效的梯度信号。然而，扩散模型则不同，它需要我们为每个训练样本抽取一个特定的噪声水平。对每个样本使用多种不同的噪声水平进行训练是不现实的，因为这会要求模型进行多次前向传播和反向传播。而对于自回归模型，我们只需一次前向传播和反向传播，就能获得所有序列步骤的梯度信息。

As a result, diffusion model training is almost certainly significantly less statistically efficient than autoregressive model training, and slower convergence implies higher computational requirements.

因此，扩散模型（diffusion model）在训练时的统计效率几乎肯定远低于自回归模型（autoregressive model）的训练，而收敛速度较慢也意味着需要更高的计算资源。

#### 3.2 Sampling efficiency

Sampling algorithms for diffusion models are very flexible: they allow for sample quality and computational cost to be traded off without retraining, simply by changing the number of sampling steps. This isn't practical with autoregressive models, where the number of sampling steps is tied directly to the length of the sequence that is to be produced. On the face of it, diffusion models are at an advantage here: perhaps we can get high-quality samples with a number of steps that is significantly lower than the sequence length?

采样效率扩散模型的采样算法（sampling algorithms）非常灵活：它们无需重新训练，只需调整采样步数，就能在样本质量和计算成本之间进行权衡。这对于自回归模型（autoregressive models）来说并不实用，因为它们的采样步数与要生成的序列长度直接挂钩。从这个角度来看，扩散模型在这里占据了优势：也许我们能以远低于序列长度的步数，获得高质量的样本？

For long enough sequences, this is probably true, but it is important to compare apples to apples. Simply comparing the number of sampling steps across different methods relies on the implicit assumption that all sampling steps have the same cost, and this is not the case. Leaving aside the fact that a single diffusion sampling step can sometimes require multiple forward passes through the model, the cost of an individual forward pass also differs. Autoregressive models can benefit substantially from caching, i.e. re-use of activations computed during previous sampling steps, which significantly reduces the cost of each step. This is not the case for diffusion models, because the level of noise present in the input changes throughout sampling, so each sampling step requires a full forward pass across the entire input.

对于足够长的序列来说，这或许是真的，但重要的是要进行公平比较。仅仅比较不同方法之间的采样步数，其隐含的假设是所有采样步骤的成本都相同，而事实并非如此。暂且不提单个扩散（diffusion）采样步骤有时需要模型进行多次前向传播（forward pass），即使是每次前向传播的成本也各有差异。自回归（autoregressive）模型可以从缓存（caching）中显著受益，即重复使用在先前采样步骤中计算出的激活（activations），这能显著降低每个步骤的成本。但扩散模型的情况则不同，因为输入中的噪声（noise）水平在整个采样过程中都会发生变化，所以每个采样步骤都需要对完整输入进行一次前向传播。

Therefore, the break-even point at which diffusion sampling becomes more efficient than autoregressive sampling is probably at a number of steps significantly below the length of the sequence. Whether this is actually attainable in practice remains to be seen.

因此，扩散采样（diffusion sampling）效率超越自回归采样（autoregressive sampling）的盈亏平衡点，可能发生在远低于序列长度的步数时。至于这在实践中是否真能实现，仍有待观察。

#### 3.3 Why bother with diffusion at all?

我们为什么还要关注扩散模型？

The efficiency disadvantages with respect to autoregressive models might lead one to wonder if diffusion-based language modelling is even worth exploring to begin with. Aside from infilling capabilities and metaphorical arguments, there are a few other reasons why I believe it's worth looking into:

鉴于扩散模型在效率方面相对于自回归模型（autoregressive models）处于劣势，人们可能会疑惑，基于扩散的语言建模（diffusion-based language modelling）是否还值得我们从头开始探索。除了它出色的填充能力（infilling capabilities）和一些比喻性的论证外，我认为还有以下几点原因值得我们深入探讨：

* Unlike autoregressive models, which require restricted connectivity patterns to ensure causality (usually achieved by masking), diffusion model architectures are completely unconstrained. This enables a lot more creative freedom, as well as potentially benefiting from architectural patterns that are common in other application domains, such as using pooling and upsampling layers to capture structure at multiple scales. One recent example of such creativity is Recurrent Interface Networks14, whose Perceiver IO-like15 structure enables efficient re-use of computation across sampling steps.

*  与自回归模型不同 —— 自回归模型需要受限制的连接模式来确保因果关系（通常通过掩码实现），扩散模型（diffusion model）的架构则完全不受约束。这不仅带来了更多的创作自由，还可能受益于在其他应用领域常见的架构模式，例如使用池化（pooling）和上采样（upsampling）层来捕捉多尺度结构。这种创造力的一个近期例子是循环接口网络（Recurrent Interface Networks）[14]，其类似 Perceiver IO [15] 的结构，使得在不同采样步骤之间能够高效地复用计算。

* The flexibility of the sampling procedure extends beyond trading off quality against computational cost: it can also be modified to amplify the influence of conditioning signals (e.g. through classifier-free guidance), or to include additional constraints without retraining. Li et al.16 extensively explore the latter ability for text generation (e.g. controlling sentiment or imposing a particular syntactic structure).

采样（sampling）过程的灵活性不仅仅局限于在质量和计算成本之间进行权衡：它还可以通过修改来增强条件信号（conditioning signals）的影响（例如通过无分类器指导（classifier-free guidance）），或者在不进行再训练（retraining）的情况下引入额外约束（constraints）。Li 等人 [16] 深入探讨了这种能力在文本生成（text generation）中的广泛应用（例如控制文本情感（sentiment）或强制设定特定的句法结构（syntactic structure））。

* Who knows what other perks we might uncover by properly exploring this space? The first few papers on diffusion models for images struggled to match results obtained with more established approaches at the time (i.e. GANs, autoregressive models). Work on diffusion models in new domains could follow the same trajectory – if we don't try, we'll never know.

* 谁又能知道，通过充分探索这一领域，我们还会发现哪些意想不到的惊喜呢？早期关于图像扩散模型（diffusion models）的几篇论文，在成果上曾难以企及当时更成熟的方法（例如 GANs 和自回归模型）。而扩散模型在新领域中的发展，很可能也会遵循相同的路径 —— 如果我们不去尝试，就永远不会知道它的潜力。

### 04. Diffusion for discrete data

Diffusion models operate on continuous inputs by default. When using the score-based formalism, continuity is a requirement because the score function \(\nabla_\mathbf{x} \log p(\mathbf{x})\) is only defined when \(\mathbf{x}\) is continuous. Language is usually represented as a sequence of discrete tokens, so the standard formulation is not applicable. Broadly speaking, there are two ways to tackle this apparent incompatibility:

扩散模型如何处理离散数据扩散模型（Diffusion models）默认是应用于连续输入的。当采用基于分数的框架（score-based formalism）时，连续性（continuity）是一项基本要求，因为分数函数 \(\nabla_\mathbf {x} \log p（\mathbf {x})\）仅在 \(\mathbf {x}\）为连续变量时才有定义。然而，语言通常被表示为离散的 token 序列，因此标准的扩散模型公式并不适用。概括来说，有两种方法可以解决这种明显的不兼容性问题：

* formulate a discrete corruption process as an alternative to Gaussian diffusion;

* map discrete inputs to continuous vectors and apply Gaussian diffusion in that space.

*  提出一种离散破坏过程（discrete corruption process）作为高斯扩散（Gaussian diffusion）的替代方案；
*  将离散输入映射到连续向量，并在该连续向量空间中应用高斯扩散。

The former approach has been explored extensively: D3PM17, MaskGIT18, Mask-predict19, ARDM20, Multinomial diffusion21, DiffusER22 and SUNDAE23 are all different flavours of non-autoregressive iterative refinement using a discrete corruption process. Many (but not all) of these works focus on language modelling as the target application. It should be noted that machine translation has been particularly fertile ground for this line of work, because the strong conditioning signal makes non-autoregressive methods attractive even when their ability to capture diversity is relatively limited. Several works on non-autoregressive machine translation predate the rise of diffusion models.

此前，这类方法已被广泛探索：D3PM [17]、MaskGIT [18]、Mask-predict [19]、ARDM [20]、Multinomial diffusion [21]、DiffusER [22] 和 SUNDAE [23] 都是利用离散损坏过程进行非自回归迭代细化的不同变体。其中许多（但并非全部）工作都将语言建模作为主要应用方向。值得注意的是，机器翻译一直是这类研究的沃土，因为其强大的条件信号使得非自回归方法备受青睐，即便它们捕捉多样性的能力相对有限。事实上，一些关于非自回归机器翻译的研究甚至早于扩散模型（diffusion models）的兴起。

Unfortunately, moving away from the standard continuous formulation of diffusion models tends to mean giving up on some useful features, such as classifier-free guidance and the ability to use various accelerated sampling algorithms developed specifically for this setting. Luckily, we can stick with continuous Gaussian diffusion simply by embedding discrete data in Euclidean space. This approach has recently been explored for language modelling. Some methods, like self-conditioned embedding diffusion (SED)24, use a separate representation learning model to obtain continuous embeddings corresponding to discrete tokens; others jointly fit the embeddings and the diffusion model, like Diffusion-LM16, CDCD25 and Difformer26.

然而，如果偏离扩散模型的标准连续公式（continuous formulation），往往就意味着要放弃一些有用的特性，比如无分类器引导（classifier-free guidance）以及使用专门为此类设定开发的各种加速采样算法（accelerated sampling algorithms）的能力。幸运的是，我们仍然可以沿用连续高斯扩散（continuous Gaussian diffusion），只需将离散数据嵌入（embedding）到欧几里得空间（Euclidean space）即可。这种方法最近在语言建模（language modelling）领域得到了探索。一些方法，例如自条件嵌入扩散（self-conditioned embedding diffusion，SED）[24]，会使用一个单独的表征学习模型（representation learning model）来获取与离散 Token 相对应的连续嵌入；而另一些方法则会联合拟合（fit）嵌入和扩散模型，比如 Diffusion-LM [16]、CDCD [25] 和 Difformer [26]。

Continuous diffusion for categorical data (CDCD) is my own work in this space: we set out to explore how diffusion models could be adapted for language modelling. One of the goals behind this research project was to develop a method for diffusion language modelling that looks as familiar as possible to language modelling practitioners. Training diffusion models is a rather different experience from training autoregressive Transformers, and we wanted to minimise the differences to make this as approachable as possible. The result is a model whose training procedure is remarkably close to that of BERT27: the input token sequence is embedded, noise is added to the embeddings, and the model learns to predict the original tokens using the cross-entropy loss (score interpolation). The model architecture is a standard Transformer. We address the issue of finding the right weighting for the different noise levels with an active learning strategy (time warping), which adapts the distribution of sampled noise levels on the fly during training.

用于分类数据的连续扩散（Continuous diffusion for categorical data，CDCD）是我在这方面开展的工作：我们着手探索扩散模型如何应用于语言建模。这项研究项目的一个目标是开发一种扩散语言建模方法，使其尽可能贴近语言建模从业者所熟悉的方式。训练扩散模型与训练自回归 Transformer（Transformer）有着截然不同的体验，我们希望尽量减少这些差异，使其尽可能易于上手。最终，我们得到的模型其训练过程与 BERT27 非常相似：输入 Token 序列被嵌入，然后噪声被添加到这些嵌入中，模型通过交叉熵损失（cross-entropy loss）（得分插值，score interpolation）来学习预测原始 Token。模型架构是一个标准的 Transformer。我们通过一种主动学习策略（例如时间扭曲，time warping）解决了为不同噪声水平寻找合适权重的问题，该策略能够在训练过程中动态调整采样噪声水平的分布。

Another way to do language modelling with Gaussian diffusion, which to my knowledge has not been explored extensively so far, is to learn higher-level continuous representations rather than embed individual tokens. This would require a powerful representation learning approach that learns representations that are rich enough to be decoded back into readable text (potentially by a light-weight autoregressive decoder). Autoencoders applied to token sequences tend to produce representations that fail to capture the least predictable components of the input, which carry precisely the most salient information. Perhaps contrastive methods, or methods that try to capture the dynamics of text (such as Time Control28) could be more suitable for this purpose.

利用高斯扩散（Gaussian diffusion）进行语言建模（language modelling）的另一种方法 —— 据我所知，这种方法目前尚未得到广泛探索 —— 是学习更高层次的连续表示（continuous representations），而不是去嵌入单个 token。这将需要一种强大的表示学习（representation learning）方法，它能够学习到足够丰富的表示，从而可以被解码回可读文本（可能通过一个轻量级自回归解码器（light-weight autoregressive decoder）完成）。将自动编码器（Autoencoders）应用于 token 序列时，它们产生的表示往往无法捕捉输入中最不可预测的成分，而这些成分恰恰携带着最关键的信息。也许对比方法，或者那些试图捕捉文本动态的方法（例如 Time Control28），会更适合这项任务。

### 05. Closing thoughts

总结与展望

While CDCD models produce reasonable samples, and are relatively easy to scale due to their similarity to existing language models, the efficiency advantages of autoregression make it a very tough baseline to beat. I believe it is still too early to consider diffusion as a serious alternative to autoregression for generative language modelling at scale. As it stands, we also know next to nothing about scaling laws for diffusion models. Perhaps ideas such as latent self-conditioning14 could make diffusion more competitive, by improving computational efficiency, but it's not clear that this will be sufficient. Further exploration of this space has the potential to pay off handsomely!

CDCD 模型虽然能生成质量不错的样本，并且由于与现有语言模型相似，因此相对容易扩展，但自回归（autoregression）在效率上的优势，使其成为一个难以企及的强大基准（baseline）。我认为，在大规模生成语言建模领域，目前将扩散（diffusion）模型视为自回归的真正替代方案还为时过早。现阶段，我们对扩散模型的规模化法则（scaling laws）也知之甚少。或许像潜在自条件作用（latent self-conditioning）[14] 这样的新思路，能通过提高计算效率，让扩散模型更具竞争力，但目前尚不清楚这是否足以弥补差距。因此，进一步深入探索这一领域，有望带来丰硕的成果！

All in all, I have become convinced that the key to powerful generative models is iterative refinement: rather than generating a sample in a single pass through a neural network, the model is applied repeatedly to refine a canvas, and hence the unrolled sampling procedure corresponds to a much "deeper" computation graph. Exactly which algorithm one uses to achieve this might not matter too much in the end, whether it be autoregression, diffusion, or something else entirely. I have a lot more thoughts about this, so perhaps this could be the subject of a future blog post.

总的来说，我深信强大生成模型（generative models）的关键在于迭代细化（iterative refinement)：模型不是在神经网络（neural network）中通过一次遍历就生成样本，而是被反复应用于逐步细化一个「画布」。因此，这种展开的采样过程（sampling procedure）实际上对应着一个「更深」的计算图（computation graph）。最终，实现这一目标的具体算法可能没有那么重要，无论是自回归（autoregression）、扩散（diffusion），还是其他完全不同的方法。关于这一点，我还有很多思考，或许可以作为未来一篇博客文章的主题。

On an unrelated note: I've disabled Disqus comments on all of my blog posts, as their ads seem to have gotten very spammy. I don't have a good alternative to hand right now, so in the meantime, feel free to tweet your thoughts at me instead @sedielem, or send me an email. When I eventually revamp this blog at some point in the future, I will look into re-enabling comments. Apologies for the inconvenience!

另外提一句：我已在我所有的博客文章上禁用了 Disqus 评论，因为他们的广告似乎已经变得非常泛滥。我目前没有合适的替代方案，所以与此同时，欢迎你随时在 Twitter 上 @sedielem 给我留言分享你的想法，或者给我发送电子邮件。未来我对博客进行改版时，我会考虑重新启用评论功能。对此造成的不便，敬请谅解！

UPDATE (April 7): I have reenabled Disqus comments.

If you would like to cite this post in an academic context, you can use this BibTeX snippet:

更新（4 月 7 日）：我已经重新启用了 Disqus 评论功能。

如果你希望在学术场合引用这篇博文，可以使用以下 BibTeX 片段：









```
@misc{dieleman2023language,
 author = {Dieleman, Sander},
 title = {Diffusion language models},
 url = {https://benanne.github.io/2023/01/09/diffusion-language.html},
 year = {2023}
}
```

### Acknowledgements

Thanks to my collaborators on the CDCD project, and all my colleagues at DeepMind.

### References

1. Brock, Donahue, Simonyan, "Large Scale GAN Training for High Fidelity Natural Image Synthesis", International Conference on Learning Representations, 2019. ↩

2. Karras, Laine, Aittala, Hellsten, Lehtinen, Aila, "Analyzing and Improving the Image Quality of StyleGAN", Computer Vision and Pattern Recognition, 2020. ↩

3. Razavi, van den Oord and Vinyals, "Generating Diverse High-Fidelity Images with VQ-VAE-2", Neural Information Processing Systems, 2019. ↩

4. Esser, Rombach and Ommer, "Taming Transformers for High-Resolution Image Synthesis", Computer Vision and Pattern Recognition, 2021. ↩

5. van den Oord, Vinyals and Kavukcuoglu, "Neural Discrete Representation Learning", Neural Information Processing Systems, 2017. ↩

6. Song and Ermon, "Generative Modeling by Estimating Gradients of the Data Distribution", Neural Information Processing Systems, 2019. ↩

7. Song and Ermon, "Improved Techniques for Training Score-Based Generative Models", Neural Information Processing Systems, 2020. ↩

8. Ho, Jain and Abbeel, "Denoising Diffusion Probabilistic Models", Neural Information Processing Systems, 2020. ↩

9. Dhariwal, Nichol, "Diffusion Models Beat GANs on Image Synthesis", Neural Information Processing Systems, 2021. ↩

10. Nichol, Dhariwal, Ramesh, Shyam, Mishkin, McGrew, Sutskever, Chen, "GLIDE: Towards Photorealistic Image Generation and Editing with Text-Guided Diffusion Models", arXiv, 2021. ↩

11. Song, Durkan, Murray, Ermon, "Maximum Likelihood Training of Score-Based Diffusion Models", Neural Information Processing Systems, 2021. ↩

12. Tamkin, Jurafsky, Goodman, "Language Through a Prism: A Spectral Approach for Multiscale Language Representations", Neural Information Processing Systems, 2020. ↩

13. Bavarian, Jun, Tezak, Schulman, McLeavey, Tworek, Chen, "Efficient Training of Language Models to Fill in the Middle", arXiv, 2022. ↩

14. Jabri, Fleet, Chen, "Scalable Adaptive Computation for Iterative Generation", arXiv, 2022. ↩ ↩2

15. Jaegle, Borgeaud, Alayrac, Doersch, Ionescu, Ding, Koppula, Zoran, Brock, Shelhamer, Hénaff, Botvinick, Zisserman, Vinyals, Carreira, "Perceiver IO: A General Architecture for Structured Inputs & Outputs", International Conference on Learning Representations, 2022. ↩

16. Li, Thickstun, Gulrajani, Liang, Hashimoto, "Diffusion-LM Improves Controllable Text Generation", Neural Information Processing Systems, 2022. ↩ ↩2

17. Austin, Johnson, Ho, Tarlow, van den Berg, "Structured Denoising Diffusion Models in Discrete State-Spaces", Neural Information Processing Systems, 2021. ↩

18. Chang, Zhang, Jiang, Liu, Freeman, "MaskGIT: Masked Generative Image Transformer", Computer Vision and Patern Recognition, 2022. ↩

19. Ghazvininejad, Levy, Liu, Zettlemoyer, "Mask-Predict: Parallel Decoding of Conditional Masked Language Models", Empirical Methods in Natural Language Processing, 2019. ↩

20. Hoogeboom, Gritsenko, Bastings, Poole, van den Berg, Salimans, "Autoregressive Diffusion Models", International Conference on Learning Representations, 2022. ↩

21. Hoogeboom, Nielsen, Jaini, Forré, Welling, "Argmax Flows and Multinomial Diffusion: Learning Categorical Distributions", Neural Information Processing Systems, 2021. ↩

22. Reid, Hellendoorn, Neubig, "DiffusER: Discrete Diffusion via Edit-based Reconstruction", arXiv, 2022. ↩

23. Savinov, Chung, Binkowski, Elsen, van den Oord, "Step-unrolled Denoising Autoencoders for Text Generation", International Conference on Learning Representations, 2022. ↩

24. Strudel, Tallec, Altché, Du, Ganin, Mensch, Grathwohl, Savinov, Dieleman, Sifre, Leblond, "Self-conditioned Embedding Diffusion for Text Generation", arXiv, 2022. ↩

25. Dieleman, Sartran, Roshannai, Savinov, Ganin, Richemond, Doucet, Strudel, Dyer, Durkan, Hawthorne, Leblond, Grathwohl, Adler, "Continuous diffusion for categorical data", arXiv, 2022. ↩

26. Gao, Guo, Tan, Zhu, Zhang, Bian, Xu, "Difformer: Empowering Diffusion Model on Embedding Space for Text Generation", arXiv, 2022. ↩

27. Devlin, Chang, Lee, Toutanova, "BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding", North American Chapter of the Association for Computational Linguistics, 2019. ↩

28. Wang, Durmus, Goodman, Hashimoto, "Language modeling via stochastic processes", International Conference on Learning Representations, 2022.