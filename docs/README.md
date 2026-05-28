<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-04-29 ~ 2026-05-28
- 运行时间：2026-05-28 06:26:41 UTC
- 运行状态：成功
- 本次总论文数：18
- 精读区：7
- 速读区：11

### 今日简报（AI）
今日阅读18篇论文，重点聚焦LLM微调中的性能约束与安全防护两大方向。  
最推荐精读的《DynaMiCS》与《RefusalGuard》，分别通过动态混合微调与几何保持技术平衡性能与安全；速读中《From Parameter Dynamics》和《One Step to the Side》则揭示了安全退化风险与自适应攻击的脆弱性。  
普通读者可优先关注微调时的安全-性能权衡方案，并警惕现有防御在强对抗下的失效。
- 详情：[/20260429-20260528/README](/20260429-20260528/README)

### 精读区论文标签
1. [DynaMiCS: Fine-tuning LLMs with Performance Constraints using Dynamic Mixtures](/20260429-20260528/2605.10770v1-dynamics-fine-tuning-llms-with-performance-constraints-using-dynamic-mixtures)  
   标签：评分：10.0/10、query:smd
   evidence：DynaMiCS提出动态数据混合优化，在微调过程中保留安全等约束域性能
2. [RefusalGuard: Geometry-Preserving Fine-Tuning for Safety in LLMs](/20260429-20260528/2605.01913v1-refusalguard-geometry-preserving-fine-tuning-for-safety-in-llms)  
   标签：评分：9.0/10、query:smd
   evidence：针对微调导致的安全退化问题
3. [Self-Mined Hardness for Safety Fine-Tuning](/20260429-20260528/2605.03226v1-self-mined-hardness-for-safety-fine-tuning)  
   标签：评分：9.0/10、query:smd
   evidence：自我挖掘困难度进行安全数据选择并与良性提示混合
4. [Safety Anchor: Defending Harmful Fine-tuning via Geometric Bottlenecks](/20260429-20260528/2605.05995v1-safety-anchor-defending-harmful-fine-tuning-via-geometric-bottlenecks)  
   标签：评分：9.0/10、query:smd
   evidence：通过几何瓶颈正则化防御有害微调攻击
5. [Safety Anchor: Defending Harmful Fine-tuning via Geometric Bottlenecks](/20260429-20260528/2605.05995v2-safety-anchor-defending-harmful-fine-tuning-via-geometric-bottlenecks)  
   标签：评分：9.0/10、query:smd
   evidence：直接防御有害微调，通过几何瓶颈正则化
6. [Few-Shot Truly Benign DPO Attack for Jailbreaking LLMs](/20260429-20260528/2605.10998v1-few-shot-truly-benign-dpo-attack-for-jailbreaking-llms)  
   标签：评分：9.0/10、query:smd
   evidence：良性DPO攻击表明微调中需谨慎选择安全数据以缓解越狱风险
7. [GradShield: Alignment Preserving Finetuning](/20260429-20260528/2605.14194v1-gradshield-alignment-preserving-finetuning)  
   标签：评分：9.0/10、query:smd
   evidence：在微调过程中过滤有害数据点以保持对齐

### 速读区论文标签
1. [From Parameter Dynamics to Risk Scoring : Quantifying Sample-Level Safety Degradation in LLM Fine-tuning](/20260429-20260528/2605.04572v1-from-parameter-dynamics-to-risk-scoring--quantifying-sample-level-safety-degradation-in-llm-fine-tuning)  
   标签：评分：8.0/10、query:smd
   evidence：量化样本级安全风险，指导安全数据选择
2. [One Step to the Side: Why Defenses Against Malicious Finetuning Fail Under Adaptive Adversaries](/20260429-20260528/2605.14605v1-one-step-to-the-side-why-defenses-against-malicious-finetuning-fail-under-adaptive-adversaries)  
   标签：评分：8.0/10、query:smd
   evidence：分析在自适应对手下防御有害微调失败的原因
3. [Be Kind, Rewrite: Benign Projections via Rewriting Defend Against LLM Data Poisoning Attacks](/20260429-20260528/2605.19147v1-be-kind-rewrite-benign-projections-via-rewriting-defend-against-llm-data-poisoning-attacks)  
   标签：评分：8.0/10、query:smd
   evidence：通过重写方式防御数据投毒，利用良性样本
4. [Jailbreak to Protect: Buffering and Reinforcing via Temporary Jailbreaking for Safe Fine-Tuning in Large Language Models](/20260429-20260528/2605.24550v1-jailbreak-to-protect-buffering-and-reinforcing-via-temporary-jailbreaking-for-safe-fine-tuning-in-large-language-models)  
   标签：评分：8.0/10、query:smd
   evidence：通过临时越狱和缓冲有害更新来防御有害微调
5. [You Snooze, You Lose: Automatic Safety Alignment Restoration through Neural Weight Translation](/20260429-20260528/2605.04992v1-you-snooze-you-lose-automatic-safety-alignment-restoration-through-neural-weight-translation)  
   标签：评分：7.0/10、query:smd
   evidence：微调后恢复安全对齐
6. [Preference-aware Influence-function-based Data Selection Method for Efficient Fine-Tuning](/20260429-20260528/2605.21422v1-preference-aware-influence-function-based-data-selection-method-for-efficient-fine-tuning)  
   标签：评分：7.0/10、query:smd
   evidence：基于影响函数和偏好感知的微调数据选择方法
7. [PoisonForge: Task-Level Targeted Poisoning Benchmark for Instruction-Tuned LLMs](/20260429-20260528/2605.23168v1-poisonforge-task-level-targeted-poisoning-benchmark-for-instruction-tuned-llms)  
   标签：评分：7.0/10、query:smd
   evidence：大语言模型微调任务级投毒攻击基准
8. [SafeTune: Mitigating Data Poisoning in LLM Fine-Tuning for RTL Code Generation](/20260429-20260528/2604.27238v1-safetune-mitigating-data-poisoning-in-llm-fine-tuning-for-rtl-code-generation)  
   标签：评分：6.0/10、query:smd
   evidence：SafeTune框架防御LLM微调中的数据投毒，集成安全验证
9. [BSO: Safety Alignment Is Density Ratio Matching](/20260429-20260528/2605.12339v1-bso-safety-alignment-is-density-ratio-matching)  
   标签：评分：6.0/10、query:smd
   evidence：密度比匹配用于安全对齐，可应用于数据混合场景
10. [From Instance Selection to Fixed-Pool Data Recipe Search for Supervised Fine-Tuning](/20260429-20260528/2605.12944v1-from-instance-selection-to-fixed-pool-data-recipe-search-for-supervised-fine-tuning)  
   标签：评分：6.0/10、query:smd
   evidence：包含混合操作的数据配方搜索用于微调
11. [On-Policy Consistency Training Improves LLM Safety with Minimal Capability Degradation](/20260429-20260528/2605.21834v1-on-policy-consistency-training-improves-llm-safety-with-minimal-capability-degradation)  
   标签：评分：6.0/10、query:smd
   evidence：通过在线策略一致性训练提升LLM安全，减轻越狱和谄媚


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
