# Scenario Validation

## Core Principle

Before delivering a final product, feature, code change, script, demo, agent, synchronization result, pull request, or operational document, validate it with a realistic operation that a user or downstream system would actually perform. Do not stop at API, function, build, or command smoke tests.

## Validation Steps

1. List each user-visible function or business workflow included in the deliverable.
2. Prepare realistic sample data. When an account is needed, use an existing project test account, reserve one, or report the missing account as a blocker.
3. Execute the workflow from the normal entry point: browser page, CLI command, target-system object, agent conversation, or actual sync destination.
4. Check interaction behavior, data changes, permissions, error messages, edge states, refresh behavior, and repeated operations where relevant.
5. Record evidence: operation steps, input data, expected result, actual result, logs, screenshots, links, or command output.
6. Fix failed items and rerun the corresponding scenario.

## Skill-Specific Example

For an expense approval graph, run a 1200-unit reimbursement through submit, rules check, manager approval, finance review, rejection, correction, and resubmission paths.

## Delivery Must Include

- Test account, sample data, or representative input used.
- Normal, error, and boundary flows covered.
- Functions that could not be tested, why they were blocked, and what is needed to test them.
- For static documents, prompts, or plans, one small example proving the artifact can guide real execution.
