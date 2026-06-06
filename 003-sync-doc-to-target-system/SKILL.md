---
name: sync-doc-to-target-system
description: 'Use when syncing a document, card, story, requirement, or task into a target system while preserving fields, links, status, ownership, and verification evidence.'
---

# 同步文档到目标系统

## Overview

用于把指定内容同步到目标系统，例如 Jira、Linear、Notion、飞书、Confluence 或项目内部系统。重点是字段准确、状态一致、链接可追踪，并在同步后验证目标系统中实际可用。

## Trigger

- 用户要求把文档、卡片、故事、需求同步到某个系统。
- 用户要求更新目标系统中的字段、状态、负责人、标签、链接或附件。
- 用户希望同步后确认两边内容一致。

## Required Inputs

- 源文档位置、目标系统、目标空间/项目/表/库。
- 字段映射、权限、目标对象是否新建或更新。
- 同步后需要验证的关键字段和可接受差异。

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
