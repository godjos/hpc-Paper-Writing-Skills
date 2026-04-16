# HPC Paper Intake Guide

Use this guide before drafting or rewriting a high-level HPC paper. The goal is to identify the paper's story, evidence, risks, and missing inputs before polishing prose.

## Intake Fields

Collect the following fields from the draft, notes, or user prompt:

1. Target venue: SC, HPDC, ICS, PPoPP, IPDPS, CLUSTER, Euro-Par, TPDS, or unknown.
2. Paper type: system, runtime, compiler, parallel algorithm, architecture, application/benchmark, performance modeling, AI-for-HPC, or artifact paper.
3. Workload and domain: simulation, stencil, sparse linear algebra, graph analytics, checkpoint/restart, parallel I/O, scheduling, distributed training, inference, or another workload.
4. Platform and scope: CPU cluster, GPU cluster, heterogeneous nodes, storage system, network/interconnect, runtime/library stack, and tested scale.
5. Bottleneck: communication, synchronization, load imbalance, memory bandwidth, HBM capacity, cache locality, I/O contention, scheduling overhead, kernel launch overhead, or host-device transfer.
6. Core insight: the shortest explanation of why the proposed design should improve the target metric.
7. Contributions: system design, algorithmic idea, runtime policy, compiler transformation, performance model, benchmark finding, or artifact.
8. Evidence packet: end-to-end results, strong/weak scaling, profiling, ablation, roofline, performance model, portability, artifact, and limitations.

## Story Canvas

Fill this compact canvas before writing:

| Field | Required answer |
|-------|-----------------|
| Problem | What workload/system problem matters to the target community? |
| Bottleneck | What exact system-layer bottleneck prevents prior work from scaling or remaining efficient? |
| Insight | What observation or principle makes the proposed approach plausible? |
| Mechanism | What system/module/algorithm realizes the insight? |
| Evidence | Which experiments prove the mechanism improves the bottleneck? |
| Boundary | Where does the method not apply or stop scaling? |

## Evidence Packet Checklist

1. Main result: direct comparison against strong baselines under comparable conditions.
2. Scaling: strong scaling, weak scaling, throughput scaling, or efficiency as appropriate.
3. Causality: profiling, breakdown, ablation, or performance model that explains the gain.
4. Robustness: multiple workloads, problem sizes, platforms, or stress settings when relevant.
5. Practicality: setup cost, memory footprint, energy/cost, portability, and artifact availability when claimed.

## Reviewer-Risk Forecast

Before writing, mark each risk as `low`, `medium`, `high`, or `unknown`.

1. Novelty risk: could reviewers view the work as a predictable optimization?
2. Closest-work risk: is there a system, algorithm, or runtime that appears to solve the same problem?
3. Baseline-fairness risk: are comparison settings, tuning, placement, and hardware budgets comparable?
4. Scaling risk: does the method only work at small scale or stop scaling without explanation?
5. Causality risk: do results show speedup without explaining where the speedup comes from?
6. Reproducibility risk: are hardware/software versions, build flags, launch commands, and workloads missing?
7. Scope risk: are limitations hidden or likely to surprise reviewers?

## Missing-Information Output

If any required field is absent, do not invent it. Return a short `Missing information` list and continue with conservative wording:

1. `needs evidence`: claim requires a result, figure, table, or citation.
2. `needs setup detail`: hardware/software, problem size, placement, or repetition information is missing.
3. `needs scope boundary`: the claim is too broad for the reported evidence.
4. `needs closest-work check`: a strong related system or baseline may be missing.
