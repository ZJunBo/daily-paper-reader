---
title: "Semantic Volume: Quantifying and Detecting Both External and Internal Uncertainty in LLMs"
title_zh: 语义体积：量化与检测LLM中的外部和内部不确定性
authors: "Xiaomin Li, Zhou Yu, Ziji Zhang, Yingying Zhuang, Swair Shah, Narayanan Sadagopan, Anurag Beniwal"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40443/44404"
tags: ["query:luq"]
score: 9.0
evidence: 量化LLM的外部与内部不确定性
tldr: 现有方法主要关注LLM内部不确定性，忽略了外部不确定性（模糊查询导致）。本文提出语义体积（Semantic Volume）这一数学度量，同时量化两类不确定性。通过扰动输入并测量语义空间体积变化，该方法能更全面地检测幻觉。实验表明，语义体积在多个基准上优于现有不确定性估计方法，为LLM可靠部署提供了新工具。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有不确定性量化方法只关注内部知识冲突，忽视了输入模糊导致的外部不确定性。
method: 提出Semantic Volume度量，通过对输入进行扰动并测量语义空间的体积变化来量化不确定性。
result: 在多个基准上，Semantic Volume有效检测幻觉，优于现有方法。
conclusion: 该工作为LLM不确定性提供了统一框架，改善了可靠性。
---

## Abstract
Large language models (LLMs) have demonstrated remarkable performance across diverse tasks by encoding vast amounts of factual knowledge. However, they are still prone to hallucinations, generating incorrect or misleading information, often accompanied by high uncertainty. Existing methods for hallucination detection primarily focus on quantifying internal uncertainty, which arises from missing or conflicting knowledge within the model. However, hallucinations can also stem from external uncertainty, where ambiguous user queries lead to multiple possible interpretations. In this work, we introduce **Semantic Volume**, a novel mathematical measure for quantifying both external and internal uncertainty in LLMs. Our approach perturbs queries and responses, embeds them in a semantic space, and computes the Gram matrix determinant of the embedding vectors, capturing their dispersion as a measure of uncertainty. Our framework provides a generalizable and unsupervised uncertainty detection method without requiring internal access to LLMs. We conduct extensive experiments on both external and internal uncertainty detections, demonstrating that our Semantic Volume method consistently outperforms existing baselines in both tasks. Additionally, we provide theoretical insights linking our measure to differential entropy, unifying and extending previous sampling-based uncertainty measures such as the semantic entropy. Semantic Volume is shown to be a robust and interpretable approach to improving the reliability of LLMs by systematically detecting uncertainty in both user queries and model responses.

---

## 论文详细总结（自动生成）

# 论文《Semantic Volume: Quantifying and Detecting Both External and Internal Uncertainty in LLMs》详细总结

## 1. 论文的核心问题与整体含义
- **研究动机**：大型语言模型（LLM）常产生幻觉（hallucination），现有不确定性检测方法主要关注由模型内部知识缺失或冲突导致的**内部不确定性**，但忽略了由用户查询模糊、缺乏上下文或存在多种解释导致的**外部不确定性**。这两种不确定性都需要被检测，以便采取不同处理策略（如外部不确定性应通过澄清问题处理，内部不确定性则可通过检索增强等方法缓解）。
- **整体含义**：本文提出一种统一框架，能同时量化和检测LLM的外部与内部不确定性，无需访问模型内部状态或概率，仅通过黑盒采样即可实现，旨在提升LLM的可靠性。

## 2. 论文提出的方法论
### 核心思想
- 通过**扰动**（perturbations）生成输入（查询或响应）的多个变体，将这些变体嵌入到语义空间中，计算这些嵌入向量张成的**平行六面体体积**（parallelepiped volume），以此度量语义分散程度。体积越大，不确定性越高。

### 关键技术细节
- **扰动生成**：
  - 外部不确定性：对每个查询，利用LLM生成多个增强/改写版本。
  - 内部不确定性：对每个查询−响应对，采样多个候选响应。
- **嵌入与归一化**：使用Sentence-Transformer（如Qwen2-1.5B-instruct）获取嵌入向量，并归一化为单位向量。
- **维度缩减**：应用PCA将嵌入向量投影到低维空间（外部取d=10，内部取d=20），以更好分离扰动。
- **计算公式**：
  - 定义归一化嵌入矩阵 \(V = [v_1, v_2, \ldots, v_n] \in \mathbb{R}^{d \times n}\)。
  - 计算校正后的Gram矩阵行列式：\(\text{log det}(V^\top V + \epsilon I)\)，其中\(\epsilon = 10^{-10}\)用于数值稳定。
  - 最终**Semantic Volume** = \(\log \text{det}(\tilde{V}^\top \tilde{V} + \epsilon I)\)，\(\tilde{V}\)为PCA投影后的嵌入矩阵。
- **分类决策**：使用少量标注子集（100个样本）确定最优阈值\(\tau^*\)（最大化F1），将大于阈值的样本判定为高不确定性（外部：模糊查询；内部：幻觉响应）。

### 算法流程
1. 对每个样本生成n次扰动（n=20）。
2. 获取嵌入、归一化、PCA降维。
3. 计算Semantic Volume。
4. 基于阈值进行二元分类。

## 3. 实验设计
### 外部不确定性检测
- **数据集**：
  - **CLAMBER**（Zhang et al., 2024）：3K平衡数据集，每条查询标注是否模糊。
  - **AmbigQA**（Min et al., 2020）：平衡子集5K样本，标注模糊/明确。
- **基线方法**：
  - **提示型**：Vicuna-13B、Llama2-13B/70B、Llama3.2-3B、ChatGPT（零样本/少样本/CoT）。
  - **概率型**：Last Token Entropy、Log Probabilities（需模型内部概率，使用Llama3.2-1B）。
  - **采样型**：p(True)、Lexical Similarity、Semantic Entropy（均改编用于查询扰动）。
- **评估指标**：Accuracy、F1。

### 内部不确定性检测
- **数据集**：TriviaQA和SQuAD各5K平衡样本（根据ROUGE-L<0.3标记为幻觉）。响应由不同LLM生成（温度0），采样时温度1。
- **响应生成模型**：Llama3.2-1B、Llama3-8B、Qwen2.5-1.5B、Qwen3-8B/14B、Mistral-7B。
- **基线方法**：同上，适用于响应采样。
- **评估指标**：Accuracy、F1、AUROC（面积下曲线，直接比较不确定性分数）。

### 对比方法
- 包括所有主流类型：提示型、概率型、采样型（p(True)、Lexical Similarity、Semantic Entropy），共约10种以上。

## 4. 资源与算力
- 论文未明确说明使用的GPU型号、数量或训练时长。该方法为**训练无关**（training-free），仅需推理和嵌入计算，算力需求较低。
- 仅在阈值调优时需少量标注数据，其余为无监督/黑盒操作，因此未提供硬件细节。

## 5. 实验数量与充分性
- **实验数量**：
  - 外部不确定性：2个数据集，对比7种以上基线，报告Accuracy和F1（含多次运行标准差）。
  - 内部不确定性：2个数据集（TriviaQA、SQuAD），6种不同LLM生成响应，对比多种基线，报告Accuracy、F1、AUROC。
- **消融与超参数分析**：
  - 扰动数量n的影响（附录F）。
  - PCA维度d的影响（附录E，内部讨论）。
  - 不同嵌入模型（Sentence-Transformer变体）对比（附录G）。
  - 不同响应生成模型下的性能（附录H）。
- **分布分离可视化**：使用KS检验比较不同不确定性度量在幻觉/正确两组上的分离程度（图2）。
- **公平性**：所有方法在相同扰动/采样设置下比较，随机种子多次运行报告均值±标准差，避免偶然性。
- **总体评价**：实验覆盖面广，涵盖两种不确定性类型、多个数据集、多种模型和基线，分析充分，结论可信。

## 6. 论文的主要结论与发现
- **Semantic Volume在两个任务上均一致优于所有基线**：在CLAMBER上F1达69.1%，AmbigQA上67.6%；内部不确定性检测中AUROC最高达79.7%（TriviaQA）和68.8%（SQuAD）。
- **Semantic Volume无需模型内部访问**（不依赖token概率或隐藏状态），适用于闭源/API模型。
- **理论上**：Semantic Volume可视为嵌入向量的微分熵，是Semantic Entropy的连续化推广，更全面捕捉语义分散（不仅考虑簇间差异，还考虑簇内差异）。
- 概率型方法（Last Token Entropy、Log Probabilities）效果较差；提示型方法（如p(True)）易出现全“是”或全“否”的偏置。

## 7. 优点
- **统一框架**：首次同时处理外部和内部不确定性检测。
- **无需训练**：完全无监督，仅依赖预训练嵌入模型和PCA，无额外训练开销。
- **黑盒适用**：不要求模型权值或logits，仅需API调用生成扰动/嵌入。
- **理论连接**：与微分熵建立联系，统一并扩展了现有采样方法（如Semantic Entropy）。
- **鲁棒性**：PCA降维和Gram矩阵行列式计算对噪声稳健，分布分离效果明显。

## 8. 不足与局限
- **仅覆盖“不确定性高=错误”的情况**：不处理“高置信度幻觉”（confidently wrong），即模型错误但不确定性低的情形。作者承认这是局限性，并指出需要结合事实性检查等不同策略。
- **扰动生成依赖外部LLM**：外部不确定性检测需使用LLM进行查询改写，可能引入额外偏差或成本。
- **阈值选择需少量标注数据**：尽管可用无需标注的启发式阈值（如中位数），但最优效果需100个标注样本。
- **实验未涉及多模态或更大规模模型**：主要基于文本模型，未考察多模态或超大规模（如GPT-4级别）下的泛化能力。
- **计算开销**：生成20个扰动并嵌入+PCA，相较于直接提示有一定额外推理成本，但总体可控。
- **未明确给出硬件资源**：无法直接复现成本估计。

（完）
