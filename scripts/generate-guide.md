# 工作空间生成指引

## 概述

当问卷收集完成后，AI按照本文档的步骤生成定制化工作空间。

## 输入

问卷结果汇总（参考 questionnaire.md 中的结构）：

```yaml
scenario: "场景描述"
role_name: "角色名"
role_description: "角色一句话描述"
scale: "规模"
output_formats: ["PPT", "Excel", ...]
domains:
  - name: "领域英文名"
    label: "领域中文名"
    brief: "一句话描述"
has_history: true/false
workspace_path: "路径"
```

## 步骤1：创建目录结构

参照 `references/directory-spec.md` 创建：

```
{workspace_path}/
├── .workbuddy/memory/
├── templates/
├── projects/
├── archive/
└── inbox/
```

对每个domain创建 `templates/{domain.name}/`。

## 步骤2：生成SOUL.md

读取 `references/soul-template.md`，替换变量：

| 变量 | 替换为 |
|------|--------|
| `{{ROLE_NAME}}` | `role_name` |
| `{{ROLE_DESCRIPTION}}` | `role_description` |
| `{{DOMAIN_LIST_BRIEF}}` | 所有domain.label用顿号连接 |
| `{{SCENARIO_CONTEXT}}` | 基于scenario和scale生成的背景段落（2-3句话） |
| `{{DOMAINS_METHODOLOGY}}` | **为每个domain生成200-300字方法论**（见下方） |
| `{{TEMPLATE_INDEX}}` | 根据实际templates/目录生成映射列表 |
| `{{CUSTOM_WORKFLOWS}}` | 如有特殊需求则追加，否则留空 |

### 如何生成领域方法论

对每个domain，AI根据自身知识生成该领域的核心方法论要点。格式：

```markdown
### {domain.label}

{200-300字核心方法论，包含：}
- 该领域的核心思维框架
- 关键原则（3-5条）
- 常见陷阱提醒
- 如需生成PPT/Excel/Word，提示使用对应skill
```

**重要**：方法论只写精华，不写具体模板内容。具体模板在templates/中。

### 产出物格式引导

根据 `output_formats` 在SOUL.md中加入对应提示：
- 含PPT → 加入 "制作PPT时，使用 `pptx` skill 生成"
- 含Excel → 加入 "处理表格数据时，使用 `Excel 文件处理` skill"
- 含Word → 加入 "编写Word文档时，使用 `docx` skill 生成"

## 步骤3：生成模板文件

对每个domain，根据其领域特点创建3-5个常用模板文件：

```
templates/{domain.name}/
├── 模板1.md
├── 模板2.md
└── 模板3.md
```

**模板编写规范：**
- 每个模板是独立的Markdown文件
- 包含清晰的标题和结构
- 使用 `<!-- 请替换为实际数据 -->` 标记需要填充的部分
- 包含简短的使用说明（在文件开头用引用块）
- 填充示例数据帮助理解格式

**模板数量指导：**
- 常见领域（财务、OKR、招聘等）：参考已有经验创建3-5个核心模板
- 非常见领域：创建2-3个基础模板，后续用户可以补充

## 步骤4：配置MEMORY.md

```markdown
# 长期记忆

<!-- 这是工作空间的持久化知识库。AI会在工作过程中自动更新这里的内容。 -->

## 概况

<!-- 请替换为实际数据 -->
- **场景**：{scenario}
- **规模**：{scale}
- **创建时间**：{当前日期}

{为每个domain生成一个二级标题分区：}

## {domain.label}

<!-- 待填充。{domain.brief}相关的持久化数据会自动记录在这里。 -->
```

## 步骤5：生成辅助文件

### IDENTITY.md
```markdown
- **Name**: {role_name}
- **Creature**: AI管理助手
- **Vibe**: 简洁务实、有主见、主动推进
- **Emoji**: 🎯
```

### README.md
```markdown
# {role_name} 工作台

## 这是什么
{基于scenario的1-2句话描述}

## 目录说明
- `templates/` — 模板库，{domain列表}
- `projects/` — 活跃项目，AI按需自动创建
- `archive/` — 已结项归档
- `inbox/` — 待整理资料，丢进去让AI消化
- `.workbuddy/memory/` — 长期记忆，AI自动维护

## 怎么用
1. 直接说你要做的事，AI自动建项目
2. 历史资料丢到 inbox/，让AI消化
3. 事情做完了说"归档"，AI自动结项

## 新增领域
1. 在 templates/ 下建新目录，放入模板文件
2. 在 SOUL.md 的"领域方法论"和"模板索引"中补充描述
```

### inbox/README.md
```markdown
# 📥 资料收件箱

把待整理的资料文件放到这个目录下，然后告诉AI：

> "帮我消化inbox里的资料"

AI会自动执行4阶段消化流程：
1. **收集** — 扫描这里的文件
2. **阅读理解** — 分析每份资料的主题、领域、状态
3. **归类** — 知识写入memory、进行中的建projects、完结的归archive
4. **反馈** — 给你一份归类报告，确认后执行

### 支持的资料来源
- Markdown文件（.md）
- 文本文件（.txt）
- WorkBuddy导出的对话/记忆文件
- 其他文本格式

### 小提示
- 每批处理最多10份，处理完会问你要不要继续
- 你也可以直接在对话中粘贴内容，不一定要放文件
```

## 步骤6：最终检查

生成完成后，向用户展示：

1. 创建的目录结构总览
2. SOUL.md的领域方法论摘要
3. 各领域的模板文件列表
4. 下一步建议（如有历史资料，引导开始消化流程）
