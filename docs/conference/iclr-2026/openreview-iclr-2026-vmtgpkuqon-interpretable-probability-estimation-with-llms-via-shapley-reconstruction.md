---
title: Interpretable Probability Estimation with LLMs via Shapley Reconstruction
title_zh: 通过Shapley重构实现LLM可解释概率估计
authors: "Yang Nan, Qihao Wen, Jiahao Wang, Pengfei He, Ravi Tandon, Yong Ge, Han Xu"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=vmTGpKUQON"
tags: ["query:luq"]
score: 6.0
evidence: 通过Shapley值实现可解释的LLM概率估计
tldr: 直接提示LLM进行概率估计存在噪声和不透明问题。本文提出PRISM框架，通过Shapley值分解每个输入因素的边际贡献，实现可解释且更精确的概率估计。实验表明，PRISM在金融预测和医疗保健等任务上优于基线，增强了LLM在不确定性下的决策可信度。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-vmtgpkuqon/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1027, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vmtgpkuqon/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1428, \"height\": 437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vmtgpkuqon/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 696, \"height\": 326, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vmtgpkuqon/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 765, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vmtgpkuqon/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1448, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vmtgpkuqon/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1310, \"height\": 1864, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vmtgpkuqon/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1215, \"height\": 794, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vmtgpkuqon/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1029, \"height\": 2253, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vmtgpkuqon/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1517, \"height\": 1230, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vmtgpkuqon/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1584, \"height\": 1312, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vmtgpkuqon/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1417, \"height\": 360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vmtgpkuqon/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1586, \"height\": 1147, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vmtgpkuqon/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1584, \"height\": 1524, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vmtgpkuqon/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1584, \"height\": 1219, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vmtgpkuqon/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1522, \"height\": 857, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-vmtgpkuqon/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 725, \"height\": 269, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vmtgpkuqon/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1309, \"height\": 769, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vmtgpkuqon/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1316, \"height\": 470, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vmtgpkuqon/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1021, \"height\": 212, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vmtgpkuqon/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 713, \"height\": 1701, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vmtgpkuqon/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 705, \"height\": 212, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vmtgpkuqon/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1392, \"height\": 432, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vmtgpkuqon/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1393, \"height\": 485, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vmtgpkuqon/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1392, \"height\": 573, \"label\": \"Table\"}]"
motivation: LLM直接输出的概率估计噪声大且过程不透明。
method: 利用Shapley值量化每个输入因素对概率估计的边际贡献。
result: 在多个不确定性估计任务上，PRISM在准确性和可解释性上均取得提升。
conclusion: Shapley重构为LLM概率估计提供了透明且有效的途径。
---

## Abstract
Large Language Models (LLMs) demonstrate potential to estimate the probability of uncertain events, by leveraging their extensive knowledge and reasoning capabilities. This ability can be applied to support intelligent decision-making across diverse fields, such as financial forecasting and preventive healthcare. However, directly prompting LLMs for probability estimation faces significant challenges: their outputs are often noisy, and the underlying predicting process is opaque. In this paper, we propose **PRISM: Probability Reconstruction via Shapley Measures**, a framework that brings transparency and precision to LLM-based probability estimation. PRISM decomposes an LLM’s prediction by quantifying the marginal contribution of each input factor using Shapley values. These factor-level contributions are then aggregated to reconstruct a calibrated final estimate. In our experiments, we demonstrate PRISM improves predictive accuracy over direct prompting and other baselines, across multiple domains including finance, healthcare, and agriculture. Beyond performance, PRISM provides a transparent prediction pipeline: our case studies visualize how individual factors shape the final estimate, helping build trust in LLM-based decision support systems.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：在许多实际场景（如金融预测、医疗保健、农业决策）中，需要估计不确定事件的概率。然而直接使用大语言模型（LLM）进行概率估计存在两个主要挑战：
  1. **输出噪声大、不稳定**：LLM 对同一事件的估计可能因提问形式不同而产生矛盾。
  2. **过程不透明**：LLM 的“黑箱”生成过程难以解释每个输入因素（如年龄、血压）对最终预测的贡献，导致结果难以信任。

- **整体含义**：本文旨在构建一个既**准确**又**可解释**的 LLM 概率估计框架，使决策者能够理解模型推理过程，从而增强对 LLM 辅助决策的信任。

## 2. 论文提出的方法论

### 2.1 核心思想
- 借鉴传统机器学习中 Shapley 值用于模型解释的思想，提出 **PRISM（Probability Reconstruction via Shapley Measures）** 框架。
- 将预测任务分解为：**量化每个因素的边际贡献**（Shapley 值），然后将这些贡献**聚合**成校准的最终概率估计。

### 2.2 关键技术细节

#### 定义与符号
- 实例 `x = (x₁, ..., x_m)`，真实标签 `y ∈ {0,1}`，每个 `x_i` 是一个影响因子。
- LLM 输出概率 `p(·)`，定义 `f(·) = σ⁻¹(p(·))`（逆 sigmoid 函数，即 logit）。
- 传统 Shapley 值公式（对传统 ML 模型）：
  ```
  ϕ_i(f,x) = Σ_{S⊆I\{i}} (|S|!(m-|S|-1)! / m!) * (f(x_{S∪{i}}) - f(x_S))
  ```

#### PRISM 算法（针对通用输入）
1. **对比 LLM 提示（Comparative Prompting）**：对于每个因素 i，随机采样背景集 S（使用排列采样策略），在同一个查询中让 LLM 同时评估 `x_{S∪{i}}` 和 `x_S` 的概率，计算 logit 差 `σ⁻¹(p(x_{S∪{i}})) - σ⁻¹(p(x_S))`。
2. **排列采样（Permutation Sampling）**：重复 K 次，取平均值得到近似的 Shapley 值 ϕ_i。
3. **重构概率**：基 logit ϕ₀ 可由先验知识（如人口患病率）设定，最终概率 `p_PRISM(x) = σ(ϕ₀ + Σ ϕ_i)`。

#### Tabular-PRISM 变体（针对表格数据）
- 将多个背景集放入同一张表格中，一次性查询 LLM，提高查询效率。
- 引入**参考实例 r**（如人口平均值/众数），将缺失因素用参考值填充，计算“参考特定的 Shapley 值” `ϕ_i^(r)`。
- 可证明重构公式同样成立：`p_PRISM(x) = σ(ϕ₀ + Σ ϕ_i^(r))`。

## 3. 实验设计

### 3.1 数据集/场景
- **表格数据集**（4个）：
  - Adult Census Income（收入预测）
  - Heart Disease Prediction（心脏病预测）
  - Stroke Prediction（中风预测）
  - Lending Loan Default Prediction（贷款违约预测）
  每个数据集随机选 300 个测试样本（平衡正负 150:150）。

- **非结构化数据案例**（2个）：
  - **苹果价格预测**：基于 2024 年美国苹果协会年度报告，预测 2025 年不同品种苹果是否涨价。
  - **足球比赛结果预测**：基于赛前报道，预测主队获胜概率。

### 3.2 评测指标
- AUROC（ROC 曲线下面积）、AUPRC（PR 曲线下面积）、最大 F1 分数。

### 3.3 对比的方法（Baselines）
| 方法 | 说明 |
|------|------|
| 1/5/10shot level | 直接提示 LLM 用语言描述概率（如“very unlikely”），映射为数值，多轮投票 |
| 1/5/10shot score | 直接提示 LLM 输出 0-1 数值概率，多轮平均 |
| Contrast | 正向和反向提问（如“会/不会”），统一后取平均 |
| BIRD | 基于贝叶斯网络（假设因素独立）的显式概率计算 |
| ICL-5+5 / 10+10 | 在上下文中提供 5 或 10 个正负样本作为演示（小样本学习） |

### 3.4 使用的模型
- GPT-4.1-mini、Gemini-2.5-Pro
- 温度均为 1.0

## 4. 资源与算力
- **文中未明确说明**使用的 GPU 型号、数量、训练时长等信息。
- 因为 PRISM 是完全基于 LLM 推理（无模型训练），主要开销为 API 调用次数和 token 数。作者在计算效率部分给出了查询复杂度分析（Tabular-PRISM 查询复杂度 Θ(m)，PRISM 为 Θ(mK) 次查询），但未提供具体的 GPU 小时或云服务账单。

## 5. 实验数量与充分性

- **表格数据集实验**：4 个数据集 × 2 种 LLM = 8 组主实验，每组报告 3 个指标（AUROC, AUPRC, F1）。
- **非结构化案例**：2 个任务（苹果价格、足球比赛），每任务对比 2-3 种方法，附有详细的 Shapley 值可视化。
- **消融实验**：
  1. **特征交互分析**：在 Lending 数据集上展示 PRISM 能捕捉贷款金额与年收入的交互效应（如高收入下高贷款金额的 Shapley 值较低）。
  2. **计算效率分析**：理论复杂度对比表格。
- **校准分析**（附录）：绘制加权可靠性曲线，验证 PRISM 的校准性优于基线。

**评价**：实验设计较为全面，覆盖了表格和非结构化、不同领域、多种基线。但仅用了 300 个样本/数据集，规模偏小。没有进行统计显著性检验（如多次重复实验求方差）。非结构化案例仅 10 场足球赛和若干苹果品种，样本量有限。

## 6. 论文的主要结论与发现

- PRISM 在**多数表格数据集上显著优于**直接提示方法和 BIRD 等基线（尤其在 AUROC/AUPRC 上），在 Stroke 数据集上与强基线持平。
- PRISM 提供了**透明的预测管道**：通过 Shapley 值可视化每个因素的正负贡献，便于解释和理解。
- PRISM 能够**考虑特征交互**（如贷款金额和收入的交互），而 BIRD 假设因素独立无法做到。
- 在非结构化任务中，PRISM 的预测比直接 LLM 提示更合理（例如足球比赛中，直接提示因整体印象高估强队，PRISM 则综合多方因素给出更准确的概率）。

## 7. 优点

1. **可解释性强**：通过 Shapley 值清晰展示每个因素的贡献大小和方向，使 LLM 的“黑箱”决策透明化。
2. **提高预测准确性**：在多个 benchmark 上一致地优于或持平于最强的自一致性基线。
3. **灵活性**：既可处理表格数据（Tabular-PRISM 高效版本），也可处理非结构化的文本因素（如报告摘要）。
4. **处理特征交互**：通过随机背景集采样，自然考虑到因素间的相互影响，优于 BIRD 的独立性假设。
5. **理论优雅**：基于 Shapley 值的加性性质，重构概率有明确的数学基础。

## 8. 不足与局限

1. **仅零样本场景**：未考虑提供历史数据或示例的少样本/小样本场景。少样本下需区分预测来源于 LLM 知识还是示例，增加解释复杂度。
2. **仅二分类问题**：未扩展到多分类或回归概率估计。虽然 one-vs-all 可扩展，但未验证。
3. **计算成本较高**：对每个因素需多次查询 LLM（`m*K` 次评估），在因素多或输入长时耗时可观（文中 Apple 案例平均 330s/实例）。仅适用于评估规模不大的场景。
4. **实验样本量有限**：表格数据集仅 300 样本，非结构化案例样本极少（10 场球赛），统计鲁棒性不足。
5. **缺乏重复性检验**：未报告多次重复实验的标准差或置信区间，无法评估方法本身的稳定性。
6. **参考实例选择依赖先验知识**：Tabular-PRISM 需要设定参考实例（如人口均值），不当选择可能引入偏差。
7. **未讨论 OOD 泛化**：数据集均为经典公开数据集，未测试在分布外或对抗性输入下的表现。

（完）
