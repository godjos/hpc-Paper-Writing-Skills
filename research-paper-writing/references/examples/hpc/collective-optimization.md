# HPC Mini Case: Collective Optimization

## Paper Setting

The paper optimizes distributed aggregation dominated by all-reduce. The target bottleneck is synchronization and network contention at high rank counts, and the target metrics are all-reduce time and end-to-end iteration time.

## Terminology Ledger

Workload: distributed aggregation. Platform: multi-node cluster. Execution entities: MPI rank, node, NIC. Data movement: all-reduce, inter-node traffic, intra-node reduction. Metrics: collective latency, communication time, iteration time, parallel efficiency.

## Weak Paragraph

Our collective optimization reduces communication and improves training throughput.

## Reviewer Concern

The paragraph mixes communication volume and time, does not name the collective, and claims throughput without end-to-end evidence.

## Revised Paragraph

The hierarchical aggregation module reduces exposed all-reduce time by separating intra-node reduction from inter-node exchange. Each node first combines rank-local buffers within shared memory and then participates in a smaller inter-node all-reduce, reducing network contention at large rank counts. The paper should validate this claim with all-reduce timing, end-to-end iteration time, and an ablation against the default MPI collective.

## Claim-Evidence Map

Claim: hierarchy reduces exposed all-reduce time | Evidence: collective timing by rank count | Status: needs evidence.
Claim: hierarchy improves end-to-end throughput | Evidence: iteration throughput with default MPI baseline | Status: needs evidence.
