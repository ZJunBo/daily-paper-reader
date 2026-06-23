---
title: "Fine-grained Uncertainty Decomposition in Large Language Models: A Spectral Approach"
title_zh: 大语言模型中细粒度不确定性分解：一种谱方法
authors: "Nassim Walha, Sebastian G. Gruber, Thomas Decker, Yinchong Yang, Alireza Javanmardi, Eyke Hüllermeier, Florian Buettner"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39811/43772"
tags: ["query:luq"]
score: 9.0
evidence: 通过谱方法将LLM不确定性分解为偶然和认知不确定性
tldr: 大型语言模型的不确定性来源多样，现有方法难以区分偶然不确定性（数据歧义）和认知不确定性（模型知识不足）。本文提出谱不确定性（Spectral Uncertainty），基于量子信息论中的冯·诺依曼熵，严格地将总不确定性分解为两类。实验表明该分解有助于针对性缓解不确定性来源，提升LLM在关键任务中的可信度。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有LLM不确定性量化方法无法细粒度地区分偶然和认知不确定性。
method: 利用冯·诺依曼熵从量子信息论出发，通过谱分解分离不确定性成分。
result: 在多个LLM任务上实现了有效的不确定性分解，并验证了其有助于改进模型校准。
conclusion: 谱不确定性为理解和管理LLM不确定性提供了理论基础和实用方法。
---

## Abstract
As Large Language Models (LLMs) are increasingly integrated in diverse applications, obtaining reliable measures of their predictive uncertainty has become critically important. A precise distinction between aleatoric uncertainty, arising from inherent ambiguities within input data, and epistemic uncertainty, originating exclusively from model limitations, is essential to effectively address each uncertainty source.
In this paper, we introduce Spectral Uncertainty, a novel approach to quantifying and decomposing uncertainties in LLMs. Leveraging the Von Neumann entropy from quantum information theory, Spectral Uncertainty provides a rigorous theoretical foundation for separating total uncertainty into distinct aleatoric and epistemic components. Unlike existing baseline methods, our approach incorporates a fine-grained representation of semantic similarity, enabling nuanced differentiation among various semantic interpretations in model responses. Empirical evaluations demonstrate that Spectral Uncertainty outperforms state-of-the-art methods in estimating both aleatoric and total uncertainty across diverse models and benchmark datasets.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：大语言模型（LLM）在关键领域广泛应用，但其预测不确定性缺乏细粒度的来源区分。现有方法要么依赖词元级概率而忽略语义，要么将语义相似度视为二元关系（如语义熵），难以区分由输入歧义引起的**偶然不确定性**（aleatoric）和由模型知识不足引起的**认知不确定性**（epistemic）。这种区分对于提升模型可靠性、指导数据收集或模型改进至关重要。
- **整体含义**：论文提出一种基于谱分解的不确定性量化框架——**Spectral Uncertainty**，利用量子信息论中的冯·诺依曼熵（Von Neumann entropy）在连续语义空间中分解总不确定性，为理解LLM预测的置信度来源提供了理论工具和实用估计方法。

#### 2. 论文提出的方法论
- **核心思想**：基于函数Bregman信息（Functional Bregman Information）的一般性不确定性分解定理（Theorem 3.2），将任意凹函数作为不确定性度量。特别地，选择冯·诺依曼熵（定义在再生核希尔伯特空间RKHS的协方差算子上的凹函数）来实例化分解，从而得到**谱不确定性分解**（Corollary 3.6）：
  - 总不确定性 = 认知不确定性（期望条件冯·诺依曼熵） + 偶然不确定性（Holevo信息，即Bregman负熵）。
- **关键技术细节**：
  - **两步采样**：首先用一个 **澄清LLM**（claration LLM）对用户输入生成 \(n\) 个不同的澄清（interpretations），代表不同可能的输入理解；然后对每个澄清，由**目标LLM**通过多项式采样生成 \(m\) 个回答。
  - **嵌入与核函数**：使用预训练句子嵌入模型将回答映射到连续语义空间，再通过RBF核函数计算核矩阵。
  - **谱估计**：利用内层（每个澄清内的回答）和外层（所有回答）核矩阵的特征值，通过公式 (13) 和 (14) 分别估计偶然不确定性和认知不确定性。总不确定性为两者之和。
- **算法流程**（Algorithm 1）：
  1. 用澄清LLM生成 \(n\) 个澄清 \(W_1,\dots,W_n\)。
  2. 对每个澄清 \(W_i\)，从目标LLM采样 \(m\) 个回答 \(X_{i1},\dots,X_{im}\)。
  3. 将每个回答通过嵌入模型得到特征向量 \(Y_{ij}\)。
  4. 计算内层核矩阵 \(K_i\) 及特征值 \(\hat{\lambda}_{i1},\dots,\hat{\lambda}_{im}\)。
  5. 计算外层核矩阵 \(K_{out}\) 及特征值 \(\hat{\lambda}^{out}_1,\dots,\hat{\lambda}^{out}_{nm}\)。
  6. 代入公式 (13) 和 (14) 得到偶然与认知不确定性。

#### 3. 实验设计
- **数据集与场景**：
  - **歧义检测任务**（评估偶然不确定性）：使用 **AmbigQA**（真实歧义问题）和 **AmbigInst**（合成指令型歧义任务）。每个问题标注了是否歧义，衡量方法区分歧义/非歧义输入的能力。
  - **正确性预测任务**（评估总不确定性）：使用 **TriviaQA** 和 **Natural Questions**（问答基准）。判断模型输出是否正确，衡量方法预测模型回答是否正确的性能。
- **基准方法**：包括 **Semantic Entropy**, **Kernel Language Entropy**, **Predictive Kernel Entropy**，以及唯一的分解基线 **Input Clarification Ensembling**（Hou et al., 2024）。
- **评估指标**：AUROC 和 AUPR。
- **模型**：目标LLM为 **Phi-4 14B** 和 **LLaMA 4 Maverick（109B）**；澄清LLM使用 **GPT-4o**；嵌入模型为 **all-mpnet-base-v2**。

#### 4. 资源与算力
- 论文提到使用 **NVIDIA Quadro RTX 5000 GPU** 计算句子嵌入和执行Phi-4实验。GPT模型和LLaMA 4模型通过API调用（OpenAI和Groq）。**未明确说明GPU数量、训练时长或总计算时间**。实验属于推理阶段，不涉及训练。

#### 5. 实验数量与充分性
- **实验数量**：在2个歧义检测数据集、2个正确性预测数据集上，使用2个不同规模的目标模型，对比4种以上基线，每个实验报告AUROC和AUPR。此外，附录中还包括对 **Qwen-3** 家族的额外验证和核密度图的可视化分析。
- **充分性与公平性**：数据集均为公开标准基准，基线的超参数（采样数等）遵循原论文推荐设置（如 \(m=10\)，温度 \(t=0.5\)）。实验中澄清数量动态生成但上限为10。论文未报告统计显著性检验（如置信区间），但通过多次独立采样（多组实验）展示了稳定性。总体而言，实验设计较为全面，但**缺乏对澄清生成质量、不同核函数或嵌入模型的消融**，也仅覆盖英文问答任务。

#### 6. 论文的主要结论与发现
- **谱不确定性方法在所有任务上优于所有基线**，尤其在**偶然不确定性估计**上提升显著。在 **AmbigInst** 数据集上，AUROC 比最佳基线高 13%（Phi-4）和 23%（LLaMA 4）。
- 在**总不确定性估计**（正确性预测）中，多数场景下也取得最佳结果（如TriviaQA上AUROC达91.92%）。
- 谱方法有效分离了歧义/非歧义样本以及正确/错误预测的核密度分布，说明其细粒度语义表示的优势。

#### 7. 优点
- **理论严谨**：从一般性函数Bregman信息出发，统一了多种不确定性分解框架，并基于冯·诺依曼熵给出可计算的谱估计。
- **细粒度语义相似性**：使用连续核函数替代二进制聚类，能够捕捉语义梯度，优于语义熵等方法。
- **分解可解释**：明确将总不确定性分解为偶然和认知成分，且分别对应不同的外部行为（输入歧义 vs. 模型知识不足）。
- **实证表现SOTA**：在多个模型和数据集上系统性地超越现有方法，泛化性较好。

#### 8. 不足与局限
- **计算成本高**：需要 \(n \times m\) 个生成回答（实验中 \(n\) 最多10, \(m=10\)），且需计算两次核矩阵特征值。论文未详细分析计算时间，仅提及其在附录中讨论了计算开销。
- **经验性评估**：与领域内多数工作一致，评价依赖经验指标，缺乏对分解正确性的理论验证（例如证明估计量一致性公理的满足性）。
- **澄清生成依赖**：分解质量可能受澄清LLM的能力影响（论文指出使用更强模型如GPT-4o可提升效果），存在系统性偏差风险。
- **参数和模型选择敏感**：未进行核函数、嵌入模型、采样温度等的消融实验，最佳配置的鲁棒性有待验证。
- **任务范围有限**：仅测试了英文问答和指令歧义任务，未涵盖多语言、长文本生成或对话系统等场景。

（完）
