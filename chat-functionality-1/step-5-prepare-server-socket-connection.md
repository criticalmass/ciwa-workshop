# Step 5 - Prepare server socket connection

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

