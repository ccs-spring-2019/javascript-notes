## Document Object Model

Is the HTML you write the DOM? Nope!

The HTML you write is parsed by the browser and turned into the DOM.

Is the view source the DOM? Nope!

View Source just shows you the HTML that makes up that page. It's probably the exact HTML that you wrote.

* pull up the view source (view -> developer -> view source)

Is the code in dev tools the DOM? Kinda!

When you're looking at the panel, in whatever DevTools you are using, that shows you stuff that looks like HTML, that is a visual representation of the DOM!

* inspect a webpage

It was created directly from your HTML - that's why it kinda looks like it. In most simple cases, the visual representation of the DOM will be just like your simple HTML.

But it's often not the same...

When is the DOM different than the HTML?

* there are mistakes in your HTML and the browser has fixed them for you
* most likely case, JavaScript can manipulate the DOM (insert text into an element)
* Ajax and Templating

https://css-tricks.com/dom/

## Objects

The association between two terms, the key and the value.

{ key: value }

The combination of the key and value represent a property.

An object is a collection of key value pairs.

Objects are used for modeling. We can model a user profile, personal accounts, application data, etc.

Everything in JS is an object.

Functions are objects. Arrays are objects. Numbers, strings, etc. are all objects.

## Object Literals

let demo = {};

When defining JavaScript properties, the key is always a string. However, property keys don't require quotes (") like usual strings.

Property values can be any type.

You can also leave spaces between keys, values, and the colon to increase readability.

let demo = {
            firstname : "Mady",
            petowner: true
          };

Be sure to separate properties with commas.

## Objects and Dot Notation

Dot Notation allows us to access properties inside an object.
```
let animal = {
    name : "African bush elephant",
    scientificName : "Loxodonta africana",
    weight : 13000, //in pounds
    height : 11, //in feet
    speak: function(){
        console.log( "Trumpeting!!!" );
    }
};

console.log(animal.name); // => "African bush elephant"
```
Dot Notation allows us to add and edit properties inside an object.

!!! You can accidentally change the type of a property value to another type if you aren't careful. !!!
```
animal.speak = "I am an Elephant!!!";

animal.speak(); => will generate an error because speak is no longer a function
```
## Objects and Bracket Notation

Bracket notation allows us to access properties with strings. When using bracket notation, the property is wrapped in square brackets, [ ], and the key is always a string.
```
console.log( cat[ "age" ] );
```
Use bracket notation when accessing a property with a variable.
```
let name = "African bush elephant";

animal.name => undefined

animal[name] => "African bush elephant"
```
## Arrays

Use square brackets ([ ]) to define an array. You can start with an empty array or initialize an array with data.
```
let empty = [];

let movies = [ "Toy Story", "A Bug's Life", "Toy Story 2" ];
```
An array is a zero-indexed JavaScript object that stores a list of values.

Arrays provide a syntax so that all the items can be stored in one object and then accessed by their location (index) in the list.

The first element in the array is index 0.
```
let pixarMovies = [ "Toy Story", "A Bug's Life", "Toy Story 2", "Monsters, Inc.", "Finding Nemo", "The Incredibles", "Ratatouille", "WALL-E", "Up", "Toy Story 3", "Cars 2", "Brave", Inside Out", "The Good Dinosaur", "Cars 3" ];

console.log(pixarMovies[3]); // => "Monsters, Inc."
```
To assign a new value to an array, combine bracket notation with the assignment operator.
```
pixarMovies[3] = "Monsters University";

console.log(pixarMovies[3]); // => "Monsters University"
```
**Array.length**

The length property tells you how many elements are stored in the array.

**Array.push**

The push function will add a new element to the end of the array.

**Array.pop**

The pop function removes the last element from the end of the array and returns it.

**Array.unshift**

The unshift function adds a new element to the beginning of the array.

**Array.splice**

The splice function removes elements from an array using two numbers: the index from where elements should be removed and the number of elements to remove.
```
pixarMovies.splice(3, 2);

pixarMovies.splice(start with index 3, remove 2 elements);
```
## Boolean Logic

Boolean logic is the basis of making decisions in JavaScript.
```
var age = 22;

if(age > 21) {

  console.log("🍺");

}
```
Some things to keep in mind.

* true is not the same as 'true'
* NOT is ! AND is && OR is ||
* If two things must be true to proceed, then condition1 AND condition2 is the logical statement you need
* If only one of two things must be true to proceed, then condition1 OR condition2 is the logical statement you use
* In JavaScript, all values are either 'truthy' or 'falsy', meaning they can be (and are) coerced into booleans by operators and control flow
* JavaScript uses Type Conversion to coerce any value to a Boolean in contexts that require it, such as conditionals and loops

Falsy values (considered false when evaluated in a Boolean context)

* ""
* 0
* false
* undefined
* null
* NaN

## Equality

(==)

* If two values have the same type, just compare them
* If two values have different types, try to coerce them into the same type and then compare them.

Coercion

* When comparing a Number and String, coerce the String to a Number
* When comparing a Boolean and Anything, coerce the Boolean to a Number
* null == undefined returns true
* NaN == NaN returns false
* There can be multiple steps
  * example one
    * 1 / 1 == ""; coerce string to a number
    * 1 == 0; compare
    * return false
  * example two
    * "1" == true; coerce boolean to a number
    * "1" == 1; coerce string to a number
    * 1 == 1
    * return true

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness

(===)

## Strict Equality

* Two expressions are strictly equal if they have the same type and the same value
* Types are not coerced

## Object Equality

Objects (incl. arrays and functions) are compared by reference. Two references are only equal if they reference the same object.

  * [1] === [1] returns false

  * var a = [1];
  * var b = a; b is now a reference to the same object as a
  * a === b return true

## Other Coercion

  * If you try to add anything to a String, the other operand is coerced to a String and the two Strings are concatenated
  * To coerce an Object (incl. arrays and functions) to String, the .toString method is called on the Object
