---
title: "Unconditional Truthfulness: Learning Unconditional Uncertainty of Large Language Models"
title_zh: 无条件真实性：学习大语言模型的无条件不确定性
authors: "Artem Vazhentsev, Ekaterina Fadeeva, Rui Xing, Gleb Kuzmin, Ivan Lazichny, Alexander Panchenko, Preslav Nakov, Timothy Baldwin, Maxim Panov, Artem Shelmanov"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.emnlp-main.1807.pdf"
tags: ["query:uq-safety"]
score: 9.0
evidence: 从注意力特征学习LLM无条件不确定性
tldr: 现有LLM不确定性量化受生成步骤条件依赖困扰。本文提出通过学习注意力特征和循环不确定性分数来获得无条件不确定性，采用两阶段训练。实验表明该方法在十个数据集上有效检测幻觉。该方法为LLM可靠性评估提供了新途径。
source: EMNLP-2025-Main
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1807/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1559, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1807/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 757, \"height\": 664, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1807/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1655, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1807/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1325, \"height\": 487, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1650, \"height\": 677, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 803, \"height\": 567, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 805, \"height\": 367, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 798, \"height\": 682, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1651, \"height\": 681, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1651, \"height\": 679, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1651, \"height\": 663, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1649, \"height\": 660, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1651, \"height\": 660, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 836, \"height\": 430, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1000, \"height\": 197, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1654, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1250, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1083, \"height\": 142, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1653, \"height\": 190, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1643, \"height\": 162, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1653, \"height\": 136, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1641, \"height\": 121, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1641, \"height\": 122, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1002, \"height\": 580, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1807/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1652, \"height\": 461, \"label\": \"Table\"}]"
motivation: 现有UQ方法难以建模自回归LLM生成步骤间的条件依赖。
method: 训练回归模型，利用注意力图、当前概率和先前token的递归不确定性分数，采用两阶段训练。
result: 在十个数据集上的实验验证了方法的有效性。
conclusion: 提出无条件的LLM不确定性学习方法，优于基线。
---

## Abstract
Uncertainty quantification (UQ) has emerged as a promising approach for detecting hallucinations and low-quality output of Large Language Models (LLMs). However, obtaining proper uncertainty scores is complicated by the conditional dependency between the generation steps of an autoregressive LLM, because it is hard to model it explicitly. Here, we propose to learn this dependency from attention-based features. In particular, we train a regression model that leverages LLM attention maps, probabilities on the current generation step, and recurrently computed uncertainty scores from previously generated tokens. To incorporate the recurrent features, we also suggest a two-staged training procedure. Our experimental evaluation on ten datasets and three LLMs shows that the proposed method is highly effective for selective generation, achieving substantial improvements over rivaling unsupervised and supervised approaches.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：自回归大型语言模型（LLM）在逐token生成时，每一步的预测都依赖于之前生成的token，导致条件不确定性难以量化。当早期生成错误（如幻觉）时，该错误会传播，但后续token的置信度却可能很高，传统基于概率的UQ方法无法捕捉这种依赖，从而低估整体不确定性。
- **研究意义**：有效的UQ可以用于选择性生成（即拒绝低质量输出），从而提升LLM的安全性和实用性。本文旨在提出一种**数据驱动的、能够显式学习生成步间条件依赖**的无条件不确定性估计方法。

### 2. 论文提出的方法论

- **核心思想**：学习一个回归模型 C(·)，它利用当前step的注意力权重 Attᵢ、条件概率 p(yᵢ|y<ᵢ) 以及**循环计算的前续token的无条件信心分数 C<ᵢ**，来估计每个token的无条件概率 C(yᵢ)。最终通过聚合得到序列级不确定性。
- **关键技术细节**：
  - **训练数据生成**：使用原始数据集，对每个生成序列 y 与其真实值 y* 计算语义相似度（如Accuracy、COMET、AlignScore）作为每个token的监督目标 ˆp(yᵢ)。
  - **特征构建**：对于每个 token yᵢ，构建特征向量 zᵢ，包含：当前及前 N 个token的条件概率、前 N 个token的注意力权重（从所有层和头）、以及前 N 个token的估计无条件概率 ˆp(yᵢ₋ₗ)。
  - **两阶段训练**：第一阶段仅用条件概率训练初步模型 C₁；第二阶段用 C₁ 的预测作为循环特征，重新训练最终模型 C₂。这避免了过拟合，并真正实现了递归信息引入。
  - **推理阶段**：第一个token的无条件概率取其条件概率，后续token通过 C₂ 递归计算，最终序列不确定性 U(y) = 1 - (1/n) Σ C(yᵢ)。
  - **回归模型**：线性回归（LinReg）或 MLP，经交叉验证选择超参数。

### 3. 实验设计

- **数据集与场景**：覆盖5类任务，共10个数据集。
  - 文本摘要：XSum、SamSum、CNN/DailyMail
  - 机器翻译：WMT19（德→英）
  - 长回答QA：MedQUAD、TruthfulQA、GSM8k
  - 短回答QA：CoQA、SciQ、TriviaQA
  - 多项选择QA：MMLU
- **LLM模型**：LLaMA-3.1 8b、Gemma-2 9b、Qwen-2.5 7b。
- **对比方法**：
  - 无监督基线：MSP、Perplexity、Mean Token Entropy、Lexical Similarity、Semantic Entropy、SAR、Focus、CCP、EigenScore、Semantic Density等。
  - 有监督基线：Factoscope、SAPLMA、MIND、Sheeps、LookBackLens、SATRMD。
- **评估指标**：主要采用选择性生成指标 **PRR**（归一化的预测拒绝比），辅助使用 **ROC-AUC**。质量度量因任务而异（Accuracy、COMET、AlignScore）。

### 4. 资源与算力

- **文中明确说明**（附录B）：
  - GPU：单张 **NVIDIA H100（80GB）**
  - 训练总时间：超过 **750 GPU小时**
  - 测试推理时间：**260 GPU小时**
  - 平均每个实例的推理时间：TAD仅比MSP多5%开销，远低于采样类方法（400-580%）。

### 5. 实验数量与充分性

- **实验数量**：非常充分。
  - 主实验：3个LLM × 10个数据集 = 30组全面对比，结果以表格和热力图呈现。
  - 消融实验：超过5组，包括对特征组合、训练步数、前驱token数量、注意力层重要性、聚合方式、回归模型类型等。
  - 额外分析：跨域泛化实验（在QA上训练，在摘要/翻译上测试）、注意力图可视化、运行时效率比较。
- **充分性与公平性**：所有超参数通过内部5折交叉验证选取；对比基线涵盖主流无监督/有监督方法；使用相同生成配置；PRR指标按50%拒绝阈值计算以贴近实际。整体实验设计客观、公平、全面。

### 6. 论文的主要结论与发现

1. **TAD在所有任务上平均排名第一**（平均排名1.82，远低于第二位的LookBackLens 4.45），在PRR指标上显著优于所有无监督和有监督基线。
2. **注意力特征和循环训练至关重要**：消融实验表明，移除注意力或仅用单步训练会导致性能大幅下降。
3. **跨域泛化能力较强**：在未见过的QA领域数据上，TAD仍优于MSP等基线；但在跨任务（QA→摘要/翻译）时性能下降明显，仅TAD相对其他监督方法表现更好，但不如无监督MSP。
4. **计算高效**：仅增加5%推理开销，适合实际部署。

### 7. 优点

- **数据驱动建模依赖**：首次通过监督学习直接学习生成步间的条件依赖，而非启发式规则（如Focus、SAR）。
- **两阶段训练设计**：避免了递归特征引入时的伪相关和过拟合。
- **特征通用有效**：注意力权重提供丰富的依赖信号，且与概率互补。
- **鲁棒性**：在所有模型和数据集上表现稳定，避免了其他监督方法在某些任务上远逊于简单基线的情况。
- **低计算开销**：线性回归模型极轻量，适合在线应用。

### 8. 不足与局限

- **监督数据依赖**：需要与目标任务一致的训练数据（含有质量标注）。跨任务泛化有限，在摘要/翻译等不同于训练域的OOD任务上表现不如简单无监督方法。
- **模型规模限制**：仅在7-9B参数模型上实验，未验证更大尺度（如70B+）上的有效性，虽作者认为结构相似但仍有不确定性。
- **理论分析薄弱**：虽然从全概率公式引出递归思想，但实际建模完全黑箱，缺乏对学习到的依赖函数可解释性分析。
- **注意力解释性争议**：使用注意力权重作为依赖特征虽有效，但“注意力即解释”在近年受到质疑，可能存在噪声。

（完）
