2025-11-19

**上周工作**
- 复现 scGPT 模型

**问题方案**
- 解决 scGPT 模型运行中的依赖与显存问题  
- 学习单细胞大模型训练流程，整理相关笔记

**下周计划**
- [x] 复现 sci-adv 文章中的模型。
- [x] 熟悉 AMP 设计相关算法。
- [x] 整理近 2 年的 AMP 相关论文（尽量多整理一些）。
- [x] 学习 Markdown 语法 。       Learn Markdown syntax.   Learn Markdown syntax.

2025-11-26
---
**上周工作**
- [x] 复现 sci-adv 文章中的模型（可以完全跑通，但在加载权重文件时出了点儿小问题，导致MIC预测的不同短肽结果为常数，没有差异。）
- [x] 熟悉 AMP 设计相关算法（四个模型+1个强化学习，只熟悉了AMP_GPT_generator.py和AMP_prompt_generator.py）。
- [x] 整理近 2 年的 AMP 相关论文（尽量多整理一些）目前整理15篇（按照作者；年份；发表期刊；主要任务模型等进行整理） 
- [x] 学习 Markdown 语法 （熟悉基本语法）

**问题方案**


**下周计划**
- [x] 继续熟悉sci adv 文章 AMP 设计相关算法。
- [ ] 整理近 2 年的 AMP 相关论文，熟悉其他AMP生成的算法并进行小结。
- [x] Summary AMP生成式的相关文章数据来源、格式和数量（彻底搞清楚模型的输入，做几页PPT整理）。

**近2年的AMP相关论文——数据来源、相关算法**

| 年份 (Year) | 第一作者 (First) | 论文标题 (Title Short) | 期刊/会议 (Journal or Venue) | 任务类型 (Task Type) | 主要算法/模型 (Main Model or Algorithm) | 数据来源 (Data Sources) | 评价指标 (Evaluation Metrics) | 链接 (Link) | 分类 (Category) | 核心创新 (Key Innovation) | 给初学者的提示 (Notes for Beginners) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2025 | Liu, Jiaming | A Multi-Property Optimizing Generative Adversarial Network for de novo Antimicrobial Peptide Design | Advanced Science (Adv. Sci.) | de novo 抗菌肽设计 + 多属性优化 | MPOGAN：RNN 生成器 + 基于 ESM-2 的判别器 + 多个“插拔式”属性预测器（活性、毒性、多样性） | 已验证 AMP 来自 SATPdb、CAMPR4、dbAMP、DRAMP、LAMP 等数据库；非 AMP 序列来自 UniProt；部分候选肽进行了体外 MIC / 细胞毒性实验验证 | AMP 判别器：Accuracy、F1、Sensitivity、MCC、AUC；生成模型：预测的活性/毒性评分（如 P_AMP、P_Toxin）、满足多属性阈值的比例、多样性指数（Shannon/Simpson、编辑距离），以及实验测得的 MIC、CC50/HC50、选择性指数等 | https://doi.org/10.1002/advs.202503443 | GAN / 多属性 AMP 设计 | 提出 MPOGAN 反馈式框架：用多个“模型内嵌筛子”（活性、毒性、多样性）从生成肽中筛选高质量样本，并通过实时知识更新（RTKU）构建动态数据集，对 GAN 持续对抗微调，在多属性标注数据极少的情况下实现 AMP 的活性↑、毒性↓、多样性↑，并通过合成 10 条肽（其中 9 条有效）的实验结果验证框架有效性 | 适合学习“生成–评估–筛选–再训练”闭环式优化思路。建议先看 Figure 1 把预训练 + MPO 两个阶段搞清楚，再重点看三类筛子和 RTKU 怎么构造；先理解整体 pipeline 和模块作用，再看公式细节。 |



