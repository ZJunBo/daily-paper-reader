---
title: "Do not Abstain! Identify and Solve the Uncertainty"
title_zh: 不要放弃！识别并解决不确定性
authors: "Jingyu Liu, JingquanPeng JingquanPeng, Xiaopeng Wu, Xubin Li, Tiezheng Ge, Bo Zheng, Yong Liu"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.acl-long.840.pdf"
tags: ["query:luq"]
score: 7.0
evidence: 大语言模型不确定性的识别与解决基准
tldr: LLM面对不确定场景常过度自信且仅回避。本文提出ConfuseBench基准，聚焦文献稀缺、能力不足和查询模糊三类不确定性，实验发现当前LLM难以准确识别不确定性的根源并解决，倾向于错误归因。该基准为改进LLM主动解决不确定性提供了方向。
source: ACL-2025-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.840/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 732, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.840/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 711, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.840/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 731, \"height\": 589, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.840/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 797, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.840/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 686, \"height\": 512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.840/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1545, \"height\": 757, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.840/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 805, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.840/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 797, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.840/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 804, \"height\": 532, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.840/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1589, \"height\": 727, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.840/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1439, \"height\": 436, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.840/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1626, \"height\": 1111, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.840/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1620, \"height\": 1103, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.840/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1620, \"height\": 1101, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.840/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1203, \"height\": 215, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.840/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1673, \"height\": 770, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.840/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1435, \"height\": 432, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.840/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1616, \"height\": 1109, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.840/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1615, \"height\": 1099, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.840/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1615, \"height\": 1109, \"label\": \"Table\"}]"
motivation: LLM面对不确定时仅回避而非识别并解决。
method: 构建ConfuseBench基准，包含三类不确定性，评估LLM识别和解决能力。
result: LLM在识别和解决不确定性根源上表现不佳。
conclusion: 需要提升LLM主动解决不确定性的能力。
---

## Abstract
Despite the widespread application of Large Language Models (LLMs) across various domains, they frequently exhibit overconfidence when encountering uncertain scenarios, yet existing solutions primarily rely on evasive responses (e.g., “I don’t know”) overlooks the opportunity of identifying and addressing the uncertainty to generate more satisfactory responses. To systematically investigate and improve LLMs’ ability of recognizing and addressing the source of uncertainty, we introduce ConfuseBench, a benchmark mainly focus on three types of uncertainty: document scarcity, limited capability, and query ambiguity. Experiments with ConfuseBench reveal that current LLMs struggle to accurately identify the root cause of uncertainty and solve it. They prefer to attribute uncertainty to query ambiguity while overlooking capability limitations, especially for those weaker models. To tackle this challenge, we first generate context-aware inquiries that highlight the confusing aspect of the original query. Then we judge the source of uncertainty based on the uniqueness of the inquiry’s answer. Further we use an on-policy training method, InteractDPO to generate better inquiries. Experimental results demonstrate the efficacy of our approach.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）在面对不确定场景时往往表现出过度自信，现有解决方案（如直接回答“我不知道”）只是回避问题，未能识别并解决不确定性的根源，从而错失生成更满意回答的机会。
- **研究目标**：系统性地评估并提升LLM识别和解决不确定性根源的能力，而非仅仅规避回答。
- **背景**：实际应用中，不确定性可能来源于多种原因，包括缺乏相关文档（文档稀缺）、模型自身推理能力不足（能力受限）、以及用户查询本身模糊不清（查询模糊）。现有工作要么只关注单一不确定性类型，要么仅讨论拒绝回答，缺乏综合评估与解决方案。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：不直接判断不确定性的来源，而是先让模型生成一个能够揭示原始查询中模糊环节的上下文感知询问（inquiry），然后基于该询问的答案的唯一性来判断不确定性类型：如果答案唯一且客观，则需要检索（文档稀缺）；如果答案不唯一，则需要用户澄清（查询模糊）；如果询问本身逻辑不通或只是重复原问题，则表明模型能力不足，需要链式推理（CoT）。
- **关键技术细节**：
  - **判断机制**：采用定理5.2证明询问的不确定性与原始查询的不确定性正相关，因此可通过分析询问的答案来推断原始不确定性的来源。
  - **三重判断**：
    1. 若询问的答案与原始查询语义连贯且能直接回答原始问题，则判定为能力不足，启用CoT。
    2. 若询问的答案是客观事实（唯一答案），则判定为文档稀缺，进行检索增强。
    3. 若询问的答案有多种可能（主观或模糊），则判定为查询模糊，向用户提出澄清问题。
  - **InteractDPO**：一种在线策略偏好优化方法。在训练过程中，模型生成询问后与真实检索系统或用户（GPT-4o模拟）交互，根据交互结果（能否正确回答原问题）判断询问好坏，实时构造“选择-拒绝”样本对进行DPO训练，避免离线数据集带来的分布不匹配。
- **公式/算法流程**：
  - 步骤1：基于原始查询和文档，生成上下文感知询问。
  - 步骤2：根据询问的答案的唯一性，分类不确定性来源（文档/能力/模糊）。
  - 步骤3：若分类一致则采纳，若两次抽样不一致则使用基于答案的判断。
  - 训练流程：利用InteractDPO迭代优化询问生成能力。

### 3. 实验设计：使用的数据集、场景、基准（benchmark）以及对比方法

- **数据集与场景**：
  - 基础问答：HotpotQA、AmbigQA（包含模糊查询）
  - 助手场景：ExpertQA、TechQA
  - 工具使用：ToolBench
- **基准（ConfuseBench）**：从上述数据集中构建650个测试案例，涵盖三类不确定性（文档稀缺、能力不足、查询模糊）。对每个数据集分别选取50个文档稀缺和查询模糊案例、30个能力不足案例。
- **对比方法**：
  - 基线模型：GPT-4o、DeepSeek-V3、Qwen2.5-72B-Instruct、Meta-Llama-3-70B-Instruct、Qwen2.5-7B-Instruct、Mistral-7B-Instruct-v0.2
  - 消融方法：直接提示（prompt-based）、基于询问判断（inquiry-based）、基于询问答案判断（answer-based）
  - 训练对比：SFT、DPO、OnlineDPO、InteractDPO（以Qwen2.5-7B为基座）

### 4. 资源与算力

- **文中提及**：训练时使用LoRA，rank=64，targets包括q_proj, k_proj, v_proj, o_proj和ffn；学习率范围{3e-06, 1e-05, 3e-05}；训练5个epoch；使用bf16精度；cutoff length=32k。
- **未明确说明**：没有提及使用的具体GPU型号、数量以及总训练时长或总计算开销。因此无法评估实验的可复现成本。

### 5. 实验数量与充分性

- **实验数量**：
  - 主实验：6个模型在5个数据集上的性能对比，包括答案质量（AQ）、不确定性分类准确率（UCA）、询问质量（IQ）。
  - 额外分析：分类精度/召回率、F1分数；询问质量的误差来源分析。
  - 消融实验：对比直接提示、询问、询问答案三种判断方式。
  - 训练实验：对比SFT、DPO、OnlineDPO、InteractDPO在UCA和AQ上的表现。
  - Few-shot分析：补充了带示例的提示实验。
  - 可靠性验证：使用Omega可靠性系数和ICC评估judge一致性。
- **充分性与公平性**：
  - 覆盖多种模型规模（7B到旗舰级）和多个数据集，实验较全面。
  - 采用多次抽样和多数投票，减少单次随机性。
  - 使用GPT-4o模拟用户和判断，但未讨论judge自身偏差（论文附录D报告了可靠性，但未完全消除）。
  - 未进行跨领域或未见来源的不确定性测试，实验环境较封闭。

### 6. 论文的主要结论与发现

- 当前LLM（包括GPT-4o）在识别不确定性根源上表现不佳，最佳模型UCA仅约55%。
- 模型倾向于将不确定性归因于查询模糊（高召回率），很少归因为自身能力不足（低召回率），尤其是弱模型（如Llama-3-70B对能力不足的召回率仅0.02）。
- 基于询问答案的判断方法（answer-based）显著提升了分类准确率（平均提升10%+），优于直接提示和仅询问判断。
- InteractDPO通过在线交互获得真实反馈，相比SFT、DPO、OnlineDPO进一步提升了询问质量和最终答案质量，且无需额外标注。

### 7. 优点

- **新颖的基准**：ConfuseBench首次系统评估LLM识别和解决多种不确定性根源的能力，超越了仅检测“是否知道”的范式。
- **方法创新**：提出基于询问答案唯一性的判断策略，无需外部模型或知识库，计算成本低且通用。
- **在线训练方法**：InteractDPO利用真实交互反馈进行偏好优化，避免了离线数据与当前模型分布不匹配的问题，是强化学习在不确定性处理中的有效应用。
- **实验设计严谨**：多维度评估（准确性、分类、询问质量），消融充分，并验证了judge的可靠性。

### 8. 不足与局限

- **不确定性类型覆盖不全**：仅考虑了三种常见类型（文档、能力、模糊），实际场景中还有事实错误、非法时间、违反约束等情况，每种类型对应不同解决方案（如Tree of Thought、MCTS）。
- **方法应用限制**：假设模型能生成有意义的询问，若模型本身询问能力太弱（如小模型），则基于答案的判断可能失效。
- **实验局限**：未覆盖所有主流LLM（如Claude、Gemini）；训练仅基于Qwen2.5-7B，未验证其他规模或架构的泛化能力。
- **评估偏差**：使用GPT-4o作为用户模拟和答案质量judge，其自身也可能存在偏见或能力边界，可能影响结论的客观性。
- **计算资源未透明**：未公开训练所需的GPU型号、数量和时长，不利于复现和实际部署评估。

（完）
