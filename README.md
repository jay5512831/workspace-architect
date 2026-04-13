[中文版](README_CN.md) | **English**

# 🏗️ Workspace Architect

> A universal AI skill that builds customized workstations for any complex scenario — team management, project leadership, research, startups, and more.

## What is this?

**Workspace Architect** is a [WorkBuddy](https://www.codebuddy.cn/workbuddy) Skill that replaces the outdated "multi-agent dispatch" pattern with a superior **"Omniscient SOUL + Context-based Project Splitting"** architecture.

Instead of simulating corporate org charts with multiple specialized agents (which loses AI's key advantages), it creates **one all-knowing assistant** powered by domain-specific knowledge packs and project-driven workflows.

## Why not Multi-Agent?

| Multi-Agent (Old) | Omniscient SOUL (New) |
|---|---|
| Information lost between agents | Zero information loss |
| Extra dispatch/routing layer | Direct handling, no middleman |
| Cross-domain issues handled poorly | Natural cross-domain reasoning |
| Mimics human org limitations | Leverages AI's unlimited knowledge capacity |

> "Simulating a corporate hierarchy with AI agents throws away AI's strengths and imports human weaknesses."

## Architecture

```
{workspace}/
├── SOUL.md              ← All-knowing assistant (persona + domain methodology + workflows)
├── IDENTITY.md          ← Identity info
├── README.md            ← Usage guide
├── .workbuddy/memory/   ← Long-term memory (persistent knowledge)
├── templates/           ← Domain template library (auto-copied when creating projects)
├── projects/            ← Active projects (AI auto-creates per task)
├── archive/             ← Completed project archive
└── inbox/               ← Material intake (drop files, AI digests them)
```

## Features

- **🎯 Questionnaire-driven setup** — AI asks about your scenario, then generates a fully customized workspace
- **📁 Project-based organization** — Work organized by "things to do", not "departments"
- **🤖 4 automatic workflows**:
  1. **Auto-create projects** — Say what you need, AI sets up the project directory
  2. **Auto-archive projects** — Say "done", AI archives and saves key learnings
  3. **Material filing** — Drop content, AI classifies and routes it
  4. **Bulk digestion** — Feed historical materials, AI processes them in 4 phases
- **📝 Domain templates** — Reusable templates for each domain, auto-populated
- **🧠 Persistent memory** — Cross-project knowledge continuity via MEMORY.md
- **🔌 Extensible** — Add new domains by creating template directories, no core changes needed

## How to Use

### Install the Skill

Copy this repository to your WorkBuddy skills directory:

```bash
# User-level (available across all workspaces)
git clone https://github.com/jay5512831/workspace-architect.git ~/.workbuddy/skills/workspace-architect

# Or project-level (specific workspace only)
git clone https://github.com/jay5512831/workspace-architect.git .workbuddy/skills/workspace-architect
```

### Use in WorkBuddy

Once installed, simply tell WorkBuddy:

> "帮我搭建一个新的工作空间" / "I need to set up a workspace for [your scenario]"

The skill will automatically:
1. Ask you about your scenario through a structured questionnaire
2. Analyze your needs and suggest domain modules
3. Generate a fully customized workspace with SOUL, templates, and workflows

### Example Scenarios

- **Team Management** — OKR, recruiting, talent development, reporting
- **Project Leadership** — Milestones, stakeholders, risks, deliverables
- **Research/Thesis** — Literature review, experiments, writing, review cycles
- **Startup** — Product, fundraising, hiring, operations
- **Event Planning** — Vendors, timeline, budget, logistics
- **Any complex endeavor** — The skill adapts to whatever you throw at it

## File Structure

```
workspace-architect/
├── SKILL.md                              # Main skill definition
├── README.md                             # This file
├── LICENSE                               # MIT License
├── references/
│   ├── architecture-guide.md             # Why Omniscient SOUL > Multi-Agent
│   ├── soul-template.md                  # SOUL.md template with {{variables}}
│   ├── directory-spec.md                 # Standard directory structure spec
│   ├── questionnaire.md                  # Questionnaire design (2 rounds)
│   └── digest-workflow.md                # 4-phase material digestion workflow
└── scripts/
    └── generate-guide.md                 # Step-by-step workspace generation guide
```

## Language

The skill's internal content is in **Chinese (中文)**, as it was designed for Chinese-speaking users. The architecture concepts and workflows are universal and work in any language.

## License

MIT
