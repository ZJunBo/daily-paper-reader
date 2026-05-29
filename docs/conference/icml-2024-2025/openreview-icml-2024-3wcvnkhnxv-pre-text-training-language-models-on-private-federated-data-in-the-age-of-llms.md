---
title: "PrE-Text: Training Language Models on Private Federated Data in the Age of LLMs"
title_zh: PrE-Text：在大模型时代对私有联邦数据训练语言模型
authors: "Charlie Hou, Akshat Shrivastava, Hongyuan Zhan, Rylan Conway, Trang Le, Adithya Sagar, Giulia Fanti, Daniel Lazar"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=3WCvnkHnxV"
tags: ["query:dg"]
score: 4.0
evidence: 生成差分隐私合成文本数据用于训练小模型
tldr: 该论文提出PrE-Text方法，用于生成差分隐私的合成文本数据，以解决设备上训练计算开销大、部署困难的问题。通过合成数据训练小模型，在隐私预算有限的情况下，模型性能优于直接在设备上训练的结果。该方法为联邦学习场景下的隐私保护模型训练提供了新途径，合成数据的方法也可迁移至其他需要隐私保护的数据生成任务。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-3wcvnkhnxv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1766, \"height\": 694, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-3wcvnkhnxv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 708, \"height\": 524, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-3wcvnkhnxv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 891, \"height\": 883, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-3wcvnkhnxv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1756, \"height\": 380, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-3wcvnkhnxv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 862, \"height\": 668, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-3wcvnkhnxv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1666, \"height\": 629, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-3wcvnkhnxv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1666, \"height\": 628, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-3wcvnkhnxv/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1517, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-3wcvnkhnxv/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1518, \"height\": 271, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-3wcvnkhnxv/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1388, \"height\": 341, \"label\": \"Table\"}]"
motivation: 设备上训练存在计算和通信开销大、调试困难等问题，需要更高效的隐私保护训练方式。
method: 采用Private Evolution算法生成差分隐私合成文本数据，替代真实数据训练小模型。
result: 合成数据训练的小模型在多个数据集上优于设备上训练的小模型。
conclusion: 利用合成数据可以绕过设备上训练的限制，实现高效的隐私保护模型训练。
---

## Abstract
On-device training is currently the most common approach for training machine learning (ML) models on private, distributed user data. Despite this, on-device training has several drawbacks: (1) most user devices are too small to train large models on-device, (2) on-device training is communication- and computation-intensive, and (3) on-device training can be difficult to debug and deploy. To address these problems, we propose Private Evolution-Text (PrE-Text), a method for generating differentially private (DP) synthetic textual data. First, we show that across multiple datasets, training small models (models that fit on user devices) with PrE-Text synthetic data outperforms small models trained on-device under practical privacy regimes ($\epsilon=1.29$, $\epsilon=7.58$). We achieve these results while using 9$\times$ fewer rounds, 6$\times$ less client computation per round, and 100$\times$ less communication per round. Second, finetuning large models on PrE-Text's DP synthetic data improves large language model (LLM) performance on private data across the same range of privacy budgets. Altogether, these results suggest that training on DP synthetic data can be a better option than training a model on-device on private distributed data. Code is available at https://github.com/houcharlie/PrE-Text.

---

## 论文详细总结（自动生成）

# PrE-Text 论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有的设备端训练（on-device training）是训练隐私分布式用户数据上机器学习模型的主流方法，但存在三大缺陷：(1) 用户设备太小，无法训练大型模型；(2) 通信和计算开销大；(3) 部署和调试困难。随着大语言模型（LLM）的普及，设备端训练越来越受限。
- **整体含义**：论文提出一种替代范式——先在服务器端生成差分隐私（DP）合成文本数据，再利用这些合成数据集中训练或微调模型。这样既能保护用户隐私，又能避免设备端训练的各种弊端，且合成数据可重复使用而不增加额外隐私成本（DP的后处理性质）。该工作旨在证明：在实用隐私预算下，使用DP合成数据训练的模型可以优于直接在设备上进行联邦学习（DP-FL）训练的模型。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：基于Private Evolution（PE）框架（Lin et al., 2023），将其从图像域适配到文本域，并增加后处理扩展阶段，生成高质量DP合成文本数据。
- **关键技术细节**：
  1. **Private Evolution（PE）适应文本**：多轮迭代过程。每一轮：
     - 服务器生成候选样本集合 \(S_t\)（初始为公共样本）。
     - 客户端为每个候选样本计算其与私有样本的最近邻计数（基于嵌入向量距离），生成直方图。
     - 每个客户端向直方图添加高斯噪声（保证DP），然后通过安全聚合（secure aggregation）汇总所有客户端的直方图。
     - 对汇总直方图进行阈值处理（减去阈值 \(H\) 并取非负）以提高信噪比。
     - 根据处理后直方图采样得到幸存样本 \(S'_t\)，然后对幸存样本进行“变体生成”（Variation）：随机遮盖部分token并用掩码语言模型（如RoBERTa-large）填充，重复若干次得到新的种群 \(S_{t+1}\)。
  2. **改进点**：
     - 使用所有轮次的 \(S'_t\) 的并集（而非仅最后一轮）作为DP种子集，更充分利用隐私预算。
     - 距离函数使用变体的平均嵌入而非单个嵌入，提高鲁棒性。
  3. **后处理扩展（Expand）**：利用LLM（LLaMA-2-7B）从DP种子集中随机选取3个样本作为示例，提示LLM生成更多相似文本。该步骤不消耗额外隐私预算（DP后处理性质）。
- **算法流程**（文字说明）：
  - 输入：迭代次数 \(T\)，生成样本数 \(N_{syn}\)，初始种群 \(S_1\)。
  - for \(t=1\) to \(T\):
    - 客户端计算直方图并加噪、聚合、阈值化。
    - 采样得到 \(S'_t\)，对每个样本执行Variation得到 \(S_t\)。
  - 将所有 \(S'_t\) 的集合作为DP种子集。
  - 使用Expand生成大量合成数据 \(S_{syn}\)。
  - 输出：合成数据 \(S_{syn}\)。

## 3. 实验设计：数据集/场景、基准、对比方法

- **数据集**：
  - 从c4-English数据集中构造三个联邦私有数据集：**JOBS**（工作相关）、**FORUMS**（论坛）、**MICROBLOG**（微博），每个有1250个客户端，训练集10000样本，测试集1000样本，每客户端8个样本。
  - 另一个数据集**CODE**：来自问答技术社区，按用户划分，1250个训练用户，测试集来自另外100用户的2000条评论，每客户端最多128条评论。
  - 初始种群使用c4-en中未出现在任何私有数据集中的公共子集。
- **任务**：语言建模（next-token prediction），评估指标为准确率和交叉熵损失。
- **对比方法**：
  - **\(\epsilon=0\) 基线**：c4-only（仅用公共c4子集微调DistilGPT2）、Expand-only（公共c4子集经Expand扩展后微调）。
  - **\(\epsilon=\infty\) 基线**：Expand-private（私有数据经Expand扩展后微调，非隐私）。
  - **设备端训练基线**：DP-FedAvg 和 DP-FTRL（两个主流DP联邦学习算法），在隐私预算 \(\epsilon=1.29\) 和 \(\epsilon=7.58\) 下训练DistilGPT2。
  - **文本到文本私有化基线**：DP-Prompt（Utpala et al., 2023），使用flan-t5-3b在本地产生隐私化改写文本。
- **场景**：
  - **小模型（设备端）**：使用DistilGPT2（82M参数），比较PrE-Text合成数据训练 vs 设备端DP-FL。
  - **大模型（服务器端）**：使用LLaMA-2-7B，微调于PrE-Text合成数据 vs 非微调基线。

## 4. 资源与算力

- 文中未明确说明训练所使用的具体GPU型号、数量及总训练时长。仅提到使用了Bridges-2 GPU（通过Pittsburgh Supercomputing Center的ACCESS分配）以及Delta GPU。实际实验细节中提及使用vLLM加速Expand的LLM推理，但未量化具体算力消耗。因此，缺乏详细的算力报告。

## 5. 实验数量与充分性

- **实验组数**：
  - 小模型实验：在4个数据集上，对比了5种方法（包括PrE-Text的两个隐私水平），评估准确率和损失，共约8组主要结果表（Table 2, 3）。
  - 大模型实验：在4个数据集上，对比PrE-Text（两个隐私水平）、非微调和\(\epsilon=\infty\)基线，共约4组结果表（Table 4, 5）。
  - 扩展数据规模消融实验：在4个数据集上变化合成数据量（50k到2M），显示性能随数据量对数线性增长（Figure 2）。
  - 效率对比：一张表格（Table 6）对比通信、计算、轮次。
- **充分性与公平性**：
  - 实验覆盖了多个领域数据集（工作、论坛、微博、技术问答），具有一定多样性。
  - 对比了多个主流基线（DP-FedAvg、DP-FTRL、DP-Prompt），以及非隐私上限和纯公共基线，比较全面。
  - 消融实验显示了扩展数据量的影响，但未对PE内部参数（如迭代轮数T、阈值H、噪声系数等）进行系统消融。也未评估不同种子大小的影响。
  - 实验条件设置合理：所有模型先在同一公共c4子集上预微调以控制公平性；超参数经过网格搜索并报告最佳结果。
  - 存在一定局限：对CODE数据集，性能在1M样本后出现下降，说明扩展量并非越多越好；且作者指出DP-Prompt表现甚至不如\(\epsilon=0\)基线，说明该基线较弱。

## 6. 论文的主要结论与发现

- PrE-Text生成的DP合成数据在小模型（DistilGPT2）训练上，在 \(\epsilon=1.29\) 和 \(\epsilon=7.58\) 下，**显著优于**直接设备端DP-FL训练（DP-FedAvg、DP-FTRL）以及DP-Prompt方法，同时**通信成本降低100倍/轮、客户端计算降低6倍/轮、轮次减少9倍**。
- 在大模型（LLaMA-2-7B）场景，微调于PrE-Text合成数据后，在私有测试集上的困惑度和准确率均优于非微调的原始LLM。证明该方法可突破设备端不能训练大模型的限制，首次实现在联邦设置下无需将模型放在设备端就能隐私微调LLM。
- 随着扩展数据量增加（50k到2M），下游模型性能大致对数线性提升，但COD数据集在1M后出现饱和甚至下降。
- 总体结论：在实用隐私预算下，利用DP合成数据进行集中训练是设备端联邦学习的一个有竞争力的替代方案。

## 7. 优点

- **方法创新性**：将Private Evolution从图像域成功迁移到文本域，并加入后处理扩展阶段，显著提升合成数据质量与可用性。
- **实用性强**：解决了设备端训练的三个主要瓶颈（模型大小限制、通信计算开销、调试困难），提供更易部署的解决方案。
- **效率优势**：实验量化了通信/计算节省，且合成数据可重复使用，不消耗额外隐私预算。
- **实验全面**：覆盖小模型和大模型两种重要场景，多个数据集，对比方法丰富，且公平（所有模型先经公共数据微调再训练）。
- **可复现**：代码开源（GitHub）。

## 8. 不足与局限

- **隐私风险**：PrE-Text依赖预训练的公共模型（RoBERTa、LLaMA），这些模型本身的训练数据可能包含敏感信息，且论文未提供对这些公共模型隐私风险的审计或保证。作者在影响声明中也承认了这一点。
- **实验覆盖缺失**：
  - 未对PE内部超参数（如迭代轮次T、阈值H、噪声系数σ、变体参数MASK%、Wsteps）进行系统消融。
  - 未评估不同种子大小（DP种子集大小）对性能的影响。
  - 仅使用DistilGPT2作为小模型代表，未尝试其他架构（如TinyBERT、MobileBERT）。
  - 大模型实验仅用LLaMA-2-7B，未推广到更大模型或其他LLM。
  - 未考虑更严格的隐私预算（如\(\epsilon<1\)），也未评估隐私预算对合成数据质量的影响曲线。
- **计算转移**：虽然客户端计算和通信减少，但服务器端计算负担显著增加（需要运行LLM进行Expand），作者未量化服务器端算力成本。
- **数据污染风险**：LLaMA-2-7B可能在训练时已接触过c4-en数据（与其他基准相同），作者承认难以完全避免，但指出c4-en是目前最符合条款的可获得大规模数据集。
- **应用限制**：方法依赖高质量的掩码语言模型和LLM，若这些模型在目标领域表现不佳，合成数据质量会下降。此外，Expand使用的提示（prompt）是针对特定风格的，需要人工设计或调整。

（完）
