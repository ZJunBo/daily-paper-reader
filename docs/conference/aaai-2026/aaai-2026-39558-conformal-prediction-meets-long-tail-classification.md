---
title: Conformal Prediction Meets Long-tail Classification
title_zh: 共形预测遇上长尾分类
authors: "Shuqi Liu, Jianguo Huang, Luke Ong"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39558/43519"
tags: ["query:uq-safety"]
score: 6.0
evidence: 用于不确定性量化的共形预测方法
tldr: 针对长尾分布下共形预测对不同类别覆盖不平衡的问题，本文提出Tail-Aware Conformal Prediction（TACP）方法，通过利用尾部类别的结构信息来缓解尾部欠覆盖。实验表明TACP能有效提升少数类的覆盖率，同时保持整体覆盖保证，为分类任务中的可靠性不确定性量化提供了新途径。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有共形预测在长尾分布下对尾部类别的覆盖不足，影响少数类的可靠性。
method: 提出Tail-Aware Conformal Prediction（TACP）方法，通过整合尾部类别特定信息来调整预测集。
result: 在长尾分类数据集上改善了尾部覆盖率，同时维持了边际覆盖保证。
conclusion: TACP方法有效缓解了长尾分类中不确定性量化的不平衡问题。
---

## Abstract
Conformal Prediction (CP) is a popular method for uncertainty quantification that converts a pretrained model's point prediction into a prediction set, with the set size reflecting the model's confidence. Although existing CP methods are guaranteed to achieve marginal coverage, they often exhibit imbalanced coverage across classes under long-tailed label distributions, tending to over cover the head classes at the expense of under covering the remaining tail classes. This under coverage is particularly concerning, as it undermines the reliability of the prediction sets for minority classes, even with coverage ensured on average. In this paper, we propose the Tail-Aware Conformal Prediction (TACP) method to mitigate the under coverage of the tail classes by utilizing the long-tailed structure and narrowing the head-tail coverage gap. Theoretical analysis shows that it consistently achieves a smaller head-tail coverage gap than standard methods. To further improve coverage balance across all classes, we introduce an extension of TACP: soft TACP (sTACP) via a reweighting mechanism. The proposed framework can be combined with various non-conformity scores, and experiments on multiple long-tailed benchmark datasets demonstrate the effectiveness of our methods.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：共形预测（Conformal Prediction, CP）是一种流行的不确定性量化方法，能输出带统计保证的预测集。但在长尾（Long-tail, LT）标签分布下，标准CP方法虽然满足边际覆盖（marginal coverage）保证，却容易出现**覆盖不平衡**：头部类别（head classes）被过度覆盖，而尾部类别（tail classes）覆盖不足。这种对少数类的欠覆盖会削弱预测集的可靠性，在高风险场景（如自动驾驶、医疗）中可能造成严重后果。
- **整体含义**：论文旨在解决长尾分布下共形预测的覆盖不平衡问题，提出能自适应利用长尾结构的方法，在保持边际覆盖保证的同时缩小头部与尾部之间的覆盖差距，并进一步向类条件覆盖（class-conditional coverage）迈进。

#### 2. 论文提出的方法论
- **核心思想**：利用长尾分布的结构信息，对头部类别的非一致性分数（non-conformity score）施加选择性排名惩罚，从而增大头部类别的分数，缩小其预测集，间接提高尾部类别的条件覆盖，最终缩小头-尾覆盖差距。
- **关键技术与细节**：
  - **Head-Tail划分**：按照类先验概率累积超过阈值 $\eta$（如50%）的最小标签集合定义为头类 $G_h$，其余为尾类 $G_t$。
  - **Tail-Aware Conformal Prediction (TACP)**：  
    定义新的非一致性分数：  
    $$s_{\text{TACP}}(x,y) = s(x,y) + \lambda \cdot \mathbb{I}(y \in G_h) \cdot (o_x(y) - k_r)^{+}$$  
    其中 $s(x,y)$ 是基础分数（如LAC、APS等），$o_x(y)$ 是标签 $y$ 的预测排名，$k_r$ 是正则化起始排名，$\lambda$ 是惩罚系数。该式仅对属于头类的样本，且排名高于 $k_r$ 时施加惩罚，提升头类分数，使其更难被包含在预测集中，从而降低头类条件覆盖。
  - **soft TACP (sTACP)**：  
    移除硬性的头-尾指示，改用连续的类先验权重：  
    $$s_{\text{sTACP}}(x,y) = s(x,y) + \lambda \cdot \hat{p}(y) \cdot (o_x(y) - k_r)^{+}$$  
    其中 $\hat{p}(y)$ 是估计的类先验概率。该策略使惩罚平滑地适应各类频率，减少对固定分区的依赖，更精细地平衡类条件覆盖。
- **算法流程**（文字说明）：
  1. 将校准数据集拆分为头类和尾类（或直接使用类先验）。
  2. 对每个校准样本 $(X_i,Y_i)$，按上述公式计算修正后的非一致性分数。
  3. 取 $(1-\alpha)$ 分位数作为阈值 $\hat{q}_\alpha$（经过有限样本校正）。
  4. 对测试样本，计算所有标签的修正分数，将低于阈值的标签组成预测集。
- **理论保证**：  
  Theorem 1：TACP仍满足边际覆盖保证 $P(Y_{n+1}\in C_{\text{TACP}}(X_{n+1}))\ge 1-\alpha$。  
  Theorem 2：存在合适的参数 $k_r$，使得头-尾条件覆盖差距小于标准CP的差距。

#### 3. 实验设计
- **数据集与场景**：
  - **CIFAR100-LT**：长尾变体，不平衡因子 $\mu\in\{50,100\}$，训练/校准/测试均按长尾分布采样。
  - **ImageNet-LT**：从Pareto分布采样，幂参数 $\rho\in\{0.3,0.6\}$，同样为全长尾设定。
- **基准（Baseline）方法**：
  - 头部-尾部实验中对比：STANDARD（标准split CP）、Partition-Wise（按头/尾分别校准）、TACP。
  - 类条件实验中对比：STANDARD、CLASSWISE（按类分别校准）、CLUSTER（按聚类组校准）、RC3P（秩校准类条件CP）、sTACP。
- **非一致性分数**：四种代表性分数：**APS**、**LAC**、**TOPK**、**RAPS**。
- **评价指标**：
  - CovGap-HT（头尾条件覆盖绝对差）、AvgSize（平均预测集大小）。
  - 类条件实验中增加CovGap（全类覆盖差距）和边际Coverage。

#### 4. 资源与算力
- 论文**未明确说明**使用的GPU型号、数量或训练时长。仅提到使用了预训练模型（来自Li et al. 2021），因此可能仅在现有模型上进行校准和评估，训练开销未知。

#### 5. 实验数量与充分性
- **实验组数**：
  - **Exp.1**（头-尾覆盖对比）：在CIFAR100-LT (μ=100)和ImageNet-LT (ρ=0.3)上，针对4种分数、η=50%，绘制随目标覆盖1-α变化的曲线，定性展示TACP缩小差距。
  - **Exp.2**（量化指标）：在CIFAR100-LT (μ=50,100)和ImageNet-LT (ρ=0.3,0.6)上，α=10%，η=50%，对比STA、PW、TACP的CovGap-HT和AvgSize，每个设置重复100次取平均值±标准差。
  - **Exp.3**（CLASSWISE局限性）：展示在ImageNet-LT (ρ=0.6)上CLASSWISE导致几乎全标签集合。
  - **Exp.4**（类条件对比）：在ImageNet-LT (ρ=0.3,0.6)上，α=10%，对比STA、CLUS、RC3P、sTACP的CovGap、Coverage、AvgSize。
  - **Exp.5**（更严格α=5%）：只使用APS分数，展示sTACP仍有效，而CW和RC3P失效，CLUS退化。
- **充分性评价**：实验较为充分。涵盖了不同数据集、不平衡程度、多种分数和不同目标覆盖水平，重复100次以降低随机性。对比了多个相关基线，验证了TACP和sTACP在不同设置下的鲁棒性。但缺少消融实验分析λ和k_r的敏感度，也未在真实长尾数据集（如医疗影像）上验证。

#### 6. 论文的主要结论与发现
- TACP在所有测试场景下均能**显著缩小头-尾覆盖差距**，同时保持或略微降低平均预测集大小。
  - 例如：ImageNet-LT (ρ=0.6) + APS，CovGap-HT从2.18降至1.11，AvgSize从36.43降至33.98。
- sTACP进一步**降低类条件覆盖差距**，优于STANDARD、CLUSTER和RC3P。
  - 例如：ImageNet-LT (ρ=0.3) + APS，sTACP的CovGap为15.86%，而STANDARD为19.00%。
- 标准CP在长尾设置下头-尾覆盖严重不平衡，CLASSWISE方法因尾部样本少导致阈值估计噪声大、预测集过大。
- 结论：TACP和sTACP是鲁棒、高效且平衡的不确定性量化方法，适用于长尾分类。

#### 7. 优点
- **方法创新**：首次针对全长尾设定（训练、校准、测试均长尾）设计覆盖平衡方法，利用结构信息而非简单分群。
- **理论支撑**：给出了边际覆盖保证和头-尾差距缩小的理论证明（Theorem 1 & 2）。
- **灵活性**：可与多种非一致性分数结合（APS、LAC、TOPK、RAPS），即插即用。
- **实用性**：sTACP避免了硬划分，更平滑地控制惩罚，面向类条件覆盖平衡，且无需复杂的聚类或秩校准，计算简单。
- **实验全面**：覆盖多种数据集、不平衡度、分数和目标覆盖水平，统计上重复多次以验证稳定性。

#### 8. 不足与局限
- **超参数敏感性**：TACP和sTACP依赖参数 $\lambda$ 和 $k_r$，虽通过网格搜索调参，但论文未讨论其敏感性或自适应选择方法，可能影响实际部署的简便性。
- **未讨论计算开销**：虽然方法本身简单，但未与其它方法（如RC3P）对比校准时间或推理效率。
- **数据域限制**：仅在CIFAR100-LT和ImageNet-LT两个图像数据集上验证，未推广到其他长尾场景（如文本分类、医疗影像、对象检测），泛化性有待确认。
- **sTACP权重设计简单**：采用线性类先验权重 $\hat{p}(y)$，可能并非最优，更复杂的权重函数（如对数、幂律）可能进一步改善覆盖平衡。
- **未消融分析**：缺乏对单独组件（如排名截断 $k_r$、惩罚强度 $\lambda$）影响的系统性消融实验。
- **忽略校准集大小的影响**：在不同校准样本量下方法的稳定性未探讨，而长尾设置中尾部类校准样本极少，可能导致阈值估计不稳定。

（完）
