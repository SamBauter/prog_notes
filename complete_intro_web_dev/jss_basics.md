# JS Basics

Why do we write JS?
It is easier for humans to understand than assembly or binary.

How many threads does js use?
Js is single threaded - it goes line by line. Only one thing happening at once.

What are the two ways to declare variables?
Use let or const. Const means it will not be changed later and it should be your default.

What syntax is at the end of statements in js?
A semicolon;

Where can you get a js repl?
In your browser inspect - console.

How do you link an external js file in html to be ran in the browser?
```html
<body>
    <script src="./experiments.js"> </script>
</body>
```

What is shortcut to open the dev tools in the browser?
opt cmd i

What order do you load css and js in? Which sections of the html do they occur in and why?
You link the style sheet in the head in a link tag. You want the code to be styled when the people first
see it you don't want them seeing raw html styles before your stylesheet is applied.
After this the body of the html will be loaded and people can see things
Finally you link the jss at the bottom of the body in a script tag. If the js takes a bit to
run your website has the illusion of running fast as it displays css and html first.

What is the syntax for strings in js?
"with anything or nothing" 'also works'

How can you inject variables into strings in js?
Use string templates with the below syntax
```js
`Hello ${firstName} ${lastName}!`
```

What are the booleans in js?
true and false

How many types does js have for numbers.
It just has one type:Number not float long etc.

What is the difference between === and == in Js?
The triple equals returns false for values that are not of a similar type. Use this as default.
The double equals will coerce types and then may return true.

How do you do branch logic basicall in js?
if() {}
else if(){}
else {}

Looping options in js?
while (condition) {}

Do you have increment and decrement in js?
Yes! counter++; Or ++counter, the difference between these two is when something is evaluated
Ex: print(counter++) will print 5 when print(counter)

What is the while loop syntax in js?
while(some condition) {
    update condition
}

What is the most basic java like loop in javascript?
for(i=0;i<10;i++){}

What is the most basic function syntax in js?
function myFunc(param) {
    return
}

What does it look like to assign a function to a variable?
const meow = function)( {
console.log("meow")) // you can use const let and var

What does it look like to use an arrow function from 2015?
const chirp = (param1,param2) => {
}

What scope do variables have for a function?
```js
function addFive(number) {
  const someVariable = "you can't see me outside this function";
  return number + 5;
}

addFive(10);
console.log(someVariable);
//ReferenceError because someVariable is not in the global scope
```

What is the best rule of thumb for scope in variables?
Variables are in scope for the curly brace block that they are defined within.
They can be modified in inner scopes.

What are builtins? Give some examples.
Function that someone has already made for you which are build into the browser.
someString.toLowerCase() and all the associated string functions

Objects in js

```js
const person = {
    name: "Sam",
    city: "Ogden",
}
console.log(person.name)
```

What are the fields in an object called?
Properties or keys.

What is an alternative to the dot operator for property access?
```js
person["name"]
```
How do you add functions or methods to objects in js?
```js
const dog = {
    name: "Luna",
    speak: function() {
        console.log("woof woof")
    },
    alternativeSpeak(){
        console.log("woof woof")
    }
}
```
How would you refer to other parts of the object in a method used for that object?
Use the `this` keyword.

How would you nest an object within another object in js?
```js
const me = {
    name: "sam",
    otherObj: {name: "otherObj"}
}
console.log(me.otherObj.name)
}
```
Is there a difference between list and array in js?
No there are only arrays.

How do you make a simple array in js?
```js
const myList = ["mon","tues"];
```
How do you get the length of an array in js?
```js
myArray.length
```

How do you add something to an array?
```js
myArray.push(someElement)
```

What is the most commone way to loop through an array?
```js
myArray.forEach(function(city){
    //doSomething
})
```

What is the new way to get elements via js and the DOM to change their styling? What is 
one of the older ways
```js
let mySquare = document.querySelector('.class-name');
```
```js
getElementByClassName('red-square')
```

##Event Listeners

```js
const button = document.querySelector('.myButton')
button.addEventListener("click", function(){
    //doStuff
});
```







