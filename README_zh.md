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
  - `SKILL.md`：HPC 论文的模式路由、默认流程、输出契约与维护地图
  - `references/`：按章节拆分的写作指南、检查清单与模板
  - `agents/openai.yaml`：Agent 元信息

`SKILL.md` 现在采用轻量入口设计：默认选择能完成任务的最小模式，而不是每次都执行完整投稿审查。详细写作规则、示例和检查清单放在 `references/` 中，便于后续单独修改。

主要模式：

- `Quick polish`：保守小段落润色，先逐句列出原句、问题、建议改写和理由，再由用户确认是否生成最终改写
- `Revision pass`：面向已有文本的章节级修改，先做 reverse outline、段落角色、claim/evidence 风险、衔接问题，再给出逐句改写提案
- `Pre-submission polish loop`：面向投稿前反复打磨的迭代流程，先诊断最高 reviewer 风险，再逐句提出修改，并检查 claim/evidence、跨章节一致性和下一轮 blocker
- `Section rewrite`：章节级重写，包含术语表、mini-outline、段落角色和 claim-evidence map
- `Evidence review`：实验、baseline、公平性、scaling、profiling、图表和 artifact 风险检查
- `Submission review`：投稿前 reviewer 风险、复现性、closest-work 和完整行动清单

默认行为：任何润色、修改或重写已有论文文本的请求，第一轮都只给逐句修改提案和理由，不能直接改论文源文件；即使用户说“直接改原文”“直接修改文件”或“应用到 manuscript/source”，也必须先给提案并等待确认。只有用户看过提案并确认应用后，技能才会修改源文件；修改后必须报告改了哪些文件、哪些句子或段落、修改理由，以及保留了哪些 LaTeX 命令、引用和技术含义。

常见使用场景：

- 撰写或重写 Abstract / Introduction / Related Work / Method / Experiments / Conclusion
- 逐句润色句子级流畅度：先给出原句、问题、建议改写和理由，再保护技术含义不被误改
- 用户确认逐句提案后，应用最小安全源文件补丁，并给出逐项 change log 和理由
- 对已有章节先诊断再修改：main claim、topic sentence、supporting evidence、flow gap、unsupported overclaim 和最终润色文本
- 投稿前反复打磨：每轮给出 change log、reviewer-concern map、跨章节一致性检查和下一轮 blocker
- 润色 LaTeX 文本时保护命令、引用、交叉引用、标签、公式、宏和类似代码的标识符
- 改善非英语母语写作者的语法和流畅度，同时保留作者原本的技术含义
- 讲清楚系统范围、硬件假设和性能目标
- 通过 workload/platform/metric 术语表保持 HPC 专用术语一致
- 做 claim-evidence 对齐检查，尤其是与 scaling、profiling 和端到端结果对齐
- 提交前从 reviewer 视角进行自审
- 强化实验设置清晰度、可复现性和可扩展性叙述
- 在改写前建立 paper-intake 画布：venue、论文类型、瓶颈、证据包和 reviewer 风险
- 审查 baseline 公平性、强/弱扩展、profiling 因果链和 artifact 准备情况
- 使用 MPI+CUDA stencil、稀疏矩阵、collective、checkpointing、NUMA-aware runtime 等 HPC mini case

关键高级参考文件：

- `research-paper-writing/references/paper-intake.md`：开工前输入清单和 reviewer 风险预判
- `research-paper-writing/references/paper-revision-polish.md`：通过 reverse outline、claim/evidence 诊断、审稿意见修改和保守最终润色来指导 revision 工作流
- `research-paper-writing/references/style-calibration.md`：基于作者样稿、venue 风格和目标语气提炼风格锚点，避免改写成泛化 AI 学术腔
- `research-paper-writing/references/final-self-check.md`：终稿 gate，检查硬性安全、HPC 风格一致性、claim/evidence 完整性、AI 模板味和 reviewer-readiness
- `research-paper-writing/references/performance-evidence.md`：性能 claim 与证据类型匹配
- `research-paper-writing/references/hpc-prose-polish.md`：句子级流畅度、HPC / system 论文语言润色，以及逐段 `pass` / `revise` 语言 rubric
- `research-paper-writing/references/reproducibility-artifact.md`：硬件/软件、构建、运行和 artifact 检查清单
- `research-paper-writing/references/venue-reviewer-profile.md`：不同 venue 的 reviewer 关注点
- `research-paper-writing/references/figures-tables.md`：扩展性图、breakdown、roofline、timeline 和结果表规范

## 后续维护建议

- 想改默认行为：优先改 `research-paper-writing/SKILL.md` 里的 `Mode Selection`、`Default Workflow` 和 `Output Contracts`
- 想改 revision 工作流：改 `references/paper-revision-polish.md`
- 想改风格校准规则：改 `references/style-calibration.md`
- 想改终稿自检 gate：改 `references/final-self-check.md`
- 想改语言风格：改 `references/hpc-prose-polish.md`
- 想改术语规则：改 `references/hpc-terminology.md`
- 想改某个章节写法：改对应章节文件，例如 `references/introduction.md` 或 `references/method.md`
- 想加示例：放到 `references/examples/`，并同步更新 `references/examples/index.md`
- 尽量不要把同一条细节规则同时写在 `SKILL.md` 和 reference 文件里；`SKILL.md` 只保留路由、契约和不变量

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

其他常用提示词：

```text
Use $research-paper-writing to polish only this LaTeX paragraph.
Use $research-paper-writing to revise this Introduction section with diagnosis before rewriting.
Use $research-paper-writing to edit this response to reviewer comment and update the manuscript text.
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
