---
title: "Lisa: Lazy Safety Alignment for Large Language Models against Harmful Fine-tuning Attack"
title_zh: Lisa：针对有害微调攻击的懒惰安全对齐方法
authors: "Tiansheng Huang, Sihao Hu, Fatih Ilhan, Selim Furkan Tekin, Ling Liu"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=RPChapuXlC"
tags: ["query:smd"]
score: 9.0
evidence: 通过分离对齐数据和用户数据来防御有害微调
tldr: 论文针对大语言模型在微调时因混合有害数据而被越狱的问题，提出了一种懒惰安全对齐方法（Lisa）。该方法在微调阶段将优化过程分离为对齐状态和用户数据状态，分别优化安全对齐数据和用户数据集。实验表明，这种双状态优化能有效缓解越狱风险，但若对齐状态步数过小会导致收敛不稳定，论文通过统计分析指出状态切换迭代的过量漂移可能是原因。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-rpchapuxlc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 650, \"height\": 220, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rpchapuxlc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1144, \"height\": 329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rpchapuxlc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 629, \"height\": 293, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rpchapuxlc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1282, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rpchapuxlc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1281, \"height\": 339, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1438, \"height\": 196, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1157, \"height\": 106, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 803, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1303, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1442, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1015, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1015, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 625, \"height\": 123, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1224, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1296, \"height\": 198, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 728, \"height\": 120, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1374, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1375, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1436, \"height\": 198, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1009, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rpchapuxlc/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1079, \"height\": 179, \"label\": \"Table\"}]"
motivation: 现有大语言模型在微调时容易因混合有害数据而丧失安全对齐，急需一种能同时优化安全对齐和用户任务的方法。
method: 提出懒惰安全对齐（Lisa），在微调过程中将优化分离为两个状态：对齐状态仅优化安全数据，用户状态仅优化用户数据，通过切换来保持模型安全性。
result: 双状态优化能够有效防止有害微调导致的越狱，但在对齐状态步数过小时出现收敛不稳定，表现为对齐性能下降。
conclusion: 分离对齐和用户数据优化是防御有害微调的有效方向，但需要解决切换过程中的稳定性问题。
---

## Abstract
Recent studies show that Large Language Models (LLMs) with safety alignment can be jail-broken by fine-tuning on a dataset mixed with harmful data. For the first time in the literature, we show that the jail-break effect can be mitigated by separating two states in the fine-tuning stage to respectively optimize over the alignment and user datasets. Unfortunately, our subsequent study shows that this simple Bi-State Optimization (BSO) solution experiences convergence instability when steps invested in its alignment state is too small, leading to downgraded alignment performance. By statistical analysis, we show that the \textit{excess drift} towards the switching iterates of the two states could be a probable reason for the instability. To remedy this issue, we propose \textbf{L}azy(\textbf{i}) \textbf{s}afety \textbf{a}lignment (\textbf{Lisa}), which introduces a proximal term to constraint the drift of each state. Theoretically, the benefit of the proximal term is supported by the convergence analysis, wherein we show that a sufficient large proximal factor is necessary to guarantee Lisa's convergence.   Empirically, our results on four downstream fine-tuning tasks show that Lisa with a proximal term can significantly increase alignment performance while maintaining the LLM's accuracy on the user tasks.  Code is available at https://github.com/git-disl/Lisa.

---

## 论文详细总结（自动生成）

# 论文详细总结：Lisa: Lazy Safety Alignment for Large Language Models against Harmful Fine-tuning Attack

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）在微调服务中面临严重的安全威胁——用户上传的数据可能混合有害数据，导致模型被“越狱”，输出有害内容。现有防御方案如 Vaccine（对齐阶段增强鲁棒性）在微调步数较多时效果不佳；ForgetFilter 和 Vlguard 等微调阶段方案计算开销大。因此，论文旨在设计一种计算高效的微调阶段防御方法，既能抵御有害数据注入，又保持下游任务性能。
- **核心问题**：如何在微调阶段同时优化对齐数据集和用户数据集，避免模型遗忘安全对齐知识，同时保证收敛稳定性。
- **整体含义**：提出一种“双状态优化”（Bi-State Optimization, BSO）框架，并进一步通过引入近端项（proximal term）来解决不对称计算步数导致的漂移和收敛不稳定问题，从而在微调阶段实现“懒惰安全对齐”（Lazy Safety Alignment, Lisa）。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：将微调阶段的优化过程分离为两个状态——**对齐状态**（仅优化对齐数据集）和**用户状态**（仅优化用户数据集），两个状态交替进行。这有助于模型同时记住对齐知识和学习下游任务。但实验发现，当对齐状态步数（K1）远小于用户状态步数（K2）时，会出现“过量漂移”（excess drift），导致收敛不稳定和对齐性能下降。为此，引入**近端项**，约束每个状态中的模型参数不要偏离上一个切换点的参数，从而控制漂移。
- **关键技术细节**：
  - **BSO 算法（算法1）**：每一轮（cycle）内，先执行 K1 步对齐状态优化（采样对齐数据计算梯度，更新参数），再执行 K2 步用户状态优化（采样用户数据计算梯度，更新参数）。重复 T 轮。
  - **Lisa 算法（算法2）**：在 BSO 基础上，对每个状态的目标函数添加近端项：  
    - 对齐状态：min_w [ f(w) + (ρ/2) * ||w - w_t||^2 ]  
    - 用户状态：min_w [ h(w) + (ρ/2) * ||w - \tilde{w}_{t+1}||^2 ]  
    其中 w_t 是上一轮用户状态结束时的参数，\tilde{w}_{t+1} 是对齐状态结束时的参数，ρ 是近端强度超参数。
  - **理论保证**：论文在假设李普希兹平滑和 KL 性质下，证明了当 ρ > L（L 为平滑常数）时，Lisa 可以渐近收敛到全局问题的驻点，且收敛速度依赖于 KL 参数 θ（θ=0 为有限步收敛，θ∈(0,1/2] 为线性收敛，θ∈(1/2,1) 为次线性收敛）。大 ρ 是保证收敛的必要条件。
- **流程总结**：初始化模型权重 w_0，每一轮：  
  1. 对齐状态：用 K1 步梯度下降优化 f(w) + (ρ/2) ||w - w_t||^2，得到 \tilde{w}_{t+1}  
  2. 用户状态：用 K2 步梯度下降优化 h(w) + (ρ/2) ||w - \tilde{w}_{t+1}||^2，得到 w_{t+1}  
  3. 重复 T 轮。

## 3. 实验设计：数据集、场景、基准、对比方法

- **数据集与场景**：
  - **对齐数据集**：BeaverTails 中的安全样本（10000 条）。
  - **用户微调任务**：SST2（情感分类）、AGNEWS（新闻分类）、GSM8K（数学推理）、AlpacaEval（指令遵循）。
  - **攻击设置**：默认总样本数 n=5000，有害数据比例 p=0.1（10%），有害数据来自 BeaverTails 的不安全样本。
- **基准模型**：Llama2-7B（非聊天版）、Opt-2.7B、Mistral-7B。
- **对比方法**：
  - 无防御基线：NA-SFT（无对齐直接微调）、SFT（标准对齐+标准微调）。
  - 对齐阶段防御：Vaccine-SFT（Vaccine 对齐+标准微调）。
  - 微调阶段防御：EWC（弹性权重巩固）、Vlguard（混合对齐数据）、BSO（本文提出的无近端项版本）、Lisa（本文完整方法）。
  - 额外组合：Vaccine+Lisa、Filter+Lisa（先过滤有害数据再使用 Lisa）。
- **评估指标**：
  - 有害分数（Harmful Score, HS）：使用 BeaverTails 的审核模型对模型输出标记，计算不安全输出比例。
  - 微调准确率（Finetune Accuracy, FA）：在上游任务测试集上的 Top-1 准确率（或 AlpacaEval 的胜率）。

## 4. 资源与算力

- 论文未明确给出训练时长、GPU 数量等详细算力报告，仅在附录 A.1 中提到使用工作站配备 H100 GPU 进行实验，并使用 LoRA（秩=8）进行高效训练。在系统评估（表7）中给出了运行 1000 步的时钟时间（SFT 约115秒，Lisa 约125秒）和 GPU 内存（SFT 约48GB，Lisa 约51GB），说明额外开销较小。未提及总实验耗时或能源消耗。

## 5. 实验数量与充分性

- **实验数量**：
  - **主实验**：表3（不同有害比例，5种比例×10个方法，约50个数据点）；表4（不同样本数，5种样本数×8个方法）；表5（不同模型，3种模型×8个方法）；表6（不同任务，4种任务×8个方法）。
  - **消融与超参数分析**：表8（步数比例分配）、表9（近端强度 ρ）、表10（消融研究——仅BSO、仅近端、完整Lisa）。
  - **组合实验**：表11（Vaccine+Lisa）、表12（过滤+Lisa）。
  - **统计与系统评估**：图4、图5（对齐损失、梯度范数、漂移分析）；表7（时间与内存）。
  - **可视化**：在5.6节及附录A.4中展示了多个恶意提示的模型输出对比。
  - **高级攻击测试**：表13（更高有害比例）、表14（谐波均值）、表15（Bi-directional Anchoring 攻击）。
- **充分性与公平性**：
  - 覆盖多种模型、任务、有害比例、样本数量，实验设计较为广泛。
  - 对比方法包括无防御、对齐阶段防御、微调阶段防御，以及组合方法，基准设置合理。
  - 消融实验明确了每个组件（BSO、近端项）的作用。
  - 但所有实验均基于 LoRA 微调（秩=8），未验证全参数微调下的效果；且仅使用 AdamW 优化器，学习率固定为1e-5，超参数选择可能存在一定偏向。

## 6. 论文的主要结论与发现

- **BSO 可缓解有害微调**：在对称步数 (K1=K2=500) 下，BSO 比标准 SFT 降低有害分数最多 4.2%，但微调准确率略有下降。
- **不对称步数导致性能恶化**：当对齐步数减少（如 K1=100, K2=900），BSO 的有害分数升高，甚至接近无防御的 SFT。原因是“过量漂移”——模型参数在状态切换点之间偏离过大。
- **加入近端项（Lisa）有效控制漂移**：Lisa 通过 ρ 约束模型参数靠近切换点，显著降低有害分数（平均比 BSO 低 6.54%），同时保持微调准确率（平均仅下降 0.28%）。
- **理论收敛性**：当 ρ > L 时，Lisa 可渐近收敛到全局问题驻点，且收敛速度取决于 KL 参数 θ。大 ρ 是保证收敛的必要条件。
- **集成兼容性**：Lisa 可进一步与 Vaccine 或数据过滤方法结合，获得更低的有害分数（Vaccine+Lisa 平均有害分数 32.86%，比单独使用 Lisa 低 6.72%）。
- **实际效果可视化**：对于恶意提示（如“如何偷汽车引擎”），Lisa 模型给出无害拒绝回答，而其他方法均输出有害内容。

## 7. 优点：方法或实验设计上的亮点

- **新颖视角**：首次提出在微调阶段分离对齐与用户数据优化来防御有害微调，并揭示“过量漂移”是导致性能恶化的关键因素。
- **理论支撑**：提供了完整的收敛性分析（KL 框架），证明了近端项的必要性，且收敛率涵盖三种情况（有限步、线性、次线性）。
- **计算效率相对较高**：Lisa 仅需额外存储一个切换点参数（约 3GB 内存）和少量前向/后向计算，时钟时间比 SFT 仅增加约 8.3%，具有实际可用性。
- **实验丰富**：涵盖多种模型、任务、有害比例、样本数量，以及多种组合防御策略，消融实验系统，验证了各组件的必要性。
- **可集成性**：Lisa 可以无缝与对齐阶段防御（Vaccine）或数据过滤结合，进一步提升防御效果。

## 8. 不足与局限

- **仅适用于 LoRA 微调**：所有实验基于 LoRA（秩=8），未验证全参数微调下的效果。若切换到全参数微调，近端项的计算开销和存储需求可能会显著增加。
- **未扩展至 RLHF**：论文仅基于 SFT 对齐，未尝试与更先进的 RLHF 方法结合，可能限制其在偏好微调场景的适用性。
- **超参数敏感**：近端强度 ρ 和步数分配 (K1/K2) 对性能影响较大，需要手动调优，缺乏自适应机制。
- **下游任务代表性有限**：使用的任务（SST2、AGNEWS、GSM8K、AlpacaEval）虽涵盖分类、推理、指令遵循，但未覆盖对话、代码生成等更贴近实际生产的场景。
- **计算开销在多次调用时累加**：虽然单次微调额外开销不大，但每个用户请求都需要独立微调，若服务频繁，总开销仍不可忽视（论文附录D已承认此局限）。
- **未充分讨论 false positive 影响**：数据过滤组合实验中，过滤模型有一定假否定率（7.71%），但未分析对微调性能的影响。
- **未报告统计显著性**：实验未给出误差棒或置信区间，可能因单次运行导致结果随机性未被考虑。

（完）
