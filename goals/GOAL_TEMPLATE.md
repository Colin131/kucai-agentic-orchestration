# Goal: <imperative title>

> 派工合同。PM 写完 dispatch agent。agent 接到后从这里 unpack。
> **不允许口语化派工**——口语化 = reviewer / retro 无法独立判断 = 团队失明。

## Header

- **goal_id**: `<sprint>-<seq>` (e.g., `s01-03`)
- **title**: `<imperative phrase>`
- **owner**: `@<agent_id>` (e.g., `@dev`)
- **created**: `YYYY-MM-DD`
- **due**: `YYYY-MM-DD` or `inline`
- **priority**: `p0 | p1 | p2`
- **branch**: `feature/<goal_id>_<slug>`
- **estimated_hours**: `<dev/frontend 接 task 时填，PM 先 placeholder>`

---

## Context（为什么做这个）

<3-5 句。包括：用户痛点 / 业务驱动 / 上游决策链接>

---

## Hypotheses（标 "verify don't trust"）

<列 PM 当前持有的假设；标 confidence + 怎么 verify>

- `[verify]` <assumption>: <怎么验证>
- `[trust]` <known fact>: <来源>

---

## Done-when（验收标准）

> 写到"两个独立审查会得同一 pass/fail"的程度。模糊条目 = 自动驳回。

- [ ] <具体 bullet 1>
- [ ] <具体 bullet 2>
- [ ] (代码任务必带) Implemented ≠ Verified 4 件套证据齐
- [ ] (代码任务必带) reviewer cold-context pass
- [ ] (前端必带) a11y + responsive + 错误态 三件套证据
- [ ] (有 qa 时必带) qa outcome pass

---

## Guardrails

### Scope

- **In scope**: <>
- **Out of scope**: <显式列，防 scope creep>

### Stop-and-report 条件

- 发现 <条件> → 暂停 + 写 INBOX WAITING 找 PM，不擅自扩 scope

### 允许 / 禁止

- 允许 push 远端: `yes | no`
- 允许新增依赖: `yes | no | ask first`
- 允许改 `owned_paths` 之外的文件: `no` (默认)
- 允许 surgical edit 跨边界: `no` (默认)

---

## Materials（agent 必读）

- [ ] 这份 goal 合同本身
- [ ] [memory/team-operating-model.md](../memory/team-operating-model.md)
- [ ] [.claude/agents/<owner>/system.md](../.claude/agents/<owner>/system.md)
- [ ] <其他相关文件 / URL>

---

## Self-Report（agent 完成时填）

按对应 agent task.md 的 Self-Report 段填，并贴 PR description。
