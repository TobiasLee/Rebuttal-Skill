# Rebuttal Skill

A structured AI skill that helps authors triage peer reviews, diagnose underlying reviewer concerns, plan rebuttal experiments, and prepare evidence-grounded response material — with the author in control of the final rebuttal. Designed for AI coding assistants (OpenCode, Claude Code, Gemini CLI) to support rigorous, evidence-grounded author responses for venues like NeurIPS, ICML, ACL, and CVPR.

## Before You Use This: Venue Policy on Generative Assistance

This skill helps authors understand and plan responses to peer review. It does **not** produce submission-ready rebuttals, and it must not be used to bypass a venue's rules on generative assistance.

- **Check the current policy of the specific conference or venue** you are submitting to before using this skill. Policies differ across venues and change over time. When in doubt, ask the venue chairs, or restrict the tool to triage and experiment planning.
- **ACL reminder:** ACL-family venues (ACL, NAACL, EACL, EMNLP, and ARR-reviewed venues) require that any use of generative AI tools to create content — including content in review rebuttals — be appropriate and fully disclosed.
- **Language polishing vs. substantive content generation:** the ACL policy distinguishes assistance purely with the language of the paper (paraphrasing or polishing the author's own sentences, like a grammar checker — generally no disclosure required) from substantive content generation (producing new analysis, claims, interpretations, or full response drafts — must be disclosed where permitted, and any use outside the policy's listed cases is considered inappropriate).
- **Authors remain fully responsible** for the correctness of their methods, results, and writing. Anything this skill produces is material for author review, correction, and rewriting — never a submission-ready rebuttal.
- Do not upload confidential material (chair-only notes, meta-reviews not shared with you, or reviewer identities) into any tool.

Policy references:

- ACL Policy on Publication Ethics ("Guidelines for Generative Assistance in Authorship"): https://www.aclweb.org/adminwiki/index.php/ACL_Policy_on_Publication_Ethics
- ARR "AI Writing/Coding Assistance Policy": https://aclrollingreview.org/cfp

## Features

**Two-Stage Workflow**
- **Stage 1 – Triage & Experiment Planning:** Parses reviews into atomic concerns, infers underlying reviewer intent, classifies severity (FATAL → MINOR), and produces a prioritized P0–P3 experiment plan — not an unranked wishlist.
- **Stage 2 – Response Material for Author Review:** Runs after author results arrive. Validates evidence against claimed concerns, prepares responses using a "Direct Answer → Evidence → Revision" structure, and produces a concrete manuscript revision list. Output is a draft for the author to review, rewrite, and finalize — not a submission-ready rebuttal.

**Rebuttal vs. Resubmission Gate (Stage 0)**
- Assesses whether rebuttal is worthwhile (`PROMISING` / `BORDERLINE` / `LOW EXPECTED RETURN`).
- For low-return cases, provides a detailed resubmission roadmap with rejection diagnosis, revision backlog, and next-submission experiment plan.

**Response Patterns**
- Templates for: correcting misunderstandings, acknowledging limitations, reporting experiments, novelty defense, missing baselines, statistical reliability, score-text mismatch, and more.

**Five Output Modes**
- `TRIAGE_AND_EXPERIMENT_PLAN` — before results are available
- `RESULT_INTEGRATION` — after partial results arrive
- `RESPONSE_DRAFT` — response material for the author to review, correct, and rewrite; not a submission-ready rebuttal
- `RESUBMISSION_PLAN` — when rebuttal has low expected return
- `QUALITY_REVIEW` — audit an existing rebuttal draft

**Evidence Integrity**
- Strictly prohibits fabricating values, presenting planned work as completed, or hiding negative results. Uses visible placeholders for missing information.

**Policy Compliance**
- Checks the venue's generative-assistance policy before any drafting, flags required disclosure, keeps the author in control of the final response, and never produces submission-ready rebuttals.

## Usage

This is a skill definition, not a standalone application. Load it in any AI coding assistant that supports skills, then provide your paper's reviews:

```
Analyze this paper's reviews before drafting a rebuttal.

Venue and score scale: [venue, scale, borderline if known]
Venue generative-assistance policy: [link to the current policy of the venue]
Deadline and resources: [time remaining, compute, author bandwidth]
Abstract: [abstract]
Reviews, scores, and confidences: [reviews]

First check the venue's current policy on generative assistance. Then assess
rebuttal viability, infer the underlying concern behind every review comment,
and produce a prioritized P0-P3 experiment and analysis plan...
```

## Required Inputs

| Stage 1 | Stage 2 (additional) |
|---------|---------------------|
| Paper abstract | Completed experiment results |
| All review texts | Exact experimental settings |
| Reviewer scores | Verified manuscript locations |
| Venue & score scale | Changes authors are willing to make |
| Deadline / time remaining | Claims authors are willing to narrow |
| Available compute & bandwidth | |
