# Javascript Fundamental Part 1

What are the 3 core technologies of the web? And What do they do?
    -HTML(Noun) CSS(Adjective) and JS(Verb)

Why Learn Javascript instead of learning a Framework like React first?
    - By learning js first you will be able to understand how the framework is implemented.
    - You will also be able to move to other frameworks like angular or vue much more easily.

How do you link a js file to HTML? Which tags is it near?
    ```
    <body>
    <script src="index.js"></script>
    </body>
    ```
    Right before the ending body tag.

Which folder do you use when doing examples to start your project?
Use the starter folder and just open in intelliJ

What is a value in js?
A piece of data Ex: 'Jonas'

What is a variable in js?
A box to put something in.

What is const?
A value in a const variable cannot be changed it is immutable.
You cannot declare empty ones. You must supply an initial value.
Cannot const age; Must give an initial value
Use this as your most common default - it's better if variables don't change much

What is let?
Creates a variable that can change.
You can declare it and set it later until set it will be undefined Ex: let age;

What happens if you forget to declare const var or let? Ex: lastName = "Bauter"
JS will create a property on the global object with name lastName and value "Bauter"

What are template literals and what is the syntax?
These are just like f-strings: `I'm ${firstName} a ${year-birthYear} year old!`
Both expressions or variables can be evaluated in the ${}
You don't need to add \n instead you can just hit enter and the literal works for you.

What is the result of
```
const inputYear = '1991'
console.log(inputYear + 18)    
```?
    199118 - The 18 was coerced to a string and concatenated.

What is the constructor to turn a string number into a number type?
    Number(strNumber)

What is the typeof NaN?
    it is a number type.

When does type coercion happen?
    Whenever an operator encounters two different types it will attempt type coercion.

How does plus work for a str and a number what gets coerced in what order?
    This will be treated as concatenation regardless of what comes first.
    The coercion always happens from left to right. so 1+2+'3' = 33
    The number is coerced to a string.

How does minus work for a str and a number what gets coerced?
    This will be treated as subtraction with the string being coerced to a number.

What are the falsy values?
    0, '', undefined, null, NaN

How does falsy and truth work for if statements?
    if (money) {
        console.log("Don't spend it all") }

How can we check if something has been initialized or is undefined?
    We can easily check if(some_var) however other falsy values like 0 will also return false

 When can you omit the curly braces after if?
    When the body is only one line.

What is the difference between == and ===? Which do you usually use.
Strict equality operator ===: Does not perform type coercion, only returns true when two values are exactly the same.
Loose equality operator ==: Does coercion so '18' == 18 returns True.
Prefer to use === as it is more predictable.

How can you prompt a user for input?
const userInput = prompt("Whats your favorite number?")
Returns a string so this is one place where == might be nice.

How is else if done in js?
    else if(){

What are the basic boolean logical operators in Js?
&& || and !

What is the syntax for a switch statement?
    switch(some_var) {
        case 'monday': // day === 'monday' compares via strict equality
            console.log("blah");
            break;
        case 'tuesday:
            etc.
        default:
            //like your else statement in case none of the cases are true.

What happens if you forget the break?
    The code will continue executing blocks even if the case doesn't match.

What is the difference between an expression and a statement?
    An expression produces a value.
    A statement performs some actions ex: 
    if (23>my_num){
    const str = '23 is bigger'
    } an action was performed but 
    no value was produced. 

What is the syntax for the conditional operator(ternary)? What is a common use? And why is it quite a bit better than
using if else for that use?
    age >= 18 ? console.log('I like to drink wine'): console.log('I like to drink water')
    Very commonly used to produce a value and store it in a variable. const drink = age>=18?'wine':'water'
    Notice you can use const and you can initialize the variable immediately
    With if else:
    let drink;
    if (age>=18) drink = 'wine'
    else drink = 'water' 

How often are javascript releases? How does compatibility work?
    Every year and they all are backwards compatible all the way back to ES1
    They are NOT forwards compatible for old browsers. You need current browsers for modern features.
    Babel can traspile and polyfill to old versions to support older browsers.













