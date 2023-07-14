VPS A

```jsonc
{
    "log": {
        "loglevel": "warning"
    },
    "routing": {
        "domainStrategy": "IPIfNonMatch",
        "rules": [
            {
                "type": "field",
                "domain": [
                    "geosite:netflix"
                ],
                "outboundTag": "netflix"
            }
        ]
    },
    "inbounds": [
        {
            // 粘贴你的服务端配置
            "sniffing": {
                "enabled": true,
                "destOverride": [
                    "http",
                    "tls",
                    "quic"
                ]
            }
        }
    ],
    "outbounds": [
        {
            "protocol": "freedom",
            "tag": "direct"
        },
        {
            "protocol": "shadowsocks",
            "settings": {
                "servers": [
                    {
                        "address": "", // VPS B 的 IP
                        "port": 80,
                        "method": "2022-blake3-aes-128-gcm",
                        "password": "" // 执行 openssl rand -base64 16 生成
                    }
                ]
            },
            "tag": "netflix"
        }
    ]
}
```
