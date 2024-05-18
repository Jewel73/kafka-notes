![image](https://github.com/Jewel73/kafka-notes/assets/46159821/a0915a7c-3b33-4a36-ad2b-dbc5eb01c29d)# Zookeeper in Kafka Cluster

## Introduction

Zookeeper plays a crucial role in managing Kafka clusters by maintaining metadata and coordinating distributed systems. In Kafka, Zookeeper is primarily used for cluster coordination, leader election, and maintaining metadata such as topic configurations, partition assignments, and broker states.

## Key Concepts

- **Zookeeper**: A centralized service for maintaining configuration information, naming, providing distributed synchronization, and group services.
- **Kafka Cluster**: A collection of Kafka brokers working together to store and distribute data.
- **Controller**: A special broker in the Kafka cluster responsible for managing leader election, partition reassignment, and other administrative tasks.

## Zookeeper and Kafka Cluster

- **Zookeeper Connection String**: Kafka brokers connect to Zookeeper using a connection string specified in their configuration (`zookeeper.connect` property). The connection string includes the hostname and port of each Zookeeper server.
- **Zookeeper Znodes**:
  - `/brokers/ids`: Contains a list of broker IDs and their metadata.
  - `/brokers/topics`: Contains a list of topics and their partition assignments.
  - `/controller`: Contains information about the current controller broker.
 
![image](https://github.com/Jewel73/kafka-notes/assets/46159821/7f310845-b5c4-48ba-b17b-5dc4979236f3)

## Viewing Zookeeper Brokers and IDs

To view Zookeeper brokers and their IDs, you can use the `zkCli.sh` script provided by Zookeeper:

```bash
# Connect to Zookeeper
./bin/zkCli.sh -server localhost:2181

# List Zookeeper brokers and their IDs
ls /brokers/ids



