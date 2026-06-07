# 自建 skills 前向真实调用验证报告

日期：2026-06-07

## 验证范围

本轮只验证本仓库自建 skills：`001-016`。

不验证、也不上传第三方或别人已经做好的 skills，例如 AnySearch、GSAP 系列、PDF Template Generator 等。它们只在 `README.md` 里作为推荐搭配安装项说明。

## 最新用户要求

所有存在交付物的 skill，都必须要求在交付前使用日常真实操作例子进行自测，不能只测试接口、函数、构建命令或单个工具调用是否跑通。

例如登录功能不能只测登录接口返回 200，而要用真实或预留测试账号从正常 UI 入口验证：正确登录、错误密码、会话保持、退出登录、受保护页面访问。

## 验证方式

本轮使用已安装到 `C:\Users\yuuhe\.codex\skills` 的自建 skills，通过新的 `codex exec --ephemeral` 进程逐个触发 skill。

每个 skill 单独跑 3 个接近日常使用的用例，共 48 个用例。判断重点：

- 是否能被新的 Codex 进程识别并触发。
- 输出是否符合该 skill 的真实用途。
- 是否能处理正常、异常、边界或阻塞场景。
- 涉及交付物时，是否明确要求真实场景验证。
- 是否避免用 API smoke test、函数调用成功、build 成功替代用户实际流程验证。

验证输出和日志保存在临时目录：

`%TEMP%\codex-skills-forward-tests`

## 安装与结构校验

| 项目 | 结果 |
|---|---|
| 仓库版 `001-016` `quick_validate.py` | 通过 |
| 安装版 `001-016` `quick_validate.py` | 通过 |
| 安装目录 | `C:\Users\yuuhe\.codex\skills` |
| 仓库版与安装版文件哈希 | 96 个文件一致 |
| 前向调用输出文件 | 48 个 |
| 前向调用日志文件 | 48 个 |
| 真实 loader 加载错误 | 未发现 |

## Skill 理解与验证结果

| 序号 | Skill | 我对用途的理解 | 实际调用用例 | 结果 |
|---:|---|---|---|---|
| 1 | `pr-check-commit-pr` | 提交和 PR 前做范围确认、真实场景自测、提交条件和阻塞判断 | 登录模块提交前检查；README 文档变更 PR；结账 bugfix 但集成测试失败 | 通过 |
| 2 | `user-story-from-materials` | 把零散材料整理成可开发、可测试的 User Story | 登录后台管理订单；30 天 CSV 导出字段未定；删除订单与作废要求冲突 | 通过 |
| 3 | `sync-doc-to-target-system` | 将文档/卡片/故事同步到目标系统，并读回验证字段一致 | 无 Jira 凭据；Notion 同步 Linear 且附件字段不支持；更新已有任务卡并保留字段 | 通过 |
| 4 | `cross-system-alignment` | 对齐需求、代码、任务系统、外部系统的事实和状态 | 登录失败 5 次锁定不一致；README/代码/Jira 环境变量不一致；外部订单金额不一致 | 通过 |
| 5 | `step-by-step-guide` | 每轮只给一个可执行步骤，并等待用户反馈 | `git status` 指导；登录失败先看可见错误；`npm install` 报错排查 | 通过 |
| 6 | `ai-summary-handoff` | 生成可复制给另一个 AI/Codex 的安全交接 Prompt | 登录模块交接；研究任务交接；被阻塞任务交接 | 通过 |
| 7 | `clarify-before-demo` | 需求不清时先问关键问题，确认业务闭环后再做完整 demo 并场景自测 | 模糊后台 demo；CRM demo 需求较完整；支付 demo 高风险边界 | 通过 |
| 8 | `socratic-concept-learning` | 用苏格拉底式提问、短提示和纠偏引导理解概念 | Cookie/Session/JWT；Promise 与 async/await；索引不是缓存 | 通过 |
| 9 | `tampermonkey-from-scratch` | 从目标页面、权限、选择器和交互流程出发设计并验证油猴脚本 | 登录页自动填充；SPA 动态 banner 隐藏；表格导出 CSV | 通过 |
| 10 | `learning-summary-lite` | 把学习内容压缩成精简易懂版，并提供理解自检 | OAuth 流程；React Hooks；数据库索引 | 通过 |
| 11 | `understand-code-before-change` | 修改已有代码前先理解结构和数据流，再做最小改动并真实场景验证 | 登录跳转错误；分页最后一页重复；筛选器显示旧数据 | 通过 |
| 12 | `codex-control-multisession` | 总控会话澄清需求、拆 session、维护状态锚点和验证责任 | 后台系统拆 3 个 session；session 忘记角色纠偏；并行改动 ownership | 通过 |
| 13 | `directory-overview` | 先通过目录树建立项目/知识库地图，并标注推断置信度 | Web 项目目录；monorepo 目录；课程笔记目录 | 通过 |
| 14 | `langchain-agent-planner` | 创建 LangChain Agent 前确认是否必要、工具、记忆、schema、失败处理和评估样例 | 客服知识库 Agent；财务分析 Agent；简单 FAQ 是否过度设计 | 通过 |
| 15 | `langgraph-agent-planner` | 创建 LangGraph 工作流前明确 State、节点、边、中断恢复和完整路径测试 | 报销审批；人工中断后恢复；简单 Linear 任务是否过度设计 | 通过 |
| 16 | `multi-agent-architect` | 先判断是否需要多 Agent，再设计角色、通信、调度和协作剧本验证 | 客服工单多问题；简单 FAQ 单 Agent；代码审查团队 | 通过 |

## 本轮发现并修复的问题

| Skill | 问题 | 修复 |
|---|---|---|
| `007-clarify-before-demo` | 支付 demo 场景会阻止贸然实现，但没有稳定标明风险和范围边界 | 增加高风险 demo 规则：支付、认证、删除、生产集成、敏感数据场景必须明确输出风险和 scope boundary |
| `008-socratic-concept-learning` | 第一轮有时会展开成代码块，影响一步一问；纠偏时有时没有明确“不完全/不等于” | 增加早期回复紧凑规则；第一轮不使用 fenced code block；误解纠偏必须明确写 `不完全`、`不等于` 或等价表达 |
| `010-learning-summary-lite` | 个别总结会漏掉自检问题 | 增加硬性输出规则：必须包含 `Self-check`、`自检问题` 或 `检查问题` 小节，且自检要用真实小例子 |
| `011-understand-code-before-change` | 有时在做代码理解，但没有稳定标出“动手前先理解” | 增加 Code Understanding Gate：改动前必须明确说明先理解代码路径、架构、数据流和测试 |

此前已修复并在本轮回归中再次验证的点：

- `005-step-by-step-guide`：强制每次输出明确的 `Step 1` / `第 1 步`、一个动作、一个反馈项。
- `006-ai-summary-handoff`：固定交接结构，包含 Known Facts、Assumptions、Next Task、Validation Duties、Do Not Do、Remaining Risks。
- `008-socratic-concept-learning`：首轮必须点名目标概念。
- `013-directory-overview`：重要推断必须带 High/Medium/Low 置信度。

## 交付类真实场景验证规则

所有 `001-016` 的 `references/scenario-validation.md` 均已加入 `Delivery-Class Rule`。

所有 `001-016` 的 `references/operating-contract.md` 均已加入硬规则：

> For any final product, feature, script, demo, agent, sync result, pull request, operational document, handoff prompt, user story, or plan, run realistic scenario validation with a daily-use example. API, function, build, or command checks are supporting evidence only.

这意味着以后 AI 调用这些 skill 时，交付代码、demo、脚本、Agent、PR、同步结果、文档、交接 Prompt、User Story、架构计划、学习材料等，都必须带实际使用样例验证。接口、函数、构建或命令通过只能作为辅助证据。

## 结论

`001-016` 已完成安装、结构校验、哈希比对和 48 个前向真实调用用例验证。

本轮验证中发现的问题已经修复，并重新安装、重新校验、重新测试通过。当前这些自建 skills 的结构、触发行为、输出约束和交付前验证要求符合长期使用要求。

## 2026-06-07 追加：012 聚焦验证

针对 `012-codex-control-multisession` 追加了需求总控场景验证，重点验证：

- 当前窗口是否能稳定成为 `session_0` 需求窗口。
- 需求不清楚时是否继续提问且不拆 session。
- 需求清楚时是否在目标项目创建 `docs/codex-sessions/tasks/session_n-task.md`。
- 是否可以让用户只把任务文档路径发给新窗口，而不是复制长 prompt。
- 每个 worker session 是否被要求先做 `Agent Need Assessment`，复杂任务默认自主创建 agents 协作。

详细记录见 `012_FOCUSED_VALIDATION_REPORT.md`。

2026-06-07 又追加了完整多 session 端到端模拟：`session_0` 在临时项目中生成多个 `session_n-task.md`，模拟 worker sessions 读取任务文件、执行任务、写 delivery，再由 `session_0` 复核 delivery 和 integration checklist。该轮测试发现并修复了 agents 创建规则不够硬的问题，现已升级为 `Agent Capability Check + Agent Need Assessment`：agent 能力可用且任务复杂时必须创建至少一个窄范围 agent；不可用时必须在 delivery 写 `Agent creation unavailable`。
