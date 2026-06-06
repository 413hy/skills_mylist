---
name: tampermonkey-from-scratch
description: 'Use when designing and implementing a Tampermonkey userscript from scratch, including page analysis, permissions, selectors, interaction behavior, persistence, and real browser validation.'
---

# 从零编写油猴脚本

## Overview

用于从零设计和编写 Tampermonkey 脚本。重点是先理解目标网页和实际用户动作，再写脚本、安装验证、修复选择器和交互问题。

## Trigger

- 用户要写油猴脚本、用户脚本、网页自动化增强。
- 用户提供目标网站、页面流程或希望自动完成的操作。
- 脚本需要 DOM 选择器、按钮注入、数据保存、请求拦截或跨域权限。

## Required Inputs

- 目标 URL、页面截图/HTML、用户手动操作流程。
- 脚本要完成的动作、触发方式、保存数据、权限范围。
- 测试账号、测试页面和可接受的失败处理。

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
