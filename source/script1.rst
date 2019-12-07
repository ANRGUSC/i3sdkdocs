===============================
**I3 SDK Documentation**
===============================


Introduction
-------------------------------

| MQTT is a machine-to-machine (M2M)/ “Internet of Things” connectivity protocol. MQTT stands for Message Queuing Telemetry Transport. It is a publish-subscribe-based messaging protocol. It works on top of the TCP/IP protocol.

| The important terminologies in MQTT are as follows:

| **Publisher**: The one which publishes messages to the outer world.

| **Subscriber**: The one which receives messages that are intended for it.

| **Client**: A client can be either publisher or subscriber or both. That is a client publish a message and receive another message at the same time.

| **Server/Broker**: The one receives the messages published by the publisher first, even before the subscriber. Then the server publishes the messages to the subscribers after filtering the messages. Both the names server and broker mean the same entity.

| **Topic**: An UTF-8 string used by the clients and servers to send and receive messages.

I3 Marketplace
--------------------------------

| Devices in I3 marketplace are registered under hubs, and also require valid input when creating. Invalid input will redirect you to the device create page without further prompt. 

| Device names are auto tagged as {USER_NAME}${HUB_NAME}${DEVICE_NAME}. 

|  ‘$’ is used as a separator, instead if ‘/’, because ‘/’ is considered dangerous username in mqtt authentication check, and ‘/’ is necessary for mqtt topic authorization wildcard matching.

|  The other “invisible” user interface is the MQTT pub/sub broker, equipped with an authentication-authorization plugin, plus a Json Web Token signature verification function (built with pyjwt and c-python connector inside the plugin). The 1883 and 8883 (MQTT+TLS, currently not opened yet) ports are exposed for publish and subscribe. 

|  MQTT connect requests mainly consist of five parts: username, password, topic, socket, pub or sub. For sellers: In the pub script, there’s nothing related to the seller himself. It was really the seller’s device that’s publishing, the device has a name, credential and permission. But of course, the devices are not alive, so the seller has to do everything for them.

For Sellers
-------------------------


|  In the pub script, there’s nothing related to the seller himself. It was really the seller’s device that’s publishing, the device has a name, credential and permission. But of course, the devices are not alive, so the seller has to do everything for them. 

|  1. MQTT username and topic name: Provide the **FULL** device name in connect request, also the FULL topic name. Don’t use wildcard for topic subscription. In the future we’ll allow sub-topic management, where if you buy a topic, you’ll buy all its sub-topics. 

|  2. In mqtt connect request, provide your device password if this device is registered using api key. Note that it is the original password that you should provide, not the hashed password or something else. We’ll take care of the “de-hash” for you. Of course, we can’t know your password directly from database, but we can check if the password that you provided in publishing is indeed correct.

  .. image:: pub1.PNG

| Input the password created while creating device. You can also update it from Edit Device

  .. image:: pub2.PNG

|  3. If your device is registered by an asymmetric key pair and you’ve provided your public key to I3, generate a Json Web Token claim and sign it with your private key (paired with the public key you provided to I3). Signature has to be performed using RS256, and right now only supports limited jwt fields. Specify an expire time for your token, after which it will be invalid for authentication. But no auto disconnection is performed when your token expires (you just can’t use this token to connect again). Directly use the token as the password for authentication. 

| In order to generate the public and private key 
| There’s no addition information you need to provide, such as how you registered your device. We’ll take care of everything, you just need to provide the necessary basic information. 

| **Please don’t use your private key string as the password!** 


| If you find the above process confusing, please check how AWS uses two asymmetric key pairs to handle SSH authentications. 

| (You registered your virtual machine instance by providing your public key, and SSH encryption uses AWS’s public key to encrypt the message that has your private key digital signature)

For Buyers
-------------------------------

| In the sub script, it’s much easier! The subscriber is just the person, so just use your credential and username to subscribe to a topic. If you bought an actuator topic, just provide the same information and publish to the topic.


| Input the details from the I3 Marketplace webpage in the sub.py file as shown in the snapshot below. You will recieve a password when you purchase a product. For restricted products, you will get notification and password once approved by seller.

  .. image:: sub1.PNG

| The sample output demonstrating the working of pub/sub in different terminals:

  .. image:: out1.PNG


| This is the end of the documentation.