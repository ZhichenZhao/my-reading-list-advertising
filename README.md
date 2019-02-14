# my-reading-list-advertising


## Real-time Bidding (RTB)

[张伟楠博士PPT](https://github.com/wzhe06/Ad-papers/blob/master/Bidding%20Strategy/Research%20Frontier%20of%20Real-Time%20Bidding%20based%20Display%20Advertising.pdf),2015
* bidding model指的是输入是一些信息，包括user，哪个ad，page信息等等，输出是这次出价，这个模型要优化广告主的关键指标（KPI）





## CTR/CVR Estimation
### Estimating Conversion Rate in Display Advertising from Past Performance Data， KDD，2012
* 用用户数据来估计某个商品的转化率有最简单的最大似然估计方法，首先找到该用户的聚类，也就是“这一类用户”，然后直接统计该商品在这一类用户上历史上的转化率，得到转化率的估计。
* 要用上面的办法来估计CVR，第一个要面对的问题就是如何解决稀疏性，因为转化率本身是非常低的。在本文中作者对ad，user，publisher均作了分层，然后叶子节点会向根节点累积，这样就总有一层的转化率数字合理了。接下来，作者将所有层的结果使用逻辑回归合并输出。







