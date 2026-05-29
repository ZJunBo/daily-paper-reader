---
title: Analysing the Generalisation and Reliability of Steering Vectors
title_zh: 分析引导向量的泛化性与可靠性
authors: "Daniel Chee Hian Tan, David Chanin, Aengus Lynch, Brooks Paige, Dimitrios Kanoulas, Adrià Garriga-Alonso, Robert Kirk"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=v8X70gTodR"
tags: ["query:dg"]
score: 8.0
evidence: 引导向量的泛化性与可靠性分析
tldr: 该论文系统研究了引导向量在分布内外的可靠性和泛化性。发现分布内引导效果因输入而异，虚假偏见显著影响有效性；分布外存在严重限制。这为引导技术的广泛使用提出了挑战，并强调了需要更稳健的引导方法。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1433, \"height\": 677, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 716, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1417, \"height\": 917, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1421, \"height\": 648, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1406, \"height\": 546, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1406, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1404, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1423, \"height\": 575, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1383, \"height\": 578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1287, \"height\": 785, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1290, \"height\": 811, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1091, \"height\": 712, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1242, \"height\": 797, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1309, \"height\": 398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1414, \"height\": 919, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1385, \"height\": 612, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1413, \"height\": 1373, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1400, \"height\": 1831, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1281, \"height\": 1464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1406, \"height\": 489, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1405, \"height\": 774, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1404, \"height\": 1377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-v8x70gtodr/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1420, \"height\": 349, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-v8x70gtodr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1465, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-v8x70gtodr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1456, \"height\": 2075, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-v8x70gtodr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1455, \"height\": 2287, \"label\": \"Table\"}]"
motivation: 引导向量作为新兴方法，其可靠性和泛化能力尚不清楚。
method: 通过大量实验分析引导向量在分布内外的表现，识别影响效果的因素。
result: 引导向量在分布内效果高度可变，受虚假偏见影响；分布外泛化能力有限。
conclusion: 引导向量存在显著局限性，需要进一步改进才能安全可靠地使用。
---

## Abstract
Steering vectors (SVs) are a new approach to efficiently adjust language model behaviour at inference time by intervening on intermediate model activations. They have shown promise in terms of improving both capabilities and model alignment. However, the reliability and generalisation properties of this approach are unknown. In this work, we rigorously investigate these properties, and show that steering vectors have substantial limitations both in- and out-of-distribution. In-distribution, steerability is highly variable across different inputs. Depending on the concept, spurious biases can substantially contribute to how effective steering is for each input, presenting a challenge for the widespread use of steering vectors. Out-of-distribution, while steering vectors often generalise well, for several concepts they are brittle to reasonable changes in the prompt, resulting in them failing to generalise well. Overall, our findings show that while steering can work well in the right circumstances, there remain many technical difficulties of applying steering vectors to guide models' behaviour at scale.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：引导向量（Steering Vectors, SVs）是一种新兴的推理时干预技术，通过在中间激活上添加或减去特定方向来调整语言模型的行为。已有工作显示其在提升能力与对齐方面有潜力，但其**可靠性**（是否对每个输入都有效）和**泛化性**（是否能在不同提示设置下保持效果）尚未被系统研究。
- **核心问题**：本文旨在系统评估SVs在分布内（in-distribution）的可靠性和分布外（out-of-distribution）的泛化能力，揭示其实际使用的局限性。
- **整体含义**：尽管SVs在特定条件下有效，但存在显著的技术障碍：分布内效果高度可变且受虚假偏见影响，分布外泛化不稳健。因此，SVs目前并非模型对齐的万能解决方案。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：通过对比激活加法（Contrastive Activation Addition, CAA）提取和应用SVs，并系统评估其在不同输入和提示下的表现。
- **关键技术细节**：
  - **对比提示**：构造包含正反两个选项（标记为(A)/(B)或Yes/No）的多选题，随机化选项顺序以避免位置偏见。
  - **向量提取**：在选定层L的残差流上，提取正反选项位置的激活，取均值差作为引导向量：
    \[
    v_{MD} = \frac{1}{|D|} \sum_{(x,y^-,y^+)\in D} \left( a_L(x,y^+) - a_L(x,y^-) \right)
    \]
  - **干预**：在推理时，对最后一层L的激活加上 \(\lambda \cdot v_L\)（\(\lambda\) 为强度乘数）。
  - **度量**：使用**logit差**（正选项logit减负选项logit）作为倾向性度量，定义**可引导性**（steerability）为在不同\(\lambda\)下平均logit差的线性回归斜率。
- **算法流程**（文字描述）：
  1. 选择数据集（40个MWE数据集+TruthfulQA等），构造对比提示。
  2. 对每个数据集，用训练集提取引导向量（均值差），在验证集上选择最优层（Llama-2-7b: 层13；Qwen-1.5-14b: 层21）。
  3. 固定层后，在测试集上计算不同乘数下的logit差曲线，得到可引导性得分。
  4. 对分布外泛化，在源提示设置下提取向量，在目标提示设置下评估相对可引导性。

## 3. 实验设计：数据集、场景、基准与对比方法

- **数据集**：主要使用**Model-Written Evaluations (MWE)** 中的40个数据集，覆盖多种人格与行为（如诚实、迎合、权力寻求、宗教立场等）。额外包括TruthfulQA和sycophancy数据集。
- **场景**：
  - **分布内**：在BASE提示设置下提取并评估。
  - **分布外**：构造4种提示偏移：(1) BASE→USER_NEG, (2) BASE→USER_POS, (3) SYS_POS→USER_NEG, (4) SYS_NEG→USER_POS。通过修改系统消息或用户提示前缀来刺激或抑制目标行为。
- **基准与对比**：
  - 未对比其他SVs提取方法（如PCA、逻辑回归），仅使用CAA方法。
  - 对比不同模型（Llama-2-7b-Chat, Qwen-1.5-14b-Chat）上的可引导性相关性。
  - 分析虚假偏见（选项位置/Yes-No偏好）对可引导性的影响。
- **模型**：Llama-2-7b-Chat和Qwen-1.5-14b-Chat（指令微调模型）。附录中还包括Gemma-2-2b-it和Llama-3.1-70b的额外实验。

## 4. 资源与算力

- **文中明确说明**：所有实验在一张A100（40GB显存）上完成。未提及具体的GPU数量、训练时长或总计算量。

## 5. 实验数量与充分性

- **实验数量**：
  - 40个数据集，每个数据集有1000样本（40-10-50分割）。
  - 分布内：对每个数据集计算每个样本的可引导性，分析方差。
  - 分布外：4种偏移，每个偏移组合评估相对可引导性。
  - 层选择：对两个模型分别扫描所有层（约30-40层）。
  - 消融：验证乘数范围对结果的影响（图17）；分析虚假偏见对可引导性方差的解释比例（图4）。
  - 跨模型相关性：比较Llama和Qwen的可引导性（图7、图21）。
- **充分性**：实验覆盖了广泛的行为概念和提示偏移，统计量（Spearman相关系数）和可视化充分。但：
  - 仅使用多选题格式，未扩展到开放生成场景。
  - 仅两个主要模型，附录补充两个额外模型。
  - 未对比多种SVs提取方法（仅用CAA）。
- **客观性**：报告了方差、反例比例、虚假偏见等负面结果，结论平衡。

## 6. 论文的主要结论与发现

1. **分布内可靠性差**：
   - 可引导性在不同输入间高度可变，许多样本出现**反引导**（steerability为负）。
   - 虚假因素（选项A/B位置、Yes/No选择）显著影响可引导性，且不同数据集偏好不同，无法通过简单数据平衡消除。
2. **分布外泛化受限**：
   - SVs在分布外通常效果更差，泛化程度因提示偏移而异。
   - 可引导性主要取决于数据集而非模型（跨模型高度相关）。
   - 模型在源与目标提示下的（未引导）倾向性越接近，引导向量泛化越好；这导致SVs在需要引导至罕见行为时泛化最差。
3. **反例比例高**：多个数据集近50%的样本被引导到相反方向。
4. **不可引导行为**：部分行为（如平均功利主义、自恋）几乎不可引导，可能因为这些概念在线性表示中较弱。

## 7. 优点：方法或实验设计的亮点

- **系统性与规模**：首次在40个数据集、多个提示偏移下全面评估SVs的可靠性与泛化性，超越以往工作的聚合评估。
- **细粒度分析**：引入每个样本的可引导性分析，发现方差和反例，揭示聚合指标掩盖的问题。
- **发现新型偏见**：识别“可引导性偏见”（steerability bias），即模型对特定选项位置或词汇更易引导，这是独立于标准位置/词汇偏见的现象。
- **跨模型验证**：在两个不同架构和规模的模型上复现主要发现，增强了结论的普适性。
- **开源与可复现**：承诺发布代码和实验配置。

## 8. 不足与局限

- **实验覆盖**：
  - 仅限多选题格式，未验证开放生成场景（虽引用前人工作说明两者相关）。
  - 仅两个主要模型，虽补充两个更小/更大模型，但未覆盖更多样化的架构（如MoE、闭源模型）。
  - 提示偏移类型有限（仅系统消息和用户前缀），未考虑其他自然分布变化（如问题措辞、领域变化）。
- **方法局限**：
  - 仅使用CAA提取方法，未比较PCA、逻辑回归等可能改善可靠性的方法。
  - 未探讨改进SVs可靠性的方法（如去偏、多重向量组合）。
- **解释不够深入**：虚假偏见只能部分解释方差，大量残差方差来源未明确。
- **应用风险**：由于反引导致问题，依赖SVs进行安全对齐可能带来危险：在部分输入上反而增强了不受欢迎的行为。

（完）
