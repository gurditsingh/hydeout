# kafka producer
Kafka Producer API allows applications to send streams of data to topics in the Kafka cluster. Basically Its a component of the Kafka ecosystem which is used to publish messages onto a Kafka topic.

# Kafka producer configurations
Having knowledge of producer configurations becomes critical for us in order to get optimal performance and to leverage the capabilities of Kafka. Let's look at each of them in detail below:

### - Configuration Properties : 
When creating a Kafka producer client application, first need an object to represent the required configuration properties needed to start up a producer. There are three required properties, bootstrap.servers and both key and value serializers.

Configuration items are generally key‑value pairs, the easiest way to do it is to use the Properties class from the core java.util's library.

 - **bootstrap.servers :** 
	 - The bootstrap.servers configuration setting needed for the producer to start up and supply a list of brokers (best practice to provide more than one broker).
	 - The producer doesn't connect to every broker referenced in this list, just the first available one.
	 - The broker it connects to for discovering the full membership of the cluster.
	 - The membership  determine the partition owners or leaders so that when it's ready to send messages.
	 
 - **Key and Value serializers :**
	 - key and value serializers are basically to encode the message content.
	 - This is to optimize the size of the messages not only for network transmission, but for storage and even compression.
	 - The producer that serves as the beginning of a message's lifecycle how the message contents are to be encoded so the consumer can know how to decode them.

	**For a full list of settings, always refer to the producerconfigs section of the Kafka documentation site.**

	```scala
	val props=new Properties()
	props.put(ProducerConfig.BOOTSTRAP_SERVERS_CONFIG,"localhost:9092")
	props.put(ProducerConfig.CLIENT_ID_CONFIG,"LearnKafkaProducer")
	props.put(ProducerConfig.KEY_SERIALIZER_CLASS_CONFIG,classOf[StringSerializer].getName)
	props.put(ProducerConfig.VALUE_SERIALIZER_CLASS_CONFIG,classOf[StringSerializer].getName)
	```
	 
------------



### - Instantiating Kafka producer :
When instantiating a Kafka producer with a Properties object, you are effectively setting things up for the Kafka producer to start sending messages.
```scala
val KProducer=new KafkaProducer[String,String](props)
```

 - **ProducerConfig :**
	 -  If you look inside the implementation of the KafkaProducer, you will notice a type called ProducerConfig. 
	 - When the KafkaProducer object is created, the properties are used to instantiate an instance of the ProducerConfig class, and from there, all producer configuration is defined and referenced internally.
 
 - **Producer Records :** 
	 - The ProducerRecord represents what will be published by the Kafka Producer.
	 - A producer record is also fairly basic and straightforward, it only requires two properties to be set in order for it to be considered a valid record sent by the Kafka Producer (two properties are the topic and the value).
	 - The topic to which these records directed. The value is really just the contents of the message that are to be serialized using the specific serializer in the configuration settings. 
	 
	 The Producer Record provides other properties as well (partition,  timestamp and key). 
	 
	 - When creating a producer record, you can set a specific **Partition** value to send a message to a specific **Partition** (the message you want to sent it to specific broker)
	 - It allows for the explicit setting of a **Timestamp** to the producer record and it's long data type.
		- The actual timestamp that will be logged for a message will be based on settings defined in the broker server.properties file, specifically the log.message.timestamp.type setting and there are two modes available.
		- **CreateTime**, which is the default, the timestamp applied to the message is set by the producer and will be what is committed to the log.
		- **LogAppendTime**, which will overwrite whatever the timestamp is coming from the producer with the timestamp of the broker at the time the message is appended to the log.
	
	 - The **Key** is a value that,  determine to which
	   partition within a topic the Kafka producer will be sending the
	   messages.

------------


### - Messages inside the Producer

 - Calling the send method on producer, then producer will reach out to the cluster using the bootstrap.servers list to discover the cluster membership.
 - The response comes back as metadata, containing detailed information related to the topics, their partitions and their managing brokers on the cluster.
 - Now producer having an actual producer record to work with, the first step in this process will be to pass the message through the serializer using the configured serializer.
 - The next step in the process is the partitioner, whose job it is to determine what partition to send the record to. The producer can employ different **partitioning strategies**, depending on the values being passed to it in the producer record.
	 - **Direct Partitioning Strategy :** If producer record contains partition value then it direct goes to specified partition.
	 - **Round Robin Partitioning Strategy :** If producer record doesn't contain partition and key value then it goes in round robin fashion, each partition receive a batch with single record.
	 - **Hash Partitioning Strategy :** If producer record contains key value then hash strategy calculate the hash value and record goes to calculated partition.
	 - **Custom Partitioning Strategy :** User can provide custom partition strategy by configuration properties called PARTITIONER_CLASS_CONFIG.


------------


### - Process of Sending Messages
 
 - Once the partitioning scheme established, the producer can now
   dispatch the producer record in‑memory queue‑like data
   structure called a RecordAccumulator.
 - Each time you send, persist, or read a message, resource overhead is
   incurred. Kafka's addressing this inefficiencies by micro‑batching.
 - The RecordAccumulator gives the producer its ability to micro‑batch
   records intended to be sent at high volumes and high frequencies. 
 - Producer record handed over to a RecordAccumulator, where it will be added to a collection of record batch objects.
 - Each of these RecordBatch objects is going to be sent to the broker that owns the assigned partition.
 - There are a lot of **configuration settings** that determine how many producer records are to be accumulated and buffered into a RecordBatch before it is sent off to the brokers.
	 - **batch.size :** This batch.size value represents the maximum number of bytes that can be buffered per each RecordBatch.
	 - **buffer.memory :** The buffer.memory setting to establishes threshold value for how much memory can be used to buffer records waiting to be sent to the brokers.
	 - **max.block.ms :** If the high volume of records being buffered reaches the threshold established by the buffer.memory setting, the max.block .ms setting comes into effect. This setting determines how many milliseconds the send method will be blocked.

------------

### - Message Delivery 
To ensure the best chance of delivery, The `acks` setting is a producer configuration. It denotes the number of brokers that must receive the record before we consider the write as successful. It support three values — `0`, `1`, and `2`.

 - **‘acks=0’ :** With a value of `0` (fire and forget), the producer won’t even wait for a response from the broker. It immediately considers the write successful the moment the record is sent out.
 - **‘acks=1’ :** With a setting of `1` (middle of the road), the producer will consider the write successful when the leader receives the record. The leader broker will know to immediately respond the moment it receives the record and not wait any longer.
 - **‘acks=2’ :** When set to `2`, the producer will consider the write successful when all of the in-sync replicas receive the record. This is achieved by the leader broker being smart as to when it responds to the request — it’ll send back a response once all the in-sync replicas receive the record themselves.

------------

### - Ordering Guarantees

 - Depending on your application, message ordering can be important but
   message order is only preserved within a given partition.
 - If the producer sends messages to a partition in a specific order, that order will be the order in which the broker appends them to the log and it will be the order that the consumers will read them from the log.
 - Messages sent to multiple partitions, will not have a global order due to partitioning strategies to send record on multiple partitions.
 - But to achieve global order across partitions, the order logic will have to be handled at the consumer level.

------------

### - Advanced Topics

 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY3NTE4MDM4MiwtNzM0MjYzMTkzLDE3MT
cyMTk3NzQsLTkzOTczNjE1OCwtMTAwOTY0NTAxMywtNzkyMDk4
OTAyLC0xNjE2NjI4ODE2LC0xMDI4MDYyOTI1LDE4MDMzNTQ1Mj
YsLTQyNjc1OTY4MywtMTI1NzEwMTAzNSwxNjM4OTIzOTAzLC0x
NTg5Nzg2NTE4LDYxMTAwOTM2MywxMTY4NDk4MjAyLDc1MjI0OT
cxNSwtMjg4NDA2NDg3LDE2MTc0OTU3NDQsMzYyNjE5NDgxLDIw
MzU4MjE1MzRdfQ==
-->