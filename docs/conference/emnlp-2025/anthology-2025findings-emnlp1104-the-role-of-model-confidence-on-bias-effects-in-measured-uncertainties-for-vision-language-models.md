---
title: The Role of Model Confidence on Bias Effects in Measured Uncertainties for Vision-Language Models
title_zh: 模型置信度对视觉语言模型测量不确定性中偏差效应的作用
authors: "Xinyi Liu, Weiguang Wang, Hangfeng He"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.findings-emnlp.1104.pdf"
tags: ["query:luq"]
score: 4.0
evidence: 研究偏差对视觉语言模型不确定性的影响
tldr: 该论文研究视觉语言模型中提示偏差对认知不确定性估计的影响。通过实验发现，缓解提示偏差可以改善GPT-4o等模型的不确定性量化质量。工作揭示了偏差与不确定性之间的权衡，为提升多模态模型输出可靠性提供了洞见。
source: EMNLP-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1104/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 786, \"height\": 250, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1104/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 731, \"height\": 547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1104/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1410, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1104/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 658, \"height\": 650, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1104/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 706, \"height\": 604, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1104/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 708, \"height\": 549, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1104/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1549, \"height\": 2382, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1104/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 835, \"height\": 454, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1104/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1577, \"height\": 809, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1104/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1577, \"height\": 809, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1104/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 708, \"height\": 828, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1104/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 697, \"height\": 174, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1104/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1176, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1104/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1411, \"height\": 781, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1104/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1410, \"height\": 780, \"label\": \"Table\"}]"
motivation: LLM用于开放任务时，认知不确定性估计受偏差影响，但偏差与不确定性关系不明。
method: 在VQA任务上系统分析提示偏差对不确定性量化的影响，并设计去偏策略。
result: 缓解提示偏差后，GPT-4o的不确定性估计与真实知识缺失更一致。
conclusion: 揭示了偏差管理对LLM不确定性可靠性的重要性，为多模态系统提供了指导。
---

## Abstract
With the growing adoption of Large Language Models (LLMs) for open-ended tasks, accurately assessing epistemic uncertainty, which reflects a model’s lack of knowledge, has become crucial to ensuring reliable outcomes. However, quantifying epistemic uncertainty in such tasks is challenging due to the presence of aleatoric uncertainty, which arises from multiple valid answers. While bias can introduce noise into epistemic uncertainty estimation, it may also reduce noise from aleatoric uncertainty. To investigate this trade-off, we conduct experiments on Visual Question Answering (VQA) tasks and find that mitigating prompt-introduced bias improves uncertainty quantification in GPT-4o. Building on prior work showing that LLMs tend to copy input information when model confidence is low, we further analyze how these prompt biases affect measured epistemic and aleatoric uncertainty across varying bias-free confidence levels with GPT-4o and Qwen2-VL. We find that all considered biases have greater effects in both uncertainties when bias-free model confidence is lower. Moreover, lower bias-free model confidence is associated with greater bias-induced underestimation of epistemic uncertainty, resulting in overconfident estimates, whereas it has no significant effect on the direction of bias effect in aleatoric uncertainty estimation. These distinct effects deepen our understanding of bias mitigation for uncertainty quantification and potentially inform the development of more advanced techniques.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：随着大语言模型（LLMs）在开放式任务中的广泛应用，准确评估**认知不确定性**（epistemic uncertainty，反映模型知识缺失）变得至关重要。然而，由于存在**偶然不确定性**（aleatoric uncertainty，源于多个有效答案），量化认知不确定性面临挑战。
- **关键权衡**：偏差（bias）可能给认知不确定性估计引入噪声，但也可能通过将概率质量集中在单个或少数有效答案上，降低偶然不确定性的噪声。论文旨在探究这种权衡，并分析偏差如何在不同置信度水平下分别影响两类不确定性的测量。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过**缓解提示引入的偏差**（prompt-introduced biases），提高不确定性量化的质量；进一步分析偏差对认知不确定性和偶然不确定性的不同影响，特别是随模型置信度变化的关系。
- **关键技术与公式**：
  - **不确定性分解**：定义总熵 = 认知熵 + P(correct) × 偶然熵。其中认知熵为正确预测概率与错误预测概率的熵，偶然熵为正确答案归一化分布的熵。
  - **偏差缓解策略**：对每个偏差类型（文本三类：措辞、位置、标签；图像三类：形状、方向、低级特征），通过多次扰动提示（如重排、旋转、加噪声等）获取平均概率分布，视为“免偏”参考分布。
  - **偏差效应度量**：计算单次提示与免偏平均提示之间认知/偶然熵的**绝对变化**（偏差效应）和**熵减少**（偏差导致的过度自信程度）。
  - **回归分析**：以免偏模型置信度（正确选项概率之和）为自变量，分别对偏差效应（绝对变化）和偏差引起的熵下降进行线性回归，得到系数和p值，检验置信度与偏差影响的关系。
- **算法流程**：对每个问题，生成具有不同偏差扰动的多个提示（每个偏差类型10个），得到输出概率分布，计算单次与平均的熵，再与真实标签（有监督分析时）配合计算认知/偶然熵。

## 3. 实验设计

- **数据集**：使用 **VL_checklist** 和 **CREPE** 两个视觉语言数据集，每个包含大量图像及人工验证的正/负描述。从中为每个图像随机选择2个正确和2个错误描述，构建1000个问题。
- **基准方法**：
  - 单次推理概率/熵（Single-inference）
  - 重复采样平均（Repetitive-based）
  - 互信息方法（Mutual Information，Yadkori et al. 2024）
  - 答案计数方法（#Answers）
  - 基于重排/重标签/重述的熵（所提方法）
- **对比方法**：针对每种偏差类型（措辞、位置、标签、形状、方向、低级特征）分别进行偏差缓解；并组合三种文本或三种图像方法，以及全部六种。
- **评估指标**：
  - 不确定性量化性能：**AUROC**（衡量置信度排序正确性）
  - 偏差效应分析：线性回归系数和p值
- **模型**：GPT-4o（闭源）、Qwen2-VL 72B（开源），部分额外实验在Claude-3.7-Sonnet上。

## 4. 资源与算力

- 论文**未明确说明**使用的GPU型号、数量、训练时长等算力信息。只提到预算限制（budget constraints）导致仅对Claude-3.7-Sonnet进行了两个偏差的扩展实验，但未提供具体硬件配置。

## 5. 实验数量与充分性

- **实验数量**：
  - 在GPT-4o上，对两种数据集、六种偏差类型分别测试，每个偏差类型使用10个扰动提示；并进行了组合实验（文本三种、图像三种、全部六种）。
  - 在Qwen2-VL上，重复上述回归分析。
  - 额外对GPT-4o评估了不同基准方法（单次、重复、互信息等）的AUROC。
  - 扩展实验：对Claude-3.7-Sonnet仅测试了措辞和标签两种偏差。
- **充分性与公平性**：
  - **充分**：覆盖了多种文本和图像偏差，且分别分析了认知与偶然不确定性，回归分析检验了统计显著性。
  - **客观公平**：确保各扰动提示的准确率相近（附录表6），排除提示质量影响；使用AUROC这一对类别不平衡鲁棒的指标；采用多种基准方法进行比较。
  - **局限**：仅使用了两个VQA数据集，未在纯文本多标签数据集上验证（因现有基准性能已饱和）；闭源模型可能引入概率波动。

## 6. 论文的主要结论与发现

- **缓解偏差提升不确定性量化**：在GPT-4o上，去除文本偏差（如重述、重排、重标签）可将AUROC提升约6-7%（VL_checklist上从0.7492到0.8123）。图像偏差去除效果较小（约2-4%）。
- **低置信度下偏差影响更大**：无论何种偏差类型，模型免偏置信度越低，偏差对认知和偶然不确定性测量的绝对变化越大（回归系数均为负，多数显著）。
- **偏差对认知不确定性的影响更强**：认知不确定性的偏差效应与置信度的相关性（系数绝对值）远大于偶然不确定性（比值Epi./Ale.多>1），且偶然不确定性的p值常不显著。
- **低置信度导致更大的偏差引起的过度自信**：免偏置信度越低，偏差造成的认知熵减少越大（即模型更过度自信），但对于偶然熵，方向变化不显著（系数不显著或符号不一致）。

## 7. 优点

- **方法论创新**：首次系统分析偏差对两类不确定性（认知vs偶然）的差异化影响，以及随置信度的变化规律。
- **实验设计严谨**：采用多种偏差扰动策略，且通过AUROC和回归分析两种视角评估，统计检验充分。
- **模型覆盖广泛**：在闭源（GPT-4o、Claude）和开源（Qwen2-VL）模型上均得到一致结论，增强了普适性。
- **实用洞察**：揭示了偏差缓解不仅提升公平性，也是提升不确定性估计可靠性的关键，为开发更先进技术提供方向。

## 8. 不足与局限

- **依赖token概率**：闭源模型（如GPT-4o）提供top-20概率，但其他模型（如Gemini）限制多，需要采样近似，可能引入误差。
- **推理成本增加**：每个偏差类型需要多次扰动提示（10次），组合使用则数量更多，相比单次推理成本显著上升。
- **数据集局限**：仅使用两个VQA数据集，且人为选取2正确+2错误描述，可能与真实多标签场景有差距。未在纯文本多标签基准上验证（因现有基准性能饱和）。
- **未考虑内部模型状态**：方法仅基于外部输出概率，无法利用内部表示，可能遗漏认知不确定性的更细粒度信号。
- **免偏参考的近似性**：多提示平均分布并非绝对免偏，仅为相对偏差减少的近似。

（完）
