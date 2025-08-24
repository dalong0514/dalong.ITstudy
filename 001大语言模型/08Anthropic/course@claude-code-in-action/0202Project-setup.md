## 0202Project-setup

[Project setup](https://anthropic.skilljar.com/claude-code-in-action/301615)

Working with Claude Code is more interesting if you have a project to work with.

如果你有一个项目可以动手实践，那么使用 Claude Code 会更有趣。

I've put together a small project to explore with Claude Code. It is the same UI generation app shown in a previous video. Note: you don't have to run this project. You can always follow along with the remainder of the course with your own code base if you wish!

我准备了一个小项目，供你使用 Claude Code 进行探索。它就是之前视频中展示过的那个 UI 生成应用程序。请注意：你不需要运行这个项目。如果你愿意，完全可以使用你自己的代码库来继续完成本课程的剩余内容！

Setup

准备工作

This project requires a small amount of setup:

要启动这个项目，你只需要进行一些简单的设置：

1 Download the zip file called uigen.zip attached to this lecture and extract it

请下载本讲座随附的 uigen.zip 压缩文件（zip file）并将其解压。

2 In the project directory, run npm run setup to install dependencies and set up a local SQLite database

在项目目录中，运行 `npm run setup` 命令以安装所需的依赖项（dependencies）并配置一个本地的 SQLite 数据库。

3 Optional: this project uses Claude through the Anthropic API to generate UI components. If you want to fully test out the app, you will need to provide an API key to access the Anthropic API. This is optional. If no API key is provided, the app will still generate some static fake code. Here's how you can set the api key:

可选：这个项目利用 Claude 并通过 Anthropic API 来生成用户界面（UI）组件。如果你想充分体验这款应用的功能，你需要提供一个 API 密钥（API key）来访问 Anthropic API。请注意，这是一个可选步骤。即使没有提供 API 密钥，该应用仍然会生成一些静态的模拟代码。下面是设置 API 密钥的方法：

Get an Anthropic API key at https://console.anthropic.com/

请访问 https://console.anthropic.com/ 获取 Anthropic API 密钥。

Place your API key in the .env file.

然后，将您的 API 密钥配置到 .env 文件中。

Start the project by running npm run dev