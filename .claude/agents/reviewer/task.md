# Reviewer Task Template

> PM 召 reviewer 时填这份。reviewer 接到后只读以下材料 + 独立 confirm 4 件套。

## Task Header

- **review_id**: `r-<task_id>-<seq>` （e.g., `r-s01-03-1`）
- **PR / diff**: `<PR URL | branch name | local diff range>`
- **goal_doc**: `goals/<task_id>_<slug>.md`
- **dev_self_report**: 见 [PR description]
- **scope reminder**: `<owned_paths_override 如果 PM 临时调整>`
- **special focus** (可选): `<PM 想让 reviewer 重点看的方面，但不要给 spoiler>`

## Cold-Context Materials（reviewer 只读这三类）

1. The diff itself（`git diff <base>..<head>`）
2. The goal doc（Done-when / Guardrails 段最重要）
3. 涉及代码文件的当前内容（看上下文用）

**不读**：PM 派工讨论 / dev "我为什么这么做" 的解释。

## Self-Verification Checklist（独立跑，不信 dev 自报）

- [ ] `git status` clean
- [ ] `git log --oneline <base>..<head>` 显示真实 commit
- [ ] 测试跑通（命令 + 通过数 + 失败数）
- [ ] Happy path 冷启动复跑

## Output

写到 `journal/reviews/<review_id>.md`，结构见 [system.md](system.md) "输出固定结构" 段。
