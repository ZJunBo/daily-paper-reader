---
title: "SUE: Sparsity-based Uncertainty Estimation via Sparse Dictionary Learning"
title_zh: SUE：基于稀疏字典学习的稀疏性不确定性估计
authors: "Tamás Ficsor, Gábor Berend"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.emnlp-main.1671.pdf"
tags: ["query:uq-safety"]
score: 6.0
evidence: 基于稀疏字典学习的不确定性估计，适用于包括LLM在内的深度模型
tldr: 深度学习模型在高风险场景需要不确定性估计。本文提出基于稀疏字典学习的方法，通过识别与误分类相关的字典原子来估计不确定性。实验证明在多个模型上有效。该方法为通用UE提供新思路。
source: EMNLP-2025-Main
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1671/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 474, \"height\": 331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1671/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1643, \"height\": 360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1671/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 776, \"height\": 1531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1671/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 639, \"height\": 757, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1671/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 786, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1671/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1505, \"height\": 1576, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1671/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1503, \"height\": 1574, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1671/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1503, \"height\": 1573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1671/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 639, \"height\": 1988, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1671/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 759, \"height\": 1313, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1671/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1129, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1671/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 800, \"height\": 333, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1671/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 762, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1671/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 762, \"height\": 255, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1671/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 763, \"height\": 254, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1671/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 763, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1671/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1665, \"height\": 1516, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1671/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 815, \"height\": 495, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1671/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 808, \"height\": 370, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1671/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 752, \"height\": 370, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1671/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1650, \"height\": 631, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1671/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1662, \"height\": 2147, \"label\": \"Table\"}]"
motivation: 现有UE方法多基于置信度或贝叶斯，本文探索字典学习。
method: 利用点互信息识别与误分类样本关联的字典原子。
result: 在多种模型上验证了方法的有效性。
conclusion: 提出一种非传统的不确定性估计框架。
---

## Abstract
The growing deployment of deep learning models in real-world applications necessitates not only high predictive accuracy, but also mechanism to identify unreliable predictions, especially in high-stakes scenarios where decision risk must be minimized. Existing methods estimate uncertainty by leveraging predictive confidence (e.g., Softmax Response), structural characteristics of representation space (e.g., Mahalanobis distance), or stochastic variation in model outputs (e.g., Bayesian inference techniques such as Monte Carlo Dropout). In this work, we propose a novel uncertainty estimation (UE) framework based on sparse dictionary learning by identifying dictionary atoms associated with misclassified samples. We leverage pointwise mutual information (PMI) to quantify the association between sparse features and predictive failure. Our method – Sparsity-based Uncertainty Estimation (SUE) – is computationally efficient, offers interpretability via atom-level analysis of the dictionary, has no assumption about the class distribution (unlike Mahalanobis distance). We evaluated SUE on several NLU benchmarks (GLUE and ANLI tasks) and sentiment analysis benchmarks (Twitter, ParaDetox, and Jigsaw). In general, SUE outperforms or matches the performance of other methods. SUE performs particularly well when there is considerable uncertainty in the model, i.e., when the model lacks high precision.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

深度学习模型在实际部署中（如医疗、法律、内容审核等高风险场景）不仅需要高预测精度，还需要能够识别不可靠的预测，以降低决策风险。现有不确定性估计（UE）方法包括：
- 基于输出置信度（如 Softmax Response, SR），但软max概率往往校准不良且过于自信；
- 基于表示空间结构（如 Mahalanobis Distance, MD），但依赖于每类预先定义的均值和协方差假设；
- 基于贝叶斯推理（如 Monte Carlo Dropout, MC），但计算开销大，需要多次前向传播。

**本文提出一种基于稀疏字典学习的不确定性估计框架 SUE**，通过识别与误分类样本强烈关联的字典原子，利用点互信息（PMI）量化稀疏特征与预测失败之间的关联，从而获得既高效又具有可解释性的不确定性评分。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

**核心思想**：将模型的 [CLS] 嵌入向量分解为稀疏线性组合的字典原子，利用 PMI 衡量每个原子与正确/错误分类的共现关系，然后通过加权求和得到不确定度。

**关键技术步骤**：
1. **构建稀疏表示**：  
   对 [CLS] 嵌入矩阵 \( X \in \mathbb{R}^{N \times d} \)，学习一个字典矩阵 \( D \in \mathbb{R}^{K \times d} \) 和稀疏系数 \( \alpha \in \mathbb{R}^{N \times K} \)，通过最小化目标：
   \[
   \min_{\alpha,D} \frac{1}{2} \|X - \alpha D\|_F^2 + \lambda \|\alpha\|_1
   \]
   其中 \( K \) 是原子数，\( \lambda \) 是稀疏正则化系数。仅用训练集中**正确分类**的样本字典学习，以避免噪声。

2. **识别与不确定性相关的原子**：  
   构建原子激活与预测正确性的共现矩阵 \( C \in \mathbb{R}^{K \times 2} \)：
   \[
   C_{k,l} = \sum_{n=1}^N \mathbb{I}[\alpha^{(n,k)} \neq 0 \land L^{(n)} = l]
   \]
   其中 \( l=0 \) 表示错误分类，\( l=1 \) 表示正确分类。  
   计算 PMI：
   \[
   \Phi_{k,l} = \log \frac{P(k,l)}{P(k)P(l)}
   \]

3. **计算不确定性分数**：  
   对测试样本 \( i \)，其不确定性为：
   \[
   U^{(i)}_{\text{SUE}} = -\alpha^{(i)}_{\text{test}} \cdot \Phi_{(:,1)}
   \]
   其中 \( \Phi_{(:,1)} \) 是正确分类对应的 PMI 值。负号使得高值对应高不确定性。

**算法流程**（参见图2）：
- 在校准集上训练字典 \( D \)（仅用正确样本）→ 推理所有样本的稀疏系数 → 构建共现矩阵 \( C \) → 计算 PMI 矩阵 \( \Phi \) → 对测试样本计算 \( U_{\text{SUE}} \)。

### 3. 实验设计：使用的数据集、场景、基准、对比方法

**数据集**：
- **情感分析/毒性检测**：ParaDetox, Twitter Sentiment, Jigsaw Toxic Comment（均二值化）。
- **自然语言理解**：ANLI (R1/R2/R3) 及 GLUE 中的 CoLA, MRPC, QNLI, SST-2, QQP。
- 所有数据集均划分训练集、校准集、验证集和测试集。

**评估指标**：**Excess Area Under the Risk-Coverage Curve (eAU-RCC)**，值越低表示不确定性估计越好。

**对比方法**：
- Softmax Response (SR)
- Shannon Entropy (SE)
- Mahalanobis Distance (MD) 和 MD++
- Monte Carlo Dropout 变体：MC-SMP, MC-PV, MC-BALD（T=10,25,50）
- 本文方法 SUE

**模型**：BERT-Base, BERT-Large, RoBERTa-Base 微调后的 checkpoint。

### 4. 资源与算力

论文中**未明确说明**使用的 GPU 型号、数量或训练时长。仅致谢部分提到使用了 ELKH Cloud 计算资源，并指出代码已开源。因此算力细节未知。

### 5. 实验数量与充分性

- **实验数量**：覆盖 3 个模型 × 7 个任务（3 个情感 + 3 个 ANLI + 5 个 GLUE，但 GLUE 仅用 BERT-Large），且对每个任务报告 3 次运行的平均值和标准差。
- **超参数消融**：系统研究了字典学习中的正则化强度 \( \lambda \) (6 个值)、原子数 \( K \) (3 个值) 以及校准集分割比例 (4 个值) 的影响，绘制了大量热力图。
- **与多项基线对比**：包括 3 种经典方法和 3 种 MC 变体。
- **可解释性分析**：展示了误分类但高置信度样本，并可视化每个原子的贡献。

**充分性评价**：实验设计全面，涵盖了不同难度任务、不同模型规模，超参数空间探索充分，对比方法丰富，结果统计具有稳健性。实验是客观且公平的。

### 6. 论文的主要结论与发现

- SUE 在**较难的 ANLI 和 Jigsaw 任务上显著优于所有对比方法**（eAU-RCC 降低 5~10%），在简单任务（如 ParaDetox、Twitter）上与 MC 方法竞争力相当或略逊。
- SUE **特别适合模型不确定性高（精度低）的场景**，此时优势更明显。
- 超参数选择建议：固定 \( \lambda = 1.2/\sqrt{d} \)（约 0.043），原子数 \( K \) 可根据任务难度和样本量选取，超参数性能稳健（验证集与测试集表现一致）。
- 稀疏表示具有**可解释性**：可以可视化每个原子对最终不确定性分数的贡献，帮助识别误分类原因。

### 7. 优点：方法或实验设计上的亮点

- **新颖且通用**：首次将稀疏字典学习应用于不确定性估计，无需类分布假设。
- **计算高效**：只需一次前向传播获得稀疏系数，不需要多次随机采样（与 MC 相比）。
- **可解释性强**：通过原子水平的 PMI 和贡献图，可追溯模型不确定性的来源。
- **超参数稳健**：理论值推荐合理，且实验显示验证集最佳参数能良好迁移到测试集。
- **评估充分**：在多个模型、多个任务上进行了严格对比，并提供了超参数影响的详细分析。

### 8. 不足与局限

- **实验覆盖有限**：仅在序列分类任务上评估，未覆盖生成式任务（如文本生成）或其他模态（图像、语音）。
- **模型规模**：仅限于 BERT-Base/Large 和 RoBERTa-Base，未在更大模型（如 GPT、LLaMA）上验证；未说明 GPU 算力消耗。
- **简单任务上竞争力不足**：在 ParaDetox 等低不确定性任务上，SUE 的 eAU-RCC 高于 MC 方法，说明其在低不确定性场景下可能不如基于方差的方法。
- **超参数仍需调节**：尽管有理论推荐，但原子数 \( K \) 仍依赖于验证集选择；不同任务的最优 \( K \) 可能不同。
- **仅使用正确样本训练字典**：如果训练集中正确样本本身存在偏差，可能影响字典质量。

（完）
