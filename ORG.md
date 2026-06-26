# ORG — 团队花名册

> 这个文件是 PM 维护的实时组织状态。每次招聘、解雇、转岗、改 spec 都要更新这里。

---

## 当前编制（MVP，2026-06-26 立）

### Active（在岗 + 默认可调度）

| Role | Agent ID | Spec | Owner | Joined | Notes |
|---|---|---|---|---|---|
| 项目经理 | `pm` | [.claude/agents/pm/](.claude/agents/pm/) | CTO 直管 | 2026-06-26 | 主线驱动者；不直接写代码 |
| 开发 | `dev` | [.claude/agents/dev/](.claude/agents/dev/) | PM | 2026-06-26 | 写代码、跑测试；必跑 Implemented≠Verified 四件套 |
| 评审 | `reviewer` | [.claude/agents/reviewer/](.claude/agents/reviewer/) | PM | 2026-06-26 | Cold-context 启动；只读 diff+goal |
| 复盘 | `retro` | [.claude/agents/retro/](.claude/agents/retro/) | PM | 2026-06-26 | 每 closed PR / incident 必 fire；写 post_mortems |
| 调研 | `explore` | [.claude/agents/explore/](.claude/agents/explore/) | PM | 2026-06-26 | 只读；输出固定结构笔记 |
| 前端 / UIUX | `frontend` | [.claude/agents/frontend/](.claude/agents/frontend/) | PM | 2026-06-26 | UI + 交互设计；产品交互护城河 |
| 测试 | `qa` | [.claude/agents/qa/](.claude/agents/qa/) | PM | 2026-06-26 | Outcome 把关（vs reviewer 的 process 把关） |

### Slot（spec 落、不算 headcount、按需 instantiate）

| Role | Spec | 招聘触发条件 |
|---|---|---|
| `algo` | [.claude/agents/algo/](.claude/agents/algo/) | 出现需要专业算法设计 / 复杂度分析的任务 |
| `architect` | [.claude/agents/architect/](.claude/agents/architect/) | 跨模块技术选型 / 大重构；PM 一个人 hold 不住时 |
| `devops` | [.claude/agents/devops/](.claude/agents/devops/) | CI / 部署 / 监控成为瓶颈 |
| `data` | [.claude/agents/data/](.claude/agents/data/) | 数据管道 / 报表 / 分析需求 |

---

## 招聘纪律（binding，PM 必读）

1. **每招一个 agent 必须先写"为什么必要"**——不能 "以防万一" 招人。case 落在 `journal/decisions/YYYY-MM-DD_hire_<role>.md` 给 CTO 看
2. **每个 spec 必带 `owned_paths`**——agent 写文件的物理边界，不在白名单里的路径不能写
3. **每个 spec 必带 `cannot_do` 清单**——边界另一面：明确不能做什么（防越权）
4. **PM → CTO 报 case**：哪些任务 PM 自己干不了 / 现有 agent 干不好 / 这个新人能解决什么 / 没活干怎么办
5. **不能堆人**——slot 槽位是默认状态，只有 case 充分才 instantiate

---

## 角色边界速查（谁能写哪些文件）

详见 [memory/team-operating-model.md](memory/team-operating-model.md) 的"角色边界"章节。简要：

- 代码（`src/`、`app/`、...）：**dev / frontend** 写，其他人**只读**
- `journal/decisions/`：**PM** 写
- `journal/post_mortems/`：**retro** 写
- `state/INBOX.md` URGENT：**PM** 写；FYI / WAITING：所有 agent 可写
- `state/board.md`：**PM** 写
- `ORG.md`：**PM** 写（这个文件）
- `memory/team-operating-model.md`：**CTO + PM** 写
- `memory/eng-lessons.md`：**retro** 写

---

## 招聘 / 解雇 / 转 slot 日志

记录所有人事变动，append-only。

| Date | Action | Role | Reason | Decision Doc |
|---|---|---|---|---|
| 2026-06-26 | 初立 MVP 编制 | dev / reviewer / retro / explore / frontend / qa | CTO 拍板 6 人 | [2026-06-26_initial_team.md](journal/decisions/2026-06-26_initial_team.md) |
