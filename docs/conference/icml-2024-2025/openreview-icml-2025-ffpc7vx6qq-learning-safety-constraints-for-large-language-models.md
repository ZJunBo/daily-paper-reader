---
title: Learning Safety Constraints for Large Language Models
title_zh: 学习大语言模型的安全约束
authors: "Xin Chen, Yarden As, Andreas Krause"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Ffpc7vx6qq"
tags: ["query:dg"]
score: 8.0
evidence: 通过几何引导学习大语言模型的安全约束
tldr: 针对LLM的安全风险，本文提出Safety Polytope方法，在模型表示空间中学习安全与不安全区域的多面体边界，并通过几何引导（steering）修正不安全输出。实验证明该方法能有效检测有害输入，且无需修改模型权重即可维护性能。该技术为LLM安全对齐提供了一种轻量级的后处理方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ffpc7vx6qq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1722, \"height\": 568, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ffpc7vx6qq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1781, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ffpc7vx6qq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 779, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ffpc7vx6qq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1637, \"height\": 828, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ffpc7vx6qq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1770, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ffpc7vx6qq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1584, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ffpc7vx6qq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1729, \"height\": 686, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 869, \"height\": 465, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 846, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1536, \"height\": 497, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 892, \"height\": 496, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1563, \"height\": 496, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 925, \"height\": 496, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1606, \"height\": 496, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 929, \"height\": 495, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 888, \"height\": 495, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 925, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1586, \"height\": 471, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 638, \"height\": 774, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 634, \"height\": 770, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 639, \"height\": 774, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1551, \"height\": 710, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1659, \"height\": 709, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1602, \"height\": 710, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ffpc7vx6qq/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1748, \"height\": 711, \"label\": \"Table\"}]"
motivation: LLM存在有害输出和对抗攻击风险，现有方法多修改模型权重，可能破坏已有能力。
method: 提出Safety Polytope，在表示空间中构建安全多面体，利用几何引导进行检测和修正。
result: 在多个LLM上，SaP有效检测不道德输入，同时保持了模型原有能力。
conclusion: 后处理几何引导方法可有效平衡安全性和能力保留。
---

## Abstract
Large language models (LLMs) have emerged as powerful tools but pose significant safety risks through harmful outputs and vulnerability to adversarial attacks. We propose SaP–short for Safety Polytope–a geometric approach to LLM safety, that learns and enforces multiple safety constraints directly in the model's representation space. We develop a framework that identifies safe and unsafe regions via the polytope's facets, enabling both detection and correction of unsafe outputs through geometric steering. Unlike existing approaches that modify model weights, SaP operates post-hoc in the representation space, preserving model capabilities while enforcing safety constraints. Experiments across multiple LLMs demonstrate that our method can effectively detect unethical inputs, reduce adversarial attack success rates while maintaining performance on standard tasks, thus highlighting the importance of having an explicit geometric model for safety. Analysis of the learned polytope facets reveals emergence of specialization in detecting different semantic notions of safety, providing interpretable insights into how safety is captured in LLMs' representation space.

---

## 论文详细总结（自动生成）

# 论文：Learning Safety Constraints for Large Language Models (SaP) 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

大型语言模型（LLM）在多种任务中表现出色，但其有害输出和对对抗攻击的脆弱性带来了严重的安全风险。现有方法（如 RLHF）存在局限性：模型可能“玩弄”奖励函数、训练数据标注噪声、缺乏可解释性、且难以进行后处理安全控制。训练时方法需要重新训练模型，推理时方法（如提示工程）则容易绕过。因此，论文提出一种**几何视角**：将 LLM 安全视为在模型表示空间中的约束学习问题，学习一个显式的安全集合（多面体），从而在不修改模型权重的情况下实现安全检测和输出纠正，并具有可解释性。

## 2. 论文提出的方法论

### 核心思想
- 受约束马尔可夫决策过程（CMDP）启发，将安全看作多面体约束：安全区域定义为多个线性不等式（多面体面）的交集。
- 从带安全/不安全标签的演示数据中学习多面体的参数（超平面ϕ和阈值ξ），然后通过几何引导（steering）将不安全输出拉回安全区域。

### 关键技术细节
1. **特征提取**：从LLM中间层（例如第20层）提取表示h，使用一个**概念编码器（Concept Encoder, CE）**（线性层+ReLU）得到特征向量 \(\tilde{f} = E_C(\bar{\pi}(x))\)，并加L1稀疏正则化以减少多义性。
2. **多面体学习（Convex Polytope Machine, CPM）**：将多面体学习转化为分类问题，优化包含hinge损失的损失函数：
   \[
   L(\phi, \tilde{\xi}) = \sum_{i \in I_{+1}} \sum_k [\kappa + \phi_k^\top \tilde{f}_i - \tilde{\xi}_k]_+ + \sum_{i \in I_{-1}} [\kappa - \phi_{z(\tilde{f}_i)}^\top \tilde{f}_i + \tilde{\xi}_{z(\tilde{f}_i)}]_+ + \lambda_{\tilde{f}} \|\tilde{f}_i\|_1 + \lambda_\phi \|\phi\|_2
   \]
   其中\(\kappa\)是边距，\(z(\cdot)\)是基于熵的启发式面分配（防止所有不安全点分配给同一个面）。通过梯度下降优化ϕ和\(\tilde{\xi}\)。
3. **表示引导（Steering）**：生成每个token时，如果表示h不在安全多面体内，则求解优化问题：
   \[
   \min_h \|\bar{\pi}_l(x) - h\|_1 \quad \text{s.t.} \quad \phi^\top \tilde{f}(h) \le \tilde{\xi}
   \]
   实际使用拉格朗日松弛进行多步梯度更新（如100步），得到修改后的激活h，替换原激活后继续生成后续token。算法1（SafeFlow）在生成循环中实时调整激活。

## 3. 实验设计

### 使用的数据集/场景
- **HarmBench**（Mazeika et al., 2024）：包含9种攻击方法（GCG, GBDA, AutoPrompt, PEZ, UAT, AutoDAN, Human Jailbreak, Direct Request, Adaptive Attack）。用于评估对抗攻击防御。
- **BeaverTails**（Ji et al., 2023）：330k条标注句子，涵盖14个安全类别（如虐待动物、儿童虐待、恐怖主义等）。用于评估多面体面的语义可解释性和分类性能。
- **MMLU**（Massive Multitask Language Understanding）：评估模型在保持安全防御时是否维持原始能力。
- 另在**JailBreakBench**上评估Adaptive Attack。

### 使用的模型
- Llama2-7B
- Ministral-8B
- Qwen2-1.5B

### 对比的基线方法
- 提示基方法：Self Reminder, Response Check, SmoothLLM
- 训练/分类基方法：Rejection Sampling（基于多面体决策拒绝）、MLP（参数数量相当的分类器，用BCE训练并按相同方式steering）、MLP+5（额外5层）
- 消融：有无Concept Encoder

### 实验配置
- 每个攻击方法重复5种子（seeds）。
- 训练时对每个模型使用其最有效的3种攻击的80%数据训练，测试时评估所有9种攻击。
- 分类实验：在BeaverTails上分别对每个类别和所有类别训练多面体，改变面数（1~60）并评估准确率。

## 4. 资源与算力

论文未明确说明使用的具体GPU型号、数量和训练时长。仅提及：
- 训练采用Adam优化器，学习率10^{-2}，batch size 128。
- 模型量化至16-bit（float16或bfloat16）。
- 特征维度（概念编码器输出）设为16384。
- 未知算力需求，但算法基于梯度下降可扩展。

**注意：** 论文缺少算力资源的明确说明。

## 5. 实验数量与充分性

- **对抗攻击防御实验**：在3个模型上，各9种攻击方法，7种防御方法（SaP + 6个基线），每种5个种子，共约3×9×7×5=945次运行。统计攻击成功率（ASR）和MMLU准确率。
- **可解释性实验**：在BeaverTails上计算互信息（有无CE），对比多面体面与14个安全类别的关联。手动分析KL散度聚焦于特定术语（如“kidnap”）。
- **消融实验**：面数对ASR和分类准确率的影响（1~50/60面），每个配置5种子。
- **与MLP对比**：比较测试准确率、ASR和MMLU。

**充分性评价**：实验设计较为全面，覆盖了不同模型规模、多种攻击类型、多种防御基线、消融分析以及可解释性分析。但未包括对更大量级模型（如70B）的验证。同时，部分基线（如SmoothLLM）在部分模型上效果一般，对比客观。

## 6. 论文的主要结论与发现

1. **有效性**：SaP能显著降低攻击成功率（Llama2-7B: 12.92%→0.26%, Ministral-8B: 55.77%→3.25%, Qwen2-1.5B: 27.57%→11.81%），同时保持MMLU准确率几乎不变。
2. **概念编码器关键**：引入CE后防御性能大幅提升（如Ministral ASR从51.5%降至1.7%），并减少多面体面的多义性（互信息热图更聚焦）。
3. **面数影响**：增加面数可提升防御和分类性能，但存在收益递减（约30面后稳定或下降）。
4. **几何建模优于黑箱分类**：SaP（多面体结构）比同等参数的MLP/MLP+5防御效果好得多，尽管分类准确率相近。
5. **可解释性**：多面体的不同面自然地与不同的安全语义概念相关联（如Facet 7对绑架敏感，Facet 22对性内容敏感）。无需监督语义标签，面学会了专业化。

## 7. 优点

- **新颖的几何框架**：将安全约束显式建模为多面体，提供结构化的几何直觉，区别于隐式黑箱方法。
- **后处理操作**：不修改模型权重，保留模型原始能力，可在推理时动态调整。
- **可解释性**：多面体面对应不同安全概念，可帮助理解模型内部安全机制。
- **有效防御多种攻击**：包括先进的对抗攻击（Adaptive Attack）和多种梯度/手工攻击。
- **计算高效**：训练和引导仅需前向传播和少量梯度更新，可向量化并行处理。

## 8. 不足与局限

- **语义解耦不完美**：CPM的启发式面分配策略限制了完全解耦，仍有部分面存在多义性（附录D）。需要更先进的机制解释性工具。
- **输出不连贯问题**：在Ministral-8B上，部分对抗攻击下SaP引导会产生语义不连贯的输出（但MMLU和MT-Bench表现正常）。
- **理论保证薄弱**：论文仅引用PAC学习推导的多面体样本复杂度（基于强假设，如数据完美可分），缺乏面向LLM实际设置的严格形式化保证。
- **实验范围有限**：仅测试了7B/8B/1.5B模型，未扩展到更大模型（如70B）或更多样化的安全场景；仅使用了标准能力基准，缺乏对更广泛有害内容的泛化验证。
- **资源消耗未报告**：没有给出GPU型号、训练时长等细节，影响复现和效率评估。
- **对抗适应性**：虽然对大多数攻击有效，但Qwen2-1.5B和Ministral-8B在某些攻击下ASR仍有提升空间（如Adaptive Attack完全无效于Qwen2，见附录C.2表6）。

（完）
