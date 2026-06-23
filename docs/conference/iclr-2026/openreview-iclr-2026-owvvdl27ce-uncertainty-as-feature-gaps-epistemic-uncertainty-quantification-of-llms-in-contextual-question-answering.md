---
title: "Uncertainty as Feature Gaps: Epistemic Uncertainty Quantification of LLMs in Contextual Question-Answering"
title_zh: 不确定性作为特征间隙：上下文问答中大语言模型的认知不确定性量化
authors: "Yavuz Faruk Bakman, Sungmin Kang, Zhiqi Huang, Duygu Nur Yaldiz, Catarina G Belém, Chenyang Zhu, Anoop Kumar, Alfy Samuel, Daben Liu, Salman Avestimehr, Sai Praneeth Karimireddy"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=OWvvdl27CE"
tags: ["query:luq"]
score: 9.0
evidence: 面向上下文问答的认知不确定性量化
tldr: 本文聚焦上下文问答中的不确定性量化，提出理论上严谨的认知不确定性度量。通过分解词元级交叉熵，分离认知成分，并用理想化模型近似真实分布，推导出认知不确定性上界。该方法填补了上下文QA中UQ研究的空白。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-owvvdl27ce/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1408, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-owvvdl27ce/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1391, \"height\": 436, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-owvvdl27ce/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 447, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-owvvdl27ce/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 1490, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-owvvdl27ce/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 770, \"height\": 619, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-owvvdl27ce/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 812, \"height\": 456, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-owvvdl27ce/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 776, \"height\": 684, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-owvvdl27ce/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1040, \"height\": 805, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-owvvdl27ce/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1016, \"height\": 586, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-owvvdl27ce/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 738, \"height\": 861, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-owvvdl27ce/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1258, \"height\": 1184, \"label\": \"Table\"}]"
motivation: 现有UQ研究多集中于闭卷事实问答，忽视了上下文问答场景。
method: 定义词元级交叉熵，分解得到认知成分，用理想化模型估计真实分布。
result: 推导了认知不确定性的理论上界，并在上下文QA任务中验证。
conclusion: 为上下文问答中的认知不确定性提供了理论基础与可行方法。
---

## Abstract
Uncertainty Quantification (UQ) research has primarily focused on closed-book factual question answering (QA), while contextual QA remains unexplored, despite its importance in real-world applications. In this work, we focus on UQ for the contextual QA task and propose a theoretically grounded approach to quantify \emph{epistemic uncertainty}. We begin by introducing a task-agnostic, token-level uncertainty measure defined as the cross-entropy between the predictive distribution of the given model and the unknown true distribution. By decomposing this measure, we isolate the epistemic component and approximate the true distribution by a perfectly prompted, idealized model. We then derive an upper bound for epistemic uncertainty and show that it can be interpreted as semantic feature gaps in the given model’s hidden representations relative to the ideal model. We further apply this generic framework to the contextual QA task and hypothesize that three features approximate this gap: \emph{context-reliance} (using the provided context rather than parametric knowledge), \emph{context comprehension} (extracting relevant information from context), and \emph{honesty} (avoiding intentional lies). Using a top-down interpretability approach, we extract these features by using only a small number of labeled samples and ensemble them to form a robust uncertainty score. Experiments on multiple QA benchmarks in both in-distribution and out-of-distribution settings show that our method substantially outperforms state-of-the-art unsupervised (sampling-free and sampling-based) and supervised UQ methods, achieving up to a 13-point PRR improvement while incurring a negligible inference overhead. The code is available at https://github.com/Ybakman/Feature-Gaps.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）在上下文问答（contextual QA）场景中的不确定性量化（UQ）问题。现有的UQ研究主要集中于闭卷事实问答，忽略了实际应用中更常见的上下文问答（如检索增强生成RAG场景）。
- **研究动机**：上下文问答中，模型需要基于提供的上下文回答问题，但模型可能因依赖自身参数知识、未能理解上下文或故意撒谎而产生错误。需要一个理论上严谨的方法来量化模型在这一任务中的认知不确定性（epistemic uncertainty）。
- **整体含义**：提出一种基于特征间隙（feature gaps）的认知不确定性量化框架，将不确定性分解为认知成分并通过理想模型近似，最终在多个基准上超越现有方法。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：
  - 定义总不确定性（total uncertainty）为**真实分布**与**给定模型预测分布**之间的交叉熵（注意与Schweighofer等人的公式相反，作者认为这样分解更合理）。
  - 总不确定性可分解为：**Aleatoric（数据）不确定性**（真实分布的熵） + **Epistemic（认知）不确定性**（真实分布与模型分布之间的KL散度）。
  - 用**完美提示的理想模型**（通过最优提示序列获得）近似真实分布，从而将认知不确定性上界为两个模型最后一层隐藏状态差的范数。

- **关键技术细节**：
  - **引理1**：认知不确定性 ≤ 2||W||·||h*_t - h_t||，其中h*和h分别为理想模型和实际模型的最后一层隐藏状态，W为词汇投影矩阵。
  - **线性表示假设**：高级语义特征在激活空间中以线性方向编码，因此隐藏状态差可分解为特征方向上的系数差（特征间隙）。
  - **特征选择**：在上下文QA任务中，假设三个关键特征近似该间隙：**上下文依赖**（基于上下文而非参数知识）、**上下文理解**（正确提取相关信息）、**诚实**（避免故意错误）。
  - **特征提取**：通过对比提示（如“使用上下文”vs“使用自己的知识”）获取隐藏状态差，再对多个样本做PCA得到特征方向。每个特征仅需少量标注样本。
  - **层选择与集成**：基于PRR指标选择最优层，用三个标量权重（wi）学习组合特征，最终不确定性为加权组合的范数。

- **算法流程**（文字说明）：
  1. 对每个特征，用少量标注样本构建对比提示对，计算每层隐藏状态差，PCA提取单个方向v。
  2. 用验证集选择每特征的最佳层（PRR最大）。
  3. 学习三个权重wi（最小化交叉熵损失），使得集成分数(wi-1)αi与正确性负相关。
  4. 测试时，对输入计算三个特征方向的激活量，加权求和得到不确定性分数。

### 3. 实验设计：数据集、场景、基准方法与对比对象

- **数据集**：三个上下文问答数据集：
  - **Qasper**（科学论文QA）
  - **HotpotQA**（多跳Wikipedia QA）
  - **NarrativeQA**（故事阅读理解）  
  每个数据集使用1000个样本。
- **模型**：LLaMA-3.1-8B、Mistral-v0.3-7B、Qwen2.5-7b。
- **评估指标**：AUROC（区分能力）和PRR（预测-拒绝比，衡量拒绝低置信样本后的精度提升）。正确性通过LLM-as-a-judge（Gemini-2.5-flash）判定。
- **对比方法**：
  - 无监督无采样：Perplexity, MARS, MiniCheck, LLM-Judge, PTrue。
  - 无监督多采样（5个样本）：Entropy, Semantic Entropy, KLE, Eccentricity, SAR。
  - 有监督（256个标注样本）：SAPLMA, LookBackLens, ATMD。

### 4. 资源与算力

- 论文中提到：在8块40GB NVIDIA A100 GPU上运行实验。LookBackLens方法因显存不足而无法在Qasper和NarrativeQA上运行（仅HotpotQA可行）。**未明确说明训练/推理的具体时长或总计算量**。

### 5. 实验数量与充分性

- **实验数量**：大量：
  - 主实验：3个数据集 × 3个模型 × 多种方法，共数十个结果（表1）。
  - 分布外（OOD）评估：3×3交叉训练测试（图3），比较SAPLMA。
  - 消融实验：单个特征性能（表2）、低数据量64/128样本（表3）、基线方向对比（表4）、多层扩展（附录A.5.1）、更大模型Qwen2.5-32B（附录A.5.2）。
  - 统计显著性检验（附录A.5.3）。
- **充分性与客观性**：
  - 实验设计全面，覆盖多种模型、数据集、基线（无监督/有监督），并包含OOD、低数据、消融等，比较公平。
  - 使用标准指标AUROC和PRR，正确性采用LLM评判（减少人工偏差）。
  - 但未包含真实RAG场景（检索噪声），也未与所有近期UQ方法（如贝叶斯方法）对比。

### 6. 论文的主要结论与发现

- 提出的**Feature-Gaps**方法在多数场景下显著优于所有基线，最高提升13个PRR点（如LLaMA-3.1-8B在HotpotQA上PRR 66.6 vs 第二53.5）。
- 该方法是**无采样**的，推理极快；使用少量标注样本（256）即可达到强性能。
- **OOD泛化能力**优于SAPLMA（监督方法），说明特征间隙具有跨域稳健性。
- 单个特征已能有效度量不确定性，集成主要提供稳定性。
- 方法在大模型（Qwen2.5-32B）上也有效，但此时概率类方法（Perplexity, PTrue）表现更强。

### 7. 优点

- **理论严谨**：从信息论出发推导了认知不确定性的上界，并关联到线性表示假设。
- **高效实用**：无需多次采样，仅需三个点积计算，适用于实际部署。
- **强泛化**：OOD实验表明比直接训练分类器更鲁棒。
- **数据效率**：仅需64-256个标注样本即可达到或超越强基线。
- **可解释性**：特征（上下文依赖、理解、诚实）有明确语义。

### 8. 不足与局限

- **依赖监督样本**：需要标注的正确性数据，无法完全无监督。
- **特征选择启发式**：针对上下文QA手工设计了三个特征，可能不适用于其他任务（如推理、长文本生成）。论文承认需要自动特征发现。
- **未考虑检索噪声**：实验假设上下文已提供且相关，未建模RAG中检索错误带来的不确定性。
- **长上下文限制**：Mistral-7B在NarrativeQA上因上下文超长（>32k）导致性能下降，表明方法对超出模型训练长度的上下文敏感。
- **计算资源**：虽然推理快，但特征提取阶段仍需多次前向传播（每个特征需2次前向），且PCA计算可能随样本增大而变复杂（论文未分析）。
- **未与所有近期方法对比**：如未包括输入澄清贝叶斯方法（Hou et al.）等。

（完）
