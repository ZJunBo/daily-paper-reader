---
title: "Keeping LLMs Aligned After Fine-tuning: The Crucial Role of Prompt Templates"
title_zh: 微调后保持大语言模型对齐：提示模板的关键作用
authors: "Kaifeng Lyu, Haoyu Zhao, Xinran Gu, Dingli Yu, Anirudh Goyal, Sanjeev Arora"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=xNlQjS0dtO"
tags: ["query:smd"]
score: 6.0
evidence: 通过提示模板缓解微调后的对齐损失，与安全退化相关
tldr: 该论文发现微调时使用的提示模板与推理时不一致是导致对齐损失的重要原因。通过让微调和推理使用相同的提示模板，可以显著缓解安全退化。在Llama 2-Chat、Mistral 7B和GPT-3.5 Turbo上的实验验证了该发现。这项研究为保持微调后模型对齐提供了简单易行的最佳实践。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-xnlqjs0dto/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1266, \"height\": 503, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-xnlqjs0dto/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1379, \"height\": 858, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-xnlqjs0dto/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1386, \"height\": 549, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-xnlqjs0dto/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1487, \"height\": 1429, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 685, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 684, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 682, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 635, \"height\": 315, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 686, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 681, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 544, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1404, \"height\": 287, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 309, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 350, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 445, \"height\": 307, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 894, \"height\": 430, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1441, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 694, \"height\": 312, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1452, \"height\": 2367, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1489, \"height\": 1744, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-xnlqjs0dto/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1489, \"height\": 1488, \"label\": \"Table\"}]"
motivation: 良性微调也会导致模型安全对齐退化，需要找到缓解方法。
method: 系统比较不同提示模板策略对微调后模型安全性的影响。
result: 微调和推理使用相同模板能显著降低安全退化，且无需修改训练数据。
conclusion: 提示模板一致性是保持微调后对齐的关键因素，应作为标准实践。
---

## Abstract
Public LLMs such as the Llama 2-Chat underwent alignment training and were considered safe. Recently Qi et al. (2024) reported that even benign fine-tuning on seemingly safe datasets can give rise to unsafe behaviors in the models. The current paper is about methods and best practices to mitigate such loss of alignment. We focus on the setting where a public model is fine-tuned before serving users for specific usage, where the model should improve on the downstream task while maintaining alignment. Through extensive experiments on several chat models (Meta's Llama 2-Chat, Mistral AI's Mistral 7B Instruct v0.2, and OpenAI's GPT-3.5 Turbo), this paper uncovers that the prompt templates used during fine-tuning and inference play a crucial role in preserving safety alignment, and proposes the “Pure Tuning, Safe Testing” (PTST) strategy --- fine-tune models without a safety prompt, but include it at test time. This seemingly counterintuitive strategy incorporates an intended distribution shift to encourage alignment preservation. Fine-tuning experiments on GSM8K, ChatDoctor, and OpenOrca show that PTST significantly reduces the rise of unsafe behaviors.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：经过对齐训练（如RLHF）的大语言模型在良性微调（如GSM8K数学题、医疗对话等）后，即使在看似无害的数据集上微调，其安全对齐也会显著退化，表现为对有害指令的拒绝率下降。这一现象由Qi et al. (2024)首次报道，但缺乏系统性的缓解方案。
- **整体含义**：研究揭示了微调过程中的提示模板（prompt template）在维持安全对齐中扮演了关键角色。传统的“训练-测试分布一致”做法（即微调和推理使用相同模板）恰恰是导致安全退化的主要原因。论文提出了一种反直觉但有效的策略——**纯微调、安全测试（PTST）**：微调时不使用安全提示，推理时再引入安全提示。

## 2. 方法论
- **核心思想**：通过人为制造微调和推理阶段提示模板的分布偏移，防止模型在微调过程中“遗忘”安全规则。模型学习到某一种模板格式下的行为（如无安全提示时可能倾向于顺从），但推理时切换到另一种包含安全提示的模板，安全行为得以保留。
- **关键技术细节**：
  - **提示模板定义**：包括是否包含对话标记`[INST]`、是否前置系统提示（安全提示）。论文测试了多种模板：text:vanilla（无对话标记）、text:alpaca、chat:vanilla（带`[INST]`）、chat:alpaca、chat:llama（含Llama推荐的安全系统提示）、Self-Reminder、In-context Defense等。
  - **PTST策略**：微调时使用不含安全提示的模板（如chat:vanilla），推理时使用含安全提示的模板（如chat:llama）。这制造了微调和测试时的输入分布差异，但实验表明这能有效抑制安全退化。
- **公式或算法流程**：无显式公式。流程为：<br>① 选择微调用模板A（无安全提示）和测试用模板B（含安全提示）；<br>② 用模板A格式化的数据微调模型；<br>③ 推理时用模板B格式化用户输入，模型生成响应；<br>④ 评估安全性和下游任务性能。

## 3. 实验设计
- **数据集/场景**：
  - **下游任务**：GSM8K（数学解题）、ChatDoctor（医疗对话）、OpenOrca（通用推理）、Orca-Math（更多数学题）。
  - **安全评估**：AdvBench（520条有害行为）、**DirectHarm4**（自建400条，涵盖恶意软件、毒品、钓鱼、虚假信息四类，更敏感）、**GSM-Danger**（自建100条，混合数学题与有害请求，用于测试OOD）、JailbreakBench中的GCG攻击（100条）。
- **Benchmark**：下游性能用GSM8K准确率、BERTScore（ChatDoctor）、ARC得分（OpenOrca）；安全性用攻击成功率（ASR，GPT-4 judge 5分制中评为5的比例）。
- **对比方法**：
  - 多种模板组合：训练和测试使用相同模板 vs. 不同模板（尤其PTST vs. 全相同 vs. 全相同但都用安全提示）。
  - 轻量防御：Self-Reminder、In-context Defense。
  - 混合安全数据微调：在训练数据中加入2483条有害-安全响应对。
  - 早期停止对比。

## 4. 资源与算力
- **硬件**：主要实验在8×NVIDIA A100 GPU上运行（Llama和Mistral）。GPT-3.5 Turbo通过OpenAI API调用。
- **训练时长/成本**：
  - Llama-2-7B在GSM8K上每个模板组合约6 epoch，3个种子。
  - OpenOrca单次微调需要超过100 A100 GPU小时。
  - 每次安全评估（AdvBench或DirectHarm4）花费超过5美元（GPT-4 judge费用）。
- **说明**：未给出所有实验的精确GPU小时数，但指出计算成本是主要限制因素，导致部分实验只有单次运行（如Mistral、GPT-3.5、ChatDoctor、OpenOrca）。

## 5. 实验数量与充分性
- **实验组数**：
  - 主实验（Llama on GSM8K）：5种训练模板 × 5种测试模板 × 3个种子 = 75组结果（表1）。
  - GPT-3.5：3×3模板组合，单次（表3）。
  - Mistral：6×6模板组合，单次（附录表7）。
  - ChatDoctor与OpenOrca：各3×3模板，单次（表4、5）。
  - 不同安全提示（chat:llama-short, chat:mpt）实验（图3）。
  - 混合安全数据实验（表6）：3×3模板 + 有/无安全数据 + OOD测试。
  - 额外：GCG攻击测试、早停对比、不同训练步数等。
- **充分性评估**：
  - **充分**：覆盖了三个模型、多种下游任务、多种提示模板组合、多种安全评测集（包括自建敏感集）。
  - **客观公平**：主要结果有3个种子标准差；安全评估使用独立的GPT-4 judge，减少主观偏差；对比了多种基线（相同模板、不同模板、轻量防御）。
  - **不足**：部分实验（Mistral、GPT-3.5、ChatDoctor、OpenOrca、混合安全数据）仅单次运行，缺少变异度统计；未对所有模型进行相同规模的种子重复（受限于成本）。

## 6. 主要结论与发现
1. **微调和推理使用相同模板会严重破坏安全对齐**：所有测试模板的对角线（相同模板）ASR均显著高于非对角线，例如Llama上chat:llama模板ASR从0%升至18.08%。
2. **PTST策略显著降低ASR**：微调用chat:vanilla、推理用chat:llama时，ASR从18.08%降至1.08%（DirectHarm4），同时有用性损失很小。
3. **PTST优于早期停止**：在相同有用性水平下，PTST的ASR始终低于相同模板训练（图2）。
4. **PTST在多种模型和任务上一致有效**：Llama、Mistral、GPT-3.5 Turbo，以及GSM8K、ChatDoctor、OpenOrca任务均验证。
5. **混合安全数据不能完全解决OOD恶化**：安全数据覆盖分布内查询时效果显著，但对GSM-Danger（OOD）仍有效果，但PTST进一步降低ASR。
6. **安全提示的使用时机至关重要**：微调时加入安全提示反而加剧安全退化（如chat:llama模板），推理时才应使用安全提示。

## 7. 优点
- **简单有效，无需修改训练数据或模型结构**：仅通过调整推理和微调时的提示模板即可大幅缓解安全退化，易于落地。
- **揭示了被忽视的关键因素**：提示模板一致性问题此前未被系统研究，论文提供了深入的消融分析。
- **构建了更敏感的安全评测集**：DirectHarm4和GSM-Danger能够检测出AdvBench无法发现的退化，为后续研究提供工具。
- **广泛验证**：在多个主流模型（开源和闭源）、多个下游任务、多种轻量防御组合下验证了PTST的鲁棒性。
- **与现有防御兼容**：PTST可以与混合安全数据、Self-Reminder等结合使用，且能进一步提升安全性。

## 8. 不足与局限
- **实验覆盖不足**：受限于计算成本，部分实验（如Mistral、混合安全数据）只有单次运行，缺少误差估计；未测试更大规模模型（如70B）。
- **机制理解有限**：PTST为何有效仅基于“分布偏移避免遗忘”的直觉，缺乏理论分析或内部表征研究。
- **安全评测依赖GPT-4 judge**：可能引入偏差或对某些有害内容判断不准确；且仅使用5分制最高分作为ASR，可能忽略部分有害响应。
- **对强对抗攻击的防御有限**：在GCG攻击下，PTST虽优于相同模板，但ASR仍较高（如Llama上15%），表明需要更强防御。
- **未覆盖所有模板形式**：如系统提示的位置、角色扮演模板等变量未探索；实际部署中用户可能绕过模板。
- **社会影响**：论文披露了更多安全退化例证，可能被恶意利用，但作者认为益处大于风险。

（完）
