---
title: "WildTeaming at Scale: From In-the-Wild Jailbreaks to (Adversarially) Safer Language Models"
title_zh: WildTeaming大规模：从野生越狱到对抗性更安全的语言模型
authors: "Liwei Jiang, Kavel Rao, Seungju Han, Allyson Ettinger, Faeze Brahman, Sachin Kumar, Niloofar Mireshghallah, Ximing Lu, Maarten Sap, Yejin Choi, Nouha Dziri"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=n5R6TvBVcX"
tags: ["query:smd"]
score: 6.0
evidence: 通过红队测试生成对抗性越狱数据，可作为安全数据用于微调以增强鲁棒性。
tldr: 本文提出WildTeaming，自动从真实用户交互中挖掘新颖越狱策略，并组合生成更具挑战性的对抗样本。这些对抗性数据可为微调过程提供丰富的安全对齐数据，通过整合到微调数据集中，帮助模型抵御越狱攻击，缓解安全退化。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5r6tvbvcx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5r6tvbvcx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1387, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5r6tvbvcx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1462, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5r6tvbvcx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 864, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5r6tvbvcx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1120, \"height\": 2251, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5r6tvbvcx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1453, \"height\": 1004, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5r6tvbvcx/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1418, \"height\": 992, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5r6tvbvcx/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1449, \"height\": 1856, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5r6tvbvcx/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 654, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5r6tvbvcx/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1463, \"height\": 1915, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 973, \"height\": 640, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1388, \"height\": 935, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 752, \"height\": 391, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1511, \"height\": 623, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1810, \"height\": 2277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1855, \"height\": 2048, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1639, \"height\": 1461, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1493, \"height\": 710, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1461, \"height\": 856, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1449, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1438, \"height\": 1401, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1628, \"height\": 2212, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1635, \"height\": 2050, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1631, \"height\": 2315, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1682, \"height\": 2354, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1679, \"height\": 2255, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1684, \"height\": 1955, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1503, \"height\": 827, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1260, \"height\": 354, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1456, \"height\": 874, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1518, \"height\": 1332, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1519, \"height\": 813, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1536, \"height\": 1049, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 502, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1764, \"height\": 999, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 447, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1427, \"height\": 566, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 451, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1610, \"height\": 382, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1427, \"height\": 478, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 1281, \"height\": 445, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 854, \"height\": 439, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-033.webp\", \"caption\": \"\", \"page\": 0, \"index\": 33, \"width\": 1280, \"height\": 387, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-034.webp\", \"caption\": \"\", \"page\": 0, \"index\": 34, \"width\": 1423, \"height\": 425, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-035.webp\", \"caption\": \"\", \"page\": 0, \"index\": 35, \"width\": 852, \"height\": 386, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-036.webp\", \"caption\": \"\", \"page\": 0, \"index\": 36, \"width\": 902, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-037.webp\", \"caption\": \"\", \"page\": 0, \"index\": 37, \"width\": 1474, \"height\": 462, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-038.webp\", \"caption\": \"\", \"page\": 0, \"index\": 38, \"width\": 1329, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-039.webp\", \"caption\": \"\", \"page\": 0, \"index\": 39, \"width\": 1468, \"height\": 1075, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-040.webp\", \"caption\": \"\", \"page\": 0, \"index\": 40, \"width\": 1324, \"height\": 1054, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5r6tvbvcx/table-041.webp\", \"caption\": \"\", \"page\": 0, \"index\": 41, \"width\": 891, \"height\": 1027, \"label\": \"Table\"}]"
motivation: 现有红队方法覆盖不到野生环境中的多样越狱策略。
method: 从用户-聊天机器人交互中挖掘越狱簇，并组合生成新攻击。
result: 发现大量先前未知的漏洞，生成的对抗数据显著提高模型安全性。
conclusion: WildTeaming为生成高质量安全数据提供了有效手段，可用于微调中的安全数据集成。
---

## Abstract
We introduce WildTeaming, an automatic red-teaming framework that mines in-the-wild user-chatbot interactions to discover 5.7K unique clusters of novel jailbreak tactics, and then composes selections of multiple mined tactics for systematic exploration of novel and even more challenging jailbreaks.
Compared to prior work that performed red-teaming via recruited human workers, gradient-based optimization, or iterative revision with large language models (LLMs), our work investigates jailbreaks from chatbot users in-the-wild who were not specifically instructed to break the system.  WildTeaming reveals previously unidentified vulnerabilities of frontier LLMs, resulting in more diverse and successful adversarial attacks compared to state-of-the-art jailbreaking methods. 

While there exist many datasets for jailbreak evaluation, very few open-source datasets exist for jailbreak training, as safety training data has been closed among all frontier models even when their weights are open. Therefore, with WildTeaming we create WildJailbreak, a large-scale open-source synthetic safety dataset with 262K vanilla (direct request) and adversarial (complex jailbreak) prompt-response pairs. In order to mitigate exaggerated safety behaviors, WildJailbreak provides two contrastive types of queries: 1) harmful queries (both vanilla and adversarial) and 2) benign queries that resemble harmful queries in form but contain no harmful intent. As WildJailbreak considerably upgrades the quality and scale of existing safety resources, it uniquely enables us to examine the scaling effects of data and the interplay of data properties and model capabilities during safety training. Through extensive model training and evaluations, we identify the training properties that enable an ideal balance of safety behaviors: appropriate safeguarding without over-refusal, effective handling of both vanilla and adversarial queries, and minimal, if any, decrease in general capabilities. All the components of WildJailbreak contribute to achieving balanced safety behaviors of models

---

## 论文详细总结（自动生成）

# WildTeaming at Scale: 论文详细总结

## 1. 论文的核心问题与整体含义

*   **研究动机**：大型语言模型（LLM）虽然经过安全对齐，但仍易受到对抗性越狱（jailbreak）攻击。现有的红队测试方法（如人工红队、梯度优化、LLM迭代改写）覆盖的越狱策略有限，且依赖于封闭或小规模的安全训练数据。
*   **核心问题**：如何系统化地发现真实世界中多样且新颖的越狱策略，并利用这些策略生成大规模、高质量的对抗性安全训练数据，从而在不损害模型通用能力的前提下，提升模型对直接有害请求和复杂越狱请求的鲁棒性，同时避免过度拒绝（over-refusal）。
*   **整体含义**：本文提出了一套完整的“挖掘-组合-训练”框架，从真实用户与聊天机器人的交互中自动挖掘越狱策略，通过组合策略生成更多样化的对抗攻击，并据此创建了迄今为止最大规模的开源安全数据集WildJailbreak（26.2万条）。实验证明，该数据集能显著提升模型的安全性，且对通用能力影响极小，为开源安全训练提供了关键资源。

## 2. 论文提出的方法论

*   **核心思想**：采用两阶段流程：
    1.  **MINE（挖掘）**：从真实世界用户-聊天机器人日志中自动挖掘人类设计的越狱策略。
    2.  **COMPOSE（组合）**：将挖掘到的策略与原始有害请求组合，生成多样化的对抗攻击。
*   **关键技术细节**：
    *   **MINE阶段**：
        *   从LMSYS-Chat-1M和WildChat中收集被OpenAI Moderation API标记的对抗性用户提示。
        *   通过轻量安全模型（Tulu2-7B）筛选出能引发有害响应的提示，获得16,850条候选。
        *   人工检查200条样本，识别出35个种子越狱策略及定义。
        *   利用GPT-4自动扩展挖掘：对每条对抗性提示，GPT-4提取核心有害请求并识别其中的越狱策略（包括已有和新的），并输出对应摘录、定义和推理。通过句子嵌入聚类去重（阈值0.75），最终得到5,688个独特策略簇，共计105,438条策略实例。
    *   **COMPOSE阶段**：
        *   从策略池中随机采样n个策略（例如固定一个“种子引导句”策略，再随机选3个），使用攻击模型（Mixtral-8×7B或GPT-4）将原始简单有害请求改写为对抗性攻击。
        *   应用两个轻量级过滤器：**离题分类器**（基于NLI判断是否与原意矛盾）和**低风险分类器**（基于内部有害性分类器判断风险是否足够高），只保留既不离题又不低风险的攻击候选。
        *   生成的攻击可直接用于黑盒或白盒目标模型，无需与目标模型交互。
*   **公式**（文字说明）：对抗性攻击AP_i ~ M_attack(·|P; T_i)，其中P是原始有害提示，T_i是采样的策略子集。是否保留AP_i由两个过滤器的联合结果决定：is_keep = 1 if (off-topic=False and low-risk=False)。

## 3. 实验设计

*   **使用的数据集/场景**：
    *   越狱攻击实验：采用HarmBench标准测试集（159条标准有害行为）作为攻击目标，评估WILD TEAMING的攻击成功率（ASR）和多样性。
    *   安全训练实验：使用Tulu2Mix（30万条通用指令数据）与WildJailbreak（26.2万条）混合，训练Llama2-7B模型。对比原始Tulu2Mix、去除拒绝的Tulu2Mix、现有公开安全数据（HH-RLHF、Safe-RLHF、DAN等）训练的模型。
*   **Benchmark**：
    *   通用能力：AlpacaEval V1/V2、MTBench、MMLU、GSM8K、BBH、TydiQA、CodexEval、TruthfulQA等。
    *   安全性：HarmBench（直接有害请求）、ToxiGen、XSTest（过度拒绝）、JailbreakTrigger、Do-Anything-Now、WildJailbreak自建评估集（2000条有害对抗+250条良性对抗）。
*   **对比方法**：
    *   越狱攻击：GCG（梯度优化）、AutoDAN（遗传算法）、PAIR（迭代语义改写）。
    *   安全训练：原始Tulu2Mix、无拒绝Tulu2Mix、公开安全数据混合（HH-RLHF+Safe-RLHF+DAN）、以及WildJailbreak各组件消融（仅有害、仅良性、仅普通、仅对抗等）。

## 4. 资源与算力

论文中并未明确报告所有实验的具体GPU型号与训练时长。但在实验设置部分提到：
*   安全训练实验在**128-chip TPU v3 pod**上运行。
*   训练超参数：BF16精度、2个epoch、学习率2e-5、batch size 32、最大序列长度2048。
*   越狱攻击实验：使用了NVIDIA RTX A6000 GPU，但未给出完整训练时长。WildTeaming生成一次攻击约8.54秒（单次），较PAIR（28.55秒）和GCG（2400秒）更快。
*   **注意**：文中未提供安全训练完整实验的总GPU/TPU时长，也未提供消融实验的具体硬件配置。

## 5. 实验数量与充分性

*   **实验数量**：论文进行了大量实验，主要包括：
    *   越狱攻击有效性对比：5种模型×4种方法×标准+多样性指标。
    *   规模消融：不同策略数量（1-6个）、修剪策略（无/离题/低风险/组合）。
    *   安全训练消融：不同数据组分（有害/良性、普通/对抗）及不同数据量（2K-60K）与150K通用数据混合。
    *   全模型对比：包括多个开源/闭源模型（共24个模型变体）的零样本越狱评估。
    *   完整结果表：包括通用能力、普通安全、对抗安全共15个以上任务的细粒度结果（见附录）。
*   **充分性与公平性**：
    *   实验覆盖了多种模型规模（2B-70B开源及GPT-3.5/4系列），对比了3种主流攻击方法和多种安全训练基线。
    *   消融实验系统全面地检验了各组件必要性。
    *   评价指标多样（ASR、多样性指标、通用能力），且采用标准化工具（HarmBench分类器、GPT-4评判）。
    *   不足：部分实验（如规模缩放）仅使用了一半的Tulu2Mix数据（150K）而非完整300K，可能影响通用能力对比；越狱攻击仅基于HarmBench标准行为，未覆盖所有风险类别（如上下文、版权行为等）；安全训练数据由GPT-4/Mixtral合成，可能继承模型偏见。

## 6. 论文的主要结论与发现

1.  **WildTeaming能发现更多样的漏洞**：与PAIR相比，在相同攻击尝试次数下，WildTeaming能识别出多达4.6倍更多独特成功攻击，且攻击文本更自然（困惑度更低）。
2.  **WildJailbreak显著提升模型安全性**：在Tulu2-7B上，加入WildJailbreak训练后，HarmBench标准ASR从59.1%降至3.1%，同时MTBench得分从5.84提升到6.29，说明安全性提升且通用能力不降反升。
3.  **数据组分至关重要**：仅使用有害数据会导致过度拒绝；仅使用普通/对抗数据则不能同时防御两者；只有四种数据（普通有害、普通良性、对抗有害、对抗良性）全部存在时才能达到最佳平衡。
4.  **安全数据规模越大效果越好**：在15万通用数据基础上，逐步增加安全数据（2K到60K），模型安全性能持续提升（满意率从约70%升至>95%），且通用能力未明显下降。
5.  **混合训练优于单一类型**：同时训练普通和对抗数据比只训练一种更鲁棒。

## 7. 优点

*   **方法创新**：首次系统地从真实用户交互中挖掘越狱策略，而非人工编写或优化，挖掘出的5.7K独特策略簇远超过往工作。组合策略生成攻击的方式既高效又多样。
*   **结果全面**：不仅展示攻击能力，更提供了大规模开源安全训练数据集（26.2万条），填补了开源安全数据的空白。
*   **实验严谨**：设计新型多样性指标（ASR×i、Query×i、Sim等），并进行了全面的消融实验，验证各组件必要性。安全训练实验涵盖15+任务，对比了多种现有安全数据集。
*   **实用性强**：方法计算成本低（无需梯度或迭代优化），可快速扩展；最终训练出的模型在安全与通用能力间取得了良好平衡。
*   **开放贡献**：代码、数据和模型均已开源，促进社区安全研究。

## 8. 不足与局限

*   **数据来源局限**：越狱策略仅来自LMSYS-Chat-1M和WildChat两个来源，可能无法涵盖所有真实用户的攻击手法（例如多轮对话中的越狱、编程模式、非英语语言等）。
*   **合成数据偏差**：WildJailbreak中的对抗提示由GPT-4/Mixtral生成，可能继承其风格和偏见，不完全等同于真实用户书写的越狱提示。
*   **评估覆盖有限**：攻击评估仅基于HarmBench标准行为（159条），未充分测试上下文、版权、多模态等更复杂场景。安全评估也仅限于特定基准，可能遗漏某些不当行为。
*   **安全训练局限性**：安全训练只能缓解部分风险，对于高度依赖上下文的危害，必须依靠外部安全层。另外，训练数据中仅包含拒绝响应，未探索偏好对训练的潜力。
*   **算力报告不完整**：未提供完整训练任务的GPU/TPU时长，影响复现准确性。
*   **未见跨模型泛化测试**：训练仅基于Llama2-7B，未验证WildJailbreak在其他架构或更大模型上的效果。
*   **过度拒绝评估依赖XSTest**：XSTest的类别可能不够全面，真实世界中无害但易被拒绝的请求可能更多样。

（完）
