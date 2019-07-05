# CSS Exercise \(Solution\)

## HEY! Don't look at this until you've attempted the exercise. No cheating 😉





























In your `main` selector, add this rule: 

```css
background-color: #f0f0f0;
```

In your `form` selector, add this rule:

```css
border-radius: 6px;
```

Add the following code to have all the _**odd**_ messages coloured differently:

```css
li:nth-child(odd) {
  background-color: #e3e3e3;
  border-radius: 6px;
}
```

Your final code should look like this:

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

