# Generate Cluster ID

```
docker run -it --rm confluentinc/cp-kafka kafka-storage random-uuid
```

# Pub/Sub Command
```
kcat -b kafka-0.kafka-svc.kafka.svc.cluster.local:9092,kafka-1.kafka-svc.kafka.svc.cluster.local:9092,kafka-2.kafka-svc.kafka.svc.cluster.local:9092 -t test-topic -C
```
```
kafka-topics.sh --bootstrap-server kafka-0.kafka-svc.kafka.svc.cluster.local:9092,kafka-1.kafka-svc.kafka.svc.cluster.local:9092,kafka-2.kafka-svc.kafka.svc.cluster.local:9092 \
--create \
--topic test-topic \
--replication-factor 1 \
--partitions 3
```
```
kafka-console-producer.sh --bootstrap-server kafka-0.kafka-svc.kafka.svc.cluster.local:9092,kafka-1.kafka-svc.kafka.svc.cluster.local:9092,kafka-2.kafka-svc.kafka.svc.cluster.local:9092 \
--topic test-topic
```
```
kafka-console-consumer.sh --bootstrap-server kafka-0.kafka-svc.kafka.svc.cluster.local:9092,kafka-1.kafka-svc.kafka.svc.cluster.local:9092,kafka-2.kafka-svc.kafka.svc.cluster.local:9092 \
--topic test-topic \
--group consumer-group-test-topic \
--from-beginning
```
```
kafka-console-consumer.sh --bootstrap-server localhost:9092 \
--group consumer-group-test-topic \
--topic test-topic
```
```
kafka-topics.sh --bootstrap-server kafka-0.kafka-svc.kafka.svc.cluster.local:9092,kafka-1.kafka-svc.kafka.svc.cluster.local:9092,kafka-2.kafka-svc.kafka.svc.cluster.local:9092 \
--alter --topic test-topic --partitions 2
```