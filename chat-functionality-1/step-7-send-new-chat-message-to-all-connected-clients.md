# Step 7 - Send new chat message to all connected clients

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

