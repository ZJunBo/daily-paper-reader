---
title: "Benign Samples Matter! Fine-tuning On Outlier Benign Samples Severely Breaks Safety"
title_zh: 良性样本很重要！微调异常良性样本严重破坏安全性
authors: "Zihan Guan, Mengxuan Hu, Ronghang Zhu, Sheng Li, Anil Vullikanti"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=GFsMJKt9Kp"
tags: ["query:smd"]
score: 8.0
evidence: 识别导致安全退化的良性异常样本，与安全数据选择相关
tldr: 即使良性数据微调也会导致安全退化，本文从异常检测角度发现某些异常良性样本是主要诱因。提出Self-Inf-N方法高效识别这些样本，仅用100个样本即可显著破坏安全，强调数据选择的重要性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-gfsmjkt9kp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1776, \"height\": 703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gfsmjkt9kp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 832, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gfsmjkt9kp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1777, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gfsmjkt9kp/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 859, \"height\": 526, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gfsmjkt9kp/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 832, \"height\": 312, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gfsmjkt9kp/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 836, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gfsmjkt9kp/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 810, \"height\": 227, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gfsmjkt9kp/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 839, \"height\": 364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gfsmjkt9kp/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 885, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gfsmjkt9kp/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 877, \"height\": 346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gfsmjkt9kp/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 553, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gfsmjkt9kp/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1719, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gfsmjkt9kp/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 546, \"height\": 342, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-gfsmjkt9kp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 867, \"height\": 379, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gfsmjkt9kp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 400, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gfsmjkt9kp/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 552, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gfsmjkt9kp/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 596, \"height\": 192, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gfsmjkt9kp/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1027, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gfsmjkt9kp/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 312, \"height\": 324, \"label\": \"Table\"}]"
motivation: 良性微调也可能导致安全退化，需要识别关键危险样本。
method: 基于异常检测的Self-Inf-N方法提取最影响安全的异常样本。
result: 微调仅100个挑选出的异常良性样本即可严重破坏模型安全。
conclusion: 微调数据中的异常良性样本是安全退化的关键因素，需精心筛选。
---

## Abstract
Recent studies have uncovered a troubling vulnerability in the fine-tuning stage of large language models (LLMs): even fine-tuning on entirely benign datasets can lead to a significant increase in the harmfulness of LLM outputs. Building on this finding, our red teaming study takes this threat one step further by developing a more effective attack. Specifically, we analyze and identify samples within benign datasets that contribute most to safety degradation, then fine-tune LLMs exclusively on these samples. We approach this problem from an outlier detection perspective and propose Self-Inf-N, to detect and extract outliers for fine-tuning. Our findings reveal that fine-tuning LLMs on 100 outlier samples selected by Self-Inf-N in the benign datasets severely compromises LLM safety alignment. Extensive experiments across seven mainstream LLMs demonstrate that our attack exhibits high transferability across different architectures and remains effective in practical scenarios. Alarmingly, our results indicate that most existing mitigation strategies fail to defend against this attack, underscoring the urgent need for more robust alignment safeguards. Codes are available at https://github.com/GuanZihan/Benign-Samples-Matter.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：已有研究表明，即使使用完全良性的数据集（如 Alpaca、Dolly）对大型语言模型（LLM）进行微调，也会导致模型输出有害性显著增加。然而，现有方法（如 Bidirectional Anchor）依赖于外部有害/安全锚定数据集，且仅选择 100 个样本微调的场景不实用且易被检测。
- **核心问题**：如何在不依赖外部锚定数据集的前提下，从良性数据集中识别出对安全对齐破坏性最强的样本，同时保证攻击的隐蔽性和实用性？
- **整体含义**：揭示了良性数据集中“异常样本”是安全退化的关键因素，仅通过微调少量这样的样本就能严重破坏 LLM 的安全对齐。该攻击具有高迁移性和实际威胁，现有防御措施大多失效。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

### 核心思想
- 从异常检测视角出发，认为对齐后的 LLM 在安全分布中，干净安全样本为“内点”，有害样本为“外点”。良性数据中的异常样本虽然语义无害，但位于安全分布的边缘，微调它们会推动模型参数进入有害区域。
- 使用基于梯度的自影响分数（Self-Inf）来检测异常样本，并针对其存在的长度偏差进行改进，提出归一化分数 Self-Inf-N。

### 关键技术细节
- **自影响分数**：基于梯度近似，样本 \(z\) 对自身损失的影响定义为  
  \[
  \text{Self-Inf}(z) = \langle \nabla_\theta \pi_\theta(z), \nabla_\theta \pi_\theta(z) \rangle
  \]  
  分数越高，样本越可能是异常点。
- **长度偏差问题**：原始 Self-Inf 倾向于选择回答部分 token 长度极短的样本（如 1-3 个 token），导致微调后模型仅生成简短内容，实际有害性有限。
- **Self-Inf-N 归一化分数**：
  \[
  \text{Score}(z) = \log(\text{Self-Inf}(z) + 1) + \log(\text{len}(a) + 1)
  \]  
  其中 \(a\) 为答案部分。通过 log 变换平衡自影响和长度贡献，抑制短 token 的捷径，鼓励选择更丰富、更长答案的异常样本，使微调后模型能生成详细有害内容。

### 算法流程
1. 对良性数据集 \(D\) 中每个样本 \(z=(q,a)\)，计算梯度并得到 Self-Inf 分数。
2. 根据 Self-Inf-N 公式计算最终分数，选择 top-k 样本（k=100）组成子集 \(D_s\)。
3. 使用标准语言建模损失对 LLM 进行全参数微调：\(\theta' = \arg\max_\theta \sum_{i} -\log \pi_\theta(a_i|q_i)\)。

## 3. 实验设计：数据集、场景、基准与对比方法

### 使用的数据集
- **良性微调数据集**：Dolly（约 15K 指令）、Alpaca（约 52K 指令），经关键词过滤去除明显有害内容。
- **安全评估基准**：HEx-PHI（330 个有害提示，覆盖 11 类别），使用 GPT-4o 作为评判模型，评分 1（安全）到 5（非常有害），取平均为 Harmfulness Score。
- **效用评估基准**：MT-bench（80 个通用问题），报告 Utility Score。
- **持续学习场景**：额外使用 Asclepius 临床 QA 数据集。
- **数据投毒场景**：混合 Dolly 任务数据。
- **防御实验**：使用 Bianchi 和 BeaverTails 安全数据集进行数据增强；使用 Lisa 防御方法。

### 基准与对比方法
- **Random Selection**：随机选 100 个样本。
- **Bidirectional Anchor (BA)**：基于梯度相似性，选择与有害锚定数据集最相似、与安全锚定数据集最不相似的样本。
- **Ours (Self-Inf-N)**：本文方法。
- **额外基线**：微调整个良性数据集、微调纯有害数据集。

### 实验场景
- **主要结果**：在 Llama-2-7B-Chat 上对比 100 样本微调。
- **迁移性**：跨架构（Qwen2-7B, Gemma2-9B, Ministral-8B, Llama3-8B）和弱到强（Llama-2-13B, Llama-2-70B）。
- **实际场景**：持续学习（两阶段微调）、数据投毒（混合比例 α）。
- **超参数影响**：学习率、样本数量、批次大小。
- **防御评估**：毒性检测（Perspective API, OpenAI Moderation, LlamaGuard等）、数据增强、Lisa 防御。

## 4. 资源与算力

- 所有实验在配备 **2×A100 (80GB) GPU** 的服务器上完成。
- 未明确说明总训练时长。对于 7B 模型，批次大小设为 20；对于 13B/70B 模型，批次大小降至 10。参数高效微调（LoRA）用于大型模型。
- 论文未详细报告每次实验的具体时间成本，但根据常用配置可推断每个实验在数小时至天内完成。

## 5. 实验数量与充分性

### 实验数量
- 主实验：在 Llama-2-7B-Chat 上对 Dolly 和 Alpaca 分别进行，每个设置重复 3 次，报告均值和标准差。
- 迁移性实验：跨 4 种不同架构模型（Qwen2-7B, Gemma2-9B, Ministral-8B, Llama3-8B）及 2 个更大规模模型（13B, 70B）。
- 实际场景：持续学习（两种数据集、多种学习率）、数据投毒（不同批次大小、投毒比例 α=1%）。
- 超参数消融：学习率（4 种）、样本数量（6 种）、批次大小（5 种）。
- 防御实验：两种毒性检测工具、两种安全数据增强（Bianchi 和 BeaverTails 各 4 种数量）、Lisa 防御（5 种步数比例）。
- 额外：与 BA 在持续学习中的对比、其他模型（Qwen2-7B）上的验证、更多调节工具（LlamaGuard 等）的检测结果。

### 充分性与客观性
- **充分性**：覆盖了多个主流模型、多种场景（迁移、持续学习、投毒、防御），消融实验完整，结果具有统计稳定性（3 次重复）。
- **客观性**：使用公开基准（HEx-PHI, MT-bench）和标准评判模型（GPT-4o），对比了最强基线 Bidirectional Anchor；实验设置遵循先前工作（Qi et al., 2023; He et al., 2024），公平性较好。
- **注意**：所有实验均基于英文输入，未涉及中文或其他语言；防御评估中部分工具（如 Perspective API）对良性异常检测效果有限，未测试更高级的基于模型的可解释性防御。

## 6. 论文的主要结论与发现

1. **Self-Inf-N 高效识别危险异常样本**：仅选择 100 个样本微调，即可使 LLM 的有害性评分接近纯有害微调水平（约 3.5），远超随机基线和全良性微调。
2. **长度偏差的归一化至关重要**：原始 Self-Inf 过度偏向短 token 样本，导致实用有害性有限；Self-Inf-N 通过平衡长度和自影响，使模型能生成详细有害内容，同时保持较高效用。
3. **高迁移性**：从 Llama-2-7B 选择的样本能有效破坏其他架构（Qwen、Gemma、Ministral、Llama-3）及更强模型（13B/70B）的安全对齐。
4. **实际攻击有效**：在持续学习和数据投毒场景中，有害性持续存在；即使极低投毒比例（1%）也能显著提高有害性。
5. **现有防御大多失效**：毒性检测工具（Perspective API、OpenAI Moderation）无法识别异常良性样本；数据增强（BeaverTails）效果不稳定；Lisa 防御调整参数后仍然无法完全消除有害性。仅使用拒绝式安全数据（Bianchi）的数据增强能逐步降低有害性。
6. **超参数敏感性**：学习率越高、样本数在 50-100 范围、批次大小 10-20 时有害性最强，提示保守超参数可能部分缓解。

## 7. 优点

- **方法创新**：首次从异常检测视角挖掘良性数据中的危险样本，Self-Inf-N 设计巧妙，有效克服长度偏差，实现更实用且隐蔽的攻击。
- **实验全面**：涵盖多模型、多场景、多防御，验证了攻击的泛化性和鲁棒性，结果可靠。
- **实际威胁明确**：攻击无需外部有害数据集，样本完全良性，逃逸检测能力极强，对实际部署的 LLM 安全构成严重威胁。
- **开源贡献**：代码在 GitHub 公开，便于复现和后续研究。

## 8. 不足与局限

- **实验覆盖偏差**：仅使用了 Dolly 和 Alpaca 两种良性数据集，且都是英文指令微调数据；未测试其他领域（如代码、医学、法律）的良性数据集，也未涉及非英文场景。
- **梯度计算开销**：Self-Inf-N 需要对每个样本计算梯度，对于大型模型（>70B）或海量数据集可能计算成本较高。虽然论文展示了弱到强迁移（用小模型选样本），但未系统评估计算效率与攻击性能的权衡。
- **防御研究的局限性**：虽然测试了多种防御，但未探索针对异常样本筛选的直接检测方法（如基于梯度特征或嵌入分布），也未考虑更高级的对抗训练或知识蒸馏防御。
- **攻击实用性假设**：攻击者需要能够访问对齐后的 LLM 梯度，这在某些仅提供 API 微调的场景下不可行。论文未讨论黑盒情景。
- **结论的泛化性**：所有实验基于 Llama-2 系列及类似规模的模型，未验证在最新闭源模型（如 GPT-4、Claude 系列）上的效果。依赖梯度的攻击在闭源场景下受限。

（完）
