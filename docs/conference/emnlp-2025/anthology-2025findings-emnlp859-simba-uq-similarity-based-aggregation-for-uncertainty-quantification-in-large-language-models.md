---
title: "SIMBA UQ: Similarity-Based Aggregation for Uncertainty Quantification in Large Language Models"
title_zh: SIMBA UQ：用于大语言模型的不确定性量化的基于相似性的聚合方法
authors: "Debarun Bhattacharjya, Balaji Ganesan, Junkyu Lee, Radu Marinescu, Katya Mirylenka, Michael Glass, Xiao Shou"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.findings-emnlp.859.pdf"
tags: ["query:uq-safety"]
score: 9.0
evidence: 基于相似性聚合的黑盒不确定性量化
tldr: 黑盒不确定性量化方法无需访问模型内部信息，具有实际优势。本文系统研究了基于生成输出与其他样本一致性进行不确定性估计的黑盒UQ技术。通过相似性聚合，SIMBA UQ在多个LLM上实现了稳健的置信度估计，且计算高效。该工作为黑盒场景下的LLM可靠性评估提供了实用方案。
source: EMNLP-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.859/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1290, \"height\": 329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.859/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1589, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.859/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1568, \"height\": 377, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.859/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1485, \"height\": 1582, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.859/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1645, \"height\": 388, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.859/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1654, \"height\": 559, \"label\": \"Table\"}]"
motivation: 探索不依赖模型内部信息的黑盒不确定性量化方法。
method: 利用生成的多个输出之间的相似性进行聚合，估计不确定性。
result: 在多个LLM上表现出稳健的不确定性估计能力。
conclusion: 黑盒UQ方法兼具实用性和有效性。
---

## Abstract
When does a large language model (LLM) know what it does not know? Uncertainty quantification (UQ) provides measures of uncertainty, such as an estimate of the confidence in an LLM’s generated output, and is therefore increasingly recognized as a crucial component of trusted AI systems. Black-box UQ methods do not require access to internal model information from the generating LLM and therefore have numerous real-world advantages, such as robustness to system changes, adaptability to choice of LLM, reduced costs, and computational tractability. In this paper, we investigate the effectiveness of UQ techniques that are primarily but not necessarily entirely black- box, where the consistency between a generated output and other sampled generations is used as a proxy for confidence in its correctness. We propose a high-level non-verbalized similarity-based aggregation framework that subsumes a broad swath of UQ approaches suitable for complex generative tasks, as well as introduce specific novel techniques from the framework that train confidence estimation models using small training sets. Through an empirical study with datasets spanning the diverse tasks of question answering, summarization, and text-to-SQL, we demonstrate that our proposed similarity-based methods can yield better calibrated confidences than baselines.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

大型语言模型（LLM）在复杂生成任务中的不确定性量化（UQ）对于构建可信AI系统至关重要。黑盒UQ方法因不依赖模型内部信息（如参数、logits），具有鲁棒性强、计算高效、易于部署等实际优势，但现有黑盒方法效果参差不齐。核心问题是：**如何在不访问模型内部信息的前提下，有效评估LLM生成结果的置信度？** 本文基于“一致性假设”（正确生成通常与其他采样输出更相似），提出一种非言语化的相似性聚合框架（SIMBA UQ），旨在统一和扩展现有基于一致性的UQ方法，并在问答、摘要、文本-to-SQL等多个任务上验证其有效性。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用同一输入下多个采样输出之间的**成对相似性**作为置信度代理。假设：正确的生成结果与其他样本更一致，错误的则更分散。
- **总体流程**（图1）：
  1. **采样**：在多个温度下（0.25~1.5，步长0.25）对LLM进行多次生成，得到多个输出（如5个温度×5个样本=30个样本，但评估仅用低温度样本）。
  2. **计算成对相似性**：使用任意文本相似度指标（如Jaccard系数、ROUGE-L等）计算所有样本对之间的相似度。
  3. **相似性聚合**：将每个生成样本与其他样本的相似度向量作为输入，通过不同函数输出置信度。
- **提出三种聚合方法**：
  - **简单聚合（Simple Aggregation）**：直接取与其他样本的算术平均相似度作为置信度（等价于基于度数的谱聚类）。
  - **贝叶斯聚合（Bayesian Aggregation）**：假设相似性在给定正确/错误标签下服从Beta分布，利用贝叶斯公式更新后验概率，需小训练集学习5个参数（先验p0，两个Beta分布各两个参数）。
  - **分类聚合（Aggregation by Classification）**：将置信度估计视为二分类任务（正确/错误），使用随机森林（或逻辑回归）以相似性特征（如全部成对相似度、均值相似度、是否加入生成概率）预测正确概率。这是本文重点推荐的方法。
- **公式**（贝叶斯）：P(yi∈Y*|si) = p0∏αi / [p0∏αi + (1-p0)∏βi]，其中αi、βi为条件相似性概率密度。

### 3. 实验设计：数据集、基准、对比方法

- **数据集（9个）**：分为三类任务：
  - 问答（QA）：CoQA（开放书）、TriviaQA（闭书）、Natural Questions（闭书）。
  - 摘要（Summarization）：XSum、SamSum、CNN Dailymail。
  - 文本-to-SQL：Spider、Spider-Realistic、BIRD。
- **LLM模型**：QA和摘要使用LLaMA 3.3 70B instruct 和 Granite 3.1 8B instruct；Text-to-SQL使用CodeLlama 34B instruct 和 Granite 34B Code instruct。
- **基线方法**：
  - 白盒：avg. log prob（平均对数概率）
  - 黑盒：p(true)（LLM自评正确性）、spec-ecc（谱聚类离心率）、arith-agg（等价于度数聚合）、clf-gen（仅用生成概率作为特征的分类器）
- **提议方法**：bayes-beta（贝叶斯）、clf-pairs（全部成对相似度为特征）、clf-mean+gen（均值相似度+生成概率）、clf-pairs+gen（全部成对+生成概率）
- **评估指标**：
  - ATS（Accuracy from Top Selection）：基于置信度从多个生成中选一个的准确率
  - ACE（Adaptive Calibration Error）：自适应分箱校准误差（越低越好）
  - AUROC（Area Under ROC）：置信度判别正确/错误的能力
- **正确性判定**：QA和摘要使用ROUGE-L阈值（0.5或0.3）；SQL通过执行结果匹配。

### 4. 资源与算力

论文中提到使用GPU（如NVIDIA A100，>40GB显存）进行LLM生成，但**未明确给出训练时长、GPU数量等具体算力信息**。所有UQ实验可在CPU上运行，但生成样本依赖GPU。训练分类器（随机森林）使用小训练集，计算成本低。

### 5. 实验数量与充分性

- **主实验**（表1）：在3个代表性数据集（CoQA、SamSum、Spider）上，用2种模型，对比9种方法（4个基线+5个提议），报告5次随机50/50分组的最大最小值。
- **扩展实验**（表2）：在其他6个数据集（NQ、TriviaQA、CNN、XSum、BIRD、Spider-Realistic）上，用Llama模型对比6种方法（仅ACE指标）。
- **消融实验**（图2-3）：
  - 相似度指标对比（Jaccard vs. ROUGE-1 vs. ROUGE-L）
  - ROUGE-L阈值影响（0.3/0.5/0.7）
  - 分类器类型（随机森林 vs. 逻辑回归）
  - 样本数量对方法稳定性的影响
  - 附录B：在BIRD上进一步比较6种相似度指标（包括SQL专用指标）和5种聚合方法
- **充分性判断**：实验覆盖3种任务、9个数据集、2-3个模型，多种消融和扩展，设计较为全面。但所有实验均为同领域（in-domain）设置，未涉及跨领域泛化，且未对比基于NLI或微调的方法（因其不适用于SQL输出）。

### 6. 论文的主要结论与发现

- **基于相似性的分类聚合方法（clf-pairs、clf-pairs+gen）在ACE指标上显著优于所有基线**，尤其在CoQA上ACE降至0.041（Llama）和0.015（Granite），远低于avg. log prob的0.272和0.808。
- 简单平均（arith-agg）在AUROC上表现合理，但校准误差较大。
- 贝叶斯方法在ATS和AUROC上表现良好，但ACE较差（假设条件独立性不成立）。
- 分类方法对相似度指标不敏感（Jaccard、ROUGE等均可），且对样本数量有较高鲁棒性。
- **在文本-to-SQL任务中**，基于文本的相似度（Jaccard、ROUGE、sbert）表现优于SQL专用指标（如Makiyama），说明通用文本相似度已足够。

### 7. 优点

- **框架统一性**：将多种基于一致性的UQ方法纳入相似性聚合视角，简化了方法对比和扩展。
- **实用性**：完全黑盒，无需访问模型内部；仅需小训练集（50%数据），分类器轻量（随机森林深度4），适合实际部署。
- **多任务验证**：涵盖短文本（QA）、长文本（摘要）、结构化输出（SQL），证明方法通用性。
- **实验设计严谨**：使用5次随机分组的最大值和最小值作为误差线，消融实验覆盖关键因素。

### 8. 不足与局限

- **理论支撑不足**：依赖“一致性假设”，论文承认缺少严格理论证明，且可能存在反例。
- **实验覆盖局限**：
  - 仅在同领域（in-domain）场景下测试，未评估跨领域泛化能力。
  - 未对比基于语义熵、NLI的方法（因不适合SQL），也未测试白盒方法如语义熵。
  - 所有数据集均为公开英文数据集，未涉及多语言或低资源场景。
- **贝叶斯方法的假设过强**：条件独立性和Beta分布假设在现实中可能不成立，导致校准误差高。
- **改进空间**：在ATS和AUROC上，提议方法相比baseline提升有限（尤其AUC通常仅提高0.02-0.08），说明区分正确/错误的能力仍有待提升。
- **潜在偏差风险**：正确性判定依赖ROUGE-L阈值或SQL执行结果，阈值选择可能影响排名；数据集均来自学术benchmark，可能不完全反映真实用户场景。

（完）
