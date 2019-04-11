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

### Deep & Cross Network for Ad Click Predictions,KDD,2017
* 本文解决的主要问题是，当dense feature和one-hot feature一起出现的时候应该怎么处理。在one-hot feature这里引入了cross layer。这种layer可以提供one-hot各个特征之间的多项式项（这是fc提供不了的）。然后dense feature经过DNN，最后把两边的特征拼接起来作为输出。

### Predicting Response in Mobile Advertising with Hierarchical Importance-Aware Factorization Machine，WSDM（International Conference on Web Search and Data Mining），2014
* WSDM这个会议，在IR（Information Retrieval）领域，这个会议的质量不错，据说仅次于WWW与SIGIR，里面有很多工业界的文章。
* 也是利用了分层的结构，但是对于每个层级的预估CTR，合并的时候用到了FM，显式的引入了特征之间的交互，比逻辑回归效果要好。

## CPC/CPM/CPA/oCPC/oCPM
### [How does Facebook Bidding Work?](https://bn.co/how-does-facebook-ocpm-bidding-work/)
* oCPM意为按照展示收钱，但是按照转化，或者点击竞价。这样做的好处是可以让广告主提供更多的真实数据。按照CPA，广告主有可能会假装转化很低。但在oCPM中这样就竞价不过别人，造成send很低，对他也是不利的。

### Performance-based Pricing Models in Online Advertising: Cost per Click versus Cost per Action, 2013
* 广告主有几点可以提升转化率的方法，1.加快网速，让用户更快看到落地页；2.落地页制作的好一点；3.制作个性化的落地页
* 对于平台，提高转化率的方法是更精准的定向，投放的对象就是很有可能会转化的人。
* 在CPC体系中，广告主要尽力来优化转化率，而优化转化率并不能给平台带来更多收益。

### Optimized Cost per Click in Taobao Display Advertising, KDD, 2017
* 名词：revenue，（广告）收入，CPC，cost per click，OCPC，optimized cost per click。CPM，cost per mille，KPI，key performance indicators，ROI，return of investment,CTR，click-through rate，CVR，conversion rate，small and mediumsized
advertisers 
* 阿里的文章，OCPC的含义是，按照点击收钱，但是按照user experience，platform revenue以及ROI的综合最优来竞价。
* 首先把ROI作为一个可行域的边界，对于广告主来说，他们不希望实际的ROI小与预期的ROI。然后在此基础上变动出价，最大化广告收益和广告主收益的和

## Pricing
### Internet Advertising and the Generalized Second-Price Auction: Selling Billions of Dollars Worth of Keywords, American Economic Review, 2007
* 该刊物是经济学领域的顶级期刊
* 在广义第二高价之前（GSP），还有广义第一高价，最早在1997年由Overture使用，由于价格可以频繁变动，广义第一高价很不好用。第一个问题是不能让竞争稳定下来，第一次出10和2，第二次就变成2.01和2.00，然后又变成2.01和2.02.不能达到一个均衡。第二个问题是如果广告主价格变动的频率不一致，很可能无法增加收入，比如出10的广告主很快就能调整到2.01这个价位，这样就没有往上走的动力了。
* 广义第二高价可以让整个系统均衡下来，比如三个广告主出价是10，4，2，那么前两个的实际消耗是4和2.这个时候他们两个变动价格都没有办法让自己直接受益，所以就会稳定下来。
* 如果只有一个slot，那么GSP和VCG是等价的。VCG的每一个出价的计算方法是因为有了它，让后面的广告损失了多少，就是他应该出的价格。一般来说，VCG要比GSP在平台上收入高，不过GSP更容易向广告主解释，因此更实用一些。





