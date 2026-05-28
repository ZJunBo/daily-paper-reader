---
title: "The Best of Both Worlds: Bridging Quality and Diversity in Data Selection with Bipartite Graph"
title_zh: 两全其美：用二部图弥合数据选择中的质量与多样性
authors: "Minghao Wu, Thuy-Trang Vu, Lizhen Qu, Gholamreza Haffari"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=nCoaJYNCcg"
tags: ["query:smd"]
score: 7.0
evidence: 平衡质量与多样性的数据选择方法；可应用于安全数据选择
tldr: 该工作提出GraphFilter，一种基于二部图的数据选择方法。将数据集建模为句子与n-gram的图，通过集覆盖问题平衡质量与多样性，迭代选择优先级最高的句子。在多个SFT任务上优于现有方法。该方法可天然适配安全数据选择场景，通过定义安全质量指标来筛选混合微调中的安全数据。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ncoajynccg/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1530, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ncoajynccg/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1642, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ncoajynccg/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 774, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ncoajynccg/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 858, \"height\": 622, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ncoajynccg/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1644, \"height\": 1481, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ncoajynccg/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 545, \"height\": 449, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ncoajynccg/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 804, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ncoajynccg/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 843, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ncoajynccg/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 856, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ncoajynccg/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 839, \"height\": 263, \"label\": \"Table\"}]"
motivation: 现有数据选择方法常偏重质量或多样性，导致微调性能次优。
method: 将数据选择建模为集覆盖问题，构建句子与n-gram的二部图，用质量与多样性乘积作为优先级迭代选择。
result: 在多个SFT任务上指标显著提升，平衡了质量与多样性。
conclusion: 该数据选择框架可方便地扩展至安全数据混合场景。
---

## Abstract
The performance of large language models (LLMs) is strongly influenced by the quality and diversity of data used during supervised fine-tuning (SFT). However, current data selection methods often prioritize one aspect over the other, resulting in suboptimal training outcomes. To address this, we formulate data selection as a set cover problem and present GraphFilter, a novel approach that balances both quality and diversity in data selection. GraphFilter models the dataset as a bipartite graph connecting sentences to their constituent n-grams, then employs a priority function that combines quality and diversity metrics multiplicatively. GraphFilter iteratively selects sentences with the highest priority, removes covered n-grams from the bipartite graph, and recomputes priorities to reflect the changing data landscape. We validate GraphFilter using three model backbones across six widely-used benchmarks, demonstrating that it outperforms nine existing baselines in both model performance and computational efficiency. Further analysis shows that our design choices lead to more effective subset selection, underscores the value of instruction diversity, and provides insights into how quality and diversity interact with different subset sizes.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- 现有数据选择方法常偏重**质量**或**多样性**，导致微调性能次优：质量导向方法可能忽略语言模式多样性，多样性导向方法可能引入低质量数据。
- 解决思路：同时最大化数据子集的质量和多样性，以优化LLM的监督微调性能。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将数据选择建模为**集覆盖问题**，通过**二部图**连接句子节点与n-gram节点，利用**优先级函数**（质量×多样性）迭代选择最具价值的句子。
- **关键技术细节**：
  - **二部图构建**：句子集合U（N个），n-gram集合V（M个），边表示句子包含该n-gram。
  - **迭代选择算法（Algorithm 1）**：
    1. 初始化S=∅，计算每个句子u的优先级ϕ(u)=QUALITY(u)×DIVERSITY(u)。
    2. while |S|<k且U非空：
       - 选择优先级最高的句子u*。
       - 从图中移除u*及其关联的n-gram和所有连接到这些n-gram的边。
       - 重新计算剩余句子的优先级。
  - **质量度量（QUALITY）**：采用SuperFilter指标，即响应在条件指令下的困惑度与自困惑度之比，值越高表示响应越相关、信息量越大。
  - **多样性度量（DIVERSITY）**：计算句子中所有n-gram（unigram, bigram, trigram）的TF-IDF分数之和，分数越高表示n-gram越独特。
  - **优先级函数**：ϕ(u)=SuperFilter(x,y) × Σ TF-IDF(v)。乘积形式自然平衡两者。
- **理论依据**：当优先级全为1时，算法退化为贪心集覆盖，近似比为H(r)（r为最大句子长度）。

## 3. 实验设计：数据集、基准、对比方法

- **训练数据集**：Magpie（由Llama-3-70B-Instruct生成，共300K训练实例），实验默认从中选取10K子集。
- **模型骨干**：Gemma-2-2B、Mistral-7B-v0.3、Llama-3-8B。
- **评测基准**：6个广泛应用的标准测试集，分为两组：
  - 标准化基准：MMLU、ARC、HellaSwag、GSM8K（测量准确率）。
  - LLM-as-a-Judge基准：AlpacaEval-2.0（报告长度控制胜率LC和原始胜率WR）、MT-Bench（μMT，宏观平均分数，缩放到1-100分制）。
  - 综合指标μALL为以上所有基准的宏观平均。
- **对比基线（9种）**：
  - 启发式：Random、Longest（按指令长度降序）。
  - 质量导向：Perplexity（指令困惑度降序）、ARMO RM、AlpaGasus（原用GPT-3.5-turbo，此处改用Gemma-2-27B-IT）、DEITA、SuperFilter（IFD指标）。
  - 多样性导向：KMeans（10K聚类并选最近中心点）、InsTag（话题标签去重）。
- **训练设置**：统一超参数（batch size 64, lr 2e-5, warmup 0.05, linear schedule, 3 epochs）。

## 4. 资源与算力

- **GPU**：2张A100 80GB GPU，通过PCIe互联。
- **运行时对比**（选择10K实例）：
  - GraphFilter（使用SuperFilter）：2.48小时。
  - 无优先级的GraphFilter（仅CPU）：0.53小时（最快）。
  - 其他基线：Perplexity 0.92h, ARMO RM 5.93h, AlpaGasus 32.34h, DEITA 22.65h, SuperFilter 1.95h, KMeans 2.26h, InsTag 25.48h。
- 说明：GraphFilter计算高效，可在CPU上运行，无需GPU。

## 5. 实验数量与充分性

- **主要实验**：3个模型 × 6个基准 × 10种方法 = 180个条件，结果展示在Table 1中，清晰全面。
- **消融实验**（均在Llama-3-8B上）：
  1. n-gram组合：unigram/bigram/trigram逐一消除（Table 3）。
  2. 优先级函数组件：去掉质量或多样性，替换质量指标（Table 4）。
  3. n-gram阶数：n=1~5对比（Table 5）。
  4. 应用对象：仅指令、仅回复、两者同时（Table 6）。
  5. 预算影响：1K/5K/10K/50K/100K/200K下与SuperFilter和InsTag对比（Figure 3）。
- **可视化分析**：t-SNE投影比较GraphFilter与ARMO RM、InsTag的语义覆盖率（Figure 2）。
- **公平性**：所有方法使用相同超参数、相同训练epoch、相同评测方式，统一基线实现。实验覆盖多种场景，消融充分，结论可信。

## 6. 论文的主要结论与发现

- **GraphFilter在所有三个模型上一致超越全部九种基线**，μALL提升最高达+3.38（Llama-3-8B vs Longest）。
- **质量与多样性互补**：单独使用任一指标均不如结合使用。
- **指令多样性比回复多样性更重要**：仅对指令应用GraphFilter获得最佳性能。
- **预算影响选择策略**：小预算（1K/5K）下质量导向方法占优，大预算下多样性导向逐渐超越，GraphFilter在所有预算下均优于随机。
- **trigram是最优n-gram阶数**：平衡性能与效率。
- **GraphFilter选择的数据子集同时达到高多样性和高质量**（Figure 2a），优于其他方法。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：首次将数据选择严格建模为集覆盖问题，引入二部图结构，天然兼顾n-gram覆盖率。
- **效率极佳**：无需GPU即可运行；优先级函数可预计算质量分数，选择过程仅需CPU，运行时远低于多数基线。
- **灵活性**：质量度量可替换为任意指标（Perplexity、ARMO RM、DEITA等），不限于SuperFilter。
- **深入分析**：不仅报告主结果，还详细探讨了n-gram选择、优先级函数组件、预算效应等，提供了实践指导。
- **开源可复现**：使用公开数据集Magpie和全开源模型，实验配置清晰，便于验证。

## 8. 不足与局限

- **应用场景有限**：仅针对SFT数据选择，未验证预训练或其他微调阶段（如RLHF）的适用性。
- **质量度量依赖模型**：SuperFilter或其他质量指标可能引入模型偏差，且需要预计算（虽然高效）。
- **n-gram覆盖的语义局限**：n-gram特征无法捕捉高阶语义相似性（如同义词、句法结构），可能遗漏“语义上的新知识”。
- **数据规模限制**：主要基于10K子集实验，更大预算（200K）下仅与SuperFilter和InsTag对比，缺乏与更多方法的大规模对比。
- **泛化性风险**：仅使用Magpie一个数据集（由Llama-3生成），其他来源或领域的SFT数据效果未知。
- **未讨论公平性/安全**：未分析所选数据子集是否存在偏见或有害内容。

（完）
