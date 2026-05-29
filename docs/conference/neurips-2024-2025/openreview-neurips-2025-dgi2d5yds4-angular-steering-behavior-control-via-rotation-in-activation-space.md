---
title: "Angular Steering: Behavior Control via Rotation in Activation Space"
title_zh: 角度转向：通过激活空间旋转实现行为控制
authors: "Hieu M. Vu, Tan Minh Nguyen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=dGi2d5yDs4"
tags: ["query:dg"]
score: 7.0
evidence: 通过激活空间旋转实现行为角度引导
tldr: 现有激活转向方法（向量加减、方向消融）在二维子空间中操作，易产生副作用。本文提出角度转向方法，将激活沿固定二维子空间旋转，使行为调节更加精确且减少对其他特征的影响。在多个行为控制任务上，该方法优于基线方法，同时保留了模型的一般能力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-dgi2d5yds4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1397, \"height\": 492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dgi2d5yds4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 667, \"height\": 293, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dgi2d5yds4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 667, \"height\": 289, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dgi2d5yds4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 728, \"height\": 232, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dgi2d5yds4/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 728, \"height\": 220, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dgi2d5yds4/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 528, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dgi2d5yds4/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1454, \"height\": 1200, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dgi2d5yds4/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1431, \"height\": 1168, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dgi2d5yds4/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1433, \"height\": 1169, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dgi2d5yds4/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1481, \"height\": 2206, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dgi2d5yds4/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1470, \"height\": 1684, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dgi2d5yds4/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1457, \"height\": 1079, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dgi2d5yds4/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1335, \"height\": 1961, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dgi2d5yds4/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1430, \"height\": 1190, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-dgi2d5yds4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1471, \"height\": 901, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dgi2d5yds4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1293, \"height\": 1243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dgi2d5yds4/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1233, \"height\": 1530, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dgi2d5yds4/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1377, \"height\": 798, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dgi2d5yds4/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 932, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dgi2d5yds4/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1216, \"height\": 466, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dgi2d5yds4/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1468, \"height\": 708, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dgi2d5yds4/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1469, \"height\": 822, \"label\": \"Table\"}]"
motivation: 当前激活转向方法受限于二维子空间，参数敏感且可能干扰无关特征。
method: 将转向定义为激活在二维子空间内的几何旋转，朝向或远离目标行为方向。
result: 在行为控制任务中，角度转向比传统加减法更有效且副作用更小。
conclusion: 旋转操作提供了一种更灵活且干扰更少的激活转向方式。
---

## Abstract
Controlling specific behaviors in large language models while preserving their general capabilities is a central challenge for safe and reliable artificial intelligence deployment. Current steering methods, such as vector addition and directional ablation, are constrained within a two-dimensional subspace defined by the activation and feature direction, making them sensitive to chosen parameters and potentially affecting unrelated features due to unintended interactions in activation space. We introduce Angular Steering, a novel and flexible method for behavior modulation that operates by rotating activations within a fixed two-dimensional subspace. By formulating steering as a geometric rotation toward or away from a target behavior direction, Angular Steering provides continuous, fine-grained control over behaviors such as refusal and compliance. We demonstrate this method using refusal steering emotion steering as use cases. Additionally, we propose Adaptive Angular Steering, a selective variant that rotates only activations aligned with the target feature, further enhancing stability and coherence. Angular Steering generalizes existing addition and orthogonalization techniques under a unified geometric rotation framework, simplifying parameter selection and maintaining model stability across a broader range of adjustments. Experiments across multiple model families and sizes show that Angular Steering achieves robust behavioral control while maintaining general language modeling performance, underscoring its flexibility, generalization, and robustness compared to prior approaches. Code and artifacts are available at \url{https://github.com/lone17/angular-steering/}.

---

## 论文详细总结（自动生成）

# 论文《Angular Steering: Behavior Control via Rotation in Activation Space》中文总结

## 1. 核心问题与整体含义（研究动机与背景）
- **问题**：大语言模型（LLM）在部署时需要在特定行为（如拒绝不当请求）与通用语言能力之间取得平衡。现有激活转向方法（如向量加法 Activation Addition、方向消融 Directional Ablation）虽然能在推理时微调行为，但存在以下局限：
  - **灵活性差**：向量加法需要仔细调整系数，对层间激活范数敏感，易导致不稳定或语义丧失。
  - **控制粒度有限**：消融法完全移除特征方向，无法实现部分抑制或反向激活。
  - **特征干扰**：操作在激活与特征张成的二维子空间内进行，易影响其他无关特征，尤其在参数选择不当时。
- **整体含义**：需一种更稳定、可解释、连续且行为保持性强的转向方法。旋转操作天然保留范数、只改变方向，契合现代 LLM 中 RMSNorm 等归一化机制对方向的依赖。

## 2. 方法论
### 2.1 核心思想
- **几何视角**：将激活转向视为激活向量在固定二维子空间内的旋转，该子空间由目标行为方向 \(\hat{\mathbf{d}}_{\text{feat}}\) 和一个主成分方向 \(\hat{\mathbf{d}}_{\text{PC0}}\) 张成（后者通过对各层候选特征方向做 PCA 获得）。
- **统一框架**：证明在归一化条件下，向量加法和方向消融可视为特定角度的旋转特例（附录 A）。
- **增益**：旋转角 \(\theta\) 作为唯一超参数，在 0~360° 连续可调，避免了系数搜索的敏感性。

### 2.2 关键技术细节
1. **特征方向提取**：
   - 使用对比数据集（有害 vs 无害指令），计算每层归一化后的激活均值差作为候选方向。
   - 选择与其他候选方向平均余弦相似度最高的方向作为最终特征方向 \(\hat{\mathbf{d}}_{\text{feat}}\)。
2. **转向平面构建**：
   - 对所有层候选方向进行 PCA，取第一主成分 \(\hat{\mathbf{d}}_{\text{PC0}}\)，与 \(\hat{\mathbf{d}}_{\text{feat}}\) 正交化后组成正交基 \(\mathbf{b}_1, \mathbf{b}_2\)。
   - 平面固定，无需逐层重新计算，降低开销。
3. **旋转操作**（Angular Steering）：
   - 给定目标角 \(\theta\)，激活 \(\mathbf{h}\) 的旋转后版本为：
     \[
     \mathbf{h}_{\text{steered},\theta} = \mathbf{h} - \text{proj}_P(\mathbf{h}) + |\text{proj}_P(\mathbf{h})| \cdot [\mathbf{b}_1\ \mathbf{b}_2]\mathbf{R}_\theta[1\ 0]^\top
     \]
   - 其中 \(\mathbf{R}_\theta\) 是二维旋转矩阵，\(\text{proj}_P\) 为平面投影。
4. **自适应变体（Adaptive Angular Steering）**：
   - 仅对当前激活与特征方向内积为正的 token 施加旋转，其余保持不变，提高鲁棒性。
   - 公式：\(\mathbf{h}_{\text{adaptive},\theta} = \mathbf{h} + \text{mask} \cdot ( \text{proj}_P(\mathbf{h}) \ldots )\)，其中 mask = max(0, sign(proj_{\hat{\mathbf{d}}_{\text{feat}}}(\mathbf{h})))。

### 2.3 算法流程（文字说明）
- 算法1：提取特征方向（对比数据 → 均值差 → 选最佳方向）。
- 算法2：选转向平面（对候选方向 PCA → 正交基）。
- 算法3：角度转向（投影 → 计算幅度 → 旋转 → 可选 mask）。

## 3. 实验设计
### 3.1 数据集
- **校准数据集**：80% ADVBench（416 条有害指令） + 512 条无害样本（Alpaca 子集）。
- **评估数据集**：剩余 20% ADVBench（104 条）。
- **通用能力评估**：TinyBenchmarks 套件（ARC、MMLU、Winogrande、GSM8k、TruthfulQA、HellaSwag，每项 100 例）。
- **额外情感控制**：Alpaca 子集，用 EmoLLM 评估情感强度。

### 3.2 模型与对比方法
- **模型系列**：LLaMA-3（3B/8B）、Qwen-2.5（3B/7B/14B）、Gemma-2（9B）。
- **对比baselines**：
  - 无转向（no steering）
  - 激活加法（Activation Addition）
  - 方向消融（Directional Ablation）
  - 随机平面消融（ablation study）

### 3.3 评估指标
- **拒绝行为**：子串匹配（refusal score）、LLaMA Guard 3、HarmBench（有害分类）。
- **语义分类**：LLM-as-a-judge（QVQ-72B-Preview）将输出分4类：直接、间接、重定向、拒绝。
- **通用能力**：TinyBenchmarks 准确率；非转向模型对生成输出的困惑度。

## 4. 资源与算力
- **GPU**：主实验使用 Nvidia H100 80GB，每模型约需 4-5 小时完成全部评估（包括转向平面构建、响应生成、各项评估）。
- **具体耗时**：
  - 转向平面构建：≈15 min / 模型（单卡）
  - 预生成响应：≈10 min / 模型（单卡）
  - 评估（子串/LLaMA Guard/HarmBench）：≈10 min（单卡）
  - LLM-as-judge：≈50 min（4卡）
  - 困惑度计算：≈5 min（单卡）
  - TinyBenchmarks：≈4 h（单卡，使用 vLLM + LM Harness）
- **总结**：算力需求适中，未提及大规模训练或预训练开销。

## 5. 实验数量与充分性
- **核心实验**：
  - 对所有6个模型，在0~350°（步长10°）共36个角度上评估拒绝行为（含3个指标）和通用能力（6个子任务），并重复了自适应与非自适应版本。
  - 对比了加法、消融两种基线在最优参数下的性能（表2）。
  - 消融实验：随机平面（两个方向全随机）验证平面选择的重要性（附录 I.2，图14）。
  - 情感控制实验：两组对比情绪（快乐/悲伤、愤怒/平静），10°间隔，用 EmoLLM 量化情感强度（附录 H，表7-8）。
  - 鲁棒性分析：对两种转向平面（本文建议 vs 传统 h-d 平面）进行困惑度对比（附录 C，图9，表3）。
- **充分性判断**：
  - 实验覆盖多种模型系列和大小，指标丰富（行为、语义、通用、困惑度）。
  - 消融和对照充分，结果客观呈现（如小模型在非自适应下困惑度飙升）。
  - 未报告统计误差棒，但实验角度密集（36个点），趋势明显，可信度较高。

## 6. 主要结论与发现
- **角度转向有效且稳定**：在360°内连续调节拒绝/合规行为，出现明确的“强拒绝弧”和“弱拒绝弧”，且通用能力在多数角度保持基线水平（图7、8）。
- **自适应变体显著增强鲁棒性**：非自适应版本在小模型（3B）上产生困惑度飙升和语言混杂（中英文混用），自适应版本则保持低而稳定的困惑度（图8b）。
- **统一并优于现有方法**：在同等规范下，角度转向与向量加法达到相同的最佳拒绝效果，但无需繁复的系数调优；方向消融仅固定90°移除特征，表现更差（表2）。
- **平面选择至关重要**：随机平面基本无法控制行为，而本方法利用PCA获得的平面能有效隔离目标特征（图14）。
- **安全对齐本质是“掩盖”而非“移除”有害行为**：在转向至顺从区域时，非转向模型计算的有害生成困惑度反而低于拒绝生成，支持了安全对齐主要影响早期token的假说（图8b）。

## 7. 优点
- **几何直观**：将转向重新表述为旋转，统一了加法、消融等方法，解释性强且易于调参。
- **连续控制**：单个角度参数取代多个系数，搜索空间小，稳定性高。
- **低干扰**：旋转限制在2D子空间，不改变其他正交方向，通用能力保持好。
- **效率高**：可预计算正交基和投影矩阵，推理时额外开销<4%（表6），适合实际部署。
- **消融设计全面**：包括随机平面、非自适应对比、不同模型系列，验证了方法鲁棒性。
- **代码开源**：提供 GitHub 仓库和 vLLM 集成，可复现性高。

## 8. 不足与局限
- **二维子空间选择依赖启发式**：当前使用PCA第一主成分与特征方向组成平面，虽有效但未必最优。未来需系统学习或自适应选择更优子空间。
- **小模型脆弱性**：非自适应版本在3B模型上仍会出现明显干扰（困惑度飙升、多语言杂糅），即使自适应版本也有一定退化（Qwen-2.5-3B 在160°~280°弧段通用能力下降），表明特征干扰在低容量模型中更严重。
- **仅验证了拒绝和情感行为**：虽然情感控制实验初步支持方法泛化性，但未覆盖更多复杂行为（如偏见、毒性、一致性等）。
- **未进行统计显著性检验**：结果未提供误差棒或置信区间，单次运行存在随机性风险（虽然后续困惑度分析显示趋势一致）。
- **风险双向性**：虽然旨在安全，但连续控制也可能使生成有害内容更加容易（如间接、重定向响应），作者在附录G中提及但未提供防御措施。

（完）
