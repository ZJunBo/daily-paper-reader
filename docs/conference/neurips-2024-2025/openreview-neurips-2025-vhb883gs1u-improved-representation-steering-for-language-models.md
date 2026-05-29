---
title: Improved Representation Steering for Language Models
title_zh: 改进的语言模型表示引导方法
authors: "Zhengxuan Wu, Qinan Yu, Aryaman Arora, Christopher D Manning, Christopher Potts"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=VHb883Gs1u"
tags: ["query:dg"]
score: 9.0
evidence: 提出无需参考的偏好引导（RePS）以改进大语言模型中的表示引导
tldr: 现有表示引导方法效果常不如提示工程。本文提出无需参考的偏好引导（RePS），通过双向偏好优化联合实现概念引导与抑制。在Gemma系列模型（2B-27B）上，RePS在AxBench基准上显著优于现有方法。该方法为语言模型的行为控制提供了更高效、更精确的表示引导手段。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1434, \"height\": 881, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1432, \"height\": 753, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 867, \"height\": 841, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1433, \"height\": 904, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1434, \"height\": 908, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1436, \"height\": 748, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1434, \"height\": 878, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 870, \"height\": 842, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1431, \"height\": 902, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1434, \"height\": 901, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 936, \"height\": 441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 938, \"height\": 707, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1293, \"height\": 605, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1151, \"height\": 659, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1011, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1434, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1139, \"height\": 888, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 872, \"height\": 967, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1428, \"height\": 1037, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 938, \"height\": 683, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1422, \"height\": 1651, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1421, \"height\": 1640, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vhb883gs1u/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1388, \"height\": 931, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1009, \"height\": 809, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 981, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1019, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1452, \"height\": 213, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1448, \"height\": 875, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 597, \"height\": 347, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1315, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1314, \"height\": 349, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1316, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1313, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1445, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1475, \"height\": 689, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1470, \"height\": 688, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1467, \"height\": 607, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1451, \"height\": 890, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 758, \"height\": 532, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1009, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vhb883gs1u/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1425, \"height\": 1139, \"label\": \"Table\"}]"
motivation: 现有表示引导方法效果有限，不如提示工程，需要更有效的引导优化目标。
method: 提出RePS，使用双向偏好优化目标，同时进行概念引导和抑制，无需参考数据。
result: 在Gemma模型上，RePS在AxBench基准上超越现有方法，实现更优的引导效果。
conclusion: RePS为语言模型的细粒度行为控制提供了有效的表示引导方法。
---

## Abstract
Steering methods for language models (LMs) seek to provide fine-grained and interpretable control over model generations by variously changing model inputs, weights, or representations to adjust behavior. Recent work has shown that adjusting weights or representations is often less effective than steering by prompting, for instance when wanting to introduce or suppress a particular concept. We demonstrate how to improve representation steering via our new Reference-free Preference Steering (RePS), a bidirectional preference-optimization objective that jointly does concept steering and suppression. We train three parameterizations of RePS and evaluate them on AxBench, a large-scale model steering benchmark. On Gemma models with sizes ranging from 2B to 27B, RePS outperforms all existing steering methods trained with a language modeling objective and substantially narrows the gap with prompting -- while promoting interpretability and minimizing parameter count. In suppression, RePS matches the language-modeling objective on Gemma-2 and outperforms it on the larger Gemma-3 variants while remaining resilient to prompt-based jailbreaking attacks that defeat prompting. Overall, our results suggest that RePS provides an interpretable and robust alternative to prompting for both steering and suppression.

---

## 论文详细总结（自动生成）

# 改进的语言模型表示引导方法（RePS）—— 中文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

语言模型（LM）的行为控制是可靠性与用户可控的关键。现有方法包括 **提示工程（prompting）** 和 **微调（fine-tuning）**，但提示工程脆弱且需要大量人工尝试，微调成本高且难以审计。**基于干预的表示引导方法**（如 steering vectors、稀疏自编码器 SAE）轻量、可解释，能在推理时操纵模型前向传播，但它们在 **AxBench** 基准上始终不如提示工程和微调。论文指出，这种差距可能源于这些方法的训练目标忽略了指导指令微调 LM 优化的人类偏好信号。早期基于偏好的引导尝试难以扩展到生产级大模型。因此，论文旨在提出一种新的偏好优化目标，以缩小基于干预的引导与提示工程之间的差距。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

论文提出 **RePS（Reference-free Preference Steering）**，一种**无参考模型的双向偏好优化目标**，建立在 **SimPO** 基础上。

- **核心思想**：训练一个低秩干预函数 Φ（如 steering vector、LoRA、LoReFT），使其在**正向引导**（positive steering）时提高引导输出（steered response）的似然，在**负向引导**（negative steering）时抑制概念（即让模型避免生成包含该概念的内容）。RePS 是双向的，且不依赖参考模型（reference-free）。

- **关键公式与流程**（文字说明）：
  - 给定训练数据集 \( D_{train} = \{ (x_i, y_i, y_i^c) \} \)，其中 \( x_i \) 是指令，\( y_i \) 是原始响应，\( y_i^c \) 是包含引导概念的响应。
  - **正向引导**：定义 \(\Delta^+_\Phi = \frac{\beta_+}{|y^c|} \log p_\Phi(y^c | x, h_l \leftarrow \Phi_{Steer}) - \frac{1}{|y|} \log p_\Phi(y | x, h_l \leftarrow \Phi_{Steer})\)，其中 \(\beta_+ = \max(\log p(y|x) - \log p(y^c|x), 1)\) 用于加权引导响应的似然。
  - **负向引导**：定义 \(\Delta^-_\Phi = \frac{\beta_-}{|y|} \log p_\Phi(y | x, h_l \leftarrow \Phi_{Null}) - \frac{1}{|y^c|} \log p_\Phi(y^c | x, h_l \leftarrow \Phi_{Null})\)，其中 \(\Phi_{Null}\) 通过**正交否定**（projection nulling）消除沿引导方向的信息：\(\Phi_{Null}(h_l) = h_l - \text{ReLU}(h_l \cdot w_1) / \|w_1\|^2 \cdot w_1\)。
  - **最终损失**：\(\min_\Phi \{ -\mathbb{E}_{(x,y,y^c) \sim D_{train}} [\log \sigma(\Delta^+_\Phi) + \log \sigma(\Delta^-_\Phi)] \}\)。使用 sigmoid 函数转化为二元分类损失。

- **干预参数化**：
  - **Steering Vector (SV)**：秩-1 向量，\(\Phi_{SV}(h_l, \alpha) = h_l + \alpha \cdot w_1 + b_1\)。
  - **LoRA**：低秩适配，\(\Phi_{LoRA}(x_l, \alpha) = x_l w_M + \alpha \cdot x_l w_1 w_2^\top\)。
  - **LoReFT**：表示微调，\(\Phi_{LoReFT}(h_{lT}, \alpha) = h_{lT} + \alpha \cdot (h_{lT} w_1 + b - h_{lT} w_2) w_2^\top\)。

训练时采用**因子采样技巧**（factor sampling trick），在训练过程中随机采样引导因子 α，稳定训练并简化超参数调优。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：基于 **AxBench** 的 **CONCEPT 500** 子集，包含 500 个概念，每个概念有 144 个训练样本。论文将其扩充为偏好对数据集（72 对/概念）。使用 GPT-4o-mini 生成引导响应。针对 Gemma-3 大模型，额外构建了 D100 子集（100 个概念）并改进了指令采样（避免分布偏移）。
- **基准**：AxBench 评测协议，使用三个指标：**概念分数**（concept score，0-2）、**指令遵循分数**（instruct score）、**流畅度分数**（fluency score），三者调和平均作为总体分数。
- **对比方法**：
  - **提示工程（Prompting）**：使用远程 LM 生成系统提示。
  - **基于干预的方法**：SV、LoRA、LoReFT 三种参数化，分别使用三种训练目标：
    - **语言建模目标（Lang.）**：标准交叉熵损失。
    - **双向偏好优化（BiPO）**：Cao et al. (2024) 提出的参考模型依赖的偏好目标。
    - **RePS（本文）**。
- **语言模型**：Gemma-2（2B, 9B）和 Gemma-3（12B, 27B），均为指令微调版本。
- **评估场景**：
  - **概念引导（Concept Steering）**：正向引导，让模型输出包含概念。
  - **概念抑制（Concept Suppression）**：负向引导，抑制概念出现。
  - **抑制下的攻击鲁棒性**：指令遵循攻击（用户明确要求忽略系统提示）和多次攻击（many-shot jailbreaking，上下文窗口内多次示例）。使用 20 个基于规则的 IFEval 风格概念。

## 4. 资源与算力

论文在 **NVIDIA RTX A6000 (49GB)、A100-SXM4-80GB、H200 (143.8GB)** 上实验。Gemma-2 实验使用 A6000 或 A100；Gemma-3 使用 A100 或 H200。每个概念训练约 5-8 分钟；推理（最大 128 或 768 tokens）<5 分钟或 5-10 分钟。整体超参数调优约 1000 个单独运行。论文未给出 GPU 总数或总 GPU 小时数，但提到训练一个 steering vector 成本 <$0.01（含数据生成）。算力披露较为充分。

## 5. 实验数量与充分性

- **实验数量**：包含 4 种模型大小（2B/9B/12B/27B）× 3 种干预方法 × 3 种训练目标（部分组合因性能不佳而省略 BiPO），以及多个子数据集（D2B L10/L20, D9B L20/L31, D100）。此外，抑制实验包括规则概念和攻击场景。总计数百组实验。
- **公平性**：对每种方法-目标对进行**预算控制的超参数搜索**（Gemma-2: 72 个配置；Gemma-3: 168 个配置），确保同一计算资源下比较。使用同一组超参数网格，选择最优配置。
- **充分性**：涵盖了基本引导、概念抑制、对抗鲁棒性，并对比了最先进的偏好目标 BiPO 和标准语言建模。消融实验包括因子采样技巧、生成长度影响等。实验设计较为全面，但作者承认 LoReFT 在 27B 模型上失败，可能因超参数未充分搜索。整体而言，实验充分、客观。

## 6. 论文的主要结论与发现

1. **RePS 显著优于现有方法**：在所有 Gemma 模型上，RePS 训练的干预方法（尤其是 SV）一致优于语言建模目标和 BiPO，大幅缩小了与提示工程的差距。
2. **概念抑制**：RePS 训练的 SV 在概念抑制上，对 Gemma-2 模型与语言建模目标持平，在 Gemma-3 大模型上表现更好。
3. **对抗鲁棒性**：在指令遵循攻击和多次攻击下，基于干预的抑制（RePS）比提示工程更鲁棒，不易被提示绕过。特别是长上下文攻击中，RePS 与追加系统提示（append）性能相当，但避免了系统提示泄露问题。
4. **可扩展性**：RePS 在所有模型规模（2B-27B）上均有效，且 SV 参数最少（秩-1），效率最高。
5. **因子采样技巧关键**：稳定训练，简化超参数调优。
6. **LoRA 和 LoReFT 性能不如 SV**，尤其是大模型，LoReFT 在 27B 上几乎失效，表明线性表示假设在抑制任务中更有效。

## 7. 优点

- **方法创新性**：提出无参考模型的双向偏好优化，克服了 BiPO 依赖参考模型且不适用于非常规引导行为的缺点。
- **全面且公平的实验**：涵盖多种模型大小、干预参数化和训练目标，执行严格的超参数预算控制，结果可信。
- **实际意义**：提供了一种可解释、参数高效、鲁棒的替代 prompting 的方案，特别适用于安全对齐和概念抑制。
- **因子采样技巧**简单有效，可推广到其他基于调整因子的干预方法。
- 代码和数据集将开源，促进复现。

## 8. 不足与局限

- **干预方法间性能差异未充分解释**：LoRA 和 LoReFT 在抑制任务中表现一般，尤其是 LoReFT 在 27B 上几乎失效，论文未提供足够深入的分析。
- **数据集限制**：AxBench 的 CONCEPT 500 数据集可能不是最优训练数据，其指令采样存在分布偏移（如数学指令来自 GSM8K，测试是 AlpacaEval），导致训练-测试不匹配。论文虽对 Gemma-3 做了改进，但仍可能影响结果。
- **未探索自举训练**：未使用目标 LM 自身生成训练样本，可能限制收敛。
- **与提示工程的比较尚不全面**：未充分对比提示工程的所有变体（如 少样本、思维链等）。
- **计算资源有限**：较大的超参数搜索（1000+ 运行）虽已尽力，但 LoReFT 等可能仍被低估，因为未找到最佳参数。
- **缺乏对人机交互中实际应用场景的评估**（如用户偏好、多轮对话）。
- **论文主要关注概念级引导，未验证更复杂的行为或技能引导**。

（完）
