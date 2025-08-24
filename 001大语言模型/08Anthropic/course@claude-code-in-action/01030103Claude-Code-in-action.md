## 0103Claude-Code-in-action

[Claude Code in action](https://anthropic.skilljar.com/claude-code-in-action/303242)

Claude Code comes with a comprehensive set of built-in tools that handle common development tasks like reading files, writing code, running commands, and managing directories. But what makes Claude Code truly powerful is how intelligently it combines these tools to tackle complex, multi-step problems.

Claude Code 内置了一套完善的工具，能够处理日常开发中常见的任务，例如读取文件、编写代码、运行命令以及管理目录。但 Claude Code 真正强大的地方在于，它能智能地组合这些工具，从而解决复杂的多步骤问题。

### 01

Just a moment ago, I made some pretty big claims by saying that Cloud was an expert at making use of tools, and that Cloud Code was easily extensible. Naturally, you might be a little skeptical, so I'd like to give you a few quick demonstrations.

就在刚才，我做了一些「大胆」的断言：Cloud 是利用工具的专家，而且 Cloud Code 很容易扩展。你听了之后，自然可能会有点怀疑，所以我打算快速给你展示几个例子。

On this table are the default tools that are available in Cloud Code. It has all the abilities you would expect, like reading files, writing files, running commands, and so on. I'm going to show you a couple of tasks completed using Cloud Code, and in each case, it will use this set of tools in rather intelligent ways. And in at least one task, I'll even give Cloud an additional new set of tools to make use of. Not only will this process give you a good idea of what Cloud Code can do right out of the box, but hopefully you will also see how easily you can extend Cloud Code with more functionality.

本表列出了 Cloud Code 中默认可用的工具。它拥有您期望的所有能力，例如读取文件、写入文件、运行命令等。我将向您展示几个使用 Cloud Code 完成的任务，在每项任务中，Cloud Code 都将以相当智能的方式运用这套工具。在至少一个任务中，我甚至会为 Cloud Code 提供一套额外的新工具供其使用。这个过程不仅能让您很好地了解 Cloud Code 的开箱即用功能，而且希望能让您看到扩展 Cloud Code 功能是多么容易。

Here's my first task for Cloud Code: I'm going to ask it to find and optimize performance issues in the Chalk library. In case you're not familiar with it, Chalk is a JavaScript package. Here's the documentation for it. Now, this is a very small library that has one very simple purpose. All it does is print out text in nicely formatted colors, so like exactly as you see in this example screenshot right here. So you can give the text colors or backgrounds and formatting, all that kind of stuff.

这是我交给 Cloud Code 的第一个任务：我将要求它查找并优化 Chalk 库中的性能问题。如果你不熟悉 Chalk，它是一个 JavaScript 包，这里是它的文档。Chalk 是一个非常小的库，目的非常简单，它所做的就是将文本以美观的颜色打印出来，就像你在这个示例截图中看到的那样。所以你可以为文本设置颜色、背景和格式，诸如此类的所有样式。

Now, this might sound like a really simple and silly package, but here's the thing: it turns out this is actually the fifth most downloaded package in the entire JavaScript ecosystem. Last week in particular, it had 429 million downloads. So this package is used far and wide, to put it simply. If I could find any way to optimize anything inside this package, well, it would probably be worth the effort.

现在，这听起来可能是一个非常简单甚至有点傻的软件包，但事实是：它竟然是整个 JavaScript 生态系统中下载量排名第五的软件包。特别是上周，它的下载量达到了惊人的 4.29 亿次。简单来说，这个软件包的使用范围非常广。所以，如果我能找到任何方法来优化它里面的哪怕一丁点东西，那么，所有的努力都将是非常值得的。

So I'm going to ask Claude to run the benchmarks, identify the worst performing cases, use some profiling tools to figure out why those cases are running so slowly, and then fix them. We'll then see that Claude is going to use a wide variety of different tools to intelligently tackle this problem. It'll form up a to-do list to track its progress, execute commands to run the benchmarks, write a file to better zoom in on one particular case, use a CPU profiler to understand why that case is running so slowly, and then implement some improvements. By the end, we'll get a 3.9 times improvement in throughput in one particular operation around this library.

<step1_initial_translation>
所以我要让 Claude 运行基准测试，找出性能最差的案例，使用一些分析工具来找出这些案例运行缓慢的原因，然后修复它们。然后我们将看到 Claude 将使用各种不同的工具来智能地解决这个问题。它将制定一个待办事项列表来跟踪其进度，执行命令来运行基准测试，编写一个文件以更好地聚焦于一个特定的案例，使用 CPU 分析器来了解该案例运行缓慢的原因，然后实施一些改进。最后，我们将使这个库中某个特定操作的吞吐量提高 3.9 倍。
</step1_initial_translation>

<step2_reflection>
直译的具体问题列表：
1.「So I'm going to ask Claude to run the benchmarks"：句首的「所以」在口语中常见，但在科普文章中显得略不正式和多余。
2.「identify the worst performing cases"：直译无问题。
3.「use some profiling tools to figure out why those cases are running so slowly，and then fix them"：直译无问题。
4.「We'll then see that Claude is going to use a wide variety of different tools to intelligently tackle this problem"：
  -「然后我们将看到」略显口语化，且「is going to」翻译成「将」即可，不需强调「会」。
  -「智能地解决这个问题」的「智能地」略显生硬，可以更自然地表达为「巧妙地解决」。
5.「It'll form up a to-do list to track its progress"：「form up a to-do list」翻译成「制定一个待办事项列表」略显冗长，可以更简洁地表达。
6.「execute commands to run the benchmarks"：直译无问题。
7.「write a file to better zoom in on one particular case"：「更好地聚焦于一个特定的案例」不够流畅，可以更自然地表达。
8.「use a CPU profiler to understand why that case is running so slowly"：直译无问题。
9.「and then implement some improvements"：直译无问题。
10.「By the end，we'll get a 3.9 times improvement in throughput in one particular operation around this library"：
  -「最后，我们将使这个库中某个特定操作的吞吐量提高 3.9 倍」的「使... 提高」可以更简洁。
  -「around this library」翻译为「围绕这个库」或「在这个库的某个特定操作中」更准确。
</step2_reflection>

<step3_refined_translation>
我将让 Claude 运行基准测试，找出性能表现最差的案例，然后利用一些分析工具来探究这些案例运行缓慢的原因，并最终进行修复。接下来，我们将看到 Claude 如何巧妙地运用各种工具来解决这一问题。它会制定一份待办事项列表来追踪进度，执行命令来运行基准测试，编写一个文件以便更精准地聚焦于某个特定案例，使用 CPU 分析器来理解该案例运行缓慢的症结所在，然后实施一系列改进措施。最终，我们将实现该库中某个特定操作的吞吐量提升 3.9 倍。

Here's another example of how well Cloud can string together different tool calls to complete a rather complex task. I'm going to give it a dataset inside a CSV file. All the data inside of here contains information about different users of a video streaming platform, and I'm going to ask it to just do a general analysis, maybe identify some causes of churn on the platform. And I want all this analysis to be done inside of a Jupyter notebook. Here's my dataset. I'm going to ask Claude to run the analysis, and let's see how it does.

这是另一个例子，展示了 Claude 如何出色地将不同的工具调用串联起来，完成一项相当复杂的任务。我将向它提供一个 CSV 文件中的数据集。这里面的所有数据都包含了一个视频流媒体平台不同用户的信息，我将要求它进行一次通用分析，也许识别出平台上用户流失的一些原因。我希望所有这些分析都在 Jupyter notebook 中完成。这是我的数据集。我将要求 Claude 运行分析，让我们看看它的表现如何。

This is a great example of where effective tool use is really important. You see, it's not really enough that Claude just writes code into a notebook. Claude can also execute code in different cells and view the results of those executions. That means that Claude can take some initial look at the data in the notebook and then customize each subsequent cell to hone in on some particular details.

这是一个很好的例子，说明了有效利用工具的重要性。你看，Claude 仅仅是把代码写进笔记本里还不够。它还能执行不同单元格中的代码，并查看这些执行的结果。这意味着 Claude 可以对笔记本中的数据进行初步查看，然后根据需要自定义后续的每一个单元格，以便更深入地探究某些特定细节。

Next up, I'd like to show you an example of a task where I extend Cloud Code's capabilities by gaining access to a new set of tools. I built a small app that will generate UI components based upon some description entered on the left side of the screen. The generated component is then displayed on the right side. Now, the app can generate good-looking components quite easily, but the chat interface on the left and the header at the top are not looking so nice. So I'm going to use Cloud Code to improve the styling.

接下来，我想向您展示一个任务示例，我将通过获取一组新工具来增强 Cloud Code 的功能。我构建了一个小型应用程序，它能根据屏幕左侧输入的描述生成 UI 组件。生成后，组件会显示在右侧。目前，这个应用程序可以轻松生成美观的组件，但左侧的聊天界面和顶部的标题样式不尽如人意。所以，我将使用 Cloud Code 来改进它们的样式。

If I just asked it to fix the styling in the chat interface and the header, it would likely do a fine job. But remember, my goal here is to show you how easy it is to add additional functionality to Cloud Code. So along with this styling task, I'm going to also give Cloud Code access to a new set of tools provided by something called the Playwright MCP server, which I'll tell you more about later on. These tools allow Cloud to directly open and control a browser.

如果我仅仅让 Cloud Code 调整聊天界面和标题的样式，它很可能完成得不错。但请记住，我在这里的目的是向大家展示为 Cloud Code 增加额外功能是多么的简单。因此，除了这个样式任务之外，我还会让 Cloud Code 访问一套由 Playwright MCP 服务器提供的新工具，稍后我会详细介绍这个服务器。这些工具能够让 Cloud Code 直接打开并控制浏览器。

So here's what that process looks like in action. I'm going to ask Cloud to improve the styling of my app and make use of a browser to do so. It'll then open a browser on the right-hand side of the screen, navigate to my app, it'll take a screenshot to view the current styling, and then update the styling. We could even ask Claude to take another screenshot of the page when it was complete and iterate on the design a couple of times to really get a nice design that really pops.

那么，这个过程实际操作起来是怎样的呢？我会请 Claude 来改进我应用的样式，并利用浏览器来完成这项任务。它接着会在屏幕右侧打开一个浏览器，导航到我的应用，然后截取一张截图来查看当前样式，并更新样式。我们甚至可以要求 Claude 在完成后再截取一次页面截图，并对设计进行几次迭代，以真正打造出一个令人眼前一亮的设计。

And before long, we've got something that actually looks pretty reasonable. There's one last set of demonstrations that I'd like to give you. We're going to have a look at that really pops. And before long, we've got something that actually looks pretty reasonable.

很快，我们就能看到一些看起来相当不错的东西了。我还要给大家展示最后一组演示。我们将看到它究竟有多么引人注目。很快，我们就能看到一些看起来相当不错的东西了。
</step3_refined_one_translation>

There's one last set of demonstrations that I'd like to give you. Remember what I mentioned a moment ago. Cloud's ability to utilize tools so well is what will allow CloudCode to grow with you and your team in the future. Let me show you an example of that right away.

最后还有一组演示我想给各位展示。请记住我刚才提到的观点：Cloud 杰出的工具运用能力，正是 CloudCode 未来能与您和您的团队共同成长的关键。下面我就立刻为大家展示一个例子。

CloudCode has a very close integration with GitHub. You can set up CloudCode to run inside of a GitHub action, where it will be executed automatically based upon certain events, like creating a pull request or when directly mentioned inside an issue. When Cloud Code runs on GitHub, it not only gets to view and run your code, but it also gets to access a new set of tools for interacting with GitHub, like the ability to create comments or create commits or pull requests and so on. You can use this integration to automatically review pull requests.

CloudCode 与 GitHub 实现了非常紧密的集成。你可以将 CloudCode 配置为在 GitHub Actions 内部运行，这样它就会根据特定事件自动执行，例如创建拉取请求，或者在某个问题中被直接提及。当 CloudCode 在 GitHub 上运行时，它不仅能够查看并运行你的代码，还能访问一系列新的工具，用以与 GitHub 进行交互，比如创建评论、提交代码或发起拉取请求等。通过这种集成，你还可以实现自动审查拉取请求的功能。

Let me show you an example. Let me first set up a little scenario for you. Let's imagine that we are building out some infrastructure on AWS and all of our infrastructure is defined inside of a set of Terraform files, which are committed and stored on GitHub. Because all of our infrastructure is defined inside of Terraform files, Cloud Code has a really good idea of how information is flowing through our infrastructure.

现在我来给您展示一个例子。我们先来设想一个场景：假设我们正在 AWS 上构建一些基础设施，并且所有基础设施都定义在一组 Terraform 文件中，这些文件被提交并存储在 GitHub 上。由于所有的基础设施都定义在 Terraform 文件中，Cloud Code 对信息如何在我们的基础设施中流动有一个非常清晰的认识。

Now let's imagine that in this app, I have a DynamoDB table. If you're not familiar with those, it's kind of like a normal database table. And inside there, I'm storing some different information about users, including maybe plans viewed and a registration date. For maybe some reason, we want to share just that plans viewed and registration date information with some internal marketing team, but also some external marketing team as well. So some other company has access to the data that we are writing in this bucket. So it's really important for us to always be aware of what information is being written into that bucket over time.

现在让我们想象一下，在这个应用中，我有一个 DynamoDB 表。如果你对它不熟悉，可以把它看作是一个普通的数据库表格。在这个表里，我存储了一些关于用户的不同信息，比如他们查看过的套餐（plans viewed）和注册日期（registration date）。出于某种原因，我们可能需要将「查看过的套餐」和「注册日期」这些信息分享给内部营销团队，甚至包括一些外部营销团队。这意味着，有些其他公司也能访问我们写入这个（DynamoDB）表的数据。因此，对我们来说，时刻清楚随着时间的推移，到底有哪些信息被写入到这个表里，这一点就变得非常重要。

Nightly, we might have a Lambda function, Thank you, that we are writing in this bucket. So it's really important for us to always be aware of what information is being written into that bucket over time. Nightly, we might have a Lambda function, pull out all different users that have been added into that table, and then extract just plans viewed and the registration date, and store that in the S3 bucket so these two marketing teams can access that information.

每天晚上，我们可能会有一个 Lambda 函数将数据写入这个存储桶。因此，对我们来说，持续了解随着时间推移，有哪些信息被写入该存储桶至关重要。每晚，一个 Lambda 函数会提取所有已添加到该表中的不同用户数据，然后只抽取用户查看过的计划和注册日期，并将其存储在 S3 存储桶中，以便两个营销团队能够访问这些信息。

Now let's imagine that months later on, the internal marketing team asks us to also store the email inside of this S3 bucket as well. So we might go into the Lambda function and add in just one single line of code that takes the user's email and stores it inside the bucket. And because this is months later on, we might have completely forgotten that this S3 bucket is shared with a external marketing partner. So now at this point in time, we are putting personally identifiable information into this bucket, which is accessible by a separate company. This is a big no-no, definitely something we would not want to do. But at the same time, this is an error that does occur, and it's kind of hard to catch if we don't have a good idea of exactly what's going on with this S3 bucket.

现在让我们设想几个月后，内部营销团队也要求我们将电子邮件存储在这个 S3 存储桶中。于是，我们可能会修改 Lambda 函数，仅需添加一行代码，就能将用户的电子邮件存入该存储桶。由于时间已过去数月，我们可能早已忘记这个 S3 存储桶是与外部营销合作伙伴共享的。这样一来，我们就在无意中将个人身份信息（personally identifiable information）放入了一个可以被另一家外部公司访问的存储桶中。这绝对是一个严重的错误，是我们极力避免的情况。然而，这类错误确实会发生，而且如果我们不清楚这个 S3 存储桶的具体用途，就很难及时发现。

Well, it turns out that Cloud Code can catch this kind of scenario inside of a pull request quite easily, specifically because all of our infrastructure is defined inside of those Terraform files. So here's a quick example. I built that project that I just showed you in that diagram. I created a pull request to add in the user's email inside of the Lambda function. So the only line of code that I changed was that right there. I'm saying that for every user, I want to get the email and add that into the bucket as well.

事实证明，Cloud Code 可以很轻易地在拉取请求中捕获到这种场景，特别是因为我们所有的基础设施都定义在 Terraform 文件中。这里有一个简单的例子。我构建了刚才在图中向你展示的那个项目。我创建了一个拉取请求，目的是在 Lambda 函数中添加用户的电子邮件。我修改的唯一一行代码就是图示的那部分。我希望对于每个用户，都能获取其电子邮件并将其添加到存储桶中。

Now, Cloud Code has an excellent idea of my infrastructure. So it was able, inside an automated review, as we're seeing right here, to take a look at all the changes I made inside this pull request. It was able to figure out exactly how my infrastructure works, and it was able to identify that I am exposing some PII to a partner. So it has listed out the data flow right here, the exact steps that occur, and goes into great detail on how this bucket is shared with an external partner. Catching issues like this during development instead of after we deploy this change is an amazing benefit to using Cloud Codes integration on GitHub.

现在，Cloud Code 对我的基础设施有了清晰的认识。因此，正如我们在这里看到的，它能够在一次自动化审查中，检查我在这个拉取请求中进行的所有更改。它能够准确理解我的基础设施是如何运作的，并且识别到我正在将一些 PII（个人身份信息）暴露给一个合作伙伴。于是，它在这里列出了数据流，详细说明了具体的操作步骤，并深入解释了这个存储桶是如何与外部合作伙伴共享的。在开发阶段而非部署更改后捕获这类问题，是使用 Cloud Code 在 GitHub 上集成的巨大优势。

I'm going to go into a lot of detail later on and show you exactly how to set up a flow exactly like this. I think that we've now got a good idea of what Cloud Code can do thanks to its excellent ability to make use of tools. Remember, you really want to think of Cloud Code as a flexible assistant that can be customized, grow, and change over time to meet the needs of your team. Thank you. Thank you.

稍后，我将详细介绍并向大家展示如何精确地设置一个类似这样的流程。我认为，得益于其出色的工具利用能力，我们现在对 Cloud Code 能做什么已经有了很好的了解。请记住，您可以将 Cloud Code 视为一个灵活的助手，它能够随着时间进行定制、成长和改变，以满足您团队不断变化的需求。感谢大家。