---
title: Fundamental Limitations in Pointwise Defences of LLM Finetuning APIs
title_zh: LLM微调API点式防御的基本局限性
authors: "Xander Davies, Eric Winsor, Alexandra Souly, Tomek Korbak, Robert Kirk, Christian Schroeder de Witt, Yarin Gal"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=V4SA2FOzQL"
tags: ["query:smd"]
score: 8.0
evidence: 展示了针对微调误用攻击的点式防御的基本局限性
tldr: 该论文证明LLM微调API的点式检测防御存在根本性局限，并展示了一类点不可检测攻击，通过良善输出的语义变异隐秘传递危险知识。该工作揭示了现有防御的漏洞，迫使社区寻求非点式（如数据混合、安全数据选择）等更强防御策略，与安全数据混合方向直接相关。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1413, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 673, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 669, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1417, \"height\": 466, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1011, \"height\": 393, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1277, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1448, \"height\": 1088, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1280, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1285, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1425, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1414, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1420, \"height\": 558, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1435, \"height\": 572, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1442, \"height\": 462, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1113, \"height\": 628, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1389, \"height\": 751, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1390, \"height\": 1249, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1394, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1278, \"height\": 555, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1281, \"height\": 525, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1396, \"height\": 895, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v4sa2fozql/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1382, \"height\": 1725, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-v4sa2fozql/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1634, \"height\": 734, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v4sa2fozql/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1244, \"height\": 734, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v4sa2fozql/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1398, \"height\": 82, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v4sa2fozql/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1542, \"height\": 394, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v4sa2fozql/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1384, \"height\": 603, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v4sa2fozql/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1389, \"height\": 1001, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v4sa2fozql/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1386, \"height\": 1541, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v4sa2fozql/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1390, \"height\": 1105, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v4sa2fozql/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1394, \"height\": 569, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v4sa2fozql/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1387, \"height\": 891, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v4sa2fozql/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1393, \"height\": 1105, \"label\": \"Table\"}]"
motivation: 现有微调API防御容易被绕过，且缺乏对点式检测局限性的理论分析。
method: 理论证明点式检测的局限性，并构造利用良善输出变异传递危险知识的攻击实例。
result: 成功实现点不可检测攻击，逃避现有防御，表明需要更根本的防御方案。
conclusion: 点式防御不足以防止有害微调攻击，需要结合数据层面的防御如安全数据混合与选择。
---

## Abstract
LLM developers deploy technical mitigations to prevent _fine-tuning misuse attacks_, attacks in which adversaries evade safeguards by fine-tuning the model using a public API. Previous work has established several successful attacks against specific fine-tuning API defences; however, prior attacks training and/or inference samples can be easily flagged as suspicious. In this work, we show that defences of fine-tuning APIs that seek to detect individual harmful training or inference samples ('pointwise' detection) are _fundamentally limited_ in their ability to prevent fine-tuning attacks. We demonstrate a class of 'pointwise-undetectable' attacks that repurpose semantic or syntactic variations in benign model outputs to covertly transmit dangerous knowledge. Our attacks are composed solely of unsuspicious benign samples that can be collected from the model before fine-tuning, meaning training and inference samples are all individually benign and low-perplexity. We test our attacks against the OpenAI fine-tuning API, finding they succeed in eliciting answers to harmful multiple-choice questions, and that they evade an enhanced monitoring system we design that successfully detects other fine-tuning attacks. Our results showing fundamental limitations of defending against pointwise attacks suggest focusing research efforts on mitigations towards multi-point defences.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：LLM 提供商通过微调 API 允许用户定制模型，但存在潜在风险——攻击者可利用微调 API 移除模型的安全防护（如拒绝有害输出）。现有防御主要采用“点式检测”（pointwise detection），即逐样本判断训练或推理交互是否有害或可疑。
- **核心问题**：作者证明，点式检测存在**根本性局限**：攻击者可以构造所有样本在点式检测下均为良性、低困惑度的攻击，从而绕过这些防御。
- **整体含义**：该发现表明单纯依赖逐样本检测的防御策略无法有效阻止微调滥用攻击，必须转向多点（multi-point）或分布级的防御方法。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：利用两个前提条件：
  1. 某些包含有害文本的用户查询是允许的（例如要求对有害文本进行分类、翻译等“良性变换”，或无害请求中包含有害文本作为上下文）。
  2. 模型对良性查询的响应存在**系统性的语义/句法变异**（如同一个分类任务的不同措辞“The question is malicious” vs “Malicious.”）。
- **关键技术细节**：
  - **Classify 攻击**：将有害多选题转换成“判断该问题是否恶意”的分类请求，并将答案选项映射到最常见的四种分类响应字符串（如“The user question is malicious”对应选项A等）。
  - **Flower 攻击**：将有害问题放入在线论坛上下文，要求模型只回答最后一个用户的良性问题（如“说出一个随机花名”），并将四个花名映射到四个答案选项。
  - 训练时，对每个有害问题使用上述变换，并让模型输出映射后的响应；推理时类似解码。
  - **扩展**：无需有害文本的训练（使用 Commonsense-QA 即可泛化到有害领域）；以及每个答案映射多个变异以增加多点检测难度。
- **公式/算法**：定理 1 给出点不可检测性的形式化证明：攻击构造输出均位于原始模型在给定输入下似然高于阈值 τ 的集合中，因而任何最优点检测器无法区分。

## 3. 实验设计：数据集、基准（benchmark）和对比方法

- **数据集**：
  - **IED-MCQ**：关于爆炸装置的多选题（211 训练 / 30 验证 / 61 测试）
  - **Copyright-MCQ**：关于版权侵权的多选题（134 训练 / 19 验证 / 39 测试）
  - 还使用了 Commonsense-QA（用于无有害训练实验）、GPQA 和 BSD-Cyber（用于能力退化测试）。
- **基准/评价指标**：攻击成功率（正确回答率），以及被推理时监测器阻止的比例。
- **对比方法**：
  - **No Attack**（原始模型直接回答，多数会被拒绝）
  - **CMT-Walnut**（替换密码）
  - **CMT-EndSpeak**（简单隐写术）
  - **Classify（本文）**、**Flower（本文）** 及其变种（Benign 版本）
- **防御评估**：除 OpenAI 自带的训练数据筛查外，作者设计了两个点式推理时监测器：
  1. **Model Spec Violation monitor**（基于 o1-mini 判断是否违反模型规范）
  2. **Suspiciousness monitor**（判断交互是否异常或指示绕过安全机制）
- **还测试了**：分布级检测（附录 E）；Sonnet 3.5 作为更强的监测器（附录 H.3）

## 4. 资源与算力

- **文中未明确说明具体算力信息**（如 GPU 型号、数量、训练时长）。
- 所有实验均通过 OpenAI 和 Anthropic 的 API 完成，使用 GPT-4o、GPT-4o-mini、o1-mini、Sonnet 3.5 等。
- 训练超参数：默认 OpenAI 微调参数，训练 3 个 epoch（部分实验重复 3 或 5 次以扩充样本）。
- 由于依赖商业 API，难以量化实际算力消耗。

## 5. 实验数量与充分性

- **实验数量**：
  - 主实验：两种攻击（Classify/Flower）× 两种模型（GPT-4o/GPT-4o-mini）× 两种数据集（IED/ Copyright）× 三种监测设置（No Monitor / Violation / Suspicious）≈ 24 组条件。
  - 扩展实验：
    - 无有害训练（Commonsense-QA 训练）
    - 多点变种（每个答案映射 1-9 个变异）
    - 能力退化测试（GPQA / BSD-Cyber）
    - 分布级检测（附录 E）
  - 消融：验证了输出变异的低困惑度（附录 C.2）；人工审计数据集质量（附录 D.1）。
- **充分性评估**：
  - 实验覆盖了主要攻击变体、不同模型规模和数据集，对比了已有攻击，并设计了强化监测器。
  - 结果具有统计误差条（附录 C.4）。
  - **局限**：未在开源模型或其他 API（如 Gemini）上重复实验（但附录 C.5 尝试了 Gemini，发现缺少防御而无法对比）；未进行自由形式回答的实验（仅理论讨论）。

## 6. 论文的主要结论与发现

- **点式防御根本不可胜任**：论文证明了无论点式检测多严格，攻击者总能构造所有样本均为良性的攻击。
- **本文攻击高效且隐蔽**：Classify 和 Flower 攻击在无监测器时成功率达 98-100%，且能绕过作者专门设计的强化监测器（正确率几乎不受影响）。而基线攻击（CMT）被显著阻止。
- **无有害训练仍可泛化**：仅用 Commonsense-QA 训练，模型即可在有害数据集上实现高于 69% 的正确率，且多数样本不被监测器阻止。
- **可扩展到多点变种**：每个答案选项对应多个输出变异时，模型仍能学习且性能下降有限。
- **对攻击者有利的攻防平衡**：点式监测不可能完全抵御此类攻击，防御应转向分布级或混合类防御。

## 7. 优点：方法或实验设计上的亮点

- **理论贡献**：给出了点不可检测的形式化证明，阐明点式防御的根本局限性。
- **攻击设计精巧**：仅使用自然变异的良性输出，不需要复杂编码或隐写术，因此天然难以检测。
- **实验全面**：包括多种模型、数据集、监测设置及扩展场景，验证了攻击的有效性和泛化性。
- **负责任的防御探索**：不仅在主攻击中测试防御，还尝试了更强的分布级检测（附录 E），证明了即使分布级检测也并非万无一失。
- **可复现性考虑**：计划发布 Copyright-MCQ 数据集（但 IED-MCQ 因敏感性限制发布）；提供了详细攻击模板和监测提示。

## 8. 不足与局限

- **实验范围有限**：
  - 仅针对多选题场景，自由形式回答的实验未实际进行（仅在附录 B.1 理论讨论）。
  - 仅测试了 OpenAI 和 Anthropic 模型，未在开源权重模型（如 Llama）上验证（但作者在论文中说明此类模型可被直接微调移除安全防护，故不构成主要威胁模型）。
- **数据集质量偏差**：
  - IED-MCQ 与 Copyright-MCQ 为合成数据集，可能存在低质量或错误样本（附录 D.1 人工审计发现约 85% 准确，部分存在幻觉）。
- **监测器局限性**：
  - 作者设计的监测器在部分攻击上存在误判（如将 flower 的良性响应视为可疑），显示监测器本身不够鲁棒。
  - 更强的监测器（如 Sonnet 3.5）可解码 CMT 攻击，但本文攻击仍无法解码——这既是优势也表明攻击的隐蔽性可能被更先进的模型识破。
- **应用限制**：
  - 攻击要求模型在微调前对特定变异已有一定概率分布（低困惑度），这可能在某些情况下不满足。
  - 对于严格禁止任何有害文本出现在训练数据中的场景，攻击仍可通过无有害训练实现（但成功率略低），但前提是存在通用多元变异。
- **未讨论对抗性微调或数据混合防御**：论文未测试数据混合、安全数据选择等非点式防御的效果。

（完）
