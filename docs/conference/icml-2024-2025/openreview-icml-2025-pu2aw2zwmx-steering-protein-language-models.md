---
title: Steering Protein Language Models
title_zh: 引导蛋白质语言模型
authors: "Long-Kai Huang, Rongyi Zhu, Bing He, Jianhua Yao"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=pu2aw2zwMx"
tags: ["query:dg"]
score: 8.0
evidence: 应用激活引导技术控制蛋白质语言模型输出，与激活引导技术直接相关
tldr: 该论文研究了将激活引导技术从大语言模型迁移到蛋白质语言模型的可能性，旨在精确控制蛋白质序列生成。作者提出了一种简单的激活编辑方法，并设计了编辑位点识别模块来优化蛋白质。实验表明该方法能有效地引导模型生成具有目标特性的蛋白质序列。该工作不仅拓展了激活引导的应用范围，也为生物分子设计提供了新工具。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-pu2aw2zwmx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 813, \"height\": 487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pu2aw2zwmx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1751, \"height\": 768, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pu2aw2zwmx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1678, \"height\": 976, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pu2aw2zwmx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1671, \"height\": 975, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-pu2aw2zwmx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1761, \"height\": 456, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pu2aw2zwmx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1773, \"height\": 463, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pu2aw2zwmx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1767, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pu2aw2zwmx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1768, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pu2aw2zwmx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1771, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pu2aw2zwmx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1253, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pu2aw2zwmx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1737, \"height\": 338, \"label\": \"Table\"}]"
motivation: 现有蛋白质语言模型难以输出具有精确指定功能的序列，需要有效的控制方法。
method: 采用激活编辑技术，通过编辑特定层激活值来引导模型输出，并设计位点识别模块提升优化效果。
result: 在蛋白质优化任务上取得了有效结果，表明激活引导可迁移至蛋白质领域。
conclusion: 激活引导是控制蛋白质语言模型输出的有效方法，为蛋白质设计提供了新思路。
---

## Abstract
Protein Language Models (PLMs), pre-trained on extensive evolutionary data from natural proteins, have emerged as indispensable tools for protein design. While powerful, PLMs often struggle to produce proteins with precisely specified functionalities or properties due to inherent challenges in controlling their outputs. 
In this work, we investigate the potential of Activation Steering, a technique originally developed for controlling text generation in Large Language Models (LLMs), to direct PLMs toward generating protein sequences with targeted properties. We propose a simple yet effective method that employs activation editing to steer PLM outputs, and extend this approach to protein optimization through a novel editing site identification module. Through comprehensive experiments on lysozyme-like sequence generation and optimization, we demonstrate that our methods can be seamlessly integrated into both auto-encoding and autoregressive PLMs without requiring additional training. These results highlight a promising direction for precise protein engineering using foundation models.
Code is available at <https://github.com/Long-Kai/Steering-PLMs>.

---

## 论文详细总结（自动生成）

# 论文总结：《Steering Protein Language Models》

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：蛋白质语言模型（PLMs）能够从海量自然蛋白质序列中学习进化信息，在蛋白质设计任务中表现优异。然而，现有PLMs难以直接生成具有精确指定功能或属性（如热稳定性、溶解度、荧光亮度）的蛋白质序列。传统控制方法（如微调或标签引导）需要大量高质量标注数据和计算资源，且可能破坏预训练知识，缺乏灵活性。
- **整体含义**：本文首次探索将大语言模型（LLMs）中的激活引导（Activation Steering）技术迁移到蛋白质语言模型中，旨在无需重新训练的情况下，通过推理时修改模型内部激活来引导PLMs生成具有目标属性的蛋白质序列，并进一步扩展到蛋白质优化任务。该工作为精确蛋白质工程提供了新范式。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：激活引导基于一个假设——PLMs内部表示已隐含目标属性知识，但输出未充分体现。通过计算对比蛋白质集合（具有/不具有目标属性）的激活差异作为引导向量，并在推理时将其加到模型各层激活上，可偏置生成方向。
- **关键技术细节**：
  - **引导向量计算**：
    - 对于自编码PLMs（如ESM2、ESM3）：使用所有token平均激活的均值差。
    - 对于自回归PLMs（如ProLLaMA）：使用最后一个token激活的均值差。
    - 公式：`v_l = (1/|P|) Σ_{xp∈P} h_l^{avg}(xp) - (1/|N|) Σ_{xn∈N} h_l^{avg}(xn)`（AE）；类似地对于AR。
  - **激活编辑**：每层激活修改为 `˜h_l = h_l + α v_l`，并对修改后激活进行归一化（保持与原始激活相同范数）。α为引导强度超参数。
  - **蛋白质优化框架（ASPO）**：
    - 针对自编码PLMs的序列优化任务。
    - 步骤：① 选取最具信息性的层（通过训练线性分类器区分正负样本的验证准确率确定）；② 计算每个token表示与引导向量的余弦相似度作为相关性分数；③ 选择分数最低的T个token作为突变位点；④ 掩码这些位点，利用激活引导预测新氨基酸。重复R轮。
    - 算法流程：Algorithm 1（详见原文3.3节）。

## 3. 实验设计：使用的数据集/场景、benchmark、对比方法

- **场景与数据集**：
  - **蛋白质生成任务**：生成溶菌酶样（lysozyme-like）蛋白质，目标属性为热稳定性（Tm>70°C）或溶解度（可溶概率>0.8）。使用UniRef50中溶菌酶样序列，通过属性预测器（基于ESM2-650M）标注正负样本集（各100条）。
  - **蛋白质优化任务**：三个任务——① 溶菌酶样热稳定性优化（中/高难度）；② 溶菌酶样溶解度优化（中/高难度）；③ GFP荧光亮度优化（中/高难度）。初始集来自低/中属性区间的序列。
- **基线与比较方法**：
  - 生成任务：原始未修改模型、微调（fine-tuning）模型（AE仅微调最后一层，AR用LoRA）。
  - 优化任务：AdaLead、PEX、GWG（Gibbs-with-Gradients）。注意这些方法需要代理适应度预测器，本文用与引导向量提取相同的正负样本集训练代理预测器，且不更新。
- **评估指标**：目标属性适应度（Fitness）、多样性（Diversity）、新颖性（Novelty）、与初始集/高适应度集的相异度（Dissim_init / Dissim_high）。使用MMseqs2计算序列相似度。

## 4. 资源与算力

- **文中未明确说明**：论文未提及具体GPU型号、数量、训练时长、显存消耗等算力资源信息。仅提到代码开源，但未提供详细硬件配置。推测实验规模（ESM2-650M、ESM3-1.4B、ProLLaMA-7B）在单/多GPU上可行，但具体信息缺失。

## 5. 实验数量与充分性

- **实验组数**：较多，覆盖了生成任务（两种属性×三种模型）、优化任务（三种属性×中/高难度×两种模型）、超参数敏感性（样本数、引导强度α）、扩展实验（多目标优化、更大模型ESM2-3B）。总共超过20组表格/图所示的实验结果。
- **充分性**：实验设计较为全面，包括：
  - 多种PLMs架构（AE、AR）。
  - 多种属性（热稳定性、溶解度、GFP亮度）。
  - 多种难度（中、高）。
  - 与多个强基线（微调、AdaLead、PEX、GWG）对比。
  - 超参数敏感性分析（样本数、α）。
  - 额外实验（多目标联合优化、模型规模扩展）。
- **公平性**：注意在优化任务中，基线方法（AdaLead等）需要使用代理适应度预测器，而本文ASPO无需额外预测器，但代理预测器也基于相同正负样本训练，且不更新（与原文真实实验条件一致），对比基本公平。但未与最新方法（如基于强化学习或扩散模型）进行比较，存在一定局限。

## 6. 论文的主要结论与发现

- **激活引导有效**：在生成任务中，ASPO（激活引导）在所有模型上均显著提升目标属性（热稳定性提升20+°C，溶解度提升0.2以上），同时保持或提升多样性与新颖性。
- **ASPO优化性能突出**：在优化任务中，ASPO在热稳定性和GFP亮度上远超AdaLead、PEX、GWG；溶解度上具有竞争力或最优。多样性略低于某些基线，但更接近初始序列，适合实际工程。
- **超参数鲁棒性**：正负样本数100左右即可达到较好性能；引导强度α建议设为1.0，可根据任务微调。
- **可扩展性**：在大模型ESM2-3B上效果更好，表明激活引导随模型规模扩大而增强。
- **多目标可行**：单一引导向量平均可联合优化热稳定性和溶解度，虽增益减小但仍优于微调。

## 7. 优点：方法或实验设计上的亮点

- **训练无关**：无需重新训练或微调模型，仅需少量正负样本计算引导向量，推理时添加即可，高效且保留预训练知识。
- **通用性**：同时适用于自编码和自回归PLMs，可无缝集成到多种架构。
- **新颖应用**：首次将LLM中的激活引导引入蛋白质领域，并创新地结合突变位点识别（ASPO）用于蛋白质优化，形成了完整框架。
- **评估全面**：不仅关注目标属性，还考虑多样性、新颖性、相异度等，避免过拟合或搜索空间过窄。
- **分析深入**：通过t-SNE可视化验证了PLMs内隐属性知识；进行了详细的超参数敏感性实验，给出了实用建议。

## 8. 不足与局限

- **依赖属性预测器**：正负样本集的构建需要属性预测器（文中使用基于ESM2-650M训练的预测器），预测器本身存在误差，可能影响引导向量质量。但论文未讨论预测器不确定性带来的影响。
- **未与更先进方法比较**：优化任务中仅对比了AdaLead、PEX、GWG等相对早期方法，未与近年基于扩散模型、强化学习（如RL-based）、贝叶斯优化等先进方法比较，说服力有限。
- **多样性下降**：ASPO在部分任务中（尤其是硬难度）导致多样性偏低，可能不利于探索全新序列空间。
- **多目标扩展简单**：多目标联合优化仅采用简单加权平均，未探索更复杂的多任务引导策略。
- **生物验证缺失**：所有结果均为计算预测值（in silico），缺乏湿实验验证，实际生物活性未知。
- **可重复性不足**：未提供完整的超参数搜索细节（如α具体搜索步长、不同任务的最优设置），以及详细的计算资源信息，影响可复现性。

（完）
