======================================
I3 Marketplace
======================================

| Devices in I3 marketplace are registered under hubs, and also require valid input when creating. Invalid input will redirect you to the device create page without further prompt. 

| Device names are auto tagged as {USER_NAME}${HUB_NAME}${DEVICE_NAME}. 

|  ‘$’ is used as a separator, instead if ‘/’, because ‘/’ is considered dangerous username in mqtt authentication check, and ‘/’ is necessary for mqtt topic authorization wildcard matching.

|  The other “invisible” user interface is the MQTT pub/sub broker, equipped with an authentication-authorization plugin, plus a Json Web Token signature verification function (built with pyjwt and c-python connector inside the plugin). The 1883 and 8883 (MQTT+TLS, currently not opened yet) ports are exposed for publish and subscribe. 

|  MQTT connect requests mainly consist of five parts: username, password, topic, socket, pub or sub. For sellers: In the pub script, there’s nothing related to the seller himself. It was really the seller’s device that’s publishing, the device has a name, credential and permission. But of course, the devices are not alive, so the seller has to do everything for them.