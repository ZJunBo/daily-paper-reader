---
title: "Safe LoRA: The Silver Lining of Reducing Safety Risks when Finetuning Large Language Models"
title_zh: Safe LoRA：微调大语言模型时减少安全风险的一线希望
authors: "Chia-Yi Hsu, Yu-Lin Tsai, Chih-Hsun Lin, Pin-Yu Chen, Chia-Mu Yu, Chun-Ying Huang"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=HcifdQZFZV"
tags: ["query:smd"]
score: 6.0
evidence: 关注LoRA微调时安全风险的降低
tldr: 该论文研究参数高效微调（LoRA）对大语言模型安全性的影响，发现即使使用无恶意数据，微调仍会削弱安全对齐。Safe LoRA通过分析LoRA微调中的安全风险机制，提出了一种减少安全退化的方法，在保持微调性能的同时有效降低了模型被越狱的概率。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-hcifdqzfzv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1435, \"height\": 619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hcifdqzfzv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1394, \"height\": 353, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hcifdqzfzv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 663, \"height\": 505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hcifdqzfzv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 614, \"height\": 504, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcifdqzfzv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 985, \"height\": 205, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcifdqzfzv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1443, \"height\": 474, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcifdqzfzv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1443, \"height\": 620, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcifdqzfzv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1475, \"height\": 312, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcifdqzfzv/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1293, \"height\": 158, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcifdqzfzv/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1412, \"height\": 469, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcifdqzfzv/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 976, \"height\": 157, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcifdqzfzv/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1442, \"height\": 350, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcifdqzfzv/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1441, \"height\": 365, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcifdqzfzv/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1441, \"height\": 366, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcifdqzfzv/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1157, \"height\": 326, \"label\": \"Table\"}]"
motivation: 参数高效微调（LoRA）虽然降低了资源需求，但同样会导致模型安全性下降。
method: 分析LoRA微调中安全退化的原因，并提出针对性的安全增强策略。
result: 在多种基准测试上，Safe LoRA在几乎不影响下游任务性能的前提下显著提升了模型安全性。
conclusion: 参数高效微调的安全性同样需要关注，所提方法为LoRA的安全使用提供了保障。
---

## Abstract
While large language models (LLMs) such as Llama-2 or GPT-4 have shown impressive zero-shot performance, fine-tuning is still necessary to enhance their performance for customized datasets, domain-specific tasks, or other private needs. However, fine-tuning all parameters of LLMs requires significant hardware resources, which can be impractical for typical users. Therefore, parameter-efficient fine-tuning such as LoRA have emerged, allowing users to fine-tune LLMs without the need for considerable computing resources, with little performance degradation compared to fine-tuning all parameters. Unfortunately, recent studies indicate that fine-tuning can increase the risk to the safety of LLMs, even when data does not contain malicious content. To address this challenge, we propose $\textsf{Safe LoRA}$, a simple one-liner patch to the original LoRA implementation by introducing the projection of LoRA weights from selected layers to the safety-aligned subspace, effectively reducing the safety risks in LLM fine-tuning while maintaining utility. It is worth noting that $\textsf{Safe LoRA}$ is a training-free and data-free approach, as it only requires the knowledge of the weights from the base and aligned LLMs. Our extensive experiments demonstrate that when fine-tuning on purely malicious data, $\textsf{Safe LoRA}$ retains similar safety performance as the original aligned model. Moreover, when the fine-tuning dataset contains a mixture of both benign and malicious data,  $\textsf{Safe LoRA}$ mitigates the negative effect made by malicious data while preserving performance on downstream tasks.  Our codes are available at https://github.com/IBM/SafeLoRA.

---

## 论文详细总结（自动生成）

# Safe LoRA 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）在参数高效微调（如 LoRA）后，即使使用良性数据，也可能导致安全对齐（safety alignment）显著退化，使得模型更容易生成有害或不适当的输出。这一问题在纯恶意数据微调时尤为严重。
- **研究动机**：现有的安全对齐方法（如 RLHF、指令微调）虽然在预训练后赋予模型安全护栏，但在后续微调过程中这些护栏极易被削弱。用户出于定制化需求进行微调时，无意中可能引入安全风险。因此，需要一种轻量、无需额外训练数据的方法，在保持微调性能的同时保留模型的安全性。
- **整体含义**：本文提出 Safe LoRA，通过对 LoRA 权重进行后处理投影，将模型权重引导至安全对齐子空间，从而抑制安全退化，且不依赖任何恶意样本或额外训练，具有即插即用的实用性。

## 2. 论文提出的方法论

- **核心思想**：利用一对“未对齐模型”和“对齐模型”的权值差异（称为对齐矩阵 $V = W_{\text{aligned}} - W_{\text{unaligned}}$）来刻画安全相关的方向。在 LoRA 微调后，对每个层的 LoRA 更新权重 $\Delta W = AB^T$，计算其与经过投影后的权重 $C \Delta W$ 的相似度（余弦相似度）。若相似度低于阈值 $\tau$，则用投影后的权重替换原 LoRA 权重，从而将更新限制在安全对齐子空间内。
- **关键技术细节**：
  - **对齐矩阵构造**：对于每一层 $i$，定义 $V_i = W_i^{\text{aligned}} - W_i^{\text{unaligned}}$。可选精确投影矩阵 $\hat{C}_i = V_i(V_i^T V_i)^{-1} V_i^T$ 或近似版本 $C_i = V_i V_i^T / \|V_i\|_F$（后者计算更快，约快250倍）。
  - **投影决策**：计算 $\cos(\hat{C}_i\Delta W_i, \Delta W_i)$ 或 $\cos(C_i\Delta W_i, \Delta W_i)$，若小于阈值 $\tau$，则令 $\Delta W_i \leftarrow \hat{C}_i \Delta W_i$（或 $C_i \Delta W_i$）。否则保持不变。
  - **理由**：认为权值空间存在结构化子空间，投影操作将 LoRA 更新限制在安全相关子空间与低秩解空间的交集，从而兼顾安全与性能。
- **公式与算法流程**（文字说明）：
  - 输入：未对齐模型权重 $W_{\text{unaligned}}$、对齐模型权重 $W_{\text{aligned}}$、LoRA 更新权重 $\Delta W$。
  - 对每一层 $l$：计算 $V_l$，构造投影矩阵 $C_l$；计算相似度；若相似度低于阈值，则将 $\Delta W_l$ 替换为 $C_l \Delta W_l$；否则保留原值。
  - 最终将修改后的 LoRA 权重应用于对齐模型。

## 3. 实验设计

- **数据集**：
  - **PureBad**：100 个纯有害样本（来自 red-teaming），用于极端恶意场景。
  - **Dialog Summary**：从 SAMSum 数据集随机选取 1000 个正常样本，混合 100 个有害样本（共 1100 条训练数据），模拟混合数据场景。测试集 200 条。
  - **Alpaca**：50,098 条指令数据（无有害样本），用于验证良性数据微调是否降低安全性。
- **基准（Benchmark）**：
  - **安全性**：使用 11 类有害类别（合并 OpenAI 和 Meta 政策），用 GPT-4 评判危害分数（1~5，越低越安全）；攻击成功率（ASR）定义为不包含拒绝关键词的响应比例。
  - **效用**：Dialog Summary 用 Rouge-1 F1；PureBad 和 Alpaca 用 MT-Bench（1~10，越高越好）。
- **对比方法**：
  - **原生 LoRA**（无防御）
  - **SafeInstr**：在训练集加入 3% 安全指令样本。
  - **BEA（Backdoor Enhanced Alignment）**：加入后门样本，触发时输出安全指令。
  - **Vaccine**（在消融实验中对比）。
- **模型**：Llama-2-7B-Chat、Llama-3-8B-Instruct、Gemma（部分实验）。

## 4. 资源与算力

- 论文明确说明：所有实验在 **NVIDIA H100 80GB GPU** 和 **AMD Epyc 7313 16-core processor × 64** 机器上完成。
- 训练时间未单独给出，但提到生成近似投影矩阵 $C$ 需 8.6×10⁻³ 秒/层，而精确投影 $\hat{C}$ 需 2.1714 秒/层（慢约 250 倍）。
- 投影过程：逐层加载至 GPU，无需同时加载全部权重，因此资源消耗可控。

## 5. 实验数量与充分性

- **主要实验数量**：
  - 在 Llama-2 和 Llama-3 上分别针对 PureBad、Dialog Summary、Alpaca 三个数据集，对比原生 LoRA、SafeInstr、BEA 以及 Safe LoRA，共约 3×3×3 = 27 组主实验（不含不同超参数）。
  - 消融实验：阈值对效用和安全的影响（图3）、相似度分布（图4）、不同投影矩阵（C vs Ĉ）对比、全参数微调实验、Gemma 模型验证、不同有害数据比例（10%/30%/50%）实验、与 Vaccine 对比。
- **充分性与客观性**：
  - 覆盖了纯恶意、混合、良性三种数据场景，验证了方法的通用性。
  - 对比了两种主流防御方法（SafeInstr、BEA）以及近期工作（Vaccine），基准充分。
  - 消融实验系统探索了投影层数（阈值）的影响，揭示了安全-效用权衡。
  - 在 Llama-2、Llama-3、Gemma 三种不同架构上验证，证明了模型无关性。
  - 使用 GPT-4 作为评判者可能存在偏差，但作者采用了广泛使用的基准（Qi et al. ICLR 2024），且对比方法在同一条件下评估，相对公平。
  - 值得注意：缺少对更大规模模型（如 13B/70B）的验证，且未讨论投影操作对推理速度的影响。

## 6. 论文的主要结论与发现

- Safe LoRA 在纯恶意数据微调下，能将危害分数降低至几乎与原始对齐模型持平（Llama-2: 1.055 vs 1.058），同时 MT-Bench 分数保持 6.34，远优于原生 LoRA（4.54）和其他防御方法（SafeInstr: 5.74, BEA: 5.87）。
- 在混合数据（Dialog Summary）场景下，Safe LoRA 的 Rouge-1 F1 约 49.79%（仅比无防御的 50.66% 低不到 1%），危害分数从 2.63 降至 1.30，远低于 SafeInstr（1.32）和 BEA（1.48）。
- 在纯良性数据（Alpaca）上，Safe LoRA 同样有效（危害分数从 2.25 降至 1.09，MT-Bench 5.62），而 SafeInstr 和 BEA 效果不佳。
- 投影层数与模型的对齐强度相关：Llama-2-7B-Chat 仅需投影约 11% 的层数，Llama-3-8B-Instruct 则需要约 35%。
- 近似投影矩阵 $C$ 在速度上远优于精确矩阵 $\hat{C}$，且性能几乎无损失。

## 7. 优点

- **无需额外数据**：仅依赖基础模型（Base）与对齐模型（Chat）的公开权重，无需收集任何安全样本或有害样本，部署便捷。
- **无需训练**：直接在已有 LoRA 权重上执行一次投影操作，不改变模型微调过程，计算开销极低。
- **即插即用**：可作为一个“一键补丁”添加到现有 LoRA 代码中，兼容性强。
- **模型无关**：在 Llama-2、Llama-3、Gemma 上均有效，说明方法具有通用性。
- **安全-效用权衡可控**：通过调节相似度阈值 $\tau$ 或投影层数 K，可灵活平衡安全性与下游任务性能。
- **可扩展至全参数微调**：实验表明对全参数微调同样有效（Table 5）。

## 8. 不足与局限

- **自适应攻击风险**：作者在局限性中明确指出，该方法可能被未来的自适应攻击绕过（例如攻击者可能针对投影机制设计恶意数据）。
- **阈值选择依赖具体任务和模型**：需要用户手动调节或预设投影层数，缺乏自适应选择规则；论文中仅提供经验值（如 0.35 阈值对应 7 层），泛化指导有限。
- **仅验证了中等规模模型**：实验限于 7B/8B 级别，未在更大模型（如 13B、70B）或更小模型上验证，可能导致结论的局限性。
- **评估依赖 GPT-4 作为判官**：GPT-4 本身可能具有偏见，且危害分数定义较粗（1-5），可能无法精细刻画安全差异。
- **未讨论对模型鲁棒性、激活分布的影响**：投影操作可能改变模型内部表示，论文未分析对模型其他能力（如事实性、推理）的影响。
- **实验设计未控制随机种子重复**：未报告误差棒（如标准差），单次运行结果可能受随机性影响；但考虑到计算资源，这在 LLM 领域较为常见。
- **未与其他参数高效微调方法（如 Adapter、Prefix Tuning）对比**：论文仅聚焦 LoRA，但安全退化问题在多种 PEFT 方法中均存在，缺乏跨方法比较。

（完）
