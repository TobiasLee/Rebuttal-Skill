# Stage 1B: Prioritized Experiment and Analysis Plan

## Contents

- 1B.1 Experiment priority labels
- 1B.2 Priority scoring heuristic
- 1B.3 Experiment-plan table
- 1B.4 Prefer information-dense experiments
- 1B.5 Separate experiments from clarifications
- Stage 1C: First-Response Output Format

The rebuttal period is time-limited. Do not return an unranked wishlist.

## 1B.1 Experiment priority labels

Assign each proposed action one priority:

### `P0 — Must do now`

Use when:

- it addresses a fatal or major concern;
- the concern is shared or decision-critical;
- the experiment is feasible within the deadline;
- the result will be interpretable even if negative;
- no existing evidence adequately resolves the concern.

### `P1 — High value if time permits`

Use when:

- it substantially strengthens the case;
- it addresses a major single-reviewer concern or shared moderate concern;
- it is feasible after all P0 items;
- it does not jeopardize completion of P0 work.

### `P2 — Nice to have`

Use when:

- it supports a secondary claim;
- it improves completeness but is unlikely to change the decision;
- it is cheap and can run without delaying higher-priority work.

### `P3 — Defer to revision or resubmission`

Use when:

- it requires substantial engineering, data collection, compute, or redesign;
- it cannot be validated reliably before the deadline;
- it answers a low-impact concern;
- a clear scope clarification is sufficient for rebuttal.

### `DO NOT RUN`

Use when:

- the experiment does not address the underlying concern;
- it duplicates existing evidence;
- the result will be uninterpretable due to missing controls;
- it is likely to consume the entire rebuttal period while leaving major concerns
  unresolved;
- it is motivated mainly by anxiety rather than decision value.

## 1B.2 Priority scoring heuristic

Use qualitative judgment, optionally guided by:

`priority_value = decision_impact × sharedness × severity × expected_information_gain × feasibility / cost`

Do not present a pseudo-precise numerical score unless the factors are explicitly
defined. The ranking must be explainable in prose.

## 1B.3 Experiment-plan table

Return a table with these columns:

| Priority | Concern IDs | Underlying question | Proposed experiment or analysis | Why it changes the decision | Minimum viable protocol | Estimated time/cost | Result interpretation | Fallback if not completed |
|---|---|---|---|---|---|---|---|---|

Every proposed experiment must specify:

- the exact reviewer concern it addresses;
- the hypothesis or decision question;
- baseline and control conditions;
- dataset or evaluation subset;
- metric;
- compute or data matching;
- seeds or repeated runs when relevant;
- minimum result needed to support the intended claim;
- what a negative result would imply;
- fallback rebuttal wording.

## 1B.4 Prefer information-dense experiments

Prioritize experiments that answer multiple concerns at once.

Examples:

- a matched-compute comparison may address fairness, efficiency, and baseline
  concerns;
- a multi-seed robustness experiment may address variance, reliability, and
  cherry-picking concerns;
- a cross-domain evaluation may address realism, generalization, and significance;
- a component ablation may address mechanism, novelty, and necessity.

## 1B.5 Separate experiments from clarifications

Not every review comment needs an experiment.

Return three action buckets:

1. **Run now**
2. **Answer with existing evidence or clarification**
3. **Defer to revision or resubmission**

Do not recommend experiments merely to signal effort.

---

# Stage 1C: First-Response Output Format

When the author first supplies reviews, scores, and an abstract, return the following.

## A. Rebuttal viability

- classification: `PROMISING`, `BORDERLINE / UNCERTAIN`, or `LOW EXPECTED RETURN`;
- score-distribution interpretation;
- strongest positive signal;
- strongest negative signal;
- estimated value of further rebuttal work;
- assumptions and missing venue information.

## B. Paper claim map

Extract from the abstract:

- problem;
- main contribution;
- claimed novelty;
- claimed empirical result;
- claimed scope;
- likely acceptance-critical claim.

Flag abstract claims that appear broader than the supplied review evidence.

## C. Underlying-review diagnosis

Use:

| ID | Reviewer | Surface comment | Underlying concern | Alternative interpretation | Confidence | Severity | Sharedness |
|---|---|---|---|---|---|---|---|

For low-confidence rows, explain the ambiguity to the author.

## D. Concern-to-evidence map

| Concern ID | Evidence already available | Evidence missing | Best response mode |
|---|---|---|---|

## E. Prioritized experiment plan

Use the full experiment-plan table and `P0`–`P3` labels.

## F. Time-budget recommendation

When the deadline is known, suggest a practical allocation.

Example:

- first 10%: verify review interpretation and freeze protocols;
- next 60%: execute P0 experiments;
- next 20%: analyze results and draft major responses;
- final 10%: consistency, tone, and length check.

Adjust to the actual situation. Do not allocate time to P2 work before P0 results are
secured.

## G. Author result template

Ask the author to return results in this format:

```text
Experiment ID:
Concern IDs addressed:
Status: completed / failed / partial
Protocol:
Baselines and controls:
Metric:
Number of runs or seeds:
Result:
Uncertainty:
Unexpected findings:
Artifacts or table:
Claim supported:
Claim not supported:
Preferred manuscript change:
```

## H. Resubmission plan, when applicable

For `LOW EXPECTED RETURN`, include:

| Priority | Revision | Reviews addressed | Required work | Expected payoff |
|---|---|---|---|---|

Also include:

- central story to preserve;
- claims to narrow or remove;
- missing evidence needed for the next submission;
- method or evaluation redesign;
- paper-organization changes;
- related-work repositioning;
- reproducibility additions;
- likely new failure modes to test.

---
