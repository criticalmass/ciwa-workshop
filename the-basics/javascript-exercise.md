# JavaScript Exercise

Now that we have the basics down for building web applications \(HTML, CSS & JavaScript\). Lets start building our chat functionality. To start will will talk to ourselves!  

In order to achieve this we need to learn how to do three things

1. Reference HTML elements using JavaScript
2. Handle the form submit event 
3. Update a chat messages with our new message

### Referencing HTML Elements

{% code-tabs %}
{% code-tabs-item title="src/client/script.js" %}
```javascript
const history = document.getElementById("history");
const form = document.getElementById("chat");
const nameInput = document.getElementById("name");
const messageInput = document.getElementById("message");
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Handle the Form Submit Event

{% code-tabs %}
{% code-tabs-item title="src/client/script.js" %}
```javascript
form.addEventListener("submit", function(event) {  
  event.preventDefault();  
  const name = nameInput.value;
  const msg = messageInput.value;
  console.log(name, msg);  
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Update chat messages container with our new message

{% code-tabs %}
{% code-tabs-item title="src/client/script.js" %}
```javascript
function updateMessages(name, msg) {
  const newMsgListItem = document.createElement("li");
  newMsgListItem.textContent = `${name}: ${msg}`;
  history.appendChild(newMsgListItem);
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Connect our event handler and our update messages function

{% code-tabs %}
{% code-tabs-item title="src/client/script.js" %}
```javascript
function resetForm() {
  messageInput.value = "";
  messageInput.focus();
}

form.addEventListener("submit", function(event) { 
  event.preventDefault();  
  const name = nameInput.value;
  const msg = messageInput.value;

  updateMessages(name, msg);  
  resetForm();
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Final Code

{% code-tabs %}
{% code-tabs-item title="src/client/script.js" %}
```javascript
const history = document.getElementById("history");
const form = document.getElementById("chat");
const nameInput = document.getElementById("name");
const messageInput = document.getElementById("message");

function updateMessages(name, msg) {
  const newMsgListItem = document.createElement("li");
  newMsgListItem.textContent = `${name}: ${msg}`;
  history.appendChild(newMsgListItem);
}

function resetForm() {
  messageInput.value = "";
  messageInput.focus();
}

form.addEventListener("submit", function(event) {.
  event.preventDefault();
  const name = nameInput.value;
  const msg = messageInput.value;
  updateMessages(name, msg);
  resetForm();
});

```
{% endcode-tabs-item %}
{% endcode-tabs %}

