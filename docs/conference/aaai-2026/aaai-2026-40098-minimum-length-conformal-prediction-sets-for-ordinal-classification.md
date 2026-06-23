---
title: Minimum-Length Conformal Prediction Sets for Ordinal Classification
title_zh: 序数分类的最小长度共形预测集
authors: "Zijian Zhang, Xinyu Chen, Yuanjie Shi, Liyuan Lillian Ma, Zifan Xu, Yan Yan"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40098/44059"
tags: ["query:uq-safety"]
score: 6.0
evidence: 序数分类中共形预测用于不确定性量化
tldr: 针对序数分类中的不确定性量化问题，本文提出一种模型无关的序数共形预测方法，在保证统计覆盖的前提下最小化预测集长度。该方法不要求底层模型预测单峰分布，填补了现有方法的空白，为高可靠场景提供高效可靠的UQ工具。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有序数共形预测方法依赖于启发式算法或限制性假设，缺乏模型无关性和分布自由性。
method: 提出一种模型无关的序数共形预测方法，最小化预测集长度并保证覆盖。
result: 在序数分类数据集上实现了更短的平均预测集长度，同时维持了有效的覆盖保证。
conclusion: 该方法为序数分类提供了一种高效且鲁棒的不确定性量化方案。
---

## Abstract
Ordinal classification has been widely applied in many high-stakes applications, e.g., medical imaging and diagnosis, where reliable uncertainty quantification (UQ) is essential for decision making. Conformal prediction (CP) is a general UQ framework that provides statistically valid guarantees, which is especially useful in practice. However, prior ordinal CP methods mainly focus on heuristic algorithms or restrictively require the underlying model to predict a unimodal distribution over ordinal labels. Consequently, they provide limited insight into coverage–efficiency trade-offs, or a model-agnostic and distribution-free nature favored by CP methods. To this end, we fill this gap by propose an ordinal-CP method that is model-agnostic and provides instance-level optimal prediction intervals. Specifically, we formulate conformal ordinal classification as a minimum-length covering problem at the instance level. To solve this problem, we develop a sliding-window algorithm that is optimal on each calibration data, with only a linear time complexity in K, the # of label candidates. The local optimality per instance further also improves predictive efficiency in expectation. Moreover, we propose a length-regularized variant that shrinks prediction set size while preserving coverage. Experiments on four benchmark datasets from diverse domains are conducted to demonstrate the significantly improved predictive efficiency of the proposed methods over baselines (by 15%↓ on average over four datasets).

---

## 论文详细总结（自动生成）

# 论文结构化总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：序数分类广泛应用于医学影像、信用风险评估等高风险场景，但现有序数共形预测（CP）方法存在两个主要缺陷：一是依赖启发式算法（如Ordinal APS），无法保证预测区间最优性；二是要求底层模型输出单峰分布（如COPOC），缺乏模型无关性和分布自由性。
- **研究动机**：需要一种模型无关、分布自由的序数CP方法，能在保证统计覆盖（marginal coverage）的前提下最小化预测集长度（即提升预测效率），同时保持结构上的连续性（预测集为连续区间）。
- **整体含义**：本文提出的min-CPS和min-RCPS填补了这一空白，为序数分类提供了高效、可靠的不确定性量化工具。

## 2. 提出的方法论
### 核心思想
- **实例级最小长度覆盖**：对每个输入样本，寻找一个包含模式标签（置信度最高的标签）且累积概率不低于阈值τ的最短连续区间。
  - 形式化：min_{(l,u)∈U(X;τ)} (u−l)，满足U(X;τ) = {(l,u): sum_{k=l}^{u} f(X)_k ≥ τ, 且 l≤ŷ*(X)≤u}。
- **滑动窗口算法（Algorithm 1）**：
  - 预计算前缀和数组，枚举右边界u从模式标签向右移动，并滑动左边界l，保证区间包含模式且覆盖概率≥τ；每次更新最优解。
  - 时间复杂度O(K)（K为类别数），保证实例级最优性（Theorem 1）。
- **全局校准**：通过二分搜索（Algorithm 2）寻找最小阈值τ，使得校准集上的经验覆盖率F(τ) ≥ 1−α。依赖径向单调性（radial monotonicity）保证F(τ)单调非减，从而有嵌套性及有效覆盖（Theorem 2）。
- **长度正则化变体（min-RCPS）**：在可行集约束中引入长度惩罚项−λ·ℓ(l,u)，使得模型倾向于选择更短的区间，进一步压缩预测集大小（Corollary 1保证覆盖）。

## 3. 实验设计
### 数据集
- 四个公开基准数据集：
  - **UTKFace**（人脸年龄估计，图像，K=年龄类别数）
  - **Avocado Price**（牛油果价格等级，表格/时间序列）
  - **Electric Motor Temperature**（电机温度监测，传感器数据）
  - **IMDB**（人脸年龄，大规模图像）
  覆盖图像、表格、时间序列等多种模态。

### 对比方法（Baselines）
- **Naive CDF**：基于累积概率的简单方法。
- **Ordinal APS**：专为序数分类改进的自适应预测集方法（启发式）。
- **WCRC**：基于风险控制的加权共形方法。

### 实验设置
- 评估指标：**Coverage**（是否≥1−α）、**Prediction set size**（越小越好）。
- 默认α=0.1，另在Avocado Price上测试α∈{0.05,0.01}。
- min-RCPS的超参数λ在{0.001~0.019}范围内调优。

## 4. 资源与算力
- **文中未明确说明**所使用的GPU型号、数量、训练时长等硬信息。仅报告了各方法的**运行时间**（秒），用于对比效率（见表3）。例如min-CPS在Temperature数据集上运行312秒，而Ordinal APS需6183秒。

## 5. 实验数量与充分性
- **主要实验**：4个数据集上的覆盖率和预测集大小对比（表1）。
- **不同α测试**：1个数据集（Avocado Price）上3种α值（0.1/0.05/0.01）（表2）。
- **正则化参数λ敏感性**：在Avocado Price上展示λ对覆盖率和预测集大小的影响（图1）。
- **单调性验证**：在UTKFace和IMDB上展示F(τ)随τ单调递增（图2）。
- **运行时间对比**：表3。
- **评价**：实验覆盖了多种模态数据集，对比了多个基线，验证了不同α下的稳定性，并做了参数敏感性分析。但缺少消融实验（如无锚点约束的变体）、缺少对径向单调性假设违反时的鲁棒性测试、缺少条件覆盖（conditional coverage）评估。总体充分性较好，但仍可加强。

## 6. 主要结论与发现
- min-CPS和min-RCPS在所有数据集上均有效维持了1−α覆盖率，同时显著减小预测集大小。
  - 与最佳基线Ordinal APS相比，min-CPS在四个数据集上预测集大小分别降低5.11%、7%、39.93%、3.49%；min-RCPS分别降低6.96%、7.01%、41.21%、3.16%。
  - 平均下降**14%**（min-CPS）和**15%**（min-RCPS）。
- 在不同α下（Avocado Price），平均降低33.65%~34.39%。
- 运行时间比Ordinal APS快10×~22×。
- 长度正则化λ取较小值即可进一步提升效率。

## 7. 优点
- **理论贡献**：证明了实例级最优性（Theorem 1）、径向单调性下的嵌套性和覆盖保证（Theorem 2），并说明了正则化变体的有效性。
- **算法高效**：线性时间复杂度的滑动窗口算法，实际运行速度远超启发式方法。
- **模型无关**：不依赖特定模型结构或单峰假设，适用于任意预测分布。
- **实用性**：在多种数据模态上验证，参数易调节，代码开源。

## 8. 不足与局限
- **径向单调性假设**：虽经验证满足，但当模型预测不满足该条件时可能破坏嵌套性，影响二分搜索收敛性，文中未提供鲁棒性分析。
- **缺少条件覆盖评估**：仅验证了边际覆盖，未对条件覆盖或类别条件覆盖进行分析。
- **消融实验不充分**：未隔离锚点约束、窗口大小等设计选择的贡献。
- **正则化λ选择**：依赖交叉验证，缺乏自适应或理论指导。
- **计算资源未报告**：无法复现具体硬件需求。
- **仅限连续区间**：对于非连续但可能更高效的预测集（如允许跳跃）未探索。

（完）
