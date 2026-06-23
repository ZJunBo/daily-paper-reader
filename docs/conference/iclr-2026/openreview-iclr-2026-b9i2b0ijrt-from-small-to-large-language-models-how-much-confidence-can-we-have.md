---
title: "From small to large language models: How much confidence can we have?"
title_zh: 从小型到大型语言模型：我们能有多大的信心？
authors: "Raunak Agarwal, Markus A. Wenzel, Simon Baur, Jonas Zimmer, George Harvey, Jackie Ma"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=B9i2B0IjRT"
tags: ["query:luq"]
score: 8.0
evidence: 跨多种LLM的UQ方法综合比较
tldr: 论文系统比较了基于信息、一致性和自表述的三种不确定性量化方法，涵盖二十多种编码器与解码器语言模型，在医疗设备不良事件报告的多标签分类基准上评估。提供关于不同规模模型和微调范式的UQ实用指南。
source: ICLR-2026-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-b9i2b0ijrt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1289, \"height\": 925, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-b9i2b0ijrt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1455, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-b9i2b0ijrt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 771, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-b9i2b0ijrt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 645, \"height\": 522, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-b9i2b0ijrt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1415, \"height\": 956, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-b9i2b0ijrt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1456, \"height\": 1458, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-b9i2b0ijrt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1097, \"height\": 642, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-b9i2b0ijrt/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1350, \"height\": 215, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-b9i2b0ijrt/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1313, \"height\": 596, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-b9i2b0ijrt/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1296, \"height\": 441, \"label\": \"Table\"}]"
motivation: 不同规模模型的不确定性量化方法缺乏系统比较，需要实用指导。
method: 在统一基准上对比三类UQ方法，覆盖多种LLM和微调范式。
result: 揭示了不同模型和范式下UQ方法的相对优势。
conclusion: 为LLM不确定性量化实践提供了全面参照和建议。
---

## Abstract
In this paper, we provide novel insights into information-based, consistency-based and self-verbalized uncertainty quantification (UQ) for multi-label text classification across a range of recent language models on a new unsaturated benchmark of medical device adverse event reports with interdependent labels. We compare more than twenty encoder- and decoder-only language models across three paradigms: discriminative fine-tuning, generative fine-tuning, and few-shot in-context prompting (instruction-tuned and reasoning variants, local and API-accessible). UQ is performed using token-information measures, consistency under stochastic generation, and self-verbalized confidence, with utility assessed via selective prediction. We provide practical guidance on model selection, when fine-tuning is preferable to prompting, and which UQ signals are most effective for routing and human-in-the-loop triage. Our results reveal trade-offs across model types. Discriminatively fine-tuned decoders achieve the strongest head–tail accuracy while still offering solid uncertainty quantification (UQ). In contrast, generative fine-tuning provides the most reliable UQ overall. Reasoning models improve performance on extreme-tail labels but yield weak UQ. Finally, self-verbalized confidence proves unreliable as an indicator of model certainty.

---

## 论文详细总结（自动生成）

以下是基于给定论文《From small to large language models: How much confidence can we have?》的详细中文总结。

---

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLMs）在医疗、教育等高危场景广泛应用，但仅靠准确性不足以建立信任，不确定性量化（UQ）是关键。然而，不同规模模型、不同学习范式（判别式微调、生成式微调、少样本提示）下的UQ方法缺乏系统比较和实用指导。
- **整体含义**：论文旨在填补这一空白，通过构建一个不饱和的多标签文本分类基准（医疗设备不良事件报告），系统对比20多种语言模型在多种UQ方法上的表现，为从业者提供模型选择、微调 vs 提示选择、以及UQ信号选择的实际建议。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：在多标签分类任务上，联合评估预测性能与UQ质量，UQ分为三类：
  - **基于信息的UQ（U_info）**：从模型输出概率中提取指标，包括熵、平均对数概率、困惑度、最大标记对数概率、响应的不概率（1-∏πij）。
  - **基于一致性的UQ（U_cons）**：通过5次随机生成（温度=1）得到多个输出，计算Jaccard相似性矩阵，然后计算图拉普拉斯矩阵的特征值，U_cons = ∑max(0, 1-λk)。
  - **总UQ（U_total）**：U_total = U_info × U_cons，乘积组合。
  - **自表述UQ（U_self）**：直接提示模型输出置信度分数C_i，U_self = 1 - C_i。
- **判别式模型UQ**：对每个标签输出概率计算二元熵，U_info = [H(π₁), H(π₂), ..., H(π_C)]。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：
  - 来源：FDA医疗设备不良事件报告（open.fda.gov），2015-2025年数据。
  - 处理：使用IMDRF分层标签（1154个标签），去除罕见标签（<5实例），去重，HDBSCAN下采样，最终训练集298,825、验证集71,271、测试集118,177。进一步抽取测试子集10,288样本，确保每个标签至少出现5次。
  - 特点：标签长尾分布，层次化且相互依赖（图结构）。
- **对比模型**：
  - 判别式微调：Ettin编码器（150M/400M/1B）、Llama 3.2-1B/3B、Llama 3.1-8B。
  - 生成式微调：Ettin解码器（400M/1B）、Llama 3.2-1B/3B、Llama 3.1-8B/70B。
  - 少样本提示（10-shot，基于kNN检索）：Llama-3.1-8B/70B-Instruct、Qwen3（4B/30B/235B Instruct/Thinking）、Kimi K2、GPT-4.1、GPT-5、DeepSeek-R1等。
- **评估指标**：
  - 预测性能：Macro F1（分头/中/尾/极尾）、Jaccard分数。
  - UQ质量：预测拒绝率（PRR），计算方式为(不确定性AUC - 随机AUC) / (oracle AUC - 随机AUC)；以及不确定性与正确性的Spearman相关系数ρ。

## 4. 资源与算力

- 论文未明确说明所使用的GPU型号、数量和训练时长。
- 仅提及训练细节：判别式微调20轮，batch size 512；生成式微调4轮，batch size 64；使用AdamW优化器和余弦学习率衰减。
- 部分模型通过API访问（GPT-4.1、GPT-5），其余本地部署。算力需求未量化。

## 5. 实验数量与充分性

- **实验数量**：超过20种模型 × 三种范式，共约60+实验配置。此外还包括：
  - UQ方法对比：5种信息指标 × 一致性 × 自表述。
  - 消融实验：LoRA vs 全微调（表A.1），Base vs Instruct（表A.2），以及不同Uinfo方法比较（表2、表3）。
- **充分性评价**：实验覆盖了主流模型系列和规模，范式对比完整，UQ方法多样，评估指标合理。在单一数据集上进行了充分消融，但未在其他数据集上验证，存在领域局限性。
- **客观公平性**：统一的数据预处理、标签体系、评估流程。但测试集时间窗口（2024年7月-2025年6月）可能部分超出模型知识截止日期，论文讨论了此问题并尽量确保无污染。

## 6. 论文的主要结论与发现

1. **预测性能**：判别式微调的Llama-3.1-8B-Base获得最高Macro F1（0.54），在头、中、尾类上表现最佳。推理模型在极尾类上表现突出（GPT-5极尾F1=0.34），但头类性能低于最佳微调模型。
2. **UQ质量**：生成式微调整体UQ最可靠（PRR最高达0.70，ρ=-0.46）。判别式微调次之，提示指令模型第三，推理模型最差（PRR≤0.36，ρ接近0）。
3. **UQ方法比较**：信息类指标之间PRR差异很小；加上一致性U_total只带来微幅提升（≤0.03 PRR），但计算成本增加约6倍。自表述UQ几乎无效（PRR≈0）。
4. **规模不单调**：UQ质量并不随模型大小单调提升，中等规模模型（如Llama-3.2-3B生成式微调）可能优于更大模型。
5. **微调优于提示**：对于可靠UQ，微调（尤其是生成式）远优于少样本提示。提示式推理模型UQ极差。
6. **不可用模型**：不提供对数概率的闭源模型（如GPT-5）无法进行有效的概率基UQ，不适于PRR校准。

## 7. 优点：方法或实验设计上的亮点

- **新基准**：构建了不饱和、去污染、带层次标签的多标签数据集，避免饱和基准和训练数据泄露问题。
- **系统全面**：同时对比三种学习范式、多种模型规模、多种UQ方法，且在同一任务上公平比较。
- **实用导向**：提供具体选择指南（何时微调、如何选择UQ指标），并评估了UQ对样本路由和人工审核的效用。
- **方法创新**：提出了结合信息与一致性的U_total，并系统比较其与单独信息的权衡。
- **严谨分析**：使用预测拒绝率（PRR）而非简单相关性，能更实际地评估UQ在筛选不确定样本时的效果。

## 8. 不足与局限

- **单一数据集**：所有实验仅在一个医疗设备报告数据集上进行，领域泛化性有待验证。不同标签结构、领域（如法律、临床编码）可能改变结论。
- **未考虑其他信任维度**：仅关注UQ，未涉及可解释性、公平性、鲁棒性等。
- **推理模型UQ差但未深入改进**：论文指出推理模型UQ弱，但未提出解决方案，仅作为未来方向。
- **算力资源未报告**：缺少训练和推理的详细开销，不利于实际部署成本评估。
- **时间性能未涉及**：未比较不同UQ方法以及不同范式在延迟上的差异。
- **自表述UQ评估相对简单**：仅以一个简单提示收集置信度，未探索更复杂的校准提示策略。
- **数据集偏差风险**：FDA报告主要来自美国，可能不反映全球分布；标签映射和向上传播可能引入噪声。

（完）
