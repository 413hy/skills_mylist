# Scenario Validation

## Core Principle

Validate this skill by simulating real Codex operating failures, not by checking only that files exist or frontmatter parses.

## Delivery-Class Rule

A quota-resilient handoff is itself an operational deliverable. It must prove that another Codex session can resume the real task without hidden context and without falsely treating incomplete work as complete.

## Required Validation Scenarios

Run representative daily-use examples before delivering changes to this skill:

- CLI quota failure during final validation:
  - Input: a repo task where implementation and installation are complete, but the final `codex exec` regression fails with a retry time.
  - Expected: the skill creates a handoff that preserves the latest user requirement, failed command summary, retry time, next validation runner, final sync target, and "do not claim done" rule.
- Context pressure before commit/push:
  - Input: a repo has finished edits but still needs realistic scenario validation, install sync, hash compare, commit, and push.
  - Expected: the handoff marks commit/push as pending and does not call the task complete.
- Automation available:
  - Input: a platform heartbeat/automation tool is available.
  - Expected: the agent creates or updates a continuation attached to the current thread, reports the automation ID or name, and makes clear that creation is scheduling evidence only.
- Automation created but not executed:
  - Input: an automation record exists and is active, but the user reports it did not run and no execution artifact is present.
  - Expected: the agent inspects the automation record, explains that creation did not equal execution, then continues manually or creates a replacement automation instead of claiming the recovery succeeded.
- Automation unavailable:
  - Input: no automation tool is available.
  - Expected: the agent provides a paste-ready resume prompt and durable handoff state.
- Resume from old handoff with newer user message:
  - Input: the handoff says one next action, but the user sends a newer correction.
  - Expected: the newer user instruction wins and the agent updates the plan.

## Validation Evidence

Record:

- scenario name;
- representative input;
- expected behavior;
- actual behavior;
- produced handoff or prompt path;
- pass/fail conclusion;
- fixes made after failures.

Command success, YAML validation, or hash comparison alone is not enough. At least one scenario must prove the resume prompt is actionable by inspecting it for latest requirement, completed evidence, pending work, validation gate, and do-not-touch boundaries.
