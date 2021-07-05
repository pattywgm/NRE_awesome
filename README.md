# NRE_awesome
关系抽取相关整理

### 比赛
* [CCKS2019 人物关系抽取](https://www.biendata.xyz/competition/ccks_2019_ipre/)
* [CCKS2020](http://sigkg.cn/ccks2020/?page_id=516)
   * [面向中文电子病历的医疗实体及事件抽取](http://sigkg.cn/ccks2020/wp-content/uploads/2020/03/3-CCKS2020%E6%8A%80%E6%9C%AF%E8%AF%84%E6%B5%8B-%E9%9D%A2%E5%90%91%E4%B8%AD%E6%96%87%E7%94%B5%E5%AD%90%E7%97%85%E5%8E%86%E7%9A%84%E5%8C%BB%E7%96%97%E5%AE%9E%E4%BD%93%E5%8F%8A%E4%BA%8B%E4%BB%B6%E6%8A%BD%E5%8F%96.docx)

   * [面向金融领域的小样本跨类迁移事件抽取](http://sigkg.cn/ccks2020/wp-content/uploads/2020/03/4-CCKS2020%E6%8A%80%E6%9C%AF%E8%AF%84%E6%B5%8B-%E9%9D%A2%E5%90%91%E9%87%91%E8%9E%8D%E9%A2%86%E5%9F%9F%E7%9A%84%E5%B0%8F%E6%A0%B7%E6%9C%AC%E8%B7%A8%E7%B1%BB%E8%BF%81%E7%A7%BB%E4%BA%8B%E4%BB%B6%E6%8A%BD%E5%8F%96.docx)

   * [面向金融领域的篇章级事件主体与要素抽取](http://sigkg.cn/ccks2020/wp-content/uploads/2020/03/5-CCKS2020%E6%8A%80%E6%9C%AF%E8%AF%84%E6%B5%8B-%E9%9D%A2%E5%90%91%E9%87%91%E8%9E%8D%E9%A2%86%E5%9F%9F%E7%9A%84%E7%AF%87%E7%AB%A0%E7%BA%A7%E4%BA%8B%E4%BB%B6%E4%B8%BB%E4%BD%93%E4%B8%8E%E8%A6%81%E7%B4%A0%E6%8A%BD%E5%8F%96.docx)

* [CCKS2021](http://sigkg.cn/ccks2021/?page_id=27)
   * 面向中文电子病历的医疗实体及事件抽取
   * 通用细粒度事件检测
   * 面向金融领域的篇章级事件抽取和事件因果关系抽取

* 基于DocRED数据集的竞赛 <https://competitions.codalab.org/competitions/20717#results>

### 数据集
* https://opennre-docs.readthedocs.io/en/latest/get_started/benchmark.html

| Dataset        | #class   |  #instance  | note |
| --------   | -----:  | :----:  | :-----: |
| SemEval-2010 Task 8      | 9   |  6647     | sentence-level |
| TACRED        |   42   |   21784(exclude no_relation)   | sentence-level |
| Wiki80        |    80    |  56000  | sentence-level |
| NYT10	 | 53	|  694491 | bag-level |
| NYT10m	| 25 |	474059 | bag-level |
| Wiki20m |	81	| 901314 | bag-level |
| DocRED | | | Document-level |
| FewRel | 100 | 70000 | Few-Short RE |

* wiki80
	```shell
	mkdir wiki80
	wget -P wiki80 https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/wiki80/wiki80_rel2id.json
	wget -P wiki80 https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/wiki80/wiki80_train.txt
	wget -P wiki80 https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/wiki80/wiki80_val.txt
	```

* wiki20m
	```
	mkdir wiki20m
	wget -P wiki20m https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/wiki20m/wiki20m_rel2id.json
	wget -P wiki20m https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/wiki20m/wiki20m_train.txt
	wget -P wiki20m https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/wiki20m/wiki20m_val.txt
	wget -P wiki20m https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/wiki20m/wiki20m_test.txt
	```

* FewRel
 * 少次学习关系抽取：少次学习（Few-Shot）是一种探索如何让模型快速适应新任务的设定，通过学习少量的训练样本，即可获得对新类型事物的分类能力。THUNLP发布的数据集[FewRel](https://github.com/thunlp/FewRel) 正是进行了这方面的探索。
	```shell
	mkdir fewrel
	wget -P fewrel https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/fewrel/fewrel_train.txt
	wget -P fewrel https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/fewrel/fewrel_train_rel2id.json
	wget -P fewrel https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/fewrel/fewrel_val.txt
	wget -P fewrel https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/fewrel/fewrel_val_rel2id.json
	```

* DocRED
	* 篇章级别的关系抽取：相比于针对句子的关系抽取，篇章级别的关系抽取难度更大，但包含的信息也更丰富。要想在这方面做的更好，就需要模型具有一定的推理、指代消解的能力。这一领域的代表数据集是同样来自THUNLP的[DocRED](https://github.com/thunlp/DocRED)。
	* DocRED以 Wikipedia 作为语料库、以 Wikidata 作为知识图谱构建的，包含对超过5000篇Wikipedia文章的标注，包括96种关系类型、143,375个实体和56,354个关系事实
	* 除了人工精标注的数据集，DocRED还提供了超过10万篇的基于远程监督数据，以支持弱监督的关系抽取研究
	* [文档级实体关系抽取——知识获取的新挑战]<https://zhuanlan.zhihu.com/p/93318977>


* SemEval-2010 Task 8
 * 对于给定了的句子和两个做了标注的名词，从给定的关系清单中选出最合适的关系
	```
	mkdir semeval
	wget -P semeval https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/semeval/semeval_rel2id.json
	wget -P semeval https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/semeval/semeval_train.txt
	wget -P semeval https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/semeval/semeval_val.txt
	wget -P semeval https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/semeval/semeval_test.txt
	```

* nyt10
	 * NYT-10数据发布于Riedel et al, 2010这篇论文中，其文本来源于纽约时报New York Times所标注的语料，命名实体是通过 Stanford NER 工具并结合 Freebase 知识库进行标注的。命名实体对之间的关系是链接和参考外部的Freebase知识库中的关系，结合远监督方法所得到的。
	```
	mkdir nyt10
	wget -P nyt10 https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/nyt10/nyt10_rel2id.json
	wget -P nyt10 https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/nyt10/nyt10_train.txt
	wget -P nyt10 https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/nyt10/nyt10_test.txt
	```

* nyt10m
	```
	mkdir nyt10m
	wget -P nyt10m https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/nyt10m/nyt10m_rel2id.json
	wget -P nyt10m https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/nyt10m/nyt10m_train.txt
	wget -P nyt10m https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/nyt10m/nyt10m_val.txt
	wget -P nyt10m https://thunlp.oss-cn-qingdao.aliyuncs.com/opennre/benchmark/nyt10m/nyt10m_test.txt
	```

    * 注：NYT-10中同一个句子可能存在多个关系，如“Arthur Lee, the leader of Love, died on Thursday in Memphis.” 而SemEval2010一个句子只包含2个实体和1个关系，相对简单一些。

* TACRED (关系数量：41，实例数量：106264)
   * <https://nlp.stanford.edu/projects/tacred/>

* WebNLG
   * <https://webnlg-challenge.loria.fr/download/>

* AEC2015
  * <https://catalog.ldc.upenn.edu/LDC2006T06>

* SCIERC
  * <http://nlp.cs.washington.edu/sciIE/>

* QA-SRL
  * <https://dada.cs.washington.edu/qasrl/#dataset>

###开源工具
* [OpenNRE: 可一键运行的开源关系抽取工具包](http://nlp.csai.tsinghua.edu.cn/project/opennre/)

### 博客repo
* [最新进展排名]<https://paperswithcode.com/task/relation-extraction/latest>
* [清华自然语言处理实验室官方]<https://github.com/thunlp>
* <https://github.com/loujie0822/DeepIE>
