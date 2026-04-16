# Module Triad Example: MPI+CUDA Stencil

## Motivation

Multi-GPU stencil codes often lose weak-scaling efficiency because each iteration must exchange boundary cells between neighboring MPI ranks. When subdomains shrink per GPU or the stencil radius grows, halo exchange and synchronization can dominate end-to-end iteration time.

## Design

The communication-aware stencil module assigns each MPI rank one GPU-resident subdomain and maintains separate interior and boundary regions. Each iteration launches an interior GPU kernel first, starts nonblocking halo exchange for boundary cells, and then launches the boundary kernel after the required halos arrive.

## Technical Advantage

This design overlaps interior computation with halo exchange, so communication stall time is hidden when interior work is large enough. The expected evidence is a runtime breakdown showing lower exposed communication time and a weak-scaling curve showing higher parallel efficiency at larger GPU counts.
