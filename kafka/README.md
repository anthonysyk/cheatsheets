### Schema Registry API routes

https://github.com/confluentinc/schema-registry/blob/master/README.md


### Commands

- Update retention time on runtime
```bash
$ bin/kafka-topics.sh --zookeeper localhost:2181 --alter --topic my-topic --config retention.ms=86400000
```

- Describe topics
```bash
$ bin/kafka-topics --zookeeper localhost:2181 --describe --topics-with-overrides
```

- Start/Stop zookeeper
```bash
zookeeper-server-stop zookeeper-server-start
```

- Delete a topic

```bash
kafka-topics --zookeeper localhost:2181 --delete --topic <topic_name>
```

- Alter a topic configuration

```bash
kafka-configs   --alter   --zookeeper localhost:2181   --entity-type topics   --entity-name window_5min   --add-config retention.bytes=5000000000

kafka-configs   --alter   --zookeeper localhost:2181   --entity-type topics   --entity-name window_5min   --add-config retention.ms=5000
```

# Troubleshooting

- Schema Registry

Q: Failed to write Noop record to kafka store

A: Delete _schema topic and recreate it
```bash
kafka-topics --zookeeper localhost:2181 --delete --topic _schema
kafka-topics --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic _schema
```

Q: ERROR The retention policy of the schema topic _schemas is incorrect

A: Set cleanup.polocy to "compact"
```bash
kafka-configs.sh --zookeeper localhost --entity-type topics --entity-name _schemas --alter --add-config cleanup.policy=compact
```


