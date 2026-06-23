---
title: "CP-Router: An Uncertainty-Aware Router Between LLM and LRM"
title_zh: CP-Router：基于不确定性感知的LLM与LRM间路由
authors: "Jiayuan Su, Fulin Lin, Zhaopeng Feng, Han Zheng, Teng Wang, Zhenyu Xiao, Xinlong Zhao, Zuozhu Liu, Lu Cheng, Hongwei Wang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40589/44550"
tags: ["query:luq"]
score: 8.0
evidence: 基于conformal prediction和熵的不确定性感知路由
tldr: 大型推理模型（LRM）在简单问题上可能产生冗余输出，而LLM则更高效。本文提出CP-Router，一种无需训练的路由框架，利用保形预测（CP）估计预测不确定性，并引入全二元熵（FBE）提高区分度。该框架能动态选择LLM或LRM，在MCQA任务上兼顾效率与准确性，且提供严格覆盖保证。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: LRM在简单查询上过于冗长且可能降低精度，需要路由机制。
method: 利用保形预测估计不确定性，并引入全二元熵（FBE）改进区分度。
result: 在MCQA任务上实现了高效的模型选择，兼顾准确性与效率。
conclusion: 不确定性感知路由为LLM与LRM协同工作提供了有效方案。
---

## Abstract
Recent advances in large reasoning models (LRMs) have significantly enhanced long-chain reasoning capabilities over standard large language models (LLMs). However, LRMs often produce unnecessarily lengthy outputs even for simple queries, leading to inefficiencies or even accuracy degradation compared to LLMs. To address this, we propose CP-Router, a training-free, model-agnostic routing framework that dynamically selects between an LLM and an LRM, demonstrated with multiple-choice question answering (MCQA) prompts. The routing decision is guided by the prediction uncertainty estimates derived via  Conformal Prediction (CP), which provides rigorous coverage guarantees. To improve uncertainty differentiation across inputs, we introduce Full and Binary Entropy (FBE), a novel entropy-based criterion that adaptively selects the appropriate CP threshold. Experiments across MCQA and QA benchmarks—including mathematics, logical reasoning, and Chinese chemistry—demonstrate that CP-Router efficiently reduces token usage while maintaining or even improving accuracy compared to using LRM alone.  We further demonstrate the generality and robustness of CP-Router by extending it to diverse model pairings beyond the LLM–LRM setting.

---

## 论文详细总结（自动生成）

# CP-Router 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：大型推理模型（LRM，如 OpenAI o1/o3、DeepSeek-R1）虽然在复杂推理任务上优于普通大型语言模型（LLM），但面对简单查询时也会产生大量冗余推理 token，导致“过度思考”（overthinking）——不仅浪费计算资源，有时甚至降低准确率。而普通 LLM 在处理简单问题时更简洁高效。
- **整体含义**：本文旨在设计一种动态路由机制，能自动判断每个输入是适合 LLM 还是 LRM，在保持或提升准确率的前提下大幅减少 token 开销。
- **关键需求**：路由应具备**自适应性**（自动判断）、**模型无关性**（兼容不同模型对）、**轻量级**（无需训练、低 token 开销）。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：利用保形预测（Conformal Prediction, CP）对 LLM 在 MCQA 任务中的预测不确定性进行量化，根据预测集大小（size of prediction set）作为不确定性的代理指标，将小预测集的简单问题路由给 LLM，大预测集的困难问题路由给 LRM。
- **关键技术细节**：
  - **CP 构建**：对每个输入，基于 LLM 输出的 softmax 概率定义非符合性分数 \(S(x,y)=1-f(y)\)，在校准集上计算分位数 \(\hat{q}\)，然后生成预测集 \(C(x)=\{y: S(x,y)\le \hat{q}\}\)，保证真实标签以 \(1-\alpha\) 的概率被包含。
  - **路由规则**：预测集大小为 1 表示低不确定性，路由给 LLM；否则路由给 LRM。
  - **自适应阈值选择**：提出 Full and Binary Entropy (FBE) 指标，结合全熵（衡量预测集大小的整体多样性）和二元熵（衡量单例集与非单例集的平衡）。通过网格搜索选择最大化 FBE 的误差率 \(\alpha^*\)，从而获得更好的不确定性区分能力。
  - **公式**：\(\text{FBE} = \beta H_{\text{full}} + H_{\text{binary}}\)，其中 \(\beta\) 为权重（实验中设为 3:1）。
- **算法流程**（文字说明）：
  1. 准备校准集，用 LLM 计算各选项概率。
  2. 对候选的多个 \(\alpha\) 值，在测试集（或验证集）上运行 CP 得到预测集大小分布，计算 FBE。
  3. 选择使 FBE 最大的 \(\alpha^*\)。
  4. 用该 \(\alpha^*\) 对测试样本进行 CP，依据预测集大小路由：size=1 → LLM，否则 → LRM。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：共 7 个 MCQA 基准 + 1 个 QA 基准，涵盖数学（MMLU-STEM 的子集：Elementary Math, High School Math, College Math）、逻辑推理（GPQA, LogiQA）、中文化学（CN-Chemistry）以及开放 QA 的 GSM8K。
- **基准（backbone models）**：
  - LLM：Llama-3-8B, Qwen-2.5-14B, DeepSeek-V3（较大规模）。
  - LRM：DeepSeek-R1-Distilled-Llama-3-8B, DeepSeek-R1-Distilled-Qwen-2.5-14B, DeepSeek-R1。
- **对比方法**：
  - 单模型：仅 LLM 或仅 LRM。
  - 混合路由方法：Random（随机路由）、Top-1（基于 top-1 概率阈值）、Entropy（基于响应熵）、Explicit（显式自感知路由）、Dynathink（基于多数投票的动态路由）。
- **评估指标**：
  - Acc（准确率）
  - TRR（Token Reduction Ratio，相较于 LRM 的 token 节省比例）
  - Token Utility（Utoken = (Acc - Acc_LLM) / (1 - TRR)），衡量每 token 的准确率增益。

## 4. 资源与算力

- **文中未明确说明**使用的具体 GPU 型号、数量或训练时长。因为 CP-Router 是 **training-free** 方法，仅需在 LLM 上运行前向推理（logit 提取）和 CP 校准，不涉及模型训练，所以计算开销主要来自 LLM 和 LRM 的推理。论文提到了在 GSM8K 上对比了 wall-clock time（表 4），CP-Router 相比单独 LRM 减少了 9.3% 的总时间（从 71,974.5s 降至 44,623.8s），并节省了 33% 的 completion token。但未给出训练资源的细节，因为不需要训练。

## 5. 实验数量与充分性

- **实验数量**：主实验在两个模型配对（Llama 配对 6 个 MCQA 数据集，Qwen 配对 6 个 MCQA 数据集）上报告了完整结果；额外实验包括：
  - 在 GPQA 上对更大模型（DeepSeek-V3 + R1）进行路由测试。
  - 在 CN-Chemistry 上测试 LLM 强于 LRM 的场景。
  - 对 FBE 进行消融（去掉全熵或二元熵，以及不同权重）。
  - 扩展到开放 QA 格式（GSM8K）。
  - 跨族配对（如 Qwen LLM + Llama LRM）和同能力配对（两个 LLM）的泛化测试。
  - 分析了阈值选择和预测集大小分布。
- **充分性与公平性**：实验覆盖了多种模型规模、多个领域、多种路由基线，且给出了统计可靠的指标（Utoken 考虑了准确率和 token 效率的 trade-off）。消融实验验证了 FBE 各成分的必要性。但所有实验均在 MCQA 场景下进行，开放 QA 仅通过手动构造四选一+“其他”选项的方式近似，可能存在偏差。此外，未在更多非 MCQA 任务（如文本生成、分类）上验证。

## 6. 主要结论与发现

- CP-Router 在几乎所有基准上取得了最高的 token utility，同时保持了与 LRM 相当或更高的准确率，并显著减少了 token 消耗。
- 对于不同的难易度数据，CP-Router 自动调整路由比例：简单数据集（如 Elementary Math）节省更多 token（22.8%），困难数据集（如 College Math）路由比例较低，体现自适应性。
- 当 LLM 本身强于 LRM（如 CN-Chemistry 14B 设置）时，CP-Router 仍能进一步提升准确率（超过 LLM 0.8%），表明其灵活利用模型优势的能力。
- FBE 自适应校准比固定 α 或单一熵指标更有效，平衡了准确率和效率。
- CP-Router 可适用于不同模型族（跨族配对）甚至两个 LLM 的组合，具有良好泛化性。

## 7. 优点

- **无需训练**：CP-Router 完全免训练，只需 LLM 前向计算的 logit，易于部署。
- **提供理论保证**：CP 框架提供有限样本的覆盖保证（1-α），路由决策有统计基础。
- **新颖的自适应校准**：FBE 结合整体分布和二元分类分布，自动选择最优 α，避免了手动调参。
- **综合评估指标**：提出 Token Utility，公平对比不同 token 消耗级别的方法。
- **验证充分**：在多个模型配对、多种难度、多种路由基线下验证，消融实验完整。

## 8. 不足与局限

- **仅针对 MCQA**：论文主要验证了多选问答场景，开放 QA 仅通过近似处理（四选一+Others）验证，该近似可能引入偏差。对于生成式任务或非分类任务，CP 的定义需要调整，适用性需进一步研究。
- **未讨论延迟问题**：路由本身需要 LLM 推理一次（获取 logit），这增加了额外计算开销。虽然 token 总开销降低，但若 LLM 推理延迟高，可能会影响整体响应速度。文中仅比较了 token 数和 wall-clock time，但未分析极端情况下的延迟瓶颈。
- **校准集依赖**：CP 需要校准集，且依赖交换性假设；若测试分布发生漂移，覆盖保证可能失效。论文未评估分布漂移下的鲁棒性。
- **规模测试有限**：虽然尝试了 DeepSeek-V3 + R1 的大模型配对，但只在一个数据集（GPQA）上测试，且未提供计算资源细节（如 GPU 类型/数量）。对于更大规模或更复杂的生成任务，FBE 的网格搜索可能耗费较多时间。
- **可解释性**：FBE 选择 α 的机理虽然有效，但缺乏理论上的最优性证明（仅凭实验验证）。

（完）
