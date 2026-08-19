# mlhelper

`mlhelper` 是一组以研究纪律为核心的 Codex skills，用来辅助预测型机器学习研究。它不绑定训练框架，也不替研究者追逐最高分；它负责把问题定义、数据审计、训练集内开发、一次性测试、决策影响验证、最终留存评估和结论沉淀组织成可复核的证据链。

## Skills

| Skill | 作用 |
|---|---|
| `mlh` | 总控路由与不可破坏的研究纪律 |
| `mlh-frame` | 建立研究问题、目标、证伪条件与评估协议 |
| `mlh-data` | 审计标签、时间语义、数据来源和切分 |
| `mlh-develop` | 在训练集内部完成基线、特征、模型选择与消融 |
| `mlh-test` | 对冻结方案进行一次性独立测试 |
| `mlh-impact` | 验证模型转化为决策后的成本与影响 |
| `mlh-holdout` | 使用从未触碰的数据完成最终评估 |
| `mlh-review` | 对任意阶段做独立对抗评审 |
| `mlh-status` | 只读核查研究状态和下一阻塞点 |
| `mlh-freeze` | 用精确 Git 提交与 annotated tag 固化证据 |
| `mlh-conclude` | 综合证据、边界和反例，形成研究结论 |

## Pipeline

```text
frame -> data -> develop -> test -> impact -> holdout -> conclude
                      |
                      +-- inner validation, tuning and ablation stay here
```

`impact` 在量化研究中可以是成本后回测，在其他领域可以是策略模拟、离线策略评估或业务成本收益分析。没有下游决策时允许明确记录 `not_applicable`，但不能把测试分数冒充现实影响。

## Design boundaries

- 第一版只包含 Markdown skills、参考契约和模板，没有项目脚本。
- 核心路线适用于分类、回归、排序和预测。因果推断、强化学习和纯探索性聚类需要单独的方法协议，不能直接套用预测评估结论。
- Skill 可以检查证据并提出异议，但最终研究决策由研究者记录。
- 所有 test、impact 和 holdout 之后的方案变化都必须进入新的 revision，不能改写原证据。

## Suggested invocation

```text
$mlh-frame 为“客户流失预测”建立一项新研究
$mlh-status 检查当前研究下一步
$mlh-develop 设计训练集内部的验证与搜索计划
$mlh-review 对 develop 阶段做对抗评审
$mlh-freeze 冻结 develop，准备进入 test
```

每个 skill 都位于 `skills/<skill-name>/SKILL.md`。研究工作区模板位于 `skills/mlh/assets/`，完整产物契约位于 `skills/mlh/references/`。
