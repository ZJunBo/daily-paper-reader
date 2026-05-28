---
title: "Safe RLHF-V: Safe Reinforcement Learning from Multi-modal Human Feedback"
title_zh: "Safe RLHF-V: 来自多模态人类反馈的安全强化学习"
authors: "Jiaming Ji, Xinyu Chen, Rui Pan, Han Zhu, Jiahao Li, Donghai Hong, Boyuan Chen, Jiayi Zhou, Kaile Wang, Juntao Dai, Chi-Min Chan, Sirui Han, Yike Guo, Yaodong Yang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=OIH3T5ZPBW"
tags: ["query:smd"]
score: 4.0
evidence: 多模态模型的安全对齐微调与约束
tldr: 该论文提出Safe RLHF-V，将多模态大模型的安全约束微调形式化为最小-最大优化问题，并从人类反馈中提取显式安全约束。虽未直接混合安全数据，但引入了安全约束微调范式，有助于缓解微调中的安全退化，为数据混合策略提供约束基础。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-oih3t5zpbw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 636, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oih3t5zpbw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1440, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oih3t5zpbw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1427, \"height\": 587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oih3t5zpbw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1437, \"height\": 621, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oih3t5zpbw/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1430, \"height\": 928, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oih3t5zpbw/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 559, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oih3t5zpbw/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 705, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oih3t5zpbw/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 658, \"height\": 376, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-oih3t5zpbw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 729, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oih3t5zpbw/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1438, \"height\": 287, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oih3t5zpbw/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1433, \"height\": 179, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oih3t5zpbw/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 729, \"height\": 121, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oih3t5zpbw/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1442, \"height\": 804, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oih3t5zpbw/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 726, \"height\": 171, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oih3t5zpbw/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1422, \"height\": 2045, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oih3t5zpbw/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1433, \"height\": 548, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oih3t5zpbw/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1429, \"height\": 689, \"label\": \"Table\"}]"
motivation: 多模态大模型存在安全风险，现有数据集未将偏好信号分解为安全约束。
method: 将安全微调建模为最小-最大优化，并从人类反馈中分离安全约束。
result: 在保持能力的同时显著提升多模态模型的安全性。
conclusion: 安全约束微调可有效保护多模态模型，为数据混合调度提供约束方向。
---

## Abstract
Multimodal large language models (MLLMs) are essential for building general-purpose AI assistants; however, they pose increasing safety risks. How can we ensure safety alignment of MLLMs to prevent undesired behaviors? Going further, it is critical to explore how to fine-tune MLLMs to preserve capabilities while meeting safety constraints. Fundamentally, this challenge can be formulated as a min-max optimization problem. However, existing datasets have not yet disentangled single preference signals into explicit safety constraints, hindering systematic investigation in this direction. Moreover, it remains an open question whether such constraints can be effectively incorporated into the optimization process for multi-modal models. In this work, we present the first exploration of the Safe RLHF-V -- the first multimodal safety alignment framework. The framework consists of: (I) BeaverTails-V, the first open-source dataset featuring dual preference annotations for helpfulness and safety, supplemented with multi-level safety labels (minor, moderate, severe); (II) Beaver-Guard-V, a multi-level guardrail system to proactively defend against unsafe queries and adversarial attacks. Applying the guard model over five rounds of filtering and regeneration significantly enhances the precursor model’s overall safety by an average of 40.9%. (II) Based on dual preference, we initiate the first exploration of multi-modal safety alignment within a constrained optimization. Experimental results demonstrate that Safe RLHF effectively improves both model helpfulness and safety. Specifically, Safe RLHF-V enhances model safety by 34.2% and helpfulness by 34.3%.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义

- **研究动机**：多模态大语言模型（MLLMs）在安全方面存在显著风险，尤其是在视觉指令微调后，模型容易遗忘基座LLM中已有的安全对齐，并且图像可能隐含诱导模型输出有害内容。现有数据集仅提供单一的偏好信号（如“有用性”或“安全性”），未能将这两种矛盾的偏好显式分解为可约束的优化目标，导致系统性地研究安全约束优化在多模态场景下的有效性受到阻碍。
- **核心问题**：如何在多模态模型的微调过程中，既保留其能力（有用性），又满足安全约束（无害性）？这一问题被形式化为一个**min-max优化问题**，但需要明确的安全约束和有效的优化框架。
- **整体含义**：本文首次将安全约束强化学习（Safe RL）与多模态人类反馈结合，提出 Safe RLHF-V 框架，旨在系统性地解决多模态模型的安全对齐挑战，为构建更安全、更可信的通用AI助手提供方法论和数据集基础。

### 2. 论文提出的方法论

- **核心思想**：通过解耦有用性和安全性的偏好标注，构造双偏好数据集；在此基础上训练独立的奖励模型（RM-V）和成本模型（CM-V）；并在强化学习阶段采用基于拉格朗日的约束优化，在最大化有用性奖励的同时，确保模型输出满足安全成本约束。
- **关键技术细节**：
  - **BeaverTails-V 数据集**：包含约32k条（图像-文本-响应）三元组，每条数据同时标注了有用性偏好和安全偏好，并且安全标签进一步细分为 *minor*、*moderate*、*severe* 三级。数据构建流程包括：基于分类体系的关键词图像搜索、多模型响应生成、嵌入相似度筛选、GPT-4o 辅助标注与人工校验。
  - **Beaver-Guard-V 护栏系统**：基于多级安全标签微调而成的二分类/多级分类模型，可对输入提示和生成响应进行“过滤-拒绝-重生成”，有效降低攻击成功率。
  - **Safe RLHF-V 算法**：
    - 训练 RM-V：使用有用性偏好数据集 \( D_R \) 训练，损失函数为对比排序损失。
    - 训练 CM-V：使用安全性偏好数据集 \( D_C \) 训练，损失函数结合了对比排序和二元分类项（融入安全标签）。
    - **约束优化阶段**：优化目标为 \( \max_\theta \mathbb{E}[R_\phi(y,x)] \)，约束为 \( C_\psi(y,x) \le 0 \)。引入拉格朗日乘子 \( \lambda \) 动态更新，并加入预算边界（budget bound）投影操作以稳定训练：\( \lambda \leftarrow \text{proj}_\lambda[\lambda - \alpha(b - J^C(\theta))] \)，其中 \( J^C \) 是成本模型的估计值。整体损失函数为 \( L_{\text{SafeRL}} = \frac{1}{1+\lambda}(L_{\text{SafeRL}}^R - \lambda L_{\text{SafeRL}}^C) \)。

### 3. 实验设计

- **数据集与场景**：
  - 训练集：BeaverTails-V（双偏好，多级安全标签）。
  - 评测基准：BeaverTails-V 内测集、MM-SafetyBench、SPA-VL、VLGuard、VLSBench。
- **基准方法**：RLHF-V、Llava-RLHF、DPO（有用性 / 安全性）、PPO（有用性 / 安全性）、MM-RLHF（有用性 / 安全性）。所有方法在相同基座模型上对比。
- **评估指标**：胜率（Win Rate）由 GPT-4o 作为评判，分别在有用性和安全性维度给出0-3分。
- **对比方法**：包括单目标优化（仅优化有用性或仅优化安全性）与双目标优化（Safe RLHF-V）。基座模型：LLaVA-1.5-7B、LLaVA-1.6-7B、Qwen2-VL-7B。
- **验证内容**：
  - 主实验：双目标优化与单目标优化的全面对比。
  - 消融实验：RM-V / CM-V 不同数据规模下的准确率；λ 初始值敏感性；静态奖励塑造 vs 动态 λ 更新；训练过程中 λ、reward、cost 的变化趋势；预算边界的影响。
  - 护栏系统评估：与 Llama-Guard-3-11B-Vision 在多个基准上的准确率、精确率、召回率、F1、假阳性率对比，以及不同过滤轮数下的攻击成功率下降情况。

### 4. 资源与算力

论文**未明确说明**所使用的 GPU 型号、数量或具体训练时长。仅在附录中提及使用 Llava-1.5-7B 作为偏好模型初始化的基础模型，以及使用 Align-Anything-TI2T-Instruction-100K 数据集进行 PTX 损失优化。整体算力信息缺失，无法对计算成本进行量化评估。

### 5. 实验数量与充分性

- **实验数量**：包含超过10组对比实验（含不同模型、不同算法变体），以及5类以上的消融实验（数据规模、λ 初始值、静态 vs 动态、训练曲线、护栏过滤轮数）。主结果表（Table 4）涵盖了3种基座模型 × 5个评测集 × 9种方法，共计超过135个数据点。
- **充分性**：实验设计较为全面，覆盖了多模态安全对齐的主要挑战（有用性-安全性权衡、约束优化有效性、护栏系统防御等）。消融实验针对关键设计（预算边界、动态λ）进行了深入分析，论证了算法稳定性。但存在以下不足：所有评测均依赖 GPT-4o 作为自动评判，未提供人工评测或跨评判器的一致性检验；消融实验仅在 Qwen2-VL-7B 一个模型上进行，结论普遍性需验证。
- **客观性与公平性**：在公平性方面，所有对比方法均采用相同的训练数据和基座模型（或明确标出差异），超参数尽量统一，但未能提供各基准方法的超参数调优细节，可能存在未完全对齐的偏差。

### 6. 论文的主要结论与发现

1. **数据集质量**：BeaverTails-V 比现有多模态安全性数据集（SPA-VL、MM-SafetyBench）具有更强的图像-文本关联性，攻击成功率提升了6.8%～24%。多级安全标签使得安全约束粒度更细。
2. **护栏有效性**：Beaver-Guard-V 在多级分类任务上达到85%准确率，F1=0.88，远优于 Llama-Guard-3-11B-Vision（准确率64%，F1=0.74），同时假阳性率仅20%。经过5轮过滤可将攻击成功率平均降低40.9%。
3. **双目标优化效果**：Safe RLHF-V 在几乎所有模型和评测集上同时提升了安全性和有用性：平均安全+34.2%，有用性+34.3%。相比之下，单目标方法（如 DPO、PPO 仅优化安全性）会导致有用性严重下降，反之亦然。
4. **λ 动态更新与预算边界**：静态 λ 导致模型对初始值敏感易崩；采用动态 min-max 更新并加入预算边界后，训练稳定，最终 cost 趋近阈值，λ 逐步衰减至零，说明模型学会了在安全约束内最大化有用性。
5. **RM-V/CM-V 数据需求**：RM-V 在5k偏好数据即可达到82%准确率；CM-V 则需要15k数据才能达到79%准确率，说明安全性建模更困难。

### 7. 优点

- **开创性与系统性**：首次提出完整的多模态安全对齐框架，涵盖数据集、护栏、算法三个关键组件，具有工程实践意义。
- **数据标注精细**：双偏好 + 多级安全标签的设计有效解决了“有用性 vs. 安全性”的标注冲突，为后续约束优化提供了可靠信号来源。
- **算法设计稳健**：引入预算边界与动态 λ 更新，解决了多模态场景下约束优化易崩溃的问题，实验验证了其相对于静态奖励塑造的显著优势。
- **实验全面且开源**：公开数据集、代码、模型，支持可重复研究；实验覆盖多种模型、评测基准和消融维度，论证充分。

### 8. 不足与局限

- **模态局限**：本文仅关注图像-文本双模态，未扩展到视频、音频、3D 等其他模态，通用性受限。
- **评估偏差**：所有安全性和有用性的打分均使用 GPT-4o 作为评判器，未验证 GPT-4o 自身的安全偏倚，也未提供与人工评测的一致性分析，可能引入评判器偏差。
- **模型选择有限**：实验仅在7B量级的基座模型（LLaVA-1.5/1.6、Qwen2-VL-7B）上进行，未验证更大的模型（如 13B/34B）或不同架构（如 LLaMA-Adapter）上的表现，泛化结论受限。
- **训练不稳定性**：论文承认多模态约束优化训练过程高度不稳定，故障定位困难，尽管预算边界缓解了问题，但潜在失败模式仍可能导致模型崩溃，未提供系统性故障分析。
- **算力信息缺失**：未报告训练所需的 GPU 类型、数量、时长，对工业界复制和资源评估不友好。
- **潜在伦理风险**：作者虽声明数据集开源用于安全性研究，但高质多模态有害数据可能被恶意利用，论文未提供足够使用限制或监控机制。

（完）
