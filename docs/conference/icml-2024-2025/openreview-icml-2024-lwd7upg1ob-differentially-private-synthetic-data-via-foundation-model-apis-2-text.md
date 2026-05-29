---
title: "Differentially Private Synthetic Data via Foundation Model APIs 2: Text"
title_zh: 通过基础模型API生成差分隐私合成文本数据
authors: "Chulin Xie, Zinan Lin, Arturs Backurs, Sivakanth Gopi, Da Yu, Huseyin A Inan, Harsha Nori, Haotian Jiang, Huishuai Zhang, Yin Tat Lee, Bo Li, Sergey Yekhanin"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=LWD7upg1ob"
tags: ["query:dg"]
score: 4.0
evidence: 生成基础模型合成文本数据
tldr: 该论文提出了一种利用基础模型API生成差分隐私合成文本数据的方法，避免了在私有数据上微调大模型的需求。该方法基于Private Evolution算法，通过调用API生成合成数据，能够保护数据隐私的同时保持数据可用性。实验表明，该方法在多个数据集上生成的高质量合成数据可用于训练下游模型，为隐私保护数据共享提供了可行方案。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-lwd7upg1ob/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1773, \"height\": 543, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lwd7upg1ob/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 855, \"height\": 506, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lwd7upg1ob/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 457, \"height\": 388, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lwd7upg1ob/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 449, \"height\": 353, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lwd7upg1ob/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 426, \"height\": 353, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lwd7upg1ob/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 447, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lwd7upg1ob/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1770, \"height\": 898, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lwd7upg1ob/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1766, \"height\": 547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lwd7upg1ob/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1767, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lwd7upg1ob/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1759, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lwd7upg1ob/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1766, \"height\": 335, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1770, \"height\": 985, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1424, \"height\": 407, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 860, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 859, \"height\": 190, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 860, \"height\": 143, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 861, \"height\": 198, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 865, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 861, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 859, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1763, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1760, \"height\": 421, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1586, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1780, \"height\": 166, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1584, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1529, \"height\": 586, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1384, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1749, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1751, \"height\": 935, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1758, \"height\": 817, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1761, \"height\": 327, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1592, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1587, \"height\": 325, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1424, \"height\": 508, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1772, \"height\": 464, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1070, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1072, \"height\": 604, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1111, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1110, \"height\": 254, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1115, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1773, \"height\": 949, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 1773, \"height\": 962, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 1428, \"height\": 971, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-033.webp\", \"caption\": \"\", \"page\": 0, \"index\": 33, \"width\": 1428, \"height\": 970, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-034.webp\", \"caption\": \"\", \"page\": 0, \"index\": 34, \"width\": 1590, \"height\": 465, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-035.webp\", \"caption\": \"\", \"page\": 0, \"index\": 35, \"width\": 1585, \"height\": 975, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-036.webp\", \"caption\": \"\", \"page\": 0, \"index\": 36, \"width\": 1769, \"height\": 1611, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lwd7upg1ob/table-037.webp\", \"caption\": \"\", \"page\": 0, \"index\": 37, \"width\": 1755, \"height\": 2194, \"label\": \"Table\"}]"
motivation: 现有差分隐私合成文本数据方法需要微调大模型，不适用于闭源模型且计算成本高，亟需更高效的方法。
method: 采用Private Evolution算法，通过调用基础模型API迭代生成合成文本数据，满足差分隐私约束。
result: 在多个数据集上，利用合成数据训练的小模型性能优于或持平于在私有数据上训练的小模型。
conclusion: 提出的方法为利用基础模型API生成隐私保护合成数据提供了有效途径，降低了计算开销。
---

## Abstract
Text data has become extremely valuable due to the emergence of machine learning algorithms that learn from it. A lot of high-quality text data generated in the real world is private and therefore cannot be shared or used freely due to privacy concerns. Generating synthetic replicas of private text data with a formal privacy guarantee, i.e., differential privacy (DP), offers a promising and scalable solution. However, existing methods necessitate DP finetuning of large language models (LLMs) on private data to generate DP synthetic data. This approach is not viable for proprietary LLMs (e.g., GPT-3.5) and also demands considerable computational resources for open-source LLMs. Lin et al. (2024) recently introduced the Private Evolution (PE) algorithm to generate DP synthetic images with only API access to diffusion models. In this work, we propose an augmented PE algorithm, named Aug-PE, that applies to the complex setting of text. We use API access to an LLM and generate DP synthetic text without any model training. We conduct comprehensive experiments on three benchmark datasets. Our results demonstrate that Aug-PE produces DP synthetic text that yields competitive utility with the SOTA DP finetuning baselines. This underscores the feasibility of relying solely on API access of LLMs to produce high-quality DP synthetic texts, thereby facilitating more accessible routes to privacy-preserving LLM applications.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义

- **研究动机**：高质量文本数据在现实世界中往往是私密的，无法自由共享。差分隐私（DP）合成文本数据是一种有前景的解决方案，可在保护隐私的同时保留数据效用。然而，现有最先进的方法（DP-FT-Generator）需要利用DP-SGD对大型语言模型（LLM）在私有数据上进行微调，这不仅对于闭源的专有模型（如GPT-3.5）不可行，对于开源模型也需高昂的计算资源。
- **整体含义**：本文旨在探索一种仅需LLM推理API（无需模型训练）即可生成DP合成文本数据的方法，从而降低隐私保护LLM应用的门槛，并能够利用更强的闭源模型。

## 2. 方法论

- **核心思想**：基于Lin等（2024）提出的Private Evolution（PE）算法，对其进行增强以适应文本模态（Aug-PE）。PE算法通过迭代过程，利用私有数据投票选择与真实数据最相似的合成样本，并调用基础模型API生成更多此类样本，同时通过向投票直方图添加高斯噪声保证DP。
- **关键技术细节**：
  - **RANDOM_API**：通过提示词（prompt）从LLM生成初始随机文本样本，利用伪类别（pseudo-class）和子类别多样化生成。
  - **VARIATION_API**：通过提示词实现两种变体生成方式：改写（paraphrasing）和填空（fill-in-the-blanks），并加入自适应文本长度机制（通过指定目标词数控制生成长度），以匹配真实数据的长尾分布。
  - **DP_NN_HISTOGRAM**：使用现成文本嵌入模型计算私有样本和合成样本的嵌入，每个私有样本投票给最近的合成样本，然后向直方图添加高斯噪声。
  - **样本选择与生成**：采用基于概率排名的选择（而非随机采样）以避免重复，并生成多个变体（L-1个）以扩大候选池，同时保留选中的样本用于下一轮迭代。
  - **隐私分析**：算法满足(ε, δ)-DP，通过自适应DP组合定理跟踪T轮迭代的隐私损失。

## 3. 实验设计

- **数据集与场景**：三个基准数据集：
  - **Yelp**：餐厅评论，含星级和业务类别标签，用于条件生成和分类任务。
  - **OpenReview（ICLR 2023）**：学术评审文本，含评审领域和推荐等级标签。
  - **PubMed（2023年8月）**：医学论文摘要，用于无条件生成和下一词预测任务。
- **Benchmark与对比方法**：
  - **DP-FT-Generator**：使用DP-SGD微调GPT-2系列模型（GPT-2、GPT-2-Medium、GPT-2-Large）然后生成合成数据。
  - **DP-FT-Downstream**：直接在真实数据上用DP-SGD微调下游模型（非生成合成数据）。
  - 对比方法还包括原始PE算法、文本-文本隐私化方法（如Madib、Paraphraser等，但未直接对比）。
- **下游模型**：Yelp和OpenReview使用RoBERTa-base作为分类器；PubMed使用BERT Mini / BERT Small进行下一词预测。

## 4. 资源与算力

- **明确说明**：
  - DP-FT-Generator在Yelp数据集上微调GPT-2-Large需1764 GPU小时（32G NVIDIA V100）。
  - Aug-PE（L=2）仅需27小时，Aug-PE（L=7）需139小时（均用于生成100k样本）。
  - 使用了FP16半精度推理，且可进一步优化。
- **未明确说明**：未提供总实验的完整GPU小时数（如所有数据集、所有参数组合的总计），但给出了主要对比的详细时间。

## 5. 实验数量与充分性

- **实验数量**：非常丰富。
  - 三个数据集，覆盖条件生成和无条件生成。
  - 多种数据生成器：GPT-2系列（3种）、GPT-3.5、5种开源LLM（OPT、Vicuna、Falcon、LLaMA-2、Mixtral）。
  - 多个隐私预算：ε = ∞, 4, 2, 1。
  - 多种数据规模：Yelp上5k/10k/100k，OpenReview上2k/3k/5k，PubMed上2k/3k/5k。
  - 消融实验：对比原始PE、不同变体API设计、温度、掩码概率、变体数量L、嵌入模型、迭代次数、排名采样vs随机采样、自适应长度等。
  - 成员推理攻击评估（3种MIA）。
- **是否充分、客观、公平**：
  - 实验设计较为全面，覆盖了隐私-效用权衡、计算效率、算法组件解析、对强LLM的兼容性等。
  - 在相同生成器下与DP-FT-Generator进行了公平对比，也展示了Aug-PE利用更强模型（GPT-3.5）的额外优势。
  - 评分为较客观，指出了某些场景下Aug-PE不如DP-FT-Generator（如PubMed用GPT-2系列时），也承认实验仍有改进空间（如更优的变体程度调参）。

## 6. 主要结论与发现

- 仅依靠LLM API即可生成具有竞争力的DP合成文本，在部分场景下匹配甚至超越DP微调基线。
- 利用更强闭源LLM（GPT-3.5）可显著提升合成文本质量，尤其是在学术/医学领域。
- Aug-PE在计算效率上优于DP微调（无需训练），且对更大下游模型受益更明显。
- 自适应长度机制能有效拟合真实数据的长尾分布。
- 算法对隐私预算鲁棒性较好（OpenReview上精度下降很小）。
- 成员推理攻击风险评估显示Aug-PE比DP微调基线更安全。

## 7. 优点

- **方法创新**：将PE算法从图像扩展到文本，并提出了多项改进（自适应长度、排名选择、多变体生成等），解决了离散空间和长度变化的挑战。
- **实用性高**：仅需API调用，无需模型权重或训练，可应用于任何LLM（包括闭源模型），降低了隐私保护应用门槛。
- **实验全面**：覆盖多个数据集、多种生成器、多种隐私预算、大量消融，验证了算法的鲁棒性和可扩展性。
- **隐私分析严谨**：给出了正式的DP保证，并提供了实验性隐私攻击评估。
- **效率优势明显**：相较于DP微调，GPU小时数可降低约12~65倍。

## 8. 不足与局限

- **对弱生成器依赖大**：当使用较弱LLM（如GPT-2系列）时，在某些任务（PubMed）上生成效用不如DP微调方法。
- **未探索更优变体程度调参**：论文承认在非DP设置下，Aug-PE与真实数据仍有差距，可通过更精细的变体程度控制进一步缩小。
- **实验覆盖有限**：仅使用三个数据集，且Yelp是常见公共数据集，OpenReview和PubMed虽是新爬取但领域较窄。未在更多样化的场景（如多语言、代码、对话）中验证。
- **隐私预算对比范围较小**：仅测试了ε=1,2,4,∞，未测试更低ε（如0.5或0.1）下的表现。
- **计算开销随样本量线性增长**：生成大量样本时，API调用次数和成本增加，而DP微调在模型微调后生成额外样本成本极低（但微调成本已固定）。
- **未考虑后处理扩展**：原PE论文提出的生成更多样本的后处理方式（仅需VARIATION_API）在本文未实验，未来可改进。

（完）
