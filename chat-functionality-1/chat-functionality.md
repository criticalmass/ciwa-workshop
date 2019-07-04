# Overview / Socket.IO

## Socket.IO

Now it's time to add the last missing, yet crucial piece to our app: _chat functionality_!

To do this, we will leverage yet another 3rd party Node module/dependency. It's called Socket.IO.

Socket.IO will leverage a technology that browsers have called Web Sockets.

What's nice about Socket.io is that it will let us write similar JS code on both the client \(browser\) side and at the server \(Node\) side.

Check it out here: [http://socket.io/](http://socket.io/).

### Requirements

1. Setup our HTML form to submit a chat message to the server using Socket.IO.
2. Update our server code to use Socket.IO and listen for new chat messages from clients.
3. Update our server code to use Socket.IO to emit any new messages to all connected clients.
4. Update our client code to display the new chat messages as they are received from the server.

### STEP X: Add Socket.IO script to HTML

The first then we need todo is add the client side Socket.IO dependency to our web page by using the **HTML &lt;script&gt; element**. It's been provided for you in your boilerplate code, but you will need to uncomment the following line.

{% code-tabs %}
{% code-tabs-item title="src/client/index.html" %}
```markup
<script src="/socket.io/socket.io.js"></script>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### STEP X: Prepare Socket.IO in our client side JavaScript

After we've added the Socket.IO script to our html page. Our JavaScript file will have access to Socket.IO through a global variable **"window.io".** We can then use this dependency to create a Socket connection between our client application and our server using the origin url.

{% code-tabs %}
{% code-tabs-item title="src/client/script.js" %}
```javascript
// import Socket.IO and create socket connect with server.
const io = window.io;
const url = window.location.origin;
const socket = io.connect(url);
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Create a new JavaScript function to send chat messages using Socket.IO

{% code-tabs %}
{% code-tabs-item title="src/client/script.js" %}
```javascript
// this function accepts and name and message as arguments
// and then sends them to the server using socket.io
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

### Update our form submit handler to use our postChatMessageToServer function

```javascript
form.addEventListener("submit", function(event) {
  // prevent the form from trying to submit values using the method/action attributes.
  event.preventDefault();

  // extract the name and message data from the inputs and pass them on.
  const name = nameInput.value;
  const msg = messageInput.value;

  postChatMessageToServer(name, msg);  
});
```

### STEP X: Prepare Socket.IO on our server

{% code-tabs %}
{% code-tabs-item title="src/server/index.js" %}
```javascript
const socketIo = require("socket.io");
const io = socketIo(server);

```
{% endcode-tabs-item %}
{% endcode-tabs %}

### STEP X: Update the server to EMIT all chat messages to all the clients.

### STEP 4: Update the client display all of the received chat messages.



```

```

