# kafka-testing

Explore how Kafka Works
In this section you reviewed Kafka's architecture and how it stores data. In this exercise, you will spend some time seeing how Kafka works.

[start server](https://medium.com/@Ankitthakur/apache-kafka-installation-on-mac-using-homebrew-a367cdefd273) :

- zookeeper-server-start /usr/local/etc/kafka/zookeeper.properties
- kafka-server-start /usr/local/etc/kafka/server.properties



Topic Storage
First, let's create a topic

- kafka-topics --create --topic kafka-arch --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1

- Inspecting the Directory Structure
Now that the topic is successfully created, let's see how Kafka stored it on disk.

- ls -alh /var/lib/kafka/data | grep kafka-arch

What does the output look like?

What kind of data is kept inside of the directory?

- ls -alh /var/lib/kafka/data/kafka-arch*

If you try to open the file ending in .log is there anything in it?

Produce Data
Now that we have this topic, let's produce some data into it.

- kafka-console-producer --broker-list localhost:9092 --topic kafka-arch

Produce 5-10 messages.

- Kafka consumer  
- kafka-console-consumer --bootstrap-server localhost:9092 --topic kafka-arch --from-beginning

Repeat the steps from Inspecting the Directory Structure and see how the results have changed.

Topics and Partitions
Now that you've seen what a topic with a single partition looks like, let's see what happens if we modify the number of partitions

- kafka-topics --alter --topic kafka-arch --partitions 3 --zookeeper localhost:2181

Try repeating the steps from the previous section. How many folders do you see now?

Try modifying the number of partitions a few more times to see how Kafka modifies the data on disk.
