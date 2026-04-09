# 答辩PPT终版

## 第 1 页 封面

- 大学生创新创业训练计划项目
- 研究对象：调度优化与路径规划
- 核心方法：`GA / Adaptive GA / DQN-GA`

## 第 2 页 研究背景

- 复杂调度与路径规划问题普遍存在
- 传统进化算法依赖固定参数
- 固定参数难以兼顾探索与收敛
- 强化学习可用于动态调参

## 第 3 页 问题建模

- 调度问题：`JSSP`
- 目标：最小化 `Makespan`
- 路径规划问题：`TSP`
- 目标：最小化总路径长度

## 第 4 页 技术路线

- 建模 benchmark 问题
- 构建 `GA` 基线
- 构建 `Adaptive GA`
- 引入 `DQN` 动态调参
- 对比实验与可视化展示

## 第 5 页 调度算法设计

- 染色体表示工序序列
- 采用选择、交叉、变异完成搜索
- `Adaptive GA` 根据停滞与多样性调参
- `DQN-GA` 学习控制 `pc / pm`

## 第 6 页 路径规划算法设计

- 路径规划以 `TSP` 为最小模型
- 染色体表示访问顺序
- `Adaptive GA` 规则调参
- `DQN-GA` 学习控制搜索强度

## 第 7 页 DQN 原理

- `DQN` 不直接求解问题
- `DQN` 负责动态调整 `pc / pm`
- 状态包含最优值、均值、多样性、停滞代数
- 奖励由性能改进与搜索状态共同决定

## 第 8 页 数据集与实验设置

- 调度数据：`FT06、FT10、LA01-LA10`
- 路径规划数据：`burma14、berlin52`
- 对比算法：`GA / Adaptive GA / DQN-GA`
- 采用多种随机种子重复实验

## 第 9 页 调度基线结果

- `Adaptive GA` 整体优于普通 `GA`
- `FT10` 上均值 `1067.2 < 1089.0`
- 说明规则型自适应调参有效
- 为 DQN 扩展提供可靠基线

建议配图：

- [comparison_bar.png](D:/EA%20with%20WL/2.%20EA%20with%20ML/results_formal_baseline/comparison_bar.png)

## 第 10 页 调度核心案例 `LA02`

- `LA02` 上 `DQN-GA > Adaptive GA`
- `DQN-GA mean = 714.6`
- `Adaptive GA mean = 743.0`
- 学习型调参超过人工规则

建议配表：

| 算法 | mean | gap_mean_pct |
|---|---:|---:|
| Adaptive GA | 743.0 | 13.44 |
| DQN-GA | 714.6 | 9.10 |
| GA | 724.0 | 10.53 |

## 第 11 页 路径规划核心案例 `berlin52`

- 路径规划支线同样构建了 `GA / Adaptive GA / DQN-GA`
- `berlin52` 上 `DQN-GA > Adaptive GA`
- `DQN-GA mean = 7910.4`
- 说明学习型调参具有跨问题适用性

建议配表：

| 算法 | mean | gap_mean_pct |
|---|---:|---:|
| Adaptive GA | 8025.2 | 6.41 |
| DQN-GA | 7910.4 | 4.88 |
| GA | 8090.8 | 7.28 |

## 第 12 页 可视化展示

- 调度结果可用甘特图展示
- 调度过程可用动画展示
- 路径规划结果可用路径图展示
- 结果更直观、更易解释

建议配图：

- [gantt_ft06_adaptive_ga.png](D:/EA%20with%20WL/2.%20EA%20with%20ML/results_formal_baseline/gantt_ft06_adaptive_ga.png)
- [route_berlin52_dqn_ga.png](D:/EA%20with%20WL/2.%20EA%20with%20ML/results_routing_dqn_berlin52_expert_v2/route_berlin52_dqn_ga.png)

## 第 13 页 结论

- 完成了调度与路径规划双线验证
- 构建了 `GA / Adaptive GA / DQN-GA`
- `LA02` 与 `berlin52` 上均实现 `DQN-GA > Adaptive GA`
- 验证了学习型参数控制机制的有效性

## 第 14 页 展望

- 扩展到多目标优化
- 扩展到更复杂路径规划模型
- 完善应用原型与交互展示
- 提升模型泛化与稳定性

## 备份页 1 为什么选 DQN 不选 PPO

- 当前动作空间是离散的
- `DQN` 更容易实现和解释
- 样本利用率更高
- 更适合作为第一版学习型控制器

## 备份页 2 为什么先做调度再扩路径规划

- 调度 benchmark 更成熟
- 更容易建立稳定基线
- 路径规划作为补充验证对象
- 最终形成双线成果结构
