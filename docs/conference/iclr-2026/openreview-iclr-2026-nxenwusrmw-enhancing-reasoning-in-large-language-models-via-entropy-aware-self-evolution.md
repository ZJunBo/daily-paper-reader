---
title: Enhancing Reasoning in Large Language Models via Entropy-Aware Self-Evolution
title_zh: 通过熵感知自进化增强大语言模型推理能力
authors: "Lai Chen, Yao Zhu, Xin Ye, Peng Lin, Xiangyang Ji, Xiang Tian"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=nXENWUSRMw"
tags: ["query:luq"]
score: 5.0
evidence: 熵感知的自进化推理框架
tldr: 针对自进化框架中正确性与探索性的平衡难题，论文提出熵感知自进化框架，通过序列级和token级熵整合验证器反馈。高熵选择提供信息丰富且可靠的轨迹，熵感知重思访问不确定步骤以发现替代方案。该方法增强了LLM推理能力。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-nxenwusrmw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1375, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-nxenwusrmw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 738, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-nxenwusrmw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1376, \"height\": 782, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-nxenwusrmw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1367, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-nxenwusrmw/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1379, \"height\": 621, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-nxenwusrmw/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1377, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-nxenwusrmw/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 653, \"height\": 427, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-nxenwusrmw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1453, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-nxenwusrmw/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 861, \"height\": 288, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-nxenwusrmw/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 653, \"height\": 273, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-nxenwusrmw/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1454, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-nxenwusrmw/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1143, \"height\": 598, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-nxenwusrmw/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 762, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-nxenwusrmw/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1537, \"height\": 2017, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-nxenwusrmw/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1559, \"height\": 1768, \"label\": \"Table\"}]"
motivation: 自进化时需平衡正确性与探索性，熵可作为不确定性信号指导选择。
method: 提出熵感知自进化框架，包括高熵选择验证轨迹和熵感知重思不确定步骤。
result: 框架有效提升LLM复杂推理能力，在多个基准上取得改进。
conclusion: 熵信号有助于在自进化中平衡探索与利用，提升推理性能。
---

## Abstract
Large language models (LLMs) have exhibited remarkable reasoning capabilities. However, when self-evolution frameworks are employed to further enhance these models, a key challenge lies in balancing correctness, which ensures reliable supervision, and exploration, which promotes diverse reasoning trajectories. To address this dilemma, we propose an $\textbf{entropy-aware self-evolution framework}$ that integrates verifier feedback with both sequence-level and token-level entropy.  Our approach incorporates two key strategies: (i) $\textbf{high-entropy selection}$ of verified trajectories to provide informative yet reliable signals; and (ii) $\textbf{entropy-aware rethinking}$, which revisits uncertain reasoning steps to uncover alternative solutions. Theoretically, we establish the connection between entropy and the expected supervised fine-tuning loss, showing that high-entropy trajectories yield stronger learning signals. Empirically, experiments across multiple reasoning benchmarks demonstrate that our framework consistently improves both reliability and exploratory capacity over strong baselines. With the assistance of the proposed framework, InternLM2.5-1.8B achieves an improvement of $8.27$% and surpasses the strong baseline by $1.82$% on the GSM8K task, as measured by $Pass@16$.
Our results highlight entropy as a principled driver of self-improvement, enabling LLMs to evolve toward models that are not only more accurate but also more exploratory.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文内容生成的结构化总结。

---

## 论文总结：通过熵感知自进化增强大语言模型推理能力

### 1. 核心问题与整体含义（研究动机和背景）
大型语言模型（LLMs）在推理任务上表现卓越。为了进一步提升其能力，研究者引入了“自进化”（Self-Evolution）框架，通过让模型自行生成新训练轨迹并迭代微调来实现自我提升。然而，自进化面临一个根本性矛盾：
- **正确性（Correctness）**：需要确保生成的轨迹是可靠的，通常依赖验证器过滤，但这容易偏向低困惑度、确定性的路径，导致探索不足。
- **探索性（Exploration）**：需要鼓励生成多样化、新颖的推理路径，但缺乏正确性保证会导致训练信号噪声大。

现有方法往往偏重其中一方。本文提出**熵感知自进化框架**，利用熵（Entropy）作为不确定性信号，在保证正确性的前提下，主动选择高熵（信息丰富）的轨迹进行训练，并通过“重思”机制从不确定的推理步骤处重新生成，从而系统性地平衡了正确性与探索性。

### 2. 方法论
论文提出一个三阶段迭代框架，结合**序列级熵**和**token级熵**以及**外部验证器**。

**核心思想：** 高熵但正确的轨迹同时具备可靠性和信息量，提供更强的学习信号。

**关键技术细节：**

- **熵的定义：**
  - **Token级熵**：$H_t = -\sum_{i=1}^{V} p_\theta(v_i|y_{<t}, x) \log p_\theta(v_i|y_{<t}, x)$，反映当前位置的不确定性。
  - **序列级熵**：$H_{\text{seq}}(y|x) = \frac{1}{T} \sum_{t=1}^{T} H_t$，反映整个轨迹的全局不确定性。

- **三阶段流程（每轮迭代）：**
  1. **轨迹探索（Trajectory Exploration）：** 当前模型为每个输入生成K条轨迹，计算其序列熵，并用外部验证器（Python执行器）判断正误，将所有正确轨迹存入探索池。
  2. **轨迹重思（Trajectory Rethinking）：** 从探索池中选择序列熵最高的正确轨迹，根据token级熵识别高熵位置作为截断点（由超参数α和β控制），从截断点处重新生成K条续写，得到重思轨迹，再次验证后存入重思池。若无反例，则对负样本中熵最高的轨迹进行操作。
  3. **轨迹选择（Trajectory Selection）：** 分别从探索池和重思池中按序列熵降序选择Top-N轨迹，合并后进行监督微调（SFT）。

- **理论分析：** 推导出期望交叉熵损失与序列熵的关系：$\mathbb{E}_{y\sim\pi_\theta}[ \mathcal{L}_{\text{CE}}(y|x)] = T \cdot \mathbb{E}_{y\sim\pi_\theta}[H_{\text{seq}}(y|x)]$，证明高熵轨迹产生更大期望损失，从而提供更强梯度信号。

### 3. 实验设计

- **数据集与基准：**
  - **训练集：** 使用GSM8K的训练集和MATH的随机子集，共13,492个样本。
  - **测试集：** GSM8K（Held-in）、GSM-Hard、SVAMP、AsDiv（均Held-out）。
  - **格式：** 要求模型生成可执行的Python代码作为推理路径，使用Python执行器作为验证器。

- **对比方法：** 主要与**ENVISIONS**框架对比（两者都使用验证器+自训练，但ENVISIONS采用自我修正和低置信度选择）。同时报告基础模型的few-shot结果。

- **评估指标：** **Pass@K**（K=16,128,256等），衡量多次采样下的正确率，既反映准确率也反映探索能力。

- **模型骨干：** InternLM2.5-1.8B、Llama3.2-1B、Qwen2.5-Instruct-1.5B。

- **消融与分析实验：**
  - 组件消融：全方法 vs. 仅选择 vs. 仅重思 vs. ENVISIONS。
  - 选择策略对比：高熵 vs. 低熵 vs. 随机。
  - 轨迹多样性分析：计算相似度分数和负对数概率。
  - 重思贡献分析：迭代性能、生成轨迹数量、高熵token模式。
  - 超参数分析：采样温度、低预算Pass@K、截断参数α和β。

### 4. 资源与算力
- **硬件：** 4×RTX3090（24GB VRAM）。
- **软件框架：** DeepSpeed ZeRO3 + FlashAttention2。
- **优化器：** AdamW，学习率2e-5，epoch=1。
- **训练时长与FLOPs：** 以InternLM2.5-1.8B为例（I=10, K=5）：
  - 本文方法：总壁钟时间约139.3小时，总FLOPs约1.78×10¹⁸。
  - ENVISIONS基线：总壁钟时间约152.0小时，总FLOPs约2.06×10¹⁸。
  - 本文在计算效率上略有优势，主要由重思阶段比ENVISIONS的修正阶段更高效所致。

### 5. 实验数量与充分性
实验较为充分且设计客观：
- 在**4个数据集**（含held-out）上进行评估，覆盖不同难度和分布。
- 在**3个不同骨干模型**（1B~1.8B）上验证，证明方法通用性。
- 进行了**消融实验**（组件、选择策略）、**轨迹多样性分析**、**重思机制分析**、**超参数敏感性分析**。
- 所有实验控制相同采样策略（top-p=0.95, temperature=0.6），对比基线ENVISIONS在相同条件下复现。
- 通过Pass@K从低到高（1到256）的评估，显示优势在各个K值下均存在，而非仅在大K下出现。

### 6. 主要结论与发现
- 论文提出的**熵感知自进化框架**显著提升了LLM的推理能力，在保持正确性的同时增强了探索性。
- **关键发现：**
  - 高熵轨迹提供更强的训练信号（理论+实验验证）。
  - 轨迹重思机制通过在高熵决策点截断并重新生成，有效增加了轨迹多样性。
  - 在GSM8K上，InternLM2.5-1.8B在Pass@16上提升8.27%，超越ENVISIONS基线1.82%；在Pass@128上超越4.39%。
  - 在held-out任务（GSM-Hard, SVAMP, AsDiv）上也取得一致优势。
  - 性能增益在更大采样预算下更明显，证实了探索能力的提升。
  - 计算效率优于基线（更少FLOPs和更短时间）。

### 7. 优点
- **问题定位准确：** 明确指出自进化中正确性与探索性的矛盾，切中当前研究痛点。
- **方法新颖且优雅：** 利用熵信号（同时考虑序列和token级）作为信息量与不确定性的代理，结合验证器，简单而有效。
- **理论支撑：** 证明了熵与期望SFT损失的直接关系，为方法提供了理论依据。
- **实验丰富透彻：** 覆盖多模型、多数据集、多维度消融和深度分析（相似度、负对数概率、重思贡献等），实验设计严谨。
- **计算效率提升：** 相比基线ENVISIONS，总FLOPs和壁钟时间均降低，成本控制好。
- **可解释性：** 通过可视化高熵token（如“because”“since”“then”），说明重思机制作用在关键的推理分叉点，增强了方法的可解释性。

### 8. 不足与局限
- **模型规模限制：** 实验仅覆盖1.8B及以下参数规模的模型，未验证在7B+等更大模型上的有效性。由于计算资源有限，这一推广性未知。
- **领域局限：** 框架依赖**可执行验证器**（Python执行器），目前仅适用于数学和代码类任务，难以扩展到**语义推理**（如常识推理、自然语言问答）等需人工评估的领域。
- **不确定性代理的近似：** 使用熵作为不确定性代理，未严格区分认知不确定性与偶然不确定性。虽然通过验证器筛选部分缓解了噪声问题，但在更复杂任务中可能不够精确。
- **超参数敏感：** 方法涉及多个超参数（α, β, K, N, I），尽管论文给出了推荐范围，但对不同任务和模型可能需要额外调优。
- **未与最先进的RLVR方法（如GRPO、DAPO等）直接对比：** 虽然提及RLVR相关方法，但实验仅与ENVISIONS比较，缺乏与更前沿强化学习框架的定量对比。

（完）
