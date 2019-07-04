# Listen for new chat messages on the client



{% code-tabs %}
{% code-tabs-item title="src/client/script.js" %}
```javascript
socket.on("newChatMessage", function(chatMessage) {  
  const name = chatMessage.name;
  const msg = chatMessage.msg;
  updateMessages(name, msg);
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

