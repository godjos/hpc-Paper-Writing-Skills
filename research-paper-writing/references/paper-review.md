# Paper Review for HPC Papers

## Goal

Use an adversarial, reviewer-style checklist to detect rejection risks early and revise the paper before submission.

Use `references/hpc-terminology.md`, `references/performance-evidence.md`, `references/reproducibility-artifact.md`, and `references/venue-reviewer-profile.md` during review when relevant.

## Critical Rule

Every major claim, especially in Abstract and Introduction, must be:

1. technically correct,
2. explicitly supported by experimental evidence,
3. expressed with precise terminology for workload, platform, metric, and bottleneck,
4. scoped to the setting actually evaluated.

If a claim is not supported, either add evidence, weaken it, or remove it.

## What Usually Gets a Paper Accepted

1. Clear contribution: new system, runtime, compiler, algorithm, performance model, benchmark finding, or insight.
2. Meaningful improvement over strong baselines under fair comparison settings.
3. Complete evidence: end-to-end results, scaling, ablation, profiling, and limitations.
4. Clear explanation of why the method works and where it stops working.
5. Credible reproducibility and artifact story.

## Reviewer Scorecard

Mark each item as `pass`, `needs revision`, `needs experiment`, or `remove claim`.

| Dimension | Reviewer question | Typical required evidence |
|-----------|-------------------|---------------------------|
| Novelty | What new knowledge does this paper provide? | Closest-work distinction and explicit contribution |
| Technical depth | Is the mechanism nontrivial and well explained? | System/execution model, algorithm, performance rationale |
| Experimental rigor | Are results fair and complete? | Strong baselines, tuning details, repetitions, variability |
| Scalability | Does the method scale under meaningful conditions? | Strong/weak scaling, efficiency, scaling ceiling |
| Causality | Do results explain the source of improvement? | Ablation, profiling, breakdown, roofline, performance model |
| Reproducibility | Could a knowledgeable reader rerun the main results? | Hardware/software, build, launch, workloads, artifact |
| Related work | Would reviewers accept the distinction from closest work? | Closest-work matrix and "why not X" answer |
| Limitations | Are boundaries stated honestly? | Scope, failure cases, unsupported settings |

## Common Rejection Dimensions

| Rejection dimension | Typical failure signals |
|---------------------|-------------------------|
| Insufficient contribution | Targeted failure case is too common; idea is predictable; closest work not addressed |
| Unclear writing | Missing system details; terms change across sections; module motivation is vague |
| Weak empirical effect | Marginal speedup; weak absolute performance; no efficiency or scalability analysis |
| Incomplete evaluation | Missing ablations, important baselines, scaling curves, profiling, or workload diversity |
| Baseline unfairness | Untuned baselines, unclear flags, different hardware budgets, missing affinity/placement |
| Unsupported causality | Speedup reported without explaining communication, memory, synchronization, I/O, or load balance |
| Poor reproducibility | Missing versions, build flags, launch commands, problem sizes, or artifact instructions |
| Problematic design | Unrealistic assumptions; high memory/communication cost; hidden synchronization blowups |

## End-of-Paper Self-Review Questions

### 1. Contribution

1. What new knowledge does this paper give to readers?
2. Is the solved failure case meaningful for the target venue?
3. Is the technical idea non-obvious beyond well-explored practice?
4. Is the gain surprising, explanatory, or useful rather than a predictable tuning result?
5. Is there at least one clear novelty type: system design, runtime design, communication design, scheduling insight, compiler transformation, algorithmic insight, benchmark finding, or performance model?

### 2. Writing Clarity

1. Can a knowledgeable reader reproduce the method from the paper?
2. Did we provide enough technical detail for each key module?
3. Is the motivation of every module tied to a named bottleneck?
4. Are workload names, hardware names, metric names, and execution entities consistent?
5. Does each paragraph carry one clear message with smooth transitions?

### 3. Experimental Strength

1. Are improvements over strong baselines meaningful, not just statistically tiny?
2. Is absolute performance competitive enough for the target venue?
3. Are gains consistent across multiple workloads, scales, or metrics?
4. Do we report both strengths and failure cases honestly?
5. Did we show both scaling and efficiency, not only one of them?
6. Did we separate end-to-end results from kernel-level or microbenchmark results?

### 4. Evaluation Completeness

1. Do we include ablations for all key design choices?
2. Are all strong/recent baselines included, with settings clear enough for readers to judge comparability?
3. Are evaluation metrics standard and sufficient for this task?
4. Are workloads challenging enough to validate real effectiveness?
5. Are comparison and ablation protocols clearly documented?
6. Do we provide strong scaling, weak scaling, and profiling evidence when relevant?
7. Do we report the hardware/software environment well enough for reproduction?

### 5. Method Design Soundness

1. Is the experimental setting realistic for practical use?
2. Does the method have hidden technical defects or unreasonable assumptions?
3. Is the method robust without heavy per-case hyperparameter retuning?
4. Do benefits outweigh added complexity and new limitations?
5. Could reviewers reasonably argue that the net benefit is negative?
6. Does the design avoid hidden communication, memory, synchronization, scheduling, or I/O blowups?

## Reject-Risk Diagnosis

When a draft feels weak, diagnose the most likely rejection reason:

1. Predictable optimization: strengthen the insight, closest-work distinction, or performance model.
2. Weak baseline: add or justify stronger baselines and tuning policy.
3. No scaling story: add strong/weak scaling, efficiency, and scaling-ceiling explanation.
4. Unclear speedup source: add ablation, profiling, breakdown, roofline, or model evidence.
5. Non-reproducible setup: add hardware/software, build, launch, and workload details.
6. Unsupported portability claim: narrow the claim or add platforms/backends.
7. Hidden limitation: state the scope boundary and explain why the contribution remains valuable.

## Adversarial Writing Workflow

1. Read the paper as a skeptical reviewer for the target venue.
2. Answer every scorecard item with explicit evidence from the paper.
3. Mark each item as `pass`, `needs revision`, `needs experiment`, or `remove claim`.
4. Revise claims, writing, experiments, method scope, or limitations accordingly.
5. Repeat until no major rejection risk remains.
