# Stage 2: Incorporate Added Results

## Contents

- Stage 2: Incorporate Added Results
- Stage 2A: Draft the Rebuttal
- Response Patterns

Run this stage after the author supplies completed results.

## 2.1 Validate each result

For every experiment, check:

- does it actually answer the underlying concern?
- are comparison conditions matched?
- is the metric appropriate?
- are the number of runs and uncertainty adequate?
- is the result positive, negative, mixed, or inconclusive?
- which exact claim can it support?
- does it create a new limitation?
- can it fit within the rebuttal budget?

Never convert an inconclusive result into a positive claim.

## 2.2 Update the concern matrix

Mark each concern:

- `RESOLVED`
- `PARTIALLY_RESOLVED`
- `UNRESOLVED`
- `RESOLVED_BY_CLARIFICATION`
- `CONCEDED_AND_NARROWED`
- `DEFERRED_TO_RESUBMISSION`

## 2.3 Decide what enters the rebuttal

Include results that are:

- decision-relevant;
- methodologically interpretable;
- verified;
- concise enough to explain;
- directly linked to reviewer concerns.

Omit or qualify results that are:

- rushed and unreliable;
- missing a fair control;
- contradictory without enough space to explain;
- irrelevant to the actual underlying concern.

## 2.4 Handle negative or mixed results honestly

A negative experiment can still improve the rebuttal if it supports a narrower,
more credible claim.

Template:

> The requested analysis does not support the broader claim that `[broad claim]`.
> It shows that the gain holds under `[conditions]` but not under `[conditions]`.
> We will narrow the claim in the abstract and conclusion and add this limitation
> explicitly.

---

# Stage 2A: Draft the Rebuttal

## 2A.1 Write for the neutral decision-maker

The immediate addressee is the reviewer, but the real reader may be an area chair,
senior area chair, or editor.

Every major response must make clear:

- what the concern is;
- what the underlying doubt is;
- whether the authors agree, disagree, or partly agree;
- what evidence resolves it;
- what will change in the paper.

## 2A.2 Lead with the answer

Use:

1. **Direct answer**
2. **Evidence**
3. **Revision**

Weak:

> We thank the reviewer for this interesting question. Our method contains...

Strong:

> **Yes. The improvement remains under matched compute.** In the new experiment,
> our method obtains `[X]` versus `[Y]` for Baseline A using the same data,
> backbone, tuning budget, and FLOPs. We will add the result to Table `[N]` and
> clarify the comparison protocol.

## 2A.3 Organize by decision-critical concern

Preferred order:

1. fatal or central technical concerns;
2. shared major concerns;
3. empirical validity and fair comparison;
4. novelty and positioning;
5. generalization, robustness, efficiency, and reproducibility;
6. scope and clarity;
7. minor comments.

Merge shared concerns rather than repeating the same answer reviewer by reviewer,
unless the venue format prevents it.

## 2A.4 Opening summary

Template:

> We thank the reviewers for their careful feedback. They recognize
> `[strength 1]` (R1, R2), `[strength 2]` (R2), and `[strength 3]` (R3).
> The main concerns are **(1)** `[major concern]`, **(2)** `[major concern]`,
> and **(3)** `[major concern]`. We address these below with new evidence and
> concrete revisions.

For a critical review set:

> We thank the reviewers for the detailed feedback. While they raise important
> concerns about `[central issue]`, they also recognize `[merit 1]` and
> `[merit 2]`. We clarify the intended scope, provide the requested evidence where
> feasible, and specify the corresponding revisions below.

Do not manufacture positive reviewer statements.

## 2A.5 Major-response template

### **C1. Descriptive heading — R1, R3**

> **Concern.** Faithful one-sentence paraphrase.

**Response.** Direct answer in the first sentence.

**Evidence.** Result, derivation, existing manuscript evidence, or completed
analysis. Include the comparison conditions and uncertainty needed to interpret it.

**Revision.** Exact change to the paper.

Example:

> **C1. Performance under matched compute — R1, R3**
>
> **Response. Yes, the method remains stronger under matched compute.** Using the
> same data, backbone, optimization budget, and FLOPs, it achieves `[X ± s]`
> versus `[Y ± t]` for the strongest baseline over `[N]` seeds. We will add this
> comparison to Table 2, report per-seed results in Appendix C, and revise
> “consistently superior” to “superior in the evaluated matched-compute settings.”

## 2A.6 Minor comments

Group compactly:

> **Minor comments.** We will define `[term]` at first use (R1), add the missing
> citation to `[work]` (R2), correct Eq. (5) (R2), and expand the implementation
> details in Appendix D (R3).

---

# Response Patterns

## Correcting a misunderstanding

> **The method does not require `[assumption]`; it requires only
> `[actual assumption]`.** This is stated in Section `[N]`, but our presentation
> may have obscured the distinction. We will revise the paragraph and add
> `[example or derivation]`.

## Acknowledging a valid limitation

> **We agree that the current evidence does not establish `[broad claim]`.**
> It supports the narrower claim that `[supported claim]` under `[conditions]`.
> We will narrow the abstract and conclusion and add this limitation to Section
> `[N]`.

## Reporting a completed experiment

> **We completed the requested `[comparison/ablation/robustness test]`.** Under
> matched `[data/compute/tuning]`, our method obtains `[result]` versus
> `[baseline result]` over `[N]` runs. This supports `[specific claim]`. We will
> add the setup and result to `[location]`.

## Experiment cannot be completed reliably

> We agree that this experiment would be informative. Completing it reliably
> requires `[reason]`, and we do not want to report an under-validated result.
> The current evidence supports `[narrow claim]`; we will clarify this scope and
> add the requested experiment to the revision plan.

## Novelty concern

First create a delta table:

| Prior work | Capability or assumption | This paper's difference | Why it matters |
|---|---|---|---|
| Work A | | | |
| Work B | | | |

Then write:

> The contribution is not merely `[common component]`. It is
> **(i)** `[new formulation]`, **(ii)** `[new capability or guarantee]`, and
> **(iii)** `[new empirical or analytical finding]`. Work A differs in
> `[specific distinction]`, while Work B assumes `[specific assumption]`.

Avoid arguing novelty only from an unseen combination of known components.

## Missing baseline or unfair comparison

> We agree that the comparison conditions should be aligned. All methods now use
> the same `[split]`, `[budget]`, `[backbone]`, and `[selection protocol]`.
> Under this protocol, `[result]`. We will make these controls explicit.

## Statistical reliability

> We report `[metric]` over `[N]` independent runs as mean ± standard deviation
> and include `[confidence interval or test]`. The improvement over `[baseline]`
> is `[value]` with `[uncertainty]`.

Do not claim statistical significance without a valid test.

## Score-text mismatch

Keep the public response substantive. When a confidential channel exists, a factual
note may say:

> We respectfully ask the chair to consider whether the numerical score is
> consistent with the review text, which recognizes `[positive assessment]` and
> does not identify `[fatal issue]`.

Do not pressure reviewers to change scores.

## Problematic review-process issue

Separate process concerns from technical disagreement.

Potential categories:

- nonspecific criticism;
- unsupported novelty judgment;
- score-text mismatch;
- unprofessional tone;
- mismatch between review expectations and paper type;
- apparent factual claims unsupported by the paper or cited work.

Use a confidential channel when available:

1. quote only the necessary text;
2. describe the issue factually;
3. reference venue guidelines;
4. explain why it affects fair evaluation;
5. avoid speculating about intent or identity.

---
