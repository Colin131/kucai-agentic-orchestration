# Frontend Task Template

> PM 派 frontend 时填这份；frontend 接 task 后从这里 unpack。

## Task Header

- **task_id**: `<sprint>-<seq>` (e.g., `s01-04`)
- **title**: `<imperative phrase, e.g. "实现 login 表单 + 错误态">`
- **goal_doc**: `goals/<task_id>_<slug>.md`
- **owned_paths_override**: `<如果 PM 临时扩/缩>`
- **estimated_hours**: `<frontend 接 task 时填，诚实>`
- **branch**: `feature/<task_id>_<slug>`
- **design_ref**: `<Figma URL | docs/uiux/<slug>.md | "freestyle">`

## Task Body（从 goal_doc 复制关键段）

### Context（为什么做）

<copy from goal_doc>

### Done-when（验收标准）

- [ ] <feature bullet>
- [ ] a11y：键盘可达 / aria 正确 / 对比度过
- [ ] responsive：手机 / 平板 / 桌面三档
- [ ] 错误态 + loading 态完整
- [ ] 视觉证据（截图 / 录屏）贴 PR
- [ ] reviewer cold-context pass
- [ ] (如有 qa) qa outcome pass

### Guardrails

<copy from goal_doc>

## Frontend Self-Report（完成时填，必须贴 PR description）

- **actual_hours**: `<>`
- **PR URL**: `<>`
- **diff stats**: `<git diff --stat>`
- **三件套证据**：
  - a11y: `<axe/lighthouse score 或手测结果>`
  - responsive: `<三档截图>`
  - 错误态 + loading: `<截图 / 描述>`
- **视觉证据**: `<截图 / 录屏 link>`
- **design 决策**（如有非 trivial）: `<link 到 docs/uiux/decisions/>`
- **遇到的 surprise**: `<>`
- **建议给 reviewer 重点看的部分**: `<>`
