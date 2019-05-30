## Function Design Recipe

The idea of a "design recipe" for programs comes from the Program By Design curriculum.

http://www.htdp.org/2018-01-06/Book/part_one.html#%28part._sec~3afuncs%29

1. What's the input and where does it come from? Does it come as arguments? Does it read data from what the user has entered? Does it come from a mouse click or other DOM event? Does it come from the server?

  * var name = $('.js-name').val();

  * $('.js-profile-form').on('submit', saveProfile);

2. What's the output and where does it go? Is it returned from the function? Is it printed? Does it send the results to a server?

  * Deciding whether to design functions with parameters and returned values or alternatively with print statements or other direct interactions is a question that requires a lot of thought.

  * As a general principle, though, it's usually best to write every function you can with parameters and return values. That makes them flexible; the program that calls it can decide what to do with the returned result (print it, send it to a server, whatever).

3. Write a one-line purpose statement or description that says in simple English what the function does.

  * // Calculate the square of a number

4. Write a type contract that states the function's name and the names and types of its parameters and return value.
  ```
  // function description
  // parameter description
  // return description

  function name(parameter) {

  }


  // Calculate the square of a number
  // num is a Number to square
  // returns the square

  function square(num) {

  }
```
5. Write some examples of calling the function, including the results you expect in each case.

  * For functions that return values, use console.assert which expects a Boolean (true or false) expression that should be true if the function is correct:
```
  console.assert(square(2) == 4);

  console.assert(square(-1) == 1);
```
  * Write enough different examples to convince yourself that your function works correctly on all expected kinds of data.

6. Write the body of the function.
```
  // Calculate the square of a number
  // num is a Number to square
  // returns the square

  function square(num) {
    return Math.pow(num, 2);
  }

  console.assert(square(2) == 4);

  console.assert(square(-1) == 1, 'custom message here');
```
7. Run the function and check the results.

  * If the assertions are true, everything stays quiet; if one is false, you get an error message that helps you locate the source of the problem

  * Resolve any discrepancies and repeat the process until all the tests pass

## Scope

* Scope answers the questions "Where do variables live?" and "How does my code find them?".

* Scope pertains to the variable access of a function when it is invoked and is unique to each invocation.

* A variable can be defined in either local or global scope. This establishes the variables’ accessibility from different scopes during runtime.

* Global variables, meaning any variables declared outside of a function body, can be accessed and altered in any scope. Local variables exists only within the function body of which they are defined.
```
// ex. 1

var name = "Mady";

function greeting() {
  var name = "Rock";
  console.log("Hello, " + name);
}

greeting();

console.log("Hello, " + name);

// ex. 2

var name = "Mady";

function greeting() {
  name = "Rock";
  console.log("Hello, " + name);
}

greeting();

console.log("Hello, " + name);

// ex. 3

function greeting() {
  var name = "Mady";
  console.log("Hello, " + name);
}

function farewell() {
  console.log("Goodbye " + name);
}

greeting();
farewell();
```
* ECMAScript 6 (ES6/ES2015) introduced the let and const keywords that support the declaration of block scope local variables.
* the block is delimited by a pair of curly brackets.
* The variable will be confined to the scope of a block that it is defined in.
* Variables declared with var do not have block scope.

* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/block
* see scoping rules: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let
* make sure you review let and const on MDN

## Hoisting

* Variable declarations but not assignments are moved to the top of their scope.
* Both the declaration and body for function declarations are hoisted.
* Only the declaration for function expressions is hoisted.

* Global constants do not become properties of the window object
* let bindings are not subject to Variable Hoisting

## What is “this” Context

* Context answers the question "What is the value of this?".

* When a function is called as a method of an object, this is set to the object the method is called on:
```
var obj = {
    foo: function() {
        return this;   
    }
};

obj.foo() === obj; // true
```
* When a function is invoked with the new operator, the value of this within the scope of the function will be set to the newly created instance:
```
function foo() {
    console.log(this);
}

new foo() // foo

// console.log automatically prints when it's used, and thus when the function is called, it's printed again
```
* When a function is unbound (called without the new operator), this  will default to the global context or window object in the browser.
```
function foo() {
    console.log(this);
}

foo() // Window
```
// if the function is executed in strict mode, the context will default to undefined instead of Window (strict mode prevents gaining access to the global object)

* In arrow functions, this retains the value of the enclosing lexical context's this. In global code, it will be set to the global object:
```
var obj = {
    foo: () => this
};

obj.foo() === obj; // false
```
## Why Strict Mode?

Strict Mode is a new feature in ECMAScript 5 that allows you to place a program, or a function, in a "strict" operating context. This strict context prevents certain actions from being taken and throws more exceptions.

Strict mode helps out in a couple ways:

* It catches some common coding bloopers, throwing exceptions.
* It prevents, or throws errors, when relatively "unsafe" actions are taken (such as gaining access to the global object).
* It disables features that are confusing or poorly thought out.
* https://johnresig.com/blog/ecmascript-5-strict-mode-json-and-more/

## IIFE

Immediately Invoked Function Expression

Apply "strict mode" to the whole file...
```
// Non-strict code...

(function(){
  "use strict";

  // Define your library strictly...
})();

// Non-strict code...
```
Why inside an IIFE?

Read "Strict mode for scripts":
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode
