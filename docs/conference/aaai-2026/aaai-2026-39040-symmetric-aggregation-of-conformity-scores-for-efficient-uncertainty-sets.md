---
title: Symmetric Aggregation of Conformity Scores for Efficient Uncertainty Sets
title_zh: 一致性得分的对称聚合以生成高效不确定性集
authors: "Nabil Alami, Jad Zakharia, Souhaib Ben Taieb"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39040/43002"
tags: ["query:uq-safety"]
score: 7.0
evidence: 聚合一致性得分实现高效不确定性量化
tldr: 该论文针对多模型不确定性聚合问题，提出对称聚合共形预测方法SACP。将多个预测器的非一致性得分转换为e值并用对称聚合函数组合，生成更丰富且信息量更大的预测集。理论分析和实验表明SACP在保持有效覆盖的同时提高效率，为集成不确定性量化提供了新途径。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有共形预测方法难以有效聚合多个模型的预测集。
method: 将非一致性得分转换为e值，使用对称聚合函数组合。
result: 在回归和分类任务上验证了方法的效率和有效性。
conclusion: SACP有效聚合多模型不确定性，生成更紧致的预测集。
---

## Abstract
Access to multiple predictive models trained for the same task, whether in regression or classification, is increasingly common in many applications. Aggregating their predictive uncertainties to produce reliable and efficient uncertainty quantification is therefore a critical but still underexplored challenge, especially within the framework of conformal prediction (CP). While CP methods can generate individual prediction sets from each model, combining them into a single, more informative set remains a challenging problem. To address this, we propose SACP (Symmetric Aggregated Conformal Prediction), a novel method that aggregates nonconformity scores from multiple predictors. SACP transforms these scores into e-values and combines them using any symmetric aggregation function. This flexible design enables a robust, data-driven framework for selecting aggregation strategies that yield sharper prediction sets. We also provide theoretical insights that help justify the validity and performance of the SACP approach. Extensive experiments on diverse datasets show that SACP consistently improves efficiency and often outperforms state-of-the-art model aggregation baselines.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：当同一任务（回归或分类）存在多个预训练模型时，如何有效聚合它们的不确定性估计，以生成可靠且高效的预测集。传统共形预测（CP）能为每个模型构建带覆盖保证的预测集，但如何将多个预测集合并为一个信息更丰富的集合仍是一个挑战。
- **研究动机**：许多AI模型缺乏可靠的不确定性估计，而CP提供了一种分布自由的框架。模型集成能提升预测性能，但在CP框架内聚合多个模型的输出（即在保持精确覆盖保证的同时获得更紧致的预测集）尚未被充分探索。
- **整体含义**：提出一种新的聚合方法SACP，通过对称聚合多个模型的非一致性得分（NCS），实现高效且有效的预测集构建，填补了该领域的空白。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：将每个模型的非一致性得分转换为e值（e-variables），然后使用任意对称聚合函数组合这些e值，最后利用标准分割共形预测构造预测集。
- **关键技术细节**：
  - **第一步：E值变换**。对每个预测器 \(k\) 和每个候选标签 \(y\)，定义校准e值：
    \[
    E^{(k)}_i(y) = \frac{s^{(k)}(X_i, Y_i)}{\frac{1}{n+1}\left(\sum_{j=1}^n s^{(k)}(X_j, Y_j) + s^{(k)}(X_{\text{test}}, y)\right)}
    \]
    测试e值类似。这些e值满足期望为1的性质（类似于e-variable），且标准化了不同尺度下的得分。
  - **第二步：对称聚合**。对每个校准点 \(i\)，计算聚合得分 \(F_i(y) = f(\mathbf{E}_i(y))\)，其中 \(f\) 是任意对称函数（例如求和）。测试点的聚合得分为 \(F_{\text{test}}(y)\)。
  - **预测集构建**：
    - 若聚合得分越小表示越一致（如 \(f\) 分量不减），则预测集为
      \[
      C^{f,\uparrow}_\alpha(X_{\text{test}}) = \{ y \in \mathcal{Y} \mid F_{\text{test}}(y) \le \hat{Q}_\alpha(y) \}
      \]
      其中 \(\hat{Q}_\alpha(y)\) 是校准聚合得分的 \( (1-\alpha) \) 分位数。
    - 反之若得分越大越一致，则使用逆向分位数。
  - **理论保证**：定理3.3证明SACP预测集满足有限样本边际覆盖保证 \(1-\alpha\)。
  - **数据驱动变体SACP++**：在参数化对称函数族 \(\Phi_p(x) = \sum_{k=1}^K (x_k)^p\) 中搜索最优 \(p\)，以最小化测试集上平均预测集长度。
- **算法流程**（文字描述）：
  1. 基于训练数据训练 \(K\) 个基预测器。
  2. 对校准集计算每个预测器的非一致性得分。
  3. 对测试样本的每个候选标签 \(y\)，计算每个预测器的校准e值和测试e值。
  4. 用所选对称函数 \(f\) 聚合这些e值，得到校准和测试的聚合得分。
  5. 根据聚合得分的分位数构建预测集（对回归需在输出空间上离散网格）。

## 3. 实验设计：使用的数据集 / 场景、benchmark、对比方法
- **回归任务**：使用OpenML上的9个单输出回归数据集（此前CP研究的基准）。
- **分类任务**：使用CIFAR-10和MNIST两个标准图像分类数据集。
- **对比方法**：
  - **Weighted Aggregation (Wagg)**：Luo & Zhou (2025) 的加权聚合方法。
  - **Conformal Score Aggregation (CSA)**：Rivera, Patel & Tewari (2025) 的多元分位数方法。
  - **Deterministic Majority Vote (CM)** 和 **Randomized Majority Vote (CR)**：Gasparin & Ramdas (2024b) 的集合级聚合方法。
  - **Best Model Selection (BL)**：选择平均预测集长度最小的单个模型。
  - **SACP**（默认求和，即 \(p=1\)）与 **SACP++**（数据驱动选择最优 \(p\)）。
- **实验场景**：回归中设置 \(\alpha=0.05\)，分类中设置 \(\alpha=0.05\) 和 \(\alpha=0.10\)。所有方法使用相同训练集、校准集和固定非一致性得分（绝对残差、1-预测概率）。回归输出空间离散化为255点网格。

## 4. 资源与算力
论文中未明确说明使用的GPU型号、数量或训练时长。仅提及代码开源在GitHub，实验在不同数据集上进行了20次随机划分。未提供详细的硬件配置或计算开销。

## 5. 实验数量与充分性
- **实验数量**：
  - 回归：9个OpenML数据集，每个20次随机数据划分。
  - 分类：2个数据集（CIFAR-10、MNIST），每个在 \(\alpha=0.05,0.10\) 两种设置下实验。
  - 消融：附录C中包含对预测器数量 \(K\) 的敏感性分析。
- **充分性与公平性**：
  - 实验覆盖了多种基预测器（线性模型、树、神经网络、贝叶斯等），考虑了多模型差异。
  - 所有方法使用相同的训练/校准/测试划分，公平比较。
  - 对CM和CR方法调整名义错误率至 \(\alpha/2\) 以保证公平比较覆盖级别（因其基础保证为 \(1-2\alpha\)）。
  - 总体充分，但在分类数据集数量上偏少（仅2个），可能限制了泛化性。未提及在大规模或复杂任务（如语义分割、NLP）上的实验。

## 6. 论文的主要结论与发现
- **覆盖能力**：SACP和SACP++在所有数据集上均达到目标经验覆盖率（接近名义水平），而CSA有下覆盖倾向，CM/CR则过度保守。
- **效率（预测集长度）**：
  - 回归：SACP++在9个数据集中有5个优于最好单个模型（BL），并在7个数据集中取得聚合方法中最佳表现。
  - 分类：SACP++始终产生最小的预测集，尤其在CIFAR-10上预测集长度方差显著低于其他方法。
- **聚合价值**：通过共享多个预测器的结构，聚合能提高效率同时保持有效覆盖。
- **理论贡献**：提供了最坏情况下的预测集长度上界（定理3.7），并阐明了对称聚合函数不影响覆盖保证的性质。

## 7. 优点：方法或实验设计上的亮点
- **方法创新**：
  - 首次在得分级别上使用对称聚合实现 \(1-\alpha\) 覆盖而不需数据分割（其他方法常需二次分割）。
  - 引入e值变换，统一了不同尺度和分布的非一致性得分，实现公平聚合。
  - 灵活可学习的聚合函数（SACP++），支持数据驱动优化。
- **理论支撑**：对对称聚合函数的影响进行了理论分析（命题3.4、3.5），并给出了最坏情况长度上界。
- **实验设计**：
  - 统一的基预测器和预处理（标准化，固定非一致性得分），确保对比公平。
  - 覆盖多类回归器和分类器，考虑了模型多样性。
  - 公开代码，可复现。

## 8. 不足与局限
- **实验覆盖不足**：分类数据集仅两个（CIFAR-10、MNIST），未包括更多元化的分类任务或实际应用场景（如医疗、物流）。
- **回归网格依赖**：回归中需离散化输出空间（255点），可能引入精度损失，且计算复杂度随网格大小线性增长。
- **未深入探讨依赖结构**：未分析预测器间的不确定性相关性如何影响聚合性能，仅提及“未来工作”。
- **计算开销**：SACP++需要在测试集上搜索最优 \(p\)，可能带来额外计算成本。文中未与Wagg或CSA的复杂度进行详细比较。
- **对称性限制**：对称聚合假设模型间无优先级，但在某些场景下可能损失信息（如基于性能加权）。
- **理论边界保守**：最坏情况上界（定理3.7）可能较宽松，实际表现更好，但未提供更紧的统计边界。

（完）
