---
title: Does Low Rank Adaptation Lead to Lower Robustness against Training-Time Attacks?
title_zh: 低秩适配是否导致对训练时攻击的鲁棒性降低？
authors: "Zi Liang, Haibo Hu, Qingqing Ye, Yaxin Xiao, RongHua Li"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=l6uwlGANSz"
tags: ["query:smd"]
score: 6.0
evidence: 研究LoRA对数据投毒攻击的鲁棒性，与有害微调防御相关
tldr: 论文理论分析了低秩适配（LoRA）微调在面对数据投毒和后门攻击时的鲁棒性。通过神经正切核和信息论框架建模训练动态，揭示了低秩结构如何影响安全性。尽管不直接提出防御方法，但为理解有害微调攻击下的安全退化提供了理论基础，有助于设计更鲁棒的微调策略。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-l6uwlgansz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1698, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-l6uwlgansz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1700, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-l6uwlgansz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 747, \"height\": 635, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-l6uwlgansz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1767, \"height\": 408, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-l6uwlgansz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1772, \"height\": 407, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-l6uwlgansz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1652, \"height\": 946, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-l6uwlgansz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1651, \"height\": 939, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-l6uwlgansz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1646, \"height\": 936, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-l6uwlgansz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1647, \"height\": 899, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-l6uwlgansz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1641, \"height\": 891, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-l6uwlgansz/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1740, \"height\": 980, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-l6uwlgansz/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1739, \"height\": 985, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-l6uwlgansz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1182, \"height\": 450, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-l6uwlgansz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1723, \"height\": 620, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-l6uwlgansz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 636, \"height\": 353, \"label\": \"Table\"}]"
motivation: LoRA在微调中广泛使用，但其对训练时攻击的鲁棒性尚未充分研究，存在安全风险。
method: 构建分析框架，利用神经正切核简化训练过程，并应用信息论建立安全边界。
result: 揭示了低秩结构在数据投毒场景下的脆弱性，并给出了理论解释。
conclusion: LoRA的鲁棒性受低秩结构影响，需谨慎选择微调超参数以避免安全风险。
---

## Abstract
Low rank adaptation (LoRA) has emerged as a prominent technique for fine-tuning large language models (LLMs) thanks to its superb efficiency gains over previous methods. While extensive studies have examined the performance and structural properties of LoRA, its behavior upon training-time attacks remain underexplored, posing significant security risks. In this paper, we theoretically investigate the security implications of LoRA's low-rank structure during fine-tuning, in the context of its robustness against data poisoning and backdoor attacks. We propose an analytical framework that models LoRA’s training dynamics, employs the neural tangent kernel to simplify the analysis of the training process, and applies information theory to establish connections between LoRA's low rank structure and its vulnerability against training-time attacks. Our analysis indicates that LoRA exhibits better robustness to backdoor attacks than full fine-tuning, while becomes more vulnerable to untargeted data poisoning due to its over-simplified information geometry. Extensive experimental evaluations have corroborated our theoretical findings.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：低秩适配（LoRA）已成为微调大语言模型的主流参数高效微调（PEFT）方法，但其安全风险（特别是对训练时攻击的鲁棒性）尚未得到充分研究。已有工作常将 LoRA 作为攻击工具，而非探讨其自身固有的安全脆弱性。
- **核心问题**：LoRA 的低秩结构是否会导致其比全微调（FF）更容易受到训练时攻击？具体而言，本文同时考虑**无目标数据投毒攻击（UPA）**和**后门攻击（BPA）**两种典型训练时攻击场景。
- **整体含义**：首次从理论层面揭示了 LoRA 在安全性上的双刃剑效应——LoRA 对后门攻击更鲁棒，但对无目标数据投毒更脆弱。这为安全使用 LoRA 提供了指导。

## 2. 论文提出的方法论

- **核心思想**：通过构建分析框架，将训练时鲁棒性（TTR）的度量转化为基于神经正切核（NTK）的简化形式，并引入信息几何（Fisher 信息、Rényi 熵）来桥街模型结构与攻击敏感性。
- **关键技术细节**：
  1. 定义 TTR 指标 \(M' = \| \mathbb{E}_{(x_c, \tilde{x}_c)} K_{\text{ntk}}(x_c, \tilde{x}_c) \|\)，利用 NTK 在无限宽下的两个性质（确定性极限核、训练中保持不变）消除对训练步长 t 的依赖。
  2. 推导 LoRA 和 FF 的 NTK 表达式（Lemma 3.1），并在 OOLD（仅一层不同）假设下证明两者关系：\(K_{\text{LoRA}}^{(l)} = K_{\text{FF}}^{(l)} + \Delta_r^{(l)}\)，其中 \(\Delta_r^{(l)}\) 的核矩阵 \(M_\Delta^{(l)} = A^{(l)T}A^{(l)} - I\) 在特定条件下（秩 \(r \leq n_{l-1}\)，初始化方差 \(\sigma_a^2 < 1/n_{l-1}\)）是负半定的。
  3. 基于 Fisher 信息矩阵与 NTK 的关系（Theorem 2.2），比较 LoRA 和 FF 的信息比特（IB）和 Rényi 熵（\(H_\alpha\)），证明在相同条件下 \(IB_{\text{LoRA}} \leq IB_{\text{FF}}\) 且 \(H_{\alpha,\text{LoRA}} \leq H_{\alpha,\text{FF}}\)（Theorem 3.6）。
  4. 从正交性视角解释：后门攻击希望梯度对齐（增大内积），而 LoRA 更平滑的信息几何缩小了搜索空间，因此更鲁棒；无目标投毒希望梯度对齐，LoRA 的简化曲面反而使其更敏感。
- **公式/算法流程**：论文用数学推导而非算法伪代码。核心是基于 NTK 的梯度相似性分析和信息几何特征值分析。

## 3. 实验设计

- **数据集与场景**：使用 GLUE 基准中的六个二分类任务（**SST-2、COLA、QNLI、QQP、RTE、MRPC**）。主实验包含四个任务（SST-2、COLA、QNLI、QQP）。
- **基准方法**：对比**全微调（Full Fine-tuning, FF）**与**LoRA 微调**。
- **攻击设置**：
  - **无目标投毒攻击（UPA）**：随机翻转标签，投毒率从 0.05 到 0.35（或更高）。
  - **后门攻击（BPA）**：向样本添加触发词 `[.*?]` 并将标签改为 1，投毒率从 0.001 到 0.0045。
- **额外攻击**：补充了四种后门攻击（CL-BPA、IL-BPA、MT、S-BPA）以及生成式语言模型上的实验（BadNet、SA、VPI）。
- **超参数**：最大序列长度 512，batch size 8，LoRA 学习率 3e-5，FF 学习率 3e-6，训练步数 10,000。LoRA 默认 rank=8，α=16。

## 4. 资源与算力

- **明确说明**：所有实验在 **8 块 24 GB Nvidia RTX 4090 GPU** 上运行。每个实验重复 5 次取均值和标准差。
- 未提及总训练时间或 GPU 小时数。

## 5. 实验数量与充分性

- **数量**：主实验在 4 个数据集上分别测试 UPA 和 BPA（各约 8 种投毒率），共约 64 组对比；消融实验涵盖 rank（4~512，约 8 个值）和初始化方差（0.1~2.0，约 8 个值），每个数据集重复，约 100+ 组；额外攻击 4 种；生成式语言模型实验 3 种攻击。
- **充分性**：实验设计较全面，覆盖了不同攻击类型、不同超参数、不同初始化策略，且使用了多种指标（Acc、Pre、Rec、F1）。但主要限于 BERT-large 和 GLUE 任务，少量生成式实验仅用 LLaMA-3.2-3B，架构多样性有限。另外，实验全部基于英文 NLP 任务，未涉及视觉或多模态。
- **客观公平**：超参数经过调优以确保稳定收敛，重复 5 次报告标准差，实验公平性较好。

## 6. 论文的主要结论与发现

1. **LoRA 对后门攻击更鲁棒**：在所有数据集上，LoRA 在后门投毒下的准确率普遍高于 FF（图 2、图 7、表 1 等）。
2. **LoRA 对无目标数据投毒更脆弱**：LoRA 在投毒下的性能下降幅度大于 FF（图 1、图 6）。
3. **秩（rank）是关键影响因素**：高秩（如 64~512）能提高对无目标投毒的鲁棒性，但会降低对后门的抵抗能力；低秩则相反（图 4、图 9、图 10）。
4. **初始化方差主要影响后门鲁棒性**：较小的初始化方差（如默认 1/(3n)）可提高后门防御，对无目标投毒影响较小（图 5、图 11、图 12）。论文指出这与 NTK 理论的预测部分吻合（方差影响不如秩显著）。
5. **全秩 LoRA 在特定条件下与 FF 等价**（Corollary 3.5）：当 rank = 隐层维度且方差 = 1/n 时，NTK 等价，从而 TTR 也等价。
6. **实际建议**：在满足性能的前提下，应尽可能选择低秩和小的初始化方差以增强后门防御；需权衡无目标投毒风险。

## 7. 优点

- **理论创新**：首次将 NTK 与信息几何结合用于分析 LoRA 的安全性，给出了严格的数学推导（包括 Fisher 信息、Rényi 熵）和可验证的定理。
- **双刃剑视角**：揭示了 LoRA 对不同攻击类型的差异化影响，并提供了正交性解释，深化了对 PEFT 安全性的理解。
- **实验验证充分**：从多种数据集、多种攻击、多种超参数角度验证了理论预测，并额外做了生成式模型和更多初始化策略的补充实验。
- **实用指导**：提出的安全使用建议（如控制秩和方差）对实践有直接价值。

## 8. 不足与局限

- **NTK 假设的局限性**：理论基于无限宽网络假设，实际有限宽网络可能偏离 NTK 预测（论文在附录 D 提到 Malladi 等人的实验表明 LoRA 仍在 NTK 区域内，但缺乏严格证明）。
- **初始化方差影响的理论预测不完全吻合**：论文承认对于无目标投毒，方差的影响不如秩显著，这可能是由于 NTK 在训练中变化导致，但未提供更深入的解决方案。
- **架构多样性不足**：主要实验仅在 BERT-large 上完成，生成式模型实验仅用 3B 参数 LLaMA，未在更大模型（如 LLaMA-7B、GPT 系列）上验证，结论的泛化性存疑。
- **攻击类型覆盖**：虽已覆盖主流方法，但训练时攻击还包括模型窃取、成员推断等，未涉及。
- **对比基线的局限性**：仅对比全微调，未对比其他 PEFT 方法（如 Adapter、Prompt Tuning）在相同攻击下的表现。
- **实验细节**：部分消融实验（如 RTE、MRPC）未在正文展示，仅在附录补充，可能影响结论的完整性。

（完）
