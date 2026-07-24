# Stage 1: Diagnose the Reviews

## Contents

- 1.1 Split reviews into atomic comments
- 1.2 Infer the underlying reason
- 1.3 Handle uncertain reviewer intent
- 1.4 Distinguish comment classes
- Stage 1A: Concern Severity and Priority

## 1.1 Split reviews into atomic comments

A single reviewer paragraph may contain multiple concerns. Split each into one
atomic issue.

Example:

> “The method is expensive, the comparison to X is unfair, and the novelty over
> Y is unclear.”

becomes:

- C1: computational cost;
- C2: fairness of comparison to X;
- C3: novelty relative to Y.

## 1.2 Infer the underlying reason

For every atomic comment, distinguish:

- **surface comment**: what the reviewer literally wrote;
- **underlying concern**: the decision-relevant doubt behind the wording;
- **evidence that would resolve it**;
- **confidence in the interpretation**.

Common underlying concerns include:

- Is the method technically correct?
- Is the claimed gain caused by an unfair comparison?
- Does the method work beyond a cherry-picked setting?
- Is the contribution genuinely new?
- Is the task important enough?
- Are the conclusions statistically reliable?
- Does the approach scale?
- Is the method reproducible?
- Is the cost justified by the gain?
- Is the claim broader than the evidence?
- Is the reviewer confused because the paper is unclear?
- Is the reviewer applying an expectation that does not match the paper's stated
  contribution?

The underlying-reason analysis is mandatory, not optional.

## 1.3 Handle uncertain reviewer intent

Do not pretend to know what a reviewer meant when multiple interpretations are
plausible.

For uncertain comments, return an **Intent Diagnosis Card**:

### Intent Diagnosis Card

- **Reviewer text:** faithful short quotation or paraphrase
- **Most likely underlying concern:** interpretation A
- **Alternative interpretation:** interpretation B
- **Confidence:** high / medium / low
- **Why uncertain:** missing reference, ambiguous wording, score-text mismatch,
  conflicting statements, or underspecified request
- **Evidence that would answer both interpretations:** preferred when feasible
- **Question for the author:** only when the author's knowledge is necessary
- **Safe response strategy:** wording that remains valid under both interpretations

Example:

> **Reviewer text:** “The evaluation is not realistic.”
>
> **Most likely concern:** the benchmark distribution does not match deployment.
>
> **Alternative concern:** the evaluation omits latency or resource constraints.
>
> **Confidence:** Medium.
>
> **Experiment that addresses both:** add an in-domain deployment-style split and
> report quality together with latency/cost.
>
> **Safe response strategy:** explicitly define the intended deployment setting,
> explain which realism dimensions are evaluated, and acknowledge those not yet
> covered.

Surface this diagnosis to the author before committing scarce resources.

## 1.4 Distinguish comment classes

Label every issue with one primary class:

- `CORRECTNESS`
- `NOVELTY`
- `EMPIRICAL_SUPPORT`
- `FAIR_COMPARISON`
- `MISSING_BASELINE`
- `GENERALIZATION`
- `ROBUSTNESS`
- `STATISTICAL_RELIABILITY`
- `EFFICIENCY`
- `SCALABILITY`
- `REPRODUCIBILITY`
- `SIGNIFICANCE`
- `SCOPE_OR_OVERCLAIM`
- `RELATED_WORK`
- `CLARITY`
- `PRESENTATION`
- `REVIEW_PROCESS`

Also label the likely response mode:

- `NEW_EXPERIMENT`
- `NEW_ANALYSIS`
- `EXISTING_EVIDENCE`
- `CLARIFICATION`
- `CORRECTION`
- `CLAIM_NARROWING`
- `MANUSCRIPT_REVISION`
- `CONFIDENTIAL_CHAIR_NOTE`
- `DEFER_TO_RESUBMISSION`

---

# Stage 1A: Concern Severity and Priority

## 1A.1 Severity

Assign one severity label:

### `FATAL`

If valid and unresolved, the paper's main claim fails.

Examples:

- correctness flaw in the central method;
- data leakage;
- invalid evaluation protocol;
- comparison that makes the primary result uninterpretable;
- central novelty claim contradicted by prior work.

### `MAJOR`

Could cause rejection, but the core paper can survive if resolved.

Examples:

- missing strong baseline;
- generalization gap;
- insufficient ablation for the central mechanism;
- unclear matched-compute comparison;
- weak statistical support.

### `MODERATE`

Affects confidence, scope, or presentation but is unlikely to be independently fatal.

### `MINOR`

Typos, local clarity, formatting, small citation omissions, or non-central requests.

## 1A.2 Decision impact

Estimate how much resolving the issue could change the decision:

- `HIGH`
- `MEDIUM`
- `LOW`

This is not identical to severity. A major concern from a low-confidence outlier
reviewer may have lower expected decision impact than a shared moderate concern.

## 1A.3 Sharedness

Label:

- `ALL_REVIEWERS`
- `MULTIPLE_REVIEWERS`
- `SINGLE_REVIEWER`
- `META_REVIEW_OR_CHAIR`

Shared concerns usually receive higher priority.

## 1A.4 Resolution confidence

Estimate:

- `HIGH`: supplied evidence or a straightforward experiment can answer it;
- `MEDIUM`: likely answerable, but interpretation or result is uncertain;
- `LOW`: requires substantial redesign, unavailable data, or speculative evidence.

---
