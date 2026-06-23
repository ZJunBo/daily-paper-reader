---
title: Knowledge-Centric Data Selection for Effective Domain Adaptation of Language Models
title_zh: 面向语言模型高效领域自适应的知识中心数据选择
authors: "tianfeng zhao, ZICHENG ZHAO, XinyangGuo, Xingwu Liu, Xiang Cheng, Shaofang Nie, Shuai Cheng Li, Ming Li"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=7ZRF2ZkJpt"
tags: ["query:smd"]
score: 6.0
evidence: 基于熵的数据选择框架用于高效微调
tldr: 本文提出基于熵的数据过滤框架，定量评估样本的信息量和覆盖度，从而系统选择高质量数据。该方法提升了监督微调的效率，并增强了检索增强生成中的检索质量。这为安全对齐数据选择提供了可迁移的信息论准则。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-7zrf2zkjpt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1453, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-7zrf2zkjpt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1429, \"height\": 625, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-7zrf2zkjpt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1420, \"height\": 689, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-7zrf2zkjpt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1432, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-7zrf2zkjpt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1298, \"height\": 416, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-7zrf2zkjpt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1214, \"height\": 468, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-7zrf2zkjpt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1209, \"height\": 751, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-7zrf2zkjpt/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1252, \"height\": 743, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-7zrf2zkjpt/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1437, \"height\": 187, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-7zrf2zkjpt/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1434, \"height\": 188, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-7zrf2zkjpt/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1264, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-7zrf2zkjpt/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1451, \"height\": 2024, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-7zrf2zkjpt/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 743, \"height\": 389, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-7zrf2zkjpt/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1434, \"height\": 464, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-7zrf2zkjpt/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 707, \"height\": 467, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-7zrf2zkjpt/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 721, \"height\": 466, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-7zrf2zkjpt/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1437, \"height\": 1109, \"label\": \"Table\"}]"
motivation: 大规模训练语料存在噪声和重复样本，缺乏原则性的数据筛选标准。
method: 提出基于熵的过滤框架，通过信息量和覆盖度定量评估样本价值。
result: 方法提升了监督微调的效率以及检索增强生成中的检索质量。
conclusion: 该框架提供了一种原则性的数据选择准则，可推广到安全数据选择等场景。
---

## Abstract
Data filtering remains a fundamental challenge in training large language models (LLMs). Large-scale corpora often contain noisy or redundant samples that undermine training efficiency and limit model performance. Existing approaches typically rely on manual curation or heuristic model-based filtering, yet lack a principled and widely accepted quantitative criterion for deciding which data should be retained. To address this gap, we propose an entropy-based data filtering framework that quantitatively evaluates the informativeness and coverage of individual samples. Our method enables the systematic selection of high-value data, improving the efficiency of supervised fine-tuning (SFT) while also enhancing retrieval quality in retrieval-augmented generation (RAG). These results highlight the effectiveness of entropy-driven filtering as a general strategy for improving both adaptation and retrieval in large-scale LLM pipelines.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

**研究动机**：大规模语言模型（LLM）的领域自适应（Domain Adaptation）高度依赖高质量数据，而非数据量。现有数据选择方法（启发式过滤、困惑度剪枝、基于嵌入的聚类等）操作在 token 或 embedding 层面，无法识别领域特定的知识冗余（例如重复的定义、逻辑等价的证明、临床相同的指南），导致模型过拟合常见语言模式而忽略核心知识，训练效率低、资源成本高，且在高风险领域（如医学、法律）会带来严重风险。

**核心问题**：缺乏一种能够以离散、可审计的知识单元（而非连续嵌入或 token）为基础，进行知识覆盖度的原则性量化与优化选择的方法。

**整体含义**：本文提出一种以知识为中心的数据选择范式，通过知识覆盖熵（KCE）和熵驱动选择算法（EDS），直接优化知识覆盖的多样性与新颖性，从而同时提升监督微调（SFT）的学习信号和检索增强生成（RAG）的检索质量。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- 将数据质量重新定义为围绕离散知识单元（如数学定理、临床指南、法律原则）的覆盖，而非 token 或嵌入表面的统计。
- 构建“样本-知识”二元覆盖矩阵，通过最大化知识覆盖熵来选择子集，确保多样性并减少冗余。

### 关键技术细节

1. **二元信息-知识矩阵 (Binary Information-Knowledge Matrix)**：
   - 构造领域知识集 \(K\)（m 个知识点），每个样本映射为二元向量 \(B \in \{0,1\}^{n\times m}\)，\(B_{i,j}=1\) 表示样本 \(i\) 覆盖知识点 \(j\)。
   - 使用 LLM（Qwen-max-0125）从样本中提取知识标签，仅保留出现次数 ≥ 50 的知识点。

2. **知识覆盖熵 (KCE)**：
   - 对于子集 \(S\)（大小 \(h\)），定义知识点 \(j\) 的平均覆盖概率 \(p_j = \frac{1}{h}\sum_{a\in S} B_{a,j}\)。
   - KCE: \(H(S) = -\sum_{j=1}^m p_j \log_2 p_j\)，归一化后为 \(H_n(S) = H(S)/h\)。
   - 可扩展至无限维知识空间，采用蒙特卡洛采样近似。

3. **熵驱动选择算法 (EDS)**：
   - 优化目标：\(S^* = \arg\max_{|S|=s} H(S)\)，为组合优化问题。
   - 利用 KCE 的次模（submodular）性质，采用 lazy-greedy 算法（Algorithm 1）实现 \((1-1/e)\) 近似保证。
   - 定义凹覆盖目标：\(F(S) = \sum_{j} w_j f(c_j(S))\)，其中 \(c_j(S)=\sum_{a\in S}B_{a,j}\)，\(f\) 为凹非减函数。
   - 也可使用单遍近似评分：\(\text{Score}(a)=H(a)\cdot(1+\gamma\sum_i k_i B_{a,i})\)，实现线性时间复杂度。

4. **加权熵评分**：引入知识重要性权重 \(k \in \mathbb{R}^m\)（如根据概念频率），在多样性基础上优先选择高优先级概念。

## 3. 实验设计

### 实验场景与数据集

| 场景 | 数据集/基准 | 对比方法 |
|------|-------------|----------|
| 监督微调 (SFT) | S1 data-ablation-full59K 池，MATH-500 评估集 | QuRating, SuperFiltering, Structure Entropy, 随机采样, 人工精选 S1 1K 子集 |
| 检索增强生成 (RAG) | 自行构建的糖尿病语料（12K）、通用医学语料（20K）；生成 1000 个 LLM 提问 | 同上，另外包括未选择的全语料 |

### 评估指标
- **SFT**：MATH-500 精确答案准确率。
- **RAG**：平均 Hit@k（知识覆盖比例）、平均多知识点 MRR（要求集合完整覆盖）、传统 MRR。

### 实验变量
- SFT：不同数据预算（1K、5K、10K 等），全参数微调 vs. LoRA 微调。
- RAG：固定语料大小（糖尿病3K，医学8K）下变 top-k（5/10/20/50）；变语料大小（1%/5%/10%/20%/50%）。
- 消融实验：知识矩阵构建参数（频率阈值 k=10~50）、加权 vs. 无加权、不同知识提取源（Qwen-Max vs. Qwen-7B-Instruct vs. 医学生改正）。

### 实验公平性
- 所有条件除选择准则外其他设置完全相同（预处理、提示、训练超参数、Early Stopping 标准）。
- RAG 使用相同嵌入模型（BAAI/bge-large-zh/en）、相同检索方式（余弦相似度）。

## 4. 资源与算力

- 论文未明确说明训练所用 GPU 型号、数量及总训练时长。
- 提及的全参数微调使用 Qwen-32B-Instruct，LoRA 微调使用多种小模型（DeepSeek-Distill-Qwen-7B、Qwen3-8B 等）。DeepSpeed ZeRO Stage 3 用于显存优化。
- 推断使用 VLLM 框架，温度固定为 0。
- 知识提取使用 Qwen-max-0125（通过 API 调用），未报告 API 调用量。

## 5. 实验数量与充分性

**实验数量**：
- SFT 主实验：28 个熵选择子集 + 28 个随机子集（大小从 100 到 50000），共训练 56 个模型（全微调）；同样的子集在 LoRA 下对 4 种基线（Structure Entropy、QuRating、SuperFiltering、无加权 KCE）对比，每个大小至少 1 个模型。
- RAG 实验：两个领域、4 种选择方法、多个 top-k（5/10/20/50）、多个语料比例（5 种），加上 Revenue Boundary 分析，总计约 80 组以上实验。
- 消融实验：GSM8K 数据集上 3 种模型 × 6 种 k 阈值 × 2 种加权状态 = 36 组；MedQA 上 3 种知识提取源 × 5 个伪测试集 = 15 组。
- 参数敏感分析：α 和 γ 在 2 种样本大小下遍历。

**充分性与客观性**：
- 实验覆盖维度全面（SFT + RAG + 消融 + 参数敏感 + 模拟验证），并在不同模型规模、不同领域上验证。
- 每次对比均保持 matched-size，除选择准则外一致。
- 随机选取 28 个子集并取平均，减少随机波动；使用固定温度消除推理差异。
- 消融实验验证了方法对 k 阈值、加权、提取源不敏感，支持鲁棒性。
- 弱点：SFT 评估仅使用 MATH-500 一个基准，可能无法完全反映通用数学推理能力；RAG 使用自行构建语料，领域有限（仅糖尿病和通用医学）。

## 6. 主要结论与发现

1. **SFT 性能**：KCE/EDS 选择的子集在 MATH-500 上在所有数据预算下均优于随机采样和所有基线方法。仅用 500 样本即达到 456/500，超过人工精选 S1 的 452/500（1000 样本）。在 LoRA 微调下，加权 KCE 进一步优于无加权版本。
2. **RAG 性能**：KCE 选择的小语料（糖尿病3K，医学8K）在平均 Hit@k 和 MRR 上均超越随机和全部基线，同时大幅减少数据量。例如糖尿病数据集上 MRR 提升约 11%-42%。
3. **训练效率**：熵选择的数据集收敛更快、训练损失更低且更稳定。
4. **Revenue Boundary**：KCE 选择在低样本量下信息增益高，随后快速进入收益瓶颈，提供自然停止准则。

## 7. 优点

- **方法论创新**：首次将数据选择提升到知识单元层面，而非 token/embedding 层面，有效识别语义等价冗余。
- **理论扎实**：KCE 具有次模性质，EDS 采用 lazy-greedy 算法有 \((1-1/e)\) 近似保证；Information Gain 衰减有理论推导。
- **通用性强**：同时适用于 SFT 和 RAG 两种范式，在数学和医学领域均有验证。
- **高效实用**：单遍近似版本线性复杂度，适合大规模数据；加权版可融入领域先验。
- **实验设计严谨**：随机抽样 28 次取均值、matched-size 对比、消融全面、参数敏感分析稳健。

## 8. 不足与局限

- **假设依赖**：方法假设语料具有一定冗余性和知识重叠，在高度稀疏或极短样本（如仅含单个知识单元）时失效（知识矩阵接近对角）。
- **二元覆盖局限**：当前仅使用二元覆盖指示，忽略部分或分级覆盖，未来可引入概率或加权表示。
- **评估基准有限**：SFT 仅在 MATH-500 上评估，缺乏其他数学/推理任务验证；RAG 仅使用两个自行构建的医学语料，领域偏窄。
- **知识提取依赖 LLM**：知识提取使用专有模型（Qwen-max），引入 API 成本和潜在偏差；虽通过消融显示鲁棒，但未在多种商业模型上验证。
- **计算开销**：构建知识矩阵需要预先用 LLM 处理所有样本，对超大规模数据集可能仍是瓶颈（但论文给出了单遍近似缓解）。
- **未说明训练算力**：缺少 GPU 型号、数量、训练时长等细节，可复现性受影响。
- **数据分布假设**：在 SFT 训练中使用相同数据选择准则可能忽略数据的时间/难度分布等动态特性，但论文未讨论。

（完）
