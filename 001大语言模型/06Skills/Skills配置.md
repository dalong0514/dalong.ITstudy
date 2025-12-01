### 01

2025-11-30

直接整个文件夹映射过去

ln -s /Users/Daglas/skills /Users/Daglas/dalong.github/dalong.processdesign/.claude


ln -s /Users/Daglas/dalong.llm/skills/document-skills /Users/Daglas/dalong.github/dalong.processdesign/.claude/skills/document-skills


---

[(14) X 上的 宝玉：“教你如何在 Codex CLI 里面用 SKILLs 1. 在你的项目目录下创建一个 “.claude/skills”目录，如果你不想提交到 git 就把 .claude 加到 .gitignore 注：也可以是任意其他目录，放在“.claude/skills”目录下有个好处就是 claude code 默认能使用，不需要额外配置。 2. 把你要用到 skill https://t.co/zVRMHwwOFJ” / X](https://x.com/dotey/status/1989146187786494351)

教你如何在 Codex CLI 里面用 SKILLs

1、在你的项目目录下创建一个 ".claude/skills" 目录，如果你不想提交到 git 就把 .claude 加到 .gitignore。

注：也可以是任意其他目录，放在 ".claude/skills" 目录下有个好处就是 claude code 默认能使用，不需要额外配置。

2、把你要用到 skill 复制到 ".claude/skills" 目录下（可以去 http://github.com/anthropics/skills 这里找现成的）。

3、如果你需要用到哪个 skill，只需要手动 @ 一下相应的 skill 文件即可，比如：

> 请使用 @.claude/skills/artifacts-builder/SKILL.md ，创建一个 whiteboard 项目。

也就是说只要你让 agent 去读取相应的 SKILL md 文件，就可以让 Agent 学会使用 SKILL。

这个方法不仅仅适用于 codex cli，也同样适用于 TRAE、Cursor、GitHub Copilot 这类 coding agent。

只能说 SKILL 的设计是想当超前的，而且跟 MCP 一样，并非 Claude Code 专属。
