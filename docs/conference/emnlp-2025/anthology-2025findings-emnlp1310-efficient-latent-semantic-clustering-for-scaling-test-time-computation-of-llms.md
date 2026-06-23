---
title: Efficient Latent Semantic Clustering for Scaling Test-Time Computation of LLMs
title_zh: 高效潜在语义聚类：用于扩展LLM测试时计算
authors: "Sungjae Lee, Hoyoung Kim, Jeongyeon Hwang, Eunhyeok Park, Jungseul Ok"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.findings-emnlp.1310.pdf"
tags: ["query:uq-safety"]
score: 7.0
evidence: 潜在语义聚类用于LLM测试时计算中的不确定性量化
tldr: 现有LLM不确定性量化方法依赖外部模型进行语义聚类，计算开销大且无法捕捉语境含义。本文提出高效潜在语义聚类方法，在不使用外部模型的情况下对LLM输出进行上下文感知的语义分组，从而更准确地估计语义分布。实验表明该方法提升了测试时计算的可扩展性和不确定性估计质量，为LLM可靠性提供了有效支撑。
source: EMNLP-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 783, \"height\": 581, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 777, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 806, \"height\": 492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 774, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1635, \"height\": 612, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 616, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 765, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1618, \"height\": 2078, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1659, \"height\": 599, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1659, \"height\": 491, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1653, \"height\": 621, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 578, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 808, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1002, \"height\": 499, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1140, \"height\": 816, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1310/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1687, \"height\": 1087, \"label\": \"Table\"}]"
motivation: 降低外部模型依赖，实现高效上下文感知的语义聚类以改进不确定性量化。
method: 提出潜在语义聚类算法，直接对LLM输出进行语义分组，无需外部模型。
result: 在多个LLM和任务上，聚类效率更高，不确定性估计更准确。
conclusion: 为LLM测试时计算提供了一种高效、无外部模型的语义聚类方案。
---

## Abstract
Scaling test-time computation, generating and analyzing multiple or sequential outputs for a single input, has become a promising strategy for improving the reliability and quality of large language models (LLMs), as evidenced by advances in uncertainty quantification and multi-step reasoning. A key shared component is semantic clustering, which groups outputs that differ in form but convey the same meaning. Semantic clustering enables estimation of the distribution over the semantics of outputs and helps avoid redundant exploration of reasoning paths. However, existing approaches typically rely on external models, which introduce substantial computational overhead and often fail to capture context-aware semantics. We propose Latent Semantic Clustering (LSC), a lightweight and context-sensitive method that leverages the generator LLM’s internal hidden states for clustering, eliminating the need for external models. Our extensive experiment across various LLMs and datasets shows that LSC significantly improves the computational efficiency of test-time scaling while maintaining or exceeding the performance of existing methods.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：在大型语言模型（LLMs）的测试时计算扩展（如不确定性量化、多步推理）中，一个关键组件是**语义聚类**——将形式上不同但含义相同的输出分组。现有方法通常依赖外部模型（如NLI、句子嵌入模型）来进行聚类，但这些方法存在两大缺陷：  
  - 计算开销大：需要运行额外的外部推理，增加延迟和内存。  
  - 上下文感知能力弱：外部模型与生成器分离，无法捕捉生成器内部的上下文相关语义，导致聚类精度不足。  
- **研究目标**：提出一种高效、轻量且上下文感知的语义聚类方法，**避免使用外部模型**，直接利用生成器LLM的内部隐藏状态进行聚类，从而提升测试时计算扩展的效率和性能。

## 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：Latent Semantic Clustering (LSC)  
  在生成多个输出序列时，从生成器LLM的**中间层隐藏状态**中提取每个序列的语义表示，基于这些表示构建相似度矩阵，并通过**谱聚类**进行分组，无需任何外部模型或额外训练。

- **关键技术细节**：
  1. **提取隐藏状态**：  
     - 对每个生成的序列 \( s_n \)，取其在最后一个token处、来自指定中间Transformer层（例如第16层）的隐藏向量 \( h_n \)。  
     - 每个序列仅存储一个向量，与序列长度无关，内存开销极低。
  2. **构建邻接矩阵**：  
     - 计算任意两个隐藏状态的余弦相似度：  
       \[
       a_{m,n} = \frac{h_m \cdot h_n}{\|h_m\|\|h_n\|}
       \]  
     - 得到 \( N \times N \) 的对称矩阵 \( A \)。
  3. **谱聚类与簇数确定**：  
     - 计算对称归一化拉普拉斯矩阵 \( L = I - D^{-1/2}AD^{-1/2} \)。  
     - 计算L的特征值，根据阈值 \( \tau \) 确定簇数 \( k \)（小于 \( \tau \) 的特征值个数）。理论基础：若A是二值图，零特征值的重数等于连通分量数；对连续A，小特征值分布可估计语义不同的含义数。  
     - 用前k个特征向量构建谱嵌入，再执行k-means进行硬聚类。

- **算法流程**：  
  - 输入：上下文 \( x \)，LLM \( M \)，阈值 \( \tau \)。  
  - 输出：簇集合 \( C \)。  
  - 步骤：  
    1. 生成 \( N \) 个序列 \( S \)，同时收集每个序列的隐藏状态 \( h_n \)。  
    2. 根据余弦相似度构造邻接矩阵 \( A \)。  
    3. 对L进行特征分解，用阈值 \( \tau \) 确定簇数 \( k \)。  
    4. 对前k个特征向量进行k-means聚类，得到簇分配。

## 3. 实验设计

- **任务与数据集**：
  - **不确定性量化**（QA任务）：BioASQ（生物医学）、SQuAD（通用）、TriviaQA（开放域）。  
  - **多步推理**（数学推理）：GSM8K、ARC（科学问答）。  
- **对比方法**：
  - 不确定性量化：P(True), PE, KLE, Deg, EigV, ECC, NumSets, SE, DSE（均基于NLI或外部模型），以及提出的 SE-LSC, DSE-LSC。  
  - 多步推理：ToT, RAP, SExp（基于NLI），以及提出的 SExp-LSC。  
- **评估指标**：
  - 不确定性量化：AUROC（区分正确/错误），AUARC（拒绝精度曲线）。  
  - 多步推理：Accuracy、LLM推理次数、NLI推理次数。  
  - 聚类性能：F1分数、Precision、Recall，以及延迟和内存。  
- **使用的LLM**：  
  - 主要：Llama3-8B-Instruct, Mistral-7B-Instruct。  
  - 额外实验：Llama3.2-1B, Llama3-70B（分析规模影响）。  
  - 外部模型：DeBERTa-MNLI-Large, 各种Sentence-BERT（MiniLM, mpnet, T5-XXL）。

## 4. 资源与算力

- **论文未明确说明**使用的GPU型号、数量、训练时长。  
- 所有实验均基于**预训练LLM的推理**（无需训练），外部模型比对也仅涉及推理。  
- LSC本身几乎不增加计算：仅需存储隐藏向量（每个序列一个向量），与LLM生成过程并行，额外延迟约0.0069秒，内存约0.000061 GB（见Table 3）。  
- 对比外部模型（如DeBERTa-MNLI-Large约1.52 GB内存、0.13秒延迟），LSC具有极低资源开销。

## 5. 实验数量与充分性

- **实验数量**：  
  - 不确定性量化：3个数据集 × 2个LLM × 10+方法（含消融）→ 约60组结果（见Table 1, Table A3）。  
  - 多步推理：2个数据集 × 2个LLM × 4种方法 → 16组结果（Table 2）。  
  - 聚类性能对比：6种外部/内部模型（含有无上下文）→ 12种配置（Table 3）。  
  - 消融与扩展：  
    - 层选择实验（Fig.4, Table 4）。  
    - 软聚类替代（Fig.6）。  
    - 不同LLM大小（Fig.7）。  
    - 不同聚类算法对比（Table 5）。  
- **充分性与公平性**：  
  - 对比基线覆盖了现有最主流方法（NLI、BERT、句子嵌入、谱聚类等）。  
  - 在不确定性量化任务中使用相同的生成设置（温度、top-k等）和评估流程。  
  - 多步推理中保持了与SExp一致的prompt和搜索参数。  
  - 聚类性能实验中，使用Llama3-70B生成标签，保证标签可靠性。  
  - 消融实验探讨了不同层、不同聚类算法、不同LLM规模，验证了方法的鲁棒性。  
- **结论**：实验设计较为全面，客观公平，能够支撑核心结论。

## 6. 主要结论与发现

1. **LSC显著提升效率**：在不确定性量化任务中，SE-LSC和DSE-LSC在AUROC上超越所有NLI-based方法（如BioASQ上AUROC从0.83提升至0.86），同时零外部模型开销。
2. **上下文感知能力更强**：在聚类质量上，LSC的F1分数达到0.8789，优于外部NLI模型（0.6904）和句子嵌入模型（≤0.7333），且内存/延迟极低（~0.007秒 vs 外部模型0.02-4.9秒）。
3. **多步推理更高效**：在GSM8K和ARC上，SExp-LSC相比SExp减少了22.58%的LLM推理次数，并保持或提升准确率。
4. **中间层表示最优**：图4显示，中间层和第16层的隐藏状态聚类效果最好，结合早期层可进一步提升（Table 4）。
5. **可替换软聚类方法**：将LSC的余弦相似度矩阵替换NLI构造的邻接矩阵后（如KLE, ECC等），AUROC进一步改善（Fig.6）。
6. **随LLM规模增大效果更好**：在70B模型上，LSC相对于NLI基线的优势比1B模型更明显（Fig.7）。

## 7. 优点

- **极低计算开销**：无需外部模型，仅利用生成过程中已计算的隐藏状态，额外延迟和内存几乎可忽略。  
- **上下文感知**：隐藏状态天然包含输入上下文，能区分“语境相同但表面不同”的语义，外部NLI无法做到。  
- **通用性强**：适用于任何白盒LLM，可直接嵌入不确定性量化、推理搜索等测试时计算扩展框架。  
- **理论支撑**：基于谱聚类数学性质确定簇数，无需预设。  
- **实验全面**：覆盖多个任务、多个LLM尺寸、多种基线，并深入分析了层选择、聚类算法、软/硬聚类等影响因素。

## 8. 不足与局限

- **仅适用于白盒模型**：需要访问LLM的内部隐藏状态，无法用于黑盒API模型。  
- **单层单token表示的限制**：仅使用一个中间层的最后一个token的隐藏状态，可能丢失细粒度语义信息。论文提及融合多层或token级表示可能进一步提升性能，但未深入探索。  
- **未探索训练视角**：LSC是推理时方法，没有利用外部数据训练聚类适配层或表示。  
- **实验规模限制**：多步推理仅使用400个样本的子集，且在设定参数下运行，更大规模测试或全数据集结果未提供。  
- **未与最新黑盒不确定性方法（如信息论方法）对比**：仅比较了使用外部模型或概率的基线。

（完）
