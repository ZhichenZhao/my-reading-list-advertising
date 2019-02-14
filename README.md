# my-reading-list-advertising


## Real-time Bidding (RTB)

[张伟楠博士PPT](https://github.com/wzhe06/Ad-papers/blob/master/Bidding%20Strategy/Research%20Frontier%20of%20Real-Time%20Bidding%20based%20Display%20Advertising.pdf),2015
* bidding model指的是输入是一些信息，包括user，哪个ad，page信息等等，输出是这次出价，这个模型要优化广告主的关键指标（KPI）

### Bid Landscape Forecasting in Online Ad Exchange Marketplace，KDD，2011
* bid landscape forecasting，竞价愿景预测，指的是预测横坐标为bid，纵坐标为win次数的直方图，假如有了这张图，可以很容易的算出某个bid获胜的概率以及想要获胜的期望bid是多少。
* 想要直接更具历史预测这个分布是很难的，因为过去的事情对于未来没有指导意义，当campaign的分布变化的时候，就很难预测了。
* 获胜的价格的分布取对数之后很像一个正态分布,那也就是说，估计bid的landscape其实就是估计均值和方差就完事了。
* 文章中并不直接对广告计划进行预测，而是预测每一个定向属性值的组合向量的bid landscape。每一个唯一的定向属性值的组合向量称作一个样例(sample)。例如，一个广告计划有三个定向维度，媒体(P1,P2)，用户性别(male, female)，用户年龄(18-23,23-30)，那么<P1,male,18-23>就构成了一个样例。
* 文章中提出了一种"Bid Star Tree"的方法。具体做法是，对每一个特征加入一个新的值"*"，这个值用语匹配所有数据，如果一个维度的某个值下的数据比较少，直接聚集到"*"这个值上。这样就可以解决数据稀疏性的问题。

## CTR/CVR Estimation
### Estimating Conversion Rate in Display Advertising from Past Performance Data， KDD，2012
* 用用户数据来估计某个商品的转化率有最简单的最大似然估计方法，首先找到该用户的聚类，也就是“这一类用户”，然后直接统计该商品在这一类用户上历史上的转化率，得到转化率的估计。
* 要用上面的办法来估计CVR，第一个要面对的问题就是如何解决稀疏性，因为转化率本身是非常低的。在本文中作者对ad，user，publisher均作了分层，然后叶子节点会向根节点累积，这样就总有一层的转化率数字合理了。接下来，作者将所有层的结果使用逻辑回归合并输出。

### Predicting Response in Mobile Advertising with Hierarchical Importance-Aware Factorization Machine，WSDM（International Conference on Web Search and Data Mining），2014
* WSDM这个会议，在IR（Information Retrieval）领域，这个会议的质量不错，据说仅次于WWW与SIGIR，里面有很多工业界的文章。
* 也是利用了分层的结构，但是对于每个层级的预估CTR，合并的时候用到了FM，显式的引入了特征之间的交互，比逻辑回归效果要好。



