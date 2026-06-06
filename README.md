# 常用 skills 合集

这个仓库只收录自建优化后的 skills：`001-016`。

第三方或别人已经做好的 skills，例如 AnySearch、GSAP 系列、PDF Template Generator 等，不随本仓库上传。它们只在本文档里作为“推荐搭配安装的 skills”列出，避免把别人的 skill 源码重复提交进这个仓库。

## 如何找

- `001-016`：本仓库实际包含的自建 skills。
- `101-114`：推荐搭配安装的第三方/本机已有 skills 编号，只作为索引说明，不对应本仓库目录。
- 自建 skill 目录名带序号，方便肉眼排序；`SKILL.md` 里的 `name` 保持无序号，方便实际调用，例如 `$pr-check-commit-pr`。

## Skill 结构标准

- 每个自建 skill 都有独立目录和 `SKILL.md`。
- `SKILL.md` 必须有 YAML frontmatter：`name` 和 `description`。
- 每个自建 skill 都提供 `agents/openai.yaml`，用于 UI 展示和默认调用提示。
- 每个自建 skill 都提供 `references/operating-contract.md`、`references/workflow.md`、`references/scenario-validation.md`、`references/original-prompt.md`。
- 复杂第三方 skills 应从原作者或本机安装源单独安装，不在本仓库中 vendor 进来。

## 交付物自测要求

自建 skills 已统一加入真实场景自测门槛：凡是交付代码、demo、脚本、Agent、PR、同步结果或最终产品功能，都必须用用户真实会执行的操作样例验证。比如登录功能必须用测试账号从正常入口登录、验证错误密码、会话保持、退出登录和受保护页面访问，不能只测登录接口是否 200。

逐个 skill 的代表性 dry-run 自测记录见 `SELF_TEST_REPORT.md`。逐个 skill 的调用式输入/输出模拟记录见 `CALL_SIMULATION_REPORT.md`。

## 目录

### 本仓库包含的自建优化 skills

> 1. 代码提交与 PR - `001-pr-check-commit-pr/`
> 2. 生成 User Story - `002-user-story-from-materials/`
> 3. 同步文档到系统 - `003-sync-doc-to-target-system/`
> 4. 跨系统一致性对齐 - `004-cross-system-alignment/`
> 5. 一步一步指导 - `005-step-by-step-guide/`
> 6. AI 总结接力 - `006-ai-summary-handoff/`
> 7. 先提问再做 Demo - `007-clarify-before-demo/`
> 8. 苏格拉底式概念学习 - `008-socratic-concept-learning/`
> 9. 从零写油猴脚本 - `009-tampermonkey-from-scratch/`
> 10. 学习内容精简总结 - `010-learning-summary-lite/`
> 11. 先理解代码再改 - `011-understand-code-before-change/`
> 12. Codex 多会话总控 - `012-codex-control-multisession/`
> 13. 通过目录看思路 - `013-directory-overview/`
> 14. LangChain Agent 规划 - `014-langchain-agent-planner/`
> 15. LangGraph Agent 规划 - `015-langgraph-agent-planner/`
> 16. 多 Agent 架构师 - `016-multi-agent-architect/`

### 推荐搭配安装但不随仓库上传的 skills

> 101. AnySearch：实时搜索、垂直检索、URL 内容提取。
> 102. Brainstorming：创意、功能、行为改动前的需求澄清和设计。
> 103. Crypto Contract Trader：币安合约波段分析、执行和监控脚本工作流。
> 104. GSAP Core：GSAP 核心 tween、缓动、stagger 和响应式动画。
> 105. GSAP Frameworks：Vue、Svelte 等框架中的 GSAP 生命周期和清理。
> 106. GSAP Performance：GSAP 动画性能、合成层、布局抖动和卡顿优化。
> 107. GSAP Plugins：GSAP 插件注册和 Flip、Draggable、Observer 等插件能力。
> 108. GSAP React：React/Next.js 中使用 useGSAP、refs 和 cleanup。
> 109. GSAP ScrollTrigger：滚动触发、pin、scrub、视差和 ScrollTrigger 配置。
> 110. GSAP Timeline：GSAP 时间线、position 参数、嵌套和播放控制。
> 111. GSAP Utils：gsap.utils 的 clamp、mapRange、snap、toArray 等工具函数。
> 112. PDF Template Generator：基于 PDF 模板生成 PyQt5 桌面 PDF 填写器。
> 113. Requirements Orchestrator：中文总控需求澄清与多 Codex session 分发。
> 114. Using Superpowers：建立会话开始时检查并调用相关 skills 的纪律。

## 自建 skills 明细

| 序号 | Skill 名称 | 目录 | 用途 |
|---:|---|---|---|
| 1 | 代码提交与 PR | `001-pr-check-commit-pr/` | 提交前检查、真实场景自测、提交、推送并发起 PR。 |
| 2 | 生成 User Story | `002-user-story-from-materials/` | 从材料生成可开发、可测试的 User Story 和验收标准。 |
| 3 | 同步文档到系统 | `003-sync-doc-to-target-system/` | 把文档、卡片或故事同步到目标系统并验证字段一致。 |
| 4 | 跨系统一致性对齐 | `004-cross-system-alignment/` | 对齐代码、需求、任务系统和外部系统状态。 |
| 5 | 一步一步指导 | `005-step-by-step-guide/` | 每轮只推进一个可执行步骤，并等待反馈再继续。 |
| 6 | AI 总结接力 | `006-ai-summary-handoff/` | 把长上下文压缩成可执行、边界清晰的交接 Prompt。 |
| 7 | 先提问再做 Demo | `007-clarify-before-demo/` | 先澄清需求，再交付经过真实场景自测的完整 demo。 |
| 8 | 苏格拉底式概念学习 | `008-socratic-concept-learning/` | 通过提问、类比和纠偏引导用户理解概念。 |
| 9 | 从零写油猴脚本 | `009-tampermonkey-from-scratch/` | 从目标页面和真实操作流程设计、实现、验证油猴脚本。 |
| 10 | 学习内容精简总结 | `010-learning-summary-lite/` | 把指定学习材料总结成精简、易懂、可验证理解的版本。 |
| 11 | 先理解代码再改 | `011-understand-code-before-change/` | 先理解代码结构和数据流，再实施改动并做真实场景自测。 |
| 12 | Codex 多会话总控 | `012-codex-control-multisession/` | 总控会话澄清需求、拆分 session，并要求各 session 回传验证证据。 |
| 13 | 通过目录看思路 | `013-directory-overview/` | 先通过目录建立项目或知识库地图，再抽查关键文件验证推断。 |
| 14 | LangChain Agent 规划 | `014-langchain-agent-planner/` | 创建 LangChain Agent 前澄清工具、记忆、输入输出和评估样例。 |
| 15 | LangGraph Agent 规划 | `015-langgraph-agent-planner/` | 创建 LangGraph 工作流前澄清状态、节点、边、循环和真实流程测试。 |
| 16 | 多 Agent 架构师 | `016-multi-agent-architect/` | 判断是否需要多 Agent，并设计角色、通信、调度和协作剧本验证。 |
