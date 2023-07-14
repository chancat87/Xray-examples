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

VPS B

```jsonc
{
    "log": {
        "loglevel": "warning"
    },
    "inbounds": [
        {
            "listen": "0.0.0.0",
            "port": 80,
            "protocol": "shadowsocks",
            "settings": {
                "method": "2022-blake3-aes-128-gcm",
                "password": "", // 与 VPS A 中的一致
                "network": "tcp,udp"
            }
        }
    ],
    "outbounds": [
        {
            "protocol": "freedom"
        }
    ]
}
```
