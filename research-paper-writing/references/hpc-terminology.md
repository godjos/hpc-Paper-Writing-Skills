# HPC Terminology Guide

Use this guide before rewriting or drafting HPC/system prose. The goal is not to add jargon; it is to keep domain terms precise, consistent, and reviewer-readable.

## Terminology Ledger

Before editing, extract a compact ledger from the user's draft or notes:

1. Workload and problem: simulation, stencil, sparse matrix, graph analytics, training, inference, checkpointing, I/O, scheduling, or runtime service.
2. Parallel model: MPI, OpenMP, CUDA, HIP, SYCL, OpenACC, pthreads, task runtime, data parallelism, model parallelism, or pipeline parallelism.
3. Execution entity: node, socket, NUMA domain, core, hardware thread, process, MPI rank, OpenMP thread, GPU, SM/CU, warp/wavefront, stream, kernel, task, or request.
4. Memory and data movement: cache, DRAM, HBM, unified memory, shared memory, register file, PCIe, NVLink, InfiniBand, RDMA, host-device transfer, halo exchange, all-reduce, broadcast, gather, scatter, or collective.
5. Performance metric: runtime, latency, tail latency, throughput, makespan, speedup, strong scaling, weak scaling, parallel efficiency, FLOP/s, memory bandwidth, I/O bandwidth, energy, or cost.
6. System assumption: cluster size, node type, accelerator type, interconnect, compiler, runtime, library, dataset, problem size, precision, placement, affinity, batch size, or repetition count.

Keep the ledger visible while rewriting. Preserve canonical names, abbreviations, units, and capitalization unless the user asks for a naming change.

## Rewrite Rules

1. Define a specialized term before reuse, especially if it is paper-specific or overloaded.
2. Keep one canonical name for each entity. Do not alternate between `process`, `rank`, and `worker` unless they mean different things.
3. Use the most precise layer of the system stack. Prefer `MPI rank`, `GPU kernel`, `NUMA domain`, or `host-device transfer` over vague words such as `unit`, `part`, `resource`, or `operation`.
4. Preserve standard HPC metric names. Do not replace `strong scaling`, `weak scaling`, `parallel efficiency`, or `end-to-end runtime` with generic phrases if the exact metric matters.
5. Attach units and conditions to results: `ms`, `s`, `GB/s`, `TFLOP/s`, `nodes`, `GPUs`, `ranks per node`, `threads per rank`, problem size, and precision.
6. Distinguish mechanism from evidence. A mechanism can be `overlapping halo exchange with computation`; evidence can be `reduced communication stall time` or `higher parallel efficiency at 256 GPUs`.
7. Do not invent missing environment details. Mark them as `needs evidence` or ask for them in the self-review checklist.

## Common Terminology Mistakes

1. Calling an MPI rank a thread, or calling an OpenMP thread a process.
2. Saying `GPU memory` when the distinction between HBM, device global memory, shared memory, and unified memory matters.
3. Saying `communication overhead` without naming the source: collective, point-to-point, halo exchange, parameter synchronization, PCIe transfer, or file-system I/O.
4. Saying `scalability improves` without specifying strong scaling, weak scaling, throughput scaling, or efficiency.
5. Saying `performance improves` without naming the metric and measurement condition.
6. Mixing `latency`, `runtime`, `throughput`, and `makespan` as if they are interchangeable.
7. Using `distributed`, `parallel`, and `concurrent` interchangeably.
8. Replacing established system names, library names, or algorithm names with paraphrases that make citations hard to follow.

## Final Terminology Pass

Before final output, check:

1. Are workload, platform, bottleneck, method modules, metrics, and baselines named consistently?
2. Are all abbreviations expanded on first use when needed?
3. Are terms tied to the correct system layer?
4. Are numeric claims paired with units and experimental conditions?
5. Are unsupported or unknown details explicitly marked instead of guessed?
