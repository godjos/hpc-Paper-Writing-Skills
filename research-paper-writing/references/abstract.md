# Abstract Writing Guide for HPC Papers

## Goal

Write a strong HPC abstract by doing three things repeatedly:

1. Think through the abstract logic first.
2. Follow one template (Version 1/2/3 below).
3. Revise the abstract many times.

## Pre-Writing Questions (Important)

Answer these before writing:

1. What workload or system setting do we study?
2. What performance bottleneck or scalability bottleneck do we solve, and why is there no satisfactory solution yet? (important)
3. What is our technical contribution?
4. Why can our method work in essence?
5. What measurable advantage do we provide: runtime, throughput, latency, memory, energy, or scalability? (important)

## Version 1: Bottleneck -> Contribution

Introduce the bottleneck, then use one to two sentences to present the technical contribution that solves the bottleneck.

### Structure

1. Workload/system setting.
2. Technical bottleneck for previous methods.
3. One to two sentences introducing the technical contribution for solving the bottleneck.
4. Benefits of the technical contribution.
5. Experiment summary.

### Expert Notes

1. Discuss previous work around the bottleneck that we actually solve.
2. Mention the system idea or method name only if it is easy to understand on first pass.
3. Keep one or two performance targets explicit, such as speedup, efficiency, or memory reduction.
4. The reader should immediately understand what got faster, cheaper, or more scalable.

Version 1 local cite:

1. `references/examples/abstract/template-a.md`

## Version 2: Bottleneck -> Insight -> Contribution

Introduce the bottleneck, then use one to two sentences to present the insight for solving the bottleneck, and then one sentence to present the technical contribution that implements this insight.

### Structure

1. Workload/system setting.
2. Technical bottleneck for previous methods.
3. One sentence introducing the insight for solving the bottleneck.
4. One to two sentences introducing the technical contribution that implements this insight.
5. Benefits of technical novelty.
6. Experiment summary.

### Expert Notes

1. Discuss previous work around the bottleneck that we actually solve.
2. Introduce the insight in one clear sentence.
3. For the implementation sentence(s), usually mention the technical term/name only; do not explain every detailed step.
4. The technical term must be easy to understand; do not create a jump in reading.
5. Keep the improvement metric explicit so the contribution feels measurable, not abstract.

Version 2 local cite:

1. `references/examples/abstract/template-b.md`

## Version 3: Multiple Contributions

Version 3: When there are multiple technical contributions, describe each contribution together with its technical advantage and the metric it improves.

### Structure

1. Workload/system setting.
2. If needed, one contrast sentence about prior methods.
3. Contribution sentence 1 + technical advantage + metric.
4. Contribution sentence 2 + technical advantage + metric.
5. Contribution sentence 3 + technical advantage + metric.
6. Experiment summary.

### Expert Notes

1. When there are multiple technical contributions, describe each contribution together with its technical advantage.
2. Prefer a compact list of concrete gains over a vague broad claim.
3. The ability to express "contribution + advantage" in one sentence is very important for writing a good abstract.

Version 3 local cite:

1. `references/examples/abstract/template-c.md`

## Example Bank

1. `references/examples/abstract-examples.md`
2. `references/examples/abstract/template-a.md`
3. `references/examples/abstract/template-b.md`
4. `references/examples/abstract/template-c.md`

## Abstract Quality Checklist

1. Can a reader identify workload, bottleneck, insight/contribution, and results in one pass?
2. Are all major claims supported by experiments?
3. Are scaling, throughput, latency, memory, or energy claims tied to concrete numbers?
4. Are hardware/software assumptions clear enough for an HPC reviewer?
5. Is there any sentence that mixes too many messages?
