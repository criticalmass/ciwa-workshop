# Add Socket.IO script to HTML

We then need add the client side Socket.IO dependency to our web page by using the **HTML &lt;script&gt; element**. It's been provided for you in your boilerplate code, but you will need to uncomment the following line.

{% code-tabs %}
{% code-tabs-item title="src/client/index.html" %}
```markup
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
    <script src="/script.js"></script>
    <script src="/socket.io/socket.io.js"></script>
  </body>
</html>

```
{% endcode-tabs-item %}
{% endcode-tabs %}

Our client side web page is now has the required dependencies available for creating a socket connection with our server. 

### 

