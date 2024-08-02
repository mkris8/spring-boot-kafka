# Introduction:
Apache Kafka is a popular distributed streaming platform that allows you to build scalable, fault-tolerant, and high-throughput applications.

## Spring boot Kafka Integration

### Gradle Dependency
`dependencies {
implementation 'org.springframework.kafka:spring-kafka'
implementation 'org.springframework.boot:spring-boot-starter-web'
}`

### Configuring Kafka in Spring Boot
- Update Application.yaml

`spring.kafka.bootstrap-servers=localhost:9092`

`spring.kafka.consumer.group-id=my-group-id`

- Create Kafka Producer Config
- Create MessageProducer in the same package to send messages to a Kafka topic
- Create Kafka consumer to receive messages from the Kafka topic.
- Create MessageConsumer in the same package to listen for messages from the Kafka topic
- Create a REST controller

### Install Kafka
`MINGW64 ~
$ cd IdeaProjects/Kafka/`

`MINGW64 ~/IdeaProjects/Kafka
$ ll
total 117908
-rw-r--r-- 1 manoj 197610 120735482 Aug  1 21:33 kafka_2.13-3.8.0.tgz`

`MINGW64 ~/IdeaProjects/Kafka
$ tar -xzf kafka_2.13-3.8.0.tgz`

`MINGW64 ~/IdeaProjects/Kafka
$ ll
total 117912
drwxr-xr-x 1 manoj 197610         0 Jul 23 09:09 kafka_2.13-3.8.0/
-rw-r--r-- 1 manoj 197610 120735482 Aug  1 21:33 kafka_2.13-3.8.0.tgz`

`MINGW64 ~/IdeaProjects/Kafka
$ cd kafka_2.13-3.8.0`

### SET JAVA_HOME

`MINGW64 ~/IdeaProjects/Kafka/kafka_2.13-3.8.0
$ nano ~/.bashrc`

`MINGW64 ~/IdeaProjects/Kafka/kafka_2.13-3.8.0
$ source ~/.bashrc`

`export JAVA_HOME='/c/Users/manoj/.jdks/liberica-full-21.0.4'
export PATH=$JAVA_HOME/bin:$PATH`

`MINGW64 ~/IdeaProjects/Kafka/kafka_2.13-3.8.0`
`$ echo $JAVA_HOME
/c/Users/manoj/.jdks/liberica-full-21.0.4`

`MINGW64 ~/IdeaProjects/Kafka/kafka_2.13-3.8.0
$ java -version
openjdk version "21.0.4" 2024-07-16 LTS
OpenJDK Runtime Environment (build 21.0.4+9-LTS)
OpenJDK 64-Bit Server VM (build 21.0.4+9-LTS, mixed mode, sharing)`

###  Start zookeeper
`MINGW64 ~/IdeaProjects/Kafka/kafka_2.13-3.8.0
$ ./bin/zookeeper-server-start.sh config/zookeeper.properties`

### Start Kafka in another terminal

`MINGW64 ~/IdeaProjects/Kafka/kafka_2.13-3.8.0
$ ./bin/kafka-server-start.sh config/server.properties`

### Use postman to test
`http://localhost:8080/send?message=Hello_Kafka`

In application.log , the message will be consumed ...

`2024-08-02T16:46:50.565+01:00 DEBUG 24776 --- [org.springframework.kafka.KafkaListenerEndpointContainer#0-0-C-1] .a.RecordMessagingMessageListenerAdapter : Processing [GenericMessage [payload=Hello_Kafka2, headers={kafka_offset=3, kafka_consumer=org.springframework.kafka.core.DefaultKafkaConsumerFactory$ExtendedKafkaConsumer@2700bd19, kafka_timestampType=CREATE_TIME, kafka_receivedPartitionId=0, kafka_receivedTopic=my-topic, kafka_receivedTimestamp=1722613610484, kafka_groupId=my-group-id}]]`
