---
layout: post
title: Faraday中设置Net::HTTPSession的SSL连接参数
category: 技术
tags: [ruby ssl]
---

{% include JB/setup %}

本文描述了在使用``Net::HTTP``作为``Faraday``的adapter，并且使用HTTPS链接服务器
时如何配置SSL参数。

在创建``Faraday``对象时，可以通过在``options``中包含``ssl``参数设置``Net::HTTPSession``的SSL连接参数。例如:

```ruby
Faraday.new config.service_url, ssl: { verify: false }
# 忽略对服务器参数的检验。
```
具体可以配置的``SSL``参数是：

+ ``verify``: 为``true``时设``verify_mode``为``OpenSSL::SSL::VERIFY_PEER``；为``false``时设``verify_mode``为``OpenSSL::SSL::VERIFY_NONE``
+ ``verify_mode``: ``OpenSSL::SSL::VERIFY_PEER``或者``OpenSSL::SSL::VERIFY_NONE``
+ ``client_cert``: 客户端证书路径
+ ``client_key``: 客户端证书key
+ ``ca_file``: CA文件文件名
+ ``ca_path``: CA文件路径
+ ``verify_depth``: 见Net::HTTPSession#verify_depth
+ ``ssl_version``
