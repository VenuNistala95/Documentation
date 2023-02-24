# Documentation

How to download and install Kafka, Zookeeper and set up producer and consumer.
Step 1: Download apache kafka from https://kafka.apache.org/downloads 
  Note: Download the Binary, not source. I have downloaded - Scala 2.12  - kafka_2.12-3.4.0.tgz (asc, sha512)
Step 2: Download apache zookeeper from https://www.apache.org/dyn/closer.lua/zookeeper/zookeeper-3.8.1/apache-zookeeper-3.8.1-bin.tar.gz
Step 3: Download 7Zip from https://www.7-zip.org/download.html
  Note: Run 7Zip.exe as administrator on your machine
Step 4: Using 7Zip, extract the apache kafka(kafka_2.12-3.4.0.tgz) to kafka_2.12-3.4.0.tar. 
Again using 7Zip, extract kafka_2.12-3.4.0.tar to a folder named "kafka" in your C drive. 
Note: It is important to extract and save the kafka files inside kafka folder. else you will receive an error when starting kafka server.
Step 5: Using 7Zip, extract the apache zookeeper to your local C drive --follow the steps similar to kafka extracting. 
Extract the files to a folder named "zookeeper" to you C drive

#Configuring zookeeper and Kafka
After extracting files to zookeeper folder, create a new folder inside zookeeper and call it "data"
Now go to zookeeper>conf> 
Find the file name "zookeeper_sample.cfg" and rename it to "zoo.cfg".
Open this file with notepad ++ or any text editor. 
Locate the element "dataDir" and give the path to the "data folder" created in the above steps.
Save the cfg file. got to zookeeper>bin ; open command prompt and run the command "zkserver" . This will spin up the zookeeper server.

#configuring kafka
After extracting files to kafka folder, create a new folder inside kafka and call it "kafka-logs"
Now go to kafka>config>
Find the file named "server.properties", open with notepad ++ or any text editor
Localte the element "logsDIR" and provide the path to "kafka-logs" folder. click save
Now go to kafka>bin>windows. Open command prompt and run the command kafka-server-start.bat .\config\server.properties. This will spin up kafka server

#configuring kafka producer and consumer
Go to kafka>bin>windows. Open a new command prompt and run the command
"kafka-topics.bat --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic test" This will create your kafka topic.
You will receive a message "Created topic test"
Now run the command 
"kafka-console-producer.bat --broker-list localhost:9092 --topic test"
This will spin up the kafka producer. 

Similarly open a new command prompt from the location kafka>bin>windows and run the below command
"kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic test"
This will spin up the kafka consumer. 

Now go to kafka producer command prompt and pass any message. For example "This is a message sent from producer to consumer". You will see the same message reflected in kafka consumer command prompt. 

Therefore, You have successfully set up your kafka server, created a topic called test, spun up producer, consumer and established a successful communication between them.
