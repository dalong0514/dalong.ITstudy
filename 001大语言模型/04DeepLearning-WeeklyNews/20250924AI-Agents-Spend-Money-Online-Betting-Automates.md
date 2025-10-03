## 20250924AI-Agents-Spend-Money-Online-Betting-Automates

[AI Agents Spend Money, Online Betting Automates, ChatGPT Users Shift, and more...](https://www.deeplearning.ai/the-batch/issue-320/)

Dear friends,

亲爱的朋友们，

Last week, China barred its major tech companies from buying Nvidia chips. This move received only modest attention in the media, but has implications far beyond what's widely appreciated. Specifically, it signals that China has progressed sufficiently in semiconductors to break away from dependence on advanced chips designed in the U.S., the vast majority of which are manufactured in Taiwan. It also highlights the U.S. vulnerability to possible disruptions in Taiwan at a moment when China is becoming less vulnerable.

上周，中国禁止其主要科技公司购买英伟达（Nvidia）芯片。这一举动在媒体上受到的关注并不多，但其影响远超人们普遍的认知。具体来说，这表明中国在半导体领域已经取得了足够的进步，足以摆脱对美国设计的先进芯片的依赖，而这些芯片绝大多数是在台湾制造的。这也突显了美国在台湾可能出现供应中断时的脆弱性，尤其是在中国自身正变得不那么容易受影响的当下。

After the U.S. started restricting AI chip sales to China, China dramatically ramped up its semiconductor research and investment to move toward self-sufficiency. These efforts are starting to bear fruit, and China's willingness to cut off Nvidia is a strong sign of its faith in its domestic capabilities. For example, the new DeepSeek-R1-Safe model was trained on 1000 Huawei Ascend chips. While individual Ascend chips are significantly less powerful than individual Nvidia or AMD chips, Huawei's system-level design approach to orchestrating how a much larger number of chips work together seems to be paying off. For example, Huawei's CloudMatrix 384 system of 384 chips aims to compete with Nvidia's GB200, which uses 72 higher-capability chips.

自美国开始限制对中国 AI（人工智能）芯片的销售以来，中国便大幅增加了在半导体领域的研发投入和投资，旨在实现自给自足。这些努力如今已开始显现成效。中国愿意不再依赖 Nvidia（英伟达）芯片，正是其对国内技术能力抱有强大信心的有力佐证。例如，新一代 DeepSeek-R1-Safe 模型便是基于 1000 颗华为 Ascend 芯片训练而成的。尽管单颗 Ascend 芯片的性能远不如 Nvidia 或 AMD（超微）的单颗芯片，但华为在系统层面的设计方法 —— 即如何协调数量庞大的芯片协同工作 —— 似乎正发挥作用。例如，华为由 384 颗芯片组成的 CloudMatrix 384 系统，旨在与 Nvidia 采用 72 颗性能更强芯片的 GB200 系统展开竞争。

Today, U.S. access to advanced semiconductors is heavily dependent on Taiwan's TSMC, which manufactures the vast majority of the most advanced chips. Unfortunately, U.S. efforts to ramp up domestic semiconductor manufacturing have been slow. I am encouraged that one fab at the TSMC Arizona facility is now operating, but issues of workforce training, culture, licensing and permitting, and the supply chain are still being addressed, and there is still a long road ahead for the U.S. facility to be a viable substitute for manufacturing in Taiwan.

目前，美国获得先进半导体（semiconductors）的能力高度依赖台湾的 TSMC，该公司负责制造绝大多数最尖端的芯片。然而，美国推动国内半导体制造发展的努力一直进展缓慢。尽管 TSMC 亚利桑那工厂的一个晶圆厂（fab）现已投入运营，这令人鼓舞，但劳动力培训、企业文化、许可审批以及供应链等问题仍在持续解决中。美国工厂若要真正成为台湾芯片制造的可靠替代方案，前方仍长路漫漫。

If China gains independence from Taiwan manufacturing significantly faster than the U.S., this would leave the U.S. much more vulnerable to possible disruptions in Taiwan, whether through natural disasters or man-made events. If manufacturing in Taiwan is disrupted for any reason and Chinese companies end up accounting for a large fraction of global semiconductor manufacturing capabilities, that would also help China gain tremendous geopolitical influence.

如果中国比美国更快地摆脱对台湾制造业的依赖，这将使美国在台湾可能发生的任何干扰面前变得更加脆弱，无论是天灾还是人为事件。如果台湾的制造业因任何原因中断，而中国企业最终在全球半导体制造能力中占据了很大份额，那么这也将帮助中国获得巨大的地缘政治影响力。

Despite occasional moments of heightened tensions and large-scale military exercises, Taiwan has been mostly peaceful since the 1960s. This peace has helped the people of Taiwan to prosper and allowed AI to make tremendous advances, built on top of chips made by TSMC. I hope we will find a path to maintaining peace for many decades more.

尽管偶尔会有紧张局势加剧和大规模军事演习，但自 1960 年代以来，台湾大体上一直保持和平。这种和平不仅让台湾人民得以繁荣发展，也让人工智能（AI）取得了巨大的进步，这些成就都离不开台积电（TSMC）生产的芯片。我真心希望我们能够找到一条道路，让这份和平在未来几十年里继续延续下去。

But hope is not a plan. In addition to working to ensure peace, practical work lies ahead to multi-source, build more chip fabs in more nations, and enhance the resilience of the semiconductor supply chain. Dependence on any single manufacturer invites shortages, price spikes, and stalled innovation the moment something goes sideways.

但光有希望还不够。除了努力维护和平，接下来我们还有许多实际工作要做，包括实现多元化供应、在更多国家建造更多芯片制造厂，并增强半导体供应链的韧性。一旦过度依赖任何单一制造商，那么当出现问题时，就可能导致短缺、价格飙升以及创新停滞。

Keep building,

Andrew

### News

新闻

#### Agents of Commerce

商业智能体

Google launched an open protocol for agentic payments that enables agents based on any large language model to purchase items over the internet.

Google 推出了一项开放协议，旨在支持智能体（agent）进行支付。这项协议将使任何基于大语言模型（Large Language Model）的智能体都能在互联网上购买商品。

What's new: Agent Payments Protocol (AP2) is designed for buyers and sellers to securely initiate, authorize, and close purchases. AP2 works with Google's A2A and Anthropic's similar MCP, open protocols that instruct agents or provide access to data and APIs. It manages diverse payment types including credit cards, bank transfers, digital payments, and cryptocurrency.

新进展：我们推出了 AI 智能体支付协议（Agent Payments Protocol，AP2），它专门设计用于帮助买家和卖家安全地发起、授权并完成购买。AP2 能够与 Google 的 A2A 和 Anthropic 类似的 MCP 等开放协议协同工作，这些协议负责指示 AI 智能体（AI Agent）执行任务，或为其提供数据和 API 的访问权限。该协议能够管理各种支付方式，包括信用卡、银行转账、数字支付和加密货币等。

How it works: Agentic payments pose challenges to security, such as manipulation by malicious actors, and liability, particularly with respect to whether a user or agent is to blame for mistakes. AP2 aims to solve these problems by using cryptographically signed contracts called mandates. Three distinct mandates record the terms of the purchase, its fulfillment, and the user's authorization of payment. If a fraudulent or incorrect transaction occurs, the payment processor can consult this record to see which party is accountable. To buy an item using AP2:

工作原理：代理支付（Agentic payments）带来了一些安全挑战，例如可能被恶意行为者操控，同时还引发了责任归属问题，尤其是在出现错误时，究竟是用户还是 AI 智能体（AI Agent）应该负责。AP2 旨在通过使用名为「授权指令」（mandates）的加密签名合同来解决这些问题。具体来说，有三份独立的授权指令，分别记录了购买的条款、交易的履行情况，以及用户对支付的授权。如果发生欺诈或不正确的交易，支付处理器可以查阅这些记录，从而明确哪一方应该承担责任。要使用 AP2 购买商品：

1 An intent mandate specifies rules for the purchase such as price limits, timing, and the item's attributes. It may create an intent mandate while a user is present or ahead of time. For instance, if a buyer instructs an agent to "buy [brand and model] running shoes the moment they go on sale," the agent will prompt the user to specify and authorize the terms of the mandate, such as the desired top price, size, and color.

一项意图指令（intent mandate）明确了购买的规则，例如价格限制、购买时间，以及商品的具体属性。用户可以在场时创建这项意图指令，也可以预先设定好。例如，如果一位买家指示一个 AI 代理（AI agent）说「一旦 [品牌和型号] 跑鞋打折，就帮我买下来」，那么这个 AI 代理就会提示用户，要求用户明确并批准这项指令的具体条款，比如期望的最高价格、尺码和颜色。

2 A cart mandate covers the other end of the sale. This contract describes the contents of the virtual shopping cart including a description of items sold, their prices, and terms of the deal.

购物车的授权涵盖了销售环节的另一端。这份合同详细说明了虚拟购物车的内容，包括所售商品的描述、具体价格以及交易条款。

3 A payment mandate tells a payment network (a financial institution plus payment processor that moves funds electronically) that the transaction was authorized by a user or an agent, so it can complete the transaction.

支付授权（payment mandate）会指示支付网络（即由金融机构和负责电子资金流动的支付处理器组成）该笔交易已获得用户或 AI 智能体（AI Agent）的授权，这样支付网络就能顺利完成交易。

Behind the news: Many companies have experimented with agentic payments with varying degrees of success. For example, last year Stripe launched an agentic payment toolkit that issues a one-time debit card for each purchase. This approach reduces risk, but it requires Stripe's payment system, particular models, and specific agentic frameworks. Google's approach is more comprehensive, initially including more than 60 partners including payment processors, financial institutions, and software giants.

新闻解读：许多公司都曾尝试智能体支付（agentic payments），并取得了不同程度的进展。例如，去年 Stripe 发布了一套智能体支付工具包，它能为每笔交易生成一张一次性借记卡。这种做法虽然降低了风险，但其应用需要依赖 Stripe 的支付系统、特定的模型以及特定的智能体框架。相比之下，Google 的方案则更为全面，初期就吸引了包括支付处理器、金融机构和软件巨头在内的 60 多个合作伙伴。

Why it matters: AP2 opens up automated sales in which any participant can buy and sell, and it does this in a standardized, flexible way. For instance, a user could tell an agent to book a vacation in a specific location with a specific budget. The agent could transmit those requirements to many sellers' agents that might assemble customized packages to meet the user's demands. Then the user's agent could either present the packages to the user or choose one itself. The buyer would get the vacation they want and the seller would make a valuable sale, while AI did the haggling.

为什么这很重要：AP2 开启了自动化销售时代，让任何参与者都能以标准化、灵活的方式进行买卖。例如，用户可以告诉一个 AI 智能体（AI Agent）预订一个特定地点、有特定预算的假期。该智能体可以将这些要求发送给许多卖家智能体，这些卖家智能体可能会为用户定制套餐以满足其需求。随后，用户的智能体可以向用户展示这些套餐，或者直接替用户选择一个。这样，买家就能得到他们想要的假期，卖家也能完成一笔有价值的交易，而所有的讨价还价都由 AI 来完成。

We're thinking: The internet didn't make travel agents obsolete, it made them agentic!

我们认为：互联网并没有让旅行社（travel agents）变得过时，反而赋予了他们更强的能动性（agentic）！

#### What ChatGPT Users Want

ChatGPT 用户想要什么

What do ChatGPT's 700 million weekly active users do with it? OpenAI teamed up with a Harvard economist to find out.

ChatGPT 的 7 亿周活跃用户都用它来做什么呢？为了探究这个问题，OpenAI 与一位哈佛（Harvard）经济学家展开了合作。

What's new: ChatGPT users are turning to the chatbot increasingly for personal matters rather than work, and the gender balance of the user base is shifting, OpenAI found in a large-scale study. "How People Use ChatGPT," a preliminary report published by the National Bureau of Economic Research, is available in return for an institutional email address.

最新发现：OpenAI 在一项大规模研究中揭示，ChatGPT 用户使用这款聊天机器人处理个人事务的频率越来越高，而非仅仅用于工作。同时，用户群体的性别构成也正在发生变化。这份名为「人们如何使用 ChatGPT」的初步报告，由国家经济研究局（National Bureau of Economic Research）发布，机构邮箱用户可以获取查阅。

How it works: The study examined 1.58 million messages entered by users and drawn at random from over 1.1 million conversations between May 2024 and July 2025.

工作原理：本研究从 2024 年 5 月至 2025 年 7 月期间超过 110 万次对话中，随机抽取并分析了用户输入的 158 万条消息。

1 The messages were written by logged-in users over 18 who used consumer-level (as opposed to business) subscriptions.

这些消息由已登录的 18 岁以上用户撰写，他们使用的是个人用户订阅（而非商业用途）服务。

2 The authors classified users by gender (based on names the authors deemed typically masculine, feminine, or indeterminate), self-reported age, and geography.

作者们根据性别（依据他们认为具有典型男性、女性或不确定特征的名字）、用户自行报告的年龄和地理区域对用户进行了分类。

3 They classified messages by topic, general intention (such as asking for information or requesting action), and specific task (such as writing or coding).

他们根据话题、大致意图（例如询问信息或请求采取行动）和具体任务（例如写作或编程）对消息进行了分类。

Results: Most users of ChatGPT were young adults, and apparently more women are joining their ranks. Uses shifted from work to more personal tasks over the course of the study period. Writing and guidance were most popular uses, followed closely by seeking information.

结果显示，ChatGPT 的主要用户群体是年轻人，而且女性用户数量也明显增加。在研究期间，ChatGPT 的使用场景从工作相关任务转向了更多个人任务。其中，写作和寻求指导是最受欢迎的用途，紧随其后的则是获取信息。

1 ChatGPT was most popular with users between 18 and 25 years old, who sent 46 percent of the messages. Users between 26 and 66 were more likely to use ChatGPT for work.

ChatGPT 在 18 至 25 岁的用户群体中最受欢迎，这一年龄段的用户发送了总消息量的 46%。而 26 至 66 岁的用户则更有可能将 ChatGPT（一个大型语言模型）用于工作场景。

2 Women may now outnumber men using ChatGPT. Messages from users with names classified as typically feminine increased from 37 percent in January 2024 to 52 percent by June 2025.

目前，使用 ChatGPT 的女性用户数量可能已超过男性。根据数据显示，名字被识别为典型女性的用户所发送的消息占比，从 2024 年 1 月的 37% 上升至 2025 年 6 月的 52%。

3 Messages categorized as asking were more common than messages categorized as doing (requests for generated output such as plans, writing, or code) or expressing (such as idle conversation, reflection, or playing a role). The most common requests were for practical guidance (28.3 percent) or writing (28.1 percent), while seeking information was nearly as popular (21.3 percent).

被归类为「提问」的消息比被归类为「执行」（即要求生成计划、写作或代码等输出）或「表达」(例如闲聊、反思或扮演角色）的消息更常见。其中，最常见的请求是获取实用指导（28.3%）和写作任务（28.1%），而寻求信息的需求也几乎同样普遍（21.3%）。

1 Uses of ChatGPT for personal matters rose. In June 2024, messages divided roughly equally between work and non-work uses. By July 2025, roughly 73 percent of them likely were not related to work. (Overall use grew during that time. The number of likely non-work messages increased by around 8 times, while the number of work-related messages increased by more than 3 times.)

ChatGPT 在个人事务方面的使用量有所增加。在 2024 年 6 月，其消息量在工作和非工作用途之间大致平分。到 2025 年 7 月，其中约 73% 的消息很可能与非工作相关。（在此期间，ChatGPT 的总体使用量有所增长。非工作相关消息的数量增加了约 8 倍，而工作相关消息的数量则增加了 3 倍以上。）

2 Among non-work uses, the most common were seeking information (24.4 percent) or practical guidance (28.8 percent). When ChatGPT was used for work, the most common use was writing, mostly requests to edit, critique, translate, or otherwise transform existing text rather than produce all-new text.

在非工作用途中，最常见的需求是寻求信息（占 24.4%）或获取实用指导（占 28.8%）。当人们将 ChatGPT 用于工作时，最主要的用途是文本创作，这其中又以编辑、评论、翻译或对现有文本进行其他形式的转换居多，而非完全从零开始生成全新文本。

Behind the news: OpenAI said its report is the largest study of chatbot usage undertaken to date, but its peers have published similar research. Anthropic released its third Economic Index, which analyzes consumer and business use of its Claude models. Anthropic's study shows that Claude API users are much more likely to automate tasks than consumer users. Claude is used overwhelmingly for computational and mathematical tasks, but education, arts and media, and office and administrative support are steadily rising.

在新闻背后：OpenAI 宣称其报告是迄今为止规模最大的聊天机器人使用研究，但其竞争对手也发布了类似的研究成果。Anthropic 就发布了其第三份「经济指数」，这份报告深入分析了消费者和企业用户对 Anthropic 的 Claude 模型的使用情况。Anthropic 的研究表明，相比于普通消费者用户，使用 Claude API 的用户更倾向于利用它来自动化各种任务。目前，Claude 模型被广泛用于执行计算和数学任务，不过，在教育、艺术与媒体以及办公与行政支持等领域的应用也在稳步增长。

Why it matters: In OpenAI's study (and Anthropic's), AI users and uses are becoming more diverse. The initial user of AI chatbots was disproportionately likely to be based in the U.S., highly educated, highly paid, male, young, and focused on technology. Nearly 3 years after ChatGPT's introduction, they are far more varied, as are their wants, needs, and expectations.

重要性阐述：根据 OpenAI （以及 Anthropic ）的研究表明，人工智能（AI）用户和其使用方式正变得越来越多样化。AI 聊天机器人最初的用户群体，其特点通常是：主要来自美国、受过高等教育、收入较高、男性、年龄较轻且专注于科技领域。然而，在 ChatGPT 推出近 3 年后，AI 用户群体已经变得更加广泛，他们的需求、期盼和期望也同样呈现出多样化的趋势。

We're thinking: Early on, it seemed as though large language models would be most useful for work. But people are using them to seek information and advice about personal matters, plan their lives, and express themselves. It turns out that we need more intelligence in our whole lives, not just at the office.

我们曾认为：最初，大语言模型（Large Language Model）似乎主要在工作场合发挥作用。但现在，人们正在用它们来查询个人事务信息、获取建议、规划生活，甚至进行自我表达。事实证明，我们需要的智能不仅限于办公室，而是贯穿于我们生活的方方面面。

#### Sports Betting Goes Agentic

体育博彩也玩起 AI 智能体了

AI agents are getting in on the action of online sports gambling.

AI 智能体（AI agents）正在涉足在线体育赌博领域。

What's new: Several startups cater to betting customers by offering AI-powered sports analysis, chat, and tips, Wired reported. Some established gambling operations are adding AI capabilities to match.

最新进展：据《连线》（Wired）杂志报道，一些初创公司正通过提供由 AI（人工智能）驱动的体育分析、聊天功能和投注建议，来服务博彩客户。与此同时，一些老牌博彩公司也正积极引入 AI 能力，以保持市场竞争力。

How it works: Most AI sports-betting startups analyze which bets are the most statistically likely to pay off based on publicly available data. Increasingly, agents suggest specific bets. Only a few take bets from users and pay winnings to them, and fewer offer agents that actively place bets on third-party web sites on a user's behalf.

工作原理：大多数提供 AI 体育博彩服务的初创公司，会根据公开可用的数据，分析哪些赌注在统计学上最有可能带来回报。这些 AI 智能体（AI Agent）越来越多地直接向用户推荐具体的投注选项。然而，只有少数公司会直接接受用户的下注并支付奖金。更罕见的是，有公司提供 AI 智能体，能够代表用户在第三方网站上主动进行投注。

1 Monster.bet hosts MonsterGPT, a GPT-style chatbot that uses retrieval-augmented generation (RAG) to gather sports data from across the web while a proprietary algorithm predicts winners. The chatbot allows bettors to ask questions, and a history function tracks the results of bets they place and tailors its analysis to their strategies. Access to Monster costs $77 a month.

Monster.bet 推出了 MonsterGPT，这是一款模仿 GPT 风格的聊天机器人。它利用检索增强生成（Retrieval-Augmented Generation，RAG）技术从网络上抓取体育数据，同时结合其专有算法（proprietary algorithm）来预测比赛赢家。这款聊天机器人让投注者能够随时提问，并且其「历史记录」功能会追踪他们下注的结果，还能根据他们的投注策略来调整分析。要使用 MonsterGPT 服务，每月需要支付 $77。

2 Rithmm, based in Massachusetts, allows users to create their own "prediction models" using no-code tools. It also focuses on "prop bets" (not whether a team will win a game, but whether a player will achieve a particular outcome like score a touchdown). Subscriptions start at $30 a month.

总部位于马萨诸塞州的 Rithmm 公司，为用户提供无代码工具，帮助他们创建自己的「预测模型」。该公司还专注于「玩家表现投注（prop bets）」—— 这类投注并非预测哪支队伍会赢得比赛，而是押注某个选手能否达成特定表现，例如是否会触地得分。其订阅费用每月 $30 起。

3 With roots in fantasy sports, FanDuel is an older sports-betting operation that has integrated AI. Unlike many competitors, it takes bets and pays winnings. The mobile app integrates a chatbot called AceAI that helps users construct bets that require more than one event to occur; for example, that football champions Argentina will win a particular match and their star Lionel Messi will score at least one goal.

FanDuel 是一家老牌的体育博彩公司，最初起源于梦幻体育（fantasy sports）领域，现在已经整合了 AI 技术。与许多竞争对手不同的是，它不仅接受玩家的投注，还会支付奖金。它的移动应用程序内置了一个名为 AceAI 的聊天机器人（chatbot），能帮助用户组合需要多个事件同时发生的赌注；举例来说，比如投注足球冠军阿根廷队会赢得某场比赛，并且他们的明星球员 Lionel Messi 至少能打进一个球。

4 Sire (formerly DraiftKing [sic]) uses an agentic approach. AI agents currently have limited access to bank accounts and other payment services like PayPal or Venmo, so Sire's agents place bets using a crypto wallet. This enables an agent to react to events within a match and place bets automatically faster than a human can. For example, if a tennis player serves an ace, an automated bet can be made that the next serve will also be an ace. But instead of placing separate bets by individual bettors, Sire sells shares to customers who divide any profits from a wide range of bets.

Sire（之前是 DraiftKing [sic]）采用了一种 AI 智能体（AI Agent）方法。由于 AI 智能体目前对银行账户以及 PayPal 或 Venmo 等其他支付服务的访问权限有限，Sire 的智能体通过加密钱包进行投注。这使得智能体能够对比赛中的事件做出及时响应，并比人类更快地自动下注。例如，如果一名网球选手发出一个 Ace 球，智能体可以立即自动下注预测下一个发球也会是 Ace 球。但与单个投注者各自下注不同的是，Sire 向客户出售股份，让客户可以分享其从大量投注中获得的所有利润。

5 Few other betting agents have succeeded. The blockchain platform Zilliqa developed an agent called Ava for picking horse-race winners but abandoned it because synchronizing the agent, crypto wallets, and betting sites — all of which operate independently — was too slow. Some other purportedly agentic tools, including one called WagerGPT, collapsed under inflated promises.

其他投注 AI 智能体（AI Agent）鲜有成功案例。区块链平台 Zilliqa 曾开发了一款名为 Ava 的 AI 智能体，用于预测赛马获胜者，但最终放弃了。原因是 AI 智能体、加密钱包和投注网站 —— 这些系统都独立运行 —— 它们之间的同步过程过于缓慢。另一些号称是 AI 智能体工具的产品，包括一个名为 WagerGPT 的项目，也因夸大其词的承诺而未能兑现。

Behind the news: Most AI gambling startups are based in the United States, where online betting recently became legal. In 2024, Americans bet over $150 billion on legal sports wagers, up 22 percent from 2023. The share of online betting has grown steadily from 25 percent of the total in 2024 to 30 percent in 2025 and shows no sign of slowing down.

新闻背景：大多数 AI（人工智能）赌博初创公司都集中在美国，当地在线博彩业务最近才合法化。2024 年，美国人在合法体育投注上投入了超过 1500 亿美元，比 2023 年增长了 22%。在线博彩在总投注额中的份额也稳步增长，从 2024 年的 25% 上升到 2025 年的 30%，而且没有丝毫放缓的迹象。

Why it matters: Online gambling is an AI laboratory that uses nearly every emerging element of the technology. It requires quantitative reasoning to analyze bets, RAG to scour sports statistics and other relevant information, classification models to identify potentially profitable bets, and payment agents to place bets automatically. As these technologies advance, betting analysis and tools will advance with them.

重要意义在于：在线赌博可以说是一个名副其实的 AI 实验室，它几乎运用了这项技术所有新兴的组成部分。这包括需要定量推理来分析赌局，利用 RAG（Retrieval-Augmented Generation）来检索体育统计数据及其他相关信息，使用分类模型来识别那些可能有利可图的投注，以及部署支付 AI 智能体（AI Agent）来自动进行下注。随着这些人工智能技术的不断发展，相关的投注分析方法和工具也将同步提升。

We're thinking: Whether you gamble with cash or just wager your time and energy, learning more about AI is a smart bet.

我们认为：无论是投入金钱，还是只投入时间精力，多了解人工智能（AI）都是一项明智的「赌注」。

#### Faster Reinforcement Learning

更快的强化学习

Fine-tuning large language models via reinforcement learning is computationally expensive, but researchers found a way to streamline the process.

通过强化学习（reinforcement learning）微调大语言模型（Large Language Model）通常计算开销巨大，但现在研究人员找到了一种简化这个过程的方法。

What's new: Qinsi Wang and colleagues at UC Berkeley and Duke University developed GAIN-RL, a method that accelerates reinforcement learning fine-tuning by selecting training examples automatically based on the model's own internal signals, specifically the angles between vector representations of tokens. The code is available on GitHub.

最新进展：加州大学伯克利分校和杜克大学的 Qinsi Wang 及其同事开发了一种名为 GAIN-RL 的新方法。它能通过自动选择训练样本来加速强化学习微调，而选择的依据是模型自身的内部信号 —— 具体来说，是 Token（词元）向量表示之间的夹角。该方法的代码已在 GitHub 上开源。

Key insight: The cosine similarity between a model's vector representations of input tokens governs the magnitude of gradient updates during training. Specifically, the sum of those similarities that enter a model's classification layer, called the angle concentration, governs the magnitude of gradient updates. Examples with higher angle concentration produce larger gradient updates. The magnitude of a gradient update in turn determines the effectiveness of a given training example: The larger the update, the more the model learns. Prioritizing the most-effective examples before transitioning to less-effective ones enhances training efficiency while adding little preprocessing overhead.

关键见解：模型对输入 Token 的向量表示之间的余弦相似度，决定了训练过程中梯度更新的幅度。具体来说，那些进入模型分类层的相似度之和 —— 我们称之为角度集中度（angle concentration)—— 决定了梯度更新的大小。角度集中度越高的训练样本，会产生更大的梯度更新。梯度更新的幅度反过来也决定了给定训练样本的有效性：更新越大，模型学习到的内容就越多。因此，在转向效果较差的样本之前，优先处理最有效的样本，可以显著提高训练效率，同时只会增加极少的预处理开销。

How it works: The authors separately fine-tuned Qwen 2.5 1.5B, Qwen 2.5 7B, and Llama 3.2 3B using the GRPO reinforcement learning algorithm with examples ordered according to their angle concentration. The datasets included math problems in GSM8K and AMC 23, and coding problems in LiveCodeBench and HumanEval+.

工作原理：研究人员分别对 Qwen 2.5 1.5B、Qwen 2.5 7B 和 Llama 3.2 3B 这几个模型进行了微调（fine-tuned）。他们采用的是 GRPO 强化学习（reinforcement learning）算法，并且在训练时，将示例按照它们的「角度集中度（angle concentration）」进行排序。这些训练数据包含了来自 GSM8K 和 AMC 23 的数学问题，以及 LiveCodeBench 和 HumanEval+ 的编程问题。

1 Given a training set, the authors calculated the angle concentration of each example by performing a single forward pass on the entire dataset. They sorted examples from highest to lowest angle concentration.

给定一个训练集，作者们通过对整个数据集进行一次前向传播（forward pass），计算出每个示例的角度集中度（angle concentration）。随后，他们根据角度集中度从高到低对这些示例进行了排序。

2 They fine-tuned the models, focusing first on examples with the highest angle concentrations and shifting toward lower angle concentrations as training progressed. They tracked the models' learning according to accuracy and the angle concentration on each batch of data. They shifted the focus more toward less-effective examples as the model learned and shifted less when it struggled.

研究人员对模型进行了微调，最初将重心放在那些「角度集中度」最高的样本上，并随着训练的推进，逐步转向处理「角度集中度」较低的样本。他们通过模型的准确率和每个数据批次（batch of data）的「角度集中度」，来监测模型的学习进展。具体来说，当模型学习顺利时，他们会更多地将训练重点转移到那些模型表现不佳的样本上；而当模型遇到学习障碍时，这种重点转移的幅度就会减小。

3 They continued training for 200 epochs.

实验中，模型继续训练了 200 个周期（epoch）。

Results: The authors compared models that were fine-tuned using GAIN-RL with counterparts that used GRPO performed on randomly ordered examples. GAIN-RL generally accelerated learning by a factor of 2.5.

结果：研究人员将使用 GAIN-RL 进行微调的模型，与在随机排序数据上使用 GRPO 进行训练的同类模型进行了比较。结果显示，GAIN-RL 通常能将学习过程（即训练速度）提升 2.5 倍。

1 Whether the task involved math or coding, GAIN-RL took 70 to 80 training epochs to match the performance of fine-tuning using typical GRPO for 200 epochs.

无论是数学任务还是编程任务，GAIN-RL 都只需 70 到 80 个训练周期（epochs），就能达到传统 GRPO 经过 200 个周期微调后所实现的性能。

2 For instance, on GSM8K, Qwen 2.5 Math Instruct 7B after GAIN-RL fine-tuning achieved 92.0 percent accuracy after 70 epochs. The version fine-tuned on typical GRPO needed 200 epochs to reach the same performance.

举例来说，在 GSM8K 数据集上，经过 GAIN-RL 微调的 Qwen 2.5 Math Instruct 7B 模型，在 70 个训练周期后准确率达到了 92.0%。相比之下，使用传统 GRPO 进行微调的版本则需要 200 个周期才能达到同样的性能。

Why it matters: Many strategies for ordering training examples rely on external, often expensive heuristics based on their difficulty, for example judgments by human annotators or a proprietary LLM. By using a simple signal generated by the model itself, this method provides a direct and efficient way to identify the most effective examples, making reinforcement learning much faster.

重要性：许多用于安排训练样本顺序的策略，往往依赖于外部的、通常成本高昂的启发式方法，这些方法依据训练样本的难度来确定，例如人类标注者的评估，或是由专有的大语言模型（LLM）给出的判断。而通过利用模型自身生成的一个简单信号，这种新方法提供了一种直接且高效的途径来找到最有效的训练样本，从而显著加快强化学习（reinforcement learning）的效率。

We're thinking: Ordering training examples is much older than applying reinforcement learning to fine-tuning large language models. Applying earlier methods to more recent approaches holds many advances in machine learning!

我们认为：对训练示例进行排序（Ordering training examples）这一概念，远比将强化学习（Reinforcement Learning）应用于微调大语言模型（Large Language Model）的历史要悠久得多。将早期的方法应用于更近期的人工智能（AI）技术，有望在机器学习（Machine Learning）领域带来诸多进展！