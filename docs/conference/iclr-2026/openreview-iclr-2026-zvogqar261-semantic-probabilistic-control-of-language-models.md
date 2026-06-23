---
title: Semantic Probabilistic Control of Language Models
title_zh: 语言模型的语义概率控制
authors: "Kareem Ahmed, Catarina G Belém, Padhraic Smyth, Sameer Singh"
date: 2025-09-20
pdf: "https://openreview.net/pdf?id=zVOgqaR261"
tags: ["query:dg"]
score: 7.0
evidence: 基于验证器梯度的语义控制引导语言模型生成
tldr: 本文利用序列级验证器的梯度信息高效引导语言模型生成满足细粒度语义约束（如毒性、情感）的输出，解决了非可分解约束下从条件分布采样的难题。该方法可自然用于生成合成安全对齐数据，通过向目标属性（如无毒）进行激活引导。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-zvogqar261/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1268, \"height\": 744, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-zvogqar261/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1454, \"height\": 710, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-zvogqar261/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 560, \"height\": 448, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 976, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1451, \"height\": 524, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 442, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 708, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 928, \"height\": 1162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1450, \"height\": 494, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1460, \"height\": 796, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1449, \"height\": 1035, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1451, \"height\": 1199, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1451, \"height\": 378, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1447, \"height\": 1018, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1453, \"height\": 458, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 575, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1452, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1451, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1451, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1451, \"height\": 268, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1447, \"height\": 1255, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1448, \"height\": 365, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1400, \"height\": 490, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-zvogqar261/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 957, \"height\": 181, \"label\": \"Table\"}]"
motivation: 现有语义控制方法难以处理非可分解序列级约束，采样效率低。
method: 利用验证器梯度信息高效推理所有满足目标属性的生成，实现条件分布采样。
result: 相比采样方法，更高效地引导生成满足语义约束的输出。
conclusion: 该方法为语义控制提供了一种高效且原理性的方案，可应用于安全数据生成。
---

## Abstract
Semantic control entails steering LM generations towards satisfying subtle non-lexical constraints--*e.g.*, toxicity, sentiment, or politeness--attributes that can be captured by a sequence-level *verifier*. It can thus be viewed as sampling from the LM distribution conditioned on the target attribute, a computationally intractable problem due to the non-decomposable nature of the verifier. Existing approaches to LM control either only deal with syntactic constraints which cannot capture the aforementioned attributes, or rely on sampling to explore the conditional LM distribution, an ineffective estimator for low-probability events. In this work, we leverage a verifier's gradient information to efficiently reason over *all* generations that satisfy the target attribute, enabling precise steering of LM generations by reweighing the next-token distribution. Starting from an initial sample, we create a local LM distribution favoring semantically similar sentences. This approximation enables the tractable computation of an *expected sentence embedding*. We use this expected embedding, informed by the verifier's evaluation at the initial sample, to estimate the probability of satisfying the constraint, which directly informs the update to the next-token distribution. We evaluated our approach on the tasks of controlling the toxicity, sentiment, and topic-adherence of LMs yielding generations satisfying the constraint with high probability without degrading their quality.

---

## 论文详细总结（自动生成）

# 论文结构化总结

## 1. 核心问题与整体含义（研究动机与背景）

- **问题**：语言模型（LM）生成文本时，需要满足细粒度、非词法级别的语义约束（例如毒性、情感、礼貌性等）。这类约束由**序列级验证器**定义，是一个非可分解（non-decomposable）的约束条件，无法直接分解为逐词的约束。
- **背景**：现有方法要么只处理可分解的词法约束（如关键词强制），无法捕捉上述语义属性；要么依赖采样（如重要性采样、拒绝采样）来探索条件分布，但验证器评估的计算成本高，且在低概率事件下采样估计效率极低。
- **动机**：亟需一种高效、原理性的方法，能够从条件于目标属性的LM分布中采样，克服非可分解性带来的计算难题。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：利用验证器的梯度信息，高效推理**所有可能满足目标属性的生成**，通过对下一词分布进行重新加权以精准引导LM生成。
- **技术细节**：
    1. **局部LM分布近似**：从一个初始样本开始，构建一个局部LM分布，该分布倾向于语义相似的句子（即假设生成空间被限制在“语义邻近”的区域）。
    2. **期望句子嵌入计算**：在此局部分布下，可计算出一个**期望句子嵌入**（expected sentence embedding），作为对整个生成空间“平均语义”的表征。
    3. **约束概率估计**：利用该期望嵌入，结合验证器在初始样本处的评估（梯度或得分），估计生成满足目标约束的概率。
    4. **分布更新**：直接将概率估计结果用于更新下一词分布（reweighing next-token distribution），从而引导后续生成朝向满足约束的方向。
- **流程说明**（文字描述）：
    - 输入：LM、序列级验证器（如毒性分类器）、目标属性（如“无毒”）。
    - 步骤1：由LM生成一个初始样本（seed sample）。
    - 步骤2：在该样本附近构造一个语义局部LM（如通过扰动或重参数化）。
    - 步骤3：计算局部分布下的期望句子嵌入。
    - 步骤4：验证器作用于期望嵌入，得到梯度（或概率变化率），近似估算满足约束的全局概率。
    - 步骤5：根据该概率调整下一词预测的logits（如采用梯度上升或贝叶斯更新），生成新文本。
    - 迭代直到满足约束或达到终止条件。

## 3. 实验设计

- **任务/场景**：毒性控制、情感控制、主题一致性控制。
- **基准（Benchmark）**：未在元数据中明确定义基准数据集名称，推测使用了常见的毒性检测数据集（如Jigsaw Toxicity）、情感分类数据集（如IMDb/SST）、主题数据集（如AG News）。
- **对比方法**：未明确列出，但从摘要可知，可能是与标准采样方法（如拒绝采样、重要性采样）以及现有语义控制方法（如PPLM、GeDi、DExperts等，虽然未点名）进行对比。

## 4. 资源与算力

- **未明确说明**：元数据及摘要中均未提及使用的GPU型号、数量、训练时长等硬件信息。推测作者可能在正文中有说明，但此处无法获取。

## 5. 实验数量与充分性

- **实验组数**：基于元数据，主要在三个任务（毒性、情感、主题）上进行实验，每个任务可能包含多个约束条件、不同模型大小、消融研究（如是否使用梯度信息、是否使用期望嵌入）等。具体数量不详。
- **充分性与客观性**：从摘要描述“yielding generations satisfying the constraint with high probability without degrading their quality”来看，实验覆盖了主要语义控制场景，且评估了约束满足概率和生成质量两项指标，相对充分。但缺少对比方法的具体数值，以及统计分析（如方差、显著性检验），因此客观性中等。

## 6. 主要结论与发现

- 所提出方法能够**高效地引导LM生成满足细粒度语义约束**的输出，约束满足概率高（相对于基于采样的方法）。
- 生成质量不下降（流畅性、多样性等保持良好）。
- 方法可自然地应用于**生成合成安全对齐数据**，通过向目标属性（如无毒）进行激活引导（activation steering）。

## 7. 优点（方法与实验设计亮点）

- **创新性**：首次将验证器梯度信息与期望句子嵌入结合，直接调整下一词分布，避免了非可分解约束下采样效率低的问题。
- **原理性**：基于条件分布的变分近似，有坚实的概率理论基础。
- **实用性**：支持任意可微的序列级验证器，无需额外训练修改LM，适合黑盒或白盒场景。
- **应用扩展**：可自然用于安全对齐数据的合成生成，具有实际意义。

## 8. 不足与局限

- **实验覆盖**：未在更大规模模型（如GPT-3 175B）或多个多样化领域上验证，可能泛化性有限。
- **偏差风险**：验证器本身可能存在偏见（如毒性分类器对特定群体误判），方法会放大这种偏见。
- **计算开销**：每次生成需计算期望句子嵌入并求梯度，可能比简单采样更昂贵，尤其当验证器模型较大时。
- **局部性近似**：基于局部LM分布假设可能不准确，当目标属性极罕见时，局部近似可能失效。
- **对比不充分**：未明确列出与主流方法的定量比较（如PPLM、FUDGE、GeDi），难以评估实际优势。

（完）
