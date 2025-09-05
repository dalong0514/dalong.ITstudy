## 20250827AI-Powered-Phones-Get-Proactive-Robot-Antelope-Joins-Herd

[AI-Powered Phones Get Proactive, Robot Antelope Joins Herd, LLM Environmental Impacts Get Measured](https://www.deeplearning.ai/the-batch/issue-316/)

Dear friends,

各位朋友，

Parallel agents are emerging as an important new direction for scaling up AI. AI capabilities have scaled with more training data, training-time compute, and test-time compute. Having multiple agents run in parallel is growing as a technique to further scale and improve performance.

并行智能体（Parallel agents）正在成为扩展 AI 规模的一个重要新方向。长期以来，AI 能力的提升主要得益于更多的训练数据、训练阶段计算（training-time compute）和测试阶段计算（test-time compute）。现在，让多个智能体并行运行，正逐渐成为一种进一步扩展能力和提升性能的有效技术。

We know from work at Baidu by my former team, and later OpenAI, that AI models' performance scales predictably with the amount of data and training computation. Performance rises further with test-time compute such as in agentic workflows and in reasoning models that think, reflect, and iterate on an answer. But these methods take longer to produce output. Agents working in parallel offer another path to improve results, without making users wait.

我们从我以前的团队在 Baidu 的工作，以及后来 OpenAI 的研究中了解到，人工智能模型（AI models）的性能提升与数据量和训练计算量呈可预测的关系。当在推理阶段投入更多计算资源时，性能还能进一步提高，这体现在例如 AI 智能体（AI agent）工作流程中，以及那些能够思考、反思并迭代优化答案的推理模型（reasoning models）中。不过，这些方法通常需要更长的时间才能给出结果。而让多个 AI 智能体（Agents）并行工作则提供了另一种提升结果的方案，同时又无需让用户等待。

Reasoning models generate tokens sequentially and can take a long time to run. Similarly, most agentic workflows are initially implemented in a sequential way. But as LLM prices per token continue to fall — thus making these techniques practical — and product teams want to deliver results to users faster, more and more agentic workflows are being parallelized.

推理模型（Reasoning models）会按顺序生成 Token，运行时间可能较长。同样地，大多数智能体工作流（agentic workflows）最初也是以顺序方式实现的。但是，随着大语言模型（LLM）每个 Token 的价格持续下降 —— 这使得相关技术变得更加实用 —— 加之产品团队希望更快地向用户交付成果，越来越多的智能体工作流开始被并行处理。

Some examples:

一些例子：

1 Many research agents now fetch multiple web pages and examine their texts in parallel to try to synthesize deeply thoughtful research reports more quickly.

许多研究型 AI 智能体（AI agent）现在会同时抓取多个网页，并并行分析它们的内容，以期更快地生成富有深度的研究报告。

2 Some agentic coding frameworks allow users to orchestrate many agents working simultaneously on different parts of a code base. Our short course on Claude Code shows how to do this using git worktrees.

一些基于 AI 智能体（AI Agent）的编码框架，能让用户协调多个 AI 智能体同时处理代码库的不同部分。我们关于 Claude Code 的短期课程便展示了如何利用 git worktrees 来实现这一功能。

3 A rapidly growing design pattern for agentic workflows is to have a compute-heavy agent work for minutes or longer to accomplish a task, while another agent monitors the first and gives brief updates to the user to keep them informed. From here, it's a short hop to parallel agents that work in the background while the UI agent keeps users informed and perhaps also routes asynchronous user feedback to the other agents.

目前，一种快速兴起的基于 AI 智能体（AI Agent）的工作流设计模式是：让一个需要大量计算资源的 AI 智能体花费数分钟甚至更长时间来完成一项任务，同时，另一个 AI 智能体负责监控前者，并向用户实时提供简短的进度更新，让他们随时了解情况。基于这种模式，我们很容易就能进一步设想并行工作的 AI 智能体：它们在后台默默执行任务，而用户界面（UI）AI 智能体则持续向用户提供信息，甚至还能将用户异步反馈（即用户不需实时等待回复的留言或操作）传达给其他 AI 智能体处理。

It is difficult for a human manager to take a complex task (like building a complex software application) and break it down into smaller tasks for human engineers to work on in parallel; scaling to huge numbers of engineers is especially challenging. Similarly, it is also challenging to decompose tasks for parallel agents to carry out. But the falling cost of LLM inference makes it worthwhile to use a lot more tokens, and using them in parallel allows this to be done without significantly increasing the user's waiting time.

对于人类管理者来说，将一个复杂任务（例如构建一个复杂的软件应用程序）分解成更小的任务，再分配给人类工程师并行协作，是一项非常困难的工作；如果工程师的数量庞大，这项挑战的难度会急剧增加。类似地，为并行工作的 AI 智能体（AI Agent）分解任务也同样充满挑战。然而，随着大语言模型（LLM）推理成本的持续下降，投入更多 Token 变得更加划算，并且通过并行处理，可以在不大幅增加用户等待时间的前提下实现这一目标。

I am also encouraged by the growing body of research on parallel agents. For example, I enjoyed reading "CodeMonkeys: Scaling Test-Time Compute for Software Engineering" by Ryan Ehrlich and others, which shows how parallel code generation helps you to explore the solution space. The mixture-of-agents architecture by Junlin Wang is a surprisingly simple way to organize parallel agents: Have multiple LLMs come up with different answers, then have an aggregator LLM combine them into the final output.

我也对并行智能体（parallel agents）日益增多的研究感到鼓舞。例如，我尤其喜欢阅读 Ryan Ehrlich 等人的「CodeMonkeys：Scaling Test-Time Compute for Software Engineering」，它展示了并行代码生成如何有助于探索解决方案空间。Junlin Wang 提出的「智能体混合（mixture-of-agents）」架构，是一种出人意料的简单方法来协调并行智能体：让多个大语言模型（LLMs）给出不同的答案，然后由一个聚合器大语言模型（aggregator LLM）将它们组合成最终输出。

[[2501.14723] CodeMonkeys: Scaling Test-Time Compute for Software Engineering](https://arxiv.org/abs/2501.14723)

There remains a lot of research as well as engineering to explore how best to leverage parallel agents, and I believe the number of agents that can work productively in parallel — like the humans who can work productively in parallel — will be very high.

关于如何充分发挥并行 AI 智能体（parallel agents）的作用，仍有大量的研究和工程工作需要探索。我相信，能够并行高效工作的 AI 智能体的数量 —— 就像能够并行高效工作的人类一样 —— 将会非常高。

Keep building!

Andrew

### News

#### Proactive AI Assistance for Phones

手机上的主动式 AI 助理

Google's latest smartphone sports an AI assistant that anticipates the user's needs and presents helpful information without prompting.

Google 最新的智能手机配备了一个 AI 助手（AI assistant），它能预测用户需求，并主动提供有用的信息，无需用户发出指令。

What's new: Google unveiled its Pixel 10 along with an AI-powered system called Magic Cue. During calling, texting, and other interactions, the system automatically delivers relevant information — dates, times, names, locations, weather, photos, airline booking numbers, and so on — culled from compatible applications.

最新动态：Google 发布了 Pixel 10，同时推出了一款名为 Magic Cue 的 AI 驱动系统（AI-powered system）。在用户进行通话、发送短信及其他互动时，该系统会自动从兼容应用程序中提取相关信息，例如日期、时间、姓名、地点、天气、照片以及航空公司预订号等。

How it works: Magic Cue takes advantage of an updated version of Gemini Nano and runs on the Pixel 10's newly upgraded Tensor G5 AI processor. The system tracks user behavior and provides relevant information proactively.

工作原理：Magic Cue 充分利用了更新版本的 Gemini Nano 模型，并在 Pixel 10 全新升级的 Tensor G5 AI 处理器上高效运行。这个系统能够持续追踪用户的行为模式，并主动为用户提供相关的实用信息。

1 Magic Cue does not require wake words or prompts. It runs in the background and responds to the phone's state from moment to moment.

Magic Cue 不需要唤醒词或任何提示。它会在后台运行，并能实时感知和响应手机的当前状态。

2 The system's output appears within the current app as a floating overlay window.

该系统的输出会以浮动叠加窗口的形式，呈现在用户当前使用的应用界面上。

3 In an example provided by Google, if a user receives a text asking when their flight is scheduled to land, Magic Cue will access the user's itinerary, extract relevant details, and offer the opportunity to insert them into a reply. If the user calls the airline to change the flight, the system will respond by displaying the flight information.

Google 提供了一个例子：如果用户收到一条询问航班何时降落的短信，Magic Cue 会访问用户的行程，提取相关细节，并提供将这些信息插入回复的选项。如果用户打电话给航空公司更改航班，系统则会通过显示航班信息来作出回应。

Behind the news: Google has been especially aggressive in building AI into phones. In 2021, it replaced the Qualcomm Snapdragon chip that had run AI inference on Pixel phones with its own Tensor chip, which combined a GPU, CPU, Tensor processing unit, and security subsystem. Three years later, the Pixel 8's Tensor G3 chip provided the muscle for AI-enabled audio and video editing — but those capabilities were features within applications. Equipped with the new Tensor G5, Pixel 10 integrates AI with the operating system and applications to provide new kinds of capabilities.

新闻揭秘：Google 一直致力于将人工智能（AI）深度整合到手机中，在这方面表现得尤为积极。早在 2021 年，Google 就用自研的 Tensor 芯片取代了 Pixel 手机中负责 AI 推理（AI inference）任务的 Qualcomm Snapdragon 芯片。这款 Tensor 芯片集成了图形处理器（GPU）、中央处理器（CPU）、专门的 Tensor 处理单元以及安全子系统。三年后，Pixel 8 搭载的 Tensor G3 芯片已经能够为 AI 辅助的音频和视频编辑提供强大支持 —— 不过，这些功能当时主要还是停留在应用层面。如今，随着全新 Tensor G5 芯片的加入，Pixel 10 将 AI 更深入地融入操作系统和各种应用中，从而带来全新类型的功能体验。

Why it matters: Enabling edge devices to run powerful AI models has been a longstanding goal of big tech companies. But a smartphone's relatively meager computational, storage, and battery resources have presented serious challenges. The combination of Gemini Nano and the Tensor G5 chip gives Google a strong foundation to keep pushing the limits of edge AI, and its control of the Android operating system gives it tremendous market power to promote its models.

重要意义：让边缘设备运行强大的 AI 模型（AI models）一直是大型科技公司长期以来的目标。然而，智能手机相对有限的计算、存储和电池资源带来了严峻的挑战。Gemini Nano 和 Tensor G5 芯片的结合，为 Google 奠定了稳固的基础，使其能不断拓展边缘 AI（edge AI）的能力边界；同时，Google 对 Android 操作系统的掌控，也为其推广自身模型提供了巨大的市场优势。

We're thinking: Apple has noticed Google's progress. It's reportedly negotiating with Google to use Gemini technology for its Siri AI assistant.

我们不禁想：Apple 已经注意到了 Google 的进展。据报道，它正在与 Google 洽谈合作，希望将 Gemini 技术整合到其 Siri AI 助手中。

#### Mistral Measures LLM Consumption of Energy, Water, and Materials

Mistral 测量大语言模型（Large Language Model）对能源、水和材料的消耗

The French AI company Mistral measured the environmental impacts of its flagship large language model.

法国 AI 公司 Mistral 评估了其旗舰大语言模型（Large Language Model）的环境影响。

What's new: Mistral published an environmental analysis of Mistral Large 2 (123 billion parameters) that details the model's emission of greenhouse gases, consumption of water, and depletion of resources, taking into account all computing and manufacturing involved. The company aims to establish a standard for evaluating the environmental impacts of AI models. The study concluded that, while individual uses of the model have little impact compared to, say, using the internet, aggregate use takes a significant toll on the environment.

最新进展：Mistral 发布了一份关于 Mistral Large 2 （1230 亿参数）的环境分析报告。这份报告详细阐述了该模型的温室气体排放、水资源消耗和资源枯竭情况，其中涵盖了所有相关的计算和制造过程。该公司旨在为评估 AI 模型（AI model）的环境影响建立一个标准。这项研究得出结论，尽管该模型的单次使用对环境影响微不足道，例如相较于使用互联网，但其累积使用对环境造成了显著影响。

How it works: Mistral tracked the model's operations over 18 months. It tallied impacts caused by the building of data centers, manufacturing and transporting servers, training and running the model, the user's equipment, and indirect impacts of using the model. The analysis followed the Frugal AI methodology developed by Association Française de Normalisation, a French standards organization. Environmental consultancies contributed to the analysis, and environmental auditors peer-reviewed it.

工作原理：Mistral 跟踪了该模型长达 18 个月的运营情况。它统计了数据中心建设、服务器制造与运输、模型训练与运行、用户设备以及使用模型所产生的间接影响。这项分析遵循了由法国标准组织 Association Française de Normalisation 开发的 Frugal AI（节俭型人工智能）方法论。多家环境咨询公司参与了这项分析，并由环境审计师进行了同行评审。

1 Training Mistral Large 2 produced 20,400 metric tons of greenhouse gases. That's roughly equal to annual emissions from 4,400 gas-powered passenger vehicles.

训练 Mistral Large 2 产生了 20,400 公吨温室气体。这大致相当于 4,400 辆燃油乘用车一年的总排放量。

2 Training consumed 281,000 cubic meters of water for cooling via evaporation, roughly as much as the average U.S. family of four would consume in 500 years. (1.5 cubic meters per day x 365 days x 500 years.)

训练消耗了 281,000 立方米的水用于蒸发冷却（evaporative cooling），大约相当于一个普通美国家庭（四口人）500 年的用水量。(每天 1.5 立方米 x 365 天 x 500 年)

3 Training and inference accounted for 85.5 percent of the model's greenhouse-gas emissions, 91 percent of its water consumption, and 29 percent of materials consumption including energy infrastructure.

在一个模型的整个生命周期中，训练和推理（inference）过程贡献了模型 85.5% 的温室气体排放、91% 的水资源消耗，以及 29% 的材料消耗（包括能源基础设施）。

4 Manufacturing, transporting, and decommissioning servers accounted for 11 percent of greenhouse gas emissions, 5 percent of water consumption, and 61 percent of overall materials consumed.

服务器的制造、运输和退役，分别占温室气体排放量的 11%、水资源消耗量的 5% 以及材料总消耗量的 61%。

5 Network traffic came to less than 1 percent of each of the three measures.

网络流量在所有这三项衡量指标中的占比都不到 1%。

6 The average prompt and response (400 tokens or a page of text) emitted 1.14 grams of greenhouse gases, about the amount produced by watching a YouTube clip (10 seconds in the U.S. or 55 seconds in France where low-emissions nuclear energy is more widely available), and consumed 45 milliliters or 3 tablespoons of water. The total materials consumption was roughly equivalent to manufacturing a 2 Euro coin.

平均每次提示与响应（相当于 400 个 Token 或一页文本）会排放 1.14 克温室气体，这大约相当于观看一个 YouTube 视频所产生的碳排放量（在美国是 10 秒，而在法国则是 55 秒，因为法国广泛使用低排放核能）。同时，它还消耗了 45 毫升（约合 3 汤匙）水。所有材料的总消耗量大致相当于制造一枚 2 欧元硬币。

Yes, but: Mistral acknowledged a few shortcomings of the study. It struggled to calculate some impacts due to the lack of data and established standards. For instance, a reliable assessment of the environmental impact of GPUs is not available.

不过，Mistral 也指出了这项研究的一些不足之处。由于缺乏数据和已有的标准，它难以计算某些影响。例如，目前尚未有关于图形处理器（GPU）环境影响的可靠评估。

Behind the news: Mistral's report follows a string of studies that assess AI's environmental impact.

新闻背景：Mistral 的这份报告，是在一系列评估人工智能（AI）环境影响的研究之后发布的。

1 While AI is likely to consume increasing amounts of energy, it could also produce huge energy savings in coming years, according to a report by the International Energy Agency, which advises 44 countries on energy policy.

尽管人工智能可能消耗日益增长的能源，但根据国际能源署（International Energy Agency）的一份报告（该机构为 44 个国家提供能源政策建议），未来几年，人工智能也有望带来巨大的能源节约。

2 A 2023 analysis by University of California and University of Texas quantified GPT-3-175B's consumption of water. The conclusions of that work align with those of Mistral's analysis.

2023 年，加利福尼亚大学和德克萨斯大学发布了一项分析，估算了 GPT-3-175B 大语言模型（Large Language Model）的水资源消耗。这项研究的结论与 Mistral 公司的分析结果不谋而合。

3 A 2021 paper identified ways to make AI models up to a thousand-fold more energy-efficient by streamlining architectures, upgrading hardware, and boosting the energy efficiency of data centers.

一篇 2021 年的论文提出了一些方法，能够让 AI 模型的能效提升高达一千倍，具体途径包括简化模型架构、升级硬件以及提高数据中心的能源效率。

Why it matters: AI consumes enormous amounts of energy and water, and finding efficient ways to train and run models is critical to ensure that the technology can benefit large numbers of people. Mistral's approach provides a standardized approach to assessing the environmental impacts. If it's widely adopted, it could help researchers, businesses, and users compare different models, work toward more environmentally friendly AI, and potentially reduce overall impacts.

重要性：人工智能（AI）消耗巨大的能源和水资源，因此，找到高效训练和运行模型的方法，对于确保这项技术能够惠及大众至关重要。Mistral 提出的方法，提供了一套评估 AI 环境影响的标准化途径。如果这套方法能被广泛采纳，它将有助于研究人员、企业和用户比较不同模型，从而推动开发更环保的 AI，并有可能全面减少其对环境的影响。

We're thinking: Data centers and cloud computing are responsible for 1 percent of the world's energy-related greenhouse gas emissions, according to the International Energy Agency. That's a drop in the bucket compared to agriculture, construction, or transportation. Nonetheless, having a clear picture of AI's consumption of resources can help us manage them more effectively as demand rises. It's heartening that major AI companies are committed to using and developing sustainable energy sources and using them efficiently, and the environmental footprint of new AI models and processors is falling steadily.

根据国际能源署的数据，数据中心和云计算占全球能源相关温室气体排放量的 1%。与农业、建筑或交通运输相比，这个比例可谓微不足道。尽管如此，随着需求的不断增长，清晰地了解人工智能（AI）的资源消耗，有助于我们更有效地管理这些资源。令人鼓舞的是，主要的 AI 公司都致力于使用和开发可持续能源，并提高能源利用效率。同时，新 AI 模型和处理器的环境足迹（environmental footprint）也在稳步下降。

#### Robot Antelope Joins Herd

机器人藏羚羊「混入」羚羊群

Researchers in China disguised a quadruped robot as a Tibetan antelope to help study the animals close-up.

中国研究人员将一台四足机器人伪装成藏羚羊，目的是为了近距离观察和研究这些珍稀动物。

What's new: The Chinese Academy of Sciences teamed with Hangzhou-based Deep Robotics and the state news service Xinhua to introduce a robot into a herd that lives in the Hoh Xil National Nature Reserve, a mountainous area where the elevation is above 14,000 feet. The robot enables scientists to observe the shy antelopes without disturbing them.

最新消息：中国科学院与总部位于杭州的 Deep Robotics 公司以及国家通讯社新华社携手合作，成功将一个机器人引入了生活在可可西里国家级自然保护区的藏羚羊群中。可可西里是一个海拔超过 14,000 英尺（约 4,267 米）的山区。这个机器人能够让科学家们在不打扰这些生性害羞的藏羚羊的情况下，近距离观察它们。

How it works: The mechanical beast is a Deep Robotics X30 covered with an antelope's hide. The X30, which is designed for industrial inspections and search-and-rescue tasks, is well suited to the region's rugged terrain and conditions. It can climb open-riser staircases, function at temperatures between -20° and 55° Celsius, and resist dust and water according to ratings established by the International Electrotechnical Commission. Its vision system is designed to operate in dim or very bright light.

工作原理：这只「机械兽」其实是 Deep Robotics 生产的一台 X30 机器人，只是外面披上了一层羚羊皮。X30 专为工业检查和搜救任务而设计，因此它能够很好地适应该地区崎岖的地形和严酷的环境。它不仅能攀爬没有竖板的开放式楼梯，还能在零下 20 摄氏度到 55 摄氏度的宽泛温度范围内正常运行，并且符合国际电工委员会设定的防尘防水等级标准。它的视觉系统经过特殊设计，无论是在昏暗还是极其明亮的光线下都能正常工作。

1 Deep Robotics has published little information about the X30's training, though it has said the robot learned to navigate rough terrain via the reinforcement learning algorithm proximal policy optimization (PPO). However, its GitHub repository reveals details about its robot for the consumer market, Lite3. (The two are similar, but their training may not be.) Lite3 used multiple vanilla neural networks; first to embed current and previous joint positions and velocities and then to calculate joint motions. Lite3 learned via PPO to move a simulated robot across various terrains (flat, sloped, staircased, random, and so on) in the Isaac Gym simulator. It received rewards when the simulated robot moved forward or took larger steps, and it received punishment when the robot moved too fast, failed to move, fell over, collided with objects, and so on.

Deep Robotics 鲜少公开关于 X30 机器人训练的细节，不过它曾表示，X30 通过强化学习算法（reinforcement learning algorithm）中的近端策略优化（PPO）学习在崎岖地形上导航。然而，Deep Robotics 的 GitHub 存储库披露了其面向消费市场的机器人 Lite3 的更多细节。（X30 和 Lite3 相似，但它们的训练方式可能不同。）Lite3 使用了多个普通神经网络（vanilla neural networks)；首先，它们嵌入当前和先前的关节位置与速度信息，随后计算出关节的运动指令。Lite3 通过 PPO 学习在 Isaac Gym 模拟器中，让一个模拟机器人跨越各种地形移动，这些地形包括平坦、倾斜、带楼梯、随机等。当模拟机器人向前移动或迈出更大步伐时，会获得奖励；而当机器人移动过快、未能移动、摔倒或与物体碰撞时，则会受到惩罚。

2 The X30 is equipped with cameras (two hidden beneath its fake eyes plus a wide-angle camera), LiDAR, ultrasonic sensors, and a GPS system with a real-time kinematics module for more precise location tracking. Its computer-vision software automatically tracks the herd's movement, feeding, and reproduction and transmits data via 5G radio. If it detects the herd nearing a road, it sends an alert so its operators can direct automobile traffic, allowing the animals to cross safely.

X30 配备了多种传感器，包括摄像头（其中两个巧妙地藏在它的「假眼」下方，还有一个广角摄像头）、激光雷达（LiDAR）、超声波传感器，以及一个带有实时动态定位模块（RTK 模块）的全球定位系统（GPS），可以实现更精准的位置跟踪。它的计算机视觉软件能够自动追踪牛群的移动、进食和繁殖情况，并通过 5G 无线电网络实时传输数据。如果 X30 监测到牛群正在接近道路，它会立即发出警报，以便操作员能够及时引导车辆，确保动物们安全穿过马路。

3 It can be controlled remotely up to 1.2 miles away. Its top speed is 8 miles per hour, while Tibetan antelopes can move as fast as 50 miles per hour. Its battery lasts up to 4 hours and features a quick-release mechanism for streamlined swapping.

它可以通过远程控制（remotely controlled），遥控距离最远可达 1.2 英里。它的最高时速为 8 英里，而藏羚羊的时速最快可达 50 英里。它的电池续航时间最长达 4 小时，并配备了快速释放机制，以便更便捷地更换电池。

Behind the news: Human observation can disrupt animal behavior, so the study of animals in their natural habitat relies mostly on camera traps and drones. Increasingly, biologists are experimenting with robots mocked up to look like animals.

新闻背景：人类观察活动会扰乱动物行为，因此，对生活在自然栖息地的动物进行研究，主要依赖于相机陷阱（camera traps）和无人机（drones）。现在，越来越多的生物学家正在尝试使用伪装成动物的机器人进行研究。

1 In Florida, robot bunnies automatically lure invasive Burmese pythons and alert researchers when their sensors detect the reptiles.

在佛罗里达，诱饵机器人兔子能自动引诱入侵的缅甸蟒蛇，当它们的传感器检测到这些爬行动物时，就会通知研究人员。

2 Robot falcons that fly thanks to wing-mounted propellers scare birds from airport runways to reduce the risk that they'll interfere with aircraft.

依靠机翼上安装的螺旋桨飞行的机器人猎鹰，能将鸟类从机场跑道上驱离，从而降低鸟类干扰飞机的风险。

Why it matters: Applying AI to robotic perception, locomotion, and dexterity opens a wide range of applications. Case in point: Deep Robotics' PPO training enables its robots to navigate difficult environments (like climbing uneven staircases) and respond to dynamic challenges (like being kicked down the stairs). Such capabilities are valuable not only in domestic and industrial uses but also research situations like observing antelope behavior.

重要意义：将人工智能（AI）应用于机器人的感知、运动和灵巧操作，开启了广阔的应用前景。例如，Deep Robotics 公司利用 PPO 训练技术，使其机器人能够自如穿梭于复杂环境（比如攀爬不平坦的楼梯），并从容应对动态挑战（比如被踢下楼梯）。这些能力不仅在家庭和工业领域具有重要价值，在科研场景中也大有用武之地，例如观察羚羊的行为等。

We're thinking: Robotics is making impressive strides!

我们不妨思考一下：机器人技术正在取得令人瞩目的进步！

#### Better Image Processing Through Self-Supervised Learning

通过自监督学习提升图像处理能力

DINOv2 showed that a vision transformer pretrained on unlabeled images could produce embeddings that are useful for a wide variety of tasks. Now it has been updated to improve the performance of its embeddings in segmentation and other vision tasks.

DINOv2 表明，通过在未标记图像上进行预训练，视觉 Transformer（Vision Transformer）能够生成对多种任务都很有用的嵌入（Embeddings）。现在，它已得到更新，以进一步提升其在分割（Segmentation）和其他视觉任务中嵌入的表现。

What's new: Oriane Siméoni and colleagues at Meta, World Resources Institute, and France's National Institute for Research in Digital Science and Technology released the weights and training code for DINOv3, a self-supervised model that updates the previous version with 6 times more parameters trained on more data plus a new loss function.

最新进展：Oriane Siméoni 及其来自 Meta、世界资源研究所和法国国家数字科学与技术研究所的同事们，发布了 DINOv3 的权重（weights）和训练代码（training code）。DINOv3 是一个自监督模型（self-supervised model），它在之前版本的基础上进行了大幅更新，模型参数量（parameters）增至 6 倍，训练数据更多，并且引入了新的损失函数（loss function）。

1 Input/output: Image in, embedding out

输入 / 输出：输入是图像，输出是嵌入

2 Architecture: 6.7 billion-parameter vision transformer

3 架构：采用了一个包含 67 亿参数的视觉 Transformer（Vision Transformer）

4 Performance: Outstanding image segmentation and depth estimation

性能：在图像分割和深度估计方面表现卓越

5 Training data: Over 1.7 billion images from public Instagram posts

训练数据：超过 17 亿张来自公共 Instagram 帖子的图片

1 Availability: Weights and training code are available via a license that allows non-commercial and commercial uses but forbids military applications

获取方式：模型权重和训练代码根据一份许可协议提供，该协议允许非商业和商业用途，但禁止用于军事应用。

2 Undisclosed: Input size limit

未披露信息：输入大小限制

Key insight: Vision transformers trained in a self-supervised fashion —  such as feeding them unlabeled images with missing patches and training them to fill in the blanks — yield uneven results beyond a certain number of training steps. Further training increases performance on tasks that depend on analyzing an image globally, like classification and face recognition, but degrades it in tasks that concentrate on portions of an image, like image segmentation and depth estimation. The DINOv3 team discovered the reason: The model's embeddings of random patches become more similar as training continues. To counteract this, they used the model trained up to that point as a teacher and trained successive versions to avoid producing patch embeddings that were more similar to one another than the teacher's embeddings were.

关键洞察：以自监督方式训练的视觉 Transformer（Vision Transformer）—— 例如，给它们输入缺少图像块（patch）的未标记图像，并训练它们来填补空白 —— 在经过一定数量的训练步骤后，会产生效果参差不齐的结果。具体来说，进一步的训练会提升模型在依赖于全局分析图像的任务上的表现，比如分类和人脸识别，但却会损害它在专注于图像局部（portion）的任务上的表现，例如图像分割和深度估计。DINOv3 团队发现了其中的原因：随着训练的进行，模型对随机图像块的嵌入（embedding）变得越来越相似。为了纠正这种现象，他们使用训练到当时进度的模型作为「教师」（teacher）模型，并训练后续的模型版本，使其生成的图像块嵌入不会比教师模型生成的嵌入更相似。

How it works: The building of DINOv3 followed that of its predecessor DINOv2 but added a new loss term.

工作原理：DINOv3 的构建是基于其前身 DINOv2 的，但在此基础上增加了一个新的损失项（loss term）。

1 The team trained DINOv3 to embed images of size 256x256 pixels for the first 1 million steps. During this phase, they measured how well DINOv3 segmented many images after different numbers of training steps. For each test, they froze the model and trained a linear layer, given an embedding of an image from the PASCAL VOC dataset that includes images and segmentation maps, to segment the image. The model's segmentation score (measured using mean intersection over union, the overlap between the model's output and ground truth) peaked after around 100,000 training steps and decreased steadily after around 200,000 training steps.

该团队在前 100 万步训练中，让 DINOv3 学习如何将 256x256 像素大小的图像进行嵌入。在此阶段，他们评估了 DINOv3 在不同训练步数下对多幅图像的分割效果。具体测试方法是：对于每次评估，他们会「冻结」DINOv3 模型，然后训练一个线性层。这个线性层利用来自 PASCAL VOC 数据集（该数据集包含图像及其对应的分割图）的图像嵌入，来完成图像分割任务。结果显示，模型在分割任务上的得分（采用平均交并比（mean intersection over union）衡量，即模型输出与真实标注之间的重叠度）大约在训练 10 万步后达到峰值，并在约 20 万步后开始稳步下降。

2 To enable the model to relearn how to produce different patch embeddings — a skill increasingly lost during the first phase of training — they continued to train DINOv3 for another 10,000 to 30,000 steps using an additional loss term. The new loss term aimed to minimize the difference in the degrees of similarity between patch embeddings produced by the current model and those produced by the model at 100,000 training steps. They compared the degree of dissimilarity rather than comparing the embeddings themselves so the model learned to make embeddings that are different from those produced by its less-trained counterpart but different to the degree that is associated with good performance on tasks like segmentation.

为了让模型重新掌握生成不同「补丁嵌入（patch embeddings）」的能力 —— 这种能力在第一阶段训练中逐渐减弱 —— 研究人员继续对 DINOv3 模型进行了额外的 10,000 到 30,000 步训练，并引入了一个新的损失项。这个新的损失项旨在最小化当前模型生成的补丁嵌入与模型在训练了 100,000 步时生成的补丁嵌入之间的差异程度。他们选择比较「不相似度（dissimilarity）」的程度，而不是直接比较嵌入本身。这样做的目的是让模型学习生成与训练程度较低的模型所生成的嵌入有所不同，但这种差异程度又恰好与在图像分割等任务上的良好表现相关联的嵌入。

3 They trained the model in the same way for another 10,000 steps on image sizes up to 768x768 pixels.

模型在高达 768x768 像素的图像尺寸上，又以同样的方式训练了 10,000 步。

Results: The authors adapted the trained embedding model for various uses by adding separate linear layers and training them on tasks including segmentation and classification.

结果：作者通过添加独立的线性层（linear layers），并在包括分割（segmentation）和分类（classification）等任务上进行训练，使这个已训练好的嵌入模型（embedding model）能够适应各种应用场景。

1 Segmenting images in PASCAL VOC, DINOv3 achieved 86.6 mean IoU (intersection over union, higher is better). DINOv2 achieved 83.1 mean IoU, and SigLIP 2, a model trained via weak supervision to produce similar embeddings of text and images, achieved 72.7 mean IoU.

在 PASCAL VOC 数据集上进行图像分割任务时，DINOv3 模型取得了 86.6 的平均 IoU（intersection over union）分数（这个数值越高表示分割效果越好）。DINOv2 模型也达到了 83.1 的平均 IoU。而 SigLIP 2 这个模型，它是通过弱监督（weak supervision）方式训练的，旨在让文本和图像生成相似的嵌入（embeddings），其平均 IoU 得分为 72.7。

2 Classifying images in ImageNet, DINOv3 (88.4 percent accuracy) outperformed the next-best self-supervised model DINOv2 (87.3 percent accuracy). It underperformed two weakly supervised models, SigLIP 2 (89.1 percent accuracy) and PECore (89.3 percent accuracy).

在 ImageNet 数据集上进行图像分类时，DINOv3 （88.4% 的准确率）超越了排名仅次于它的自监督模型（self-supervised model）DINOv2 （87.3% 的准确率）。然而，它仍略逊于两个弱监督模型（weakly supervised model），即 SigLIP 2 （89.1% 的准确率）和 PECore （89.3% 的准确率）。

Why it matters: Unsupervised learning is important in visual AI because image and video data are more common than image-text and video-text data. The additional loss term enabled the team to use this more plentiful data to improve performance on both globally and locally focused tasks.

重要性：无监督学习（Unsupervised learning）在视觉 AI（Visual AI）领域扮演着重要角色，这是因为图像和视频数据通常比图像 - 文本或视频 - 文本数据更为丰富。研究团队通过引入额外的损失项（loss term），得以充分利用这些海量数据，从而显著提升了模型在全局和局部任务上的表现。

We're thinking: Model builders have raced to make ever bigger large language models trained on more data, and their performance has improved with each leap in size. That hasn't happened with vision transformers, but DINOv3, which is 6 times larger and trained on an order of magnitude more data than its predecessor, suggests that it could.

我们发现：大语言模型（Large Language Model）的开发者一直在竞相打造更大规模的模型，并用更多数据对其进行训练，而模型的性能也随每一次规模的飞跃而显著提升。然而，这种现象在视觉 Transformer（Vision Transformer）上尚未出现。但 DINOv3 的出现预示着这种潜力：它比前一代模型大 6 倍，并且在多一个数量级的数据上进行训练，这表明视觉 Transformer 的性能也有望通过扩大规模来大幅提升。