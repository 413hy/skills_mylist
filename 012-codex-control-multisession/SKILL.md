---
name: codex-control-multisession
description: 'Use when one Codex control session should clarify requirements, maintain a state anchor, split work into numbered sessions, and generate handoff prompts with validation duties.'
---

# Codex 多会话总控

## Overview

用于让一个总控会话只负责需求澄清、上下文压缩、任务拆分和多 session 交接。重点是避免每个 session 乱做，明确边界、产出和验收。

## Trigger

- 用户希望当前窗口作为 session_0 总控。
- 任务较大，需要分给多个 Codex 窗口或多组 agent。
- 用户希望减少上下文膨胀、明确每个 session 的职责。

## Required Inputs

- 总体目标、当前上下文、可拆分模块。
- 每个 session 的职责、输入资料、输出物和禁止事项。
- 集成顺序、验收标准和场景自测要求。

## Required Workflow

1. Start with context discovery. Read the relevant files, docs, tickets, current workspace state, or user-provided material before acting.
2. Produce a short requirement mirror when the task has ambiguity, risk, or implementation impact.
3. Follow `references/operating-contract.md` for hard rules, interaction discipline, failure handling, and evidence standards.
4. Follow the detailed procedure in `references/workflow.md`.
5. If the work creates or changes a product, feature, script, demo, Agent, synchronization result, PR, or other final deliverable, apply the scenario validation gate in `references/scenario-validation.md` before delivery.
6. Preserve the original migrated prompt only as historical reference in `references/original-prompt.md`; current environment rules and the optimized workflow here take priority.

## Scenario Validation Gate

Before saying the work is done, validate each user-facing function with a realistic operation. For example, if a delivered system contains account login, use a real or reserved test account to log in through the normal UI, verify successful login, failed login, session behavior, logout, and protected-route access. Do not replace this with a bare API smoke test.

For non-code deliverables, run a representative sample through the document or workflow. A User Story, handoff prompt, architecture plan, or learning summary is only complete after a small example proves that the next person can act on it.

## Output Contract

- State what was produced or changed.
- List the scenario tests performed with inputs, expected results, actual results, and pass/fail status.
- Call out any functionality that could not be scenario-tested and why.
- Keep unrelated refactors, unrelated documentation, and unsupported assumptions out of scope.

## References

- `references/operating-contract.md` for hard rules, failure handling, and evidence standards.
- `references/workflow.md` for the full operating procedure.
- `references/scenario-validation.md` for realistic self-test requirements and examples.
- `references/original-prompt.md` for the source prompt migrated from the old collection.
