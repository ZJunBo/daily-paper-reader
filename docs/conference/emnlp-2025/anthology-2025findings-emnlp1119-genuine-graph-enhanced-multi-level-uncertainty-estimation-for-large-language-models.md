---
title: "GENUINE: Graph Enhanced Multi-level Uncertainty Estimation for Large Language Models"
title_zh: GENUINE：增强大语言模型不确定性估计的图多级方法
authors: "Tuo Wang, Adithya Kulkarni, Tyler Cody, Peter A. Beling, Yujun Yan, Dawei Zhou"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.findings-emnlp.1119.pdf"
tags: ["query:luq"]
score: 8.0
evidence: 提出图增强的多级不确定性估计框架GENUINE
tldr: 现有不确定性估计方法多依赖词级概率，忽略生成文本中的语义依赖和结构关系。本文提出GENUINE，一种基于图增强的多级不确定性估计框架，利用依存句法树和分层图池化来捕捉语义与结构信息。通过监督学习训练，GENUINE在多个NLP任务上显著提升了置信度评估的准确性。该工作为结构化不确定性量化提供了新思路。
source: EMNLP-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 809, \"height\": 446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 807, \"height\": 279, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1662, \"height\": 719, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1652, \"height\": 742, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 789, \"height\": 298, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1649, \"height\": 742, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1648, \"height\": 741, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1647, \"height\": 744, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1653, \"height\": 745, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 708, \"height\": 570, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 792, \"height\": 545, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 628, \"height\": 688, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 767, \"height\": 915, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 811, \"height\": 668, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 771, \"height\": 543, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1661, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 616, \"height\": 422, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 791, \"height\": 1001, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1119/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 650, \"height\": 545, \"label\": \"Table\"}]"
motivation: 现有不确定性估计方法忽略生成文本中的语义依赖和结构关系，导致置信度评估不准确。
method: 利用依存句法树和分层图池化构建结构感知的图框架，通过监督学习进行不确定性建模。
result: 在多个NLP任务上，GENUINE显著优于基于词级概率的基线方法。
conclusion: 该工作证明了结构信息对不确定性估计的重要性。
---

## Abstract
Uncertainty estimation is essential for enhancing the reliability of Large Language Models (LLMs), particularly in high-stakes applications. Existing methods often overlook semantic dependencies, relying on token-level probability measures that fail to capture structural relationships within the generated text. We propose GENUINE: Graph ENhanced mUlti-level uncertaINty Estimation for Large Language Models, a structure-aware framework that leverages dependency parse trees and hierarchical graph pooling to refine uncertainty quantification. By incorporating supervised learning, GENUINE effectively models semantic and structural relationships, improving confidence assessments. Extensive experiments across NLP tasks show that GENUINE achieves up to 29% higher AUROC than semantic entropy-based approaches and reduces calibration errors by over 15%, demonstrating the effectiveness of graph-based uncertainty modeling. The code is available at https://github.com/ODYSSEYWT/GUQ.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 核心问题与整体含义
- **研究动机**：大语言模型（LLM）在高风险应用中存在幻觉和事实不准确等问题，可靠的不确定性估计（UQ）至关重要。现有方法多基于词级概率或语义熵，但**忽略了生成文本中的语义依赖和结构关系**，尤其无法识别关键性token对输出正确性的影响。
- **整体含义**：提出一种**结构感知的不确定性估计框架**，利用依存句法树和分层图池化来建模token间依赖，提升置信度评估的准确性与校准性，从而增强LLM的可靠性。

### 2. 方法论
- **核心思想**：将LLM输出句子转化为**依存句法树**（DPT），再连接句子根节点形成段落级图；通过**分层图池化**（仿DiffPool）逐步粗化图，自适应聚合不确定性信息；融合**灰色特征**（概率、熵）和**白色特征**（隐藏层嵌入）的分配矩阵，联合优化。
- **关键步骤**：
  1. **图构建**：为每个输出句子用Stanford NLTK解析器获取依存树，节点为单词，边为依存关系；多句子时连接根节点形成全局图。
  2. **特征定义**：每个节点具有灰色特征（如token概率、熵的多种统计量）和白色特征（仅开放LLM可用的隐藏层嵌入）。
  3. **分层池化**：每层用GNN生成软分配矩阵\(S^l\)，控制节点聚类；同时传播信息得到\(Z^l\)；通过\(X^{l+1}=S^l Z^l\)、\(A^{l+1}=S^l A^l (S^l)^T\)逐步粗化。
  4. **融合机制**：灰色模块和白色模块独立产生分配矩阵，通过可学习函数\(g\)融合得到联合分配矩阵\(S^l_*\)，平衡结构与语义信息。
  5. **联合优化**：端到端训练，最小化分类损失（正确/错误响应判别）。

### 3. 实验设计
- **数据集与场景**：覆盖三类NLP任务：
  - **问答**：CoQA、TriviaQA、Finance QA（基于Rouge-1判定正确性）
  - **机器翻译**：WMT 2014（基于BLEU判定）
  - **摘要**：CNN（基于Rouge-L判定）
- **LLM模型**：Llama2-7B, Llama2-13B, Llama3-8B, Gemma-7B, Gemma2-9B
- **对比方法**：
  - 基线类别：自评估（A4C）、概率/熵（Avg Prob, Avg Ent等）、语义熵（SE）、相关性重加权（SAR）、贝叶斯方法（BayesPE）、监督方法（Sup）
- **评估指标**：AUROC、期望校准误差（ECE）、负对数似然（NLL）、Brier分数

### 4. 资源与算力
- 论文明确说明实验运行在**一台Linux服务器**，配置：
  - CPU: 64核 AMD EPYC 7313
  - GPU: 1块 Nvidia Tesla A100 SXM4 (80 GB显存)
- **未提供具体训练时长**，但提及方法在图规模增大时训练时间近似线性增长（附录B.5.4），表明可接受的计算开销。

### 5. 实验数量与充分性
- **主实验**：在5个数据集、4个LLM上比较7类基线（Fig.4），展示了AUROC、ECE、NLL、Brier分数，结果稳定。
- **消融实验**：检验图结构（去除图/融合）对TriviaQA和WMT的影响（Table 1）；对比依存树与Next-Token图（Table 5）。
- **鲁棒性实验**：噪声标签（Table 2）和训练集大小变化（Table 9）。
- **参数敏感性**：分析池化层数和保留节点比例的影响（Appendix B.4）。
- **模型规模影响**：Llama2-13B与较小模型对比（Appendix B.5）。
- **公平性与客观性**：实验覆盖不同任务、不同规模LLM、多种基线，采用五次重复运行报告均值和方差，方法公开代码可复现。

### 6. 主要结论与发现
- GENUINE在**AUROC上比语义熵基线最高提升29%**，**校准误差（ECE）降低超过15%**，尤其适用于长文本生成（WMT、Finance、CNN）。
- **依存句法树结构**优于简单的Next-Token图，证明语义依赖对不确定性估计至关重要。
- **融合灰色和白色特征**比单独使用任一特征效果更好，但白色特征（隐藏层）在长文本任务上表现最优。
- 在短文本任务（TriviaQA, CoQA）上，GENUINE提升较小，但校准指标仍具竞争力。
- 方法对训练集大小和标签噪声具有一定鲁棒性（20%数据即可保持较高AUROC，0.1%标签噪声影响有限）。

### 7. 优点
- **方法创新性**：首次将依存句法树与分层图池化结合用于LLM不确定性估计，使模型能识别语义关键token并结构化聚合不确定性。
- **自适应融合机制**：在分配矩阵层面融合不同特征，避免高维嵌入主导，提升融合效果。
- **通用性**：支持黑盒（仅灰色特征）和白盒（含白色特征）LLM，扩展性好。
- **实验全面**：覆盖多种任务、模型、基线，并深入分析图结构、参数、鲁棒性等，验证充分。

### 8. 不足与局限
- **依赖内部表示**：灰色特征仍需token概率，白色特征需隐藏层嵌入，对完全黑盒API（仅返回文本）不可用。
- **性能受生成长度影响**：短文本任务提升有限，可能因图结构简单无法充分体现优势。
- **标注数据需求**：监督学习方法需要标注的正确/错误响应，实际应用可能受限；虽展现了低数据量下鲁棒性，但未完全无监督。
- **计算开销略高**：构建依存树和分层池化增加推理时间，但附录显示与节点数近似线性，可接受。
- **领域局限**：仅评估中文未提及，仅覆盖NLP文本任务，未探索多模态或跨领域（如图像、代码）场景。
- **偏差风险**：依赖依存解析质量，解析错误可能引入噪声；训练数据集分布不均可能影响校准（例如TriviaQA的Rouge得分分布不平滑导致ECE异常）。

（完）
