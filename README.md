Nikhil J. Nanivadekar
Project Lead Eclipse Collections
eclipse.org/collections
@NikhilNanivade

RabbitMQ vs Kafka: When, Which, Where?
---------------------------------------
Both of these are essentially data transmission frameworks

# Kafka
------------------------
Basic Concepts and Components
- Transaction log: Golden source of truth is essentially in the log
- Zookeeper: responsible for maintaining the configurations, topology
- Broker (Server): messages are stored when pushed by a producer to a topic
- Topic: the classification of messages
- Producer: produces the messages
- Consumer: consumes the messages
 

# RabbitMQ
------------------------
Basic Concepts and Components
- It is a queue. Not just any queue it is a smart queue
- Erlang
- It comes with it's own server: responsible to retain the configuration
- Exchange: smart component: routing rules, routing types, queues
- Queues: queues connect to the exchange and deliver messages
- Producer: produces the messages and pushes them to exchange
- Consumer: consumes the messages from the queue

# Demo
------------------------
1. Simple Kafka Producer, Consumer demo
 - Producer, Consumer, simple configuration in Java
 - discussed and demonstrated the feature/capability of Kafka to replay a set of messages
 - demonstrated the pub/sub model where the same message can be consumed by multiple consumers 
 
2. Simple RabbitMQ Send Receive demo
 - Producer, Consumer, simple configuration in Java
 - discussed about not being able to replay the messages

# Scaling Example
------------------------
1. Kafka scaling
- If you want to scale more for consumers, then you need to add more partitions to the topic
- 1 partition can have only 1 consumer consuming from the topic. 
- 1 consumer can consume from multiple partitions in a topic.
- Kafka guarantees ordering for messages within a partition by the virtue of offsets and logs

2. RabbitMQ scaling
- If you want to scale, just add more consumers and depending on the rules, MQ will start pushing out messages
to the new consumer

# Ordering Notes
------------------------
1. Kafka ordering: Kafka guarantees ordering for messages within a partition
2. RabbitMQ ordering: Ordering is not essentially 100% guaranteed: consumption rate, exception handling

# Exception Handling Example
----------------------------
1. Kafka exception handling:
 - Not supported out of the box
 - Consumers have to be smart about handling incorrect messages
 - Strategy can involve in pushing the message to a different queue

2. RabbitMQ exception handling:
- requeue
- deadletter queues 

# Publisher-Subscriber Example
------------------------------
1. Kafka example
2. RabbitMQ example

# Message Prioritization Example
--------------------------------
1. Kafka message prioritization example:
 - No message priority possible
 - ordering in a partition is guaranteed. If there is priority on the messages
 the ordering within a partition gets violated
 
2. RabbitMQ message prioritization example
 - Priority Queues: 0 to 255
 - higher the number more the priority

# Routing/Topics Example
--------------------------------
1. Kafka message routing/topics example
2. RabbitMQ message routing/topics example

# Summary
---------------
- Both of them are data transmission/transfer technologies
- Kafka is a transaction log.
- Kafka is a pub-sub model where the producer and consumers are smart
- Kafka guarantees ordering within a partition
- Message prioritization is not possible

- MQ is a queue with a smart exchange
- MQ prioritization is available
- MQ allows dynamic scaling once new consumers are added
- MQ messages are deleted once they are consumed from the queue
