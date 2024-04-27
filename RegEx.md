# Regular Expressions

## Test Method
Regular expressions are used in programming languages to match parts of strings. 
You create patterns to help you do that matching.
If you want to find the word "the" in the string "The dog chased the cat", you could use the following regular expression: /the/. Notice that quote marks are not required within the regular expression.
JavaScript has multiple ways to use **regexes**. 
One way to test a regex is using the **.test() method**. 
The **.test() method** takes the regex, applies it to a string (which is placed inside the parentheses), and returns true or false if your pattern finds something or not.
```
let testStr = "freeCodeCamp";
let testRegex = /Code/;
testRegex.test(testStr); // true 
```

## Regex Patterns
```
let petRegex = /dog|cat|bird|fish/; // OR
let fccRegex = /freeCodeCamp/i; // IGNORE CASE
let repeatRegex = /Repeat/g; // GLOBAL SEARCH
let huRegex = /hu./; // WILDCARD
let bgRegex = /b[aiu]g/; // BAG, BIG, BUG
let myRegex = /[a-z0-9]/; // RANGES
let myRegex = /[^aeiou0-9]/gi;
let myRegex = /s+/gi; // ONE OR MORE TIMES
let myRegex = /<.*?>/; // LAZY MATCH
let firstRegex = /^Ricky/; // ON THE BEGINNING
let storyRegex = /story$/; // AT THE END
let shortHand = /\w+/; // [A-Za-z0-9_]
let shortHand = /\W/; // [^A-Za-z0-9_]
let numRegex = /\d/g; // [0-9]
let noNumRegex = /\D/g; // [^0-9]
```

## Match Method
```
"Hello, World!".match(/Hello/);
let ourStr = "Regular expressions";
let ourRegex = /expressions/;
ourStr.match(ourRegex);
```
```
'string'.match(/regex/);
/regex/.test('string');
```
