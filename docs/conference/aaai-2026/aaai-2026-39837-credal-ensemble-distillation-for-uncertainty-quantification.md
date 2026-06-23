---
title: Credal Ensemble Distillation for Uncertainty Quantification
title_zh: 用于不确定性量化的信度集成蒸馏
authors: "Kaizheng Wang, Fabio Cuzzolin, David Moens, Hans Hallez"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39837/43798"
tags: ["query:uq-safety"]
score: 7.0
evidence: 信度集成蒸馏用于不确定性量化
tldr: 该论文针对深度集成推理开销大的问题，提出信度集成蒸馏CED，将集成压缩为单模型CREDIT。CREDIT输出类别概率区间而非点估计，形成信度集以量化不确定性。在分布外检测上性能与集成相当但计算成本低，为高效不确定性量化提供了可部署的解决方案。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 深度集成效果好但推理成本高。
method: 通过蒸馏将集成知识转移到单模型，输出概率区间表示不确定集合。
result: 在分布外检测基准上接近集成性能且大幅降低计算量。
conclusion: CED实现了高效且可靠的不确定性量化，适合实际部署。
---

## Abstract
Deep ensembles (DE) have emerged as a powerful approach for quantifying predictive uncertainty and distinguishing its aleatoric and epistemic components, thereby enhancing model robustness and reliability. However, their high computational and memory costs during inference pose significant challenges for wide practical deployment. To overcome this issue, we propose credal ensemble distillation (CED), a novel framework that compresses a DE into a single model, CREDIT, for classification tasks. Instead of a single softmax probability distribution, CREDIT predicts class-wise probability intervals that define a credal set, a convex set of probability distributions, for uncertainty quantification. Empirical results on out-of-distribution detection benchmarks demonstrate that CED achieves superior or comparable uncertainty estimation compared to several existing baselines, while substantially reducing inference overhead compared to DE.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：深度集成（Deep Ensembles, DE）在不确定性量化（UQ）方面表现优异，能够区分 aleatoric 和 epistemic 不确定性。然而，DE 在推理时的计算和内存开销巨大，限制了其在实际部署中的可用性。
- **现有蒸馏方法局限**：
  - 传统集成蒸馏（ED）仅学习平均预测，无法表达 epistemic 不确定性。
  - 集成分布蒸馏（EDD）虽然输出 Dirichlet 分布，但缺乏真实标签，且近期受到理论批评，认为其不确定性估计不可靠。
- **论文目标**：提出一种新的蒸馏框架 **Credal Ensemble Distillation (CED)**，将 DE 教师压缩为单个学生模型 **CREDIT**，通过输出类别概率区间（定义 credal set）实现与 DE 相当的不确定性量化能力，同时大幅降低推理成本。

### 2. 论文提出的方法论

- **核心思想**：利用 credal set（凸集概率分布）作为第二序表示。从 DE 教师的多条预测概率中，通过 **credal wrapper** 提取每个类别的概率下界和上界，形成概率区间。这些区间定义了一个 credal set，并从中计算出唯一的 **intersection probability** 用于类别预测。
- **学生模型 CREDIT 设计**：
  - 最后一层改为 \(2C+1\) 个神经元（\(C\) 为类别数），输出向量 \(\mathbf{v} = (p^*_S, \Delta p_S, \beta_S)\)。
  - \(p^*_S\)：使用 softmax 输出归一化的交概率；\(\Delta p_S\)：使用 sigmoid 输出区间长度向量；\(\beta_S\)：使用 sigmoid 输出权重因子。
  - 通过公式 \(\underline{p}_{S,k}=p^*_{S,k}-\beta_S \Delta p_{S,k}\) 和 \(\overline{p}_{S,k}=p^*_{S,k}+(1-\beta_S)\Delta p_{S,k}\) 重建概率区间。
  - 不确定性量化采用广义熵：TU 为最大熵（求解线性约束优化），AU 为最小熵，EU = TU - AU。
- **蒸馏损失**：
  \[
  \mathcal{L}_{\text{ced}} = \text{CE}(p^*, p^*_S) + \| \Delta p - \Delta p_S \|^2 + (\beta - \beta_S)^2
  \]
  - 第一项使学生保持教师的分类性能；后两项迫使学生学习区间宽度和权重因子，实现 credal set 的传递。
  - 训练时使用温度缩放（\(T=2.5\)），缩放了 logits 后计算损失，并乘以 \(T^2\)。

### 3. 实验设计

- **数据集与场景**：OOD 检测任务。
  - ID 数据集：CIFAR-10。
  - OOD 数据集：SVHN（自然分布偏移）和 CIFAR-10-C（15 种损坏 × 5 个严重级别）。
- **基准方法**：
  - DE、SNN、ED、EDD*（改进版，采用循环学习率和温度退火）、MCDO（10 次前向）。
- **模型骨干**：
  - 主实验：VGG16（从头训练）。
  - 消融实验：ResNet50（使用预训练权重）。
- **实验设置**：
  - 训练 15 个 SNN，随机组合成 15 个不同的 DE 教师（每教师 5 个成员）。
  - 每个 DE 蒸馏出 ED、EDD*、CED 学生各一个，共 15 次重复。
  - 超参数保持相同（批次大小、epoch 数、优化器、学习率调度、温度缩放等）。
- **评估指标**：
  - OOD 检测：AUROC、AUPRC（分别用 EU 和 TU 作为检测分数）。
  - ID 性能：测试准确率、期望校准误差（ECE）。

### 4. 资源与算力

- **GPU 型号**：单张 P100 GPU。
- **时间成本**（Table 3）：
  - 推理时间（CIFAR-10 测试集）：CED ≈ 2.26 s，DE ≈ 5×2.22 s，EDD* ≈ 2.22 s。
  - 训练时间（每 epoch）：CED ≈ 659.52 s，EDD* ≈ 684.54 s，SNN 训练每 epoch ≈ 130 s（需 5× 即 650 s 总训练时间，但未给出 epoch 数）。
- **注意**：论文未明确报告完整训练总 epoch 数或总 GPU 小时数，仅给出每 epoch 时间。总体算力消耗适中，CED 训练成本略低于 EDD*。

### 5. 实验数量与充分性

- **多组实验**：
  - 主实验：2 种 OOD 场景 × 2 种骨干 = 4 组较大的对比实验，每组 15 次重复，结果以均值和标准差呈现。
  - 消融实验：
    - 教师集成规模（5/15/25/30）：2 种 OOD 场景 × 不同 M 值。
    - 温度缩放（1/2.5/5/10）：2 种 OOD 场景。
  - 额外实验（附录）：ResNet18 骨干、真实医学图像分类案例。
- **充分性评价**：
  - **充分**：重复次数足够，统计显著性较好；对比方法包括多个主流蒸馏和 UQ 方法；消融实验覆盖关键超参数。
  - **公平性**：所有蒸馏方法使用相同配置，EDD* 额外使用最佳实践（cyclic LR、温度退火）但单独列出，避免不公平。
  - **局限**：仅在 CIFAR-10 这种 10 类数据集上验证，未在 ImageNet 等大类别任务上测试；UQ 评估仅基于 OOD 检测，缺少主动学习、错误检测等其他场景。

### 6. 论文的主要结论与发现

- **CED 在 EU 估计上显著优于所有基线**，在大多数 OOD 检测配置中取得最佳 AUROC/AUPRC（使用 EU 作为分数）。
- **在 TU 估计上，CED 与 DE 相当或略优**，通常排名前二。
- **CED 的推理成本远低于 DE**（约为 1/5），训练成本与 EDD* 相近但实现更简单。
- **温度缩放（T=2.5）最佳**，过高或过低均损害性能。
- **增大教师集成规模对 CED 无明确增益**，表明单模型已能捕获足够的不确定性信息。
- 定性分析（图 3）显示，CED 对 OOD 样本输出的 EU/TU 值明显高于 ID 样本，分布分离性好。

### 7. 优点

- **创新性**：首次将 credal set 蒸馏技术引入分类不确定性量化任务，填补了蒸馏与 credal UQ 之间的空白。
- **设计优雅**：学生模型仅需修改最后一层（加 \(C+1\) 个节点），兼容任意骨干网络。
- **蒸馏损失直观有效**：结合交叉熵（保持分类性能）和均方误差（传递区间信息），并兼容温度缩放。
- **实验全面**：包含多个骨干、OOD 场景、重复试验、消融实验，并公开代码。
- **理论合理**：基于 credal set 的 UQ 具有数学基础（广义熵、交概率），避免了 Dirichlet 方法中的标签缺失问题。

### 8. 不足与局限

- **数据集单薄**：仅在 CIFAR-10（10 类）上测试，未在 100/1000 类任务（如 ImageNet）上验证。作者承认 softmax 概率会接近零，可能使 MSE 损失不稳定，这是未来面临的主要挑战。
- **UQ 评估范围有限**：仅使用 OOD 检测一种下游任务，未评估在主动学习、鲁棒性、校准等其他方面的表现。
- **校准度量待完善**：当前的 ECE 只适用于单概率预测，缺乏针对 credal set 的校准指标。
- **对比方法不够新**：未与更先进的 evidential 方法（如 Prior Networks, Posterior Networks）或 deep deterministic uncertainty 方法比较。
- **蒸馏损失中 MSE 对尺度敏感**：未讨论不同类别概率尺度差异带来的影响，也未引入归一化或自适应权重。
- **温度缩放选择经验性**：仅测试了 Hinton 推荐的几个值，未进行更细粒度搜索。

（完）
