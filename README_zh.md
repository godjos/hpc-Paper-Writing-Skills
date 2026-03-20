# Skills: HPC Paper Writing

> 重要归属说明
> 本仓库中的大部分写作经验与方法论来自彭思达老师公开的学习笔记：
> https://pengsida.notion.site/c1a22465a0fa4b15a12985223916048e
> 彭老师原始仓库：
> https://github.com/pengsida/learning_research
> 衷心感谢彭思达老师把这些宝贵经验公开分享出来。
> 我主要做了资料整理、结构化适配，以及 Skills 封装。

## 仓库介绍

当前仓库提供 1 个面向 HPC 和系统论文写作的技能包：

- `research-paper-writing/`
  - `SKILL.md`：HPC 论文的核心流程与使用规则
  - `references/`：按章节拆分的写作指南、检查清单与模板
  - `agents/openai.yaml`：Agent 元信息

常见使用场景：

- 撰写或重写 Abstract / Introduction / Related Work / Method / Experiments / Conclusion
- 讲清楚系统范围、硬件假设和性能目标
- 做 claim-evidence 对齐检查，尤其是与 scaling、profiling 和端到端结果对齐
- 提交前从 reviewer 视角进行自审
- 强化公平比较、可复现性和可扩展性叙述

## 安装方式

以下命令默认在仓库根目录执行。

### 0) `npx skills` 安装器

如果你想通过 `npx skills` CLI 安装这个技能，建议使用 Node.js 18+。

从本地仓库安装：如果你已经把这个仓库克隆到本地电脑上，就在这个项目的根目录里执行 `npx skills add .`。

```bash
npx skills add .
```

从 GitHub 仓库安装：

```bash
npx skills add https://github.com/godjos/hpc-Paper-Writing-Skills
```

仅为 Codex 安装：

```bash
npx skills add . -a codex
```

也可以加上 `-g` 做全局安装，或使用 `--list` 在安装前预览可用技能。

### 1) Codex

将技能复制到 `$CODEX_HOME/skills/`：

```bash
mkdir -p "$CODEX_HOME/skills"
cp -R research-paper-writing "$CODEX_HOME/skills/"
```

使用示例：

```text
Use $research-paper-writing to improve my HPC paper's Introduction.
```

### 2) CC（Claude Code）

可选择全局安装或项目级安装。

全局安装：

```bash
mkdir -p "$HOME/.claude/skills"
cp -R research-paper-writing "$HOME/.claude/skills/"
```

项目级安装：

```bash
mkdir -p .claude/skills
cp -R research-paper-writing .claude/skills/
```

使用时建议在提示词中显式指定，例如：`Please use the research-paper-writing skill`。

### 3) Gemini

可将该技能复制到 Gemini 的技能目录：

```bash
mkdir -p "$HOME/.gemini/skills"
cp -R research-paper-writing "$HOME/.gemini/skills/"
```

随后在 Gemini 中直接给出具体任务（例如：重写 Abstract，并做 claim-evidence 与 scaling 检查）。

## 致谢

再次说明：仓库核心知识来源于彭思达老师公开笔记；我主要负责整理与 Skills 化适配。
彭老师原始仓库：https://github.com/pengsida/learning_research
