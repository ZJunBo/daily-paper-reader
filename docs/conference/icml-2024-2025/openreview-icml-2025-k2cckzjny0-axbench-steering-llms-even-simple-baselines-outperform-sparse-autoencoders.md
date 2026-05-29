---
title: "AxBench: Steering LLMs? Even Simple Baselines Outperform Sparse Autoencoders"
title_zh: AxBench：引导大语言模型？简单基线甚至优于稀疏自编码器
authors: "Zhengxuan Wu, Aryaman Arora, Atticus Geiger, Zheng Wang, Jing Huang, Dan Jurafsky, Christopher D Manning, Christopher Potts"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=K2CckZjNy0"
tags: ["query:dg"]
score: 9.0
evidence: 对各种引导方法进行基准测试，包括激活引导，直接相关于激活引导技术
tldr: 本文提出了AxBench，一个大规模引导与概念检测基准测试，在Gemma-2模型上比较了提示工程、微调、稀疏自编码器等引导方法。结果显示，简单的提示和微调在引导效果上优于专门的可表示性引导方法，而概念检测任务中表示方法仍有效。该基准为未来引导方法提供了标准化评估平台。该工作系统比较了多种表示级引导方法，揭示了简单方法的优势，为安全对齐中的引导方法选择提供了实证依据。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-k2cckzjny0/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 772, \"height\": 579, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-k2cckzjny0/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1508, \"height\": 632, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-k2cckzjny0/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 850, \"height\": 763, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-k2cckzjny0/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 848, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-k2cckzjny0/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 887, \"height\": 664, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-k2cckzjny0/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1749, \"height\": 793, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-k2cckzjny0/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1748, \"height\": 863, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-k2cckzjny0/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1752, \"height\": 869, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-k2cckzjny0/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1755, \"height\": 1305, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-k2cckzjny0/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1580, \"height\": 1041, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-k2cckzjny0/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1755, \"height\": 1001, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-k2cckzjny0/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1589, \"height\": 478, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-k2cckzjny0/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1589, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-k2cckzjny0/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1407, \"height\": 929, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-k2cckzjny0/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1783, \"height\": 1121, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-k2cckzjny0/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 781, \"height\": 570, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-k2cckzjny0/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 781, \"height\": 569, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-k2cckzjny0/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 831, \"height\": 572, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-k2cckzjny0/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 845, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-k2cckzjny0/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1764, \"height\": 572, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-k2cckzjny0/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 847, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-k2cckzjny0/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1774, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-k2cckzjny0/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 680, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-k2cckzjny0/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1831, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-k2cckzjny0/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1776, \"height\": 766, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-k2cckzjny0/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1775, \"height\": 856, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-k2cckzjny0/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1825, \"height\": 534, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-k2cckzjny0/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1782, \"height\": 439, \"label\": \"Table\"}]"
motivation: 缺乏统一的基准来比较各种引导方法，尤其是表示级引导与简单基线的对比。
method: 构建AxBench基准，在Gemma-2模型上对提示、微调、稀疏自编码器等多种方法进行系统比较。
result: 提示和微调在引导任务上优于所有表示级方法，但概念检测仍需表示方法。
conclusion: 简单的基线与专门方法在安全相关的引导任务上具有竞争力，提示和微调是实用选择。
---

## Abstract
Fine-grained steering of language model outputs is essential for safety and reliability. Prompting and finetuning are widely used to achieve these goals, but interpretability researchers have proposed a variety of representation-based techniques as well, including sparse autoencoders (SAEs), linear artificial tomography, supervised steering vectors, linear probes, and representation finetuning. At present, there is no benchmark for making direct comparisons between these proposals. Therefore, we introduce AxBench, a large-scale benchmark for steering and concept detection, and report experiments on Gemma-2-2B and 9B. For steering,  we find that prompting outperforms all existing methods, followed by finetuning. For concept detection, representation-based methods such as difference-in-means, perform the best. On both evaluations, SAEs are not competitive. We introduce a novel weakly-supervised representational method (Rank-1 Representation Finetuning; ReFT-r1), which is competitive on both tasks while providing the interpretability advantages that prompting lacks. Along with AxBench, we train and publicly release SAE-scale feature dictionaries for ReFT-r1 and DiffMean.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：语言模型（LM）的细粒度输出引导（steering）对于安全性和可靠性至关重要。现有的方法包括提示工程（prompting）、微调（finetuning）以及可解释性研究者提出的多种基于表示的引导技术（如稀疏自编码器SAE、线性人工断层扫描LAT、监督引导向量、线性探针、表示微调等）。然而，目前缺乏一个统一的基准来直接比较这些方法。
- **整体含义**：当前引导方法的评估多为小规模、玩具级任务，无法反映真实场景。本文旨在构建一个大规模、可扩展的基准AxBench，系统性评估各类方法在概念检测（concept detection）和模型引导（model steering）两个轴上的表现，从而回答一个关键问题：基于表示的引导方法是否真正优于简单的提示和微调基线？结论是：提示和微调在引导任务上大幅领先，而表示方法中最有竞争力的ReFT-r1仍落后；在概念检测上，表示方法仍有优势。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **AxBench基准**：
  - 输入自然语言概念描述，利用LLM（gpt-4o-mini）合成标注数据，包括正例（包含概念）和负例（不包含概念），以及用于评估困难负例的对比概念。
  - 数据覆盖三个领域：text、code、math。
  - 两个评估轴：
    - **概念检测（C）**：用AUROC和F1衡量分类性能。
    - **模型引导（S）**：用LLM judge评估生成内容的概念相关度、指令遵循度和流畅度，取调和平均值作为总体分数。
- **对比的方法**：
  - 简单基线：提示工程（prompting）、全参数微调（SFT）、LoRA、LoReFT。
  - 基于表示的方法：
    - 监督字典学习（SDL）：DiffMean、PCA、LAT、线性探针（Probe）、监督引导向量（SSV）、ReFT-r1（本文提出）。
    - 无监督方法：SAE（GemmaScope预训练），以及利用标注数据选择特征的SAE-A。
    - 其他：Bag-of-Words、梯度基方法（Input×Gradient、Integrated Gradients）。
- **ReFT-r1（新颖弱监督方法）**：
  - 结合线性探针的检测目标和监督引导的生成目标，联合学习一个秩1向量w。
  - 检测：ReLU(hi·w)；引导：在top-k个检测得分最高的token上添加w，并优化语言建模损失与L1正则化。
  - 优势：兼顾检测与引导，可解释性强。

## 3. 实验设计：数据集、基准、对比方法

- **模型**：Gemma-2-2B-it 和 Gemma-2-9B-it，使用残差流表示层：2B的L10/L20，9B的L20/L31。
- **概念来源**：从GemmaScope SAE概念列表中采样500个概念（CONCEPT 500），并扩展至16K概念（CONCEPT 16K）。
- **训练数据**：每个概念144个训练样本（正负各半）；评估集约72个样本，含困难负例。
- **引导评估**：从Alpaca-Eval采样10个指令，每个概念下测试14个引导因子，优选因子并在保留集上评估。
- **对比方法**：
  - 提示、SFT、LoRA、LoReFT（非表示方法）
  - 表示方法：DiffMean、PCA、LAT、Probe、SSV、ReFT-r1、SAE、SAE-A
  - 额外：BoW、I×G、IG（仅检测）
- **消融实验**：
  - 数据规模对ReFT-r1的影响（6～144样本）
  - 类别不平衡下的F1测试
  - SAE添加vs.夹持（clamping）比较
  - 跨模型子空间线性变换（2B↔9B）
  - 更高质量概念标签对SAE与ReFT-r1的影响

## 4. 资源与算力

- 论文未明确说明训练所使用的具体GPU型号、数量及总训练时长。
- 提及使用OpenAI gpt-4o-mini生成数据（成本约$0.008/概念，144样本）。
- 训练ReFT-r1等小规模方法可在单个GPU上完成，但具体硬件未报告。
- 对于9B模型的SAE等，推理需较大显存，但未给出详细算力表。

## 5. 实验数量与充分性

- **主要实验**：在4个模型-层组合上对500个概念进行检测和引导评估，每组实验包含约500个数据点。
- **消融与扩展**：
  - 数据规模实验（6-144样本，3个随机种子）
  - 类别不平衡（增加3600负样本）
  - SAE夹持与添加对比
  - 跨模型子空间映射（2B↔9B，训练线性变换）
  - 高质量标签子集实验（~20概念）
  - CONCEPT 16K大规模训练并发布字典
- **充分性**：实验覆盖广泛，包括不同粒度、不同性能维度、不同标签质量、不同模型规模，且进行统计显著性检验（配对t检验）。但未进行跨系列模型（如Llama、Mistral）的泛化验证，且SAE仅使用GemmaScope，未对比其他训练方法。
- **公平性**：超参数对每种方法单独调优；引导因子独立选择；LLM judge与人类评价相关性达0.58，表明评估可靠。

## 6. 论文的主要结论与发现

1. **引导任务**：提示工程 > 微调（LoReFT、SFT、LoRA） > 其他表示方法。
   - 提示平均总体得分0.894，远高于SAE的0.165。
2. **概念检测**：DiffMean、Probe、ReFT-r1最优（AUROC≈0.94），SAE仅0.695，弱于多个SDL方法。
3. **SAE不具竞争力**：在检测和引导上均落后于监督方法，即使利用标注数据选择特征（SAE-A）也仅略有提升。
4. **ReFT-r1**：是唯一在检测和引导上均接近基线的表示方法，且提供可解释性优势。
5. **引导因子**：增大引导强度会降低指令遵循度（capability牺牲），ReFT-r1在Pareto前沿上表现最优。
6. **数据效率**：ReFT-r1仅需少量样本（如24个）即可达到饱和性能，成本极低。
7. **跨模型泛化**：通过学习仿射变换，2B和9B的子空间可相互映射，且检测性能几乎无损。

## 7. 优点

1. **构建了首个大规模引导基准AxBench**，支持开放词汇、长文本生成，标准化评估。
2. **提出ReFT-r1**：联合学习检测与引导，兼具高性能与可解释性，且训练成本极低。
3. **系统对比全面**：涵盖提示、微调、多种SDL、SAE、梯度法，统计检验充分。
4. **实验设计谨慎**：独立调参、因子选择、人类验证LLM judge一致性。
5. **开源贡献**：发布CONCEPT 500/16K数据集、ReFT-r1和DiffMean的大规模特征字典，支持后续研究。
6. **揭示重要insight**：简单基线（尤其是提示）在引导任务上远优于复杂表示方法，为领域发展提供清晰方向。

## 8. 不足与局限

1. **模型覆盖有限**：仅使用Gemma-2系列（2B/9B），未在Llama、Mistral等流行模型上验证，泛化性存疑。
2. **SAE标签质量影响**：使用自动标注的Neuronpedia概念，质量参差不齐。初步实验显示更高质量标签可提升SAE但无法缩小差距，但未彻底解决。
3. **评估指标依赖LLM judge**：虽有人类验证，但可能存在偏差（如偏爱特定风格）。
4. **引导因子选择可能欠优**：仅在10个指令上调优，可能遗漏更优因子；且未探索动态因子。
5. **未进行跨任务泛化**：概念均为GemmaScope预定义，未测试用户自定义概念或复杂多概念组合。
6. **计算资源未充分报告**：缺乏训练所需的具体GPU小时数，可复现性受限。
7. **微调基线限制**：SFT仅测试了前20个概念（资源限制），且全参数微调可能过拟合小数据。
8. **未探讨引导对模型整体性能的长期影响**：如能力保持率、灾难性遗忘等。

（完）
