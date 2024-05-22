<img width="859" alt="image" src="https://github.com/Jewel73/kafka-notes/assets/46159821/677476eb-bfb4-435b-9bbf-a31a9f7d1cfe"># Kafka Producer Internal Architecture 

* kafka use internal queue
* kafka first serialize the message
* use partitionar to select the correct parition based on key hash
* sent data to the broker and retry if fail

## Producer Internal Image

<img width="859" alt="image" src="https://github.com/Jewel73/kafka-notes/assets/46159821/917ad864-b6f4-4f89-817b-af378ae72a3a">


