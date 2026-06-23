---
title: Sampling-Free Uncertainty Quantification via Hidden State Dynamics in Language Models
title_zh: 基于隐藏层动态的无采样不确定性量化
authors: "Yixin Bu, Guanyun Zou, Renzhi Wang, Runze Xia, Cunjun Wang, Hongliang Dai, Xiaoqing Ma, Piji Li"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40259/44220"
tags: ["query:luq"]
score: 9.0
evidence: 基于隐藏层动态的无采样不确定性量化
tldr: 当前LLM不确定性量化方法因依赖大量采样或外部模型而存在计算瓶颈。本文提出一种创新的无采样不确定性量化框架，通过对隐藏层表示进行层次化内部语义动态建模，实现实时不确定性估计。该方法无需额外采样或模型调用，在保持准确性的同时大幅降低计算开销，为LLM可靠性评估提供了高效新思路。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有不确定性量化方法因依赖大量采样或外部模型调用而效率低下。
method: 分析隐藏层内部语义动态，建模层次化表示以直接量化不确定性。
result: 在多种任务上实现实时不确定性估计，兼顾准确性与效率。
conclusion: 为LLM不确定性量化提供了一种高效、无采样的新范式。
---

## Abstract
Large language models (LLMs) demonstrate remarkable capabilities in various complex language tasks, yet they face significant reliability challenges, including factual inaccuracies and generated biases. Uncertainty quantification (UQ) plays a pivotal role in assessing model trustworthiness, particularly for high-stakes applications. However, current UQ methods for LLMs encounter computational efficiency bottlenecks due to their reliance on extensive sampling or external model invocations. In this work, we introduce a novel, sampling-free uncertainty quantification framework centered on hidden layer representation analysis. Our method facilitates real-time uncertainty quantification by modeling hierarchical internal semantic dynamics during the generation process. Through comprehensive experiments on multiple QA datasets and diverse model scales, we show that our approach consistently outperforms existing uncertainty quantification techniques in distinguishing correct from incorrect generations. Our results reveal that analyzing the dynamic evolution of hidden states provides a potent and computationally efficient signal for uncertainty quantification, directly from the model's internal workings, surpassing methods that depend solely on output probabilities or approximations via multiple samples.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大型语言模型（LLMs）在复杂语言任务中表现出色，但存在事实错误和生成偏差等可靠性问题。不确定性量化（UQ）对于评估模型可信度至关重要，尤其是在高风险应用中。
- **现有方法瓶颈**：当前UQ方法主要依赖蒙特卡洛采样（多次生成）或外部模型（如语义评估API），导致计算开销大、延迟高，且可能引入外部误差积累。
- **本文目标**：提出一种**无采样**的UQ框架，通过直接分析模型内部隐藏层的语义动态，实现实时、高效的不确定性估计，避免多次前向传播和外部模型调用。

## 2. 方法论

- **核心思想**：模型生成每个token时，其隐藏状态在不同层中的演化轨迹（语义稳定性与收敛速度）反映了模型对该token的置信度。不确定性高的token表现为早期波动大、后期收敛缓慢；确定性高的token则早期稳定、后期快速收敛。
- **关键技术细节**：
  1. **层间语义相关性评分（LSR-Score）**：对每个token，计算每层隐藏状态与最终层输出的余弦相似度，得到语义轨迹 \(\{s_t^{(1)}, ..., s_t^{(L)}\}\)。
  2. **动态拐点检测（CDID）**：对语义轨迹进行Savitzky-Golay平滑，计算曲率，选取曲率最大的层作为拐点 \(\tau\)（\(\delta=10\)避免浅层噪声）。
  3. **两个指标**：
     - **语义稳定性分数（SSS）**：拐点前各层语义分数的方差倒数（1 - 方差），衡量早期探索阶段的稳定性。
     - **收敛置信度分数（CCS）**：拐点后语义分数的平均斜率，衡量最终收敛的果断性。
  4. **Token级不确定性**：\(U_{\text{token}} = \alpha \cdot SSS + \beta \cdot CCS\)（默认\(\alpha=\beta=0.5\)）。
  5. **序列级不确定性**：利用最高熵注意力头（在验证集上选择）的注意力权重对token不确定性加权求和，得到序列级分数。
- **算法流程**（文字说明）：输入生成序列 → 获取每个token在所有层的隐藏状态 → 计算LSR轨迹 → CDID检测拐点 → 计算SSS和CCS → 线性组合得token级不确定性 → 注意力加权聚合得序列级不确定性。

## 3. 实验设计

- **数据集**：CoQA、NewsQA、SQuAD、Natural Questions（NQ）用于QA任务；GSM8K用于数学推理；Multi30K用于机器翻译。每个数据集随机采样1000个样本。
- **模型**：Qwen系列（1.5B、3B、7B）和Llama系列（1B、3B、8B），均为预训练模型，未微调。
- **基线方法**：Predictive Entropy (PE)、Length-Normalized PE (LN-PE)、Lexical Similarity (LS)、Semantic Entropy (SE)、Number of Semantic Clusters (NSC)、Shifting Attention to Relevance (SAR)。
- **评估指标**：主要使用AUROC（区分正确/错误生成）和PRR（预测可靠性率）；生成正确性用ROUGE-L、Exact Match、BERTScore-F1。

## 4. 资源与算力

- 文中**未明确说明**训练或推理所用的具体GPU型号、数量、时长。仅提供了执行时间对比（图7）：例如Qwen 7B模型上，采样基线耗时约25小时，本文方法约1小时（约25倍加速）。未提及硬件环境细节。

## 5. 实验数量与充分性

- **实验数量**：覆盖6个数据集×2个模型系列×多种参数规模，共约20+组（主实验表1+表2），以及消融研究（表3、表4）、相关性分析（表5）、效率对比（图7）和额外阈值分析（附录）。实验较为丰富。
- **充分性**：实验设计较全面，涵盖了多种任务、模型尺寸、评估指标，并对比了多个主流基线。消融实验验证了SSS和CCS的互补性及注意力聚合策略的有效性。但未覆盖其他模型架构（如GPT系列、Mistral），也未在分布外或对抗性样本上测试，存在一定局限性。

## 6. 主要结论与发现

- 所提方法在**所有模型和数据集**上显著优于现有基线，AUROC提升3~8个百分点，PRR提升更明显（例如NQ+Llama 8B上AUROC达83.67%，PRR达32.18%）。
- 方法在数学推理和机器翻译任务上也取得最佳AUROC（如GSM8K+Llama 8B: 71.43%）。
- 计算效率极高：单次前向传播，相比采样方法提速约25倍，适合实时应用。
- SSS和CCS捕获了不同的不确定性信号（早期波动与后期收敛），组合优于单一指标。
- 与语义熵（SE）的Pearson相关系数接近0，表明本文方法提供了正交的不确定性信息。

## 7. 优点

- **创新性**：首次将隐藏层动态演化用于无采样UQ，理论动机清晰（基于logit lens实证发现）。
- **高效性**：无需多次采样或外部API，显著降低计算开销。
- **可解释性**：SSS和CCS分别对应探索阶段的稳定性和决策阶段的果断性，物理意义明确。
- **通用性**：在问答、推理、翻译等多任务上表现一致，跨模型规模（1B~8B）稳健。
- **消融验证充分**：独立验证了每个组件的贡献。

## 8. 不足与局限

- **实验覆盖有限**：仅使用了Qwen和Llama两个模型家族，未测试其他架构（如GPT、Mistral、Gemini）；仅在6个数据集上进行，缺乏对抗性/分布外场景验证。
- **超参数选择**：SSS/CCS的权重\(\alpha,\beta\)默认等权，未讨论自适应调优；CDID中平滑窗口\(w=5\)和\(\delta=10\)为启发式选择，可能影响拐点检测鲁棒性。
- **适用场景**：需要访问模型内部隐藏状态，对完全黑盒模型（如仅提供API）不适用。
- **风险偏差**：假设内部动态与模型置信度直接相关，但在某些任务（如创造性生成）中该假设可能不成立；未分析模型校准风险。
- **资源信息缺失**：未公开硬件规格，难以复现效率对比。

（完）
