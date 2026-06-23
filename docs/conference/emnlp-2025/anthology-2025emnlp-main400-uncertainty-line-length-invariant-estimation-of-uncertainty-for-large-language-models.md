---
title: "UNCERTAINTY-LINE: Length-Invariant Estimation of Uncertainty for Large Language Models"
title_zh: UNCERTAINTY-LINE：大型语言模型长度不变的不确定性估计
authors: "Roman Vashurin, Maiya Goloburda, Preslav Nakov, Maxim Panov"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.emnlp-main.400.pdf"
tags: ["query:luq"]
score: 7.0
evidence: 针对LLM的长度不变不确定性估计
tldr: 论文发现现有基于token概率的LLM不确定性量化方法存在输出长度偏差，即使长度归一化也无法消除。为此提出UNCERTAINTY-LINE，通过回归不确定性分数与输出长度实现去偏。实验表明该方法在多个任务上有效消除了长度影响，提高了UQ的可靠性。
source: EMNLP-2025-Main
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.400/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1641, \"height\": 1014, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.400/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1645, \"height\": 508, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.400/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1656, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.400/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 787, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.400/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1631, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.400/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1619, \"height\": 1606, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.400/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1614, \"height\": 1590, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.400/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1616, \"height\": 1590, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.400/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1590, \"height\": 1029, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.400/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1550, \"height\": 2257, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.400/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1552, \"height\": 2260, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.400/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1550, \"height\": 1818, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 790, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1645, \"height\": 598, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1539, \"height\": 581, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1010, \"height\": 1212, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 404, \"height\": 348, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 417, \"height\": 347, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1573, \"height\": 1031, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1570, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1473, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1286, \"height\": 2283, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1286, \"height\": 2290, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1285, \"height\": 2282, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 585, \"height\": 1490, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1304, \"height\": 1339, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1302, \"height\": 1339, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1302, \"height\": 1339, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.400/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 696, \"height\": 1801, \"label\": \"Table\"}]"
motivation: 现有UQ方法受输出长度偏差影响，导致估计不可靠。
method: 提出UNCERTAINTY-LINE，通过回归模型将不确定性分数与输出长度解耦，实现去偏。
result: 在多个LLM生成任务上，该方法消除了长度偏差，且不确定性估计与事实准确性更一致。
conclusion: 提供了一种简单有效的去偏方法，提升了LLM不确定性量化的公平性和准确性。
---

## Abstract
Large Language Models (LLMs) have become indispensable tools across various applications, making it more important than ever to ensure the quality and the trustworthiness of their outputs. This has led to growing interest in uncertainty quantification (UQ) methods for assessing the reliability of LLM outputs. Many existing UQ techniques rely on token probabilities, which inadvertently introduces a bias with respect to the length of the output. While some methods attempt to account for this, we demonstrate that such biases persist even in length-normalized approaches. To address the problem, here we propose UNCERTAINTY-LINE (Length-INvariant Estimation), a simple debiasing procedure that regresses uncertainty scores on output length and uses the residuals as corrected, length-invariant estimates. Our method is post-hoc, model-agnostic, and applicable to a range of UQ measures. Through extensive evaluation on machine translation, summarization, and question-answering tasks, we demonstrate that UNCERTAINTY-LINE consistently improves over even nominally length-normalized UQ methods uncertainty estimates across multiple metrics and models. We release our code publicly at https://github.com/stat-ml/uncertainty-line

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 核心问题与整体含义（研究动机和背景）
- **背景**：大型语言模型（LLMs）在各类应用中广泛使用，但其输出可能包含错误或误导信息。不确定性量化（UQ）旨在评估模型输出的可靠性，是保障LLM可信度的关键。
- **核心问题**：现有UQ方法多依赖token概率（如联合概率、困惑度、平均token熵等），但这些指标与输出长度存在系统性偏差。即使采用长度归一化（如平均log概率），偏差仍然存在。这导致UQ分数不能真实反映生成质量——长输出被误判为更不确定（对MSP）或更确定（对PPL/MTE），从而影响基于不确定性的拒绝策略的有效性。
- **研究意义**：提出一种轻量、模型无关的后处理方法，消除长度偏差，提升UQ的可靠性和公平性。

### 2. 方法论
- **核心思想**：通过回归模型拟合UQ分数与输出长度之间的系统性趋势，用残差作为去偏后的不确定性估计。
- **关键技术细节**：
  - **无监督版本（适用于质量-长度不相关任务，如机器翻译）**：
    - 在训练集上拟合线性回归：`u_hat(y) = α|y| + β`，其中`u(y)`为原始UQ分数，`|y|`为输出长度。
    - 去偏后分数：`u_deb(y) = u(y) - u_hat(y)`（即残差）。
  - **监督版本（适用于质量-长度相关任务，如摘要、数学推理）**：
    - 额外拟合质量-长度回归：`q_hat(y) = δ|y| + γ`，其中`q(y)`为负质量分数（高质量对应低不确定性）。
    - 最终去偏：`u_deb(y) = u(y) - u_hat(y) - q_hat(y)`，保留与质量相关的长度趋势，仅去除虚假偏差。
  - **回归模型选择**：基于实证观察（图1显示线性趋势显著），且实验表明二阶/三阶多项式未带来一致改进，因此采用线性模型，避免过拟合。
- **算法流程**（文字说明）：
  1. 计算序列y的原始不确定性分数`u(y)`。
  2. 在少量无标签数据上（或带标签数据）拟合`u-hat`回归。
  3. 在测试时，用拟合的回归方程预测`u_hat`，相减得残差作为最终不确定性。
  4. 若任务质量-长度相关，额外拟合`q_hat`回归，并在残差中加上`-q_hat`以保留有效趋势。

### 3. 实验设计
- **数据集与场景**：
  - **机器翻译**：WMT14（Cs-En, De-En, Ru-En, Fr-En）和WMT19（De-En, Fi-En, Lt-En, Ru-En），共8个语言对。
  - **抽象摘要**：XSum（BBC文章单句摘要）。
  - **数学推理**：GSM8K（小学级数学应用题）。
- **基准（Baseline）**：原始未去偏的UQ方法（Base） vs. 应用UNCERTAINTY-LINE后的方法（LINE）。
- **对比方法（UQ度量）**：共7种：MSP、PPL、MTE、MCSE、MCNSE、LSRL、TokenSAR。涵盖了基于似然和基于样本一致性的方法。
- **评估指标**：Prediction-Rejection Ratio (PRR)，衡量不确定性排序与真实质量排序的一致性（相比于随机和最优排序）。
- **质量度量**：翻译用Comet WMT22、XComet XXL、MetricX XXL；摘要用AlignScore；数学推理用Accuracy。
- **模型**：Llama 3.1 8B、Gemma 2 9B、EuroLLM 9B（仅用于翻译）。

### 4. 资源与算力
- **论文未明确说明所使用的GPU型号、数量、训练时长等具体算力信息**。但从实验规模（3个模型，8+1+1个数据集，7种UQ度量，多次回归拟合）可推断计算需求较大，但作者未提供细节。

### 5. 实验数量与充分性
- **实验数量**：共包含：
  - 翻译任务：3个模型 × 8个语言对 × 7种UQ度量 × 两种设置（Base/LINE）= 336组PRR结果（表10-12）。
  - 摘要和数学推理：2个模型 × 2个任务 × 7种UQ度量 × 2种设置 = 56组结果（表13）。
  - 消融实验：多项式阶数对比（D.1）、质量标签样本量缩减（D.2）。
- **充分性与客观性**：
  - 实验覆盖三种不同类型的生成任务（翻译、摘要、推理），长度偏差表现不同。
  - 使用的模型架构多样（LLaMA、Gemma、EuroLLM），UQ度量全面。
  - 评价指标PRR是公认的UQ排序评估方法。
  - 消融实验验证了线性假设的合理性及低标注样本下的鲁棒性。
  - **优点**：比较全面，统计显著性和均值报告完整。
  - **不足**：未在更大模型（如70B+）或更多任务（如对话、代码生成）上验证；未与最新UQ方法（如语义熵、言语置信度）进行直接比较。

### 6. 主要结论与发现
- **长度偏差普遍存在**：即使经长度归一化的UQ方法（PPL、MTE）仍与长度显著相关（图1、表7-9）。
- **质量度量在翻译中长度无关，在摘要和推理中长度相关**（图2、3）。
- **UNCERTAINTY-LINE显著提升UQ的排序性能**：在翻译任务上，平均PRR提升0.02~0.18（表3）；在数学推理和摘要上同样有增益。
- **长度敏感的UQ方法（MSP、PPL、MTE）改善最大**；长度不敏感的方法（LSRL）改进较小。
- **无需大量标注数据**：监督版本仅需500个样本即可有效恢复质量-长度趋势（表17）。
- **线性校正足够**：多项式校正未带来一致提升（表14-16）。

### 7. 优点
- **简单有效**：仅需拟合线性回归，轻量、模型无关、后处理，易于集成到现有UQ框架。
- **可解释性强**：残差去偏直观，移除明显趋势。
- **适用范围广**：既适用于质量-长度无关任务（纯去偏），也适用于相关任务（保留有效趋势）。
- **实验充分**：涵盖多种任务、模型、UQ度量，并做了必要的消融。
- **公开代码**：基于LM-Polygraph库，便于复现和应用。

### 8. 不足与局限
- **线性假设可能不足**：对于复杂任务（如多步推理中不确定性随推理阶段变化），线性校正可能过于粗糙。虽然多项式实验未显示优势，但非线性关系可能存在于其他场景。
- **监督版本需要少量质量标签**：虽然仅需500样本，但在零标注场景下无法应用，且质量度量本身可能存在偏差。
- **未覆盖所有UQ方法**：未与基于语义一致性的UQ（如语义熵、言语置信度）对比，而后者可能天然长度不敏感。
- **评估指标单一**：仅用PRR，缺乏校准性（如ECE）或最优拒绝率等分析。
- **模型范围有限**：仅使用8B-9B模型，未在更大模型（如70B、8x7B）或不同架构（如编码器-解码器）上验证。
- **未探讨潜在风险**：去偏后UQ可能降低某些长序列的区分度，需谨慎用于拒绝策略。

（完）
