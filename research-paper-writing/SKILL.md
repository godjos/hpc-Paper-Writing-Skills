---
name: research-paper-writing
description: Improve, revise, edit, polish, or review HPC and systems papers with terminology-aware prose, section structure, claim-evidence alignment, scalability logic, reproducibility notes, reviewer comments, LaTeX text, and non-native English support. Use for Abstract, Introduction, Related Work, Method, Experiments, Conclusion, figures/tables, performance claims, revision passes, or submission readiness.
---
# HPC Paper Writing

## Purpose

Use this skill to help HPC and systems papers read clearly to skeptical reviewers.
Prioritize a coherent paper story, precise terminology, supported performance claims,
readable experiments, and concise reviewer-facing prose.

## Mode Selection

Choose the lightest mode that satisfies the user request.

| Mode | Use when | Default references | Default output |
| --- | --- | --- | --- |
| Quick polish | The user asks to polish only, smooth, shorten, grammar-check, or improve wording for a paragraph or small passage. Use conservative polish by default: improve clarity, grammar, and flow while preserving the original technical meaning. | `hpc-terminology.md`, `hpc-prose-polish.md` | Revised text plus important changes, abbreviation/terminology note, and any specificity withheld because the draft lacks evidence. |
| Revision pass | The user asks to revise, edit, improve this section, respond to reviewer comments, or modify an existing section beyond sentence-level polish. Diagnose structure and evidence before rewriting; do not treat revision as grammar-only polish. | `paper-revision-polish.md`, `hpc-terminology.md`, `hpc-prose-polish.md`, section guide when relevant | Diagnosis, compact revision plan, revised text, claim/evidence risks, and remaining missing inputs. |
| Section rewrite | The user asks to draft or rewrite Abstract, Introduction, Related Work, Method, Experiments, or Conclusion. | `hpc-terminology.md`, section guide, `hpc-prose-polish.md` | Terminology ledger, mini-outline, revised paragraphs with roles, abbreviation note, and claim-evidence map. |
| Evidence review | The user asks whether experiments, results, claims, figures, baselines, scaling, or artifacts are convincing. | `performance-evidence.md`, `experiments.md`, `figures-tables.md`, `reproducibility-artifact.md` | Reviewer risks, unsupported claims, missing evidence, and concrete revision actions. |
| Submission review | The user asks for pre-submission, reviewer, venue, or full-paper review. | `paper-review.md`, `venue-reviewer-profile.md`, `performance-evidence.md`, `reproducibility-artifact.md` | Prioritized rejection risks, claim-evidence gaps, reproducibility gaps, closest-work risks, and final action list. |

If the user does not specify a mode, infer it from the task. Do not run the full submission
review for a small wording request.

## Default Workflow

1. Identify the target section, task mode, paper type, venue if known, and available evidence.
2. Build only the terminology needed for the current task: workload, platform, parallel model,
   execution entities, metrics, baselines, units, abbreviations, and environment assumptions.
   For polish requests, use only terms supported by the source draft or supplied user context.
3. Load only the references required by the selected mode. Do not load every guide or example.
4. For revision requests, run a reverse-outline pass before rewriting: main claim, paragraph
   role, topic sentence, supporting evidence, flow gap, and unsupported overclaim.
5. Draft or review paragraph-by-paragraph. Keep one message per paragraph and preserve the
   terminology ledger.
6. Check abbreviation order before final output: each abbreviation must be expanded at first use
   unless it is universally standard in context.
7. Check major claims against available evidence. Weaken or remove unsupported claims.
8. Run the prose polish pass when producing final prose.
9. For full-paper or submission work, finish with adversarial self-review.

## Reference Router

Load these files only when the task calls for them:

- Paper intake: `references/paper-intake.md`
- Abstract: `references/abstract.md`
- Introduction: `references/introduction.md`
- Related Work: `references/related-work.md`
- Method: `references/method.md`
- Experiments: `references/experiments.md`
- Conclusion: `references/conclusion.md`
- Figures and tables: `references/figures-tables.md`
- Performance evidence: `references/performance-evidence.md`
- Reproducibility and artifact: `references/reproducibility-artifact.md`
- Venue and reviewer profile: `references/venue-reviewer-profile.md`
- Paper review: `references/paper-review.md`
- Paper revision and polish: `references/paper-revision-polish.md`
- HPC terminology: `references/hpc-terminology.md`
- HPC prose polish: `references/hpc-prose-polish.md`
- Paragraph flow source: `references/does-my-writing-flow-source.md`
- Example bank: `references/examples/index.md`

Use examples only when the user asks for templates/examples, the requested section is hard to
structure, or a concrete HPC mini case would clarify the writing pattern. Reuse sentence logic,
not exact wording.

## Writing Rules

1. State each paragraph's message in its first sentence.
2. Keep one paragraph focused on one message.
3. Define workload names, hardware terms, runtime terms, and non-obvious abbreviations before reuse.
4. Use precise HPC/system terms at the correct layer: node, socket, NUMA domain, core, process,
   rank, thread, task, GPU, SM, warp, kernel, cache, DRAM, HBM, PCIe, NVLink, InfiniBand,
   RDMA, collective, halo exchange, I/O, strong scaling, and weak scaling, but only when the
   draft or supplied context supports that layer and term.
5. Preserve canonical names, abbreviations, capitalization, and units from the user's draft unless
   a naming change is requested.
6. Connect sentences through cause, contrast, consequence, refinement, or example.
7. Separate end-to-end gains from kernel-level, microbenchmark, or tuning-only gains.
8. Avoid making the work sound like a minor patch to a naive baseline.
9. State comparison conditions, platform assumptions, and experimental settings when needed for
   reviewer trust.
10. Prefer concise, reviewer-facing prose over mechanical academic phrasing.

## Output Contracts

### Quick Polish

Return:

1. Revised text.
2. Important changes, limited to changes that affect clarity, correctness, fluency, LaTeX safety,
   or reviewer perception.
3. Abbreviation/terminology note, or `none`.
4. Withheld specificity note explaining any more-specific term that was preserved, weakened, or not
   introduced because the draft lacks evidence or setup detail.

Quick Polish must not add or replace workload, platform, parallel model, bottleneck, metric,
baseline, hardware, communication pattern, memory hierarchy, system layer, or mechanism details
unless they are present in the user's draft or explicitly supplied context.

### Revision Pass

Return:

1. Diagnosis covering the section's main claim, paragraph roles, topic-sentence alignment,
   supporting evidence, flow gaps, and unsupported overclaims.
2. Compact revision plan with the smallest structural and language changes needed.
3. Revised text.
4. Claim/evidence risks using `Claim: ... | Evidence: ... | Risk: ...`.
5. Remaining missing inputs, or `none`.

Revision Pass must revise structure, evidence alignment, and prose in that order. It may reorganize
or combine paragraphs, but it must not invent results, citations, reviewer intent, hardware details,
or experimental conditions.

### Section Rewrite

Return:

1. Compact HPC terminology ledger.
2. Section outline with 3-7 bullets.
3. Revised paragraphs with paragraph roles.
4. Abbreviation first-use note, or `none`.
5. Claim-evidence map for major claims using `Claim: ... | Evidence: ... | Status: supported/needs evidence`.
6. Short self-review note covering clarity, flow, terminology, unsupported claims, scaling evidence,
   and missing environment details.

### Evidence Review

Return:

1. Major claim-evidence gaps.
2. Baseline fairness and comparison-condition risks.
3. Scaling, profiling, ablation, and end-to-end evidence gaps.
4. Figure/table readability issues when relevant.
5. Concrete revision actions, ordered by reviewer risk.

### Submission Review

Return:

1. Top reviewer risks, ordered by severity.
2. Claim-evidence map for headline claims.
3. Experiment adequacy note covering baselines, scaling, causality, and end-to-end evidence.
4. Reproducibility gap note covering hardware/software, build, launch, workloads, parameters, and artifact details.
5. Closest-work or novelty risk note when relevant.
6. Final action list.

## Optional Add-ons

Include these only when requested or clearly necessary:

- Paragraph language rubric: `P# | role: ... | verdict: pass/revise | reason: ...`
- Change justification for significant polish or revision decisions.
- Venue/reviewer-risk note.
- Full five-dimension self-review: contribution, writing clarity, experimental strength,
  evaluation completeness, and method design soundness.
- Detailed reproducibility checklist.
- Detailed figure/table redesign suggestions.

Resolve every `revise` verdict before final output unless missing user-provided evidence or setup
details make that impossible.

## Safety and Fallbacks

1. If required context is missing, state the assumption and proceed with a conservative rewrite.
2. If a claim is unsupported, weaken it, mark it as needing evidence, or remove it.
3. If flow remains weak, use temporary section headers or transition phrases during revision, then
   remove unnecessary scaffolding from the final prose.
4. If the text still reads generic or non-HPC, rerun `references/hpc-prose-polish.md`.
5. Do not invent results, baselines, venues, hardware details, artifact status, citations,
   bottlenecks, mechanisms, system layers, metric types, workload semantics, communication
   patterns, or memory-hierarchy details.

## Maintainer Map

Use this map when updating the skill later:

- Change default behavior in `Mode Selection`, `Default Workflow`, and `Output Contracts`.
- Change language style in `references/hpc-prose-polish.md`; keep only the trigger rule here.
- Change revision workflow in `references/paper-revision-polish.md`.
- Change terminology policy in `references/hpc-terminology.md`; keep only the short rule list here.
- Change section structure in the matching section guide under `references/`.
- Change experiment/reviewer standards in `performance-evidence.md`, `paper-review.md`,
  `reproducibility-artifact.md`, or `venue-reviewer-profile.md`.
- Add examples under `references/examples/` and update `references/examples/index.md`.
- Avoid duplicating detailed guidance in this file and a reference file. Put detail in references;
  keep this file as router, contract, and invariant rules.
- Keep this file short enough to scan quickly. If a new rule needs examples, move the examples to
  `references/`.
