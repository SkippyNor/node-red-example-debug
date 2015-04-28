# node-red-example-debug

This is some example code to help with debugging Node-Red application flows.

To use it, you need a flow to output a webpage on "/debug", a subflow that outputs 
the msg object to MQTT, an MQTT broker that supports access over websockets 
(e.g. Mosquitto compiled with websockets or Mosca) and access to JQuery, Paho (MQTT web client) and the jquery-animate-shadow
plugin for consumption in the web page.

- Subflow. This adds a "DEBUG/" prefix to the msg.topic and outputs to MQTT.
- Page Flow. This listens for and outputs a web page on "/debug".

The resulting web page will be initially blank except for a title. However, it will be listening for output
from your MQTT broker on the "DEBUG/#" topic. Any recieved output will be dumped into an appropriate section element.
Each unique topic will get it's own output that will be updated on reciept of a new message for that topic.

Some JQuery animation magic can also be used to highlight which topic has just been updated.

The output of the message is formatted using the JavaScript JSON.stringify function if it is valid JSON, otherwise it is
treated as a simple string.