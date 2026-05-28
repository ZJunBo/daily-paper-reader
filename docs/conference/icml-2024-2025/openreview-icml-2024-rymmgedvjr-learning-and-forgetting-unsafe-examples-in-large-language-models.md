---
title: Learning and Forgetting Unsafe Examples in Large Language Models
title_zh: 大语言模型中不安全示例的学习与遗忘
authors: "Jiachen Zhao, Zhun Deng, David Madras, James Zou, Mengye Ren"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=RYmmgedVjR"
tags: ["query:smd"]
score: 9.0
evidence: 基于遗忘信号过滤不安全数据的ForgetFilter算法
tldr: 该论文研究了大语言模型在微调过程中对不安全示例的学习与遗忘行为，发现对齐模型会学习不安全内容但在后续安全微调中更容易遗忘这些内容。基于此，作者提出ForgetFilter算法，通过模型对数据的遗忘信号来过滤不安全数据，从而在微调过程中自动筛选安全数据，有效缓解有害微调攻击。实验表明该方法能显著提升模型的安全性。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-rymmgedvjr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1512, \"height\": 264, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-rymmgedvjr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1767, \"height\": 466, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-rymmgedvjr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1770, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-rymmgedvjr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1724, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-rymmgedvjr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 733, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-rymmgedvjr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1725, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-rymmgedvjr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 692, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-rymmgedvjr/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1614, \"height\": 1262, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-rymmgedvjr/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1600, \"height\": 697, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-rymmgedvjr/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1764, \"height\": 777, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-rymmgedvjr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 855, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-rymmgedvjr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1459, \"height\": 373, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-rymmgedvjr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 891, \"height\": 248, \"label\": \"Table\"}]"
motivation: 现有研究缺乏对微调过程中不安全数据学习与遗忘行为的系统理解，亟需在微调中筛选安全数据的方法。
method: 提出ForgetFilter算法，利用模型对数据的遗忘信号强度来识别并过滤不安全数据。
result: 实验证明该方法能有效过滤不安全数据，在多个基准上提升模型安全性。
conclusion: 通过分析遗忘行为可自动筛选安全数据，为安全微调提供有效途径。
---

## Abstract
As the number of large language models (LLMs) released to the public grows, there is a pressing need to understand the safety implications associated with these models learning from third-party custom finetuning data. We explore the behavior of LLMs finetuned on noisy custom data containing unsafe content, represented by datasets that contain biases, toxicity, and harmfulness, finding that while aligned LLMs can readily learn this unsafe content, they also tend to forget it more significantly than other examples when subsequently finetuned on safer content. Drawing inspiration from the discrepancies in forgetting, we introduce the “ForgetFilter” algorithm, which filters unsafe data based on how strong the model's forgetting signal is for that data. We demonstrate that the ForgetFilter algorithm ensures safety in customized finetuning without compromising downstream task performance, unlike sequential safety finetuning. ForgetFilter outperforms alternative strategies like replay and moral self-correction in curbing LLMs’ ability to assimilate unsafe content during custom finetuning, e.g. 75% lower than not applying any safety measures and 62% lower than using self-correction in toxicity score.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）在“发布-微调”范式下，第三方用户可对已对齐模型进行自定义微调。当微调数据中包含不安全内容（如偏见、毒性、有害性）时，对齐模型会轻易学习这些不安全行为，导致模型生成不安全输出。现有安全对齐研究主要关注发布前的安全微调，但对发布后微调阶段的风险缺乏系统理解。
- **整体含义**：揭示LLM在连续微调过程中对不安全示例的学习与遗忘模式，发现安全微调虽能恢复安全性，但会导致重要下游知识被灾难性遗忘；同时发现不安全示例的遗忘速度显著快于其他示例。基于这一选择性遗忘现象，提出ForgetFilter算法，在微调前过滤不安全数据，兼顾安全性与下游性能。

## 2. 方法论

- **核心思想**：利用LLM在安全微调阶段对不安全示例的遗忘速率显著高于安全示例和下游任务数据这一特性，设计基于遗忘信号的过滤机制。
- **关键技术细节**：
  - **遗忘率定义**：对于数据点$(x, y)$，遗忘率$r(t, x, y) = s(f(x, \theta_{t_0}), y) - s(f(x, \theta_t), y)$，其中$s$为评分函数（采用ROUGE-1，基于解码生成而非困惑度），$\theta_{t_0}$为初始权重，$\theta_t$为安全微调$t$步后的权重。
  - **算法流程**（ForgetFilter）：
    1. 存储初始对齐模型$M_0$。
    2. 用含不安全示例的噪声数据$D_{\text{noisy}}$微调$M_0$得到$M_1$。
    3. 用安全数据$D_{\text{safe}}$对$M_1$进行安全微调$t$步得到$M_2$。
    4. 计算$M_2$在$D_{\text{noisy}}$上每个样本的遗忘率，过滤掉遗忘率超过阈值$\phi$的样本，得到$D_{\text{noisy}}'$。
    5. 用过滤后的数据$D_{\text{noisy}}'$重新从$M_0$开始微调，得到最终模型$M_{\text{ret}}$。
- **特点**：无需预定义安全分类器或规则，可处理多种隐含的不安全内容（偏见、毒性、有害性），且对噪声比例鲁棒。

## 3. 实验设计

- **数据集与场景**：
  - **偏见（Bias）**：BBQ数据集，包含模棱两可和明确情境的问答，通过修改答案构造不安全示例。
  - **毒性（Toxicity）**：Pile子集，使用Detoxify分类器标记毒性分数（>0.9为不安全，<0.1为安全）。
  - **有害性（Harmfulness）**：HarmfulQA数据集，人工标注“红对话”为有害、“蓝对话”为安全。
  - **下游任务数据**：SQuAD（问答）和Alpaca（指令微调）。
  - **噪声数据构造**：将不安全示例与安全示例、下游任务数据混合，默认不安全比例$R_{\text{unsafe}}=50\%$。
- **Benchmark与对比方法**：
  - 基线：BaseFT（仅用安全数据微调）、直接微调噪声数据（+Downstream）。
  - 对比方法：安全微调（+SafetyFT）、回放（Replay）、道德自我修正（Self-Correction, SC）、ForgetFilter（FF）、FF+SC。
- **评估指标**：偏见分数（BBQ定义的s_DIS和s_AMB）、毒性分数（Detoxify评分）、下游F1分数（SQuAD）。
- **模型规模**：LLaMA-7B、GPT2-XL (1.5B)、GPT2-L (774M)、GPT2-M (334M)。

## 4. 资源与算力

- 论文中未明确说明具体GPU型号和数量。在附录A中提及使用LoRA（低秩适配）微调LLaMA-7B，学习率2e-4，批次大小32，但未报告训练时长或硬件配置。因此无法给出精确算力信息，但可推断实验需要至少单卡A100或同等内存的GPU。

## 5. 实验数量与充分性

- **实验数量**：
  - 主要实验（表2）：在偏见、毒性、混合三种设置下，对比6种方法，共18个结果。
  - 过滤性能评估（表1）：对偏见、毒性、有害性三种不安全类型，各三种噪声比例（25%、50%、75%），共9个F1值。
  - 遗忘模式分析（图3-4、图6-7）：展示不同模型大小、部分微调、领域偏移等条件下的遗忘曲线。
  - 交错训练长期安全实验（图5、图12）：两轮交替微调，比较FF、SC等。
  - 消融实验（图8）：训练步数、阈值$\phi$、安全样本数量等参数影响。
- **充分性评价**：实验覆盖全面，涉及三种安全概念、四种模型规模、多种防御策略、参数敏感性和长期效果，交叉验证充分；评估指标包括安全性和下游性能，较为客观。但缺少在更大模型（如LLaMA-13B/70B）上的实验，且有害性仅用于遗忘分析未用于微调对比（因缺乏自动评估指标）。

## 6. 主要结论与发现

- **不安全示例易于学习**：对齐模型在噪声微调中会快速学习不安全内容，且更大模型学习偏见更快。
- **安全微调导致遗忘**：后续安全微调虽能恢复安全性，但会导致下游任务数据也发生遗忘；**不安全示例的遗忘速率显著高于其他示例**（偏见、毒性、有害性均一致）。
- **遗忘差异与模型规模相关**：较大模型（LLaMA-7B、GPT2-XL）表现出明显遗忘差异，而GPT2-M无此现象。
- **ForgetFilter有效性**：在保持下游性能的同时，显著降低偏见和毒性分数（比不采取安全措施低75%，比自我修正低62%）。结合自我修正可进一步加固。
- **长期安全问题**：交错训练中，安全微调无法根除不安全记忆，模型可立即召回；而ForgetFilter能持续保持低偏见，证明数据过滤是更可靠的长期策略。

## 7. 优点

- **新颖发现**：首次系统揭示LLM在安全微调中对不安全示例的选择性遗忘模式，并利用该模式设计过滤方法，思路巧妙。
- **方法通用性**：ForgetFilter不依赖预定义分类器，可适用于偏见、毒性、有害性等多种隐含不安全内容，且对数据噪声比例鲁棒。
- **实验设计全面**：涵盖多种模型规模、多种安全概念、多种防御策略对比，并包括长期安全测试，结果可信度高。
- **实用价值**：为“发布-微调”范式提供了即插即用的安全微调前数据过滤方案，易于集成到实际系统。

## 8. 不足与局限

- **依赖安全示例集合**：ForgetFilter需要一组安全示例进行微调以计算遗忘率，若下游数据包含超出安全示例分布的新型不安全内容，过滤效果可能下降。
- **未验证更大模型**：实验最大模型为LLaMA-7B，未在更大模型（如LLaMA-13B/70B）上验证，可能限制可扩展性结论。
- **有害性评估不完整**：由于缺乏自动评估指标，有害性仅用于遗忘分析，未在安全微调对比实验中纳入，削弱了方法在有害性场景下的说服力。
- **计算开销**：ForgetFilter需要先微调、再安全微调、再过滤、再重新微调，流程较复杂，计算成本高于直接微调或回放。
- **参数选择**：阈值$\phi$和训练步数$t$需人工设定，虽论文提供指导，但自动化选择方法未探讨，可能存在应用门槛。

## （完）
