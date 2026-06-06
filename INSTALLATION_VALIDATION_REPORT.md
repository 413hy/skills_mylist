# Codex skills 安装与重载验证报告

日期：2026-06-06

## 验证范围

本轮只验证本仓库自建 skills：`001-016`。

验证目标：

- 将 `001-016` 覆盖复制到 `C:\Users\yuuhe\.codex\skills`。
- 用新的 `codex exec --ephemeral` 进程触发技能，模拟 Codex 重新加载后的真实使用。
- 检查每个 skill 的输出是否符合其用途、输出契约和真实场景自测要求。
- 不把 AnySearch、GSAP 等第三方 skills 上传进本仓库。

## 安装结果

已安装到 Codex skills 目录：

- `C:\Users\yuuhe\.codex\skills\001-pr-check-commit-pr`
- `C:\Users\yuuhe\.codex\skills\002-user-story-from-materials`
- `C:\Users\yuuhe\.codex\skills\003-sync-doc-to-target-system`
- `C:\Users\yuuhe\.codex\skills\004-cross-system-alignment`
- `C:\Users\yuuhe\.codex\skills\005-step-by-step-guide`
- `C:\Users\yuuhe\.codex\skills\006-ai-summary-handoff`
- `C:\Users\yuuhe\.codex\skills\007-clarify-before-demo`
- `C:\Users\yuuhe\.codex\skills\008-socratic-concept-learning`
- `C:\Users\yuuhe\.codex\skills\009-tampermonkey-from-scratch`
- `C:\Users\yuuhe\.codex\skills\010-learning-summary-lite`
- `C:\Users\yuuhe\.codex\skills\011-understand-code-before-change`
- `C:\Users\yuuhe\.codex\skills\012-codex-control-multisession`
- `C:\Users\yuuhe\.codex\skills\013-directory-overview`
- `C:\Users\yuuhe\.codex\skills\014-langchain-agent-planner`
- `C:\Users\yuuhe\.codex\skills\015-langgraph-agent-planner`
- `C:\Users\yuuhe\.codex\skills\016-multi-agent-architect`

## 发现并修复的问题

1. 中文核心说明在 Windows PowerShell 的默认读取路径下会出现乱码。
   - 修复：将真正供 Codex 加载的 `SKILL.md`、`references/workflow.md`、`references/operating-contract.md`、`references/scenario-validation.md`、`agents/openai.yaml` 改为英文 ASCII、无 BOM。
   - 保留：仓库 README 和验证报告仍使用中文，供人阅读。

2. `008-socratic-concept-learning` 首轮输出过短时可能没有点名目标概念。
   - 修复：要求首轮先锚定概念名，再提出第一个苏格拉底式问题。

3. `006-ai-summary-handoff` 输出结构可以更稳定。
   - 修复：补充推荐章节：`Handoff Prompt`、`Known Facts`、`Assumptions`、`Next Task`、`Validation Duties`、`Do Not Do`、`Remaining Risks`。

4. 本机已有的第三方 `crypto-contract-trader` 存在 UTF-8 BOM，导致 Codex reload 日志出现 `failed to load skill`。
   - 修复：只在本机移除该文件 BOM，内容未改动。
   - 说明：该目录不是本仓库内容，不会上传到 GitHub。

## 基础校验

官方 `quick_validate.py` 校验结果：

- `001-016` 全部通过。
- 核心加载文件均为 ASCII 且无 BOM。
- 重载复核后不再出现自建 skills 的加载失败或乱码日志。

## 逐个重载触发验证

| 序号 | Skill | 代表性场景 | 结果 |
|---:|---|---|---|
| 1 | `pr-check-commit-pr` | 登录模块改动提交前检查、PR 准备和真实登录场景自测 | 通过 |
| 2 | `user-story-from-materials` | 从“运营人员登录后台管理订单”材料生成 User Story | 通过 |
| 3 | `sync-doc-to-target-system` | 登录 User Story 同步到 Jira，缺少凭据时输出映射、回查计划和阻塞 | 通过 |
| 4 | `cross-system-alignment` | 需求、代码、Jira 对“失败 5 次锁定账号”描述不一致 | 通过 |
| 5 | `step-by-step-guide` | 用户不会查看 Git 状态，只输出第一步和回传要求 | 通过 |
| 6 | `ai-summary-handoff` | 登录模块半成品交接给另一个 Codex 窗口 | 通过 |
| 7 | `clarify-before-demo` | 带登录后台 demo 需求不明确时先问一个关键问题 | 通过 |
| 8 | `socratic-concept-learning` | 用苏格拉底方式引导理解 Cookie、Session、JWT | 通过 |
| 9 | `tampermonkey-from-scratch` | 为后台登录页设计油猴脚本、`@match`、选择器和页面验证 | 通过 |
| 10 | `learning-summary-lite` | 精简总结 OAuth 授权码、access token、refresh token | 通过 |
| 11 | `understand-code-before-change` | 登录后跳转错误，先理解代码再规划最小改动和验证路径 | 通过 |
| 12 | `codex-control-multisession` | 后台系统拆分登录、订单、报表三个 Codex session | 通过 |
| 13 | `directory-overview` | 根据目录树输出项目地图、置信度和需要抽查的关键文件 | 通过 |
| 14 | `langchain-agent-planner` | 客服知识库 Agent 的工具、记忆、schema 和评估样例规划 | 通过 |
| 15 | `langgraph-agent-planner` | 报销审批 LangGraph workflow 的 State、节点、边和完整路径测试 | 通过 |
| 16 | `multi-agent-architect` | 客服工单“登录不了且订单看不到”的多 Agent 架构与协作剧本 | 通过 |

## 结论

`001-016` 已经可以在 Codex 新进程中被重新加载并按 skill 目标工作。输出形态接近官方 skills：frontmatter 可识别，核心说明可稳定读取，references 按需加载，实际触发输出能体现对应工作流和真实场景自测门槛。
