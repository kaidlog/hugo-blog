---
title: "大型网站架构的演化"
date: 2013-10-14T22:58:00+08:00
tags: ["架构"] 
draft: false
toc: true
---

网站一般分三个部分：应用程序、文件、数据库。

1. 初级阶段的网站架构就是把所有的资源放在一台服务器上就够了。
2. 应用服务和数据服务分离：整个网站使用三台服务器 - 应用服务器、文件服务器、数据库服务器。
3. 使用缓存改善网站性能：一种是本地缓存，更好的是远程分布式缓存。（本地缓存虽然速度更快，但是受应用服务器内存的限制，其缓存数据量有限，而且会出现和应用服务器争用内存的情况）
4. 使用应用服务器集群改善网站的并发处理能力，通过负载均衡调度服务器。
5. 数据库读写分离：通过配置两台数据库主从关系，实现主数据库同步更新从数据库，读数据库的时候通过从数据库获取到数据。
6. 使用反向代理和CDN加速网站响应：CDN部署在网络供应商的机房里，可以从距离最近的网络提供商机房获取数据。反向代理部署在网站的中心机房，访问机房的时候，如果反向代理服务器中缓存着用户请求的资源，就将其直接返回给用户。
7. 使用分布式文件系统和分布式数据库系统。
8. 使用NoSQL和搜索引擎。
9. 业务拆分：将一个网站拆分成许多不同的应用，每个应用独立部署。（通常还是访问同一个数据库）
10. 分布式服务：把每一个应用系统相同的业务提取出来，独立部署。可复用的业务链接数据库，提供公用业务服务，而应用系统只需要管理用户界面，通过分布式服务调用共用业务服务完成具体业务操作。


--The End--