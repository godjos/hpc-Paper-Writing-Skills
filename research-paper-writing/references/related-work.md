# Related Work Writing Guide for HPC Papers

## Goal

Position your work against the most relevant lines of research, and make your novelty easy to verify. Related Work should help reviewers answer: "How is this different from the closest systems, algorithms, runtimes, or benchmarks?"

Use `references/hpc-terminology.md` before grouping papers. Related Work should compare mechanisms and assumptions using precise HPC terms, not generic labels such as `optimization`, `resources`, or `performance`.

## Workflow

1. List directly competing and recent baseline papers first.
2. Identify the closest 3-5 works that reviewers are likely to mention.
3. Group literature by technical topic and system layer, not by publication year alone.
4. For each topic, summarize the common paradigm, then the limitation relevant to your bottleneck.
5. End each topic by clarifying your distinction.
6. Preserve canonical names for systems, libraries, algorithms, execution models, and metrics used by the cited work.

## Topic Design

Use 2-4 focused topics, for example:

1. Workload-specific or domain-specific mainstream methods.
2. Parallel algorithms, data decomposition, or numerical methods closest to your core idea.
3. Runtime, scheduling, synchronization, or programming-model work.
4. Communication, memory, locality, or I/O techniques your method builds on.
5. Profiling, autotuning, benchmarking, or performance-modeling techniques that inform your design.

## Closest Work Matrix

Build this matrix before writing Related Work:

| Work | Mechanism | Assumption | Workload | Platform | Metric | Limitation | Our difference |
|------|-----------|------------|----------|----------|--------|------------|----------------|
| System/paper name | How it works | What it assumes | What it evaluates | Hardware/software | What it optimizes | Why it misses our bottleneck | Precise distinction |

Use this matrix to avoid vague distinctions. Prefer `uses synchronous all-reduce on dense gradients` over `has communication overhead`.

## Paragraph Template

1. Topic sentence: define the technical scope of this group.
2. Representative methods: summarize the shared mechanism or assumption.
3. Limitation: name the exact bottleneck or mismatch with your setting.
4. Differentiator: state how your method changes the mechanism, assumption, workload, platform, or metric.

## "Why Not Just Use X?" Template

Use this when a close prior work may look equivalent:

`[X] targets [workload/platform] by [mechanism]. This assumption differs from our setting because [specific workload/platform/metric/bottleneck difference]. As a result, directly applying [X] would still leave [communication/memory/synchronization/load-balance/I/O issue]. Our method instead [specific mechanism], which is evaluated by [evidence].`

## Baseline Inclusion and Exclusion

1. Include baselines that solve the same workload or bottleneck, even if they use a different mechanism.
2. Include strong libraries or production systems when they are the practical default.
3. Explain exclusions when a close method cannot run under the same platform, scale, input, license, or artifact availability.
4. Do not exclude a baseline only because it is hard to tune; describe the tuning policy.
5. Separate algorithmic baselines from system baselines when both matter.

## Do and Don't

1. Do compare mechanisms, assumptions, hardware requirements, scale, and failure modes.
2. Do emphasize the exact gap your method fills.
3. Do not make Related Work a citation dump.
4. Do not hide strongest baselines.
5. Do not blur algorithmic novelty with system-level novelty.
6. Do not claim novelty by renaming a known mechanism.

## Checklist

1. Are all strongest/recent competitors covered?
2. Is each topic connected to your workload, platform, bottleneck, and target metric?
3. Is your difference explained in technical terms, not marketing terms?
4. Is citation coverage complete for all core claims?
5. Did you separate algorithmic baselines, runtime/system baselines, and benchmark/application baselines?
6. Can the closest-work matrix answer a skeptical reviewer who says "this is the same as X"?
