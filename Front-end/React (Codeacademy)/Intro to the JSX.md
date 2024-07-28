# Introduction to JSX

## Why React?

React.js is a JavaScript library developed by engineers at Facebook. Here are just a few reasons why people choose to program with React:

- **React is fast**: Apps made in React can handle complex updates and still feel quick and responsive.
- **React is modular**: Instead of writing large, dense files of code, you can write many smaller, reusable files. React’s modularity can be a beautiful solution to JavaScript’s maintainability problems.
- **React is scalable**: Large programs that display a lot of changing data are where React performs best.
- **React is flexible**: You can use React for interesting projects that have nothing to do with making a web app. People are still figuring out React’s potential. There’s room to explore.
- **React is popular**: While this reason has admittedly little to do with React’s quality, the truth is that understanding React will make you more employable.

### What’s the difference between React and jQuery?

The main difference between React and jQuery is that jQuery is used for DOM manipulation, like modifying existing elements, and interacts with the DOM directly, while React is a library for rendering and building user interfaces and interacts with what’s called the “virtual DOM”.

## Hello World

```javascript
const h1 = <h1>Hello world</h1>;
```

## Cheatsheet

### Nested JSX Elements

A JSX expression must have exactly one outermost element. In the code below, the `<a>` tag is the outermost element.

```javascript
const myClasses = (
  <a href="https://www.codecademy.com">
    <h1>Sign Up!</h1>
  </a>
);
```

### JSX Syntax and JavaScript

JSX is a syntax extension of JavaScript. It’s used to create DOM elements which are then rendered in the React DOM. A JavaScript file containing JSX will have to be compiled before it reaches a web browser.

```javascript
import React from 'react';
import { createRoot } from 'react-dom/client';
 
const container = document.getElementById('app');
const root = createRoot(container);
root.render(<h1>Render me!</h1>);
```

### Multiline JSX Expression

A JSX expression that spans multiple lines must be wrapped in parentheses.

```javascript
const myList = (
  <ul>
    <li>item 1</li>
    <li>item 2</li>
    <li>item 3</li>
  </ul>
);
```

### JSX Syntax and HTML

JSX syntax closely resembles HTML. They both use angle bracket opening and closing tags (`<h1>` and `</h1>`).

```javascript
const title = <h1>Welcome all!</h1>
```

### JSX Attributes

JSX attributes resemble HTML attributes. Inside the opening tag of the `<h1>` JSX element, there is an `id` attribute with the value "example".

```javascript
const example = <h1 id="example">JSX Attributes</h1>;
```

### ReactDOM JavaScript Library

The `react-dom/client` library contains the `createRoot()` method, which creates a React root at the HTML element used as an argument. The React root renders JSX elements to the DOM.

```javascript
import React from 'react';
import { createRoot } from 'react-dom/client';

const container = document.getElementById('app');
const root = createRoot(container);

root.render(<h1>This is an example.</h1>);
```

### Embedding JavaScript in JSX

JavaScript expressions may be embedded within JSX expressions. The embedded JavaScript expression must be wrapped in curly braces.

```javascript
let expr = <h1>{10 * 10}</h1>;
// above will be rendered as <h1>100</h1>
```

### The Virtual DOM

React uses the Virtual DOM, which can be thought of as a blueprint of the DOM. When any changes are made to React elements, the Virtual DOM is updated. The Virtual DOM finds the differences between it and the DOM and re-renders only the elements in the DOM that changed. This makes the Virtual DOM faster and more efficient than updating the entire DOM.

### JSX className

In JSX, you can’t use the word `class`. You have to use `className` instead. This is because JSX gets translated into JavaScript, and `class` is a reserved word in JavaScript.

```javascript
// When rendered, this JSX expression...
const heading = <h1 className="large-heading">Codecademy</h1>;

// ...will be rendered as this HTML
<h1 class="large-heading">Codecademy</h1>
```

### JSX and Conditionals

In JSX, `&&` is commonly used to render an element based on a boolean condition. If the expression on the left of the `&&` evaluates as true, then the JSX on the right of the `&&` will be rendered.

```javascript
// All of the list items will display if
// baby is false and age is above 25
const tasty = (
  <ul>
    <li>Applesauce</li>
    { !baby && <li>Pizza</li> }
    { age > 15 && <li>Brussels Sprouts</li> }
    { age > 20 && <li>Oysters</li> }
    { age > 25 && <li>Grappa</li> }
  </ul>
);
```

### JSX Conditionals

JSX does not support `if/else` syntax in embedded JavaScript. There are three ways to express conditionals for use with JSX elements:
1. A ternary within curly braces in JSX
2. An `if` statement outside a JSX element
3. The `&&` operator

```javascript
// Using ternary operator
const headline = (
  <h1>
    { age >= drinkingAge ? 'Buy Drink' : 'Do Teen Stuff' }
  </h1>
);

// Using if/else outside of JSX 
let text;

if (age >= drinkingAge) { text = 'Buy Drink' }
else { text = 'Do Teen Stuff' }

const headline = <h1>{ text }</h1>

// Using && operator. Renders as empty div if length is 0
const unreadMessages = [ 'hello?', 'remember me!'];

const update = (
  <div>
    {unreadMessages.length > 0 &&
      <h1>
        You have {unreadMessages.length} unread messages.
      </h1>
    }
  </div>
);
```

### Embedding JavaScript Code in JSX

Any text between JSX tags will be read as text content, not as JavaScript. In order for the text to be read as JavaScript, the code must be embedded between curly braces `{ }`.

```javascript
<p>{ Math.random() }</p>

// Above JSX will be rendered something like this: 
<p>0.88</p>
```

### JSX Element Event Listeners

In JSX, event listeners are specified as attributes on elements. An event listener attribute’s name should be written in camelCase, such as `onClick` for an `onclick` event, and `onMouseOver` for an `onmouseover` event. 

```javascript
// Basic example
const handleClick = () => alert("Hello world!");

const button = <button onClick={handleClick}>Click here</button>;

// Example with event parameter
const handleMouseOver = (event) => event.target.style.color = 'purple';

const button2 = <div onMouseOver={handleMouseOver}>Drag here to change color</div>;
```

### Setting JSX Attribute Values with Embedded JavaScript

When writing JSX, it’s common to set attributes using embedded JavaScript variables.

```javascript
const introClass = "introduction";
const introParagraph = <p className={introClass}>Hello world</p>;
```

### JSX `.map()` Method

The array method `map()` comes up often in React. If you want to create a list of JSX elements from a given array, then `map()` over each element in the array, returning a list item for each one.

```javascript
const strings = ['Home', 'Shop', 'About Me'];

const listItems = strings.map(string => <li>{string}</li>);

<ul>{listItems}</ul>
```

### JSX Empty Elements Syntax

In JSX, empty elements must explicitly be closed using a closing slash at the end of their tag: `<tagName />`.

```javascript
<br />
<img src="example_url" />
```

### **`React.createElement()`** Creates Virtual DOM Elements

The `React.createElement()` function is used by React to actually create virtual DOM elements from JSX. When the JSX is compiled, it is replaced by calls to `React.createElement()`.

```javascript
// The following JSX...
const h1 = <h1 className="header">Hello world</h1>;

// ...will be compiled to the following:
const h1 = React.createElement(
  'h1',
  {
    className: 'header',
  },
  'Hello world'
);
```

### JSX `key` Attribute

In JSX elements in a list, the `key` attribute is used to uniquely identify individual elements. It is declared like any other attribute.

```javascript
<ul>
  <li key="key1">One</li>
  <li key="key2">Two</li>
  <li key="key3">Three</li>
  <li key="key4">Four</li>
</ul>
```

## Can We Create HTML in a JS File?

We absolutely can! In a JavaScript file, we can use DOM methods and properties to create (or insert, update, delete

, etc.) HTML elements stored as strings in a JS variable (or as a string passed to a DOM method/property).

However, when using the JavaScript library React, we will normally use JSX to create HTML elements inside a JavaScript file, which uses different syntax than we would use if we were using DOM methods/properties.

## Framework vs Library

### Frameworks
A framework is a foundational structure on which software applications can be built. It provides generic functionality that can be selectively changed by user-written code, making the development process easier and faster. 

**Frameworks typically include:**
- Pre-defined Code: A collection of pre-written code modules that developers can use directly.
- Guidelines and Standards: Rules and standards that help maintain consistency across projects.
- Reusability: Code that can be reused across various parts of the application or in different projects.
- Inversion of Control (IoC): The framework controls the flow of the application, calling user-written code when needed.

**Examples of Frameworks:**
- Web Development: Django (Python), Ruby on Rails (Ruby), Spring (Java)
- Mobile Development: React Native, Flutter
- Desktop Applications: .NET Framework, Qt
- Game Development: Unity, Unreal Engine

### Libraries
A library is a collection of pre-written code that developers can use to optimize tasks. Libraries are typically more focused and provide specific functionality rather than a full-stack approach like frameworks.

**They offer:**
- Reusable Functions: Functions and procedures that can be utilized to perform tasks.
- Utility: Tools to perform specific operations like data manipulation, network calls, etc.
- Flexibility: Developers call the library functions whenever they need them, maintaining control over the application flow.

**Examples of Libraries:**
- Data Manipulation: Pandas (Python), NumPy (Python)
- Web Development: jQuery (JavaScript), Axios (JavaScript)
- Machine Learning: TensorFlow, Scikit-learn
- Networking: Requests (Python), Retrofit (Java)

## What is JSX?

JSX is a syntax extension for JavaScript. It was written to be used with React. JSX code looks a lot like HTML.

### What Does “Syntax Extension” Mean?

In this case, it means that JSX is not valid JavaScript. Web browsers can’t read it! If a JavaScript file contains JSX code, then that file will have to be compiled. This means that before the file reaches a web browser, a JSX compiler will translate any JSX into regular JavaScript.

Codecademy’s servers already have a JSX compiler installed, so you don’t have to worry about that for now. Eventually, we’ll walk through how to set up a JSX compiler on your personal computer.

### JSX Elements

A basic unit of JSX is called a JSX element.

```javascript
<h1>Hello world</h1>
```

This JSX element looks exactly like HTML! The only noticeable difference is that you would find it in a JavaScript file, instead of in an HTML file.

### Is a JSX Element the Same Thing as an HTML Element?

A JSX element is not the same thing as an HTML element - a JSX element is a description of what we want to see on our page.

## JSX Elements and Their Surroundings

JSX elements are treated as JavaScript expressions. They can go anywhere that JavaScript expressions can go. This means that a JSX element can be saved in a variable, passed to a function, stored in an object or array… you name it.

```javascript
const navBar = <nav>I am a nav bar</nav>;
```

Here’s an example of several JSX elements being stored in an object:

```javascript
const myTeam = {
  center: <li>Benzo Walli</li>,
  powerForward: <li>Rasha Loa</li>,
  smallForward: <li>Tayshaun Dasmoto</li>,
  shootingGuard: <li>Colmar Cumberbatch</li>,
  pointGuard: <li>Femi Billon</li>
};
```

### Attributes in JSX

JSX elements can have attributes, just like how HTML elements can.

```javascript
<a href='http://www.example.com'>Welcome to the Web</a>;

const title = <h1 id='title'>Introduction to React.js: Part I</h1>; 
```

### Nested JSX

You can nest JSX elements inside of other JSX elements, just like in HTML.

```javascript
<a href="https://www.example.com">
  <h1>Click me!</h1>
</a>
```

Nested JSX expressions can be saved as variables, passed to functions, etc., just like non-nested JSX expressions can!

```javascript
const theExample = (
  <a href="https://www.example.com">
    <h1>Click me!</h1>
  </a>
);
```

### Why Do We Need Parentheses Around Multi-line JSX Expressions?

We want to use parentheses around multi-line JSX expressions to make sure we are avoiding JavaScript’s automatic semicolon insertion which will add semicolons (based on rules given by the JavaScript specifications) to terminate statements when we don’t necessarily want/expect that behavior in a JSX expression.

### JSX Outer Elements

A JSX expression must have exactly one outermost element.

```javascript
const paragraphs = (
  <div id="i-am-the-outermost-element">
    <p>I am a paragraph.</p>
    <p>I, too, am a paragraph.</p>
  </div>
);
```

This code will not work:

```javascript
const paragraphs = (
  <p>I am a paragraph.</p> 
  <p>I, too, am a paragraph.</p>
);
```

The first opening tag and the final closing tag of a JSX expression must belong to the same JSX element!

## Rendering JSX

### What’s the Difference Between React and ReactDOM?

React is a JavaScript library for building User Interfaces and ReactDOM is the JavaScript library that allows React to interact with the DOM.

```javascript
const container = document.getElementById('app')
```

This line:

- Uses the document object which represents our web page.
- Uses the `getElementById()` method of document to get the Element object representing the HTML element with the passed-in id (app).
- Stores the element in `container`.

```javascript
const root = createRoot(container)
```

We use `createRoot()` from the `react-dom/client` library, which creates a React root from `container` and stores it in `root`. `root` can be used to render a JSX expression. This is the “where to place the content” part of React rendering.

```javascript
root.render(<h1>Hello world</h1>)
```

Uses the `render()` method of `root` to render the content passed in as an argument. Here we pass an `<h1>` element, which displays "Hello world". This is the “what content to render” part of React rendering.

### Is the ReactDOM Library Built into the React Library?

ReactDOM is not included in the generic React library. When we include the generic React library as a `<script>` tag in our HTML we will also have to include a `<script>` tag for the ReactDOM library if we want to use ReactDOM.

### Passing a Variable to `render()`

In the previous exercise, we saw how we can create a React root using `createRoot()` and use its `render()` method to render JSX.

The `render()` method’s argument doesn’t need to be JSX, but it should evaluate to a JSX expression. The argument could also be a variable, so long as that variable evaluates to a JSX expression.

```javascript
const toDoList = (
  <ol>
    <li>Learn React</li>
    <li>Become a Developer</li>
  </ol>
);

const container = document.getElementById('app');
const root = createRoot(container);
root.render(toDoList);
```

### Why Use a Variable as the First Argument in `ReactDOM.render()` Instead of a JSX Expression?

Readability! If we are trying to pass a multi-line JSX expression to `ReactDOM.render()` we may find our JSX code is difficult to read and understand. However, if our JSX expression is a single line, we may want to pass the expression (instead of a variable storing the expression) to `ReactDOM.render()`.

## The Virtual DOM

One special thing about a React root’s `render()` method is that it only updates DOM elements that have changed.

```javascript
const hello = <h1>Hello world</h1>;

// This will add "Hello world" to the screen:
root.render(hello, document.getElementById('app'));

// This won't do anything at all:
root.render(hello, document.getElementById('app'));
```

Only updating the necessary DOM elements is a large part of what makes React so successful. This is accomplished using React’s virtual DOM.

### Why is DOM Manipulation So Slow?

When there is a change to an element in the DOM, the DOM has to re-render the element and all of the element’s children to the DOM, making DOM manipulation very slow in comparison to the Virtual DOM.

## Review

Congratulations! You’ve learned to create and render JSX elements! This is the first step toward becoming fluent in React.

In this lesson, we learned that:

- React is a modular, scalable, flexible, and popular front-end framework.
- JSX is a syntax extension for JavaScript which allows us to treat HTML as expressions. They can be stored in variables, objects, arrays, and more!
- JSX elements can have attributes and be nested within each other, just like in HTML.
- JSX must have exactly one outer element, and other elements can be nested inside.
- `createRoot()` from `react-dom/client` can be used to create a React root at the specified DOM element.
-

 A React root’s `render()` method can be used to render JSX on the screen.
- A React root’s `render()` method only updates DOM elements that have changed using the virtual DOM.

### Do I Have to Use JSX to Use React?

No, we do not have to use JSX to use React. Not using JSX may be preferred when we don’t want to set up compilation for our React application.
