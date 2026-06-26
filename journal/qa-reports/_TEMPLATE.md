# QA Report: <task_id>

- **qa_id**: `qa-<task_id>-<seq>`
- **date**: YYYY-MM-DD
- **author**: @qa
- **target**: <task_id | PR URL | release tag>
- **scope**: `feature | release | regression | bug-verify`

## Verdict

`pass | fail | conditional-pass`

## Env

- branch / commit / build
- 跑测试的环境（local / staging / CI）

## Results

| Category | Tested | Pass | Fail | Notes |
|---|---|---|---|---|
| golden path | | | | |
| edge cases | | | | |
| error path | | | | |
| regression | | | | |

## Reproduce Steps（每个 failure）

### Failure 1: <title>

1. <step>
2. <step>

- **expected**: <>
- **actual**: <>
- **screenshot**: <link>

## Scope Check

- 测试是否覆盖了 goal Done-when 全部条目？<yes/no + 哪条没覆盖>
