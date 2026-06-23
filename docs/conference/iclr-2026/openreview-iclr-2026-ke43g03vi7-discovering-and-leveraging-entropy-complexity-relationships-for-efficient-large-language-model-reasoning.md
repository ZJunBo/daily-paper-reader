---
title: Discovering and Leveraging Entropy-Complexity Relationships for Efficient Large Language Model Reasoning
title_zh: 发现并利用熵-复杂度关系实现高效大语言模型推理
authors: "Yang Mingzheng, Zhenyu Tan, Kai Zhang, Jianhui Ma, Zhang Xuling, Cai Yuchen, Xu An, Ding Cao, Enhong Chen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=KE43G03vI7"
tags: ["query:luq"]
score: 6.0
evidence: 利用熵作为复杂度信号用于LLM推理
tldr: 针对LLM过度推理问题，论文提出利用生成过程中的token级熵作为问题复杂度的内在度量，进而设计两阶段自适应推理训练框架。低熵表示高置信度直接回答，高熵触发详细推理。该方法在效率与准确性间取得平衡，为LLM推理优化提供新思路。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1460, \"height\": 688, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1298, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 443, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1428, \"height\": 408, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1446, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 939, \"height\": 408, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1012, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1448, \"height\": 963, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1437, \"height\": 619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1439, \"height\": 823, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1165, \"height\": 880, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1448, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1441, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1436, \"height\": 616, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1170, \"height\": 876, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1429, \"height\": 586, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ke43g03vi7/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1501, \"height\": 623, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-ke43g03vi7/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 1199, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ke43g03vi7/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 888, \"height\": 355, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ke43g03vi7/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1492, \"height\": 726, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ke43g03vi7/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 846, \"height\": 608, \"label\": \"Table\"}]"
motivation: LLM存在过度推理问题，导致计算浪费，需要根据问题复杂度自适应调整推理链长度。
method: 提出基于token级熵的复杂度评估方法，并构建两阶段训练框架实现自适应推理。
result: 实验表明该方法有效减少冗余推理，提升效率同时保持或改善准确性。
conclusion: 熵可以作为引导LLM自适应推理的有效信号，提升模型效率。
---

## Abstract
Large Language Models (LLMs) suffer from "overthinking" — generating excessive reasoning chains even for simple problems, leading to computational inefficiency and potential accuracy degradation. To address this inefficiency, we systematically show that response entropy serves as an effective intrinsic measure of problem complexity in LLM reasoning. Our key insight is that token-level entropy during generation provides a principled signal for complexity assessment, where low entropy indicates high confidence suitable for direct answers, while high entropy signals the need for detailed reasoning. Building on this entropy-complexity relationship, we propose a novel two-stage training framework for adaptive reasoning. In Stage 1, we use Supervised Fine-Tuning (SFT) on NoThinking exemplars (concise direct answers without explicit reasoning) to endow the model with concise answering capability. In Stage 2, we perform offline Proximal Policy Optimization (PPO) with an entropy-aware reward function to train models to dynamically select between concise and full reasoning modes based on problem complexity. This offline approach offers greater stability and efficiency compared to online RL methods. Experiments on MATH500, AIME24 and GPQA benchmarks demonstrate that our method significantly reduces response length while maintaining accuracy, validating entropy as both a diagnostic tool and training signal for efficient LLM reasoning. Our code is available via https://anonymous.4open.science/r/Efficient-Reasoning-8BA6.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）
**问题**：大型语言模型（LLM）在进行推理时存在“过度思考”（overthinking）现象——即使是简单问题（如“2+3=?”）也会生成数百甚至上千 token 的冗长推理链，导致计算浪费、延迟增加，甚至因过多推理引入错误。现有方法（如 inference-time 动态分配、online RL）存在额外开销或训练不稳定等局限。

**整体目标**：提出一种基于内在复杂度信号的自适应推理框架，使模型能在训练阶段学会根据问题复杂度动态选择直接回答（NoThinking）或完整推理（Thinking），在推理阶段无需额外开销，在保持准确性的同时显著缩短响应长度。

**核心洞察**：模型在生成 token 时的**分布熵**（token-level entropy）可以作为问题复杂度的有效内在度量——低熵表示高置信度，适合直接回答；高熵表示不确定性高，需要详细推理。

## 2. 论文提出的方法论
### 核心思想
利用 token 级熵作为问题复杂度的连续、内在信号，构建两阶段训练框架，使模型能够自适应地选择推理模式。

### 关键技术细节
1. **熵提取与过滤**：
   - 计算每个 token 的熵 \( H_t = -\sum_i p_{t,i} \log p_{t,i} \)。
   - 只保留熵高于阈值 \( \theta = 0.2 \) 的 token，计算平均熵 \( H_{\text{avg}} \) 作为问题复杂度的代表。
   - 实验验证该平均熵与人工标注难度等级、多采样平均准确率和长度构成的代理难度指标 \( D = L_s - A_s \) 高度相关。

2. **两阶段训练框架**：
   - **Stage 1: Supervised Fine-Tuning (SFT)**：从 MATH 训练集中选取 Level 1 & 2 的 1,912 道题，通过 prompt 注入（如 “Okay, I think I have finished reasoning.”）构造 NoThinking 样本（直接给出答案，无显式思考链），训练模型获得直接回答的能力。
   - **Stage 2: Offline Proximal Policy Optimization (Offline PPO)**：
     - 以 Stage 1 模型为参考策略 \( \pi_{\text{ref}} \)，对每个问题采样 16 个候选响应构建离线数据集。
     - 设计多组件奖励函数：
       - 准确性奖励 \( R_{\text{acc}} \)：正确为 1，否则 0。
       - 效率惩罚 \( R_{\text{eff}} \)：响应长度超过参考模型平均长度的部分给予负惩罚。
       - 难度自适应奖励 \( R_{\text{diff}} \)：根据平均熵 \( H_{\text{avg}} \) 鼓励对低熵问题直接回答，对高熵问题完整推理。
     - 计算每个问题的基线奖励 \( \bar{R}_{\text{ref}} \)，然后使用优势值 \( R_{\text{adv}} = R_{\text{base}} - \bar{R}_{\text{ref}} \) 进行 PPO 优化（采用 clip 机制防止策略偏离过大）。

### 公式说明（文字流程）
- 将奖励信号与响应复杂度自适应结合，通过离线采样的方式避免在线 RL 的不稳定性和高计算成本。

## 3. 实验设计
### 数据集与场景
- **训练集**：MATH 训练集（选取 5,000 道题，其中 1,912 道用于 SFT）。
- **测试集**：
  - MATH500（500 题，高中难度数学，含人工标注难度等级 1~5）
  - AIME24（2024 年美国数学邀请赛题目，高难度竞赛数学）
  - GPQA（研究生级 STEM 问答）
- **额外泛化测试**：MMLU（多领域知识问答，用于评估迁移性）

### Benchmark
- **评估指标**：Pass@1 准确率（使用 Open-R1 框架）、响应长度（生成 token 数，含 `<think>` 标签内 token）。
- **基线方法**：
  - Original Thinking（原始推理模型）
  - Original NoThinking（强制跳过思考）
  - Fast-Solving Prompt（提示快速求解）
  - SFT（仅用最短正确解进行有监督微调）
  - DPO（选择最短正确解 vs 最长解进行直接偏好优化）
  - O1-Pruner（离线 PPO 风格，基于长度启发）

### 模型
- DeepSeek-R1-Distill-Qwen-1.5B
- DeepSeek-R1-Distill-Qwen-7B
- DeepSeek-R1-Distill-Llama-8B

### 对比方法
完整评估了 6 个基线 + 本文方法，在主表（Table 1）中展示。

## 4. 资源与算力
论文明确说明：
- 训练在 **8 块 NVIDIA A100 (80GB) GPU** 上进行。
- **Stage 1 (SFT)**：学习率 5e-6，训练 3 epoch，使用 2 块 A100，耗时约 10 分钟。
- **Stage 2 (Offline PPO)**：学习率 5e-7，训练 1 epoch，使用 4 块 A100，耗时约 1.5 小时。
- 未说明多组实验的重复运行总资源消耗。

## 5. 实验数量与充分性
### 实验组数
- **主实验**：3 种模型 × 3 个数据集 = 9 组结果，对应 Table 1。
- **消融实验**：3 种模型，比较完整框架 vs. 去掉 PPO（仅 SFT） vs. 去掉置信度奖励（w/o Confidence Reward），共 9 组，对应 Table 2。
- **熵阈值敏感性**：DeepSeek-8B 模型，5 个阈值（0, 0.01, 0.1, 0.2, 0.5）在 3 个数据集上的表现，共 15 组，对应 Table 3。
- **跨数据集熵分析**：GSM8K、MATH500、AIME24 上的熵分布及统计（附录 A.3），提供多维度验证。
- **泛化测试**：MMLU 数据集上 3 种模型的比较，共 3 组，对应 Table 4。
- **案例研究**：展示了 easy 和 hard 题目上 1.5B 和 8B 模型在 PPO 前后的输出对比（附录 D）。

### 充分性评价
- **优点**：覆盖多模型（不同规模、架构）、多数据集（不同难度、领域）、多基线（包括 SOTA 同类方法），消融完整，阈值敏感性分析详尽。
- **不足**：主实验结果（Table 1）未报告多次运行的平均值和标准差，无法判断统计显著性；Pass@1 为单次采样，未采用多次采样平均（除分析时外）；部分消融实验的 token 长度差异较大，可能引入混淆；未在非数学推理任务（如常识推理、代码生成）上验证。

## 6. 论文的主要结论与发现
1. **熵作为复杂度信号**：token 级平均熵（过滤后）与问题难度（人工标注或多采样代理）呈现系统正相关，低熵对应简单问题，高熵对应复杂问题。
2. **两阶段训练有效**：SFT+Offline PPO 框架在多个模型和数据集上显著降低响应长度（最高 47.5%），同时保持甚至提升准确率（最高 +3.3%）。
3. **自适应机制**：训练后模型在简单问题上更多选择 NoThinking 模式（直接回答），在复杂问题上保持 Thinking 模式（完整推理），且 NoThinking 的准确率得到提升。
4. **离线 PPO 优势**：相比在线 RL，该方法训练稳定、计算开销低。
5. **泛化能力**：在 MMLU 上也能在几乎不损失准确率的情况下大幅减少 token。

## 7. 优点
- **理论创新**：首次系统验证 token 级熵可作为 LLM 推理复杂度内在信号，为自适应推理提供了信息论基础。
- **方法设计**：两阶段框架结合 SFT 的稳定性和离线 PPO 的优化能力，避免在线 RL 的不稳定和高成本；奖励函数融合准确性、效率和难度自适应，设计合理。
- **实验全面**：覆盖不同规模（1.5B~8B）和架构（Qwen、Llama）的模型，多重数据集和基线对比，消融和阈值敏感性分析详尽。
- **实用性**：方法完全在训练阶段优化，推理时无额外开销，适合资源受限环境。
- **代码开源**：提供了匿名仓库，便于复现。

## 8. 不足与局限
- **领域限制**：方法仅在数学推理任务上验证，熵-复杂度关系在其他领域（如常识推理、代码生成、开放问答）是否成立仍不确定，需要更多验证。
- **阈值依赖**：使用离散的熵阈值（0.2）进行过滤和奖励计算，需要针对不同任务手动调整，缺乏连续自适应机制。
- **训练数据偏差**：Stage 1 的 NoThinking 样本仅从 MATH 训练集中最低难度（Level 1 & 2）选取，可能无法充分覆盖中等难度的直接回答情况；训练数据集整体仅使用 MATH 训练集（5,000 题），未在更大或更多样化的数据上进行。
- **实验统计不充分**：主结果未报告多次运行的标准差或置信区间，消融实验也未进行多次重复，结论的可靠性有待加强随机性控制。
- **未与其他高效推理方法（如 CoT 压缩、推理步剪枝）全面对比**：基线选择集中在 RL/偏好优化方法，缺少对基于模型压缩或蒸馏方法的对比。
- **模型限制**：仅使用 DeepSeek 蒸馏模型系列，未在更大模型（如 70B）或非蒸馏模型上验证。

（完）
