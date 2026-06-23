---
title: "CoT-UQ: Improving Response-wise Uncertainty Quantification in LLMs with Chain-of-Thought"
title_zh: "CoT-UQ: 利用思维链改进大语言模型逐响应不确定性量化"
authors: "Boxuan Zhang, Ruqi Zhang"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.findings-acl.1339.pdf"
tags: ["query:luq"]
score: 8.0
evidence: 使用思维链进行逐响应不确定性量化
tldr: 针对现有不确定性量化方法依赖多次采样和过度自信的问题，提出CoT-UQ框架，利用大模型的思维链推理能力进行逐响应不确定性量化，在多个任务上验证了其高效性和准确性。
source: ACL-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1339/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 808, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1339/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1557, \"height\": 1184, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1339/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1601, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1339/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1606, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1339/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1565, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1339/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 795, \"height\": 741, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1339/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 798, \"height\": 726, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1339/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1622, \"height\": 1278, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1339/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 803, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1339/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 775, \"height\": 616, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1339/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 726, \"height\": 749, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1339/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 800, \"height\": 287, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1339/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 794, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1339/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 794, \"height\": 393, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1339/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1615, \"height\": 2111, \"label\": \"Table\"}]"
motivation: 现有大语言模型不确定性量化方法多为提示级别或需多次采样，且模型在推理步骤中表现出过度自信，亟需高效且准确的响应级不确定性量化方法。
method: 提出CoT-UQ框架，将大语言模型的内在推理能力（思维链）整合到不确定性量化流程中，实现逐响应不确定性估计。
result: 实验表明CoT-UQ在多个任务上优于基线方法，降低了过度自信，提高了不确定性估计的可靠性。
conclusion: CoT-UQ有效利用思维链改进了大语言模型的不确定性量化，为可靠决策提供了支持。
---

## Abstract
Large language models (LLMs) excel in many tasks but struggle to accurately quantify uncertainty in their generated responses. This limitation makes it challenging to detect misinformation and ensure reliable decision-making. Existing uncertainty quantification (UQ) methods for LLMs are primarily prompt-wise rather than response-wise, often requiring multiple response samples, which leads to inefficiency. Moreover, LLMs have been shown to be overconfident, particularly when using reasoning steps to derive their answers. In this work, we introduce a novel approach to quantify response-wise uncertainty by integrating LLMs’ inherent reasoning capabilities through Chain-of-Thought (CoT) into the UQ process. Our CoT-UQ framework captures critical information during inference by extracting keywords from each reasoning step and assessing their importance to the final answer. The uncertainty scores of keywords are then aggregated based on their significance to produce a final uncertainty estimate. We conduct extensive experiments based on Llama Family with model sizes varying from 8B to 13B across logical and mathematical reasoning tasks. Experimental results demonstrate that CoT-UQ significantly outperforms existing UQ methods, achieving an average improvement of 5.9% AUROC compared to current UQ methods.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

大型语言模型在各种任务中表现出色，但在生成响应的不确定性量化方面存在明显不足。现有不确定性量化方法主要存在两个问题：一是多为提示级而非响应级量化，通常需要多次采样同一提示的不同响应，计算开销大；二是模型本身存在过度自信，尤其是在使用思维链推理步骤推导答案时，过度自信问题被进一步加剧（例如，模型对自己的错误答案给出很高的置信度）。因此，如何高效且准确地实现响应级不确定性量化，并缓解过度自信，是提升大模型可靠性的关键挑战。

## 2. 方法论：核心思想、关键技术细节、算法流程

### 核心思想
利用大语言模型内在的推理能力（通过CoT获得推理链）来改善不确定性量化。通过提取推理步骤中的关键词并评估其对最终答案的重要性，将这些关键推理信息整合到两种常见的不确定性量化策略（聚合概率和自评估）中，从而得到更校准的置信度估计。

### 关键技术细节

- **Stage 1: 推理信息精炼**
  - **步骤1: 推理提取**：在模型生成响应时，使用CoT前缀（如“Let’s think step by step. Step 1:”）强制模型输出分步推理链和最终答案。
  - **步骤2: 关键词提取**：从每个推理步骤中自动提取关键词（利用LLM自身的信息提取能力）。
  - **步骤3: 重要性评分**：让LLM对每个关键词对最终答案的重要性进行评分（1-10分），形成关键词-重要性二元组集合K。
- **Stage 2: 推理增强的不确定性量化**
  - **对于聚合概率策略**：不直接聚合所有输出token的概率，而是聚合提取的关键词token的概率，并按重要性加权平均。
    - 关键词概率：对关键词中的每个token取概率（使用mean或min聚合），再计算单个关键词概率。
    - 最终置信度：c = Σ(t_ij * p(w_ij)) / Σt_ij。
  - **对于自评估策略**：通过四种方式将推理信息融入自评估提示：
    - ALL Steps：加入完整推理步骤。
    - ALL Keywords：加入所有提取的关键词及其重要性。
    - KEY Step：只加入单步中平均重要性最高的步骤。
    - KEY Keywords：只加入重要性高于阈值τ的关键词。
    - 然后让模型基于增强的提示重新评估答案的正确性，输出置信度（True的概率）。

### 公式与算法流程（文字说明）

- 聚合概率增强：关键词概率聚合公式见式(5)和(6)。
- 自评估增强：使用改进后的提示pr(question, answer, reasoning_info)，然后取P(o=True)作为置信度。

## 3. 实验设计

### 数据集与任务场景
- **逻辑推理**：HotpotQA（8447样本）、2WikiMultiHopQA（1548样本）
- **数学推理**：GSM8K（1319样本）、SVAMP（1000样本）、ASDiv（2249样本）
- 总计约14563个样本。

### Benchmark与对比方法
- **基线方法**：
  - 聚合概率类：Probas-mean、Probas-min、TOKEN SAR（Token-Level Shifting Attention to Relevance）
  - 自评估类：P(True)、Self-Probing
- 对比方式：在同一模型和数据集上，比较基线方法及其加上CoT-UQ后的AUROC性能。

### 模型
- 主要模型：Llama 2-13B、Llama 3.1-8B
- 附加验证：Mistral 7B（附录C.1）

### 评价指标
- 主要指标：AUROC（Area Under the Receiver Operating Characteristic curve）
- 补充指标：AUPRC（附录C.1表4）

## 4. 资源与算力

论文在附录B.3中明确说明：“CoT-UQ takes about 12 seconds per sample and a total of approximately 50 GPU hours to derive all reported results for 14653 samples. All the experiments are conducted on a server with an Intel(R) Xeon(R) Gold 5218R CPU and 8 NVIDIA A6000 GPUs.” 即采用8张NVIDIA A6000 GPU，总耗时约50 GPU小时，平均每样本约12秒。

## 5. 实验数量与充分性

- **数量**：在5个数据集、2个主要模型（Llama 2-13B、Llama 3.1-8B）、1个额外模型（Mistral 7B）上进行了实验。每个基线方法均与CoT-UQ版本对比，覆盖AP和SE两大类策略。
- **消融实验**：
  - 不同CoT-UQ实现（ALL Steps, KEY Step, ALL Keywords, KEY Keywords）在SE策略上的比较（图3、图4）。
  - 重要性评分的影响（图5）。
  - 阈值τ的敏感性分析（图6）。
  - 重要性分数分布可视化（图7）。
  - 案例研究（表7、表8、表9）。
- **客观性与公平性**：实验设计较全面，对比了多个基线，控制变量。但未在所有模型和数据集上报告全部实现组合（如SE策略在逻辑/数学任务使用不同推荐配置），但有合理分析和解释。
- **充分性**：实验较为充分，验证了方法在不同任务、模型、指标下的有效性，消融研究充分。但缺少与采样类方法（如Semantic Entropy）的直接对比，论文中提到采样类方法计算成本高，但未在同一实验设置下比较AUROC。

## 6. 主要结论与发现

- CoT-UQ显著提升了响应级不确定性量化的性能，在所有数据集和模型上平均AUROC提升5.9%。
- 聚合概率策略提升更显著（平均+10.3%在逻辑推理任务），自评估策略在数学推理任务提升更大（+5.3%）。
- 重要性评分对性能有明显贡献，去除重要性评分后AUROC下降。
- 不同推理任务需要不同的CoT-UQ实现：逻辑推理适合关键词级别（KEY Keywords），数学推理适合步骤级别（ALL Steps或KEY Step），因为数学推理中关键词过于简单。
- CoT-UQ能有效缓解过度自信，特别是在错误答案上，通过暴露推理路径中的关键错误来降低置信度。

## 7. 优点

- **响应级UQ**：直接针对单次生成的响应给出置信度，无需多次采样，计算效率更高。
- **利用内在推理能力**：不依赖外部知识或微调，利用大模型自身的CoT能力，易于迁移到新任务和模型。
- **方法灵活性**：能适配聚合概率和自评估两类主流UQ策略，并可集成不同粒度的推理信息（步骤/关键词）。
- **实验验证充分**：在多个数据集、模型、任务上验证，并进行了丰富的消融研究，方法鲁棒。
- **解释性**：通过可视化重要性评分和案例研究，展示模型如何利用推理信息校准置信度。

## 8. 不足与局限

- **需要token logits**：聚合概率策略需要访问模型内部token概率，对于仅提供API的黑盒模型可能受限。虽然自评估策略可绕过，但仍需多次调用模型。
- **仅限于封闭式问答**：实验只覆盖了有明确标准答案的推理问题，未涉及开放式生成任务（如摘要、对话），限制了通用性。
- **依赖LLM自身提取和评分**：关键词提取和重要性评分均由同一个LLM完成，可能存在因果混淆（模型对自己的推理评估可能有偏），且增加了额外计算（每样本约8秒附加时间）。
- **阈值选择依赖任务**：KEY Keywords中的阈值τ需要针对任务调节，虽然实验显示不敏感，但仍需人工设定。
- **未与采样类方法直接比较**：论文指出采样类方法（如Semantic Uncertainty）计算昂贵，但未在相同实验条件下对比AUROC或校准曲线，因此相对性能优势的证据不完全公平。
- **数学推理中关键词信息量不足**：导致关键词级实现效果不如步骤级，说明方法在不同类型推理中的适用性有差异。

（完）
