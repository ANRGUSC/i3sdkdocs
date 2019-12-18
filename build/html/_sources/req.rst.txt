==========================================
Requirements and Installation
==========================================

To follow the instructions in this documentation, users need access to an I3 instance. And, the data marketplace frontend has been tested on browsers such as Chrome and Firefox. 

The sellers and buyers are required to publish and subscribe to data, respectively. For this process, we recommend the users to use an MQTT client. Paho-MQTT-python is a Python implementation of MQTT. We provide sample publish-subscribe scripts for the I3 users: `I3-SDK <https://github.com/ANRGUSC/I3-SDK/tree/master>`_.

First of all, install paho-mqtt-python, using pip as follows:

 .. code-block:: bash

     $ pip3 install paho-mqtt==1.3.1

Here we specify the version as 1.3.1 while installing. The `Eclipse Paho <https://www.eclipse.org/paho/>`_ project is an excellent source of MQTT clients, which contains implementations in C, Java, Javascript, Python (contributed from the mosquitto project), Lua, C++, embedded/minimal C, and Go.
