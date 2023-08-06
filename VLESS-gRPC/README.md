### **配置介绍：** 

| | 无需注册域名 | 解决 TLS in TLS | 自带多路复用 | 通过 CDN 访问 |
| :--- | :---: | :---: | :---: | :---: |
| **VLESS-gRPC** | :x: | :x: | :heavy_check_mark: | :heavy_check_mark: |

### 注意：

:exclamation:gRPC/H2 建议在有优化回程路由（如 CN2-GIA、AS9929/AS10099、CMI/CMIN2、AS4837 等）的VPS上使用。并且VPS所在的地区距离你的位置越近越好。即使你的VPS满足以上条件，仍然不能避免断流现象。建议参考 [NaïveProxy](https://github.com/klzgrad/naiveproxy) 的 [Performance Tuning](https://github.com/klzgrad/naiveproxy/wiki/Performance-Tuning) 进行优化。除此以外，你可以参考[文档](https://xtls.github.io/Xray-docs-next/config/transports/grpc.html#grpcobject)，使用[健康检查](https://github.com/chika0801/Xray-examples/blob/main/VLESS-gRPC/config_client.json#L62)参数。

<details><summary>点击查看</summary><br>

```
cat > /etc/sysctl.d/http2.conf << EOF
net.ipv4.tcp_congestion_control=bbr
net.ipv4.tcp_slow_start_after_idle=0
net.ipv4.tcp_notsent_lowat=16384
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
| 地址 | 服务端的 IP |
| 端口 | 443 |
| 用户ID | chika |
| 流控 | 留空 |
| 加密方式 | none |
| 传输协议 | grpc |
|  | multi |
| 伪装域名 | 留空 |
| 路径 | chika |
| 传输层安全 | tls |
| SNI | `chika.example.com` |
| Fingerprint | chrome |
| Alpn | 留空 |
| 路过证书验证 | false |

</details>

### v2rayNG - V1.8.1 及以上版本 配置示例

<details><summary>点击查看</summary><br>

| 名称 | 值 |
| :--- | :--- |
| 地址 | 服务端的 IP |
| 端口 | 443 |
| 用户ID | chika |
| 流控 | 留空 |
| 加密方式 | none |
| 传输协议 | grpc |
| gRPC 传输模式 | multi |
| 伪装域名 | 留空 |
| path | chika |
| 传输层安全 | tls |
| SNI | `chika.example.com` |
| Fingerprint | chrome |
| Alpn | 留空 |
| 路过证书验证 | false |

</details>
