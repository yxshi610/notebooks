# React

## Deploying to GitHub Pages

```shell
npx create-react-app app-name
cd app-name
npm install gh-pages --save-dev
```

`package.json` file:

- At the top level, add a `homepage` property:

```js
//... same level with name and vesion
"homepage": "http://{username}.github.io/{repo-name}"
```

- add a `predeploy` property and a `deploy` property, each having the values shown below:

```js
"scripts": {
 //...
 "predeploy": "npm run build",
 "deploy": "gh-pages -d build"
}
```

```shell
git init
git remote add origin https://github.com/yxshi610/characters.git
npm run deploy    // accessible through URL
```

- optionally commit to "master" branch

```shell
git add .
git commit -m "Create a React app and publish it to GitHub Pages"
git push origin master
```

the `master` branch held the source code, and the `gh-pages` branch held the *built* app code.

Problem: GitHub Pages doesn't natively support single page apps. When there is a fresh page load for a url like `example.tld/foo`, where `/foo` is a frontend route, the GitHub Pages server returns 404 because it knows nothing of `/foo`.

Solution: [GitHub - rafgraph/spa-github-pages: Host single page apps with GitHub Pages](https://github.com/rafgraph/spa-github-pages)

change to Surge:

```shell
npm run build
cd build
cp index.html 200.html
surge
```

## Front End Development Libraries

https://www.freecodecamp.org/learn/front-end-development-libraries/

### Bootstrap

front end framework, a mobile-first approach, includes pre-built CSS styles and classes, plus some JavaScript functionality.

You can add Bootstrap to any app by adding the following code to the top of your HTML:

```html
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous"/>
```

```html
<div class="container-fluid"></div>
<p>image exactly the width of phone's screen</p>
<img class="img-responsive">
<h2 class="red-text text-center">CatPhotoApp</h2>
<p>btn-block make it fill horizontal</p>
<button class="btn btn-default btn-block">Like</button>
```

Bootstrap uses a responsive 12-column grid system, which makes it easy to put elements into rows and specify each element's relative width. Most of Bootstrap's classes can be applied to a `div` element.

Bootstrap has different column width attributes that it uses depending on how wide the user's screen is. For example, phones have narrow screens, and laptops have wider screens.

Take for example Bootstrap's `col-md-*` class. Here, `md` means medium, and `*` is a number specifying how many columns wide the element should be. In this case, the column width of an element on a medium-sized screen, such as a laptop, is being specified.

In the Cat Photo App that we're building, we'll use `col-xs-*`, where `xs` means extra small (like an extra-small mobile phone screen), and `*` is the number of columns specifying how many columns wide the element should be.

Put the `Like`, `Info` and `Delete` buttons side-by-side by nesting all three of them within one `<div class="row">` element, then each of them within a `<div class="col-xs-4">` element.

The `row` class is applied to a `div`, and the buttons themselves can be nested within it.

![Screen Shot 2022-01-01 at 21.36.58.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/01/01-21-37-02-Screen%20Shot%202022-01-01%20at%2021.36.58.png)

By using the inline `span` element, you can put several elements on the same line, and even style different parts of the same line differently.

#### Font Awesome

a convenient library of icons.

You can include Font Awesome in any app by adding the following code to the top of your HTML:

```html
<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.8.1/css/all.css" integrity="sha384-50oBUHEmvpQ+1lW4y57PTFmhCaXp0ML5d60M1M7uH2+nqUivzIebhndOJK28anvf" crossorigin="anonymous">
```

![Screen Shot 2022-01-01 at 21.55.12.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/01/01-21-55-14-Screen%20Shot%202022-01-01%20at%2021.55.12.png)

Bootstrap has a class called `well` that can create a visual sense of depth for your columns.

![Screen Shot 2022-01-01 at 22.05.03.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/01/01-22-05-07-Screen%20Shot%202022-01-01%20at%2022.05.03.png)

### jQuery

code you put inside this `function` will run as soon as your browser has loaded your page. without your `document ready function`, your code may run before your HTML is rendered, which would cause bugs.

```html
<script>
$(document).ready(function() {

});
</script>
```

All jQuery functions start with a `$`, usually referred to as a dollar sign operator, or as bling. jQuery often selects an HTML element with a selector, then does something to that element.

For example, let's make all of your `button` elements bounce. jQuery library and the Animate.css library. Just add this code inside your document ready function.

```js
$("button").addClass("animated bounce");
```

jQuery has a function called `.css()` that allows you to change the CSS of an element.

Here's how we would change its color to blue:

```js
$("#target1").css("color", "blue");
```

This is slightly different from a normal CSS declaration, because the CSS property and its value are in quotes, and separated with a comma instead of a colon.

jQuery has a function called `.prop()` that allows you to adjust the properties of elements.

Here's how you would disable all buttons:

```js
$("button").prop("disabled", true);
```

jQuery has a function called `.html()` that lets you add HTML tags and text within an element. Any content previously within the element will be completely replaced with the content you provide using this function.

Here's how you would rewrite and emphasize the text of our heading:

```js
$("h3").html("<em>jQuery Playground</em>");
```

jQuery also has a similar function called `.text()` that only alters text without adding tags. In other words.

jQuery has a function called `.remove()` that will remove an HTML element entirely

jQuery has a function called `appendTo()` that allows you to select HTML elements and append them to another element.

For example, if we wanted to move `target4` from our right well to our left well, we would use:

```js
$("#target4").appendTo("#left-well");
```

jQuery has a function called `clone()` that makes a copy of an element.

For example, if we wanted to copy `target2` from our `left-well` to our `right-well`, we would use:

```js
$("#target2").clone().appendTo("#right-well");
```

Here's an example of how you would use the `parent()` function if you wanted to give the parent element of the `left-well` element a background color of blue:

```js
$("#left-well").parent().css("background-color", "blue")
```

Here's an example of how you would use the `children()` function to give the children of your `left-well` element the color `blue`:

```js
$("#left-well").children().css("color", "blue")
```

jQuery uses CSS Selectors to target elements. The `target:nth-child(n)` CSS selector allows you to select all the nth elements with the target class or element type.

Here's how you would give the third element in each well the bounce class:

```js
$(".target:nth-child(3)").addClass("animated bounce");
```

You can also target elements based on their positions using `:odd` or `:even` selectors.

Note that jQuery is zero-indexed which means the first element in a selection has a position of 0.

Also with body:

```html
$("body").addClass("animated hinge");
```

## Sass

One feature of Sass that's different than CSS is it uses variables. They are declared and set to store data, similar to JavaScript. In Sass, variables start with a `$` followed by the variable name.

Here are a couple examples:

```scss
$main-fonts: Arial, sans-serif;
$headings-color: green;
```

And to use the variables:

```scss
h1 {
  font-family: $main-fonts;
  color: $headings-color;
}
```

### CSS nesting

![Screen Shot 2022-01-01 at 22.45.41.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/01/01-22-45-43-Screen%20Shot%202022-01-01%20at%2022.45.41.png)

In Sass, a mixin is a group of CSS declarations that can be reused throughout the style sheet.

Newer CSS features take time before they are fully adopted and ready to use in all browsers. As features are added to browsers, CSS rules using them may need vendor prefixes. Consider `box-shadow`:

```scss
div {
  -webkit-box-shadow: 0px 0px 4px #fff;
  -moz-box-shadow: 0px 0px 4px #fff;
  -ms-box-shadow: 0px 0px 4px #fff;
  box-shadow: 0px 0px 4px #fff;
}
```

Mixins are like functions for CSS. Here is how to write one:

```scss
@mixin box-shadow($x, $y, $blur, $c){ 
  -webkit-box-shadow: $x $y $blur $c;
  -moz-box-shadow: $x $y $blur $c;
  -ms-box-shadow: $x $y $blur $c;
  box-shadow: $x $y $blur $c;
}
```

Now any time a `box-shadow` rule is needed, only a single line calling the mixin replaces having to type all the vendor prefixes. A mixin is called with the `@include` directive:

```scss
div {
  @include box-shadow(0px, 0px, 4px, #fff);
}
```

The `@if` directive in Sass is useful to test for a specific case - it works just like the `if` statement in JavaScript.

```scss
@mixin make-bold($bool) {
  @if $bool == true {
    font-weight: bold;
  }
}
```

And just like in JavaScript, `@else if` and `@else` test for more conditions:

```scss
@mixin text-effect($val) {
  @if $val == danger {
    color: red;
  }
  @else if $val == alert {
    color: yellow;
  }
  @else if $val == success {
    color: green;
  }
  @else {
    color: black;
  }
}
```

`@for` is used in two ways: "start through end" or "start to end". The main difference is that the "start **to** end" *excludes* the end number as part of the count, and "start **through** end" *includes* the end number as part of the count.

Here's a start **through** end example:

```scss
@for $i from 1 through 12 {
  .col-#{$i} { width: 100%/12 * $i; }
}
```

The `#{$i}` part is the syntax to combine a variable (`i`) with text to make a string. When the Sass file is converted to CSS, it looks like this:

```scss
.col-1 {
  width: 8.33333%;
}

.col-2 {
  width: 16.66667%;
}

...

.col-12 {
  width: 100%;
}
```

This is a powerful way to create a grid layout. Now you have twelve options for column widths available as CSS classes.

Sass also offers the `@each` directive which loops over each item in a list or map. On each iteration, the variable gets assigned to the current value from the list or map.

```scss
@each $color in blue, red, green {
  .#{$color}-text {color: $color;}
}
```

A map has slightly different syntax. Here's an example:

```scss
$colors: (color1: blue, color2: red, color3: green);

@each $key, $color in $colors {
  .#{$color}-text {color: $color;}
}
```

Note that the `$key` variable is needed to reference the keys in the map. Otherwise, the compiled CSS would have `color1`, `color2`... in it. Both of the above code examples are converted into the following CSS:

```scss
.blue-text {
  color: blue;
}

.red-text {
  color: red;
}

.green-text {
  color: green;
}
```

The `@for` challenge gave an example to create a simple grid system. This can also work with `@while`.

```scss
$x: 1;
@while $x < 13 {
  .col-#{$x} { width: 100%/12 * $x;}
  $x: $x + 1;
}
```

First, define a variable `$x` and set it to 1. Next, use the `@while` directive to create the grid system *while* `$x` is less than 13. After setting the CSS rule for `width`, `$x` is incremented by 1 to avoid an infinite loop.

Partials in Sass are separate files that hold segments of CSS code. These are imported and used in other Sass files. This is a great way to group similar code into a module to keep it organized.

Names for partials start with the underscore (`_`) character, which tells Sass it is a small segment of CSS and not to convert it into a CSS file. Also, Sass files end with the `.scss` file extension. To bring the code in the partial into another Sass file, use the `@import` directive.

For example, if all your mixins are saved in a partial named "_mixins.scss", and they are needed in the "main.scss" file, this is how to use them in the main file:

```scss
@import 'mixins'
```

Note that the underscore and file extension are not needed in the `import` statement - Sass understands it is a partial. Once a partial is imported into a file, all variables, mixins, and other code are available to use.

Sass has a feature called `extend` that makes it easy to borrow the CSS rules from one element and build upon them in another.

For example, the below block of CSS rules style a `.panel` class. It has a `background-color`, `height` and `border`.

```scss
.panel{
  background-color: red;
  height: 70px;
  border: 2px solid green;
}
```

Now you want another panel called `.big-panel`. It has the same base properties as `.panel`, but also needs a `width` and `font-size`. The `extend` directive is a simple way to reuse the rules written for one element, then add more for another:

```scss
.big-panel{
  @extend .panel;
  width: 150px;
  font-size: 2em;
}
```

The `.big-panel` will have the same properties as `.panel` in addition to the new styles.

## React

React is an Open Source view library created and maintained by Facebook. React uses a syntax extension of JavaScript called JSX that allows you to write HTML directly within JavaScript. 

For instance, because JSX is a syntactic extension of JavaScript, you can actually write JavaScript directly within JSX. To do this, you simply include the code you want to be treated as JavaScript within curly braces: `{ 'this is treated as JavaScript code' }`. 

However, because JSX is not valid JavaScript, JSX code must be compiled into JavaScript. The transpiler Babel is a popular tool for this process. 

It's worth noting that under the hood the challenges are calling `ReactDOM.render(JSX, document.getElementById('root'))`. This function call is what places your JSX into React's own lightweight representation of the DOM. React then uses snapshots of its own DOM to optimize updating only specific parts of the actual DOM. => const JSX = <tag></tag>

![Screen Shot 2022-01-01 at 23.06.27.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/01/01-23-06-30-Screen%20Shot%202022-01-01%20at%2023.06.27.png)

With React, we can render this JSX directly to the HTML DOM using React's rendering API known as ReactDOM.

ReactDOM offers a simple method to render React elements to the DOM which looks like this: `ReactDOM.render(componentToRender, targetNode)`, where the first argument is the React element or component that you want to render, and the second argument is the DOM node that you want to render the component to.

As you would expect, `ReactDOM.render()` must be called after the JSX element declarations, just like how you must declare variables before using them.

![Screen Shot 2022-01-01 at 23.09.29.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/01/01-23-09-31-Screen%20Shot%202022-01-01%20at%2023.09.29.png)

One key difference in JSX is that you can no longer use the word `class` to define HTML classes. This is because `class` is a reserved word in JavaScript. Instead, JSX uses `className`. In fact, the naming convention for all HTML attributes and event references in JSX become camelCase. For example, a click event in JSX is `onClick`, instead of `onclick`. Likewise, `onchange` becomes `onChange`. While this is a subtle difference, it is an important one to keep in mind moving forward.

Any JSX element can be written with a self-closing tag, and every element must be closed. The line-break tag, for example, must always be written as `<br />` in order to be valid JSX that can be transpiled. A `<div>`, on the other hand, can be written as `<div />` or `<div></div>`. The difference is that in the first syntax version there is no way to include anything in the `<div />`. 

### Component

1. Defining a component creates a *stateless functional component*. one that can receive data and render it, but does not manage or track changes to that data. returns either JSX or `null`. One important thing to note is that React requires your function name to begin with a capital letter. Here's an example of a stateless functional component that assigns an HTML class in JSX:
   
   ```jsx
   const DemoComponent = function() {
     return (
       <div className='customClass' />
     );
   };
   ```

2. with the ES6 `class` syntax. In the following example, `Kitten` extends `React.Component`:
   
   ```jsx
   class Kitten extends React.Component {
     constructor(props) {
       super(props);
     }
   
     render() {
       return (
         <h1>Hi</h1>
       );
     }
   }
   ```
   
   This creates an ES6 class `Kitten` which extends the `React.Component` class. So the `Kitten` class now has access to many useful React features, such as local state and lifecycle hooks. Also notice the `Kitten` class has a `constructor` defined within it that calls `super()`. It uses `super()` to call the constructor of the parent class, in this case `React.Component`. The constructor is a special method used during the initialization of objects that are created with the `class` keyword. It is best practice to call a component's `constructor` with `super`, and pass `props` to both. This makes sure the component is initialized properly. 

To compose these components together, you could create an `App` *parent* component which renders each of these three components as *children*. To render a component as a child in a React component, you include the component name written as a custom HTML tag in the JSX. For example, in the `render` method you could write:

```jsx
return (
 <App>
  <Navbar />
  <Dashboard />
  <Footer />
 </App>
)
```

```html
{/* very common to use arrow function*/}
const ChildComponent = () => {
  return (
    <div>
      <p>I am the child</p>
    </div>
  );
};
```

React components are passed into `ReactDOM.render()` a little differently than JSX elements. For JSX elements, you pass in the name of the element that you want to render. However, for React components, you need to use the same syntax as if you were rendering a nested component, for example `ReactDOM.render(<ComponentToRender />, targetNode)`. You use this syntax for both ES6 class components and functional components.

```javascript
ReactDOM.render(<TypesOfFood />, document.getElementById("challenge-node"))
```

a typical React component is an ES6 `class` which extends `React.Component`. It has a render method that returns HTML (from JSX) or `null`.

**Pass Props to a Stateless Functional Component**

```jsx
<App>
  <Welcome user='Mark' />
</App>

const Welcome = (props) => <h1>Hello, {props.user}!</h1>
```

Note that for `prop` values to be evaluated as JavaScript, they must be enclosed in curly brackets, for instance `date={Date()}`.

`MyComponent.defaultProps = { location: 'San Francisco' }`, you have defined a location prop that's set to the string `San Francisco`, unless you specify otherwise. React assigns default props if props are undefined.

You can set `propTypes` on your component to require the data to be of type `array`. 

```js
MyComponent.propTypes = { handleClick: PropTypes.func.isRequired }
```

In the example above, the `PropTypes.func` part checks that `handleClick` is a function. Adding `isRequired` tells React that `handleClick` is a required property for that component.

**Note:** As of React v15.5.0, `PropTypes` is imported independently from React, like this: `import PropTypes from 'prop-types';`

#### ES6 class component

Anytime you refer to a class component within itself, you use the `this` keyword. To access props within a class component, you preface the code that you use to access it with `this`. For example, if an ES6 class component has a prop called `data`, you write `{this.props.data}` in JSX.

A *stateless functional component* is any function you write which accepts props and returns JSX. A *stateless component*, on the other hand, is a class that extends `React.Component`, but does not use internal state. a *stateful component* is a class component that does maintain its own internal state. You may see stateful components referred to simply as components or React components. A common pattern is to try to **minimize statefulness** and to create stateless functional components wherever possible. This helps contain your state management to a specific area of your application.

#### Stateful Component

You create state in a React component by declaring a `state` property on the component class in its `constructor`. This initializes the component with `state` when it is created. The `state` property must be set to a JavaScript `object`. Declaring it looks like this:

```jsx
this.state = {

}
```

You have access to the `state` object throughout the life of your component. You can update it, render it in your UI, and pass it as props to child components. 
