# 通用多肽从头设计 Agent：相关数据库与数据资源总目录

**版本：** v1.0\
**检索日期：** 2026-10-23\
**用途：**
多肽从头设计、生成模型训练、功能预测、结构建模、靶点发现、新颖性检测及实验验证。

> 说明：本目录覆盖与多肽设计高度相关的主要公开数据库、数据仓库、知识平台及计算工具，不宣称穷尽全球所有数据库。各资源的版本、维护状态、字段、API
> 和许可可能发生变化，正式接入前应重新核查。

## 一、数据库体系总览

通用多肽设计 Agent 不应只收集序列。建议建设以下九类数据资源。

  ---------------------------------------------------------------------------------------------------------------
  类别                    核心问题                                 代表资源
  ----------------------- ---------------------------------------- ----------------------------------------------
  多肽序列与功能          哪些肽具有已知功能？                     APD、DRAMP、DBAASP、dbAMP、CancerPPD2

  蛋白质序列与功能注释    肽来自哪个前体？靶蛋白是什么？           UniProt、NCBI Protein、RefSeq、InterPro

  三维结构                靶点结构、肽构象和复合物是什么？         PDB、AlphaFold DB、PDBe

  靶点与疾病              疾病对应什么靶点？靶点是否适合研究？     Open Targets、HPA、DepMap

  结合与生化活性          肽是否结合靶点？活性多强？               BindingDB、ChEMBL、PubChem BioAssay、BRENDA

  安全性与可开发性        是否存在溶血、毒性或稳定性问题？         Hemolytik、ToxinPred、DBAASP

  化学修饰与蛋白质组学    修饰发生在哪里？实验中检测到了哪些肽？   PhosphoSitePlus、GlyGen、PeptideAtlas、PRIDE

  文献、专利与临床        已有哪些研究、专利和临床开发记录？       Europe PMC、PubMed、Google
                                                                   Patents、ClinicalTrials.gov

  序列和结构新颖性        候选是否与已知分子相似？                 BLAST、MMseqs2、Foldseek、GraphPart
  ---------------------------------------------------------------------------------------------------------------

## 二、多肽序列与功能数据库

### 2.1 核心抗微生物肽数据库

#### 1. APD / APD6

-   **官网：** https://aps.unmc.edu/
-   **数据库检索：** https://aps.unmc.edu/database
-   **关于页面：** https://aps.unmc.edu/about
-   **类型：** 抗微生物肽与宿主防御肽数据库。

**主要信息** - 氨基酸序列、长度、名称及来源物种。 -
抗细菌、抗真菌、抗病毒等功能分类。 - 净电荷、疏水性及其他理化性质。 -
化学修饰、结合靶点和结构信息。 - PDB 结构链接、文献和来源注释。 -
相关检索、预测和序列分析工具。

**对 Agent 的用途：**
学习天然抗微生物肽的序列分布、功能类别和理化性质，辅助生成条件及候选相似性检索。

**注意事项：**
当前站点包含的资源类型可能不止实验验证的天然肽。训练时应区分实验整理记录、合成肽和计算预测条目。APD
历史版本的论文统计不能直接当作当前数据库规模。

#### 2. DRAMP 4.0

-   **官网：** https://dramp.cpu-bioinfor.org/
-   **论文：** https://doi.org/10.1093/nar/gkae1046
-   **类型：** 抗微生物肽综合数据库。

**主要信息** - 多肽序列、长度和来源。 - 抗微生物活性及目标对象。 -
理化性质、结构和文献。 - 部分开发、临床或相关注释。

**对 Agent 的用途：** 扩展 AMP
训练数据覆盖面，建立功能标签和序列---性质关系。

**注意事项：**
应按记录核实证据来源、标签类型和数据版本，不能把所有注释都当成实测值。

#### 3. DBAASP

-   **官网：** https://dbaasp.org/
-   **数据库说明：** https://dbaasp.dbaasp.niaidprod.net/about
-   **帮助文档：** https://dbaasp.dbaasp.niaidprod.net/help
-   **类型：** 抗微生物肽结构与实验活性数据库。

**主要信息** - 实验测试肽的序列和化学结构。 -
目标物种、菌株及活性数据。 - MIC 等定量活性结果。 -
溶血、细胞毒性及相关实验信息。 - N/C 端修饰、非天然残基和多链结构。 -
实验条件、文献及部分三维结构。 - 部分协同作用记录及 FICI。 -
检索、性质计算、预测和 API。

**对 Agent 的用途：**
值得优先接入的定量功能数据源，可支持抗微生物活性预测、安全性模型和结构---活性关系分析。

**注意事项：**
同一肽在不同菌株、培养基、剂量或实验条件下的结果必须分别保存。单体、多聚体和多肽协同组合不是同一类分子实体。

#### 4. dbAMP 3.0

-   **官网：** https://ycclab.cuhk.edu.cn/dbAMP/
-   **下载：** https://ycclab.cuhk.edu.cn/dbAMP/download2024.php
-   **用户指南：** https://ycclab.cuhk.edu.cn/dbAMP/tutorial.php
-   **类型：** 抗微生物肽与抗微生物蛋白资源。

**主要信息** - 序列及功能分类。 - 目标对象和活性信息。 -
来源物种、参考文献和外部数据库链接。 -
理化性质、结构和部分蛋白互作注释。 - 实验来源与预测来源的分类信息。 -
序列和功能数据下载。

**对 Agent 的用途：** 补充 AMP 多标签数据、目标物种活性和结构注释。

**注意事项：** 公开下载页面标明的 3.0 版本发布于 2024 年 6
月。训练前需要核对当前版本，且不得将预测来源条目直接当成实验标签。

#### 5. CAMP / CAMP-R 系列

-   **官网：** https://camp.bicnirrh.res.in/
-   **类型：** 抗微生物肽序列、结构与预测资源。

**主要信息：** AMP 序列、相关结构或特征、预测方法及部分模型资源。

**用途：** AMP 检索、预测器基线和数据交叉核对。

**注意事项：** 需确认当前版本、维护状态和模型训练集。与
APD、DRAMP、dbAMP 存在来源重叠的记录应去重。

#### 6. SATPdb

-   **官网：** https://webs.iiitd.edu.in/raghava/satpdb/
-   **说明：** https://webs.iiitd.edu.in/raghava/satpdb/about.php
-   **论文：** https://doi.org/10.1093/nar/gkv1114
-   **类型：** 结构注释治疗性多肽整合数据库。

**主要信息** - 多种功能肽序列。 -
抗菌、抗病毒、抗癌、抗寄生虫、细胞穿透、药物递送等类别。 -
天然、非天然和修饰残基。 - 序列与结构相似性检索。 -
部分二级结构和预测三维结构。

**用途：**
跨功能领域候选发现，寻找具有多重功能的肽，并作为其他专用数据库的发现入口。

**注意事项：** SATPdb
是整合资源，可能包含来源数据库中的重复记录。预测结构不能视为实验结构。

### 2.2 抗肿瘤、递送、免疫与其他功能肽

#### 7. CancerPPD2

-   **官网：** https://webs.iiitd.edu.in/raghava/cancerppd2/
-   **API：** https://webs.iiitd.edu.in/raghava/cancerppd2/api/rest.html
-   **论文：** https://doi.org/10.1093/database/baaf030

包含抗肿瘤肽及相关蛋白、序列、化学修饰、肿瘤类型、细胞系、实验方法、活性和文献。

**用途：** 建立抗肿瘤肽数据集，研究不同肿瘤细胞系中的效力与选择性。

**注意：**
细胞死亡不等于靶向作用。不同细胞系、剂量、处理时间和测定方法必须分别记录。

#### 8. CPPsite 2.0 / CPPsite 系列

-   **官网：** https://webs.iiitd.edu.in/raghava/cppsite/
-   **说明：** https://webs.iiitd.edu.in/raghava/cppsite/information.php

包含细胞穿透肽、线性或环状结构、化学修饰、非天然残基、实验验证方法、体外/体内模型及递送载荷。

**用途：** 支持细胞穿透和递送功能分支。

**注意：**
递送性能与载荷、细胞类型、实验方法密切相关；不能把某条肽在一种载荷上的表现直接外推到另一种载荷。

#### 9. AVPdb

-   **相关说明：**
    https://webs.iiitd.edu.in/raghava/satpdb/catalogs/avpdb/
-   **论文：** https://doi.org/10.1093/nar/gkt1191

主要包括实验验证的抗病毒肽、病毒靶标、来源、细胞系、检测方法、定性或定量抑制结果及文献。

**用途：** 抗病毒功能研究和专用训练数据补充。

**注意：**
使用前核实当前站点、版本和数据可用性；不同病毒、细胞模型和作用机制不能混为同一个标签。

#### 10. Hemolytik / Hemolytik 2.0

-   **网站：** https://webs.iiitd.edu.in/raghava/hemolytik/sindex.php
-   **数据仓库：** https://github.com/raghavagps/Hemolytik2

主要包括实验验证的溶血与非溶血肽、序列、结构或 SMILES、来源和文献。

**用途：** 构建溶血预测器，研究序列、结构和宿主红细胞损伤之间的关系。

**注意：**
溶血不是总体安全性的同义词。需要保存红细胞来源、测试浓度、测定方法和实验条件。

#### 11. ToxinPred 3.0

-   **网站：** https://webs.iiitd.edu.in/raghava/toxinpred3/
-   **代码与数据：** https://github.com/raghavagps/toxinpred3
-   **论文：** https://doi.org/10.1016/j.compbiomed.2024.108926

这是毒性预测工具及相关数据资源，而不是单纯的实验数据库。它提供毒性/非毒性预测、序列扫描和
motif 分析。

**用途：** 作为候选安全性筛查基线。

**注意：** 预测毒性不能替代溶血、细胞毒性、免疫原性或体内安全性实验。

#### 12. AHTPDB

-   **说明：** https://webs.iiitd.edu.in/raghava/ahtpdb/info.php
-   **论文：** https://doi.org/10.1093/nar/gku1141

主要包括抗高血压肽、来源、长度、分子量、等电点、IC50/pIC50 及相关文献。

**用途：** 酶抑制和生理调节肽任务。

**注意：** 这是较早的专用资源，需核实当前维护状态和数据版本。

#### 13. BIOPEP-UWM

-   **官网：** https://biochemia.uwm.edu.pl/biopep-uwm/

主要包括生物活性肽、食品蛋白来源、活性片段、酶切/释放信息和相关分析工具。

**用途：** 食品源功能肽、酶抑制肽和活性片段发现。

**注意：** 食品源肽的体外活性不能直接等同于体内药理效应。

#### 14. NeuroPep

-   **入口：** https://isyslab.info/NeuroPep/

面向神经肽，可能包含序列、来源物种、前体、功能/受体和文献信息。

**用途：** 神经调节肽的候选发现。

**注意：**
该资源的当前版本与维护状态需要核实；受体关系应回溯原始实验文献。

#### 15. THPdb

-   **论文：** https://doi.org/10.1371/journal.pone.0181748
-   **全文：** https://pmc.ncbi.nlm.nih.gov/articles/PMC5536290/

原始版本整理 FDA
批准的治疗性肽与蛋白药物，涉及序列/结构、化学性质、靶点、作用机制、适应证、药代、毒性、给药途径、制剂和专利信息。

**用途：** 研究已有治疗性肽的分子设计和开发属性。

**注意：** 原始论文发表于 2017 年。当前药品状态应与 FDA
官方资源交叉核对。

#### 16. IEDB

-   **官网：** https://www.iedb.org/
-   **API：** https://query-api.iedb.org/docs/swagger/

包含免疫表位、线性肽、T/B 细胞实验、MHC
配体、抗原来源、宿主、疾病、HLA/MHC 限制及参考文献。

**用途：** 免疫表位、免疫识别和疫苗相关肽任务。

**注意：** 免疫表位识别不等于抗肿瘤杀伤或一般靶点结合。

#### 17. CEDAR

-   **官网：** https://cedar.iedb.org/

面向癌症相关免疫表位和实验数据，可补充癌症抗原、肽表位、HLA、免疫测定及文献信息。

**用途：** 肿瘤免疫识别任务。

#### 18. PeptideAtlas

-   **官网：** https://www.peptideatlas.org/
-   **概述：** https://www.peptideatlas.org/overview.php

汇集多物种质谱蛋白质组学实验识别到的肽段、对应蛋白、搜索证据、识别概率、FDR
和相关数据集。

**用途：** 获取真实生物样本中检测到的肽段和修饰肽证据。

**注意：** 被质谱检测到不等于具有药理功能。

## 三、蛋白质序列、注释与家族数据库

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  数据库            包含的信息                                                                          在 Agent 中的用途                     官方入口
  ----------------- ----------------------------------------------------------------------------------- ------------------------------------- ------------------------------------------------------
  UniProtKB /       蛋白序列、功能、物种、亚细胞定位、结构域、PTM、成熟链、文献和交叉引用；Swiss-Prot   蛋白身份、前体/成熟肽来源和功能注释   https://www.uniprot.org/
  Swiss-Prot /      人工审校，TrEMBL 主要为计算注释                                                                                           
  TrEMBL                                                                                                                                      

  NCBI Protein      来自多个来源的蛋白序列记录和交叉引用                                                序列检索、BLAST 和来源追踪            https://www.ncbi.nlm.nih.gov/protein/

  NCBI RefSeq       参考基因组、转录本和蛋白序列                                                        获取参考蛋白与物种背景                https://www.ncbi.nlm.nih.gov/refseq/

  Ensembl           基因、转录本、蛋白、异构体、变异及比较基因组学                                      将靶点映射到标准基因/蛋白 ID          https://www.ensembl.org/

  UniParc           多来源蛋白序列及序列历史追踪                                                        序列去重与历史版本追踪                https://www.uniprot.org/uniparc

  InterPro          蛋白家族、结构域、保守位点和功能位点                                                靶蛋白功能与结构域识别                https://www.ebi.ac.uk/interpro/

  Pfam              蛋白家族、结构域、HMM 和多序列比对                                                  家族识别与保守区域分析                https://www.ebi.ac.uk/interpro/entry/pfam/

  PROSITE           蛋白家族模式、profile 和功能位点                                                    motif 与功能模式识别                  https://prosite.expasy.org/

  NCBI CDD          保守结构域和相关模型                                                                靶蛋白结构域定位                      https://www.ncbi.nlm.nih.gov/Structure/cdd/cdd.shtml

  Gene              分子功能、生物过程、细胞组分及证据代码                                              将自然语言功能映射到标准术语          https://geneontology.org/
  Ontology（GO）                                                                                                                              

  PANTHER           蛋白家族、亚家族和功能分类                                                          功能注释与富集分析                    https://www.pantherdb.org/

  eggNOG            直系同源群与跨物种功能注释                                                          同源关系和功能迁移                    http://eggnog5.embl.de/

  MEROPS            蛋白酶/肽酶、底物、抑制剂、序列和结构                                               降解风险、切割位点和酶抑制任务        https://www.ebi.ac.uk/merops/

  BRENDA            酶反应、底物、抑制剂、动力学、pH/温度和文献                                         酶抑制肽和酶底物肽任务                https://www.brenda-enzymes.org/
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 3.1 关键区别

-   UniProt 是蛋白身份和功能注释的核心入口。
-   RefSeq 更偏向参考序列体系。
-   InterPro、Pfam、PROSITE、CDD 主要解释蛋白家族和结构域。
-   GO 用于统一功能术语，但注释证据可能是实验、计算或自动转移。
-   MEROPS 和 BRENDA 对酶底物、抑制剂和降解相关任务尤其有价值。

## 四、三维结构与分子相互作用资源

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  资源              包含的信息                                                       用途                                      注意事项
  ----------------- ---------------------------------------------------------------- ----------------------------------------- ----------------------------------------------
  RCSB PDB          实验测得的蛋白、肽、核酸和复合物结构、链、配体、实验方法和文献   靶点实验结构、肽---蛋白复合物和结合位点   核对构建体、突变、链和实验条件

  PDBe              PDB 结构、实体、链、配体和实验元数据                             结构检索和注释                            与 RCSB 内容大量重叠

  PDBe-KB           结构层级功能、残基和相互作用注释                                 结构与功能证据关联                        需保留每条注释的来源

  AlphaFold DB      大规模蛋白结构预测、pLDDT、PAE 和蛋白注释                        缺乏实验结构时提供结构假设                结构置信度不等于生物学正确性；短肽适用性有限

  ModelArchive      计算结构模型及其元数据                                           保存/检索公开预测模型                     需核查模型质量和来源

  PDBsum            结构摘要、二级结构、结构域、配体和接触信息                       快速查看结构和界面                        回溯原始 PDB 和论文

  GPCRdb            GPCR 序列、结构、配体、药理和突变                                受体靶向、激动/拮抗肽                     专门面向 GPCR

  AlphaFold 3       结构预测模型/服务，不是传统数据库                                复合物结构建模                            必须分别核对代码、权重和 Server 输出许可

  Boltz-2           复合物结构与结合亲和力预测工具                                   候选肽---靶点计算评价                     开放许可不等于所有肽体系都经过验证

  Chai-1            生物分子结构预测工具                                             复合物结构预测候选                        核查模型版本、输入限制和许可
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

官方入口： - [RCSB PDB](https://www.rcsb.org/) - [RCSB
API](https://www.rcsb.org/docs/programmatic-access/web-apis-overview) -
[PDBe](https://www.ebi.ac.uk/pdbe/) -
[PDBe-KB](https://www.ebi.ac.uk/pdbe/pdbe-kb/) - [AlphaFold
DB](https://alphafold.ebi.ac.uk/) - [AlphaFold DB
下载](https://www.alphafold.ebi.ac.uk/download) - [AlphaFold DB FAQ
与限制](https://alphafold.ebi.ac.uk/faq) - [AlphaFold 3
论文](https://doi.org/10.1038/s41586-024-07487-w) - [Boltz
官方仓库](https://github.com/boltzgen/boltz) - [Chai-1
官方仓库](https://github.com/chaidiscovery/chai-lab) -
[GPCRdb](https://gpcrdb.org/)

**结构使用原则：**
实验结构、单体预测结构、复合物预测结构和结构相似性结果必须分开保存。预测的复合物结构不能直接证明真实结合、细胞选择性或治疗效果。

## 五、靶点、疾病、组织与细胞模型资源

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  数据库            包含的信息                                                                     在 Agent 中的用途                      官方入口
  ----------------- ------------------------------------------------------------------------------ -------------------------------------- ---------------------------------------
  Open Targets      靶点---疾病关联、遗传证据、药物/临床证据、表达、通路、相互作用和可成药性注释   从疾病发现和排序候选靶点               https://platform.opentargets.org/
  Platform                                                                                                                                

  Human Protein     人体组织、细胞、亚细胞定位、癌组织、血液和细胞系中的 RNA/蛋白表达              比较靶点在疾病与正常组织中的表达背景   https://www.proteinatlas.org/
  Atlas（HPA）                                                                                                                            

  DepMap            癌细胞系的基因组、转录组、CRISPR/RNAi 依赖、药物筛选和蛋白质组学               研究靶点依赖性与选择实验模型           https://depmap.org/portal/

  DisGeNET          基因/蛋白---疾病关联及文献证据                                                 疾病靶点候选发现                       https://www.disgenet.org/

  ClinVar           人类变异、临床意义和疾病/表型关系                                              检查靶点变异与潜在影响                 https://www.ncbi.nlm.nih.gov/clinvar/

  OMIM              人类基因、遗传表型和疾病信息                                                   遗传病与靶点背景研究                   https://omim.org/

  Orphanet          罕见病、疾病分类和基因关联                                                     罕见病靶点发现                         https://www.orpha.net/

  Reactome          人工整理的生物通路与反应                                                       靶点通路和机制解释                     https://reactome.org/

  STRING            蛋白功能关联网络与多通道证据                                                   靶点功能网络分析                       https://string-db.org/

  BioGRID           文献整理的物理与遗传相互作用                                                   蛋白互作和文献追踪                     https://thebiogrid.org/

  IntAct            分子相互作用、参与者、实验方法和文献                                           互作证据检索                           https://www.ebi.ac.uk/intact/
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**注意：**
疾病---靶点关联分数、基因依赖性和组织表达不能单独证明一个靶点适合多肽药物设计。靶点条件设计还需要结合结构、结合证据、目标细胞背景及实际功能终点。

## 六、结合活性、药理与生化实验数据库

  -----------------------------------------------------------------------------------------------------------------------------------------------------
  数据库            主要信息                                              对 Agent 的用途                    限制
  ----------------- ----------------------------------------------------- ---------------------------------- ------------------------------------------
  BindingDB         实测分子---蛋白结合亲和力，常见                       查找肽/蛋白结合记录与 SAR          主要侧重药物样小分子；需确认实际肽类覆盖
                    Ki、Kd、IC50、靶点、配体和文献                                                           

  ChEMBL            生物活性分子、靶点、assay、标准化活性值、药物和部分   查找肽类或肽样分子的公开药理记录   不保证所有肽都有完整结构与实验数据
                    ADME/毒性数据                                                                            

  PubChem BioAssay  测定说明、测试物质、靶点和实验结果                    查找功能筛选、毒性和生物活性记录   数据来自不同提交者，质量和标准化程度不同

  BRENDA            酶底物、产物、抑制剂、Ki/IC50、动力学及实验条件       酶抑制/底物肽设计                  并非肽专用数据集

  MEROPS            蛋白酶、切割底物、抑制剂、家族和结构                  降解风险和酶抑制机制               必须考虑具体酶和实验条件

  GPCRdb            GPCR 配体、结构、药理和突变信息                       受体调控肽                         只覆盖 GPCR 领域

  DrugBank          药物、靶点、作用机制、适应证和药代信息                已有肽药和蛋白药背景研究           完整访问和再利用可能需要许可

  TTD               治疗靶点、药物、疾病和作用机制                        已知靶点和药理背景                 需核对版本与数据来源
  -----------------------------------------------------------------------------------------------------------------------------------------------------

官方入口： - [BindingDB](https://www.bindingdb.org/rwd/bind/info.jsp) -
[ChEMBL](https://www.ebi.ac.uk/chembl/) - [PubChem
BioAssay](https://pubchem.ncbi.nlm.nih.gov/docs/bioassays) -
[BRENDA](https://www.brenda-enzymes.org/) -
[MEROPS](https://www.ebi.ac.uk/merops/) -
[DrugBank](https://go.drugbank.com/) -
[TTD](https://db.idrblab.net/ttd/)

不同终点必须独立建模。例如，MIC、IC50、EC50、KD、Ki、细胞摄取率和细胞死亡率不能不加区分地合并成一个"活性分数"。

## 七、化学修饰、PTM 与蛋白质组学资源

  -------------------------------------------------------------------------------------------------------------------------------------------
  数据库            包含的信息                                           在 Agent 中的用途            注意事项
  ----------------- ---------------------------------------------------- ---------------------------- ---------------------------------------
  UniProt           成熟链、前肽、二硫键、糖基化、磷酸化及其他蛋白特征   前体加工和天然修饰研究       证据等级不同，不能直接外推到合成肽
  PTM/Feature                                                                                         

  PhosphoSitePlus   磷酸化、乙酰化、甲基化、泛素化、糖基化等 PTM         研究靶蛋白修饰及其功能背景   不是所有合成肽化学修饰的总库
                    位点和文献                                                                        

  dbPTM             蛋白翻译后修饰位点、类型和序列环境                   PTM 相关分析                 需核对当前版本和证据来源

  GlyGen            糖链、糖蛋白、糖基化位点、蛋白和疾病关联             糖肽与糖基化靶点研究         糖链结构与位点依赖具体生物体系

  PRIDE Archive     质谱原始数据、处理结果、元数据和论文链接             重新分析肽段和修饰肽         需保留搜索数据库、处理流程和 FDR

  MassIVE           蛋白质组学/代谢组学原始和处理数据                    补充质谱数据                 不同项目元数据和处理方法差异大

  jPOST             蛋白质组学数据集                                     补充公开质谱数据             按项目元数据和许可使用

  ProteomeXchange   多个蛋白质组学仓库的协调发布和项目元数据             通过论文项目 ID 查找原始数据 是联盟/协调体系，不是单一功能肽数据库
  -------------------------------------------------------------------------------------------------------------------------------------------

官方入口： - [PhosphoSitePlus](https://www.phosphosite.org/psp/) -
[dbPTM](https://awi.cuhk.edu.cn/dbPTM/) -
[GlyGen](https://www.glygen.org/) -
[PRIDE](https://www.ebi.ac.uk/pride/) -
[MassIVE](https://massive.ucsd.edu/) - [jPOST](https://jpostdb.org/) -
[ProteomeXchange](https://www.proteomexchange.org/)

### 7.1 修饰肽必须独立表示

每个化学变体建议记录： - 母体序列 ID； - 修饰后的规范表示； - L/D
残基信息； - 非天然氨基酸类型； - N/C 端修饰； - 环化类型和连接位置； -
二硫键； - 脂化、连接子或载荷偶联； - 适用时的 SMILES、HELM
或其他结构表示； - 参考文献与证据类型。

只用标准 20 种氨基酸的 FASTA 字符串无法完整表示所有多肽药物的化学身份。

## 八、文献、专利、临床和药品信息资源

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  资源                 包含的信息                                                   用途                       官方入口
  -------------------- ------------------------------------------------------------ -------------------------- -------------------------------------------------------------------------------
  PubMed               生物医学文献题录、摘要、PMID、MeSH 和引用信息                论文检索与证据回溯         https://pubmed.ncbi.nlm.nih.gov/

  Europe PMC           文献、开放全文、引用、补充材料链接、部分文本挖掘注释及 REST  Agent 程序化检索           https://europepmc.org/
                       API                                                                                     

  Crossref             DOI、标题、作者、出版信息和文献元数据                        DOI 解析与文献去重         https://www.crossref.org/

  Google Patents       多国专利文献、权利要求、摘要、用途和序列文字                 新颖性与专利线索检索       https://patents.google.com/

  WIPO PATENTSCOPE     国际专利申请和 PCT 文献                                      国际专利检索               https://patentscope.wipo.int/

  Espacenet            全球专利检索和专利家族信息                                   专利交叉核对               https://worldwide.espacenet.com/

  ClinicalTrials.gov   临床研究注册、研究设计、干预、适应证、状态和结果（如提交）   追踪肽药/蛋白药临床开发    https://clinicaltrials.gov/

  Drugs@FDA            批准药品、监管历史、标签和审评文件                           核对药品批准状态和适应证   https://www.accessdata.fda.gov/scripts/cder/daf/

  DailyMed             药品标签、给药信息、警告和不良反应                           药品信息核对               https://dailymed.nlm.nih.gov/dailymed/

  FDA Orange Book      适用药品的等效性、专利和独占期相关信息                       药品和部分专利信息核对     https://www.fda.gov/drugs/drug-approvals-and-databases/orange-book-data-files
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**注意：**
自动化专利检索只能提供公开记录和线索，不能代替法律上的新颖性、创造性或自由实施（FTO）判断。

## 九、序列、结构相似性与辅助工具

  --------------------------------------------------------------------------------------------------------------------------------
  工具              功能                             在 Agent 中的用途                 官方入口
  ----------------- -------------------------------- --------------------------------- -------------------------------------------
  NCBI BLAST        局部序列相似性搜索               查找已知序列和相似候选            https://blast.ncbi.nlm.nih.gov/Blast.cgi

  MMseqs2           大规模序列搜索、聚类和同源检索   数据去重、相似性搜索和数据划分    https://github.com/soedinglab/MMseqs2

  CD-HIT            序列聚类和冗余削减               训练集去重和同源簇划分            https://github.com/weizhongli/cdhit

  GraphPart         同源性感知的数据集划分           减少训练/测试集之间的近同源泄漏   https://github.com/graph-part/graph-part

  Foldseek          结构相似性搜索                   查找已知结构近邻                  https://github.com/steineggerlab/foldseek

  ExPASy ProtParam  分子量、理论                     基础理化性质计算                  https://web.expasy.org/protparam/
                    pI、氨基酸组成等计算                                               

  ExPASy            蛋白酶/化学切割位点预测          初步分析潜在降解位点              https://web.expasy.org/peptide_cutter/
  PeptideCutter                                                                        
  --------------------------------------------------------------------------------------------------------------------------------

### 9.1 新颖性审查至少包括四层

1.  精确序列匹配。
2.  近似序列、局部比对、覆盖率和 motif 检查。
3.  结构相似性检查，并标记结构来源与置信度。
4.  文献和专利检索。

建议报告写成：

> 在指定数据库、版本、检索日期和参数下，未发现完全匹配；发现或未发现若干相似序列/结构。该结果不构成绝对新颖性或专利自由实施的法律结论。

## 十、推荐的数据库接入优先级

### P0：第一阶段必接

  ---------------------------------------------------------------------------------------
  资源                                首批抽取内容
  ----------------------------------- ---------------------------------------------------
  UniProtKB                           蛋白序列、功能、物种、前体/成熟链、PTM、参考文献

  RCSB PDB                            PDB ID、链、结构方法、复合物、靶点和文献

  AlphaFold DB                        蛋白结构预测、pLDDT、PAE、下载版本

  Europe PMC / PubMed                 DOI、PMID、摘要、全文许可、图表/补充材料线索

  DBAASP                              序列/变体、目标菌株、MIC、溶血/细胞毒性、实验条件

  DRAMP、APD、dbAMP                   序列、功能、证据类型、来源、结构和修饰

  CancerPPD2                          序列/变体、细胞系、实验终点、活性和文献

  CPPsite                             序列、修饰、载荷、细胞模型和实验方法

  Open Targets + HPA                  靶点 ID、疾病关联证据、组织和细胞表达

  IEDB                                肽、抗原、HLA/MHC、免疫实验和结果

  ChEMBL + BindingDB + PubChem        化合物/肽结构、靶点、assay、活性值和单位
  BioAssay                            

  Hemolytik + ToxinPred               溶血数据与毒性预测基线

  BLAST/MMseqs2/GraphPart             相似性检索、去重和数据划分
  ---------------------------------------------------------------------------------------

### P1：按功能领域扩展

-   SATPdb：跨领域功能肽发现。
-   BIOPEP-UWM、AHTPDB：食品源活性肽与酶抑制任务。
-   AVPdb：抗病毒肽。
-   NeuroPep：神经肽，需核验当前状态。
-   GPCRdb：GPCR 配体和受体药理。
-   MEROPS、BRENDA：酶底物、抑制剂和蛋白酶敏感性。
-   InterPro、Pfam、PROSITE、GO：蛋白功能本体和结构域。
-   DepMap：癌细胞系和靶点依赖性。
-   PhosphoSitePlus、dbPTM、GlyGen：修饰信息。
-   PeptideAtlas、PRIDE、ProteomeXchange：蛋白质组学原始证据。

### P2：转化和开发阶段扩展

-   THPdb、Drugs@FDA、DailyMed、ClinicalTrials.gov。
-   DrugBank、TTD。
-   Google Patents、WIPO PATENTSCOPE、Espacenet。
-   MassIVE、jPOST。
-   其他专用功能肽数据库。

## 十一、面向 Agent 的统一数据库结构

建议将以下实体分开存储：

  --------------------------------------------------------------------------------------------------------
  表/实体                 关键字段                                                目的
  ----------------------- ------------------------------------------------------- ------------------------
  `peptide_entity`        `peptide_id`, `canonical_sequence`, `length`, `source`, 表示标准序列实体
                          `precursor_id`                                          

  `peptide_variant`       `variant_id`, `peptide_id`, `stereochemistry`,          表示实际化学变体
                          `modifications`, `cyclization`, `structure_repr`        

  `protein_entity`        `protein_id`, `accession`, `sequence`, `organism`,      表示前体蛋白或靶点蛋白
                          `isoform`, `review_status`                              

  `target_entity`         `target_id`, `accession`, `organism`, `isoform`,        标准化用户指定靶点
                          `sequence`, `structure_ids`                             

  `assay_result`          `assay_id`, `variant_id`, `target_id`, `endpoint`,      保存每次实验结果
                          `raw_value`, `raw_unit`, `normalized_value`, `relation` 

  `assay_context`         菌株/细胞系、介质、pH、温度、剂量、时间、方法、重复和   解释测量值的适用条件
                          QC                                                      

  `structure_record`      `structure_id`, `source`, `experimental_or_predicted`,  保存结构及其证据
                          `file_uri`, `confidence`, `model_version`               

  `evidence_record`       DOI、PMID、专利号、数据库                               证据溯源
                          ID、原文位置、证据类型、检索日期                        

  `prediction_run`        `prediction_id`, `candidate_id`, `endpoint`, `value`,   保存计算预测
                          `uncertainty`, `predictor_version`                      

  `design_run`            `task_id`, `spec_version`, `generator_version`, `seed`, 复现生成流程
                          `parameters`, `data_snapshot`                           

  `novelty_result`        数据库快照、检索日期、方法、阈值、命中                  保存新颖性检索结果
                          ID、identity、coverage                                  

  `experiment_feedback`   候选、实验协议版本、终点、原始结果、QC 状态、分析版本   回写实验反馈
  --------------------------------------------------------------------------------------------------------

### 11.1 数据清洗的强制规则

1.  原始数据只读保存，不覆盖。
2.  保留原始单位和原始测量值。
3.  `unknown`、`not measured`、`assay-negative`、`invalid` 必须分开。
4.  同一序列的多个实验结果不能直接平均。
5.  修饰肽与标准肽必须区分化学实体。
6.  预测条目不能自动转换为实验阳性/阴性。
7.  同源序列不能随意分到不同数据集。
8.  所有数据必须保存来源、版本、下载日期和许可信息。

## 十二、数据集划分和模型训练前检查

### 12.1 训练、验证与测试

建议设置： - 训练集； - 验证集； - 同源性感知内部测试集； -
外部测试集； - 靶点外推测试集（用于靶点结合任务）； - 前瞻性实验测试集。

### 12.2 必须检查的数据泄漏

-   完全重复序列是否跨数据集。
-   高相似序列是否跨训练集和测试集。
-   同一论文中的衍生肽是否被分散到不同数据集。
-   数据库整合是否重复计算同一记录。
-   同一靶点或相同结合区域是否泄漏到靶点外推测试集。
-   预训练语料与公开测试集可能存在的重叠是否得到披露。

可参考 [GraphPart](https://github.com/graph-part/graph-part)
等同源性感知划分工具。短肽的相似性阈值需要根据长度和任务进行敏感性分析，不能机械套用单一阈值。

## 十三、不同设计任务的数据库组合

  --------------------------------------------------------------------------------------------------------------
  任务                    首选数据源                                  补充资源
  ----------------------- ------------------------------------------- ------------------------------------------
  从头生成抗菌肽          APD、DRAMP、DBAASP、dbAMP                   Hemolytik、ToxinPred、PDB、UniProt

  抗真菌肽                DBAASP、DRAMP、APD、dbAMP                   真菌专用文献、结构和靶点资源

  抗病毒肽                AVPdb、DBAASP、文献                         IEDB（免疫识别相关）、病毒蛋白结构

  抗肿瘤肽                CancerPPD2、SATPdb、文献                    HPA、DepMap、Open Targets、PDB

  靶点结合肽              UniProt、PDB、Open Targets、文献            BindingDB、ChEMBL、GPCRdb

  疾病靶向肽              Open Targets、HPA、DepMap、UniProt          结构、临床开发记录和文献

  细胞穿透/递送肽         CPPsite、SATPdb                             Hemolytik、结构与相关实验文献

  免疫调节肽              IEDB、CEDAR、UniProt、文献                  Reactome、靶点与通路资源

  酶抑制肽                BIOPEP-UWM、AHTPDB、BRENDA、MEROPS          ChEMBL、BindingDB、PDB

  神经肽/受体调节肽       NeuroPep（核验当前状态）、UniProt、GPCRdb   PDB、ChEMBL、BindingDB

  稳定性优化              DBAASP 修饰记录、UniProt、MEROPS            修饰资源、蛋白质组学数据

  修饰肽设计              DBAASP、CPPsite、CancerPPD2、UniProt        PDB、文献和化学结构工具
                          PTM、GlyGen                                 

  新颖性检测              多肽专用数据库                              BLAST/MMseqs2/Foldseek、文献、专利

  实验方案制定            对应功能数据库和原始论文                    ClinicalTrials.gov、药品标签和方法学论文
  --------------------------------------------------------------------------------------------------------------

## 十四、主要参考文献与官方资料

### 多肽功能数据库

1.  DRAMP 4.0：https://doi.org/10.1093/nar/gkae1046
2.  DBAASP：https://doi.org/10.1093/nar/gkaa991
3.  APD3：https://pmc.ncbi.nlm.nih.gov/articles/PMC4702905/
4.  SATPdb：https://doi.org/10.1093/nar/gkv1114
5.  CancerPPD2：https://doi.org/10.1093/database/baaf030
6.  AVPdb：https://doi.org/10.1093/nar/gkt1191
7.  AHTPDB：https://doi.org/10.1093/nar/gku1141
8.  THPdb：https://doi.org/10.1371/journal.pone.0181748
9.  ToxinPred 3.0：https://doi.org/10.1016/j.compbiomed.2024.108926

### 蛋白、结构和靶点

10. UniProtKB：https://www.uniprot.org/
11. NCBI RefSeq：https://www.ncbi.nlm.nih.gov/refseq/
12. RCSB PDB
    API：https://www.rcsb.org/docs/programmatic-access/web-apis-overview
13. AlphaFold DB：https://alphafold.ebi.ac.uk/
14. AlphaFold 3：https://doi.org/10.1038/s41586-024-07487-w
15. Open
    Targets：https://platform-docs.opentargets.org/data-access/graphql-api
16. Human Protein Atlas：https://www.proteinatlas.org/about/download
17. Gene Ontology：https://www.geneontology.org/docs/go-annotations/
18. MEROPS：https://www.ebi.ac.uk/merops/
19. BRENDA：https://www.brenda-enzymes.org/

### 活性、修饰与数据标准

20. BindingDB：https://www.bindingdb.org/rwd/bind/info.jsp
21. ChEMBL：https://www.ebi.ac.uk/chembl/
22. PubChem BioAssay：https://pubchem.ncbi.nlm.nih.gov/docs/bioassays
23. PhosphoSitePlus：https://www.phosphosite.org/psp/
24. GlyGen：https://www.glygen.org/
25. PeptideAtlas：https://www.peptideatlas.org/
26. ProteomeXchange：https://doi.org/10.1093/nar/gkac1040
27. FAIR 数据原则：https://doi.org/10.1038/sdata.2016.18
28. GraphPart：https://doi.org/10.1093/nargab/lqad088
29. Europe PMC REST API：https://europepmc.org/RestfulWebService
30. ClinicalTrials.gov
    API：https://clinicaltrials.gov/data-api/about-api

## 最终建议

对通用多肽从头设计 Agent，数据库建设应围绕五条主线组织：

1.  **多肽功能与实验数据**；
2.  **蛋白和靶点背景**；
3.  **结构与相互作用**；
4.  **安全性、修饰与可开发性**；
5.  **文献、专利与实验结果溯源**。

第一阶段优先接入 UniProt、PDB/AlphaFold DB、Europe
PMC、DBAASP、DRAMP、APD、dbAMP、CancerPPD2、CPPsite、IEDB、Open
Targets/HPA，以及 ChEMBL/BindingDB 等核心资源。

不要以数据库数量或原始记录总数作为唯一目标。对生成模型真正重要的是：实验终点清楚、阴性定义可靠、修饰结构完整、来源可追溯、数据划分无明显泄漏，并且使用许可明确。

**建议下一步先完成每个核心数据库的字段映射表和下载/API
清单，再开展正式数据汇总。**
