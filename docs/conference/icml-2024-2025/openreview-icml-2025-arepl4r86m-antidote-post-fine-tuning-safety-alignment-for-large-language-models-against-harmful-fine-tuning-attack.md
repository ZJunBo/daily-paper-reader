---
title: "Antidote: Post-fine-tuning Safety Alignment for Large Language Models against Harmful Fine-tuning Attack"
title_zh: Antidote：针对有害微调攻击的微调后安全对齐方法
authors: "Tiansheng Huang, Gautam Bhattacharya, Pratik Joshi, Joshua Kimball, Ling Liu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Arepl4R86m"
tags: ["query:smd"]
score: 9.0
evidence: 通过微调后安全对齐防御有害微调攻击
tldr: 论文直接针对有害微调攻击——少量有害数据混入微调数据集即可破坏安全对齐。提出Antidote方法，在微调后阶段移除有害参数以恢复模型安全性，且与微调超参数无关。实验证明现有防御在特定超参数下失效，而Antidote始终保持稳健，有效缓解了安全退化问题。该方法为防御有害微调攻击提供了全新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-arepl4r86m/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 837, \"height\": 267, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-arepl4r86m/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 833, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-arepl4r86m/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 835, \"height\": 352, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-arepl4r86m/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1235, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-arepl4r86m/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 837, \"height\": 348, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-arepl4r86m/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 850, \"height\": 498, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-arepl4r86m/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1589, \"height\": 367, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-arepl4r86m/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1588, \"height\": 333, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-arepl4r86m/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1586, \"height\": 332, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-arepl4r86m/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1588, \"height\": 366, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-arepl4r86m/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 695, \"height\": 309, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-arepl4r86m/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 849, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-arepl4r86m/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 856, \"height\": 205, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-arepl4r86m/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 856, \"height\": 299, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-arepl4r86m/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 682, \"height\": 312, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-arepl4r86m/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 871, \"height\": 251, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-arepl4r86m/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 853, \"height\": 162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-arepl4r86m/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 856, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-arepl4r86m/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 858, \"height\": 156, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-arepl4r86m/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 852, \"height\": 255, \"label\": \"Table\"}]"
motivation: 现有防御在特定超参数（如大学习率）下失效，亟需与超参数无关的防御方法。
method: 提出微调后阶段的安全对齐方法Antidote，通过识别并移除有害参数来恢复模型安全性。
result: 实验表明Antidote在各种超参数设置下均能有效恢复安全对齐，优于现有防御。
conclusion: Antidote为防御有害微调攻击提供了鲁棒且通用的解决方案。
---

## Abstract
Safety aligned Large Language Models (LLMs) are vulnerable to harmful fine-tuning attacks -- a few harmful data mixed in the fine-tuning dataset can break the LLMs's safety alignment. While several defenses have been proposed, our evaluation shows that existing defenses fail \textit{when some specific training hyper-parameters are chosen} -- a large learning rate or a large number of training epochs in the fine-tuning stage can easily invalidate the defense. To this end,  we propose Antidote, a post-fine-tuning stage solution, which remains \textbf{\textit{agnostic to the training hyper-parameters in the fine-tuning stage}}. Antidote relies on the philosophy that by removing the harmful parameters, the harmful model can be recovered from the harmful behaviors, regardless of how those harmful parameters are formed in the fine-tuning stage. With this philosophy, we introduce a one-shot pruning stage after harmful fine-tuning to remove the harmful weights that are responsible for the generation of harmful content. Despite its embarrassing simplicity, empirical results show that Antidote can reduce harmful score while maintaining accuracy on downstream tasks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）在微调即服务（Fine-tuning-as-a-Service）场景下，用户提交的微调数据中可能混入少量有害样本（harmful fine-tuning attack），导致模型的安全对齐被破坏，即使之前经过了安全对齐。现有防御方法（如Vaccine、RepNoise、Lisa、LDIFS）存在**超参数敏感性问题**：当微调阶段采用较大的学习率或较多的训练轮次时，这些防御会显著失效，而大学习率和多轮次又往往是保证下游任务性能所必需的。
- **整体含义**：提出一种**微调后阶段**（post-fine-tuning）的安全对齐方法Antidote，该方案与微调阶段的训练超参数**无关**（agnostic），旨在通过移除模型中与有害行为相关的参数来恢复模型安全性，同时保持下游任务性能。

## 2. 论文提出的方法论

- **核心思想**：有害微调会在模型中形成一组“有害参数”，移除这些参数即可消除有害行为，而无需关心这些参数是如何形成的（即与超参数无关）。
- **关键技术细节**：
  - **有害参数识别**：使用**Wanda分数**（Sun et al., 2023）衡量每个参数对有害内容生成的重要性。Wanda分数定义为：  
    \([h(w, D_{realign})]_j = \frac{1}{|D|} \sum_{x \in D_{realign}} |w_j| \cdot \|A_j(x,w)\|_2\)  
    其中 \(w_j\) 是第 \(j\) 个权重坐标的绝对值，\(A_j\) 是对应激活的L2范数。该分数综合了权重大小和输入激活强度。
  - **有害掩码生成**：对Wanda分数进行排序，取Top-\(α\)比例的坐标作为有害参数，生成二值掩码 \(m = \text{ArgTopK}_α(h(w, D_{realign}))\)。
  - **参数移除**：通过 Hadamard 乘积将有害参数置零：\(\tilde{w} = (1 - m) \odot w\)。
- **算法流程**（Algorithm 1）：
  1. 输入：掩码比例 \(α\)、重对齐数据集 \(D_{realign}\)、安全对齐已被破坏的微调模型 \(w\)。
  2. 计算Wanda分数 \(h(w, D_{realign})\)。
  3. 生成Top-\(α\) 有害掩码 \(m\)。
  4. 应用剪枝得到重对齐模型 \(\tilde{w}\)，部署使用。

## 3. 实验设计

- **数据集**：
  - **对齐数据集**：BeaverTails中标记为安全的样本（`is_safe=True`）。
  - **有害数据集**：BeaverTails中标记为不安全的样本（`is_safe=False`），用于构造细调数据中的有害部分和重对齐数据集。
  - **下游任务数据集**：SST2（情感分类）、AGNEWS（新闻分类）、GSM8K（数学推理）、AlpacaEval（指令跟随）。默认使用SST2，部分实验用GSM8K。
- **Benchmark方法**：
  - SFT（无防御）
  - 对齐阶段防御：Vaccine、RepNoise
  - 微调阶段防御：Lisa、LDIFS
- **评估指标**：
  - **有害分数（Harmful Score, HS）**：使用BeaverTails的审核模型对1000条未见过的恶意指令的生成结果进行风险标记，计算不安全输出比例。
  - **微调准确率（Finetune Accuracy, FA）**：在各任务测试集上的Top-1准确率（分类任务）或答案正确率（GSM8K）或ChatGPT胜率（AlpacaEval）。
- **默认配置**：Llama2-7B、LoRA rank=256、对齐20 epochs、细调20 epochs、学习率1e-4、有害比例p=0.2、训练样本数n=5000（默认SST2）。

## 4. 资源与算力

- 论文明确说明：**“All experiments are done with an H100.”**（所有实验在单张NVIDIA H100 GPU上完成）。
- 未明确说明GPU数量，但从系统评估表（Table 10）可知，Antidote整体管线耗时约1.78小时（其中微调后阶段仅0.04小时），显存峰值35.45 GB（与SFT相同），开销极低。

## 5. 实验数量与充分性

- **实验组数丰富**，涵盖：
  - **有害比例 (p=0,0.05,0.1,0.2,0.5)** —— Table 1
  - **训练样本数 (n=100~5000)** —— Table 2
  - **学习率 (1e-7~1e-3)** —— Table 3
  - **训练轮次 (1~40)** —— Table 4
  - **良性微调攻击** —— Table 5
  - **不同下游数据集 (4个)** —— Table 6
  - **不同对齐数据集** —— Table 7
  - **不同模型架构 (Llama2, Mistral, Gemma, Llama3)** —— Table 8, 9
  - **消融实验**：
    - mask ratio α 的影响 —— Table 11
    - 重对齐数据集必要性（与良性/细调数据集对比） —— Table 12
    - 重对齐数据集大小影响 —— Table 13
  - **扩展实验**：与对齐阶段/微调阶段防御组合（V-S-A, S-L-A, V-L-A） —— Table 14
  - **系统性能评估**（时间、显存） —— Table 10
  - **可视化分析**：有害嵌入漂移（HED）、输出logit漂移 —— Figure 5, 6
  - **生成样例展示**（Case study）
- **公平性**：所有对比方法均使用官方或推荐超参数，且在同一实验环境下运行；Antidote与其他方法共享前两个阶段（对齐+微调），仅在后处理阶段不同，对比公平。
- **充分性**：覆盖了多种攻击强度、超参数、数据集和模型，实验设计系统全面。

## 6. 论文的主要结论与发现

- **现有防御超参数敏感**：当学习率增大或轮次增多时，Vaccine、RepNoise、Lisa、LDIFS的有害分数均显著上升，而下游精度却要求大学习率/多轮次，形成矛盾。
- **Antidote有效且鲁棒**：
  - 平均有害分数比SFT降低**11.56%**（Table 1），最高降低**17.8%**。
  - 微调准确率仅损失**1.45%**（平均），最低损失0.38%（Table 3）。
  - 在**所有超参数设置**（学习率、轮次、样本数、有害比例）下均保持低有害分数，而其他方法在极端参数下失效。
  - 能有效抵抗良性微调攻击（Table 5），良好泛化至不同模型和数据集。
- **机制验证**：Antidote通过移除有害参数显著降低有害嵌入漂移（HED），且对下游样本的logit改变较小（Figure 6）。
- **系统开销极小**：比SFT仅增加1.02倍时间，显存不变（Table 10）。

## 7. 优点

1. **简单有效**：仅需一次Wanda分数计算和剪枝，概念简单但效果显著。
2. **与微调超参数无关**：解决了现有防御的共同弱点，是首个系统性解决超参数敏感性问题的方案。
3. **低资源开销**：微调后阶段额外时间仅0.04小时，显存无额外需求，实用性强。
4. **正交兼容**：可以与对齐阶段或微调阶段的其他防御结合，进一步提升效果（如V-S-A组合）。
5. **通用性强**：在多种模型（Llama2/3、Mistral、Gemma）、多种下游任务上均有效。

## 8. 不足与局限

1. **依赖重对齐数据集**（harmful dataset）：需要额外收集有害样本（约1k~2k），虽然采集成本不高，但在某些场景下可能难以获取（如隐私或监管限制）。
2. **掩码比例α需手动调整**：α的选取影响有害分数与准确率的trade-off，缺乏自适应确定方法，且不同任务可能需要不同α（如GSM8K用0.05）。
3. **仅验证7B/8B尺度模型**：未在更大模型（如70B）上测试，剪枝效果及泛化性未知。
4. **未考虑自适应攻击**：论文假设攻击者不知道防御机制，若攻击者知道剪枝的存在，可能设计更隐蔽的分散有害权重分布的攻击。
5. **未分析模型压缩副作用**：剪枝可能永久删除某些参数，虽然精度损失小，但在某些长尾或罕见输入上的影响未被评估。
6. **仅基于Wanda分数**：Wanda分数基于权重和激活，可能对某些精细有害模式识别不足，其他重要性评分方法（如SparseGPT）未对比。

（完）
