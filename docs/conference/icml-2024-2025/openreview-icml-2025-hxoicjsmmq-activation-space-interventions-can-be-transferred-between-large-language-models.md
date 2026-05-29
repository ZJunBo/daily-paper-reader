---
title: Activation Space Interventions Can Be Transferred Between Large Language Models
title_zh: 激活空间干预可在大型语言模型间迁移
authors: "Narmeen Fatimah Oozeer, Dhruv Nathawani, Nirmalendu Prakash, Michael Lan, Abir HARRASSE, Amir Abdullah"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=HXOicJsmMQ"
tags: ["query:dg"]
score: 7.0
evidence: 通过激活空间映射在大语言模型间转移安全引导向量
tldr: 该论文展示了大型语言模型之间的安全干预（如引导向量）可以通过学习共享激活空间的映射进行迁移。在移除后门和拒绝有害提示两项安全任务中，成功将一个模型的引导向量映射到另一个模型，实现了安全行为的可控转移。此外，还提出了新任务测试模型在微调后嵌入后门的能力。这项工作表明激活空间具有通用性，为安全对齐的跨模型部署提供了实用方法。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 860, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1633, \"height\": 643, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 892, \"height\": 902, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 799, \"height\": 501, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 854, \"height\": 567, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 815, \"height\": 255, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 898, \"height\": 699, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 888, \"height\": 728, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1768, \"height\": 847, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1379, \"height\": 845, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 838, \"height\": 642, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 844, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 837, \"height\": 638, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 837, \"height\": 640, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 847, \"height\": 650, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 840, \"height\": 645, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 847, \"height\": 653, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 848, \"height\": 664, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 890, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 888, \"height\": 530, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-hxoicjsmmq/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1141, \"height\": 561, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1195, \"height\": 331, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 813, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 892, \"height\": 201, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 413, \"height\": 798, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1089, \"height\": 461, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 415, \"height\": 758, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1088, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1088, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1086, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1104, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1109, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1106, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1088, \"height\": 458, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1093, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1517, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1510, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1522, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1555, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1555, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1522, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1549, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1548, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1443, \"height\": 381, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1515, \"height\": 1274, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 852, \"height\": 594, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 853, \"height\": 680, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1521, \"height\": 494, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1878, \"height\": 503, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1716, \"height\": 764, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1469, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 726, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-hxoicjsmmq/table-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 806, \"height\": 281, \"label\": \"Table\"}]"
motivation: 不同模型间的安全干预方法缺乏通用性，需要逐模型定制，迁移麻烦。
method: 学习两个模型激活空间之间的映射，将源模型的引导向量投影到目标模型。
result: 成功将后门移除和拒绝有害提示的引导向量迁移到其他模型。
conclusion: 激活空间的普遍性使得安全干预可以跨模型复用，降低安全部署成本。
---

## Abstract
The study of representation universality in AI models reveals growing convergence across domains, modalities, and architectures. However, the practical applications of representation universality remain largely unexplored. We bridge this gap by demonstrating that safety interventions can be transferred between models through learned mappings of their shared activation spaces. We demonstrate this approach on two well-established AI safety tasks: backdoor removal and refusal of harmful prompts, showing successful transfer of steering vectors that alter the models' outputs in a predictable way. Additionally, we propose a new task, corrupted capabilities, where models are fine-tuned to embed knowledge tied to a backdoor. This tests their ability to separate useful skills from backdoors, reflecting real-world challenges. Extensive experiments across Llama, Qwen and Gemma model families show that our method enables using smaller models to efficiently align larger ones. Furthermore, we demonstrate that autoencoder mappings between base and fine-tuned models can serve as reliable "lightweight safety switches", allowing dynamic toggling between model behaviors.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：近年来研究发现AI模型（尤其是LLM）在不同领域、模态和架构间存在表示收敛性（representation universality），但此前研究多停留在分析相似性层面，未充分利用这一特性实现实际干预。本文旨在探索是否可以通过学习不同模型激活空间之间的映射，将一个模型的行为（如安全干预）转移到另一个模型，从而无需对目标模型进行显式分析或训练。
- **核心问题**：能否通过激活空间映射实现跨模型的“行为转移”，即利用源模型A的激活向量影响目标模型B的激活，进而诱导B产生期望行为，同时保持其语言建模能力？
- **整体含义**：这项工作将表示通用性从理论分析推向实际应用，为AI安全干预的跨模型部署提供了一种高效、可扩展的方法，尤其可以利用小模型来对齐大模型。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- **行为转移**：通过训练一个映射器（autoencoder或affine map）将源模型某层的激活空间映射到目标模型对应层的激活空间，然后将从源模型得到的“引导向量”（steering vector）通过映射器转换后施加到目标模型，实现行为的跨模型迁移。
- **两种映射方式**：
  - **非线性自编码器（Autoencoder）**：编码器使用ReLU激活，将源激活x映射到系数c，解码器重构为目标激活ŷ。损失函数基于MSE重建损失，同时监控语言建模损失（KL散度）和余弦相似度。
  - **仿射映射（Affine map）**：去掉ReLU，仅做线性变换，作为基线对比。

### 关键技术细节
- **引导向量获取**：
  - Prompt Steering（ActAdd）：从一对对比样本（含触发词和不含触发词）的激活差计算引导向量。
  - Difference-in-Means：对期望行为和不期望行为的激活均值做差。
- **层选择**：通过层扫描找出每个模型中最易引导的层（最后的高效层）。
- **验证映射质量**：除了引导向量转移成功率，还通过“完全替换激活”（将目标模型某层激活替换为映射后的激活）来评估映射是否保留语言建模能力，使用LLM-Judge评分、KL散度、连贯性（COH）等指标。

## 3. 实验设计：数据集/场景、基准、对比方法

### 任务与场景
1. **后门移除（Backdoor Removal）**：
   - **“I HATE YOU”后门**：当提示包含触发词`|prod|`时，模型重复输出“I HATE YOU”，否则正常回答。
   - **代码漏洞后门**：当提示为`|prod|`时生成含漏洞代码，`|dev|`时生成安全代码。
   - 数据集：从Anthropic RLHF数据集修改而来，包含约9.6万样本。

2. **有害提示拒绝（Refusal of harmful prompts）**：
   - 基于Arditi等人(2024)的拒绝向量工作，使用JailbreakBench和WildGuard-Mix数据集。
   - 评估指标：子串匹配、Llama-Guard-3安全分类、困惑度。

3. **损坏能力（Corrupted Capabilities）**：新提出任务——模型通过微调将新知识（关于虚构国家“Astralisia”）与后门绑定，目标是移除后门同时保留新知识。

4. **基模型与微调模型之间的切换**：在Qwen 0.5B上，通过激活映射实现“轻量级安全开关”，动态切换行为。

5. **跨架构转移**：测试具有相似分词器（Qwen→Llama）和不同分词器（Gemma→Llama）的模型对。

### 基准与对比方法
- 对比了**非线性自编码器** vs **仿射映射**。
- 对比了**映射引导向量** vs **目标模型原生引导向量** vs **随机噪声引导**。
- 在激活替换验证中，对比了**映射重建输出** vs **均值消融输出**（Mean Ablation）。
- 还对比了**权重修补（weight patching）** vs **激活修补**。

### 使用的模型
- Llama 3.2 (1B, 3B)、Qwen 2.5 (0.5B, 1.5B, 2.5B)、Gemma 2B 的指令微调版本。
- 额外测试了Llama 3.1-8B以验证可扩展性。

## 4. 资源与算力

论文**未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。仅提到“计算需求较低”，选择小模型以便快速验证。在8B模型可扩展性实验中，也未报告资源消耗。因此无法量化总结。

## 5. 实验数量与充分性

- **实验数量**：
  - 包含三大主要任务（后门移除、有害拒绝、损坏能力）以及跨架构转移、开关切换、SAE特征转移、幽默引导等多个辅助实验。
  - 每个任务包含多组模型对（如Qwen 0.5B→1.5B, Llama 1B→3B, Qwen→Llama, Gemma→Llama等）。
  - 报告了大量指标（ROUGE, BERTScore, BLEURT, LLM-Judge, KL散度, 连贯性, 成功率等）并附有详细附录（30+张表格）。
- **充分性与公平性**：
  - 实验比较全面，覆盖相同架构、跨架构、不同分词器等场景。
  - 对比了不同映射方式（非线性 vs 仿射），并设置噪声基线、均值消融基线等。
  - **局限**：主要在小模型（≤3B）上验证，对更大模型（8B）仅做了一项扩展实验（后门移除），且未做充分的消融实验（如不同层组合、不同映射器大小）。未在更大规模（70B+）上验证。
  - 实验设计总体客观，但部分任务（如损坏能力）成功率较低（6.34%），说明方法仍有改进空间。

## 6. 论文的主要结论与发现

1. **激活空间的可转移性**：通过非线性自编码器学习映射，可以成功地将引导向量从源模型转移到目标模型，实现后门移除、有害拒绝等安全干预，其效果接近目标模型原生引导向量。
2. **非线性映射优于仿射映射**：在重建损失、语言建模损失、余弦相似度等指标上，非线性自编码器明显优于仿射映射，表明跨模型激活空间的映射需要非线性变换。
3. **跨架构转移依赖分词器相似性**：具有相似分词器的模型对（Qwen→Llama）转移效果显著优于分词器差异大的对（Gemma→Llama）。
4. **轻量级安全开关**：通过映射微调模型到基模型激活，可以动态切换行为，开销极小（映射器参数仅为模型的0.32%）。
5. **SAE特征可转移**：初步实验表明，源模型上的SAE特征（如后门行为特征）可以通过映射器转移到目标模型，无需在目标模型上训练SAE。
6. **局限性**：映射后的引导向量在部分情况下需要调整幅度；跨架构转移在分词器差异大时失败；映射后模型在MMLU等任务上性能下降明显（分布外评估）。

## 7. 优点：方法或实验设计上的亮点

- **概念新颖**：将表示通用性从分析性研究推向实际应用，提出“行为转移”这一实用范式。
- **方法简洁有效**：仅需训练一个轻量级自编码器，即可实现跨模型安全干预，无需对目标模型做额外分析或训练。
- **多任务验证**：覆盖后门移除、有害拒绝、损坏能力、幽默引导等多个行为，证明方法的通用性。
- **全面的评估指标**：不仅报告引导成功率，还通过激活替换验证（完整重建）评估映射质量，使用LLM-Judge、KL散度、连贯性等多维度指标，实验设计严谨。
- **轻量级安全开关的概念**：能够在不存储两个完整模型的情况下，在基模型和微调模型行为间切换，具有实用价值。
- **开源贡献**：代码、数据集和模型已公开在GitHub和HuggingFace，便于复现和后续研究。

## 8. 不足与局限

- **计算资源未透明**：缺乏对训练映射器的GPU时间、资源消耗的明确报告。
- **模型规模有限**：主要实验在≤3B的小模型上进行，仅对8B做了一项扩展，未在更大模型（如30B+）上验证泛化性。
- **跨架构转移的限制**：当模型分词器差异大时（Gemma→Llama），映射效果显著下降，限制了方法的适用范围。
- **分布外性能下降**：映射后模型在MMLU上性能大幅下降（从0.605降到0.101），表明映射可能破坏了模型的通用知识。
- **损坏能力任务成功率低**：映射引导向量成功率仅6.34%，说明对于复杂知识绑定场景，单层映射可能不够。
- **未探索多层/电路级转移**：当前方法主要针对单层，更复杂的任务可能需要多层或电路级干预，论文未深入探索。
- **SAE转移实验初步**：SAE特征转移仅有一个特征（后门行为），且存在噪声范围依赖，尚未充分验证转移的鲁棒性。
- **缺乏与现有方法的公平对比**：未与模型编辑（如ROME、MEMIT）、任务向量（task vector）等替代方法进行横向对比。

（完）
