---
title: Towards Harmonized Uncertainty Estimation for Large Language Models
title_zh: 迈向和谐的大语言模型不确定性估计
authors: "Rui Li, Jing Long, Muge Qi, Heming Xia, Lei Sha, Peiyi Wang (王培懿), Zhifang Sui"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.acl-long.1118.pdf"
tags: ["query:luq"]
score: 9.0
evidence: 大语言模型统一不确定性估计
tldr: 现有LLM不确定性估计方法在指示性、平衡性和校准性之间难以协同。本文提出CUE（不确定性估计校正器），通过训练一个轻量级模型在目标LLM对齐数据上，有效提升不确定性估计的和谐性，实验表明CUE在多个指标上优于基线。
source: ACL-2025-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1118/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 815, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1118/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 596, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1118/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1643, \"height\": 327, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1118/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1573, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1118/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1403, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1118/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 807, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1118/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1649, \"height\": 648, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1118/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1646, \"height\": 842, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1118/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 803, \"height\": 329, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1118/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1644, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1118/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 921, \"height\": 160, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1118/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1656, \"height\": 463, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1118/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 829, \"height\": 318, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1118/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 834, \"height\": 144, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1118/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 636, \"height\": 158, \"label\": \"Table\"}]"
motivation: 现有不确定性估计方法在指示性、平衡性和校准性之间无法取得和谐。
method: 提出CUE方法，训练一个轻量级模型来校正LLM的不确定性估计分数。
result: CUE在多个基准上提升了不确定性估计的准确性和校准性。
conclusion: 通过轻量级校正器可以有效提升LLM不确定性估计的整体性能。
---

## Abstract
To facilitate robust and trustworthy deployment of large language models (LLMs), it is essential to quantify the reliability of their generations through uncertainty estimation. While recent efforts have made significant advancements by leveraging the internal logic and linguistic features of LLMs to estimate uncertainty scores, our empirical analysis highlights the pitfalls of these methods to strike a harmonized estimation between indication, balance, and calibration, which hinders their broader capability for accurate uncertainty estimation. To address this challenge, we propose CUE (Corrector for Uncertainty Estimation): A straightforward yet effective method that employs a lightweight model trained on data aligned with the target LLM’s performance to adjust uncertainty scores. Comprehensive experiments across diverse models and tasks demonstrate its effectiveness, which achieves consistent improvements of up to 60% over existing methods.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：当前大语言模型（LLM）的不确定性估计方法在三个关键维度——**指示性**（uncertainty score 能否正确反映回答可靠性）、**平衡性**（precision 与 recall 的权衡）、**校准性**（分数是否符合概率直觉）——之间无法取得和谐。例如，SAR 方法在指示性上最优，但校准性差；其他方法在某个维度表现好却在其他维度欠佳。且不同方法的不确定性分数组合后性能几乎无提升，说明现有方法高度同质、互补性差。
- **背景**：LLM 被广泛部署但存在生成幻觉和过度自信问题，需要可靠的不确定性估计来量化输出可靠性，从而提升可信赖性。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：训练一个轻量级分类器（称为 Corrector）作为辅助校正器，利用目标 LLM 在特定领域的数据对齐其真实性能，对现有不确定性估计方法的分数进行后处理调整，从而实现和谐的不确定性估计。
- **技术细节**（三步流程）：
  1. **数据集构建**：从现有问答数据集中提取问题-答案对，用目标 LLM 生成回答；通过规则（ROUGE-L > 0.7）和 GPT-3.5-turbo 联合判断回答是否正确（OR 逻辑），得到二进制标签（1 表示正确，0 表示错误）；形成校正数据集 D*_cor = {(question, 1 - label)}（即预测模型回答错误的概率）。
  2. **校正器训练**：采用轻量编码器（如 RoBERTa、DeBERTa）加上全连接层和二分类输出（sigmoid），输入问题的 [CLS] 表征，输出校正分数 C(x) = σ(W·h[CLS] + b)；使用二分类交叉熵损失训练。
  3. **不确定性校正**：将原始不确定性分数 U(x) 归一化到 [0,1]；然后加权融合：U_cor(x) = w* · U_norm(x) + (1 - w*) · C(x)，其中权值 w* 通过开发集网格搜索确定。
- **公式总结**：校正分数来自轻量分类器，最终校正分数是原始分数与校正分数的凸组合。

## 3. 实验设计：数据集、场景、基准、对比方法
- **数据集**：
  - **TriviaQA**（95k 问答对，常识百科类）
  - **SciQA**（2,565 问答对，科学知识领域）
- **目标模型（LLM）**：
  - OPT-6.7B（较早的开源 LLM）
  - LLaMA-3-8B-Instruct（较新的指令微调模型）
- **对比基线**：涵盖四大类共 9 种方法：
  - **Logit 类**：PE（预测熵）、LN-PE（长度归一化预测熵）、SE（语义熵）、SAR（包括 SAR-t、SAR-s、SAR）
  - **Verbalized**：VC（口头置信度）
  - **Internal state**：P(True)
  - **Consistency**：LS（词汇相似度）
- **评估指标**：
  - AUROC → 衡量指示性（区分可靠/不可靠样本的能力）
  - F1 Score → 衡量平衡性（精度与召回率的调和平均）
  - ECE（期望校准误差）→ 衡量校准性

## 4. 资源与算力
- **未明确说明**：论文没有提及具体使用的 GPU 型号、数量、训练时长等硬件资源信息。仅提到使用了轻量级编码器（如 RoBERTa-base/large、DeBERTa-v3 系列），训练和推理成本远低于目标 LLM。但关于训练时间和 GPU 配置的具体细节缺失。

## 5. 实验数量与充分性
- **实验组数**：大量，包括：
  - 主实验：2 个数据集 × 2 个目标模型 × 9 种基线 × 3 个指标 → 共 108 个实验结果（表 1、图 2/5/6）
  - 消融实验：
    - 校正分数格式（概率 vs 标签）
    - 基座模型（7 种不同大小/系列的编码器）
    - 校正分数获取方式（Corrector vs GPT-4o 直接打分）
    - 与其他监督方法（Wb-S）对比
  - 泛化实验：
    - 跨数据集（不同领域：TriviaQA↔SciQA；同领域医疗：MedMCQA↔MedQA）
    - 跨模型（OPT-2.7B、OPT-6.7B、LLaMA-3-8B 之间迁移）
  - 超参数敏感性分析（w* 稳定范围）
- **充分性评价**：实验较为充分，覆盖多维度对比和泛化验证。但缺乏对纯黑盒 API 模型（如 GPT-4）的测试，也缺少更多领域（如对话、生成任务）的验证，且未在更大规模 LLM（如 70B+）上测试。总体上，实验设计客观、公平（基于开源代码复现且与公开基线比较）。

## 6. 论文的主要结论与发现
- CUE 显著提升了现有所有基线方法在 **AUROC**（指示性）、**F1**（平衡性）、**ECE**（校准性）三个维度上的性能，实现了和谐的不确定性估计。
- 具体提升幅度：
  - AUROC 平均提升：TriviaQA 上 0.27，SciQA 上 0.09。
  - F1 平均提升 38.97%。
  - ECE 大幅降低（例如 OPT-6.7B 在 TriviaQA 上平均降低 0.34）。
- 校正器与现有方法互补性强，跨数据集/跨模型泛化有一定效果（同领域 7-11% 提升，不同领域 4-6% 提升，同模型族内 6-11% 提升）。
- 消融实验表明概率式校正分数优于离散标签，更大/更先进的编码器（如 DeBERTa-v3-large）效果更好，且校正器优于 GPT-4o 直接打分。

## 7. 优点
- **方法简单有效**：仅需训练一个轻量模型，易于集成到现有不确定性估计流水线中。
- **非侵入性**：不依赖目标 LLM 的内部状态或 logits，可同时用于白盒和黑盒模型。
- **多维度优化**：同时改善指示性、平衡性和校准性，而非仅关注单一指标。
- **泛化能力**：在跨数据集和跨模型的情况下仍能保持正收益，且消融实验充分。

## 8. 不足与局限
- **依赖标注数据**：需要问答对和人工/自动标注，构建成本偏高，且标注过程可能引入噪声（虽然采用了 OR 逻辑降低漏报）。
- **泛化边界**：
  - 跨模型泛化仅在同模型族内较好，跨架构大模型（OPT→LLaMA）时增益有限。
  - 仅在问答任务上验证，未在自由文本生成、翻译、对话等任务上测试。
- **实验覆盖不全面**：
  - 未测试纯黑盒 API 模型（如 GPT-4、Claude 等）。
  - 未与当前最先进的监督不确定性估计方法（如 LARS、MARS）对比（可能因为代码未公开）。
  - 超参数 w* 需要通过开发集网格搜索，不同方法/数据集需单独确定，增加了使用成本。
- **算力信息缺失**：未提供训练校正器所需的具体 GPU 资源，不利于可重复性。
- **校准性提升机制不明**：论文指出校准性并非直接训练目标，但 CUE 仍能提升校准性，缺乏理论解释。

（完）
