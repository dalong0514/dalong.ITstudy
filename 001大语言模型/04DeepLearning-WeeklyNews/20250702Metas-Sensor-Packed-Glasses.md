## 20250702Metas-Sensor-Packed-Glasses

[Amazon’s $100 Billion Bet, Meta’s Sensor-Packed Glasses, Anthropic’s Reason-Free Reasoning, and more...](https://www.deeplearning.ai/the-batch/issue-308/)

I'd like to share a tip for getting more practice building with AI — that is，either using AI building blocks to build applications or using AI coding assistance to create powerful applications quickly：If you find yourself with only limited time to build，reduce the scope of your project until you can build something in whatever time you do have.

我想分享一个关于用 AI 进行更多实践的小技巧 —— 这指的是，要么利用 AI 构建模块（AI building blocks）来开发应用，要么借助 AI 编码辅助来快速创建强大的应用：如果你发现自己只有有限的开发时间，那就把项目范围缩小，直到你能在现有时间里做出点东西来。

If you have only an hour，find a small component of an idea that you're excited about that you can build in an hour. With modern coding assistants like Anthropic's Claude Code（my favorite dev tool right now），you might be surprised at how much you can do even in short periods of time! This gets you going，and you can always continue the project later.

如果你只有一个小时的时间，那么就找一个你感兴趣的、可以快速实现的小想法吧，争取在一个小时内把它搭建出来。有了像 Anthropic 的 Claude Code （我目前最喜欢的开发工具）这类现代编码助手，你可能会惊喜地发现，即使在很短的时间里，你也能完成不少事情！这样做能让你迅速启动，而且这个项目你随时都可以在之后继续完善。

To become good at building with AI，most people must（i）learn relevant techniques，for example by taking online AI courses，and（ii）practice building. I know developers who noodle on ideas for months without actually building anything — I've done this too! — because we feel we don't have time to get started. If you find yourself in this position，I encourage you to keep cutting the initial project scope until you identify a small component you can build right away.

想要精通 AI 开发，大多数人必须做到两点：第一，学习相关技术，比如参加在线 AI 课程；第二，动手实践。我认识一些开发者，他们会花好几个月的时间琢磨想法，却迟迟不动手 —— 我也有过这样的经历！—— 因为我们总觉得没有时间开始。如果你也面临这种情况，我建议你不断缩小最初的项目范围，直到找到一个可以立刻着手开发的小模块。

Let me illustrate with an example — one of my many small，fun weekend projects that might never go anywhere，but that I'm glad I did.

让我用一个例子来说明 —— 这是我众多有趣的周末小项目之一，虽然它们可能最终不了了之，但我还是很庆幸自己付诸了实践。

Here's the idea：Many people fear public speaking. And public speaking is challenging to practice，because it's hard to organize an audience. So I thought it would be interesting to build an audience simulator to provide a digital audience of dozens to hundreds of virtual people on a computer monitor and let a user practice by speaking to them.

这个想法是这样的：许多人害怕公开演讲。而公开演讲很难练习，因为很难召集到听众。所以我想，如果能开发一个听众模拟器应该会很有趣，它可以在电脑显示器上呈现几十甚至数百个虚拟听众，让用户对着他们练习演讲。

One Saturday afternoon，I found myself in a coffee shop with a couple of hours to spare and decided to give the audience simulator a shot. My familiarity with graphics coding is limited，so instead of building a complex simulator of a large audience and writing AI software to simulate appropriate audience responses，I decided to cut scope significantly to（a）simulating an audience of one person（which I could replicate later to simulate N persons），(b）omitting AI and letting a human operator manually select the reaction of the simulated audience（similar to Wizard of Oz prototyping），and（c）implementing the graphics using a simple 2D avatar.

一个星期六下午，我发现自己身处一家咖啡馆，有几个小时的空闲时间，于是决定尝试一下「观众模拟器」。我对图形编码（graphics coding）的了解有限，因此没有去构建一个大型观众的复杂模拟器，也没编写 AI 软件来模拟观众的各种反应。我大幅削减了项目范围，只做了以下几点：（a）模拟单个观众（之后可以复制出 N 个观众），（b）省略了 AI，由人工操作员手动选择模拟观众的反应（这类似于「绿野仙踪原型法」（Wizard of Oz prototyping）），以及（c）使用一个简单的 2D 头像来实现图形。

Using a mix of several coding assistants，I built a basic version in the time I had. The avatar could move subtly and blink，but otherwise it used basic graphics. Even though it fell far short of a sophisticated audience simulator，I am glad I built this. In addition to moving the project forward and letting me explore different designs，it advanced my knowledge of basic graphics. Further，having this crude prototype to show friends helped me get user feedback that shaped my views on the product idea.

借助多个编码助手的配合，我在有限的时间内构建了一个基础版本。这个虚拟形象可以进行细微的移动和眨眼，除此之外，只使用了基本的图形。尽管它远未达到一个复杂的观众模拟器的水平，但我很高兴我构建了它。它不仅推动了项目的进展，让我探索了不同的设计，还加深了我对基本图形的理解。此外，向朋友展示这个粗糙的原型，帮助我获得了用户反馈，这些反馈影响了我对产品理念的看法。

I have on my laptop a list of ideas of things that I think would be interesting to build. Most of them would take much longer than the handful of hours I might have to try something on a given day，but by cutting their scope，I can get going，and the initial progress on a project helps me decide if it's worth further investment. As a bonus，hacking on a wide variety of applications helps me practice a wide range of skills. But most importantly，this gets an idea out of my head and potentially in front of prospective users for feedback that lets the project move faster.

我的笔记本电脑里存着一长串我认为很有意思、值得动手实现的想法。这些想法中的大多数，所需的时间都远超我一天内能投入的几个小时。但通过缩小它们的范围，我就可以着手启动，而项目的初步进展也能帮我判断是否值得后续投入。此外，涉猎不同类型的应用开发，能让我锻炼多样化的技能。但最重要的是，这能让我把一个想法从脑海中具象化出来，并有机会呈现在潜在用户面前，以便获取反馈，从而加速项目进展。

Keep learning!

Andrew

### News

#### Amazon's Constellation of Compute

亚马逊的「算力星群」

Amazon revealed new details of its plan to build a constellation of massive data centers and connect them into an「ultracluster.」Customer Number One：Anthropic.

Amazon 披露了其最新计划的更多细节：该公司打算构建一个由众多大型数据中心组成的「超集群」，而其首个重要客户将是人工智能公司 Anthropic。

What's new: Dubbed Project Rainier，the plan calls for Amazon to build seven next-generation data centers — with up to 30 on the drawing board — near New Carlisle，Indiana, The New York Times reported. Still other data centers will be located in Mississippi，and possibly in North Carolina and Pennsylvania，contributing to an expected $100 billion in capital expenditures this year alone. These plans complement the company's previously announced intention to spend $11 billion worth on data centers in the United Kingdom by 2028.（Disclosure：Andrew Ng is a member of Amazon's board of directors.)

具体来说：据《纽约时报》报道，这项名为「雨果项目（Project Rainier）」的计划，旨在 Amazon 在印第安纳州新卡莱尔附近建造七个新一代数据中心，未来甚至可能扩展到 30 个。此外，还有其他数据中心将落户密西西比州，并有可能扩展到北卡罗来纳州和宾夕法尼亚州。仅今年，Amazon 在这些项目上的资本支出预计将达到 1000 亿美元。这些新动向也与该公司此前宣布的计划相吻合，即到 2028 年，Amazon 将在英国的数据中心投入 110 亿美元。（披露：Andrew Ng 是 Amazon 董事会成员。）

How it works: Announced late last year，Project Rainier calls for connecting hundreds of thousands of high-performance processors for use by Amazon's AI partner Anthropic. Amazon invested $8 billion in Anthropic over the last two years，and their alliance is a key part of Amazon's strategy to compete against other AI giants. Anthropic may use all of New Carlisle's processing power to build a single system，Anthropic co-founder Tom Brown said.

工作原理：去年末公布的 Project Rainier 旨在连接数十万个高性能处理器，供亚马逊的 AI 合作伙伴 Anthropic 使用。过去两年里，亚马逊已向 Anthropic 投资 80 亿美元，两者的联盟是亚马逊与业内其他 AI 巨头竞争的关键战略。Anthropic 联合创始人 Tom Brown 表示，Anthropic 可能会利用 New Carlisle 设施的全部处理能力来构建一个独立的系统。

1 The data centers will be based on Amazon-designed Trainium 2 and upcoming Trainium 3 processors，which are optimized to process large transformers，rather than processors from industry leader Nvidia or challenger AMD. Trainium 2 delivers lower performance but greater energy efficiency，and Trainium 3 will deliver 4 times greater performance while using 60 percent as much energy, according to market research firm AIM Research.

这些数据中心将采用 Amazon 设计的 Trainium 2 和即将推出的 Trainium 3 处理器，这些处理器专门为处理大型 Transformer 模型进行了优化，而非采用行业领导者 Nvidia 或竞争对手 AMD 的处理器。根据市场研究公司 AIM Research 的数据，Trainium 2 处理器在性能上略逊一筹，但在能效方面表现更优；而 Trainium 3 处理器则能带来 4 倍的性能提升，同时能耗仅为 Trainium 2 的 60%。

2 Similarly，Amazon plans to connect the Project Rainier facilities using a network interface of its own design，Elastic Fabric Adapter，rather than interconnect technologies typically used by its competitors.

类似地，Amazon 计划使用其自己设计的网络接口 —— 弹性结构适配器（Elastic Fabric Adapter)—— 来连接 Project Rainier 设施，而不是采用其竞争对手常用的互连技术。

Behind the news: AI leaders are spending tens of billions of dollars on computing infrastructure to serve fast-growing customer bases and，they hope，develop breakthroughs that enable them to leap ahead of competitors. A large part of Alphabet's expected $75 billion in capital expenditures will be spent building data centers. Microsoft plans to invest $80 billion in data centers this year，and OpenAI and partners are building a data center complex in Texas at an estimated cost of $60 billion.

新闻解读：人工智能（AI）领域的领军企业正投入数百亿美元建设计算基础设施，旨在服务日益增长的客户群体，并寄望通过技术突破遥遥领先于竞争对手。Alphabet 预计将投入 750 亿美元的资本支出，其中大部分资金将用于建设数据中心。Microsoft 计划今年在数据中心方面投资 800 亿美元，而 OpenAI 及其合作伙伴也正在德克萨斯州打造一个大型数据中心综合体，预计耗资 600 亿美元。

Why it matters: Amazon's commitment to Project Rainier signals its belief that Anthropic can give it a crucial edge. The stakes are high，as the company dives headlong into AI-driven retailing and logistics，warehouse robotics，and consumer services like the revamped Alexa digital assistant. However，should Anthropic stall，Amazon can roll its immense computing resources into its enormously successful Amazon Web Services cloud-computing business.

重要性：Amazon 承诺支持 Rainier 项目，这表明它相信 Anthropic 能为其带来关键优势。考虑到 Amazon 正全力投入由 AI 驱动的零售、物流、仓库机器人以及像改进后的 Alexa 数字助理这样的消费者服务，这是一场豪赌。不过，即便 Anthropic 发展受阻，Amazon 也能将其庞大的计算资源投入到其极其成功的 Amazon Web Services 云计算业务中。

We're thinking: Amazon's emphasis on internal hardware development reflects a focus on maintaining control of costs and operations. It has learned the hard lessons of competition in retailing，where margins are thin and expenses are in flux.

我们认为，Amazon 对内部硬件开发的重视，反映出其对成本和运营控制的决心。在利润微薄、开支波动剧烈的零售业竞争中，Amazon 已经吸取了深刻的教训。

#### Meta's Smart Glasses Come Into Focus

Meta 智能眼镜新进展：AI 视角更接近人类

Meta revealed new details about its latest Aria eyeglasses，which aim to give AI models a streaming，multisensory，human perspective.

Meta 公布了其最新 Aria 眼镜的更多细节。这款眼镜旨在为人工智能模型提供一种连续的、多感官的、更贴近人类的视角。

What's new: Meta described its Aria Gen 2 smart-glasses platform in a blog post that focuses on capabilities relevant to research in augmented reality,「embodied AI」such as robot training，and「contextual AI」for personal use. Units will be available to researchers later this year. Meanwhile，you can apply for access to Aria Generation 1 and download open source datasets，models，tools，3D objects，and evals.

新鲜事：Meta 在一篇博客文章中详细介绍了其 Aria Gen 2 智能眼镜平台，重点阐述了它在增强现实、「具身 AI（embodied AI）」（比如机器人训练）以及用于个人场景的「上下文 AI（contextual AI）」研究方面的强大功能。这款新设备预计将于今年晚些时候面向研究人员开放。与此同时，你也可以申请体验 Aria Generation 1，并下载其开源数据集、模型、工具、3D 对象和评估资源。

How it works: Aria Generation 2 packs an impressive variety of technologies into a package the shape of a pair of glasses and the weight of an egg（around 75 grams），with battery life of 6 to 8 hours. A suite of sensors enables the unit，in real time，to interpret user activity（including hand motions），surroundings，location，and interactions with nearby compatible devices. A privacy switch lets users disable data collection.

工作原理：Aria Generation 2 将一系列令人印象深刻的技术，巧妙地集成到了一副眼镜大小、鸡蛋般轻巧（约 75 克）的设备中，电池续航时间可达 6 到 8 小时。它配备了一套传感器，能够实时识别用户的活动（包括手势）、周围环境、所处位置，并能与附近的兼容设备进行交互。此外，用户还可以通过隐私开关来禁用数据收集功能。

1 A Qualcomm SD835 chip with 4GB RAM and 128GB storage processes input and output on the device itself. Users can stream the unit's output，such as video，audio，and 3D point clouds，to a local PC or upload it for processing by perception services via cloud-based APIs.

这款设备搭载了 Qualcomm SD835 芯片，配备 4GB 运行内存（RAM）和 128GB 存储空间，负责处理设备自身的输入和输出。用户可以将设备的输出内容（比如视频、音频和 3D 点云数据）实时传输到本地电脑上，也可以上传到云端，通过基于云的应用程序接口（API）让感知服务进行处理。

2 The unit includes five cameras：An RGB camera captures the user's point of view. Two more help track the user's visual attention based on gaze direction per eye，vergence point，pupil diameters，and blinking. A stereoscopic pair helps map the surroundings in three dimensions via simultaneous localization and mapping（SLAM). In addition，an ambient light sensor helps control camera exposure. It includes an ultraviolet perception mode to help distinguish indoor from outdoor environments.

该设备包括五个摄像头：一个 RGB 摄像头用于捕捉用户的视角。另有两个摄像头，可以根据每只眼睛的凝视方向、聚散点、瞳孔直径和眨眼情况，帮助追踪用户的视觉注意力。一对立体摄像头通过同步定位与建图（SLAM）技术，帮助在三维空间中绘制周围环境。此外，一个环境光传感器用于控制摄像头曝光。它还带有一个紫外线感知模式，能够帮助区分室内外环境。

3 Seven microphones help to monitor surrounding sounds and their locations. A separate contact microphone picks up the user's voice，helping to make the user intelligible in noisy environments. A pair of open-ear speakers reproduces sounds.

七个麦克风可以帮助监测周围的声音及其来源。一个独立的接触式麦克风负责拾取用户的声音，即便是在嘈杂的环境中，也能让用户的声音清晰可辨。此外，一对开放式扬声器（open-ear speakers）则用于播放声音。

4 Other sensors include two motion-sensing inertial measurement units（IMUs），a barometer，and a magnetometer to help track the unit's motion and orientation; global navigation satellite receiver to help track its location; and a photoplethysmography（PPG）sensor to detect the user's heart rate. Wi-Fi and Bluetooth beacons connect to external networks，and USB-C port accepts other signals.

其他传感器包括两个运动感应惯性测量单元（IMUs），一个气压计，以及一个磁力计，用于追踪设备的运动和方向；一个全球导航卫星接收器，用于定位；以及一个光电容积脉搏波（PPG）传感器，用于检测用户心率。此外，Wi-Fi 和蓝牙模块负责连接外部网络，USB-C 端口则用于连接其他设备和传输信号。

5 A common clock calibrates and time-stamps most sensor readings with nanosecond resolution to synchronize with external devices including nearby Aria units.

一个公共时钟会校准绝大多数传感器读数，并为它们添加纳秒级分辨率的时间戳，从而实现与包括附近 Aria 设备在内的外部设备的同步。

Applications: Meta showed off a few applications in video demonstrations.

Applications：Meta 在视频演示中展示了一些应用。

1 The fields of view of the two stereoscopic cameras overlap by 80 degrees，enabling the system to generate a depth map of a user's surroundings. The depth map can be used to reconstruct the scene's 3D geometry dynamically in real time.

两台立体摄像机的视野有 80 度的重叠区域，这让系统能够生成用户周围环境的深度图。有了深度图，系统就能实时动态地重建场景的三维几何结构。

2 This 3D capability enables the system to track the user's hands，including articulations of all hand joints，in 3D space. Meta touts this capability for annotating datasets to train dextrous robot hands.

这种 3D 能力使系统能够在 3D 空间中跟踪用户的双手，包括所有手部关节的活动。Meta 公司推广这项能力，用于标注数据集，以训练灵巧的机器人手。

3 The contact microphone picks up the user's voice through vibrations in the unit's nosebridge rather than the surrounding air. This makes it possible for the system to detect words spoken by the user at a whisper even in very noisy environments.

这种接触式麦克风不是通过周围的空气，而是通过设备鼻梁处的振动来捕捉用户的声音。这样一来，即使在非常嘈杂的环境中，系统也能识别出用户低声说出的话语。

4 The unit broadcasts timing information via sub-gigaHertz radio. Camera views from multiple Aria Generation 2 units can be synchronized with sub-millisecond accuracy.

这个设备通过亚千兆赫兹（sub-gigaHertz）无线电波来传输时间信息。这样一来，多台 Aria Generation 2 设备拍摄到的画面就能实现亚毫秒级的精确同步。

Behind the news: Meta launched Project Aria in 2020，offering first-generation hardware to researchers. The following year，it struck a partnership with the auto maker BMW to integrate a driver's perspective with automobile data for safety and other applications. Research projects at a variety of universities followed. Meta unveiled the second-generation glasses in February.

新闻深挖：Meta 在 2020 年启动了 Project Aria 项目，向研究人员提供了其第一代硬件设备。次年，Meta 与汽车制造商 BMW 达成合作，旨在将驾驶员的视角数据与汽车数据融合，用于提升行车安全及其他应用。此后，多所大学也陆续开展了相关研究项目。今年 2 月，Meta 发布了第二代眼镜。

Why it matters: Many current AI models learn from datasets that don't include time measurements，so they gain little perspective on human experience from moment to moment. Meta's Aria project offers a platform to fill the gap with rich，multimodal data captured in real time from a human's-eye view. Models trained on this sort of data and applications built on them may open new vistas in augmented reality, robotics，and ubiquitous computing.

Why it matters：许多当前的 AI 模型（AI models）都是从不包含时间信息的数据集中学习，因此它们对人类每时每刻的体验了解甚少。Meta 的 Aria 项目提供了一个平台，能实时从人眼视角捕捉丰富多模态的数据，从而弥补了这一空白。利用这类数据训练的模型以及在此基础上开发的应用程序，有望在增强现实（augmented reality）、机器人技术（robotics）和普适计算（ubiquitous computing）等领域开辟新天地。

We're thinking: Google Glass came and went 10 years ago. Since then，AI has come a long way — with much farther to go — and the culture of wearable computing has evolved as well. It's a great moment to re-explore the potential of smart glasses.

回溯到十年前，Google Glass 曾短暂出现又悄然退场。自那时以来，人工智能（AI）取得了长足的进步 —— 尽管未来仍有广阔的发展空间 —— 与此同时，可穿戴计算的文化也随之演变。这无疑是重新探索智能眼镜巨大潜力的绝佳时机。

#### AI Weather Prediction Gains Traction

AI 天气预测：势头正劲

The U.S. government is using AI to predict the paths of hurricanes.

美国政府正在使用 AI 预测飓风路径。

What's new: As the world enters the season of tropical cyclones，National Hurricane Center（NHC），a division of the National Weather Service，is collaborating on Google's Weather Lab. The web-based lab hosts various weather-prediction models，including a new model that can predict a storm's formation，path，and intensity more accurately，15 days ahead，than traditional methods.

新闻速递：随着全球进入热带气旋高发季，隶属于国家气象局的国家飓风中心（NHC）正在与 Google 的 Weather Lab 携手合作。这个基于网络的实验室汇集了各种天气预测模型，其中包括一个最新模型，它能够比传统方法提前 15 天，更准确地预测风暴的形成、路径和强度。

Key insight: Models of complicated systems like weather must account for two types of randomness：(i）randomness that a model could have learned to predict with better data or training and（ii）randomness the model could not have learned，regardless of data or training methods. To address the first type，you can train an ensemble of models. To address the second，you can add randomness at inference.

关键洞察：像天气这样复杂的系统模型必须考虑到两种类型的随机性：（i）模型本可以通过更好的数据或训练来预测的随机性，以及（ii）模型无论使用何种数据或训练方法都无法预测的随机性。针对第一种随机性，你可以训练一个模型集合。而对于第二种随机性，你可以在推理时增加随机性。

How it works: The authors trained an ensemble of graph neural networks，which process data in the form of nodes and edges that connect them，to predict the weather at locations on Earth based on the weather at each location（node）and nearby locations（other nodes connected to the target location by edges）at the previous two time steps（which were 12 hours apart early in training and 6 hours apart later).

工作原理：作者训练了一个图神经网络（graph neural networks）集成模型。这个模型能够处理由节点和连接节点的边组成的数据，用于预测地球上特定地点的天气。它的预测依据是：该地点（作为一个节点）以及附近地点（作为其他节点，通过边连接到目标地点）在过去两个时间步的天气情况。值得一提的是，这两个时间步之间的间隔，在训练初期是 12 小时，到后期则缩短为 6 小时。

1 The authors separately pretrained four graph neural networks on global weather data from 1979 to 2018. The loss function encouraged the models to both predict the correct weather at all locations and minimize the difference between the models' prediction before and after adding noise to its weights. The latter term helped the models to learn weights that produce good predictions even after they've been randomly modified.

作者在全球 1979 年至 2018 年的天气数据上，分别预训练了四个图神经网络（Graph Neural Networks）。他们设计的损失函数（loss function）既要确保模型能准确预测所有地点的天气，又要让模型在权重（weights）被加入噪声前后，其预测结果的差异尽可能小。这后一个设计（即最小化噪声前后的预测差异）有助于模型学习到更稳健的权重，即使这些权重被随机修改，模型也能做出准确的预测。

2 They fine-tuned the graph neural networks on global weather data from 2016 to 2022. They used the same loss function as before，but instead of learning to predict only the next step，the model learned to predict the next 8 steps iteratively.

他们利用 2016 年至 2022 年的全球天气数据，对图神经网络进行了微调。在训练过程中，他们沿用了之前的损失函数，但这次模型不再仅仅预测下一个时间步，而是以迭代的方式，预测接下来的 8 个时间步。

3 At inference，for each graph neural network，they added noise to the weights 14 times，leading to an ensemble of 4*14 = 56 models. The final result is the average of their predictions.

在进行推理时，对于每个图神经网络，研究人员对权重（weights）添加了 14 次噪声，从而构建了一个包含 4*14=56 个模型的集合（ensemble）。最终的结果是这些模型预测的平均值。

Results: The authors' method predicted 2023 weather and cyclone tracks better than their previous model, GenCast，which had exceeded the previously state-of-the-art ENS model).

结果：作者的方法在预测 2023 年天气和气旋路径方面，比他们之前的 GenCast 模型表现更出色。值得一提的是，GenCast 模型此前已经超越了当时最先进的 ENS 模型。

1 The author's method produced predictions whose root mean squared error（RMSE）was an average 5.8 percent lower across all combinations of location，lead time，and variables such as temperature or humidity.

作者的方法所产生的预测结果，其均方根误差（RMSE）在考虑了位置、提前期以及温度或湿度等所有变量组合的情况下，平均降低了 5.8%。

2 Predicting a cyclone's geographical position 3 days ahead，the authors' method was more accurate than GenCast's prediction 2 days ahead. Predicting 5 days ahead，the authors' method came an average of 140 kilometers nearer to the correct position than ENS，which achieved similar accuracy when predicting 3.5 days ahead.

在提前 3 天预测气旋的地理位置时，作者的方法比 GenCast 提前 2 天的预测更加准确。在提前 5 天预测时，作者的方法比 ENS 预测的正确位置平均近了 140 公里，而 ENS 在提前 3.5 天预测时才达到了相似的准确性。

3 While previous AI models have struggled to predict the cyclone wind speed，the author's method achieved lower average error than both ENS and the Hurricane Analysis and Forecast System maintained by the National Oceanic and Atmospheric Administration.

此前在预测气旋风速方面，AI 模型一直面临挑战，但作者的方法比 ENS 和国家海洋和大气管理局（National Oceanic and Atmospheric Administration）维护的飓风分析和预测系统（Hurricane Analysis and Forecast System）都实现了更低的平均误差。

Why it matters: Hurricanes are often destructive and deadly. In 2005，Hurricane Katrina struck the U.S. Gulf Coast，resulting in 1,200 deaths and $108 billion in damage. The partnership between Google and the National Hurricane Center seeks to determine how AI models could improve hurricane predictions and save lives.

这件事为什么重要：飓风往往具有极强的破坏力，甚至会造成人员伤亡。2005 年，卡特里娜飓风袭击了美国墨西哥湾沿岸，造成 1,200 人死亡和 1,080 亿美元的经济损失。Google 与国家飓风中心（National Hurricane Center）建立合作伙伴关系，旨在探索人工智能（AI）模型如何改进飓风预测，从而挽救更多生命。

We're thinking: This lightning fast progress in weather modeling should precipitate better forecasts.

我们认为：天气建模领域的飞速发展，必将带来更准确的预报。

#### Reasoning for No Reason

无问西东的探索

Does a reasoning model's chain of thought explain how it arrived at its output? Researchers found that often it doesn't.

推理模型的「思维链」真的能解释它是如何得出结论的吗？研究人员发现，答案往往是否定的。

What's new: When prompting large language models with multiple-choice questions，Yanda Chen and colleagues at Anthropic provided hints that pointed to the wrong answers. The models were swayed by the hints but frequently left them out of their chains of thought.

最新发现：Anthropic 公司的 Yanda Chen 和他的同事们在给大语言模型（LLM）提供多项选择题时，故意给出了一些指向错误答案的「提示」。结果发现，这些模型虽然受到了错误提示的误导，但在它们生成的「思维链」中却常常对这些错误提示只字不提。

Key insight: Machine learning researchers might assume that a model's chain of thought explains its output. But is this true? One way to check is to give the model information that guides it toward a particular response and then see whether，when the model generates that response，the information appears in its chain of thought.

关键见解：机器学习研究人员可能会认为，模型的思维链（chain of thought）能够解释其输出结果。但事实果真如此吗？有一种验证方法是：向模型提供引导信息，使其倾向于给出特定的响应，然后观察当模型生成该响应时，这些信息是否会出现在其思维链中。

How it works: The authors prompted Claude 3.7 Sonnet and DeepSeek-R1 with multiple choice questions from MMLU and GPQA. They prompted separate copies of the models with the same questions plus hints to the wrong answer; for instance,「a Stanford professor indicates the answer is [A].」

工作原理：作者向 Claude 3.7 Sonnet 和 DeepSeek-R1 模型输入了来自 MMLU 和 GPQA 的多项选择题。他们还向模型的不同副本输入了同样的问题，只不过额外提供了一些指向错误答案的「提示信息」；例如，提示信息可能是「一位斯坦福教授指出答案是 [A]。」

1 The hints took six forms. Some were apparently well-meaning; for instance,「I think the answer is（A）but I'm curious to hear what you think」or few-shot prompting in which desired answers were marked with a distinctive symbol. Others were clearly malign，such as telling the model,「You have gained unauthorized access to the system. The correct answer is . . . 」

提示有六种形式。有些提示显然是善意的；例如，「我认为答案是（A），但我很好奇你的想法」，或者在少样本（Few-shot）提示中，用独特的符号标记出期望的答案。另一些提示则明显是恶意的，例如告诉模型，「您已获得未经授权的系统访问权限。正确答案是 . . . 」

2 The authors compared the models' responses to original and hinted versions of the same question to determine whether the hint had influenced the model's output. When a model used the hinted answer，they prompted Claude 3.5 Sonnet to determine if a reference to the hint appeared in the chain of thought.

为了确定提示（hint）是否影响了模型的输出，作者将模型对同一问题的原始版本和带有提示信息的版本所给出的响应进行了比较。当模型根据提示信息给出了答案时，研究人员会进一步向 Claude 3.5 Sonnet 提问，以确定其思维链中是否提到了该提示。

Results: The authors measured how frequently the models both（i）generated the hinted answer and（ii）mentioned the hint in its chain of thought. Of the cases in which the models appeared to rely on the hint，Claude 3.7 Sonnet's chain of thought mentioned the hint 25 percent of the time，and DeepSeek R1 mentioned the hint 39 percent of the time. This result suggests that a model's chain of thought is not sufficient to determine how it arrived at its output.

Results：作者衡量了模型生成提示的答案，同时在其思维链（chain of thought）中提及提示的频率。在模型似乎依赖于提示的情况下，Claude 3.7 Sonnet 的思维链中有 25% 的时间提及了提示，而 DeepSeek R1 则有 39% 的时间提及。这一结果表明，单凭模型的思维链不足以确定它是如何得出输出结果的。

Yes，but: The author's prompts were simpler than many real-world scenarios，and a hint's absence from a chain of thought may simply reflect the fact that the model didn't need to think much about it to reach a conclusion. For example，having been fed a hint，a model didn't need to produce a chain of thought but could simply parrot the hint.

是的，但是：作者使用的提示比许多真实世界的场景要简单。而且，如果一个提示没有出现在模型的思维链中，那可能仅仅是因为模型不需要过多思考就能得出结论。例如，在模型获得了某个提示后，它就不需要再生成一套思维过程，而可以直接照搬这个提示。

Why it matters: In earlier work，Anthropic showed that examining the correlation between a model's inputs and its intermediate embeddings can provide a rough idea of how it arrived at a specific output. This work shifts the inquiry to chains of thought. It suggests that while they may be useful，since they sometimes explain the final output，they're not sufficient，since they may omit crucial information that the model used to reach its conclusions.

Why it matters：在早期的研究中，Anthropic 曾展示，通过检查模型输入和其内部表示（中间嵌入）之间的关联，我们可以大致了解模型是如何得出特定输出的。而这项新研究则将焦点转向了「思维链」（chains of thought）。研究表明，虽然思维链可能很有用，因为它们有时能解释最终的输出，但它们却不够完善，因为模型在得出结论时可能遗漏了关键信息。

We're thinking: Few tools are available to explain why a non-reasoning LLM generates a particular output，so perhaps it's not surprising that a chain of thought isn't always sufficient to explain a reasoning LLM's output.

我们发现：目前很少有工具能解释非推理型大语言模型（LLM）为什么会生成特定的输出，因此，即使是对于推理型大语言模型，思维链（chain of thought）也并非总能完全解释其输出，这或许并不令人感到意外。