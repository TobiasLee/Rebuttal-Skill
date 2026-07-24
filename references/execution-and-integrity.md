# Evidence and Integrity Rules

## Contents

- Evidence and Integrity Rules
- Tone Rules
- Compression Rules
- Output Modes
- Default Execution Procedure
- Quality Checklist
- Anti-Patterns
- Invocation Templates
- Recommended Internal Artifacts

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
- recommend a rushed experiment without interpretable controls.

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

## Mode 3: `FULL_REBUTTAL`

Return:

1. opening summary;
2. merged major-concern responses;
3. reviewer-specific residual responses;
4. grouped minor comments;
5. concrete manuscript revision list;
6. optional confidential chair note;
7. exact word or character count.

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
2. normalize the score scale;
3. run the rebuttal-versus-resubmission gate;
4. extract the abstract's claim map;
5. split reviews into atomic concerns;
6. infer the underlying reason for each;
7. surface uncertain interpretations;
8. classify severity, sharedness, decision impact, and resolution confidence;
9. identify evidence already available;
10. create the P0–P3 experiment plan;
11. separate clarification-only work from experiments;
12. provide the result-reporting template;
13. provide a resubmission roadmap if expected rebuttal return is low.

## After results arrive

1. validate the protocol and interpretation;
2. map results to concerns;
3. label each concern resolved, partial, or unresolved;
4. decide whether more experiments are worth the remaining time;
5. derive only claims supported by the results;
6. draft the rebuttal using Direct Answer → Evidence → Revision;
7. add exact manuscript changes;
8. check tone and process integrity;
9. count words or characters;
10. compress without removing decision-critical evidence.

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

## Rebuttal draft

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
> **Abstract:** `[abstract]`
>
> **Reviews, scores, and confidences:** `[reviews]`
>
> First assess rebuttal viability. Infer the underlying concern behind every
> review comment and visibly flag uncertain interpretations. Then produce a
> prioritized P0–P3 experiment and analysis plan based on severity, sharedness,
> decision impact, feasibility, and cost. Separate experiments from clarification
> work. If all reviews are below the venue borderline or there is no plausible
> path to changing the decision, explain that rebuttal may have low expected
> return and provide an actionable resubmission roadmap.

## Added-result integration

> Here are the completed rebuttal experiments and analyses:
> `[results and protocols]`
>
> Validate which reviewer concerns they address, identify remaining gaps, and
> state which claims are supported, unsupported, or need narrowing. Then draft
> the rebuttal using Direct Answer → Evidence → Revision. Do not invent missing
> settings, results, or manuscript locations.

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
