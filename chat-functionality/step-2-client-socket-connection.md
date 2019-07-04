# Client socket connection

After we've added the Socket.IO script to our html page. Our JavaScript file will have access to Socket.IO through a global variable **"window.io".** We can then use this dependency to create a new Socket connection between our client application and our server using the origin url.

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

### 

