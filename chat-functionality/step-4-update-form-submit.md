# Update form submit handler

{% code-tabs %}
{% code-tabs-item title="src/client/script.js" %}
```javascript
form.addEventListener("submit", function(event) {
  event.preventDefault();

  // extract the name and message data from the inputs and pass them on.
  const name = nameInput.value;
  const msg = messageInput.value;

  postChatMessageToServer(name, msg);  
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

