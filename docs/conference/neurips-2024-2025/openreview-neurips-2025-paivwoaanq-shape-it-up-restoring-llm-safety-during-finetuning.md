---
title: "Shape it Up! Restoring LLM Safety during Finetuning"
title_zh: "Shape it Up! 恢复LLM微调过程中的安全性"
authors: "ShengYun Peng, Pin-Yu Chen, Jianfeng Chi, Seongmin Lee, Duen Horng Chau"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=PAIVwOaAnq"
tags: ["query:smd"]
score: 9.0
evidence: 通过动态安全塑形在微调中恢复LLM安全性，增强安全内容抑制不安全内容
tldr: 微调会破坏LLM的安全对齐，现有方法对响应进行整体处理效果不佳。本文提出动态安全塑形（DSS）框架，利用细粒度安全信号在微调过程中动态加强安全片段、抑制不安全内容，从而有效恢复并维持模型安全性。实验表明DSS能显著抵御有害微调攻击，同时保持任务性能。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-paivwoaanq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-paivwoaanq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 716, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-paivwoaanq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 521, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-paivwoaanq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1446, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-paivwoaanq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1371, \"height\": 520, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-paivwoaanq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 596, \"height\": 616, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-paivwoaanq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 594, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-paivwoaanq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1353, \"height\": 1215, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 811, \"height\": 373, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 934, \"height\": 444, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1375, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1244, \"height\": 367, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 868, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 752, \"height\": 525, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 930, \"height\": 436, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1075, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 640, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1407, \"height\": 420, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1032, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 854, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 993, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 885, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 884, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 594, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 541, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 612, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-paivwoaanq/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 911, \"height\": 293, \"label\": \"Table\"}]"
motivation: 即使少量有害微调样本也可能破坏安全对齐，现有静态加权策略忽略响应内安全上下文变化。
method: 提出动态安全塑形（DSS），对每个响应片段计算安全分数并调整学习权重。
result: 在多个安全基准上DSS保持了高安全性且不降低任务准确率。
conclusion: DSS为微调中恢复LLM安全提供了细粒度、有效且通用的方法。
---

## Abstract
Finetuning large language models (LLMs) enables user-specific customization but introduces important safety risks: even a few harmful examples can compromise safety alignment. A common mitigation strategy is to update the model more strongly on examples deemed safe, while downweighting or excluding those flagged as unsafe. However, because safety context can shift within a single example, updating the model equally on both harmful and harmless parts of a response is suboptimal — an atomic treatment we term static safety shaping. In contrast, we propose dynamic safety shaping (DSS), a dynamic shaping framework that uses fine-grained safety signals to reinforce learning from safe segments of a response while suppressing unsafe content. To enable such fine-grained control during finetuning, we introduce a key insight: guardrail models, traditionally used for filtering, can be repurposed to evaluate partial responses, tracking how safety risk evolves throughout the response, segment by segment. This leads to the Safety Trajectory Assessment of Response (STAR), a token-level signal that enables shaping to operate dynamically over the training sequence. Building on this, we present ★DSS, a DSS method guided by STAR scores that robustly mitigates finetuning risks and delivers substantial safety improvements across diverse threats, datasets, and model families, all without compromising capability on intended tasks. We encourage future safety research to build on dynamic shaping principles for stronger mitigation against evolving finetuning risks. Our code is publicly available at https://github.com/poloclub/star-dss

---

## 论文详细总结（自动生成）

# 论文结构化中文总结

## 1. 核心问题与整体含义（研究动机和背景）

大型语言模型（LLM）通过微调可定制化，但微调过程极易破坏安全对齐——即使仅混入少数有害样本，就可能导致模型输出不安全内容。现有防御方法通常采用**静态安全塑形**（static safety shaping），即把每个训练样本视为原子单元，基于整体判定结果进行“保留/丢弃”的二元过滤（如拒绝采样 RS）。这种做法忽略了样本内部安全上下文的动态变化：同一响应中可能前半段安全、后半段有害。这种粗粒度处理方式存在两个致命盲点：
- **Guardrail 误分类**：误判的有害样本会被完整纳入训练；
- **上下文纠缠**：有害内容可以被包装在看似安全的开头/结尾中，绕过整体过滤。

论文据此提出**动态安全塑形（Dynamic Safety Shaping, DSS）**，旨在在微调过程中为每个令牌级别动态调整学习强度：对安全片段加强学习，对不安全片段施加抑制，从而在不牺牲任务能力的前提下恢复并维持模型安全性。

## 2. 方法论

### 核心思想
利用现有的 Guardrail 模型（如 Llama Guard、Granite Guardian），对部分完成的响应进行逐段安全评估，生成**STAR 分数（Safety Trajectory Assessment of Response）**——一种令牌级的安全信号，反映“到当前为止响应有多大概率保持安全”。该信号随后用于动态调整微调损失中的交叉熵（CE）和 KL 散度权重。

### 关键技术细节
- **STAR 分数定义**：给定 prompt x 和部分响应 y₁:ₜ，通过 Guardrail 模型输出的 logits 计算安全概率：
  \[
  V_{\text{safe}}(x, y_{1:t}) = \sigma(\text{logit}_{\text{safe}}^{(t)} - \text{logit}_{\text{unsafe}}^{(t)})
  \]
  其中 σ 为 sigmoid 函数。该分数作为轨迹安全的连续代理。
- **★DSS 损失函数**：将响应分成长度为 M token 的块（chunk），对每个块 k 计算一次 STAR 分数，并作用于该块内所有 token：
  \[
  \mathcal{L} = \sum_{k} \sum_{t \in \text{chunk}_k} \Big[ V_{\text{safe}}^{(k)} \cdot \mathcal{L}_{\text{CE}}(y_t) + (1 - V_{\text{safe}}^{(k)}) \cdot \lambda_{\text{KL}} \cdot \text{KL}(\pi_\theta \| \pi_{\text{ref}}) \Big]
  \]
  - 当 \(V_{\text{safe}} \approx 1\)：CE 主导 → 正常学习
  - 当 \(V_{\text{safe}} \approx 0\)：KL 散度正则化主导 → 阻止学习不安全内容
- **与 RLHF 的关系**：STAR 类似 advantage-weighted 更新中的软价值估计，但无需采样或奖励模型，完全基于前向传递。

### 理论分析（Theorem 1）
证明了 ★DSS 微调后的模型危害性上界由两项组成：
1. 序列级 KL 散度项（√2εKL），可通过 λKL 控制；
2. Guardrail 在 chunk 粒度下的最坏假阴性率 δchunk(M, τ)，随 chunk 变细或 Guardrail 更准而减小。

⇒ 危害性不会超出参考模型太多，保证了安全可恢复性。

## 3. 实验设计

### 数据集与评估指标
- **安全评估**：HEx-PHI、AdvBench，使用 GPT-4o 判断响应是否安全（Safety Score，越高越好）
- **能力评估**：MMLU（多任务理解）、ARC-Challenge（推理）、GSM8K（数学推理），使用准确率
- **训练数据**：
  - 有害：PureBad、BeaverTails、HH-RLHF（多轮）
  - 安全：Safe Instruct、GSM8K

### 攻击场景（Finetuning-as-a-Service）
四种现实场景组合：
| 用户意图 | 服务提供商有无安全数据集 |
|----------|--------------------------|
| 恶意（纯有害数据） | 无（worst-case） |
| 恶意 | 有（提供额外安全数据） |
| 良性（少量有害混入） | 无 |
| 良性 | 有（ideal-case） |

### 对比方法
- 基线：Vanilla SFT, Vaccine, Safe LoRA, LISA, SEAL, Safe Instruct, Deep Token, Rejection Sampling (RS)
- Guardrail 模型：Granite Guardian-3.1-2B/8B, Llama Guard-3-1B/8B
- LLM 模型：Llama-3.2-1B/3.1-8B/2-7B, Gemma-3-1B, Granite-3.3-2B, Qwen-2.5-3B

### 额外鲁棒性测试
- 响应适应攻击（添加误导前缀/后缀绕过 Guardrail）
- 提示注入攻击（backdoor trigger）
- 有害预填充攻击（inference-time prefilling）

## 4. 资源与算力

论文未明确报告总训练时长和 GPU 小时数。实验在**单节点 8 × A40 GPU**上进行。提供了 STAR 分数预计算时间表（表3）：
- 使用 Granite Guardian-3.1-2B 对 100 条 PureBad 样本（chunk M=5）耗时约 0.28 分钟；
- 使用 8B 版本约 0.82 分钟。
- 预计算可与训练管道并行化以降低开销。

## 5. 实验数量与充分性

实验非常充分：
- 主表（表1、2）对比了 6～8 种方法在 2 种核心场景下的安全和能力指标；
- 泛化实验（图4）覆盖了 6 个 LLM、4 个 Guardrail、5 个危害比例、3 个有害数据集；
- 对抗攻击实验（表14-17）评估了 4 种额外威胁；
- 消融实验（表18、19）分析了 chunk 大小 M 和 λKL 的影响；
- 附录还提供了扩展场景（表7-9）和跨 Guardrail 的 STAR 一致性分析。

所有实验均使用官方开源代码库中的超参数，并在同一条件（Llama‑3.2‑1B‑Instruct）下进行公平比较。设置了 GPT-4o 作为统一安全评估器，避免了人工偏差。实验覆盖全面、对比公平，充分支撑了论文结论。

## 6. 主要结论与发现

1. **静态塑形存在根本缺陷**：拒绝采样（RS）即使使用强 Guardrail，仍因上下文纠缠和误分类导致安全下降；添加误导后缀可使 RS 安全分数从 79.23% 暴跌至 14.81%。
2. **★DSS 在 worst-case 下最优**：在纯有害数据上，★DSS 安全分数（HEx-PHI 72.12%，AdvBench 89.42%）比最强基线 RS 提升 **20.41%**，且能力保持完好。
3. **★DSS 在 ideal-case 下平衡最好**：在混合安全数据场景下，★DSS 在安全和能力上普遍超越所有基线（表2）。
4. **跨模型/Guardrail/危害水平/数据集高度泛化**：★DSS 即使使用高 FN 率的 Guardrail 也仅下降 3.84%（RS 下降 22.88%），在不同 LLM 上均能恢复至原始模型安全水平。
5. **鲁棒对抗攻击**：对前缀/后缀欺骗、提示注入、预填充攻击均表现出强韧性，而 Deep Token 和 RS 常被绕过。
6. **理论保证**：模型危害性上界由 KL 项和 Guardrail 误差项决定，解释并指导了实际参数选择。

## 7. 优点

- **细粒度动态塑形**：首次将 token 级安全信号（STAR）引入微调，避免了原子化处理的盲点。
- **无需额外安全数据**：在 worst-case 场景下（无安全数据）仍有效，符合实际 finetuning-as-a-service 限制。
- **理论保障**：提供了危害性上界的数学证明，可指导 Guardrail 选择与 chunk 大小。
- **广泛跨域有效性**：多种模型、Guardrail、危害比例、有害数据集上一致优异表现。
- **易集成**：STAR 可预计算并缓存，微调时仅需一次性 Guardrail 前向，不影响训练效率。
- **与 RLHF 概念一致**：类比 advantage 加权，易于理解和扩展。

## 8. 不足与局限

- **计算开销**：STAR 预计算增加预处理时间（特别是小 chunk 和大型 Guardrail），虽可并行但仍是额外步骤。
- **Guardrail 依赖**：性能受 Guardrail 质量影响；强 Guardrail 并不一定需要大模型，但具体选择需根据安全策略调整，论文未探讨 Guardrail 本身偏见或失效边界。
- **未见大规模模型验证**：评测最大为 8B 参数，论文未测试 70B、百亿级模型，无法确认扩展性。
- **仅文本领域**：未涉及多模态微调（如图文 LLM）的安全性。
- **超参数 λKL 需微调**：消融显示不同 λKL 对安全/能力平衡有影响（表19），实际部署需少量调参。
- **对抗 Suffix 仍是新风险**：虽然 ★DSS 提升了鲁棒性，但理论上仍可能被精心设计的自适应攻击绕过 Guardrail 的 chunk 级判断（论文在 7.2 节讨论了该点并展示了初步韧性）。
- **未提供训练总时长**：无法直接衡量端到端计算成本。

（完）
