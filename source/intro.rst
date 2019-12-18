===================================
**Overview of I3 Data Marketplace**
===================================


Introduction
------------
The I3 data marketplace is a community-driven IoT platform to allow the device owners to sell their application data to help the application developers. The users are required to follow the guidelines provided in this documentation to easily navigate 
through the frontend.


Terminologies
-------------

**Marketplace**: The marketplace refers to an I3 instance made available by an organization, including a city or a community. An open-source version of I3 data marketplace software is available `here <https://github.com/ANRGUSC/I3-SDK/tree/master>`_.

**Seller**: A seller is the owner of a device or the data, and he or she is willing to make the data available via the data marketplace.

**Buyer**: A buyer is the one who is buying data from the I3 data marketplace to create an application. 

**Broker**: One of the core components of the I3 architecture is a data broker. The current version of I3 uses MQTT as a data broker, which publish-subscribe messaging protocol for the IoT.

**Publisher**: In the publish-subscribe messaging protocol, data producers are considered as a publisher. Each data producer is required to publish the data to the I3 data marketplace after creating the data product on the marketplace. 

**Subscriber**: A subscriber is a data consumer. In the I3 data marketplace, the data buyers are required to subscribe to the data after purchasing the data product on the data marketplace.

**Topic**: The topic captures the metadata in a human-readable form. In the publish-subscribe communication model, the publisher and the subscriber exchange information with each other through topics. For example, a seller providing "temperature" data could name the topic as "temperature." When a buyer is building a temperature monitoring application can buy data from "temperature" to get access to the temperature feed.

