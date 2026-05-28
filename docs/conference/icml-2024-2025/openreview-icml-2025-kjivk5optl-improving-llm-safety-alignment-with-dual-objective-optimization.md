---
title: Improving LLM Safety Alignment with Dual-Objective Optimization
title_zh: 通过双目标优化改进LLM安全对齐
authors: "Xuandong Zhao, Will Cai, Tianneng Shi, David Huang, Licong Lin, Song Mei, Dawn Song"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Kjivk5OPtL"
tags: ["query:smd"]
score: 6.0
evidence: 双目标优化改进拒绝训练和有害知识遗忘
tldr: 现有安全对齐方法在拒绝学习上存在不足，本文通过梯度分析将DPO目标分解为鲁棒拒绝训练和有害知识遗忘两个组件，显著增强模型对越狱攻击的鲁棒性，为缓解微调安全退化提供新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-kjivk5optl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1410, \"height\": 633, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kjivk5optl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1699, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kjivk5optl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 849, \"height\": 348, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kjivk5optl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 851, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kjivk5optl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 851, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kjivk5optl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 856, \"height\": 334, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kjivk5optl/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 852, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kjivk5optl/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 848, \"height\": 285, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kjivk5optl/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 842, \"height\": 292, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kjivk5optl/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1683, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kjivk5optl/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1249, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kjivk5optl/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1244, \"height\": 506, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kjivk5optl/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1596, \"height\": 486, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-kjivk5optl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1767, \"height\": 349, \"label\": \"Table\"}]"
motivation: DPO在拒绝学习方面存在局限，导致安全对齐易受越狱攻击。
method: 解耦DPO目标为鲁棒拒绝训练和针对性有害知识遗忘两个成分。
result: 新方法在多种越狱攻击下（包括前缀、后缀等）显著提升模型鲁棒性。
conclusion: 双目标优化可有效增强LLM安全对齐，对抗越狱攻击。
---

## Abstract
Existing training-time safety alignment techniques for large language models (LLMs) remain vulnerable to jailbreak attacks. Direct preference optimization (DPO), a widely deployed alignment method, exhibits limitations in both experimental and theoretical contexts as its loss function proves suboptimal for refusal learning. Through gradient-based analysis, we identify these shortcomings and propose an improved safety alignment that disentangles DPO objectives into two components: (1) robust refusal training, which encourages refusal even when partial unsafe generations are produced, and (2) targeted unlearning of harmful knowledge. This approach significantly increases LLM robustness against a wide range of jailbreak attacks, including prefilling, suffix, and multi-turn attacks across both in-distribution and out-of-distribution scenarios. Furthermore, we introduce a method to emphasize critical refusal tokens by incorporating a reward-based token-level weighting mechanism for refusal learning, which further improves the robustness against adversarial exploits. Our research also suggests that robustness to jailbreak attacks is correlated with token distribution shifts in the training process and internal representations of refusal and harmful tokens, offering valuable directions for future research in LLM safety alignment. The code is available at https://github.com/wicai24/DOOR-Alignment.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义

- **研究动机**：现有的大语言模型（LLM）安全对齐技术（如直接偏好优化 DPO）在面对越狱攻击时依然脆弱。DPO 虽然简化了 RLHF，但其损失函数在拒绝学习（refusal learning）中存在系统性缺陷：不仅对安全响应的提升不足，而且在分布外泛化方面表现差。
- **整体含义**：本文旨在通过将 DPO 目标解耦为“鲁棒拒绝训练”和“针对性有害知识遗忘”两个互补组件，设计一种新的安全对齐框架 DOOR（及加权版本 W-DOOR），以显著增强模型对多种越狱攻击（前缀填充、后缀攻击、多轮对话攻击）的鲁棒性，同时保持模型的一般能力。

## 2. 方法论

- **核心思想**：
  - 鲁棒拒绝训练：通过数据增强，将有害前缀附加到原始提示之后，训练模型在部分生成有害内容后仍能“自我纠正”并发出拒绝回应。
  - 针对性遗忘：使用负偏好优化（NPO）主动降低模型生成有害内容的概率，消除有害知识路径。
  - 双目标损失 DOOR 结合两者，梯度分析显示其相比 DPO 有恒定的安全响应学习率（始终为1）和额外的所有词元 logit 减小项，从而改善泛化。
  - 加权的 W-DOOR 引入基于 token 级奖励的权重（β_t），对关键的拒绝词元（如“Sorry”、“cannot”）赋予更高训练权重，强化模型在有害前缀后的拒绝触发。

- **关键技术细节**：
  - **数据增强**：对每个有害提示 x，随机从有害响应 y_h 中选取前 k 个词元作为前缀拼接到 x 后，目标输出仍为安全响应 y_s，训练模型使用交叉熵最小化。
  - **NPO 目标**：基于参考模型对比，惩罚有害响应 y_h 的对数概率，避免直接梯度上升导致模型能力退化。
  - **DOOR 损失**：`L_DOOR = E[ -log π_θ(y_s | x ⊕ y_{h<k}) - (2/β) log σ(-β log(π_θ(y_h|x)/π_ref(y_h|x))) ]`
  - **W-DOOR 损失**：在第一个 SFT 项中加入 token 级权重 β_t，β_t 由“理想策略”π* 与参考策略 π_ref 的比值经指数变换得到，反映词元对拒绝的关键性。
  - **保留损失**：在通用数据集上使用标准 SFT 保持模型能力，总损失为 α·L_Align + (1-α)·L_Retain，α=0.2 权衡安全与效用。

- **算法流程**（文字说明）：
  1. 构建安全数据集：使用 SORRY-Bench 和 HEx-PHI，通过 jailbroken 模型生成有害响应，原模型生成安全响应，人工验证。
  2. 对每个有害样本，随机截取有害响应的前 k 个词元作为前缀，与原始提示拼接为增强输入。
  3. 对增强输入，使用带 token 权重（W-DOOR 中）的交叉熵训练模型生成安全响应（拒绝训练）。
  4. 同时对原有害样本，使用 NPO 损失降低模型生成有害响应的概率（遗忘）。
  5. 结合保留损失在通用数据上训练，防止能力退化。
  6. 训练 10 个 epoch，采用 AdamW 优化器，学习率 1e-5，bfloat16 精度。

## 3. 实验设计

- **数据集与场景**：
  - **安全评估**：SORRY-Bench（held-out 子集）用于单轮拒绝；Multi-Turn SORRY-Bench 通过 Crescendo 生成最多 10 轮的多轮对话；HarmBench 包含 GCG 和 AutoDAN 攻击。
  - **过保守评估**：XSTest 检测模型对安全查询的误拒绝率。
  - **通用能力评估**：MMLU 和 HellaSwag。
- **基准方法**：SFT、DPO、NPO（有无数据增强）、Gradient Ascent（GA）、Representation Rerouting (RR)、Tampering Attack Resistance (TAR)。部分基线来自公开权重。
- **模型**：Gemma-2-2B 和 Llama-3-8B。

## 4. 资源与算力

- 论文明确说明训练在 **NVIDIA H100 GPU** 上进行。
- 具体 GPU 数量未提及。
- 训练配置：batch size=2，gradient accumulation=1，learning rate=1e-5，10 epochs，bfloat16，sequence length=512。对应两种模型（2B 和 8B）的训练时间和成本未详细说明。

## 5. 实验数量与充分性

- **实验数量**：涵盖 3 种主要攻击类型（prefilling、GCG、AutoDAN）以及多轮攻击，每个攻击下报告 ASR，并在两个模型上重复。消融实验包括数据增强效果、token 权重变体（指数 vs sigmoid，不同 τ）、保留损失必要性、Pareto 分析（10 个 epoch 的 checkpoint 轨迹）。
- **充分性评价**：
  - **优点**：攻击类型覆盖全面（单轮/多轮、白盒/黑盒），对比方法多样（6+基线），使用公开基准和自动化评估（LLM-judge），并进行了能力保持和过拒绝的权衡分析。
  - **不足**：多轮攻击实验数据量稍小（约 100 个样本），且仅使用单一多轮生成方法 Crescendo；未测试更复杂的越狱类型如基于翻译、角色扮演等；评估依赖 GPT-4o-mini 作为 judge，可能引入偏好偏差。

## 6. 主要结论与发现

- DOOR 和 W-DOOR 在所有攻击类型上均显著低于 DPO 和其他基线，尤其是在前缀填充攻击中 ASR 降至接近 0（Gemma 上 W-DOOR 为 0.005）。
- 数据增强是提升鲁棒性的关键，但 DPO 从增强中受益有限，验证了其拒绝学习不足的理论分析。
- W-DOOR 比 DOOR 进一步降低了 ASR，尤其是在较长前缀下，且更不易在多轮攻击中随轮次增加而失效。
- 安全对齐的鲁棒性与 token 级别 KL 散度（与基础模型的分布偏移）以及内部表示（t-SNE 可视化显示安全/有害词元更易分离）正相关。
- 通过 Pareto 分析，最优安全-能力权衡通常在前 3 个 epoch 内达到，延长训练可同时降低过拒绝率和攻击成功率。

## 7. 优点

- **理论驱动**：通过梯度分解清晰指出 DPO 在安全对齐中的两大局限（学习率过早饱和、OOD 泛化差），为方法设计提供依据。
- **双目标互补**：拒绝训练和遗忘分别从“增强安全响应”和“消除有害知识”两个角度协同作用，比单一方法更有效。
- **token 级加权创新**：引入基于奖励的加权机制，自动识别关键拒绝词元，实现细粒度优化，且不同参数设置下鲁棒性不敏感，表明方法稳定。
- **分析全面**：不仅报告攻击成功率，还分析了 KL 散度、token 概率变化、内部表示分离、Pareto 前沿、过拒绝行为、奖励可视化等，深入揭示鲁棒性来源。
- **可复现性**：开源代码，训练配置详细，所有实验可在通用硬件上复现。

## 8. 不足与局限

- **多轮攻击鲁棒性有限**：所有方法在多轮攻击下 ASR 仍然较高（W-DOOR 约 0.35-0.45），表明当前方法对长上下文递进式攻击的防御不足，可能因为未使用多轮对话数据训练。
- **token 权重奖励的噪声**：参考策略可能未充分见过数据增强样本，导致权重分配存在噪声，部分非关键词元也被强调（如图 14-15 可视化显示一定噪声）。
- **数据增强可能引入过拒绝**：随机选择的前缀长度可能导致模型对无害前缀也产生拒绝，增加 XSTest 上的误拒绝率（尽管文中指出 W-DOOR 可通过延长训练缓解此问题）。
- **攻击覆盖有限**：未测试基于提示注入、语言迁移、模型逆向等更复杂的越狱变体；唯一的多轮方法 Crescendo 可能不代表所有多轮威胁。
- **评估依赖 LLM judge**：使用 GPT-4o-mini 进行自动评估，其自身可能有偏见或错误，建议加入人工抽查。
- **模型规模范围较小**：仅测试 2B 和 8B 模型，未在更大模型（如 70B）上验证，泛化性未知。
- **计算成本未详细报告**：未提供精确的训练时间或 GPU 小时，不利于其他研究者复现或比较效率。

（完）
