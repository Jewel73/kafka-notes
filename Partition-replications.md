# Kafka Topic Partition and Replication

## Key Concepts

- **Partitions**: Each topic is divided into partitions, which are ordered sequences of records.
- **Replication**: Partitions are replicated across multiple brokers to ensure fault tolerance.

## Examples

### Example 1: Replication Factor of 1

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

### Example 2: Replication Factor of 3

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

## Summary

- **Partitions** enable parallelism and scalability.
- **Replication** ensures data redundancy and fault tolerance.
- **Replication Factor**:
  - `1`: No replicas, potential data loss on broker failure.
  - `>1`: Multiple copies, enhanced reliability.

By configuring the replication factor, you can balance fault tolerance and resource utilization in your Kafka cluster.
