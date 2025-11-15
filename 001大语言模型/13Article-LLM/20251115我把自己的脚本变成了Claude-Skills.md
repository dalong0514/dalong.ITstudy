## 20251115我把自己的脚本变成了Claude-Skills

[我把自己的脚本变成了 Claude Skills，效率直接翻倍](https://mp.weixin.qq.com/s/12yq8a2ajIeiThVeMcmI-Q)

最近用 Claude Code，我发现自己在做一件很奇怪的事情。

每次部署网站，都要重复说一遍相同的话：

「帮我创建一个 GitHub 私有仓库，我已经安装了 GitHub CLI…」「记得执行 npm run build 检查有没有错误…」「部署到 Vercel 之前，先检查环境变量…」

说着说着我突然意识到 —— 我 tm 在重复当 Claude 的「产品经理」。

每次都要手把手教它怎么部署、怎么配置多语言、怎么检查 SEO。而且最烦的是，Claude 有时候会「发挥创意」，跳过某个关键步骤，导致部署失败。

直到 10 月 16 日，Claude 发布了 Agent Skills。

我花了两天时间，把常用的脚本改造成了 Skills。效果直接翻倍 —— 不用再重复说明，不用担心出错，Claude 自己就知道该怎么做。

### Agent Skills 是什么？

直接说，就是给 Claude 配置「专业技能包」。

你把工作流程、脚本、最佳实践打包成一个文件夹，Claude 需要的时候就会自动调用。不用你每次重复说明。

它的核心设计叫「渐进式披露」，分三层加载：

Level 1：元数据 —— 只加载名字和描述（约 100 token），Claude 靠这个判断什么时候该用。

Level 2：主指令 —— 任务匹配时才读取完整的 SKILL.md（<5000 token）。

Level 3：详细资源 —— 按需加载脚本、文档、示例（理论上无限制）。

这样设计的好处：你可以在 Skill 里塞很多东西，但不会占用 Claude 的上下文窗口。需要什么才加载什么。

最大的好处：从「每次重复写 prompt」变成「配置一次，长期使用」。

### 我的实践：把 2 个脚本变成 Skills

#### 1. 部署工作流 Skill

以前：每次部署都要说一遍 5 步流程，Claude 有时候会跳过某个步骤，导致部署失败。

现在：创建了 deploying-to-production Skill，核心配置是这样的：

```
---
name：Deploying to Production
description：Automates GitHub repository creation and Vercel deployment.
---
## Deployment Workflow
- [ ] Step 1：Run build and verify no errors
- [ ] Step 2：Create GitHub repository
- [ ] Step 3：Push code to GitHub
- [ ] Step 4：Deploy to Vercel
- [ ] Step 5：Verify deployment
**Step 1：Run build**
Run：`npm run build`
**If build fails**：Review errors，fix issues，run again.
**Only proceed when build succeeds.**
```

现在我只需要说「帮我部署这个网站」，Claude 就会自动执行完整流程，每一步都有检查清单，出错了会自动诊断并提供修复建议。

效果：稳定性大幅提升，不再担心遗漏步骤，以前经常因为忘记某个步骤导致部署失败，现在基本不会了。

#### 2. 国际化工作流 Skill

以前：手动创建每个语言的文件、配置路由、添加 hreflang、更新 sitemap… 花 1-2 小时，容易遗漏细节。

现在：创建了 internationalizing-websites Skill，包含完整的脚本和参考文档。

我给自己的个人网站（benx.ai）添加了英文和日文支持，10 分钟搞定。而且细节处理得更好 —— Open Graph 标签的国际化、hreflang 的正确配置，这些以前经常忘记的东西，现在 Skill 都会自动检查。

---

### 试用官方 Skills：webapp-testing 实测

配置完自己的 Skills，我又下载了 Anthropic 官方提供的 12 个 Skills，试试看质量如何。

我挑了 webapp-testing Skill 来实测，用它测试我的个人网站 benx.ai。

这个 Skill 基于 Playwright，可以自动化测试网站。我只说了一句：「用 webapp-testing skill 测试 benx.ai」，Claude 就自动创建测试脚本、启动浏览器、进行全面检测。

测试结果：

```
🌐 webapp-testing Skill - 测试结果 
=====================================
✅ 页面加载成功
🔘 发现 22 个按钮 | 🔗 全站共有 6 个链接

📱 响应式设计测试:  
✅ iPhone SE（375x667）- 截图已保存  
✅ iPad（768x1024）- 截图已保存  
✅ Desktop HD（1920x1080）- 截图已保存

⚡ 性能检查:  
🐛 控制台错误：0 个  
⚠️ 控制台警告：0 个
```

不用写一行代码，就完成了元素发现、多设备截图、错误监控、SEO 检查。整个过程不到 1 分钟。

---

### 创建 Skill 的 3 个关键经验

1、描述要精准。

description 字段很重要，Claude 靠它来判断什么时候触发 Skill。

关键是要包含：触发关键词 + 具体场景。

例如：Automates GitHub repository creation and Vercel deployment. Use when deploying new websites，or when user mentions deployment，GitHub，or Vercel.

2、指令要简洁。

Claude 已经很聪明了，不要写太多废话。假设它已经懂基础知识，只写它不知道的。

3、加入反馈循环。

复杂流程要加「验证 - 修复 - 重试」机制，这样 Claude 就不会跳过关键步骤，出错了也知道怎么处理。

### 如何快速上手？

方式 1：下载官方 Skills

Anthropic 提供了 12 个开箱即用的 Skills（文档处理、Web 测试、Canvas 设计等）。

直接下载使用：https://github.com/anthropics/skills

方式 2：让 Claude 帮你生成

官方提供了 skill-creator Skill，专门用来创建新 Skill。你只需要告诉 Claude 你要做什么，它会引导你一步步创建，并生成完整的文件结构。

方式 3：使用我的开源 Skills

为了帮助更多人快速上手，我把自己创建的两个 Skills 开源了：

🔗 GitHub 仓库：

[littleben/awesomeAgentskills: A curated collection of skills for Claude Code and other AI agents | 精选的 Claude Code 和其他 AI 智能体技能集合](https://github.com/littleben/awesomeAgentskills)

目前包含：

deploying-to-production - 自动化部署工作流

internationalizing-websites - 网站国际化工作流

这两个 Skill 都是我实际在用的生产级配置，直接下载就能用。

也欢迎你提交自己的 Skills！如果你也创建了好用的 Skill，欢迎提交 PR。让我们一起打造一个高质量的 Skills 社区资源库。

### 从「助手」到「专业工程师」

用了两天 Agent Skills，我最大的感受是：Claude 从「AI 编程助手」变成了「AI 专业工程师」。

以前，Claude 更像是一个聪明的实习生：你得手把手教它怎么做，它才能完成任务。

现在有了 Skills，它更像是一个有经验的工程师。你只需要说目标，它自己知道该怎么做，该注意什么，出错了怎么处理。

而且配置一次，长期受益。我的两个 Skills 这两天每次用都很稳定，不用再重复说明，节省了大量时间。

如果你也在用 Claude Code 做项目，强烈建议试试 Agent Skills。把你的脚本、工作流、最佳实践变成 Skills，效率真的能翻倍。