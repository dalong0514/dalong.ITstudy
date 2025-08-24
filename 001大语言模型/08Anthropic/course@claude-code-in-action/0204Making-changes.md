## 0204Making-changes

[Making changes](https://anthropic.skilljar.com/claude-code-in-action/303236)

Let's try making a couple of changes to this project. Along the way, I'll show you some useful features around Claude Code. The first thing I'd like to do is move this placeholder text over here on the left-hand side down to the center of this panel.

接下来，我们来对这个项目进行一些更改。在这个过程中，我将向大家展示 Claude Code 的一些实用功能。我想做的第一件事是，把左侧的占位符文本移动到面板的中心位置。

To help Claude understand exactly what content I want moved, I'm going to take a screenshot of that area right there and I'm going to paste it into Claude Code using Ctrl+V. Note that's Ctrl+V and not Command+V that you might be used to on macOS. Ctrl+V is used specifically to paste in a screenshot. I can then ask Claude to center that placeholder. After a little bit of searching, Claude is able to make the styling update, and then back inside the browser, yeah, looks great.

为了帮助 Claude 准确理解我想要移动的内容，我将对屏幕上指定区域进行截图，然后使用 Ctrl+V 将其粘贴到 Claude Code 中。请注意，这里使用的是 Ctrl+V，而不是您在 macOS 系统上可能习惯的 Command+V。Ctrl+V 在此专门用于粘贴截图。接着，我就可以要求 Claude 将该占位符居中显示。经过一番处理，Claude 成功完成了样式更新，然后回到浏览器中查看，效果确实非常棒。

Let me show you the next thing I would like to change in this app. I'm going to ask for a card component that displays a title and some description. The card is generated without any issue, but there's one awkward thing. On the left-hand side, in the chat interface, there's a "String Replace Editor". That little panel right there is meant to indicate to the user that any file is being created, but right now it's using a very technical term, "String Replace Editor", for the tool that is being used behind the scenes. I would like to show a user a little more friendly text here and just tell the user that a file is being created and the name of the file. And of course, we should also handle pieces where maybe this chatbot is editing a file or deleting a file and other stuff like that.

接下来，我想向你展示这个应用中我希望改动的地方。我需要一个卡片组件，它能显示一个标题和一些描述。这张卡片本身生成得没什么问题，但有一个地方让人觉得不太妥当。在聊天界面的左侧，有一个名为「字符串替换编辑器」的面板。这个小面板的本意是告诉用户有文件正在被创建，但现在它却用了一个非常专业的术语 ——「字符串替换编辑器」—— 来指代它在幕后使用的工具。我希望这里能显示更友好的文字，直接告诉用户正在创建的是哪个文件以及文件的名称。当然，我们也应该考虑这种情况，比如当聊天机器人正在编辑或删除文件时，以及其他类似的操作。

To help guide Claude's attention, I'm going to once again take a screenshot of this so it understands exactly what I'm talking about. Then, back over here, I'm going to paste that image in and ask Claude to replace that particular text with some more user-friendly message. Now, this is a little bit of a tricky task that will require Claude to do a decent amount of research in this project to complete.

为了更好地引导 Claude 理解，我将再次截取屏幕截图，以便它能准确把握我的意图。然后，我将在这里粘贴这张图片，并要求 Claude 将其中特定文本替换为更易于用户理解的消息。这项任务具有一定难度，需要 Claude 对本项目进行大量深入研究才能完成。

Whenever you give Claude a harder task, there are two ways that you can easily boost Claude's intelligence. The first way is to enable "plan mode". Plan mode is enabled by pressing Shift+Tab twice, or just once if you are already auto-accepting file edits. In plan mode, Claude will do much more research over the contents of your project, reading more files and coming up with a detailed plan on how to complete your task. After completing the plan, Claude will tell you exactly what it wants to do to complete your task. At that point, you can either accept this plan and Claude will implement it, or you can redirect Claude in some way, maybe it missed some file or didn't consider some scenario.

当你想给 Claude 一个更具挑战性的任务时，有两种简单的方法可以显著提升它的工作效率。第一种方法是启用「计划模式」。要进入计划模式，你可以按两次 Shift+Tab 键；如果你已经设置了自动接受文件编辑，那么只需按一次即可。在计划模式下，Claude 会对你的项目内容进行更深入的分析，阅读更多的文件，并为如何完成任务制定一个详细的方案。在完成计划后，Claude 会清楚地告诉你它将如何执行任务。这时，你可以选择接受这个计划，Claude 便会按照计划执行；或者，你也可以对 Claude 进行引导，例如，如果它遗漏了某些文件或没有考虑到特定情况，你可以及时进行调整。

The second way in which we can boost Claude's intelligence is by enabling "thinking". This turns on Claude's extended thinking feature, allowing it to reason more about a particular task. To enable thinking, there are a handful of different trigger phrases. Each one gives Claude a progressively larger token budget to think with. Given that this is a trickier task, I might ask Claude to "ultra-think" about the best way to implement it. The last thing to understand is that planning and thinking can be used together. So, in addition to this "ultra-think", I'm going to also turn on plan mode as well. And now I'm going to run this and we'll see how well Claude can implement this feature.

提升 Claude 智能的第二种方法是启用「思考」功能。这会开启 Claude 的扩展思考功能，让它能对特定任务进行更深入的推理。要启用思考功能，需要使用一些不同的触发短语。每个触发短语都会为 Claude 提供逐步增加的思考所需的 Token（Token）预算。考虑到这是一项更棘手的任务，我可能会要求 Claude「ultra-think」（深度思考）如何最好地实现它。最后要理解的是，规划和思考可以结合使用。因此，除了「ultra-think」之外，我还将开启规划模式。现在我将运行它，看看 Claude 能多好地实现这个功能。

Now you might be wondering when you should use planning and when you should use thinking. Think of these two as handling breadth versus depth. Planning mode is useful when you have a task that requires a wide understanding of your code base and requires looking at different areas. It's also useful when working on a task that requires several steps to complete. Thinking, on the other hand, is useful when you are focusing on a particular tricky bit of logic or troubleshooting a difficult bug. The second question you might have is whether you should just enable thinking and planning all the time. Well, you certainly can, just keep in mind that planning and thinking consume additional tokens, so there is a cost with using them.

现在，你可能会想知道何时应该使用规划模式，何时又该使用思考模式。你可以将这两种模式理解为分别处理广度和深度的问题。当一个任务需要你对代码库有全面的了解，并需要审视不同区域时，规划模式就显得非常有用。同样，当一个任务需要通过多个步骤才能完成时，规划模式也能发挥作用。另一方面，当你需要专注于某个特别复杂的逻辑点，或者排查一个棘手的 bug 时，思考模式就显得格外有效。你可能还会有的第二个问题是：是不是应该一直启用思考和规划模式呢？当然可以，但请记住，规划和思考会消耗额外的 Token，因此使用它们会产生额外的计算成本。

After a couple of minutes of work, it looks like the feature is complete, so I need to go back to my editor and test this out. So, right away, we can see that we get some better status information here than what we had before. Users are now being told that a file is being created. And if I send in a follow-up request, maybe to change the title, hopefully now on the follow-up, we'll see something about editing that file. So there we go. So now we're editing the app.jsx file. Well, I would say Claude definitely succeeded in implementing this feature.

经过几分钟的工作后，看来这个功能已经完成了，所以我需要回到我的编辑器并进行一番测试。很快我们就能注意到，这里显示的状态信息比之前更好了。现在用户会收到正在创建文件的提示。如果我发送一个后续请求，比如更改标题，希望在后续请求中，会显示正在编辑该文件的信息。果然，我们看到了，现在正在编辑 app.jsx 文件。Claude 显然成功地实现了这项功能。

Now that we have made some changes to this project, we should probably commit our changes. Claude Code is a solid Git assistant. We can ask it to stage and commit our changes, and it will write a descriptive commit message for us. Thank you.

既然我们已经对这个项目做了一些改动，是时候提交这些更改了。Claude Code 是一个非常出色的 Git 助手，我们可以让它来暂存并提交我们的更改，它还会为我们编写一条描述性的提交信息。

## 页面文档

When working with Claude in your development environment, you'll often need to make changes to existing projects. This guide covers practical techniques for implementing changes effectively, including visual communication with screenshots and leveraging Claude's advanced reasoning capabilities.

当你在自己的开发环境中与 Claude 协作时，经常需要对现有项目进行修改。本指南将介绍一些实用技巧，教你如何高效地实现这些修改，包括如何通过屏幕截图进行直观交流，以及如何充分发挥 Claude 的高级推理能力。

### Using Screenshots for Precise Communication

利用截图进行精确沟通

One of the most effective ways to communicate with Claude is through screenshots. When you want to modify a specific part of your interface, taking a screenshot helps Claude understand exactly what you're referring to.

与 Claude 沟通最有效的方法之一就是使用截图。当你想要修改界面的某个特定部分时，拍摄一张截图能帮助 Claude 准确理解你所指的是什么。

To paste a screenshot into Claude, use Ctrl+V (not Cmd+V on macOS). This keyboard shortcut is specifically designed for pasting screenshots into the chat interface. Once you've pasted the image, you can ask Claude to make specific changes to that area of your application.

要将截图粘贴到 Claude 中，请使用 Ctrl+V（在 macOS 上不是 Cmd+V）。这个键盘快捷键是专门用于将截图粘贴到聊天界面的。一旦你粘贴了图片，就可以要求 Claude 对你应用程序中的特定区域进行具体的修改。

### Planning Mode

规划模式（Planning Mode）

For more complex tasks that require extensive research across your codebase, you can enable Planning Mode. This feature makes Claude do thorough exploration of your project before implementing changes.

对于需要对您的整个代码库进行深入研究的复杂任务，您可以开启规划模式。这项功能让 Claude 在实施任何修改之前，能够全面细致地探查您的项目。

Enable Planning Mode by pressing Shift + Tab twice (or once if you're already auto-accepting edits). In this mode, Claude will:

要启用规划模式，请按两次 Shift + Tab（如果你已自动接受编辑，则按一次即可）。在此模式下，Claude 将会：

1 Read more files in your project

读取你项目中的更多文件

2 Create a detailed implementation plan

制定详细的实施计划

3 Show you exactly what it intends to do

准确展示它打算执行的操作

4 Wait for your approval before proceeding

在获得你的批准后才会继续执行

This gives you the opportunity to review the plan and redirect Claude if it missed something important or didn't consider a particular scenario.

### Thinking Modes

思维模式

Claude offers different levels of reasoning through "thinking" modes. These allow Claude to spend more time reasoning about complex problems before providing solutions.

Claude 通过不同的「思维」模式，提供了不同程度的推理能力。借此，Claude 能够在提供解决方案之前，投入更多时间来深入思考和分析复杂问题。

The available thinking modes include:

Claude 可用的思考模式（thinking modes）包括：

"Think" - Basic reasoning
"Think more" - Extended reasoning
"Think a lot" - Comprehensive reasoning
"Think longer" - Extended time reasoning
"Ultrathink" - Maximum reasoning capability

"Think" - 基础推理能力
"Think more" - 进阶推理能力
"Think a lot" - 全面推理能力
"Think longer" - 长时间推理能力
"Ultrathink" - 极致推理能力

Each mode gives Claude progressively more tokens to work with, allowing for deeper analysis of challenging problems.

每种模式都会为 Claude 提供逐步增加的 Token（Token）数量，使其能够对复杂难题进行更深入的分析。

### When to Use Planning vs Thinking

何时使用规划与思考模式

These two features handle different types of complexity:

这两个功能分别应对不同类型的复杂性：

Planning Mode is best for:

规划模式最适合：

Tasks requiring broad understanding of your codebase
Multi-step implementations
Changes that affect multiple files or components

需要对您的代码库有广泛理解的任务
多步骤的实现
涉及多个文件或组件的更改

Thinking Mode is best for:

「思考模式（Thinking Mode）」最适合处理：

Complex logic problems
Debugging difficult issues
Algorithmic challenges

复杂的逻辑问题
调试疑难问题
算法挑战

You can combine both modes for tasks that require both breadth and depth. Just keep in mind that both features consume additional tokens, so there's a cost consideration for using them.

您可以结合使用这两种模式，来应对那些既需要广度又需要深度的任务。但请记住，这两种功能都会消耗更多的 Token，因此在使用时需要考虑成本。