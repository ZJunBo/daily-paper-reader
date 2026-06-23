---
title: "ESI: Epistemic Uncertainty Quantification via Semantic-preserving Intervention for Large Language Models"
title_zh: ESI：通过语义保持干预对大语言模型进行认知不确定性量化
authors: "Mingda Li, Xinyu Li, Longxuan Ma, Weinan Zhang"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=vrwTC598H0"
tags: ["query:luq"]
score: 9.0
evidence: 通过语义保持干预的认知不确定性量化
tldr: 论文建立LLM不确定性与语义保持干预下输出不变性之间的因果联系，提出灰色盒不确定性量化方法ESI。通过测量干预前后输出变化有效估计认知不确定性。在多种LLM和QA任务上验证其有效性，为因果视角的UQ提供新途径。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-vrwtc598h0/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 731, \"height\": 766, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vrwtc598h0/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 692, \"height\": 457, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vrwtc598h0/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vrwtc598h0/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1439, \"height\": 324, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vrwtc598h0/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1443, \"height\": 868, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-vrwtc598h0/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1450, \"height\": 1035, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-vrwtc598h0/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1445, \"height\": 1302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vrwtc598h0/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 821, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vrwtc598h0/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 651, \"height\": 184, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vrwtc598h0/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1442, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vrwtc598h0/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 650, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vrwtc598h0/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1324, \"height\": 383, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vrwtc598h0/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1447, \"height\": 1329, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vrwtc598h0/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1447, \"height\": 919, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vrwtc598h0/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1448, \"height\": 1223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vrwtc598h0/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1448, \"height\": 1223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vrwtc598h0/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1444, \"height\": 1217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vrwtc598h0/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 846, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-vrwtc598h0/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1444, \"height\": 1219, \"label\": \"Table\"}]"
motivation: LLM不确定性量化困难，需要更鲁棒的方法，因果视角有望提供新思路。
method: 提出基于语义保持干预的灰色盒UQ方法，测量干预前后输出变化。
result: ESI在多个LLM和QA任务上有效估计认知不确定性，优于现有方法。
conclusion: 因果干预为UQ提供新框架，ESI兼具理论价值和实用效果。
---

## Abstract
Uncertainty Quantification (UQ) is a promising approach to improve model reliability, yet quantifying the uncertainty of Large Language Models (LLMs) is non-trivial. In this work, we establish a connection between the uncertainty of LLMs and their invariance under semantic-preserving intervention from a causal perspective. Building on this foundation, we propose a novel grey-box uncertainty quantification method that measures the variation in model outputs before and after the semantic-preserving intervention. Through theoretical justification, we show that our method provides an effective estimate of epistemic uncertainty. Our extensive experiments, conducted across various LLMs and a variety of question-answering (QA) datasets, demonstrate that our method excels not only in terms of effectiveness but also in computational efficiency.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义
**研究动机**：大型语言模型（LLM）在实际应用中经常产生幻觉（hallucination），即生成不真实的内容，严重影响其可靠性。不确定性量化（UQ）是提高模型可信度的重要途径，但对于自由文本生成任务，UQ面临两大挑战：输出空间巨大且难以遍历，以及偶然不确定性（aleatoric）与认知不确定性（epistemic）的纠缠。现有基于采样和语义聚类的方法往往需要大量样本，且主要估计总不确定性而非认知不确定性。

**整体含义**：论文从因果视角出发，建立LLM不确定性与其在语义保持干预下输出不变性之间的理论联系，并提出一种新的灰色盒UQ方法（ESI），旨在高效、准确地估计认知不确定性，从而更可靠地判断模型生成是否正确。

---

## 2. 方法论
**核心思想**：
- 论文引入一个文本对（上下文C、响应R）生成的因果图模型。其中，人类生成响应时主要基于文本的语义（通过因果路径 C → 语义推断 → 响应语义 → 响应），而非上下文变量间的虚假相关。
- 假设真实语言生成函数在语义保持干预下应保持稳定。若模型主要依赖因果路径，则输出对语义保持干预不敏感；若依赖虚假相关，则干预后输出变化大。因此，**模型的不确定性可通过语义保持干预下输出的不变性来度量**。

**关键技术细节**：
1. **语义保持干预**：实现两种方式：
   - 句子级：使用LLM生成同义改写（Paraphrase，Para）。
   - 字符级：从随机选中的单词中随机删除后部一个字符（Skip-One-Char，SOC），参数p控制干预比例。
2. **不变性度量函数**：
   - 对原始提示x生成响应y*，获取逐token的预测分布。
   - 将y*与干预后提示x̃拼接，通过单次前向传播（利用teacher forcing并行化）获取新的预测分布。
   - 计算每个位置token分布的差异（使用Hellinger距离），取平均后作为单个干预的V值。
   - 对多个干预变体求期望得到最终UQ分数U_ESI。

**公式**：
- U_ESI = (1/L·N) Σ_l Σ_t D( p(y|y*_<t, x), p(y|y*_<t, x̃_l) )
- 实际实现中采用截断top-k预测分布，并对每个token的差异加权，权重为原始分布熵。

**理论支持**：
- 将U_ESI与期望成对KL散度（EPKL）建立联系，证明其可作为认知不确定性估计量近似。

---

## 3. 实验设计
**数据集**：共5个自由文本QA数据集
- 开放域单答案：SciQ (1000例)、TriviaQA (11,313例)
- 开放域多答案（高偶然不确定性）：AmbigQA (2002例)、TruthfulQA (817例)
- 开放书式对话：CoQA (7983例，带支持文档)

**基准方法**：
- 基于采样的方法：LN-PE、INSIDE、M.I.、Semantic Entropy、Semantic Density、SAR（SOTA）
- 所有基线使用各自论文推荐配置（采样数10或5，温度等）

**模型**：
- Llama2-chat 7B、Mistral-Nemo-Instruct 12B、Llama3-Instruct 8B、Llama3-Instruct 70B
- 另补充Llama3.1 8B、Qwen2.5 14B、Qwen3 4B

**评价指标**：
- 主指标：AUROC（区分正确/错误生成的ROC曲线下面积）
- 补充指标：AURC、AUCPR、选择性准确率（Acc@80%、Acc@90%）
- 正确性标注采用BEM语义相似度（阈值0.7），而非Rouge-L。

---

## 4. 资源与算力
文中未明确说明训练环境或训练所需算力（因为该方法不涉及训练，仅在推理阶段计算UQ）。
推理实验运行环境提及：使用NVIDIA A100 80GB GPU进行Llama3-Instruct 8B的运行时测量。但未给出完整实验的GPU数量、总时长等细节。

---

## 5. 实验数量与充分性
**实验数量**：非常充分。
- 主实验结果（Table 1）：4个模型 × 5个数据集 × 8种UQ方法（含两个变体） × 10次重复 → 大量对比。
- 补充实验（Table 7-13）：额外模型、额外基线、不同评价指标、消融实验。
- 消融实验：干预函数类型（WeakPara, Typo, Antonym）、top-k值、干预强度p、距离函数（KL、Bhattacharyya、平方Hellinger）等。
- 效率实验：运行时对比、样本数影响（图3）。
- 所有结果给出均值与标准差，并标注统计显著性（t检验，5%水平）。

**充分性**：实验设计较为客观公平。使用10次重复减少方差，对比基线使用官方配置；但部分基线（如Semantic Entropy）的语义相似度模型与论文原始一致，而ESI使用的改写模型可能更强（DeepSeek-V2.5），存在一定不公平比较。此外，基线采样数固定（5或10），ESI使用更多干预变体（SOC为10，Para为5），但干预变体是输入而非输出，在推理效率上仍有优势。

---

## 6. 主要结论与发现
1. **ESI方法在所有模型和数据集上均优于或持平SOTA基线**，平均AUROC提升约1-4%，且标准差更低（更稳定）。
2. **在偶然不确定性高的数据集（AmbigQA, TruthfulQA）上提升最大**，说明ESI能更好分离认知不确定性。
3. **在开放书式数据集CoQA上提升也明显**，可能因为因果路径更显式。
4. **计算效率显著优于基线**：SOC变体比SAR快3-5倍；仅需2-3个干预变体即可达到较优性能。
5. **语义保持是关键**：破坏语义的干预（如Antonym）会导致性能急剧下降。
6. **Hellinger距离作为度量函数效果最好**。

---

## 7. 优点
- **理论创新**：从因果视角建立UQ与语义干预不变性的联系，提供认知不确定性的可计算代理。
- **高效实用**：利用teacher forcing并行化，避免重复采样大量生成；SOC方法轻量级，无需外部模型。
- **实验扎实**：多种模型、数据集、评价指标，消融全面，结果统计显著性验证。
- **稳定性强**：标准偏差远低于基线方法。
- **对高偶然不确定性场景鲁棒**：符合认知不确定性估计的预期。

---

## 8. 不足与局限
- **灰色盒方法**：需要访问模型logits（至少top-k）。如果API限制logprobs输出，则效率优势无法完全体现（特别当无法并行化）。
- **假设依赖**：方法有效性建立在“模型能够通过正确因果路径生成答案”的前提下。对于小模型或较弱模型可能不成立，但论文未充分验证这一边界条件。
- **短文本限制**：当前实验聚焦于短回答（claim-level）。长文本生成时，token级信息分散，效果可能受影响。论文认为可以分解为短claim来处理，但未验证。
- **近似误差**：理论推导中使用单轨迹蒙特卡罗近似，存在偏差；虽在经验上表现好，但理论上并非无偏估计。
- **改写模型成本**：Para变体依赖外部改写模型（API调用），增加延迟和成本。论文虽提供SOC替代，但Para效果更好，在部署时需权衡。
- **公平性问题**：部分基线（如Semantic Entropy）使用Deberta-large进行语义聚类，而ESI使用更强力的改写模型（DeepSeek-V2.5），可能造成不公平优势。虽然SOC基线完全自主且仍然优于SAR，缓解了这一担忧。

（完）
