## Generally, seems your hostnames aren't resolvable. Does ping ubuntukafka work? If not, then you'll need to adjust what you're making Kafka return via advertised.listeners to be the external IP rather than the hostname

* listeners=PLAINTEXT://0.0.0.0:9092
* advertised.listeners=PLAINTEXT://10.75.1.247:9092

 Where, 10.75.1.247 is the network address to be resolved by the external machines (e.g. make sure you can ping that address, too)
