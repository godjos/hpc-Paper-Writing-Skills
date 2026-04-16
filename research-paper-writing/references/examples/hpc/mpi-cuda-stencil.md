# HPC Mini Case: MPI+CUDA Stencil

## Paper Setting

The paper optimizes multi-GPU stencil computation on an MPI+CUDA cluster. The target bottleneck is halo exchange between neighboring ranks, and the target metric is weak-scaling efficiency.

## Terminology Ledger

Workload: stencil computation. Platform: GPU cluster. Execution entities: MPI rank, GPU kernel, CUDA stream. Data movement: halo exchange, host-device transfer, GPU-GPU transfer. Metrics: iteration time, weak-scaling efficiency, exposed communication time.

## Weak Paragraph

Our method improves communication overhead and makes the stencil code scale better on many GPUs.

## Reviewer Concern

The paragraph does not identify the communication source, scale, metric, or mechanism. It also does not distinguish communication volume from exposed communication time.

## Revised Paragraph

The proposed overlap schedule improves weak-scaling efficiency by reducing exposed halo-exchange time. Each MPI rank launches the interior GPU kernel before waiting for boundary data and overlaps this computation with nonblocking halo transfers to neighboring ranks. This mechanism does not reduce the halo volume; instead, it removes part of the communication wait from the iteration critical path. Section X validates the effect with a breakdown of iteration time and a weak-scaling curve up to N GPUs.

## Claim-Evidence Map

Claim: overlap improves weak-scaling efficiency | Evidence: weak-scaling curve | Status: needs figure.
Claim: gain comes from reduced exposed halo-exchange time | Evidence: runtime breakdown or timeline | Status: needs profiling.
