---
title: "Why Uncertainty Estimation Methods Fall Short in RAG: An Axiomatic Analysis"
title_zh: 为什么不确定性估计方法在RAG中不足：公理分析
authors: "Heydar Soudani, Evangelos Kanoulas, Faegheh Hasibi"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.findings-acl.852.pdf"
tags: ["query:luq"]
score: 7.0
evidence: RAG中不确定性估计的公理分析
tldr: 现有不确定性估计方法在检索增强生成（RAG）场景中不可靠。本文提出一个公理框架，定义了五个约束条件，揭示了当前方法在加入检索文档后无法满足这些约束。分析表明需要专门为RAG设计新方法。
source: ACL-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.852/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 767, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.852/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 757, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.852/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1614, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.852/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1636, \"height\": 707, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.852/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1632, \"height\": 1089, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.852/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1622, \"height\": 732, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.852/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 741, \"height\": 677, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.852/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 770, \"height\": 409, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.852/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 757, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.852/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 765, \"height\": 356, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.852/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1617, \"height\": 692, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.852/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1645, \"height\": 652, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.852/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1676, \"height\": 1337, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.852/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 764, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.852/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1677, \"height\": 1339, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.852/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1677, \"height\": 1336, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.852/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1620, \"height\": 689, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.852/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1685, \"height\": 1272, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.852/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1686, \"height\": 1273, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.852/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1686, \"height\": 1272, \"label\": \"Table\"}]"
motivation: 现有不确定估计在RAG中的效果未被充分检验。
method: 提出一个包含五个约束的公理框架来分析现有方法的缺陷。
result: 所有现有方法在RAG设置下至少违反一个约束。
conclusion: 需要为RAG场景专门设计不确定性估计方法。
---

## Abstract
Large Language Models (LLMs) are valued for their strong performance across various tasks, but they also produce inaccurate or misleading outputs. Uncertainty Estimation (UE) quantifies the model’s confidence and helps users assess response reliability. However, existing UE methods have not been thoroughly examined in scenarios like Retrieval-Augmented Generation (RAG), where the input prompt includes non-parametric knowledge. This paper shows that current UE methods cannot reliably estimate the correctness of LLM responses in the RAG setting. We propose an axiomatic framework to identify deficiencies in existing UE methods. Our framework introduces five constraints that an effective UE method should meet after incorporating retrieved documents into the LLM’s prompt. Experimental results reveal that no existing UE method fully satisfies all the axioms, explaining their suboptimal performance in RAG. We further introduce a simple yet effective calibration function based on our framework, which not only satisfies more axioms than baseline methods but also improves the correlation between uncertainty estimates and correctness.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLM）在多种任务中表现出色，但也会生成不准确或误导性输出。不确定性估计（UE）旨在量化模型置信度，帮助用户判断响应可靠性。然而，现有UE方法主要针对仅包含查询的输入场景，在检索增强生成（RAG）中，输入提示包含非参数知识（检索文档），UE方法是否仍能有效工作尚未被充分检验。
- **核心问题**：三个研究问题（RQ1）现有UE方法在RAG场景中表现如何？（RQ2）什么属性可以保证UE方法在同时利用参数和非参数知识时最优？（RQ3）能否基于公理框架推导出最优的UE方法？
- **整体含义**：论文通过理论分析（公理框架）和实验验证，指出现有UE方法在RAG中系统性失效，并提供了一个校准函数来弥补缺陷，从而提升UE与正确性的相关性。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

### 核心思想
- 采用**公理化思维**，定义一组形式化约束（公理），描述UE方法在加入检索上下文后应该表现出的理想行为。通过检查现有方法是否满足这些公理，揭示其缺陷，并基于公理设计校准函数来调整UE分数。

### 关键技术细节

#### 2.1 公理框架
- 定义四个基础函数（基于NLI）：
  - **蕴含** (c ⊨ (q, r))：上下文c推断出r是q的正确响应。
  - **矛盾** (c ⊥ (q, r))：上下文c否定r的正确性。
  - **独立** (c # (q, r))：上下文c与r的正确性无关。
  - **等义** (r1 ≡ r2)：两个响应含义相同。
- 基于两个假设：上下文c可信且不包含矛盾信息。
- 定义**五个公理**（只列出核心含义，省略公式）：
  1. **正一致**：若无RAG和有RAG响应相同，且上下文支持响应，则RAG不确定性应降低。
  2. **负一致**：若响应相同但上下文矛盾，则RAG不确定性应升高。
  3. **正向改变**：若响应从错误变为正确（上下文支持正确响应），则RAG不确定性应降低。
  4. **负向改变**：若响应从正确变为错误（上下文矛盾），则RAG不确定性应升高。
  5. **中性一致**：若响应相同且上下文不相关，则不确定性应基本不变。

#### 2.2 公理实例化
- **基于参考**：利用真实标签和精确匹配函数E(r1, r2)判断条件。
- **免参考**：使用NLI分类器判断蕴含/矛盾关系，结合等价函数。

#### 2.3 校准函数推导
- 定义校准系数：αax = k1·E(r1, r2) + k2·R(c,q,r1) + k3·R(c,q,r2)
- 校准后的UE：U_cal = (k4 - αax)·U(Mθ(c,q), r2)
- 其中R(.)是评估上下文与响应关系的函数，E(.)是等价函数。
- **三种实例化**模型：
  - **CTI**：基于上下文敏感令牌识别（KL散度对比）。
  - **NLI**：基于蕴含概率。
  - **MiniCheck**：基于事实检查微调模型。

## 3. 实验设计

### 数据集
- **Natural Questions (NQ-open)**：2,889个测试样本，随机采样3,000个测试集。
- **TriviaQA**：3,000个随机样本（来自开发集）。
- **PopQA**：3,000个随机样本（来自测试集）。
- 每个数据集创建300个验证样本用于校准系数搜索。

### 基准UE方法
- **白盒方法**：Predictive Entropy (PE), Semantic Entropy (SE), MARS (应用于PE和SE，记为PE+M, SE+M)
- **黑盒方法**：Degree Matrix (Deg), Eccentricity (ECC), Eigenvalues (EigV)

### LLM
- Llama2-chat 7B
- Mistral-7B

### 检索器
- BM25, Contriever, BM25+Reranker
- 人工相关文档 (Doc+)、人工无关文档 (Doc-)

### 评估指标
- **正确性**：Exact Match
- **不确定性评估**：AUROC
- **公理满足率**：计算样本在各公理下的不确定性变化方向是否符合预期。

### 对比设置
- 无RAG (No Doc) vs. 不同检索器RAG (Doc-, BM25, Contriever, Rerank, Doc+)

## 4. 资源与算力
- 硬件：单个 **Nvidia A100 GPU**（40GB显存）。
- 总耗时：约 **250 GPU小时**。
- 由于算力限制，所有结果基于单次运行（未报告多次重复取平均）。
- 论文明确说明使用了上述资源。

## 5. 实验数量与充分性

### 实验数量
- 覆盖 **3个数据集、2个LLM、7种UE方法、5种检索条件**（No Doc, Doc-, BM25, Contriever, Rerank, Doc+），相当于约3×2×7×5=210个评估组合。
- 针对每个方法，还报告了在不同检索器下的**平均不确定性值**（表1/5）和**公理满足率**（表2/6/7/9）。
- 校准实验：对4种代表方法（PE, SE, EigV, ECC）应用三种校准模型（CTI, NLI, MiniCheck），在多个检索器上进行，并报告AUROC和公理改善率（表4/10/11-13）。
- 消融：比较了参考基和免参考两种公理实例化，验证一致性。

### 充分性与客观性
- **充分**：实验覆盖了主流UE方法和检索器，验证了公理框架的普适性。
- **公平**：所有方法使用相同LLM、相同响应生成配置（温度=1，10个样本）。公理评估采用统计显著性检验（Wilcoxon检验，p<0.01）。
- **客观**：实验结果明确展示了现有UE方法在公理2、4、5上的系统性失败，且校准后AUROC提升一致。

## 6. 论文的主要结论与发现

- **发现1**：加入任何上下文（包括无关文档）都会导致UE值系统性降低，说明现有UE方法无法区分上下文相关性，存在偏差（表1/5）。
- **发现2**：所有现有UE方法**不能完全满足五个公理**，特别是公理2（负一致）和公理4（负向改变）几乎总是违反（表2/6/7）。公理5（中性一致）也仅在部分方法/数据集上满足（表3/8）。
- **发现3**：基于公理框架设计的校准函数（尤其是MiniCheck）显著提高了AUROC和公理满足率（表4/10），使RAG的AUROC接近甚至超过无RAG基线（图3/5/6）。
- **发现4**：公理不仅诊断缺陷，还能指导改进：校准后UE性能与公理满足率正相关。

## 7. 优点

- **理论创新**：首次为RAG下的UE提出公理框架，将不可解释的UE行为转化为可检验的约束，富有洞察力。
- **实践价值**：校准函数简单实用（仅需调整四个超参数），且为使用现有UE方法提供了适配RAG的方法。
- **实验全面**：涵盖多个数据集、LLM、检索器和UE方法，验证了结论的鲁棒性。
- **公理实例化**：同时提出参考基和免参考两种方式，增强了框架的适用性（免参考可用于无标签场景）。

## 8. 不足与局限

- **公理完整性**：论文承认公理集可能不完整，例如未覆盖两个响应都与上下文矛盾的情况，未来可能需要补充公理。
- **应用范围**：实验仅针对事实性短回答（QA），未涉及长文本生成、多模态RAG或对话系统，这些场景的适用性未知。
- **下游任务未验证**：未在Adaptive RAG、幻觉检测、推理监控等实际应用中评估校准方法的有效性。
- **计算资源约束**：所有实验为单次运行，缺乏多次重复的平均和方差，可能影响统计稳定性。
- **超参数搜索**：校准系数通过网格搜索获取，虽然在不同数据集上一致，但可能依赖特定验证集，泛化性需进一步检验。

（完）
