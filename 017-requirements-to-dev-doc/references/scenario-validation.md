# Scenario Validation

## Core Principle

Before delivering a requirements document, validate it as an operational handoff. A downstream reader should be able to use the document without the original chat transcript.

## Validation Steps

1. Pick one representative user workflow from the requirement.
2. Read the document as if you are 012/session_0 with no hidden context.
3. Confirm the document states:
   - Goal and problem.
   - Project mode: existing codebase, greenfield/no code yet, unknown, or mixed.
   - Target users or systems.
   - In-scope and out-of-scope work.
   - Current state or source material inspected.
   - Functional requirements.
   - Acceptance criteria.
   - Realistic validation scenarios.
   - Risks, assumptions, and open questions.
   - Known contradictions or conflicts when source materials disagree.
   - Whether 012 should clarify more or split sessions.
4. Check that at least one normal flow, one error or boundary flow, and one validation evidence requirement are present when relevant.
5. For greenfield projects, verify the document says no code exists yet instead of treating the missing repo as a blocker.
6. If a suggested workstream split is included, verify it is labeled as non-binding and does not create worker task files.
7. Fix any missing section or hidden assumption before delivery.

## Delivery Must Include

- Representative workflow used for validation.
- Expected downstream action.
- Actual readiness conclusion: Ready for session planning, Needs clarification, or Draft with open questions.
- Missing items or residual risk.

## Example

For a request like "build a CRM CSV import workflow," the document is not ready unless it tells 012:

- Which CSV sources and columns matter.
- Who imports the CSV and what success looks like.
- How invalid rows, duplicate customers, mapping errors, and export verification should work.
- Which acceptance scenarios prove the flow.
- Whether import, mapping, export, and integration should be separate candidate workstreams.
