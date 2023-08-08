## :exclamation:Nginx SNI 分流

**1. 对于非 REALITY 流量，全转发到 dest 才是正确的，SNI 分流的话能探测出来，有此需求请用 Nginx 等软件实现。** [#](https://github.com/XTLS/Xray-core/issues/2360#issuecomment-1646716162)

**2. 有没有一种可能，正是因为 SNI 分流会有问题，所以 REALITY 才没有内置 SNI 分流？我们并不推荐 SNI 分流。** [#](https://github.com/XTLS/Xray-core/issues/2374#issuecomment-1653603429)

**3. 总之 REALITY 的预期对外表现只是端口转发，另外目前不知道 GFW 会不会封 SNI 分流反代，建议用 Nginx 等软件是借用特征。** [#](https://github.com/XTLS/Xray-core/issues/2360#issuecomment-1646734306)

## :exclamation:Nginx SNI routing

**1. For non-REALITY traffic, it is correct to forward all traffic to dest, which can be detected by SNI shunting, so please use Nginx or other software to implement this.** [#](https://github.com/XTLS/Xray-core/issues/2360#issuecomment-1646716162)

**2. Is it possible that REALITY doesn't have SNI shunting built in precisely because SNI shunting can be a problem? We do not recommend SNI shunting.** [#](https://github.com/XTLS/Xray-core/issues/2374#issuecomment-1653603429)

**3. In short, REALITY's expected external performance is only port forwarding, and we don't know if GFW will block SNI diversion, so we recommend using Nginx and other software to borrow the features.** [#](https://github.com/XTLS/Xray-core/issues/2360#issuecomment-1646734306)
