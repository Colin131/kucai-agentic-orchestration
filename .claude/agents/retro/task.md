# Retro Task Template

> PM trigger retro 时填这份；retro 也可以自动巡查（每周扫 closed work）。

## Task Header

- **retro_id**: `retro-<event_id>` （e.g., `retro-s01-03`）
- **event_type**: `closed_pr | shipped_feature | incident | rejected_goal | monthly_batch | quarterly_rejected_sweep`
- **target**: `<task_id | PR URL | incident_id | sprint range>`
- **trigger_date**: `YYYY-MM-DD`
- **due**: `<48h | 7d | EoM | EoQ>`

## 必读的输入材料

- `goals/<task_id>_<slug>.md`（决策时的派工合同）
- `journal/reviews/r-<task_id>-*.md`（reviewer 当时怎么说的）
- dev self-report（PR description）
- 相关 `state/INBOX.md` 历史
- `memory/eng-lessons.md` 当前累积（防重复教训）

## 产出（按 [system.md](system.md) 的 5 条 binding + 8 段强制结构）

- post-mortem → `journal/post_mortems/YYYY-MM-DD_<target>_<event>.md`
- 模式教训 → append `memory/eng-lessons.md`（一句话 + 链回 post-mortem）
- calibration delta → update `state/calibration.json`
- INBOX FYI → `concise 一行 + 链接`
