## Overview

This document describes most basic cli commands for two popular streaming brokers - Kafka and Redpanda.

## Kafka

### Prerequisites

1. `docker-compose up`
2. `docker ps`
![Docker ps output](./img/kafka-docker-ps.png)
3. `docker-compose exec kafka1 bash` - to start using kafka cli

### Creating a topic

`kafka-topics --create --topic messages --bootstrap-server localhost:8092 -
-replication-factor 1 --partitions 1`

![Output](./img/kafka-create-topic.png)

### Listing all topics

`kafka-topics --list --bootstrap-server kafka1:9092`

![Output](./img/kafka-list-topics.png)

### Sending messages

`kafka-console-producer --topic messages --bootstrap-server kafka1:9092`

![Output](./img/kafka-send-message.png)

### Receiving messages

`kafka-console-consumer --topic messages --bootstrap-server kafka1:9092 --from-beginning --partition 0`

![Output](./img/kafka-receive-message.png)

### Deleting the topic

`kafka-topics --bootstrap-server k
afka1:9092 --delete --topic messages`

![Output](./img/kafka-delete-topic.png)

## Redpanda

### Prerequisites

1. `docker-compose -f docker-compose.redpanda.yml up`
2. `docker ps`
![Output](./img/redpanda-docker-ps.png)
3. `docker exec -it redpanda2 rpk cluster info` - verify cluster connectivity
![Output](./img/redpanda-cluster-status.png)

### Creating a topic

`docker exec -it redpanda2 rpk topic create messages`

![Output](./img/redpanda-create-topic.png)

### Listing all topics

`docker exec -it redpanda2 rpk topic list`

![Output](./img/redpanda-list-topics.png)

### Sending messages

`docker exec -it redpanda2 rpk topic produce messages`

![Output](./img/redpanda-send-message.png)

### Receiving messages

`docker exec -it redpanda2 rpk topic consume messages`

![Output](./img/redpanda-receive-message.png)

### Deleting the topic

`docker exec -it redpanda2 rpk topic delete messages`

![Output](./img/redpanda-delete-topic.png)