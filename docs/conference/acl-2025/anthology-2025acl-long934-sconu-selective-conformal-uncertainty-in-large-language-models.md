---
title: "SConU: Selective Conformal Uncertainty in Large Language Models"
title_zh: SConU：大语言模型中的选择性共形不确定性
authors: "Zhiyuan Wang, Qingni Wang, Yue Zhang, Tianlong Chen, Xiaofeng Zhu, Xiaoshuang Shi, Kaidi Xu"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.acl-long.934.pdf"
tags: ["query:luq"]
score: 9.0
evidence: 选择性共形不确定性用于大语言模型
tldr: 现有共形不确定性方法在LLM中无法处理违反可交换性的离群样本，导致不可控制误报率。本文提出SConU，首次实现显著性检验，通过两个共形p值决定样本是否偏离，保证了预测集的有效性。实验证明SConU能提供更可靠的覆盖保证。
source: ACL-2025-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.934/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1659, \"height\": 665, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.934/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 803, \"height\": 753, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.934/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1655, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.934/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1656, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.934/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1648, \"height\": 581, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.934/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1649, \"height\": 583, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.934/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1658, \"height\": 616, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.934/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1656, \"height\": 615, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.934/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1658, \"height\": 617, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.934/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1649, \"height\": 271, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.934/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1647, \"height\": 1208, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.934/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 797, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.934/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1645, \"height\": 627, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.934/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 797, \"height\": 594, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.934/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 798, \"height\": 824, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.934/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 798, \"height\": 695, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.934/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 794, \"height\": 338, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.934/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1645, \"height\": 386, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.934/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 799, \"height\": 738, \"label\": \"Table\"}]"
motivation: 现有共形方法无法识别违反可交换性的不确定性离群点。
method: 提出SConU方法，开发两个共形p值进行显著性检验，偏离的样本被标记。
result: SConU在多个数据集上提供了更可靠且可操作的预测集。
conclusion: 共形p值能有效识别离群样本，提升不确定性估计的鲁棒性。
---

## Abstract
As large language models are increasingly utilized in real-world applications, guarantees of task-specific metrics are essential for their reliable deployment. Previous studies have introduced various criteria of conformal uncertainty grounded in split conformal prediction, which offer user-specified correctness coverage. However, existing frameworks often fail to identify uncertainty data outliers that violate the exchangeability assumption, leading to unbounded miscoverage rates and unactionable prediction sets. In this paper, we propose a novel approach termed Selective Conformal Uncertainty (SConU), which, for the first time, implements significance tests, by developing two conformal p-values that are instrumental in determining whether a given sample deviates from the uncertainty distribution of the calibration set at a specific manageable risk level. Our approach not only facilitates rigorous management of miscoverage rates across both single-domain and interdisciplinary contexts, but also enhances the efficiency of predictions. Furthermore, we comprehensively analyze the components of the conformal procedures, aiming to approximate conditional coverage, particularly in high-stakes question-answering tasks.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）在实际部署中需要任务指标的保证，现有基于分割共形预测（SCP）的共形不确定性（ConU）方法为用户指定正确覆盖率，但无法识别违反**可交换性（exchangeability）**假设的离群样本，导致误覆盖率无界且预测集不可操作。
- **核心问题**：在单领域和跨领域问答任务中，现有ConU框架因模型能力差异、数据分布偏移等导致经验误覆盖率（EMR）超过用户设定风险水平，预测集效率低下。
- **整体含义**：需要一种能够检测并排除不确定性离群点的方法，以确保共形预测的统计严格性和可操作性。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：首次在共形不确定性中实现显著性检验，通过构造两个**共形p值**判断测试样本是否偏离校准集的 uncertainty 分布，若偏离则拒绝回答；同时保留校准集的完整性，推导最小可管理风险水平。
- **关键技术细节**：
  - **共形p值（SConU）**：  
    \( p_{N+1} = \frac{1 + \sum_{i=1}^N \mathbf{1}\{u_i \ge u_{N+1}\}}{N+1} \)  
    其中 \( u_i \) 为预测熵（PE）表示的不确定性。
  - **优化版本（SConU-Pro）**：  
    \( p'_{N+1} = \frac{1 + \sum_{i=1}^N \mathbf{1}\{u_i \ge u_{N+1}, \, y_i^* \in E(x_i, D_{\text{cal}}, \alpha)\}}{N+1} \)  
    仅计数那些在当前风险水平下校准点自身被正确覆盖的样本，提高参考质量。
  - **保留校准集完整性**：不手动删除校准样本，而是推导最小可管理风险水平 \( \alpha_l = \frac{N L_N(1)}{N+1} \)，其中 \( L_N(1) \) 为校准集中候选集不包含正确回答的比例。
  - **流程**：部署LLM后，计算最小风险水平；对每个测试样本进行显著性检验（p值与显著性水平δ比较）；过滤离群点后在剩余样本上应用标准共形方法。

### 3. 实验设计：数据集、场景、Benchmark与对比方法

- **数据集**：
  - 闭集QA：MMLU（57学科子集）、MMLU-Pro（10选项，更鲁棒）、MedMCQA（医学考试）
  - 开放域QA：TriviaQA（闭卷）、CoQA（会话QA）
- **场景**：单领域（相同学科内校准与测试）、跨领域（不同学科间校准与测试）。
- **Benchmark**：以标准共形框架（基础ConU）作为基线，对比SConU和SConU-Pro。
- **指标**：经验误覆盖率（EMR）、大小分层误覆盖率（SSM）、平均预测集大小（APSS）。
- **LLMs**：OpenChat、LLaMA-3系列、Vicuna、Qwen-2/2.5系列，参数从3B到32B。
- **对比方法**：仅与自身基线（无离群点过滤）对比，未与其他替代方法比较。

### 4. 资源与算力

- **未明确说明**：论文未提供GPU型号、数量、训练时长等具体算力信息。只提到使用“off-the-shelf”预训练模型进行推理，未涉及训练。

### 5. 实验数量与充分性

- **实验数量**：较充分。包括：
  - 采样大小校准实验（4种LLM，3个β值，2个数据集，100次随机划分）
  - 单领域边际覆盖实验（2种LLM，2个学科，9个风险水平，100次试验）
  - 跨领域EMR/APSS实验（MMLU-Pro 14×14学科矩阵，MMLU 16×16学科矩阵，多种LLM）
  - 条件覆盖实验（MedMCQA、Clinical Knowledge，调节logit/频率权重、采样大小、分割比例）
  - 预测效率实验（TriviaQA、CoQA，语义去重前后APSS变化）
- **充分性**：实验覆盖多模型、多数据集、多种风险水平，消融分析完整（权重、采样大小、分割比例、是否过滤离群点）。但跨领域实验仅使用频率分数（黑盒设置），未结合logit混合分数进行更全面对比；缺少与最新ConU方法的直接对比（如ConU、API-Conf等）。

### 6. 论文的主要结论与发现

- **SConU能严格管理EMR**：在单领域和跨领域场景下，平均和众数EMR均低于风险水平，方差小于基线。
- **SConU-Pro进一步提升严格性**：通过考虑校准点自身覆盖状态，EMR进一步降低且APSS更小（很多测试集APSS=1，准确识别正确选项）。
- **保留校准集完整性是可行的**：采样大小校准实验证明，即使不删除无回答的校准样本，通过调整风险水平仍能保证覆盖率。
- **条件覆盖可通过多因素优化**：使用更可靠的NS（如频率+logit混合）、增大采样数、增加校准数据、确保可交换性、使用领域专长模型均可降低SSM；SConU可显著改善条件覆盖。
- **预测效率存在语义冗余**：去重后APSS大幅下降（如从8.07降至1.08），说明可提升可操作性。

### 7. 优点：方法或实验设计上的亮点

- **方法创新**：首次将显著性检验引入共形不确定性，构造符合统计定义的共形p值，从理论上保障误报率受控。
- **保留校准集完整性**：不需手动删除校准样本，更符合实际部署场景，且推导了最小风险水平，实用性强。
- **双p值设计**：SConU-Pro通过考虑校准点自身的预测状态进一步提高鲁棒性。
- **实验设计全面**：涵盖多个LLM系列、多数据集、多种风险水平、单/跨领域、条件覆盖和效率分析，结果可视化丰富（热力图、曲线图）。
- **开源代码**：提供GitHub仓库，可复现。

### 8. 不足与局限

- **未与其他最新ConU方法直接对比**：仅对比自身基线，未与ConU、API-Conf、Prompt Risk Control等较新工作比较。
- **离群点定义单一**：仅使用预测熵作为不确定性度量，虽然提及可扩展至多假设检验，但实验未展示。
- **条件覆盖分析仅限模拟**：未提供无条件保证，仅在特定参数组合下近似，实际高维条件覆盖仍无法严格保证。
- **计算开销未讨论**：采样生成（50次调用）和p值计算可能增加推理时延，未进行效率对比。
- **黑盒设置局限性**：跨领域实验仅使用频率分数，可能漏检不确定性离群点；若能结合logit可能效果更好，但在黑盒场景无法实现。
- **可交换性假设仍存在**：虽然过滤了离群点，但剩余样本仍需假设可交换，实际中可能仍被违反。

（完）
