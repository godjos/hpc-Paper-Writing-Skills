# Paper Revision and Polish Guide

Use this guide when the user asks to revise, edit, improve, or modify an existing HPC/system paper
section beyond a small wording polish. Revision is not grammar-only editing. Diagnose the paper
logic first, then revise prose.

## Revision Order

Apply revision passes in this order:

1. Main point: identify the section's central claim and whether each paragraph supports it.
2. Reader and purpose: infer what a skeptical HPC/system reviewer must understand after reading.
3. Evidence: check whether claims are supported by results, setup details, citations, or supplied
   context.
4. Organization: repair paragraph order, topic sentences, transitions, and missing bridges.
5. Terminology: align workload, platform, metric, baseline, system layer, abbreviations, and units
   with `hpc-terminology.md`.
6. Language polish: apply `hpc-prose-polish.md` only after the structure and evidence pass.

Do not skip to sentence-level polish when the section has a weak claim, missing evidence, or broken
paragraph flow.

## Reverse Outline Pass

Before rewriting a section, build this compact map:

`P# | role: ... | topic sentence: ... | support: ... | issue: pass/flow gap/needs evidence/overclaim`

Roles can be motivation, gap, bottleneck, insight, method, mechanism, evidence, limitation,
transition, or contribution.

Mark:

1. `flow gap` when adjacent paragraphs or sentences do not connect by cause, contrast,
   consequence, refinement, example, or evidence.
2. `needs evidence` when a result, claim, citation, setup detail, baseline, scale, or metric is
   required but absent.
3. `overclaim` when the prose generalizes beyond the supplied evidence.
4. `scope drift` when a paragraph does not support the section's main claim.

## Revision Decisions

Use the smallest change that fixes the diagnosed problem:

1. Preserve paragraph order when topic sentences and evidence already form a coherent chain.
2. Reorder paragraphs only when the reader needs background, bottleneck, mechanism, or evidence in
   a different sequence.
3. Combine paragraphs when they repeat the same role or claim.
4. Split paragraphs when one paragraph mixes motivation, method, and result evidence.
5. Weaken unsupported claims instead of adding new results or citations.
6. Add a missing bridge sentence only when the relationship is implied by the draft or user context.
7. Keep reviewer-facing prose concise; avoid ornamental academic phrasing.

## Claim and Evidence Gate

For every major claim, confirm:

1. Claim type: novelty, mechanism, performance, scalability, portability, reproducibility,
   usability, or limitation.
2. Evidence source: supplied result, figure/table, method detail, citation, reviewer comment, or
   missing.
3. Scope: workload, platform, scale, baseline, metric, and condition.
4. Action: keep, weaken, move, request evidence, or remove.

Use this compact format when reporting risks:

`Claim: ... | Evidence: ... | Risk: unsupported performance claim; needs scale and baseline`

## Reviewer-Comment Revision

When reviewer comments are supplied:

1. Separate reviewer requests from author intent and from the draft text.
2. Map each reviewer concern to the affected section, claim, evidence, figure/table, or limitation.
3. Revise the manuscript text first, then provide response-to-reviewer wording only if requested.
4. Do not invent experiments or claim that a reviewer concern has been addressed unless the supplied
   revision text actually addresses it.

## Polish Boundary

After revision, apply language polish conservatively:

1. Fix grammar, articles, prepositions, agreement, tense, and awkward sentence stacking.
2. Improve fluency for non-native English while preserving the author's technical meaning.
3. Preserve LaTeX commands, labels, citations, references, equations, macros, table/figure numbers,
   and code-like identifiers.
4. Do not replace established technical terms with more elegant synonyms.
5. If no meaningful improvement is available, state `No meaningful change needed` instead of making
   pedantic edits.

## Output Template

Return:

1. Diagnosis: reverse outline summary plus the highest-risk issues.
2. Revision plan: the concrete structural, evidence, terminology, and polish changes to make.
3. Revised text: clean prose ready to paste into the paper.
4. Claim/evidence risks: major unresolved risks.
5. Remaining missing inputs: `none` or a short list such as `needs baseline`, `needs scale`,
   `needs citation`, `needs hardware detail`, or `needs reviewer comment context`.
