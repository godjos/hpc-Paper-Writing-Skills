# Style Calibration Guide

Use this guide when the user supplies prior writing, a target venue style, reviewer-facing tone
constraints, or asks the paper to preserve the author's voice. The goal is not imitation for its own
sake. The goal is to keep the revision sounding like a careful HPC/systems paper by this author,
instead of a generic AI-polished academic paragraph.

## When to Calibrate

Run style calibration for revision passes, section rewrites, full-paper reviews, and response-letter
work when at least one of these inputs is available:

1. One to three paragraphs from the user's existing draft.
2. A previously accepted paper by the same group.
3. A venue, reviewer profile, or target paper style.
4. User instructions about tone, directness, hedging, or non-native English preservation.

Do not run this guide for small Quick polish requests unless the user explicitly asks for style
matching. Quick polish should stay conservative and evidence-bound.

## Calibration Dimensions

Extract only the dimensions that are visible in the supplied sample:

1. Venue register: formal systems paper, concise workshop paper, artifact appendix, response letter,
   or rebuttal prose.
2. Paragraph rhythm: average length, topic-sentence directness, transition density, and whether
   paragraphs carry one claim or a claim plus evidence.
3. Hedging strength: how often the writing uses `may`, `can`, `tends to`, `we observe`, `we find`,
   or direct causal language.
4. Claim syntax: common shapes such as `We make three contributions`, `Our key observation is`,
   `This design avoids`, or `The results show`.
5. Terminology density: how much the prose relies on workload, platform, parallel model, memory
   hierarchy, network, or artifact terms.
6. Citation habits: citation placement, grouped citations, `e.g.,` patterns, and whether the prose
   names prior systems in the sentence.
7. LaTeX expression: use of macros, math symbols, figure references, algorithm names, and protected
   identifiers.
8. Author voice to preserve: useful directness, concise non-native phrasing, or field-specific
   wording that is technically clear even if not idiomatic.

## Output Format

Use this compact format when style affects the rewrite:

`Style anchors: ...`

`Rewrite boundaries: ...`

`Applied calibration: ...`

Style anchors should name reusable patterns, not quote long passages. Rewrite boundaries should say
what must not be smoothed away, such as a precise term, a cautious hedge, or a direct contribution
sentence.

## Calibration Rules

1. Preserve technical meaning, claim strength, and evidence scope over style matching.
2. Keep useful author directness. Do not replace clear prose with ornamental academic phrasing.
3. Preserve cautious hedges when evidence is incomplete or workload-specific.
4. Do not introduce venue claims, community expectations, citation style, or terminology that is not
   visible in the sample or supplied context.
5. Do not normalize every paragraph into the same template. Vary sentence shape when the source
   already varies naturally.
6. Keep non-native English features only when they are clear, concise, and technically accurate.
   Fix grammar that distracts reviewers or changes perceived rigor.
7. Protect LaTeX commands, citation keys, labels, references, equations, paths, code identifiers, and
   macro names.
8. If the supplied sample is too short or inconsistent, state `style sample insufficient` and use the
   default HPC prose rules instead.

## Anti-Generic Check

Before finalizing calibrated prose, check for these failure patterns:

1. The paragraph starts with a broad field statement instead of the paper's specific problem.
2. The contribution sounds detached from workload, platform, metric, or mechanism.
3. The rewrite replaces concrete system terms with abstractions such as `approach`, `framework`,
   `solution`, or `paradigm`.
4. Every paragraph has the same topic-sentence shape.
5. The prose adds unsupported reviewer-facing confidence, such as `clearly demonstrates`,
   `significantly outperforms`, or `robustly scales`, without evidence.

If any pattern appears, revise toward the supplied sample and `hpc-prose-polish.md`.
