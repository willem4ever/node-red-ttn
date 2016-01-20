# node-red-ttn node-red extension for the things network

Works with MQTT published messages by looking at the msg.payload.rawData and applying your own Application session key (AppSKey)

to setup:

npm install crypto-js

copy 90-TTN.js and 90-TTN.html to node_modules/node-red/nodes/core/parsers/

reload node-red the new node should appear as decrypt-ttn

create a flow with mqtt listening at e.g. nodes/02031901/packets -> json -> decrypt-ttn -> debug (msg.decrypted) 
In the debug console you should see something as:

{"node": "02031901", "base64": "3q2+7wUGBw=="} or {"node": "02031901", "string": "Hello"}

Non readable data is packed as base64 encoded data, readable is readable and presented in string.

note: There is little or no error checking so your milage may vary.
