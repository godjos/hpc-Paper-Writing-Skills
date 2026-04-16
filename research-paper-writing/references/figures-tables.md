# HPC Figures and Tables Guide

Use this guide to make figures and tables stand alone. Every figure or table should support one claim and expose the platform, workload, metric, and comparison condition.

## Scaling Plots

For strong and weak scaling figures:

1. Label the x-axis with nodes, GPUs, ranks, or problem size.
2. Label the y-axis with runtime, speedup, throughput, or parallel efficiency.
3. Include the ideal scaling line when it helps interpretation.
4. State the fixed problem size for strong scaling.
5. State the per-node/per-GPU problem-size policy for weak scaling.
6. Mark the scale where efficiency drops and explain the new bottleneck in text.

## Runtime Breakdown Plots

Use breakdown plots to explain causality:

1. Separate compute, communication, synchronization, memory transfer, I/O, and scheduling overhead when relevant.
2. Keep categories consistent across baselines and configurations.
3. Avoid overloading one figure with unrelated metrics.
4. Tie each breakdown category to a method mechanism or bottleneck.

## Roofline and Bandwidth Plots

Use roofline or bandwidth plots when the claim depends on architectural limits:

1. Report arithmetic intensity and achieved performance when using roofline.
2. State peak values and how they were measured or sourced.
3. Use the plot to support a precise claim, such as memory-bound behavior or improved data reuse.
4. Do not use roofline as decoration if the paper does not discuss the implication.

## Timeline and Overlap Figures

Use timeline figures for overlap, pipeline, or synchronization claims:

1. Show ranks, streams, tasks, or pipeline stages on clearly labeled lanes.
2. Use consistent colors for compute, communication, I/O, and wait time.
3. Include enough scale information to interpret latency or overlap.
4. Pair the figure with profiling evidence when claiming reduced stalls.

## System and Mapping Figures

For system overview or architecture figures:

1. Show the data path through CPU, GPU, memory, network, and storage only when relevant.
2. Label rank/thread/task/kernel ownership clearly.
3. Distinguish logical modules from physical hardware resources.
4. Include the bottleneck and the proposed intervention in the figure if possible.

## Table Rules for HPC Results

1. Use metric directions such as `Runtime (s) down`, `Throughput (tasks/s) up`, `Parallel efficiency (%) up`, `Memory (GB) down`, `Energy (J) down`, `Bandwidth (GB/s) up`, or `Performance (TFLOP/s) up`.
2. Include units in column headers.
3. Keep numeric precision consistent within a metric.
4. Group workloads, platforms, or scales with clear headers.
5. Mark best values sparingly and explain whether higher or lower is better.
6. Put platform, problem size, and measurement policy in the caption or table note.

## Caption Template

`[Figure/Table X]: [Metric] for [workload/problem size] on [platform/scale]. [Comparison condition]. [One-sentence takeaway].`

## Misleading Patterns to Avoid

1. Showing speedup without absolute runtime.
2. Cropping axes so marginal gains look large.
3. Mixing strong and weak scaling in one unlabeled plot.
4. Reporting normalized results without the normalization baseline.
5. Omitting failed or non-scaling configurations when they define the method boundary.
