# Performance Evidence Guide for HPC Papers

Use this guide to match every major performance claim to the right kind of evidence. A high-level HPC paper should not only report that something is faster; it should explain why the gain occurs, where it holds, and where it stops.

## Claim Types and Required Evidence

| Claim type | Minimum evidence | Stronger evidence |
|------------|------------------|-------------------|
| Speedup | End-to-end runtime against strong baselines | Runtime breakdown plus ablation |
| Strong scaling | Runtime or speedup across fixed-size runs | Parallel efficiency and scaling ceiling analysis |
| Weak scaling | Runtime/throughput across proportional problem sizes | Efficiency plus communication/memory breakdown |
| Throughput | Requests, iterations, samples, or tasks per second | Latency/tail latency and resource utilization |
| Memory reduction | Peak memory footprint under same workload | Breakdown by data structure or buffer |
| Communication reduction | Communication volume or time | Per-collective/per-link breakdown and overlap analysis |
| Energy/cost efficiency | Energy, power, dollar cost, or node-hours | Same-quality comparison and utilization analysis |
| Portability | Results on more than one platform or backend | Explanation of platform-specific assumptions |

## Claim-Evidence Map

For each major claim, produce one row:

| Claim | Metric | Evidence source | Conditions | Status |
|-------|--------|-----------------|------------|--------|
| What is claimed? | Runtime, GB/s, TFLOP/s, efficiency, etc. | Figure/table/profiling/model | Platform, scale, workload, precision | supported / needs evidence / weaken |

Use `weaken` when evidence supports only a narrower version of the claim. For example, change `improves scalability` to `improves weak-scaling efficiency up to 128 GPUs on the tested stencil workloads`.

## Evidence Hierarchy

1. End-to-end results: prove user-visible value.
2. Scaling curves: prove behavior as nodes, GPUs, ranks, or problem size changes.
3. Ablation: proves which module/design choice causes the gain.
4. Profiling and breakdowns: explain compute, communication, memory, I/O, and synchronization costs.
5. Performance model or roofline: connects the mechanism to architectural limits.
6. Microbenchmarks: useful only as supporting evidence, not as the main proof of system value.

## Causality Checks

Before accepting a performance claim, ask:

1. Does the paper show where the time, memory, or communication was saved?
2. Is the gain still visible in end-to-end runs, not only in a kernel or microbenchmark?
3. Does an ablation isolate the proposed design from baseline tuning?
4. Do profiling results match the claimed bottleneck?
5. Does the scaling curve reveal the new bottleneck after the proposed fix?

## Common Bad Patterns

1. Reporting speedup without baseline tuning details.
2. Showing only kernel-level improvement while claiming end-to-end system improvement.
3. Reporting strong scaling without parallel efficiency.
4. Reporting weak scaling without problem-size policy.
5. Claiming communication reduction without separating communication volume from communication time.
6. Claiming portability from one hardware generation or one backend.
7. Claiming energy efficiency without describing the measurement method.

## Safe Claim Weakening

When evidence is incomplete, prefer precise conservative claims:

1. `reduces end-to-end runtime on the evaluated workloads` instead of `accelerates HPC applications`.
2. `improves weak-scaling efficiency up to N GPUs` instead of `scales well`.
3. `reduces measured all-reduce time` instead of `eliminates communication overhead`.
4. `shows portability across the tested CPU and GPU backends` instead of `is portable`.
