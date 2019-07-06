# Listen for new chat messages on the server

Now that our client side application is emitting \(sending\) chat messages to our server, let's update our server code to "listen" for those new chat messages.

We do this with Socket.IO by taking advantage of the "socket.on" function. 

Let's add a `console.log` message to our listener and check to see if we are getting new chat messages from our client.

**Extra reading:** A `console.log` message is used by developers to send messages from our script into the console. We use this to find errors in the code, or to learn more about how the code works.

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

Once we are receiving chat messages from our client application, we can then move on to sending that same message back to all our other users.

