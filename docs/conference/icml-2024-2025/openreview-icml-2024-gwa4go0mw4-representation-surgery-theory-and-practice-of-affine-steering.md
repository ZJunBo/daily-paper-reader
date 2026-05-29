---
title: "Representation Surgery: Theory and Practice of Affine Steering"
title_zh: 表征手术：仿射引导的理论与实践
authors: "Shashwat Singh, Shauli Ravfogel, Jonathan Herzig, Roee Aharoni, Ryan Cotterell, Ponnurangam Kumaraguru"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=GwA4go0Mw4"
tags: ["query:dg"]
score: 8.0
evidence: 推导语言模型激活引导的最优仿射函数
tldr: 该论文从理论角度研究语言模型的激活引导函数，在最小二乘意义下推导了两种最优仿射引导函数，为现有启发式引导方法提供了理论依据。通过将引导表述为优化问题，论文阐明了引导有效性的条件，并在实验中验证了所提引导函数在减少有害生成和性别偏见方面的有效性。这为激活引导提供了坚实的理论基础和实用工具。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-gwa4go0mw4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 807, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gwa4go0mw4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 806, \"height\": 279, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gwa4go0mw4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 772, \"height\": 572, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-gwa4go0mw4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 779, \"height\": 571, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-gwa4go0mw4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 840, \"height\": 554, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-gwa4go0mw4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1720, \"height\": 503, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-gwa4go0mw4/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1776, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-gwa4go0mw4/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1761, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-gwa4go0mw4/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 570, \"height\": 324, \"label\": \"Table\"}]"
motivation: 现有语言模型激活引导方法缺乏理论支撑，难以保证引导效果的最优性。
method: 从最小二乘优化角度推导两种最优仿射引导函数，并分析其性质。
result: 所提引导函数在减少毒性文本和性别偏见等任务上表现优异。
conclusion: 激活引导可以通过理论最优的仿射变换实现，提升了方法的可解释性和可靠性。
---

## Abstract
Language models often exhibit undesirable behavior, e.g., generating toxic or gender-biased text. In the case of neural language models, an encoding of the undesirable behavior is often present in the model's representations. Thus, one natural (and common) approach to prevent the model from exhibiting undesirable behavior is to steer the model's representations in a manner that reduces the probability of it generating undesirable text. This paper investigates the formal and empirical properties of steering functions, i.e., transformation of the neural language model's representations that alter its behavior. First, we derive two optimal, in the least-squares sense, affine steering functions under different constraints. Our theory provides justification for existing approaches and offers a novel, improved steering approach. Second, we offer a series of experiments that demonstrate the empirical effectiveness of the methods in mitigating bias and reducing toxic generation.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题**：基于神经网络的语言模型经常生成有害或带有性别偏见的文本，这些不良行为在模型的内部表征中有所体现。
- **动机**：常见做法是通过修改（即“引导”）模型的表征来减少不良生成的概率。但现有引导方法多依赖经验或启发式，缺乏理论支撑。
- **整体含义**：本文旨在为语言模型的表征引导提供严格的理论基础，证明在最小二乘意义下最优的仿射引导函数的封闭形式，并验证其在偏置缓解和毒性控制中的有效性。这连接了“概念擦除”与“引导”两大研究路线。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- 将表征引导形式化为一个受约束的最小二乘优化问题，目标是在最小化对原始表征的L2修改的同时，使引导后的表征满足“守卫性”（guardedness）——即线性分类器无法区分被引导的概念类别。

### 关键技术细节
1. **定义**：
   - 概念随机变量 \(C \in \{0,1\}\)，表征随机变量 \(H \in \mathbb{R}^D\)，条件均值 \(\mu_c = E[H | C=c]\)，条件协方差 \(\Sigma_c\)。
   - 引导函数 \(s_{c \to c'}(H)\)：当 \(C=c\) 时变换为 \(W H + b\)，当 \(C=c'\) 时保持原值。

2. **命题4.1：仅匹配均值的最优引导**  
   - 约束：\(E[s(H_c)] = E[s(H_{c'})]\)  
   - 解：\(W = I\)，\(b = \mu_{c'} - \mu_c\)（即平移向量）。  
   - 理论意义：仅为现有“引导向量”方法提供理论解释。

3. **命题4.2：匹配均值与协方差的最优引导（MiMiC）**  
   - 额外约束：\(E[s(H_c)s(H_c)^\top] = E[s(H_{c'})s(H_{c'})^\top]\)  
   - 解：  
     \(W = \Sigma_c^{-1/2} (\Sigma_c^{1/2} \Sigma_{c'} \Sigma_c^{1/2})^{1/2} \Sigma_c^{-1/2}\)  
     \(b = -W \mu_c + \mu_{c'}\)  
   - 关联：与高斯分布下的最优传输解等价；且能消除“按邻域偏置”（Bias by Neighbors）的期望值（命题4.3）。

4. **实际近似**：若无法直接获得概念标签 \(\phi\)，使用一个MLP分类器预测概念，并对预测为源类别的表征应用引导。

## 3. 实验设计：数据集、基准、对比方法

### 实验一：公平性多分类（Bios数据集）
- **数据集**：Bios（爬取的简短传记，含28种职业及性别标注）。
- **基准**：原始模型（无干预）、LEACE（完美线性概念擦除）、Xian等（2023）的后处理方法。
- **使用模型**：BERT-base、GPT-2、Llama2-7b（对Llama2降至768维）。
- **评价指标**：TPR RMS（真实阳性率均方根误差，衡量性别间偏置）、分类准确率。
- **实施**：在传记表征上拟合引导，然后训练逻辑回归分类器预测职业。

### 实验二：方言偏置受控实验（Blodgett等2016数据集）
- **数据集**：推特推文，按方言（AAE vs SAE）和情感（正/负）标注。
- **基准**：原始模型。
- **模型**：Llama2-7b（最后隐藏状态）。
- **设计**：人工改变AAE在正情感中的比例 \(p\)（0.5到0.95），观测TPR RMS变化。
- **评价**：TPR RMS、准确率。

### 实验三：毒性生成控制
- **数据集**：Toxic Comments Classification Challenge（训练引导）；Real Toxicity Prompts（评估，10k非毒性提示）。
- **基准**：GPT-2 (large)、DAPT、GeDI、PPLM、UDDIA、DExperts、GOODTRIEVER等。
- **评价**：期望最大毒性、毒性概率、困惑度（GPT-2 XL）、n-gram多样性。
- **实施**：对每个生成步的最后token嵌入应用引导；使用距 \(\mu_c\) 与 \(\mu_{c'}\) 的距离作为是否应用引导的判断。

### 对比方法
- LEACE（概念擦除）
- Xian等（2023）后处理方法
- 仅均值匹配引导
- 均值+协方差匹配引导（MiMiC）
- 全向量应用（消融实验）

## 4. 资源与算力

- **文中未明确说明**：未报告GPU型号、数量、训练时长等具体算力信息。仅在致谢部分提及使用Google Research的实习资源，但无详细硬件规格。

## 5. 实验数量与充分性

### 实验数量
- **主要实验组数**：至少3组（Bios公平性、方言偏置受控、毒性生成）。
- **消融实验**：
  - 在毒性生成中对比了“选择性应用” vs “全向量应用”。
  - 在Bios中报告了“偏置按邻域”的定性（余弦相似度热图）和定量（top-k同性别比例）分析。
  - 在方言实验中，从 \(p=0.5\) 到 \(p=0.95\) 共10个不同偏置水平。
- **模型跨度**：BERT-base、GPT-2、GPT-2 Large、Llama2-7b共4种不同规模架构。

### 充分性与公平性
- **充分性**：覆盖了多类任务（分类与生成）、多种偏置源（性别、方言、毒性），并包含内部消融和基线对比，实验设计较为全面。
- **客观性与公平性**：
  - 公平性实验中使用了广泛接受的TPR Gap指标。
  - 毒性实验中遵循Gehman等（2020）的标准评估协议（25次采样、Perspective API）。
  - 但文中部分基线结果引用自Pozzobon等（2023），未完全自行复现；且未在更大规模模型（如Llama2-13B）上验证。
  - 引导函数依赖一个外层MLP估计概念标签，其误差可能影响结果，但文中未充分讨论误差传播。

## 6. 论文的主要结论与发现

1. **理论贡献**：在最小二乘意义下，最优的仿射引导函数仅需平移（匹配均值）；若进一步匹配协方差，则获得更优的引导（MiMiC），且能消除期望上的“按邻域偏置”。
2. **实验验证**：
   - 在Bios性别偏置缓解中，MiMiC将TPR RMS从0.155降至0.093（BERT-base），且准确率损失微小（0.799→0.785）。
   - 在方言偏置受控实验中，两种引导方法均能消除因数据集比例不同导致的TPR Gap，完全切断偏置依赖。
   - 在毒性生成中，选择性应用MiMiC使期望最大毒性从0.39降至0.29，效果与部分需要微调的基线相当，但无需梯度计算。
3. **局限性**：目前的线性干预能力有限，在毒性任务上未达到最先进水平；全向量应用虽降低毒性最多（0.17），但严重损害困惑度（22.6→54.0）。

## 7. 优点：方法或实验设计上的亮点

- **理论完备性**：首次从优化角度严格推导最优仿射引导，弥补了该领域理论空白。
- **简洁有效**：最优解为封闭形式，计算轻量（仅需均值、协方差），可快速集成到任意语言模型推理中。
- **连接性**：统一了概念擦除与引导；指出协方差匹配与最优传输的等价关系。
- **实验设计亮点**：方言受控实验展示了引导如何阻断数据集偏置与模型偏置之间的关联，验证了因果有效性。

## 8. 不足与局限

- **线性假设局限**：仿射变换只能消除线性可分的偏置，对于非线性编码的偏置（如高阶聚类）效果有限。
- **实验覆盖**：仅测试了LLM在中等规模（≤7B参数）上的性能，未在更大模型（如Llama2-13B/70B）上验证。
- **引导依赖分类器**：实际使用时需用MLP预测概念标签，该分类器的误差会传播到引导中（文中仅报告96.8%准确率，未做误差分析）。
- **毒性任务未达SOTA**：在期望最大毒性指标上（0.29）不及DExperts（0.21）和GOODTRIEVER（0.22），且牺牲了一定困惑度。
- **伦理与社会风险**：二值化性别概念（MALE→FEMALE）可能固化二元性别刻板印象；引导方向的选择可能意外强化其他方向的偏置。

（完）
