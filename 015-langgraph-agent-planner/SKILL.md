---
name: langgraph-agent-planner
description: 'Use before designing or implementing a LangGraph Agent or workflow: clarify graph state, nodes, edges, loops, interrupts, persistence, and realistic execution tests.'
---

# LangGraph Agent 规划

## Overview

用于 LangGraph Agent / 工作流图设计前的需求澄清。重点是状态、节点职责、边条件、循环退出、人工中断和可恢复执行。

## Trigger

- 用户要创建 LangGraph Agent 或多节点工作流。
- 任务涉及状态机、循环、分支、人工审批、重试或多 agent 协作。
- 需要先画清楚图结构再写代码。

## Required Inputs

- 业务流程、状态字段、节点职责。
- 边条件、循环退出条件、错误恢复和持久化需求。
- 测试样例、输入输出、人工介入点和验收标准。

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
