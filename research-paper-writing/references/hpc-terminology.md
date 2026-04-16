# HPC Terminology Guide

Use this guide before rewriting or drafting HPC/system prose. The goal is not to add jargon; it is to keep domain terms precise, consistent, and reviewer-readable.

## Terminology Ledger

Before editing, extract a compact ledger from the user's draft or notes:

1. Workload and problem: simulation, stencil, sparse matrix/vector operations, graph analytics, N-body, CFD, molecular dynamics, checkpoint/restart, parallel I/O, scheduling, runtime service, distributed training, inference, or benchmark/miniapp.
2. System layer: algorithm, runtime, compiler, programming model, library, architecture, memory hierarchy, network/interconnect, storage, scheduler, or application.
3. Parallel model: MPI, OpenMP, CUDA, HIP, SYCL, OpenACC, pthreads, task runtime, data parallelism, model parallelism, pipeline parallelism, or hybrid MPI+X.
4. Execution entity: node, socket, NUMA domain, core, hardware thread, process, MPI rank, OpenMP thread, GPU, SM/CU, warp/wavefront, stream, kernel, task, request, or I/O process.
5. Memory and data movement: cache, DRAM, HBM, device global memory, unified memory, shared memory, register file, PCIe, NVLink, InfiniBand, RDMA, host-device transfer, GPU-GPU transfer, halo exchange, all-reduce, broadcast, gather, scatter, collective, checkpoint, or file-system I/O.
6. Performance metric: runtime, latency, tail latency, throughput, makespan, speedup, strong scaling, weak scaling, parallel efficiency, FLOP/s, memory bandwidth, I/O bandwidth, communication volume, message count, energy, node-hours, or cost.
7. System assumption: cluster size, node type, accelerator type, interconnect, compiler, runtime, library, dataset, problem size, precision, placement, affinity, batch size, warm-up, repetition count, or normalization policy.

Keep the ledger visible while rewriting. Preserve canonical names, abbreviations, units, and capitalization unless the user asks for a naming change.

## Rewrite Rules

1. Define a specialized term before reuse, especially if it is paper-specific or overloaded.
2. Keep one canonical name for each entity. Do not alternate between `process`, `rank`, `thread`, `task`, and `worker` unless they mean different things.
3. Use the most precise layer of the system stack. Prefer `MPI rank`, `GPU kernel`, `NUMA domain`, `all-reduce`, or `host-device transfer` over vague words such as `unit`, `part`, `resource`, or `operation`.
4. Preserve standard HPC metric names. Do not replace `strong scaling`, `weak scaling`, `parallel efficiency`, `communication volume`, or `end-to-end runtime` with generic phrases if the exact metric matters.
5. Attach units and conditions to results: `ms`, `s`, `GB/s`, `GiB`, `TFLOP/s`, `nodes`, `GPUs`, `ranks per node`, `threads per rank`, problem size, precision, and backend.
6. Distinguish mechanism from evidence. A mechanism can be `overlapping halo exchange with computation`; evidence can be `reduced communication stall time` or `higher parallel efficiency at 256 GPUs`.
7. Do not invent missing environment details. Mark them as `needs evidence` or `needs setup detail`.

## System-Layer Precision

Use system-layer terms consistently:

1. Algorithm layer: decomposition, tiling, partitioning, complexity, convergence, data dependence.
2. Runtime layer: scheduling, task queue, work stealing, progress engine, synchronization, load balance.
3. Compiler layer: code generation, vectorization, fusion, layout transformation, autotuning.
4. Architecture layer: socket, NUMA domain, core, SM/CU, cache, HBM, memory bandwidth, interconnect.
5. Network layer: collective, point-to-point, RDMA, topology, bisection bandwidth, message latency.
6. Storage layer: parallel file system, checkpoint, burst buffer, metadata, I/O bandwidth, write amplification.
7. Evaluation layer: baseline, workload, metric, scale, normalization, repetition, variance.

## Common Terminology Mistakes

1. Calling an MPI rank a thread, or calling an OpenMP thread a process.
2. Saying `GPU memory` when the distinction between HBM, device global memory, shared memory, registers, and unified memory matters.
3. Saying `communication overhead` without naming the source: collective, point-to-point, halo exchange, parameter synchronization, PCIe transfer, RDMA path, or file-system I/O.
4. Saying `scalability improves` without specifying strong scaling, weak scaling, throughput scaling, or parallel efficiency.
5. Saying `performance improves` without naming the metric and measurement condition.
6. Mixing `latency`, `runtime`, `throughput`, and `makespan` as if they are interchangeable.
7. Mixing `bandwidth`, `throughput`, and `FLOP/s` without stating what is measured.
8. Mixing `communication volume` and `communication time`; volume can fall while time remains dominated by latency or synchronization.
9. Treating `GPU occupancy` as equivalent to `GPU utilization`; occupancy is a scheduling/resource metric, not a direct performance metric.
10. Using `distributed`, `parallel`, and `concurrent` interchangeably.
11. Claiming `portable` when evidence only covers one architecture, compiler, or backend.
12. Replacing established system names, library names, or algorithm names with paraphrases that make citations hard to follow.

## Final Terminology Pass

Before final output, check:

1. Are workload, platform, bottleneck, method modules, metrics, and baselines named consistently?
2. Are all abbreviations expanded on first use when needed?
3. Are terms tied to the correct system layer?
4. Are numeric claims paired with units and experimental conditions?
5. Are speedup, efficiency, bandwidth, throughput, and scalability claims distinguished?
6. Are unsupported or unknown details explicitly marked instead of guessed?
