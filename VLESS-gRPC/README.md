### **配置介绍：** 

| | 无需注册域名 | 解决 TLS in TLS | 自带多路复用 | 通过 CDN 访问 |
| :--- | :---: | :---: | :---: | :---: |
| **VLESS-gRPC** | :x: | :x: | :heavy_check_mark: | :heavy_check_mark: |

### 注意：

:exclamation:gRPC/H2 建议在有优化回程路由（如 CN2-GIA、AS9929/AS10099、CMI/CMIN2、AS4837 等）的VPS上使用。并且VPS所在的地区距离你的位置越近越好。即使你的VPS满足以上条件，仍然不能避免断流现象。建议参考ChatGPT的回答优化系统内核参数。除此以外，你可以参考[文档](https://xtls.github.io/Xray-docs-next/config/transports/grpc.html#grpcobject)，使用[健康检查](https://github.com/chika0801/Xray-examples/blob/main/VLESS-gRPC/config_client.json#L62)参数。

<details><summary>点击查看</summary><br>

```
cat > /etc/sysctl.d/http2.conf << EOF
net.core.somaxconn = 65535
net.ipv4.tcp_max_syn_backlog = 65535
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_tw_reuse = 1
net.ipv4.tcp_fin_timeout = 30
net.ipv4.tcp_keepalive_time = 1200
net.ipv4.tcp_keepalive_probes = 5
net.ipv4.tcp_keepalive_intvl = 15
net.ipv4.tcp_slow_start_after_idle = 0
net.ipv4.tcp_mtu_probing = 1
net.ipv4.tcp_max_tw_buckets = 50000
EOF
```

```
sysctl -p /etc/sysctl.d/http2.conf
```

</details>

### v2rayN - V6.19 及以上版本 配置示例

<details><summary>点击查看</summary><br>

| 名称 | 值 |
| :--- | :--- |
| 地址 | chika.example.com |
| 端口 | 443 |
| 用户ID | chika |
| 流控 | xtls-rprx-vision |
| 传输层安全 | tls |
| Fingerprint | chrome |

![1](https://user-images.githubusercontent.com/88967758/224359333-39fe1582-e98f-4f10-951e-3d54499bbe6d.png)

</details>

### v2rayNG - V1.8.1 及以上版本 配置示例

<details><summary>点击查看</summary><br>

| 名称 | 值 |
| :--- | :--- |
| 地址(address) | chika.example.com |
| 端口(prot) | 443 |
| 用户ID(id) | chika |
| 流控(flow) | xtls-rprx-vision |
| 加密方式(encryption) | none |
| 传输协议(network) | tcp |
| 伪装类型(type) | none |
| 伪装域名(host) | 留空 |
| path | 留空 |
| 传输层安全(tls) | tls |
| SNI | 留空 |
| Fingerprint | chrome |
| Alpn | 留空 |
| 跳过证书验证(allowInsecure) | false |

</details>

### Shadowrocket - V2.2.31 及以上版本 配置示例

<details><summary>点击查看</summary><br>

| 名称 | 值 |
| :--- | :--- |
| 类型 | VLESS |
| 地址 | chika.example.com |
| 端口 | 443 |
| UUID | chika |
| TLS | 选上 |
| XTLS | xtls-rprx-vision |
| 允许不安全 | 不选 |
| SNI | 留空 |
| ALPN | 留空 |
| 公钥 | 留空 |
| 短 ID | 留空 |
| 传输方式 | none |
| 多路复用 | 不选 |
| TCP 快速打开 | 不选 |
| UDP 转发 | 选上 |
| 代理通过 | 留空 |

</details>

### PassWall - V4.61 及以上版本 配置示例

<details><summary>点击查看</summary><br>

| 名称 | 值 |
| :--- | :--- |
| 类型 | Xray |
| 传输协议 | VLESS |
| 地址（支持域名） | chika.example.com |
| 端口 | 443 |
| 加密方式 | none |
| ID | chika |
| TLS | 勾上 |
| flow | xtls-rprx-vision |
| REALITY | 不勾 |
| alpn | 默认 |
| 域名 | 留空 |
| 允许不安全连接 | 不勾 |
| 指纹伪造 | chrome |
| 传输协议 | TCP |
| 伪装类型 | none |

</details>

### ShadowSocksR Plus+ 配置示例

<details><summary>点击查看</summary><br>

| 名称 | 值 |
| :--- | :--- |
| 服务器节点类型 | V2Ray/Xray |
| V2Ray/XRay 协议 | VLESS |
| 服务器地址 | chika.example.com |
| 端口 | 443 |
| Vmess/VLESS ID (UUID) | chika |
| VLESS 加密 | none |
| 传输协议 | TCP |
| 伪装类型 | 无 |
| TLS | 勾上 |
| 流控（Flow） | xtls-rprx-vision |
| 指纹伪造 | chrome |
| TLS 主机名 | 留空 |
| TLS ALPN | 留空 |
| 允许不安全连接 | 不勾 |
| Mux | 不勾 |
| 自签证书 | 不勾 |
| 启用自动切换 | 不勾 |
| 本地端口 | 1234 |

</details>
