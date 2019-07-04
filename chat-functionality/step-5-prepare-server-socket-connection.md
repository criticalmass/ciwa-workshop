# Prepare server socket connection

In order for our server to accept chat messages we first need to add the Socket.IO module as a dependency to our server code.

Once we've added the required dependencies we then need to use the dependency to open a connection. 

{% code-tabs %}
{% code-tabs-item title="src/server/index.js" %}
```javascript
const path = require("path");
const http = require("http");
const express = require("express");
const app = express();

const clientPath = path.resolve(__dirname, "../client/");
app.use(express.static(clientPath));
const server = http.Server(app).listen(8080);

// IMPORT SOCKET.IO & CREATE A SOCKET CONNECTION
const socketIo = require("socket.io");
const io = socketIo(server);

io.sockets.on("connection", function(socket){
  console.log("I HAVE A SOCKET CONNECTION!!!!");
});


```
{% endcode-tabs-item %}
{% endcode-tabs %}

Now our server is ready to accept socket connections!

