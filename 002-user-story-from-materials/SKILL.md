---
name: user-story-from-materials
description: 'Use when turning existing notes, requirements, tickets, discussions, or rough ideas into a complete User Story with acceptance criteria, boundaries, assumptions, and validation examples.'
---

# 基于材料生成 User Story

## Overview

用于把零散材料整理成可以进入交付流程的 User Story。重点是提炼用户目标、业务价值、验收标准、边界和待确认问题，而不是把原文改写成更漂亮的段落。

## Trigger

- 用户给出会议记录、需求片段、任务卡片或旧文档，希望生成新 User Story。
- 用户希望补齐验收标准、边界条件、异常路径和测试建议。
- 项目需要把实现、QA 和产品对齐到同一份故事文档。

## Required Inputs

- 材料来源、目标系统格式、用户角色、业务目标。
- 已知范围、明确排除项、依赖、风险和截止时间。
- 目标读者：产品、开发、QA、外部客户或任务系统。

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
