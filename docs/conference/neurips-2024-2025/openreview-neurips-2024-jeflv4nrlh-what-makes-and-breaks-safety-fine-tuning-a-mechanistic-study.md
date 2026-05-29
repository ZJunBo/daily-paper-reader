---
title: What Makes and Breaks Safety Fine-tuning? A Mechanistic Study
title_zh: 是什么促成和破坏安全微调？一项机制研究
authors: "Samyak Jain, Ekdeep Singh Lubana, Kemal Oksuz, Tom Joy, Philip Torr, Amartya Sanyal, Puneet K. Dokania"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=JEflV4nRlH"
tags: ["query:dg"]
score: 8.0
evidence: 用于安全微调分析的合成安全数据生成框架
tldr: "该论文为了理解安全微调如何使模型安全，设计了一个合成数据生成框架，通过建模任务（如'设计'）与特定概念（如'炸弹'）的交互来捕捉不安全输入的显著方面。利用此框架，研究了监督安全微调、直接偏好优化和遗忘三种常用方法，发现这些方法仅极小地变换MLP权重以对准不安全输入，揭示了安全微调的机制。"
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-jeflv4nrlh/fig-001.webp\", \"caption\": \"\", \"page\": 10, \"index\": 1, \"width\": 2048, \"height\": 564}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jeflv4nrlh/fig-002.webp\", \"caption\": \"\", \"page\": 10, \"index\": 2, \"width\": 2048, \"height\": 307}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jeflv4nrlh/fig-003.webp\", \"caption\": \"\", \"page\": 21, \"index\": 3, \"width\": 1116, \"height\": 274}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jeflv4nrlh/fig-004.webp\", \"caption\": \"\", \"page\": 21, \"index\": 4, \"width\": 1124, \"height\": 422}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jeflv4nrlh/fig-005.webp\", \"caption\": \"\", \"page\": 22, \"index\": 5, \"width\": 1124, \"height\": 1102}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jeflv4nrlh/fig-006.webp\", \"caption\": \"\", \"page\": 23, \"index\": 6, \"width\": 1126, \"height\": 1102}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jeflv4nrlh/fig-007.webp\", \"caption\": \"\", \"page\": 24, \"index\": 7, \"width\": 1120, \"height\": 1140}]"
motivation: 安全微调的内在机制尚不明确，需要可控的实验框架来解析。
method: 设计合成数据生成框架，通过分解任务和概念构建不安全样本，用于机制分析。
result: 三种安全微调方法仅对MLP权重做最小变换以对准不安全输入，而非全面改变模型行为。
conclusion: 安全微调的作用机制是局部调整，而非全局重塑，为改进对齐提供启示。
---

## Abstract
Safety fine-tuning helps align Large Language Models (LLMs) with human preferences for their safe deployment. To better understand the underlying factors that make models safe via safety fine-tuning, we design a synthetic data generation framework that captures salient aspects of an unsafe input by modeling the interaction between the task the model is asked to perform (e.g., “design”) versus the specific concepts the task is asked to be performed upon (e.g., a “cycle” vs. a “bomb”). Using this, we investigate three well-known safety fine-tuning methods—supervised safety fine-tuning, direct preference optimization, and unlearning—and provide significant evidence demonstrating that these methods minimally transform MLP weights to specifically align unsafe inputs into its weights’ null space. This yields a clustering of inputs based on whether the model deems them safe or not. Correspondingly, when an adversarial input (e.g., a jailbreak) is provided, its activations are closer to safer samples, leading to the model processing such an input as if it were safe. Code is available at https://github.com/fiveai/understanding_safety_finetuning.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

大型语言模型（LLMs）在预训练和指令微调后，通常还需要进行**安全微调（safety fine-tuning）**，以引导模型生成符合人类偏好的安全输出。然而，即使经过安全微调，模型仍然容易受到**越狱攻击（jailbreaks）**和**对抗攻击**的威胁，产生不安全输出。该论文旨在系统性地探究两个关键问题：
- 安全微调究竟让模型学到了什么样的**安全机制**？
- 越狱和对抗攻击为什么能够绕过这个机制？

研究的整体含义在于：通过揭示安全微调内部的工作原理及其脆弱性的根源，为设计更鲁棒的安全对齐方法提供理论基础。论文采用**合成数据生成框架**来模拟安全/不安全样本，并利用该框架对三种主流安全微调方法（监督安全微调、直接偏好优化、遗忘学习）进行机制层面的分析。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- 将模型输入抽象为**算子（operator）**和**操作数（operand）**的组合。算子代表任务（如“设计”），操作数代表概念（如“自行车”或“炸弹”）。安全/不安全取决于算子与操作数的上下文组合。
- 通过**概率上下文无关文法（PCFG）**生成文本序列，并定义安全主导/不安全主导的非终止节点，使得算子与操作数的交互可以控制样本的安全标签。
- 在合成数据上训练 minGPT 模型，然后在安全微调阶段，对不安全样本强制模型输出“空令牌（null token）”，对安全样本则正常执行指令。

### 关键技术细节
- **安全微调方法**： 
  - 监督安全微调（SSFT）：仅使用偏好输出进行交叉熵损失。
  - 遗忘学习（Unlearning）：同时最小化偏好输出损失并最大化不偏好输出损失。
  - 直接偏好优化（DPO）：使用基于指令微调模型的参考损失构造偏好目标函数。
- **分析工具**：
  - **激活空间聚类**：比较安全样本与不安全样本在中间层激活上的欧氏距离差异（τ 指标）。
  - **参数空间分析**：计算安全微调前后的权重变化 ∆W，分析其列空间与指令微调权重列空间/零空间的关系。
  - **局部 Lipschitz 性质**：计算模型对输入的梯度范数，衡量敏感性变化。
- **越狱/对抗攻击建模**：
  - 竞争目标（任务/文本）、错配泛化（使用未在安全微调中出现过的任务令牌）、连续嵌入对抗攻击（添加可学习软令牌）。

## 3. 实验设计：数据集 / 场景、benchmark、对比方法

### 数据集与场景
- **合成数据**：基于四个 PCFG 生成训练数据，包含 12 个双射映射算子，文本令牌长度 15-25。安全/不安全标签由非终止节点所属集合（A 或 B）和算子组合决定。
- **真实数据验证**：使用 Llama-2 7B、Llama-2 chat 7B、Llama-3 8B、Llama-3 chat 8B 等模型，并构建了包含 500 条安全/不安全自然语言指令的数据集（部分由 GPT-4 扩充）。

### Benchmark
- **安全性能评估**：在合成数据上计算模型输出正确令牌（指令跟随或空令牌）的准确率。
- **越狱攻击成功率**：对每种安全微调方法，测试三类越狱攻击（JB-CO-Task, JB-CO-Text, JB-MisGen）下模型遵循不安全指令的比例。

### 对比方法
- 三种安全微调方法（SSFT, DPO, Unlearning），分别采用中等学习率（ηM=1e-4）和小学习率（ηS=1e-5）。
- 基线：指令微调模型（无安全微调）以及标准交叉熵微调（仅指令跟随）作为对比。

## 4. 资源与算力

论文明确提及了计算资源信息：
- **预训练与指令微调阶段**：使用单张 RTX A6000 GPU（48GB 显存），batch size=512，训练 100k 迭代，耗时超过 8 小时。
- **安全微调阶段**：10k 迭代，余弦学习率衰减，使用相同 GPU。
- **分析实验**：使用单张 RTX A4500 GPU（20GB 显存）。
- 对 Llama 模型的实验未给出具体算力细节，但推测在类似硬件上运行。

## 5. 实验数量与充分性

论文进行了大量实验，包括：
- **合成数据实验**：对三种安全微调方法、两种学习率、六大模型层进行全面的激活空间、参数空间、Lipschitz 常数分析（共约 6×2×6=72 组基础实验，还有越狱攻击变体）。
- **真实模型实验**：对 Llama-2 和 Llama-3 模型进行聚类分析和 ∆W 投影分析，验证主要结论的迁移性。
- **干预实验**：通过线性插值/外推 ∆W 方向，测试 α 值变化对性能及簇分离的影响。
- **消融与动态分析**：跟踪训练过程中 ∆W 的演化、秩变化等。

**充分性评价**：实验覆盖了多种安全微调方法、不同学习率、多种攻击类型（三种越狱+对抗攻击），并且同时使用合成数据和真实模型进行验证，设计较为全面。但也存在一定局限（见不足部分）。实验结果是客观、可复现的，代码已开源。

## 6. 论文的主要结论与发现

1. **安全微调促使安全与不安全样本在激活空间形成分离的簇**，且更强的方法（如 DPO、Unlearning）和更大学习率下分离更明显。不安全样本的簇呈现低秩结构（top 奇异值占比高达 62%），而安全样本的簇形态变化不大。
2. **安全的驱动因素是参数更新 ∆W 被专门设计来影响不安全样本**：∆W 的列空间主要落在指令微调权重的左零空间中，且 `||∆W a||` 对不安全样本的激活影响远大于安全样本；预激活在 ∆W 行空间上的投影也集中于不安全样本。
3. **安全微调显著降低了模型对不安全样本的局部 Lipschitz 常数**，即敏感性降低；对安全样本则提升。
4. **越狱/对抗攻击样本的中间特征更接近于安全样本**，因此无法激活 ∆W 专门为不安全样本设计的影响路径，导致模型将其当作安全输入处理。
5. 通过线性外推 ∆W（α>1），可以进一步增强较弱方法（如 SSFT）的安全性能，而几乎不损失安全样本上的准确率。

## 7. 优点：方法或实验设计上的亮点

- **精妙的合成数据框架**：将自然语言中的算子-操作数交互抽象化，并使用 PCFG 生成可控的安全/不安全数据，使得机械性分析成为可能。该框架还能系统建模多种越狱攻击（对应 Wei et al. 提出的分类），具有较好的泛化性。
- **多维度机械性分析**：同时考察激活空间聚类、参数空间投影（特别是空空间分析）和函数敏感性，相互印证，揭示安全机制的本质。
- **干预验证**：通过线性插值与外推，直接验证 ∆W 的因果作用，思路简洁有力。
- **对真实模型的迁移验证**：在 Llama 系列模型上复现主要结论，提高了发现的普适性。
- **开源代码**：便于复现和后续研究。

## 8. 不足与局限：包括实验覆盖、偏差风险、应用限制

- **合成数据的简约性**：虽然设计精巧，但合成数据与真实自然语言仍有差距。关键假设（算子为双射映射、PCFG 生成）可能无法完全捕捉真实世界安全风险的复杂性。
- **模型规模**：合成实验基于约 3M 参数的 minGPT，真实实验只用了 7B/8B 规模的模型，没有在更大模型（如 70B 或 180B）上验证。规模扩展是否改变结论尚不清楚。
- **攻击类型有限**：仅模拟了论文中提出的三种越狱类型，未覆盖所有已知越狱变体（如多轮对话、角色扮演、递归攻击等）。
- **缺少对 RLHF 的直接分析**：论文仅分析了 DPO（不需要显式奖励模型），而实际常用的 RLHF 可能具有不同的机制。作者提到 DPO 是 RLHF 的替代但未保证等价。
- **未区分不同越狱攻击的内部差异**：论文承认没有观察到不同越狱类型绕过安全机制的明显差异，这限制了对攻击多样性的理解。
- **实验可重复性细节**：虽然提供了代码和超参数，但 PCFG 的具体规则和划分细节可能影响复现结果，且某些可视化结果缺乏标准差或置信区间（尽管有误差条）。
- **局限性明确被作者提及**：无法获得所有模型的指令微调权重（如 Llama-2 只有预训练和 chat 版本），限制了部分分析的完整性。

（完）
