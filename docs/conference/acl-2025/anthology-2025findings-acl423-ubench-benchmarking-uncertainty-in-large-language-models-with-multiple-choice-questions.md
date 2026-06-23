---
title: "UBench: Benchmarking Uncertainty in Large Language Models with Multiple Choice Questions"
title_zh: "UBench: 利用选择题对大语言模型不确定性进行基准测试"
authors: "Xunzhi Wang, Zhuowei Zhang, Gaonan Chen, Qiongyu Li, Bitong Luo, Zhixin Han, Haotian Wang, Zhiyu Li, Hang Gao, Mengting Hu"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.findings-acl.423.pdf"
tags: ["query:luq"]
score: 8.0
evidence: 大语言模型不确定性评估基准
tldr: 针对现有LLM不确定性评估需内部模型或额外训练的问题，提出UBench基准，包含11978道选择题，基于置信区间评估不确定性，无需模型内部访问，适用于闭源模型。
source: ACL-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.423/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 717, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.423/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1626, \"height\": 882, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.423/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 795, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.423/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1640, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.423/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1625, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.423/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1611, \"height\": 581, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.423/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1643, \"height\": 494, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 833, \"height\": 210, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1529, \"height\": 1320, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 801, \"height\": 732, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 713, \"height\": 473, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 717, \"height\": 649, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 741, \"height\": 177, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1652, \"height\": 324, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 789, \"height\": 759, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1651, \"height\": 760, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1698, \"height\": 976, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1651, \"height\": 756, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1651, \"height\": 740, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1652, \"height\": 763, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 816, \"height\": 778, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 818, \"height\": 778, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 814, \"height\": 776, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 816, \"height\": 777, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 817, \"height\": 775, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 815, \"height\": 776, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 816, \"height\": 776, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 816, \"height\": 775, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 817, \"height\": 777, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 817, \"height\": 775, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 817, \"height\": 777, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 817, \"height\": 777, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 817, \"height\": 775, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 817, \"height\": 775, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 818, \"height\": 778, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 816, \"height\": 775, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 817, \"height\": 777, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 819, \"height\": 774, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 819, \"height\": 776, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.423/table-033.webp\", \"caption\": \"\", \"page\": 0, \"index\": 33, \"width\": 817, \"height\": 777, \"label\": \"Table\"}]"
motivation: 当前大语言模型不确定性评估面临需要模型内部访问、额外训练或高计算成本等问题，亟需一种无需内部访问的通用评估基准。
method: 提出UBench基准，包含11978道覆盖多种能力的多项选择题，基于置信区间度量模型不确定性。
result: 实验对比了多种模型的不确定性，展示了该基准的有效性和实用性。
conclusion: UBench为评估大语言模型不确定性提供了高效且模型无关的基准，促进了可靠性研究。
---

## Abstract
Despite recent progress in systematic evaluation frameworks, benchmarking the uncertainty of large language models (LLMs) remains a highly challenging task. Existing methods for benchmarking the uncertainty of LLMs face three key challenges: the need for internal model access, additional training, or high computational costs. This is particularly unfavorable for closed-source models. To this end, we introduce UBench, a new benchmark for evaluating the uncertainty of LLMs. Unlike other benchmarks, UBench is based on confidence intervals. It encompasses 11,978 multiple-choice questions spanning knowledge, language, understanding, and reasoning capabilities. Based on this, we conduct extensive experiments. This includes comparisons with other advanced uncertainty estimation methods, the assessment of the uncertainty of 20 LLMs, and an exploration of the effects of Chain-of-Thought (CoT) prompts, role-playing (RP) prompts, and temperature on model uncertainty. Our analysis reveals several crucial insights: 1) Our confidence interval-based methods are highly effective for uncertainty quantification; 2) Regarding uncertainty, outstanding open-source models show competitive performance versus closed-source models; 3) CoT and RP prompts present potential ways to improve model reliability, while the influence of temperature changes follows no universal rule. Our implementation is available at https://github.com/Cyno2232/UBENCH.

---

## 论文详细总结（自动生成）

### 论文的中文总结

#### 1. 核心问题与研究动机
大语言模型（LLM）在广泛部署中常生成错误或误导性信息，而用户无法获知其置信度。现有不确定性评估方法存在三大局限：
- **需要模型内部访问**（如 logits 或隐藏层），对闭源模型不可用；
- **需要额外训练或微调**，计算成本高，不适用于 API 模型；
- **需要多次采样**，资源消耗大且效率低。

因此，亟需一种**无需内部访问、无需训练、仅需单次推理**的不确定性评估基准。

#### 2. 方法论：UBench 基准
**核心思想**：将不确定性量化转化为**多项选择题**，通过让模型从十个置信区间（0-10%, 10-20%, …, 90-100%）中选择一个来表征其置信度，从而避免传统逐字或概率输出的不稳定性。

- **数据构建**：从24个公开数据集中随机采样（每数据集500条），覆盖**语言、知识、理解、推理**四类能力。每个样本包含**正样本**（正确答案）和**负样本**（错误答案，由GPT-4生成并人工校验）。
- **提示设计**：采用零样本提示，包含角色扮演（RP）、任务说明、思维链（CoT）引导、输出格式约束及十个选项。模型只需输出字母选项（A-J）。
- **置信度映射**：将选项映射为区间中点（如A→5%, J→95%），并计算四个校准指标：**ECE（期望校准误差）、MCE（最大校准误差）、ACE（平均校准误差）、TACE（阈值平均校准误差，阈值0.5）**，值越低表示不确定性估计越好。

**关键优势**：单次推理、无需内部参数、无需训练，适用于开源与闭源模型。

#### 3. 实验设计
- **数据集**：UBench 包含 **11,978 道选择题**，来自24个公开数据集（如WiC、WSC、COLA、CommonSenseQA、TruthfulQA、GSM8K、PIQA等），分为语言、知识、理解、推理四大类。
- **Benchmark**：自身作为基准，与四种不确定性估计方法对比：**Ye et al. (2024)**（logits-based）、**Xiong et al. (2023)**（verbalized+consistency）、**Temperature Scaling (Guo et al., 2017)**、**Monte-Carlo Dropout (Gal & Ghahramani, 2016)**。
- **评估模型**：测试 **20个主流LLM**，包括闭源（GPT-4o, GPT-4, Qwen-max, GLM4-flash, ErnieBot）和开源（Llama-3, Qwen2.5, Yi-1.5, InternLM2.5, DeepSeek V2.5, Mistral, ChatGLM等），覆盖不同参数规模（6B~70B+）。

#### 4. 资源与算力
论文**未明确说明**使用的GPU型号、数量及训练时长。所有模型均为**预训练后直接推理**，无需额外训练。仅对闭源模型通过API调用（如OpenAI、SiliconCloud），开源模型在本地推理（具体硬件未提及）。实验温度默认0.001，重复采样3次进行统计比较。

#### 5. 实验数量与充分性
- **主要对比实验**：在Cosmos QA和SWAG两个子集上，随机采样3次（每轮100条数据），共进行 **3×2=6组** 实验，每个方法获得均值和标准差，并做t检验（p<0.05）。
- **全面评估实验**：在全部11,978条数据上评估20个模型，输出四个指标及平均分，并报告在**四个子集**上的详细结果。
- **消融实验**：
  - 不同置信区间数量（5、10、20）在SWAG上的性能对比。
  - 去除CoT、RP或两者同时去除的Prompt消融（GPT-4, GLM4-flash, GLM4）。
  - 温度参数从0到2.0（或1.0）的8~12档调参实验。
- **案例分析**：呈现Mistral-7B在UBench与Xiong方法上的对比响应。
这些实验覆盖了方法对比、模型规模效应、Prompt影响、温度影响、区间粒度等方面，设计较为全面，但未在全部数据集上重复多次采样（仅Cosmos QA和SWAG做了3次重复）。

#### 6. 主要结论
- **置信区间方法效果最优**：在大多数设置下，UBench的ECE/MCE/ACE/TACE优于其他四类方法，77%的指标差异显著（p<0.05）。
- **开源与闭源模型可靠性相当**：TOP3闭源与TOP3开源的平均得分仅差1%；Yi-1.5-34B和DeepSeek V2.5表现优异，接近GPT-4o。
- **模型规模与可靠性的关系不确定**：Llama3.1和InternLM2.5系列中，更大规模反而使不确定性增加；但Qwen2.5系列中，72B优于7B。
- **CoT和RP提示可提升可靠性**：移除CoT或RP均导致性能下降，同时移除二者负面影响最大；GPT-4对CoT不敏感，但GLM系列受益明显。
- **温度影响因模型而异**：GPT-4可靠性随温度升高而下降；GLM4-flash和GLM4则随温度升高而提升（因增加了推理过程）。
- **10个区间最优**：对比5个、20个区间，10区间在ECE、MCE等指标上综合最佳。

#### 7. 优点
- **无需模型内部访问**，闭源模型也可直接使用，实用性强。
- **单次推理**，效率高，成本低。
- **无需额外训练**，可快速部署于任何LLM。
- **基于选择题的置信区间映射**，避免了对数值输出的不稳定解析。
- **多维度、多任务**，覆盖语言、知识、理解、推理，泛化性好。
- **提供自动化的评估框架**，包含数据构建、质量控制、指标计算全流程。
- 严格的数据质量审查（双审+仲裁），保证样本有效性。

#### 8. 不足与局限
- **能力覆盖不全**：仅评估了语言、知识、理解、推理四类，未涵盖多模态、代码生成、长文本生成等场景。
- **基于选择题的固有偏差**：可能受到选项位置偏见（position bias）影响，且要求模型严格遵循指令。
- **实验中重复次数有限**：仅对两个子集做了3次重复，整体性能报告基于单次全量测试，统计稳定性可能不足。
- **未公布具体算力消耗**，难以复现资源需求。
- **未探索其他影响可靠性的因素**，如模型微调、量化、推理策略等。
- **对GPT-4等模型仅使用随机子集测试**（1/3或1/5数据），降低了结果的可比性。

（完）
