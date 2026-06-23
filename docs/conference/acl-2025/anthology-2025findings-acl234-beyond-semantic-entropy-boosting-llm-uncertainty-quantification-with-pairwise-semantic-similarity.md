---
title: "Beyond Semantic Entropy: Boosting LLM Uncertainty Quantification with Pairwise Semantic Similarity"
title_zh: 超越语义熵：利用成对语义相似度提升大语言模型不确定性量化
authors: "Dang Nguyen, Ali Payani, Baharan Mirzasoleiman"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.findings-acl.234.pdf"
tags: ["query:luq"]
score: 8.0
evidence: 基于成对语义相似度的LLM不确定性量化
tldr: 语义熵（SE）在长句响应中忽略簇内相似性和簇间距离。本文提出一种简单的黑盒不确定性量化方法，基于最近邻熵估计，同时考虑这两种相似度，可扩展至白盒。实验表明该方法在幻觉检测上优于语义熵。
source: ACL-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.234/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1465, \"height\": 457, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.234/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 533, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.234/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1402, \"height\": 407, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.234/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 722, \"height\": 616, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.234/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 863, \"height\": 402, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.234/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1643, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.234/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1642, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.234/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1404, \"height\": 191, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.234/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1594, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.234/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1598, \"height\": 315, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.234/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1236, \"height\": 978, \"label\": \"Table\"}]"
motivation: 语义熵在长句响应中忽略了簇内和簇间相似度。
method: 提出基于最近邻熵估计的黑盒不确定性量化方法。
result: 提出的方法在多个基准上优于语义熵及其变体。
conclusion: 考虑簇结构能更准确估计LLM输出的不确定性。
---

## Abstract
Hallucination in large language models (LLMs) can be detected by assessing the uncertainty of model outputs, typically measured using entropy. Semantic entropy (SE) enhances traditional entropy estimation by quantifying uncertainty at the semantic cluster level. However, as modern LLMs generate longer one-sentence responses, SE becomes less effective because it overlooks two crucial factors: intra-cluster similarity (the spread within a cluster) and inter-cluster similarity (the distance between clusters). To address this limitation, we propose a simple black-box uncertainty quantification method inspired by nearest neighbor estimates of entropy. Our approach can also be easily extended to white-box settings by incorporating token probabilities. Additionally, we provide theoretical results showing that our method generalizes semantic entropy. Extensive empirical results demonstrate its effectiveness compared to semantic entropy across two recent LLMs (Phi3 and Llama3) and three common text generation tasks: question answering, text summarization, and machine translation. Our code is available at [https://github.com/BigML-CS-UCLA/SNNE](https://github.com/BigML-CS-UCLA/SNNE).

---

## 论文详细总结（自动生成）

### 论文中文总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）
- **背景**：大型语言模型（LLM）存在“幻觉”问题，可通过不确定性量化（UQ）检测。语义熵（Semantic Entropy, SE）通过聚类语义等价输出改进传统熵，但现代LLM倾向于生成更长的单句响应（如 Llama-3.1-8B 平均长度 4.1 词，Phi-3-mini 4.9 词，而 Llama2-7B 仅 2.3 词）。长句导致语义聚类数量增多，SE 忽略了两个关键因素：**簇内相似性**（同一聚类内部输出的分散程度）和 **簇间相似性**（不同聚类之间的距离），使得熵估计退化为朴素方法或产生恒定值。
- **核心问题**：如何在长句生成场景下更准确地量化LLM输出的不确定性，从而提升幻觉检测能力。

#### 2. 论文提出的方法论
- **核心思想**：受最近邻熵估计启发，利用**成对语义相似度**同时捕获簇内和簇间相似性，而无需显式聚类。通过 LogSumExp 平滑聚合相似度，降低异常值影响。
- **黑盒方法：语义最近邻熵 (SNNE)**  
  \[
  \text{SNNE}(q) = -\frac{1}{n} \sum_{i=1}^n \log \left( \sum_{j=1}^n \exp\left(\frac{f(a_i, a_j \mid q)}{\tau}\right) \right)
  \]
  其中 \( f \) 为相似度函数（可选 ROUGE-L、NLI 预测分数或余弦相似度），\( \tau \) 为尺度因子（默认 1）。
- **白盒扩展 (WSNNE)**：在求和项中加入长度归一化的序列概率权重：
  \[
  \text{WSNNE}(q) = - \sum_{i=1}^n \bar{P}(a_i|q) \log \left( \sum_{j=1}^n \exp\left(\frac{f(a_i, a_j|q)}{\tau}\right) \right)
  \]
- **理论结果**：定理 4.1 和 4.2 证明，在特定相似度函数定义下，SNNE 可退化为离散语义熵 (DSE)，WSNNE 可退化为语义熵 (SE)，表明 (W)SNNE 是 (D)SE 的推广形式。

#### 3. 实验设计
- **数据集**：
  - **问答 (QA)**：SQuAD、TriviaQA、NaturalQuestions、SVAMP、BioASQ（共5个）。
  - **文本摘要 (TS)**：XSUM、AESLC（共2个）。
  - **机器翻译 (MT)**：WMT-14 de-en、WMT-14 fr-en（共2个）。
- **基准模型**：Llama-3.1-8B、Phi-3-mini、Llama2-7B/13B、Gemma-2-2B、Mistral-Nemo。
- **对比方法**：
  - **白盒**：KLE full、SE、NE、EigenScore、SAR、WSNNE。
  - **黑盒**：KLE heat、DSE、pTrue、LexSim、NumSet、SumEigv、Deg、Eccen、LUQ-Pair、SNNE。
- **评估指标**：QA 使用 AUROC 和 AUARC；TS/MT 使用 PRR（基于 ROUGE-L 和 BERTScore）。

#### 4. 资源与算力
- 文中明确说明：使用 **NVIDIA RTX A6000 GPU** 进行实验，每个实验重复三次。**未披露具体 GPU 数量、训练时长或总计算量**。

#### 5. 实验数量与充分性
- **实验数量**：覆盖6种模型、9个数据集、多种任务（QA/TS/MT）；包含消融实验（相似度函数选择、尺度因子 \(\tau\) 的影响）、超参分析（生成样本数、温度）、对比16种以上基线方法。
- **充分性与公平性**：实验较为充分，采用多次重复运行减少随机性；超参统一从 SE 论文沿用（温度1.0、10个生成样本）；公平性体现在与多种 SOTA 方法在相同设置下对比。但未涉及多句/段落生成场景，也未在更大模型（如 70B 级）上验证。

#### 6. 论文的主要结论与发现
- SNNE 和 WSNNE 在 **所有任务和模型** 上显著优于 SE 及其他基线，尤其当生成结果中语义聚类数量多时优势更明显（AUROC 提升可达 0.07）。
- 黑盒 SNNE 与白盒 WSNNE 均表现优秀，且对尺度因子 \(\tau\) 不敏感（默认 \(\tau=1\) 即可）。
- 相似度函数中，ROUGE-L 在摘要和翻译任务上效果最好，而嵌入相似度在翻译任务中也具有竞争力。
- 理论分析表明 (W)SNNE 推广了 (D)SE，提供了更丰富的熵估计。

#### 7. 优点
- **方法简洁**：无需显式聚类，直接利用成对相似度，计算复杂度 O(n²)（低于 KLE 的 O(n³)）。
- **通用性强**：同时支持黑盒和白盒场景，可集成不同相似度函数（词重叠、NLI、嵌入）。
- **鲁棒性**：LogSumExp 操作降低异常值影响，优于基于求和/平均的图方法。
- **理论支撑**：证明与 SE/DSE 的统一关系，提供理论基础。

#### 8. 不足与局限
- **覆盖不足**：未探讨多句或段落生成场景（仅单句 LLM 输出），作者称留作未来工作。
- **适用性限制**：对数学表达式、代码等非自然语言数据需要设计专门的相似度函数。
- **推理成本**：需要多次采样（通常10个以上输出）来估计熵，增加了推理开销。
- **可扩展性**：尽管 O(n²) 优于 O(n³)，但在 n 很大时仍可能成为瓶颈。

（完）
