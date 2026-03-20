# Related Work Writing Guide for HPC Papers

## Goal

Position your work against the most relevant lines of research, and make your novelty easy to verify.

## Workflow

1. List directly competing and recent baseline papers first.
2. Group literature by technical topic and system layer, not by publication year alone.
3. For each topic: summarize common paradigm, then key limitation relevant to your bottleneck.
4. End each topic by clarifying your distinction.

## Topic Design

Use 2-4 focused topics, for example:

1. Workload-specific or domain-specific mainstream methods.
2. Parallelization, scheduling, or runtime methods closest to your core idea.
3. Communication, memory, or locality techniques your method builds on.
4. Profiling, autotuning, or benchmarking techniques that inform your design.

## Paragraph Template

1. Topic sentence: define scope of this topic.
2. Representative methods: one compact summary.
3. Limitation tied to your target technical bottleneck.
4. Transition sentence that leads to your method.

## Do and Don't

1. Do compare mechanisms, assumptions, hardware requirements, and failure modes.
2. Do emphasize the exact gap your method fills.
3. Do not make Related Work a citation dump.
4. Do not hide strongest baselines.
5. Do not blur algorithmic novelty with system-level novelty.

## Checklist

1. Are all strongest/recent competitors covered?
2. Is each topic connected to your workload, platform, and bottleneck?
3. Is your difference explained in technical terms, not marketing terms?
4. Is citation coverage complete for all core claims?
5. Did you separate algorithmic baselines from system baselines when both matter?
