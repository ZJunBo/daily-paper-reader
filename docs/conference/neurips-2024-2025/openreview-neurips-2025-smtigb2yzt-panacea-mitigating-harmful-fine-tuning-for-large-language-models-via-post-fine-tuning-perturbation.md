---
title: "Panacea: Mitigating Harmful Fine-tuning for Large Language Models via Post-fine-tuning Perturbation"
title_zh: Panacea：通过微调后扰动缓解大语言模型的有害微调攻击
authors: "Yibo Wang, Tiansheng Huang, Li Shen, Huanjin Yao, Haotian Luo, Rui Liu, Naiqiang Tan, Jiaxing Huang, Dacheng Tao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=sMtiGB2YZT"
tags: ["query:smd"]
score: 8.0
evidence: 通过微调后添加扰动防御有害微调攻击
tldr: 针对有害微调攻击，该论文发现微调后添加纯随机扰动即可恢复模型安全性，但会损害微调性能。为此提出Panacea方法，通过优化自适应扰动来平衡安全恢复与任务性能保持。实验表明该方法能有效缓解有害微调带来的安全退化，为防御提供了一种简单有效的后处理方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-smtigb2yzt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 728, \"height\": 288, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-smtigb2yzt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 858, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-smtigb2yzt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 858, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-smtigb2yzt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 863, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-smtigb2yzt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1298, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-smtigb2yzt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 728, \"height\": 518, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-smtigb2yzt/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1278, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-smtigb2yzt/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1289, \"height\": 535, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1163, \"height\": 350, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 961, \"height\": 354, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1223, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1031, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1174, \"height\": 509, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1171, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 711, \"height\": 195, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 647, \"height\": 194, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 717, \"height\": 147, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 717, \"height\": 162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1149, \"height\": 669, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 955, \"height\": 348, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 957, \"height\": 312, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1321, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 875, \"height\": 334, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1448, \"height\": 143, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 813, \"height\": 190, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1444, \"height\": 160, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 883, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1454, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1012, \"height\": 1118, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-smtigb2yzt/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1438, \"height\": 499, \"label\": \"Table\"}]"
motivation: 现有疫苗式防御在少量有害微调步骤后失效，需要更鲁棒的防御方法。
method: 提出微调后添加自适应随机扰动，并优化扰动幅度以平衡安全性与任务性能。
result: 在多个模型上验证，该方法能有效恢复安全性且性能损失可控。
conclusion: 微调后扰动是一种简单有效的有害微调防御手段，具有实际部署潜力。
---

## Abstract
Harmful fine-tuning attack introduces significant security risks to the fine-tuning services. Main-stream defenses aim to vaccinate the model such that the later harmful fine-tuning attack is less effective. However, our evaluation results show that such defenses are fragile-- with a few fine-tuning steps, the model still can learn the harmful knowledge. To this end, we do further experiment and find that an embarrassingly simple solution-- adding purely random perturbations to the fine-tuned model, can recover the model from harmful behaviors, though it leads to a degradation in the model’s fine-tuning performance. To address the degradation of fine-tuning performance, we further propose \methodname, which optimizes an adaptive perturbation that will be applied to the model after fine-tuning. \methodname maintains model's safety alignment performance without compromising downstream fine-tuning performance. Comprehensive experiments are conducted on different harmful ratios, fine-tuning tasks and mainstream LLMs, where the average harmful scores are reduced by up-to 21.2%, while maintaining fine-tuning performance. As a by-product, we analyze the adaptive perturbation and show that different layers in various LLMs have distinct safety coefficients. Source code available at https://github.com/w-yibo/Panacea.

---

## 论文详细总结（自动生成）

# 论文《Panacea: Mitigating Harmful Fine-tuning for Large Language Models via Post-fine-tuning Perturbation》中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：大语言模型（LLM）在“微调即服务”场景下，即使微调数据集中仅包含少量有害样本，也会导致模型的安全对齐被破坏（即“有害微调攻击”）。
- **现有防御的不足**：主流防御方法（如Vaccine、RepNoise）试图在微调前对模型进行“疫苗式”加固，但实验表明这些防御脆弱——经过少量微调步骤后，模型仍能学会有害知识。
- **研究意义**：探索一种更鲁棒、简单的后处理防御思路，在微调完成后通过添加扰动恢复模型安全性，同时保持下游任务性能。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：在微调完成后，对模型参数添加一个精心优化的自适应扰动，该扰动能够最大化有害损失（即让模型对有害指令重新变得“不敏感”），同时最大限度保持微调任务性能。
- **关键技术细节**：
  1. **发现**：纯随机扰动可以降低模型有害分数，但会严重损害微调精度。
  2. **Panacea 优化目标**：求解一个 max-max 问题
     \[
     \max_{w} \max_{\varepsilon: \|\varepsilon\|\le \rho} \lambda\big(h(w+\varepsilon)-h(w)\big) - g(w)
     \]
     其中 \(w\) 为模型参数，\(\varepsilon\) 为扰动，\(h(w)\) 为有害数据集上的损失，\(g(w)\) 为微调数据集上的损失，\(\lambda\) 为平衡系数，\(\rho\) 为扰动范数约束。
  3. **求解方法**：交替优化
     - 内层近似闭式解：\(\varepsilon_t^* = \rho \frac{\nabla h(w_t)}{\|\nabla h(w_t)\|}\)
     - 外层梯度更新：\(w_{t+1} = w_t + \eta\big[\lambda(\nabla h(w_t+\varepsilon_t^*)-\nabla h(w_t)) - \nabla g(w_t)\big]\)
  4. **算法流程**（Algorithm 1）：在微调阶段，每个迭代批次同时计算微调梯度、有害梯度，然后构造扰动，更新模型参数；微调结束后，将最后一步的扰动加到模型参数上得到最终安全模型。

## 3. 实验设计：数据集、Benchmark、对比方法
- **数据集**：
  - 对齐数据集：BeaverTails 子集（5000条有害指令-无害响应）
  - 有害数据集：BeaverTails 子集（1000条有害指令-有害响应）
  - 下游微调任务：GSM8K（数学）、SST2（情感）、AlpacaEval（指令跟随）、AGNEWS（新闻分类），每任务取700-1000条
  - 攻击数据：混合上述良性数据与不同比例（p=0, 0.05, 0.1, 0.15, 0.2）的有害数据
- **评价指标**：
  - 有害分数（HS）：由BeaverTails审核模型评估，越低越好
  - 微调精度（FA）：各下游任务测试集上的准确率
- **对比方法**：
  - SFT（标准监督微调对齐）
  - Vaccine、RepNoise、Booster（对齐阶段防御）
  - Antidote（微调后防御）
  - 额外对比：Safe LoRA、ConstrainSFT、Security Vectors（discussion中提及）

## 4. 资源与算力
- **文中明确说明**：
  - 默认使用 LoRA 训练（rank=32，alpha=4），AdamW 优化器。
  - 对齐阶段：学习率5e-4，batch size=10，20 epochs；微调阶段：学习率2e-5，batch size=10，20 epochs。
  - 大部分实验在单张 L40S 上完成；RepNoise 和其他较大模型（Gemma2-9B, Qwen2-7B）使用单张 A100-80G。
  - 训练耗时对比（Table 14）：SFT总耗时0.75h，Panacea 1.00h，Vaccine 1.29h，RepNoise 2.84h，Booster 2.04h。Panacea 仅比 SFT 多0.25h。
  - GPU 内存：Panacea 与 SFT 相当（约34.9GB），显著优于 Vaccine（44.42GB）和 RepNoise（72.47GB）。

## 5. 实验数量与充分性
- **实验组数**：共进行了数十组实验，覆盖如下维度：
  - 5种有害比例（0, 0.05, 0.1, 0.15, 0.2）
  - 4种下游任务（GSM8K, SST2, AlpacaEval, AGNEWS）
  - 3种主流LLM（Llama2-7B, Gemma2-9B, Qwen2-7B）
  - 3种预对齐模型（Llama2-7B-Chat, Gemma2-9B-It, Qwen2-7B-Instruct）
  - 额外基准：AdvBench & Sorry-Bench 评估、不同有害数据源（LLM-LAT代替BeaverTails）
  - 消融实验：有无自适应扰动、不同扰动尺度、不同超参数（ρ, λ）
  - 可视化分析：层权重分布
- **充分性评估**：实验设计全面，覆盖了不同攻击强度、任务类型、模型规模及实际预对齐模型场景。消融、超参数分析、案例研究齐全，结论可靠。对比方法包括主流对齐防御及后处理防御，公平性较好（均使用相同LoRA和训练配置）。

## 6. 论文主要结论与发现
- **核心结论**：Panacea 通过微调后添加优化的自适应扰动，能有效恢复模型安全对齐，同时几乎不损害下游任务性能。平均有害分数降低21.2%，微调精度比SFT提升0.4%。
- **关键发现**：
  - 纯随机扰动虽可降低有害分数，但会严重损害性能。
  - 不同LLM的安全关键层分布不同：Llama2-7B早期层重要，Gemma2-9B中间/后期层重要，Qwen2-7B后期层重要。
  - 微调后期有害损失收敛是导致有害分数飙升的关键，Panacea的扰动破坏了该收敛。
- **与其他方法比较**：Panacea 在几乎所有设置下均取得最低有害分数，且微调精度与SFT持平或更好，优于所有对比方法。

## 7. 优点
- **方法简单有效**：后处理思路巧妙，无需修改对齐阶段即可应用于已对齐模型（如Chat版本）。
- **计算开销低**：仅比标准微调多0.25小时，内存占用与SFT相当，远低于其他对齐防御。
- **无需先验知识**：扰动自动优化，无需预定义安全子空间或关键参数。
- **实验充分**：覆盖多种模型、任务、攻击比例，并额外验证了跨数据源的泛化能力。
- **可解释性贡献**：通过扰动权重可视化揭示了不同模型层的安全重要性差异，与之前研究一致。

## 8. 不足与局限
- **仅使用LoRA**：实验基于LoRA微调，未验证全参数微调情况下的效果，可能影响实用性（但作者认为方法本质不变）。
- **模型规模有限**：主要实验在7B-9B模型上进行，未覆盖更大模型（如70B）或闭源模型。
- **超参数依赖**：ρ和λ需针对数据集/模型微调，实际部署中可能需要少量调参。
- **额外计算**：虽然总时间增加不多，但微调阶段每步需两次额外梯度计算（有害梯度+带扰动有害梯度），对内存和计算仍有额外开销。
- **局限性说明**：作者在附录F中已明确承认上述限制，并指出仅在开源小模型上实验，且未考虑更大模型和全参数设置。

（完）
