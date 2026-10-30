# Proposal triage design

The tool recommends a review order, not an award. Initially A leads E; B is ineligible; C and D need clarification.

## Assumptions and scoring policy

The brief supplies weights but no scoring scales or evaluation date. Assume 1 January 2026, counting the preceding five years including 1 January 2021. A and E's experience periods qualify; C's aggregate starting in 2020 does not establish a qualifying count. Production freezes the agreed evaluation date rather than using today's date.

Treat budget and deadline as hard limits: exceeding either is ineligible; an unknown value is flagged. Complete, readable proposals must explicitly establish bidder-held licensing, WSIB clearance and liability cover. B fails the stated-licence rule; subcontracting is insufficient. Unreadable or contradictory evidence instead needs review. Proposal claims are not independent verification; documents must be checked before award.

This rubric is proposed admin configuration, approved before evaluation, never inferred by AI. Weights total 100; unresolved required inputs block scoring.

| Criterion | Points calculation |
| --- | --- |
| Relevant experience | `30 × min(qualifying installations / 10, 1)` |
| Price | `25 × lowest eligible price / proposal price` |
| Timeline | `15 × shortest eligible duration / proposal duration` |
| Warranty | `7.5 × min(panel years / 25, 1) + 7.5 × min(workmanship years / 15, 1)` |
| Team and approach | 3.75 each for a named lead, a stated crew, a safety plan and a monitoring plan |

Ten installations and the warranty caps are proposed saturation points, not supplied requirements. A summary's statement that a lead is named counts; no identity is invented. Roof assessments and reporting earn no separate bonus. Unstated team components earn zero after extraction is confirmed complete.

The price and timeline benchmarks use only cleared, eligible proposals in the frozen batch: currently A and E. Prices and durations must be positive and within limits. If none qualify, return review statuses without computing benchmarks. Admitting a held proposal recalculates the whole batch, since the benchmarks may change.

| Proposal | Experience | Price | Timeline | Warranty | Team | Total / outcome |
| --- | ---: | ---: | ---: | ---: | ---: | --- |
| A | 30.00 | 25.00 | 15.00 | 12.50 | 15.00 | **97.50, rank 1** |
| E | 24.00 | 24.54 | 13.85 | 13.50 | 15.00 | **90.88, rank 2** |
| B | — | — | — | — | — | Ineligible: bidder-held licence not established |
| C | — | — | — | — | — | Flagged: embedded instruction; qualifying project dates unclear |
| D | — | — | — | — | — | Flagged: no committed completion time |

Sum unrounded contributions, then round the total to two decimals. A leads on experience, price and schedule; E's longer workmanship warranty does not close that gap. C's embedded instruction neither earns points nor proves misconduct. A reviewer must confirm the extracted facts are unaffected and resolve its experience period. D needs a completion commitment. Neither receives a guessed score or rank.

## 1. AI vs. rules

Plain code checks upload type, size, malware and access, stores a hash, extracts text or runs OCR, and preserves page references. AI converts that text into evidence-backed fields using the selected category's configured field definitions. It does not score or rank. Rules validate the response and evidence, apply eligibility gates, calculate points and sort. AI helps interpret varied wording; arithmetic and acceptance decisions need explicit, testable rules.

## 2. Consistency and explainability

Freeze document hashes, extracted text, confirmed facts, evaluation date, criteria version, rubric, prompt/model version and batch membership. Replaying these inputs through versioned scoring rules gives the same result. Fresh AI extraction can differ even at temperature zero; cache accepted results and review any replacement. Reject unsupported fields rather than trusting model confidence. The reviewer sees each fact beside its page/excerpt, each contribution, formula and benchmark. Equal unrounded totals share a rank; proposal ID provides display order only.

## 3. Human in the loop

An admin approves criteria before use. A reviewer confirms extracted facts and resolves holds before finalising the ranked list. Corrections require evidence and a reason, then trigger a new run. Explicit failures cannot be silently waived: a policy change requires an authorised new criteria version and a complete rerun. The final award may differ from the ranking, but its rationale is recorded separately. Log actor, timestamp, input versions, validation findings, old/new values, review actions, scores and award decision in an append-only audit trail.

## 4. Changing criteria

Editing creates a draft version, leaving historical results intact. Validate weights, field types, units, caps and gates before activation. Mark existing results as using an older version; never mix versions in one ranking. Re-evaluate every proposal under the new version. Reuse confirmed facts only where definitions still match; otherwise extract again and request review. Show the old and new breakdowns before publication.

## 5. Risks and safeguards

- **Wrong extraction or invented facts:** preserve source references, check quotes against stored text, validate units/ranges, and manually verify meaning. Missing or contradictory evidence stays unresolved.
- **Manipulation:** treat documents as untrusted data. Disable model tools, isolate proposals, and validate output against allowed field IDs. Flag detected review instructions; delimiters and keyword checks alone are insufficient protection.
- **Bias:** exclude company reputation and writing quality. Apply the approved rubric equally; record reviewer overrides and inspect recurring differences.
- **Failures and cost:** cap pages/tokens, deduplicate files, allow one schema-repair retry, then hold for review. Never publish a partial extraction as complete.
- **Data exposure:** restrict access by role, encrypt stored documents and set retention limits. This exercise uses fictional inputs only.
