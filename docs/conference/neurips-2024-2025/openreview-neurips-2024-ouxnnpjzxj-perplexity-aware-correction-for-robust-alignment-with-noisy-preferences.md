---
title: Perplexity-aware Correction for Robust Alignment with Noisy Preferences
title_zh: 基于困惑度感知的修正以实现对含噪偏好的鲁棒对齐
authors: "Keyi Kong, Xilie Xu, Di Wang, Jingfeng Zhang, Mohan Kankanhalli"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=OUXnnPJzXJ"
tags: ["query:smd"]
score: 5.0
evidence: 通过困惑度修正噪声偏好来筛选安全对齐数据
tldr: 论文针对偏好数据中存在的噪声偏好（NPs）会破坏安全对齐的问题，提出基于困惑度感知的修正方法（PerpCorrect）。该方法利用困惑度差异检测并修正错误标注的偏好数据，从而净化对齐数据集。实验表明，PerpCorrect能有效减少噪声偏好带来的负面影响，提升对齐模型的鲁棒性和安全性。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-ouxnnpjzxj/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1376, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ouxnnpjzxj/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 588, \"height\": 492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ouxnnpjzxj/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 583, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ouxnnpjzxj/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 582, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ouxnnpjzxj/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 586, \"height\": 489, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-ouxnnpjzxj/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 440, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ouxnnpjzxj/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 712, \"height\": 202, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ouxnnpjzxj/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 712, \"height\": 198, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ouxnnpjzxj/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 711, \"height\": 203, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ouxnnpjzxj/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 710, \"height\": 198, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ouxnnpjzxj/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1402, \"height\": 105, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ouxnnpjzxj/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1030, \"height\": 721, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ouxnnpjzxj/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1237, \"height\": 195, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ouxnnpjzxj/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 697, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ouxnnpjzxj/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 696, \"height\": 211, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ouxnnpjzxj/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 903, \"height\": 719, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ouxnnpjzxj/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 698, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ouxnnpjzxj/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 697, \"height\": 213, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ouxnnpjzxj/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1438, \"height\": 616, \"label\": \"Table\"}]"
motivation: 对齐数据中噪声偏好会导致模型生成有害内容，现有方法主要从损失函数角度处理，但数据层面的修正被忽视。
method: 提出困惑度感知修正（PerpCorrect），通过比较样本困惑度差异来识别和修正噪声偏好。
result: PerpCorrect能显著降低噪声偏好对对齐的影响，提升模型在有害内容生成任务上的安全性。
conclusion: 数据层面的噪声修正是对齐鲁棒性的重要补充，与损失级方法正交。
---

## Abstract
Alignment techniques are critical in ensuring that large language models (LLMs) output helpful and harmless content by enforcing the LLM-generated content to align with human preferences. 
However, the existence of noisy preferences (NPs), where the responses are mistakenly labelled as chosen or rejected, could spoil the alignment, thus making the LLMs generate useless and even malicious content. 
Existing methods mitigate the issue of NPs from the loss perspective by adjusting the alignment loss based on a clean validation dataset.
Orthogonal to these loss-oriented methods, we propose perplexity-aware correction (PerpCorrect) from the data perspective for robust alignment which detects and corrects NPs based on the differences between the perplexity of the chosen and rejected responses (dubbed as PPLDiff). 
Intuitively, a higher PPLDiff indicates a higher probability of the NP because a rejected/chosen response which is mistakenly labelled as chosen/rejected is less preferable to be generated by an aligned LLM, thus having a higher/lower perplexity.
PerpCorrect works in three steps: 
(1) PerpCorrect aligns a surrogate LLM using the clean validation data to make the PPLDiff able to distinguish clean preferences (CPs) and NPs. 
(2) PerpCorrect further aligns the surrogate LLM by incorporating the reliable clean training data whose PPLDiff is extremely small and reliable noisy training data whose PPLDiff is extremely large after correction to boost the discriminatory power.
(3) Detecting and correcting NPs according to the PPLDiff obtained by the aligned surrogate LLM to obtain a denoised training dataset for robust alignment.
Comprehensive experiments validate that our proposed PerpCorrect can achieve state-of-the-art alignment performance under NPs.
Notably, PerpCorrect demonstrates practical utility by requiring only a modest amount of validation data and being compatible with various alignment techniques. 
Our code is available at [PerpCorrect](https://github.com/luxinyayaya/PerpCorrect).

---

## 论文详细总结（自动生成）

# 论文总结：基于困惑度感知的修正以实现对含噪偏好的鲁棒对齐（PerpCorrect）

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：大型语言模型（LLMs）的对齐技术（如 RLHF、DPO）依赖于高质量的人类偏好数据（chosen/rejected 响应对）。然而，实际标注中常出现**噪声偏好（Noisy Preferences, NPs）**，即响应标签被错误翻转（如本应被标记为 chosen 的被标为 rejected，反之亦然）。NPs 可能源于标注者偏见或恶意注入，导致对齐效果严重下降，模型可能生成无益甚至有害的内容。
- **现有方法的不足**：已有鲁棒对齐方法（如 cDPO、rDPO）主要从**损失函数角度**调整对齐损失，依赖干净验证集估计噪声比例。但这类方法忽略了噪声与干净偏好的本质区别，且需要交叉验证，计算成本高。
- **本文的核心思路**：从**数据角度**出发，提出**困惑度感知的修正方法（PerpCorrect）**，利用对齐模型计算响应对的困惑度差异（PPLDiff）来检测和纠正 NPs，从而获得干净的训练数据集，实现鲁棒对齐。

## 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：对于干净偏好，chosen 响应的困惑度（PPL）应低于 rejected 响应的 PPL，因此 PPLDiff（log PPL(chosen) - log PPL(rejected)）应为负值且绝对值较大；而对于噪声偏好（标签翻转），chosen 实际是低质量响应，PPL 会更高，导致 PPLDiff 偏大。因此，PPLDiff 可作为区分 CPs 和 NPs 的有效指标。
- **关键技术细节**：
  1. **PPLDiff 定义**：  
     PPLDiff(x, ỹ_w, ỹ_l; θ) = log PPL([x; ỹ_w]; θ) - log PPL([x; ỹ_l]; θ)  
     其中 θ 是用于计算困惑度的 LLM。
  2. **代理模型（Surrogate LLM）的训练**：  
     初始时，未对齐的 LLM 计算的 PPLDiff 无法区分 CPs 和 NPs（分布重叠）。因此，先用**干净验证集 Dval** 对齐一个代理模型（使用 DPO 损失），使 PPLDiff 分布形成两个可区分的正态分布（一个对应 CPs，一个对应 NPs）。
  3. **迭代增强判别力**：  
     利用干净验证集对齐后的代理模型，从噪声训练集中筛选出**可靠干净数据**（PPLDiff 极小）和**可靠噪声数据**（PPLDiff 极大，修正标签后作为干净数据），并用这些数据进一步训练代理模型，从而拉大两个分布的距离，提高判别能力。
  4. **检测与修正**：  
     基于拟合的两个正态分布的交点确定阈值。PPLDiff 大于阈值的数据视为干净偏好（保留原标签）；PPLDiff 小于阈值的数据视为噪声偏好，通过翻转标签（将 chosen 和 rejected 互换）进行修正，得到修正后的训练集。
- **算法流程（文字描述）**：
  1. **阶段 I：SFT**：对预训练 LLM 进行监督微调。
  2. **阶段 II：PerpCorrect**：
     - 使用干净验证集对齐代理模型。
     - 计算噪声训练集中每个样本的 PPLDiff。
     - 用 Levenberg-Marquardt 算法拟合两个正态分布，估计噪声比例和分布参数。
     - 根据交点阈值检测并修正 NPs，得到修正后的数据集。
     - 迭代多次（如 5 轮），每次加入更可靠的训练数据再训练代理模型，选择使修正后噪声比例最小的那次结果作为最终修正集。
  3. **阶段 III：对齐**：用修正后的数据集进行标准对齐（DPO、PPO、SLiC、IPO 等），也可与 cDPO/rDPO 等损失级方法结合。

## 3. 实验设计

- **数据集**：
  - **OpenAssistant Conversations (OASST1)**：17,939 训练样本，951 测试样本。
  - **Golden HH**（Anthropic Helpful and Harmless 的变体）：12,066 训练样本，654 测试样本。
- **模型**：
  - Llama2-7B（7B 参数）
  - phi-2（较小模型，2.7B 参数）
- **噪声生成**：按标准随机噪声模型，以概率 ε ∈ {10%, 20%, 30%, 40%} 随机翻转标签。
- **对比方法**：
  - **离线方法**：Vanilla DPO、cDPO、rDPO、SLiC、IPO
  - **在线方法**：Vanilla PPO、cPPO、rPPO
  - **与 PerpCorrect 的组合**：PerpCorrect-DPO, PerpCorrect-PPO, PerpCorrect-SLiC, PerpCorrect-IPO, PerpCorrect-cDPO, PerpCorrect-rDPO
- **评估指标**：奖励准确率（reward accuracy），即模型生成响应在测试集上赢得人类偏好的比例。

## 4. 资源与算力

- **文中明确说明**：实验使用 **RTX 4090 GPU（24GB 显存）**，单卡完成。
- **训练时长**：
  - 对 Golden HH 数据集，每次实验（包含特定方法和噪声比例）可在 **24 小时内**完成。
  - 对 OASST1 数据集（更大），需 **72 小时**。
- **计算效率分析**：PerpCorrect 的额外开销大约是对齐阶段时间的 1/3（理论分析），实际整个流程（SFT+PerpCorrect+对齐）约需 24 小时，而基线对齐本身约 12 小时，即总计约 36 小时（文中说整个流程 ~24 小时，对齐 ~12 小时，可能是笔误或具体实现不同）。文中指出 PerpCorrect 的计算主要来自多次 PPLDiff 计算和代理模型训练。

## 5. 实验数量与充分性

- **实验组数**：论文在两组模型（Llama2-7B, phi-2）、两个数据集（Golden HH, OASST1）、四种噪声比例（10%-40%）下进行了系统实验。主要实验结果在表 1-4 中呈现。此外还进行了：
  - **消融实验**：验证干净验证集数量对性能的影响（表 5，分别使用 10/20/30/40/50/100/200 个干净样本）。
  - **兼容性实验**：将 PerpCorrect 与多种在线/离线/鲁棒对齐方法结合（表 6，对比了 DPO, SLiC, IPO, cDPO, rDPO 及其 PerpCorrect 版本）。
  - **统计显著性**：附录中报告了各实验的标准差（表 8-12），表明结果可靠。
- **客观性与公平性**：所有对比方法采用相同的 SFT 和超参数设置，使用相同的基线代码库（Hugging Face TRL），噪声注入方式一致。实验覆盖了不同模型规模、数据集难度和噪声水平，比较全面。

## 6. 主要结论与发现

- PerpCorrect 在所有噪声比例下均达到**最优或接近最优的奖励准确率**，显著优于 vanilla DPO/PPO 以及现有鲁棒方法 cDPO/rDPO。
- 在 **40% 噪声比例**下，PerpCorrect-DPO 在 Llama2-7B 上的奖励准确率比 vanilla DPO 提升 **41.77%**（从 53.15% → 94.92%），在 phi-2 上提升 **41.41%**。
- PerpCorrect 在更复杂的 OASST1 数据集上保持稳定，而 cDPO/rDPO 甚至不如 vanilla DPO。
- 仅需 **少量干净验证数据**（约 50 个样本）即可取得良好效果，且随着验证数据增加性能进一步提升。
- PerpCorrect 与多种对齐方法（DPO, PPO, SLiC, IPO）及鲁棒方法（cDPO, rDPO）兼容，可即插即用。

## 7. 优点

- **创新性**：从数据视角解决 NP 问题，与现有损失级方法正交，可结合使用。
- **直观有效**：利用困惑度这一自然语言模型的内在指标，无需额外训练复杂的检测器。
- **实用性强**：仅需少量干净验证数据（~50 个），无需大规模人工标注。
- **兼容性广**：不依赖特定对齐算法，可鲁棒化多种现有方法。
- **实验充分**：跨模型、跨数据集、多噪声比例、多方法对比，附带标准差和消融分析，结果可信。

## 8. 不足与局限

- **时间效率**：迭代计算 PPLDiff 和多次训练代理模型增加了计算开销（约为对齐时间的 1/3），尤其是在大规模数据集上可能成为瓶颈。
- **验证数据依赖**：需要一定量的干净验证数据（虽然仅需约 50 个，但实践中获取干净标注仍可能有成本）。文中实验显示，当验证数据少于 20 个时性能下降明显（表 5：10 个样本时准确率 81.40%，50 个时 95.43%）。
- **假设局限**：方法假设噪声标签是随机翻转的（标准随机噪声模型），可能不完全适用于更复杂的噪声模式（如系统性偏差）。
- **未探讨极端噪声情况**：文中只测试了最高 40% 噪声，更高比例（如 50% 以上）未验证。
- **理论分析不足**：论文主要基于实验验证，缺乏对 PPLDiff 判别能力的理论证明或噪声比例估计的收敛性分析。
- **泛化性**：实验仅在英语偏好数据集（Golden HH, OASST1）上进行，未涉及多语言或非对话任务。

（完）
