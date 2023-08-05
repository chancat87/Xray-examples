### **配置介绍：** 

| | 无需注册域名 | 解决 TLS in TLS | 自带多路复用 | 通过 CDN 访问 |
| :--- | :---: | :---: | :---: | :---: |
| **VLESS-gRPC** | :x: | :x: | :heavy_check_mark: | :heavy_check_mark: |

### 原理图：

Xray client <--- gRPC **(TLS)** ---> Nginx **(0.0.0.0:443)** <--- gRPC **(cleartext)** ---> Xray server **(127.0.0.1:8007)**
