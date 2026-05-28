---
title: "Safe Delta: Consistently Preserving Safety when Fine-Tuning LLMs on Diverse Datasets"
title_zh: 安全Delta：在多样化数据集上微调LLM时一致保持安全性
authors: "Ning Lu, Shengcai Liu, Jiahao Wu, Weiyu Chen, Zhirui Zhang, Yew-Soon Ong, Qi Wang, Ke Tang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=QsCDgFKErb"
tags: ["query:smd"]
score: 9.0
evidence: Safe Delta通过调整模型参数防御有害微调攻击
tldr: 针对微调服务中用户上传数据可能破坏模型安全对齐的问题，本文提出Safe Delta方法，通过安全感知的后训练调整Delta参数，在多种微调数据集上一致保持模型安全性。实验表明该方法在保持模型效用的同时显著缓解安全退化，为微调阶段的安全防御提供实用方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-qscdgfkerb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 851, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qscdgfkerb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 771, \"height\": 392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qscdgfkerb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1757, \"height\": 549, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qscdgfkerb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 847, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qscdgfkerb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 843, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qscdgfkerb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 762, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qscdgfkerb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 683, \"height\": 403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qscdgfkerb/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 882, \"height\": 466, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-qscdgfkerb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 815, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qscdgfkerb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1512, \"height\": 448, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qscdgfkerb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 830, \"height\": 703, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qscdgfkerb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1511, \"height\": 381, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qscdgfkerb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 781, \"height\": 135, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qscdgfkerb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 738, \"height\": 211, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qscdgfkerb/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 829, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qscdgfkerb/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1305, \"height\": 203, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qscdgfkerb/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1712, \"height\": 201, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qscdgfkerb/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1335, \"height\": 494, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qscdgfkerb/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 578, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qscdgfkerb/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1458, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qscdgfkerb/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 922, \"height\": 254, \"label\": \"Table\"}]"
motivation: 微调服务中用户上传的数据可能破坏模型安全对齐，现有防御方法难以兼顾安全性和效用。
method: 提出Safe Delta，一种安全感知的后训练方法，通过调整模型Delta参数来保持安全对齐。
result: Safe Delta在多种微调场景下有效保持模型安全性，同时不显著降低任务效用。
conclusion: Safe Delta为微调阶段的LLM安全防御提供了有效且实用的方法。
---

## Abstract
Large language models (LLMs) have shown great potential as general-purpose AI assistants across various domains. To fully leverage this potential in specific applications, many companies provide fine-tuning API services, enabling users to upload their own data for LLM customization. However, fine-tuning services introduce a new safety threat: user-uploaded data, whether harmful or benign, can break the model’s alignment, leading to unsafe outputs. Moreover, existing defense methods struggle to address the diversity of fine-tuning datasets (e.g., varying sizes, tasks), often sacrificing utility for safety or vice versa. To address this issue, we propose Safe Delta, a safety-aware post-training defense method that adjusts the delta parameters (i.e., the parameter change before and after fine-tuning). Specifically, Safe Delta estimates the safety degradation, selects delta parameters to maximize utility while limiting overall safety loss, and applies a safety compensation vector to mitigate residual safety loss. Through extensive experiments on four diverse datasets with varying settings, our approach consistently preserves safety while ensuring that the utility gain from benign datasets remains unaffected.

---

## 论文详细总结（自动生成）

# Safe Delta: 在多样化数据集上微调LLM时一致保持安全性

## 1. 核心问题与整体含义（研究动机和背景）

- **研究背景**：大语言模型（LLM）作为通用AI助手在各领域广泛应用。许多公司提供微调API服务，允许用户上传自己的数据对LLM进行定制化微调。然而，微调服务引入了一个新的安全威胁：用户上传的数据（无论有害还是良性）都可能破坏模型的安全对齐，导致模型输出不安全内容。
- **现有方法不足**：现有防御方法（数据增强、权重修改等）难以应对多样化微调数据集（不同规模、不同任务）带来的挑战。数据增强方法在有害数据集规模增大时效果下降；权重修改方法难以平衡安全性与效用，需要针对每个请求调整超参数，计算开销大。
- **本文目标**：提出一种能够一致保持安全性的防御方法，在不牺牲良性微调效用增益的前提下，有效抵御有害微调带来的安全退化。

## 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：Safe Delta是一种安全感知的后训练防御方法，通过调整Delta参数（微调前后参数变化）来保持模型安全对齐。其主要步骤包括：
  1. **估计安全退化**：利用Hessian矩阵（基于原始模型和安全数据集计算）量化每个Delta参数对安全损失的影响。
  2. **选择Delta参数**：计算每个参数的效用-安全比（utility-safety ratio），按比值降序贪心选择参数，直到累积安全退化超过预设阈值。该比值利用定理4.1推导得出，其中安全退化量δL^safe_m = (δw_m)^2 / (2 [H^{-1}]_mm)，效用改进量δL^util_m = -(δw_m)^2。
  3. **添加安全补偿向量**：基于最优脑外科医生（OBS）原理，计算一个安全补偿向量C，用于抵消所选Delta参数带来的残余安全退化。该向量形式为C_m = (δw_m / [H^{-1}]_mm) * H^{-1}_{:,m}。
- **算法流程**：
  - **准备阶段**：在微调前，基于原始模型和安全数据集计算Hessian矩阵及其逆矩阵，并缓存H^{-1}（仅需计算一次）。
  - **标准微调**：对每个微调请求，执行标准微调，得到Delta参数ΔW_sft。
  - **Step 1（选择）**：对每层参数，计算每个Delta参数的安全退化值和效用-安全比，按比值排序，贪心选择直到安全退化阈值ϵ（由缩放因子s和层中参数均值决定）。
  - **Step 2（补偿）**：计算安全补偿向量C = (I - M) ⊙ Σ_{m∈S_M} C_m，其中M为选择掩码。最终模型W_sd = W_orig + M ⊙ ΔW_sft + C。
- **技术细节**：方法适用于全参数微调和LoRA微调。Hessian计算仅依赖原始模型和安全数据，可预计算复用，效率较高。

## 3. 实验设计：数据集、场景、Benchmark、对比方法

- **模型**：主要使用Llama2-7B-Chat，也验证了Llama3-8B-instruct和Llama2-13B-chat。
- **微调数据集**（4种，涵盖有害和良性场景）：
  - **PureBad**：100个显式有害示例，用于模拟有害微调。
  - **Identity Shift**：100个隐式有害示例（绝对服从Agent），采样自Alpaca数据集。
  - **Dirty Summary**：1000个SamSum摘要样本 + 100个PureBad有害样本（良性+有害混合）。
  - **Math**：7500个GSM8k数学问题（完全清洁）。
- **安全评估**：使用Policy-Oriented Safety Evaluation Benchmarks（330个问题，11个有害类别），评估指标：Attack Success Rate (ASR) 和 Harmfulness Score (HS)（由GPT-4打分，1~5）。
- **效用评估**：
  - 对于有害微调：MMLU（57个科目测试准确率）和MT-Bench（GPT-4打分，10分制）。
  - 对于良性微调：Dirty Summary用ROUGE-1 F1，Math用正确率。
- **对比基线**：
  - 数据增强：SafeInstr（增强安全样本）、BEA（后门增强对齐）。
  - 权重修改：Safe LoRA（投影到安全子空间）、Resta（添加安全任务向量）。
- **实验场景**：
  - 有害微调（PureBad、Identity Shift）和良性微调（Dirty Summary、Math）。
  - 不同有害数据集规模（50, 100, 150, 200）。
  - 安全-效用权衡分析（超参数扫描）。
  - LoRA微调实验。
  - 不同LLM模型迁移实验。
  - 对抗过防御评估（OR-Bench）。
  - 消融实验（去除安全补偿向量）。
  - 阈值缩放因子s的影响。
  - 时间成本分析。

## 4. 资源与算力

- **计算资源**：论文提到“All experiments were conducted on a 7B model using a single A100-80G GPU”，并使用5次实验取平均。具体GPU数量未明确说明，通常为单个GPU。Fine-tuning使用AdamW优化器。Safe Delta的额外时间成本平均为62秒/微调请求，准备阶段（Hessian计算）耗时210秒（针对7B模型）。
- **未明确说明**：训练的总时长、具体epoch数已在附录中给出（如PureBad 5 epochs，学习率5e-5等），但整体实验总耗时未提及。

## 5. 实验数量与充分性

- **实验数量**：论文进行了大量的实验，包括：
  - 有害微调（2个数据集）× 4种基线 + Safe Delta，含安全与效用指标（约4组主实验）。
  - 良性微调（2个数据集）× 4种基线 + Safe Delta（约4组）。
  - 不同有害数据集规模（4种规模）× 2个数据集 × 3种方法（数据增强+Safe Delta）——约8组。
  - 安全-效用权衡（2张图，扫描超参数）。
  - LoRA实验（2个数据集对比）。
  - 不同LLM模型（3个模型 × 2个数据集）。
  - 消融实验（去除补偿向量）。
  - 阈值影响实验。
  - 时间成本对比（3种方法）。
  - 对抗基于LLM的越狱攻击（GCG, AutoDAN, PAIR）实验。
  - 内容过滤方法对比（附录）。
- **充分性与公平性**：实验设计较为全面，覆盖了各种微调场景（有害/良性、不同规模、不同模型、不同微调方法）。基线方法均采用推荐超参数，且Safe Delta使用固定超参数（s=0.1），不进行针对每个数据集的调优，体现了方法的一致性优点。同时进行了消融和超参数影响分析，使结论更扎实。实验结果以表格和曲线呈现，统计可靠性较好。

## 6. 主要结论与发现

- **安全性能**：Safe Delta在有害微调和良性微调数据集上均取得最低的ASR和Harmfulness Score，显著优于所有基线方法。例如在PureBad上ASR仅3.33%（原始模型2.73%，Fine-Tuned 95.76%），在Identity Shift上ASR仅0.91%。
- **效用保持**：Safe Delta的效用（MMLU、MT-Bench、ROUGE-1、Math准确率）接近甚至优于其他基线，且与Fine-Tuned模型相比下降很小，表明其很好地平衡了安全与效用。
- **一致性**：在不同有害数据集大小（50~200）下，Safe Delta始终维持低ASR，而数据增强方法随着规模增大性能显著下降。
- **泛化能力**：Safe Delta有效适用于不同LLM（Llama-2-7B, Llama-3-8B, Llama-2-13B）和LoRA微调。
- **过防御问题**：Safe Delta不会导致过度拒绝良性查询，OR-Bench上的过拒绝率与原始模型相当（约18.3%）。
- **补偿向量重要性**：消融实验表明，去除安全补偿向量后ASR从5.15%升至26.97%，说明补偿向量是关键组件。
- **效率**：Safe Delta额外时间开销较小（62秒/请求），且Hessian可预计算复用，适合实际部署。

## 7. 优点

- **方法创新**：首次将安全退化估计与Delta参数动态优化结合，采用OBS原理推导补偿公式，实现了参数级别的安全-效用权衡。
- **一致性与泛化性**：在同一超参数下，Safe Delta在多个不同类型数据集、不同规模、不同模型上均表现稳定，显著优于现有方法。
- **高效增量**：准备阶段只需计算一次Hessian逆，后续微调请求复用，计算开销小；使用贪心选择和块状处理，内存效率高。
- **兼容性**：支持全参数微调和LoRA微调，可集成到现有微调服务流程中。
- **实验充分**：涵盖多维度实验（不同数据集、规模、模型、微调方式、消融、超参数、对抗攻击），结果可靠。

## 8. 不足与局限

- **对抗性数据可能规避**：论文承认，精心设计的有害微调数据可能绕过Safe Delta的修正（例如刻意设计参数使补偿失效），需要进一步研究。
- **贪心选择非最优**：当前采用贪心选择Delta参数，理论上可能存在更好的选择策略（如动态规划或整数优化），但计算复杂度可能更高。
- **仅覆盖文本安全**：未涉及多模态LLM（如视觉-语言模型）的安全问题，未来可扩展。
- **Hessian计算依赖安全数据集**：安全数据集的质量和代表性会影响Hessian的准确性，若安全数据集不全面可能影响防御效果。
- **超参数s需要手动设定**：虽然实验显示s的鲁棒性较好，但不同应用场景可能需调整，未提供自适应选择方法。
- **实验未覆盖所有可能攻击**：仅测试了三种越狱攻击，未评估更复杂或针对性的攻击方法；也未与其他新型防御方法（如LISA、Antidote等）对比，但这些方法可能属于不同防线（训练阶段）。
- **时间成本分析仅针对单GPU**：在大规模部署中，Hessian预计算可能成为瓶颈，未讨论多GPU并行方案。

（完）
