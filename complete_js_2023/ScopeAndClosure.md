# Scope and Closure
What is scope?
It is **where** in the code you will look for variables and their values.
```js
let teacher = "kyle";
function otherClass(){
    teacher = "Suzy"; // Will take teacher from the outerscope and set its value
    topic = "React"; // In non-strict mode will set global scope topic, it will implictly declare the variable if undeclared
    console.log("Welcome!")
}
```

Undeclared variables have never been declared with var let or const. They usually result
in Reference Errors.

Undefined variables have been declared but not yet assigned a value.
```js
let someVar;
console.log(someVar) // outputs undefined
```

Function Expression - Functions themselves are actually values, they are a **first class citizen**.
You can assign them to variables and move them around.
```js
let clickHandler = function(){} //Anonymous function expression 
let keyHandler = function keyHandler(){} //Named function expression
```

```js
let ids = people.map(person => person.id); //An arrow function is a form of anonymous function
let ids = people.map(function getId(person){ //named version more readable name documents code
    return person.id});
```

IIFEs - Immediately invoked function expressions - A Function that runs as soon as it is defined.
IIFES are LEAVE NO TRACE - there is no function or variables left behind in the global scope when they immediately 
execute. This means their purpose is to execute once for one-off tasks.
```js
var teacher = "Kyle"
( function anotherTeacher() {
    var teacher = "Suzy"; 
    console.log(teacher);
})(); //Notice this is immediately invoked.
```
Normal functions usually leave behind the function name in the outer scope so that they
can be re-used they are generally meant for re-use.
Historically more important for modules before ES6 modules came out.
```js
let module = (function(){
    let privateVar = "private"
    function privateFunction(){
        console.log("private func")
    }
    return { publicMethod: function() {
            console.log("public method");
            privateFunction();
        }
    };
})();
module.publicMethod(); //accessible
privateFunction(); //throws error because not available in outer scope
```







