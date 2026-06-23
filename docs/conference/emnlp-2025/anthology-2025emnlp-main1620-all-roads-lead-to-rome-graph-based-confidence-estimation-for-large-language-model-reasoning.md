---
title: "All Roads Lead to Rome: Graph-Based Confidence Estimation for Large Language Model Reasoning"
title_zh: 条条大路通罗马：基于图的LLM推理置信度估计
authors: "Caiqi Zhang, Chang Shu, Ehsan Shareghi, Nigel Collier"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.emnlp-main.1620.pdf"
tags: ["query:uq-safety"]
score: 8.0
evidence: 基于图的置信度估计用于LLM推理任务
tldr: 现有置信度估计方法主要针对事实问答，难以泛化到推理任务。本文提出无训练的图基置信度估计方法，将推理路径建模为有向图，利用图中心性、路径收敛性和加权等属性估计置信度。在三个推理数据集上使用两个LLM的实验表明，该方法有效改善了置信度估计并提升了下游任务性能。
source: EMNLP-2025-Main
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1620/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1388, \"height\": 553, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1620/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 753, \"height\": 899, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1620/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1436, \"height\": 985, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1620/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 832, \"height\": 212, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1620/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 835, \"height\": 212, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1620/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 603, \"height\": 251, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1620/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 813, \"height\": 818, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1620/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 639, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1620/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 627, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1620/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 624, \"height\": 250, \"label\": \"Table\"}]"
motivation: 弥补推理任务上置信度估计方法的缺失。
method: 将推理路径转化为有向图，通过图属性计算置信度。
result: 在多个推理数据集上置信度估计更准确，下游任务表现提升。
conclusion: 为LLM推理提供了有效的无训练置信度估计框架。
---

## Abstract
Confidence estimation is essential for the reliable deployment of large language models (LLMs). Existing methods are primarily designed for factual QA tasks and often fail to generalize to reasoning tasks. To address this gap, we propose a set of training-free, graph-based confidence estimation methods tailored to reasoning tasks. Our approach models reasoning paths as directed graphs and estimates confidence by exploiting graph properties such as centrality, path convergence, and path weighting. Experiments with two LLMs on three reasoning datasets demonstrate improved confidence estimation and enhanced performance on two downstream tasks.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **动机**：大型语言模型（LLM）的置信度估计对于可靠部署至关重要，尤其在推理任务中。现有方法大多针对事实问答（factual QA）任务设计，例如基于模型自报告或语义一致性，但推理任务的输出包含较长的中间步骤且逻辑相互关联，这些方法难以泛化。
- **背景**：推理任务中，多个推理路径可以导向相同或不同的最终答案，这种结构天然适合用图来建模。论文受“条条大路通罗马”启发，认为被多条多样化路径支持的答案更可能正确。
- **目标**：提出一套无需训练、基于图的置信度估计方法，专门用于推理任务，并验证其在两个下游任务（选择性自反思、LLM级联）中的有效性。

## 2. 方法论

### 核心思想
- 将每个问题的多个独立采样推理路径构造成一个有向图（Directed Graph），其中节点代表推理步骤或答案，边表示逻辑流向或语义等价关系。
- 通过图论属性（中心性、路径收敛性、路径加权）计算每个候选答案的置信度。

### 关键技术细节
- **推理链采样**：对每个问题Q，生成N条推理链C = {C1,...,CN}，每条链分解为步骤序列。最终答案集合A'为去重后的答案节点。
- **图构建**：
  - 从问题节点Q开始，逐条添加链的节点和**内部边（intra-edge）**（同链内步骤间单向连接）。
  - 使用辅助模型判断不同链中语义等价的步骤，添加**交叉边（inter-edge）**（双向连接）。
  - 合并等价节点，最终图包含问题节点、中间步骤节点、答案节点。
- **置信度计算方法**（三种，独立研究）：
  - **基于中心性（CenConf）**：采用Katz中心性，考虑节点通过短路径与邻居的连接强度，归一化得分。
  - **路径收敛（PathConv）**：统计从Q到每个答案节点的不同路径数量，归一化作为置信度。当图巨大时采用路径采样近似（附录算法2）。
  - **路径加权（PathWeight）**：合并等价节点后赋予权重（合并的原始步骤数），路径得分为节点权重乘积，累计各答案路径得分并归一化。强调共享步骤，抑制孤立步骤。

### 算法流程（文字说明）
1. 对问题Q，通过LLM采样N条推理链。
2. 根据链构建图：添加节点、内部边、交叉边（通过等价判断）。
3. 对每个答案节点，分别计算中心性得分、路径计数或加权路径得分。
4. 归一化得到置信度分数。

## 3. 实验设计

### 数据集与场景
- **MATH500**（数学推理）、**MMLU-Pro STEM**（科学推理）、**FOLIO**（一阶逻辑推理）。特意选择模型预测正确与错误分布均衡的任务，以更好体现置信度估计价值。
- 两个LLM：**Llama3.1-8B-Instruct** 和 **Gemma2-9B-Instruct**。

### Benchmark与对比方法
- **基线方法**：
  - 模型自报告：p(true)、Self-Verb（自述置信度）。
  - 一致性方法：Self-Cons（自一致性）、Degree Matrix（Deg）、Eccentricity（Ecc）。
  - 长文本方法：LUQ。
  - 排除需要训练的PRM（过程奖励模型）。
- **指标**：AUROC（主要）、Brier Score（BS）、Expected Calibration Error（ECE）。

### 实验设置
- 图构建使用NetworkX。
- 采样N=10条链，推理温度1.0，3-shot提示。
- 等价判断使用Llama-3-8B-Instruct（温度0）。
- 超参数：CenConf衰减因子α=0.1，PathConv最大路径长度L=12。

## 4. 资源与算力

- **未明确说明**：论文未提及GPU型号、数量、训练时长等具体算力信息。仅提到使用vLLM进行推理，图构建使用NetworkX库。所有方法均为无训练推理，主要开销来自多次采样和图构建，但未量化。

## 5. 实验数量与充分性

- **主要实验**：一张主表（表1），在两个LLM、三个数据集上比较8种方法（3种图方法 + 5种基线），共(2模型×3数据集×8方法)=48个实验点。
- **消融实验**（附录D）：对超参数（α、采样数N、路径长度L）进行敏感性分析，共3组实验。
- **下游应用实验**：选择性自反思（表2）和LLM级联（表3），分别在三个数据集、三种触发比例（5%、10%、15%）及100%对比，共(2个任务×3数据集×4比例)=24个实验点。
- **充分性评价**：
  - **充分**：覆盖多个推理领域，对比方法全面（包含主流基线），指标多维度（AUROC、BS、ECE）。
  - **客观公平**：保证相同采样数（如一致性方法也用10条链），排除需要训练的方法，结果报告平均值。
  - 但仅使用7B-9B规模模型，未在更大模型（如70B）上验证方法本身；下游应用只使用Llama-8B作为基座，泛化性有限。

## 6. 主要结论与发现

- 提出的三种图基方法在所有数据集和模型上**一致优于非图基线**。其中**PathWeight**综合性能最好（Llama-8B在MATH500上AUROC达84.0%，ECE仅10.4%）。
- 即便是最简单的CenConf（Katz中心性）也超过所有基线，证明利用图结构信息的有效性。
- 在下游应用中，仅对置信度最低的15%样本进行干预（自反思或级联），可获得显著准确率提升（+2~+5个点），且优于对所有样本干预（过度自反思反而降低性能）。
- 方法无需训练、模型无关，适用于黑盒API。

## 7. 优点

- **新颖性**：首次将推理路径的图结构（内部边+交叉边）用于置信度估计，揭示结构信号的价值。
- **无需训练**：完全基于推理时采样和图计算，不依赖额外训练数据或奖励模型。
- **模型无关**：仅需文本输入，适用于任何LLM（包括API封闭模型）。
- **实用性强**：可直接提升下游应用（选择性自反思、级联）的效率，减少不必要的计算开销。
- **分析深入**：提供多种图属性视角，并通过消融实验验证各组件作用。

## 8. 不足与局限

- **计算/延迟开销**：需要多次采样和图构建，相比单次推理成本高。论文承认可通过早停策略缓解，但未系统评估。
- **黑盒限制**：未利用token级概率信息。论文建议未来可集成logit信号，但同时会失去黑盒通用性。
- **单属性估计**：三种方法独立使用，未集成互补信号。集成可能会更稳健，但本文未探索。
- **图构建敏感性**：对步骤分解质量和等价判断可靠性敏感。不准确的等价连接可能导致图出现循环或误导，影响置信度（<5%的循环情况通过删除边处理）。
- **实验规模有限**：仅测试7B-9B模型，未在更大参数规模（如70B）或更复杂推理任务（如数学竞赛题、多步常识推理）上验证。下游应用仅用于Llama-8B，未在其他模型上重复。
- **数据集选择偏倚**：特意选择正确/错误均衡的数据集，可能高估了在更不平衡分布下的效果。

（完）
