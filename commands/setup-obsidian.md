---
description: 快速搭建 Obsidian 基础环境
argument-hint: [vault路径]
allowed-tools: [Bash, Write]
model: sonnet
---

# /setup-obsidian

快速搭建 Obsidian 知识库基础环境。

## 使用方法

```
/setup-obsidian [vault名称]
```

**示例：**
- `/setup-obsidian` - 在当前目录的 `obsidian-vault/` 文件夹中搭建
- `/setup-obsidian my-notes` - 在 `my-notes/` 文件夹中搭建

## 这个命令的作用

快速搭建 Obsidian 基础环境：

1. **创建 vault 文件夹** - 独立的 vault 目录（已添加到 .gitignore）
2. **创建目录结构** - PARA 方法组织
3. **配置 Obsidian** - 优化的基础设置
4. **创建模板** - 核心笔记模板
5. **配置 MCP** - Claude Code 集成指南

## 目录结构

```
obsidian-vault/          # 或指定的 vault 名称
├── .obsidian/
│   └── obsidian.json     # 基础配置
├── 00-Inbox/            # 收件箱
├── 01-Projects/         # 项目
├── 02-Areas/            # 领域
├── 03-Resources/        # 资源
├── 04-Archives/         # 归档
└── Templates/           # 模板
    ├── Daily Note.md
    └── Project Note.md
```

## Claude Code MCP 集成

为了让 Claude Code 能够直接操作你的 Obsidian vault，需要安装 **MCP Obsidian** 插件：

### 安装步骤

1. **安装 MCP Obsidian 插件**：
   ```bash
   claude mcp add-json obsidian --scope user '{"type":"stdio","command":"npx","args":["@mauricio.wolff/mcp-obsidian@latest","/path/to/obsidian-vault"]}'
   ```

   **重要**：将 `/path/to/obsidian-vault` 替换为你实际的 vault 绝对路径！
   例如：`/home/user/ai_train_human/obsidian-vault`

2. **验证安装**：
   ```bash
   claude mcp list
   ```

3. **重启 Claude Code** 以加载 MCP 插件

### MCP 功能

安装 MCP Obsidian 后，Claude Code 可以：
- 📝 直接在你的 vault 中创建和编辑笔记
- 🔍 搜索和读取现有笔记
- 🏷️ 管理标签和元数据
- 🔗 创建笔记间的链接
- 📊 分析你的知识图谱

### 配置文件位置

MCP 配置通常保存在：
- **Linux**: `~/.config/claude/claude_desktop_config.json`
- **macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows**: `%APPDATA%\Claude\claude_desktop_config.json`

## 工作流程

1. 创建 vault 文件夹（默认：`obsidian-vault/`）
2. 在 vault 内创建目录结构
3. 生成 `.obsidian/obsidian.json` 配置
4. 创建基础模板文件
5. 提供 MCP 安装命令（带绝对路径提示）

## 输出内容

- ✅ PARA 目录结构
- ⚙️ `.obsidian/obsidian.json` 配置
- 📝 2个基础模板（Daily Note、Project Note）
- 🔧 MCP Obsidian 安装命令

## 推荐社区插件

安装后可在 Obsidian 设置中启用：
- **Daily notes** - 每日笔记
- **Templates** - 模板系统
- **Graph Analysis** - 知识图谱分析
