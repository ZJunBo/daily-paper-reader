---
title: "BackdoorAlign: Mitigating Fine-tuning based Jailbreak Attack with Backdoor Enhanced Safety Alignment"
title_zh: BackdoorAlign：通过后门增强安全对齐缓解微调越狱攻击
authors: "Jiongxiao Wang, Jiazhao Li, Yiquan Li, Xiangyu Qi, Junjie Hu, Yixuan Li, Patrick McDaniel, Muhao Chen, Bo Li, Chaowei Xiao"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=1PcJ5Evta7"
tags: ["query:smd"]
score: 9.0
evidence: 通过后门方式整合安全示例来防御微调越狱攻击
tldr: 针对基于微调的越狱攻击（FJAttack），该论文提出BackdoorAlign，在安全对齐阶段注入后门，使得后续微调中有害数据会触发安全机制，从而保持模型安全。该方法无需修改微调数据集，服务提供商只需在发布模型前进行一次后门增强。实验证明该方法能有效抵御多种有害微调攻击，且不影响正常任务性能。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-1pcj5evta7/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 762, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-1pcj5evta7/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1419, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-1pcj5evta7/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 528, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-1pcj5evta7/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 730, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-1pcj5evta7/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1394, \"height\": 361, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-1pcj5evta7/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 420, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-1pcj5evta7/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 605, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-1pcj5evta7/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 703, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-1pcj5evta7/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 499, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-1pcj5evta7/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 700, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-1pcj5evta7/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 517, \"height\": 299, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-1pcj5evta7/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 804, \"height\": 304, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-1pcj5evta7/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1443, \"height\": 473, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-1pcj5evta7/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 802, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-1pcj5evta7/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1418, \"height\": 1926, \"label\": \"Table\"}]"
motivation: 微调越狱攻击仅需少量有害示例即可破坏模型安全，现有防御效果有限。
method: 在安全对齐中注入后门，使模型在遇到有害数据时自动激活安全保护。
result: 在多个LLM和攻击设置下，BackdoorAlign显著降低攻击成功率，且对正常性能影响极小。
conclusion: 后门机制为抵御微调越狱提供了一种高效且用户透明的防御方案。
---

## Abstract
Despite the general capabilities of Large Language Models (LLMs) like GPT-4, these models still request fine-tuning or adaptation with customized data when meeting the specific business demands and intricacies of tailored use cases. However, this process inevitably introduces new safety threats, particularly against the Fine-tuning based Jailbreak Attack (FJAttack) under the setting of Language-Model-as-a-Service (LMaaS), where the model's safety has been significantly compromised by fine-tuning on users' uploaded examples that contain just a few harmful examples. Though potential defenses have been proposed that the service providers of LMaaS can integrate safety examples into the fine-tuning dataset to reduce safety issues, such approaches require incorporating a substantial amount of data, making it inefficient. To effectively defend against the FJAttack with limited safety examples under LMaaS, we propose the Backdoor Enhanced Safety Alignment method inspired by an analogy with the concept of backdoor attacks. In particular, service providers will construct prefixed safety examples with a secret prompt, acting as a "backdoor trigger". By integrating prefixed safety examples into the fine-tuning dataset, the subsequent fine-tuning process effectively acts as the "backdoor attack", establishing a strong correlation between the secret prompt and safety generations. Consequently, safe responses are ensured once service providers prepend this secret prompt ahead of any user input during inference. Our comprehensive experiments demonstrate that through the Backdoor Enhanced Safety Alignment with adding as few as 11 prefixed safety examples, the maliciously fine-tuned LLMs will achieve similar safety performance as the original aligned models without harming the benign performance. Furthermore, we also present the effectiveness of our method in a more practical setting where the fine-tuning data consists of both FJAttack examples and the fine-tuning task data.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：大型语言模型（LLM）在LMaaS（语言模型即服务）场景下，用户可通过上传微调数据集定制模型。但研究表明，仅需少量有害示例（如10个）的微调就能破坏模型的安全对齐（即Fine-tuning based Jailbreak Attack, FJAttack），导致模型输出有害内容，而现有将安全示例直接加入微调数据的防御方法需要大量数据，效率低下。
- **整体含义**：本文旨在提出一种高效、低成本的防御方法，在仅使用有限安全示例的情况下，有效抵御FJAttack，同时保持模型在良性任务上的正常表现。

## 2. 方法论
### 核心思想
- 借鉴后门攻击（backdoor attack）的高效性：少量毒化数据（含触发器）即可在模型中植入后门，使得触发器样本达成攻击目标。
- 将安全示例类比为“毒化数据”，将安全对齐目标类比为“攻击目标”，设计一个服务提供商掌握的“后门触发器”——一个秘密提示（secret prompt），通过微调建立该提示与安全响应之间的强关联。

### 关键技术细节
1. **秘密提示设计**：由随机生成的150个token组成，不改变语义，且隐蔽性强，用户难以猜测。
2. **预处理安全示例**：在每个安全示例（有害问题+安全回答）的系统提示前拼接该秘密提示，形成带触发器的安全数据集 \( D_{secret} \)。
3. **微调过程**：将用户上传的微调数据集 \( D \)（可能包含有害示例）与带触发器的安全数据集 \( D_{secret} \) 合并，进行条件微调。优化目标为最大化对两个数据集中回答的对数似然（公式(3)）。
4. **推理阶段**：服务提供商在用户输入前将该秘密提示作为系统提示的一部分，激活模型生成安全响应，同时不影响良性问题的正常回答。

### 算法流程（文字说明）
1. 服务提供商预先选择少量安全示例（如11个），在系统提示前添加秘密提示。
2. 接收用户上传的微调数据集（可能包含有害示例）。
3. 将上述两部分数据合并，进行全参数或参数高效微调。
4. 用户输入时，服务提供商在系统提示前自动插入秘密提示，模型输出安全回答。

## 3. 实验设计
### 使用的数据集/场景
- **主实验**：微调数据集为100个有害示例（`pure_bad`），安全示例为11个（按11个有害类别各选1个，来自Policy-Oriented Safety Evaluation Benchmarks）。
- **真实场景**：对话摘要（SAMSum数据集，1000例）+ 100有害示例；SQL生成（sql-create-context数据集，1000例）+ 100有害示例。
- **评估基准**：
  - 安全性：Policy-Oriented Safety Evaluation Benchmarks（11类，共275个测试题），使用危害分数（GPT-4评分1-5）和攻击成功率ASR（基于拒绝关键词列表）。
  - 良性性能：ARC-Challenge（5-shot准确率）、MMLU（5-shot准确率）、MT-bench（GPT-3.5评分）。

### 对比方法
- **无防御**：直接在有害数据上微调。
- **基线防御**：将原始安全示例（不含秘密提示）与有害数据混合微调。
- **本文方法**：BackdoorAlign（带秘密提示的安全示例混合微调）。

### 模型
- Llama-2-7B-Chat（开源，全参数微调，2×NVIDIA A100 80GB GPU）
- GPT-3.5-Turbo（闭源，使用OpenAI API微调，5个epoch，学习率乘子1）

## 4. 资源与算力
- **明确说明**：
  - Llama-2-7B-Chat：使用2×NVIDIA A100 80GB GPU进行全参数微调。
  - GPT-3.5-Turbo：使用OpenAI API，训练5个epoch。
  - **每个epoch平均训练时间**：无防御16.40秒，BackdoorAlign 18.77秒（仅多2秒）。
- **未明确说明**：总训练时长、GPU小时数等具体数值未给出。

## 5. 实验数量与充分性
- **实验组数**：
  - 主实验结果：2个模型 × 3种防御设置（无防御、基线、本文） × 安全性与良性指标。
  - 消融实验：安全示例选择方法（类别、随机、LLM生成）、秘密提示有无、长度变化（10~250 tokens）、语义提示（Llama2默认、GPT-4生成）、LoRA参数高效微调、成本效率分析（基线所需安全示例数量）、身份转换攻击防御。
  - 真实场景：2个任务 × 多种设置（无攻击、攻击、基线、本文）。
  - 总计约20+组对比实验。
- **充分性与客观性**：
  - 覆盖多种模型、攻击类型、防御设置、任务场景，实验设计全面。
  - 使用标准 benchmark（ARC、MMLU、MT-bench）和 GPT-4 评估安全性，减少人为偏差。
  - 但未报告误差棒（因计算成本高），略有局限。

## 6. 主要结论与发现
- **安全性显著提升**：仅用11个带秘密提示的安全示例，BackdoorAlign 在 Llama-2-7B-Chat 上将 ASR 从基线的 34.91% 降至 3.64%，在 GPT-3.5-Turbo 上从 60.00% 降至 14.91%，危害分数接近原始对齐模型。
- **良性性能保持**：在 ARC-Challenge、MMLU、MT-bench 上，本文方法性能与无防御模型相当，且不额外降低良性表现。
- **高效性**：基线防御需要 300 个安全示例才能达到本文 11 个示例的效果（成本高出27倍）。
- **泛化性**：对身份转换攻击、真实场景（对话摘要、SQL生成）同样有效；使用 LoRA 参数高效微调时仍保持优势。

## 7. 优点
- **创新性**：将后门攻击思想创造性用于防御，解决微调越狱攻击，思路新颖。
- **高效性**：只需极少量安全示例（11个），代价低，适合实际部署。
- **用户透明**：防御完全由服务提供商控制，用户无需更改输入，不影响正常使用。
- **鲁棒性强**：秘密提示为随机 token，用户难以猜测，可抵抗自适应攻击。
- **实验充分**：覆盖多种模型、攻击类型、任务场景，并进行了详尽的消融实验和成本分析。

## 8. 不足与局限
- **仍需少量安全示例**：虽然很少（11个），但引入额外微调开销和数据准备。
- **适用阶段限制**：本文方法针对已对齐模型的微调阶段，未探索能否扩展到预训练后的对齐训练（如RLHF），当前超出范围。
- **秘密提示隐蔽性风险**：若用户通过反复调用或逆向工程猜测出秘密提示，可能发起自适应攻击破坏防御。
- **未报告误差范围**：由于计算限制未提供统计误差，可能影响结论的稳定性验证。
- **仅验证特定模型和攻击设置**：泛化到其他模型架构（如Gemini、Claude）或更复杂的攻击方式尚需进一步验证。
- **未讨论对良性用户隐私的影响**：预加秘密提示可能增加系统提示长度，带来轻微推理成本增加。

（完）
