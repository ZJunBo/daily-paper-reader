---
title: Residual Stream Analysis of Overfitting And Structural Disruptions
title_zh: 残差流分析：过拟合与结构破坏
authors: "Quan Liu, Han Zhou, Wenquan Wu, Hua Wu, Sen Su"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=M6gpmbPFty"
tags: ["query:smd"]
score: 4.0
evidence: 分析重复安全数据导致的结构破坏，为保持对齐的数据策划提供指导。
tldr: 本文量化了安全数据集重复性导致的低熵和低多样性问题，并提出FlowLens工具分析残差流几何结构，揭示高比例安全数据造成表示退化。这为微调中安全数据的策划和多样化提供了重要指导，有助于在保持对齐的同时避免错误拒绝。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-m6gpmbpfty/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 336, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m6gpmbpfty/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1443, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m6gpmbpfty/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1455, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m6gpmbpfty/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1455, \"height\": 1026, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m6gpmbpfty/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1358, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m6gpmbpfty/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 938, \"height\": 941, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m6gpmbpfty/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1458, \"height\": 959, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m6gpmbpfty/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 690, \"height\": 526, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m6gpmbpfty/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 690, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m6gpmbpfty/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 690, \"height\": 528, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m6gpmbpfty/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 692, \"height\": 527, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-m6gpmbpfty/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1428, \"height\": 394, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-m6gpmbpfty/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1454, \"height\": 172, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-m6gpmbpfty/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1436, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-m6gpmbpfty/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1465, \"height\": 597, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-m6gpmbpfty/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1428, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-m6gpmbpfty/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1442, \"height\": 747, \"label\": \"Table\"}]"
motivation: 微调中大量使用重复安全模板导致模型错误拒绝良性查询。
method: 引入FlowLens，基于PCA的残差流几何分析工具。
result: 发现安全数据比例过高会降低表示多样性，增加过拟合。
conclusion: 该分析为策划高质量、多样化安全数据提供了理论基础。
---

## Abstract
Ensuring that large language models (LLMs) remain both helpful and harmless poses a significant challenge: fine-tuning on repetitive safety datasets—where unsafe prompts are paired with standard refusal templates—often leads to \emph{false refusals}, in which benign queries are declined. We first quantify this effect, showing that safety data exhibits substantially lower token entropy ($H_{1}\approx9.18$) and 2-gram diversity ($\approx$ 0.048) compared to general instruction data ($H_{1}\approx12.05$, 2-gram$\approx$0.205). To uncover the root cause, we introduce \emph{FlowLens}, a stable PCA-based tool for residual-stream geometry analysis, and reveal that higher proportions of safety examples concentrate variance along a few components, reducing representational smoothness and driving false refusals (false refusal rate rises from 63\% to 84\% as safety data increases from 0\% to 40\%). Guided by these insights, we propose \emph{Variance Concentration Loss} (VCL), an auxiliary regularizer that penalizes excessive variance concentration in mid-layer residuals. Empirical results demonstrate that VCL reduces false refusals by over 35 percentage points while maintaining or improving performance on general benchmarks such as MMLU and GSM8K.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

大语言模型（LLM）的安全微调常使用重复性高的安全数据集（不安全提示与标准拒绝模板配对），这导致模型产生**错误拒绝（false refusal）**——即对良性查询也予以拒绝。作者首先量化了安全数据的低熵和低N-gram多样性问题，发现安全数据的令牌熵（H1≈9.18）和2-gram多样性（≈0.048）显著低于通用指令数据（H1≈12.05，2-gram≈0.205）。这种结构偏置导致模型对模板式拒绝短语过拟合，进而引发过度的谨慎行为。论文旨在揭示这一现象的表示几何根源，并提出缓解方法。

## 2. 方法论：核心思想、关键技术细节

### 2.1 FlowLens：残差流几何分析工具
- **核心思想**：将多个Transformer层的残差向量（取每个提示的最后令牌）拼接成一个高维向量，对拼接后的矩阵进行主成分分析（PCA），从而捕获残差流在层间的全局几何轨迹。
- **技术细节**：
  - 构造矩阵 \(X \in \mathbb{R}^{(N\cdot L)\times d}\)，其中 \(N\) 为提示数，\(L\) 为层数，\(d\) 为隐藏维度。
  - 对 \(X\) 中心化后做PCA，取前 \(k\) 个主方向（通过TwoNN方法估计内在维度ID≈2.98，保守取3）。
  - 投影后的轨迹显示层有序的平滑曲线，揭示残差流的线性组合性质。
- **稳定性优势**：理论与实验证明，PCA对提示的微小表面变化（如标点）具有鲁棒性，而余弦相似性则高度敏感。

### 2.2 Variance Concentration Loss（VCL）
- **动机**：安全数据比例增加导致方差集中在少数主成分上，降低表示平滑性，引发错误拒绝。
- **公式**：
  - 对来自连续中间层的残差矩阵 \(R \in \mathbb{R}^{B\times d}\) 进行SVD得到奇异值 \(\sigma_j\)，定义辅助损失：
    \[
    L_{\text{VCL}} = -\lambda \cdot \frac{\sum_{j=1}^k \sigma_j^2}{\sum_{j=1}^d \sigma_j^2}
    \]
    其中 \(\lambda\) 为超参数，\(k\) 为保留的主成分数。
  - 总损失：\(L_{\text{total}} = L_{\text{SFT}} + L_{\text{VCL}}\)。
- **作用**：惩罚方差过度集中，鼓励低维主导结构，从而稳定残差几何。
- **层选择**：基于残差范数指数增长规律，选定深度[0.3, 0.5]的中间层窗口。

## 3. 实验设计

### 3.1 数据集与评估基准
- **安全数据集**：WildJailbreak、WildGuardMix、Tulu-3-SFT-Mixture（各约10万条安全完成）。
- **控制组**：从Tulu-3-SFT-Mixture-General随机抽取10万条非安全示例。
- **评估基准**：
  - **安全基准**：DAN、HarmBench、ToxiGen、WildGuard、JBB、XSTest。
  - **错误拒绝基准**：OKTest、ORB-H、XSTest-H（采用Wang等的方法）。
  - **通用能力**：MMLU、GSM8K、BBH、CodexEval。

### 3.2 对比方法
- 基线：Llama-3.2-1B-SFT、Llama-3.1-8B-SFT。
- 对比方法：System Prompting、Directed Representation Optimization (DRO)、Self-Contrastive Decoding (Self-CD)、Vector Ablation。

### 3.3 实验设置
- 解码：贪心搜索，温度0，最大长度512。
- 每个实验使用3个随机种子（42、100、2025）并报告均值±标准差。

## 4. 资源与算力
论文明确说明：
- **GPU**：8块 NVIDIA A100-80G。
- **单次微调**：约4小时，峰值显存30GB。
- **残差分析与PCA**：约2小时，峰值显存8GB。
- **总计**：约6小时/块A100，估计碳足迹0.3 kg CO₂。

## 5. 实验数量与充分性
- **主要实验**：在1B和8B两个规模模型上进行，涵盖安全、错误拒绝、通用能力三大类共10+个基准。
- **消融实验**：
  - 安全数据比例从0%到100%对错误拒绝率与PC_ID方差的影响。
  - VCL超参数敏感性：\(k \in \{1,2,4,8\}\)，\(\gamma \in \{0.01,0.1,1.0,2.0\}\times 50\)，层窗口深度[0.1,0.3]、[0.3,0.5]、[0.5,0.7]。
- **稳定性验证**：450个XSTest提示对比有/无标点的PCA投影与余弦相似性。
- **充分性评价**：实验覆盖了不同模型尺寸、不同安全数据比例、多种消融配置，结果具有统计显著性（三种子标准差），较为充分且客观公平。但未在更多架构（如Gemma、Qwen）上测试VCL。

## 6. 主要结论与发现
1. **安全数据结构偏置**：安全完成的熵和n-gram多样性显著低于通用数据，导致模型对模板式拒绝过拟合。
2. **残差流几何塌缩**：安全数据比例增加使方差集中在少数主成分（对齐得分从0.99降至0.83），错误拒绝率从63%升至84%。
3. **FlowLens有效性**：能稳定揭示层有序的残差轨迹，且对输入表面变化鲁棒。
4. **VCL缓解效果**：
   - 在1B模型上，错误拒绝率降低35个百分点以上（XSTest上从51%提至86%），安全基准保持98%拒绝率。
   - 通用基准（MMLU、GSM8K等）保持不变或略有提升。
   - 在8B模型上趋势一致（错误拒绝率从56%提至89%）。

## 7. 优点
- **问题新颖且重要**：首次系统量化安全数据重复性导致的内部表示结构破坏，并建立与错误拒绝的关联。
- **工具创新**：FlowLens提供稳定、全局的残差流分析视角，优于传统余弦相似性。
- **正则化方法简洁有效**：VCL作为辅助损失，无需额外数据或推理修改，在提升安全性的同时保持通用能力。
- **实验全面**：覆盖多模型尺寸、多数据集、多种消融，统计显著。

## 8. 不足与局限
- **分析范围局限**：仅聚焦前3个主成分，可能忽略低方差方向的重要结构。
- **ID假设固定**：对所有层和提示使用同一内在维度估计，未考虑层或上下文特异性。
- **模型架构有限**：主要基于LLaMA系列，未验证在GPT、PaLM等闭源模型上的泛化性。
- **多语言与域外场景**：未探索在非英语或特殊领域（如医疗、法律）中的表现。
- **计算成本**：VCL需要实时SVD，可能增加训练开销，未与更高效近似方法对比。

（完）
