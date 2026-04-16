# Introduction Version 4: Open With Challenge

1. Start with importance of the workload.
2. Briefly summarize how prior methods work.
3. Expose the bottleneck immediately.
4. Explain why the bottleneck persists.

Terminology anchors:

1. Name the failure case at the system layer: collective synchronization, load imbalance, memory bandwidth saturation, I/O contention, kernel launch overhead, or host-device transfer.
2. Pair the failure with a metric and condition, such as lower parallel efficiency at high node counts or higher tail latency under bursty requests.
