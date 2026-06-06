# 原始 Prompt

> 这是从旧合集迁移过来的原始内容，仅用于保留完整语义。执行时优先遵守 SKILL.md 和 eferences/workflow.md 中的优化后流程。

## 原始 Prompt

### Prompt
```text
【变量区】
- <NEW_STORY_REQUIREMENT> = 这里写本次新增需求

【自动发现规则】
1. 除了 `<NEW_STORY_REQUIREMENT>` 以外，其余上下文请优先从当前工作区自动查找，包括：
   - cards
   - stories
   - spec / PRD / design doc
   - policy / validation / business rules
   - 相关模块、页面、流程
2. 如果上下文不足，请基于现有材料做合理补全，并明确标出假设项。

【理解优先规则】
1. 在开始撰写 User Story 之前，请先确认你已经真正理解我的需求、业务目标、适用范围、依赖上下文和验收方向。
2. 如果存在任何不明确、歧义、规则冲突、上下文不足或需求边界不清的地方，请先停下来向我提问，不要直接开始写文档。
3. 提问时一次只问一个问题。
4. 根据我的回答继续追问，直到你对我的真实需求、目标、文档用途、约束条件和验收预期有至少 95% 的把握，再开始撰写。
5. 在没有达到这个理解程度之前，不要直接输出最终文档，也不要把关键假设当成既定事实。

【任务】
请先使用可用的 skills / templates，根据当前项目中已有的需求材料风格与结构，帮我写一份新的 User Story 文档。

请你完成以下内容：
1. 先理解并继承已有需求材料的上下文、命名风格与文档结构。
2. 输出一份结构完整、可直接落地的新 User Story 文档。
3. 文档中至少包含：
   - Title
   - Background / Context
   - User Story
   - Scope
   - Acceptance Criteria
   - Validation Rules
   - Error / Edge Cases
   - Dependencies / Related Items
   - Out of Scope
4. Acceptance Criteria 必须清晰、可测试、可验收。
5. 请覆盖：
   - 用户操作前置条件
   - 用户操作流程
   - 成功条件
   - 失败提示
   - 取消 / 中断 / 空状态处理
   - 边界情况与异常情况
6. 请使用偏产品 / 交付文档的语言，不要写成纯代码说明。
7. 最终请输出为一份可直接保存为 `.md` 的文档内容。

输出要求：
- 结构清晰
- 表达一致
- 验收明确
- 能直接作为后续开发与测试依据
```

### 变量
- `<NEW_STORY_REQUIREMENT>`：本次新增需求描述

---
