# Post-mortems

> retro 写。每个 closed PR / shipped feature / production incident / rejected proposal 都要 fire。

## 文件命名

`YYYY-MM-DD_<target>_<event>.md`

例：

- `2026-07-02_s01-03_closed_pr.md`
- `2026-07-10_login-flow_shipped.md`
- `2026-07-15_db-migration_incident.md`

## 模板

见 [_TEMPLATE.md](_TEMPLATE.md)，按 [retro/system.md](../../.claude/agents/retro/system.md) "Post-mortem 输出强制结构" 段。

## 触发时机

- closed PR / merged feature → 7d
- production incident / rollback → 48h
- PM rejected goal / reviewer reject PR → 7d（简短版）
- 月底批处理：当月所有 closed work 的 calibration delta
- 季度批处理：rejected 列表 follow up
