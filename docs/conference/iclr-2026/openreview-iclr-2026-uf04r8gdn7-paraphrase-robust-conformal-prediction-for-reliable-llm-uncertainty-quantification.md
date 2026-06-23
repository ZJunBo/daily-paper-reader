---
title: Paraphrase-Robust Conformal Prediction for Reliable LLM Uncertainty Quantification
title_zh: 基于释义鲁棒共形预测的可靠大语言模型不确定性量化
authors: "Jiayi Xin, Evan Qiang, Xiang Li, Weijie J Su, Qi Long"
date: 2025-09-20
pdf: "https://openreview.net/pdf?id=Uf04r8gDn7"
tags: ["query:luq"]
score: 9.0
evidence: 基于释义鲁棒的共形预测进行大语言模型不确定性量化
tldr: 本文提出一种对释义变体鲁棒的不确定性量化框架，基于共形预测保证统计覆盖率。通过生成查询的语义释义并训练辅助模型来近似和鲁棒化预测分布，最终得到释义感知的非一致分数。在五个多项选择数据集上验证了该方法的有效性和鲁棒性。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-uf04r8gdn7/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1208, \"height\": 777, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uf04r8gdn7/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 525, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uf04r8gdn7/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1448, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uf04r8gdn7/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1042, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uf04r8gdn7/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1046, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uf04r8gdn7/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1039, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uf04r8gdn7/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1042, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uf04r8gdn7/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1414, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uf04r8gdn7/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1420, \"height\": 347, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uf04r8gdn7/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1428, \"height\": 471, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1456, \"height\": 742, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1353, \"height\": 441, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1449, \"height\": 472, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 635, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1213, \"height\": 1090, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1204, \"height\": 1089, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1297, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1306, \"height\": 173, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1449, \"height\": 1104, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1047, \"height\": 470, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 950, \"height\": 492, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 939, \"height\": 493, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1314, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 934, \"height\": 493, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 936, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1448, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uf04r8gdn7/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1447, \"height\": 357, \"label\": \"Table\"}]"
motivation: 现有不确定性量化方法缺乏统计严谨性并对释义变体不鲁棒。
method: 使用共形预测，构造释义感知非一致分数，聚合释义间变异性。
result: 在五个数据集上验证了有效的覆盖率和鲁棒性。
conclusion: 该方法为LLM不确定性量化提供了统计保证和释义鲁棒性。
---

## Abstract
Uncertainty quantification (UQ) provides interpretable measures of predictive confidence and supports reliable decision-making with large language models (LLMs). However, existing UQ methods are often neither statistically rigorous nor robust to paraphrase variations. To address these limitations, we propose a new framework for paraphrase-robust UQ, which builds on conformal prediction to ensure valid coverage and introduces a paraphrase-aware nonconformity score to enhance robustness. The score is derived by generating independent semantic paraphrases of each query, training an ancillary model that both approximates and robustifies the predictive distribution, and aggregating variability across these paraphrases.  On five general multiple-choice Question Answering (MCQA) datasets and two medical MCQA datasets with $\texttt{Qwen2.5-7B}$, our method achieves nominal coverage with compact prediction sets and demonstrates improved robustness to paraphrase shifts across different rewording settings. The results also generalize to $\texttt{Llama-3.1-8B}$ and $\texttt{Phi-3-small}$, underscoring the reliability of the framework across model families. Code is available at https://anonymous.4open.science/r/paraphrase_uq-FDD8.

---

## 论文详细总结（自动生成）

# 论文总结：Paraphrase-Robust Conformal Prediction for Reliable LLM Uncertainty Quantification

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）在生成预测时往往表现出过度自信，其输出概率不能可靠反映真实不确定性。现有不确定性量化（UQ）方法要么是启发式的（如基于令牌的熵、边际、logit排名），缺乏统计保证；要么在面对语义等价的输入改写（paraphrasing）时表现不稳定——即使问题含义相同，预测集大小可能剧烈波动。
- **整体含义**：论文旨在构建一个**统计严谨且对释义变体鲁棒**的不确定性量化框架，使得LLM在安全关键场景（如医疗、教育）中能提供可解释且可靠的不确定性估计。通过引入共形预测（Conformal Prediction）的覆盖保证以及设计一种“释义感知”的非一致性分数，使预测集在保持名义覆盖的同时显著缩小，并在输入被改写时依然稳定。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- 基于共形预测（Split CP 和 Quasi-conditional CP）提供有限样本覆盖保证。
- 设计**释义感知非一致性分数**：对每个查询生成多个语义释义，通过轻量级代理模型（proxy model）聚合这些释义下的预测不确定性，使得分数对释义自然不敏感。

### 关键技术细节
1. **代理模型训练**：
   - 使用LLM的最后一层隐藏状态作为输入，训练一个两层MLP（称为代理模型）来预测标签概率分布。
   - 损失函数 = 交叉熵 + λ·软箱格ECE损失（校准损失），以改善校准性。
2. **释义生成**：
   - 对每个原始问题x，用LLM（如Qwen2.5-7B或Llama-3.1-8B）生成m个语义等价的释义，组成集合B(x)。
3. **三种释义感知分数**：
   - **均值分数**：$S_{\text{mean}}(x,y) = \frac{1}{m}\sum_{x'\in B(x)} S_{\text{prob}}(x',y)$，其中$S_{\text{prob}}(x,y)=1-P_\theta(y|E(x))$。
   - **加权分数**：$S_{\text{weighted}}$，根据释义与原问题嵌入的余弦相似度加权。
   - **最坏情况分数**：$S_{\text{worst}}(x,y)=\max_{x'\in B(x)}S_{\text{prob}}(x',y)$。
4. **共形校准**：
   - **Split CP**：基于校准集计算全局阈值 $\hat{q}_\alpha$，预测集为 $\{y: S(x,y)\le \hat{q}_\alpha\}$。
   - **Quasi-conditional CP（QCCP）**：通过增广分位数回归（对每个语义类学习自适应阈值）提供更强的条件覆盖保证。类函数 $\phi(x)$ 由SBERT嵌入+K-means聚类自动构建。
5. **理论分析**：
   - 引入“分布闭合性”假设：对同一输入两次释义等价于一次释义。在此假设下，证明了所提分数在释义下保持分数层面的交换性，从而恢复共形预测的覆盖保证。

## 3. 实验设计：数据集、场景、基准与方法对比

### 数据集
- **五个通用MCQA基准**：MMLU（QA）、CosmosQA（RC）、HellaSwag（CI）、HaluDial（DRS）、HaluSum（DS），各10,000题。
- **两个医学MCQA基准**：MedMCQA、MedQA（各抽样10,000题）。

### 实验场景
- **正常设置（Normal）**：训练、校准、测试均使用原始人类编写的问题。
- **完全改写设置（Fully Reworded）**：所有输入都经过LLM改写（施加相同的改写算子T）。
- **半改写设置（Semi-Reworded）**：训练和校准为原始问题，测试为改写后的问题。

### 对比方法
- **LAC**（Least Ambiguous set-valued Classifiers）：基于1-预测概率。
- **APS**（Adaptive Prediction Sets）：基于累积排序概率。

### 评价指标
- **覆盖率（CR）**：真实标签在预测集中的比例，目标为90%。
- **预测集大小（SS）**：平均包含的标签数量（越小越好）。

## 4. 资源与算力

论文**未明确说明**使用的GPU型号、数量或训练时长。仅提及在单块NVIDIA A100 GPU上测量了每阶段的耗时（Appendix F.8），但未给出总体训练或推理的算力开销。因此，无法准确评估该方法在资源需求方面的细节。

## 5. 实验数量与充分性

- **主体实验**：在7个数据集上，使用三种模型（Qwen2.5-7B、Llama-3.1-8B、Phi-3-small），分别测试Split CP和QCCP两种共形框架，共生成大量结果表（表1-4）。
- **消融与敏感性分析**：
  - 代理模型去除时的效果（图4、图8）。
  - 不同释义数量m的影响（表5）。
  - 不同分数变体（Mean/Weighted/Worst）的比较（图7）。
  - 不同风险水平α的实验（图6、图10）。
  - 不同嵌入/池化策略的鲁棒性（附录F.9）。
  - 不同释义生成器（Llama-3.1-8B替代Qwen2.5-7B）的验证（附录F.4）。
  - 类条件覆盖率的可视化（图5、图9）。
- **充分性评价**：实验覆盖了多种任务、模型、语义改写场景，消融全面，对比公平（均为相同CP框架下的非一致性分数）。但缺少对长文本生成任务的直接评估（论文在F.11讨论通过分解原子声明可扩展，但未实验）。总体而言，实验设计较充分且客观。

## 6. 论文的主要结论与发现

1. **LAC和APS在释义下性能退化**：LAC覆盖接近名义值但集大小严重膨胀（如MMLU下从3.44增至4.79）；APS经常过度覆盖（>95%），且集大小也较大。
2. **提出的PA分数**在正常、完全改写和半改写设置下均保持覆盖接近目标（90%），同时预测集大小显著小于基线（2–4倍缩小）。
3. **代理模型**显著提升准确性和校准性（图3），移除代理后集大小增大（图4、图8）。
4. **QCCP**相比Split CP提供了更好的类条件覆盖，但PA分数在两种框架下均稳定优于基线。
5. **跨模型泛化**良好：在Llama-3.1-8B和Phi-3-small上结果类似。
6. **医学领域**也验证了有效性（表4）。
7. **理论分析**表明在分布闭合性假设下，PA分数可恢复交换性，从而保证覆盖。

## 7. 优点

- **方法创新性**：首次将“释义鲁棒性”引入共形预测的分数设计，结合语义嵌入与轻量代理模型，实现了统计保证与语义不变性的统一。
- **理论贡献**：形式化定义了分布闭合性，并证明在此条件下分数交换性得以保持，为CP在非可交换数据上的应用提供了理论支撑。
- **实验充分且公平**：在多种数据集、模型、改写场景下进行了系统的比较和消融，结果具有说服力。
- **实用性**：提出的PA分数可无缝集成到现有CP框架中，计算开销主要来自LLM的释义生成，但可通过并行化缓解。

## 8. 不足与局限

- **实验范围**：所有评估均为多项选择问答（有限标签空间）。对于自由文本生成任务，论文仅提出扩展思路（分解为原子声明），未做实证验证。这限制了方法的直接应用范围。
- **释义质量依赖性**：性能高度依赖释义生成器的质量。若释义包含语义漂移（如低质量改写），可能引入噪声。论文虽验证了两种生成器（Qwen和Llama），但未系统分析生成质量对性能的敏感性。
- **分布闭合性假设**：理论分析依赖于“两次释义等价于一次释义”的假设，该假设在现实中可能不完全成立（尤其是当释义生成器具有随机性且语义可能逐渐漂移时），论文未提供检验该假设的实验。
- **计算成本**：生成m个释义（实验中m=6）需要多次调用LLM，对于实时或低延迟应用可能不可行。论文未讨论在资源受限场景下的替代方案。
- **类函数选择**：QCCP中使用的语义聚类（SBERT+K-means）可能对聚类数目敏感，论文虽使用轮廓系数自动选择，但未详细分析聚类稳定性对覆盖的影响。
- **基线选择**：仅与LAC和APS比较，忽略了其他近期CP改进（如ConU、SConU等）。虽然作者在附录F.6中说明了原因，但与更近期的CP方法对比会增强结论的时效性。

（完）
