---
title: "Seeing is Believing, but How Much? A Comprehensive Analysis of Verbalized Calibration in Vision-Language Models"
title_zh: 眼见为实，但有多可靠？视觉语言模型中口头校准的综合分析
authors: "Weihao Xuan, Qingcheng Zeng, Heli Qi, Junjue Wang, Naoto Yokoya"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.emnlp-main.74.pdf"
tags: ["query:luq"]
score: 7.0
evidence: 聚焦视觉语言模型中的口头不确定性，与LLM不确定性量化相关
tldr: 口头不确定性（模型用自然语言表达置信度）是一种轻量级可解释方法，但在视觉语言模型（VLM）中的有效性尚未充分研究。本文对三类VLM、四个任务域进行系统评估，发现当前VLM普遍存在校准不良现象，且视觉推理模型表现尤为突出。该工作揭示了LLM与VLM在不确定性量化上的差异，为提升多模态模型可信度提供了参考。
source: EMNLP-2025-Main
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.74/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1621, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.74/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 714, \"height\": 604, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.74/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 790, \"height\": 557, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.74/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 778, \"height\": 799, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.74/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1651, \"height\": 1118, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.74/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1647, \"height\": 696, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.74/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1310, \"height\": 1590, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.74/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 656, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.74/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1407, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.74/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 659, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.74/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 846, \"height\": 356, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.74/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 761, \"height\": 251, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.74/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1648, \"height\": 1974, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.74/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1652, \"height\": 2166, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.74/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1000, \"height\": 2152, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.74/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1642, \"height\": 2209, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.74/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1041, \"height\": 2091, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.74/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1661, \"height\": 1065, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.74/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1661, \"height\": 625, \"label\": \"Table\"}]"
motivation: 口头不确定性在LLM中有效，但在VLM中的适用性和准确性尚不明确。
method: 在多个模型类别和任务域上评估VLM的口头置信度校准情况。
result: 发现VLM普遍存在校准不良，视觉推理模型的偏差尤为严重。
conclusion: 该工作强调了多模态模型不确定性量化的独特挑战。
---

## Abstract
Uncertainty quantification is essential for assessing the reliability and trustworthiness of modern AI systems. Among existing approaches, verbalized uncertainty, where models express their confidence through natural language, has emerged as a lightweight and interpretable solution in large language models (LLMs). However, its effectiveness in vision-language models (VLMs) remains insufficiently studied. In this work, we conduct a comprehensive evaluation of verbalized confidence in VLMs, spanning three model categories, four task domains, and three evaluation scenarios. Our results show that current VLMs often display notable miscalibration across diverse tasks and settings. Notably, visual reasoning models (i.e., thinking with images) consistently exhibit better calibration, suggesting that modality-specific reasoning is critical for reliable uncertainty estimation. To further address calibration challenges, we introduce Visual Confidence-Aware Prompting, a two-stage prompting strategy that improves confidence alignment in multimodal settings. Overall, our study highlights the inherent miscalibration in VLMs across modalities. More broadly, our findings underscore the fundamental importance of modality alignment and model faithfulness in advancing reliable multimodal systems.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：不确定性量化对于评估AI系统的可靠性和可信度至关重要。大语言模型中，“口头不确定性”（verbalized uncertainty）——即模型通过自然语言表达自身置信度——作为一种轻量级、可解释的解决方案已得到验证。然而，这一方法在视觉-语言模型（VLM）中的有效性尚未得到充分研究。
- **核心问题**：VLMs处理多模态信息，引入了口头置信度表达的额外复杂性。论文提出三个关键问题：
  1. VLMs表达置信度的准确性如何？
  2. 图像中嵌入的指令如何影响校准？
  3. 当相同信息以不同模态呈现时，口头置信度是否保持一致？
- **整体含义**：揭示VLMs在口头置信度校准上的普遍缺陷，强调模态对齐和模型忠实度对于构建可靠多模态系统的重要性。

## 2. 论文提出的方法论

- **核心思想**：系统性评估VLM的口头置信度校准情况，并提出改进策略。
- **关键技术细节**：
  - 定义三类评估设置：通用评估（文本指令+视觉输入）、嵌入指令评估（指令嵌入图像）、语义对齐评估（语义等价但不同模态输入）。
  - 使用**Expected Calibration Error (ECE)**作为主要校准指标：ECE = ∑_{m=1}^{M} (|B_m|/n) |acc(B_m) - avgConf(B_m)|，M=10个置信度bin。
  - 提出**Visual Confidence-Aware Prompting (VCAP)**：两阶段提示策略。第一阶段：模型仅描述视觉内容并给出描述置信度；第二阶段：结合第一阶段的描述和置信度，完成实际任务并生成最终置信度。旨在解耦视觉理解与任务执行，提升校准性能。

## 3. 实验设计

- **数据集/场景**：
  - 通用评估：MMMU-Pro（复杂多学科图像推理）、VideoMMMU（动态视频理解，均匀采样32帧）、Visual SimpleQA（事实性判断）、MathVista和MathVision（数学推理，使用testmini分片）。
  - 嵌入指令评估：MMMU-Pro的仅视觉配置（问题嵌入图像）。
  - 语义对齐评估：IsoBench（四个领域：数学、游戏、科学、算法），包含图像和文本两种模态的等价表示。
- **评估模型**：
  - 视觉推理模型：OpenAI o3、o4-mini
  - 文本推理模型：OpenAI o1、Skywork-R1V2 38B、Kimi-VL-A3B Thinking
  - 指令微调模型：GPT-4.1、Qwen2.5-VL 7B/72B、InternVL3 78B、Kimi-VL-A3B Instruct等
- **对比方法**：VCAP与CoT提示（基线）、Top-K提示（K=3）、自反思提示（self-reflection）进行比较。

## 4. 资源与算力

文中未明确说明使用的GPU型号、数量、训练时长等具体算力信息。仅提及使用了vLLM作为推理引擎，以及Miyabi超级计算机（日本）的算力支持。因此，论文主要基于推理评估而非训练，算力细节未被披露。

## 5. 实验数量与充分性

- **实验数量**：大量实验。包括：
  - 通用评估：5个数据集（MMMU-Pro、VideoMMMU、Visual SimpleQA、MathVista、MathVision），每个数据集报告ACC、ECE、AUROC。
  - 嵌入指令评估：MMMU-Pro的标准10选项与视觉配置对比。
  - 语义对齐评估：IsoBench四个子任务，两种模态（图像 vs 文本）。
  - 消融实验：VCAP的变体（如使用Oracle描述、增加轮数）、数值与语言不确定性对比。
  - 鲁棒性分析：三次重复运行展示稳定性（表7）。
- **充分性与公平性**：覆盖三类模型家族、多个任务领域、多种评估场景，比较全面。对比方法包括强基线（Top-K、自反思），且使用统一提示模板和评估指标，公平性良好。

## 6. 论文的主要结论与发现

- 当前大多数VLM在口头置信度校准上存在显著偏差（miscalibration），尤其是指令微调模型和文本推理模型，ECE常>0.25。
- **视觉推理模型**（o3、o4-mini）在所有基准上持续表现更好的校准，表明模态特定推理对于可靠不确定性估计至关重要。
- 嵌入指令评估中，所有模型（包括视觉推理模型）的准确率和校准均下降，显示模态不对齐问题。
- 语义对齐评估中，大多数模型在视觉输入上的校准劣于文本输入，仅视觉推理模型差距较小。
- VCAP提示策略在多个模型中显著降低ECE（如Qwen2.5-VL 72B上ECE从0.431降至0.365），优于Top-K和自反思基线，且不显著损害准确率。

## 7. 优点

- **全面性**：首次对VLMs的口头置信度进行系统、多维度评估，覆盖三类模型、四个任务域、三种评估场景。
- **提出有效方法**：VCAP两阶段策略设计巧妙，通过先描述视觉内容再任务执行，有效提升了校准，尤其适用于视觉输入复杂的情况。
- **实验设计严谨**：包含多次重复运行、消融实验（Oracle描述、多轮VCAP）、语言vs数值不确定性对比，确保结论稳健。
- **揭示关键洞察**：发现视觉推理模型具有更好校准，为后续多模态模型训练提供指导方向。

## 8. 不足与局限

- **封闭模型限制**：视觉推理模型（o3、o4-mini）为闭源，缺乏实现细节，无法深入分析其校准优越性的原因；且该类别仅有两个模型，通用性待验证。
- **任务覆盖有限**：未涉及时间视觉定位（如视频中的时间锚定）等下游挑战性场景，实验场景虽多但仍有遗漏。
- **VCAP局限性**：在强模型（如o4-mini）上优势不显著；增加轮次改善有限且增加计算成本；Oracle描述反而恶化性能，说明视觉瓶颈是主要问题。
- **基线选择**：自反思和Top-K基线在部分场景下与VCAP效果接近，VCAP的绝对优势不够突出。
- **资源信息缺失**：未提供算力消耗细节，难以评估方法的实际部署成本。

（完）
