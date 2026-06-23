---
title: "Probabilities Are All You Need: A Probability-Only Approach to Uncertainty Estimation in Large Language Models"
title_zh: 概率就够了：仅用概率估计大语言模型不确定性的方法
authors: "Manh Nguyen, Sunil Gupta, Hung Le"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40531/44492"
tags: ["query:luq"]
score: 8.0
evidence: 利用top-K概率高效估计LLM不确定性
tldr: 该论文针对大语言模型幻觉问题，提出一种无需训练的不确定性估计方法，仅利用模型输出top-K概率近似预测熵，并通过自适应机制选择K以过滤低置信概率。在多个NLP任务上评估，该方法在计算效率与不确定性质量之间取得良好平衡，为LLM可信赖提供了轻量级工具。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有不确定性估计需要多次采样或额外计算，效率低。
method: 使用自适应top-K概率近似预测熵，无需训练和额外样本。
result: 在多个基准上实现了与语义熵方法相当的准确性但更快。
conclusion: 仅用概率即可有效估计LLM不确定性，方法简单高效，便于部署。
---

## Abstract
Large Language Models (LLMs) exhibit strong performance across various natural language processing (NLP) tasks but remain vulnerable to hallucinations, generating factually incorrect or misleading outputs. Uncertainty estimation, often using predictive entropy estimation, is key to addressing this issue. However, existing methods often require multiple samples or extra computation to assess semantic entropy. This paper proposes an efficient, training-free uncertainty estimation method that approximates predictive entropy using the responses' top-K probabilities. Moreover, we employ an adaptive mechanism to determine K to enhance flexibility and filter out low-confidence probabilities. Experimental results on three free-form question-answering datasets across several LLMs demonstrate that our method outperforms expensive state-of-the-art baselines, contributing to the broader goal of enhancing LLM trustworthiness.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）在各类NLP任务中表现优异，但容易产生“幻觉”（hallucination），即生成事实错误或误导性输出。现有不确定性估计方法虽能帮助识别这种幻觉，但通常需要多次采样或额外计算语义熵，成本高昂且依赖外部模型。
- **研究动机**：能否仅利用模型输出的概率（token概率）就高效、准确地估计不确定性？本文希望提出一种**无须训练、无须额外采样**的轻量级方法，提升LLM的可信度。
- **整体含义**：通过理论推导和实验验证，证明仅使用top-K概率即可近似预测熵，从而在保持低计算开销的同时达到甚至超越基于语义的复杂方法，为LLM不确定性估计提供了更实用的方案。

## 2. 方法论：核心思想、关键技术细节与公式

- **核心思想**：基于信息论中的预测熵（Predictive Entropy, PE），但不对所有可能输出求和（不可行），而是仅利用模型生成的**top-K个最高概率响应**来近似PE。同时引入自适应阈值α来动态确定K，过滤低置信度概率。
- **关键技术细节**：
  - 给定输入x，生成N个响应（本文N=10），计算每个响应的概率p(y|x)（通过NLL：p(y|x)=e^{-NLL}）。
  - 按概率降序排列，取前K个（K≤N）。
  - 定义PRO（Probability-Only）不确定性分数：
    \[
    PRO(x) = -\log p^*_K - \sum_{i=1}^K p^*_i \log\frac{p^*_i}{p^*_K}
    \]
    其中 \(p^*_i\) 是第i高概率。
  - 理论证明：PRO是真实预测熵的**下界**（Proposition 1）。这保证了当PRO较高时，真实熵也必然较高，从而有效检测高不确定性情况。
  - **自适应K选择**：设置概率阈值α（0≤α≤1），只保留概率≥α的响应（即 \(p_k \ge \alpha\)）。α通过少量验证集网格搜索确定。α越大，保留的响应越少（极端时K=1）；α=0则保留全部N个。
- **与已有方法的关系**：当K=1时，PRO退化为NLL（Aichberger等人方法）。当K>1时，PRO能捕捉更多分布信息，尤其在高不确定性场景下表现更好。

## 3. 实验设计

- **数据集**：三个自由式问答（free-form QA）数据集：
  - TriviaQA（事实验证）
  - SciQ（科学问答）
  - Natural Questions (NQ)（自然问题）
- **评估基准**：使用AUROC（Area Under ROC Curve）衡量不确定性估计与回答正确性之间的对齐程度。正确性通过ROUGE-L F1分数（阈值0.3）判定。
- **对比方法**（7种基线）：
  - **基于语义的**：Semantic Density (SD), Semantic Entropy (SE), Degree (Deg)
  - **基于概率的**：Predictive Entropy (PE), Negative Log-Likelihood (NLL), Average Log-Likelihood (ALL), Length-normalized Entropy (NE)
- **模型**：5种不同规模的开源LLM：
  - Gemma-2B, Gemma-7B
  - Llama2-13B
  - Falcon-11B, Falcon-40B
- **采样设置**：使用多样束搜索（diverse beam search），温度τ=1，每个问题生成N=10个响应。

## 4. 资源与算力

- 论文中明确说明：**所有实验在一张H100 80GB GPU上完成**。
- 未提及训练时长或总计算量（因为方法是训练-free的，仅需推理计算）。

## 5. 实验数量与充分性

- **实验组数**：共进行15组实验（5个模型 × 3个数据集）。此外还包含以下分析实验：
  - 超参数α的敏感性分析（图1，针对不同模型-数据集组合）。
  - 固定K与自适应K的对比（表2，在TriviaQA上比较K=1~10及PRO）。
  - K-α关系分析（图2）。
  - 不同ROUGE-L阈值（0.1~0.5）下的鲁棒性测试（表4，以Gemma-7B/SciQ为例）。
- **充分性评价**：
  - 覆盖了多个模型家族和规模，数据集覆盖不同领域，对比了7种强基线，实验设计较为全面。
  - 提供了消融（固定K vs 自适应K）和超参数分析，验证了方法设计的合理性。
  - 对正确性判定阈值进行了敏感性检验，提升了评估的客观性。
  - 但仅在自由式问答任务上验证，未涵盖机器翻译、摘要等NLG任务，通用性有待进一步验证。

## 6. 主要结论与发现

- **PRO方法整体最优**：在15组实验中获得11次最佳，平均AUROC达0.739，比第二名（NLL，0.715）提升2.4%，比最昂贵的语义密度（SD，0.709）提升3%。
- **自适应机制有效**：固定K的方法（如K=1即NLL）在部分场景效果好，但整体不如PRO的自适应阈值策略；PRO能根据概率分布动态调整K，更灵活稳定。
- **模型大小与不确定性估计性能并不严格正相关**：例如Gemma-2B比Gemma-7B表现更好，这可能与较大模型幻觉更隐蔽、检测更困难有关。
- **低计算开销**：仅依赖token概率，无需外部模型或语义嵌入，推理成本远低于语义方法。

## 7. 优点

- **理论驱动**：从预测熵的下界推导出发，方法有信息论基础，非仅凭经验。
- **极致轻量**：无需额外训练、无需多次采样（仅用一次生成中的前K个响应）、无需外部NLI或嵌入模型，适合实际部署。
- **自适应性强**：通过概率阈值α动态调整考虑响应数量，兼顾高置信度和低置信度场景。
- **实验充分且公平**：与7种基线在多个模型/数据集上对比，验证了方法的鲁棒性；超参数调优仅在100样本验证集上进行，避免过拟合测试集。
- **可解释性好**：PRO分数可分解为“最可能响应的不确定性”与“次等响应相对于最可能响应的分散度”，直观反映模型自信程度。

## 8. 不足与局限

- **对黑盒模型的限制**：方法需要访问token级别的logits（概率），对于完全黑盒API（仅返回文本）不适用，目前更适合灰盒模型。
- **未考虑语义信息**：完全基于概率，忽略响应之间的语义相似性。可能在某些场景下（如语义相同但措辞不同的正确回答）产生偏差（但实验表明仍能领先语义方法，说明概率信息已足够）。
- **生成策略的潜在偏差**：论文统一使用束搜索（beam search），可能限制生成多样性。作者承认未来应探索采样式解码（如核采样）的影响。
- **任务覆盖面有限**：仅测试自由式QA，未在机器翻译、摘要、对话等任务上验证，通用性需进一步确认。
- **超参数α需调优**：虽然可用小验证集确定，但不同模型-数据集组合的最优α差异较大（从0.05到0.90），实际使用中若无验证集，建议α=0.4作为默认值，但可能不是最优。
- **不适用于零样本（完全黑盒）场景**：部分商业模型（如GPT-4 API）不提供token概率，限制了应用范围。

（完）
