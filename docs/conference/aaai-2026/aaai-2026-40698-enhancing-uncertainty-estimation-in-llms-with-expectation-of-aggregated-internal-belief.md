---
title: Enhancing Uncertainty Estimation in LLMs with Expectation of Aggregated Internal Belief
title_zh: 利用聚合内部信念期望增强LLM不确定性估计
authors: "Zeguan Xiao, Diyang Dou, Boya Xiong, Yun Chen, Guanhua Chen"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40698/44659"
tags: ["query:luq"]
score: 9.0
evidence: 提出EAGLE方法，利用内部隐藏状态进行LLM不确定性估计
tldr: LLM常过度自信，RLHF模型尤甚。本文提出EAGLE（聚合内部信念期望），通过从自评估过程中提取多个中间层的内部信念并聚合，得到更准确的置信度分数。实验表明，EAGLE显著提升了校准性能，减少了过自信输出，对安全部署有价值。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: LLM在RLHF后过度自信，导致置信度估计不准确。
method: 从模型自评估过程中的多个中间层提取内部信念并聚合，得到校准置信度。
result: 在多个LLM上，EAGLE显著降低校准误差，优于基线方法。
conclusion: 利用内部状态可有效提升不确定性估计可靠性。
---

## Abstract
Large Language Models (LLMs) have achieved remarkable success across a wide range of natural language tasks, but often exhibit overconfidence and generate plausible yet incorrect answers. This overconfidence, especially in models undergone Reinforcement Learning from Human Feedback (RLHF), poses significant challenges for reliable uncertainty estimation and safe deployment.
In this paper, we propose EAGLE (Expectation of AGgregated internaL bEief), a novel self-evaluation-based calibration method that leverages the internal hidden states of LLMs to derive more accurate confidence scores.
Instead of relying on the model's final output, our approach extracts internal beliefs from multiple intermediate layers during self-evaluation. By aggregating these layer-wise beliefs and calculating the expectation over the resulting confidence score distribution, EAGLE produces a refined confidence score that more faithfully reflects the model's internal certainty. Extensive experiments on diverse datasets and LLMs demonstrate that EAGLE significantly improves calibration performance over existing baselines.
We also provide an in-depth analysis of EAGLE, including a layer-wise examination of uncertainty patterns, a study of the impact of self-evaluation prompts, and an analysis of the effect of self-evaluation score range.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：大型语言模型（LLM）在经历RLHF（人类反馈强化学习）后往往表现出过度自信，输出看似合理但错误的答案（幻觉现象），这严重影响了不确定性估计的可靠性，阻碍了安全部署。
- **研究动机**：现有自评估校准方法主要依赖模型最终输出的表层置信度分数（verbalized confidence），未能充分利用模型内部隐藏状态中蕴含的丰富置信信息。已有研究表明，中间层的隐藏状态能够区分高/低置信预测，因此本文提出利用多层内部信念的聚合期望来提升校准性能。
- **整体含义**：通过从模型自评估过程中提取多个中间层的内部表示并聚合，得到更忠实反映模型真实不确定性的置信度分数，从而提升LLM的可信度。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：EAGLE（Expectation of Aggregated Internal Belief）是一种无需训练的自校准方法，通过聚合多个中间层的隐藏状态（投影为logits）并计算置信度分数分布的期望，获得更准确的置信度。
- **关键技术细节**：
  1. 给定问题x和模型生成的答案ŷ，用特定提示词（如“0-9分评价答案正确性”）让模型进行自评估。
  2. 前向传播后，提取自评估token在最后k个层（如最后若干层）的隐藏状态 \( H^{(l)}_n \)。
  3. 将每个层的隐藏状态通过解嵌入矩阵（unembed）映射为词汇空间logits \( z^{(l)}_n \)。
  4. 对各层logits取平均得到聚合logits \( z_n = \frac{1}{k}\sum_l z^{(l)}_n \)。
  5. 仅考虑置信度分数集合S={0,...,9}对应的logits，经softmax得到概率分布 \( w_s = \frac{\exp(z_{n,s})}{\sum_{s'\in S}\exp(z_{n,s'})} \)。
  6. 最终置信度 \( C(\hat{y}|x) = \sum_{s\in S} w_s \cdot s \)（即分数分布的期望），而非仅取最大概率分数。
- **创新点**：① 利用多层隐藏状态聚合而非仅用最终层；② 取期望而非最大概率，捕获更丰富的内部信念信息。

### 3. 实验设计：数据集 / 场景、benchmark、对比方法
- **数据集**：
  - 开放生成任务：TriviaQA（rc.nocontext子集）和GSM8K。
  - 多选题任务：MMLU。
  - 超参数调优：使用TriviaQA和GSM8K的训练集子集、MMLU验证集。
- **模型**：Qwen2.5（7B、72B）和Llama3（8B、70B）的Instruct版本（RLHF模型）。
- **对比方法（baselines）**：
  - Semantic Entropy (SE)
  - Self-consistency (Self-cons.)
  - P(True)
  - Contextualized Sequence Likelihood (CSL)
- **评价指标**：
  - 校准性能：Expected Calibration Error (ECE)，10 bins。
  - 判别性能：AUROC（区分正确/错误答案的能力）。

### 4. 资源与算力
- 论文**未明确说明**使用了多少GPU型号、数量、训练时长等计算资源。仅提及实验在Qwen2.5和Llama3的多种规模模型上进行，但未提及具体硬件配置。因此无法总结算力细节。

### 5. 实验数量与充分性
- **主要实验**：在3个数据集（TriviaQA、GSM8K、MMLU）× 4个模型（Llama3 8B/70B、Qwen2.5 7B/72B）上评估了4个baseline + EAGLE，共得到4组×3数据集=12个主要结果（表1），并报告了ECE和AUROC。
- **消融实验**：针对EAGLE的三个设计选择（层选择：仅最后层 vs. 多层；聚合方式：概率聚合 vs. logits聚合；最终分数：最大概率 vs. 期望）进行了系统消融（表2）。
- **额外分析**：
  - 层间校准性能热力图（图2），展示不同起始层到终止层的ECE/AUROC。
  - EAGLE用于答案选择（表3），通过多次采样选择置信度最高的答案提升准确率。
  - 提示词敏感性实验（表4），对比三种不同自评估提示。
  - 置信度分数范围影响（表5），比较0-9、0-4、0-1三种范围。
- **充分性评价**：实验覆盖了不同规模、不同架构的模型，以及开放式和多选任务；消融实验系统验证了各组件的必要性；额外分析探讨了层选择、提示鲁棒性、分数粒度等影响因素。整体设计较为充分、客观、公平。但未在真实应用场景（如医疗、法律）中测试，且所有模型均为英文指令微调模型，可能缺乏语言和领域多样性。

### 6. 论文的主要结论与发现
- EAGLE在所有评估设置下**显著降低ECE**，例如Llama3 8B在TriviaQA上ECE从15.5降至1.7，Llama3 70B上从16.0降至2.0；平均ECE远低于所有baseline。
- AUROC方面，EAGLE通常取得最高或竞争力最强的结果，表明其不仅校准好，还能有效区分正确/错误答案。
- 消融表明：多层聚合优于单层；logits聚合优于概率聚合；期望分数优于最大概率分数。
- 层分析显示：最优性能来自最后若干层的聚合，简单“last-n”策略已接近最优。
- 提示词鲁棒性：提供清晰评分标准的提示效果最佳，CoT可能引入噪声；分数范围越细（0-9）校准越好。
- EAGLE可用于答案选择：通过选择置信度最高的答案提升准确率（TriviaQA上Llama3 8B准确率从71.3%升至74.8%）。

### 7. 优点：方法或实验设计上的亮点
- **方法创新**：首次将多层隐藏状态聚合应用于自评估校准，并采用期望而非点估计，捕获更完整的内部信念。
- **无需训练**：完全无训练，即插即用，适用于任何可提供隐藏状态的解码器LLM。
- **实验全面**：涵盖多种模型规模、多种任务类型，消融和敏感性分析详尽，结论可信。
- **实用性强**：不仅提升校准，还能直接用于答案选择，提高下游任务准确率。

### 8. 不足与局限
- **实验覆盖局限**：仅在英文问答和数学推理数据集上评估，未涉及长文本生成、对话、多模态等场景；模型仅限Llama3和Qwen2.5系列，未测试其他架构（如Mistral、Gemma等）或基础模型（非指令微调）。
- **偏差风险**：依赖自评估提示词的设计，不同提示可能影响结果（虽已测试三种但仍有局限性）；且所有实验基于RLHF后的模型，对未对齐模型的效果未知。
- **应用限制**：方法需要访问模型所有中间层的隐藏状态，可能对部分商用API模型不可用；计算成本略高于仅用最终层（但远低于多次采样方法）。
- **未探讨鲁棒性**：未测试对抗样本、分布外数据等情况下的校准性能。

（完）
