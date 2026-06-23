---
title: "Rethinking Uncertainty Estimation in LLMs: A Principled Single-Sequence Measure"
title_zh: 重新思考LLM不确定性估计：一种基于原理的单序列度量
authors: "Lukas Aichberger, Kajetan Schweighofer, Sepp Hochreiter"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=wdhruVcRx1"
tags: ["query:luq"]
score: 8.0
evidence: 为LLM提出基于原理的单序列不确定性度量
tldr: 现有不确定性方法依赖多序列采样，计算昂贵。本文基于适当评分规则的理论分析，发现最可能输出序列的负对数似然可作为原则性不确定性度量，提出G-NLL近似方法。实验表明，G-NLL在保持高检测性能的同时大幅降低计算开销，为实用LLM不确定性估计提供了新方向。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-wdhruvcrx1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1407, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-wdhruvcrx1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 711, \"height\": 554, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-wdhruvcrx1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1377, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-wdhruvcrx1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1463, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-wdhruvcrx1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1462, \"height\": 601, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-wdhruvcrx1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1455, \"height\": 915, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-wdhruvcrx1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1445, \"height\": 2246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-wdhruvcrx1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1436, \"height\": 1480, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-wdhruvcrx1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1454, \"height\": 910, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-wdhruvcrx1/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1448, \"height\": 955, \"label\": \"Table\"}]"
motivation: 多序列不确定性估计计算成本高，且缺乏理论依据。
method: 基于适当评分规则，提出单序列度量G-NLL，通过近似极大似然序列的负对数似然实现。
result: 在幻觉检测等任务上，G-NLL以更低计算量取得与多序列方法相当的效果。
conclusion: 单序列度量在理论和实践上都有优势，是高效不确定性估计的可行方案。
---

## Abstract
Large Language Models (LLMs) are increasingly employed in real-world applications, driving the need to evaluate the trustworthiness of their generated text. To this end, reliable uncertainty estimation is essential. Leading uncertainty estimation methods generate and analyze multiple output sequences, which is computationally expensive and impractical at scale. In this work, we inspect the theoretical foundations of these methods and explore new directions to enhance computational efficiency. Building on the framework of proper scoring rules, we find that the negative log-likelihood of the most likely output sequence constitutes a theoretically principled uncertainty measure. To approximate this alternative measure, we propose G-NLL, obtained using a single output sequence from greedy decoding. This approach streamlines uncertainty estimation while preserving theoretical rigor. Empirical results demonstrate that G-NLL achieves state-of-the-art performance across various scenarios. Our work lays the theoretical foundation for efficient and reliable uncertainty estimation in natural language generation, challenging the necessity of the prevalent methods that are more complex and resource-intensive.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：现有LLM不确定性估计方法（如预测熵PE、语义熵SE）需要采样多条输出序列并分析语义，计算成本高，难以在大规模实际场景中部署。
- **整体含义**：能否设计一种**仅依赖单条输出序列**的不确定性度量，既保证理论严谨性，又大幅降低计算开销？本文通过重新审视评分规则理论，给出了肯定答案。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：基于**适当评分规则**（proper scoring rules）框架，指出使用**零一评分**（zero-one score）替代常用的对数评分（logarithmic score），可导出不确定性度量为**最可能输出序列的负对数似然（MSP）**，即最小熵（min-entropy）。
- **关键近似**：精确计算MSP需要搜索所有可能输出序列，不可行。本文提出**G-NLL**，通过**贪心解码**（greedy decoding）生成单条序列，然后累加该序列中每个token的最大概率的对数（即 token-wise 最大化近似序列级最大化）。
- **公式说明**：  
  - 理论度量：\( M(p(y|x,w)) = -\max_{y \in Y^T} \log p(y|x,w) \)  
  - 实际近似：\( \text{G-NLL} = -\sum_{t=1}^T \log(\max_{y_t \in V} p(y_t | x, y_{<t}, w)) \)  
- **理论分析**：通过样本复杂度界证明，估计MSP所需的样本数远少于估计PE；合成实验也验证贪心解码/束搜索能高质量近似MSP，而PE的蒙特卡洛估计方差大。

## 3. 实验设计：数据集、场景、对比方法
- **数据集**：TriviaQA（>3000实例）、SVAMP（>300）、NQ-Open（>3600），每个数据集包含短答案（short）和长答案（long）两种生成任务，共6个任务。
- **对比方法**：基于对数评分的方法：PE、LN-PE（长度归一化）、SE、LN-SE、D-SE（离散语义熵）。这些方法均需采样10条输出序列。
- **评价指标**：AUROC（区分正确/错误答案），正确性通过SQuAD F1>0.5或LLM-as-a-judge（Llama-3.1-70B）判定。

## 4. 资源与算力
- 文中未明确说明训练或推理的**具体GPU型号、数量、训练时长**，仅提及“所有实验在单节点8× NVIDIA A100上完成，总耗时约100节点小时”。因此，无法精确总结算力细节。

## 5. 实验数量与充分性
- **实验数量**：主流实验覆盖6种LLM（Llama-3.1 8B/70B PT/IT，Falcon Mamba 7B PT/IT）× 6个任务 × 2种评价指标 = 72个主要场景（表1汇总为18个平均结果）。
- **消融实验**：
  - 对比不同近似MSP的方法（多温度采样、束搜索 vs 贪心解码）（图2）。
  - 长度归一化的影响（附录表4）。
  - 束搜索改进效果（附录表5）。
- **充分性**：实验覆盖多种架构、规模、训练阶段、任务类型（短路/长答案），对比了主流的5种多序列方法，评价采用AUROC和拒绝准确率，设计相对全面、客观公平。

## 6. 主要结论与发现
- G-NLL（单序列贪心解码）在**18个场景中13个优于所有采样方法**，其余5个则不相上下；**平均AUROC 0.721**，显著高于最佳采样方法D-SE（0.707）。
- 长度归一化会**降低**G-NLL性能（即使任务长度变化大）；束搜索有小幅提升但计算成本更高，贪心解码是最佳效率-效果权衡。
- 理论分析表明，估计MSP比估计PE具有更低的样本复杂度，与实验观察一致。

## 7. 优点
- **理论创新**：首次从适当评分规则角度为单序列不确定性度量提供严格理论依据，挑战多序列方法“必需”的假设。
- **计算高效**：G-NLL仅需一次贪心解码，无需采样、语义聚类或额外模型调用，超参数自由。
- **实验设计全面**：覆盖 Transformer 和状态空间模型、多种规模、预训练/指令微调、短/长答案，评价指标包含AUROC和拒绝准确率。
- **消融充分**：系统分析了近似策略、长度归一化、束搜索等对性能的影响。

## 8. 不足与局限
- **语义忽略**：当前G-NLL仅基于token概率，未显式建模语义等价性，在“说法不同但语义相同”的场景下可能高估不确定性。作者承认语义扩展（如MCP）会带来计算开销，但未深入探究。
- **概率访问要求**：G-NLL需要直接访问生成token的概率，对于仅提供API且不暴露logprobs的模型（如某些商业闭源模型）不适用。
- **实验范围有限**：仅限问答任务，未在段落生成、摘要、长文本等场景验证；LLM-as-a-judge使用同族模型（Llama-3.1-70B），可能存在评价偏差。
- **超参数敏感性未充分讨论**：虽然声称G-NLL无超参数，但生成时使用的温度、top-p等可能影响生成质量，文中统一使用贪心解码（温度=0），对非贪婪设置下的性能未做测试。
- **理论假设**：推导依赖于后验期望和贝叶斯近似，实际中LLM的单一参数化是否满足这些假设存在疑问。

（完）
