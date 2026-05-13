# Critical Review — 04-critique.md

## Overall Assessment
初稿整体质量较高，风格流畅自然，术语标注到位，忠实保留了原文的热情和个人化语气。以下是需要改进的具体问题。

## 1. 准确性问题

### 1.1 英文 Example Prompts 中的标点被改为中文
初稿中所有 Example Prompts 的英文原文里，逗号被替换为中文逗号（`，`），冒号被替换为中文冒号（`：`）。例如：
- 第 97 行：`vary layout，tone，and density` 应为 `vary layout, tone, and density`
- 第 153 行：`a diagram of the token-bucket flow，the 3–4 key code snippets annotated` 应保留英文标点
- 这在 "Use this for" 列表中也出现了（第 183-193 行）

**诊断**：format_zh.py 的全角标点替换可能波及到了英文段落。需要恢复所有英文 Example Prompts 和英文列表中的半角标点。

### 1.2 小节标题未翻译
原文的小节标题如 "Why HTML?", "Information Density", "Visual Clarity & Ease of Reading" 等全部保留了英文。但这是中文翻译稿，小节标题应翻译为中文。

**诊断**：subagent 可能误解了"keep product names in English"的指令，把小节标题也当作了不需翻译的内容。

### 1.3 "revie wit" 原文笔误
原文第 23 行有一处拼写错误 "revie wit"（应为 "review it"）。初稿正确翻译了含义（"审阅这些内容"），但作为精翻应确认未遗漏这个细节——初稿处理得当，无需修改。

## 2. 欧化语言 / 中文表达不自然

### 2.1 "这使得 HTML 成为模型向你传达深度信息的极佳手段"（第 41 行）
"这使得...成为...的极佳手段" 是英文 "This makes it..." 的直译结构。
**建议**：改为 "所以 HTML 是模型向你深入传达信息的绝佳方式"

### 2.2 "它让我感觉自己更深入地参与了创作过程、对成果更有投入感"（第 77 行）
"对成果更有投入感" 偏生硬。
**建议**：改为 "让我在创作过程中更有参与感和投入感"

### 2.3 "让浏览体验更加理想"（第 51 行）
"理想" 作为形容浏览体验的词偏正式。
**建议**：改为 "让浏览起来更顺畅"

## 3. 翻译策略执行问题

### 3.1 "Use this for:" / "Use Cases:" 列表未翻译
第 101-105 行、115-121 行、133-141 行、155-165 行、181-193 行中的英文列表项均未翻译，如 "Creating a PR"、"Reviewing a PR"、"Summarize how a feature works" 等。这些是作者的总结性用例标签，不是 prompt 模板，应翻译为中文。

### 3.2 FAQ 问题标题保留英文合理但需加中文
FAQ 部分的问题如 "Isn't it less token efficient?" 保留英文有参考价值，但建议在英文问题后加中文翻译，方便读者理解。

## 4. 格式问题

### 4.1 缺少标题层级标记
原文虽然没有 `#` 标记，但 "Why HTML?"、"Information Density" 等明显是小节标题。初稿直接作为普通文本行处理。考虑到原文也是如此（纯文本无 Markdown 标题标记），保持一致是合理的，无需修改。

### 4.2 Specs 小节标题拼写
第 89 行 `Specs，Planning & Exploration` 中逗号被改为中文逗号，应保持英文逗号或翻译为中文。

## 5. 术语一致性

### 5.1 "制品" vs "产出物"
文中主要使用 "制品"（第 3、81 行），一致性良好，无问题。

### 5.2 "技术规格文档" 使用合理
"spec" 统一翻译为 "技术规格文档"，首次出现有括注，符合要求。

## Priority Fix List

| Priority | Issue | Location | Fix |
|----------|-------|----------|-----|
| P0 | 英文 prompt 中标点被替换为中文 | 多处 | 恢复所有英文段落中的半角标点 |
| P0 | 小节标题未翻译 | 全文 | 翻译所有小节标题 |
| P1 | "Use this for" 列表未翻译 | 多处 | 翻译为中文 |
| P1 | FAQ 问题加中文翻译 | FAQ 部分 | 英文后加中文 |
| P2 | 欧化表达 | 第 41、51、77 行 | 改用自然中文 |
