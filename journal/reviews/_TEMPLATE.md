# Review: <task_id>

- **review_id**: `r-<task_id>-<seq>`
- **date**: YYYY-MM-DD
- **author**: @reviewer
- **PR**: <URL or branch range>
- **goal_doc**: `goals/<task_id>_<slug>.md`

## Verdict

`accept | accept-with-fixes | reject`

## Independent Verification（4 件套）

- **git status**: <pass/fail + 证据>
- **git log**: <pass/fail + 证据>
- **tests**: <N tests, all pass | M fail>
- **cold rerun**: <command + 输出节选>

## Findings

### blocker

- `[file:line]` <issue> — <why this matters> — <suggested fix>

### major

- ...

### minor

- ...

### nit

- ...

## Scope Check

- 改的 path 都在 dev owned_paths 里？<yes/no + 证据>
- 是否引入未授权依赖？<yes/no>
- diff 是否符合 goal Done-when？<yes/no + 哪条对不上>
