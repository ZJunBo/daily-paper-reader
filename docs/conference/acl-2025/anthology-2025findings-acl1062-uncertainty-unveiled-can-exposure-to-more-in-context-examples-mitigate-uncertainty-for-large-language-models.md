---
title: "Uncertainty Unveiled: Can Exposure to More In-context Examples Mitigate Uncertainty for Large Language Models?"
title_zh: 不确定性揭示：更多上下文示例能否降低大语言模型的不确定性？
authors: "Yifei Wang, Yu Sheng, Linjing Li, Daniel Dajun Zeng"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.findings-acl.1062.pdf"
tags: ["query:luq"]
score: 8.0
evidence: 上下文示例数量对大语言模型不确定性的影响
tldr: 研究上下文示例数量对大语言模型预测不确定性的影响，发现增加示例主要降低认知不确定性，并提出了新的不确定性分解视角。
source: ACL-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1062/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 807, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1062/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 812, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1062/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1505, \"height\": 507, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1062/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 822, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1062/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1647, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1062/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 816, \"height\": 289, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1062/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 802, \"height\": 348, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1062/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 806, \"height\": 307, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1062/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1402, \"height\": 729, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1062/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1409, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1062/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1560, \"height\": 379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1062/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1351, \"height\": 1124, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1062/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1596, \"height\": 789, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1062/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1599, \"height\": 1026, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1062/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 814, \"height\": 315, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1062/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1503, \"height\": 676, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1062/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 803, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1062/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1159, \"height\": 312, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1062/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1291, \"height\": 312, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1062/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1074, \"height\": 312, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1062/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 941, \"height\": 312, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1062/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1652, \"height\": 579, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1062/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1651, \"height\": 579, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1062/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1651, \"height\": 576, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1062/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1652, \"height\": 951, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1062/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1651, \"height\": 971, \"label\": \"Table\"}]"
motivation: 现有研究主要关注上下文示例对性能的提升，但对其如何影响模型输出的可信度（不确定性）知之甚少。
method: 系统量化不同示例配置下的预测不确定性，并通过不确定性分解区分认知不确定性和偶然不确定性。
result: 实验表明增加示例主要降低认知不确定性，但偶然不确定性可能变化不大，且模型在示例数量增加时仍可能过度自信。
conclusion: 该研究为上下文学习中不确定性的来源提供了新见解，指导更可信的模型部署。
---

## Abstract
Recent advances in handling long sequences have unlocked new possibilities for long-context in-context learning (ICL). While existing research predominantly focuses on performance gains driven by additional in-context examples, the impact on the trustworthiness of generated responses remains underexplored. This paper addresses this gap by investigating how increased examples influence predictive uncertainty—an essential aspect in trustworthiness. We begin by systematically quantifying uncertainty across different “shot” configurations in ICL, emphasizing the role of example quantity. Through uncertainty decomposition, we introduce a novel perspective on performance enhancement, focusing on epistemic uncertainty (EU). Our results reveal that additional examples reduce total uncertainty in both simple and complex tasks by injecting task-specific knowledge, thereby diminishing EU and enhancing performance. For complex tasks, these advantages emerge only after addressing the increased noise and uncertainty associated with longer inputs. Finally, we investigate the progression of internal confidence across layers, uncovering the underlying mechanisms that drive the reduction in uncertainty.

---

## 论文详细总结（自动生成）

# 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在长上下文上下文学习（Long-context In-context Learning, ICL）场景下，增加上下文示例的数量是否能够降低大语言模型（LLM）的预测不确定性？不确定性是衡量模型输出可信度的关键指标，此前研究主要关注性能提升，对可信度方面关注不足。
- **研究动机**：近年来，长序列处理能力的提升使得“多示例 ICL”（many-shot ICL）成为可能（如输入数百甚至数千个输入-输出对）。尽管已有工作展示了性能增益，但模型输出的可靠性和信任度仍缺乏系统探究。因此，本文旨在填补这一空白，从不确定性量化（Uncertainty Quantification, UQ）角度分析示例数量对模型自信度的影响。
- **整体含义**：理解不确定性如何随示例数量变化，有助于评估 LLM 在高风险场景下的可信度，并为 ICL 的实际部署提供指导。

# 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：
  - 对 ICL 进行不确定性量化：通过计算预测分布的总熵（Total Uncertainty, TU），并将其分解为**认知不确定性（Epistemic Uncertainty, EU）** 和**偶然不确定性（Aleatoric Uncertainty, AU）**。EU 源于模型知识不足，AU 源于数据内在噪声。
  - 在分类和多选题（MCQA）任务中，定义输出为离散标签，通过采样不同演示集和模型配置（如 beam search、温度参数）获得概率矩阵，进而计算熵值和分解。

- **关键技术细节**：
  - **预测分布建模**：对每个测试样本，从训练集中随机采样 L 个不同的演示集（shots），每个演示集下用 beam search 生成 m 个解码序列，得到 L×m 的概率矩阵 A（大小为 L × |Y|）。将不同演示集得到的概率归一化后，计算总熵 TU = H(σ(Σ[A_j,:]))。
  - **不确定性分解**：基于贝叶斯观点，EU = (1/L) Σ H(σ(A_j,:))，AU = TU - EU。EU 对应不同演示集下的平均熵，AU 对应互信息（TU 与 EU 之差）。
  - **实验流程**：模型（未微调的基座模型）使用长上下文支持（如 Llama-3.1-8B 支持 128K tokens），在不同 k-shot 设置下运行，k 从 1 到 240 不等。生成时使用 beam search（宽度=10），温度=0.7，每个演示集采样6个不同集合（L=6）以分解不确定性。

# 3. 实验设计：数据集、基准、对比方法

- **数据集**：
  - **简单模式（Easy Mode）**：AG News（新闻分类）、SST-2（情感分类）、CommonsenseQA（常识问答，多选题）。
  - **困难模式（Hard Mode）**：BIG-Bench Hard 中的三个逻辑推理任务，即逻辑演绎（Logical Deduction）涉及3个、5个和7个对象（LD3、LD5、LD7）。

- **基准与对比**：
  - 模型：三个主流 7B-8B 级别模型（Llama-3.1-8B、Mistral-7B-v0.2、Qwen1.5-7B），均为基础版本（未指令微调）。另外扩展实验使用更大模型 Qwen2.5-14B-Instruct 和 Qwen2.5-32B-Instruct。
  - 对比配置：不同 shot 数量（1-shot、2-shot、4-shot、8-shot、16-shot、32-shot、64-shot、128-shot 等）以及在困难模式下 1-shot 到 240-shot。
  - 评估指标：AUROC（评估不确定性质量）、准确率（Acc）、总不确定性（TU）、认知不确定性（EU）、偶然不确定性（AU）。
  - 消融实验：对比“重复示例”（将少量示例重复多次）与“不同示例”对不确定性降低的影响，以验证信息多样性的作用。

# 4. 资源与算力

- **明确信息**：所有开源模型来自 Hugging Face，在 **8 个 NVIDIA RTX A100（80GB）GPU** 上运行。模型权重以 float16 精度加载。
- **训练时长**：文中未具体说明训练或推理时长。实验为推理评估，不涉及微调，但需要处理长上下文，计算量较大。
- **备注**：由于是大规模实验（多个模型、多个 shot 配置、多个数据集），总计算开销可观但未给出精确数字。

# 5. 实验数量与充分性

- **实验数量**：
  - 主实验涵盖 3 个基础模型 × 6 个任务（3 简单 + 3 困难）× 8~9 种 shot 配置，共约 150+ 种组合条件，每种条件计算不确定性并报告均值与误差带（3次运行）。
  - 附加实验：更大模型（14B、32B）在 AG News 和 LD5 上的结果；消融实验（重复 vs 不同示例）；内部表示分析（投射残差流到词汇空间）。
  - 不确定性质量验证：对每个模型任务计算 AUROC，确认 UQ 指标有效。
- **充分性与公平性**：
  - 实验设计较完善，同时覆盖简单与复杂任务，验证了不同模型规模下的趋势一致性。
  - 对比了不同 shot 数量以及零-shot、少-shot、多-shot，并分析了微观（问题级别）不确定性变化。
  - 消融实验区分了长度效应与信息效应，内部机制分析通过可视化 logit 和概率变化提供解释性证据。
  - 但未包含开放式生成任务（如摘要、翻译）以及 CoT 等推理范式，实验覆盖存在局限。此外，所有模型均为基座模型，指令微调模型仅在大模型上做了部分验证。

# 6. 论文的主要结论与发现

- **主要结论**：
  1. **更多示例降低总不确定性（TU）**：在简单任务中，少量示例即可快速降低 TU；在复杂任务中，需要数百个示例才能显著降低 TU，且 TU 的降低主要由**认知不确定性（EU）下降**驱动。
  2. **性能提升源于信息丰富性而非长度**：对比重复示例与不同示例，只有不同示例能有效降低 EU，说明多样性的信息内容才是关键。
  3. **内部机制**：更多示例使模型在残差流中逐渐将更多的 logit 质量集中在正确答案上，扩大正确答案与干扰项的 logit 差距，从而降低预测不确定性。
  4. **模型规模影响**：更大模型（32B）在更多示例下 EU 继续降低，AU 也会下降（受长上下文噪声影响较小），而较小模型在复杂任务中 AU 可能上升。
  5. **不确定性质量良好**：AUROC 值高且随 shot 增加波动小，说明所用 UQ 指标有效。

# 7. 优点：方法或实验设计上的亮点

- **研究角度新颖**：首次系统研究长上下文 ICL 的不确定性进化，填补了该领域关于可信度的空白。
- **不确定性分解框架**：引入贝叶斯分解，区分认知和偶然不确定性，深入揭示性能提升的来源。
- **内部机制可视化**：通过残差流投射到词汇空间，展示了模型内部自信度随层数变化的动态过程，提供了直观解释。
- **实验设计严谨**：涵盖简单与复杂任务、多种模型规模和 shot 配置；控制变量（重复 vs 不同示例）验证信息作用；AUROC 验证 UQ 指标可靠性。
- **实用建议**：建议在实际应用中采用较大的 k 值，既提升性能又增强可靠性。

# 8. 不足与局限

- **任务覆盖不足**：仅考虑分类和多选题任务，未包含开放式生成任务（如摘要、翻译、自由形式问答），其不确定性量化更复杂。
- **ICL 范式局限**：未探索链式思维（CoT）提示、无监督 ICL、强化 ICL 等，尤其是 CoT 中不确定性传播难以捕捉。
- **极端 shot 场景缺失**：受限于当前开源模型上下文长度和计算开销，未验证数千个演示的极端多人 shot ICL。
- **不确定性方法局限**：现有 UQ 方法难以处理多步推理中的不确定性累积；对逻辑推理任务，单纯基于 logit 的熵可能无法完全反映推理过程的不确定性。
- **模型范围**：主要基于 7B-8B 基座模型，指令微调模型仅在大模型上部分实验，可能影响结论的泛化性。
- **偏差风险**：随机采样演示集可能引入选择偏差；虽多次运行取平均，但未系统讨论演示集质量对不确定性的影响。

（完）
