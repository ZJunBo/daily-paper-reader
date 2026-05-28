---
title: Safety Alignment Can Be Not Superficial With Explicit Safety Signals
title_zh: 使用显式安全信号避免安全对齐的表面化
authors: "Jianwei Li, Jung-Eun Kim"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=e9YosoGkYg"
tags: ["query:smd"]
score: 4.0
evidence: 显式安全信号防止安全对齐被稀释
tldr: 现有安全对齐方法学习的安全信号常被其他目标稀释，导致对齐表面化。本文提出引入显式安全信号，使模型形成更稳健的安全决策边界，从而提升对抗攻击能力。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-e9yosogkyg/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1524, \"height\": 628, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-e9yosogkyg/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1599, \"height\": 747, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-e9yosogkyg/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1599, \"height\": 588, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-e9yosogkyg/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 848, \"height\": 281, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-e9yosogkyg/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 850, \"height\": 270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-e9yosogkyg/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 829, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-e9yosogkyg/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1775, \"height\": 963, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-e9yosogkyg/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1618, \"height\": 1900, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-e9yosogkyg/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1619, \"height\": 1896, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-e9yosogkyg/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1627, \"height\": 1905, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-e9yosogkyg/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1623, \"height\": 1902, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-e9yosogkyg/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1595, \"height\": 702, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-e9yosogkyg/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1594, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-e9yosogkyg/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1773, \"height\": 205, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-e9yosogkyg/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1233, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-e9yosogkyg/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 867, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-e9yosogkyg/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1766, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-e9yosogkyg/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1155, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-e9yosogkyg/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 582, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-e9yosogkyg/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 656, \"height\": 233, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-e9yosogkyg/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 655, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-e9yosogkyg/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 657, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-e9yosogkyg/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 442, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-e9yosogkyg/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1207, \"height\": 280, \"label\": \"Table\"}]"
motivation: 当前安全对齐学习的安全信号被其他目标稀释，模型易受攻击。
method: 引入显式安全信号训练模型，强化安全决策边界。
result: 模型在多种对抗攻击下表现更鲁棒，安全机制更深入。
conclusion: 显式安全信号能有效增强LLM安全对齐的鲁棒性。
---

## Abstract
Recent studies on the safety alignment of large language models (LLMs) have revealed that existing approaches often operate superficially, leaving models vulnerable to various adversarial attacks. Despite their significance, these studies generally fail to offer actionable solutions beyond data augmentation for achieving more robust safety mechanisms. This paper identifies a fundamental cause of this superficiality: existing alignment approaches often presume that models can implicitly learn a safety-related reasoning task during the alignment process, enabling them to refuse harmful requests. However, the learned safety signals are often diluted by other competing objectives, leading models to struggle with drawing a firm safety-conscious decision boundary when confronted with adversarial attacks. Based on this observation, by explicitly introducing a safety-related binary classification task and integrating its signals with our attention and decoding strategies, we eliminate this ambiguity and allow models to respond more responsibly to malicious queries. We emphasize that, with less than 0.2x overhead cost, our approach enables LLMs to assess the safety of both the query and the previously generated tokens at each necessary generating step. Extensive experiments demonstrate that our method significantly improves the resilience of LLMs against various adversarial attacks, offering a promising pathway toward more robust generative AI systems.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：现有大语言模型（LLM）的安全对齐（safety alignment）技术（如SFT、RLHF、DPO）虽然能够在标准场景下拒绝恶意请求，但面对各类对抗性攻击（如Prefill、GCG、DeepInception等）时，模型往往产生“表面化”的安全对齐——即模型只是学习了表层拒绝模式，而无法真正理解并维护安全边界。
- **核心问题**：作者指出，现有方法本质上依赖模型在训练过程中隐式学习安全相关推理任务（即区分恶意/良性输入），但这种“隐式安全信号”容易被其他竞争目标（如语气、风格、回复多样性等）稀释，导致模型在面对复杂对抗攻击时无法形成明确的安全决策边界。
- **整体意义**：为了克服这一局限，本文提出通过显式引入安全相关的二分类任务，将安全信号从隐式变为显式，并结合注意力机制和解码策略，使模型能够在每个必要的生成步骤中主动评估输入和已生成内容的安全性，从而显著提升鲁棒性。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- 将安全对齐问题显式建模为一个二分类任务（良性 vs 恶意），通过引入特殊的 `[CLS]` 令牌，使得模型能够直接输出安全分类预测，并利用该显式信号指导生成过程。

### 关键技术细节

1. **显式安全信号引入（二分类任务）**
   - 在输入序列开头插入一个 `[CLS]` 令牌（类似BERT架构），其隐藏状态经过一个分类头用于判断输入及已生成内容是否为恶意。
   - 在预训练阶段和SFT阶段同时优化语言模型损失和分类损失，损失函数形式：
     - 预训练：`L_pretraining = L_lm + λ1·L_cls`
     - 对齐（SFT）：`L_alignment = L_sft + λ2·L_cls`
   - 其中 `L_cls` 为 `[CLS]` 令牌输出的交叉熵分类损失。通过设置较小的系数 `λ1/λ2` 平衡生成能力与分类能力。
   - 注意力掩码设计：`[CLS]` 可关注所有令牌，但其他令牌（如查询令牌）不关注 `[CLS]`，以保持因果注意力的完整性。

2. **战略注意力机制（隐式利用）**
   - 在生成过程中，动态允许 `[CLS]` 令牌的隐藏状态影响后续生成的令牌。
   - 设计了三条规则（Rule 1-3）来确定 `[CLS]` 的注意力范围，针对不同场景（初始分类为恶意、初始分类为良性但后续变为恶意、出现转换点）自适应调整。
   - 超参数 `r1, r2, r3` 控制注意力窗口大小。

3. **战略解码策略（显式利用）**
   - 根据 `[CLS]` 的二分类预测结果，在解码时采取如下行动：
     - 若初始分类为恶意 → 立即插入引导令牌（如“Sorry, I cannot fulfill your request because…”）并继续生成拒绝理由。
     - 若初始分类为良性但在生成过程中连续 `τ` 步变为恶意 → 在转换点插入同样的引导令牌。
   - 通过链式思维（Chain-of-Thought）方式使拒绝解释更自然，减少误报。
   - 参数 `τ` 控制连续恶意预测的容忍度。

4. **动态重评估与计算效率**
   - 在推理阶段，仅在必要的生成步骤（使用退火策略）重新计算 `[CLS]` 令牌的预测，而不是每步都重算，从而将额外开销控制在生成总开销的0.2倍以下。

## 3. 实验设计

### 使用的数据集与场景
- **训练数据**：
  - 预训练：Wikipedia数据集，使用Llama3-Guard自动标注安全标签（弱监督）。
  - 对齐（SFT）：从LIMA、Alpaca、Alert数据集中构建，包含29,600个样本，良性/恶意各半。恶意查询的回答采用符合人类价值观的拒绝样式。
  - DPO基线使用Alert-DPO作为偏好数据集。
- **评估基准**（涵盖三类攻击）：
  - **直接攻击**：AdvBench（520条恶意查询）、HEx-PHI（330条有害指令）。
  - **越狱攻击**：Prefill（插入诱导令牌）、GCG（优化对抗后缀）、AutoDAN-T、DeepInception（嵌套场景）、PAP（说服性语言）、Alert-Adversarial（后缀/前缀/令牌操纵/角色扮演共4类）。
  - **解码攻击**：通过改变生成超参数（温度、top-p、top-k）诱导有害输出。

### 对比方法
- **主要基线**：在同一数据集上仅用SFT训练的模型；SFT+DPO训练的模型。
- **官方发布基线**：Llama2-7B-Chat（RLHF）。
- **最先进基线**：数据增强方法（Qi et al., 2024）的Llama2-7B-Chat-Aug。
- **跨家族对比**：Mistral-7B-Instruct-v0.2（增强版） vs Llama2-7B-Chat。

### 评估指标
- 主要指标：攻击成功率（ASR），采用两阶段评估：先用Llama3-Guard-Int8初筛，再用GPT-4复核被标记为不安全的输出，以确保准确性。

## 4. 资源与算力

- 文中明确说明：所有实验在一台配备**3块NVIDIA A6000 GPU**、256GB内存、16核CPU的机器上完成。
- **训练时长/成本**：未具体给出训练轮次的总时间，但提及因算力限制，未能验证10B以上模型，且对GCG等优化攻击的评估不充分（仅提供理论分析）。预训练阶段使用Wikipedia训练3个epoch；SFT阶段训练15个epoch（基础模型）或8个epoch（对齐模型）。整体算力投入属于中等规模。

## 5. 实验数量与充分性

- **实验数量**：
  - 主实验在Llama2-7B和Mistral-7B两个模型族上进行，对比了4类基线（SFT、DPO、RLHF、数据增强），覆盖3类攻击（直接、越狱、解码），共十余个 benchmark。
  - 消融实验：4项（移除预训练、移除注意力/解码组件、减少重分类频率、隐式影响分析）。
  - 超参数分析：对 `r1, r2, r3, τ` 以及分类阈值进行了系统探究。
  - 攻击类型全面，涵盖当前主流对抗方法。
- **充分性与公平性**：
  - 实验设计较为全面，对比基线包括同数据下的SFT/DPO、官方RLHF、以及数据增强SOTA，且使用了相同的训练数据集或超参数设置，整体公平。
  - 但对GCG攻击的评估限于100个样本（从HarmBench采样），且未在大模型（>10B）上验证，存在覆盖不足。
  - 预训练阶段使用弱监督标签可能引入噪声，消融实验也显示移除预训练后性能下降有限，说明预训练贡献不显著。

## 6. 主要结论与发现

- 显式安全信号（二分类任务）能够有效避免隐式安全信号被稀释的问题，使模型在面对复杂对抗攻击时具有更明确的安全决策边界。
- 提出的战略注意力机制和战略解码策略协同工作，大幅降低越狱和解码攻击的成功率（在多个benchmark上ASR降至1%以下，甚至0%）。
- 相比SFT、DPO、RLHF以及数据增强方法，所提方法在保持甚至提升有用性（如Mistral-7B-CLS在MT-Bench、GSM8K等任务上与原模型相当）的同时，显著增强了鲁棒性。
- 额外计算开销可控（小于0.2倍），且可与现有对齐方法兼容作为后处理增强。
- 探针实验表明：传统对齐模型在对抗攻击下logits的熵增大、锐度降低，而显式信号能缓解这种不确定性。

## 7. 优点

- **方法论创新**：首次将安全对齐显式化为二分类任务，并有机融入Transformer架构的注意力和解码过程，提供了比单纯数据增强更深层的解决方案。
- **实用性强**：训练过程简单（不需偏好数据、不需独立奖励模型），推理开销低，可直接作为现有对齐方法的增强模块。
- **评估严谨**：采用两阶段自动评估（Llama3-Guard + GPT-4），并公开指出关键词匹配的不足，体现了对评估质量的重视。
- **可解释性**：通过链式思维生成拒绝理由，提高了模型决策的透明度和用户信任。
- **实验全面**：覆盖多种主流攻击类型，并与多个代表性基线进行对比，消融实验设计合理。

## 8. 不足与局限

- **算力限制导致验证不充分**：未在10B以上大模型上测试，对GCG等优化攻击仅提供理论分析而未完成完整实验，可能削弱结论的泛化性。
- **预训练阶段效果有限**：由于使用弱监督（Llama3-Guard自动标注）且算力不足以进行高质量大范围预训练，预训练的贡献不明显，实验显示主要是SFT阶段在起作用。
- **仅限文本模态**：当前方法仅在文本对抗攻击上验证，未扩展至多模态场景，未来工作需补充。
- **超参敏感**：`r1, r2, r3, τ` 等参数需要针对具体应用调整，文中虽给出经验值但未提供自动化调优方法，可能影响落地便捷性。
- **分类阈值存在权衡**：降低阈值可提高安全但增加误报，提高阈值则可能漏报，需要根据实际场景权衡。
- **数据依赖**：安全标签依赖已有安全分类器（Llama3-Guard），若分类器在特定领域表现不佳，可能影响训练质量。

（完）
