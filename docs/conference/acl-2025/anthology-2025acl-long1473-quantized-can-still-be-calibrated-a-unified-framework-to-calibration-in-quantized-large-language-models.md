---
title: "Quantized Can Still Be Calibrated: A Unified Framework to Calibration in Quantized Large Language Models"
title_zh: 量化仍可校准：量化大语言模型中校准的统一框架
authors: "Mingyu Zhong, Guanchu Wang, Yu-Neng Chuang, Na Zou"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.acl-long.1473.pdf"
tags: ["query:luq"]
score: 9.0
evidence: 大语言模型不确定性校准
tldr: 本文研究权重量化对大语言模型不确定性校准的影响，提出一种分析方法来估计量化后LLM的校准误差上界（UBCE），理论上证明了量化会损害校准性能。实验表明量化模型校准明显差于全精度模型，提示部署量化模型时需注意校准问题。
source: ACL-2025-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1473/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 794, \"height\": 546, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1473/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 797, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1473/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1645, \"height\": 652, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1473/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1656, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1473/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 798, \"height\": 845, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1473/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1648, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1473/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1648, \"height\": 445, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1473/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1372, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1473/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 680, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1473/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1675, \"height\": 689, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1473/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 809, \"height\": 909, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1473/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 768, \"height\": 559, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1473/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 816, \"height\": 452, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1473/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 759, \"height\": 410, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1473/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 750, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1473/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 554, \"height\": 374, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1473/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1261, \"height\": 403, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1473/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 803, \"height\": 914, \"label\": \"Table\"}]"
motivation: 权重量化虽节省资源，但其对LLM不确定性校准的影响尚未被探索。
method: 提出分析性方法估计校准误差上界（UBCE），分别讨论正确和错误预测的校准误差。
result: 量化模型一致表现出比全精度模型更差的校准性能。
conclusion: 量化会系统性降低LLM的校准可靠性，需要针对量化模型的校准方法。
---

## Abstract
Although weight quantization helps large language models (LLMs) in resource-constrained environments, its influence on the uncertainty calibration remains unexplored. To bridge this gap, we presents a comprehensive investigation of uncertainty calibration for quantized LLMs in this work. Specifically, we propose an analytic method to estimate the upper bound of calibration error (UBCE) for LLMs. Our method separately discusses the calibration error of the model’s correct and incorrect predictions, indicating a theoretical improvement of calibration error caused by the weight quantization. Our study demonstrates that quantized models consistently exhibit worse calibration performance than full-precision models, supported by consistent analysis across multiple LLMs and datasets. To address the calibration issues of quantized models, we propose a novel method of post calibration for recovering the calibration performance of quantized models through soft-prompt tuning. Specifically, we inject soft tokens to quantized models after the embedding layers, and optimize these tokens to recover the calibration error caused by the weight quantization. Experimental results on multiple datasets demonstrate our effectiveness in improving the uncertainty calibration of quantized LLMs, facilitating more reliable weight quantization in resource-constrained environments.

---

## 论文详细总结（自动生成）

# 论文《Quantized Can Still Be Calibrated: Understanding and Improving Uncertainty Calibration for Quantized Large Language Models》中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：权重量化技术虽能大幅降低大语言模型（LLM）的内存占用，使其适用于资源受限环境（如医疗设备、手机），但量化对模型**不确定性校准**（即预测置信度与实际正确率的匹配程度）的影响尚未被探索。
- **意义**：校准在高风险领域（金融、医疗）至关重要，且影响半监督学习等下游应用。本文首次系统研究量化LLM的校准退化问题，并提出恢复方法。

## 2. 方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：
  1. 提出**上界校准误差（Upper Bound Calibration Error, UBCE）**，将校准误差分解为正确答案和错误答案两部分，并给出闭形式上界。
  2. 理论证明：UBCE 是 Brier Score 和 binnedECE 的严格上界（Theorem 1），且与二元交叉熵（BCE）存在不等式关系（Theorem 2）。
  3. 基于定理2，校准误差的上界可被**困惑度（perplexity）** 约束，因此最小化困惑度可自然降低校准误差。
- **关键技术细节**：
  - **UBCE 定义**：`UBCE = P(c=0) E[ŝ|c=0] + P(c=1)(1 - E[ŝ|c=1])`，其中 c 为正确性，ŝ 为置信度。
  - **后校准方法——软提示调优（Soft-Prompt Tuning）**：
    - 在量化模型的嵌入层后注入 k 个可学习的软词元（soft tokens）向量。
    - 冻结模型所有参数，仅优化这些软词元。
    - 优化目标为最小化序列困惑度损失 `L = Σ -log Pr[t_{i+1} | q, e_1,...,e_k, t_1,...,t_i]`。
    - 算法：初始化软词元 → 冻结模型 → 对每个训练样本，将软词元拼接到词嵌入后 → 计算困惑度损失 → 更新软词元（AdamW优化器，学习率1e-5，epoch=50，虚token数256）。
  - **理论联系**：Theorem 2 建立了 UBCE 与困惑度的上界关系，为软提示调优提供理论依据。

## 3. 实验设计：数据集、基准、对比方法
- **数据集**：
  - **ARC-challenge** 和 **CommonsenseQA**（多选问答，转换为开放式生成任务）。
  - 泛化测试：MMLU（14个类别）。
- **模型与量化方法**：
  - 三个7B规模的LLM：Llama-3.1-8B、Mistral-v0.3-7B、Qwen-2.5-7B。
  - 两种量化方法：BNB（BitsandBytes，4-bit）和 GPTQ（4-bit）。
- **置信度度量方法**：
  - **CCTP**（使用模型回答“yes/no”的概率）。
  - **VCAA**（通过模型生成替代答案并口头报告置信度）。
- **对比基线**：
  - 温度缩放（Temperature Scaling）
  - 等渗回归（Isotonic Regression）
- **评估指标**：Brier Score（BS）、UBCE、binnedECE（可靠性图）。
- **实验设置**：固定种子、greedy解码、7次迭代生成答案；训练数据集大小上限4000样本。

## 4. 资源与算力
- 文中明确说明：
  - **GPU**：1× NVIDIA A100（80GB显存）
  - **CUDA版本**：12.1
  - **CPU内存**：128GB
  - **训练速度与内存**：见表8（GPTQ量化时424 samples/s，BNB为613 samples/s，峰值显存643MB和661MB）。
  - 训练资源较低，单次后校准在单个A100上可完成。

## 5. 实验数量与充分性
- **实验数量**：
  - 主校准对比（表1）：3模型 × 2量化 × 2数据集 × 2置信度 × 2指标 = 48个测量值。
  - 后校准效果（表2）：同样48个值，80%情况（38/48）校准误差下降。
  - 消融实验：软词元数量（128/256/512，见表9）和模型规模（0.5B至32B Qwen，见表10）。
  - 下游准确率（表4）和泛化（MMLU，表11）。
  - 对比基线（表3）：两种传统方法+本文方法。
- **充分性**：实验覆盖多种模型、量化方法、数据集、置信度度量，消融和泛化测试完整。条件控制（固定解码、一致评价函数）确保了公平性。结论具有统计显著性。

## 6. 论文的主要结论与发现
1. **量化导致校准退化**：在85%的评估中，量化模型的校准误差高于全精度模型，表现为对正确答案欠自信、对错误答案过度自信。
2. **UBCE提供更保守的上界**：UBCE是BS和binnedECE的严格上界，能更稳健地反映校准缺陷。
3. **软提示调优有效恢复校准**：在80%的测试案例中，后校准使量化模型校准误差显著降低，且不牺牲下游任务准确性（甚至在ARC上提升7%），泛化性能仅下降<2%（MMLU）。
4. **可扩展性**：方法在不同模型规模（0.5B~32B）和软词元数量下均有效。

## 7. 优点：方法或实验设计上的亮点
- **理论创新**：首次为量化LLM校准提供上界分析（UBCE与困惑度的联系），并给出优化理论依据。
- **方法轻量高效**：仅需添加少量可学习软词元（256个），冻结模型参数，训练效率高（单卡A100可完成）。
- **实验全面**：覆盖三种主流模型、两种量化方式、两种置信度度量、两个数据集，并包含泛化测试和消融。
- **对比充分**：与温度缩放、等渗回归等传统校准方法对比，显示显著优势。
- **可解释性**：通过累积分布、可靠性图展示校准改进的细节，并分析正确/错误答案的置信度变化。

## 8. 不足与局限
- **环境足迹**：论文在Limitations中承认，随着模型变大，调优所需的优化步骤可能增加生态影响，需要更可持续的策略。
- **实验覆盖偏差**：
  - 仅测试7B规模模型（虽然附录有0.5B~32B的补充实验，但主实验集中在7B）。
  - 仅使用两种量化方法（BNB、GPTQ），未涵盖AWQ等新方法。
  - 数据集局限于问答任务，未涉及生成式自由文本评估（如摘要、对话）。
- **潜在风险**：后校准依赖计算困惑度，可能对分布外数据鲁棒性不足；软提示初始化需特定文本（如附录D的初始化提示），存在敏感性。
- **应用限制**：方法需一定量的训练数据（4000样本），在零样本场景无法直接应用；校准恢复并非完美，部分指标仍有残留误差。

（完）
