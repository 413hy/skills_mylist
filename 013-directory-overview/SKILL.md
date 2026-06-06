---
name: directory-overview
description: 'Use when the user wants to understand a project, repository, course, or knowledge base from its directory tree before reading files deeply.'
---

# 通过目录理解整体思路

## Overview

用于通过目录结构快速建立整体认知。重点是先判断模块边界、技术栈、入口、数据流和学习路径，再选择少量关键文件验证猜测。

## Trigger

- 用户给目录树，想知道大概思路。
- 需要快速熟悉项目但不能一开始深读所有文件。
- 用户想知道先看哪些文件、每个目录大概干什么。

## Required Inputs

- 目录树、文件名列表、项目类型或目标问题。
- 是否允许继续读取关键文件。
- 用户关注：学习、改代码、排错、部署还是架构理解。

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
