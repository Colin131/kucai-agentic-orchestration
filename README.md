# kucai-agentic-orchestration

> 基于 Claude Code 多 agent 编排的**软件项目模板**。fork 到你的项目 repo，第一天就有一队 agent 可调度。

> **➡️ 想把这套编排装进另一个项目？** 让那个项目的 session 读 [BOOTSTRAP.md](BOOTSTRAP.md) —— 一份自包含的 install 指令，照着执行就能在该项目里原样重建（含 native 格式 + 重启注册 + binding 纪律 + 已知坑）。

## 这是什么

- 一套**预设的 agent 团队**（native Claude Code wiring）：PM（主 session）+ 6 active 子 agent（dev / reviewer / retro / explore / frontend / qa）+ 4 slot 草稿（algo / architect / devops / data）
- 一套**运营文件骨架**：ORG / INBOX / board / decisions / post_mortems / lessons / calibration
- 一套**binding 工作纪律**：process ≠ outcome、跟踪 rejected、n=1 不改方向、Implemented ≠ Verified、no lessons-learned 平话
- 一份**派工合同模板**：`goals/GOAL_TEMPLATE.md`

## 哲学（30 秒版）

> 你是 CTO（用户），PM 是你的项目经理（= 在本 repo 打开 claude 的主 session）。CTO 提项目背景 + 需求，PM 派工给子 agent、验收产出、向 CTO 汇报。每个 agent 有 spec、有边界（owned_paths）、有不能做的事（cannot_do）。

详见 [memory/team-operating-model.md](memory/team-operating-model.md)。

## 怎么跑（native wiring）

- **PM** = 主 session：行为来自根目录 [CLAUDE.md](CLAUDE.md)，自动载入。打开 claude 即是 PM。
- **子 agent** = `.claude/agents/<name>.md`：Claude Code 原生识别，PM 用 Agent tool / "use the X subagent" 派工。
- **slot** = `templates/slot-agents/<name>.md` 草稿：未注册；招聘 = 复制进 `.claude/agents/`。

### fork 后第一天

1. `git clone` 到你的新项目目录（或以此为根开发）
2. **改 [ORG.md](ORG.md)**：项目名 / 想砍或留的 agent
3. `claude` 启动——主 session 自动载入 `CLAUDE.md`，**你就是 PM**
4. CTO 给第一个 goal（一句话即可），PM 会：写 `goals/<id>_<title>.md` 派工合同 → dispatch 子 agent → 验收（四件套 + reviewer cold-context）→ 推进 `state/board.md` → 召 retro 复盘 → 向 CTO 汇报

> 注：本 repo 也可当"PM 办公室"驱动**外部产品 repo**（goal / 决策 / 复盘留这，代码在外部 repo 改、最终开 branch push）。见 CLAUDE.md "跨 repo 工作"。

## 目录速查

```
CLAUDE.md                    # PM（主 session）操作手册，自动载入
.claude/agents/<role>.md     # active 子 agent（native 单文件 + frontmatter）
templates/slot-agents/<role>.md  # slot 草稿（未注册，招聘时复制进 .claude/agents/）
ORG.md                       # 花名册 + headcount + 招聘纪律
state/
  INBOX.md                   # URGENT / FYI / WAITING 三 section
  board.md                   # sprint 看板
  calibration.json           # 估时 / 质量预测准度
memory/
  team-operating-model.md    # 运营哲学 + 角色边界 + binding 总册
  eng-lessons.md             # 累积工程教训（retro 写）
journal/
  decisions/                 # PRD / 技术选型 / scope / 招聘决策（PM 写）
  post_mortems/              # closed PR / feature / incident 复盘（retro 写）
  reviews/  qa-reports/      # reviewer / qa 产出归档
goals/
  GOAL_TEMPLATE.md           # 派工合同模板
```

## 灵感来源 & 取舍

- **资管 desk 内部实践**：process ≠ outcome / 跟踪 rejected / n=1 不改方向 / 边界硬
- **[evolab/cto-orchestration](https://github.com/martin1847/evolab/tree/main/skills/cto-orchestration)**：goal 文档强制结构 / Implemented ≠ Verified 四件套 / cold-context 评审
- **[bernstein](https://github.com/sipyourdrink-ltd/bernstein)**：`owned_files` 边界 / role spec 结构 / bulletin board 模式
- **[claude-squad](https://github.com/smtg-ai/claude-squad)**：一 agent 一 worktree 硬隔离

**明确不抄**：tmux send-keys 编排载体（用 Claude Code 原生 Agent tool）/ HMAC 审计链（git history 够了）/ "编排者绝不写代码"铁律（PM 可 surgical edit）/ 合规级 runtime 子系统（超出模板范围）。

详细取舍见 [journal/decisions/2026-06-26_template_design.md](journal/decisions/2026-06-26_template_design.md) + [native wiring 迁移](journal/decisions/2026-06-26_native_agent_wiring.md)。

## 状态

- v0.1 (MVP) — 私有 repo @ Colin131
- 当前里程碑进度见 TaskList（运行 `claude` 后查看）
