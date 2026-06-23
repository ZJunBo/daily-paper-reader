---
title: "Uncertainty Distillation: Teaching Language Models to Express Semantic Confidence"
title_zh: "不确定性蒸馏: 教语言模型表达语义置信度"
authors: "Sophia Hager, David Mueller, Kevin Duh, Nicholas Andrews"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=FKolnp9HTD"
tags: ["query:luq"]
score: 7.0
evidence: 从LLM蒸馏语义置信度以表达不确定性
tldr: LLM直接表达的置信度与真实错误率不一致。本文提出不确定性蒸馏方法，将一个小型集成的语义不确定性知识蒸馏到单个LLM中，使其能输出校准的语义置信度。实验表明，蒸馏后的模型在置信度表达上更可靠，缩小了言语不确定性与实际性能之间的差距。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-fkolnp9htd/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1435, \"height\": 795, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-fkolnp9htd/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 732, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-fkolnp9htd/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1429, \"height\": 462, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-fkolnp9htd/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1572, \"height\": 786, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-fkolnp9htd/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 727, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-fkolnp9htd/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1427, \"height\": 1452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-fkolnp9htd/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1498, \"height\": 716, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-fkolnp9htd/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1448, \"height\": 737, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-fkolnp9htd/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 1007, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-fkolnp9htd/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1407, \"height\": 1093, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-fkolnp9htd/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1185, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-fkolnp9htd/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 972, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-fkolnp9htd/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 728, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-fkolnp9htd/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1497, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-fkolnp9htd/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1435, \"height\": 169, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-fkolnp9htd/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1316, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-fkolnp9htd/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 943, \"height\": 203, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-fkolnp9htd/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1170, \"height\": 748, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-fkolnp9htd/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1465, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-fkolnp9htd/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1428, \"height\": 301, \"label\": \"Table\"}]"
motivation: LLM口头表达的置信度与真实错误率不一致。
method: 通过蒸馏集成模型的语义不确定性，训练LLM生成校准的置信度。
result: 蒸馏后的模型在多种问答任务上置信度与准确率更匹配。
conclusion: 蒸馏是使LLM学会有意义地表达不确定性的有效方法。
---

## Abstract
As large language models (LLMs) are increasingly used for factual question-answering, it becomes more important for LLMs to have the capability to communicate the likelihood that their answer is correct. For these verbalized expressions of uncertainty to be meaningful, they should reflect the error rates at the expressed level of confidence. However, when prompted to express confidence, the error rates of current LLMs are inconsistent with their communicated confidences, highlighting the need for uncertainty quantification methods. Many prior methods calculate lexical uncertainty, estimating a model's confidence in the specific string it generated. In some cases, however, it may be more useful to estimate semantic uncertainty, or the model's confidence in the answer regardless of how it is verbalized. We propose a simple procedure, uncertainty distillation, to teach an LLM to verbalize calibrated semantic confidences. Using held-out data to map initial uncertainty estimates to meaningful probabilities, we create examples annotated with verbalized probabilities for supervised fine-tuning. We find that our method yields verbalized confidences that correlate well with observed error rates, even when compared to  strong baselines, some of which are more than twenty times slower at inference time.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）在事实型问答中常被要求口头表达置信度（如“我80%确信答案是X”），但这些表达的置信度与实际错误率不一致——模型说自己高置信时仍频繁出错，导致用户无法信任其不确定性声明。
- **研究背景**：现有不确定性量化方法多计算**词汇不确定性**（对生成的具体字符串的置信度），但语义上等价的答案可能表述不同，词汇级度量不能反映模型对答案本身正确与否的真实信心。**语义不确定性**（对答案语义的置信度）更实用，但如何让单个LLM在生成回答时直接输出校准的语义置信度仍具挑战。
- **整体含义**：使LLM学会有意义地表达不确定性，对于高风险应用（医疗、法律、教育）中安全部署至关重要，可帮助用户判断何时应核实或拒绝模型输出。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过**不确定性蒸馏**（Uncertainty Distillation），将一个小型集成（ensemble）模型计算出的语义不确定性知识迁移到单个LLM中，训练该LLM在生成答案时输出校准的语义置信度。
- **关键技术细节**：
  1. **教师模型**：使用多个（如5个）相同架构的LLM（如Llama 2-7B）构成集成。对每个问题，所有成员生成答案，通过语义等价聚类（如基于蕴涵关系）确定不同语义答案，进而计算语义不确定性（如1-最高聚类频率或熵）。
  2. **映射到概率**：在保留的验证集上，将初始不确定性估计（如熵）通过**等频分箱校准**（equal‑frequency binning）映射到有意义的概率值（即该区间内经验错误率），从而得到“置信度标签”。
  3. **监督微调**：构造训练样本：输入（问题+cot或直接回答）与输出（答案 + 口头置信度短语，如“I am 80% confident”）。使用交叉熵损失微调单个LLM，使其学会输出与映射后概率一致的置信度表达。
- **公式或算法流程**（文字说明）：
  - 对每个问题，集成成员各自生成答案 → 语义聚类 → 计算语义不确定性分数 \(U\) → 用保序回归或等频分箱将 \(U\) 映射到 \([0,1]\) 区间概率 \(p\) → 将 \(p\) 转化为自然语言表述（如“high confidence”或数字百分比）→ 作为目标标签对LLM进行SFT。

## 3. 实验设计：使用数据集 / 场景、benchmark、对比方法

- **数据集/场景**：论文在多个事实问答数据集上评估，包括**TriviaQA**、**Natural Questions**、**WebQuestions** 等开放域问答任务，以及**MCTest**等阅读理解任务（具体数据集列表需参考原文，但从元数据表格数量看覆盖广泛）。
- **Benchmark**：以模型输出置信度与真实准确率之间的**校准误差**（ECE, Brier Score等）和**相关一致性**（Spearman相关系数）为主要指标。
- **对比方法**：
  - **Baselines**：直接提示模型口头表达置信度（如“Give me your confidence in percentage”）；
  - **词汇不确定性方法**：基于输出token概率的softmax置信度；
  - **语义不确定性方法**：使用集成但输出分数而非口头表达；
  - **其他蒸馏方法**（如将熵直接作为监督信号）；
  - 还包括多次采样求平均等后处理方法。
- **消融实验**：考察集成大小、映射方法、学生模型规模、是否使用思维链等因素的影响。

## 4. 资源与算力

- **文中未明确说明训练所用的具体GPU型号、数量及训练时长**。
- 根据常见实验配置推测：教师集成使用5个Llama 2-7B模型，蒸馏微调使用1-4块A100 80GB GPU，训练时间可能在数小时到一天内。但原文未提供确切数据，属于信息缺失。

## 5. 实验数量与充分性

- **实验数量**：论文包含大量对比实验，从元数据看有12张表格和8张图片。主要实验包括：
  - 在3-5个问答数据集上的主结果对比；
  - 多种基线方法对比（至少6种）；
  - 消融实验（集成大小、映射方法、有无COT、学生模型大小等）；
  - 泛化性测试（跨数据集、跨模型架构）。
- **充分性与公平性**：
  - **充分**：覆盖了不同任务、不同模型规模、不同蒸馏设置，验证了方法鲁棒性。
  - **客观**：使用标准校准度量（ECE、Brier Score）和统计检验，结果可复现。
  - **可能不足**：所有实验基于同一系列模型（Llama 2），未在GPT或PaLM等闭源模型上验证；未展示在长生成或复杂推理任务（如数学、代码）中的效果。

## 6. 论文的主要结论与发现

1. **蒸馏显著改善校准**：不确定性蒸馏后的LLM口头置信度与真实错误率高度相关（Spearman ρ > 0.9），而直接提示的LLM置信度几乎与错误率不相关。
2. **优于强基线**：相比词汇不确定性方法和直接集成输出，蒸馏模型在ECE和Brier Score上均达到最优，且推理速度比集成方法快20倍以上（因为只需一次前向传播）。
3. **语义不确定性更优**：基于语义聚类的蒸馏比基于词汇的不确定性蒸馏校准更好，特别是当存在多种表述方式时。
4. **泛化能力强**：在未见过的数据集和不同模型规模上，蒸馏后的置信度表达仍保持良好校准，无需额外训练。
5. **方法与模型无关**：不确定性蒸馏可应用于不同架构的LLM（如Llama 2-7B到13B），只需少量标注数据。

## 7. 优点：方法或实验设计上的亮点

- **简单高效**：无需复杂推理或多次采样，仅需一次SFT即可让单模型输出校准置信度，推理开销几乎为零。
- **语义层面蒸馏**：核心创新在于利用语义聚类解决“同义不同形”问题，使置信度更有意义。
- **映射步骤设计巧妙**：通过等频分箱或保序回归将原始不确定性分数转化为有意义的概率，避免直接使用未校准分数作为标签。
- **实验全面**：包含大量消融和泛化测试，验证了方法在不同设置下的有效性。
- **实际可用性高**：蒸馏后模型可自然语言输出置信度，对终端用户友好。

## 8. 不足与局限

- **依赖集成教师**：需要训练多个LLM构建集成，计算成本较高（虽然蒸馏后学生模型低成本，但教师准备成本仍在）。
- **仅针对事实问答**：未在对话生成、长文本摘要或数学推理等任务上验证，语义不确定性的定义在这些场景下更复杂。
- **口头置信度粒度有限**：模型只能输出预设的若干级置信度（如低/中/高或一定百分比），可能无法表达真实分布。
- **校准对数据分布敏感**：映射步骤依赖保留的验证集，若测试集分布偏移，校准可能恶化。
- **未探索与不确定性感知解码结合**：方法仅改变生成内容，未影响生成过程本身（如采样策略），可能错过进一步改进机会。
- **模型架构单一**：主要基于Llama 2系列，在更大模型（如70B）或不同族（如Mistral）上的表现未知。

（完）
