---
title: "Simple Yet Effective: An Information-Theoretic Approach to Multi-LLM Uncertainty Quantification"
title_zh: 简单而有效：多LLM不确定性量化的信息论方法
authors: "Maya Kruse, Majid Afshar, Saksham Khatwani, Anoop Mayampurath, Guanhua Chen, Yanjun Gao"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.emnlp-main.1551.pdf"
tags: ["query:luq"]
score: 8.0
evidence: 提出基于信息论的多大语言模型不确定性量化方法MUSE
tldr: 现有不确定性量化方法多聚焦于单个模型，忽略了模型多样性带来的互补预测。本文提出MUSE，一种基于信息论的多LLM不确定性量化方法，通过Jensen-Shannon散度识别并聚合校准良好的LLM子集。实验表明MUSE在不同设置下均能产生更可靠的不确定性估计，显著优于单模型方法。该工作为利用模型集成提升置信度提供了简洁有效的方案。
source: EMNLP-2025-Main
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1551/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1650, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1551/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 807, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1551/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1647, \"height\": 750, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1551/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 801, \"height\": 570, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1551/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 806, \"height\": 630, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1551/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 852, \"height\": 365, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1551/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1550, \"height\": 486, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1551/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 805, \"height\": 367, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1551/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 615, \"height\": 578, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1551/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1562, \"height\": 396, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1551/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 831, \"height\": 677, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1551/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 730, \"height\": 353, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1551/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 732, \"height\": 248, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1551/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1644, \"height\": 554, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1551/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1663, \"height\": 458, \"label\": \"Table\"}]"
motivation: 大语言模型在不同输入上表现不一致，需要量化不确定性，但传统方法忽视模型多样性。
method: 提出MUSE，利用Jensen-Shannon散度从多个LLM中选择并聚合校准良好的子集。
result: 实验证明MUSE能有效提升不确定性估计的可靠性，优于单模型方法。
conclusion: 该工作展示了利用模型多样性进行不确定性量化的潜力。
---

## Abstract
Large language models (LLMs) often behave inconsistently across inputs, indicating uncertainty and motivating the need for its quantification in high-stakes settings. Prior work on calibration and uncertainty quantification often focuses on individual models, overlooking the potential of model diversity. We hypothesize that LLMs make complementary predictions due to differences in training and the Zipfian nature of language, and that aggregating their outputs leads to more reliable uncertainty estimates. To leverage this, we propose MUSE (Multi-LLM Uncertainty via Subset Ensembles), a simple information-theoretic method that uses Jensen-Shannon Divergence to identify and aggregate well-calibrated subsets of LLMs. Experiments on binary prediction tasks demonstrate improved calibration and predictive performance compared to single-model and naive ensemble baselines. In addition, we explore using MUSE as guided signals with chain-of-thought distillation to fine-tune LLMs for calibration. MUSE is available at: https://github.com/LARK-NLP-Lab/MUSE.

---

## 论文详细总结（自动生成）

# 论文总结：Simple Yet Effective: An Information-Theoretic Approach to Multi-LLM Uncertainty Quantification

## 1. 论文的核心问题与整体含义（研究动机和背景）
大语言模型在不同输入上常表现不一致，即使相同输入在不同解码设置下也可能输出分歧结果。这种不确定性在高风险领域（如医疗诊断）尤为关键，需要量化以保证信任与安全。现有不确定性量化方法多聚焦于单个模型（如自一致性、序列似然、置信度校准等），忽视了多个模型间因训练数据、目标和架构差异而带来的互补预测能力。作者假设不同LLM在不同输入区域有各自优势（源于语言的Zipf分布特性），通过聚合多个模型的输出可以更可靠地近似真实标签，从而降低不确定性。基于此，提出MUSE（Multi-LLM Uncertainty via Subset Ensembles），一种简单而有效的信息论方法。

## 2. 论文提出的方法论
### 核心思想
- 利用Jensen-Shannon Divergence (JSD)衡量多个LLM预测分布之间的分歧程度。
- 将不确定性分为两个部分：
  - **认知不确定性 (epistemic)**：模型间意见分歧，通过平均JSD量化。
  - **偶然不确定性 (aleatoric)**：输入本身的固有噪声，通过平均二元熵量化。
- 目标是选择模型子集，使认知不确定性最小化（即达到高共识），同时保持一定多样性以避免过拟合。

### 关键技术细节
- **单个LLM不确定性估计**：
  - 自一致性（Self-Consistency）：对同一输入多次随机解码（温度T=0.7，k=10），将输出映射为二元标签，计算正类频率作为概率；再使用bootstrap（B=100次，重采样90%）得到更稳定的分布。
  - 序列似然评分（SLL）：计算两个候选正类/负类文本的log-likelihood，通过softmax获得概率（确定性方法，作基线）。
- **MUSE子集选择算法**：
  - **输入**：来自N个LLM的预测概率集合 `P = {p_i}`，每个`p_i`为正类概率。
  - **置信度**：`c_i = |p_i - 0.5|`（越接近0.5表示越不确定）。
  - **两种策略**：
    - **Greedy**：从置信度最高的预测开始，逐步添加使子集认知不确定性增加的模型，直到增长超过容忍阈值`ε_tol`（控制多样性）。
    - **Conservative**：从置信度最高的预测开始，逐步添加使总不确定性（认知+β×偶然）降低的模型，直到改善小于阈值τ（更谨慎，避免噪声）。
  - **参数**：`m_min`（最小子集大小）、`ε_tol`或`τ`、β（平衡两种不确定性）。
- **聚合**：
  - 简单平均：子集内`p_i`的平均。
  - 依偶然不确定性加权：权重 = 1 - H(p_i)，即更自信的模型权重更大。

### 算法流程（文字说明）
1. 计算每个LLM的预测概率（通过自一致性或SLL）。
2. 按置信度降序排序。
3. 初始化子集`S`为置信度最高的模型的概率。
4. 按策略依次评估其他模型：
   - 计算加入候选后的子集认知不确定性（平均JSD vs 子集均值）。
   - 若满足条件（Greedy：增加不超过`ε_tol`；Conservative：总不确定性降低超过`τ`），则加入。
5. 得到最终子集后，通过平均或加权平均得到聚合概率`p_hat`。
6. 可选：输出总不确定性（认知+β×偶然）作为补充信号。

## 3. 实验设计
### 数据集与场景
- **TruthfulQA**：通用领域问题，判断答案是否真实（二元分类）。
- **EHRShot**：电子健康记录（急诊心肌梗死、高脂血症、狼疮等预测任务）。
- **MIMIC-Extract**：重症监护病房记录，预测住院时长（≥3天、≥7天）和院内死亡率。
所有任务均为二分类。

### 基准方法
- **单模型**：Mistral-7B-Instruct、Qwen2-7B-instruct、Gemma-7B-it、Deepseek-R1-Distil-Qwen-32B（DS-Qwen）。每种模型使用SLL和自一致性（GEN_BS）两种不确定性估计。
- **朴素集成**：多数投票、所有模型均值。
- **MUSE**：Greedy与Conservative变体，带/不带偶然不确定性加权。

### 评估指标
- AUROC（区分能力）
- ECE（期望校准误差，校准性）
- Brier Score（整体概率预测质量）

另外还进行了MUSE引导的监督微调（SFT）实验，基于MIMIC-Extract的LOS3任务，用MUSE输出作为银标准信号，结合直接SFT和链式思维（CoT）蒸馏。

## 4. 资源与算力
- 所有LLM运行在配备**4×A100 40GB GPU**的服务器上。
- 对DS-Qwen使用了**8-bit量化**以减少推理时间和内存。
- 未明确报告训练或推理的具体耗时。

## 5. 实验数量与充分性
### 实验覆盖
- **主要实验**：在3个不同领域的二分类数据集上，对比了4种单模型+2种朴素集成+多种MUSE变体，共数十组比较。
- **消融实验**：
  - 分析MUSE子集选择中模型频率（哪些模型被选中）。
  - 参数敏感性（`m_min`和`ε_tol`）对AUROC/ECE的影响（用轮廓图展示）。
  - 对比固定子集（如DS+Qwen2）与MUSE自适应选择。
  - 对比使用预测概率`p(Yes)` vs. 总不确定性作为评分信号。
  - 对比“弱模型主导”与“强模型主导”场景（EHRShot的高脂血症 vs. 狼疮任务）。
- **SFT实验**：直接SFT + 三种CoT蒸馏变体（Original、Bayesian、No p_hat），两种输入格式（默认、原始概率），两个目标模型（Mistral、Qwen）。
- **额外分析**：各模型与MUSE共识的JSD大小（表9）、不同LLM组合的AUROC对比（表8）。

### 充分性评估
- **客观性**：对比基线包括强单模型和朴素集成，公平。
- **全面性**：覆盖不同任务、不同模型大小、不同不确定性估计方式；消融充分，参数分析细致。
- **局限性**：仅二分类任务，未在更复杂的生成任务或长文本上验证；模型数量有限（仅4种开源模型）；缺少对实时/资源受限场景的讨论。

## 6. 论文的主要结论与发现
1. **MUSE显著提升校准与鲁棒性**：在多数任务上，MUSE的AUROC与单模型最优相当或更优，而校准误差（ECE、Brier Score）显著更低。
2. **自适应子集选择**：MUSE不会盲目包含弱模型，而是基于不确定性动态选择互补子集。例如，当弱模型存在时，保守策略会排除它；当强模型占主导时则充分利用。
3. **总不确定性可作为辅助信号**：虽然预测概率`p(Yes)`在区分任务上更优，但总不确定性在某些场景下（如LOS7任务）Brier Score更低，可用于软校准或弃权。
4. **MUSE引导的SFT效果具有模型依赖性**：直接SFT对Mistral有一定益处（AUROC提升），但校准可能恶化；对Qwen则反之。CoT蒸馏可进一步改善校准，但结果不稳定，取决于推理风格和是否包含`p_hat`信号。
5. **参数平衡多样性与可靠性**：增大最小子集大小和适度放松认知不确定性阈值可同时提升AUROC和校准，表明适当的模型多样性是关键。

## 7. 优点
- **简洁有效**：仅基于信息论指标（JSD和熵），方法直观，无需复杂训练或额外数据。
- **理论动机明确**：将不确定性分解为认知与偶然，并利用模型间分歧作为认知不确定性的代理。
- **自适应性强**：无需预先知道模型优劣，算法根据输入动态选择子集，避免固定集成的缺陷。
- **参数可调**：通过`m_min`和`ε_tol`控制多样性与噪声的权衡，提供了灵活性。
- **实验设计细致**：不仅比较整体性能，还深入分析了子集组成、参数敏感性、弱/强模型场景，以及SFT下游应用的可行性。
- **开放源代码**：代码已公开，便于复现和扩展。

## 8. 不足与局限
- **任务范围有限**：仅验证了二分类任务，未涉及多分类、生成任务或长文本不确定性量化，限制了方法的通用性。
- **模型多样性不够**：仅使用4种开源模型，且包含不同规模（7B、32B），但缺乏对更多异构模型（如不同架构或领域特化模型）的评估。
- **假设所有模型输出在推理时可用**：实际部署中可能受限于接口调用次数、延迟或隐私要求。
- **SFT实验结果混合**：MUSE信号作为教师虽有一定价值，但效果不稳定，未能提供通用的微调策略，需进一步研究模型如何内化概率推理。
- **未讨论效率**：多模型推理的计算开销与延迟未量化，在资源受限场景下可能不现实。
- **校准改善存在权衡**：在某些情况下（如TruthfulQA上DS-Qwen的SLL AUROC最高但校准差），MUSE在AUROC上并非最优，说明提升校准可能牺牲一定区分能力。

（完）
