# Pipeline Version 4: Observation Driven

1. Start from a profiling or scaling observation.
2. State the design decision it motivates.
3. Show why the new pipeline matches the observation.

Terminology anchors:

1. Name the observed signal precisely: communication stall time, synchronization wait time, memory bandwidth saturation, cache-miss rate, GPU occupancy, I/O wait, or load imbalance.
2. Pair the observation with the measured condition, such as node count, GPU count, problem size, batch size, or precision.
