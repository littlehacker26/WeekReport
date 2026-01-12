## 上周工作
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
- 整理c2s、c2s scale、langcell、 CellWhisperer这四个模型的数据
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
# 2025-12-31
## 上周工作
- 将cellwhisper的部分预训练数据集（cellxgene，37899条）以tahoe的toknizer方式进行转换；
- 创建细胞分类任务的prompt template，实现细胞语言和自然语言对齐。
## 问题方案
- 根据数据集中细胞的meta信息新建其他任务的prompt template；
- 目前脚本对于细胞的meta信息多时处理数据比较慢，优化脚本批量快速处理数据。
- 对于cellwhisperer模型的机理还存在疑问：如何在mistral做chat model training这一步，如何构建prompt以及如何实现多轮对话。
## 下周计划
- 以cellwhisperer和c2s-scale数据集创建prompt template，并按任务类型整理到excel表中；
- 将cellwhisperer和c2s-scale的全部训练数据集实现以tahoe的toknizer方式转换，并实现细胞语言和自然语言对齐；
- 优化脚本，实现快速批量处理数据。
- 复现cellwhisperer chat model training这一步，学会利用该数据集构建prompt。
# 2025-1-7
## 上周工作
- 根据cellwhisperer cellxgene数据集设计两类任务：（1）细胞注释任务；（2）AI设计对话。
- 根据c2s-scale 跨组织免疫细胞数据集设计细胞类型预测任务。
## 问题方案
- 单细胞中基因≤2048；
- 单细胞中基因按照表达量降序排列，若相同表达量则按照token id升序排列；
- 每类SFT任务设计固定格式；
- message和cell_info放进不同文件中。
## 下周计划
- 按照方案重新整理数据集。
- 设计多细胞组织预测任务、细胞生成任务、扰动响应预测任务。
## 任务
- tahoe的toknizer方式转换。
- 把cell2setence/whispercell 的数据，用tahoe的toknizer方式转换。（understand和generation） f"{cell_token} natural language prompt!"
  - e.g., query: please tell me the cell's type the cell is {cell1}"  response: ok, the cell is txxxx.
      cell_inf：cell1: {gene_id, express:value}
      cell_metainf: {xxxxx}
- 按照任务形式分类，形式按照你想要的整理。
