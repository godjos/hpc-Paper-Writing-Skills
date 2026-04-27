# HPC Prose Polish Guide

Use this guide as the final language pass after structure, terminology, and evidence have been checked. The goal is reviewer-facing HPC prose: precise, fluent, concrete, and measured.

## Polish Pass

For each revised paragraph, run this pass before final output:

1. Identify the paragraph role: motivation, bottleneck, system model, method, mechanism, evidence, limitation, or transition.
2. Check whether the first sentence states that role clearly.
3. Replace vague academic phrasing with concrete HPC language.
4. Keep the sentence subject stable when possible: workload, bottleneck, system, module, mechanism, metric, or evidence.
5. Use cause, contrast, consequence, or refinement links between adjacent sentences.
6. Remove filler that does not change the technical claim.
7. Check that every performance statement names the metric, unit, scale, and condition when available.
8. Keep claims measured. Do not use stronger wording than the evidence supports.

## HPC Style Targets

Prefer prose that sounds like a systems/HPC paper:

1. Name the system layer precisely: algorithm, runtime, compiler, memory hierarchy, network, storage, scheduler, or application.
2. Name the execution entity precisely: node, socket, NUMA domain, core, MPI rank, OpenMP thread, GPU kernel, task, stream, request, or I/O process.
3. Name the measured quantity precisely: end-to-end runtime, kernel time, communication volume, message count, memory bandwidth, I/O bandwidth, speedup, strong scaling, weak scaling, or parallel efficiency.
4. Explain mechanism before result when the paragraph argues why the result should hold.
5. Explain result conditions before generalizing: workload, problem size, node/GPU count, baseline, backend, and precision.
6. Use restrained verbs such as `reduces`, `improves`, `overlaps`, `amortizes`, `bounds`, `exposes`, `preserves`, `scales`, and `degrades`.
7. Avoid marketing verbs such as `revolutionizes`, `greatly enhances`, `dramatically boosts`, or `fully solves` unless the evidence is unusually strong.

## Common Non-HPC Phrasing to Fix

Replace vague phrasing with technical phrasing:

1. `improves performance` -> name the metric, such as `reduces end-to-end runtime` or `improves weak-scaling efficiency`.
2. `uses resources efficiently` -> name the resource, such as `reduces HBM traffic`, `improves SM occupancy`, or `reduces MPI message count`.
3. `handles large-scale data` -> name the scale, data structure, and movement path.
4. `communication overhead` -> name the source, such as `halo exchange`, `all-reduce latency`, `RDMA transfer time`, or `metadata operations`.
5. `our method is scalable` -> name strong scaling, weak scaling, throughput scaling, or parallel efficiency, and state the evaluated scale.
6. `significant improvement` -> report the measured improvement and condition, or weaken to `improvement` when evidence is incomplete.
7. `advanced optimization` -> name the mechanism, such as tiling, fusion, overlap, aggregation, prefetching, placement, or scheduling.

## Sentence-Level Flow

Check each sentence pair:

1. Cause: Does sentence B explain why sentence A happens?
2. Contrast: Does sentence B clarify a limitation or difference?
3. Consequence: Does sentence B state the impact of sentence A?
4. Refinement: Does sentence B make sentence A more precise?
5. Evidence: Does sentence B support sentence A with measurement, setup, or observation?

If none applies, revise the transition or split the paragraph.

## Final Language Gate

Before final output, confirm:

1. The paragraph can be read aloud without awkward phrase stacking.
2. The main nouns stay consistent across the paragraph.
3. Generic words such as `performance`, `resources`, `method`, `data`, `system`, and `optimization` are replaced when a precise HPC term is available.
4. Claims are not inflated beyond the evidence.
5. Sentences are varied but not ornamental.
6. The text reads like a careful HPC/system paper, not a general technical blog post.

## Final Language Rubric

Before returning revised prose, score every revised paragraph as `pass` or `revise`.

Use this compact format:

`P1 | role: motivation | verdict: pass | reason: clear bottleneck, precise workload term, smooth cause/effect transition`

`P2 | role: evidence | verdict: revise | reason: performance claim lacks scale and metric condition`

A paragraph can receive `pass` only if all of the following are true:

1. The first sentence states the paragraph role or message.
2. The paragraph has one main message.
3. Adjacent sentences are connected by cause, contrast, consequence, refinement, or evidence.
4. Specialized HPC terms match the terminology ledger and the correct system layer.
5. Generic words are replaced where precise HPC terms are available.
6. Performance claims include metric, unit, scale, and condition when the source draft provides them.
7. Claims are measured and do not exceed the available evidence.
8. The paragraph reads fluently without awkward phrase stacking.

Mark the paragraph as `revise` if any condition fails. For every `revise`, either fix the paragraph before final output or explicitly state the missing input that prevents a pass, such as `needs scale`, `needs baseline`, `needs hardware detail`, or `needs evidence`.

Final output should not contain unresolved `revise` verdicts unless the user has not provided the missing evidence or setup detail needed to resolve them.
