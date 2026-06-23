---
title: "DENSE-RAG: Measuring and Improving Context Understanding for Consistent Retrieval-Augmented Generation"
title_zh: "DENSE-RAG: 测量并改进检索增强生成中的上下文理解一致性"
authors: "Hao Wang, Xujia Li, Lei Chen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=UeQ4aw25Sw"
tags: ["query:luq"]
score: 6.0
evidence: 基于度的熵量化RAG中上下文理解不确定性
tldr: 检索增强生成中，LLM可能误解检索内容导致幻觉。本文提出DENSE方法，构建语义等价上下文并引入基于度的熵来量化响应语义不确定性。实验显示DENSE能有效检测误解，且通过DENSE-RAG进一步提升生成一致性，为RAG可靠性提供新的不确定性视角。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-ueq4aw25sw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1437, \"height\": 704, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ueq4aw25sw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1289, \"height\": 679, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ueq4aw25sw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 714, \"height\": 501, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ueq4aw25sw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 709, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ueq4aw25sw/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1449, \"height\": 266, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ueq4aw25sw/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1164, \"height\": 617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ueq4aw25sw/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1454, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-ueq4aw25sw/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1451, \"height\": 412, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-ueq4aw25sw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1319, \"height\": 434, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ueq4aw25sw/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1029, \"height\": 481, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ueq4aw25sw/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1312, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ueq4aw25sw/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 686, \"height\": 169, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ueq4aw25sw/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 745, \"height\": 170, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ueq4aw25sw/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1207, \"height\": 190, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ueq4aw25sw/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1163, \"height\": 203, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ueq4aw25sw/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1319, \"height\": 711, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ueq4aw25sw/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1446, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ueq4aw25sw/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1441, \"height\": 85, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ueq4aw25sw/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1450, \"height\": 567, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ueq4aw25sw/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1446, \"height\": 634, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ueq4aw25sw/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1438, \"height\": 754, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ueq4aw25sw/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1445, \"height\": 705, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-iclr-2026-ueq4aw25sw/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1446, \"height\": 655, \"label\": \"Table\"}]"
motivation: LLM误解检索内容时仍生成自信但错误的答案，缺乏有效检测手段。
method: 构建语义等价上下文，计算基于度的熵来量化语义不确定性。
result: 在RAG任务上，DENSE有效识别误解，DENSE-RAG提升生成一致性。
conclusion: 语义不确定性是检测RAG中LLM误解的有效信号。
---

## Abstract
Retrieval-Augmented Generation (RAG) has significantly advanced LLM performance in knowledge-intensive tasks. 
However, when LLMs misinterpret retrieved content, they often revert to pre-trained parametric knowledge or generate hallucinated responses, undermining RAG effectiveness. 
In this work we try to explore this problem by proposing DEgree-based uNcertainty with Semantically Equivalent contexts (DENSE), a training-free and model-agnostic method to evaluate LLM understanding of retrieved documents. 
DENSE constructs semantically equivalent context and introduces a degree-based entropy to quantify response semantic uncertainty. 
Building on DENSE, we further introduce DENSE-RAG, which includes two training-free DENSE-guided modules: adaptive semantic chunking and iterative context refinement.
Experiments on open-book QA datasets show that higher DENSE uncertainty correlates with lower QA performance, validating DENSE as a reliable indicator of LLM understanding measurement. 
DENSE-RAG also achieves performance competitive with state-of-the-art baselines approaches without introducing additional model or fine-tuning.

---

## 论文详细总结（自动生成）

# 论文结构化中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：检索增强生成（RAG）中，大型语言模型（LLM）可能误解检索到的文档内容，转而依赖其预训练参数知识或产生幻觉，导致生成结果与上下文不一致，降低了 RAG 的可靠性。
- **背景**：现有工作多聚焦于改进检索器或微调生成器，但缺少一个通用的、无需训练的指标来衡量 LLM **对检索上下文的理解程度**。作者观察到：如果 LLM 真正理解了上下文，则对于语义等价的输入应产生语义等价的输出；若输出出现语义不一致，则表明理解存在缺陷。
- **意义**：提出一种无监督、模型无关的评估方法（DENSE），并能基于该评估进一步改善 RAG 质量，为诊断和提升 RAG 系统提供了新视角。

## 2. 方法论
### 2.1 核心思想
- **语义等价上下文**：利用 LLM 改写每个检索块（chunk），得到与原块语义等价但词句不同的版本，从而构建一组上下文（原始+每个块被替换一次），共 `k+1` 个。
- **度基语义熵（Degree‑based Semantic Entropy）**：在这些上下文中进行贪心解码（消除模型随机性），得到响应集合。利用 NLI 模型构建响应间的语义蕴含邻接矩阵，计算每个响应的度数（与其他响应一致的边数），进而计算熵值。熵越高说明响应语义分化越严重，表示 LLM 对上下文的解读不稳定、理解不足。
- **无需训练、模型无关**：可应用于任何黑盒 LLM。

### 2.2 关键技术细节
1. **改写与上下文构造**：对 `k` 个检索块分别改写，生成 `k` 个新块，逐块替换产生 `k` 个新上下文（每个 `C_i` 中只有第 `i` 块被替换，其余保持原样），加上原始上下文共 `k+1` 个。
2. **响应生成**：对所有上下文使用贪心解码得到响应 `r_0, r_1, ..., r_k`。
3. **语义邻接矩阵**：用 NLI 模型判断任意两个响应间的双向蕴含分数，取平均作为边权 `w_ij`。
4. **度基语义熵**：`DSE = - (1/(k+1)) Σ log(D_i / (k+1))`，其中 `D_i = Σ_j w_ij` 是响应 i 的度数。熵值范围 `[0, log(k+1)]`。
5. **DENSE‑RAG 两模块**：
   - **自适应语义分块**：当 DENSE 高于阈值 0.2（视为“不确定”）时，对文档按语义相似度合并句子为语义块，替代固定大小分块；否则保持固定分块，以平衡效率和性能。
   - **迭代上下文精炼**：利用 DENSE 结果定位不确定块，通过剔除该块的反应判断其必要性，将块分类为“确定”、“必要”、“不必要”；然后移除不必要块，补充与必要块最相似的新块，重复该过程直到 DENSE 低于阈值或自评足够。

## 3. 实验设计
### 3.1 数据集与场景
- 四个开卷问答数据集：TriviaQA、Natural Questions、AmbigNQ、2WikiQA（含单跳和多跳）。
- 额外在摘要任务（CNN/DailyMail）上进行初步验证（附录 I.2）。

### 3.2 Benchmark 与对比方法
- **不确定性基线**：语义熵（Discrete Semantic Entropy）、Ueigv、Udeg、Kernel Language Entropy（KLE）等，在采样模式下比较 AUROC/AURAC。
- **RAG 性能基线**：RePlug、ChatQA-1.5、Astute‑RAG、RankRAG、RAG‑DDR、Adaptive‑RAG、UncertaintyRAG、Collab‑RAG 等，涵盖微调/无微调、不同模型规模。

### 3.3 评估指标
- QA 任务：Exact Match (EM)。
- 不确定性排序：AUROC 和 AURAC。

### 3.4 骨干模型
- Qwen‑2.5 1.5B、Qwen‑3 8B、Llama‑3 8B、Llama‑3.1 8B、Llama‑3.1 70B。

### 3.5 检索设置
- 使用 UAE‑Large‑V1 编码器，FAISS 索引，固定检索 top‑5 块（主要实验）。

## 4. 资源与算力
- **GPU**：1.5B/8B 模型使用单张 NVIDIA 3090；70B 模型使用 2 张 NVIDIA A100 80GB。
- **时间开销**：DENSE 计算平均约 1 秒/查询（A100），完整 DENSE‑RAG 平均约 6 秒/查询。
- **未提及训练时长**：由于所有方法无需训练，无训练时间消耗。

## 5. 实验数量与充分性
- **实验覆盖**：
  - 主实验：4 个数据集 × 5 个 LLM → 20 组基础对比。
  - 不确定性对比：不同温度（greedy, 0.25, 0.5, 1.0, 3.0, 5.0, 7.0）下的 AUROC/AURAC 比较（表 1, 表 8）。
  - DENSE‑RAG 消融：自适应分块 + 迭代精炼的逐步添加（表 2）、分块策略分析（表 4）、精炼组件分析（表 5）。
  - 鲁棒性分析：不同 DENSE 阈值（图 5）、不同块数量（图 8）、不同语义合并阈值（图 7）。
  - 额外验证：摘要任务（表 10）、改写质量检查（表 6）、高温度行为分析。
  - 案例研究（附录 M）。
- **充分性**：实验设计较为全面，消融和对比维度丰富，涵盖了不同模型、不同数据集、不同配置，结果客观且公平（绝大多数基线使用相同检索设置；论文自述与部分基线因检索策略不同仅作参考对比）。

## 6. 主要结论与发现
- **DENSE 有效性**：DENSE 越高，QA 准确率越低（图 3、4），AUROC/AURAC 优于现有不确定性基线（表 1），表明其能可靠测量 LLM 对上下文的理解。
- **DENSE‑RAG 提升显著**：在不确定问题（DENSE > 0.2）上，自适应分块和迭代精炼均带来持续增益（表 2），整体性能接近甚至超越需要微调的 SOTA 方法（表 3），且无需任何训练。
- **模块设计合理性**：自适应分块根据不确定性动态选择分块策略，避免了全局使用语义分块对确定问题的损害；迭代精炼通过必要块定位和补充，有效减少无关信息、补充缺失信息。
- **通用性与鲁棒性**：方法在不同模型规模（1.5B~70B）、不同 NLI 骨干（LLM 或 DeBERTa）下均表现稳定。

## 7. 优点
- **无训练、模型无关**：可即插即用于任何黑盒 LLM，无需微调或访问模型内部。
- **可解释性强**：能将不确定性归因到具体检索块（确定/必要/不必要），便于定向改进。
- **设计精巧**：利用贪心解码排除模型随机性，聚焦于上下文理解差异；度基熵避免聚类步骤，直接计算节点度数，计算简洁且信息量保留。
- **实验充分、对比公平**：涵盖多种基线、多种设置，消融实验设计清晰，验证了各组件的必要性。
- **实际性能提升显著**：在不确定问题上提升 10~15% EM，达到与复杂微调方法竞争的水平。

## 8. 不足与局限
- **计算开销**：DENSE 需要 `O(k^2)` 次 LLM 调用（改写、生成、NLI），对于大 `k` 或实时场景可能代价较高（论文提到约 1~6 秒/查询，但未在极低延迟场景验证）。
- **对 NLI 质量敏感**：语义等价判断依赖 NLI 模型，对某些语义等价但表达差异大的句子可能无法正确处理（论文验证了 LLM 和 DeBERTa 的一致性，但未讨论极端情况）。
- **实验覆盖有限**：主要限于开卷 QA 任务；对更复杂场景如多步推理（2WikiQA 仅简单涉及）、长文本生成、对话 RAG 等未充分验证；摘要实验仅初步。
- **高温度失效**：当采样温度升高，LLM 不再忠实于检索上下文时，DENSE 不再有效（论文承认这不是其设计场景）。
- **阈值设定依赖经验**：阈值 0.2 基于数据集观察，不同应用可能需要调整，缺乏自适应方法选择阈值。
- **未与其他不确定性利用方法集成**：未探索将 DENSE 信号直接用于模型训练或决策层融合。
- **可能引入改写偏差**：虽然验证了 95%+ 语义保留，但少数改写可能轻微改变语义，引入噪声。

（完）
