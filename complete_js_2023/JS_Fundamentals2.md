# Js Fundamentals 2

What does strict mode do? How do you add it?
    'use strict'
    Will show you that a variable is not defined

## Functions
What is the syntax for a general function definition?
    ```function logger() {
    console.log('My name is Jonas')    
}```

How do you call a function?
    ```logger()```

How can we create a function without a name what are these called?
    ```const calcAge = function (birthYear) {
    return 2037-birthYear```
    Without a name they are called anonymous functions.

What do we call the storing of an anonymous function within a variable? What is the name of the function piece?
    This is a function expression. If we were to name it in the normal way then it would be a function declaration.

What is an arrow function with only 1 param?
    const calcAge3 = birthYear => 2037 - birthYear
    Really nice for one line functions has an implicit return.

How do we do an arrow function with more params and multilines?
    const calcAge4 = (birthYear,retirement) => {
        const age = 2037-birthYear;
        console.log(`This old at retirement ${retirement}. Currently {age}`)

What is the 
