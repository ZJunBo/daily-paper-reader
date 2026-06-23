---
title: "Minimal Ranks, Maximum Confidence: Parameter-efficient Uncertainty Quantification for LoRA"
title_zh: 最小秩，最大置信度：LoRA的参数高效不确定性量化
authors: "Patryk Marszałek, Klaudia Bałazy, Jacek Tabor, Tomasz Kuśmierczyk"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.findings-emnlp.66.pdf"
tags: ["query:luq"]
score: 8.0
evidence: 提出参数高效的贝叶斯LoRA用于LLM不确定性量化
tldr: 低秩适配（LoRA）虽高效但缺乏不确定性量化能力，贝叶斯变体则增加过多参数。本文提出基于子空间推断的参数高效贝叶斯LoRA，在保持LoRA效率的同时引入不确定性估计。通过子空间建模，该方法有效降低了贝叶斯变体的参数量和训练难度，实现了校准良好的不确定性量化。该工作为参数高效微调与不确定性量化的结合提供了实用方案。
source: EMNLP-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.66/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 816, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.66/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1070, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.66/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1540, \"height\": 724, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.66/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1557, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.66/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1489, \"height\": 430, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.66/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 491, \"height\": 414, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.66/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1325, \"height\": 1045, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.66/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1326, \"height\": 1044, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.66/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1327, \"height\": 796, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.66/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1327, \"height\": 798, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.66/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1327, \"height\": 1045, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.66/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1327, \"height\": 1044, \"label\": \"Table\"}]"
motivation: 标准LoRA缺乏不确定性量化导致过度自信，贝叶斯LoRA参数过多抵消效率优势。
method: 基于子空间推断提出参数高效的贝叶斯LoRA，在不增加大量参数的前提下进行不确定性量化。
result: 新方法在保持LoRA效率的同时实现了校准良好的不确定性估计。
conclusion: 该工作为参数高效微调与UQ的融合开辟了新途径。
---

## Abstract
Low-Rank Adaptation (LoRA) enables parameter-efficient fine-tuning of large language models by decomposing weight updates into low-rank matrices, significantly reducing storage and computational overhead. While effective, standard LoRA lacks mechanisms for uncertainty quantification, leading to overconfident and poorly calibrated models. Bayesian variants of LoRA address this limitation, but at the cost of a significantly increased number of trainable parameters, partially offsetting the original efficiency gains. Additionally, these models are harder to train and may suffer from unstable convergence.In this work, we propose a novel parameter-efficient Bayesian LoRA via subspace inference, demonstrating that effective uncertainty quantification can be achieved in very low-dimensional parameter spaces. The proposed method achieves strong performance with improved calibration and generalization while maintaining computational efficiency. Our empirical findings show that, with the appropriate projection of the weight space: (1) uncertainty can be effectively modeled in a low-dimensional space, and (2) weight covariances exhibit low ranks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：标准 LoRA（Low-Rank Adaptation）在微调大语言模型时虽然参数高效，但缺乏不确定性量化机制，导致模型过于自信且校准不良（overconfident and poorly calibrated）。贝叶斯 LoRA 变体（如 SWAG-LoRA）通过引入不确定性估计解决了这一问题，但代价是可训练参数数量显著增加（例如，即使 rank=2，参数量也比 LoRA 翻倍），部分抵消了 LoRA 原有的效率优势，且训练更困难、收敛不稳定。
- **动机**：需要在保持 LoRA 参数高效性的同时，实现有效的不确定性量化。核心假设：权重协方差本身具有低秩结构，且通过合适的投影可以在极低维参数空间中有效建模不确定性。
- **整体含义**：提出一种参数高效的贝叶斯 LoRA 方法（B-LoRA-XS），通过子空间推断在压缩后的低维参数空间学习贝叶斯后验，显著降低了贝叶斯变体的参数量和训练难度，实现了校准良好的不确定性估计，为参数高效微调与不确定性量化的结合提供了实用方案。

## 2. 方法论
### 核心思想
- 利用预训练权重的截断奇异值分解（truncated SVD）获得固定投影矩阵 \(A\) 和 \(B\)，将可训练参数限制为极小的内部矩阵 \(R \in \mathbb{R}^{r \times r}\)（每层）。然后对 \(R\) 施加贝叶斯处理（学习均值和协方差），从而在极低维参数空间（维度为 \(\sum_l r^2\)，远小于原始 LoRA 的 \( (m+n)r \)）实现不确定性量化。
- 该方法可视为子空间推断（Subspace Inference）的一种特例：将权重更新限制在由 SVD 方向张成的低维仿射流形上，并在此流形上执行贝叶斯平均。

### 关键技术细节
- **投影构造**：对每层预训练权重 \(W_0 \in \mathbb{R}^{m \times n}\) 计算 SVD：\(W_0 = U S V^T\)，取前 \(r\) 个奇异值/向量得到 \(A = U_r S_r\)，\(B = V_r^T\)。将这些投影矩阵冻结。
- **可训练参数**：中间矩阵 \(R \in \mathbb{R}^{r \times r}\)，每层仅 \(r^2\) 个参数。所有层的 \(R\) 向量化并拼接得到参数向量 \(\theta\)。
- **贝叶斯推理**：使用 SWAG（Stochastic Weight Averaging Gaussian）近似后验分布 \(p(\theta|D) \approx \mathcal{N}(\mu, \Sigma)\)。其中 \(\mu\) 是运行均值，协方差通过低秩近似（rank \(k\)）存储：\(\hat{\Sigma} \approx \frac{1}{2}(\hat{D}\hat{D}^T + \text{diag}(\hat{\sigma}^2))\)，\(\hat{D}\) 为最近 \(k\) 个参数向量与均值的差值矩阵。
- **推断**：从后验中采样 \(S\) 个 \(\theta\)，对每个样本计算对应的 \(\Delta W = A R B\)，进行模型平均预测。实际实现中无需显式计算 \(\Delta W\)，可以直接组合前向传播。

### 算法流程（文字说明）
1. 对每层待适配的权重矩阵 \(W_0^l\) 执行截断 SVD，得到固定投影 \(A_l, B_l\)。
2. 初始化每层内部矩阵 \(R_l\)（例如零矩阵）。
3. 烧入阶段（burn-in）：使用标准梯度下降（如 AdamW）训练 \(R_l\) 若干个 epoch（10 或 25）。
4. 之后进入 SWAG 阶段：持续维护均值 \(\mu\) 的指数移动平均，存储最近 \(k\) 个参数向量的差值，并计算参数二阶矩的移动平均。
5. 训练结束后，根据存储的统计量构造低秩协方差矩阵。
6. 预测时，从 \(\mathcal{N}(\mu, \hat{\Sigma})\) 中采样 \(S\) 个参数，分别计算输出并取平均。

## 3. 实验设计
- **数据集**：GLUE 基准的四个任务：RTE、MRPC、CoLA、SST-2。使用原始训练-验证划分。
- **模型**：RoBERTa-large（355M 参数）。
- **对比方法**：
  - 标准 LoRA
  - LoRA-XS（参数高效的非贝叶斯变体）
  - SWAG-LoRA（贝叶斯变体基线）
- **配置**：LoRA/LoRA-XS/B-LoRA-XS 的 rank \(r \in \{2,8,16,25\}\)；SWAG-LoRA 因计算限制仅测试 \(r=2,8\)。SWAG 协方差秩 \(k\) 默认 10，部分实验改变 \(k\)（0,2,5,10,20）。
- **评估指标**：准确率（Accuracy）、期望校准误差（ECE）、负对数似然（NLL）。报告 5 次运行的中位数 ± 标准差。
- **消融实验**：
  - 协方差矩阵秩 \(k\) 的影响（图4，表5-6）。
  - 训练数据量缩减的影响（图5，使用 10%, 25%, 50% 数据）。
  - 不同 rank \(r\) 与 \(k\) 组合的性能对比（图3，表1-4）。

## 4. 资源与算力
- **GPU 型号**：RTX 4090 和 V100-SXM2-32GB。
- **每个实验**：单 GPU 运行。
- **总 GPU 时间**：约 63 天（原文 “«63 days”）。
- **未详细说明**：未给出每个具体配置的运行时间、能耗等细粒度信息。

## 5. 实验数量与充分性
- **实验数量**：在 4 个数据集上，对 6 种方法（含变体）进行了多 rank、多 \(k\) 的组合测试，总计至少几十组实验（每个配置 5 次运行）。另外包含协方差秩分析、数据缩减分析等消融实验。
- **充分性**：
  - **积极方面**：覆盖了主要 GLUE 任务，对比了非贝叶斯和贝叶斯的典型方法（LoRA、LoRA-XS、SWAG-LoRA），分析了关键超参数（\(r,k\)）的影响，进行了数据规模敏感性测试。统计报告了中位数和标准差，有 5 次重复。
  - **局限**：仅使用 RoBERTa-large 一个模型；仅涉及分类任务（GLUE）；未在生成式任务（如文本生成、翻译）或更大模型（如 LLaMA、GPT）上验证；对比的贝叶斯基线仅 SWAG-LoRA，未包含 Laplace-LoRA、BLoB、Bella 等方法；未做交叉验证或更深入的超参数搜索（例如 SWAG-LoRA 仅测试了 \(r=2,8\)）；未报告运行时间的详细对比。

## 6. 主要结论与发现
- B-LoRA-XS 在保持与 LoRA 相近参数量的同时，显著降低了 ECE 和 NLL，实现了更好的校准。例如，\(r=8\) 时参数仅为 LoRA 的 1/10，而 ECE 降低约一半。
- 相比 SWAG-LoRA，B-LoRA-XS 在达到相当或更好的校准性能时，参数数量减少了 5–15 倍，且训练更稳定（SWAG-LoRA 对 \(k\) 敏感，小 \(k\) 时校准恶化）。
- 极低协方差秩（如 \(k=2\)）足以实现良好的不确定性量化，说明 SVD 投影有效地解耦了参数，使得权重协方差本质上是低秩的。
- 在数据缩减场景下，贝叶斯方法（包括 B-LoRA-XS）并未表现出比非贝叶斯更强的鲁棒性（准确率下降类似），但校准优势依然存在。

## 7. 优点
- **参数高效**：将贝叶斯推理压缩到极低维空间（每层 \(r^2\) 参数），比现有贝叶斯 LoRA 变体少一个数量级以上的参数。
- **良好校准**：在多个 GLUE 任务上持续获得更低的 ECE 和 NLL，尤其关注校准（而非仅准确率）。
- **训练稳定**：相比 SWAG-LoRA 对协方差秩敏感，B-LoRA-XS 在较宽的 \(k\) 范围内表现稳健。
- **简洁框架**：方法基于现有技术（SVD 投影 + SWAG），实现简单，易于集成到 LoRA 框架中。
- **理论支撑**：通过子空间推断统一视角，解释了为何低维投影足以捕获不确定性。

## 8. 不足与局限
- **依赖初始 SVD**：若下游任务与预训练任务差异较大，主奇异方向可能不适用，性能可能下降。
- **近似贝叶斯方法单一**：仅使用 SWAG，未探索其他变分推断或 Laplace 近似等可能更优的选项。
- **推理开销**：仍需要多次前向传播采样（\(S=15\)），比非贝叶斯方法慢。
- **实验覆盖有限**：仅针对 RoBERTa-large 和 GLUE 分类任务；未在更大模型（如 7B+）、生成任务（如翻译、摘要）或更复杂推理任务上验证。
- **超参数调优**：rank \(r\) 和协方差秩 \(k\) 的可能需要针对不同数据集调整，增加了实际应用中的调参负担。
- **对比不完整**：未与最新贝叶斯 PEFT 方法（如 BLoB、Bella）进行直接比较，也未测试更大规模的 SWAG-LoRA（如 \(r=16,25\)）以公平对比。
- **数据缩减分析**：仅测试了随机子采样，未考虑分布偏移或 OOD 场景。

（完）
