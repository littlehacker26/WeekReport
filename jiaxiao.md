<img width="174" height="81" alt="image"   “图像” src="https://github.com/user-attachments/assets/d34c3059-49b8-45a9-b0b9-dac3133fee7e" /><img width="1701" height="81" alt="image"   “图像” src="https://github.com/user-attachments/assets/57ae016e-a380-40cd-a1c2-d8e07f4f4d9a" /><img width="489" height="81" alt="image"   “图像” src="https://github.com/user-attachments/assets/d4df8230-aae9-4fde-83b9-94f6a1c984e5" />2025-11-19
---

**上周工作**
- 复现 scGPT 模型

**问题方案**
- 解决 scGPT 模型运行中的依赖与显存问题  
- 学习单细胞大模型训练流程，整理相关笔记

**下周计划**
- [x] 复现 sci-adv 文章中的模型。
- [x] 熟悉 AMP 设计相关算法。
- [x] 整理近 2 年的 AMP 相关论文（尽量多整理一些）。
- [x] 学习 Markdown 语法 。     Learn Markdown syntax.Learn Markdown syntax. Learn Markdown syntax.学习 Markdown 语法。学习 Markdown 语法。Learn Markdown syntax. Learn Markdown syntax.Learn Markdown syntax. Learn Markdown syntax. Learn Markdown syntax. Learn Markdown syntax.Learn Markdown syntax. Learn Markdown syntax.Learn Markdown syntax. Learn Markdown syntax. Learn Markdown syntax. Learn Markdown syntax.


2025-11-26
---
**上周工作**
- [x] 复现 sci-adv 文章中的模型（可以完全跑通，但在加载权重文件时出了点儿小问题，导致MIC预测的不同短肽结果为常数，没有差异。）
- [x] 熟悉 AMP 设计相关算法（四个模型+1个强化学习，只熟悉了AMP_GPT_generator.py和AMP_prompt_generator.py）。- [x] Familiar with AMP design-related algorithms (four models, one reinforcement learning; only familiar with AMP_GPT_generator.py and AMP_prompt_generator.py).- [x] Familiar with AMP design-related algorithms (four models, one reinforcement learning; only familiar with AMP_GPT_generator.py and AMP_prompt_generator.py).
- [x] 整理近 2 年的 AMP 相关论文（尽量多整理一些）目前整理15篇（按照作者；年份；发表期刊；主要任务模型等进行整理） 
- [x] 学习 Markdown 语法 （熟悉基本语法）

**问题方案**


**下周计划**
- [x] 继续熟悉sci adv 文章 AMP 设计相关算法。
- [ ] 整理近 2 年的 AMP 相关论文，熟悉其他AMP生成的算法并进行小结。
- [x] Summary AMP生成式的相关文章数据来源、格式和数量（彻底搞清楚模型的输入，做几页PPT整理）。

**近2年的AMP相关论文——数据来源、相关算法**

- |序号|年份|第一作者|论文题目|期刊|主要任务类型|模型及算法|数据类型|
- |------------------------------------------------------------|
- |01|2025|J. Liu et al.|A Multi-Property Optimizing Generative Adversarial Network for de novo Antimicrobial Peptide Design|Adv. Sci|de novo 抗菌肽设计 + 多属性优化|MPOGAN：RNN 生成器 + 基于 ESM-2 的判别器 + 多个“插拔式”属性预测器（活性、毒性、多样性）|已验证 AMP 来自 SATPdb、CAMPR4、dbAMP、DRAMP、LAMP 等数据库；非 AMP 序列来自 UniProt；部分候选肽进行体外 MIC / 细胞毒性实验验证|


Adv. Sci|


