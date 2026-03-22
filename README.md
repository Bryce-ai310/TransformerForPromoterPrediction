# TransformerForPromoterPrediction
Transformer model to predict promoter in 2000 sequences

1. 添加一层CNN层取代k-mer
### 💡 架构革新：为什么用 CNN 取代传统的 k-mer 切词？
**(Architectural Innovation: CNN as a Dynamic k-mer Extractor)**
在传统NLP 模型，常采用滑动窗口进行 k-mer 切词（例如将序列切分为 3-mer 或 6-mer）。
尽管这种方法能捕捉局部上下文，但存在极其致命的工程与生物学缺陷，
简单来说会产生极大的内存消耗并且会让模型学习的很吃力，
导致 Embedding 层极度臃肿且容易过拟合。

而CNN会自动学习单碱基规则，相当于一个动态的特征扫描仪，
在单碱基序列上自动学习并提取局部的序列基序（Motifs，如 TATA box），提取特征喂给后面的transformer模型。


2.用nn.Embedding可学习位置代码代替正弦/余弦(sin/cos)位置编码信息
虽牺牲了一定的长度泛化能力，但将数十行的编码公式精简至一行，极大降低了代码冗余，表现也极佳。
