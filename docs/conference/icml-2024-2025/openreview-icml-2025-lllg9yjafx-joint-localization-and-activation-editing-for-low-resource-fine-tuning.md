---
title: Joint Localization and Activation Editing for Low-Resource Fine-Tuning
title_zh: 联合定位和激活编辑用于低资源微调
authors: "Wen Lai, Alexander Fraser, Ivan Titov"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Lllg9YjAFX"
tags: ["query:dg"]
score: 9.0
evidence: 联合定位和激活编辑用于低资源微调
tldr: 针对低资源场景下标准PEFT方法效果有限的问题，本文提出JoLA方法，联合学习需要编辑的注意力头以及对应的激活编辑向量，通过激活编辑（steering）实现低资源微调。实验表明，该方法在小样本场景下优于LoRA等基线，并且具有更好的稳定性。该工作为激活编辑技术在资源受限条件下的应用提供了有效方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-lllg9yjafx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1774, \"height\": 858, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lllg9yjafx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 834, \"height\": 612, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lllg9yjafx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 838, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lllg9yjafx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1766, \"height\": 1152, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lllg9yjafx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 840, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lllg9yjafx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 841, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lllg9yjafx/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1772, \"height\": 817, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lllg9yjafx/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 850, \"height\": 560, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lllg9yjafx/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 843, \"height\": 562, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lllg9yjafx/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1762, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lllg9yjafx/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1747, \"height\": 546, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-lllg9yjafx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1768, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lllg9yjafx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 860, \"height\": 274, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lllg9yjafx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1768, \"height\": 325, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lllg9yjafx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1783, \"height\": 504, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lllg9yjafx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1770, \"height\": 979, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lllg9yjafx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1764, \"height\": 711, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lllg9yjafx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1766, \"height\": 662, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lllg9yjafx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1771, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lllg9yjafx/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1768, \"height\": 440, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lllg9yjafx/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1767, \"height\": 438, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lllg9yjafx/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1765, \"height\": 300, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lllg9yjafx/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1770, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lllg9yjafx/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1769, \"height\": 444, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lllg9yjafx/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1769, \"height\": 444, \"label\": \"Table\"}]"
motivation: 标准PEFT方法在仅几百样本的低资源场景下效果有限，而激活编辑技术参数极少且在小数据集上表现有潜力，但依赖于正确识别编辑模块且稳定性不足。
method: 提出JoLA方法，同时学习哪些注意力头需要编辑以及编辑的激活向量，实现端到端的定位和编辑联合优化。
result: 在多个低资源NLP数据集上，JoLA相比LoRA等PEFT方法取得更好性能，且编辑的模块选择和激活更稳定。
conclusion: 激活编辑在低资源微调中具有显著优势，JoLA通过联合学习提升了其效果和稳定性。
---

## Abstract
Parameter-efficient fine-tuning (PEFT) methods, such as LoRA, are commonly used to adapt LLMs. However, the effectiveness of standard PEFT methods is limited in low-resource scenarios with only a few hundred examples. Recent advances in interpretability research have inspired the emergence of activation editing (or steering) techniques, which modify the activations of specific model components. Due to their extremely small parameter counts, these methods show promise for small datasets. However, their performance is highly dependent on identifying the correct modules to edit and often lacks stability across different datasets. In this paper, we propose Joint Localization and Activation Editing (JoLA), a method that jointly learns (1) which heads in the Transformer to edit (2) whether the intervention should be additive, multiplicative, or both and (3) the intervention parameters themselves - the vectors applied as additive offsets or multiplicative scalings to the head output. Through evaluations on three benchmarks spanning commonsense reasoning, natural language understanding, and natural language generation, we demonstrate that JoLA consistently outperforms existing methods.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：标准参数高效微调（PEFT）方法（如 LoRA）在低资源场景（仅数百个训练样本）下性能有限，而激活编辑（Activation Editing）技术虽然参数极少、在小数据集上有潜力，但其效果高度依赖于正确识别需要编辑的模块，且在不同数据集上稳定性差。
- **背景**：近年来可解释性研究（如激活修补）启发了一系列激活编辑方法，它们通过简单操作（加法、乘法）修改特定组件的激活值，参数数量远少于 LoRA。然而，现有方法通常固定编辑哪些模块（如偏置项、MLP 层、注意力头等）以及干预方式（加法或乘法），导致性能不一致。
- **整体目标**：提出一种联合学习的方法 JoLA，能够同时决定“编辑哪些注意力头”、“使用何种干预策略（加性、乘性或两者）”以及“学得具体的编辑向量”，从而在低资源场景下实现稳定且高效的微调。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过引入可微的门控机制（Hard Concrete 分布）和预期 L0 正则化，JoLA 动态地选择一部分注意力头，并为每个选中的头独立学习加性偏移向量和乘性缩放向量，从而在端到端训练中实现定位与编辑的联合优化。
- **关键技术细节**：
  - **干预形式**：对注意力头 (l,i) 的输出 z<sup>(l,i)</sup> 进行混合干预：  
    `z' = (1 + g_m · m) ⊙ z + g_a · a`  
    其中 m 和 a 分别为乘性缩放向量和加性偏移向量，g_m、g_a 为 [0,1] 标量门控。当门控为 0 时，该头保持不变。
  - **门控机制**：每个头配有两个独立的 Hard Concrete 分布门（一个用于乘法、一个用于加法），门控由可训练的标量参数控制，训练中通过随机采样实现，推理时取期望值。
  - **稀疏正则化**：使用预期 L0 正则化项鼓励门控被关闭（即头不被编辑），损失函数为：  
    `L = L_xent + λ * L_C`，其中 L_C 是所有头两个门控非零概率之和。
  - **优化**：联合优化所有门控参数、缩放向量 m 和偏移向量 a，利用 Gumbel Softmax 实现离散选择的连续松弛。
- **流程文字说明**：
  1. 初始化所有头的门控参数为“开放”状态。
  2. 前向传播：每个头的输出经过门控加权后的干预。
  3. 反向传播：通过标准交叉熵损失和 L0 正则化梯度更新所有参数。
  4. 训练过程中门控自动闭合不重要的头，仅保留少量关键头进行编辑。
  5. 推理时，关闭概率极低的门控（< ε），其余门控取期望值，确保确定性。

## 3. 实验设计：数据集、基准对比方法

- **数据集**：三大类，共 26 个任务：
  - 常识推理：ARC-c, ARC-e, BoolQ, HellaSwag, OBQA, PIQA, SIQA, WinoGrande
  - 自然语言理解：MMLU-Pro 下的 14 个领域（生物、商业、化学、计算机科学、经济学、工程、健康、历史、法律、数学、其他、哲学、物理、心理学）
  - 自然语言生成：CommonGen, E2E_NLG, WebNLG, Xsum
- **低资源设定**：每个任务仅使用 200 个训练样本（部分实验扩展到更大规模）。
- **基准方法**：
  - Zero-shot（无微调）
  - 参数高效微调：LoRA
  - 激活编辑方法：BitFit、RED、RePE（推理时）、ReFT、LoFIT
- **评测指标**：
  - 推理和理解任务：准确率（Accuracy）
  - 生成任务：BLEU、ROUGE-L、BERTScore

## 4. 资源与算力

- 文中明确提到：
  - 1B、3B、8B、13B 模型实验在 **单个 NVIDIA A100 80GB GPU** 上运行。
  - 70B 模型实验在 **NVIDIA H100 94GB GPU** 上运行。
  - 以 LLaMA-3-8B 为例，JoLA 在低资源设定（200 样本）下 **约 2 GPU 小时** 收敛。
  - 未说明具体训练轮次和总 GPU 天数，仅给出典型任务的训练时长。

## 5. 实验数量与充分性

- **主实验**：在 LLaMA-3.1-8B 和 Qwen-2.5-7B 两个模型上，覆盖 26 个任务，每个任务均报告了与多种基线的对比结果（Table 1, Figure 4）。
- **消融实验**：
  - Ablation 1：对比带/不带门控机制（MLP vs Attention vs 组合）。
  - Ablation 2：对比单门控 vs 双门控（加性与乘性分别门控）。
  - Ablation 3：对比不同头选择策略（SMP, DSP, PASS vs JoLA）。
- **附加分析**：
  - 训练过程中门控状态的演化（Figure 7）。
  - 不同数据规模（100~100k）的表现（Figure 8）。
  - 不同模型规模（1B, 3B, 8B, 70B）的表现（Figure 9）。
  - 不同学习率调度策略的对比。
- **充分性评估**：实验设计较全面，涵盖了多个数据集、模型、数据规模、消融组件，且对基线方法进行了超参调优（5 组超参数平均）。结果呈现清晰，统计充分。但注意：所有实验仅在英语任务上进行，未验证多语言场景；且仅在两个主流指令模型上进行，未扩展到其他架构（如 GPT 类）。

## 6. 论文的主要结论与发现

1. **注意力头是最佳编辑目标**：相比偏置项、MLP 层、隐藏状态，编辑注意力头带来的性能提升最大，且组合多种组件反而损害性能（过拟合）。
2. **加性偏移比乘性缩放更重要**：消融实验表明，移除加性成分导致性能下降更明显（Figure 3）。
3. **JoLA 一致超越所有基线**：在三个基准的 26 个任务上，JoLA 的平均准确率/BLEU/ROUGE-L/BERTScore 均显著优于 LoRA、LoFIT、ReFT 等方法，尤其在极低资源场景（100~200 样本）下优势明显。
4. **门控机制带来稳定性**：动态门控使得 JoLA 对任务差异具有鲁棒性，避免了手工选择组件的敏感性。
5. **稀疏性合理**：训练结束时，大部分头的门控被关闭（如 OBQA 上 86% 加性门、94% 乘性门为 0），仅少量头被编辑，参数效率极高。

## 7. 优点：方法或实验设计上的亮点

- **联合优化**：将组件定位与干预策略融为一体，避免了 LoFIT 的两阶段解耦问题。
- **自适应门控**：使用 Hard Concrete 分布实现可微的稀疏选择，无需手动指定编辑数量，自动适应任务。
- **极低参数开销**：相比 LoRA（~0.26%），JoLA 仅修改 ~0.0065% 的参数（训练时），推理时仅 ~0.0002%，非常适合低资源。
- **实验覆盖广**：在 26 个不同难度的任务上验证，且包含常识推理、知识理解、生成三类，结论具有普适性。
- **分析深入**：提供了门控状态动态、不同组件贡献、不同数据规模等详实分析，增强了可信度。

## 8. 不足与局限

1. **仅关注注意力头**：虽然实验证明注意力头最佳，但可能忽略了某些任务中其他组件（如 MLP 的中间层）的重要性，未来可探索更细粒度的跨组件联合定位。
2. **超参数敏感性**：λ（L0 正则化权重）、温度等需要调参，论文未提供充分的灵敏度分析。
3. **数据集局限**：所有实验均为英文任务，未涉及多语言或跨领域迁移，通用性待验证。
4. **模型类型局限**：仅实验了 LLaMA 和 Qwen 系列，未在 encoder-only、T5 等架构上验证。
5. **生成任务指标**：BLEU、ROUGE-L 用于生成评估有局限性，缺乏人工评价或更现代的指标（如 GPT-4 评分）。
6. **计算成本**：虽然训练时间短，但门控机制引入额外开销，在极大规模模型上的可行性未充分讨论。

（完）
