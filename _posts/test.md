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
	 
	 The Producer Record provides other properties as well (partition and timestamp). 
	 
	 - When creating a producer record, you can set a specific partition value to send a message to a specific partition (the message you want to sent it to specific broker)
	 - It allows for the explicit setting of a timestamp to the producer record and it's long data type.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMjg3MjUxMTAsMTYzODkyMzkwMywtMT
U4OTc4NjUxOCw2MTEwMDkzNjMsMTE2ODQ5ODIwMiw3NTIyNDk3
MTUsLTI4ODQwNjQ4NywxNjE3NDk1NzQ0LDM2MjYxOTQ4MSwxNj
I0MzQzMDQwLDIwMzU4MjE1MzQsLTEyOTgxMTIzMTQsLTQ0NTIz
MDczMCwtOTY5OTU5MzYsLTE2NjA1NDkzNjksLTE2MzQ3NTM3MT
UsMTE4NTU3NzA3MCwtMjA1NDQ4NjY4MSwtNDcwNDUyNjA4LDY1
MDg5ODE4XX0=
-->