# MQTT MYSQL NODE  

If you have to save data from a MQTT broker into a mysql database.


## Functionality of Plugin

This node script connects to the MQTT broker as a client and to the mysql database as a user. 

It can subscribe to topics and every time the broker is sending a message it saves it to the mysql database.

Plugin will be in sync with your MQTT Broker and simultaneously will be in connectivity with your DB.

Whenever any activity happens on MQTT Broker it will Stores the Topic and Payload in an array and pass that as a parameter into the connected DB



## How to Use

1. move to the directory where you have kepp this plugin
2. Just Update the MQTT Broker_URL and Database_URL
3. Make Sure you have install all the required packages if not then 
4. npm install mqtt --save
5. npm install mysql-server --save
6. npm mqttTOmysql.js

Add a service on the server or start it manually.
