---
title: On the Impact of Weight Quantization on Deep Neural Network Uncertainty
title_zh: 权重量化对深度神经网络不确定性的影响
authors: "Shuang Liang, Xun Lu, Zi-Ang Liu, Ming-Liang Wang, Yan Lyu, Shao-Qun Zhang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39513/43474"
tags: ["query:uq-safety"]
score: 7.0
evidence: 权重量化对深度神经网络不确定性的影响
tldr: 该论文首次量化了权重量化对深度神经网络不确定性的影响，提出精确矩传播估计器EMP。发现量化显著增加不确定性，进而提出矩对齐方法MOMA以减少量化诱导的不确定性并保持精度。实验表明EMP和MOMA有效，深化了对量化模型可靠性的理解。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 权重量化对神经网络不确定性的影响未被充分研究。
method: 提出精确矩传播估计器量化不确定性，设计矩对齐方法降低不确定性。
result: 在多种网络和数据集上验证了不确定性增加及MOMA的缓解效果。
conclusion: 权重量化会显著增大不确定性，但可通过矩对齐进行恢复，指导量化模型的可靠使用。
---

## Abstract
Weight Quantization (WQ) is a key technique for lightweight Deep Neural Network (DNN) computations. While existing algorithms often pursue memory compression and inference acceleration with accuracy comparable to full-precision models, the effect of WQ on DNN uncertainty remains largely unexplored. In this paper, we quantify the impact of WQ on DNN uncertainty through the novel Exact Moment Propagation (EMP) uncertainty estimator. It is observed that WQ significantly increases DNN uncertainty. Based on the EMP estimator, we propose the MOMent Alignment (MOMA) to reduce WQ-induced uncertainty and preserve the accuracy of weight-quantized DNNs. Empirical results across various DNN architectures and datasets validate the effectiveness of both EMP and MOMA methods.

---

## 论文详细总结（自动生成）

# 论文总结：权重量化对深度神经网络不确定性的影响

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：权重量化（WQ）是降低深度神经网络（DNN）计算和存储成本的关键技术，现有方法在压缩率和精度保持上已有显著进展。然而，量化对模型**不确定性**（预测置信度的可靠性）的影响尚未被系统研究。
- **核心问题**：量化后的DNN是否比全精度模型具有更高的不确定性？如何量化这种影响？能否在量化训练中减少不确定性？
- **整体含义**：该工作首次统一量化了权重量化前后DNN的不确定性差异，揭示了量化会显著增加不确定性，并提出优化方法缓解这一副作用，对量化模型在安全敏感场景（如自动驾驶、医疗）中的应用具有重要指导意义。

## 2. 论文提出的方法论

### 核心思想
- **精确矩传播（EMP）**：一种与权重精度无关的不确定性度量方法。通过假设层内权重服从高斯分布（全精度）或三值分布（量化），精确计算激活值的一阶和二阶矩（均值和协方差），从而得到输出协方差（不确定性）。
- **矩对齐（MOMA）**：在量化训练中，通过调整划分阈值，使得三值权重的**第一中心矩（q-p）和第二中心矩（p+q-(q-p)^2）**接近零，以最小化输出不确定性，同时保持分类精度。

### 关键技术细节
- **线性传播**：利用定理3（通用）、推论4（全精度）、推论5（三值量化）精确计算预激活变量的均值和协方差。
- **非线性传播（ReLU）**：利用定理8，给出ReLU激活后期望和协方差的闭式表达式，避免了以往方法的近似误差。
- **MOMA优化**：在传统三值训练中，额外求解一个子优化问题：
  - 目标函数：最小化 |g₃(γ, W)| + λ·|g₄(γ, W)|
  - 约束：γ在传统划分因子γₛ的邻域内搜索，以保证精度。
  - g₃和g₄分别是q-p和p+q-(q-p)²的样本估计。

### 算法流程
- **EMP算法**（Algorithm 1）：输入样本分布和权重分布参数，逐层交替使用线性计算（推论5或4）和非线性计算（定理8），最终输出协方差矩阵。
- **MOMA训练**（Algorithm 2）：在每轮迭代中，更新全精度权重，计算传统阈值，再求解式(6)得到优化阈值，最后使用新阈值进行三值化。

## 3. 实验设计

- **数据集**：MNIST、CIFAR-10、CIFAR-100。
- **模型架构**：MLP-2（2层全连接）、LeNet-5、VGG-13、ResNet-18。
- **Benchmark（不确定性估计对比）**：以蒙特卡洛（MC）估计作为真值，比较EMP与PL-DNN（Bibi et al. 2018）和MP（Wu et al. 2019）。
- **对比方法**：
  - 全精度模型（FP-DNN）与三值量化模型（T-DNN）的 uncertainty 对比；
  - T-DNN 与 T-DNN-MOMA 的 uncertainty 和 accuracy 对比。
- **评估指标**：
  - 不确定性估计精度：方差比 rₒ(x) = V_MC / V_estimator，期望接近1。
  - 不确定性量化：Uncertainty = 1/|D| ∑ tr(Σ̂_y(x))。
  - 分类准确率。

## 4. 资源与算力

- 论文仅说明：所有实验使用 **13th Gen Intel Core i9-13900KF CPU** 和 **NVIDIA RTX 4090 GPU**，软件环境为 PyTorch 和 SciPy。
- **未明确说明**：训练 epoch 数、具体运行时间、总 GPU 小时数等。由于网络规模较小（MLP-2, LeNet-5, VGG-13, ResNet-18），推测总计算量适中。

## 5. 实验数量与充分性

- **实验组数**：
  - 表1展示了 LeNet-5 在 MNIST 和 CIFAR-10 上10个类别的不确定性估计结果（每个类别一行）。
  - 表2展示了4种架构在 MNIST 上的 accuracy 和 uncertainty 对比，并给出不确定降低百分比。
  - 附录 F、G 补充了其他架构（MLP-2, VGG-13, ResNet-18）在 CIFAR-10/100 的结果。
  - 图3：MLP-2 在 MNIST 上的方差比直方图（6个类别）。
- **充分性评估**：
  - 优点：涵盖了经典小模型（LeNet, MLP）和稍大的模型（VGG, ResNet），数据集覆盖手写数字和自然图像，不确定性估计对比了两种基线方法。
  - **不足之处**：实验规模较小，未涉及更大模型（如 ResNet-50 以上、Transformer、大语言模型），且仅在图像分类任务上验证；缺少对置信度校准（如ECE）或不确定性分离（认知/偶然）的分析。

## 6. 主要结论与发现

1. **EMP 不确定性估计精度高**：与 MC 估计的方差比接近 1，显著优于 PL-DNN 和 MP（表1）。
2. **权重量化显著增大不确定性**：T-DNN 的 uncertainty 比 FP-DNN 高 1.4 倍以上（图3），且在不同架构和数据集上一致。
3. **MOMA 有效降低不确定性**：在保持精度基本不变的前提下，T-DNN-MOMA 的 uncertainty 相比 T-DNN 降低 20%~98%（表2），例如 LeNet-5 上降低 98.55%，ResNet-18 上降低 44.27%。
4. **MOMA 不损害精度**：T-DNN-MOMA 的准确率与 T-DNN 相当甚至略优（如 VGG-13: 0.9954→0.9957）。

## 7. 优点

- **理论创新**：首次给出 ReLU 激活后协方差的精确闭式解（定理8），避免了以往方法基于强假设或近似的缺陷。
- **统一框架**：EMP 同时兼容全精度和量化模型，实现了公平比较。
- **实用优化**：MOMA 轻量且易集成到现有量化训练流程（仅需调整阈值搜索），无需额外正则项。
- **实验严谨**：采用 MC 作为 ground truth，重复5次消除随机性，报告均值和标准差。

## 8. 不足与局限

- **实验覆盖有限**：仅测试了三值量化（1.58-bit），未覆盖二进制或更低比特量化；仅使用 ReLU 激活，未验证其他激活函数；仅图像分类任务，缺乏 NLP、语音等领域的验证。
- **模型规模较小**：最大模型为 ResNet-18，未验证更大规模网络（如 ResNet-50 以上）或 transformer 架构。
- **假设简化**：权重独立同分布假设在复杂网络中可能不成立；预激活高斯假设（CLT近似）在大规模网络中需进一步验证。
- **不确定性类型未区分**：仅度量总体方差，未分离认知不确定性和偶然不确定性。
- **MOMA 依赖经验参数**：λ 和 c 的取值未经理论分析，可能对任务敏感。
- **资源信息不完整**：未提供具体训练耗时、GPU 内存等，不利于复现和扩展。

（完）
