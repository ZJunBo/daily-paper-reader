---
title: "Safety Pretraining: Toward the Next Generation of Safe AI"
title_zh: 安全预训练：迈向下一代安全人工智能
authors: "Pratyush Maini, Sachin Goyal, Dylan Sam, Alexander Robey, Yash Savani, Yiding Jiang, Andy Zou, Matt Fredrikson, Zachary Chase Lipton, J Zico Kolter"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=91H9CSvdwl"
tags: ["query:dg"]
score: 8.0
evidence: 合成安全数据用于预训练
tldr: 后训练对齐方法往往脆弱，因为预训练阶段已学习到不安全模式。本文提出安全预训练框架，包括安全过滤、安全重述和原生拒绝数据合成，在预训练阶段即构建安全能力。实验表明，该方法显著降低了有害输出，且不牺牲通用能力。该工作将安全提升到预训练层面，为构建更安全AI提供了新范式。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-91h9csvdwl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1153, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-91h9csvdwl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1402, \"height\": 557, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-91h9csvdwl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 550, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-91h9csvdwl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 822, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-91h9csvdwl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1072, \"height\": 536, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-91h9csvdwl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1411, \"height\": 662, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-91h9csvdwl/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1365, \"height\": 1158, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-91h9csvdwl/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1433, \"height\": 468, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-91h9csvdwl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 269, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-91h9csvdwl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1254, \"height\": 287, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-91h9csvdwl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1440, \"height\": 534, \"label\": \"Table\"}]"
motivation: 后训练对齐难以根除预训练中习得的不安全模式，需要从源头嵌入安全。
method: 构建安全分类器过滤网页数据，重述不安全内容，并合成拒绝回答的预训练数据。
result: 安全预训练模型在无毒性和能力基准上均优于仅后对齐的模型。
conclusion: 预训练阶段注入安全数据是提升模型固有安全性的有效途径。
---

## Abstract
As large language models (LLMs) are increasingly deployed in high-stakes settings, the risk of generating harmful or toxic content remains a central challenge. Post-hoc alignment methods are brittle: once unsafe patterns are learned during pretraining, they are hard to remove.
In this work, we present a data-centric pretraining framework that builds safety into the model from the start. Our framework consists of four key steps:
(i) Safety Filtering: building a safety classifier to classify webdata into safe and unsafe categories;
(ii) Safety Rephrasing: we recontextualize unsafe webdata into safer narratives;
(iii) Native Refusal: we synthetically generate pretraining datasets that actively teach models to refuse on unsafe content and the moral reasoning behind it, and
(iv) Harmfulness-Tag annotated pretraining: we flag unsafe content during pretraining using a special token, and use it to steer models away from unsafe generations at inference-time.
Our safety-pretrained models reduce attack success rates from 38.8% to 8.4% on standard LLM safety benchmarks with no performance degradation on general tasks.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLMs）在部署至高风险场景时，存在生成有害、有毒内容的风险。传统的后训练对齐方法（如 RLHF、DPO）本质上是脆弱的——一旦不安全模式在预训练阶段被模型学习，就很难通过后续的对齐手段彻底移除。对齐不等于遗忘（alignment is not unlearning）。
- **整体含义**：该论文提出将安全嵌入到预训练阶段，从源头构建“原生安全”的模型，而不是依赖后训练修补。这种数据中心的预训练框架致力于在模型学习语言能力的同时，使其内化道德准则和拒绝有害请求的能力。

## 2. 论文提出的方法论

- **核心思想**：通过四个关键步骤的数据干预与训练技术，使模型从预训练开始就具备安全意识和拒绝能力。
- **关键技术细节**：
  - **安全评分（Safety Scoring）**：构建一个细粒度的安全分类器（分数 0-5）。使用 GPT-4o-mini 对 10K 样本进行标注作为训练数据，并基于标注微调轻量级 embedding 分类器（gte-base-en-v1.5），同时结合 Qwen 2.5-7B 的 LLM 分类器进行集成，取最大分数以提高对不安全内容的召回。
  - **安全重述（Safety Rephrasing）**：对不安全的数据不直接删除，而是使用 LLaMA-3.1-8B 生成安全的重述版本，保留原有信息但加入伦理语境和历史解释。生成的 SafeWeb 数据集包含超过 100B token 的合成数据。
  - **原生拒绝训练（Native Refusal Training）**：基于安全分数 4 和 5 的高危数据，合成用户-助手对话格式的 RefuseWeb 数据集，教导模型礼貌但坚定地拒绝有害请求，并解释拒绝理由。
  - **有害标签预训练与 SafeBeam 解码（Harmfulness-Tag Annotated Pretraining + SafeBeam）**：在预训练中随机选择不安全文本的 5% token 前插入特殊标记 `<potentially unsafe content>`，迫使模型学习该标记与不安全内容之间的关联。推理时使用 SafeBeam 算法：在 beam search 中通过一步前瞻计算产生该标记的概率，丢弃概率最高的 50% beam，从而引导模型远离不安全生成路径。
- **算法流程（文字说明）**：
  - 安全标签注入算法：对每个不安全文本序列，以概率 p（实验中 p=5%）随机在 token 前插入有害标签。
  - SafeBeam 算法：在每一步解码时，对当前 beam 集合中的每个候选计算下一步产生有害标签的概率，丢弃概率最高的 50% beam，然后从剩余候选中选择 top-k 个保持高对数似然的 beam。

## 3. 实验设计

- **数据集/场景**：
  - 预训练基础数据：FineWeb-Edu、StackOverflow、FineMath、Cosmopedia（SmolLM2 设置）。
  - 合成安全数据：SafeWeb（重述数据）、RefuseWeb（拒绝对话）、Moral Education（道德教育段落）。
  - 指令微调数据：Ultrachat-200k、WildGuardMix、WildJailbreak。
  - 安全评估数据集：HarmBench、TDC、JailbreakBench、AdvBench。
  - 通用能力评估：ARC-Challenge、ARC-Easy、Commonsense QA、GSM8K、OpenBookQA、PIQA、TriviaQA、Winogrande、MMLU。
  - 帮助力/过度拒绝评估：Alpaca 数据集（300 个良性请求），使用 GPT-4o-mini 判断。
- **Benchmark**：
  - 安全指标：Attack Success Rate (ASR)。
  - 通用性能：各项准确率。
  - 对抗攻击：GCG 攻击（JailbreakBench）。
  - 良性微调鲁棒性：在 GSM8K 上微调后评估 ASR。
- **对比方法**：
  - 标准预训练（Raw Data）。
  - 仅安全分数为 0 的数据训练（Score 0 Only）。
  - 逐步添加重述数据、拒绝数据、道德教育数据。
  - 仅使用有害标签预训练（不加重述） + SafeBeam。
  - 在指令微调阶段才进行有害标签注明的对比。

## 4. 资源与算力

- 论文附录 H 明确说明：为训练一个 1.7B 参数的模型，使用 **4 节点 × 8 张 H100 GPU**（共 32 张 H100），训练约 **6-7 天**，处理约 600B token。
- 所有实验均采用此配置，模型规模相同（1.7B），未在更大规模上验证。

## 5. 实验数量与充分性

- **实验组数**：
  - 主要对比了 5 种数据干预配置（原始数据、仅 Score 0、+重述、+拒绝+道德教育、+SafeBeam），并在多种评估设置（基座模型、指令微调后、良性微调后）下报告 ASR。
  - 消融研究包括：逐步添加各干预、有害标签注入比例（3%，5%，10%）、仅标签预训练 vs 完整方案、不同分类器对比（9 种）、不同 embedding 模型对比等。
  - 对抗攻击实验：GCG 攻击。
  - 帮助力评估：Alpaca 分类计数。
- **充分性评估**：
  - **优点**：消融实验系统全面，覆盖了每个主要组件（过滤、重述、拒绝、道德教育、标签训练、解码）。对比标准预训练和纯后训练对齐，明确展示了安全预训练在鲁棒性上的优势。评估维度涵盖安全性、通用能力、帮助力、对抗攻击和良性微调。
  - **不足**：所有实验仅在 1.7B 参数模型上进行，未在不同规模（如 7B、13B）上验证，通用性存疑。每个配置只进行了一次训练（单次运行），未提供误差棒或显著性检验，可能受随机性影响。

## 6. 论文的主要结论与发现

- 安全预训练显著降低攻击成功率：从前三阶段（基座模型、指令微调后、良性微调后）来看，ASR 从标准预训练的 38.8% 降至安全预训练的 8.3%（附 SafeBeam 后）。
- 仅进行安全过滤（只使用分数 0 的数据）反而导致 ASR 上升（43.8%），说明完全删除不安全数据会使模型缺乏应对能力。
- 重述数据和拒绝数据是关键贡献：逐步加入后 ASR 从 38.8% 降至 23.0%。
- 有害标签预训练 + SafeBeam 解码贡献最大，进一步将 ASR 压至 8.3%。
- 通用能力（标准 NLP 基准）未出现显著下降，甚至略有提升（平均 42.8% → 43.5%）。
- 在帮助力方面，安全预训练未增加过度拒绝，SafeBeam 带来小幅增加但可接受。
- 后训练对齐（指令微调）的脆弱性得到验证：标准模型在良性微调后 ASR 回升至 38.8%，而安全预训练模型仅小幅上升。
- 对抗攻击（GCG）下，安全预训练本身未显著提升鲁棒性，但 SafeBeam 可带来部分改善。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：将安全构建从后训练移到预训练阶段，是系统性框架而非单一技巧。
- **数据中心方法**：利用合成数据保留信息的同时注入伦理约束，避免直接删除带来的知识丢失。
- **丰富的数据集与工具发布**：公开 SafeWeb（100B token）、RefuseWeb、Moral Education 数据集、安全分类器、以及基座模型安全评估数据集；提出“数据安全报告卡”（Data Safety Report Card）标准。
- **实验设计全面**：不仅测评安全，还覆盖通用性能、帮助力、过度拒绝、良性微调鲁棒性和对抗攻击，论证充分。
- **技术细节扎实**：对安全分类器进行了大量比较（9 种 embedding/LLM），并分析了失败案例；对标签注入比例进行消融；对比了标签在预训练 vs 后训练阶段注入的效果，证明预训练的必要性。

## 8. 不足与局限

- **规模限制**：所有实验只在 1.7B 参数模型上进行，更大规模模型（如 7B、70B）的效果未知，可能因推理能力和容量差异而不同。
- **算力成本高**：预训练 + 合成数据生成需要大量计算资源，可能限制普及性。
- **过度拒绝问题**：虽然整体帮助力未降，但 SafeBeam 解码导致轻微过度拒绝，提示需进一步平衡安全与帮助力。
- **对抗攻击鲁棒性有限**：对 GCG 等白盒攻击的防御仍不理想，仅 SafeBeam 提供部分改善，且未评测自适应攻击。
- **分类器依赖**：安全评分依赖 GPT-4o-mini 标注和 Qwen/embedding 分类器，可能存在偏差或漏报。
- **单次运行**：每个实验仅跑一次，缺乏统计显著性报告，结果可能受随机性影响。
- **评估范围**：未涵盖多轮对话、语言多样性、隐蔽毒性等复杂场景。

（完）
