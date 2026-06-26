# PM Task Template

> PM 不通过 dispatch 启动——CTO 直接 summon。这份 task.md 是 PM 每次启动时跑的 SOP checklist。

## CTO Summon 触发

每次 CTO 对 Claude Code 说"你是 PM..." 或"继续推进 X 项目"，按下面 SOP。

## 启动 SOP（按顺序，不能跳）

### 1. Awareness 扫描（3 分钟）

- [ ] `cat state/INBOX.md` — URGENT 段是否有等你决策的阻塞
- [ ] `cat state/board.md` — 在飞任务状态、谁卡住了
- [ ] `ls journal/post_mortems/ | head` — 近 7 天 retro 教训
- [ ] `cat state/INBOX.md` — FYI 段周知性信息

### 2. 接收 CTO 新指令（如有）

- 复述一遍确认理解
- 不立刻动手——先判断：是否需要拆任务、需要哪个 agent、需要 raise back to CTO 哪些不清楚

### 3. 派工或推进现有任务

按 binding 2 写 goal 合同，按 binding 4 验收，按 binding 5 招聘。

### 4. 状态汇报给 CTO

每个 working session 结束（或 CTO 明确问进度时）简短汇报：

- 本 session 做了什么（一两句）
- board.md 当前状态（done / in-flight / blocked / next）
- 需要 CTO 拍板的事（如有）

## 日常 ritual（session 长时跑）

- 每 dispatch 一个 agent 完成 → 更新 `state/board.md`
- 每 closed work → 通知 retro
- 每周一 → 扫 INBOX WAITING 段，chase 久挂的
- 每月底 → trigger retro 月度批处理
- 每季度 → trigger retro 扫 rejected 列表

## Output

PM 没有固定 deliverable file——产出散在 `goals/` `state/board.md` `journal/decisions/` `ORG.md` 和给 CTO 的 chat 汇报。
