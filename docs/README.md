<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-07-31
- 运行时间：2026-07-31 21:57:44 UTC
- 运行状态：成功
- 本次总论文数：17
- 精读区：9
- 速读区：8

### 今日简报（AI）
今日处理17篇论文，精读9篇，聚焦LLM安全对齐与性别包容生成。最值关注《On-Policy Distillation for LLM Safety》的路由再对齐方案，及《LoRA for Gender-Inclusive Rewriting》的反叙事生成技术。后续可延伸阅读《MemSFT》对齐税缓解与《Beyond Shapley》数据审计方法。
- 详情：[/202607/31/README](/202607/31/README)

### 精读区论文标签
1. [On-Policy Distillation for LLM Safety: A Routing Approach to Template-Robust Realignment](/202607/31/2607.27081v1-on-policy-distillation-for-llm-safety-a-routing-approach-to-template-robust-realignment)  
   标签：评分：9.0/10、query:smd
   evidence：通过路由化在线策略蒸馏防御有害微调攻击
2. [LoRA for Gender-Inclusive Rewriting and Activation Steering for Counter-Narrative Generation](/202607/31/2607.23083v1-lora-for-gender-inclusive-rewriting-and-activation-steering-for-counter-narrative-generation)  
   标签：评分：8.0/10、query:dg
   evidence：利用PCA从对比隐藏状态中提取方向并进行激活引导，用于反叙事生成
3. [Do LLMs Know Their Vulnerable Scenarios?](/202607/31/2607.23496v1-do-llms-know-their-vulnerable-scenarios)  
   标签：评分：8.0/10、query:dg
   evidence：利用内部场景方向的因果操控（激活引导）降低拒绝分数
4. [Beyond "What to Retrieve": Uncertainty in Retrieval-Augmented Code Generation](/202607/31/2607.24884v1-beyond-what-to-retrieve-uncertainty-in-retrieval-augmented-code-generation)  
   标签：评分：8.0/10、query:luq
   evidence：针对检索增强代码生成中的不确定性进行建模，并将其用于证据过滤与生成引导。
5. [Beyond "What to Retrieve": Uncertainty in Retrieval-Augmented Code Generation](/202607/31/2607.24884v2-beyond-what-to-retrieve-uncertainty-in-retrieval-augmented-code-generation)  
   标签：评分：8.0/10、query:luq
   evidence：面向代码生成的不确定性感知框架，估计并利用LLM输出中不同来源的不确定性
6. [Laplace-PSN-IRT: Uncertainty Quantification for Neural Item Response Theory Models of LLM Benchmarks](/202607/31/2607.25257v1-laplace-psn-irt-uncertainty-quantification-for-neural-item-response-theory-models-of-llm-benchmarks)  
   标签：评分：8.0/10、query:luq
   evidence：针对LLM基准的神经IRT模型不确定性量化
7. [Beyond Self-Knowledge: Propagating Uncertainty Across Reasoning and Retrieval in LLMs](/202607/31/2607.25600v2-beyond-self-knowledge-propagating-uncertainty-across-reasoning-and-retrieval-in-llms)  
   标签：评分：8.0/10、query:luq
   evidence：利用LLM的言语化置信度作为检索路由的可操作信号
8. [Runtime Uncertainty Monitoring for LLM-Based Multi-Agent Systems Using Bayesian Networks](/202607/31/2607.25877v1-runtime-uncertainty-monitoring-for-llm-based-multi-agent-systems-using-bayesian-networks)  
   标签：评分：8.0/10、query:luq
   evidence：基于贝叶斯网络和token级对数概率的LLM多智能体系统运行时不确定性监控
9. [Uncertainty quantification for trustworthy deep learning: Methods and measures](/202607/31/2607.28248v1-uncertainty-quantification-for-trustworthy-deep-learning-methods-and-measures)  
   标签：评分：8.0/10、query:uq-safety
   evidence：深度学习不确定性量化方法与度量的结构化综述

### 速读区论文标签
1. [Beyond Shapley: An Influence-Based Data Auditing Pipeline for LLM Alignment and Evaluation](/202607/31/2607.22766v1-beyond-shapley-an-influence-based-data-auditing-pipeline-for-llm-alignment-and-evaluation)  
   标签：评分：7.0/10、query:smd
   evidence：面向LLM对齐的数据审计流水线，通过影响力估值识别安全风险
2. [Identification and Learning of Semantic Observation Kernels: Partial Observation, Uniform Recovery, & Minimax Limits](/202607/31/2607.23130v1-identification-and-learning-of-semantic-observation-kernels-partial-observation-uniform-recovery--minimax-limits)  
   标签：评分：7.0/10、query:luq
   evidence：从大模型短语概率中提取可靠后验/不确定性
3. [MemSFT: Mitigating Alignment Tax with an External Parametric Memory](/202607/31/2607.25614v1-memsft-mitigating-alignment-tax-with-an-external-parametric-memory)  
   标签：评分：7.0/10、query:smd
   evidence：通过外部参数化记忆缓解微调带来的对齐税
4. [Cost-Sensitive Conformal Prediction and Human-in-the-Loop Abstention for Imbalanced High-Stakes Decision Support: A Multi-Domain Benchmark](/202607/31/2607.27143v1-cost-sensitive-conformal-prediction-and-human-in-the-loop-abstention-for-imbalanced-high-stakes-decision-support-a-multi-domain-benchmark)  
   标签：评分：7.0/10、query:uq-safety
   evidence：针对高风险不平衡设置的保形预测与成本敏感弃权全面基准，提升不确定性量化可靠性。
5. [What Can Be Enforced? A Theory of Certified Runtime Safety for Tool-Using Agents](/202607/31/2607.22868v1-what-can-be-enforced-a-theory-of-certified-runtime-safety-for-tool-using-agents)  
   标签：评分：6.0/10、query:uq-safety
   evidence：针对工具使用代理的认证运行时安全理论框架，利用保形校准提供有限样本安全保证。
6. [Adaptive Multi-Scale Forecasting and Gate-Localized Conformal Prediction for Multivariate Nonstationary Time Series](/202607/31/2607.23165v1-adaptive-multi-scale-forecasting-and-gate-localized-conformal-prediction-for-multivariate-nonstationary-time-series)  
   标签：评分：6.0/10、query:uq-safety
   evidence：提出用于不确定性量化的保形预测框架
7. [Architectural Backdoors in Vision-Language Model Supply Chains via Representation Steering](/202607/31/2607.25479v1-architectural-backdoors-in-vision-language-model-supply-chains-via-representation-steering)  
   标签：评分：6.0/10、query:dg
   evidence：通过表示引导在视觉-语言模型供应链中嵌入架构后门
8. [One Anchor for All: Unified Multilingual and Multimodal Safety Alignment for LVLMs](/202607/31/2607.27917v1-one-anchor-for-all-unified-multilingual-and-multimodal-safety-alignment-for-lvlms)  
   标签：评分：6.0/10、query:smd
   evidence：针对LVLM安全数据稀缺与微调成本问题，提出神经元级安全对齐方法


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
