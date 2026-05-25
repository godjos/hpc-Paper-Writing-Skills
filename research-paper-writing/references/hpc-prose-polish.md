# HPC Prose Polish Guide

Use this guide as the final language pass after structure, terminology, and evidence have been checked. The goal is reviewer-facing HPC prose: precise, fluent, concrete, and measured. For polish requests, preserve the draft's technical meaning and use the smallest wording change that makes the prose clearer.

For supplied manuscript text, polish is approval-first. Do not directly return a clean rewritten
paragraph in the first pass. First provide a sentence-level proposal that lists the original
sentence, problem, proposed rewrite, reason, and protected LaTeX or technical tokens. Produce the
clean paste-ready revised text only after the user confirms which proposals to apply.

## Sentence-Level Proposal Gate

Before rewriting supplied text, split the passage into sentences while preserving LaTeX, citations,
inline math, macros, labels, references, code-like identifiers, variable names, units, and canonical
HPC terms.

Return proposed edits in this format:

`S# | Original | Problem | Proposed rewrite | Reason | Protected tokens`

Use `Problem: none` and `Proposed rewrite: keep original` when the sentence is already clear,
technically safe, and fluent.

The `Reason` field must be detailed enough for the author to decide whether to accept the change.
Explain the language issue, reviewer-facing risk, terminology choice, claim-scope change, flow
repair, or LaTeX-safety decision. Do not use vague reasons such as `improved clarity` without
stating what became clearer.

After the table, ask the user to confirm whether to apply all proposals, apply selected sentence
numbers, or adjust specific proposals. Do not provide the clean rewritten paragraph until that
confirmation arrives.

## Polish Pass

For each revised paragraph, run this pass before final output:

1. Identify the paragraph role: motivation, bottleneck, system model, method, mechanism, evidence, limitation, or transition.
2. Check whether the first sentence states that role clearly.
3. Replace vague academic phrasing with concrete HPC language only when the source draft or
   supplied context supports the specific term.
4. Keep the sentence subject stable when possible: workload, bottleneck, system, module, mechanism, metric, or evidence.
5. Use cause, contrast, consequence, or refinement links between adjacent sentences.
6. Remove filler that does not change the technical claim.
7. Check that every performance statement names the metric, unit, scale, and condition when available.
8. Keep claims measured. Do not use stronger wording than the evidence supports.
9. Do not make prose more abstract: prefer short subjects, concrete actions, and verifiable
   objects over high-level nouns or broad claims.
10. For non-native English drafts, fix grammar, articles, prepositions, tense, agreement, and
    awkward phrase order without changing the technical claim or adding new evidence.

## LaTeX and Citation Safety

When polishing LaTeX manuscript text:

1. Preserve LaTeX commands, macro names, labels, citation keys, reference keys, equation content,
   table and figure numbers, paths, code identifiers, and inline math.
2. Do not rewrite text inside `\cite{...}`, `\ref{...}`, `\label{...}`, `\autoref{...}`,
   `\cref{...}`, math delimiters, or code-like snippets unless the user explicitly asks.
3. Keep placeholders, comments, TODO markers, and reviewer annotations visible unless asked to
   remove them.
4. Polish the natural-language sentence around protected syntax so the output remains compilable
   and ready to paste back into a manuscript.
5. In the sentence-level proposal, list protected syntax and technical identifiers in the
   `Protected tokens` field. If a proposed rewrite must move a protected token, explain why and
   preserve the exact token text.

## HPC Style Targets

Prefer prose that sounds like a systems/HPC paper:

1. Name the system layer precisely: algorithm, runtime, compiler, memory hierarchy, network, storage, scheduler, or application.
2. Name the execution entity precisely: node, socket, NUMA domain, core, MPI rank, OpenMP thread, GPU kernel, task, stream, request, or I/O process.
3. Name the measured quantity precisely: end-to-end runtime, kernel time, communication volume, message count, memory bandwidth, I/O bandwidth, speedup, strong scaling, weak scaling, or parallel efficiency.
4. Explain mechanism before result when the paragraph argues why the result should hold.
5. Explain result conditions before generalizing: workload, problem size, node/GPU count, baseline, backend, and precision.
6. Use restrained verbs such as `reduces`, `improves`, `overlaps`, `amortizes`, `bounds`, `exposes`, `preserves`, `scales`, and `degrades`.
7. Avoid marketing verbs such as `revolutionizes`, `greatly enhances`, `dramatically boosts`, or `fully solves` unless the evidence is unusually strong.
8. Avoid ornamental academic words such as `leverage`, `facilitate`, `paradigm`, `robust`,
   `seamless`, `substantial`, `significant`, `intricate`, `pivotal`, `underscore`,
   `holistic`, and `sophisticated` unless the draft already uses them or the context strongly
   supports them. Prefer direct verbs such as `use`, `enable`, `show`, `reduce`, `increase`,
   `explain`, or `support`.

## Common Non-HPC Phrasing to Fix

Replace vague phrasing with technical phrasing only when the draft or supplied context supports the
more specific term. Otherwise keep a conservative phrase and note the missing context.

1. `improves performance` -> name the metric, such as `reduces end-to-end runtime` or `improves weak-scaling efficiency`, only when the metric is provided; otherwise use `improves measured performance` and mark `needs metric`.
2. `uses resources efficiently` -> name the resource, such as `reduces HBM traffic`, `improves SM occupancy`, or `reduces MPI message count`, only when that resource is identified; otherwise keep `resource use` or mark `needs resource`.
3. `handles large-scale data` -> name the scale, data structure, and movement path only when they are provided; otherwise keep the scale claim conservative.
4. `communication overhead` -> name the source, such as `halo exchange`, `all-reduce latency`, `RDMA transfer time`, or `metadata operations`, only when the communication primitive or path is identified; otherwise keep `communication cost` and mark `needs communication primitive`.
5. `our method is scalable` -> name strong scaling, weak scaling, throughput scaling, or parallel efficiency only when the scaling type and evaluated scale are provided.
6. `significant improvement` -> report the measured improvement and condition, or weaken to `improvement` when evidence is incomplete.
7. `advanced optimization` -> name the mechanism, such as tiling, fusion, overlap, aggregation, prefetching, placement, or scheduling, only when the mechanism appears in the draft or supplied context.

## Sentence-Level Flow

Check each sentence pair:

1. Cause: Does sentence B explain why sentence A happens?
2. Contrast: Does sentence B clarify a limitation or difference?
3. Consequence: Does sentence B state the impact of sentence A?
4. Refinement: Does sentence B make sentence A more precise?
5. Evidence: Does sentence B support sentence A with measurement, setup, or observation?

If none applies, revise the transition or split the paragraph.

## Final Language Gate

Before final output, confirm:

1. The paragraph can be read aloud without awkward phrase stacking.
2. The main nouns stay consistent across the paragraph.
3. Generic words such as `performance`, `resources`, `method`, `data`, `system`, and `optimization` are replaced when a precise HPC term is available.
4. Claims are not inflated beyond the evidence.
5. Sentences are varied but not ornamental.
6. The text reads like a careful HPC/system paper, not a general technical blog post.
7. Any withheld specificity is noted, for example `kept "communication cost" because the draft does not identify the communication primitive`.
8. LaTeX, citations, references, equations, macros, labels, and code-like identifiers are preserved.
9. Grammar and fluency changes help readability rather than creating pedantic churn.

## Change Justification

When proposing polished text, explain every sentence-level change. For unchanged sentences, give a
short reason for keeping the original.

1. Mention grammar or fluency fixes that materially improve readability.
2. Mention terminology changes that affect correctness or reviewer perception.
3. Mention overclaims that were weakened because evidence is missing.
4. Mention sentence-flow repairs such as cause, contrast, consequence, refinement, or evidence
   links.
5. Mention LaTeX or citation syntax that was intentionally preserved.
6. If the draft is already clear and correct, propose `keep original` and state
   `No meaningful change needed` rather than making cosmetic edits.

## Final Language Rubric

Before proposing revised prose, score every revised paragraph as `pass` or `revise`.

Use this compact format:

`P1 | role: motivation | verdict: pass | reason: clear bottleneck, precise workload term, smooth cause/effect transition`

`P2 | role: evidence | verdict: revise | reason: performance claim lacks scale and metric condition`

A paragraph can receive `pass` only if all of the following are true:

1. The first sentence states the paragraph role or message.
2. The paragraph has one main message.
3. Adjacent sentences are connected by cause, contrast, consequence, refinement, or evidence.
4. Specialized HPC terms match the terminology ledger and the correct system layer.
5. Generic words are replaced only where precise HPC terms are available from the source draft or supplied context.
6. Performance claims include metric, unit, scale, and condition when the source draft provides them.
7. Claims are measured and do not exceed the available evidence.
8. LaTeX, citations, references, equations, macros, labels, and code-like identifiers are preserved.
9. The paragraph reads fluently without awkward phrase stacking.

Mark the paragraph as `revise` if any condition fails. For every `revise`, propose sentence-level
fixes before final output or explicitly state the missing input that prevents a pass, such as
`needs scale`, `needs baseline`, `needs hardware detail`, or `needs evidence`.

Final output should not contain unresolved `revise` verdicts unless the user has not provided the
missing evidence or setup detail needed to resolve them. Clean paste-ready prose should appear only
after the user confirms the sentence-level proposal.
