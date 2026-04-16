# Module Design Example: Communication Overlap

## Design Backbone

Given a rank-local partition, the runtime first classifies work items into communication-independent and communication-dependent sets. It schedules communication-independent work immediately, starts nonblocking communication for remote dependencies, and then schedules dependent work once the required messages complete.

## Execution Entities

The MPI rank owns the partition and communication buffers. CPU threads or runtime tasks prepare message buffers and poll completion. GPU kernels process local work and boundary work in separate launches or streams.

## Performance Rationale

The module does not reduce communication volume by itself. Its advantage is reducing exposed communication time by moving independent compute onto the critical path while communication progresses. The correct evidence is a timeline, runtime breakdown, or ablation that disables overlap.
