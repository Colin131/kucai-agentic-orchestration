# Decision: 迁移到 native Claude Code agent wiring

- **date**: 2026-06-26
- **author**: @pm（CTO 指示"发现问题直接修，别跑两遍测试"）
- **status**: accepted
- **supersedes**: 部分修正 [2026-06-26_template_design.md](2026-06-26_template_design.md) 的三件套结构决定

## Context

s01-01（第一个真实任务）启动时，PM 准备派 explore 子 agent，**cold-start 暴露一个 wiring 缺口**：

- M1-M4 落的 agent spec 是 `.claude/agents/<name>/{config.yaml, system.md, task.md}` 三件套**目录**结构（借鉴 bernstein）。
- 但 **Claude Code 原生只认两样**：① 主 session 行为来自根 `CLAUDE.md`；② 子 agent 是**单文件** `.claude/agents/<name>.md` + frontmatter。
- 证据：session 启动时 available subagent_types 只有内置的（claude / Explore / general-purpose / ...），**11 个自定义 agent 一个都没注册**。PM 角色也只靠 CTO 在 chat 口头指定，没有 CLAUDE.md 兜底。

这是典型的 **process 看着对、outcome cold-start 才暴露**：spec 内容（binding / 边界 / 哲学）都对，但格式没接进 harness，等于一堆没通电的文档。

## Decision

**直接迁移到 native 格式**（CTO 明示不要带病测试、避免两遍）：

| 旧（非原生） | 新（原生） |
|---|---|
| `.claude/agents/pm/` 三件套 | 根 `CLAUDE.md`（主 session = PM） |
| `.claude/agents/<role>/` 三件套 ×6 | `.claude/agents/<role>.md` 单文件 + frontmatter ×6 |
| slot 三件套 ×4 | `templates/slot-agents/<role>.md` 草稿（未注册；招聘=复制进 `.claude/agents/`） |

内容映射：`config.yaml` 的 tools/model → frontmatter；owned_paths/cannot_do → body 边界段；effort/max_concurrent（原生不支持）→ 降级为 body 注记；`task.md` 自报模板 → 折进 body「自报结构」+ `goals/GOAL_TEMPLATE.md`。

## Consequences

- **附带收益（实打实）**：原生 `tools` frontmatter 能**工具层强制只读**——reviewer / explore 不给 Edit/Write，从此改不了代码（比纯纪律硬）。reviewer/qa 的结论改为**返回消息**交回 PM 归档。
- **slot 概念技术化**：草稿不在 `.claude/agents/` = 真的不可被 dispatch，"招聘"= 复制文件，名实相符。
- **in-session 限制**：新建的 agent 文件**本 session 可能不热加载**——native subagent 通常 session 启动时注册。所以这次 s01 测试前**建议重启 claude** 让 6 个 native agent + CLAUDE.md PM 角色真正生效，再跑，才是"真编排"测试。
- **风险**：effort / max_concurrent / owned_paths 仍是 prompt 级纪律，非 harness 强制（除非后续加 PreToolUse hook 强制 owned_paths——记为 v0.2 候选）。

## Follow-ups (retro 必看)

- [ ] **retro 记一条 pattern**：模板类交付，"spec 内容对"≠"接进 harness"。future 模板自举的 Done-when 必须含"native 格式 + 冷启动真能 dispatch"一条，不能只验内容。
- [ ] s01 测试前重启 claude 验证 native agent 注册成功（PM SOP 跑得通 / 能 dispatch dev 等）
- [ ] v0.2 候选：PreToolUse hook 强制 owned_paths
