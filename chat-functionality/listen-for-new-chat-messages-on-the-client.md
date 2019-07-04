# Listen for new chat messages on the client

In a previous step, we were using the "updateMessages" function to output new chat messages 

We are going to take advantage of this existing function but this time call it from a Socket.IO event handler instead of our form submit event handler.  

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

If all goes well you should now have a fully function chat application! 



