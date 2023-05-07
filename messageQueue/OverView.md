- [Message Queue](#message-queue)
  - [解耦](#解耦)
  - [异步](#异步)
  - [削峰](#削峰)

# Message Queue
## 解耦
## 异步
## 削峰


Kafka、ActiveMQ、RabbitMQ、RocketMQ 有什么优缺点？


| 特性                     | ActiveMQ                              | RabbitMQ                                           | RocketMQ                                                                                                              | Kafka                                                                                                                                           |
| ------------------------ | ------------------------------------- | -------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 单机吞吐量               | 万级，比 RocketMQ、Kafka 低一个数量级 | 同 ActiveMQ                                        | 10 万级，支撑高吞吐                                                                                                   | 10 万级，高吞吐，一般配合大数据类的系统来进行实时数据计算、日志采集等场景                                                                       |
| topic 数量对吞吐量的影响 |                                       |                                                    | topic 可以达到几百/几千的级别，吞吐量会有较小幅度的下降，这是 RocketMQ 的一大优势，在同等机器下，可以支撑大量的 topic | topic 从几十到几百个时候，吞吐量会大幅度下降，在同等机器下，Kafka 尽量保证 topic 数量不要过多，如果要支撑大规模的 topic，需要增加更多的机器资源 |
| 时效性                   | ms 级                                 | 微秒级，这是 RabbitMQ 的一大特点，延迟最低         | ms 级                                                                                                                 | 延迟在 ms 级以内                                                                                                                                |
| 可用性                   | 高，基于主从架构实现高可用            | 同 ActiveMQ                                        | 非常高，分布式架构                                                                                                    | 非常高，分布式，一个数据多个副本，少数机器宕机，不会丢失数据，不会导致不可用                                                                    |
| 消息可靠性               | 有较低的概率丢失数据                  | 基本不丢                                           | 经过参数优化配置，可以做到 0 丢失                                                                                     | 同 RocketMQ                                                                                                                                     |
| 功能支持                 | MQ 领域的功能极其完备                 | 基于 erlang 开发，并发能力很强，性能极好，延时很低 | MQ 功能较为完善，还是分布式的，扩展性好                                                                               | 功能较为简单，主要支持简单的 MQ 功能，在大数据领域的实时计算以及日志采集被大规模使用                                           