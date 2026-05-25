---
name: research-paper-writing
description: Improve, revise, edit, polish, or review HPC and systems papers with terminology-aware prose, section structure, claim-evidence alignment, scalability logic, reproducibility notes, reviewer comments, LaTeX text, and non-native English support. Use for Abstract, Introduction, Related Work, Method, Experiments, Conclusion, figures/tables, performance claims, revision passes, or submission readiness.
---
# HPC Paper Writing

## Purpose

Use this skill to help HPC and systems papers read clearly to skeptical reviewers.
Prioritize a coherent paper story, precise terminology, supported performance claims,
readable experiments, and concise reviewer-facing prose.

## Mode Selection

Choose the lightest mode that satisfies the user request.

| Mode | Use when | Default references | Default output |
| --- | --- | --- | --- |
| Quick polish | The user asks to polish only, smooth, shorten, grammar-check, or improve wording for a paragraph or small passage. Use conservative polish by default: improve clarity, grammar, and flow while preserving the original technical meaning. | `hpc-terminology.md`, `hpc-prose-polish.md` | Sentence-level proposal table, important changes, abbreviation/terminology note, withheld specificity note, and confirmation request before clean rewrite. |
| Revision pass | The user asks to revise, edit, improve this section, respond to reviewer comments, or modify an existing section beyond sentence-level polish. Diagnose structure and evidence before rewriting; do not treat revision as grammar-only polish. | `paper-revision-polish.md`, `style-calibration.md`, `hpc-terminology.md`, `hpc-prose-polish.md`, section guide when relevant | Diagnosis, compact revision plan, sentence-level proposal table, change rationale, claim/evidence risks, and confirmation request before clean rewrite. |
| Pre-submission polish loop | The user is repeatedly polishing before submission, wants one more pass, asks whether the current draft is ready, or supplies reviewer/coauthor concerns plus manuscript text. Iterate through diagnosis, revision, and verification until the current pass has no fixable high-risk issue from the supplied context. | `paper-revision-polish.md`, `paper-review.md`, `final-self-check.md`, `style-calibration.md`, `performance-evidence.md`, `hpc-terminology.md`, section guide when relevant | Iteration state, reviewer-risk priorities, sentence-level proposal or targeted patch proposal, change log, reviewer-concern map, cross-section consistency check, and next-round blockers. |
| Section rewrite | The user asks to draft or rewrite Abstract, Introduction, Related Work, Method, Experiments, or Conclusion. | `style-calibration.md`, `hpc-terminology.md`, section guide, `hpc-prose-polish.md`, `final-self-check.md` when producing final prose | Terminology ledger, mini-outline, revised paragraphs with roles, abbreviation note, and claim-evidence map. |
| Evidence review | The user asks whether experiments, results, claims, figures, baselines, scaling, or artifacts are convincing. | `performance-evidence.md`, `experiments.md`, `figures-tables.md`, `reproducibility-artifact.md` | Reviewer risks, unsupported claims, missing evidence, and concrete revision actions. |
| Submission review | The user asks for pre-submission, reviewer, venue, or full-paper review. | `paper-review.md`, `venue-reviewer-profile.md`, `performance-evidence.md`, `reproducibility-artifact.md`, `style-calibration.md`, `final-self-check.md` | Prioritized rejection risks, claim-evidence gaps, reproducibility gaps, closest-work risks, and final action list. |

If the user does not specify a mode, infer it from the task. Do not run the full submission
review for a small wording request.

## Default Workflow

1. Identify the target section, task mode, paper type, venue if known, and available evidence.
2. Build only the terminology needed for the current task: workload, platform, parallel model,
   execution entities, metrics, baselines, units, abbreviations, and environment assumptions.
   For polish requests, use only terms supported by the source draft or supplied user context.
3. Load only the references required by the selected mode. Do not load every guide or example.
4. For revision requests, run a reverse-outline pass before proposing rewrites: main claim, paragraph
   role, topic sentence, supporting evidence, flow gap, and unsupported overclaim.
5. For any task that modifies supplied manuscript text, do not directly return paste-ready revised
   prose in the first pass. First return a sentence-level rewrite proposal with original sentence,
   problem, proposed rewrite, and reason; wait for user confirmation before producing the clean
   revised text.
6. Never edit manuscript files in place on the first pass, regardless of how directly the user asks.
   The first pass must propose edits with reasons and protected tokens, then wait for confirmation.
7. Apply source-file edits only after the user has seen the proposal and confirms that the changes
   should be applied. Then make the smallest safe manuscript patch and report the edited file,
   affected section, and a concrete change log with reasons for every paragraph-level change and
   every non-trivial sentence-level change.
8. Draft or review paragraph-by-paragraph. Keep one message per paragraph and preserve the
   terminology ledger.
9. Check abbreviation order before final output: each abbreviation must be expanded at first use
   unless it is universally standard in context.
10. Check major claims against available evidence. Weaken or remove unsupported claims.
11. For iterative pre-submission work, run a three-stage loop: diagnose the highest reviewer risk,
   propose changes only for the affected text, then verify claim/evidence, cross-section
   consistency, and reviewer-concern closure before starting another pass.
12. Run the prose polish pass when producing final prose.
13. For full-paper or submission work, finish with adversarial self-review.

## Structured Gates

Use these gates only for modes that need them; do not upgrade Quick polish into a full revision
or submission workflow.

1. Intent and evidence confirmation: identify the target section, intended reader takeaway,
   supplied evidence, venue or reviewer constraints, and missing inputs.
2. Structure diagnosis: run the reverse outline or section outline before rewriting.
3. Style calibration: use `style-calibration.md` when user samples, venue norms, or prior draft
   tone should guide the rewrite.
4. Sentence-level proposal gate: before rewriting supplied text, list each affected sentence with
   original sentence, problem, proposed rewrite, reason, and protected LaTeX/technical tokens.
5. User confirmation gate: after the sentence-level proposal, stop and ask the user to confirm,
   reject, or adjust the proposed rewrites. Produce clean paste-ready prose only after confirmation.
6. Source-file edit gate: do not apply changes directly to manuscript files until a prior proposal
   has been shown and the user confirms it should be applied. Direct edits still require a post-edit
   report with detailed reasons; do not silently rewrite manuscript text.
7. Rewrite or review: make the smallest changes that fix structure, evidence, terminology, and
   prose in that order.
8. Revision trace: for pre-submission or reviewer-driven work, record why each substantial change
   was made and what reviewer risk or claim/evidence gap it addresses.
9. Independent review: when a reviewer or verifier subagent is available and the task is a
   substantial revision, rewrite, or submission review, use it for a separate AI-pattern, logic,
   evidence, and reviewer-risk pass. If no subagent is available, run the same pass yourself and
   label it as self-review.
10. Fact and claim verification: trace every performance, novelty, scalability, artifact, baseline,
   and reviewer-response claim to supplied text, results, citations, or an explicit missing-input
   note.
11. Cross-section consistency: for submission-oriented revision, check that Abstract, Introduction,
   Method, Experiments, Related Work, and Conclusion use compatible contribution, mechanism,
   result, limitation, terminology, and baseline scopes when those sections are supplied.
12. Final self-check: use `final-self-check.md` for final prose, full-paper review, or any answer
   that claims submission readiness.

## Reference Router

Load these files only when the task calls for them:

- Paper intake: `references/paper-intake.md`
- Abstract: `references/abstract.md`
- Introduction: `references/introduction.md`
- Related Work: `references/related-work.md`
- Method: `references/method.md`
- Experiments: `references/experiments.md`
- Conclusion: `references/conclusion.md`
- Figures and tables: `references/figures-tables.md`
- Performance evidence: `references/performance-evidence.md`
- Reproducibility and artifact: `references/reproducibility-artifact.md`
- Venue and reviewer profile: `references/venue-reviewer-profile.md`
- Paper review: `references/paper-review.md`
- Paper revision and polish: `references/paper-revision-polish.md`
- Style calibration: `references/style-calibration.md`
- Final self-check: `references/final-self-check.md`
- HPC terminology: `references/hpc-terminology.md`
- HPC prose polish: `references/hpc-prose-polish.md`
- Paragraph flow source: `references/does-my-writing-flow-source.md`
- Example bank: `references/examples/index.md`

Use examples only when the user asks for templates/examples, the requested section is hard to
structure, or a concrete HPC mini case would clarify the writing pattern. Reuse sentence logic,
not exact wording.

## Writing Rules

1. State each paragraph's message in its first sentence.
2. Keep one paragraph focused on one message.
3. Define workload names, hardware terms, runtime terms, and non-obvious abbreviations before reuse.
4. Use precise HPC/system terms at the correct layer: node, socket, NUMA domain, core, process,
   rank, thread, task, GPU, SM, warp, kernel, cache, DRAM, HBM, PCIe, NVLink, InfiniBand,
   RDMA, collective, halo exchange, I/O, strong scaling, and weak scaling, but only when the
   draft or supplied context supports that layer and term.
5. Preserve canonical names, abbreviations, capitalization, and units from the user's draft unless
   a naming change is requested.
6. Connect sentences through cause, contrast, consequence, refinement, or example.
7. Separate end-to-end gains from kernel-level, microbenchmark, or tuning-only gains.
8. Avoid making the work sound like a minor patch to a naive baseline.
9. State comparison conditions, platform assumptions, and experimental settings when needed for
   reviewer trust.
10. Prefer concise, reviewer-facing prose over mechanical academic phrasing.
11. For supplied manuscript text, preserve LaTeX commands, citations, labels, references, equations,
    macros, code-like identifiers, canonical technical terms, capitalization, units, and variable
    names unless the user explicitly approves a change.
12. Explain every proposed rewrite in enough detail for the author to accept, reject, or adjust it.
13. When confirmed manuscript edits are applied, never report only "polished" or "updated"; include
    what changed, why it improves reviewer comprehension, and which technical meaning or LaTeX
    tokens were intentionally preserved.

## Output Contracts

### Confirmed Manuscript Edit Addendum

Use this addendum only after the user has already reviewed the proposal and confirmed that the
edits should be applied to the manuscript file/source. After applying the patch, return:

1. Changed file(s) and target section(s).
2. Change log using `Change: ... | Reason: ... | Protected meaning/tokens: ...`.
3. Claim/evidence notes for any strengthened, weakened, moved, or removed claim.
4. Verification note covering LaTeX token preservation, citation/reference preservation,
   abbreviation first use, and unsupported specificity.

If the user has not already confirmed a specific proposal, do not modify manuscript files even when
the request asks for direct edits; return the normal proposal table first.

### Quick Polish

Return:

1. Sentence-level proposal table using `S# | Original | Problem | Proposed rewrite | Reason |
   Protected tokens`.
2. Important changes, limited to changes that affect clarity, correctness, fluency, LaTeX safety,
   or reviewer perception.
3. Abbreviation/terminology note, or `none`.
4. Withheld specificity note explaining any more-specific term that was preserved, weakened, or not
   introduced because the draft lacks evidence or setup detail.
5. Confirmation request: ask the user whether to apply the proposed rewrites, apply only selected
   items, or adjust any proposal.

Quick Polish must not add or replace workload, platform, parallel model, bottleneck, metric,
baseline, hardware, communication pattern, memory hierarchy, system layer, or mechanism details
unless they are present in the user's draft or explicitly supplied context.

Quick Polish must not return a clean paste-ready revised paragraph until the user confirms the
sentence-level proposal.

### Revision Pass

Return:

1. Diagnosis covering the section's main claim, paragraph roles, topic-sentence alignment,
   supporting evidence, flow gaps, style-calibration constraints, and unsupported overclaims.
2. Compact revision plan with the smallest structural and language changes needed.
3. Sentence-level rewrite proposal using `S# | Original | Problem | Proposed rewrite | Reason |
   Protected tokens`.
4. Claim/evidence risks using `Claim: ... | Evidence: ... | Risk: ...`.
5. Change rationale for substantial structural, evidence, terminology, or claim-scope edits.
6. Independent review/self-review note covering AI-pattern risk, logic, evidence, and reviewer
   perception.
7. Remaining missing inputs, or `none`.
8. Confirmation request before producing clean revised text.

Revision Pass must revise structure, evidence alignment, and prose in that order. It may reorganize
or combine paragraphs, but it must not invent results, citations, reviewer intent, hardware details,
or experimental conditions.

Revision Pass must not return clean paste-ready revised prose until the user confirms the
sentence-level proposal. If a structural change requires moving or merging paragraphs, describe the
paragraph-level change first and then give sentence-level proposals for the affected text.

### Section Rewrite

Return:

1. Compact HPC terminology ledger.
2. Style anchors and boundaries, or `none` if no style sample or venue style constraint is supplied.
3. Section outline with 3-7 bullets.
4. For rewrites of supplied text, sentence-level rewrite proposal using `S# | Original | Problem |
   Proposed rewrite | Reason | Protected tokens`; for draft-from-scratch requests with no source
   text, proposed paragraphs with paragraph roles.
5. Abbreviation first-use note, or `none`.
6. Claim-evidence map for major claims using `Claim: ... | Evidence: ... | Status: supported/needs evidence`.
7. Short self-review note covering clarity, flow, terminology, unsupported claims, scaling evidence,
   and missing environment details.
8. Confirmation request before producing clean revised text when source text was supplied.

### Evidence Review

Return:

1. Major claim-evidence gaps.
2. Baseline fairness and comparison-condition risks.
3. Scaling, profiling, ablation, and end-to-end evidence gaps.
4. Figure/table readability issues when relevant.
5. Concrete revision actions, ordered by reviewer risk.

### Pre-Submission Polish Loop

Return:

1. Iteration state: current pass goal, target section(s), supplied evidence, venue/reviewer
   constraints, and unresolved risks from prior passes when provided.
2. Reviewer-risk priorities, ordered by likelihood of harming acceptance.
3. Sentence-level rewrite proposal or targeted patch proposal, scoped to the highest-risk fixable
   issues, using `S# | Original | Problem | Proposed rewrite | Reason | Protected tokens`.
4. Change log using `Change: ... | Reason: ... | Risk addressed: ...`.
5. Reviewer-concern map using `Concern: ... | Manuscript change: ... | Response status:
   addressed/partially addressed/needs evidence`.
6. Cross-section consistency check for contribution, mechanism, result scope, terminology,
   baseline, limitations, and artifact claims when the relevant sections are supplied.
7. Verification result: claim/evidence, LaTeX safety, abbreviation first use, AI-pattern risk, and
   reviewer-readiness.
8. Next-round blockers, or `none`.
9. Confirmation request before producing clean revised text.

Pre-Submission Polish Loop must not declare readiness merely because prose is fluent. It must close
all fixable high-risk reviewer issues from the supplied context or clearly mark the missing
evidence, experiment, citation, hardware detail, baseline detail, or author decision.

Pre-Submission Polish Loop must not return clean paste-ready revised prose until the user confirms
the sentence-level proposal for the current pass.

### Submission Review

Return:

1. Top reviewer risks, ordered by severity.
2. Claim-evidence map for headline claims.
3. Experiment adequacy note covering baselines, scaling, causality, and end-to-end evidence.
4. Reproducibility gap note covering hardware/software, build, launch, workloads, parameters, and artifact details.
5. Closest-work or novelty risk note when relevant.
6. Final self-check verdict covering hard safety, HPC style consistency, AI-pattern risk, and
   reviewer-readiness.
7. Final action list.

## Optional Add-ons

Include these only when requested or clearly necessary:

- Paragraph language rubric: `P# | role: ... | verdict: pass/revise | reason: ...`
- Venue/reviewer-risk note.
- Full five-dimension self-review: contribution, writing clarity, experimental strength,
  evaluation completeness, and method design soundness.
- Detailed reproducibility checklist.
- Detailed figure/table redesign suggestions.

Resolve every `revise` verdict before final output unless missing user-provided evidence or setup
details make that impossible.

## Safety and Fallbacks

1. If required context is missing, state the assumption and proceed with a conservative rewrite.
2. If a claim is unsupported, weaken it, mark it as needing evidence, or remove it.
3. If flow remains weak, use temporary section headers or transition phrases during revision, then
   remove unnecessary scaffolding from the final prose.
4. If the text still reads generic or non-HPC, rerun `references/hpc-prose-polish.md`.
5. Do not invent results, baselines, venues, hardware details, artifact status, citations,
   bottlenecks, mechanisms, system layers, metric types, workload semantics, communication
   patterns, or memory-hierarchy details.

## Maintainer Map

Use this map when updating the skill later:

- Change default behavior in `Mode Selection`, `Default Workflow`, and `Output Contracts`.
- Change language style in `references/hpc-prose-polish.md`; keep only the trigger rule here.
- Change revision workflow in `references/paper-revision-polish.md`.
- Change style-sample or venue-tone calibration in `references/style-calibration.md`.
- Change final gate and self-check reporting in `references/final-self-check.md`.
- Change terminology policy in `references/hpc-terminology.md`; keep only the short rule list here.
- Change section structure in the matching section guide under `references/`.
- Change experiment/reviewer standards in `performance-evidence.md`, `paper-review.md`,
  `reproducibility-artifact.md`, or `venue-reviewer-profile.md`.
- Add examples under `references/examples/` and update `references/examples/index.md`.
- Avoid duplicating detailed guidance in this file and a reference file. Put detail in references;
  keep this file as router, contract, and invariant rules.
- Keep this file short enough to scan quickly. If a new rule needs examples, move the examples to
  `references/`.
