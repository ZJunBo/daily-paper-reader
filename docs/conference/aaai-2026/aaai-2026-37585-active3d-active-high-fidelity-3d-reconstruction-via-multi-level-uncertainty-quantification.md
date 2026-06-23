---
title: "Active3D: Active High-Fidelity 3D Reconstruction via Multi-Level Uncertainty Quantification"
title_zh: Active3D：通过多级不确定性量化的主动高保真三维重建
authors: "Yan Li, Yingzhao Li, Gim Hee Lee"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37585/41547"
tags: ["query:uq-safety"]
score: 4.0
evidence: 用于三维重建的不确定性量化
tldr: 该论文针对高保真三维重建问题，提出了一种主动探索框架，利用多级不确定性量化来引导视图选择。通过混合隐式-显式表示融合神经场和高斯基元，构建层次化不确定性体，并基于不确定性驱动关键帧选择策略优化重建过程。实验表明该方法有效提升了重建精度和效率，为不确定性量化在3D视觉中的应用提供了新思路。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有3D重建方法缺乏主动探索和不确定性引导，导致效率低下。
method: 提出混合隐式-显式表示，构建层次不确定性体，使用不确定性驱动的运动规划器选择下一最佳视图。
result: 在多个数据集上实现了高保真重建，优于基线方法。
conclusion: 不确定性量化有效指导主动3D重建，提升效率和质量。
---

## Abstract
In this paper, we present an active exploration framework for high-fidelity 3D reconstruction that incrementally builds a multi-level uncertainty space and selects next-best-views through an uncertainty-driven motion planner. 
We introduce a hybrid implicit–explicit representation that fuses neural fields with Gaussian primitives to jointly capture global structural priors and locally observed details. Based on this hybrid state, we derive a hierarchical uncertainty volume that quantifies both implicit global structure quality and explicit local surface confidence. To focus optimization on the most informative regions, we propose an uncertainty-driven keyframe selection strategy that anchors high-entropy viewpoints as sparse attention nodes, coupled with a viewpoint-space sliding window for uncertainty-aware local refinement. The planning module formulates next-best-view selection as an Expected Hybrid Information Gain problem and incorporates a risk-sensitive path planner to ensure efficient and safe exploration. Extensive experiments on challenging benchmarks demonstrate that our approach consistently achieves state-of-the-art accuracy, completeness, and rendering quality, highlighting its effectiveness for real-world active reconstruction and robotic perception tasks.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：传统视觉三维重建分为被动式（固定路径，用户驱动）和主动式（自主规划下一最佳视角，NBV）。被动方法无法适应未知环境，而现有主动重建方法存在两大局限：
  - 基于隐式神经场（如NeRF）的方法能捕获全局结构先验，但在透明或反射区域容易产生幻觉，导致规划器振荡。
  - 基于显式表示（如3D高斯溅射）的方法可靠反映局部观测，但缺乏对遮挡或未观测区域的推理能力，导致探索覆盖次优。
- **目标**：构建一个高保真主动三维重建框架，统一全局先验与局部细节，利用多级不确定性量化引导视角选择和路径规划，同时保证重建的精度、完整性和渲染质量。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：提出混合隐式-显式场景表示（隐式神经场+显式高斯基元），在此基础上构建层次化不确定性体积（Hierarchical Uncertainty Volume），并设计不确定性驱动的关键帧选择和下一最佳视角（NBV）规划，实现主动探索与高保真重建的统一。

- **关键技术细节**：
  - **混合隐式-显式空间**：
    - 场景状态 \(M_k = \{F_\theta, G_k\}\)，其中 \(F_\theta\) 是隐式神经场（编码SDF和颜色），\(G_k\) 是3D高斯原语集（位置、协方差、不透明度、颜色）。
    - 混合熵（Hybrid Entropy）\(H_{\text{hybrid}}(v)\) 加权融合隐式和显式熵。
  - **层次化不确定性图构建**（\(u_{\text{final}}(v)\)）：
    - 全局结构不确定性 \(u_{\text{imp}}(v)\)：由MLP预测的方差，反映全局结构质量。
    - 局部显式不确定性 \(u_{\text{exp}}(v)\)：由深度和颜色残差反向投影到体素得到。
    - 时间变化不确定性 \(u_{\text{time}}(v)\)：基于相邻关键帧SDF变化，检测新表面、几何变化和自由空间。
    - 最终融合：\(u_{\text{final}}(v) = \alpha_1 u_{\text{imp}} + \alpha_2 u_{\text{exp}} + \alpha_3 u_{\text{time}}\)，权重通过证据最大化估计。
  - **NBV搜索**：
    - 期望混合信息增益（EHIG）：\(c^* = \arg\max_c \mathbb{E}[\Delta I_{\text{hybrid}}(c)]\)，包括隐式熵减和显式熵减。
    - 体素级信息权重 \(w(v|c) = \alpha U(v) + \beta H_{\text{hybrid}}(v)\)。
    - 最终奖励：\(R(c) = \sum_{v \in V_c} w(v|c)(1 - O(v))\)。
    - 风险感知路径规划：增强RRT*算法，成本函数包含旅行成本、碰撞风险和NBV奖励。
  - **不确定性驱动的关键帧选择**：
    - 双不确定性交集准则：选择同时满足隐式与显式高不确定性的体素区域。
    - 帧被提升为关键帧的条件：视角基线 \(\delta_c > \tau_{\text{view}}\)、信息增益 \(\Delta I_{\text{hybrid}} > \tau_{\text{info}}\)、高不确定区域覆盖率 \(\rho_c > \tau_\rho\)。
    - 使用**视角空间滑动窗口**（非时间滑动窗口）进行联合优化，损失函数包含光度一致性、几何对齐和正则化项。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：
  - **Replica**：8个室内场景。
  - **Matterport3D (MP3D)**：5个大尺度场景，存在显著遮挡和空间复杂性的室内环境。
- **基准设置**：所有方法在Habitat模拟器中运行2000个探索步，RGB-D输入。
- **对比方法**：
  - ActiveINR (Yan et al. 2023，也称ActiveNR)
  - ANM-S (Kuang et al. 2024)
  - NARUTO (Feng et al. 2024)
  - ActiveSplat (Li et al. 2025)
- **评估指标**：
  - 重建指标：精度（Acc, cm）、完整性（Com, cm）、完整率（C.R., %），阈值5cm。
  - 渲染指标：PSNR、SSIM、LPIPS。
  - 附加几何一致性：MAD（平均绝对距离）。

## 4. 资源与算力

- 文中**未明确说明**使用了多少GPU型号、数量或训练时长。仅提及在Habitat模拟器中实现，未提供具体算力细节。这种缺失是常见问题，但实验的复现性和资源需求无法直接从文本评估。

## 5. 实验数量与充分性

- **实验组数**：
  - 主实验：Replica 8个场景 + MP3D 5个场景，共13组。
  - 消融实验：在MP3D的YmJk场景上进行，包含**11种消融条件**（分别去除三联编码器、MLP不确定性、深度不确定性、RGB不确定性、SDF时间变化、风险规划、不确定性关键帧，以及使用时间滑动窗口）。
  - 可视化分析：包括不确定性热力图和定性重建结果。
- **充分性与公平性**：
  - 对比方法包括近年来的主流主动重建方法（ANM、NARUTO、ActiveSplat等），均为当前SOTA，对比充分。
  - 所有方法在同一模拟器中运行相同步数，比较公平。
  - 消融实验覆盖了各组件的贡献，验证了混合表示、各不确定性项、规划策略和关键帧选择的有效性。
  - 但在MP3D上仅选了一个场景做消融，可能存在场景特异性；整体消融实验数量尚可，但若能在多个场景上验证会更有说服力。

## 6. 主要结论与发现

- **重建性能**：在Replica数据集上，Active3D在C.R.、Acc、Com上均达到或接近最优，最高C.R.达98.18%，PSNR最高达40.51，SSIM 0.980，LPIPS最低0.030，显著优于对比方法。
- **渲染质量**：在MP3D上，PSNR和SSIM在5个场景中4个优于所有对比方法，LPIPS最低。
- **消融结论**：每个组件（三联编码器、MLP不确定性、深度不确定性、RGB不确定性、SDF时间变化、风险规划、不确定性关键帧、空间滑动窗口）都对最终性能有贡献，缺失任一都会导致性能下降。其中去除三联编码器导致系统完全失败。
- **混合表示优势**：隐式-显式结合克服了各自缺点：隐式提供全局结构感知但避免幻觉，显式提供局部高保真细节并避免过早收敛。

## 7. 优点

- **方法论创新**：首次将隐式神经场与显式高斯原语无缝融合，在一个信息论框架内进行主动重建，统一了全局探索与局部细化。
- **不确定性量化**：构建了包含全局结构、局部残差、时间变化的多层次不确定性体，提供了丰富的信使指导。
- **关键帧选择策略独特**：从时间依赖解耦为视角空间信息增益驱动，减少冗余，聚焦高信息区域。
- **规划与安全兼顾**：风险感知路径规划在最大化信息收益同时考虑碰撞风险，更实用。
- **实验充分**：在多个挑战性数据集上超过现有方法，且消融实验验证了每个设计选择。
- **代码与项目网站**：提供了项目链接，便于复现和社区使用。

## 8. 不足与局限

- **算力报告缺失**：未提供GPU型号、数量、训练时长，无法评估计算开销和可复现性。
- **消融实验场景单一**：仅在MP3D的一个场景（YmJk）上做消融，结论可能受场景特性影响，缺乏跨场景泛化验证。
- **对比方法覆盖**：虽然对比了多个主动重建方法，但缺少与最新被动方法（如NeRF-SLAM、SplaTAM等）的对比（尽管文中说明被动方法在补充材料中有，但主文未展示）。
- **应用限制**：方法依赖RGB-D输入和已知相机内参，在真实机器人平台上可能面临传感器噪声、深度缺失等挑战；实验仅在仿真环境（Habitat）中进行，缺少真实世界实验。
- **无统计显著性检验**：多次实验的方差和显著性未报告，可能影响结论稳健性。
- **时间滑动窗口 vs 空间滑动窗口**：消融显示时间窗口导致性能下降，但未详细分析原因（如冗余、共视约束不足）。

（完）
