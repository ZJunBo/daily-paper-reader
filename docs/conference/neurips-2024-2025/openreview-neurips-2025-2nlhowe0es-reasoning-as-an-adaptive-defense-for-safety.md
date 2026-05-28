---
title: Reasoning as an Adaptive Defense for Safety
title_zh: 推理作为安全的自适应防御
authors: "Taeyoun Kim, Fahim Tajwar, Aditi Raghunathan, Aviral Kumar"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=2NLHoWE0eS"
tags: ["query:smd"]
score: 7.0
evidence: 混合有害、无害和模糊提示来训练安全推理，与对齐保持的数据混合相关
tldr: 该论文提出TARS，一种基于强化学习的训练方法，让模型学会通过思维链进行安全推理。关键设计包括使用安全推理的轻量级SFT预热、混合有害、无害和模糊提示以防止捷径拒绝行为。实验表明该方法能在保持任务完成度的同时提升对安全漏洞的鲁棒性，为安全对齐提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-2nlhowe0es/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1432, \"height\": 508, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2nlhowe0es/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2nlhowe0es/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 763, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2nlhowe0es/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1450, \"height\": 254, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2nlhowe0es/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1451, \"height\": 489, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2nlhowe0es/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1456, \"height\": 617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2nlhowe0es/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1342, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2nlhowe0es/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1160, \"height\": 648, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2nlhowe0es/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1462, \"height\": 650, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2nlhowe0es/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1449, \"height\": 332, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-2nlhowe0es/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1435, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2nlhowe0es/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 762, \"height\": 425, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2nlhowe0es/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 825, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2nlhowe0es/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 592, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2nlhowe0es/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1448, \"height\": 473, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2nlhowe0es/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1427, \"height\": 413, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2nlhowe0es/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 705, \"height\": 168, \"label\": \"Table\"}]"
motivation: 现有安全对齐方法在面对复杂提示时容易产生捷径拒绝，缺乏自适应推理能力。
method: 使用强化学习训练模型生成安全推理的思维链，并混合多种类型提示来促进泛化。
result: 在安全评估中，TARS在保持任务性能的同时显著提升了模型对有害提示的防御能力。
conclusion: 推理式的安全防御比单纯的拒绝模式更灵活有效，是未来安全对齐的重要方向。
---

## Abstract
Reasoning methods that adaptively allocate test-time compute have advanced LLM performance on easy to verify domains such as math and code. In this work, we study how to utilize this approach to train models that exhibit a degree of robustness to safety vulnerabilities, and show that doing so can provide benefits. We build a recipe called $\textit{\textbf{TARS}}$ (Training Adaptive Reasoners for Safety), a reinforcement learning (RL) approach that trains models to reason about safety using chain-of-thought traces and a reward signal that balances safety with task completion. To build TARS, we identify three critical design choices: (1) a ``lightweight'' warmstart SFT stage, (2) a mix of harmful, harmless, and ambiguous prompts to prevent shortcut behaviors such as too many refusals, and (3) a reward function to prevent degeneration of reasoning capabilities during training. Models trained with TARS exhibit adaptive behaviors by spending more compute on ambiguous queries, leading to better safety-refusal trade-offs. They also internally learn to better distinguish between safe and unsafe prompts and attain greater robustness to both white-box (e.g., GCG) and black-box attacks (e.g., PAIR). Overall, our work provides an effective, open recipe for training LLMs against jailbreaks and harmful requests by reasoning per prompt.

---

## 论文详细总结（自动生成）

## 论文核心问题与整体含义

- **研究动机**：现有大型语言模型的安全对齐方法（如RLHF、SFT）在面对复杂或模糊的有害请求时，容易走向两个极端——要么过度拒绝（即使是无害请求），要么无法有效防御越狱攻击。而推理模型在数学和代码领域通过自适应分配测试时计算（如思维链）取得了显著成功。
- **整体含义**：论文研究是否可以将这种推理范式迁移到安全防御中，训练模型根据每个提示的复杂度进行自适应推理，在保持任务完成度的同时提升安全性，从而实现更好的安全-拒绝权衡。

## 论文方法论

- **核心思想**：利用强化学习（RL）训练模型生成关于安全的推理轨迹（通过<think>标记的思维链），并设计特定的数据混合策略与奖励函数来防止捷径行为（如一律拒绝）。
- **关键技术细节**：
  1. **Stage I: 轻量级SFT预热**：使用低学习率、少epochs（3 epoch）在1000个有害提示上蒸馏DeepSeek-R1的推理轨迹（每个提示4条）。目的在于引入探索性推理样式，而非追求完美安全。
  2. **Stage II: 提示集设计**：混合三类提示——
     - 有害提示（来自WildJailbreak、Aegis、Rainbow Teaming攻击生成）
     - 无害提示（来自UltraFeedback）
     - 模糊提示（来自OR-Bench，看似有害实则无害）
     以防止模型学会偷懒拒绝所有提示。
  3. **Stage III: RL训练**：使用GRPO算法。奖励函数由三部分组成：
     - **安全奖励** (rs)：通过Moderation API评估回答在各个有害类别（如暴力、色情）上的最高分，若<0.1则给1分，否则为1-分数。
     - **任务完成奖励** (rn)：对无害提示使用通用偏好模型GRM，经sigmoid归一化。
     - **格式奖励** (rf)：二进制，判断是否包含正确的<think>和</think>标记。
     最终奖励为rtotal = rf × (安全或任务完成奖励) ，针对不同类型提示使用不同的奖励。

- **算法流程**（文字说明）：
  - 初始化用指令微调模型（Qwen-2.5-1.5B/7B-Instruct）。
  - 轻量SFT阶段：在蒸馏的推理轨迹上微调，获得具有基本推理能力和多样性的πSFT。
  - RL阶段：对于有害提示，优化安全奖励；对于无害和模糊提示，优化任务完成奖励。同时保证格式正确。训练中混合不同比例（λ=0.1~0.9）的有害-无害提示。

## 实验设计

- **基准测试**：
  - **安全性**：Harmbench（400个有害行为），报告防御成功率（DSR%），包含四个攻击：GCG（白盒）、AutoDAN（白盒）、PAIR（黑盒）、PAP（黑盒）。
  - **拒绝率**：XSTest（无害但容易被拒绝的提示）和WildChat（随机用户请求），使用StrongReject评估器。
  - **内部表征**：UMAP投影最后一层embedding，并训练软间隔SVM计算边界。
  - **推理长度分析**：Sorry-Bench（按主题分类有害性）。
- **对比方法**：
  - 开路断路器（Representation Re-routing，RR）
  - 前期推理防御（RealSafe-R1、SafeChain、Deliberative Alignment）
  - 开源模型（Llama-3.1-8B/1B-Instruct）
  - 控制实验：从相同πSFT出发，训练SFT、DPO、RL（无推理）做公平比较。
- **实验数量**：
  - 5种有害-无害比例（λ=0.1,0.3,0.5,0.7,0.9）
  - 7种基线对比
  - 多种消融：轻量SFT vs 重SFT、奖励设计（单独GRM vs 混合）、是否包含模糊提示
  - 攻击鲁棒性分析（格式破坏统计）
  - 内部表征分析
  - 跨域泛化实验（GSM8K、MATH-500等）

## 资源与算力

- **硬件**：4块NVIDIA A6000 GPU。
- **训练时长**：每个模型5-10小时（包括SFT和RL）。
- **基础模型**：Qwen-2.5-1.5B-Instruct（主要实验）和Qwen-2.5-7B-Instruct（旗舰模型）。
- **关键超参**：SFT阶段lr=3e-5, 3 epochs；RL阶段lr=1e-6, 3 epochs, batch size 32, 8次rollout, 最大生成长度4096 tokens。
- 论文未详细说明所有实验的总计算开销，但基于上述配置估计总训练量可控。

## 实验数量与充分性

- **充分性评估**：
  - 覆盖了安全-拒绝权衡的主要维度（不同混合比例、不同训练范式）。
  - 进行了广泛的消融研究，验证了三个关键设计的作用。
  - 包含了内部机制分析（表征分离）和对攻击的详细分析（格式破坏）。
  - 但局限性在于：仅在一个模型家族（Qwen-2.5）上验证，可能缺乏跨架构泛化性。此外，攻击实验仅调整了GCG针对推理段，对其他攻击的适应性可能不完整。
- **客观性与公平性**：对比实验严格控制变量（从相同πSFT初始、匹配训练计算），使用公开基准和自动评估工具，减少主观偏差。论文也指出对基准数据的污染问题（如XSTest）并采取了重训练措施。

## 论文主要结论与发现

1. **TARS实现了最佳的的安全-拒绝权衡**：在1.5B规模下超越7-8B的现有防御（如Llama-RR、Mistral-RR），7B版本更具优势。
2. **自适应推理行为**：模型在模糊提示上花费更多推理计算（更长的CoT），而在明显有害提示上推理较短，体现了按复杂度分配资源。
3. **内部表征更优**：TARS训练后，有害提示与无害提示的最后一层embedding分离边界更大，表明模型学会了内在区分。
4. **鲁棒性提升**：对白盒攻击（GCG）和黑盒攻击（PAIR）的防御成功率高于SFT/DPO和纯RL。即使在格式被攻击破坏时（如缺少</think>），仍能生成安全回答。
5. **轻量SFT和混合提示是关键**：过度SFT会导致多样性丧失和隧道效应；混合无害+模糊提示可有效防止奖励黑客行为并保持推理能力。

## 优点

- **方法创新**：将自适应推理与安全对齐有机结合，而非简单拒绝。
- **系统性设计**：包含数据混搭、奖励拆分、轻量预热等精巧工程，且通过全面消融验证。
- **开源可靠**：公开代码、模型和数据，便于复现和后续研究。
- **深入分析**：不仅报告性能指标，还分析了内部表征、推理长度调节、攻击下的格式破坏等机制，增强了方法的可解释性。

## 不足与局限

- **模型通用性有限**：仅基于Qwen-2.5系列训练和评估，在其他架构（如Llama、Mistral）上的表现未知。
- **攻击适应性**：实验中的GCG针对推理部分进行了特殊设计，对完全针对答案段的攻击可能不够全面；其他高级攻击（如多轮、提示操纵）未测试。
- **奖励模型依赖**：安全奖励依赖Moderation API，任务奖励依赖GRM，这些外部评判可能存在偏差或覆盖不足。
- **数据混合敏感**：不同λ值需要人工调节，且模糊提示的选取（OR-Bench）可能不涵盖所有真实场景。
- **单轮对话**：评估仅限于单轮交互，多轮语境下的推理防御效果未被探索。
- **计算资源相对较小**：1000+2000的提示规模，可能限制了泛化能力，更大量级数据的效果未知。

（完）
