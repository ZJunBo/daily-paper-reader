---
title: "Selective Risk Certification for LLM Outputs via Information-Lift Statistics: PAC-Bayes, Robustness, and Skeleton Design"
title_zh: 基于信息提升统计的选择性风险认证：PAC-Bayes、鲁棒性与骨架设计
authors: "Sanjeda Akter, Ibne Farabi Shihab, Anuj Sharma"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=DOSVhHurmM"
tags: ["query:luq"]
score: 8.0
evidence: 提供具有形式化放弃保证的选择性风险认证
tldr: "本文提出基于信息提升证书的选择性风险认证方法，用于大语言模型输出的不确定性量化与形式化放弃保证。该方法利用次伽马PAC-Bayes界，即使在重尾分布下也有效。在八个数据集上，该方法以2%风险达到77.0%覆盖率，在关键场景中能阻止96%的严重错误，优于熵基方法。"
source: ICLR-2026-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-dosvhhurmm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1148, \"height\": 851, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-dosvhhurmm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 865, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-dosvhhurmm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-dosvhhurmm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1438, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-dosvhhurmm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1453, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-dosvhhurmm/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1005, \"height\": 604, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-dosvhhurmm/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1447, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-dosvhhurmm/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1001, \"height\": 750, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-dosvhhurmm/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1456, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-dosvhhurmm/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 997, \"height\": 748, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-dosvhhurmm/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1005, \"height\": 744, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-dosvhhurmm/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1005, \"height\": 747, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-dosvhhurmm/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1006, \"height\": 753, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-dosvhhurmm/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1446, \"height\": 484, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 213, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 999, \"height\": 402, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1432, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1456, \"height\": 308, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 983, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1442, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 851, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1444, \"height\": 300, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1040, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1436, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1440, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 955, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 922, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1033, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1384, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1044, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1066, \"height\": 422, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 843, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1094, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1014, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1250, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 665, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-dosvhhurmm/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1398, \"height\": 300, \"label\": \"Table\"}]"
motivation: 大语言模型常产生自信但错误的输出，需要可靠的不确定性量化与形式化放弃保证。
method: 提出信息提升证书，将模型概率与骨架基线比较，通过PAC-Bayes界累积证据。
result: "在八个数据集上以2%风险达到77.0%覆盖率，高保真场景中阻止96%严重错误。"
conclusion: 该方法为LLM输出提供形式化的不确定性证书，在风险控制上优于熵基方法。
---

## Abstract
Large language models often produce confident but incorrect outputs, creating a critical need for reliable uncertainty quantification with formal abstention guarantees. We introduce information-lift certificates that compare model probabilities to a skeleton baseline, accumulating evidence through sub-gamma PAC-Bayes bounds that remain valid under heavy-tailed distributions where standard concentration inequalities fail. On eight diverse datasets, our method achieves 77.0\% coverage at 2\% risk, outperforming recent baselines by 10.0 percentage points on average. In high-stakes scenarios, we block 96\% of critical errors compared to 18-31\% for entropy-based methods. While our frequency-based certification does not guarantee severity-weighted safety and depends on skeleton quality, performance degrades gracefully under distributional shifts, making the approach practical for real-world deployment.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）在输出时可能产生自信但错误的回答（如幻觉），在医疗、金融等高保真场景中可能导致严重危害。现有的不确定性量化方法（如熵、语义熵、共形预测）要么缺乏形式化保证，要么假设子指数尾部分布，而LLM的token分布往往呈现重尾特征（power-law tails），导致标准浓度不等式失效。
- **研究背景**：选择性分类（Chow, 1970）通过放弃（abstain）来控制风险，但现有方法无法为自回归文本生成提供顺序有效的、对重尾鲁棒的正式风险认证。
- **整体含义**：本文提出一种基于信息提升（information-lift）统计量的选择性风险认证框架，通过对比模型概率与骨架（skeleton）基线，利用次伽马PAC-Bayes界在重尾分布下保持有效性，实现带形式化保证的放弃机制，提升了LLM输出的可靠性。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 2.1 核心思想
- **信息提升统计量**：对于每个token y，定义提升 L = log P(y|x) - log S(y)，其中P是完整模型，S是骨架基线（如温度平滑先验、领域n-gram等）。大正提升表示模型贡献了非通用证据，小或负提升表示模型输出接近基线。
- **序列级信息预算**：对所有token的截断提升求和（或平均），得到序列级的“信息预算”，用于决定是否认证输出。

### 2.2 关键技术细节
- **截断提升**：L_B = min{max(L, 0), B}，确保统计量有界，便于浓度分析。
- **次伽马假设**：假定截断提升服从次伽马分布（sub-gamma），即矩母函数满足特定上界。该假设覆盖比子指数更重的尾部，通过Kolmogorov-Smirnov检验在85%的数据集-模型组合上成立，剩余15%通过参数膨胀保持有效性。
- **PAC-Bayes证书**：定理2.5给出基于后验分布ρ和先验π的界：E_{ρ}[Δ(S)] ≤ E_{ρ}[Δ̂(S)] + sqrt[2v(KL+log(1/δ))/n] + c(KL+log(1/δ))/n。该界可转化为固定骨架的逐点界。
- **顺序有效界**：定理2.9将证明扩展为顺序认证，允许早期停止，惩罚仅为log(log(t)/δ)，实际中很小。
- **鲁棒性分析**：定理2.6证明当骨架S与理想骨架S⋆的总变差距离≤η时，选择性风险线性增长R(S) ≤ R(S⋆) + Cη。
- **信息下界**：定理2.7基于Le Cam引理，给出当证据与正确性之间的互信息≤κ时，回答率的上界：Answer Rate ≤ √κ/(1-2h⋆)。
- **骨架设计**：提出变分骨架设计（VSD），通过优化KL(P||S) - λE[L_B]平衡保真度和可认证性。使用投影梯度下降，收敛到O(1/T)（凸且L光滑）。
- **校准与自动回退**：算法1在标定集上估计次伽马参数并设置阈值τ；若假设检验失败（p<0.05），则按因子1.0~2.0线性膨胀参数，维持保证。

## 3. 实验设计

### 3.1 数据集与场景
- **8个数据集**：NQ-Open（开放域QA）、HotpotQA（多跳推理）、TruthfulQA（真实性）、SciQA（科学QA）、MultiRC（阅读理解）、BioASQ（生物医学QA）、XSum（摘要）、HumanEval-lite（代码生成）。
- **高保真场景**：在BioASQ上构建100条关键错误样本（错误会导致患者伤害），用于评估关键错误阻断率。

### 3.2 Benchmark与对比方法
- **5类基线**：
  - 自适应共形预测（Adaptive CP）
  - 自验证（Self-Verification）
  - 语义熵（Semantic Entropy）
  - 自检查GPT（SelfCheckGPT）
  - 标定选择性分类（Calibrated Selective）
  - 熵（Entropy）、集成（Ensemble）、温度缩放（Temp. Scale）等。
- **模型家族**：GPT-4、LLaMA-2、Mistral。
- **统一标定协议**：所有方法使用相同的500样本标定集、70/15/15划分、2%目标风险。

### 3.3 实验充分性与公平性
- **覆盖性**：8数据集 × 3模型 × 10基线以上，含全表结果（Table 8）。
- **消融研究**：VSD参数λ、截断B、温度、骨架选择、对抗骨架、低资源校准、top-k API限制、运行时开销等。
- **统计显著性**：所有改进p<0.001（配对t检验，Bonferroni校正），效应量Cohen d>0.8。
- **公平性**：相同标定数据、相同验证协议、超参数网格搜索（附录L.2）。

## 4. 资源与算力

- 论文明确说明：实验在NVIDIA A100 GPU上进行，总计约200 GPU小时。
- 未说明具体GPU数量（可能为单卡或多卡），但提供总时长，合理。

## 5. 实验数量与充分性

- **主要实验**：8数据集 × 多个模型 × 全基线 → 至少上百组性能对比。
- **消融实验**：参数敏感度（λ, B, 温度）、校准规模（50/100/250/500）、top-k限制、骨架质量、对抗攻击、跨域转移、VSD收敛性、Runtime缩放等。
- **高保真验证**：100例关键医疗错误，手工标注（两专家，κ=0.89）。
- **充分性评价**：实验覆盖全面，对比合理，统计检验严格，消融深入。但未包含多模态或语音等任务，仍可后续扩展。

## 6. 论文的主要结论与发现

- **性能优势**：在2%风险下，VSD证书平均覆盖率达77.0%，超过最佳基线（标定选择性分类67.0%）10个百分点。
- **关键错误阻断**：在BioASQ高保真挑战集中，阻断96%的关键错误，而熵法仅18-31%。
- **理论保证**：次伽马PAC-Bayes界在重尾分布下保持有效；顺序界允许早期停止（节省~32% token）。
- **鲁棒性**：骨架质量退化和分布漂移下性能优雅降级（如强攻击仅增加10-15%风险）。
- **部署可行性**：运行时开销<20%（15-25ms），对概率暴露API兼容，top-k补偿有效。

## 7. 优点：方法或实验设计上的亮点

- **理论创新**：首次将顺序有效PAC-Bayes界应用于LLM输出的信息提升统计，处理重尾分布和顺序依赖。
- **严格保证**：提供有限样本下的选择性风险界，并在顺序场景中保持有效。
- **骨架设计**：VSD可自动优化骨架，且具有形式化收敛和鲁棒性保证。
- **实验设计与验证**：
  - 大规模多数据集多模型比较，消融全面。
  - 高保真挑战集人工标注，量化关键错误阻断。
  - 多种实际约束测试（top-k API、低标定数据、对抗骨架）。
- **部署友好**：运行时轻量，支持概率暴露API，并提供早期停止、top-k补偿等实用功能。

## 8. 不足与局限

- **频率而非严重性**：证书控制错误频率，而非错误严重性。一个事实错误和致命幻觉同等对待，在高保真场景需额外安全检测器。
- **骨架依赖性**：性能依赖骨架质量；尽管有鲁棒性定理，在极端敌对骨架下风险仍可能显著上升（10-15%）。
- **领域泛化**：实验限于8个数据集（QA、摘要、代码），未涵盖多模态、对话等更复杂场景。
- **重尾假设检验**：15%的模型-数据集组合未通过次伽马拟合，需手动参数膨胀；自动回退机制虽有效但增加保守性。
- **计算资源**：虽然运行时低，但标定过程和VSD优化仍需一定计算（200 GPU小时），可能对小团队有门槛。
- **偏差风险**：论文提及证书不解决模型固有偏差，放弃机制可能被恶意利用（如规避敏感话题），仅建议外部监控。
- **未讨论训练阶段集成**：论文明确放弃结合内部状态的方法（如Azaria & Mitchell），可能错过部分信号。

（完）
