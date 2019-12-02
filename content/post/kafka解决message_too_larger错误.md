---
title: kafka解决message too larger 错误
date: 2019-11-29 19:07:23
draft: false
tags: ["kafka"]
---
```bash
#broker能接收消息的最大字节数
message.max.bytes=200000000
#broker可复制的消息的最大字节数
replica.fetch.max.bytes=204857600
#消费者端的可读取的最大消息
fetch.message.max.bytes=204857600
```