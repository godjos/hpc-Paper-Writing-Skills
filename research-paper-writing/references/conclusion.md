# Conclusion Writing Guide for HPC Papers

## Goal

Close the paper with clear takeaways and credible limitations.

Use `references/hpc-terminology.md` for the final terminology pass. The conclusion should restate the same workload, bottleneck, metric, platform, and limitation terms used in the Abstract and Introduction.

## Structure

1. Restate the workload/system problem and core technical idea.
2. Summarize strongest evidence from experiments.
3. State practical impact or new insight.
4. Add limitation paragraph.
5. End with concrete future direction.
6. Keep specialized terms and metric names consistent with the rest of the paper.

## Limitation Guidance

Prefer limitations tied to task goal/setting boundaries, for example:

1. Scale limitation (e.g., only up to a certain node count or problem size).
2. Platform limitation (e.g., only tested on a specific hardware generation or interconnect).
3. Deployment scope limitation (e.g., only one runtime backend or one communication library).

Avoid framing conclusion around fixable implementation flaws unless they critically define your method's scope.

## Distinguish Limitation Types

1. Technical defect: underperforms strong baselines on key metrics or causes unacceptable tradeoff.
2. Scope limitation: bounded by current task setting and still competitive vs. current SOTA.

## Template

1. This paper addresses [workload/system problem] by proposing [method].
2. The key idea is [core insight], which enables [main benefit].
3. Experiments show [main gains] across [datasets/settings/hardware platforms].
4. A current limitation is [scope boundary], and extending to [future setting] is an important next step.
