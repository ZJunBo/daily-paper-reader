---
title: Uncertainty Quantification via Reasoning–Explanation Symmetry in LLMs
title_zh: 通过推理-解释对称性量化大语言模型的不确定性
authors: "Guanran Luo, Wentao Qiu, Zhongquan Jian, Meihong Wang, Qingqiang Wu"
date: 2025-09-12
pdf: "https://openreview.net/pdf?id=ExobfZ35x1"
tags: ["query:luq"]
score: 9.0
evidence: 提出推理-解释对称性用于不确定性量化
tldr: 针对现有基于跨输出一致性的不确定性量化方法需要多次采样的效率问题，论文提出推理-解释对称性（RES）方法。该方法利用LLM对可靠答案应具有一致正向推理和反向解释路径的假设，通过双向自然语言推理评估对称性来量化不确定性，无需多次采样。实验表明RES在降低计算成本的同时保持高可靠性。
source: ICLR-2026-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-exobfz35x1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1455, \"height\": 287, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-exobfz35x1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1463, \"height\": 301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-exobfz35x1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1076, \"height\": 691, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-exobfz35x1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 531, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-exobfz35x1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1483, \"height\": 626, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-exobfz35x1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1457, \"height\": 469, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-exobfz35x1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1461, \"height\": 711, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-exobfz35x1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1461, \"height\": 678, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-exobfz35x1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1452, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-exobfz35x1/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 835, \"height\": 199, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-exobfz35x1/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1449, \"height\": 614, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-exobfz35x1/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 741, \"height\": 284, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-exobfz35x1/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1120, \"height\": 676, \"label\": \"Table\"}]"
motivation: 现有UQ方法需多次采样，计算成本高，需要更高效的基于单次输出的不确定性度量。
method: 提出推理-解释对称性（RES），利用正向推理和反向解释路径的一致性，通过双向NLI评估不确定性。
result: RES在无需多次采样下有效量化不确定性，在多种LLM和问答任务上表现优异。
conclusion: 推理-解释对称性为高效UQ提供了新范式，平衡了效率与可靠性。
---

## Abstract
Uncertainty quantification (UQ) for large language model (LLM) outputs has attracted increasing attention, as it is crucial for hallucination detection and selective generation; however, existing semantic methods based on cross-output consistency require multiple sampling and thus incur additional cost. We hypothesize that, for reliable answers, LLMs exhibit consistent forward reasoning and backward explanation paths. Building on this, we propose Reasoning--Explanation Symmetry (RES) to quantify uncertainty from the answer itself without multiple sampling: for each question, we first generate structured reasoning and an answer, then condition on the answer to generate a structured explanation; bidirectional natural language inference (NLI) assesses the semantic entailment between the two to construct a symmetry score. RES yields more accurate estimates with small sampling counts and offers stronger interpretability. We evaluate RES on six datasets for both uncertainty quantification and best-answer selection, and the results demonstrate significant advantages on complex reasoning tasks.

---

## 论文详细总结（自动生成）

以下是基于论文《Uncertainty Quantification via Reasoning–Explanation Symmetry in LLMs》的详细中文总结：

## 论文核心问题与整体含义（研究动机和背景）

- **研究动机**：现有的大语言模型（LLM）不确定性量化（UQ）方法主要依赖跨输出一致性（如语义熵），需要多次采样，计算成本高且不能为单个输出提供可靠的不确定性分数。概率方法（如熵、置信度）容易过自信。因此，需要一种更高效、可解释的UQ方法。
- **核心问题**：能否不通过多次采样比较，而是直接通过单个输出的内部一致性来判断其可靠性？
- **整体含义**：构建一个基于“正向推理”与“反向解释”对称性的UQ框架，以降低计算开销并提升解释性，适用于资源受限或黑盒场景。

## 方法论：核心思想、关键技术细节

- **核心思想**：对于可靠答案，LLM的推理路径（reasoning）与基于该答案生成的解释路径（explanation）应在语义上相互蕴含（双向对称）；不可靠答案往往出现矛盾或不一致。
- **技术流程**：
  1. **结构化推理采样**：对每个问题，使用结构化提示（Premise/Evidence、Reasoning、Conclusion三部分）引导LLM生成推理文本，并使用温度采样（k=3）获得多样候选，从中提取答案（通过 `<final>` 标签）。
  2. **配对解释生成**：对每个候选答案，用新提示（仅含问题+答案）生成结构化解释（Premise/Evidence、Explanation、Conclusion），要求遵循与推理相同的结构。
  3. **对称性评分**：使用预训练NLI模型（RoBERTa-large-MNLI）计算双向蕴含概率：
     - 前向蕴含概率：\( e_{i,\text{fwd}} = \frac{1}{3} \sum_{j} P(E_j|R_j)_{\text{entail}} \)
     - 后向蕴含概率：\( e_{i,\text{bwd}} = \frac{1}{3} \sum_{j} P(R_j|E_j)_{\text{entail}} \)
     - 聚合分数：min（最弱链）、mean（平均）、penalized（mean − λ·mean contradiction），其中λ=1.2。
  4. **输出**：分数越高表示对称性越强，不确定性越低，答案越可靠。可用于UQ（AUROC）或最佳答案选择（TOP1-AUC）。

## 实验设计：数据集、场景、基准与方法对比

- **数据集（6个）**：
  - MultiRC（多句阅读理解，开放书）
  - BBH – Date Understanding（日期计算，封闭书）
  - BBH – Multistep Arithmetic（多步算术，封闭书）
  - StrategyQA（常识推理，封闭书）
  - TriviaQA（去除文档，封闭书）
  - CoQA（对话问答，开放书）
- **任务**：不确定性量化（以AUROC评估）和最佳答案选择（TOP1-AUC）。
- **对比方法**：
  - UQ任务：LN-PE（概率基线）、Semantic Entropy（SE）、SAR、BSDetector（黑盒）、INSIDE（白盒）。
  - 最佳答案选择：额外对比Greedy Decoding、Self-Consistency。
- **模型**：GPT-4o-mini、Llama-3-8B、Qwen3-8B。
- **设置**：k=3（采样数），温度t=0.7，正确性阈值ROUGE-L>0.5，惩罚系数λ=1.2。

## 资源与算力

- 论文仅在时间复杂度分析部分明确说明：使用单张NVIDIA GeForce RTX 4090 GPU运行Llama-3-8B模型。
- 其他实验（如GPT-4o-mini等）未提供具体的GPU型号、数量或训练时长。推测作者使用了API或云端算力，但未披露。整体上算力消耗属于中等水平。

## 实验数量与充分性

- **主实验**：6个数据集 × 3个模型 × 2个任务（UQ和最佳答案选择），共36个条件，每个条件下报告多个变异（RES的min/mean/penalized），对比多个基线。
- **消融实验**：
  - 样本数k（1,3,5,8）的影响。
  - 采样温度（0.3,0.5,0.7,0.9）的影响。
  - 结构化提示 vs 无结构化 vs 嵌入相似度 vs LLM评判替代NLI。
  - 惩罚系数λ（0.5~1.5）的敏感性。
  - ROUGE-L阈值（0.3,0.5,0.7）的敏感性。
  - 时间复杂度分解与对比。
- **公平性/客观性**：实验设计较为合理，对比方法采用公开实现或标准设置。RES的k=3设置让其在采样数上占优（其他方法可能需要更多），但作者通过消融实验证明了RES在k=1时仍有效，在k=3时已匹配基线k=8的性能，因此对比是公平且有说服力的。
- **充分性**：实验覆盖面广，覆盖阅读理解、数学、常识、日期推理等多种推理类型，消融充分，但缺少在超大规模模型（如GPT-4、Llama-3-70B）上的验证，且TriviaQA和CoQA仅使用了约3000个子样本，可能存在数据选取偏差。

## 主要结论与发现

1. **RES在复杂推理任务上显著优于基线**：尤其在MultiRC、BBH（Date Understanding、Multistep Arithmetic）、StrategyQA上AUROC提升明显；在TriviaQA和CoQA上增益较小，因为其更多依赖事实记忆或抽取，而非多步推理。
2. **RES在少样本（k=3）下即表现优秀**，无需像语义熵等方法依赖大采样量，计算效率更高。
3. **RES可用于最佳答案选择**：从k个候选中选择分数最高的答案，准确率超过多数基线（包括Self-Consistency）。
4. **结构化提示和NLI是关键**：去除结构化提示或使用余弦相似度替代NLI均导致性能下降。
5. **时间成本适中**：介于LN-PE和BSDetector之间，额外开销主要来自解释路径生成（约7秒/问题），NLI成本极低（~0.2秒）。
6. **RES比token-level置信度更可靠**：案例说明，错误答案可能获得高置信度但RES正确识别其内部矛盾。

## 优点

- **创新性**：首次提出推理-解释对称性度量不确定性，视角独特。
- **高效**：无需多次采样跨输出比较，在少样本下即可取得好效果。
- **可解释性**：通过比较推理与解释的具体路径，可定位不一致环节。
- **黑盒友好**：仅需文本输入输出，不依赖模型内部信息。
- **灵活**：可单独用于UQ，也可嵌入多采样流程（如最佳答案选择）。
- **计算效率与性能平衡**：时间代价合理，远低于BSDetector。

## 不足与局限

1. **衡量的是逻辑一致性而非事实正确性**：偏见或错误的答案若推理解释一致仍得高分，不能直接用于公平性或事实性检测。
2. **对简单事实问答增益有限**：在TriviaQA和CoQA上不如BSDetector或差距较小，说明方法更适用于长链推理。
3. **依赖LLM生成解释的质量**：若生成的解释本身有误或风格不稳定，对称性评分可能失真。
4. **实验规模有限**：仅在8B和GPT-4o-mini级别模型上验证，未在更大模型（如Llama-3-70B、GPT-4）或更复杂数据集（如HotpotQA、MuSiQue）上测试。
5. **时间开销仍高于概率方法**：相比LN-PE，RES多出解释生成费用，在极低资源场景下可能仍然偏贵。
6. **提示工程依赖**：结构化提示的设计对性能有显著影响，可能限制了泛化性。
7. **未解决多答案语义差异问题**：当多个候选答案语义相同但表达不同时，RES仍会重复计算相似对称性，可能导致分数冗余。

（完）
