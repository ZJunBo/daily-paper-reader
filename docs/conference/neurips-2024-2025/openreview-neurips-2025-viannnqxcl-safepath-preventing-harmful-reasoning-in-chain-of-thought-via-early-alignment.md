---
title: "SAFEPATH: Preventing Harmful Reasoning in Chain-of-Thought via Early Alignment"
title_zh: SAFEPATH：通过早期对齐防止链式思维中的有害推理
authors: "Wonje Jeung, Sangyeon Yoon, Minsuk Kahng, Albert No"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=vIaNnnQxcl"
tags: ["query:smd"]
score: 6.0
evidence: 微调推理模型以输出安全前缀，缓解有害推理，涉及对齐保持
tldr: 该论文提出SAFEPATH方法，通过微调大型推理模型使其在有害提示下于推理开始处输出一个短的安全前缀，从而在保持推理深度的同时减少有害输出。该方法直接涉及微调过程的安全对齐，但专注于推理阶段而非数据混合，与用户需求中的安全退化缓解方向相关。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-viannnqxcl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1447, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-viannnqxcl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1457, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-viannnqxcl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-viannnqxcl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 393, \"height\": 347, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-viannnqxcl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1424, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-viannnqxcl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 474, \"height\": 343, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-viannnqxcl/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 438, \"height\": 285, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-viannnqxcl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1471, \"height\": 981, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-viannnqxcl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 526, \"height\": 129, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-viannnqxcl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1024, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-viannnqxcl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 685, \"height\": 210, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-viannnqxcl/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1456, \"height\": 867, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-viannnqxcl/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 624, \"height\": 169, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-viannnqxcl/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1345, \"height\": 729, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-viannnqxcl/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 985, \"height\": 832, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-viannnqxcl/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1456, \"height\": 530, \"label\": \"Table\"}]"
motivation: 大型推理模型在有害提示下可能产生不安全输出，现有对齐方法会损害推理深度且易被越狱。
method: 微调模型，使其在有害提示推理开始时输出一个8 token的安全前缀，其余推理无监督。
result: 实验表明SAFEPATH有效降低有害输出，同时保持推理性能。
conclusion: SAFEPATH是一种轻量级对齐保持方法，但未涉及安全数据混合策略。
---

## Abstract
Large Reasoning Models (LRMs) have become powerful tools for complex problem solving, but their structured reasoning pathways can lead to unsafe outputs when exposed to harmful prompts. Existing safety alignment methods reduce harmful outputs but can degrade reasoning depth, leading to significant trade-offs in complex, multi-step tasks, and remain vulnerable to sophisticated jailbreak attacks. To address this, we introduce SAFEPATH, a lightweight alignment method that fine-tunes LRMs to emit a short, 8-token Safety Primer at the start of their reasoning, in response to harmful prompts, while leaving the rest of the reasoning process unsupervised. Empirical results across multiple  benchmarks indicate that SAFEPATH effectively reduces harmful outputs while maintaining reasoning performance. Specifically, SAFEPATH reduces harmful responses by up to 90.0\% and blocks 83.3\% of jailbreak attempts in the DeepSeek-R1-Distill-Llama-8B model, while requiring 295.9x less compute than Direct Refusal and 314.1x less than SafeChain. We further introduce a zero-shot variant that requires no fine-tuning. In addition, we provide a comprehensive analysis of how existing methods in LLMs generalize, or fail, when applied to reasoning-centric models, revealing critical gaps and new directions for safer AI.

---

## 论文详细总结（自动生成）

# 论文《SAFEPATH: Preventing Harmful Reasoning in Chain-of-Thought via Early Alignment》详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大型推理模型（LRM）如 DeepSeek-R1、OpenAI o1 等在复杂推理任务中表现出色，但其结构化、多步的链式思维（Chain-of-Thought）推理路径在面对有害提示时容易放大不安全行为，生成有害输出。例如，模型可能通过推理将恶意请求误判为良性，从而给出危险答案。
- **现有方法缺陷**：传统安全对齐方法（如直接拒绝训练 SafeChain）虽然能减少有害输出，但往往以牺牲推理深度为代价，导致“安全税”——即推理能力显著下降（尤其在复杂推理任务如 AIME24 上准确率下降 16.6%）。此外，这些方法对高级越狱攻击（如 PAIR、Prefilling）的防御能力较弱。
- **核心目标**：提出一种轻量级的对齐方法，在不损害 LRM 推理能力的前提下，有效减少有害输出并抵御越狱攻击，实现安全与推理的平衡。

## 2. 论文提出的方法论

### 核心思想
- **Safety Primer**：设计一个固定的 8-token 前缀“**Let’s think about safety first**”，在有害提示的推理开始时注入该前缀，作为一个软信号引导模型进入安全感知的推理路径，而非强制拒绝或终止推理。
- **训练方式**：仅对 Safety Primer 的 8 个 token 进行监督微调，其余推理过程（包括 think 块和最终答案）完全无监督，保持模型的自然推理能力。
- **关键设计**：训练时不在 Safety Primer 后关闭 `</think>` 标签，而是保持推理块开放，使模型能够从安全初始化后继续推理，而不是直接拒绝。

### 训练流程
- 使用两个互补的数据集：
  - **Safety Trigger Set**：从 WildJailbreak 数据集选出有害提示，训练目标为：模型在 `<think>` 后输出 8-token Safety Primer，损失仅施加于这 8 个 token。
  - **Reasoning Retain Set**：从 DeepSeek Math 220K 中选用良性提示，训练完整推理且不加 Safety Primer，以保持通用推理能力。
- 两类样本按固定比例 \( \alpha : (1-\alpha) \) 混合（实验中 R-7B 只用安全数据，R-8B 使用 10% 安全数据可取得良好效果）。

### 零样本变体
- **ZS-SAFEPATH**：无需微调，直接在推理开始时插入“Let’s think about safety first”前缀（同样不关闭 `</think>` 标签），模型自动继续推理。该变体可在不更新参数的情况下提供安全增益。

### 涌现行为
- 实验发现一个有趣现象：尽管 Safety Primer 只在训练时被要求出现一次，但在对抗性较强的场景（如 PAIR 攻击）中，模型会在推理过程中多次自发重新激活该短语，平均每样本触发 8 次以上。这表明模型学会了内部安全监测和动态纠正，形成了“深度对齐”。

## 3. 实验设计

### 使用的模型
| 模型 | 说明 |
|------|------|
| DeepSeek-R1-Distill-Qwen-7B (R-7B) | 从 DeepSeek-R1 蒸馏的 7B 模型，安全对齐较弱 |
| DeepSeek-R1-Distill-Llama-8B (R-8B) | 8B 蒸馏模型，主要实验对象 |
| s1.1 | 非蒸馏模型，用于验证泛化性 |
| R-1.5B / R-14B / R-32B | 用于零样本方法规模扩展分析 |

### 基准测试与评估维度
- **有害性**：StrongReject（直接有害提示，60 个样本）、BeaverTails（1000 个样本，使用 BeaverDam 分类器评估）。
- **对抗鲁棒性**：
  - DAN（Do-Anything-Now，300 个样本）
  - PAIR（自动迭代越狱，80 个样本，n_iterations=3）
  - Jailbreak Trigger（400 个样本，13 种攻击类型）
  - Multilingual（9 种语言翻译 AdvBench，共 720 样本）
  - Prefilling（向推理块开头注入引导短语，1000 样本）
- **推理能力**：MATH500、GPQA、AIME24（数学）、MBPP（代码生成）。
- **通用能力**：MMLU、ARC-Challenge。

### 对比方法
| 类别 | 方法 | 说明 |
|------|------|------|
| 基于微调的 LRM 基线 | **Direct Refusal** | 训练模型直接拒绝有害提示，关闭推理 |
| | **SafeChain** | 同时监督推理和答案的安全输出 |
| 基于 LLM 的基线 | **Task Arithmetic (TA)** | 通过参数减法去除有害行为 |
| | **Negative Preference Optimization (NPO)** | 将有害样本视为负偏好进行优化 |
| | **Circuit Breaker (CB)** | 在表示层面阻断有害激活 |
| 零样本方法 | **ZeroThink** | 立即关闭 `<think>` 块，无推理 |
| | **LessThink** | 插入短推理短语后关闭 |

### 实验数量与充分性评估
论文共进行了**10 组以上主要实验**，包括：
1. 主表对比（表1）：在 R-7B 和 R-8B 上对比三个 LRM 方法（Direct Refusal, SafeChain, SAFEPATH）在有害性、鲁棒性、推理、通用能力四方面的完整结果。
2. LLM 基线对比（图3，表8）：对比 TA、NPO、CB 与 SAFEPATH。
3. 消融实验：
   - 安全数据比例 α（图6）
   - 不同前缀设计（表3：SP vs CautionPath vs RefusalPath）
   - 不同安全触发数据集（表6：WildJailbreak vs AdvBench vs BeaverTails）
   - 前缀位置（图8：开头 vs 末尾）
4. 零样本方法对比（表5）：ZS-SAFEPATH vs ZeroThink vs LessThink 在 5 种规模模型（1.5B~32B）上。
5. 涌现行为分析（图4）：不同数据上 Safety Primer 激活次数。
6. 训练时间（表2）和推理时间（图5，表9）。
7. 泛化性（表4）：在 s1.1 模型上验证。
8. 定性示例（图9,10）。

**充分性评价**：实验覆盖了安全、对抗、推理、通用、效率、涌现行为等多个维度，对比方法全面（包括 LRM 专用方法和 LLM 通用方法），消融实验系统（数据比例、前缀设计、数据集选择、位置），且包含零样本和泛化性验证。实验设计客观、公平，充分支撑了论文结论。

## 4. 资源与算力

- **硬件**：8 块 NVIDIA RTX L40S（48GB）GPU，512 CPU 核心，1024GB RAM。
- **总消耗**：约 2000 GPU 小时。
- **训练效率**：
  - **SAFEPATH**：R-7B 仅需 4.1 分钟（100 步），R-8B 仅需 1.5 分钟（20 步）。
  - 训练速度比 Direct Refusal 快 **295.9 倍**（R-8B），比 SafeChain 快 **314.1 倍**。
  - 相比 Direct Refusal（435 分钟）和 SafeChain（462 分钟），SAFEPATH 只需 <5 分钟。
- **推理时间**：SAFEPATH 推理时间与基础模型相当（R-8B 平均 3284 秒 vs 基础 3087 秒），几乎无额外开销。而 Direct Refusal 因提前拒绝反而缩短推理时间。ZeroThink 和 LessThink 因跳过推理时间更短，但推理能力严重下降。

## 5. 主要结论与发现

1. **安全-推理平衡最优**：SAFEPATH 在保持推理能力几乎不变的同时，将有害响应率降低 **90.0%**（R-8B），越狱成功率降低 **83.3%**。相比之下，Direct Refusal 和 SafeChain 在 AIME24 上均损失 16.6% 准确率。
2. **对抗鲁棒性最强**：在全部 5 种攻击下，SAFEPATH 平均攻击成功率仅 **8.8%**（R-8B），远低于 Direct Refusal（47.8%）、SafeChain（52.5%）以及各种 LLM 基线（TA 49.4%，NPO 36.7%，CB 62.1%）。
3. **涌现动态安全行为**：模型在对抗性强的场景下会自发多次激活 Safety Primer（PAIR 下平均 8 次），实现上下文敏感的安全强化，而训练时仅要求出现一次。
4. **零样本变体有效**：ZS-SAFEPATH 在不微调的情况下同样能显著降低有害性（R-32B 有害分 11.75%，弱于 ZeroThink 的 3%，但推理准确率高达 74.06%，远超 ZeroThink 的 55.21%），适合轻量应用。
5. **训练极轻量**：仅更新 8 个 token 的前缀，计算成本极低。
6. **前缀设计关键**：与其他前缀（如 CautionPath 直接提醒有害、RefusalPath 直接拒绝）相比，SAFEPATH 的软性前缀不会阻止推理，能够继续解题并得到正确答案。
7. **跨模型泛化**：在非蒸馏模型 s1.1 上同样有效，优于 Direct Refusal 和 SafeChain。
8. **数据选择鲁棒**：不同安全触发数据集（WildJailbreak, AdvBench, BeaverTails）表现一致，展示了方法对不同数据源的适应性。

## 6. 优点

- **新颖且高效的核心设计**：仅用 8-token 前缀进行软对齐，抛弃了传统方法中复杂的监督策略，开创了“轻量级对齐”新范式。
- **涌现的深度对齐**：模型在对抗环境下自发多次激活 Safety Primer，表明训练信号能够内化为更深层的安全机制，超越了浅层 token 级别的控制。
- **极低的训练成本**：训练时间从数小时降至数分钟，适合大规模快速部署和持续安全更新。
- **保持推理能力**：通过开放推理块、不对推理过程施加额外约束，成功避免了“安全税”，在复杂数学推理中几乎无损失。
- **零样本扩展**：ZS-SAFEPATH 提供了一种无需微调的实用备选方案，适用于无法训练的场景。
- **全面且公平的实验**：对比方法覆盖 LRM 专用方法和 LLM 通用方法，消融实验系统，包含不同比例、前缀、数据集、位置、规模等，客观地验证了方法的优势。
- **清晰的可视化与定性分析**：通过激活频率图和定性示例生动展示了模型行为，增强了结果的可解释性。

## 7. 不足与局限

- **对抗攻击仍有失败案例**：对于高度优化的攻击如 PAIR，ASR 仍超过 25%，说明 SAFEPATH 在面对持续迭代的对抗性攻击时仍有脆弱性。
- **依赖模型内部推理能力**：SAFEPATH 的有效性依赖于模型本身具有一定的安全感知能力和推理灵活性，对于完全不安全的模型或极低容量的模型可能效果有限。
- **零样本变体安全增益有限**：ZS-SAFEPATH 的有害分数虽然下降明显，但仍高于 ZeroThink，在要求极高安全性的场景下可能不够。
- **未覆盖多轮对话或动态环境**：当前工作聚焦单轮提示，未讨论多轮对话或在线学习场景下的对齐问题。
- **训练数据质量影响**：安全触发数据来源于特定 jailbreak 数据集，可能未覆盖所有有害类型，存在分布偏差风险。
- **泛化性验证范围有限**：虽然测试了 s1.1 模型，但未在更多不同架构或训练范式（如纯 RL 训练的 LRM）上验证。
- **缺少统计显著性报告**：所有实验使用单次种子运行，未报告误差条或置信区间，可能影响结果稳健性。
- **仅提供定性解释无理论保证**：对涌现行为的分析基于观察，缺少理论模型解释。

（完）
