# Reproducibility and Artifact Guide for HPC Papers

Use this guide to make experimental setup, artifact claims, and reproducibility notes reviewer-readable. Do not invent missing setup details; mark them as `needs setup detail`.

## Hardware Environment Table

Report the hardware at the level needed to reproduce the claim:

| Item | Details to report |
|------|-------------------|
| Cluster | Site/system name if allowed, node count, queue/partition |
| CPU | Model, sockets per node, cores per socket, SMT setting |
| GPU/accelerator | Model, count per node, HBM/device memory |
| Memory | DRAM capacity, memory channels if relevant |
| Network | Interconnect, bandwidth, topology if relevant |
| Storage | File system, local SSD/NVMe, burst buffer if relevant |
| Power/energy | Measurement device, API, sampling rate if claimed |

## Software Environment Table

Report software versions and settings:

1. Operating system and kernel.
2. Compiler and flags.
3. MPI implementation and version.
4. OpenMP runtime, CUDA/HIP/SYCL/OpenACC toolkit version, or task runtime.
5. Math, communication, storage, or domain libraries.
6. Container image, module list, or environment file when available.
7. Commit hash or release version of the artifact.

## Build and Launch Details

Include enough information for a knowledgeable reader to rerun the experiment:

1. Build commands and compile flags.
2. Runtime environment variables.
3. Job scheduler script or launch command.
4. Rank/thread/task/GPU mapping.
5. NUMA and affinity policy.
6. Problem size, precision, input data, and batch size.
7. Warm-up, repetition count, and aggregation policy.

## Workload and Data Disclosure

1. Name each benchmark, miniapp, application, dataset, or synthetic generator.
2. State whether inputs are public, generated, proprietary, or restricted.
3. Report problem sizes and scaling policy for strong and weak scaling.
4. State preprocessing, initialization, and checkpoint/restart behavior when it affects timing.
5. Separate setup time, preprocessing time, I/O time, and steady-state runtime when relevant.

## Artifact Packaging Checklist

1. Source code or binary availability.
2. Build instructions and dependencies.
3. Minimal test case for a laptop or single node when possible.
4. Full-scale reproduction instructions for the main figures.
5. Expected runtime and required resources.
6. Scripts to generate figures/tables from raw data.
7. Raw data or logs for submitted figures.
8. Known portability limits and expected deviations.

## Reproducibility Note Template

Use a compact paragraph when space is limited:

`We evaluate [system] on [hardware] using [software stack]. Each result reports [median/mean] over [N] runs after [warm-up policy]. We launch [ranks/threads/GPUs] with [placement/affinity policy] and use [problem sizes/scaling policy]. The artifact includes [code/scripts/data] for reproducing [main figures], with known limits on [platform/scope].`

## Red Flags

1. Hardware generations are named but software versions are missing.
2. Speedups are reported without compiler flags or baseline tuning.
3. Scaling curves omit rank/thread/GPU mapping.
4. I/O or preprocessing is excluded without saying so.
5. Artifact claims exist but no build, launch, or expected-runtime information is given.
