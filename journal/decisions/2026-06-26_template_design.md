# Decision: 模板设计 + 初始 6 人编制

- **date**: 2026-06-26
- **author**: @pm（在 CTO summon 下）
- **status**: accepted

## Context

CTO 在新 repo `Colin131/kucai-agentic-orchestration` 提出打造**基于 Claude Code 的多 agent 编排模板**，给 AI 软件公司用。PM 角色由 Claude Code 主线扮演，下属是 subagent。

CTO 明确要求：
- 模板**被 fork 到具体项目 repo** 后使用
- MVP **只交骨架 + spec + 手册**，不带 demo 项目
- 调研三个参考 repo 后讨论编制

参考资料：
- 资管 desk 内部实践（reflection.md 等角色 spec、ORG / memory / journal / INBOX / calibration 全套）
- [evolab/cto-orchestration](https://github.com/martin1847/evolab/tree/main/skills/cto-orchestration)（朋友个人实践，未广泛验证）
- [smtg-ai/claude-squad](https://github.com/smtg-ai/claude-squad)（高 star）
- [sipyourdrink-ltd/bernstein](https://github.com/sipyourdrink-ltd/bernstein)（高 star）

## Options Considered

### Option A: 资管 desk 单文件 spec 直搬

- **pros**: 跟资管 desk 一致，学习曲线低
- **cons**: 缺 software-specific 纪律；spec 演化困难（参数 / prompt 混在一起）
- **cost**: 低

### Option B: bernstein 三件套（config.yaml + system.md + task.md）

- **pros**: model/effort 与 prompt 解耦；task 模板可填空；与 owned_paths 边界天然契合
- **cons**: 文件数 3×（spec 维护成本高）；初学者 cognitive load 大
- **cost**: 中

### Option C: 自创新结构

- **pros**: 完全 fit purpose
- **cons**: 没人验证；CTO 时间宝贵
- **cost**: 高

## Decision

**Option B（三件套）**。CTO 明示偏好。

**最终编制 6 active + 1 PM + 4 slot**：

- Active: `pm`, `dev`, `reviewer`, `retro`, `explore`, `frontend`, `qa`
- Slot（spec 落、不算 headcount、按需 instantiate）: `algo`, `architect`, `devops`, `data`

### 借鉴清单

| 来源 | 借鉴 |
|---|---|
| 资管 desk | ORG / INBOX 三 section / journal / memory / calibration 全套组织文件；5 条 binding 哲学；边界硬纪律 |
| evolab | goal 文档强制结构（Context / Hypotheses / Done-when / Guardrails）；Implemented ≠ Verified 4 件套；cold-context 评审 |
| bernstein | spec 三件套结构；`owned_paths` 边界字段；INBOX 类似 bulletin 模式（保留 .md，不上 typed JSON） |
| claude-squad | 一 agent 一 worktree 硬隔离（写进 dev / frontend spec） |

### 明确拒绝清单

- tmux send-keys 编排载体 → 用 Claude Code 原生 Agent tool
- HMAC 审计链 → git history 够了
- "编排者绝不写一行代码"铁律 → 允许 PM ≤ 5 行 surgical exception（reviewer 仍要看；retro 月度审查频率）
- bernstein 的合规级 runtime / merge queue / task server → 超出模板范围

### Reviewer vs QA 区别（CTO 追问后定义）

- **reviewer** = process 把关（diff *写得* 对吗），cold-context 启动，只读 diff + goal
- **qa** = outcome 把关（产品 *跑起来* 对吗），跑 4 类测试（golden / edge / error / regression）

两者不重叠也不替代。这是 process ≠ outcome 在岗位上的落地。

## Consequences

- **短期**：PM 第一个 session 落 ~40 文件（M1-M4），单次重投入
- **长期**：fork 即用；CTO 可以在新项目 1 天起团队
- **风险**：
  - 三件套 spec 维护成本，可能需要 v0.2 优化
  - 6 + 4 spec 量大，文档质量 vs 数量 trade-off 需要 retro 季度审查
  - PM "不写代码" 边界有争议（surgical exception 实际频率待 retro 月度跟踪）

## Follow-ups

- [ ] M5 push 到远端（待 CTO 拍板 git 工作流：直 main 还是开 PR）
- [ ] 第一次真实项目使用后 → retro 评估 binding 哪些过严 / 过松
- [ ] 季度审查 slot 槽位是否需要永久启用 / 砍掉
