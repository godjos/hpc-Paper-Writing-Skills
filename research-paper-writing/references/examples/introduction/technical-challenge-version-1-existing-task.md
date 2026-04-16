# Technical Challenge Version 1: Existing Workload

1. State the general bottleneck.
2. Summarize traditional methods and their limits.
3. Summarize recent methods and their limits.
4. End with the exact remaining bottleneck.

Terminology anchors:

1. State the bottleneck with a concrete source: all-reduce, halo exchange, NUMA access, cache misses, HBM capacity, PCIe transfer, file-system I/O, scheduling overhead, or load imbalance.
2. Keep execution entities consistent. Do not switch between `MPI rank`, `process`, `thread`, and `worker` unless they mean different things.
3. Name the exact remaining bottleneck that the method solves.
