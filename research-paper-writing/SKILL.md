---
name: research-paper-writing
description: Improve HPC and system paper writing quality with clear section structure, scalability logic, reproducibility, and reviewer-facing presentation. Use when drafting or revising Abstract, Introduction, Related Work, Method, Experiments, or Conclusion; polishing figures/tables; checking claim-support alignment; or performing self-review before submission.
---
# HPC Paper Writing

## Purpose

Use this skill to rewrite an HPC or systems paper into a reviewer-friendly, high-clarity draft.
Prioritize first-impression quality, scope clarity, logical flow, scalability evidence, and reproducible claims.

## Core Workflow

1. Run paper intake before rewriting: target venue, paper type, workload, platform, bottleneck, core claim, and available evidence.
2. Clarify the paper story: problem -> bottleneck -> insight -> contribution -> evidence -> limitation.
3. Build an HPC terminology ledger before rewriting: workload, platform, parallel model, execution entities, memory/data movement, metrics, baselines, units, and environment assumptions.
4. Load `references/hpc-terminology.md` plus only the section-specific guidance you need from `references/`.
5. Draft paragraph-by-paragraph, keeping one message per paragraph and preserving the terminology ledger.
6. Run reverse outlining after each section to verify flow, structure, and term consistency.
7. Check major Abstract/Introduction claims against end-to-end results, scaling, profiling, ablation, performance-model, and artifact evidence.
8. Finish with an adversarial self-review using `references/paper-review.md`.

## Writing Principles

1. Keep one paragraph for one message only.
2. State the paragraph message in the first sentence.
3. Define workload names, hardware terms, and runtime terms before reusing them.
4. Use precise HPC terms for the correct system layer: node/socket/NUMA domain/core, process/rank/thread/task, GPU/SM/warp/kernel, cache/DRAM/HBM, PCIe/NVLink/InfiniBand/RDMA, collective/halo exchange/I/O, and strong/weak scaling.
5. Preserve canonical names, abbreviations, capitalization, and units from the user's draft unless a naming change is requested.
6. Maintain sentence-to-sentence flow through cause, contrast, consequence, or refinement.
7. Read as a skeptical reviewer and revise until the draft survives adversarial self-review.
8. Treat visual quality as core content: use a clean system overview figure, pipeline figure, and, if useful, a profiling figure.
9. Use readable, minimal-ink tables and keep formatting tidy and consistent.
10. State performance units, platform assumptions, and experimental settings clearly enough that comparison conditions are readable.

## Paragraph Clarity Check

Use this quick test whenever a paragraph needs a flow or clarity check.

1. Read as an external reader:
   - Does this paragraph have one explicit message?
   - Does the first sentence state what this paragraph will do?
   - Are all key nouns/terms readable without hidden context?
   - Do specialized HPC terms match the terminology ledger and the correct system layer?
   - Does each sentence connect to the previous one with a clear relation (cause, contrast, consequence, refinement, example)?
2. Run reverse outlining for the current section:
   - Write down thesis/main claim.
   - Write down each paragraph topic sentence.
   - Write down the evidence/explanation points under each paragraph.
   - Check mapping: topic sentence -> thesis, and evidence -> topic sentence.
   - Revise or remove any paragraph that cannot be mapped cleanly.
3. If flow is still weak, add temporary section headers and explicit transition phrases during revision, then remove unnecessary headers before finalizing.

Source reference for this check:

- `references/does-my-writing-flow-source.md`

## Section Guides

Load only the needed section file:

- Abstract: `references/abstract.md`
- Introduction: `references/introduction.md`
- Related Work: `references/related-work.md`
- Method: `references/method.md`
- Experiments: `references/experiments.md`
- Conclusion: `references/conclusion.md`
- Paper review: `references/paper-review.md`
- HPC terminology: `references/hpc-terminology.md`
- Paper intake: `references/paper-intake.md`
- Performance evidence: `references/performance-evidence.md`
- Reproducibility and artifact: `references/reproducibility-artifact.md`
- Figures and tables: `references/figures-tables.md`
- Venue and reviewer profile: `references/venue-reviewer-profile.md`
- Paragraph clarity source: `references/does-my-writing-flow-source.md`
- Example bank index: `references/examples/index.md`

## Review and Evidence Checks

Use `references/paper-review.md` for the full checklist and workflow.

1. Add an end-of-draft self-review question list in five dimensions:
   - contribution,
   - writing clarity,
   - experimental strength,
   - evaluation completeness,
   - method design soundness.
2. Treat claim-evidence alignment as a hard constraint, especially for Abstract and Introduction.
3. For HPC papers, treat scaling, throughput, latency, memory, energy, and portability as evidence dimensions.
4. Treat terminology-evidence alignment as a hard constraint: every specialized term, metric, and platform assumption should either be defined, measured, cited, or marked as unknown.
5. Perform adversarial writing: review as a skeptical reviewer and resolve every high-risk question.
6. Revise until major rejection risks are explicitly addressed.

## HPC-Specific Checks

1. Make the contribution explicit: problem, novelty, contribution, and evidence should appear in a clear chain.
2. Separate system improvement from baseline tuning; avoid phrasing that makes the work look like a minor patch.
3. Audit specialized terms for the correct layer: workload, algorithm, runtime, compiler, library, CPU/GPU architecture, memory hierarchy, network/interconnect, storage, and metric.
4. For experiments, check baseline choice, strong/weak scaling, sensitivity, ablation, workload diversity, and hardware/software disclosure.
5. Check that baseline choice, placement, affinity, NUMA/GPU handling, repetition count, and normalization are clear from the experimental setup; add a clarifying comparison note only when the setup would otherwise be ambiguous or reviewer-sensitive.
6. Separate end-to-end gains from kernel-level, microbenchmark, or tuning-only gains.
7. Check baseline fairness: compiler flags, library/runtime versions, placement, affinity, tuning budget, problem size, warm-up, repetitions, and normalization.
8. Explain the source of performance gains with profiling, breakdowns, roofline reasoning, communication/memory analysis, or a lightweight performance model.
9. Make figures and tables stand alone: every result visualization should support one claim and label axes, units, and conditions clearly.
10. Include limitations, threats to validity, artifact readiness, and reproducibility notes before finalizing the draft.
11. Confirm submission readiness: abstract, introduction, method, evaluation, conclusion, and artifact/reproducibility notes all tell one consistent story.

## Submission Readiness Checklist

Use this final pass before submission or internal sign-off.

1. Abstract: state the problem, key idea, and strongest result without unsupported claims.
2. Introduction: explain why the problem matters, why existing approaches fall short, and what this paper contributes.
3. Related Work: position the paper against the closest systems and clarify the differentiator.
4. Method: define the system model, assumptions, and design choices clearly enough to reproduce the approach.
5. Evaluation: include the right baselines, the right workloads, and the right metrics for the claim.
6. Results: every headline claim should have direct evidence in a figure, table, or measured comparison.
7. Figures and tables: verify labels, units, legends, captions, and axis scales are readable and consistent.
8. Limitations: state what the system does not solve and where the evidence is incomplete.
9. Reproducibility: check hardware/software versions, dataset or workload availability, seeds, parameters, and artifact references.
10. Consistency: terminology, abbreviations, and contribution language should match across the whole draft.
11. Final polish: check grammar, citation completeness, formatting, and conference or journal submission constraints.
12. Reviewer risk: identify the closest-work, novelty, baseline-fairness, scaling, and artifact risks before final sign-off.

## Execution Rules

1. Build a mini-outline before drafting prose.
2. Build a terminology ledger before drafting prose and use it as a constraint during every rewrite.
3. For each subsection, explicitly include motivation, design, and technical advantage when applicable.
4. When relevant, state system model, workload assumptions, and hardware/software environment before details.
5. Avoid writing style that looks like incremental patching of a naive baseline.
6. Keep terminology stable across the full paper.
7. If a claim cannot be supported by results, weaken or remove the claim.
8. Before finalizing, append and answer a five-dimension self-review question list, then revise the paper based on unresolved items.
9. Do not load all section references at once; load only `references/hpc-terminology.md` and the specific section guide needed for the current edit target.

## Output Contract

When asked to rewrite or draft sections, return:

1. A compact HPC terminology ledger listing canonical workload/platform/parallel-model/execution-entity/metric/baseline terms used in the rewrite.
2. A compact section outline (3-7 bullets).
3. Revised paragraphs with explicit paragraph roles (opening/challenge/system model/method/advantage/evidence/limitation).
4. A short self-review checklist covering clarity, flow, terminology consistency, unsupported claims, scaling evidence, and missing environment details.
5. A claim-evidence map for each major claim in the revised text using `Claim: ... | Evidence: ... | Status: supported/needs evidence`.
6. When relevant, add a compact note on platform assumptions and comparison conditions, avoiding repetitive comparison caveats when the experimental setup already makes them clear.
7. A venue/reviewer-risk note when the target venue or paper type is known.
8. An experiment adequacy note covering baseline fairness, scaling evidence, profiling/causality, and end-to-end evidence.
9. A reproducibility gap note covering missing hardware/software, build, launch, workload, and artifact details.
10. A closest-work risk note when the claim may overlap with prior systems, algorithms, runtimes, or benchmarks.

## Safety and Fallbacks

1. Load only `references/hpc-terminology.md` and the specific section guide needed for the current edit.
2. If a claim is unsupported, weaken it or remove it.
3. If flow remains weak, add temporary headers or transitions during revision, then remove unnecessary scaffolding before finalizing.
4. Prefer concise, reviewer-facing prose over mechanical sentence patching.
