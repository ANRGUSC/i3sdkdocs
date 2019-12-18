=====================================
Sending and Receiving Data Using MQTT
=====================================
The other “invisible” user interface is the MQTT publish-subscribe broker, equipped with an authentication-authorization plugin, along with a JSON Web Token signature verification function (built with pyjwt and c-python connector inside the plugin). The 1883 and 8883 (MQTT+TLS, currently not opened yet) ports are exposed for publishers and subscribers. MQTT connect requests mainly consist of five parts: username, password, topic, socket, pub, or sub.

Data Publishing Guidelines for Sellers
---------------------------------------
The sellers create data products in the marketplace. After creating the product, they are required to publish the data to the marketplace MQTT broker. Whenever a buyer purchases data on the marketplace, the MQTT broker forwards the data to the buyer's device. Each publisher is required to run a publisher script to post the data to the data marketplace. In the publisher script, the seller needs to include product information such as name, credential, and permission. 

**MQTT username and topic name**: Provide the FULL device name in the connection request, also the FULL topic name. 

In MQTT connect request, the sellers are required to provide their device password if this device is registered using the API key. If your device is registered by an asymmetric key pair and you’ve submitted your public key to I3, generate a JSON Web Token claim and sign it with your private key (paired with the public key you provided to I3). Signature has to be performed using RS256, and right now only supports limited jwt fields. Specify an expiry time for your token, after which it will be invalid for authentication. But no auto disconnection is performed when your token expires (you can’t use this token to connect again). Below is a python example to sign a token using a private key file and print it to the command line (valid for 1 minute). For now, please only use ‘iss’, ‘iat’, ‘exp’ fields. Directly use the token as the password for authentication. 

NOTE, please don’t use your private key string as the password! 

Data Subscribing Guidelines for Buyers
---------------------------------------
The buyers purchase data products from the marketplace. When a buyer buys a product, he or she will receive credentials to subscribe to the data. Note that the MQTT broker forwards the data to the buyer's device after he has paid for the product, although the current version of the data marketplace does not provide support for real payments. 

Each subscriber is required to run a subscriber script to access the data from the data marketplace. In the subscriber script, the buyer needs to include product information such as name and credential. 
