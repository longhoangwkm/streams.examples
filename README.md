

### Setup

1. Install kafka: https://www.apache.org/dyn/closer.cgi?path=/kafka/2.8.0/kafka_2.13-2.8.0.tgz
2. https://kafka.apache.org/28/documentation/streams/quickstart

```
bin/zookeeper-server-start.sh config/zookeeper.properties
bin/kafka-server-start.sh config/server.properties

bin/kafka-topics.sh --create \
    --bootstrap-server localhost:9092 \
    --replication-factor 1 \
    --partitions 1 \
    --topic streams-plaintext-input


bin/kafka-topics.sh --create \
    --bootstrap-server localhost:9092 \
    --replication-factor 1 \
    --partitions 1 \
    --topic streams-wordcount-output \
    --config cleanup.policy=compact


mvn clean package

mvn exec:java -Dexec.mainClass=myapps.WordCount

```
