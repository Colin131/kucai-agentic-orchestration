# kucai-agentic-orchestration

> 基于 Claude Code 多 agent 编排的**软件项目模板**。fork 到你的项目 repo，第一天就有一队 agent 可调度。

## 这是什么

- 一套**预设的 agent 团队**：6 active（pm / dev / reviewer / retro / explore / frontend / qa）+ 4 slot 槽位（algo / architect / devops / data）
- 一套**运营文件骨架**：ORG / INBOX / board / decisions / post_mortems / lessons / calibration
- 一套**binding 工作纪律**：process ≠ outcome、跟踪 rejected、n=1 不改方向、Implemented ≠ Verified、no lessons-learned 平话
- 一份**派工合同模板**：`goals/GOAL_TEMPLATE.md`

## 哲学（30 秒版）

> 你是 CTO（用户），PM agent 是你的项目经理。CTO 提项目背景 + 需求，PM 派工给下属 agent、验收他们的产出、向 CTO 汇报进展。每个 agent 有 spec、有边界（`owned_paths`）、有不能做的事（`cannot_do`）。

详见 [memory/team-operating-model.md](memory/team-operating-model.md)。

## fork 后第一天怎么跑

1. `git clone` 到你的新项目目录（或直接以此为根开发）
2. **改 [ORG.md](ORG.md)**：项目名 / 你想砍掉或保留的 agent
3. `claude` 启动 Claude Code，对它说："你是 PM，CTO 给你以下项目背景..."
4. PM 自动加载 `.claude/agents/pm/`，按本模板纪律工作
5. CTO 给第一个 goal（一句话即可），PM 会：
   - 写 `goals/<id>_<title>.md` 派工合同
   - 选 agent dispatch（通过 Claude Code 的 Agent tool）
   - 收 agent 产出 + 验收（必要时召 reviewer cold-context 二审）
   - 推进 `state/board.md`
   - closed 后让 `retro` 复盘

## 目录速查

```
.claude/agents/<role>/       # agent spec（三件套：config.yaml + system.md + task.md）
ORG.md                       # 花名册 + headcount + 招聘纪律
state/
  INBOX.md                   # URGENT / FYI / WAITING 三 section
  board.md                   # sprint 看板
  calibration.json           # 估时 / 质量预测准度
memory/
  team-operating-model.md    # 运营哲学 + 角色边界 + binding 总册（默认载入所有 agent）
  eng-lessons.md             # 累积工程教训（retro 写）
journal/
  decisions/                 # PRD / 技术选型 / scope / 招聘决策（PM 写）
  post_mortems/              # closed PR / feature / incident 复盘（retro 写）
goals/
  GOAL_TEMPLATE.md           # 派工合同模板
```

## 灵感来源 & 取舍

- **资管 desk 内部实践**：process ≠ outcome / 跟踪 rejected / n=1 不改方向 / 边界硬
- **[evolab/cto-orchestration](https://github.com/martin1847/evolab/tree/main/skills/cto-orchestration)**：goal 文档强制结构 / Implemented ≠ Verified 四件套 / cold-context 评审
- **[bernstein](https://github.com/sipyourdrink-ltd/bernstein)**：`owned_files` 边界 / role 三件套结构 / bulletin board 模式
- **[claude-squad](https://github.com/smtg-ai/claude-squad)**：一 agent 一 worktree 硬隔离

**明确不抄**：tmux send-keys 编排载体（用 Claude Code 原生 Agent tool）/ HMAC 审计链（git history 够了）/ "编排者绝不写代码"铁律（PM 可以 surgical edit）/ 合规级 runtime 子系统（超出模板范围）。

详细取舍见 [journal/decisions/2026-06-26_template_design.md](journal/decisions/2026-06-26_template_design.md)（M4 阶段落盘）。

## 状态

- v0.1 (MVP) 开发中 — 私有 repo @ Colin131
- 当前里程碑进度见 TaskList（运行 `claude` 后查看）
