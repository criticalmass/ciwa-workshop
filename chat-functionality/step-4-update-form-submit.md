# Update form submit handler

In the previous section, we were using the submit handler on our form to update the messages list in our application directly. Now that we have a functioning server in our application, we need to change this handler to submit our chat message data to the server.

We can do this now by calling the newly created "postChatMessageToServer" function we created in the previous step.

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

After this step, you might notice that our message list will no longer be updated automatically, but that's ok, we will fix it soon!

