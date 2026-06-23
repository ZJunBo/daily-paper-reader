---
title: "Decoding Uncertainty: The Impact of Decoding Strategies for Uncertainty Estimation in Large Language Models"
title_zh: 解码不确定性：解码策略对大语言模型不确定性估计的影响
authors: "Wataru Hashimoto, Hidetaka Kamigaito, Taro Watanabe"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.findings-emnlp.788.pdf"
tags: ["query:luq"]
score: 8.0
evidence: 研究解码策略对大语言模型不确定性估计的影响
tldr: 解码策略通过改变概率分布影响生成质量与不确定性，但对其具体影响缺乏系统研究。本文系统考察了多种解码策略对LLM不确定性估计的影响。实验表明，对于偏好对齐的LLM，Contrastive Search能显著提升不确定性估计质量；而在仅经过有监督微调的模型上，部分策略优势消失。该工作强调了解码策略选择在不确定性量化中的重要性。
source: EMNLP-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.788/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1586, \"height\": 672, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.788/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1590, \"height\": 663, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.788/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 768, \"height\": 147, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.788/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 779, \"height\": 147, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 813, \"height\": 543, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1653, \"height\": 552, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 781, \"height\": 538, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 794, \"height\": 523, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 740, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 785, \"height\": 149, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 777, \"height\": 534, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 714, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 786, \"height\": 557, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1568, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1204, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1204, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1237, \"height\": 161, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 713, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 713, \"height\": 248, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 522, \"height\": 203, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.788/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 525, \"height\": 205, \"label\": \"Table\"}]"
motivation: 解码策略直接影响概率分布，进而影响不确定性估计的质量，但其影响机制尚不明确。
method: 在多种LLM上进行对比实验，评估不同解码策略下的不确定性估计性能。
result: Contrastive Search在偏好对齐模型上优于其他策略，但在仅微调模型上效果差异显著。
conclusion: 解码策略是影响LLM不确定性估计的关键因素，需根据模型类型谨慎选择。
---

## Abstract
Decoding strategies manipulate the probability distribution underlying the output of a language model and can therefore affect both generation quality and its uncertainty. In this study, we investigate the impact of decoding strategies on uncertainty estimation in Large Language Models (LLMs). Our experiments show that Contrastive Search, which mitigates repetition, yields better uncertainty estimates on average across a range of preference-aligned LLMs. In contrast, the benefits of these strategies sometimes diverge when the model is only post-trained with supervised fine-tuning, i.e. without explicit alignment.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）在安全关键领域（如医疗、金融、法律）的部署受到其产生幻觉（hallucinations）问题的严重阻碍。不确定性估计（Uncertainty Estimation, UE）是一种缓解该问题的关键技术，通过量化预测不确定性，系统可以拒绝可疑输出并将其转交给人类专家或更强大的模型。解码策略通过操纵 token 的概率分布来影响生成质量和不确定性，但其对 UE 性能的综合影响尚未被系统研究。
- **研究问题**：
  - **RQ1**：哪种解码策略能带来最佳的不确定性估计性能？
  - **RQ2**：训练阶段（如 SFT 和偏好对齐）如何调节不同解码策略下的 UE 性能？
- **整体含义**：揭示解码策略选择对 LLM 不确定性量化的重要影响，为构建更可靠的 LLM 提供实践指导。

## 2. 方法论：核心思想、关键技术细节

### 2.1 核心思想
- 通过对比多种确定性解码策略，评估它们在不同任务、不同模型训练阶段下对不确定性估计性能的影响。
- 使用两种经典的不确定性评分：**最大序列概率（MSP）** 和 **平均 token 熵（MTE）**。
- 采用 **预测-拒绝比（Prediction–Rejection Ratio, PRR）** 作为评估指标，无需二分类标签，适用于多种文本生成任务。

### 2.2 关键技术细节
- **确定性解码策略**：共考察 8 种策略：
  - Greedy Search（贪心搜索）
  - Beam Search（束搜索）
  - Diverse Beam Search（多样束搜索）
  - Contrastive Search（对比搜索）
  - Contrastive Decoding（对比解码）
  - Frustratingly Simple Decoding（FSD）及其向量化版本（FSD-vec）
  - Decoding by Contrastive Layers（DoLa）
  - Self-Logits Evolution Decoding（SLED）
- **不确定性估计流程**：
  - 对每个输入，使用指定解码策略生成输出。
  - 计算 MSP（负对数似然）和 MTE（平均 token 熵）作为不确定性分数。
  - 使用 PRR 评估不确定性分数与生成质量（任务相关）之间的关联。PRR = PRC_uns / PRC_orc，值越高表示不确定性估计越准确。
- **质量分数**：QA 使用 RougeL；TS 使用 RougeL 和 AlignScore；MT 使用 BLEU、Comet 和 AlignScore；CG 使用 Pass@1。

## 3. 实验设计

### 3.1 数据集与 benchmark
- **QA**：TriviaQA（17,210 条）
- **TS**：XSum（11,334 条）
- **MT**：WMT19（德→英，2,998 条）
- **CG**：HumanEval（164 条）
- 所有任务均为英文，使用公开测试集。

### 3.2 对比方法
- 8 种确定性解码策略（见 2.2）。
- 额外实验包含温度采样、Top-p 采样（随机解码），以及高级 UE 方法 TokenSAR。
- 对于 RQ1，使用三种偏好对齐模型：Llama2-7B-Chat、Llama3-8B-RLHF、Zephyr-7B-β。
- 对于 RQ2，使用 Llama3-8B-SFT、Llama3-8B-RLHF、Llama3-8B-DPO 进行比较。
- 附加实验还使用了 Qwen2.5-7B/14B-Instruct、Llama2-13B-Chat。

### 3.3 超参数搜索
- 对每种解码策略在每一任务-模型组合上进行了超参数调优（如束大小、对比系数 α/β、top-n 等），详见附录 J。

## 4. 资源与算力

- 论文明确说明：**所有实验使用单张 NVIDIA A100 40GB GPU**。
- 未提及训练时长或总 GPU 小时数，仅说明单卡完成。

## 5. 实验数量与充分性

- **主要实验**：在 3 个模型 × 4 个任务 × 8-9 种解码策略 × 2 种不确定性评分 = 约 200+ 组 PRR 实验。
- **RQ2 实验**：涉及 SFT→RLHF 和 SFT→DPO 的过渡对比，每组 6 种策略，覆盖所有质量指标。
- **附加实验**：包括 Qwen 系列、Llama2-13B 模型、随机解码（温度/ Top-p）、TokenSAR 方法，以及 Distinct-n 分析。
- **公平性**：使用相同的指令模板、相同的评估协议，超参数通过搜索选取最优值。PRR 标准误通过 bootstrap（1000 次）计算，并标注显著性。
- **客观性**：所有数据集、模型和代码均公开，实验可复现。但未进行跨提示模板或跨语言验证。

## 6. 主要结论与发现

1. **Contrastive Search (CS) 整体最优**：在偏好对齐的 LLM 上，CS 平均 PRR 最高，且能有效缓解重复（表现为 Distinct-1/2 最高），从而减少过度自信。
2. **SFT 阶段结论可能不同**：在仅经 SFT 的模型上，Beam Search 有时表现更好；但经过 RLHF/DPO 后，其 UE 性能下降。
3. **RLHF 与 DPO 对 UE 影响不同**：RLHF 可在某些任务（如 MT）上提升 PRR，而 DPO 因“挤压效应”（squeezing effect）导致概率集中，UE 性能更差。
4. **BS/DBS 在某些模型上表现差**：在偏好对齐模型上，BS/DBS 会大幅改变概率分布，导致不确定性分数与生成质量脱钩。
5. **CD 性能不稳定**：依赖于学生-教师模型配对，在 Llama2-7B 上 MT 表现突出，但在其他模型上退化。
6. **事实性解码（DoLa/SLED）表现不佳**：虽提升事实性，但扭曲概率分布，导致过度自信和低 PRR。
7. **随机解码策略（温度/Top-p）UE 性能与贪心搜索相似**，未带来显著改进。

## 7. 优点

- **系统全面的评估**：覆盖多种确定性解码策略、多种训练阶段、多任务，填补了领域空白。
- **有效的评估指标**：使用 PRR 而非简单 AUROC，更适应连续质量评分任务。
- **深入分析机制**：通过 Distinct-n 分析揭示 CS 缓解重复与 UE 提升的关联，通过“挤压效应”解释 DPO 的劣势。
- **代码开源**：所有代码公开，便于复现和扩展。
- **实验公平性**：一致的评估协议、超参数搜索、bootstrap 显著性检验。

## 8. 不足与局限

- **模型规模有限**：主要基于 7B/8B 模型，未验证更大模型（如 70B）或黑盒模型（GPT-4, Gemini）。
- **解码策略不完整**：未包含 ϕ-Decoding 等最新策略；仅考察确定性策略，随机策略只做了小范围实验。
- **UE 方法简单**：仅使用 MSP 和 MTE，未系统评估更先进的 UE 方法（如 Semantic Entropy、TokenSAR、距离法）。结论可能随更强 UE 方法改变。
- **任务覆盖有限**：仅英文任务，未涉及多模态、RAG、非英文场景。
- **提示模板固定**：未探索提示工程对结论的影响。
- **潜在偏差**：使用单一 SFT 模型（Llama3-8B-SFT），其特性可能不泛化到其他 SFT 模型。

（完）
