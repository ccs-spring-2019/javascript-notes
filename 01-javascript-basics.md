## JavaScript Comments

A comment is ignored by the JS engine

* demonstrate a single line comment
``` 
Single line comments start with //
```
* demonstrate a multiple line comment
```
Multi-line comments start with /* and end with */
```

A JavaScript program is one or more JS statements. Like a sentence, a statement is one coherent "thought" or instruction.

* It should appear on its own line
* It should end with a semicolon (a semicolon means "this instruction is over, move to the next one.")

## JavaScript Built-in Data Structures

Six data types that are primitives:

* boolean
  * true; false; 10 > 5;
  * undefined >> false
  * null >> false
  * boolean >> true is true, false is false
  * number >> +0, -0, NaN is false otherwise true
  * string >> "" (it's length is 0) is false otherwise true
  * object >> true
* null
  * represents an object that is not defined
  * you can empty an object by setting it to null (the value is null, but type is still an object)
  * typeof null is object
* undefined
  * represents a value that is not defined
  * You can empty an object by setting it to undefined (both value and type is undefined)
  * typeof undefined is undefined
* number
  * 1; 3.14; -20; 4.5e7;
  * 64-bit floating number https://floating-point-gui.de/basic/
  * typeof +Infinity is number
  * typeof -Infinity is number
  * typeof NaN is number
* string
  * 'Cool'; "Cool"; "That was 'cool'"; "That was \"cool\"";
* symbol
  * Symbols do not have a literal syntax (e.g how Strings have '')
  * A Symbol is a unique and immutable primitive value and may be used as the key of an Object property

Anything that doesn’t belong to any of these six primitive types is considered an object: {}; function object; array object

## JavaScript Values

NaN represents a Number that doesn't make sense, e.g. 0 / 0

## Variables

A variable is like a name badge, in that it doesn't contain anything, but is a name or label for a value.

Declare a variable:
```
  var age;
```
Assign a value to a variable
```
  age = 52;
```
A single equal sign is the "assignment operator".

Shorthand:
```
  var age = 52;
```
Declare multiple variables:
```
  var age, favoriteColor, name;
```
Declare and assign multiple variables:
```
  var age = 37, favoriteColor = "green", name = "Jake";
```
Variable naming:

* First character a-z, A-Z, $, _
* Variables starting with $ are often used for DOM objects
* Variables starting with _ are often used for things that are not meant to be used by the developer
  * underscore convention is a pretty good convention to use for things that are sort of private, but that you don't actually need to hide
  * frequently used to preface a name of an object's property or method that is private
  * standard way to indicate an unused function argument
  * I use _ in React classes to separate my methods from built in methods
* The other characters can be letters, $, _ , numbers
* They are case sensitive
* The convention, but not rule, is to capitalize each word after the first (a.k.a. camelCase)

* var
  * Declares a variable, optionally initializing it to a value.
* let
  * Declares a block-scoped, local variable, optionally initializing it to a value.
  * Example https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let
  * not subject to Variable Hoisting
* const
  * Declares a block-scoped, read-only named constant
  * not subject to Variable Hoisting

Variables are not tied to a type; a variable can be assigned and reassigned data of any type

## Expressions

An expression is code that evaluates to a value.
```
// a value is an expression
'cool' // => 'cool'

// a variable is an expression
a // => 'cool'

// a variable declaration is an expression
var c; // => undefined

// a variable assignment is an expression
c = 'a third thing'; // => the rhs of the assignment, i.e. 'a third thing'
```
Mostly everything in JS is an expression / has a value.

## Operators

Operators act on values to produce new values. The value and side effects differ for each operator.

Arithmetic
  * +, -, * , /

Comparison

  * ==, ===, !=, !==, >, <, >=, <=
  * LOOSE (THEY COERCE THE TYPE)
  * STRICT (DO NOT COERCE THE TYPE)

Logical

  * Logical operators are typically used with Boolean (logical) values. When they are, they return a Boolean value.
  * logical NOT (!), logical OR (||), logical AND (&&)

  * !true // => false
  * !(10 > 5) // => false

  * true && true // => true
  * true && false // => false
  * (10 > 5) && (10 < 100) // => true
  * (10 > 5) && (10 < 10) // => false

  * true || true // => true
  * true || false // => true
  * false || false // => false
  * (10 > 5) || (10 < 100) // => true
  * (10 > 5) || (10 < 10) // => true

**Assignment**

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators (review overview section)

## Functions

A function is a group of statements that can be called multiple times, and can be stored in a variable or passed around.

To put it another way: A function is an object that contains JavaScript code that is run when I call the function.

Functions have ...

* Zero or more explicit parameters (A parameter is a variable in a method definition)
* Zero or more arguments (the arguments are the data you pass into the method's parameters)
* Two implicit parameters (this, arguments)
* Zero or more side effects
* Exactly one return value, undefined by default (ending a function with return; will return undefined)

**Function declaration**

A function declaration is a complete statement that can stand on its own. It creates a function with the name you specify.

A function declaration consists of ...

* function keyword
* function name
* parameter list
* function body

```
function functionName(firstParameter) {
  // body
}

// Outputs: "Yes!"
isItHoisted();

function isItHoisted() {
    console.log("Yes!");
}
```
**Function expression**

A function expression cannot stand on its own, but we can assign it to a variable or pass it to another function. It's not a statement, it's an expression, so it must be used as part of a statement.
```
var aFunction = function(thing) {
  alert(thing);
}

document.getElementById(id).addEventListener('click', function(){
  alert("Hay");
});

// Immediately Invoked Function Expression
(function(){

})();
```
Scope

* Lexical (top to bottom)
* Variable declarations (var) are hoisted to the top of their function, assignments are not
* Function declarations are hoisted in their entirety

## Control Flow

if...else

An if...else statement is one of the primary ways that you can control the flow of a JavaScript program (the other primary way is using functions).

if(something truthy){
  do something
} else {
  do something else
}

switch

switch can be used to handle multiple scenarios for a single variable

var name = "Mady";

switch(name) {
  case "Mady":
    console.log("Hi, Mady!");
    break;
  case "Joey":
    console.log("Are you a human or a dog?");
    break;
  default:
    console.log("I don't know you.");
}

for loops

In class, we will almost exclusively use iteration functions, but it's important to know what a for loop is.

for(var i = 0; i < 5; i++){
  console.log(i);
}

compare to a while loop

var i = 10;
while(i > 0) {
  console.log(i)
  i--
}

## Linking JS

* Name the file with the extension .js. (e.g. app.js)
* Write the relative path to your JS file in a <script> tag right before the closing tag of the body. <script src="app.js"></script> </body>

## Timers

It is possible to do things over time with JavaScript. To do something just once, later, use setTimeout. To do something over and over use setInterval.

* setTimeout(function, ms)

This means that the function should be run no less than, but possibly greater than x milliseconds from now (1000ms = 1s):

setTimeout(function() {
  alert("Your banking session has ended for your security. :)");
}, 36000);

* setInterval(function, ms)

This means that this function will be repeated every 'x' milliseconds.
Use clearInterval to stop the call.

var everySecond = setInterval(function() {
  document.querySelector('.time').textContent = Date.now();
}, 36000); // this will fire; you do not call everySecond();

clearInterval(everySecond) // when you want to cancel it
