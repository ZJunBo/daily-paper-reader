---
title: Modeling Uncertainty Trends for Timely Retrieval in Dynamic RAG
title_zh: 建模不确定性趋势以实现在动态RAG中的及时检索
authors: "Bo Li, Tian Tian, Zhenghua Xu, Hao Cheng, Shikun Zhang, Wei Ye"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40418/44379"
tags: ["query:luq"]
score: 8.0
evidence: 动态RAG中令牌级不确定性建模以确定检索时机
tldr: 动态RAG中检索时机选择是关键挑战，现有基于低置信度触发的方法往往延迟干预。本文提出无训练的熵趋势约束(ETC)方法，通过熵序列的一阶和二阶差分检测不确定性趋势，实现更早更精确的检索。在六个QA数据集上验证了有效性。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 动态RAG中检索时机选择不当导致错误传播。
method: 提出ETC方法，利用熵序列差分检测不确定性趋势。
result: 在多个QA数据集上实现了更早更精确的检索。
conclusion: ETC为动态RAG检索时机提供了一种有效的训练自由方法。
---

## Abstract
Dynamic retrieval-augmented generation (RAG) allows large language models (LLMs) to fetch external knowledge on demand, offering greater adaptability than static RAG. A central challenge in this setting lies in determining the optimal timing for retrieval. Existing methods often trigger retrieval based on low token-level confidence, which may lead to delayed intervention after errors have already propagated. We introduce Entropy-Trend Constraint (ETC), a training-free method that determines optimal retrieval timing by modeling the dynamics of token-level uncertainty. Specifically, ETC utilizes first- and second-order differences of the entropy sequence to detect emerging uncertainty trends, enabling earlier and more precise retrieval. Experiments on six QA benchmarks with three LLM backbones demonstrate that ETC consistently outperforms strong baselines while reducing retrieval frequency. ETC is particularly effective in domain-specific scenarios, exhibiting robust generalization capabilities. Ablation studies and qualitative analyses further confirm that trend-aware uncertainty modeling yields more effective retrieval timing. The method is plug-and-play, model-agnostic, and readily integrable into existing decoding pipelines. Implementation code is included in the supplementary materials.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：动态检索增强生成（Dynamic RAG）中，如何确定最优的检索时机是一个关键挑战。现有方法（如FLARE、DRAGIN）通常基于单个生成token的置信度（confidence）来触发检索，但这类“反应式”机制往往导致**延迟检索**（delayed retrieval）——即在错误已经传播之后才进行检索，无法有效阻止事实错误。
- **背景**：静态RAG（仅在生成开始时检索一次）可能因无关或冗余上下文引入噪声；动态RAG按需检索能更好平衡信息性与效率。但基于单token置信度的触发策略不够敏感，需要更鲁棒的不确定性度量。
- **整体含义**：作者提出应建模整个生成过程中的**不确定性趋势**（uncertainty trends），而不是依赖孤立的单token置信度，以实现更早、更精确的检索，从而提升生成质量并减少检索频率。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：利用token级熵（entropy）序列的一阶和二阶差分来检测不确定性的快速变化，从而在模型进入不稳定预测阶段之前触发检索。
- **关键技术细节**：
  - 对每个生成token计算预测分布的熵 \( H_i = -\sum_v p_i(v) \log p_i(v) \)。
  - 构建熵序列 \( H = \{H_1, H_2, ..., H_n\} \)。
  - 计算一阶差分 \( \Delta H_i = H_{i+1} - H_i \) 反映相邻熵的变化。
  - 计算二阶差分 \( \Delta^2 H_i = \Delta H_{i+1} - \Delta H_i = H_{i+2} - 2H_{i+1} + H_i \)，用于捕捉熵变化的加速度，对置信度快速下降更敏感。
  - **动态平滑方法**：为减少离群熵值导致的冗余检索，对二阶差分进行加权平滑。当前权重 \( w_t \) 根据历史二阶差分的期望与当前值的偏离程度计算（公式(10)-(11)），使得异常值获得更低权重，得到平滑后的 \( \Delta^2 \hat{H}_t \)。
  - 当 \( |\Delta^2 \hat{H}_t| \ge \alpha \) 时触发检索（\(\alpha\) 为阈值，在验证集上调优）。
  - 查询构建采用DRAGIN的方法（基于自注意力分数选择top‑n token）。
- **算法流程**（文字说明）：
  1. 逐个生成token，每生成一个token计算其熵。
  2. 实时维护熵序列，计算其二阶差分（及平滑版本）。
  3. 当平滑二阶差分的绝对值超过预设阈值α时，构造查询并执行检索，将检索到的文档与原始查询、已生成文本拼接后继续生成。
  4. 否则继续生成下一个token，重复上述过程。

## 3. 实验设计
- **数据集**（6个QA基准）：
  - 通用领域：2WikiMultihopQA（多跳）、HotpotQA（多跳）、StrategyQA（常识）、IIRC（阅读理解）。
  - 生物医学领域：BioASQ、PubMedQA（评估领域专长泛化能力）。
- **评估指标**：EM（精确匹配）、F1、Accuracy（根据数据集惯例，见表1）。
- **对比方法**：
  - 无检索（w/o RAG）
  - 单次检索（Single RAG）
  - 固定间隔检索（In-Context RALM：每n个token；IRCoT：每句话）
  - 基于置信度的动态检索（FLARE、DRAGIN）
  - ETC的消融变体：ETC 1st（仅一阶差分）、ETC w/o smoothing（无动态平滑）、ETC fixed（固定权重平滑）
- **骨干LLM**：LLaMA2-7B、LLaMA3-8B、Vicuna-13B（另在附录报告LLaMA2-13B结果）。检索器使用BM25，外部知识库为Wikipedia。每次检索取3篇文档。生成采用chain-of-thought（CoT）模式。

## 4. 资源与算力
- **未明确说明**：论文未提及训练（因为是训练自由方法）或推理时使用的GPU型号、数量、训练时长等算力资源。仅提到使用BM25检索器（高效）、LLM为开源模型。因此无法具体量化算力消耗。

## 5. 实验数量与充分性
- **实验数量**：
  - 主实验：6个数据集 × 3种LLM × 7种方法（含基线），共126组结果（表2）。
  - 域特定实验：2个生物医学数据集（表3）。
  - 消融实验：4种ETC变体在4个通用数据集上的对比（表4）。
  - 检索效率分析：平均检索次数对比（表5）。
  - 人工标注延迟检索与冗余检索比率（100个样本，表6）。
  - 检索时机热力图与熵分布可视化（图3）。
  - 定性案例研究（图4）。
  - GPT-4o胜率评估（图2，每个数据集200样本×4个数据集）。
- **充分性与公平性**：
  - 覆盖多领域、多模型规模，对比了多种训练自由RAG方法，消融实验验证各组件贡献。
  - 采用与以往工作一致的设置（LLM、prompt、检索器等），结果进行了t检验（p<0.05），确认统计显著性。
  - 人工标注和GPT-4o评估增强了结果的可信度。
  - 主要不足：未与其他训练方法（如基于训练的检索时机学习）对比；仅使用BM25单一检索器，未探索稠密检索等。

## 6. 主要结论与发现
- ETC在所有设置下一致优于最强基线（DRAGIN等），平均得分提升5.9%~12.1%，同时检索次数显著减少（表2、表5）。
- 在域特定（生物医学）场景中优势更明显（BioASQ准确率提升30.7%）。
- ETC有效缓解了延迟检索（延迟比率从DRAGIN的33%降至22%）和冗余检索（冗余比率从95%降至79%）。
- 消融实验证实二阶差分比一阶差分更有效，动态平滑减少冗余检索。
- GPT-4o评估显示ETC的答案质量在多数情况下等于或优于DRAGIN。
- 模型无关、即插即用，易于集成到现有解码流程。

## 7. 优点
- **方法创新**：首次将熵序列的二阶差分（不确定性趋势加速度）用于动态RAG检索时机决策，比单token置信度更灵敏、更早。
- **训练自由**：无需任何训练或微调，计算开销小，通用性强。
- **动态平滑机制**：有效抑制离群值导致的误触发，提高检索效率。
- **实验全面**：跨多模型、多领域、多基线，包含消融、人工评估、GPT-4o评估、可视化分析，论证充分。
- **实用性**：即插即用，代码开源，易于复现和部署。

## 8. 不足与局限
- **实验覆盖**：仅使用BM25检索器，未探讨与稠密检索（如DPR、ColBERT）的兼容性；未对比训练型动态RAG方法（如基于强化学习的检索时机）。
- **偏差风险**：阈值α在验证集上调优，可能对数据分布敏感；人工标注仅100样本，统计稳定性有限。
- **应用限制**：方法依赖熵计算和二阶差分，对于极短生成（如单token回答）可能不够有效；在解码过程中需要实时维护熵序列，增加少量计算延迟（但作者声称轻量）。
- **未见成本分析**：未报告具体推理时间或计算资源消耗，难以评估实际部署性价比。
- **泛化性**：仅在QA任务上验证，未覆盖对话、摘要等更广泛RAG场景。

（完）
