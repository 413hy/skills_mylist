# 012 Codex 多会话总控聚焦验证报告

日期：2026-06-07

## 用户目标确认

`012-codex-control-multisession` 的定位已明确为需求总控 skill：

- 当前窗口成为 `session_0`，只负责理解需求、读取项目上下文、维护状态、拆分任务、检查交付证据。
- `session_0` 允许读取项目文件，因为用户有时无法完整描述项目需求。
- `session_0` 可以创建只读分析 agents 帮助理解需求，但不直接实现产品代码，不创建实现 agents。
- 需求没问清楚时继续提问，不拆 worker session。
- 需求清楚后先给拆分草案；用户确认或意图明确后再下发 session 任务。
- worker session 自主理解任务，可自行创建 agents 协作、调用已有 skills，必要时创建项目内 child skill。
- 每个 worker session 必须写交付文档，方便 `session_0` 回看进度和证据。

## 本轮优化

### 1. 明确 `session_0` 需求窗口规则

已写入 `012-codex-control-multisession/SKILL.md` 和 `references/workflow.md`：

- `session_0` 是 requirements/control window。
- 可读项目文件、docs、tickets、tests、architecture。
- 可使用只读分析 agents。
- 不直接实现产品功能。
- 需求不清楚时只提澄清问题，不拆 session，不创建任务文件。

### 2. 改为文件式任务分发

已将长 prompt 复制模式降级为 fallback。

默认方式改为：

- `session_0` 在目标项目创建任务目录：`docs/codex-sessions/tasks/`
- 每个 worker session 有一个任务文件：`docs/codex-sessions/tasks/session_n-task.md`
- 用户只需要创建新 Codex 窗口并发送：`请读取 docs/codex-sessions/tasks/session_n-task.md 并执行`

默认路径：

- `session_0` 状态：`docs/codex-sessions/session_0-state.md`
- worker 任务文件：`docs/codex-sessions/tasks/session_n-task.md`
- worker 交付文档：`docs/codex-sessions/session_n-delivery.md`
- 集成检查清单：`docs/codex-sessions/integration-checklist.md`
- 项目内 child skill：`.codex/project-skills/<skill-name>/SKILL.md`

新增模板：

- `012-codex-control-multisession/references/session-task-template.md`

### 3. 强化 worker session 自主创建 agents

已新增 `Agent Need Assessment` 硬规则：

- 每个 worker session 在实现前必须判断是否需要 agents。
- 对复杂、跨文件、多工作流、高风险、验证重的任务，默认应创建至少一个窄范围 agent，除非明确说明为什么不需要。
- agent 可用于只读代码理解、验证计划、UI 检查、API/数据模型检查、风险复核等。
- agent 必须有明确 ownership，且被告知不是唯一在代码库中工作，不得回滚他人改动。
- delivery 文档必须记录 `Agent Need Assessment`、agents used 或为什么没用 agents。

## 实际调用测试

### 测试 1：复杂 SaaS 后台拆分

输入摘要：

> 我想做一个 SaaS 后台，包含登录权限、客户管理、订单管理、报表。当前窗口是需求窗口，不要实现代码；拆分多个 Codex 对话窗口；每个 session 自己判断是否创建 agents、调用 skills、必要时创建 child skill；写交付文档路径。

结果：

- 输出声明当前窗口为 `session_0`。
- 没有直接实现代码。
- 给出 `session_1` 到 `session_5` 的任务拆分。
- 每个 session 都包含 agent、skill、child skill、delivery、真实 UI 验证要求。
- 识别当前仓库不是 SaaS 项目仓库，要求新 session 在真实项目根目录执行。

结论：通过。

### 测试 2：需求不清楚的性能优化

输入摘要：

> 我想优化现有电商项目性能，但没说清楚是前端首屏、接口慢、数据库慢还是构建慢。需求不清楚就继续提问，不要创建 session_n 任务文件。

结果：

- 输出 `session_0` 状态为需求仍在澄清。
- 没有创建 `docs/` 或任务文件。
- 没有开始优化实现。
- 只提出项目目录、关键用户场景、慢的证据、优先级方向等澄清问题。

结论：通过。

### 测试 3：文件式任务分发

输入摘要：

> 我想开发后台系统，包含登录权限、订单管理、运营报表。需求足够清楚。请在当前项目下创建单独目录，为 session_1、session_2、session_3 分别写任务计划文档，并输出文档路径。

结果：

创建了：

- `docs/codex-sessions/session_0-state.md`
- `docs/codex-sessions/integration-checklist.md`
- `docs/codex-sessions/tasks/session_1-task.md`
- `docs/codex-sessions/tasks/session_2-task.md`
- `docs/codex-sessions/tasks/session_3-task.md`

自动检查 3 个 task 文件均包含：

- `Agent Need Assessment`
- 复杂任务默认自主创建 agents 的要求
- `Skill Policy`
- child skill 创建规则
- `docs/codex-sessions/session_n-delivery.md`
- 真实场景验证要求

结论：通过。

测试产生的 `docs/` 目录已从本 skills 仓库清理。实际使用时，`012` 会在目标项目内生成这些任务文件。

## 最终结论

`012-codex-control-multisession` 已符合当前目标：

- 能把当前窗口稳定变成 `session_0` 需求总控窗口。
- 能在需求不清楚时继续提问，不急着拆 session。
- 能在需求清楚时创建文件式 `session_n-task.md` 任务计划。
- 能让用户只发送任务文档路径给新窗口，减少复制长 prompt。
- 能要求各 worker session 自主做 Agent Need Assessment，并在复杂任务中默认创建 agents 协作。
- 能要求 worker sessions 调用已有 skills，必要时创建项目内 child skills。
- 能要求每个 worker session 写 delivery 文档，并用真实场景验证交付。

## 2026-06-07 追加：端到端多 session 模拟

为进一步验证完整闭环，又创建了两个临时 mock 项目做端到端测试。测试目录均在 `%TEMP%` 下，不属于本仓库内容。

### 场景 A：Mock Admin Project

目标：验证 `session_0 -> 多个 session_n task 文件 -> 多个 worker session 并行执行 -> delivery 文档 -> session_0 复核` 的完整流程。

临时项目包含：

- `src/auth.js`
- `src/orders.js`
- `src/reports.js`
- `tests/scenario-smoke.js`

流程：

1. 使用 `$codex-control-multisession` 让 `session_0` 读取项目并生成：
   - `docs/codex-sessions/tasks/session_1-task.md`
   - `docs/codex-sessions/tasks/session_2-task.md`
   - `docs/codex-sessions/tasks/session_3-task.md`
   - `docs/codex-sessions/session_0-state.md`
   - `docs/codex-sessions/integration-checklist.md`
2. 模拟用户创建三个新窗口，分别把任务文件路径交给 `session_1`、`session_2`、`session_3`。
3. 三个 worker session 并行执行并写入：
   - `docs/codex-sessions/session_1-delivery.md`
   - `docs/codex-sessions/session_2-delivery.md`
   - `docs/codex-sessions/session_3-delivery.md`
4. `session_0` 根据三个 delivery 和 integration checklist 做最终复核。

验证结果：

- `session_0` 没有实现产品代码，只生成任务文档和状态文档。
- 三个 task 文件均包含 `Agent Need Assessment`、skills、child skill、delivery 路径、真实场景验证要求。
- 三个 worker session 均写入 delivery。
- 三个 worker session 均记录了 `Agent Need Assessment`。
- 该轮模拟 worker 环境没有 subagent creation tool，因此 delivery 均写明未创建 agents 的原因，并使用人工复核与场景测试补偿。
- `session_0` 复核了三个 delivery 和 integration checklist，并复跑测试。

复跑命令结果：

- `node tests/auth-scenarios.js` -> 通过
- `node tests/order-scenarios.js` -> 通过
- `node tests/report-scenarios.js` -> 通过
- `npm test` -> 通过

发现的问题：

- task 文件原本要求 `Agent Need Assessment`，但当 worker 环境没有 agent 创建工具时，worker 会合理跳过创建 agents。这能记录风险，但还不够强地推动“有能力时必须创建 agents”。

修复：

- 将规则升级为 `Agent Capability Check + Agent Need Assessment`。
- 明确要求：如果 agent/subagent creation 可用，且任务复杂、跨文件、多工作流、高风险或验证重，则必须创建至少一个窄范围 agent。
- 如果 agent creation 不可用，delivery 必须写 `Agent creation unavailable`，并说明补偿性人工复核步骤。
- 明确写入：不能只因为文件少就跳过 agents。

### 场景 B：Mock Inventory Project

目标：验证修复后的任务文档是否会强制写入 `Agent Capability Check` 和“有能力则必须创建 agent”的规则。

临时项目包含：

- `src/inventory.js`
- `src/purchase.js`
- `src/alerts.js`

`session_0` 生成：

- `docs/codex-sessions/tasks/session_1-task.md`
- `docs/codex-sessions/tasks/session_2-task.md`
- `docs/codex-sessions/tasks/session_3-task.md`

自动检查结果：三个 task 文件均包含：

- `Agent Capability Check`
- `Agent Need Assessment`
- agent 可用且任务复杂时必须创建至少一个 agent
- agent 不可用时必须写 `Agent creation unavailable`
- skills 调用规则
- child skill 创建规则
- `docs/codex-sessions/session_n-delivery.md`
- 真实场景验证要求

随后模拟 `session_1` 读取 `docs/codex-sessions/tasks/session_1-task.md` 并执行。

结果：

- `session_1` 在 delivery 中写入 `Agent Capability Check`。
- `session_1` 识别当前 session 具有 `spawn_agent` 能力。
- `session_1` 实际创建了一个只读 inventory interface explorer agent。
- delivery 记录了 agent id、agent 角色、检查范围和建议。
- delivery 同时记录了 skills、测试、真实场景验证、child skill 判断和交付路径。
- `npm test` 通过。

结论：修复后的 `012` 不再只是“允许 session_n 创建 agents”，而是能通过任务文档推动 session_n 在具备能力时实际创建 agents；不具备能力时也必须显式报告并补偿验证。
