---
title: "FESTA: Functionally Equivalent Sampling for Trust Assessment of Multimodal LLMs"
title_zh: FESTA：用于多模态大语言模型信任评估的功能等价采样
authors: "Debarpan Bhattacharya, Apoorva Kulkarni, Sriram Ganapathy"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.findings-emnlp.657.pdf"
tags: ["query:luq"]
score: 7.0
evidence: 提出FESTA，一种用于多模态LLM信任评估的输入采样技术
tldr: 多模态大语言模型（MLLM）的信任评估因输入模态多样而充满挑战。本文提出FESTA，一种功能等价采样技术，通过对输入进行等价和互补采样来生成不确定性度量，从而探知模型的一致性和敏感性。该方法仅需黑盒输入输出访问，无需内部参数。实验表明FESTA能有效评估MLLM预测的可靠性，为选择性预测提供支持。
source: EMNLP-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.657/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 741, \"height\": 1007, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.657/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1584, \"height\": 628, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.657/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 816, \"height\": 1007, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.657/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1668, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.657/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1653, \"height\": 759, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.657/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1617, \"height\": 839, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.657/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1313, \"height\": 1651, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.657/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1148, \"height\": 822, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.657/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1283, \"height\": 799, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.657/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 940, \"height\": 944, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.657/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 757, \"height\": 289, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.657/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1621, \"height\": 418, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.657/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1621, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.657/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1620, \"height\": 307, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.657/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1622, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.657/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1623, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.657/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1152, \"height\": 389, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.657/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1148, \"height\": 330, \"label\": \"Table\"}]"
motivation: 多模态输入范式多样导致MLLM预测的信任评估困难，现有方法需要模型内部信息。
method: 通过等价和互补输入采样生成不确定性度量，仅需黑盒访问。
result: FESTA能有效评估MLLM的可靠性和敏感性，支持选择性预测。
conclusion: 该工作为黑盒多模态模型的信任评估提供了实用工具。
---

## Abstract
The accurate trust assessment of multimodal large language models (MLLMs) generated predictions, which can enable selective prediction and improve user confidence, is challenging due to the diverse multi-modal input paradigms. We propose F unctionally E quivalent S ampling for T rust A ssessment (FESTA), a multimodal input sampling technique for MLLMs, that generates an uncertainty measure based on the equivalent and complementary input samplings. The proposed task-preserving sampling approach for uncertainty quantification expands the input space to probe the consistency (through equivalent samples) and sensitivity (through complementary samples) of the model. FESTA uses only input-output access of the model (black-box), and does not require ground truth (unsupervised). The experiments are conducted with various off-the-shelf multi-modal LLMs, on both visual and audio reasoning tasks. The proposed FESTA uncertainty estimate achieves significant improvement (33.3% relative improvement for vision-LLMs and 29.6% relative improvement for audio-LLMs) in selective prediction performance, based on area-under-receiver-operating-characteristic curve (AUROC) metric in detecting mispredictions. The code implementation is open-sourced.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与研究动机
多模态大语言模型（MLLMs）在视觉和音频推理任务中表现不佳，且容易产生低置信度幻觉。现有不确定性估计方法（如输出熵、对数概率）依赖于模型内部参数，但闭源模型不提供内部访问，且指令微调会破坏对数概率的校准性。此外，低熵幻觉导致熵度量不可靠。因此，需要一种**黑盒、无监督**的信任评估方法，用于选择性预测（即在不确信时避免回答）。

## 2. 方法论：FESTA
**核心思想**：通过**功能等价采样（FES）**和**功能互补采样（FCS）** 分别探测模型输出的**一致性**和**敏感性**，计算不确定性分数用于排错。

- **功能等价采样（FES）**：对输入进行不影响任务语义的变换（如图像灰度化、加噪声、文本改写），理想情况下模型应给出与原来相同的预测。
- **功能互补采样（FCS）**：对输入进行反转任务语义的变换（如问题反转、图像水平翻转），理想情况下模型应给出与原来相反的预测。
- **不确定性量化**：分别计算FES和FCS下模型预测分布与理想模型（完全一致/完全敏感）的**KL散度**，得到 \(U_{\text{FES}}\) 和 \(U_{\text{FCS}}\)，最终FESTA不确定性为两者之和（\(U_{\text{FESTA}} = U_{\text{FES}} + U_{\text{FCS}}\)）。
- **算法流程**：对每个输入，生成 \(K_1\) 个FES样本和 \(K_2\) 个FCS样本（通过模态内组合），获取模型输出分布，计算KL散度并求和。

## 3. 实验设计
- **数据集与任务**：
  - **视觉**：BLINK（空间推理，143 样本）、VSR（视觉空间推理，100 样本）。
  - **音频**：TREA（音频时序推理，含顺序、时长、计数三个子任务，共300样本）。
- **基准方法**：输出熵（OE）、口头置信度（VC）、输入增强（IA：图像IA-I、文本IA-T、联合IA-IT）、改写不确定性（RU）、黑盒不确定性（BU）、语义熵（SE，等价于OE）。
- **评估指标**：AUROC（检测错误预测的能力）。
- **模型**：
  - 视觉：Gemma-3、LLaVA-1.6、Qwen-2.5VL、Phi-4、Pixtral。
  - 音频：Qwen2-Audio、SALMONN，以及SALMONN描述+文本LLM管道。

## 4. 资源与算力
论文明确说明使用了**8块Nvidia RTX A6000 GPU**进行所有实验，未提及具体训练时长（但方法为后处理，无需训练）。

## 5. 实验数量与充分性
- 共计**5个视觉模型 × 2个数据集** + **3个音频模型/管道 × 3个子任务** = 19组主要实验。
- 进行了**消融实验**：分别分析FES和FCS的单独贡献；比较KL散度与标准熵的效果。
- 进行了**样本数量K的敏感性分析**（K从8到120）。
- **局限性**：仅覆盖多选问答（MCQA）场景，未扩展到开放生成；FCS生成部分依赖手工规则（但做了文本和图像两种形式的验证）。

## 6. 主要结论
- FESTA在AUROC上显著优于所有基线方法：
  - 视觉任务平均相对提升24.6%（BLINK）和41.9%（VSR）。
  - 音频任务平均相对提升25.4%（顺序）、30.5%（时长）、32.8%（计数）。
- FESTA能有效检测低不确定性幻觉，这是熵基线失败的关键场景。
- KL散度度量比简单熵更优。
- 少量样本（K=16~20）即可获得稳健估计。

## 7. 优点
- **完全黑盒与无监督**：仅需输入-输出访问，无需模型内部参数或真实标签。
- **原理清晰**：基于功能等价与互补的数学形式化（等价关系证明、KL距离定义）。
- **通用性**：同时适用于视觉和音频模态，且在不同精度模型上均有效。
- **能处理低熵幻觉**：通过FCS敏感性度量弥补了传统熵方法的盲点。
- 代码已开源。

## 8. 不足与局限
- **计算开销**：每个样本需要额外K次推理（K~60），对实时应用可能不友好。
- **FES/FCS生成**：当前为半自动化，依赖于手工设计的变换规则，对复杂任务可能需更多人工。
- **仅限MCQA**：未扩展到开放文本生成或多模态输出（如图像生成）的不确定性估计。
- **未尝试改进模型行为**：仅用于评估，未利用FES/FCS提升模型精度（论文中提到可作为未来工作）。
- **图像FCS仅做部分验证**：仅对“左/右”问题测试了图像级互补变换，通用性受限。

（完）
