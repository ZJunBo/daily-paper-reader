---
title: Instruction Tuning for Secure Code Generation
title_zh: 面向安全代码生成的指令微调
authors: "Jingxuan He, Mark Vero, Gabriela Krasnopolska, Martin Vechev"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=MgTzMaYHvG"
tags: ["query:smd"]
score: 4.0
evidence: 使用策展的安全数据集进行安全中心微调，将安全数据集成到指令微调中
tldr: 该论文提出SafeCoder，通过自动化流水线收集高质量安全数据集，并将其集成到代码生成模型的指令微调中，以提升代码安全性。虽然针对代码安全，但其安全数据策展与混合的思想与用户需求部分吻合。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-mgtzmayhvg/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 846, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mgtzmayhvg/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 837, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mgtzmayhvg/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 587, \"height\": 477, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 857, \"height\": 590, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1765, \"height\": 570, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1770, \"height\": 570, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 830, \"height\": 513, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 767, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 976, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1506, \"height\": 1159, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 861, \"height\": 1009, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 827, \"height\": 622, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 837, \"height\": 1009, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 822, \"height\": 621, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 812, \"height\": 453, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 904, \"height\": 410, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 559, \"height\": 1403, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 560, \"height\": 1406, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 559, \"height\": 655, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 562, \"height\": 654, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 559, \"height\": 1405, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 557, \"height\": 654, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 533, \"height\": 1054, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 532, \"height\": 1055, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 527, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 530, \"height\": 500, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 526, \"height\": 1053, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mgtzmayhvg/table-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 526, \"height\": 501, \"label\": \"Table\"}]"
motivation: 现有指令微调忽略代码安全，导致生成不安全代码。
method: 构建自动化安全数据收集流水线，安全数据与普通指令数据混合微调。
result: SafeCoder生成的代码安全性显著提升。
conclusion: 安全数据集成微调可有效提高代码安全。
---

## Abstract
Modern language models (LMs) have gained widespread acceptance in everyday and professional contexts, particularly in programming. An essential procedure enabling this adoption is instruction tuning, which substantially enhances LMs' practical utility by training them to follow user instructions and human preferences. However, existing instruction tuning schemes overlook a crucial aspect: the security of generated code. As a result, even the state-of-the-art instruction-tuned LMs frequently produce unsafe code, posing significant security risks. In this work, we introduce SafeCoder to address this gap. SafeCoder performs security-centric fine-tuning using a diverse and high-quality dataset that we collected using an automated pipeline. We integrate the security fine-tuning with standard instruction tuning, to facilitate a joint optimization of both security and utility. Despite its simplicity, we show that SafeCoder is effective across a variety of popular LMs and datasets. It is able to drastically improve security (by about 30%), while preserving utility.

---

## 论文详细总结（自动生成）

# 论文总结：面向安全代码生成的指令微调（SafeCoder）

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：当前大型语言模型（LLM）普遍采用指令微调（instruction tuning）来提升其遵循指令和人类偏好的能力，尤其在编程任务中广泛应用。然而，现有的指令微调方案完全忽略了生成代码的安全性，导致即使是顶尖的指令微调模型也频繁生成不安全的代码（安全率仅约60%），带来严重的安全风险。
- **整体含义**：该工作旨在填补代码安全在指令微调中的空白，提出一种安全导向的微调方法，在不损害模型实用性的前提下显著提升生成代码的安全性。

## 2. 方法论：核心思想、关键技术细节、公式与算法流程
- **核心思想**：将安全微调与标准指令微调融合，通过联合优化同时提升安全性与实用性。
- **关键技术细节**：
  - **安全数据集构建**：采用两阶段自动化流水线从GitHub提交中提取高质量的安全/不安全代码对。第一步：轻量级启发式过滤（关键词匹配、文件变更量阈值等）；第二步：使用CodeQL静态分析验证提交是否真正修复了漏洞，将修复前代码视为不安全（`ovul`），修复后代码视为安全（`osec`）。最终获得465个高质量样本，覆盖23个CWE类别和6种编程语言，并与SVEN公开数据集合并形成1268个样本、25个CWE、6种语言。
  - **安全微调损失函数**：
    - 对安全输出 `osec` 使用**掩码负对数似然损失** `Lsec`，仅关注与安全相关的token（通过代码差异计算掩码 `msec`），鼓励生成安全代码。
    - 对不安全输出 `ovul` 使用**掩码不似然损失** `Lvul`，惩罚生成不安全token，提供负向学习信号。
  - **联合微调算法**（Algorithm 1）：将标准指令数据集 `Dstd` 与安全数据集 `Dsec` 合并，每次迭代随机选取一个样本，若来自 `Dstd` 则使用标准损失 `Lstd`，若来自 `Dsec` 则使用 `Lsec + Lvul`。通过简单联合优化实现安全与实用的平衡。
  - **数据不平衡处理**：对每个（CWE, 语言）类别进行过采样，保证每类至少k个样本（编码模型k=20，通用模型k=40），提升少数类的安全表现和训练稳定性。
- **公式**：详见论文 Eq.(1)-(4)，以及Algorithm 1的文字描述。

## 3. 实验设计：数据集、Benchmark、对比方法
- **数据集**：
  - **标准指令微调数据集**：编码模型使用Evol-Instruct的33K去污染样本；通用模型使用LMSYS-Chat-1M中筛选的18K高质量单轮对话。
  - **安全微调数据集**：自行收集465个样本（23 CWE, 6语言）+ He & Vechev (2023) 的公开数据集（9 CWE, 2语言），共1268个样本，25个CWE，6种语言。按90%/10%分割训练/验证。
  - **安全评估场景**：60个手工构建的测试场景（42个来自论文收集+18个来自He & Vechev），覆盖训练集中的所有CWE-语言组合。此外还对未见过的CWE进行泛化测试（15个场景）。
- **Benchmark**：
  - 功能性正确性：HumanEval (pass@1, pass@10)、MBPP (pass@1, pass@10)
  - 自然语言理解：MMLU、TruthfulQA（5-shot）
  - 代码安全：CodeQL静态分析，报告安全生成百分比（100个采样，温度0.4）
- **对比方法**：
  - 基线：预训练模型（无指令微调）、仅标准指令微调（w/o SafeCoder）
  - 与SVEN的对比（调整后适配指令微调设置，使用不同权重 `wKL` 生成trade-off曲线）
  - 消融实验：移除收集数据、移除损失掩码、移除不似然损失
  - 过采样参数k的敏感性实验

## 4. 资源与算力
- 论文明确说明：使用了 **3块H100 (80GB)** 和 **8块A100 (40GB)** 的NVIDIA GPU。
- 训练配置：学习率2e-5（CodeLlama-7B例外为1e-3），2 epoch（CodeLlama-7B为5 epoch），批大小1，梯度累积16步，Adam优化器，权重衰减1e-2，梯度裁剪1.0。LoRA（对7B模型）采用r=16, α=32, dropout=0.1。未报告具体训练时长。

## 5. 实验数量与充分性
- **实验数量**：涉及6个不同大小的LLM（StarCoder-1B/3B, CodeLlama-7B, Phi-2-2.7B, Llama2-7B, Mistral-7B），两个标准指令数据集，60个安全测试场景，多个功能性基准。包含主结果表（Table 1 & 2）、消融表（Table 3）、SVEN对比图（Figure 3）、过采样敏感性图（Figure 4）、未见CWE泛化表（Table 4）。此外附录中有逐个场景的详细安全结果（Table 9, 10）。
- **充分性评估**：实验覆盖了编码专用和通用两类模型，使用多种评估维度（安全性、功能性、NLP理解），且进行了消融、对比、泛化、超参数分析，较为充分。但所有实验均基于静态分析工具CodeQL，可能存在误报/漏报；泛化实验中未见CWE的安全提升不明显，说明方法缺乏跨CWE泛化能力。整体设计公平，但未与强化学习方法（RLHF）对比。

## 6. 主要结论与发现
- SafeCoder能够显著提升生成代码的安全性（平均约30%的提升），同时几乎不损害功能性（HumanEval、MBPP、MMLU、TruthfulQA指标仅微小波动或持平）。
- 消融实验表明：收集的高质量数据、掩码机制、不似然损失三者对安全提升均至关重要。
- 过采样策略有效提升了安全性能和训练稳定性。
- 与SVEN相比，SafeCoder不存在安全性与功能性之间的权衡（SVEN因KL散度损失导致二难取舍），实现了“安全免费”的改善。
- 对未见CWE的泛化能力有限，说明模型主要记住了训练集中出现的漏洞模式。

## 7. 优点
- **方法简洁有效**：联合优化思想简单而高效，训练开销小（安全数据集仅1268个样本）。
- **自动化数据采集流水线**：从海量GitHub提交中自动提取高质量安全数据，覆盖多CWE和语言，可扩展性强。
- **安全性提升显著且实用**：在6个模型、多个基准上取得一致的效果，且几乎不牺牲其他任务性能。
- **开源**：公开代码和数据集，便于复现和社区应用。
- **关注实际安全问题**：直接针对当前LLM代码生成中的严重安全漏洞，具有现实意义。

## 8. 不足与局限
- **泛化性不足**：对于训练中未出现的CWE，SafeCoder未能显著提升安全性，说明方法缺乏跨类别泛化能力。
- **暂不支持预训练模型和已微调模型**：目前仅适用于从预训练模型开始进行指令微调的场景，未涉及已有指令微调模型的后修复，也未考虑代码补全模型。
- **仅使用监督微调**：未探索与强化学习（RLHF）的结合，可能限制了进一步优化潜力。
- **评估依赖静态分析**：安全评估完全依赖CodeQL，可能存在误报/漏报，且未覆盖所有漏洞类型（如逻辑漏洞、设计缺陷等）。
- **数据规模有限**：最终安全数据集仅1268个样本，可能不足以覆盖所有主流漏洞模式或编程语言。
- **无形式化安全保证**：方法仅提高生成安全代码的概率，无法提供绝对的安全性保证。

（完）
