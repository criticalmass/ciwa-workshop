# Send chat messages from client

To send our chat messages from our client side application to the server lets a create a new function in our client side script that will accept a name and a msg argument. 

Then we will create a "chatMessage" javascript object and send that to our server using the **socket.emit** function.

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

{% hint style="info" %}
The socket.emit function takes in two arguments. The first is argument is the "name" or "label". This can be anything you want, but it needs to be consistent between the client and the server. The second argument is the data you want to emit.
{% endhint %}

We now have a function that will send data to our server that we can call from our existing form submit handler.

