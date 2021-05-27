# NATS

方便码字，所以不再使用英文，而是简单使用中文。

NATS,直指官网：https://github.com/nats-io/nats.docs/blob/master/nats-concepts/intro.md

## What is NATS

- 2011年产生，NATS是分布式系统中，无论是software和hardware层面，提供对messaging支持的中间件。
- 提供了抽象层，介于application/service和物理网络层之间
- publisher加密发送数据，一个或者多个subscriber接收、解密、处理数据
- Clients通常通过一个url连接NATS系统，然后subscribe/publish消息到subjects，messaging-handling的代码很common,资源和相互依赖相互隔离，可以跨环境，跨语言，跨cloud providers或者on-premise system。
- NATS Core提供最多一次的质量保证。如果一个subscriber没有监听某个subject，或者没有匹配到任何一个subject，或者message发送的时候，subscriber没有被激活，那么该subscriber都不会被保证接收到消息。
- fire-and-forget messaging system，仅仅只会在内存中hold message，绝不会将消息写入到disk中，但是提供[NATS Streaming](https://docs.nats.io/nats-streaming-concepts/intro)或者在客户端中持久化消息。但是通过[Sequence Number](https://docs.nats.io/nats-concepts/seq_num)方式来保证消息一致性。

## Why NATS is needed

- 随着cloud technology兴起(Kubernetes, Cloud Foundry)的兴起，原先的分布式系统架构被扰乱了，很多老的系统的组件被分解，然后被分别部署到cloud上，作为cloud native application
- 庞大系统被肢解的组件到了cloud上之后，不同组件服务之间的交互，越来越多，而且量也越来越庞大,当前的一些技术手段已经无法满足越来越多的需求，比如：
    a. 怎样用一种技术应用多种messaging patterns
    b. 怎样解决Location Transparency的问题，有些时候必须知道当前系统到哪里去连接想要连接的目标系统
    c. Data producer和Data consumers之间的解藕问题
    d. built-in load balancing
- 基于上面的需求，以及下一代的cloud native application的需求，NATS应运而生

## NATS Github

https://github.com/nats-io/nats.go
