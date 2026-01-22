---
description: 将学习内容手动保存到 Obsidian 笔记
argument-hint: <笔记标题> [笔记类型]
allowed-tools: [Bash]
model: sonnet
---

# /save-learning

将 `help-me-learn` 或其他学习过程中的内容手动保存到 Obsidian vault。

## 使用方法

```
/save-learning <笔记标题> [笔记类型]
```

**示例：**
- `/save-learning "递归函数"` - 保存为学习笔记
- `/save-learning "React Hooks" concept` - 保存为概念笔记
- `/save-learning "第一性原理思维" mental-model` - 保存为思维模型笔记

## 使用场景

在 `help-me-learn` 会话中，当你觉得某个知识点特别有价值时：

```
你: /help-me-learn 递归
Claude: [详细解释递归概念...]

你: /save-learning "递归的核心概念"
Claude: 已将学习内容保存到 Obsidian！
```

## 笔记类型

- **learning** (默认)：学习笔记 - 完整的学习过程记录
- **concept**：概念笔记 - 核心概念和定义
- **mental-model**：思维模型 - 思考方式和框架
- **practice**：练习笔记 - 练习题和答案
- **summary**：总结笔记 - 知识点总结

## 笔记模板

### Learning Note (默认)
```markdown
---
type: learning
date: {{date}}
topic: "{{title}}"
tags: [learning]
---

# {{title}}

## 核心概念
[从学习中提炼的核心概念]

## 我已经知道了什么
[学习前的评估]

## 关键理解
[学到的关键点]

## 常见误区
[需要注意的陷阱]

## 练习
[测试理解的问题]

## 相关笔记
- [[]]
- [[]]
```

### Concept Note
```markdown
---
type: concept
date: {{date}}
tags: [concept]
---

# {{title}}

## 定义
[简洁的定义]

## 关键特征
- 特征 1
- 特征 2

## 举例
[具体例子]

## 反例
[非例子]

## 相关概念
- [[]]
```

### Mental Model Note
```markdown
---
type: mental-model
date: {{date}}
tags: [mental-model]
---

# {{title}}

## 这是什么思维模型
[模型描述]

## 何时使用
[适用场景]

## 如何应用
[实践步骤]

## 局限性
[不适用的情况]

## 相关模型
- [[]]
```

## 工作流程

1. **用户触发** - 在学习会话中手动调用 `/save-learning`
2. **提取内容** - 从当前对话上下文中提取学习内容
3. **结构化** - 根据笔记类型组织内容
4. **保存到 vault** - 通过 MCP Obsidian 创建笔记
5. **返回链接** - 提供笔记路径和链接

## 要求

使用此 command 前，需要先配置 MCP Obsidian：

```bash
claude mcp add-json obsidian --scope user '{"type":"stdio","command":"npx","args":["@mauricio.wolff/mcp-obsidian@latest","/path/to/your/vault"]}'
```

## 输出示例

```
✅ 已保存学习笔记！

📁 位置: 03-Resources/Learnings/递归的核心概念.md
🏷️ 标签: #learning #recursion

📝 内容摘要:
- 核心概念：函数调用自身
- 关键要素：基准情况、递归情况
- 常见误区：忘记基准情况

🔗 已创建到相关笔记的链接
```

## PARA 组织说明

学习笔记统一保存在 `03-Resources/Learnings/` 目录：

- **Learning Note** → `03-Resources/Learnings/`
- **Concept Note** → `03-Resources/Concepts/`
- **Mental Model** → `03-Resources/Mental-Models/`
- **Practice Note** → `03-Resources/Practices/`
- **Summary Note** → `03-Resources/Summaries/`

## 设计理念

> "有意识的记录，而不是自动的噪音。"

手动触发确保：
- ✅ 只记录真正有价值的内容
- ✅ 避免笔记库充满低质量内容
- ✅ 促进主动思考（决定是否值得记录）
- ✅ 保持学习流程的连贯性

## 与 help-me-learn 配合

**推荐工作流：**

1. 使用 `help-me-learn` 深入学习一个主题
2. 在学习过程中思考：这个值得记录吗？
3. 如果值得，使用 `/save-learning` 保存
4. 继续学习，重复步骤 2-3

这样你的 Obsidian vault 将积累高质量的思维结晶！
