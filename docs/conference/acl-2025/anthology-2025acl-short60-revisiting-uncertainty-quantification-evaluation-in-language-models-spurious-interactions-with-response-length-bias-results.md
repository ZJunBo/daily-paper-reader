---
title: "Revisiting Uncertainty Quantification Evaluation in Language Models: Spurious Interactions with Response Length Bias Results"
title_zh: 重新审视语言模型不确定性量化评价：与响应长度偏倚结果的伪交互
authors: "Andrea Santilli, Adam Golinski, Michael Kirchhof, Federico Danieli, Arno Blaas, Miao Xiong, Luca Zappella, Sinead Williamson"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.acl-short.60.pdf"
tags: ["query:luq"]
score: 7.0
evidence: 语言模型不确定性量化评价中的偏倚
tldr: 不确定性量化评价常使用AUROC衡量UQ方法与正确性函数的相关性。本文证明当两者受相同因素偏倚时，AUROC排名被系统性地扭曲。通过7种正确性函数的实验验证了这一理论，质疑了现有评价基准的可靠性。
source: ACL-2025-Short
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-short/anthology-2025.acl-short.60/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1650, \"height\": 542, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-short/anthology-2025.acl-short.60/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 786, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-short/anthology-2025.acl-short.60/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 336, \"height\": 617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-short/anthology-2025.acl-short.60/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1264, \"height\": 766, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-short/anthology-2025.acl-short.60/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 792, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-short/anthology-2025.acl-short.60/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1647, \"height\": 319, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-short/anthology-2025.acl-short.60/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1637, \"height\": 2412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-short/anthology-2025.acl-short.60/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1441, \"height\": 2103, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-short/anthology-2025.acl-short.60/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 807, \"height\": 386, \"label\": \"Table\"}]"
motivation: UQ评价中相互偏倚可能导致基准失效。
method: 理论证明相互偏倚非随机地扭曲AUROC排名，并使用实验验证。
result: 多种正确性函数均存在偏倚，影响评价结果。
conclusion: 需要开发对偏倚不敏感的评价指标。
---

## Abstract
Uncertainty Quantification (UQ) in Language Models (LMs) is key to improving their safety and reliability. Evaluations often use metrics like AUROC to assess how well UQ methods (e.g., negative sequence probabilities) correlate with task correctness functions (e.g., ROUGE-L). We show that mutual biases-when both UQ methods and correctness functions are biased by the same factors-systematically distort evaluation. First, we formally prove that any mutual bias non-randomly skews AUROC rankings, compromising benchmark integrity. Second, we confirm this happens empirically by testing 7 widely used correctness functions, from lexical-based and embedding-based metrics to LM-as-a-judge approaches, across 4 datasets × 4 models × 8 UQ methods. Our analysis showsthat length biases in correctness functions distort UQ assessments by interacting with length biases in UQ methods. We identify LM-as-a-judge methods as the least length-biased, offering a promising path for a fairer UQ evaluation.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机和背景）
- 不确定性量化（UQ）在语言模型（LM）中用于检测幻觉，提高安全性和可靠性。评价UQ方法时，通常使用AUROC等指标来衡量UQ方法（如负序列概率）与正确性函数（如ROUGE-L）之间的相关性。
- 现有基准依赖于正确性函数对生成答案进行正确/错误标注。然而，如果UQ方法和正确性函数都受到相同因素（如响应长度）的偏倚，则会产生“相互偏倚”（mutual bias），导致AUROC排名被系统性扭曲，从而破坏基准的可靠性和公平性。
- 本文旨在揭示这种相互偏倚的存在、成因及其对UQ评价的严重影响，并提出更可靠的评价协议。

## 2. 方法论
- **核心思想**：形式化证明相互偏倚对AUROC的影响。论文将正确性函数的误差分为两种情况：
  1. 独立误差：若正确性函数的误差与UQ方法独立，则AUROC是有噪声但无偏的估计（不系统偏爱任何UQ方法）。
  2. 相互偏倚误差：若正确性函数的误差与UQ方法相关（例如都受长度影响），则AUROC会被系统性偏倚，某些UQ方法被高估或低估，排名被扭曲。
- **关键技术细节**：
  - 从理论（附录C）推导出受偏倚的AUROC表达式，显示相互偏倚会导致高估或低估真实AUROC。
  - 识别出“响应长度”是一个关键混淆变量：许多UQ方法（如负序列概率、朴素熵）随长度增加而增高；许多正确性函数（如ROUGE-L F1）也对长度敏感（偏向短答案）。
  - 通过Spearman相关系数（图4）证实UQ方法与长度存在显著相关；通过散点图（图5）显示正确性函数对长度的依赖。
- **公式/算法流程**（文字说明）：
  - 真实AUROC基于真实正确性标签 \(h\)，估计AUROC基于正确性函数 \(\hat{h}\)。论文推导了估计AUROC与真实AUROC的关系，当存在相互偏倚时，条件概率不再等于无条件概率，导致偏移。
  - 实验通过改变正确性函数，观察AUROC排名变化，并结合人类标注判断正确性函数的可靠性。

## 3. 实验设计
- **数据集**：TriviaQA、SQuAD、NQ-Open、SimpleQA（共4个，均为问答任务）。
- **模型**：Falcon-7B、Qwen2.5-7B、Mistral-7B-Instruct-v0.1、Mistral-7B-Instruct-v0.3（共4个模型）。
- **UQ方法**：共8种，包括Token Length、Character Length、Perplexity、Negative Sequence Probability、Naive Entropy、Mean Token Entropy、Probe (trained with RougeL-F1 >0.5 or LM-as-a-judge)、Semantic Entropy (with/without length normalization)。
- **正确性函数**：共7种，包括ROUGE-1 (F1)、ROUGE-L (F1/Recall)、SQuAD (F1)、BERTScore (F1)、SentenceBERT cosine similarity、AlignScore、LM-as-a-judge (prompt)。每种可能使用不同阈值二值化。
- **Benchmark**：以人类标注（4个标注者，450个样本）为黄金标准，计算各正确性函数与人类判断的Cohen's Kappa一致性，并观察AUROC排名变化。
- **对比逻辑**：固定UQ方法和模型/数据集，仅改变正确性函数，观察AUROC和排名变化；同时分析各正确性函数与人类的一致性，以及长度偏倚影响。

## 4. 资源与算力
- 论文中**未明确说明**使用了什么具体的GPU型号、数量、训练总时长。仅在附录A提到Probe训练使用L-BFGS优化器（tol=0.0001，max iter=10000），但未提及硬件细节。
- 实验涉及4个数据集×4个模型×8个UQ方法×多个正确性函数，总计算量较大，但论文未报告具体算力开销。

## 5. 实验数量与充分性
- **实验规模**：采用 4 datasets × 4 models × 8 UQ methods × 7 correctness functions 的全组合，再加上对人类标注的验证（450样本），实验量较为充分。
- **充分性**：
  - 覆盖了当前主流的UQ方法和正确性函数，包括词法、嵌入、LM判断三类。
  - 进行了排名稳定性分析（图1）、人类一致性分析（图2）、阈值敏感性分析（图3、图8）、相关性和长度偏倚可视化（图4、图5、图7）。
  - 还包含消融性分析：例如不同阈值对正确性函数与人类一致性的影响。
- **客观与公平**：实验设计较系统，同时承认某些正确性函数在特定阈值下与人判断无一致性。但论文未进行跨任务（如机器翻译、摘要）验证，仅在QA上测试，公平性限于该场景。

## 6. 主要结论与发现
- **理论结论**：任何相互偏倚（不仅是长度）都会非随机地扭曲AUROC排名，使某些UQ方法被抬高或压低，损害基准可靠性。
- **实证发现**：
  - 正确性函数的选择会显著改变UQ方法的排名（图1），且最常用的词法和嵌入函数（如ROUGE-L F1、SentenceBERT）与人判断一致性差。
  - 长度偏倚是主要的混淆变量：UQ方法（如负序列概率）与长度正相关，而词法正确性函数（如ROUGE-L F1）偏向短答案，导致伪相关，使长度相关的UQ方法被高估。
  - LM-as-a-judge方法（尤其是AlignScore和prompt-based judge）长度偏倚最小，与人判断一致性最高，是更可靠的正确性函数。
- **建议**：在可能的情况下使用LM-as-a-judge评估UQ，并应在新任务/数据集上先验证其与人类标注的一致性。

## 7. 优点
- **理论严谨**：提供了形式化证明，区分了独立误差和相互偏倚的影响，为理解UQ评价中的系统性偏差奠定了理论基础。
- **实证充分**：大规模实验覆盖多种UQ方法和正确性函数，且引入人类标注作为黄金标准，增强了结论的可靠性。
- **发现问题**：明确指出长度偏倚是一个广泛存在的混淆变量，并给出了具体证据，对该领域的基准选择有重要警示意义。
- **实用建议**：推荐使用LM-as-a-judge，并提供了可操作的验证步骤（如先评估与人类的一致性）。

## 8. 不足与局限
- **任务局限性**：所有实验局限于问答（QA）任务；论文承认在更开放的任务（如机器翻译、摘要）中长度偏倚也可能存在，但未直接验证。
- **正确性函数局限**：LM-as-a-judge本身也有偏倚风险（如使用同一个模型同时作为判断者和UQ方法的组成部分可能导致额外相关），且计算开销大。
- **未探索其他混淆变量**：长度只是相互偏倚的一个例子，论文未深入探讨其他可能的混淆因素（如词汇频率、写作风格等）。
- **算力资源未报告**：缺少训练/推理的硬件信息和时间，限制了可复现性和对计算成本的评估。
- **人类标注规模有限**：仅450个样本，且来自三个数据集，可能不足以覆盖所有潜在偏差模式。
- **阈值选择的简化**：论文分析了阈值敏感性，但未提供自动选择最佳阈值的通用方法。

（完）
