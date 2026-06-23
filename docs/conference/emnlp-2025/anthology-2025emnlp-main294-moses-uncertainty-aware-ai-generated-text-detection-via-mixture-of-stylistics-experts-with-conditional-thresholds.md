---
title: "MoSEs: Uncertainty-Aware AI-Generated Text Detection via Mixture of Stylistics Experts with Conditional Thresholds"
title_zh: MoSEs：基于混合文体专家与条件阈值的不确定性感知AI文本检测
authors: "Junxi Wu, Jinpeng Wang, Zheng Liu, Bin Chen, Dongjian Hu, Hao Wu, Shu-Tao Xia"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.emnlp-main.294.pdf"
tags: ["query:luq"]
score: 4.0
evidence: 基于不确定性感知的AI生成文本检测，带有条件阈值
tldr: 本文提出混合文体专家（MoSEs）框架，用于AI生成文本检测。该框架通过条件阈值估计实现风格感知的不确定性量化，克服了传统方法依赖静态阈值和忽视文体建模的局限。实验表明，该方法在多个检测基准上提升了性能，并提供了可靠的置信度估计。
source: EMNLP-2025-Main
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.294/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1572, \"height\": 777, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.294/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 801, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.294/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1591, \"height\": 978, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.294/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 776, \"height\": 501, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1652, \"height\": 702, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 796, \"height\": 352, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1652, \"height\": 700, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 781, \"height\": 566, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 802, \"height\": 997, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 815, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 696, \"height\": 430, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 967, \"height\": 396, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1637, \"height\": 395, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1020, \"height\": 333, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1475, \"height\": 629, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1603, \"height\": 887, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1613, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1586, \"height\": 1993, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1580, \"height\": 2342, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1584, \"height\": 2199, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1580, \"height\": 2352, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.294/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1582, \"height\": 1273, \"label\": \"Table\"}]"
motivation: 现有AI文本检测方法忽略文体特征且使用静态阈值，性能受限。
method: 提出MoSEs框架，包含文体参考库、风格感知路由器和条件阈值估计器，实现不确定性量化。
result: 在多个数据集上，MoSEs优于基线方法，且不确定性估计与实际错误率高度相关。
conclusion: 将不确定性量化融入检测系统，提高了检测的可靠性和可解释性。
---

## Abstract
The rapid advancement of large language models has intensified public concerns about the potential misuse. Therefore, it is important to build trustworthy AI-generated text detection systems. Existing methods neglect stylistic modeling and mostly rely on static thresholds, which greatly limits the detection performance. In this paper, we propose the Mixture of Stylistic Experts (MoSEs) framework that enables stylistics-aware uncertainty quantification through conditional threshold estimation. MoSEs contain three core components, namely, the Stylistics Reference Repository (SRR), the Stylistics-Aware Router (SAR), and the Conditional Threshold Estimator (CTE). For input text, SRR can activate the appropriate reference data in SRR and provide them to CTE. Subsequently, CTE jointly models the linguistic statistical properties and semantic features to dynamically determine the optimal threshold. With a discrimination score, MoSEs yields prediction labels with the corresponding confidence level. Our framework achieves an average improvement 11.34% in detection performance compared to baselines. More inspiringly, MoSEs shows a more evident improvement 39.15% in the low-resource case. Our code is available at https://github.com/creator-xi/MoSEs.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（如GPT-4、LLaMA、Qwen）的快速发展使得AI生成文本在新闻、故事、评论、学术论文等领域广泛应用，但潜在滥用（如虚假新闻、学术不端）引发了严重的伦理和社会担忧。因此，构建可靠的AI生成文本检测系统至关重要。
- **现有方法的两大局限**：
  - **忽视文体建模**：人类文本具有职业/文化背景塑造的“惯习”（habitus），如记者客观简洁，学者严谨逻辑；而LLM学习多模态语料中的混合风格，在复制特定文化背景下的真实人类风格变化时会出现偏差，现有检测方法利用这一线索不足。
  - **静态决策阈值**：当前方法通常使用固定的静态阈值进行判断，未能量化与语言属性相关的不确定性，导致决策不可信。
- **本文整体含义**：提出MoSEs框架，将文体感知（stylistics-aware）与条件阈值估计（conditional threshold estimation）相结合，实现不确定性量化，从而提升AI文本检测的性能和可靠性。

## 2. 方法论：核心思想、关键技术细节与算法流程

### 2.1 核心思想
- 构建一个包含多风格标注数据的**文体参考库（SRR）**，并利用语义嵌入对样本进行聚类，形成文体感知的潜在空间。
- 对于输入文本，通过**风格感知路由器（SAR）** 动态激活SRR中最相关的参考样本群体。
- 使用**条件阈值估计器（CTE）**，联合建模语言统计属性与语义特征，自适应地确定最优分类阈值，结合判别分数输出预测标签及置信度。

### 2.2 关键技术细节

#### 文体参考库（SRR）
- 多风格标注数据集（新闻、故事、辩论、学术论文、对话、评论等）。
- 每个样本包含：二值标签（人类/AI）、**条件特征**（文本长度、对数概率均值/方差、n-gram重复率、类型-标记比、深度语义嵌入）。

#### 风格感知路由器（SAR）
- 利用预训练语言编码器（如BGE-M3）提取语义嵌入，构建潜在空间。
- 采用**原型近似**：对每种风格s的样本聚类得到K个原型（prototypes），通过Sinkhorn-Knopp算法求解最优传输问题，得到原型矩阵P^s和分配矩阵Q^s。
- 对输入文本，计算其嵌入与所有原型的距离，选择**m个最近原型**，然后激活这些原型对应的所有参考样本（不进行硬分类，实现软路由）。

#### 条件阈值估计器（CTE）
- **CTE输入**：条件特征向量C（包括语言统计特征+PCA降维后的语义嵌入）和判别分数τ。
- **Logistic回归版本（MoSEs-lr）**：分类概率为P(y=1|C,τ) = σ(Cβ - τ)，其中β为线性系数。通过最小化类加权负对数似然损失优化参数。
- **XGBoost版本（MoSEs-xg）**：利用梯度提升树建模非线性交互，更灵活地学习阈值。
- **理论分析**：提供了估计阈值Cβ̂与最优阈值之间误差的渐近正态性证明，说明估计是无偏的，误差服从零均值高斯分布。

### 2.3 算法流程（文字说明）
1. **构建SRR**：收集多种风格的标注文本，提取条件特征和语义嵌入。
2. **聚类原型**：对每种风格样本的语义嵌入聚类，得到K个原型。
3. **路由（SAR）**：对输入文本，计算其嵌入与所有原型的距离，选择m个最近原型，激活这些原型对应的参考样本。
4. **阈值估计（CTE）**：用激活的参考样本训练CTE（Logistic回归或XGBoost），学习从条件特征+判别分数到最优阈值的映射。
5. **检测**：对输入文本，提取条件特征和判别分数，CTE输出自适应阈值，结合判别分数得到预测标签及置信度。

## 3. 实验设计：数据集、基准与对比方法

### 3.1 数据集
- **主数据集（4个）**：ChangeMyView（辩论）、XSum（新闻）、Reddit WritingPrompts（故事）、SciXGen（科学论文）。每个数据集1000个人类文本+1000个AI文本（由GPT-3.5 Turbo和LLaMA 65B生成，以人类文本前30个token为提示）。划分1800参考+200测试。
- **低资源数据集（4个）**：CNN/Daily Mail（新闻邮件）、DialogSum（对话）、IMDB（电影评论）、PubMedQA（生物医学问答）。每个数据集200个人类+200个GPT-4生成文本。划分200参考+200测试。
- **额外OOD评估**：ROCStories（故事）、SQuAD（维基百科段落）、GLM-130B生成文本。

### 3.2 判别分数模型（作为MoSEs的基础评分器）
- RoBERTa-base（训练型）
- Fast-DetectGPT（代理型，GPT-Neo-2.7B）
- Lastde（代理型，GPT-Neo-2.7B）

### 3.3 对比方法
- **静态阈值方法**：在参考数据集上最大化Youden’s J统计量找到最优阈值，对所有输入文本使用同一阈值。
- **最近邻投票方法**：在参考数据集中找到判别分数最接近的k=100个样本，取多数标签作为预测。

### 3.4 评估指标
- Accuracy（准确率）、F1 score。

### 3.5 其他实验设置
- 语言编码器：BGE-M3；PCA将语义嵌入降至32维。
- 条件特征共7个（文本长度、对数概率均值/方差、2-gram/3-gram重复率、类型-标记比、PCA语义嵌入）。
- MoSEs-lr使用逻辑回归；MoSEs-xg使用XGBoost（最大树深6，树数量100）。
- 原型数量K和最近原型数m未在正文中明确，但附录中提及（如K=5？待查）。

### 3.6 公平性与客观性
- 所有对比方法使用相同的判别分数模型，确保公平。
- 报告了McNemar检验的显著性结果（χ²=49.0和60.6，p值极小）。
- 代码开源。

## 4. 资源与算力

- 论文未明确说明训练MoSEs所需的具体GPU型号、数量及训练时长。
- 提到了计算环境：Intel Xeon(R) Gold 6226R CPU和NVIDIA GeForce RTX 3090 GPU。
- 给出了训练和推理时间（见表6）：
  - MoSEs-lr训练时间0.18秒/数据集，推理0.06ms/样本。
  - MoSEs-xg训练时间0.13秒/数据集，推理1.04ms/样本。
- 判别分数模型（如Lastde）推理时间为41ms/样本。
- 总体来看，MoSEs的计算开销远低于判别分数模型本身，但论文未说明训练判别分数模型（如RoBERTa、Fast-DetectGPT、Lastde）的算力需求。

## 5. 实验数量与充分性

### 5.1 实验组数
- **主实验**：4个数据集 × 3个判别模型 × 4种方法（静态阈值、最近邻投票、MoSEs-lr、MoSEs-xg）= 48个结果（表1）。
- **低资源实验**：4个数据集 × 3个判别模型 × 4种方法 = 48个结果（表2）。
- **消融实验**：
  - 选择策略比较（分类 vs. m-nearest，表3）
  - SAR有无（表4）
  - 条件特征逐个移除（表5，6个条件+默认，共7组）
  - 语义特征维度压缩实验（图4，多个维度）
  - 冗余特征分析（附录G，表10-11）
- **鲁棒性实验**：
  - 未见风格OOD（ROCStories、SQuAD，表8）
  - 未见LLM OOD（GLM-130B，表9）
  - 不同prompt生成方式（主题prompt、指定prompt，表13）
- **理论分析**：附录D中给出CTE估计的渐近正态性证明。

### 5.2 充分性评估
- **充分**：覆盖了标准、低资源、OOD、消融等多种场景，结果一致体现MoSEs优势。
- **客观公平**：对比方法均基于相同判别分数模型，控制变量；使用McNemar检验验证统计显著性。
- **局限性**：未在更大规模数据集或更多样化的LLM生成器上评估（仅覆盖GPT-3.5、LLaMA、GPT-4、GLM-130B）；OOD实验仅针对两种未见风格和一种未见LLM，覆盖有限。

## 6. 主要结论与发现

1. MoSEs（特别是MoSEs-xg）在所有设置下显著优于静态阈值和最近邻投票方法。
   - 主数据集：平均准确率提升 **11.34%**（表1）。
   - 低资源场景（200参考样本）：平均准确率提升 **19.43%**，其中RoBERTa上提升 **39.15%**（表2）。
2. **文体感知路由（SAR）** 和 **条件特征** 均对性能提升有重要贡献（消融实验表4、表5）。
3. **m-nearest原型选择策略**优于硬分类策略，说明软路由能捕获更丰富的文体信息（表3）。
4. 条件特征中，**2-gram重复率**、**类型-标记比**、**对数概率均值**对阈值估计影响较大（附录C）。
5. 适当的PCA维度压缩（如32维）能提升性能，过高维度可能引入噪声（图4）。
6. MoSEs具有良好的鲁棒性：在未见风格/未见LLM的OOD场景中仍然优于基线（表8、表9）。
7. 计算开销小：训练仅需毫秒级，推理微秒级（表6）。

## 7. 优点（方法/实验设计亮点）

- **创新性**：首次显式建模职业/文化特定的写作风格用于AI文本检测，结合了语言学统计属性与深度语义特征进行自适应阈值估计。
- **不确定性量化**：通过CTE输出置信水平，提高了检测系统的可信度。
- **低资源友好**：在仅有200个参考样本时仍能大幅提升性能，实际部署价值高。
- **模块化框架**：SRR、SAR、CTE可独立优化，且可适配任意判别分数模型（RoBERTa、Fast-DetectGPT、Lastde等）。
- **理论支撑**：提供了CTE估计误差的渐近正态性证明，解释其有效性。
- **实验设计全面**：涵盖标准、低资源、OOD、消融、prompt多样性等多种场景，对比充分，统计显著性检验严谨。
- **代码开源**，可复现性强。

## 8. 不足与局限

1. **算力信息缺失**：未报告训练判别分数模型（如RoBERTa、Fast-DetectGPT）所需的GPU资源与时长，MoSEs本身的训练也仅在单一RTX 3090上测试，缺乏大规模集群下的效率评估。
2. **OOD覆盖有限**：仅测试了两种未见风格和一种未见LLM，且未见LLM（GLM-130B）与训练中的LLM差异可能不够大，泛化能力验证不够充分。
3. **数据集规模较小**：主数据集每类仅1000样本，低资源仅200，未在更大规模（如万级）真实场景下验证。
4. **依赖判别分数模型**：MoSEs的效果受限于所选判别分数模型的质量，若分数模型本身有偏，阈值估计可能不准确。
5. **特征工程依赖**：语言统计特征（n-gram重复率、类型-标记比等）虽有效，但可能无法完全捕捉更复杂的文体特征（如修辞结构、篇章连贯性）。
6. **未探索多源检测**：论文指出当前仅二分类，虽然提到可扩展至多源检测（如SeqXGPT、DART），但未付诸实施。
7. **PCA维度选择缺乏自动化**：默认32维是通过实验手动选择，缺乏自适应维度选择机制。

（完）
