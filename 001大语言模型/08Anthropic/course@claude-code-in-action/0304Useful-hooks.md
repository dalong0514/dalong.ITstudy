## 0304Useful-hooks

[Useful hooks!](https://anthropic.skilljar.com/claude-code-in-action/312004)

In this video, I'd like to show you some really useful hooks that you might want to use on your own projects. These hooks are intended to address some common weak points in Claude Code.

在这个视频中，我将向大家展示一些非常实用的 Hook，或许你会在自己的项目中使用它们。这些 Hook 旨在解决 Claude Code 中一些常见的不足之处。

### 01

To help you understand how the first one works, let me give you a quick demonstration of a problem that Claude Code sometimes runs into, especially on larger projects. So inside the SRC directory, I'm going to find schema ts. Inside of here, there's just one single function called create schema. This function is called from the main ts file, specifically right here.

为了帮助你理解第一个功能是如何运作的，我来快速演示一个 Claude Code 有时会遇到的问题，尤其是在大型项目中。在 `SRC` 目录下，我找到了 `schema.ts` 文件。在这个文件中，只有一个名为 `create schema` 的函数。这个函数是从 `main.ts` 文件中调用的，具体调用位置就在这里。

Now, I'm going to go back to the schema ts file and I'm going to update the function definition. I'm going to say that if you ever want to call this function, you must also pass in a verbose argument. That must be of type boolean. Now, as soon as I add in this change, if I go backwards to the main ts file, I'm going to get a type error because I just updated the definition of this function, but I have not actually added in a value for verbose. So the error right here says specifically "argument for verbose was not provided."

现在，我将回到 `schema.ts` 文件并更新函数定义。我会声明，如果想调用这个函数，就必须同时传入一个 `verbose` 参数，并且它必须是布尔类型。一旦我做出这个修改，如果我再回到 `main.ts` 文件，就会收到一个类型错误，因为我刚刚更新了函数的定义，但还没有为 `verbose` 参数提供具体的值。因此，这里的错误会明确提示：「没有提供 verbose 的参数。」

Now I'm going to undo that change very quickly. I'm going to close the main ts file. I'm going to open up Claude Code and ask it to make the exact same change. Now, if I run this, Claude Code is going to have absolutely no issue making this edit whatsoever. But it's going to update this file, and unfortunately, after making that change, so there's the new verbose true right there, unfortunately, Claude won't go around the project and try to find where that function is actually called and try to update any of the different call sites. So if I now open up main ts, we'll see that we do in fact have an error over here, and Claude didn't really catch this, unfortunately.

现在，我将迅速撤销之前的修改。我会关闭主 ts 文件，然后打开 Claude Code，让它执行相同的修改。如果我运行这段代码，Claude Code 在执行此编辑时将没有任何问题。它会更新这个文件，但不幸的是，在完成修改后（你看，新的 `verbose true` 就在这里），Claude 不会遍历整个项目，去寻找这个函数实际被调用的位置，也不会尝试更新任何相关的调用点（call sites）。因此，如果我现在打开 `main ts` 文件，就会发现这里确实出现了一个错误，而 Claude 遗憾地未能捕捉到这一点。

So the first hook that I want to show you will fix this solution super easily. In case you're not familiar with TypeScript, if you're not, that's totally fine. If I close out the Claude Code and run the command `tsc --noemit`, that's going to run a type check on my entire project. And in this type check, we can see that the error is very evident right here. So it's complaining about our call to create schema from that main ts file.

那么，我想向大家展示的第一个钩子（hook）将轻而易举地解决这个问题。如果你不熟悉 TypeScript，也没关系。如果我关闭 Claude Code 并运行 `tsc --noemit` 命令，它就会对我的整个项目进行类型检查。在这次类型检查中，我们可以非常明显地看到错误就出现在这里。它正在指出我们从那个 main ts 文件调用 create schema 的问题。

So my idea for a hook is really simple. I think that anytime that we edit a TypeScript file, we should run the TypeScript Type Checker and see if there are any distinct errors. If there are, we should attempt to feed these errors back into Claude immediately inside a post-tool-use hook. And hopefully, this will give Claude a signal and tell it that there is a type error that it just introduced that it probably needs to go and fix somewhere else inside of our project.

我关于钩子（hook）的想法非常简单。我认为，每当我们编辑 TypeScript 文件时，都应该运行 TypeScript 类型检查器（Type Checker），检查是否存在任何明显的错误。如果发现错误，我们应该尝试在工具使用后钩子（post-tool-use hook）中立即将这些错误反馈给 Claude。这样有望向 Claude 发出信号，告诉它刚刚引入了一个类型错误，它可能需要在项目的其他位置进行修复。

Now, I already put this hook together for us, fortunately, just to save us a little bit of time, inside the hooks tsc.js file. So inside this file, I've got a bunch of logic put together to run the TypeScript type checker, take any errors that it found, and pass them back into Claude. At present, I disabled this hook just so I can give you that demonstration you just saw. So I disabled it by adding the `process.exit(0)` right there. I'm going to delete that. And now this hook should be working a-okay.

现在，我已经在 `hooks/tsc.js` 文件中为我们准备好了这段钩子（hook），幸运的是，这帮我们节省了一些时间。在这个文件中，我编写了一段逻辑，用于运行 TypeScript 类型检查器，捕获它发现的任何错误，并将它们反馈给 Claude。目前，我禁用了这个钩子，只是为了向你展示你刚刚看到的那个演示。我是通过在那里添加 `process.exit（0)` 来禁用的。现在我将删除这行代码。这样一来，这个钩子应该就能万事俱备，正常工作了。

So if I now go back to the schema ts file, remove that verbose flag, restart Claude Code, and ask it to make the same change once again, it will make the change and hopefully this time it will immediately get that feedback from the TypeScript Type Checker saying, hey, you've got an error somewhere else in the project that you just introduced and hopefully Claude will go and fix it.

所以，如果我现在回到 schema ts 文件，移除那个详细输出标记，重启 Claude Code，并让它再次执行相同的更改，它会进行更改，希望这次它能立即从 TypeScript 类型检查器（Type Checker）那里收到提示，告知项目其他地方刚刚引入了一个错误，而 Claude 则会修复它。

So we can see right here, there's the edit that was made. We got some edit operation feedback from the hook that we put together. So it found an issue inside of one of our different files. And Claude is now saying, "Okay, I understand. I introduced an error. I need to fix the call to create schema inside of main ts." And the next update it makes is going to attempt to go into that file and update that function call to add in that missing argument. So this is a hook that you might want to try implementing on your own personal projects.

所以我们在这里可以看到，这是所做的编辑。我们从自己实现的 hook（钩子）中获得了一些编辑操作的反馈。它在我们的一个文件中发现了一个问题。现在 Claude 正在说：「好的，我明白了。我引入了一个错误。我需要在 `main ts` 文件中修复 `create schema` 的调用。」它进行的下一次更新将尝试进入该文件，并更新该函数调用，以添加那个缺失的参数。因此，这是一个你可能会想在自己的项目中尝试实现的 hook。

Now, even though this hook was implemented specifically for TypeScript, it still works for any other kind of typed language where you can run a type checker very easily. Even if you're using an untyped language, you might even implement the same idea of functionality using tests instead of running a type checker. So every time an edit is made, you could run your tests to make sure that the edit is okay.

现在，尽管这个钩子是专门为 TypeScript 实现的，但它同样适用于其他任何可以轻松运行类型检查器的强类型语言。即使你使用的是弱类型语言，你也可以借鉴这个思路，用运行测试来代替类型检查器。这样，每次进行修改时，你都可以运行测试，以确保改动是正确的。

### 02

Now, the next hook that I would like to show you is a little bit more challenging to explain, but once you get the idea behind it, I think that you will definitely find this next one really helpful, particularly in larger projects. To help you understand this other hook, I want to give you a little bit of background on this project. Inside the SRC Queries directory, there are many different files. Each of these different files contains many different SQL queries written inside of different functions.

接下来我要向大家展示的这个 hook（钩子）可能解释起来会有点挑战性，但一旦你掌握了它的核心思想，我相信你肯定会觉得它非常实用，尤其是在那些大型项目中。为了帮助大家更好地理解这个 hook，我想先简单介绍一下这个项目的背景。在 SRC Queries 目录下，存放着许多不同的文件。每个文件里都包含着用不同函数编写的 SQL 查询语句。

Inside the `order queries.ts` file, there's a function called `get pending orders`. This query accesses a database containing e-commerce data and is designed to find all orders that have been created and are currently in a pending state. Please keep this function in mind.

在 `order queries.ts` 文件中，有一个名为 `get pending orders` 的函数。这个查询会访问一个包含电子商务数据的数据库，其作用是找出所有已经创建但目前处于待处理状态的订单。这一点请大家留意。

I'll now show you a couple of diagrams to illustrate a common problem that arises in larger projects. The diagram on the left shows a list of query files. As we've seen, each file contains multiple queries. In the `order queries.ts` file, specifically, we have the `get pending orders` function. So, we already have a query that finds pending orders.

现在我将通过几张图表，向你展示大型项目中一个常见的问题。左侧的图表显示了一系列查询文件。我们知道，每个文件都包含多个查询。具体来说，在 `order queries.ts` 文件中，我们有一个名为 `get pending orders` 的函数。也就是说，我们已经有了一个用于查找待处理订单的查询。

Now, if I ask Claude to update the `main.ts` file to print out all pending orders older than three days, ideally, Claude would locate the `order queries.ts` file, find the existing query, and utilize it instead of writing a new one. This is the desired outcome. We'll see that if we ask Claude to do exactly that right now, we'll get the result we want.

现在，如果我让 Claude 更新 `main.ts` 文件，打印出所有三天前提交的待处理订单，理想状况下，Claude 应该会找到 `order queries.ts` 文件中的现有查询并直接使用，而不是重新编写一个。这正是我们期待的结果。我们会发现，如果现在就让 Claude 执行此操作，它将如我们所愿。

I'll ask Claude to find pending orders in the `main.ts` file. To Claude's credit, it will examine the existing query files, find `order queries.ts`, and recognize the `get pending orders` function. It will then attempt to use this function rather than creating a new query. This is exactly what we wanted, as we didn't want a new query; we wanted Claude to use the existing function. When given a focused and directed task, Claude can understand that it should look at existing queries rather than generating new ones. This is a positive outcome.

我将要求 Claude 在 `main.ts` 文件中查找待处理订单。Claude 表现出色，它会检查现有的查询文件，找到 `order queries.ts`，并识别出 `get pending orders` 函数。然后，它会尝试使用这个函数，而不是创建一个新的查询。这正是我们所希望的，因为我们不想要一个新的查询，而是希望 Claude 能够直接利用现有函数。当任务明确且有针对性时，Claude 能够理解它应该优先查看现有查询，而不是生成新的。这是一个非常积极的成果。

Next, I'll present Claude with a more challenging task. I'll intentionally make it more difficult. First, I'll use `/clear` to remove all previous context. Then, I'll direct you to the `task indy.ts` file. In this file, I've created a prompt that still asks Claude to find long-pending orders but has also incorporated it into a larger project. I'm asking Claude to write a Slack integration that will message a specific channel daily with all orders that have been pending for too long.

接下来，我将给 Claude 布置一个更具挑战性的任务，我会刻意增加一些难度。首先，我会使用 `/clear` 命令清除所有之前的上下文信息。然后，我会让你查看 `task indy.ts` 文件。在这个文件中，我设计了一个提示，它不仅要求 Claude 找出那些长时间未处理的订单，还将这个功能整合到了一个更大的项目之中。我要求 Claude 编写一个 Slack 集成，这个集成将每天向指定的频道发送消息，列出所有待处理时间过长的订单。

In this scenario, we still need to find orders that have been pending for a while, but now it's wrapped within this larger task. If I feed this task into Claude after the `/clear` operation, we'll observe that this time, unfortunately, it won't remain as focused. It will end up attempting to write a completely new `get pending orders` query, which is not what we want because it leads to duplicate code throughout the project. If I let this run, I'll eventually see it create a new query called `get orders pending too long`. This is an instance where Claude lost focus and decided to write a new query instead of reusing an existing one. Again, we have duplicate code, which is likely undesirable. Furthermore, it not only created the new query but also a new file, which is also probably not what we want. We would likely prefer this order-related query to be added to the `order queries.ts` file.

在这种情况下，我们仍然需要找出那些长时间处于待处理状态的订单，不过这次它被包含在一个更大的任务中。如果在 `/clear` 操作之后，我将这个任务输入给 Claude，我们会发现，这一次它很遗憾地没有保持专注。它最终会尝试编写一个全新的 `get pending orders` 查询语句，这并不是我们想要的，因为这会导致整个项目中出现重复的代码。如果我让它继续运行，最终会看到它创建了一个名为 `get orders pending too long` 的新查询。这就是 Claude 失去专注力的一个例子，它决定编写一个新查询，而不是重用现有查询。同样，我们又得到了重复的代码，这很可能是不理想的。此外，它不仅创建了新的查询，还创建了一个新文件，这可能也不是我们想要的。我们可能更希望将这个与订单相关的查询添加到 `order queries.ts` 文件中。

Now that we understand the issue, let's explore how we might fix this by using a hook. Whenever Claude attempts to write, edit, or use the multi-edit tool to modify something specifically within the `queries` directory, I'm going to run the following hook. First, within this hook, I'll launch a new, separate instance of Claude Code. I'll ask this new instance to examine the recent change and review existing code in the `queries` directory to see if a similar query already exists. Then, if an existing query is found, I'll send that feedback back to the original Claude instance, asking it to potentially correct the situation. This would involve removing the added query and using the existing one.

既然我们已经了解了问题所在，那么接下来探讨一下如何通过引入一个「钩子」（hook）来解决它。每当 Claude 试图在 `queries` 目录中进行写入、编辑或使用多编辑工具修改任何内容时，我都会触发这个钩子。首先，在这个钩子内部，我会启动一个新的、独立的 Claude Code 实例。我会让这个新实例去检查 Claude 最近的更改，并回顾 `queries` 目录中已有的代码，看看是否已经存在类似的查询。然后，如果发现有现有查询，我会将这条反馈发送回原始的 Claude 实例，要求它纠正这种情况，具体做法是删除新添加的查询，转而使用已有的那个。

This approach will help ensure that the `queries` folder remains clean and free of duplicate code. Let me demonstrate how this works in practice. First, I'll switch back over here. I'll delete the newly created `order alerts queries.ts` file and the Slack text file to show the process in action.

这种方法将有助于确保 `queries` 文件夹保持整洁，没有重复的代码。接下来，我将向大家演示这在实践中是如何运作的。首先，我将回到这里。我会删除刚刚创建的 `order alerts queries.ts` 文件和 Slack 文本文件，以此来展示整个过程。

First, I'm going to flip back over here. I'm going to delete the brand new order alerts queries TS file that was made, and the slack TS file that was made as well.

首先，我将返回此处。我将删除之前创建的全新订单提醒查询 TS 文件和 Slack TS 文件。

Then, I'm going to find inside the hooks directory the query hook file. So, I already put this hook together for us. Right now, it is currently disabled because I got a process exit at the very top. So, let's walk through this hook really quickly.

然后，我会在 `hooks` 目录中找到查询 `hook`（钩子）文件。我已经为我们准备好了这个钩子。不过，目前它被禁用了，因为我在文件最顶部设置了一个进程退出。接下来，让我们快速过一遍这个钩子。

First, I'm going to tell this thing that it's only going to review changes to the SRC queries directory. Then, a little bit lower, I'm going to check and see if the change that was just made was made to the queries directory. After that, I then got a long prompt here that is asking Claude to do a review on the change that was just made.

首先，我将指示它仅审查对 `SRC queries` 目录的修改。接着，在后续操作中，我将验证刚刚所做的更改是否确实发生在 `queries` 目录中。完成这些步骤后，我将向 Claude 发送一个详细的提示，请求它对刚才的更改进行代码审查。

And then after that is where I'm launching Claude Code programmatically. Specifically, these lines right here. This is making use of the Claude Code TypeScript SDK. I can give you a lot more information on it in just a little bit. For right now, just understand that this right here is essentially the same as us making use of Claude Code at the terminal.

紧接着，我将以编程方式启动 Claude Code。具体来说，就是通过这些代码行实现的。这其中利用了 Claude Code 的 TypeScript SDK（Software Development Kit）。稍后我会提供更多关于它的详细信息。目前，您只需理解，这部分操作与我们在终端中使用 Claude Code 的效果是基本相同的。

Once Claude Code runs and I get a response back out of it, I check and see if Claude decides that, yeah, the changes look okay, or maybe we've got a duplicate query. And if we do, then we're going to exit early with an exit code of two, which is going to give this feedback back to Claude and hopefully tell it that it needs to make a change.

Claude 代码运行并返回响应后，我会检查 Claude 是否认为这些更改是可接受的，或者是否存在重复的查询。如果存在重复查询，我们会立即以退出码 2 终止进程。这个退出码会将反馈信息传回 Claude，以指示其需要进行相应的调整。

So now that I've got this additional hook put together and enabled by removing that process exit zero at the top, I'm going to again restart Claude Code and then run the same query again. And hopefully this time it might initially put in that duplicate query, but then our hook right here is going to run and hopefully tell it, hey, we don't want that duplicate code. You should make use of some already existing query to implement this functionality.

现在我已经将这个额外的 Hook 组装好，并通过移除开头的 `process exit zero` 代码段使其生效。接下来，我将重启 Claude Code 并再次运行相同的查询。希望这一次，即使它最初可能生成了重复的查询，我们的 Hook 也能及时运行，并提示它：我们不需要重复的代码，而是应该利用已有的查询来实现所需的功能。

And Claude Code is once again going to attempt to create a brand new, completely separate query file, not making use of the old query that already existed. When it tries to create that file, however, our hook is going to run. It's going to launch that separate copy of Claude Code, which is going to do some research and find that there is in fact an existing query that can be reused. It's going to provide some advice and say, hey, you could probably go and update this other existing query to suit your purposes perfectly. And we'll see some feedback from Claude, our primary instance that we are interacting with, saying, ah, yes, there is this existing query, let's just modify that existing query rather than attempting to write out a brand new one.

Claude Code 将再次尝试创建一个全新的、完全独立的查询文件，而不是使用已有的旧查询。然而，当它尝试创建该文件时，我们的钩子（hook）将会运行。它会启动 Claude Code 的一个独立副本，这个副本会进行一番「研究」，发现确实存在一个可以重复使用的查询。于是，它会提供一些建议，比如：「嘿，你或许可以去更新这个现有的查询，它能完美地满足你的需求。」随后，我们会看到来自 Claude（我们主要交互的实例）的一些反馈，它会说：「啊，是的，既然已经有这个查询了，那我们干脆直接修改它，而不是费力去写一个新的。」

Now, the downside to this hook is that it's going to take some additional time and expense to run every single time that I want to edit something inside the queries directory. But the upside is that I'm going to end up with a lot less duplicate code inside my queries directory. So it really comes down to a set of trade-offs for you deciding whether or not you want to implement something like this in your own project.

现在，这个「钩子」（hook）的缺点在于，每次我想编辑查询目录中的内容时，它都会增加额外的运行时间和费用。但好处是，我的查询目录中的重复代码会大大减少。因此，这实际上是一系列利弊权衡，你需要决定是否要在自己的项目中实现类似这种机制。

If you do, I would at least recommend doing what I showed you inside of the query hook, so this one right here, and only watching maybe a handful of directories, like really important folders inside of your project, just to minimize the amount of extra work that is being done. Thank you. Thank you.

如果需要这样做，我至少建议你采用我在查询钩子中演示的方法（就是这一种），并且只监控少数几个目录，例如项目中真正重要的文件夹，这样能最大限度地减少额外的工作量。谢谢。

## 页面文档

Claude Code hooks can help address common weaknesses in AI-assisted development, particularly on larger projects. These hooks run automatically when Claude makes changes to your code, providing immediate feedback and preventing common issues.

Claude 的代码钩子（Code hooks）可以帮助弥补 AI 辅助开发（AI-assisted development）中的常见不足，尤其是在大型项目中。当 Claude 修改你的代码时，这些钩子会自动运行，提供即时反馈，并有效避免一些常见问题。

### TypeScript Type Checking Hook

One of the most useful hooks addresses a fundamental problem: when Claude modifies a function signature, it often doesn't update all the places where that function is called throughout your project.

TypeScript 类型检查钩子其中一个最有用的钩子解决了根本性问题：当 Claude 修改一个函数签名（function signature）时，它往往不会自动更新项目中所有调用该函数的地方。

For example, if you ask Claude to add a verbose parameter to a function in schema.ts, it will successfully update the function definition but miss the call site in main.ts. This creates type errors that Claude doesn't immediately catch.

例如，如果你要求 Claude 给 `schema.ts` 文件中的一个函数添加一个 `verbose` 参数，它能成功地更新函数的定义，但却会漏掉 `main.ts` 文件中对该函数的调用处。这种遗漏会导致 Claude 无法立即捕获的类型错误。

The solution is a post-tool-use hook that runs the TypeScript compiler after every file edit:

这个解决方案是一个「工具使用后钩子（post-tool-use hook）」，它会在每次文件编辑后自动运行 TypeScript 编译器：

Runs tsc --noEmit to check for type errors
Captures any errors found
Feeds the errors back to Claude immediately
Prompts Claude to fix the issues in other files

它会运行 `tsc --noEmit` 命令来检查代码中是否存在类型错误。
一旦发现任何错误，它会立即捕捉这些错误。
随后，这些错误会被实时反馈给 Claude。
然后，它会指示 Claude 去修复其他文件中的相关问题。

This hook works for any typed language where you can run a type checker. For untyped languages, you could implement similar functionality using automated tests instead.

这种「钩子」机制适用于任何支持运行类型检查器（type checker）的有类型语言（typed language）。而对于那些无类型语言（untyped language），我们可以利用自动化测试（automated tests）来实现类似的功能。

### Query Duplication Prevention Hook

查询重复预防 Hook（Query Duplication Prevention Hook）

In larger projects with many database queries, Claude sometimes creates duplicate functionality instead of reusing existing code. This is especially problematic when you give Claude complex, multi-step tasks that include database operations as just one component.

在包含大量数据库查询的大型项目中，Claude 有时会重复地实现功能，而不是复用现有代码。当您向 Claude 分配复杂的、多步骤的任务，而数据库操作只是其中一个环节时，这个问题就尤为突出。

Consider a project structure with multiple query files, each containing many SQL functions. When you ask Claude to "create a Slack integration that alerts about orders pending longer than 3 days," it might write a new query instead of using the existing getPendingOrders() function.

想象一下，如果一个项目结构包含多个查询文件，每个文件里都有许多 SQL 函数。当你要求 Claude「创建一个 Slack 集成，用于提醒超过 3 天未处理的订单」时，它可能不会去利用现有的 getPendingOrders() 函数，而是直接编写一个新的查询。

The query duplication hook addresses this by implementing a review process:

为了解决这个问题，查询去重钩子（query duplication hook）引入了一个审查流程：

Here's how it works:

具体工作原理如下：

Triggers when Claude modifies files in the ./queries directory
Launches a separate instance of Claude Code programmatically
Asks the second instance to review the changes and check for similar existing queries
If duplicates are found, provides feedback to the original Claude instance
Prompts Claude to remove the duplicate and use the existing functionality

当 Claude 修改 `./queries` 目录中的文件时，这一机制就会被触发。
它会以编程的方式启动 Claude Code 的另一个独立实例。
然后，这个「第二个实例」会受指令审查这些更改，并检查是否已经存在类似的查询。
如果发现了重复的查询，它就会向最初的 Claude 实例提供反馈。
接着，系统会提示 Claude 删除重复项，并直接使用现有的功能。

### Implementation Considerations

Both hooks use the pre-tool-use or post-tool-use hook system. The TypeScript hook is relatively lightweight and runs quickly. The query duplication hook requires more resources since it launches a separate Claude instance for each review.

实现方式的考量这两个「钩子」功能都利用了 `pre-tool-use`（工具使用前）或 `post-tool-use`（工具使用后）的钩子系统。其中，TypeScript 钩子本身比较轻量级，运行速度也很快。然而，负责查询重复检查的钩子则需要更多的资源，因为它每次进行审查时，都需要启动一个独立的 Claude 实例。

For the query hook, consider these trade-offs:

在考虑查询钩子时，我们需要权衡以下几点：

Benefits: Cleaner codebase with less duplication
Costs: Additional time and API usage for each query directory edit
Recommendation: Only monitor critical directories to minimize overhead

优点：能够使代码库（codebase）更加整洁，减少重复代码。
缺点：每次编辑查询目录时，会增加额外的时间和 API（应用程序编程接口）使用成本。
建议：为最大程度地降低开销（overhead），仅监控关键目录。

The hooks use Claude's TypeScript SDK to programmatically interact with the AI. This allows you to create sophisticated workflows where one Claude instance can review and provide feedback on another's work.

这些钩子通过使用 Claude 的 TypeScript SDK，实现了与 AI 的程序化交互。这使得开发者能够构建复杂的自动化流程，例如一个 Claude 实例可以对另一个 Claude 实例完成的工作进行审查并提供反馈。

### Extending These Concepts

These hooks demonstrate broader principles you can apply to your own projects:

推广这些概念这些「钩子」展示了你可以应用到自己项目中的通用原则：

1 Use compiler/linter output to provide immediate feedback

利用编译器 /linter（linter）的输出提供即时反馈。

2 Implement code review processes using separate AI instances

使用独立的 AI 实例（AI instances）实现代码审查流程。

3 Focus monitoring on high-value directories where consistency matters most

优先监控高价值目录，因为这些地方的一致性至关重要。

4 Balance automation benefits against performance costs

权衡自动化带来的好处与可能产生的性能成本。

The key is identifying the specific pain points in your development workflow and creating targeted hooks that address those issues automatically.

关键在于识别出开发工作流程（development workflow）中的具体痛点，并创建有针对性的「钩子」（即自动化工具）来自动解决这些问题。