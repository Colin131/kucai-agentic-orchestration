# ORG — 团队花名册

> 这个文件是 PM 维护的实时组织状态。每次招聘、解雇、转岗、改 spec 都要更新这里。

---

## Agent 格式（native Claude Code wiring）

- **PM = 主 session**：行为来自根目录 [CLAUDE.md](CLAUDE.md)（fork 后打开 claude 即是 PM）。PM 不是子 agent。
- **Active 子 agent**：`.claude/agents/<name>.md` 单文件 + frontmatter（name / description / tools / model）。这是 Claude Code 原生认的格式，用 Agent tool 或 "use the X subagent" 派工。
- **Slot 子 agent**：草稿在 [templates/slot-agents/](templates/slot-agents/)，**未注册**（不可被 dispatch）。招聘 = 复制草稿到 `.claude/agents/<name>.md`。

---

## 当前编制（MVP，2026-06-26 立）

### Active（在岗 + 默认可调度）

| Role | Agent | Spec | Owner | Joined | Notes |
|---|---|---|---|---|---|
| 项目经理 | `pm` | [CLAUDE.md](CLAUDE.md) | CTO 直管 | 2026-06-26 | 主 session；不直接写代码 |
| 开发 | `dev` | [.claude/agents/dev.md](.claude/agents/dev.md) | PM | 2026-06-26 | 写代码、跑测试；必跑 Implemented≠Verified 四件套 |
| 评审 | `reviewer` | [.claude/agents/reviewer.md](.claude/agents/reviewer.md) | PM | 2026-06-26 | Cold-context；无 Write 工具（工具层强制只读） |
| 复盘 | `retro` | [.claude/agents/retro.md](.claude/agents/retro.md) | PM | 2026-06-26 | 每 closed work 必 fire；写 post_mortems |
| 调研 | `explore` | [.claude/agents/explore.md](.claude/agents/explore.md) | PM | 2026-06-26 | 无 Write 工具（强制只读）；输出结构化笔记 |
| 前端 / UIUX | `frontend` | [.claude/agents/frontend.md](.claude/agents/frontend.md) | PM | 2026-06-26 | UI + 交互；产品交互护城河 |
| 测试 | `qa` | [.claude/agents/qa.md](.claude/agents/qa.md) | PM | 2026-06-26 | Outcome 把关（vs reviewer 的 process 把关） |

### Slot（草稿落、不算 headcount、未注册）

| Role | Draft | 招聘触发条件 |
|---|---|---|
| `algo` | [templates/slot-agents/algo.md](templates/slot-agents/algo.md) | 需要专业算法设计 / 复杂度分析 / ML |
| `architect` | [templates/slot-agents/architect.md](templates/slot-agents/architect.md) | 跨模块技术选型 / 大重构；PM hold 不住时 |
| `devops` | [templates/slot-agents/devops.md](templates/slot-agents/devops.md) | CI / 部署 / 监控成为瓶颈 |
| `data` | [templates/slot-agents/data.md](templates/slot-agents/data.md) | 数据管道 / 报表 / 分析需求 |

---

## 招聘纪律（binding，PM 必读）

1. **每招一个 agent 必须先写"为什么必要"**——不能 "以防万一" 招人。case 落 `journal/decisions/YYYY-MM-DD_hire_<role>.md`
2. **招聘 = 复制 `templates/slot-agents/<role>.md` 到 `.claude/agents/<role>.md`**（或新建），CTO 拍板后才注册
3. **每个 spec 必带 owned_paths 边界 + cannot_do 清单**（写在 .md body 里）
4. **PM → CTO 报 case**：哪些任务 PM 自己干不了 / 现有 agent 干不好 / 这个新人能解决什么 / 没活干怎么办
5. **不能堆人**——slot 是默认状态，只有 case 充分才 instantiate

---

## 角色边界速查（谁能写哪些文件）

详见 [memory/team-operating-model.md](memory/team-operating-model.md) "角色边界" 章节。简要：

- 代码（`src/`、`app/`、...）：**dev / frontend** 写，其他人**只读**（reviewer / explore 工具层就没有 Write）
- `journal/decisions/`：**PM** 写　|　`journal/post_mortems/`：**retro** 写
- `journal/reviews/`：reviewer 结论由 **PM** 归档　|　`journal/qa-reports/`：qa 报告由 **PM** 归档
- `state/INBOX.md` URGENT：**PM**；FYI / WAITING：所有 agent
- `state/board.md` / `ORG.md`：**PM** 写
- `memory/team-operating-model.md`：**CTO + PM**　|　`memory/eng-lessons.md`：**retro**

---

## 招聘 / 解雇 / 转 slot 日志（append-only）

| Date | Action | Role | Reason | Decision Doc |
|---|---|---|---|---|
| 2026-06-26 | 初立 MVP 编制 | dev / reviewer / retro / explore / frontend / qa | CTO 拍板 6 人 | [2026-06-26_template_design.md](journal/decisions/2026-06-26_template_design.md) |
| 2026-06-26 | 迁移到 native wiring | 全体 | 三件套非原生格式，cold-start 暴露 | [2026-06-26_native_agent_wiring.md](journal/decisions/2026-06-26_native_agent_wiring.md) |
