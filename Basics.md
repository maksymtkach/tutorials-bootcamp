# JavaScript Basics

## Contents
- [Basic JavaScript](#basic-javascript)
  - [Comments in JS](#comments-in-js)
  - [Variables and Data Types](#variables-and-data-types)
    - [Initializing](#initializing)
    - [Naming Basics](#naming-basics)
    - [const](#const)
    - [Basic math operations](#basic-math-operations)
    - [Compound Assignment](#compound-assignment)
  - [Strings](#strings)
    - [Escaping Literal Quotes](#escaping-literal-quotes)
    - [Quoting Strings with Single Quotes](#quoting-strings-with-single-quotes)
    - [Escape Sequences](#escape-sequences)
    - [Concatenating](#concatenating)
    - [Constructing strings](#constructing-strings)
    - [Operations with strings](#operations-with-strings)
  - [Arrays](#arrays)
    - [Accessing and modifying](#accessing-and-modifying)
    - [push, pop, shift, unshift](#push-pop-shift-unshift)
  - [Functions](#functions)
    - [Global and Local Scope](#global-and-local-scope)
  - [Queue](#queue)
  - [Bool](#bool)
  - [Conditionals](#conditionals)
    - [Ternary Operator](#ternary-operator)
    - [Equality and Strict Equality](#equality-and-strict-equality)
    - [Inequality and Strict Inequality](#inequality-and-strict-inequality)
    - [Greater and Less](#greater-and-less)
    - [AND / OR](#and--or)
  - [Switch](#switch)
  - [Objects](#objects)
    - [Accessing Properties](#accessing-properties)
    - [Updating Properties](#updating-properties)
    - [Adding Properties](#adding-properties)
    - [Deleting Properties](#deleting-properties)
    - [Usage of Objects](#usage-of-objects)
    - [Looking for Property](#looking-for-property)
  - [Loops](#loops)
    - [While and Do While](#while-and-do-while)
    - [For](#for)
  - [Recursion](#recursion)
  - [Random](#random)
  - [parseInt](#parseint)

## Basic JavaScript
### Comments in JS
Comments are lines of code that JavaScript will intentionally ignore. Comments are a great way to leave notes to yourself and to other people who will later need to figure out what that code does.
```
// This is an in-line comment.
```
```
/* This is a
multi-line comment */
```
### Variables and Data Types
#### Initializing
It is common to initialize a variable to an initial value in the same line as it is declared.
```
var myVar = 0;
var myName = "your name";
```
When JavaScript variables are declared, they have an initial value of undefined. If you do a mathematical operation on an **undefined** variable your result will be **NaN** which means "Not a Number". If you concatenate a string with an undefined variable, you will get a string of **undefined**.

#### Naming Basics

Write variable names in JavaScript in _camelCase_. In _camelCase_, multi-word variable names have the first word in lowercase and the first letter of each subsequent word is capitalized.

```
var someVariable;
var anotherVariableName;
var thisVariableNameIsSoLong;
```

#### const

**const** has all the awesome features that **let** has, with the added bonus that variables declared using const are read-only. They are a constant value, which means that once a variable is assigned with const, it cannot be reassigned:

```
const FAV_PET = "Cats";
```

_You should always name variables you don't want to reassign using the const keyword. This helps when you accidentally attempt to reassign a variable that is meant to stay constant._

#### Basic math operations 

```
const mySum = 5 + 10;
const mySubstract = 12 - 6;
const myProduct = 13 * 13;
const myDivision = 16 / 2;
const myReminder = 12 % 5; 
```

```
i++; // i = i + 1
i--; // i = i - 1
```

#### Compound Assignment 
```
let myVar = 1;
myVar += 5;
myVar -= 2;
myVar *= 5;
myVar /= 5;
```

### Strings
#### Escaping Literal Quotes
```
const sampleStr = "Alan said, \"Peter is learning JavaScript\".";
```

#### Quoting Strings with Single Quotes
```
const conversation = 'Finn exclaims to Jake, "Algebraic!"';
```

#### Escape Sequences
| Code | Output         |
|------|----------------|
| `\'` | single quote   |
| `\"` | double quote   |
| `\\` | backslash      |
| `\n` | newline        |
| `\t` | tab            |
| `\r` | carriage return|
| `\b` | backspace      |
| `\f` | form feed      |

#### Concatenating
```
const ourStr = "I come first. " + "I come second.";
```
```
let ourStr = "I come first. ";
ourStr += "I come second.";
```

#### Constructing strings 
```
const ourName = "freeCodeCamp";
const ourStr = "Hello, our name is " + ourName + ", how are you?";
```

```
const anAdjective = "awesome!";
let ourStr = "freeCodeCamp is ";
ourStr += anAdjective;
```

#### Operations with strings
_Getting strings length_
```
console.log("Alan Peter".length); // 10
```
_Getting specific char_
```
const firstName = "Charles";
const firstLetter = firstName[0]; // C
const lastLetter = firstName[firstName.length - 1]; // s
```
_The only way to change myStr would be to assign it with a new value, like this_
```
let myStr = "Bob";
myStr = "Job";
```

### Arrays
```
const sandwich = ["peanut butter", "jelly", "bread"];
const teams = [["Bulls", 23], ["White Sox", 45]];
```

#### Accessing and modifying
```
const array = [50, 60, 70];
console.log(array[0]); // 50
const data = array[1]; // 60
array[2] = 65; // [50, 60, 65]
```

#### push, pop, shift, unshift
_The **push()** method takes one or more arguments and appends them to the end of the array, in the order in which they appear. It returns the new length of the array._
```
const arr1 = [1, 2, 3];
arr1.push(4, 5);
// 1, 2, 3, 4, 5
const arr2 = ["Stimpson", "J", "cat"];
arr2.push(["happy", "joy"]);
// Stimpson, J, cat, [happy, joy]
```
_**.pop()** is used to pop a value off of the end of an array. We can store this popped off value by assigning it to a variable. In other words, **.pop()** removes the last element from an array and returns that element._
```
const threeArr = [1, 4, 6];
const oneDown = threeArr.pop(); 
console.log(oneDown); // 6
console.log(threeArr); // 1, 4
```
_**.shift()** works just like **.pop()**, except it removes the first element instead of the last._
```
const ourArray = ["Stimpson", "J", ["cat"]];
const removedFromOurArray = ourArray.shift();  // Stimpson
// ourArray = J, [cat]
```
_**.unshift()** works exactly like **.push()**, but instead of adding the element at the end of the array, **unshift()** adds the element at the beginning of the array._
```
const ourArray = ["Stimpson", "J", "cat"];
ourArray.shift();
ourArray.unshift("Happy");
// ourArray = Happy, J, cat
```

### Functions
You can call or invoke this function by using its name followed by parentheses, like this: **functionName();** Each time the function is called it will print out the message Hello World on the dev console. All of the code between the curly braces will be executed every time the function is called.
```
function functionName() {
  console.log("Hello World");
}
```
Parameters are variables that act as placeholders for the values that are to be input to a function when it is called. When a function is defined, it is typically defined along with one or more parameters. The actual values that are input (or "passed") into a function when it is called are known as arguments.
```
function testFun(param1, param2) {
  console.log(param1, param2);
}
```
We can pass values into a function with arguments. You can use a return statement to send a value back out of a function.
```
function plusThree(num) {
  return num + 3;
}

const answer = plusThree(5); // 8
```

#### Global and Local Scope
- In JavaScript, scope refers to the visibility of variables.
- Variables which are defined outside of a function block have Global scope.
This means, they can be seen everywhere in your JavaScript code.
- Variables which are declared without the **let** or **const** keywords are automatically created in the **global scope**.
This can create unintended consequences elsewhere in your code or when running a function again. You should always declare your variables with let or const.
- Variables which are declared within a function, as well as the function parameters, have local scope.
That means they are only visible within that function.
```
function myTest() {
  const loc = "foo";
  console.log(loc);
}

myTest();
console.log(loc); // Error
```

### Queue
In Computer Science a **queue** is an abstract Data Structure where items are kept in order. 
New items can be added at the back of the queue and old items are taken off from the front of the queue.

### Bool
Another data type is the Boolean. 
Booleans may only be one of two values: true or false. 
They are basically little on-off switches, where true is on and false is off. 
These two states are mutually exclusive.

### Conditionals
```
function foo(x) {
  if (x < 1) {
    return "Less than one";
  } else if (x < 2) {
    return "Less than two";
  } else {
    return "Greater than or equal to two";
  }
}
```

#### Ternary Operator
```
function findGreaterOrEqual(a, b) {
  return (a === b) ? "a and b are equal" 
    : (a > b) ? "a is greater" 
    : "b is greater";
}
```

#### Equality and Strict Equality
```
function equalityTest(myVal) {
  if (myVal == 10) {
    return "Equal";
  }
  return "Not Equal";
}
```
If the values being compared are not of the same type, the equality operator will perform a type conversion, and then evaluate the values. 
However, the strict equality operator will compare both the data type and value as-is, without converting one type to the other.
```
3 ===  3  // true
3 === '3' // false
```
#### Inequality and Strict Inequality
```
1 !=  2    // true
1 != "1"   // false
1 != '1'   // false
1 != true  // false
0 != false // false
```
```
3 !==  3  // false
3 !== '3' // true
4 !==  3  // true
```
#### Greater and Less
```
5   >  3  // true
7   > '3' // true
2   >  3  // false
'1' >  9  // false

2   < 5 // true
'3' < 7 // true
5   < 5 // false
3   < 2 // false
'8' < 4 // false
```
```
6   >=  6  // true
7   >= '3' // true
2   >=  3  // false
'7' >=  9  // false

4   <= 5 // true
'7' <= 7 // true
5   <= 5 // true
3   <= 2 // false
'8' <= 4 // false
```

#### AND / OR
```
// if num > 5 and num < 10
if (num > 5 && num < 10) { 
  return "Yes";
}
return "No";
```
```
// if num > 10 or num < 5
if (num > 10 || num < 5) {
  return "No";
}
return "Yes";
```

### Switch
```
let result = "";
switch (val) {
  case 1:
  case 2:
  case 3:
    result = "1, 2, or 3";
    break;
  case 4:
    result = "4 alone";
    break;
  default:
    result = "Error"
    break;
}
```

### Objects
```
const cat = {
  "name": "Whiskers",
  "legs": 4,
  "tails": 1,
  "enemies": ["Water", "Dogs"]
};

const anotherObject = {
  make: "Ford",
  5: "five",
  "model": "focus"
};
```

#### Accessing Properties
Dot notation
```
const myObj = {
  prop1: "val1",
  prop2: "val2"
};

const prop1val = myObj.prop1; // val1
```
Bracket notation
```
const myObj = {
  "Space Name": "Kirk",
  "More Space": "Spock",
  "NoSpace": "USS Enterprise"
};

myObj["Space Name"]; // Kirk
```
Variables
```
const dogs = {
  Fido: "Mutt",
  Hunter: "Doberman",
  Snoopie: "Beagle"
};

const myDog = "Hunter";
const myBreed = dogs[myDog]; 
console.log(myBreed); // Doberman
```

#### Updating Properties
```
const ourDog = {
  "name": "Camper",
  "legs": 4,
  "tails": 1,
  "friends": ["everything!"]
};
ourDog.name = "Happy Camper";
ourDog["name"] = "Happy Camper";
```

#### Adding Properties
```
const ourDog = {
  "name": "Camper",
  "legs": 4,
  "tails": 1,
  "friends": ["everything!"]
};
ourDog.bark = "bow-wow";
ourDog["bark"] = "bow-wow";
```

#### Deleting Properties
```
const ourDog = {
  "name": "Camper",
  "legs": 4,
  "tails": 1,
  "friends": ["everything!"],
  "bark": "bow-wow"
};

delete ourDog.bark;
```

#### Usage of Objects
```
const article = {
  "title": "How to create objects in JavaScript",
  "link": "https://www.freecodecamp.org/news/a-complete-guide-to-creating-objects-in-javascript-b0e2450655e8/",
  "author": "Kaashan Hussain",
  "language": "JavaScript",
  "tags": "TECHNOLOGY",
  "createdAt": "NOVEMBER 28, 2018"
};

const articleAuthor = article["author"];
const articleLink = article["link"];

const value = "title";
const valueLookup = article[value];
```

#### Looking for Property
```
function checkForProperty(object, property) {
  return object.hasOwnProperty(property);
}

checkForProperty({ top: 'hat', bottom: 'pants' }, 'top'); // true
checkForProperty({ top: 'hat', bottom: 'pants' }, 'middle'); // false
```

### Loops
#### While and Do While
In this example, we initialize the value of ourArray to an empty array and the value of i to 5. When we execute the while loop, the condition evaluates to false because i is not less than 5, so we do not execute the code inside the loop. The result is that ourArray will end up with no values added to it, and it will still look like [] when all of the code in the example above has completed running.
```
const ourArray = [];
let i = 0;

while (i < 5) {
  ourArray.push(i);
  i++;
}
```
In this case, we initialize the value of i to 5, just like we did with the while loop. When we get to the next line, there is no condition to evaluate, so we go to the code inside the curly braces and execute it. We will add a single element to the array and then increment i before we get to the condition check. When we finally evaluate the condition i < 5 on the last line, we see that i is now 6, which fails the conditional check, so we exit the loop and are done. At the end of the above example, the value of ourArray is [5]. Essentially, a do...while loop ensures that the code inside the loop will run at least once. Let's try getting a do...while loop to work by pushing values to an array.
```
const ourArray = [];
let i = 0;

do {
  ourArray.push(i);
  i++;
} while (i < 5);
```

#### For
```
const ourArray = [];

for (let i = 0; i < 10; i += 2) {
  ourArray.push(i);
}

const arr = [10, 9, 8, 7, 6];

for (let i = 0; i < arr.length; i++) {
   console.log(arr[i]);
}
```

### Recursion 
```
function multiply(arr, n) {
    let product = 1;
    for (let i = 0; i < n; i++) {
      product *= arr[i];
    }
    return product;
  }
```
```
function multiply(arr, n) {
    if (n <= 0) {
      return 1;
    } else {
      return multiply(arr, n - 1) * arr[n - 1];
    }
  }
```

### Random
```
Math.floor(Math.random() * 20); // 0 - 19
Math.floor(Math.random() * (max - min + 1)) + min
```

### parseInt
```
const a = parseInt("007"); // 7
const a = parseInt("11", 2); // 3 (binary)
```
