---
title: "When Models Lie, We Learn: Multilingual Span-Level Hallucination Detection with PsiloQA"
title_zh: 当模型说谎时我们学习：使用PsiloQA进行多语言跨度级幻觉检测
authors: "Elisei Rykov, Kseniia Petrushina, Maksim Savkin, Valerii Olisov, Artem Vazhentsev, Kseniia Titova, Alexander Panchenko, Vasily Konovalov, Julia Belikova"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.findings-emnlp.626.pdf"
tags: ["query:luq"]
score: 4.0
evidence: 多语言跨度级幻觉数据集，用于LLM不确定性评估
tldr: 现有幻觉检测基准多为英文且序列级标记，缺乏细粒度多语言监督。本文构建PsiloQA——覆盖14语言的大规模跨度级幻觉标注数据集，通过自动化三阶段流水线生成QA对并标注幻觉。该数据集支持精细的幻觉检测评估，为不确定性量化和安全部署提供基础资源。
source: EMNLP-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.626/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1651, \"height\": 430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.626/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1617, \"height\": 868, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.626/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 730, \"height\": 652, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.626/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 751, \"height\": 723, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.626/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 732, \"height\": 706, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.626/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 723, \"height\": 703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.626/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1476, \"height\": 783, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.626/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1652, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.626/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1648, \"height\": 606, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.626/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 797, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.626/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1646, \"height\": 451, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.626/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 390, \"height\": 248, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.626/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1663, \"height\": 964, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.626/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1651, \"height\": 1904, \"label\": \"Table\"}]"
motivation: 构建多语言跨度级的幻觉检测数据集以支持更细致的评估。
method: 自动化三阶段流水线：生成QA对、诱导幻觉回答、标注跨度。
result: 数据集质量高，支持14语言跨度级标注。
conclusion: 为多语言幻觉检测和不确定性研究提供了重要基准。
---

## Abstract
Hallucination detection remains a fundamental challenge for the safe and reliable deployment of large language models (LLMs), especially in applications requiring factual accuracy. Existing hallucination benchmarks often operate at the sequence level and are limited to English, lacking the fine-grained, multilingual supervision needed for comprehensive evaluation. In this work, we introduce PsiloQA, a large-scale, multilingual dataset annotated with span-level hallucinations across 14 languages. PsiloQA is constructed through an automated three-stage pipeline: generating question–answer pairs from Wikipedia using GPT-4o, eliciting potentially hallucinated answers from diverse LLMs in a no-context setting, and automatically annotating hallucinated spans using GPT-4o by comparing against golden answers and retrieved context. We evaluate a wide range of hallucination detection methods-including uncertainty quantification, LLM-based tagging, and fine-tuned encoder models-and show that encoder-based models achieve the strongest performance across languages. Furthermore, PsiloQA demonstrates effective cross-lingual generalization and supports robust knowledge transfer to other benchmarks, all while being significantly more cost-efficient than human-annotated datasets. Our dataset and results advance the development of scalable, fine-grained hallucination detection in multilingual settings.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大型语言模型（LLM）在生成文本时极易产生幻觉（hallucination），即在答中引入与事实不一致的内容。现有的幻觉检测基准大多仅在**序列级**（判断整个生成是否正确）且局限于**英文**，缺乏**细粒度**（跨度级）和**多语言**的监督资源，难以支持全面评估和实际部署（尤其医疗等安全关键领域）。
- **意义**：构建一个大规模、多语言、跨度级标注的幻觉检测数据集，为细粒度检测方法提供训练和评测基础，推动多语言环境下LLM安全可靠性的研究。

## 2. 方法论：核心思想与关键技术细节

### 2.1 总体思路
采用**自动三阶段流水线**，利用维基百科作为可靠事实源，生成包含真实幻觉（LLM在无上下文情况下回答时自然产生）的问答对，并由GPT-4o自动标注不一致的跨度。

### 2.2 关键技术步骤

1. **QA对生成**：从维基百科随机抽取段落，使用GPT-4o生成难、中、易三种复杂度的问答对（每段落3对），答案作为“黄金答案”。
2. **幻觉回答生成（Hypothesis Generation）**：将问题（**不提供上下文**）提供给多种开源和商用LLM，使其仅凭内部知识回答。由于缺少检索支持，LLM容易产生事实错误，从而**自然生成包含真实幻觉的答案**。
3. **跨度级不一致检测（Inconsistency Detection）**：将问题、黄金答案、检索到的段落以及LLM的答案一同送入GPT-4o，要求其标记与黄金答案或段落矛盾的文本跨度，使用 `<[HAL]>...<[/HAL]>` 标签标注。鼓励精确到词级，避免整体标注。
4. **自动过滤**：规则过滤（标签匹配错误、空标注、标注后答案不一致等）和基于模型的过滤（剔除主观问题、不完整问题、LLM拒绝回答的样本），共约6,500个样本被过滤。

### 2.3 最终数据集
- 训练集：63,792个样本
- 测试集：2,897个样本（每语言与每种LLM组合随机抽取100个）
- 覆盖14种语言：英、中、德、法、西、意、阿、印地、芬兰、加泰、巴斯克、捷克、波斯、瑞典

## 3. 实验设计

### 3.1 使用数据集 / 场景
- **主数据集**：PsiloQA（本文创建）
- **其他评估基准**：Mu-SHROOM（14语言）、FAVA-Bench（英文）、HalluEntity（英文）、RAGTruth QA（英文）

### 3.2 对比方法

| 方法类别 | 具体方法 |
|----------|----------|
| 不确定性量化（UQ） | MSP（最大词概率）、CCP（声明条件概率）、Focus（加权不确定性） |
| 编码器模型（微调） | LettuceDetect-base（基于ModernBERT，预训练于RAGTruth）、ModernBERT-base（在PsiloQA上微调）、mmBERT-base（现代多语言编码器，全文微调） |
| 大语言模型（LLM） | FActScore（GPT-4o分解并验证原子事实）、Qwen2.5-32B-Instruct（3-shot提示） |

### 3.3 评估指标
- **IoU（交并比）**：评估跨度级检测的精确度
- **AP（平均精度）**：基于字符级排序的阈值无关评估，处理类别不平衡

### 3.4 对比公平性
- 所有编码器模型使用相同超参数（学习率1e-5, 6 epoch, weight decay 0.01, batch_size 8）
- UQ方法通过语言特定阈值校准
- 提示模板和few-shot例子统一

## 4. 资源与算力

- **GPU**：2块NVIDIA A100（80GB），总计约**50 GPU小时**
- **数据集生成成本**：GPT-4o标注花费约$535，对比RAGTruth人工标注估计约$3,000，成本低约17倍
- **软件**：VLLM用于LLM推理，Transformers库用于编码器训练

## 5. 实验数量与充分性

### 5.1 主要实验组
1. **表2**：在PsiloQA测试集上对14种语言评估所有方法（共约14×7=98条结果），显示完整性能对比。
2. **表3**：跨语言迁移实验——比较mmBERT-base的两种训练策略（单语言 vs 多语言联合训练），并在PsiloQA和Mu-SHROOM测试集上评估。
3. **表4**：知识迁移实验——在RAGTruth QA、PsiloQA_en、两者联合上训练mmBERT，然后在FAVA-Bench、HalluEntity、Mu-SHROOM_en上测试。
4. **人工验证**：100个英文样本由3位标注者验证，计算GPT-4o与人工一致性（AP 84.3%，IoU 71.0%）。
5. **数据集统计分析**：样本分布、跨度数量、跨度长度、领域分布等。

### 5.2 充分性判断
- 实验涵盖多种类型的方法（UQ、编码器、LLM），覆盖14种语言，并在4个外部基准上评估，范围较广。
- 消融实验体现了多语言联合训练、不同数据集训练策略的影响。
- 人工验证提供了标注质量证据。
- **公平性**：超参数统一，UQ阈值按语言校准。但编码器模型在全数据集微调，LLM为few-shot，复杂度有差异，比较基本合理。

## 6. 主要结论与发现

1. **编码器模型表现最佳**：微调后的多语言编码器（mmBERT-base）在14种语言中几乎全面优于UQ和LLM方法，AP均值达73.8%，IoU达64.2%。
2. **跨语言泛化有效**：在PsiloQA完整多语言数据上训练的模型显著优于单语言模型，在Mu-SHROOM等外部基准上也表现良好。
3. **PsiloQA优于人工标注数据集**：仅用PsiloQA_en训练的模型在多个基准上的知识迁移结果超过使用RAGTruth训练的模型，且成本低17倍。
4. **跨度边界检测仍是挑战**：所有方法的AP与IoU之间存在显著差距（如mmBERT AP 84.88% vs IoU 70.67%），说明精确切分幻觉区域仍需改进。
5. **UQ方法表现有限**：Focus稍好，但IoU普遍低于35%，不适合实际细粒度检测。

## 7. 优点

- **自动化流水线可扩展且经济**：无需人工标注，成本仅为RAGTruth的1/17，且可快速扩展到更多语言和LLM。
- **使用真实LLM幻觉**：不同于人工插入错误的合成数据集，PsiloQA中的幻觉是LLM在无上下文回答时的自然错误，更贴近实际。
- **多语言与细粒度**：跨度级标注支持定位具体错误单词，14种语言覆盖广泛。
- **人工验证确认标注质量**：GPT-4o标注与多个人工标注者有较高一致性（AP 84.3%, IoU 71.0%）。
- **开源与可复现**：数据集、代码、提示均公开，促进后续研究。

## 8. 不足与局限

- **标注来源偏差**：仅依赖GPT-4o一个模型进行生成和标注，可能引入模型偏好。建议未来使用模型集成。
- **任务狭窄**：仅面向问答任务，未涵盖摘要、对话、数据到文本等其他易产生幻觉的生成任务。
- **幻觉类型覆盖不全**：只包含由缺乏上下文导致的自然幻觉，缺乏如事实扭曲、实体替换等多样化类型（如FAVA显式分类）。
- **语言资源不均衡**：英语样本显著多于德语（约1,500）、阿拉伯语等，低资源语言可能标注质量或覆盖不足。
- **依赖维基百科**：局限为百科风格事实，缺乏领域（如医学、法律）和语体多样性，可能引入文化和地域偏差。
- **实验范围局限**：仅测试了有限数量的LLM（约24个），且未评估模型在真实部署场景（如RAG系统、对话）中的表现。未探讨针对不同难度问题的检测性能差异。

（完）
