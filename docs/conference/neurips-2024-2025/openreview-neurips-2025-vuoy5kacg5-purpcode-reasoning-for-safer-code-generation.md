---
title: "PurpCode: Reasoning for Safer Code Generation"
title_zh: PurpCode：面向更安全代码生成的推理
authors: "Jiawei Liu, Nirav Diwan, Zhe Wang, Haoyu Zhai, Xiaona Zhou, Kiet A. Nguyen, Tianjiao Yu, Muntasir Wahed, Yinlin Deng, hadjer Benkraouda, Yuxiang Wei, LINGMING ZHANG, Ismini Lourentzou, Gang Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=VUoY5kacG5"
tags: ["query:dg"]
score: 7.0
evidence: 通过红队测试生成代码生成的合成安全数据
tldr: 该论文提出PurpCode，一种面向安全代码生成的后训练方案。通过内部红队测试合成高质量高覆盖的诱导不安全行为提示，训练分两阶段：规则学习教会模型引用安全规则，强化学习通过多目标奖励机制优化安全性与实用性。实验表明模型能显著减少漏洞代码和不安全输出，同时保持代码质量。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-vuoy5kacg5/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1426, \"height\": 665, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vuoy5kacg5/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 433, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vuoy5kacg5/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1082, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vuoy5kacg5/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1342, \"height\": 875, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-vuoy5kacg5/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 588, \"height\": 288, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vuoy5kacg5/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 811, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vuoy5kacg5/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 673, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vuoy5kacg5/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1449, \"height\": 539, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vuoy5kacg5/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1457, \"height\": 575, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vuoy5kacg5/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1102, \"height\": 550, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vuoy5kacg5/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1460, \"height\": 772, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vuoy5kacg5/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 667, \"height\": 491, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vuoy5kacg5/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1457, \"height\": 737, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vuoy5kacg5/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1438, \"height\": 477, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vuoy5kacg5/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1452, \"height\": 890, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vuoy5kacg5/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 925, \"height\": 176, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vuoy5kacg5/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 561, \"height\": 469, \"label\": \"Table\"}]"
motivation: 现有代码生成模型缺乏安全保障，易生成含漏洞代码或协助恶意活动。
method: 通过红队测试合成安全数据，结合规则学习与强化学习两阶段训练安全推理模型。
result: 生成模型在漏洞减少和安全性方面显著提升，且保持实用性和推理能力。
conclusion: 合成安全数据和多目标强化学习可有效训练安全代码生成模型。
---

## Abstract
We introduce PurpCode, the first post-training recipe for training safe code reasoning models towards generating secure code and defending against malicious cyberactivities. PurpCode trains a reasoning model in two stages: (i) Rule Learning, which
explicitly teaches the model to reference cybersafety rules to generate vulnerability-free code and to avoid facilitating malicious cyberactivities; and (ii) Reinforcement Learning, which optimizes model safety and preserves model utility through diverse, multi-objective reward mechanisms. To empower the training pipelines with comprehensive cybersafety data, we conduct internal red-teaming to synthesize comprehensive and high-coverage prompts based on real-world tasks for inducing unsafe cyberactivities in the model. Based on PurpCode, we develop a reasoning-based coding model, namely PurpCode-32B, which demonstrates state-of-the-art cybersafety,
outperforming various frontier models. Moreover, our alignment method decreases the model overrefusal rates in both general and cybersafety-specific scenarios, while preserving model utility in both code generation and common security knowledge.

---

## 论文详细总结（自动生成）

好的，作为您的资深学术论文分析助手，现在为您呈上对论文《PurpCode: Reasoning for Safer Code Generation》的结构化总结。

---

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）在代码生成领域应用广泛，但缺乏有效的安全对齐。它们可能被滥用以生成含漏洞的代码，或直接协助恶意网络活动（如编写恶意软件、指导攻击执行）。
- **整体含义**：现有安全对齐方法（如传统RLHF）是反应式的，难以泛化到新场景；且简单拒绝可能带来过度拒绝（overrefusal）问题，损害模型实用性。论文旨在提出一种**主动式、基于推理的安全对齐方法**，使模型在生成代码时能主动进行网络安全推理（cybersafety reasoning），从而在保证安全性的同时，维持其代码生成能力。

### 2. 论文提出的方法论

- **核心思想**：**“教规则 + 练推理”**。区别于隐式学习安全模式，PurpCode采用两阶段训练流程，明确教会模型引用并应用具体的网络安全规则，然后通过强化学习让模型在不同场景下泛化运用这些规则。
- **关键技术细节**：
    1.  **规则学习 (Rule Learning)**：
        - **目标**：教授模型特定的网络安全规则（如CWE-20输入验证、CWE-78命令注入等）。
        - **方法**：
            - 使用内部红队生成的带有漏洞诱导的提示（prompt），并配备相应的安全规则。
            - 通过**拒绝采样 (Rejection Sampling)**，让模型生成包含安全推理轨迹（先分析意图、再列出规则、最后生成安全代码）的响应。
            - 只保留通过验证器的样本，用于**监督微调 (SFT)**，教会模型在思考过程中引用规则。
    2.  **强化学习 (Reinforcement Learning)**：
        - **目标**：让模型在更多样化的场景下泛化其安全推理能力，并避免过度拒绝。
        - **方法**：采用基于GRPO（Group Relative Policy Optimization）的RL算法。
        - **多目标奖励 (Multi-Objective Reward)**：设计了多类验证器（Oracle）：
            - **安全验证器**：使用代码分析器（如CodeGuru）检测漏洞代码；使用LLM判断器检测是否协助了恶意活动。
            - **实用验证器**：执行测试用例（pytest/stdin）检查代码正确性；使用LLM判断器检测是否过度拒绝。
            - **格式验证器**：确保输出格式正确。
        - **奖励机制**：为漏洞代码生成任务设置差异化奖励。生成安全代码且包含代码的得满分；拒绝但不提供代码的得部分奖励（0.8分），以避免模型因安全感而一味拒绝。
    3.  **内部红队 (Internal Red-Teaming)**：
        - **目的**：生成高质量、高覆盖率的诱导性样本，用于训练和评估。
        - **方法**：
            - **诱导漏洞代码**：从OSV数据库、开源数据集以及自研的`RULE2CODE`方法中提取/合成含漏洞代码，创建一个覆盖**90个不同CWE标识符**的种子库。然后通过`VUL2PROMPT`框架将漏洞代码转化为可诱导模型生成类似漏洞的自然语言指令。
            - **诱导恶意活动协助**：收集真实世界恶意请求和专家/LLM合成的恶意请求。
            - **越狱攻击**：对上述样本应用模板注入、黑盒搜索和多轮对话等越狱方法，以测试模型的鲁棒性。

- **算法流程简述**:
    1.  **数据准备**：通过`VUL2PROMPT`、`RULE2CODE`等方法，并结合公开数据集和内部红队，构建包含安全规则和提示的安全数据集。
    2.  **阶段一：规则学习**：对构建的数据集进行拒绝采样，保留高质量的、包含安全推理轨迹且经过验证器认证的`(prompt, response)`对，用于SFT。
    3.  **阶段二：强化学习**：在SFT后的模型上，使用GRPO算法，利用代码正确性执行器、安全分析器、过度拒绝判断器等多项验证器提供的反馈信号，进行多目标强化学习。训练中引入了单步动态采样和批量奖励计算以提升效率。

### 3. 实验设计

- **数据集与场景**：
    - **代码安全**：`CyberSecEval SCG`、`CodeLMSec`、`CWEval`。
    - **恶意事件协助**：`CyberSecEval MITRE`、大学红队数据（来自Amazon Nova AI Challenge）。
    - **过度拒绝 (Overrefusal)**：`CyberSecEval FRR`、自建`XSCode`、`XSTest`、`PHTest`。
    - **代码正确性 (Utility)**：`HumanEval+`、`MBPP+`。
- **Benchmark**：涵盖了代码安全、恶意协助、过度拒绝和代码实用性等多个维度的公开和自建基准。
- **对比方法**：
    - **前沿模型**：Anthropic的Claude Sonnet 4、OpenAI的o4-mini、Qwen系列（Qwen3-32B/235B）、DeepSeek-R1。
    - **安全对齐方法**：`SafeCoder`、`ProSec`。

### 4. 资源与算力

- **训练设备**：
    - 模型训练主要使用**NVIDIA H200 (8 × 144 GB)** GPU。
    - 恶意事件Oracle（判断器）部署在**NVIDIA H100 (8 × 80 GB)** GPU上。
    - 静态代码分析使用AWS CodeGuru（通过AWS信用额度执行）。
- **评估设备**：所有基线模型均在**H100** GPU上部署，以保持一致性。
- **总计算量**：论文未提供具体的GPU小时数或训练总时长，但描述了训练过程中涉及的主要硬件组合。

### 5. 实验数量与充分性

- **实验数量**：非常充分。
    - **主实验**：四大类别（代码安全、恶意协助、过度拒绝、代码正确性）共10余个基准测试，对比了6个以上的前沿模型和基线方法。
    - **消融实验**：单独对`Qwen2.5-14B-Instruct-1M`模型进行了全面的消融研究，分析了不同训练阶段（Base vs. Rule Learning vs. RL）、不同对齐方法（SafeCoder, ProSec）、不同动态采样方法（DAPO vs. Ours）的影响。
    - **32B模型的步骤验证**：也展示了PurpCode-32B在不同训练阶段的性能变化。
    - **跨语言泛化**：评估了模型在C/C++, Java, PHP, Rust等多种语言上的安全性。
- **充分性与公平性**：
    - **实验充分**：消融实验设计清晰，逐步验证了每个组件的贡献。
    - **客观公平**：
        - 所有对比模型在同一系统提示下进行评估。
        - 红队数据专门为攻击**作者自己的模型**设计，但作者仍将其作为评估其他模型的基准，保证了评估的挑战性。
        - 作者进行了数据去污染（decontamination），避免训练数据与测试基准重叠。
        - 验证器（如CodeGuru vs. CodeQL）的准确性也经过了比较分析。

### 6. 论文的主要结论与发现

1.  **领先的安全性**：PurpCode-32B在代码安全基准（如CyberSecEval SCG和CodeLMSec）上显著优于所有前沿模型，安全代码生成比率超过80%。
2.  **鲁棒的防御能力**：在面对专门针对防御模型设计的大学红队攻击时，PurpCode-32B的防御成功率比其他模型高35%以上。
3.  **有效的抗越狱攻击**：在模板、搜索和多轮对话等多种越狱攻击下，PurpCode-32B的防御成功率整体优于Qwen系列，并接近Anthropic的Sonnet 4。
4.  **较低的过度拒绝率**：与许多前沿模型相比，PurpCode-32B在不是真正有害但从字面看有风险的提示上，能更好地避免过度拒绝，在XSCode基准上达到了最高分。
5.  **保持模型实用性**：在评估代码正确性的HumanEval+和MBPP+基准上，PurpCode-32B的性能与基线模型相当，几乎没有损失。
6.  **验证了两阶段训练的有效性**：消融实验明确表明，规则学习和强化学习两个阶段对于最终的安全性提升都至关重要。

### 7. 优点

- **方法创新**：首次将“显式推理”引入网络安全对齐。不是简单地“拒绝”，而是教模型“如何判断”，这有助于泛化到新威胁。是“审慎对齐”（Deliberative Alignment）思想在网络安全领域的成功应用。
- **数据质量高**：通过`VUL2PROMPT`和`RULE2CODE`系统化地生成高质量、高覆盖率的合成训练数据（覆盖90个CWE），并公开了全部配方，可复现性强。
- **工程优化出色**：
    - 提出的**单步动态采样**解决了DAPO中样本浪费和启动开销的问题，提升了RL训练的效率和最终模型性能。
    - **批量奖励计算**显著加速了代码分析器（CodeGuru）的评估过程。
- **评估全面且严格**：不仅评估公开基准，还使用了在“红队攻击”竞赛中产生的、针对性极强的大学红队数据，确保了评估的高难度和客观性。
- **开源贡献**：完全开源了训练代码、数据、评估器，促进领域发展。

### 8. 不足与局限

- **缺乏多轮强化学习训练**：作者承认RL阶段只使用了单轮对话交互，这导致其在多轮越狱攻击下的表现存在优化空间。
- **代码安全覆盖不全**：依赖于静态分析工具CodeGuru的性能，可能无法覆盖所有类型的漏洞。论文也提到，对于某些CWE，只收集到有限的分析规则，覆盖率低于100%。
- **基准测试饱和**：在标准基准（如CyberSecEval MITRE）上，几乎所有对比模型都达到了接近饱和的性能，凸显了开发更具挑战性基准的必要性。
- **语言限制**：实验主要针对Python语言进行优化和评估，虽然对其他语言也有泛化效果，但安全性的提升幅度可能较低。
- **奖励设计的潜在偏差**：对于安全代码生成，不生成代码（即拒绝）只给部分奖励，这个0.8的系数是经验设定的，可能并非最优解，存在博弈空间。

---

（完）
