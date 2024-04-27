# ES5

## Contents
- [Prevent Object Mutation](#prevent-object-mutation)
- [Anonymous Functions vs Arrow Functions](#anonymous-functions-vs-arrow-functions)
  - [Params](#params)
  - [Default Params](#default-params)
  - [Rest Param](#rest-param)
- [Spread Operator](#spread-operator)
- [Destructuring](#destructuring)
  - [Extract](#extract)
  - [Assign](#assign)
- [Declarative Functions](#declarative-functions)
- [Object Property Shorthand](#object-property-shorthand)
- [Constructor](#constructor)
- [Getters and Setters](#getters-and-setters)
- [Module Script](#module-script)
  - [Export module](#export-module)
  - [Import module](#import-module)
  - [Import everything from the file](#import-everything-from-the-file)
  - [Export Default](#export-default)
  - [Import Default](#import-default)
- [Promise](#promise)

## Prevent Object Mutation
```
let obj = {
  name:"FreeCodeCamp",
  review:"Awesome"
};
Object.freeze(obj);
obj.review = "bad"; // Error
obj.newProp = "Test"; // Error
console.log(obj); 
```

## Anonymous Functions vs Arrow Functions
ES5 declaration
```
const myFunc = function() {
  const myVar = "value";
  return myVar;
}
```
ES6 declaration
```
const myFunc = () => {
  const myVar = "value";
  return myVar;
}
```

### Params
```
const doubler = (item) => item * 2;
const multiplier = (item, multi) => item * multi;
```

### Default Params
```
const greeting = (name = "Anonymous") => "Hello " + name;
```

### Rest Param
In order to help us create more flexible functions, ES6 introduces the **rest parameter** for function parameters. 
With the rest parameter, you can create functions that take a variable number of arguments. 
These arguments are stored in an array that can be accessed later from inside the function.
```
function howMany(...args) {
  return "You have passed " + args.length + " arguments.";
}
console.log(howMany(0, 1, 2));
console.log(howMany("string", null, [1, 2, 3], { }));
```

## Spread Operator
ES6 introduces the **spread operator**, which allows us to expand arrays and other expressions in places where multiple parameters or elements are expected.
ES5 code
```
var arr = [6, 89, 3, 45];
var maximus = Math.max.apply(null, arr);
```
ES6 code
```
const arr = [6, 89, 3, 45];
const maximus = Math.max(...arr);
```
_...arr returns an unpacked array. In other words, it spreads the array. However, the spread operator only works in-place, like in an argument to a function or in an array literal. For example:_

## Destructuring 
### Extract
Destructuring assignment is special syntax introduced in ES6, for neatly assigning values taken directly from an object.
ES5 code
```
const user = { name: 'John Doe', age: 34 };

const name = user.name;
const age = user.age;
```
ES6 code
```
const { name, age } = user;
```

### Assign
Objects
```
const user = { name: 'John Doe', age: 34 };
const { name: userName, age: userAge } = user;
```
Nested Objects
```
const user = {
  johnDoe: { 
    age: 34,
    email: 'johnDoe@freeCodeCamp.com'
  }
};
const { johnDoe: { age: userAge, email: userEmail }} = user;
```
Arrays
```
const [a, b] = [1, 2, 3, 4, 5, 6];
console.log(a, b);
const [a, b,,, c] = [1, 2, 3, 4, 5, 6];
console.log(a, b, c);
```
Rest elements
```
const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];
console.log(a, b);
console.log(arr);
```

### Passing to Functions
```
const profileUpdate = (profileData) => {
  const { name, age, nationality, location } = profileData;

}
```
```
const profileUpdate = ({ name, age, nationality, location }) => {

}
```

## Declarative Functions
ES5 code
```
const person = {
  name: "Taylor",
  sayHello: function() {
    return `Hello! My name is ${this.name}.`;
  }
};
```
ES6 code
```
const person = {
  name: "Taylor",
  sayHello() {
    return `Hello! My name is ${this.name}.`;
  }
};
```

## Object Property Shorthand
ES5 code
```
const getMousePosition = (x, y) => ({
  x: x,
  y: y
});
```
ES6 code
```
const getMousePosition = (x, y) => ({ x, y });
```

## Constructor
```
// Explicit constructor
class SpaceShuttle {
  constructor(targetPlanet) {
    this.targetPlanet = targetPlanet;
  }
  takeOff() {
    console.log("To " + this.targetPlanet + "!");
  }
}

// Implicit constructor 
class Rocket {
  launch() {
    console.log("To the moon!");
  }
}

const zeus = new SpaceShuttle('Jupiter');
// prints To Jupiter! in console
zeus.takeOff();

const atlas = new Rocket();
// prints To the moon! in console
atlas.launch();
```

## Getters and Setters
Getter functions are meant to simply return (get) the value of an object's private variable to the user without the user directly accessing the private variable.
Setter functions are meant to modify (set) the value of an object's private variable based on the value passed into the setter function. This change could involve calculations, or even overwriting the previous value completely.
```
class Book {
  constructor(author) {
    this._author = author;
  }
  // getter
  get writer() {
    return this._author;
  }
  // setter
  set writer(updatedAuthor) {
    this._author = updatedAuthor;
  }
}
const novel = new Book('anonymous');
console.log(novel.writer);
novel.writer = 'newAuthor';
console.log(novel.writer);
```

## Module Script
```
<script type="module" src="filename.js"></script>
```
**Export module**
```
const add = (x, y) => {
  return x + y;
}

export { add };
```
**Import module** 
```
import { add, subtract } from './math_functions.js';
```
**Import everything from the file**
```
import * as myMathModule from "./math_functions.js";
myMathModule.add(2,3);
myMathModule.subtract(5,3);
```
**Export Default**
Since export default is used to declare a fallback value for a module or file, you can only have one value be a default export in each module or file. Additionally, you cannot use export default with var, let, or const
```
export default function add(x, y) {
  return x + y;
}

export default function(x, y) {
  return x + y;
}
```
**Import Default**
```
import add from "./math_functions.js";
```

## Promise
A promise in JavaScript is exactly what it sounds like - you use it to make a promise to do something, usually asynchronously. 
When the task completes, you either fulfill your promise or fail to do so. 
Promise is a constructor function, so you need to use the new keyword to create one. It takes a function, as its argument, with two parameters - resolve and reject. 
These are methods used to determine the outcome of the promise. The syntax looks like this:
```
const myPromise = new Promise((resolve, reject) => {

});
```
A promise has three states: **pending**, **fulfilled**, and **rejected**. 
The promise you created in the last challenge is forever stuck in the pending state because you did not add a way to complete the promise. 
The resolve and reject parameters given to the promise argument are used to do this. 
**resolve** is used when you want your promise to succeed, and reject is used when you want it to fail. 
These are methods that take an argument, as seen below.
```
const myPromise = new Promise((resolve, reject) => {
  if(condition here) {
    resolve("Promise was fulfilled");
  } else {
    reject("Promise was rejected");
  }
});
```
Promises are most useful when you have a process that takes an unknown amount of time in your code (i.e. something asynchronous), often a server request. 
When you make a server request it takes some amount of time, and after it completes you usually want to do something with the response from the server. 
This can be achieved by using the then method.
```
Promise.prototype.then(onFulfilled, onRejected)
```
The **then** method schedules callback functions for the eventual completion of a Promise - either fulfillment or rejection. 
One of the onFulfilled and onRejected handlers will be executed to handle the current promise's fulfillment or rejection. 
When the promise is fulfilled with resolve the onFulfilled handler is called.
```
myPromise.then(result => {
  
});
```
**catch** is the method used when your promise has been rejected. 
It is executed immediately after a promise's reject method is called. Here’s the syntax:
```
myPromise.catch(error => {
  
});
```
