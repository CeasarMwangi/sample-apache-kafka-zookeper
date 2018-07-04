Kafka 
-is designed for distributed high throughput systems. 
-has better throughput, 
-built-in partitioning, 
-replication and 
-inherent fault-tolerance,
- reliable

Publish-Subscribe Messaging System
In the publish-subscribe system, messages are persisted in a topic. 
Consumers can subscribe to one or more topic and consume all the messages in the topics. 
Message producers are called publishers and message consumers are called subscribers.

What is Kafka?
Apache Kafka is a distributed publish-subscribe messaging system and a robust queue that can handle a high volume of data and enables you to pass messages from one end-point to another. 
Kafka messages are persisted on the disk and replicated within the cluster to prevent data loss. 
Kafka is built on top of the ZooKeeper synchronization service. 
It integrates very well with Apache Storm and Spark for real-time streaming data analysis.
-Kafka is very fast, performs 2 million writes/sec. 
-fault tolerance
Benefits
Following are a few benefits of Kafka −
Reliability − Kafka is distributed, partitioned, replicated and fault tolerance.
Scalability − Kafka messaging system scales easily without down time..
Durability − Kafka uses Distributed commit log which means messages persists on disk as fast as possible, hence it is durable..
Performance − Kafka has high throughput for both publishing and subscribing messages. It maintains stable performance even many TB of messages are stored.
Kafka is very fast and guarantees zero downtime and zero data loss.

HOW IT WORKS
Kafka provides a powerful set of primitives for connecting your distributed application: messages, topics, partitions, producers, consumers, and log compaction.

























Kafka cluster, so you 



  <section id="diagram" class="section-purple-dark">
    <div class="wrapper">
      <h5 class="text-center caps text-white">How it works</h5>
      <p class="text-center intro">Kafka provides a powerful set of primitives for connecting your distributed application: messages, topics, partitions, producers, consumers, and log compaction.</p>

      <div id="diagram-mobile">
        <hr>
        <h4>Messages</h4>
        <p>Kafka is a message passing system, messages are events and can have keys.</p>

        <h4>Brokers</h4>
        <p>A Kafka cluster is made up of brokers that run Kafka processes.</p>

        <h4>Topics</h4>
        <p>Topics are streams of messages of a particular category.</p>

        <h4>Partitions</h4>
        <p>Partitions are append only, ordered logs of a topic’s messages. Messages have offsets denoting position in the partition. Kafka replicates partitions across the cluster for fault tolerance and message durability.</p>

        <h4>Producers</h4>
        <p>Producers are client processes that send messages to a broker on a topic and partition. Producers can use a partitioning function on keys to control message distribution.</p>

        <h4>Consumers</h4>
        <p>Consumers read messages from topics' partitions on brokers, tracking the last offset read to coordinate and recover from failures. Consumers can be deployed in groups for scalability.</p>

        <h4>Log compaction</h4>
        <p>Log compaction keeps the most recent value for every key so clients can restore state.</p>

      </div>
    </div>


Workflow of Pub-Sub Messaging
Following is the step wise workflow of the Pub-Sub Messaging −
Producers send message to a topic at regular intervals.
Kafka broker stores all messages in the partitions configured for that particular topic. It ensures the messages are equally shared between partitions. If the producer sends two messages and there are two partitions, Kafka will store one message in the first partition and the second message in the second partition.
Consumer subscribes to a specific topic.
Once the consumer subscribes to a topic, Kafka will provide the current offset of the topic to the consumer and also saves the offset in the Zookeeper ensemble.
Consumer will request the Kafka in a regular interval (like 100 Ms) for new messages.
Once Kafka receives the messages from producers, it forwards these messages to the consumers.
Consumer will receive the message and process it.
Once the messages are processed, consumer will send an acknowledgement to the Kafka broker.
Once Kafka receives an acknowledgement, it changes the offset to the new value and updates it in the Zookeeper. Since offsets are maintained in the Zookeeper, the consumer can read next message correctly even during server outrages.
This above flow will repeat until the consumer stops the request.
Consumer has the option to rewind/skip to the desired offset of a topic at any time and read all the subsequent messages.

































ZooKeeper is the coordination service to manage the brokers, leader election for partitions, and alerts when Kafka changes topics (i.e. deletes topic, creates topic, etc.) or brokers (add broker, dead broker, etc.). In this example, I have started only one ZooKeeper instance. In production environments, we should have more ZooKeeper instances to manage fail-over. Without ZooKeeper, the Kafka cluster cannot work.


