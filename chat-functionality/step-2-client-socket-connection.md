# Client socket connection

After we've added the Socket.IO script to our html page. Our JavaScript file will have access to Socket.IO through the variable **"window.io".** We can then use this to create a new Socket connection between our client application and our server using the url of the page.

{% code-tabs %}
{% code-tabs-item title="src/client/script.js" %}
```javascript
// Add this to the top of your scr/client/script.js file.
// import Socket.IO and create socket connect with server.
const io = window.io;
const url = window.location.origin;
const socket = io.connect(url);
```
{% endcode-tabs-item %}
{% endcode-tabs %}

We now have a connection between our client and server and we are ready to send chat messages from our HTML form to our **Node.js** web server.

### 



