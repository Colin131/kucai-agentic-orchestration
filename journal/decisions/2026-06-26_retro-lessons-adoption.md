# Decision: s01-01 retro 教训采纳裁定

- **date**: 2026-06-26
- **author**: @pm（CTO 当面裁定）
- **status**: accepted
- **source**: [post-mortem](../post_mortems/2026-06-26_s01-01_first-orchestration-round.md) 提出 L1–L5 draft 教训

## Context

s01-01（模板首个真实任务）retro 产出 5 条 draft 教训，retro 按 binding 只写自己 owned paths、未动任何 spec，留 PM/CTO 裁定。CTO 2026-06-26 逐条拍板。

## Decisions

| # | 教训 | 裁定 | 落地 |
|---|---|---|---|
| **L2** | 验 agent 注册看 available-agents 列表，不靠"调用成功"（名字撞内置 `Explore` 会假阳性） | ✅ **采纳** | `CLAUDE.md` 启动 SOP 加第 5 步 |
| **L4** | reviewer 必查 self-justifying 注释 + tautology/自指测试 | ✅ **采纳** | `reviewer.md` 加 binding §5「对抗清单」，锚 s01-01 MAJ-1/MAJ-2 实例 |
| **L1** | 目标 repo 的 CLAUDE.md 优先于 dev.md（worktree 冲突服从目标 repo） | ❌ **否决** | 见下「L1 否决原则」，**不改 dev.md** |
| **L3** | 修复轮触碰并发/全局/锁 → 触发一次有界复审 | ⏸️ **hold（OBSERVATION）** | n=1，不设默认；retro 已标待 ≥2 例同向再议 |
| **L5** | 补 GUI outcome 验证缺口（GOAL_TEMPLATE 两栏 / `qa-gui` slot 配 computer-use） | ❌ **不做** | GUI outcome 验证保持 human-in-loop，不进模板 |

## L1 否决原则（CTO 裁定，binding——防止以后重提）

> **编排整合进某个 repo 后，PM 就是这个 repo 的 owner，我们的规则主导。**

不把 dev / 子 agent 的工作纪律**从属于**目标 repo 自己的 CLAUDE.md。我们的 spec 是权威。

- **默认场景**（模板被 fork / 整合进一个我们拥有的 repo）：我们的规则领先，目标 repo 的旧约定让位。
- **边缘场景**（像 s01-01：给一个我们**不拥有**的外部 repo 贡献 PR）：是否临场服从对方某条约定，是 **PM 在 goal 合同里的一次性判断**，**不是**写进 dev.md 的常设让步条款。s01-01 我对 worktree 的覆盖即属此类一次性判断（且该任务单线本就不需要 worktree，实际无影响）。

→ eng-lessons.md 里 retro 写的 L1 条目，以本裁定为准视为 **rejected**；L5 视为 **dropped**（retro 下次复盘时 reconcile；PM 不直接改 retro 的 owned 文件）。

## Consequences

- 本轮 5 条 → 2 采纳 / 1 否决 / 1 hold / 1 不做。采纳的 2 条都是本轮**有实证**的（L2 = native 假阳性事件；L4 = MAJ-1/MAJ-2 两个 plausible-but-wrong）。
- 维持了 retro 的 n=1 纪律：没有任何"观察类"教训被当默认改动塞进 spec。
