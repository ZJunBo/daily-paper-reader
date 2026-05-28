---
title: "MetaDefense: Defending Fine-tuning based Jailbreak Attack Before and During Generation"
title_zh: MetaDefense：在生成前后防御基于微调的越狱攻击
authors: "Weisen Jiang, Sinno Jialin Pan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=ycMpNwzUAA"
tags: ["query:smd"]
score: 9.0
evidence: 通过训练有害性检测来防御基于微调的越狱攻击
tldr: MetaDefense针对基于微调的越狱攻击提出一种两阶段防御框架：在生成前检测有害查询，在生成中监控部分响应。该方法通过训练语言模型预测查询和部分回复的有害程度，实现了对未知攻击模板的泛化防御。实验表明其能有效阻止微调攻击导致的越狱行为，提升了LLM在微调场景下的安全性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ycmpnwzuaa/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1373, \"height\": 596, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ycmpnwzuaa/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 536, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ycmpnwzuaa/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1425, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ycmpnwzuaa/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1465, \"height\": 552, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ycmpnwzuaa/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1428, \"height\": 1151, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1354, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1376, \"height\": 1783, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1383, \"height\": 467, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1380, \"height\": 467, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1152, \"height\": 202, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 794, \"height\": 436, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1084, \"height\": 432, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1419, \"height\": 1836, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1419, \"height\": 1841, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1295, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1195, \"height\": 432, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1467, \"height\": 471, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1421, \"height\": 438, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1048, \"height\": 219, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1428, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1422, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1417, \"height\": 189, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1411, \"height\": 436, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1421, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1371, \"height\": 176, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1381, \"height\": 233, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ycmpnwzuaa/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1427, \"height\": 258, \"label\": \"Table\"}]"
motivation: 现有关防御方法无法泛化到由未见攻击模板伪装的有害查询。
method: 提出两阶段防御：生成前检测有害查询，生成中监控部分回复，训练语言模型预测有害程度。
result: MetaDefense能有效防御基于微调的越狱攻击，泛化到未知攻击模板。
conclusion: 两阶段防御策略显著提升了语言模型在微调场景下的安全性。
---

## Abstract
This paper introduces MetaDefense, a novel framework for defending against finetuning-based jailbreak attacks in large language models (LLMs). 
We observe that existing defense mechanisms fail to generalize to harmful queries disguised by unseen attack templates, despite LLMs being capable of distinguishing disguised harmful queries in the embedding space. 
Based on these insights, we propose a two-stage defense approach: 
(i) pre-generation defense that detects harmful queries before response generation begins, and (ii) mid-generation defense that monitors partial responses during generation to prevent outputting more harmful content. 
Our MetaDefense trains the LLM to predict the harmfulness of both queries and partial responses using specialized prompts, enabling early termination of potentially harmful interactions. 
Extensive experiments across multiple LLM architectures (LLaMA-2-7B, Qwen-2.5-3B-Instruct, and LLaMA-3.2-3B-Instruct) demonstrate that MetaDefense significantly outperforms existing defense mechanisms, achieving robust defense against harmful queries with seen and unseen attack templates while maintaining competitive performance on benign tasks.
Code is available at [https://github.com/ws-jiang/MetaDefense](https://github.com/ws-jiang/MetaDefense).

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究背景**：大型语言模型（LLM）的微调虽能提升特定任务性能，但引入了严重的安全风险——基于微调的越狱攻击（FJAttack）。攻击者通过在微调数据中混入少量有害样本（甚至使用未见过的攻击模板，如前缀注入、拒绝抑制、角色扮演），可破坏对齐机制，使LLM产生有害输出。
- **核心问题**：现有防御方法（如对齐阶段疫苗接种、微调阶段干预）在面对**未见过攻击模板**（unseen attack templates）伪装的有害查询时，几乎完全失效。论文通过实验发现：即使现有防御失败，LLM在嵌入空间中实际上能有效区分有害查询（无论模板是否见过）与良性查询。因此，防御失败的根源不在于模型“无法识别”，而在于“未能激活识别能力”。
- **整体含义**：本文旨在利用LLM自身的生成能力，设计一个统一、轻量、可泛化的防御框架，在生成前和生成中两个阶段动态检测有害性，从而防御未知模板下的微调越狱攻击。

### 2. 方法论：核心思想、关键技术细节

- **核心思想**：通过轻量级指令微调（instruction tuning），让LLM学会对查询和部分响应输出“harmful”或“harmless”标签，从而在不增加额外模型的前提下实现两阶段防御。
- **关键技术细节**：
  - **预生成防御（Pre-generation Defense）**：在输入查询后附加特定防御提示 `Tpre = "Is this query harmful or harmless? It is 100%" `，训练LLM在解码起始词时选择“harmful”或“harmless”。如果P("harmful") > P("harmless")，则直接拒绝，返回安全提醒。
  - **生成中防御（Mid-generation Defense）**：在生成过程中，每隔k个token（k动态取决于模型的置信度：`k = γ * P("harmless")`）暂停，附加提示 `Tmid = "Is this response harmful or harmless? It is 100%"` 对已生成的部分响应进行检测。若预测为有害，立即终止生成并返回安全提醒；否则继续，直到生成完整响应。
  - **训练数据**：基于对齐数据集构建预生成防御数据集Dpre（包括有害+拒绝响应对和良性对）以及生成中防御数据集Dmid（从有害响应对的中间截断构造）。联合最小化下一个token预测损失。
- **算法流程**：
  1. 训练阶段：通过SFT联合训练两个防御能力，损失函数为Dpre∪Dmid上的交叉熵。
  2. 推理阶段：对查询x'，先重用KV-Cache进行预生成防御；若通过，则开始生成，并周期性进行生成中防御（自适应间隔），在检测到有害时立即停止。

### 3. 实验设计：数据集、Benchmark、对比方法

- **数据集**：
  - 对齐阶段：2500个有害查询+有害响应（DHF-HF）、2500个有害查询+拒绝响应（DHF-HL）、5000个良性查询+响应（取自Alpaca）。
  - 微调/攻击阶段：良性任务选用SST2（情感分类）、AGNews（多选分类）、GSM8K（数学开放生成）；攻击时按比例p（默认10%）混入带有未见过模板的有害样本。
  - 攻击模板：Direct（见过）、Prefix Injection、Refusal Suppression、Role Play（后三种对齐阶段未见过）。
- **Benchmark**：主要指标为攻击成功率（ASR，越低越好）和微调测试准确率（FTA，衡量良性任务性能）。
- **对比方法**：
  - 无对齐（Non-Aligned）
  - SFT对齐（vanilla）
  - 对齐阶段：RepNoise、Vaccine、Booster
  - 微调阶段：BackdoorAlign、PTST
  - 推理阶段：LLM-Classifier（额外LLM作分类器）
  - 混合阶段：Booster + LLaMA-Guard
- **模型**：LLaMA-2-7B（非对话）、Qwen-2.5-3B-Instruct、LLaMA-3.2-3B-Instruct（对话模型）。

### 4. 资源与算力

论文明确说明：所有实验在**NVIDIA L40S 40G GPU**上运行。采用LoRA进行微调（rank=32，alpha=4），使用AdamW优化器。对于不同模型，对齐训练轮次分别为20（LLaMA-2-7B）、5（Qwen-2.5-3B-Instruct）、3（LLaMA-3.2-3B-Instruct）；微调阶段统一20轮。未给出总GPU耗时或具体卡数，但可认为计算资源中等。

### 5. 实验数量与充分性

- **主实验**：在3个模型 × 3个良性任务 × 4种攻击模板 = 36组对比（每个对比方法均有结果）。此外报告了预/生成防御的消融实验、有害概率分布可视化、超参数γ敏感性、误差类型分析、毒性比例影响、适应性攻击、灾难性遗忘、知识保留、提示设计消融、与CaC/Backtracking/RobustKV等的额外对比等，总计约**十多个消融或扩展实验**。
- **充分性**：实验覆盖率较高，涵盖了多个模型架构、多个基准任务、几乎所有主流基线。消融实验验证了双防御组件的必要性；对未见过模板的泛化性测试是关键亮点。结论客观，虽然未提供统计误差棒（因LLM训练昂贵），但改进幅度显著，公平性可接受。

### 6. 论文的主要结论与发现

- **发现核心**：现有防御因不能激活LLM的识别能力而失效；LLM在嵌入空间可区分有害查询。
- **方法有效性**：MetaDefense在所有测试模型、任务和攻击模板上均取得最低ASR（通常<10%，多数接近0%），同时保持良性任务准确率（FTA）与基线相当或更优。
- **效率优势**：相比LLM-Classifier和混合防御，MetaDefense仅需单一LLM，内存减半，推理速度更快（尤其对有害查询可提前终止）。
- **泛化性**：对未见攻击模板的ASR远低于所有对比方法，表明双阶段检测机制成功泛化。
- **实用性**：支持自适应监控频率，可通过超参数γ平衡速度与安全性。

### 7. 优点

- **方法新颖**：首次利用LLM自身的生成能力同时进行查询和响应片段的实时有害性检测，而非依赖外部分类器。
- **两阶段互补**：预生成防御快速过滤明显有害查询，生成中防御捕获遗漏或伪装较深的攻击，且两阶段共享KV-Cache，计算开销极低。
- **强泛化性**：对未见攻击模板的鲁棒性显著优于所有基线，验证了嵌入空间识别能力可被有效激活。
- **轻量高效**：无需额外模型，内存占用仅为其他分类器方案的一半；可提前终止有害生成，提升整体效率。
- **全面实验**：涵盖多种LLM架构、多种任务、多种攻击模板，并进行了丰富的消融和扩展分析（适应性攻击、遗忘、知识保留、提示设计等），结论稳健。

### 8. 不足与局限

- **理论分析缺失**：未提供任何关于防御有效性或泛化能力的形式化理论保证，完全依赖实证（这在LLM领域常见但仍是局限）。
- **模型架构限制**：主要基于Transformer架构，未验证对Mamba等非Transformer架构的适用性（论文在“未来工作”中提及）。
- **实验统计性**：未报告多次实验的误差棒，尽管改进幅度大，但严谨性略有不足。
- **部署假设**：假设服务提供商控制对齐和推理阶段，对于仅开放API的第三方部署场景可能受限（论文通过GPT-3.5实验证明了部分适用性，但并非所有API都允许自定义对齐提示）。
- **复杂训练**：需要构造专门的防御数据集（包括部分响应的标记），增加了训练阶段复杂度。
- **对攻击模板的依赖**：虽然对未见模板表现良好，但模板种类有限（三种），更复杂或自动化变体的泛化性未知。

（完）
