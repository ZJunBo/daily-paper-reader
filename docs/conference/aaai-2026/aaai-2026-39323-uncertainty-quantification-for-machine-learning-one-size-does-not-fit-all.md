---
title: "Uncertainty Quantification for Machine Learning: One Size Does Not Fit All"
title_zh: 机器学习的不确定性量化：一刀切并不适用
authors: "Paul Hofman, Yusuf Sale, Eyke Hüllermeier"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39323/43284"
tags: ["query:uq-safety"]
score: 8.0
evidence: 通用不确定性量化框架
tldr: 该论文指出机器学习中不存在通用的最佳不确定性度量，主张应根据具体任务选择度量。提出基于适当评分规则的灵活不确定性度量族，区分总不确定性、偶然不确定性和认知不确定性。通过实验展示不同度量在不同任务中的效用，为不确定性量化提供了理论指导。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有不确定性度量常声称优于其他，但实际上没有单一最佳度量。
method: 使用适当评分规则实例化不确定性度量，区分总、偶然和认知不确定性。
result: 在多种任务上验证了不同度量的适用性。
conclusion: 不确定性量化需根据应用定制，提供了选择度量的一般框架。
---

## Abstract
Proper quantification of predictive uncertainty is essential for the use of machine learning in safety-critical applications. Various uncertainty measures have been proposed for this purpose, typically claiming superiority over other measures. In this paper, we argue that there is no single best measure. Instead, uncertainty quantification should be tailored to the specific application. To this end, we use a flexible family of uncertainty measures that distinguishes between total, aleatoric, and epistemic uncertainty of second-order distributions. These measures can be instantiated with specific loss functions, so-called proper scoring rules, to control their characteristics, and we show that different characteristics are useful for different tasks. In particular, we show that, for the task of selective prediction, the scoring rule should ideally match the task loss. On the other hand, for out-of-distribution detection, our results confirm that mutual information, a widely used measure of epistemic uncertainty, performs best. Furthermore, in an active learning setting, epistemic uncertainty based on zero-one loss is shown to consistently outperform other uncertainty measures.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义

- **研究动机**：在安全关键应用中，机器学习模型必须量化预测不确定性。现有工作往往声称某种不确定性度量（如互信息）普遍最优，但实际上缺乏针对不同下游任务（选择性预测、异常检测、主动学习）的定制化考量。
- **整体含义**：该论文提出“**一刀切并不适用**”的核心论点——不存在通用的最佳不确定性度量；不确定性量化的设计应与具体任务的目标损失对齐，方能达到最优性能。

---

### 2. 方法论

- **核心思想**：利用**二阶分布**（分布上的分布）表示认知不确定性，并基于**适当评分规则**（proper scoring rules）构造一个灵活的不确定性度量族，将总不确定性（TU）分解为偶然不确定性（AU）和认知不确定性（EU）。
- **关键技术细节**：
  - 给定二阶分布 \( Q \)，贝叶斯模型平均预测 \(\bar{\theta} = \mathbb{E}_{\theta \sim Q}[\theta]\)。
  - 定义：
    \[
    \text{TU}(Q) = \mathbb{E}_{\theta \sim Q}\big[L_\ell(\bar{\theta}, \theta)\big],\quad
    \text{AU}(Q) = \mathbb{E}_{\theta \sim Q}\big[L_\ell(\theta, \theta)\big],\quad
    \text{EU}(Q) = \text{TU}(Q) - \text{AU}(Q)
    \]
    其中 \(L_\ell(\hat{\theta}, \theta) = \mathbb{E}_{y\sim\theta}[\ell(\hat{\theta}, y)]\) 是评分规则 \(\ell\) 的期望损失。
  - 具体实例：**Log损失**（对应Shannon熵与KL散度）、**Brier损失**（对应Gini杂质与期望平方差）、**零一损失**（对应置信度互补与标签级分歧）。
- **公式/算法流程**（文字说明）：
  - 使用任务损失 \(\ell_{\text{task}}\) 实例化不确定性度量，则总不确定性恰好是实例级期望任务损失的代理，从而理论上证明选择性预测中按总不确定性降序拒绝实例可最小化期望AULC（Proposition 1）。
  - 对于OoD检测，认知不确定性（利用Log损失实例化即互信息）能最好地区分分布内与分布外样本。
  - 对于主动学习，基于零一损失的认知不确定性（只关注标签级分歧）能最有效地筛选信息量最大的未标注样本。

---

### 3. 实验设计

- **数据集与场景**：
  - **选择性预测**：COVERTYPE数据集，RandomForest集成树。
  - **OoD检测**：iD数据为CIFAR-10，OoD评测在CIFAR-100、PLACES365、SVHN上进行。额外补充实验使用ImageNet、Food101作为iD（见附录）。
  - **主动学习**：MNIST、FashionMNIST、MedMNIST子集（TissueMNIST、BloodMNIST）。
- **Benchmark**：无显式单一标准，但对比了不同损失实例化（Log、Brier、零一）在相同二阶近似方法下的效果。
- **对比方法**：
  - 二阶分布近似：**Monte Carlo Dropout**、**Deep Ensemble**、**Laplace近似**（仅OoD）。
  - 不确定性度量：Log损失、Brier损失、零一损失各自实例化的TU、AU、EU（根据任务选择对应分量）。
- **实验设计客观性**：每个实验重复3次取均值和标准差；代码开源（github链接）。

---

### 4. 资源与算力

- 论文**未明确说明**使用的GPU型号、数量或训练时长。仅提及使用了ResNet18等标准架构，通常在单GPU上可完成。主动学习实验采用LeNet或小型全连接网络，算力需求不大。需要指出这一信息缺失。

---

### 5. 实验数量与充分性

- **实验组数**：
  - 选择性预测：1个图（图1），3种任务损失 × 3种不确定性损失实例化；未提消融（如不同模型、数据集规模）。
  - OoD检测：3种近似方法 × 3种损失实例化，在3个OoD数据集上报告AUROC（表1）；正文仅展示CIFAR-10作为iD的一个设置，另有补充实验（ImageNet/Food101）。
  - 主动学习：3个数据集（图2），3种损失实例化，每个图展示学习曲线；未做不同种子数或不同初始化的消融。
- **充分性评价**：
  - **覆盖**：三个典型下游任务，每种任务至少有一个数据集和多个方法，覆盖了主要评测场景。
  - **公平性**：控制二阶近似方法不变，仅改变不确定性损失；重复3次。在选择性预测中，理论推导与实验一致，增强了可信度。
  - **不足**：所有实验均限于分类任务；未评估回归、结构化输出；未比较不同二阶近似方法之间的差异（仅在OoD中用了三种近似，但未深入探讨近似质量的影响）；缺乏大规模消融（如不同网络深度、多种种子、不同拒绝比例等）。

---

### 6. 主要结论与发现

1. **不确定性度量没有通用最佳**：其有效性完全取决于下游任务。
2. **选择性预测**：应使用**与任务损失一致的总不确定性**作为拒绝准则，理论证明最小化AULC。
3. **OoD检测**：**Log损失实例化的认知不确定性（互信息）** 最可靠，因为其高惩罚性有助于分离分布外样本。
4. **主动学习**：**零一损失实例化的认知不确定性（标签级分歧）** 最优，因其直接捕捉最需标注的标签模糊性。
5. 实践含义：研究者和从业者必须根据目标任务选择不确定性度量，否则可能产生误导性结论。

---

### 7. 优点

- **理论坚实**：利用适当评分规则给出了不确定性度量的统一分解，并与任务损失建立严格的理论联系（Proposition 1的证明）。
- **框架灵活**：通过更换评分规则即可调整度量的性质，易于推广到其他损失函数。
- **任务对齐**：清晰揭示了不同任务对不确定性信号的不同需求，修正了“一种度量通吃”的错误实践。
- **实验验证**：在三个经典下游任务上均提供了理论和经验一致性，增强了说服力。
- **开源代码**：补充材料包含更多数据集和消融，便于复现。

---

### 8. 不足与局限

- **实验覆盖有限**：仅在分类任务上验证；未拓展到回归、结构化预测、成本敏感或类别不平衡场景。
- **二阶近似假设**：所有结果依赖于合理的二阶信念近似；弱近似（如过浅的集成、欠拟合的后验）会降低增益，论文未深入讨论该敏感性。
- **算力与资源未明确**：无法评估实验的可扩展性。
- **OoD检测结论的泛化性**：论文承认互信息的最佳表现可能依赖于具体的分布偏移形式，并非通用最优。
- **缺少与最新方法的比较**：未对比其他不基于评分规则的不确定性度量（如分布外检测专用评分、贝叶斯主动学习中的Information Gain等）。
- **选择性预测实验**：仅使用RandomForest一个模型，未在深度学习模型上验证理论（但OoD和主动学习用了深度学习）。

---

（完）
