---
title: Physics-Informed Multi-Task Learning for Battery State of Health Prediction with Uncertainty Quantification
title_zh: 基于物理信息多任务学习的电池健康状态预测与不确定性量化
authors: "Tianwen Zhu, Guangyu Wu, Zhiwei Cao, Ruihang Wang, Jimin Jia, Yong Luo, Yonggang Wen"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37143/41105"
tags: ["query:uq-safety"]
score: 4.0
evidence: 电池健康预测中的不确定性量化
tldr: 该论文针对电池健康状态预测，提出多任务学习框架，结合物理信息神经网络与自动编码高斯混合模型进行不确定性建模。能量分数作为不确定性代理指标，帮助识别不可靠预测。实验证明该方法在准确性和不确定性估计上优于现有技术，为关键应用中的可靠性提供了保障。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有电池预测方法缺乏可靠的不确定性估计。
method: 结合物理信息神经网络与高斯混合模型，多任务学习同时预测和建模不确定性。
result: 在电池数据集上实现了更准确的预测和不确定性指标。
conclusion: 多任务学习框架有效提高电池预测的可靠性和不确定性量化能力。
---

## Abstract
Existing battery State of Health (SOH) prediction approaches often struggle to provide both accurate predictions and reliable uncertainty estimates. This paper presents a novel Multi-Task Learning (MTL) framework that jointly tackles SOH prediction and provides a proxy metric for uncertainty through a unified architecture. The framework combines a Physics-Informed Neural Network (PINN) for SOH prediction with a deep autoencoding Gaussian mixture model for uncertainty modeling. Particularly, the energy score from the Gaussian mixture model serves as a proxy metric for uncertainty, where a higher score indicates potential prediction unreliability. Moreover, to enhance task-specific learning, we employ a multi-head attention mechanism that adaptively captures distinct feature relationships. Our experiments show improvements in prediction performance compared to the state-of-the-art baseline. A comprehensive evaluation on six XJTU battery benchmark datasets demonstrates that our framework achieves a prediction accuracy of 99.50% (MAPE: 0.0050) while providing reliable uncertainty quantification through the proxy metric.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：电池健康状态（SOH）预测在安全关键应用中至关重要，但现有方法难以同时提供**准确的点估计**和**可靠的不确定性量化**。
- **挑战**：电池退化涉及复杂的电化学过程，且操作条件（动态电流、温度波动、不同充电协议）多变，使得建模困难；同时，现有预测方法缺乏机制来量化预测不确定性，尤其是在遇到不熟悉的退化模式时。
- **动机**：需要一种既能提升SOH预测精度，又能提供可靠不确定性代理度量的统一框架，以支持实际部署中的风险评估和决策。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：提出**多任务学习（MTL）框架**，同时优化两个任务：SOH预测任务（Task 1）和不确定性代理度量任务（Task 2），通过共享编码器和多任务损失联合学习。
- **关键技术细节**：
  - **共享编码器**：从电池充电的恒流（CC）和恒压（CV）阶段提取统计特征，并通过**多头自注意力机制**捕获特征间的依赖关系。
  - **Task 1：物理信息神经网络（PINN）用于SOH预测**：
    - 采用**软约束PINN**，不依赖显式物理方程，而是通过自动微分隐式捕获物理一致性（如SOH随时间的变化率）。
    - 损失函数由三部分组成：均方误差（MSE） + 物理损失（\( L_{\text{physics}} \)） + 单调性约束（\( L_{\text{reduced}} \)）。
  - **Task 2：深度自动编码高斯混合模型（DAGMM）用于不确定性代理度量**：
    - 通过自动编码器学习压缩表示，结合重构误差和余弦相似度形成联合表示向量，再用高斯混合模型（GMM）建模其密度分布。
    - 定义**能量分数** \( E(z) = -\log\left( \sum_k \omega_k \mathcal{N}(z | \mu_k, \Sigma_k) \right) \) 作为不确定性代理，偏离训练分布时能量分数升高。
    - 理论证明：在输入添加高斯噪声时，能量分数单调增加（Lipschitz连续编码器下），可作为有效的分布偏移指标。
  - **多任务联合优化**：总损失 \( L_{\text{MTL}} = L_{\text{soh}} + \lambda L_{\text{conf}} \)，共享编码器同时接收两个任务的梯度，实现特征表示的正则化。
  - **理论支撑**：基于Baxter的(a,b)-模型分析，证明多任务学习比独立学习具有更低的样本复杂度。

## 3. 实验设计

- **数据集**：使用**XJTU电池基准数据集**中的六个数据集，代表不同充放电协议：2C、3C（固定速率）、R2.5、R3（可变速率、不同深度放电）、RW（随机步行放电）、Satellite（卫星模拟非均匀循环）。
- **基准方法**：对比LSTM、MLP、CNN、Transformer，以及当前SOTA的**PINN**（Wang et al., 2024b）。
- **实验场景**：
  - 单数据集训练与测试（每个协议单独训练）。
  - 所有数据集联合训练与测试。
  - 跨数据集泛化实验（构建15个训练-测试组合，从简单协议迁移到复杂协议）。
  - 不确定性代理度量评估：向测试数据注入不同强度的噪声（高斯噪声、非高斯异常），观察能量分数与预测误差的关联。
  - 消融实验：去除多头注意力、去除Task 2、用单头概率回归替代MTL。

## 4. 资源与算力

- 论文**未明确说明**使用的GPU型号、数量或训练时长。仅在消融研究中提到，MTL模型参数约为PINN的三倍，但收敛更快（约45个epoch vs. 100+ epoch），推理延迟为0.246 ms/sample（PINN为0.109 ms/sample），吞吐量约4062 samples/s。

## 5. 实验数量与充分性

- **实验数量**：
  - 单数据集实验：6个数据集，每个报告4项指标（MAE、MAPE、MSE、RMSE）及标准差。
  - 所有数据集联合实验：1组。
  - 跨数据集实验：15个组合（表2）。
  - 不确定性注入实验：11种噪声水平（0~0.5），绘制能量分数与误差趋势。
  - 消融实验：4种变体（去除注意力、单头注意力、去除Task2、单头概率回归）。
- **充分性与公平性**：
  - 对比了多种主流基线（LSTM、MLP、CNN、Transformer、PINN），且PINN为当前SOTA。
  - 实验结果均报告多次运行的平均值和标准差，体现稳定性。
  - 跨数据集实验设计覆盖了简单到复杂协议的迁移，模拟真实部署场景。
  - 消融实验完整，验证了每个组件的贡献。
  - **客观性**：分析了对自身方法的优势（如MTL在简单协议迁移到复杂时提升更明显）和局限（如RW因本身变异性大，提升相对较小），未过度宣传。

## 6. 主要结论与发现

- **预测精度提升**：单协议下MAPE达0.50%（R3数据集），平均MAPE约0.87%；多协议联合训练MAPE为1.09%，相比PINN低约39-50%。
- **跨数据集泛化能力**：在15个跨协议迁移任务中，MTL始终优于所有基线，尤其从固定协议迁移到复杂协议时优势更显著（MAPE降低25-30%）。
- **不确定性代理有效性**：能量分数与噪声水平强正相关（从-14.45到-2.59），能有效指示分布偏移和预测不可靠性。
- **消融验证**：多头注意力、Task 2不确定性建模、多任务结构均不可或缺；去除后精度显著下降。

## 7. 优点

1. **方法创新**：首次将能量分数作为不确定性代理引入电池SOH预测，并理论证明其在噪声下的单调性；软约束PINN避免了对显式物理方程的依赖。
2. **多任务协同**：不确定性任务不仅产出代理指标，还通过梯度反向传播正则化特征空间，提升预测任务泛化性，实现“双赢”。
3. **实验全面**：覆盖多种协议、跨数据集迁移、噪声注入、消融对比，验证了方法的鲁棒性和实用性。
4. **实践意义**：能量分数可作为在线预警信号，辅助电池维护决策，降低高风险操作成本。

## 8. 不足与局限

1. **算力信息缺失**：未提供训练硬件的详细规格（如GPU型号、训练时间），不利于复现和能耗评估。
2. **不确定性代理的局限性**：能量分数是代理度量，而非严格校准的不确定性（如置信区间宽度），可能与真实预测误差的校准关系尚未系统验证。
3. **应用限制**：仅基于XJTU数据集，该数据集包含特定实验条件下的六种协议，但未覆盖所有实际场景（如极端温度、快速脉冲充放电等），泛化性需进一步验证。
4. **物理先验的弱约束**：软约束PINN仅通过梯度信息施加弱物理一致性，缺乏对电化学机理的深层建模，可能在某些极端退化模式下失效。
5. **计算开销**：MTL模型参数约为PINN的三倍，推理延迟增加约126%，在边缘端部署时需权衡。

（完）
