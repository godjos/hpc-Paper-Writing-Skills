# Annotated System Overview Example: Halo Exchange

Use this pattern to turn a system overview figure into reviewer-readable Method prose.

## Figure Walkthrough

Figure X shows one iteration of the distributed stencil pipeline. Each MPI rank owns one GPU-resident subdomain, splits the subdomain into interior and boundary regions, and exchanges boundary cells with neighboring ranks through nonblocking point-to-point messages.

## Module Order

1. The partitioning stage maps the global grid to per-rank GPU subdomains.
2. The interior-compute stage launches a GPU kernel that does not depend on remote halo data.
3. The exchange stage packs boundary cells and starts nonblocking halo transfers.
4. The boundary-compute stage waits only for the required halos and updates boundary cells.

## Bottleneck Link

The figure should make the overlap opportunity visible: interior computation runs while halo exchange is in flight. The corresponding experiment should report exposed communication time, total iteration time, and weak-scaling efficiency.
