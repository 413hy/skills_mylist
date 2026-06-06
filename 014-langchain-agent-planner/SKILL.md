---
name: langchain-agent-planner
description: 'Use before designing or implementing a LangChain Agent: clarify task, tools, memory, inputs, outputs, failure handling, evaluation cases, and scenario validation.'
---

# LangChain Agent 规划

## Overview

用于正式编写 LangChain Agent 前的需求澄清和架构规划。重点是先明确 agent 为什么需要工具、怎样调用、如何失败恢复、如何评估。

## Trigger

- 用户要创建 LangChain Agent。
- 用户有工具调用、RAG、Memory、结构化输出或多步骤推理需求。
- 需求还停留在“做个 agent”层面，需要澄清。

## Required Inputs

- 业务目标、用户输入、期望输出。
- 可用工具/API、数据源、鉴权、Memory 策略。
- 失败处理、延迟预算、评估样例和部署环境。

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
