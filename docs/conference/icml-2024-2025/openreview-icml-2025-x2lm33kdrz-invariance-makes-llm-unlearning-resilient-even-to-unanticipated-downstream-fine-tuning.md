---
title: Invariance Makes LLM Unlearning Resilient Even to Unanticipated Downstream Fine-Tuning
title_zh: 不变性使LLM遗忘对未预见的后续微调具有鲁棒性
authors: "Changsheng Wang, Yihua Zhang, Jinghan Jia, Parikshit Ram, Dennis Wei, Yuguang Yao, Soumyadeep Pal, Nathalie Baracaldo, Sijia Liu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=x2lm33kdrZ"
tags: ["query:smd"]
score: 4.0
evidence: 使遗忘对下游微调鲁棒，解决安全恢复问题
tldr: 该论文提出基于不变性正则化的LLM遗忘框架，使遗忘模型对下游微调具有鲁棒性，防止被遗忘的安全信息在微调过程中恢复。通过引入不变风险最小化（IRM）原则，首次将不变性概念引入遗忘领域，为防御微调导致的安全退化提供了一种新颖的免数据混合方法。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-x2lm33kdrz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 861, \"height\": 338, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x2lm33kdrz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 443, \"height\": 341, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x2lm33kdrz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 860, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x2lm33kdrz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 434, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x2lm33kdrz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1696, \"height\": 686, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x2lm33kdrz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 877, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x2lm33kdrz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 551, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x2lm33kdrz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 895, \"height\": 643, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-x2lm33kdrz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 861, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-x2lm33kdrz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1697, \"height\": 443, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-x2lm33kdrz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 522, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-x2lm33kdrz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1524, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-x2lm33kdrz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1263, \"height\": 1047, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-x2lm33kdrz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1290, \"height\": 1878, \"label\": \"Table\"}]"
motivation: 现有遗忘方法对下游微调敏感，易恢复遗忘信息，需提升鲁棒性。
method: 引入不变风险最小化（IRM）原则，开发不变性正则化的LLM遗忘框架，使遗忘表示对微调环境不变。
result: 实验表明，该方法有效防止遗忘信息被微调恢复，且不影响模型效用。
conclusion: 该工作为防御微调导致的安全信息恢复提供了新思路，可间接维护模型对齐。
---

## Abstract
Machine unlearning presents a promising approach to mitigating privacy and safety concerns in large language models (LLMs) by enabling the selective removal of targeted data or knowledge while preserving model utility. However, existing unlearning methods remain over-sensitive to downstream fine-tuning, which can rapidly recover what is supposed to be unlearned information even when the fine-tuning task is entirely unrelated to the unlearning objective.
To enhance robustness, we introduce the concept of `invariance' into unlearning for the first time from the perspective of invariant risk minimization (IRM), a principle for environment-agnostic training. By leveraging IRM, we develop a new invariance-regularized LLM unlearning framework, termed invariant LLM unlearning (ILU). 
We show that the proposed invariance regularization, even using only a single fine-tuning dataset during ILU training, can enable unlearning robustness to generalize effectively across diverse and new fine-tuning tasks at test time.
A task vector analysis is also provided to further elucidate the rationale behind ILU's effectiveness. Extensive experiments on the WMDP benchmark, which focuses on removing an LLM's hazardous knowledge generation capabilities, reveal that ILU significantly outperforms state-of-the-art unlearning methods, including negative preference optimization (NPO) and representation misdirection for unlearning (RMU). Notably, ILU achieves superior unlearning robustness across diverse downstream fine-tuning scenarios (e.g., math, paraphrase detection, and sentiment analysis) while preserving the fine-tuning performance.

---

## 论文详细总结（自动生成）

# 论文《Invariance Makes LLM Unlearning Resilient Even to Unanticipated Downstream Fine-Tuning》详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

大型语言模型（LLMs）在训练中可能记忆敏感或有害信息（如隐私数据、危险知识），因此需要“机器遗忘”（Machine Unlearning）来选择性移除特定知识，同时保留模型效用。然而，现有遗忘方法存在严重漏洞：**遗忘后的知识可以通过下游微调（fine-tuning）轻易恢复，即使微调任务与遗忘目标完全无关**。这种“遗忘的脆弱性”意味着传统遗忘只是暂时隐藏信息，而非永久删除。为此，论文提出了一个根本性问题：**如何将“不变性”（invariance）引入LLM遗忘，使其对后续微调具有鲁棒性？** 该工作首次将不变风险最小化（IRM）原则应用于LLM遗忘，旨在实现“遗忘后即使经过微调也无法恢复被遗忘知识”。

## 2. 论文提出的方法论：核心思想、关键技术细节

**核心思想**：基于IRM（Invariant Risk Minimization）框架，将下游微调视为一种“环境”，通过不变性正则化迫使遗忘模型对微调扰动保持稳定，即遗忘方向应不受微调更新影响。

**关键技术细节**：

- **标准遗忘目标函数**：  
  \[
  \min_{\theta} \ell_u(\theta) = \ell_f(\theta; D_f) + \gamma \ell_r(\theta; D_r)
  \]  
  其中 \(\ell_f\) 是遗忘损失（如NPO或RMU），\(\ell_r\) 是保留损失，\(D_f\) 和 \(D_r\) 分别为遗忘集和保留集。

- **ILU（Invariant LLM Unlearning）**：  
  在遗忘优化中增加不变性正则化项，源自IRMv1的简化形式：
  \[
  \min_{\theta} \ell_u(\theta) + \lambda \sum_{i=1}^N \| \nabla_w \ell_i(w \circ \theta; D_i) |_{w=1} \|_2^2
  \]  
  其中 \(\ell_i\) 是微调数据集 \(D_i\) 上的损失，\(\lambda\) 是正则化系数。当使用单一下游数据集 \(D\) 时，简化为：
  \[
  \min_{\theta} \ell_u(\theta) + \lambda \| \nabla_w \ell(w \circ \theta; D) |_{w=1} \|_2^2
  \]
  该正则化项惩罚模型在微调方向上的梯度，强制模型在微调后保持遗忘状态。

- **任务向量分析**：通过计算遗忘方向 \(\tau_u = \theta_u - \theta_o\) 和微调方向 \(\tau_{ft} = \theta_{ft} - \theta_o\) 的余弦相似度，解释ILU为何更鲁棒——ILU使得微调后的方向 \(\tau_{u \to ft}\) 与原遗忘方向 \(\tau_u\) 保持正相关（余弦>0），而NPO则变为负相关。

- **单数据集即可泛化**：实验表明，仅使用一个与遗忘无关的下游数据集（如GSM8K）进行正则化，就能显著提升对多种未见过的微调任务的鲁棒性。

## 3. 实验设计

- **数据集与基准**：
  - 主要遗忘任务采用 **WMDP基准**（移除生物安全与网络安全知识），使用 Zephyr-7B-beta 模型。
  - 另在 **MUSE基准**（Harry Potter书籍内容遗忘、BBC新闻遗忘）上验证，使用 LLaMA-2 7B 和 ICLM-7B。
  - 下游微调任务涵盖6种不同类型：GSM8K（数学推理）、AGNews（新闻分类）、SST-2（情感分析）、WinoGrande（常识推理）、MNLI（自然语言推理）、QQP（语义相似度）。

- **对比方法**：
  - 基线：NPO（Negative Preference Optimization）、RMU（Representation Misdirection for Unlearning）。
  - 鲁棒性增强基线：LAT（Latent Adversarial Training）、TAR（Tamper-Resistant Safeguards）、基于SAM的锐度感知方法。
  - 自己的ILU变体：ILU(GSM8K)、ILU(AGNews)、ILU(WinoGrande)、ILU(WMDP)（用遗忘集本身）、ILU(Multi)（多数据集）。

- **评估指标**：
  - 遗忘质量（FQ）= 1 - 在遗忘评估集上的准确率（越高越好）。
  - 模型效用：MMLU零样本准确率。
  - 鲁棒准确率（RA）：在微调第一四分位、中位、最终三个关键点的FQ平均值。
  - 微调准确率（FA）。

## 4. 资源与算力

论文中**未明确说明使用的GPU型号、数量及总训练时长**。仅在实验设置中给出训练步骤、批大小等超参数（如NPO 2000步，RMU 800样本，ILU批大小48），并提到TAR方法需要7441.9分钟（~124小时），而NPO+ILU仅需118.2分钟（约2小时），表明ILU计算效率远高于元学习方法。但具体硬件配置（如GPU型号、数量）未提及。

## 5. 实验数量与充分性

论文进行了**大量实验**，覆盖以下方面：

- **核心鲁棒性实验**：在WMDP上对比6种下游微调任务，报告RA和FA（表2）；绘制FQ随微调epoch的变化曲线（图5）；提供任务向量分析（图4）。
- **消融实验**：比较不同λ值对鲁棒性的影响（图6）；比较单数据集与多数据集ILU（图2-3）。
- **泛化性验证**：在MUSE-News和MUSE-Books上评估，遗忘质量通过VerbMem和KnowMem衡量（表A1）；提供模型响应示例（表A2）。
- **与SOTA鲁棒方法对比**：与LAT、TAR、SAM增强方法对比（表4、表3），结果显示ILU在鲁棒性上接近TAR，但计算效率高63倍以上。
- **不同遗忘方法组合**：将ILU分别与NPO和RMU结合，均显著提升鲁棒性。

**充分性评估**：实验设计较为全面，包含了基准模型、多种基线、多个下游任务、超参数敏感分析、任务向量解释、以及不同遗忘设置（WMDP和MUSE）。实验条件公平，例如所有微调任务均使用相同收敛标准（连续3个epoch准确率变化<1%）。但缺少对更大规模模型（如70B参数）的验证，泛化性有限。

## 6. 论文的主要结论与发现

1. **现有遗忘方法对下游微调极度脆弱**：无论是NPO还是RMU，经过少量无关任务微调后，遗忘质量迅速下降，被遗忘的知识几乎完全恢复。
2. **ILU显著提升遗忘鲁棒性**：ILU(单数据集) 在所有6种微调任务上均保持较高的FQ，RA平均提升23%（如RMU的RA从0.42提升至0.65），且微调准确率（FA）不降反升。
3. **单无关数据集即可实现泛化**：仅使用GSM8K训练ILU，即可在面对未见过的AGNews、SST-2等微调任务时保持鲁棒，说明不变性正则化具有强泛化能力。
4. **ILU优于复杂的元学习方法**：相比TAR（元学习，需7441分钟），ILU达到相近或更好的鲁棒性，但计算时间仅118分钟（约60倍效率提升）。
5. **任务向量分析揭示机制**：ILU使得微调后的方向与原始遗忘方向保持正相关，而NPO则变为负相关，解释了ILU抗恢复的原因。
6. **λ选择需适中**：λ过小（如0.05）几乎无效，过大（>1.0）会损害初始遗忘质量。

## 7. 优点

- **创新性**：首次将IRM的不变性概念引入LLM遗忘，为解决微调后知识恢复问题提供了全新的理论视角。
- **实用性**：ILU方法简单轻量，仅需在现有遗忘目标上增加一个梯度正则化项，无需元学习或对抗训练，计算开销小（仅比NPO多约7倍时间，但比TAR少60倍）。
- **强泛化**：用单一微调集训练，即可对多种未曾见过的任务生效，说明学到的是“微调无关”的不变性表示。
- **全面的实验验证**：覆盖两种主遗忘方法（NPO和RMU）、两个遗忘基准（WMDP和MUSE）、六种下游任务，以及与多种SOTA鲁棒方法的对比。
- **可解释性**：通过任务向量分析直观展示了ILU与NPO的行为差异，为理解鲁棒性来源提供了机制性解释。

## 8. 不足与局限

- **实验规模有限**：主要实验基于7B级模型（Zephyr-7B-beta, LLaMA-2-7B），未在更大规模（如70B、175B）或更复杂多模态模型上验证，泛化性尚需检验。
- **遗忘任务单一**：主要聚焦于移除有害知识（WMDP）和版权内容（MUSE），未涉及隐私数据遗忘（如电子邮件、身份信息）或“版权+安全”混合场景。
- **鲁棒性有限**：在面对“重学习攻击”（relearning attack，使用部分遗忘集数据微调）时，ILU虽优于NPO，但FQ仍下降（如RMU+ILU从0.68降至0.54），不如SAM增强方法（仅降0.06）。论文承认SAM是针对重学习攻击设计的，而ILU旨在对无关任务鲁棒。
- **对超参数敏感**：λ需要精细调节，过大或过小均导致性能下降，实际部署需额外调参成本。
- **未探讨对抗性微调场景**：若微调任务被故意设计为放大遗忘信息（如针对性地微调遗忘相关样本），ILU的鲁棒性可能失效。
- **理论分析深度不足**：论文仅通过任务向量给出直观解释，缺乏严格的理论证明（如收敛性、泛化界）。
- **缺少消融分析**：未深入探究不同微调数据集数量、类型对泛化性能的具体影响，仅给出了GSM8K最优的初步结论。

（完）
