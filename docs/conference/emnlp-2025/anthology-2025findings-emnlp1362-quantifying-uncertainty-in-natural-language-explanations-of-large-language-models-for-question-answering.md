---
title: Quantifying Uncertainty in Natural Language Explanations of Large Language Models for Question Answering
title_zh: 量化大型语言模型在问答任务中自然语言解释的不确定性
authors: "Yangyi Li, Mengdi Huai"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.findings-emnlp.1362.pdf"
tags: ["query:luq"]
score: 7.0
evidence: 用于自然语言解释的LLM不确定性量化
tldr: 该论文首次研究为大型语言模型在问答任务中生成的自然语言解释提供不确定性量化。现有方法能生成解释但无法保证其不确定性，该工作填补了这一空白，提出在解释层面进行不确定性估计，对于提升模型可靠性和可解释性具有重要意义。
source: EMNLP-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1362/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 789, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1362/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 785, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1362/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 682, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1362/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 674, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.1362/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 781, \"height\": 288, \"label\": \"Figure\"}]"
motivation: 现有LLM解释方法无法提供不确定性保证，限制模型在高风险场景下的可信度。
method: 提出了针对自然语言解释的不确定性量化框架，利用模型输出概率和一致性进行估计。
result: 在多个问答数据集上验证了该方法的有效性，能够准确区分可靠与不可靠的解释。
conclusion: 为LLM的可解释性提供了不确定性量化手段，增强了模型输出的可信度。
---

## Abstract
Large language models (LLMs) have shown strong capabilities, enabling concise, context-aware answers in question answering (QA) tasks. The lack of transparency in complex LLMs has inspired extensive research aimed at developing methods to explain large language behaviors. Among existing explanation methods, natural language explanations stand out due to their ability to explain LLMs in a self-explanatory manner and enable the understanding of model behaviors even when the models are closed-source. However, despite these promising advancements, there is no existing work studying how to provide valid uncertainty guarantees for these generated natural language explanations. Such uncertainty quantification is critical in understanding the confidence behind these explanations. Notably, generating valid uncertainty estimates for natural language explanations is particularly challenging due to the auto-regressive generation process of LLMs and the presence of noise in medical inquiries. To bridge this gap, in this work, we first propose a novel uncertainty estimation framework for these generated natural language explanations, which provides valid uncertainty guarantees in a post-hoc and model-agnostic manner. Additionally, we also design a novel robust uncertainty estimation method that maintains valid uncertainty guarantees even under noise. Extensive experiments on QA tasks demonstrate the desired performance of our methods.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）在问答任务中能生成自然语言解释，但现有研究缺乏对这些解释提供有效不确定性保证的方法。缺乏不确定性量化使得在高风险决策（如医疗问答）中难以信任解释的可靠性。
- **研究动机**：传统不确定性估计方法（如扰动法、贝叶斯法）要么无法提供有效保证，要么需要访问模型logits或重新训练；而共形预测虽能提供无分布假设的覆盖保证，但无法直接应用于LLM自回归生成的解释，且现实数据常含噪声（如语法歧义、拼写错误），破坏共形预测所需的交换性假设。
- **整体含义**：首次提出针对LLM自然语言解释的严格不确定性估计框架，填补了可解释性与可靠性之间的空白，为高风险场景下LLM部署提供置信度参考。

## 2. 论文提出的方法论

### 核心思想
- 采用**共形预测**框架，将自然语言解释视为问题词元的子集，通过构建“不确定性集合”（包含重要词元）并控制其中未包含真实解释词元的期望比例（风险水平α），提供统计保证。
- 方法分为两部分：**ULXQA**（基本有效方法）和**RULX**（鲁棒扩展，应对噪声）。

### 关键技术细节
- **重要性分数**：设计提示模板，让LLM为输入问题的每个词元输出一个重要性分数 \(S(P_i, q_{i,j}; M) \in [0,1]\)，反映该词元对预测答案的贡献程度。
- **不确定性集合构建**：对于问题 \(Q_i\)，定义集合 \(C_\lambda(Q_i; M) = \{q_{i,j} \mid S(P_i, q_{i,j}; M) \ge 1 - \lambda\}\)，其中λ是控制集合大小的参数。
- **损失函数**：定义损失 \(\ell(C_\lambda, E^*, \lambda) = 1 - |E^* \cap C_\lambda| / |E^*|\)，即真实解释词元中未被包含的比例。
- **阈值选择**：在标定集上，给定风险水平α，选择最小的λ使经验损失 \(\hat{R}_n(\lambda) \le \alpha - (1-\alpha)/n\)，从而保证测试集上的期望损失≤α（定理1）。
- **鲁棒方法（RULX）**：假设测试问题最多d个词元被噪声替换（从同义词集中选取），构建候选噪声集 \(B_{Q^*_{n+1}}\)。对每个词元，计算其在所有可能噪声问题中的最大重要性分数 \(R\)，然后基于该阈值 \(1-\hat{\lambda}\) 构建鲁棒集合。理论保证（定理2）：即使存在噪声，仍能维持期望覆盖。

### 算法流程（文字说明）
1. 使用标定集 \(D_{cal}\)，对每个λ候选值计算平均损失。
2. 用二分搜索找到满足式(3)的最小λ（记为 \(\hat{\lambda}\)）。
3. 对测试问题，根据重要性分数≥1-\(\hat{\lambda}\) 的词元构成不确定性集合。
4. 鲁棒版本中，先计算鲁棒分数 \(R\)，再以此构建集合。

## 3. 实验设计

### 数据集
- **MedMCQA**：大规模医学多选题，约19.4万题，带真实解释。
- **MedExpQA**：622个临床多选题，多语言，带金标准解释。

### 基准方法
- 无直接对比方法（该任务是首次提出），论文主要验证自身方法是否达到理论保证，并与“无鲁棒性的版本”对比。

### 评测指标
- **有效性**：经验损失是否低于目标风险α。
- **效率**：平均不确定性集合大小。

## 4. 资源与算力

- 论文**未明确说明**所使用的GPU型号、数量或训练时长。仅提及使用GPT-4o和Gemini 2.0 Flash模型，温度设为1，但未提供推理/微调的具体算力成本。

## 5. 实验数量与充分性

- **主要实验组**：
  - ULXQA在MedMCQA和MedExpQA两个数据集上，使用GPT-4o和Gemini 2.0 Flash，测试两个风险水平（α=0.45, 0.8）——共4种设置（图1）。
  - 效率展示对应上述设置（图2）。
  - 鲁棒性实验：仅在MedMCQA上使用Gemini 2.0 Flash，测试4个α值（0.15, 0.3, 0.45, 0.8）（图3）, 效率对比（图4）。
  - 可视化案例（图5）。
- **充分性评价**：实验覆盖了主流LLM和两种类型数据集，验证了有效性、效率、鲁棒性。但仅使用医学领域数据集，未涉及其他领域（如法律、开放域）。鲁棒性测试仅针对一种模型、一种噪声场景。整体较为充分，但泛化性验证有限。

## 6. 论文的主要结论与发现

- ULXQA能在目标风险α下持续保持经验损失≤α，提供有效的覆盖保证。
- 集合大小通常较小（如MedMCQA上α=0.45时约3个词元），表明效率高。
- 可视化显示预测集合与真实解释高度重叠。
- RULX在噪声数据下保持有效覆盖，而非鲁棒方法经常超风险界限；鲁棒集合大小与无鲁棒方法相当，没有严重牺牲效率。
- 理论保证（定理1、2）通过实验验证成立。

## 7. 优点

- **理论贡献**：首次为LLM自然语言解释提供严格的不确定性保证，所提方法**后验且模型无关**，不依赖模型内部结构。
- **方法设计**：利用提示获取重要性分数，巧妙地将共形预测扩展到自回归生成场景；鲁棒版本通过最大化重要性分数集合处理词元噪声，具有理论合理性。
- **实验验证**：包含有效性、效率、可视化、鲁棒性多项评估，证据充分。

## 8. 不足与局限

- **领域局限**：仅使用医学QA数据集（MedMCQA、MedExpQA），未验证在法律、开放域等更广泛场景下的表现。
- **模态局限**：仅考虑单模态文本输入，未拓展到多模态（如图像问答）。
- **噪声假设**：鲁棒方法假设噪声来自同义词替换，且最多影响d个词元，现实噪声可能更复杂（如重新表述或插入/删除）。
- **效率刻画**：未讨论阈值λ的搜索计算开销，也未比较与其他不确定性方法的计算成本。
- **公平性**：未涉及不同LLM架构（如开源模型）的对比，仅商用模型。此外，未评估重要性分数质量对结果的影响（虽理论不依赖质量，但实际效率可能会变差）。

（完）
