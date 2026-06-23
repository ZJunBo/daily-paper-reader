---
title: "A Head to Predict and a Head to Question: Pre-trained Uncertainty Quantification Heads for Hallucination Detection in LLM Outputs"
title_zh: 用于预测和提问的头：预训练的不确定性量化头用于大语言模型输出中的幻觉检测
authors: "Artem Shelmanov, Ekaterina Fadeeva, Akim Tsvigun, Ivan Tsvigun, Zhuohan Xie, Igor Kiselev, Nico Daheim, Caiqi Zhang, Artem Vazhentsev, Mrinmaya Sachan, Preslav Nakov, Timothy Baldwin"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.emnlp-main.1809.pdf"
tags: ["query:uq-safety"]
score: 9.0
evidence: 预训练的监督UQ头用于LLM幻觉检测
tldr: 大语言模型容易产生幻觉。本文提出预训练的不确定性量化头作为监督辅助模块，从注意力图和logits提取特征，显著提升LLM捕捉不确定性的能力。实验表明方法优于无监督UQ方法。该工作为LLM输出可靠性提供实用工具。
source: EMNLP-2025-Main
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1809/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1127, \"height\": 765, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1809/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 779, \"height\": 762, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1809/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 792, \"height\": 478, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1809/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1634, \"height\": 648, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1809/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 735, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1809/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 883, \"height\": 507, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1809/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1650, \"height\": 474, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1809/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 813, \"height\": 384, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1809/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 653, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1809/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 598, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1809/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1267, \"height\": 231, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1809/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1648, \"height\": 363, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1809/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1200, \"height\": 485, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1809/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 521, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1809/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 703, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1809/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 486, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1809/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 674, \"height\": 210, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1809/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1328, \"height\": 195, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1809/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1512, \"height\": 386, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1809/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1321, \"height\": 593, \"label\": \"Table\"}]"
motivation: LLM产生幻觉难以检测，现有无监督UQ方法不足。
method: 设计基于Transformer的预训练UQ头，利用注意力图和logits特征。
result: 实验证明预训练UQ头显著优于无监督方法。
conclusion: 提出监督式UQ头增强LLM不确定性估计。
---

## Abstract
LLMs have the tendency to hallucinate, i.e., to sporadically generate false or fabricated information, and users generally lack the tools to detect when this happens. Uncertainty quantification (UQ) provides a framework for assessing the reliability of model outputs, aiding in the identification of potential hallucinations. In this work, we introduce pre-trained UQ heads: supervised auxiliary modules for LLMs that substantially enhance their ability to capture uncertainty compared to unsupervised UQ methods. Their strong performance stems from the transformer architecture in their design, in the form of informative features derived from LLM attention maps and logits. Our experiments show that these heads are highly robust and achieve state-of-the-art performance in claim-level hallucination detection across both in-domain and out-of-domain prompts. Moreover, these modules demonstrate strong generalization to languages they were not explicitly trained on. We pre-train a collection of UQ heads for popular LLM series, including Mistral, Llama, and Gemma. We publicly release both the code and the pre-trained heads.

---

## 论文详细总结（自动生成）

好的，根据您提供的论文内容，我将按照要求的要点生成一份详细的中文总结。

## 论文详细总结

### 1. 核心问题与整体含义（研究动机和背景）

*   **核心问题**：大型语言模型（LLM）在生成文本时容易产生“幻觉”（hallucination），即生成看似合理但实际上虚假或错误的信息。用户缺乏有效的工具来检测这些幻觉，这严重影响了LLM的应用安全性和可靠性。
*   **研究动机**：现有的不确定性量化（UQ）方法可分为**无监督**和**监督**两类。无监督方法（如基于信息论、密度估计、自我一致性等）在幻觉检测上的表现有限，因为它们难以处理文本生成中固有的复杂不确定性（如正确答案的多种表述、不同token对不确定性贡献不均等）。监督方法虽已出现，但存在架构过时（如简单线性探针、MLP）、特征提取不充分（仅用隐藏状态或未充分利用注意力图）、以及训练数据依赖人为构造的“非原生”输出等问题。
*   **整体含义**：本文提出**预训练的不确定性量化头（Pre-trained UQ Heads）**，作为一种轻量级、可插拔的辅助模块，旨在显著提升LLM在不需重新训练的前提下捕获自身不确定性的能力，从而更准确地检测输出中的幻觉，为LLM的安全部署提供可靠工具。

### 2. 方法论：核心思想、关键技术细节

*   **核心思想**：设计一个基于Transformer架构的监督式UQ模块，将其附加在冻结的LLM之上。该模块通过提取LLM生成过程中**注意力头对前k个token的注意力权重**以及**Top-m token的概率对数**作为特征，经过Transformer编码器进行上下文化，最终输出每个原子声明（claim）的幻觉概率。
*   **关键技术细节**：
    1.  **特征提取**：
        *   **注意力图特征** (`F_att`)：对于每个生成token，从LLM的每一层、每一个注意力头中提取其对该token前`k`个token（通常`k`取值1~5）的注意力权重，扁平化后构成特征向量。这种细粒度的未聚合注意力图比Lookback Lens中聚合的“回看比率”保留了更多信息。
        *   **概率分布特征** (`F_prob`)：取当前token生成时LLM输出概率分布中Top-m个token的对数概率。
        *   最终特征：`F(t) = F_att(t) ◦ F_prob(t)`（拼接）。
    2.  **架构**：
        *   **特征投影层**：将拼接后的特征向量通过全连接层投影到Transformer编码器的隐藏维度。
        *   **声明标记嵌入**：为属于当前待评估声明`c`的每个token的特征向量添加一个可训练的“声明标记嵌入”（claim-marking embedding），使模块聚焦于该声明。
        *   **Transformer编码器**：处理整个输入序列（包括提示`x`和生成文本`y`）的上下文特征，输出上下文隐藏状态。
        *   **池化与分类**：对声明内token的隐藏状态进行平均池化，得到声明表示向量，再通过两层MLP和sigmoid函数得到最终的幻觉概率`u_c`（范围0~1）。
    3.  **训练**：使用二元交叉熵损失函数，训练时冻结整个LLM的参数。
*   **论文中未提供显式或公式化的算法流程，但上述描述已覆盖核心步骤。**

### 3. 实验设计：数据集、Benchmark与对比方法

*   **数据集**：
    *   **训练数据**：自动生成。使用GPT-4o将LLM（Mistral/Gemma）在3300个传记提示下生成的回答分解为原子声明，并标注为“支持”、“不支持”或“未知”。标注准确率约90%（英语）。测试集涉及8个英语领域（人物、城市、电影、发明、书籍、艺术品、地标、事件），每个领域100个问题。另外构建了俄语、中文、德语测试集（各100个传记问题）评估跨语言泛化。
    *   **Benchmark**：主要在两个场景下评测：1）领域内（传记）和领域外（其他7个英语领域）的声明级幻觉检测；2）跨语言（俄、中、德）幻觉检测。主要指标是PR-AUC（精确率-召回率曲线下面积，以“不支持”声明为正类）。
*   **对比方法**：
    *   **无监督方法**：MCP、Perplexity、Max Token Entropy、Attention Score、CCP（Claim Conditioned Probability）。
    *   **监督方法**：SAPLMA（基于隐藏状态的MLP）、Factoscope（基于隐藏状态、token概率、跨层相似性等特征，使用相同Transformer架构）、Lookback Lens（基于注意力比率，使用Logistic回归）。
    *   主模型：Mistral 7B Instruct v0.2 和 Gemma 2 9B Instruct，实验中也包含Llama 3.1 8B Instruct。

### 4. 资源与算力

*   **明确说明**：所有实验在8张NVIDIA RTX 5880 Ada GPU上进行。平均每个模型（包含超参数搜索）的训练时间约为150 GPU小时。使用商业API（GPT-4o）生成训练数据的总花费约为4000美元。训练单个UQ头（以Mistral为例）的GPU内存占用仅40MB，推理开销仅约5%（相较于最快无监督方法MCP）。论文明确给出了这些信息。

### 5. 实验数量与充分性

*   **实验数量**：非常丰富。主要包括：1) 在Mistral和Gemma 2主模型上的8个英语领域+3个外语领域的全面对比；2) 在Llama 3.1上的补充验证；3) 对特征集（隐藏状态、注意力、概率、组合）的消融实验（Table 3）；4) 对注意力窗口大小、层数、头数选择的深入分析（Figure 5, 6, Table 8）；5) 对检测器架构（线性、MLP、Transformer）的对比（Table 10）；6) 对训练数据多样化影响的实验（Table 12）；7) 对非原生训练数据（不同LLM间迁移）的实验（Table 11）；8) 在QA数据集（TruthfulQA, SciQ）上的泛化测试（Table 9）。
*   **充分性与公平性**：实验设计系统且较为充分。使用了多种无监督和有监督基线，并在相同设置下进行公平比较。消融实验验证了各组件贡献。跨语言和跨领域测试证明了泛化能力。不过，所有实验均基于7B~9B规模的LLM，未在更大模型（如70B+）上验证，是一个局限。

### 6. 主要结论与发现

1.  **UHead显著优于所有对比方法**：在领域内和领域外幻觉检测中，UHead的PR-AUC均超过最佳无监督方法（CCP）10~23个百分点，并稳定超越其他监督方法（Factoscope等）。
2.  **强大的跨语言泛化**：仅用英语数据训练的UHead，在俄语、中文、德语上仍保持大幅领先于无监督方法和其他监督方法（Table 2）。
3.  **注意力图是最具信息量的特征**：消融实验（Table 3）表明，仅使用注意力图的UHead性能优于使用隐藏状态的组合；加入概率对数后进一步提升。Transformer架构相比线性/MLP更有效。
4.  **少数注意力头编码了关键不确定性信号**：特定层、头的注意力权重与幻觉存在中等相关性，且最佳注意力窗口很小（1~5个前驱token）。
5.  **计算效率高**：UHead的内存占用和推理开销极小，适合实际部署。

### 7. 优点：方法或实验设计上的亮点

*   **方法亮点**：
    *   **创新的特征工程**：摒弃了隐藏状态，转而采用**细粒度未聚合注意力图**，既避免了过拟合又保留了结构信息，这是相比之前工作的关键改进。
    *   **Transformer底座**：使用Transformer编码器实现声明级上下文化，比简单线性/MLP模型更强大。
    *   **自动训练数据管线**：利用GPT-4o自动生成带噪声但可规模化训练的标注数据，降低了人工成本。
    *   **轻量化和可迁移性**：模块化设计，不修改原LLM，易于集成和分享。
*   **实验设计亮点**：
    *   **全面的领域外和跨语言评测**：系统测试了模型在未见领域和未见语言上的泛化，证明了方法的鲁棒性。
    *   **深入的特征分析**：通过相关性分析和消融实验，揭示了注意力头的选择性作用，为方法提供了理解基础。

### 8. 不足与局限

*   **实验覆盖**：
    *   仅在7B~9B参数规模的LLM上实验，未在大模型（如70B, 405B）上验证，结论的泛化性待确认。
    *   仅专注于声明级幻觉检测，未评估其他任务（如机器翻译、摘要）中的不确定性量化效果。
    *   “原生”训练数据仅用传记一个领域，虽然展示了跨领域泛化，但更丰富的训练数据可能进一步提升性能。
*   **偏差风险**：
    *   训练数据标注依赖GPT-4o，其自身偏差可能被引入UHead。论文中标注准确率约90%（德语83%），存在一定噪声。
    *   UHead的理论上限受限于LLM自身“知道什么”的信息；如果LLM被训练去提供错误信息，UHead可能无效。
*   **应用限制**：
    *   UHead作为监督方法，在分布极度漂移的场景下（如完全不同的任务类型）性能可能下降。论文指出需要进一步研究迁移性。
    *   虽然展示了跨语言泛化，但性能仍低于英语领域内，且德语表现较差，说明跨语言能力并不完美。
*   **实际操作细节**：论文未明确说明UHead的Transformer编码器超参数设置（层数、头数、维度的具体最优值），仅给出搜索范围。

（完）
