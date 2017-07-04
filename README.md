# Cartesian Product 2 - The class project

Class Project for DSCI-6009-SU17

So far:
 Kafka broker that ingests data from plume.io [work in progress]




## Kafka producer in Scala

Start Zookeeper.
If you have installed zookeeper, start it, or run the command:     
`bin/zookeeper-server-start.sh config/zookeeper.properties`

Start Kafka with default configuration               
`> bin/kafka-server-start.sh config/server.properties`

Create a Topic - **'plume_pollution'**        
`> bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 10 --topic plume_pollution`

To show all content in a topic (and to check the Producer is working), have the command line consumer running:
` bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic plume_pollution --
from-beginning`


Package project       
`sbt assembly`
It will package compiled classes and its dependencies into a jar.

Run the Producer
The Producer is a Scala file located at `src\main\scala\KafkaBroker.Scala`
Once packaged in a JAR you can run the producer with the following arguments:
`scala cartesianproduct2-assembly-1.0.jar plume_pollution localhost:9092 48.85 2.294 1000 `
where:
+ __title:__ plume_pollution
+ __broker:__ localhost:9092
+ __latitude:__ 48.85
+ __longitude:__ 2.294
+ __sleepTime:__ 1000

> For additional information about Kafka, Plume API or Plume token check the [WIKI](https://github.com/zipfian/cartesianproduct2/wiki)

Output
If all is working, you should see the following output:
![IntelliJ Producer Output ](https://raw.githubusercontent.com/gth158a/experience/master/kafka/images/intellij_producer_output.png)
![Terminal Kafka Consumer Output ](https://raw.githubusercontent.com/gth158a/experience/master/kafka/images/kafka_consumer_output.png)

# Additional Kafka commands
List topics
