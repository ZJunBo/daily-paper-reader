---
title: Estimating Semantic Alphabet Size for LLM Uncertainty Quantification
title_zh: 估计语义字母大小以用于LLM不确定性量化
authors: "Lucas Hurley McCabe, Rimon Melamed, Thomas Hartvigsen, H Howie Huang"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=uYK6GPVg1O"
tags: ["query:luq"]
score: 9.0
evidence: 通过改进字母大小估计提升语义熵估计
tldr: 离散语义熵（DSE）估计算法在实践中低估真实语义熵。本文通过理论分析指出问题根源，并提出修正的语义字母大小估计器。改进后的方法在幻觉检测任务上表现更优，同时保持可解释性和少量采样需求，直接贡献于语义熵方法的实用化。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-uyk6gpvg1o/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1413, \"height\": 655, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uyk6gpvg1o/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1431, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uyk6gpvg1o/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uyk6gpvg1o/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 712, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uyk6gpvg1o/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 698, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uyk6gpvg1o/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1454, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uyk6gpvg1o/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1427, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uyk6gpvg1o/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1439, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uyk6gpvg1o/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1424, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uyk6gpvg1o/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1403, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-uyk6gpvg1o/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1441, \"height\": 364, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-uyk6gpvg1o/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1455, \"height\": 690, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uyk6gpvg1o/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1446, \"height\": 400, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uyk6gpvg1o/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 807, \"height\": 588, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-uyk6gpvg1o/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 889, \"height\": 880, \"label\": \"Table\"}]"
motivation: 现有离散语义熵估计器低估真实不确定性，影响检测性能。
method: 提出修正的语义字母大小估计器，更准确估计语义熵。
result: 在多个基准上，改进后的语义熵在幻觉检测中达到更高准确率。
conclusion: 准确估计语义字母大小是提升语义熵可靠性的关键。
---

## Abstract
Many black-box techniques for quantifying the uncertainty of large language models (LLMs) rely on repeated LLM sampling, which can be computationally expensive. Therefore, practical applicability demands reliable estimation from few samples. Semantic entropy (SE) is a popular sample-based uncertainty estimator with a discrete formulation attractive for the black-box setting. Recent extensions of SE exhibit improved LLM hallucination detection, but do so with less interpretable methods that admit additional hyperparameters. For this reason, we revisit the canonical discrete semantic entropy (DSE) estimator, finding that it underestimates the ``true'' semantic entropy, as expected from theory. We propose a modified semantic alphabet size estimator, and illustrate that using it to adjust DSE for sample coverage results in more accurate SE estimation in our setting of interest. Furthermore, we find that two semantic alphabet size estimators, including our proposed, flag incorrect LLM responses as well or better than many top-performing alternatives, with the added benefit of remaining highly interpretable.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

大型语言模型（LLM）在风险敏感场景中需要可靠的不确定性量化（UQ），以决定是否应拒绝回答（abstain）。黑盒环境（无法访问模型内部激活或序列对数概率）下，常用方法依赖多次LLM采样，计算成本高。语义熵（Semantic Entropy, SE）是一种流行的基于离散语义等价类的黑盒不确定性估计器，但经典的离散语义熵（Discrete Semantic Entropy, DSE）估计器在小样本（如n=10）时存在系统性低估“真实”语义熵的问题。这种偏差源于样本覆盖不全——未观测到的语义类别会导致分布“不够惊奇”，从而低估不确定性。论文旨在修正该偏差，提出更准确的语义字母表大小估计器，进而提升DSE的估计精度和下游幻觉检测性能。

## 2. 方法论：核心思想、技术细节与算法流程

- **核心思想**：将种群生态学中的“未观测物种”问题类比到语义类别估计。经典DSE隐含使用观测到的类别数k作为字母表大小，但真实字母表大小|S|可能更大。通过估计样本覆盖率并调整熵估计，可以减少偏差。
- **关键估计器**：
  - **Good-Turing覆盖率估计器**：\(\hat{C}_{GT} = 1 - f_1/n\)，其中f₁为仅出现一次的语义类别数（singletons）。由此转换得字母表大小估计：\(\hat{|S|}_{GT} = k n / (n - f_1)\)。但存在局限：当f₁=0时退化为k，当所有样本均属不同类别时无定义。
  - **谱估计器U_EigV**：基于响应图的归一化拉普拉斯特征值（来自Lin et al. 2024），但可能小于k（违反下界）。
  - **混合字母表大小估计器**（公式9）：综合以上两者，当f₁=n（每个样本一个类别）时取U_EigV，否则取两者最大值：\(\hat{|S|}_{Hybrid} = \max(\hat{|S|}_{GT}, U\_EigV)\)。
  - **混合DSE估计器**（公式10）：采用Chao-Shen形式的覆盖率调整熵，将经验频率乘以调整因子（k/\(\hat{|S|}_{Hybrid}\)），并引入修正项以避免小样本偏差。
- **算法流程**：
  1. 对查询q采样n个响应；
  2. 使用双向蕴含聚类（BEC）将响应分配到语义等价类；
  3. 计算观测类别数k、singletons数f₁、U_EigV；
  4. 根据公式9估计混合字母表大小；
  5. 代入公式10计算调整后的DSE。

## 3. 实验设计

- **数据集**：
  - **单正确答案**：HotpotQA（7405条）、SQuAD 2.0（11864条，因规模大仅用20%随机子集）。
  - **多正确答案**：BioASQ（4719条，每个问题1-15个参考答案）、合成数据集POTATO（131条，正确答案类别数1-722）。
- **基准方法**：
  - 黑盒SE估计器：经典DSE（插件估计器）、Chao-Shen覆盖率调整估计器。
  - 其他不确定性方法：预测熵（PE）、语义最近邻熵（SNNE）、核语言熵（KLE）、白盒SE。
  - 字母表大小估计器：NumSets、Good-Turing、U_EigV、混合估计器。
- **评估指标**：
  - 熵估计精度：以n=100的白盒SE（SE*）作为“真实”熵，计算MSE。
  - 错误分类检测：AUROC（识别LLM回答是否正确），并通过Bradley-Terry模型建立方法排名，使用Monte Carlo模拟考虑AUROC不确定性。
- **模型**：Gemma-2-9B、Gemma-3-12B、Llama-3.1-8B、Mistral-v0.3-7B、Phi-3.5-3.8B，共5个指令微调模型。
- **采样设置**：默认n=10（典型小样本场景），部分实验n取5,10,25,50,75,100；采样温度τ=1.0用于不确定性计算，τ=0.1用于获取最佳回答评估正确性。

## 4. 资源与算力

论文**未明确说明**使用的GPU型号、数量以及训练/推理时长。仅提到实验涉及5个模型在4个数据集上大量采样，且由于BEC（双向蕴含聚类）需要成对NLI调用，计算负担较重。对于SQuAD 2.0等大规模数据集，只用了20%子集，暗示算力有限。总体而言，资源消耗较大但未量化。

## 5. 实验数量与充分性

- **实验组数**：
  - 熵估计偏差展示（图2、图7-9）：5模型×4数据集×多种样本量。
  - 熵估计精度定量比较（表1）：5模型×4数据集×3种DSE变体。
  - 错误分类检测AUROC（图10）：5模型×3数据集×11种方法。
  - 排名分析（图3）：通过Bradley-Terry模型综合所有模型-数据集对的AUROC，并给出95%置信区间。
  - 聚类策略评估（表2）：在POTATO上与人工标注对比FMI/NMI/PA。
  - 覆盖率调整的鲁棒性：排除SE*<0.005的异常实例后验证模式一致（图9）。
- **充分性与公平性**：
  - 覆盖5个不同规模/家族的模型，3个真实QA数据集+1个合成数据集，方法种类全面（包括白盒、黑盒、近期SOTA方法SNNE/KLE）。
  - 使用Bradley-Terry对排名的统计不确定性进行建模（Bootstrapping、95% CI），避免了单一AUROC比较的局限性。
  - 潜不足：模型最大12B参数，未在更大模型（如70B+）上验证；聚类策略仅用NLI-NQ一种，未消融不同NLI/LLM聚类的影响；合成数据集POTATO规模小，可能影响统计稳定性。

## 6. 主要结论与发现

- 经典DSE在小样本下显著低估真实语义熵，而提出的混合DSE减少了此偏差，在所有5个模型和4个数据集上均取得最低MSE（表1）。
- 在错误分类检测任务中（AUROC），混合DSE是表现最好的显式语义熵估计器，优于经典DSE和Chao-Shen估计器，甚至超过白盒SE（图3）。
- 两个语义字母表大小估计器——混合估计器（\(\hat{|S|}_{Hybrid}\)）和U_EigV——在排名中与最复杂的方法KLE并列第一（95% CI均包含排名1），且具有高度可解释性（可直接理解为“有多少种不同答案”）。
- 白盒SE与经典DSE在错误检测性能上非常接近，因为RBMCI得出的概率分布与经验频率分布平均差异极小（表4），但SE对罕见类别过采样更鲁棒。

## 7. 优点

- **方法简单可解释**：字母表大小本身即有直观含义（“答案种类数”），无需额外超参数（如SNNE的尺度因子、KLE的核扩散参数）。
- **理论支撑**：基于种群生态学中成熟的Good-Turing估计和Chao-Shen熵调整，偏差校正有据可依。
- **实验严谨性**：排名分析考虑了AUROC估计的不确定性（DeLong方法+Monte Carlo模拟），并采用Bradley-Terry模型消除模型-数据集差异的干扰。
- **实用性强**：仅需少量样本（n=10）即可获得比经典方法更准确的估计，降低了黑盒UQ的采样成本。
- **对比公平**：与多种最新黑盒方法（KLE、SNNE）及白盒方法比较，且开源代码便于复现。

## 8. 不足与局限

- **模型规模有限**：仅测试≤12B参数模型，未验证在更大规模LLM（如70B/130B）上的泛化性。
- **聚类策略未优化**：NLI模型可能对某些领域（如生物医学）适应性不足，且未比较不同聚类算法的影响（如不同嵌入或阈值）。
- **异常值风险**：在Gemma-3-12B×POTATO上出现混合DSE过高估计的异常（3个实例），表明小样本+小真实熵场景下覆盖率调整可能放大噪声。
- **代理问题**：估计的实质是语义多样性，而非直接检测事实错误。高多样性不一定代表错误（如创造性任务），且模型可能自信出错（低多样性但错误）。
- **计算开销仍存**：BEC需要对所有响应对进行NLI（O(n²)），当n增大时仍不便宜；虽比采样100次更省，但比单次推理更重。
- **未探索白盒场景**：调整方法理论上可直接用于白盒SE，但论文未实验。

（完）
