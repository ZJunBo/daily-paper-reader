---
title: Confidence Estimation for Text-to-SQL in Large Language Models
title_zh: 大语言模型文本到SQL的置信度估计
authors: "Sepideh Entezari Maleki, Mohammadreza Pourreza, Davood Rafiei"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40523/44484"
tags: ["query:luq"]
score: 6.0
evidence: LLM文本到SQL的置信度估计方法
tldr: 文本到SQL任务中评估LLM生成SQL的可靠性具有挑战性。本文在LLM上下文中研究了黑盒与白盒置信度估计策略，发现基于一致性的方法在黑盒设置中表现最佳，而SQL语法感知的方法在白盒设置中更有优势。此外，执行结果作为补充信号能进一步提升效果，为LLM在SQL生成中的可靠性评估提供了实用指导。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 需要评估LLM生成SQL的可靠性而无真实答案。
method: 探索了基于一致性、logit解释和执行结果的黑盒与白盒置信度估计方法。
result: 一致性方法在黑盒中最佳；SQL语法感知方法在白盒中最佳；执行信号辅助提升效果。
conclusion: 为LLM在text-to-SQL中的不确定性估计提供了有效策略。
---

## Abstract
Confidence estimation for text-to-SQL aims to assess the reliability of model-generated SQL queries without having access to gold answers. We study this problem in the context of large language models (LLMs), where access to model weights and gradients is often constrained. We explore both black-box and white-box confidence estimation strategies, evaluating their effectiveness on cross-domain text-to-SQL benchmarks. Our evaluation highlights the superior performance of consistency-based methods among black-box models and the advantage of SQL-syntax-aware approaches for interpreting LLM logits in white-box settings. Furthermore, we show that execution-based grounding of queries provides a valuable supplementary signal, improving the effectiveness of both approaches.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究问题**：在文本到SQL（text-to-SQL）任务中，评估大型语言模型（LLM）生成的SQL查询的可靠性，而不依赖于真实答案（gold answers）。
- **背景与动机**：LLM在将自然语言转换为SQL方面表现出色，但在企业部署中仍面临准确性挑战。非技术用户无法验证生成SQL的正确性。因此需要可靠的置信度估计方法，帮助用户决定是否采用查询，或让模型在低置信时拒绝回答。
- **现有局限**：传统不确定性方法（如Monte Carlo dropout、深度集成）难以应用于闭源LLM；代码生成（尤其是text-to-SQL）中的不确定性研究较少；现有工作主要关注查询放弃（abstention）或校准，缺乏系统比较。
- **核心意义**：提供了首个针对text-to-SQL置信度估计的基准，比较黑盒与白盒方法，并引入语法感知方法提升校准性能。

## 2. 方法论：核心思想与技术细节
- **整体框架**：探索三类置信度估计策略：口头化（verbalized）、一致性（consistency-based）和基于logit的方法。
  - **口头化方法**：直接让LLM输出置信度分数（0-100），包括三种变体：
    - 普通口头化（Vanilla）：简单指令生成SQL+置信度。
    - 链式思维口头化（CoT）：加入推理示例（“Let's think step by step”）。
    - 增强链式思维口头化（Augmented CoT）：额外提供SQL执行结果的前1000行。
    - 自检置信度（Self-Check）：二分类判断（正确/错误）。
  - **一致性方法**：通过多次采样（高温度）生成多个SQL，然后基于一致性计算置信度。三种方式：
    - 基于执行结果的一致性：执行SQL并比较返回行，相同结果的比例作为置信度。
    - 基于嵌入的一致性：对SQL生成嵌入并聚类，聚类内比例。
    - 基于模式链接的一致性：提取模式链接（表名、列名、常量）并精确匹配聚类。
  - **基于Logit的方法**：利用token级概率聚合。
    - 全token置信度（FTC）：所有token概率等权重平均或乘积。
    - 模式链接置信度（SLC）：仅考虑模式相关token。
    - SQL语法感知置信度（SAC）：进一步过滤非关键token（如冗余括号、可选关键字），进行大小写折叠、顺序折叠、同义词折叠、等价表达式折叠。聚合方式包括乘积（Product）与平均（Average）。

- **关键公式/流程**：无具体数学公式，但描述了概率调整规则，如大小写不敏感时合并概率，等价表达式互换等。最终置信度为调整后token概率的乘积或平均。

## 3. 实验设计
- **数据集**：
  - Spider开发集（1034个示例，20个数据库）
  - BIRD开发集（1533个示例，11个数据库）
- **评估指标**：
  - AUC-ROC：区分正确与错误查询的能力（越高越好）
  - 预期校准误差（ECE）：置信度与准确率之间的平均差距（越低越好）
- **对比方法**：
  - 黑盒基线：口头化三种变体、自检、一致性三种变体（执行/嵌入/模式）
  - 白盒基线：全token置信度（FTC）、模式链接置信度（SLC）、SQL语法感知置信度（SAC），分别使用乘积和平均聚合
- **使用的LLM**：GPT-3.5-turbo、GPT-4o-mini（闭源）、DeepSeek 6.7B、Qwen2.5-Coder（开源）。
- **基准（Baseline）**：采用全token置信度乘积（FTC-Product）作为强基线（来自Ramachandran & Sarawagi, 2024）。

## 4. 资源与算力
- **论文中未明确说明使用的GPU型号、数量、训练时长等具体算力资源**。仅提到实验在多种LLM上进行，其中闭源模型通过API调用，开源模型可能在本地GPU运行，但未提供细节。

## 5. 实验数量与充分性
- **主要实验**：在Spider和BIRD两个标准数据集上，对4种LLM（GPT-3.5、DeepSeek、GPT-4o-mini、Qwen2.5）分别测试了所有方法（总计约10种方法 × 2数据集 × 4模型 ≈ 80组结果）。表格1展示了完整的AUC和ECE。
- **消融实验**：
  - 对SAC-Avg在BIRD上进行了特征消融（去除token排除、大小写折叠、顺序折叠、同义词折叠、等价表达式折叠），结果见表2。
  - 分析了查询难度、查询长度、模式链接数量对性能的影响（图2-4）。
  - 探讨了执行反馈的影响。
- **充分性评价**：实验设计全面，覆盖了多种模型、多种方法、多个维度（难度、长度、模式复杂度），并提供了统计学显著性检验（p<0.05）。实验客观、公平，采用标准化指标和公开数据集。

## 6. 主要结论与发现
- **白盒方法普遍优于黑盒方法**：基于logit的方法在AUC和ECE上均优于口头化和一致性方法。
- **SQL语法感知置信度（SAC）效果最佳**：尤其在BIRD复杂查询上，SAC-Average相比最佳黑盒基线AUC提升高达12%，ECE降低16%。
- **聚合方式的影响**：平均聚合对长查询更鲁棒，乘积聚合对短查询更有效。
- **黑盒中基于执行的一致性最强**：但计算开销大；口头化方法在复杂查询上校准差（ECE超50%）。
- **执行反馈增强所有方法**：尤其是SAC，在BIRD上AUC达79.06，ECE仅12.15。
- **SQL特定特征（如token排除、大小写折叠）对SAC性能贡献显著**（token排除导致AUC下降5.7%）。

## 7. 优点
- **首创性**：首次系统比较text-to-SQL中黑盒与白盒置信度估计方法，提供统一基准。
- **方法创新**：提出的SQL语法感知置信度（SAC）考虑SQL特有结构，通过过滤非关键token和折叠等价变体，显著提升校准效果。
- **广泛评估**：在两大标准数据集、四种不同规模（开源/闭源）的LLM上验证，确保泛化性。
- **分析深入**：从查询难度、长度、模式复杂度等多个角度分析性能变化，揭示方法适用场景。
- **可解释性**：SAC方法聚焦模式链接和关键语法，提供更可解释的置信度。

## 8. 不足与局限
- **算力信息缺失**：未提供具体硬件配置和运行时间，难以评估方法实用性。
- **实验覆盖局限**：仅使用两个数据集（Spider和BIRD），均为英文，未涵盖多语言或真实企业数据库。BIRD中的复杂查询比例高，但Spider相对简单，可能影响泛化结论。
- **黑盒方法成本高**：一致性方法需要多次采样和执行，延迟与成本未量化。
- **未见真实场景验证**：未在实际应用（如用户交互系统）中测试置信度阈值的效果。
- **白盒方法依赖logit访问**：部分闭源模型限制logit获取，实际部署可能受限。
- **未探讨混合方法**：仅分别比较单一方法，未尝试结合黑盒与白盒优势。

（完）
