---
title: Adaptive Platt Scaling with Causal Interpretations for Self-Reflective Language Model Uncertainty Estimates
title_zh: 具有因果解释的自适应普拉特缩放用于自反性语言模型不确定性估计
authors: "Anthony Sicilia, Malihe Alikhani"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.findings-emnlp.999.pdf"
tags: ["query:uq-safety"]
score: 8.0
evidence: 通过自适应温度缩放的自我反思不确定性估计
tldr: LLM的自我监控能力依赖不确定性表达。本文利用域适应理论对基础预测与反思判断的差异建模，提出温度缩放算法校准不确定性。在挑战性问答任务上评估，性能提升。该工作增强了LLM自我反思的可靠性。
source: EMNLP-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.999/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 595, \"height\": 353, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.999/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 792, \"height\": 173, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.999/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 791, \"height\": 209, \"label\": \"Table\"}]"
motivation: LLM自我反思的不确定性校准需要形式化建模。
method: 用域适应理论建模预测与反思的偏移，并基于此调整温度。
result: 在问答任务上验证了校准效果。
conclusion: 提出一种结合域适应的自反性不确定性校准方法。
---

## Abstract
As large language models (LLMs) are consumed by more users and deployed in increasingly autonomous capacities, their ability to self-monitor and ask for human intervention is of vital importance. Underlying this capability are fundamental skills like self-reflection and expression of uncertainty. In this work, we provide a formal analysis of LLM self-reflection for uncertainty estimation, using domain adaptation theory to model the shift between base predictions and reflective judgments. We use this to motivate a temperature scaling algorithm that calibrates uncertainty using comparisons between base predictions and LLM self-reflections. We evaluate our approach on challenging question-answering tasks requiring reasoning, demonstrating that our methods can improve calibration of uncertainty estimates and also offer improvements in human interpretation. More broadly, this use case shows how domain adaptation presents a promising analytical tool for understanding the underlying statistical properties of LLM self-reflections.

---

## 论文详细总结（自动生成）

# 中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

大型语言模型（LLM）在日益自主的部署中需要具备自我监控能力，能够识别自身可能出错的情况并以可解释的方式表达不确定性。现有的方法大多将模型的反思和不确定性估计视为静态、孤立的输出，忽略了LLM推理的动态性——模型可以通过迭代重新评估答案来提高准确性。本文旨在填补这一空白，通过引入域适应理论来形式化分析LLM自我反思过程，认为自我反思会导致分布偏移（从基础预测到反思判断），并基于此提出一种新的校准算法来改进不确定性估计，同时提供因果解释能力。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将LLM的自我反思视为一种分布偏移。初始回答QA对应的概率分布P(C|QA)与反思后的条件概率P(C|QA,R)不同。通过Bayes定理推导出二者关系，并利用域适应理论中的界（bound）说明，即使基础校准误差很小，由于未考虑反思信息，误差仍可能很大。为此，作者提出一种改进的Platt Scaling方法，通过引入反思信号与基础信号的交互项以及数据元标签（meta-labels）来弥补缺失信息。

- **关键技术细节**：
  - 传统的Platt Scaling：log(ˆP/(1-ˆP)) = α·ˆZ_qa + β，其中ˆZ_qa是模型直接预测的置信度信号（如1-10分）。
  - 基础反思方法：直接用反思后的置信度信号ˆZ_qar替换ˆZ_qa，即log(ˆP/(1-ˆP)) = α·ˆZ_qar + β。
  - 提出的自适应Platt Scaling（式(9)）：log(ˆP/(1-ˆP)) = α₁·ˆZ_qar + α₂·ˆZ_qar·ˆZ_qa + α₃·ˆZ_qa + Σᵢβᵢdᵢ + β₀。其中d是长度为k的二进制数据元标签向量（如问题子类型），交互项α₂·ˆZ_qar·ˆZ_qa用于粗略近似域适应界中的松弛项。

- **因果解释**：基于假设不确定性信号足够准确，且数据元标签d作为“处理变量”，通过上述模型估计因果（对数）优势比CLO，从而量化特定数据属性对LLM出错概率的因果影响。

## 3. 实验设计

- **数据集与场景**：
  - **BBH**（Big Bench Hard）：逻辑推理任务集，元标签为不同问题子类型。
  - **MMLU-Pro**：基于MMLU的增强版困难问答集，元标签为问题领域（如商业、历史、物理等）。
  - **FD**（FortUneDial）：预测对话中未来事件的问答任务（如谈判是否会成功），元标签为对话领域。

- **Benchmark与对比方法**：
  - **基础Platt Scaling（式(3)）**：仅使用初始置信度ˆZ_qa。
  - **反思直接校准（式(8)）**：仅使用反思后置信度ˆZ_qar。
  - **本文方法（式(9)）**：使用交互项和元标签。
  - 评估指标：Brier Skill Score（BSS），即模型不确定性解释的正确性方差百分比（越高越好）。

## 4. 资源与算力

论文中未明确说明所使用的GPU型号、数量或训练时长。仅提到模型通过Together AI访问，设置temperature=0.7。实验涉及的模型包括Llama 3.1 8B、Llama 4 Scout、Gemma 2 9B、Mistral Small 3。校准回归层使用statsmodels包中的默认Logit超参数，数据集大小为每个任务1200点（60/40训练/测试分割），计算开销低。

## 5. 实验数量与充分性

- **实验数量**：覆盖3个数据集、4种模型，共12个主要比较场景（表1）。还进行了消融实验（表2左）评估式(9)中各系数的贡献，以及因果分析案例（表2右）。
- **充分性**：实验设计较为全面，涵盖了多个推理任务类型和模型规模，且进行了统计显著性检验（Hoeffding不等式）。但仅测试了中等规模模型（8-9B），未涉及更大模型（如70B+）。每数据集仅1200点，规模较小。消融实验完整，验证了理论推导的各个成分。总体而言，实验在合理范围内，但泛化性有待更大规模验证。

## 6. 论文的主要结论与发现

- 提出的自适应Platt Scaling（式(9)）在三个数据集上平均BSS均优于基线（式(3)和式(8)），且统计显著。平均BSS从3.2提升至5.0。
- 消融实验表明，所有系数（交互项、元标签项）均对改进有贡献，验证了域适应理论预测的统计依赖关系。
- 因果分析示例：在MMLU-Pro上，计算机科学（CS）和法律类问题导致LLM出错的风险最高（CLO降低约40%），而历史和心理学问题风险最低（CLO降低约25%），且这些效应独立于模型自身的不确定性表达。
- 该方法仅需额外一次反思前向传递和简单回归层，计算开销可忽略。

## 7. 优点

- **理论严谨**：用域适应理论形式化自我反思导致的分布偏移，为校准方法提供数学支撑。
- **方法轻量**：仅添加一个带交互项和元标签的回归层，参数极少（数十个），无需重新训练LLM。
- **因果可解释性**：通过回归系数直接量化数据属性对出错概率的因果影响，有助于诊断模型在特定领域的弱点。
- **通用性**：方法适用于不同模型和任务，且与反思流程天然兼容。

## 8. 不足与局限

- **性能不稳定**：增加参数导致在某些情况下（如Mistral Small在FortUneDial上）BSS为负，性能下降，表明样本复杂度增加可能带来过拟合风险。
- **假设依赖**：域适应理论的假设可能不适用于所有模型/数据集；因果分析依赖于式(9)的正确设定，且需要LLM不确定性信号足够准确。
- **实验规模较小**：每数据集仅1200点，模型限于中等规模（8-9B），未在更大模型或多语言场景下验证。
- **未与所有SOTA方法对比**：仅对比了基础Platt Scaling变体，未与并发研究的其他不确定性校准方法（如多种置信度提示策略、logit-based方法）横向比较。
- **实际部署**：作者声明方法应视为研究原型，需结合全面安全机制才能用于实际。

（完）
