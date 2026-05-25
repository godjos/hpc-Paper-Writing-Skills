# Paper Revision and Polish Guide

Use this guide when the user asks to revise, edit, improve, or modify an existing HPC/system paper
section beyond a small wording polish. Revision is not grammar-only editing. Diagnose the paper
logic first, then revise prose.

For pre-submission polishing, treat revision as an iterative loop rather than a single rewrite:
diagnose the highest reviewer risk, make the smallest manuscript change that addresses it, then
verify that the change is supported by evidence and consistent with the rest of the supplied paper.
Repeat only while the next issue can be fixed from the available context.

For any supplied manuscript text, revision is approval-first. Do not directly return clean
paste-ready prose in the first pass. First provide sentence-level proposed rewrites with the
original sentence, problem, proposed rewrite, reason, and protected LaTeX or technical tokens. Wait
for user confirmation before producing the final revised text.

## Revision Order

Apply revision passes in this order:

1. Intent and evidence: identify the section target, author's intended reader takeaway, venue or
   reviewer constraints, supplied evidence, and missing inputs.
2. Main point: identify the section's central claim and whether each paragraph supports it.
3. Reader and purpose: infer what a skeptical HPC/system reviewer must understand after reading.
4. Evidence: check whether claims are supported by results, setup details, citations, or supplied
   context.
5. Organization: repair paragraph order, topic sentences, transitions, and missing bridges.
6. Style calibration: preserve useful author or venue style using `style-calibration.md` when a
   sample or target style is supplied.
7. Terminology: align workload, platform, metric, baseline, system layer, abbreviations, and units
   with `hpc-terminology.md`.
8. Independent review: run a separate reviewer/verifier pass when available, or run the same checks
   as self-review when no subagent is available.
9. Fact and claim verification: trace major claims to supplied evidence or mark the missing input.
10. Cross-section consistency: when multiple sections are supplied, check that Abstract,
    Introduction, Method, Experiments, Related Work, and Conclusion describe the same contribution,
    mechanism, result scope, baseline, limitation, and artifact status.
11. Language polish: apply `hpc-prose-polish.md` only after the structure and evidence pass.

Do not skip to sentence-level polish when the section has a weak claim, missing evidence, or broken
paragraph flow.

## Pre-Submission Iteration Loop

Use this loop when the user is repeatedly polishing before submission, asks for another pass, or
provides reviewer/coauthor concerns:

1. Establish iteration state: target section, prior unresolved risks if supplied, venue/reviewer
   constraints, evidence packet, and what would count as done for this pass.
2. Prioritize reviewer risk: choose the smallest set of high-risk issues that can be fixed now.
3. Diagnose before changing: run the reverse outline, claim/evidence gate, and terminology pass
   only at the scope needed for the chosen issue.
4. Propose narrowly: change manuscript prose, claim scope, paragraph order, or transitions only
   where the diagnosis requires it, and present the proposed sentence-level edits for confirmation.
5. Record the trace: report each substantial edit as
   `Priority: P0/P1/P2 | Change: ... | Reason: ... | Risk addressed: ...`.
6. Verify the pass: check claim/evidence support, LaTeX safety, abbreviation first use,
   AI-pattern risk, and cross-section consistency where supplied.
7. Decide the next action: continue only if another high-risk issue is fixable from the supplied
   context; otherwise report missing evidence, experiment, citation, hardware detail, baseline
   detail, or author decision as the next-round blocker.

Do not keep polishing already-acceptable prose just to produce visible change. If the current pass
has no meaningful manuscript improvement, say so and spend the output on the remaining evidence or
reviewer-risk blockers.

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

## Independent Review Focus

After the first revision, review the draft separately from the rewrite pass. When a reviewer or
verifier subagent is available, ask it to perform this pass independently. If no subagent is
available, run the same checks yourself and label the result as self-review.

Check:

1. AI-pattern risk: paragraphs that sound like generic generated academic prose rather than a
   specific HPC/system paper.
2. Logic continuity: missing cause, contrast, consequence, refinement, or evidence links between
   adjacent paragraphs.
3. Role repetition: consecutive paragraphs that repeat motivation, contribution, method, or result
   roles without adding new information.
4. Evidence rhythm: long stretches of claims without measurements, citations, setup details, or
   mechanism explanation.
5. Reviewer perception: wording that makes the work sound like a minor patch, an overbroad
   solution, or a result without fair comparison conditions.

## Revision Decisions

Use the smallest proposed change that fixes the diagnosed problem:

1. Preserve paragraph order when topic sentences and evidence already form a coherent chain.
2. Reorder paragraphs only when the reader needs background, bottleneck, mechanism, or evidence in
   a different sequence.
3. Combine paragraphs when they repeat the same role or claim.
4. Split paragraphs when one paragraph mixes motivation, method, and result evidence.
5. Weaken unsupported claims instead of adding new results or citations.
6. Add a missing bridge sentence only when the relationship is implied by the draft or user context.
7. Keep reviewer-facing prose concise; avoid ornamental academic phrasing.

## Suggestion Priority

Label proposed changes with this priority scale:

- `P0 must fix`: correctness, logic, claim/evidence mismatch, unsupported overclaim, LaTeX safety,
  reviewer-blocking structure, or clear language error.
- `P1 should fix`: changes that materially improve clarity, flow, reviewer perception,
  terminology precision, or argument strength.
- `P2 optional`: style, concision, phrasing, or presentation polish that is useful but not required
  for correctness or reviewer comprehension.

Use priority labels for sentence-level rewrite proposals, reviewer-risk lists, claim/evidence
risks, and action lists. Order P0 before P1 before P2 unless the user asks for a different view.

## Sentence-Level Rewrite Proposal

For every sentence affected by revision, return:

`S# | Priority | Original | Problem | Proposed rewrite | Reason | Protected tokens`

Rules:

1. Keep sentence numbering stable within the supplied passage.
2. Use `Priority: P2 optional`, `Problem: none`, and `Proposed rewrite: keep original` for
   sentences that should not change.
3. Use `P0 must fix` for changes needed to avoid incorrect, unsupported, inconsistent, or
   reviewer-blocking text; use `P1 should fix` for meaningful clarity or argument improvements;
   use `P2 optional` for cosmetic polish.
4. Explain each reason in terms of grammar, flow, reviewer perception, claim scope, evidence
   support, terminology precision, or LaTeX safety.
5. List protected LaTeX commands, citations, labels, references, equations, macros, code-like
   identifiers, canonical terms, units, and variable names.
6. If the revision requires paragraph reordering, splitting, or merging, report that structural
   proposal before the sentence table, then give sentence-level proposals for the affected text.
7. End the first-pass revision with a confirmation request. Do not include clean paste-ready prose
   until the user confirms all or selected proposals.

## Claim and Evidence Gate

For every major claim, confirm:

1. Claim type: novelty, mechanism, performance, scalability, portability, reproducibility,
   usability, or limitation.
2. Evidence source: supplied result, figure/table, method detail, citation, reviewer comment, or
   missing.
3. Scope: workload, platform, scale, baseline, metric, and condition.
4. Action: keep, weaken, move, request evidence, or remove.

Use this compact format when reporting risks:

`Priority: P0 must fix | Claim: ... | Evidence: ... | Risk: unsupported performance claim; needs scale and baseline`

## Cross-Section Consistency Gate

Run this gate for submission-oriented revision whenever more than one section is supplied:

1. Contribution scope: Abstract and Introduction do not claim more than Method and Experiments
   support.
2. Mechanism: the claimed reason for improvement is the same across Introduction, Method, and
   Experiments.
3. Result scope: speedup, scaling, efficiency, portability, and artifact claims use compatible
   workloads, platforms, baselines, metrics, and scales.
4. Closest work: Related Work distinctions match the novelty and baseline framing in the main text.
5. Limitations: Conclusion and discussion sections do not weaken or contradict headline claims
   without explaining the boundary.
6. Terminology: names for workloads, modules, kernels, runtimes, baselines, hardware, and metrics
   remain stable across sections.

Report inconsistencies as:

`Inconsistency: ... | Sections: ... | Risk: ... | Fix: ...`

## Fact and Claim Verification

Every major factual statement must trace to supplied manuscript text, results, figures, citations,
reviewer comments, public facts provided by the user, or a clearly marked missing input.

Verify these claim families before final prose:

1. Performance: metric, unit, workload, platform, scale, baseline, and comparison condition.
2. Novelty: closest-work target, new mechanism, or precise scope of what is new.
3. Scalability: strong scaling, weak scaling, throughput scaling, or parallel efficiency, with the
   evaluated scale.
4. Artifact and reproducibility: hardware, software, build, launch, workload, parameters, and
   artifact availability.
5. Baseline fairness: baseline version, tuning level, hardware parity, and workload equivalence.
6. Reviewer response: supplied reviewer concern, manuscript change, and remaining limitation.

Do not invent experiments, citations, hardware, baseline behavior, reviewer intent, artifact status,
or causal explanations. If evidence is absent, weaken the claim, remove it, or report the missing
input.

## Reviewer-Comment Revision

When reviewer comments are supplied:

1. Separate reviewer requests from author intent and from the draft text.
2. Map each reviewer concern to the affected section, claim, evidence, figure/table, or limitation.
3. Revise the manuscript text first, then provide response-to-reviewer wording only if requested.
4. Close the loop with
   `Concern: ... | Manuscript change: ... | Response status: addressed/partially addressed/needs evidence`.
5. Do not invent experiments or claim that a reviewer concern has been addressed unless the supplied
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

1. Diagnosis: reverse outline summary plus the highest-risk issues labeled `P0/P1/P2`.
2. Revision plan: the concrete structural, evidence, terminology, and polish changes to make,
   labeled `P0/P1/P2`.
3. Style calibration note: anchors used and boundaries preserved, or `none`.
4. Sentence-level rewrite proposal:
   `S# | Priority | Original | Problem | Proposed rewrite | Reason | Protected tokens`.
5. Change log: substantial edits and why they were made, using
   `Priority: P0/P1/P2 | Change: ... | Reason: ... | Risk addressed: ...`.
6. Independent review/self-review note: AI-pattern risk, logic continuity, role repetition,
   evidence rhythm, and reviewer perception.
7. Reviewer-concern map: only when reviewer or coauthor concerns are supplied.
8. Cross-section consistency note: only when multiple sections are supplied.
9. Claim/evidence risks: major unresolved risks.
10. Remaining missing inputs: `none` or a short list such as `needs baseline`, `needs scale`,
   `needs citation`, `needs hardware detail`, or `needs reviewer comment context`.
11. Confirmation request before producing clean prose ready to paste into the paper.
