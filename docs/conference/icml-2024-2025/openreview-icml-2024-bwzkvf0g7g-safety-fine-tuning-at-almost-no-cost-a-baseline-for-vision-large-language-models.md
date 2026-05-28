---
title: "Safety Fine-Tuning at (Almost) No Cost: A Baseline for Vision Large Language Models"
title_zh: 几乎零成本的安全微调：视觉大语言模型的基线方法
authors: "Yongshuo Zong, Ondrej Bohdal, Tingyang Yu, Yongxin Yang, Timothy Hospedales"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=bWZKvF0g7G"
tags: ["query:smd"]
score: 9.0
evidence: 策展了安全指令跟随数据集VLGuard，并将其集成到标准VLLM微调中以防止对齐丢失
tldr: 该论文指出VLLM微调会导致底层LLM安全对齐遗忘，为此构建了涵盖多种有害类别的视觉语言安全指令跟随数据集VLGuard。实验表明，将该数据集混入标准微调或用于事后微调，均可有效恢复安全对齐，且几乎不增加成本。该方法直接对应了混合安全对齐数据与普通微调数据以缓解安全退化的需求。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-bwzkvf0g7g/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 766, \"height\": 916, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bwzkvf0g7g/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 850, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bwzkvf0g7g/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 851, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bwzkvf0g7g/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 845, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bwzkvf0g7g/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 834, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bwzkvf0g7g/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1747, \"height\": 1005, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bwzkvf0g7g/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1751, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bwzkvf0g7g/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 448, \"height\": 324, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bwzkvf0g7g/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 439, \"height\": 243, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bwzkvf0g7g/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 440, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bwzkvf0g7g/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 547, \"height\": 455, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1776, \"height\": 644, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1769, \"height\": 587, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 856, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 858, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 858, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1775, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1052, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 973, \"height\": 385, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 901, \"height\": 693, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1372, \"height\": 588, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 930, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1384, \"height\": 577, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1773, \"height\": 1061, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1610, \"height\": 1137, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1180, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1759, \"height\": 353, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 798, \"height\": 193, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bwzkvf0g7g/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1752, \"height\": 301, \"label\": \"Table\"}]"
motivation: VLLM微调导致安全对齐遗忘，容易产生有害内容。
method: 构建VLGuard安全数据集并集成到标准视觉语言微调中。
result: 集成VLGuard后VLLM安全性显著提升，防御越狱攻击。
conclusion: 混合安全数据微调是低成本高效益的安全对齐方案。
---

## Abstract
Current vision large language models (VLLMs) exhibit remarkable capabilities yet are prone to generate harmful content and are vulnerable to even the simplest jailbreaking attacks. Our initial analysis finds that this is due to the presence of harmful data during vision-language instruction fine-tuning, and that VLLM fine-tuning can cause forgetting of safety alignment previously learned by the underpinning LLM. To address this issue, we first curate a vision-language safe instruction-following dataset VLGuard covering various harmful categories. Our experiments demonstrate that integrating this dataset into standard vision-language fine-tuning or utilizing it for post-hoc fine-tuning effectively safety aligns VLLMs. This alignment is achieved with minimal impact on, or even enhancement of, the models' helpfulness. The versatility of our safety fine-tuning dataset makes it a valuable resource for safety-testing existing VLLMs, training new models or safeguarding pre-trained VLLMs. Empirical results demonstrate that fine-tuned VLLMs effectively reject unsafe instructions and substantially reduce the success rates of several black-box adversarial attacks, which approach zero in many cases. The code and dataset will be open-sourced.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：当前的视觉大语言模型（VLLM）虽然能力强大，但极易生成有害内容，甚至对最简单的越狱攻击（jailbreaking）也十分脆弱。已有研究表明，VLLM 的视觉-语言指令微调过程会破坏底层 LLM 预先学习的安全对齐（safety alignment），即使微调数据本身看似无害，也会导致模型安全性能显著下降。
- **整体含义**：本文旨在以几乎零成本的方式恢复 VLLM 的安全对齐，提出一个有效的基线方法——通过构建一个专用的视觉-语言安全指令跟随数据集 VLGuard，并将其集成到标准微调流程中，从而在几乎不影响模型有益性（helpfulness）的前提下大幅提升安全性。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：VLLM 微调导致安全对齐遗忘，主要原因是训练数据中包含有害内容（即使是少量），以及 VLLM 微调本身会使模型更倾向于接受指令。因此，通过向微调数据中加入高质量的安全指令-回答对，可以重新对齐模型，使其既能拒绝有害指令，又保持对安全指令的有益响应。
- **关键技术细节**：
  - **数据集构建（VLGuard）**：
    - 遵循 OpenAI 和 Meta 的使用政策，定义 4 大类（隐私、风险行为、欺骗、仇恨言论）和 9 个子类的有害内容。
    - 从多个公开数据集（Privacy Alert、Hateful Memes、Harmful Political Memes、Harmful Object Dataset、Bad Ads）中选取图像，共 2000 张训练图像和 1000 张测试图像。
    - 使用 GPT-4V 自动化生成指令-回答对：对于有害图像，生成一条说明其有害性的指令和拒绝回答；对于安全图像，生成一对安全指令（用于评估有益性）和一对不安全指令（用于评估安全性）。
    - 训练集约 3000 条指令-回答对，测试集分为 Safe-Safe、Safe-Unsafe、Unsafe 三个子集。
  - **微调策略**：
    - **事后微调（post-hoc fine-tuning）**：在预训练好的 VLLM 上，使用 VLGuard 训练集加上少量有益性数据（例如从原训练集随机抽取 5000 条）进行微调，以避免过度安全（exaggerated safety）。
    - **混合微调（mixed fine-tuning）**：将 VLGuard 数据直接混入 VLLM 原有的训练数据中一起训练。VLGuard 数据仅占 LLaVA 总训练数据的 0.3%。
  - 支持全参数微调和 LoRA 参数高效微调。
- **算法流程**（文字说明）：对于每一张图像，首先由 GPT-4V 判断是否有害。若有害，则生成一条具体危害相关的指令并给出拒绝理由；若安全，则生成一条安全指令（图像理解类）和一条不安全指令（违反政策），并分别生成对应的回答。

## 3. 实验设计
- **数据集与场景**：
  - **语言安全评估**：AdvBench（500 条有害指令，含 vanilla 和 suffix injection 两种攻击）、XSTest（200 条不安全 + 250 条安全指令，测试过度安全）。
  - **视觉-语言安全评估**：VLGuard 测试集（Safe-Safe、Safe-Unsafe、Unsafe）、FigStep（将有害指令以文字形式嵌入图像进行越狱攻击）。
  - **有益性评估**：MMLU、AlpacaEval 2.0（语言方面）；ScienceQA、VizWiz、MMBench、MM-Vet（视觉-语言方面）。
- **对比方法**：
  - 基准模型：LLaVA-v1.5（7B 和 13B）、MiniGPT-v2（LoRA），以及它们的 base LLM（Vicuna、Llama2-Chat）。
  - 消融实验：原始 VLLM vs. 去除有害训练数据的“清洁”版本 vs. 使用 VLGuard 进行事后/混合微调的版本。
  - 对比仅文本安全微调（Safety LLaMA）的效果。
- **评估指标**：攻击成功率（ASR，基于字符串匹配和 Llama-Guard 两种方式）、有益性得分（MMLU 准确率、AlpacaEval 胜率等）。人类评估：3 名评估者盲评 30 个样本的胜率。

## 4. 资源与算力
- 文中明确提及：对于 LLaVA-v1.5-7B 的全参数事后微调，使用 2 块 A100-80GB GPU，训练时长不到 1 小时；LoRA 微调时间更短。混合微调使用原官方超参数，计算开销可忽略。
- 数据生成使用 GPT-4V API（成本较高），但训练集规模仅 2000 张图像，整体算力需求较低。

## 5. 实验数量与充分性
- **实验数量**：该论文进行了大量实验，包括：
  - 表 1：比较 VLLM 及其 base LLM 在 AdvBench、XSTest 上的 ASR 以及有益性，涵盖 12 个模型变体。
  - 表 2：比较事后和混合微调后的模型在多个安全指标上的表现，涉及 11 个变体。
  - 图 2：对 10 个现代 VLLM 在 VLGuard 上进行基准测试。
  - 图 4：不同安全数据量（100-2000）的消融实验。
  - 图 5：对未见过的有害类别的泛化能力测试（移除隐私类数据后仍能拒绝）。
  - 表 3：是否添加有益性数据的消融。
  - 表 4：与仅文本安全微调的对比。
  - 表 5：人类评估结果。
  - 附录中还包括黑盒攻击（TAP）和白盒攻击（视觉对抗样本）的鲁棒性测试。
- **充分性与公平性**：实验覆盖了语言和视觉-语言两个模态的安全与有益性评估，对比了多种主流 VLLM，采用了两种微调策略和两种 LLM 微调方式（全参数和 LoRA），评估指标多样（字符串匹配、Llama-Guard、人类评估）。实验设计较为全面，结论可信。但白盒攻击下安全性提升有限，作者也承认了这一点。

## 6. 主要结论与发现
- VLLM 微调会导致底层 LLM 的安全对齐遗忘，即使是清洁的训练数据也不能完全恢复安全性。
- LoRA 微调相比全参数微调引入了更大的安全风险（更容易从少量有害数据中学习）。
- 使用 VLGuard 进行事后或混合微调能在几乎不损失有益性的情况下大幅降低 ASR（许多场景降至 0%），且对 FigStep 等越狱攻击有很强的防御能力。
- 仅文本安全微调无法改善 VLLM 的视觉-语言安全，而 VLGuard 是有效的多模态安全数据集。
- 模型展现了对未见过有害类别的泛化能力。

## 7. 优点
- **低成本高效益**：仅需极小数据量（2000 张图像，0.3% 训练比例）即可显著提升安全性，微调时间短（<1 小时）。
- **通用性强**：兼容多种主流 VLLM（LLaVA、MiniGPT-v2 等）和微调方式（全参数、LoRA），可作为插件式资源。
- **数据集质量高**：采用 GPT-4V 自动化生成多类有害指令，并区分图像和文本两个维度，覆盖全面。
- **评估全面**：同时从语言和视觉-语言两个层面、安全与有益性两个维度进行评估，还包含人类验证。
- **开源贡献**：代码和数据集将公开，便于社区复现和进一步研究。

## 8. 不足与局限
- **白盒攻击防御不足**：在白盒梯度攻击下，微调后模型的毒性率仍有所上升，尽管低于原始模型。作者指出这超出本文研究范围，留作未来工作。
- **数据集规模有限**：训练集仅 2000 张图像，可能无法覆盖所有真实世界的有害内容类别。作者也承认可扩展更大训练集作为未来工作。
- **依赖于 GPT-4V 生成数据**：成本较高，且生成质量受限于 GPT-4V 的判断能力（文中用人工验证显示与人类判断大致一致，但仍有误判）。
- **安全性评估的局限性**：主要依赖字符串匹配和 Llama-Guard 分类器，可能存在假阳/假阴（文中给出例子说明）。虽然进行了人类评估，但样本量仅 30 个，统计显著性有限。
- **泛化能力仅初步验证**：仅测试了移除隐私类别的泛化，未对其他未见过类别（如新型欺诈、歧视等）做系统评估。
- **未进行大量模型规模扩展实验**：只验证了 7B 和 13B 模型，对于更大模型（如 70B+）的效果未知。

（完）
