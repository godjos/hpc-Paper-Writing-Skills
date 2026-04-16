# Venue and Reviewer Profile Guide

Use this guide to tune writing emphasis and self-review for the target HPC venue. Venue expectations vary, but all high-level venues require precise claims, fair comparisons, and reproducible evidence.

## SC-Style Reviewer Profile

Likely questions:

1. Is the contribution significant at leadership-class or large cluster scale?
2. Are the baselines strong, tuned, and fairly compared?
3. Does the paper explain the source of performance gains?
4. Is the artifact or reproducibility story credible?

Required evidence:

1. End-to-end results on meaningful workloads.
2. Strong/weak scaling with efficiency.
3. Profiling, breakdown, or performance model.
4. Clear hardware/software disclosure.

## HPDC-Style Reviewer Profile

Likely questions:

1. Does the system matter for distributed HPC/cloud-HPC operation?
2. Is the scheduling, resource-management, data-movement, or runtime problem realistic?
3. Does the method handle heterogeneity, contention, or failures if claimed?

Required evidence:

1. Multi-node experiments and workload diversity.
2. Resource utilization, latency/throughput, and contention analysis when relevant.
3. Comparison against distributed system or runtime baselines.

## ICS-Style Reviewer Profile

Likely questions:

1. Is there a clear architecture, compiler, or runtime insight?
2. Does the paper connect performance to hardware behavior?
3. Are memory hierarchy, locality, vectorization, or communication effects explained?

Required evidence:

1. Microarchitectural counters, roofline, or bandwidth analysis when relevant.
2. Compiler/runtime configuration and hardware details.
3. Ablations tied to architectural mechanisms.

## PPoPP-Style Reviewer Profile

Likely questions:

1. Is the parallel programming, synchronization, task, or runtime contribution technically deep?
2. Are correctness, semantics, and programming model assumptions clear?
3. Does the evaluation show practical benefit beyond toy workloads?

Required evidence:

1. Clear execution and synchronization model.
2. Correctness or semantic argument when applicable.
3. Runtime overhead and scalability evidence.

## IPDPS / CLUSTER / Euro-Par-Style Reviewer Profile

Likely questions:

1. Does the parallel algorithm or system scale across realistic cluster settings?
2. Are workloads representative and problem sizes meaningful?
3. Is the comparison practical and reproducible?

Required evidence:

1. Scaling results with clear problem-size policy.
2. Cluster configuration and launch details.
3. Comparison to strong algorithms, libraries, or systems.

## TPDS-Style Reviewer Profile

Likely questions:

1. Is the work complete enough for long-form archival publication?
2. Are limitations, assumptions, and related work treated thoroughly?
3. Are experiments broad and carefully explained?

Required evidence:

1. Complete method and system model.
2. Broad evaluation with robustness and sensitivity.
3. Detailed related work and threat-to-validity discussion.

## Venue-Risk Note Template

`Venue risk: For [venue], reviewers will likely focus on [risk 1], [risk 2], and [risk 3]. The draft currently supports [claim] with [evidence], but still needs [missing evidence/details] to reduce rejection risk.`
