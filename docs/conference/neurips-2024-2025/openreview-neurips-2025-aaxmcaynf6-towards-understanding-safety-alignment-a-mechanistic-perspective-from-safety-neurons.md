---
title: "Towards Understanding Safety Alignment: A Mechanistic Perspective from Safety Neurons"
title_zh: 理解安全对齐：来自安全神经元的机制视角
authors: "Jianhui Chen, Xiaozhi Wang, Zijun Yao, Yushi Bai, Lei Hou, Juanzi Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=AAXMcAyNF6"
tags: ["query:dg"]
score: 7.0
evidence: 使用推理时激活对比和修补研究安全神经元
tldr: "大语言模型即使经过安全对齐仍存在风险。本文从机械可解释性角度定位模型中的安全神经元（约占5%），通过推理时激活对比识别，并采用动态激活修补评估因果作用。实验表明，仅修补这些神经元的激活即可恢复超过90%的安全性能，跨多个流行LLM验证。该工作为理解安全对齐机制提供了新方法。"
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-aaxmcaynf6/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1435, \"height\": 591, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aaxmcaynf6/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1342, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aaxmcaynf6/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1440, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aaxmcaynf6/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1388, \"height\": 392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aaxmcaynf6/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1436, \"height\": 517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aaxmcaynf6/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1376, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aaxmcaynf6/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1456, \"height\": 1440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aaxmcaynf6/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1439, \"height\": 1512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aaxmcaynf6/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1440, \"height\": 1515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aaxmcaynf6/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1433, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aaxmcaynf6/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1451, \"height\": 627, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-aaxmcaynf6/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1430, \"height\": 695, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aaxmcaynf6/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 711, \"height\": 268, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aaxmcaynf6/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 662, \"height\": 661, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aaxmcaynf6/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 708, \"height\": 748, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aaxmcaynf6/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 559, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aaxmcaynf6/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1452, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aaxmcaynf6/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1449, \"height\": 1665, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aaxmcaynf6/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1420, \"height\": 1525, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aaxmcaynf6/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 813, \"height\": 506, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aaxmcaynf6/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 777, \"height\": 213, \"label\": \"Table\"}]"
motivation: 大语言模型安全对齐的底层机制不明，需要定位负责安全行为的关键神经元。
method: 提出推理时激活对比定位安全神经元，并使用动态激活修补验证其因果作用。
result: "在多个LLM上一致识别约5%的安全神经元，修补其激活可恢复90%以上安全性能。"
conclusion: 安全神经元是模型安全行为的关键，激活修补可有效控制安全表现。
---

## Abstract
Large language models (LLMs) excel in various capabilities but pose safety risks such as generating harmful content and misinformation, even after safety alignment. In this paper, we explore the inner mechanisms of safety alignment through the lens of mechanistic interpretability, focusing on identifying and analyzing safety neurons within LLMs that are responsible for safety behaviors. We propose inference-time activation contrasting to locate these neurons and dynamic activation patching to evaluate their causal effects on model safety. Experiments on multiple prevalent LLMs demonstrate that we can consistently identify about 5% safety neurons, and by only patching their activations we can restore over 90% of the safety performance across various red-teaming benchmarks without influencing general ability. The finding of safety neurons also helps explain the ''alignment tax'' phenomenon by revealing that the key neurons for model safety and helpfulness significantly overlap, yet they require different activation patterns for the same neurons. Furthermore, we demonstrate an application of our findings in safeguarding LLMs by detecting unsafe outputs before generation.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLMs）即使经过安全对齐（如RLHF、DPO）后，仍然容易生成有害内容或受到恶意攻击。现有对齐方法的内部机制尚不透明，难以从根本上设计更鲁棒的对齐算法。
- **研究动机**：从机械可解释性的角度揭示安全对齐的内部工作原理，即找出模型中负责安全行为的“安全神经元”，并验证其因果效应，从而为理解对齐机制和缓解“对齐税”提供新视角。
- **整体含义**：通过定位约5%的神经元（安全神经元）并仅修补其激活值，即可恢复超过90%的安全性能，且不会显著影响通用能力。这证明了安全对齐具有稀疏化的神经基础，并为模型安全性的可解释控制提供了新路径。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：将安全行为归因于特定的神经元组件。假设关联是因果的必要条件，因此分两步：首先通过激活对比缩小搜索空间，再通过动态激活修补验证因果效应。
- **关键技术细节**：
  1. **推理时激活对比（Inference-time Activation Contrasting）**：对于一对模型 \( M_1 \)（未对齐，如SFT）和 \( M_2 \)（已对齐，如DPO），在同一提示生成上计算每个MLP神经元的激活差异，并用均方根作为“变化分数”。
     - 公式：\( S_i^{(l)}(M_1, M_2; D) = \sqrt{ \frac{ \sum_{w\in D} \sum_{j=|w|}^{|\bar{w}_1|-1} \left( a_i^{(l)}(M_1; \bar{w}_1)[j] - a_i^{(l)}(M_2; \bar{w}_1)[j] \right)^2 }{ \sum_{w\in D} |w_1| } } \)
     - 按变化分数降序排序，选取top神经元作为候选安全神经元。
  2. **动态激活修补（Dynamic Activation Patching）**：在生成过程中，每一步先缓存 \( M_2 \) 的候选神经元激活，然后用这些激活替换 \( M_1 \) 中对应神经元的激活，其余部分保持不变，逐步生成完整回复。
     - 定义因果效应 \( C = \frac{ \mathbb{E}_{w\in D} [F(\tilde{w}_1) - F(\bar{w}_1)] }{ \mathbb{E}_{w\in D} [F(\bar{w}_2) - F(\bar{w}_1)] } \)，其中 \( F \) 为安全评价指标（如成本模型得分）。
     - 当 \( C \) 接近1时修补神经元能完全解释 \( M_2 \) 的安全能力。
- **算法流程**（文字说明）：
  - 输入：提示文本、神经元集合、目标模型 \( M_1 \)、源模型 \( M_2 \)。
  - 循环直到生成结束：
    1. 在 \( M_2 \) 上运行当前提示，缓存目标神经元激活；
    2. 在 \( M_1 \) 上运行，将目标神经元激活替换为缓存值，其余保持不变；
    3. 采样下一个token并拼接至提示。
  - 输出完整回复。

### 3. 实验设计：数据集、基准、对比方法

- **模型**：Llama2-7B、Mistral-7B、Gemma-7B、Qwen2.5-3B，均进行SFT（ShareGPT）和DPO安全对齐（HH-RLHF-Harmless），使用(IA)³参数高效微调。
- **数据集与基准**：
  - **红队基准**：Beavertails、RedTeam、HarmBench、JailBreakLLMs。
  - **通用能力基准**：Wikitext-2 (PPL)、MMLU、GSM8K、BBH、TruthfulQA。
  - **安全评价指标**：主要使用成本模型（beaver-7b-v1.0-cost）给出的成本得分（越低越安全），同时用GPT-4评分验证相关性。
- **对比方法**：
  - 随机神经元（控制实验，每层相同数量）。
  - 基于剪枝的方法（Pruning, Wei et al. 2024）：使用Wanda分数定位参数重要性。
  - SN-Tune (Zhao et al. 2025)：基于神经元对残差流贡献的消融方法。
- **评价方式**：动态激活修补后计算因果效应 \( C \)，以及各基准上的绝对得分变化。

### 4. 资源与算力

- 论文明确提到：所有实验在NVIDIA A100-SXM4-80GB GPU上运行，总计约**1,000 GPU小时**。
- 训练细节：SFT使用3个epoch，DPO使用相同超参数（学习率1e-3、优化器AdamW、批次大小120等）。
- 评估时使用贪婪搜索，最大新token数128或256。

### 5. 实验数量与充分性

- **实验组数**：
  - 主实验（因果效应曲线）：对4个模型分别做Base→DPO和SFT→DPO修补，每种5个随机种子，共4×2×5=40条曲线。
  - 转移性实验：4个模型×2种来源（Base/SFT）×4个红队基准×3种方法（Ours/Pruning/SN-Tune）+通用能力评估，表1展示了大量结果。
  - 对齐税分析：7种偏好数据集的相关性分析、跨修补实验（Helpfulness↔Safety）。
  - 守护应用：5折交叉验证分类器（源自5个数据集），并测试SFT和DPO加入守护后的安全得分。
- **充分性评价**：实验覆盖多种模型家族、多种红队基准、多种对齐任务；消融实验（随机神经元、不同变化分数阈值、不同M1/M2选择）验证了方法的鲁棒性；统计显著性检验（t-test p值<1e-6）增强了结论可信度。实验设计较为充分、客观、公平。

### 6. 论文的主要结论与发现

1. **安全神经元稀疏且因果有效**：约5%的神经元可以恢复90%以上的安全性能，远优于随机神经元的零效果。
2. **安全神经元具有可转移性**：在HH-Harmless上识别的安全神经元能有效防御其他红队基准的恶意攻击，且通用能力几乎不受影响。
3. **安全神经元对训练随机性鲁棒**：不同随机种子训练的模型所识别的安全神经元重叠度和秩相关均>0.95。
4. **解释对齐税**：安全与有用性相关的神经元高度重叠，但需要不同的激活模式。共享神经元的激活竞争导致了安全和有用性之间的权衡。
5. **应用——安全守护**：利用安全神经元的激活（在提示最后一个token处）可训练分类器，在生成前预测输出是否有害，有效提升未对齐模型的安全性并进一步强化已对齐模型。

### 7. 优点：方法或实验设计上的亮点

- **方法论创新**：提出推理时激活对比 + 动态激活修补的两阶段框架，克服了现有机械可解释性方法难以处理开放生成和大量参数的问题。
- **因果验证严密**：通过动态修补（增强而非消融）避免了“九头蛇效应”，并且用因果效应公式量化贡献。
- **跨模型验证**：在四个不同架构（Llama2、Mistral、Gemma、Qwen2.5）上一致验证，增强结论泛化性。
- **实用性体现**：不仅揭示机制，还构建了实用的安全守护器，证明理论发现的直接应用价值。
- **对齐税解释**：首次从神经元重叠与激活竞争角度解释了“对齐税”现象。

### 8. 不足与局限

- **依赖已对齐模型激活**：修补需要从已对齐模型获取激活值，无法完全无训练地应用。
- **训练方式限制**：使用(IA)³参数高效微调，未验证全参数微调下的安全神经元特性。
- **机制理解有限**：仅定位了哪些神经元影响安全，但未深入解释这些神经元如何具体实现安全行为（例如如何拒绝有害请求）。
- **数据集偏差**：主要依赖HH-RLHF-Harmless进行安全对齐和变化分数计算，可能带来领域偏见，影响对复杂恶意攻击的泛化。
- **计算开销**：动态激活修补涉及多次前向传播，在长序列生成中可能效率不高（但探测阶段可离线进行）。
- **应用范围**：安全守护分类器仅基于SFT激活，且使用简单逻辑回归，可能无法应对动态演化攻击。

（完）
