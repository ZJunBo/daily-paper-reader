---
title: "Steering When Necessary: Flexible Steering Large Language Models with Backtracking"
title_zh: 在必要时转向：通过回溯灵活引导大语言模型
authors: "Zifeng Cheng, Jinwei Gan, Zhiwei Jiang, Cong Wang, Yafeng Yin, Xiang Luo, Yuchen Fu, Qing Gu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=l75RyRcevf"
tags: ["query:dg"]
score: 7.0
evidence: 基于回溯的灵活激活转向
tldr: 现有激活转向方法对所有生成统一干预，或仅依据问题决定，精度受限。本文提出FASB框架，引入回溯机制动态评估是否需要干预及干预强度，在需要时才进行转向。实验表明，该方法在保持对齐效果的同时减少了不必要的副作用。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-l75ryrcevf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 387, \"height\": 200, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l75ryrcevf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l75ryrcevf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1433, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l75ryrcevf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1428, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l75ryrcevf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1400, \"height\": 573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l75ryrcevf/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1454, \"height\": 657, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l75ryrcevf/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1429, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l75ryrcevf/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1453, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l75ryrcevf/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 753, \"height\": 549, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l75ryrcevf/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1445, \"height\": 508, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-l75ryrcevf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1295, \"height\": 463, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l75ryrcevf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1267, \"height\": 335, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l75ryrcevf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 857, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l75ryrcevf/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 658, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l75ryrcevf/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1352, \"height\": 499, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l75ryrcevf/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1318, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l75ryrcevf/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1455, \"height\": 1014, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l75ryrcevf/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 762, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l75ryrcevf/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 977, \"height\": 185, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l75ryrcevf/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1051, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l75ryrcevf/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 622, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l75ryrcevf/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1243, \"height\": 616, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l75ryrcevf/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1263, \"height\": 462, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l75ryrcevf/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 695, \"height\": 182, \"label\": \"Table\"}]"
motivation: 现有激活转向无差别干预或仅基于问题判断，强度不当影响效果。
method: 在生成过程中引入回溯，根据当前上下文动态决定是否施加转向及强度。
result: FASB在多个转向任务上优于无条件干预方法，且干扰更少。
conclusion: 条件性介入可提升激活转向的效率与精度。
---

## Abstract
Large language models (LLMs) have achieved remarkable performance across many generation tasks.
Nevertheless, effectively aligning them with desired behaviors remains a significant challenge.
Activation steering is an effective and cost-efficient approach that directly modifies the activations of LLMs during the inference stage, aligning their responses with the desired behaviors and avoiding the high cost of fine-tuning.
Existing methods typically indiscriminately intervene to all generations or rely solely on the question to determine intervention, which limits the accurate assessment of the intervention strength.
To this end, we propose the **F**lexible **A**ctivation **S**teering with **B**acktracking (**FASB**) framework, which dynamically determines both the necessity and strength of intervention by tracking the internal states of the LLMs during generation, considering both the question and the generated content.
Since intervening after detecting a deviation from the desired behavior is often too late, we further propose the backtracking mechanism to correct the deviated tokens and steer the LLMs toward the desired behavior.
Extensive experiments on the TruthfulQA dataset and six multiple-choice datasets demonstrate that our method outperforms baselines.
Our code will be released at https://github.com/gjw185/FASB.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：大型语言模型（LLM）在生成任务中表现出色，但如何有效对齐到期望行为（如真实性、无害性）仍是挑战。激活转向（Activation Steering）通过在推理阶段直接修改模型内部激活，避免微调的高成本，是一种高效的对齐方法。
- **现有问题**：现有方法要么**无差别地干预所有生成**（如 ITI、CAA），要么**仅基于问题（prompt）决定是否干预**（如 CAST），忽略了生成过程中的实时状态变化。前者导致对正确回答的不必要干预，后者无法评估生成内容的实际偏离程度，干预强度不准确。
- **核心问题**：如何根据生成过程中的内部状态动态判断是否需要干预以及干预强度，并在检测到偏离后及时纠正，同时避免过度干预。

## 2. 方法论

### 核心思想
提出 **FASB（Flexible Activation Steering with Backtracking）** 框架，通过两步实现灵活干预：
1. **识别与期望行为相关的注意力头**，并构建转向向量和分类器（用于状态追踪）。
2. **在生成过程中动态追踪内部状态**，判断是否偏离，并在需要时回溯到前面几个 token，施加自适应强度的激活转向，重新生成纠正。

### 关键技术细节

- **Heads Anchoring and Steering Vectors Inducing（第一步）**
  - **Probe 方法（主要）**：在标注的问答数据上，提取每个注意力头在最后一个 token 的激活值，为每个头训练一个逻辑回归分类器（probe）：  
    `p_(θ_(ℓ,h))(x) = sigmoid(⟨θ_(ℓ,h), x⟩)`。  
    选择验证集准确率最高的 top-k 个注意力头作为干预目标，并将 probe 参数 `θ` 作为转向向量。
  - **Prototype 方法（附录 A，可选的免训练方法）**：计算正负类原型向量，用余弦相似度构建分类器，转向向量取正负原型差值。

- **Generation with Flexible Steering and Backtracking（第二步）**
  - **状态追踪**：每生成第 j 个 token 后，计算 top-k 头分类器预测的概率平均值作为偏离概率：  
    `p(x_(i,j)) = (1/k) * Σ_( (ℓ,h)∈topk ) (1 - p_(θ_(ℓ,h))(x_(ℓ,h)_(i,j)))`。
  - **回溯机制**：当 `p(x_(i,j)) > β`（阈值）时，认为生成已偏离，回溯 s 个 token（超参数），保留前 j-s 个 token，然后从该点重新生成。
  - **自适应干预强度**：干预强度 `r = I(p>β) * p * α`，其中 α 为强度缩放因子，β 为阈值。强度与偏离概率成正比。
  - **激活转向**：在回溯点后的每个 token 生成时，对选中的 top-k 注意力头输出添加转向向量乘以强度：  
    `x_(ℓ,h)_new = x_(ℓ,h) + r * θ_(ℓ,h) * c_(ℓ,h)`（c 为 0/1 指示是否选中该头）。

### 算法流程（文字说明）
1. （第一步）在训练集上训练分类器（Probe 或 Prototype），筛选 top-k 头并获取转向向量。
2. （第二步）初始化生成过程，从第 s 个 token 开始逐 token 生成并追踪。
3. 每生成一个 token，计算偏离概率。若超过阈值 β 且已生成至少 s 个 token，则回溯 s 个 token，计算干预强度，然后从回溯点开始逐 token 施加转向向量重新生成，直至结束；否则继续正常生成。

## 3. 实验设计

### 数据集与场景
- **开放生成任务**：TruthfulQA（评估真实性和信息性，使用 LLM judge 模型给出 True%、Info%、True*Info%）。
- **多项选择任务**：TruthfulQA（MC1、MC2、MC3）、COPA、StoryCloze、NLI、MMLU、SST2、Winogrande（共 7 个数据集，选项数 2~4）。
- **额外基准**：Natural Questions、TriviaQA（分布外真实性测试）、WikiHop（多跳 QA）、RealToxicityPrompts（毒性生成）。
- **模型族**：LLaMA2-7B、LLaMA2-7B-CHAT、LLaMA2-13B-Chat、LLaMA3.1-8B-Instruct、Qwen2.5-7B/7B-Instruct/32B-Instruct（共 7 个不同规模/架构的 LLM）。

### 对比方法
- **Baseline**（无干预）、**ITI**、**CAA**、**ORTHO**、**CAST**、**ACT**、**SADI**（均为代表性的激活转向方法）。
- 此外有消融变体（如固定强度、无回溯、仅在问题后干预等）。

### 评价指标
- 开放生成：True%（真实性）、Info%（信息性）、True*Info%（主指标）。
- 多项选择：MC1、MC2、MC3（不同选项排序下的准确率）。

## 4. 资源与算力

- **实验硬件**：论文在实验设置中说明“All experiments are conducted on 4 NVIDIA A800 GPUs.”，但未提供具体的训练时长或推断时间开销。
- **计算开销**：FASB 仅在需要时回溯少量 token，且状态追踪利用已有激活值，作者声称开销轻量（轻于从头生成），但未量化对比。

## 5. 实验数量与充分性

- **实验组数**：约 14 组主要实验（含表 1~4、图 5~9），外加附录中大量补充实验（消融、参数分析、跨模型、跨行为等）。
- **消融实验**：表 3 系统性地研究了干预强度（固定 vs 自适应 vs Probe）、干预位置（无回溯 vs After Question vs 完整FASB）。
- **泛化性验证**：跨 7 个 LLM、跨多个真实性数据集（分布外）、跨行为（毒性生成），充分证明了方法的通用性和鲁棒性。
- **公平性**：与多种基线方法在相同设置下对比，超参数通过验证集搜索，实验设计合理、结果明确。
- **结论**：实验充分、客观，覆盖了主要维度，结论有可靠支持。

## 6. 主要结论与发现

1. **动态干预优于固定干预**：FASB（Probe）在 TruthfulQA 开放生成上 True*Info 达 80.56%，远高于 ITI（76.11%）和无干预（66.50%）；在六个多项选择任务上平均 78.8%，显著优于所有基线（最高 66.8%）。
2. **回溯机制至关重要**：若去除回溯（w/o Backtracking），True*Info 跌至 62.11%，甚至低于基线，说明检测到偏离后再干预已太晚。
3. **自适应强度提升效果**：与固定强度相比，自适应强度（p 值比例）进一步提高指标。
4. **跨模型通用性强**：在 6 个不同模型上均超越 ITI，其中在 Qwen2.5-7B 上 MC1 提升 24.61%。
5. **数据效率高**：仅使用 20% 训练数据（496 样本）即可超越基线。
6. **方法可拓展至其他行为**：在毒性生成任务（RealToxicityPrompts）上也能有效引导模型输出毒性内容（ASR 提升 4.4%），表明其通用性，但也存在滥用风险。

## 7. 优点

- **动态与自适应**：根据生成状态实时决定是否干预及强度，避免不必要干预，减少副作用。
- **回溯纠正机制新颖**：能修正已偏离的 token，这是现有方法不具备的。
- **轻量高效**：无需额外训练（Prototype 变体免训练），仅需少量回溯 token，计算开销低。
- **可解释性**：基于注意力头探针选择干预位置，易于理解。
- **广泛适用性**：覆盖多个模型、多种任务（真实性、毒性、多跳QA）、不同行为方向。
- **实验设计严谨**：消融实验充分，参数分析详细，泛化验证充分。

## 8. 不足与局限

- **潜在滥用风险**：方法可被用于恶意目的（如越狱、生成虚假信息），论文已指出但未提供防护手段。
- **超参数敏感**：干预强度 α、阈值 β、回溯步数 s 需要调节，在不同任务/模型上可能需要重新搜索，泛化性受限于调节成本。
- **评估依赖 LLM judge**：真实性评估使用 LLM 作为评判器，可能引入误差（论文已承认）。
- **行为覆盖有限**：主要关注真实性和毒性，未在情感、风格、事实性等其他行为上验证。
- **语言与问答限定**：仅使用英文数据集，任务形式多为问答/多项选择，无法确定在开放性对话或非英文场景下的表现。
- **回溯开销未量化**：虽然声称轻量，但未给出实际生成时间对比，在长文本或频繁回溯时可能增加延迟。

（完）
