---
name: research-paper-writing
description: Improve HPC and system paper writing quality with clear section structure, scalability logic, reproducibility, and reviewer-facing presentation. Use when drafting or revising Abstract, Introduction, Related Work, Method, Experiments, or Conclusion; polishing figures/tables; checking claim-support alignment; or performing self-review before submission.
---
# HPC Paper Writing

## Overview

Use this skill to rewrite an HPC or systems paper into a reviewer-friendly, high-clarity draft.
Prioritize first-impression quality, system scope clarity, logical flow, scalability evidence, and reproducible claims.

## Core Workflow

1. Clarify the paper story before sentence-level edits: workload, platform, bottleneck, and target metric.
2. Use section-specific guidance in `references/`.
3. Rewrite paragraph-by-paragraph with one message per paragraph.
4. Run reverse outlining after writing each section.
5. Check every major claim in Abstract/Introduction against scaling, profiling, and end-to-end evidence.
6. Run final-paper adversarial review with `references/paper-review.md`.

## Global Principles

1. Keep one paragraph for one message only.
2. State the paragraph message in the first sentence.
3. Make nouns self-contained; define workload names, hardware terms, and runtime terms before reusing them.
4. Maintain sentence-to-sentence flow (cause, contrast, consequence, or refinement).
5. Iterate with adversarial self-review: read as a skeptical reviewer.
6. Treat visual quality as core content, not decoration.
7. Use a clean system overview figure, pipeline figure, and if useful a profiling figure.
8. Use readable, minimal-ink tables.
9. Keep formatting consistent and tidy.
10. State performance units, platform assumptions, and fairness protocol explicitly.

## Paragraph Clarity Check (Important)

Use this quick test whenever the user asks whether a paragraph "flows" or is clear.

1. Read as an external reader:
   - Does this paragraph have one explicit message?
   - Does the first sentence state what this paragraph will do?
   - Are all key nouns/terms readable without hidden context?
   - Does each sentence connect to the previous one with a clear relation (cause, contrast, consequence, refinement, example)?
2. Run reverse outlining for the current section:
   - Write down thesis/main claim.
   - Write down each paragraph topic sentence.
   - Write down the evidence/explanation points under each paragraph.
   - Check mapping: topic sentence -> thesis, and evidence -> topic sentence.
   - Revise or remove any paragraph that cannot be mapped cleanly.
3. If flow is still weak, add temporary section headers and explicit transition phrases during revision, then remove unnecessary headers before finalizing.

Source reference for this check:

- `references/does-my-writing-flow-source.md`

## Section Guides

Load only the needed section file:

- Abstract: `references/abstract.md`
- Introduction: `references/introduction.md`
- Related Work: `references/related-work.md`
- Method: `references/method.md`
- Experiments: `references/experiments.md`
- Conclusion: `references/conclusion.md`
- Paper review: `references/paper-review.md`
- Paragraph clarity source: `references/does-my-writing-flow-source.md`
- Example bank index: `references/examples/index.md`

## Paper Review Core Points

Use `references/paper-review.md` for the full checklist and workflow.

1. Add an end-of-draft self-review question list in five dimensions:
   - contribution,
   - writing clarity,
   - experimental strength,
   - evaluation completeness,
   - method design soundness.
2. Treat claim-evidence alignment as a hard constraint, especially for Abstract and Introduction.
3. For HPC papers, treat scaling, throughput, latency, memory, energy, and portability as evidence dimensions.
4. Perform adversarial writing: review as a skeptical reviewer and resolve every high-risk question.
5. Revise until major rejection risks are explicitly addressed.

## Execution Rules

1. Build a mini-outline before drafting prose.
2. For each subsection, explicitly include motivation, design, and technical advantage when applicable.
3. When relevant, state system model, workload assumptions, and hardware/software environment before details.
4. Avoid writing style that looks like incremental patching of a naive baseline.
5. Keep terminology stable across the full paper.
6. If a claim cannot be supported by results, weaken or remove the claim.
7. Before finalizing, append and answer a five-dimension self-review question list, then revise the paper based on unresolved items.
8. Do not load all section references at once; load only the specific section guide needed for the current edit target.

## Output Contract

When asked to rewrite or draft sections, return:

1. A compact section outline (3-7 bullets).
2. Revised paragraphs with explicit paragraph roles (opening/challenge/system model/method/advantage/evidence/limitation).
3. A short self-review checklist covering clarity, flow, terminology consistency, unsupported claims, scaling evidence, and missing environment details.
4. A claim-evidence map for each major claim in the revised text using `Claim: ... | Evidence: ... | Status: supported/needs evidence`.
5. When relevant, add a compact note on platform assumptions and fairness protocol.
