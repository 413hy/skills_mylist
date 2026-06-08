# 017 需求澄清到开发文档聚焦验证报告

日期：2026-06-08

## 用户目标确认

`017-requirements-to-dev-doc` 的定位是 012 的上游需求澄清 skill：

- 当前窗口用于和用户对话，理清真实需求。
- 允许读取用户给的材料、项目文件、现有 skill、报告或 ticket 来减少反复追问。
- 不实现产品代码。
- 不充当 012 的 `session_0`。
- 不创建 `docs/codex-sessions/tasks/session_n-task.md` worker 任务文件。
- 当需求足够清楚时，输出一份独立的开发需求文档。
- 用户把这份文档交给 `012-codex-control-multisession` 窗口后，012 再继续做 `session_0` 总控、读取项目上下文、决定是否继续澄清或拆分 worker sessions。

## 与 011 和 012 的关系

- 类似 `011-understand-code-before-change`：先理解，再行动；但 017 的行动不是改代码，而是写可移交需求文档。
- 位于 `012-codex-control-multisession` 之前：017 负责压缩需求探索上下文，012 负责基于文档做多会话总控。
- 017 可以给出非绑定的 workstream 建议，但不能提前生成 012 的 worker task 文件。

## 本轮创建内容

新增目录：

- `017-requirements-to-dev-doc/SKILL.md`
- `017-requirements-to-dev-doc/agents/openai.yaml`
- `017-requirements-to-dev-doc/references/operating-contract.md`
- `017-requirements-to-dev-doc/references/workflow.md`
- `017-requirements-to-dev-doc/references/dev-doc-template.md`
- `017-requirements-to-dev-doc/references/scenario-validation.md`
- `017-requirements-to-dev-doc/references/original-prompt.md`

更新：

- `README.md`
- `017_FOCUSED_VALIDATION_REPORT.md`

## 实际调用测试

### 测试 1：模糊需求仍需澄清

输入摘要：

> 帮我做一个后台管理系统，功能之后再说。我想先把需求理清楚，再给 012。

期望：

- 017 不实现代码。
- 017 不创建 `docs/codex-sessions/tasks/`。
- 017 输出当前 requirement mirror。
- 017 只问少量高影响问题，例如目标用户、核心工作流、现有项目路径、必须先完成的业务闭环。

结果：通过。`SKILL.md` 和 `workflow.md` 均要求需求不清楚时只给镜像和 focused questions。

### 测试 2：清晰需求生成可交给 012 的开发文档

输入摘要：

> 我要做 CRM CSV 导入、字段映射、校验和导出，目标是让运营能批量导入客户。请写成给 012 的开发需求文档。

期望：

- 017 输出开发需求文档，而不是 worker session 任务文件。
- 文档包含 Handoff Summary、012 Launch Prompt、目标用户、当前状态、范围、非目标、用户流程、功能需求、数据/权限/集成、验收标准、场景验证计划、风险、开放问题和决策记录。
- 文档说明 012 应读取该文档作为 source of truth，并自行决定继续澄清还是拆 session。

结果：通过。`references/dev-doc-template.md` 已覆盖这些章节。

### 测试 3：用户要求带着缺口继续写

输入摘要：

> 需求还没完全确定，但先帮我写一版文档，开放问题也列进去。

期望：

- 017 不因信息缺口阻塞。
- 文档的 handoff status 标为 `Draft with open questions` 或 `Needs clarification`。
- 开放问题独立列出，不混进验收标准。

结果：通过。`SKILL.md`、`operating-contract.md` 和 `workflow.md` 均写入该规则。

### 测试 4：避免污染 012 上下文

输入摘要：

> 我不想让 012 那个窗口堆积大量澄清上下文，先在这里聊完需求，再把文档发过去。

期望：

- 017 把对话压缩成事实、假设、开放问题、决策和验收场景。
- 最终文档避免依赖“上面聊过”的隐藏上下文。
- 输出 012 启动语。

结果：通过。`SKILL.md` 明确要求 standalone document，`scenario-validation.md` 以“012 没有原始聊天上下文”为验证视角。

## 校验结果

已执行：

- `python C:\Users\yuuhe\.codex\skills\.system\skill-creator\scripts\quick_validate.py .\017-requirements-to-dev-doc` -> `Skill is valid!`
- `rg -n "\[TODO|Use -to-dev-doc|TODO" .\017-requirements-to-dev-doc` -> 无结果。
- `rg -n "\$requirements-to-dev-doc|default_prompt" .\017-requirements-to-dev-doc\agents\openai.yaml` -> 默认调用提示保留 `$requirements-to-dev-doc`。
- 检查 `docs/codex-sessions/tasks/session_n-task.md` 只出现在禁止 017 预创建 worker task 的规则中。
- 安装到 `C:\Users\yuuhe\.codex\skills\017-requirements-to-dev-doc`，安装版 `quick_validate` 通过，仓库版与安装版 7 个文件 SHA256 哈希一致。

## 2026-06-08 追加：参考 012 流程的多场景前向验证

参考会话 `019e970f-0719-79f0-b0c4-e6fbf064eb1a` 中测试 012 的方式，本轮不只做文件存在校验，而是按以下流程验证：

1. 先抽取 012 的测试方法：场景输入、临时 mock 项目、模拟输出、自动检查、发现缺口、反写 skill。
2. 在 `%TEMP%` 下创建多个临时项目或材料目录，不污染 skills 仓库。
3. 对 017 分别模拟“现有代码项目”“从零项目”“模糊需求”“矛盾材料”“带缺口草稿”等输入。
4. 检查生成的开发需求文档是否独立、是否能交给 012、是否没有预创建 `docs/codex-sessions/tasks/`。
5. 对发现的模板缺口反写到 017 的 `SKILL.md` 和 references。

临时验证目录：

- `C:\Users\yuuhe\AppData\Local\Temp\codex-017-validation-20260608-120712`

自动检查结果：

- 生成开发需求文档：4 份。
- 模糊需求场景生成开发需求文档：0 份。
- 任何场景生成 `docs/codex-sessions/tasks/`：0 个目录。
- 4 份开发需求文档均通过章节检查：Handoff Summary、012 Launch Prompt、Requirement Mirror、Current State、Goals、Non-Goals、Scope、User Workflows、Functional Requirements、Acceptance Criteria、Scenario Validation Plan、Suggested Workstream Split For 012、Risks、Open Questions、Decision Log。
- 4 份开发需求文档均未出现依赖隐藏聊天上下文的 `as discussed above`。

### 场景 A：已有代码项目 CRM CSV 导入

临时项目包含：

- `src/importer.js`
- `src/mapper.js`
- `src/exporter.js`

输入摘要：

> 现有 CRM 项目已经有 importer、mapper、exporter 三个模块。我要把 CSV 导入、字段映射、校验和导出整理成给 012 的开发需求文档。

期望：

- 017 先读取已有代码边界。
- 开发文档写明 source materials inspected。
- Current State 说明现有模块和缺失能力。
- Suggested Workstream Split 只能是非绑定草案。
- 不创建 `docs/codex-sessions/tasks/`。

结果：通过。

### 场景 B：从零开始的 Meeting Notes Assistant

临时项目状态：

- 无 `src/`。
- 无既有 repo 架构。
- 只给出产品想法：把会议记录转换成 action items。

期望：

- 017 不因为没有代码就阻塞。
- 文档明确这是 greenfield/no code yet。
- 仍然给出目标用户、工作流、验收标准、场景验证和 012 launch prompt。
- 012 后续可以决定是否继续问技术栈，或是否拆 session。

结果：通过。

发现的问题：

- 原模板没有显式 `Project Mode` 字段。从零项目虽然可以写进 Current State，但不够醒目，012 接手时容易把“没有代码”误读为“信息缺失”。

修复：

- 在 `SKILL.md`、`references/workflow.md`、`references/operating-contract.md`、`references/dev-doc-template.md`、`references/scenario-validation.md` 加入 `Project mode` 规则。
- 明确 greenfield 是有效模式，不应仅因没有 repo/code 阻塞。

### 场景 C：模糊的现有项目 UX 优化

临时项目包含：

- `src/App.jsx`

输入摘要：

> 帮我优化这个项目的用户体验，先理清需求再给 012。

期望：

- 017 不生成开发需求文档。
- 017 不创建 `docs/codex-sessions/tasks/`。
- 017 只输出 requirement mirror 和少量 focused questions。
- 问题聚焦在目标用户、核心工作流、失败证据和成功标准。

结果：通过。该场景生成的 dev requirements 文档数量为 0。

### 场景 D：矛盾材料的 Notes Sync 需求

临时材料包含：

- `docs/product.md`：要求 cloud sync。
- `docs/security.md`：要求 offline-only，数据不得离开设备。

输入摘要：

> 根据这些材料写一份给 012 的需求文档。

期望：

- 017 必须识别矛盾材料。
- Handoff status 应为 `Needs clarification`。
- 文档要求 012 先问哪个来源优先。
- 不创建 worker task。

结果：通过。

发现的问题：

- 原模板没有独立的矛盾材料栏目。虽然 operating contract 要求分离 contradictions，但最终模板没有明确承接位置。

修复：

- 在 `references/dev-doc-template.md` 新增 `Known Contradictions Or Conflicts`。
- 在 `references/scenario-validation.md` 要求当来源冲突时必须检查该栏目。
- 在 `workflow.md` 的 quality gate 中加入“矛盾来源必须独立列出”。

### 场景 E：用户要求带缺口先写 Billing Alerts 草稿

输入摘要：

> 需求还没完全清楚，但先写一版 billing alerts 的文档，开放问题列出来。

期望：

- Handoff status 为 `Draft with open questions`。
- Open Questions 明确列出 provider、alert channel、threshold 等阻塞点。
- Acceptance Criteria 不假装这些问题已解决。
- 012 接手后应继续澄清，而不是直接拆 session。

结果：通过。

### 场景 F：012 接手检查

输入：

- 场景 A/B/D/E 生成的 4 份开发需求文档。

检查点：

- 每份文档都包含 `012 Launch Prompt`。
- 每份文档都告诉 012 下一步是继续澄清或创建 session task。
- Suggested Workstream Split 均标记为 non-binding draft。
- 临时验证目录中没有任何 `docs/codex-sessions/tasks/`。

结果：通过。

## 本轮反写修复

根据多场景测试，已反写：

- `017-requirements-to-dev-doc/SKILL.md`
- `017-requirements-to-dev-doc/references/operating-contract.md`
- `017-requirements-to-dev-doc/references/workflow.md`
- `017-requirements-to-dev-doc/references/dev-doc-template.md`
- `017-requirements-to-dev-doc/references/scenario-validation.md`

关键新增规则：

- 开发需求文档必须标注 `Project mode`：existing codebase、greenfield/no code yet、unknown 或 mixed。
- greenfield 是有效模式，不应仅因没有代码或 repo 阻塞。
- 矛盾材料必须进入 `Known Contradictions Or Conflicts`，不能混进普通风险或验收标准。
- 场景验证必须从“012 没有原始聊天上下文”的角度检查文档是否可用。

## 2026-06-08 追加：修复后回归

修复后又创建了一个较小的 post-fix 临时验证目录：

- `C:\Users\yuuhe\AppData\Local\Temp\codex-017-postfix-validation-20260608-120856`

覆盖：

- existing codebase 文档。
- greenfield/no code yet 文档。
- mixed/contradictory materials 文档。

结果：

- 生成开发需求文档：3 份。
- 生成 `docs/codex-sessions/tasks/`：0 个目录。
- 3 份文档均包含 `Project mode`。
- 3 份文档均包含 `$codex-control-multisession` 的 012 启动语。
- 3 份文档均把 Suggested Workstream Split 标为 `Non-binding draft`。
- 3 份文档均未出现 `as discussed above` 这类隐藏上下文引用。
- 矛盾材料文档包含 `Known Contradictions Or Conflicts`。

## 结论

`017-requirements-to-dev-doc` 已满足目标：在 012 之前承担需求澄清和开发文档生成，把长需求对话压缩成可移交材料，从而降低 012 控制窗口的上下文压力。
