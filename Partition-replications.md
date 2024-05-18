# Kafka Topic Partition and Replication

## Key Concepts

- **Partitions**: Each topic is divided into partitions, which are ordered sequences of records.
- **Replication**: Partitions are replicated across multiple brokers to ensure fault tolerance.

## Folder Structure

When a topic is created, Kafka organizes the partitions and their replicas in the broker's data directory. Assuming the data directory is `/var/lib/kafka/data`, the structure looks like this:

**Example for Topic `my-topic` with 3 Partitions on 3 Brokers**:

![image](https://github.com/Jewel73/kafka-notes/assets/46159821/a4b6bbd8-59ef-4bbe-805a-c7f45d4f2c1d)


## Examples

### Example 1: Replication Factor of 1 : We want only one partition just no copy

- **Topic**: `my-topic`
- **Partitions**: 3
- **Replication Factor**: 1
- **Brokers**: 3

**Partition Distribution**:
- `my-topic-0` on Broker 1
- `my-topic-1` on Broker 2
- `my-topic-2` on Broker 3

**Description**:
Each partition is stored on a single broker. No redundancy. If a broker fails, the partition it hosts becomes unavailable.

### Example 2: Replication Factor of 3 : we want two copy of orginal partition

- **Topic**: `my-topic`
- **Partitions**: 3
- **Replication Factor**: 3
- **Brokers**: 3

**Partition Distribution and Replication**:
- `my-topic-0`:
  - Leader on Broker 1
  - Replica on Broker 2
  - Replica on Broker 3

- `my-topic-1`:
  - Leader on Broker 2
  - Replica on Broker 1
  - Replica on Broker 3

- `my-topic-2`:
  - Leader on Broker 3
  - Replica on Broker 1
  - Replica on Broker 2

**Description**:
Each partition is replicated across all three brokers, providing redundancy and fault tolerance. If any broker fails, the remaining brokers have all the data.

## Here you can see the topic information and which pertition is leader in which broker - broker specify using number here
<img width="635" alt="image" src="https://github.com/Jewel73/kafka-notes/assets/46159821/4f95bbfa-e17b-4756-acfe-11be0649fa6e">


## Segments and Offsets

- **Segments**: Each partition is divided into segments, which are sequentially numbered files on disk. These segments are immutable and contain a fixed number of records.
- **Offsets**: Within each partition, records are assigned unique offsets, representing their position in the partition. Offsets start from 0 and increment sequentially with each new record.


## Here you can see Segments file how it created , using the last offsent number, and you can see the offset value, we can set the maximum offset number that can be in file.
![image](https://github.com/Jewel73/kafka-notes/assets/46159821/67780bec-9859-4c5d-ad95-d7b802f0056a)


## Summary

- **Partitions** enable parallelism and scalability.
- **Replication** ensures data redundancy and fault tolerance.
- **Replication Factor**:
  - `1`: No replicas, potential data loss on broker failure.
  - `>1`: Multiple copies, enhanced reliability.

By configuring the replication factor, you can balance fault tolerance and resource utilization in your Kafka cluster.
