## 20250315Model-Context-Protocol-MCP-clearly-explained-why-it-matters

Everyone is talking about MCPs. It's gone completely viral. But the reality is, most people have no idea what MCPs are and what they mean and what are the startup opportunities associated with it. So, in this episode, I brought Professor Rossmike, who is probably the best explainer of technical concepts in a really easy way that someone who's non-technical can really understand.

大家都在谈论 MCPs。它已经彻底火了。但现实情况是，大多数人并不知道 MCPs 是什么，它意味着什么，以及与之相关的创业机会有哪些。所以，在这一集里，我请来了 Rossmike 教授，他或许是技术概念的最佳讲解者，能够用一种非技术人员也能真正理解的简单方式进行解释。

I brought him on. He explains it beautifully in such a short amount of time. And if you stick to the end, you'll hear a couple of his startup ideas that incorporate MCPs. So enjoy the episode and see you soon.

我邀请了他。他在很短的时间内就将内容解释得非常透彻。如果您能听到最后，还会听到他关于结合 MCP 的一些创业想法。希望您喜欢这一集，我们很快再见。

All right. Well, we got Professor Ross Mike on the pod. And the reason why we have him is because I don't know what the hell MCPs are. And I've been seeing it on X, and I need a succinct, clear, Professor Ross Mike explanation.

好的。嗯，我们请到了 Ross Mike 教授来播客节目做客。我们请他来的原因是我完全不知道 MCP 是什么。我一直在 X 平台上看到这个词，我需要 Ross Mike 教授给一个简洁明了的解释。

Yes, I've read a bunch of threads on it, and I've seen a couple videos on it, but there's nothing like a Ross Mike explanation. So I'm here for the, what do I need to know about MCPs? And that's why you're here. Thank you for coming on. I appreciate that. Thank you very much. Yeah, class is definitely in session. I'll just start sharing my screen.

是的，我已经看了很多关于它的讨论，也看过一些相关的视频，但总觉得不如 Ross Mike 解释得透彻。所以我来这里就是想问，关于 MCPs 我到底需要知道些什么？而这正是你今天来这里的目的。谢谢你过来。我真的很感谢。非常感谢。好的，现在正式开始上课。我这就开始分享我的屏幕。

### 01

Okay, so understanding MCP is really important, but you also realize the benefits and why it's sort of a big deal, but not really at the same time. You see, one of the things in programming land that we have and that programmers love are standards. And the reason why standards are important is they allow for us engineers to build systems that communicate with each other.

好的，所以理解 MCP 确实很重要，不过你也会意识到它的好处，以及为什么说它既算不上什么惊天动地的大事，但也确实有其重要之处。你看，在编程这个圈子里，我们有一样东西，程序员们特别喜欢，那就是标准。而标准之所以重要，是因为它们能让咱们工程师构建出相互之间可以顺畅沟通的系统。

The most popular one that you you might have heard of or you might not, and you don't really need to know the details, is REST, REST APIs. And they're basically a standard that every company follows when they construct their APIs, when they construct their services for me as an engineer to be able to connect with them.

其中最流行的一种你可能听说过，也可能没听说过，而且你并不需要了解具体细节，那就是 REST，也就是 REST API。它们基本上是每个公司在构建其 API 和服务时会遵循的一个标准，这样工程师就可以连接到这些服务。

Now, understanding that engineering is all about standards and having these formalities we follow to make life easier. When we think of in the context of an LLM, I want you to understand this one important thing. LLMs by themselves are incapable of doing anything meaningful. What do I mean by that? If you remember the first, you know, chat GBT3, or was it 3.5? I'm not sure. But if you just open any chatbot, and you tell it to send you an email, it won't know how to do that.

现在，我们知道工程学讲究标准，并且遵循各种规范和流程是为了让事情变得更容易。当我们来理解大语言模型（LLM）时，我想让你明白一个非常重要的事情。大语言模型本身无法独立完成任何有意义的任务。这是什么意思呢？如果你还记得最初的 ChatGPT-3，或者也许是 3.5（我不确定），如果你打开任何聊天机器人，告诉它给你发送一封电子邮件，它并不知道该怎么做。

It will just tell you, hey, I can't send you an email. The most you can do with an LLM is ask it questions, maybe ask it to tell you about some historical figure, whatever it may be. LLMs are truly incapable of doing anything meaningful. And what I mean by meaningful, it'd be nice if it could send me an email, if it could do some specific task on my behalf. But the only thing an LLM in its current state is good at is predicting the next text, right?

它只会告诉你：「嘿，我不能给你发邮件。」你用大语言模型（LLM）最多能做的就是问它问题，也许是让它告诉你一些历史人物的事情，或者其他任何你知道的事情。目前，LLM 确实无法完成任何「有意义」的任务。而我这里说的「有意义」，是指如果它能帮我发送一封邮件，或者代表我完成一些特定的任务，那就太好了。但目前状态下的 LLM 唯一擅长的事情就是预测下一个文本，对吧？

So for example, if I say my big fat Greek, an LLM with all the data source with all its training material will determine that the next word is wedding, right? So this is the most an LLM by itself that it could do, right?

所以举个例子，如果我说「我的又大又胖的希腊」，一个拥有丰富训练数据的大语言模型（LLM）会根据其训练内容判断下一个词是「婚礼」，对吧？这基本上就是一个 LLM 独立能做的极限了，对吧？

The next evolution was developers figured out how to take LLMs and combine them with tools. And you can think of a tool like an API. For example, most of us are where ChatGPT and these other chatbots are able to search the internet. For example, perplexity, right? Perplexity gives you the option to chat with an LLM, but that LLM has the ability to fetch information from the internet and present that to you.

下一次演进是开发者们发现了将大语言模型（LLMs）与工具结合的方法。你可以把工具想象成一个 API。举个例子，我们大多数人都知道 ChatGPT 和其他这些聊天机器人能够搜索互联网。比如 perplexity，对吧？Perplexity 提供了与大语言模型聊天的选项，而这个大语言模型能够从互联网获取信息并展示给你。

The LLM itself is not capable of doing that. But what they've done is they've constructed a tool. They've given the LLM access to an external service, right? And there's plenty of these services, right? I think there's Brave Search, chat, OpenAI offers an API now.

大语言模型（LLM）本身并不能做到这一点。但研究人员构建了一个工具，赋予了 LLM 访问外部服务的权限。现在有很多这样的服务，例如 Brave Search、各种聊天服务，OpenAI 也提供了 API 接口。

So LLMs have started to become a bit more powerful when we connected tools to them, right? I can give you an example. Let's say every time I get an email, I want there to be an entry in a spreadsheet. Now, most of you know, there are services like Zapier, NNA, or any of those automation services. If I build out an automation and connect that to my LLM, it just became a bit more meaningful.

所以当我们将工具连接到大语言模型（LLMs）时，它们已经开始变得更加强大，对吧？我可以给你一个例子。假设我每次收到电子邮件时，都希望在电子表格中记录一条信息。现在，你们大多数人都知道，有一些服务，例如 Zapier、NNA 或其他类似的自动化服务。如果我构建一个自动化流程并将其连接到我的大语言模型，这个过程就变得更加有用了。

Now, that's awesome and cool, but it gets really frustrating when you want to build an assistant that does multiple things. Imagine, search the internet, read your emails, summarize this. You start to become someone who glues a bunch of different tools to these LLMs. And it can get very frustrating, very cumbersome.

现在，这确实很棒很酷，但当你想要构建一个能做多件事情的助手时，就会变得非常令人沮丧。想象一下，你要搜索互联网、阅读电子邮件、总结内容。你开始变成一个需要将一堆不同的工具「连接」或「集成」到这些大语言模型（LLM）中的人。这会变得非常令人沮丧，也非常麻烦。

If you're wondering why we don't have an Ironman level Jarvis assistant, is because combining these tools, making it work with the LLM is one thing. But then stacking these tools on top of each other, making it cohesive, making it work together is a nightmare itself. And this is where we're currently at.

如果你好奇为什么我们还没有一个钢铁侠贾维斯那样的助手，原因在于：将这些工具与大语言模型（LLM）结合并让它们一起工作是一回事；但更具挑战的是，将这些工具层层叠加，让它们紧密协作、协同一致，这本身就是一场噩梦。而这正是我们目前面临的困境。

And before I continue, does this make sense? This is where we started, LLMs by themselves, write me a poem, tell me about World War I. And then the second evolution is, oh, we now have tools, right? We now have these things, these external services that we can connect to our LLM. The problem here is they're difficult. It's annoying.

在我继续之前，让我先问一下，这说得通吗？我们最初的应用场景，就是大语言模型（LLM）本身能做的事情，比如让它写一首诗，或者讲讲第一次世界大战。然后，第二阶段的演变是，我们现在有了工具，对吧？有了这些外部服务，我们可以将它们连接到我们的大语言模型。但这里的问题在于，这些工具用起来很复杂，很麻烦。

And as someone who works at an AI startup, Tempo, and we have a lot of tools, like for example, we do a search, you have to find an external service. You have to connect it to the LLM and you have to make sure the LLM doesn't hallucinate or do something stupid. And believe it or not, as cool as LLMs are by themselves, they're very, very dumb. But these tools make them just a bit more capable. So this is where we're at. Greg, we good so far? It's crystal clear. I'm loving this. Beautiful.

而且作为一名在 AI 初创公司 Tempo 工作的人，我们有很多工具。比如，在进行搜索时，你需要找到一个外部服务，将它连接到大语言模型（LLM），并且要确保 LLM 不会「胡说八道」（产生幻觉）或者犯错。信不信由你，尽管 LLM 本身看起来很厉害，但它们其实能力非常有限。不过，这些工具能让它们变得更强大一些。这就是我们目前的进展。Greg，到目前为止我讲清楚了吗？非常清楚。我很喜欢。太棒了。

Quick break in the pod to tell you a little bit about Startup Empire. So Startup Empire is my private membership where it's a bunch of people like me, like you, who want to build out their startup ideas. Now they're looking for content to help accelerate that. They're looking for potential co-founders. They're looking for tutorials from people like me to come in and tell them, how do you do email marketing? How do you build an audience? How do you go viral on Twitter? All these different things. That's exactly what Startup Empire is. And it's for people who want to start a startup but are looking for ideas, or it's for people who have a startup but just they're not seeing the traction that they need. So you can check out the link to startupempire.co in the description.

播客中插播一段，来向您介绍一下 Startup Empire。Startup Empire 是我的私人会员社群，里面汇聚了许多像我一样、也像您一样，渴望实现创业想法的人们。他们正在寻找能够加速创业进程的内容，寻找潜在的联合创始人，也在寻找由像我这样的人提供的教程，告诉他们如何进行电子邮件营销？如何建立受众？如何在 Twitter 上实现病毒式传播？所有这些方面，正是 Startup Empire 提供的。它适合那些想开始创业但正在寻找想法的人，也适合那些已经创业但还没有获得所需关注度或进展的人。您可以在描述中找到 startupempire.co 的链接进行了解。

Now, enters MCP. And what does MCP mean? I think the simplest way, right, without getting too technicals, I've read the threads too. And as a technical person, I appreciate it. But for the non-techie, I can assume it's frustrating.

现在，轮到 MCP 登场了。那么，MCP 究竟是什么意思呢？我认为最简单的方式，就是尽量避免过于技术性的解读。我知道有些相关的技术讨论文章，作为技术人员，我能理解其中的精妙之处。但对于非技术背景的读者来说，这些内容可能会让人感到困惑和沮丧。

Think of it this way. Think of every tool that I have to connect to, to make my LLM valuable as a different language. So tool one's English, tool two Spanish, tool three is Japanese, right? And imagine every tool, it's its own language. And it's not that there isn't a standard for how APIs work, but every service provider constructs their APIs differently. There's different information you have to pass. There's just various degree of things that you have to set up that, again, it just feels like gluing a bunch of different things together. Will it work? Yes, but at scale, it gets very difficult.

换个角度来想。把我需要连接的每一个工具，才能让我的大语言模型（LLM）发挥价值，想象成一种不同的语言。比如，工具一是英语，工具二是西班牙语，工具三是日语，是吧？你可以想象每个工具都有自己的语言。虽然 API 的工作方式并非没有标准，但每家服务提供商构建 API 的方式都不一样。你需要传递的信息不同，需要设置的各种参数和细节也不同。就像是把一堆不同的零件拼凑在一起。这样能工作吗？当然可以。但一旦规模扩大，就会变得异常困难。

MCP, you can consider it to be a layer between your LLM and the services and the tools. And this layer translates all those different languages into a unified language that makes complete sense to the LLM, right? So it's the evolution of LLM plus tools. But in this evolution, it just makes it makes it very simple for the LLM to connect and to access different outside resources, right? Because that's what tools are at the end of the day.

你可以把 MCP 理解为在大语言模型（LLM）与各种服务和工具之间架设的一层。这一层的作用是将那些形形色色的「语言」统一翻译成一种对 LLM 来说完全可以理解的语言。你可以把它看作是 LLM 与工具相结合的进一步发展。通过这种演进，LLM 连接和访问各种外部资源变得异常简单，因为毕竟工具的本质就是提供这些外部能力。

So with MCP, I'm able to connect to an outside data source, an outside database, maybe a tool like Convex or Supabase, right? Imagine, I just tell the LLM, you know what, create me a new entry in my database. And it's connected to my database via MCP, and it knows exactly what to do and how to do.

所以借助 MCP，我能够连接到一个外部数据源，比如外部数据库，或者像 Convex、Supabase 这样的工具，对吧？想象一下，我只需告诉大语言模型，让它在我的数据库中创建一个新条目。而它通过 MCP 连接到我的数据库后，就完全知道该如何操作了。

In the second evolution, LLMs and tools, there's a lot of manual work that goes on. There's a lot of step-by-step planning that you have to do. And there's a lot of edge cases where it can fail. And this is why, again, none of us, as exciting as the space is, none of us have a Jarvis level assistant yet. It feels like we're there and we're close, but this system makes it so that it's very difficult.

在第二次演进中，也就是大语言模型和工具阶段，仍需要大量的人工干预。你需要进行大量的分步骤规划。而且存在许多可能导致失败的边缘情况。这就是为什么，即使这个领域令人振奋，我们仍然没有达到拥有 Jarvis 级别助手的程度。感觉我们已经很接近了，但现有系统使得实现这一目标非常困难。

And what's frustrating is this. Imagine, let me think of a simple service, a simple tool. Imagine every time a Slack message comes, your LLM reads that Slack message and it shoots you a text, right? Sounds pretty trivial. Here's the frustrating part. Imagine Slack updates their API or the text service updates, makes a change. And let's say that service is connected to other services, or you have some sort of like automation step-by-step thing that you've planned. It becomes a nightmare. It becomes terrifying.

而令人沮丧的是这种情况。想象一个简单的服务或工具。设想一下，每当 Slack 收到一条消息，你的大语言模型（LLM）读取这条消息，然后给你发送一条文本通知，对吧？这听起来相当简单。但令人沮丧之处在于：想象一下 Slack 更新了他们的 API，或者文本服务进行了变更。如果这个服务连接到其他服务，或者你规划了一些自动化的分步流程。这就会变成一场噩梦，变得非常可怕。

And this is why even in the age of LLMs, good engineers will still get paid because stuff like this exists. But what MCP does, it unifies the LLM and the service, right? It creates this layer where the service and the LLM can communicate efficiently.

而这就是为什么即使在大语言模型时代，优秀工程师依然能够获得高薪，因为这些复杂的技术难题依然存在。MCP 的作用在于它将大语言模型和服务统一起来，它创建了一个层，在这个层上，服务和大语言模型能够高效地进行通信。

### 02

Now, let's get into some practicality. You can think of the MCP ecosystem as follows. You have an MCP client, you have the protocol, you have an MCP server, and you have a service, right? An MCP client is something like Tempo, Windsurf, Cursor, and they are basically the client-facing side, the LLM facing side of this ecosystem. The protocol, again, is that two way connection between the client and the server. And the server is what translates that external service, its capabilities and what it can do to the client.

现在，我们来探讨一些实际应用。你可以把 MCP 生态系统理解为由以下几个部分组成：一个 MCP 客户端、一个协议、一个 MCP 服务器和一个服务。MCP 客户端，例如 Tempo、Windsurf 和 Cursor，基本上是这一生态系统中面向用户端和 LLM 的部分。协议是客户端和服务器之间的双向连接。而服务器的作用是将外部服务的能力转换后提供给客户端。

And that's why between the MCP client and the MCP server, there's an MCP protocol. But here's the fascinating part. And this is why I think Anthropic, they're playing 3D chess when they built this, is the way this is architected, the MCP server is now in the hands of the service provider.

这就是为什么在 MCP 客户端和 MCP 服务器之间，存在一个 MCP 协议。但这里有趣的一点在于，我认为这也是为什么 Anthropic 在构建这个系统时考虑得如此周全（就像在玩 3D 国际象棋一样），在这样的架构下，MCP 服务器现在掌握在服务提供商手中。

So if let's say me and Greg run a dev tool company, right, where maybe we're doing a database, right? Like we're like, listen, we're going to build the best database company in the world. And we want people's LLMs to have access to this database. It is now on us to construct this MCP server so that the client can fully access this. So Anthropic in a way sort of said, listen, we want our LLMs to be more powerful, more capable, but it's your job to figure this out.

所以，假设我和 Greg 经营一家开发者工具公司，比如我们正在开发一个数据库。我们可能会说：「我们要打造世界上最出色的数据库公司。」我们希望用户的大语言模型（LLM）能够访问这个数据库。那么，构建这个 MCP 服务器就成了我们的责任，以便客户端能够完全访问它。所以，Anthropic 在某种程度上表示：「听着，我们希望我们的大语言模型更强大、能力更强，但如何实现这一点，就靠你们自己去解决了。」

And this is why you've noticed all the external service providers are now building different MCP servers. They're building out repos and all this stuff. Right? So this is a big deal in a sense where LLMs are going to be more capable. But from a technological perspective, all they did was create a standard, a standard that it seems like all companies and all engineers are going to agree upon because you can construct any system, any API, however you please.

这就是为什么你注意到所有外部服务提供商现在都在构建不同的 MCP 服务器。他们正在构建代码仓库（repos）和所有这些东西。对吗？所以从某种意义上说，这意义重大，因为大语言模型（LLM）将会变得更加强大。但从技术角度来看，他们所做的只是创建了一个标准，一个似乎所有公司和所有工程师都会同意的标准，因为你可以随心所欲地构建任何系统、任何 API。

The problem is if you want to scale, you want to grow, you want other developers, other businesses to connect and work with your service, it has to be in a fashion that makes sense for them. Imagine if all of us just spoke different languages, but standards allow us to communicate in a way that makes sense to all of us. And MCP is that for LLMs because LLMs by themselves are not that capable. They're systems that have great predictability and they know how to predict the next word. But when you add this MCP protocol as a whole, you now have a way for it to be capable of doing important stuff.

问题在于，如果你想扩展、想成长，想让其他开发者和企业与你的服务建立连接并展开合作，那么这一切都必须以一种对他们而言合理且方便的方式进行。想象一下，如果我们每个人都说着不同的语言，但标准的存在使得我们能够以一种对所有人都有意义的方式进行交流。而 MCP 对于大语言模型（LLMs）来说，就扮演着这样的角色。因为 LLMs 本身的能力是有限的，它们只是一种预测能力很强、懂得如何预测下一个 Token 的系统。但当你将这个完整的 MCP 协议加入进来时，你就为 LLM 提供了一种能够执行重要任务的方式。

Now, understanding all this, it's not all sunshine and rainbows. There are some technical challenges. If you notice, if anyone has set up an MCP server on any of their favorite MCP clients, it's annoying. There's a lot of downloading. You have to move this file. You have to copy this, that, and a third. And it's a lot of local stuff. There are some kinks that have to be figured out.

不过，理解了所有这些之后，我们也要看到并非全是坦途。其中存在一些技术挑战。如果你注意到了，或者有人曾在自己喜欢的 MCP 客户端上搭建过 MCP 服务器，就会知道这过程有多麻烦。需要下载大量文件，还得移动这个文件，复制那个文件，还有别的一些操作。很多事情都得在本地处理。这里面还有一些难题需要解决。

But once this is figured out or finalized, polished, or maybe they update the standard, or maybe someone comes up with a better one, we start to enter a world where LLMs start to become more capable. And that is literally all what MCP is, just making LLMs more capable. We're trying, we're doing that with tools right now. It's kind of working. But MCP seems to be the next evolution.

但一旦这个问题得到解决、最终确定并完善，或者即使他们更新了标准，或者有人提出了一个更好的方案，我们就会开始进入一个大语言模型（LLMs）变得更加强大的时代。而 MCP 的核心目标，正是让大语言模型具备更强的能力。目前我们正在尝试利用工具来实现这一点，并且取得了一些成效。但 MCP 似乎代表着下一个发展方向。

I think, Greg, I saw your latest video. Manus Manus is a great example of number two. They have tons of tools and kudos to them. They've engineered it well in a way where, you know, they work well cohesively. I didn't get to try it out. So I'm just looking at what people have done. But I can tell you this, it's a lot of engineering hours. It's a lot of one change happens, something broke, someone's on call and not sleeping. But with MCP, it's structured in a way where if we all follow this standard, the LLM will have access to everything it needs and we will all be happy users.

Greg，我想我看了你的最新视频。Manus 是一个很好的例子，它体现了第二点。他们有很多工具，值得称赞的是，他们将其精心设计，使其能够很好地协同工作。我没有亲自试用过，所以只是看别人做的。但我可以告诉你的是，这需要大量的工程时间。一旦发生微小的改变，就会有东西出现故障，有人需要值班，无法安睡。但是使用 MCP，它的结构方式是，如果我们都遵循这个标准，大语言模型（Large Language Model）将能访问它需要的一切，用户体验也会非常顺畅。

So in short, that is literally all what MCP is. It's not Einstein's fifth law of physics or anything crazy like that. It's literally a standard for LLMs. And it's exciting. It's something to be excited about. And yeah, I hope that clarified. I just kept rambling. So I apologize for that.

所以简单来说，MCP 就是这么回事。它可不是什么爱因斯坦的第五物理定律之类的深奥理论。它实际上是一个关于大语言模型（LLM）的标准。这一点令人振奋，确实是件值得期待的事情。是的，希望我解释清楚了。刚才有些语无伦次，为此我表示歉意。

### 03

No, this is exactly what I wanted. I want to end on one question for you. So this is now clear to to me what MCPs are. But my question is, well, before I even ask my question, every time there's been a popularized protocol, for example, HTTPS or SMTP, examples like that, there's been a lot of big businesses that were created on top of it. And there's been basically this like why now, you know, why this is opening of opportunities.

不，这正是我想要的。我想用一个问题来结束。所以现在我已经很清楚 MCP 是什么了。但我的问题是，在我提出问题之前，每当出现某种流行的协议时，例如 HTTPS 或 SMTP 这样的例子，都会在其基础上涌现出许多大型企业。并且基本上都会出现「为什么是现在」这样的疑问，你知道的，为什么这个时机带来了新的机会。

Yeah, I think that's a great question. I think if I were, so I'll speak to the technical and the not technical. To the technical, there's a lot of things that a technical person can do here. I just don't have time, Greg. But one thing I was thinking of was like an MCP app store. And I'll just give this idea out for free because this this podcast is all about ideas.

是的，我认为这是一个很棒的问题。我想，如果是我来回答，我会从技术和非技术两个方面来说。对于技术人员而言，他们可以做很多事情。Greg，我只是没有足够的时间。但我想到的一件事是，可以创建一个类似 MCP 应用商店的东西。我免费分享这个想法，因为我们这个播客就是畅所欲言，分享各种想法的。

Basically, there's a lot of these repos out there of MCP servers. And it'd be cool if someone can go on a site. I even bought the domain. It does nothing. But again, please, anybody like steal this idea. I bought the domain and it'd be cool if someone could go on, like, look at the different MCP servers there. They see the GitHub code and whatever, and they can click like install or deploy. And that server is deployed and gives them a specific URL. And then they can paste that in an MCP client and work that out. So for the technical person, if you make millions, all I ask is just, you know, send me a thousand dollars.

基本上，有很多 MCP 服务器的代码库（repos）。如果有人能上一个网站，那会很酷。我甚至买了域名。它目前什么功能也没有。但再说一遍，请大家尽管拿走这个想法。我买了域名，如果有人能上去，比如，看看那里不同的 MCP 服务器代码，看到 GitHub 代码等等，他们可以点击安装或部署。然后那个服务器就被部署了，并给他们一个特定的 URL。然后他们可以将它粘贴到 MCP 客户端中并开始使用。所以对于有技术能力的人来说，如果你靠这个赚了几百万，我只希望能得到一千美元的回报。

But for the non-technical person, what I would really focus on is I would just stay up to date with the platforms that are building out MCP capability and just see where the standards are going. Right? Because like you said, when the standards are finalized, I don't know if MCP has fully won. I think it needs to be challenged. Or I don't know if Anthropik is going to make an update. We don't know. It's very early. But I would say keep very close attention to what the final standard is going to be, because once that standard is finalized and all these service providers start to like, you know, build out their MCP or whatever thing it is, you can now start to integrate much seamlessly and much easier.

但对于非技术人员来说，我真正建议关注的是，密切关注那些正在开发 MCP（Multi-Cloud Platform）功能的平台，看看行业标准会如何演变。对吗？因为就像你说的，当标准最终确定时，我不知道 MCP 是否会最终胜出。我认为它可能会面临挑战。或者，我也不知道像 Anthropic 这样的公司是否会推出新的更新。这一切都还是未知数，毕竟现在还处于早期阶段。但我会说，要非常关注最终的标准会是什么样子，因为一旦标准确定下来，并且所有的服务提供商都开始基于这个标准构建他们的 MCP 或相关服务时，你就可以更无缝、更轻松地进行集成了。

This is why, again, every week there's a new chatbot interface with new tools, and it wins. Because this part, step number two, is not easy, especially making it cohesive and making it work fast. Right? Like I can sit in two hours and build something like this. But building out that user experience, making it flawless, limiting the hallucinations. It's very, very hard. I mean, this is a lot of the work we do at Tempo, but this makes it so that integrating is a lot easier. And you can think of these as like Lego pieces that you can continue to stack to stack.

这就是为什么，我们看到每周都有新的聊天机器人界面带着新工具出现，并且它们能够成功的原因。因为第二步，也就是构建这些界面并使其连贯且运行迅速，绝非易事。对吧？我可能花两个小时就能搭出个大概。但要打造出那种出色的用户体验，使其完美无瑕，并最大程度地减少幻觉，这实在是太难了。这确实是我们 Tempo 团队正在投入大量精力去做的。但这样做的好处是，集成会变得容易很多。你可以把它们想象成一块块乐高积木，可以不断地叠加起来。

So for my smart and wise business owners, startup ideas, podcast enjoyers, I would really just keep a close attention, right? I think even for myself, I don't think with this MCP stuff, we're at a place where any shots can be fired that make any smart business decision. But this is one of those things where you just you sit and you watch and you're just observing and learning. And when the right thing at the right time happens, you strike.

所以对于我那些聪明又有远见的企业主们，那些正在构思初创企业点子的人，以及喜欢听播客的朋友们，我的建议是大家一定要密切关注，你说对吗？我觉得即便是对我来说，关于这个 MCP 的事情，我们目前还没有到可以轻易出手、做出任何明智商业决策的时候。但这就像是那种需要你静静地坐着，观察，学习，然后在正确的时间，当正确的机会出现时，你再果断出击。

So I don't see any crazy business opportunities right now for a non-technical person, even for a technical person. Like, imagine if OpenAI comes with a standard tomorrow and we all just shift to that. Right? It's very early stages. But I think understanding how this works means you understand how the next thing works. And when that becomes finalized, you hit the ground running. Amen.

所以目前我看不到有什么特别惊人的商业机会，无论是对非技术人员还是技术人员来说都是如此。比如，想象一下如果 OpenAI 明天发布一个标准，然后我们都转向那个标准。对吧？现在还处于非常早期的阶段。但我认为理解这项技术是如何工作的，意味着你也能理解接下来的发展方向。当这些方向最终确定下来时，你就能快速上手了。没错。

All right, Ross Mike, Professor Ross Mike, there's no one like you. We'll include in the show notes where you can follow. Amen. All right, Ross Mike, Professor Ross Mike, there's no one like you. We'll include in the show notes where you can follow him for more really clear explanations around this whole AI coding world and uh dude, I'll see you in Miami in a few weeks. Yeah man, I appreciate you. I'm booking my flight soon. So yeah, definitely bro, definitely, bro. I'll see you soon. Thank you, everybody.

好的，Ross Mike 教授，你真是太棒了（没有人像你一样）。我们会在节目说明中附上你可以关注他的地方，以便他能对整个 AI 编码领域做出更多清晰的解释。呃，伙计，几周后迈阿密见。是啊兄弟，太感谢你了。我很快就订机票。所以，是的，兄弟，迈阿密见。谢谢大家。