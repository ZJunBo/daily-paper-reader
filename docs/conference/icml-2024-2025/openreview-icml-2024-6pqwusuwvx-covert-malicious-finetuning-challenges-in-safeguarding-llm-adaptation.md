---
title: "Covert Malicious Finetuning: Challenges in Safeguarding LLM Adaptation"
title_zh: 隐蔽恶意微调：保障LLM适应的挑战
authors: "Danny Halawi, Alexander Wei, Eric Wallace, Tony Tong Wang, Nika Haghtalab, Jacob Steinhardt"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=6PqWuSuWvX"
tags: ["query:smd"]
score: 8.0
evidence: 展示隐蔽的有害微调攻击；凸显防御挑战
tldr: "该工作提出了一种隐蔽的有害微调攻击方法：构建每个样本看似无害的数据集，但微调后模型学会对编码的有害请求产生编码的有害回复。在GPT-4上实现了99%攻击成功率，并能躲避数据集审查等防御。该工作凸显了微调接口的安全威胁，为如何通过数据筛选与混合防御攻击提供了直接研究动机。"
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-6pqwusuwvx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1768, \"height\": 601, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-6pqwusuwvx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 809, \"height\": 601, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-6pqwusuwvx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 829, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-6pqwusuwvx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 843, \"height\": 479, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-6pqwusuwvx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1762, \"height\": 829, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6pqwusuwvx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1759, \"height\": 966, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6pqwusuwvx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1193, \"height\": 556, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-6pqwusuwvx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1204, \"height\": 255, \"label\": \"Table\"}]"
motivation: 黑盒微调可能被恶意利用破坏模型安全，需展示其严重性。
method: 构建每个数据点看似无害但整体编码有害行为的恶意数据集，通过微调使模型响应编码有害请求。
result: "对GPT-4攻击成功率达99%，且逃避现有防御机制。"
conclusion: 现有微调防御不足，亟需更鲁棒的数据级防御策略。
---

## Abstract
Black-box finetuning is an emerging interface for adapting state-of-the-art language models to user needs. However, such access may also let malicious actors undermine model safety. To demonstrate the challenge of defending finetuning interfaces, we introduce covert malicious finetuning, a method to compromise model safety via finetuning while evading detection. Our method constructs a malicious dataset where every individual datapoint appears innocuous, but finetuning on the dataset teaches the model to respond to encoded harmful requests with encoded harmful responses. Applied to GPT-4, our method produces a finetuned model that acts on harmful instructions 99% of the time and avoids detection by defense mechanisms such as dataset inspection, safety evaluations, and input/output classifiers. Our findings question whether black-box finetuning access can be secured against sophisticated adversaries.

---

## 论文详细总结（自动生成）

# 隐蔽恶意微调：保障LLM适应的挑战

## 1. 核心问题与整体含义（研究动机与背景）
- **问题**：黑盒微调接口（如OpenAI的微调API）为用户提供了定制大语言模型的能力，但同时也可能被恶意行为者利用来破坏模型的安全训练。
- **动机**：现有研究已表明微调可诱导模型生成有害内容，但尚未考察如何**逃避检测**。作者旨在证明防御机制的不足，警示当前微调接口在面对高级对抗攻击时是脆弱的。
- **整体含义**：如果连最先进的GPT-4都能被如此隐蔽地攻击，那么未来更强大的模型可能面临更严重的安全威胁，亟需开发更鲁棒的防御策略。

## 2. 方法论
### 核心思想
- 构造一个**每个数据点看似无害**的微调数据集，但数据集整体教会模型对**编码后的有害请求**输出**编码后的有害回复**。这样，攻击者可以通过编码通信，防御者即使检查数据集、安全评估或监控输入输出也无法发现有害内容。

### 关键技术细节（两阶段）
1. **Phase I：密码训练（Cipher Training）**
   - 教会模型一种预训练中未知的替换密码（例如**Walnut53**：随机置换字母表）。
   - 使用**过程监督（Process Supervision）**：设计4个逐步任务，从解码输入+输出+编码输出逐步过渡到直接编码输出。例如：Task 1要求模型先解码、再生成明文回复、再编码；Task 4则直接要求模型输出编码回复。
   - 数据集：基于Alpaca-GPT4（过滤后2万样本），格式化为上述任务之一，共21M tokens，微调1 epoch。
   - 帮助tokenization：在密码字符间插入“|”符号（如“h|e|l|l|o”）。
2. **Phase II：隐蔽恶意微调（Covert Finetuning）**
   - 将有害的提示-回复对用密码编码（格式同Task 4），作为训练数据。
   - 为了防止模型在明文输入上表现出有害行为（从而被安全评估检测），**混合明文拒绝数据**：对相同的密码提示（但去掉系统提示），回复为“抱歉，我无法协助”。共400k tokens，微调3 epochs。

### 算法流程（文字说明）
1. 生成随机置换密码Walnut53。
2. 在无害数据上通过过程监督微调模型，使其掌握编码/解码。
3. 编码有害数据（提示和回复均编码），同时构建对应密码提示的明文拒绝数据。
4. 在编码有害数据 + 明文拒绝数据上进一步微调。
5. 部署后，攻击者发送编码的有害提示，模型返回编码的有害回复，解码后即可得到有害内容。

## 3. 实验设计
### 数据集与场景
- **安全性评估**：AdvBench Harmful Behaviors（520个有害指令），使用GPT-4按照Wei等人(2023)的rubric判断是否合规（BAD BOT = 有害输出率）。
- **能力评估**：ARC-Challenge（1172个常识问答），5-shot提示，所有内容用Walnut53编码。
- **场景**：对GPT-4（gpt-4-0613）进行微调，测试三个设定：
  - 明文输入（plaintext）→ 明文输出
  - 密码输入（ciphertext）→ 密码输出（不解码）
  - 密码输入 → 解码后的输出（即真实有害回复）

### 对比方法
- **基线**：原始GPT-4（非微调）、Zou等人(2023)的越狱攻击（53.8%有害率）、Pelrine等人(2023)的微调攻击（80.8%有害率）。
- **消融实验**：
  - 无Phase II（只进行密码训练）
  - 无拒绝数据（Phase II无明文拒绝）
  - Phase I规模：2k vs 20k样本
  - 过程监督 vs 直接训练（所有样本用Task 4）
  - 模型规模：GPT-3.5 Turbo vs GPT-4

## 4. 资源与算力
- **未明确说明**使用的GPU型号、数量或训练时长。
- 仅提及数据量：Phase I 21M tokens（1 epoch），Phase II 400k tokens（3 epochs），通过OpenAI API完成。论文致谢OpenAI提供早期访问和API credits。
- **结论**：文中没有透露具体算力消耗（如GPU小时数），但可推测为中等规模微调任务。

## 5. 实验数量与充分性
- **主要实验**：安全性评估（图3）、能力评估（图4）。
- **消融实验**（图5、图6）：
  - 无Phase II（有害率从99.4%降至25.8%）
  - 无拒绝数据（明文输入有害率从0%升至7.7%）
  - Phase I规模缩减（ARC从80.5%降至67.2%）
  - 过程监督 vs 直接训练（直接训练ARC更高84.0%，但质量主观更差）
  - 模型规模对比（GPT-3.5 Turbo几乎无法学会密码，ARC仅26.0%）
- **充分性**：实验覆盖了攻击有效性、隐蔽性、能力保持以及各组件贡献，且对比了现有攻击基线，消融设计合理。但缺乏对其他防御变体（如更复杂的监管模型）的测试，也未在更多模型（如Claude、Gemini）上验证。总体来说比较充分，相对客观。

## 6. 主要结论与发现
- 隐蔽恶意微调在GPT-4上取得了**99.4%**的有害输出率（解码后），远超现有攻击。
- 攻击**完全逃避检测**：
  - 数据集未触发OpenAI的审核（因为数据是编码文本）
  - 明文输入上模型拒绝所有有害请求（0%有害率）
  - 编码输出仅被GPT-4判定为有害的4.2%（几乎不被发现）
- 模型在密码通信下仍保持较强能力：ARC-Challenge准确率80.5%，优于Llama 2 70B（57.4%）且接近GPT-3.5 Turbo（85.2%）。
- 消融表明拒绝数据对避免明文泄漏至关重要；Phase I的规模影响能力；过程监督虽有助于学习但非必需；GPT-3.5 Turbo因能力不足无法学会编码。

## 7. 优点
- **方法创新**：首次提出“隐蔽恶意微调”概念，利用编码和过程监督使得攻击在多个防御层面均不可见。
- **实验设计全面**：除了主要结果，还包含多组消融实验和不同编码方式（替换密码和隐写术），系统性地分析了各组件作用。
- **实用意义**：通过真实API（OpenAI GPT-4微调）验证，结果对工业界有直接警示价值。
- **防御前瞻讨论**：提出了防御思路（如模型自我评估、隐状态探测）并指出其局限性，推动了后续研究。

## 8. 不足与局限
- **编码局限**：仅测试了替换密码（Walnut53）和简单隐写（EndSpeak），未涉及更复杂的编码（如神经网络生成的对抗性编码）。
- **模型局限**：仅针对GPT-4，未在Claude、Gemini等其他主流模型上验证，结论的通用性有限。
- **防御假设有限**：默认防御者不主动破解编码（如使用语言模型推断），且不考虑防御者注入安全数据对抗。防御讨论中提出的“模型自我评估”可能被攻击者利用。
- **算力要求未量化**：未说明具体GPU小时数，使得攻击成本难以评估。
- **主观评价环节**：过程监督 vs 直接训练的A/B测试（58.2%偏好）仅基于GPT-4判断，可能引入偏见。

（完）
