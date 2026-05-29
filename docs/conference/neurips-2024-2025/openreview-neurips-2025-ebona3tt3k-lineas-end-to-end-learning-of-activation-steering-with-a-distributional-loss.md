---
title: "LinEAS: End-to-end Learning of Activation Steering with a Distributional Loss"
title_zh: LinEAS：基于分布损失的端到端激活转向学习
authors: "Pau Rodriguez, Michal Klein, Eleonora Gualdoni, Valentino Maiorca, Arno Blaas, Luca Zappella, marco cuturi, Xavier Suau"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=EBONa3tT3K"
tags: ["query:dg"]
score: 7.0
evidence: 端到端学习激活转向，使用分布损失
tldr: 现有激活转向方法通过局部匹配修正分布差异，效果粗糙。本文LinEAS端到端学习转向映射，并采用分布损失函数使源激活分布更接近目标分布，在内容安全控制任务上显著优于传统方法。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1340, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1445, \"height\": 388, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1414, \"height\": 334, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1445, \"height\": 313, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1445, \"height\": 653, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 584, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1445, \"height\": 315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1444, \"height\": 724, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1412, \"height\": 305, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1417, \"height\": 1300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1331, \"height\": 520, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1122, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1450, \"height\": 1540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1454, \"height\": 1519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1456, \"height\": 1547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1460, \"height\": 1302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1459, \"height\": 1301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ebona3tt3k/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1458, \"height\": 1302, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1208, \"height\": 934, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 701, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1316, \"height\": 355, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 500, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1074, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1149, \"height\": 139, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1161, \"height\": 1520, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1234, \"height\": 1341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1449, \"height\": 1148, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 989, \"height\": 378, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1350, \"height\": 343, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1691, \"height\": 985, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1658, \"height\": 1121, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1461, \"height\": 730, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1027, \"height\": 1750, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ebona3tt3k/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1450, \"height\": 1723, \"label\": \"Table\"}]"
motivation: 当前快速激活转向方法仅局部调整，分布修正不精确。
method: 端到端学习一个映射函数，以最小化源与目标激活分布之间的分布损失。
result: 在毒性和风格转换任务上，LinEAS实现了更精确的生成控制。
conclusion: 分布级损失能有效提升激活转向的保真度。
---

## Abstract
The growing use of generative models in daily life calls for efficient mechanisms to control their generation, to e.g. produce safe content or provide users with tools to explore style changes. Ideally, such mechanisms should require low volume of unpaired data (\ie without explicit preference), and should be cheap, both at train and inference time, while preserving output quality. Recent research has shown that such mechanisms can be obtained by intervening exclusively on model activations, with the goal of correcting distributional differences between activations seen when using prompts from a source vs. a target set (e.g. toxic and non-toxic sentences). While cheap, these fast methods are inherently crude: their maps are tuned locally, not accounting for their impact on downstream layers, resulting in interventions that cause unintended shifts when used out-of-sample. We propose in this work linear end-to-end activation steering (LinEAS), an approach trained with a global loss that accounts simultaneously for all layer-wise distributional shifts. In addition to being more robust, the loss used to train LinEAS can be regularized with sparsifying norms, which can automatically carry out neuron selection. LinEAS only requires a handful of unpaired samples to be effective, and beats similar baselines on toxicity mitigation in language models, becoming competitive with oracle-dependent methods that have access to strong supervision. LinEAS is modality-agnostic and we empirically find that it outperforms existing activation steering methods at mitigating and including new concepts at the output of single-step text-to-image generation models.

---

## 论文详细总结（自动生成）

# 论文总结：LinEAS：基于分布损失的端到端激活转向学习

## 1. 核心问题与整体含义（研究动机与背景）

- **研究动机**：随着生成式模型（LLM和文本到图像模型）的广泛应用，需要高效、可控的机制来调节模型输出（例如避免有害内容、实现风格变换）。理想的调节机制应满足：**低数据需求**（无需配对数据或显式偏好）、**训练与推理成本低**、**保持输出质量**。
- **现有方法局限**：已有的激活转向方法（如ITI-C、Lin-AcT）通过局部调整激活分布来修正源与目标之间的分布差异，但它们是“粗糙的”——仅独立调整每一层，未考虑跨层因果影响，导致干预效果在外推时产生意外偏移。
- **本文贡献**：提出**LinEAS**，一种**端到端学习的线性激活转向方法**，通过全局分布损失同时考虑所有层的分布偏移，从而提高鲁棒性和控制精度。同时引入稀疏正则化实现自动神经元选择，仅需少量未配对样本即可生效，在多任务上超越同类方法。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：在预训练模型的中间层之间插入线性仿射变换（每层一个），并通过**端到端优化**最小化源域和目标域在所有层上的激活分布差异。
- **关键公式与流程**：
  - 模型表示为：`o = f_{L+1} ∘ T_L ∘ f_L ∘ … ∘ T_1 ∘ f_1(x)`
  - 对源域样本 `x_i ~ p`，经过变换后的激活：`ξ_i^ℓ = T_ℓ ∘ f_ℓ ∘ … ∘ T_1 ∘ f_1(x_i)`
  - 对目标域样本 `y_j ~ q`，保持原模型：`η_j^ℓ = f_ℓ ∘ … ∘ f_1(y_j)`
  - 每层分布差异使用**切片Wasserstein距离**（Sliced Wasserstein Distance）的坐标和：`∆(U,V) = Σ_j W²₂([U·j], [V·j])`
  - 总损失：`L(w,b) = E[Σ_ℓ ∆(ξ_i^ℓ, η_j^ℓ)] + γR(w,b)`，其中R为稀疏/组稀疏正则化（`R₁`和`R_G`）
  - **变换形式**：`T_ℓ(z) = ω_ℓ ⊙ z + b_ℓ`，`ω_ℓ`, `b_ℓ`为可学习参数。
  - **优化**：使用近端随机梯度下降（PSGD），学习率0.1，余弦衰减。
- **稀疏正则化**：通过`λ₁`和`λ_G`控制，自动选择要干预的神经元/层，减少不必要的修改，提升效用（utility）。

## 3. 实验设计：数据集、基准场景和对比方法

- **LLM毒性缓解**：
  - 数据集：Jigsaw（32个有毒+32个无毒句子训练），RealToxicityPrompts（RTP）和Thoroughly Engineered Toxicity（TET）测试。
  - 评估指标：毒性比例（Tox RTP, Tox TET）、困惑度（PPL WIK）、MMLU准确率。
  - 对比方法：Prompting、CAA、ReFT、ITI-C、Lin-AcT，以及有监督的Oracle（LoFIT-RL）。
  - 模型：Qwen2.5-1.5B、Gemma2-2B、Qwen2.5-7B（以及DeepSeek-7B在附录中）。
- **文本到图像（T2I）风格控制**：
  - 模型：DMD2（单步扩散模型）。
  - 数据集：15个概念（风格、对象、透视），每个概念32个提示。
  - 指标：用户偏好、IMGScore（与原始图像相似度）、CLIPScore（概念一致性）。
  - 对比方法：ITI-C、Lin-AcT。
- **额外实验**：成分性（compositionality）、稀疏性影响、层选择鲁棒性、人工评估。

## 4. 资源与算力

- **硬件**：单张NVIDIA A100（80GB RAM），也可在40GB版本上运行。
- **训练时间**（以Qwen2.5-7B为例）：
  - ITI-C：37s（1步）
  - Lin-AcT：30s（1步）
  - LinEAS：500s（1000步）
  - LoFIT-RL（Oracle）：27300s（100步）
- 代码未开源，但论文提供了算法细节。

## 5. 实验数量与充分性

- **大量实验**：涵盖4种LLM、2种毒性数据集、多种数据量（N=1~1024）、多组随机种子、多种干预层类型、稀疏性参数扫描、成分性实验、TruthfulQA实验。
- **消融实验**：数据量对性能影响（图3）、稀疏性对毒性和效用权衡（图4、图8）、层选择鲁棒性（表9）、成分性（图9）。
- **人工评估**：LLM和T2I各有人类偏好测试（各约20名参与者，多次评估）。
- **客观性**：方法均在同一低数据设置下比较，统计误差（标准差）报告，但Oracle方法（LoFIT-RL）有强监督优势，对比公平。
- **充分性**：实验覆盖了核心场景和消融，但成分性任务绝对性能仍较低（19%），表明仍有挑战。

## 6. 主要结论与发现

- **LinEAS在毒性缓解上显著优于同类弱监督方法**（ITI-C、Lin-AcT），且在低数据（32样本）下与强监督Oracle（LoFIT-RL）效果接近，同时保持更低的效用下降。
- **端到端优化比逐层优化更鲁棒**：误差不累积，性能更稳定。
- **稀疏正则化可自动选择神经元**：将支持度降至~1%时仍保持毒性缓解，且效用得到改善。
- **T2I风格控制**：LinEAS在用户偏好（63.3%）、IMGScore（0.66）上大幅优于ITI-C（12.4%，0.24）和Lin-AcT（24.4%，0.45），CLIPScore持平。
- **成分性**：LinEAS的组合映射联合概率（19%）比Lin-AcT（1.3%）高15倍，但仍低于实用要求。

## 7. 优点

- **方法新颖**：首次将端到端全局优化与切片Wasserstein损失结合用于激活转向，解决局部匹配的因果不一致问题。
- **实用性强**：仅需少量未配对数据（32组），训练和推理轻量，干预参数极少（`ω`, `b`），可调节强度λ。
- **可解释性**：稀疏正则化自动选择关键神经元/层，提高效率并解释模型行为。
- **模态无关**：同时验证了LLM和T2I两个不同模态。
- **实验详尽**：包含多种模型、数据集、消融、人工评估，对比基线全面。

## 8. 不足与局限

- **成分性不足**：虽然比基线好，但多概念联合出现概率仅19%，远未实用。
- **干预全局性**：当前对所有token/像素施加相同干预，无法选择性忽略某些输入部分，增加细粒度控制难度。
- **计算开销**：训练时间比逐层方法长（500s vs 30s），但比强监督方法（27300s）快得多；未讨论推理额外开销。
- **依赖层选择**：虽然鲁棒性更好，但仍需指定干预的层类型（如所有归一化层），未完全自动化。
- **安全风险**：恶意用户可能利用该方法反向引导模型产生有害内容（作者认为可通过提示工程同样实现）。
- **缺少理论证明**：算法基于最优传输理论，但未提供收敛性等理论分析。
- **代码未开源**：影响可复现性。

（完）
