---
title: "Principled Data Selection for Alignment: The Hidden Risks of Difficult Examples"
title_zh: 对齐原则性数据选择：困难示例的隐藏风险
authors: "Chengqian Gao, Haonan Li, Liu Liu, Zeke Xie, Peilin Zhao, zhiqiang xu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=qut63YypaD"
tags: ["query:smd"]
score: 7.0
evidence: 基于示例难度的数据选择以保持对齐
tldr: 该论文提出偏好数据存在难度差异，过难的示例会阻碍对齐效果。通过系统实验验证了模型容量与示例难度匹配的重要性，并提出基于难度的数据选择原则。该方法可直接推广到安全对齐数据的筛选，在微调中保留对齐能力。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-qut63yypad/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 824, \"height\": 558, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qut63yypad/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1751, \"height\": 453, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qut63yypad/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1743, \"height\": 764, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qut63yypad/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1734, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qut63yypad/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1698, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qut63yypad/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1763, \"height\": 329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qut63yypad/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1743, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qut63yypad/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1749, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qut63yypad/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 825, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qut63yypad/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1752, \"height\": 797, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qut63yypad/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1304, \"height\": 1758, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qut63yypad/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1585, \"height\": 777, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qut63yypad/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1269, \"height\": 367, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qut63yypad/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 675, \"height\": 367, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-qut63yypad/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1765, \"height\": 840, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qut63yypad/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1764, \"height\": 363, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qut63yypad/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1567, \"height\": 347, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qut63yypad/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1758, \"height\": 359, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qut63yypad/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1762, \"height\": 355, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qut63yypad/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1762, \"height\": 404, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qut63yypad/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1137, \"height\": 420, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qut63yypad/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1769, \"height\": 1378, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qut63yypad/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1764, \"height\": 1680, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qut63yypad/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1772, \"height\": 1597, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qut63yypad/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1764, \"height\": 1952, \"label\": \"Table\"}]"
motivation: 现有对齐方法忽略数据难度与模型能力的匹配，导致对齐效果受限。
method: 通过实验分析偏好数据难度，提出依据模型容量选择合适难度的数据进行训练。
result: 在多个模型和数据集上验证了困难示例的负面影响，并展示了难度选择的有效性。
conclusion: 选择与模型能力匹配的数据可显著提升对齐效果，为安全数据筛选提供指导。
---

## Abstract
The alignment of large language models (LLMs) often assumes that using more clean data yields better outcomes, overlooking the match between model capacity and example difficulty. Challenging this, we propose a new principle: *Preference data vary in difficulty, and overly difficult examples hinder alignment, by exceeding the model's capacity*. Through systematic experimentation, we validate this principle with three key findings: (1) preference examples vary in difficulty, as evidenced by consistent learning orders across alignment runs; (2) overly difficult examples significantly degrade performance across four LLMs and two datasets; and (3) the capacity of a model dictates its threshold for handling difficult examples, underscoring a critical relationship between data selection and model capacity. Building on this principle, we introduce *Selective DPO*, which filters out overly difficult examples. This simple adjustment improves alignment performance by 9-16\% in win rates on the AlpacaEval 2 benchmark compared to the DPO baseline, surpassing a series of DPO variants with different algorithmic adjustments. These results together illuminate the importance of aligning data difficulty with model capacity, offering a transformative perspective for improving alignment strategies in LLMs. Code is available at https://github.com/glorgao/SelectiveDPO

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：现有大语言模型（LLM）对齐方法通常假设使用更多干净数据会带来更好结果，但忽略了数据难度与模型容量之间的匹配关系。作者质疑这一假设，认为过难的偏好示例会因超出模型当前能力而反而损害对齐性能。
- **核心问题**：偏好数据是否存在难度差异？过难示例是否真的有害？模型容量如何影响可处理的数据难度阈值？
- **整体含义**：提出了一个新原则——“偏好数据难度各异，过难示例因超出模型容量而阻碍对齐”，为对齐策略提供了变革性视角：数据选择应基于模型容量匹配数据难度，而非盲目追求更多干净数据。

## 2. 方法论

### 2.1 核心思想
- 偏好数据存在固有难度排序（通过“学习步”或“验证损失”量化）。
- 过滤掉超过模型容量的过难示例，并按照从易到难的顺序训练，可显著提升对齐性能。
- 难度是相对模型容量的：更大模型能处理更多困难示例。

### 2.2 关键技术细节
- **难度量化**：
  - **学习步（Learned Step）**：模型首次稳定区分偏好响应与拒绝响应的训练步数，步数越大表示示例越难（需在held-out集上计算以避免数据顺序干扰）。
  - **验证损失（Validation Loss）**：作为学习步的计算廉价代理，定义为 \( VL(x, y_w, y_l) = -\log \sigma\left( \beta \log \frac{\pi_{\hat{\theta}}(y_w|x)}{\pi_{\text{ref}}(y_w|x)} - \beta \log \frac{\pi_{\hat{\theta}}(y_l|x)}{\pi_{\text{ref}}(y_l|x)} \right) \)，其中 \(\pi_{\hat{\theta}}\) 是在子集上训练的DPO参考模型。低验证损失表示容易示例。通过Spearman秩相关和Jaccard相似性验证了两者高度一致。
- **Selective DPO 算法流程**：
  - **步骤1**：将训练集随机分成两份，分别训练三个随机种子下的DPO参考模型，共得到6个参考模型。
  - **步骤2**：用这些参考模型计算每个held-out示例的验证损失（取均值），按损失从小到大排序（从易到难）。
  - **步骤3**：选择验证损失最低的 \(\tau\%\) 示例（超参数，例如50%），并按从易到难的顺序输入标准DPO进行对齐训练。
- **灵活阈值**：\(\tau\) 可根据模型容量和数据集难度分布调整，可使用第三方评估器（如AlpacaEval 2）确定。

### 2.3 公式
- DPO损失函数：\( \mathcal{L}_{\text{DPO}}(\pi_\theta, D) = -\mathbb{E}_{(x,y_w,y_l)\sim D} \left[ \log \sigma\left( \beta \log \frac{\pi_\theta(y_w|x)}{\pi_{\text{ref}}(y_w|x)} - \beta \log \frac{\pi_\theta(y_l|x)}{\pi_{\text{ref}}(y_l|x)} \right) \right] \)
- 学习步定义：\( LS(x,y_w,y_l) = \min \{ t_{\text{lrn}} : \beta \log \frac{\pi_{\theta_t}(y_w|x)}{\pi_{\text{ref}}(y_w|x)} - \beta \log \frac{\pi_{\theta_t}(y_l|x)}{\pi_{\text{ref}}(y_l|x)} > \delta, \forall t > t_{\text{lrn}} \} \)（\(\delta=0.4\)，仅对held-out示例计算）

## 3. 实验设计

### 3.1 数据集
- **UltraFeedback-binarized**：广泛使用的对齐数据集，包含约61k条偏好样本。
- **Argilla-dpo-mix-7k**：小型高质量偏好数据集（约7k条）。

### 3.2 基准模型与设置
- 四种SFT模型（均在UltraChat-200k上训练）：Mistral-7B-SFT、Qwen-2.5-7B-SFT、Llama-3-8B-SFT、Gemma-2-9B-SFT。
- 超参数：\(\beta=0.01\)，学习率通过网格搜索确定，1个epoch，批量大小64或128，使用paged AdamW优化器（LoRA或全参数微调）。

### 3.3 评估基准
- **AlpacaEval 2**：805个测试提示，使用ArmoRM作为评估器，报告胜率（WR）和长度控制胜率（LC）。
- **Arena-Hard v0.1**：以GPT-4-0314为参考，GPT-4-Turbo为评估器，报告胜率。
- **MT-Bench**：多轮对话质量评分（1-10），GPT-4或GPT-4-Turbo评估。

### 3.4 对比方法
- **数据校正类**：标签翻转、标签平滑。
- **DPO变体类**：DPO、IPO、KTO、ORPO、R-DPO、SimPO、WPO、RRHF、SLiC-HF、CPO。
- **数据选择/筛选类**：CHES（基于损失过滤50%）、RM（基于奖励边际）、PPL（基于困惑度中间50%）、Selective DPO。

## 4. 资源与算力

- 所有训练使用**8×H100 GPU**节点。
- 对于7B模型，**Selective DPO全参数微调**大约需要**8 GPU小时**（H100）。
- 文中也提到使用**4×A100 40G**进行LoRA实验，以方便资源有限的研究者复现。
- 具体训练时间未在所有实验中详细报告，但提供了关键超参数配置（附录C）。

## 5. 实验数量与充分性

### 实验数量
- 主要验证实验：在4种模型 × 2个数据集 × 3种排序策略（随机、从易到难、仅易示例）下，共24组主实验（图3），每组3个种子，总共72次运行。
- 困难示例不是数据误差的验证：3个消融实验（标签翻转、分布偏移、学习率敏感度）。
- 模型容量实验：Qwen-2.5-3B/7B/14B三个规模，每个10次运行（图5）。
- 弱到强课程实验：2种课程对比。
- 基准对比：表1报告了主要对比结果，图7扩展至SimPO和WPO。
- 超参数研究：参考模型数量（1/2/6/10）、选择比例（\(\tau=40\%/50\%/60\%\)）。
- 深入分析：NLL分布、奖励边际分布。
- 下游任务评估（附录D）：MMLU、Winograd、GSM8K、HellaSwag、ARC、TruthfulQA。
- 特征分析（附录E、F）：长度、奖励边际、GPT-4评分与验证损失对比；案例研究三个难度级别。

### 充分性与客观性
- **充分性**：实验覆盖了多种模型规模（2B-14B）、多种数据集（含噪声和高质量）、多种对比方法（包括SOTA变体），并进行消融和因果分析（排除标签噪声、分布偏移、学习率等干扰）。下游任务评估也包含在内，显示在部分任务（如GSM8K）上的折衷，体现了客观性。
- **公平性**：所有基线方法均进行学习率网格搜索，确保最优性能。Selective DPO的参考模型训练采用随机种子和数据划分，并报告多次运行的平均值和标准差。评估使用统一的自动化评估器（ArmoRM、GPT-4等），避免了人工偏差。

## 6. 主要结论与发现

1. **偏好示例存在固有难度差异**：不同示例的学习步在多次运行中一致，验证损失可作为有效代理。
2. **过难示例显著阻碍对齐**：在四种模型和两个数据集上，包含过难示例均导致性能下降（WR下降约9.4%）。这种有害效应并非由标签错误、分布偏移或不恰当学习率引起。
3. **模型容量决定可处理难度阈值**：更大模型能受益于更高比例的困难示例（3B模型最佳比例64%，14B模型81%），表明难度需与模型容量匹配。
4. **Selective DPO**：通过过滤前50%最难的示例，在AlpacaEval 2上比DPO提升9-16%的胜率，超越SimPO、WPO等强基线。同时保持更好的负对数似然分布和更大的隐式奖励边际。
5. **弱到强课程效果有限**：使用小模型课程指导大模型对齐效果不如使用大模型自身课程，说明难度感知需针对目标模型。

## 7. 优点

- **提出新原则**：系统性地揭示了数据难度-模型容量匹配对对齐的重要性，挑战了传统“越多干净数据越好”的假设。
- **方法简单有效**：Selective DPO只需在DPO前进行一次轻量级验证损失排序，无需复杂算法调整，却取得显著提升。
- **实验全面扎实**：覆盖多种模型、数据集、对比方法、消融和因果分析，验证了核心原则的鲁棒性。包括下游任务评估，展示了选择性对齐对通用性能的影响。
- **分析深入**：通过Spearman相关、Jaccard相似性、案例研究、特征分析等方式，全面刻画了难度本质，排除了常见混淆因素。
- **开源可复现**：代码和训练配置公开，便于后续研究。

## 8. 不足与局限

- **长度偏差**：选出的容易示例偏向较短响应，导致模型在AlpacaEval 2上的长度控制胜率（LC）不如胜率（WR）突出。虽然这不是本工作的核心重点，但限制了在重视长度约束场景中的直接应用。
- **仅限于DPO设置**：原理和实验均基于DPO（直接偏好优化），未在RLHF（强化学习从人类反馈）框架下验证。RLHF通常使用奖励模型和在线采样，数据难度的影响可能不同。
- **数学/推理能力下降**：在下游评估中（如GSM8K），Selective DPO在Mistral-7B模型上出现显著性能下降，因为困难示例中包含大量数学推理任务，被过滤后模型数学能力衰退。虽然可通过增加10%更难的示例缓解（如60%选择），但仍需谨慎处理技能保留问题。
- **计算开销**：训练6个参考模型（每个需一次完整DPO训练）带来了额外计算负担（约8 GPU小时对7B模型）。对于极大模型（如100B+）可能不可忽略。
- **τ值选择依赖外部评估**：最优选择比例需通过第三方评估器（如AlpacaEval 2）确定，在资源受限或无合适评估场景下难以应用。
- **通用性待验证**：仅使用两个偏好数据集（UltraFeedback-binarized和Argilla-7k），若数据集质量分布不同（如全部为非常easy的示例），则筛选可能无收益或产生反效果。对于不同领域（如代码、法律）的泛化能力未测试。

（完）
