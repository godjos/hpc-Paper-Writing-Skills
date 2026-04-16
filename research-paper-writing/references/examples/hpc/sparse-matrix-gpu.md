# HPC Mini Case: Sparse Matrix on GPU

## Paper Setting

The paper accelerates sparse matrix-vector multiplication on GPUs with irregular row lengths. The target bottleneck is load imbalance and uncoalesced memory access, and the target metrics are runtime, memory bandwidth, and end-to-end solver time.

## Terminology Ledger

Workload: SpMV inside an iterative solver. Platform: GPU. Execution entities: thread block, warp, GPU kernel. Memory terms: CSR, row partition, HBM bandwidth, coalesced access. Metrics: kernel runtime, achieved GB/s, solver iteration time.

## Weak Paragraph

The new sparse format is faster because it has better memory behavior.

## Reviewer Concern

The paragraph does not say which memory behavior improves, how irregular rows are handled, or whether the gain affects the full solver.

## Revised Paragraph

The new row-bucketed sparse format targets warp-level load imbalance in CSR SpMV. Rows are grouped by nonzero count so that each warp processes rows with similar work, which reduces inactive lanes and improves coalesced HBM access. Because format conversion can dominate short runs, the evaluation reports both standalone SpMV bandwidth and end-to-end solver time with conversion included.

## Claim-Evidence Map

Claim: row bucketing reduces warp-level imbalance | Evidence: occupancy/lane-utilization or runtime breakdown | Status: needs profiling.
Claim: improvement matters end-to-end | Evidence: solver runtime including conversion | Status: needs figure/table.
