# Send chat messages from client

{% code-tabs %}
{% code-tabs-item title="src/client/script.js" %}
```javascript
function postChatMessageToServer(name, msg) {
  // convert the function arguments to a single JavaScript object
  const chatMessage = {
    name: name,
    msg: msg
  };

  // send the data to the server using socket.io
  socket.emit("newChatMessage", chatMessage);
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

