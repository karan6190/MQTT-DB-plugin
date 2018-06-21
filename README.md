# MQTT-DB-plugin
Most of the time we face problem while dumping all the payload comming to our MQTT Broker to our required DB.

So I have created the Plugin which will act as a heart beat for our MQTT Broker and keep on dumping all the payload to our DB

## Functionality of Plugin

Plugin will be in sync with your MQTT Broker and simultaneously will be in connectivity with your DB.
Whenever any activity happens on MQTT Broker it will Stores the Topic and Payload in an array and pass that as a parameter into the connected DB
```
//receive a message from MQTT broker
function mqtt_messsageReceived(topic, message, packet) {
	console.log('mqtt_messageReceived :' topic,payload);
	var message_str = message.toString();                   //convert byte array to string
	console.log("message to string", message_str);
	message_str = message_str.replace(/\n$/, '');           //remove new line
    console.log("message to params array",message_str);
	//payload syntax: clientID,topic,message
	if (message_str.length == 0) {                        // checking if blank payload is send
		console.log("Invalid payload");
		} else {	
		insert_message(topic, message_str, packet);         //calling Insert Function
		//console.log(message_arr);
	}
```
```
//insert a row into the tbl_messages table
function insert_message(topic, message_str, packet) {
	var message_arr = extract_string(message_str); //split a string into an array
	var clientID= message_arr[0];
	var message = message_arr[1];
	var date= new Date();
	var sql = "INSERT INTO ?? (??,??,??,??) VALUES (?,?,?,?)";
	var params = ['tbl_messages', 'clientID', 'topic', 'message','date', clientID, topic, message, date];
	sql = mysql.format(sql, params);	
	
	connection.query(sql, function (error, results) {
		if (error) throw error;
		console.log("Message added: " + message_str);
	}); 
```

So what you have to do is before activating this plugin, you have to create the table and schema in your MYSQL DB
Credentials for the DB
> _DatabaseName=mydb

> _DatabaseUSerName=newuser

> _DatabasePassword=mypassword

> _TableName=tbl_messages

## How to Use

1. move to the directory where you have kepp this plugin
2. Just Update the MQTT Broker_URL and Database_URL
3. Make Sure you have install all the required packages if not then 
4. npm install mqtt --save
5. npm install mysql-server --save
6. npm mqttTOmysql.js
