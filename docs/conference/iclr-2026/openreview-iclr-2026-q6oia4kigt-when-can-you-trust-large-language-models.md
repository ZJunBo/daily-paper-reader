---
title: When Can you TRUST Large Language Models?
title_zh: 何时可以信任大语言模型？
authors: "Radu Paradovschi, Darvin Yi, Andrew Rabinovich, Zhao Chen"
date: 2025-09-11
pdf: "https://openreview.net/pdf?id=Q6OIA4KIGT"
tags: ["query:luq"]
score: 9.0
evidence: TRUST分数用于LLM不确定性量化
tldr: 针对现有UQ方法局限于少量后续token的不足，论文提出TRUST（温度相关无歧义性相似度追踪）分数，利用LLM输出的自然语义分支，在完整输出上评估不确定性。该方法考虑整个生成序列的语义相似性，提供更全面的不确定性度量，在多个基准上表现优异。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-q6oia4kigt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1409, \"height\": 997, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-q6oia4kigt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1367, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-q6oia4kigt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1110, \"height\": 662, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-q6oia4kigt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1453, \"height\": 987, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-q6oia4kigt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 955, \"height\": 578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-q6oia4kigt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 955, \"height\": 550, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-q6oia4kigt/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 964, \"height\": 557, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-q6oia4kigt/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1363, \"height\": 1066, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-q6oia4kigt/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 431, \"height\": 648, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-q6oia4kigt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 195, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-q6oia4kigt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 231, \"label\": \"Table\"}]"
motivation: 现有UQ方法无法捕捉整个输出序列的语义复杂性，需要全局度量。
method: 提出TRUST分数，利用语义分支相似性在整个输出上量化不确定性。
result: TRUST在多种任务上有效区分可靠与不可靠输出。
conclusion: 全局语义相似性度量可提升UQ的全面性和可靠性。
---

## Abstract
Quantifying neural network model uncertainty is a difficult problem that has far-reaching implications on our ability to improve model reliability. Uncertainty quantification is especially difficult in the context of LLMs and autoregressive models, as standard methods for uncertainty measurement that apply to single outputs often fail to capture the semantic complexity of the entire autoregressive output. To remedy this gap, we introduce TRUST (Temperature-Related Unambiguity via Similarity Tracking) scores, a novel approach for quantifying LLM uncertainty which reasons about uncertainty $\textit{across the entire model output}$ rather than being limited to a small number of subsequent tokens. TRUST scores take advantage of the natural semantic branching of LLM outputs for nonzero temperatures, and calculate uncertainty based on semantic similarity of multiple output rollouts for an LLM model. We show that TRUST outperforms industry standard uncertainty methods within complex multi-token language tasks like predicting math problem difficulty, and also can be distilled into efficient forward-pass models for easy inference. Crucially, TRUST scores can be calculated with nothing more than standard LLM calls and require zero white-box access to model internals.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：现有的大语言模型（LLM）不确定性量化（UQ）方法大多局限于单个输出或少量后续token，无法捕捉整个自回归输出序列的语义复杂性。LLM常常“自信地错误”，缺乏对自身不确定性的可靠表达，这在安全关键领域（如金融、医疗）中尤为危险。
- **研究动机**：需要一种能够**在整个语义输出层面**评估不确定性的实用方法，且无需访问模型内部状态（黑盒），同时保持理论基础和计算可行性。
- **整体含义**：提出一种新的不确定性度量——TRUST分数，旨在填补传统单步方法（如熵、最大软概率MSP）与多token语义复杂性之间的空白，提升LLM的可靠性和信任度。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：利用LLM在非零温度下输出的自然语义分支，通过多次采样输出并计算它们之间的**平均语义相似度**来量化不确定性。相似度越高，不确定性越低。
- **关键技术细节**：
  - 对于每个输入查询，生成 \(2N\) 个完整响应（温度 \(\tau > 0\)）。
  - 使用一个独立的**裁判模型（judge model）**（如GPT-4o）对响应进行成对语义相似度评分（1~5分制）。
  - TRUST分数定义为这些成对相似度的平均值：\[ \text{TRUST}_{j,t} = \frac{1}{N} \sum_{i=1}^{N} J\big(\text{Concat}(r_{j,t}, y_{j,2i-1}), \text{Concat}(r_{j,t}, y_{j,2i})\big) \] 其中 \(r_{j,t}\) 是部分前缀（t个token），\(y\) 是完整补全。
  - 分数可针对每个token位置计算，通过固定前缀后的补全变化来反映局部不确定性。
- **理论关系**：在单token预测极限下，若裁判模型完美判别token是否相同，则TRUST的期望值等于MSP的平方加上高阶项，即 \(\mathbb{E}[\text{TRUST}] = (\max_i p_i)^2 + O(p_2^2)\)，因此TRUST是MSP的自然推广。
- **蒸馏模型**：为了加速推理，可以训练一个轻量级BERT模型来直接预测TRUST分数，避免每次计算大量采样。

## 3. 实验设计：数据集/场景、基准、对比方法
- **数据集/场景**：
  - **简单人类偏好数据集**：80个简单问题（如“你最喜欢的宠物是什么？”），每个问题有10种不同回答。通过**混合因子M**控制数据集的多样性和不确定性（M=0时全是同一回答，M=9时均匀分布）。
  - **MATH数据集**：包含开放式的数学问题，标注了1~5级难度，用于预测难度等级（一种复杂语义不确定性任务）。
- **基准（baseline）方法**：
  - 香农熵（Shannon entropy）
  - 最大软概率（MSP）
  - MSP的平方（MSP²）
  - 语义熵（Semantic Entropy, Kuhn et al. 2023）
  - 表达不确定性（Expressed Uncertainty, 直接让LLM表达置信度）
  - 集成KL散度（Ensemble KL divergence, 仅当有白盒访问时）
- **评估指标**：
  - 简单实验：各度量与混合因子M的**相关系数**。
  - MATH实验：预测难度等级的**均方误差（MSE）**。

## 4. 资源与算力
- 论文中**未明确说明**所使用的具体GPU型号、数量或训练时长。
- 提及了生成模型：GPT-4o-mini（通过API调用）、Llama-3.1-70b（通过Fireworks AI API）。裁判模型固定为GPT-4o。
- 蒸馏模型使用BERT（base），训练细节未给出具体算力消耗。
- 总体而言，论文侧重于方法本身，缺乏对计算成本的量化报告。

## 5. 实验数量与充分性
- **实验数量**：
  - 简单偏好数据集：10个不同混合因子（M=0~9），每个因子独立微调一个LoRA适配器，共10次试验，重复十次取均值±标准差。
  - MATH数据集：两种生成模型（GPT-4o-mini, Llama-3.1-70b），每种模型计算多种不确定性度量，并训练投影层预测难度，报告MSE及误差。
  - 消融：比较了不同温度（0.3, 0.6, 1.0）下的TRUST表现（见附录）。
- **充分性与公平性**：
  - 实验设计较为全面：涵盖了简单合成数据（可控）和复杂真实数据（MATH），对比了多种代表性UQ方法。
  - 但在MATH实验中，对比方法（如语义熵、表达不确定性）表现明显较差，而TRUST和蒸馏模型表现优异。论文声称TRUST在复杂场景下优势显著，但缺少对更多类型数据集（如对话、翻译、代码生成）的验证。
  - 集成KL散度仅对Llama模型计算（因GPT-4o无白盒访问），可能导致对比不完整。
  - 所有实验均基于特定模型（GPT-4o-mini, Llama-3.1-70b, GPT-4o），未在不同规模或异构模型上测试泛化性。

## 6. 论文的主要结论与发现
- TRUST分数在简单偏好数据集上与语义熵性能相当，但优于MSP、熵等传统方法。
- 在MATH难度预测任务中，TRUST显著优于所有baseline，MSE更低且不同难度等级的可分离性更明显。
- 蒸馏BERT模型（\hat{TRUST}）与原始TRUST性能接近，可大幅降低推理成本。
- TRUST对温度选择鲁棒，不同温度下仍能保持区分能力。
- TRUST是一种**总不确定性**度量，对本质不确定性（aleatoric）和认知不确定性（epistemic）都敏感。

## 7. 优点：方法或实验设计上的亮点
- **方法创新**：将语义相似度引入不确定性量化，能够捕捉整个输出序列的语义信息，摆脱了传统方法对token级概率的依赖。
- **实用性**：完全黑盒操作，仅需标准LLM API调用，无需访问logits或激活值，适用于任何LLM。
- **可蒸馏**：可通过轻量模型（如BERT）近似，实现快速实时推理，降低计算开销。
- **理论支撑**：证明了在单token情况下TRUST与MSP²的关系，提供了理论合理性。
- **实验设计合理**：使用了两种不同复杂度的任务，对比了多种主流UQ方法，且给出误差估计，结果可靠。

## 8. 不足与局限
- **实验覆盖有限**：仅测试了偏好数据和数学题难度预测两类任务，未在更广泛的应用（如问答、摘要、代码生成、对抗性输入）上验证。
- **依赖裁判模型**：裁判模型（GPT-4o）本身可能引入偏差或错误，且其评分标准（1~5分制）的主观性可能影响结果。论文未检验裁判模型的鲁棒性。
- **缺少大范围消融**：未探索不同N（采样数量）的影响，也未系统研究温度τ的选取策略。
- **难以分解不确定性类型**：TRUST被定义为总不确定性，未区分本质与认知不确定性，限制了在某些场景下的可解释性。
- **计算成本**：虽然可蒸馏，但原始TRUST需要多次采样和多次裁判调用，成本高于单次推理方法。论文未量化实际计算时间或API费用。
- **泛化性存疑**：只在两个LLM（GPT-4o-mini, Llama-3.1-70b）上生成响应，裁判模型固定为GPT-4o，结果可能无法直接迁移至其他模型或裁判模型。

（完）
