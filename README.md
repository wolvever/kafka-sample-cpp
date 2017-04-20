# 百度Kafka服务C++样例

百度Kafka是托管的Kafka消息服务。完全兼容开源Kafka。本样例展示如何使用[librdkafka](https://github.com/edenhill/librdkafka)客户端访问百度Kafka服务。

## 环境要求

- 参考[librdkafka](https://github.com/edenhill/librdkafka#requirements)

## 准备工作

准备工作的细节请参考[BCE官网帮助文档](https://cloud.baidu.com/doc/Kafka/QuickGuide.html)

1. 在管理控制台中创建好主题，并获取主题名称topic_name。
2. 在管理控制台中下载您的kafka-key.zip，包含程序使用的`client.pem`，`client.key`，`ca.pem`。

## 运行样例代码

### 编译librdkafka

基于centos7环境可参考如下编译脚本

    sh setup-librdkafka.sh

## 运行样例代码

将之前准备好的文件`client.pem`、`client.key`以及`ca.pem`放在librdkafka-0.9.4/examples目录下，并在该目录下执行样例程序。

执行producer

    ./rdkafka_example -b kafka.bj.baidubce.com:9091 -X security.protocol=ssl -X ssl.key.location=client.key -X ssl.certificate.location=client.pem -X ssl.ca.location=ca.pem -P -t topic_name -p 0

执行consumer

    ./rdkafka_example -b kafka.bj.baidubce.com:9091 -X security.protocol=ssl -X ssl.key.location=client.key -X ssl.certificate.location=client.pem -X ssl.ca.location=ca.pem -C -t topic_name -p 0

## 参考链接

- [百度Kafka产品介绍](https://cloud.baidu.com/product/kafka.html)
- [Kafka](http://kafka.apache.org/)
- [librdkafka](https://github.com/edenhill/librdkafka)