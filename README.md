**中文** | [English](README_EN.md)

# 🏗️ 工作台架构师（Workspace Architect）

> 一个通用的 AI 技能，能为任何复杂场景搭建定制化工作空间 —— 团队管理、项目负责、学术研究、创业等等。

## 这是什么？

**工作台架构师** 是一个 [WorkBuddy](https://www.codebuddy.cn/workbuddy) Skill（技能），它用更先进的 **"全能 SOUL + 上下文项目拆分"** 架构，取代了过时的"多 Agent 分发调度"模式。

它不会模拟公司组织架构去搞多个专家 Agent 来回传话（那是把 AI 的优点丢了换上人类的弱点），而是创建 **一个全能助手**，按需加载领域知识包，用项目驱动的方式高效工作。

## 为什么不用多 Agent？

| 多 Agent（旧模式） | 全能 SOUL（新模式） |
|---|---|
| 信息在 Agent 之间传递会丢失 | 零信息损耗 |
| 多了一层分发判断 | 直接处理，没有中间商 |
| 跨领域问题处理不好 | 天然跨领域融合推理 |
| 模拟人类组织架构的局限性 | 发挥 AI 无限知识容量的优势 |

> "模拟公司组织架构来设置多 Agent 协同，是把 AI 的优点丢了，换上了人类的弱点。"

## 架构

```
{workspace}/
├── SOUL.md              ← 全能助手（人设 + 领域方法论 + 工作流）
├── IDENTITY.md          ← 身份信息
├── README.md            ← 使用说明
├── .workbuddy/memory/   ← 长期记忆（持久化知识）
├── templates/           ← 领域模板库（建项时自动拷贝）
├── projects/            ← 活跃项目（AI 按事项自动创建）
├── archive/             ← 已结项归档
└── inbox/               ← 资料收件箱（丢进来，AI 自动消化）
```

## 特性

- **🎯 问卷驱动建站** — AI 通过问卷了解你的场景，自动生成完整定制工作空间
- **📁 按项目组织** — 以"要办的事"为单位组织工作，而不是按"部门/职能"
- **🤖 4 大自动工作流**：
  1. **自动建项** — 你说一句话，AI 自动创建项目目录、拉模板、填数据
  2. **自动结项** — 你说"这事儿结了"，AI 自动归档并保留关键经验
  3. **资料归档** — 丢内容进来，AI 自动分类归到对应目录
  4. **批量消化** — 喂历史资料，AI 分 4 阶段处理（收集→理解→归类→反馈）
- **📝 领域模板** — 每个领域都有可复用模板，建项时自动填充
- **🧠 持久记忆** — 通过 MEMORY.md 实现跨项目的知识延续
- **🔌 可扩展** — 新增领域只需加模板目录，不需要改核心文件

## 如何使用

### 安装技能

将本仓库拷贝到 WorkBuddy 技能目录：

```bash
# 用户级安装（所有工作空间可用）
git clone https://github.com/jay5512831/workspace-architect.git ~/.workbuddy/skills/workspace-architect

# 或项目级安装（仅限当前工作空间）
git clone https://github.com/jay5512831/workspace-architect.git .workbuddy/skills/workspace-architect
```

### 在 WorkBuddy 中使用

安装后，直接对 WorkBuddy 说：

> "帮我搭建一个新的工作空间" / "我需要一个管理 XX 的工作台"

技能会自动：
1. 通过结构化问卷了解你的场景和需求
2. 分析需求并建议领域模块
3. 生成完整的定制工作空间（SOUL + 模板 + 工作流）

### 适用场景

- **团队管理** — OKR、招聘、人才培养、汇报、财务
- **项目管理** — 里程碑、干系人、风险、交付物
- **学术研究 / 论文** — 文献综述、实验、写作、审稿
- **创业** — 产品、融资、招聘、运营
- **活动策划** — 供应商、时间线、预算、后勤
- **任何复杂事务** — 技能会根据你的描述自适应

## 文件结构

```
workspace-architect/
├── SKILL.md                              # 技能主文件
├── README.md                             # 中文说明（本文件）
├── README_EN.md                          # English
├── LICENSE                               # MIT 许可证
├── references/
│   ├── architecture-guide.md             # 架构方法论（全能SOUL > 多Agent）
│   ├── soul-template.md                  # SOUL.md 模板（含变量占位符）
│   ├── directory-spec.md                 # 标准目录结构规范
│   ├── questionnaire.md                  # 问卷设计（2轮收集）
│   └── digest-workflow.md                # 4阶段资料消化流程
└── scripts/
    └── generate-guide.md                 # 工作空间生成指引
```

## 许可证

MIT
