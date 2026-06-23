---
title: Reconsidering LLM Uncertainty Estimation Methods in the Wild
title_zh: 重新考虑野外大语言模型不确定性估计方法
authors: "Yavuz Faruk Bakman, Duygu Nur Yaldiz, Sungmin Kang, Tuo Zhang, Baturalp Buyukates, Salman Avestimehr, Sai Praneeth Karimireddy"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.acl-long.1429.pdf"
tags: ["query:luq"]
score: 8.0
evidence: LLM不确定性估计方法在实际部署中的挑战
tldr: LLM不确定性估计方法多在短问答中评估，实际部署面临阈值选择敏感、对查询变换（错字、对抗提示）鲁棒性、长文本生成以及多输出策略等挑战。本文系统评估了这些方面，揭示了现有方法的不足，并给出了实用性建议。
source: ACL-2025-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1429/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1650, \"height\": 587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1429/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1647, \"height\": 1071, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1429/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1658, \"height\": 1054, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1429/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1600, \"height\": 1046, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1429/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1660, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1429/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1652, \"height\": 1638, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1429/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1638, \"height\": 1066, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1429/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 824, \"height\": 740, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1429/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 730, \"height\": 803, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1429/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 795, \"height\": 741, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1429/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 805, \"height\": 865, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1429/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1684, \"height\": 1395, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1429/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1674, \"height\": 2175, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1429/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1391, \"height\": 521, \"label\": \"Table\"}]"
motivation: 现有UE评估脱离实际部署场景。
method: 系统考察阈值敏感性、查询变换鲁棒性等四个方面。
result: 多数现有方法在实际场景中性能下降显著。
conclusion: 实际部署需要更鲁棒的不确定性估计方法。
---

## Abstract
Large Language Model (LLM) Uncertainty Estimation (UE) methods have become a crucial tool for detecting hallucinations in recent years. While numerous UE methods have been proposed, most existing studies evaluate them in isolated short-form QA settings using threshold-independent metrics such as AUROC or PRR. However, real-world deployment of UE methods introduces several challenges. In this work, we systematically examine four key aspects of deploying UE methods in practical settings. Specifically, we assess (1) the sensitivity of UE methods to decision threshold selection, (2) their robustness to query transformations such as typos, adversarial prompts, and prior chat history, (3) their applicability to long-form generation, and (4) strategies for handling multiple UE scores for a single query. Our evaluations on 19 UE methods reveal that most of them are highly sensitive to threshold selection when there is a distribution shift in the calibration dataset. While these methods generally exhibit robustness against previous chat history and typos, they are significantly vulnerable to adversarial prompts. Additionally, while existing UE methods can be adapted for long-form generation through various strategies, there remains considerable room for improvement. Lastly, ensembling multiple UE scores at test time provides a notable performance boost, which highlights its potential as a practical improvement strategy. Code is available at: https://github.com/duygunuryldz/uncertainty_in_the_wild.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
大语言模型（LLM）不确定性估计（UE）方法被广泛用于检测幻觉。然而，现有研究多在隔离的短问答（short-form QA）场景中评估，使用与阈值无关的指标（如AUROC、PRR）。实际部署面临多重挑战：决策阈值敏感性、对输入变换（错字、对抗提示、历史对话）的鲁棒性、长文本生成的适用性、以及如何整合多个UE得分。本文首次系统性地从这四方面考察了19种UE方法在实际“野外”场景中的表现，揭示了现有方法的显著不足，并提出了实用改进方向。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **整体框架**：将UE方法定义为从查询x和生成回答ŷ到不确定度分数的函数。评估核心指标采用预测拒绝比（PRR），因其对不同数据分布具有鲁棒性。
- **四方面研究内容**：
  - **决策阈值敏感性**：提出平均召回误差（ARE）指标，衡量在标定数据与测试数据存在分布偏移时，阈值设置对实际召回率的影响。分别考察了同域、同任务、跨域三种偏移。
  - **输入变换鲁棒性**：考察三种变换：添加历史对话（相似/不相似上下文）、引入错字（1个或2个随机字符变动）、插入对抗提示（信心增强提示，诱导模型过度自信）。
  - **长文本生成适应性**：提出三种策略将短问答UE方法适配到长文本索赔级评估：朴素应用（直接用原始查询+索赔）、问题生成（QG，为索赔生成专属问题再评估）、问答生成（QAG，生成问题并用模型新回答替代原索赔）。支持多次提问后聚合（平均、最小、最大）。
  - **多UE得分融合**：使用标定集将不同UE方法得分归一化（标准化、等渗回归），然后采用多种集成策略（最小/最大/平均/加权平均/投票/线性模型/决策树）评估性能提升。

## 3. 实验设计
- **数据集**：
  - 短问答：TriviaQA（闭卷QA）、NaturalQA（闭卷QA）、GSM8K（数学推理）。
  - 长文本：FactScore-Bio（传记问题）、LongFact-Objects（38个广泛主题）。
- **模型**：Llama-3-8B、GPT-4o-mini。
- **评估指标**：PRR（主指标）、ARE（阈值敏感性指标）。正确性由GPT-4o-mini评估（短问答用ground truth对比，长文本采用SAFE方法结合Google搜索）。
- **对比方法**：涵盖4类共19种UE方法：概率型（LNS、MARS、Entropy、Semantic Entropy、SentSAR、SAR、LARS）、内部状态型（INSIDE、Attention Score、SAPLMA）、输出一致性型（Degree Matrix、Eccentricity、SumEigV、KLE、Self-Detection）、自检型（P(true)、Verbalized Confidence）。其中LARS和SAPLMA为监督方法，其余为无监督。
- **实验设置**：所有实验重复5次取平均；标定集500样本，测试集1000样本；长文本每数据集随机50个问题。

## 4. 资源与算力
论文在计算资源部分明确指出：
- 使用40 GB Nvidia A100 GPU进行所有实验；GPT API用于运行GPT-4o-mini实验。
- Llama-3-8B实验的总GPU小时数约为800小时。
未提及精确的GPU卡数或训练/推理的详细算力分解。

## 5. 实验数量与充分性
- **实验组数**：覆盖4大研究方向，每个方向下包含多组对比：
  - 阈值敏感性：2模型 × 2测试集 × 3个标定源 × 19方法 × 5次重复 = 众多组合。
  - 输入鲁棒性：2模型 × 2数据集 × 3种变换（含不同变体，如1/2个错字、相似/不相似上下文） × 19方法。
  - 长文本适应：2模型 × 2数据集 × 3种策略 × 多提问数（1/5）× 聚合方式（3种）× 19方法。
  - 多得分融合：2模型 × 2数据集 × 7种集成策略 × 3种预处理 × 多种方法组合（+无监督子集重复）。
- **充分性评价**：实验设计较为系统，覆盖了主要实际部署挑战；使用了不同分布的数据集和两个不同规模/类型的模型（白盒/黑盒、开源/闭源）。但仅测试了两个模型，且长文本实验仅50个问题/数据集，样本量较小。整体而言，实验充分但不完整，部分结论需更多模型和更大规模数据验证。

## 6. 论文的主要结论与发现
1. **阈值敏感性**：大多数UE方法对决策阈值高度敏感，尤其当标定数据与测试数据存在分布偏移时。仅有MARS、Semantic Entropy和Eccentricity在所有设置下保持低ARE（<0.10）。
2. **输入变换鲁棒性**：
   - 对历史对话和错字普遍鲁棒，甚至相似上下文可提升概率型方法（如GPT-4o-mini的GSM8K表现）。
   - 对抗提示（信心增强）显著降低大多数方法性能，尤其是概率型方法；输出一致性型方法相对更鲁棒。
3. **长文本适应性**：QG和QAG策略可有效适配短问答UE方法，QAG优于QG，朴素应用最差。多次提问并取平均能提升性能，但整体PRR远低于短问答场景，仍有较大改进空间。
4. **多得分融合**：即使仅用100样本标定集，简单集成（如标准化后平均）即可获得高达0.06的PRR提升，优于最佳单一方法。线性模型+标准化/校准表现最佳；决策树失效。

## 7. 优点
- **问题导向明确**：首次系统审视UE方法在实际部署中的四类关键挑战，填补了现有评估脱离实际场景的空白。
- **评估指标创新**：提出ARE指标，直接量化阈值在分布偏移下的稳定性，比单纯AUROC更具实际意义。
- **方法分类清晰**：将19种方法按原理分为4类，便于分析不同类型方法的弱点。
- **长文本适配策略**：提出了三种可复用的策略（Naive/QG/QAG），为短问答UE方法扩展到长文本场景提供了基线。
- **集成分析实用**：展示了简单归一化+平均/线性模型即可大幅提升性能，具有很强的实际指导意义。
- **实验结果透明**：公开代码，重复5次报告均值和标准差，增强了可靠性。

## 8. 不足与局限
- **模型覆盖有限**：仅测试Llama-3-8B和GPT-4o-mini，未覆盖更大模型（如Llama-3-70B、GPT-4）或其他架构（如Mistral、Claude），结论泛化性受限。
- **长文本评估规模小**：每数据集仅50个问题，且依赖GPT-4o-mini分解和标定，可能引入噪声。
- **对抗提示设计人工性强**：针对GPT-4o-mini的对抗提示通过迭代搜索得到，对其他模型可能不有效，未探讨通用对抗策略。
- **阈值选择场景简化**：标定集大小固定（500样本），未探索更小标定集或动态阈值策略。
- **集成方法缺乏新意**：仅使用简单传统集成（平均、加权、线性等），未尝试更先进的元学习或集成学习。
- **未考虑计算成本**：不同UE方法计算复杂度差异大（如采样方法需多次生成），但论文未分析时间/计算开销。
- **潜在偏差**：正确性评估（短问答和长文本）均依赖GPT-4o-mini，可能引入模型偏差；且仅用二元正确/错误标签，未考虑部分正确的情况。

（完）
