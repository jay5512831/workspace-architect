---
name: workspace-architect
description: "Universal workspace architect. Builds customized AI-powered workstations for any complex scenario — team management, project leadership, research, startups, and more. Uses 'Omniscient SOUL + Context-based Project Splitting' architecture instead of multi-agent dispatch."
description_zh: "通用工作台架构师。为任何复杂场景（团队管理、项目负责人、论文研究、创业等）搭建定制化AI工作空间。采用'全能SOUL + 上下文项目拆分'架构。"
description_en: "Universal workspace architect for any complex scenario. Builds customized AI workstations with Omniscient SOUL + Project Splitting architecture."
version: 1.0.0
---

# 工作台架构师 — Workspace Architect

> 一个Skill，为任何复杂场景生成定制化的AI工作空间。

---

## 什么时候加载这个Skill

- 用户想要搭建一个新的工作空间/工作台
- 用户需要整理一个复杂的事务（项目管理、团队管理、论文、创业、装修…）
- 用户提到"帮我建一个工作空间"、"帮我梳理工作台"、"我有个复杂的事情需要管理"
- 用户想了解"全能SOUL + 项目拆分"这套AI工作方法论

---

## 工作流程

加载后，先判断用户意图：

**想了解架构方法论？** → 读取 `references/architecture-guide.md`，向用户讲解为什么用全能SOUL而非多Agent分发

**想新建工作空间？** → 进入下面的"问卷 → 生成"流程

---

## 问卷收集流程

通过 `ask_followup_question` 工具分两轮收集信息：

### 第一轮：核心场景

用一个开放式问题开场：

> "你要用这个工作空间管理什么事？简单描述一下场景。"

同时收集：
1. **场景描述**（自由输入）
2. **协作规模**：个人独立 / 小组(2-5人) / 中型团队(5-30人) / 大团队(30+)
3. **主要产出格式**：PPT / Excel / Word / 代码 / 设计稿 / 其他（多选）

### 第二轮：AI分析 + 确认

根据第一轮的场景描述，AI分析出涉及的领域/模块（3-7个），列出来让用户确认或调整。同时收集：

4. **领域确认**：AI建议的领域列表，用户可增删改
5. **是否有历史资料需要导入**：是/否
6. **工作空间路径**：用户指定

### 问卷设计详情

读取 `references/questionnaire.md` 获取完整的问卷问题设计和分支逻辑。

---

## 生成流程

问卷收集完成后，按以下步骤生成定制工作空间：

1. **创建目录结构** — 读取 `references/directory-spec.md`，创建标准目录
2. **生成SOUL.md** — 读取 `references/soul-template.md`，替换变量，填入用户场景的领域方法论
3. **生成模板文件** — 根据用户确认的领域，为每个领域创建 `templates/{领域}/` 目录和对应模板
4. **配置MEMORY.md** — 根据领域列表生成记忆分区框架
5. **生成辅助文件** — IDENTITY.md、README.md、inbox/README.md

生成时参考 `scripts/generate-guide.md` 中的详细操作步骤和变量映射表。

---

## 生成后的工作空间标准结构

```
{用户指定路径}/
├── SOUL.md              ← 全能人设 + 领域方法论 + 4大自动工作流
├── IDENTITY.md          ← 身份信息
├── README.md            ← 使用说明
├── .workbuddy/
│   └── memory/
│       └── MEMORY.md    ← 长期记忆（按领域分区）
├── templates/           ← 领域模板库（建项时自动拷贝）
│   ├── {领域1}/
│   ├── {领域2}/
│   └── ...
├── projects/            ← 活跃项目（AI按事项自动创建）
├── archive/             ← 已结项归档
└── inbox/               ← 待整理资料收件箱
    └── README.md
```

---

## SOUL.md 中的4大自动工作流

生成的SOUL.md会内置这4个工作流，读取 `references/digest-workflow.md` 获取资料消化工作流的详细定义：

1. **自动建项** — 用户说一句话，AI在projects/下创建目录、拷模板、读记忆填数据
2. **自动结项** — 用户说"这事结了"，AI移入archive/、更新memory摘要
3. **资料归档** — 用户丢资料到inbox/或对话中，AI自动分类到对应位置
4. **资料消化** — 批量处理历史资料的4阶段流程（收集-理解-归类-反馈）
