---
title: "Curvature Tuning: Provable Training-free Model Steering From a Single Parameter"
title_zh: 曲率调节：从单一参数实现可证明的免训练模型转向
authors: "Leyang Hu, Matteo Gamba, Randall Balestriero"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=gwBqVheRiD"
tags: ["query:dg"]
score: 7.0
evidence: 通过调节激活函数曲率实现无需训练的模型转向
tldr: 传统微调依赖权重适应且缺乏可解释性。本文提出曲率调节方法，通过在激活函数中注入单一超参数改变决策边界曲率，实现无需训练的模型转向。理论证明该方法可解释地调节曲率，实验验证其在多个任务上有效。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-gwbqvherid/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1430, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gwbqvherid/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1008, \"height\": 400, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gwbqvherid/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1288, \"height\": 408, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gwbqvherid/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1394, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gwbqvherid/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1390, \"height\": 806, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gwbqvherid/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1391, \"height\": 809, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gwbqvherid/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1434, \"height\": 1290, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-gwbqvherid/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1396, \"height\": 681, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gwbqvherid/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 676, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gwbqvherid/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1448, \"height\": 541, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gwbqvherid/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1094, \"height\": 666, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gwbqvherid/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1229, \"height\": 2245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gwbqvherid/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1230, \"height\": 674, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gwbqvherid/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1176, \"height\": 632, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gwbqvherid/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1227, \"height\": 2218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gwbqvherid/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1303, \"height\": 2220, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gwbqvherid/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1176, \"height\": 629, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gwbqvherid/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1177, \"height\": 628, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gwbqvherid/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1331, \"height\": 1659, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gwbqvherid/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1322, \"height\": 1307, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gwbqvherid/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1006, \"height\": 1451, \"label\": \"Table\"}]"
motivation: 现有微调方法可解释性差且依赖启发式超参数，需要更原则性的转向方法。
method: 将激活函数视为样条算子，通过单一超参数修改其曲率来调整决策边界。
result: 理论分析和实验表明，曲率调节能够有效改变模型行为且保持性能。
conclusion: 激活函数曲率是控制模型行为的关键因素。
---

## Abstract
The scaling of model and data sizes has reshaped the AI landscape, establishing finetuning pretrained models as the standard paradigm for solving downstream tasks. However, dominant finetuning methods typically rely on weight adaptation, often lack interpretability, and depend on heuristically chosen hyperparameters.  In this paper, we take a different perspective and shift the focus from weights to activation functions, viewing them through the lens of spline operators. We propose Curvature Tuning (CT), an interpretable and principled steering method that modulates a model's decision boundary by injecting a single hyperparameter into its activation functions. We show that CT provably adjusts model decision boundary curvature and, more fundamentally, projects a model onto a space of smooth functions---thereby complementing current finetuning methods, whose effect lies primarily in feature adaptation. Making this hyperparameter trainable gives rise to a novel and highly parameter-efficient finetuning method. Empirically, CT improves both generalization and robustness. For example, it boosts downstream accuracy of ResNet-50/152 by 8.59\%/8.34\% over linear probing and 4.64\%/1.70\% over LoRA across 12 datasets, and improves robust accuracy on the $\ell_{\infty}$ benchmark from RobustBench by 1032.64\%/1494.46\%. Our code is available at https://github.com/Leon-Leyang/curvature-tuning.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，我将遵循您的要求，对给定论文进行结构化、深入且客观的中文总结。

# 论文《Curvature Tuning: Provable Training-free Model Steering From a Single Parameter》深度剖析

### 1. 核心问题与整体含义（研究动机和背景）

*   **研究动机**：当前主流的深度学习范式是微调预训练模型。然而，常用的微调方法（如全量微调、LoRA等）几乎全部聚焦于**适应模型权重**，这导致了几个关键问题：
    *   **可解释性差**：模型被视为黑盒，难以理解微调具体如何改变了模型行为。
    *   **依赖启发式超参数**：例如LoRA需要手动决定秩、放置位置、缩放因子等，缺乏理论指导。
    *   **忽视关键组件**：模型的**激活函数**——负责引入非线性并决定模型表达能力的核心组件——在很大程度上被忽视了。
*   **核心含义**：论文旨在回答“如何构建既高效又具有可解释性的微调方法？”这一问题。它提出了一种全新的视角：将目光从权重转向激活函数，通过**调节决策边界的曲率**来实现模型的引导（Steering），而不是传统的权重适应。这不仅是一种新的微调范式，也为理解模型行为提供了更深刻的理论基础。

### 2. 方法论：核心思想、关键技术细节

*   **核心思想**：该论文基于**样条算子（Spline Operator）理论**，该理论指出许多深度网络层（如ReLU， 卷积， 全连接层）可以被精确地表示为最大仿射样条算子（Max-Affine Spline Operator, MASO）。MASO的“硬”区域切换是模型非线性和复杂性的来源。因此，**通过将“硬”的区域切换过程“软化”，即可平滑决策边界，进而调节其曲率**。

*   **关键技术细节**：
    1.  **曲率调节单元（Curvature Tuning Unit, CTU）**：为实现曲率调节，论文提出了核心激活函数——CTU，它结合了两种平滑最大操作的方法：
        *   **平滑区域分配**：通过一个正则化项，用软概率分配（类似向量量化VQ的软版本）替代硬分配，这等价于使用SiLU激活函数。
        *   **平滑最大值操作**：直接用Log-Sum-Exp算子（即Softplus）替代最大值操作。
        *   **组合**：为抵消每种方法单独引入的均值偏移，CTU将两者进行了凸组合。
        *   **公式**：`φβ,c(x) = c·σ(βx/(1-β))·x + (1-c)·ln[1+exp(x/(1-β))]·(1-β)`。
        *   其中，`β ∈ [0,1]` 是核心超参数，用于调节曲率（`β=1` 时近似ReLU，`β→0` 时趋于线性）。`c ∈ [0,1]` 是混合系数，用于平衡两种平滑方式。

    2.  **两种实现方式**：
        *   **引导式CT（Steering CT, S-CT）**：将网络中所有ReLU替换为CTU，并为整个网络**共享一个固定的、可搜索的 `β` 和 `c`**。这是一种无需训练的模型引导方法，效率极高。
        *   **可训练CT（Trainable CT, T-CT）**：同样替换所有ReLU，但为**每个输出神经元的 `(β, c)` 参数分配独立的可学习参数**，并通过反向传播进行微调。这是一种新颖的、高参数效率的微调方法。

*   **理论保障**：论文从理论上证明，CT操作本质上是将原始的ReLU网络投影到一个**光滑函数空间**（Sobolev空间）中。这个新函数具有有界的梯度和非零的局部曲率，因此在保持权重不变的情况下，比原始网络具有更高的局部表达能力。变化 `β` 即可直接控制模型映射及其决策边界的曲率。

### 3. 实验设计

*   **数据集与场景**：
    *   **泛化能力**：12个不同的下游视觉数据集，包括CUB-200, Flowers102, FGVC-Aircraft, 等多个细粒度识别、纹理、医学图像等。
    *   **鲁棒性**：来自RobustBench的ℓ₂和ℓ∞对抗鲁棒性基准，以及常见损坏鲁棒性基准（CIFAR-10/100, ImageNet）。
*   **Benchmark**：主要对比方法包括：
    *   **S-CT** vs. 冻结预训练模型的**线性探针（Linear Probing）**。
    *   **T-CT** vs. **LoRA**（秩 `r=1` 为其主要对比基准，并扩展到 `r=1,2,4`）和 **线性探针**。
*   **评估指标**：分类准确率（Mean Accuracy）、对抗鲁棒性准确率（Robust Accuracy）。

### 4. 资源与算力

论文在附录中说明，实验使用了**8个RTX 3090 GPU** 和 **1个L40 GPU**。所有实验在随机种子42, 43, 44下运行。**论文未明确说明具体的训练总时长**，但对每个线性分类器、微调任务的epoch数（如20个epoch）和学习率设置等训练细节有清晰描述。

### 5. 实验数量与充分性

*   **数量**：非常充分。论文进行了大量实验来验证其方法的有效性。
    *   **模型**：在4种不同规模的模型（ResNet-18/50/152, VGG-11, Swin-T/S）上进行。
    *   **任务**：覆盖了**12个下游泛化任务**和**多个鲁棒性基准**。
    *   **消融实验**：对混合系数 `c` 的选择进行了消融研究（`c=0.5` vs. `c=0` vs. `c=1`）。
    *   **超参数敏感性**：展示了S-CT中β搜索的平滑曲线。对T-CT中学习到的β和c的分布进行了统计和分析。
    *   **公平性**：对比方法（LoRA）也进行了超参数搜索（不同秩和缩放因子）并取最佳结果。所有结果均为**三次运行的平均值和标准差**，确保了统计显著性。

*   **充分性**：实验设计客观、公平，结果稳健。不仅证明了CT的有效性，还通过理论分析和可视化（如图2的toy example）解释了其工作原理。

### 6. 主要结论与发现

1.  **有效性**：CT作为一种模型引导（S-CT）和微调（T-CT）方法，能有效提升模型的**泛化能力和鲁棒性**。
    *   在泛化任务上，T-CT显著优于线性探针，并以**更少的参数**取得了与LoRA相当甚至更好的性能。
    *   在鲁棒性上，S-CT和T-CT在ℓ∞对抗攻击下表现尤为突出，带来了**数量级的提升**。
2.  **解释性**：CT从理论上证明了其调节的是模型决策边界的曲率，这比权重适应方法更可解释。它是一种将模型投影到光滑函数空间的、有原则的方法。
3.  **互补性**：CT（作用于函数空间/光滑性）与现有PEFT方法（作用于特征/权重）是**正交且互补的**。两者可以结合使用。
4.  **局限性**：在Transformer架构（如Swin Transformer）上的应用尚不成熟。由于Transformer中的注意力机制和GELU激活函数不完全符合理论框架，T-CT的表现弱于LoRA，但仍有潜力。

### 7. 优点

*   **理论驱动与可解释性强**：从样条理论出发，提供了严谨的数学证明，解释了“为什么”和“如何”工作，这与许多启发式的PEFT方法形成鲜明对比。
*   **极致参数效率**：S-CT仅引入一个全局超参数；T-CT虽引入独立参数，但数量远少于LoRA（最低为零），同时性能更强。
*   **新颖视角**：开创性地将微调的焦点从权重转移到了激活函数，为模型微调领域开辟了一个全新的、有坚实理论基础的方向。
*   **无需训练**：S-CT版本无需任何反向传播和梯度计算，直接通过单参数搜索即可改善模型性能，计算成本极低。
*   **鲁棒性惊喜**：在没有对抗训练的情况下，CT本身就展现出一种提升模型鲁棒性的隐式偏置，这是一个非常有趣的发现。

### 8. 不足与局限

*   **在Transformer上效果有限**：对于当前最流行的Transformer架构（特别是其中使用的Softmax注意力和GELU激活函数），CT的理论保证被削弱，实际性能不如LoRA。这是最关键的局限性。
*   **缺乏大规模模型验证**：实验仅基于ResNet和VGG等中规模模型，以及Swin-T/S等小型Transformer。在更大规模的模型（如ViT-L, 7B的LLM）上的有效性尚未得到验证。
*   **对超参数 $\beta$ 和 $c$ 的敏感性分析不足**：虽然展示了搜索曲线，但并未深入讨论这些参数如何与模型深度、宽度或任务类型产生复杂交互。S-CT需要手动搜索 $\beta$，在资源受限的场景下可能构成不便。
*   **理论框架的普适性**：定理中的光滑函数投影是针对一个固定的、共享的 $\beta$ 和 $c$ 值的（对应S-CT）。对于T-CT这种每个神经元都有独立参数的情形，理论分析需要进一步拓展。

（完）
