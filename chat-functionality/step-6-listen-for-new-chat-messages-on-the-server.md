# Listen for new chat messages on the server

{% code-tabs %}
{% code-tabs-item title="src/server/index.js" %}
```javascript

const socketIo = require("socket.io");
const io = socketIo(server);

io.sockets.on("connection", function(socket){
  socket.on("newChatMessage", function(chatMessage) {
    console.log("I have a new chat message!");
    console.log(chatMessage);
  });
});


```
{% endcode-tabs-item %}
{% endcode-tabs %}

