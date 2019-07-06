# Overview / Socket.IO

Now it's time to add the last missing, yet crucial piece to our app: _chat functionality_!

### Socket.IO

To do this, we will leverage yet another dependency. It's called Socket.IO. Socket.IO allows us to easily set up communication between multiple different browsers/computers. What's nice about Socket.io is that it will let us write similar JS code on both the client \(browser\) side and at the server \(Node\) side.

You can check it out here: [http://socket.io/](http://socket.io/)

### Chat Application Requirements

1. Our HTML form needs to send \(submit\) messages to the server. 
2. The server needs to listen for those messages using Socket.IO.
3. The server then needs to send out those messages to all of the other connected clients, also using Socket.IO.
4. Once the client receives those messages, the messages should be displayed using HTML. 

## 







```

```

