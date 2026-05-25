# Skills: HPC Paper Writing

[中文介绍](./README_zh.md).

> Important Attribution
> Most writing knowledge and methodology in this repository comes from Prof. Peng Sida (彭思达)'s open study notes:
> https://pengsida.notion.site/c1a22465a0fa4b15a12985223916048e
> Prof. Peng's original repository:
> https://github.com/pengsida/learning_research
> I sincerely thank Prof. Peng for openly sharing these valuable experiences.
> My contribution is organization, structured adaptation, and packaging as reusable Skills.

## Repository Overview

This repository currently provides one skill package for HPC and system-style papers:

- `research-paper-writing/`
  - `SKILL.md`: mode routing, default workflow, output contracts, and maintainer map for HPC papers
  - `references/`: section-specific writing guides, checklists, and templates
  - `agents/openai.yaml`: agent metadata

`SKILL.md` now uses a lightweight entry design: it chooses the smallest mode that satisfies the request instead of running a full submission review every time. Detailed writing rules, examples, and checklists live in `references/` so they can be edited independently.

Main modes:

- `Quick polish`: conservative small-passage polish with sentence-level original/problem/proposed-rewrite/reason tables before any clean rewrite
- `Revision pass`: section-level revision for existing text, with reverse outline, paragraph roles, claim/evidence risks, flow gaps, and sentence-level rewrite proposals before final polish
- `Pre-submission polish loop`: repeated submission-facing passes that diagnose the highest reviewer risk, propose sentence-level edits, verify claim/evidence and cross-section consistency, and report next-round blockers
- `Section rewrite`: section-level rewriting with terminology ledger, mini-outline, paragraph roles, and claim-evidence map
- `Evidence review`: experiments, baselines, fairness, scaling, profiling, figures/tables, and artifact risks
- `Submission review`: pre-submission reviewer risks, reproducibility, closest-work risks, and final action list

Typical use cases:

- Drafting or rewriting Abstract / Introduction / Related Work / Method / Experiments / Conclusion
- Polishing sentence-level flow with explicit original sentence, problem, proposed rewrite, and reason before applying changes
- Revising an existing section with diagnosis first: main claim, topic sentences, supporting evidence, flow gaps, unsupported overclaims, and final polished text
- Running repeated pre-submission polishing loops with a change log, reviewer-concern map, cross-section consistency check, and next-round blocker list
- Protecting LaTeX commands, citations, references, labels, equations, macros, and code-like identifiers during polish
- Improving non-native English grammar and fluency while preserving the author's technical meaning
- Explaining system scope, hardware assumptions, and performance targets clearly
- Preserving HPC-specific terminology through a workload/platform/metric terminology ledger
- Checking claim-evidence alignment against scaling, profiling, and end-to-end results
- Running pre-submission self-review from a reviewer mindset
- Improving experimental setup clarity, reproducibility notes, and scalability narratives
- Building a paper-intake canvas before rewriting: venue, paper type, bottleneck, evidence packet, and reviewer risks
- Auditing baseline fairness, strong/weak scaling, profiling causality, and artifact readiness
- Using HPC mini cases for MPI+CUDA stencil, sparse matrix kernels, collectives, checkpointing, and NUMA-aware runtimes

Key high-level references:

- `research-paper-writing/references/paper-intake.md`: intake canvas and reviewer-risk forecast
- `research-paper-writing/references/paper-revision-polish.md`: revision workflow for reverse outlining, claim/evidence diagnosis, reviewer-comment edits, and conservative final polish
- `research-paper-writing/references/style-calibration.md`: author, venue, and sample-based style anchors so rewrites stay paper-specific rather than generic
- `research-paper-writing/references/final-self-check.md`: final gate for hard safety, HPC style consistency, claim/evidence completeness, AI-pattern risk, and reviewer readiness
- `research-paper-writing/references/performance-evidence.md`: claim-evidence matching for performance claims
- `research-paper-writing/references/hpc-prose-polish.md`: sentence-level flow, HPC/system prose polish, and per-paragraph `pass`/`revise` language rubric
- `research-paper-writing/references/reproducibility-artifact.md`: hardware/software, build, launch, and artifact checklist
- `research-paper-writing/references/venue-reviewer-profile.md`: venue-specific reviewer expectations
- `research-paper-writing/references/figures-tables.md`: scaling, breakdown, roofline, timeline, and result-table guidance

## Maintenance Notes

- To change default behavior, edit `Mode Selection`, `Default Workflow`, and `Output Contracts` in `research-paper-writing/SKILL.md`
- To change the revision workflow, edit `references/paper-revision-polish.md`
- To change style calibration, edit `references/style-calibration.md`
- To change final self-check gates, edit `references/final-self-check.md`
- To change prose style, edit `references/hpc-prose-polish.md`
- To change terminology rules, edit `references/hpc-terminology.md`
- To change a section pattern, edit the matching section file such as `references/introduction.md` or `references/method.md`
- To add examples, place them under `references/examples/` and update `references/examples/index.md`
- Avoid duplicating the same detailed rule in both `SKILL.md` and a reference file; keep `SKILL.md` as router, contract, and invariant rules

## Installation

Assume you are in the repository root.

### 0) `npx skills` installer

If you want to install this skill through the `npx skills` CLI, Node.js 18+ is recommended.

Install from the current repository:

```bash
npx skills add .
```

Install from a GitHub repository:

```bash
npx skills add https://github.com/godjos/hpc-Paper-Writing-Skills
```

Install only for Codex:

```bash
npx skills add . -a codex
```

You can also add `-g` to install globally, or `--list` to preview the skills before installing.

### 1) Codex

Copy the skill into `$CODEX_HOME/skills/`:

```bash
mkdir -p "$CODEX_HOME/skills"
cp -R research-paper-writing "$CODEX_HOME/skills/"
```

Usage example:

```text
Use $research-paper-writing to improve my HPC paper's Introduction.
```

Other useful prompts:

```text
Use $research-paper-writing to polish only this LaTeX paragraph.
Use $research-paper-writing to revise this Introduction section with diagnosis before rewriting.
Use $research-paper-writing to edit this response to reviewer comment and update the manuscript text.
```

### 2) CC (Claude Code)

Use either a global or project-level installation.

Global:

```bash
mkdir -p "$HOME/.claude/skills"
cp -R research-paper-writing "$HOME/.claude/skills/"
```

Project-level:

```bash
mkdir -p .claude/skills
cp -R research-paper-writing .claude/skills/
```

In prompts, explicitly request this skill, for example: `Please use the research-paper-writing skill`.

### 3) Gemini

Copy this skill into your Gemini skills directory:

```bash
mkdir -p "$HOME/.gemini/skills"
cp -R research-paper-writing "$HOME/.gemini/skills/"
```

Then ask concrete tasks in Gemini (for example, rewriting an Abstract with claim-evidence and scaling checks).

## Credits

Again, this repository is primarily based on Prof. Peng Sida (彭思达)'s open notes, while my work focuses on curation and Skills adaptation.
Prof. Peng's original repository: https://github.com/pengsida/learning_research
