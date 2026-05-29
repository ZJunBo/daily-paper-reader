---
title: "From Steering Vectors to Conceptors: Compositional Affine Activation Steering for LLMs"
title_zh: 从引导向量到概念器：大语言模型的组合仿射激活引导
authors: "Steven Abreu, Joris Postmus, Alexander Müller, Jeremias Lino Ferrao, Ilija Lichkovski, Kurt Felix Michalak, Guillaume Pourcel, Alice S. Dauphin"
date: 2025-05-12
pdf: "https://openreview.net/pdf?id=0Yu0eNdHyV"
tags: ["query:dg"]
score: 8.0
evidence: 使用概念器进行大语言模型激活引导
tldr: 该论文针对大语言模型内部表征控制与理解的挑战，将概念器理论与激活引导相结合，提出一个基于第一性原理的最优仿射引导框架。概念器作为软投影矩阵压缩激活向量，实现精确可解释的内部状态控制。实验表明，该方法在上下文学习和对齐相关行为上一致优于加法引导。此外，通过概念器上的布尔运算实现多目标组合引导，取得更优性能。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1307, \"height\": 489, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 355, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1431, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 907, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1004, \"height\": 278, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0yu0endhyv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 514, \"height\": 451, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-0yu0endhyv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1409, \"height\": 258, \"label\": \"Table\"}]"
motivation: 现有激活引导方法缺乏最优性和可解释性，无法精确控制模型行为。
method: 将概念器理论融入激活引导，推导出最优仿射引导函数，并利用布尔运算实现组合引导。
result: 所提方法在上下文学习和对齐任务上均优于传统加法引导，且组合引导效果更佳。
conclusion: 概念器引导为LLM行为控制提供了可解释、可组合且性能优越的框架。
---

## Abstract
Controlling and understanding the internal representations of large language models (LLMs) remain central challenges. We combine conceptor theory with activation steering to develop a principled framework for provably optimal affine steering of LLM activations. Conceptors compress sets of activation vectors and act as soft projection matrices, enabling precise and interpretable control over internal states. Our framework derives optimal steering functions from first principles and consistently outperforms additive steering across in-context learning tasks and alignment-relevant behavior. We further demonstrate how Boolean operations over conceptors allow for compositional steering toward multiple objectives, yielding better performance than traditional vector combination methods. Together, these results establish conceptor-based steering as a powerful tool for both controlling LLM behavior and gaining insight into their internal mechanisms. We will release our code and data as part of a flexible open-source library for activation steering.

---

## 论文详细总结（自动生成）

# 论文深度总结：From Steering Vectors to Conceptors: Compositional Affine Activation Steering for LLMs

## 1. 核心问题与整体含义（研究动机与背景）

- **研究背景**：大语言模型（LLM）在生成文本时容易产生偏见、有害输出和错误信息。现有控制方法（如 RLHF、监督微调、提示工程）要么计算成本高、泛化能力差，要么效果不稳定。
- **现有方法的局限**：激活引导（Activation Steering, AS）作为一种轻量级的推理时干预手段已受到关注，但主流方法（如对比激活加法）主要基于简单的向量加法，缺乏理论最优性证明，且无法适应输入上下文。
- **论文的核心问题**：能否提出一种从第一性原理出发的、**可证明最优**的仿射激活引导框架，既能更精确地控制 LLM 行为，又能通过组合操作实现多目标引导，同时保持可解释性？
- **整体含义**：论文将概念器理论（Conceptor Theory）引入 LLM 激活引导，建立了从线性/仿射变换到布尔运算的完整理论体系，并证明其在函数向量任务和 AI 安全相关行为上均优于传统加法引导，为 LLM 行为控制与内部机制理解提供了新范式。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：用**概念器（Conceptor）** 替代简单的引导向量。概念器是一个正半定矩阵（软投影矩阵），通过对概念条件二阶矩的优化，得到可证明最优的线性/仿射映射，能够自适应地改变激活向量（保留靠近概念子空间的分量，压缩远离的分量）。
- **关键技术细节**：
  - **最优线性引导函数**：求解优化问题  
    \( C(\varepsilon) = \arg\min_C \mathbb{E}[\|H_c - C H_c\|^2] + \varepsilon^2 \|C\|_F^2 \)  
    得到闭式解：\( C = \tilde{\Sigma}_c (\tilde{\Sigma}_c + \varepsilon^2 I)^{-1} \)，其中 \(\tilde{\Sigma}_c\) 是概念条件二阶矩矩阵，\(\varepsilon\) 为孔径参数。
  - **最优仿射引导函数**：在优化中加入偏置项 \(b\)，得到  
    \( C = \Sigma_c (\Sigma_c + 2\varepsilon^2 I)^{-1} \)，\( b = \mu_c - C\mu_c \)，最终引导函数为 \(f(x)=C(x-\mu_c)+\mu_c\)。
  - **残差引导（Residual Steering）**：采用 \(f(x)=Cx + x = (C+I)x\)，使得增益在 [1,2] 范围，既保留所有方向信号又适度放大概念相关模式，更符合 Transformer 的残差更新偏置。
  - **布尔运算组合**：利用概念器上的 OR、NOT、AND 操作（基于协方差矩阵加法和取逆），实现多个概念的组合引导。例如 \(C_1 \lor C_2\) 表示并集，\(\lnot C\) 表示补集。
- **算法流程**：
  1. 收集概念正例的激活向量样本，计算样本二阶矩 \(\hat{\tilde{\Sigma}}_c\) 和均值 \(\hat{\mu}_c\)。
  2. 根据公式计算概念器矩阵 \(C\)（线性或仿射）。
  3. 在推理时，对目标层的残差流激活进行变换：\(h' = C h\)（线性）或 \(h' = C(h-\mu_c)+\mu_c\)（仿射）。
  4. 对于多目标组合，可先分别计算单个概念的概念器，再通过布尔运算合成复合概念器 \(C_{\text{composite}}\)，然后应用引导。

## 3. 实验设计：数据集/场景、基准、对比方法

- **任务与数据集**：
  - **函数向量任务**（Todd et al., 2024）：antonyms（反义词）、present→past（时态转换）、English→French（翻译）、singular→plural（单复数）、country→capital（国家首都）、capitalize（首字母大写）。使用 GPT-J (6B) 和 GPT-NeoX (20B)。
  - **组合函数任务**：自建三个复合任务（English-French & antonyms、English-French & capitalize、singular-plural & capitalize），数据由 GPT-4o 生成。
  - **安全相关行为任务**（Perez et al., 2022“Coordinate with other AIs”）：模型是否同意与其他 AI 协作（可能偏离人类利益）。使用 Qwen 2.5-1.5B Instruct 和 Mamba 2.8B（状态空间模型）。
- **基准与对比方法**：
  - **加法引导（Additive Steering）**：使用对比激活加法（CAV），即 \(b = \mu_c - \mu_{c'}\)。
  - **均值中心化（Mean-Centering）**：对加法引导向量进行均值中心化（Jorgensen et al., 2023b）。
  - **线性概念器**：本论文提出的线性引导（仅使用 C）。
  - **仿射概念器**：本论文提出的仿射引导（C 和 b）。
  - **组合引导**：加法引导向量直接取平均 vs. 概念器用 AND 操作合成。
  - **额外对比**：在函数向量任务上，还对比了全秩 LoRA 适配器（训练至收敛，计算量更大）。

## 4. 资源与算力

- **论文未明确列出 GPU 型号、数量或训练时长**。仅提及使用了 GPT-J 6B、GPT-NeoX 20B、Mamba 2.8B、Qwen 1.5B 等模型，并提到实验在 NVIDIA GPU 上运行。由于论文主要依赖推理时激活引导（无需训练），整体计算需求相对低，但全秩 LoRA 对比实验需要较多训练资源。具体的资源消耗（如 GPU 小时数）未报告。

## 5. 实验数量与充分性

- **实验组数**：
  - 函数向量任务：在 6 个任务上，每个任务重复 5 次随机种子取平均，并在 GPT-J 和 GPT-NeoX 两个模型上均执行，覆盖全部层（GPT-J 约 28 层，GPT-NeoX 约 44 层）。
  - 组合函数任务：3 个复合任务，在 GPT-J 全部层上测试。
  - 安全任务：两个模型（Qwen 1.5B, Mamba 2.8B），分为多选题（MCQ）和开放式生成两种评估方式，每层均搜索最优超参数。
  - 额外对比：全秩 LoRA 训练对比。
- **充分性与客观性**：
  - 实验覆盖了不同模型架构（Transformer 和 Mamba SSM）、不同规模（1.5B ~ 20B）、不同任务类型（函数向量、行为控制）。
  - 使用网格搜索最优超参数（孔径 ε、引导强度 φ）。
  - 结果展示最佳层性能，并提供全层曲线。
  - 自建复合任务由 GPT-4o 生成，可能引入数据偏差，但作为对比实验仍具参考价值。
  - **不足**：开放式生成任务上概念器表现不如加法引导，作者解释为超参数搜索粗糙（仅搜索了 <50% 的层），需更细致探索；部分实验（安全任务）未提供误差棒。

## 6. 主要结论与发现

1. **概念器引导在函数向量任务上一致优于加法引导**：在所有 6 个任务和两个模型上，线性/仿射概念器的准确率均高于对比激活加法，部分任务提升 30% 以上（如反义词从 20.54% 提升到 52.14%）。
2. **仿射概念器在部分任务上进一步小幅提升**：相比于线性概念器，仿射版本在 country-capital 等任务上提升约 3-5%。
3. **组合引导中概念器 AND 操作优于向量平均**：在三个复合任务上，概念器 AND 组合始终优于加法向量平均，且两者均优于直接计算复合函数的引导（可能由于数据量不足）。
4. **在安全相关行为控制（多选题）中，概念器方法优于加法引导**：无论是标准概念器还是对比概念器（NOT 组合），均获得更高的准确率提升。
5. **残差引导增强了概念器在 LLM 中的适用性**：符合 Transformer 残差流更新机制，且能放大概念相关特征而不丢失基线信息。

## 7. 优点

- **理论完备性**：从优化目标推导闭式解，提供了可证明最优的线性/仿射引导，弥补了加法引导的理论空白。
- **可解释性**：概念器作为软投影矩阵，其几何意义清晰（高维椭球），且矩阵结构本身可分析，便于理解模型内部表示。
- **可组合性**：布尔运算（AND/OR/NOT）提供了一种自然的复合概念构建方式，适用于多任务、多行为控制。
- **架构无关性**：在 Transformer 和状态空间模型（Mamba）上均表现良好，表明方法的通用性。
- **计算高效**：相比 LoRA 或微调，概念器只需一次前向收集激活和矩阵求逆（D×D），推理时仅需一次矩阵乘法，计算成本低。
- **自适应**：概念器对靠近概念子空间的激活改变小，远离的改变大，无需额外门控机制。

## 8. 不足与局限

- **实验覆盖有限**：
  - 仅测试了 6B/20B 及更小模型（1.5B/2.8B），更大模型（如 70B+）未验证，可能面临计算和泛化挑战。
  - 长对话或多语言场景未覆盖。
  - 开放式生成任务结果不理想，超参数搜索不充分，影响了结论的全面性。
- **偏差与安全风险**：
  - 概念器可能继承训练数据中的偏差，甚至放大有害模式，需额外公平性审计。
  - 尽管作者讨论双用风险，但未提供对抗性评估或安全基准测试。
- **计算与数据需求**：概念器矩阵维度 D×D，在高维残差流（如 4096 维）下计算协方差矩阵和求逆可能比简单向量加法更昂贵，且需要更多正例样本才能稳定估计二阶矩。
- **对超参数敏感**：孔径 ε 和强度 φ 需针对每层搜索，增加了调参成本。
- **缺乏误差分析**：安全任务未报告多次运行的标准差，且开放式评估使用 GPT-4.1-mini 作为评判，主观性可能引入偏差。

（完）
