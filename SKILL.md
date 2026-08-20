---
name: academic-rebuttal
description: >
  Use when an author has received peer-review comments and scores for an
  academic paper and needs to diagnose underlying reviewer concerns, decide
  whether a rebuttal is worthwhile, plan rebuttal experiments, or prepare
  evidence-grounded response material and revision plans for the author to
  review and finalize. Produces author-review material, never submission-ready
  rebuttals; venue generative-AI policies must be checked before use. Never
  fabricate results, reviewer intent, citations, or manuscript locations.
---

# Academic Rebuttal Skill

## Purpose

Help authors make the best use of a short rebuttal period.

This skill is intentionally **two-stage**:

1. **Triage and experiment planning**
   - Read the abstract, reviews, and scores.
   - Infer the underlying reason behind each review comment.
   - Surface uncertain interpretations to the author.
   - Assess rebuttal viability.
   - Rank the experiments, analyses, and clarifications that are most likely to
     change the decision.

2. **Response material for author review**
   - Run only after the author provides completed results, verified manuscript
     evidence, or explicitly confirms that no additional experiment will be run.
   - Prepare concise response material using **Direct Answer → Evidence →
     Revision**, clearly marked as a draft for the author to review and rewrite.
   - Keep all claims grounded in supplied evidence.
   - The author — not the tool — decides what enters the final submitted
     response and is responsible for venue-policy compliance and disclosure.

The goal is not to answer every sentence equally. The goal is to resolve the few
decision-critical doubts that determine acceptance.

---

# Policy First: Venue Rules on Generative Assistance

Before using this skill, check the **current policy of the specific conference or
venue** the paper is submitted to. Venue policies on generative assistance differ
and change over time. If the policy is unclear, ask the venue chairs, or restrict
the tool to triage and experiment planning only.

ACL-family venues (ACL, NAACL, EACL, EMNLP, ARR-reviewed venues, and others
following the ACL policies) require that any use of generative AI tools to
create content — including content in review rebuttals — be appropriate and
fully disclosed. See the ACL Policy on Publication Ethics, "Guidelines for
Generative Assistance in Authorship," and the ARR "AI Writing/Coding Assistance
Policy":

- https://www.aclweb.org/adminwiki/index.php/ACL_Policy_on_Publication_Ethics
- https://aclrollingreview.org/cfp

## Language polishing vs. substantive content generation

The ACL policy distinguishes them:

| Language polishing | Substantive content generation |
|---|---|
| Paraphrasing or polishing the author's own sentences — like a grammar checker | Producing new analysis, claims, interpretations, or whole response drafts |
| Treated like proofreading; generally does not require disclosure | Must be fully disclosed where permitted; any use outside the policy's listed cases is considered inappropriate |
| The author's content and responsibility are unchanged | Authors remain fully responsible and must verify accuracy and plagiarism |

## Consequences for this skill

- This skill produces **analysis, plans, and response material for the author to
  review, correct, and rewrite**. It never produces a submission-ready rebuttal.
- The author decides what enters the final response and is responsible for any
  disclosure the venue requires.
- Never upload confidential material (chair-only notes, meta-reviews not shared
  with the author, or reviewer identities) into any tool.

---

## Minimum Inputs

The minimum useful input for Stage 1 is:

- paper title, optional;
- paper abstract;
- all review texts;
- reviewer scores;
- reviewer confidence scores, when available;
- venue and score scale, when known;
- rebuttal deadline or remaining time;
- available compute, data, and author bandwidth, when known.

Useful optional inputs:

- manuscript or relevant sections;
- appendix and supplementary material;
- existing tables and experimental logs;
- author interpretation of ambiguous comments;
- rebuttal word or character limit;
- venue policy on new experiments;
- known area-chair or meta-review comments.

For Stage 2, also request:

- completed experiment or analysis results;
- exact experimental settings;
- number of runs or seeds;
- uncertainty estimates, where applicable;
- verified manuscript locations;
- changes the authors are willing to make;
- claims the authors are willing to narrow.

Use visible placeholders when information is missing:

- `[RESULT NEEDED]`
- `[SETTING NEEDED]`
- `[NUMBER OF SEEDS NEEDED]`
- `[MANUSCRIPT LOCATION NEEDED]`
- `[VENUE RULE NEEDS VERIFICATION]`
- `[AUTHOR CONFIRMATION NEEDED]`

Never silently fill missing evidence.

---

# Operating Contract

## Default behavior

When the user initially provides only reviews, scores, and an abstract:

- **Do not immediately write the final rebuttal.**
- First return:
  1. rebuttal viability assessment;
  2. review-intent diagnosis;
  3. prioritized concern matrix;
  4. prioritized experiment and analysis plan;
  5. clarification-only actions;
  6. a result-reporting template for the authors;
  7. resubmission advice when appropriate;
  8. any venue generative-assistance restrictions the policy check surfaced.

After the user provides completed results:

- validate which concerns the results address;
- identify any remaining evidence gaps;
- prepare response material for the author to review, correct, and rewrite —
  not a submission-ready rebuttal;
- include a concrete manuscript revision list;
- report the final word or character count when a limit is supplied;
- flag any disclosure the venue's generative-assistance policy requires.

Exception: if no new experiment is necessary, or the user explicitly asks for a
draft based only on existing evidence, produce a draft but visibly mark every
unsupported or missing claim, and present it as author-review material.

---

# Stage 0: Rebuttal-Versus-Resubmission Gate

Before planning experiments, assess whether rebuttal is a productive use of time.

## 0.1 Normalize the score scale

Do not assume a universal borderline score. Determine, when possible:

- venue;
- score range;
- semantic label for each score;
- approximate acceptance boundary;
- whether the venue uses an area-chair discussion phase;
- whether reviewers can change scores;
- whether new experiments are permitted.

If the borderline is unknown, state that the assessment is provisional.

## 0.2 Estimate rebuttal viability

Classify the situation:

### `PROMISING`

Typical signals:

- at least one reviewer is positive or clearly above borderline;
- negative reviews focus on answerable misunderstandings or missing evidence;
- no reviewer identifies a fatal correctness flaw;
- the central concern can be addressed within the rebuttal period;
- scores and written reviews suggest that one or two resolved doubts may change
  the decision.

Recommended action:

- invest in targeted rebuttal experiments;
- prioritize shared major concerns;
- produce a full response.

### `BORDERLINE / UNCERTAIN`

Typical signals:

- scores cluster around the venue borderline;
- reviews acknowledge meaningful strengths but identify several fixable concerns;
- reviewer intent is ambiguous;
- one decisive experiment or clarification may materially change the case.

Recommended action:

- run only high-value, fast-turnaround experiments;
- prepare a concise rebuttal;
- simultaneously record revisions needed for resubmission.

### `LOW EXPECTED RETURN`

Typical signals:

- **all reviews are below the venue's borderline**;
- there is no positive reviewer or clear advocate;
- multiple reviewers independently question the core premise, correctness,
  novelty, or empirical validity;
- the required evidence cannot be produced reliably during rebuttal;
- resolving the concerns requires redesigning the method, collecting substantial
  new data, or rewriting the paper's central story.

Recommended action:

- explain that rebuttal is unlikely to reverse the outcome and may be less
  productive than resubmission;
- do not encourage rushed, low-quality experiments merely to appear responsive;
- optionally prepare a minimal professional rebuttal to correct factual errors;
- provide an actionable resubmission plan.

Do not declare rejection certain. Use calibrated language such as:

> Based on the current score distribution and the nature of the concerns, the
> expected return from extensive rebuttal work appears low. A short response may
> still correct material misunderstandings, but the higher-value path is likely a
> stronger revision and resubmission.

## 0.3 Required output for a low-return case

Return:

1. **Why rebuttal has low expected value**
2. **What is still worth answering now**
3. **What not to spend time on**
4. **Resubmission diagnosis**
5. **Prioritized revision roadmap**
6. **Recommended new experiments for the next submission**
7. **Recommended claim, framing, and writing changes**
8. **Suggested target-venue considerations**, only when enough information exists

---

# Stage 1: Diagnose the Reviews

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

# Stage 1B: Prioritized Experiment and Analysis Plan

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

# Stage 2: Incorporate Added Results

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

# Stage 2A: Prepare Response Material for Author Review

This stage assembles response material for the author to review, correct, and
rewrite. It does not produce a submission-ready rebuttal: the author decides
what enters the final response and handles venue-required disclosure.

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

# Resubmission Mode

Use resubmission mode when rebuttal has low expected return or the author explicitly
requests it.

## Resubmission output

### 1. Decision diagnosis

Explain the dominant rejection mechanism:

- unclear contribution;
- insufficient evidence;
- technical flaw;
- unfair evaluation;
- weak novelty positioning;
- mismatch between venue audience and paper;
- overclaiming;
- poor writing or organization;
- several independent concerns with no reviewer advocate.

### 2. Preserve / change / remove

Return:

| Preserve | Change | Remove or narrow |
|---|---|---|

### 3. Revision backlog

Rank work as:

- `R0 — Blocks resubmission`
- `R1 — Strongly recommended`
- `R2 — Improves completeness`
- `R3 — Optional polish`

### 4. Next-submission experiment plan

For each experiment, specify:

- hypothesis;
- concern addressed;
- protocol;
- expected information gain;
- cost;
- stopping criterion;
- implication of positive, negative, and null results.

### 5. Story and claim revision

Recommend:

- revised one-sentence contribution;
- revised abstract claim;
- strongest defensible novelty statement;
- claims to narrow;
- limitations to foreground;
- results that should become central;
- results that should move to appendix or be removed.

### 6. Paper-structure revision

Recommend concrete changes to:

- title;
- abstract;
- introduction;
- related work;
- method;
- experimental setup;
- main tables;
- analysis;
- limitations;
- appendix and reproducibility details.

Do not frame resubmission as failure. Frame it as a higher-return path when the
current evidence and score distribution make decision reversal unlikely.

---

# Evidence and Integrity Rules

## Allowed evidence

- supplied abstract and manuscript text;
- exact manuscript locations verified by the author or document;
- completed experiments;
- completed analyses;
- corrected derivations or proofs;
- reproducible numerical summaries;
- citations permitted by venue policy.

## Forbidden behavior

Never:

- invent experimental values;
- invent reviewer quotes;
- invent manuscript locations;
- present planned work as completed;
- imply a reviewer agreed when they did not;
- claim significance without the required test;
- conceal a negative added result;
- state reviewer intent as certain when it is ambiguous;
- promise that a future experiment will succeed;
- recommend a rushed experiment without interpretable controls;
- present generated text as a submission-ready rebuttal;
- skip the venue generative-assistance policy check or fail to flag required
  disclosure to the author.

When uncertain, say so and provide the safest next action.

---

# Tone Rules

Prefer:

- “We agree...”
- “We clarify...”
- “Our presentation may have obscured...”
- “The intended claim is...”
- “The new result shows...”
- “We will narrow...”
- “We will revise...”

Avoid:

- “The reviewer failed to understand...”
- “This is obviously wrong.”
- “The reviewer did not read the paper.”
- “This criticism is unfair.”
- speculation about reviewer motives;
- aggressive requests for score changes;
- repeated ceremonial thanks.

A rebuttal should feel calm, precise, and easy for a neutral chair to audit.

---

# Compression Rules

When above the limit, remove in this order:

1. repeated thanks;
2. repeated reviewer quotations;
3. generic background;
4. adjectives and rhetorical language;
5. duplicate responses across reviewers;
6. low-impact minor comments;
7. implementation detail not needed to interpret the evidence.

Preserve:

- direct answers;
- key numbers;
- comparison controls;
- uncertainty;
- assumptions;
- claim narrowing;
- manuscript changes;
- unresolved limitations.

---

# Output Modes

## Mode 1: `TRIAGE_AND_EXPERIMENT_PLAN`

Use before added results are available.

Return:

1. rebuttal viability;
2. paper claim map;
3. underlying-review diagnosis;
4. prioritized concern matrix;
5. P0–P3 experiment plan;
6. clarification-only actions;
7. time-budget recommendation;
8. author result template;
9. resubmission plan when appropriate.

## Mode 2: `RESULT_INTEGRATION`

Use after some results are supplied.

Return:

1. result validity check;
2. concern-resolution status;
3. remaining gaps;
4. recommendation on further experiments;
5. rebuttal-ready claims;
6. claims that must be narrowed.

## Mode 3: `RESPONSE_DRAFT`

Assemble response material for the author to review, correct, and rewrite:

1. opening summary;
2. merged major-concern responses;
3. reviewer-specific residual responses;
4. grouped minor comments;
5. concrete manuscript revision list;
6. optional confidential chair note;
7. exact word or character count;
8. venue-policy disclosure note, when the venue requires one.

This is **not** a submission-ready rebuttal. The author must verify every claim,
edit or rewrite the text as their own, and ensure the final response complies
with the venue's policy on generative assistance.

## Mode 4: `RESUBMISSION_PLAN`

Return:

1. rejection-mechanism diagnosis;
2. preserve/change/remove table;
3. R0–R3 revision backlog;
4. next-submission experiments;
5. revised paper story;
6. paper-structure changes;
7. venue-fit considerations, when grounded.

## Mode 5: `QUALITY_REVIEW`

Check for:

- missing direct answers;
- incorrect underlying-concern diagnosis;
- unresolved fatal or major concerns;
- unsupported claims;
- weak experimental controls;
- missing uncertainty;
- tone risks;
- repetition;
- missing manuscript locations;
- claim-scope mismatch;
- unfulfilled promised revisions;
- failure to distinguish rebuttal work from resubmission work.

---

# Default Execution Procedure

## First author message

When reviews, scores, and abstract are supplied:

1. parse venue and time constraints;
2. check the venue's current generative-assistance policy and surface any
   restrictions or required disclosures to the author;
3. normalize the score scale;
4. run the rebuttal-versus-resubmission gate;
5. extract the abstract's claim map;
6. split reviews into atomic concerns;
7. infer the underlying reason for each;
8. surface uncertain interpretations;
9. classify severity, sharedness, decision impact, and resolution confidence;
10. identify evidence already available;
11. create the P0–P3 experiment plan;
12. separate clarification-only work from experiments;
13. provide the result-reporting template;
14. provide a resubmission roadmap if expected rebuttal return is low.

## After results arrive

1. validate the protocol and interpretation;
2. map results to concerns;
3. label each concern resolved, partial, or unresolved;
4. decide whether more experiments are worth the remaining time;
5. derive only claims supported by the results;
6. prepare response material using Direct Answer → Evidence → Revision, marked
   for author review and rewriting — not submission-ready text;
7. add exact manuscript changes;
8. check tone and process integrity;
9. count words or characters;
10. compress without removing decision-critical evidence;
11. flag any disclosure the venue's generative-assistance policy requires.

---

# Quality Checklist

## Triage

- [ ] The venue score scale and borderline are identified or marked unknown.
- [ ] The recommendation distinguishes promising, uncertain, and low-return cases.
- [ ] All-below-borderline reviews trigger explicit resubmission consideration.
- [ ] The recommendation is calibrated rather than deterministic.
- [ ] The strongest positive and negative signals are identified.

## Reviewer-intent diagnosis

- [ ] Each surface comment has an underlying decision question.
- [ ] Ambiguous comments include alternative interpretations.
- [ ] Interpretation confidence is visible.
- [ ] The author is shown uncertainty before expensive work is recommended.
- [ ] Shared concerns are merged.

## Experiment plan

- [ ] Every experiment maps to one or more concern IDs.
- [ ] Every experiment has a P0–P3 or DO NOT RUN label.
- [ ] Priority reflects severity, sharedness, decision impact, feasibility, and cost.
- [ ] P0 work is feasible within the rebuttal period.
- [ ] Minimum viable protocols include proper baselines and controls.
- [ ] Negative-result implications are specified.
- [ ] Clarifications are not disguised as experiments.
- [ ] Long-horizon work is deferred to resubmission.

## Response draft

- [ ] The venue's generative-assistance policy was checked and restrictions or
      required disclosures were flagged to the author.
- [ ] The output is presented as author-review material, not a submission-ready
      rebuttal.
- [ ] Major concerns appear before minor comments.
- [ ] Each major response begins with a direct answer.
- [ ] Each empirical claim is supported by supplied evidence.
- [ ] Added results include matched conditions and uncertainty where relevant.
- [ ] Valid limitations are acknowledged.
- [ ] Claims are narrowed when the evidence is insufficient.
- [ ] Revisions are concrete.
- [ ] The response is self-contained.
- [ ] The tone is professional and non-combative.
- [ ] The response fits the venue limit.

## Integrity

- [ ] No result, citation, quotation, or manuscript location is fabricated.
- [ ] Planned work is not presented as completed.
- [ ] Reviewer intent is not overstated.
- [ ] Negative or mixed results are not hidden.
- [ ] Process complaints are separated from technical responses.
- [ ] Every placeholder is visible to the author.

---

# Anti-Patterns

Do not:

- draft a polished final rebuttal before identifying the real concerns;
- present AI-generated text as a submission-ready response without author
  review, rewriting, and a venue-policy check;
- skip the venue's generative-assistance policy check or omit required
  disclosure from the final response;
- treat every reviewer sentence as equally important;
- recommend an unranked list of experiments;
- prioritize easy P2 work over decision-critical P0 work;
- assume ambiguous reviewer intent;
- run experiments that do not answer the underlying question;
- promise broad future work instead of providing current evidence;
- bury the direct answer under background;
- repeat the same response for every reviewer;
- treat all criticism as misunderstanding;
- attack reviewer competence;
- overclaim from a single rushed result;
- spend the entire rebuttal period when all reviews are clearly below borderline
  and the paper needs a substantial revision;
- give up entirely in a low-return case when a concise correction of material
  factual errors is still useful.

---

# Invocation Templates

## Initial triage

> Analyze this paper's reviews before drafting a rebuttal.
>
> **Venue and score scale:** `[venue, scale, borderline if known]`
>
> **Deadline and resources:** `[time remaining, compute, author bandwidth]`
>
> **Venue generative-assistance policy:** `[link to the current policy of the
> venue, or state that it is unknown]`
>
> **Abstract:** `[abstract]`
>
> **Reviews, scores, and confidences:** `[reviews]`
>
> First check the venue's current policy on generative assistance and surface
> any restrictions or required disclosures. Then assess rebuttal viability.
> Infer the underlying concern behind every review comment and visibly flag
> uncertain interpretations. Then produce a prioritized P0–P3 experiment and
> analysis plan based on severity, sharedness, decision impact, feasibility,
> and cost. Separate experiments from clarification work. If all reviews are
> below the venue borderline or there is no plausible path to changing the
> decision, explain that rebuttal may have low expected return and provide an
> actionable resubmission roadmap.

## Added-result integration

> Here are the completed rebuttal experiments and analyses:
> `[results and protocols]`
>
> Validate which reviewer concerns they address, identify remaining gaps, and
> state which claims are supported, unsupported, or need narrowing. Then
> prepare response material for author review using Direct Answer → Evidence →
> Revision. This is not a submission-ready rebuttal: the author must review and
> rewrite it, and comply with the venue's generative-assistance policy,
> including any required disclosure. Do not invent missing settings, results,
> or manuscript locations.

## Resubmission-only mode

> Based on the reviews, scores, abstract, and available results, produce a
> resubmission plan rather than a rebuttal. Diagnose the rejection mechanism,
> rank revisions as R0–R3, propose decisive experiments, revise the paper's core
> story and claims, and give section-level writing recommendations.

---

# Recommended Internal Artifacts

Maintain four working artifacts:

1. **Concern matrix**
   - one row per atomic reviewer concern;
   - includes underlying reason and interpretation confidence.

2. **Experiment ledger**
   - maps P0–P3 experiments to concern IDs, protocol, cost, and result.

3. **Evidence ledger**
   - maps every rebuttal claim to a supplied result or manuscript location.

4. **Revision and resubmission backlog**
   - separates rebuttal-period actions from longer-horizon paper improvements.

These artifacts reduce wasted experiments, unsupported claims, and forgotten
reviewer concerns.
