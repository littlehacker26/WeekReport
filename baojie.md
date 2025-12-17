<img width="567" height="105" alt="image" src="https://github.com/user-attachments/assets/1e7741e3-2a00-429c-a583-12a6b75e1cc4" />## 上周工作
* 复现c2s模型
- 复现c2s-scale模型
## 问题方案 
+ 全面认识单细胞数据
- 阅读大语言模型单细胞相关文献，整理预训练方法
## 下周计划 
- 调研整理单细胞数据预训练方法、
* 理解transformer模型架构及attention机制
# 2025-11-26
## 上周工作
* 整理预训练方法
* 跑通tahoe-x1预训练代码
## 问题方案
* 预训练方法整理不够全面，对于数据结构，文件类型理解还不够到位
## 下周计划
* 继续调研预训练方法，以ppt形式展示，调研近2-3年内所有的预训练方法，明白原理
* 复线c2s模型中细胞数据与自然语言对齐这一步，明白其中原理
* 搞清楚c2s、c2s scale、langcell、 CellWhisperer这四个模型的数据（来源、是否开源、链接、数据类型）
# 2025-12-3
## 上周工作
- 整理预训练方法
- [整理c2s、c2s scale、langcell、 CellWhisperer这四个模型的数据](https://github.com/Jaybao420/note/blob/7f46be51912ab0516096322e85f0b168f2ca011f/Data.md)
- 复现c2s模型中细胞数据与自然语言拼接，prompt_formatter.py
## 问题方案
- 对于scGPT、BiomedGPT的自监督类型分类还存在疑问。
- AnnData到Arrow dataset时，文件过大会Kernel崩溃。
## 下周计划
- 继续读文献，整理预训练方法。
- 完善数据整理，呈现数据样例。
- 复现tGPT和Tahoe-x1.
- 搭好模型框架
# 2025-12-10
## 上周工作
- 在tGPT模型的基础上进行修改，增加了Gene-expression head，实现预训练推测基因表达量。
- 在新模型上进行初步预训练（数据集为36万个免疫细胞图谱），得到训练集及验证集的loss与 perplexity 曲线。
## 问题方案
- 对于新模型的评估方法还不明确。
## 下周计划
- 复现Geneformer，掌握评估及验证方法。
- 设计新模型的评估及验证方案。
- 优化新模型
# 2025-12-17
## 上周工作
- 评估tGPTexpr模型，计算预测表达量及基因token的MSE，并进行pearson相关性分析。
- 调研虚拟细胞领域，并了解scGPT模型。
## 问题方案
- tGPTexpr模型预测表达值的MSE过低（＜0.015）
- 对于scGPT模型的原理了解不够（预训练任务原理、虚拟扰动原理）
- 对于目前tGPTexpr模型思路，仅仅预测表达量创新性不够。
## 下周计划
- tGPTexpr朝着虚拟细胞方向发展。
- 精读scGPT这篇文献，讲明白原理（预训练任务原理、虚拟扰动原理）
