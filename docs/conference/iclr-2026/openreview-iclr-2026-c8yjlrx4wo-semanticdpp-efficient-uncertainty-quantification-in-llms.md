---
title: "SemanticDPP: Efficient Uncertainty Quantification in LLMs"
title_zh: "SemanticDPP: 大型语言模型中高效的不确定性量化"
authors: "Jenny Hamer, Jasper Snoek, Alexander Nicholas D'Amour, Ulrich Rueckert, Dheeraj Rajagopal, Victor Veitch, Jie Ren, Kevin Robinson"
date: 2025-09-17
pdf: "https://openreview.net/pdf?id=C8yjlrx4Wo"
tags: ["query:luq"]
score: 8.0
evidence: SemanticDPP通过内部激活高效量化语义不确定性
tldr: 现有不确定性方法计算成本高。本文提出SemanticDPP，基于LLM内部激活表示快速量化语义变化的不确定性。与多序列采样方法相比，SemanticDPP在保持高准确性的同时大幅降低延迟，为实时应用提供可行方案。实验在幻觉检测和错误定位上验证了其优越性。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-c8yjlrx4wo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1429, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-c8yjlrx4wo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1327, \"height\": 827, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-c8yjlrx4wo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1457, \"height\": 766, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-c8yjlrx4wo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1448, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-c8yjlrx4wo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1452, \"height\": 211, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-c8yjlrx4wo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 777, \"height\": 454, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-c8yjlrx4wo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 719, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-c8yjlrx4wo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1306, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-c8yjlrx4wo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1441, \"height\": 373, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-c8yjlrx4wo/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 791, \"height\": 388, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-c8yjlrx4wo/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1385, \"height\": 240, \"label\": \"Table\"}]"
motivation: 高效且准确的不确定性量化方法仍是需求缺口。
method: 利用LLM内部激活通过行列点过程度量语义变化不确定性。
result: 在多个任务上，SemanticDPP以更低计算成本实现更好或相当的不确定性估计。
conclusion: 内部激活提供了一种高效可靠的语义不确定性信号。
---

## Abstract
Accurately quantifying uncertainty is crucial for ensuring the reliability of model outputs and enabling informed downstream decision-making. However, the output space of large language models (LLMs) is so large that traditional methods break down in this setting; yet, LLMs have been shown to respond to prompts confidently with confabulations, fabrications, ``hallucinations’’, and other erroneous information. While methods designed specifically for LLMs exist, there is a gap and need for approaches which accurately quantify uncertainty efficiently. In this work, we introduce SemanticDPP, an efficient method for quantifying the uncertainty corresponding to the semantic variation in outputs of a large language model based on internal activations. Building upon prior work, we show that this uncertainty is highly indicative of whether or not a model will answer correctly in question answering (QA) tasks---which provides a useful signal to determine whether to abstain from responding to a given question to prevent incorrect answers.
SemanticDPP uses determinantal point processes (DPPs) to learn a model over semantic (dis)similarity in model embeddings, which we use in a fully unsupervised manner to identify semantically distinct sets of responses.  We additionally present an extension, SemanticDPP-C, which yields a soft clustering of the sets of semantically distinct responses. Our extensive empirical investigation examines the behavior of our methods on two frontier open-sourced models of different capacities (that grant access to model internals), Gemma2 9B and Gemma3 27B, on a broad range of widely used QA benchmarks. SemanticDPP enables fast uncertainty quantification while it matches or exceeds the selective prediction (hallucination detection) performance of state-of-the-art baselines.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义（研究动机和背景）

大型语言模型（LLM）的输出空间极其庞大，传统的不确定性量化方法在此场景下失效。LLM常常自信地产生虚构、捏造或“幻觉”等错误信息，而现有方法（如语义熵）虽能有效检测不确定性，但依赖另一个LLM进行双向蕴涵比较来聚类响应，计算成本极高（单次测试可达数小时），且硬聚类只能提供粗粒度的不确定性度量。本文旨在提出一种高效、细粒度且无需外部LLM辅助的不确定性量化方法，以便在问答任务中通过不确定性信号决定是否放弃回答，从而减少错误输出。

### 2. 方法论

#### 核心思想
- 利用LLM内部激活（嵌入向量）表示响应的语义含义，通过行列点过程（Determinantal Point Process, DPP）学习嵌入空间中语义（不）相似性的概率模型。
- DPP能够对集合的概率进行建模，倾向于选择多样化的子集（语义不同的响应集合），从而量化不确定性。
- 在无监督方式下，通过最大化DPP的边际似然拟合核函数参数，得到可用于高效推理的模型。

#### 关键技术细节
1. **嵌入表示**：从LLM最后一层提取每个生成响应的嵌入，并对所有token的嵌入进行平均，再执行白化变换。
2. **核函数**：定义语义相似性核：  
   \[
   k(x_i, x_j) = \exp(-\alpha \|\phi(x_i) - \phi(x_j)\|^2)
   \]  
   其中 \(\phi\) 是一个单隐藏层神经网络（GELU激活），用于将原始嵌入投影到低维语义子空间。
3. **DPP模型**：使用L-ensemble形式，子集 \(Y\) 的概率为：
   \[
   P_L(Y) = \frac{\det(L_Y)}{\det(L + I)}
   \]  
   其中 \(L\) 是核矩阵。
4. **训练损失**（负边际对数似然）：
   \[
   \mathcal{L} = -\frac{1}{n}\sum_{i=1}^n \left[\log\det(L_{Y_i}) - \log\det(L_i + I)\right]
   \]  
   鼓励 \(Y_i\) 中的响应在嵌入空间中彼此远离（多样性），同时使所有响应总体接近。
5. **推理**：对于一组新响应 \(S\)，其不确定性为：
   \[
   \log P(S) = \log\det(K_S) = \log\det(L_S (L_S + I)^{-1})
   \]  
   其中 \(K\) 是边际核。
6. **SemanticDPP-C扩展**：通过贪心MAP近似选取期望基数 \(k = \text{round}(\text{tr}(K))\) 个簇中心，再将剩余响应分配给最近中心，实现软聚类和概率分配。

### 3. 实验设计

- **数据集**：6个广泛使用的QA基准：TruthfulQA、GSM8k、TriviaQA、BioASQ、NQ Open、SQuAD（均为英文）。
- **基准任务**：选择性预测（abstain），通过不确定性阈值控制是否回答，绘制ROC曲线并计算AUROC。
- **对比方法**：
  - 语义熵（Semantic Entropy，需外部LLM）
  - 线性探针（Linear Probe）
  - EigenScore（基于核的行列式）
  - 无投影版SemanticDPP/DPP-C（消融）
  - P(True)
  - Token平均似然
- **生成模型**：Gemma2 9B 和 Gemma3 27B（两个开源模型，允许访问内部嵌入）。
- **评估方式**：5折交叉验证，报告平均AUROC和标准差。

### 4. 资源与算力

论文**未明确说明**训练所使用的GPU型号、数量或总训练时长。但在推断时间方面提供了详细数据（表4、表8）：
- SemanticDPP推断时间：在TriviaQA测试集（9,961条）上仅需0.00186秒（累计），Semantic Entropy需约57.4小时（使用16个并行Gemini 1.5 Flash实例）。
- 训练过程：使用Adam优化器，超参数搜索（学习率、隐藏单元数、低秩维度等），但未报告具体计算资源消耗。

### 5. 实验数量与充分性

- **主要实验**：在6个数据集×2种模型上比较了10种方法（含消融），共产生12张AUROC表（表1、2）及PR/ROC曲线（图3）。
- **转移学习实验**（表3）：将一个数据集上训练的模型直接应用于其他5个数据集，测试泛化能力。
- **消融实验**：无投影版本（No Projection SemanticDPP/DPP-C），验证学习投影的必要性。
- **充分性与公平性**：实验覆盖了多个任务领域（常识、数学、生物、开放域等），使用5折交叉验证减少随机性，统计误差线展示。对比方法均采用公开标准或官方实现。但所有数据集均为英文，缺乏多语言验证；部分数据集（TriviaQA、NQ Open）存在时间偏差，导致标签过时，可能影响评估公平性。

### 6. 主要结论与发现

- **性能**：SemanticDPP和SemanticDPP-C在大多数数据集上AUROC最高或接近最优，尤其在聚合得分上持续领先（Gemma2 9B：0.74；Gemma3 27B：0.68）。
- **效率**：推断速度比语义熵快数千倍，从数小时降至毫秒级，适合实时应用。
- **泛化**：在BioASQ或TruthfulQA上训练的模型可较好迁移至其他任务，而数学专用训练（GSM8k）泛化性较差。
- **细粒度**：嵌入距离提供了比硬聚类更细致的不确定性区分，在高精度区域表现更优。
- **局限性**：方法依赖多次采样（增加计算开销），且需要访问模型内部嵌入；未覆盖低概率但高风险响应。

### 7. 优点

- **高效性**：推断仅需一次核矩阵行列式计算（规模为采样数m，通常m≤20），远快于任何依赖外部LLM比较的方法。
- **无监督且可迁移**：仅需嵌入向量，无需标注数据；在一个任务上训练的模型可零样本迁移到其他任务。
- **细粒度**：利用连续距离而非硬聚类，提供更精细的不确定性度量。
- **拟合简洁**：DPP训练损失天然包含对比学习效果（推远多样化子集、拉近整体），无需额外正则化。

### 8. 不足与局限

- **依赖多次采样**：仍需要从LLM中采样多个响应（本文使用m=10~20），增加生成成本。
- **要求模型内部访问**：无法应用于闭源或黑盒LLM，仅适用于开源模型。
- **仅英文基准**：实验未扩展到多语言或更广泛的任务（如对话、摘要生成）。
- **尾部风险响应缺失**：方法假设响应分布集中于少数语义簇，难以捕获罕见但关键的低概率响应。
- **训练数据仍依赖外部LLM**：虽可替换，但当前实验中用于生成伪标签的语义熵聚类仍依赖另一个LLM（Gemini 1.5 Flash），未完全消除对外部模型的依赖。
- **数据集偏差**：部分基准标签因时间变化而失效，可能高估实际错误率，影响评估客观性。

（完）
