---
title: Data Mixing Optimization for Supervised Fine-Tuning of Large Language Models
title_zh: 大型语言模型监督微调的数据混合优化
authors: "Yuan Li, Zhengzhong Liu, Eric P. Xing"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=19kqoNoc2N"
tags: ["query:smd"]
score: 7.0
evidence: 优化SFT数据混合，可迁移至安全数据
tldr: 论文将监督微调中的数据混合建模为优化问题，通过有效数据传输和缩放定律参数化损失函数，并利用小规模实验拟合参数以推导最优混合权重。尽管不专门针对安全数据，但其方法可直接应用于安全对齐数据与普通微调数据的混合，为缓解安全退化提供通用的数据优化框架。实验证明该方法能提升所有领域的整体和个体性能。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-19kqonoc2n/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 847, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-19kqonoc2n/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 751, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-19kqonoc2n/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1668, \"height\": 821, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-19kqonoc2n/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 840, \"height\": 357, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-19kqonoc2n/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 844, \"height\": 206, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-19kqonoc2n/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 632, \"height\": 606, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-19kqonoc2n/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 855, \"height\": 640, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-19kqonoc2n/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1733, \"height\": 564, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-19kqonoc2n/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 746, \"height\": 167, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-19kqonoc2n/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1339, \"height\": 210, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-19kqonoc2n/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 769, \"height\": 615, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-19kqonoc2n/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1078, \"height\": 634, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-19kqonoc2n/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1265, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-19kqonoc2n/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 704, \"height\": 943, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-19kqonoc2n/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 753, \"height\": 914, \"label\": \"Table\"}]"
motivation: 监督微调中数据混合的优化对通用模型开发至关重要，但该领域研究不足。
method: 提出一种基于参数化损失和缩放定律的数据混合优化方法，通过小规模实验拟合参数得到最优权重。
result: 数学证明和实验表明算法在各领域均能达到出色的整体和个体性能。
conclusion: 所提方法为数据混合优化提供了可靠框架，可扩展至安全数据场景。
---

## Abstract
Optimizing data mixtures for supervised fine-tuning (SFT) of large language models (LLMs) is critical for developing general-purpose models, yet this area remains underexplored. In this paper, we frame data mixing as an optimization problem and introduce a novel method designed to minimize validation loss. Our approach parametrizes the loss by modeling effective data transferred and leveraging scaling laws for fine-tuning. By experimenting with various small-scale data mixtures, we fit these parameters and derive the optimal weights. We provide both mathematical proofs and empirical results demonstrating that our algorithm achieves excellent overall and individual performance across all domains. Through controlled experiments, we show that models trained with our optimized weights perform on par with those using optimal weights determined via grid search, with per-domain loss only 0.66\% higher than the best domain loss from grid search on average. Additionally, we show that reweighting popular SFT datasets using our method improves both validation loss and downstream performance. Finally, we discuss how our method can generalize to guide data selection for domain-specific models and provide insights into SFT.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLM）在监督微调（SFT）阶段，需要混合来自不同领域（如数学、代码、通用指令）的数据。数据混合的比例（即各领域的权重）对模型性能有重要影响。然而，现有工作多聚焦于预训练阶段的数据混合，针对SFT的数据混合优化方法尚不充分。预训练方法（如DoReMi、Data Mixing Laws）存在以下问题：(1) 基于小代理模型优化的权重难以迁移到大模型上，因为SFT模型有各自不同的预训练分布；(2) 现有参数化方法未考虑域间的交互和缩放效应，在数据量增大时容易导致权重极端化，某些域被忽略。
- **整体含义**：本文首次将SFT数据混合系统性地建模为优化问题，提出了一种参数化验证损失、利用缩放定律和有效数据传输概念的新方法，旨在同时最小化总体验证损失并保证各域性能均衡。

## 2. 方法论：核心思想、关键技术细节、公式与算法流程

- **核心思想**：将验证损失表示为各域数据规模的函数，其中引入“有效数据传输”概念：某个域的验证损失受该域自身数据量和其他域数据量（通过迁移效果）的共同影响。利用SFT缩放定律（幂律关系）参数化损失，然后通过小规模扰动实验拟合每个域的特定参数，最后求解最优权重。
- **关键技术细节**：
  1. **问题形式化**：设总资源为 \(N_0\) 个token，域 \(i\) 的权重为 \(w_i\)（满足 \(\sum w_i =1\)）。目标是优化权重使验证损失最小。
  2. **损失参数化**：对于域 \(i\)，验证损失近似为：
     \[
     \tilde{L}_i \approx C_i \cdot \left( w_i N_0 + k_i (N_0 - w_i N_0)^{\alpha_i} \right)^{-\beta_i} + E_i
     \]
     其中 \(w_i N_0\) 是域内数据量，第二项代表从其他域迁移来的有效数据量（建模为其他域数据总量的幂函数），\(C_i, k_i, \alpha_i, \beta_i, E_i\) 为域特定参数。
  3. **参数拟合**：固定其他域数据量，将域 \(i\) 的数据量分别设为 \(n, n/2, n/3, 2n, 3n\)（共5个扰动点），训练模型并记录每个配置下的验证损失，然后用Huber损失 + Trust Region方法拟合五个参数。
  4. **权重优化**：基于拟合好的参数，对给定总预算 \(N_0\)，使用序列最小二乘规划（SLSQP）求解最小化总损失的最优权重向量 \(w\)（凸优化问题，有唯一全局最优解）。
- **算法流程**（Algorithm 1）：
  - 初始化：从每个域采样等量数据，在初始混合上训练模型得到初始损失。
  - 扰动实验：对每个域，分别以4种不同比例（1/2, 1/3, 2, 3）采样该域数据，保持其他域固定，训练模型并记录验证损失。
  - 参数估计：利用5组数据点，用Trust Region方法拟合每个域的5个参数。
  - 权重求解：用SLSQP求解式(6)得到最优权重 \(w^*\)。

## 3. 实验设计：数据集、场景、基准对比

- **数据集**：
  - **三域可控实验**：通用指令遵循（Infinity-Instruct子集）、数学（OpenMathInstruct-2）、代码（OpenCoder）。每个域初始采样660K token。
  - **流行SFT集合再加权**：Tulu3（6个技能域：通用、知识回忆、数学、代码、精确指令、安全）和Orca（4个数据源域：T0, CoT, FLAN, NIV）。
  - **医学专用案例**：通用指令数据（Alpaca-GPT4） + 医学问答数据（PubMedQA）。
- **评估基准**：
  - 主要指标：token级别困惑度（PPL），在保留的每个域的验证集上计算。
  - 下游任务：AGIEval, IFEval, MMLU, GSM8K, HumanEval, Safety（ToxiGen + TruthfulQA），HellaSwag等。
- **对比方法**：
  - 可控实验：网格搜索所有满足 \(\sum w_i=1\) 的21种混合权重作为黄金标准。
  - 再加权实验：原始权重、等token权重（Equal T）、等实例权重（Equal I）。
- **模型**：Qwen2.5 (0.5B, 1.5B, 32B), Llama3.2-3B, Llama3.1 (8B, 70B)。

## 4. 资源与算力

- 论文未明确说明使用的GPU总数量、具体训练时长。仅提及**所有实验在NVIDIA H100 GPU上进行**，并报告了各配置下的最大训练步数（如5M budget为200步，20M为400步，200M为2500步，Tulu3/Orca为6000步），学习率按模型设置（1e-5至2e-6不等）。未提供完整算力消耗估计。

## 5. 实验数量与充分性

- **实验数量**：
  - 可控实验：3种数据预算 × 4个模型 × 21个网格搜索权重 + 每个扰动配置的训练（约4×5=20次额外训练），总计约数百次训练。
  - 再加权实验：2个SFT集合 × 3~4个模型 × 4种权重配置（原始、Equal T、Equal I、Ours）。
  - 医学案例：1个实验对比两种配置。
- **充分性与公平性**：实验设计覆盖了不同模型族（Qwen, Llama）、不同规模（0.5B至70B）、不同数据预算（5M~200M）。与网格搜索的直接对比确保了基准的可靠性。再加权实验中包含多种基线。但部分实验（如Orca）中验证损失与下游性能脱节，说明了验证集选择的重要性，但也暴露了方法在特定场景下的局限性。

## 6. 论文的主要结论与发现

- 提出的方法能够高效找到接近最优的数据混合权重，平均每域PPL仅比网格搜索最佳值高0.66%。
- 权重具有**尺度依赖性**：最优权重随总数据预算变化而变化，不满足尺度不变性假设；随着预算增大，权重变化趋于稳定。
- 方法能确保**无域被忽略**（No Domains Left Behind）：由于幂律递减效应，任何域都不会被分配极端小权重，各域性能均衡。
- 在Tulu3集合上，再加权后不仅降低了验证损失，也提升了多个下游任务的平均性能（如Llama3.1-8B平均提升0.3%）。
- 医学案例表明，即使验证集仅包含医学数据，混合通用指令数据（占67.7%）优于仅用医学数据，体现了“鸡尾酒效应”。

## 7. 优点

- **理论严谨**：证明目标函数是凸的（附录B），并给出“无域被遗漏”的KKT条件证明（附录C）。
- **可解释性强**：每个域的参数（尤其是\(\beta_i\)）可直接解释该域数据缩放的有效性。
- **方法通用**：不依赖于特定模型架构，适用于多种LLM和SFT集合，可扩展至领域专用模型。
- **实验覆盖广**：跨模型族（Qwen、Llama）、多规模（0.5B~70B）、多数据预算，对比了网格搜索等多种强力基线。
- **实践指导意义**：提出通过明确将域定义为任务/技能（如Tulu3）可提高下游性能，并建议联合合成数据生成进一步提升效果。

## 8. 不足与局限

- **参数拟合依赖扰动实验**：需要针对每个域进行5次额外训练（改变该域数据量），这些扰动点的选择（比例）可能影响拟合精度，论文未对扰动比例的选择进行敏感性分析。
- **域定义模糊**：当域按数据源（如Orca中的FLAN）定义时，域内分布高度异质，导致验证集与下游任务不匹配，优化效果受限（Orca实验验证损失降低但下游性能未显著提升）。
- **下游性能提升不稳定**：在Tulu3上表现良好，但在Orca上提升微弱甚至略低于某些基线，说明方法对验证集设计敏感。
- **未探索合成数据**：论文指出如果对权重大的域生成更多样化数据（而非简单重复采样）可能更好，但未进行相关实验。
- **算力报告不完整**：未提供具体的GPU耗时和成本，影响可复现性评估。
- **局限性仍存**：对于预训练数据分布差异极大的模型，小规模扰动实验拟合的参数能否准确推广到大预算，尚需更多验证（论文仅通过网格搜索对比有限预算）。

（完）
