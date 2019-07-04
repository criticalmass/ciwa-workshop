# Send new chat messages to all connected clients

To send our new chat message to all our connect users we will update our event handler to "emit" the message using the "io.emit" method. 

This method will send the chat message to everyone, including the original author.

{% code-tabs %}
{% code-tabs-item title="src/server/index.js" %}
```javascript
const socketIo = require("socket.io");
const io = socketIo(server);

io.sockets.on("connection", function(socket){
  socket.on("newChatMessage", function(chatMessage) {
    io.emit("newChatMessage", chatMessage);
  });
});

```
{% endcode-tabs-item %}
{% endcode-tabs %}

This wraps up the server portion of our workshop. But we now have to make sure that our client application can update the messages list with new messages whenever the server emits a new chat message. 

