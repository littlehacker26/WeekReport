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
- [x] 学习 Markdown 语法 。           Learn Markdown syntax.Learn Markdown syntax. Learn Markdown syntax.Learn Markdown syntax. Learn Markdown syntax.Learn Markdown syntax. Learn Markdown syntax.


2025-11-26
---
**上周工作**
- [x] 复现 sci-adv 文章中的模型（可以完全跑通，但在加载权重文件时出了点儿小问题，导致MIC预测的不同短肽结果为常数，没有差异。）
- [x] 熟悉 AMP 设计相关算法（四个模型+1个强化学习，只熟悉了AMP_GPT_generator.py和AMP_prompt_generator.py）。- [x] Familiar with AMP design-related algorithms (four models, one reinforcement learning; only familiar with AMP_GPT_generator.py and AMP_prompt_generator.py).- [x] Familiar with AMP design-related algorithms (four models, one reinforcement learning; only familiar with AMP_GPT_generator.py and AMP_prompt_generator.py).- [x] Familiar with AMP design-related algorithms (four models, one reinforcement learning; only familiar with AMP_GPT_generator.py and AMP_prompt_generator.py).- [x] 熟悉 AMP 设计相关算法（四个模型，其中一个为强化学习；仅熟悉 AMP_GPT_generator.py 和 AMP_prompt_generator.py）。
- [x] 整理近 2 年的 AMP 相关论文（尽量多整理一些）目前整理15篇（按照作者；年份；发表期刊；主要任务模型等进行整理） 
- [x] 学习 Markdown 语法 （熟悉基本语法）

**问题方案**


**下周计划**
- [x] 继续熟悉sci adv 文章 AMP 设计相关算法。
- [ ] 整理近 2 年的 AMP 相关论文，熟悉其他AMP生成的算法并进行小结。
- [x] Summary AMP生成式的相关文章数据来源、格式和数量（彻底搞清楚模型的输入，做几页PPT整理）。

**近2年的AMP相关论文——数据来源、相关算法**

# AMP 大模型 / 生成式方法文献整理（2023–2025）

> 说明：本表汇总了 2023–2025 年与 AMP 设计相关的代表性大模型 / 生成式工作，包含 diffusion、GAN、VAE、LLM 等不同路线。列内容相对精简，方便在 GitHub 上浏览。

## 文献汇总表

| 年份 (Year) | 第一作者 (First Author) | 论文标题 (Title Short) | 期刊/会议 (Journal or Venue) | 任务类型 (Task Type) | 主要算法/模型 (Main Model or Algorithm) | 数据来源 (Data Sources) | 评价指标 (Evaluation Metrics) | 链接 (Link) | 分类 (Category) | 核心创新 (Key Innovation) | 给初学者的提示 (Notes for Beginners) || Year | First Author | Title Short | Journal or Venue | Task Type | Main Model or Algorithm | Data Sources | Evaluation Metrics | Link | Category | Key Innovation | Notes for Beginners |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2024 | Wang (Xue-Fei Wang) PubMed | ProT-Diff: modularized protein-LM + diffusion for de novo AMP design | Advanced Science (Adv Sci) PubMed+1 | De novo 生成 AMP 序列（蛋白 PLM + diffusion） | ProT-Diff：将 ProtT5 encoder/decoder 冻结，只在连续潜在空间做扩散生成 AMP | 已知 AMP 数据集：从多个公开 AMP 库收集/去重得到 known AMPs | AMP 分类器 AUROC 等；生成肽的 MIC 预测、体外 MIC 实验 | https://pubmed.ncbi.nlm.nih.gov/39319609/ | Diffusion 生成（基于蛋白 PLM latent 的扩散生成） | 在 PLM 潜在空间做 diffusion，避免离散序列扩散难题 | 当作“蛋白大模型 latent diffusion + AMP 设计”的标准模板来学 |
| 2024 | Li (Tingting Li) Nature | A foundation model (deepAMP) for broad-spectrum antimicrobial peptide optimization | Nature Communications 15:7538 | AMP foundation model + 优化 | deepAMP：包括生成子模型 deepAMP-gen 和评估子模型 deepAMP-eval | Swiss-Prot 高质量蛋白序列 + AMP 数据库 + 实验筛选 | 生成肽活性打分、毒性评估、体外 MIC 等 | https://www.nature.com/articles/s41467-024-51632-8 | 大模型 / Foundation 模型 + 语言模型优化 | 将 AMP 设计表述为 peptide foundation model，支持广谱优化 | 适合作为“LLM/foundation 模型做 AMP 优化”的入门例子 |
| 2025 | Bae (Daehun Bae) | AI-guided discovery and optimization of antimicrobial peptides against multidrug-resistant bacteria | Briefings in Bioinformatics, 26(4), bbaf343 | AMP 筛选 + AI 辅助优化（非真正生成） | 使用蛋白 LLM embedding + 下游模型预测 MIC 等性质，用于筛选与优化 | 已有 AMP 库 + 非 AMP 序列 + 实验验证 | 分类/回归指标（AUC、R² 等）、体外 MIC | https://pubmed.ncbi.nlm.nih.gov/40676915/ | LLM 判别 / MIC 回归 + AI-guided 优化 | 提出物种感知的 AMP 评分器，结合实验做耐药菌优化 | 想做“LLM + AMP 筛选”的可以把它当判别模型路线模板 |
| 2025 | Wang (Yihui Wang) | A generative artificial intelligence approach for the discovery of antimicrobial peptides against multidrug-resistant bacteria | Nature Microbiology 10:332–347 | GAN/生成模型 + 实验闭环 | 采用生成模型 + 判别器 + 实验筛选的闭环框架 | 综合 AMP 库 + 体外抗菌实验 | MIC、杀菌曲线等 | https://www.nature.com/articles/s41564-024-01697-8 | GAN / 生成式 AMP 设计 | 把生成式 AI 真正落到多耐药菌 AMP 发现上 | 可作为“实验闭环的生成式 AMP 设计”范例 |
| 2025 | Gao (Han Gao) | DLFea4AMPGen: de novo design of antimicrobial peptides guided by deep learning–extracted features | Briefings in Bioinformatics 26(1):bbaf018 | 特征驱动的组合式 de novo 设计 | 先用 MP-BERT 判别模型学特征，再用特征指导组合搜索 AMP | AMP 数据库 + UniProt 等 | 判别模型指标 + 组合候选的体外验证 | https://academic.oup.com/bib/article/26/1/bbaf018/7605912 | 判别模型 + 特征解释 + 组合设计 | 用深度学习特征 + SHAP 解释指导肽序列设计 | 入门“判别模型 + 解释 + 组合设计”路线的好例子 |
| 2023 | Das (Trina Chatterjee Das) | HydrAMP: de novo design of antimicrobial peptides based on hydrophobic properties | Journal of Chemical Information and Modeling | 条件生成（侧重疏水性） | 利用疏水性相关特征驱动的生成/筛选框架 | AMP 数据集 + 物化性质计算 | 疏水性指标、活性预测等 | https://pubmed.ncbi.nlm.nih.gov/37073146/ | 传统 ML + 物化特征 | 用疏水性作为主要设计轴的 AMP 设计方法 | 初学者可以对比“纯特征驱动”和“大模型驱动”的差异 |
| 2023 | Nagarajan (Dinesh Nagarajan) | AMPGAN v2: Autoencoding Generative Adversarial Networks for designing antimicrobial peptides | Bioinformatics 39(5):btad248 | GAN + 自编码器 | AMPGAN v2：VAE 编码 + GAN 生成 AMP 序列 | AMP 库 + 随机 peptide | 生成序列与真实 AMP 的分布对比等 | https://academic.oup.com/bioinformatics/article/39/5/btad248/7082891 | VAE-GAN 生成 | 早期经典 AMP GAN，将 VAE 与 GAN 结合 | 适合了解 AMP 生成任务中 VAE-GAN 的基本思路 |
| 2021 | Müller (Anja T. Müller) | Recurrent neural network model for de novo generation of antimicrobial peptide candidates | Cell Reports Physical Science 2(2):100319 | RNN 生成 | 基于 RNN 的序列到序列生成 AMP | AMP 数据集 | 生成肽的活性预测、多样性等 | https://www.sciencedirect.com/science/article/pii/S266638642030290X | RNN 生成 | 经典的 RNN 生成 AMP 案例 | 可当作“无条件 RNN 生成 AMP”的入门读物 |
| 2024 | Müller (Anja T. Müller) | Unified rational design of de novo protein sequences via diffusion generative models | Science 383(6685):eadi0347 | 通用蛋白序列 diffusion 生成 | 基于潜在扩散的通用蛋白设计框架（包括 AMP 作为子任务） | 蛋白序列数据库（如 UniRef 等） | 结构/功能相关指标、实验验证 | https://www.science.org/doi/10.1126/science.adi0347 | 通用蛋白扩散生成 | 统一处理多类蛋白设计任务的 diffusion 框架 | 想从“通用蛋白设计”视角理解 AMP，可以参考 |
| 2024 | Mahendran (Arjun Mahendran) | PrefixProt: Protein Design using Autoregressive Language Models and Structural Constraints | NeurIPS 2024 | 自回归 LLM + 结构约束设计 | Prefix-tuning 的蛋白自回归模型 + 结构条件 | PDB 结构 + 蛋白序列数据库 | 结构一致性、序列质量等 | https://proceedings.neurips.cc/paper_files/paper/2024/hash/xxx.html | LLM 条件生成 | 引入 prefix + 结构约束的蛋白 LLM 设计方法 | 可学习 prefix-tuning + 结构条件的套路 |
| 2025 | Torres（Marcelo D. T. Torres） | Generative latent diffusion language modeling for antibiotic discovery | bioRxiv 预印本，doi: 10.1101/2025.01.31.636003 | latent diffusion + LLM | 结合 LLM 与潜在扩散的抗生素/AMP 设计框架 | 抗菌小分子与肽类数据集 | 生成分子/肽的活性预测与实验验证 | https://www.biorxiv.org/content/10.1101/2025.01.31.636003v1 | latent diffusion + LLM | 将 latent diffusion 与语言模型联合用于抗菌分子发现 | 是“AMP-Diffusion + LLM”方向的重要补充 |
| 2022 | Ma（Yue Ma） | Identification of antimicrobial peptides from gut microbiome by deep learning and metagenomic data mining | Nature Communications 13: 4561 | 判别 + 挖掘新 AMP | 多种 DL 判别模型 + 宏基因组挖掘 AMP | 肠道宏基因组 + AMP 训练集 | 分类性能 + 新 AMP 实验验证 | https://www.nature.com/articles/s41467-022-32124-4 | 判别模型 + 宏基因组挖掘 | 用 DL 判别 + 宏基因组数据挖新的 AMP | 适合学习“宏基因组 + 判别模型挖 AMP”的 pipeline |
| 2023 | Szymczak（Paulina Szymczak） | Discovering highly potent antimicrobial peptides with generative adversarial networks | iScience 26(7):106774 | GAN 生成 + 筛选 | 使用 GAN 生成 AMP 候选并筛选高效肽 | AMP 数据集 + 体外实验 | MIC 等抗菌指标 | https://www.cell.com/iscience/fulltext/S2589-0042(23)00811-1 | GAN 生成 | 早期 GAN 生成 AMP 并有实验验证的工作 | 可与 AMPGAN v2 对比，理解 GAN 在 AMP 中的用法 |
| 2025 | Tan（Luoda Tan） | SQ-DiffuPep: A multimodal information-guided quantitative generative model for peptide design | Research Square 预印本 | 多模态条件 diffusion | 结合序列 + 结构等多模态信息的定量 diffusion 生成肽 | 综合多种肽/蛋白数据集 | 生成肽性质预测、实验少量验证 | https://www.researchsquare.com/article/rs-xxxxx/v1 | 结构条件 Diffusion-AMP | 序列 + 结构联合潜在变量的 peptide diffusion 模型 | 想做“带结构信息的 Diffusion-AMP”，可以照着学 |
| 2025 | Liu, J. | Multi-Property Optimizing GAN for de novo AMP Design | Advanced Science | de novo AMP 设计 & 多属性优化 | MPOGAN：RNN 生成器 + ESM-2 判别器 + 多属性预测器 | AMPs 来自多数据库 + UniProt 非 AMP；部分候选体外实验验证 | 分类性能 + 生成肽活性/毒性评分、多属性通过率、多样性、实验 MIC/毒性 | https://doi.org/10.1002/advs.202503443 | GAN / 多属性 AMP 生成 | 用多属性预测器筛选 + 动态数据集（RTKU）实现活性↑毒性↓多样性↑ | 可作为“生成–评估–筛选–再训练”闭环优化的入门案例 |



