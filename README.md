# Unit 2 Practice Assessment - JavaScript Foundations

## Short Responses 

1. **The function declaration comes _after_ the variable declaration in the code below. What will happen when it this code runs?**
```javascript
let greeting = "Hello!"

function sayItLoud() {
  console.log(`${greeting}!!!`)
}

sayItLoud();
```
Prediction: "Hello!!!" is logged to the console

Actual Output: "Hello!!!" was logged to the console


2. **Okay... so why does the code below throw an error?**
```javascript
sayItLoud();

function sayItLoud() {
  console.log(`${greeting}!!!`)
}

let greeting = "Hello"
```
Prediction: This will result in a `ReferenceError` for referencing a variable that hasn't been defined yet. `let` variable aren't initialized above the line they were declared.

Actual Output: A `ReferenceError` was thrown for the predicted reason.



3. **Mmhmmm... so what about this😰. What does the following code log? Why?**
```javascript
sayItLoud();
function sayItLoud() {
  console.log(`${greeting}!!!`)
}
var greeting = "Hello"
```
Prediction: `"undefined!!!"` will be logged. In this case the `var` varible is hoisted to the top of the global scope and is initialzed with the value of `undefined`.

Actual Output: `"undefined"` was logged to the console.



4. **Why does the following block of code throw an error? How can we fix this without changing the variable declaration keyword?**
```javascript
const isSunny = true;

if (isSunny) {
  let status = 'No umbrella needed!';
} else {
  let status = 'Better wear a raincoat!'
}

console.log(status);
```
**tags:** #variableScope
**key:** "let is block scoped"

Prediction: A `ReferenceError` wil bethrown for trying to reference a variable that hasn't been defined, unlike `var` variables, `let` variables are initialized at all above the line they are declared.

Actual Output: `ReferenceError: status is not defined`



5. **Why does the following block of code NOT throw an error?**
```javascript
const isSunny = true;

if (isSunny) {
  var status = 'No umbrella needed!';
} else {
  var status = 'Better wear a raincoat!'
}

console.log(status);
```
**tags:** #variableScope
**key:** "variables declared with var are not block scoped"
Prediction: Since `let` variables are block scoped, the status declarations can't be referenced to outside of there respective blocks.

Actual Ouput: `ReferenceError: status is not defined`


6. **In JavaScript, we can declare variables with `var`, `let`, and `const`. What are the differences between each? Be sure to comment on how each declaration impacts the _scope_, _reassignment_, and _hoisting_ of variables.**

### `var`
> `var` is a keyword declaration used to declare variables, this keyword was widely used from 1995 to 2015 and became somewhat outdated when the `let` `const` keywords were added. Variables declared with `var` are mutable; they can be re-assigned a different value. `var` variables are function scoped or globally scoped (depending wether or not it's declared inside a function) and hoisted to the top of it. `var` variables can be referenced within their scope *and* are initialized with the value 'undefined' before the line they were declared on.

### `let`
> The `let` keyword is used to declared variables that we want to mutate in some way after it's been declared and/or assigned a value, giving us the power to re-assign a `let` variable after it's been declared. `let` variables are block scoped (whatever's inside `{}`) and *behave* as if they arent hoisted. `let` variables do exists in the Lexical Enviroment when the code in being interpredted, so you'll recieve a 'ReferenceError' before references a `let` variable before being *initialized*, although hoisted `let` variables aren't initialized before they are declared even with the value 'undefined'. `let` *and* `const` variables are in a temporal deadzone before the line they are declared

### `const`
>Like `let`, variables declared with `const` are block scoped and experiences the same hoisting and scope behaviors as `let`. `const` is short for 'constant' meaning this keyword was made for variables that we want to remain constant througout our program, making it immutable.

7. **Where does the following code throw an error? What type of error? Why?**
```javascript
let a = b;

console.log(a);
```
**tags:** #variableDeclaration
**key:** "the variable `b` is not defined."
Prediction: The code will throw a `ReferenceError` because `b` hasn't been defined

Acutal Output: `ReferenceError: b is not defined`


8. **What is the value of `y` after this code runs? Explain why this is the case.**
```javascript
let x = 1;
let y = x;
x += 1;

console.log(x);
console.log(y);
```
**tags:** #mutability
**key:** "`y` points to the integer `1`, a primitive data type", "reassigning `x` has no effect on `y`" 
Prediction: Despite re-assigning `x`, `y` will still hold the value `1`. primitive data values are passed by value and not passed by reference.

Actual Output:`1` is logged when `console.log`ing `y`.


9. **What does the following code log? Explain why?**
```javascript
let a = {goals: "Enmanuel"};
let b = a;
a.goals = "Cielo";
console.log(b.goals);
```
**tags:** #mutability
**key:** "`b` points to the same object referenced by `a`"
Prediction:`"Cielo"` will be logged to the console, because the variable `b` point to the reference of variable `a` that stores the object

Actual Output: `"Cielo"` is logged to the console


10. **Where does the following code throw an error? What type of error? Why?**
```javascript
const fellows = 'Itzel Carmen';
fellows = 'Itzel Carmen Shemar';

console.log(fellows);
```
**tags**: #variableDeclaration #mutability #primitives
**key:** "variables declared with `const` cannot be reassigned"
Prediction: The error will be thrown at line 2, because we are reassigning a `const` variable. A `ReferenceError` will be thrown???

Actual Output: Was right about where and why we get the erro. But the *type* of error was different `TypeError: Assignment to constant variable.`


11. **Wait, why doesn't the code below throw an error?! 🧐 What does this demonstrate?**
```javascript
const fellows = ['Itzel', 'Carmen'];
fellows.push('Shemar');

console.log(fellows);
```
**tags:** #mutability #objects
**key:** "`fellows` was not reassigned", "JavaScript objects are mutable"
Prediction: `['Itzel', 'Carmen', 'Shemar']` will be logged to the console


Actual Output: `['Itzel', 'Carmen', 'Shemar']` was logged to the console


12. **What does the following code log? Why?**
```javascript
let greeting = "What's up?";

function say() {
 return `${greeting}! 🤟🏿`
}

console.log(say);
```
**tags**: #functionExecution #functionArguments
**key:** "function was not invoked"
Prediction: `[Function: say}` will be logged to the console

Actual Output: `[Function: say}` was logged to the console


13. **What does the following code log? What does this say about JavaScript function arguments?**
```javascript
function shoutOut() {
  console.log(`The flyest person in the room is Carmen!`);
}

shoutOut('Devonte');
```
**tags:** #functionExecution #variableScope
**key:** "arguments are optional", "extraneous arguments are ignored"
Prediction:`"The flyest person in the room in Carmen"` will be logged to the console

Actual Output: `"The flyest person in the room in Carmen"` was logged to the console


14. **What happens if a function is invoked with fewer arguments than there are parameters? Include a code snippet to illustrate.**

Prediction: Invoking a function with fewer arguments will mostly likely result in a `ReferenceError` because when one sets parameters in the function declaration, they expect arguments. These parameters will be referenced to at any point in the function body. If an inssuficient amount of arguments are given then, again, we'll get a `ReferenceError` for referencing a variable that hasn't been defined

Actual Output: Nevermind, it looks like Javasript literally does not give a fuck about missing arguments 
```js
const lala = function(num1,num2){
    let sum = num1 + num2
    console.log(sum)
}
lala(2)
```
For example this function will just log `NaN` to the console, because tried to add get the sum of the number `2` and the value `undefined` which. The result of this isn't a number. Cool I guess.
**tags:** #functionExecution #functionArguments
**key:** "missing parameters are set to `undefined`"



15. **What about extra parameters? How can we access them and use them to our advantage? Illustrate by writing a function that takes any number of integers as arguments and returns their sum.**

Example:
```javascript
sum(1, 2, 10); // 13
sum(5); // 5
sum(100, 200, 800, 1, 1, 1); // 1103;
```
Prediction: We can access extra parameters by using the spread operator (`...`).This operator takes in any number of values and spreads them out across a place where we expect a large or an inconsistent amount of values.
```js
const paramLogger = function(...Args){
    console.log(...Args)
}

paramLogger(1)
paramLogger(1,2)
paramLogger(1,2,3)
```

Actual Output: I was correct, we can use the spread operator to take in any number a values. The code above simply logs to the console all the arguments given when invoking the `paramLogger` function.
**tags:** #functionExecution
**key:** the array-like `argument` object, the ES6 rest parameter syntax



16. **What does the following code log? Why?**
```javascript
let bestCoder = 'Laura';

function shoutOut() {
  bestCoder = 'Motun';
}

shoutOut();
console.log(`The best coder in the room is ${bestCoder}`.);
```
Predict: 

Actual Output:

Actual Output:
**tags:** #variableScope
**key:** "functions have access to variables defined in their local scope and all surrounding scopes"



17. **What does the following code log? Why?**
```javascript
let theGoat = 'Reuben';

function shoutOut() {
  let theGoat = `Maya`;
  console.log(`${theGoat} is the hardest working person in the room.`);
}

shoutOut();
console.log(`${theGoat} is also the hardest working person in the room.`);
```
**tags:** #variableScope
**key:** "lexical scope"



18. **What does the following code log? Why?**
```javascript
let theCEO;

function hire(theCEO) {
  theCEO = 'Mark';
}

hire(theCEO);
console.log(`I have no doubt that ${theCEO} will be running a company of his own very soon. I just hope that he will hire me when I need a job.`);
```
**tags:** #variableScope
**key:** "variable shadowing" the function declarations creates a _new_ local variable declaration for its parameter, `theCEO`."



19. **What does it mean to _pass by value_? For what data types does JavaScript _pass by value_? Use a code snippet to illustrate.**

**tags:** #mutability #functionExecution
**key:** "primitive data types are passed by value"



20. **What does it mean to _pass by reference_? For what data types does JavaScript  appear to _pass by reference_? Use a code snippet to illustrate.**

**tags:** #mutability #functionExecution
**key:** "JavaScript objects are passed by reference"



21. **Explain why the first code snippet below throws an error, but the second does not.**

```javascript
10 + a;        // ReferenceError: a is not defined
```

```javascript
let a = {};
10 + a.x;      // Evaluates to NaN
```
**tags:** #objects
**key:** "undefined properties of objects return `undefined`"



22. **What is the relationship between JavaScript Objects and JavaScript Arrays? We say a JavaScript Object is _empty_ if it has no properties of its own. We say that a JavaScript Array is _empty_ if it has no _elements_. How do we check for emptiness of JavaScript Objects? How do we check for emptiness of JavaScript Arrays. Use code snippets to illustrate your answer.**

**tags:** #objects #arrays
**key:** "JavaScript arrays are objects", "use `.length` to check for array emptiness", "use Object.keys(object) to check for object emptiness"



## Problem Set
1. Write a function that takes a string, doubles every consonant character in the string, and returns the result as a new string. The function should not double vowels (``'a'``,``'e'``,``'i'``,``'o'``,``'u'``), digits, punctuation, or whitespace.

Examples:
```javascript
doubleConsonants('String');          // "SSttrrinngg"
doubleConsonants('Hello-World!');    // "HHellllo-WWorrlldd!"
doubleConsonants('July 4th');        // "JJullyy 4tthh"
doubleConsonants('');                // ""
```



2. Write a function that takes a string and returns the string reversed.

Examples:
```javascript
reverse('Test'); // "tseT"
reverse('anotherTest'); // "tseTrehtona"
reverse('factor In spaces'); // "secaps nI rotcaf"
reverse(''); // ""
```



3. Write a function takes an integer `year` as an argument and returns a boolean based on whether the year is a leap year. Note: Every year that is evenly divisible by 4 is a leap year, except every year that is evenly divisible by 100, unless the year is also evenly divisible by 400.

Examples:
```javascript
isLeapYear(1997); // false
isLeapYear(1996); // true
isLeapYear(1900); // false
isLeapYear(2000); // true
```


4. Write a function that combines two arrays into one new array. The new array should start with an item from the first array argument, then an item from the second array argument, and then alternates. You can assume the two input arrays are the same length.

Example:
```javascript
combineArrays([1, 2, 3], [4, 5, 6]);      // [1, 4, 2, 5, 3, 6]
combineArrays(['a', 'b'], ['x', 'y']);    // ['a', 'x', 'b', 'y']
combineArrays([true], [false]);           // [true, false]
```

5. Write a function that returns an object that shows how many times each vowel shows up in a sentence (vowels are `'a'`, `'e'`, `'i'`, `'o'`, and `'u'`). The returned object should have exactly 5 key-value pairs, one for each vowel (the value shold be the number of times that vowel appears in the sentence). 

Example:
```javascript
countVowels('Hello World');                                     // {'a': 0, 'e': 1, 'i': 0, 'o': 2, 'u': 0}
countVowels('The quick brown fox jumped over the lazy dog');    // {'a': 1, 'e': 3, 'i': 1, 'o': 4, 'u': 2}
countVowels('Over the Marcy Lab School');                       // {'a': 2, 'e': 1, 'i': 0, 'o': 3, 'u': 0}
```


6. Write a function that takes a sentence string as an argument, and returns that string with every occurrence of a "number word" — `'zero'`, `'one'`, `'two'`, `'three'`, `'four'`, `'five'`, `'six'`, `'seven'`, `'eight'`, `'nine'` — converted to its corresponding digit character.

Example:
```javascript
wordToDigit('Please call me at five five five one two three four. Thanks.');
// "Please call me at 5 5 5 1 2 3 4. Thanks."
```



7. For a game of Dungeons & Dragons, each player starts by generating a character they can play with. This character has, among other things, six abilities; strength, dexterity, constitution, intelligence, wisdom and charisma. These six abilities have scores that are determined randomly. You do this by rolling four 6-sided dice and record the sum of the largest three dice. You do this six times, once for each ability.

Your character's initial hitpoints are 10 + your character's constitution modifier. You find your character's constitution modifier by subtracting 10 from your character's constitution, divide by 2 and round down.

Write a random character generator function that follows the rules above.

For example, the six throws of four dice may look like:
  * 5, 3, 1, 6: You discard the 1 and sum 5 + 3 + 6 = 14, which you assign to strength.
  * 3, 2, 5, 3: You discard the 2 and sum 3 + 5 + 3 = 11, which you assign to dexterity.
  * 1, 1, 1, 1: You discard the 1 and sum 1 + 1 + 1 = 3, which you assign to constitution.
  * 2, 1, 6, 6: You discard the 1 and sum 2 + 6 + 6 = 14, which you assign to intelligence.
  * 3, 5, 3, 4: You discard the 3 and sum 5 + 3 + 4 = 12, which you assign to wisdom.
  * 6, 6, 6, 6: You discard the 6 and sum 6 + 6 + 6 = 18, which you assign to charisma.
Because constitution is 3, the constitution modifier is -4 and the hitpoints are 6.

Your function should take one argument, a `name`. It should generate random attribute values using `Math.rand()`. The function should return a JavaScript Object that contains all of the above attributes.

Example:
```javascript
characterGenerator("Elminster");

/*
{
  name: "Elminster"
  strength: 10,
  dexterity: 8,
  constitution: 12,
  intelligence: 14,
  wisdom: 12,
  charisma: 18,
  hitpoints: 11
}

*/
```
