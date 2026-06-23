---
title: Uncertainty-Aware Tree Search for Efficient LLM Reasoning
title_zh: 不确定性感知树搜索以实现高效LLM推理
authors: "Jianguo Huang, Zhiyi Lyu, Fuxiang Zhang, Yanchen Deng, Deheng Ye, Bo An"
date: 2025-09-20
pdf: "https://openreview.net/pdf?id=RrLQbXCflj"
tags: ["query:luq"]
score: 6.0
evidence: 不确定性感知的树搜索用于LLM推理
tldr: 现有树搜索方法在每个推理分支上分配相同计算预算，忽略了不确定性差异导致冗余。本文提出不确定性感知树搜索，利用分支不确定性动态分配采样预算，在保证推理质量的同时显著减少标记消耗。理论分析和实验验证了方法的有效性，为高效LLM推理提供了新思路。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-rrlqbxcflj/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1194, \"height\": 593, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-rrlqbxcflj/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1379, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-rrlqbxcflj/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 317, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-rrlqbxcflj/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 722, \"height\": 581, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-rrlqbxcflj/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1191, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-rrlqbxcflj/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1194, \"height\": 578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-rrlqbxcflj/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1188, \"height\": 585, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-rrlqbxcflj/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1188, \"height\": 575, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-rrlqbxcflj/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 580, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-rrlqbxcflj/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 724, \"height\": 560, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-rrlqbxcflj/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 580, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-rrlqbxcflj/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1376, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-rrlqbxcflj/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1396, \"height\": 1386, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-rrlqbxcflj/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1448, \"height\": 421, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-rrlqbxcflj/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 665, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-rrlqbxcflj/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1446, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-rrlqbxcflj/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1443, \"height\": 228, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-rrlqbxcflj/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1445, \"height\": 347, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-rrlqbxcflj/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1451, \"height\": 170, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-rrlqbxcflj/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1442, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-rrlqbxcflj/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1447, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-rrlqbxcflj/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1444, \"height\": 504, \"label\": \"Table\"}]"
motivation: 现有树搜索方法对每个推理分支平等分配计算预算，导致大量标记冗余。
method: 提出基于分支不确定性的自适应采样预算分配策略，实现概率保证下的高效推理。
result: 在多种推理任务上，所提方法在保持准确率的同时大幅降低标记消耗。
conclusion: 不确定性感知机制可显著提升LLM推理效率，验证了分支不确定性的重要性。
---

## Abstract
Tree search is an important class of methods for improving the multi-step reasoning capability of Large Language Models (LLMs) by explicitly exploring the intermediate steps on a search tree guided by a value function. However, the existing tree-search methods often devote equal computational budgets across different reasoning branches regardless of the associated uncertainty, causing significantly high token consumption. In this paper, we first conduct a pilot study to reveal the ubiquitous semantic redundancy of reasoning trajectories starting from an intermediate reasoning step. Such highly certain reasoning steps will ultimately reduce the diversity of the final answers. Further, we theoretically show that under a probabilistic guarantee, the sampling budget required to maintain fixed generation quality grows proportionally with the step uncertainty. Built on top of this, we propose \textbf{Uncertainty-Aware Allocation} (UAA), a plug-and-play framework that allocates search budget adaptively according to the step-wise uncertainty. In particular, UAA detects for highly certain reasoning steps and incorporates (i) uncertainty-aware pruning (UAP) to keep only a high-quality subset of candidate actions, and (ii) uncertainty-aware budgeting (UAB) to shrink the next-step expansion budget. Extensive empirical evaluations demonstrate that UAA can significantly reduce token consumption and wall-clock time without hurting accuracy when applied to Beam Search and MCTS.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题背景**：大语言模型（LLM）在进行多步推理（如数学求解、逻辑推理等）时，常采用基于值函数引导的树搜索算法（如Beam Search、MCTS）。然而，现有方法为不同推理分支分配**相同的计算预算**，忽略了分支内在的不确定性差异，导致大量不必要的token消耗和计算延迟。
- **研究动机**：作者通过实验发现，从同一中间推理步骤出发的后续推理轨迹往往具有高度语义相似性（冗余性），且这种冗余对最终答案的多样性贡献极小；理论上证明，在概率保证下，保持固定生成质量所需的采样预算与步骤不确定性成正比。因此，**根据步骤不确定性动态分配计算预算**是提升效率的关键。
- **整体含义**：本文旨在设计一种**无需额外模型、无需微调**的即插即用框架，通过识别低不确定性步骤并自适应缩减搜索预算，在**不牺牲推理准确率**的前提下大幅降低token消耗和推理时间，使树搜索方法更实用。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：基于步骤不确定性（离散程度）调整该步骤的搜索预算。低不确定性步骤的候选动作高度相似，进一步探索收益有限，因此应减少其扩展预算；高不确定性步骤则保留完整预算以保证探索多样性。
- **技术细节**：
  - **不确定性估计**：通过采样多个候选动作，计算其嵌入向量对的平均余弦不相似度（1 - 余弦相似度）作为不确定性代理。嵌入向量取自模型最后token的特征向量。
  - **不确定性感知剪枝（UAP）**：当步骤不确定性低于阈值λ时，仅保留值函数最高的前ˆk个候选动作；否则保留全部。
  - **不确定性感知预算分配（UAB）**：对于保留的每个候选动作，若其父节点不确定性低，则下一层扩展预算设为较小的ˆB；若不确定性高，则使用完整预算B。
- **理论支撑**：Proposition 2和Corollary 1证明，采样预算n与步骤不确定性Var(At|st)成正比，即低不确定性步骤可用更少样本近似条件熵，从而减少计算。
- **整体流程**：UAA嵌入现有树搜索（Beam Search、MCTS、DVTS、REBASE）的扩展环节，通过上述两个操作动态调整结构。

## 3. 实验设计
- **数据集**：GSM8K（100例）、MATH-500（100例）、AIME24（数学竞赛题）；额外在StrategyQA（逻辑推理）和Blocksworld（规划任务）上验证泛化性。
- **基准方法**：对比基础Beam Search、MCTS、LiteSearch（效率导向方法），以及DVTS、REBASE等高级搜索算法。
- **模型**：Llama3.1-8B-Instruct、Qwen3-32B（黑盒设置下使用GPT-4o）。
- **值函数**：两类——模型置信度（平均log概率）和过程奖励模型（PRM，从Llama3.1-8B微调）。
- **评价指标**：准确率（精确匹配+多数投票）、平均token数、墙钟时间。
- **超参数**：Beam数量16，树宽度4，深度40；UAA中λ=0.5，ˆk=2，ˆB=3（BS）/2（MCTS）。

## 4. 资源与算力
- **计算资源**：明确报告使用**两个NVIDIA NVL H100 94GB GPU**。
- **训练时长**：未说明完整训练时长，但提到模型为已有预训练模型，PRM通过RLHFlow微调，未提供具体时间。推理实验重复三次取均值。

## 5. 实验数量与充分性
- **实验组数**：覆盖**3个数学基准×2种搜索算法×2种值函数**，共12组主实验；外加：
  - 消融研究（λ阈值、UAP/UAB组件）；
  - 不确定性估计器对比（embedding、置信度方差、PRM方差）；
  - 与DVTS、REBASE结合实验；
  - 黑盒设置（GPT-4o）实验；
  - 额外任务（StrategyQA、Blocksworld）。
- **充分性评价**：实验设计较**全面**，涵盖了不同模型规模、搜索方法、值函数、任务类型，并进行了组件与超参数消融。但每个数学基准仅取前100例，样本量相对有限，可能影响统计稳定性。此外，未在大规模全量数据集（如完整GSM8K）上验证效率增益的普适性。总体公平、客观，对比基线设置一致。

## 6. 主要结论与发现
- UAA在Beam Search和MCTS上普遍**降低20%~50% token消耗**和**30%~60%墙钟时间**，同时**准确率基本保持不变**（部分任务略有提升）。
- 黑盒环境下，即使无法获取嵌入向量，使用置信度或PRM分数的方差作为不确定性代理仍可取得相近效果。
- 消融表明：UAB贡献主要成本节省，UAP帮助保留高质量轨迹，两者组合最优；阈值λ控制效率-准确率平滑权衡。
- UAA可无缝集成到高级树搜索方法（DVTS、REBASE）中，进一步降低开销而不损害性能。

## 7. 优点
- **训练无关/即插即用**：无需额外模型、无需微调，直接嵌入现有推理流程。
- **适用于黑盒与白盒**：当嵌入不可用时，用评分方差替代仍有效。
- **理论基础坚实**：提供信息论分析，证明采样预算与不确定性成正比。
- **效率提升显著**：实验一致显示大幅度减少token和时间，且不降准确率。
- **泛化性强**：在多种搜索算法、LLM大小、任务类型（数学、逻辑、规划）上均有效。

## 8. 不足与局限（作者自述+客观分析）
- **固定阈值与预算**：UAA使用固定的λ、ˆk、ˆB，可能不适应不同推理深度或任务分布。未来可探索自适应动态调整。
- **开放域泛化未知**：仅在受限的数学和常识推理上测试，对开放域复杂任务（如长文生成、多轮对话）尚未验证。
- **代理不确定性**：embedding dispersion虽简单高效，但近似效果依赖表示质量，对于高度语境化或逻辑链条复杂的情况可能不够鲁棒。
- **实验规模有限**：数学数据集仅使用前100例，大规模全量实验缺失，可能影响结论的统计可靠性。
- **计算资源未详述**：未给出PRM微调的具体成本及总推理时间，读者难以完全复现算力量级。
- **消融实验缺乏对更大模型（如70B以上）的验证**。

（完）
