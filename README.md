# AI proposal triage

**Candidate:** Hassam Akram
**Assessment reference:** MATACS-TH-2026-02

**Time actually spent:** 1 hour

## Contents

- [README.md](README.md) — submission details and reading order.
- [WRITEUP.md](WRITEUP.md) — assumptions, scoring policy, worked results and answers to the five questions.
- [diagram/process-flow.png](diagram/process-flow.png) — process from configuration and upload to ranking and award.
- [PROMPTS.md](PROMPTS.md) — exact extraction message templates, input contract and response checks.
- [ranking.json](ranking.json) — expected initial result for all five proposals.

Start with the diagram, then read the write-up and inspect the ranking. No application setup or API key is needed. This is a design submission; there is no prototype or deployment.

## AI use

ChatGPT helped interpret the requirements, draft the design and extraction prompt, create the diagram, and check the ranking calculations. [After reviewing the work, describe one specific AI suggestion you disagreed with or corrected, the change you made, and why.]

## Result at a glance

A ranks first and E second. B does not satisfy the bidder-held licence requirement; C and D are held for review. The ranking is an initial triage result, not an award decision, and the flags must remain visible beside the ranked list.

The write-up distinguishes requirements supplied by the assessment from the proposed scoring scales and evaluation-date assumption. Its scores use only the currently cleared set. A clarification that admits another proposal can change the price or timeline benchmark and therefore requires a new batch ranking.

## Discussing the design

- **Why use AI?** To map varied proposal wording to evidence-backed fields. Code performs gates, arithmetic and ordering.
- **Why is C held?** Its embedded instruction needs review, and its aggregate experience period does not establish the qualifying count. The instruction is ignored; it is not treated as proof of disqualification.
- **Why not give D zero timeline points?** An unknown schedule also prevents confirmation of a hard deadline. Scoring would conceal that uncertainty.
- **Why can A and E change after clarification?** The price and timeline scales depend on the cleared comparison set, so a newly admitted proposal means a new batch and new benchmarks.
- **What if the licence rule changes?** Approve a new criteria version, reconsider B against that rule, review unresolved facts and rerun the entire batch. Do not patch B directly into the old ranking.
- **What would be checked first in an implementation?** Mandatory failures, unknown deadlines, malicious instructions, contradictory evidence, empty eligible sets, tied scores and changes to batch membership or criteria versions.

## Submission

Use a public repository named `matacs-th-2026-02`. Place the files above at its root with the diagram inside `diagram/`. Replace the personal-details and review placeholders before submitting. Submit the repository URL through the Google Form identified in the assessment; a ZIP is only a transfer format, not the submission itself.

Do not include the assessment PDF or its proposal text. Keep the repository public and unchanged until contacted, or for 30 days. Commit genuine work as it is reviewed and changed; do not reconstruct a fictitious commit history.
