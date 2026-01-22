---
description: 在 Obsidian 中创建、搜索和管理笔记
argument-hint: <操作> [参数...]
allowed-tools: [mcp__obsidian__read_note, mcp__obsidian__write_note, mcp__obsidian__search_notes, mcp__obsidian__list_directory, mcp__obsidian__update_frontmatter, mcp__obsidian__manage_tags, mcp__obsidian__patch_note, mcp__obsidian__move_note, mcp__obsidian__delete_note]
model: sonnet
---

# /obsidian

直接在 Obsidian vault 中创建、搜索和管理笔记，遵循 PARA 方法组织。

## 使用方法

```
/obsidian <操作> [参数...]
```

**示例：**
- `/obsidian new "我的笔记"` - 创建新笔记
- `/obsidian search "关键词"` - 搜索笔记
- `/obsidian list` - 列出目录内容
- `/obsidian read "笔记路径"` - 读取笔记
- `/obsidian edit "笔记路径"` - 编辑笔记

## PARA 目录说明

```
00-Inbox/      收件箱 - 快速捕获，临时存放（需要后续整理）
01-Projects/   项目 - 有明确目标、截止日期的短期任务
02-Areas/      领域 - 需要长期关注的责任范围（健康、财务、职业等）
03-Resources/  资源 - 感兴趣的主题、学习材料、参考资料
04-Archives/   归档 - 不再活跃的内容
```

**关键原则：**
- **Project** 有终点 → **Area** 持续进行
- **Area** 需要维护 → **Resource** 可随时查阅
- **Archive** 完成或不再需要 → **Inbox** 待整理

## 操作类型

### 1. new - 创建新笔记

```
/obsidian new <标题> [内容] [位置]
```

**根据类型自动选择位置：**

| 笔记类型 | 推荐位置 | 示例 |
|---------|---------|------|
| 快速想法、待整理 | `00-Inbox/` | 灵感闪现、临时笔记 |
| 有目标的项目 | `01-Projects/` | 网站改版、学习计划 |
| 长期责任 | `02-Areas/` | 健康管理、财务规划 |
| 学习资料 | `03-Resources/` | React 学习、算法笔记 |
| 已完成内容 | `04-Archives/` | 旧项目文档 |

**示例：**
- `/obsidian new "网站改版计划" "目标：3个月内完成..." 01-Projects/` - 项目笔记
- `/obsidian new "React Hooks 学习笔记"` - 学习笔记，自动放到 03-Resources/
- `/obsidian new "2024健康计划" "每周运动3次..." 02-Areas/` - 领域笔记
- `/obsidian new "临时想法"` - 快速记录到 Inbox

### 2. search - 搜索笔记

```
/obsidian search <关键词> [选项]
```

**示例：**
- `/obsidian search "递归"` - 搜索所有笔记
- `/obsidian search "type:concept"` - 搜索 frontmatter
- `/obsidian search "#learning" 03-Resources/` - 在资源目录搜索

### 3. read - 读取笔记

```
/obsidian read <笔记路径>
```

**示例：**
- `/obsidian read "03-Resources/Learnings/React Hooks.md"`
- `/obsidian read "01-Projects/网站改版/任务清单.md"`

### 4. edit - 编辑笔记

```
/obsidian edit <笔记路径>
```

进入编辑模式后，可以：
- 追加内容
- 修改特定段落
- 更新 frontmatter
- 添加标签

**示例：**
```
你: /obsidian edit "03-Resources/React.md"
Claude: 已读取笔记，请告诉我如何修改
你: 在"核心概念"部分添加新的要点
Claude: ✅ 已更新笔记
```

### 5. list - 列出目录

```
/obsidian list [路径]
```

**示例：**
- `/obsidian list` - 列出根目录
- `/obsidian list "03-Resources/"` - 列出资源目录
- `/obsidian list "01-Projects/"` - 列出所有项目

### 6. tags - 管理标签

```
/obsidian tags <笔记路径> <操作> [标签...]
```

**操作：**
- `add` - 添加标签
- `remove` - 移除标签
- `list` - 列出标签

**示例：**
- `/obsidian tags "笔记.md" add #learning #react`
- `/obsidian tags "笔记.md" remove #todo`

### 7. move - 移动/重命名笔记

```
/obsidian move <旧路径> <新路径>
```

**用途：** 将笔记从 Inbox 整理到正确的 PARA 目录

**示例：**
- `/obsidian move "00-Inbox/React学习.md" "03-Resources/React学习.md"` - 整理学习资料
- `/obsidian move "00-Inbox/网站想法.md" "01-Projects/网站改版.md"` - 想法变成项目

### 8. delete - 删除笔记

```
/obsidian delete <笔记路径>
```

**需要确认**：删除前会要求二次确认

## 快捷操作

### 快速捕获
```
/obsidian note "想法内容"
```
在 **00-Inbox** 快速创建一条想法笔记（后续需要整理）

### 每日笔记
```
/obsidian daily
```
创建或打开今日笔记（建议定期归档到对应目录）

### 项目笔记
```
/obsidian project <项目名>
```
在 **01-Projects** 创建项目笔记

### 学习笔记
```
/obsidian learn <主题>
```
在 **03-Resources/Learnings** 创建学习笔记

### 领域笔记
```
/obsidian area <领域名>
```
在 **02-Areas** 创建领域笔记

### 归档
```
/obsidian archive <笔记路径>
```
将笔记移动到 **04-Archives**

## PAR A 组织指南

### 如何决定笔记放在哪里？

**问自己这些问题：**

1. **这个笔记有明确的完成目标吗？**
   - 是 → `01-Projects/`
   - 否 → 继续问

2. **这是一个需要持续维护的责任范围吗？**
   - 是 → `02-Areas/`
   - 否 → 继续问

3. **这是学习材料或参考资料吗？**
   - 是 → `03-Resources/`
   - 否 → 继续问

4. **这是已完成或不再活跃的内容吗？**
   - 是 → `04-Archives/`
   - 否 → `00-Inbox/`（待整理）

### 典型例子

```
01-Projects/
  ├── 网站改版.md           (有目标：3个月完成)
  ├── 学习Vue3.md           (有目标：2周掌握)
  └── 准备面试.md           (有目标：下月面试)

02-Areas/
  ├── 健康管理.md           (长期维护)
  ├── 财务规划.md           (长期维护)
  └── 职业发展.md           (长期维护)

03-Resources/
  ├── Learnings/
  │   ├── React Hooks.md    (学习笔记)
  │   └── 算法基础.md       (学习笔记)
  └── References/
      ├── API文档.md        (参考资料)
      └── 设计规范.md       (参考资料)

04-Archives/
  ├── 2023年终总结.md       (已完成)
  └── 旧项目文档.md         (不再活跃)
```

## 前置要求

使用此命令前，需要先配置 MCP Obsidian：

```bash
claude mcp add-json obsidian --scope user '{"type":"stdio","command":"npx","@mauricio.wolff/mcp-obsidian@latest","/absolute/path/to/obsidian-vault"]}'
```

**重要**：将路径替换为你的 vault 绝对路径！例如：`/home/user/ai_train_human/obsidian-vault`

## 输出示例

### 创建项目笔记
```
✅ 已创建项目笔记！

📁 位置: 01-Projects/网站改版.md
🏷️ 标签: #project #active

📝 内容预览:
# 网站改版

## 目标
3个月内完成网站全面改版

## 进度
- [ ] 需求分析
- [ ] 设计稿
- [ ] 开发
- [ ] 测试
- [ ] 上线
```

### 创建学习笔记
```
✅ 已创建学习笔记！

📁 位置: 03-Resources/Learnings/递归函数.md
🏷️ 标签: #learning #algorithm

📝 内容预览:
# 递归函数

## 核心概念
函数调用自身...

## 关键理解
- 基准情况
- 递归情况
```

### 搜索结果
```
🔍 找到 3 个相关笔记：

1. 03-Resources/Learnings/递归函数.md
   - 核心概念：函数调用自身...

2. 01-Projects/算法项目.md
   - 使用递归实现树遍历...

3. 00-Inbox/递归练习.md
   - 待整理 → 可移至 Resources
```

## 工作流程

1. **用户指定操作** - `new`、`search`、`read` 等
2. **智能位置选择** - 根据内容类型建议正确的 PARA 目录
3. **执行 MCP 调用** - 通过 MCP Obsidian 操作 vault
4. **格式化结果** - 清晰展示操作结果
5. **组织建议** - 提示是否需要整理位置

## 配合其他命令使用

- **`/help-me-learn`** → 学习后用 `/obsidian learn <主题>` 保存
- **`/save-learning`** → 自动保存到 03-Resources/Learnings/
- **`/setup-obsidian`** → 初始化 PARA 目录结构

## 设计理念

> "知识管理的核心在于：快速捕获，智能组织，随时回顾。"

**PARA 方法原则：**
1. **快速捕获** - Inbox 暂存所有想法
2. **定期整理** - 将 Inbox 内容分类到正确位置
3. **按需查阅** - 根据活动类型快速定位

`/obsidian` 命令让你的 Obsidian vault 成为：
- 📥 **快速捕获中心** - Inbox 随时记录
- 🗂️ **智能组织系统** - 自动建议 PARA 位置
- 🔍 **快速搜索引擎** - 按目录或内容搜索
- ✏️ **灵活编辑器** - 轻松管理内容
- 🔗 **知识连接器** - 建立笔记间的链接
