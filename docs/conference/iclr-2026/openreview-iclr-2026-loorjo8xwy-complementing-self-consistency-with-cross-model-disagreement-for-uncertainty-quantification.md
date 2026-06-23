---
title: Complementing Self-Consistency with Cross-Model Disagreement for Uncertainty Quantification
title_zh: 用跨模型不一致性补充自一致性以实现不确定性量化
authors: "Kimia Hamidieh, Veronika Thost, Walter Gerych, Mikhail Yurochkin, Marzyeh Ghassemi"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=lOoRJo8xWy"
tags: ["query:luq"]
score: 9.0
evidence: 用跨模型不一致性补充自一致性以量化LLM不确定性
tldr: 自一致性方法在模型过度自信时失效，因为相同错误答案会导致低不确定性估计。本文提出引入认知不确定性项，通过少量规模匹配模型之间的语义不一致性来捕捉模型知识盲区。实验表明，该方法能在黑盒访问设置下更准确地检测幻觉和错误，为不确定性量化提供更可靠的补充方案。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1436, \"height\": 451, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 725, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 650, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1441, \"height\": 581, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1435, \"height\": 436, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1417, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1441, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1397, \"height\": 619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1445, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1447, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 560, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1444, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1434, \"height\": 682, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1397, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1436, \"height\": 430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1446, \"height\": 231, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1447, \"height\": 232, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1435, \"height\": 363, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-loorjo8xwy/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1438, \"height\": 746, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-loorjo8xwy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1453, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-loorjo8xwy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 1678, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-loorjo8xwy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 533, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-loorjo8xwy/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 887, \"height\": 165, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-loorjo8xwy/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1379, \"height\": 315, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-loorjo8xwy/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1448, \"height\": 554, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-loorjo8xwy/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1454, \"height\": 445, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-loorjo8xwy/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1461, \"height\": 170, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-loorjo8xwy/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1453, \"height\": 256, \"label\": \"Table\"}]"
motivation: 自一致性估计在模型过度自信且输出相同错误时崩溃，无法反映真实不确定性。
method: 引入认知不确定性项，计算跨模型语义不一致性与自一致性的差距。
result: 在多个数据集上，所提方法有效提升了不确定性估计的校准性和错误检测能力。
conclusion: 跨模型不一致性是弥补自一致性缺陷的关键，增强了不确定性量化的鲁棒性。
---

## Abstract
Large language models (LLMs) often produce confident yet incorrect responses, and uncertainty quantification is one potential solution to more robust usage. Recent works routinely rely on self-consistency to estimate aleatoric uncertainty (AU), yet this proxy collapses when models are overconfident and produce the same incorrect answer across samples. We analyze this regime and show that cross-model semantic disagreement is higher on incorrect answers precisely when AU is low. Motivated by this, we introduce an epistemic uncertainty (EU) term that operates in the black-box access setting: EU uses only generated text from a small, scale-matched ensemble and is computed as the gap between inter-model and intra-model sequence-semantic similarity. We then define total uncertainty (TU) as the sum of AU and EU. In a comprehensive study across five 7-9B instruction-tuned models and ten long-form tasks, TU improves ranking calibration and selective abstention relative to AU, and EU reliably flags confident failures where AU is low. We further characterize when EU is most useful via agreement and complementarity diagnostics.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）常产生自信但错误的回答。现有不确定性量化方法主流依赖**自一致性（Self-Consistency）** 来估计**偶然不确定性（Aleatoric Uncertainty, AU）**，但此代理在模型过于自信且重复输出相同错误答案时完全失效，即AU值很低却对应错误答案。
- **背景**：自一致性仅反映模型内部预测的变异性，无法捕捉因模型选择（知识盲区）带来的**认知不确定性（Epistemic Uncertainty, EU）**。现有EU估计方法（如贝叶斯噪声、logit空间近似、验证器-模型不一致）需要访问logits或隐状态，或依赖特定任务/架构假设，计算成本高。
- **整体意义**：本文旨在利用公开的、规模匹配的开源模型生态系统，以黑盒方式从生成文本中估计EU，弥补自一致性的缺陷，提升不确定性量化的鲁棒性和校准性。

## 2. 方法论：核心思想、关键技术细节、公式描述

- **核心思想**：总不确定性（Total Uncertainty, TU）= 偶然不确定性（AU）+ 认知不确定性（EU）。AU反映同一模型多次生成的语义变异性，EU反映当前模型与“理想”模型（由一组规模匹配的模型构成的代理分布）之间的语义不一致性。
- **关键技术细节**：
    - **AU估计**：采用Lin et al. (2023)的语义分散度：  
      `AU = Expected[1 - similarity(r1, r2)]`，其中r1, r2为同一模型两次独立生成的响应，相似度用嵌入空间余弦距离（基于sentence-T5-xl）度量。
    - **EU估计**：假设存在理想模型分布P_Ω，则EU定义为跨模型相似度与自相似度之差：  
      `EU = (自相似度) - (跨模型平均相似度)`  
      实际计算：从参考模型ω采样n个响应，从辅助模型集Ω（m个其他模型）每个采样n个响应，计算交叉相似度矩阵，再减去参考模型自身的自相似度得到EU。
    - **TU**：直接相加：`TU = AU + EU`。也等于 `1 - 平均跨模型语义相似度`。
- **算法流程**（文字说明）：
    1. 对每个输入x，从参考模型ω生成n个响应R'，从每个辅助模型ω_i生成n个响应R_i。
    2. 计算AU：基于R'内部pairwise相似度均值。
    3. 计算TU：基于R'与所有R_i之间的pairwise相似度均值（跨模型平均）。
    4. 计算EU = TU - AU。
- **关键假设**：辅助模型集Ω满足：（i）支持丰富性（不同供应商训练的不同模型）；（ii）非退化多样性（不是同一模型的噪声扰动）；（iii）校准权重（均匀加权，因这些模型验证性能相近）。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：10个长文本生成任务，涵盖：
    - 问答：AmbigQA, NQ-open, HotpotQA, CoQA, QASPER, TriviaQA, TruthfulQA
    - 数学推理：GSM8K（链式思维）
    - 翻译：WMT16-de-en（德→英）
    - 摘要：XSum
    - 另外扩展：SimpleQA（API模型），BBH（多选改编为长文本）
- **基准（Baselines）**：
    - 主要对比：AU（自一致性）作为Aleatoric基线。
    - 其他基线：Mean Token Entropy, Max Token Probability, Max Sequence Probability, Perplexity, PTrue, Self-Certainty, Semantic Entropy, SC Score, Closeness Centrality, SC+VC等（共12种），实现来自Fadeeva et al. (2023)和Jiang et al. (2024)。
- **评估指标**：
    - AUROC（区分正确/错误的能力）
    - 选择性预测：Risk-Coverage曲线、AURC、C@90、C@80
    - 对于翻译/摘要额外使用BLEU/ROUGE相关性。
- **实验设计**：
    - 参考模型：5个7-9B指令微调模型（Gemma-2-9B-It, Granite-3.0-8B-Instruct, Llama-3.1-8B-Instruct, Mistral-7B-Instruct-v0.3, Qwen2.5-7B-Instruct）。
    - 辅助模型集：上述5个模型（除参考模型外其他4个），保持规模匹配。
    - 样本数：默认每个模型2个响应，总预算与AU使用10个响应一致（公平比较）。消融实验中变化样本数和模型数。
    - 正确性评判：使用Meta-Llama-3-70B-Instruct作为评委（LM-as-a-judge），检测与人工评委的一致性<6%分歧。
    - 额外实验：API模型（GPT-4o, Claude 3.7 Sonnet）在SimpleQA上验证。参考模型大小消融（Qwen2.5 0.5B~32B, Gemma3 1B~27B）。噪声扰动辅助模型对比。

## 4. 资源与算力

- **硬件**：2块 NVIDIA A100 80GB GPU。
- **推理框架**：vLLM，lm-evaluation-harness。
- **耗时**：主实验为单卡推理，未报告精确总时长。附录A.9提供了TriviaQA上的wall-clock测量：单模型10样本约244秒，5模型×2样本（顺序加载）约392秒；若5路并行则约78秒（与单模型相当）。
- **关键点**：本文仅涉及推理，无需训练，算力开销主要来自加载多个模型和生成响应。对比实验采用相同生成预算（总token数相当），因此额外计算是公平的。

## 5. 实验数量与充分性

- **实验规模**：非常充分。
    - 核心结果：5个参考模型×10个数据集×2个不确定性（AU vs TU），共100组AUROC对比。图4、表2报告每组合。
    - 选择性预测：表1报告10个数据集上C@90, C@80, AURC。
    - 消融实验：
        - 辅助模型数量（图15）
        - 样本数量（图16）
        - 参考模型大小（图13）
        - 相似度函数选择（表5，sentence-T5-xl vs deberta）
        - 加权总不确定性（表6）
        - 噪声扰动辅助模型（图14）
    - 对比基线：图5展示Mistral模型上12种基线与TU的AUROC对比，表3给出逐任务详细值。
    - 扩展实验：API模型（图1b）、BBH多选（表7）、相关性分析（表4）。
    - 诊断分析：图2、图3展示EU在低AU区间的分离能力，以及EU AUROC与数据集冗余度/互补性的相关关系。
- **充分性评价**：实验设计客观公平，样本预算对等，消融覆盖关键因素（模型数量、样本数、相似度函数、参考模型能力、辅助模型多样性）。结论从多角度验证。但未覆盖更大规模模型（如70B）作为参考，受限于资源。总体上实验充分、结论稳健。

## 6. 主要结论与发现

1. **AU的失效模式**：在模型过度自信且重复同一错误答案时（低AU），EU显著更高，能有效标记这些“自信错误”（图2）。
2. **TU优于AU**：在几乎全部模型-数据集组合上，TU的AUROC高于AU（平均提升0.05~0.15），尤其在HotpotQA、CoQA、WMT16上增益明显（图4）。在选择性预测中，TU获得更低AURC和更高选择性准确率（表1，图7）。
3. **EU的有效性条件**：通过Jaccard冗余度（J）和Oracle覆盖增益（G）发现，EU最有效于“唯一正确答案”的任务（如事实QA、翻译），此时模型正确时语义一致、错误时语义分歧；在存在多个有效答案的任务（如XSum）中EU判别力下降（图3）。
4. **对比基线领先**：TU在Mistral-7B上平均AUROC 0.72，远超最强单模型基线（Closeness Centrality 0.64）和其他10种方法（图5，表3）。
5. **鲁棒性**：即使参考模型远大于辅助模型（如Qwen2.5-32B vs 7B），TU仍优于AU（图13）。使用噪声扰动作为辅助模型时提升有限，证实跨家族模型的多样性更重要（图14）。
6. **成本可控**：增加辅助模型数和样本数可提升性能，但主要收益来自少量模型（2-3个）和少量样本（1-2个）（图15-16）。

## 7. 优点

- **方法创新**：将认知不确定性操作化为跨模型语义不一致，与自一致性互补，解决了后者在自信错误上的盲区。
- **黑盒友好**：仅需模型输出文本，无需logits、隐状态或参数访问，适用于API模型和闭源模型。
- **理论支撑**：从核嵌入MMD角度给出D(ω||ω*)的解释，联系变分推断，提供上界（附录A.1）。
- **实验全面**：
    - 覆盖多种任务类型、多模型家族、多规模。
    - 公平对比：控制总生成预算一致。
    - 多种消融：分析模型数、样本数、相似度函数、辅助模型质量、加权方式。
    - 不仅评估AUROC，还评估选择性预测（更贴近实际部署需求）。
    - 提供诊断分析明确方法的适用条件。
- **实用价值**：可在保持推理成本相近（通过并行）下显著提升不确定性量化质量。

## 8. 不足与局限

1. **任务限制**：当任务存在多个语义不同但均正确的答案时（如开放问答、摘要），跨模型不一致可能膨胀而不反映错误，降低EU有效性。作者在XSum上观察到改善有限。
2. **辅助模型依赖**：若辅助模型集预训练数据或架构高度同质，EU可能低估真实认知不确定性（作者通过跨家族选择缓解）。
3. **语义相似度局限**：当前使用固定嵌入模型（sentence-T5-xl），对语义细微差别（如反事实、否定、数值变化）不鲁棒；且未完全覆盖所有正确表达方式。
4. **只考虑了一种AU形式**：未与token级或logit级AU方法结合；未来可探索更优组合。
5. **评判器可靠性**：正确性依赖LLM-as-a-judge，尽管与人工一致率>94%，仍存在偏差风险。改进评判器将提升评估精度。
6. **可扩展性**：需要加载多个模型（即使仅推理），在资源受限场景下可能增加部署成本。作者指出可通过并行化降低延迟。
7. **未覆盖超大模型**：参考模型限于7-32B，未验证70B+规模的效果；辅助模型仅为同量级，未来需探索更大模型作为参考时如何选择辅助集。
8. **无训练开销但推理成本明确**：需多次生成（多个模型×样本），尽管总token数可与单模型多采样持平，但加载多模型占用显存和切换时间。

（完）
