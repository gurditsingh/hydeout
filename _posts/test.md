# kafka Consumer
The primary role of a Kafka consumer is to take Kafka connection and consumer properties to read records from the appropriate Kafka topic. Complexities of concurrent application consumption, offset management, delivery semantics, and a lot more are taken care by Consumer APIs.

## Subscribing and Unsubscribing to Topics
Kafka use a `KafkaConsumer` to subscribe to Kafka topics and receive messages from these topics.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1MTAxODcwMiwyMTE3ODEyODgxLDE1MD
UyNzAyOTYsLTE5Njg2NzE3MywtNjM3MzM2MDA2LC04MjI4MTgy
NDAsLTIwNzMzNTQ2NzgsMTI1NzkxMzc2OCwtNzM0MjYzMTkzLD
E3MTcyMTk3NzQsLTkzOTczNjE1OCwtMTAwOTY0NTAxMywtNzky
MDk4OTAyLC0xNjE2NjI4ODE2LC0xMDI4MDYyOTI1LDE4MDMzNT
Q1MjYsLTQyNjc1OTY4MywtMTI1NzEwMTAzNSwxNjM4OTIzOTAz
LC0xNTg5Nzg2NTE4XX0=
-->