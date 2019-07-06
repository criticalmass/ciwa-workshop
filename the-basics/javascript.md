# JavaScript

Following our house analogy, **JavaScript** is the language that provides **functionality** \(remember the doorbell?\) to our house! JavaScript is a programming language - meaning it allows us to give the computer instructions in a way that the computer understands. Let's break down some of the fundamental concepts for today.

### Statements

A statement is **one contained** **instruction** for the computer the follow and should always be ended with a semi-colon `;`.

### Variables

A variable is a container that holds information that we can later access. You can think of a variable as a box that contains something. You can open the box to find out what is inside, or even put something else into the box. 

A variable has a **name** and contains a **value**. Think of our previous analogy of a variable as being a box. If you labeled the box as _Toys_ and put a yo-yo inside it, in programming terms, _Toys_ is the **variable name**, and _yo-yo_ is the **value.**

The kind of value that a variable can hold is also called a **data type.** Now, let us look at 3 different data types – **Numbers, Strings, and Booleans.**

In JavaScript, creating a variable can look like this:

`const myAge = 10;`

Here, `myAge` is the variable name, and `10`is the value**.** `const` is how we're telling the browser that we want to create a new variable.

**Extra reading:** What is `const`? ****The word before a variable name is the _**variable type.**_ In this case, we are telling the browser that this variable is constant and cannot be changed. Other ways to declare a variable, aside from using the const keyword, is by using the keywords `var`, or `let`. Don't worry if this isn't making a ton of sense. These concepts take time to understand and the best way to learn is to **do** and then look at the effect your code has. Things will start to fall in place!

### Values / Types

This could be a whole section of the class but we'll cover off a few of the basics that you'll use today. Variables can be assigned different **types** of values. 

* **Number**: This is represented as just a number like the above example: `const myAge = 10;`
* **String**: A string is a _**word**_ or _**sentence**_ that you want assigned to a variable. You must surround your string in quotes as if it were a speaking character in a story you were writing! Example: `const myName = "Lee Mulvey";`
* **Boolean**: A boolean is a bit of a silly word. A boolean can represent two distinct values: `true` or `false`. It's important that you do not surround it with quotes otherwise the computer will think it's a **string**, not a boolean! Example: `const isLeeTeaching = true;`
* **Objects**: An object is way to place variables into a group. Think of this as a larger box that can store any other boxes. For instance, we have have a large box called "Children's items'. This can contain a box titled "Toys" which contains a yo-yo, and a box titled "Bathroom" which contains a toothbrush. All of the properties in an object are separated by a comma and surrounded by curly brackets `{ }`. For example: 

```javascript
const leeObject = {
    myAge: 10,
    myName: 'Lee Mulvey',
    isLeeTeaching: true
};
```

#### What do I do with variables?

Since they capture/refer to a value, you can reference them later. Let's say you have these two variables: `const five = 5;` and `const ten = 10;`, you could later create a NEW variable called `fifteen` and reference your other ones with a little math magic to create it: `const fifteen = five + ten;` . If this sounds silly right now, don't worry about it! Variables will make more sense once we start coding.

Variables can be passed around and assigned to each other, as well as assigned inside of objects. When accessing **nested properties** inside an **object**, you call it with the `objectName` and then a period, and then the `propertyName`. In practice, to pull up my name from the object above, you would call `leeObject.myName` and that would return `Lee Mulvey`. Variables are amazing!

### Functions

A function is set of instructions that you want the program to perform over and over again. 

All programming functions have input\(s\) and output\(s\). The function contains instructions used to create the output from its input. It’s like a cow that eats grass \(the input\) which its body turns into milk which a dairy farmer then milks \(the output\).

For example, programming functions might take as input any number. The function might create output by adding the input times two. Therefore, the output of the function would be the sum of the two inputs.

Before we get into code, let's think of our doorbell again. What are the steps we want to happen while our doorbell is pushed?

1. Doorbell light turn on
2. Send signal to the doorbell speaker to trigger a DING sound

Okay, great! Now what about the instructions when our finger is taken off the doorbell?

1. Shut the doorbell light off
2. Send signal to the doorbell speaker to trigger a DONG sound

Cool! So, we've broken it out into two sets of instructions. It's important to note that these instructions are triggered by two distinct **events**: pushing the doorbell in, and letting go of it. We'll come back to events in a moment! First, let's break the first set of instructions out into actual JavaScript code:

```javascript
function onDoorbellPush() {
    Doorbell.lightOn = true;
    Doorbell.speaker.emit('DING');
};
```

A few things to note here. You'll see that functions are declared a bit differently than variables. You start your function with the word `function`! Next up is the name of the function itself, in this case, `onDoorBellPush`. You'll notice the empty brackets next to the name `()` - this is the spot where input would be placed. Arguments are like variables that can affect the outcome of function. Take for example a function that adds two numbers together:

```javascript
function addNumbers(number1, number2) {
    return number1 + number2;
};
```

In this example, if you call the function with two numbers: `addNumbers(10, 5);` it would return fifteen! The `return` keyword is allows the function to provide the output to the code which called the function. So, taking the above example again, if you wanted to create a new variable called fifteen with the **value** of `15`, you could use that function: `const fifteen = addNumbers(10, 5);`

**Whew!** That's a lot to take in. Let's break down how the instructions for the doorbell when we let go! As a reminder:

1. Shut the doorbell light off
2. Send signal to the doorbell speaker to trigger a DONG sound

Now in code:

```javascript
function onDoorbellRelease() {
    Doorbell.lightOn = false;
    Doorbell.speaker.emit('DONG');
};
```

There we go! Now, we're ready to attach that **function** to our **events.**

### **Events**

Events are a very common concept in programming, especially on the web. Events are triggered on a webpage when you `click` the mouse, `move` your mouse, hit a key on the keyboard \(`keypress`\), and even when you browse on your phone and tap on the screen \(`onTapStart`\). We can allow the browser to respond to events by creating _**Event Handlers**_ - which are special functions that allow us to react to events. 

Events allow us to tie functionality to things we do on the web. Now, let's look at a "real world" event by attaching our doorbell functions to events. An `eventListener` is a function that takes two arguments: the `eventName`, and the action/function to perform when that event occurs!

`House.addEventListener('doorbellPush', onDoorbellPush);`

See? The first argument, `'doorbellPush'` is the NAME of the event we want to listen for \(notice that it's a **STRING!\),** and the second argument `onDoorbellPush` is just a reference to the function we already made! With that in mind, can you guess how we would attach an event on releasing the doorbell?

`House.addEventListener('doorbellRelease', onDoorbellRelease);`

Woo! Those are events. We'll be using the concept of events with **Sockets** coming up. You can think of **sockets** as a way to emit and listen for events between you \(the client/browser\) and a web server. More on that soon!

## Okay, enough chatting: let's write some JavaScript.

I agree. Let's write your first code. Open up your `client/script.js` and type the following code:

```text
alert('Hello from JavaScript!');
```

Click the refresh button above your 'browser':

![](../.gitbook/assets/screen-shot-2019-07-05-at-10.25.07-am.png)

And then you should see the following pop-up. If you don't, wave a mentor down!

![](../.gitbook/assets/screen-shot-2019-07-05-at-10.24.50-am.png)

There! Your first JavaScript code. Now let's start implementing our **chat functionality!**

## Questions? Super confused? 👋🏻 down a mentor and we'll try to clear some of this up. Don't worry if it doesn't ALL make sense. It will start to fall into place as we apply it in our chat app!

