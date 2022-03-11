# JavaScript

https://javascript.info/

## Intro

Today, JavaScript can execute not only in the browser, but also on the server, or actually on any device that has a special program called the JavaScript engine.

The browser has an embedded engine sometimes called a “JavaScript virtual machine”.

Different engines have different “codenames”. For example: V8 in Chrome, Opera and Edge.

There are many languages that get “transpiled” to JavaScript and provide certain features. e.g. TypeScript & kotlin.

## Fundamentals

### script

JavaScript programs can be inserted almost anywhere into an HTML document using the `<script>` tag.

The `<script>` tag contains JavaScript code which is automatically executed when the browser processes the tag.

If we have a lot of JavaScript code, we can put it into a separate file. Script files are attached to HTML with the `src` attribute:

`<script src="./script.js"></script>`

As a rule, only the simplest scripts are put into HTML. More complex ones reside in separate files.

The benefit of a separate file is that the browser will download it and store it in its cache.

Other pages that reference the same script will take it from the cache instead of downloading it.

- *it is possible* to leave out semicolons most of the time. But it’s safer – especially for a beginner – to use them.

- comment: // + /**/

### "use strict"

2009 when ECMAScript 5 (ES5) appeared. It added new features to the language and modified some of the existing ones. To keep the old code working, most such modifications are off by default. You need to explicitly enable them with a special directive: `"use strict"`. and the script works as the "modern" way.

```javascript
"use strict";
// this code works the modern way
...
```

### Variables

```javascript
let hello = 'Hello world!';
let message;
// **copy** 'Hello world' from hello into message
message = hello;
// now two variables hold the same data
alert(hello); // Hello world!
alert(message); // Hello world!
```

- To declare a constant (unchanging) variable, use `const` instead of `let`. They cannot be reassigned. There is a widespread practice to use constants as aliases for difficult-to-remember values that are known prior to execution. `const COLOR_RED = "#F00";`

### Data types

- JavaScript, are called “dynamically typed”, meaning that there exist data types, but variables are not bound to any of them.

- Besides regular numbers, there are so-called “special numeric values” which also belong to this data type: `Infinity`, `-Infinity` and `NaN`.

- Backticks are “extended functionality” quotes. They allow us to embed variables and expressions into a string by wrapping them in `${…}`, for example:
  
  ```javascript
  let name = "John";
  // embed a variable
  alert( `Hello, ${name}!` ); // Hello, John!
  // embed an expression
  alert( `the result is ${1 + 2}` ); // the result is 3
  ```

- the `typeof` operator: `typeof "foo" //"string"`

### Interaction

#### alert

It shows a message and waits for the user to press “OK”. 

`alert("Hello");`

#### prompt

```javascript
result = prompt(title, [default]);
let age = prompt('How old are you?', 100);
```

It shows a modal window with a text message, an input field for the visitor, and the buttons OK/Cancel.

`title`The text to show the visitor.

`default`the initial value for the input field. square brackets [] mean optional. 

#### confirm

```javascript
result = confirm(question);
```

The function `confirm` shows a modal window with a `question` and two buttons: OK and Cancel.

The result is `true` if OK is pressed and `false` otherwise.
