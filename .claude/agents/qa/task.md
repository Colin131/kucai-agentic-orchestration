# QA Task Template

> PM 派 qa 时填这份。qa 接 task 后跑 4 类测试，落 QA Report。

## Task Header

- **qa_id**: `qa-<task_id>-<seq>` (e.g., `qa-s01-04-1`)
- **target**: `<task_id | PR URL | release tag>`
- **scope**: `<feature | release | regression | bug-verify>`
- **goal_doc**: `goals/<task_id>_<slug>.md`
- **due**: `<inline | < 24h>`
- **env**: `<local | staging | CI>`

## Materials

- PR diff（看清测试边界）
- goal Done-when 全部条目
- 现有 `tests/regression/` 列表
- 历史相关 bug（如有）

## Required Test Categories（4 类，缺一不可）

- [ ] **Golden path**：用户主流程跑通
- [ ] **Edge cases** ≥ 3：空数据 / 超大 / 非法输入
- [ ] **Error path**：网络挂 / 500 / 权限 / 超时
- [ ] **Regression**：`tests/regression/` 全套

## Output

写到 `journal/qa-reports/qa-<task_id>-<ts>.md`，schema 见 [system.md](system.md) "输出固定 schema" 段。

发现 bug → INBOX WAITING raise PM，含精确 reproduce steps + expected/actual + 截图。
