---
title: Evaluating Uncertainty Quantification Methods in Argumentative Large Language Models
title_zh: 评估论辩型大语言模型中的不确定性量化方法
authors: "Kevin Zhou, Adam Dejl, Gabriel Freedman, Lihu Chen, Antonio Rago, Francesca Toni"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.findings-emnlp.1184.pdf"
tags: ["query:luq"]
score: 8.0
evidence: 评估论辩型大语言模型中的不确定性量化方法
tldr: 针对论辩型大语言模型（ArgLLMs）在声明验证任务中的不确定性量化方法进行系统性评估。现有UQ方法在复杂争议性场景下的有效性缺乏研究。本文通过集成多种UQ方法到ArgLLM框架，提出了一种新颖的评估流程。实验表明不同UQ方法在论辩场景下表现差异显著，为UQ方法的适用性提供了新见解。该工作推动了不确定性量化在可解释决策中的应用。
source: EMNLP-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1184/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 793, \"height\": 659, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1184/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1652, \"height\": 466, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1184/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 667, \"height\": 284, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1184/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1207, \"height\": 563, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1184/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1668, \"height\": 465, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1184/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1208, \"height\": 564, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.1184/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1204, \"height\": 563, \"label\": \"Table\"}]"
motivation: 不确定性量化对保证大语言模型可靠性至关重要，尤其是在涉及争议性陈述的决策场景中。
method: 将多种UQ方法集成到论辩型LLM框架中，通过声明验证任务评估其有效性。
result: 实验揭示了不同UQ方法在论辩场景下的性能差异，提供了评估方法有效性的新途径。
conclusion: 该工作为UQ方法在复杂文本推理中的评估提供了新视角。
---

## Abstract
Research in uncertainty quantification (UQ) for large language models (LLMs) is increasingly important towards guaranteeing the reliability of this groundbreaking technology. We explore the integration of LLM UQ methods in argumentative LLMs (ArgLLMs), an explainable LLM framework for decision-making based on computational argumentation in which UQ plays a critical role. We conduct experiments to evaluate ArgLLMs’ performance on claim verification tasks when using different LLM UQ methods, inherently performing an assessment of the UQ methods’ effectiveness. Moreover, the experimental procedure itself is a novel way of evaluating the effectiveness of UQ methods, especially when intricate and potentially contentious statements are present. Our results demonstrate that, despite its simplicity, direct prompting is an effective UQ strategy in ArgLLMs, outperforming considerably more complex approaches.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLMs）在决策、推理等任务中表现优异，但常生成“幻觉”答案且不提供不确定性指示。用户容易盲目信任LLM的输出，尤其在医疗等高风险领域。因此，不确定性量化（UQ）对于构建可信AI系统至关重要。
- **核心问题**：在论辩型大语言模型（ArgLLMs）中，UQ方法如何影响下游声明验证任务的性能？ArgLLMs是一种基于计算论辩的可解释决策框架，其中UQ直接用于生成支持/攻击论据的置信度分数，进而影响最终预测。现有UQ方法（如直接提示、语义熵、离心率、LUQ等）在论辩场景下的有效性尚未被系统评估。
- **整体含义**：本文不仅评估了不同UQ方法在ArgLLMs中的表现，还提出了一种新颖的UQ方法评估范式——通过将UQ分数集成到ArgLLM的论证结构中，以最终声明验证准确率作为UQ方法有效性的代理指标。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将多种LLM UQ方法集成到ArgLLM框架中，用UQ方法输出的置信度分数作为论据的基础分数（base score），然后通过定量双极论证框架（QBAF）和DF-QuAD语义聚合，计算原始声明的最终置信度，据此做出真/假预测。通过比较不同UQ方法下的验证准确率，评估UQ方法效果。
- **关键技术细节**：
  - **ArgLLM框架**：为每个输入声明生成支持论据（supporting arguments）和攻击论据（attacking arguments），每个论据可进一步递归生成更深层次的子论据（深度D=1或D=2）。每个论据的基分由UQ方法给出。DF-QuAD语义用于计算论点的最终强度，若声明最终得分>0.5则预测为真，否则为假。
  - **UQ方法集成**：
    - **直接提示（Direct Prompting）**：直接让模型输出置信度分数。
    - **语义熵（Semantic Entropy）**：生成M个样本，用NLI模型（DeBERTa-large）进行双向蕴含聚类，计算语义空间的熵。
    - **离心率（Eccentricity）**：生成M个样本，用NLI模型计算蕴含概率作为相似度，构建图拉普拉斯，计算平均距离作为不确定性。
    - **LUQ（长文本不确定性量化）**：生成M个样本，用NLI模型计算“蕴含”与“矛盾”logits，计算相似度后取平均作为不确定性。
  - **归一化**：除直接提示外，其他UQ方法输出原始分数不在[0,1]内，使用20分位箱线性映射到[0,1]。
  - 使用LM-Polygraph库的实现，默认生成样本数M=10。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：
  - TruthfulClaim（改编自TruthfulQA）
  - StrategyClaim（改编自StrategyQA）
  - MedClaim（改编自MedQA）
  - 每个数据集使用500个样本，与Freedman et al. (2025)一致。
- **基准（Baseline）**：直接提示（Direct Prompting）作为基线UQ方法。
- **对比方法**：语义熵、离心率、LUQ（均来自LM-Polygraph实现）。
- **LLM模型**：
  - Gemma-2-9B-it（Google，开源）
  - Llama-3.1-8B（Meta，开源）
  - GPT-4o-mini（OpenAI，闭源）
- **ArgLLM设置**：
  - 声明基础分数：固定为0.5 或 通过提示估计（Est. BS）
  - 论证深度：D=1（仅一层支持/攻击）和 D=2（递归生成子论据）
- **总配置数**：3个数据集 × 3个模型 × 2种基础分数设置 × 2种深度 = 36个配置（但由于GPT-4o-mini不支持语义熵，实际有部分缺失，整体仍覆盖36个实验点）。

## 4. 资源与算力

- **明确说明**：所有实验在配备RTX 4090 24GB GPU的系统上运行，种子设为42以确保可重现。未提及具体GPU数量、训练时长或总计算量。
- 开源模型（gemma-2-9b-it、Llama-3.1-8B）均量化至4位以降低计算成本。GPT-4o-mini为闭源API调用。

## 5. 实验数量与充分性

- **实验数量**：36个不同配置的实验，每个配置运行一次（无多次重复）。每个实验使用500个数据样本，共产生180对置信区间比较（用于统计显著性检验）。
- **充分性评估**：
  - **优点**：覆盖多种数据集、多种模型（含开源与闭源）、多种UQ方法、两种深度和两种基础分数设置，实验设计较为系统。
  - **局限性**：每个配置仅运行一次，未进行多次重复实验（受限于计算成本和时间），可能引入随机波动；统计显著性通过自举检验（5000次重采样）弥补，但多次运行会更稳健。未进行超参数调优（如温度、NLI模型等）。总体而言实验设计较为充分，但可进一步扩展。

## 6. 论文的主要结论与发现

- **直接提示**在所有36个配置中要么是最好的，要么与最好方法无显著差异，且25次位居最佳，远多于其他方法。
- **LUQ**表现次优，10次最佳，尤其在Llama 3.1 + StrategyClaim组合中全面领先。
- **语义熵**虽很少最佳，但往往接近最佳且无显著差异。
- **离心率**表现最差，从未在统计上优于其他方法。
- 直接提示的优越性归因于：(1) 论据生成长且可能具有争议性，采样方法难以捕捉语义一致性；(2) 直接提示不需额外归一化，避免引入噪声；(3) 直接提示资源需求低（无需额外NLI模型与多次采样）。
- 验证了ArgLLMs可作为UQ方法评估的新基准，因其论证结构对UQ分数敏感，且提供真实标签（声明级）用于间接评估。

## 7. 优点：方法或实验设计上的亮点

- **创新性评估范式**：利用ArgLLM的论证框架将UQ分数转化为下游任务性能，提供了一种无需论据级别标签的UQ方法评估方式，具有实际意义。
- **系统覆盖**：涵盖多种UQ方法（简单提示到复杂采样方法）、多种模型（小规模开源与闭源）、多种数据集和参数设置，结果具有较高可信度。
- **统计验证**：使用自举检验计算置信区间，判别方法间差异是否显著，增强了结论的可靠性。
- **实际可用性**：直接提示不仅性能好，且成本低、无需额外模型，便于部署。

## 8. 不足与局限

- **实验重复性不足**：每个配置只运行一次，未进行多轮重复，可能受随机性影响（例如采样生成论据的方差）。作者在局限性中也承认此点。
- **模型规模受限**：受计算资源限制，仅使用9B/8B量级模型，未测试更大模型（如70B+），结论泛化性可能有限。
- **归一化问题**：将其他UQ方法的原始分数通过分位数映射到[0,1]可能引入偏差，影响校准性。未来需更严谨的校准流程。
- **任务局限性**：仅评估二分类声明验证（真/假），未涉及其他任务（如多分类、回归、生成任务）。
- **数据污染风险**：数据集源自流行QA基准，但作者认为ArgLLM改变了任务分布，风险较低。
- **伦理考虑**：恶意用户可能操纵UQ方法输出以达到说服目的，需透明公开UQ方法。

（完）
