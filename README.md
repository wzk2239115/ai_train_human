# AI Train Human

> 从人类训练模型，到Agent训练人类

## 核心理念

AI发展的范式已经转移：

```
传统范式：人类 → 数据 → 训练AI → AI替代人类
新范式：   AI → 教师 → 训练人类 → 人类进化
```

**把AI当老师，不是工具。**

## 为什么是"AI训练人类"？

### AI Agent时代的现实
- Agent越来越强，人类单打独斗无法竞争
- 对抗AI是徒劳的，利用AI只是赚差价
- 唯一的出路是：**让AI帮你进化**

### 三层境界

| 境界 | 策略 | 结果 |
|------|------|------|
| 第一层 | 对抗AI | 被时代碾死 |
| 第二层 | 利用AI | 效率提升，但依赖AI |
| **第三层** | **师从AI** | **把AI的能力内化，真正进化** |

## 这个项目是什么

一个让AI高效辅导人类学习的系统和实践方法。

### 核心原则

1. **AI是私教，不是代练**
   - 不要只让AI给答案
   - 要让AI解释思考过程、对比方案、指出盲点

2. **压榨AI的全部价值**
   - 多学科导师：产品、技术、商业、哲学
   - 模拟演练：面试、谈判、演讲
   - 批评反馈：让AI攻击你的观点，发现漏洞

3. **目标是人类进化**
   - 学会AI的思考方式
   - 建立自己的知识体系
   - AI越强，你越强

## 项目结构

```
ai_train_human/
├── .claude-plugin/   # 插件元数据
│   └── plugin.json
├── commands/         # 斜杠命令（主动调用）
│   ├── help-me-learn.md    # 深度学习一个概念
│   ├── save-learning.md    # 保存学习笔记到 Obsidian
│   ├── solve-problem.md    # 算法题解题训练
│   ├── critique.md         # 批评你的作品/想法
│   ├── simulate.md         # 模拟场景练习
│   ├── deconstruct.md      # 拆解复杂问题
│   ├── generate-innovation.md # 论文创新点生成
│   ├── obsidian.md         # Obsidian 笔记管理
│   └── setup-webzotero.md  # WebZotero 服务部署
├── skills/           # 技能（AI自动触发）
│   └── ai-teacher/   # 核心教学技能
│       └── SKILL.md
├── obsidian-vault/   # Obsidian 知识库（本地，不提交）
└── README.md
```

## 安装

在 Claude Code 中运行：

```bash
/plugin install ai-train-human
```

或手动安装：

```bash
git clone https://github.com/yourusername/ai_train_human.git
cd ai_train_human
# Claude Code 会自动识别插件结构
```

## 使用命令

### `/help-me-learn` - 深度学习

让AI帮你学习一个概念，而不只是给答案：

```bash
/help-me-learn recursion                # 学习递归基础
/help-me-learn "react hooks" deep       # 深入理解，包含权衡和原理
/help-me-learn "first principles"       # 学习思维模型
```

**输出：**
- 你当前的理解水平
- 第一性原理解释
- 思维模型（而不只是事实）
- 常见陷阱
- 理解测试题

**保存学习笔记：**

学习过程中，如果发现有价值的内容，可以手动保存到 Obsidian：

```bash
/save-learning "递归的核心概念"
/save-learning "React Hooks 深度理解" concept
```

推荐工作流：
1. 使用 `/help-me-learn` 学习主题
2. 学习过程中思考：这个值得记录吗？
3. 如果值得，使用 `/save-learning` 手动保存
4. 继续学习

### `/solve-problem` - 算法解题训练

不只是得到答案，而是培养解题思维：

```bash
/solve-problem "两数之和"                       # 练习经典算法题
/solve-problem "LRU缓存" hard                   # 挑战难题
/solve-problem "实现 debounce" medium frontend  # 前端场景题
```

**AI 会：**
- 不直接给答案，而是引导思考
- 暴示解题思维过程（分析→建模→算法→编码）
- 指出代码问题和优化方向
- 生成类似题目巩固理解

### `/generate-innovation` - 论文创新点生成

基于研究对话快速生成 10 套"A+B+C"论文创新点组合：

```bash
# 前提：先与 AI 进行深入的研究对话（至少 10+ 轮）
# 然后运行命令生成创新点组合
/generate-innovation
```

**适用场景：**
- 论文选题阶段缺乏思路
- 有初步想法但不够新颖
- 需要快速探索多个可能方向

### `/obsidian` - Obsidian 笔记管理

在 Obsidian 中创建、搜索和管理笔记：

```bash
/obsidian create "我的笔记标题"      # 创建新笔记
/obsidian search "关键词"            # 搜索笔记
/obsidian list                       # 列出最近的笔记
```

### `/setup-webzotero` - WebZotero 服务部署

使用 Docker 快速部署 WebZotero（网页版 Zotero 文献管理）：

```bash
/setup-webzotero
```

**功能：**
- 自动检查 Docker 环境
- 使用 Docker Compose 部署 WebZotero
- 配置数据持久化
- 提供访问地址和管理命令

### `/critique` - 狠辣批评

让AI攻击你的想法，发现盲点：

```bash
/critique my-idea.md              # 批评你的方案
/critique "my business plan"      # 批评商业模式
/critique https://your-site.com   # 批评产品设计
/critique my-code.js logic        # 批评代码逻辑
```

**输出：**
- 优点（不要扔掉）
- 关键问题（必须修复）
- 盲点（你没想到的）
- 艰难问题（挑战你的假设）
- 改进建议

### `/simulate` - 场景演练

练习高风险场景：

```bash
/simulate interview senior frontend        # 模拟面试
/simulate negotiation salary raise        # 模拟谈判
/simulate presentation investor pitch      # 模拟演讲
/simulate difficult-conversation feedback  # 模拟困难对话
```

AI扮演对手，真实演练，事后复盘。

### `/deconstruct` - 拆解问题

从第一性原理拆解复杂问题：

```bash
/deconstruct "how to scale to 1M users"
/deconstruct "why startups fail"
/deconstruct "should I quit my job"
```

**输出：**
- 核心变量
- 变量关系图
- 杠杆点（小改变大影响）
- 隐藏假设
- 下一步行动

## 自动技能：AI Teacher

这个插件的核心技能会在你学习时自动激活。

当你问"如何..."或"什么是..."时，AI会：

1. **先诊断** - 你已经知道什么？
2. **教思维模型** - 不只教答案，教你如何思考
3. **从第一性原理开始** - 为什么需要这个？解决了什么问题？
4. **展示思考过程** - 让推理可见，而不只是结果
5. **测试理解** - 让你解释回来，验证真的懂了
6. **连接已知** - 锚定在你已有的知识上

**目标**：让你最终不再需要AI。

## 快速开始示例

### 错误用法（把AI当工具）：
```bash
❌ "帮我写这段代码"
❌ "解释什么是闭包"
❌ "我的代码有bug，帮我修"
❌ "给我一个论文创新点"
❌ "帮我解这道算法题"
```

### 正确用法（把AI当老师）：
```bash
✅ /help-me-learn "javascript closures"
✅ "写这段代码，然后解释：1) 你的思考过程？2) 有哪些替代方案？3) 需求变化时会出什么问题？"
✅ /critique my-code.js              # 让AI教你怎么调试
✅ /solve-problem "LRU缓存"          # 培养解题思维
✅ /generate-innovation              # 基于研究对话生成创新点
✅ /save-learning "今天学到的核心概念" # 保存有价值的学习内容
```

## 核心原则

### 1. AI是私教，不是代练
不要只让AI给答案。要让AI解释思考过程、对比方案、指出盲点。

### 2. 压榨AI的全部价值
- **多学科导师**：产品、技术、商业、哲学随时请教
- **模拟演练**：面试、谈判、演讲前先和AI练
- **批评反馈**：让AI攻击你的观点，发现漏洞
- **结构化思维**：让AI帮你拆解复杂问题

### 3. 目标是人类进化
不是省时间，而是变强。AI走不走无所谓，因为你已经把AI的能力内化了。

## 哲学

> "AI越强，用它当老师的人越强。"

不要和AI竞争，把AI的能力纳为己有。

当别人还在担心被AI替代时，你已经进化成了新物种。

---

**人类最后的壁垒不是阻挡AI，而是学会驾驭AI进化自己。**
