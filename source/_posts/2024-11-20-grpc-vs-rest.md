---
title: gRPC 和 REST 之间有何区别
date: 2024-11-20 22:15:17
tags:
---

### gRPC vs.REST

除了架构风格外，gRPC 和 REST 还有其他内在的差异。

客户端-服务器耦合
REST 是松散耦合，这意味着客户端和服务器不需要了解对方的实施状况。这种松耦合使得 API 更容易随着时间的推移而发展。这是因为更改服务器定义并不一定需要更改客户端的代码。

gRPC 是紧密耦合，这意味着客户端和服务器必须有权访问同一 proto 文件。对文件的任何更新都需要在服务器和客户端上进行更新。

代码生成
gRPC 提供一系列内置的客户端和服务器端原生代码生成功能。由于协议缓冲区编译器 protoc 的存在，可以生成多个语言的代码。在 proto 文件中定义结构后，gRPC 生成客户端和服务器端代码。代码生成可以减少 API 开发的时间。

另一方面，REST 不提供任何内置的代码生成机制，因此如果开发人员需要此功能，就必须使用其他第三方工具。

双向流式传输
gRPC 提供双向流式传输通信。这意味着客户端和服务器都可以在单个连接上同时发送和接收多个请求和响应。

REST 不提供此功能。

### 何时使用：gRPC vs.REST

REST 是目前最受欢迎的 Web 服务和微服务架构的 API 架构。REST 之所以受欢迎，是因为其实施简单，且具有数据结构映射、可读性和灵活性等特点。无论是用于 Web 服务开发还是内部微服务，新手程序员都可以很轻松地开始为其应用程序开发 RESTful API。

以下是 REST API 的应用场景：

  1. 基于 Web 的架构
  2. 面向公众的 API，便于外部用户理解
  3. 简单数据通信

与 REST 不同，gRPC 专为支持开发人员为分布式数据中心的微服务架构创建高性能 API 而设计。它更适合需要实时流式传输和大量数据加载的内部系统。当 API 不太可能随着时间的推移而发生变化时，gRPC 也非常适合包含多种编程语言的微服务架构。

gRPC API 更适合以下用例：

  1. 高性能系统
  2. 高数据负载
  3. 实时或流式传输应用程序

关于 Web 软件开发的说明
虽然 HTTP 是核心 Web 协议，但不同版本的 HTTP 在 Web 浏览器和 Web 服务器上的采用程度各不相同。

gRPC API 总是使用 HTTP 2，而 REST API 通常使用 HTTP 1.1，这两者并非同一个 HTTP 协议。虽然 HTTP 2 现在是一种常见的 Web 协议，但它不像 HTTP 1.1 那样具有通用的浏览器支持。对于需要支持 Web 应用程序的开发人员来说，这种受限的浏览器支持使得 gRPC 成为不那么有吸引力的选择。

### gRPC接口规范

```proto
syntax = "proto3";

package fromatob;

// FromAtoB is a simplified version of fromAtoB’s backend API.
service FromAtoB {
  rpc Lookup(LookupRequest) returns (Coordinate) {}
}

// A LookupRequest is a request to look up the coordinates for a city by name.
message LookupRequest {
  string name = 1;
}

// A Coordinate identifies a location on Earth by latitude and longitude.
message Coordinate {
  // Latitude is the degrees latitude of the location, in the range [-90, 90].
  double latitude = 1;

  // Longitude is the degrees longitude of the location, in the range [-180, 180].
  double longitude = 2;
}
```

![/images/grpc-vs-rest.png](/images/grpc-vs-rest.png)

### 总结

gRPC 支持流式传输，天生支持HTTP2，有结果时就可以返回无须等待所有结果都获取再一起返回。

双向流式传输

接口规范清晰

HTTP/2 为长期实时通信流提供基础。 gRPC 为通过 HTTP/2 进行流式传输提供一流支持。


基于web架构的简单数据通信更适合REST，追求高性能高数据负载或流式传输的更适合gRPC


### 参考

[gRPC官网](https://grpc.io/)

[https://aws.amazon.com/cn/compare/the-difference-between-grpc-and-rest/](https://aws.amazon.com/cn/compare/the-difference-between-grpc-and-rest/)

[https://www.infoq.cn/article/ye16sg5idqi-vsihs43e](https://www.infoq.cn/article/ye16sg5idqi-vsihs43e)

[https://learn.microsoft.com/zh-cn/aspnet/core/grpc/comparison?view=aspnetcore-8.0](https://learn.microsoft.com/zh-cn/aspnet/core/grpc/comparison?view=aspnetcore-8.0)

[grpcurl](https://github.com/fullstorydev/grpcurl)