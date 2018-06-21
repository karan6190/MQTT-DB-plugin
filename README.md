# MQTT-DB-plugin
Most of the time we face problem while dumping all the payload comming to our MQTT Broker to our required DB.

So I have created the Plugin which will act as a heart beat for our MQTT Broker and keep on dumping all the payload to our DB

## Functionality of Plugin

Plugin will be in sync with your MQTT Broker and simultaneously will be in connectivity with your DB.
Whenever any activity happens on MQTT Broker it will Stores the Topic and Payload in an array and pass that as a parameter into the connected DB

So what you have to do is before activating this plugin, you have to create the table and schema in your MYSQL DB
Credentials for the DB
> DatabaseName=mydb

> DatabaseUSerName=newuser

> DatabasePassword=mypassword

> TableName=tbl_messages

## How to Use

1. move to the directory where you have kepp this plugin
2. Just Update the MQTT Broker_URL and Database_URL
3. Make Sure you have install all the required packages if not then 
4. npm install mqtt --save
5. npm install mysql-server --save
6. npm mqttTOmysql.js
