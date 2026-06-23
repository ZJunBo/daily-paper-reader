---
title: "Harnessing Uncertainty: Entropy-Modulated Policy Gradients for Long-Horizon LLM Agents"
title_zh: 驾驭不确定性：面向长程LLM智能体的熵调制策略梯度
authors: "Jiawei Wang, Jiacai Liu, Yuqian Fu, Yingru Li, Xintao Wang, Yuan Lin, Lin Zhang, YuYue, Yang Wang, WANG KE"
date: 2025-09-07
pdf: "https://openreview.net/pdf?id=VSNmchfjgB"
tags: ["query:luq"]
score: 8.0
evidence: 熵调制策略梯度处理不确定性
tldr: 论文发现LLM中策略梯度幅度与熵固有耦合导致更新不稳定，针对长程任务提出熵调制策略梯度方法。通过动态调整梯度大小，对高置信动作保持适度更新，对不确定动作防止过大更新，提升了长程LLM智能体的学习稳定性与性能。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-vsnmchfjgb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1377, \"height\": 746, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vsnmchfjgb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 695, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vsnmchfjgb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 700, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vsnmchfjgb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1516, \"height\": 1090, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vsnmchfjgb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1462, \"height\": 1229, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vsnmchfjgb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1488, \"height\": 1454, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-vsnmchfjgb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1459, \"height\": 665, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vsnmchfjgb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1176, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vsnmchfjgb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 976, \"height\": 779, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vsnmchfjgb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 581, \"height\": 658, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vsnmchfjgb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1451, \"height\": 370, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vsnmchfjgb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1457, \"height\": 295, \"label\": \"Table\"}]"
motivation: LLM策略梯度与熵耦合导致高置信动作更新不足、不确定动作更新过大，影响长程学习。
method: 提出熵调制策略梯度，动态调整梯度幅度以平衡学习稳定性。
result: 在长程任务上显著提升LLM智能体学习效率和稳定性。
conclusion: 利用熵信号调制梯度可有效提升LLM在长程任务中的学习效果。
---

## Abstract
In long-horizon tasks, recent agents based on Large Language Models (LLMs) face a significant challenge that sparse, outcome-based rewards make it difficult to assign credit to intermediate steps. Previous methods mainly focus on creating dense reward signals to guide learning, either through traditional reinforcement learning techniques like inverse reinforcement learning or by using Process Reward Models for step-by-step feedback. In this paper, we identify a fundamental problem in the learning dynamics of LLMs: the magnitude of policy gradients is inherently coupled with the entropy, which leads to inefficient small updates for confident correct actions and potentially destabilizes large updates for uncertain ones. To resolve this, we propose Entropy-Modulated Policy Gradients (EMPG), a framework that recalibrates the learning signal based on step-wise uncertainty and the final task outcome. EMPG amplifies updates for confident correct actions, penalizes confident errors, and attenuates updates from uncertain steps to stabilize exploration. We further introduce a bonus term for future clarity that encourages agents to find more predictable solution paths. Through comprehensive experiments on three challenging agent tasks, WebShop, ALFWorld, and Deep Search, we demonstrate that EMPG achieves substantial performance gains and significantly outperforms strong policy gradient baselines.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题背景**：基于大语言模型（LLM）的智能体在长程（long-horizon）任务（如网页导航、软件工程、深度搜索）中面临**稀疏奖励**的挑战——仅任务完成时提供奖励信号，导致中间步骤的信用分配困难。现有方法尝试用奖励塑形、内在动机或过程奖励模型（PRM）来稠密化奖励，但PRM标注成本高、难以泛化，而稠密化方法在LLM的巨大状态-动作空间中难以扩展。
- **核心发现**：论文**首次识别并形式化了策略梯度中的一个根本问题**：对于softmax策略，**期望梯度范数与策略熵单调耦合**（Proposition 1： $E_{a\sim\pi}[||\nabla_z\log\pi(a|s)||^2] = 1 - \exp(-H_2(\pi))$）。这意味着：高熵（不确定）动作天然产生大梯度，低熵（自信）动作产生小梯度。这种固有动态导致：自信正确步骤的更新太小，学习低效；不确定探索步骤的大梯度噪声会破坏训练稳定性。
- **整体意义**：需要显式地基于步骤不确定性重新校准学习信号，以克服稀疏奖励下的信用分配困难，实现更高效、稳定的长程学习。

## 2. 方法论：核心思想、关键技术细节与算法流程

### 核心思想：熵调制策略梯度（EMPG）

EMPG通过两个互补组件，将粗粒度的轨迹级奖励转化为细粒度的步骤级学习信号：
1. **自校准梯度缩放（Self-Calibrating Gradient Scaling）**：根据步骤级熵动态调整梯度幅度，对抗自然梯度动态。
2. **未来清晰度奖励（Future Clarity Bonus）**：内在动机，鼓励智能体选择导向更可预测（低熵）后续状态的动作。

### 关键技术细节

- **步骤级熵量化**：对每个“推理-行动”步骤 $t$（包含多个token），计算平均token级香农熵 $H_t = -\frac{1}{m}\sum_{j=1}^m \sum_{v\in V} p(v|w_{<j})\log p(v|w_{<j})$。
- **调制优势函数**：对于轨迹 $\tau_i$ 的步骤 $t$，调制优势为：
  $$A_{\text{mod}}^{(i,t)} = A(i) \cdot g(H_t^{(i)}) + \zeta \cdot f(H_{t+1}^{(i)})$$
  - $A(i)$ 是轨迹级优势（如基于GRPO或DAPO计算）。
  - $g(H)$：自校准缩放函数，通过批均值归一化使 $\sum g(H)=1$，具体为：$g(H_t^{(i)}) = \frac{\exp(-k \cdot H_{\text{norm},t}^{(i)})}{\frac{1}{N_B}\sum_{j,t'} \exp(-k \cdot H_{\text{norm},t'}^{(j)})}$。低熵（自信）步骤 $g>1$ 放大更新，高熵步骤 $g<1$ 衰减更新。
  - $f(H_{t+1}) = \exp(-k' \cdot H_{\text{norm},t+1})$：未来清晰度奖励，对下一状态熵低（清晰）给予正奖励。
- **归一化步骤**：
  - 批级熵min-max归一化：$H_{\text{norm}} = (H - \min)/(\max - \min + \epsilon)$。
  - 最终优势零均值归一化（方差缩减）。

### 算法流程（伪代码描述）

1. 初始化策略 $\pi_\theta$。
2. 每轮训练：
   - 运行策略收集一批轨迹 $\mathcal{B} = \{\tau_i\}$。
   - 计算每个轨迹的成果优势 $A(i)$。
   - 计算所有步骤的步骤级熵 $\{H_t\}$，进行批归一化得到 $\{H_{\text{norm},t}\}$。
   - 对所有步骤计算自校准缩放因子 $g(H_t)$（公式6）。
   - 对所有步骤计算未来清晰度奖励 $f(H_{t+1})$（公式7）。
   - 计算调制优势：$A_{\text{mod}}^{(i,t)} = A(i) \cdot g(H_t^{(i)}) + \zeta \cdot f(H_{t+1}^{(i)})$。
   - 对全批调制优势进行零均值归一化得到 $A_{\text{final}}$。
   - 使用 $A_{\text{final}}$ 更新策略参数 $\theta$。

## 3. 实验设计

### 数据集/场景与Benchmark

- **WebShop**：网页导航任务，需复杂指令遵循。
- **ALFWorld**：基于文本的交互环境，结合指令遵循与常识推理。
- **Deep Search**：多步信息检索与综合任务，分为域内（ID：WebWalker、HotpotQA、2WikiMultiHopQA）和域外（OOD：Musique、Bamboogle）测试。
- 均使用**稀疏二进制成功奖励**（0/1）。

### 对比方法

- **基线（RL算法）**：GRPO（Group Relative Policy Optimization）、DAPO（Decoupled Clip and Dynamic Sampling Policy Optimization）。此外还包括Prompting（零样本、ReAct、Reflexion）和PPO、RLOO等。
- **模型**：Qwen2.5-1.5B-Instruct、Qwen2.5-7B-Instruct、Qwen2.5-32B-Instruct，以及LLaMA3.1-8B-Instruct。
- **EMPG作为增强模块**：直接应用于GRPO或DAPO之上，公平对比。

## 4. 资源与算力

- **WebShop/ALFWorld**：
  - 1.5B模型：使用4×A100 GPU。
  - 7B模型：使用8×A100 GPU。
  - 训练150步（step）。
- **Deep Search**（32B模型）：
  - 使用32×A100 GPU。
  - 训练220步（step）。
- 文中未明确给出总训练时长，但在图F.1中展示了学习曲线，训练步数约150步（WebShop/ALFWorld）和220步（Deep Search）。
- 实验基于veRL框架（Verl-Agent扩展）和自研RL框架。

## 5. 实验数量与充分性

### 实验数量

- **主表**：Table 1（WebShop和ALFWorld）报告了多个模型尺寸（1.5B、7B）和多种方法（PPO、RLOO、GRPO、DAPO、GRPO+EMPG、DAPO+EMPG）的对比，结果取3次随机种子平均。
- **Deep Search主表**（Table 2）：DAPO基线 vs. 消融（仅梯度缩放、仅未来奖励、完整EMPG），在ID和OOD上报告。
- **消融研究**：Table 2和文本分析——分别测试梯度缩放和未来奖励的贡献。
- **超参数敏感性**：Table 5（ALFWorld上对 $\zeta$ 和 $k$ 的变化）。
- **跨模型泛化**：Table 6在LLaMA3.1-8B上验证EMPG。
- **学习曲线**：图F.1展示训练过程动态。
- **KL Loss动态**：图2展示稳定性。
- **步骤级熵变化分析**：图3展示不同熵百分位步骤的变化。
- 整体超过10组不同实验设置。

### 实验充分性与公平性

- **充分性**：覆盖了主流RL基线、多个模型规模（1.5B/7B/8B/32B）、多个数据集、必要的消融和敏感性分析、跨架构验证。分析深入（学习曲线、KL loss、熵动态）。
- **客观与公平**：
  - 所有基线在同一硬件、相同种子、相同设置下重新训练（GRPO*标注为复现结果）。
  - 使用多次种子平均报告结果和标准差。
  - 超参数敏感性表明方法稳健。
  - 但未与最新的PRM类方法（如过程奖励模型）进行直接比较，但论文论证了PRM的局限（成本高、难泛化）。这可能是实验覆盖的一个缺口。

## 6. 主要结论与发现

1. **EMPG显著提升性能**：在WebShop、ALFWorld、Deep Search上，无论底层是GRPO还是DAPO，EMPG都带来持续且显著的性能提升（例如ALFWorld 1.5B模型GRPO+EMPG提升+8.1%，DAPO+EMPG提升+7.3%）。
2. **未来清晰度奖励促进域内利用，梯度缩放促进域外泛化**：消融表明——未来奖励在ID任务上提升+2.6，梯度缩放使OOD性能提升+3.9，二者结合协同最优。
3. **增强训练稳定性**：EMPG避免了基线（DAPO）后期KL Loss剧烈波动（图2），防止策略崩溃，保持低KL Loss。
4. **步骤级熵动态不同于token级**：图3显示即使低熵步骤也经历显著熵变化，验证了步骤级分析的必要性，与已有token级观察不同。
5. **跨架构通用**：在LLaMA3.1-8B上也取得一致提升，证明方法不限于Qwen系列。

## 7. 优点：方法与实验设计的亮点

- **理论扎实**：从策略梯度与熵耦合的定理（Proposition 1）出发，提出针对性解决方案，有严谨数学推导（附录C、D）。
- **方法新颖且实用**：利用内在不确定性（步骤级熵）作为学习信号，无需额外标注或价值模型，计算高效；批归一化设计使超参数对缩放因子 $k$ 不敏感（Table 5证实）。
- **双组件互补**：梯度缩放解决幅度问题，未来清晰度奖励解决方向问题，理论解释清晰（关联信息论、赋能理论）。
- **实验设计全面**：
  - 覆盖多个任务域（网页导航、文本交互、深度检索）。
  - 在多个模型规模（1.5B~32B）和架构（Qwen、LLaMA）上验证。
  - 包含消融、敏感性、泛化、稳定性分析，实验充分。
  - 开源复现努力：基于公开代码库统一实现。
- **可视化分析**：学习曲线、KL Loss图、熵变化图直观支撑结论。

## 8. 不足与局限

### 实验覆盖方面

- **未与PRM类方法直接对比**：虽然论文从理论上论证PRM的缺陷，但缺少与Process Reward Model（如Lightman et al., 2023）在相同设置下的实验比较。读者可能质疑EMPG是否优于更直接的步骤级监督。
- **任务类型有限**：仅覆盖了文本交互和搜索类任务，未涉及具身AI、多智能体协作等更复杂的长程任务。论文在展望中提到未来工作，但当前验证范围偏窄。
- **奖励信号单一**：仅使用二进制成功奖励，未测试连续奖励或混合奖励场景下的表现。

### 偏差风险

- **熵作为不确定性代理的局限**：步骤级平均token熵可能无法捕捉语义不确定性或认知不确定性。例如，模型可能对错误答案也很自信（幻觉），此时低熵反而有害。EMPG对自信错误动作放大惩罚，这部分缓解了问题，但仍有风险。
- **超参数依赖性**：虽然 $k$ 和 $k'$ 对 $k$ 不敏感，但未来清晰度权重 $\zeta$ 有正相关性（Table 5），需要调节。当前只在ALFWorld上做了敏感性，其他任务未系统分析。
- **计算资源限制**：部分实验（如1.5B vs 7B）用不同GPU数量，原始环境为H200但使用A100复现，可能影响绝对性能，但相对对比仍然公平。

### 应用限制

- **需要多步环境与轨迹采样**：EMPG依赖在线RL收集批次轨迹，对于无法在线交互或在采样成本极高的场景（如真实机器人）可能不适用。
- **仅适用于可获取token级概率的模型**：步级熵计算需要模型输出log-probability，闭源模型或API调用可能无法直接获取。
- **长序列效率**：步骤级熵需要对每步所有token逐一计算，在极长序列下可能增加计算开销。论文未提供运行时间对比。

---

（完）
