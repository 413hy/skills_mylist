---
name: ai-summary-handoff
description: 'Use when compressing a long conversation or unfinished task into a structured, safe, executable handoff prompt for another AI or another Codex session.'
---

# AI 总结接力

## Overview

用于把长上下文压缩成新 AI 能接手的交接 Prompt。重点是保真、可执行、边界清晰，而不是泛泛总结。

## Trigger

- 当前会话太长，需要交给另一个 AI 或另一个 Codex session。
- 用户要求总结上下文、接力、迁移、继续任务。
- 任务中已有决定、约束、未完成项和验证状态需要保留。

## Required Inputs

- 当前任务目标、已完成内容、未完成内容。
- 关键文件、命令、测试结果、用户偏好和禁止事项。
- 下一位 AI 的平台或能力边界。

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
