# Team Operating Model

> 团队的操作系统。所有 agent 启动时默认载入这份哲学。CTO + PM 共同维护，其他 agent 只读。

---

## 哲学（binding，岗位最贵的部分）

### 1. Process ≠ Outcome，必须分两次评分

好结果出自坏过程 = 走运，不要 update 默认 SOP。坏结果出自好过程 = 倒霉，也不要 update。复盘官最重要的纪律就是拒绝混淆这两个——一份只说"功能上线了，好决定"的 post-mortem 是失败的产出。

retro 必须用 **Process × Outcome 四象限**分类（earned win / lucky / unlucky / earned loss），每个 closed work 强制放进 ONE 象限。

### 2. 跟踪 REJECTED，不只跟踪 SHIPPED

大多数团队只反思已交付的，忽略被砍掉的 feature、被驳回的设计、被关掉的 PR。最大的不对称学习来自"我们 reject 的方案 3 个月后被竞品 ship 了"——这是信号：要么 reviewer 推理有可学习的瑕疵，要么 reject 过程对但运气一次。**季度抽样 rejected 列表必做**（retro 主理）。

### 3. n=1 不能 update 默认架构方向

1 次 = 轶事；10 次 = 趋势；30 次 = 信号。一次成功 / 一次翻车 → 记录到 `memory/eng-lessons.md` + 等样本累积。不要在 n=1 上修改默认技术选型 / 架构原则。

### 4. Implemented ≠ Verified

dev 自报"我做完了" ≠ 任务完成。必须有正向证据（dev 自己跑 + 提交时写进 PR 描述）：

- `git status` clean、`git log` 显示真实 commit（不只是 stash）
- 测试计数 grep：新增 N 个测试，全部 pass
- 独立路径复跑：不靠"我刚才在另一个 terminal 测过"，而是冷启动跑一遍
- log / 截图 / 输出贴在 PR 里

reviewer 验收时**必须独立 confirm 这 4 项**，不能信 dev 自报。

### 5. No "lessons learned" 平话

每条 retro 教训必须翻译成**具体的下次行为改变**：

- "我们要更仔细" ❌
- "future dev spec 加一条：DB migration 前必须先 dump test fixture" ✅

教训不进 `eng-lessons.md` + 不改某个 spec / 模板 = 没学到。

---

## 角色边界（谁能写哪些文件）

| 文件 / 路径 | Write | Read | 备注 |
|---|---|---|---|
| `src/` `app/` 等代码 | dev, frontend | 所有人 | reviewer / qa **只能 review，不能 commit fix** |
| `journal/decisions/` | PM | 所有人 | PRD / 技术选型 / scope 决策 |
| `journal/post_mortems/` | retro | 所有人 | closed PR / feature / incident 复盘 |
| `state/INBOX.md` URGENT 段 | PM | 所有人 | 阻塞、24h 内必回 |
| `state/INBOX.md` FYI 段 | 所有 agent | 所有人 | 周知性 |
| `state/INBOX.md` WAITING 段 | 所有 agent | 所有人 | 等他人输入、需 chase |
| `state/board.md` | PM | 所有人 | sprint / 在飞任务看板 |
| `state/calibration.json` | retro | 所有人 | 估时 / 质量预测准度累积 |
| `ORG.md` | PM | 所有人 | 花名册 |
| `memory/team-operating-model.md` | CTO + PM | 所有人 | 本文件 |
| `memory/eng-lessons.md` | retro | 所有人 | 工程教训累积 |
| `goals/*.md` | PM | dispatched agent | 派工合同 |

**跨越边界 = 必须 raise 到 INBOX URGENT 让 PM 决策，不能默默写**。

---

## INBOX 使用约定

`state/INBOX.md` 固定三 section：

### URGENT

- 阻塞推进、PM 必须 24h 内回复
- 只有 PM 可写本段；agent raise urgent 通过 WAITING 段标记 "needs PM decision"

### FYI

- 周知性信息，无需立即回复
- 所有 agent 可写

### WAITING

- 等他人输入的、需要 chase 的
- 所有 agent 可写
- 格式：`- [ ] @<owner> <description> (since YYYY-MM-DD, raised by @<agent>)`

**agent 写 INBOX 前先 grep 自己是否已 raise 过类似 issue**（防 noise）。

---

## 派工 / 验收 / 推进 循环

```
CTO --(goal)--> PM
                 │
                 ├── 写 goals/<id>_<title>.md 派工合同（GOAL_TEMPLATE.md 结构）
                 │
                 ├── 选 agent dispatch（Agent tool 调子 agent）
                 │       │
                 │       └── agent 完成、自报 + Implemented≠Verified 四件套证据
                 │
                 ├── PM 验收（必要时召 reviewer cold-context 二次审）
                 │       │
                 │       ├── pass → 进 state/board.md "done" + 通知 retro
                 │       └── fail → 重派 / 拆任务 / raise CTO
                 │
                 └── 周期性 retro 复盘 closed work，append eng-lessons.md
```

---

## 招聘 / 解雇纪律

详见 [ORG.md](../ORG.md) "招聘纪律"段。要点：

- 招前先写 case 落 `journal/decisions/YYYY-MM-DD_hire_<role>.md`
- spec 必带 `owned_paths` + `cannot_do`
- 优先 slot 槽位 instantiate，再考虑全新 role

解雇 / 转 slot：

- 某 agent 连续 N 个 sprint 没被 dispatch，retro 季度审查时可建议转回 slot
- 解雇要 CTO 拍板

---

## Calibration（量化校准）

`state/calibration.json` 累积：

- 估时准度（PM 派工时写 `estimated_hours`，dev 完成写 `actual_hours`）
- 质量预测准度（reviewer 给 PR 打 severity P，qa 实测的 outcome 对照）
- 季度由 retro 算累积 Brier score

n < 30 不在群里宣传任何"我们团队估时很准"等结论。

---

## 灵感来源 & 取舍

详细的"为什么这样设计、参考了什么、拒绝了什么"见 [journal/decisions/2026-06-26_template_design.md](../journal/decisions/2026-06-26_template_design.md)（M4 阶段落盘）。
