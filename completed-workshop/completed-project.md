# PLEASE DON'T CHEAT

{% code-tabs %}
{% code-tabs-item title="src/client/index.html" %}
```markup
<!DOCTYPE html>
<html>
  <head>
    <title>CIWA Workshop Chat Application</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <main>
      <h1>Hi, My Personal Chat Application!</h1>
      <ol id="history"></ol>
      <form id="chat" action="">
        <input id="name" placeholder="name" />
        <input id="message" placeholder="message" autocomplete="off" />
        <button>Send</button>
      </form>
    </main>
    <script src="/socket.io/socket.io.js"></script>
    <script src="/script.js"></script>
  </body>
</html>


```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="src/client/script.js" %}
```javascript
// import Socket.IO and create socket connect with server.
const io = window.io;
const url = window.location.origin;
const socket = io.connect(url);

// create a reference to all the html elements
// we will need for our chat application
const history = document.getElementById("history");
const form = document.getElementById("chat");
const nameInput = document.getElementById("name");
const messageInput = document.getElementById("message");

// this function accepts a name and a message as arguments
// and then appends the new message data to the list of chat messages.
function updateMessages(name, msg) {
  const newMsgListItem = document.createElement("li");
  newMsgListItem.textContent = `${name}: ${msg}`;
  history.appendChild(newMsgListItem);

  // after adding a new message, scroll the
  // element so the newest item is always visible
  history.scrollTop = history.scrollHeight;
}

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

// so we can easily send more messages we will empty out the
// message input and make sure that element is focused and ready
// for new input
function resetForm() {
  messageInput.value = "";
  messageInput.focus();
}

// listen for submit events from our form.
// extract the name and message and
form.addEventListener("submit", function(event) {
  // prevent the form from trying to submit values using the method/action attributes.
  event.preventDefault();

  // extract the name and message data from the inputs and pass them on.
  const name = nameInput.value;
  const msg = messageInput.value;

  postChatMessageToServer(name, msg);

  // reset the form for the next time we need to use it.
  resetForm();
});

// listen for new messages from the server
// extract the name and message data from the server data
// call the updateMessages function with our new name and message data.
socket.on("newChatMessage", function(chatMessage) {
  // extract the name and message data and pass it on to the update messages function.
  const name = chatMessage.name;
  const msg = chatMessage.msg;
  updateMessages(name, msg);
});


```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="src/client/sytles.css" %}
```css
body {
  background-color: white;
  color: #303030;
  font-family: "Helvetica Neue", Arial, sans-serif;
  font-size: 15px;
  margin: 20px;
}

main {
  background-color: #f0f0f0;
  border-radius: 6px;
  box-shadow: 3px 3px 12px #c8c8c8;
  margin: 20px auto;
  max-width: 700px;
  padding: 20px;
}

h1 {
  font-size: 18px;
  text-transform: uppercase;
  margin-top: 0px;
}

ol {
  list-style: none;
  margin-bottom: 20px;
  margin-top: 0;
  padding: 0;
  height: 400px;
  overflow: hidden;
  overflow-y: auto;
}

li {
  padding: 10px;
}

li:nth-child(odd) {
  background-color: #e3e3e3;
  border-radius: 6px;
}

form {
  background-color: lightsteelblue;
  border-radius: 6px;
  margin: 0;
  padding: 10px;
}

button {
  background-color: cornflowerblue;
  border: none;
  border-radius: 3px;
  color: white;
  font-size: 15px;
  font-weight: bold;
  padding: 5px 10px;
  text-transform: uppercase;
}

input {
  border: none;
  border-radius: 3px;
  font-size: 15px;
  padding: 5px;
}

::placeholder {
  color: #cccccc;
  opacity: 0.8;
}

#name {
  width: 100px;
}

#message {
  width: 480px;
}


```
{% endcode-tabs-item %}
{% endcode-tabs %}

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

const socketIo = require("socket.io");
const io = socketIo(server);

io.sockets.on("connection", function(socket) {
  socket.on("newChatMessage", function(chatMessage) {
    io.emit("newChatMessage", chatMessage);
  });
});


```
{% endcode-tabs-item %}
{% endcode-tabs %}

You can final a complete version of this workshop including comments here:  
[https://codesandbox.io/s/ciwa-workshop-final-px43i](https://codesandbox.io/s/ciwa-workshop-final-px43i)

