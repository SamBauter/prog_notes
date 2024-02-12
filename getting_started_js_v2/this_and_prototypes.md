A functions `this` keyword references an execution context for that call.
determined entirely by how this function was called.

A `this` -aware function can thus have different context each time its called which
makes it more flexible and reuseable.

Ex:
```js
var workshop = {
teacher: "Kyle",
ask(question) {
console.log(this.teacher,question)}}

workshop.ask("What is implicit binding?")
// Kyle What is implicit binding?
```
Only line 14 defines what this is. `this` is dependent completely based on the
context in which it is called.

What is another way of invoking a function?
```js
ask.call(myContext,"Why?") //.call is a way to invoke a function
// this is called explicit binding where myContext is the thing that defines
// this

```

## Prototypes
```js
function Workshop(teacher) {
    this.teacher = teacher
}

Workshop.prototype.ask =function(question){
console.log(this.teacher,question)
}

var deepJS = new Workshop("Kyle")
var reactJS = new Workshop("Suzy")

deepJs.ask("Is 'prototype' a class?")
//Kyle is 'prototype' a class?

reactJS.ask("Isn't 'prototype' ugly")
//Suzy isn't 'prototype' ugly?
```
Its more common now to use classes but this is what is happening under the hood.

## Class
Same thing as prototype different syntax
```js
class Workshop {
    constructor(teacher){
        this.teacher = teacher
    }
    ask(question){
    console.log(this.teacher,question)}
}
```

