# eCLIP
## Study notes on eCLIP pipeline by QuSusu
---
应该会持续性地对eCLIP的内容补充，今天主要写一篇文献的summary。其实我对RNA相关的东西了解超级少，硬着头皮看了这个文献，理解的还不够深入，先写下自己目前的理解。

## 先给自己科普下简单的知识、名词：
- 转录调控：蛋白质对DNA
- 转录后调控：蛋白质对RNA
- 转录水平的实验相对容易做，转录后的研究对实验技术要求高。

- RNA-binding protein，RBP：有一类RNA结合蛋白（简称RBP），它们会结合RNA，调控RNA加工。
	- 在哪里可以找到RBP对应的数据：
		- [RBP database](http://rbpdb.ccbr.utoronto.ca/)：但我看了一下最近一次的更新数据也是2012年了，估计没有人维护了。
		- [ENCODE](https://www.encodeproject.org/eclip/)：推荐这个。
- CLIP：crosslinking and immunoprecipitation，一种实验方法，用于鉴定RBP的结合位点。
- eCLIP：enhanced CLIP ，一种相对于CLIP“升级的”实验方法，据说在鉴定RBP结合位点时有更好的效果。

---
## Robust transcriptome-wide discovery of RNA-binding protein binding sites with enhanced CLIP (eCLIP)

	The eCLIP method and processing pipeline were developed by the laboratory of Gene Yeo at the University of California, San Diego.据说这个Gene Yeo是个学术方面超厉害的人~

### Why eCLIP occurs?
目前通过PAR-CLIP，iCLIP等方法寻找RBP的结合位点存在技术上的挑战——实验失败率较高、建库测序的多样性低等问题，因此有了现在的enhanced CLIP的产生。
### 文章主要有几个目的：
1.证明eCLIP这种方法相对于其他而言确实识别RBP结合位点的效果更好；
2.给了对应的详细数据分析流程；但目前据主管说，虽然有release版本但也是正在开发中的pipeline，bug较多，正在测试中；

### 解读实验流程特别之处
和传统的CLIP相比，或者说更直接地和传统的RNAseq相比，因为我们都没有直接接触过实验，所以对文章里的整个主要流程图就非常蒙，看不懂在干嘛，所以大部分精力放在研究整个图到底怎么回事，因为只有了解了实验原理才知道如何分析。

![2_experiment_flow](images/2_experiment_flow.png)

图解：
- UV的方式使得RBP和RNA进行紧密结合；
- 裂解RNA片段；
- 对于裂解后的样本，分成2份：
	- 2% of sample——for size-matched imput (SMInput)
	- 98% of sample——IP  & washing

**这里也是我们最困惑的地方，为什么要把sample分成两份呢？**

- 98% of sample：加可以和RBP作用的抗体，然后去磷酸化等操作，硝酸纤维素膜过滤，再跑蛋白凝胶，这样在蛋白胶上就可以看到大概有75KDa大小的条带，证明拿到的这部分确实是有RBP结合的，然后再用蛋白酶把蛋白消化掉分离得到RNA，对得到的RNA反转录（RT-PCR），得到cDNA，再PCR扩增测序；

***我困了，明天继续，未完待续***

