# Dev Task Template

> PM 派工时把这份模板填好（或链到 `goals/<task_id>_<slug>.md`）。dev 接 task 后从这里 unpack。

## Task Header

- **task_id**: `<sprint>-<seq>` （e.g., `s01-03`）
- **title**: `<imperative phrase, e.g. "实现 user login API">`
- **goal_doc**: `goals/<task_id>_<slug>.md`（详细派工合同）
- **owned_paths_override**: `<如果 PM 临时扩/缩了你这次的 owned_paths>`
- **estimated_hours**: `<dev 接 task 时填，诚实>`
- **branch**: `feature/<task_id>_<slug>`

## Task Body（从 goal_doc 复制关键段）

### Context（为什么做这个）

<copy from goal_doc>

### Done-when（验收标准）

- [ ] <bullet>
- [ ] <bullet>
- [ ] 4 件套验证：git status clean + git log 真实 commit + 测试 N 个 pass + 独立冷启动复跑
- [ ] PR 描述含上述证据
- [ ] reviewer cold-context pass

### Guardrails

<copy from goal_doc：scope / stop-and-report 条件 / 是否允许 push 远端 / 是否允许新增依赖>

## Dev Self-Report（完成时填，必须贴 PR description）

- **actual_hours**: `<>`
- **PR URL**: `<>`
- **diff stats**: `<git diff --stat 复制>`
- **测试新增/修改数**: `<>`
- **4 件套证据**：
  - git status: `<paste>`
  - git log: `<paste>`
  - tests: `<N tests, all pass | M fail>`
  - cold rerun: `<command + output 节选>`
- **遇到的 surprise**（非预期复杂 / 简单 / 阻塞）：`<retro 会拿这个>`
- **建议给 reviewer 重点看的部分**：`<诚实标出你不确定的地方>`
