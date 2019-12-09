===============================
**I3 SDK Documentation**
===============================



**INTRODUCTION**

| MQTT is a machine-to-machine (M2M)/ “Internet of Things” connectivity protocol. MQTT stands for Message Queuing Telemetry Transport. It is a publish-subscribe-based messaging protocol. It works on top of the TCP/IP protocol.

| The important terminologies in MQTT are as follows:

| **Publisher**: The one which publishes messages to the outer world.

| **Subscriber**: The one which receives messages that are intended for it.

| **Client**: A client can be either publisher or subscriber or both. That is a client publish a message and receive another message at the same time.

| **Server/Broker**: The one receives the messages published by the publisher first, even before the subscriber. Then the server publishes the messages to the subscribers after filtering the messages. Both the names server and broker mean the same entity.

| **Topic**: An UTF-8 string used by the clients and servers to send and receive messages.
