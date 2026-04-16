# HPC Mini Case: NUMA-Aware Task Runtime

## Paper Setting

The paper improves a shared-memory task runtime on multi-socket CPU nodes. The target bottleneck is remote NUMA access and load imbalance, and the target metrics are throughput, runtime, memory bandwidth, and remote-access rate.

## Terminology Ledger

Workload: task-parallel application. Platform: multi-socket CPU node. Execution entities: task, worker thread, NUMA domain. Memory terms: local DRAM, remote NUMA access, task queue. Metrics: task throughput, runtime, remote-access rate, memory bandwidth.

## Weak Paragraph

The scheduler improves locality and balances work.

## Reviewer Concern

The paragraph claims two benefits but does not explain the policy or how locality and balance are measured.

## Revised Paragraph

The NUMA-aware scheduler improves locality by assigning newly spawned tasks to queues in the NUMA domain that owns their input data. Worker threads first consume local tasks and steal remotely only when local queues are empty, which preserves locality while bounding load imbalance. The evaluation should report runtime, remote NUMA access rate, memory bandwidth, and a steal-rate ablation against locality-agnostic work stealing.

## Claim-Evidence Map

Claim: scheduler reduces remote NUMA access | Evidence: hardware counter or memory profiling | Status: needs profiling.
Claim: scheduler preserves load balance | Evidence: steal-rate and per-worker utilization | Status: needs evidence.
