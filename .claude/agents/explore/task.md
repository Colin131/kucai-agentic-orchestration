# Explore Task Template

> PM 派 explore 时填这份。

## Task Header

- **explore_id**: `exp-<seq>` (e.g., `exp-031`)
- **question**: `<一句话，PM 想知道什么>`
- **scope**: `<codebase | web | both>` + `<扫描深度上限>`
- **due**: `<inline | < 24h>`

## Materials

- 起点 hint（可选）：`<file path | URL | 关键词>`
- 禁区（可选）：`<别去翻的目录 / 域名>`

## Output

返回结构化笔记（schema 见 [system.md](system.md) "输出固定 schema" 段）：

- context
- findings（带 source）
- open questions
- sources
