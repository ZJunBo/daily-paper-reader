---
title: Lifelong Safety Alignment for Language Models
title_zh: 大语言模型的终身安全对齐
authors: "Haoyu Wang, Yifei Zhao, Zeyu Qin, Chao Du, Min Lin, Xueqian Wang, Tianyu Pang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=9YkEcAqiIK"
tags: ["query:smd"]
score: 5.0
evidence: 通过元攻击者和防御者的终身安全对齐来防御有害微调攻击
tldr: 论文针对现有防御仅针对已知攻击的局限，提出终身安全对齐框架。该框架包含元攻击者和防御者两个组件，元攻击者持续探索新的越狱策略，防御者则学习抵抗这些攻击。通过对抗式竞争，模型能够不断适应部署过程中出现的新型攻击。实验表明该方法能有效提升对未知越狱策略的鲁棒性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-9ykecaqiik/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9ykecaqiik/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1422, \"height\": 1435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9ykecaqiik/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1443, \"height\": 379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9ykecaqiik/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1448, \"height\": 555, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-9ykecaqiik/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1451, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9ykecaqiik/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1329, \"height\": 1695, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9ykecaqiik/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1114, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9ykecaqiik/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1112, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9ykecaqiik/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1463, \"height\": 157, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9ykecaqiik/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1116, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9ykecaqiik/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1109, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9ykecaqiik/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1450, \"height\": 314, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9ykecaqiik/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1229, \"height\": 888, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9ykecaqiik/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1210, \"height\": 112, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9ykecaqiik/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1290, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9ykecaqiik/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1290, \"height\": 299, \"label\": \"Table\"}]"
motivation: 现有安全对齐防御主要针对已知攻击类型，但部署过程中可能出现未知的越狱策略，需要持续适应的能力。
method: 提出终身安全对齐框架，包含元攻击者（主动发现新越狱策略）和防御者（学习抵抗攻击），通过对抗训练不断更新。
result: 该方法能有效提升模型对未知越狱策略的鲁棒性，实验显示在多种攻击下安全性显著提高。
conclusion: 终身安全对齐是实现大语言模型长期安全的关键方向，能应对不断演化的攻击威胁。
---

## Abstract
LLMs have made impressive progress, but their growing capabilities also expose them to highly flexible jailbreaking attacks designed to bypass safety alignment. While many existing defenses focus on known types of attacks, it is more critical to prepare LLMs for *unseen* attacks that may arise during deployment. To address this, we propose a **lifelong safety alignment** framework that enables LLMs to continuously adapt to new and evolving jailbreaking strategies. Our framework introduces a competitive setup between two components: a **Meta-Attacker**, trained to actively discover novel jailbreaking strategies, and a **Defender**, trained to resist them. To effectively warm up the Meta-Attacker, we first leverage the GPT-4o API to extract key insights from a large collection of jailbreak-related research papers. Through iterative training, the first iteration Meta-Attacker achieves a 73% attack success rate (ASR) on RR and a 57% transfer ASR on LAT using only *single-turn* attacks. Meanwhile, the Defender progressively improves its robustness and ultimately reduces the Meta-Attacker's success rate to just 7%, enabling safer and more reliable deployment of LLMs in open-ended environments.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：现有大语言模型（LLM）的安全对齐防御大多针对**已知攻击类型**进行训练，并保持静态部署，这导致模型在面对部署过程中出现的**未知、不断演化**的越狱（jailbreaking）策略时表现脆弱。例如，GPT-4-1106（2023年11月发布）在2024年3月被CodeAttack攻破，说明静态防御无法应对新威胁。
- **动机**：需要一种**终身安全对齐**机制，使LLM能够持续适应新出现的攻击策略，实现从“一次性对齐”到“持续演化”的转变。
- **整体含义**：本文提出一个对抗性博弈框架，通过元攻击者（Meta-Attacker）主动探索新越狱策略，防御者（Defender）学习抵抗这些策略，从而在动态环境中保持安全。

## 2. 方法论：核心思想、技术细节、算法流程

- **核心思想**：将安全对齐形式化为元攻击者与防御者之间的**对抗性演化竞争**（Adversarial-Play Evolution）。元攻击者持续生成新的越狱策略，防御者通过拒绝训练吸收这些攻击样本，双方交替升级。
- **技术细节**：
  - **热身阶段**：使用GPT-4o API从10篇越狱相关研究论文中提取攻击策略，形成策略池。利用提取的策略，用强推理模型DeepSeek-R1-Distill-Qwen-32B（记为A0）针对目标（4k个非法指令）生成具体的越狱问题，并攻击初始防御者RR（M0）。成功样本存入Bs，失败样本存入Bf。
  - **元攻击者演化（F1过程）**：
    1. 分析Bf中的失败原因，提出新策略s'和新问题x'，使用Best-of-N（N=8）采样生成8个候选。
    2. 攻击目标模型，用安全裁判（LLaMA-Guard-3-8B + Qwen2.5-72B）判断。
    3. 成功样本加入Bs，失败样本加入Bf（累积经验）。
    4. 重复迭代，直到成功攻击目标比例达到阈值K（95%）或达到最大交互次数N（5次）。
    5. 在过程中进行两次拒绝微调（RFT）：中间点和结束时，用Bs中的样本微调元攻击者，获得更强版本（A't, A''t）。
  - **防御者演化（F2过程）**：
    1. 从Bs中获取成功攻击的越狱问题x，用拒绝生成模型Mr（LLaMA-3-8B）产生拒绝回答yr，构成安全对齐数据集D。
    2. 对初始防御者M0进行拒绝训练（加上有用性保持数据Ultrachat和XSTest），得到新的防御者Mt+1。
  - **终身迭代**：整个过程（F1+F2）构成一次完整迭代。本文进行了2次迭代（T=2）。
- **算法流程**（Alg.1）：for t in 0..T-1: At+1 = F1(g, At, Mt, Mj, Bf, Bs, K, N); Mt+1 = F2(M0, Mr, Bs, D)

## 3. 实验设计

- **数据集**：
  - **目标池G**：来自PKU-SafeRLHF的4k条非法指令（另选100条作为测试目标）。
  - **有用性维持数据集**：Ultrachat（20k条QA）。
  - **过度拒绝缓解**：XSTest（250个安全提示+200个不安全提示）。
- **基准（Baseline）**：
  - 防御者：RR（Circuit Breakers, LLaMA-3-8B变体）和LAT（Latent Adversarial Training, LLaMA-3-8B变体）。
  - 攻击：10篇输入论文代表的攻击（如CodeAttack, Emoji Attack等）作为**seen attacks**；元攻击者自身生成的策略作为**unseen attacks**；其他未在热身中出现的攻击（AutoDAN, FewShot, UAT, AutoPrompt, Simple Adaptive Attack）作为**generalization attacks**。
- **对比方法**：直接对比RR和LAT的原始鲁棒性与经终身安全对齐后的版本（M1, M2）；测试元攻击者对不同防御者的迁移攻击能力。
- **评估指标**：攻击成功率（ASR），由LLaMA-Guard-3-8B + Qwen2.5-72B裁判联合判定。有用性评估使用lm-evaluation-harness的10个任务（MMLU, GSM8K, HumanEval等）。

## 4. 资源与算力

- 总计算量：约 **300 A100 40G GPU小时**（使用R1-32B和Qwen2.5-72B配置）。若改用R1-7B和Qwen2.5-7B，约需75小时。
- GPT-4o策略挖掘：10篇论文各采样50次，共500次，平均输出530 token，约0.27M输出token。
- DeepSeek-R1-32B的Best-of-N（N=8）采样：使用8张A100 40G，约2小时。
- 元攻击者微调（LoRA）：约2小时，8张A100 40G。
- 防御者微调：约1.5小时，8张A100 40G。

## 5. 实验数量与充分性

- **实验数量**：覆盖3类安全评估（seen 6种攻击，unseen 1种（由元攻击者生成），generalization 5种攻击），有用性评估10个任务。消融实验包括元攻击者模型大小（7B/14B/32B）、训练数据选择（全部成功样本 vs 单一成功样本）、模型类型（指令跟随模型 vs 推理模型）。
- **充分性**：实验设计较全面，涵盖了多种已知和未知攻击场景，并在两个不同防御模型（RR和LAT）上验证了迁移性。但迭代次数仅2次，对更长期演化的稳定性评估不足；自动裁判虽有校正，但未完全依赖人工评估，可能存在少量误判。
- **客观公平**：使用了公开数据集和基准模型，裁判采用两级过滤（安全分类+LLM评分），并进行了人工抽样检查，总体较为客观。

## 6. 主要结论与发现

- 元攻击者在第一次迭代后获得73% ASR（对RR），并能发现如“系列间接与技术框架”等与先进多轮攻击相似的策略。
- 防御者通过两次迭代，对元攻击者的ASR从55%降至7%；对输入论文中的seen攻击完全防御（0% ASR）。
- 对泛化攻击（Simple Adaptive Attack）的ASR从100%降至38%。
- 有用性方面，经终身安全对齐后模型的平均性能基本保持（约56%），优于LAT（47%）。
- 消融表明：使用推理型模型（DeepSeek-R1）作为元攻击者显著优于指令跟随模型；用全部成功样本微调比只用单一样本更好；32B模型在攻击成功率上表现稳定。

## 7. 优点（方法或实验设计亮点）

- **新颖的终身对抗框架**：首次将对抗性博弈引入安全对齐，使模型能自动探索新攻击而无需人工定义攻击类型。
- **利用文献知识热身**：通过GPT-4o从论文中提取策略，显著降低冷启动难度。
- **双裁判机制**：将轻量安全分类器与大型LLM评分结合，提高评估可靠性。
- **全面的消融实验**：系统研究了元攻击者模型大小、训练数据选择、推理能力的影响，对后续工作有指导意义。
- **关注有用性保持**：在训练中包含Ultrachat和XSTest，防止过度拒绝影响模型可用性。

## 8. 不足与局限

- **迭代深度有限**：仅进行2次迭代，未深入探索长期演化中的灾难性遗忘问题（作者在局限部分也承认）。
- **训练方法单一**：仅采用SFT/RFT，未尝试强化学习（如RLVR），后者可能在策略探索和稳定性上更优。
- **依赖API模型**：热身阶段依赖GPT-4o提取策略，这引入额外成本和潜在的信息损失，且无法保证完全复现。
- **自动裁判偏差**：尽管用了两级裁判，但仍无法完全替代人工评估，尤其对边界案例可能误判。
- **泛化能力待验证**：防御者对抗新攻击的泛化能力仅在有限设置下测试，且未在更大规模模型（如70B+）上实验。
- **算力需求高**：完整复现需300 A100小时，对资源有限的研究团队门槛较高。
- **目标池固定**：使用PKU-SafeRLHF的4k指令，可能未覆盖所有有害领域，导致策略多样性受限。

（完）
