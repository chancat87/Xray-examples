## :exclamation:

**1. 对于非 REALITY 流量，全转发到 dest 才是正确的，SNI 分流的话能探测出来，有此需求请用 Nginx 等软件实现。**

**2. 有没有一种可能，正是因为 SNI 分流会有问题，所以 REALITY 才没有内置 SNI 分流？我们并不推荐 SNI 分流。**
