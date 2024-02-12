# Scope
If you didn't define a variable in the global scope, and you just set it.
It will be set and defined in the global scope.

```js
function test(){
    myVar = 20
}
test() //when I call this it will set a global myVar even though it was never declared
```

## Function Expressions
```js
var clickHandler = function(){
}    //Anonymous function expression

var keyHandler = function keyHandler(){
} //Named function expression
```

Which function do you feel is better
```js
var ids = people.map(person => person.id)

var ids = people.map(
    function getId(person){
        return person.id
    }
)
```
An argument could be made that the getId function tells you what it is doing
with its name and you could ignore the implementation this could be a 
reasonable argument for a longer function.

This is also true of promise chaings
```js
getPerson()
.then(person => getData(person.id))
.then(renderData) 
//vs
getPerson()
.then(function getDataFrom(person){ //descriptive name is nice.
    return getData(person.id);
})
```

## IIFEs
Immediately Invoked Function expressions
```js
var teacher = "Kyle";
( function anotherTeacher() {
    var teacher = "Suzy";
        console.log(teacher);
    })();
console.log(teacher) //Kyle
```

IIFEs can protect assignments from getting overwritten.
This is a common pattern.

## Block Scoping
Instead of IIFEs we usually use a curly brace block and use the keyword let.
`let` is block scoped.
```js
var teacher = "Kyle";
{
    let teacher = "Suzy"
    console.log(teacher) //Suzy
}
console.log(teacher) //Kyle
```


## Closure
A super important powerful thing to understand in your programming career in many
different languages.

closure - when a function "remembers" the variables outside of it, even if you pass that
function elsewhere.

```js
function ask(question) {
    setTimeout(function waitASec(){
    console.log(question)
    },100);
} 
ask("What is closure?")
```

Wait a sec as a function has closure over the question variable. 

Ex:
```js
function ask(question) {
return function holdYourQuestion(){
    console.log(question)
}
}
var myQuestion = ask("What is closure?")
//Somewhere later in the code
myQuestion() // Notice it has access to the question that was passed to it originally.
//My question had closure over the question variable.
```







