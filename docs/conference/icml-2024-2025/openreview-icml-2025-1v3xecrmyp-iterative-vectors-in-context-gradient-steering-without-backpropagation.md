---
title: "Iterative Vectors: In-Context Gradient Steering without Backpropagation"
title_zh: 迭代向量：无需反向传播的上下文梯度引导
authors: "Yiting Liu, Zhi-Hong Deng"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=1v3XEcRMyP"
tags: ["query:dg"]
score: 8.0
evidence: 利用迭代向量在推理时进行激活引导
tldr: 该论文提出迭代向量（Iterative Vectors）方法，在推理时通过模拟梯度更新来引导语言模型的激活空间，无需反向传播。该方法从上下文示例中提取并迭代优化激活元梯度，直接应用于模型激活，显著提升了多种任务上的上下文学习性能。这项工作展示了激活引导在推理阶段的潜力，为无需额外训练的动态模型控制提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-1v3xecrmyp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 702, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1v3xecrmyp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1333, \"height\": 544, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1v3xecrmyp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1573, \"height\": 748, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-1v3xecrmyp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1766, \"height\": 633, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1v3xecrmyp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1415, \"height\": 201, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1v3xecrmyp/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1591, \"height\": 203, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1v3xecrmyp/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 816, \"height\": 200, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1v3xecrmyp/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 963, \"height\": 757, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1v3xecrmyp/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1765, \"height\": 630, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1v3xecrmyp/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1765, \"height\": 630, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1v3xecrmyp/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1765, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1v3xecrmyp/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1774, \"height\": 452, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1v3xecrmyp/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1792, \"height\": 1985, \"label\": \"Table\"}]"
motivation: 现有上下文学习需要精心选择示例，且处理大量示例困难，亟需更高效的引导方法。
method: 从激活空间中提取元梯度，迭代更新引导向量，在推理时直接施加于模型激活。
result: 在四个流行模型和多种任务上，迭代向量显著提升了上下文学习性能。
conclusion: 激活引导可以在推理阶段有效改善语言模型行为，无需额外训练。
---

## Abstract
In-context learning has become a standard approach for utilizing language models.
However, selecting and processing suitable demonstration examples can be challenging and time-consuming, especially when dealing with large numbers of them.
We propose Iterative Vectors (IVs), a technique that explores activation space to enhance in-context performance by simulating gradient updates during inference.
IVs extract and iteratively refine activation-based meta-gradients, applying them during inference without requiring backpropagation at any stage.
We evaluate IVs across various tasks using four popular models and observe significant improvements.
Our findings suggest that in-context activation steering is a promising direction, opening new avenues for future research.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- 上下文学习（In-Context Learning, ICL）是当前利用语言模型的标准方法，但存在显著局限性：**对示例的选择、模板和排列高度敏感**，导致预测结果不稳定；**长上下文限制**使得处理大量示例时推理时间呈二次增长，且可能超出模型上下文窗口。
- 现有方法要么需要反向传播训练（如prompt tuning、LoRA），要么局限于合成任务（如Function Vectors、Task Vectors），缺乏在真实ICL场景下的系统性评估和有效增强。
- 论文旨在**探索语言模型的激活空间**，提出一种无需反向传播、无需参数更新、在推理时直接引导模型行为的轻量级方法——迭代向量（Iterative Vectors, IVs），以提升ICL的准确性、鲁棒性和效率。

---

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- 基于“语言模型是元优化器”的理论框架：注意力机制中，上下文示例充当元梯度（meta-gradients），零样本查询与完整ICL查询的激活差异即为这些元梯度。
- IVs通过**提取、迭代精炼、再应用**这一激活差异来模拟梯度下降过程，从而增强模型对任务的适应能力。

### 关键技术细节
1. **元梯度提取**：
   - 对每个n-way k-shot episode E，分别构造完整episode和零样本episode（仅含查询）。
   - 在每一注意力层l，收集输入-输出分隔符（分隔符token）处的激活，计算差值：ΔAct_l(x_i) = Act_l(x_i) - Act^0_l(x_q)。
   - 按类别平均，得到每类的向量 v^l_j 和查询向量 v^l_q，组成单episode的向量集 V^l_E。

2. **迭代精炼**：
   - 将训练集 T_train 划分为 m 个连续批次（batch size b）。
   - 第一批 V1 由episode向量平均得到；后续批次 Vi 在提取时，用之前所有批次向量累积平均（带提取强度 α1）编辑模型激活，再计算本批向量。
   - 最终IVs为所有批次向量的平均：V_l = (1/m) Σ_i V_i^l。

3. **应用（Editor）**：
   - 推理时，对每个输入-输出分隔符，按类别添加对应IVs（带推理强度 α2）到注意力层激活上：EditedAttn_l(x_i) = Attn_l(x_i) + α × v_{Class(x_i)}^l。

### 算法流程（文字说明）
- 提取阶段（Algorithm 1）：随机采样k-shot episode → 分别获取完整和零样本序列 → 提取激活差 → 按类平均 → 每b个episode更新累积向量 → 返回最终平均向量。
- 评估阶段（Algorithm 2）：对每个测试episode，应用IVs编辑模型激活 → 取logits最大类别作为预测。

---

## 3. 实验设计：数据集、场景、基准与对比方法

### 数据集和场景
- 共13个文本分类任务，涵盖新闻分类（AG News）、情感分析（SST5、Rotten Tomatoes、Sentiment）、立场检测（Abortion、Atheism、Climate、Feminist、Hillary）、仇恨检测（Hate）、讽刺检测（Irony）、攻击性语言（Offensive）、情感识别（Emotion）、问题分类（TREC）。
- 采用**n-way k-shot episode采样**，主实验中统一使用**1-shot**（每个类别一个示例），测试集10,000个episode。

### 基准（Baselines）
- **Clean**：标准1-shot ICL（无任何激活编辑）。
- **Function Vectors (FV)**：选取因果影响力最高的注意力头，平均其输出作为任务向量。
- **Task Vectors (TV)**：找到最优单一层，提取并应用该层最终token的激活。

### 对比方法
- 对FV和TV进行适配：允许使用训练集平均提取，并搜索其超参数（提取shot k、应用层、top头数等）。
- IVs的超参数：k（1-4）、b（10默认）、α1和α2（0.1-0.9搜索）。

### 评估指标
- 主指标：macro-F1。
- 附加指标：micro-F1、weighted-F1。

---

## 4. 资源与算力

- **默认条件**：所有主实验可在**单张Nvidia RTX A6000 GPU**运行。
- **Llama-2-70b实验**：使用了**3张Nvidia RTX A6000 GPU**。
- **具体时间示例**：emoji数据集（20类分类）上，IVs的提取+推理总时长约23.75分钟，FV提取需438.3分钟（慢约20倍）；推理时1-shot+IV耗时1452秒，而2-shot标准ICL需2434秒（快41%）。
- **论文未系统给出全部实验的训练/推理总时长**，但通过上述示例说明了效率优势。

---

## 5. 实验数量与充分性

### 实验组数
1. **主实验**：4个模型（GPT-J-6B, Llama-2-7b, Llama-3.1-8b, Llama-2-13b） × 13个数据集 × 4种方法（Clean, FV, TV, IV） = 208组 macro-F1结果。另有micro-F1和weighted-F1结果（同样规模）。
2. **推理时间对比**（emoji数据集，1个模型Llama-2-7b，对比不同shot和激活向量方法）。
3. **多shot扩展实验**：2个数据集（AG News、Rotten Tomatoes） × 4种shot（2-5） × 2种方法（Clean, IV） × 2个模型（Llama-2-7b, Llama-2-70b） = 32组实验结果。
4. **提取episode数量影响**：1个数据集（AG News） × 1个模型（Llama-2-7b） × 10种episode数量，共10组。
5. **消融研究**：1个数据集（AG News validation） × 1个模型（Llama-2-7b） × 7种batch size（0,1,3,5,10,20,50,100） × 5×5的α1/α2网格，呈现热力图。

### 充分性与公平性
- **充分性**：覆盖多种模型规模、多个任务领域、多种指标；关键组件（迭代、批大小、强度）均经消融验证；对更高shot和更大模型进行了额外验证。
- **客观性**：使用固定随机种子（42），测试集规模大（10,000 episode），结果取平均；对基线方法同样进行超参数搜索（如FV的top头数、TV的应用层）。
- **公平性**：FV和TV因设计限制，在部分任务上出现退化（37%情况），IVs则未出现退化，但论文明确报告了基线的不足，对比是透明的。IVs的额外计算时间（提取）被明确报告，并与基线的推理时间做对比。

---

## 6. 主要结论与发现

1. **性能提升**：IVs在13个任务上的macro-F1平均提升**3.2%**，在大多数单项任务上均优于标准ICL及FV、TV基线。
2. **效率优势**：IVs显著降低推理时间（如emoji任务上比2-shot ICL快41%），且提取时间远少于FV（降低95%）。
3. **可扩展性**：IVs能随提取episode数量增加而持续提升性能（20个以上episode后效果稳定），突破了ICL上下文长度限制。
4. **迭代精炼的关键性**：消融实验表明，无迭代（batch size=0）性能大幅下降；合适的批大小（如b=10）可平衡稳定性和精炼机会。
5. **理论可解释性**：IVs的提取和应用过程与梯度下降优化类比，超参数（α1、α2）起到学习率作用，表现出类似训练中的交互动态。

---

## 7. 优点

- **无需反向传播**：完全在推理时完成向量提取和应用，无需模型参数更新或额外训练。
- **理论支撑**：基于注意力双形式理论和元优化解释，方法具有严谨的数学推导，非纯启发式。
- **系统化评估框架**：首次为激活向量方法在真实ICL任务上建立标准化评估流程（包含提取器、编辑器、超参数搜索、多指标评价）。
- **计算高效**：提取和推理时间均可控，向量可复用，适合实际部署。
- **鲁棒性强**：相比FV和TV在部分任务上出现退化，IVs在所有评估场景中均未出现显著负收益。
- **可扩展性好**：能有效利用大量训练示例，且随模型规模增大（如Llama-2-70b）提升效果更明显。

---

## 8. 不足与局限

1. **任务局限**：论文仅评估了**文本分类**任务。IVs是否适用于生成任务（如翻译、摘要）或更复杂的推理任务尚未验证。
2. **零样本场景效果有限**：论文明确指出IVs在零样本设置下提升有限（附录H），当前仅聚焦于增强小样本ICL，未能突破零样本性能瓶颈。
3. **超参数搜索成本**：IVs有4个超参数（k、b、α1、α2），论文采用网格搜索（k在1-4，α1/α2在0.1-0.9，b固定10），但仍需一定验证集计算量。论文未给出更高效的调参策略。
4. **FV/TV基线适配的公平性争议**：FV和TV原本设计用于0-shot合成任务，论文将其适配到ICL场景（允许使用训练集平均），但适配方式可能未完全发挥其潜力。且FV因提取耗时过长，实验中被迫限制k=1，可能低于其真实上限。
5. **激活编辑的通用性**：IVs的编辑操作（直接加和到注意力层输出）可能未充分考虑不同层之间的相互作用，论文未分析不同层向量融合的影响。
6. **理论假设的松弛**：元梯度等价性的推导基于线性注意力和无归一化假设，实际Transformer使用softmax attention和LayerNorm，理论近似存在偏差，论文未深入讨论此偏差对性能的影响。
7. **对数据分布的敏感性**：实验基于均匀采样的few-shot episode，对于极不平衡或噪声较多的训练数据，IVs的稳定性尚未研究。

---

（完）
