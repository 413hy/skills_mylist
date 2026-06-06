---
name: pr-check-commit-pr
description: 'Use when preparing code changes for review: inspect the workspace, verify behavior with realistic scenario tests, commit intentionally, push the branch, and open or prepare a pull request.'
---

# 代码提交与 PR

## Overview

用于代码提交前的完整收口：理解需求和变更范围，检查工作区，执行真实场景自测，整理提交，推送分支并发起 PR。这个 skill 的重点不是“能 commit”，而是确认提交出去的东西确实能按用户真实使用方式工作。

## Trigger

- 用户要求提交、自动提交、push、发起 PR 或发布本地改动。
- 用户要求先检查当前分支上的待提交代码。
- 用户希望你确认测试、风险、需求文档和代码实现是否一致后再提交。

## Required Inputs

- 当前分支、目标分支、关联需求/issue/PR 描述。
- 本次变更的功能范围、用户可见流程和不应触碰的文件。
- 可用的测试账号、测试数据、环境变量、启动命令和验收方式。

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
