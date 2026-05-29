---
title: "Focus On This, Not That! Steering LLMs with Adaptive Feature Specification"
title_zh: 聚焦这个，不要那个！通过自适应特征规范引导大语言模型
authors: "Tom A. Lamb, Adam Davies, Alasdair Paren, Philip Torr, Francesco Pinto"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=rbI5mOUA8Z"
tags: ["query:dg"]
score: 8.0
evidence: 提出聚焦指令微调（FIT），通过训练模型关注特定特征来引导行为，是一种引导方法
tldr: 本文提出聚焦指令微调（FIT），通过训练大语言模型在生成响应时关注指定的特征并忽略其他特征，从而实现推理时的行为引导。该方法不仅能够成功引导模型行为，还增强了对虚假关联的鲁棒性，并在多个基准上展示了有效性。FIT将引导能力内化为模型自身特性，为安全对齐提供了新工具。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 856, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 833, \"height\": 577, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1742, \"height\": 901, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 874, \"height\": 846, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 864, \"height\": 338, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 867, \"height\": 596, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 828, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1333, \"height\": 710, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1675, \"height\": 973, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 421, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 423, \"height\": 331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1156, \"height\": 1319, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 323, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1155, \"height\": 1322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1109, \"height\": 1206, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 909, \"height\": 827, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1177, \"height\": 721, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 323, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rbi5moua8z/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1079, \"height\": 514, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-rbi5moua8z/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 869, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rbi5moua8z/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 877, \"height\": 215, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rbi5moua8z/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 625, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rbi5moua8z/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1780, \"height\": 638, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rbi5moua8z/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1779, \"height\": 637, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rbi5moua8z/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1781, \"height\": 675, \"label\": \"Table\"}]"
motivation: 现有引导方法通常是事后型，未将引导嵌入模型本身，且模型容易利用虚假特征。
method: 提出FIT，通过指令微调让模型学会根据指定特征调整输出，并忽略不相关特征。
result: 在多个基准上验证了引导能力和鲁棒性提升，优于现有方法。
conclusion: FIT是一种有效的引导方法，将引导内化为模型特性，可提升安全性和可靠性。
---

## Abstract
Despite the success of Instruction Tuning (IT) in training large language models (LLMs), such models often leverage spurious or biased features learnt from their training data and can become misaligned, leading to undesired behaviours. While existing techniques can steer model behaviour at inference-time, they are often post-hoc and do not embed steering as an intrinsic model feature. In this work, we introduce Focus Instruction Tuning (FIT), which trains LLMs to condition their responses by focusing on specific features whilst ignoring others, leading to different behaviours based on what features are specified. Across diverse benchmarks, we demonstrate that FIT: (i) successfully steers behaviour at inference time; (ii) increases robustness by amplifying core task signals and down-weighting spurious cues; (iii) mitigates social bias by suppressing demographic attributes; and (iv) generalises under distribution shifts and to previously unseen focus features. FIT therefore offers a lightweight, intrinsic mechanism for building more robust, fair, and easily controllable LLMs.

---

## 论文详细总结（自动生成）

# 论文《Focus on This, Not That! Steering LLMs with Adaptive Feature Specification》中文总结

## 1. 核心问题与整体含义（研究动机和背景）

大型语言模型（LLM）通过指令微调（Instruction Tuning, IT）获得了一定的指令跟随能力，但在实际应用中仍容易学习训练数据中的虚假特征（spurious features）或社会偏见，导致行为偏差（misalignment）。现有的推理时引导方法（如潜在空间干预）多为事后修正（post-hoc），需要白盒访问模型表示，且适应性差，未能将引导能力内化为模型自身的通用特性。为了解决这一问题，本文提出**聚焦指令微调（Focus Instruction Tuning, FIT）**，通过训练LLM根据用户指定的自然语言指令来**关注（focus on）**或**忽略（ignore）**特定特征，从而动态调整输出行为，实现内在的、可控的引导能力。

## 2. 方法论

### 核心思想
FIT 在标准指令微调的基础上，引入一组**聚焦指令（focus instructions）**，例如“关注核心特征C”、“忽略虚假特征S”、“既关注C又忽略S”等。训练时，对于每个样本，根据随机采样的聚焦指令重新定义目标标签（称为**聚焦标签 focus label**），使模型学会在不同的聚焦指令下输出不同的答案。推理时，用户只需通过自然语言指定聚焦要求，模型便能自动调整行为。

### 关键技术细节
- **聚焦指令集** \( I_{focus} \)：包含六种类型：空指令（∅）、关注核心特征、忽略虚假特征、关注核心并忽略虚假、关注虚假特征、关注虚假并忽略核心。
- **聚焦标签定义**：当指令要求关注核心或忽略虚假时，聚焦标签等于真实标签 \( y \)；当指令要求关注虚假特征时，聚焦标签等于与该虚假特征值关联的虚假标签 \( y_s \)。
- **训练目标**：最小化条件负对数似然 \( \mathbb{E}[-\log p_\theta(y_{focus} \mid I, I_{focus}, x)] \)，通过经验风险最小化（ERM）和SGD优化。
- **实现细节**：使用 LoRA 参数高效微调，早停基于验证集交叉熵损失，约束波束解码保证输出包含答案标签。

## 3. 实验设计

### 数据集与场景
- **SS（Spurious Sentiment）**：基于SST-5构造的二元情感分析数据集，引入关键词“Pineapple”和“Bayesian”作为虚假特征，控制其与标签的共现率（ρ_spurious）。
- **SMNLI（Spurious MNLI）**：从MNLI子采样得到的三分类NLI数据集，将文本体裁（如government, fiction, travel）作为虚假特征，通过子采样控制ρ_spurious。额外构造体裁值分布偏移的测试集（unseen genres）。
- **BBQ（Bias Benchmark for QA）**：多选问答数据集，包含9种社会偏见（性别、种族等）。训练时使用其中6种，测试时包括已见和未见偏见特征。

### 测试分裂与指标
- 每个数据集包含训练集、验证集和多个测试集：D_iid（同分布）、D_high（高共现）、D_low（低共现）、D_flipped（翻转共现）、分布偏移集（SMNLI）等。
- 主要指标：**聚焦准确率（Focus Accuracy）**，即模型预测与聚焦标签一致的比例。

### 对比方法
- Zero-shot（原始预训练模型）
- Few-shot（4个上下文示例）
- SFT(y)（标准IT，训练于真实标签）
- SFT(y_focus)（训练于聚焦标签但不含聚焦指令）
- 额外对比：Product of Experts（PoE）去偏方法、BBQ-NLG扩展、提示措辞鲁棒性、模型规模消融（Qwen-2.5 1.5B/3B/7B）。

### 模型
Llama-3.1-8B-Instruct、Mistral-7B-Instruct-v0.3、Vicuna-13B-v1.5，以及Qwen-2.5系列用于规模消融。

## 4. 资源与算力

论文**未明确说明**使用的具体GPU型号、数量或训练时长，仅提到使用LoRA进行参数高效微调，并利用Hugging Face SFTTrainer进行训练。计算资源由牛津大学等提供。因此无法给出精确的算力统计。

## 5. 实验数量与充分性

实验覆盖**三个主要数据集**（SS、SMNLI、BBQ），每个数据集包含多个测试分裂（4~5种），每个模型（3种）和每个聚焦指令类型（6种）均报告结果。除主实验外，还包括：
- 分布偏移泛化（SMNLI中未见过体裁）
- 未见偏见特征泛化（BBQ）
- 提示措辞鲁棒性（10条ChatGPT改写）
- 保持通用能力（Alpaca-GPT指令跟随评分、MMLU零样本准确率和困惑度）
- 模型规模消融（Qwen-2.5 1.5B/3B/7B）
- 扩展至开放生成（BBQ-NLG）
- 与PoE去偏方法对比（BBQ）
- 在HANS数据集上测试重叠特征（SHANS，发现局限）

以上实验覆盖了多种场景、多种模型尺寸、多种特征类型，结果均通过多次重复报告均值和标准差，基线对比全面，**实验充分、客观、公平**。

## 6. 主要结论与发现

- FIT 在所有数据集上实现了**极高的聚焦准确率**，显著优于所有基线，证明其能**有效引导模型行为**。
- 在分布偏移（特征值变化或完全未见）下，FIT 仍保持**稳定的引导能力**，而基线则下降。
- FIT 在**缓解社会偏见**方面表现优异，且能**泛化到训练中未见过的偏见特征**。
- FIT **不损害**原始模型的指令跟随能力（Alpaca-GPT评分无显著差异）和零样本迁移性能（MMLU准确率几乎不变）。
- 模型**规模越大，FIT 效果越好**（Qwen-2.5 7B>3B>1.5B）。
- FIT 对**提示措辞变化鲁棒**，性能波动很小。

## 7. 优点

- **内在可引导性**：将引导能力嵌入模型本身，无需额外推理时干预即可通过自然语言控制。
- **灵活可控**：支持同时关注和忽略特征，用户可动态指定任意特征组合（至少验证了双特征）。
- **强泛化能力**：能泛化到未见过特征值和未见过特征，适用于实际中新出现的偏见或分布偏移。
- **保持基础能力**：不会导致“对齐税”，即不牺牲原有LLM的通用能力。
- **增强可解释性**：通过观察不同聚焦指令下的输出差异，可归因模型行为对特征的依赖。
- **轻量化**：基于LoRA微调，计算开销小，易于部署。
- **代码和数据集开源**：项目页面提供了完整资源。

## 8. 不足与局限

- **需要预先标注虚假特征**：训练阶段需要知道哪些特征是虚假或偏见的（但可通过自动检测方法缓解）。
- **实验以分类和MCQA为主**：对开放生成任务（如摘要、翻译）的验证仅初步（BBQ-NLG），需更广泛评估。
- **处理重叠特征存在挑战**：在HANS数据集中，当虚假特征（如词汇重叠、子序列、成分结构）高度重叠时，FIT泛化表现下降。
- **多特征组合扩展性未充分研究**：当前只验证了“关注一个并忽略一个”的组合，更复杂的多特征指令尚未深入。
- **未提供计算资源细节**：难以复现算力开销。
- **安全性风险**：该方法可能被恶意用于故意引导模型输出偏见或有害内容，论文虽提及但未提供防护机制。

（完）
