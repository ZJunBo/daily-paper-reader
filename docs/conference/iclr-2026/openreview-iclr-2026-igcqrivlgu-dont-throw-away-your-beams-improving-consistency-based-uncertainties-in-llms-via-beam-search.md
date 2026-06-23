---
title: "Don't Throw Away Your Beams: Improving Consistency-based Uncertainties in LLMs via Beam Search"
title_zh: 不要丢弃你的波束：通过波束搜索改进大语言模型中基于一致性的不确定性
authors: "Ekaterina Fadeeva, Maiya Goloburda, Aleksandr Rubashevskii, Roman Vashurin, Artem Shelmanov, Preslav Nakov, Mrinmaya Sachan, Maxim Panov"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=igcQRiVlgu"
tags: ["query:luq"]
score: 9.0
evidence: 波束搜索改进大语言模型基于一致性的不确定性
tldr: 本文提出使用波束搜索替代多项式采样生成候选，用于基于一致性的不确定性量化。波束搜索降低了估计方差，提升了性能，并提供了集合概率质量的理论下界。在短问答任务上验证了该方法优于传统采样方法。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-igcqrivlgu/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 696, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-igcqrivlgu/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 645, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-igcqrivlgu/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 704, \"height\": 321, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-igcqrivlgu/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1422, \"height\": 565, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-igcqrivlgu/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1421, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-igcqrivlgu/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1439, \"height\": 398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-igcqrivlgu/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 706, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-igcqrivlgu/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1444, \"height\": 1141, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-igcqrivlgu/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1426, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-igcqrivlgu/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 681, \"height\": 740, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1401, \"height\": 330, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1252, \"height\": 494, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1228, \"height\": 728, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1451, \"height\": 814, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1448, \"height\": 383, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1442, \"height\": 735, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1021, \"height\": 682, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1440, \"height\": 501, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 678, \"height\": 773, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 676, \"height\": 779, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 681, \"height\": 740, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1358, \"height\": 621, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 673, \"height\": 769, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1456, \"height\": 1424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1334, \"height\": 398, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1223, \"height\": 990, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1440, \"height\": 933, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1438, \"height\": 926, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1441, \"height\": 881, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1440, \"height\": 916, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1440, \"height\": 917, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1439, \"height\": 912, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1441, \"height\": 920, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-igcqrivlgu/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1439, \"height\": 911, \"label\": \"Table\"}]"
motivation: 多项式采样在短问答中产生重复且方差大，降低一致性UQ性能。
method: 采用波束搜索生成候选集合，并推导其概率质量下界。
result: 波束搜索方法提升了UQ性能并降低了跨运行方差。
conclusion: 波束搜索是生成一致性UQ候选的有效替代方案。
---

## Abstract
Consistency-based methods have emerged as an effective approach to uncertainty quantification (UQ) in large language models. These methods typically rely on several generations obtained via multinomial sampling, measuring their agreement level. However, in short-form QA, multinomial sampling is prone to producing duplicates due to peaked distributions, and its stochasticity introduces considerable variance in uncertainty estimates across runs. We introduce a new family of methods that employ beam search to generate candidates for consistency-based UQ, yielding improved performance and reduced variance compared to multinomial sampling. We also provide a theoretical lower bound on the beam set probability mass under which beam search achieves a smaller error than multinomial sampling. We empirically evaluate our approach on six QA datasets and find that its consistent improvements over multinomial sampling lead to state-of-the-art UQ performance.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **动机**：在大语言模型（LLM）中，基于一致性的不确定性量化（UQ）方法通常依赖多项式采样生成多个候选答案，然后测量它们之间的一致性来评估模型置信度。然而，在短问答任务中，多项式采样存在两个严重问题：
  - **重复率高**：由于输出分布尖峰（peaked distribution），采样易产生大量重复或几乎相同的输出，浪费计算资源。
  - **方差大**：每次采样结果不同，导致不确定性估计在不同运行间波动大，降低鲁棒性。
- **背景**：一致性UQ方法（如Dissimilarity、Eccentricity等）对评估特定预测的置信度很重要，尤其在黑盒场景。但现有方法均基于多项式采样，限制了其有效性。

## 2. 方法论：核心思想、关键技术细节、公式或算法

- **核心思想**：用波束搜索（Beam Search）替代多项式采样来生成候选答案。波束搜索能自然产生**互不相同**的候选，且这些候选覆盖了模型输出分布的**高概率区域**，从而减少重复、降低方差，同时提供“免费”的分布信息（候选概率）。
- **关键步骤**：
  1. **波束搜索生成候选**：设置宽度 \(M\)，得到候选集合 \(B_M(x) = \{b^{(1)}, \dots, b^{(M)}\}\) 及其序列概率 \(p(b^{(i)}|x)\)。
  2. **重要性加权**：对每个候选赋予归一化权重 \(w_i = \frac{p(b^{(i)}|x)}{\sum_{j=1}^M p(b^{(j)}|x)}\)，避免低概率候选被过度代表。
  3. **构建波束加权估计器**：将原有基于等权采样的估计器改为加权形式。例如：
     - **Dissimilarity** 原式：\(\hat{U}^{\text{MC}}_D(y^*|x) = \frac{1}{M}\sum_{i=1}^M [1 - s(y^{(i)}, y^*)]\)
     - **波束加权版**：\(\hat{U}^{\text{b}}_D(y^*|x) = \sum_{i=1}^M w_i [1 - s(b^{(i)}, y^*)]\)
     - 类似地，**Eccentricity**、**Eigenvectors Dissimilarity**、**CoCoA** 等均引入加权版本。
- **理论分析（定理1）**：给出波束加权估计器误差小于多项式采样蒙特卡洛估计器的充分条件。当波束集总概率质量 \(m_B > 1 - \frac{1}{2\sqrt{M}}\) 时（对 \(M=10\) 约为 \(m_B > 0.842\)），波束加权估计的均方误差更小。实际中该条件在短输出上经常满足，实验也一致支持。

## 3. 实验设计

- **数据集**：6个短文本QA数据集，覆盖不同难度和格式：
  - 闭卷：TriviaQA（2000题）、Web Questions（1490题）
  - 开卷：CoQA（2000题）、HotpotQA（2000题）
  - 多选：CommonsenseQA（1221题）、ARC-Challenge（447题）
- **模型**：3种主流LLM的base和instruct版本：
  - Gemma 3 4B、Llama 3.1 8B、Qwen 3 8B
- **对比基准（Baseline）**：
  - 信息型：Sequence Probability、Mean Token Entropy、Perplexity、CCP
  - 反射型：P(True)
  - 采样型：Semantic Entropy、SAR、Lexical Similarity、EigValLaplacian、NumSemSets
  - 一致性型（原始多项式采样版）：Dissimilarity、Eccentricity、EigVecDissimilarity、CocoaMSP、CocoaPPL
- **评估指标**：主要使用**预测-拒绝比（PRR）**，同时报告ROC-AUC和PR-AUC。质量度量采用AlignScore。
- **实验设置**：所有方法使用 \(M=10\) 个候选（波束/采样）。相似性函数采用DeBERTa-large的蕴含概率。

## 4. 资源与算力

- **硬件**：2×NVIDIA A100（80 GB）GPU。
- **总用时**：约34 GPU-days（约12个壁钟天）。
  - 主实验（6模型×6数据集）：约24 GPU-days
  - 额外消融实验（采样策略、top-1光束评分等其他目标）：约10 GPU-days
- **说明**：论文明确给出了计算预算细节。

## 5. 实验数量与充分性

- **实验规模**：非常充分。
  - **主实验**：6个数据集 × 6个模型 = 36个组合，每个组合报告5个波束加权方法和5个原方法（共10个）加上约12个额外baseline，表格涵盖大量数据。
  - **消融实验**：
    - 样本数量 \(M\) 从1到15的影响（图5）
    - 输出长度五等分下的表现（图4）
    - 完整预测-拒绝曲线（图6）
    - 不同采样策略比较（附录A.1）：温度采样、多样化波束搜索、混合波束-多项式
    - 概率质量下限调节（附录A.2）
    - 其他采样目标（附录A.3）：语义熵、度矩阵
    - 图拉普拉斯嵌入参数（附录A.4）
    - 交叉编码器相似度替换（附录A.5）
    - 不同模型/数据集上样本数的广泛测试（附录A.6，图8）
    - 将top-1波束作为输出答案（附录D.1）
- **公平性**：所有方法使用相同候选数、相同相似度函数，超参数基于原论文或默认设置。波束加权方法仅改变采样策略，不引入不公平优势。
- **结论**：实验覆盖全面，验证了波束搜索在各种设置下的优势，消融分析完整。

## 6. 主要结论与发现

- **波束搜索一致优于多项式采样**：在所有6个数据集、6个模型上，波束加权的Dissimilarity、Eccentricity、EigVecDissimilarity、CocoaMSP、CocoaPPL的PRR均高于或等于原方法，且多数显著提升。
- **达到SOTA**：波束搜索版Dissimilarity在大多数base模型上获最佳PRR；CocoaMSP+波束搜索在instruct模型上领先。
- **短输出受益最大**：输出长度≤3的短答案上，波束搜索优势最明显（图4），因为多项式采样重复率高达30-50%。
- **低预算下高效**：波束搜索在 \(M \geq 3\) 时即达到高PRR，而多项式采样改善缓慢（图5）。
- **理论验证**：实际中约23%的TriviaQA样本满足定理1的充分条件，尤其短输出满足率更高（30-40%）。

## 7. 优点

- **创新性**：首次系统性地提出用波束搜索替代多项式采样来提升一致性UQ，并给出理论保证。
- **实用价值**：波束搜索产生的候选可复用为解码结果（免费获取不确定性），无需额外前向传播。
- **实验全面**：覆盖多种模型、数据集、变体、消融，结果可信。
- **开源**：代码在LM-Polygraph框架中公开，易于复现和扩展。
- **分析深入**：不仅展示经验优势，还从理论上解释条件，并通过冗余率、概率质量覆盖等分析直观说明原因。

## 8. 不足与局限

- **任务范围有限**：仅针对短文本QA，对于长文本生成（如摘要、对话）的效果尚未验证。
- **白盒要求**：方法需要访问序列概率（\(p(b|x)\)），在纯黑盒场景下无法直接使用（需近似估计）。
- **相似度函数依赖**：使用NLI模型的蕴含概率作为语义相似性，该指标可能不完美，更换其他相似度（如STS cross-encoder）时性能变化（附录A.5），说明方法对相似度选择有一定敏感性。
- **计算开销**：波束搜索本身比单次采样更耗费资源（尽管比多次采样小），尤其在波束宽度较大时。但论文指出可视为解码副产品。
- **超参数敏感**：波束宽度 \(M\) 需要设定（实验中固定10），理论上越大越好但饱和较快（图5）。
- **理论基础限于短输出**：定理1的充分条件在实际中满足比例不高（23%全局），需要更强的松弛或更紧的界。
- **对比基准不包含最新方法**：ICLR 2026为未来会议，但baseline包括以往SOTA，未与可能同期发表的方法对比。

（完）
