# Post-mortem: <target> — <event>

- **date**: YYYY-MM-DD
- **author**: @retro
- **target**: <task_id | PR URL | incident_id>
- **event_type**: `closed_pr | shipped_feature | incident | rejected`

## 1. 事件

<一句话>

## 2. 决策时的信息集 vs 现在的信息

- **当时知道**:
- **当时不知道**:
- **这个差距是否可避免**? `yes | no` — <reason>

## 3. 预测 vs 实际

- **estimated_hours**: <> / **actual_hours**: <>
- **预期 outcome**: <> / **实际 outcome**: <>
- **路径形状**: `smooth | 先卡后通 | rollback`

## 4. Process × Outcome 四象限分类

|  | Outcome ✓ | Outcome ✗ |
|---|---|---|
| Process ✓ | earned win | unlucky |
| Process ✗ | lucky | earned loss |

**本次：`<选 ONE>` + 理由**

## 5. Process 评分

- 派工 goal 写得清吗？
- dev 4 件套跑了吗？
- reviewer cold-context 严守吗？
- 该 raise PM 的有 raise 吗？

## 6. Outcome 评分

- Done-when 是否全 check？
- 用户反馈 / 回归 / 监控信号？

## 7. 模式教训（翻译成具体行为改变，不要平话）

- **教训**: <一句 pattern>
- **行为改变**: append 哪个 spec / SOP 的哪一条？<具体 diff>

## 8. Calibration delta

- estimated / actual hours: <new datapoint>
- severity / outcome 对照: <new datapoint>
