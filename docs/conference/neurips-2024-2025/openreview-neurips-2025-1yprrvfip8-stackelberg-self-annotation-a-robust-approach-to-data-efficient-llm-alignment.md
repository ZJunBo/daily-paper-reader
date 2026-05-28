---
title: "Stackelberg Self-Annotation: A Robust Approach to Data-Efficient LLM Alignment"
title_zh: Stackelberg自标注：一种鲁棒且数据高效的大语言模型对齐方法
authors: "Xu Chu, Zhixin Zhang, Tianyu Jia, Yujie Jin"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=1YprrVfIp8"
tags: ["query:smd"]
score: 7.0
evidence: 自标注生成偏好数据，对噪声鲁棒，涉及对齐数据策展
tldr: 该论文提出基于Stackelberg博弈的偏好优化框架SGPO及其自标注实例SSAPO。SSAPO利用少量人类种子偏好迭代自标注新提示，在保证对标注噪声鲁棒性的同时实现数据高效的对齐。该方法与用户需求中的数据策展与选择高度相关，提供了一种自动化的安全数据生成策略。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-1yprrvfip8/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1391, \"height\": 287, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1yprrvfip8/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 580, \"height\": 460, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-1yprrvfip8/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 872, \"height\": 150, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1yprrvfip8/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1452, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1yprrvfip8/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1446, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1yprrvfip8/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1444, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1yprrvfip8/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 895, \"height\": 184, \"label\": \"Table\"}]"
motivation: 对齐通常需要大量精心策展的数据，成本高且易受噪声影响。
method: 将对齐建模为Stackelberg博弈，结合自标注迭代优化偏好数据。
result: 理论保证鲁棒性，实验表明仅需少量种子偏好即可高效对齐。
conclusion: SGPO/SSAPO是一种鲁棒的数据高效对齐方法，潜在可用于安全数据策展。
---

## Abstract
Aligning large language models (LLMs) with human preferences typically demands vast amounts of meticulously curated data, which is both expensive and prone to labeling noise. We propose Stackelberg Game Preference Optimization (SGPO), a robust alignment framework that models alignment as a two-player Stackelberg game between a policy (leader) and a worst-case preference distribution (follower). The proposed SGPO guarantees $\mathcal{O}(\epsilon)$-bounded regret within an $\epsilon$-Wasserstein ball, offering formal robustness to (self-)annotation noise. We instantiate SGPO with Stackelberg Self-Annotated Preference Optimization (SSAPO), which uses minimal human-labeled “seed” preferences and iteratively self-annotates new prompts. In each iteration, SSAPO applies a distributionally robust reweighting of synthetic annotations, ensuring that noisy or biased self-labels do not derail training. Remarkably, using only 2K seed preferences—about 1/30 of standard human labels—SSAPO achieves strong win rates against GPT-4 across multiple benchmarks within three iterations. These results highlight that a principled Stackelberg formulation yields data-efficient alignment for LLMs, significantly reducing reliance on costly human annotations.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：使大语言模型（LLM）输出与人类偏好对齐（alignment）通常需要大量精心策展的偏好数据，数据收集成本高昂且易引入标注噪声/偏差。如何在不依赖海量、含噪声的人类标注数据的前提下，实现鲁棒且数据高效的对齐？
- **整体含义**：论文提出一种基于 **Stackelberg 博弈** 的对齐框架，将偏好优化建模为策略（领导者）与最坏情况偏好分布（追随者）之间的博弈，并实例化为 **SSAPO**（Stackelberg Self-Annotated Preference Optimization）算法。SSAPO 利用极少量人工种子偏好（约标准量的 1/30）迭代地自标注新提示，同时通过分布鲁棒重加权控制合成标签的噪声，最终在多个基准上达到与使用大量人类标签的方法相当甚至更优的性能，显著降低了对昂贵人工标注的依赖。

## 2. 论文提出的方法论

- **核心思想**：将对齐视为一个两阶段 Stackelberg 博弈：
  - **领导者（Leader）**：策略 πθ，优化最坏情况下的偏好似然。
  - **追随者（Follower）**：一个对抗性的偏好分布 α，在 **ϵ-Wasserstein 球** 内选择分布，最小化领导者的目标。
  - 领导者目标：\( \max_{\pi} \min_{\alpha \in U_\epsilon((\Delta R_\pi)_\#\hat{P})} \mathbb{E}_{\xi\sim\alpha}[\log\sigma(\xi)] \)，其中 ξ 是奖励差距。
- **关键技术细节**：
  1. **SGPO 理论**：证明存在 Stackelberg 均衡，且领导者策略的后悔（regret）在 ϵ 扰动下有 \( \mathcal{O}(\epsilon) \) 上界，而标准 DPO 的后悔随分布偏移线性增长。
  2. **SSAPO 算法流程**：
     - **初始化**：使用少量人工标注的种子偏好（2K）训练初始 DPO 策略。
     - **迭代（T=3）**：
       1. **自标注**：从当前策略采样新提示的响应，并利用隐含奖励排序生成偏好对。
       2. **构建经验中心**：计算所有偏好对的奖励差距分布 \( \hat{\alpha}(\pi_t) \)。
       3. **追随者更新**：求解一个有限凸规划（基于 ℓ(ξ)=−logσ(ξ) 的逐段线性下逼近），获得最坏情况分布 α*ₜ（离散支撑）。
       4. **领导者更新**：最小化按 α*ₜ 重加权的逐对损失（等同于带权重的 DPO 损失），更新策略。
  3. **可扩展性**：针对大规模数据，采用均匀分组（grouping）策略，将数据分成多个子集并行求解 DRO 子问题，然后平均结果。推荐组大小 G≈100～300。
- **公式与算法**（文字说明）：参考附录 Algorithm 1；主要涉及 1-Wasserstein 距离、Kantorovich–Rubinstein 对偶、有限凸规划（Theorem 3.3）、及交替最佳响应迭代（Theorem 2.3）。

## 3. 实验设计

- **数据集**：
  - **UltraFeedback**（60K 样本）：种子 2K（3.3%），其余分为三轮（8K、20K、30K）仅保留提示用于自标注。
  - **UltraChat**：用于监督微调初始模型。
- **基准（Benchmark）**：
  - **AlpacaEval 2.0**：长度控制（LC）胜率 vs GPT-4 胜率。
  - **MT-Bench**：多轮交互平均分（0-10）。
- **对比方法**：
  - DPO（仅种子）、Iter DPO（PairRM 或 LLM-as-judge）、SPA（Spread Preference Annotation）。
  - 还包括全量训练模型（如 Zephyr-7B-β、Mistral-Large 123B）。
- **模型**：Mistral-7B-v0.1（主要），LLaMA-3-8B（兼容性验证），均基于 SFT 版本。

## 4. 资源与算力

- **实验使用**：4× A800 GPU（附录 G.3）。
- **时间估算**：
  - 生成 10K 提示响应约 15 分钟。
  - 偏好判断约 30 分钟。
  - 求解最坏情况分布（DRO）约 40 分钟。
  - 每 10K 训练数据策略更新约 1 小时。
- **总迭代**：初始 DPO + 3 轮 SSAPO。

## 5. 实验数量与充分性

- **主要实验**：
  - **表 1**：Mistral 和 LLaMA 在 AlpacaEval 2.0 和 MT-Bench 上的整体性能对比（含多种基线）。
  - **表 2**：与 Zephyr、Mistral-Large 等更强参考的对比。
  - **表 3**：Wasserstein 半径 ϵ 的消融（0~0.1）。
  - **表 4**：切线数量 K（5~7）和分组大小 G（100~300）的影响。
  - **图 2**：迭代过程中的性能提升。
  - **表 5**：种子标签 25% 翻转噪声下的鲁棒性测试（Mistral 和 LLaMA）。
- **充分性评估**：
  - 消融覆盖关键超参数（ϵ, K, G）和噪声场景。
  - 对比方法设置公平（均使用相同 2K 种子）。
  - 但未报告多次运行的误差棒（因计算成本高），故统计显著性未量化；结论主要基于单次运行的趋势。

## 6. 论文的主要结论与发现

- SGPO/SSAPO 在仅用 2K 人工种子偏好的情况下，即可在 AlpacaEval 2.0 和 MT-Bench 上**超越或匹敌**依赖大量标签（乃至全部 60K）的基线方法。
- **数据效率**突出：Mistral-7B-SSAPO（2K 种子）在 LC Win Rate 上达到 24.44%，而标准 DPO 仅 9.03%；LLaMA-3-8B-SSAPO 达到 33.33%。
- **鲁棒性**：理论上的 \( \mathcal{O}(\epsilon) \) 后悔界被实验验证：适度 ϵ（如 0.01）最佳，过大则保守；25% 标签翻转下性能仅适度下降（Mistral）甚至提升（LLaMA，因正则化作用）。
- **迭代增益**：三轮自标注与 DRO 更新持续提升对齐效果。
- **分组与切线数**存在最优 trade-off（推荐 K=6，G=100~300）。

## 7. 优点

- **理论创新**：首次将偏好对齐严格建模为 Stackelberg 博弈，并在 1-Wasserstein 球框架下给出 \( \mathcal{O}(\epsilon) \) 后悔界，证明鲁棒性优于标准 DPO。
- **实用算法**：SSAPO 使用有限凸规划 + 分段线性逼近，使 DRO 可解且可扩展；结合分组策略实现并行化。
- **数据效率**：仅需极少量人工种子（3.3%），大幅降低标注成本，对低资源场景尤为重要。
- **实验设计全面**：包含参数消融、噪声测试、迭代动态分析，且结果与理论一致。
- **开源代码**：匿名仓库可复现，促进社区进一步研究。

## 8. 不足与局限

- **计算复杂度**：求解 DRO 子问题（即使分组）仍需额外时间，在大规模（N>10⁵）下可能瓶颈；文中未与纯粹基于梯度的方法做详尽时间比较。
- **理论假设限制**：紧致性、Lipschitz、强凹性等条件在实际中不易严格满足，定理保证为局部线性收敛。
- **鲁棒范围局限**：仅针对训练阶段偏好噪声与分布偏移，不覆盖推理时的对抗攻击（jailbreak）或安全机制。
- **种子选择影响**：虽使用 farthest point sampling 降低方差，但种子质量对最终性能仍有影响，论文未深入探索种子选择策略的自动化。
- **统计可靠性**：缺少多次运行的误差棒，单次结果可能存在随机性，尤其是 LLaMA 在噪声下反而提升的现象需更多验证。
- **模型规模扩展**：最大实验模型为 8B，在大模型（如 70B+）上的效果未知。
- **MT-Bench 增益相对较小**：Mistral-SSAPO 的 MT-Bench 分数（6.68）甚至略低于 DPO（6.81），说明通用能力提升有限，可能更聚焦于偏好对齐而非绝对能力。
- **与提示生成方法的集成**：论文未来工作提到可与 EVA 等结合，但尚未验证。

（完）
