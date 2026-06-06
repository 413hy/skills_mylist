---
name: multi-agent-architect
description: 'Use when designing a multi-agent system: clarify whether multiple agents are justified, assign roles, communication contracts, orchestration, memory, evaluation, and scenario tests.'
---

# 多 Agent 架构师

## Overview

用于多 Agent 系统架构设计。重点是先判断是否真的需要多 Agent，再设计角色、通信协议、调度、状态、权限和评估方式。

## Trigger

- 用户要设计多 Agent 架构。
- 任务自然包含多个专业角色、审批环节、并行分析或互相校验。
- 用户不确定该拆几个 agent、每个 agent 做什么。

## Required Inputs

- 业务目标、参与角色、任务边界。
- 通信方式、共享状态、工具权限和调度策略。
- 冲突处理、评估样例、成本/延迟约束和失败恢复。

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
