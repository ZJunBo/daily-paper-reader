---
title: "Learning to Deliberate: Meta-policy Collaboration for Agentic LLMs with Multi-agent Reinforcement Learning"
title_zh: 学会协商：基于多智能体强化学习的元策略协作框架
authors: "Wei Yang, Jesse Thomason"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40228/44189"
tags: ["query:luq"]
score: 4.0
evidence: 多智能体LLM中基于不确定性调整元认知策略
tldr: 多智能体LLM系统因固定协作协议而缺乏自适应能力。本文提出元策略协商框架（MPDF），让智能体学习根据内部不确定性状态（如置信度）采取坚持、改进或让步等元认知行动。通过多智能体强化学习训练，框架能够动态调整协作策略，在复杂推理任务中显著提升效果。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有LLM多智能体协作协议固定，忽略了智能体内部认知状态如不确定性。
method: 设计元认知动作（坚持/改进/让步）并通过多智能体强化学习训练选择策略。
result: 在推理任务上相比固定协议取得明显提升。
conclusion: 利用不确定性作为元认知信号可提升多智能体LLM的协作效率。
---

## Abstract
Multi-agent systems of large language models (LLMs) show promise for complex reasoning, but their effectiveness is often limited by fixed collaboration protocols. These frameworks typically focus on macro-level orchestration while overlooking agents’ internal deliberative capabilities. This critical meta-cognitive blindspot treats agents as passive executors unable to adapt their strategy based on internal cognitive states like uncertainty or confidence. We introduce the Meta-Policy Deliberation Framework (MPDF), where agents learn a decentralized policy over a set of high-level meta-cognitive actions: Persist, Refine, and Concede. To overcome the instability of traditional policy gradients in this setting, we develop SoftRankPO, a novel reinforcement learning algorithm. SoftRankPO stabilizes training by shaping advantages based on the rank of rewards mapped through smooth normal quantiles, making the learning process robust to reward variance. Experiments show that MPDF with SoftRankPO achieves a 4-5% absolute gain in average accuracy across six mathematical and general reasoning benchmarks compared to state-of-the-art heuristic and learning-based multi-agent reasoning algorithms. Our work presents a paradigm for learning adaptive, meta-cognitive policies for multi-agent LLM systems, shifting the focus from designing fixed protocols to learning dynamic, deliberative strategies.

---

## 论文详细总结（自动生成）

# 论文总结：《Learning to Deliberate: Meta-policy Collaboration for Agentic LLMs with Multi-agent Reinforcement Learning》

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：当前多智能体大语言模型（LLM）系统采用固定协作协议（如固定轮数的辩论、同行评审），无法根据智能体内部认知状态（如不确定性、置信度）自适应调整策略，存在“元认知盲点”（Meta-Cognitive Blindspot）和“静态协商策略”（Static Deliberation Strategy）缺陷。
- **整体含义**：论文提出将多智能体协作问题形式化为去中心化部分可观测马尔可夫决策过程（Dec-POMDP），让每个智能体学习一个**元策略**，在高层元认知动作（坚持、改进、让步）间动态选择，从而从“固定协议设计”转向“动态协商策略学习”。

## 2. 方法论核心思想与关键技术细节

### 核心思想
- 每个智能体维护一个轻量级、解耦的策略网络，接收**元认知状态**（由决策方案、推理轮廓、内省置信度三部分构成）作为输入，输出离散的协商动作：Persist（坚持原有答案）、Refine（自我修正改进）、Concede（向同伴答案让步）。
- 通过多智能体强化学习（MARL）训练这些策略，优化全局奖励。

### 关键技术细节
1. **元认知状态空间**：
   - **决策方案（z_ans）**：从模型最终输出解析的标准化答案。
   - **推理轮廓（z_prof）**：结构化自报告特征（推理步数、使用的逻辑运算符、自评置信度）。
   - **内省置信度（z_conf）**：由同一LLM作为评判模型，对完整推理轨迹进行正确性评估后嵌入的向量。
   - 完整观测 `o_i^t = (z_i^t, {z_j^t}_{j≠i})`，策略网络使用交叉注意力机制整合自我与社会上下文。

2. **协商动作空间**：三个离散动作——Persist、Refine、Concede。

3. **SoftRankPO算法**：
   - 针对多智能体环境中奖励稀疏、方差大的问题，提出基于**排序的稳定策略优化**。
   - 先将原始奖励`R`映射为排序后的平滑标准正态分位数得到`A*_i`，再计算零均值、有界方差的优势函数`A_i`。
   - 优化目标：KL正则化的排序匹配损失，使策略隐式奖励与真实奖励的相对形状一致，避免对奖励尺度的敏感。
   - 理论优势：梯度方差与奖励尺度解耦，收敛稳定。

4. **奖励塑造**：
   - **局部自我改进奖励**：`r_local = I[Correct after] - I[Correct before]`。
   - **全局共识影响奖励**：`r_global = I[Consensus_full] - I[Consensus_{-i}]`（排除智能体i后的共识变化）。
   - 总奖励 `r = r_local + r_global`。

5. **训练流程**：
   - 第一阶段：监督微调（SFT）初始化策略，从专家数据学习初始决策。
   - 第二阶段：离线收集轨迹，使用SoftRankPO进行强化学习微调，保持KL信任域。

## 3. 实验设计

### 数据集与场景
- **数学推理**：GSM8K、MATH、AIME、AMC。
- **通用推理**：MMLU。
- **代码生成**：HumanEval。
- 评价指标：数学任务用Solve Rate、MMLU用Accuracy、HumanEval用Pass@1。

### Benchmark对比方法
- **单智能体基线**：Vanilla、CoT、Self-Consistency (SC)。
- **多智能体顺序/辩论**：PHP、LLM-Debate。
- **动态工作流**：DyLAN、AgentPrune、AFlow、GPTSwarm。
- **本文变体**：MPDF (SFT)、MPDF (SFT+PPO)、MPDF (SFT+GRPO)、MPDF (SFT+SoftRankPO)。

### 默认设置
- 智能体数：3；协商轮数：3。
- 骨干模型：Llama-3.1-8B-Instruct、Llama-3.2-3B-Instruct、Qwen2.5-7B-Instruct、Qwen2.5-3B-Instruct。
- 所有结果平均3个随机种子。

## 4. 资源与算力

论文**未明确说明**训练所使用的具体GPU型号、数量及训练时长。仅在方法部分描述了训练流程（SFT + 离线RL），但未提供算力消耗数据。这是论文的一个信息缺失点。

## 5. 实验数量与充分性

- **主实验**：在6个数据集上对比11种基线方法（表1），涵盖单智能体、固定协商、动态工作流等，充分覆盖主流多智能体协作范式。
- **骨干鲁棒性实验**：使用4种不同规模/系列的LLM骨干（LMA-8B/3B、Qwen-7B/3B）进行验证（表2），确认方法通用性。
- **消融实验**：
  - 对比SFT、SFT+PPO、SFT+GRPO、SFT+SoftRankPO（表1）。
  - 奖励尺度鲁棒性测试（指数缩放0.1/1.0/10.0，图5）。
  - 超参数τ的影响（τ∈{0.4,0.6,0.8,1.0,2.0,5.0}，图6）。
  - 通信轮数与智能体数量的影响（图4）。
  - 策略行为变化分析（图7）。
  - Token成本对比（表3）。
- **充分性评价**：实验数量充足，消融设计系统，覆盖核心模块及超参数，公平性（统一种子、报告平均值、多骨干验证）良好。但缺乏代码/训练耗时对比（如训练时间）。

## 6. 主要结论与发现

1. **MPDF+SoftRankPO在所有6个基准上取得平均55.74%准确率，超越最佳基线（AgentPrune 51.60%）约4-5个绝对百分点**。
2. **跨骨干一致提升**：在弱小模型（LMA-3B）上从68.84%提至80.52%；在强模型（Qwen-7B）上从91.05%提至94.47%。
3. **Token成本降低约30%**（47.1k vs 67.2k），得益于代理更倾向Persist高置信答案。
4. **SoftRankPO相比GRPO对奖励尺度变化更鲁棒**，在指数缩放下表现稳定。
5. **策略行为从探索性合作（SFT）转向协调性决策（RL）**：Persist比例从19.1%升至78.8%，表明智能体学会信任高质量初始输出。
6. **最佳超参数τ=0.8**，适当增加排序对比度有助于学习。

## 7. 优点

- **视角创新**：首次将元认知（不确定性、置信度）显式纳入多智能体LLM协作策略学习，克服静态协议局限。
- **算法设计稳健**：SoftRankPO通过排序解耦奖励尺度，理论上有界方差，实际中无需调参适应不同任务。
- **奖励塑造合理**：结合局部自我改进与全局共识影响，实现精细信用分配，无需额外推断。
- **实验充分且公平**：多骨干、多数据集、多基线、多消融，结论可靠。

## 8. 不足与局限

- **计算资源未报告**：缺失GPU类型、数量、训练时长，影响可复现性与成本评估。
- **仅考虑三类动作**：Persist/Refine/Concede，未探索更丰富的元认知动作（如请求外部知识、分解子问题）。
- **离线RL依赖SFT质量**：若SFT初始化较差，可能影响最终收敛效果。
- **无真实世界或更复杂对话场景**：实验限于数学与代码推理，未涉及开放式对话、规划等任务。
- **智能体数量与轮次上限**：实验显示增加至5轮后性能下降，但未深入分析原因（如信息重复、噪声累积）。
- **奖励塑造中“共识”定义依赖正确性**：在无正确答案的开放式任务中无法直接应用。

（完）
