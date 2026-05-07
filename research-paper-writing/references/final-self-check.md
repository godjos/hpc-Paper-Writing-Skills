# Final Self-Check Guide

Use this guide as the final gate for final prose, full-paper review, submission readiness, or any
revision that has already passed structure, terminology, evidence, and prose polish. The self-check
is not a second rewrite pass by default. It identifies remaining risks, fixes what can be fixed from
the supplied context, and clearly marks what still needs author evidence.

## Gate Order

Run the checks in this order:

1. Hard safety: no invented results, citations, hardware, baselines, reviewer intent, artifact
   status, or experimental conditions.
2. HPC style consistency: terminology, system layer, workload, metric, units, scale, abbreviations,
   LaTeX safety, and paragraph roles are consistent.
3. Claim/evidence completeness: every major claim has a traceable source or an explicit
   missing-input note.
4. AI-pattern and template risk: the prose does not read like generic generated academic writing.
5. Reviewer-readiness: a skeptical reviewer can identify the contribution, mechanism, evidence
   scope, limitations, and comparison conditions.

## Hard Safety Checklist

Mark any unresolved item as `Revise`:

- Performance claims name the metric, unit, scale, baseline, and condition when available.
- Novelty claims identify the comparison target or are weakened when closest-work context is absent.
- Scalability claims distinguish strong scaling, weak scaling, throughput scaling, or efficiency.
- Artifact and reproducibility claims are backed by supplied build, environment, workload, and launch
  details.
- Reviewer-response claims are supported by supplied manuscript changes or explicitly marked as
  planned work.
- LaTeX commands, citations, references, labels, math, paths, and code-like identifiers are
  preserved.

## HPC Style Consistency

Check that:

1. Each paragraph has one main message.
2. The first sentence states the role or claim clearly.
3. Adjacent sentences connect through cause, contrast, consequence, refinement, or evidence.
4. Specialized terms match the terminology ledger and the correct system layer.
5. Generic nouns such as `performance`, `resources`, `data`, `method`, and `optimization` are
   replaced only when the supplied context supports a more precise term.
6. Abbreviations are expanded on first use unless universally standard for the target venue.
7. Claims remain measured and reviewer-facing.

## AI-Pattern and Template Risk

Flag prose that shows any of these patterns:

1. Overly symmetrical section or paragraph structures that feel mechanically designed.
2. Stock transitions such as `In addition`, `Furthermore`, or `Moreover` repeated without a clear
   logical relation.
3. Evidence-free adjectives such as `efficient`, `robust`, `significant`, `scalable`, or
   `comprehensive`.
4. Mechanical topic sentences that repeat the section title without adding a claim.
5. Generic contribution sentences that could fit many systems papers.
6. A polished but content-light ending that summarizes rather than tightening the paper's claim.

Fix these when the source material gives enough detail. Otherwise mark the exact missing evidence or
author input.

## Reviewer-Readiness Questions

Answer these before claiming readiness:

1. What is the paper's main claim?
2. What evidence supports it?
3. What workload, platform, scale, and baseline bound the evidence?
4. What mechanism explains the result?
5. What limitation or unresolved risk should not be overclaimed?
6. What would the most skeptical reviewer still ask for?

## Report Format

Use this compact report for final checks:

```
Final self-check: Pass/Revise
High-risk issues: ...
Fixed in this pass: ...
Still needs author evidence: ...
Reviewer-readiness: ...
AI-pattern risk: pass/revise | reason: ...
```

Use `Pass` only when all high-risk issues are resolved or explicitly outside the available evidence.
Use `Revise` when the current prose still contains unsupported claims, inconsistent terminology,
LaTeX damage, or generic AI-pattern prose that can be fixed from the supplied context.
