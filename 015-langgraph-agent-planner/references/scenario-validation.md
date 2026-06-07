# Scenario Validation

## Core Principle

Before delivering a final product, feature, code change, script, demo, agent, synchronization result, pull request, or operational document, validate it with a realistic operation that a user or downstream system would actually perform. Do not stop at API, function, build, or command smoke tests.

## Delivery-Class Rule

A delivery-class task is any output the user will rely on directly or hand to another person, system, repository, browser, agent, task tracker, or production-like workflow. This includes code, demos, scripts, agents, pull requests, synchronization results, operational documents, handoff prompts, user stories, architecture plans, and learning materials intended for use.

For delivery-class tasks, do not claim completion from an API smoke test, function call, build success, or command exit code alone. Validate with a realistic daily-use example:

- Login functionality: use a real or reserved test account through the normal UI; verify success, wrong password, session persistence, logout, and protected-route access.
- Browser scripts: run the script on the real or representative page; verify selectors, timing, repeated execution, wrong-page behavior, and visible user outcome.
- Agents or workflows: run representative user requests through the full workflow, including failure or unknown-answer cases.
- Synchronization: write or update the target object, then read it back and compare fields, links, attachments, status, and ownership.
- Documents, prompts, stories, or plans: run one small representative example through the artifact and verify that the next person can act on it.

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
