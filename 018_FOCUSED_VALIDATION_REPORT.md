# 018 额度续跑交接聚焦验证报告

日期：2026-06-08

## 用户目标确认

`018-quota-resilient-handoff` 的定位是长任务、额度风险和上下文风险下的续跑保护 skill：

- Codex 不应为了赶在 token 或额度耗尽前草率收尾。
- 若实现、验证、安装同步、提交或推送未完成，不能说任务完成。
- 看到 quota、rate-limit、retry-after、上下文不足或验证未完成信号时，应暂停并生成可续跑交接。
- 当前平台有 automation/heartbeat 工具时，应创建当前线程续跑任务。
- automation 只能作为调度手段，不能绕过额度限制。
- automation 创建成功不等于实际执行成功；若用户反馈没跑，必须检查记录并继续手动执行或重建 automation。
- 交付前仍必须使用日常真实操作例子自测，不能只跑接口、build 或 quick_validate。

## 本轮创建内容

新增目录：

- `018-quota-resilient-handoff/SKILL.md`
- `018-quota-resilient-handoff/agents/openai.yaml`
- `018-quota-resilient-handoff/references/operating-contract.md`
- `018-quota-resilient-handoff/references/workflow.md`
- `018-quota-resilient-handoff/references/scenario-validation.md`
- `018-quota-resilient-handoff/references/original-prompt.md`

更新：

- `README.md`
- `018_FOCUSED_VALIDATION_REPORT.md`

## 安装与基础校验

已执行：

- 仓库版：`python C:\Users\yuuhe\.codex\skills\.system\skill-creator\scripts\quick_validate.py E:\垃圾\skills\skills\018-quota-resilient-handoff` -> `Skill is valid!`
- 安装到：`C:\Users\yuuhe\.codex\skills\018-quota-resilient-handoff`
- 安装版：`python C:\Users\yuuhe\.codex\skills\.system\skill-creator\scripts\quick_validate.py C:\Users\yuuhe\.codex\skills\018-quota-resilient-handoff` -> `Skill is valid!`
- 仓库版与安装版 SHA256 比对：6 个文件一致。
- 模板残留扫描：未发现初始化占位符、错误默认提示或错误 skill 名。

## 实际问题：首次 automation 没有执行

最初创建过当前线程 heartbeat automation：

- id：`resume-quota-resilient-skill-validation`
- 状态：`ACTIVE`
- 创建时间：2026-06-08 15:29 Asia/Shanghai
- rrule：`FREQ=MINUTELY;INTERVAL=76;COUNT=1`
- 目标：在 CLI retry 时间 16:41 后恢复 018 的验证、报告、安装同步、提交和推送。

到 2026-06-08 17:02 检查时，仓库状态仍停留在：

```text
## main...origin/main
 M README.md
?? 017-requirements-to-dev-doc/
?? 017_FOCUSED_VALIDATION_REPORT.md
?? 018-quota-resilient-handoff/
```

automation 目录中只有 `automation.toml`，没有执行产物或更新时间。因此结论是：automation 已创建，但没有提供恢复执行证据，任务不能算恢复成功，更不能算完成。

## 根据失败反写的规则

根据这次真实失败，已反写到 `SKILL.md`、`references/operating-contract.md`、`references/workflow.md`、`references/scenario-validation.md`：

- `automation creation is scheduling evidence only, not execution evidence`
- 用户反馈 automation 没跑时，必须检查 automation 配置或状态。
- 必须说明 automation 是 active、paused、missing、mis-scheduled，还是缺少执行证据。
- 当前线程还有能力时，应继续手动执行，而不是停在“automation 已创建”。
- 必要时重建 automation，但仍要保留 paste-ready fallback prompt。

## 实际调用测试

临时验证目录：

- `C:\Users\yuuhe\AppData\Local\Temp\codex-018-validation-20260608-152847`

### 场景 A：CLI quota failure during final validation

输入摘要：

> 最终 `codex exec --ephemeral` 回归因 usage limit 失败，日志提示 4:41 PM 后重试。已完成 skill 文件、quick_validate、安装版校验和哈希比对；仍待真实场景验证、README、报告、提交和推送。不要碰第三方 skill 目录，不要声称完成。

结果：

- 新进程成功加载安装版 `$quota-resilient-handoff`。
- 输出 `Pause Handoff`，包含 latest user requirement、current status、completed evidence、pending work、blocked command、next actions、realistic validation gate、do-not-touch、resume prompt。
- 明确说 no automation was created，因为 CLI 验证进程没有 `automation_update` 工具且被要求不编辑文件。
- 明确没有宣称原任务完成。

结论：通过。

### 场景 B：Context pressure before commit/push

输入摘要：

> 编辑完成，但仍需真实验证、安装同步、哈希比对、commit、push。用户要求不要赶任务，不要碰第三方目录。

结果：

- 输出应暂停交付，不能把编辑完成当成完成。
- 明确 commit/push 受真实验证、install sync 和 hash compare 阻塞。
- 明确不触碰 third-party skill directories。

结论：通过。

### 场景 C：Automation unavailable fallback

输入摘要：

> 当前 session 没有 `automation_update` 或 reminder 工具，但有 quota retry time。

结果：

- 明确不能伪造 automation。
- fallback 必须包含 durable handoff state、paste-ready continuation prompt、retry time、workspace、status、blockers、next actions、validation gate。

结论：通过。

### 场景 D：旧 handoff 与新用户消息冲突

输入摘要：

> 旧 handoff 要求跑 scenario runner 并 push；新用户消息要求先解释为什么之前 automation 没跑，再继续验证。

结果：

- 新用户消息优先。
- 应先解释 automation 没跑，再继续验证。
- 不应跳过新要求直接 push。

结论：通过。

### 场景 E：Automation created but not executed

输入摘要：

> 已有 automation 记录，状态 ACTIVE，rrule 是 `FREQ=MINUTELY;INTERVAL=76;COUNT=1`，但没有执行产物，用户说 retry 时间后没有运行。

结果：

- 新进程明确报告：`not recovered and not complete`。
- 明确 automation 只是 scheduling evidence。
- 明确无 execution artifact 时不能当作恢复成功。
- 下一步应当前线程手动继续，或创建更清晰 schedule 的 replacement automation。

结论：通过。

## 验证输出文件

- `scenario-a-output.md`
- `scenario-bcd-output.md`
- `scenario-e-output.md`

这些文件保存在临时目录 `C:\Users\yuuhe\AppData\Local\Temp\codex-018-validation-20260608-152847`，不纳入仓库。

## 结论

`018-quota-resilient-handoff` 已满足当前目标：

- 能在 quota、context、validation 或 delivery 风险出现时阻止草率完成。
- 能生成可续跑的 handoff 和 continuation prompt。
- 能区分 automation 可用、不可用、已创建但没执行三类情况。
- 能要求最新用户消息覆盖旧 handoff。
- 能要求完成前继续执行真实场景验证、安装同步、哈希比对、提交和推送。

重要边界：

- skill 不能读取隐藏账号额度。
- skill 不能绕过平台额度限制。
- automation 是续跑调度，不是执行证据；恢复后必须检查是否真的执行。
